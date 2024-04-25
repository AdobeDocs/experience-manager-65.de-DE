---
title: Veraltete und entfernte Funktionen in Adobe Experience Manager Version 6.5.
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.5.
exl-id: d9b6140a-c37d-4b90-a60c-01f471d65621
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 100%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

<!-- Search&Promote is end-of-life September 1, 2022 | Assets | If a user does not have sufficient (read and write) permissions on `/content/dam/collections`, the user cannot create a Collection. | Honor the access control setup of user and ensure appropriate permissions. ||
|Adobe Search & Promote|The integration with Adobe Search & Promote is deprecated. Adobe does not plan to make further enhancements to the Search & Promote integration. Adobe Search & Promote integration remains fully supported while being deprecated.||| -->

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Bekanntgabe der bevorstehenden Entfernung oder Ersetzung von Adobe Experience Manager (AEM)-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktionen veraltet sind, sind sie weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das geplante Datum für die Entfernung wird später bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die in AEM 6.5 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
|---|---|---|---|
|   |   |   |   |
| Sites | Der Dienst **Adobe AEM Managed Polling Configuration**: `com.day.cq.polling.importer.impl.ManagedPollConfigImpl` | Der Dienst **Adobe AEM Analytics Report-Sling-Importer**. Siehe „Herstellen einer Verbindung zu Adobe Analytics und Erstellen von Frameworks“ – [Konfigurieren des Importintervalls](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval) | 6.5.19.0 |
| Screens | ActiveMQ in Adobe Experience Manager (AEM). ActiveMQ wurde für die Kommunikation zwischen zwei AEM-Publishing-Instanzen verwendet. | Adobe empfiehlt, dass Kundinnen und Kunden jetzt einen Lastenausgleich verwenden. | 6.5.18.0 |
| Experience Fragments-Eigenschaften für **Social-Media-Status**. |   | 6.5.11.0 |
| [!DNL Sites] | Inhaltsfragmentvorlagen zum Erstellen einfacher Inhaltsfragmente. | Jetzt [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md). | 6.5.11.0 |
| Creative Cloud-Integration | Die Ordnerfreigabe von AEM zu Creative Cloud wurde in AEM 6.2 eingeführt. Sie bietet eine Möglichkeit, kreativen Benutzerinnen und Benutzern Zugriff auf Elemente aus AEM zu geben, damit sie diese in [!DNL Creative Cloud]-Anwendungen öffnen und neue Dateien hochladen oder Änderungen in AEM speichern können.  Eine neue Funktion im Creative Cloud-Client, Adobe Asset Link, bietet ein besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf AEM-Assets direkt aus Photoshop, InDesign und Illustrator heraus.  Adobe plant keine weiteren Verbesserungen an der Integration der Ordnerfreigabe aus AEM in Creative Cloud. Obwohl die Funktion in AEM enthalten ist, wird Kundinnen und Kunden der Einsatz von Ersatzlösungen empfohlen. | Kunden sollten auf neue Creative Cloud-Integrationsfunktionen wie Adobe Asset Link oder AEM Desktop-App umsteigen. |  |
| Assets | `AssetDownloadServlet` ist bei den Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md). | Konfiguration, wie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md) beschrieben. |  |
| Integrationen | Der Bildschirm **[!UICONTROL Experience Manager Cloud Services Opt-in]** ist veraltet, da die Integration mit [!DNL Experience Manager] und [!DNL Adobe Target] in [!DNL Experience Manager] 6.5 aktualisiert wird. Die Integration unterstützt die Adobe Target Standard-API. Die API verwendet die Authentifizierung über Adobe IMS und [!DNL Adobe I/O Runtime]. Sie unterstützt die wachsende Rolle von Adobe Launch, um [!DNL Experience Manager]-Seiten für Analysen und Personalisierung zu instrumentieren, der Assistent für die Anmeldung ist funktionell irrelevant. | Konfigurieren Sie Systemverbindungen, Adobe IMS-Authentifizierung und [!DNL Adobe I/O Runtime]-Integrationen über die jeweiligen [!DNL Experience Manager]-Cloud-Services. | 6.5.7.0 |
| Connectoren | Der Adobe JCR-Connector für Microsoft® SharePoint 2010 und Microsoft® SharePoint 2013 wird für [!DNL Experience Manager] 6.5 nicht mehr unterstützt. | Nicht zutreffend |  |
| Dynamic Tag Manager (DTM) | Die Integration mit DTM wird nicht mehr unterstützt. | Steigen Sie auf Adobe Experience Platform Launch als Tag-Manager um. |   |
| Adobe Target | Durch das Hinzufügen der Möglichkeit in AEM 6.5, dass AEM über die [!DNL Adobe I/O]-basierte Adobe Target Standard-API (REST-API) eine Verbindung zum Adobe Target-Service herstellt, ist die Methode unter Verwendung der Target Classic-API (AML) veraltet. | Konfigurieren Sie die Integration so, dass [die neue API verwendet werden kann](/help/sites-administering/target.md). |  |
| Adobe Target | Die Verwendung der `mbox.js`-basierten Integration mit Adobe Target ist in AEM als veraltet gekennzeichnet. | Stellen Sie auf `at.js` 1.x um. |  |
| Commerce | [CIF REST](https://github.com/adobe/commerce-cif-api) wurde 2018 als Microservice bereitgestellt, um Integrationen zwischen AEM- und Commerce-Engines zu ermöglichen. Nachdem Adobe Mitte 2018 Adobe Commerce (ehemals Magento) übernommen hatte, entschied sich Adobe aus zwei Gründen für einen anderen Ansatz.  Commerce verfügt über einen eigenen Satz von Commerce-APIs (REST und GraphQL), und es wäre keine gute Idee, zwei Sätze von APIs zu pflegen. Die Markt-Trends zeigten, dass Kundinnen und Kunden zu GraphQL übergegangen sind, da dies eine effizientere Methode zur Datenabfrage ist. Im Jahr 2019 hat Adobe das neue Commerce Integration Framework veröffentlicht, das die GraphQL-APIs von Commerce als verbindliche Datenquelle nutzt.  Adobe plant keine weiteren Investitionen in CIF REST. Kundinnen und Kunden wird dringend empfohlen, die Ersatzlösung zu verwenden. | Für AEM-Commerce-Integrationen wechseln Sie zu [AEM CIF-Archetyp](https://github.com/adobe/aem-cif-project-archetype) und [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components).  Siehe Integration von AEM und Adobe Commerce [mithilfe des Commerce Integration Framework](/help/commerce/cif/integrating/magento.md). Die Unterstützung für die Integration von Drittanbietern (außer Commerce) mit dem neuen Ansatz ist Teil der Roadmap von Adobe. |  |
| Komponenten (AEM Sites) | Adobe plant keine weiteren Verbesserungen an den meisten Foundation-Komponenten, die in `/libs/foundation/components` gespeichert sind. Suchen Sie im Komponentenordner nach den Eigenschaften `cq:deprecated` und `cq:deprecatedReason`. Die Foundation-Komponenten sind in AEM 6.5 enthalten und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Darüber hinaus werden die Foundation-Komponenten unterstützt, auch wenn sie veraltet sind. | Adobe empfiehlt die Verwendung der Kernkomponenten für zukünftige Projekte. Vorhandene Websites können unverändert bleiben oder Sie gestalten die Website mit der [AEM-Modernisierungs-Tool-Suite](https://github.com/adobe/aem-modernize-tools) so um, dass Kernkomponenten verwendet werden. |  |
| Komponenten (AEM Sites) | Design-Import-Tool-Komponenten (`/libs/wcm/designimporter/components`) sind seit 6.5 als veraltet gekennzeichnet. Adobe plant keine weiteren Verbesserungen an dieser Implementierung des Design-Import-Tools. | Adobe plant für künftige Versionen eine alternative Implementierung des Nutzungsszenarios. |  |
| Foundation | Granite-Auslagerungs-Framework. Adobe plant keine weiteren Verbesserungen am Auslagerungs-Framework, das in Version CQ 5.6.1 zur Externalisierung der Asset-Verarbeitung eingeführt wurde. | Adobe arbeitet an einem cloudnativen Auslagerungs-Framework der nächsten Generation. |  |
| Entwickler | `Hobbes.js`. Adobe plant keine weiteren Verbesserungen am `hobbes.js`-Framework zum Testen von Benutzeroberflächen. | Adobe empfiehlt, dass Kunden die Selenium-Automatisierung verwenden. |  |
| Entwickler | jQuery UI-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der jQuery UI-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die nach wie vor die jQuery-Benutzeroberfläche für ihren Code benötigen, diese Erweiterung zu ihrer Projekt-Code-Basis hinzuzufügen. |  |
| Entwickler | jQuery Animation-Client-Bibliothek (`granite.jquery.animation`). Adobe plant keine weitere Pflege und Aktualisierung der jQuery Animation-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die nach wie vor jQuery-Animationen für ihren Code benötigen, diese Erweiterung zu ihrer Projekt-Code-Basis hinzuzufügen. |  |
| Entwickler | Handlebars-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Handlebar-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kundinnen und Kunden, die nach wie vor `Handlebars` für ihren Code benötigen, diese in ihre Projekt-Code-Basis aufzunehmen. |  |
| Entwickler | Lawnchair-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Lawnchair-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die nach wie vor Lawnchair für ihren Code benötigen, diese Erweiterung zu ihrer Projekt-Code-Basis hinzuzufügen. |  |
| Entwickler | `Granite.Sling.js`-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Granite.Sling.js-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die sich auf die Fähigkeiten der Bibliothek verlassen, ihren Code zu überarbeiten, diese nicht mehr zu verwenden. |  |
| Entwickler | Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken: Adobe plant keine weitere Aktualisierung der YUI-Bibliothek. Bis AEM 6.4 wurde YUI standardmäßig verwendet, um JavaScript zu minimieren – mit optionalem Wechsel zu Google Closure Compiler (GCC). Ab AEM 6.5 ist GCC der Standard. | Adobe empfiehlt Kunden, die ein Upgrade auf AEM 6.5 durchführen, für ihre Implementierungen auf GCC umzustellen. |  |
| Entwicklerinnen und Entwickler | Klassischer UI-Dialog-Editor in CRXDE Lite.  Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird | Es steht kein Ersatz zur Verfügung. |  |
| Formulare | Die Integration von AEM Forms mit AEM Mobile ist veraltet. | Es ist kein Ersatz verfügbar. |
| Entwicklerinnen und Entwickler | Klassischer UI-Dialog-Editor in CRXDE Lite.  Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird | Es steht kein Ersatz zur Verfügung. |  |
| Entwickler | Lodash/Underscore-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Lodash/underscore-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die nach wie vor Lodash/Underscore für ihren Code benötigen, diese Erweiterung zu ihrer Projekt-Code-Basis hinzuzufügen. |  |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die aus AEM 6.5 entfernt wurden und in früheren Versionen als veraltet gekennzeichnet waren.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |
| Integration mit [!DNL Experience Cloud] | Sie können Ihre Assets mit [!DNL Experience Cloud] synchronisieren, mithilfe einer Konfiguration über [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] hieß zuvor [!DNL Adobe Experience Cloud]. | Bei Fragen [wenden Sie sich an den Kunden-Support von Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support). |  |
| Analytics Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Verwenden Sie das [von Adobe Analytics bereitgestellte Activity Map-Plug-in](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de). |  |
| Integrationen | Die ExactTarget-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist nicht mehr verfügbar. | Kein Ersatz. |  |
| Integrationen | Die Salesforce Force-API-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist jetzt ein zusätzliches, über [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) zu installierendes Paket. | Die Funktion ist immer noch verfügbar. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Dienst wurde entfernt, da Adobe Central nicht mehr unterstützt wird. | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Kein Ersatz vorhanden |  |
| Formulare | Ein einmaliges Upgrade von LiveCycle ES4 SP1 auf AEM 6.5 Forms on JEE ist nicht verfügbar. | In der Dokumentation zu AEM Forms-Upgrades finden Sie die [verfügbaren Upgrade-Pfade](../forms/using/upgrade.md). |  |
| Formulare | Unterstützung für UPD-basiertes Clustering wurde von AEM Forms on JEE entfernt | Sie können nur TCP-basiertes Clustering in AEM Forms on JEE verwenden. Wenn Sie für einen UDP-Multicast-Server ein Upgrade von einer früheren Version auf AEM 5.5 Forms auf JEE durchführen, führen Sie manuelle Konfigurationen durch, um zum TCP-basierten Gemfire-Clustering zu wechseln. Detaillierte Anweisungen finden Sie unter [Upgrade auf AEM 6.5 Forms on JEE](../forms/using/upgrade-forms-jee.md) |  |
| Entwickler | Firebug Lite wurde aus der Standardverteilung (Quickstart) entfernt | Verwenden der integrierten Entwicklerkonsolen des Browsers |
| Entwickler | Die Unterstützung für `customJavaScriptPath` wurde im HTML Client Library Manager eingestellt. | Kein Ersatz vorhanden |  |
| [!DNL Assets] | Die Asset-Auslagerungsfunktion wurde in [!DNL Adobe Experience Manager] 6.5 entfernt. | Es steht kein Ersatz zur Verfügung. |  |
| Cache | `system/console/slingjsp` wurde entfernt und ist in AEM 6.5 nicht mehr verfügbar. | Klassen und Slightly-Cache werden im Apache Sling Commons FileSystem ClassLoader-Bundle gespeichert. Sie können die Bundle-Nummer in der AEM-Web-Konsole überprüfen und den Cache-Ordner direkt aus dem Dateisystem entfernen (`crx-quickstart/launchpad/felix/bundle<ID>`). |  |
| Screens | Unterstützung für das activemq-Bundle und die zugehörigen Konfigurationen wurde entfernt. |  |  |

<!-- ## Pre-announcement for next release {#pre-announcement-for-next-release}

This section is used to pre-announce the upcoming changes in the future releases. The announced changes are not yet effective but will impact customers. For example, the features are not yet deprecated but impacts the users after deprecation. These updates are provided for planning purpose.

|Area|Feature|Announcement|
|--- |--- |--- |
|Foundation|UI Framework|Adobe is planning to deprecate the Coral UI 2 components in 2019. Coral UI 3 was introduced with AEM 6.2, and AEM 6.5 is fully based on Coral 3. Adobe recommends customers and partners that have build custom UIs with Coral 2 to refactored them to Coral 3. Adobe is providing a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/modernization-tools.md).|
-->
