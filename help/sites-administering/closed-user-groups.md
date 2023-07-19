---
title: Geschlossene Benutzergruppen in AEM
description: Erfahren Sie mehr über geschlossene Benutzergruppen in AEM.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 39e35a07-140f-4853-8f0d-8275bce27a65
feature: Security
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '6845'
ht-degree: 48%

---

# Geschlossene Benutzergruppen in AEM{#closed-user-groups-in-aem}

## Einführung {#introduction}

Seit AEM 6.3 gibt es eine neue Implementierung geschlossener Benutzergruppen , die die Leistungs-, Skalierbarkeits- und Sicherheitsprobleme in der bestehenden Implementierung beheben soll.

>[!NOTE]
>
>Der Einfachheit halber wird das Feature im Rahmen dieser Dokumentation als „CUG“ abgekürzt (für Closed User Group, geschlossene Benutzergruppe).

Das Ziel der neuen Implementierung ist, wo nötig vorhandene Funktionen zu übernehmen, aber gleichzeitig Probleme und entwicklungsbedingte Einschränkungen älterer Versionen zu beheben. Das Ergebnis ist ein neues CUG-Design mit den folgenden Eigenschaften:

* Klare Trennung der Authentifizierungs- und Autorisierungselemente, die einzeln oder in Kombination verwendet werden können;
* Dediziertes Autorisierungsmodell, das den eingeschränkten Lesezugriff in den konfigurierten CUG-Bäumen widerspiegelt, ohne andere Einrichtungs- und Berechtigungsanforderungen für die Zugriffskontrolle zu beeinträchtigen;
* Trennung zwischen der Einrichtung der Zugriffssteuerung für den eingeschränkten Lesezugriff, der normalerweise auf Autoreninstanzen benötigt wird, und der Berechtigungsprüfung, die normalerweise nur auf Veröffentlichungsinstanzen benötigt wird
* Bearbeiten des eingeschränkten Lesezugriffs ohne Berechtigungseskalierung;
* Dedizierte Knotentyperweiterung zum Markieren der Authentifizierungspflicht;
* Optionaler Anmeldepfad, der der Authentifizierungspflicht zugeordnet ist.

### Die neue Implementierung der benutzerspezifischen Benutzergruppe {#the-new-custom-user-group-implementation}

Eine CUG, wie sie im Kontext von AEM bekannt ist, besteht aus folgenden Schritten:

* Schränken Sie den Lesezugriff auf den Baum ein, der geschützt werden muss, und erlauben Sie nur das Lesen für Prinzipale, die entweder mit einer bestimmten CUG-Instanz aufgelistet oder ganz aus der CUG-Bewertung ausgeschlossen sind. Dies wird als **Autorisierung** -Element.
* Erzwingen Sie die Authentifizierung in einem gegebenen Baum und geben Sie optional eine dedizierte Anmeldeseite für diesen Baum an, die anschließend ausgeschlossen wird. Dies wird als **Authentifizierung** -Element.

Die neue Implementierung wurde entwickelt, um eine Linie zwischen den Authentifizierungs- und den Autorisierungselementen zu ziehen. Ab AEM 6.3 ist es möglich, den Lesezugriff zu beschränken, ohne explizit eine Authentifizierungspflicht hinzuzufügen. Wenn beispielsweise eine bestimmte Instanz eine Authentifizierung erfordert oder sich eine bestimmte Struktur bereits in einer Unterstruktur befindet, für die bereits eine Authentifizierung erforderlich ist.

Gleichermaßen kann eine gegebene Baumstruktur mit einer Authentifizierungspflicht markiert werden, ohne die verwendete Berechtigungseinrichtung zu ändern. Die Kombinationen und Ergebnisse werden im [Kombinieren von CUG-Richtlinien und der Authentifizierungspflicht](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) Abschnitt.

## Übersicht {#overview}

### Autorisierung: Beschränken des Lesezugriffs {#authorization-restricting-read-access}

Die Schlüsselfunktion einer CUG besteht darin, den Lesezugriff auf eine bestimmte Struktur im Inhalts-Repository für alle außer ausgewählten Prinzipalen zu beschränken. Anstatt den standardmäßigen Inhalt der Zugriffskontrolle sofort zu bearbeiten, verfolgt die neue Implementierung einen anderen Ansatz, indem sie einen dedizierten Typ von Zugriffssteuerungsrichtlinie definiert, die eine CUG darstellt.

#### Zugriffssteuerungsrichtlinie für CUG {#access-control-policy-for-cug}

Diese neue Art von Richtlinie weist die folgenden Merkmale auf:

* Zugriffssteuerungsrichtlinie des Typs „org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy“ (definiert von der Apache Jackrabbit-API).
* PrincipalSetPolicy gewährt einem anpassbaren Satz von Prinzipalen Berechtigungen.
* Die erteilten Berechtigungen und der Umfang dieser Richtlinie sind ein Implementierungsdetail.

Die Implementierung von PrincipalSetPolicy, das zur Darstellung von CUGs verwendet wird, definiert zusätzlich Folgendes:

* CUG-Richtlinien gewähren nur Lesezugriff auf reguläre JCR-Elemente (beispielsweise sind Zugriffssteuerungsinhalte ausgeschlossen).
* Der Umfang wird durch den zugriffsgesteuerten Knoten definiert, der die CUG-Richtlinie enthält.
* CUG-Richtlinien können verschachtelt werden. Eine verschachtelte CUG startet eine neue CUG, ohne den Hauptsatz der übergeordneten CUG zu übernehmen.
* Wenn die Bewertung aktiviert ist, wird der Effekt der Richtlinie an die gesamte Unterstruktur bis zur nächsten verschachtelten CUG vererbt.

