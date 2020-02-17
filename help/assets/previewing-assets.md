---
title: Asset-Vorschau
description: Erfahren Sie, wie Sie eine Vorschau von Assets in dynamischen Medien anzeigen können
uuid: 09e97245-373b-4d50-8ba3-5d1034a29988
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: bb8c355c-4475-45ec-9096-0975f0ce2c27
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Previewing assets{#previewing-assets}

Mit der Vorschau können Sie sehen, wie ein hochgeladenes digitales Asset aussieht, wenn es von einem Kunden in seinem eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabeformate von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/viewer-presets.md)

>[!NOTE]
>
>Auf einer Webseite (Sites) in AEM können Sie Assets im Modus **Bearbeiten** nicht in einer Vorschau anzeigen. Navigieren Sie in den **Vorschaumodus**, indem Sie in der oberen rechten Ecke auf **Vorschau** klicken.

To enable or disable viewer presets in the user interface, see [Managing Viewer Presets](/help/assets/managing-viewer-presets.md).

**So zeigen Sie die Asset-Vorschau an**

1. From **[!UICONTROL Adobe Experience Manager**, on the **[!UICONTROL Navigation** page, tap **[!UICONTROL Assets]**, then **[!UICONTROL Files]** to access assets.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL List View]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:

   <table>
    <tbody>
      <tr>
      <td><strong>Per Klick ausgewählter Asset-Typ</strong><br /> </td>
      <td><strong>Asset-Vorschau in bestimmtem Ausgabeformat möglich?</strong></td>
      <td><strong>Asset-Vorschau in bestimmtem Viewer möglich?</strong></td>
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
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li>
        </ul> <p>Wenn Sie eine Videowiedergabe mit höherer Auflösung für die Vorschau auswählen, wird das Video möglicherweise abgeschnitten angezeigt. Das liegt daran, dass die Vorschau der Darstellung die exakte Auflösung zeigt, die Ihre Kunden sehen werden, und zwar im Kontext des eingebetteten Viewers, der für die Vorschau verwendet wird.</p> <p>Wenn Sie eine Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Darstellungen in einem Wiedergabeerlebnis gruppiert. That is, the adaptive video is sized properly for viewing and played back using the best resolution in the context of your viewing device and connection speed.<br /> </p> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Sets für gemischte Medien</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Karussell-Set</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><strong>Asset-Vorschau in bestimmtem Viewer</strong>
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
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Originalzoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>
