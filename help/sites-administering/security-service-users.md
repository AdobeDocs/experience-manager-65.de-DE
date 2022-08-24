---
title: Dienstbenutzer in AEM
seo-title: Service Users in AEM
description: Hier erfahren Sie mehr über Dienstbenutzer in AEM.
seo-description: Learn about Service Users in AEM.
uuid: 4efab5fb-ba11-4922-bd68-43ccde4eb355
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 9cfe5f11-8a0e-4a27-9681-a8d50835c864
exl-id: ccd8577b-3bbf-40ba-9696-474545f07b84
feature: Security
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '1778'
ht-degree: 76%

---

# Dienstbenutzer in AEM{#service-users-in-aem}

## Übersicht {#overview}

Die Hauptmethode zum Abrufen einer Verwaltungssitzung oder eines Ressourcen-Resolvers in AEM war die Verwendung der `SlingRepository.loginAdministrative()` und `ResourceResolverFactory.getAdministrativeResourceResolver()` -Methoden, die von Sling bereitgestellt werden.

Allerdings waren diese beiden Methoden um das sogenannte [Principle of Least Privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege) (Prinzip der geringsten Berechtigung) aufgebaut und sie machen es Entwicklern zu einfach, anfangs eine angemessene Struktur und entsprechende Zugriffssteuerungsebenen für die Inhalte zu ignorieren. Wenn in einem solchen Dienst eine Sicherheitslücke vorhanden ist, führt dies oft zu Berechtigungseskalationen für die `admin` Benutzer, auch wenn der Code selbst keine Administratorrechte benötigt, um zu funktionieren.

## So werden Adminsitzungen abgebaut {#how-to-phase-out-admin-sessions}

### Priorität 0: Ist die Funktion aktiv/erforderlich/veraltet? {#priority-is-the-feature-active-needed-derelict}

