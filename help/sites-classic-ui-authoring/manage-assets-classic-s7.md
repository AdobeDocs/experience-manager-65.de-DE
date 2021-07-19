---
title: Hinzufügen von Dynamic Media Classic (Scene7)-Funktionen zu Ihrer Seite
description: Adobe Dynamic Media Classic (Scene7) ist eine gehostete Lösung für die Verwaltung, Erweiterung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, mobile, E-Mail- und Internet-verbundene Anzeigen und Drucken.
uuid: dc463e2d-a452-490e-88af-f79bdaa3b089
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dc0191d0-f181-4e1e-b3f4-73427aa22073
docset: aem65
exl-id: bc9c864b-8bc3-42b4-ba25-6c5108be4f65
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '3511'
ht-degree: 22%

---

# Hinzufügen von Dynamic Media Classic (Scene7)-Funktionen zu Ihrer Seite{#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic (Scene7) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html) ist eine gehostete Lösung für die Verwaltung, Erweiterung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobile-, E-Mail- und Internet-verbundene Anzeigen und Drucken.

Sie können in Dynamic Media Classic (Scene7) veröffentlichte Experience Manager-Assets in verschiedenen Viewern anzeigen:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Sie können digitale Assets direkt aus Experience Manager in Dynamic Media Classic (Scene7) veröffentlichen und digitale Assets aus Dynamic Media Classic (Scene7) in Experience Manager veröffentlichen.

In diesem Dokument wird beschrieben, wie Sie digitale Assets von Experience Manager in Dynamic Media Classic (Scene7) und umgekehrt veröffentlichen. Die Viewer werden auch detailliert beschrieben. Informationen zum Konfigurieren von Experience Manager für Dynamic Media Classic (Scene7) finden Sie unter [Integrieren von Dynamic Media Classic (Scene7) mit Experience Manager](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](/help/assets/image-maps.md).

Weitere Informationen zur Verwendung von Videokomponenten mit Experience Manager finden Sie unter folgenden Themen:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Wenn Dynamic Media Classic (Scene7)-Assets nicht ordnungsgemäß angezeigt werden, stellen Sie sicher, dass Dynamic Media [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) ist, und aktualisieren Sie dann die Seite.

## Manuelles Veröffentlichen in Dynamic Media Classic (Scene7) aus Assets {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets in Dynamic Media Classic (Scene7) entweder über die Konsole &quot;Assets&quot;in der klassischen Benutzeroberfläche oder direkt über das Asset veröffentlichen.

>[!NOTE]
>
>Experience Manager wird asynchron in Dynamic Media Classic (Scene7) veröffentlicht. Nachdem Sie **[!UICONTROL Publish]** ausgewählt haben, kann es mehrere Sekunden dauern, bis Ihr Asset in Dynamic Media Classic (Scene7) veröffentlicht wird.


### Veröffentlichen über die Asset-Konsole {#publishing-from-the-assets-console}

Sie können über die Assets-Konsole in Dynamic Media Classic (Scene7) veröffentlichen, wenn sich die Assets in einem Dynamic Media Classic (Scene7)-Zielordner befinden.

1. Wählen Sie in der klassischen Experience Manager-Benutzeroberfläche **[!UICONTROL Digitale Assets]** aus, um auf den Digital Asset Manager zuzugreifen.

1. Wählen Sie das Asset (oder die Assets) oder den Ordner aus dem Zielordner aus, den Sie in Dynamic Media Classic (Scene7) veröffentlichen möchten, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL In Dynamic Media Classic (Scene7) veröffentlichen]** aus. Alternativ können Sie **[!UICONTROL In Dynamic Media Classic (Scene7)]** veröffentlichen aus dem Menü **[!UICONTROL Tools]** auswählen.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Wechseln Sie zu Dynamic Media Classic (Scene7) und überprüfen Sie, ob die Assets verfügbar sind.

   >[!NOTE]
   >
   >Wenn sich die Assets nicht in einem synchronisierten Ordner von Dynamic Media Classic (Scene7) befinden, ist **[!UICONTROL In Dynamic Media Classic (Scene7) veröffentlichen]** in beiden Menüs sichtbar, aber deaktiviert.

