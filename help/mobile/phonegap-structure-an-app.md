---
title: Strukturieren einer App
description: Auf dieser Seite erfahren Sie, wie Sie eine Struktur einer App erstellen. Auf dieser Seite wird beschrieben, wie Sie Vorlagen und Komponenten zusammen mit Informationen zu JavaScript- und CSS-Clientlibs strukturieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: f37f239f-065b-44f8-acb1-93485b713b49
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 0%

---

# Strukturieren einer App{#structure-an-app}

{{ue-over-mobile}}

Ein AEM Mobile-Projekt umfasst eine Vielzahl von Inhaltstypen, darunter Seiten, JavaScript- und CSS-Client-Bibliotheken, wiederverwendbare AEM-Komponenten, Inhaltssynchronisierungskonfigurationen und PhoneGap-App-Shell-Inhalte. Wenn Sie Ihre neue AEM Mobile-App auf dem [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) basieren, können Sie alle Arten von Inhalten in unsere empfohlene Struktur integrieren, um sowohl die Portabilität als auch die Wartbarkeit langfristig zu erleichtern.

## Seiteninhalt {#page-content}

Die Seiten Ihrer Anwendung sollten sich alle unter /content/mobileapps befinden, damit sie von der AEM Mobile-Konsole erkannt werden.

![chlimage_1-52](assets/chlimage_1-52.png)

