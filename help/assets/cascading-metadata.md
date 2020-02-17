---
title: Kaskadierende Metadaten
description: In diesem Artikel wird die Definition kaskadierender Metadaten für Assets beschrieben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Kaskadierende Metadaten {#cascading-metadata}

Beim Erfassen der Metadateninformationen eines Assets geben Benutzer Informationen in den verschiedenen verfügbaren Feldern an. Sie können bestimmte Metadatenfelder oder Feldwerte anzeigen, die von den in anderen Feldern ausgewählten Optionen abhängig sind. Solche bedingt angezeigten Metadaten werden als „kaskadierende Metadaten“ bezeichnet. Anders ausgedrückt können Sie eine Abhängigkeit zwischen einem bestimmten Metadatenfeld/-wert und einem oder mehreren Feldern und/oder dessen/deren Werten schaffen.

Verwenden Sie Metadatenschemata, um Regeln für die Anzeige kaskadierender Metadaten zu definieren. Beispiel: Wenn Ihr Metadatenschema ein Feld für den Assettyp enthält, können Sie einen relevanten Satz von Feldern erstellen, die basierend auf der Art des von einem Benutzer ausgewählten Assets angezeigt werden.

Nachfolgend finden Sie einige Anwendungsfälle, für die Sie kaskadierende Metadaten definieren können:

* Wenn der Standort des Benutzers erforderlich ist, können Sie die Namen relevanter Städte basierend auf dem vom Benutzer angegebenen Land und Staat anzeigen.
* Laden Sie relevante Markennamen basierend auf der vom Benutzer ausgewählten Produktgruppe in einer Liste.
* Aktivieren/Deaktivieren Sie die Sichtbarkeit eines bestimmten Felds basierend auf dem in einem anderen Feld angegebenen Wert. Zeigen Sie beispielsweise unterschiedliche Lieferadressen an, wenn der Benutzer angibt, dass die Lieferung an eine andere Adresse gehen soll.
* Benennen Sie ein Feld als obligatorisch basierend auf dem in einem anderen Feld angegebenen Wert.
* Ändern Sie die für ein bestimmtes Feld angezeigten Optionen basierend auf dem in einem anderen Wert angegebenen Wert.
* Legen Sie den standardmäßigen Metadatenwert in einem bestimmten Feld basierend auf dem in einem anderen Feld angegebenen Wert fest.

## Erstellen kaskadierender Metadaten in AEM {#configure-cascading-metadata-in-aem}

Stellen Sie sich ein Szenario vor, bei dem Sie kaskadierende Metadaten anzeigen möchten, die auf dem ausgewählten Assettyp basieren. Beispiele

* Zeigen Sie für Videos zutreffende Felder wie Format, Codec, Dauer usw. an.
* Zeigen Sie für ein Word- oder PDF-Dokument Felder wie Seitenzahl, Autor usw. an.

Zeigen Sie unabhängig vom ausgewählten Asset-Typ die Copyright-Informationen als erforderliches Feld an.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Wählen Sie auf der Seite **[!UICONTROL Schemaformulare]** ein Schemaformular aus und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**, um das Schema zu bearbeiten.

   ![select_form](assets/select_form.png)

1. (Optional) Erstellen Sie im Metadatenschema-Editor ein neues bedingtes Feld. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an.

   To create a new tab, tap/click `+` to add a tab and then add a metadata field.

   ![add_tab](assets/add_tab.png)

1. Fügen Sie ein Dropdownfeld für den Assettyp hinzu. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an. Fügen Sie optional eine Beschreibung hinzu.

   ![asset_type_field](assets/asset_type_field.png)

1. Schlüssel-Wert-Paare sind die von einem Formularbenutzer angegebenen Optionen. Sie können Schlüssel-Wert-Paare entweder manuell oder über eine JSON-Datei angeben.

   * Um die Werte manuell anzugeben, wählen Sie **[!UICONTROL Manuell hinzufügen]** aus, tippen/klicken Sie auf **[!UICONTROL Auswahl hinzufügen]** und geben Sie den Optionstext und -wert an. Legen Sie z. B. die Assettypen „Video“, „PDF“, „Word“ und „Bild“ fest.

   * Um die Werte dynamisch aus einer JSON-Datei abzurufen, wählen Sie **[!UICONTROL Über JSON-Pfad hinzufügen]** aus und geben Sie den Pfad einer JSON-Datei an. AEM ruft die Schlüssel-Wert-Paare in Echtzeit ab, wenn das Formular dem Benutzer angezeigt wird.
   Es kann immer nur eine der beiden Optionen aktiv sein. Sie können keine Optionen aus einer JSON-Datei importieren und sie manuell bearbeiten.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >Wenn Sie eine JSON-Datei hinzufügen, werden die Schlüssel-Wert-Paare nicht im Metadatenschema-Editor angezeigt, sind jedoch im veröffentlichten Formular verfügbar.

   >[!NOTE]
   >
   >Wenn Sie Auswahlmöglichkeiten hinzufügen, wird beim Klicken auf das Dropdown-Feld die Benutzeroberfläche verzerrt dargestellt und das Löschsymbol für die Auswahlmöglichkeiten funktioniert nicht mehr. Klicken Sie erst dann auf das Dropdown, wenn die Änderungen gespeichert wurden. Wenn dieses Problem auftritt, speichern Sie das Schema und öffnen Sie es erneut, um die Bearbeitung fortzusetzen.

1. (Optional) Fügen Sie die anderen erforderlichen Felder hinzu, wie z. B. Format, Codec und Dauer für Assets vom Typ „Video“.

   Fügen Sie ebenso abhängige Felder für andere Asset-Typen hinzu. Fügen Sie z. B. die Anzahl der Felder und den Autor für Dokumentelemente wie PDF- und Word-Dateien hinzu.

   ![video_dependence_fields](assets/video_dependent_fields.png)

1. Um eine Abhängigkeit zwischen dem Feld „Assettyp“ und anderen Feldern zu erstellen, wählen Sie das abhängige Feld aus und öffnen Sie die Registerkarte **[!UICONTROL Regeln]**.

   ![select_depenentfield](assets/select_dependentfield.png)

1. Wählen Sie unter **[!UICONTROL Anforderung]** die Option **[!UICONTROL Erforderlich, basierend auf neuer Regel]** aus.
1. Tippen/klicken Sie auf **[!UICONTROL Regel hinzufügen]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]** aus, um eine Abhängigkeit zu erstellen. Wählen Sie außerdem den Feldwert aus, für den die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Tippen/klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >Sie können mit Regeln Dropdown-Listen mit manuell vordefinierten Werten verwenden. Dropdownmenüs mit konfiguriertem JSON-Pfad können nicht in Verbindung mit Regeln verwendet werden, die vordefinierte Werte zur Anwendung von Bedingungen verwenden. Wenn die Werte zur Laufzeit aus einer JSON-Datei geladen werden, ist es nicht möglich, vordefinierte Regeln anzuwenden.

