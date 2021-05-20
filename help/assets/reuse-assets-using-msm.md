---
title: Wiederverwenden von Assets mit MSM
description: Sie können Assets für mehrere Seiten/Ordner verwenden, die aus übergeordneten Assets abgeleitet und mit diesen verknüpft sind. Die Assets bleiben mit einer Primärkopie synchronisiert und erhalten mit wenigen Klicks die Aktualisierungen von übergeordneten Assets.
contentOwner: AG
mini-toc-levels: 1
role: Business Practitioner, Administrator, Architect
feature: Asset-Management, Multi-Site-Manager
exl-id: 4d0367c4-88aa-4aef-b23d-828609b0df09
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3371'
ht-degree: 69%

---

# Wiederverwenden von mit MSM für Assets[!DNL Assets]{#reuse-assets-using-msm-for-assets}

Mit der Funktion &quot;Multi Site Manager&quot;(MSM) in [!DNL Adobe Experience Manager] können Benutzer Inhalte wiederverwenden, die einmal erstellt und über mehrere Webspeicherorte hinweg wiederverwendet werden. Dasselbe gilt für digitale Assets wie MSM für die Funktion [!DNL Assets]. Mit MSM für [!DNL Assets] können Sie:

* Einmal Assets anlegen und dann Kopien dieser Assets erstellen, um sie in anderen Bereichen der Site wiederzuverwenden.
* Halten Sie mehrere Kopien in Synchronisierung und aktualisieren Sie die ursprüngliche primäre Kopie einmal, um die Änderungen an die untergeordneten Kopien zu übertragen.
* Lokale Änderungen vornehmen, indem Sie die Verknüpfung zwischen übergeordneten und untergeordneten Assets vorübergehend oder dauerhaft unterbrechen.

## Voraussetzungen {#prereq}

Um MSM für [!DNL Assets] zu verwenden, installieren Sie mindestens [!DNL Experience Manager] 6.5 Service Pack 1. Weitere Informationen finden Sie unter [Versionshinweise des neuesten Service Packs](/help/release-notes/sp-release-notes.md).

## Wissenswertes über Vorteile und Konzepte {#concepts}

### Funktionsweise und Vorteile {#how-it-works-and-the-benefits}

Weitere Informationen zu Nutzungsszenarien einer Wiederverwendung identischer Inhalte (Text und Assets) über mehrere Web-Speicherorte hinweg finden Sie unter [Mögliche MSM-Szenarien](/help/sites-administering/msm.md). [!DNL Experience Manager] unterhält einen Link zwischen dem ursprünglichen Asset und dessen verknüpften Kopien, die als Live Copies (LCs) bezeichnet werden. Diese bestehende Verknüpfung ermöglicht Push-Übertragungen zentraler Änderungen an eine große Zahl von Live Copies. Auf diese Weise werden schnellere Aktualisierungen ermöglicht, während die mit der Verwaltung doppelter Kopien einhergehenden Beschränkungen entfallen. Die Übertragung von Änderungen erfolgt fehlerfrei und zentralisiert. Die Funktion lässt Raum für Aktualisierungen, die auf ausgewählte Live Copies beschränkt sind. Benutzer können die Verknüpfung trennen, d. h. die Vererbung unterbrechen, und lokale Bearbeitungen vornehmen, die nicht überschrieben werden, wenn die primäre Kopie das nächste Mal aktualisiert und Änderungen eingeführt werden. Die Trennung kann für einige ausgewählte Metadatenfelder oder für ein vollständiges Asset vorgenommen werden. Dies ermöglicht eine flexible lokale Aktualisierung von Assets, die ursprünglich von einer Primärkopie übernommen wurden.

MSM behält eine (Live-)Beziehung zwischen dem Quell-Asset und seinen Live Copies bei, sodass:

* Änderungen an den Quell-Assets auch auf Live Copies angewendet werden (Rollout), d. h., die Live Copies werden mit der Quelle synchronisiert;
* Sie Live Copies aktualisieren können, indem Sie die Live-Beziehung aussetzen oder die Vererbung für wenige begrenzte Felder entfernen. Die Änderungen an der Quelle werden nicht mehr auf die Live Copy angewendet.

### Glossar von MSM für [!DNL Assets]-Begriffe {#glossary}

