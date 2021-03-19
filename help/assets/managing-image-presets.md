---
title: Verwalten von Dynamic Media-Bildvorgaben
description: Verstehen Sie Dynamic Media-Bildvorgaben und lernen Sie, wie Sie Bildvorgaben erstellen, ändern und verwalten.
uuid: 3e9a7af6-bf49-4cff-b516-0a3ee9765391
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cc1111c4-6e24-4570-9ac7-97c25cf24ede
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/image-presets
feature: Bildvorgaben
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '3833'
ht-degree: 89%

---


# Verwalten von Dynamic Media-Bildvorgaben{#managing-image-presets}

Anhand von Bildvorgaben kann AEM Assets Bilder mit unterschiedlichen Größen, Formaten oder Bildeigenschaften dynamisch bereitstellen. Jede Bildvorgabe stellt eine vordefinierte Sammlung aus Größen- und Formatierungsbefehlen für die Anzeige von Bildern dar. Beim Erstellen einer Bildvorgabe wählen Sie eine Größe für die Bildbereitstellung aus. Außerdem wählen Sie Formatierungsbefehle, damit die Darstellung des Bildes bei der Bereitstellung zur Anzeige optimiert wird.

Administratoren können Vorgaben für den Export von Assets erstellen. Benutzer können eine Vorgabe auswählen, wenn sie Bilder exportieren, sodass die Bilder entsprechend den Spezifikationen des Administrators umformatiert werden.

Sie können auch responsive Bildvorgaben erstellen. Wenn Sie eine responsive Bildvorgabe auf Assets anwenden, werden diese je nach Gerät oder Bildschirmgröße bei der Anzeige geändert. Sie können Bildvorgaben konfigurieren, um im Farbraum zusätzlich zu RGB oder Graustufen auch CMYK zu verwenden.

In diesem Abschnitt wird beschrieben, wie Bildvorgaben erstellt, geändert und allgemein verwaltet werden. Sie können jederzeit bei der Vorschau eines Bildes eine Bildvorgabe darauf anwenden. Siehe [Anwenden von Bildvorgaben](/help/assets/image-presets.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/imaging-faq.md).

## Die Dynamic Media-Bildvorgaben {#understanding-image-presets}

Wie ein Makro ist eine Bildvorgabe eine vordefinierte Sammlung aus Größenangaben und Formatierungsbefehlen, die unter einem Namen gespeichert wird. Stellen Sie sich folgendes Szenario vor, um ein besseres Verständnis von Bildvorgaben zu erlangen: Für Ihre Website muss jedes Produktbild in unterschiedlichen Größen, Formaten und Kompressionsraten auf Desktop- und Mobilgeräten angezeigt werden.

>[!NOTE]
>
>Im Dynamic Media-Scene7-Modus werden Bildvorgaben nur für Bild-Assets unterstützt.

Sie können zwei Bildvorgaben erstellen: eine mit 500 x 500 Pixel für die Desktopcomputerversion und die andere mit 150 x 150 Pixel für die Mobilgeräteversion. Sie können zwei Bildvorgaben erstellen: `Enlarge` (Vergrößern) dient der Anzeige von Bildern mit einer Auflösung von 500 x 500 Pixel, `Thumbnail` (Miniaturansicht) der Anzeige von Bildern mit einer Auflösung von 150 x 150 Pixel. Zum Übermitteln von Bildern mit der Größe `Enlarge` und `Thumbnail` sucht AEM nach der Definition der Bildvorgabe „Vergrößern“ und nach der Bildvorgabe „Miniaturansicht“. AEM generiert anschließend dynamisch ein Bild anhand der Größen- und Formatierungsspezifikationen der jeweiligen Bildvorgabe.

Bilder, die bei der dynamischen Bereitstellung verkleinert werden, können an Schärfe und Detailgenauigkeit verlieren. Aus diesem Grund umfasst jede Bildvorgabe Formatierungssteuerelemente für die Optimierung eines Bildes, wenn es mit einer bestimmten Größe bereitgestellt wird. Dadurch wird sichergestellt, dass die Bilder scharf und deutlich auf der Website oder im Programm angezeigt werden.

Administratoren können Bildvorgaben erstellen. Sie können völlig neue Bildvorgaben erstellen oder eine vorhandene Vorgabe bearbeiten und unter einem neuen Namen speichern.

## Verwalten von Dynamic Media-Bildvorgaben {#managing-image-presets-1}

