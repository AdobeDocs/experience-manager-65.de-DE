---
title: Interaktive Bilder
description: Erfahren Sie, wie Sie in Dynamic Media mit interaktiven Bildern arbeiten
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: Interactive Images
role: User, Admin
exl-id: 8a609024-e9e6-4805-8306-48d095110eb6
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '4130'
ht-degree: 98%

---

# Interaktive Bilder{#interactive-images}

Sie können aus statischen Bildern ganz einfach ansprechende Erlebnisse für Kunden machen, indem Sie Hotspots mit Shopping-Funktion auf ein Bild ziehen und dort ablegen. Hotspots mit Shopping-Funktion kombinieren zusätzliche Informationen über ein Produkt oder eine Dienstleistung mit einer direkten POS-Funktion, wie „In den Einkaufswagen legen“ oder „Kaufen“. Kundinnen und Kunden können diese Hotspots auswählen und direkt eine Verbindung mit dem Produkt oder Service herstellen, es zum Warenkorb hinzufügen oder es mit einer Webseite verknüpfen. Direkte Erlebnisse wie diese erhöhen Kundeninteraktionen und Konversionen auf Ihrer Website.

Die folgende Abbildung zeigt ein Banner mit Shopping-Funktion mit einem Schnellansichts-Popup. Benutzerinnen und Benutzer können die Schnellansicht aktivieren, indem sie den Kreis oder „Hotspot“ des Modells auswählen.

![chlimage_1-152](assets/chlimage_1-368.png)

Zeigen Sie die interaktiven Bilder in Aktion auf der oben gezeigten Webseite an, indem Sie Folgendes aufrufen:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html?lang=de)

## Sehen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Sehen Sie sich eine exemplarische Vorgehensweise dazu an, [wie interaktive Bildbanner erstellt werden](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 Minuten und 33 Sekunden). Außerdem erfahren Sie, wie Sie interaktive Bild-Banner in der Vorschau betrachten, bearbeiten und bereitstellen können.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen den schnellen Einstieg in die Arbeit mit interaktiven Bildern in Adobe Experience Manager Assets ermöglichen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Es enthält ein kurzes Tutorial, das auf dem folgenden Webseitenbeispiel basiert, dem noch keine interaktiven Bilder hinzugefügt wurden:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Die Beispiele veranschaulichen die Schritte zur Integration interaktiver Videos auf Ihrer Website.

Schritte zum Erstellen interaktiver Bilder:

1. **(Optional) Ermitteln von Hotspot-Variablen**: Wenn Sie Experience Manager Assets und Dynamic Media eigenständig verwenden, ermitteln Sie zunächst die dynamischen Variablen, die in Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden. Anschließend können Sie beim Erstellen des interaktiven Bildes Hotspot-Daten eingeben. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).
Wenn Sie jedoch Adobe Experience Manager Sites, Adobe Experience Manager eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.
Siehe [E-Commerce-Konzepte in Experience Manager Assets](/help/commerce/cif-classic/administering/concepts.md).

