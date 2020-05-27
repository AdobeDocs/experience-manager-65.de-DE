---
title: Metadaten-Profil zum Anpassen der Metadatenanforderungen für Assets
description: Informieren Sie sich über Metadatenprofile für Assets. Erfahren Sie, wie Sie Metadatenprofile erstellen und auf Ordner-Assets anwenden können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 58%

---


# Metadatenprofile {#metadata-profiles}

Mit einem Metadaten-Profil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadaten-Profil und wenden Sie es auf einen Ordner an. Alle Assets, die Sie anschließend in den Ordner hochladen, übernehmen die Standardmetadaten, die Sie im Metadaten-Profil konfiguriert haben.

## Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Navigieren Sie zu **[!UICONTROL Extras > Assets > Metadaten-Profil]** und klicken Sie auf **[!UICONTROL Erstellen]**.
1. Enter a title for the Metadata Profile, for example Sample Metadata, and click **[!UICONTROL Create]**. The [!UICONTROL Edit Form] for the metadata profile is displayed.

   ![chlimage_1-197](assets/chlimage_1-480.png)

1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.

   ![chlimage_1-198](assets/chlimage_1-481.png)

   Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbeschriftung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.

   * **[!UICONTROL Zu Eigenschaft]** zuordnen: Der Wert dieser Eigenschaft stellt den relativen Pfad/Namen zu dem Asset-Knoten bereit, in dem er im Repository gespeichert wird. Der Wert sollte immer mit dem Beginn übereinstimmen, `./` da er angibt, dass sich der Pfad unter der Node des Assets befindet.
   ![chlimage_1-199](assets/chlimage_1-482.png)

   Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Beispiel: Wenn Sie `/jcr:content/metadata/dc:desc` als Name der Eigenschaft &quot; **[!UICONTROL Zuordnung zu&quot;]**, speichert Assets den Wert `dc:desc` auf dem Metadaten-Knoten des Assets.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.
   ![chlimage_1-200](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Wenn Sie einer neuen Metadateneigenschaft (die noch nicht im Knoten `/jcr:content/metadata` vorhanden ist) einen Standardwert hinzufügen, werden die Eigenschaft und deren Wert nicht standardmäßig auf der Eigenschaftsseite des Assets angezeigt. To view the new property on the assets&#39; [!UICONTROL Properties] page, modify the corresponding schema form.

1. (Optional) Fügen Sie dem Bearbeitungsformular auf der Registerkarte **[!UICONTROL Formular erstellen]** weitere Komponenten hinzu und konfigurieren Sie die zugehörigen Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Die folgenden Eigenschaften sind auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbar:

| Komponente | Eigenschaften |
| ----------------------------- | ----------------------------------------------------------------------- |
| [!UICONTROL Bereichs-Kopfzeile] | Field Label, <br> Description |
| [!UICONTROL Einzelzeilentext] | Field Label, <br> Map to property, <br> Default Value |
| [!UICONTROL Mehrwerttext] | Field Label, <br> Map to property, <br> Default Value |
| [!UICONTROL Zahl] | Field Label, <br> Map to property, <br> Default Value |
| [!UICONTROL Datum] | Field Label, <br> Map to property, <br> Default Value |
| [!UICONTROL Standard-Tags] | Field Label, <br> Map to property, <br> Default Value, <br> Description |

![chlimage_1-201](assets/chlimage_1-484.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird der Liste der Profile auf der Seite **[!UICONTROL Metadatenprofile]** hinzugefügt.<br>

   ![Auf der Seite &quot;Metadaten-Profil&quot;hinzugefügtes Metadaten-Profil](assets/MetadataProfiles-page.png)

## Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a metadata profile to make a copy of it.

   ![chlimage_1-203](assets/chlimage_1-486.png)

1. Click **[!UICONTROL Copy]** from the toolbar.
1. Geben Sie im Dialogfeld **[!UICONTROL Metadatenprofil kopieren]** einen Titel für die neue Kopie des Metadatenprofils ein.
1. Klicken Sie auf **[!UICONTROL Kopieren]**. Die Kopie des Metadatenprofils wird in der Liste mit Profilen auf der Seite **[!UICONTROL Metadatenprofile]** angezeigt.

   ![Eine Kopie des Metadaten-Profils, das auf der Seite &quot;Metadaten-Profil&quot;hinzugefügt wurde](assets/copy-metadata-profile.png)

## Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

   ![chlimage_1-205](assets/chlimage_1-488.png)

1. Ta[] **[!UICONTROL Delete Metadata Profiles]** in the toolbar.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]**, um den Löschvorgang zu bestätigen. Das Metadatenprofil wird aus der Liste gelöscht.

## Anwenden eines Metadatenprofils auf Ordner {#applying-a-metadata-profile-to-folders}

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Metadatenprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-206](assets/chlimage_1-489.png)

Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden von Metadatenprofilen auf bestimmte Ordner {#applying-metadata-profiles-to-specific-folders}

Sie können ein Metadatenprofil über das Menü **[!UICONTROL Werkzeuge]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Anwenden von Metadatenprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

Gehen Sie wie folgt vor, um Metadaten-Profil anzuwenden:

1. Click the Experience Manager logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-207](assets/chlimage_1-490.png)

