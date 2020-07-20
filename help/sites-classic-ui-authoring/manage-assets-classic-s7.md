---
title: Hinzufügen von Scene7-Features zu Ihrer Seite
seo-title: Hinzufügen von Scene7-Features zu Ihrer Seite
description: Adobe Scene7 ist eine gehostete Lösung für das Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Ressourcen für das Web, für Mobilgeräte, für E-Mails, für mit dem Internet verbundene Anzeigen und für den Druck.
seo-description: Adobe Scene7 ist eine gehostete Lösung für das Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Ressourcen für das Web, für Mobilgeräte, für E-Mails, für mit dem Internet verbundene Anzeigen und für den Druck.
uuid: dc463e2d-a452-490e-88af-f79bdaa3b089
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dc0191d0-f181-4e1e-b3f4-73427aa22073
docset: aem65
translation-type: tm+mt
source-git-commit: eb5ec39431d365ed6ba274018bbca437a58bfafe
workflow-type: tm+mt
source-wordcount: '3221'
ht-degree: 77%

---


# Hinzufügen von Scene7-Features zu Ihrer Seite{#adding-scene-features-to-your-page}

[Adobe Scene7](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) ist eine gehostete Lösung für das Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Ressourcen für das Web, für Mobilgeräte, E-Mails, für mit dem Internet verbundene Anzeigen und für den Druck.

Die in Scene7 veröffentlichten AEM-Assets können in verschiedenen Viewern angezeigt werden:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Digitale Assets können direkt über AEM in Scene7 veröffentlicht werden und umgekehrt.

Dieses Dokument beschreibt, wie digitale Assets von AEM in Scene7 und umgekehrt veröffentlicht werden. Die Viewer werden auch detailliert beschrieben. Informationen über das Konfigurieren von AEM für Scene7 finden Sie unter [Integrieren von Scene7 in AEM](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](/help/assets/image-maps.md).

