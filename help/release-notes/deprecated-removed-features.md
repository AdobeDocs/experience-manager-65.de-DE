---
title: Veraltete und entfernte Funktionen in Adobe Experience Manager Version 6.5.
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.5.
exl-id: d9b6140a-c37d-4b90-a60c-01f471d65621
source-git-commit: 11e848d93964b5f8e45ccd7388a48953a3148e35
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 90%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Bekanntgabe des bevorstehenden Entfernens oder Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktionen veraltet sind, sind sie weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Das Entfernen veralteter Funktionen erfolgt frühestens mit Einführung der nächsten Hauptversion. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die in AEM 6.5 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
|---|---|---|---|
| [!DNL Sites] | Experience Fragments-Eigenschaften für **Social-Media-Status**. |   | 6.5.11.0 |
| [!DNL Sites] | Inhaltsfragmentvorlagen zum Erstellen einfacher Inhaltsfragmente. | Jetzt [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md). | 6.5.11.0 |
| Creative Cloud-Integration | Die Ordnerfreigabe aus AEM in Creative Cloud wurde mit AEM 6.2 eingeführt. Kreative Anwender können hierdurch auf AEM-Assets zugreifen und diese in [!DNL Creative Cloud]-Anwendungen öffnen sowie neue Dateien in AEM hochladen oder dort Änderungen speichern. Eine neue Funktion des Creative Cloud-Programms, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus. Adobe plant keine weiteren Verbesserungen an der Integration der Ordnerfreigabe aus AEM in Creative Cloud. Obwohl die Funktion in AEM enthalten ist, wird Kundinnen und Kunden der Einsatz von Ersatzlösungen empfohlen. | Kunden sollten auf neue Creative Cloud-Integrationsfunktionen wie Adobe Asset Link oder AEM Desktop-App umsteigen. |  |
| Assets | `AssetDownloadServlet` ist bei den Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md). | Konfiguration, wie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md) beschrieben. |  |
<!-- Search&Promote is end-of-life September 1, 2022 | Assets | If a user does not have sufficient (read and write) permissions on `/content/dam/collections`, the user cannot create a Collection. | Honor the access control setup of user and ensure appropriate permissions. ||
|Adobe Search & Promote|The integration with Adobe Search & Promote is deprecated. Adobe does not plan to make further enhancements to the Search & Promote integration. Adobe Search & Promote integration remains fully supported while being deprecated.||| -->
| DTM Tag Manager | Die Integration mit DTM (dynamischer Tag-Manager) wird nicht mehr unterstützt. | Steigen Sie auf Adobe Experience Platform Launch als Tag-Manager um. ||
|Adobe Target|Durch das Hinzufügen der Möglichkeit für AEM, sich mit dem Adobe Target-Dienst mithilfe der [!DNL Adobe I/O]-basierten Adobe Target Standard-API (Rest-API) in AEM 6.5 zu verbinden, ist der Weg über die klassische Target-API (XML) veraltet.|Konfigurieren Sie die Integration neu, um [die neue API zu verwenden](/help/sites-administering/target.md). ||
|Adobe Target|Die Verwendung der `mbox.js`-basierten Integration mit Adobe Target in AEM ist veraltet.|Wechseln Sie zur Verwendung von `at.js` 1.x.||
| Commerce | [CIF REST](https://github.com/adobe/commerce-cif-api) wurde 2018 als eine Reihe von Micro-Services bereitgestellt, um Integrationen zwischen AEM und Commerce-Engines zu ermöglichen. Nachdem Adobe Mitte 2018 Magento erworben hatte, beschloss Adobe, seinen Ansatz aus zwei Gründen zu ändern. Magento verfügt über einen eigenen Satz von Commerce-APIs (REST und GraphQL) und es empfiehlt sich nicht, zwei API-Sätze zu verwalten. Die Markttrends zeigten, dass Kunden zu GraphQL übergegangen sind, da dies eine effizientere Methode zur Datenabfrage ist. 2019 hat Adobe das neue Commerce Integration Framework (CIF) veröffentlicht, das die GraphQL-APIs von Magento als zentrale, verbindliche Datenquelle verwendet. Adobe plant keine weiteren Investitionen in CIF REST. Kundinnen und Kunden wird dringend empfohlen, die Ersatzlösung zu verwenden.|Wechseln Sie bei AEM-Magento-Integrationen zum [AEM CIF-Archetyp](https://github.com/adobe/aem-cif-project-archetype) und zu [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). Siehe Integration von AEM und Adobe Commerce [mithilfe des Commerce Integration Framework](/help/commerce/cif/integrating/magento.md). Die Unterstützung von Drittanbieter-Integrationen (außer Magento) mit dem neuen Ansatz steht auf dem Programm.||
|Komponenten (AEM Sites) | Adobe plant keine weiteren Verbesserungen der meisten in `/libs/foundation/components` gespeicherten Foundation-Komponenten. Suchen Sie im Komponentenordner nach den Eigenschaften `cq:deprecated` und `cq:deprecatedReason`. Die Foundation-Komponenten sind in AEM 6.5 enthalten und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Darüber hinaus werden die Foundation-Komponenten unterstützt, auch wenn sie veraltet sind. | Adobe empfiehlt die Verwendung der Kernkomponenten für zukünftige Projekte. Vorhandene Websites können unverändert bleiben, oder Sie gestalten die Website mit der [AEM-Modernisierungs-Tool-Suite](https://github.com/adobe/aem-modernize-tools) so um, dass Kernkomponenten verwendet werden. ||
|Komponenten (AEM Sites)|Design-Import-Tool-Komponenten `/libs/wcm/designimporter/components` sind seit 6.5 als veraltet gekennzeichnet. Adobe plant keine weiteren Verbesserungen an dieser Implementierung des Design-Import-Tools. | Adobe plant für künftige Versionen eine alternative Implementierung des Nutzungsszenarios. ||
|Foundation|Granite-Auslagerungs-Framework. Adobe plant keine weiteren Verbesserungen am Auslagerungs-Framework, das in Version CQ 5.6.1 zur Externalisierung der Asset-Verarbeitung eingeführt wurde.|Adobe arbeitet an einem Cloud-nativen Auslagerungs-Framework der nächsten Generation.||
|Entwickler|`Hobbes.js`. Adobe plant keine weiteren Verbesserungen am `hobbes.js`-Framework zum Testen von Benutzeroberflächen.|Adobe empfiehlt, dass Kundinnen und Kunden die Selenium-Automatisierung verwenden.||
|Entwickler|jQuery UI-Client-Bibliothek. Adobe plant nicht, die jQuery UI-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu pflegen und zu aktualisieren.|Adobe empfiehlt Kundinnen und Kunden, die weiterhin eine jQuery-Benutzeroberfläche für ihren Code benötigen, diese der Code-Basis ihrer Projekte hinzuzufügen.||
|Entwickler|jQuery-Animation-Client-Bibliothek (`granite.jquery.animation`). Adobe plant nicht, die jQuery-Animation-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu pflegen und zu aktualisieren.|Adobe empfiehlt Kundinnen und Kunden, die weiterhin jQuery-Animationen für ihren Code benötigen, diese in die Code-Basis ihrer Projekte einzufügen.||
|Entwickler|Handlebars-Client-Bibliothek. Adobe plant nicht, die Handlebars-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu pflegen und zu aktualisieren.|Adobe empfiehlt Kundinnen und Kunden, die weiterhin Handlebars für ihren Code benötigen, diese in die Code-Basis ihrer Projekte einzufügen.||
|Entwickler|Lawnchair-Client-Bibliothek. Adobe plant nicht, die im Rahmen der Distribution bereitgestellte Lawnchair-Client-Bibliothek weiter zu pflegen und zu aktualisieren (Quickstart).|Adobe empfiehlt Kundinnen und Kunden, die weiterhin Lawnchair für ihren Code benötigen, diese in die Code-Basis ihrer Projekte einzufügen.||
|Entwickler|`Granite.Sling.js`-Client-Bibliothek. Adobe plant nicht, die Granite.Sling.js-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu erweitern.|Adobe empfiehlt Kundinnen und Kunden, die auf die Bibliotheksfunktion angewiesen sind, ihren Code zu refaktorieren und nicht mehr zu verwenden.||
|Entwickler|Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken. Adobe plant keine weitere Aktualisierung der YUI-Bibliothek. Bis AEM 6.4 wurde YUI standardmäßig verwendet, um JavaScript zu minimieren – mit optionalem Wechsel zu Google Closure Compiler (GCC). Ab AEM 6.5 ist GCC der Standard.|Adobe empfiehlt Kundinnen und Kunden, die auf AEM 6.5 aktualisieren, für ihre Implementierung auf GCC zu wechseln.||
|Entwickler|Dialog-Editor für die klassische Benutzeroberfläche in CRXDE Lite. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Distribution (Quickstart) bereitgestellt wird.| Es ist kein Ersatz verfügbar. ||
|Forms|Die Integration von AEM Forms in AEM Mobile ist veraltet. | Es ist kein Ersatz verfügbar. ||Entwickler|Dialog-Editor für klassische Benutzeroberflächen in CRXDE Lite. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Distribution (Quickstart) bereitgestellt wird.| Es ist kein Ersatz verfügbar. ||
|Developers|Lodash/Underscore-Client-Bibliothek. Adobe plant nicht, die Lodash-/Unterstrich-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu pflegen und zu aktualisieren. | Adobe empfiehlt Kundinnen und Kunden, die für ihren Code weiterhin einen Lodash/Unterstrich benötigen, diesen in die Code-Basis ihrer Projekte einzufügen. || |Screens|Adobe plant nicht, das com.adobe.cq.screens.mq.activemq-Bundle und die damit verbundenen Konfigurationen, die für die Einrichtung von 2Publishern verwendet werden, weiter zu verwalten und zu aktualisieren.| Adobe empfiehlt Kunden, die weiterhin die Einrichtung von 2Publishern benötigen, die [Lastenausgleich](https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=screens&amp;title=AEM+Screens+publish+environment+horizontal+scaling+through+Load+Balancer+session+stickiness) Ansatz. ||

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die aus AEM 6.5 entfernt wurden und in früheren Versionen als veraltet gekennzeichnet waren.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |
| Integration mit [!DNL Experience Cloud] | Sie können Ihre Assets mit [!DNL Experience Cloud] synchronisieren, mithilfe einer Konfiguration über [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] hieß zuvor [!DNL Adobe Experience Cloud]. | Bei Fragen [wenden Sie sich an den Kunden-Support von Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support). |  |
| Analytics-Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Verwenden Sie das [von Adobe Analytics bereitgestellte Activity Map-Plug-in](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de). |  |
| Integrationen | Die ExactTarget-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist nicht mehr verfügbar. | Kein Ersatz. |  |
| Integrationen | Die Salesforce Force-API-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist jetzt ein zusätzliches, über [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) zu installierendes Paket. | Die Funktion ist immer noch verfügbar. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Dienst wurde entfernt, da das Adobe Central-Produkt nicht mehr unterstützt wird. | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Kein Ersatz vorhanden. |  |
| Formulare | Ein einmaliges Upgrade von LiveCycle ES4 SP1 auf AEM 6.5 Forms on JEE ist nicht verfügbar. | In der Dokumentation zu AEM Forms-Upgrades finden Sie die [verfügbaren Upgrade-Pfade](../forms/using/upgrade.md). |  |
| Formulare | Unterstützung für UPD-basiertes Clustering wurde von AEM Forms on JEE entfernt | Sie können nur TCP-basiertes Clustering in AEM Forms on JEE verwenden. Wenn Sie für einen UDP-Multicast-Server ein Upgrade von einer früheren Version auf AEM 5.5 Forms on JEE durchführen, führen Sie manuelle Konfigurationen durch, um zum TCP-basierten Gemfire-Clustering zu wechseln. Detaillierte Anweisungen finden Sie unter [Upgrade auf AEM 6.5 Forms on JEE](../forms/using/upgrade-forms-jee.md) |  |
| Entwickler  | Firebug Lite wurde aus der Standardverteilung (Quickstart) entfernt | Verwenden der integrierten Entwicklerkonsolen des Browsers |
| Entwickler  | Die Unterstützung für `customJavaScriptPath` wurde im HTML Client Library Manager eingestellt. | Kein Ersatz vorhanden. |  |
| [!DNL Assets] | Die Asset-Auslagerungsfunktion wurde in [!DNL Adobe Experience Manager] 6.5 entfernt. | Es steht kein Ersatz zur Verfügung. |  |
| Cache | `system/console/slingjsp` wurde entfernt und ist nicht mehr in AEM 6.5 verfügbar. | Klassen und Slightly-Cache werden im Apache Sling Commons FileSystem ClassLoader-Bundle gespeichert. Sie können die Bundle-Nummer in der AEM-Web-Konsole überprüfen und den Cache-Ordner direkt aus dem Dateisystem entfernen (`crx-quickstart/launchpad/felix/bundle<ID>`). |  |

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Dieser Abschnitt wird verwendet, um die bevorstehenden Änderungen in zukünftigen Versionen vorab anzukündigen. Die angekündigten Änderungen sind noch nicht wirksam, wirken sich jedoch auf die Kunden aus. Die Funktionen sind zum Beispiel noch nicht veraltet, haben aber Auswirkungen auf die Benutzenden, sobald sie veraltet sind. Diese Updates werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Ankündigung |
|--- |--- |--- |
| Foundation | UI-Framework | Adobe plant, die Coral UI 2-Komponenten 2 im Jahr 2019 zu veraltet zu machen. Coral UI 3 wurde mit AEM 6.2 eingeführt und AEM 6.5 basiert vollständig auf Coral 3. Adobe empfiehlt Kunden und Partnern, die benutzerdefinierte Benutzeroberflächen mit Coral 2 erstellt haben, diese auf Coral 3 umzugestalten. Adobe stellt ein Tool zum Konvertieren von Coral 2-Dialogfeldern in Coral 3 bereit - [Mehr dazu](/help/sites-developing/modernization-tools.md). |
