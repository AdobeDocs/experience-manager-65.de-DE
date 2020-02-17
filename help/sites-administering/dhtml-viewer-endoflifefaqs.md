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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Häufig gestellte Fragen zur Einstellung der Unterstützung für DHTML-Viewer{#dhtml-viewer-end-of-life-faqs}

Am 31. Januar 2014 wurde die DHTML-Viewer-Plattform von Scene7 offiziell eingestellt. Mit dieser Benachrichtigung erhalten Sie Antworten auf häufig gestellte Fragen, sodass Sie sich auf die Umstellung auf unsere neue HTML5-Viewer-Plattform vorbereiten können.

**Welche Änderungen gibt es?**

Mit Wirkung vom 31. Januar 2014 wird die DHTML-Viewer-Plattform nicht mehr offiziell von Adobe Scene7 unterstützt.

**Was bedeutet Lebensende?**

Einstellung der Unterstützung bedeutet, dass Scene7 (1) der DHTML-Viewer-Plattform keine Funktionsverbesserungen mehr hinzufügt, (2) keine Fehlerbehebungen zur DHTML-Viewer-Plattform mehr an die DHTML-Viewer-Plattform richtet oder für diese veröffentlicht und (3) der Kundendienst keine Unterstützung mehr bei DHTML-bezogenen Viewer-Problemen oder -Fragen bereitstellt.

**Warum nimmt Scene7 diese Änderung vor?**

Die Webstandards entwickeln sich ständig weiter und DHTML ist eine ältere Webentwicklungstechnologie, die rasch durch HTML5 ersetzt wird. Die größte Beschränkung der DHTML-Plattform ist, dass sie kein so umfangreiches Erlebnis bieten kann, wie es HTML5 durchgängig, einfacher und browserübergreifend kann. Solche Beschränkungen umfassen beispielsweise eine mangelnde browserübergreifende Unterstützung für:

* Benutzerdefinierte Mauszeiger
* Abgerundete Ecken
* Animationen (wie Umblättern, einfacheres Zoomen)
* Effekte (wie Schatten, Leuchten)
* Umfassende Schriftartunterstützung
* Videowiedergabe ohne Plug-ins

Bei der Scene7-DHTML-Viewer-Plattform wurden sowohl die JSP-basierte Lösung als auch die Javascript-APIs nicht für die Nutzung von Multitouch- und Gestenfunktionen auf Mobilgeräten optimiert. Und obwohl 2011/Anfang 2012 veröffentlichte DHTML-Viewer für Mobilgeräte optimiert sind, war es mangels eines flexiblen auf SDK-Komponenten basierenden Entwicklungsframeworks schwierig, sie benutzerdefiniert anzupassen und zu warten.

Aufgrund dieser Einschränkungen bei DHTML und der schnellen Branchenausübung mit HTML5 als neuem Standard für Desktop- und Mobilgeräte hat Scene7 beschlossen, in eine HTML5-basierte Viewer-Plattform zu investieren. Diese Investition bietet unseren Kunden eine solide Plattform, auf deren Grundlage sie umfangreichere, interaktivere Viewer entwickeln können, um Kunden sowohl über Desktop-, iOS- als auch Android-Geräte zu erreichen.

**Woher weiß ich, dass mein Viewer die DHTML-Plattform verwendet?**

Um zu bestimmen, ob der Viewer Ihres Unternehmens DHTML verwendet und daher von dieser Änderung betroffen ist, überprüfen Sie, ob:

1. Ihr Unternehmen verwendet einen standardmäßigen Scene7-Viewer, der in der folgenden Tabelle aufgeführt ist, in der &quot;Viewer-Technologie&quot;als &quot;DHTML&quot;gekennzeichnet ist:

   [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Ihr Unternehmen verwendet einen Viewer, der als neue Vorgabe basierend auf einem standardmäßigen Scene7-Viewer in der folgenden Tabelle erstellt wurde, wobei die &quot;Viewer-Technologie&quot;als &quot;DHTML&quot;gekennzeichnet ist:

   [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html#WS1c46793299cf21d77e926d1613177f0a020-8000)

1. Ihr Unternehmen einen benutzerdefinierten Viewer verwendet, der auf Grundlage der JSP-basierten DHTML-Lösung erstellt wurde:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#JSP_Reference](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#JSP_Reference)

1. Ihr Unternehmen verwendet einen benutzerdefinierten Viewer, der über die JavaScript-API erstellt wurde:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#API_Reference](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#API_Reference)

1. Ihr Unternehmen verwendet einen benutzerdefinierten Viewer, der mit der DHTML-Flyout-API für mehrere Bildschirme erstellt wurde:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Multi-screen_Flyout_Viewer)

1. Ihr Unternehmen verwendet einen benutzerdefinierten Viewer, der mit der DHTML Desktop Flyout API erstellt wurde:

   [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Desktop_Flyout_Viewer](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Desktop_Flyout_Viewer)

1. Ihr Unternehmen eine Geräteerkennungsbibliothek verwendet, die Teil des DHTML-Viewer-Pakets ist:

   Überprüfen Sie, ob JS in Ihrem Code „sj_deviceDetect.js“ enthält.

   This has been replaced by new JS device detection code here: [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Detecting_devices_and_browsers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Detecting_devices_and_browsers) .

**Welche Viewer-Plattform ist der Ersatz?**

Der Ersatz für DHTML ist die Scene7-HTML5-Viewer-Plattform, die sich zusammensetzt aus:

* standardmäßigen HTML5-Viewern mit optimierten Interaktionen über zahlreiche Viewer-Typen hinweg, darunter Basic-Zoom, Flyout-Zoom, Bildsets, Mustersets, multidimensionale Rotation und gemischte Medien. For full up-to-date examples of these viewers, please refer to: [https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html)
* HTML5-Viewer-SDK, das die umfangreiche benutzerspezifische Anpassung von Adobe Scene7-Viewern für HTML5-unterstützte Sites und Geräte (wie iOS und Android) sowie größtmögliche Flexibilität und Kreativität zur Gestaltung des Erscheinungsbilds und der Interaktivität des Viewers ermöglicht. Der Vorteil wiederverwendbarer, leistungsoptimierter Komponenten senkt die Gesamtkosten der Viewer-Entwicklung und beschleunigt die benutzerdefinierte Entwicklung.

**Wann wird die HTML5-Viewer-Plattform über die Funktionen verfügen, die ich für die Umstellung von der DHTML-Viewer-Plattform benötige?**

Scene7 hat das erste HTML5-Viewer-SDK im Herbst 2011 zusammen mit Version 5.5 veröffentlicht. Seitdem haben wir die Plattform um zahlreiche Funktionen ergänzt und die Unterstützung auf immer mehr Arten von Viewern ausgeweitet. Im Hinblick auf die gängigsten Viewer-Anforderungen verfügt die HTML5-Viewer-Plattform mit hoher Wahrscheinlichkeit bereits über die benötigten Funktionen für eine sofortige Migration. Und wir investieren mit vierteljährlichen Versionen weiterhin intensiv in diese Viewer-Plattform.

Um zu bestimmen, ob Ihre Viewer-Anforderungen heute von der HTML5-Viewer-Plattform erfüllt werden, sehen Sie in der folgenden Dokumentation nach:

[https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#About_HTML5_Viewers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#About_HTML5_Viewers) (für vordefinierte Viewer-Funktionen und Anpassungsfunktionen)

[https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html) (für den Zugriff auf die SDK-API-Dokumentation)

Wenn Sie nach wie vor unsicher sind, ob das HTML5-Viewer-SDK Ihre Anforderungen erfüllen kann, wenden Sie sich an unser Professional Services-Team.

**Wie stelle ich meine Viewer auf die HTML5-Plattform um?**

Um Ihre Viewer auf die HTML5-Plattform umzustellen, bietet Scene7 die folgenden Optionen:

1. Use one of the Scene7 out-of-box HTML5 viewers, examples of which can be found here: [https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html](https://microsite.omniture.com/t2/help/en_US/s7/vlist/vlist.html)
1. Konfigurieren Sie einen der standardmäßigen HTML5-Viewer von Scene7 unter dem Setup der SPS-Anwendung. This will allow you to customize certain behavior such as viewer size, transitions, zoom behavior, etc: [https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html](https://help.adobe.com/en_US/scene7/using/WS6E593DEA-7D81-4cd6-84B0-85E8BB274176.html)
1. Customize look and feel of the Scene7 out-of-box HTML5 viewers by modifying CSS to change visual design such as button artwork, placement, transparency, background colors, etc: [https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Customizing_HTML5_Viewers](https://microsite.omniture.com/t2/help/en_US/s7/viewers_ref/index.html#Customizing_HTML5_Viewers)
1. Create a custom HTML5 viewer from scratch using the SDK which can be downloaded here: [https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html](https://help.adobe.com/en_US/scene7/using/WSd4272150f67705c11b002eec12fcba4dee6-8000.html). Sie können sich mit professionellen Diensten in Verbindung setzen, um den benutzerdefinierten Viewer zu erstellen, oder Sie können ihn von Ihrem eigenen Webentwicklungsteam erstellen lassen.

**Wie sieht es mit Browsern aus, die HTML5 nicht unterstützen?**

HTML5 wird von vielen Mobilgeräten und Webbrowsern unterstützt und seine Bedeutung nimmt weiterhin zu. Obwohl HTML5 aktuell nicht von Internet Explorer 8 oder früher unterstützt, hat Scene7 unsere HTML5-Viewer-Plattform so gestaltet, dass sie sogar von IE7 und IE8 unterstützt wird. Mit der HTML5-Viewer-Plattform von Scene7 können Sie die überwältigende Mehrheit der Desktop- und Mobilgerätebenutzer über eine einzige Entwicklungsplattform erreichen.

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

Obwohl Sie mit DHTML-basierten Viewern weiterhin live arbeiten können, ist es wichtig zu beachten, dass es nach dem 31. Januar 2014 keine Erweiterungen, Fehlerbehebungen und Kundenunterstützung mehr geben wird. Daher raten wir allen Kunden dringen, eine Migration auf unsere solidere HTML5-Viewer-Plattform vorzunehmen. . Wenn Ihre geschäftliche Situation jedoch eine solche Migration bis zum Datum der Einstellung der Unterstützung verhindert, können Sie einen Vertrag mit Professional Services schließen, um den unterstützten Wartungszeitraum zu verlängern. Weitere Informationen erhalten Sie von Ihrem Kundenbetreuer.

**An wen kann ich mich wenden, um weitere Informationen zu erhalten?**

Falls nicht all Ihre Fragen durch diese FAQ beantwortet werden konnten, wenden Sie sich an den Support ([s7support@adobe.com](mailto:s7support@adobe.com)) oder Ihren Adobe-Kundenbetreuer.