Weitere Informationen über die Arbeit mit Videokomponenten mit AEM finden Sie unter:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>If Scene7 assets do not display properly, please make sure that Dynamic media is [disabled](/help/assets/config-dynamic.md#disabling-dynamic-media) and then refresh the page.

## Manuelles Veröffentlichen über Assets in Scene7 {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets über die Konsole „Assets“ auf der klassischen Benutzeroberfläche oder direkt über das Asset in Scene7 veröffentlichen.

>[!NOTE]
>
>AEM nimmt die Veröffentlichung in Scene7 auf asynchrone Weise vor. Nachdem Sie auf **Veröffentlichen** geklickt haben, dauert es möglicherweise ein paar Sekunden, bis das Asset in Scene7 veröffentlicht wird.


### Veröffentlichen über die Asset-Konsole {#publishing-from-the-assets-console}

So veröffentlichen Sie über die Konsole „Assets“ in Scene7, wenn sich die Assets in einem Scene7-Zielordner befinden:

1. In the AEM classic UI, click **Digital Assets** to access the digital asset manager.

1. Wählen Sie das Asset (oder die Assets) oder den Ordner innerhalb des Zielordners aus, den Sie in Scene7 veröffentlichen möchten, klicken Sie dann mit der rechten Maustaste und wählen Sie **In Scene7 veröffentlichen** aus. Alternativ können Sie **In Scene7 veröffentlichen** über das Menü **Tools auswählen**.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Wechseln Sie zu Scene7 und überprüfen Sie, ob die Assets verfügbar sind.

   >[!NOTE]
   >
   >Wenn sich die Assets nicht in einem Scene7-synchronisierten Ordner befinden, ist **In Scene7 veröffentlichen** zwar in beiden Menüs sichtbar, aber deaktiviert.

### Veröffentlichen über ein Asset {#publishing-from-an-asset}

Sie können ein Asset manuell veröffentlichen, sofern sich dieses Asset im synchronisierten Scene7-Ordner befindet.

>[!NOTE]
>
>Wenn sich das Asset nicht im Scene7-synchronisierten Ordner befindet, wird der Link **In Scene7 veröffentlichen** nicht angezeigt.

So veröffentlichen Sie direkt über ein digitales Asset in Scene7:

1. Klicken Sie in AEM auf **Digitale Assets**, um auf den Digital Asset Manager zuzugreifen.

1. Doppelklicken Sie, um ein Asset zu öffnen.

1. Wählen Sie im Asset-Detailbereich **In Scene7 veröffentlichen** aus.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. Der Link ändert sich zu **Wird veröffentlicht ...** und dann zu **Veröffentlicht**. Wechseln Sie zu Scene7 und überprüfen Sie, ob das Asset verfügbar ist.

   >[!NOTE]
   >
   >Wenn das Asset nicht ordnungsgemäß in Scene7 veröffentlicht wurde, wird der Link zu **Veröffentlichung fehlgeschlagen** geändert. Wenn das Asset bereits in Scene7 veröffentlicht wurde, lautet der Link **Erneut in Scene7 veröffentlichen**. Durch das erneute Veröffentlichen können Sie Änderungen an einem Asset in AEM vornehmen und eine erneute Veröffentlichung vornehmen.

### Veröffentlichen von Assets außerhalb des CQ-Zielordners {#publishing-assets-from-outside-the-cq-target-folder}

Adobe empfiehlt, dass Sie Assets nur über die im Scene7-Zielordner befindlichen Assets in Scene7 veröffentlichen. However, if you need to upload assets from a folder outside of the target folder, you can still do that by uploading them to an **ad-hoc** folder on Scene7.

Dafür müssen Sie zunächst die Cloud-Konfiguration für die Seite konfigurieren, auf der das Asset angezeigt wird. Anschließend fügen Sie der Seite eine Scene7-Komponente hinzu, ziehen ein Asset und legen es auf der Komponente ab. After the page properties are set for that page, a **Publish to Scene7** link appears that when selected triggers uploading to Scene7.

>[!NOTE]
>
>Im Ad-hoc-Ordner befindliche Assets werden im Scene7-Inhaltsbrowser nicht angezeigt.

So veröffentlichen Sie außerhalb des CQ-Zielordners befindliche Assets:

1. Klicken Sie in AEM auf der klassischen Benutzeroberfläche auf **Websites** und navigieren Sie zur Webseite, zu der Sie ein digitales Asset hinzufügen möchten, das bisher noch nicht in Scene7 veröffentlicht wurde. (Es gelten normale Seitenübernahmeregeln.)

1. Klicken Sie im Sidekick auf das Symbol **Seite** und klicken Sie auf **Seiteneigenschaften**.

1. Klicken Sie auf **Cloud-Services**, klicken Sie auf **Service hinzufügen** und wählen Sie **Scene7** aus.
1. Wählen Sie in der Dropdown-Liste **Adobe Scene7** die gewünschte Konfiguration aus und klicken Sie auf **OK**.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Fügen Sie auf der Webseite eine Scene7-Komponente zur gewünschten Position auf der Seite hinzu.
1. Ziehen Sie in der Inhaltssuche ein digitales Asset zur Komponente. Es wird ein Link zur **Prüfung des Scene7-Veröffentlichungsstatus** angezeigt.

   >[!NOTE]
   >
   >If the digital asset is in the CQ target folder, then no link to **Check Scene7 Publication Status** appears. Die Assets werden einfach in der Komponente platziert.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Klicken Sie auf die Option zum Prüfen des Scene7-Veröffentlichungsstatus. **** Wenn die Assets unveröffentlicht sind, veröffentlicht AEM das Asset in Scene7. Nach dem Upload befindet sich das Asset im Ad-hoc-Ordner. Standardmäßig befindet sich der Ad-hoc-Ordner unter **Name_des_Unternehmens/CQ5_adhoc**. Sie können dies [bei Bedarf konfigurieren](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Wenn sich das Asset nicht in einem Scene7-synchronisierten Ordner befindet und keine Scene7-Cloud-Konfiguration mit der aktuellen Seite verknüpft ist, ist der Upload fehlerhaft.

## Scene7-Komponenten {#scene-components}

Die folgenden Scene7-Komponenten sind in AEM verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen im Designmodus ausgewählt werden, bevor sie verwendet werden können.

Nachdem sie im Designmodus zur Verfügung gestellt wurden, können Sie Komponenten zu Ihrer Seite wie jede andere AEM-Komponente hinzufügen. Noch nicht in Scene7 veröffentlichte Assets werden in Scene7 in einem synchronisierten Ordner oder auf einer Seite oder mit einer Scene7-Cloud-Konfiguration veröffentlicht.

>[!NOTE]
>
>If you are creating and developing custom S7 viewers and using the Content Finder, you need to explicity add the **allowfullscreen** parameter.

### Hinweis zur Einstellung von Flash-Viewer {#flash-viewers-end-of-life-notice}

Mit Wirkung vom 31. Januar 2017 wird die Flash-Viewer-Plattform nicht mehr offiziell von Adobe Scene7 unterstützt.

Weitere Informationen zu dieser wichtigen Änderung finden Sie unter [Fragen und Antworten zum Lebenszyklusende von Flash Viewer](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Hinzufügen einer Scene7-Komponente zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Scene7-Komponente zu einer Seite entspricht dem Hinzufügen einer Komponente zu einer Seite. Die Scene7-Komponenten werden in den folgenden Abschnitten detailliert beschrieben.

So fügen Sie eine Scene7-Komponente bzw. einen -Viewer zu einer Seite auf der klassischen Benutzeroberfläche hinzu:

1. Öffnen Sie in AEM die Seite, auf der Sie die Scene7-Komponente hinzufügen möchten.

1. Klicken Sie bei nicht verfügbaren Scene7-Komponenten auf das Lineal im Sidekick, um in den Modus **Design** zu wechseln. Klicken Sie auf das ParSys **Bearbeiten** und wählen Sie alle **Scene7**-Komponenten aus, um sie verfügbar zu machen.

1. Return to **Edit** mode by clicking the pencil in the sidekick.

1. Ziehen Sie eine Komponente aus der **Scene7**-Gruppe in den Sidekick auf die Seite an der gewünschten Position.

1. Klicken Sie auf **Bearbeiten**, um die Komponente zu öffnen.

1. Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **OK**, um die Änderungen zu speichern.

### Hinzufügen von interaktiven Anzeigeerlebnissen zu einer dynamischen Website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Dynamisches Design für Ihre Assets bedeutet, dass Ihre Assets in Abhängigkeit ihrer Anzeigeposition angepasst werden. Mithilfe des dynamischen Designs können dieselben Assets auf mehreren Geräten effektiv dargestellt werden.

So fügen Sie ein interaktives Anzeigeerlebnis zu einer dynamischen Website auf der klassischen Benutzeroberfläche hinzu:

1. Melden Sie sich bei AEM an und stellen Sie sicher, dass Sie die [Adobe Scene7-Cloud-Services konfiguriert](/help/sites-administering/scene7.md#configuring-scene-integration) haben und dass die Scene7-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn Scene7 WCM-Komponenten nicht verfügbar sind, stellen Sie sicher, dass sie über den Designmodus aktiviert werden.

1. Ziehen Sie auf einer Website mit aktivierten Scene7-Komponenten einen **Bild**-Viewer auf die Seite.
1. Bearbeiten Sie die Komponente und passen Sie die Haltepunkte auf der Registerkarte **Scene7-Einstellungen** an.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktopcomputer, Tablets und Mobilgeräte optimiert sind.

### Für alle Scene7-Komponenten gemeinsame Einstellungen {#settings-common-to-all-scene-components}

Auch wenn sich die Konfigurationsoptionen unterscheiden, sind folgende für alle Scene7-Komponenten gleich:

* **Dateiverweis**: Navigieren Sie zu einer Datei, die Sie referenzieren möchten. Der Dateiverweis zeigt die Asset-URL und nicht zwangsläufig die vollständige Scene7-URL, einschließlich der URL-Befehle und -Parameter. Das Hinzufügen von Scene7-URL-Befehlen und -Parametern ist in diesem Feld nicht möglich. Sie müssen über die entsprechende Funktionalität in der Komponente hinzugefügt werden.
* **Breite**: Hiermit kann die Breite angepasst werden.
* **Höhe**: Hiermit kann die Höhe angepasst werden.

Sie können diese Konfigurationsoptionen festlegen, indem Sie eine Scene7-Komponente (per Doppelklick) öffnen. Zum Beispiel beim Öffnen einer **Zoom**-Komponente:

![chlimage_1-52](assets/chlimage_1-52.png)

### Zoom {#zoom}

Die HTML5 Zoom-Komponente zeigt ein größeres Bild an, wenn Sie die Taste „+“ drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Klicken Sie auf **+** zum Vergrößern. Klicken Sie auf **-** zum Verkleinern. Clicking the **x** or the reset zoom arrow brings the image back to the original size it was imported as. Klicken Sie auf die diagonalen Pfeile, um es im Vollbild anzuzeigen. Klicken Sie auf **Bearbeiten**, um die Komponente zu konfigurieren. With this component, you can configure [settings common to all Scene7 components](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In der HTML5 Flyout-Komponente wird das Asset als geteilter Bildschirm angezeigt. Links wird das Asset in der angegebenen Größe angezeigt, rechts wird der Zoomteil angezeigt. Klicken Sie auf **Bearbeiten**, um die Komponente zu konfigurieren. With this component, you can configure [settings common to all Scene7 components](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Wenn die Flyout-Komponente eine benutzerdefinierte Größe aufweist, wird diese benutzerdefinierte Größe verwendet und die dynamische Einrichtung der Komponente ist deaktiviert.
>
>Wenn Ihre Flyout-Komponente die in der Design-Ansicht festgelegte Standardgröße verwendet, wird die Standardgröße verwendet und die Komponente wird so gedehnt, dass sie der Seitenlayoutgröße bei aktiviertem responsiven Setup der Komponente entspricht. Beachten Sie jedoch, dass es eine Beschränkung für das reaktionsfähige Setup der Komponente gibt. Beim Verwenden der Flyout-Komponente mit dynamischer Einrichtung sollten Sie sie nicht mit vollständiger Seitendehnung verwenden. Andernfalls kann der Flyout über den rechten Rand der Seite hinausgehen.

![chlimage_1-53](assets/chlimage_1-53.png)

### Bild {#image}

Mit der Scene7-Bildkomponente können Sie Ihren Bildern Scene7-Funktionen hinzufügen. Dazu zählen beispielsweise Scene7-Modifizierer, -Bilder oder Viewer-Vorgaben und Scharfzeichnen. Die Scene7-Bildkomponente ähnelt anderen Bildkomponenten in AEM mit spezieller Scene7-Funktionalität. In diesem Beispiel wurde der Scene7-URL-Modifizierer **&amp;op_invert=1** auf das Bild angewendet.

![](do-not-localize/chlimage_1-4.png)

**Titel, Alt-Text** Fügen Sie auf der Registerkarte Erweitert einen Titel zum Bild und alternativer Text für die Benutzer hinzu, die Grafiken deaktiviert haben.

**URL, Öffnen in** Sie können ein Asset so einstellen, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-54](assets/chlimage_1-54.png)

**Viewer-Vorgabe** Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Viewer-Vorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**Scene7-Konfiguration** Wählen Sie die Scene7-Konfiguration aus, die Sie verwenden möchten, um aktive Bildvorgaben aus dem SPS abzurufen.

**Bildvorgabe** Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Bildvorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**Ausgabeformat** Wählen Sie das Ausgabeformat des Bilds, z. B. jpeg. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen möglicherweise zusätzliche Konfigurationsoptionen zur Verfügung. Siehe Best Practices für Bildvorgaben.

**Scharfzeichnen** Wählen Sie aus, wie das Bild scharfgezeichnet werden soll. Das Scharfzeichnen wird unter Best Practices für Bildvorgaben und in den Best Practices für das Scharfzeichnen detailliert beschrieben.

**URL-Modifikatoren** Sie können Bildeffekte ändern, indem Sie zusätzliche S7-Bildbefehle bereitstellen. Diese werden unter Bildvorgaben und in der Befehlsreferenz beschrieben.

**Haltepunkte** Wenn Ihre Website responsiv ist, sollten Sie die Haltepunkte anpassen. Haltepunkte müssen durch Kommas (,) voneinander getrennt werden.

### Bildvorlage {#image-template}

Bei [Scene7-Bildvorlagen](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) handelt es sich um Photoshop-Inhalt mit mehreren Ebenen, der in Scene7 importiert wurde, wo Inhalt und Eigenschaften zwecks Variabilität parametrisiert wurden. Mit der Komponente **Bildvorlage** können Sie Bilder importieren und den Text in AEM dynamisch ändern. Zusätzlich können Sie die Komponente **Bildvorlage** dahingehend konfigurieren, dass sie Werte aus dem Clientkontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Klicken Sie auf **Bearbeiten**, um die Komponente zu konfigurieren. You can configure [settings common to all Scene7 components](/help/sites-administering/scene7.md#settingscommontoallscene7components) as well as other settings described in this section.

![chlimage_1-55](assets/chlimage_1-55.png)

**Dateiverweis, Breite, Höhe** Siehe Einstellungen, die allen Scene7-Komponenten gemein sind.

>[!NOTE]
>
>Scene7-URL-Befehle und -Parameter können nicht direkt zur Dateiverweis-URL hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **Parameter** definiert werden.

**Titel, Alt-Text** Fügen Sie auf der Registerkarte &quot;Scene7-Bildvorlage&quot;dem Bild einen Titel und Alternativtext für Benutzer hinzu, die Grafiken deaktiviert haben.

**URL, Öffnen in** Sie können ein Asset so einstellen, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-56](assets/chlimage_1-56.png)

**Parameterbedienfeld** Beim Importieren eines Bildes werden die Parameter mit Informationen aus dem Bild vorausgefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Geben Sie zum dynamischen Ändern des Texts neuen Text in die Felder ein und klicken Sie auf **OK**. In diesem Beispiel lautet der **Preis** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-58](assets/chlimage_1-58.png)

Der Text im Bild ändert sich. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **Zurücksetzen** klicken.

![chlimage_1-59](assets/chlimage_1-59.png)

#### Ändern von Text zum Berücksichtigen des Werts eines Clientkontextwerts {#changing-text-to-reflect-the-value-of-a-client-context-value}

To link a field to a client context value, click **Select** to open the client-context menu, select the client context, and click **OK**. In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-60](assets/chlimage_1-60.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **Zurücksetzen** klicken.

![chlimage_1-61](assets/chlimage_1-61.png)

#### Ändern der Scene7-Bildvorlage zu einem Link {#making-the-scene-image-template-a-link}

So machen Sie aus der Scene7-Bildvorlagenkomponente einen klickbaren Link:

1. Klicken Sie auf der Seite mit der Scene7-Bildvorlagenkomponente auf **Bearbeiten**.
1. Geben Sie im Feld **URL** die URL ein, zu der Benutzer wechseln, wenn sie auf das Bild klicken. Wählen Sie im Feld **Öffnen in** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Klicken Sie auf **OK**.

### Komponente „Video“{#video-component}

The Scene7 **Video** component (available from the Scene7 section of the sidekick) uses device and bandwidth detection to serve the right video to each screen. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen darüber, wie Videos mit Scene7-Integration funktionieren, finden Sie unter [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md). Sehen Sie sich darüber hinaus einen [Vergleich der **Scene7-Video**-Komponente mit der grundlegenden **Video**-Komponente an](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-63](assets/chlimage_1-63.png)

### Bekannte Einschränkungen für die Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen an, ob ein primäres Quellvideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Kodierte Scene7-Ausgabeformate
* Adaptive Scene7-Videosets

Beim Verwenden eines adaptiven Videosets mit der Scene7-Videokomponente muss die Größe der Komponente geändert werden, um sie an die Abmessungen des Videos anzupassen.

## Scene7-Inhaltsbrowser {#scene-content-browser}

Mit dem Scene7-Inhaltsbrowser können Sie Inhalt aus Scene7 direkt in AEM anzeigen. To access the content browser, in the Content Finder, select **Scene7** in the touch-optimized user interface or the **S7** icon in the classic user interface. Die Funktionalität ist zwischen den beiden Benutzeroberflächen identisch.

Wenn Sie über mehrere Konfigurationen verfügen, zeigt AEM standardmäßig die [Standardkonfiguration](/help/sites-administering/scene7.md#configuring-a-default-configuration) an. Sie können unterschiedliche Kategorien direkt im Scene7-Inhaltsbrowser im Dropdownmenü auswählen.

>[!NOTE]
>
>* Im Ad-hoc-Ordner befindliche Assets werden im Scene7-Inhaltsbrowser nicht angezeigt.
>* Bei [aktivierter sicherer Vorschau](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) werden die auf Scene7 veröffentlichten und nicht veröffentlichten Assets im Scene7-Inhaltsbrowser angezeigt.
>* If you do not see **Scene7** or the **S7** icon as an option in the content browser, you need to [configure Scene7 to work with AEM](/help/sites-administering/scene7.md).

   >
   >
* Für Videos unterstützt der Scene7-Inhaltsbrowser Folgendes:
   >
   >   
   * Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
   >   * Einzelnes MP4-Video
   >   * Einzelnes F4V-Video


### Durchsuchen von Inhalten {#browsing-content-in-the-classic-ui}

Durchsuchen Sie Inhalt in Scene7, indem Sie auf die Registerkarte **S7** klicken.

Sie können die Konfiguration ändern, auf die Sie zugreifen, indem Sie die Konfiguration auswählen. Die Ordner ändern sich in Abhängigkeit der von Ihnen ausgewählten Konfiguration.

![chlimage_1-64](assets/chlimage_1-64.png)

Wie mit der Inhaltssuche für Assets können Sie nach Assets suchen und Ergebnisse filtern. Im Gegensatz zur Asset-Suche **beginnt** der Dateiname jedoch beim Eingeben eines Keywords auf der Registerkarte **S7** mit dem von Ihnen eingegebenen String, anstatt dass das Keyword im Dateinamen **enthalten** ist.

Standardmäßig werden Assets nach Dateiname angezeigt. Sie können Ergebnisse auch nach Asset-Typ filtern.

>[!NOTE]
>
>Für Videos unterstützt der Scene7-Inhaltsbrowser von WCM Folgendes:
>
>* Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
>* Einzelnes MP4-Video
>* Einzelnes F4V-Video

>



### Durchsuchen von Scene7-Assets mit dem Inhaltsbrowser {#searching-for-scene-assets-with-the-content-browser}

Das Suche nach Scene7-Assets ähnelt der Suche nach AEM-Assets. Bei der Suche wird jedoch eine Remoteansicht der Assets im Scene7-System angezeigt, anstatt dass sie direkt in AEM importiert werden.

Sie können die klassische oder Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. In Abhängigkeit von der Oberfläche unterscheidet sich die Art und Weise der Suche etwas.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**Suchbegriffe** Sie können Assets anhand des Namens suchen. Bei der Suche entsprechen die von Ihnen eingegebenen Keywords dem Beginn des Dateinamens. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Drücken Sie die Eingabetaste, nachdem Sie den Begriff eingegeben haben, um nach dem Asset zu suchen.

![chlimage_1-65](assets/chlimage_1-65.png)

**Ordner/Pfad** Der Name des angezeigten Ordners basiert auf der ausgewählten Konfiguration. Sie können niedrigere Ebenen anzeigen, indem Sie auf das Ordnersymbol klicken, einen Unterordner auswählen und dann auf das Häkchen klicken, um ihn auszuwählen.

Wenn Sie ein Keyword eingeben und einen Ordner auswählen, durchsucht AEM diesen Ordner und die zugehörigen Unterordner. Wenn Sie jedoch bei der Suche keine Keywords eingeben, wird durch die Auswahl des Ordners das Asset nur in diesem Ordner angezeigt und nicht in Unterordnern.

Standardmäßig durchsucht AEM den ausgewählten Ordner und alle Unterordner.

![chlimage_1-66](assets/chlimage_1-66.png)

**Asset** -Typ Wählen Sie Scene7, um Scene7-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Scene7 konfiguriert wurde.

![chlimage_1-67](assets/chlimage_1-67.png)

**Konfiguration** Wenn in Cloud Services mehr als eine Scene7-Konfiguration definiert ist, können Sie diese hier auswählen. Der Ordner ändert sich anhand der von Ihnen ausgewählten Konfiguration.

![chlimage_1-68](assets/chlimage_1-68.png)

**Asset-Typ** Im Scene7-Browser können Sie die Ergebnisse filtern, um Folgendes einzuschließen: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Asset-Typ auswählen, durchsucht AEM standardmäßig alle Asset-Typen.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>* Auf der klassischen Benutzeroberfläche können Sie auch nach **Flash** und **FXG** suchen. Das Filtern nach diesen auf der Touch-optimierten Benutzeroberfläche wird derzeit nicht unterstützt.
   >
   >
* Beim Durchsuchen eines Videos suchen Sie nach einem einzelnen Ausgabeformat. Die Ergebnisse geben das ursprüngliche (nur *.mp4) und das kodierte Ausgabeformat zurück.
* Beim Durchsuchen eines adaptiven Videosets suchen Sie den Ordner und alle Unterordner, allerdings nur, wenn Sie der Suche einen Suchbegriff hinzugefügt haben. Wenn Sie kein Keyword hinzugefügt haben, durchsucht AEM nicht die Unterordner.



**Veröffentlichungsstatus** Sie können nach Assets basierend auf dem Veröffentlichungsstatus filtern: Veröffentlichung rückgängig gemacht oder veröffentlicht. Wenn Sie keinen Veröffentlichungsstatus auswählen, durchsucht AEM standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-70](assets/chlimage_1-70.png)
