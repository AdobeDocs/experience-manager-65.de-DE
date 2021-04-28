---
title: Geschlossene Benutzergruppen in AEM
seo-title: Geschlossene Benutzergruppen in AEM
description: Hier erfahren Sie mehr über geschlossene Benutzergruppen in AEM.
seo-description: Hier erfahren Sie mehr über geschlossene Benutzergruppen in AEM.
uuid: 83396163-86ce-406b-b797-2457ed975ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: a2bd7045-970f-4245-ad5d-a272a654df0a
docset: aem65
exl-id: 39e35a07-140f-4853-8f0d-8275bce27a65
feature: Sicherheit
translation-type: tm+mt
source-git-commit: cb4b0cb60b8709beea3da70495a15edc8c4831b8
workflow-type: tm+mt
source-wordcount: '6886'
ht-degree: 61%

---

# Geschlossene Benutzergruppen in AEM{#closed-user-groups-in-aem}

## Einführung {#introduction}

Seit Einführung von AEM 6.3 gibt es eine neue Implementierung des Features „Geschlossene Benutzergruppe“, welche die Probleme hinsichtlich der Leistung, Skalierbarkeit und Sicherheit der bestehenden Implementierung beheben soll.

>[!NOTE]
>
>Der Einfachheit halber wird das Feature im Rahmen dieser Dokumentation als „CUG“ abgekürzt (für Closed User Group, geschlossene Benutzergruppe).

Ziel der neuen Implementierung ist es, bestehende Funktionen bei Bedarf abzudecken und gleichzeitig Probleme und Designbeschränkungen älterer Versionen zu beheben. Das Ergebnis ist eine neue CUG-Version mit den folgenden Eigenschaften:

* Deutliche Trennung der Authentifizierungs- und Autorisierungselemente, die einzeln oder in Kombination eingesetzt werden können
* Dediziertes Autorisierungsmodell, das eingeschränkten Lesezugriff auf die konfigurierten CUG-Baumstrukturen bietet, ohne andere Einrichtungs- und Erlaubnisanforderungen für die Zugriffskontrolle zu beeinträchtigen
* Trennung zwischen der Einrichtung der Zugriffskontrolle für den eingeschränkten Lesezugriff, die normalerweise in Autoreninstanzen benötigt wird, und der Berechtigungsüberprüfung, die normalerweise nur bei der Veröffentlichung gewünscht wird;
* Bearbeiten des eingeschränkten Lesezugriffs ohne Berechtigungseskalation
* Dedizierte Knotentyperweiterung zur Markierung der Authentifizierungspflicht
* Optionaler, der Authentifizierungspflicht zugehöriger Anmeldepfad

### Die neue benutzerdefinierte Benutzergruppenimplementierung {#the-new-custom-user-group-implementation}

Eine CUG besteht im Kontext von AEM aus den folgenden Schritten:

* Schränken Sie den Lesezugriff auf die Baumstruktur ein, die geschützt werden muss, und gewähren Sie nur Prinzipalen Lesezugriff, die entweder mit einer gegebenen CUG-Instanz aufgeführt oder in der CUG-Prüfung nicht berücksichtigt werden. Dies wird als Element der **Autorisierung** bezeichnet.
* Erzwingen Sie die Authentifizierung bei einer gegebenen Baumstruktur und geben Sie optional eine dedizierte Anmeldeseite für die Struktur an, die daraufhin ausgeschlossen wird. Dies wird als Element der **Authentifizierung** bezeichnet.

Die neue Implementierung unterscheidet zwischen Autorisierungselementen und Authentifizierungselementen. Seit AEM 6.3 ist es möglich, den Lesezugriff zu beschränken, ohne eine Authentifizierungspflicht hinzufügen. Dies ist beispielsweise gebräuchlich, wenn eine bestimmte Instanz eine vollständige Authentifizierung anfordert oder eine gegebene Baumstruktur bereits in einem Teilbaum vorhanden ist, der bereits eine Authentifizierung anfordert.

Ebenso kann eine bestimmte Struktur mit einer Authentifizierungsanforderung versehen werden, ohne dass die effektive Berechtigungseinstellung geändert werden muss. Die Kombinationen und die Ergebnisse werden im Abschnitt [Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) aufgeführt.

## Überblick {#overview}

### Autorisierung: Beschränken des Lesezugriffs {#authorization-restricting-read-access}

Das zentrale Feature einer CUG besteht in der Einschränkung des Lesezugriffs auf eine bestimmte Baumstruktur im Content-Repository für alle außer ausgewählte Prinzipale. Die neue Implementierung manipuliert nicht spontan die Standardinhalte der Zugriffssteuerung, sondern definiert einen dedizierten Typ von Zugriffssteuerungsrichtlinie, der eine CUG darstellt.

#### Zugriffssteuerungsrichtlinie für CUG  {#access-control-policy-for-cug}

Dieser neue Typ von Richtlinie weist die folgenden Eigenschaften auf:

* Zugriffskontrolle policy of type org.apache.jackrabbit.api.security.approval.PrincipalSetPolicy (durch die Apache Jackrabbit API definiert);
* PrincipalSetPolicy gewährt Privilegien für einen veränderbaren Satz von Prinzipalen.
* Die erteilten Berechtigungen und der Umfang dieser Richtlinie sind ein Implementierungsdetail.

Die Implementierung von PrincipalSetPolicy zur Darstellung von CUGs definiert außerdem Folgendes:

* CUG-Richtlinien gewähren nur Lesezugriff auf reguläre JCR-Elemente (beispielsweise sind Zugriffssteuerungsinhalte ausgeschlossen).
* Der Umfang wird durch den zugriffsgesteuerten Knoten definiert, der die CUG-Richtlinie enthält.
* CUG-Richtlinien können verschachtelt werden. Eine verschachtelte CUG fängt als neue CUG an, ohne den Prinzipalsatz der übergeordneten CUG zu übernehmen.
* Der Effekt der Richtlinie wird an den gesamten Teilbaum und bis an die nächste verschachtelte CUG weitergegeben.