1. **(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder**: Passen Sie das Grafikbild an, das zur Darstellung von Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.
Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bildbanners**: Laden Sie Bildbanner hoch, die Sie interaktiv machen möchten.
Siehe [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bildbanner**: Fügen Sie einem Bildbanner einen oder mehrere Hotspots hinzu und weisen Sie jedem eine Aktion wie beispielsweise einen Hyperlink, eine Schnellansicht oder ein Experience Fragment zu. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.

   * Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
   * Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
   * Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website**: Wenn Sie Experience Manager Sites, eCommerce oder beides verwenden, können Sie das interaktive Bild in Experience Manager zu einer Web-Seite hinzufügen. Ziehen Sie die interaktive Medienkomponente auf die Seite. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

   Wenn Sie lediglich Experience Manager Assets und Dynamic Media verwenden, müssen Sie den Einbettungs-Code auf Ihrer Website kopieren und in Ihre vorhandene Schnellansicht integrieren. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   Wenn Sie einen Drittanbieter-WCM (Web Content Manager) verwenden, müssen Sie das neue interaktive Video in die vorhandene Schnellansichtsimplementierung integrieren, die auf Ihrer Website verwendet wird. Siehe [Integrieren eines interaktiven Bildes in einer Schnellansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Ermitteln von Hotspot-Variablen {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie können das Bild durch Auslösen von Schnellansichten in ein interaktives Bild umwandeln.
>* Ihre Experience Manager-Implementierung verwendet *kein* E-Commerce-Integrations-Framework, um Produktdaten aus einer E-Commerce-Lösung wie IBM® WebSphere® Commerce, Elastic Path, Hybris oder Intershop in Experience Manager abzurufen. Siehe [E-Commerce-Konzepte in Experience Manager Assets](/help/commerce/cif-classic/administering/concepts.md).
>
Wenn Ihre Experience Manager-Implementierung E-Commerce nutzt, können Sie diese Aufgabe überspringen und mit der nächsten Aufgabe fortfahren.

Ermitteln Sie zunächst die dynamischen Variablen, die von Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie einem Bannerbild in Experience Manager Assets Hotspots hinzufügen, müssen Sie jedem Hotspot eine SKU (Stock Keeping Unit, Bestandseinheit) und optional zusätzliche Variablen zuweisen. Anhand dieser Hotspot-Variablen werden Hotspots später mit Schnellansichtsinhalten abgeglichen.

Es ist wichtig, die Anzahl und den Typ der Variablen, denen Hotspot- oder Imagemap-Daten zugewiesen werden sollen, korrekt zu ermitteln. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal ist es ausreichend, die IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Sie wissen wahrscheinlich, welche Daten mindestens erforderlich sind, um eine Schnellansicht im System zu identifizieren. Es jedoch auch möglich, einfach das vorhandene Verhalten des Frontend-Codes zu analysieren.

Bei den meisten Schnellansichtsimplementierungen wird das folgende Muster verwendet:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Dazu kann er beispielsweise auf die Schaltfläche „Schnellansicht“ klicken.
* Die Website sendet eine Ajax-Anfrage an das Backend, um bei Bedarf die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Web-Seite vorbereitet zu werden.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Im Anschluss sollten verschiedene Bereiche der bestehenden Website besucht werden, in denen die Schnellansichtsfunktion implementiert ist. Lösen Sie dann die Schnellansicht aus und erfassen Sie die Ajax-URL, die von der Website zum Laden der Schnellansichtsdaten oder -inhalte gesendet wird.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Im Folgenden finden Sie einige Beispiele für Webbrowser, die Web-Inspektoren beinhalten:

* Wenn Sie alle ausgehenden HTTP-Anfragen in Google Chrome anzeigen möchten, drücken Sie F12, um den Bereich für Entwickler-Tools zu öffnen; wählen Sie dann die Registerkarte „Netzwerk“ aus.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und wählen Sie dann die Registerkarte „Netzwerk“ aus.

* In Firefox können Sie entweder durch Drücken von F12 das Firebug-Plug-in aktivieren und dessen Registerkarte „Netzwerk“ verwenden oder das integrierte Inspektor-Tool und dessen Registerkarte „Netzwerk“ einsetzen.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Arbeitsbereich mit Entwickler-Tools zu öffnen, und wählen Sie dann die Registerkarte „Inspektor“ aus.

Wenn die Netzwerküberwachung im Browser aktiviert ist, lösen Sie die Schnellansicht auf der Seite aus.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. In den meisten Fällen werden beim Auslösen der Schnellansicht zahlreiche Anfragen an den Server gesendet. In der Regel ist die Schnellansichts-Ajax-URL die erste URL in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/html`, `text/xml` oder `text/javascript`.

Während dieses Vorgangs müssen Sie verschiedene Bereiche der Website mit verschiedenen Produktkategorien und -typen besuchen. Grund dafür ist, dass Schnellansichts-URLs Bestandteile aufweisen, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert das einzige Datenelement, das Sie benötigen, um dem Bannerbild Hotspots hinzuzufügen.

In komplexen Fällen hat die Schnellansichts-URL allerdings mehrere verschiedene Elemente zusätzlich zur SKU, wie Kategorie-ID, Farb-Code usw. In diesen Fällen ist jedes Element eine separate Variable in der Hotspot-Datendefinition der Funktion für interaktive Bilder mit Shopping-Funktion in Experience Manager Assets.

Nachfolgend finden Sie einige Beispiele für Schnellansichts-URLs und die resultierenden Hotspot-Variablen:

<table>
  <tbody>
  <tr>
    <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters „productId=“ und ist offensichtlich ein SKU-Wert. Daher müssen nur die SKU-Felder der Hotspots mit Werten wie <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong> oder <strong><code>1898294</code></strong> ausgefüllt werden.</p> </td>
  </tr>
  <tr>
    <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Der variable Teil befindet sich im letzten Abschnitt des Pfads und wird zum SKU-Wert der Hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs enthalten Folgendes:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. Die SKU wird im <code>prodId</code> Parameter gespeichert, während die Kategorie-ID<code></code> im <code>category=</code> Parameter gespeichert wird.</p> <p>Im eigentlichen Sinne handelt es sich bei Hotspot-Definitionen um Paare. Also einen SKU-Wert und eine zusätzliche Variable mit dem Namen <code>categoryId</code>. Die resultierenden Paare lauten wie folgt:</p>
    <ul>
      <li><p>Die SKU lautet <strong><code>305466</code></strong> und <code>categoryId</code> lautet <code>1100004</code>.</p> </li>
      <li><p>Die SKU lautet <strong><code>310181</code></strong> und <code>categoryId</code> lautet <strong><code>1100004</code></strong>.</p> </li>
      <li><p>Die SKU lautet <strong><code>308706</code></strong> und <code>categoryId</code> lautet <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Beispiel**

Sie können den in den drei oben genannten Beispielen verwendeten Ansatz auch auf die Demo-Web-Seite anwenden:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Die Demo-Web-Seite enthält mehrere Produktminiaturen. Jede davon verfügt über eine Schnellansichts-Schaltfläche mit der Bezeichnung „Mehr anzeigen“. Wählen Sie bei aktiviertem Debugging-Tool des Webbrowsers jede einzelne Schaltfläche aus und notieren Sie sich die aufgezeichneten Schnellansichts-URLs. Nachdem Sie alle vier Produktschnellansichten auf der Seite aktiviert haben, verfügen Sie über die folgende Liste mit den an das Backend gesendeten Schnellansichtsanforderungen:

* `/datafeed/Male-Windbreaker.json`
* `/datafeed/Male-SimpleHenley.json`
* `/datafeed/Male-CamoPullover.json`
* `/datafeed/Female-QuiltedDownJacket.json`

Wenn Sie die Server-Aufrufe betrachten, sehen Sie, dass nur der Anfragepfad produktspezifische Informationen enthält. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist „Männlich“ oder „Weiblich“. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, z. B. CamoPullover. Sie können davon ausgehen, dass dies die Produkt-SKU ist.

Mit diesen Informationen hat die gesamte Schnellansichts-URL das folgende Muster:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Jetzt können Sie ein Bildbanner hochladen und diesem Hotspots hinzufügen, indem Sie die Funktion für interaktive Bilder mit Shopping-Funktion in Experience Manager Assets verwenden.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder {#optional-creating-an-interactive-image-viewer-preset}

Sie können die standardmäßige vorkonfigurierte Viewer-Vorgabe für interaktive Bilder mit dem Namen `Shoppable_Banner` verwenden, die in Experience Manager Assets integriert ist. Sie können auch eine eigene benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Erscheinungsbild von Hotspots auf dem Bildbanner bestimmen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

Nachdem Sie die Viewer-Vorgabe gespeichert haben, wird sie automatisch auf der Seite mit der Liste der „Viewer-Vorgaben“ in Experience Manager Assets aktiviert (eingeschaltet). Diese Funktionalität bedeutet, dass sie in der interaktiven Medienkomponente sowie dann sichtbar ist, wenn Sie ein Asset anzeigen. Um jedoch ein interaktives Banner mit dieser Viewer-Vorgabe *bereitzustellen*, müssen Sie auch Ihre Viewer-Vorgabe *veröffentlichen*. Diese Regel gilt für benutzerdefinierte oder vordefinierte Viewer-Vorgaben.

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder:**

1. Navigieren Sie links in der Leiste zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer-Vorgaben]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „Neue Viewer-Vorgabe“ einen Namen ein, um die Viewer-Vorgabe für interaktive Banner zu beschreiben.

   Der Titel wird nach dem Speichern in der Liste „Viewer-Vorgaben“ angezeigt.

1. Wählen Sie im Pulldown-Menü „Rich-Media-Typ“ die Option **[!UICONTROL Interaktives Bild]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ die Registerkarte **[!UICONTROL Erscheinungsbild]** aus.
1. Führen Sie einen der folgenden Schritte aus:

   * Um ein eigenes Hotspot-Bild hochzuladen, das Sie für Bilder verwenden möchten, wählen Sie das Symbol für die Asset-Auswahl aus. Navigieren Sie auf der Seite „Inhalt auswählen“ zum gewünschten Hotspot-Bild, wählen Sie es aus und aktivieren Sie oben rechts das Häkchen.
   * Um ein vordefiniertes Hotspot-Bild auszuwählen, tippen Sie auf das Symbol für die Hotspot-Galerie. Wählen Sie in der Palette der Hotspot-Galerie das gewünschte Hotspot-Bild aus.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

   Stellen Sie sicher, die neue Viewer-Vorgabe zu veröffentlichen.

   Siehe [Veröffentlichen von hinzugefügten Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

   Sie sind nun bereit, ein Bildbanner hochzuladen.

## Laden Sie ein Bildbanner hoch {#uploading-an-image-banner}

Wenn Sie die gewünschten Bilder bereits hochgeladen haben, fahren Sie mit dem nächsten Schritt fort: [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).

**So laden Sie ein Bildbanner hoch:**

1. Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Informationen hierzu finden Sie unter [Hochladen von Assets](/help/assets/manage-assets.md#uploading-assets).

   Sie können jetzt dem Bildbanner Hotspots hinzuzufügen. Anweisungen dazu finden Sie in der folgenden Aufgabe.

## Hinzufügen von Hotspots zu einem Bildbanner {#adding-hotspots-to-an-image-banner}

Sie können einem Bildbanner Hotspots hinzufügen, indem Sie den Editor auf der Seite „Hotspot-Verwaltung“ verwenden.

Beim Hinzufügen von Hotspots können Sie sie als eine Schnellansichts-Popup-Anzeige, als einen Hyperlink oder als ein Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
Im interaktiven Bild werden die Tools zur Freigabe in Social Media nicht unterstützt, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.

Wenn Sie die Erstellung des interaktiven Bildes abgeschlossen haben, können Sie eine Vorschau anzeigen, um das interaktive Bild aus der Perspektive der Kunden zu betrachten.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
Wenn Sie einem Bild in einem interaktiven Bild oder einem Karussell-Banner Hotspots hinzufügen, werden die Hotspot-Informationen am selben Metadaten-Speicherort gespeichert. Der Speicherort ist relativ zur Position des Bildes, unabhängig davon, ob es sich um ein interaktives Bild oder ein Karussell-Banner handelt. Das bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.
>
Karussell-Banner unterstützen Imagemaps auf Bildern, die auch Hotspots enthalten können. Interaktive Bilder nicht. Dies sollten Sie beachten, wenn Sie ein interaktives Bild oder ein Karussell-Banner mit demselben Bild erstellen möchten. Stattdessen können Sie separate Kopien desselben Bildes verwenden, um interaktive Bilder und Karussell-Banner zu erstellen.
>
Siehe auch [Karussellbanner](/help/assets/carousel-banners.md).

>[!NOTE]
>
Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu:**

1. Navigieren Sie in der Assets-Ansicht zu dem Bildbanner, das Sie interaktiv machen möchten.
1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über das Bild und klicken Sie dann auf **[!UICONTROL Auswählen]** (Häkchensymbol). Wählen Sie in der Symbolleiste die Option **[!UICONTROL Bearbeiten]** aus.

   * Bewegen Sie den Mauszeiger über dem Bild und wählen Sie dann **[!UICONTROL Mehr Aktionen]** (Ellipsensymbol) **[!UICONTROL Bearbeiten]** aus.

   * Wählen Sie das Bild aus, um es auf der Seite Detailansicht zu öffnen. Wählen Sie in der Symbolleiste die Option **[!UICONTROL Bearbeiten]** aus.

1. Wählen Sie links oben auf der Seite die Option **[!UICONTROL Hotspot hinzufügen]** (Fingernensymbol), um die Hotspot-Verwaltungsseite zu öffnen.
1. Wählen Sie in der linken oberen Ecke der Seite **[!UICONTROL Hotspot]** aus.

   1. Wählen Sie in der rechten oberen Ecke der Seite „Hotspot-Verwaltung“ **[!UICONTROL Hotspot]** aus.
   1. Wählen Sie im Bild die Stelle aus, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen.
   1. Fügen Sie bei Bedarf weitere Hotspots hinzu, indem Sie die Schritte a und b wiederholen.
   1. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn auf dem Bild aus und wählen dann **[!UICONTROL Löschen]** (Papierkorb-Symbol) unter der Überschrift **[!UICONTROL Hotspots]** aus.

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots ein. Dieser Name wird auch in der Dropdown-Liste „Ausgewählte Hotspots“ angezeigt.
1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie **[!UICONTROL Schnellansicht]** aus.

      * Wenn Sie Experience Manager Sites- oder E-Commerce-Kunde sind, wählen Sie das Produktauswahlsymbol (Lupe) aus, um die Seite „Produkt wählen“ zu öffnen. Wählen Sie das Produkt aus, das Sie verwenden möchten, und wählen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Auswählen]**, um zur Seite „Hotspot-Verwaltung“ zurückzukehren.
      * Wenn Sie *kein* Experience Manager Sites- oder E-Commerce-Kunde sind, gehen Sie wie folgt vor:

         * Siehe [Identifizieren von Hotspot-Variablen](#optional-identifying-hotspot-variables); Sie müssen diese Variablen definieren.
         * Geben Sie anschließend manuell den SKU-Wert ein. Geben Sie im Textfeld „SKU-Wert“ die Bestandseinheit (Stock Keeping Unit, SKU) des Produkts ein. Hierbei handelt es sich um eine eindeutige Kennung für die jeweiligen von Ihnen angebotenen Produkte oder Services. Der variable Teil der Schnellansichtsvorlage wird automatisch mit dem eingegebenen SKU-Wert ausgefüllt, sodass das System den Hotspot, der ausgewählt wird, mit der Schnellansicht einer bestimmten SKU verbinden kann.
         * (Optional) Wenn andere Variablen in der Schnellansicht vorhanden sind, die Sie verwenden müssen, um ein Produkt weitergehend zu identifizieren, wählen Sie **[!UICONTROL Generische Variable hinzufügen]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Males` eine hinzugefügte Variable.

   * Wählen Sie **[!UICONTROL Hyperlink]** aus.

      * Wenn Sie Experience Manager Sites-Kunde sind, klicken Sie auf das Symbol zur Website-Auswahl (Ordner), um zu einer URL zu gehen. Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
      * Wenn Sie Einzelkunde sind, geben Sie im Textfeld „HREF“ den vollständigen URL-Pfad zu einer verknüpften Web-Seite an.

   Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md).

   * Wählen Sie **[!UICONTROL Experience Fragment]** aus.

      * Wenn Sie AEM Sites-Kunde sind, klicken Sie auf das Suchsymbol (Lupe), um die Seite „Experience Fragment“ zu öffnen. Wählen Sie das Experience Fragment aus, das Sie verwenden möchten, und wählen Sie dann **[!UICONTROL Auswählen]** in der rechten oberen Ecke der Seite, um zur Seite „Hotspot-Verwaltung“ zurückzukehren.
Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

      * Legen Sie die Breite und Höhe des Experience Fragment fest, so wie es im Banner angezeigt werden soll.

        >[!NOTE]
        >
        Im interaktiven Bild werden die Tools zur Freigabe in Social Media nicht unterstützt, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

1. Wählen Sie **[!UICONTROL Speichern]** aus, um Ihre Änderungen zu speichern, und kehren Sie zur Seite „Durchsuchen“ zurück.
1. Veröffentlichen Sie das interaktive Bild. Durch eine Veröffentlichung kann das Banner über die Cloud bereitgestellt werden. Außerdem wird ein Einbettungs-Code zur Integration auf externen Websites generiert.

   Siehe [Veröffentlichen von Assets](/help/assets/manage-assets.md#publishing-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zuzuschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder {#optional-previewing-interactive-images}

Mithilfe der Vorschau können Sie eine Darstellung des interaktiven Bildes aus der Perspektive der Kundschaft anzeigen und die Hotspots des Bildes testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau für interaktive Bilder an:**

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, und wählen Sie es aus, um es in der Vorschau zu öffnen.
1. Wählen Sie in der linken oberen Ecke der Seite „Vorschau“ in der Dropdown-Liste „Inhalt“ **[!UICONTROL Viewer]** aus.
1. Wählen Sie in der Liste „Viewer“ **[!UICONTROL Shoppable_Banner]** oder den Namen der von Ihnen erstellten Viewer-Vorgabe für interaktive Bilder aus.
1. Wählen Sie Hotspots auf dem Bild aus, um die zugehörigen Aktionen zu testen.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt auf Ihrer Website hinzufügen.

Wenn Sie Experience Manager Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

Wenn Sie nur Experience Manager Assets verwenden, können Sie das interaktive Bild manuell zu Ihrer Website hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten interaktiven Bildes.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).

1. Fügen Sie den kopierten Einbettungs-Code auf dem gewünschten Bereich innerhalb der Web-Seite hinzu.
Der kopierte Einbettungs-Code ist für eine responsive Umgebung ausgelegt, sodass die Anpassung an den zugewiesenen Bereich automatisch erfolgt.

**Beispiel**

Verwenden der Demo-Website als ein Beispiel:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html?lang=de)

Beachten Sie, dass es sich beim Bild der drei Männer um ein statisches `IMG`-Tag handelt:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist sehr einfach. Sie entfernen das `IMG`-Tag und ersetzen es durch den kopierten Einbettungs-Code aus Experience Manager Assets. Sie können das Ergebnis in der folgenden URL anzeigen, die ein interaktives Bild mit Shopping-Funktion auf der Seite mit drei Kreis-Hotspots anzeigt:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html?lang=de)

>[!NOTE]
>
Zurzeit dienen die Hotspots auf dem interaktiven Bild mit Shopping-Funktion auf der Demo-Website nur zu Anzeigezwecken. Sie sind noch nicht in die vorhandene Schnellansicht integriert.

Um einen „Zuschnitt“ auf ein interaktives Bild mit Shopping-Funktion für eine responsive Umgebung anzuwenden, fügen Sie im Pfad das Konfigurationsattribut `ZoomView.iscommand` für das interaktive Bild ein. Die Komponente `ZoomView` wird aufgerufen und `iscommand` ist der von Ihnen verwendete Image-Serving-Befehl „Zuschnitt“.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=de).