**Quelle:** Die ursprünglichen Assets oder Ordner. Primäre Kopie, von der Live Copies abgeleitet werden.

**Live Copy:** Die Kopie der Quell-Assets/-Ordner, die mit der zugehörigen Quelle synchronisiert wird. Live Copies können eine Quelle für weitere Live Copies sein. Siehe „Erstellen von LCs“.

**Vererbung:** Ein Link/Verweis zwischen einem Live Copy-Asset/-Ordner und seiner Quelle, mit dem das System speichert, wo die Aktualisierungen gesendet werden. Eine Vererbung existiert für Metadatenfelder auf granularer Ebene. Die Vererbung kann für ausgewählte Metadatenfelder entfernt werden, während die Live-Beziehung zwischen Quelle und zugehöriger Live Copy beibehalten wird.

**Rollout:** Eine Aktion, durch die die Änderungen an der Quelle nachgelagert an die Live Copies weitergegeben werden. Es ist möglich, mithilfe der Aktion „Rollout“ eine oder mehrere Live Copies in einem Schritt zu aktualisieren. Siehe „Rollout“.

**Rollout-Konfiguration:**  Regeln, die bestimmen, welche Eigenschaften wie und wann synchronisiert werden. Diese Konfigurationen werden beim Erstellen von Live Copies angewendet und können später bearbeitet werden. Dabei kann ein untergeordnetes Element die Rollout-Konfiguration vom zugehörigen übergeordneten Asset übernehmen. Verwenden Sie für MSM für [!DNL Assets] nur die standardmäßige Rollout-Konfiguration. Die anderen Rollout-Konfigurationen sind für MSM für [!DNL Assets] nicht verfügbar.

**Synchronisieren:** Eine weitere Aktion, die zusätzlich zum Rollout für Parität zwischen Quelle und deren Live Copy sorgt, indem Aktualisierungen von der Quelle an Live Copies gesendet werden. Eine Synchronisierung wird für eine bestimmte Live Copy initiiert und die Aktion ruft die Änderungen von der Quelle ab. Mit dieser Aktion können Sie nur eine der Live Copies aktualisieren. Siehe „Aktion &#39;Synchronisieren&#39;“.

**Aussetzen:** Entfernt vorübergehend die Live-Beziehung zwischen einer Live Copy und dem zugehörigen Quell-Asset/-Ordner. Sie können die Beziehung wieder aufnehmen. Siehe „Aktion &#39;Aussetzen&#39;“.

**Fortsetzen:** Setzt die Live-Beziehung fort, damit eine Live Copy erneut Aktualisierungen von der Quelle erhält. Siehe „Aktion &#39;Fortsetzen&#39;“.

**Zurücksetzen:** Durch die Aktion &quot;Zurücksetzen&quot;wird die Live Copy wieder zu einer Replikation der Quelle, indem lokale Änderungen überschrieben werden. Außerdem werden abgebrochene Vererbungsvorgänge entfernt und Vererbungen in allen Metadatenfeldern zurückgesetzt. Für zukünftige lokale Änderungen müssen Sie die Vererbung bestimmter Felder erneut abbrechen. Siehe „Lokale Änderungen an LC“.

**Trennen:** Entfernt unwiderruflich die Live-Beziehung eines Live Copy-Assets/-Ordners. Nach der Aktion „Trennen“ können Live Copies niemals Aktualisierungen aus der Quelle empfangen und sie haben keinen Live Copy-Status mehr. Siehe „Entfernen von Beziehungen“.

## Erstellen von Live Copies eines Assets {#createlc}

Führen Sie einen der folgenden Schritte aus, um eine Live Copy aus einem oder mehreren Quell-Assets oder -Ordnern zu erstellen:

* Methode 1: Wählen Sie die Quell-Assets aus und klicken Sie oben in der Symbolleiste auf **[!UICONTROL Erstellen]** > **[!UICONTROL Live Copy]** .
* Methode 2: Klicken Sie in der [!DNL Experience Manager] -Benutzeroberfläche oben rechts auf **[!UICONTROL Erstellen]** > **[!UICONTROL Live Copy]** .

