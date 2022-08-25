---
title: Geschlossene Benutzergruppen in AEM
seo-title: Closed User Groups in AEM
description: Hier erfahren Sie mehr über geschlossene Benutzergruppen in AEM.
seo-description: Learn about Closed User Groups in AEM.
uuid: 83396163-86ce-406b-b797-2457ed975ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: a2bd7045-970f-4245-ad5d-a272a654df0a
docset: aem65
exl-id: 39e35a07-140f-4853-8f0d-8275bce27a65
feature: Security
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '6872'
ht-degree: 60%

---

# Geschlossene Benutzergruppen in AEM{#closed-user-groups-in-aem}

## Einführung    {#introduction}

Seit Einführung von AEM 6.3 gibt es eine neue Implementierung des Features „Geschlossene Benutzergruppe“, welche die Probleme hinsichtlich der Leistung, Skalierbarkeit und Sicherheit der bestehenden Implementierung beheben soll.

>[!NOTE]
>
>Der Einfachheit halber wird das Feature im Rahmen dieser Dokumentation als „CUG“ abgekürzt (für Closed User Group, geschlossene Benutzergruppe).

Ziel der neuen Implementierung ist es, bei Bedarf vorhandene Funktionen abzudecken und gleichzeitig Probleme und Designbeschränkungen älterer Versionen zu beheben. Das Ergebnis ist eine neue CUG-Version mit den folgenden Eigenschaften:

* Deutliche Trennung der Authentifizierungs- und Autorisierungselemente, die einzeln oder in Kombination eingesetzt werden können
* Dediziertes Autorisierungsmodell, das eingeschränkten Lesezugriff auf die konfigurierten CUG-Baumstrukturen bietet, ohne andere Einrichtungs- und Erlaubnisanforderungen für die Zugriffskontrolle zu beeinträchtigen
* Trennung zwischen der Einrichtung der Zugriffskontrolle für den eingeschränkten Lesezugriff, der normalerweise in Autoreninstanzen benötigt wird, und der Berechtigungsprüfung, die normalerweise nur in der Veröffentlichung gewünscht wird;
* Bearbeiten des eingeschränkten Lesezugriffs ohne Berechtigungseskalation
* Dedizierte Knotentyperweiterung zur Markierung der Authentifizierungspflicht
* Optionaler, der Authentifizierungspflicht zugehöriger Anmeldepfad

### Die neue benutzerdefinierte Benutzergruppenimplementierung {#the-new-custom-user-group-implementation}

Eine CUG besteht im Kontext von AEM aus den folgenden Schritten:

* Schränken Sie den Lesezugriff auf die Baumstruktur ein, die geschützt werden muss, und gewähren Sie nur Prinzipalen Lesezugriff, die entweder mit einer gegebenen CUG-Instanz aufgeführt oder in der CUG-Prüfung nicht berücksichtigt werden. Dies wird als Element der **Autorisierung** bezeichnet.
* Erzwingen Sie die Authentifizierung bei einer gegebenen Baumstruktur und geben Sie optional eine dedizierte Anmeldeseite für die Struktur an, die daraufhin ausgeschlossen wird. Dies wird als Element der **Authentifizierung** bezeichnet.

Die neue Implementierung unterscheidet zwischen Autorisierungselementen und Authentifizierungselementen. Seit AEM 6.3 ist es möglich, den Lesezugriff zu beschränken, ohne eine Authentifizierungspflicht hinzufügen. Dies ist beispielsweise gebräuchlich, wenn eine bestimmte Instanz eine vollständige Authentifizierung anfordert oder eine gegebene Baumstruktur bereits in einem Teilbaum vorhanden ist, der bereits eine Authentifizierung anfordert.

Ebenso kann eine bestimmte Baumstruktur mit einer Authentifizierungspflicht markiert werden, ohne dass die effektive Einrichtung der Berechtigungen geändert werden muss. Die Kombinationen und die Ergebnisse werden im Abschnitt [Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) aufgeführt.

## Übersicht {#overview}

### Autorisierung: Beschränken des Lesezugriffs {#authorization-restricting-read-access}

Das zentrale Feature einer CUG besteht in der Einschränkung des Lesezugriffs auf eine bestimmte Baumstruktur im Content-Repository für alle außer ausgewählte Prinzipale. Die neue Implementierung manipuliert nicht spontan die Standardinhalte der Zugriffssteuerung, sondern definiert einen dedizierten Typ von Zugriffssteuerungsrichtlinie, der eine CUG darstellt.

#### Zugriffssteuerungsrichtlinie für CUG {#access-control-policy-for-cug}

Dieser neue Typ von Richtlinie weist die folgenden Eigenschaften auf:

* Zugriffssteuerungsrichtlinie des Typs org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy (definiert durch die Apache Jackrabbit-API);
* PrincipalSetPolicy gewährt Berechtigungen für einen veränderbaren Satz von Prinzipalen.
* Die erteilten Berechtigungen und der Umfang dieser Richtlinie sind ein Implementierungsdetail.

Die Implementierung von PrincipalSetPolicy, die zur Darstellung von CUGs verwendet wird, definiert zusätzlich Folgendes:

* CUG-Richtlinien gewähren nur Lesezugriff auf reguläre JCR-Elemente (beispielsweise sind Zugriffssteuerungsinhalte ausgeschlossen).
* Der Umfang wird durch den zugriffsgesteuerten Knoten definiert, der die CUG-Richtlinie enthält.
* CUG-Richtlinien können verschachtelt werden. Eine verschachtelte CUG fängt als neue CUG an, ohne den Prinzipalsatz der übergeordneten CUG zu übernehmen.
* Der Effekt der Richtlinie wird an den gesamten Teilbaum und bis an die nächste verschachtelte CUG weitergegeben.

