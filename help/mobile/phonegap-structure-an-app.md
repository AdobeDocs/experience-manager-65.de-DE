---
title: App strukturieren
seo-title: Structure an App
description: Auf dieser Seite erfahren Sie, wie Sie eine App-Struktur erstellen. Auf dieser Seite wird beschrieben, wie Sie Vorlagen und Komponenten zusammen mit Informationen zu JavaScript- und CSS-Clientlibs strukturieren.
seo-description: Follow this page to learn about how to create structure of an app. This page describes how to structure templates and components along with information on JavaScript and CSS Clientlibs.
uuid: bf0e8b0c-a075-4847-b56d-de458715027c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c614a7ff-0d13-4407-bda0-c0a402a13dcd
exl-id: f37f239f-065b-44f8-acb1-93485b713b49
source-git-commit: 17d13e9b201629d9d1519fde4740cf651fe89d2c
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 2%

---

# App strukturieren{#structure-an-app}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Ein AEM Mobile-Projekt umfasst eine Vielzahl von Inhaltstypen, darunter Seiten, JavaScript- und CSS-Client-Bibliotheken, wiederverwendbare AEM, Inhaltssynchronisierungskonfigurationen und Shell-Inhalte der PhoneGap-App. Stützen der neuen AEM Mobile-App auf [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) ist eine gute Möglichkeit, alle verschiedenen Inhaltstypen in unsere empfohlene Struktur zu integrieren, um die Portabilität und Wartbarkeit langfristig zu erleichtern.

## Seiteninhalt {#page-content}

Die Seiten Ihrer Anwendung sollten sich alle unter /content/mobileapps befinden, damit sie von der AEM Mobile-Konsole erkannt werden.

![chlimage_1-52](assets/chlimage_1-52.png)