Sie können Live Copies eines Assets oder Ordners einzeln erstellen. Sie können Live Copies erstellen, die aus einem Asset oder Ordner abgeleitet werden, der ebenfalls eine Live Copy ist. Inhaltsfragmente werden für das Nutzungsszenario nicht unterstützt. Wenn Sie versuchen, deren Live Copies zu erstellen, werden die Inhaltsfragmente wie vorliegend und ohne Beziehung kopiert. Die kopierten Inhaltsfragmente sind eine Momentaufnahme und werden nicht zusammen mit den ursprünglichen Inhaltsfragmenten aktualisiert.

Führen Sie folgende Schritte aus, um Live Copies mit der ersten Methode zu erstellen:

1. Wählen Sie Quell-Assets oder -ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** > **[!UICONTROL Live Copy]**.

   ![Erstellen einer Live Copy über die  [!DNL Experience Manager] Benutzeroberfläche](assets/create_lc1.png)

   *Abbildung: Erstellen Sie eine Live Copy über die  [!DNL Experience Manager] Benutzeroberfläche.*

1. Wählen Sie einen Zielordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und Namen an. Assets haben keine untergeordneten Elemente. Wenn Sie eine Live Copy von Ordnern erstellen, können Sie die untergeordneten Elemente ein- oder ausschließen.
1. Wählen Sie eine Rollout-Konfiguration aus. Klicken Sie auf **[!UICONTROL Erstellen]**.

Führen Sie folgende Schritte aus, um Live Copies mit der zweiten Methode zu erstellen:

1. Klicken Sie in der [!DNL Experience Manager]-Benutzeroberfläche oben rechts auf **[!UICONTROL Erstellen]** > **[!UICONTROL Live Copy]**.

   ![Erstellen einer Live Copy über die  [!DNL Experience Manager] Benutzeroberfläche](assets/create_lc2.png)

   *Abbildung: Erstellen Sie eine Live Copy über die  [!DNL Experience Manager] Benutzeroberfläche.*

1. Wählen Sie Quell-Asset oder -ordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie einen Zielordner aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und Namen an. Assets haben keine untergeordneten Elemente. Wenn Sie eine Live Copy von Ordnern erstellen, können Sie die untergeordneten Elemente ein- oder ausschließen.
1. Wählen Sie eine Rollout-Konfiguration aus. Klicken Sie auf **[!UICONTROL Erstellen]**.

>[!NOTE]
>
>Wenn eine Quelle oder Live Copy verschoben wird, werden die Beziehungen beibehalten. Wenn eine Live Copy gelöscht wird, werden die Beziehungen entfernt.

## Anzeigen verschiedener Eigenschaften und Status von Quelle und Live Copy {#properties}

Sie können die Informationen und MSM-bezogenen Status von Live Copies wie Beziehung, Synchronisierung, Rollouts und mehr aus den verschiedenen Bereichen der [!DNL Experience Manager]-Benutzeroberfläche anzeigen.

Die folgenden beiden Methoden funktionieren für Assets und Ordner:

* Wählen Sie ein Live Copy-Asset aus und suchen Sie nach Informationen auf der zugehörigen Eigenschaftenseite.
* Wählen Sie den Quellordner aus und suchen Sie die detaillierten Informationen zu den einzelnen Live Copies über die [!UICONTROL Live Copy-Konsole].

>[!TIP]
>
>Um den Status einiger separater Live Copies zu überprüfen, verwenden Sie die erste Methode, um die Seite **[!UICONTROL Eigenschaften]** zu überprüfen. Um den Status vieler Live Copies zu überprüfen, verwenden Sie die zweite Methode, um die Seite **[!UICONTROL Beziehungsstatus]** zu überprüfen.

### Informationen und Status von Live Copies   {#statuslcasset}

Führen Sie folgende Schritte aus, um Informationen und Status eines Live Copy-Assets oder -Ordners zu prüfen.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy]**. Sie können den Pfad der Quelle, den Aussetzen-Status, den Synchronisierungsstatus, das letzte Rollout-Datum und den Benutzer, der das letzte Rollout durchgeführt hat, prüfen.

   ![Live Copy-Informationen und -Status werden in einer Konsole in den Eigenschaften angezeigt](assets/lcfolder_info_properties.png)

   *Abbildung: Live Copy-Informationen und -Status.*

1. Eine Aktivierung oder Deaktivierung ist möglich, wenn untergeordnete Assets die Live Copy-Konfiguration übernehmen.

