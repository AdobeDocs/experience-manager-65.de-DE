---
title: Konfiguration und Verwaltung der Metadatenfunktionalität.
description: Konfiguration und Verwaltung der Funktion [!DNL Experience Manager Assets] im Zusammenhang mit dem Hinzufügen und Verwalten von Metadaten.
contentOwner: AG
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 55%

---


# Konfiguration und Verwaltung der Metadatenfunktionalität in [!DNL Assets] {#config-metadata}

<!-- Scope of metadata articles:
* metadata.md: The scope of this article is basic metadata updates, changes, etc. operations that end-users can do.
* metadata-concepts.md: All conceptual information. Minor instructions are OK but it is an FYI article about support and standards.
* metadata-config.md: New article. Contains all configuration and administration how-to info related to metadata of assets.
-->

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten. [!DNL Adobe Experience Manager Assets] ermöglicht Administratoren die Konfiguration und Anpassung der Metadatenfunktionalität, um das Standardangebot für Adoben zu ändern.

## Metadaten-Schema {#metadata-schema} bearbeiten

Weitere Informationen finden Sie unter [Metadaten-Schema-Formulare bearbeiten](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerspezifischen Namensraums innerhalb von [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

Sie können innerhalb von [!DNL Experience Manager] eigene Namensraum hinzufügen. Ebenso wie vordefinierte Namensraum wie `cq`, `jcr` und `sling` vorhanden sind, können Sie einen Namensraum für Ihre Repository-Metadaten und die XML-Verarbeitung haben.

1. Greifen Sie auf die Knotentyp-Verwaltungsseite `https://[aem_server]:[port]/crx/explorer/nodetypes/index.jsp` zu.
1. Klicken Sie auf **[!UICONTROL Namensraum]** oben auf der Seite, um auf die Seite &quot;Namensraum-Administration&quot;zuzugreifen.
1. Klicken Sie zum Hinzufügen eines Namensraums unten auf der Seite auf **[!UICONTROL Neu]**.
1. Geben Sie einen benutzerdefinierten Namensraum in der XML-Namensraum-Konvention an. Geben Sie die ID in Form eines URI und eines zugehörigen Präfix für die ID an. Klicken Sie auf **[!UICONTROL Speichern]**.

## Beschränkungen für Massenmetadaten-Update {#bulk-metadata-update-limit} konfigurieren

Um zu verhindern, dass eine DOS-ähnliche Situation (Denial of Service) vorliegt, wird die Anzahl der in einer Sling-Anforderung unterstützten Parameter begrenzt. [!DNL Enterprise Manager] Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. Enterprise Manager erzeugt die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, rufen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** auf und ändern Sie den Wert von **[!UICONTROL Maximale POST Parameter]** in **[!UICONTROL Apache Sling-Anforderungsparameter-Verarbeitung]** OSGi-Konfiguration.

## Metadatenprofile {#metadata-profiles}

Mit einem Metadaten-Profil können Sie Standardmetadaten auf Assets in einem Ordner anwenden. Erstellen Sie ein Metadaten-Profil und wenden Sie es auf einen Ordner an. Alle Assets, die Sie anschließend in den Ordner hochladen, übernehmen die Standardmetadaten, die Sie im Metadaten-Profil konfiguriert haben.

### Hinzufügen eines Metadatenprofils {#adding-a-metadata-profile}

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Profil]** und klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel für das Profil ein, z. B. `Sample Metadata`, und klicken Sie auf **[!UICONTROL Erstellen]**. Das [!UICONTROL Formular bearbeiten] für das Metadaten-Profil wird angezeigt.

   ![Metadatenformular bearbeiten](assets/metadata-edit-form.png)

1. Klicken Sie auf eine Komponente und konfigurieren Sie deren Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Klicken Sie beispielsweise auf die Komponente **[!UICONTROL Beschreibung]** und bearbeiten Sie die zugehörigen Eigenschaften.

   ![Festlegen einer Komponente im Metadaten-Profil](assets/metadata-profile-component-setting.png)

   Bearbeiten Sie die folgenden Eigenschaften für die Komponente **[!UICONTROL Beschreibung]**:

   * **[!UICONTROL Feldbeschriftung]**: Der Anzeigename der Metadateneigenschaft. Dieser dient lediglich als Referenz für den Benutzer.

   * **[!UICONTROL Zu Eigenschaft]** zuordnen: Der Wert dieser Eigenschaft gibt den relativen Pfad oder Namen zu dem Asset-Knoten an, in dem sie im Repository gespeichert wird. Der Wert sollte immer mit `./` Beginn werden, da er angibt, dass sich der Pfad unter der Node des Assets befindet.

   ![Zu Eigenschaftseinstellung im Metadaten-Profil zuordnen](assets/metadata-profile-setting-map-property.png)

   Der Wert, den Sie für **[!UICONTROL Zu Eigenschaft zuordnen]** angeben, wird als Eigenschaft unter dem Metadatenknoten des Assets gespeichert. Wenn Sie beispielsweise `./jcr:content/metadata/dc:desc` als Namen von **[!UICONTROL Eigenschaft]** zuordnen angeben, speichert [!DNL Assets] den Wert `dc:desc` auf dem Metadaten-Knoten des Assets.

   * **[!UICONTROL Standardwert]**: Mit dieser Eigenschaft können Sie einen Standardwert für die Metadatenkomponente hinzufügen. Wenn Sie beispielsweise „Meine Beschreibung“ angeben, wird dieser Wert der Eigenschaft `dc:desc` im Metadatenknoten des Assets zugewiesen.

   ![Standardbeschreibung im Metadaten-Profil festlegen](assets/metadata-profile-setting-default-value.png)

   >[!NOTE]
   >
   >Wenn Sie einer neuen Metadateneigenschaft (die noch nicht im Knoten `/jcr:content/metadata` vorhanden ist) einen Standardwert hinzufügen, werden die Eigenschaft und deren Wert nicht standardmäßig auf der Eigenschaftsseite des Assets angezeigt. Um die neue Eigenschaft auf der Seite &quot;[!UICONTROL Eigenschaften]&quot;der Assets Ansicht, ändern Sie das entsprechende Schema-Formular.

1. (Optional) Fügen Sie dem Bearbeitungsformular auf der Registerkarte **[!UICONTROL Formular erstellen]** weitere Komponenten hinzu und konfigurieren Sie die zugehörigen Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Die folgenden Eigenschaften sind auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbar:

| Komponente | Eigenschaften |
| ----------------------------- | ----------------------------------------------------------------------- |
| [!UICONTROL Bereichs-Kopfzeile] | Feldbeschriftung, <br> Beschreibung |
| [!UICONTROL Einzelzeilentext] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Mehrwerttext] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Zahl] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Datum] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert |
| [!UICONTROL Standard-Tags] | Feldbeschriftung, <br> Zu Eigenschaft zuordnen, <br> Standardwert, <br> Beschreibung |

