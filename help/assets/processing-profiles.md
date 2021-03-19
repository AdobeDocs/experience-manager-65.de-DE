---
title: Profile für die Verarbeitung von Metadaten, Bildern und Videos
description: Profile enthalten eine Reihe von Regeln rund um die Optionen, die auf in einen Ordner hochgeladene Assets angewendet werden. Geben Sie an, welches Metadaten- und welches Videokodierungsprofil auf Video-Assets angewendet werden soll, die Sie hochladen. Bei Bild-Assets können Sie auch angeben, welches Bildprofil auf Bild-Assets angewendet werden soll, um sie zuzuschneiden.
uuid: 6ded2a2f-a0d3-4f43-af97-02fbc0902c25
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b555bf0c-44cb-4fbf-abc4-15971663904d
docset: aem65
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: ebe7042b931869c3b4b7204e3ce7afa52d56f0ef
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 89%

---


# Profile für die Verarbeitung von Metadaten, Bildern und Videos{#profiles-for-processing-metadata-images-and-videos}

Profile sind Rezepte, die vorgeben, welche Optionen auf Assets angewendet werden, die in einen Ordner hochgeladen werden. Beispielsweise können Sie angeben, welches Metadatenprofil und welches Videokodierungsprofil auf Video-Assets angewendet wird, die Sie hochladen. Alternativ können Sie angeben, welche Imaging-Profile auf Image-Assets angewendet werden, damit sie entsprechend zugeschnitten werden.

Dazu kann das Hinzufügen von Metadaten, das smarte Zuschneiden von Bildern oder die Erstellung von Videokodierungsprofilen gehören. In AEM können Sie drei Arten von Profilen erstellen. Sie werden unter den folgenden Links detailliert vorgestellt:

