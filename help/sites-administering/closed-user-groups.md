---
title: Geschlossene Benutzergruppen in AEM
description: Erfahren Sie mehr über geschlossene Benutzergruppen und die Vorteile, die sie für Skalierbarkeit und Sicherheit in AEM bieten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 39e35a07-140f-4853-8f0d-8275bce27a65
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '6650'
ht-degree: 100%

---

# Geschlossene Benutzergruppen in AEM{#closed-user-groups-in-aem}

## Einführung {#introduction}

Seit der Einführung von AEM 6.3 gibt es eine neue Implementierung des Features „Geschlossene Benutzergruppe“, welche die Probleme hinsichtlich der Leistung, Skalierbarkeit und Sicherheit der bestehenden Implementierung beheben soll.

>[!NOTE]
>
>Der Einfachheit halber wird das Feature im Rahmen dieser Dokumentation als „CUG“ abgekürzt (für Closed User Group, geschlossene Benutzergruppe).

Das Ziel der neuen Implementierung ist, wo nötig vorhandene Funktionen zu übernehmen und gleichzeitig Probleme und entwicklungsbedingte Einschränkungen älterer Versionen zu beheben. Das Ergebnis ist eine neue CUG-Version mit den folgenden Eigenschaften:

* Deutliche Trennung der Authentifizierungs- und Autorisierungselemente, die einzeln oder in Kombination eingesetzt werden können.
* Dediziertes Autorisierungsmodell, das eingeschränkten Lesezugriff auf die konfigurierten CUG-Baumstrukturen bietet, ohne andere Einrichtungs- und Erlaubnisanforderungen für die Zugriffskontrolle zu beeinträchtigen.
* Trennung zwischen der Einrichtung der Zugriffssteuerung für den eingeschränkten Lesezugriff, der auf Autoreninstanzen benötigt wird, und der Berechtigungsprüfung, die nur auf Veröffentlichungsinstanzen benötigt wird
* Bearbeiten des eingeschränkten Lesezugriffs ohne Berechtigungseskalation.
* Dedizierte Knotentyperweiterung zur Markierung der Authentifizierungsanforderung
* Optionaler, zur Authentifizierungsanforderung zugehöriger Anmeldepfad

### Die neue benutzerdefinierte Benutzergruppenimplementierung {#the-new-custom-user-group-implementation}

Eine CUG besteht im Kontext von AEM aus den folgenden Schritten:

* Schränken Sie den Lesezugriff auf die Baumstruktur ein, die geschützt werden muss, und gewähren Sie nur Prinzipalen Lesezugriff, die entweder mit einer gegebenen CUG-Instanz aufgeführt oder in der CUG-Prüfung nicht berücksichtigt werden.  Dies wird als **Autorisierungselement** bezeichnet.
* Erzwingen Sie die Authentifizierung bei einer gegebenen Baumstruktur und geben Sie optional eine dedizierte Anmeldeseite für die Struktur an, die dann ausgeschlossen wird.  Dies wird als **Authentifizierungselement** bezeichnet.

In der neuen Implementierung wird klar zwischen Autorisierungselementen und Authentifizierungselementen unterschieden.  Seit AEM 6.3 ist es möglich, den Lesezugriff zu beschränken, ohne explizit eine Authentifizierungspflicht hinzufügen.  Dies ist beispielsweise gebräuchlich, wenn eine bestimmte Instanz eine vollständige Authentifizierung erfordert oder eine gegebene Baumstruktur bereits in einer Teilbaumstruktur vorhanden ist, die schon eine Authentifizierung erfordert.

Gleichermaßen kann eine gegebene Baumstruktur mit einer Authentifizierungspflicht markiert werden, ohne die verwendete Berechtigungseinrichtung zu ändern. Die Kombinationen und die Ergebnisse werden im Abschnitt [Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) aufgeführt.

## Überblick {#overview}

### Autorisierung: Beschränken des Lesezugriffs {#authorization-restricting-read-access}

Die Schlüsselfunktion einer CUG besteht in der Einschränkung des Lesezugriffs auf eine bestimmte Baumstruktur im Content-Repository für alle außer ausgewählte Prinzipale.  Die neue Implementierung manipuliert nicht spontan die Standardinhalte der Zugriffssteuerung, sondern verwendet einen anderen Ansatz, indem sie einen speziellen Typ von Zugriffskontrollrichtlinien definiert, der eine CUG darstellt.

#### Zugriffssteuerungsrichtlinie für CUG {#access-control-policy-for-cug}

Dieser neue Typ von Richtlinie weist die folgenden Eigenschaften auf:

* Zugriffssteuerungsrichtlinie des Typs „org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy“ (definiert von der Apache Jackrabbit-API).
* PrincipalSetPolicy gewährt einem anpassbaren Satz von Prinzipalen Berechtigungen.
* Die erteilten Berechtigungen und der Umfang dieser Richtlinie sind ein Implementierungsdetail.

Die Implementierung von PrincipalSetPolicy, das zur Darstellung von CUGs verwendet wird, definiert zusätzlich Folgendes:

* CUG-Richtlinien gewähren nur Lesezugriff auf reguläre JCR-Elemente (beispielsweise sind Zugriffssteuerungsinhalte ausgeschlossen).
* Der Umfang wird durch den zugriffsgesteuerten Knoten definiert, der die CUG-Richtlinie enthält.
* CUG-Richtlinien können verschachtelt werden. Eine verschachtelte CUG fängt als neue CUG an, ohne den Prinzipalsatz der übergeordneten CUG zu übernehmen.
* Der Effekt der Richtlinie wird an die gesamte Teilbaumstruktur bis hin zur nächsten verschachtelten CUG weitergegeben, wenn die Auswertung aktiviert ist.

