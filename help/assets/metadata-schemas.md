---
title: 'Metadaten-Schema zum Definieren des Layouts der Metadateneigenschaften in [!DNL Adobe Experience Manager Assets]. '
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadaten-Eigenschaften. Erfahren Sie, wie Sie benutzerdefinierte Metadatenschemen erstellen und Metadatenschemen bearbeiten und auf Assets anwenden können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0496d2d541be052e1201ada2bff99a2ed6fef4f3
workflow-type: tm+mt
source-wordcount: '2670'
ht-degree: 53%

---


# Metadatenschemata {#metadata-schemas}

Organisationen verfügen über ein Metadatenmodell, das die Ermittlung, Verwendung, Interoperabilität usw. von Assets verbessert. Die Anwendung für korrekte Metadaten ist für die Aufrechterhaltung von metadatenbasierten Workflows und Prozessen ungefährlich. Um die unternehmensweite Metadatenstrategie und -standards einzuhalten, können Sie Metadaten-Schema verwenden, die DAM-Benutzern helfen, diese auszurichten. [!DNL Adobe Experience Manager] ermöglicht einfache und flexible Methoden zum Erstellen, Verwalten und Anwenden von Metadaten-Schemas.

In [!DNL Adobe Experience Manager Assets]Schemas sind spezielle Felder enthalten, in die die spezifischen Informationen eingetragen werden sollen. Es enthält außerdem Layoutinformationen, um Metadatenfelder benutzerfreundlich anzuzeigen. Zu den Metadateneigenschaften gehören Titel, Beschreibung, MIME-Typen, Tags und mehr. You can use the [!UICONTROL Metadata Schema Forms] editor to modify the existing schemas or add custom metadata schemas.

Gehen Sie wie folgt vor, um die Eigenschaftsseite für ein Asset Ansicht und zu bearbeiten:

1. Klicken Sie in den Schnellaktionen auf der Asset-Kachel in der Ansicht auf die Option &quot; **[!UICONTROL Ansicht-Eigenschaften]** &quot;.

   ![Schnellaktionen für Asset-Kacheln](assets/chlimage_1-170.png)

   Alternativ können Sie ein Asset auswählen und dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]** klicken.

1. Sie können die verschiedenen Eigenschaften bearbeitbarer Metadaten unter den verfügbaren Registerkarten bearbeiten. However, you cannot modify the asset [!UICONTROL Type] in the [!UICONTROL Basic] tab of properties page.

   ![Grundlegende Registerkarte der Asset-Eigenschaften, auf der der Asset-Typ nicht geändert werden kann](assets/asset-properties-basic-tab.png)