1. Klicken Sie auf **[!UICONTROL Fertig]**. Das Metadatenprofil wird der Liste der Profile auf der Seite **[!UICONTROL Metadatenprofile]** hinzugefügt.<br>

   ![Auf der Seite &quot;Metadaten-Profil&quot;hinzugefügtes Metadaten-Profil](assets/MetadataProfiles-page.png)

### Kopieren eines Metadatenprofils {#copying-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadaten-Profil]** ein Metadaten-Profil aus, um eine Kopie davon zu erstellen.

   ![Kopieren eines Metadatenprofils](assets/metadata-profile-edit-copy-option.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Kopieren]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Metadatenprofil kopieren]** einen Titel für die neue Kopie des Metadatenprofils ein.
1. Klicken Sie auf **[!UICONTROL Kopieren]**. Die Kopie des Metadatenprofils wird in der Liste mit Profilen auf der Seite **[!UICONTROL Metadatenprofile]** angezeigt.

   ![Eine Kopie des Metadaten-Profils, das auf der Seite &quot;Metadaten-Profil&quot;hinzugefügt wurde](assets/copy-metadata-profile.png)

### Löschen eines Metadatenprofils {#deleting-a-metadata-profile}

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenprofile]** das zu löschende Profil aus.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Metadaten-Profil löschen]**.
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

## Metadaten-Schema für einen Ordner {#folder-metadata-schema}

Mit [!DNL Adobe Experience Manager Assets] können Sie Metadatenschemata für Asset-Ordner erstellen, die die auf Seiten mit Ordnereigenschaften angezeigten Layouts und Metadaten definieren.

### Hinzufügen von Ordner-Metadatenschema-Formularen  {#add-a-folder-metadata-schema-form}

Verwenden Sie den Editor für Metadatenschema-Formulare, um Metadatenschemata für Ordner zu erstellen und zu bearbeiten.

1. Wechseln Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordnermetadaten-Schema]**.
1. Klicken Sie auf der Seite [!UICONTROL Ordnermetadaten-Schema Forms] auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen für das Formular ein und klicken Sie auf **[!UICONTROL Erstellen]**. Das neue Schema-Formular wird auf der Seite [!UICONTROL Schema Forms] aufgeführt.

