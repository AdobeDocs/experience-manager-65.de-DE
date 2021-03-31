---
title: 'Metadaten-Schema zum Definieren des Layouts der Metadateneigenschaften-Seite in [!DNL Adobe Experience Manager Assets]. '
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadaten-Eigenschaften. Erfahren Sie, wie Sie benutzerdefinierte Metadatenschemen erstellen und Metadatenschemen bearbeiten und auf Assets anwenden können.
contentOwner: AG
role: Geschäftspraktiker, Administrator
feature: 'Metadaten  '
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '3605'
ht-degree: 61%

---


# Metadatenschemata {#metadata-schemas}

Organisationen verfügen über ein Metadatenmodell, das die Ermittlung, Verwendung, Interoperabilität usw. von Assets verbessert. Die Anwendung für korrekte Metadaten ist für die Aufrechterhaltung von metadatenbasierten Workflows und Prozessen ungefährlich. Um die unternehmensweite Metadatenstrategie und -standards einzuhalten, können Sie Metadaten-Schema verwenden, die DAM-Benutzern helfen, diese auszurichten. [!DNL Adobe Experience Manager] ermöglicht einfache und flexible Methoden zum Erstellen, Verwalten und Anwenden von Metadaten-Schemas.

In [!DNL Adobe Experience Manager Assets] enthalten Schemas spezielle Felder, um bestimmte Informationen auszufüllen. Es enthält außerdem Layoutinformationen, um Metadatenfelder benutzerfreundlich anzuzeigen. Zu den Metadateneigenschaften gehören Titel, Beschreibung, MIME-Typen, Tags und mehr. Sie können den Editor [!UICONTROL Metadaten-Schema Forms] verwenden, um die vorhandenen Schema zu ändern oder benutzerspezifische Metadaten-Schema hinzuzufügen.

Gehen Sie wie folgt vor, um die Eigenschaftsseite für ein Asset Ansicht und zu bearbeiten:

1. Klicken Sie auf die Option **[!UICONTROL Eigenschaften von Ansichten]** aus den Schnellaktionen auf der Elementkachel in der Ansicht der Karte. Alternativ können Sie ein Asset auswählen und dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]** ![Eigenschaften der Ansicht](assets/do-not-localize/info-circle-icon.png) klicken.

1. Sie können die verschiedenen Eigenschaften bearbeitbarer Metadaten unter den verfügbaren Registerkarten bearbeiten. Das Asset [!UICONTROL Typ] kann jedoch auf der Eigenschaftenseite auf der Registerkarte [!UICONTROL Einfach] nicht geändert werden.

   ![Grundlegende Registerkarte der Asset-Eigenschaften, auf der der Asset-Typ nicht geändert werden kann](assets/asset-properties-basic-tab.png)

