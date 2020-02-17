---
title: Metadatenprofile zum Anpassen der Metadatenanforderungen für Assets
description: Informieren Sie sich über Metadatenprofile für Assets. Erfahren Sie, wie Sie Metadatenprofile erstellen und auf Ordner-Assets anwenden können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9658fbf8c918b9051a35e7477afa01af7722a662

---


# Metadatenprofile {#metadata-profiles}

Mit einem Metadatenprofil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadatenprofil und wenden Sie es auf einen Ordner an. Alle Assets, die Sie anschließend in den Ordner hochladen, übernehmen die Standardmetadaten, die Sie im Metadatenprofil konfiguriert haben.

## Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Navigieren Sie zu **[!UICONTROL Werkzeuge > Assets > Metadatenprofile]** und tippen Sie auf **[!UICONTROL Erstellen]**.
1. Enter a title for the Metadata Profile, for example Sample Metadata, and tap **[!UICONTROL Create]**. The [!UICONTROL Edit Form] for the metadata profile is displayed.

   ![chlimage_1-197](assets/chlimage_1-480.png)

1. Click a component and configure its properties in the **[!UICONTROL Settings]** tab. For example, click the **[!UICONTROL Description]** component and edit its properties.

   ![chlimage_1-198](assets/chlimage_1-481.png)

   Edit the following properties for the **[!UICONTROL Description]** component:

   * **[!UICONTROL Feldbeschriftung]** : Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.

   * **[!UICONTROL Zu Eigenschaft]** zuordnen: Der Wert dieser Eigenschaft stellt den relativen Pfad/Namen zu dem Asset-Knoten bereit, in dem er im Repository gespeichert wird. Der Wert sollte immer mit beginnen, `./` da er angibt, dass sich der Pfad unter der Node des Assets befindet.
   ![chlimage_1-199](assets/chlimage_1-482.png)

   The value you specify for **[!UICONTROL Map to property]** is stored as a property under the asset&#39;s metadata node. For example, if you specify . `/jcr:content/metadata/dc:desc` als Name der Eigenschaft &quot; **[!UICONTROL Zuordnung zu&quot;]**, speichert AEM Assets den Wert `dc:desc` am Metadaten-Knoten des Assets.

   * **[!UICONTROL Standardwert]** - Verwenden Sie diese Eigenschaft, um einen Standardwert für die Metadatenkomponente hinzuzufügen. For example, if you specify &quot;My description&quot; then this value is assigned to the property `dc:desc` at the asset&#39;s metadata node.
   ![chlimage_1-200](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Hinzufügen eines Standardwert zu einer neuen Metadateneigenschaft (die nicht bereits im vorhanden ist. Node `/jcr:content/metadata` ) zeigt die Eigenschaft und ihren Wert standardmäßig nicht auf der Seite Eigenschaften des Assets an. To view the new property on the assets&#39; [!UICONTROL Properties] page, modify the corresponding schema form.

1. (Optional) Add more components to the Edit Form from the **[!UICONTROL Build Form]** tab, and configure their properties in the **[!UICONTROL Settings]** tab. The following properties are available from the **[!UICONTROL Build Form]** tab:

| Komponente | Eigenschaften |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Feldbeschriftung, <br> Beschreibung |
| [!UICONTROL Einzelzeilentext] | Feldbeschriftung, <br> Zuordnung zu Eigenschaft, <br> Standardwert |
| [!UICONTROL Mehrwerttext] | Feldbeschriftung, <br> Zuordnung zu Eigenschaft, <br> Standardwert |
| [!UICONTROL Zahl] | Feldbeschriftung, <br> Zuordnung zu Eigenschaft, <br> Standardwert |
| [!UICONTROL Datum] | Feldbeschriftung, <br> Zuordnung zu Eigenschaft, <br> Standardwert |
| [!UICONTROL Standard-Tags] | Feldbeschriftung, <br> Zuordnung zu Eigenschaft, <br> Standardwert, <br> Beschreibung |

![chlimage_1-201](assets/chlimage_1-484.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird der Liste der Profile auf der Seite **[!UICONTROL Metadatenprofile]** hinzugefügt.<br>


   ![Auf der Seite &quot;Metadatenprofile&quot;hinzugefügtes Metadatenprofil](assets/MetadataProfiles-page.png)

## Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. From the **[!UICONTROL Metadata Profiles]** page, select a metadata profile to make a copy of it.

   ![chlimage_1-203](assets/chlimage_1-486.png)

1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Kopieren]** .
1. Geben Sie im Dialogfeld **[!UICONTROL Metadatenprofil kopieren]** einen Titel für die neue Kopie des Metadatenprofils ein.
1. Tippen Sie auf **[!UICONTROL Kopieren]**. Die Kopie des Metadatenprofils wird in der Liste mit Profilen auf der Seite **[!UICONTROL Metadatenprofile]** angezeigt.

   ![Eine Kopie des auf der Seite &quot;Metadatenprofile&quot;hinzugefügten Metadatenprofils](assets/copy-metadata-profile.png)

## Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

   ![chlimage_1-205](assets/chlimage_1-488.png)

1. Ta[] **[!UICONTROL Delete Metadata Profiles]** in the toolbar.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]**, um den Löschvorgang zu bestätigen. Das Metadatenprofil wird aus der Liste gelöscht.

