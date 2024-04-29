---
title: Verwalten von Metadaten für digitale Assets
description: Erfahren Sie mehr über die Metadatentypen und die Verwaltung von Metadaten für Assets, um Assets einfach zu organisieren und zu verarbeiten.
contentOwner: AG
mini-toc-levels: 1
feature: Tagging, Metadata
role: Architect, Leader
exl-id: c630709a-7e8b-417c-83a4-35ca9be832a0
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2332'
ht-degree: 100%

---

# Verwalten von Metadaten für digitale Assets {#managing-metadata-for-digital-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-metadata.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

<!-- Scope of metadata articles:
* metadata.md: The scope of this article is basic metadata updates, changes, and so on, operations that end-users can do.
* metadata-concepts.md: All conceptual information. Minor instructions are OK but it is an FYI article about support and standards.
* metadata-config.md: New article. Contains all configuration and administration how-to info related to metadata of assets.
-->

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Metadaten können aus in [!DNL Experience Manager Assets] hochgeladenen Dateien extrahiert werden. Damit lässt sich die Metadatenverwaltung in den kreativen Workflow integrieren. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten.

## Metadaten und ihr Ursprung {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Sie werden zu Assets hinzugefügt und in [!DNL Experience Manager] beim Hochladen eines Assets verarbeitet. Sie können die vorhandenen Metadaten bearbeiten und vorhandenen Feldern neue Metadateneigenschaften hinzufügen. Organisationen benötigen kontrolliertes und zuverlässiges Vokabular für Metadaten. Daher ermöglicht [!DNL Experience Manager Assets] kein On-Demand-Hinzufügen neuer Metadateneigenschaften. Nur Admins sowie Entwicklerinnen und Entwickler können neue Eigenschaften oder Felder hinzufügen, die Metadaten enthalten. Benutzerinnen und Benutzer können die vorhandenen Felder mit Metadaten füllen.

Die folgenden Methoden können zum Hinzufügen von Metadaten zu digitalen Assets verwendet werden:

