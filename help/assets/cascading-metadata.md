---
title: Kaskadieren von Metadaten in [!DNL Adobe Experience Manager Assets].
description: In diesem Artikel wird die Definition kaskadierender Metadaten für Assets beschrieben.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Kaskadierende Metadaten {#cascading-metadata}

Beim Erfassen der Metadateninformationen eines Assets geben Benutzer Informationen in den verschiedenen verfügbaren Feldern an. Sie können bestimmte Metadatenfelder oder Feldwerte anzeigen, die von den in anderen Feldern ausgewählten Optionen abhängig sind. Solche bedingt angezeigten Metadaten werden als „kaskadierende Metadaten“ bezeichnet. Anders ausgedrückt können Sie eine Abhängigkeit zwischen einem bestimmten Metadatenfeld/-wert und einem oder mehreren Feldern und/oder dessen/deren Werten schaffen.

Verwenden Sie Metadatenschemata, um Regeln für die Anzeige kaskadierender Metadaten zu definieren. Beispiel: Wenn Ihr Metadatenschema ein Feld für den Assettyp enthält, können Sie einen relevanten Satz von Feldern erstellen, die basierend auf der Art des von einem Benutzer ausgewählten Assets angezeigt werden.

Nachfolgend finden Sie einige Anwendungsfälle, für die Sie kaskadierende Metadaten definieren können:

* Wenn der Standort des Benutzers erforderlich ist, können Sie die Namen relevanter Städte basierend auf dem vom Benutzer angegebenen Land und Staat anzeigen.
* Laden Sie relevante Markennamen basierend auf der vom Benutzer ausgewählten Produktgruppe in einer Liste.
* Aktivieren/Deaktivieren Sie die Sichtbarkeit eines bestimmten Felds basierend auf dem in einem anderen Feld angegebenen Wert. Zeigen Sie beispielsweise unterschiedliche Lieferadressen an, wenn der Benutzer angibt, dass die Lieferung an eine andere Adresse gehen soll.
* Legen Sie ein Feld basierend auf dem in einem anderen Feld angegebenen Wert als Pflichtfeld fest.
* Ändern Sie die für ein bestimmtes Feld angezeigten Optionen basierend auf dem in einem anderen Wert angegebenen Wert.
* Legen Sie den standardmäßigen Metadatenwert in einem bestimmten Feld basierend auf dem in einem anderen Feld angegebenen Wert fest.

## Configure cascading metadata in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Stellen Sie sich ein Szenario vor, bei dem Sie kaskadierende Metadaten anzeigen möchten, die auf dem ausgewählten Assettyp basieren. Beispiele

* Zeigen Sie für Videos zutreffende Felder wie Format, Codec, Dauer usw. an.
* Zeigen Sie für ein Word- oder PDF-Dokument Felder wie Seitenzahl, Autor usw. an.

Zeigen Sie unabhängig vom ausgewählten Asset-Typ die Copyright-Informationen als erforderliches Feld an.

1. Wechseln Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadaten-Schema]**.
1. In the **[!UICONTROL Schema Forms]** page, select a schema form and then click **[!UICONTROL Edit]** from the toolbar to edit the schema.

   ![Auswahlformular](assets/select_form.png)

1. (Optional) Erstellen Sie im Metadatenschema-Editor ein neues bedingtes Feld. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an.

   To create a new tab, click `+` to add a tab and then add a metadata field.

   ![Registerkarte hinzufügen](assets/add_tab.png)

1. Fügen Sie ein Dropdownfeld für den Assettyp hinzu. Geben Sie auf der Registerkarte **[!UICONTROL Einstellungen]** einen Namen und den Eigenschaftenpfad an. Fügen Sie optional eine Beschreibung hinzu.

   ![Asset-Typ-Field](assets/asset_type_field.png)