*Abbildung: Registerkarte &quot;Einfach&quot;bei Asset- [!UICONTROL Eigenschaften].*

Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. Weitere Informationen finden Sie unter [Metadaten-Schema bearbeiten Forms](/help/assets/metadata-schemas.md#edit-metadata-schema-forms). Wenn Sie das Metadaten-Schema eines MIME-Typs ändern, wird das Layout der Eigenschaftsseite für die Assets und alle Untertypen geändert. Durch die Bearbeitung des jpeg-Schemas unter `default/image` wird nur das Metadaten-Layout (Asset-Eigenschaften) für Assets mit dem MIME-Typ `image/jpeg` bearbeitet. Wenn Sie allerdings das „default“-Schema ändern, wird dadurch das Metadaten-Layout für alle Asset-Typen geändert.

## Metadaten-Schema-Formulare {#default-metadata-schema-forms}

Um eine Liste von Formularen oder Vorlagen Ansicht, navigieren Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**.

[!DNL Experience Manager] stellt die folgenden Metadaten-Schema-Formularvorlagen bereit.

| Vorlagen |  | Beschreibung |
|---|---|---|
| [!UICONTROL default] |  | Dies ist das Basisformular für Assets. |
|  | Die folgenden untergeordneten Formulare übernehmen die Eigenschaften des Formulars [!UICONTROL default]: |  |
|  | <ul><li>[!UICONTROL dm_video]</li></ul> | Schema-Formular für Dynamic Media-Videos. |
|  | <ul><li>[!UICONTROL image]</li></ul> | Schema-Formular für Bilder mit dem MIME-Typ wie `image/jpeg` und `image/png`. <br> Das   Bildformular verfügt über die folgenden Vorlagen für untergeordnete Formulare: <ul><li> [!UICONTROL jpeg]: Schema-Formular für Assets mit  [!UICONTROL JPEG]-Untertyp.</li> <li>[!UICONTROL tiff]: Schema-Formular für die Assets mit dem Untertyp TIFF.</li></ul> |
|  | <ul><li>[!UICONTROL Anwendung]</li></ul> | Schema-Formular für Assets mit MIME-Typ wie `application/pdf` und `application/zip`. <br>[!UICONTROL pdf]: Schema-Formular für Assets mit dem Untertyp PDF. |
|  | <ul><li>[!UICONTROL Video]</li></ul> | Schema-Formular für Video-Assets mit MIME-Typ wie `video/avi` und `video/mp4`. |
| [!UICONTROL collection] |  | Schema-Formular für Sammlungen. |
| [!UICONTROL contentfragment] |  | [Schemaformular für Inhaltsfragmente](/help/sites-developing/customizing-content-fragments.md). |
| [!UICONTROL forms] |  | Dieses Schema-Formular bezieht sich auf [Adobe Experience Manager Forms](/help/forms/home.md). |
| [!UICONTROL ugc_contentfragment] |  | Schema-Formular für vom Benutzer erstellte Inhaltselemente und Assets, die in Experience Manager aus sozialen Medien integriert sind. |

>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#add-a-metadata-schema-form}

Gehen Sie wie folgt vor, um ein Metadaten-Schema-Formular hinzuzufügen:

1. Um eine benutzerdefinierte Vorlage zur Liste hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Ein Sperrsymbol wird mit den nicht bearbeiteten Vorlagen angezeigt. Wenn Sie eine Vorlage anpassen, wird sie nicht gesperrt. ![Sperren](assets/do-not-localize/lock_closed_icon.svg).

1. Geben Sie im Dialogfeld den Titel des Formulars ein und klicken Sie auf **[!UICONTROL Erstellen]**, um den Formularerstellungsprozess abzuschließen.

## Bearbeiten von Metadatenschema-Formularen {#edit-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadaten-Schema-Formular enthält Registerkarten und Formularelemente in Registerkarten. Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadaten-Schema-Formular Registerkarten oder Formularelemente hinzufügen. Die vom übergeordneten Objekt abgeleiteten Registerkarten und Formularelemente sind gesperrt. Sie können auf untergeordneter Ebene nicht geändert werden.

1. Wählen Sie auf der Seite [!UICONTROL Metadaten-Schema Forms] ein Formular aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Passen Sie auf der Seite **[!UICONTROL Metadaten-Schema-Formulareditor]** das Metadatenformular an. Ziehen Sie die erforderlichen Komponenten aus der Registerkarte **[!UICONTROL Formular erstellen]** auf eine der Registerkarten.

   ![Metadaten-Schema-Editor zum Anpassen der Seite &quot;Asset-Eigenschaften&quot;](assets/metadata-schema-editor.png)

   *Abbildung: Eine  [!UICONTROL Metadata Schema Form ] Editor-Seite mit verfügbaren Registerkarten.*

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

### Komponenten innerhalb der Registerkarte [!UICONTROL Formular erstellen] {#components-within-the-build-form-tab}

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

Um die Eigenschaften einer Metadatenkomponente im Formular zu bearbeiten, klicken Sie auf die Komponente, um alle oder eine Untergruppe der folgenden Eigenschaften in der Registerkarte **[!UICONTROL Einstellungen]** zu bearbeiten.

**Feldbezeichnung**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**Zu Eigenschaft** zuordnen: Diese Eigenschaft gibt den relativen Pfad oder den Namen des Asset-Knotens an, in dem er im CRX-Repository gespeichert wird. Es wird mit `./` Beginn, um anzugeben, dass sich der Pfad unter dem Asset-Knoten befindet.

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
* **Löschen**: Klicken Sie auf   Löschen, um eine Komponente aus dem Schema-Formular zu löschen.

>[!NOTE]
>
>Die Komponente [!UICONTROL Ausgeblendetes Feld] enthält diese Attribute nicht. Sie enthält stattdessen Eigenschaften wie die Attribute „Name“, „Wert“, „Feldbezeichnung“ und „Beschreibung“. Die Werte für die Komponente „Ausgeblendetes Feld“ werden beim Speichern des Assets als POST-Parameter gesendet. Sie werden nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bedienfeld **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadatenvalidierung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. Die Suchergebnisse zeigen Assets an, denen erforderliche Metadaten fehlen, die Sie über das Schemaformular konfiguriert haben.

![Option im Bereich &quot;Metadaten-Validierung - Vorhersage für Filter&quot;](assets/invalid-metadata-predicate.png)

Wenn Sie die Komponente „Kontextuelle Metadaten“ in eine beliebige Registerkarte eines Schemaformulars einfügen, wird sie in der Eigenschaftenseite der Assets als Liste angezeigt, auf die das bestimmte      Schema angewendet wird. Die Liste enthält alle anderen Registerkarten außer der Registerkarte, auf die Sie die Komponente „Kontextuelle Metadaten“ angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

![Registerkarten der Asset-Eigenschaften mit Kontextmetadatenkomponenten](assets/metadata-contextual-component-list.png)

Um neben der Registerkarte, auf die die Komponente &quot;Kontextuelle Metadaten&quot;angewendet wird, eine beliebige Registerkarte auf der Seite &quot;Eigenschaften&quot;anzuzeigen, wählen Sie die Registerkarte in der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

![Die auf der Liste der Kontextmetadaten ausgewählte Registerkarte wird auf der Seite mit den Asset-Eigenschaften angezeigt](assets/contextual-metadata-asset-properties.png)

*Abbildung: Kontextbezogene Metadaten auf der Seite mit den Asset-Eigenschaften.*

### Festlegen von Eigenschaften in einer JSON-Datei {#specify-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Geben Sie den Pfad der JSON-Datei im Feld **[!UICONTROL JSON-Pfad]** an.

#### Hinzufügen oder Löschen von Registerkarten im Schemaformular {#adding-deleting-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. Das Standardformular für Schemas enthält die Registerkarten **[!UICONTROL Basic]**, **[!UICONTROL Advanced]**, **[!UICONTROL IPTC]** und **[!UICONTROL IPTC Extension]**.

![Standardregisterkarten im Metadaten-Schema-Formular](assets/metadata-schema-form-tabs.png)

Klicken Sie auf `+`, um einem Schema-Formular eine Registerkarte hinzuzufügen. Standardmäßig hat die neue Registerkarte den Namen `Unnamed-1`. Sie können den Namen auf der Registerkarte **[!UICONTROL Einstellungen]** ändern. Klicken Sie auf `X`, um eine Registerkarte zu löschen.

![hinzufügen oder Löschen einer Registerkarte mit dem Metadaten-Schema-Editor](assets/metadata-schema-form-new-tab.png)

## Kaskadierende Metadaten {#cascading-metadata}

Beim Erfassen der Metadateninformationen eines Assets geben Benutzer Informationen in den verschiedenen verfügbaren Feldern an. Sie können bestimmte Metadatenfelder oder Feldwerte anzeigen, die von den in anderen Feldern ausgewählten Optionen abhängig sind. Solche bedingt angezeigten Metadaten werden als „kaskadierende Metadaten“ bezeichnet. Anders ausgedrückt können Sie eine Abhängigkeit zwischen einem bestimmten Metadatenfeld/-wert und einem oder mehreren Feldern und/oder dessen/deren Werten schaffen.

Verwenden Sie Metadatenschemata, um Regeln für die Anzeige kaskadierender Metadaten zu definieren. Beispiel: Wenn Ihr Metadatenschema ein Feld für den Assettyp enthält, können Sie einen relevanten Satz von Feldern erstellen, die basierend auf der Art des von einem Benutzer ausgewählten Assets angezeigt werden.

>[!CAUTION]
>
>Das Kaskadieren von Metadaten wird für Inhaltsfragmente nicht unterstützt.

Nachfolgend finden Sie einige Anwendungsfälle, für die Sie kaskadierende Metadaten definieren können:

* Wenn der Standort des Benutzers erforderlich ist, können Sie die Namen relevanter Städte basierend auf dem vom Benutzer angegebenen Land und Staat anzeigen.
* Laden Sie relevante Markennamen basierend auf der vom Benutzer ausgewählten Produktgruppe in einer Liste.
* Aktivieren/Deaktivieren Sie die Sichtbarkeit eines bestimmten Felds basierend auf dem in einem anderen Feld angegebenen Wert. Zeigen Sie beispielsweise unterschiedliche Lieferadressen an, wenn der Benutzer angibt, dass die Lieferung an eine andere Adresse gehen soll.
* Legen Sie ein Feld basierend auf dem in einem anderen Feld angegebenen Wert als Pflichtfeld fest.
* Ändern Sie die für ein bestimmtes Feld angezeigten Optionen basierend auf dem in einem anderen Wert angegebenen Wert.
* Legen Sie den standardmäßigen Metadatenwert in einem bestimmten Feld basierend auf dem in einem anderen Feld angegebenen Wert fest.

### Erstellen kaskadierender Metadaten in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Stellen Sie sich ein Szenario vor, bei dem Sie kaskadierende Metadaten anzeigen möchten, die auf dem ausgewählten Assettyp basieren. Beispiele

* Zeigen Sie für Videos zutreffende Felder wie Format, Codec, Dauer usw. an.
* Zeigen Sie für ein Word- oder PDF-Dokument Felder wie Seitenzahl, Autor usw. an.

Zeigen Sie unabhängig vom ausgewählten Asset-Typ die Copyright-Informationen als erforderliches Feld an.

1. Wechseln Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**.
1. Wählen Sie auf der Seite **[!UICONTROL Schema Forms]** ein Schema-Formular aus und klicken Sie dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste, um das Schema zu bearbeiten.

   ![Auswahlformular](assets/select_form.png)

1. (Optional) Erstellen Sie im Metadatenschema-Editor ein neues bedingtes Feld. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an.

   Um eine neue Registerkarte zu erstellen, klicken Sie auf `+`, um eine Registerkarte hinzuzufügen, und fügen Sie dann ein Metadatenfeld hinzu.

   ![Registerkarte hinzufügen](assets/add_tab.png)

1. Fügen Sie ein Dropdown-Feld für den Asset-Typ hinzu. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an. Fügen Sie optional eine Beschreibung hinzu.

   ![Asset-Typ-Field](assets/asset_type_field.png)

1. Schlüssel-Wert-Paare sind die von einem Formularbenutzer angegebenen Optionen. Sie können Schlüssel-Wert-Paare entweder manuell oder über eine JSON-Datei angeben.

   * Um die Werte manuell anzugeben, wählen Sie **[!UICONTROL Hinzufügen Manuell]** und klicken Sie auf **[!UICONTROL Hinzufügen Auswahl]** und geben Sie den Optionstext und den -wert an. Legen Sie z. B. die Assettypen „Video“, „PDF“, „Word“ und „Bild“ fest.

   * Um die Werte dynamisch aus einer JSON-Datei abzurufen, wählen Sie **[!UICONTROL Über JSON-Pfad hinzufügen]** aus und geben Sie den Pfad einer JSON-Datei an. [!DNL Experience Manager] ruft die Schlüssel-Wert-Paare in Echtzeit ab, wenn das Formular dem Anwender angezeigt wird.

   Es kann immer nur eine der beiden Optionen aktiv sein. Sie können keine Optionen aus einer JSON-Datei importieren und sie manuell bearbeiten.

   ![Auswahlmöglichkeiten hinzufügen](assets/add_choice.png)

   >[!NOTE]
   >
   >Wenn Sie eine JSON-Datei hinzufügen, werden die Schlüssel-Wert-Paare nicht im Metadatenschema-Editor angezeigt, sind jedoch im veröffentlichten Formular verfügbar.

   >[!NOTE]
   >
   >Wenn Sie Auswahlmöglichkeiten hinzufügen und auf das Dropdown-Feld klicken, wird die Benutzeroberfläche verzerrt und die Option zum Löschen der Auswahlmöglichkeiten funktioniert nicht mehr. Klicken Sie erst dann auf das Dropdown, wenn die Änderungen gespeichert wurden. Wenn dieses Problem auftritt, speichern Sie das Schema und öffnen Sie es erneut, um die Bearbeitung fortzusetzen.

1. (Optional) Fügen Sie die anderen erforderlichen Felder hinzu, wie z. B. Format, Codec und Dauer für Assets vom Typ „Video“.

   Fügen Sie ebenso abhängige Felder für andere Asset-Typen hinzu. Fügen Sie bei Dokumenten-Assets wie PDF- und Word-Dateien beispielsweise die Felder „Seitenanzahl“ und „Autor“ hinzu.

   ![Videoabhängigkeitsfelder](assets/video_dependent_fields.png)

1. Um eine Abhängigkeit zwischen dem Feld „Asset-Typ“ und anderen Feldern zu erstellen, wählen Sie das abhängige Feld aus und öffnen Sie die Registerkarte **[!UICONTROL Regeln]**.

   ![Abhängigkeitsfeld auswählen](assets/select_dependentfield.png)

1. Wählen Sie unter **[!UICONTROL Anforderung]** die Option **[!UICONTROL Erforderlich, basierend auf neuer Regel]** aus.
1. Klicken Sie auf **[!UICONTROL Hinzufügen Regel]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]**, um eine Abhängigkeit zu erstellen. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![Regel festlegen](assets/define_rule.png)

   >[!NOTE]
   >
   >Sie können mit Regeln Dropdown-Listen mit manuell vordefinierten Werten verwenden. Dropdownmenüs mit konfiguriertem JSON-Pfad können nicht in Verbindung mit Regeln verwendet werden, die vordefinierte Werte zur Anwendung von Bedingungen verwenden. Wenn die Werte zur Laufzeit aus einer JSON-Datei geladen werden, ist es nicht möglich, vordefinierte Regeln anzuwenden.