1. Sie können die Option für die Live Copy wählen, um die Rollout-Konfiguration vom übergeordneten Asset zu übernehmen oder die Konfiguration zu ändern.

### Informationen und Status aller Live Copies eines Ordners {#status-lc-folder}

[!DNL Experience Manager] stellt eine Konsole bereit, um die Status aller Live Copies eines Quellordners zu prüfen. Diese Konsole zeigt den Status aller untergeordneten Assets an.

1. Wählen Sie einen Quellordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy-Quelle]**. Klicken Sie auf **[!UICONTROL Live Copy-Übersicht]**, um die Konsole zu öffnen. Dieses Dashboard liefert übergeordnete Statusinformationen aller untergeordneten Assets.

   ![Anzeigen der Status von Live Copies in der Live Copy-Konsole der Quelle](assets/livecopy-statuses.png)

   *Abbildung: Anzeigen des Status von Live Copies in der  [!UICONTROL Live Copy-] Konsole der Quelle*

1. Um die detaillierten Informationen zu den einzelnen Assets im Ordner „Live Copy“ anzuzeigen, wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Beziehungsstatus]**.

   ![Detaillierte Informationen und Status eines untergeordneten Live Copy-Assets in einem Ordner](assets/livecopy_relationship_status.png)

   Detaillierte Informationen und Status eines untergeordneten Live Copy-Assets in einem Ordner

>[!TIP]
>
>Sie können die Status von Live Copies anderer Ordner schnell sehen, ohne zu viel durchsuchen zu müssen. Ändern Sie den Ordner im oberen mittleren Teil der **[!UICONTROL Live Copy-Übersicht]**-Benutzeroberfläche.

### Schnellaktionen in der Leiste „Verweise“ für Quellen {#refrailsource}

Für Quell-Assets oder -ordner können Sie die folgenden Informationen über die Leiste „Verweise“ anzeigen und die folgenden Aktionen von dort aus direkt ausführen:

* Anzeigen der Pfade von Live Copies
* Öffnen oder zeigen Sie eine bestimmte Live Copy in der [!DNL Experience Manager]-Benutzeroberfläche an.
* Synchronisieren von Aktualisierungen mit einer bestimmten Live Copy
* Aussetzen der Beziehung oder Ändern der Rollout-Konfiguration für eine bestimmte Live Copy
* Zugreifen auf die Konsole „Live Copy-Übersicht“

Wählen Sie Quell-Asset oder -ordner aus, öffnen Sie die linke Leiste und klicken Sie auf **[!UICONTROL Verweise]**. Sie können auch ein Asset oder einen Ordner auswählen und den Tastaturbefehl `Alt + 4` verwenden.

![In der Leiste „Verweise“ für die ausgewählte Quelle verfügbare Aktionen und Informationen](assets/referencerail_source.png)

*Abbildung: Aktionen und Informationen, die in der Leiste &quot;Verweise&quot;für die ausgewählte Quelle verfügbar sind.*

Klicken Sie für eine bestimmte Live Copy auf **[!UICONTROL Live Copy bearbeiten]**, um die Beziehung auszusetzen oder die Rollout-Konfiguration zu ändern.

![Für eine bestimmte Live Copy ist die Option zum Aussetzen der Beziehung oder Ändern der Rollout-Konfiguration über die Leiste &quot;Verweise&quot;verfügbar, wenn das Quell-Asset ausgewählt ist.](assets/referencerail_editlc_options.png)

*Abbildung: Aussetzen der Beziehung oder Ändern der Rollout-Konfiguration einer bestimmten Live Copy*

### Schnellaktionen in der Leiste „Verweise“ für Live Copies   {#ref-rail-lc}

Für Live Copy-Assets oder -Ordner können Sie die folgenden Informationen über die Leiste „Verweise“ anzeigen und die folgenden Aktionen von dort aus direkt ausführen:

* Anzeigen des Pfads der zugehörigen Quelle.
* Öffnen oder zeigen Sie eine bestimmte Live Copy in der [!DNL Experience Manager]-Benutzeroberfläche an.
* Stellen Sie die Aktualisierungen bereit.

Wählen Sie Live Copy-Asset oder -Ordner aus, öffnen Sie die linke Leiste und klicken Sie auf **[!UICONTROL Verweise]**. Sie können auch ein Asset oder einen Ordner auswählen und den Tastaturbefehl `Alt + 4` verwenden.

