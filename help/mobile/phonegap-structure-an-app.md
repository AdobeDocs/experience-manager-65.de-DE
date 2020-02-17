---
title: App strukturieren
seo-title: App strukturieren
description: Auf dieser Seite erfahren Sie, wie Sie eine App-Struktur erstellen. Diese Seite beschreibt, wie Vorlagen und Komponenten zusammen mit Informationen zu JavaScript und CSS Clientlibs strukturiert werden.
seo-description: Auf dieser Seite erfahren Sie, wie Sie eine App-Struktur erstellen. Diese Seite beschreibt, wie Vorlagen und Komponenten zusammen mit Informationen zu JavaScript und CSS Clientlibs strukturiert werden.
uuid: bf0e8b0c-a075-4847-b56d-de458715027c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c614a7ff-0d13-4407-bda0-c0a402a13dcd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# App strukturieren{#structure-an-app}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Ein AEM Mobile-Projekt umfasst verschiedene Inhaltstypen wie Seiten, JavaScript- und CSS-Client-Bibliotheken, wiederverwendbare AEM-Komponenten, Inhaltssynchronisierungskonfigurationen und PhoneGap-App-Shell-Inhalte. Die Stützung Ihrer neuen AEM Mobile-App auf dem [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) ist eine gute Möglichkeit, alle verschiedenen Inhaltstypen in unsere empfohlene Struktur zu integrieren, um die Portabilität und Wartbarkeit langfristig zu erleichtern.

## Seiteninhalt {#page-content}

Die Seiten Ihrer Anwendung sollten sich alle unter &quot;/content/mobileapps&quot;befinden, damit sie von der AEM Mobile-Konsole erkannt werden.

![chlimage_1-52](assets/chlimage_1-52.png)

Gemäß der AEM-Konvention sollte die erste Seite Ihrer App eine Umleitung zu einem untergeordneten Element der App sein, das als Standardsprache der App dient (&quot;en&quot;in beiden Fällen &quot;Geometrixx&quot;und &quot;Starter Kit&quot;). Die Seite mit dem Gebietsschema auf der obersten Ebene wird normalerweise von der Komponente &quot;splash-page&quot;der Stiftung (/libs/mobileapps/components/splash-page) übernommen, die die erforderliche Initialisierung übernimmt, um die Installation von Updates mit der Inhaltssynchronisierung zu unterstützen (der contentInit-Code kann unter /etc/clientlibs/mobile/content-sync/js/contentInit.js gefunden werden).

## Vorlagen und Komponenten {#templates-and-components}

Der Vorlagen- und Komponentencode für Ihre App sollte sich unter /apps//&lt;Name der App>/ befinden. In Übereinstimmung mit der Konvention sollten Sie Ihre Vorlage und Ihren Komponentencode in /apps/&lt;Name der Marke>/&lt;Name der App> platzieren. Dieses Muster sollte Entwicklern vertraut sein, die bereits mit Site in AEM gearbeitet haben. Es wird normalerweise gefolgt, da &quot;/apps/&quot;in Veröffentlichungsinstanzen standardmäßig auf anonymen Zugriff gesperrt ist. Dementsprechend wird Ihr roher JSP-Code von potenziellen Angreifern verschleiert.

App-spezifische Vorlagen können so konfiguriert werden, dass sie nur angezeigt werden, indem der `allowedPaths` Eigenschafts-Knoten in der Vorlage selbst verwendet und der zugehörige Wert auf &quot;/content/mobileapps(/&quot;festgelegt wird.&amp;ast;)?&quot; - oder etwas Spezifischeres, wenn die Vorlage nur für eine einzelne App verwendet werden sollte. Die `allowedParents` und `allowedChildren` Eigenschaften können auch für eine sehr feine, abgestufte Steuerung genutzt werden, welche Vorlagen einem Autor je nach dem Erstellungsort der neuen Seite zur Verfügung stehen.