*Abbildung: Registerkarte &quot;Einfach&quot;bei Asset-[!UICONTROL Eigenschaften].*

Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. See [Edit Metadata Schema Forms](/help/assets/metadata-schemas.md#edit-metadata-schema-forms) for more information. Wenn Sie das Metadaten-Schema eines MIME-Typs ändern, wird das Layout der Eigenschaftsseite für die Assets und alle Untertypen geändert. Durch die Bearbeitung des jpeg-Schemas unter `default/image` wird nur das Metadaten-Layout (Asset-Eigenschaften) für Assets mit dem MIME-Typ `image/jpeg` bearbeitet. Wenn Sie allerdings das „default“-Schema ändern, wird dadurch das Metadaten-Layout für alle Asset-Typen geändert.

## Metadaten-Schemaformulare {#default-metadata-schema-forms}

Um eine Liste von Formularen oder Vorlagen Ansicht, navigieren Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**.

[!DNL Experience Manager] stellt die folgenden Metadaten-Schema-Formularvorlagen bereit.

| Vorlagen |  | Beschreibung |
|---|---|---|
| [!UICONTROL default] |  | Dies ist das Basisformular für Assets. |
|  | The following child forms inherit the properties of the [!UICONTROL default] form: |  |
|  | [!UICONTROL dm_video] | Schema-Formular für Dynamic Media Videos. |
|  | [!UICONTROL image] | Schema-Formular für Bilder mit dem MIME-Typ wie `image/jpeg` und `image/png`. <br> Das [!UICONTROL Bildformular] verfügt über die folgenden Vorlagen für untergeordnete Formulare: <ul><li> [!UICONTROL jpeg]: Schema-Formular für Assets mit [!UICONTROL JPEG]-Untertyp.</li> <li>[!UICONTROL tiff]: Schema-Formular für die Assets mit dem Untertyp TIFF.</li></ul> |
|  | [!UICONTROL Anwendung] | Schema form for assets with MIME type such as `application/pdf` and `application/zip`. <br>[!UICONTROL pdf]: Schema-Formular für Assets mit dem Untertyp PDF. |
|  | [!UICONTROL Video] | Schema-Formular für Video-Assets mit MIME-Typ wie `video/avi` und `video/mp4`. |
| [!UICONTROL collection] |  | Schema-Formular für Sammlungen. |
| [!UICONTROL contentfragment] |  | [Schemaformular für Inhaltsfragmente](/help/sites-developing/customizing-content-fragments.md). |
| [!UICONTROL forms] |  | This schema form relates to [Adobe Experience Manager Forms](/help/forms/home.md). |
| [!UICONTROL ugc_contentfragment] |  | Schema-Formular für vom Benutzer erstellte Inhaltselemente und Assets, die in Experience Manager aus sozialen Medien integriert sind. |

<!-- 
TBD: video doesn't contain any sub types as listed above OOTB.
application doesn't contain the sub type zip OOTB.
-->

>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#add-a-metadata-schema-form}

Gehen Sie wie folgt vor, um ein Metadaten-Schema-Formular hinzuzufügen:

1. Um eine benutzerdefinierte Vorlage zur Liste hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Ein Sperrsymbol wird mit den nicht bearbeiteten Vorlagen angezeigt. Wenn Sie eine Vorlage anpassen, wird sie nicht gesperrt ![und geschlossen](assets/do-not-localize/lock_closed_icon.svg).

1. In the dialog, provide the title of the schema form and click **[!UICONTROL Create]** to complete the form creation process.

## Bearbeiten von Metadatenschema-Formularen {#edit-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadaten-Schema-Formular enthält Registerkarten und Formularelemente in Registerkarten. Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadaten-Schema-Formular Registerkarten oder Formularelemente hinzufügen. Die vom übergeordneten Objekt abgeleiteten Registerkarten und Formularelemente sind gesperrt. Sie können auf untergeordneter Ebene nicht geändert werden.

1. Wählen Sie auf der Seite &quot; [!UICONTROL Metadata Schema Forms] &quot;ein Formular aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]** .

1. Passen Sie auf der Seite &quot; **[!UICONTROL Metadata Schema Form Editor]** &quot;das Metadatenformular an. Ziehen Sie die erforderlichen Komponenten aus der Registerkarte &quot;Formular **[!UICONTROL erstellen]** &quot;auf eine der Registerkarten.

   ![Metadaten-Schema-Editor zum Anpassen der Seite &quot;Asset-Eigenschaften&quot;](assets/metadata-schema-editor.png)

   *Abbildung: Eine[!UICONTROL Metadaten-Schema-Formulareditorseite]mit verfügbaren Registerkarten.*

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

### Components within the [!UICONTROL Build Form] tab {#components-within-the-build-form-tab}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Schemaformular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Die folgende Tabelle enthält die auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Formularelemente:

| Komponentenname | Beschreibung |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzelzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdown-Liste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Smart-Tags] | Fügen Sie automatisch Metadaten-Tags hinzu, um Suchfunktionen zu ergänzen. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |
| [!UICONTROL Asset referenziert von] | Fügen Sie diese Komponente hinzu, um eine Liste der vom Asset referenzierten Assets anzuzeigen. |
| [!UICONTROL Asset-Verweise] | Fügen Sie dies hinzu, um eine Liste der Assets anzuzeigen, die das Asset referenzieren. |
| [!UICONTROL Produktverweise] | Fügen Sie dies hinzu, um die Liste der mit dem Asset verknüpften Produkte anzuzeigen. |
| [!UICONTROL Asset-Bewertung] | Fügen Sie dies hinzu, um Optionen zur Bewertung des Assets anzuzeigen. |
| [!UICONTROL Kontextuelle Metadaten] | Fügen Sie diese Komponente hinzu, um weitere Metadaten auf der Seite „Eigenschaften“ von Assets anzuzeigen. |