1. Schlüssel-Wert-Paare sind die von einem Formularbenutzer angegebenen Optionen. Sie können Schlüssel-Wert-Paare entweder manuell oder über eine JSON-Datei angeben.

   * To specify the values manually, select **[!UICONTROL Add Manually]**, and click **[!UICONTROL Add Choice]** and specify the option text and value. Legen Sie z. B. die Assettypen „Video“, „PDF“, „Word“ und „Bild“ fest.

   * Um die Werte dynamisch aus einer JSON-Datei abzurufen, wählen Sie **[!UICONTROL Über JSON-Pfad hinzufügen]** aus und geben Sie den Pfad einer JSON-Datei an. [!DNL Experience Manager] ruft die Schlüssel-Wert-Paare in Echtzeit ab, wenn das Formular dem Benutzer angezeigt wird.
   Es kann immer nur eine der beiden Optionen aktiv sein. Sie können keine Optionen aus einer JSON-Datei importieren und sie manuell bearbeiten.

   ![Auswahlmöglichkeiten hinzufügen](assets/add_choice.png)

   >[!NOTE]
   >
   >Wenn Sie eine JSON-Datei hinzufügen, werden die Schlüssel-Wert-Paare nicht im Metadatenschema-Editor angezeigt, sind jedoch im veröffentlichten Formular verfügbar.

   >[!NOTE]
   >
   >Wenn Sie Auswahlmöglichkeiten hinzufügen, wird beim Klicken auf das Dropdown-Feld die Benutzeroberfläche verzerrt dargestellt und das Löschsymbol für die Auswahlmöglichkeiten funktioniert nicht mehr. Klicken Sie erst dann auf das Dropdown, wenn die Änderungen gespeichert wurden. Wenn dieses Problem auftritt, speichern Sie das Schema und öffnen Sie es erneut, um die Bearbeitung fortzusetzen.

1. (Optional) Fügen Sie die anderen erforderlichen Felder hinzu, wie z. B. Format, Codec und Dauer für Assets vom Typ „Video“.

   Fügen Sie ebenso abhängige Felder für andere Asset-Typen hinzu. Fügen Sie bei Dokumenten-Assets wie PDF- und Word-Dateien beispielsweise die Felder „Seitenanzahl“ und „Autor“ hinzu.

   ![Videoabhängigkeitsfelder](assets/video_dependent_fields.png)

1. Um eine Abhängigkeit zwischen dem Feld „Asset-Typ“ und anderen Feldern zu erstellen, wählen Sie das abhängige Feld aus und öffnen Sie die Registerkarte **[!UICONTROL Regeln]**.

   ![Abhängigkeitsfeld auswählen](assets/select_dependentfield.png)

1. Wählen Sie unter **[!UICONTROL Anforderung]** die Option **[!UICONTROL Erforderlich, basierend auf neuer Regel]** aus.
1. Click **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Click **[!UICONTROL Done]** to save the changes.

   ![Regel festlegen](assets/define_rule.png)

   >[!NOTE]
   >
   >Sie können mit Regeln Dropdown-Listen mit manuell vordefinierten Werten verwenden. Dropdownmenüs mit konfiguriertem JSON-Pfad können nicht in Verbindung mit Regeln verwendet werden, die vordefinierte Werte zur Anwendung von Bedingungen verwenden. Wenn die Werte zur Laufzeit aus einer JSON-Datei geladen werden, ist es nicht möglich, vordefinierte Regeln anzuwenden.

1. Wählen Sie unter **[!UICONTROL Sichtbarkeit]** die Option **[!UICONTROL Sichtbar, basierend auf neuer Regel]** aus.

1. Click **[!UICONTROL Add Rule]** and choose the **[!UICONTROL Asset Type]** field to create a dependency. Wählen Sie auch den Feldwert, auf dessen Grundlage die Abhängigkeit erstellt werden soll. Wählen Sie in diesem Fall **[!UICONTROL Video]** aus. Click **[!UICONTROL Done]** to save the changes.

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
