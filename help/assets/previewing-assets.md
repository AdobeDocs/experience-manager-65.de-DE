---
title: Anzeigen von Assets in einer Vorschau
description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
uuid: 09e97245-373b-4d50-8ba3-5d1034a29988
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: bb8c355c-4475-45ec-9096-0975f0ce2c27
docset: aem65
translation-type: tm+mt
source-git-commit: 9e6aba1f511754080305c0a97ce9bc85511f29a7
workflow-type: tm+mt
source-wordcount: '1346'
ht-degree: 68%

---


# Anzeigen einer Asset-Vorschau über die Software-Benutzeroberfläche {#previewing-assets}

Mit der Vorschau können Sie prüfen, wie ein von Ihnen hochgeladenes digitales Asset aussieht, wenn es von einem Kunden im eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabeformate von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Webseite (Sites) in AEM befinden, können Sie keine Asset-Vorschau im **Bearbeitungsmodus** anzeigen. You need to go to **Preview** mode by clicking **Preview** in the upper right-hand corner of the page.

Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

**So erstellen Sie eine Vorschau von Assets über die Softwareoberfläche**

1. Tippen Sie in **Adobe Experience Manager** auf der Seite **Navigation** auf **[!UICONTROL Assets]** und **[!UICONTROL Dateien]**, um auf Assets zuzugreifen.
1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Listenansicht]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:


   <table>
    <tbody>
      <tr>
      <td><strong>Per Klick ausgewählter Asset-Typ</strong><br /> </td>
      <td><strong>Asset-Vorschau in bestimmtem Ausgabeformat möglich?</strong></td>
      <td><strong>Kann Asset in einem Viewer Vorschau werden?</strong></td>
      <td> </td>
      </tr>
      <tr>
      <td><p>3D</p> </td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>So erstellen Sie eine Vorschau eines 3D-Assets im Dimensions-Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong> und wählen Sie dann den Dimensions-Viewer aus.</li>
      <li>Tap <strong>Reset</strong> to return the image to the original zoom.</li>
      <li>Tippen Sie auf <strong>Vollbild</strong> , um den Viewer auf dem Anzeigegerät zu maximieren.</li>
      </ul>
      <p><strong>Navigieren in der 3D-Szene</strong></p>
      <ul>
      <li><p><strong>Drehen Sie Ihre 3D-Kamera</strong> - Drehen Sie Ihre Ansicht um die 3D-Szene und -Objekte.</p> Maus: Klicken Sie mit der linken Maustaste und ziehen Sie. </p> TouchScreen: Drücken Sie + Ziehen.</p></li>
      <li><p><strong>Schwenken Sie Ihre Ansicht</strong> - Drehen Sie sie nach links, rechts, oben und unten.</p> Maus: Rechtsklick + Ziehen. </p> TouchScreen: Drücken Sie die Zwei-Finger-Taste und ziehen Sie.</p></li>
      <li><p><strong>Zoomen Sie Ihre Kamera</strong> - Zoomen Sie Ihre Kamera, um sich in den Bereichen der 3D-Szene zu bewegen.</p> Maus: Scrollen Sie mit dem Mausrad. </p> TouchScreen: Finger-Pinch.</p></li>
      <li><p><strong>Setzen Sie Ihre Kamera</strong> neu ein - Richten Sie Ihre Ansicht um die 3D-Szene und -Objekte.</p> Maus: Doppelklicken Sie. </p> TouchScreen: Tippen Sie auf Dublette.</li></ul></td>
      </tr>
      <tr>
      <td><p>Bild</p> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Use the <strong>+</strong> and <strong>–</strong> icons to increase or decrease the zoom of the selected image, respectively. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Wenn Sie sich auf einem Touchscreen befinden, tippen Sie mit der Dublette schrittweise auf das Bild, um es einzuzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p>Wenn Sie ein Videoausgabeformat mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Dies liegt daran, dass in der Vorschau des Ausgabeformats die genaue Auflösung angezeigt wird, die auch die Kunden sehen, und zwar im Kontext des eingebetteten Viewers, über den die Vorschau erfolgt.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabeformate in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Use the <strong>+</strong> and <strong>–</strong> icons to increase or decrease the zoom of the selected image, respectively. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Wenn Sie sich auf einem Touchscreen befinden, tippen Sie mit der Dublette schrittweise auf das Bild, um es einzuzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Use the <strong>+</strong> and <strong>–</strong> icons to increase or decrease the zoom of the selected image, respectively. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Wenn Sie sich auf einem Touchscreen befinden, tippen Sie mit der Dublette schrittweise auf das Bild, um es einzuzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Sets für gemischte Medien</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Use the <strong>+</strong> and <strong>–</strong> icons to increase or decrease the zoom of the selected image, respectively. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Wenn Sie sich auf einem Touchscreen befinden, tippen Sie mit der Dublette schrittweise auf das Bild, um es einzuzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Karussell-Set</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>360-Grad-Video<br /> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
      <ul>
      <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie <strong>Ausgabeformate</strong> und dann das Ausgabeformat aus, das Sie in der Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie <strong>Viewer</strong> und dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Use the <strong>+</strong> and <strong>–</strong> icons to increase or decrease the zoom of the selected image, respectively. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Wenn Sie sich auf einem Touchscreen befinden, tippen Sie mit der Dublette schrittweise auf das Bild, um es einzuzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>

## Anzeigen einer Asset-Vorschau mit einer Tastatur {#keyboard-navigation-asset-preview}

1. Navigieren Sie in der Benutzeroberfläche &quot;Assets&quot;zu einem Ordner, der ein Asset enthält, das Sie Vorschau haben möchten.

1. Drücken Sie im Ordner die `<Tab>` Taste oder die Pfeiltasten auf der Tastatur, um das Asset auszuwählen.

1. Drücken Sie `<Enter>` die Eingabetaste, um das ausgewählte Asset im Modus &quot;Vorschau&quot;zu öffnen.

1. Führen Sie einen der folgenden Schritte aus:

   * Um einzuzoomen, drücken Sie `<Tab>` die Eingabetaste, um den Fokus auf das Symbol für das Einzoomen (+) zu verschieben, und drücken Sie dann `<Enter>` mindestens ein Mal, um den Zoom inkrementell durchzuführen.

   * Um die Ansicht zu verkleinern, drücken Sie `<Tab>` die Eingabetaste, um den Fokus auf das Symbol zum Auszoomen (-) zu verschieben, und drücken Sie dann `<Enter>` mindestens ein Mal, um den Zoom schrittweise auszuzoomen.

   * Um die Ansicht eines *gezoomten* Assets horizontal oder vertikal zu verschieben, drücken Sie die entsprechenden Pfeiltasten.

   * Drücken Sie `<Shift>` + `<Tab>` , um die Ansicht zurückzusetzen und den Fokus wieder auf das Asset zu legen.