## Apply a metadata profile to folders {#applying-a-metadata-profile-to-folders}

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Metadatenprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![chlimage_1-206](assets/chlimage_1-489.png)

Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Apply metadata profiles to specific folders {#applying-metadata-profiles-to-specific-folders}

Sie können Metadatenprofile über das Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf Ordner anwenden. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Metadatenprofile auf Ordner anwenden können.

Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Apply metadata profiles to folders from Profiles user interface {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

Gehen Sie wie folgt vor, um das Metadatenprofil anzuwenden:

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-207](assets/chlimage_1-490.png)

1. Tap **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and tap **[!UICONTROL Done]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

#### Apply metadata profiles to folders from Properties {#applying-metadata-profiles-to-folders-from-properties}

1. In the left rail, tap **[!UICONTROL Assets]** then navigate to the folder that you want to apply a metadata profile to.
1. On the folder, tap or click the check mark to select it and then tap or click **[!UICONTROL Properties]**.

1. Select the **[!UICONTROL Metadata Profiles]** tab and select the profile from the drop-down menu and tap **[!UICONTROL Save]**.

   ![chlimage_1-208](assets/chlimage_1-491.png)

   Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

### Apply a metadata profile globally {#applying-a-metadata-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in AEM-Assets in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

**Um ein Metadatenprofil global anzuwenden, führen Sie einen der folgenden Schritte aus**

* Navigieren Sie zum entsprechenden Profil, wenden Sie es an `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und klicken Sie auf **[!UICONTROL Speichern]**.

   ![chlimage_1-209](assets/chlimage_1-492.png)

* Navigate to CRXDE Lite to the following node: `/content/dam/jcr:content`. Fügen Sie die Eigenschaft hinzu `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` und tippen Sie auf Alle **speichern**.

   ![chlimage_1-210](assets/chlimage_1-493.png)

## Remove a metadata profile from folders {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

You can remove a metadata profile from a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from the **[!UICONTROL Properties]**. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Metadatenprofile aus Ordnern entfernen können.

### Remove metadata profiles from folders via Profiles user interface {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Tap **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from and tap **[!UICONTROL Done]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Remove metadata profiles from folders via Properties {#removing-metadata-profiles-from-folders-via-properties}

1. Tap the AEM logo and navigate **[!UICONTROL Assets]** and then to the folder that you want to remove an metadata profile from.
1. On the folder, tap the check mark to select it and then tap **[!UICONTROL Properties]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend **[!UICONTROL Keine]** aus dem Dropdownmenü aus und klicken Sie auf **[!UICONTROL Speichern]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

>[!MORELIKETHIS]
>
>* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md)
>* [Best Practices zum Organisieren digitaler Assets für die Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md)

