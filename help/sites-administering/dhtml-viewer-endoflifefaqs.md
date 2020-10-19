---
title: Häufig gestellte Fragen zur Einstellung der Unterstützung für DHTML-Viewer
seo-title: Häufig gestellte Fragen zur Einstellung der Unterstützung für DHTML-Viewer
description: Am 31. Januar 2014 wurde die DHTML-Viewer-Plattform von Scene7 offiziell eingestellt. Mit dieser Benachrichtigung erhalten Sie Antworten auf häufig gestellte Fragen, sodass Sie sich auf die Umstellung auf unsere neue HTML5-Viewer-Plattform vorbereiten können.
seo-description: Am 31. Januar 2014 wurde die DHTML-Viewer-Plattform von Scene7 offiziell eingestellt. Mit dieser Benachrichtigung erhalten Sie Antworten auf häufig gestellte Fragen, sodass Sie sich auf die Umstellung auf unsere neue HTML5-Viewer-Plattform vorbereiten können.
uuid: a78c03b3-6513-42e1-881f-6a9551659769
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: d94244ac-a5f6-4c95-ab8c-26b41d25863f
translation-type: tm+mt
source-git-commit: 283802809d665cd979e2f1a4fa969b6ddc491ed6
workflow-type: tm+mt
source-wordcount: '1665'
ht-degree: 98%

---


# Häufig gestellte Fragen zur Einstellung der Unterstützung für DHTML-Viewer{#dhtml-viewer-end-of-life-faqs}

Am 31. Januar 2014 wurde die DHTML-Viewer-Plattform von Scene7 offiziell eingestellt. Mit dieser Benachrichtigung erhalten Sie Antworten auf häufig gestellte Fragen, sodass Sie sich auf die Umstellung auf unsere neue HTML5-Viewer-Plattform vorbereiten können.

**Welche Änderungen gibt es?**

Mit Wirkung vom 31. Januar 2014 wird die DHTML-Viewer-Plattform nicht mehr offiziell von Adobe Scene7 unterstützt.

**Was bedeutet „Einstellung der Unterstützung“?**

Einstellung der Unterstützung bedeutet, dass Scene7 (1) der DHTML-Viewer-Plattform keine Funktionsverbesserungen mehr hinzufügt, (2) keine Fehlerbehebungen zur DHTML-Viewer-Plattform mehr an die DHTML-Viewer-Plattform richtet oder für diese veröffentlicht und (3) der Kundendienst keine Unterstützung mehr bei DHTML-bezogenen Viewer-Problemen oder -Fragen bereitstellt.

**Warum nimmt Scene7 diese Änderung vor?**

Die Webstandards entwickeln sich ständig weiter und DHTML ist eine ältere Webentwicklungstechnologie, die rasch durch HTML5 ersetzt wird. Die größte Beschränkung der DHTML-Plattform ist, dass sie kein so umfangreiches Erlebnis bieten kann, wie es HTML5 durchgängig, einfacher und Browser-übergreifend kann. Solche Beschränkungen umfassen beispielsweise eine mangelnde browserübergreifende Unterstützung für:

* Benutzerdefinierte Mauszeiger
* Abgerundete Ecken
* Animationen (wie Umblättern, einfacheres Zoomen)
* Effekte (wie Schatten, Leuchten)
* Umfassende Schriftartunterstützung
* Videowiedergabe ohne Plug-ins

Bei der Scene7-DHTML-Viewer-Plattform wurden sowohl die JSP-basierte Lösung als auch die Javascript-APIs nicht für die Nutzung von Multitouch- und Gestenfunktionen auf Mobilgeräten optimiert. Und obwohl 2011/Anfang 2012 veröffentlichte DHTML-Viewer für Mobilgeräte optimiert sind, war es mangels eines flexiblen auf SDK-Komponenten basierenden Entwicklungsframeworks schwierig, sie benutzerdefiniert anzupassen und zu warten.

Aufgrund dieser Beschränkungen von DHTML und der schnellen branchenweiten Verbreitung von HTML5 als Standard für sowohl Desktop- als auch Mobilgeräte wurde auch für Scene7 eine HTML5-basierte Viewer-Plattform beschlossen. Diese Investition bietet unseren Kunden eine solide Plattform, auf deren Grundlage sie umfangreichere, interaktivere Viewer entwickeln können, um Kunden sowohl über Desktop-, iOS- als auch Android-Geräte zu erreichen.

**Woher weiß ich, dass mein Viewer die DHTML-Plattform verwendet?**

