---
title: Interaktive Bilder
description: Erfahren Sie, wie Sie in Dynamic Media mit interaktiven Bildern arbeiten
uuid: 0bdb73f7-6ce9-4cdf-b6b5-a4d3d4e19a23
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: a6f58f6a-015a-4ced-941c-ef1b6d3e1d6f
docset: aem65
feature: Interaktive Bilder
role: Business Practitioner, Administrator
exl-id: 8a609024-e9e6-4805-8306-48d095110eb6
source-git-commit: b1e0ea01688095b29d8fb18baf6fa0bda660dad5
workflow-type: tm+mt
source-wordcount: '4332'
ht-degree: 99%

---

# Interaktive Bilder {#interactive-images}

Sie können statische Bilder mühelos in umfassende, begeisternde Erlebnisse für Kunden umwandeln, indem Sie Shop-fähige Hotspots per Drag-and-Drop auf ein Bild ziehen. In Shop-fähigen Hotspots werden zusätzliche Informationen über ein Produkt oder einen Service mit einer direkten Point-of-Sale-Funktion vom Typ „Zu Warenkorb hinzufügen“ oder „Kaufen“ kombiniert. Kunden können auf diese Hotspots tippen oder klicken und können direkt mit dem Produkt oder Service eine Verbindung herstellen, es zum Warenkorb hinzufügen oder es mit einer Web-Seite verknüpfen. Direkte Erlebnisse wie diese erhöhen die Kundeninteraktion bzw. -konversion auf Ihrer Website.

Die folgende Abbildung zeigt ein Banner mit Shopping-Funktion mit einem Schnellansichts-Popup. Benutzer können die Schnellansicht aktivieren, indem sie auf den Kreis oder „Hotspot“ des Modells tippen.

![chlimage_1-152](assets/chlimage_1-368.png)

Zeigen Sie die interaktiven Bilder in Aktion auf der oben gezeigten Webseite an, indem Sie Folgendes aufrufen:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html)

## Sehen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Hier erhalten Sie eine Einführung (10 Min., 33 Sek.) in die [Erstellung interaktiver Bild-Banner](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Außerdem erfahren Sie, wie Sie interaktive Bildbanner in der Vorschau betrachten, bearbeiten und bereitstellen können.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen den schnellen Einstieg in die Arbeit mit interaktiven Bildern in AEM Assets ermöglichen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Hier finden Sie ein kurzes Tutorial, das auf der folgenden Beispielwebseite basiert, der noch keine interaktiven Bilder hinzugefügt wurden:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

Das Tutorial veranschaulicht die Schritte zur Integration von interaktiven Bildern auf Ihrer eigenen Website.

Schritte zum Erstellen interaktiver Bilder:

1. **(Optional) Ermitteln von Hotspot-Variablen**: Wenn Sie lediglich AEM Assets und Dynamic Media verwenden, ermitteln Sie zunächst die dynamischen Variablen, die in Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie bei der Erstellung des interaktiven Bildes Hotspot-Daten eingeben können. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).
Wenn Sie jedoch AEM Sites, AEM eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.
Siehe [eCommerce-Konzepte in AEM Assets](/help/commerce/cif-classic/administering/concepts.md).