* Zunächst fügen die nativen Programme, die Assets erstellen, einige Metadaten hinzu. Beispiel: [Acrobat fügt einige Metadaten](https://helpx.adobe.com/de/acrobat/using/pdf-properties-metadata.html) zu PDF-Dateien hinzu oder eine Kamera fügt einige grundlegende Metadaten zu Fotos hinzu. Beim Generieren von Assets können Sie die Metadaten in nativen Programmen selbst hinzufügen. Sie können beispielsweise [IPTC-Metadaten in Adobe Lightroom hinzufügen](https://helpx.adobe.com/de/lightroom-classic/help/metadata-basics-actions.html).

* Vor dem Hochladen eines Assets in [!DNL Experience Manager]können Sie Metadaten bearbeiten und ändern, indem Sie entweder das native Programm zum Erstellen eines Assets oder eine andere Metadaten-Bearbeitungsanwendung verwenden. Wenn Sie ein Asset in Experience Manager hochladen, werden die Metadaten verarbeitet. Lesen Sie hierzu beispielsweise [Arbeiten mit Metadaten in [!DNL Adobe Bridge]](https://helpx.adobe.com/de/bridge/user-guide.html/bridge/using/metadata-adobe-bridge.ug.html) und [Tag-Bereich für [!DNL Adobe Bridge]](https://exchange.adobe.com/creativecloud.details.20009.aem-tags-panel-for-bridge-cc.html) in [!DNL Adobe Exchange].

* In [!DNL Experience Manager Assets] können Sie Metadaten von Assets auf der Seite [!UICONTROL Eigenschaften] manuell hinzufügen oder bearbeiten.

* Sie können [Metadatenprofil](/help/assets/metadata-config.md#metadata-profiles)-Funktionen von [!DNL Experience Manager Assets] verwenden, um beim Hochladen von Assets in DAM automatisch Metadaten hinzuzufügen.

## Hinzufügen oder Bearbeiten von Metadaten in [!DNL Experience Manager Assets] {#add-edit-metadata}

Führen Sie zum Bearbeiten von Metadaten eines Assets in [!DNL Assets] die folgenden Schritte aus:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus und klicken Sie auf der Symbolleiste auf **[!UICONTROL Eigenschaften anzeigen]**.
   * Wählen Sie die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus der Miniatur des Assets aus.
   * Klicken Sie auf der Asset-Seite auf der Symbolleiste auf **[!UICONTROL Eigenschaften anzeigen]** ![Symbol für Assets-Informationen](assets/do-not-localize/info-circle-icon.png).

   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Die Metadaten werden extrahiert, wenn das Asset in [!DNL Experience Manager] hochgeladen (aufgenommen) wird.

   ![Auswählen der Eigenschaften eines Assets, um seine Metadaten anzuzeigen](assets/asset-metadata.png)

   *Abbildung: Bearbeiten oder Hinzufügen von Metadaten auf der Seite [!UICONTROL Eigenschaften] des Assets.*

1. Nehmen Sie auf den verschiedenen Registerkarten bei Bedarf Änderungen an den Metadaten vor. Klicken Sie anschließend auf der Symbolleiste auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Klicken Sie auf **[!UICONTROL Schließen]**, um zur Web-Benutzeroberfläche von [!DNL Assets] zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen.

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Der Metadaten-Writeback-Workflow fügt die Metadaten zur ursprünglichen Binärdatei hinzu. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich anwenderdefinierten Eigenschaften wie `cq:tags`) mit dem Schema hinzugefügt.

XMP-Writeback wird für die unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md) beschriebenen Plattformen und Dateiformate unterstützt und aktiviert.

## Bearbeiten von Metadateneigenschaften für mehrere Assets {#editing-metadata-properties-of-multiple-assets}

Mit [!DNL Adobe Enterprise Manager Assets] können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Sie können die Metadaten für mehrere Sammlungen zusammen bearbeiten. Verwenden Sie die Eigenschaftenseite, um Metadatenänderungen an mehreren Assets oder Sammlungen durchzuführen:

* Metadateneigenschaften in einen gemeinsamen Wert ändern
* Tags hinzufügen oder ändern

Verwenden Sie zum Anpassen der Seite mit Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den [Schemaeditor](metadata-config.md#folder-metadata-schema).

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](search-assets.md#metadataupdates).

1. Navigieren Sie auf der [!DNL Assets]-Benutzeroberfläche zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Eigenschaften]**, um für die ausgewählten Assets die Seite „Eigenschaften“ zu öffnen.
1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um die Metadaten für ein bestimmtes Asset anzuzeigen. Wenn Sie die Auswahl einiger Assets auf der Seite [!UICONTROL Eigenschaften] abbrechen, werden die Metadaten dieser Assets nicht aktualisiert.
1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, klicken Sie auf der Symbolleiste auf **[!UICONTROL Einstellungen]** und wählen Sie das gewünschte Schema aus. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Klicken Sie auf **[!UICONTROL Senden]**.

![Massenanwendung des Metadatenschemata auf mehrere Assets](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Importieren von Metadaten {#import-metadata}

Mit [!DNL Assets] können Sie Asset-Metadaten mithilfe einer CSV-Datei in Massen importieren. Sie können für die kürzlich hochgeladenen Assets oder die vorhandenen Assets eine Massenaktualisierung durchführen, indem Sie eine CSV-Datei importieren. Außerdem können Sie Asset-Metadaten von Drittanbietersystemen mithilfe des CSV-Formats in Batches erfassen.

Die Metadaten werden asynchron importiert, sodass der Import die Systemleistung nicht beeinträchtigt. Die gleichzeitige Aktualisierung der Metadaten für mehrere Assets kann aufgrund der XMP-Writeback-Aktivität ressourcenintensiv sein, wenn die Hervorhebung für die Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Server-Nutzung, um Leistungseinbußen für andere Benutzende zu vermeiden.

>[!NOTE]
>
>Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.

1. Navigieren Sie zur [!DNL Assets]-Benutzeroberfläche und klicken Sie auf der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie aus dem Menü **[!UICONTROL Metadaten]** aus.
1. Tippen/klicken Sie auf der Seite **[!UICONTROL Metadaten-Import]** auf **[!UICONTROL Datei auswählen]**. Wählen Sie die CSV-Datei mit den Metadaten aus.
1. Geben Sie die folgenden Parameter an. Eine CSV-Beispieldatei finden Sie unter [metadata-import-sample-file.csv](/help/assets/assets/metadata-import-sample-file.csv).

   | Metadaten-Importparameter | Beschreibung |
   |:---|:---|
   | [!UICONTROL Batch-Größe] | Anzahl der Assets in einem Batch, für die Metadaten importiert werden sollen. Der Standardwert ist 50. Der Wert darf maximal 100 betragen. |
   | [!UICONTROL Feldtrennzeichen] | Der Standardwert ist `,` (ein Komma). Sie können jedoch ein beliebiges anderes Zeichen eingeben. |
   | [!UICONTROL Mehrfachtrennzeichen] | Trennzeichen für Metadatenwerte. Der Standardwert ist `|`. |
   | [!UICONTROL Workflows starten] | Lautet standardmäßig „False“. Wenn hier `true` festgelegt ist und die standardmäßigen Einstellungen für den Workflow „[!UICONTROL DAM-Metadaten-WriteBack]“ aktiv sind (der Metadaten in die binären XMP-Daten schreibt). Die Aktivierung von Workflows verlangsamt das System. |
   | [!UICONTROL Asset-Pfad-Spaltenname] | Definiert den Namen der Spalte in der CSV-Datei, die die Assets enthält. |

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Importieren]**. Nachdem die Metadaten importiert wurden, wird eine Benachrichtigung in Ihrem [!UICONTROL Benachrichtigungs]-Posteingang angezeigt.

1. Navigieren Sie zum Überprüfen des korrekten Imports zur Seite [!UICONTROL Eigenschaften] eines Assets und überprüfen Sie die Werte in den Feldern.

Um beim Importieren von Metadaten Datum und Zeitstempel hinzuzufügen, verwenden Sie das `YYYY-MM-DDThh:mm:ss.fff-00:00`-Format für Datum und Uhrzeit. Datum und Uhrzeit werden durch `T` getrennt angegeben. `hh` ist Stunden im 24-Stunden-Format, `fff` ist Nanosekunden und `-00:00` ist der Zeitzonenversatz. Zum Beispiel ist `2020-03-26T11:26:00.000-07:00` der 26. März 2020 um 11:26:00.000 Uhr (PST).

>[!CAUTION]
>
>Wenn das Datumsformat nicht mit `YYYY-MM-DDThh:mm:ss.fff-00:00` übereinstimmt, werden die Datumswerte nicht eingestellt. Die Datumsformate der exportierten Metadaten-CSV-Datei entsprechen dem Format `YYYY-MM-DDThh:mm:ss-00:00`. Wenn Sie das Datum importieren möchten, konvertieren Sie es in das akzeptable Format, indem Sie den mit `fff` angegebenen Nanosekundenwert hinzufügen.

## Exportieren von Metadaten {#export-metadata}

Sie können Metadaten für mehrere Assets in einem CSV-Format exportieren. Die Metadaten werden asynchron exportiert, sodass der Export die Systemleistung nicht beeinträchtigt. Wenn Sie Metadaten exportieren, durchsucht [!DNL Experience Manager] die Eigenschaften des Asset-Knotens `jcr:content/metadata` und der untergeordneten Knoten und exportiert die Metadateneigenschaften in eine CSV-Datei.

Einige Nutzungsszenarien für den Massenexport von Metadaten:

* Importieren Sie die Metadaten in ein Drittanbietersystem, wenn Sie Assets migrieren.
* Geben Sie Asset-Metadaten für ein breiteres Projektteam frei.
* Testen oder prüfen Sie die Metadaten auf Ihre Konformität.
* Externalisieren Sie die Metadaten, um sie separat zu lokalisieren.

1. Wählen Sie einen Asset-Ordner aus, der Assets enthält, für die Sie Metadaten exportieren möchten. Wählen Sie in der Symbolleiste **[!UICONTROL Metadaten exportieren]** aus.

1. Geben Sie im Dialogfeld [!UICONTROL Metadatenexport] einen Namen für die CSV-Datei an. Um Metadaten von Assets in Unterordnern zu exportieren, wählen Sie **[!UICONTROL Assets in Unterordnern einschließen]**.

   ![Benutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in einem Ordner](assets/export_metadata_page.png "Benutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in einem Ordner")

1. Wählen Sie die gewünschten Optionen aus. Geben Sie einen Dateinamen und ggf. ein Datum an.

1. Geben Sie im Feld **[!UICONTROL Zu exportierende Eigenschaften]** an, ob Sie alle oder nur bestimmte Eigenschaften exportieren wollen. Wenn Sie für den Export „Selektive Eigenschaften“ auswählen, fügen Sie die gewünschten Eigenschaften hinzu.

1. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Exportieren]**. Sie erhalten eine Meldung, die bestätigt, dass die Metadaten exportiert wurden. Schließen Sie die Meldung.

1. Öffnen Sie die Posteingangsbenachrichtigung für den Exportauftrag. Wählen Sie den Auftrag aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Öffnen]**. Um die CSV-Datei mit den Metadaten herunterzuladen, klicken Sie auf der Symbolleiste auf **[!UICONTROL CSV-Download]**. Klicken Sie auf **[!UICONTROL Schließen]**.

   ![Dialogfeld zum Herunterladen der CSV-Datei mit Metadaten, die stapelweise exportiert wurden](assets/csv_download.png)

   *Abbildung: Dialogfeld zum Herunterladen der CSV-Datei mit Metadaten, die stapelweise exportiert wurden.*