Informationen finden Sie unter [Image-Serving-Befehl](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=de).

Jetzt können Sie das interaktive Bild in eine vorhandene Schnellansicht auf Ihrer Website integrieren.

## Integrieren eines interaktiven Bildes in einer Schnellansicht {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
Diese Aufgabe ist nur relevant, wenn Sie ausschließlich Experience Manager Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Schnellansichtsimplementierung ist einzigartig und erfordert eine individuelle Vorgehensweise. Wahrscheinlich ist dabei die Unterstützung von Frontend-IT-Mitarbeitenden erforderlich.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Web-Seite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Frontend-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt dem Frontend-Code die entsprechenden Schnellansichtsdaten oder -inhalte zurück.
1. Der Frontend-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Frontend-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen keine unabhängigen öffentlichen API-Aufrufe dar, die durch die Web-Seitenlogik in einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Während das interaktive Bild mit Shopping-Funktion Schritt 1 und teilweise Schritt 2 ersetzt, werden Benutzerinteraktionen beim Klicken auf einen Hotspot auf dem Bild mit Shopping-Funktion durch den Viewer verarbeitet. Der Viewer gibt ein Ereignis an die Web-Seite zurück, das alle Hotspot-Daten enthält, die zuvor zu Experience Manager Assets hinzugefügt wurden.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Er lauscht auf ei Ereignis, das durch das interaktive Bild mit Shopping-Funktion ausgegeben wurde.
* Er erstellt anhand der Hotspot-Daten eine Schnellansichts-URL.
* Er löst den Schnellansichts-Ladevorgang vom Backend aus und rendert die Schnellansicht auf dem Bildschirm, um sie anzuzeigen.

