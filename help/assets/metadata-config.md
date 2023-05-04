---
title: Konfiguration und Verwaltung von Metadatenfunktionen
description: Konfiguration und Verwaltung von  [!DNL Experience Manager Assets] -Funktionen im Zusammenhang mit dem Hinzufügen und Verwalten von Metadaten.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 56c92b7f-e687-4ab5-a376-afa58bdb6ee0
source-git-commit: 3d713021ac410ca2925a282c5dfca98ed4e483ee
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 93%

---

# Konfiguration und Verwaltung der Metadatenfunktionalität in [!DNL Assets] {#config-metadata}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/metadata-profiles.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

<!-- Scope of metadata articles:
* metadata.md: The scope of this article is basic metadata updates, changes, etc. operations that end-users can do.
* metadata-concepts.md: All conceptual information. Minor instructions are OK but it is an FYI article about support and standards.
* metadata-config.md: New article. Contains all configuration and administration how-to info related to metadata of assets.
-->

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten. [!DNL Adobe Experience Manager Assets] ermöglicht es Admins, die Metadatenfunktionalität zu konfigurieren und anzupassen, um das standardmäßige Adobe-Angebot zu ändern.

## Bearbeiten eines Metadatenschemas {#metadata-schema}

Weitere Informationen finden Sie unter [Bearbeiten von Metadatenschema-Formularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerdefinierten Namespace in [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in [!DNL Experience Manager] hinzufügen. Es gibt vordefinierte Namespaces wie `cq`, `jcr` und `sling`. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Zugriff auf die Knotentyp-Administrationsseite `https://[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Um auf die Seite zur Namespace-Verwaltung zuzugreifen, klicken Sie oben auf der Seite auf **[!UICONTROL Namespaces]**.
1. Um einen Namespace hinzuzufügen, klicken Sie unten auf der Seite auf **[!UICONTROL Neu]**.
1. Geben Sie einen benutzerdefinierten Namespace gemäß der XML-Namespace-Konvention an. Geben Sie die ID in Form eines URI und verknüpftes Präfix für ID an. Klicken Sie auf **[!UICONTROL Speichern]**.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#bulk-metadata-update-limit}

Um DoS (Denial of Service)-ähnliche Situationen zu vermeiden, beschränkt [!DNL Enterprise Manager] die Anzahl der Parameter, die in einer Sling-Anforderung unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise das Limit, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. Enterprise Manager generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um das Limit zu ändern, gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** und ändern Sie den Wert der **[!UICONTROL Max. POST-Parameter]** in der OSGi-Konfiguration für das **[!UICONTROL Parameter-Handling von Apache Sling-Anfragen]**.

## Metadatenprofile {#metadata-profiles}

Mit einem Metadatenprofil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadatenprofil und wenden Sie es auf einen Ordner an. Jedes Asset, das Sie später in den Ordner hochladen, erbt die standardmäßigen Metadaten, die Sie in „Metadatenprofil“ konfiguriert haben.

### Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]** und klicken Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel für das Profil ein, z. B. `Sample Metadata`, und klicken Sie auf **[!UICONTROL Erstellen]**. Es wird [!UICONTROL Formular bearbeiten] für das Metadatenprofil angezeigt.

   ![Bearbeiten eines Metadaten-Formulars](assets/metadata-edit-form.png)

1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.

   ![Festlegen einer Komponente im Metadatenprofil](assets/metadata-profile-component-setting.png)

   Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbezeichnung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.

   * **[!UICONTROL Zu Eigenschaft zuordnen]**: Der Wert dieser Eigenschaft liefert den relativen Pfad oder Namen zum Asset-Knoten für dessen Speicherort im Repository. Der Wert sollte immer mit `./` beginnen, weil dies anzeigt, dass sich der Pfad unter dem Knoten des Assets befindet.

   ![Einstellung von „Zu Eigenschaft zuordnen“ im Metadatenprofil](assets/metadata-profile-setting-map-property.png)

   Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Wenn sie z. B. `./jcr:content/metadata/dc:desc` als Namen von **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, speichert [!DNL Assets] den Wert `dc:desc` im Metadatenknoten des Assets. Es wird empfohlen, einer bestimmten Eigenschaft im Metadatenschema nur ein Feld zuzuordnen. Andernfalls wird das der Eigenschaft zuletzt zugeordnete Feld vom System ausgewählt.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.

   ![Festlegen einer Standardbeschreibung im Metadatenprofil](assets/metadata-profile-setting-default-value.png)

   >[!NOTE]
   >
   >Wenn Sie einer neuen Metadateneigenschaft (die noch nicht im Knoten `/jcr:content/metadata` vorhanden ist) einen Standardwert hinzufügen, werden die Eigenschaft und deren Wert nicht standardmäßig auf der Seite [!UICONTROL Eigenschaften] des Assets angezeigt. Um die neue Eigenschaft auf der Seite [!UICONTROL Eigenschaften] des Assets anzuzeigen, müssen Sie das entsprechende Schemaformular ändern.

1. (Optional) Fügen Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** weitere Komponenten zu [!UICONTROL Formular bearbeiten] hinzu, und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Folgende Eigenschaften sind auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbar:

| Komponente | Eigenschaften |
| ----------------------------- | ----------------------------------------------------------------------- |
| [!UICONTROL Bereichs-Kopfzeile] | Feldbezeichnung, <br>-Beschreibung |
| [!UICONTROL Einzeiliger Text] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Mehrfachwerttext] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Zahl] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Datum] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Standard-Tags] | Feldbezeichnung, <br> Zu Eigenschaft zuordnen, <br> Standardwert, <br> Beschreibung |

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird der Liste der Profile auf der Seite **[!UICONTROL Metadatenprofile]** hinzugefügt.<br>

   ![Auf der Seite „Metadatenprofile“ hinzugefügtes Metadatenprofil](assets/MetadataProfiles-page.png)

### Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** ein Metadatenprofil aus, um eine Kopie davon zu erstellen.

   ![Kopieren eines Metadatenprofils](assets/metadata-profile-edit-copy-option.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Metadatenprofil kopieren]** einen Titel für die neue Kopie des Metadatenprofils ein.
1. Klicken **[!UICONTROL Kopieren]**. Die Kopie des Metadatenprofils wird in der Liste mit Profilen auf der Seite **[!UICONTROL Metadatenprofile]** angezeigt.

   ![Eine Kopie des auf der Seite „Metadatenprofile“ hinzugefügten Metadatenprofils](assets/copy-metadata-profile.png)

### Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Metadatenprofile löschen]**.
1. Klicken Sie im Dialogfeld auf **[!UICONTROL Löschen]**, um den Löschvorgang zu bestätigen. Das Metadatenprofil wird aus der Liste gelöscht.

<!-- TBD: Revisit to find out the correct config. and update these steps. When fixed, also o
These steps have been carried forward from old AEM versions. See https://helpx.adobe.com/experience-manager/6-2/assets/using/metadata-profiles.html#ApplyingaMetadataProfiletoFolders

### Configuration to apply a metadata profile globally {#apply-a-metadata-profile-globally}

In addition to applying a profile to a folder, you can also apply one globally so that any content uploaded into [!DNL Experience Manager] assets in any folder has the selected profile applied.

You can reprocess assets in a folder that already has an existing metadata profile that you later changed. See [Reprocessing assets in a folder after you have edited its processing profile](processing-profiles.md#reprocessing-assets).

To apply a metadata profile globally, follow these steps:

* Navigate to `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` and apply the appropriate profile and click **[!UICONTROL Save]**.

  ![Apply metadata profile to a folder globally](assets/metadata-profile-folder-setting.png)

* In CRXDE Lite, navigate to the following node: `/content/dam/jcr:content`. Add the property `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` and click **[!UICONTROL Save All]**.

  ![See applied metadata profile to a folder in the JCR in CRXDE](assets/metadata-profile-folder-setting2.png)
-->

## Metadatenschema für einen Ordner {#folder-metadata-schema}

Mit [!DNL Adobe Experience Manager Assets] können Sie Metadatenschemata für Asset-Ordner erstellen, die die auf Seiten mit Ordnereigenschaften angezeigten Layouts und Metadaten definieren.

### Hinzufügen von Ordner-Metadatenschema-Formularen {#add-a-folder-metadata-schema-form}

Verwenden Sie den Editor für Metadatenschema-Formulare, um Metadatenschemata für Ordner zu erstellen und zu bearbeiten.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Klicken Sie auf der Seite [!UICONTROL Ordner-Metadaten-Schemaformulare] auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen für das Formular an und klicken Sie auf **[!UICONTROL Erstellen]**. Das neue Schemaformular wird auf der Seite [!UICONTROL Schemaformulare] aufgeführt.

### Bearbeiten von Ordner-Metadatenschema-Formularen {#edit-folder-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten, das Folgendes enthält:

* Registerkarten
* Formularelemente in Registerkarten.

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen.

1. Wählen Sie auf der Seite „Schemaformulare“ das erstellte Formular aus und klicken Sie in der Symbolleiste auf die Option **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf der Seite „Ordner-Metadatenschema-Editor“ auf `+`, um eine Registerkarte zum Formular hinzuzufügen. Um die Registerkarte umzubenennen, klicken Sie auf den Standardnamen und geben Sie unter **[!UICONTROL Einstellungen]** den neuen Namen an.

   ![custom_tab](assets/custom_tab.png)

   Um weitere Registerkarten hinzuzufügen, klicken Sie auf `+`. Klicken Sie zum Löschen in einer Registerkarte auf `X`.

1. Fügen Sie in der aktiven Registerkarte eine oder mehrere Komponenten von der Registerkarte **[!UICONTROL Formular erstellen]** hinzu.

   ![adding_components](assets/adding_components.png)

   Wenn Sie mehrere Registerkarten erstellen, klicken Sie auf eine bestimmte Registerkarte, um Komponenten hinzuzufügen.

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

   Löschen Sie ggf. eine Komponente über die Registerkarte **[!UICONTROL Einstellungen]**.

   ![configure_properties](assets/configure_properties.png)

1. Um die Änderungen zu speichern, klicken Sie in der Symbolleiste auf **[!UICONTROL Speichern]**.

#### Komponenten zum Erstellen von Formularen {#components-to-build-forms}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Ordner-Metadatenschema-Formular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Im Folgenden finden Sie eine Liste der auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Elemente:

| Komponentenname | Beschreibung |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrfachwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdown-Liste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |

#### Bearbeiten von Formularelementen {#editing-form-items}

Um die Eigenschaften von Formularelementen zu bearbeiten, klicken Sie auf die Komponente und bearbeiten Sie folgende Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

**[!UICONTROL Feldbezeichnung]**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**[!UICONTROL Zu Eigenschaft zuordnen]**: Diese Eigenschaft gibt den relativen Pfad des Ordnerknotens im CRX-Repository an, wo das Element gespeichert ist. Er beginnt mit &quot;**./**&quot;, was angibt, dass sich der Pfad unter dem Knoten des Ordners befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Ordners als Eigenschaft `dc:title`.

* `./jcr:created`: Zeigt die Eigenschaft „JCR“ im Knoten des Ordners an. Wenn Sie diese Eigenschaften in CRXDE konfigurieren, empfiehlt Adobe, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls tritt der Fehler `Asset(s) failed to modify` auf, wenn Sie die Eigenschaften des Assets speichern.

Um zu gewährleisten, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, fügen Sie dem Eigenschaftenpfad keine Leerzeichen hinzu.

**[!UICONTROL JSON-Pfad]**: Verwenden Sie diese Eigenschaft, um den Pfad der JSON-Datei anzugeben, in der Sie Schlüssel-Wert-Paare für Optionen speichern.

**[!UICONTROL Platzhalter]**: Verwenden Sie diese Eigenschaft, um relevanten Platzhaltertext für die Metadateneigenschaft anzugeben.

**[!UICONTROL Wahlen]**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**[!UICONTROL Beschreibung]**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**[!UICONTROL Klasse]**: Objektklasse, mit der die Eigenschaft verknüpft ist.

### Löschen von Ordner-Metadatenschema-Formularen {#delete-folder-metadata-schema-forms}

Sie können Ordner-Metadatenschema-Formulare über die Seite „Ordner-Metadatenschema-Formulare“ löschen. Um ein Formular zu löschen, wählen Sie es aus und klicken Sie in der Symbolleiste auf die Option „Löschen“.

![delete_form](assets/delete_form.png)

### Zuweisen eines Ordner-Metadatenschemas {#assign-a-folder-metadata-schema}

Sie können ein Ordner-Metadatenschema über die Seite „Ordner-Metadatenschema-Formulare“ oder bei der Ordnererstellung einem Ordner zuordnen.

Wenn Sie ein Metadatenschema für einen Ordner konfigurieren, wird der Pfad in der Eigenschaft `folderMetadataSchema` des Ordnerknotens unter `./jcr:content` gespeichert.

#### Zuweisen eines Schemas über die Seite „Ordner-Metadatenschema“ {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Wählen Sie auf der Seite „Ordner-Metadatenschema-Formulare“ das Schemaformular aus, das Sie auf einen Ordner anwenden möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**.

1. Wählen Sie den Ordner aus, auf den Sie das Schema anwenden möchten, und klicken Sie auf **[!UICONTROL Anwenden]**. Wenn bereits ein Metadatenschema auf den Ordner angewendet wurde, wird eine Warnung dazu angezeigt, dass das bestehende Schema überschrieben wird. Klicken Sie auf **[!UICONTROL Überschreiben]**.
1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.

   ![Ordnereigenschaften](assets/folder_properties.png)

   Um die Felder der Ordnermetadaten anzuzeigen, klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

#### Zuweisen eines Schemas bei der Ordnererstellung {#assign-a-schema-when-creating-a-folder}

Sie können beim Erstellen eines Ordners ein Ordner-Metadatenschema zuweisen. Wenn mindestens ein Ordner-Metadatenschema im System vorhanden ist, wird eine zusätzliche Liste im **[!UICONTROL Ordner erstellen]** angezeigt. Sie können das gewünschte Schema auswählen. Standardmäßig ist kein Schema ausgewählt.

1. Klicken Sie in der Symbolleiste der [!DNL Experience Manager Assets]-Benutzeroberfläche auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel und einen Namen für den Ordner an.
1. Wählen Sie in der Liste Ordner-Metadatenschema das gewünschte Schema aus. Klicken Sie dann auf **[!UICONTROL Erstellen]**.

   ![select_schema](assets/select_schema.png)

1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.
1. Um die Felder der Ordnermetadaten anzuzeigen, klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

### Verwenden des Ordner-Metadatenschemas {#use-the-folder-metadata-schema}

Öffnen Sie die Eigenschaften für einen Ordner, der mit einem Ordner-Metadatenschema konfiguriert wurde. Hierdurch wird die Registerkarte **[!UICONTROL Ordnermetadaten]** auf der Seite mit den [!UICONTROL Eigenschaften] des Ordners angezeigt. Um das Ordner-Metadatenschema-Formular anzuzeigen, wählen Sie diese Registerkarte aus.

Geben Sie Metadatenwerte in die verschiedenen Felder ein und klicken Sie auf **[!UICONTROL Speichern]**, um die Werte zu speichern. Die angegebenen Werte werden im Ordnerknoten im CRX-Repository gespeichert.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

## Tipps und Einschränkungen {#best-practices-limitations}

* Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.
* Die Eigenschaftenauswahl zeigt Eigenschaften an, die in Schema-Editoren und Suchformularen verwendet werden. Die Eigenschaftenauswahl wählt keine Metadateneigenschaften aus einem Asset aus.
* Möglicherweise sind bereits vorhandene Metadatenprofile vorhanden, bevor Sie ein Upgrade auf [!DNL Experience Manager] 6.5 durchführen. Wenn Sie nach dem Upgrade ein solches Profil in den Ordner-[!UICONTROL Eigenschaften] in der Registerkarte [!UICONTROL Metadatenprofile] anwenden, werden die Metadatenformularfelder nicht angezeigt. Wenn Sie jedoch ein neu erstelltes Metadatenprofil anwenden, werden die Formularfelder angezeigt, sind aber wie erwartet nicht verfügbar. Es gibt keinen Funktionsverlust. Wenn Sie jedoch die (nicht verfügbaren) Formularfelder anzeigen möchten, bearbeiten und speichern Sie die vorhandenen Metadatenprofile.

>[!MORELIKETHIS]
>
>* [Metadatenkonzepte und Grundlegendes](metadata-concepts.md).
>* [Bearbeiten von Metadateneigenschaften mehrerer Sammlungen](manage-collections.md#editing-collection-metadata-in-bulk).
>* [Import und Export von Metadaten in Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/metadata-import-export.html?lang=de).
>* [Profile zur Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md).
>* [Best Practices zum Organisieren digitaler Assets für die Verwendung in der Verarbeitung von Profilen](/help/assets/organize-assets.md).
>* [XMP-Writeback](/help/assets/xmp-writeback.md).