### Veröffentlichen aus einem Asset {#publishing-from-an-asset}

Sie können ein Asset manuell veröffentlichen, solange sich dieses Asset im synchronisierten Ordner von Dynamic Media Classic (Scene7) befindet.

>[!NOTE]
>
>Wenn sich das Asset nicht im synchronisierten Ordner Dynamic Media Classic (Scene7) befindet, wird der Link zu **[!UICONTROL In Dynamic Media Classic (Scene7) veröffentlichen]** nicht angezeigt.

So veröffentlichen Sie direkt über ein digitales Asset in Dynamic Media Classic (Scene7):

1. Wählen Sie in Experience Manager **[!UICONTROL Digitale Assets]** aus, um auf den Digital Asset Manager zuzugreifen.

1. Doppelklicken Sie, um ein Asset zu öffnen.

1. Wählen Sie im Asset-Detailbereich **[!UICONTROL In Dynamic Media Classic (Scene7)]** veröffentlichen aus.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Der Link ändert sich zu **[!UICONTROL Wird veröffentlicht ...]** und dann zu **[!UICONTROL Veröffentlicht]**. Wechseln Sie zu Dynamic Media Classic (Scene7) und überprüfen Sie, ob das Asset verfügbar ist.

   >[!NOTE]
   >
   >Wenn das Asset nicht ordnungsgemäß in Dynamic Media Classic (Scene7) veröffentlicht wird, ändert sich der Link in **[!UICONTROL Veröffentlichung fehlgeschlagen]**. Wenn das Asset bereits in Dynamic Media Classic (Scene7) veröffentlicht wurde, lautet der Link **[!UICONTROL Erneut in Dynamic Media Classic (Scene7)]** veröffentlichen. Durch das erneute Veröffentlichen können Sie Assets in Experience Manager ändern und erneut veröffentlichen.

### Veröffentlichen von Assets außerhalb des CQ-Zielordners {#publishing-assets-from-outside-the-cq-target-folder}

Adobe empfiehlt, Assets nur aus Assets im Zielordner von Dynamic Media Classic (Scene7) in Dynamic Media Classic (Scene7) zu veröffentlichen. Wenn Sie jedoch Assets aus einem Ordner außerhalb des Zielordners hochladen müssen, können Sie dies dennoch tun, indem Sie sie in einen On-Demand-Ordner unter Dynamic Media Classic (Scene7) hochladen. Konfigurieren Sie zunächst die Cloud-Konfiguration für die Seite, auf der das Asset angezeigt werden soll. Anschließend fügen Sie eine Dynamic Media Classic (Scene7)-Komponente zur Seite hinzu und ziehen ein Asset per Drag-and-Drop auf die Komponente. Nachdem die Seiteneigenschaften für diese Seite festgelegt wurden, wird ein Link **[!UICONTROL In Dynamic Media Classic veröffentlichen (Scene7)]** angezeigt, der beim Hochladen auf Dynamic Media Classic (Scene7) auf ausgewählte Trigger erscheint.

>[!NOTE]
>
>Assets, die sich im Ordner &quot;On-Demand&quot;befinden, werden nicht im Inhaltsbrowser von Dynamic Media Classic (Scene7) angezeigt.

**So veröffentlichen Sie Assets außerhalb des CQ-Zielordners:**

1. Wählen Sie in Experience Manager in der klassischen Benutzeroberfläche **[!UICONTROL Websites]** aus und navigieren Sie zur Webseite, der Sie ein digitales Asset hinzufügen möchten, das noch nicht in Dynamic Media Classic (Scene7) veröffentlicht wurde. (Es gelten normale Seitenübernahmeregeln.)

1. Wählen Sie im Sidekick das Symbol **[!UICONTROL Seite]** und dann **[!UICONTROL Seiteneigenschaften]** aus.