1. Click **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and click **[!UICONTROL Done]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

#### Anwenden von Metadatenprofilen auf Ordner aus „Eigenschaften“ {#applying-metadata-profiles-to-folders-from-properties}

1. In the left rail, click **[!UICONTROL Assets]** then navigate to the folder that you want to apply a metadata profile to.
1. On the folder, click the check mark to select it and then click **[!UICONTROL Properties]**.

1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend das Profil aus dem Dropdownmenü aus und klicken Sie auf **[!UICONTROL Speichern]**.

   ![chlimage_1-208](assets/chlimage_1-491.png)

   Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

### Globales Anwenden eines Metadatenprofils {#applying-a-metadata-profile-globally}

Sie können ein Profil nicht nur auf einen Ordner anwenden, sondern auch global anwenden, sodass für alle Inhalte, die in Experience Manager-Assets in einem beliebigen Ordner hochgeladen werden, das ausgewählte Profil angewendet wird.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

Gehen Sie wie folgt vor, um ein Metadaten-Profil global anzuwenden:

* Navigate to `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` and apply the appropriate profile and click **[!UICONTROL Save]**.

   ![chlimage_1-209](assets/chlimage_1-492.png)

* In CRXDE Lite, navigate to the following node: `/content/dam/jcr:content`. Add the property `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` and click **[!UICONTROL Save All]**.

   ![chlimage_1-210](assets/chlimage_1-493.png)

## Remove a metadata profile from folders {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können ein Metadatenprofil aus einem Ordner im Menü **[!UICONTROL Tools]** entfernen. Wenn Sie sich im Ordner befinden, ist dies über die **[!UICONTROL Eigenschaften]** möglich. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten aus Ordnern entfernen.

### Remove metadata profiles from folders via Profiles user interface {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Click the Experience Manager logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Click **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from and click **[!UICONTROL Done]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Remove metadata profiles from folders via Properties {#removing-metadata-profiles-from-folders-via-properties}

1. Click the Experience Manager logo and navigate **[!UICONTROL Assets]** and then to the folder that you want to remove an metadata profile from.
1. On the folder, click the check mark to select it and then click **[!UICONTROL Properties]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend **[!UICONTROL Keine]** aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

## Einschränkungen und Best Practices {#limitations-best-practices-tips}

* Möglicherweise gibt es bereits vorhandene Metadaten-Profile, bevor Sie auf [!DNL Experience Manager] 6.5 aktualisieren. Wenn Sie nach der Aktualisierung ein solches Profil auf der Registerkarte &quot; [!UICONTROL Eigenschaften] von Ordnern&quot;auf die Registerkarte &quot; [!UICONTROL Metadaten-Profile] &quot;anwenden, werden die Metadatenformularfelder nicht angezeigt. Wenn Sie jedoch ein neu erstelltes Metadaten-Profil anwenden, werden die Formularfelder angezeigt, aber nicht wie erwartet verfügbar. Die Funktionen gehen nicht verloren, wenn Sie jedoch die (nicht verfügbaren) Formularfelder anzeigen möchten, bearbeiten und speichern Sie die vorhandenen Metadaten-Profil.

>[!MORELIKETHIS]
>
>* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
>* [Best Practices zum Organisieren digitaler Assets für die Verwendung von Profilen zur Verarbeitung](/help/assets/organize-assets.md)

