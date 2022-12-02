---
title: Erstellen von Workflow-Modellen
seo-title: Creating Workflow Models
description: Sie erstellen ein Workflow-Modell, um die Schritte zu definieren, die ausgeführt werden, wenn ein Benutzer den Workflow startet.
seo-description: You create a workflow model to define the series of steps executed when a user starts the workflow.
uuid: 31071d3a-d6d5-4476-9ac0-7b335de406d9
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c097b60f-bcdf-45de-babe-b4c2e2b746a1
docset: aem65
exl-id: 6790202f-0542-4779-b3ce-d394cdba77b4
source-git-commit: 840ea373537799af995c3b8ce0c8bf575752775b
workflow-type: tm+mt
source-wordcount: '2464'
ht-degree: 100%

---

# Erstellen von Workflow-Modellen{#creating-workflow-models}

>[!CAUTION]
>
>Informationen zur Verwendung der klassischen Benutzeroberfläche finden Sie in der [Dokumentation zu AEM 6.3](https://helpx.adobe.com/de/experience-manager/6-3/help/sites-developing/workflows-models.html).

Sie erstellen ein [Workflow-Modell](/help/sites-developing/workflows.md#model), um die Schritte zu definieren, die ausgeführt werden, wenn ein Benutzer den Workflow startet. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt.

Wenn ein Benutzer einen Workflow startet, wird eine Instanz gestartet. Dabei handelt es sich um das entsprechende Laufzeitmodell, das erstellt wird, wenn Sie Ihre Änderungen durch Klicken auf [Sync](#sync-your-workflow-generate-a-runtime-model) synchronisieren.

## Erstellen neuer Workflows {#creating-a-new-workflow}

Wenn Sie zum ersten Mal ein neues Workflow-Modell erstellen, umfasst es Folgendes:

* Die Schritte **Fluss-Start** und **Fluss-Ende**.
Diese stellen den Anfang und das Ende des Workflows dar. Diese Schritte sind erforderlich und können nicht bearbeitet bzw. entfernt werden.
* Ein **Teilnehmer**-Beispielschritt namens **Schritt 1**.
Dieser Schritt ist so konfiguriert, dass er dem Workflow-Initiator ein Arbeitselement zuordnet. Sie können diesen Schritt nach Bedarf bearbeiten oder löschen und Schritte hinzufügen.

Gehen Sie folgendermaßen vor, um einen neuen Workflow mit dem Editor zu erstellen:

1. Öffnen Sie die **Workflow-Modelle-Konsole** über **Tools** > **Workflow** > **Modelle** oder beispielsweise über: [https://localhost:4502/aem/workflow](https://localhost:4502/aem/workflow)
1. Wählen Sie **Erstellen** und dann **Modell erstellen** aus.
1. Das Dialogfeld **Arbeitsablaufmodell hinzufügen** wird angezeigt. Geben Sie den **Titel** und den **Namen** (optional) ein. Wählen Sie anschließend **Fertig** aus.
1. Das neue Modell wird nun in der **Workflow-Modelle-Konsole** aufgeführt.
1. Wählen Sie Ihren neuen Workflow aus und öffnen Sie ihn dann, indem Sie auf [**Bearbeiten** klicken, um ihn zu konfigurieren](#editinganexistingworkflow):
   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>Wenn Sie Modelle programmgesteuert (mithilfe eines CRX-Pakets) erstellen, können Sie auch einen Unterordner erstellen:
>
>`/var/workflow/models`
>
>Beispiel: `/var/workflow/models/prototypes`
>
>Dieser Ordner kann anschließend zum [Verwalten des Zugriffs auf die Modelle in diesem Ordner](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that) verwendet werden.

## Bearbeiten von Workflows {#editing-a-workflow}

Sie können jedes vorhandene Workflow-Modell zu folgenden Zwecken bearbeiten:

* [zum Definieren von Schritten](#addingasteptoamodel-) und ihren [Parametern](#configuring-a-workflow-step)
* zum Konfigurieren von Workflow-Eigenschaften, einschließlich [Phasen](#configuring-workflow-stages-that-show-workflow-progress), [egal ob es sich um einen Übergangs-Workflow handelt](#creatingatransientworkflow-) und/oder [der Workflow mehrere Ressourcen verwendet](#configuring-a-workflow-for-multi-resource-support)

Das Bearbeiten eines (vordefinierten) [**Standard- bzw. Legacy**-Workflows](#editing-a-default-or-legacy-workflow-for-the-first-time) umfasst einen zusätzlichen Schritt, um sicherzustellen, dass eine [sichere Kopie](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) erstellt wird, bevor Sie Änderungen vornehmen.

Wenn Sie mit den Änderungen an Ihrem Workflow fertig sind, müssen Sie zum **Generieren eines Laufzeitmodells** auf **Sync** klicken. Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

### Synchronisieren von Workflows – Generieren von Laufzeitmodellen {#sync-your-workflow-generate-a-runtime-model}

Wenn Sie rechts in der Editor-Symbolleiste auf **Sync** klicken, wird ein [Laufzeitmodell](/help/sites-developing/workflows.md#runtime-model) generiert. Das Laufzeitmodell ist das Modell, das tatsächlich verwendet wird, wenn ein Benutzer einen Workflow startet. Wenn Sie Ihre Änderungen nicht durch Klicken auf **Sync** synchronisieren, stehen diese nicht zur Laufzeit zur Verfügung.

Wenn Sie (oder andere Benutzer) Änderungen am Workflow vornehmen, müssen Sie auf **Sync** klicken, um ein Laufzeitmodell zu erstellen, auch wenn einzelne Dialogfelder (z. B. für Schritte) eigene Optionen zum Speichern aufweisen.

Nachdem die Änderungen mit dem (gespeicherten) Laufzeitmodell synchronisiert wurden, wird stattdessen **Synchronisiert** angezeigt.

Bei einigen Schritten gibt es Pflichtfelder und/oder eine integrierte Validierung. Wenn die entsprechenden Bedingungen nicht erfüllt sind, wird eine Fehlermeldung angezeigt, falls Sie versuchen, das Modell mithilfe der Option **Sync** zu synchronisieren. Etwa wenn für einen **Teilnehmer**-Schritt kein Teilnehmer definiert wurde:

![wf-21](assets/wf-21.png)

### Erstmaliges Bearbeiten von Standard- oder Legacy-Workflows {#editing-a-default-or-legacy-workflow-for-the-first-time}

Wenn Sie ein [Standard- bzw. Legacy-Modell](/help/sites-developing/workflows.md#workflow-types) zur Bearbeitung öffnen, finden Sie die folgenden Bedingungen vor:

* Der Schritte-Browser (auf der linken Seite) ist nicht verfügbar.
* Die Symbolleiste weist eine Option zum **Bearbeiten** auf (auf der rechten Seite).
* Zunächst werden das Modell und seine Eigenschaften im schreibgeschützten Modus wie folgt dargestellt:
   * Standard-Workflows befinden sich unter `/libs`.
   * Legacy-Workflows befinden sich unter `/etc`.
Durch die Auswahl von 
**Bearbeiten** wird:
* eine Kopie des Workflows unter `/conf` gespeichert
* der Schritte-Browser verfügbar gemacht
* es möglich, Änderungen vorzunehmen.

>[!NOTE]
>
>Unter [Speicherorte von Workflow-Modellen](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) finden Sie weitere Informationen.

![wf-22](assets/wf-22.png)

### Hinzufügen von Schritten zu Modellen {#adding-a-step-to-a-model}

Sie müssen zu Ihrem Modell Schritte hinzufügen, um die auszuführende Aktivität darzustellen. Mit jedem Schritt wird eine bestimmte Aktivität ausgeführt. In einer Standard-AEM-Instanz stehen unterschiedliche Schrittkomponenten zur Auswahl.

Wenn Sie ein Modell bearbeiten, werden die verfügbaren Schritte in den verschiedenen Gruppen des **Schritte-Browsers** angezeigt. Beispiel:

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>Weitere Informationen zu den primären Schrittkomponenten, die mit AEM installiert werden, finden Sie in der [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md).

Gehen Sie folgendermaßen vor, um Schritte zu Ihrem Workflow-Modell hinzuzufügen:

1. Öffnen Sie ein vorhandenes Workflow-Modell zur Bearbeitung. Wählen Sie in der **Workflow-Modelle-Konsole** das gewünschte Modell aus und klicken Sie anschließend auf **Bearbeiten**.
1. Öffnen Sie über das Symbol **Seitliches Bedienfeld ein/aus** links in der oberen Symbolleiste den Schritte-Browser. Folgende Informationen/Optionen sind verfügbar:

   * Die Option **Filter** zum Filtern nach bestimmten Schritten.
   * Verwenden Sie das Dropdown-Menü, um die Auswahl auf eine bestimmte Gruppe von Schritten zu begrenzen.
   * Über das Symbol ![wf-stepinfo-icon](assets/wf-stepinfo-icon.png) zum Anzeigen von Breschreibungen können Sie weitere Informationen zum jeweiligen Schritt anzeigen.

   ![wf-02](assets/wf-02.png)

1. Ziehen Sie die entsprechenden Schritte an die gewünschte Stelle im Modell,

   beispielsweise einen **Teilnehmer-Schritt**.

   Nachdem Sie ihn zum Workflow hinzugefügt haben, können Sie [den Schritt konfigurieren](#configuring-a-workflow-step).

   ![wf-03](assets/wf-03.png)

1. Fügen Sie nach Bedarf Schritte hinzu oder nehmen Sie andere Änderungen vor.

   Zur Laufzeit werden die Schritte in der Reihenfolge ausgeführt, in der sie im Modell erscheinen. Nachdem Sie Schrittkomponenten hinzugefügt haben, können Sie diese an eine andere Stelle im Modell ziehen.

   Sie können vorhandene Schritte wie beim [Seiten-Editor](/help/sites-authoring/editing-content.md) darüber hinaus kopieren, ausschneiden, einfügen, gruppieren oder löschen.

   Unterteilte Schritte können auch mithilfe der Symbolleistenoption ![wf-collapseexpand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png) ein- oder ausgeblendet werden. 

1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **Sync** klicken, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

### Konfigurieren von Workflow-Schritten {#configuring-a-workflow-step}

Sie können das **Verhalten** von Workflow-Schritten über das Dialogfeld **Schritt-Eigenschaften** konfigurieren und anpassen.

1. Führen Sie zum Öffnen des Dialogfelds **Schritt-Eigenschaften** einen der folgenden Schritte durch:

   * Klicken/tippen Sie auf den **-Schritt im Workflow-Modell und wählen Sie in der Komponenten-Symbolleiste die Option **Konfigurieren** aus.

   * Doppelklicken Sie auf den Schritt.
   >[!NOTE]
   >
   >Weitere Informationen zu den primären Schrittkomponenten, die mit AEM installiert werden, finden Sie in der [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md).

1. Konfigurieren Sie die **Schritt-Eigenschaften** nach Bedarf. Die jeweils verfügbaren Eigenschaften hängen vom Schritttyp ab, ggf. stehen auch mehrere Registerkarten zur Verfügung. Beispiel: der standardmäßige **Teilnehmer-Schritt**, der in einem neuen Workflow als `Step 1` enthalten ist:

   ![wf-11](assets/wf-11.png)

1. Bestätigen Sie die Änderungen durch Klicken auf das Häkchen-Symbol.
1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **Sync** klicken, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

### Erstellen von Übergangs-Workflows {#creating-a-transient-workflow}

Sie können ein [Übergangs-](/help/sites-developing/workflows.md#transient-workflows)Workflow-Modell erstellen, wenn Sie ein neues Modell erstellen oder ein vorhandenes Modell bearbeiten:

1. Öffnen Sie das Workflow-Modell zur [Bearbeitung](#editinganexistingworkflow).
1. Wählen Sie in der Symbolleiste die Option **Eigenschaften für Workflow-Modell** aus.
1. Aktivieren Sie im Dialogfeld das Kontrollkästchen **Übergangs-Workflow** (bzw. deaktivieren Sie es, falls erforderlich):

   ![wf-07](assets/wf-07.png)

1. Bestätigen Sie die Änderung mit **Speichern und schließen** und klicken Sie anschließend in der Editor-Symbolleiste auf **Sync**, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

>[!NOTE]
>
>Beim Ausführen eines Workflows im [Übergangsmodus](/help/sites-developing/workflows.md#transient-workflows) speichert AEM keinen Workflow-Verlauf. Aus diesem Grund werden in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) keine Informationen zu diesem Workflow angezeigt.

## Workflow-Modelle in der Touch-Benutzeroberfläche verfügbar machen {#classic2touchui}

Befolgen Sie die Konfiguration, wenn ein Workflow-Modell der klassischen Benutzeroberfläche im Auswahl-Popup-Menü der **[!UICONTROL Zeitleiste]** in der Touch-Benutzeroberfläche fehlt und verfügbar gemacht werden muss. Die folgenden Schritte zeigen die Verwendung des Workflow-Modells namens **[!UICONTROL Aktivierungsanfrage]**.

1. Vergewissern Sie sich, dass das Modell nicht in der Touch-Benutzeroberfläche verfügbar ist. Greifen Sie über den Pfad `/assets.html/content/dam` auf ein Asset zu. Auswählen eines Assets. Öffnen Sie **[!UICONTROL Zeitleiste]** in der linken Leiste. Klicken Sie auf **[!UICONTROL Workflow starten]** und bestätigen Sie, dass das **[!UICONTROL Aktivierungsanfrage]**-Modell nicht in der Popup-Liste vorhanden ist.

1. Navigieren Sie wie folgt: **[!UICONTROL Tools > Allgemein > Tagging]**. Wählen Sie **[!UICONTROL Workflow]**.

1. Wählen Sie **[!UICONTROL Erstellen > Tag erstellen]**. Legen Sie den **[!UICONTROL Titel]** als `DAM` und den **[!UICONTROL Namen]** als `dam` fest. Klicken Sie auf **[!UICONTROL Übermitteln]**.
   ![Tag im Workflow-Modell erstellen](assets/workflow_create_tag.png)

1. Gehen Sie zu **[!UICONTROL Tools > Workflow > Modelle]**. Wählen Sie **[!UICONTROL Aktivierungsanfrage]** aus und wählen Sie dann **[!UICONTROL Bearbeiten]**.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]** und öffnen Sie das Menü **[!UICONTROL Seiteninformationen]**. Von dort wählen Sie **[!UICONTROL Eigenschaften öffnen]** und gehen Sie zur Registerkarte **[!UICONTROL Allgemein]** (falls noch nicht geöffnet).

1. Fügen Sie `Workflow : DAM` zum Feld **[!UICONTROL Tags]** hinzu. Bestätigen Sie die Auswahl mit dem Häkchen.

1. Bestätigen Sie das Hinzufügen des Tags mit **[!UICONTROL Speichern und schließen]**.
   ![Seiteneigenschaften des Modells bearbeiten](assets/workflow_model_edit_activation1.png)

1. Schließen Sie den Prozess mit **[!UICONTROL Synchronisieren]** ab. Der Workflow ist jetzt in der Touch-optimierten Benutzeroberfläche verfügbar.

### Konfigurieren von Workflows für die Unterstützung für mehrere Ressourcen {#configuring-a-workflow-for-multi-resource-support}

Sie konfigurieren ein Workflow-Modell für die [Unterstützung für mehrere Ressourcen](/help/sites-developing/workflows.md#multi-resource-support), wenn Sie ein neues Modell erstellen oder ein vorhandenes Modell bearbeiten:

1. Öffnen Sie das Workflow-Modell zur [Bearbeitung](#editinganexistingworkflow).
1. Wählen Sie in der Symbolleiste die Option **Eigenschaften für Workflow-Modell** aus.

1. Aktivieren Sie im Dialogfeld das Kontrollkästchen **Unterstützung für mehrere Ressourcen** (bzw. deaktivieren Sie es, falls erforderlich):

   ![wf-08](assets/wf-08.png)

1. Bestätigen Sie die Änderung mit **Speichern und schließen** und klicken Sie anschließend in der Editor-Symbolleiste auf **Sync**, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

### Konfigurieren von Workflow-Phasen (die den Workflow-Fortschritt anzeigen) {#configuring-workflow-stages-that-show-workflow-progress}

Die [Workflow-Phasen](/help/sites-developing/workflows.md#workflow-stages) sind hilfreich, um den Fortschritt eines Workflows beim Ausführen von Aufgaben anzuzeigen.

>[!CAUTION]
>
>Wenn Workflow-Phasen in **Seiteneigenschaften** definiert sind, aber für keinen der Workflow-Schritte verwendet werden, zeigt der Fortschrittsbalken keinen Fortschritt an (unabhängig vom aktuellen Workflow-Schritt).

Die jeweils verfügbaren Phasen werden in den Workflow-Modellen definiert. Die vorhandenen Workflow-Modelle können aktualisiert werden, um die Phasendefinitionen einzubinden. Sie können eine beliebige Anzahl von Phasen für das Workflow-Modell definieren.

Gehen Sie folgendermaßen vor, um **Phasen** zu definieren:

1. Öffnen Sie das Workflow-Modell zur Bearbeitung.
1. Wählen Sie in der Symbolleiste die Option **Eigenschaften für Workflow-Modell** aus. Wechseln Sie dann zur Registerkarte **Phasen**.
1. Fügen Sie Ihre gewünschten **Phasen** hinzu (und positionieren Sie sie). Sie können eine beliebige Anzahl von Phasen für das Workflow-Modell definieren.

   Beispiel:

   ![wf-08-1](assets/wf-08-1.png)

1. Klicken Sie zum Speichern der Eigenschaften auf **Speichern und schließen.**
1. Ordnen Sie jedem der Schritte im Workflow-Modell eine Phase zu. Beispiel:

   ![wf-09](assets/wf-09.png)

   Eine Phase kann mehreren Schritten zugeordnet werden. Beispiel:

   | **Schritt** | **Staging** |
   |---|---|
   | Schritt 1 | Erstellen |
   | Schritt 2 | Erstellen |
   | Schritt 3 | Überprüfung |
   | Schritt 4 | Genehmigen |
   | Schritt 5 | Genehmigen |
   | Schritt 6 | Fertig stellen |

1. Bestätigen Sie Ihre Änderungen, indem Sie in der Editor-Symbolleiste auf **Sync** klicken, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

## Exportieren von Workflow-Modellen in Pakete {#exporting-a-workflow-model-in-a-package}

Gehen Sie folgendermaßen vor, um ein Workflow-Modell in ein Paket zu exportieren:

1. Erstellen Sie mit [Package Manager](/help/sites-administering/package-manager.md#package-manager) ein neues Paket:

   1. Navigieren Sie über **Tools** > **Bereitstellung** > **Pakete** zu Package Manager.

   1. Klicken Sie auf **Paket erstellen**.
   1. Geben Sie den **Paketnamen** sowie alle weiteren erforderlichen Informationen an.
   1. Klicken Sie auf **OK**.

1. Klicken Sie in der Symbolleiste Ihres neuen Pakets auf **Bearbeiten**.

1. Öffnen Sie die Registerkarte **Filter**.

1. Wählen Sie **Filter hinzufügen** und geben Sie den Pfad zum *Design* Ihres Workflow-Modells ein:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   Klicken Sie auf **Fertig**.

1. Wählen Sie **Filter hinzufügen** und geben Sie den Pfad zu Ihrem *Laufzeit*-Workflow-Modell ein:

   `/var/workflow/models/<*your-model-name*>`

   Klicken Sie auf **Fertig**.

1. Fügen Sie weitere Filter für alle benutzerdefinierten Skripte hinzu, die von Ihrem Modell verwendet werden.
1. Klicken Sie auf **Speichern**, um Ihre Filterdefinitionen zu bestätigen.
1. Wählen Sie in der Symbolleiste Ihrer Paketdefinition die Option **Build** aus.
1. Wählen Sie in der Symbolleiste Ihres Pakets die Option **Herunterladen** aus.

## Verwenden von Workflows zum Verarbeiten von Formularübermittlungen {#using-workflows-to-process-form-submissions}

Sie können ein Formular so konfigurieren, dass es durch den ausgewählten Workflow verarbeitet wird. Wenn Benutzer das Formular übermitteln, wird eine neue Workflow-Instanz mit den Daten der Formularübermittlung als Payload erstellt.

Gehen Sie folgendermaßen vor, um den Workflow zur Verwendung mit Ihrem Formular zu konfigurieren:

1. Erstellen Sie eine neue Seite und öffnen Sie sie zur Bearbeitung.
1. Fügen Sie der Seite die Komponente **Formular** hinzu.
1. **Konfigurieren** Sie die Komponente **Formular-Start**, die auf der Seite angezeigt wird.
1. Wählen Sie mithilfe von **Workflow starten** den gewünschten Workflow aus den verfügbaren Optionen aus:

   ![wf-12](assets/wf-12.png)

1. Bestätigen Sie die neue Formularkonfiguration durch Klicken auf das Häkchen-Symbol.

## Testen von Workflows {#testing-workflows}

Beim Testen eines Workflows ist es sinnvoll, verschiedene Payload-Typen zu verwenden, auch solche, die sich von denen unterscheiden, für die der Workflow entwickelt wurde. Wenn Sie beispielsweise möchten, dass Ihr Workflow für die Verwendung mit Assets ausgelegt ist, testen Sie ihn, indem Sie eine Seite als Payload festlegen und sicherstellen, dass keine Fehler auftreten.

Testen Sie Ihren neuen Workflow beispielsweise wie folgt:

1. [Starten Sie Ihr Workflow-Modell](/help/sites-administering/workflows-starting.md) über die Konsole.
1. Definieren Sie die **Payload** und bestätigen Ihre Eingaben.

1. Ergreifen Sie die erforderlichen Maßnahmen, damit der Workflow fortgesetzt wird.
1. Überwachen Sie während der Ausführung des Workflows die Protokolldateien.

Sie können AEM auch so konfigurieren, dass die **DEBUG**-Meldungen in den Protokolldateien angezeigt werden. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md). Wenn die Entwicklung abgeschlossen ist, legen Sie die Einstellung für die **Protokollebene** wieder auf **Informationen** fest.

## Beispiele {#examples}

### Beispiel: Erstellen eines (einfachen) Workflows zum Annehmen oder Ablehnen einer Anfrage zur Veröffentlichung {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

Um einige der Möglichkeiten zur Erstellung eines Workflows zu veranschaulichen, wird im folgenden Beispiel eine Variante des Workflows `Publish Example` erstellt.

1. [Erstellen Sie ein neues Workflow-Modell](#creating-a-new-workflow).

   Der neue Workflow umfasst Folgendes:

   * **Prozessstart**
   * `Step 1`
   * **Prozessende**

1. Löschen Sie `Step 1` (da es sich um den falschen Schritttyp für dieses Beispiel handelt):

   * Klicken Sie auf den Schritt und klicken Sie in der Komponenten-Symbolleiste auf **Löschen**. Bestätigen Sie die Aktion.

1. Ziehen Sie aus der **Workflow**-Auswahl des Schritte-Browsers einen **Teilnehmer-Schritt** auf den Workflow und positionieren Sie ihn zwischen **Fluss-Start** und **Fluss-Ende**.
1. Führen Sie zum Öffnen des Dialogfelds „Eigenschaften“ einen der folgenden Schritte durch:

   * Klicken Sie auf den Teilnehmer-Schritt und klicken Sie in der Komponenten-Symbolleiste auf **Konfigurieren**.
   * Doppelklicken Sie auf den Teilnehmer-Schritt.

1. Geben Sie auf der Registerkarte **Allgemein** `Validate Content` als **Titel** und **Beschreibung** ein.
1. Öffnen Sie die Registerkarte **Benutzer/Gruppe**:

   * Aktivieren Sie das Kontrollkästchen **Benachrichtigen Sie den Benutzer per E-Mail**.
   * Wählen Sie für das Feld **Benutzer/Gruppe** die Option `Administrator` (`admin`) aus.

   >[!NOTE]
   >
   >Damit E-Mails versendet werden können, müssen [der E-Mail-Dienst und die Benutzerkontoinformationen konfiguriert werden](/help/sites-administering/notification.md).

1. Bestätigen Sie die Änderungen durch Klicken auf das Häkchen-Symbol.

   Daraufhin wird wieder die Übersicht über das Workflow-Modell angezeigt. Der Teilnehmer-Schritt ist nun in `Validate Content` umbenannt.

1. Ziehen Sie eine **ODER-Teilung** auf den Workflow und positionieren Sie sie zwischen `Validate Content` und **Fluss-Ende**.
1. Öffnen Sie die **ODER-Teilung** zur Konfiguration.
1. Konfigurieren:

   * **Allgemein**: Geben Sie den Teilungsnamen an.
   * **Zweig 1**: Wählen Sie **Standardroute** aus.

   * **Zweig 2**: Stellen Sie sicher, dass **Standardroute** nicht ausgewählt ist.

1. Bestätigen Sie die Änderungen an der **ODER-Teilung**.
1. Ziehen Sie einen **Teilnehmer-Schritt** auf den linken Zweig, öffnen Sie die Eigenschaften, geben Sie die folgenden Werte an und bestätigen Sie die Änderungen:

   * **Titel**: `Reject Publish Request`

   * **Benutzer/Gruppe**: z. B. `projects-administrators`

   * **Benachrichtigen des Benutzers per E-Mail**: Aktivieren Sie dieses Kontrollkästchen, damit die Benutzer per E-Mail benachrichtigt werden.

1. Ziehen Sie einen **Prozessschritt** auf den rechten Zweig, öffnen Sie die Eigenschaften, geben Sie die folgenden Werte an und bestätigen Sie die Änderungen:

   * **Titel**: `Publish Page as Requested`

   * **Prozess**: Wählen Sie `Activate Page` aus. Mit diesem Prozess wird die ausgewählte Seite in den Publisher-Instanzen veröffentlicht.

1. Klicken Sie in der Editor-Symbolleiste auf **Sync**, um das Laufzeitmodell zu generieren.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

   Ihr neues Workflow-Modell sieht dann wie folgt aus:

   ![wf-13](assets/wf-13.png)

1. Wenden Sie diesen Workflow auf Ihre Seite an, sodass Benutzer, die zur Phase **Fertig stellen** übergehen, den Schritt **Inhalt überprüfen** auswählen können, egal ob sie die **Seite wie angefordert veröffentlichen** oder die **Anfrage zur Veröffentlichung ablehnen** möchten.

   ![chlimage_1-72](assets/chlimage_1-72.png)

### Beispiel: Definieren einer Regel für eine ODER-Teilung     mit einem ECMA-Skript {#defineruleecmascript}

**ODER-Teilung**-Schritte ermöglichen es Ihnen, bedingte Verarbeitungspfade in Ihren Workflow einzubinden.

Gehen Sie folgendermaßen vor, um eine Regel für eine ODER-Teilung zu definieren:

1. Erstellen Sie zwei Skripte und speichern Sie diese im Repository, beispielsweise unter:

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >Die Skripte müssen eine [Funktion `check()`](#function-check) aufweisen, die einen booleschen Wert zurückgibt.

1. Bearbeiten Sie den Workflow und fügen Sie die **ODER-Teilung** zum Modell hinzu.
1. Bearbeiten Sie die Eigenschaften von **Zweig 1** der **ODER-Teilung**:

   * Definieren Sie dies als **Standardroute**, indem Sie den **Wert** auf `true` festlegen.

   * Geben Sie für **Regel** den Pfad zum Skript an. Beispiel:
      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   >
   >Sie können die Reihenfolge der Verzweigungen ändern, sofern dies erforderlich ist.

1. Bearbeiten Sie die Eigenschaften von **Zweig 2** der **ODER-Teilung**:

   * Geben Sie für **Regel** den Pfad zum anderen Skript an. Beispiel:
      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. Legen Sie die Eigenschaften der einzelnen Schritte in jedem Zweig fest. Stellen Sie sicher, dass die Einstellung für **Benutzer/Gruppe** festlegt ist.
1. Klicken Sie in der Editor-Symbolleiste auf **Sync**, um Ihre Änderungen am Laufzeitmodell beizubehalten.

   Weitere Informationen finden Sie unter [Synchronisieren von Workflows](#sync-your-workflow-generate-a-runtime-model).

#### Funktion „Check()“ {#function-check}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verwenden von ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).

Das folgende Beispielskript gibt `true` zurück, wenn es sich bei dem Knoten um einen `JCR_PATH` unter `/content/we-retail/us/en` handelt:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      }
     } else {
      return false;
     }
}
```

### Beispiel: Benutzerdefinierte Aktivierungsanfrage {#example-customized-request-for-activation}

Sie können jeden der vorkonfigurierten Workflows anpassen. Um das Verhalten anzupassen, überlagern Sie Details des entsprechenden Workflows.

Beispielsweise der Workflow **Aktivierungsanfrage**. Dieser wird für die Veröffentlichung von Seiten innerhalb von **Sites** verwendet und automatisch ausgelöst, wenn ein Inhaltsautor nicht über die entsprechenden Replikationsrechte verfügt. Weitere Informationen finden Sie unter [Anpassen der Seitenbearbeitung – Anpassen des Workflows „Aktivierungsanfrage“](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow).