### Bearbeiten von Ordner-Metadatenschema-Formularen   {#edit-folder-metadata-schema-forms}

Sie können neu erstellte oder bestehende Metadatenschema-Formulare bearbeiten. Hierzu zählen folgende Elemente:

* Registerkarten
* Formularelemente innerhalb von Registerkarten

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen.

1. Wählen Sie auf der Seite &quot;Schema Forms&quot;das erstellte Formular aus und wählen Sie dann in der Symbolleiste die Option **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf der Seite &quot;Ordnermetadaten-Schema-Editor&quot;auf `+`, um dem Formular eine Registerkarte hinzuzufügen. Um die Registerkarte umzubenennen, klicken Sie auf den Standardnamen und geben Sie unter **[!UICONTROL Einstellungen]** den neuen Namen ein.

   ![custom_tab](assets/custom_tab.png)

   Um weitere Registerkarten hinzuzufügen, klicken Sie auf `+`. Klicken Sie auf einer Registerkarte auf `X`, um sie zu löschen.

1. Fügen Sie in der aktiven Registerkarte eine oder mehrere Komponenten von der Registerkarte **[!UICONTROL Formular erstellen]** hinzu.

   ![adding_components](assets/adding_components.png)

   Wenn Sie mehrere Registerkarten erstellen, klicken Sie auf eine bestimmte Registerkarte, um Komponenten hinzuzufügen.

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

   Löschen Sie ggf. eine Komponente über die Registerkarte **[!UICONTROL Einstellungen]**.

   ![configure_properties](assets/configure_properties.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

#### Komponenten zum Erstellen von Formularen   {#components-to-build-forms}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Ordner-Metadatenschema-Formular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Im Folgenden finden Sie eine Liste der auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Elemente:

| Komponentenname | Beschreibung |
|---|---|
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzelzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdown-Liste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |

#### Bearbeiten von Formularelementen   {#editing-form-items}

Um die Eigenschaften von Formularelementen zu bearbeiten, klicken Sie auf die Komponente und bearbeiten Sie alle oder eine Untergruppe der folgenden Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

**[!UICONTROL Feldbezeichnung]**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**[!UICONTROL Zu Eigenschaft zuordnen]**: Diese Eigenschaft gibt den relativen Pfad des Ordnerknotens im CRX-Repository an, wo das Element gespeichert ist. Sie beginnt mit „**./**“. Dies zeigt an, dass sich der Pfad unter dem Knoten des Ordners befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Ordners als Eigenschaft `dc:title`.

* `./jcr:created`: Zeigt die Eigenschaft „JCR“ im Knoten des Ordners an. Wenn Sie diese Eigenschaften in CRXDE konfigurieren, empfiehlt Adobe, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls tritt der Fehler `Asset(s) failed to modify` auf, wenn Sie die Eigenschaften des Assets speichern.

Um zu gewährleisten, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, fügen Sie dem Eigenschaftenpfad keine Leerzeichen hinzu.

**[!UICONTROL JSON-Pfad]**: Verwenden Sie diese Eigenschaft, um den Pfad der JSON-Datei anzugeben, in der Sie Schlüssel-Wert-Paare für Optionen speichern.

**[!UICONTROL Platzhalter]**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.

**[!UICONTROL Wahlen]**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**[!UICONTROL Beschreibung]**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**[!UICONTROL Klasse]**: Objektklasse, der die Eigenschaft zugeordnet ist.

### Löschen von Ordner-Metadatenschema-Formularen   {#delete-folder-metadata-schema-forms}

Sie können Ordner-Metadatenschema-Formulare über die Seite „Ordner-Metadatenschema-Formulare“ löschen. Um ein Formular zu löschen, wählen Sie das Formular aus und klicken Sie in der Symbolleiste auf die Option &quot;Löschen&quot;.

![delete_form](assets/delete_form.png)

### Zuordnen eines Ordner-Metadatenschemas {#assign-a-folder-metadata-schema}

Sie können ein Ordner-Metadatenschema über die Seite „Ordner-Metadatenschema-Formulare“ oder bei der Ordnererstellung einem Ordner zuordnen.

Wenn Sie ein Metadaten-Schema für einen Ordner konfigurieren, wird der Pfad zum Schema-Formular in der `folderMetadataSchema`-Eigenschaft des Ordnerknotens unter `./jcr:content` gespeichert.

#### Zuweisen eines Schemas über die Seite „Ordner-Metadatenschema“   {#assign-to-a-schema-from-the-folder-metadata-schema-page}

1. Wechseln Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordnermetadaten-Schema]**.
1. Wählen Sie auf der Seite „Ordner-Metadatenschema-Formulare“ das Schemaformular aus, das Sie auf einen Ordner anwenden möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**.

1. Wählen Sie den Ordner aus, auf den das Schema angewendet werden soll, und klicken Sie dann auf **[!UICONTROL Apply]**. Wenn bereits ein Metadatenschema auf den Ordner angewendet wurde, wird eine Warnung dazu angezeigt, dass das bestehende Schema überschrieben wird. Klicken Sie auf **[!UICONTROL Überschreiben]**.
1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.

   ![Ordnereigenschaften](assets/folder_properties.png)

   Um die Ordnermetadatenfelder Ansicht, klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

   ![folder_metadata_properties](assets/folder_metadata_properties.png)

#### Zuweisen eines Schemas bei der Ordnererstellung {#assign-a-schema-when-creating-a-folder}

Sie können Ordner-Metadatenschemata auch beim Erstellen eines Ordners zuweisen. Wenn bereits mindestens ein Ordner-Metadatenschema im System vorhanden ist, wird eine zusätzliche Liste im Dialogfeld **[!UICONTROL Ordner erstellen]** angezeigt. Sie können das gewünschte Schema auswählen. Standardmäßig ist kein Schema ausgewählt.

1. Klicken Sie in der Benutzeroberfläche [!DNL Experience Manager Assets] in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Titel und einen Namen für den Ordner an.
1. Wählen Sie in der Liste „Ordner-Metadatenschema“ das gewünschte Schema aus. Klicken Sie dann auf **[!UICONTROL Erstellen]**.

   ![select_schema](assets/select_schema.png)

1. Öffnen Sie die Metadateneigenschaften für den Ordner, auf den Sie das Schema angewendet haben.
1. Um die Ordnermetadatenfelder Ansicht, klicken Sie auf die Registerkarte **[!UICONTROL Ordnermetadaten]**.

### Verwenden des Ordner-Metadatenschemas {#use-the-folder-metadata-schema}

Öffnen Sie die Eigenschaften für einen Ordner, der mit einem Ordner-Metadatenschema konfiguriert wurde. Die Registerkarte **[!UICONTROL Ordnermetadaten]** wird im Ordner [!UICONTROL Eigenschaften] angezeigt. Um das Ordner-Metadatenschema-Formular anzuzeigen, wählen Sie diese Registerkarte aus.

Geben Sie Metadatenwerte in die verschiedenen Felder ein und klicken Sie auf **[!UICONTROL Speichern]**, um die Werte zu speichern. Die angegebenen Werte werden im Ordnerknoten im CRX-Repository gespeichert.

![folder_metadata_properties-1](assets/folder_metadata_properties-1.png)

## Tipps und Einschränkungen {#best-practices-limitations}

* Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.
* Die Eigenschaftsauswahl zeigt Eigenschaften an, die in Schema-Editoren und Suchformularen verwendet werden. Der Eigenschaftenwähler wählt keine Metadateneigenschaften aus einem Asset aus.
* Möglicherweise sind bereits vorhandene Metadaten-Profil vorhanden, bevor Sie auf [!DNL Experience Manager] 6.5 aktualisieren. Wenn Sie nach der Aktualisierung ein solches Profil im Ordner [!UICONTROL Properties] auf der Registerkarte [!UICONTROL Metadaten-Profil] anwenden, werden die Metadaten-Formularfelder nicht angezeigt. Wenn Sie jedoch ein neu erstelltes Metadaten-Profil anwenden, werden die Formularfelder angezeigt, aber nicht wie erwartet verfügbar. Die Funktionen gehen nicht verloren, wenn Sie jedoch die (nicht verfügbaren) Formularfelder anzeigen möchten, bearbeiten und speichern Sie die vorhandenen Metadaten-Profil.

>[!MORELIKETHIS]
>
>* [Metadaten-Konzepte und -Verständnis](metadata-concepts.md).
>* [Bearbeiten von Metadateneigenschaften von mehreren Sammlungen](manage-collections.md#editing-collection-metadata-in-bulk).
>* [Metadaten-Import und -Export in Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html).
>* [Profile zum Verarbeiten von Metadaten, Bildern und Videos](processing-profiles.md).
>* [Best Practices zum Organisieren digitaler Assets für die Verwendung von Profilen](/help/assets/organize-assets.md) zur Verarbeitung.
>* [XMP-Writeback](/help/assets/xmp-writeback.md).

