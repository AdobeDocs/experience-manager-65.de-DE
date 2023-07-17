---
title: Dienstbenutzer in Adobe Experience Manager
description: Erfahren Sie mehr über Dienstbenutzer in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: ccd8577b-3bbf-40ba-9696-474545f07b84
feature: Security
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '1766'
ht-degree: 37%

---

# Dienstbenutzer in Adobe Experience Manager (AEM) {#service-users-in-aem}

## Übersicht {#overview}

Bisher erhielten Sie eine Admin-Sitzung oder einen Resource Resolver in AEM mithilfe der Sling-Methoden `SlingRepository.loginAdministrative()` und `ResourceResolverFactory.getAdministrativeResourceResolver()`.

Allerdings waren diese beiden Methoden um das sogenannte [Principle of Least Privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) (Prinzip der geringsten Berechtigung) aufgebaut und sie machen es Entwicklern zu einfach, anfangs eine angemessene Struktur und entsprechende Zugriffssteuerungsebenen für die Inhalte zu ignorieren. Wenn in einem solche Dienst eine Sicherheitslücke vorhanden ist, führt dies oft zu Berechtigungseskalationen an den `admin`, auch wenn der Code selbst keine Administratorrechte benötigt, um zu funktionieren.

## Ausstieg aus Admin-Sitzungen {#how-to-phase-out-admin-sessions}

### Priorität 0: Ist die Funktion aktiv/erforderlich/entfällt sie? {#priority-is-the-feature-active-needed-derelict}