1. Under **[!UICONTROL Visibility]**, choose the **[!UICONTROL Visible, based on new rule]** option.

1. Tippen/klicken Sie auf **[!UICONTROL Regel hinzufügen]** und wählen Sie das Feld **[!UICONTROL Asset-Typ]** aus, um eine Abhängigkeit zu erstellen. Wählen Sie außerdem den Feldwert aus, für den die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Tippen/klicken Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern.

   ![define_visibilityRule](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Durch Tippen/Klicken auf einen Leerraum (oder einen anderen Ort als die Werte) werden die Werte zurückgesetzt. Wenn dies der Fall ist, wählen Sie die Werte erneut aus.

   >[!NOTE]
   >
   >Sie können die Bedingungen **[!UICONTROL Anforderung]** und **[!UICONTROL Sichtbarkeit]** unabhängig voneinander anwenden.

1. Erstellen Sie auf ähnliche Weise eine Abhängigkeit zwischen dem Wert Video im Feld Asset-Typ und anderen Feldern, z. B. Codec und Dauer.
1. Repeat the steps to create dependency between document assets (PDF and Word) in the [!UICONTROL Asset Type] field and fields such as [!UICONTROL Page Count] and [!UICONTROL Author].
1. Klicken Sie auf **[!UICONTROL Speichern]**. Wenden Sie das Metadatenschema auf einen Ordner an.

1. Navigieren Sie zu dem Ordner, auf den Sie das Metadatenschema angewendet haben, und öffnen Sie die Eigenschaftenseite eines Assets. Je nachdem, was Sie im Feld „Assettyp“ auswählen, werden relevante kaskadierende Metadatenfelder angezeigt.

   ![Kaskadierende Metadaten für Video-Assets](assets/video_asset.png)
   *Abbildung: Kaskadieren von Metadaten für ein Video*

   ![Kaskadierende Metadaten für Dokumenten-Assets](assets/doc_type_fields.png)
   *Abbildung: Metadaten für ein Dokument kopieren*