Der von Experience Manager Assets zurückgegebene Einbettungs-Code verfügt über einen einsatzbereiten Ereignis-Handler, der auskommentiert ist, wie im folgenden hervorgehobenen Code-Fragment zu sehen ist:

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : {
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/",
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you must add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //See your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handler-Text durch den Code zu ersetzen, der für die bestimmte Web-Seite spezifisch ist.

Die Vorgehensweise zum Erstellen der Schnellansichts-URL ist im Prinzip das Gegenteil des vorhin beschriebenen Prozesses zum Ermitteln von Hotspot-Variablen.

Siehe [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

Unter Verwendung der vorherigen Schnellansichts-URL-Beispiele können Sie in den folgenden Beispielen sehen, wie die Schnellansichts-URL in jedem Fall erstellt wird:

<table>
 <tbody>
  <tr>
   <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
 </tbody>
</table>

Der letzte Schritt besteht darin, die Schnellansichts-URL auszulösen, und für das Aktivieren des Schnellansichtsbereichs ist höchstwahrscheinlich die Unterstützung eines Frontend-IT-Mitarbeiters aus Ihrer IT-Abteilung erforderlich. Diese Fachkraft verfügt am ehesten über das entsprechende Fachwissen, um mithilfe einer vordefinierten Schnellansichts-URL die Implementierung der Schnellansicht im entsprechenden Schritt auszulösen.

Sie können sehen, wie diese Schritte auf die Demo-Website angewendet werden, sodass ein interaktives Bild mit Shopping-Funktion mit dem Schnellansichts-Code voll integriert wird. Zuvor wurde die Struktur der Schnellansichts-URL wie folgt ermittelt:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Um diese URL innerhalb der Handlers `quickViewActivate` zu rekonstruieren, können Sie die Felder `categoryId` und `SKU` verwenden, die im Objekt `inData` verfügbar sind, das durch den Code des Viewers an den Handler übergeben wird:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Auf der Demo-Website wird die Anzeige des Schnellansichtsdialogfelds durch einen einfachen `loadQuickView()`-Funktionsaufruf ausgelöst. Diese Funktion akzeptiert als einziges Argument die Schnellansichtsdaten-URL. Der letzte Schritt bei der Integration des interaktiven Bildes mit Shopping-Funktion besteht darin, dem `quickViewActivate`-Handler die folgende Code-Zeile hinzuzufügen:

```xml
loadQuickView(quickViewUrl);
```

Im Folgenden finden Sie den vollständigen Quell-Code:

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : {
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   });
 s7interactiveimageviewer.init();
```

Die endgültige Demowebsite mit dem vollständig integrierten interaktiven Bild sieht wie folgt aus:

[https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=de](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html?lang=de)

## Verwenden der Schnellansicht zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Erstellen eines benutzerdefinierten Popup-Fensters mithilfe einer Schnellansicht](/help/assets/custom-pop-ups.md).