Standardmäßig sollte die erste Seite Ihrer App eine Umleitung zu einem der untergeordneten Elemente sein, die als Standardsprache der App dient (&quot;en&quot;sowohl in Geometrixx- als auch in Starter Kit-Fällen). Die Gebietsschema-Seite der obersten Ebene übernimmt normalerweise die Foundation-Komponente &quot;splash-page&quot;(/libs/mobileapps/components/splash-page), die die erforderliche Initialisierung übernimmt, um die Installation von Aktualisierungen der Inhaltssynchronisierung außerhalb der Luft zu unterstützen (der ContentInit-Code finden Sie unter /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Vorlagen und Komponenten {#templates-and-components}

Die Vorlage und der Komponentencode für Ihre App sollten sich unter /apps/ befinden.&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. In Übereinstimmung mit der Konvention sollten Sie Ihre Vorlage und Ihren Komponentencode in /apps/ platzieren.&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. Dieses Muster sollte Entwicklern bekannt sein, die bereits mit Site in AEM gearbeitet haben. Dies wird in der Regel so ausgeführt, dass /apps/ standardmäßig in Veröffentlichungsinstanzen auf anonymen Zugriff beschränkt ist. Dementsprechend wird Ihr roher JSP-Code vor potenziellen Angreifern verborgen.

App-spezifische Vorlagen können so konfiguriert werden, dass sie nur mit dem `allowedPaths` Eigenschaftenknoten auf der Vorlage selbst und legen Sie den Wert auf &quot;/content/mobileapps(/&quot;fest.&amp;ast;)?&#39; - oder etwas spezifischeres, wenn die Vorlage nur für eine einzelne App verwendet werden sollte. Die `allowedParents` und `allowedChildren` -Eigenschaften können auch genutzt werden, um sehr präzise steuern zu können, welche Vorlagen einem Autor je nach dem, wo die neue Seite erstellt wird, zur Verfügung stehen.

Wenn Sie eine neue App-Seitenkomponente von Grund auf neu erstellen, wird empfohlen, den `sling:resourceSuperType` -Eigenschaft auf &quot;mobileapps/components/angular/ng-page&quot;fest. Dadurch wird Ihre Seite sowohl für das Authoring als auch für das Rendering als Einzelseitenanwendung eingerichtet und Sie können alle JSP-Dateien überlagern, die Ihre Komponente möglicherweise ändern muss. Da ng-page überhaupt kein UI-Framework enthält, überlagert ein Entwickler normalerweise (zumindest) &quot;template.jsp&quot;(überlagert von /libs/mobileapps/components/angular/ng-page/template.jsp).

Autorenfähige Seitenkomponenten, die AngularJS nutzen möchten, verfügen über eine gleichwertige `sling:resourceSuperType` Komponente unter /libs/mobileapps/components/angular/ng-component , die auf dieselbe Weise überlagert und angepasst werden kann.

## JavaScript- und CSS-Clientlibs {#javascript-and-css-clientlibs}

In Bezug auf Client-Bibliotheken stehen dem Entwickler einige Optionen zur Verfügung, in denen er sie im Repository platzieren kann. Das folgende Muster wird zur Anleitung angeboten, ist jedoch keine schwierige Anforderung.

Wenn Ihr clientseitiger Code alleine stehen kann und nicht mit einer bestimmten Komponente Ihrer Anwendung in Verbindung steht - d. h., er kann in anderen Anwendungen wiederverwendet werden -, empfehlen wir, ihn in /etc/clientlibs/ zu speichern.&lt;brand name=&quot;&quot;>/&lt;lib name=&quot;&quot;>. Wenn die clientlib dagegen für eine einzelne App spezifisch ist, können Sie sie als untergeordnetes Element des Design-Knotens Ihrer App verschachteln. /etc/designs/phonegap/&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>/clientlibs. Die Kategorie dieser clientlib sollte nicht von anderen Bibliotheken verwendet werden und sollte verwendet werden, um ggf. andere Bibliotheken einzubetten. Durch dieses Muster wird verhindert, dass Entwickler bei jedem Hinzufügen einer Client-Bibliothek zur App neue Konfigurationen für die Inhaltssynchronisierung hinzufügen müssen, anstatt einfach die Eigenschaft &quot;embetts&quot;der Design-Client-Bibliothek der App zu aktualisieren. Sehen Sie sich beispielsweise den Konfigurationsknoten Geometrixx clientlibs-all Content Sync unter /content/phonegap/geometrixx-outdoors/en/jcr:content/page-app/app-config/clientlibs-all an.

Wenn Ihr clientseitiger Code eng mit einer bestimmten Komponente verknüpft ist, platzieren Sie diesen Code in einer Client-Bibliothek, die unter dem Speicherort der Komponente in /apps/ verschachtelt ist, und betten Sie ihn in die Client-Bibliothek &quot;Design&quot;Ihrer App ein.

## PhoneGap-Konfiguration {#phonegap-configuration}

Jede AEM Mobile-App enthält einen Ordner, in dem die von PhoneGap verwendeten Konfigurationsdateien gespeichert werden. [Befehlszeilenschnittstelle](https://github.com/phonegap/phonegap-cli) und PhoneGap-Build unter `https://build.phonegap.com/` , um Ihren Webinhalt in eine ausführbare Anwendung umzuwandeln. Im Geometrixx-Beispiel befindet sich dieser Ordner (/content/phonegap/geometrixx-outdoors/shell/jcr:content/page-app/app-content) als Teil der Shell. eine Designentscheidung getroffen wurde, da sie nur Inhalte enthält, die nicht sofort aktualisiert werden können, z. B. Plugins, die Geräte-APIs behandeln und die Konfiguration der App selbst.

In diesem Verzeichnis finden Sie auch eine Reihe von [Cordova-Hooks](https://cordova.apache.org/docs/en/edge/guide_appdev_hooks_index.md.html#Hooks%20Guide) , die zum Installieren von Plug-ins, zum Platzieren von Ressourcendateien an ihren plattformspezifischen Speicherorten und anderen Aktionen verwendet werden kann, die im Rahmen des Builds ausgeführt werden sollen. Hinweis: als Alternative zum Herunterladen jedes Plug-ins als Teil des Builds können Sie dem Muster der Kitchen Sink-App folgen und [Plug-in-Quellcode einschließen](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) mit dem Rest Ihres App-Projekts.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie sich mit der Struktur der App vertraut gemacht haben, finden Sie weitere Informationen unter [Erstellen und Bearbeiten von Apps mithilfe der App Console](/help/mobile/phonegap-apps-console.md).
