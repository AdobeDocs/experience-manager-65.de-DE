---
title: Videoprofile
description: Dynamic Media enthält bereits das vordefinierte Profil „Adaptive Videoverschlüsselung“. Die Einstellungen in diesem vordefinierten Profil sind so optimiert, dass sie Ihren Kunden Ansichten in bestmöglicher Qualität bieten. Sie können für Ihre Videos auch smartes Zuschneiden nutzen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
docset: aem65
feature: Video Profiles
role: User, Admin
mini-toc-levels: 3
exl-id: b290fac2-7259-45d7-b733-70419d632b07
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '3770'
ht-degree: 98%

---

# Videoprofile {#video-profiles}

Dynamic Media enthält bereits das vordefinierte Profil „Adaptive Videoverschlüsselung“. Die Einstellungen in diesem vordefinierten Profil sind so optimiert, dass sie Ihren Kunden Ansichten in bestmöglicher Qualität bieten. Beim Kodieren von primären Videos mithilfe des Profils „Adaptive Videoverschlüsselung“ passt der Video-Player während der Wiedergabe automatisch die Qualität des Video-Streams auf Grundlage der Internet-Verbindungsgeschwindigkeit Ihrer Kunden an. Diese Funktionalität wird als Streaming mit adaptiver Bit-Rate bezeichnet.

Die folgenden weiteren Faktoren wirken sich auf die Qualität Ihrer Videos aus:

* **Auflösung des hochgeladenen primären Videos**

  Wenn das MP4-Video mit einer geringeren Auflösung (wie 240 p oder 360 p) aufgenommen wurde, kann es nicht in High Definition gestreamt werden.

* **Größe des Video-Players**

  Standardmäßig ist die „Breite“ im Profil „Adaptive Videoverschlüsselung“ auf „Automatisch“ festgelegt. Wie erwähnt, wird je nach Größe des Players bei der Wiedergabe die bestmögliche Qualität verwendet.

