---
title: App strukturieren
description: Auf dieser Seite erfahren Sie, wie Sie eine App-Struktur erstellen. Auf dieser Seite wird beschrieben, wie Sie Vorlagen und Komponenten zusammen mit Informationen zu JavaScript- und CSS-Clientlibs strukturieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: f37f239f-065b-44f8-acb1-93485b713b49
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 2%

---

# App strukturieren{#structure-an-app}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Ein AEM Mobile-Projekt umfasst eine Vielzahl von Inhaltstypen, darunter Seiten, JavaScript- und CSS-Client-Bibliotheken, wiederverwendbare AEM, Inhaltssynchronisierungskonfigurationen und Shell-Inhalte der PhoneGap-App. Stützen der neuen AEM Mobile-App auf [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) ist eine gute Möglichkeit, alle verschiedenen Inhaltstypen in unsere empfohlene Struktur zu integrieren, um die Portabilität und Wartbarkeit langfristig zu erleichtern.

## Seiteninhalt {#page-content}

Die Seiten Ihrer Anwendung sollten sich alle unter /content/mobileapps befinden, damit sie von der AEM Mobile-Konsole erkannt werden.

![chlimage_1-52](assets/chlimage_1-52.png)

Standardmäßig sollte die erste Seite Ihrer App eine Umleitung zu einem seiner untergeordneten Elemente sein, die als Standardsprache der App dienen (&quot;en&quot;sowohl in Geometrixx- als auch in Starter Kit-Fällen). Die Gebietsschema-Seite der obersten Ebene übernimmt normalerweise die Foundation-Komponente &quot;splash-page&quot;(/libs/mobileapps/components/splash-page), die die erforderliche Initialisierung übernimmt, um die Installation von Aktualisierungen der Inhaltssynchronisierung über die Luft zu unterstützen (der ContentInit-Code finden Sie unter /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Vorlagen und Komponenten {#templates-and-components}

Vorlage und Komponentencode für Ihre App sollten sich in /apps/ befinden.&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. In Übereinstimmung mit der Konvention sollten Sie Ihre Vorlage und Ihren Komponentencode in /apps/ platzieren.&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. Dieses Muster sollte Entwicklern bekannt sein, die bereits mit Site in AEM gearbeitet haben. Dies wird in der Regel so ausgeführt, dass /apps/ standardmäßig in Veröffentlichungsinstanzen auf anonymen Zugriff beschränkt ist. Ihr roher JSP-Code ist also vor potenziellen Angreifern verborgen.

App-spezifische Vorlagen können so konfiguriert werden, dass sie nur mit dem `allowedPaths` Eigenschaftenknoten auf der Vorlage selbst und legen Sie den Wert auf &quot;/content/mobileapps(/&quot;fest.&amp;ast;)?&#39; - oder etwas spezifischeres, wenn die Vorlage nur für eine einzelne App verwendet werden sollte. Die `allowedParents` und `allowedChildren` -Eigenschaften können auch verwendet werden, um präzise steuern zu können, welche Vorlagen einem Autor je nachdem, wo die neue Seite erstellt wird, zur Verfügung stehen.

Wenn Sie eine App-Seitenkomponente von Grund auf neu erstellen, wird empfohlen, `sling:resourceSuperType` -Eigenschaft auf &quot;mobileapps/components/angular/ng-page&quot;fest. Dadurch wird Ihre Seite sowohl für das Authoring als auch für das Rendering als Einzelseitenanwendung eingerichtet und Sie können alle JSP-Dateien überlagern, die Ihre Komponente möglicherweise ändern muss. Da ng-page überhaupt kein UI-Framework enthält, überlagert ein Entwickler normalerweise (zumindest) &quot;template.jsp&quot;(überlagert von /libs/mobileapps/components/angular/ng-page/template.jsp).

Autorbare Seitenkomponenten, die AngularJS verwenden möchten, verfügen über eine gleichwertige `sling:resourceSuperType` -Komponente unter /libs/mobileapps/components/angular/ng-component , die auf dieselbe Weise überlagert und angepasst werden kann.

## JavaScript- und CSS-Clientlibs {#javascript-and-css-clientlibs}

In Client-Bibliotheken stehen Entwicklern einige Optionen zur Verfügung, in denen sie sie im Repository platzieren können. Das folgende Muster wird zur Anleitung angeboten, ist jedoch keine schwierige Anforderung.

Wenn Ihr clientseitiger Code alleine stehen kann und nicht mit einer bestimmten Komponente Ihrer Anwendung in Verbindung steht (d. h., er kann in anderen Anwendungen wiederverwendet werden), empfiehlt Adobe, ihn in /etc/clientlibs/ zu speichern.&lt;brand name=&quot;&quot;>/&lt;lib name=&quot;&quot;>. Wenn die clientlib dagegen für eine einzelne App spezifisch ist, können Sie sie als untergeordnetes Element des Design-Knotens Ihrer App verschachteln: /etc/designs/phonegap/&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>/clientlibs. Verwenden Sie nicht die Kategorie dieser clientlib mit anderen Bibliotheken, sondern betten Sie ggf. andere Bibliotheken ein. Dadurch wird verhindert, dass Entwickler bei jedem Hinzufügen einer Client-Bibliothek zur App neue Konfigurationen für die Inhaltssynchronisierung hinzufügen müssen, anstatt einfach die Eigenschaft &quot;embetts&quot;der Design-Client-Bibliothek der App zu aktualisieren. Betrachten Sie beispielsweise den Konfigurationsknoten &quot;Geometrixx clientlibs-all Content Sync&quot;unter /content/phonegap/geometrixx-outdoors/en/jcr:content/page-app/app-config/clientlibs-all.

Wenn Ihr clientseitiger Code eng mit einer bestimmten Komponente verknüpft ist, platzieren Sie diesen Code in einer Client-Bibliothek, die unter dem Speicherort der Komponente in /apps/ verschachtelt ist, und betten Sie die zugehörige Kategorie in die &quot;Design&quot;-Client-Bibliothek Ihrer App ein.

## PhoneGap-Konfiguration {#phonegap-configuration}

Jede AEM Mobile-App enthält einen Ordner, in dem die von PhoneGap verwendeten Konfigurationsdateien gespeichert werden. [Befehlszeilenschnittstelle](https://github.com/phonegap/phonegap-cli) und PhoneGap-Build unter `https://build.phonegap.com/` , um Ihren Webinhalt in eine ausführbare Anwendung umzuwandeln. Im Geometrixx-Beispiel befindet sich dieser Ordner (/content/phonegap/geometrixx-outdoors/shell/jcr:content/page-app/app-content) als Teil der Shell. Eine Designentscheidung wurde getroffen, da er nur Inhalte enthält, die nicht direkt aktualisiert werden können, z. B. Plug-ins, die Geräte-APIs und die Konfiguration der App selbst behandeln.

In diesem Verzeichnis finden Sie auch einige [Cordova-Hooks](https://cordova.apache.org/docs/en/dev/guide/appdev/hooks/index.html#Hooks%20Guide) , die zum Installieren von Plug-ins, zum Platzieren von Ressourcendateien an ihren plattformspezifischen Speicherorten und anderen Aktionen verwendet werden kann, die im Rahmen des Builds ausgeführt werden sollen. Hinweis: Als Alternative zum Herunterladen jedes Plug-ins im Rahmen des Builds können Sie dem Muster der Kitchen Sink-App folgen und Plug-in-Quellcode einschließen<!-- THIS URL IS 404 (https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) --> mit dem Rest Ihres App-Projekts.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit der Struktur der App vertraut gemacht haben, finden Sie weitere Informationen unter [Erstellen und Bearbeiten von Apps mithilfe der App-Konsole](/help/mobile/phonegap-apps-console.md).