## Bearbeiten der Metadaten von Sammlungen {#collections-metadata}

Weitere Informationen finden Sie unter [Anzeigen und Bearbeiten von Sammlungsmetadaten](/help/assets/manage-collections.md#view-edit-collection-metadata) und [Stapelweises Bearbeiten der Metadaten mehrerer Sammlungen](/help/assets/manage-collections.md#editing-collection-metadata-in-bulk).

## Anwenden eines Metadatenprofils auf Ordner {#applying-a-metadata-profile-to-folders}

<!-- TBD: Review this overview.
-->

Wenn Sie ein Metadatenprofil zu einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Metadatenprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Metadatenprofil zugewiesen haben, überschreibt das neue Profil das vorherige Profil. Die zuvor vorhandenen Ordner-Assets bleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche durch den Namen des Profils angegeben, der im Kartennamen angezeigt wird.

![Kartenansicht mit dem Metadatenprofil, das auf einen Ordner angewendet wurde](assets/metadata-profile-card-view-display.png)

Sie können Metadatenprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

Sie können ein Metadatenprofil über das Menü **[!UICONTROL Tools]** oder, falls Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Metadatenprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden von Metadatenprofilen auf Ordner über die Benutzeroberfläche [!UICONTROL Profile] {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

Gehen Sie wie folgt vor, um das Metadatenprofil anzuwenden:

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.
1. Klicken Sie auf **[!UICONTROL Metadatenprofil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Klicken Sie anschließend auf **[!UICONTROL Fertig]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

### Anwenden von Metadatenprofilen auf Ordner über [!UICONTROL Eigenschaften] {#applying-metadata-profiles-to-folders-from-properties}

1. Klicken Sie auf der linken Leiste auf **[!UICONTROL Assets]** und navigieren Sie dann zu dem Ordner, auf den Sie ein Metadatenprofil anwenden möchten.
1. Klicken Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.

1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** und anschließend das Profil aus dem Popup-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

<!-- TBD: Commenting as the topic in metadata-config.md is incomplete.

### Apply metadata profile globally {#metadata-profile-global}

For details, see [configuration to apply metadata profile globally](/help/assets/metadata-config.md#apply-a-metadata-profile-globally). -->

### Entfernen eines Metadatenprofils aus Ordnern {#removing-a-metadata-profile-from-folders}

Wenn Sie ein Metadatenprofil aus einem Ordner entfernen, übernehmen alle Unterordner automatisch die Entfernung des Profils aus dem übergeordneten Ordner. Die Verarbeitung von Dateien, die in den Ordnern stattgefunden hat, bleibt jedoch intakt.

Sie können ein Metadatenprofil aus einem Ordner über das Menü **[!UICONTROL Tools]** oder über die **[!UICONTROL Eigenschaften]** im Ordner entfernen.

#### Entfernen von Metadatenprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.
1. Wählen Sie ein Metadatenprofil aus, das Sie aus einem oder mehreren Ordnern entfernen möchten.
1. Klicken Sie auf **[!UICONTROL Metadatenprofil aus Ordner(n) entfernen]** und wählen Sie einen oder mehrere Ordner aus, aus dem bzw. denen ein Profil entfernt werden soll, und klicken Sie dann auf **[!UICONTROL Fertig]**.

   Sie können bestätigen, dass das Metadatenprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

#### Entfernen von Metadatenprofilen aus Ordnern über „Eigenschaften“ {#removing-metadata-profiles-from-folders-via-properties}

1. Klicken Sie auf das [!DNL Experience Manager]-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann in den Ordner, aus dem Sie ein Metadatenprofil entfernen möchten.
1. Klicken Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Metadatenprofile]** aus. Wählen Sie anschließend **[!UICONTROL Keine]** aus dem Dropdown-Menü aus und klicken Sie auf **[!UICONTROL Speichern]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

## Tipps und Einschränkungen {#best-practices-limitations}

* Die über die Benutzeroberfläche aktualisierten Metadaten ändern die Metadateneigenschaften im `dc`-Namespace. Jegliche über die HTTP-API vorgenommenen Aktualisierungen ändern die Metadateneigenschaften im `jcr`-Namespace. Siehe [Aktualisieren von Metadaten mithilfe der HTTP-API](/help/assets/mac-api-assets.md#update-asset-metadata).

* Die CSV-Datei zum Importieren von Asset-Metadaten weist ein sehr spezifisches Format auf. Um Aufwand und Zeit zu sparen und unbeabsichtigte Fehler zu vermeiden, können Sie zum Erstellen der CSV-Datei das Format einer exportierten CSV-Datei als Ausgangspunkt verwenden.

* Beim Importieren von Metadaten aus einer CSV-Datei ist das erforderliche Datumsformat `YYYY-MM-DDThh:mm:ss.fff-00:00`. Wenn ein anderes Format verwendet wird, werden die Datumswerte nicht festgelegt. Die Datumsformate der exportierten Metadaten-CSV-Datei entsprechen dem Format `YYYY-MM-DDThh:mm:ss-00:00`. Wenn Sie das Datum importieren möchten, konvertieren Sie es in das akzeptable Format, indem Sie den mit `fff` angegebenen Nanosekundenwert hinzufügen.

>[!MORELIKETHIS]
>
>* [Konzepte und Grundlagen von Metadaten](metadata-concepts.md).
>* [Bearbeiten von Metadateneigenschaften mehrerer Sammlungen](manage-collections.md#editing-collection-metadata-in-bulk)
>* [Importieren und Exportieren von Metadaten in Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html?lang=de)

<!-- TBD: Try filling the available information in these topics to the extent possible. As and when complete, publish the sections live.

## Where to find metadata of an asset or folder {#find-metadata}

What all methods to access asset Properties. More Details option in column view. Select asset and click Properties. Keyboard shortcut `p`. What else?

## Understand metadata handling in Experience Manager {#metadata-possibilities-with-aem}

Describe the journey of an assets' metadata. What all happens to metadata when an asset is added to Experience Manager.

## Add metadata to your digital assets {#add-metadata}

* To begin with, assets come with some metadata. The applications that create digital assets add some metadata to the assets created. Before uploading an asset to Experience Manager, you can edit and modify metadata using either the native application used to create an asset or using some other metadata editing application. When you upload an asset to Experience Manager, the metadata is processed.

* Link to PS, ID, AI, PDF, and so on, metadata-related help articles.

* Link to XMP writeback.

* Manually add (or edit) metadata in AEM in Properties page.

* Metadata profiles

* Any workflows related to metadata?

* Advanced topic: Add, edit, modify, process and writeback metadata of subassets.

## Metadata of assets, folders, and collections {#metadata-of-assets-folders-collections}

Similarities and differences between metadata of asset and folder. 

Link to metadata handling of collections.

## Modify metadata of an asset, folder, or collection {#modify-metadata}

* While creating assets: Native application.

* Before ingesting assets: Metadata editors

* After ingesting assets: Properties of an asset, folder, collection, and so on.

* Any supported programmatic method to bulk edit metadata directly in JCR?

## Modify metadata in bulk {#modify-metadata-in-bulk}

[!DNL Adobe Enterprise Manager Assets] lets you edit the metadata of multiple assets simultaneously so you can quickly propagate common metadata changes to assets in bulk. You can also edit the metadata for multiple collections in bulk.

Use the properties page to perform metadata changes on multiple assets or collections:

* Change metadata properties to a common value

* Add or modify tags

To customize the metadata properties page, including adding, modifying, deleting metadata properties, use the schema editor.

>[!NOTE]
>
>The bulk editing methods work for assets available in a folder or a collection. For the assets that are available across folders or match a common criteria, it is possible to [bulk update the metadata after searching](search-assets.md#metadataupdates).

1. In the [!DNL Assets] user interface, navigate to the location of the assets you want to edit.
1. Select the assets for which you want to edit common properties.
1. From the toolbar, click **[!UICONTROL Properties]** to open the properties page for the selected assets.

   >[!NOTE]
   >
   >When you select multiple assets, the lowest common parent form is selected for the assets. In other words, the properties page only displays metadata fields that are common across the properties pages of all the individual assets.

1. Modify the metadata properties for selected assets under the various tabs.
1. To view the metadata editor for a specific asset, deselect the remaining assets in the list. The metadata editor fields are populated with the metadata for the particular asset.

   >[!NOTE]
   >
   >* In the Properties page, you can remove assets from the asset list by deselecting them. The asset list has all the assets selected by default. The metadata for assets that you remove from the list is not updated.
   >
   >* At the top of assets list, select the check box near **[!UICONTROL Title]** to toggle between selecting the assets and clearing the list.

1. To select a different metadata schema for the assets, click **[!UICONTROL Settings]** from the toolbar, and select the desired schema.
1. Save the changes.
1. To append the new metadata with the existing metadata in fields that contain multiple values, select **[!UICONTROL Append mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. click **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >For single-value fields, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

-->