Diese CUG-Richtlinien werden über ein separates Autorisierungsmodul namens oak-authorization-cug in einer AEM-Instanz bereitgestellt. Dieses Modul verfügt über eine eigene Zugriffssteuerungsverwaltung und Berechtigungsprüfung. Das heißt, die Standardversion von AEM umfasst eine Oak-Content-Repository-Konfiguration, die mehrere Autorisierungsmechanismen kombiniert. Weitere Informationen finden Sie unter [diese Seite in der Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

Bei dieser Composite-Konfiguration ersetzt eine neue CUG nicht den vorhandenen Zugriffssteuerungsinhalt, der an den Zielknoten angehängt ist, sondern dient als Ergänzung, die später auch entfernt werden kann, ohne die ursprüngliche Zugriffskontrolle zu beeinträchtigen. Standardmäßig wäre dies in AEM eine Zugriffssteuerungsliste.

Anders als bei der vorherigen Implementierung werden neue CUG-Richtlinien immer als Zugriffssteuerungsinhalt erkannt und behandelt. Dies bedeutet, dass sie mit der JCR-Zugriffssteuerungsverwaltungs-API erstellt und bearbeitet werden. Weitere Informationen finden Sie unter [Verwalten von CUG-Richtlinien](#managing-cug-policies) Abschnitt.

#### Berechtigungsprüfung von CUG-Richtlinien {#permission-evaluation-of-cug-policies}

Neben einer dedizierten Zugriffssteuerungsverwaltung für CUGs, ermöglicht das neue Autorisierungsmodell bedingt die Aktivierung der Berechtigungsprüfung für seine Richtlinien. Dies ermöglicht die Einrichtung von CUG-Richtlinien in einer Staging-Umgebung. Dabei wird die Prüfung der effektiven Berechtigungen erst aktiviert, wenn sie in die Produktionsumgebung repliziert werden.

Die Berechtigungsprüfung für CUG-Richtlinien und die Interaktion mit dem standardmäßigen oder zusätzlichen Autorisierungsmodellen folgen dem Muster, das für mehrere Autorisierungsmechanismen in Apache Jackrabbit Oak entworfen wurde: Ein gegebener Berechtigungssatz wird gewährt, falls – und nur falls – alle Modelle Zugriff erteilen. Siehe [diese Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) für weitere Details.

Die folgenden Eigenschaften gelten für die Berechtigungsprüfung, die mit dem Autorisierungsmodell verknüpft ist, das CUG-Richtlinien verarbeiten und prüfen soll:

* Sie verarbeitet nur Leseberechtigungen für normale Knoten und Eigenschaften, aber keine Zugriffssteuerungsinhalte.
* Es werden keine Schreibberechtigungen und keine für die Änderung geschützter JCR-Inhalte erforderlichen Berechtigungen verwaltet (Zugriffskontrolle, Informationen zum Knotentyp, Versionierung, Sperren oder Benutzerverwaltung usw.). Diese Berechtigungen sind von einer CUG-Richtlinie nicht betroffen und werden vom zugehörigen Autorisierungsmodell nicht bewertet. Ob diese Berechtigungen gewährt werden, hängt von den anderen Modellen ab, die in der Sicherheitseinrichtung konfiguriert sind.

Die Auswirkungen einer einzelnen CUG-Richtlinie auf die Berechtigungsprüfung lassen sich wie folgt zusammenfassen:

* Lesezugriff wird allen vorenthalten, außer Subjekten, die ausgeschlossene oder aufgeführte Prinzipale enthalten.
* Die Richtlinie wirkt sich auf den zugriffsgesteuerten Knoten aus, der die Richtlinie und ihre Eigenschaften enthält.
* Der Effekt wird zusätzlich in der Hierarchie vererbt, d. h. in der Elementstruktur, die vom zugriffsgesteuerten Knoten definiert wird.
* Sie betrifft jedoch weder Geschwister noch Vorgänger des zugriffsgesteuerten Knotens.
* Die Vererbung einer gegebenen CUG hält an einer verschachtelten CUG an.

#### Best Practices {#best-practices}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition des eingeschränkten Lesezugriffs durch CUGs berücksichtigt werden:

* Entscheiden Sie bewusst, ob Sie die CUG benötigen, um Lesezugriff einzuschränken oder die Authentifizierung zu erzwingen. Sollte dies der Fall sein oder beides erforderlich sein, finden Sie im Abschnitt Best Practices weitere Informationen zur Authentifizierungspflicht .
* Erstellen Sie ein Bedrohungsmodell für die Daten oder Inhalte, die geschützt werden müssen, um Bedrohungsgrenzen zu identifizieren und ein klares Bild der Empfindlichkeit der Daten und Rollen zu erhalten, die mit autorisiertem Zugriff verbunden sind.
* Modellieren Sie die Repository-Inhalte und CUGs unter Berücksichtigung allgemeiner Aspekte bezüglich der Autorisierung und bewährter Vorgehensweisen:

   * Denken Sie daran, dass Leseberechtigungen nur gewährt werden, wenn eine bestimmte CUG und die Prüfung anderer in der Einrichtung bereitgestellter Module einem bestimmten Subjekt erlauben, ein bestimmtes Repository-Element zu lesen.
   * Vermeiden Sie die Erstellung überflüssiger CUGs, wenn der Lesezugriff bereits von anderen Autorisierungsmodulen eingeschränkt ist.
   * Ein extremer Bedarf an verschachtelten CUGs weist möglicherweise auf Fehler beim Content-Design hin.
   * Ein extrem übermäßiger Bedarf an CUGs (z. B. auf jeder einzelnen Seite) weist möglicherweise darauf hin, dass ein benutzerdefiniertes Autorisierungsmodell besser geeignet wäre, um den Sicherheitsanforderungen der vorliegenden Anwendung und Inhalte gerecht zu werden.

* Beschränken Sie die Pfade mit Unterstützung für CUG-Richtlinien auf einige wenige Baumstrukturen im Repository, um eine optimale Leistung zu ermöglichen. Beispielsweise nur CUGs unter dem Knoten /content zulassen, die seit AEM 6.3 als Standardwert geliefert wurden.
* CUG-Richtlinien sind darauf ausgelegt, einem kleinen Prinzipalsatz Lesezugriff zu gewähren. Der Bedarf an einer sehr großen Anzahl an Prinzipalen deutet möglicherweise auf Fehler beim Content- bzw. Anwendungsdesign hin und sollte überdacht werden.

### Authentifizierung: Definieren der Authentifizierungspflicht {#authentication-defining-the-auth-requirement}

Die Teile des CUG-Features, die für Authentifizierung relevant sind, ermöglichen die Markierung von Baumstrukturen, die Authentifizierung erfordern, und optional die Angabe einer dedizierten Anmeldeseite. Gemäß der vorherigen Version ermöglicht die neue Implementierung die Kennzeichnung von Baumstrukturen, die eine Authentifizierung im Content-Repository erfordern, und die bedingte Aktivierung der Synchronisierung mit der `Sling org.apache.sling.api.auth.Authenticator`verantwortlich für die Durchsetzung der Anforderung und die Umleitung zu einer Anmelderessource.

Diese Anforderungen werden mit dem Authenticator anhand eines OSGi-Services registriert, der die Registrierungseigenschaft `sling.auth.requirements` zur Verfügung stellt. Diese Eigenschaften werden dann dazu verwendet, die Authentifizierungspflichten dynamisch zu erweitern. Weitere Informationen finden Sie in der [Sling-Dokumentation](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### Definieren der Authentifizierungspflicht mithilfe eines dedizierten Mixin-Typs {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Aus Sicherheitsgründen ersetzt die neue Implementierung die Verwendung einer verbleibenden JCR-Eigenschaft durch einen dedizierten Mixin-Typ namens `granite:AuthenticationRequired`, der eine einzelne optionale Eigenschaft des Typs STRING für den Anmeldepfad definiert `granite:loginPath`. Nur Inhaltsänderungen mit Bezug zu diesem Mixin-Typ führen zur Aktualisierung der beim Apache Sling Authenticator registrierten Anforderungen. Die Änderungen werden beim Beibehalten vorübergehender Änderungen nachverfolgt und erfordern daher eine `javax.jcr.Session.save()` auffordern, wirksam zu werden.

Dasselbe gilt für die `granite:loginPath` -Eigenschaft. Sie wird nur berücksichtigt, wenn sie durch den Mixin-Typ definiert ist, der sich auf die auth-requirement bezieht. Wenn Sie eine Resteigenschaft mit genau diesem Namen auf einem unstrukturierten JCR-Knoten hinzufügen, wird die gewünschte Wirkung nicht angezeigt und die Eigenschaft wird von dem Handler ignoriert, der für die Aktualisierung der OSGi-Registrierung verantwortlich ist.

>[!NOTE]
>
>Die Anmeldepfadeigenschaft ist optional und muss nur dann festgelegt werden, wenn die Baumstruktur, welche die Authentifizierung erfordert, nicht auf den Standard oder eine anderweitig übernommene Anmeldeseite zurückfallen kann. Siehe dazu unten die [Prüfung des Anmeldepfads](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path).

#### Registrieren der Authentifizierungspflicht und des Anmeldepfads mit dem Sling Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Da diese Art von Authentifizierungspflicht voraussichtlich auf bestimmte Ausführungsmodi und auf eine kleine Untergruppe von Baumstrukturen im Inhalts-Repository beschränkt ist, ist das Tracking des Anforderungs-Mixin-Typs und der Eigenschaften des Anmeldepfads an eine bedingte und an eine entsprechende Konfiguration gebunden, die die unterstützten Pfade definiert (siehe Konfigurationsoptionen unten). Daher lösen nur Änderungen im Rahmen dieser unterstützten Pfade eine Aktualisierung der OSGi-Registrierung aus, anderswo werden der Mixin-Typ und die Eigenschaft ignoriert.

Das standardmäßige AEM-Setup nutzt diese Konfiguration jetzt, indem es ermöglicht, das Mixin im Autorenausführungsmodus festzulegen, es jedoch nur bei Replikation auf der Veröffentlichungsinstanz wirksam zu machen. Siehe [diese Seite](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) für Details, wie Sling die Authentifizierungspflicht durchsetzt.

Hinzufügen der `granite:AuthenticationRequired` Der Mixin-Typ innerhalb der konfigurierten unterstützten Pfade führt dazu, dass die OSGi-Registrierung des verantwortlichen Handlers mit einem neuen, zusätzlichen Eintrag mit dem `sling.auth.requirements` -Eigenschaft. Wenn eine bestimmte Authentifizierungspflicht das optionale `granite:loginPath` -Eigenschaft, wird der Wert zusätzlich beim Authenticator mit dem Präfix &quot;-&quot;registriert, um von der Authentifizierungspflicht ausgeschlossen zu werden.

#### Auswertung und Vererbung der Authentifizierungspflicht {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling-Authentifizierungspflichten sollen anhand der Seiten- oder Knotenhierarchie vererbt werden. Die Details der Vererbung und der Prüfung von Authentifizierungspflichten (wie Reihenfolge und Rangfolge) sind ein Implementierungsdetail und werden in diesem Artikel nicht behandelt.

#### Prüfung des Anmeldepfads {#evaluation-of-login-path}

Die Bewertung des Anmeldepfads und die Umleitung zur entsprechenden Ressource bei Authentifizierung sind derzeit ein Implementierungsdetail des Authentifizierungs-Handlers der Adobe Granite Login Selector ( `com.day.cq.auth.impl.LoginSelectorHandler`), ein standardmäßig mit AEM konfigurierter Apache Sling AuthenticationHandler.

Bei Aufruf `AuthenticationHandler.requestCredentials` Dieser Handler versucht, die Zuordnungs-Anmeldeseite zu ermitteln, an die der Benutzer umgeleitet wird. Dies umfasst die folgenden Schritte:

* Es wird unterschieden, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * aus dem LoginPathProvider, wie vom neuen `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * von der veralteten CUG-Implementierung
   * aus den Anmeldeseitenzuordnungen , wie mit der Variablen `LoginSelectorHandler`,
   * und schließlich zur standardmäßigen Anmeldeseite wechseln, wie mit der Variablen `LoginSelectorHandler`.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Ziel dieser Dokumentation ist die Bewertung des Anmeldepfads, wie er von der internen `LoginPathProvider` -Schnittstelle. Die seit Einführung von AEM 6.3 enthaltene Implementierung verhält sich wie folgt:

* Die Registrierung des Anmeldepfads hängt von der Unterscheidung ab, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * von `LoginPathProvider` durch die neue `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * von der veralteten CUG-Implementierung
   * aus den Anmeldeseitenzuordnungen , wie mit der Variablen `LoginSelectorHandler`,
   * und gehen Sie schließlich zur standardmäßigen Anmeldeseite, wie mit der Variablen `LoginSelectorHandler`.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Die `LoginPathProvider` wie von der neuen Unterstützung für Authentifizierungsanforderungen in Granite implementiert, stellt Anmeldepfade bereit, die durch die `granite:loginPath` -Eigenschaften, die wiederum vom Mixin-Typ wie oben beschrieben definiert werden. Die Zuordnung des Ressourcenpfads, der den Anmeldepfad und den Eigenschaftswert selbst enthält, wird im Speicher aufbewahrt und wird geprüft, um einen geeigneten Anmeldepfad für andere Knoten in der Hierarchie zu ermitteln.

>[!NOTE]
>
>Die Prüfung wird nur für Anfragen durchgeführt, die mit Ressourcen verknüpft sind, die sich in den konfigurierten unterstützten Pfaden befinden. Für alle anderen Anfragen werden die alternativen Möglichkeiten zum Ermitteln des Anmeldepfads geprüft.

#### Best Practices {#best-practices-1}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition von Authentifizierungspflichten berücksichtigt werden:

* Verschachtelung von Authentifizierungspflichten vermeiden: Eine einzelne „auth-requirement“-Markierung am Anfang einer Baumstruktur sollte ausreichen und wird an den gesamten vom Zielknoten definierten Teilbaum weitergegeben. Zusätzliche Authentifizierungspflichten innerhalb dieser Baumstruktur sind als redundant zu betrachten und führen möglicherweise zu Leistungseinbußen bei der Prüfung der Authentifizierungspflicht in Apache Sling. Aufgrund der Trennung der autorisierungs- und authentifizierungsrelevanten CUG-Bereiche ist es möglich, den Lesezugriff anhand von CUG-Richtlinien oder anderen Richtlinien einzuschränken und gleichzeitig in der gesamten Baumstruktur die Authentifizierung zu erzwingen.
* Modellieren Sie Repository-Inhalte so, dass Authentifizierungsanforderungen für die gesamte Baumstruktur gelten, ohne verschachtelte Unterbäume erneut von der Anforderung ausschließen zu müssen.
* Zur Vermeidung genauer Angaben und der darauf folgenden Registrierung redundanter Anmeldepfade:

   * sich auf Vererbung verlassen und vermeiden, verschachtelte Anmeldepfade zu definieren,
   * Legen Sie für den optionalen Anmeldepfad keinen Wert fest, der dem Standardwert oder einem vererbten Wert entspricht.
   * Anwendungsentwickler müssen identifizieren, welche Anmeldepfade in den globalen „login-path“-Konfigurationen (Standard und Zuordnungen) konfiguriert werden müssen, die mit dem `LoginSelectorHandler` verknüpft sind.

## Darstellung im Repository {#representation-in-the-repository}

### CUG-Richtliniendarstellung im Repository {#cug-policy-representation-in-the-repository}

In der Oak-Dokumentation wird beschrieben, wie die neuen CUG-Richtlinien im Repository-Inhalt dargestellt werden. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Authentifizierungspflicht im Repository {#authentication-requirement-in-the-repository}

Die Notwendigkeit einer separaten Authentifizierungspflicht spiegelt sich im Repository-Inhalt wider, wobei ein dedizierter Mixin-Knotentyp auf dem Zielknoten platziert wird. Der Mixin-Typ definiert eine optionale Eigenschaft, um für die vom Zielknoten definierte Baumstruktur eine dedizierte Anmeldeseite festzulegen.

Die mit dem Anmeldepfad verknüpfte Seite kann sich innerhalb oder außerhalb dieser Baumstruktur befinden. Sie ist von der Authentifizierungspflicht ausgenommen.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Verwalten von CUG-Richtlinien und der Authentifizierungspflicht {#managing-cug-policies-and-authentication-requirement}

### Verwalten von CUG-Richtlinien {#managing-cug-policies}

Der neue Typ von Zugriffssteuerungsrichtlinien zur Beschränkung des Lesezugriffs für eine CUG wird mithilfe der JCR-Zugriffssteuerungs-Management-API verwaltet und folgt den Mechanismen, die mit der [JCR 2.0-Spezifikation](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html).

#### Neue CUG-Richtlinie erstellen {#set-a-new-cug-policy}

Code für die Anwendung einer neuen CUG-Richtlinie auf einen Knoten, der vorher keinen CUG-Satz aufwies. Bitte beachten Sie, dass `getApplicablePolicies` gibt nur neue Richtlinien zurück, die noch nicht festgelegt wurden. Am Ende muss die Richtlinie zurückgeschrieben und Änderungen müssen beibehalten werden.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

AccessControlPolicyIterator it = acMgr.getApplicablePolicies(path);
while (it.hasNext()) {
        AccessControlPolicy policy = it.nextAccessControlPolicy();
        if (policy instanceof PrincipalSetPolicy) {
           cugPolicy = (PrincipalSetPolicy) policy;
           break;
        }
}

if (cugPolicy == null) {
   log.debug("no applicable policy"); // path not supported or no applicable policy (e.g.
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### Vorhandene CUG-Richtlinie bearbeiten {#edit-an-existing-cug-policy}

Die folgenden Schritte sind erforderlich, um eine vorhandene CUG-Richtlinie zu bearbeiten. Beachten Sie, dass die geänderte Richtlinie zurückgeschrieben werden muss und Änderungen beibehalten werden müssen, indem Sie `javax.jcr.Session.save()`.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
     if (policy instanceof PrincipalSetPolicy) {
        cugPolicy = (PrincipalSetPolicy) policy;
        break;
     }
}

if (cugPolicy == null) {
   log.debug("no policy to edit"); // path not supported or policy not set before
   return;
}

if (cugPolicy.addPrincipals(toAdd1, toAdd2) || cugPolicy.removePrincipals(toRemove)) {
   acMgr.setPolicy(path, cugPolicy);
   session.save();
} else {
     log.debug("cug policy not modified");
}
```

### Effektive CUG-Richtlinien abrufen {#retrieve-effective-cug-policies}

Die JCR-Zugriffssteuerungsverwaltung definiert eine optimale Methode zum Abrufen der Richtlinien, die an einem gegebenen Pfad wirksam sind. Da die Auswertung von CUG-Richtlinien bedingt ist und von der entsprechenden Konfiguration abhängt, die aktiviert werden muss, wird `getEffectivePolicies` ist eine praktische Methode, um zu überprüfen, ob eine bestimmte CUG-Richtlinie in einer bestimmten Installation wirksam wird.

>[!NOTE]
>
>Bitte beachten Sie den Unterschied zwischen `getEffectivePolicies` und das nachfolgende Codebeispiel, das die Hierarchie führt, um zu ermitteln, ob ein bestimmter Pfad bereits Teil einer vorhandenen CUG ist.

```java
String path = [...] // needs to be a supported, absolute path

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

// log an debug message of all CUG policies that take effect at the given path
// there could be zero, one or many (creating nested CUGs is possible)
for (AccessControlPolicy policy : acMgr.getEffectivePolicies(path) {
     if (policy instanceof PrincipalSetPolicy) {
        String policyPath = "-";
        if (policy instanceof JackrabbitAccessControlPolicy) {
           policyPath = ((JackrabbitAccessControlPolicy) policy).getPath();
        }
        log.debug("Found effective CUG for path '{}' at '{}', path, policyPath);
     }
}
```

#### Übernommene CUG-Richtlinien abrufen {#retrieve-inherited-cug-policies}

Suchen aller verschachtelten CUGs, die an einem bestimmten Pfad definiert wurden, gleichgültig, ob sie wirksam sind oder nicht. Weitere Informationen finden Sie im Abschnitt [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

```java
String path = [...]

List<AccessControlPolicy> cugPolicies = new ArrayList<AccessControlPolicy>();
while (isSupportedPath(path)) {
     for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
         if (policy instanceof PrincipalSetPolicy) {
            cugPolicies.add(policy);
         }
      }
      path = (PathUtils.denotesRoot(path)) ? null : PathUtils.getAncestorPath(path, 1);
}
```

#### Verwalten von CUG-Richtlinien nach Prinzipalen {#managing-cug-policies-by-pincipal}

Die durch `JackrabbitAccessControlManager` die die Bearbeitung von Zugriffskontrollrichtlinien durch Prinzipale ermöglichen, werden nicht mit der CUG-Zugriffssteuerungsverwaltung implementiert, da eine CUG-Richtlinie per Definition immer alle Prinzipale betrifft: mit den `PrincipalSetPolicy` erhalten Lesezugriff, während alle anderen Prinzipale daran gehindert werden, Inhalte in der vom Zielknoten definierten Baumstruktur zu lesen.

Die entsprechenden Methoden geben immer ein leeres Richtlinienfeld zurück, aber keine Ausnahmefehler.

### Verwalten der Authentifizierungspflicht {#managing-the-authentication-requirement}

Die Erstellung, Änderung oder Entfernung neuer Authentifizierungsanforderungen wird durch Änderung des effektiven Knotentyps des Zielknotens erreicht. Die optionale Anmeldepfadeigenschaft kann dann mit der normalen JCR-API geschrieben werden.

>[!NOTE]
>
>Die Änderungen an einem bestimmten Zielknoten, die oben erwähnt werden, werden nur dann auf dem Apache Sling Authenticator angezeigt, wenn die `RequirementHandler` wurde konfiguriert und das Ziel ist in den Baumstrukturen enthalten, die von den unterstützten Pfaden definiert werden (siehe Abschnitt Konfigurationsoptionen).
>
>Weitere Informationen finden Sie unter [Zuweisen von Mixin-Knotentypen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Zuweisen von Mixin-Knotentypen) und [Hinzufügen von Knoten und Festlegen von Eigenschaften](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4 Hinzufügen von Knoten und Festlegen von Eigenschaften)

#### Hinzufügen einer neuen Authentifizierungspflicht {#adding-a-new-auth-requirement}

Im Folgenden finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht. Beachten Sie, dass die Anforderung nur beim Apache Sling Authenticator registriert wird, wenn die `RequirementHandler` wurde für den Baum konfiguriert, der den Zielknoten enthält.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Neue Authentifizierungspflicht mit Anmeldepfad hinzufügen {#add-a-new-auth-requirement-with-login-path}

Hier finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht mit einem Anmeldepfad. Beachten Sie, dass die Anforderung und der Ausschluss für den Anmeldepfad nur beim Apache Sling Authenticator registriert werden, wenn die `RequirementHandler` wurde für den Baum konfiguriert, der den Zielknoten enthält.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Vorhandenen Anmeldepfad ändern {#modify-an-existing-login-path}

Im Folgenden finden Sie Schritte zum Ändern eines vorhandenen Anmeldepfads. Die Änderung wird nur beim Apache Sling Authenticator registriert, wenn die `RequirementHandler` wurde für den Baum konfiguriert, der den Zielknoten enthält. Der vorherige Anmeldepfadwert wird aus der Registrierung entfernt. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht ist von dieser Änderung nicht betroffen.

```java
Node targetNode = [...]
String newLoginPath = [...] // STRING property

if (targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", newLoginPath);
   session.save();
} else {
     log.debug("cannot modify login path property; mixin type missing");
}
```

#### Vorhandenen Anmeldepfad entfernen {#remove-an-existing-login-path}

Hier finden Sie Schritte zum Entfernen eines vorhandenen Anmeldepfads. Die Registrierung des Anmeldepfadeintrags wird nur dann aus dem Apache Sling Authenticator entfernt, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht ist nicht betroffen.

```java
Node targetNode = [...]

if (targetNode.hasProperty("granite:loginPath") &&
   targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", null);
   session.save();
} else {
     log.debug("cannot remove login path property; mixin type missing");
}
```

Alternativ erfüllt die unten aufgeführte Methode denselben Zweck:

```java
String path = [...] // absolute path to target node

String propertyPath = PathUtils.concat(path, "granite:loginPath");
if (session.propertyExists(propertyPath)) {
    session.getProperty(propertyPath).remove();
    // or: session.removeItem(propertyPath);
    session.save();
}
```

#### Authentifizierungspflicht entfernen {#remove-an-auth-requirement}

Hier finden Sie Schritte zum Entfernen einer vorhandenen Authentifizierungspflicht. Die Registrierung der Anforderung wird nur dann vom Apache Sling Authenticator aufgehoben, wenn die `RequirementHandler` wurde für den Baum konfiguriert, der den Zielknoten enthält.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Effektive Authentifizierungspflichten abrufen {#retrieve-effective-auth-requirements}

Es gibt keine dedizierte öffentliche API, um alle effektiven Authentifizierungsanforderungen zu lesen, die beim Apache Sling Authenticator registriert sind. Die Liste wird jedoch in der Systemkonsole unter `https://<serveraddress>:<serverport>/system/console/slingauth` unter &quot;**Konfiguration der Authentifizierungspflicht**&quot;.

Die folgende Abbildung zeigt die Authentifizierungspflichten einer AEM -Veröffentlichungsinstanz mit Demoinhalten an. Der hervorgehobene Pfad der Community-Seite zeigt, wie eine von der in diesem Dokument beschriebenen Implementierung hinzugefügte Anforderung im Sling Apache Authenticator dargestellt wird.

>[!NOTE]
>
>In diesem Beispiel wurde die optionale Anmeldepfadeigenschaft nicht festgelegt. Folglich ist beim Authenticator kein zweiter Eintrag registriert.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Effektiven Anmeldepfad abrufen {#retrieve-the-effective-login-path}

Es gibt derzeit keine öffentliche API zum Abrufen des Anmeldepfads, der beim anonymen Zugriff auf eine Ressource, für die eine Authentifizierung erforderlich ist, wirksam wird. Im Abschnitt „Prüfung des Anmeldepfades“ finden Sie weitere Informationen dazu, wie der Anmeldepfad abgerufen wird.

Neben den anhand dieser Funktion definierten Anmeldepfaden gibt es noch andere Wege, die Weiterleitung zur Anmeldung zu definieren. Diese sollten bei der Entwicklung des Inhaltsmodells und der Authentifizierungspflichten einer jeweiligen AEM-Installation immer erwogen werden.

#### Übernommene Authentifizierungspflicht abrufen {#retrieve-the-inherited-auth-requirement}

Wie beim Anmeldepfad gibt es keine öffentlichen APIs zum Abrufen der im Inhalt definierten geerbten Authentifizierungspflichten. Das folgende Beispiel zeigt, wie alle Authentifizierungsanforderungen aufgelistet werden, die mit einer bestimmten Hierarchie definiert wurden, unabhängig davon, ob sie wirksam werden oder nicht. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

>[!NOTE]
>
>Es wird empfohlen, sich sowohl für Authentifizierungsanforderungen als auch für den Anmeldepfad auf den Vererbungsmechanismus zu verlassen und die Erstellung verschachtelter Authentifizierungspflichten zu vermeiden.
>
>Weitere Informationen finden Sie unter [Auswertung und Vererbung der Authentifizierungspflicht](#evaluation-and-inheritance-of-the-authentication-requirement), [Auswertung des Anmeldepfads](#evaluation-of-login-path) und [Best Practices](#best-practices).

```java
String path = [...]
Node node = session.getNode(path);

Map<String, String> authRequirements = new ArrayList<String, String>();
while (isSupported(node)) {
     if (node.isNodeType("granite:AuthenticationRequired")) {
         String loginPath = (node.hasProperty("granite:loginPath") ?
                                     node.getProperty("granite:loginPath").getString() :
                                     "";
        authRequirements.put(node.getPath(), loginPath);
        node = node.getParent();
     }
}
```

### Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht {#combining-cug-policies-and-the-authentication-requirement}

In der folgenden Tabelle finden Sie die gültigen Kombinationen von CUG-Richtlinien und der Authentifizierungspflicht in einer AEM-Instanz, in der aufgrund der Konfiguration beide Module aktiviert sind.

| **Authentifizierung erforderlich** | **Anmeldepfad** | **Eingeschränkter Lesezugriff** | **Erwartete Auswirkungen** |
|---|---|---|---|
| Ja | Ja | Ja | Ein bestimmter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird zur angegebenen Anmeldeseite weitergeleitet. |
| Ja | Nein | Ja | Ein bestimmter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. |
| Ja | Ja | Nein | Ein nicht authentifizierter Benutzer wird zur angegebenen Anmeldeseite weitergeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Ja | Nein | Nein | Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Nein | Nein | Ja | Ein bestimmter authentifizierter oder nicht authentifizierter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird gleich behandelt und nicht zur Anmeldeseite weitergeleitet. |

>[!NOTE]
>
>Die Kombination Authentifizierungspflicht = Ja und Anmeldepfad = Ja wird oben nicht angeführt, da es sich beim Anmeldepfad um eine optionales, mit einer Authentifizierungspflicht verknüpftes Attribut handelt. Das Angeben einer JCR-Eigenschaft mit diesem Namen ohne Hinzufügen des definierten Mixin-Typs hat keine Auswirkungen und wird vom entsprechenden Handler ignoriert.

## OSGi-Komponenten und -Konfiguration {#osgi-components-and-configuration}

Diese Abschnitte bieten einen Überblick über die OSGi-Komponenten und die einzelnen Konfigurationsoptionen, die mit der neuen CUG-Implementierung eingeführt wurden.

Eine umfassende Zuordnung der Konfigurationsoptionen zwischen der alten und der neuen Implementierung finden Sie in der Dokumentation zur CUG-Zuordnung .

### Autorisierung: Einrichtung und Konfiguration {#authorization-setup-and-configuration}

Die neuen Teile für die Autorisierung gehören zum Bundle **Oak CUG Authorization** (`org.apache.jackrabbit.oak-authorization-cug`), das Teil der Standardinstallation von AEM ist. Das Bundle definiert ein separates Berechtigungsmodell, das als zusätzliche Option für die Verwaltung des Lesezugriffs gedacht ist.

#### Einrichten der CUG-Autorisierung {#setting-up-cug-authorization}

Die Einrichtung der CUG-Autorisierung wird im Abschnitt [relevante Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability). Standardmäßig stellt AEM die CUG-Autorisierung in allen Ausführungsmodi bereit. Die schrittweisen Anweisungen können auch verwendet werden, um die CUG-Autorisierung in Installationen zu deaktivieren, die eine andere Autorisierungseinrichtung erfordern.

#### Konfigurieren des Referrer-Filters {#configuring-the-referrer-filter}

Außerdem müssen Sie die [Sling Referrer Filter](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) mit allen Hostnamen, die für den Zugriff auf AEM verwendet werden können; z. B. über CDN, Load Balancer und andere.

Wenn der Referrer-Filter nicht konfiguriert ist, treten Fehler wie der folgende auf, wenn ein Benutzer versucht, sich bei einer CUG-Website anzumelden:

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### Eigenschaften von OSGi-Komponenten {#characteristics-of-osgi-components}

Die folgenden beiden OSGi-Komponenten wurden hinzugefügt, um Authentifizierungspflichten zu definieren und dedizierte Anmeldepfade festzulegen:

* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration`
* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl`

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration**

<table>
 <tbody>
  <tr>
   <td>Bezeichnung</td>
   <td>Apache Jackrabbit Oak CUG-Konfiguration</td>
  </tr>
  <tr>
   <td>Beschreibung</td>
   <td>Autorisierungskonfiguration zum Einrichten und Auswerten von CUG-Berechtigungen.</td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>
    <ul>
     <li><code>cugSupportedPaths</code></li>
     <li><code>cugEnabled</code></li>
     <li><code>configurationRanking</code></li>
    </ul> <p>Siehe auch <a href="#configuration-options">Konfigurationsoptionen</a> unten.</p> </td>
  </tr>
  <tr>
   <td>Konfigurationsrichtlinie</td>
   <td><code>ConfigurationPolicy.REQUIRE</code></td>
  </tr>
  <tr>
   <td>Verweise</td>
   <td><code>CugExclude (ReferenceCardinality.OPTIONAL_UNARY)</code></td>
  </tr>
 </tbody>
</table>

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl**

<table>
 <tbody>
  <tr>
   <td>Bezeichnung</td>
   <td>Apache Jackrabbit Oak CUG Exclude List</td>
  </tr>
  <tr>
   <td>Beschreibung</td>
   <td>Ermöglicht den Ausschluss von Prinzipalen mit den konfigurierten Namen von der CUG-Auswertung.</td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>
    <ul>
     <li><code>principalNames</code></li>
    </ul> <p>Siehe auch den Abschnitt Konfigurationsoptionen unten.</p> </td>
  </tr>
  <tr>
   <td>Konfigurationsrichtlinie</td>
   <td><code>ConfigurationPolicy.REQUIRE</code></td>
  </tr>
  <tr>
   <td>Verweise</td>
   <td>nicht vorhanden</td>
  </tr>
 </tbody>
</table>

#### Konfigurationsoptionen {#configuration-options}

Die wichtigsten Konfigurationsoptionen sind:

* `cugSupportedPaths`: gibt die Teilbäume an, die CUGs enthalten dürfen. Es ist kein Standardwert festgelegt.
* `cugEnabled`: Konfigurationsoption zur Aktivierung der Berechtigungsprüfung für die vorhandenen CUG-Richtlinien.

Die mit dem CUG-Autorisierungsmodul verknüpften verfügbaren Konfigurationsoptionen werden in der [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration) aufgeführt und genauer beschrieben.

#### Ausnehmen von Prinzipalen von der CUG-Prüfung {#excluding-principals-from-cug-evaluation}

Das Ausnehmen einzelner Prinzipale von der CUG-Prüfung wurde aus der vorherigen Implementierung übernommen. Die neue CUG-Autorisierung behandelt dies mit einer dedizierten Schnittstelle namens CugExclude. Apache Jackrabbit Oak 1.4 umfasst eine Standardimplementierung, die einen festen Satz von Prinzipalen sowie eine erweiterte Implementierung umfasst, welche die Konfiguration individueller Prinzipalnamen ermöglicht. Letztere ist in AEM-Veröffentlichungsinstanzen konfiguriert.

Der Standard seit Einführung von AEM 6.3 verhindert, dass die folgenden Prinzipale von CUG-Richtlinien beeinflusst werden:

* Prinzipale mit Administratorrechten (Administratoren, Administratorgruppe)
* Dienstbenutzerprinzipale
* Repository-interne Systemprinzipale

Weitere Informationen finden Sie in der Tabelle im folgenden Abschnitt [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem).

Der Ausschluss der Gruppe &quot;Administratoren&quot;kann in der Systemkonsole im Konfigurationsabschnitt von **Apache Jackrabbit Oak CUG Exclude List**.

Alternativ ist es möglich, eine benutzerdefinierte Implementierung der CugExclude-Schnittstelle bereitzustellen und bereitzustellen, um den Satz ausgeschlossener Prinzipale bei besonderen Bedürfnissen anzupassen. Weitere Informationen finden Sie in der Dokumentation unter [CUG-Pluggabelbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) für Details und eine Beispielimplementierung.

### Authentifizierung: Einrichten und Konfiguration {#authentication-setup-and-configuration}

Die neuen Teile für die Authentifizierung gehören zum Bundle **Adobe Granite Authentication Handler** (`com.adobe.granite.auth.authhandler` Version 5.6.48). Dieses Bundle ist Teil der Standardinstallation von AEM 

Zur Einrichtung des Authentifizierungspflichtersatzes für die veraltete CUG-Unterstützung müssen einige OSGi-Komponenten in einer jeweiligen AEM-Installation vorhanden und aktiv sein. Weitere Informationen finden Sie im Abschnitt **Eigenschaften von OSGi-Komponenten** unten.

>[!NOTE]
>
>Aufgrund der obligatorischen Konfigurationsoption mit dem RequirementHandler sind die zur Authentifizierung gehörigen Teile nur aktiv, falls das Feature durch Angabe eines Satzes unterstützter Pfade aktiviert wurde. Bei einer Standardinstallation von AEM ist das Feature im Autorenausführungsmodus deaktiviert und für „/content“ im Veröffentlichungsausführungsmodus aktiviert.

**Eigenschaften von OSGi-Komponenten**

Die folgenden beiden OSGi-Komponenten wurden hinzugefügt, um Authentifizierungspflichten zu definieren und dedizierte Anmeldepfade festzulegen:

* `com.adobe.granite.auth.requirement.impl.RequirementService`
* `com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler`

**com.adobe.granite.auth.requirement.impl.RequirementService**

<table>
 <tbody>
  <tr>
   <td>Bezeichnung</td>
   <td>-</td>
  </tr>
  <tr>
   <td>Beschreibung</td>
   <td>Dedizierter OSGi-Dienst für Authentifizierungsanforderungen, der einen Beobachter für Inhaltsänderungen registriert, die sich auf die Authentifizierungspflicht auswirken (über das <code>granite:AuthenticationRequirement</code> Mixin-Typ) und Anmeldepfade mit werden für die <code>LoginSelectorHandler</code>. </td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>-</td>
  </tr>
  <tr>
   <td>Konfigurationsrichtlinie</td>
   <td><code>ConfigurationPolicy.OPTIONAL</code></td>
  </tr>
  <tr>
   <td>Verweise</td>
   <td>
    <ul>
     <li><code>RequirementHandler (ReferenceCardinality.MANDATORY_UNARY)</code></li>
     <li><code>Executor (ReferenceCardinality.MANDATORY_UNARY)</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

**com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler**

| Bezeichnung | Adobe Granite-Authentifizierungspflicht und Anmeldungspfad-Handler |
|---|---|
| Beschreibung | `RequirementHandler` -Implementierung, die die Authentifizierungsanforderungen für Apache Sling und den entsprechenden Ausschluss für die zugehörigen Anmeldepfade aktualisiert. |
| Konfigurationseigenschaften | `supportedPaths` |
| Konfigurationsrichtlinie | `ConfigurationPolicy.REQUIRE` |
| Verweise | nicht vorhanden |

#### Konfigurationsoptionen {#configuration-options-1}

Die Teile der CUG-Umschreibung, die für Authentifizierung relevant sind, umfassen nur eine einzelne Konfigurationsoption, die „Adobe Granite Authentication Requirement and Login Path Handler“ zugehörig ist:

**&quot;Authentication Requirement and Login Path Handler&quot;**

<table>
 <tbody>
  <tr>
   <td>Eigenschaft</td>
   <td>Typ</td>
   <td>Standardwert</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><p>Beschriftung = Unterstützte Pfade</p> <p>Name = 'supportedPaths'</p> </td>
   <td>Satz&lt;string&gt;</td>
   <td>-</td>
   <td>Pfade, unter denen Authentifizierungsanforderungen von diesem Handler eingehalten werden. Lassen Sie diese Konfiguration deaktiviert, wenn Sie die <code>granite:AuthenticationRequirement</code> Mixin-Typ zu Knoten, ohne dass sie erzwungen werden (z. B. in Autoreninstanzen). Wenn nicht vorhanden, ist die Funktion deaktiviert. </td>
  </tr>
 </tbody>
</table>

## Standardkonfiguration seit Einführung von AEM 6.3 {#default-configuration-since-aem}

Neue Installationen von AEM verwenden standardmäßig die neuen Implementierungen für die autorisierungs- und authentifizierungsrelevanten Teile des CUG-Features. Die alte Implementierung &quot;Adobe Granite Closed User Group (CUG) Support&quot; ist veraltet und wird standardmäßig in allen AEM Installationen deaktiviert. Stattdessen werden die neuen Implementierungen wie folgt aktiviert:

### Autoreninstanzen {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade `/content` | Die Zugriffssteuerungsverwaltung für CUGpolicies ist aktiviert. |
| CUG-Auswertung aktiviert FALSE | Die Berechtigungsprüfung ist deaktiviert. CUG-Richtlinien sind nicht wirksam. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

>[!NOTE]
>
>Für **Apache Jackrabbit Oak CUG Exclude List** und **Adobe Granite Authentication Requirement and Login Path Handler** ist auf standardmäßigen Autoreninstanzen keine Konfiguration vorhanden.

### Veröffentlichungsinstanzen {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade `/content` | Die Zugriffssteuerungsverwaltung für CUG-Richtlinien wird unter den konfigurierten Pfaden aktiviert. |
| CUG-Prüfung aktiviert TRUE | Die Berechtigungsprüfung wird unter den konfigurierten Pfaden aktiviert. CUG-Richtlinien werden wirksam `Session.save()`. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

| **&quot;Apache Jackrabbit Oak CUG Exclude List&quot;** | **Erklärung** |
|---|---|
| Prinzipalnamen-Administratoren | Schließt den Administratorprinzipal aus der CUG-Auswertung aus. |

| **&quot;Adobe Granite Authentication Requirement and Login Path Handler&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade  `/content` | Authentifizierungsanforderungen, die im Repository mithilfe des `granite:AuthenticationRequired` Mixin-Typ wird unten wirksam `/content` upon `Session.save()`. Sling Authenticator wird aktualisiert. Wird der Mixin-Typ außerhalb der unterstützten Pfade hinzugefügt, so wird dies ignoriert. |

## Deaktivieren der CUG-Autorisierungs- und Authentifizierungspflicht {#disabling-cug-authorization-and-authentication-requirement}

Diese neue Implementierung kann u. U. vollständig deaktiviert werden, falls eine bestimmte Installation keine CUGs nutzt bzw. eine andere Möglichkeit für Authentifizierung und Autorisierung verwendet.

### CUG-Autorisierung deaktivieren {#disable-cug-authorization}

In der Dokumentation zur [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) finden Sie Informationen dazu, wie Sie das CUG-Autorisierungsmodell aus der kombinierten Autorisierungseinrichtung entfernen.

### Authentifizierungspflicht deaktivieren {#disable-the-authentication-requirement}

Zum Deaktivieren der Unterstützung der Authentifizierungspflicht, die vom Modul `granite.auth.authhandler` bereitgestellt wird, muss nur die Konfiguration entfernt werden, die mit **Adobe Granite Authentication Requirement and Login Path Handler** verknüpft ist.

>[!NOTE]
>
>Das Entfernen der Konfiguration hebt die Registrierung des Mixin-Typs nicht auf, der noch immer auf Knoten angewendet wurde, ohne wirksam zu werden.

## Interaktion mit anderen Modulen {#interaction-with-other-modules}

### Apache Jackrabbit-API {#apache-jackrabbit-api}

Die von Apache Jackrabbit definierte API wurde erweitert, um dem neuen Typ von Zugriffssteuerungsrichtlinie zu entsprechen, die vom CUG-Autorisierungsmodell verwendet wird. Seit Version 2.11.0 des `jackrabbit-api` -Modul definiert eine neue Schnittstelle namens `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die sich auf `javax.jcr.security.AccessControlPolicy`.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Der Importmechanismus von Apache Jackrabbit FileVault wurde angepasst, um Zugriffssteuerungsrichtlinien vom Typ `PrincipalSetPolicy`.

### Apache Sling-Inhaltsverteilung {#apache-sling-content-distribution}

Weitere Informationen finden Sie oben im Abschnitt [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault).

### Adobe Granite-Replikation {#adobe-granite-replication}

Das Replikationsmodul wurde etwas angepasst, um in der Lage zu sein, die CUG-Richtlinien zwischen verschiedenen AEM-Instanzen zu replizieren:

* `DurboImportConfiguration.isImportAcl()` wird wörtlich interpretiert und betrifft nur die Richtlinien zur Zugriffskontrolle, die implementieren `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` berücksichtigt diese Konfiguration nur für echte ACLs
* Andere Richtlinien, z. B. vom CUG-Autorisierungsmodell erstellte `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`-Instanzen, werden immer repliziert und die Konfigurationsoption `DurboImportConfiguration.isImportAcl`() wird ignoriert.

Es gibt eine Einschränkung hinsichtlich der Replikation von CUG-Richtlinien. Wenn eine bestimmte CUG-Richtlinie entfernt wird, ohne den entsprechenden Mixin-Knotentyp zu entfernen `rep:CugMixin,` die Entfernung wird bei der Replikation nicht berücksichtigt. Dies wurde korrigiert, indem bei Entfernung einer Richtlinie immer der Mixin-Typ entfernt wird. Die Einschränkung macht sich aber möglicherweise bemerkbar, wenn der Mixin-Typ manuell hinzugefügt wurde.

### Adobe Granite-Authentifizierungs-Handler {#adobe-granite-authentication-handler}

Der Authentifizierungs-Handler **Adobe Granite HTTP Header Authentication Handler** im Bundle `com.adobe.granite.auth.authhandler` verweist auf die Schnittstelle `CugSupport`, die vom selben Modul definiert wird. Sie wird unter bestimmten Bedingungen zur Berechnung des Bereichs verwendet, wobei auf den mit dem Handler konfigurierten Bereich zurückgefallen wird.

Dies wurde angepasst, um den Verweis auf `CugSupport` optional zu machen, um die größtmögliche Abwärtskompatibilität zu erreichen, wenn eine Einrichtung entscheidet, die veraltete Implementierung erneut zu aktivieren. Bei Installationen, die die Implementierung verwenden, wird der Bereich nicht mehr aus der CUG-Implementierung extrahiert, sondern der Bereich wird immer wie definiert angezeigt mit **Adobe Granite HTTP Header Authentication Handler**.

>[!NOTE]
>
>Standardmäßig wird die **Adobe Granite HTTP Header Authentication Handler** wird nur im Veröffentlichungsausführungsmodus mit &quot;Anmeldeseite deaktivieren&quot;konfiguriert ( `auth.http.nologin`) aktiviert ist.

### AEM-Live Copy {#aem-livecopy}

Die Konfiguration von CUGs in Verbindung mit LiveCopy wird im Repository durch Hinzufügen eines zusätzlichen Knotens und einer zusätzlichen Eigenschaft wie folgt dargestellt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide Elemente werden unter dem `cq:Page`. Mit dem aktuellen Design verarbeitet MSM nur Knoten und Eigenschaften, die sich unter der `cq:PageContent` (`jcr:content`).

Daher können CUG-Gruppen nicht in Live Copies aus Blueprints bereitgestellt werden. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Änderungen mit der neuen CUG-Implementierung {#changes-with-the-new-cug-implementation}

Das Ziel dieses Abschnitts besteht darin, einen Überblick über die am CUG-Feature vorgenommenen Änderungen sowie einen Vergleich der alten und der neuen Implementierung zur Verfügung zu stellen. Es werden alle Änderungen aufgeführt, die beeinflussen, wie CUG-Unterstützung konfiguriert wird, und beschrieben, wie und von wem CUGs im Repository-Content verwaltet werden.

### Unterschiede bei der CUG-Einrichtung und -Konfiguration {#differences-in-cug-setup-and-configuration}

Die veraltete OSGi-Komponente **Adobe Granite Closed User Group (CUG) Support** (`com.day.cq.auth.impl.cug.CugSupportImpl`) wurde durch neue Komponenten ersetzt, damit die autorisierungs- und authentifizierungsrelevanten Teile des vorherigen CUG-Features getrennt verwaltet werden können.

## Unterschiede bei der Verwaltung von CUGs im Repository-Inhalt {#differences-in-managing-cugs-in-the-repository-content}

Die folgenden Abschnitte beschreiben die Unterschiede zwischen der alten und der neuen Implementierung aus der Implementierungs- und Sicherheitsperspektive. Die neue Implementierung soll dieselbe Funktionalität zur Verfügung stellen, aber es gibt einige dezente Unterschiede, die Sie kennen sollten, wenn Sie das neue CUG-Feature verwenden.

### Unterschiede bei der Zulassung {#differences-with-regards-to-authorization}

Die wichtigsten Unterschiede aus der Sicht der Zulassung sind in der folgenden Liste zusammengefasst:

**Dedizierter Zugriffssteuerungsinhalt für CUGs**

In der alten Implementierung wurde das standardmäßige Autorisierungsmodell dazu verwendet, die Zugriffssteuerungslistenrichtlinien auf der Veröffentlichungsinstanz zu manipulieren, wobei bestehende ACEs aufgrund der von der CUG erzwungenen Einrichtung ersetzt wurden. Dies wurde durch die Eingabe regulärer JCR-Resteigenschaften ausgelöst, die auf der Veröffentlichungsinstanz interpretiert wurden.

Mit der neuen Implementierung ist die Einrichtung der Zugriffskontrolle des Standardautorisierungsmodells nicht von der Erstellung, Änderung oder Entfernung einer CUG betroffen. Stattdessen wurde eine neue Art von Richtlinie mit dem Namen `PrincipalSetPolicy` wird als zusätzlicher Zugriffssteuerungsinhalt auf den Zielknoten angewendet. Diese zusätzliche Richtlinie ist ein untergeordnetes Element des Zielknotens und ist ein gleichrangiges Element des Standardrichtlinienknotens, falls dieser vorhanden ist.

**Bearbeiten von CUG-Richtlinien in der Zugriffssteuerungsverwaltung**

Dieses Abweichen von JCR-Resteigenschaften hin zu einer dedizierten Zugriffssteuerungsrichtlinie hat Auswirkungen auf die Berechtigung, die zum Erstellen oder Ändern des Autorisierungsteils des CUG-Features benötigt wird. Da dies als Änderung beim Inhalt der Zugriffskontrolle betrachtet wird, ist dies erforderlich `jcr:readAccessControl` und `jcr:modifyAccessControl` -Berechtigungen, um in das Repository geschrieben zu werden. Daher können nur Inhaltsautoren, die zur Änderung der Zugriffssteuerungsinhalte einer Seite berechtigt sind, diese Inhalte einrichten oder ändern. Im Vergleich dazu war in der alten Implementierung die Berechtigung zum Schreiben regulärer JCR-Eigenschaften ausreichend. Dies führt zu einer Berechtigungseskalation.

**Durch eine Richtlinie definierter Zielknoten**

CUG-Richtlinien sollen am JCR-Knoten erstellt werden und die Leseberechtigung für den Teilbaum einschränken. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll.

Beachten Sie, dass das Platzieren der CUG-Richtlinie nur im Knoten jcr:content unterhalb einer bestimmten Seite nur den Zugriff auf den Inhalt s.str einer bestimmten Seite einschränkt, jedoch nicht auf gleichrangigen oder untergeordneten Seiten wirkt. Dies kann ein gültiger Anwendungsfall sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Anwendung detaillierter Zugriffssteuerungsinhalte erlaubt. Sie steht jedoch im Gegensatz zur früheren Implementierung, bei der das Platzieren einer cq:cugEnabled -Eigenschaft auf dem Knoten jcr:content intern dem Seitenknoten neu zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

**Berechtigungsprüfung mit CUG-Richtlinien**

Die Umstellung von der alten CUG-Unterstützung auf ein zusätzliches Autorisierungsmodell verändert die Art und Weise, wie wirksame Leseberechtigungen geprüft werden. Wie im Abschnitt [Jackrabbit-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html), ein bestimmter Prinzipal, der die `CUGcontent` wird nur dann Lesezugriff gewährt, wenn die Berechtigungsprüfung aller im Oak-Repository konfigurierten Modelle Lesezugriff gewährt.

Anders ausgedrückt, bei der Auswertung der wirksamen Berechtigungen werden sowohl die `CUGPolicy` als auch die Standardzugriffssteuerungseinträge berücksichtigt. Lesezugriff auf den CUG-Inhalt wird nur gewährt, wenn beide Richtlinientypen ihn gewähren. In einer standardmäßigen AEM Veröffentlichungsinstallation, bei der Lesezugriff auf die vollständige `/content` -Struktur für alle bestimmt ist, wird die Wirkung der CUG-Richtlinien mit der alten Implementierung übereinstimmen.

**Prüfung nach Bedarf**

Das CUG-Autorisierungsmodell ermöglicht das individuelle Aktivieren von Zugriffssteuerungsverwaltung und Berechtigungsprüfung:

* Zugriffssteuerungsverwaltung wird aktiviert, wenn das Modul über einen oder mehrere unterstützte Pfade verfügt, in denen CUGs erstellt werden können.
* Berechtigungsprüfung wird nur aktiviert, wenn die Option **CUG-Prüfung aktiviert** zusätzlich aktiviert wird.

In der neuen Standardeinrichtung von AEM wird die Prüfung von CUG-Richtlinien nur im Ausführungsmodus „publish“ aktiviert. Zeigen Sie dazu die näheren Informationen zur [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem) an. Dies lässt sich überprüfen, indem die effektiven Richtlinien für einen bestimmten Pfad mit den im Inhalt gespeicherten Richtlinien verglichen werden. Wirksame Richtlinien werden nur angezeigt, wenn die Berechtigungsprüfung für CUGs aktiviert ist.

Wie oben erläutert, werden die CUG-Zugriffssteuerungsrichtlinien jetzt immer im Inhalt gespeichert. Eine Bewertung der effektiven Berechtigungen, die sich aus diesen Richtlinien ergeben, wird jedoch nur dann erzwungen, wenn **CUG-Prüfung aktiviert** ist in der Systemkonsole bei Apache Jackrabbit Oak aktiviert **CUG-Konfiguration.** Standardmäßig ist sie nur mit dem Ausführungsmodus &#39;publish&#39; aktiviert.

### Unterschiede in Bezug auf Authentifizierung {#differences-with-regards-to-authentication}

Im Folgenden werden die Unterschiede im Hinblick auf die Authentifizierung beschrieben.

#### Dedizierter Mixin-Typ für Authentifizierungspflicht {#dedicated-mixin-type-for-authentication-requirement}

In der bisherigen Implementierung wurden die Autorisierungs- und Authentifizierungsaspekte einer CUG durch eine einzelne JCR-Eigenschaft ausgelöst ( `cq:cugEnabled`). Insoweit die Authentifizierung betroffen ist, hat dies zu einer aktualisierten Liste von Authentifizierungspflichten geführt, die in der Apache Sling Authenticator-Implementierung gespeichert werden. Bei der neuen Implementierung wird dasselbe Ergebnis erzielt, indem der Zielknoten mit einem dedizierten Mixin-Typ (`granite:AuthenticationRequired`) markiert wird.

#### Eigenschaft zum Ausnehmen des Anmeldepfades {#property-for-excluding-login-path}

Der Mixin-Typ definiert eine einzelne optionale Eigenschaft mit dem Namen `granite:loginPath`, was im Wesentlichen der `cq:cugLoginPage` -Eigenschaft. Im Gegensatz zur früheren Implementierung wird die Anmeldepfadeigenschaft nur berücksichtigt, wenn ihr deklarierender Knotentyp im Mixin-Typ aufgeführt wird. Wird eine Eigenschaft mit diesem Namen hinzugefügt, ohne den Mixin-Typ festzulegen, hat dies keine Auswirkungen und an den Authenticator werden keine neue Pflicht und keine Ausnahme für den Anmeldepfad gemeldet.

#### Berechtigung für Authentifizierungspflicht {#privilege-for-authentication-requirement}

Zum Hinzufügen oder Entfernen eines Mixin-Typs ist die Berechtigung `jcr:nodeTypeManagement` erforderlich. In der vorherigen Implementierung wird die `jcr:modifyProperties` -Berechtigung zum Bearbeiten der Resteigenschaft verwendet.

Was `granite:loginPath` angeht, wird dieselbe Berechtigung benötigt, um die Eigenschaft hinzuzufügen, zu ändern oder zu entfernen.

#### Vom Mixin-Typ definierter Zielknoten {#target-node-defined-by-mixin-type}

Authentifizierungspflichten sollen am JCR-Knoten erstellt werden und die Authentifizierungspflicht für den Teilbaum definieren. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll. Die Benutzeroberfläche für die neue Implementierung fügt den Mixin-Typ „auth-requirement“ konsequent dem Seitenknoten hinzu.

Wenn Sie die CUG-Richtlinie nur auf den Knoten jcr:content platzieren, der sich unter einer bestimmten Seite befindet, wird der Zugriff auf den Inhalt nur eingeschränkt, jedoch nicht auf den Seitenknoten selbst oder auf untergeordneten Seiten.

Dies kann ein gültiges Szenario sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Platzierung des Mixin-Typs an allen Knoten ermöglicht. Das Verhalten steht jedoch im Gegensatz zur vorherigen Implementierung, bei der das Platzieren einer Eigenschaft cq:cugEnabled oder cq:cugLoginPage auf dem Knoten jcr:content intern auf den Seitenknoten neu zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

#### Konfigurierte unterstützte Pfade {#configured-supported-paths}

Beide `granite:AuthenticationRequired` Mixin-Typ und die Eigenschaft granite:loginPath werden nur innerhalb des durch den Satz von **Unterstützte Pfade** -Konfigurationsoption, die bei der **Adobe Granite-Authentifizierungspflicht und Anmeldungspfad-Handler**. Wenn keine Pfade festgelegt werden, wird das Authentifizierungspflicht-Feature komplett deaktiviert. In diesem Fall werden der Mixin-Typ und die Eigenschaft wirksam, wenn sie hinzugefügt oder auf einen bestimmten JCR-Knoten festgelegt werden.

### Zuordnen von JCR-Inhalt, OSGi-Diensten und Konfigurationen {#mapping-of-jcr-content-osgi-services-and-configurations}

Das folgende Dokument bietet eine umfassende Zuordnung von OSGi-Diensten, Konfigurationen und Repository-Inhalten zwischen der alten und der neuen Implementierung.

CUG-Zuordnung seit Einführung von AEM 6.3

[Datei herunterladen](assets/cug-mapping.pdf)

## Aktualisieren der CUG {#upgrade-cug}

### Bestehende Installationen, welche die veraltete CUG verwenden {#existing-installations-using-the-deprecated-cug}

Die alte CUG-Unterstützungsimplementierung ist veraltet und wird aus zukünftigen Versionen entfernt. Es wird empfohlen, bei der Aktualisierung von Versionen vor AEM 6.3 auf die neuen Implementierungen umzustellen.

Bei aktualisierten AEM-Installationen darf nur eine CUG-Implementierung aktiviert sein. Die Kombination der neuen und der veralteten CUG-Unterstützung wurde nicht getestet und verursacht wahrscheinlich ein unerwartetes Verhalten:

* Kollisionen im Sling Authenticator in Bezug auf Authentifizierungspflichten
* Verweigerter Lesezugriff, wenn die mit der alten CUG verknüpfte ACL-Einrichtung mit einer neuen CUG-Richtlinie kollidiert

### Migrieren vorhandener CUG-Inhalte {#migrating-existing-cug-content}

Adobe stellt ein Tool für die Migration zur neuen CUG-Implementierung zur Verfügung. Sie müssen die folgenden Schritte ausführen, um es zu verwenden:

1. Navigieren Sie zu `https://<serveraddress>:<serverport>/system/console/cug-migration` , um auf das Tool zuzugreifen.
1. Geben Sie den Stammpfad ein, auf den Sie CUGs überprüfen möchten, und klicken Sie auf die Schaltfläche **Probelauf durchführen**. Dadurch wird nach CUGs gesucht, die für die Konvertierung am ausgewählten Speicherort infrage kommen.
1. Klicken Sie nach der Prüfung der Ergebnisse auf die Schaltfläche **Migration durchführen**, um zur neuen Implementierung zu migrieren.

>[!NOTE]
>
>Wenn Probleme auftreten, können Sie eine bestimmte Protokollfunktion unter **DEBUG** Ebene auf `com.day.cq.auth.impl.cug` , um die Ausgabe des Migrationstools zu erhalten. Weitere Informationen dazu finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