1. Wählen Sie unter **[!UICONTROL Sichtbarkeit]** die Option **[!UICONTROL Sichtbar, basierend auf neuer Regel]** aus.

1. Klicken Sie auf **[!UICONTROL Hinzufügen Regel]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]**, um eine Abhängigkeit zu erstellen. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![Sichtbarkeitsregel festlegen](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Durch Klicken auf einen Leerraum (oder eine andere Stelle als die Werte) werden die Werte zurückgesetzt. Wenn dies der Fall ist, wählen Sie die Werte erneut aus.

   >[!NOTE]
   >
   >Sie können die Bedingungen **[!UICONTROL Anforderung]** und **[!UICONTROL Sichtbarkeit]** unabhängig voneinander anwenden.

1. Erstellen Sie auf ähnliche Weise eine Abhängigkeit zwischen dem Wert „Video“ im Feld „Asset-Typ“ und anderen Feldern wie „Codec“ und „Dauer“.
1. Wiederholen Sie die Schritte, um eine Abhängigkeit zwischen Dokumenten-Assets (PDF und Word) im Feld [!UICONTROL Asset-Typ] und Feldern wie [!UICONTROL Seitenzahl] und [!UICONTROL Autor] zu erstellen.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Wenden Sie das Metadatenschema auf einen Ordner an.

1. Navigieren Sie zu dem Ordner, auf den Sie das Metadatenschema angewendet haben, und öffnen Sie die Eigenschaftenseite eines Assets. Je nachdem, was Sie im Feld „Assettyp“ auswählen, werden relevante kaskadierende Metadatenfelder angezeigt.

   ![Kaskadierende Metadaten für Video-Assets](assets/video_asset.png)

   *Abbildung: Kaskadieren von Metadaten für ein Video.*

   ![Kaskadierende Metadaten für Dokumenten-Assets](assets/doc_type_fields.png)

   *Abbildung: Kaskadieren von Metadaten für ein Dokument*

## Löschen von Metadatenschema-Formularen {#delete-metadata-schema-forms}

In [!DNL Experience Manager] können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können aber alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie ein Formular aus und klicken Sie auf &quot;Löschen&quot;.

>[!NOTE]
>
>* Nachdem Sie benutzerdefinierte Änderungen an einem Standardformular gelöscht haben, wird vor dem Formular die Sperrung ![Sperren](assets/do-not-localize/lock_closed_icon.svg) erneut angezeigt. Es zeigt an, dass das Formular wieder in den Standardstatus zurückgesetzt wird.
>* Sie können die standardmäßigen Metadaten-Schema-Formulare in [!DNL Assets] nicht löschen.


## Schemaformulare für MIME-Typen   {#schema-forms-for-mime-types}

[!DNL Experience Manager] stellt voreingestellte Standardformulare für verschiedene MIME-Typen bereit. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### hinzufügen neuer Formulare für MIME-Typen {#add-new-forms-for-mime-types}

Erstellen Sie ein Formular unter dem entsprechenden Formulartypen. Um beispielsweise eine Vorlage für den Untertyp `image/png` hinzuzufügen, erstellen Sie das Formular unter den &quot;image&quot;-Formularen. Der Titel für das Schemaformular ist der Name des Untertyps. In diesem Fall ist der Titel `png`.

#### Vorhandene Schema-Vorlage für verschiedene MIME-Typen {#use-an-existing-schema-template-for-various-mime-types} verwenden

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. Nutzen Sie beispielsweise das Formular `image/jpeg` für Assets mit dem MIME-Typ `image/png`.

Erstellen Sie in diesem Fall einen Knoten unter `/etc/dam/metadataeditor/mimetypemappings` im CRX-Repository. Geben Sie einen Namen für den Knoten an und definieren Sie die folgenden Eigenschaften:

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

Die Funktion „Metadatenschema“ ist nur für Administratoren verfügbar. Administratoren können jedoch Zugriff auf Nicht-Administratoren gewähren, indem sie einige Berechtigungen ändern. Geben Sie an, ob Benutzer, die keine Administratoren sind, Berechtigungen für `/conf` erstellen, ändern und löschen möchten.

## Anwenden von ordnerspezifischen Metadaten {#apply-folder-specific-metadata}

[!DNL Assets]Mit können Sie Varianten eines Metadatenschemas definieren und auf einen bestimmten Ordner anwenden.

Zum Beispiel können Sie eine Variante des Standard-Metadatenschemas definieren und diese auf einen Ordner anwenden. Das ursprüngliche Standard-Metadatenschema wird dabei überschrieben.

Nur Assets, die in den Ordner hochgeladen wurden, auf den dieses Schema angewendet wird, entsprechen den geänderten Metadaten, die im Schema für Variantenmetadaten definiert wurden. [!DNL Assets] in anderen Ordnern, für die das ursprüngliche Schema gilt, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Metadatenübernahme durch Assets richtet sich nach dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Assets in Ordnern, die keine Unterordner enthalten, übernehmen die Metadaten aus dem Schema, das auf ihren Ordner angewendet wird.

Sie können ein anderes Schema auf den Unterordner anwenden. Die Assets in einem Unterordner übernehmen das Metadaten-Schema des unmittelbaren Unterordners. Wenn kein Schema oder dasselbe Schema auf Unterordnerebene angewendet wird, übernehmen die Assets Schema vom übergeordneten Ordner.

1. Navigieren Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Aktivieren Sie das Kontrollkästchen vor einem Formular, z. B. das Standard-Metadatenformular, und klicken Sie auf **[!UICONTROL Kopieren]** und speichern Sie es als benutzerdefiniertes Formular. Geben Sie einen benutzerdefinierten Namen für das Formular an, beispielsweise `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

1. Wählen Sie auf der Seite **[!UICONTROL Metadaten-Schema Forms]** das `my_default`-Formular und klicken Sie dann auf **[!UICONTROL Bearbeiten]**.

1. Fügen Sie auf der Seite **[!UICONTROL Metadatenschema-Editor]** ein Textfeld in das Schemaformular ein. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu.

   ![Textfeld zum Metadaten-Schema-Formulareditor hinzugefügt](assets/text-field-metadata-schema-editor.png)

   *Abbildung: Textfeld zum Metadaten-Schema-Formulareditor hinzugefügt.*

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.

1. Wählen Sie den Ordner aus, auf den das geänderte Schema angewendet werden soll, und klicken Sie dann auf **[!UICONTROL Apply]**.

   ![Ordner zum Anwenden des Metadaten-Schemas auswählen](assets/metadata-schema-select-folder.png)

1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Klicken Sie auf **Überschreiben**.
1. Klicken Sie auf **OK**, um die Erfolgsmeldung zu schließen.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren obligatorischer Metadaten  {#define-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in den Assets in der Ansicht eine visuelle Anzeige für fehlende Metadaten angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In der Ansicht der Karte zeigt [!DNL Experience Manager] keine Warnmeldung zu fehlenden Metadaten für solche Pflichtmetadatenfelder an.

1. Navigieren Sie in der [!DNL Experience Manager]-Schnittstelle zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie sie beispielsweise unter dem Namen `my_default`.

1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu und definieren Sie es als Pflichtfeld.

   ![hinzufügen eines erforderlichen Felds in das Metadatenformular, indem Sie im Metadaten-Schema-Formulareditor auf der Registerkarte &quot;Regeln&quot;die Option &quot;Erforderlich&quot;auswählen](assets/mandatory-field-metadata-schema-editor.png)

   *Abbildung: Obligatorisches Feld im Metadaten-Schema-Formulareditor.*

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Wählen Sie das Formular aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.

1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. Auf der Ansicht des Assets wird eine Meldung zu den fehlenden Metadaten für das Pflichtfeld angezeigt.

   ![Meldung für fehlende erforderliche Metadaten bei der Ansicht der Asset-Karte beim Hochladen von Assets in den Ordner](assets/metadata-missing-info-card-view.png)

1. (Optional) Rufen Sie `https://[aem_server]:[port]/system/console/components/` auf. Konfigurieren und aktivieren Sie die Komponente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob`, die standardmäßig deaktiviert ist. Legen Sie eine Häufigkeit fest, mit der [!DNL Experience Manager] die Gültigkeit von Metadaten für die Assets überprüft. Diese Konfiguration fügt eine Eigenschaft `hasValidMetadata` zu `jcr:content` in Assets hinzu. [!DNL Experience Manager] verwendet diese Eigenschaft, um die ungültigen Assets in einem Suchergebnis zu filtern. Wenn Sie ein Asset nach einer Prüfung hinzufügen, wird das Asset erst nach der nächsten geplanten Prüfung mit `hasValidMetadata` gekennzeichnet. Daher werden die Assets erst nach der nächsten geplanten Prüfung in den Filtern für ungültige Metadaten angezeigt.

   >[!CAUTION]
   >
   >Die Prüfungen zur Metadatenüberprüfung sind ressourcenintensiv und können sich auf die Leistung Ihres Systems auswirken. Planen Sie die Überprüfungen entsprechend. Wenn der Server die Last nicht bewältigen kann, versuchen Sie, diesen Auftrag zu deaktivieren.

<!-- TBD: Add this method to find invalid metadata in the metadata.md article later when it is published as a top-level metadata article.
-->