Diese CUG-Richtlinien werden anhand eines separaten Autorisierungsmoduls namens „oak-authorization-cug“ auf einer AEM-Instanz bereitgestellt. Dieses Modul verfügt über eine eigene Zugriffssteuerungsverwaltung und Berechtigungsprüfung. Das heißt, die Standardversion von AEM umfasst eine Konfiguration des Oak-Content-Repositorys, die mehrere Autorisierungsmechanismen kombiniert.  Weitere Informationen finden Sie auf [dieser Seite auf der Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

In dieser zusammengesetzten Konfiguration ersetzt eine neue CUG nicht den vorhandenen Zugriffssteuerungsinhalt, der an den Zielknoten angehängt ist. Stattdessen ist sie eine Ergänzung, die später auch entfernt werden kann, ohne die ursprüngliche Zugriffskontrolle zu beeinträchtigen, die standardmäßig in AEM eine Zugriffssteuerungsliste wäre.

Anders als bei der vorherigen Implementierung werden neue CUG-Richtlinien immer als Zugriffssteuerungsinhalte erkannt und behandelt.  Dies bedeutet, dass sie mit der JCR-Zugriffssteuerungsverwaltungs-API erstellt und bearbeitet werden.  Weitere Informationen finden Sie im Abschnitt [Verwalten von CUG-Richtlinien](#managing-cug-policies).

#### Auswertung der Berechtigung von CUG-Richtlinien {#permission-evaluation-of-cug-policies}

Neben einer dedizierten Zugriffssteuerungsverwaltung für CUGs, ermöglicht das neue Autorisierungsmodell ein bedingtes Aktivieren der Auswertung der Berechtigung für seine Richtlinien.  Dies ermöglicht die Einrichtung von CUG-Richtlinien in einer Staging-Umgebung. Dabei wird die Auswertung der effektiven Berechtigungen erst aktiviert, wenn sie in die Produktionsumgebung repliziert werden.

Die Berechtigungsprüfung für CUG-Richtlinien und die Interaktion mit dem standardmäßigen oder einem zusätzlichen Autorisierungsmodell folgen dem Muster, das für mehrfache Autorisierungsmechanismen in Apache Jackrabbit Oak entworfen wurde: Ein gegebener Berechtigungssatz wird also gewährt, wenn – und nur wenn – alle Modelle Zugriff erteilen.  Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

Die folgenden Eigenschaften gelten für die Auswertung der Berechtigung, die mit dem Autorisierungsmodell verknüpft ist, das CUG-Richtlinien verarbeiten und prüfen soll:

* Sie verarbeitet nur Leseberechtigungen für normale Knoten und Eigenschaften, aber keine Lesezugriffssteuerungsinhalte.
* Sie verarbeitet keine Schreibberechtigungen oder irgendwelche Berechtigungen für die Änderung von geschützten JCR-Inhalten (z. B. Zugriffssteuerung, Knotentypinformationen, Versionierung, Sperren oder Benutzerverwaltung).  Diese Berechtigungen sind nicht von CUG-Richtlinien betroffen und werden vom zugehörigen Autorisierungsmodell nicht geprüft. Ob diese Berechtigungen gewährt werden oder nicht, hängt von den anderen Modellen ab, die in der Sicherheitseinrichtung konfiguriert sind.

Der Effekt einer einzelnen CUG-Richtlinie auf die Berechtigungsprüfung kann wie folgt zusammengefasst werden:

* Lesezugriff wird allen vorenthalten, außer Subjekten, die ausgeschlossene oder aufgeführte Prinzipale enthalten.
* Die Richtlinie wirkt sich auf den Knoten mit Zugriffssteuerung aus, der die Richtlinie und ihre Eigenschaften umfasst.
* Der Effekt wird außerdem in der Hierarchie, also im vom Knoten mit Zugriffssteuerung definierten Elementbaum, nach unten weitergegeben
* Gleichrangige Elemente oder Vorgänger des Knotens mit Zugriffssteuerung sind jedoch nicht betroffen.
* Die Vererbung einer gegebenen CUG hält an einer verschachtelten CUG an.

#### Best Practices {#best-practices}

Die folgenden Best Practices sollten bei der Definition des eingeschränkten Lesezugriffs durch CUGs berücksichtigt werden:

* Entscheiden Sie bewusst, ob Sie eine CUG benötigen, um Lesezugriff einzuschränken oder die Authentifizierung zu erzwingen. Falls Sie Letzteres oder beides benötigen, finden Sie im Abschnitt zu den Best Practices Details hinsichtlich der Authentifizierungspflicht
* Erstellen Sie ein Bedrohungsmodell für die Daten oder Inhalte, die geschützt werden müssen, um Bedrohungsgrenzen zu identifizieren und ein klares Bild der Vertraulichkeit der Daten und der Rollen zu erhalten, die mit dem autorisierten Zugriff verbunden sind
* Modellieren Sie die Repository-Inhalte und CUGs unter Berücksichtigung allgemeiner Aspekte bezüglich der Autorisierung und Best Practices:

   * Denken Sie daran, dass Leseberechtigungen nur gewährt werden, wenn eine bestimmte CUG und die Prüfung anderer in der Einrichtung bereitgestellter Module einem bestimmten Subjekt erlauben, ein bestimmtes Repository-Element zu lesen
   * Vermeiden Sie die Erstellung überflüssiger CUGs, wenn der Lesezugriff bereits von anderen Autorisierungsmodulen eingeschränkt wird.
   * Ein übermäßiger Bedarf an verschachtelten CUGs weist möglicherweise auf Fehler beim Content-Design hin.
   * Ein übermäßiger Bedarf an CUGs (z. B. auf jeder Seite) weist möglicherweise darauf hin, dass ein benutzerdefiniertes Autorisierungsmodell besser geeignet wäre, um den Sicherheitsanforderungen der vorliegenden Anwendung und Inhalte gerecht zu werden.

* Beschränken Sie die Pfade mit Unterstützung für CUG-Richtlinien auf einige wenige Baumstrukturen im Repository, um eine optimale Leistung zu ermöglichen.  Lassen Sie CUGs beispielsweise nur unterhalb des Knotens „/content“ zu, wie es seit Einführung von AEM 6.3 standardmäßig festgelegt ist.
* CUG-Richtlinien sind darauf ausgelegt, einem kleinen Prinzipalsatz Lesezugriff zu gewähren.  Ein Bedarf an einer sehr großen Anzahl an Prinzipalen deutet möglicherweise auf Fehler beim Content- bzw. Anwendungs-Design hin und sollte überdacht werden.

### Authentifizierung: Definieren der Authentifizierungspflicht {#authentication-defining-the-auth-requirement}

Die Teile des CUG-Features, die für die Authentifizierung relevant sind, ermöglichen die Markierung von Baumstrukturen, die eine Authentifizierung erfordern, und optional die Angabe einer dedizierten Anmeldeseite.  Sie können in Übereinstimmung mit der vorherigen Version mit der neuen Implementierung Baumstrukturen markieren, die eine Authentifizierung im Inhalts-Repository erfordern. Sie ermöglicht auch bedingt die Synchronisierung mit dem `Sling org.apache.sling.api.auth.Authenticator`, der für die Durchsetzung der Anforderung und die Umleitung zu einer Anmelderessource verantwortlich ist.

Diese Anforderungen werden mit dem Authenticator anhand eines OSGi-Dienstes registriert, der die Registrierungseigenschaft `sling.auth.requirements` zur Verfügung stellt. Diese Eigenschaften werden dann dazu verwendet, die Authentifizierungspflichten dynamisch zu erweitern.  Weitere Informationen finden Sie in der [Sling-Dokumentation](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### Definieren der Authentifizierungspflicht mithilfe eines dedizierten Mixin-Typs {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Aus Sicherheitsgründen ersetzt die neue Implementierung die Verwendung einer übrigen JCR-Eigenschaft durch einen dedizierten Mixin-Typ mit der Bezeichnung `granite:AuthenticationRequired`. Er definiert eine einzelne optionale Eigenschaft des Typs STRING für den Anmeldepfad `granite:loginPath`. Nur Inhaltsänderungen mit Bezug zu diesem Mixin-Typ führen zu einer Aktualisierung der beim Apache Sling Authenticator registrierten Anforderungen. Die Änderungen werden nachverfolgt, wenn Übergangsänderungen beibehalten werden, daher muss `javax.jcr.Session.save()` aufgerufen werden, damit die Änderungen wirksam werden.

Dasselbe gilt für die Eigenschaft `granite:loginPath`. Sie wird nur berücksichtigt, wenn sie von dem Mixin-Typ definiert wird, der mit der Authentifizierungspflicht zusammenhängt. Wird eine Resteigenschaft mit genau diesem Namen einem nicht strukturierten JCR-Knoten hinzugefügt, hat dies nicht den gewünschten Effekt und die Eigenschaft wird von dem Handler ignoriert, der für die Aktualisierung der OSGi-Registrierung zuständig ist.

>[!NOTE]
>
>Das Festlegen der Eigenschaft für den Anmeldepfad ist optional und nur erforderlich, wenn der Baum, der die Authentifizierung erfordert, nicht auf die standardmäßige oder eine anderweitig geerbte Anmeldeseite zurückgesetzt werden kann. Siehe dazu unten die [Auswertung des Anmeldepfads](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path).

#### Registrieren der Authentifizierungspflicht und des Anmeldepfads mit dem Sling Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Da diese Art der Authentifizierungspflicht nur auf bestimmte Ausführungsmodi und auf eine kleine Teilmenge von Baumstrukturen innerhalb des Content-Repositorys beschränkt sein soll, ist das Tracking des Mixin-Typs der Anforderung und der Anmeldepfadeigenschaften eine Bedingung. Sie ist gebunden an eine entsprechende Konfiguration, welche die unterstützten Pfade definiert (siehe „Konfigurationsoptionen“ weiter unten). Daher lösen nur Änderungen im Rahmen dieser unterstützten Pfade eine Aktualisierung der OSGi-Registrierung aus. Ansonsten werden der Mixin-Typ und die Eigenschaft ignoriert.

Die standardmäßige Einrichtung von AEM nutzt nun diese Konfiguration, indem sie ermöglicht, für den Mixin-Typ den Autorenausführungsmodus festzulegen, ihn aber erst wirksam werden zu lassen, wenn er auf die Veröffentlichungsinstanz repliziert wurde. Auf [dieser Seite](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) finden Sie Einzelheiten dazu, wie Sling die Authentifizierungspflicht durchsetzt.

Indem Sie in den konfigurierten unterstützten Pfaden den Mixin-Typ `granite:AuthenticationRequired` hinzufügen, wird die OSGi-Registrierung des verantwortlichen Handlers mit einem neuen, zusätzlichen Eintrag mit der Eigenschaft `sling.auth.requirements` aktualisiert. Wenn eine gegebene Authentifizierungspflicht die optionale Eigenschaft `granite:loginPath` angibt, wird der Wert außerdem beim Authenticator mit dem Präfix „-“ registriert, um von der Authentifizierungspflicht ausgeschlossen zu werden.

#### Prüfung und Vererbung der Authentifizierungspflicht {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling-Authentifizierungspflichten werden anhand der Seiten- oder Knotenhierarchie vererbt. Die Details der Vererbung und der Auswertung von Authentifizierungspflichten (wie Reihenfolge und Rangfolge) sind ein Implementierungsdetail und werden in diesem Artikel nicht behandelt.

#### Auswertung des Anmeldepfads {#evaluation-of-login-path}

Die Prüfung des Anmeldepfads und die Weiterleitung an die entsprechende Ressource bei Authentifizierung sind Implementierungsdetails von Adobe Granite Login Selector Authentication Handler (`com.day.cq.auth.impl.LoginSelectorHandler`), einem Apache Sling-AuthenticationHandler, der standardmäßig mit AEM konfiguriert ist.

Nach dem Aufruf von `AuthenticationHandler.requestCredentials` versucht dieser Handler, die Zuordnungsanmeldeseite zu identifizieren, an die die Benutzerin oder der Benutzer weitergeleitet wird. Dies umfasst die folgenden Schritte:

* Es wird unterschieden, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Bei einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom LoginPathProvider (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * als Letztes ein Zurückgreifen auf die standardmäßige Anmeldeseite (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung der Benutzerin bzw. des Benutzers an diese Seite weitergeleitet.

Das Ziel dieser Dokumentation ist die Prüfung des Anmeldepfads, wie er von der internen Schnittstelle `LoginPathProvider` angezeigt wird. Die seit der Einführung von AEM 6.3 enthaltene Implementierung verhält sich wie folgt:

* Die Registrierung des Anmeldepfads hängt von der Unterscheidung ab, ob der Grund für die Weiterleitung ein abgelaufenes Kennwort oder eine normale Anmeldeanfrage ist.
* Bei einer regulären Anmeldung wird in der folgenden Reihenfolge überprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom `LoginPathProvider` (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * als Letztes ein Zurückgreifen auf die standardmäßige Anmeldeseite (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung der Benutzerin bzw. des Benutzers an diese Seite weitergeleitet.

`LoginPathProvider` zeigt anhand der Implementierung der neuen Authentifizierungspflichtunterstützung in Granite Anmeldepfade, wie sie anhand der `granite:loginPath`-Eigenschaften definiert sind, die wiederum wie oben beschrieben vom Mixin-Typ definiert werden. Die Zuordnung des Ressourcenpfads, der den Anmeldepfad und den Eigenschaftswert selbst enthält, wird im Speicher aufbewahrt und wird geprüft, um einen geeigneten Anmeldepfad für andere Knoten in der Hierarchie zu ermitteln.

>[!NOTE]
>
>Die Auswertung wird nur für Anfragen durchgeführt, die mit Ressourcen verknüpft sind, die sich in den konfigurierten unterstützten Pfaden befinden.  Für alle anderen Anfragen werden die alternativen Möglichkeiten zum Ermitteln des Anmeldepfads ausgewertet.

#### Best Practices {#best-practices-1}

Die folgenden Best Practices sollten bei der Definition von Authentifizierungsanforderungen berücksichtigt werden:

* Verschachtelung von Authentifizierungsanforderungen vermeiden: Eine einzelne „auth-requirement“-Markierung am Anfang einer Baumstruktur sollte ausreichen, denn sie wird an die gesamte vom Zielknoten definierte Teilbaumstruktur weitergegeben.  Zusätzliche Authentifizierungsanforderungen innerhalb dieser Baumstruktur sind als redundant zu betrachten und führen möglicherweise zu Leistungseinbußen bei der Prüfung der Authentifizierungsanforderung in Apache Sling.  Aufgrund der Trennung der autorisierungs- und authentifizierungsrelevanten CUG-Bereiche ist es möglich, den Lesezugriff anhand von CUG-Richtlinien oder anderen Richtlinien einzuschränken und gleichzeitig in der gesamten Baumstruktur die Authentifizierung zu erzwingen.
* Passen Sie Repository-Inhalte so an, dass die Authentifizierungsanforderungen für die gesamte Baumstruktur gelten, ohne verschachtelte Nebenbaumstrukturen wieder davon ausschließen zu müssen.
* Zur Vermeidung genauer Angaben und der darauf folgenden Registrierung redundanter Anmeldepfade:

   * Nutzen Sie die Vererbung und vermeiden Sie die Definition verschachtelter Anmeldepfade.
   * Legen Sie für den optionalen Anmeldepfad keinen Wert fest, der dem Standardwert oder einem vererbten Wert entspricht.
   * Anwendungsentwickler müssen identifizieren, welche Anmeldepfade in den globalen „login-path“-Konfigurationen (Standard und Zuordnungen) konfiguriert werden müssen, die mit dem `LoginSelectorHandler` verknüpft sind.

## Darstellung im Repository {#representation-in-the-repository}

### Darstellung der CUG-Richtlinien im Repository {#cug-policy-representation-in-the-repository}

Die Oak-Dokumentation beschreibt, wie die neuen CUG-Richtlinien im Repository-Content dargestellt werden. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Authentifizierungspflicht im Repository {#authentication-requirement-in-the-repository}

Die Notwendigkeit einer separaten Authentifizierungspflicht zeigt sich im Repository-Content anhand eines dedizierten Mixin-Knotentyps am Zielknoten. Der Mixin-Typ definiert eine optionale Eigenschaft, um für die vom Zielknoten definierte Baumstruktur eine dedizierte Anmeldeseite festzulegen.

Die mit dem Anmeldepfad verknüpfte Seite kann sich innerhalb oder außerhalb dieser Baumstruktur befinden.  Sie ist von der Authentifizierungspflicht ausgenommen.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Verwalten von CUG-Richtlinien und der Authentifizierungspflicht {#managing-cug-policies-and-authentication-requirement}

### Verwalten von CUG-Richtlinien {#managing-cug-policies}

Der neue Richtlinientyp für die Zugriffssteuerung, mit dem der Lesezugriff für eine CUG eingeschränkt wird, wird mithilfe der JCR-Zugriffssteuerungsverwaltungs-API verwaltet und folgt den Mechanismen, die in der [Beschreibung von JCR 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) aufgeführt werden.

#### Erstellen einer neuen CUG-Richtlinie {#set-a-new-cug-policy}

Code für die Anwendung einer neuen CUG-Richtlinie auf einen Knoten, der vorher keinen CUG-Satz aufwies.  Beachten Sie, dass `getApplicablePolicies` nur neue Richtlinien zurückgibt, die noch nie vorher festgelegt wurden. Am Ende muss die Richtlinie zurückgeschrieben und Änderungen müssen beibehalten werden.

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
   log.debug("no applicable policy"); // path not supported or no applicable policy (for example,
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### Bearbeiten einer vorhandenen UG-Richtlinie {#edit-an-existing-cug-policy}

Die folgenden Schritte sind erforderlich, um eine vorhandene CUG-Richtlinie zu bearbeiten.  Die angepasste Richtlinie muss zurückgeschrieben und Änderungen müssen mit `javax.jcr.Session.save()` beibehalten werden.

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

### Abrufen effektiver CUG-Richtlinien {#retrieve-effective-cug-policies}

Die Verwaltung der JCR-Zugriffssteuerung definiert eine optimale Methode zum Abrufen der Richtlinien, die an einem gegebenen Pfad wirksam sind.  Weil die Auswertung von CUG-Richtlinien bedingt ist und davon abhängt, ob die entsprechende Konfiguration aktiviert ist, stellt ein Aufruf von `getEffectivePolicies` eine einfache Methode dar, um zu überprüfen, ob eine gegebene CUG-Richtlinie in einer gegebenen Installation wirksam ist.

>[!NOTE]
>
>Zwischen `getEffectivePolicies` und dem folgenden Code-Beispiel, das die Hierarchie von unten nach oben betrachtet, um herauszufinden, ob ein gegebener Pfad bereits Teil einer bestehenden CUG ist, bestehen Unterschiede.

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

#### Abrufen übernommener CUG-Richtlinien {#retrieve-inherited-cug-policies}

Suchen aller verschachtelten CUGs, die an einem bestimmten Pfad definiert wurden, gleichgültig, ob sie wirksam sind oder nicht.  Weitere Informationen finden Sie im Abschnitt [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

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

#### Verwalten von CUG-Richtlinien nach Prinzipal {#managing-cug-policies-by-pincipal}

Die von `JackrabbitAccessControlManager` definierten Erweiterungen, welche die Bearbeitung von Zugriffssteuerungsrichtlinien nach Prinzipalen ermöglichen, werden nicht anhand der CUG-Zugriffssteuerungsverwaltung implementiert, da CUG-Richtlinien definitionsgemäß immer alle Prinzipale betreffen: Den mit `PrincipalSetPolicy` aufgeführten Prinzipalen wird Lesezugriff gewährt, während alle anderen Prinzipale in der vom Zielknoten definierten Baumstruktur keine Inhalte lesen können.

Die entsprechenden Methoden geben immer ein leeres Richtlinien-Array zurück, aber keine Ausnahmen.

### Verwalten der Authentifizierungsanforderungen {#managing-the-authentication-requirement}

Sie erstellen, ändern oder entfernen neue Authentifizierungsanforderungen, indem Sie den effektiven Knotentyp des Zielknotens ändern. Die optionale Anmeldepfadeigenschaft kann dann mit der normalen JCR-API geschrieben werden.

>[!NOTE]
>
>Die oben genannten Änderungen an einem bestimmten Zielknoten werden nur dann im Apache Sling Authenticator übernommen, wenn der `RequirementHandler` konfiguriert und das Ziel in den von den unterstützten Pfaden definierten Baumstrukturen vorhanden ist (siehe Abschnitt „Konfigurationsoptionen“).
>
>Weitere Informationen finden Sie unter [Zuweisen von Mixin-Knotentypen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Assigning Mixin Node Types) und [Hinzufügen von Knoten und Festlegen von Eigenschaften](https://docs.adobe.com/docs/de-DE/spec/jcr/2.0/10_Writing.html#10.4 Hinzufügen von Knoten und Festlegen von Eigenschaften).

#### Hinzufügen einer neuen Authentifizierungsanforderung {#adding-a-new-auth-requirement}

Im Folgenden finden Sie Schritte zum Erstellen einer Authentifizierungsanforderung.  Die Anforderung wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Hinzufügen einer neuen Authentifizierungsanforderung mit Anmeldepfad {#add-a-new-auth-requirement-with-login-path}

Hier finden Sie Schritte zum Erstellen einer Authentifizierungsanforderung mit einem Anmeldepfad. Die Pflicht und die Ausnahme für den Anmeldepfad werden nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Ändern eines vorhandenen Anmeldepfads {#modify-an-existing-login-path}

Im Folgenden finden Sie die Schritte zum Ändern eines vorhandenen Anmeldepfads.  Die Änderung wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Der vorherige Anmeldepfadwert wird aus der Registrierung entfernt.  Die mit dem Zielknoten verknüpfte Authentifizierungsanforderung ist von dieser Änderung nicht betroffen.

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

#### Entfernen eines vorhandenen Anmeldepfads {#remove-an-existing-login-path}

Hier finden Sie die Schritte zum Entfernen eines vorhandenen Anmeldepfads.  Die Registrierung des Anmeldepfadeintrags wird nur dann aus dem Apache Sling Authenticator entfernt, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Die mit dem Zielknoten verknüpfte Authentifizierungsanforderung ist nicht betroffen.

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

#### Entfernen einer Authentifizierungsanforderung {#remove-an-auth-requirement}

Hier finden Sie Schritte zum Entfernen einer vorhandenen Authentifizierungspflicht. Die Registrierung der Pflicht wird nur dann aus dem Apache Sling Authenticator entfernt, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Abrufen effektiver Authentifizierungspflichten {#retrieve-effective-auth-requirements}

Es gibt keine dedizierte öffentliche API zum Lesen aller effektiven Authentifizierungspflichten, die beim Apache Sling Authenticator registriert sind. Die Liste wird jedoch in der Systemkonsole unter `https://<serveraddress>:<serverport>/system/console/slingauth` im Abschnitt **Konfiguration der Authentifizierungspflicht** verfügbar gemacht.

Die folgende Abbildung zeigt die Authentifizierungsanforderungen einer AEM-Veröffentlichungsinstanz mit Demoinhalten. Der hervorgehobene Pfad der Community-Seite zeigt, wie eine Anforderung, die von der in diesem Dokument beschriebenen Implementierung hinzugefügt wurde, im Apache Sling Authenticator dargestellt wird.

>[!NOTE]
>
>In diesem Beispiel wurde die Eigenschaft für einen optionalen Anmeldepfad nicht festgelegt. Folglich wurde beim Authenticator kein zweiter Eintrag registriert.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Abrufen des effektiven Anmeldepfads {#retrieve-the-effective-login-path}

Derzeit gibt es keine öffentliche API zum Abrufen des Anmeldepfads, der verwendet wird, wenn anonym auf eine Ressource zugegriffen wird, die eine Authentifizierung erfordert. Im Abschnitt „Prüfung des Anmeldepfads“ finden Sie Implementierungsdetails dazu, wie der Anmeldepfad abgerufen wird.

Beachten Sie jedoch, dass es neben den mit dieser Funktion definierten Anmeldepfaden alternative Möglichkeiten gibt, die Weiterleitung zur Anmeldung anzugeben. Diese sollten bei der Entwicklung des Inhaltsmodells und der Authentifizierungsanforderungen einer jeweiligen AEM-Installation berücksichtigt werden.

#### Abrufen der übernommenen Authentifizierungsanforderung {#retrieve-the-inherited-auth-requirement}

Ebenso wie beim Anmeldepfad gibt es keine öffentliche API zum Abrufen der übernommenen Authentifizierungsanforderungen, die im Inhalt definiert sind. Das folgende Beispiel zeigt, wie alle Authentifizierungspflichten aufgeführt werden, die mit einer bestimmten Hierarchie definiert wurden, unabhängig davon, ob sie wirksam sind oder nicht. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

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

### Kombinieren von CUG-Richtlinien und der Authentifizierungsanforderung {#combining-cug-policies-and-the-authentication-requirement}

In der folgenden Tabelle sind die gültigen Kombinationen aus CUG-Richtlinien und Authentifizierungsanforderung in einer AEM-Instanz aufgeführt, in der durch eine entsprechende Konfiguration beide Module aktiviert sind.

| **Authentifizierung erforderlich** | **Anmeldepfad** | **Eingeschränkter Lesezugriff** | **Erwartete Auswirkungen** |
|---|---|---|---|
| Ja | Ja | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Eine nicht authentifizierte Person wird an die angegebene Anmeldeseite umgeleitet. |
| Ja | Nein | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Eine nicht authentifizierte Person wird an eine übernommene Standardanmeldeseite umgeleitet. |
| Ja | Ja | Nein | Eine nicht authentifizierte Person wird an die angegebene Anmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Ja | Nein | Nein | Eine nicht authentifizierte Person wird an eine übernommene Standardanmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungsanforderung markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es ist keine dedizierte CUG vorhanden, die den Lesezugriff einschränkt. |
| Nein | Nein | Ja | Authentifizierte oder nicht authentifizierte Benutzende können den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Nicht authentifizierte Benutzende werden gleich behandelt und nicht zur Anmeldeseite weitergeleitet. |

>[!NOTE]
>
>Die Kombination „Authentifizierungspflicht = Ja“ und „Anmeldepfad = Ja“ wird oben nicht angeführt, da es sich beim Anmeldepfad um eine optionales, mit einer Authentifizierungspflicht verknüpftes Attribut handelt. Wird eine JCR-Eigenschaft mit diesem Namen ohne den definierenden Mixin-Typ angegeben, so hat dies keine Auswirkungen und der entsprechende Handler ignoriert die Eigenschaft.

## OSGi-Komponenten und -Konfiguration {#osgi-components-and-configuration}

Dieser Abschnitt liefert Ihnen einen Überblick über die OSGi-Komponenten und die einzelnen Konfigurationsoptionen, die mit der neuen CUG-Implementierung eingeführt wurden.

In der CUG-Zuordnungsdokumentation finden Sie eine umfassende Aufstellung der Konfigurationsoptionen der alten und der neuen Implementierung.

### Autorisierung: Einrichtung und Konfiguration {#authorization-setup-and-configuration}

Die neuen Teile für die Autorisierung gehören zum Bundle **Oak CUG Authorization** (`org.apache.jackrabbit.oak-authorization-cug`), das Teil der Standardinstallation von AEM ist. Das Bundle definiert ein separates Autorisierungsmodell, das als zusätzliche Option für die Verwaltung des Lesezugriffs vorgesehen ist.

#### Einrichten der CUG-Autorisierung {#setting-up-cug-authorization}

Das Einrichten der CUG-Autorisierung wird in der [relevanten Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) detailliert beschrieben. Standardmäßig stellt AEM die CUG-Autorisierung in allen Ausführungsmodi bereit. Die schrittweisen Anweisungen können auch verwendet werden, um die CUG-Autorisierung in Installationen zu deaktivieren, für die eine andere Art der Autorisierung eingerichtet werden muss.

#### Konfigurieren des Referrer-Filters {#configuring-the-referrer-filter}

Sie müssen außerdem den [Sling Referrer-Filter](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) mit allen Host-Namen konfigurieren, die für den Zugriff auf AEM verwendet werden können, z. B. via CDN oder Lastenausgleich.

Wenn der Referrer-Filter nicht konfiguriert ist, treten Fehler wie der folgende auf, sobald jemand versucht, sich bei einer CUG-Website anzumelden:

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### Eigenschaften von OSGi-Komponenten {#characteristics-of-osgi-components}

Die beiden folgenden OSGi-Komponenten wurden hinzugefügt, um Authentifizierungsanforderungen zu definieren und dedizierte Anmeldepfade festzulegen:

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
   <td>Ermöglicht den Ausschluss von Prinzipalen mit den konfigurierten Namen aus der CUG-Auswertung.</td>
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

Eine Aufstellung der mit dem CUG-Autorisierungsmodul verknüpften verfügbaren Konfigurationsoptionen samt Beschreibung finden Sie in der [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration).

#### Ausnehmen von Prinzipalen von der CUG-Auswertung {#excluding-principals-from-cug-evaluation}

Das Ausschließen einzelner Prinzipale aus der CUG-Auswertung wurde aus der vorherigen Implementierung übernommen. Die neue CUG-Autorisierung behandelt dies anhand einer dedizierten Schnittstelle mit der Bezeichnung „CugExclude“. Apache Jackrabbit Oak 1.4 umfasst eine Standardimplementierung, die einen festen Satz von Prinzipalen ausschließt, und eine erweiterte Implementierung, die die Konfiguration individueller Prinzipalnamen ermöglicht. Letztere wird in AEM-Veröffentlichungsinstanzen konfiguriert.

Der Standard seit Einführung von AEM 6.3 verhindert, dass die folgenden Prinzipale von CUG-Richtlinien beeinflusst werden:

* Prinzipale mit Administratorrechten (Admins, Administratorgruppe)
* Dienstbenutzerprinzipale
* Repository-interne Systemprinzipale

Weitere Informationen finden Sie in der Tabelle im nachfolgenden Abschnitt [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem).

Die Ausnahme der Administratorgruppe kann in der Systemkonsole im Konfigurationsabschnitt **Apache Jackrabbit Oak CUG Exclude List** geändert oder erweitert werden.

Es kann auch eine benutzerdefinierte Bereitstellung der CugExclude-Schnittstelle bereitgestellt werden, um den Satz der ausgenommenen Prinzipale bei speziellen Anforderungen anzupassen. Weitere Informationen sowie eine Beispielimplementierung finden Sie in der Dokumentation zu [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability).

### Authentifizierung: Einrichtung und Konfiguration {#authentication-setup-and-configuration}

Die neuen Teile für die Authentifizierung gehören zum Bundle **Adobe Granite Authentication Handler** (`com.adobe.granite.auth.authhandler`, Version 5.6.48). Dieses Bundle ist Teil der Standardinstallation von AEM.

Um den Ersatz der Authentifizierungsanforderungen für die veraltete CUG-Unterstützung einzurichten, müssen einige OSGi-Komponenten in der jeweiligen AEM-Installation vorhanden und aktiv sein. Weitere Informationen finden Sie unten im Abschnitt **Eigenschaften von OSGi-Komponenten**.

>[!NOTE]
>
>Aufgrund der obligatorischen Konfigurationsoption mit dem RequirementHandler sind die zur Authentifizierung gehörigen Teile nur aktiv, wenn die Funktion durch Angabe eines Satzes unterstützter Pfade aktiviert wurde. Bei einer AEM-Standardinstallation ist die Funktion im author-Ausführungsmodus deaktiviert und für „/content“ im publish-Ausführungsmodus aktiviert.

**Eigenschaften von OSGi-Komponenten**

Die beiden folgenden OSGi-Komponenten wurden hinzugefügt, um Authentifizierungsanforderungen zu definieren und dedizierte Anmeldepfade festzulegen:

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

Die Teile der CUG-Neuschreibung, die für die Authentifizierung relevant sind, umfassen nur eine einzelne Konfigurationsoption, die dem „Adobe Granite Authentication Requirement and Login Path Handler“ zugehörig ist:

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
   <td><p>Bezeichnung = Unterstützte Pfade</p> <p>Name = „supportedPaths“</p> </td>
   <td>Set&lt;String&gt;</td>
   <td>-</td>
   <td>Pfade, in denen Authentifizierungspflichten von diesem Handler eingehalten werden. Legen Sie diese Konfiguration nicht fest, wenn Sie den Mixin-Typ <code>granite:AuthenticationRequirement</code> Knoten hinzufügen möchten, ohne dass sie erzwungen werden (beispielsweise auf Autoreninstanzen). Wenn nicht vorhanden, ist die Funktion deaktiviert. </td>
  </tr>
 </tbody>
</table>

## Standardkonfiguration seit Einführung von AEM 6.3 {#default-configuration-since-aem}

Neue AEM-Installationen verwenden standardmäßig die neuen Implementierungen für die autorisierungs- und authentifizierungsrelevanten Teile der CUG-Funktionalität. Die alte Implementierung „Adobe Granite Closed User Group (CUG) Support“ ist veraltet und wird standardmäßig in allen Installationen von AEM deaktiviert. Stattdessen werden die neuen Implementierungen wie folgt aktiviert:

### Autoreninstanzen {#author-instances}

| **„Apache Jackrabbit Oak CUG Configuration“** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Die Zugriffssteuerungsverwaltung für „CUGpolicies“ ist aktiviert. |
| CUG-Prüfung aktiviert: FALSE | Die Berechtigungsprüfung ist deaktiviert. CUG-Richtlinien sind nicht wirksam. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

>[!NOTE]
>
>Für **Apache Jackrabbit Oak CUG Exclude List** und **Adobe Granite Authentication Requirement and Login Path Handler** ist in standardmäßigen Autoreninstanzen keine Konfiguration vorhanden.

### Veröffentlichungsinstanzen {#publish-instances}

| **„Apache Jackrabbit Oak CUG Configuration“** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Die Zugriffssteuerungsverwaltung für CUG-Richtlinien wird in den konfigurierten Pfaden aktiviert. |
| CUG-Prüfung aktiviert: TRUE | Die Berechtigungsprüfung wird in den konfigurierten Pfaden aktiviert. CUG-Richtlinien werden wirksam bei `Session.save()`. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

| **„Apache Jackrabbit Oak CUG Exclude List“** | **Erklärung** |
|---|---|
| Prinzipalnamen: Admins | Schließt den Administratorprinzipal aus der CUG-Prüfung aus. |

| **„Adobe Granite Authentication Requirement and Login Path Handler“** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Authentifizierungspflichten, die im Repository durch den Mixin-Typ `granite:AuthenticationRequired` definiert wurden, werden in `/content` bei `Session.save()` wirksam. Sling Authenticator wird aktualisiert. Wird der Mixin-Typ außerhalb der unterstützten Pfade hinzugefügt, so wird dies ignoriert. |

## Deaktivieren der CUG-Autorisierung und der Authentifizierungspflicht {#disabling-cug-authorization-and-authentication-requirement}

Diese neue Implementierung kann u. U. vollständig deaktiviert werden, falls eine bestimmte Installation keine CUGs nutzt bzw. eine andere Möglichkeit zur Authentifizierung und Autorisierung verwendet.

### Deaktivieren der CUG-Autorisierung {#disable-cug-authorization}

In der Dokumentation zur [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) finden Sie Informationen dazu, wie Sie das CUG-Autorisierungsmodell aus der kombinierten Autorisierungseinrichtung entfernen.

### Deaktivieren der Authentifizierungspflicht {#disable-the-authentication-requirement}

Zum Deaktivieren der Unterstützung der Authentifizierungspflicht, die vom Modul `granite.auth.authhandler` bereitgestellt wird, muss nur die Konfiguration entfernt werden, die mit **Adobe Granite Authentication Requirement and Login Path Handler** verknüpft ist.

>[!NOTE]
>
>Beachten Sie jedoch, dass durch das Entfernen der Konfiguration die Registrierung des Mixin-Typs nicht aufgehoben wird, der noch immer auf Knoten anwendbar war, ohne wirksam zu werden.

## Interaktion mit anderen Modulen {#interaction-with-other-modules}

### Apache Jackrabbit-API {#apache-jackrabbit-api}

Die von Apache Jackrabbit definierte API wurde erweitert, um dem neuen Typ von Zugriffssteuerungsrichtlinie zu entsprechen, die vom CUG-Autorisierungsmodell verwendet wird. Seit Version 2.11.0 definiert das Modul `jackrabbit-api` eine neue Schnittstelle mit der Bezeichnung `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die aus `javax.jcr.security.AccessControlPolicy` hervorgeht.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Der Importmechanismus von Apache Jackrabbit FileVault wurde angepasst, um mit Zugriffssteuerungsrichtlinien des Typs `PrincipalSetPolicy` umgehen zu können.

### Apache Sling-Inhaltsverteilung {#apache-sling-content-distribution}

Siehe den Abschnitt [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault) oben.

### Adobe Granite-Replikation {#adobe-granite-replication}

Das Replikationsmodul wurde geringfügig angepasst, um die CUG-Richtlinien zwischen verschiedenen AEM-Instanzen replizieren zu können:

* `DurboImportConfiguration.isImportAcl()` wird wörtlich interpretiert und betrifft nur Zugriffssteuerungsrichtlinien, die `javax.jcr.security.AccessControlList` implementieren.

* `DurboImportTransformer` respektiert nur diese Konfiguration für echte ACLs.
* Andere Richtlinien, z. B. vom CUG-Autorisierungsmodell erstellte `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`-Instanzen, werden immer repliziert und die Konfigurationsoption `DurboImportConfiguration.isImportAcl`() wird ignoriert.

Es gibt eine Einschränkung hinsichtlich der Replikation von CUG-Richtlinien. Wenn eine CUG-Richtlinie entfernt wird, ohne dass der entsprechende Mixin-Knotentyp `rep:CugMixin,` entfernt wird, wird die Entfernung in der Replikation nicht berücksichtigt. Dies wurde korrigiert, indem mit einer Richtlinie auch immer der Mixin-Typ entfernt wird. Die Einschränkung macht sich aber möglicherweise trotzdem bemerkbar, wenn der Mixin-Typ manuell hinzugefügt wurde.

### Adobe Granite-Authentifizierungs-Handler {#adobe-granite-authentication-handler}

Der Authentifizierungs-Handler **Adobe Granite HTTP Header Authentication Handler** im Bundle `com.adobe.granite.auth.authhandler` verweist auf die Schnittstelle `CugSupport`, die vom selben Modul definiert wird. Sie wird unter bestimmten Bedingungen zur Berechnung des Bereichs verwendet, wobei auf den mit dem Handler konfigurierten Bereich ausgewichen wird.

Dies wurde angepasst, um den Verweis auf `CugSupport` optional zu machen und so die größtmögliche Abwärtskompatibilität zu erreichen, falls bei einer Einrichtung die veraltete Implementierung erneut aktiviert werden soll. Für Installationen, welche die Implementierung verwenden, wird der Bereich nicht mehr aus der CUG-Implementierung extrahiert, sondern stattdessen wird der Bereich immer als mit **Adobe Granite HTTP Header Authentication Handler** definiert angezeigt.

>[!NOTE]
>
>Standardmäßig ist der **Adobe Granite HTTP Header Authentication Handler** nur im Veröffentlichungsausführungsmodus mit aktivierter Option „Anmeldeseite deaktivieren“ (`auth.http.nologin`) konfiguriert.

### AEM Live Copy {#aem-livecopy}

Die Konfiguration von CUGs mit LiveCopy wird im Repository durch das Hinzufügen eines zusätzlichen Knotens und einer zusätzlichen Eigenschaft wie folgt dargestellt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide Elemente werden unter `cq:Page` erstellt. Mit dem aktuellen Design verarbeitet MSM nur Knoten und Eigenschaften, die sich unter dem Knoten `cq:PageContent` (`jcr:content`) befinden.

Daher können CUG-Gruppen in Live Copies nicht aus Blueprints bereitgestellt werden. Berücksichtigen Sie dies, wenn Sie eine Live Copy konfigurieren.

## Änderungen mit der neuen CUG-Implementierung {#changes-with-the-new-cug-implementation}

Dieser Abschnitt liefert einen Überblick über die an der CUG-Funktion vorgenommenen Änderungen sowie einen Vergleich zwischen der alten und der neuen Implementierung. Es werden alle Änderungen aufgeführt, die beeinflussen, wie die CUG-Unterstützung konfiguriert wird, und beschrieben, wie und von wem CUGs im Repository-Content verwaltet werden.

### Unterschiede bei CUG-Einrichtung und -Konfiguration {#differences-in-cug-setup-and-configuration}

Die veraltete OSGi-Komponente **Adobe Granite Closed User Group (CUG) Support** (`com.day.cq.auth.impl.cug.CugSupportImpl`) wurde durch neue Komponenten ersetzt, damit die autorisierungs- und authentifizierungsrelevanten Teile der vorherigen CUG-Funktionalität getrennt verwaltet werden können.

## Unterschiede beim Verwalten von CUGs im Repository-Content {#differences-in-managing-cugs-in-the-repository-content}

Die folgenden Abschnitte beschreiben die Unterschiede zwischen der alten und der neuen Implementierung im Hinblick auf die Implementierung und Sicherheit. Die neue Implementierung soll dieselbe Funktionalität bieten, aber es gibt einige geringfügige Unterschiede, die Sie kennen sollten, wenn Sie die neue CUG-Funktion verwenden.

### Unterschiede in Bezug auf die Autorisierung {#differences-with-regards-to-authorization}

Im Folgenden finden Sie eine Zusammenfassung der wichtigsten Unterschiede hinsichtlich Autorisierung:

**Dedizierter Zugriffssteuerungsinhalt für CUGs**

Bei der alten Implementierung wurde das standardmäßige Autorisierungsmodell dazu verwendet, die Richtlinien für Zugriffssteuerungslisten in Publish zu ändern, wobei bestehende ACEs aufgrund der von der CUG vorgegebenen Einrichtung ersetzt wurden. Dies wurde durch die Eingabe regulärer JCR-Resteigenschaften ausgelöst, die in Publish interpretiert wurden.

Bei der neuen Implementierung wird die Zugriffssteuerungseinrichtung des Standardautorisierungsmodells nicht von der Erstellung, Änderung oder Entfernung von CUGs beeinflusst. Stattdessen wird ein neuer Typ von Richtlinie mit der Bezeichnung `PrincipalSetPolicy` als zusätzlicher Zugriffssteuerungsinhalt auf den Zielknoten angewendet. Diese zusätzliche Richtlinie ist ein untergeordnetes Element des Zielknotens und ein gleichrangiges Element des Standardrichtlinienknotens, falls dieser vorhanden ist.

**Bearbeiten von CUG-Richtlinien in der Zugriffssteuerungsverwaltung**

Dieses Abweichen von JCR-Resteigenschaften hin zu einer dedizierten Zugriffssteuerungsrichtlinie hat Auswirkungen auf die Berechtigung, die zum Erstellen oder Ändern des Autorisierungsteils der CUG-Funktion benötigt wird. Da dies eine Modifikation des Zugriffssteuerungsinhalts darstellt, sind die Berechtigungen `jcr:readAccessControl` und `jcr:modifyAccessControl` für das Schreiben in das Repository erforderlich. Daher können nur Inhaltsautorinnen und -autoren, die zur Änderung der Zugriffssteuerungsinhalte einer Seite berechtigt sind, diese Inhalte einrichten oder ändern. Im Vergleich dazu war bei der alten Implementierung die Berechtigung zum Schreiben regulärer JCR-Eigenschaften ausreichend. Das Ergebnis war eine Berechtigungseskalation.

**Ein durch eine Richtlinie definierter Zielknoten**

Erstellen Sie CUG-Richtlinien am JCR-Knoten, der die Unterstruktur definiert, die einem eingeschränkten Lesezugriff unterliegen soll. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll.

Wird die CUG-Richtlinie am Knoten „jcr:content“ unterhalb einer bestimmten Seite platziert, so wird nur der Zugriff auf den Inhalt (im engeren Sinne) einer bestimmten Seite eingeschränkt, wobei die Richtlinie keine Auswirkungen auf gleichrangige oder untergeordnete Seiten hat. Dies kann ein gültiger Anwendungsfall sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Anwendung detaillierter Zugriffssteuerungsinhalte erlaubt. Bei der früheren Implementierung hingegen wurde eine auf dem Knoten „jcr:content“ platzierte Eigenschaft „cq:cugEnabled“ intern dem Seitenknoten zugeordnet. Diese Zuordnung wird nicht mehr durchgeführt.

**Auswertung der Berechtigung mit CUG-Richtlinien**

Die Umstellung von der alten CUG-Unterstützung auf ein zusätzliches Autorisierungsmodell verändert die Art und Weise, wie wirksame Leseberechtigungen geprüft werden. Wie in der [Jackrabbit-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) beschrieben, wird einem jeweiligen Prinzipal mit der Berechtigung zum Anzeigen von `CUGcontent` nur dann Lesezugriff gewährt, wenn die Berechtigungsprüfung aller im Oak-Repository konfigurierten Modelle Lesezugriff gewährt.

Anders ausgedrückt, bei der Auswertung der wirksamen Berechtigungen werden sowohl die `CUGPolicy` als auch die standardmäßigen Zugriffssteuerungseinträge berücksichtigt. Lesezugriff auf den CUG-Inhalt wird nur gewährt, wenn beide Richtlinientypen ihn gewähren. In einer standardmäßigen Veröffentlichungsinstallation von AEM, in der jedem Lesezugriff auf die vollständige Baumstruktur `/content` gewährt wird, haben die CUG-Richtlinien dieselben Auswirkungen wie in der alten Implementierung.

**Auswertung nach Bedarf**

Das CUG-Autorisierungsmodell ermöglicht das individuelle Aktivieren von Zugriffssteuerungsverwaltung und Berechtigungsprüfung:

* Die Zugriffssteuerungsverwaltung wird aktiviert, wenn das Modul über einen oder mehrere unterstützte Pfade verfügt, in denen CUGs erstellt werden können
* Die Auswertung der Berechtigungen wird nur aktiviert, wenn die Option zur **CUG-Auswertung** zusätzlich aktiviert wird.

In der neuen Standardeinrichtung von AEM wird die Prüfung von CUG-Richtlinien nur im Ausführungsmodus „publish“ aktiviert. Zeigen Sie dazu die näheren Informationen zur [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem) an. Dies lässt sich durch den Vergleich der wirksamen Richtlinien eines Pfads mit den im Inhalt gespeicherten Richtlinien verifizieren. Wirksame Richtlinien werden nur angezeigt, wenn die Berechtigungsprüfung für CUGs aktiviert ist.

Wie oben erklärt, werden die CUG-Zugriffssteuerungsrichtlinien nicht immer im Inhalt gespeichert, aber die Prüfung der gültigen Berechtigungen, die aus diesen Richtlinien hervorgehen, wird nur durchgesetzt, wenn in der Systemkonsole in der **CUG-Konfiguration** von Apache Jackrabbit Oak die Option **CUG-Prüfung aktiviert.** aktiviert ist. Standardmäßig wird sie nur im Ausführungsmodus „Veröffentlichen“ aktiviert.

### Unterschiede im Hinblick auf die Authentifizierung {#differences-with-regards-to-authentication}

Im Folgenden werden die Unterschiede im Hinblick auf die Authentifizierung beschrieben.

#### Dedizierter Mixin-Typ für die Authentifizierungsanforderung {#dedicated-mixin-type-for-authentication-requirement}

In der bisherigen Implementierung wurden die Autorisierungs- und Authentifizierungsaspekte einer CUG durch eine einzelne JCR-Eigenschaft ausgelöst (`cq:cugEnabled`). Insoweit die Authentifizierung betroffen ist, hat dies zu einer aktualisierten Liste von Authentifizierungspflichten geführt, die in der Apache Sling Authenticator-Implementierung gespeichert werden. Bei der neuen Implementierung wird dasselbe Ergebnis erzielt, indem der Zielknoten mit einem dedizierten Mixin-Typ (`granite:AuthenticationRequired`) markiert wird.

#### Eigenschaft zum Ausnehmen des Anmeldepfads {#property-for-excluding-login-path}

Der Mixin-Typ definiert eine einzelne optionale Eigenschaft mit der Bezeichnung `granite:loginPath`, die grundsätzlich der Eigenschaft `cq:cugLoginPage` entspricht. Im Gegensatz zur früheren Implementierung wird die Anmeldepfadeigenschaft nur berücksichtigt, wenn ihr deklarierender Knotentyp das genannte Mixin ist. Wird eine Eigenschaft mit diesem Namen hinzugefügt, ohne den Mixin-Typ festzulegen, hat dies keine Auswirkungen und an den Authenticator wird weder eine neue Anforderung noch eine Ausnahme für den Anmeldepfad gemeldet.

#### Berechtigung für die Authentifizierungsanforderung {#privilege-for-authentication-requirement}

Zum Hinzufügen oder Entfernen eines Mixin-Typs ist die Berechtigung `jcr:nodeTypeManagement` erforderlich. In der vorherigen Implementierung wurde zum Bearbeiten der Resteigenschaft die Berechtigung `jcr:modifyProperties` benötigt.

Was `granite:loginPath` angeht, wird dieselbe Berechtigung benötigt, um die Eigenschaft hinzuzufügen, zu ändern oder zu entfernen.

#### Vom Mixin-Typ definierter Zielknoten {#target-node-defined-by-mixin-type}

Erstellen Sie Authentifizierungsanforderungen am JCR-Knoten, der die Unterstruktur definiert, die der erzwungenen Anmeldung unterliegen soll. Hierbei handelt es sich wahrscheinlich um eine AEM-Seite, falls die CUG die gesamte Baumstruktur betreffen soll. Die Benutzeroberfläche für die neue Implementierung fügt daher den Mixin-Typ „auth-requirement“ zum Seitenknoten hinzu.

Wird die CUG-Richtlinie am Knoten „jcr:content“ unterhalb einer bestimmten Seite platziert, so wird nur der Zugriff auf den Inhalt einer bestimmten Seite eingeschränkt.  Dies hat jedoch keine Auswirkungen auf den Seitenknoten selbst oder auf untergeordnete Seiten.

Dies kann ein gültiges Szenario sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Platzierung des Mixins an einem beliebigen Knoten ermöglicht. Allerdings stellt das Verhalten einen Kontrast zur vorherigen Implementierung dar, wo eine auf dem Knoten „jcr:content“ platzierte Eigenschaft „cq:cugEnabled“ oder „cq:cugLoginPage“ intern dem Seitenknoten zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

#### Konfigurierte unterstützte Pfade {#configured-supported-paths}

Sowohl der Mixin-Typ `granite:AuthenticationRequired` als auch die Eigenschaft „granite:loginPath“ werden nur innerhalb des Bereichs berücksichtigt, der durch den Konfigurationsoptionssatz **Unterstützte Pfade** in **Adobe Granite Authentication Requirement and Login Path Handler** definiert wird. Wenn keine Pfade festgelegt werden, wird die Funktion zur Authentifizierungspflicht komplett deaktiviert. In diesem Fall werden weder der Mixin-Typ noch die Eigenschaft wirksam, wenn sie hinzugefügt oder auf einen JCR-Knoten festgelegt werden.

### Zuordnen von JCR-Inhalt, OSGi-Diensten und Konfigurationen {#mapping-of-jcr-content-osgi-services-and-configurations}

Das folgende Dokument bietet eine umfassende Zuordnung von OSGi-Diensten, Konfigurationen und Repository-Inhalten der alten und der neuen Implementierung.

CUG-Zuordnung seit Einführung von AEM 6.3

[Datei abrufen](assets/cug-mapping.pdf)

## Aktualisieren einer CUG {#upgrade-cug}

### Bestehende Installationen mit veralteter CUG {#existing-installations-using-the-deprecated-cug}

Die alte CUG-Unterstützungsimplementierung ist veraltet und wird aus zukünftigen Versionen entfernt. Es wird empfohlen, beim Upgrade von Versionen vor AEM 6.3 auf die neuen Implementierungen umzustellen.

Bei aktualisierten AEM-Installationen darf nur eine einzige CUG-Implementierung aktiviert sein. Die Kombination der neuen und der veralteten CUG-Unterstützung wurde nicht getestet und führt wahrscheinlich zu unerwartetem Verhalten:

* Kollisionen im Sling Authenticator in Bezug auf Authentifizierungsanforderungen
* Verweigerung des Lesezugriffs, wenn die mit der alten CUG verknüpfte ACL-Einrichtung mit einer neuen CUG-Richtlinie kollidiert

### Migrieren vorhandener CUG-Inhalte {#migrating-existing-cug-content}

Adobe bietet ein Tool für die Migration zur neuen CUG-Implementierung. Gehen Sie wie folgt vor, um es zu verwenden:

1. Navigieren Sie zu `https://<serveraddress>:<serverport>/system/console/cug-migration`, um auf das Tool zuzugreifen.
1. Geben Sie den Stammpfad ein, für den CUGs geprüft werden sollen, und klicken Sie auf die Schaltfläche zum **Durchführen eines Probelaufs**. Dies löst am angegebenen Speicherort eine Suche nach CUGs aus, die konvertiert werden können.
1. Klicken Sie nach der Prüfung der Ergebnisse auf die Schaltfläche **Migration durchführen**, um zur neuen Implementierung zu migrieren.

>[!NOTE]
>
>Bei Problemen können Sie eine bestimmte Protokollfunktion auf **DEBUG**-Ebene unter `com.day.cq.auth.impl.cug` einrichten, um die Ausgabe des Migrations-Tools abzurufen. Weitere Informationen dazu finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