1. **(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder**: Passen Sie das Grafikbild an, das zur Darstellung von Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.
Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](/help/assets/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bild-Banners**: Laden Sie Bildbanner hoch, die Sie interaktiv machen möchten. Siehe [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bildbanner**: Fügen Sie einem Bildbanner einen oder mehrere Hotspots hinzu und weisen Sie jedem eine Aktion wie beispielsweise einen Hyperlink, eine Schnellansicht oder ein Experience Fragment zu. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.

   * Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
   * Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
   * Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website oder zu Ihrer Website in AEM**
Wenn Sie AEM Sites, AEM eCommerce oder beides verwenden, können Sie das interaktive Bild direkt auf einer Web-Seite in AEM hinzufügen, indem Sie die interaktive Medienkomponente auf die Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten.](/help/assets/adding-dynamic-media-assets-to-pages.md).
Wenn Sie lediglich AEM Assets und Dynamic Media verwenden, müssen Sie den Einbettungs-Code auf Ihrer Website kopieren und in Ihre vorhandene Schnellansicht integrieren. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).
Wenn Sie einen Drittanbieter-WCM (Web Content Manager) verwenden, müssen Sie das neue interaktive Video in die vorhandene Schnellansichtsimplementierung integrieren, die auf Ihrer Website verwendet wird. Siehe [Integrieren eines interaktiven Bildes in einer Schnellansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Ermitteln von Hotspot-Variablen {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie möchten das Bild durch Auslösen von Schnellansichten in ein interaktives Bild umwandeln.
>* Ihre AEM-Implementierung verwendet *kein* E-Commerce-Integrations-Framework, um Produktdaten aus einer E-Commerce-Lösung wie IBM Websphere Commerce, Elastic Path, hybris oder Intershop in AEM abzurufen. Siehe [eCommerce-Konzepte in AEM Assets](/help/commerce/cif-classic/administering/concepts.md).

>
>
Wenn Ihre AEM-Implementierung eCommerce nutzt, können Sie diese Aufgabe überspringen und mit der nächsten Aufgabe fortfahren.

Ermitteln Sie zunächst die dynamischen Variablen, die von Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie einem Bannerbild in AEM Assets Hotspots hinzufügen, müssen Sie eine SKU (Stock Keeping Unit: eindeutiger Bezeichner für die jeweiligen von Ihnen angebotenen Produkte oder Services) und optionale zusätzliche Variablen für jeden Hotspot zuweisen. Anhand dieser Hotspot-Variablen werden Hotspots später mit Schnellansichtsinhalten abgeglichen.

Sie müssen die Anzahl und den Typ der Variablen für die Verknüpfung mit Hotspot-Daten korrekt identifizieren. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal ist es ausreichend, IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Diese kennen wahrscheinlich den Mindestsatz an Daten, der zum Ermitteln der Schnellansicht im System erforderlich ist. In den meisten Fällen ist es jedoch auch möglich, einfach das vorhandene Verhalten des Frontend-Codes zu analysieren.

Die meisten Schnellansichtsimplementierungen verwenden das folgende Modell:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Dazu kann er beispielsweise auf die Schaltfläche „Schnellansicht“ klicken.
* Die Website sendet eine Ajax-Anfrage an das Backend, um bei Bedarf die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Web-Seite vorbereitet zu werden.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Dann werden unterschiedliche Bereiche der vorhandenen Website besucht, auf denen die Schnellansichtsfunktion implementiert wird, die Schnellansicht wird ausgelöst und die Ajax-URL, die durch die Web-Seite zum Laden der Schnellansichtsdaten oder -inhalte gesendet wurde, wird erfasst.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* Um alle ausgehenden HTTP-Anfragen in Google Chrome anzuzeigen, drücken Sie F12, um den Bereich für Entwickler-Tools zu öffnen; klicken Sie dann auf die Registerkarte „Netzwerk“.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Netzwerk“.

* In Firefox können Sie entweder durch Drücken von F12 das Firebug-Plug-in aktivieren und dessen Registerkarte „Netzwerk“ verwenden oder das integrierte Inspektor-Tool und dessen Registerkarte „Netzwerk“ einsetzen.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Inspektor“.

Wenn die Netzwerküberwachung im Browser aktiviert ist, lösen Sie die Schnellansicht auf der Seite aus.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. In den meisten Fällen werden beim Auslösen der Schnellansicht zahlreiche Anfragen an den Server gesendet. In der Regel ist die Schnellansichts-Ajax-URL die erste URL in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/xml`, `text/html` oder `text/javascript`.

Während dieses Vorgangs müssen Sie verschiedene Bereiche der Website mit verschiedenen Produktkategorien und -typen besuchen. Grund dafür ist, dass Schnellansichts-URLs möglicherweise Teile aufweisen, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert das einzige Datenteil, das Sie benötigen, um dem Bannerbild Hotspots hinzuzufügen.

In komplexen Fällen hat die Schnellansichts-URL allerdings mehrere verschiedene Elemente zusätzlich zur SKU, wie Kategorie-ID, Farb-Code, Größen-Code usw. In diesen Fällen ist jedes Element eine separate Variable in der Hotspot-Datendefinition der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets.

Im Folgenden finden Sie einige Beispiele für Schnellansichts-URLs und die resultierenden Hotspot-Variablen:

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

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

Die Demo-Web-Seite enthält mehrere Produkt-Miniaturansichten. Jede davon verfügt über eine Schnellansichts-Schaltfläche mit der Bezeichnung „Mehr anzeigen“. Klicken Sie bei aktiviertem Debugging-Tool des Webbrowsers auf jede Schaltfläche und notieren Sie sich die aufgezeichneten Schnellansichts-URLs. Nachdem Sie alle vier Produktschnellansichten auf der Seite aktiviert haben, verfügen Sie über die folgende Liste mit den an das Backend gesendeten Schnellansichtsanfragen:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wenn Sie diese Server-Aufrufe betrachten, sehen Sie, dass nur der Anfragepfad produktspezifische Informationen enthält. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist „Männer“ oder „Frauen“. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, wie beispielsweise „CamoPullover“. Sie können davon ausgehen, dass dies die Produkt-SKU ist.

Mit diesen Informationen hat die gesamte Schnellansichts-URL das folgende Muster:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Jetzt können Sie ein Bildbanner hochladen und diesem Hotspots mit der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets hinzufügen.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder {#optional-creating-an-interactive-image-viewer-preset}

Sie können die standardmäßige Viewer-Vorgabe für interaktive Bilder mit dem Namen `Shoppable_Banner` verwenden, die in AEM Assets integriert ist. Sie können auch eine eigene benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Erscheinungsbild von Hotspots auf dem Bildbanner bestimmen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

Nachdem Sie die Viewer-Vorgabe gespeichert haben, wird sie automatisch auf der Seite mit der Liste der „Viewer-Vorgaben“ in AEM Assets aktiviert (eingeschaltet). Diese Funktionalität bedeutet, dass sie in der interaktiven Medienkomponente sowie dann sichtbar ist, wenn Sie ein Asset anzeigen. Um jedoch ein interaktives Banner mit dieser Viewer-Vorgabe bereitzustellen, müssen Sie die Viewer-Vorgabe auch veröffentlichen (gilt für benutzerdefinierte und standardmäßige Viewer-Vorgaben).

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder:**

1. Tippen Sie links in der Leiste auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer-Vorgaben]**.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „Neue Viewer-Vorgabe“ einen Namen ein, um die Viewer-Vorgabe für interaktive Banner zu beschreiben.

   Hierbei handelt es sich um den Titel, der nach dem Speichern auf der Listenseite „Viewer-Vorgabe“ angezeigt wird.

1. Wählen Sie im Pulldown-Menü „Rich-Media-Typ“ die Option **[!UICONTROL Interaktives Bild]** aus.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Erscheinungsbild]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Um ein eigenes Hotspot-Bild hochzuladen, das Sie für Bilder verwenden möchten, tippen Sie auf das Symbol für die Asset-Auswahl. Navigieren Sie auf der Seite „Inhalt auswählen“ zum gewünschten Hotspot-Bild, wählen Sie es aus und tippen Sie oben rechts auf das Häkchen.
   * Um ein vordefiniertes Hotspot-Bild auszuwählen, tippen Sie auf das Symbol für die Hotspot-Galerie. Tippen Sie in der Palette der Hotspot-Galerie auf das gewünschte Hotspot-Bild.

1. Tippen Sie oben rechts auf **[!UICONTROL Speichern]**.

   Stellen Sie sicher, die neue Viewer-Vorgabe zu veröffentlichen.

   Informationen finden Sie unter [Veröffentlichen der von Ihnen hinzugefügten Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

   Sie sind nun bereit, ein Bildbanner hochzuladen.

## Hochladen eines Bildbanners  {#uploading-an-image-banner}

Wenn Sie die gewünschten Bilder bereits hochgeladen haben, fahren Sie mit dem nächsten Schritt fort: [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).

**So laden Sie ein Bildbanner hoch:**

1. Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Informationen hierzu finden Sie unter [Hochladen von Assets](/help/assets/manage-assets.md#uploading-assets).

   Sie können jetzt dem Bildbanner Hotspots hinzuzufügen. Anweisungen dazu finden Sie in der folgenden Aufgabe.

## Hinzufügen von Hotspots zu einem Bildbanner  {#adding-hotspots-to-an-image-banner}

Sie können einem Bildbanner Hotspots hinzufügen, indem Sie den Editor auf der Seite „Hotspot-Verwaltung“ verwenden.

Beim Hinzufügen von Hotspots können Sie sie als eine Schnellansichts-Popup-Anzeige, als einen Hyperlink oder als Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

>[!NOTE]
>
>Beachten Sie, dass im interaktiven Bild die Tools zur Freigabe in Social Media nicht unterstützt werden, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.

Wenn Sie die Erstellung des interaktiven Bildes abgeschlossen haben, können Sie eine Vorschau anzeigen, um das interaktive Bild aus der Perspektive der Kunden zu betrachten.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wenn Sie Hotspots einem interaktiven Bild oder einem Bild für ein Karussellbanner hinzufügen, werden die Hotspot-Informationen immer am selben Metadatenspeicherort gespeichert, der relativ zum Speicherort des Bildes ist, unabhängig davon, ob es sich um ein interaktives Bild oder um ein Karussellbanner handelt. Das bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.
>
>Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Dies sollten Sie beachten, wenn Sie ein interaktives Bild oder ein Karussellbanner mit demselben Bild erstellen möchten. Stattdessen sollten Sie separate Kopien desselben Bildes verwenden, um interaktive Bilder und Karussellbilder zu erstellen.
>
>Weitere Informationen finden Sie unter [Karussellbanner](/help/assets/carousel-banners.md).

>[!NOTE]
>
>Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**

1. Navigieren Sie in der Ansicht „Assets“ zu dem Bildbanner, das interaktiv sein soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie dann auf **[!UICONTROL Weitere Aktionen]** (Drei-Punkte-Symbol) **[!UICONTROL Bearbeiten]**.

   * Tippen Sie auf das Bild, um es auf der Seite „Detailansicht“ zu öffnen. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Hotspot hinzufügen]** (Fingertipp-Symbol), um die Hotspot-Verwaltungsseite zu öffnen.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Hotspot]**.

   1. Tippen Sie in der rechten oberen Ecke der Seite „Hotspot-Verwaltung“ auf **[!UICONTROL Hotspot]**.
   1. Tippen Sie im Bild auf eine Stelle, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen.
   1. Fügen Sie bei Bedarf weitere Hotspots hinzu, indem Sie die Schritte a und b wiederholen.
   1. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn auf dem Bild aus und tippen Sie dann auf **[!UICONTROL Löschen]** (Papierkorb-Symbol) unter der Überschrift **[!UICONTROL Hotspots]**.

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots ein. Dieser Name wird auch in der Dropdownliste „Ausgewählter Hotspot“ angezeigt.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Schnellansicht]**.

      * Wenn Sie AEM Sites- oder eCommerce-Kunde sind, tippen oder klicken Sie auf das Produktauswahlsymbol (Lupe), um die Seite „Produkt wählen“ zu öffnen. Tippen oder klicken Sie auf das Produkt, das Sie verwenden möchten, und tippen Sie in der rechten oberen Ecke der Seite auf **Auswählen**, um zur Seite „Hotspot-Verwaltung“ zurückzukehren.
      * Wenn Sie *kein* AEM Sites- oder eCommerce-Kunde sind, gehen Sie wie folgt vor:

         * Lesen Sie den Abschnitt [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables). Diese Variablen müssen Sie definieren.
         * Geben Sie anschließend manuell den SKU-Wert ein. Geben Sie im Textfeld „SKU-Wert“ die Bestandseinheit (Stock Keeping Unit, SKU) des Produkts ein. Hierbei handelt es sich um eine eindeutige Kennung für die jeweiligen von Ihnen angebotenen Produkte oder Services. Der variable Teil der Schnellansichtsvorlage wird automatisch mit dem eingegebenen SKU-Wert ausgefüllt, sodass das System den Hotspot, auf den getippt wird, mit der Schnellansicht einer bestimmten SKU verbinden kann.
         * (Optional) Wenn andere Variablen in der Schnellansicht vorhanden sind, die Sie verwenden müssen, um ein Produkt weitergehend zu identifizieren, tippen Sie auf **[!UICONTROL Generische Variable hinzufügen]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
   * Tippen Sie auf **[!UICONTROL Hyperlink]**.

      * Wenn Sie AEM Sites-Kunde sind, tippen oder klicken Sie auf das Symbol zur Site-Auswahl (Ordner), um zu einer URL zu navigieren. Beachten Sie, dass die URL-basierte Verknüpfungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
      * Wenn Sie Einzelkunde sind, geben Sie im Textfeld „HREF“ den vollständigen URL-Pfad zu einer verknüpften Web-Seite an.

   Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md).

   * Tippen Sie auf **[!UICONTROL Experience Fragment]**.

      * Wenn Sie AEM Sites-Kunde sind, tippen oder klicken Sie auf das Suchsymbol (Lupe), um die Seite „Experience Fragment“ zu öffnen. Tippen oder klicken Sie auf das Experience Fragment, das Sie verwenden möchten, und tippen Sie in der rechten oberen Ecke der Seite auf „Auswählen“, um zur Seite „Hotspot-Verwaltung“ zurückzukehren.
Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-authoring/experience-fragments.md).

      * Legen Sie die Breite und Höhe des Experience Fragment fest, so wie es im Banner angezeigt werden soll.

         >[!NOTE]
         >
         >Beachten Sie, dass im interaktiven Bild die Tools zur Freigabe in Social Media nicht unterstützt werden, wenn Sie den Viewer in ein Experience Fragment einbetten. Um dies zu vermeiden, können Sie Viewer-Vorgaben verwenden oder erstellen, die keine Tools zur Freigabe in Social Media aufweisen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.



1. Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern, und kehren Sie zur Seite „Durchsuchen“ zurück.
1. Veröffentlichen Sie das interaktive Bild. Durch eine Veröffentlichung kann das Banner über die Cloud bereitgestellt werden. Außerdem wird ein Einbettungs-Code zur Integration auf der Website von Dritten generiert.

   Siehe [Veröffentlichen von Assets](/help/assets/manage-assets.md#publishing-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   >
   >Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder  {#optional-previewing-interactive-images}

Mithilfe der Vorschau können Sie eine Darstellung des interaktiven Bildes aus der Perspektive der Kunden anzeigen und die Hotspots des Bildes testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Beachten Sie, dass die URL-basierte Verknüpfungsmethode nicht möglich ist, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau für interaktive Bilder an:**

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, um es in der Vorschau zu öffnen.
1. Tippen Sie in der Nähe der linken oberen Ecke der Seite „Vorschau“ in der Dropdown-Liste „Inhalt“ auf **[!UICONTROL Viewer]**.
1. Tippen Sie in der Liste „Viewer“ auf **[!UICONTROL Shoppable_Banner]** oder auf den Namen der von Ihnen erstellten Viewer-Vorgabe für interaktive Bilder.
1. Tippen Sie auf die Hotspots auf dem Bild, um ihre zugehörigen Aktionen zu testen.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt auf Ihrer Website hinzufügen.

Wenn Sie AEM Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

Wenn Sie nur AEM Assets verwenden, können Sie das interaktive Bild Ihrer Website manuell hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten interaktiven Bildes.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).

1. Fügen Sie den kopierten Einbettungs-Code auf dem gewünschten Bereich innerhalb der Web-Seite hinzu.
Der kopierte Einbettungs-Code ist für eine responsive Umgebung ausgelegt, sodass die Anpassung an den zugewiesenen Bereich automatisch erfolgen sollte.

**Beispiel**

Verwenden der Demo-Website als ein Beispiel:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html)

Beachten Sie, dass es sich beim Bild der drei Männer um ein statisches `IMG`-Tag handelt:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist so einfach wie das Entfernen des `IMG`-Tags und dessen entsprechende Ersetzung durch den kopierten Integrations-Code aus AEM Assets. Sie können das Ergebnis in der folgenden URL anzeigen, die ein interaktives Bild mit Shopping-Funktion auf der Seite mit drei Kreis-Hotspots anzeigt:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html)

>[!NOTE]
>
>Zurzeit dienen die Hotspots auf dem interaktiven Bild mit Shopping-Funktion auf der Demo-Website nur zu Anzeigezwecken. Sie sind zurzeit noch nicht in die Schnellansichten integriert.

Um einen „Zuschnitt“ auf ein interaktives Bild mit Shopping-Funktion für eine responsive Umgebung anzuwenden, können Sie das Konfigurationsattribut für das interaktive Bild `ZoomView.iscommand` im Pfad einbeziehen, wobei `ZoomView` die aufzurufende Komponente und `iscommand` der von Ihnen angewendete Image-Serving-Befehl „Zuschneiden“ ist.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=de).

Informationen finden Sie unter [Image-Serving-Befehl](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=de).

Jetzt können Sie das interaktive Bild in eine vorhandene Schnellansicht auf Ihrer Website integrieren.

## Integrieren eines interaktiven Bildes in einer Schnellansicht   {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Diese Aufgabe ist nur relevant, wenn Sie die Standalone-Version von AEM Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Schnellansichtsimplementierung ist einzigartig. Daher ist ein spezifischer Ansatz erforderlich, wofür höchstwahrscheinlich die Unterstützung eines Frontend-IT-Mitarbeiters nötig ist.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Web-Seite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Frontend-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt dem Frontend-Code die entsprechenden Schnellansichtsdaten oder -inhalte zurück.
1. Der Frontend-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Frontend-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen möglicherweise keine unabhängigen öffentlichen API-Aufrufe dar, die durch die Web-Seitenlogik in einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Gleichzeitig, wenn das interaktive Bild mit Shopping-Funktion Schritt 1 und teilweise Schritt 2 ersetzt, sofern ein Benutzer auf einen Hotspot auf dem Bild mit Shopping-Funktion klickt, wird eine derartige Benutzerinteraktion durch den Viewer verarbeitet. Der Viewer gibt der Web-Seite ein Ereignis zurück, das alle zuvor zu AEM Assets hinzugefügten Hotspot-Daten aufweist.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das interaktive Bild mit Shopping-Funktion ausgegeben wurde.
* Er erstellt anhand der Hotspot-Daten eine Schnellansichts-URL.
* Er löst den Schnellansichts-Ladevorgang vom Backend aus und rendert die Schnellansicht auf dem Bildschirm, um sie anzuzeigen.

Der von AEM Assets zurückgegebene Einbettungs-Code verfügt über einen einsatzbereiten Ereignis-Handler, der auskommentiert ist, wie im folgenden hervorgehobenen Code-Fragment zu sehen ist:

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
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Web-Seite spezifisch ist.

Der Prozess der Erstellung der Schnellansichts-URL ist im Prinzip das Gegenteil des Prozesses, der verwendet wird, um die zuvor erläuterten Hotspot-Variablen zu ermitteln.

Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

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

Der letzte Schritt besteht darin, die Schnellansichts-URL auszulösen, und für das Aktivieren des Schnellansichtsbereichs ist höchstwahrscheinlich die Unterstützung eines Frontend-IT-Mitarbeiters aus Ihrer IT-Abteilung erforderlich. Er verfügt am ehesten über das entsprechende Fachwissen, um die Schnellansichtsimplementierung aus dem entsprechenden Schritt entsprechend auszulösen, um über eine einsatzbereite Schnellansichts-URL zu verfügen.

Sie können sehen, wie diese Schritte auf die Demo-Website angewendet werden, sodass ein interaktives Bild mit Shopping-Funktion mit dem Schnellansichts-Code voll integriert wird. Die Struktur der Schnellansichts-URL wurde bereits wie folgt ermittelt:

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

Die endgültige Demowebsite mit dem vollständig integrierten interaktiven Bild hat folgendes Aussehen:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html)

## Verwenden von Schnellansichten zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Popups mithilfe von benutzerspezifischen Schnellansichten erstellen](/help/assets/custom-pop-ups.md).