Um zu bestimmen, ob der Viewer Ihres Unternehmens DHTML verwendet und daher von dieser Änderung betroffen ist, überprüfen Sie, ob:

1. Ihr Unternehmen einen standardmäßigen Scene7-Viewer aus dieser Tabelle verwendet, bei dem die „Viewer-Technologie“ als „DHTML“ angegeben ist:

   [https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Ihr Unternehmen einen Viewer verwendet, der basierend auf einem standardmäßigen Scene7-Viewer aus dieser Tabelle erstellt wurde, bei dem die „Viewer-Technologie“ als „DHTML“ angegeben ist:

   [https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Ihr Unternehmen einen benutzerdefinierten Viewer verwendet, der auf Grundlage der JSP-basierten DHTML-Lösung erstellt wurde:

   [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#JSP_Reference](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#JSP_Reference)

1. Ihr Unternehmen einen benutzerdefinierten Viewer verwendet, der auf Grundlage der Javascript-API erstellt wurde:

   [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#API_Reference](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#API_Reference)

1. Ihr Unternehmen einen benutzerdefinierten, mit der DHTML-Multi-Screen-Flyout-API erstellten Viewer verwendet:

   [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer)

1. Ihr Unternehmen einen benutzerdefinierten, mit der DHTML-Desktop-Flyout-API erstellten Viewer verwendet:

   [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Desktop_Flyout_Viewer](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Desktop_Flyout_Viewer)

1. Ihr Unternehmen eine Geräteerkennungsbibliothek verwendet, die Teil des DHTML-Viewer-Pakets ist:

   Überprüfen Sie, ob JS in Ihrem Code „sj_deviceDetect.js“ enthält.

   Dieser wurde durch den folgenden neuen JS-Geräteerkennungs-Code ersetzt: [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Detecting_devices_and_browsers](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Detecting_devices_and_browsers).

**Welche Viewer-Plattform ist der Ersatz?**

Der Ersatz für DHTML ist die Scene7-HTML5-Viewer-Plattform, die sich zusammensetzt aus:

* standardmäßigen HTML5-Viewern mit optimierten Interaktionen über zahlreiche Viewer-Typen hinweg, darunter Basic-Zoom, Flyout-Zoom, Bildsets, Mustersets, multidimensionale Rotation und gemischte Medien. Die vollständigen aktuellen Beispiele für diese Viewer finden Sie unter: [https://microsite.omniture.com/t2/help/de_DE/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/de_DE/s7/vlist/vlist.html)
* HTML5-Viewer-SDK, das die umfangreiche benutzerspezifische Anpassung von Adobe Scene7-Viewern für HTML5-unterstützte Sites und Geräte (wie iOS und Android) sowie größtmögliche Flexibilität und Kreativität zur Gestaltung des Erscheinungsbilds und der Interaktivität des Viewers ermöglicht. Der Vorteil wiederverwendbarer, leistungsoptimierter Komponenten senkt die Gesamtkosten der Viewer-Entwicklung und beschleunigt die benutzerdefinierte Entwicklung.

**Wann wird die HTML5-Viewer-Plattform über die Funktionen verfügen, die ich für die Umstellung von der DHTML-Viewer-Plattform benötige?**

Scene7 hat das erste HTML5-Viewer-SDK im Herbst 2011 zusammen mit Version 5.5 veröffentlicht. Seitdem haben wir die Plattform um zahlreiche Funktionen ergänzt und die Unterstützung auf immer mehr Arten von Viewern ausgeweitet. Im Hinblick auf die gängigsten Viewer-Anforderungen verfügt die HTML5-Viewer-Plattform mit hoher Wahrscheinlichkeit bereits über die benötigten Funktionen für eine sofortige Migration. Und wir investieren mit vierteljährlichen Versionen weiterhin intensiv in diese Viewer-Plattform.

Um zu bestimmen, ob Ihre Viewer-Anforderungen heute von der HTML5-Viewer-Plattform erfüllt werden, sehen Sie in der folgenden Dokumentation nach:

[https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#About_HTML5_Viewers](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#About_HTML5_Viewers) (zu Funktionen und Möglichkeiten zur benutzerspezifischen Anpassung standardmäßiger Viewer)

[https://help.adobe.com/de_DE/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/de_DE/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html) (für den Zugriff auf die SDK-API-Dokumentation)

Wenn Sie nach wie vor unsicher sind, ob das HTML5-Viewer-SDK Ihre Anforderungen erfüllen kann, wenden Sie sich an unser Professional Services-Team.

**Wie stelle ich meine Viewer auf die HTML5-Plattform um?**

Um Ihre Viewer auf die HTML5-Plattform umzustellen, bietet Scene7 die folgenden Optionen:

1. Verwenden Sie einen der standardmäßigen HTML5-Viewer von Scene7, die hier zu finden sind: [https://microsite.omniture.com/t2/help/de_DE/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/de_DE/s7/vlist/vlist.html)
1. Konfigurieren Sie einen der standardmäßigen Scene7-HTML5-Viewer gemäß der SPS-Anwendungseinstellungen. Dies ermöglicht Ihnen die Anpassung von Viewer-Größe, Übergängen, Zoomverhalten usw.: [https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html](https://help.adobe.com/de_DE/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html)
1. Passen Sie das Erscheinungsbild der standardmäßigen HTML5-Viewer von Scene7 benutzerdefiniert an, indem Sie CSS modifizieren, um das visuelle Design wie die Schaltflächengestaltung, die Positionierungen, die Transparenz, Hintergrundfarben usw. zu ändern: [https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Customizing_HTML5_Viewers](https://microsite.omniture.com/t2/help/de_DE/s7/viewers_ref/index.html#Customizing_HTML5_Viewers)
1. Erstellen Sie von Grund auf einen benutzerdefinierten HTML5-Viewer mithilfe des SDK, das hier heruntergeladen werden kann: [https://help.adobe.com/de_DE/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/de_DE/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html). Sie können mit Professional Services interagieren, um einen benutzerdefinierten Viewer zu erstellen, oder Ihr Web-Entwicklungs-Team kann einen solchen Viewer entwickeln.

**Wie sieht es mit Browsern aus, die HTML5 nicht unterstützen?**

HTML5 wird von vielen Mobilgeräten und Webbrowsern unterstützt und seine Bedeutung nimmt weiterhin zu. Obwohl HTML5 aktuell nicht von Internet Explorer 8 oder früher unterstützt wird, hat Scene7 unsere HTML5-Viewer-Plattform so gestaltet, dass sie sogar von IE7 und IE8 unterstützt wird. Mit der HTML5-Viewer-Plattform von Scene7 können Sie die überwältigende Mehrheit der Desktop- und Mobilgerätebenutzer über eine einzige Entwicklungsplattform erreichen.

Die aktuellen Systemanforderungen der HTML5-SDK-Version 2.2.1 sind:

* Microsoft® Windows® XP oder höher, Macintosh® OS X 10.6 oder höher
* Firefox 17, Safari 5.1, Chrome 23, Internet Explorer 7 oder höher
* iOS 3.2.2 oder höher
* Zertifiziert für iPhone 3 oder höher und iPad 1 oder höher (native Browser)
* Android OS 2.2 oder höher

Zur Überprüfung, ob Ihr Browser mit unserer HTML5-Viewer-Plattform kompatibel ist, starten Sie den folgenden Beispiel-Viewer:

[https://s7d1.scene7.com/s7viewers/html5/flyout.html?asset=Scene7SharedAssets/Sample%20Image](https://s7d1.scene7.com/s7viewers/html5/flyout.html?asset=Scene7SharedAssets/Sample%20Image)

Wenn Sie das vergrößerte Bild sehen, indem Sie mit dem Mauszeiger oder Ihrem Finger über das Hauptbild fahren, handelt es sich um einen unterstützten Browser/ein unterstütztes Gerät.

**Welche Optionen habe ich, wenn ich meinen vorhandenen DHTML-Viewer weiter bei der Produktion einsetzen möchte?**

Auch wenn Sie den DHTML-Viewer weiterhin bei der Produktion einsetzen können, ist zu beachten, dass seit dem 31. Januar 2014 keinerlei Optimierungen, Fehlerbehebungen oder Kundenunterstützung mehr hierfür bereitgestellt werden. Daher raten wir allen Kunden dringend, eine Migration auf unsere solidere HTML5-Viewer-Plattform vorzunehmen. Wenn Ihre geschäftliche Situation jedoch eine solche Migration bis zum Datum der Einstellung der Unterstützung verhindert, können Sie einen Vertrag mit Professional Services schließen, um den unterstützten Wartungszeitraum zu verlängern. Weitere Informationen erhalten Sie von Ihrem Kundenbetreuer.

**An wen kann ich mich wenden, um weitere Informationen zu erhalten?**

Wenn diese FAQ nicht alle Ihre Fragen beantwortet haben, [verwenden Sie die Admin Console, um einen Supportfall](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) zu erstellen, oder wenden Sie sich an Ihren Kundenbetreuer.