#### Bearbeiten von Metadatenkomponenten {#edit-the-metadata-component}

To edit the properties of a metadata component on the form, click the component to edit all or a subset of the following properties in the **[!UICONTROL Settings]** tab.

**Feldbezeichnung**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**Zu Eigenschaft** zuordnen: Diese Eigenschaft gibt den relativen Pfad oder den Namen des Asset-Knotens an, in dem er im CRX-Repository gespeichert wird. It starts with `./` to indicate that the path is under the asset&#39;s node.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Assets als die Eigenschaft `dc:title`.

* `./jcr:created`: Speichert das Erstellungsdatum und die Erstellungsuhrzeit eines Assets. Dies ist eine geschützte Eigenschaft. Wenn Sie diese Eigenschaften konfigurieren, empfiehlt Adobe, dass Sie sie mit Bearbeitung deaktivieren markieren.

Um sicherzustellen, dass die Komponente im Metadaten-Schemaformular korrekt angezeigt wird, sollte der Eigenschaftenpfad keine Leerzeichen enthalten.

* **Platzhalter**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.
* **Erforderlich**: Mit dieser Eigenschaft können Sie eine Metadateneigenschaft auf der Eigenschaftenseite als obligatorisch markieren.
* **Bearbeiten** deaktivieren: Verwenden Sie diese Eigenschaft, um Änderungen an einer Eigenschaft auf der Eigenschaftsseite zu deaktivieren.
* **Leeres Feld schreibgeschützt anzeigen**: Markieren Sie diese Eigenschaft, um eine Metadateneigenschaft auch dann auf der Eigenschaftenseite anzuzeigen, wenn sie keinen Wert aufweist. Standardmäßig werden Metadateneigenschaften ohne Werte nicht auf der Eigenschaftenseite aufgeführt.
* **Liste geordnet anzeigen**: Mit dieser Eigenschaft zeigen Sie eine geordnete Liste von Optionen an..
* **Wahlen**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.
* **Beschreibung**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.
* **Klasse**: Objektklasse, der die Eigenschaft zugeordnet ist.
* **Löschen**: Klicken Sie auf [!UICONTROL Löschen] , um eine Komponente aus dem Schema-Formular zu löschen.

>[!NOTE]
>
>The [!UICONTROL Hidden Field] component does not include these attributes. Sie enthält stattdessen Eigenschaften wie die Attribute „Name“, „Wert“, „Feldbezeichnung“ und „Beschreibung“. Die Werte für die Komponente „Ausgeblendetes Feld“ werden beim Speichern des Assets als POST-Parameter gesendet. Sie werden nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bedienfeld **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadatenvalidierung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. Die Suchergebnisse zeigen Assets an, denen erforderliche Metadaten fehlen, die Sie über das Schemaformular konfiguriert haben.

![Ungültige Option im Bereich &quot;Metadaten-Validierung - Vorhersage für Filter&quot;ausgewählt ](assets/chlimage_1-178.png)

Wenn Sie die Komponente „Kontextuelle Metadaten“ in eine beliebige Registerkarte eines Schemaformulars einfügen, wird sie in der Eigenschaftenseite der Assets als Liste angezeigt, auf die das bestimmte      Schema angewendet wird. Die Liste enthält alle anderen Registerkarten außer der Registerkarte, auf die Sie die Komponente „Kontextuelle Metadaten“ angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

![Komponentenliste für kontextbezogene Metadaten, Registerkarten mit Asset-Eigenschaften](assets/chlimage_1-179.png)

Um neben der Registerkarte, auf die die Komponente &quot;Kontextuelle Metadaten&quot;angewendet wird, eine beliebige Registerkarte auf der Seite &quot;Eigenschaften&quot;anzuzeigen, wählen Sie die Registerkarte in der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

![Die in der Liste &quot;Kontextuelle Metadaten&quot;ausgewählte Registerkarte wird auf der Seite &quot;Asset-Eigenschaften&quot;angezeigt](assets/contextual-metadata-asset-properties.png)

*Abbildung: Kontextbezogene Metadaten auf der Seite mit den Asset-Eigenschaften.*

### Festlegen von Eigenschaften in einer JSON-Datei {#specify-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Geben Sie den Pfad der JSON-Datei im Feld **[!UICONTROL JSON-Pfad]** an.

