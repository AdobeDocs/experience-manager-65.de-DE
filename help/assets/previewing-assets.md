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
feature: Asset-Verwaltung
role: Business Practitioner, Administrator
exl-id: 84f0c406-4ab6-48c7-8223-61a8c3ade363
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1346'
ht-degree: 83%

---

# Vorschau von Assets über die Software-Oberfläche {#previewing-assets}

Mit der Vorschau können Sie prüfen, wie ein von Ihnen hochgeladenes digitales Asset aussieht, wenn es von einem Kunden im eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabedarstellungen von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Web-Seite (Sites) in AEM befinden, können Sie keine Asset-Vorschau im **Bearbeitungsmodus** anzeigen. Sie müssen in den **Vorschaumodus** wechseln, indem Sie oben rechts auf der Seite auf **Vorschau** klicken.

Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

**Vorschau von Assets über die Software-Oberfläche anzeigen**

1. Tippen Sie in **[!UICONTROL Adobe Experience Manager]** auf der **[!UICONTROL Navigationsseite]** auf **[!UICONTROL Assets]** und dann auf **[!UICONTROL Dateien]**, um auf Assets zuzugreifen.
1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Listenansicht.]**
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:


   <table>
    <tbody>
      <tr>
      <td><strong>Per Klick ausgewählter Asset-Typ</strong><br /> </td>
      <td><strong>Asset-Vorschau in bestimmter Ausgabedarstellung möglich?</strong></td>
      <td><strong>Asset-Vorschau in einem Viewer möglich?</strong></td>
      <td> </td>
      </tr>
      <tr>
      <td><p>3D</p> </td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines 3D-Assets im Dimensional-Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong> und wählen Sie dann den Dimensional-Viewer aus.</li>
      <li>Tippen Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.</li>
      <li>Tippen Sie auf <strong>Vollbild</strong>, um den Viewer auf dem Anzeigegerät zu maximieren.</li>
      </ul>
      <p><strong>Navigieren in der 3D-Szene</strong></p>
      <ul>
      <li><p><strong>3D-Kamera drehen</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Klicken und ziehen Sie mit der linken Maustaste. </p> Touchscreen: Drücken und ziehen Sie.</p></li>
      <li><p><strong>Kamera schwenken</strong>: Schwenken Sie die Ansicht nach links, rechts, oben und unten.</p> Maus: Klicken und ziehen Sie mit der rechten Maustaste. </p> Touchscreen: Drücken und ziehen Sie mit zwei Fingern.</p></li>
      <li><p><strong>Kamera zoomen</strong>: Zoomen Sie Ihre Kamera, um sich in Bereiche in der 3D-Szene hinein- und herauszubewegen.</p> Maus: Scrollen Sie mit dem Mausrad. </p> Touchscreen: Führen Sie mit den Fingern Pinch-Gesten aus.</p></li>
      <li><p><strong>Kamera neu zentrieren</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Doppelklicken Sie. </p> Touchscreen: Doppeltippen Sie.</li></ul></td>
      </tr>
      <tr>
      <td><p>Bild</p> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die Symbole <strong>+</strong> und <strong>-</strong>, um den Zoom des ausgewählten Bildes zu erhöhen bzw. zu verringern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p>Wenn Sie eine Videoausgabedarstellung mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Dies liegt daran, dass in der Vorschau der Ausgabedarstellung die genaue Auflösung angezeigt wird, die auch die Kunden sehen, und zwar im Kontext des eingebetteten Viewers, über den die Vorschau erfolgt.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabedarstellungen in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die Symbole <strong>+</strong> und <strong>-</strong>, um den Zoom des ausgewählten Bildes zu erhöhen bzw. zu verringern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die Symbole <strong>+</strong> und <strong>-</strong>, um den Zoom des ausgewählten Bildes zu erhöhen bzw. zu verringern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Sets für gemischte Medien</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die Symbole <strong>+</strong> und <strong>-</strong>, um den Zoom des ausgewählten Bildes zu erhöhen bzw. zu verringern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Karussellset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>360-Grad-Video<br /> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Ausgabedarstellungen</strong> und dann die Ausgabedarstellung aus, die Sie in der Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Viewer</strong> und dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die Symbole <strong>+</strong> und <strong>-</strong>, um den Zoom des ausgewählten Bildes zu erhöhen bzw. zu verringern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>

## Vorschau von Assets mit einer Tastatur {#keyboard-navigation-asset-preview}

1. Navigieren Sie in der Assets-Benutzeroberfläche zu einem Ordner, der ein Asset enthält, das Sie in der Vorschau anzeigen möchten.

1. Drücken Sie im Ordner die `<Tab>` -Taste oder -Pfeiltasten auf Ihrer Tastatur, um das Asset auszuwählen.

1. Drücken Sie `<Enter>`, um das ausgewählte Asset im Vorschaumodus zu öffnen.

1. Führen Sie einen der folgenden Schritte aus:

   * Drücken Sie zum Vergrößern die Taste `<Tab>`, um den Fokus auf das Symbol zum Vergrößern (+) zu verschieben, und drücken Sie dann `<Enter>` ein oder mehrere Male, um schrittweise einzuzoomen.

   * Um auszuzoomen, drücken Sie `<Tab>`, um den Fokus auf das Symbol zum Auszoomen (-) zu verschieben, und drücken Sie dann `<Enter>` ein oder mehrere Male, um schrittweise herauszuzoomen.

   * Um die Ansicht eines *gezoomten*-Assets horizontal oder vertikal zu verschieben, drücken Sie die entsprechenden Pfeiltasten.

   * Drücken Sie `<Shift>` + `<Tab>` , um die Ansicht zurückzusetzen und den Fokus wieder auf das Asset zu legen.
