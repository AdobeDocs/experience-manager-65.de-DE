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
ht-degree: 99%

---

# Geschlossene Benutzergruppen in AEM{#closed-user-groups-in-aem}

## Einführung {#introduction}

Seit Einführung von AEM 6.3 gibt es eine neue Implementierung des Features „Geschlossene Benutzergruppe“, welche die Probleme hinsichtlich der Leistung, Skalierbarkeit und Sicherheit der bestehenden Implementierung beheben soll.

>[!NOTE]
>
>Der Einfachheit halber wird das Feature im Rahmen dieser Dokumentation als „CUG“ abgekürzt (für Closed User Group, geschlossene Benutzergruppe).

Das Ziel der neuen Implementierung ist, wo nötig vorhandene Funktionen zu übernehmen, aber gleichzeitig Probleme und entwicklungsbedingte Einschränkungen älterer Versionen zu beheben. Das Ergebnis ist eine neue CUG-Version mit den folgenden Eigenschaften:

* Deutliche Trennung der Authentifizierungs- und Autorisierungselemente, die einzeln oder in Kombination eingesetzt werden können
* Dediziertes Autorisierungsmodell, das eingeschränkten Lesezugriff auf die konfigurierten CUG-Baumstrukturen bietet, ohne andere Einrichtungs- und Erlaubnisanforderungen für die Zugriffskontrolle zu beeinträchtigen
* Trennung zwischen der Einrichtung der Zugriffssteuerung für den eingeschränkten Lesezugriff, der normalerweise auf Autoreninstanzen benötigt wird, und der Berechtigungsprüfung, die normalerweise nur auf Veröffentlichungsinstanzen benötigt wird
* Bearbeiten des eingeschränkten Lesezugriffs ohne Berechtigungseskalation
* Dedizierte Knotentyperweiterung zur Markierung der Authentifizierungspflicht
* Optionaler, der Authentifizierungspflicht zugehöriger Anmeldepfad

### Die neue benutzerdefinierte Benutzergruppenimplementierung {#the-new-custom-user-group-implementation}

Eine CUG besteht im Kontext von AEM aus den folgenden Schritten:

* Schränken Sie den Lesezugriff auf die Baumstruktur ein, die geschützt werden muss, und gewähren Sie nur Prinzipalen Lesezugriff, die entweder mit einer gegebenen CUG-Instanz aufgeführt oder in der CUG-Prüfung nicht berücksichtigt werden. Dies wird als Element der **Autorisierung** bezeichnet.
* Erzwingen Sie die Authentifizierung bei einer gegebenen Baumstruktur und geben Sie optional eine dedizierte Anmeldeseite für die Struktur an, die daraufhin ausgeschlossen wird. Dies wird als Element der **Authentifizierung** bezeichnet.

Die neue Implementierung unterscheidet zwischen Autorisierungselementen und Authentifizierungselementen. Seit AEM 6.3 ist es möglich, den Lesezugriff zu beschränken, ohne eine Authentifizierungspflicht hinzufügen. Dies ist beispielsweise gebräuchlich, wenn eine bestimmte Instanz eine vollständige Authentifizierung anfordert oder eine gegebene Baumstruktur bereits in einem Teilbaum vorhanden ist, der bereits eine Authentifizierung anfordert.

Gleichermaßen kann eine gegebene Baumstruktur mit einer Authentifizierungspflicht markiert werden, ohne die verwendete Berechtigungseinrichtung zu ändern. Die Kombinationen und die Ergebnisse werden im Abschnitt [Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) aufgeführt.

## Übersicht {#overview}

### Autorisierung: Beschränken des Lesezugriffs {#authorization-restricting-read-access}

Das zentrale Feature einer CUG besteht in der Einschränkung des Lesezugriffs auf eine bestimmte Baumstruktur im Content-Repository für alle außer ausgewählte Prinzipale. Die neue Implementierung manipuliert nicht spontan die Standardinhalte der Zugriffssteuerung, sondern definiert einen dedizierten Typ von Zugriffssteuerungsrichtlinie, der eine CUG darstellt.

#### Zugriffssteuerungsrichtlinie für CUG {#access-control-policy-for-cug}

Dieser neue Typ von Richtlinie weist die folgenden Eigenschaften auf:

* Zugriffssteuerungsrichtlinie des Typs „org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy“ (definiert von der Apache Jackrabbit-API).
* PrincipalSetPolicy gewährt einem anpassbaren Satz von Prinzipalen Berechtigungen.
* Die erteilten Berechtigungen und der Umfang dieser Richtlinie sind ein Implementierungsdetail.

Die Implementierung von PrincipalSetPolicy, das zur Darstellung von CUGs verwendet wird, definiert zusätzlich Folgendes:

* CUG-Richtlinien gewähren nur Lesezugriff auf reguläre JCR-Elemente (beispielsweise sind Zugriffssteuerungsinhalte ausgeschlossen).
* Der Umfang wird durch den zugriffsgesteuerten Knoten definiert, der die CUG-Richtlinie enthält.
* CUG-Richtlinien können verschachtelt werden. Eine verschachtelte CUG fängt als neue CUG an, ohne den Prinzipalsatz der übergeordneten CUG zu übernehmen.
* Der Effekt der Richtlinie wird an den gesamten Teilbaum und bis an die nächste verschachtelte CUG weitergegeben.