Bildvorgaben verwalten Sie in AEM, indem Sie auf das AEM-Logo tippen oder klicken, um auf die globale Navigationskonsole zuzugreifen. Tippen oder klicken Sie dann auf das Werkzeugsymbol und navigieren Sie zu **[!UICONTROL Assets > Bildvorgaben.]**

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle erstellten Bildvorgaben sind auch als dynamische Ausgabedarstellungen verfügbar, wenn Sie eine Vorschau von Assets anzeigen oder Assets bereitstellen.
>
>Im *Modus „Dynamic Media – Scene7“* müssen Sie Bildvorgaben *nicht* veröffentlichen, da die Veröffentlichung von Bildvorgaben automatisch erfolgt.
>
>Im *Modus „Dynamic Media – Hybrid“* müssen Sie Bildvorgaben manuell veröffentlichen.
>
>Siehe [Veröffentlichen von Bildvorgaben](#publishing-image-presets).

>[!NOTE]
>
>Das System zeigt mehrere Ausgabedarstellungen, wenn Sie **[!UICONTROL Ausgabedarstellungen]** in der Detailansicht eines Assets auswählen. Sie können die Anzahl der angezeigten Bildvorgaben erhöhen oder verringern. Siehe [Erhöhung der Anzahl der angezeigten Bildvorgaben](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Smart Cards, Adobe Illustrator (AI), Postscript (EPS) und PDF-Dateiformate {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

>[!NOTE]
>
>Dieses Thema bezieht sich nur auf den Dynamic Media-Hybridmodus.

Wenn Sie AI-, EPS- und PDF-Dateien unterstützen möchten, um aus diesen Dateiformaten dynamische Ausgabedarstellungen zu generieren, sollten Sie die folgenden Informationen lesen, bevor Sie Bildvorgaben erstellen.

Das Dateiformat von Adobe Illustrator ist eine Variante von PDF. Dies sind die wichtigsten Unterschiede im Hinblick auf AEM Assets:

* Adobe Illustrator-Dokumente bestehen aus einer einzelnen Seite mit mehreren Ebenen. Jede Ebene wird als PNG-Teil-Asset unter dem Illustrator-Haupt-Asset extrahiert.
* PDF-Dokumente bestehen aus einer oder mehreren Seiten. Jede Seite wird als einseitiges PDF-Teil-Asset unter dem mehrseitigen PDF-Hauptdokument extrahiert.

Die Teil-Assets werden von der Komponente `Create Sub Asset process` im übergeordneten `DAM Update Asset`-Workflow erstellt. Um diese Prozesskomponente innerhalb des Workflows anzuzeigen, tippen Sie auf **[!UICONTROL Tools > Workflow > Modelle > DAM-Update-Asset > Bearbeiten.]**

Siehe auch [Seiten einer mehrseitigen Datei anzeigen](/help/assets/managing-linked-subassets.md#view-pages-of-a-multi-page-file).

Sie können die Teil-Assets oder die Seiten anzeigen, wenn Sie das Asset öffnen, auf das Menü „Inhalt“ tippen und **[!UICONTROL Teil-Assets]** oder **[!UICONTROL Seiten auswählen.]** Teil-Assets sind echte Assets. Daher werden PDF-Seiten durch den Workflow `Create Sub Asset` (Teil-Asset erstellen) extrahiert. Die Seiten werden dann unter dem Haupt-Asset als `page1.pdf`, `page2.pdf` usw. gespeichert. Nach dem Speichern werden sie vom Workflow `DAM Update Asset` verarbeitet.

Um Dynamic Media zu verwenden und dynamische Ausgabedarstellungen für AI-, EPS- oder PDF-Dateien als Vorschau anzuzeigen oder zu generieren, sind folgende Verarbeitungsschritte erforderlich:

1. Im Workflow `DAM Update Asset` wird die erste Seite des ursprünglichen Assets mithilfe der konfigurierten Auflösung von der Prozesskomponente `Rasterize PDF/AI Image Preview Rendition` in einer Ausgabedarstellung `cqdam.preview.png` gerastert.

1. Die Ausgabedarstellung `cqdam.preview.png` wird dann im Workflow durch die Prozesskomponente `Dynamic Media Process Image Assets` zu einer PTIFF-Datei optimiert.

>[!NOTE]
>
>Im Arbeitsablauf [!UICONTROL DAM-Update-Asset] generiert der Schritt **[!UICONTROL EPS-Miniaturansichten]** Miniaturansichten für EPS-Dateien.

#### Metadateneigenschaften von PDF-/AI-/EPS-Assets  {#pdf-ai-eps-asset-metadata-properties}

| **Metadateneigenschaft** | **Beschreibung** |
|---|---|
| dam:Physicalwidthininches | Dokumentbreite in Zoll. |
| dam:Physicalheightininches | Dokumenthöhe in Zoll. |

Sie können `Rasterize PDF/AI Image Preview Rendition`-Prozesskomponentenoptionen über den Workflow `DAM Update Asset` aufrufen.

Tippen Sie links oben auf Adobe Experience Manager und navigieren Sie zu **[!UICONTROL Tools > Workflow > Modelle.]** Wählen Sie auf der Seite „Workflow-Modelle“ **[!UICONTROL DAM-Update-Asset]** aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Bearbeiten.]**[!UICONTROL  Doppeltippen Sie auf der Seite „Workflow DAM-Update-Asset“ auf die Prozesskomponente ], um das Dialogfeld „Schritteigenschaften“ zu öffnen.`Rasterize PDF/AI Image Preview Rendition`

#### PDF-/AI-Bildvorschau-Ausgabedarstellung rastern – Optionen {#rasterize-pdf-ai-image-preview-rendition-options}

![Argumente zum Rastern von PDF- oder AI-Workflows](assets/rasterize_pdf_ai_image_preview.png)

Argumente zum Rastern von PDF- oder AI-Workflows

<table>
 <tbody>
  <tr>
   <td><strong>Prozessargument</strong></td>
   <td><strong>Standardeinstellung</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>MIME-Typen</td>
   <td><p>application/pdf</p> <p>application/postscript</p> <p>application/illustrator<br /> </p> </td>
   <td>Liste der Dokument-MIME-Typen, die als PDF- oder Illustrator-Dokumente gelten.<br /> </td>
  </tr>
  <tr>
   <td>Max. Breite</td>
   <td>2048</td>
   <td>Maximale Breite der generierten Vorschaudarstellung in Pixel.<br /> </td>
  </tr>
  <tr>
   <td>Max. Höhe</td>
   <td>2048</td>
   <td>Maximale Höhe der generierten Vorschaudarstellung in Pixel.<br /> </td>
  </tr>
  <tr>
   <td>Auflösung</td>
   <td>72</td>
   <td>Auflösung zum Rastern der ersten Seite in ppi (Pixel pro Zoll).</td>
  </tr>
 </tbody>
</table>

Bei Verwendung der standardmäßigen Prozessargumente wird die erste Seite eines PDF/AI-Dokuments mit 72 ppi gerastert und das generierte Vorschaubild hat eine Größe von 2048 x 2048 Pixel. Für eine typische Implementierung können Sie die Auflösung auf einen Mindestwert von 150 ppi oder mehr erhöhen. Für ein US Letter-Dokument ist z. B. für 300 ppi eine maximale Breite und Höhe von 2550 x 3300 Pixel erforderlich.

Die max. Breite und die max. Höhe beschränken die Auflösung, in der die Rasterung erfolgt. Wenn z. B. die Maximalwerte unverändert bleiben und die Auflösung auf 300 ppi festgelegt wird, wird ein US Letter-Dokument mit 186 ppi gerastert. Das Dokument ist demnach 1581 x 2046 Pixel groß.

Für die Prozesskomponente `Rasterize PDF/AI Image Preview Rendition` ist ein Maximalwert definiert, um sicherzustellen, dass im Arbeitsspeicher keine zu großen Bilder erstellt werden. Zu große Bilder können zu einem Überlauf des für die JVM (Java Virtual Machine) bereitgestellten Speichers führen. Achten Sie darauf, der JVM ausreichend Arbeitsspeicher zur Verwaltung der konfigurierten Anzahl paralleler Workflows zur Verfügung zu stellen, da jeder Workflow potenziell ein Bild in der konfigurierten Maximalgröße erstellen kann.

### InDesign-Dateiformat (INDD)   {#indesign-indd-file-format}

Wenn Sie die Aufnahme von INDD-Dateien unterstützen möchten, um aus diesem Dateiformat dynamische Ausgabedarstellungen zu generieren, sollten Sie die folgenden Informationen lesen, bevor Sie Bildvorgaben erstellen.

Für InDesign-Dateien werden nur dann Teil-Assets extrahiert, wenn der Adobe InDesign Server in AEM integriert ist. Referenzierte Assets werden auf der Grundlage ihrer Metadaten verknüpft. Für die Verknüpfung ist InDesign Server nicht erforderlich. Die referenzierten Assets müssen jedoch in AEM vorhanden sein, bevor die InDesign-Dateien verarbeitet werden, damit die Verknüpfungen zwischen den InDesign-Dateien und den referenzierten Assets erstellt werden können.

Siehe [Integrieren von AEM Assets in InDesign Server](/help/assets/indesign.md).

Die Media Extraktion-Prozesskomponente im `DAM Update Asset`-Arbeitsablauf führt mehrere vorkonfigurierte Extend-Skripte zur Verarbeitung von InDesign-Dateien aus.

![Die ExtendScript-Pfade in den Argumenten des Prozesses zum Extrahieren von Medien](assets/6_5_mediaextractionprocess.png)

Die ExtendScript-Pfade in den Argumenten der Media Extraktion-Prozesskomponente im Arbeitsablauf [!UICONTROL DAM Update Asset].

Die folgenden Skripte werden von der Dynamic Media-Integration verwendet:

<table>
 <tbody>
  <tr>
   <td><strong>ExtendScript-Name</strong></td>
   <td><strong>Default</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>ThumbnailExport.jsx</td>
   <td>Ja</td>
   <td>Erstellt eine 300 ppi große <code>thumbnail.jpg</code>-Darstellung, die von der Prozesskomponente <code>Dynamic Media Process Image Assets</code> optimiert und in eine PTIFF-Darstellung umgewandelt wird.<br /> </td>
  </tr>
  <tr>
   <td>JPEGPagesExport.jsx</td>
   <td>Ja</td>
   <td>Generiert für jede Seite ein 300 ppi großes JPEG-Teil-Asset. Das JPEG-Teil-Asset ist ein echtes Asset, das unter dem InDesign-Asset gespeichert wird. Es wird auch vom Workflow <code>DAM Update Asset</code> optimiert und in eine PTIFF-Darstellung umgewandelt.<br /> </td>
  </tr>
  <tr>
   <td>PDFPagesExport.jsx</td>
   <td>Nein</td>
   <td>Generiert für jede Seite ein PDF-Teil-Asset. Das PDF-Teil-Asset wird wie zuvor beschrieben verarbeitet. Da das PDF-Asset nur eine Seite enthält, werden keine Teil-Assets generiert.<br /> </td>
  </tr>
 </tbody>
</table>

## Konfigurieren der Größe der Miniaturansicht {#configuring-image-thumbnail-size}

Sie können die Größe von Miniaturansichten über die Einstellungen im Workflow **[!UICONTROL DAM-Update-Asset]** konfigurieren. Im Workflow sind zwei Schritte enthalten, in denen Sie die Größe der Miniaturansichten von Bild-Assets konfigurieren können. Obwohl der eine (**[!UICONTROL Dynamic Media Process Image-Assets]**) für das Generieren dynamischer Bild-Assets und der andere (**[!UICONTROL Miniaturansichten verarbeiten]**) für das Generieren statischer Miniaturansichten verwendet wird bzw. dann, wenn alle anderen Prozesse zum Generieren von Miniaturansichten fehlschlagen, sollten *beide* dieselben Einstellungen haben.

Im Schritt **[!UICONTROL Bild-Assets-Prozess für Dynamic Media]** werden vom Bild-Server Miniaturansichten generiert. Diese Konfiguration ist unabhängig von der Konfiguration, die auf den Schritt **[!UICONTROL Prozessminiaturansichten]** angewendet wird. Das Generieren von Miniaturansichten mit dem Schritt **[!UICONTROL Miniaturansichten verarbeiten]** ist das langsamste und speicherintensivste Verfahren zum Erstellen von Miniaturansichten.

Die Größe der Miniaturansichten wird im folgenden Format definiert: **[!UICONTROL width:height:center]**, z. B. *80:80:false*. Die Breite und die Höhe legen die Größe der Miniaturansicht in Pixel fest. Für den Center-Wert ist entweder false oder true festgelegt. Wenn true festgelegt ist, hat das Miniaturbild exakt die in der Konfiguration festgelegte Größe. Wenn das in der Größe angepasste Bild kleiner ist, wird es im Miniaturbildfenster zentriert.

>[!NOTE]
>
>* Die Größe der Miniaturansichten für EPS-Dateien wird im Schritt **[!UICONTROL EPS-Miniaturen]** auf der Registerkarte **[!UICONTROL Argumente]** unter „Miniaturansichten“ konfiguriert.
   >
   >
* Die Größe der Miniaturansichten für Videos wird im Schritt **[!UICONTROL FFmpeg-Miniaturansichten]** unter **[!UICONTROL Prozess]** auf der Registerkarte **[!UICONTROL Argumente]** konfiguriert.

>



**So konfigurieren Sie die Größe** der Miniaturansicht:

1. Tippen Sie auf **[!UICONTROL Tools > Workflow > Modelle > DAM-Update-Asset > Bearbeiten.]**
1. Tippen Sie auf den Schritt **[!UICONTROL Dynamic Media Process Image-Assets]** und dann auf die Registerkarte **[!UICONTROL Miniaturansichten]**. Ändern Sie bei Bedarf die Größe der Miniaturansichten und tippen Sie auf **[!UICONTROL OK.]**

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Tippen Sie auf den Schritt **[!UICONTROL Miniaturansichten verarbeiten]** und dann auf die Registerkarte **[!UICONTROL Miniaturansichten]**. Ändern Sie bei Bedarf die Größe der Miniaturansichten und tippen Sie auf **[!UICONTROL OK.]**

   >[!NOTE]
   >
   >Die Werte im Argument „Miniaturansichten“ im Schritt **[!UICONTROL Miniaturansichten verarbeiten]** müssen mit dem Argument „Miniaturansichten“ im Schritt **[!UICONTROL Bild-Assets-Verarbeitung für Dynamic Media]** übereinstimmen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen am Workflow zu speichern.

### Anzahl der Dynamic Media-Bildvorgaben erhöhen oder verringern, die {#increasing-or-decreasing-the-number-of-image-presets-that-display} anzeigen

Erstellte Bildvorgaben sind auch als dynamische Ausgabedarstellungen verfügbar, wenn Sie eine Vorschau von Assets anzeigen. AEM zeigt verschiedene dynamische Ausgabedarstellungen an, wenn Sie ein Asset unter **[!UICONTROL Detailansicht > Ausgabedarstellung anzeigen.]** Sie können die Anzahl der angezeigten Ausgabedarstellungen erhöhen oder verringern.

**So erhöhen oder verringern Sie die Anzahl der angezeigten** Dynamic Media-Bildvorgaben:

1. Navigieren Sie zu CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten für die Bildvorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`.

   ![increase_decreasethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Ändern Sie für die Eigenschaft **[!UICONTROL limit]** den **[!UICONTROL Wert]**, für den standardmäßig 15 festgelegt ist, in einen höheren Wert.
1. Navigieren Sie zur Datenquelle der Bildvorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Ändern Sie in der Eigenschaft „limit“ den Wert auf die gewünschte Zahl, z. B. `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`.
1. Tippen Sie auf **[!UICONTROL Alle speichern.]**

## Erstellen einer Dynamic Media-Bildvorgabe {#creating-image-presets}

Wenn Sie eine Dynamic Media-Bildvorgabe erstellen, können Sie diese Einstellungen bei der Vorschau oder Veröffentlichung auf alle Bilder anwenden.

>[!NOTE]
>
>Wenn Sie Internet Explorer 9 verwenden und eine Vorgabe erstellen, wird diese nicht sofort nach dem Speichern in der Vorgabenliste angezeigt. Um dieses Problem zu umgehen, deaktivieren Sie den Cache für IE9.

Wenn Sie AI-, PDF-, und EPS-Dateien unterstützen möchten, um aus diesen Dateiformaten dynamische Ausgabedarstellungen zu generieren, sollten Sie die folgenden Informationen lesen, bevor Sie Bildvorgaben erstellen.
Siehe [Dateiformate Adobe Illustrator (AI), Postscript (EPS) und PDF](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Wenn Sie die Aufnahme von INDD-Dateien unterstützen möchten, um aus diesem Dateiformat dynamische Ausgabedarstellungen zu generieren, sollten Sie die folgenden Informationen lesen, bevor Sie Bildvorgaben erstellen.
Siehe [InDesign-Dateiformat (INDD)](#indesign-indd-file-format).

>[!NOTE]
>
>Zum Erstellen von Dynamic Media-Bildvorgaben müssen Sie über Administratorrechte als AEM Administrator oder Admin Console-Administrator verfügen.

**So erstellen Sie eine Dynamic Media-Bildvorgabe**:

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools > Assets > Bildvorgaben.]**
1. Klicken Sie auf **[!UICONTROL Erstellen.]** Das Fenster **[!UICONTROL Bildvorgabe bearbeiten]** wird geöffnet.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Damit diese Bildvoreinstellung responsiv wird, löschen Sie die Werte in den Feldern **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** und lassen Sie sie leer.

1. Geben Sie Werte wie gewünscht in die Registerkarten **[!UICONTROL Allgemein]** und **[!UICONTROL Erweitert]** ein, einschließlich eines Namens. Die Optionen werden unter [Bildvoreinstellungsoptionen](#image-preset-options) beschrieben. Vorgaben werden im linken Bereich angezeigt und können nur zusammen mit anderen Assets verwendet werden.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Erstellen einer reaktionsfähigen Bildvorgabe {#creating-a-responsive-image-preset}

Um eine responsive Bildvorgabe zu erstellen, führen Sie die im Abschnitt [Erstellen von Bildvorgaben](#creating-image-presets) beschriebenen Schritte durch. Löschen Sie die Werte für Höhe und Breite im Fenster **[!UICONTROL Bildvorgabe bearbeiten]** und lassen Sie sie leer.

Dadurch wird diese Vorgabe in AEM als responsiv erkannt. Sie können die anderen Werte nach Bedarf anpassen.



>[!NOTE]
>
>Um die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL RESS]** beim Anwenden einer Bildvorgabe auf ein Asset anzuzeigen, muss das Asset veröffentlicht werden.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>Im Modus „Dynamic Media – Scene7“ werden Bildvorgaben und Bildelemente automatisch veröffentlicht.
>
>Im Modus „Dynamic Media – Hybrid“ müssen Sie Bildvorgaben und Bildelemente manuell veröffentlichen.

### Optionen für Bildvorgaben {#image-preset-options}

Die in diesem Abschnitt beschriebenen Optionen sind beim Erstellen oder Bearbeiten von Bildvorgaben verfügbar. Adobe empfiehlt zudem die folgenden Best Practices für den Anfang:

* **[!UICONTROL Format]** (Registerkarte **[!UICONTROL Allgemein]**) – Wählen Sie **[!UICONTROL JPEG]** oder ein anderes Format, das Ihren Anforderungen entspricht. Alle Webbrowser unterstützen das JPEG-Bildformat; es bietet eine gute Balance zwischen Dateigröße und Bildqualität. Bilder im JPEG-Format nutzen jedoch ein verlustbehaftetes Komprimierungsschema, das unerwünschte Bildartefakte hervorrufen kann, wenn die Komprimierungseinstellung zu niedrig ist. Aus diesem Grund empfiehlt Adobe, die Komprimierungsqualität auf 75 einzustellen. Diese Einstellung bietet einen angemessenen Ausgleich zwischen Bildqualität und kleiner Dateigröße.

* **[!UICONTROL Einfaches Scharfzeichnen aktivieren]**: Aktivieren Sie nicht die Option **[!UICONTROL Einfaches Scharfzeichnen aktivieren]** (dieser Scharfzeichnungsfilter bietet weniger Kontrolle als die Einstellungen für „Unschärfemaske“).

* **[!UICONTROL Scharfzeichnen: Resampling-Modus]**: Wählen Sie **[!UICONTROL Bikubisch.]**

#### Optionen auf der Registerkarte „Basis“ {#basic-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Feld</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Name</strong></td>
   <td>Geben Sie einen aussagekräftigen Namen ohne Leerzeichen ein. Nehmen Sie die Bildgröße in den Namen auf, damit Benutzer diese Bildvorgabe einfacher identifizieren können.</td>
  </tr>
  <tr>
   <td><strong>Breite und Höhe</strong></td>
   <td>Geben Sie die Größe in Pixel ein, in der das Bild übermittelt wird. Breite und Höhe müssen größer als 0 Pixel sein. Wenn einer der beiden Werte 0 ist, wird keine Vorgabe erstellt. Wenn beide Werte leer sind, wird eine responsive Bildvorgabe erstellt.</td>
  </tr>
  <tr>
   <td><strong>Format</strong></td>
   <td><p>Wählen Sie ein Format im Menü aus.</p> <p>Bei <strong>JPEG</strong> erhalten Sie die folgenden zusätzlichen Optionen:</p>
    <ul>
     <li><strong>Qualität</strong>: Steuert die JPEG-Komprimierungsstufe. Diese Einstellung wirkt sich sowohl auf die Dateigröße als auch auf die Bildqualität aus. Die JPEG-Qualitätsskala reicht von 1 bis 100. Die Skala ist sichtbar, wenn Sie den Schieberegler bewegen.</li>
     <li><strong>JPG-Chrominanz-Downsampling aktivieren</strong>: Da das menschliche Auge weniger empfindlich gegenüber hochfrequenten Farbinformationen als gegenüber hochfrequenter Luminanz ist, teilen JPEG-Bilder die Bildinformationen in Luminanz und Farbkomponenten. Wenn ein JPEG-Bild komprimiert wird, bleibt die Luminanzkomponente in der vollen Auflösung erhalten, während bei den Farbkomponenten ein Downsampling anhand einer Durchschnittsbildung von Pixelgruppen erfolgt. Beim Downsampling wird das Datenvolumen um die Hälfte oder ein Drittel reduziert, ohne dass dies entscheidende Auswirkungen auf die wahrgenommene Qualität hat. Downsampling kann nicht auf Graustufen-Bilder angewendet werden. Diese Technik reduziert den Komprimierungsgrad, was bei Bildern mit hohem Kontrast hilfreich ist (z. B. bei Bildern mit überlagertem Text).</li>
    </ul>
    <div>
      Bei Auswahl von <strong>GIF</strong> oder <strong>GIF mit Alpha</strong> werden die folgenden zusätzlichen Optionen für <strong>GIF-Farbquantisierung</strong> verfügbar:
    </div>
    <ul>
     <li><strong>Typ</strong>: Wählen Sie <strong>Adaptiv</strong> (Standard), <strong>Web</strong> oder <strong>Macintosh</strong>. Wenn Sie <strong>GIF mit Alpha</strong> auswählen, ist die Option „Macintosh“ nicht verfügbar.</li>
     <li><strong>Dithering</strong>: Wählen Sie <strong>Diffus</strong> oder <strong>Aus</strong>.</li>
     <li><strong>Anzahl Farben</strong>: Geben Sie eine Zahl zwischen 2 und 256 ein.</li>
     <li><strong>Farbliste</strong>: Geben Sie eine durch Komma getrennte Liste ein. Geben Sie beispielsweise für Weiß, Grau und Schwarz „000000,888888,ffffff“ ein.</li>
    </ul>
    <div>
      Bei Auswahl von
     <strong>PDF</strong>,
     <strong>TIFF</strong> oder
     <strong>TIFF mit Alpha</strong> erhalten Sie die folgende zusätzliche Option:
    </div>
    <ul>
     <li><strong>Komprimierung</strong>: Wählen Sie einen Komprimierungsalgorithmus. Die Algorithmusoptionen für PDF lauten <strong>Kein</strong>, <strong>ZIP</strong> und <strong>JPEG</strong>. Für TIFF lauten sie <strong>Kein</strong>, <strong>LZW</strong>, <strong>JPEG</strong> und <strong>ZIP</strong>. Für TIFF mit Alpha lauten sie <strong>Kein</strong>, <strong>LZW</strong> und <strong>ZIP</strong>.</li>
    </ul> <p>Die Auswahl <strong>PNG</strong>, <strong>PNG mit Alpha</strong> oder <strong>EPS</strong> ergibt keine zusätzlichen Optionen.</p> </td>
  </tr>
  <tr>
   <td><strong>Scharfzeichnen</strong></td>
   <td>Wählen Sie die Option <strong>Einfaches Scharfzeichnen aktivieren</strong>, um einen einfachen Scharfzeichnungsfilter auf das Bild anzuwenden, nachdem die Skalierung abgeschlossen wurde. Mit der Scharfzeichnung können Sie unter Umständen Weichzeichnung kaschieren, die durch die Anzeige eines Bildes in einer anderen Größe entsteht. </td>
  </tr>
 </tbody>
</table>

#### Optionen auf der Registerkarte „Erweitert“ {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Feld</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Farbraum</strong></td>
   <td>Wählen Sie <strong>RGB, CMYK</strong> oder <strong>Graustufen</strong> als Farbraum aus.</td>
  </tr>
  <tr>
   <td><strong>Farbprofil</strong></td>
   <td>Wählen Sie das Profil des Ausgabefarbraums aus, in den das Asset konvertiert werden soll, sofern dieser sich von dem des Arbeitsprofils unterscheidet.</td>
  </tr>
  <tr>
   <td><strong>Rendering-Intent</strong></td>
   <td>Sie können den Standardwert für Rendering-Intent überschreiben. Rendering-Intent legt fest, was mit Farben passiert, die im Farbprofil des Ziels nicht wiedergegeben werden können (außerhalb der Farbskala). Rendering-Intent wird ignoriert, wenn das ICC-Profil nicht kompatibel ist.
    <ul>
     <li>Wählen Sie <strong>Wahrnehmungsoptimiert</strong> aus, damit die gesamte Farbskala von einem Farbraum in einen anderen Farbraum komprimiert wird, wenn eine oder mehrere Farben im Originalbild außerhalb der Farbskala des Zielfarbraums liegen.</li>
     <li>Wählen Sie <strong>Relativ farbmetrisch</strong> aus, wenn eine Farbe des aktuellen Farbraums im Zielfarbraum außerhalb der Farbskala liegt und auf die nächstmögliche Farbe der Farbskala des Zielfarbraums abgebildet werden soll, ohne dass andere Farben betroffen sind. </li>
     <li>Wählen Sie <strong>Sättigung</strong> aus, um die Sättigung des Originalbilds beim Konvertieren in den Zielfarbraum zu übernehmen. </li>
     <li>Wählen Sie <strong>Absolut farbmetrisch</strong> aus, um Farben exakt und ohne Weißpunkt- oder Schwarzpunktanpassung abzubilden, wodurch die Helligkeit verändert würde.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Tiefenkompensierung</strong></td>
   <td>Wählen Sie diese Option aus, wenn das Ausgabeprofil diese Funktion unterstützt. Die Tiefenkompensierung wird ignoriert, wenn sie nicht mit dem angegebenen ICC-Profil kompatibel ist.</td>
  </tr>
  <tr>
   <td><strong>Dithering</strong></td>
   <td>Wählen Sie diese Option aus, um Farbstreifen-Artefakte möglichst zu vermeiden oder zu reduzieren. </td>
  </tr>
  <tr>
   <td><strong>Scharfzeichnungstyp</strong></td>
   <td><p>Wählen Sie <strong>Kein</strong>, <strong>Scharfzeichnen</strong> oder <strong>Unschärfemaske</strong> aus. </p>
    <ul>
     <li>Wählen Sie <strong>Kein</strong>, um die Scharfzeichnung zu deaktivieren.</li>
     <li>Aktivieren Sie <strong>Scharfzeichnen</strong>, um einen einfachen Scharfzeichnungsfilter auf das Bild anzuwenden, nachdem die Skalierung abgeschlossen ist. Mit der Scharfzeichnung können Sie unter Umständen Weichzeichnung kaschieren, die durch die Anzeige eines Bildes in einer anderen Größe entsteht. </li>
     <li>Wählen Sie <strong>Unschärfemaske</strong>, um einen Scharfzeichnungsfiltereffekt für das endgültige Bild nach dem Downsampling zu optimieren. Sie können die Intensität und den Radius des Effekts (in Pixel gemessen) sowie einen Kontrastschwellenwert, der ignoriert wird, steuern. Bei diesem Effekt werden dieselben Optionen wie im Filter „Unschärfemaske“ von Photoshop verwendet.</li>
    </ul> <p>In <strong>Unschärfemaske</strong> sind die folgenden Optionen verfügbar:</p>
    <ul>
     <li><strong>Betrag</strong>: Steuert den auf die Kantenpixel angewendeten Kontrastwert. Der Standardwert für die reelle Zahl ist 1,0. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5,0 erhöhen. Der Wert dient hierbei als ein Maß für die Filterintensität.</li>
     <li><strong>Radius</strong>: Bestimmt die Anzahl der Pixel um die Kantenpixel, die sich auf die Scharfzeichnung auswirken. Geben Sie für Bilder mit hoher Auflösung eine reelle Zahl zwischen 1 und 2 ein. Mit einem niedrigeren Wert werden nur die Kantenpixel scharfgezeichnet, während mit einem höheren Wert mehr Pixel scharfgezeichnet werden. Der korrekte Wert hängt von der Bildgröße ab.</li>
     <li><strong>Schwellenwert</strong>: Bestimmt den Kontrastbereich, der bei der Anwendung des Filters „Unschärfemaske“ ignoriert werden soll. In anderen Worten: Die Option bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und scharfgezeichnet werden. Um Rauschen zu vermeiden, experimentieren Sie mit Ganzzahlwerten zwischen 2 und 20. </li>
     <li><strong>Anwenden auf</strong>: Bestimmt, ob die Unscharfzeichnung für jede Farbe oder Helligkeit gilt.</li>
    </ul>
    <div>
      Das Scharfzeichnen wird unter
     <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/sharpening_images.pdf">Scharfzeichnen von Bildern</a> beschrieben.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Resampling-Modus</strong></td>
   <td>Wählen Sie eine Option für den <strong>Resampling-Modus</strong>. Diese Optionen sorgen dafür, dass das Bild beim Downsampling scharf bleibt:
    <ul>
     <li><strong>Bilinear</strong>: Die schnellste Resampling-Methode. Einige Aliasing-Artefakte sind sichtbar.</li>
     <li><strong>Bikubisch</strong>: Erhöht die CPU-Auslastung, bietet jedoch schärfere Bilder mit weniger deutlichen Aliasing-Artefakten.</li>
     <li><strong>Scharf2</strong>: Kann im Vergleich zu „Bikubisch“ etwas schärfere Ergebnisse erzeugen, ist jedoch CPU-intensiver.</li>
     <li><strong>Bi-Sharp</strong>: Wählt den Standard-Resampler in Photoshop zum Reduzieren der Bildgröße aus, was in Adobe Photoshop als <strong>bikubisch schärfer</strong> bezeichnet wird.</li>
     <li><strong>Jede Farbe</strong> und <strong>Helligkeit</strong>: Jede Methode kann auf Farbe oder Helligkeit basieren. Standardmäßig ist <strong>Jede Farbe</strong> ausgewählt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Druckauflösung</strong></td>
   <td>Wählen Sie eine Auflösung für den Druck dieses Bildes. Der Standardwert beträgt 72 Pixel.</td>
  </tr>
  <tr>
   <td><strong>Bildmodifikator</strong></td>
   <td><p>Neben den allgemeinen Bildeinstellungen in der Benutzeroberfläche unterstützt Dynamic Media zahlreiche erweiterte Bearbeitungsoptionen für Bilder, die Sie im Feld <strong>Bild-Modifikatoren</strong> festlegen können. Diese Parameter werden in der <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en#image-serving-api">Befehlsreferenz für das Image Server-Protokoll</a> definiert.</p> <p>Wichtig: Die folgenden in der API aufgelisteten Funktionen werden nicht unterstützt:</p>
    <ul>
     <li>Grundlegende Befehle zur Vorlagenerstellung und Textdarstellung: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> und <code>textPs=</code></li>
     <li>Lokalisierungsbefehle: <code>locale=</code> und <code>req=xlate</code></li>
     <li><code>req=set</code> ist nicht für die allgemeine Anwendung verfügbar.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Dynamic Media-Neben-Services: SVG, Rendering von Bildern und Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Definieren von Bildvorgabeoptionen mit Bildmodifikatoren {#defining-image-preset-options-with-image-modifiers}

Zusätzlich zu den auf den Registerkarten „Allgemein“ und „Erweitert“ verfügbaren Optionen können Sie Bildmodifikatoren definieren, damit Sie beim Definieren von Bildvorgaben über mehr Optionen verfügen. Das Image Rendering basiert auf der Image Rendering API, die im [HTTP Protocol Reference](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html#image-serving-api) detailliert definiert ist.

Im Folgenden finden Sie einige einfache Beispiele für die Nutzung von Bild-Modifikatoren.

>[!NOTE]
>
>Einige Bildmodifikatoren [können nicht in AEM verwendet werden](#advanced-tab-options).

* [op_invert](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html#image-serving-api): Invertiert jede Farbkomponente für einen negativen Bildeffekt.

   ```xml
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html#image-serving-api): Wendet einen Weichzeichenfilter auf das Bild an.

   ```xml
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Kombinierte Befehle - op_blur und op-invert

   ```xml
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [Op_brightness](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html#image-serving-api): Verringert oder erhöht die Helligkeit.

   ```xml
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html#image-serving-api): Passt die Bilddeckkraft an. Ermöglicht es Ihnen, die Vordergrunddeckkraft zu verringern.

   ```xml
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

## Bearbeiten von Bildvorgaben {#modifying-image-presets}

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools > Assets > Bildvorgaben.]**

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Wählen Sie eine Vorgabe aus und klicken Sie auf **[!UICONTROL Bearbeiten.]** Das Fenster **[!UICONTROL Bildvorgabe bearbeiten]** wird geöffnet.
1. Nehmen Sie Änderungen vor und klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern, oder auf **[!UICONTROL Abbrechen]**, um sie zu verwerfen.

## Veröffentlichen von Dynamic Media-Bildvorgaben {#publishing-image-presets}

Wenn Sie den Modus „Dynamic Media –Hybrid“ ausführen, müssen Sie Bildvorgaben manuell veröffentlichen.

(Wenn Sie den Modus „Dynamic Media – Scene7“ ausführen, werden Bildvorgaben automatisch veröffentlicht und Sie müssen diese Schritte nicht ausführen.)

**So veröffentlichen Sie Bildvorgaben im Dynamic Media-Hybridmodus**:

1. Tippen Sie AEM auf das AEM, um auf die globale Navigationskonsole zuzugreifen, klicken Sie auf das Symbol &quot;Werkzeuge&quot;und navigieren Sie zu **[!UICONTROL Assets > Bildvorgaben.]**
1. Wählen Sie in der Liste der Bildvorgaben eine oder mehrere Bildvorgaben aus und klicken oder tippen Sie auf **[!UICONTROL Veröffentlichen.]**
1. Nachdem die Bildvorgabe veröffentlicht wurde, ändert sich der Status von „Nicht veröffentlicht“ in „Veröffentlicht“.

   ![chlimage_1-81](assets/chlimage_1-505.png)

## Löschen von Dynamic Media-Bildvorgaben {#deleting-image-presets}

1. Tippen oder klicken Sie in AEM auf das AEM Logo, um auf die globale Navigationskonsole zuzugreifen.
1. Tippen Sie auf das Symbol **[!UICONTROL Tools]** und navigieren Sie dann zu **[!UICONTROL Assets > Bildvorgaben.]**
1. Wählen Sie eine Vorgabe aus und klicken Sie dann auf **[!UICONTROL Löschen]**. Dynamic Media bestätigt Ihre Löschabsicht. Tippen Sie auf **[!UICONTROL Löschen]**, um den Löschvorgang vorzunehmen, oder auf **[!UICONTROL Abbrechen]**, um den Vorgang abzubrechen.