![In der Leiste „Verweise“ für die ausgewählte Live Copy verfügbare Aktionen](assets/referencerail_livecopy.png)

*Abbildung: In der Leiste &quot;Verweise&quot;für die ausgewählte Live Copy verfügbare Aktionen.*

## Übertragen von Änderungen von der Quelle an Live Copies   {#rolloutsync}

Nach der Bearbeitung einer Quelle können die Änderungen entweder mithilfe einer Aktion „Synchronisieren“ oder „Rollout“ an die Live Copies übertragen werden. Informationen zu den Unterschieden zwischen beiden Aktionen finden Sie im [Glossar](#glossary).

### Aktion „Rollout“  {#rollout}

Sie können eine Aktion „Rollout“ über das Quell-Asset initiieren und alle oder einige ausgewählte Live Copies aktualisieren.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy-Quelle]**. Klicken Sie in der Symbolleiste auf **[!UICONTROL Rollout]** .
1. Wählen Sie die zu aktualisierenden Live Copies aus. Klicken Sie auf **[!UICONTROL Rollout]**.
1. Um ein Rollout der an den untergeordneten Assets vorgenommenen Aktualisierungen durchzuführen, wählen Sie **[!UICONTROL Rollout von Quelle und allen untergeordneten Elementen]** aus.

   ![Rollout von Quelländerungen an einige oder alle Live Copies](assets/livecopy_rollout_page.png)

   *Abbildung: Rollout von Quelländerungen an einige oder alle Live Copies.*

>[!NOTE]
>
>Änderungen an einem Quell-Asset werden nur den Live Copies mit einem direkten Verweis bereitgestellt. Wenn eine Live Copy von einer anderen Live Copy abgeleitet wird, werden die Änderungen nicht der abgeleiteten Live Copy bereitgestellt.