Es kann vorkommen, dass die Adminsitzung nicht verwendet wird oder die Funktion vollständig deaktiviert ist. Ist dies mit Ihrer Implementierung der Fall, entfernen Sie die Funktion vollständig oder bauen Sie [Nulloperationscode](https://en.wikipedia.org/wiki/NOP) darin ein.

### Priorität 1: Die Anfragesitzung nutzen {#priority-use-the-request-session}

Refaktorieren Sie das Feature wann immer möglich, damit die gegebene, authentifizierte Anfragesitzung für das Lesen und Schreiben von Inhalten verwendet werden kann. Wenn dies nicht machbar ist, erreichen Sie dieses Ziel, indem Sie die Prioritäten anwenden, die nach den folgenden aufgeführt werden.

### Priorität 2: Inhalte umstrukturieren {#priority-restructure-content}

Viele Probleme lassen sich durch die Umstrukturierung des Inhalts lösen. Berücksichtigen Sie bei der Umstrukturierung die folgenden einfachen Regeln:

* **Zugriffssteuerung ändern**

   * Stellen Sie sicher, dass die Benutzer oder Gruppen, die tatsächlich Zugriff benötigen, auch Zugriff haben.

* **Inhaltsstruktur verfeinern**

   * Verschieben Sie sie an andere Orte, beispielsweise an einen Ort, wo die Zugriffssteuerung den verfügbaren Anfragesitzungen entspricht.
   * Ändern Sie die Granularität der Inhalte.

* **Code zum korrekten Dienst refaktorieren**

   * Verschieben Sie die Geschäftslogik vom JSP-Code in den Dienst. Dies ermöglicht eine unterschiedliche Inhaltsmodellierung.

Achten Sie außerdem darauf, dass alle neu entwickelten Funktionen diesen Richtlinien entsprechen:

* **Sicherheitsanforderungen müssen Inhaltsstruktur unterstützen**

   * Die Verwaltung der Zugriffssteuerung muss sich natürlich anfühlen.
   * Zugriffssteuerung muss vom Repository durchgesetzt werden, nicht von der Anwendung.

* **Knotentypen nutzen**

   * Schränken Sie den Satz festlegbarer Eigenschaften ein.

* **Datenschutzeinstellungen respektieren**

   * Bei privaten Profilen wäre es beispielsweise nicht möglich, das Profilbild, die E-Mail-Adresse oder den vollständigen Namen auf der privaten Seite anzuzeigen. `/profile` Knoten.

## Strenge Zugriffssteuerung {#strict-access-control}

Unabhängig davon, ob Sie die Zugriffskontrolle bei der Neustrukturierung von Inhalten anwenden oder ob Sie dies für einen neuen Dienstbenutzer tun, müssen Sie die strengsten ACLs anwenden, die möglich sind. Verwenden Sie alle verfügbaren Funktionen für die Zugriffssteuerung:

* Anstatt beispielsweise `jcr:read` on `/apps`, nur anwenden auf `/apps/*/components/*/analytics`

* Verwenden Sie [Einschränkungen](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html).

* Wenden Sie Zugriffssteuerungsebenen für alle Knotentypen an.
* Schränken Sie Berechtigungen ein.

   * Wenn Sie beispielsweise nur Eigenschaften schreiben müssen, geben Sie nicht `jcr:write` Erlaubnis, use `jcr:modifyProperties` anstelle

## Dienstbenutzer und Zuordnungen {#service-users-and-mappings}

Wenn der oben genannte Fehler auftritt, bietet Sling 7 einen Dienst für die Benutzerzuordnung, der die Konfiguration einer Bundle-zu-Benutzer-Zuordnung und zweier entsprechender API-Methoden ermöglicht: ` [SlingRepository.loginService()](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)` und ` [ResourceResolverFactory.getServiceResourceResolver()](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)` , die einen Sitzungs-/Ressourcen-Resolver nur mit den Berechtigungen eines konfigurierten Benutzers zurückgeben. Diese Methoden verfügen über die folgenden Merkmale:

* Sie ermöglichen die Zuordnung von Diensten zu Benutzern.
* Sie ermöglichen die Definition von Unterdienstbenutzern.
* Der zentrale Konfigurationspunkt ist: `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`.
* `service-id` = `service-name` [ &quot;:&quot; subservice-name ] 

* `service-id` wird einem Resource Resolver und/oder einer JCR-Repository-Benutzer-ID zur Authentifizierung zugewiesen.
* `service-name` ist der symbolische Name des Bundles, das den Service zur Verfügung stellt.

## Andere Empfehlungen {#other-recommendations}

### Ersetzen der Adminsitzung durch einen Dienstbenutzer {#replacing-the-admin-session-with-a-service-user}

Dienstbenutzer sind JCR-Benutzer ohne festgelegtes Kennwort und mit einem minimalen Satz von Berechtigungen, die zur Durchführung einer bestimmten Aufgabe erforderlich sind. Da kein Kennwort festgelegt ist, kann man sich nicht als Dienstbenutzer anmelden.

Adminsitzungen können verringert werden, indem sie durch Dienstbenutzersitzungen ersetzt werden. Sie können bei Bedarf auch durch mehrere Unterdienstbenutzer ersetzt werden.

Ersetzen Sie eine Adminsitzung wie folgt durch einen Dienstbenutzer:

1. Identifizieren Sie die erforderlichen Berechtigungen für den Dienst. Berücksichtigen Sie dabei das Prinzip der geringsten Berechtigung.
1. Überprüfen Sie, ob bereits ein Benutzer mit denselben Berechtigungen, die Sie benötigen, vorhanden ist. Erstellen Sie einen neuen Systemdienstbenutzer, falls kein vorhandener Benutzer Ihren Anforderungen entspricht. RTC ist erforderlich, um einen neuen Dienstbenutzer zu erstellen. Manchmal ist es sinnvoll, mehrere Unterdienstbenutzer zu erstellen (beispielsweise einen zum Schreiben und einen zum Lesen), um den Zugriff noch weiter aufzuteilen.
1. Richten Sie für Ihren Benutzer ACEs ein und testen Sie sie.
1. Hinzufügen einer `service-user` Zuordnung für Ihren Dienst und für `user/sub-users`

1. Stellen Sie das Dienstbenutzer-Sling-Feature Ihrem Bundle zur Verfügung: Aktualisieren Sie auf die neueste Version von `org.apache.sling.api`.

1. Ersetzen Sie die `admin-session` in Ihrem Code mit dem `loginService` oder `getServiceResourceResolver` APIs.

## Erstellen eines neuen Dienstbenutzers {#creating-a-new-service-user}

Nachdem Sie überprüft haben, dass kein Benutzer in der Liste der AEM-Dienstbenutzer Ihrem Anwendungsfall entspricht und die jeweiligen RTC-Ausgaben genehmigt wurden, können Sie den neuen Benutzer zum Standardinhalt hinzufügen.

Es wird empfohlen, einen Dienstbenutzer zu erstellen, um den Repository-Explorer unter *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*

Das Ziel ist, eine gültige Eigenschaft `jcr:uuid` zu erhalten, die erforderlich ist, um den Benutzer anhand einer Inhaltspaketinstallation zu erstellen.

Dienstbenutzer erstellen Sie wie folgt:

1. Wechseln Sie zum Repository-Explorer unter *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*
1. Melden Sie sich als Administrator an, indem Sie oben links auf dem Bildschirm auf **Anmelden** klicken.
1. Als Nächstes erstellen und benennen Sie Ihren Systembenutzer. Um den Benutzer als Systembenutzer zu erstellen, legen Sie für den intermediate-Pfad `system` fest und fügen Sie je nach Bedarf optionale Unterordner hinzu:

   ![chlimage_1-102](assets/chlimage_1-102a.png)

1. Überprüfen Sie, ob Ihr Systembenutzerknoten wie folgt aussieht:

   ![chlimage_1-103](assets/chlimage_1-103a.png)

   >[!NOTE]
   >
   >Dienstbenutzern werden keine Mixin-Typen zugeordnet. Das heißt, dass es für Systembenutzer keine Zugriffssteuerungsrichtlinien gibt.

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

Um eine Zuordnung vom Dienst zu den entsprechenden Systembenutzern hinzuzufügen, müssen Sie eine Werkskonfiguration für den Dienst ` [ServiceUserMapper](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html)` erstellen. Um die Modularität zu gewährleisten, können derartige Konfigurationen mithilfe des [Sling-Änderungsmechanismus](https://issues.apache.org/jira/browse/SLING-3578) bereitgestellt werden. Zum Installieren solcher Konfigurationen mit Ihrem Bundle wird [Sling Initial Content Loading](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html) empfohlen:

1. Erstellen Sie einen Unterordner SLING-INF/content unterhalb des Ordners src/main/resources Ihres Bundles
1. Erstellen Sie in diesem Ordner eine Datei mit dem Namen org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.modified-&lt;some unique=&quot;&quot; name=&quot;&quot; for=&quot;&quot; your=&quot;&quot; factory=&quot;&quot; configuration=&quot;&quot;>.xml mit dem Inhalt Ihrer Werkskonfiguration (einschließlich aller Unter-Service-Benutzerzuordnungen). Beispiel:

1. Erstellen Sie eine `SLING-INF/content` Ordner unterhalb der `src/main/resources` Ordner Ihres Bundles;
1. Erstellen Sie in diesem Ordner eine Datei. `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` mit dem Inhalt Ihrer Werkskonfiguration, einschließlich aller Unter-Service-Benutzerzuordnungen.

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

1. Referenzieren Sie den anfänglichen Sling-Inhalt in der Konfiguration der `maven-bundle-plugin` im `pom.xml` Ihres Bundles. Beispiel:

   ```xml
   <Sling-Initial-Content>
      SLING-INF/content;path:=/libs/system/config;overwrite:=true;
   </Sling-Initial-Content>
   ```

1. Installieren Sie das Bundle und prüfen Sie, ob die Werkskonfiguration installiert wurde. Gehen Sie dazu wie folgt vor:

   * Wechseln Sie zur Web-Konsole unter *https://serverhost:serveraddress/system/console/configMgr*
   * Suchen Sie nach **Apache Sling Service User Mapper Service Amendment**.
   * Klicken Sie auf den Link, um zu sehen, ob die korrekte Konfiguration vorhanden ist.

## Umgang mit freigegebenen Sitzungen in Diensten {#dealing-with-shared-sessions-in-services}

Aufrufe an `loginAdministrative()` häufig zusammen mit freigegebenen Sitzungen angezeigt werden. Diese Sitzungen werden bei Aktivierung des Diensts abgerufen und erst abgemeldet, wenn der Dienst gestoppt wird. Dies ist zwar gängige Praxis, führt aber zu zwei Problemen:

* **Sicherheit:** Derartige Adminsitzungen werden verwendet, um Ressourcen oder andere Objekte, die an die freigegebene Sitzung gebunden sind, zwischenzuspeichern und zurückzugeben. Später im Aufrufstapel könnten diese Objekte für Sitzungen oder Resource Resolvers mit erhöhten Berechtigungen angepasst werden. Oft ist der aufrufenden Person nicht klar, dass sie mit einer Adminsitzung arbeitet.
* **Leistung:** In Oak können freigegebene Sitzungen Leistungsprobleme verursachen, daher wird derzeit davon abgeraten, sie zu nutzen.

Die offensichtlichste Lösung für das Sicherheitsrisiko besteht darin, einfach die `loginAdministrative()` Aufruf mit `loginService()` einen Benutzer mit eingeschränkten Berechtigungen. Dies hat jedoch keine Auswirkungen auf potenzielle Leistungsbeeinträchtigungen. Eine Chance, dies zu verringern, besteht darin, alle erforderlichen Informationen in einem Objekt zu verpacken, das keine Verbindung zur Sitzung aufweist. Erstellen (oder zerstören) Sie die Sitzung dann bei Bedarf.

Die empfohlene Vorgehensweise besteht darin, die API des Dienstes zu refaktorieren, um der aufrufenden Person die Kontrolle über die Erstellung bzw. Zerstörung der Sitzung zu gewähren.

## Adminsitzungen in JSPs {#administrative-sessions-in-jsps}

JSPs können nicht verwenden `loginService()`, da es keinen zugehörigen Dienst gibt. Adminsitzungen in JSPs sind jedoch normalerweise ein Zeichen für einen Verstoß gegen das MVC-Paradigma.

Dies kann auf zwei Arten behoben werden:

1. Umstrukturieren des Inhalts auf eine Art, welche ermöglicht, dass er anhand der Benutzersitzung geändert wird
1. Extrahieren der Logik für einen Dienst, der eine API enthält, die durch das JSP verwendet werden kann

Die erste Methode wird bevorzugt.

## Verarbeiten von Ereignissen, Replikationsvorprozessen und Aufträgen {#processing-events-replication-preprocessors-and-jobs}

Bei der Verarbeitung von Ereignissen oder Aufträgen und in manchen Fällen Workflows geht die Sitzung, die das Ereignis ausgelöst hat, irgendwann verloren. Dies führt dazu, dass Ereignis-Handler und Auftragsprozesse oft Adminsitzungen zur Verrichtung ihrer Arbeit nutzen. Zu diesem Problem gibt es verschiedene denkbare Lösungsansätze, die alle jeweils verschiedene Vorteile und Nachteile aufweisen:

1. `user-id` an die Ereignisnutzlast weitergeben und Personifikation nutzen

   **Vorteile:** Benutzerfreundlich.

   **Nachteile:** Standuse `loginAdministrative()`. Authentifiziert eine Anfrage erneut, die bereits authentifiziert wurde.

1. Erstellen oder erneutes Verwenden eines Dienstbenutzers, der Zugriff auf die Daten hat

   **Vorteile:** Entspricht aktuellem Design. Erfordert minimale Änderung.

   **Nachteile:** Benötigt sehr leistungsstarke Dienstbenutzer, um flexibel zu sein, was leicht zu Berechtigungseskalationen führen kann. Umgeht das Sicherheitsmodell.

1. Übergeben einer Serialisierung des `Subject` in der Ereignis-Payload und erstellen Sie eine `ResourceResolver` auf der Grundlage dieses Themas. Ein Beispiel ist die Verwendung des JAAS `doAsPrivileged` in der `ResourceResolverFactory`.

   **Vorteile:** Saubere Implementierung von einem Sicherheitsstandpunkt aus. Diese Methode vermeidet die erneute Authentifizierung und nutzt die ursprünglichen Berechtigungen. Sicherheitsrelevanter Code ist für den Verbraucher des Ereignisses nicht sichtbar.

   **Nachteile:** Muss umstrukturiert werden. Die Tatsache, dass sicherheitsrelevanter Code für den Verbraucher nicht sichtbar ist, kann auch zu Problemen führen.

Der dritte Ansatz ist derzeit die bevorzugte Verarbeitungsweise.

## Workflow-Prozesse {#workflow-processes}

Innerhalb von Workflow-Prozessimplementierungen geht die entsprechende Benutzersitzung, die den Workflow ausgelöst hat, für gewöhnlich verloren. Dies führt dazu, dass Workflowprozesse oft Adminsitzungen zur Verrichtung ihrer Arbeit nutzen.

Zur Behebung dieser Probleme sollten ebenfalls die Ansätze im Abschnitt [Verarbeiten von Ereignissen, Replikationsvorprozessen und Aufträgen](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) verwendet werden.

## Sling-POST-Prozesse und gelöschte Seiten {#sling-post-processors-and-deleted-pages}

In Sling-POST-Prozessimplementierungen werden mehrere Adminsitzungen verwendet. In der Regel werden Adminsitzungen verwendet, um auf Knoten zuzugreifen, die im verarbeiteten POST zur Löschung markiert sind. Daher sind sie nicht mehr über die Anfragesitzung verfügbar. Auf zur Löschung markierte Knoten kann zugegriffen werden, um Metadaten anzuzeigen, die ansonsten nicht sichtbar sein sollten.
