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
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Profiles for processing metadata, images, and videos{#profiles-for-processing-metadata-images-and-videos}

Profile sind Rezepte, die vorgeben, welche Optionen auf Assets angewendet werden, die in einen Ordner hochgeladen werden. Beispielsweise können Sie angeben, welches Metadatenprofil und welches Videokodierungsprofil auf Video-Assets angewendet wird, die Sie hochladen. Alternativ können Sie angeben, welche Imaging-Profile auf Image-Assets angewendet werden, damit sie entsprechend zugeschnitten werden.

Dazu kann das Hinzufügen von Metadaten, das smarte Zuschneiden von Bildern oder die Erstellung von Videokodierungsprofilen gehören. In AEM können Sie drei Arten von Profilen erstellen. Sie werden unter den folgenden Links detailliert vorgestellt:

* [Metadatenprofile](/help/assets/metadata-profiles.md)
* [Bildprofile](/help/assets/image-profiles.md)
* [Videoprofile](/help/assets/video-profiles.md)

Um Metadaten-, Bild- oder Videoprofile erstellen, bearbeiten oder löschen zu können, benötigen Sie Administratorrechte.

Nachdem Sie Ihr Metadaten-, Bild- oder Videoprofil erstellt haben, weisen Sie es mindestens einem Ordner zu, den Sie als Ziel für neu hochgeladene Assets verwenden.

Ein wichtiges Konzept zur Verwendung von Profilen in AEM Assets ist deren Zuweisung zu Ordnern. In einem Profil sind Einstellungen in Form von Metadatenprofilen zusammen mit Videoprofilen oder Bildprofilen enthalten. Mit diesen Einstellungen wird der Inhalt eines Ordners und seiner zugehörigen Unterordner verarbeitet. Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, hat daher eine erhebliche Auswirkung darauf, wie diese Assets durch ein Profil verarbeitet werden.
Indem Sie konsistente und geeignete Datei- und Ordnernamensstrategien zusammen mit angemessenen Metadatenpraktiken einsetzen, können Sie die Sammlung Ihrer digitalen Assets optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

>[!NOTE]
>
>Assets, die Sie von einem Ordner zum nächsten verschieben, werden nicht erneut verarbeitet. Angenommen, Sie haben Ordner 1, dem Profil A zugewiesen ist, und Ordner 2, dem Profil B zugewiesen ist. Wenn Sie Assets aus Ordner 1 in Ordner 2 verschieben, behalten die verschobenen Assets ihre ursprüngliche Verarbeitung aus Ordner 1 bei.
>
>Dasselbe gilt auch, wenn Sie Assets zwischen zwei Ordnern verschieben, denen dasselbe Profil zugewiesen ist.

## Neuverarbeitung von Assets in einem Ordner {#reprocessing-assets}

>[!NOTE]
>
>Gilt nur für *dynamische Medien - Scene7-Modus* in AEM 6.4.6.0 oder höher.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein bestehendes Verarbeitungsprofil verfügt, das Sie später geändert haben.

Angenommen, Sie haben ein Bildprofil erstellt und es einem Ordner zugewiesen. Bei allen Bild-Assets, die Sie in den Ordner hochgeladen haben, wurde automatisch das Bildprofil auf die Assets angewendet. Später entscheiden Sie sich jedoch, dem Profil ein neues Verhältnis für intelligente Beschneidung hinzuzufügen. Anstatt die Assets erneut auszuwählen und in den Ordner hochzuladen, führen Sie einfach *Scene7 aus: Arbeitsablauf für Assets* neu verarbeiten.

Sie können den Arbeitsablauf für die Neuverarbeitung für ein Asset ausführen, bei dem die Verarbeitung zum ersten Mal fehlgeschlagen ist. Selbst wenn Sie kein Verarbeitungsprofil bearbeitet oder ein Verarbeitungsprofil angewendet haben, können Sie den Arbeitsablauf für die erneute Verarbeitung jederzeit für einen Asset-Ordner ausführen.

Sie können optional die Stapelgröße des Arbeitsablaufs für die Neuverarbeitung von 50 Assets bis zu 1000 Assets anpassen. Wenn Sie _Scene7 ausführen: Assets_ -Workflow in einem Ordner neu verarbeiten, werden Assets in Stapeln gruppiert und zur Verarbeitung an den Server für dynamische Medien gesendet. Nach der Verarbeitung werden die Metadaten der einzelnen Assets im gesamten Stapelsatz auf AEM aktualisiert. Wenn die Stapelgröße sehr groß ist, kann es zu einer Verzögerung bei der Verarbeitung kommen. Wenn die Stapelgröße zu klein ist, kann dies zu vielen Rundfahrten zum Dynamic Media-Server führen.

Siehe [Anpassen der Stapelgröße des Neuverarbeitungsarbeitsablaufs](#adjusting-load).

>[!NOTE]
>
>Wenn Sie eine Massenmigration von Assets von Dynamic Media Classic zu AEM durchführen, müssen Sie den Migrationsreplikationsagenten auf dem Dynamic Media-Server aktivieren. Stellen Sie nach Abschluss der Migration sicher, dass Sie den Agenten deaktivieren.
Der Migrationsveröffentlichungsagent muss auf dem Server für dynamische Medien deaktiviert werden, damit der Arbeitsablauf für die Neuverarbeitung erwartungsgemäß funktioniert.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**So verarbeiten Sie Assets in einem Ordner** neu
1. Navigieren Sie in AEM auf der Seite &quot;Assets&quot;zu einem Ordner mit Assets, dem ein Verarbeitungsprofil zugewiesen ist und für den Sie **Scene7 anwenden möchten: Asset** -Arbeitsablauf neu verarbeiten,

   Ordner, denen bereits ein Verarbeitungsprofil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen in der Kartenansicht angezeigt.

1. Wählen Sie einen Ordner aus.

   * Im Workflow werden alle Dateien im ausgewählten Ordner rekursiv berücksichtigt.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie neu.
   * Es empfiehlt sich, diesen Workflow nicht in einer Ordnerhierarchie mit mehr als 1000 Assets auszuführen.

1. Near the upper-left corner of the page, from the drop-down list, click **[!UICONTROL Timeline]**.
1. Klicken Sie in der linken unteren Ecke der Seite rechts neben dem Feld Kommentar auf das Karussymbol ( **^** ) .

   ![Assets-Workflow 1 neu verarbeiten](/help/assets/assets/reprocess-assets1.png)

1. Klicken Sie auf **[!UICONTROL Arbeitsablauf starten]**.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Arbeitsablauf]** starten die Option **[!UICONTROL Scene7: Assets]** neu verarbeiten
1. (Optional) Geben Sie im Textfeld **Titel des Workflows** eingeben einen Namen für den Workflow ein. Sie können den Namen gegebenenfalls verwenden, um auf die Workflow-Instanz zu verweisen.

   ![Assets 2 neu verarbeiten](/help/assets/assets/reprocess-assets2.png)

1. Klicken Sie auf **[!UICONTROL Start]** und dann auf **[!UICONTROL Bestätigen]**.

   Klicken Sie auf der AEM-Hauptseite der Konsole auf **[!UICONTROL Tools > Workflow]**, um den Workflow zu überwachen oder dessen Fortschritt zu überprüfen. Wählen Sie auf der Seite &quot;Workflow-Instanzen&quot;einen Workflow aus. Klicken Sie in der Menüleiste auf Verlauf **[!UICONTROL öffnen]**. Sie können einen ausgewählten Workflow auch auf derselben Seite &quot;Workflow-Instanzen&quot;beenden, aussetzen oder umbenennen.

### Stapelgröße des Arbeitsablaufs anpassen {#adjusting-load}

(Optional) Die standardmäßige Stapelgröße im Arbeitsablauf für die Wiederaufbereitung beträgt 50 Assets pro Auftrag. Diese optimale Stapelgröße wird durch die durchschnittliche Asset-Größe und die Mime-Typen von Assets bestimmt, auf denen die Neuverarbeitung ausgeführt wird. Ein höherer Wert bedeutet, dass Sie viele Dateien in einem einzigen Wiederaufbereitungsauftrag haben. Dementsprechend bleibt das Verarbeitungsbanner länger auf AEM-Assets. Wenn die durchschnittliche Dateigröße kleiner als 1 MB oder kleiner ist, empfiehlt Adobe jedoch, den Wert auf mehrere Hundert zu erhöhen, jedoch nie auf mehr als 1000. Bei einer durchschnittlichen Dateigröße von Hunderten Megabytes empfiehlt Adobe, die Stapelgröße auf 10 zu verringern.

**So passen Sie optional die Stapelgröße des Neuverarbeitungsarbeitsablaufs an**

1. Tippen Sie in Experience Manager auf **[!UICONTROL Adobe Experience Manager]** , um auf die globale Navigationskonsole zuzugreifen, und tippen Sie dann auf das Symbol **[!UICONTROL Tools]** (Hammer) > **[!UICONTROL Workflow > Modelle]**.
1. Wählen Sie auf der Seite &quot;Workflow-Modelle&quot;in der Karten- oder Listenansicht **[!UICONTROL Scene7: Assets]** neu verarbeiten

   ![Seite &quot;Workflow-Modelle&quot;mit Scene7: In der Kartenansicht ausgewählter Arbeitsablauf zum Neuverarbeiten von Assets](/help/assets/assets-dm/reprocess-assets7.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**. Eine neue Registerkarte für den Browser öffnet Scene7: Assets-Workflow-Modellseite neu verarbeiten.
1. Scene7: Workflow-Seite &quot;Assets neu verarbeiten&quot;in der oberen rechten Ecke tippen Sie auf **[!UICONTROL &quot;Bearbeiten&quot;]** , um den Workflow zu entsperren.
1. Wählen Sie im Workflow die Komponente Scene7 Batch Upload aus, um die Symbolleiste zu öffnen, und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Konfigurieren]** .

   ![Komponente &quot;Scene7 Batch Upload&quot;](/help/assets/assets-dm/reprocess-assets8.png)

1. Legen Sie im Dialogfeld &quot; **[!UICONTROL Batch-Upload zu Scene7 - Schritt-Eigenschaften]** &quot;Folgendes fest:
   * Geben Sie in die Textfelder **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** einen neuen Titel und eine neue Beschreibung für den Auftrag ein, falls gewünscht.
   * Wählen Sie &quot; **[!UICONTROL Handler-Modus]** &quot;, wenn der Handler zum nächsten Schritt fortfahren soll.
   * Geben Sie im Feld **[!UICONTROL Timeout]** den externen Prozess-Timeout (Sekunden) ein.
   * Geben Sie im Feld **[!UICONTROL Zeitraum]** ein Abfrageintervall (Sekunden) ein, um zu testen, ob der externe Prozess abgeschlossen ist.
   * Geben Sie im Feld &quot; **[!UICONTROL Stapel&quot;die maximale Anzahl von Assets (50-1000) ein, die in einem Stapelverarbeitungs-Upload-Auftrag für den dynamischen Medienserver verarbeitet werden]** sollen.
   * Wählen Sie **[!UICONTROL Bei Zeitüberschreitung]** fortfahren, wenn Sie beim Erreichen des Zeitlimits fortfahren möchten. Deaktivieren Sie diese Option, wenn beim Erreichen des Timeouts mit dem Posteingang fortgefahren werden soll.
   ![Eigenschaften, Dialogfeld](/help/assets/assets-dm/reprocess-assets3.png)

1. Tippen Sie in der oberen rechten Ecke des Dialogfelds &quot; **[!UICONTROL Stapel-Upload zu Scene7 - Schritt-Eigenschaften]** &quot;auf **[!UICONTROL Fertig]**.

1. Oben rechts in Scene7: Seite zum Assets-Workflow-Modell neu verarbeiten, tippen Sie auf **[!UICONTROL Synchronisieren]**. Wenn das Workflow-Laufzeitmodell **[!UICONTROL synchronisiert]** wird, wird es erfolgreich synchronisiert und kann Assets in einem Ordner neu verarbeiten.

   ![Synchronisieren des Workflow-Modells](/help/assets/assets-dm/reprocess-assets1.png)

1. Schließen Sie die Browser-Registerkarte, auf der Scene7 angezeigt wird: Workflow-Modell für Assets neu verarbeiten

<!--1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main AEM console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.-->
