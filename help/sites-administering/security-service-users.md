---
title: Dienstbenutzende in Adobe Experience Manager
description: Erfahren Sie mehr über Dienstbenutzende in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: ccd8577b-3bbf-40ba-9696-474545f07b84
feature: Security
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 86%

---


# Dienstbenutzende in Adobe Experience Manager (AEM) {#service-users-in-aem}

## Übersicht {#overview}

Bisher erhielten Sie eine Admin-Sitzung oder einen Resource Resolver in AEM mithilfe der Sling-Methoden `SlingRepository.loginAdministrative()` und `ResourceResolverFactory.getAdministrativeResourceResolver()`.

Allerdings wurde keine dieser Methoden für die [Grundsatz der geringsten Berechtigung](https://en.wikipedia.org/wiki/Principle_of_least_privilege). Es macht es für Entwickler zu einfach, frühzeitig keine geeignete Struktur und entsprechende Zugriffssteuerungsebenen (Access Control Levels, ACLs) für ihren Inhalt zu planen. Wenn in einem solche Dienst eine Sicherheitslücke vorhanden ist, führt dies oft zu Berechtigungseskalationen an den `admin`, auch wenn der Code selbst keine Administratorrechte benötigt, um zu funktionieren.

## Auslaufen von Admin-Sitzungen {#how-to-phase-out-admin-sessions}

### Priorität 0: Ist die Funktion aktiv/erforderlich/veraltet? {#priority-is-the-feature-active-needed-derelict}

Es kann vorkommen, dass die Adminsitzung nicht verwendet wird oder die Funktion vollständig deaktiviert ist. Wenn dies bei Ihrer Implementierung der Fall ist, stellen Sie sicher, dass Sie die Funktion ganz entfernen oder an sie anpassen. [NOP-Code](https://en.wikipedia.org/wiki/NOP).

### Priorität 1: Verwendung der Anfragesitzung {#priority-use-the-request-session}

Ändern Sie nach Möglichkeit Ihre Funktion so, dass die angegebene authentifizierte Anfragesitzung zum Lesen oder Schreiben von Inhalten verwendet werden kann. Wenn dies nicht möglich ist, kann die Anwendung folgender Prioritäten häufig helfen.

### Priorität 2: Inhalt neu strukturieren {#priority-restructure-content}

Viele Probleme können durch eine Umstrukturierung des Inhalts gelöst werden. Beachten Sie bei der Umstrukturierung folgende einfache Regeln:

* **Zugriffskontrolle ändern**

   * Stellen Sie sicher, dass die Benutzenden oder Gruppen, die wirklich Zugriff benötigen, tatsächlich Zugriff haben.

* **Inhaltsstruktur verfeinern**

   * An andere Stellen verschieben, wo z. B. die Zugriffssteuerung mit den verfügbaren Anfragesitzungen übereinstimmt;
   * Die Inhaltsgranularität ändern;

* **Code zum korrekten Dienst refaktorieren**

   * Verschieben Sie die Geschäftslogik vom JSP-Code in den Dienst. Dies ermöglicht eine unterschiedliche Inhaltsmodellierung.

Stellen Sie außerdem sicher, dass alle neuen Funktionen, die Sie entwickeln, diesen Grundsätzen entsprechen:

* **Sicherheitsanforderungen sollten die Inhaltsstruktur bestimmen**

   * Die Zugriffskontrolle sollte sich selbstverständlich anfühlen
   * Die Zugriffskontrolle muss vom Repository durchgesetzt werden, nicht von der Anwendung

* **Knotentypen verwenden**

   * Beschränken Sie die Menge der Eigenschaften, die festgelegt werden können

* **Datenschutzeinstellungen respektieren**

   * Im Falle privater Profile würden z. B. das Profilbild, die E-Mail-Adresse und der volle Name, die alle auf dem privaten `/profile`-Knoten zu finden sind, nicht angezeigt.

## Strenge Zugriffssteuerung {#strict-access-control}

Unabhängig davon, ob Sie Zugriffssteuerung bei der Umstrukturierung von Inhalten oder auf neue Dienstbenutzende anwenden, müssen Sie die strengsten möglichen Zugriffssteuerungsebenen anwenden. Nutzen Sie alle verfügbaren Funktionen für die Zugriffssteuerung:

* Wenden Sie beispielsweise `jcr:read` nicht auf `/apps`, sondern nur auf `/apps/*/components/*/analytics` an.

* Verwenden Sie [Einschränkungen](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

* Anwenden von ACLs für Knotentypen
* Begrenzen von Berechtigungen

   * Wenn jemand beispielsweise nur Eigenschaften schreiben muss, vergeben Sie nicht die Berechtigung `jcr:write`, sondern die Berechtigung `jcr:modifyProperties`.

## Dienstbenutzende und Zuordnungen {#service-users-and-mappings}

Wenn der oben genannte Fehler auftritt, bietet Sling 7 einen Dienst für die Benutzerzuordnung, mit dem Sie eine Bundle-zu-Benutzer-Zuordnung und zwei entsprechende API-Methoden konfigurieren können:

* [`SlingRepository.loginService()`](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)
* [`ResourceResolverFactory.getServiceResourceResolver()`](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)

Die Methoden geben nur einen Sitzungs-/Ressourcen-Resolver mit den Berechtigungen einer konfigurierten Benutzerin oder eines konfigurierten Benutzers zurück. Diese Methoden verfügen über die folgenden Merkmale:

* Sie ermöglichen die Zuordnung von Diensten zu Benutzenden.
* Sie ermöglichen die Definition von Unterdienstbenutzenden.
* Der zentrale Konfigurationspunkt ist: `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`.
* `service-id` = `service-name` [&quot;:&quot; subservice-name]

* `service-id` wird einem Resource Resolver und/oder einer JCR-Repository-Benutzer-ID zur Authentifizierung zugewiesen.
* `service-name` ist der symbolische Name des Bundles, das den Service zur Verfügung stellt.

## Andere Empfehlungen {#other-recommendations}

### Ersetzen der Admin-Sitzung durch eine Dienstbenutzerin oder einen Dienstbenutzer {#replacing-the-admin-session-with-a-service-user}

Dienstbenutzerinnen oder Dienstbenutzer sind JCR-Benutzerinnen oder JCR-Benutzer ohne festgelegtes Kennwort und mit einem minimalen Satz von Berechtigungen, die zur Durchführung einer bestimmten Aufgabe erforderlich sind. Wenn kein Kennwort festgelegt ist, ist es nicht möglich, sich bei einem Dienstbenutzer anzumelden.

Admin-Sitzungen können verringert werden, indem sie durch Dienstbenutzerinnen- bzw. Dienstbenutzersitzungen ersetzt werden. Sie können bei Bedarf auch durch mehrere Unterdienstbenutzerinnen oder -benutzer ersetzt werden.

Ersetzen Sie eine Admin-Sitzung wie folgt durch eine Dienstbenutzerin oder einen Dienstbenutzer:

1. Identifizieren Sie die erforderlichen Berechtigungen für den Dienst. Berücksichtigen Sie dabei das Prinzip der geringsten Berechtigung.
1. Überprüfen Sie, ob bereits eine Benutzerin oder ein Benutzer mit denselben Berechtigungen, die Sie benötigen, vorhanden ist. Erstellen Sie eine Systemdienstbenutzerin oder einen Systemdienstbenutzer, falls keine vorhandene Benutzerin oder kein vorhandener Benutzer Ihren Anforderungen entspricht. RTC ist erforderlich, um eine Dienstbenutzerin oder einen Dienstbenutzer zu erstellen. Manchmal ist es sinnvoll, mehrere Unterdienstbenutzerinnen oder -benutzer zu erstellen (beispielsweise einen bzw. eine zum Schreiben und einen bzw. eine zum Lesen), um den Zugriff noch weiter aufzuteilen.
1. Richten Sie für Ihre Benutzerin oder Ihren Benutzer ACEs ein und testen Sie sie.
1. Fügen Sie eine `service-user`-Zuordnung für Ihren Dienst und für `user/sub-users` hinzu.

1. Stellen Sie das Dienstbenutzer-Sling-Feature Ihrem Bundle zur Verfügung: Aktualisieren Sie auf die neueste Version von `org.apache.sling.api`.

1. Ersetzen Sie die `admin-session` in Ihrem Code durch den `loginService` oder `getServiceResourceResolver`-APIs.

## Erstellen einer neuen Dienstbenutzerin oder eines neuen Dienstbenutzers {#creating-a-new-service-user}

Nachdem Sie überprüft haben, ob kein Benutzer in der Liste AEM Dienstbenutzer für Ihren Anwendungsfall geeignet ist und die entsprechenden RTC-Probleme genehmigt wurden, fügen Sie den neuen Benutzer zum Standardinhalt hinzu.

Es wird empfohlen, einen Dienstbenutzer zu erstellen, um den Repository-Explorer unter *https://&lt;Server>:&lt;Port>/crx/explorer/index.jsp* zu verwenden.

Das Ziel ist, eine gültige Eigenschaft `jcr:uuid` zu erhalten, die erforderlich ist, um die Benutzerin oder den Benutzer anhand einer Inhaltspaketinstallation zu erstellen.

Dienstbenutzende erstellen Sie wie folgt:

1. Verwenden Sie den Repository-Explorer unter *https://&lt;Server>:&lt;Port>/crx/explorer/index.jsp.*.
1. Melden Sie sich als Admin an, indem Sie oben links auf dem Bildschirm auf **Anmelden** klicken.
1. Als Nächstes erstellen und benennen Sie Ihre Systembenutzerin oder Ihren Systembenutzer. Um den Benutzer oder die Benutzerin als Systembenutzer bzw. Systembenutzerin zu erstellen, legen Sie für den intermediate-Pfad `system` fest und fügen Sie je nach Bedarf optionale Unterordner hinzu:

   ![chlimage_1-102](assets/chlimage_1-102a.png)

1. Überprüfen Sie, ob Ihr Systembenutzerknoten wie folgt aussieht:

   ![chlimage_1-103](assets/chlimage_1-103a.png)

   >[!NOTE]
   >
   >Dienstbenutzerinnen oder -benutzern werden keine Mixin-Typen zugeordnet. Das bedeutet, dass es für Systembenutzer keine Zugriffssteuerungsrichtlinien gibt.

Vergewissern Sie sich beim Hinzufügen der entsprechenden „.content.xml“ zum Inhalt des Bundles, dass Sie die `rep:authorizableId` festgelegt haben und der primäre Typ `rep:SystemUser` ist. Dies sollte wie folgt aussehen:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:rep="internal"
    jcr:primaryType="rep:SystemUser"
    jcr:uuid="4917dd68-a0c1-3021-b5b7-435d0044b0dd"
    rep:principalName="authentication-service"
    rep:authorizableId="authentication-service"/>
```

## Hinzufügen einer Konfigurationsänderung zur ServiceUserMapper-Konfiguration {#adding-a-configuration-amendment-to-the-serviceusermapper-configuration}

Um eine Zuordnung vom Dienst zu den entsprechenden Systembenutzerinnen und -benutzern hinzuzufügen, müssen Sie eine Werkskonfiguration für den Dienst [`ServiceUserMapper`](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html) erstellen. Um die Modularität zu gewährleisten, können derartige Konfigurationen mithilfe des [Sling-Änderungsmechanismus](https://issues.apache.org/jira/browse/SLING-3578) bereitgestellt werden. Zum Installieren solcher Konfigurationen mit Ihrem Paket wird [Sling Initial Content Loading](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html) empfohlen:

1. Erstellen Sie unterhalb des Ordners „src/main/resources“ des Bundles einen Unterordner „SLING-INF/content“.
1. Erstellen Sie in diesem Ordner eine Datei mit der Benennung „org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-&lt;eindeutiger Name für Ihre Werkskonfiguration>.xml“ mit dem Inhalt Ihrer Werkskonfiguration (einschließlich aller Zuordnungen von Unterdienstbenutzerinnen oder Unterdienstbenutzern). Beispiel:

1. Erstellen Sie unterhalb des Ordners `SLING-INF/content` des Bundles einen Ordner `src/main/resources`.
1. Erstellen Sie in diesem Ordner eine Datei. `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` mit dem Inhalt Ihrer Werkskonfiguration, einschließlich aller Subservice-Benutzerzuordnungen.

   Wählen Sie zu Illustrationszwecken die Datei `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-com.adobe.granite.auth.saml.xml` aus:

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

1. Installieren Sie Ihr Paket und stellen Sie sicher, dass die Werkskonfiguration installiert ist. Gehen Sie dazu wie folgt vor:

   * Wechseln Sie zur Web-Konsole unter *https://Serverhost:Server-Adresse/system/console/configMgr*.
   * Suchen Sie nach **Apache Sling Service User Mapper Service Amendment**.
   * Klicken Sie auf den Link, um zu sehen, ob die richtige Konfiguration vorhanden ist.

## Umgang mit freigegebenen Sitzungen in Diensten {#dealing-with-shared-sessions-in-services}

`loginAdministrative()`-Aufrufe treten häufig zusammen mit freigegebenen Sitzungen auf. Diese Sitzungen werden bei Aktivierung des Diensts abgerufen und erst abgemeldet, wenn der Dienst gestoppt wird. Dies ist eine gängige Vorgehensweise führt aber zu zwei Problemen:

* **Sicherheit:** Diese Admin-Sitzungen werden verwendet, um Ressourcen oder andere Objekte, die an die freigegebene Sitzung gebunden sind, zwischenzuspeichern und zurückzugeben. Später im Aufrufstapel können diese Objekte an Sitzungen oder Ressourcenauflöser mit erhöhten Berechtigungen angepasst werden. Oft ist dem Anrufer nicht klar, dass es sich um eine Admin-Sitzung handelt, mit der er arbeitet.
* **Leistung:** In Oak können freigegebene Sitzungen Leistungsprobleme verursachen und sollten deshalb besser nicht verwendet werden.

Die offensichtlichste Lösung für das Sicherheitsrisiko besteht darin, den Aufruf `loginAdministrative()` durch einen Aufruf `loginService()` an eine Benutzerin oder einen Benutzer mit eingeschränkten Berechtigungen zu ersetzen. Dies hat jedoch keine Auswirkungen auf eine potenzielle Leistungsbeeinträchtigung. Eine Möglichkeit, dies zu umgehen, besteht darin, alle angeforderten Informationen in ein Objekt einzuschließen, das nicht mit der Sitzung verknüpft ist. Erstellen (oder zerstören) Sie dann die Sitzung nach Bedarf.

Der empfohlene Ansatz besteht darin, die API des Dienstes so zu ändern, dass der Aufrufer die Kontrolle über die Erstellung/Zerstörung der Sitzung hat.

## Admin-Sitzungen in JSPs {#administrative-sessions-in-jsps}

JSPs können `loginService()` nicht verwenden, weil kein zugehöriger Dienst vorhanden ist. Allerdings sind Adminsitzungen in JSPs für gewöhnlich ein Zeichen einer Verletzung des MVC-Paradigmas.

Dies kann auf zwei Arten behoben werden:

1. Neustrukturierung des Inhalts auf eine Weise, die die Bearbeitung in der Benutzersitzung ermöglicht, oder
1. Extrahieren der Logik zu einem Dienst, der eine API bereitstellt, die dann von der JSP verwendet werden kann.

Die erste Methode wird bevorzugt.

## Verarbeitungsereignisse, Replikations-Vorprozessoren und Aufträge {#processing-events-replication-preprocessors-and-jobs}

Bei der Verarbeitung von Ereignissen, Aufträgen und manchmal Workflows geht die entsprechende Sitzung, die das Ereignis ausgelöst hat, verloren. Dies führt dazu, dass Ereignis-Handler und Auftragsverarbeiter häufig Admin-Sitzungen verwenden, um ihre Arbeit zu erledigen. Es gibt verschiedene Ansätze, um dieses Problem zu lösen,die jedoch ihre eigenen Vor- und Nachteile haben:

1. `user-id` an die Ereignis-Payload weitergeben und Personifikation nutzen

   **Vorteile:** Benutzerfreundlich.

   **Nachteile:** Verwendet dennoch `loginAdministrative()`. Eine bereits authentifizierte Anforderung wird erneut authentifiziert.

1. Erstellen oder verwenden Sie eine Dienstbenutzerin oder einen Dienstbenutzer, die bzw. der Zugriff auf die Daten hat.

   **Vorteile:** Entspricht aktuellem Design. Erfordert minimale Änderung.

   **Nachteile:** Erfordert sehr mächtige Dienstbenutzerinnen und Dienstbenutzer, um flexibel zu sein, was schnell zu Berechtigungseskalationen führen kann. Umgeht das Sicherheitsmodell.

1. Übergeben Sie eine Serialisierung des `Subject` in der Ereignis-Payload und erstellen Sie einen `ResourceResolver` auf Grundlage dieses Betreffs. Ein Beispiel ist die Verwendung des JAAS `doAsPrivileged` in der `ResourceResolverFactory`.

   **Vorteile:** Saubere Implementierung von einem Sicherheitsstandpunkt aus. Eine erneute Authentifizierung wird vermieden und die ursprünglichen Berechtigungen werden genutzt. Der Sicherheits-Code ist für die Person, die das Ereignis nutzt, transparent.

   **Nachteile:** Muss umstrukturiert werden. Die Tatsache, dass der Sicherheits-Code für die Person, die das Ereignis nutzt, transparent ist, kann ebenfalls zu Problemen führen.

Der dritte Ansatz ist die bevorzugte Verarbeitungstechnik.

## Workflow-Prozesse {#workflow-processes}

Bei Workflow-Prozessimplementierungen geht die entsprechende Benutzersitzung verloren, die den Workflow ausgelöst hat. Dies führt zu Workflow-Prozessen, die häufig Admin-Sitzungen verwenden, um ihre Arbeit auszuführen.

Um diese Probleme zu beheben, wird empfohlen, dieselben Ansätze zu verwenden, die unter [Verarbeitungsereignisse, Replikations-Vorprozessoren und Aufträge](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) erwähnt werden.

## Sling-POST-Prozessoren und gelöschte Seiten {#sling-post-processors-and-deleted-pages}

Einige Admin-Sitzungen werden in Sling-POST-Prozessor-Implementierungen verwendet. In der Regel werden Admin-Sitzungen verwendet, um auf Knoten zuzugreifen, die innerhalb der verarbeiteten POST noch gelöscht werden müssen. Daher sind sie nicht mehr über die Anfragesitzung verfügbar. Auf einen Knoten, dessen Löschung aussteht, kann zugegriffen werden, um Metadaten anzuzeigen, auf die andernfalls nicht zugegriffen werden sollte.