Diese CUG-Richtlinien werden anhand eines separaten Autorisierungsmoduls namens „oak-authorization-cug“ auf einer AEM-Instanz bereitgestellt. Dieses Modul verfügt über eine eigene Zugriffssteuerungsverwaltung und Berechtigungsprüfung. Das heißt, die Standardversion von AEM umfasst eine Oak-Content-Repository-Konfiguration, die mehrere Autorisierungsmechanismen kombiniert. Weitere Informationen finden Sie auf [dieser Seite auf der Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

In dieser Verbundeinrichtung ersetzen neue CUGs nicht den vorhandenen Zugriffssteuerungsinhalt, der dem Zielknoten angehängt ist, sondern sind als Zusatz entworfen, der später ebenso entfernt werden kann, ohne die ursprüngliche Zugriffssteuerung zu beeinträchtigen, die in AEM standardmäßig eine Zugriffssteuerungsliste darstellen würde.

Anders als bei der vorherigen Implementierung werden neue CUG-Richtlinien immer als Zugriffssteuerungsinhalt erkannt und behandelt. Dies bedeutet, dass sie mit der JCR-Zugriffssteuerungsverwaltungs-API erstellt und bearbeitet werden. Weitere Informationen finden Sie im Abschnitt [Verwalten von CUG-Richtlinien](#managing-cug-policies).

#### Berechtigungsprüfung von CUG-Richtlinien {#permission-evaluation-of-cug-policies}

Neben einer dedizierten Zugriffssteuerungsverwaltung für CUGs, ermöglicht das neue Autorisierungsmodell bedingt die Aktivierung der Berechtigungsprüfung für seine Richtlinien. Dies ermöglicht die Einrichtung von CUG-Richtlinien in einer Staging-Umgebung. Dabei wird die Prüfung der effektiven Berechtigungen erst aktiviert, wenn sie in die Produktionsumgebung repliziert werden.

Die Berechtigungsprüfung für CUG-Richtlinien und die Interaktion mit dem standardmäßigen oder zusätzlichen Autorisierungsmodellen folgen dem Muster, das für mehrere Autorisierungsmechanismen in Apache Jackrabbit Oak entworfen wurde: Ein gegebener Berechtigungssatz wird gewährt, falls – und nur falls – alle Modelle Zugriff erteilen. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

Die folgenden Eigenschaften gelten für die Berechtigungsprüfung, die mit dem Autorisierungsmodell verknüpft ist, das CUG-Richtlinien verarbeiten und prüfen soll:

* Sie verarbeitet nur Leseberechtigungen für normale Knoten und Eigenschaften, aber keine Zugriffssteuerungsinhalte.
* Sie verarbeitet keine Schreibberechtigungen oder irgendwelche Berechtigungen für die Änderung von geschütztem JCR-Inhalt (z. B. Zugriffssteuerung, Knotentypinformationen, Versionierung, Sperren oder Benutzerverwaltung). Diese Berechtigungen sind von CUG-Richtlinien nicht betroffen und werden vom zugehörigen Autorisierungsmodell nicht geprüft. Ob diese Berechtigungen gewährt werden, hängt von den anderen Modellen ab, die in der Sicherheitseinrichtung konfiguriert sind.

Der Effekt einer einzelnen CUG-Richtlinie auf die Berechtigungsprüfung kann wie folgt zusammengefasst werden:

* Lesezugriff wird allen vorenthalten, außer Subjekten, die ausgeschlossene oder aufgeführte Prinzipale enthalten.
* Die Richtlinie wirkt sich auf den Knoten mit Zugriffssteuerung aus, der die Richtlinie und ihre Eigenschaften umfasst.
* Der Effekt wird außerdem in der Hierarchie, also im vom Knoten mit Zugriffssteuerung definierten Elementbaum, nach unten weitergegeben.
* Gleichrangige Elemente oder Vorgänger des Knotens mit Zugriffssteuerung sind nicht betroffen.
* Die Vererbung einer gegebenen CUG hält an einer verschachtelten CUG an.

#### Best Practices {#best-practices}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition des eingeschränkten Lesezugriffs durch CUGs berücksichtigt werden:

* Entscheiden Sie bewusst, ob Sie die CUG benötigen, um Lesezugriff einzuschränken oder die Authentifizierung zu erzwingen. Falls Sie Letzteres oder beides benötigen, finden Sie im Abschnitt „Best Practices“ Details hinsichtlich der Authentifizierungspflicht.
* Erstellen Sie ein Bedrohungsmodell für die Daten oder Inhalte, die geschützt werden müssen, um Bedrohungsgrenzen zu identifizieren und ein klares Bild der Empfindlichkeit der Daten und Rollen zu erhalten, die mit autorisiertem Zugriff verbunden sind.
* Modellieren Sie die Repository-Inhalte und CUGs unter Berücksichtigung allgemeiner Aspekte bezüglich der Autorisierung und bewährter Vorgehensweisen:

   * Denken Sie daran, dass Leseberechtigungen nur gewährt werden, wenn eine bestimmte CUG und die Prüfung anderer in der Einrichtung bereitgestellter Module einem bestimmten Subjekt erlauben, ein bestimmtes Repository-Element zu lesen.
   * Vermeiden Sie die Erstellung überflüssiger CUGs, wenn der Lesezugriff bereits von anderen Autorisierungsmodulen eingeschränkt ist.
   * Ein extremer Bedarf an verschachtelten CUGs weist möglicherweise auf Fehler beim Content-Design hin.
   * Ein extrem übermäßiger Bedarf an CUGs (z. B. auf jeder einzelnen Seite) weist möglicherweise darauf hin, dass ein benutzerdefiniertes Autorisierungsmodell besser geeignet wäre, um den Sicherheitsanforderungen der vorliegenden Anwendung und Inhalte gerecht zu werden.

* Beschränken Sie die Pfade mit Unterstützung für CUG-Richtlinien auf einige wenige Baumstrukturen im Repository, um eine optimale Leistung zu ermöglichen. Lassen Sie CUGs beispielsweise nur unterhalb des Knotens „/content“ zu, wie seit Einführung von AEM 6.3 standardmäßig festgelegt ist.
* CUG-Richtlinien sind darauf ausgelegt, einem kleinen Prinzipalsatz Lesezugriff zu gewähren. Der Bedarf an einer sehr großen Anzahl an Prinzipalen deutet möglicherweise auf Fehler beim Content- bzw. Anwendungsdesign hin und sollte überdacht werden.

### Authentifizierung: Definieren der Authentifizierungspflicht {#authentication-defining-the-auth-requirement}

Die Teile des CUG-Features, die für Authentifizierung relevant sind, ermöglichen die Markierung von Baumstrukturen, die Authentifizierung erfordern, und optional die Angabe einer dedizierten Anmeldeseite. Wie die vorherige Version ermöglicht die neue Implementierung das Markieren von Baumstrukturen, die Authentifizierung erfordern, im Content-Repository sowie die bedingte Aktivierung der Synchronisierung mit dem `Sling org.apache.sling.api.auth.Authenticator`, der für die Durchsetzung der Anforderung und die Weiterleitung an die Anmelderessource verantwortlich ist.

Diese Anforderungen werden mit dem Authenticator anhand eines OSGi-Dienstes registriert, der die Registrierungseigenschaft `sling.auth.requirements` zur Verfügung stellt. Diese Eigenschaften werden dann dazu verwendet, die Authentifizierungspflichten dynamisch zu erweitern. Weitere Informationen finden Sie in der [Sling-Dokumentation](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### Definieren der Authentifizierungspflicht mithilfe eines dedizierten Mixin-Typs {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Aus Sicherheitsgründen ersetzt die neue Implementierung die Verwendung einer übrigen JCR-Eigenschaft durch einen dedizierten Mixin-Typ mit der Bezeichnung `granite:AuthenticationRequired`. Er definiert eine einzelne optionale Eigenschaft des Typs STRING für den Anmeldepfad `granite:loginPath`. Nur Inhaltsänderungen mit Bezug zu diesem Mixin-Typ führen zur Aktualisierung der beim Apache Sling Authenticator registrierten Anforderungen. Die Änderungen werden nachverfolgt, wenn Übergangsänderungen beibehalten werden, daher muss `javax.jcr.Session.save()` aufgerufen werden, damit die Änderungen wirksam werden.

Dasselbe gilt für die Eigenschaft `granite:loginPath`. Sie wird nur berücksichtigt, wenn sie von dem Mixin-Typ definiert wird, der mit der Authentifizierungspflicht zusammenhängt. Wird eine Resteigenschaft mit genau diesem Namen einem nicht strukturierten JCR-Knoten hinzugefügt, hat dies nicht den gewünschten Effekt und die Eigenschaft wird von dem Handler ignoriert, der für die Aktualisierung der OSGi-Registrierung zuständig ist.

>[!NOTE]
>
>Die Anmeldepfadeigenschaft ist optional und muss nur dann festgelegt werden, wenn die Baumstruktur, welche die Authentifizierung erfordert, nicht auf den Standard oder eine anderweitig übernommene Anmeldeseite zurückfallen kann. Siehe dazu unten die [Prüfung des Anmeldepfads](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path).

#### Registrieren der Authentifizierungspflicht und des Anmeldepfads mit dem Sling Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Da diese Art der Authentifizierungspflicht nur auf bestimmte Ausführungsmodi und auf eine kleine Teilmenge von Baumstrukturen innerhalb des Content-Repository beschränkt sein soll, ist das Tracking des Mixin-Typs der Anforderung und der Anmeldepfadeigenschaften eine Bedingung und gebunden an eine entsprechende Konfiguration, welche die unterstützten Pfade definiert (siehe „Konfigurationsoptionen“ weiter unten). Daher lösen nur Änderungen im Rahmen dieser unterstützten Pfade eine Aktualisierung der OSGi-Registrierung aus. Ansonsten werden der Mixin-Typ und die Eigenschaft ignoriert.

Die standardmäßige Einrichtung von AEM nutzt nun diese Konfiguration, indem sie ermöglicht, für den Mixin-Typ den Autorenausführungsmodus festzulegen, ihn aber erst wirksam werden zu lassen, wenn er auf die Veröffentlichungsinstanz repliziert wurde. Auf [dieser Seite](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) finden Sie Einzelheiten dazu, wie Sling die Authentifizierungspflicht durchsetzt.

Indem Sie in den konfigurierten unterstützten Pfaden den Mixin-Typ `granite:AuthenticationRequired` hinzufügen, wird die OSGi-Registrierung des verantwortlichen Handlers mit einem neuen, zusätzlichen Eintrag mit der Eigenschaft `sling.auth.requirements` aktualisiert. Wenn eine gegebene Authentifizierungspflicht die optionale Eigenschaft `granite:loginPath` angibt, wird der Wert zusätzlich beim Authenticator mit dem Präfix „-“ registriert, um von der Authentifizierungspflicht ausgeschlossen zu werden.

#### Prüfung und Vererbung der Authentifizierungspflicht {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling-Authentifizierungspflichten sollen anhand der Seiten- oder Knotenhierarchie vererbt werden. Die Details der Vererbung und der Prüfung von Authentifizierungspflichten (wie Reihenfolge und Rangfolge) sind ein Implementierungsdetail und werden in diesem Artikel nicht behandelt.

#### Prüfung des Anmeldepfads {#evaluation-of-login-path}

Die Prüfung des Anmeldepfads und die Weiterleitung an die entsprechende Ressource bei Authentifizierung sind derzeit Implementierungsdetails von Adobe Granite Login Selector Authentication Handler (`com.day.cq.auth.impl.LoginSelectorHandler`), einem Apache Sling-AuthenticationHandler, der standardmäßig mit AEM konfiguriert ist.

Nach dem Aufruf von `AuthenticationHandler.requestCredentials` versucht dieser Handler, die Zuordnungsanmeldeseite zu identifizieren, an die der Benutzer weitergeleitet wird. Dies umfasst die folgenden Schritte:

* Es wird unterschieden, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom LoginPathProvider (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * Rückgriff auf die standardmäßige Anmeldeseite (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Das Ziel dieser Dokumentation ist die Prüfung des Anmeldepfads, wie er von der internen Schnittstelle `LoginPathProvider` angezeigt wird. Die seit Einführung von AEM 6.3 enthaltene Implementierung verhält sich wie folgt:

* Die Registrierung des Anmeldepfads hängt von der Unterscheidung ab, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Im Falle einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom `LoginPathProvider` (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * Rückgriff auf die standardmäßige Anmeldeseite (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

`LoginPathProvider` zeigt anhand der Implementierung der neuen Authentifizierungspflichtunterstützung in Granite Anmeldepfade, wie sie anhand der `granite:loginPath`-Eigenschaften definiert sind, die wiederum wie oben beschrieben vom Mixin-Typ definiert werden. Die Zuordnung des Ressourcenpfads, der den Anmeldepfad und den Eigenschaftswert selbst enthält, wird im Speicher aufbewahrt und wird geprüft, um einen geeigneten Anmeldepfad für andere Knoten in der Hierarchie zu ermitteln.

>[!NOTE]
>
>Die Prüfung wird nur für Anfragen durchgeführt, die mit Ressourcen verknüpft sind, die sich in den konfigurierten unterstützten Pfaden befinden. Für alle anderen Anfragen werden die alternativen Möglichkeiten zum Ermitteln des Anmeldepfads geprüft.

#### Best Practices {#best-practices-1}

Die folgenden bewährten Vorgehensweisen müssen bei der Definition von Authentifizierungspflichten berücksichtigt werden:

* Verschachtelung von Authentifizierungspflichten vermeiden: Eine einzelne „auth-requirement“-Markierung am Anfang einer Baumstruktur sollte ausreichen und wird an den gesamten vom Zielknoten definierten Teilbaum weitergegeben. Zusätzliche Authentifizierungspflichten innerhalb dieser Baumstruktur sind als redundant zu betrachten und führen möglicherweise zu Leistungseinbußen bei der Prüfung der Authentifizierungspflicht in Apache Sling. Aufgrund der Trennung der autorisierungs- und authentifizierungsrelevanten CUG-Bereiche ist es möglich, den Lesezugriff anhand von CUG-Richtlinien oder anderen Richtlinien einzuschränken und gleichzeitig in der gesamten Baumstruktur die Authentifizierung zu erzwingen.
* Passen Sie Repository-Inhalte so an, dass die Authentifizierungspflicht für die gesamte Baumstruktur gilt, ohne verschachtelte Teilbäume wieder von ihr ausnehmen zu müssen.
* Zur Vermeidung genauer Angaben und der darauf folgenden Registrierung redundanter Anmeldepfade:

   * Nutzen Sie die Vererbung und vermeiden Sie die Definition verschachtelter Anmeldepfade.
   * Legen Sie für den optionalen Anmeldepfad keinen Wert fest, der dem Standardwert oder einem vererbten Wert entspricht.
   * Anwendungsentwickler müssen identifizieren, welche Anmeldepfade in den globalen „login-path“-Konfigurationen (Standard und Zuordnungen) konfiguriert werden müssen, die mit dem `LoginSelectorHandler` verknüpft sind.

## Darstellung im Repository {#representation-in-the-repository}

### CUG-Richtliniendarstellung im Repository {#cug-policy-representation-in-the-repository}

Die Oak-Dokumentation beschreibt, wie die neuen CUG-Richtlinien im Repository-Content dargestellt werden. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Authentifizierungspflicht im Repository {#authentication-requirement-in-the-repository}

Die Notwendigkeit einer separaten Authentifizierungspflicht zeigt sich im Repository-Content anhand eines dedizierten Mixin-Knotentyps am Zielknoten. Der Mixin-Typ definiert eine optionale Eigenschaft, um für die vom Zielknoten definierte Baumstruktur eine dedizierte Anmeldeseite festzulegen.

Die mit dem Anmeldepfad verknüpfte Seite kann sich innerhalb oder außerhalb dieser Baumstruktur befinden. Sie ist von der Authentifizierungspflicht ausgenommen.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Verwalten von CUG-Richtlinien und der Authentifizierungspflicht {#managing-cug-policies-and-authentication-requirement}

### Verwalten von CUG-Richtlinien {#managing-cug-policies}

Der neue Richtlinientyp für die Zugriffssteuerung, mit dem der Lesezugriff für eine CUG eingeschränkt wird, wird mithilfe der JCR-Zugriffssteuerungsverwaltungs-API verwaltet und folgt den Mechanismen, die in der [Beschreibung von JCR 2.0](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) aufgeführt werden.

#### Neue CUG-Richtlinie erstellen {#set-a-new-cug-policy}

Code für die Anwendung einer neuen CUG-Richtlinie auf einen Knoten, der vorher keinen CUG-Satz aufwies. `getApplicablePolicies` gibt nur neue Richtlinien zurück, die noch nie festgelegt wurden. Am Ende muss die Richtlinie zurückgeschrieben und Änderungen müssen beibehalten werden.

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

Die folgenden Schritte sind erforderlich, um eine vorhandene CUG-Richtlinie zu bearbeiten. Die angepasste Richtlinie muss zurückgeschrieben und Änderungen müssen mit `javax.jcr.Session.save()` beibehalten werden.

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

Die JCR-Zugriffssteuerungsverwaltung definiert eine optimale Methode zum Abrufen der Richtlinien, die an einem gegebenen Pfad wirksam sind. Weil die Prüfung von CUG-Richtlinien bedingt ist und davon abhängt, ob die entsprechende Konfiguration aktiviert ist, stellt der Aufruf von `getEffectivePolicies` eine einfache Methode dar, um zu überprüfen, ob eine gegebene CUG-Richtlinie in einer gegebenen Installation wirksam ist.

>[!NOTE]
>
>Zwischen `getEffectivePolicies` und dem folgenden Codebeispiel, das die Hierarchie von unten nach oben betrachtet, um herauszufinden, ob ein gegebener Pfad bereits Teil einer bestehenden CUG ist, bestehen Unterschiede.

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

Die von `JackrabbitAccessControlManager` definierten Erweiterungen, welche die Bearbeitung von Zugriffssteuerungsrichtlinien nach Prinzipalen ermöglichen, werden nicht anhand der CUG-Zugriffssteuerungsverwaltung implementiert, da CUG-Richtlinien per Definition immer alle Prinzipale betreffen: Den mit `PrincipalSetPolicy` aufgeführten Prinzipalen wird Lesezugriff gewährt, während alle anderen Prinzipale in der vom Zielknoten definierten Baumstruktur keine Inhalte lesen können.

Die entsprechenden Methoden geben immer ein leeres Richtlinienfeld zurück, aber keine Ausnahmefehler.

### Verwalten der Authentifizierungspflicht {#managing-the-authentication-requirement}

Sie erstellen, ändern oder entfernen neue Authentifizierungspflichten, indem Sie den effektiven Knotentyp des Zielknotens ändern. Die optionale Anmeldepfadeigenschaft kann dann mit der normalen JCR-API geschrieben werden.

>[!NOTE]
>
>Die oben genannten Änderungen an einem bestimmten Zielknoten werden nur dann im Apache Sling Authenticator übernommen, wenn der `RequirementHandler` konfiguriert und das Ziel in den von den unterstützten Pfaden definierten Baumstrukturen vorhanden ist (siehe Abschnitt „Konfigurationsoptionen“).
>
>Weitere Informationen finden Sie unter [Zuweisen von Mixin-Knotentypen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Assigning Mixin Node Types) und [Hinzufügen von Knoten und Festlegen von Eigenschaften](https://docs.adobe.com/docs/de-DE/spec/jcr/2.0/10_Writing.html#10.4 Hinzufügen von Knoten und Festlegen von Eigenschaften).

#### Hinzufügen einer neuen Authentifizierungspflicht {#adding-a-new-auth-requirement}

Im Folgenden finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht. Die Pflicht wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Neue Authentifizierungspflicht mit Anmeldepfad hinzufügen {#add-a-new-auth-requirement-with-login-path}

Hier finden Sie Schritte zum Erstellen einer neuen Authentifizierungspflicht mit einem Anmeldepfad. Die Pflicht und die Ausnahme für den Anmeldepfad wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Vorhandenen Anmeldepfad ändern {#modify-an-existing-login-path}

Im Folgenden finden Sie Schritte zum Ändern eines vorhandenen Anmeldepfads. Die Änderung wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Der vorherige Anmeldepfadwert wird aus der Registrierung entfernt. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht ist von dieser Änderung nicht betroffen.

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

Hier finden Sie Schritte zum Entfernen einer vorhandenen Authentifizierungspflicht. Die Registrierung der Pflicht wird nur dann aus dem Apache Sling Authenticator entfernt, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Abrufen effektiver Authentifizierungspflichten {#retrieve-effective-auth-requirements}

Es gibt keine dedizierte öffentliche API zum Lesen aller effektiven Authentifizierungspflichten, die beim Apache Sling Authenticator registriert sind. Die Liste wird jedoch in der Systemkonsole unter `https://<serveraddress>:<serverport>/system/console/slingauth` im Abschnitt **Konfiguration der Authentifizierungspflicht** verfügbar gemacht.

Die folgende Abbildung zeigt die Authentifizierungspflichten einer AEM -Veröffentlichungsinstanz mit Demoinhalten an. Der hervorgehobene Pfad der Community-Seite zeigt, wie eine von der in diesem Dokument beschriebenen Implementierung hinzugefügte Anforderung im Sling Apache Authenticator dargestellt wird.

>[!NOTE]
>
>In diesem Beispiel wurde die optionale Anmeldepfadeigenschaft nicht festgelegt. Folglich ist beim Authenticator kein zweiter Eintrag registriert.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Abrufen des effektiven Anmeldepfads {#retrieve-the-effective-login-path}

Derzeit gibt es keine öffentliche API zum Abrufen des Anmeldepfads, der verwendet wird, wenn anonym auf eine Ressource zugegriffen wird, die eine Authentifizierung erfordert. Im Abschnitt „Prüfung des Anmeldepfades“ finden Sie weitere Informationen dazu, wie der Anmeldepfad abgerufen wird.

Neben den anhand dieser Funktion definierten Anmeldepfaden gibt es noch andere Wege, die Weiterleitung zur Anmeldung zu definieren. Diese sollten bei der Entwicklung des Inhaltsmodells und der Authentifizierungspflichten einer jeweiligen AEM-Installation immer erwogen werden.

#### Übernommene Authentifizierungspflicht abrufen {#retrieve-the-inherited-auth-requirement}

Wie beim Anmeldepfad gibt es keine öffentlichen APIs zum Abrufen der im Inhalt definierten geerbten Authentifizierungspflichten. Das folgende Beispiel zeigt, wie alle Authentifizierungspflichten aufgeführt werden, die mit einer bestimmten Hierarchie definiert wurden, unabhängig davon, ob sie wirksam sind oder nicht. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

>[!NOTE]
>
>Es wird empfohlen, den Vererbungsmechanismus sowohl für Authentifizierungspflichten als auch für den Anmeldepfad zu verwenden und die Erstellung verschachtelter Authentifizierungspflichten zu vermeiden.
>
>Weitere Informationen finden Sie in [Prüfung und Vererbung der Authentifizierungspflicht](#evaluation-and-inheritance-of-the-authentication-requirement), [Prüfung des Anmeldepfads](#evaluation-of-login-path) und [Best Practices](#best-practices).

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
| Ja | Ja | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird an die angegebene Anmeldeseite umgeleitet. |
| Ja | Nein | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. |
| Ja | Ja | Nein | Ein nicht authentifizierter Benutzer wird an die angegebene Anmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Ja | Nein | Nein | Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Nein | Nein | Ja | Ein bestimmter authentifizierter oder nicht authentifizierter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird gleich behandelt und nicht zur Anmeldeseite weitergeleitet. |

>[!NOTE]
>
>Die Kombination „Authentifizierungspflicht = Ja“ und „Anmeldepfad = Ja“ wird oben nicht angeführt, da es sich beim Anmeldepfad um eine optionales, mit einer Authentifizierungspflicht verknüpftes Attribut handelt. Wird eine JCR-Eigenschaft mit diesem Namen ohne den definierenden Mixin-Typ angegeben, so hat dies keine Auswirkungen und der entsprechende Handler ignoriert die Eigenschaft.

## OSGi-Komponenten und -Konfiguration {#osgi-components-and-configuration}

Diese Abschnitte bieten einen Überblick über die OSGi-Komponenten und die einzelnen Konfigurationsoptionen, die mit der neuen CUG-Implementierung eingeführt wurden.

In der CUG-Zuordnungsdokumentation finden Sie eine umfassende Aufstellung der Konfigurationsoptionen der alten und der neuen Implementierung.

### Autorisierung: Einrichtung und Konfiguration {#authorization-setup-and-configuration}

Die neuen Teile für die Autorisierung gehören zum Bundle **Oak CUG Authorization** (`org.apache.jackrabbit.oak-authorization-cug`), das Teil der Standardinstallation von AEM ist. Das Bundle definiert ein separates Berechtigungsmodell, das als zusätzliche Option für die Verwaltung des Lesezugriffs gedacht ist.

#### Einrichten der CUG-Autorisierung {#setting-up-cug-authorization}

Das Einrichten der CUG-Autorisierung wird in der [relevanten Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) detailliert beschrieben. Standardmäßig stellt AEM die CUG-Autorisierung in allen Ausführungsmodi bereit. Die schrittweisen Anweisungen können auch verwendet werden, um die CUG-Autorisierung in Installationen zu deaktivieren, die eine andere Autorisierungseinrichtung erfordern.

#### Konfigurieren des Referrer-Filters {#configuring-the-referrer-filter}

Sie müssen außerdem den [Sling Referrer-Filter](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) mit allen Host-Namen konfigurieren, die für den Zugriff auf AEM verwendet werden können, z. B. via CDN oder Lastenausgleich.

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
   <td>Apache Jackrabbit Oak CUG Configuration</td>
  </tr>
  <tr>
   <td>Beschreibung</td>
   <td>Autorisierungskonfiguration zum Einrichten und Prüfen von CUG-Berechtigungen.</td>
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
   <td>Ermöglicht den Ausschluss von Prinzipalen mit den konfigurierten Namen von der CUG-Prüfung.</td>
  </tr>
  <tr>
   <td>Konfigurationseigenschaften</td>
   <td>
    <ul>
     <li><code>principalNames</code></li>
    </ul> <p>Siehe auch den Abschnitt „Konfigurationsoptionen“ unten.</p> </td>
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

Das Ausnehmen einzelner Prinzipale von der CUG-Prüfung wurde aus der vorherigen Implementierung übernommen. Die neue CUG-Autorisierung behandelt dies anhand einer dedizierten Schnittstelle mit der Bezeichnung „CugExclude“. Apache Jackrabbit Oak 1.4 umfasst eine Standardimplementierung, die einen festen Satz von Prinzipalen sowie eine erweiterte Implementierung umfasst, welche die Konfiguration individueller Prinzipalnamen ermöglicht. Letztere ist in AEM-Veröffentlichungsinstanzen konfiguriert.

Der Standard seit Einführung von AEM 6.3 verhindert, dass die folgenden Prinzipale von CUG-Richtlinien beeinflusst werden:

* Prinzipale mit Administratorrechten (Administratoren, Administratorgruppe)
* Dienstbenutzerprinzipale
* Repository-interne Systemprinzipale

Weitere Informationen finden Sie in der Tabelle im folgenden Abschnitt [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem).

Die Ausnahme der Administratorgruppe kann in der Systemkonsole im Konfigurationsabschnitt **Apache Jackrabbit Oak CUG Exclude List** geändert oder erweitert werden.

Alternativ ist es möglich, eine benutzerdefinierte Implementierung der CugExclude-Schnittstelle bereitzustellen, um den Satz ausgenommener Prinzipale im Falle spezieller Anforderungen anzupassen. Weitere Informationen sowie eine Beispielimplementierung finden Sie in der Dokumentation zu [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability).

### Authentifizierung: Einrichtung und Konfiguration {#authentication-setup-and-configuration}

Die neuen Teile für die Authentifizierung gehören zum Bundle **Adobe Granite Authentication Handler** (`com.adobe.granite.auth.authhandler`, Version 5.6.48). Dieses Bundle ist Teil der Standardinstallation von AEM 

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
   <td>Dedizierter OSGi-Dienst für Authentifizierungsanforderungen, der einen Beobachter für Inhaltsänderungen registriert, die sich auf die Authentifizierungspflicht auswirken (über den Mixin-Typ <code>granite:AuthenticationRequirement</code>), und Anmeldepfade werden für <code>LoginSelectorHandler</code> verfügbar gemacht. </td>
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

| Bezeichnung | Adobe Granite Authentication Requirement and Login Path Handler |
|---|---|
| Beschreibung | `RequirementHandler`-Implementierung, die die Authentifizierungsanforderungen für Apache Sling und den entsprechenden Ausschluss für die zugehörigen Anmeldepfade aktualisiert. |
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
   <td><p>Bezeichnung = Unterstützte Pfade</p> <p>Name = „supportedPaths“</p> </td>
   <td>Set&lt;String&gt;</td>
   <td>-</td>
   <td>Pfade, in denen Authentifizierungspflichten von diesem Handler eingehalten werden. Legen Sie diese Konfiguration nicht fest, wenn Sie den Mixin-Typ <code>granite:AuthenticationRequirement</code> Knoten hinzufügen möchten, ohne dass sie erzwungen werden (beispielsweise auf Autoreninstanzen). Wenn nicht vorhanden, ist die Funktion deaktiviert. </td>
  </tr>
 </tbody>
</table>

## Standardkonfiguration seit Einführung von AEM 6.3 {#default-configuration-since-aem}

Neue Installationen von AEM verwenden standardmäßig die neuen Implementierungen für die autorisierungs- und authentifizierungsrelevanten Teile des CUG-Features. Die alte Implementierung &quot;Adobe Granite Closed User Group (CUG) Support&quot; ist veraltet und wird standardmäßig in allen AEM Installationen deaktiviert. Stattdessen werden die neuen Implementierungen wie folgt aktiviert:

### Autoreninstanzen {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Die Zugriffssteuerungsverwaltung für „CUGpolicies“ ist aktiviert. |
| CUG-Prüfung aktiviert: FALSE | Die Berechtigungsprüfung ist deaktiviert. CUG-Richtlinien sind nicht wirksam. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

>[!NOTE]
>
>Für **Apache Jackrabbit Oak CUG Exclude List** und **Adobe Granite Authentication Requirement and Login Path Handler** ist auf standardmäßigen Autoreninstanzen keine Konfiguration vorhanden.

### Veröffentlichungsinstanzen {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Die Zugriffssteuerungsverwaltung für CUG-Richtlinien wird in den konfigurierten Pfaden aktiviert. |
| CUG-Prüfung aktiviert: TRUE | Die Berechtigungsprüfung wird in den konfigurierten Pfaden aktiviert. CUG-Richtlinien werden wirksam bei `Session.save()`. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

| **&quot;Apache Jackrabbit Oak CUG Exclude List&quot;** | **Erklärung** |
|---|---|
| Prinzipalnamen: Admins | Schließt den Administratorprinzipal aus der CUG-Prüfung aus. |

| **&quot;Adobe Granite Authentication Requirement and Login Path Handler&quot;** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Authentifizierungspflichten, die im Repository mithilfe des Mixin-Typs `granite:AuthenticationRequired` definiert wurden, werden in `/content` bei `Session.save()` wirksam. Sling Authenticator wird aktualisiert. Wird der Mixin-Typ außerhalb der unterstützten Pfade hinzugefügt, so wird dies ignoriert. |

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

### Apache Jackrabbit-API {#apache-jackrabbit-api}

Die von Apache Jackrabbit definierte API wurde erweitert, um dem neuen Typ von Zugriffssteuerungsrichtlinie zu entsprechen, die vom CUG-Autorisierungsmodell verwendet wird. Seit Version 2.11.0 definiert das Modul `jackrabbit-api` eine neue Schnittstelle mit der Bezeichnung `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die aus `javax.jcr.security.AccessControlPolicy` hervorgeht.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Der Importmechanismus von Apache Jackrabbit FileVault wurde angepasst, um mit Zugriffssteuerungsrichtlinien des Typs `PrincipalSetPolicy` umgehen zu können.

### Apache Sling-Inhaltsverteilung {#apache-sling-content-distribution}

Weitere Informationen finden Sie oben im Abschnitt [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault).

### Adobe Granite-Replikation {#adobe-granite-replication}

Das Replikationsmodul wurde etwas angepasst, um in der Lage zu sein, die CUG-Richtlinien zwischen verschiedenen AEM-Instanzen zu replizieren:

* `DurboImportConfiguration.isImportAcl()` wird wörtlich interpretiert und betrifft nur Zugriffssteuerungsrichtlinien, die `javax.jcr.security.AccessControlList` implementieren.

* `DurboImportTransformer` respektiert nur diese Konfiguration für echte ACLs.
* Andere Richtlinien, z. B. vom CUG-Autorisierungsmodell erstellte `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`-Instanzen, werden immer repliziert und die Konfigurationsoption `DurboImportConfiguration.isImportAcl`() wird ignoriert.

Es gibt eine Einschränkung hinsichtlich der Replikation von CUG-Richtlinien. Wenn eine CUG-Richtlinie entfernt wird, ohne dass der entsprechende Mixin-Knotentyp `rep:CugMixin,` entfernt wird, wird die Entfernung in der Replikation nicht berücksichtigt. Dies wurde korrigiert, indem bei Entfernung einer Richtlinie immer der Mixin-Typ entfernt wird. Die Einschränkung macht sich aber möglicherweise bemerkbar, wenn der Mixin-Typ manuell hinzugefügt wurde.

### Adobe Granite-Authentifizierungs-Handler {#adobe-granite-authentication-handler}

Der Authentifizierungs-Handler **Adobe Granite HTTP Header Authentication Handler** im Bundle `com.adobe.granite.auth.authhandler` verweist auf die Schnittstelle `CugSupport`, die vom selben Modul definiert wird. Sie wird unter bestimmten Bedingungen zur Berechnung des Bereichs verwendet, wobei auf den mit dem Handler konfigurierten Bereich ausgewichen wird.

Dies wurde angepasst, um den Verweis auf `CugSupport` optional zu machen, um die größtmögliche Abwärtskompatibilität zu erreichen, wenn eine Einrichtung entscheidet, die veraltete Implementierung erneut zu aktivieren. Für Installationen, welche die Implementierung verwenden, wird der Bereich nicht mehr aus der CUG-Implementierung extrahiert, stattdessen wird der Bereich immer als mit **Adobe Granite HTTP Header Authentication Handler** definiert angezeigt.

>[!NOTE]
>
>Standardmäßig wird die **Adobe Granite HTTP Header Authentication Handler** wird nur im Veröffentlichungsausführungsmodus mit &quot;Anmeldeseite deaktivieren&quot;konfiguriert ( `auth.http.nologin`) aktiviert ist.

### AEM Live Copy {#aem-livecopy}

Die Konfiguration von CUGs in Verbindung mit Live Copy wird im Repository durch das Hinzufügen eines zusätzlichen Knotens und einer zusätzlichen Eigenschaft wie folgt dargestellt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide Elemente werden unter `cq:Page` erstellt. Mit dem aktuellen Design verarbeitet MSM nur Knoten und Eigenschaften, die sich unter dem Knoten `cq:PageContent` (`jcr:content`) befinden.

Daher können CUG-Gruppen in Live Copies nicht aus Blueprints bereitgestellt werden. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Änderungen mit der neuen CUG-Implementierung {#changes-with-the-new-cug-implementation}

Das Ziel dieses Abschnitts besteht darin, einen Überblick über die am CUG-Feature vorgenommenen Änderungen sowie einen Vergleich der alten und der neuen Implementierung zur Verfügung zu stellen. Es werden alle Änderungen aufgeführt, die beeinflussen, wie CUG-Unterstützung konfiguriert wird, und beschrieben, wie und von wem CUGs im Repository-Content verwaltet werden.

### Unterschiede bei CUG-Einrichtung und -Konfiguration {#differences-in-cug-setup-and-configuration}

Die veraltete OSGi-Komponente **Adobe Granite Closed User Group (CUG) Support** (`com.day.cq.auth.impl.cug.CugSupportImpl`) wurde durch neue Komponenten ersetzt, damit die autorisierungs- und authentifizierungsrelevanten Teile des vorherigen CUG-Features getrennt verwaltet werden können.

## Unterschiede beim Verwalten von CUGs im Repository-Content {#differences-in-managing-cugs-in-the-repository-content}

Die folgenden Abschnitte beschreiben die Unterschiede zwischen der alten und der neuen Implementierung aus der Implementierungs- und Sicherheitsperspektive. Die neue Implementierung soll dieselbe Funktionalität zur Verfügung stellen, aber es gibt einige dezente Unterschiede, die Sie kennen sollten, wenn Sie das neue CUG-Feature verwenden.

### Unterschiede in Bezug auf Autorisierung {#differences-with-regards-to-authorization}

Im Folgenden finden Sie eine Zusammenfassung der wichtigsten Unterschiede hinsichtlich Autorisierung:

**Dedizierter Zugriffssteuerungsinhalt für CUGs**

In der alten Implementierung wurde das standardmäßige Autorisierungsmodell dazu verwendet, die Zugriffssteuerungslistenrichtlinien auf der Veröffentlichungsinstanz zu manipulieren, wobei bestehende ACEs aufgrund der von der CUG erzwungenen Einrichtung ersetzt wurden. Dies wurde durch die Eingabe regulärer JCR-Resteigenschaften ausgelöst, die auf der Veröffentlichungsinstanz interpretiert wurden.

Bei der neuen Implementierung wird die Zugriffssteuerungseinrichtung des Standardautorisierungsmodells nicht von der Erstellung, Änderung oder Entfernung von CUGs beeinflusst. Stattdessen wird ein neuer Typ von Richtlinie mit der Bezeichnung `PrincipalSetPolicy` als zusätzlicher Zugriffssteuerungsinhalt auf den Zielknoten angewendet. Diese zusätzliche Richtlinie ist ein untergeordnetes Element des Zielknotens und ist ein gleichrangiges Element des Standardrichtlinienknotens, falls dieser vorhanden ist.

**Bearbeiten von CUG-Richtlinien in der Zugriffssteuerungsverwaltung**

Dieses Abweichen von JCR-Resteigenschaften hin zu einer dedizierten Zugriffssteuerungsrichtlinie hat Auswirkungen auf die Berechtigung, die zum Erstellen oder Ändern des Autorisierungsteils des CUG-Features benötigt wird. Da dies eine Modifikation am Zugriffssteuerungsinhalt darstellt, sind die Berechtigungen `jcr:readAccessControl` und `jcr:modifyAccessControl` für das Schreiben in das Repository erforderlich. Daher können nur Inhaltsautoren, die zur Änderung der Zugriffssteuerungsinhalte einer Seite berechtigt sind, diese Inhalte einrichten oder ändern. Im Vergleich dazu war in der alten Implementierung die Berechtigung zum Schreiben regulärer JCR-Eigenschaften ausreichend. Dies führt zu einer Berechtigungseskalation.

**Durch eine Richtlinie definierter Zielknoten**

CUG-Richtlinien sollen am JCR-Knoten erstellt werden und die Leseberechtigung für den Teilbaum einschränken. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll.

Wird die CUG-Richtlinie am Knoten „jcr:content“ unterhalb einer bestimmten Seite platziert, so wird nur der Zugriff auf den Inhalt (im engeren Sinn) einer bestimmten Seite eingeschränkt, wobei die Richtlinie keine Auswirkungen auf gleichrangige oder untergeordnete Seiten hat. Dies kann ein gültiger Anwendungsfall sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Anwendung detaillierter Zugriffssteuerungsinhalte erlaubt. In der früheren Implementierung wurde eine auf dem Knoten „jcr:content“ platzierte Eigenschaft „cq:cugEnabled“ intern dem Seitenknoten zugeordnet. Diese Zuordnung wird nicht mehr durchgeführt.

**Berechtigungsprüfung mit CUG-Richtlinien**

Die Umstellung von der alten CUG-Unterstützung auf ein zusätzliches Autorisierungsmodell verändert die Art und Weise, wie wirksame Leseberechtigungen geprüft werden. Wie in der [Jackrabbit-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) beschrieben, wird einem jeweiligen Prinzipal mit der Berechtigung zum Anzeigen von `CUGcontent` nur dann Lesezugriff gewährt, wenn die Berechtigungsprüfung aller im Oak-Repository konfigurierten Modelle Lesezugriff gewährt.

Anders ausgedrückt, bei der Auswertung der wirksamen Berechtigungen werden sowohl `CUGPolicy` als auch die standardmäßigen Zugriffssteuerungseinträge berücksichtigt. Lesezugriff auf den CUG-Inhalt wird nur gewährt, wenn beide Richtlinientypen ihn gewähren. In einer standardmäßigen Veröffentlichungsinstallation von AEM, in der jedem Lesezugriff auf die vollständige Baumstruktur `/content` gewährt wird, haben die CUG-Richtlinien dieselben Auswirkungen wie in der alten Implementierung.

**Prüfung nach Bedarf**

Das CUG-Autorisierungsmodell ermöglicht das individuelle Aktivieren von Zugriffssteuerungsverwaltung und Berechtigungsprüfung:

* Zugriffssteuerungsverwaltung wird aktiviert, wenn das Modul über einen oder mehrere unterstützte Pfade verfügt, in denen CUGs erstellt werden können.
* Berechtigungsprüfung wird nur aktiviert, wenn die Option **CUG-Prüfung aktiviert** zusätzlich aktiviert wird.

In der neuen Standardeinrichtung von AEM wird die Prüfung von CUG-Richtlinien nur im Ausführungsmodus „publish“ aktiviert. Zeigen Sie dazu die näheren Informationen zur [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem) an. Dies lässt sich durch den Vergleich der wirksamen Richtlinien eines Pfads mit den im Inhalt gespeicherten Richtlinien verifizieren. Wirksame Richtlinien werden nur angezeigt, wenn die Berechtigungsprüfung für CUGs aktiviert ist.

Wie oben erklärt, werden die CUG-Zugriffssteuerungsrichtlinien nicht immer im Inhalt gespeichert, aber die Prüfung der gültigen Berechtigungen, die aus diesen Richtlinien hervorgehen, wird nur durchgesetzt, wenn in der Systemkonsole in der **CUG-Konfiguration** von Apache Jackrabbit Oak die Option **CUG-Prüfung aktiviert.** aktiviert ist. Standardmäßig wird sie nur im Ausführungsmodus „Veröffentlichen“ aktiviert.

### Unterschiede in Bezug auf Authentifizierung {#differences-with-regards-to-authentication}

Im Folgenden werden die Unterschiede im Hinblick auf die Authentifizierung beschrieben.

#### Dedizierter Mixin-Typ für Authentifizierungspflicht {#dedicated-mixin-type-for-authentication-requirement}

In der bisherigen Implementierung wurden die Autorisierungs- und Authentifizierungsaspekte einer CUG durch eine einzelne JCR-Eigenschaft ausgelöst (`cq:cugEnabled`). Insoweit die Authentifizierung betroffen ist, hat dies zu einer aktualisierten Liste von Authentifizierungspflichten geführt, die in der Apache Sling Authenticator-Implementierung gespeichert werden. Bei der neuen Implementierung wird dasselbe Ergebnis erzielt, indem der Zielknoten mit einem dedizierten Mixin-Typ (`granite:AuthenticationRequired`) markiert wird.

#### Eigenschaft zum Ausnehmen des Anmeldepfads {#property-for-excluding-login-path}

Der Mixin-Typ definiert eine einzelne optionale Eigenschaft mit der Bezeichnung `granite:loginPath`, die grundsätzlich der Eigenschaft `cq:cugLoginPage` entspricht. Im Gegensatz zur früheren Implementierung wird die Anmeldepfadeigenschaft nur berücksichtigt, wenn ihr deklarierender Knotentyp im Mixin-Typ aufgeführt wird. Wird eine Eigenschaft mit diesem Namen hinzugefügt, ohne den Mixin-Typ festzulegen, hat dies keine Auswirkungen und an den Authenticator werden keine neue Pflicht und keine Ausnahme für den Anmeldepfad gemeldet.

#### Berechtigung für Authentifizierungspflicht {#privilege-for-authentication-requirement}

Zum Hinzufügen oder Entfernen eines Mixin-Typs ist die Berechtigung `jcr:nodeTypeManagement` erforderlich. In der vorherigen Implementierung wurde zum Bearbeiten der Resteigenschaft die Berechtigung `jcr:modifyProperties` benötigt.

Was `granite:loginPath` angeht, wird dieselbe Berechtigung benötigt, um die Eigenschaft hinzuzufügen, zu ändern oder zu entfernen.

#### Vom Mixin-Typ definierter Zielknoten {#target-node-defined-by-mixin-type}

Authentifizierungspflichten sollen am JCR-Knoten erstellt werden und die Authentifizierungspflicht für den Teilbaum definieren. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll. Die Benutzeroberfläche für die neue Implementierung fügt den Mixin-Typ „auth-requirement“ konsequent dem Seitenknoten hinzu.

Wird die CUG-Richtlinie am Knoten „jcr:content“ unterhalb einer bestimmten Seite platziert, so wird nur der Zugriff auf den Inhalt einer bestimmten Seite eingeschränkt, wobei die Richtlinie keine Auswirkungen auf den Seitenknoten selbst oder auf untergeordnete Seiten hat.

Dies kann ein gültiges Szenario sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Platzierung des Mixin-Typs an allen Knoten ermöglicht. Allerdings stellt das Verhalten einen Kontrast zur vorherigen Implementierung dar, wo eine auf dem Knoten „jcr:content“ platzierte Eigenschaft „cq:cugEnabled“ oder „cq:cugLoginPage“ intern dem Seitenknoten zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

#### Konfigurierte unterstützte Pfade {#configured-supported-paths}

Sowohl der Mixin-Typ `granite:AuthenticationRequired` als auch die Eigenschaft „granite:loginPath“ werden nur innerhalb des Bereichs berücksichtigt, der durch den Konfigurationsoptionssatz **Unterstützte Pfade** in **Adobe Granite Authentication Requirement and Login Path Handler** definiert wird. Wenn keine Pfade festgelegt werden, wird das Authentifizierungspflicht-Feature komplett deaktiviert. In diesem Fall werden weder der Mixin-Typ noch die Eigenschaft wirksam, wenn sie hinzugefügt oder auf einen JCR-Knoten festgelegt werden.

### Zuordnen von JCR-Inhalt, OSGi-Diensten und Konfigurationen {#mapping-of-jcr-content-osgi-services-and-configurations}

Das folgende Dokument bietet eine umfassende Zuordnung von OSGi-Diensten, Konfigurationen und Repository-Inhalten der alten und der neuen Implementierung.

CUG-Zuordnung seit Einführung von AEM 6.3

[Datei abrufen](assets/cug-mapping.pdf)

## Aktualisieren der CUG {#upgrade-cug}

### Bestehende Installationen, welche die veraltete CUG verwenden {#existing-installations-using-the-deprecated-cug}

Die alte CUG-Unterstützungsimplementierung ist veraltet und wird aus zukünftigen Versionen entfernt. Es wird empfohlen, bei der Aktualisierung von Versionen vor AEM 6.3 auf die neuen Implementierungen umzustellen.

Bei aktualisierten AEM-Installationen darf nur eine CUG-Implementierung aktiviert sein. Die Kombination der neuen und der veralteten CUG-Unterstützung wurde nicht getestet und verursacht wahrscheinlich ein unerwartetes Verhalten:

* Kollisionen im Sling Authenticator in Bezug auf Authentifizierungspflichten
* Verweigerter Lesezugriff, wenn die mit der alten CUG verknüpfte ACL-Einrichtung mit einer neuen CUG-Richtlinie kollidiert

### Migrieren vorhandener CUG-Inhalte {#migrating-existing-cug-content}

Adobe stellt ein Tool für die Migration zur neuen CUG-Implementierung zur Verfügung. Sie müssen die folgenden Schritte ausführen, um es zu verwenden:

1. Navigieren Sie zu `https://<serveraddress>:<serverport>/system/console/cug-migration`, um auf das Tool zuzugreifen.
1. Geben Sie den Stammpfad ein, auf den Sie CUGs überprüfen möchten, und klicken Sie auf die Schaltfläche **Probelauf durchführen**. Dies löst am angegebenen Speicherort eine Suche nach CUGs aus, die konvertiert werden können.
1. Klicken Sie nach der Prüfung der Ergebnisse auf die Schaltfläche **Migration durchführen**, um zur neuen Implementierung zu migrieren.

>[!NOTE]
>
>Bei Problemen können Sie eine bestimmte Protokollfunktion auf **DEBUG**-Ebene unter `com.day.cq.auth.impl.cug` einrichten, um die Ausgabe des Migrations-Tools abzurufen. Weitere Informationen dazu finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