Sie können eine Aktion „Rollout“ auch über die Leiste „Verweise“ initiieren, nachdem Sie eine bestimmte Live Copy ausgewählt haben. Weitere Informationen finden Sie unter [Schnellaktionen in der Leiste „Verweise“ für Live Copies](#ref-rail-lc). Bei dieser Rollout-Methode werden nur die ausgewählte Live Copy und optional deren untergeordnete Elemente aktualisiert.

![Rollout von Quelländerungen an die ausgewählte Live Copy](assets/livecopy_rollout_dialog.png)

*Abbildung: Rollout der Quelländerungen an die ausgewählte Live Copy*

### Wissenswertes über die Aktion „Synchronisieren“ {#about-sync}

Durch eine Aktion „Synchronisieren“ werden die Änderungen einer Quelle nur an die ausgewählte Live Copy übertragen. Die Aktion „Synchronisieren“ respektiert und bewahrt die lokalen Änderungen, die nach dem Abbrechen der Vererbung vorgenommen wurden. Die lokalen Änderungen werden nicht überschrieben und die abgebrochene Vererbung wird nicht wiederhergestellt. Sie haben drei Möglichkeiten, um eine Aktion „Synchronisieren“ zu initiieren.

| Wo in der [!DNL Experience Manager]-Benutzeroberfläche | Zeitpunkt und Grund für die Verwendung | Informationen zur Verwendung |
|---|---|---|
| [!UICONTROL Leiste „Verweise“] | Schnelles Synchronisieren bei bereits ausgewählter Quelle | Siehe [Schnellaktionen in der Leiste „Verweise“ für Quellen](#refrailsource) |
| Symbolleiste auf der Seite [!UICONTROL Eigenschaften] | Initiieren von Synchronisationen bei bereits öffneten Live Copy-Eigenschaften | Siehe [Synchronisieren von Live Copies](#sync-lc) |
| [!UICONTROL Konsole „Live Copy-Übersicht“] | Schnelles Synchronisieren mehrerer Assets (nicht notwendigerweise aller), wenn der Quellordner ausgewählt ist oder die Konsole [!UICONTROL Live Copy-Übersicht] bereits geöffnet ist. Initiieren der Aktion „Synchronisieren“ für jeweils ein Asset, aber eine schnellere Methode, um mehrere Assets auf einmal zu synchronisieren | Siehe [Aktionen für viele Assets in einem Live Copy-Ordner](#bulk-actions) |

### Synchronisieren von Live Copies    {#sync-lc}

Um eine Aktion „Synchronisieren“ zu starten, öffnen Sie die Seite **[!UICONTROL Eigenschaften]** einer Live Copy, klicken Sie auf **[!UICONTROL Live Copy]** und dann auf die gewünschte Aktion in der Symbolleiste.

Anweisungen zum Anzeigen von Status und Informationen zu einer Aktion „Synchronisieren“ finden Sie unter [Informationen und Status von Live Copies](#statuslcasset) sowie [Informationen und Status aller Live Copies eines Ordners](#status-lc-folder).

![Aktion „Synchronisieren“ – Abrufen von Quelländerungen](assets/livecopy_sync.png)

*Abbildung: Aktion &quot;Synchronisieren&quot;ruft die an der Quelle vorgenommenen Änderungen ab.*

>[!NOTE]
>
>Wenn die Beziehung ausgesetzt ist, ist die Aktion „Synchronisieren“ in der Symbolleiste nicht verfügbar. Ist die Aktion „Synchronisieren“ in der Leiste „Verweise“ verfügbar, werden die Änderungen auch bei erfolgreichem Rollout nicht übertragen.

## Aussetzen und Fortsetzen der Beziehung {#suspend-resume}

Sie können die Beziehung vorübergehend aussetzen, um zu verhindern, dass eine Live Copy am Quell-Asset oder -ordner vorgenommene Änderungen erhält. Die Beziehung kann für die Live Copy auch fortgesetzt werden, um Änderungen von der Quelle zu erhalten.

Zum Aussetzen oder Fortsetzen öffnen Sie die Seite **[!UICONTROL Eigenschaften]** einer Live Copy, klicken Sie auf **[!UICONTROL Live Copy]** und dann auf die gewünschte Aktion in der Symbolleiste.

Beziehungen von mehreren Assets in einem Live Copy-Ordner können auch schnell über die Konsole **[!UICONTROL Live Copy-Übersicht]** ausgesetzt oder fortgesetzt werden. Siehe [Ausführen von Aktionen für viele Assets in einem Live Copy-Ordner](#bulk-actions).

## Lokales Ändern von Live Copies {#local-mods}

Eine Live Copy ist eine Replikation der ursprünglichen Quelle zum Zeitpunkt ihrer Erstellung. Die Metadatenwerte einer Live Copy werden von der Quelle übernommen. Die Metadatenfelder halten einzeln die Vererbung mit den entsprechenden Feldern des Quell-Assets aufrecht.

Sie haben jedoch die Flexibilität, lokale Änderungen an einer Live Copy vorzunehmen, um einige ausgewählte Eigenschaften zu ändern. Um lokale Änderungen vorzunehmen, brechen Sie die Vererbung der gewünschten Eigenschaft ab. Wenn die Vererbung von mindestens einem Metadatenfeld abgebrochen wird, werden Live-Beziehung des Assets und Vererbung der anderen Metadatenfelder beibehalten. Bei einer Synchronisierung oder einem Rollout werden die lokalen Änderungen nicht überschrieben. Öffnen Sie dazu die Seite **[!UICONTROL Eigenschaften]** eines Live Copy-Assets und klicken Sie auf die Option **[!UICONTROL Vererbung abbrechen]** neben einem Metadatenfeld.

Sie können alle lokalen Änderungen rückgängig machen und das Asset auf den Status seiner Quelle zurücksetzen. Setzen Sie die Aktion unwiderruflich zurück, überschreiben Sie sofort alle lokalen Änderungen und stellen Sie die Vererbung bei allen Metadatenfeldern wieder her. Zwecks Wiederherstellung klicken Sie auf der Seite **[!UICONTROL Eigenschaften]** eines Live Copy-Assets in der Symbolleiste auf **[!UICONTROL Zurücksetzen]**.

![Aktion „Zurücksetzen“ – Überschreiben lokaler Bearbeitungen und Abgleichen der Live Copy mit der zugehörigen Quelle](assets/livecopy_reset.png)

*Abbildung: Aktion &quot;Zurücksetzen&quot;- Überschreiben lokaler Bearbeitungen und Abgleichen der Live Copy mit der zugehörigen Quelle*

## Entfernen von Live-Beziehungen   {#detach}

Sie können die Beziehung zwischen Quelle und Live Copy mit der Aktion „Trennen“ vollständig entfernen. Nach dem Trennen wird die Live Copy zu einem eigenständigen Asset oder Ordner. Sie wird unmittelbar nach dem Trennen in der [!DNL Experience Manager]-Benutzeroberfläche als neues Asset angezeigt. Führen Sie die folgenden Schritte aus, um eine Live Copy von ihrer Quelle zu trennen.

1. Wählen Sie ein Live Copy-Asset oder einen Ordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.

1. Klicken Sie auf **[!UICONTROL Live Copy]**. Klicken Sie in der Symbolleiste auf **[!UICONTROL Trennen]**. Klicken Sie im angezeigten Dialogfeld auf **[!UICONTROL Trennen]**.

   ![Aktion „Trennen“ – vollständiges Entfernen der Beziehung zwischen Quelle und Live Copy](assets/livecopy_detach.png)

   *Abbildung: Die Aktion &quot;Trennen&quot;entfernt die Beziehung zwischen Quelle und Live Copy vollständig.*

   >[!CAUTION]
   >
   >Die Beziehung wird entfernt, sobald Sie im Dialogfeld auf **[!UICONTROL Trennen]** klicken. Sie können diesen Vorgang nicht rückgängig machen, indem Sie auf der Seite „Eigenschaften“ auf **[!UICONTROL Abbrechen]** klicken.

Mehrere Assets in einem Live Copy-Ordner können auch schnell über die Konsole **[!UICONTROL Live Copy-Übersicht]** getrennt werden. Siehe [Ausführen von Aktionen für viele Assets in einem Live Copy-Ordner](#bulk-actions).

## Massenaktionen in einem Live Copy-Ordner {#bulk-actions}

Wenn mehrere Assets in einem Live Copy-Ordner vorhanden sind, kann das Initiieren von Aktionen für jedes Asset mühsam sein. Sie können die grundlegenden Aktionen für viele Assets schnell über [!UICONTROL Live Copy-Konsole] starten. Die oben genannten Methoden können nach wie vor für einzelne Assets verwendet werden.

1. Wählen Sie einen Quellordner aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**. Sie können auch den Tastaturbefehl `p` verwenden.
1. Klicken Sie auf **[!UICONTROL Live Copy-Quelle]**. Klicken Sie auf **[!UICONTROL Live Copy-Übersicht]**, um die Konsole zu öffnen.
1. Wählen Sie in diesem Dashboard ein Live Copy-Asset aus einem Live Copy-Ordner aus. Klicken Sie in der Symbolleiste auf die gewünschten Aktionen. Die verfügbaren Aktionen sind **[!UICONTROL Synchronisieren]**, **[!UICONTROL Zurücksetzen]**, **[!UICONTROL Aussetzen]** und **[!UICONTROL Lösen]**. Sie können diese Aktionen schnell für beliebige Assets in einer beliebigen Anzahl von Live Copy-Ordnern starten, die sich in einer Live-Beziehung mit dem ausgewählten Quellordner befinden.

   ![Einfaches Aktualisieren vieler Assets in Live Copy-Ordnern über die Konsole „Live Copy-Übersicht“](assets/livecopyconsole_update_many_assets.png)

   *Abbildung: Einfaches Aktualisieren vieler Assets in Live Copy-Ordnern über die  [!UICONTROL Live Copy-] Übersichtskonsole*

## Erweitern Sie MSM für [!DNL Assets] {#extend-api}

[!DNL Experience Manager] ermöglicht es, die Funktionalität mithilfe der MSM-Java-APIs zu erweitern. Bei [!DNL Assets] funktioniert die Erweiterung genauso wie bei MSM für [!DNL Sites]. Weitere Details finden Sie unter [Erweitern von MSM](/help/sites-developing/extending-msm.md) sowie Informationen zu bestimmten Aufgaben in den folgenden Abschnitten:

* [Übersicht über APIs](/help/sites-developing/extending-msm.md#overview-of-the-java-api)
* [Synchronisierungsaktion erstellen](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action)
* [Erstellen einer Rollout-Konfiguration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration)
* [Erstellen und Verwenden einer einfachen LiveActionFactory-Klasse](/help/sites-developing/extending-msm.md#creating-and-using-a-simple-liveactionfactory-class)

>[!NOTE]
>
>* Blueprint in MSM für [!DNL Sites] wird in MSM als Live Copy-Quelle für [!DNL Assets] bezeichnet.
>* Das Entfernen des Kapitelschritts im Assistenten zum Erstellen einer Site wird in MSM für [!DNL Assets] nicht unterstützt.
>* Die Konfiguration von MSM-Sperren in den Seiteneigenschaften (Touch-optimierte Benutzeroberfläche) wird in MSM für [!DNL Assets] nicht unterstützt.


## Auswirkungen von Asset-Management-Aufgaben auf Live Copies {#manage-assets}

Live Copies und Quellen sind Assets oder Ordner, die in gewissem Umfang als digitale Assets verwaltet werden können. Einige Asset-Management-Aufgaben in [!DNL Experience Manager] wirken sich spezifisch auf die Live Copies aus.

* Beim Kopieren einer Live Copy wird ein Live Copy-Asset mit derselben Quelle wie bei der ersten Live Copy erstellt.
* Wenn Sie eine Quelle oder eine Live Copy verschieben, wird die Live-Beziehung beibehalten.
* Die Aktion „Bearbeiten“ funktioniert nicht bei Live Copy-Assets. Wenn die Quelle einer Live Copy selbst eine Live Copy ist, kann die Aktion „Bearbeiten“ für diese nicht eingesetzt werden.
* Die Aktion „Checkout“ ist nicht für Live Copy-Assets verfügbar.
* Für Quellordner ist die Option zum Erstellen von Prüfungsaufgaben verfügbar.
* Beim Anzeigen der Asset-Liste in der Listen- und Spaltenansicht sind Live Copy-Assets oder -Ordner mit „Live Copy“ gekennzeichnet. Dadurch können Sie Live Copies in einem Ordner leicht identifizieren.

## MSM für [!DNL Assets] und [!DNL Sites] vergleichen {#comparison}

In anderen Szenarien entspricht MSM für [!DNL Assets] dem Verhalten der MSM für Sites-Funktionalität. Einige wichtige Unterschiede lauten wie folgt:

* Blueprint in MSM für [!DNL Sites] wird in MSM als Live Copy-Quelle für [!DNL Assets] bezeichnet.
* In Sites können Sie einen Blueprint mit seiner Live Copy vergleichen, in [!DNL Assets] ist es jedoch nicht möglich, eine Quelle mit ihrer Live Copy zu vergleichen.
* Sie können eine Live Copy nicht in [!DNL Assets] bearbeiten.
* Sites haben normalerweise untergeordnete Elemente, [!DNL Assets] jedoch nicht. Die Option zum Ein- oder Ausschließen von untergeordneten Elementen ist beim Erstellen von Live Copies einzelner Assets nicht vorhanden.
* Das Entfernen des Kapitelschritts im Assistenten zum Erstellen einer Site wird in MSM für [!DNL Assets] nicht unterstützt.
* Die Konfiguration von MSM-Sperren für Seiteneigenschaften (Touch-optimierte Benutzeroberfläche) wird in MSM für [!DNL Assets] nicht unterstützt.
* Verwenden Sie für MSM für [!DNL Assets] nur die **[!UICONTROL Standard-Rollout-Konfiguration]**. Die anderen Rollout-Konfigurationen sind für MSM für [!DNL Assets] nicht verfügbar.

## Best Practices {#best-practices}

Zu Best Practices für MSM gehören:

* Planen Sie die Beziehungen zwischen über- und untergeordneten Assets und Inhaltsflüssen, bevor Sie mit der Implementierung beginnen.

## Beschränkungen und bekannte Probleme bei MSM für [!DNL Assets] {#limitations}

Folgende Beschränkung besteht für MSM für [!DNL Assets].

* Inhaltsfragmente werden für das Nutzungsszenario nicht unterstützt. Wenn Sie versuchen, deren Live Copies zu erstellen, werden die Inhaltsfragmente wie vorliegend und ohne Beziehung kopiert. Die kopierten Inhaltsfragmente sind Momentaufnahmen und werden nicht aktualisiert, wenn die ursprünglichen Inhaltsfragmente aktualisiert werden.

* MSM funktioniert nicht mit aktiviertem Metadaten-Writeback. Beim Zurückschreiben bricht die Vererbung.