1. Wählen Sie **[!UICONTROL Cloud Services]** aus.
1. Wählen Sie **[!UICONTROL Dienste hinzufügen]**.
1. Wählen Sie **[!UICONTROL Dynamic Media Classic (Scene7)]** aus.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Adobe Dynamic Media Classic (Scene7)]** die gewünschte Konfiguration aus und wählen Sie **[!UICONTROL OK]** aus.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Fügen Sie auf der Webseite eine Dynamic Media Classic (Scene7)-Komponente an der gewünschten Stelle auf der Seite hinzu.
1. Ziehen Sie in der Inhaltssuche ein digitales Asset zur Komponente. Es wird ein Link zu **[!UICONTROL Überprüfen des Veröffentlichungsstatus von Dynamic Media Classic (Scene7)]** angezeigt.

   >[!NOTE]
   >
   >Wenn sich das digitale Asset im CQ-Zielordner befindet, wird kein Link zu **[!UICONTROL Überprüfen des Veröffentlichungsstatus von Dynamic Media Classic (Scene7)]** angezeigt. Die Assets werden in der Komponente platziert.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Wählen Sie **[!UICONTROL Dynamic Media Classic (Scene7) Publishing Status]** aus. Wenn die Assets nicht veröffentlicht werden, veröffentlicht Experience Manager das Asset in Dynamic Media Classic (Scene7). Nach dem Hochladen befindet sich das Asset im Ordner &quot;On-Demand&quot;. Standardmäßig befindet sich der Ordner &quot;On-Demand&quot;im Ordner **[!UICONTROL name_of_the_company/CQ5_adhoc]**. Sie können den Ordner &quot;On-Demand&quot;bei Bedarf ](#configuringtheadhocfolder) konfigurieren.[

   >[!NOTE]
   >
   >Wenn sich das Asset nicht in einem synchronisierten Ordner von Dynamic Media Classic (Scene7) befindet und der aktuellen Seite keine Cloud-Konfiguration von Dynamic Media Classic (Scene7) zugeordnet ist, schlägt der Upload fehl.

## Komponenten von Dynamic Media Classic (Scene7) {#scene-components}

Die folgenden Dynamic Media Classic (Scene7)-Komponenten sind in Experience Manager verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen vor der Verwendung im Designmodus ausgewählt werden.

Nachdem sie im Designmodus verfügbar gemacht wurden, können Sie die Komponenten wie jede andere Experience Manager-Komponente zu Ihrer Seite hinzufügen. Assets, die noch nicht in Dynamic Media Classic (Scene7) veröffentlicht wurden, werden in Dynamic Media Classic (Scene7) veröffentlicht, wenn sie sich in einem synchronisierten Ordner, auf einer Seite oder mit einer Dynamic Media Classic (Scene7)-Cloud-Konfiguration befinden.

>[!NOTE]
>
>Wenn Sie benutzerdefinierte S7-Viewer erstellen und entwickeln und die Inhaltssuche verwenden, müssen Sie den Parameter `allowfullscreen` explizit hinzufügen.

### Hinweis zum End of Life von Flash-Viewern {#flash-viewers-end-of-life-notice}

Ab dem 31. Januar 2017 hat Adobe Dynamic Media Classic (Scene7) offiziell die Unterstützung für die Flash Viewer-Plattform beendet.

### Hinzufügen einer Dynamic Media Classic (Scene7)-Komponente zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Dynamic Media Classic (Scene7)-Komponente zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer beliebigen Seite. Die Komponenten von Dynamic Media Classic (Scene7) werden in den folgenden Abschnitten ausführlich beschrieben.

So fügen Sie einer Seite in der klassischen Benutzeroberfläche eine Komponente/einen Viewer für Dynamic Media Classic (Scene7) hinzu:

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Komponente Dynamic Media Classic (Scene7) hinzufügen möchten.

1. Wenn keine Dynamic Media Classic (Scene7)-Komponenten verfügbar sind, wählen Sie das Lineal im Sidekick aus, um in den Modus **Design** zu wechseln, wählen Sie **[!UICONTROL Bearbeiten]** parsys und wählen Sie alle Komponenten **[!UICONTROL Dynamic Media Classic (Scene7)]** aus, um sie verfügbar zu machen.

1. Kehren Sie zum Modus **Bearbeiten** zurück, indem Sie das Stiftsymbol im Sidekick auswählen.

1. Ziehen Sie eine Komponente aus der Gruppe **[!UICONTROL Dynamic Media Classic (Scene7)]** im Sidekick auf die Seite an der gewünschten Position.

1. Wählen Sie ***[!UICONTROL Bearbeiten]** aus, damit Sie die Komponente öffnen können.

1. Bearbeiten Sie die Komponente nach Bedarf und wählen Sie **[!UICONTROL OK]** aus, um Änderungen zu speichern.

### Hinzufügen interaktiver Anzeigeerlebnisse zu einer responsiven Website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Responsives Design für Ihre Assets bedeutet, dass sich Ihre Assets an den Ort anpassen, an dem sie angezeigt werden. Mithilfe des dynamischen Designs können dieselben Assets auf mehreren Geräten effektiv dargestellt werden.

So fügen Sie ein interaktives Anzeigeerlebnis zu einer dynamischen Website auf der klassischen Benutzeroberfläche hinzu:

1. Melden Sie sich bei Experience Manager an und stellen Sie sicher, dass Sie über [konfigurierte Cloud Services der Adobe Dynamic Media Classic (Scene7)](/help/sites-administering/scene7.md#configuring-scene-integration) verfügen und dass Dynamic Media Classic (Scene7)-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn die WCM-Komponenten von Dynamic Media Classic (Scene7) nicht verfügbar sind, stellen Sie sicher, dass Sie sie über den Designmodus aktivieren.

1. Ziehen Sie auf einer Website mit aktivierten Dynamic Media Classic-Komponenten (Scene7) einen Viewer **[!UICONTROL Bild]** auf die Seite.
1. Bearbeiten Sie die Komponente und passen Sie die Haltepunkte auf der Registerkarte **[!UICONTROL Dynamic Media Classic (Scene7) Settings]** an.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktopcomputer, Tablets und Mobilgeräte optimiert sind.

### Für alle Dynamic Media Classic (Scene7)-Komponenten gemeinsame Einstellungen {#settings-common-to-all-scene-components}

Obwohl die Konfigurationsoptionen variieren, gelten für alle Dynamic Media Classic (Scene7)-Komponenten folgende gemeinsame Optionen:

* **Dateiverweis**: Navigieren Sie zu einer Datei, die Sie referenzieren möchten. Der Dateiverweis zeigt die Asset-URL und nicht notwendigerweise die vollständige Dynamic Media Classic (Scene7)-URL, einschließlich der URL-Befehle und -Parameter. In diesem Feld können Sie keine URL-Befehle und -Parameter für Dynamic Media Classic (Scene7) hinzufügen. Stattdessen müssen sie über die entsprechende Funktionalität in der Komponente hinzugefügt werden.
* **Breite**: Hiermit kann die Breite angepasst werden.
* **Höhe**: Hiermit kann die Höhe angepasst werden.

Sie legen diese Konfigurationsoptionen fest, indem Sie eine Komponente von Dynamic Media Classic (Scene7) öffnen (durch Doppelklicken), z. B. beim Öffnen einer Komponente **Zoom**:

![chlimage_1-52](assets/chlimage_1-52.png)

### Zoom {#zoom}

Die HTML5 Zoom-Komponente zeigt ein größeres Bild an, wenn Sie die Taste „+“ drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Wählen Sie **[!UICONTROL +]** zum Vergrößern aus. Wählen Sie **[!UICONTROL -]** aus, um die Anzahl zu verringern. Wenn Sie **[!UICONTROL x]** oder den Pfeil zum Zurücksetzen des Zooms auswählen, wird das Bild wieder in der ursprünglichen Größe angezeigt, als es importiert wurde. Wählen Sie die diagonalen Pfeile aus, damit Sie den Vollbildmodus aktivieren können. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie die Komponente konfigurieren können. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die für alle Dynamic Media Classic (Scene7)-Komponenten](#settings-common-to-all-scene-components) gelten.

![](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In der HTML5 Flyout-Komponente wird das Asset als geteilter Bildschirm angezeigt. Links wird das Asset in der angegebenen Größe angezeigt, rechts wird der Zoomteil angezeigt. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie die Komponente konfigurieren können. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die für alle Dynamic Media Classic (Scene7)-Komponenten](/help/sites-administering/scene7.md#settingscommontoallscene7components) gelten.

>[!NOTE]
>
>Wenn die Flyout-Komponente eine benutzerdefinierte Größe aufweist, wird diese benutzerdefinierte Größe verwendet und die dynamische Einrichtung der Komponente ist deaktiviert.
>
>Wenn Ihre Flyout-Komponente die in der Designansicht festgelegte Standardgröße verwendet, wird die Standardgröße verwendet. Die Komponente erstreckt sich, um die Seitenlayoutgröße mit der responsiven Einrichtung der Komponente aufzunehmen. Beachten Sie jedoch, dass die responsive Einrichtung der Komponente eingeschränkt ist. Wenn Sie die Flyout-Komponente mit responsiven Einstellungen verwenden, sollten Sie sie nicht mit vollständiger Seitendehnung verwenden. Andernfalls kann das Flyout über den rechten Rand der Seite hinausgehen.

![chlimage_1-53](assets/chlimage_1-53.png)

### Bild {#image}

Mit der Bildkomponente Dynamic Media Classic (Scene7) können Sie Ihren Bildern Dynamic Media Classic (Scene7)-Funktionen hinzufügen, z. B. Dynamic Media Classic (Scene7)-Modifikatoren, Bild- oder Viewer-Vorgaben und Scharfzeichnen. Die Bildkomponente Dynamic Media Classic (Scene7) ähnelt anderen Bildkomponenten in Experience Manager mit speziellen Dynamic Media Classic (Scene7)-Funktionen. In diesem Beispiel wird auf das Bild der URL-Modifikator Dynamic Media Classic (Scene7), `&op_invert=1` angewendet.

![](do-not-localize/chlimage_1-4.png)

**Titel, ALT-Text**  - Fügen Sie auf der Registerkarte &quot;Erweitert&quot;einen Titel zum Bild und alternativen Text für die Benutzer hinzu, deren Grafiken deaktiviert sind.

**URL, Öffnen in**  - Sie können ein Asset von festlegen, um einen Link zu öffnen. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-54](assets/chlimage_1-54.png)

**Viewer-Vorgabe** : Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Viewer-Vorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**Dynamic Media Classic (Scene7)-Konfiguration**  - Wählen Sie die Dynamic Media Classic (Scene7)-Konfiguration aus, die Sie verwenden möchten, um aktive Bildvorgaben aus dem SPS abzurufen.

**Bildvorgabe** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Bildvorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**Ausgabeformat**  - Wählen Sie das Ausgabeformat des Bildes aus, z. B. jpeg. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen möglicherweise zusätzliche Konfigurationsoptionen zur Verfügung. Siehe Best Practices für Bildvorgaben.

**Scharfzeichnen**  - Wählen Sie aus, wie das Bild scharfgezeichnet werden soll. Das Scharfzeichnen wird unter Best Practices für Bildvorgaben und in den Best Practices für das Scharfzeichnen detailliert beschrieben.

**URL-Modifikatoren** : Sie können Bildeffekte ändern, indem Sie zusätzliche S7-Bildbefehle bereitstellen. Diese Befehle werden unter Bildvorgaben und in der Befehlsreferenz beschrieben.

**Haltepunkte**  - Wenn Ihre Website responsiv ist, möchten Sie die Haltepunkte anpassen. Haltepunkte müssen durch Kommas (,) voneinander getrennt werden.

### Bildvorlage {#image-template}

Dynamic Media Classic (Scene7)-Bildvorlagen sind Photoshop-Inhalte mit Ebenen, die in Dynamic Media Classic (Scene7) importiert wurden und in denen Inhalte und Eigenschaften für Variabilität parametrisiert wurden. Mit der Komponente **[!UICONTROL Bildvorlage]** können Sie Bilder importieren und den Text dynamisch in Experience Manager ändern. Zusätzlich können Sie die Komponente **[!UICONTROL Bildvorlage]** dahingehend konfigurieren, dass sie Werte aus dem Clientkontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Wählen Sie **[!UICONTROL Bearbeiten]** - aus, um die Komponente zu konfigurieren. Sie können [Einstellungen konfigurieren, die für alle Dynamic Media Classic (Scene7)-Komponenten](/help/sites-administering/scene7.md#settingscommontoallscene7components) und andere in diesem Abschnitt beschriebene Einstellungen gelten.

![chlimage_1-55](assets/chlimage_1-55.png)

**Dateiverweis, Breite, Höhe**  - Siehe  [Einstellungen, die für alle Dynamic Media Classic (Scene7)-Komponenten](/help/sites-administering/scene7.md#settingscommontoallscene7components) gelten.

>[!NOTE]
>
>Dynamic Media Classic (Scene7)-URL-Befehle und -Parameter können der Dateiverweis-URL nicht direkt hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **[!UICONTROL Parameter]** definiert werden.

**Titel, Alternativtext**  - Fügen Sie auf der Registerkarte &quot;Dynamic Media Classic (Scene7)-Bildvorlage&quot;einen Titel zum Bild und Alternativtext für die Benutzer hinzu, die Grafiken deaktiviert haben.

**URL, Öffnen in**  - Sie können ein Asset von festlegen, um einen Link zu öffnen. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-56](assets/chlimage_1-56.png)

**Parameterbereich**  - Beim Import eines Bildes werden die Parameter vorab mit Informationen aus dem Bild gefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Um den Text dynamisch zu ändern, geben Sie neuen Text in die Felder ein und wählen Sie **[!UICONTROL OK]** aus. In diesem Beispiel lautet der **Preis** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-58](assets/chlimage_1-58.png)

Der Text im Bild ändert sich. Sie können den Text wieder auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld **[!UICONTROL Zurücksetzen]** auswählen.

![chlimage_1-59](assets/chlimage_1-59.png)

#### Ändern Sie den Text, um den Wert eines Client-Kontextwerts widerzuspiegeln. {#changing-text-to-reflect-the-value-of-a-client-context-value}

Um ein Feld mit einem Client-Kontextwert zu verknüpfen, wählen Sie **[!UICONTROL Wählen Sie]** aus, um das Client-Kontextmenü zu öffnen, wählen Sie den Client-Kontext aus und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-60](assets/chlimage_1-60.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text wieder auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld **[!UICONTROL Zurücksetzen]** auswählen.

![chlimage_1-61](assets/chlimage_1-61.png)

#### Machen Sie die Bildvorlage Dynamic Media Classic (Scene7) zu einem Link {#making-the-scene-image-template-a-link}

Sie können die Bildvorlagenkomponente von Dynamic Media Classic (Scene7) zu einem anklickbaren Link machen.

1. Wählen Sie auf der Seite mit der Bildvorlagenkomponente Dynamic Media Classic (Scene7) **[!UICONTROL Bearbeiten]** aus.
1. Geben Sie im Feld **[!UICONTROL URL]** die URL ein, zu der Benutzer wechseln, wenn sie auf das Bild klicken. Wählen Sie im Feld **[!UICONTROL Öffnen in]** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Wählen Sie **[!UICONTROL OK]** aus.

### Komponente „Video“ {#video-component}

Die Komponente Dynamic Media Classic (Scene7) **[!UICONTROL Video]** (verfügbar im Abschnitt Dynamic Media Classic (Scene7) des Sidekicks) verwendet die Geräte- und Bandbreitenerkennung, um jedem Bildschirm das richtige Video bereitzustellen. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen zur Verwendung von Videos mit der Integration von Dynamic Media Classic (Scene7) finden Sie unter [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) . Sehen Sie sich außerdem an, wie die [Dynamic Media Classic (Scene7)-Komponente **mit der Foundation-Komponente** video **verglichen wird.**](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

![chlimage_1-63](assets/chlimage_1-63.png)

### Bekannte Einschränkungen für die Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen an, ob ein Primärvideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Dynamic Media Classic (Scene7)-kodierte Ausgabeformate
* Adaptive Dynamic Media Classic (Scene7)-Videosets

Bei Verwendung eines adaptiven Videosets mit der Dynamic Media Classic (Scene7)-Videokomponente muss die Größe der Komponente an die Abmessungen des Videos angepasst werden.

## Dynamic Media Classic (Scene7)-Inhaltsbrowser {#scene-content-browser}

Mit dem Inhaltsbrowser Dynamic Media Classic (Scene7) können Sie Inhalte aus Dynamic Media Classic (Scene7) direkt in Experience Manager anzeigen. Um auf den Inhaltsbrowser zuzugreifen, wählen Sie in der Inhaltssuche **Dynamic Media Classic (Scene7)** in der Touch-optimierten Benutzeroberfläche oder in der klassischen Benutzeroberfläche das Symbol **S7** aus. Die Funktionalität ist zwischen den beiden Benutzeroberflächen identisch.

Wenn mehrere Konfigurationen vorhanden sind, zeigt Experience Manager standardmäßig die Standardkonfiguration [a1/> an. ](/help/sites-administering/scene7.md#configuring-a-default-configuration) Sie können verschiedene Konfigurationen direkt im Inhaltsbrowser von Dynamic Media Classic (Scene7) im Dropdown-Menü auswählen.

>[!NOTE]
>
>* Assets im Ordner &quot;On-Demand&quot;werden nicht im Inhaltsbrowser von Dynamic Media Classic (Scene7) angezeigt.
>* Wenn [Sichere Vorschau aktiviert ist](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), werden sowohl veröffentlichte als auch nicht veröffentlichte Assets in Dynamic Media Classic (Scene7) im Inhaltsbrowser von Dynamic Media Classic (Scene7) angezeigt.
>* Wenn **[!UICONTROL Dynamic Media Classic (Scene7)]** oder das **[!UICONTROL S7]**-Symbol nicht als Option im Inhaltsbrowser angezeigt wird, müssen Sie [Dynamic Media Classic (Scene7) für die Verwendung mit Experience Manager](/help/sites-administering/scene7.md) konfigurieren.
>* Für Videos unterstützt der Inhaltsbrowser Dynamic Media Classic (Scene7) Folgendes:
   >   * Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
   >   * Einzelnes MP4-Video
   >   * Einzelnes F4V-Video


### Inhalt durchsuchen {#browsing-content-in-the-classic-ui}

Durchsuchen Sie Inhalte in Dynamic Media Classic (Scene7), indem Sie die Registerkarte **[!UICONTROL S7]** auswählen.

Sie können die Konfiguration, auf die Sie zugreifen, ändern, indem Sie die Konfiguration auswählen. Die Ordner ändern sich je nach ausgewählter Konfiguration.

![chlimage_1-64](assets/chlimage_1-64.png)

Wie mit der Inhaltssuche für Assets können Sie nach Assets suchen und Ergebnisse filtern. Im Gegensatz zur Asset-Suche **beginnt** der Dateiname jedoch beim Eingeben eines Keywords auf der Registerkarte **S7** mit dem von Ihnen eingegebenen String, anstatt dass das Keyword im Dateinamen **enthalten** ist.

Standardmäßig werden Assets nach Dateiname angezeigt. Sie können die Ergebnisse jedoch auch nach Asset-Typ filtern.

>[!NOTE]
>
>Für Videos unterstützt der Inhaltsbrowser von Dynamic Media Classic (Scene7) von WCM Folgendes:
>
>* Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
>* Einzelnes MP4-Video
>* Einzelnes F4V-Video

>



### Suchen Sie mit dem Inhaltsbrowser nach Dynamic Media Classic (Scene7)-Assets. {#searching-for-scene-assets-with-the-content-browser}

Die Suche nach Dynamic Media Classic (Scene7)-Assets ähnelt der Suche nach Experience Manager-Assets. Eine Ausnahme besteht darin, dass bei der Suche tatsächlich eine Remote-Ansicht der Assets im Dynamic Media Classic (Scene7)-System angezeigt wird, anstatt sie direkt in Experience Manager zu importieren.

Sie können die klassische oder Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. In Abhängigkeit von der Oberfläche unterscheidet sich die Art und Weise der Suche etwas.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**Keywords**  - Sie können Assets nach Namen suchen. Bei der Suche nach den Keywords geben Sie an, mit welchem Dateinamen sie beginnt. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Stellen Sie sicher, dass Sie nach der Eingabe des Begriffs &quot;Eingabe&quot;auswählen, um das Asset zu finden.

![chlimage_1-65](assets/chlimage_1-65.png)

**Ordner/Pfad**  - Der Name des Ordners basiert auf der von Ihnen ausgewählten Konfiguration. Sie können einen Drilldown in niedrigere Ebenen durchführen, indem Sie das Ordnersymbol auswählen, einen Unterordner auswählen und dann das Häkchen auswählen, um ihn auszuwählen.

Wenn Sie einen Suchbegriff eingeben und einen Ordner auswählen, durchsucht Experience Manager diesen und alle Unterordner. Wenn Sie bei der Suche jedoch keine Keywords eingeben, werden bei der Auswahl des Ordners nur die Assets in diesem Ordner angezeigt und keine Unterordner.

Standardmäßig durchsucht Experience Manager den ausgewählten Ordner und alle Unterordner.

![chlimage_1-66](assets/chlimage_1-66.png)

**Asset-Typ**  - Wählen Sie Dynamic Media Classic (Scene7) aus, um Dynamic Media Classic (Scene7)-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Dynamic Media Classic (Scene7) konfiguriert wurde.

![chlimage_1-67](assets/chlimage_1-67.png)

**Konfiguration**  - Wenn Sie in Cloud Services mehr als eine Dynamic Media Classic (Scene7)-Konfiguration definiert haben, können Sie sie hier auswählen. Daher ändert sich der Ordner je nach ausgewählter Konfiguration.

![chlimage_1-68](assets/chlimage_1-68.png)

**Asset-Typ**  - Im Browser Dynamic Media Classic (Scene7) können Sie die Ergebnisse filtern, um Folgendes einzuschließen: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Asset-Typ auswählen, durchsucht Experience Manager standardmäßig alle Asset-Typen.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>* Auf der klassischen Benutzeroberfläche können Sie auch nach **Flash** und **FXG** suchen. Das Filtern dieser beiden Begriffe in der Touch-optimierten Benutzeroberfläche wird nicht unterstützt.
   >
   >
* Beim Durchsuchen eines Videos suchen Sie nach einem einzelnen Ausgabeformat. Die Ergebnisse geben das ursprüngliche (nur *.mp4) und das kodierte Ausgabeformat zurück.
* Bei der Suche nach einem adaptiven Videoset durchsuchen Sie den Ordner und alle Unterordner, allerdings nur, wenn Sie der Suche ein Keyword hinzugefügt haben. Wenn Sie keinen Suchbegriff hinzugefügt haben, durchsucht Experience Manager die Unterordner nicht.



**Veröffentlichungsstatus**  - Sie können nach Assets basierend auf dem Veröffentlichungsstatus filtern: Veröffentlichung rückgängig gemacht oder veröffentlicht. Wenn Sie keinen Veröffentlichungsstatus auswählen, durchsucht Experience Manager standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-70](assets/chlimage_1-70.png)