* [Metadatenprofile](/help/assets/metadata-config.md#metadata-profiles)
* [Bildprofile](/help/assets/image-profiles.md)
* [Videoprofile](/help/assets/video-profiles.md)

Um Metadaten-, Bild- oder Videoprofile erstellen, bearbeiten oder löschen zu können, benötigen Sie Administratorrechte.

Nachdem Sie Ihr Metadaten-, Bild- oder Videoprofil erstellt haben, weisen Sie es mindestens einem Ordner zu, den Sie als Ziel für neu hochgeladene Assets verwenden.

Ein wichtiges Konzept zur Verwendung von Profilen in AEM Assets ist deren Zuweisung zu Ordnern. In einem Profil sind Einstellungen in Form von Metadatenprofilen zusammen mit Videoprofilen oder Bildprofilen enthalten. Mit diesen Einstellungen wird der Inhalt eines Ordners und seiner zugehörigen Unterordner verarbeitet. Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, hat daher eine erhebliche Auswirkung darauf, wie diese Assets durch ein Profil verarbeitet werden.
Indem Sie konsistente und geeignete Datei- und Ordnernamensstrategien zusammen mit angemessenen Metadatenpraktiken einsetzen, können Sie die Sammlung Ihrer digitalen Assets optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

>[!NOTE]
>
>Assets, die Sie von einem Ordner in einen anderen verschieben, werden nicht erneut verarbeitet. Angenommen, Sie verfügen über Ordner 1, dem das Profil A zugewiesen ist, und über Ordner 2, dem das Profil B zugewiesen ist. Wenn Sie die Assets aus Ordner 1 in Ordner 2 verschieben, behalten die verschobenen Assets ihre ursprüngliche Verarbeitung aus Ordner 1 bei.
>
>Dasselbe gilt auch, wenn Sie Assets zwischen zwei Ordnern verschieben, denen dasselbe Profil zugewiesen ist.

## Neuverarbeitung von Assets in einem Ordner {#reprocessing-assets}

>[!NOTE]
>
>Gilt nur für *Dynamic Media - Scene7-Modus* in AEM 6.4.6.0 oder höher.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Verarbeitungsprofil verfügt, das Sie nachträglich geändert haben.

Angenommen, Sie haben ein Bildprofil erstellt und es einem Ordner zugewiesen. Bei allen Bild-Assets, die Sie in den Ordner hochgeladen haben, wurde automatisch das Bildprofil auf die Assets angewendet. Später entscheiden Sie sich jedoch, dem Profil ein neues Verhältnis für den smarten Zuschnitt hinzuzufügen. Anstatt die Assets erneut auszuwählen und in den Ordner hochzuladen, führen Sie einfach den Workflow *Scene7: Assets erneut verarbeiten* aus.

Sie können den Neuverarbeitungs-Workflow für ein Asset ausführen, bei dem die Verarbeitung beim ersten Mal fehlgeschlagen ist. Selbst wenn Sie kein Verarbeitungsprofil bearbeitet oder angewendet haben, können Sie den Neuverarbeitungs-Workflow jederzeit für einen Asset-Ordner ausführen.

Sie können optional die Batch-Größe des Neuverarbeitungs-Workflows von 50 Assets bis zu 1000 Assets anpassen. Wenn Sie den Workflow _Scene7: Assets erneut verarbeiten_ für in einen Ordner ausführen, werden die Assets in Batches gruppiert und zur Verarbeitung an den Dynamic Media-Server gesendet. Nach der Verarbeitung werden die Metadaten der einzelnen Assets im gesamten Batch auf AEM aktualisiert. Wenn die Batch-Größe sehr groß ist, kann es zu einer Verzögerung bei der Verarbeitung kommen. Wenn die Batch-Größe zu klein ist, kann dies zu vielen Umläufen zum Dynamic Media-Server führen.

Siehe [Anpassen der Batch-Größe des Neuverarbeitungs-Workflows](#adjusting-load).

>[!NOTE]
>
>Wenn Sie eine Massenmigration von Assets von Dynamic Media Classic zu AEM durchführen, müssen Sie den Migrationsreplikationsagenten auf dem Dynamic Media-Server aktivieren. Stellen Sie nach Abschluss der Migration sicher, dass Sie den Agenten deaktivieren.
>
>Der Migrationsveröffentlichungsagent muss auf dem Dynamic Media-Server deaktiviert werden, damit der Neuverarbeitungs-Workflow erwartungsgemäß funktioniert.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**Neuverarbeitung von Assets in einem Ordner**:
1. Navigieren Sie in AEM auf der Seite „Assets“ zu einem Ordner mit Assets, dem ein Verarbeitungsprofil zugewiesen ist und für den Sie den Workflow **Scene7: Assets erneut verarbeiten** anwenden möchten.

   Bei Ordnern, denen bereits ein Verarbeitungsprofil zugewiesen wurde, wird der Name des Profils direkt unter dem Ordnernamen in der Kartenansicht angezeigt.

1. Wählen Sie einen Ordner aus.

   * Der Workflow berücksichtigt rekursiv alle Dateien in dem ausgewählten Ordner.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie neu.
   * Es empfiehlt sich, diesen Workflow nicht in einer Ordnerhierarchie mit mehr als 1.000 Assets auszuführen.

1. Klicken Sie oben links auf der Seite in der Dropdown-Liste auf **[!UICONTROL Zeitleiste.]**
1. Klicken Sie unten links auf der Seite rechts neben dem Kommentarfeld auf das Caret-Symbol (**^**).

   ![Workflow zur Neuverarbeitung von Assets 1](/help/assets/assets/reprocess-assets1.png)

1. Klicken Sie auf **[!UICONTROL Workflow starten.]**
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Beginn Workflow]** **[!UICONTROL Scene7: Assets neu verarbeiten.]**
1. (Optional) Geben Sie im Textfeld **Titel des Workflows eingeben** einen Namen für den Workflow ein. Sie können den Namen gegebenenfalls verwenden, um auf die Workflow-Instanz zu verweisen.

   ![Assets erneut verarbeiten 2](/help/assets/assets/reprocess-assets2.png)

1. Klicken Sie auf **[!UICONTROL Starten]** und dann auf **[!UICONTROL Bestätigen.]**

   Klicken Sie auf der Hauptseite der AEM-Konsole auf **[!UICONTROL Tools > Workflow, um den Workflow zu überwachen oder dessen Fortschritt zu überprüfen.]** Wählen Sie auf der Seite „Workflow-Instanzen“ einen Workflow aus. Klicken Sie in der Menüleiste auf **[!UICONTROL Offener Verlauf.]** Sie können einen ausgewählten Workflow auch auf derselben Seite „Workflow-Instanzen“ beenden, aussetzen oder umbenennen.

### Anpassen der Batch-Größe des Neuverarbeitungs-Workflows {#adjusting-load}

(Optional) Die standardmäßige Batch-Größe im Neuverarbeitungs-Workflow beträgt 50 Assets pro Auftrag. Diese optimale Stapelgröße wird durch die durchschnittliche Asset-Größe und die MIME-Typen von Assets bestimmt, auf denen die Neuverarbeitung ausgeführt wird. Ein höherer Wert bedeutet, dass ein Neuverarbeitungsauftrag viele Dateien enthalten wird. Dementsprechend wird das Verarbeitungsbanner länger für AEM-Assets angezeigt. Wenn die durchschnittliche Dateigröße jedoch nur 1 MB oder weniger beträgt, empfiehlt Adobe, den Wert auf mehrere Hundert, aber niemals mehr als 1.000 zu erhöhen. Wenn die durchschnittliche Dateigröße Hunderte von Megabyte beträgt, empfiehlt Adobe, die Batch-Größe auf bis zu 10 zu reduzieren.

**Anpassen der Batch-Größe des Neuverarbeitungs-Workflows**

1. Klicken Sie in Experience Manager auf **[!UICONTROL Adobe Experience Manager]**, um die globale Navigationskonsole aufzurufen, und klicken Sie dann auf das Symbol **[!UICONTROL Tools]** (Hammer) > **[!UICONTROL Workflow > Modelle.]**
1. Wählen Sie auf der Seite „Workflow-Modelle“ in der Karten- oder Listenansicht **[!UICONTROL Scene7: Assets erneut verarbeiten]** aus.

   ![Seite „Workflow-Modelle“ mit „Scene7: Assets erneut verarbeiten“ in der Kartenansicht ausgewählt](/help/assets/assets-dm/reprocess-assets7.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten.]** Eine neue Browser-Registerkarte öffnet die Workflow-Modellseite „Scene7: Assets erneut verarbeiten“.
1. Scene7: Workflow-Seite &quot;Assets neu verarbeiten&quot;rechts oben auf **[!UICONTROL Bearbeiten]** klicken, um den Workflow zu &quot;entsperren&quot;.
1. Wählen Sie im Workflow die Komponente Scene7 Batch Upload aus, um die Symbolleiste zu öffnen, und klicken Sie dann auf **[!UICONTROL Configure]** in der Symbolleiste.

   ![Komponente „Massen-Upload in Scene7“](/help/assets/assets-dm/reprocess-assets8.png)

1. Legen Sie im Dialogfeld **[!UICONTROL Massen-Upload zu Scene7 – Schritt-Eigenschaften]** Folgendes fest:
   * Geben Sie in die Textfelder **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** einen neuen Titel und eine neue Beschreibung für den Auftrag ein, falls gewünscht.
   * Wählen Sie **[!UICONTROL Handler-Modus]** aus, wenn der Handler mit dem nächsten Schritt fortfahren soll.
   * Geben Sie im Feld **[!UICONTROL Timeout]** den externen Prozess-Timeout (Sekunden) ein.
   * Geben Sie im Feld **[!UICONTROL Zeitraum]** ein Abrufintervall (Sekunden) ein, um zu testen, ob der externe Prozess abgeschlossen ist.
   * Geben Sie im Feld **[!UICONTROL Batch]** die maximale Anzahl von Assets (50-1.000) ein, die in einem Massen-Upload-Auftrag auf den Dynamic Media-Server verarbeitet werden sollen.
   * Wählen Sie **[!UICONTROL Bei Zeitüberschreitung fortsetzen]** aus, wenn Sie beim Erreichen des Zeitlimits fortfahren möchten. Auswahl abbrechen, wenn Sie zum Posteingang wechseln möchten, wenn der Timeout erreicht ist.

   ![Dialogfeld „Eigenschaften“](/help/assets/assets-dm/reprocess-assets3.png)

1. Klicken Sie in der rechten oberen Ecke des Dialogfelds **[!UICONTROL Batch Upload to Scene7 - Step Properties]** auf **[!UICONTROL Done]**.

1. Oben rechts im Scene7: Die Seite zum Workflow-Modell für Assets neu verarbeiten, klicken Sie auf **[!UICONTROL Synchronisieren]**. Wenn Sie **[!UICONTROL Synchronisiert]** sehen, ist das Workflow-Laufzeitmodell erfolgreich synchronisiert und bereit, Assets in einem Ordner erneut zu verarbeiten.

   ![Synchronisieren des Workflow-Modells](/help/assets/assets-dm/reprocess-assets1.png)

1. Schließen Sie die Browser-Registerkarte, auf der „Scene7: Assets erneut verarbeiten“ angezeigt wird.

<!--1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, click **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then click the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite.]**
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, click **[!UICONTROL Add.]** The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, click **[!UICONTROL Save All.]**
1. In the upper-left corner of the page, click **[!UICONTROL CRXDE Lite]** to return to the main AEM console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.-->