Nach AEM-Konvention sollte die erste Seite der App eine Umleitung auf eines der untergeordneten Elemente sein, die als Standardsprache der App dienen („en“ sowohl in Geometrixx- als auch in Starter Kit-Fällen). Die Gebietsschema-Seite der obersten Ebene erbt normalerweise von der „splash-page“-Foundation-Komponente (/libs/mobileapps/components/splash-page), die die Initialisierung übernimmt, die für die Installation von Over-the-Air-Inhaltssynchronisierungs-Updates erforderlich ist (contentInit-Code finden Sie unter /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Vorlagen und Komponenten {#templates-and-components}

Die Vorlage und der Komponenten-Code für Ihre App sollten unter /apps/&lt;Name der Marke>/&lt;Name der App> zu finden sein. In Übereinstimmung mit der Konvention sollten Sie Ihre Vorlage und den Komponenten-Code in /apps/&lt;Name der Marke>/&lt;Name der App> platzieren. Dieses Muster sollte Entwicklern bekannt sein, die bereits mit Site in AEM gearbeitet haben. Es wird normalerweise gefolgt, da /apps/ auf Veröffentlichungsinstanzen standardmäßig für den anonymen Zugriff gesperrt ist. Ihr roher JSP-Code ist also vor potenziellen Angreifern verborgen.

Anwendungsspezifische Vorlagen können so konfiguriert werden, dass sie nur mithilfe des `allowedPaths` Eigenschaftsknotens auf der Vorlage selbst präsentiert werden, wobei der Wert auf &quot;/content/mobileapps(/&quot; festgelegt wird.&ast;)?&#39; - oder sogar etwas spezifischeres, wenn die Vorlage nur für eine einzelne App nutzbar sein soll. Die `allowedParents`- und `allowedChildren` können auch verwendet werden, um genau zu steuern, welche Vorlagen einem Autor zur Verfügung stehen, je nachdem, wo die neue Seite erstellt wird.

Wenn Sie eine App-Seitenkomponente von Grund auf neu erstellen, wird empfohlen, die `sling:resourceSuperType`-Eigenschaft auf „mobileApps/components/angular/ng-page“ festzulegen. Dadurch wird Ihre Seite für das Authoring und Rendering als Einzelseiten-App eingerichtet und Sie können alle JSP-Dateien überlagern, die Ihre Komponente möglicherweise ändern muss. Da ng-page überhaupt kein UI-Framework enthält, überlagert ein Entwickler meist (zumindest) „template.jsp“ (überlagert von /libs/mobileapps/components/angular/ng-page/template.jsp).

Für bearbeitbare Seitenkomponenten, die AngularJS verwenden möchten, gibt es eine entsprechende `sling:resourceSuperType` unter /libs/mobileapps/components/angular/ng-component, die auf die gleiche Weise überlagert und angepasst werden kann.

## JavaScript- und CSS-Clientlibs {#javascript-and-css-clientlibs}

In Client-Bibliotheken stehen Entwicklern einige Optionen zur Verfügung, um zu entscheiden, wo sie sie im Repository platzieren können. Das folgende Muster dient als Anleitung, ist jedoch keine zwingende Voraussetzung.

Wenn Ihr Client-seitiger Code eigenständig ausgeführt werden kann und sich nicht auf eine bestimmte Komponente Ihrer Anwendung bezieht (d. h. er kann in anderen Anwendungen wiederverwendet werden), empfiehlt Adobe, ihn in &quot;/etc/clientlibs/&lt;Name der Marke>/&lt;Name der Bibliothek>&quot; zu speichern. Wenn die Client-Bibliothek jedoch spezifisch für eine einzelne App ist, können Sie sie als untergeordnetes Element des Design-Knotens Ihrer App verschachteln: /etc/designs/phonegap/&lt;Markenname>/&lt;App-Name>/clientlibs. Verwenden Sie diese Kategorie der Client-Bibliothek nicht mit anderen Bibliotheken. Betten Sie stattdessen ggf. andere Bibliotheken ein. Nach diesem Muster müssen Entwicklerinnen und Entwickler nicht jedes Mal, wenn eine Client-Bibliothek zur App hinzugefügt wird, neue Inhaltssynchronisierungskonfigurationen hinzufügen, sondern sie müssen nur die Eigenschaft „embed“ der Design-Client-Bibliothek der App aktualisieren. Sehen Sie sich beispielsweise den Konfigurationsknoten Geometrixx clientlibs-all content sync unter /content/phonegap/geometrixx-outdoors/en/jcr:content/pge-app/app-config/clientlibs-all an.

Wenn Ihr Client-seitiger Code eng mit einer bestimmten Komponente verknüpft ist, platzieren Sie diesen Code in einer Client-Bibliothek, die unter dem Speicherort der Komponente in /apps/ verschachtelt ist, und betten Sie ihre Kategorie in die Client-Bibliothek „Design“ Ihrer Anwendung ein.

## Telefonlückenkonfiguration {#phonegap-configuration}

Jede AEM Mobile-App enthält ein Verzeichnis, in dem die von PhoneGap [Befehlszeilenschnittstelle) und PhoneGap](https://github.com/phonegap/phonegap-cli)Build verwendeten Konfigurationsdateien `https://build.phonegap.com/` sind, um Ihren Webinhalt in eine ausführbare Anwendung zu verwandeln. Im Geometrixx-Beispiel beispielsweise befindet sich dieses Verzeichnis (/content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-content) als Teil der Shell. Eine Design-Entscheidung wird getroffen, weil es nur Inhalte enthält, die nicht über die Luft aktualisiert werden können, wie etwa Plug-ins, die sich mit Geräte-APIs und der Konfiguration der App selbst befassen.

In diesem Verzeichnis finden Sie auch einige [Cordova-Hooks](https://cordova.apache.org/docs/en/dev/guide/appdev/hooks/index.html#Hooks%20Guide) die verwendet werden können, um Plug-ins zu installieren, Ressourcendateien an ihren plattformspezifischen Speicherorten zu platzieren und andere Aktionen, die als Teil des Builds ausgeführt werden sollten. Hinweis: Als Alternative zum Herunterladen jedes Plug-ins als Teil des Builds können Sie dem Muster der Kitchen Sink App folgen und den Quell-Code des Plug-ins <!-- THIS URL IS 404 (https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) --> den Rest Ihres App-Projekts einfügen.

## Die nächsten Schritte {#the-next-steps}

Weitere Informationen zur Struktur der App finden Sie unter [Erstellen und Bearbeiten der Apps mit der App-Konsole](/help/mobile/phonegap-apps-console.md).