Siehe [Best Practices zur Videokodierung](/help/assets/video.md#best-practices-for-encoding-videos).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

>[!NOTE]
>
>Um die Metadaten eines Videos und die zugehörigen Videobild-Miniaturansichten zu generieren, muss das Video selbst den Kodierungsprozess in Dynamic Media durchlaufen. In Adobe Experience Manager kodiert der Workflow für **[!UICONTROL Dynamic Media-Videokodierung]** Videos, wenn Dynamic Media aktiviert und Video-Cloud Services eingerichtet sind. Dieser Workflow erfasst den Verlauf der Workflow-Prozesse und Informationen zu Fehlern. Siehe [Überwachen der Videokodierung und des YouTube-Veröffentlichungs-Fortschritts](/help/assets/video.md#monitoring-video-encoding-and-youtube-publishing-progress). Wenn Sie Dynamic Media aktiviert und Video-Cloud Services eingerichtet haben, wird der Workflow für die **[!UICONTROL Videokodierung mit Dynamic Media]** automatisch beim Hochladen eines Videos wirksam. (Wenn Sie Dynamic Media nicht verwenden, wird der Workflow **[!UICONTROL DAM Update Asset]** wirksam.)
>
>Metadaten sind nützlich, wenn Sie nach Assets suchen. Die Miniaturen sind statische Videobilder, die bei der Kodierung generiert werden. Sie sind für das Adobe Experience Manager-System erforderlich und werden in der Benutzeroberfläche eingesetzt, damit Sie Videos in der Kartenansicht, der Suchergebnisansicht und der Asset-Listenansicht einfacher identifizieren können. Sie können die generierten Miniaturen sehen, wenn Sie auf das Ausgabedarstellungs-Symbol (eine Malerpalette) eines kodierten Videos klicken.

Wenn Sie das Erstellen des Videoprofils abgeschlossen haben, wenden Sie es auf einen oder mehrere Ordner an. Siehe [Anwenden eines Videoprofils auf Ordner](#applying-a-video-profile-to-folders).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](/help/assets/config-dms7.md#configuring-asset-processing).

Siehe auch [Profile für die Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md).

## Vorgaben für adaptive Videoverschlüsselung {#adaptive-video-encoding-presets}

In der folgenden Tabelle werden die Best Practice Codierungsprofile für das adaptive Video-Streaming auf Smartphones und Tablets sowie Desktop-Computern angegeben. Sie können diese Vorgaben für Videos mit jedem Seitenverhältnis verwenden.

<table>
 <tbody>
  <tr>
   <td><strong>Videoformat-Codec</strong></td>
   <td><strong>Videogröße – Breite (px)</strong></td>
   <td><strong>Videogröße – Höhe (px)</strong></td>
   <td><strong>Seitenverhältnis beibehalten?</strong></td>
   <td><strong>Video-Bitrate (kBit/s)</strong></td>
   <td><strong>Video-Framerate (FPS)</strong></td>
   <td><strong>Audio-Codec</strong></td>
   <td><strong>Audio-Bitrate (kBit/s)</strong></td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>360</td>
   <td>Ja</td>
   <td>730</td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>540</td>
   <td>Ja</td>
   <td>2.000<br /> </td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>720<br /> </td>
   <td>Ja</td>
   <td>3.000<br /> </td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
 </tbody>
</table>

## Über die Verwendung von smartem Zuschneiden in Videoprofilen {#about-smart-crop-video}

Intelligentes Zuschneiden für Videos – eine optionale Funktion, die in Videoprofilen verfügbar ist – ist ein Tool, das die Leistungsfähigkeit künstlicher Intelligenz in Adobe Sensei nutzt. Es erkennt den Fokus automatisch in jedem adaptiven Video oder progressiven Video, das Sie hochgeladen haben, unabhängig von der Größe, und schneidet entsprechend zu.

Zu den unterstützten Videoformaten für smartes Zuschneiden gehören MP4, MKV, MOV, AVI, FLV und WMV.

Für die maximal unterstützte Videodateigröße beim smarten Zuschneiden gelten folgende Kriterien:

* Dauer von fünf Minuten.
* 30 Frames pro Sekunde (FPS).
* Dateigröße 300 MB.

Adobe Sensei ist auf 9000 Frames beschränkt. Das heißt: fünf Minuten bei 30 FPS. Wenn Ihr Video eine höhere FPS-Rate aufweist, verringert sich die maximal unterstützte Videodauer entsprechend. Beispielsweise darf ein 60-FPS-Video maximal 2,5 Minuten lang sein, damit es von Adobe Sensei und smartem Zuschneiden unterstützt werden kann.

![Smartes Zuschneiden für Video](assets/smart-crop-video.png)

>[!IMPORTANT]
>
>Damit das smarte Zuschneiden für Videos funktioniert, müssen Sie mindestens eine Vorgabe für Videokodierung in Ihr Videoprofil einschließen.

Wenn Sie smartes Zuschneiden für Videos verwenden möchten, erstellen Sie ein Profil für adaptive oder progressive Videoverschlüsselung. Verwenden Sie im Rahmen Ihres Profils das Tool **[!UICONTROL Smart Crop Ratio]**, um vordefinierte Seitenverhältnisse auszuwählen. Nachdem Sie beispielsweise Ihre Videokodierungsvorgaben definiert haben, können Sie eine Definition für &quot;Mobiles Querformat&quot;mit einem Seitenverhältnis von 16×9 und eine Definition für &quot;Mobiles Hochformat&quot;mit einem Seitenverhältnis von 9×16 hinzufügen. Andere Seiten- oder Zuschnittverhältnisse, aus denen Sie wählen können, sind 1×1, 4×3 und 4×5.

![Bearbeiten von Videokodierungsprofilen mit smartem Zuschneiden](assets/edit-smart-crop-video2.png)

Sie können mit dem Schieberegler ganz rechts neben **[!UICONTROL Seitenverhältnis für intelligentes Zuschneiden]** in der Benutzeroberfläche das intelligente Zuschneiden im Videoprofil aktivieren oder deaktivieren.

Nachdem Sie Ihr Videoprofil erstellt und gespeichert haben, können Sie es auf die gewünschten Ordner anwenden.

Siehe [Anwenden eines Videoprofils auf bestimmte Ordner](#applying-video-profiles-to-specific-folders) oder [Globales Anwenden eines Videoprofils](#applying-a-video-profile-globally).

Siehe auch [Smartes Zuschneiden für Bilder](image-profiles.md).

## Erstellen eines Videoprofils für Streaming mit adaptiver Bit-Rate {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media umfasst standardmäßig das vordefinierte Profil „Adaptive Videoverschlüsselung“ (eine Gruppe mit Video-Upload-Einstellungen für MP4 H.264), das für das beste Anzeigeerlebnis optimiert ist. Sie können dieses Profil beim Hochladen von Videos verwenden.

Wenn dieses vordefinierte Profil Ihre Anforderungen jedoch nicht erfüllt, können Sie ein eigenes Profil für die adaptive Videoverschlüsselung erstellen. Wenn Sie die Einstellung **[!UICONTROL Für adaptives Streaming kodieren]** verwenden (eine empfohlene Vorgehensweise), werden alle dem Profil hinzugefügten Kodierungsvorgaben validiert, um sicherzustellen, dass alle Videos dasselbe Seitenverhältnis aufweisen. Darüber hinaus werden die kodierten Videos als Multi-Bitrate-Set für das Streaming behandelt.

Beim Erstellen des Videokodierungsprofils sehen Sie, dass die meisten Kodierungsoptionen vorab mit empfohlenen Standardeinstellungen gefüllt sind, um Ihnen die Arbeit zu erleichtern. Wenn Sie allerdings einen anderen Wert als den empfohlenen Standardwert auswählen, kann dies zu einer schlechten Videoqualität bei der Wiedergabe und zu anderen Leistungsproblemen führen.

Für alle MP4 H.264-Videocodierungsvorgaben im Profil werden also die folgenden Werte validiert, um sicherzustellen, dass diese über individuelle Codierungsvorgaben hinweg identisch sind. Dadurch wird Streaming mit adaptiver Bit-Rate ermöglicht:

* Videoformat-Codec – MP4 H.264 (.mp4)
* Audio-Codec
* Audiobitrate
* Seitenverhältnis beibehalten
* Codierung mit zwei Durchgängen
* Konstante Bit-Rate
* H264-Profil
* Audio-Sampling-Rate

Wenn die Werte nicht identisch sind, können Sie das Profil durchaus im Istzustand erstellen. Streaming mit adaptiver Bit-Rate ist dann jedoch nicht möglich. Stattdessen wird das Einzel-Bitraten-Streaming durchgeführt. Es wird empfohlen, dass Sie die Kodierungseinstellungen so bearbeiten, dass dieselben Werte über individuelle Kodierungsvorgaben hinweg im Profil verwendet werden. (Der Videoprofil-/Vorgabeneditor erzwingt die Parität der adaptiven Videokodierungseinstellungen, wenn die Einstellung **[!UICONTROL Für adaptives Streaming kodieren]** aktiviert ist.)

Siehe auch [Erstellen eines Videokodierungsprofils für progressives Streaming](#creating-a-video-encoding-profile-for-progressive-streaming).

Siehe auch [Best Practices zur Videokodierung](/help/assets/video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](/help/assets/config-dms7.md#configuring-asset-processing).

**So erstellen Sie ein Videoprofil für Streaming mit adaptiver Bit-Rate**:

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um ein Videoprofil hinzuzufügen.

1. Geben Sie einen Namen und eine Beschreibung für das Profil ein.
1. Klicken Sie auf der Seite „Videokodierungsvorgaben erstellen/bearbeiten“ auf **[!UICONTROL Videokodierungsvorgabe hinzufügen]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Allgemein]** die Video- und Audiooptionen fest.
Klicken Sie auf das Informationssymbol neben den einzelnen Optionen, um zusätzliche Beschreibungen oder empfohlene Einstellungen auf Grundlage des ausgewählten Videoformat-Codecs anzuzeigen.
1. Stellen Sie unter der Überschrift „Videogröße“ sicher, dass **[!UICONTROL Seitenverhältnis beibehalten]** aktiviert ist.
1. Legen Sie die Video-Frame-Auflösung in Pixeln fest. Verwenden Sie den Wert **[!UICONTROL Auto]**, um das Seitenverhältnis der Quelle anzupassen (Verhältnis von Breite zu Höhe). Beispiel: Auto x 480 oder 640 x Auto.

1. Führen Sie einen der folgenden Schritte aus:

   * Geben Sie im Feld **[!UICONTROL Breite]** die Option **[!UICONTROL auto]** ein. Geben Sie im Feld **[!UICONTROL Höhe]** einen Wert in Pixel ein.

   * Klicken Sie zum Visualisieren der Größe des Videos auf das Informationssymbol (i) rechts neben **[!UICONTROL Höhe]**, um die Seite mit der Größenberechnung zu öffnen. Legen Sie mit der **[!UICONTROL Größenberechnung]** die gewünschten Abmessungen des Videos fest (durch das blaue Feld dargestellt). Klicken Sie oben rechts auf **[!UICONTROL X]**, wenn Sie fertig sind.

1. (Optional) Klicken Sie auf die Registerkarte **[!UICONTROL Erweitert]** und stellen Sie sicher, dass das Kontrollkästchen **[!UICONTROL Standardwerte verwenden]** ausgewählt ist (empfohlen). Alternativ können Sie erweiterte Video- und Audioeinstellungen anpassen.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um die Vorgabe zu speichern.
1. Führen Sie einen der folgenden Schritte aus:
   * Wiederholen Sie Schritt 4 bis 10, um weitere Kodierungsvorgaben zu erstellen. (Das adaptive Video-Streaming erfordert mehrere Videovorgaben.)
   * Fahren Sie mit dem nächsten Schritt fort.

1. (Optional) Gehen Sie wie folgt vor, um den Videos, auf die dieses Profil angewendet wird, smartes Zuschneiden hinzuzufügen:
   * Klicken Sie auf der Seite „Videoprofil bearbeiten“ rechts neben der Überschrift „Seitenverhältnis für intelligentes Zuschneiden“ auf **[!UICONTROL Neu hinzufügen]**.
   * Geben Sie im Feld „Name“ einen Namen für das Zuschnittverhältnis ein, damit Sie es leicht erkennen können.
   * Wählen Sie aus der Dropdown-Liste **[!UICONTROL Zuschnittverhältnis]** das Verhältnis aus, das Sie verwenden möchten.

1. Führen Sie einen der folgenden Schritte aus:

   * Fügen Sie bei Bedarf weitere Zuschnittverhältnisse hinzu.
   * Fahren Sie mit dem nächsten Schritt fort.

1. Klicken Sie oben rechts auf der Seite erneut auf **[!UICONTROL Speichern]**, um das Profil zu speichern.

Sie können das Profil jetzt auf Ordner anwenden, die Videos enthalten. Siehe [Anwenden eines Videoprofils auf Ordner](#applying-a-video-profile-to-folders) oder [Globales Anwenden eines Videoprofils](#applying-a-video-profile-globally).

## Erstellen eines Videoprofils für progressives Streaming {#creating-a-video-encoding-profile-for-progressive-streaming}

Wenn Sie die Option **[!UICONTROL Kodieren für adaptives Streaming]** nicht verwenden möchten, werden alle Kodierungsvoreinstellungen, die Sie dem Profil hinzufügen, als einzelne Videoausgabedarstellungen für Single-Bitrate-Streaming oder progressive Videoausgabesdarstellung behandelt. Außerdem gibt es keine Validierung, um sicherzustellen, dass alle Videoausgabedarstellungen dasselbe Seitenverhältnis aufweisen.

Je nachdem, welchen Modus Sie ausführen, werden die folgenden Videoformat-Codecs unterstützt:

* Dynamic Media-Scene7-Modus: H.264 (.mp4)
* Dynamic Media-Hybridmodus: H.264 (.mp4), WebM

Siehe auch [Erstellen eines Videocodierungsprofils für Streaming mit adaptiver Bit-Rate](#creating-a-video-encoding-profile-for-adaptive-streaming).

Siehe auch [Best Practices zur Videokodierung](/help/assets/video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](/help/assets/config-dms7.md#configuring-asset-processing).

**So erstellen Sie ein Videoprofil für progressives Streaming**:

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um ein Videoprofil hinzuzufügen.
1. Geben Sie einen Namen und eine Beschreibung für das Profil ein.
1. Klicken Sie auf der Seite „Videokodierungsvorgaben erstellen/bearbeiten“ auf **[!UICONTROL Videokodierungsvorgabe hinzufügen]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Allgemein]** die Video- und Audiooptionen fest.
Klicken Sie auf das Informationssymbol neben den einzelnen Optionen, um zusätzliche Beschreibungen oder empfohlene Einstellungen auf Grundlage des ausgewählten Videoformat-Codecs anzuzeigen.
1. (Optional) Deaktivieren Sie unter der Überschrift „Videogröße“ das Kontrollkästchen **[!UICONTROL Seitenverhältnis beibehalten]**.
1. Gehen Sie folgendermaßen vor:
   * Geben Sie im Feld **[!UICONTROL Breite]** die Option **[!UICONTROL auto]** ein.
   * Geben Sie im Feld **[!UICONTROL Höhe]** einen Wert in Pixel ein.
Klicken Sie zur Visualisierung der Größe des Videos auf das Informationssymbol „Höhe“, um die Seite **[!UICONTROL Größenberechnung]** zu öffnen. Passen Sie die Größe des Videos auf der Seite **[!UICONTROL Größenberechnung]** wunschgemäß weiter an. Wenn Sie damit fertig sind, klicken Sie oben rechts im Dialogfeld auf **[!UICONTROL X]**.
1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf die Registerkarte **[!UICONTROL Erweitert]** und stellen Sie sicher, dass das Kontrollkästchen **[!UICONTROL Standardwerte verwenden]** ausgewählt ist (empfohlen).

   * Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Standardwerte verwenden]** und geben Sie die gewünschten Video- und Audioeinstellungen an.
Klicken Sie auf das Informationssymbol neben den einzelnen Optionen, um zusätzliche Beschreibungen oder empfohlene Einstellungen auf Grundlage des ausgewählten Videoformat-Codecs anzuzeigen.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um die Vorgabe zu speichern.
1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie die Schritte 4 bis 9, um weitere Codierungsvorgaben zu erstellen.
   * Fahren Sie mit dem nächsten Schritt fort.

1. (Optional) Gehen Sie wie folgt vor, um den Videos, auf die dieses Profil angewendet wird, smartes Zuschneiden hinzuzufügen:

   * Klicken Sie auf der Seite „Videoprofil bearbeiten“ rechts neben der Überschrift „Seitenverhältnis für intelligentes Zuschneiden“ auf **[!UICONTROL Neu hinzufügen]**.
   * Geben Sie im Feld „Name“ einen Namen für das Zuschnittverhältnis ein, damit Sie es leicht erkennen können.
   * Wählen Sie aus der Dropdown-Liste **[!UICONTROL Zuschnittverhältnis]** das Verhältnis aus, das Sie verwenden möchten.

1. Führen Sie einen der folgenden Schritte aus:

   * Fügen Sie bei Bedarf weitere Zuschnittverhältnisse hinzu.
   * Fahren Sie mit dem nächsten Schritt fort.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**, um das Profil zu speichern.

Sie können das Profil jetzt auf Ordner anwenden, die Videos enthalten. Siehe [Anwenden eines Videoprofils auf Ordner](#applying-a-video-profile-to-folders) oder [Globales Anwenden eines Videoprofils](#applying-a-video-profile-globally).

## Verwenden von vom Benutzer hinzugefügten Videokodierungsparametern {#using-custom-added-video-encoding-parameters}

Sie können nun vorhandene Videokodierungsprofile bearbeiten, um von erweiterten Parametern zur Videokodierung zu profitieren, die beim Erstellen oder Bearbeiten eines Videoprofils in Adobe Experience Manager nicht in der Benutzeroberfläche vorhanden sind. Sie können Ihrem bestehenden Profil einen oder mehrere erweiterte Parameter wie „minBitrate“ und „maxBitrate“ hinzufügen.

**So verwenden Sie vom Benutzer hinzugefügte Videokodierungsparameter:**

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie auf der Seite „CRXDE Lite“ im linken Bereich des Explorers in das folgende Verzeichnis:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit`

1. Geben Sie im Bereich rechts unten auf der Seite auf der Registerkarte „Eigenschaften“ **[!UICONTROL Name]**, **[!UICONTROL Typ]** und **[!UICONTROL Wert]** des zu verwendenden Parameters an.

   Die folgenden erweiterten Parameter sind verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Name</strong></td>
   <td><strong>Beschreibung</strong><br /> </td>
   <td><strong>Typ</strong><br /> </td>
   <td><strong>Wert</strong></td>
  </tr>
  <tr>
   <td><code>h264Level</code></td>
   <td>Zu verwendende H.264-Stufe für die Kodierung. Normalerweise wird dieser Parameter basierend auf den verwendeten Kodierungseinstellungen automatisch bestimmt.</td>
   <td><code>String</code></td>
   <td><p>10 * H.264-Stufe</p> <p>Zum Beispiel: 3,0 = 30, 1,3 = 13</p> <p>Kein Standardwert.</p> </td>
  </tr>
  <tr>
   <td><code>keyframe</code></td>
   <td>Die Zielzahl der Frames zwischen Keyframes. Berechnen Sie diesen Wert, damit alle 2 bis 10 Sekunden ein Keyframe generiert werden kann. Bei 30 Frames pro Sekunde sollte das Keyframe-Intervall zwischen 60 und 300 liegen.<br /> <br /> Niedrigere Keyframe-Intervalle verbessern das Verhalten bei Stream-Suche und Stream-Wechsel für adaptive Videoverschlüsselung und können auch die Qualität bei Videos mit viel Bewegung verbessern. Da Keyframes die Größe einer Datei erhöhen, bewirkt ein niedrigeres Keyframe-Intervall in der Regel eine niedrigere Videogesamtqualität bei einer bestimmten Bit-Rate.</td>
   <td><code>String</code></td>
   <td><p>Positive Zahl.</p> <p>Der Standardwert ist 300.</p> <p>Der empfohlene Wert für DASH oder HLS ist 60-90. (Um DASH für Ihre Videos zu verwenden, muss es zunächst in Ihrem Konto aktiviert werden. Siehe <a href="/help/assets/video.md#enable-dash">Aktivieren von DASH in Ihrem Konto</a>.)</p> </td>
  </tr>
  <tr>
   <td><code>minBitrate</code></td>
   <td><p>Minimale Bit-Rate, um Kodierungen mit variabler Bit-Rate zu ermöglichen (Kbit/s).</p> <p>Dieser Parameter ist nur gültig, wenn bei der Erstellung oder Bearbeitung eines Videokodierungsprofils auf der Registerkarte „Erweitert“ die Option <strong>Konstante Bit-Rate verwenden</strong> deaktiviert ist.</p> <p>Siehe auch <a href="/help/assets/video.md#bitrate">Bit-Rate</a>.</p> </td>
   <td><code>String</code></td>
   <td><p>Positive Zahl in Kbit/s.</p> <p>Kein Standardwert.</p> </td>
  </tr>
  <tr>
   <td><code>maxBitrate</code></td>
   <td><p>Maximale Bit-Rate, um Kodierungen mit variabler Bit-Rate zu ermöglichen (Kbit/s).</p> <p>Dieser Parameter ist nur gültig, wenn bei der Erstellung oder Bearbeitung eines Videokodierungsprofils auf der Registerkarte „Erweitert“ die Option <strong>Konstante Bit-Rate verwenden</strong> deaktiviert ist.</p> <p>Siehe auch <a href="/help/assets/video.md#bitrate">Bit-Rate</a>.</p> </td>
   <td><code>String</code></td>
   <td><p>Positive Zahl in Kbit/s.</p> <p>Kein Standardwert. Der empfohlene Wert entspricht jedoch bis zum Zweifachen der Kodierungs-Bit-Rate.</p> </td>
  </tr>
  <tr>
   <td><code>audioBitrateCustom</code></td>
   <td>Setzen Sie den Wert auf <code>true</code>, um eine konstante Bit-Rate für den Audio-Stream zu erzwingen, sofern dies vom Audio-Codec unterstützt wird.</td>
   <td><code>String</code></td>
   <td><p><code>true</code>/<code>false</code></p> <p>Der Standardwert ist <code>false</code>.</p> <p>Empfohlener Wert für DASH oder HLS: <code>false</code>. (Um DASH für Ihre Videos zu verwenden, muss es zunächst in Ihrem Konto aktiviert werden. (Siehe <a href="/help/assets/video.md#enable-dash">Aktivieren von DASH in Ihrem Konto</a>.)</p> <p> </p> </td>
  </tr>
 </tbody>
</table>

![chlimage_1-516](assets/chlimage_1-516.png)

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Hinzufügen]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Wiederholen Sie die Schritte 3 und 4, um Ihrem Videocodierungsprofil einen weiteren Parameter hinzuzufügen.
   * Klicken Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Alle speichern]**.

1. Klicken Sie in der oberen linken Ecke der Seite „CRXDE Lite“ auf das Symbol **[!UICONTROL Zurück zur Startseite]**, um zu Adobe Experience Manager zurückzukehren.

### Bearbeiten eines Videoprofils {#editing-a-video-encoding-profile}

Sie können die Videoprofile bearbeiten, die Sie erstellt haben, um die in diesen Profilen enthaltenen Videovorgaben hinzuzufügen, zu bearbeiten oder zu löschen.

Die Bearbeitung des bereits in Dynamic Media integrierten Profils **[!UICONTROL Adaptive Videokodierung]** ist standardmäßig deaktiviert. Sie können das Profil einfach kopieren und dann unter einem neuen Namen speichern. Sie können dann die gewünschten Vorgaben im kopierten Profil bearbeiten.

Siehe auch [Best Practices zur Videokodierung](/help/assets/video.md#best-practices-for-encoding-videos).

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](/help/assets/config-dms7.md#configuring-asset-processing).

**So bearbeiten Sie ein Videoprofil:**

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Aktivieren Sie auf der Seite „Videoprofile“ einen Videoprofilnamen.
1. Wählen Sie in der Symbolleiste die Option **[!UICONTROL Bearbeiten]** aus.
1. Bearbeiten Sie den Namen und die Beschreibung nach Bedarf auf der Seite „Videokodierungsprofil“.
1. Als Best Practice hat es sich bewährt, das Kontrollkästchen **[!UICONTROL Für Streaming mit adaptiver Bit-Rate codieren]** zu aktivieren.
Klicken Sie auf das Informationssymbol, um eine Beschreibung von Streaming mit adaptiver Bit-Rate anzuzeigen. (Wenn Sie ein progressives Videoprofil bearbeiten, aktivieren Sie dieses Kontrollkästchen nicht.)
1. Unter der Überschrift „Videokodierungsvorgaben“ können Sie die Videokodierungsvorgaben des Profils hinzufügen, bearbeiten oder löschen.

   Klicken Sie neben den einzelnen Optionen auf den Registerkarten **[!UICONTROL Allgemein]** und **[!UICONTROL Erweitert]** auf das Informationssymbol, um zusätzliche Beschreibungen oder empfohlene Einstellungen auf Grundlage des ausgewählten Videoformat-Codecs anzuzeigen.

1. Klicken Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Speichern]**.

### Kopieren eines Videoprofils {#copying-a-video-encoding-profile}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Aktivieren Sie auf der Seite „Videoprofile“ einen Videoprofilnamen.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie auf der Seite „Videokodierungsprofil“ einen neuen Namen für das Profil ein.
1. Als Best Practice hat es sich bewährt, das Kontrollkästchen **[!UICONTROL Für adaptives Streaming kodieren]** zu aktivieren. Klicken Sie auf das Informationssymbol, um eine Beschreibung von Streaming mit adaptiver Bit-Rate anzuzeigen. (Wenn Sie ein progressives Videoprofil kopieren, aktivieren Sie dieses Kontrollkästchen nicht.)

   Wenn im Hybridmodus von Dynamic Media eine WebM-Videovoreinstellung Teil des Videoprofils ist, ist die Option **[!UICONTROL Für adaptives Streaming kodieren]** nicht möglich, da alle Vorgaben das MP4-Format aufweisen müssen.
1. Unter der Überschrift „Videokodierungsvorgaben“ können Sie die Videokodierungsvorgaben des Profils hinzufügen, bearbeiten oder löschen.

   Klicken Sie neben den einzelnen Optionen in den Registerkarten „Allgemein“ und „Erweitert“ auf das Informationssymbol, um die empfohlenen Einstellungen und die Beschreibung anzuzeigen.

1. Klicken Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Speichern]**.

### Löschen eines Videoprofils {#deleting-a-video-encoding-profile}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Aktivieren Sie auf der Seite „Videoprofile“ mindestens einen Videoprofilnamen.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Löschen]** aus.
1. Klicken Sie auf **[!UICONTROL OK]**.

## Anwenden eines Videoprofils auf Ordner {#applying-a-video-profile-to-folders}

Wenn Sie ein Videoprofil einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Diese Regel bedeutet, dass Sie einem Ordner nur ein Videoprofil zuweisen können. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Videoprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-517](assets/chlimage_1-517.png)

Sie können Videoprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden eines Videoprofils auf bestimmte Ordner {#applying-video-profiles-to-specific-folders}

Sie können ein Videoprofil über das Menü **[!UICONTROL Werkzeuge]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Videoprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Siehe auch [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung seines Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Anwenden von Videoprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-video-profiles-to-folders-by-way-of-the-profiles-user-interface}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Wählen Sie ein Videoprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.
1. Klicken Sie auf **[!UICONTROL Profil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Klicken Sie dann auf **[!UICONTROL Anwenden]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird (solange Sie sich in der **[!UICONTROL Kartenansicht]** befinden).
Sie können [den Fortschritt eines Videoprofil-Verarbeitungsauftrags überwachen](#monitoring-the-progress-of-an-encoding-job).

#### Anwenden eines Videoprofils auf Ordner aus „Eigenschaften“ {#applying-video-profiles-to-folders-from-properties}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Assets]** und dann in den Ordner, auf den Sie ein Videoprofil anwenden möchten.
1. Klicken Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Videoprofile]** das Profil aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern und schließen]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

   ![chlimage_1-518](assets/chlimage_1-518.png)
Sie können [den Fortschritt eines Videoprofil-Verarbeitungsauftrags überwachen](#monitoring-the-progress-of-an-encoding-job).

### Globales Anwenden eines Videoprofils {#applying-a-video-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird auf alle Inhalte, die Sie in Adobe Experience Manager Assets in beliebigen Ordnern hochladen, das ausgewählte Profil angewendet.

Siehe auch [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung seines Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

**So wenden Sie ein Videoprofil global an**:

* Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`. Fügen Sie die Eigenschaft `videoProfile:/libs/settings/dam/video/dynamicmedia/<name of video encoding profile>` hinzu und wählen Sie **[!UICONTROL Alle speichern]**.

  ![chlimage_1-519](assets/chlimage_1-519.png)
* Sie können [den Fortschritt eines Videoprofil-Verarbeitungsauftrags überwachen](#monitoring-the-progress-of-an-encoding-job).

## Überwachen des Fortschritts eines Videoprofil-Verarbeitungsvorgangs {#monitoring-the-progress-of-an-encoding-job}

Eine Verarbeitungsanzeige (oder Statusleiste) wird angezeigt, damit Sie den Fortschritt eines Videoprofil-Verarbeitungsvorgangs visuell überwachen können.

In der Datei `error.log` können Sie den Fortschritt des Kodierungsvorgangs ebenfalls anzeigen. Sie können prüfen, ob die Kodierung abgeschlossen ist oder ob Auftragsfehler angezeigt werden. Die Datei `error.log` befindet sich im `logs`-Protokollordner, in dem Ihre Instanz von Adobe Experience Manager installiert ist.

## Entfernen eines Videoprofils aus Ordnern {#removing-a-video-profile-from-folders}

Wenn Sie ein Videoprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können ein Videoprofil aus einem Ordner im Menü **[!UICONTROL Tools]** entfernen. Wenn Sie sich im Ordner befinden, ist dies über die **[!UICONTROL Ordnereinstellungen]** möglich. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Videoprofile aus Ordnern entfernen können.

### Entfernen von Videoprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-video-profiles-from-folders-by-way-of-the-profiles-user-interface}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Wählen Sie das Videoprofil, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Klicken Sie auf **[!UICONTROL Profil aus Ordner(n) entfernen]** und wählen Sie den Ordner oder mehrere Ordner aus, aus denen das Profil entfernt werden soll. Klicken Sie dann auf **[!UICONTROL Fertig]**.

   Sie können sich vergewissern, dass das Videoprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Videoprofilen aus Ordnern über „Eigenschaften“ {#removing-video-profiles-from-folders-by-way-of-properties}

1. Klicken Sie auf das Adobe Experience Manager-Logo und gehen Sie zu **[!UICONTROL Assets]** und dann in den Ordner, aus dem Sie ein Videoprofil entfernen möchten.
1. Markieren Sie am Ordner das Kontrollkästchen, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Videoprofile]** die Option **[!UICONTROL Keine]** aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern und schließen]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