#### Hinzufügen oder Löschen von Registerkarten im Schemaformular {#adding-deleting-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. The default schema form includes the **[!UICONTROL Basic]**, **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]**, and **[!UICONTROL IPTC Extension]** tabs.

![Standardregisterkarten im Metadaten-Schema-Formular](assets/chlimage_1-181.png)

Click `+` to add a tab on a schema form. By default, the new tab has the name `Unnamed-1`. Sie können den Namen auf der Registerkarte **[!UICONTROL Einstellungen]** ändern.

Klicken Sie auf `X`, um eine Registerkarte zu löschen.

![Hinzufügen oder Löschen einer Registerkarte mit dem Metadaten-Schema-Editor](assets/chlimage_1-182.png)

## Löschen von Metadatenschema-Formularen {#delete-metadata-schema-forms}

In [!DNL Experience Manager] können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können aber alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie ein Formular aus und klicken Sie auf &quot;Löschen&quot;.

>[!NOTE]
>
>* Nachdem Sie benutzerdefinierte Änderungen an einem Standardformular gelöscht haben, wird vor dem Formular die ![Sperre geschlossen](assets/do-not-localize/lock_closed_icon.svg) erneut angezeigt. Es zeigt an, dass das Formular wieder in den Standardstatus zurückgesetzt wird.
>* Sie können die standardmäßigen Metadaten-Schema-Formulare in [!DNL Assets]nicht löschen.


## Schemaformulare für MIME-Typen   {#schema-forms-for-mime-types}

[!DNL Experience Manager] stellt voreingestellte Standardformulare für verschiedene MIME-Typen bereit. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### Add new forms for MIME types {#add-new-forms-for-mime-types}

Erstellen Sie ein Formular unter dem entsprechenden Formulartypen. For example, to add a template for the `image/png` subtype, create the form under the &quot;image&quot; forms. Der Titel für das Schemaformular ist der Name des Untertyps. In this case, the title is `png`.

#### Use an existing schema template for various MIME types {#use-an-existing-schema-template-for-various-mime-types}

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. Nutzen Sie beispielsweise das Formular `image/jpeg` für Assets mit dem MIME-Typ `image/png`.

In this case, create a node at `/etc/dam/metadataeditor/mimetypemappings` in the CRX repository. Geben Sie einen Namen für den Knoten an und definieren Sie die folgenden Eigenschaften:

| Name | Beschreibung | Typ | Wert |
|------|-------------|------|-------|
| `exposedmimetype` | Name des vorhandenen Formulars, das zugeordnet werden soll | `String` | `image/jpeg` |
| `mimetypes` | Liste der MIME-Typen, die das im Attribut `exposedmimetype` definierte Formular verwenden | `String` | `image/png` |

[!DNL Assets] ordnet die folgenden MIME-Typen und Schemaformulare zu:

