---
title: Veraltete und entfernte Funktionen in Adobe Experience Manager 6.5.
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.5.
exl-id: d9b6140a-c37d-4b90-a60c-01f471d65621
source-git-commit: c9db5a1764d98bb049c08a0e6962b7ed5e1bfe5c
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 42%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Mitteilung der bevorstehenden Entfernung oder Ersetzung AEM Funktionen gelten folgende Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese Funktion nicht mehr unterstützt wird, sind die Funktionen weiterhin verfügbar, sie werden jedoch nicht weiter verbessert.
1. Die veralteten Funktionen werden frühestens in der folgenden Hauptversion entfernt. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die in AEM 6.5 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz | Version (SP) |
|---|---|---|---|
| [!DNL Sites] | Inhaltsfragmentvorlagen zum Erstellen einfacher Inhaltsfragmente. | [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md) jetzt. | 6.5.11.0 |
| Creative Cloud-Integration | Die AEM zur Ordnerfreigabe in Creative Cloud wurde in AEM 6.2 eingeführt, um kreativen Benutzern den Zugriff auf Assets aus AEM zu ermöglichen, damit sie sie in öffnen können. [!DNL Creative Cloud] und laden Sie neue Dateien hoch oder speichern Sie Änderungen in AEM. Eine neue Funktion des Creative Cloud-Programms, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus. Adobe plant keine weiteren Verbesserungen an der Integration der Ordnerfreigabe aus AEM in Creative Cloud. Obwohl die Funktion in AEM enthalten ist, wird Kunden ausdrücklich der Einsatz von Ersatzlösungen empfohlen. | Kunden wird empfohlen, zu neuen Creative Cloud-Integrationsfunktionen wie Adobe Asset Link oder AEM Desktop-Programm zu wechseln. |  |
| Assets | `AssetDownloadServlet` ist bei den Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md). | Konfiguration, wie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md) beschrieben. |  |
| Assets | Wenn ein Benutzer nicht über ausreichende (Lese- und Schreibberechtigungen) für `/content/dam/collections`, kann der Benutzer keine Sammlung erstellen. | Einhaltung der Zugangssteuerungseinrichtung für den Benutzer und Sicherstellung entsprechender Berechtigungen.  |  |
| Adobe Search &amp; Promote | Die Integration mit Adobe Search&amp;Promote wird nicht mehr unterstützt. Adobe plant keine weiteren Verbesserungen an der Search &amp; Promote-Integration. Beachten Sie, dass die Search &amp; Promote-Integration zwar veraltet ist, aber weiterhin umfassend unterstützt wird. |  |  |
| DTM Tag Manager | Die Integration in DTM (Dynamic Tag Manager) ist als veraltet gekennzeichnet. | Steigen Sie auf Adobe Experience Platform als Tagmanager um.. |  |
| Adobe Target | Hinzufügen der Möglichkeit für AEM, mithilfe der [!DNL Adobe I/O] Aufgrund der Adobe Target Standard-API (Rest-API) in AEM 6.5 wird die Target Classic-API-Methode (XML) nicht mehr unterstützt. | Integration neu konfigurieren zu [die neue API verwenden](https://helpx.adobe.com/de/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html). |  |
| Adobe Target | Verwenden der `mbox.js` Die basierte Integration mit Adobe Target in AEM wird nicht mehr unterstützt. | Zur Verwendung wechseln `at.js` 1.x. |  |
| Commerce | [CIF REST](https://github.com/adobe/commerce-cif-api) wurde 2018 als Microservices bereitgestellt, um Integrationen zwischen AEM- und Commerce-Engines zu ermöglichen. Nachdem Adobe Mitte 2018 Magento erworben hatte, beschloss Adobe, ihren Ansatz aus zwei Gründen zu ändern. Magento verfügt über einen eigenen Satz von Commerce-APIs (REST und GraphQL) und es empfiehlt sich nicht, zwei API-Sätze zu verwalten. Die Markttrends zeigten, dass Kunden zu GraphQL übergegangen sind, da dies eine effizientere Methode zur Datenabfrage ist. 2019 hat Adobe das neue Commerce Integration Framework veröffentlicht, das die GraphQL-APIs von Magento als &quot;Source of Truth&quot;verwendet. Adobe plant keine weiteren Investitionen in CIF REST. Kunden wird dringend empfohlen, die Ersatzlösung zu verwenden. | Wechseln Sie bei AEM-Magento-Integrationen zu [CIF-Archetyp AEM](https://github.com/adobe/aem-cif-project-archetype) und [CIF-Kernkomponenten AEM](https://github.com/adobe/aem-core-cif-components). Siehe AEM- und Magento-Integration [Verwenden des Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md). Die Unterstützung von Drittanbieter-Integrationen (außer Magento) mit dem neuen Ansatz liegt auf unserer Roadmap. |  |
| Komponenten (AEM Sites) | Adobe plant keine weiteren Verbesserungen an den meisten Foundation-Komponenten, die in gespeichert sind. `/libs/foundation/components`. Suchen Sie nach `cq:deprecated` und `cq:deprecatedReason` -Eigenschaft im Komponentenordner. In AEM 6.5 sind die Foundation-Komponenten enthalten, und Kunden, die ein Upgrade von früheren Versionen durchführen, können diese weiterhin unverändert verwenden. Darüber hinaus werden die Foundation-Komponenten vollständig unterstützt, auch wenn sie nicht mehr unterstützt werden. | Adobe empfiehlt die Verwendung der Kernkomponenten für zukünftige Projekte. Vorhandene Sites können unverändert bleiben oder die [AEM Modernisierung der Tools Suite](https://github.com/adobe/aem-modernize-tools) , um die Site für die Verwendung von Kernkomponenten umzugestalten. |  |
| Komponenten (AEM Sites) | Design Importer-Komponenten `/libs/wcm/designimporter/components` wurden ab 6.5 als veraltet gekennzeichnet. Adobe plant keine weiteren Verbesserungen an der Implementierung des Design Importers. | Adobe plant, eine alternative Implementierung des Anwendungsfalls in zukünftigen Versionen bereitzustellen. |  |
| Foundation | Granite-Abladeframework. Adobe plant keine weiteren Verbesserungen am Abladeframework, das in CQ 5.6.1 eingeführt wurde, um die Asset-Verarbeitung zu externalisieren. | Adobe arbeitet an einem cloudnativen Abladeframework der nächsten Generation. |  |
| Entwickler | `Hobbes.js`. Adobe plant keine weiteren Verbesserungen an der `hobbes.js` Testframework für die Benutzeroberfläche. | Adobe empfiehlt, dass Kunden Selenium-Automatisierung verwenden. |  |
| Entwickler | jQuery UI-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der jQuery UI-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die weiterhin jQuery-Benutzeroberfläche für ihren Code benötigen, diese zur Projektcodebasis hinzuzufügen. |  |
| Entwickler | jQuery Animation-Client-Bibliothek (`granite.jquery.animation`). Adobe plant keine weitere Pflege und Aktualisierung der jQuery Animation-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die für ihren Code weiterhin jQuery Animations benötigen, ihn zu ihrer Projektcodebasis hinzuzufügen. |  |
| Entwickler | Handlebars-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Handlebars-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die weiterhin Handlebars für ihren Code benötigen, ihn zu ihrer Projektcodebasis hinzuzufügen. |  |
| Entwickler | Lawnchair-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Lawnchair-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die weiterhin Lawnchair für ihren Code benötigen, ihn zu ihrer Projektcodebasis hinzuzufügen. |  |
| Entwickler | `Granite.Sling.js` Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Granite.Sling.js-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die auf die Fähigkeit der -Bibliothek angewiesen sind, ihren Code zu umgestalten und nicht mehr zu verwenden. |  |
| Entwickler | Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken: Adobe plant keine weitere Aktualisierung der YUI-Bibliothek. Bis AEM 6.4 wurde JavaScript in der YUI standardmäßig mit der Option zum Google Closure Compiler (GCC) minimiert. Ab AEM 6.5 ist GCC der Standard. | Adobe empfiehlt Kunden, die auf AEM 6.5 aktualisieren, zur Implementierung auf GCC zu wechseln |  |
| Entwickler | Dialog-Editor für klassische UI in CRXDE Lite.. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Es steht kein Ersatz zur Verfügung. |  |
| Formulare | Die Integration von AEM Forms mit AEM Mobile wird nicht mehr unterstützt. | Es ist kein Ersatz verfügbar. |  | Entwickler | Dialog-Editor für klassische UI in CRXDE Lite.. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Es steht kein Ersatz zur Verfügung. |  |
| Entwickler | Client-Bibliothek laden/unterstreichen. Adobe plant nicht, die Lodash-/Unterstrich-Client-Bibliothek, die im Rahmen der Distribution (Quickstart) bereitgestellt wird, weiter zu pflegen und zu aktualisieren. | Adobe empfiehlt Kunden, die für ihren Code weiterhin einen Bindestrich/Unterstrich benötigen, diesen zur Projektcodebasis hinzuzufügen. |  |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgelistet, die aus AEM 6.5 entfernt wurden. Frühere Versionen dieser Funktionen waren als veraltet gekennzeichnet.

| Bereich | Funktion | Ersatz | Version (SP) |
|--- |--- |--- |--- |
| Integration mit [!DNL Experience Cloud] | Sie können Ihre Assets mit synchronisieren. [!DNL Experience Cloud] mithilfe einer Konfiguration über [!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] zuvor [!DNL Adobe Marketing Cloud]. | Bei Abfragen: [Adobe-Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html). |  |
| Analytics Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Verwenden Sie die [Von Adobe Analytics bereitgestelltes ActivityMap-Plugin](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de#activity-map). |  |
| Integrationen | Die ExactTarget-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist nicht mehr verfügbar. | Kein Ersatz. |  |
| Integrationen | Die Salesforce Force API-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist jetzt ein zusätzliches Paket, aus dem installiert werden kann [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). | Die Funktion ist weiterhin verfügbar. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Service wurde eingestellt, da Adobe Central nicht länger unterstützt wird. | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Kein Ersatz. |  |
| Formulare | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Kein Ersatz vorhanden. |  |
| Formulare | Eine einmalige Aktualisierung von LiveCycle ES4 SP1 auf AEM 6.5 Forms on JEE ist nicht verfügbar. | Siehe [verfügbare Aktualisierungspfade](../forms/using/upgrade.md) in der AEM Forms-Upgrade-Dokumentation. |  |
| Formulare | Unterstützung für UPD-basiertes Clustering von AEM Forms on JEE entfernt | Sie können nur TCP-basiertes Clustering in AEM Forms on JEE verwenden. Wenn Sie ein UDP-Multicast-Server von einer früheren Version auf AEM 5.5 Forms on JEE aktualisieren, führen Sie manuelle Konfigurationen durch, um zum TCP-basierten Gemfire-Clustering zu wechseln. Detaillierte Anweisungen finden Sie unter [Aktualisierung auf AEM 6.5 Forms on JEE](../forms/using/upgrade-forms-jee.md) |  |
| Entwickler | Firebug Lite wurde aus der Standardverteilung (Quickstart) entfernt. | Verwenden Sie die im Browser integrierten Entwicklerkonsolen. |
| Entwickler | Entfernen `customJavaScriptPath` Unterstützung im HTML Client Library Manager. | Kein Ersatz vorhanden. |  |
| [!DNL Assets] | Die Asset-Abladefunktion wird in [!DNL Adobe Experience Manager] 6.5. | Es steht kein Ersatz zur Verfügung. |  |
| Cache | `system/console/slingjsp` entfernt ist nicht mehr in AEM 6.5 verfügbar. | Klassen und Slightly-Cache werden im Apache Sling Commons FileSystem ClassLoader-Bundle gespeichert. Sie können die Bundle-Nummer in der AEM Web Console überprüfen und den Cache-Ordner direkt aus dem Dateisystem entfernen (`crx-quickstart/launchpad/felix/bundle<ID>`). |  |

## Vorankündigung für die nächste Version {#pre-announcement-for-next-release}

Dieser Abschnitt wird verwendet, um die bevorstehenden Änderungen in zukünftigen Versionen vorab anzukündigen. Die angekündigten Änderungen sind noch nicht wirksam, wirken sich jedoch auf die Kunden aus. Beispielsweise sind die Funktionen noch nicht veraltet, wirken sich aber nach der Einstellung auf die Benutzer aus. Diese Updates werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Mitteilung |
|--- |--- |--- |
| Stiftung | UI-Framework | Adobe plant, die Coral UI 2-Komponenten im Jahr 2019 als veraltet zu kennzeichnen. Coral UI 3 wurde mit AEM 6.2 eingeführt und AEM 6.5 basiert vollständig auf Coral 3. Adobe empfiehlt Kunden und Partnern, die benutzerdefinierte UIs mit Coral 2 erstellt haben, ihre UIs für Coral 3 neu zu strukturieren. Adobe stellt ein Tool zur Konvertierung von Coral 2-Dialogfeldern in Coral 3 bereit. [Klicken Sie hier, um mehr zu erfahren.](/help/sites-developing/modernization-tools.md) |