Es kann vorkommen, dass die Adminsitzung nicht verwendet wird oder die Funktion vollständig deaktiviert ist. Ist dies mit Ihrer Implementierung der Fall, entfernen Sie die Funktion vollständig oder bauen Sie [Nulloperations-Code](https://en.wikipedia.org/wiki/NOP) darin ein.

### Priorität 1: Verwenden der Anforderungssitzung {#priority-use-the-request-session}

Ändern Sie nach Möglichkeit Ihre Funktion so, dass die angegebene, authentifizierte Anfragesitzung zum Lesen oder Schreiben von Inhalten verwendet werden kann. Wenn dies nicht möglich ist, kann dies oft durch die Anwendung der folgenden Prioritäten erreicht werden.

### Priorität 2: Inhalt neu strukturieren {#priority-restructure-content}

Viele Probleme können durch eine inhaltliche Umstrukturierung gelöst werden. Beachten Sie bei der Umstrukturierung die folgenden einfachen Regeln:

* **Zugriffskontrolle ändern**

   * Stellen Sie sicher, dass die Benutzer oder Gruppen, die wirklich Zugriff benötigen, tatsächlich Zugriff haben.

* **Inhaltsstruktur verfeinern**

   * Verschieben Sie sie an andere Stellen, z. B. wo die Zugriffssteuerung mit den verfügbaren Anfragesitzungen übereinstimmt.
   * Ändern der Inhaltsgranularität;

* **Code zum korrekten Dienst refaktorieren**

   * Verschieben Sie die Geschäftslogik vom JSP-Code in den Dienst. Dies ermöglicht eine unterschiedliche Inhaltsmodellierung.

Stellen Sie außerdem sicher, dass alle neuen Funktionen, die Sie entwickeln, diesen Grundsätzen entsprechen:

* **Sicherheitsanforderungen sollten die Inhaltsstruktur bestimmen**

   * Die Zugriffskontrolle sollte sich als selbstverständlich erweisen
   * Die Zugriffskontrolle muss vom Repository durchgesetzt werden, nicht von der Anwendung

* **Verwenden von Knotentypen**

   * Beschränken Sie den Satz von Eigenschaften, die festgelegt werden können

* **Datenschutzeinstellungen respektieren**

   * Wenn es private Profile gibt, könnte ein Beispiel darin bestehen, das Profilbild, die E-Mail-Adresse oder den vollständigen Namen, der auf der privaten Seite gefunden wird, nicht anzuzeigen. `/profile` Knoten.

## Strenge Zugriffssteuerung {#strict-access-control}

Unabhängig davon, ob Sie Zugriffssteuerung bei der Umstrukturierung von Inhalten oder auf neue Dienstbenutzende anwenden, müssen Sie die strengsten möglichen Zugriffssteuerungsebenen anwenden. Nutzen Sie alle verfügbaren Funktionen für die Zugriffssteuerung:

* Wenden Sie beispielsweise `jcr:read` nicht auf `/apps`, sondern nur auf `/apps/*/components/*/analytics` an.

* Verwenden Sie [Einschränkungen](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

* Anwenden von ACLs für Knotentypen
* Berechtigungen begrenzen

   * Wenn jemand beispielsweise nur Eigenschaften schreiben muss, vergeben Sie nicht die Berechtigung `jcr:write`, sondern die Berechtigung `jcr:modifyProperties`.

## Dienstbenutzende und Zuordnungen {#service-users-and-mappings}

Falls das oben Genannte fehlschlägt, bietet Sling 7 einen Dienst für die Zuordnung von Dienstbenutzenden, der die Konfiguration einer Bundle-zu-Benutzenden-Zuordnung und zweier entsprechender API-Methoden ermöglicht: ` [SlingRepository.loginService()](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)` und ` [ResourceResolverFactory.getServiceResourceResolver()](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)`, die eine Sitzung bzw. einen Resource Resolver mit ausschließlich den Berechtigungen einer konfigurierten Benutzerin oder eines konfigurierten Benutzers zurückgeben. Diese Methoden verfügen über die folgenden Merkmale:

* Sie ermöglichen die Zuordnung von Diensten zu Benutzenden.
* Sie ermöglichen die Definition von Subdienstbenutzern
* Der zentrale Konfigurationspunkt ist: `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`.
* `service-id` = `service-name` [&quot;:&quot; subservice-name]

* `service-id` wird einem Resource Resolver und/oder einer JCR-Repository-Benutzer-ID zur Authentifizierung zugewiesen.
* `service-name` ist der symbolische Name des Bundles, das den Service zur Verfügung stellt.

## Sonstige Recommendations {#other-recommendations}

### Ersetzen der Admin-Sitzung durch einen Service-Benutzer {#replacing-the-admin-session-with-a-service-user}

Ein Dienstbenutzer ist ein JCR-Benutzer ohne festgelegtes Kennwort und mit minimalen Berechtigungen, die für die Ausführung einer bestimmten Aufgabe erforderlich sind. Wenn kein Kennwort festgelegt ist, ist es nicht möglich, sich bei einem Dienstbenutzer anzumelden.

Eine Verwaltungssitzung kann eingestellt werden, indem sie durch Service-Benutzersitzungen ersetzt wird. Sie kann bei Bedarf auch durch mehrere Subdienstbenutzer ersetzt werden.

Um die Admin-Sitzung durch einen Dienstbenutzer zu ersetzen, führen Sie die folgenden Schritte aus:

1. Identifizieren Sie die erforderlichen Berechtigungen für Ihren Dienst unter Berücksichtigung des Prinzips der geringsten Berechtigung.
1. Überprüfen Sie, ob bereits ein Benutzer mit genau den benötigten Berechtigungen verfügbar ist. Erstellen Sie einen Systemdienstbenutzer, wenn kein bestehender Benutzer Ihren Anforderungen entspricht. RTC ist erforderlich, um einen Dienstbenutzer zu erstellen. Manchmal ist es sinnvoll, mehrere Subservice-Benutzer zu erstellen (z. B. eine zum Schreiben und eine zum Lesen), um den Zugriff noch stärker zu gliedern.
1. Richten Sie ACEs ein und testen Sie sie für Ihren Benutzer.
1. Fügen Sie eine `service-user`-Zuordnung für Ihren Dienst und für `user/sub-users` hinzu.

1. Stellen Sie das Dienstbenutzer-Sling-Feature Ihrem Bundle zur Verfügung: Aktualisieren Sie auf die neueste Version von `org.apache.sling.api`.

1. Ersetzen Sie die `admin-session` in Ihrem Code durch den `loginService` oder `getServiceResourceResolver`-APIs.

## Dienstbenutzer erstellen {#creating-a-new-service-user}

Nachdem Sie überprüft haben, ob kein Benutzer in der Liste AEM Dienstbenutzer für Ihren Anwendungsfall geeignet ist und die entsprechenden RTC-Probleme genehmigt wurden, können Sie fortfahren und den neuen Benutzer zum Standardinhalt hinzufügen.

Es wird empfohlen, einen Dienstbenutzer zu erstellen, um den Repository-Explorer unter *https://&lt;Server>:&lt;Port>/crx/explorer/index.jsp* zu verwenden.

Das Ziel besteht darin, eine gültige `jcr:uuid` -Eigenschaft, die erforderlich ist, um den Benutzer über eine Inhaltspaketinstallation zu erstellen.

Dienstbenutzende erstellen Sie wie folgt:

1. Verwenden Sie den Repository-Explorer unter *https://&lt;Server>:&lt;Port>/crx/explorer/index.jsp.*.
1. Melden Sie sich als Administrator an, indem Sie die **Anmelden** in der oberen linken Ecke des Bildschirms.
1. Erstellen und benennen Sie als Nächstes Ihren Systembenutzer. Um den Benutzer als Systembenutzer zu erstellen, legen Sie den Zwischenpfad auf `system` und fügen Sie je nach Bedarf optionale Unterordner hinzu:

   ![chlimage_1-102](assets/chlimage_1-102a.png)

1. Überprüfen Sie, ob Ihr Systembenutzerknoten wie folgt aussieht:

   ![chlimage_1-103](assets/chlimage_1-103a.png)

   >[!NOTE]
   >
   >Dienstbenutzern sind keine Mixin-Typen zugeordnet. Das heißt, dass es für Systembenutzende keine Zugriffssteuerungsrichtlinien gibt.

Vergewissern Sie sich beim Hinzufügen der entsprechenden „.content.xml“ zum Inhalt des Bundles, dass Sie die `rep:authorizableId` festgelegt haben und der primäre Typ `rep:SystemUser` ist. Sie sollte wie folgt aussehen:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:rep="internal"
    jcr:primaryType="rep:SystemUser"
    jcr:uuid="4917dd68-a0c1-3021-b5b7-435d0044b0dd"
    rep:principalName="authentication-service"
    rep:authorizableId="authentication-service"/>
```

## Hinzufügen einer Konfigurationsänderung zur ServiceUserMapper-Konfiguration {#adding-a-configuration-amendment-to-the-serviceusermapper-configuration}

Um eine Zuordnung von Ihrem Dienst zu den entsprechenden Systembenutzern hinzuzufügen, erstellen Sie eine Werkskonfiguration für die ` [ServiceUserMapper](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html)` Dienst. Um diesen modularen Aufbau beizubehalten, kann eine solche Konfiguration mithilfe des [Sling-Änderungsmechanismus](https://issues.apache.org/jira/browse/SLING-3578). Die empfohlene Methode zur Installation solcher Konfigurationen mit Ihrem Bundle ist die Verwendung von [Laden anfänglicher Inhalte von Sling](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html):

1. Erstellen Sie unterhalb des Ordners „src/main/resources“ des Bundles einen Unterordner „SLING-INF/content“.
1. Erstellen Sie in diesem Ordner eine Datei mit dem Namen org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.modified-&lt;some unique=&quot;&quot; name=&quot;&quot; for=&quot;&quot; your=&quot;&quot; factory=&quot;&quot; configuration=&quot;&quot;>.xml mit dem Inhalt Ihrer Factory-Konfiguration (einschließlich aller Subservice-Benutzerzuordnungen). Beispiel:

1. Erstellen Sie unterhalb des Ordners `SLING-INF/content` des Bundles einen Ordner `src/main/resources`.
1. Erstellen Sie in diesem Ordner eine Datei. `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` mit dem Inhalt Ihrer Werkskonfiguration, einschließlich aller Subservice-Benutzerzuordnungen.

   Nehmen Sie zur Veranschaulichung die Datei mit dem Namen `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-com.adobe.granite.auth.saml.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <node>
       <primaryNodeType>sling:OsgiConfig</primaryNodeType>
       <property>
           <name>user.default</name>
           <value></value>
       </property>
       <property>
           <name>user.mapping</name>
           <values>
               <value>com.adobe.granite.auth.saml=authentication-service</value>
           </values>
       </property>
   </node>
   ```

1. Verweisen Sie auf den anfänglichen Sling-Inhalt in der Konfiguration des `maven-bundle-plugin` in der Datei `pom.xml` Ihres Bundles. Beispiel:

   ```xml
   <Sling-Initial-Content>
      SLING-INF/content;path:=/libs/system/config;overwrite:=true;
   </Sling-Initial-Content>
   ```

1. Installieren Sie Ihr Bundle und stellen Sie sicher, dass die Werkskonfiguration installiert ist. Gehen Sie dazu wie folgt vor:

   * Wechseln Sie zur Web-Konsole unter *https://Serverhost:Server-Adresse/system/console/configMgr*.
   * Suchen Sie nach **Apache Sling Service User Mapper Service Amendment**.
   * Klicken Sie auf den Link, um zu sehen, ob die korrekte Konfiguration vorhanden ist.

## Umgang mit freigegebenen Sitzungen in Diensten {#dealing-with-shared-sessions-in-services}

`loginAdministrative()`-Aufrufe treten häufig zusammen mit freigegebenen Sitzungen auf. Diese Sitzungen werden bei Aktivierung des Diensts abgerufen und erst abgemeldet, wenn der Dienst gestoppt wird. Dies ist eine gängige Vorgehensweise führt aber zu zwei Problemen:

* **Sicherheit:** Diese Admin-Sitzungen werden verwendet, um Ressourcen oder andere Objekte, die an die freigegebene Sitzung gebunden sind, zwischenzuspeichern und zurückzugeben. Später im Aufrufstapel können diese Objekte an Sitzungen oder Ressourcenauflöser mit erhöhten Berechtigungen angepasst werden. Oft ist dem Aufrufer nicht klar, ob es sich um eine Admin-Sitzung handelt, mit der er arbeitet.
* **Leistung:** In Oak können freigegebene Sitzungen Leistungsprobleme verursachen, und es wird nicht empfohlen, diese zu verwenden.

Die offensichtlichste Lösung für das Sicherheitsrisiko besteht darin, den Aufruf `loginAdministrative()` durch einen Aufruf `loginService()` an eine Benutzerin oder einen Benutzer mit eingeschränkten Berechtigungen zu ersetzen. Dies hat jedoch keine Auswirkungen auf eine potenzielle Leistungsbeeinträchtigung. Eine Möglichkeit, dies zu umgehen, besteht darin, alle angeforderten Informationen in ein Objekt einzuschließen, das keine Verbindung zur Sitzung hat. Erstellen (oder zerstören) Sie dann die Sitzung nach Bedarf.

Der empfohlene Ansatz besteht darin, die API des Diensts neu zu gestalten, um dem Anrufer die Kontrolle über die Erstellung/Zerstörung der Sitzung zu geben.

## Administrative Sitzungen in JSPs {#administrative-sessions-in-jsps}

JSPs können `loginService()` nicht verwenden, weil kein zugehöriger Dienst vorhanden ist. Allerdings sind Adminsitzungen in JSPs für gewöhnlich ein Zeichen einer Verletzung des MVC-Paradigmas.

Dies kann auf zwei Arten behoben werden:

1. Neustrukturierung des Inhalts auf eine Weise, die die Bearbeitung mit der Benutzersitzung ermöglicht;
1. Extrahieren der Logik zu einem Dienst, der eine API bereitstellt, die dann von der JSP verwendet werden kann.

Die erste Methode wird bevorzugt.

## Verarbeitungsereignisse, Replikations-Präprozessoren und Aufträge {#processing-events-replication-preprocessors-and-jobs}

Bei der Verarbeitung von Ereignissen oder Aufträgen und manchmal Workflows geht die entsprechende Sitzung, die das Ereignis ausgelöst hat, verloren. Dies führt dazu, dass Ereignis-Handler und Auftragsverarbeiter häufig administrative Sitzungen verwenden, um ihre Arbeit zu erledigen. Es gibt verschiedene denkbare Ansätze, um dieses Problem zu lösen, jeweils mit ihren Vor- und Nachteilen:

1. `user-id` an die Ereignis-Payload weitergeben und Personifikation nutzen

   **Vorteile:** Benutzerfreundlich.

   **Nachteile:** Verwendet dennoch `loginAdministrative()`. Eine bereits authentifizierte Anforderung wird erneut authentifiziert.

1. Erstellen oder verwenden Sie einen Dienstbenutzer, der Zugriff auf die Daten hat.

   **Vorteile:** Entspricht aktuellem Design. Erfordert minimale Änderung.

   **Nachteile:** Benötigt leistungsstarke Dienstbenutzer, um flexibel zu sein, was leicht zu Berechtigungseskalationen führen kann. Umgeht das Sicherheitsmodell.

1. Übergeben Sie eine Serialisierung des `Subject` in der Ereignis-Payload und erstellen Sie einen `ResourceResolver` auf Grundlage dieses Betreffs. Ein Beispiel ist die Verwendung des JAAS `doAsPrivileged` in der `ResourceResolverFactory`.

   **Vorteile:** Saubere Implementierung von einem Sicherheitsstandpunkt aus. Es vermeidet die erneute Authentifizierung und funktioniert mit den ursprünglichen Berechtigungen. Der sicherheitsrelevante Code ist für den Verbraucher des Ereignisses transparent.

   **Nachteile:** Muss umstrukturiert werden. Die Tatsache, dass der sicherheitsrelevante Code für den Verbraucher des Ereignisses transparent ist, kann ebenfalls zu Problemen führen.

Der dritte Ansatz ist die bevorzugte Verarbeitungstechnik.

## Workflow-Prozesse {#workflow-processes}

Bei Workflow-Prozessimplementierungen geht die entsprechende Benutzersitzung verloren, die den Workflow ausgelöst hat. Dies führt zu Workflow-Prozessen, die häufig administrative Sitzungen verwenden, um ihre Arbeit auszuführen.

Um diese Probleme zu beheben, wird empfohlen, dieselben Ansätze wie unter [Verarbeitungsereignisse, Replikations-Präprozessoren und Aufträge](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) verwendet werden.

## Sling POST Processors und gelöschte Seiten {#sling-post-processors-and-deleted-pages}

Es gibt einige Verwaltungssitzungen, die in Sling POST Processor-Implementierungen verwendet werden. In der Regel werden Admin-Sitzungen verwendet, um auf Knoten zuzugreifen, die innerhalb der verarbeiteten POST noch gelöscht werden müssen. Daher sind sie nicht mehr über die Anforderungssitzung verfügbar. Es kann auf einen Knoten zugegriffen werden, der gelöscht werden muss, um Metadaten anzuzeigen, auf die andernfalls nicht zugegriffen werden sollte.