| Schemaformular | MIME-Typen |
| --------------------------- | --------------------------------------------------- |
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Zugriff auf Metadatenschemata gewähren {#grant-access-to-metadata-schemas}

Die Funktion „Metadatenschema“ ist nur für Administratoren verfügbar. Administratoren können jedoch Zugriff auf Nicht-Administratoren gewähren, indem sie einige Berechtigungen ändern. Geben Sie an, ob Benutzer, die keine Administratoren sind, Berechtigungen für den `/conf` Ordner erstellen, ändern und löschen möchten.

## Anwenden von ordnerspezifischen Metadaten {#apply-folder-specific-metadata}

[!DNL Assets]Mit können Sie Varianten eines Metadatenschemas definieren und auf einen bestimmten Ordner anwenden.

Zum Beispiel können Sie eine Variante des Standard-Metadatenschemas definieren und diese auf einen Ordner anwenden. Das ursprüngliche Standard-Metadatenschema wird dabei überschrieben.

Nur Assets, die in den Ordner hochgeladen wurden, auf den dieses Schema angewendet wird, entsprechen den geänderten Metadaten, die im Schema für Variantenmetadaten definiert wurden. [!DNL Assets] in anderen Ordnern, für die das ursprüngliche Schema gilt, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Metadatenübernahme durch Assets richtet sich nach dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Assets in Ordnern, die keine Unterordner enthalten, übernehmen die Metadaten aus dem Schema, das auf ihren Ordner angewendet wird.

Sie können ein anderes Schema auf den Unterordner anwenden. Die Assets in einem Unterordner übernehmen das Metadaten-Schema des unmittelbaren Unterordners. Wenn kein Schema oder dasselbe Schema auf Unterordnerebene angewendet wird, übernehmen die Assets Schema vom übergeordneten Ordner.

1. Navigieren Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Select the check box before a form, for example the default metadata form, and click the **[!UICONTROL Copy]** and save it as a custom form. Geben Sie einen benutzerdefinierten Namen für das Formular an, beispielsweise `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

1. In the **[!UICONTROL Metadata Schema Forms]** page, select the `my_default` form, and then click **[!UICONTROL Edit]**.

1. Fügen Sie auf der Seite **[!UICONTROL Metadatenschema-Editor]** ein Textfeld in das Schemaformular ein. For example, add a field with the label **[!UICONTROL Category]**.

   ![Textfeld zum Metadaten-Schema-Formulareditor hinzugefügt](assets/text-field-metadata-schema-editor.png)

   *Abbildung: Textfeld zum Metadaten-Schema-Formulareditor hinzugefügt.*

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Click **[!UICONTROL Apply to Folder(s)]** from the toolbar to apply the custom metadata to a folder.

1. Select the folder on which to apply the modified schema and then click **[!UICONTROL Apply]**.

   ![Ordner zum Anwenden des Metadaten-Schemas auswählen](assets/chlimage_1-188.png)

1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Klicken Sie auf **Überschreiben**.
1. Klicken Sie auf **OK**, um die Erfolgsmeldung zu schließen.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren obligatorischer Metadaten {#define-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in den Assets in der Ansicht eine visuelle Anzeige für fehlende Metadaten angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In the card view, [!DNL Experience Manager] does not display the warning message about missing metadata for such mandatory metadata fields.

1. Navigieren Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie sie beispielsweise unter dem Namen `my_default`.

1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu und definieren Sie es als Pflichtfeld.

   ![Hinzufügen eines erforderlichen Felds in das Metadatenformular, indem Sie im Metadaten-Schema-Formulareditor auf der Registerkarte &quot;Regeln&quot;die Option &quot;Erforderlich&quot;auswählen](assets/mandatory-field-metadata-schema-editor.png)

   *Abbildung: Obligatorisches Feld im Metadaten-Schema-Formulareditor.*

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Select the form and then click **[!UICONTROL Apply to Folder(s)]** from the toolbar to apply the custom metadata to a folder.

1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. Auf der Ansicht des Assets wird eine Meldung zu den fehlenden Metadaten für das Pflichtfeld angezeigt.

   ![Meldung für fehlende erforderliche Metadaten bei der Ansicht der Asset-Karte beim Hochladen von Assets in den Ordner](assets/chlimage_1-192.png)

1. (Optional) Rufen Sie `https://[aem_server]:[port]/system/console/components/` auf. Konfigurieren und aktivieren Sie die Komponente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob`, die standardmäßig deaktiviert ist. Set a frequency at which [!DNL Experience Manager] checks for the validity of metadata on the assets. Diese Konfiguration fügt eine Eigenschaft `hasValidMetadata` zu `jcr:content` in Assets hinzu. [!DNL Experience Manager] verwendet diese Eigenschaft, um die ungültigen Assets in einem Suchergebnis zu filtern. Wenn Sie ein Asset nach einer Prüfung hinzufügen, wird das Asset erst nach der nächsten geplanten Prüfung markiert `hasValidMetadata` . Daher werden die Assets erst nach der nächsten geplanten Prüfung in den Filtern für ungültige Metadaten angezeigt.

   >[!CAUTION]
   >
   >Die Prüfungen zur Metadatenüberprüfung sind ressourcenintensiv und können sich auf die Leistung Ihres Systems auswirken. Planen Sie die Überprüfungen entsprechend. Wenn der Server die Last nicht bewältigen kann, versuchen Sie, diesen Auftrag zu deaktivieren.

<!-- TBD: Add this method to find invalid metadata in the metadata.md article later when it is published as a top-level metadata article.
-->
