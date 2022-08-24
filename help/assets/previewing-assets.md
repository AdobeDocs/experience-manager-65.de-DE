---
title: Anzeigen einer Vorschau für Assets
description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
uuid: 09e97245-373b-4d50-8ba3-5d1034a29988
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: bb8c355c-4475-45ec-9096-0975f0ce2c27
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 84f0c406-4ab6-48c7-8223-61a8c3ade363
source-git-commit: 363e5159d290ecfbf4338f6b9793e11b613389a5
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 67%

---

# Asset-Vorschau über die Software-Oberfläche {#previewing-assets}

Mit der Vorschau können Sie prüfen, wie ein von Ihnen hochgeladenes digitales Asset aussieht, wenn es von einem Kunden im eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung verschiedener Einstellungen oder *Vorgaben*, wie die Anzeigegröße des Viewers, das Zoomverhalten, Farbschemata, Rahmen und Schriftarten. Diese Vorgaben bestimmen, wie Benutzer Rich-Media-Assets auf ihren Computer-Bildschirmen und Mobilgeräten anzeigen.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabedarstellungen von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/viewer-presets.md)

>[!NOTE]
>
>Wenn Sie sich auf einer Web-Seite (Sites) in Adobe Experience Manager befinden, können Sie Assets im **Bearbeitungsmodus** nicht in der Vorschau anzeigen. Wechseln Sie zum Vorschaumodus, indem Sie auf **[!UICONTROL Vorschau]** in der oberen rechten Ecke der Seite.

Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie unter [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

**So zeigen Sie eine Vorschau von Assets über die Software-Oberfläche an:**

1. Von **[!UICONTROL Adobe Experience Manager]** auf **[!UICONTROL Navigation]** Seite, wählen Sie **[!UICONTROL Assets]**, dann **[!UICONTROL Dateien]** , um auf Assets zuzugreifen.
1. Wählen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** die Option **[!UICONTROL Listenansicht]** aus.
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
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus und wählen Sie dann den Dimensional-Viewer aus.</li>
      <li>Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.</li>
      <li>Auswählen <strong>Vollbild</strong> , um den Viewer auf dem Anzeigegerät zu maximieren.</li>
      </ul>
      <p><strong>Navigieren in der 3D-Szene</strong></p>
      <ul>
      <li><p><strong>3D-Kamera drehen</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Klicken und ziehen Sie mit der linken Maustaste </p> Touchscreen: Drücken und ziehen Sie</p></li>
      <li><p><strong>Kamera schwenken</strong>: Schwenken Sie die Ansicht nach links, rechts, oben und unten.</p> Maus: Klicken und ziehen Sie mit der rechten Maustaste </p> Touchscreen: Drücken und ziehen Sie mit zwei Fingern</p></li>
      <li><p><strong>Kamera zoomen</strong> - Zoomen Sie Ihre Kamera, damit Sie sich in Bereiche der 3D-Szene hinein- und ausbewegen können.</p> Maus: Scrollen Sie mit dem Mausrad </p> Touchscreen: Führen Sie mit den Fingern Pinch-Gesten aus</p></li>
      <li><p><strong>Kamera neu zentrieren</strong>: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.</p> Maus: Doppelklicken Sie </p> Touchscreen: Doppeltippen</li></ul></td>
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
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die <strong>+</strong> und <strong>-</strong> Symbole zum Vergrößern bzw. Verkleinern des ausgewählten Bildes. Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmter Ausgabedarstellung</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabedarstellungen</strong> und wählen Sie dann die Ausgabedarstellung, die Sie in einer Vorschau anzeigen möchten.</li>
      </ul> <p>Wenn Sie eine Videoausgabedarstellung mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Das Problem besteht darin, dass die Vorschau der Ausgabedarstellung die genaue Auflösung anzeigt, die Ihre Kunden im Kontext des eingebetteten Viewers sehen, der für die Vorschau verwendet wird.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabedarstellungen in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die <strong>+</strong> und <strong>-</strong> -Symbole, sodass Sie den Zoom des ausgewählten Bildes erhöhen oder verringern können. Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die <strong>+</strong> und <strong>-</strong> Symbole zum Vergrößern bzw. Verkleinern des ausgewählten Bildes. Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Sets für gemischte Medien</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdown-Liste angezeigt wird. Wählen Sie in der Liste <strong>Viewer</strong> aus. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die <strong>+</strong> und <strong>-</strong> Symbole zum Vergrößern bzw. Verkleinern des ausgewählten Bildes. Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
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
      <li>Klicken Sie oben links auf der Seite auf das Symbol, sodass die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Ausgabedarstellungen</strong> und dann die Ausgabedarstellung aus, die Sie in der Vorschau anzeigen möchten.</li>
      </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
      <ul>
      <li>Klicken Sie oben links auf der Seite auf das Symbol, sodass die Dropdown-Liste angezeigt wird. Wählen Sie <strong>Viewer</strong> und dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
      </ul> <p>Verwenden Sie die <strong>+</strong> und <strong>-</strong> Symbole zum Vergrößern bzw. Verkleinern des ausgewählten Bildes. Auswählen <strong>Zurücksetzen</strong> , wenn Sie das Bild zum ursprünglichen Zoom zurückführen möchten.<br /> Mit einem Touchscreen können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>

## Asset-Vorschau über eine Tastatur {#keyboard-navigation-asset-preview}

1. Navigieren Sie in der Assets-Benutzeroberfläche zu einem Ordner, der ein Asset enthält, das Sie in der Vorschau anzeigen möchten.

1. Drücken Sie im Ordner die `<Tab>` Taste oder Pfeiltasten auf der Tastatur, um das Asset auszuwählen.

1. Presse `<Enter>` damit Sie das ausgewählte Asset im Vorschaumodus öffnen können.

1. Führen Sie einen der folgenden Schritte aus:

   * Drücken Sie zum Einzoomen die Eingabetaste. `<Tab>` , um den Fokus auf das Zoom-Symbol (+) zu verschieben, und drücken Sie dann die `<Enter>` eine oder mehrere Male, um schrittweise einzuzoomen.
   * Um auszuzoomen, drücken Sie die `<Tab>` , um den Fokus auf das Symbol zum Verkleinern (-) zu verschieben, und drücken Sie dann die `<Enter>` eine oder mehrere Male, um schrittweise auszuzoomen.
   * So verschieben Sie die Ansicht eines *gezoomt* Assets horizontal oder vertikal anzeigen, drücken Sie die entsprechenden Pfeiltasten.
   * Presse `<Shift>` + `<Tab>` sodass Sie die Ansicht zurücksetzen und den Fokus wieder auf das Asset legen können.