Diese CUG-Richtlinien werden anhand eines separaten Autorisierungsmoduls namens „oak-authorization-cug“ auf einer AEM-Instanz bereitgestellt. Dieses Modul verfügt über eine eigene Zugriffssteuerungsverwaltung und Berechtigungsprüfung. Das heißt, die standardmäßige AEM-Einrichtung enthält eine Oak Content Repository-Konfiguration, die mehrere Autorisierungsmechanismen kombiniert. Weitere Informationen finden Sie auf [dieser Seite auf der Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

In dieser Verbundeinrichtung ersetzen neue CUGs nicht den vorhandenen Zugriffssteuerungsinhalt, der dem Zielknoten angehängt ist, sondern sind als Zusatz entworfen, der später ebenso entfernt werden kann, ohne die ursprüngliche Zugriffssteuerung zu beeinträchtigen, die in AEM standardmäßig eine Zugriffssteuerungsliste darstellen würde.

Im Gegensatz zur früheren Implementierung werden die neuen CUG-Richtlinien immer als Zugriffssteuerungsinhalte erkannt und behandelt. Dies bedeutet, dass sie mit der JCR-Zugriffssteuerungs-Management-API erstellt und bearbeitet werden. Weitere Informationen finden Sie im Abschnitt [Verwalten von CUG-Richtlinien](#managing-cug-policies).

#### Berechtigungsprüfung von CUG-Richtlinien {#permission-evaluation-of-cug-policies}

Neben einer dedizierten Zugriffssteuerungsverwaltung für CUGs können Sie mit dem neuen Autorisierungsmodell die Berechtigungsprüfung für die Richtlinien bedingt aktivieren. Auf diese Weise können Sie CUG-Richtlinien in einer Staging-Umgebung einrichten und nur die Auswertung der effektiven Berechtigungen aktivieren, nachdem diese in die Produktionsumgebung repliziert wurden.

Die Berechtigungsprüfung für CUG-Richtlinien und die Interaktion mit dem standardmäßigen oder zusätzlichen Autorisierungsmodellen folgen dem Muster, das für mehrere Autorisierungsmechanismen in Apache Jackrabbit Oak entworfen wurde: Ein gegebener Berechtigungssatz wird gewährt, falls – und nur falls – alle Modelle Zugriff erteilen. Weitere Informationen finden Sie auf [dieser Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

Die folgenden Merkmale gelten für die Berechtigungsprüfung im Zusammenhang mit dem Autorisierungsmodell zur Verarbeitung und Bewertung von CUG-Richtlinien:

* Sie verarbeitet nur Leseberechtigungen für reguläre Knoten und Eigenschaften, nicht jedoch Lesezugriffssteuerungsinhalte
* Es werden keine Schreibberechtigungen und keine Berechtigungen verwaltet, die für die Änderung geschützter JCR-Inhalte erforderlich sind (Zugriffskontrolle, Informationen zum Knotentyp, Versionierung, Sperren oder Benutzerverwaltung usw.). Diese Berechtigungen sind von einer CUG-Richtlinie nicht betroffen und werden vom zugehörigen Autorisierungsmodell nicht bewertet. Ob diese Berechtigungen gewährt werden, hängt von den anderen Modellen ab, die in der Sicherheitseinrichtung konfiguriert sind.

Der Effekt einer einzelnen CUG-Richtlinie auf die Berechtigungsprüfung kann wie folgt zusammengefasst werden:

* Lesezugriff wird allen vorenthalten, außer Subjekten, die ausgeschlossene oder aufgeführte Prinzipale enthalten.
* Die Richtlinie wirkt sich auf den zugriffsgesteuerten Knoten aus, der die Richtlinie und ihre Eigenschaften enthält.
* Der Effekt wird zusätzlich in der Hierarchie vererbt, d. h. in der Elementstruktur, die vom zugriffsgesteuerten Knoten definiert wird.
* Sie betrifft jedoch weder Geschwister noch Vorgänger des zugriffsgesteuerten Knotens.
* Die Vererbung einer bestimmten CUG stoppt bei einer verschachtelten CUG.

#### Best Practices {#best-practices}

Die folgenden Best Practices sollten bei der Definition des eingeschränkten Lesezugriffs über CUGs berücksichtigt werden:

* Entscheiden Sie bewusst, ob Sie die CUG benötigen, um Lesezugriff einzuschränken oder die Authentifizierung zu erzwingen. Wenn letzteres der Fall ist oder beides erforderlich ist, finden Sie im Abschnitt Best Practices weitere Informationen zur Authentifizierungspflicht.
* Erstellen Sie ein Bedrohungsmodell für die Daten oder Inhalte, die geschützt werden müssen, um Bedrohungsgrenzen zu identifizieren und ein klares Bild der Vertraulichkeit der Daten und der Rollen im Zusammenhang mit dem autorisierten Zugriff zu erhalten.
* Modellieren des Repository-Inhalts und der CUGs unter Berücksichtigung allgemeiner autorisierungsbezogener Aspekte und Best Practices:

   * Beachten Sie, dass die Leseberechtigung nur erteilt wird, wenn eine bestimmte CUG und die Auswertung anderer im Setup bereitgestellter Module es einem bestimmten Subjekt erlauben, ein bestimmtes Repository-Element zu lesen
   * Vermeiden Sie das Erstellen redundanter CUGs, bei denen der Lesezugriff bereits durch andere Autorisierungsmodule eingeschränkt ist.
   * Ein übermäßiger Bedarf an verschachtelten CUGs kann Probleme beim Inhaltserstellung hervorheben
   * Ein sehr übermäßiger Bedarf an CUGs (z. B. auf jeder einzelnen Seite) kann auf die Notwendigkeit eines benutzerdefinierten Autorisierungsmodells hinweisen, das möglicherweise besser auf die spezifischen Sicherheitsanforderungen der vorliegenden Anwendung und des vorliegenden Inhalts abgestimmt ist.

* Beschränken Sie die für CUG-Richtlinien unterstützten Pfade auf einige Bäume im Repository, um eine optimierte Leistung zu ermöglichen. Lassen Sie CUGs beispielsweise nur unterhalb des Knotens „/content“ zu, wie seit Einführung von AEM 6.3 standardmäßig festgelegt ist.
* CUG-Richtlinien sind so konzipiert, dass sie Lesezugriff auf eine kleine Gruppe von Prinzipalen gewähren. Die Notwendigkeit einer großen Anzahl von Prinzipalen kann Probleme beim Inhalt oder Anwendungsdesign hervorheben und sollte überdacht werden.

### Authentifizierung: Authentifizierungspflicht definieren {#authentication-defining-the-auth-requirement}

Mit den authentifizierungsbezogenen Teilen der CUG-Funktion können Sie Bäume markieren, die authentifiziert werden müssen, und optional eine dedizierte Anmeldeseite angeben. In Übereinstimmung mit der vorherigen Version können Sie mit der neuen Implementierung Bäume markieren, die eine Authentifizierung im Content Repository erfordern, und die Synchronisierung mit dem `Sling org.apache.sling.api.auth.Authenticator`verantwortlich für die Durchsetzung der Anforderung und die Umleitung zu einer Anmelderessource.

Diese Anforderungen werden mit dem Authenticator anhand eines OSGi-Dienstes registriert, der die Registrierungseigenschaft `sling.auth.requirements` zur Verfügung stellt. Diese Eigenschaften werden dann verwendet, um die Authentifizierungsanforderungen dynamisch zu erweitern. Weitere Informationen finden Sie im [Sling-Dokumentation](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### Definieren der Authentifizierungspflicht mit einem dedizierten Mixin-Typ {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Aus Sicherheitsgründen ersetzt die neue Implementierung die Verwendung einer übrigen JCR-Eigenschaft durch einen dedizierten Mixin-Typ mit der Bezeichnung `granite:AuthenticationRequired`. Er definiert eine einzelne optionale Eigenschaft des Typs STRING für den Anmeldepfad `granite:loginPath`. Nur Inhaltsänderungen mit Bezug zu diesem Mixin-Typ führen zur Aktualisierung der beim Apache Sling Authenticator registrierten Anforderungen. Die Änderungen werden nachverfolgt, wenn Übergangsänderungen beibehalten werden, daher muss `javax.jcr.Session.save()` aufgerufen werden, damit die Änderungen wirksam werden.

Dasselbe gilt für die Eigenschaft `granite:loginPath`. Sie wird nur berücksichtigt, wenn sie von dem Mixin-Typ definiert wird, der mit der Authentifizierungspflicht zusammenhängt. Wird eine Resteigenschaft mit genau diesem Namen einem nicht strukturierten JCR-Knoten hinzugefügt, hat dies nicht den gewünschten Effekt und die Eigenschaft wird von dem Handler ignoriert, der für die Aktualisierung der OSGi-Registrierung zuständig ist.

>[!NOTE]
>
>Das Festlegen der Eigenschaft für den Anmeldepfad ist optional und nur erforderlich, wenn der Baum, der die Authentifizierung erfordert, nicht auf die standardmäßige oder anderweitig geerbte Anmeldeseite zurückgesetzt werden kann. Siehe [Auswertung des Anmeldepfads](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path) unten.

#### Registrieren der Authentifizierungspflicht und des Anmeldepfads mit dem Sling Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Da diese Art der Authentifizierungspflicht nur auf bestimmte Ausführungsmodi und auf eine kleine Teilmenge von Baumstrukturen innerhalb des Content-Repository beschränkt sein soll, ist das Tracking des Mixin-Typs der Anforderung und der Anmeldepfadeigenschaften eine Bedingung und gebunden an eine entsprechende Konfiguration, welche die unterstützten Pfade definiert (siehe „Konfigurationsoptionen“ weiter unten). Daher lösen nur Änderungen im Rahmen dieser unterstützten Pfade eine Aktualisierung der OSGi-Registrierung aus. Ansonsten werden der Mixin-Typ und die Eigenschaft ignoriert.

Die standardmäßige Einrichtung von AEM nutzt nun diese Konfiguration, indem sie ermöglicht, für den Mixin-Typ den Autorenausführungsmodus festzulegen, ihn aber erst wirksam werden zu lassen, wenn er auf die Veröffentlichungsinstanz repliziert wurde. Auf [dieser Seite](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) finden Sie Einzelheiten dazu, wie Sling die Authentifizierungspflicht durchsetzt.

Hinzufügen der `granite:AuthenticationRequired` Der Mixin-Typ innerhalb der konfigurierten unterstützten Pfade führt dazu, dass die OSGi-Registrierung des verantwortlichen Handlers mit einem neuen, zusätzlichen Eintrag mit dem `sling.auth.requirements` -Eigenschaft. Wenn eine gegebene Authentifizierungspflicht die optionale Eigenschaft `granite:loginPath` angibt, wird der Wert zusätzlich beim Authenticator mit dem Präfix „-“ registriert, um von der Authentifizierungspflicht ausgeschlossen zu werden.

#### Prüfung und Vererbung der Authentifizierungspflicht {#evaluation-and-inheritance-of-the-authentication-requirement}

Von Apache Sling-Authentifizierungsanforderungen wird erwartet, dass sie über die Seiten- oder Knotenhierarchie übernommen werden. Die genauen Details der Vererbung und die Bewertung der Authentifizierungsanforderungen wie Reihenfolge und Priorität werden als Implementierungsdetails betrachtet und in diesem Artikel nicht dokumentiert.

#### Auswertung des Anmeldepfads {#evaluation-of-login-path}

Die Prüfung des Anmeldepfads und die Weiterleitung an die entsprechende Ressource bei Authentifizierung sind derzeit Implementierungsdetails von Adobe Granite Login Selector Authentication Handler (`com.day.cq.auth.impl.LoginSelectorHandler`), einem Apache Sling-AuthenticationHandler, der standardmäßig mit AEM konfiguriert ist.

Nach dem Aufruf von `AuthenticationHandler.requestCredentials` versucht dieser Handler, die Zuordnungsanmeldeseite zu identifizieren, an die der Benutzer weitergeleitet wird. Dazu gehören die folgenden Schritte:

* Unterscheidung zwischen abgelaufenem Passwort und Notwendigkeit einer regelmäßigen Anmeldung als Grund für die Umleitung;
* Bei einer regulären Anmeldung wird in der folgenden Reihenfolge geprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom LoginPathProvider (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * und gehen Sie dann zurück zur standardmäßigen Anmeldeseite, wie mit der Variablen `LoginSelectorHandler`.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

Das Ziel dieser Dokumentation ist die Prüfung des Anmeldepfads, wie er von der internen Schnittstelle `LoginPathProvider` angezeigt wird. Die seit AEM 6.3 ausgelieferte Implementierung verhält sich wie folgt:

* Die Registrierung von Anmeldepfaden hängt davon ab, ob zwischen abgelaufenem Passwort und der Notwendigkeit einer regulären Anmeldung als Grund für die Umleitung unterschieden wird.
* Bei regulärer Anmeldung wird in der folgenden Reihenfolge geprüft, ob ein Anmeldepfad abgerufen werden kann:

   * vom `LoginPathProvider` (entsprechend der Implementierung des neuen `com.adobe.granite.auth.requirement.impl.RequirementService`)
   * von der veralteten CUG-Implementierung
   * von den Anmeldeseitenzuordnungen (entsprechend der mit dem `LoginSelectorHandler` erstellten Definition)
   * und kehren schließlich zur standardmäßigen Anmeldeseite zurück, wie mit der Variablen `LoginSelectorHandler`.

* Sobald anhand der oben genannten Aufrufe ein gültiger Anmeldepfad abgerufen wurde, wird die Anforderung des Benutzers an diese Seite weitergeleitet.

`LoginPathProvider` zeigt anhand der Implementierung der neuen Authentifizierungspflichtunterstützung in Granite Anmeldepfade, wie sie anhand der `granite:loginPath`-Eigenschaften definiert sind, die wiederum wie oben beschrieben vom Mixin-Typ definiert werden. Die Zuordnung des Ressourcenpfads mit dem Anmeldepfad und dem Eigenschaftswert selbst wird im Speicher beibehalten und ausgewertet, um einen geeigneten Anmeldepfad für andere Knoten in der Hierarchie zu finden.

>[!NOTE]
>
>Die Auswertung wird nur für Anfragen durchgeführt, die mit Ressourcen verknüpft sind, die sich in den konfigurierten unterstützten Pfaden befinden. Für alle anderen Anfragen werden die alternativen Methoden zur Bestimmung des Anmeldepfads ausgewertet.

#### Best Practices {#best-practices-1}

Bei der Definition von Authentifizierungsanforderungen sollten die folgenden Best Practices berücksichtigt werden:

* Vermeiden Sie Verschachtelung von Authentifizierungsanforderungen: Die Platzierung einer einzelnen Authentifizierungspflicht-Markierung am Anfang eines Baums sollte ausreichend sein und wird an die gesamte vom Zielknoten definierte Unterstruktur vererbt. Zusätzliche Authentifizierungsanforderungen in diesem Baum sollten als redundant betrachtet werden und können bei der Bewertung der Authentifizierungspflicht in Apache Sling zu Leistungsproblemen führen. Durch die Trennung von Autorisierungs- und authentifizierungsbezogenen CUG-Bereichen ist es möglich, den Lesezugriff durch CUG oder andere Richtlinien zu beschränken und gleichzeitig die Authentifizierung für den gesamten Baum zu erzwingen.
* Modellieren Sie Repository-Inhalte so, dass Authentifizierungsanforderungen für die gesamte Baumstruktur gelten, ohne verschachtelte Unterbäume erneut von der Anforderung ausschließen zu müssen.
* Zur Vermeidung genauer Angaben und der darauf folgenden Registrierung redundanter Anmeldepfade:

   * Nutzen Sie die Vererbung und vermeiden Sie die Definition verschachtelter Anmeldepfade.
   * Legen Sie für den optionalen Anmeldepfad keinen Wert fest, der dem Standardwert oder einem vererbten Wert entspricht.
   * Anwendungsentwickler müssen identifizieren, welche Anmeldepfade in den globalen „login-path“-Konfigurationen (Standard und Zuordnungen) konfiguriert werden müssen, die mit dem `LoginSelectorHandler` verknüpft sind.

## Darstellung im Repository {#representation-in-the-repository}

### Darstellung von CUG-Richtlinien im Repository {#cug-policy-representation-in-the-repository}

Die Oak-Dokumentation beschreibt, wie die neuen CUG-Richtlinien im Repository-Content dargestellt werden. Weitere Informationen finden Sie unter [diese Seite](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Authentifizierungspflicht im Repository {#authentication-requirement-in-the-repository}

Die Notwendigkeit einer separaten Authentifizierungspflicht zeigt sich im Repository-Content anhand eines dedizierten Mixin-Knotentyps am Zielknoten. Der Mixin-Typ definiert eine optionale Eigenschaft, um eine dedizierte Anmeldeseite für die vom Zielknoten definierte Baumstruktur anzugeben.

Die mit dem Anmeldepfad verknüpfte Seite kann sich innerhalb oder außerhalb dieses Baums befinden. Sie wird von der Authentifizierungspflicht ausgeschlossen.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Verwalten von CUG-Richtlinien und Authentifizierungspflichten {#managing-cug-policies-and-authentication-requirement}

### Verwalten von CUG-Richtlinien {#managing-cug-policies}

Der neue Richtlinientyp für die Zugriffssteuerung, mit dem der Lesezugriff für eine CUG eingeschränkt wird, wird mithilfe der JCR-Zugriffssteuerungsverwaltungs-API verwaltet und folgt den Mechanismen, die in der [Beschreibung von JCR 2.0](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) aufgeführt werden.

#### Neue CUG-Richtlinie festlegen {#set-a-new-cug-policy}

Code zum Anwenden einer neuen CUG-Richtlinie auf einen Knoten, für den zuvor keine CUG festgelegt wurde. `getApplicablePolicies` gibt nur neue Richtlinien zurück, die noch nie festgelegt wurden. Am Ende muss die Richtlinie zurückgeschrieben und Änderungen müssen beibehalten werden.

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

Die JCR-Zugriffssteuerungsverwaltung definiert eine Methode mit bestem Aufwand, um die Richtlinien abzurufen, die an einem bestimmten Pfad wirksam werden. Da die Auswertung von CUG-Richtlinien bedingt ist und von der entsprechenden Konfiguration abhängt, die aktiviert werden soll, muss `getEffectivePolicies` ist eine praktische Methode, um zu überprüfen, ob eine bestimmte CUG-Richtlinie in einer bestimmten Installation wirksam wird.

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

#### Vererbte CUG-Richtlinien abrufen {#retrieve-inherited-cug-policies}

Suchen aller verschachtelten CUGs, die an einem bestimmten Pfad definiert wurden, unabhängig davon, ob sie wirksam werden oder nicht. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options) Abschnitt.

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

Die von `JackrabbitAccessControlManager` definierten Erweiterungen, welche die Bearbeitung von Zugriffssteuerungsrichtlinien nach Prinzipalen ermöglichen, werden nicht anhand der CUG-Zugriffssteuerungsverwaltung implementiert, da CUG-Richtlinien per Definition immer alle Prinzipale betreffen: Den mit `PrincipalSetPolicy` aufgeführten Prinzipalen wird Lesezugriff gewährt, während alle anderen Prinzipale in der vom Zielknoten definierten Baumstruktur keine Inhalte lesen können.

Die entsprechenden Methoden geben immer ein leeres Richtlinien-Array zurück, geben jedoch keine Ausnahmen aus.

### Verwalten der Authentifizierungspflicht {#managing-the-authentication-requirement}

Das Erstellen, Ändern oder Entfernen einer neuen Authentifizierungspflicht wird erreicht, indem der effektive Knotentyp des Zielknotens geändert wird. Die optionale Anmeldepfadeigenschaft kann dann mit der normalen JCR-API geschrieben werden.

>[!NOTE]
>
>Die oben genannten Änderungen an einem bestimmten Zielknoten werden nur dann im Apache Sling Authenticator übernommen, wenn der `RequirementHandler` konfiguriert und das Ziel in den von den unterstützten Pfaden definierten Baumstrukturen vorhanden ist (siehe Abschnitt „Konfigurationsoptionen“).
>
>Weitere Informationen finden Sie unter [Zuweisen von Mixin-Knotentypen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Assigning Mixin Node Types) und [Hinzufügen von Knoten und Festlegen von Eigenschaften](https://docs.adobe.com/docs/de-DE/spec/jcr/2.0/10_Writing.html#10.4 Hinzufügen von Knoten und Festlegen von Eigenschaften).

#### Hinzufügen einer neuen Authentifizierungspflicht {#adding-a-new-auth-requirement}

Die Schritte zum Erstellen einer neuen Authentifizierungspflicht werden nachfolgend beschrieben. Die Pflicht wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Hinzufügen einer neuen Authentifizierungspflicht mit dem Anmeldepfad {#add-a-new-auth-requirement-with-login-path}

Schritte zum Erstellen einer neuen Authentifizierungspflicht, einschließlich eines Anmeldepfads. Die Pflicht und die Ausnahme für den Anmeldepfad wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Vorhandenen Anmeldepfad ändern {#modify-an-existing-login-path}

Die Schritte zum Ändern eines vorhandenen Anmeldepfads werden nachfolgend beschrieben. Die Änderung wird nur dann beim Apache Sling Authenticator registriert, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Der Wert des vorherigen Anmeldepfads wird aus der Registrierung entfernt. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht wird von dieser Änderung nicht beeinflusst.

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

Schritte zum Entfernen eines vorhandenen Anmeldepfads. Die Registrierung des Anmeldepfadeintrags wird nur dann aus dem Apache Sling Authenticator entfernt, wenn der `RequirementHandler` für die Baumstruktur mit dem Zielknoten konfiguriert wurde. Die mit dem Zielknoten verknüpfte Authentifizierungspflicht ist nicht betroffen.

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

Oder Sie können die folgende Methode verwenden, um denselben Zweck zu erreichen:

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

Die folgende Abbildung zeigt die Authentifizierungsanforderungen einer AEM Veröffentlichungsinstanz mit Demoinhalt. Der hervorgehobene Pfad der Community-Seite zeigt, wie eine von der in diesem Dokument beschriebenen Implementierung hinzugefügte Anforderung im Apache Sling Authenticator dargestellt wird.

>[!NOTE]
>
>In diesem Beispiel wurde die optionale Eigenschaft des Anmeldepfads nicht festgelegt. Folglich wurde kein zweiter Eintrag beim Authentifizierer registriert.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Abrufen des effektiven Anmeldepfads {#retrieve-the-effective-login-path}

Derzeit gibt es keine öffentliche API zum Abrufen des Anmeldepfads, der verwendet wird, wenn anonym auf eine Ressource zugegriffen wird, die eine Authentifizierung erfordert. Implementierungsdetails dazu, wie der Anmeldepfad abgerufen wird, finden Sie unter Bewertung des Anmeldepfads .

Beachten Sie jedoch, dass es neben den mit dieser Funktion definierten Anmeldepfaden alternative Möglichkeiten gibt, die Weiterleitung zur Anmeldung anzugeben, die bei der Erstellung des Inhaltsmodells und der Authentifizierungsanforderungen einer bestimmten AEM berücksichtigt werden sollten.

#### Abrufen der geerbten Authentifizierungspflicht {#retrieve-the-inherited-auth-requirement}

Wie beim Anmeldepfad gibt es keine öffentliche API zum Abrufen der im Inhalt definierten geerbten Authentifizierungsanforderungen. Das folgende Beispiel zeigt, wie alle Authentifizierungspflichten aufgeführt werden, die mit einer bestimmten Hierarchie definiert wurden, unabhängig davon, ob sie wirksam sind oder nicht. Weitere Informationen finden Sie unter [Konfigurationsoptionen](/help/sites-administering/closed-user-groups.md#configuration-options).

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

In der folgenden Tabelle sind die gültigen Kombinationen von CUG-Richtlinien und die Authentifizierungspflicht in einer AEM Instanz aufgeführt, in der beide Module durch Konfiguration aktiviert sind.

| **Authentifizierung erforderlich** | **Anmeldepfad** | **Eingeschränkter Lesezugriff** | **Erwarteter Effekt** |
|---|---|---|---|
| Ja | Ja | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird an die angegebene Anmeldeseite umgeleitet. |
| Ja | Nein | Ja | Ein bestimmter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. |
| Ja | Ja | Nein | Ein nicht authentifizierter Benutzer wird an die angegebene Anmeldeseite umgeleitet. Ob es erlaubt ist, die mit der Authentifizierungspflicht markierte Baumstruktur anzuzeigen, hängt von den effektiven Berechtigungen der einzelnen Elemente in dem Teilbaum ab. Es gibt keine dedizierte CUG, die den Lesezugriff einschränkt. |
| Ja | Nein | Nein | Ein nicht authentifizierter Benutzer wird an eine übernommene Standardanmeldeseite umgeleitet. Ob die mit der Authentifizierungspflicht markierte Baumstruktur angezeigt werden kann, hängt von den effektiven Berechtigungen der einzelnen Elemente in dieser Unterstruktur ab. Es gibt keine dedizierte CUG, die den Lesezugriff einschränkt. |
| Nein | Nein | Ja | Ein bestimmter authentifizierter oder nicht authentifizierter Benutzer kann den mit der CUG-Richtlinie markierten Teilbaum nur anzeigen, wenn die effektive Berechtigungsprüfung den Zugriff gewährt. Ein nicht authentifizierter Benutzer wird gleich behandelt und nicht zur Anmeldung weitergeleitet. |

>[!NOTE]
>
>Die Kombination „Authentifizierungspflicht = Ja“ und „Anmeldepfad = Ja“ wird oben nicht angeführt, da es sich beim Anmeldepfad um eine optionales, mit einer Authentifizierungspflicht verknüpftes Attribut handelt. Wird eine JCR-Eigenschaft mit diesem Namen ohne den definierenden Mixin-Typ angegeben, so hat dies keine Auswirkungen und der entsprechende Handler ignoriert die Eigenschaft.

## OSGi-Komponenten und -Konfiguration {#osgi-components-and-configuration}

Dieser Abschnitt bietet einen Überblick über die OSGi-Komponenten und die einzelnen Konfigurationsoptionen, die mit der neuen CUG-Implementierung eingeführt wurden.

Eine umfassende Zuordnung der Konfigurationsoptionen zwischen der alten und der neuen Implementierung finden Sie in der Dokumentation zur CUG-Zuordnung .

### Autorisierung: Einrichtung und Konfiguration {#authorization-setup-and-configuration}

Die neuen Teile, die sich auf die Zulassung beziehen, sind im **Oak CUG-Autorisierung** Bundle ( `org.apache.jackrabbit.oak-authorization-cug`), die Teil der AEM Standardinstallation ist. Das Bundle definiert ein separates Autorisierungsmodell, das als zusätzliche Methode zur Verwaltung des Lesezugriffs bereitgestellt werden soll.

#### Einrichten der CUG-Autorisierung {#setting-up-cug-authorization}

Das Einrichten der CUG-Autorisierung wird in der [relevanten Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) detailliert beschrieben. Standardmäßig AEM die CUG-Autorisierung in allen Ausführungsmodi bereitgestellt. Die schrittweise Anleitung kann auch verwendet werden, um die CUG-Autorisierung in Installationen zu deaktivieren, die eine andere Autorisierung erfordern.

#### Konfigurieren des Referrer-Filters {#configuring-the-referrer-filter}

Sie müssen außerdem den [Sling Referrer-Filter](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) mit allen Host-Namen konfigurieren, die für den Zugriff auf AEM verwendet werden können, z. B. via CDN oder Lastenausgleich.

Wenn der Referrer-Filter nicht konfiguriert ist, treten Fehler wie die folgende auf, wenn ein Benutzer versucht, sich bei einer CUG-Site anzumelden:

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### Eigenschaften von OSGi-Komponenten {#characteristics-of-osgi-components}

Die folgenden beiden OSGi-Komponenten wurden eingeführt, um Authentifizierungspflichten zu definieren und dedizierte Anmeldepfade anzugeben:

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

Die verfügbaren Konfigurationsoptionen, die mit dem CUG-Autorisierungsmodul verbunden sind, sind im Abschnitt [Dokumentation zu Apache Oak](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration).

#### Ausschluss von Prinzipalen aus der CUG-Auswertung {#excluding-principals-from-cug-evaluation}

Die Befreiung einzelner Prinzipale von der CUG-Bewertung wurde von der früheren Implementierung übernommen. Die neue CUG-Autorisierung behandelt dies anhand einer dedizierten Schnittstelle mit der Bezeichnung „CugExclude“. Apache Jackrabbit Oak 1.4 umfasst eine Standardimplementierung, die einen festen Satz von Prinzipalen sowie eine erweiterte Implementierung umfasst, welche die Konfiguration individueller Prinzipalnamen ermöglicht. Letztere wird in AEM Veröffentlichungsinstanzen konfiguriert.

Der Standardwert seit AEM 6.3 verhindert, dass die folgenden Prinzipale von CUG-Richtlinien betroffen sind:

* Administratorprinzipale (Admin-Benutzer, Administratorgruppe)
* Service-Benutzerprinzipale
* Repository-interner Systemprinzipal

Weitere Informationen finden Sie in der Tabelle im [Standardkonfiguration seit AEM 6.3](#default-configuration-since-aem) unten.

Die Ausnahme der Administratorgruppe kann in der Systemkonsole im Konfigurationsabschnitt **Apache Jackrabbit Oak CUG Exclude List** geändert oder erweitert werden.

Alternativ ist es möglich, eine benutzerdefinierte Bereitstellung der CugExclude-Schnittstelle bereitzustellen, um den Satz ausgenommener Prinzipale im Falle spezieller Anforderungen anzupassen. Weitere Informationen sowie eine Beispielimplementierung finden Sie in der Dokumentation zu [CUG-Austauschbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability).

### Authentifizierung: Einrichtung und Konfiguration {#authentication-setup-and-configuration}

Die neuen, authentifizierungsbezogenen Teile sind im **Adobe Granite Authentication Handler** Bundle ( `com.adobe.granite.auth.authhandler` Version 5.6.48). Dieses Bundle ist Teil der AEM Standardinstallation.

Um den Ersatz der Authentifizierungspflicht für die veraltete CUG-Unterstützung einzurichten, müssen einige OSGi-Komponenten in einer bestimmten AEM vorhanden und aktiv sein. Weitere Informationen finden Sie unter **Eigenschaften von OSGi-Komponenten** unten.

>[!NOTE]
>
>Aufgrund der obligatorischen Konfigurationsoption mit dem RequirementHandler sind die authentifizierungsbezogenen Teile nur aktiv, wenn die Funktion durch Angabe einer Reihe unterstützter Pfade aktiviert wurde. Bei einer standardmäßigen AEM-Installation ist die Funktion im Autorenausführungsmodus deaktiviert und im Veröffentlichungsausführungsmodus für /content aktiviert.

**Eigenschaften von OSGi-Komponenten**

Die folgenden beiden OSGi-Komponenten wurden eingeführt, um Authentifizierungspflichten zu definieren und dedizierte Anmeldepfade anzugeben:

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

Die authentifizierungsbezogenen Teile des CUG-Rewrite enthalten nur eine Konfigurationsoption, die mit der Adobe Granite Authentication Requirement and Login Path Handler verknüpft ist:

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

## Standardkonfiguration seit AEM 6.3 {#default-configuration-since-aem}

Neue Installationen von AEM werden standardmäßig die neuen Implementierungen sowohl für die autorisierungs- als auch authentifizierungsbezogenen Teile der CUG-Funktion verwenden. Die alte Implementierung „Adobe Granite Closed User Group (CUG) Support“ ist veraltet und wird standardmäßig in allen Installationen von AEM deaktiviert. Die neuen Implementierungen werden stattdessen wie folgt aktiviert:

### Autoreninstanzen {#author-instances}

| **„Apache Jackrabbit Oak CUG Configuration“** | **Erklärung** |
|---|---|
| Unterstützte Pfade: `/content` | Die Zugriffssteuerungsverwaltung für „CUGpolicies“ ist aktiviert. |
| CUG-Prüfung aktiviert: FALSE | Die Berechtigungsprüfung ist deaktiviert. CUG-Richtlinien sind nicht wirksam. |
| Ranking | 200 | Siehe Oak-Dokumentation. |

>[!NOTE]
>
>Keine Konfiguration für **Apache Jackrabbit Oak CUG Exclude List** und **Adobe Granite-Authentifizierungspflicht und Anmeldungspfad-Handler** ist in Standard-Authoring-Instanzen vorhanden.

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
| Unterstützte Pfade: `/content` | Authentifizierungspflichten, die im Repository mithilfe des Mixin-Typs `granite:AuthenticationRequired` definiert wurden, werden in `/content` bei `Session.save()` wirksam. Sling Authenticator wird aktualisiert. Das Hinzufügen des Mixin-Typs außerhalb der unterstützten Pfade wird ignoriert. |

## Deaktivieren der CUG-Autorisierungs- und Authentifizierungspflicht {#disabling-cug-authorization-and-authentication-requirement}

Die neue Implementierung kann vollständig deaktiviert werden, wenn eine bestimmte Installation keine CUGs nutzt oder andere Authentifizierungs- und Autorisierungsmöglichkeiten verwendet.

### CUG-Autorisierung deaktivieren {#disable-cug-authorization}

Lesen Sie die [CUG-Pluggabelbarkeit](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) Dokumentation für Details zum Entfernen des CUG-Autorisierungsmodells aus der Composite-Autorisierungseinrichtung.

### Authentifizierungspflicht deaktivieren {#disable-the-authentication-requirement}

Zum Deaktivieren der Unterstützung der Authentifizierungspflicht, die vom Modul `granite.auth.authhandler` bereitgestellt wird, muss nur die Konfiguration entfernt werden, die mit **Adobe Granite Authentication Requirement and Login Path Handler** verknüpft ist.

>[!NOTE]
>
>Beachten Sie jedoch, dass das Entfernen der Konfiguration nicht dazu führt, dass die Registrierung des Mixin-Typs aufgehoben wird, der weiterhin für Knoten gilt, ohne wirksam zu werden.

## Interaktion mit anderen Modulen {#interaction-with-other-modules}

### Apache Jackrabbit-API {#apache-jackrabbit-api}

Um den neuen Typ der Zugriffssteuerungsrichtlinie widerzuspiegeln, die vom CUG-Autorisierungsmodell verwendet wird, wurde die von Apache Jackrabbit definierte API erweitert. Seit Version 2.11.0 definiert das Modul `jackrabbit-api` eine neue Schnittstelle mit der Bezeichnung `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die aus `javax.jcr.security.AccessControlPolicy` hervorgeht.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Der Importmechanismus von Apache Jackrabbit FileVault wurde angepasst, um mit Zugriffssteuerungsrichtlinien des Typs `PrincipalSetPolicy` umgehen zu können.

### Apache Sling-Inhaltsverteilung {#apache-sling-content-distribution}

Siehe oben [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault) Abschnitt.

### Adobe Granite-Replikation {#adobe-granite-replication}

Das Replikationsmodul wurde geringfügig angepasst, um die CUG-Richtlinien zwischen verschiedenen AEM-Instanzen replizieren zu können:

* `DurboImportConfiguration.isImportAcl()` wird wörtlich interpretiert und betrifft nur Zugriffssteuerungsrichtlinien, die `javax.jcr.security.AccessControlList` implementieren.

* `DurboImportTransformer` respektiert nur diese Konfiguration für echte ACLs.
* Andere Richtlinien, z. B. vom CUG-Autorisierungsmodell erstellte `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`-Instanzen, werden immer repliziert und die Konfigurationsoption `DurboImportConfiguration.isImportAcl`() wird ignoriert.

Es gibt eine Einschränkung hinsichtlich der Replikation von CUG-Richtlinien. Wenn eine CUG-Richtlinie entfernt wird, ohne dass der entsprechende Mixin-Knotentyp `rep:CugMixin,` entfernt wird, wird die Entfernung in der Replikation nicht berücksichtigt. Dies wurde behoben, indem das Mixin beim Entfernen der Richtlinie immer entfernt wurde. Die Einschränkung kann jedoch angezeigt werden, wenn der Mixin-Typ manuell hinzugefügt wird.

### Adobe Granite Authentication Handler {#adobe-granite-authentication-handler}

Der Authentifizierungs-Handler **Adobe Granite HTTP Header Authentication Handler** im Bundle `com.adobe.granite.auth.authhandler` verweist auf die Schnittstelle `CugSupport`, die vom selben Modul definiert wird. Sie wird unter bestimmten Bedingungen zur Berechnung des Bereichs verwendet, wobei auf den mit dem Handler konfigurierten Bereich ausgewichen wird.

Dies wurde angepasst, um den Verweis auf `CugSupport` optional zu machen, um die größtmögliche Abwärtskompatibilität zu erreichen, wenn eine Einrichtung entscheidet, die veraltete Implementierung erneut zu aktivieren. Für Installationen, welche die Implementierung verwenden, wird der Bereich nicht mehr aus der CUG-Implementierung extrahiert, stattdessen wird der Bereich immer als mit **Adobe Granite HTTP Header Authentication Handler** definiert angezeigt.

>[!NOTE]
>
>Standardmäßig ist der **Adobe Granite HTTP Header Authentication Handler** nur im Veröffentlichungsausführungsmodus mit aktivierter Option „Anmeldeseite deaktivieren“ (`auth.http.nologin`) konfiguriert.

### AEM Live Copy {#aem-livecopy}

Die Konfiguration von CUGs in Verbindung mit Live Copy wird im Repository durch das Hinzufügen eines zusätzlichen Knotens und einer zusätzlichen Eigenschaft wie folgt dargestellt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide Elemente werden unter `cq:Page` erstellt. Mit dem aktuellen Design verarbeitet MSM nur Knoten und Eigenschaften, die sich unter dem Knoten `cq:PageContent` (`jcr:content`) befinden.

Daher können CUG-Gruppen in Live Copies nicht aus Blueprints bereitgestellt werden. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Änderungen an der neuen CUG-Implementierung {#changes-with-the-new-cug-implementation}

Ziel dieses Abschnitts ist es, einen Überblick über die Änderungen an der CUG-Funktion sowie einen Vergleich zwischen der alten und der neuen Implementierung zu geben. Er listet die Änderungen auf, die sich auf die Konfiguration der CUG-Unterstützung auswirken, und beschreibt, wie und von wem CUGs im Repository-Inhalt verwaltet werden.

### Unterschiede bei CUG-Einrichtung und -Konfiguration {#differences-in-cug-setup-and-configuration}

Die veraltete OSGi-Komponente **Adobe Granite Closed User Group (CUG)-Unterstützung** ( `com.day.cq.auth.impl.cug.CugSupportImpl`) durch neue Komponenten ersetzt wurde, um die Autorisierung und authentifizierungsbezogene Teile der vorherigen CUG-Funktionalität separat handhaben zu können.

## Unterschiede beim Verwalten von CUGs im Repository-Content {#differences-in-managing-cugs-in-the-repository-content}

In den folgenden Abschnitten werden die Unterschiede zwischen den alten und den neuen Implementierungen aus der Implementierung und der Sicherheitsperspektive beschrieben. Obwohl die neue Implementierung darauf abzielt, die gleichen Funktionen bereitzustellen, gibt es geringfügige Änderungen, die bei der Verwendung der neuen CUG wichtig sind.

### Unterschiede bei der Zulassung {#differences-with-regards-to-authorization}

Im Folgenden finden Sie eine Zusammenfassung der wichtigsten Unterschiede hinsichtlich Autorisierung:

**Dedizierte Zugriffssteuerungsinhalte für CUGs**

In der alten Implementierung wurde das standardmäßige Autorisierungsmodell verwendet, um Zugriffssteuerungslisten-Richtlinien bei der Veröffentlichung zu bearbeiten und bestehende ACEs durch das von der CUG angeforderte Setup zu ersetzen. Dies wurde durch das Schreiben regulärer, verbleibender JCR-Eigenschaften ausgelöst, die bei der Veröffentlichung interpretiert wurden.

Mit der neuen Implementierung ist die Einrichtung der Zugriffskontrolle des Standardautorisierungsmodells nicht von der Erstellung, Änderung oder Entfernung einer CUG betroffen. Stattdessen wird ein neuer Typ von Richtlinie mit der Bezeichnung `PrincipalSetPolicy` als zusätzlicher Zugriffssteuerungsinhalt auf den Zielknoten angewendet. Diese zusätzliche Richtlinie ist ein untergeordnetes Element des Zielknotens und ist ein gleichrangiges Element des Standardrichtlinienknotens, falls dieser vorhanden ist.

**Bearbeiten von CUG-Richtlinien in der Zugriffssteuerungsverwaltung**

Dieser Wechsel von den restlichen JCR-Eigenschaften zu einer dedizierten Zugriffskontrollrichtlinie hat Auswirkungen auf die Berechtigung, die zum Erstellen oder Ändern des Autorisierungsteils der CUG-Funktion erforderlich ist. Da dies eine Modifikation am Zugriffssteuerungsinhalt darstellt, sind die Berechtigungen `jcr:readAccessControl` und `jcr:modifyAccessControl` für das Schreiben in das Repository erforderlich. Daher können nur Inhaltsautoren, die berechtigt sind, den Inhalt der Zugriffskontrolle einer Seite zu ändern, diesen Inhalt einrichten oder ändern. Dies steht im Gegensatz zur alten Implementierung, bei der die Möglichkeit zum Schreiben regulärer JCR-Eigenschaften ausreichend war, was zu einer Berechtigungseskalation führte.

**Von Richtlinie definierter Zielknoten**

Es wird erwartet, dass CUG-Richtlinien auf dem JCR-Knoten erstellt werden, der die Unterstruktur definiert, die eingeschränktem Lesezugriff unterliegen soll. Dies ist wahrscheinlich eine AEM Seite, falls die CUG voraussichtlich die gesamte Baumstruktur betrifft.

Wird die CUG-Richtlinie am Knoten „jcr:content“ unterhalb einer bestimmten Seite platziert, so wird nur der Zugriff auf den Inhalt (im engeren Sinn) einer bestimmten Seite eingeschränkt, wobei die Richtlinie keine Auswirkungen auf gleichrangige oder untergeordnete Seiten hat. Dies kann ein gültiger Anwendungsfall sein, und es ist möglich, dies mit einem Repository-Editor zu erreichen, der es ermöglicht, feinkörnigen Zugriffsinhalt anzuwenden. Sie steht jedoch im Gegensatz zur früheren Implementierung, bei der das Platzieren einer cq:cugEnabled -Eigenschaft auf dem Knoten jcr:content intern zum Seitenknoten neu zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

**Berechtigungsprüfung mit CUG-Richtlinien**

Die Umstellung von der alten CUG-Unterstützung auf ein zusätzliches Autorisierungsmodell verändert die Art und Weise, wie wirksame Leseberechtigungen geprüft werden. Wie in der [Jackrabbit-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) beschrieben, wird einem jeweiligen Prinzipal mit der Berechtigung zum Anzeigen von `CUGcontent` nur dann Lesezugriff gewährt, wenn die Berechtigungsprüfung aller im Oak-Repository konfigurierten Modelle Lesezugriff gewährt.

Anders ausgedrückt, bei der Auswertung der wirksamen Berechtigungen werden sowohl `CUGPolicy` als auch die standardmäßigen Zugriffssteuerungseinträge berücksichtigt. Lesezugriff auf den CUG-Inhalt wird nur gewährt, wenn beide Richtlinientypen ihn gewähren. In einer standardmäßigen Veröffentlichungsinstallation von AEM, in der jedem Lesezugriff auf die vollständige Baumstruktur `/content` gewährt wird, haben die CUG-Richtlinien dieselben Auswirkungen wie in der alten Implementierung.

**On-Demand-Auswertung**

Das CUG-Autorisierungsmodell ermöglicht es, die Zugriffskontrolle und Berechtigungsprüfung einzeln zu aktivieren:

* Die Zugriffssteuerungsverwaltung ist aktiviert, wenn das Modul über einen oder mehrere unterstützte Pfade verfügt, in denen CUGs erstellt werden können
* Berechtigungsprüfung ist nur aktiviert, wenn Option **CUG-Prüfung aktiviert** zusätzlich überprüft.

In der neuen Standardeinrichtung von AEM wird die Prüfung von CUG-Richtlinien nur im Ausführungsmodus „publish“ aktiviert. Zeigen Sie dazu die näheren Informationen zur [Standardkonfiguration seit Einführung von AEM 6.3](#default-configuration-since-aem) an. Dies lässt sich durch den Vergleich der wirksamen Richtlinien eines Pfads mit den im Inhalt gespeicherten Richtlinien verifizieren. Wirksame Richtlinien werden nur angezeigt, wenn die Berechtigungsprüfung für CUGs aktiviert ist.

Wie oben erklärt, werden die CUG-Zugriffssteuerungsrichtlinien nicht immer im Inhalt gespeichert, aber die Prüfung der gültigen Berechtigungen, die aus diesen Richtlinien hervorgehen, wird nur durchgesetzt, wenn in der Systemkonsole in der **CUG-Konfiguration** von Apache Jackrabbit Oak die Option **CUG-Prüfung aktiviert.** aktiviert ist. Standardmäßig wird sie nur im Ausführungsmodus „Veröffentlichen“ aktiviert.

### Unterschiede bei der Authentifizierung {#differences-with-regards-to-authentication}

Die Unterschiede bei der Authentifizierung werden nachfolgend beschrieben.

#### Dedizierter Mixin-Typ für Authentifizierungspflicht {#dedicated-mixin-type-for-authentication-requirement}

In der bisherigen Implementierung wurden die Autorisierungs- und Authentifizierungsaspekte einer CUG durch eine einzelne JCR-Eigenschaft ausgelöst (`cq:cugEnabled`). Insoweit die Authentifizierung betroffen ist, hat dies zu einer aktualisierten Liste von Authentifizierungspflichten geführt, die in der Apache Sling Authenticator-Implementierung gespeichert werden. Bei der neuen Implementierung wird dasselbe Ergebnis erzielt, indem der Zielknoten mit einem dedizierten Mixin-Typ (`granite:AuthenticationRequired`) markiert wird.

#### Eigenschaft zum Ausnehmen des Anmeldepfads {#property-for-excluding-login-path}

Der Mixin-Typ definiert eine einzelne optionale Eigenschaft mit der Bezeichnung `granite:loginPath`, die grundsätzlich der Eigenschaft `cq:cugLoginPage` entspricht. Im Gegensatz zur vorherigen Implementierung wird die Eigenschaft des Anmeldepfads nur berücksichtigt, wenn der deklarierende Knotentyp der erwähnte Mixin ist. Das Hinzufügen einer Eigenschaft mit diesem Namen ohne Festlegen des Mixin-Typs hat keine Auswirkungen, und weder eine neue Anforderung noch ein Ausschluss für den Anmeldepfad wird dem Authentifizierer gemeldet.

#### Berechtigung für Authentifizierungspflicht {#privilege-for-authentication-requirement}

Zum Hinzufügen oder Entfernen eines Mixin-Typs ist die Berechtigung `jcr:nodeTypeManagement` erforderlich. In der vorherigen Implementierung wurde zum Bearbeiten der Resteigenschaft die Berechtigung `jcr:modifyProperties` benötigt.

Soweit `granite:loginPath` betrifft die Berechtigung, die zum Hinzufügen, Ändern oder Entfernen der Eigenschaft erforderlich ist.

#### Vom Mixin-Typ definierter Zielknoten {#target-node-defined-by-mixin-type}

Authentifizierungspflichten sollen am JCR-Knoten erstellt werden und die Authentifizierungspflicht für den Teilbaum definieren. Dies ist wahrscheinlich eine AEM Seite, falls die CUG voraussichtlich die gesamte Baumstruktur betrifft und die Benutzeroberfläche für die neue Implementierung dementsprechend den Mixin-Typ auth-requirement auf dem Seitenknoten hinzufügt.

Wenn Sie die CUG-Richtlinie nur auf den Knoten jcr:content platzieren, der sich unter einer bestimmten Seite befindet, wird der Zugriff auf den Inhalt nur eingeschränkt, jedoch keine Auswirkungen auf den Seitenknoten selbst oder auf untergeordnete Seiten.

Dies kann ein gültiges Szenario sein. Sie erreichen dies mithilfe eines Repository-Editors, der die Platzierung des Mixin-Typs an allen Knoten ermöglicht. Allerdings stellt das Verhalten einen Kontrast zur vorherigen Implementierung dar, wo eine auf dem Knoten „jcr:content“ platzierte Eigenschaft „cq:cugEnabled“ oder „cq:cugLoginPage“ intern dem Seitenknoten zugeordnet wurde. Diese Zuordnung wird nicht mehr durchgeführt.

#### Konfigurierte unterstützte Pfade {#configured-supported-paths}

Sowohl der Mixin-Typ `granite:AuthenticationRequired` als auch die Eigenschaft „granite:loginPath“ werden nur innerhalb des Bereichs berücksichtigt, der durch den Konfigurationsoptionssatz **Unterstützte Pfade** in **Adobe Granite Authentication Requirement and Login Path Handler** definiert wird. Wenn keine Pfade angegeben sind, ist die Authentifizierungspflicht-Funktion vollständig deaktiviert. In diesem Fall werden weder der Mixin-Typ noch die Eigenschaft wirksam, wenn sie hinzugefügt oder auf einen JCR-Knoten festgelegt werden.

### Zuordnung von JCR-Inhalten, OSGi-Diensten und Konfigurationen {#mapping-of-jcr-content-osgi-services-and-configurations}

Das folgende Dokument bietet eine umfassende Zuordnung von OSGi-Diensten, Konfigurationen und Repository-Inhalten zwischen der alten und der neuen Implementierung.

CUG-Zuordnung seit Einführung von AEM 6.3

[Datei abrufen](assets/cug-mapping.pdf)

## CUG-Aktualisierung {#upgrade-cug}

### Vorhandene Installationen mit der veralteten CUG {#existing-installations-using-the-deprecated-cug}

Die alte Implementierung der CUG-Unterstützung ist veraltet und wird in zukünftigen Versionen entfernt. Es wird empfohlen, beim Upgrade von älteren Versionen als AEM 6.3 auf die neuen Implementierungen umzustellen.

Bei einer aktualisierten AEM ist es wichtig sicherzustellen, dass nur eine CUG-Implementierung aktiviert ist. Die Kombination der neuen und alten, veralteten CUG-Unterstützung wird nicht getestet und kann wahrscheinlich zu unerwünschtem Verhalten führen:

* Kollisionen im Sling Authenticator in Bezug auf Authentifizierungsanforderungen
* Lesezugriff verweigert, wenn das mit der alten CUG verknüpfte ACL-Setup mit einer neuen CUG-Richtlinie kollidiert.

### Migrieren vorhandener CUG-Inhalte {#migrating-existing-cug-content}

Adobe bietet ein Tool für die Migration zur neuen CUG-Implementierung. Führen Sie die folgenden Schritte aus, um sie zu verwenden:

1. Navigieren Sie zu `https://<serveraddress>:<serverport>/system/console/cug-migration`, um auf das Tool zuzugreifen.
1. Geben Sie den Stammpfad ein, für den Sie CUGs überprüfen möchten, und drücken Sie die **Ausführen von Trockenlauf** Schaltfläche. Dies löst am angegebenen Speicherort eine Suche nach CUGs aus, die konvertiert werden können.
1. Klicken Sie nach der Prüfung der Ergebnisse auf die Schaltfläche **Migration durchführen**, um zur neuen Implementierung zu migrieren.

>[!NOTE]
>
>Bei Problemen können Sie eine bestimmte Protokollfunktion auf **DEBUG**-Ebene unter `com.day.cq.auth.impl.cug` einrichten, um die Ausgabe des Migrations-Tools abzurufen. Weitere Informationen dazu finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
