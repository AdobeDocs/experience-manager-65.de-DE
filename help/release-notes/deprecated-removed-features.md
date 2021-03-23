---
title: Veraltete und entfernte Funktionen in Adobe Experience Manager 6.5.
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '1719'
ht-degree: 42%

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Für die Mitteilung der bevorstehenden Entfernung oder Ersetzung AEM Funktionen gelten folgende Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Obwohl diese nicht mehr unterstützt werden, sind die Funktionen weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Die veralteten Funktionen werden frühestens in der folgenden Hauptversion entfernt. Das geplante Datum für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden die Merkmale und Funktionen aufgelistet, die in AEM 6.5 als veraltet gekennzeichnet wurden. Im Allgemeinen werden Funktionen, deren Entfernung in einer zukünftigen Version geplant ist, zunächst als veraltet gekennzeichnet und es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz |
|---|---|---|
| Integration von Creative Clouden | Die AEM zum Freigeben von Creative Clouden wurde in AEM 6.2 eingeführt, um kreativen Benutzern Zugriff auf Assets aus AEM zu geben, sodass sie diese in CC-Anwendungen öffnen und neue Dateien hochladen oder Änderungen an AEM speichern können. Eine neue Funktion des Creative Cloud-Programms, Adobe Asset Link, bietet ein wesentlich besseres Benutzererlebnis und einen leistungsfähigeren Zugriff auf Assets aus AEM direkt aus Photoshop, InDesign und Illustrator heraus. Adobe plant keine weiteren Verbesserungen an der Integration der Ordnerfreigabe aus AEM in Creative Cloud. Obwohl die Funktion in AEM enthalten ist, wird Kunden ausdrücklich der Einsatz von Ersatzlösungen empfohlen. | Den Kunden wird empfohlen, auf neue Funktionen zur Creative Cloud-Integration umzustellen, einschließlich Adobe Asset Link oder AEM Desktop-App. Weitere Informationen finden Sie unter Best Practices zur Integration von AEM und Creative Cloud. |
| Assets | `AssetDownloadServlet` ist bei den Veröffentlichungsinstanzen standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md). | Konfiguration, wie unter [Checkliste für die AEM-Sicherheit](/help/sites-administering/security-checklist.md) beschrieben. |
| Assets | Wenn ein Benutzer für `/content/dam/collections` nicht über ausreichende (Lese- und Schreibberechtigungen verfügt, kann er keine Sammlung erstellen. | Einhaltung der Zugangssteuerungseinrichtung für den Benutzer und Sicherstellung entsprechender Berechtigungen.  |
| Adobe Search &amp; Promote | Die Integration mit Adobe Search&amp;Promote ist veraltet. Adobe plant keine weiteren Verbesserungen an der Search &amp; Promote-Integration. Beachten Sie, dass die Search &amp; Promote-Integration zwar veraltet ist, aber weiterhin umfassend unterstützt wird. |  |
| DTM Tag Manager | Die Integration in DTM (Dynamic Tag Manager) ist als veraltet gekennzeichnet. | Steigen Sie auf Adobe Experience Platform als Tagmanager um.. |
| Adobe Target | Die Zielgruppe Classic API (XML)-Methode wird nicht mehr unterstützt, da AEM mit der [!DNL Adobe I/O]-basierten Adobe Target Standard-API (Rest-API) in AEM 6.5 eine Verbindung zum Adobe Target-Dienst herstellen können. | Konfigurieren Sie die Integration auf [verwenden Sie die neue API](https://helpx.adobe.com/de/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html). |
| Adobe Target | Die Verwendung der `mbox.js`-basierten Integration mit Adobe Target in AEM ist veraltet. | Wechseln Sie zu `at.js` 1.x. |
| Commerce | [CIF ](https://github.com/adobe/commerce-cif-api) RESTwurde 2018 als eine Reihe von Mikrodiensten bereitgestellt, um Integrationen zwischen AEM und Commerce-Engines zu ermöglichen. Nachdem Adobe Mitte 2018 Magento erlangt hatte, entschied sich die Adobe aus zwei Gründen, ihren Ansatz zu ändern. Magento verfügt über einen eigenen Satz Commerce-APIs (REST und GraphQL) und es empfiehlt sich nicht, zwei Gruppen von APIs zu verwalten. Die Markttrends deuten darauf hin, dass Kunden sich auf GraphQL zubewegen, weil es eine effizientere Art ist, Daten abzufragen. 2019 hat die Adobe das neue Commerce Integration Framework unter Verwendung der GraphQL APIs von Magento als Wahrheitsquelle veröffentlicht. Adobe plant keine weiteren Investitionen in CIF REST. Kunden wird dringend empfohlen, die Ersatzlösung zu verwenden. | Bei AEM-Magento-Integrationen wechseln Sie zu [AEM CIF-Archetype](https://github.com/adobe/aem-cif-project-archetype) und [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components). Siehe AEM und Magento-Integration [mit Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md). Die Unterstützung von Drittanbieterintegrationen (außer Magento) mit dem neuen Ansatz steht auf unserem Fahrplan. |
| Komponenten (AEM Sites) | Adobe plant keine weiteren Verbesserungen an den meisten in `/libs/foundation/components` gespeicherten Foundation-Komponenten. Suchen Sie im Komponentenordner nach der Eigenschaft `cq:deprecated` und `cq:deprecatedReason`. AEM 6.5 enthält die Foundation-Komponenten, und Kunden, die von früheren Versionen aktualisieren, können diese weiterhin wie bisher verwenden. Darüber hinaus werden die Foundation-Komponenten vollständig unterstützt, auch wenn sie nicht mehr unterstützt werden. | Adobe empfiehlt die Verwendung der Kernkomponenten für zukünftige Projekte. Bestehende Sites können unverändert bleiben oder die [AEM Tools Suite modernisieren](https://github.com/adobe/aem-modernize-tools) verwenden, um die Site für die Verwendung der Kernkomponenten umzugestalten. |
| Komponenten (AEM Sites) | Design Importer-Komponenten `/libs/wcm/designimporter/components` wurden ab Version 6.5 als veraltet markiert. Adobe plant keine weiteren Verbesserungen bei der Implementierung des Design-Importeurs. | Adobe plant, eine alternative Implementierung des Anwendungsfalls in zukünftigen Versionen bereitzustellen. |
| Foundation | Granite-Abladeframework. Adobe plant keine weiteren Verbesserungen am Ablade-Framework, das in CQ 5.6.1 eingeführt wurde, um die Verarbeitung von Assets zu externalisieren. | Adobe arbeitet an einem cloudnativen Abladeframework der nächsten Generation. |
| Entwickler | `Hobbes.js`. Adobe plant keine weiteren Verbesserungen am `hobbes.js`-Testframework für die Benutzeroberfläche. | Adobe empfiehlt, Selenium-Automatisierung zu verwenden. |
| Entwickler | jQuery UI-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der jQuery UI-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die noch jQuery-UI benötigen, um den Code in ihre Projektcodebasis einzufügen. |
| Entwickler | jQuery Animation-Client-Bibliothek (`granite.jquery.animation`). Adobe plant keine weitere Pflege und Aktualisierung der jQuery Animation-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die noch jQuery Animations benötigen, um den Code in ihre Projektcodebasis einzufügen. |
| Entwickler | Handlebars-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Handlebars-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die für ihren Code immer noch Handlebars benötigen, um ihn in ihre Projektcodebasis einzufügen. |
| Entwickler | Lawnchair-Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Lawnchair-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die noch einen Lawnchair benötigen, damit ihr Code in ihre Projektcodebasis aufgenommen werden kann. |
| Entwickler | `Granite.Sling.js` Client-Bibliothek. Adobe plant keine weitere Pflege und Aktualisierung der Granite.Sling.js-Client-Bibliothek, die im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Adobe empfiehlt Kunden, die sich auf die Bibliotheksfunktion verlassen, um ihren Code umzurechnen und nicht mehr zu verwenden. |
| Entwickler | Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken: Adobe plant keine weitere Aktualisierung der YUI-Bibliothek. Bis AEM 6.4 wurde JavaScript standardmäßig mit der Option zum Wechsel zu Google Closure Compiler (GCC) minimiert. Ab AEM 6.5 ist GCC der Standard. | Adobe empfiehlt Kunden, die zur Implementierung auf AEM 6.5 aktualisieren, um auf GCC zu wechseln |
| Entwickler | Dialog-Editor für klassische UI in CRXDE Lite.. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Es steht kein Ersatz zur Verfügung. |
| Formulare | Die AEM Forms-Integration mit AEM Mobile ist veraltet. | Es steht kein Ersatz zur Verfügung. |  | Entwickler | Dialog-Editor für klassische UI in CRXDE Lite.. Adobe plant keine weitere Pflege und Aktualisierung des Dialog-Editors für klassische UI, der im Rahmen der Verteilung (Quickstart) bereitgestellt wird. | Es steht kein Ersatz zur Verfügung. |
| Entwickler | Client-Bibliothek &quot;Lodash/Unterstrich&quot;. Adobe plant nicht, die Lodash/underscore-Client-Bibliothek, die im Lieferumfang enthalten ist, weiter zu pflegen und zu aktualisieren (Quickstart) | Adobe empfiehlt Kunden, die für ihren Code immer noch einen Lodash/Unterstrich benötigen, um ihn in ihre Projektcodebasis einzufügen. |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die aus AEM 6.5 entfernt wurden. Frühere Versionen hatten diese Funktionen als veraltet markiert.

| Bereich | Funktion | Ersatz |
|--- |--- |--- |
| Analytics Activity Map | Die Version der Activity Map, die in AEM enthalten ist. | Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden. Verwenden Sie das [ActivityMap-Plugin, das von Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de#activity-map) bereitgestellt wird. |
| Integrationen | Die ExactTarget-Integration wurde aus der Standardverteilung (QuickStart) entfernt und ist nicht mehr verfügbar. | Kein Ersatz. |
| Integrationen | Die Salesforce Force API-Integration wurde aus der Standardverteilung (Quickstart) entfernt und ist jetzt ein zusätzliches Paket, das von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) installiert werden kann. | Die Funktion ist weiterhin verfügbar. |
| Formulare | Die Unterstützung für den Adobe Central Migration Bridge-Service wurde eingestellt, da Adobe Central nicht länger unterstützt wird. | Kein Ersatz. |
| Formulare | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Kein Ersatz. |
| Formulare | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Kein Ersatz vorhanden. |
| Formulare | Ein Single-Hop-Upgrade von LiveCycle ES4 SP1 auf AEM 6.5 Forms on JEE ist nicht verfügbar | Siehe [Verfügbare Upgrade-Pfade](../forms/using/upgrade.md) in der AEM Forms-Aktualisierungsdokumentation. |
| Formulare | Unterstützung für UPD-basiertes Clustering von AEM Forms on JEE entfernt | Sie können nur TCP-basiertes Clustering in AEM Forms on JEE verwenden. Wenn Sie einen UDP-Multicast-Server von einer früheren Version auf AEM 5.5 Forms on JEE aktualisieren, führen Sie manuelle Konfigurationen durch, um zu TCP-basiertem Gemfire-Clustering zu wechseln. Detaillierte Anweisungen finden Sie unter [Aktualisierung auf AEM 6.5 Forms on JEE](../forms/using/upgrade-forms-jee.md) |
| Entwickler | Firebug Lite wurde aus der Standardverteilung (Quickstart) entfernt. | Verwenden Sie die im Browser integrierten Entwicklerkonsolen. |
| Entwickler | Entfernen Sie die `customJavaScriptPath`-Unterstützung im HTML-Client-Bibliotheksmanager. | Kein Ersatz vorhanden. |
| [!DNL Assets] | Die Funktion zum Abladen von Assets wird in [!DNL Adobe Experience Manager] 6.5 entfernt. | Es steht kein Ersatz zur Verfügung. |
| Cache | `system/console/slingjsp` entfernt ist nicht mehr in AEM 6.5 verfügbar. | Klassen und Leichter Cache werden unter dem Apache Sling Commons FileSystem ClassLoader Bundle gespeichert. Sie können die Bundle-Nummer in der AEM Web Console überprüfen und den Cache-Ordner direkt aus dem Dateisystem (`crx-quickstart/launchpad/felix/bundle<ID>`) entfernen. |

## Vorankündigung für nächste Version {#pre-announcement-for-next-release}

Dieser Abschnitt dient zur Vorankündigung der bevorstehenden Änderungen in den zukünftigen Versionen. Die angekündigten Änderungen sind noch nicht wirksam, wirken sich aber auf die Kunden aus. Beispielsweise sind die Funktionen noch nicht veraltet, wirken sich aber nach dem Verfall auf die Benutzer aus. Diese Updates werden für Planungszwecke bereitgestellt.

| Bereich | Funktion | Mitteilung |
|--- |--- |--- |
| Stiftung | UI-Framework | Adobe plant, die Coral UI 2-Komponenten im Jahr 2019 als veraltet zu kennzeichnen. Coral UI 3 wurde mit AEM 6.2 eingeführt und AEM 6.5 basiert vollständig auf Coral 3. Adobe empfiehlt Kunden und Partnern, die benutzerdefinierte UIs mit Coral 2 erstellt haben, ihre UIs für Coral 3 neu zu strukturieren. Adobe stellt ein Tool zur Konvertierung von Coral 2-Dialogfeldern in Coral 3 bereit. [Klicken Sie hier, um mehr zu erfahren.](/help/sites-developing/modernization-tools.md) |