Diese CUG-Richtlinien werden über ein separates Autorisierungsmodul namens oak-approval-cug in einer AEM Instanz bereitgestellt. Dieses Modul verfügt über eine eigene Zugriffssteuerungsverwaltung und Berechtigungsprüfung. Das heißt, die Standardversion von AEM umfasst eine Oak-Content-Repository-Konfiguration, die mehrere Autorisierungsmechanismen kombiniert. Weitere Informationen finden Sie auf dieser Seite in der Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).[

In diesem Composite-Setup ersetzt ein neues CUG nicht den bestehenden Zugriffskontrolle-Inhalt, der an den Zielgruppe-Knoten angehängt ist, sondern ist als Ergänzung konzipiert, die später auch entfernt werden kann, ohne dass die ursprüngliche Zugriffskontrolle, die standardmäßig in AEM wäre eine Zugriffskontrolle Liste.

Anders als bei der vorherigen Implementierung werden neue CUG-Richtlinien immer als Zugriffssteuerungsinhalt erkannt und behandelt. Dies bedeutet, dass sie mit der JCR-Zugriffssteuerungsverwaltungs-API erstellt und bearbeitet werden. Weitere Informationen finden Sie im Abschnitt [Verwalten von CUG-Richtlinien](#managing-cug-policies).

#### Berechtigungsprüfung von CUG-Richtlinien {#permission-evaluation-of-cug-policies}

Neben einer dedizierten Zugriffssteuerungsverwaltung für CUGs, ermöglicht das neue Autorisierungsmodell bedingt die Aktivierung der Berechtigungsprüfung für seine Richtlinien. Dies ermöglicht die Einrichtung von CUG-Richtlinien in einer Staging-Umgebung. Dabei wird die Prüfung der effektiven Berechtigungen erst aktiviert, wenn sie in die Produktionsumgebung repliziert werden.

Die Berechtigungsprüfung für CUG-Richtlinien und die Interaktion mit dem standardmäßigen oder zusätzlichen Autorisierungsmodellen folgen dem Muster, das für mehrere Autorisierungsmechanismen in Apache Jackrabbit Oak entworfen wurde: Ein gegebener Berechtigungssatz wird gewährt, falls – und nur falls – alle Modelle Zugriff erteilen. Weitere Informationen finden Sie unter [diese Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

Die folgenden Eigenschaften gelten für die Berechtigungsprüfung, die mit dem Autorisierungsmodell verknüpft ist, das CUG-Richtlinien verarbeiten und prüfen soll:

* Sie verarbeitet nur Leseberechtigungen für normale Knoten und Eigenschaften, aber keine Zugriffssteuerungsinhalte.
* Es werden weder Schreibberechtigungen noch Berechtigungen verarbeitet, die für die Änderung von geschützten JCR-Inhalten erforderlich sind (Zugriffskontrolle, Informationen zum Knotentyp, Versionierung, Sperren oder Benutzerverwaltung unter anderem); Diese Berechtigungen sind von einer CUG-Richtlinie nicht betroffen und werden nicht vom zugehörigen Autorisierungsmodell bewertet. Ob diese Berechtigungen gewährt werden, hängt von den anderen Modellen ab, die in der Sicherheitseinrichtung konfiguriert sind.

Die Auswirkungen einer einzelnen CUG-Richtlinie auf die Beurteilung von Genehmigungen lassen sich wie folgt zusammenfassen:

* Lesezugriff wird allen vorenthalten, außer Subjekten, die ausgeschlossene oder aufgeführte Prinzipale enthalten.
* Die Richtlinie gilt für den zugriffsgesteuerten Knoten, der die Richtlinie und ihre Eigenschaften enthält.
* Der Effekt wird zusätzlich in der Hierarchie geerbt - also in der Elementstruktur, die durch den zugriffsgesteuerten Knoten definiert wird.
* Sie betrifft jedoch weder Geschwister noch Vorfahren des zugriffsüberwachten Knotens;
* Die Vererbung einer gegebenen CUG hält an einer verschachtelten CUG an.

#### Best Practices {#best-practices}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition des eingeschränkten Lesezugriffs durch CUGs berücksichtigt werden:

* Entscheiden Sie bewusst, ob Sie die CUG benötigen, um Lesezugriff einzuschränken oder die Authentifizierung zu erzwingen. Im letzteren Fall oder wenn beides erforderlich ist, finden Sie im Abschnitt über bewährte Verfahren Einzelheiten zur Authentifizierungspflicht
* Erstellen Sie ein Bedrohungsmodell für die Daten oder Inhalte, die geschützt werden müssen, um Bedrohungsgrenzen zu identifizieren und ein klares Bild der Empfindlichkeit der Daten und Rollen zu erhalten, die mit autorisiertem Zugriff verbunden sind.
* Modellieren Sie die Repository-Inhalte und CUGs unter Berücksichtigung allgemeiner Aspekte bezüglich der Autorisierung und bewährter Vorgehensweisen:

   * Denken Sie daran, dass Leseberechtigungen nur gewährt werden, wenn eine bestimmte CUG und die Prüfung anderer in der Einrichtung bereitgestellter Module einem bestimmten Subjekt erlauben, ein bestimmtes Repository-Element zu lesen.
   * Vermeiden Sie die Erstellung überflüssiger CUGs, wenn der Lesezugriff bereits von anderen Autorisierungsmodulen eingeschränkt ist.
   * Ein extremer Bedarf an verschachtelten CUGs weist möglicherweise auf Fehler beim Content-Design hin.
   * Ein extrem übermäßiger Bedarf an CUGs (z. B. auf jeder einzelnen Seite) weist möglicherweise darauf hin, dass ein benutzerdefiniertes Autorisierungsmodell besser geeignet wäre, um den Sicherheitsanforderungen der vorliegenden Anwendung und Inhalte gerecht zu werden.

* Beschränken Sie die Pfade mit Unterstützung für CUG-Richtlinien auf einige wenige Baumstrukturen im Repository, um eine optimale Leistung zu ermöglichen. So lassen Sie z. B. nur CUGs unter dem Knoten /content zu, die seit AEM 6.3 als Standardwert geliefert wurden.
* CUG-Richtlinien sind darauf ausgelegt, einem kleinen Prinzipalsatz Lesezugriff zu gewähren. Der Bedarf an einer sehr großen Anzahl an Prinzipalen deutet möglicherweise auf Fehler beim Content- bzw. Anwendungsdesign hin und sollte überdacht werden.

### Authentifizierung: Definieren der Authentifizierungspflicht  {#authentication-defining-the-auth-requirement}

Die Teile des CUG-Features, die für Authentifizierung relevant sind, ermöglichen die Markierung von Baumstrukturen, die Authentifizierung erfordern, und optional die Angabe einer dedizierten Anmeldeseite. In Übereinstimmung mit der vorherigen Version erlaubt die neue Implementierung, Bäume zu markieren, die eine Authentifizierung im Inhalts-Repository erfordern, und die Synchronisierung mit dem `Sling org.apache.sling.api.auth.Authenticator`bedingt zu aktivieren, der für die Durchsetzung der Anforderung verantwortlich ist und zu einer Anmelderessource umgeleitet wird.

Diese Anforderungen werden mit dem Authenticator anhand eines OSGi-Services registriert, der die Registrierungseigenschaft `sling.auth.requirements` zur Verfügung stellt. Diese Eigenschaften werden dann dazu verwendet, die Authentifizierungspflichten dynamisch zu erweitern. Weitere Informationen finden Sie in der [Sling-Dokumentation](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### Definieren der Authentifizierungspflicht mithilfe eines dedizierten Mixin-Typs  {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Aus Sicherheitsgründen ersetzt die neue Implementierung die Verwendung einer verbleibenden JCR-Eigenschaft durch einen dedizierten Mixin-Typ mit dem Namen `granite:AuthenticationRequired`, der eine einzelne optionale Eigenschaft des Typs STRING für den Anmeldepfad `granite:loginPath` definiert. Nur Inhaltsänderungen mit Bezug zu diesem Mixin-Typ führen zur Aktualisierung der beim Apache Sling Authenticator registrierten Anforderungen. Die Änderungen werden bei Beibehaltung vorübergehender Änderungen nachverfolgt und erfordern daher einen `javax.jcr.Session.save()`-Aufruf, um wirksam zu werden.

Dasselbe gilt für die Eigenschaft `granite:loginPath`. Sie wird nur eingehalten, wenn sie durch den Typ der auth-requirements-bezogenen Mixin definiert ist. Wenn Sie eine Resteigenschaft mit diesem Namen auf einem unstrukturierten JCR-Knoten hinzufügen, wird der gewünschte Effekt nicht angezeigt und die Eigenschaft wird von dem für die Aktualisierung der OSGi-Registrierung verantwortlichen Handler ignoriert.

>[!NOTE]
>
>Die Anmeldepfadeigenschaft ist optional und muss nur dann festgelegt werden, wenn die Baumstruktur, welche die Authentifizierung erfordert, nicht auf den Standard oder eine anderweitig übernommene Anmeldeseite zurückfallen kann. Siehe dazu unten die [Prüfung des Anmeldepfads](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path).

#### Registrieren der Authentifizierungspflicht und des Anmeldepfads mit dem Sling Authenticator  {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Da diese Art von Authentifizierungsanforderungen voraussichtlich auf bestimmte Ausführungsmodi und auf eine kleine Untergruppe von Bäumen im Inhalts-Repository beschränkt sein wird, ist die Verfolgung des Anforderungsmixtyps und der Eigenschaften des Anmeldepfads bedingt und an eine entsprechende Konfiguration gebunden, die die unterstützten Pfade definiert (siehe Konfigurationsoptionen unten). Daher lösen nur Änderungen im Rahmen dieser unterstützten Pfade eine Aktualisierung der OSGi-Registrierung aus, anderswo werden der Mixin-Typ und die Eigenschaft ignoriert.

Das standardmäßige AEM-Setup nutzt jetzt diese Konfiguration, indem es ermöglicht, das mixin im Autorenmodus festzulegen, jedoch erst bei der Replikation auf die Veröffentlichungsinstanz wirksam zu machen. Weitere Informationen dazu, wie Sling die Authentifizierungsanforderung durchsetzt, finden Sie unter [diese Seite](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html).

Wenn Sie den Mixin-Typ `granite:AuthenticationRequired` innerhalb der konfigurierten unterstützten Pfade hinzufügen, wird die OSGi-Registrierung des verantwortlichen Handlers mit einem neuen zusätzlichen Eintrag mit der Eigenschaft `sling.auth.requirements` aktualisiert. Wenn eine angegebene Authentifizierungsanforderung die optionale `granite:loginPath`-Eigenschaft angibt, wird der Wert zusätzlich beim Authentifizierer mit dem Präfix &#39;-&#39; registriert, um von der Authentifizierungsanforderung ausgeschlossen zu werden.

#### Auswertung und Vererbung der Authentifizierungsanforderung {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling-Authentifizierungspflichten sollen anhand der Seiten- oder Knotenhierarchie vererbt werden. Die Details der Vererbung und der Prüfung von Authentifizierungspflichten (wie Reihenfolge und Rangfolge) sind ein Implementierungsdetail und werden in diesem Artikel nicht behandelt.

#### Prüfung des Anmeldepfads  {#evaluation-of-login-path}

Die Auswertung des Anmeldepfads und die Umleitung auf die entsprechende Ressource bei der Authentifizierung ist derzeit ein Implementierungsdetails des Authentifizierungshandlers für die Granite-Login-Auswahl ( `com.day.cq.auth.impl.LoginSelectorHandler`) der Adobe, bei dem es sich um einen standardmäßig mit AEM konfigurierten Apache Sling AuthenticationHandler handelt.

Beim Aufrufen von `AuthenticationHandler.requestCredentials` versucht dieser Handler, die Zuordnungsseite zu ermitteln, zu der der Benutzer umgeleitet wird. Dies umfasst die folgenden Schritte:

* Es wird unterschieden, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * aus dem LoginPathProvider, wie durch das neue `com.adobe.granite.auth.requirement.impl.RequirementService` implementiert,
   * von der veralteten CUG-Implementierung
   * aus den mit `LoginSelectorHandler` definierten Zuordnungen von Anmeldeseiten,
   * und schließlich zur Standardanmeldeseite, wie mit `LoginSelectorHandler` definiert.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Die Zielgruppe dieser Dokumentation ist die Auswertung des Anmeldepfads, wie durch die interne `LoginPathProvider` Schnittstelle offen gelegt. Die seit Einführung von AEM 6.3 enthaltene Implementierung verhält sich wie folgt:

* Die Registrierung des Anmeldepfads hängt von der Unterscheidung ab, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * von `LoginPathProvider`, wie durch das neue `com.adobe.granite.auth.requirement.impl.RequirementService` implementiert,
   * von der veralteten CUG-Implementierung
   * aus den mit `LoginSelectorHandler` definierten Zuordnungen der Anmeldeseite,
   * und gehen Sie schließlich zur Standardseite für die Anmeldung zurück, wie mit `LoginSelectorHandler` definiert.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Die durch die neue auth-requirements-Unterstützung in Granite implementierte `LoginPathProvider`-Variable stellt Login-Pfade bereit, die durch die `granite:loginPath`-Eigenschaften definiert werden, die wiederum durch den Mixin-Typ wie oben beschrieben definiert werden. Die Zuordnung des Ressourcenpfads, der den Anmeldepfad und den Eigenschaftswert selbst enthält, wird im Speicher aufbewahrt und wird geprüft, um einen geeigneten Anmeldepfad für andere Knoten in der Hierarchie zu ermitteln.

>[!NOTE]
>
>Die Prüfung wird nur für Anfragen durchgeführt, die mit Ressourcen verknüpft sind, die sich in den konfigurierten unterstützten Pfaden befinden. Für alle anderen Anfragen werden die alternativen Möglichkeiten zum Ermitteln des Anmeldepfads geprüft.

#### Best Practices {#best-practices-1}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition von Authentifizierungspflichten berücksichtigt werden:

* Verschachtelung von Authentifizierungspflichten vermeiden: Eine einzelne „auth-requirement“-Markierung am Anfang einer Baumstruktur sollte ausreichen und wird an den gesamten vom Zielknoten definierten Teilbaum weitergegeben. Zusätzliche Authentifizierungspflichten innerhalb dieser Baumstruktur sind als redundant zu betrachten und führen möglicherweise zu Leistungseinbußen bei der Prüfung der Authentifizierungspflicht in Apache Sling. Aufgrund der Trennung der autorisierungs- und authentifizierungsrelevanten CUG-Bereiche ist es möglich, den Lesezugriff anhand von CUG-Richtlinien oder anderen Richtlinien einzuschränken und gleichzeitig in der gesamten Baumstruktur die Authentifizierung zu erzwingen.
* Projektarchivinhalt, sodass Authentifizierungsanforderungen für den gesamten Baum gelten, ohne verschachtelte Unterbäume erneut von der Anforderung ausschließen zu müssen.
* Zur Vermeidung genauer Angaben und der darauf folgenden Registrierung redundanter Anmeldepfade:

   * sich auf Vererbung verlassen und verschachtelte Anmeldepfade nicht definieren,
   * Legen Sie für den optionalen Anmeldepfad keinen Wert fest, der dem Standardwert oder einem vererbten Wert entspricht.
   * Anwendungsentwickler müssen identifizieren, welche Anmeldepfade in den globalen „login-path“-Konfigurationen (Standard und Zuordnungen) konfiguriert werden müssen, die mit dem `LoginSelectorHandler` verknüpft sind.

## Darstellung im Repository {#representation-in-the-repository}

### CUG-Richtliniendarstellung im Repository {#cug-policy-representation-in-the-repository}

Die Oak-Dokumentation beschreibt, wie die neuen CUG-Richtlinien im Repository-Inhalt widergespiegelt werden. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Authentifizierungspflicht im Repository  {#authentication-requirement-in-the-repository}

Die Notwendigkeit einer separaten Authentifizierung wird im Repository-Inhalt widergespiegelt, wobei ein dedizierter Mixin-Knotentyp auf dem Knoten Zielgruppe platziert wird. Der Mixin-Typ definiert eine optionale Eigenschaft, um für die vom Zielknoten definierte Baumstruktur eine dedizierte Anmeldeseite festzulegen.

Die mit dem Anmeldepfad verknüpfte Seite kann sich innerhalb oder außerhalb dieser Baumstruktur befinden. Sie ist von der Authentifizierungspflicht ausgenommen.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Verwalten von CUG-Richtlinien und der Authentifizierungspflicht  {#managing-cug-policies-and-authentication-requirement}

### Verwalten von CUG-Richtlinien {#managing-cug-policies}

Der neue Typ von Zugriffskontrolle-Richtlinien zur Einschränkung des Lesezugriffs für eine CUG wird mithilfe der JCR-Zugriffskontrolle-Management-API verwaltet und befolgt die mit der [JCR 2.0-Spezifikation](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html) beschriebenen Mechanismen.

#### Neue CUG-Richtlinie erstellen {#set-a-new-cug-policy}

Code für die Anwendung einer neuen CUG-Richtlinie auf einen Knoten, der vorher keinen CUG-Satz aufwies. Beachten Sie, dass `getApplicablePolicies` nur neue Richtlinien zurückgibt, die noch nicht festgelegt wurden. Am Ende muss die Richtlinie zurückgeschrieben und Änderungen müssen beibehalten werden.

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

#### Vorhandene CUG-Richtlinie bearbeiten  {#edit-an-existing-cug-policy}

Die folgenden Schritte sind erforderlich, um eine vorhandene CUG-Richtlinie zu bearbeiten. Bitte beachten Sie, dass die geänderte Richtlinie zurückgeschrieben werden muss und die Änderungen mit `javax.jcr.Session.save()` beibehalten werden müssen.

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

Die JCR-Zugriffssteuerungsverwaltung definiert eine optimale Methode zum Abrufen der Richtlinien, die an einem gegebenen Pfad wirksam sind. Da die Bewertung von CUG-Richtlinien bedingt ist und von der entsprechenden Konfiguration abhängt, ist es eine praktische Möglichkeit, `getEffectivePolicies` aufzurufen, um zu überprüfen, ob eine bestimmte CUG-Richtlinie in einer bestimmten Installation wirksam wird.

>[!NOTE]
>
>Beachten Sie den Unterschied zwischen `getEffectivePolicies` und dem folgenden Codebeispiel, das die Hierarchie aufwärts führt, um zu ermitteln, ob ein bestimmter Pfad bereits Teil eines vorhandenen CUG ist.

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

#### Verwalten von CUG-Richtlinien nach Prinzipalen  {#managing-cug-policies-by-pincipal}

Die von `JackrabbitAccessControlManager` definierten Erweiterungen, die die Bearbeitung von Richtlinien zur Zugriffskontrolle per Prinzipal ermöglichen, werden nicht mit der CUG-Zugriffskontrolle-Verwaltung implementiert, da definitionsgemäß eine CUG-Richtlinie immer alle Prinzipale betrifft: die mit `PrincipalSetPolicy` aufgelisteten werden Lesezugriff gewährt, während alle anderen Prinzipale verhindert werden, Inhalte in der vom Zielgruppe-Knoten definierten Struktur zu lesen.

Die entsprechenden Methoden geben immer ein leeres Richtlinienfeld zurück, aber keine Ausnahmefehler.

### Verwalten der Authentifizierungspflicht  {#managing-the-authentication-requirement}

Das Erstellen, Ändern oder Entfernen neuer Authentifizierungsanforderungen wird durch Ändern des effektiven Knotentyps der Zielgruppe-Node erreicht. Die optionale Anmeldepfadeigenschaft kann dann mit der normalen JCR-API geschrieben werden.

>[!NOTE]
>
>Die oben erwähnten Änderungen an einem bestimmten Zielgruppen-Knoten werden nur dann auf dem Apache Sling Authenticator angezeigt, wenn das `RequirementHandler` konfiguriert wurde und die Zielgruppe in den von den unterstützten Pfaden definierten Bäumen enthalten ist (siehe Konfigurationsoptionen).
>
>Weitere Informationen finden Sie unter [Zuweisen von Mixin-Knotentypen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Zuweisen von Mixin-Knotentypen) und [Hinzufügen von Knoten und Festlegen von Eigenschaften](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4 Hinzufügen von Knoten und Festlegen von Eigenschaften)

#### Hinzufügen einer neuen Authentifizierungspflicht {#adding-a-new-auth-requirement}

Im Folgenden finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht. Beachten Sie, dass die Anforderung nur beim Apache Sling Authenticator registriert wird, wenn `RequirementHandler` für den Baum konfiguriert wurde, der den Knoten Zielgruppe enthält.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Neue Authentifizierungspflicht mit Anmeldepfad hinzufügen {#add-a-new-auth-requirement-with-login-path}

Hier finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht mit einem Anmeldepfad. Beachten Sie, dass die Anforderung und der Ausschluss für den Anmeldepfad nur beim Apache Sling Authenticator registriert werden, wenn `RequirementHandler` für den Baum konfiguriert wurde, der den Knoten Zielgruppe enthält.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Vorhandenen Anmeldepfad ändern {#modify-an-existing-login-path}

Im Folgenden finden Sie Schritte zum Ändern eines vorhandenen Anmeldepfads. Die Änderung wird nur beim Apache Sling Authenticator registriert, wenn das `RequirementHandler` für den Baum konfiguriert wurde, der den Knoten Zielgruppe enthält. Der vorherige Anmeldepfadwert wird aus der Registrierung entfernt. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht ist von dieser Änderung nicht betroffen.

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

#### Vorhandenen Anmeldepfad entfernen  {#remove-an-existing-login-path}

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

#### Authentifizierungspflicht entfernen  {#remove-an-auth-requirement}

Hier finden Sie Schritte zum Entfernen einer vorhandenen Authentifizierungspflicht. Die Anforderung wird vom Apache Sling Authenticator nur dann nicht registriert, wenn `RequirementHandler` für den Baum konfiguriert wurde, der den Knoten Zielgruppe enthält.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Effektive Authentifizierungspflichten abrufen {#retrieve-effective-auth-requirements}

Es gibt keine dedizierte öffentliche API zum Lesen aller wirksamen Authentifizierungsanforderungen, die beim Apache Sling Authenticator registriert sind. Die Liste wird jedoch in der Systemkonsole unter `https://<serveraddress>:<serverport>/system/console/slingauth` unter &quot;**Konfiguration der Authentifizierungsanforderung**&quot;angezeigt.

Die folgende Abbildung zeigt die Authentifizierungspflichten einer AEM -Veröffentlichungsinstanz mit Demoinhalten an. Der hervorgehobene Pfad der Community-Seite zeigt, wie eine von der in diesem Dokument beschriebenen Implementierung hinzugefügte Anforderung im Sling Apache Authenticator dargestellt wird.

>[!NOTE]
>
>In diesem Beispiel wurde die optionale Anmeldepfadeigenschaft nicht festgelegt. Folglich ist beim Authenticator kein zweiter Eintrag registriert.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Effektiven Anmeldepfad abrufen {#retrieve-the-effective-login-path}

Es gibt derzeit keine öffentliche API zum Abrufen des Anmeldepfads, der beim anonymen Zugriff auf eine Ressource, für die eine Authentifizierung erforderlich ist, wirksam wird. Im Abschnitt „Prüfung des Anmeldepfades“ finden Sie weitere Informationen dazu, wie der Anmeldepfad abgerufen wird.

Neben den anhand dieser Funktion definierten Anmeldepfaden gibt es noch andere Wege, die Weiterleitung zur Anmeldung zu definieren. Diese sollten bei der Entwicklung des Inhaltsmodells und der Authentifizierungspflichten einer jeweiligen AEM-Installation immer erwogen werden.

#### Übernommene Authentifizierungspflicht abrufen  {#retrieve-the-inherited-auth-requirement}

Wie beim Anmeldepfad gibt es keine öffentlichen APIs zum Abrufen der im Inhalt definierten geerbten Authentifizierungspflichten. Im folgenden Beispiel wird veranschaulicht, wie alle Authentifizierungsanforderungen, die mit einer bestimmten Hierarchie definiert wurden, unabhängig davon, ob sie wirksam werden oder nicht, Liste werden. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

>[!NOTE]
>
>Es wird empfohlen, sich sowohl für Authentifizierungsanforderungen als auch für den Anmeldepfad auf den Vererbungsmechanismus zu verlassen und die Erstellung verschachtelter Authentifizierungsanforderungen zu vermeiden.
>
>Weitere Informationen finden Sie unter [Bewertung und Vererbung von Authentifizierungsanforderungen](#evaluation-and-inheritance-of-the-authentication-requirement), [Auswertung von Anmeldepfaden](#evaluation-of-login-path) und [Best Practices](#best-practices).

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

| **Authentifizierung erforderlich** | **Anmeldepfad** | **Eingeschränkter Lesezugriff** | **Erwartete Wirkung** |
|---|---|---|---|
| Ja | Ja | Ja | Ein bestimmter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur dann Ansichten vornehmen, wenn eine effektive Berechtigungsbewertung den Zugriff zulässt. Ein nicht authentifizierter Benutzer wird zur angegebenen Anmeldeseite weitergeleitet. |
| Ja | Nein | Ja | Ein bestimmter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur dann Ansichten vornehmen, wenn eine effektive Berechtigungsbewertung den Zugriff zulässt. Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. |
| Ja | Ja | Nein | Ein nicht authentifizierter Benutzer wird zur angegebenen Anmeldeseite weitergeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Ja | Nein | Nein | Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Nein | Nein | Ja | Ein bestimmter authentifizierter oder nicht authentifizierter Benutzer kann die mit der CUG-Richtlinie markierte Unterstruktur nur dann Ansicht werden, wenn eine effektive Berechtigungsbewertung den Zugriff zulässt. Ein nicht authentifizierter Benutzer wird gleich behandelt und nicht zur Anmeldeseite weitergeleitet. |

>[!NOTE]
>
>Die Kombination Authentifizierungspflicht = Ja und Anmeldepfad = Ja wird oben nicht angeführt, da es sich beim Anmeldepfad um eine optionales, mit einer Authentifizierungspflicht verknüpftes Attribut handelt. Das Angeben einer JCR-Eigenschaft mit diesem Namen ohne Hinzufügen des definierten mixin-Typs hat keine Auswirkungen und wird vom entsprechenden Handler ignoriert.

## OSGi-Komponenten und -Konfiguration {#osgi-components-and-configuration}

Diese Abschnitte bieten einen Überblick über die OSGi-Komponenten und die einzelnen Konfigurationsoptionen, die mit der neuen CUG-Implementierung eingeführt wurden.

Eine umfassende Zuordnung der Konfigurationsoptionen zwischen der alten und der neuen Implementierung finden Sie in der CUG-Zuordnungsdokumentation.

### Autorisierung: Einrichtung und Konfiguration {#authorization-setup-and-configuration}

Die neuen Teile für die Autorisierung gehören zum Bundle **Oak CUG Authorization** (`org.apache.jackrabbit.oak-authorization-cug`), das Teil der Standardinstallation von AEM ist. Das Bundle definiert ein separates Berechtigungsmodell, das als zusätzliche Option für die Verwaltung des Lesezugriffs gedacht ist.

#### Einrichten der CUG-Autorisierung  {#setting-up-cug-authorization}

Das Einrichten der CUG-Autorisierung wird im Detail in der [relevanten Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) beschrieben. Standardmäßig stellt AEM die CUG-Autorisierung in allen Ausführungsmodi bereit. Die schrittweisen Anweisungen können auch verwendet werden, um die CUG-Autorisierung in Installationen zu deaktivieren, die eine andere Autorisierungseinrichtung erfordern.

#### Konfigurieren des Referrer-Filters  {#configuring-the-referrer-filter}

Sie müssen außerdem den [Sling-Werber-Filter](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) mit allen Hostnamen konfigurieren, die für den Zugriff auf AEM verwendet werden können. z. B. über CDN, Lastenausgleich und andere.

Wenn der Referrer-Filter nicht konfiguriert ist, treten Fehler wie der folgende auf, wenn ein Benutzer versucht, sich bei einer CUG-Website anzumelden:

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### Eigenschaften von OSGi-Komponenten  {#characteristics-of-osgi-components}

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
   <td>Autorisierungskonfiguration zum Einrichten und Auswerten der CUG-Berechtigungen.</td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>
    <ul>
     <li><code>cugSupportedPaths</code></li>
     <li><code>cugEnabled</code></li>
     <li><code>configurationRanking</code></li>
    </ul> <p>Siehe auch <a href="#configuration-options">Konfigurationsoptionen</a> weiter unten.</p> </td>
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
   <td>Apache Jackrabbit Oak CUG Liste ausschließen</td>
  </tr>
  <tr>
   <td>Beschreibung</td>
   <td>Ermöglicht den Ausschluss von Prinzipalen mit dem/den konfigurierten Namen/en aus der CUG-Bewertung.</td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>
    <ul>
     <li><code>principalNames</code></li>
    </ul> <p>Siehe auch Konfigurationsoptionen unten.</p> </td>
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

#### Ausnehmen von Prinzipalen von der CUG-Prüfung  {#excluding-principals-from-cug-evaluation}

Das Ausnehmen einzelner Prinzipale von der CUG-Prüfung wurde aus der vorherigen Implementierung übernommen. Die neue CUG-Autorisierung deckt dies mit einer dedizierten Schnittstelle namens CugExclude ab. Apache Jackrabbit Oak 1.4 umfasst eine Standardimplementierung, die einen festen Satz von Prinzipalen sowie eine erweiterte Implementierung umfasst, welche die Konfiguration individueller Prinzipalnamen ermöglicht. Letztere ist in AEM-Veröffentlichungsinstanzen konfiguriert.

Der Standard seit Einführung von AEM 6.3 verhindert, dass die folgenden Prinzipale von CUG-Richtlinien beeinflusst werden:

* Prinzipale mit Administratorrechten (Administratoren, Administratorgruppe)
* Dienstbenutzerprinzipale
* Repository-interne Systemprinzipale

Weitere Informationen finden Sie in der Tabelle im folgenden Abschnitt [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem).

Der Ausschluss der Gruppe &quot;Administratoren&quot;kann in der Systemkonsole im Konfigurationsabschnitt von **Apache Jackrabbit Oak CUG Exclude Liste** geändert oder erweitert werden.

Alternativ können Sie eine benutzerdefinierte Implementierung der CugExclude-Schnittstelle bereitstellen und bereitstellen, um die Gruppe ausgeschlossener Prinzipale bei besonderen Bedürfnissen anzupassen. Weitere Informationen und eine Beispielimplementierung finden Sie in der Dokumentation zu [CUG pluggability](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability).

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
   <td>Spezifischer OSGi-Dienst für Authentifizierungsanforderungen, der einen Beobachter für Inhaltsänderungen registriert, die sich auf die Authentifizierungsanforderungen auswirken (durch den Mixin-Typ <code>granite:AuthenticationRequirement</code>), und für Anmeldepfade mit denen die Parameter <code>LoginSelectorHandler</code> offen gelegt werden. </td>
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

| Bezeichnung | Adobe Granite-Authentifizierungsanforderungen und Anmeldungspfad-Handler |
|---|---|
| Beschreibung | `RequirementHandler` Implementierung, die die Apache Sling-Authentifizierungsanforderungen und den entsprechenden Ausschluss für die zugehörigen Anmeldepfade aktualisiert. |
| Konfigurationseigenschaften | `supportedPaths` |
| Konfigurationsrichtlinie | `ConfigurationPolicy.REQUIRE` |
| Verweise | nicht vorhanden |

#### Konfigurationsoptionen {#configuration-options-1}

Die Teile der CUG-Umschreibung, die für Authentifizierung relevant sind, umfassen nur eine einzelne Konfigurationsoption, die „Adobe Granite Authentication Requirement and Login Path Handler“ zugehörig ist:

**„Authentication Requirement and Login Path Handler“**

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
   <td>Set&lt;String&gt;</td>
   <td>-</td>
   <td>Pfade, unter denen Authentifizierungsanforderungen von diesem Handler eingehalten werden. Lassen Sie diese Konfiguration deaktiviert, wenn Sie den Mixin-Typ <code>granite:AuthenticationRequirement</code> zu Knoten hinzufügen möchten, ohne dass diese erzwungen werden (z. B. bei Autoreninstanzen). Wenn nicht vorhanden, ist die Funktion deaktiviert. </td>
  </tr>
 </tbody>
</table>

## Standardkonfiguration seit Einführung von AEM 6.3 {#default-configuration-since-aem}

Neue Installationen von AEM verwenden standardmäßig die neuen Implementierungen für die autorisierungs- und authentifizierungsrelevanten Teile des CUG-Features. Die alte Implementierung „Adobe Granite Closed User Group (CUG) Support“ ist veraltet und wird standardmäßig in allen Installationen von AEM deaktiviert. Stattdessen werden die neuen Implementierungen wie folgt aktiviert:

### Autoreninstanzen {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade `/content` | Zugriffskontrolle-Management für CUGpolicies ist aktiviert. |
| CUG-Test aktiviert FALSE | Die Berechtigungsauswertung ist deaktiviert. CUG-Richtlinien sind nicht wirksam. |
| Rangansicht | 200 | Siehe Oak-Dokumentation. |

>[!NOTE]
>
>Für **Apache Jackrabbit Oak CUG Exclude List** und **Adobe Granite Authentication Requirement and Login Path Handler** ist auf standardmäßigen Autoreninstanzen keine Konfiguration vorhanden.

### Veröffentlichungsinstanzen {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade `/content` | Die Zugriffskontrolle-Verwaltung für CUG-Richtlinien ist unterhalb der konfigurierten Pfade aktiviert. |
| CUG-Bewertung aktiviert TRUE | Die Berechtigungsauswertung ist unterhalb der konfigurierten Pfade aktiviert. CUG-Richtlinien treten mit `Session.save()` in Kraft. |
| Rangansicht | 200 | Siehe Oak-Dokumentation. |

| **&quot;Apache Jackrabbit Oak CUG Ausschließen Liste&quot;** | **Erklärung** |
|---|---|
| Prinzipalnamenadministratoren | Schließt den Administratorprinzipal aus der CUG-Auswertung aus. |

| **&quot;Adobe Granite Authentication Requirement and Login Path Handler&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade `/content` | Die Authentifizierungsanforderungen, die im Repository mithilfe des Mixin-Typs `granite:AuthenticationRequired` definiert sind, werden unter `/content` bei `Session.save()` wirksam. Sling Authenticator wird aktualisiert. Wird der Mixin-Typ außerhalb der unterstützten Pfade hinzugefügt, so wird dies ignoriert. |

## Deaktivieren der CUG-Autorisierungs- und Authentifizierungspflicht {#disabling-cug-authorization-and-authentication-requirement}

Diese neue Implementierung kann u. U. vollständig deaktiviert werden, falls eine bestimmte Installation keine CUGs nutzt bzw. eine andere Möglichkeit für Authentifizierung und Autorisierung verwendet.

### CUG-Autorisierung deaktivieren  {#disable-cug-authorization}

In der Dokumentation zur [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) finden Sie Informationen dazu, wie Sie das CUG-Autorisierungsmodell aus der kombinierten Autorisierungseinrichtung entfernen.

### Authentifizierungspflicht deaktivieren  {#disable-the-authentication-requirement}

Zum Deaktivieren der Unterstützung der Authentifizierungspflicht, die vom Modul `granite.auth.authhandler` bereitgestellt wird, muss nur die Konfiguration entfernt werden, die mit **Adobe Granite Authentication Requirement and Login Path Handler** verknüpft ist.

>[!NOTE]
>
>Das Entfernen der Konfiguration hebt die Registrierung des Mixin-Typs nicht auf, der noch immer auf Knoten angewendet wurde, ohne wirksam zu werden.

## Interaktion mit anderen Modulen  {#interaction-with-other-modules}

### Apache Jackrabbit-API {#apache-jackrabbit-api}

Die von Apache Jackrabbit definierte API wurde erweitert, um dem neuen Typ von Zugriffssteuerungsrichtlinie zu entsprechen, die vom CUG-Autorisierungsmodell verwendet wird. Seit Version 2.11.0 des Moduls `jackrabbit-api` definiert eine neue Schnittstelle namens `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die von `javax.jcr.security.AccessControlPolicy` reicht.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Der Importmechanismus von Apache Jackrabbit FileVault wurde angepasst, um mit Zugriffskontrollen vom Typ `PrincipalSetPolicy` umzugehen.

### Apache Sling-Inhaltsverteilung {#apache-sling-content-distribution}

Weitere Informationen finden Sie oben im Abschnitt [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault).

### Adobe Granite-Replikation  {#adobe-granite-replication}

Das Replikationsmodul wurde etwas angepasst, um in der Lage zu sein, die CUG-Richtlinien zwischen verschiedenen AEM-Instanzen zu replizieren:

* `DurboImportConfiguration.isImportAcl()` wird wörtlich interpretiert und betrifft nur die Zugriffskontrollen, die die Implementierung der  `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` wird diese Konfiguration nur für echte ACLs respektieren
* Andere Richtlinien, z. B. vom CUG-Autorisierungsmodell erstellte `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`-Instanzen, werden immer repliziert und die Konfigurationsoption `DurboImportConfiguration.isImportAcl`() wird ignoriert.

Es gibt eine Einschränkung hinsichtlich der Replikation von CUG-Richtlinien. Wenn eine bestimmte CUG-Richtlinie entfernt wird, ohne den entsprechenden Mixin-Knotentyp `rep:CugMixin,` zu entfernen, wird die Entfernung bei der Replikation nicht übernommen. Dies wurde korrigiert, indem bei Entfernung einer Richtlinie immer der Mixin-Typ entfernt wird. Die Einschränkung macht sich aber möglicherweise bemerkbar, wenn der Mixin-Typ manuell hinzugefügt wurde.

### Adobe Granite-Authentifizierungs-Handler  {#adobe-granite-authentication-handler}

Der Authentifizierungs-Handler **Adobe Granite HTTP Header Authentication Handler** im Bundle `com.adobe.granite.auth.authhandler` verweist auf die Schnittstelle `CugSupport`, die vom selben Modul definiert wird. Sie wird unter bestimmten Bedingungen zur Berechnung des Bereichs verwendet, wobei auf den mit dem Handler konfigurierten Bereich zurückgefallen wird.

Dies wurde angepasst, um den Verweis auf `CugSupport` optional zu machen, um die größtmögliche Abwärtskompatibilität zu erreichen, wenn eine Einrichtung entscheidet, die veraltete Implementierung erneut zu aktivieren. Bei Installationen, die die Implementierung verwenden, wird der Bereich nicht mehr aus der CUG-Implementierung extrahiert, sondern immer der Bereich angezeigt, der mit **Adobe Granite HTTP Header Authentication Handler** definiert wurde.

>[!NOTE]
>
>Standardmäßig ist **Adobe Granite HTTP Header Authentication Handler** nur im Veröffentlichungsausführungsmodus konfiguriert, wobei die Option „Anmeldeseite deaktivieren“ (`auth.http.nologin`) aktiviert ist.

### AEM-Live Copy {#aem-livecopy}

Die Konfiguration von CUGs in Verbindung mit LiveCopy wird im Repository durch den Zusatz eines zusätzlichen Knotens und einer zusätzlichen Eigenschaft wie folgt dargestellt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide Elemente werden unter `cq:Page` erstellt. Beim aktuellen Entwurf verarbeitet MSM nur Knoten und Eigenschaften, die sich unter dem Knoten `cq:PageContent` (`jcr:content`) befinden.

Deshalb können CUG-Gruppen nicht in Live Copies von Blueprints ausgeführt werden. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Änderungen mit der neuen CUG-Implementierung {#changes-with-the-new-cug-implementation}

Das Ziel dieses Abschnitts besteht darin, einen Überblick über die am CUG-Feature vorgenommenen Änderungen sowie einen Vergleich der alten und der neuen Implementierung zur Verfügung zu stellen. Es werden alle Änderungen aufgeführt, die beeinflussen, wie CUG-Unterstützung konfiguriert wird, und beschrieben, wie und von wem CUGs im Repository-Content verwaltet werden.

### Unterschiede bei CUG-Einrichtung und -Konfiguration {#differences-in-cug-setup-and-configuration}

Die veraltete OSGi-Komponente **Adobe Granite Closed User Group (CUG) Support** (`com.day.cq.auth.impl.cug.CugSupportImpl`) wurde durch neue Komponenten ersetzt, damit die autorisierungs- und authentifizierungsrelevanten Teile des vorherigen CUG-Features getrennt verwaltet werden können.

## Unterschiede bei der Verwaltung von CUGs im Repository-Inhalt {#differences-in-managing-cugs-in-the-repository-content}

Die folgenden Abschnitte beschreiben die Unterschiede zwischen der alten und der neuen Implementierung aus der Implementierungs- und Sicherheitsperspektive. Die neue Implementierung soll dieselbe Funktionalität zur Verfügung stellen, aber es gibt einige dezente Unterschiede, die Sie kennen sollten, wenn Sie das neue CUG-Feature verwenden.

### Unterschiede bei der Zulassung {#differences-with-regards-to-authorization}

Die wichtigsten Unterschiede aus der Sicht der Zulassung sind in der nachstehenden Liste zusammengefasst:

**Dedizierter Zugriffssteuerungsinhalt für CUGs**

In der alten Implementierung wurde das standardmäßige Autorisierungsmodell dazu verwendet, die Zugriffssteuerungslistenrichtlinien auf der Veröffentlichungsinstanz zu manipulieren, wobei bestehende ACEs aufgrund der von der CUG erzwungenen Einrichtung ersetzt wurden. Dies wurde durch die Eingabe regulärer JCR-Resteigenschaften ausgelöst, die auf der Veröffentlichungsinstanz interpretiert wurden.

Bei der neuen Implementierung wird die Zugriffskontrolle des Standard-Autorisierungsmodells nicht durch das Erstellen, Ändern oder Entfernen von CUG beeinflusst. Stattdessen wird ein neuer Richtlinientyp mit dem Namen `PrincipalSetPolicy` als zusätzlicher Zugriffskontrolle-Inhalt auf den Knoten Zielgruppe angewendet. Diese zusätzliche Richtlinie ist ein untergeordnetes Element des Zielknotens und ist ein gleichrangiges Element des Standardrichtlinienknotens, falls dieser vorhanden ist.

**Bearbeiten von CUG-Richtlinien in der Zugriffssteuerungsverwaltung**

Dieses Abweichen von JCR-Resteigenschaften hin zu einer dedizierten Zugriffssteuerungsrichtlinie hat Auswirkungen auf die Berechtigung, die zum Erstellen oder Ändern des Autorisierungsteils des CUG-Features benötigt wird. Da dies als Änderung an den Inhalten der Zugriffskontrolle betrachtet wird, sind `jcr:readAccessControl`- und `jcr:modifyAccessControl`-Berechtigungen erforderlich, um in das Repository geschrieben zu werden. Daher können nur Inhaltsautoren, die zur Änderung der Zugriffssteuerungsinhalte einer Seite berechtigt sind, diese Inhalte einrichten oder ändern. Im Vergleich dazu war in der alten Implementierung die Berechtigung zum Schreiben regulärer JCR-Eigenschaften ausreichend. Dies führt zu einer Berechtigungseskalation.

**Durch eine Richtlinie definierter Zielknoten**

CUG-Richtlinien sollen am JCR-Knoten erstellt werden und die Leseberechtigung für den Teilbaum einschränken. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll.

Beachten Sie, dass das Platzieren der CUG-Richtlinie nur am Knoten jcr:content unterhalb einer bestimmten Seite den Zugriff auf den Inhalt s.str einer bestimmten Seite beschränkt, jedoch nicht auf Geschwisterseiten oder untergeordneten Seiten wirksam wird. Dies kann ein gültiger Anwendungsfall sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Anwendung detaillierter Zugriffssteuerungsinhalte erlaubt. Es steht jedoch im Gegensatz zur früheren Implementierung, bei der die Platzierung einer cq:cugEnabled-Eigenschaft auf dem Knoten jcr:content intern dem Seitenknoten neu zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

**Berechtigungsprüfung mit CUG-Richtlinien**

Die Umstellung von der alten CUG-Unterstützung auf ein zusätzliches Autorisierungsmodell verändert die Art und Weise, wie wirksame Leseberechtigungen geprüft werden. Wie in der [Jackrabbit-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) beschrieben, erhält ein bestimmter Prinzipal, der die `CUGcontent`-Ansicht erlaubt, nur Lesezugriff, wenn die Berechtigungsbewertung aller im Oak-Repository konfigurierten Modelle Lesezugriff gewährt.

Anders ausgedrückt, bei der Auswertung der wirksamen Berechtigungen werden sowohl die `CUGPolicy` als auch die Standardzugriffssteuerungseinträge berücksichtigt. Lesezugriff auf den CUG-Inhalt wird nur gewährt, wenn beide Richtlinientypen ihn gewähren. In einer standardmäßigen AEM Veröffentlichungs-Installation, bei der Leserechte auf den kompletten `/content`-Baum gewährt werden, sind die CUG-Richtlinien dieselbe Wirkung wie bei der alten Implementierung.

**Prüfung nach Bedarf**

Das CUG-Autorisierungsmodell ermöglicht das individuelle Aktivieren von Zugriffssteuerungsverwaltung und Berechtigungsprüfung:

* Zugriffssteuerungsverwaltung wird aktiviert, wenn das Modul über einen oder mehrere unterstützte Pfade verfügt, in denen CUGs erstellt werden können.
* Berechtigungsprüfung wird nur aktiviert, wenn die Option **CUG-Prüfung aktiviert** zusätzlich aktiviert wird.

In der neuen Standardeinrichtung von AEM wird die Prüfung von CUG-Richtlinien nur im Ausführungsmodus „publish“ aktiviert. Zeigen Sie dazu die näheren Informationen zur [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem) an. Dies kann überprüft werden, indem die effektiven Richtlinien für einen bestimmten Pfad mit den im Inhalt gespeicherten Richtlinien verglichen werden. Wirksame Richtlinien werden nur angezeigt, wenn die Berechtigungsprüfung für CUGs aktiviert ist.

Wie oben erläutert, werden die CUG-Zugriffskontrollen-Richtlinien jetzt immer im Inhalt gespeichert, aber die Bewertung der effektiven Berechtigungen, die sich aus diesen Richtlinien ergeben, wird nur erzwungen, wenn **CUG Evaluation Enabled** in der Systemkonsole bei Apache Jackrabbit Oak **CUG-Konfiguration aktiviert ist.** Standardmäßig ist sie nur im Ausführungsmodus &quot;Veröffentlichen&quot;aktiviert.

### Unterschiede in Bezug auf Authentifizierung {#differences-with-regards-to-authentication}

Im Folgenden werden die Unterschiede im Hinblick auf die Authentifizierung beschrieben.

#### Dedizierter Mixin-Typ für Authentifizierungspflicht  {#dedicated-mixin-type-for-authentication-requirement}

In der bisherigen Implementierung wurden die Autorisierungs- und Authentifizierungsaspekte einer CUG durch eine einzelne JCR-Eigenschaft ausgelöst ( `cq:cugEnabled`). Insoweit die Authentifizierung betroffen ist, hat dies zu einer aktualisierten Liste von Authentifizierungspflichten geführt, die in der Apache Sling Authenticator-Implementierung gespeichert werden. Bei der neuen Implementierung wird dasselbe Ergebnis erzielt, indem der Zielknoten mit einem dedizierten Mixin-Typ (`granite:AuthenticationRequired`) markiert wird.

#### Eigenschaft zum Ausnehmen des Anmeldepfades {#property-for-excluding-login-path}

Der mixin-Typ definiert eine einzelne optionale Eigenschaft mit dem Namen `granite:loginPath`, die grundsätzlich der Eigenschaft `cq:cugLoginPage` entspricht. Im Gegensatz zur früheren Implementierung wird die Anmeldepfadeigenschaft nur berücksichtigt, wenn ihr deklarierender Knotentyp im Mixin-Typ aufgeführt wird. Wird eine Eigenschaft mit diesem Namen hinzugefügt, ohne den Mixin-Typ festzulegen, hat dies keine Auswirkungen und an den Authenticator werden keine neue Pflicht und keine Ausnahme für den Anmeldepfad gemeldet.

#### Berechtigung für Authentifizierungspflicht  {#privilege-for-authentication-requirement}

Zum Hinzufügen oder Entfernen eines Mixin-Typs ist die Berechtigung `jcr:nodeTypeManagement` erforderlich. In der vorherigen Implementierung wird das `jcr:modifyProperties`-Privileg verwendet, um die Resteigenschaft zu bearbeiten.

Was `granite:loginPath` angeht, wird dieselbe Berechtigung benötigt, um die Eigenschaft hinzuzufügen, zu ändern oder zu entfernen.

#### Vom Mixin-Typ definierter Zielknoten {#target-node-defined-by-mixin-type}

Authentifizierungspflichten sollen am JCR-Knoten erstellt werden und die Authentifizierungspflicht für den Teilbaum definieren. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll. Die Benutzeroberfläche für die neue Implementierung fügt den Mixin-Typ „auth-requirement“ konsequent dem Seitenknoten hinzu.

Wenn Sie die CUG-Richtlinie nur auf dem Knoten jcr:content unterhalb einer bestimmten Seite platzieren, wird der Zugriff auf den Inhalt nur eingeschränkt, jedoch nicht auf dem Seitenknoten selbst oder auf untergeordneten Seiten.

Dies kann ein gültiges Szenario sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Platzierung des Mixin-Typs an allen Knoten ermöglicht. Das Verhalten steht jedoch im Gegensatz zur früheren Implementierung, bei der das Platzieren einer Eigenschaft cq:cugEnabled oder cq:cugLoginPage auf dem Knoten jcr:content intern letztendlich dem Knoten page zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

#### Konfigurierte unterstützte Pfade  {#configured-supported-paths}

Sowohl der Mixin-Typ `granite:AuthenticationRequired` als auch die Granite:loginPath-Eigenschaft werden nur innerhalb des Bereichs beachtet, der durch die Konfigurationsoption **Unterstützte Pfade** definiert wird, die mit der Konfigurationsoption **Adobe Granite Authentication Requirement and Login Path Handler** vorhanden ist. Wenn keine Pfade festgelegt werden, wird das Authentifizierungspflicht-Feature komplett deaktiviert. In diesem Fall werden mixin-Typ und -Eigenschaft wirksam, wenn ein JCR-Knoten hinzugefügt oder auf einen bestimmten JCR-Knoten eingestellt wird.

### Zuordnen von JCR-Inhalt, OSGi-Diensten und Konfigurationen {#mapping-of-jcr-content-osgi-services-and-configurations}

Das nachstehende Dokument bietet eine umfassende Zuordnung von OSGi-Diensten, -Konfigurationen und -Repository-Inhalten zwischen der alten und der neuen Implementierung.

CUG-Zuordnung seit Einführung von AEM 6.3

[Datei laden](assets/cug-mapping.pdf)

## Aktualisieren der CUG {#upgrade-cug}

### Bestehende Installationen, welche die veraltete CUG verwenden {#existing-installations-using-the-deprecated-cug}

Die alte CUG-Unterstützungsimplementierung ist veraltet und wird aus zukünftigen Versionen entfernt. Es wird empfohlen, bei der Aktualisierung von Versionen vor AEM 6.3 auf die neuen Implementierungen umzustellen.

Bei aktualisierten AEM-Installationen darf nur eine CUG-Implementierung aktiviert sein. Die Kombination der neuen und der veralteten CUG-Unterstützung wurde nicht getestet und verursacht wahrscheinlich ein unerwartetes Verhalten:

* Kollisionen im Sling Authenticator in Bezug auf Authentifizierungspflichten
* Verweigerter Lesezugriff, wenn die mit der alten CUG verknüpfte ACL-Einrichtung mit einer neuen CUG-Richtlinie kollidiert

### Migrieren vorhandener CUG-Inhalte {#migrating-existing-cug-content}

Adobe stellt ein Tool für die Migration zur neuen CUG-Implementierung zur Verfügung. Sie müssen die folgenden Schritte ausführen, um es zu verwenden:

1. Gehen Sie zu `https://<serveraddress>:<serverport>/system/console/cug-migration`, um auf das Tool zuzugreifen.
1. Geben Sie den Stammpfad ein, auf den Sie CUGs überprüfen möchten, und klicken Sie auf die Schaltfläche **Probelauf durchführen**. Dadurch wird nach CUGs gesucht, die für eine Konvertierung am ausgewählten Ort infrage kommen.
1. Klicken Sie nach der Prüfung der Ergebnisse auf die Schaltfläche **Migration durchführen**, um zur neuen Implementierung zu migrieren.

>[!NOTE]
>
>Wenn Probleme auftreten, ist es möglich, eine bestimmte Protokollfunktion auf **DEBUG**-Ebene auf `com.day.cq.auth.impl.cug` einzurichten, um die Ausgabe des Migrationswerkzeugs abzurufen. Weitere Informationen dazu finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