Wenn Sie eine neue App-Seitenkomponente von Grund auf neu erstellen, wird empfohlen, ihre `sling:resourceSuperType` Eigenschaft auf &quot;mobileapps/components/angular/ng-page&quot;festzulegen. Dadurch wird Ihre Seite sowohl für das Authoring als auch für das Rendering als eine einseitige App eingerichtet und Sie können alle .jsp-Dateien überlagern, die Ihre Komponente möglicherweise ändern muss. Da ng-page überhaupt kein UI-Framework enthält, wird ein Entwickler in der Regel Überlagerungen (mindestens) &quot;template.jsp&quot;(überlagert von /libs/mobileapps/components/angular/ng-page/template.jsp) erstellen.

Autorbare Seitenkomponenten, die AngularJS nutzen möchten, verfügen über eine gleichwertige `sling:resourceSuperType` Komponente unter /libs/mobileapps/components/angular/ng-component, die auf dieselbe Weise überlagert und angepasst werden kann.

## JavaScript- und CSS-Clientlibs {#javascript-and-css-clientlibs}

Wenn es um Client-Bibliotheken geht, stehen dem Entwickler einige Optionen zur Verfügung, wo sie im Repository abgelegt werden können. Das folgende Muster wird zur Orientierung angeboten, ist aber keine schwierige Voraussetzung.

Wenn der clientseitige Code selbstständig sein kann und nicht mit einer bestimmten Komponente Ihrer Anwendung in Verbindung steht - d. h., er kann in anderen Anwendungen wiederverwendet werden -, empfehlen wir, ihn in /etc/clientlibs// zu speichern. Wenn die clientlib-Datei hingegen für eine einzelne App spezifisch ist, können Sie sie als untergeordnetes Element des Design-Knotens Ihrer App verschachteln. /etc/designs/phonegap/&lt;Name der Marke>//clientlibs. Diese clientlib-Kategorie sollte nicht von anderen libs verwendet werden und sollte verwendet werden, um andere libs nach Bedarf einzubetten. Wenn Sie diesen Mustern folgen, müssen Entwickler keine neuen Content Sync-Konfigurationen jedes Mal hinzufügen, wenn eine Client-Bibliothek der App hinzugefügt wird, und stattdessen einfach die Eigenschaft &quot;embed&quot;des Entwurfs-clientlib der App aktualisieren. Sehen Sie sich beispielsweise den Knoten Geometrixx clientlibs-all Content Sync unter /content/phonegap/geometrixx-outdoors/en/jcr:content/pge-app/app-config/clientlibs-all an.

Wenn Ihr clientseitiger Code eng mit einer bestimmten Komponente verbunden ist, platzieren Sie diesen Code in einer Client-Bibliothek, die unter dem Speicherort der Komponente in &quot;/apps/&quot;verschachtelt ist, und betten Sie ihn in die &quot;design&quot;-clientlib Ihrer App ein.

## PhoneGap Configuration {#phonegap-configuration}

Jede AEM Mobile-App enthält einen Ordner, in dem die Konfigurationsdateien gespeichert sind, die von der PhoneGap- [Befehlszeilenschnittstelle](https://github.com/phonegap/phonegap-cli) und dem [PhoneGap-Build](https://build.phonegap.com/) verwendet werden, um Ihre Webinhalte in eine ausführbare Anwendung zu verwandeln. Im Geometrixx-Beispiel befindet sich dieser Ordner (/content/phonegap/geometrixx-outdoors/shell/jcr:content/page-app/app-content) beispielsweise als Teil der Shell; eine Designentscheidung getroffen wurde, weil sie nur Inhalte enthält, die nicht im Freien aktualisiert werden können, z. B. Plugins, die Geräte-APIs und die Konfiguration der App selbst betreffen.

In diesem Verzeichnis finden Sie auch eine Reihe von [Cordova-Haken](https://cordova.apache.org/docs/en/edge/guide_appdev_hooks_index.md.html#Hooks%20Guide) , die zum Installieren von Plugins, Platzieren von Ressourcendateien an ihren plattformspezifischen Speicherorten und andere Aktionen verwendet werden können, die als Teil des Builds ausgeführt werden sollten. Hinweis: als Alternative zum Herunterladen jedes Plugins als Teil des Builds können Sie dem Muster der Kitchen Sink-App folgen und [Plugin-Quellcode](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) mit dem Rest Ihres App-Projekts einschließen.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie mehr über die Struktur der App erfahren haben, lesen Sie [Erstellen und Bearbeiten der Apps mit der App-Konsole](/help/mobile/phonegap-apps-console.md).
