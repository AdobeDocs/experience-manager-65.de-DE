---
title: XMP-Writeback zu Ausgabedarstellungen
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 82148ae5-37e9-4fc5-ada9-db3d91b29c33
source-git-commit: 9d5440747428830a3aae732bec47d42375777efd
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 63%

---

# XMP-Writeback zu Ausgabedarstellungen {#xmp-writeback-to-renditions}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/xmp-metadata.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/xmp-writeback.html?lang=en) |

Die XMP-Writeback-Funktion in [!DNL Adobe Experience Manager Assets] repliziert Änderungen von Metadaten in den Ausgabedarstellungen des Original-Assets. Wenn Sie die Metadaten für ein Asset in Assets ändern oder das Asset hochladen, werden die Änderungen zunächst im Metadatenknoten in der Asset-Hierarchie gespeichert.

Mit der XMP-Writeback-Funktion können Sie die Metadatenänderungen in alle oder nur in bestimmte Ausgabedarstellungen des Assets kopieren. Die Funktion schreibt nur die Metadateneigenschaften zurück, die den Namespace `jcr` verwenden, d. h. eine Eigenschaft namens `dc:title` wird zurückgeschrieben, eine Eigenschaft namens `mytitle` jedoch nicht.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall wird die [!DNL Experience Manager Assets] speichert die Änderungen an der **[!UICONTROL Titel]** -Eigenschaft in `dc:title` -Parameter für die in der Asset-Hierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

[!DNL Experience Manager Assets] propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabedarstellungen eines Assets. Siehe [Wie wird XMP Writeback aktiviert?](#enable-xmp-writeback).

## Aktivieren der XMP-Writeback-Funktion {#enable-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL XMP propagieren]** aus und speichern Sie die Änderungen.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion Metadatenänderungen an Ausgabeformate weiterleiten kann, geben Sie diese Ausgabeformate im Workflow-Schritt XMP Writeback-Prozess von [!UICONTROL DAM-Metadaten-WriteBack] Arbeitsablauf. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Navigieren Sie in der Experience Manager-Benutzeroberfläche zu **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Öffnen Sie über die Seite „Modelle“ das Workflow-Modell **[!UICONTROL DAM-Metadaten-Writeback]**.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1. Im [!UICONTROL Schritt-Eigenschaften] Klicken Sie im Dialogfeld auf **[!UICONTROL Prozess]** Registerkarte.
1. Im **Argumente** Feld, hinzufügen `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`und klicken Sie auf **[!UICONTROL OK]**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. So generieren Sie die Pyramid TIFF-Ausgabeformate für [!DNL Dynamic Media] Bilder mit den neuen Attributen, fügen Sie die **[!UICONTROL Dynamic Media Process Image Assets]** Schritt zum [!UICONTROL DAM-Metadaten-Writeback] Arbeitsablauf.

   PTIFF-Ausgabedarstellung werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate „thumbnail.140.100.png“ und „thumbnail.319.319.png“ des Elements und nicht auf die anderen Ausgabeformate übertragen.

>[!NOTE]
>
>XMP Probleme beim Writeback unter 64 Bit Linux finden Sie unter [Aktivieren XMP Writeback auf 64-Bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Informationen zu den unterstützten Plattformen finden Sie unter [Voraussetzungen für XMP Zurückschreiben von Metadaten](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] unterstützt sowohl die Blockierungsliste- als auch die Zulassungsliste-Filterung von Eigenschaften/Knoten für XMP Metadaten, die aus Asset-Binärdateien gelesen und in JCR gespeichert werden, wenn Assets erfasst werden.

Bei der Filterung über eine Blockierungsliste können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn beim Filtern mit einer Blockierungsliste eine große Anzahl von Assets mit zahlreichen XMP Metadaten importiert werden kann, wird die [!DNL Experience Manager] -Implementierungen können auf Stabilitätsprobleme stoßen, z. B. blockierte Beobachtungswarteschlangen.

Durch Filtern von XMP-Metadaten über die Zulassungsliste wird dieses Problem behoben, indem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Filter hinzufügen, der eine Blockierungsliste verwendet.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. Experience Manager speichert diesen Wert in einem Metadatenfeld mit dem Namen `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Um die Filterfunktion mit einer Zulassungsliste anzuwenden, klicken Sie auf **[!UICONTROL Zulassungsliste auf XMP-Eigenschaften anwenden]** und geben Sie die Eigenschaften an, die in das Feld **[!UICONTROL Zulässige XML-Namen für XMP-Filterfunktion]** importiert werden sollen.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Um die blockierten XMP nach Anwendung der Filterung über die Zulassungsliste herauszufiltern, geben Sie diese in der **[!UICONTROL Blockierte XML-Namen für XMP Filterung]** ankreuzen.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blockierungsliste auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Mit anderen Worten, das Filtern über eine Blockierungsliste ist standardmäßig aktiviert. Um diese Filterung zu deaktivieren, brechen Sie die Auswahl der **[!UICONTROL Anwenden der Blockierungsliste auf XMP Eigenschaften]** -Option.

1. Speichern Sie die Änderungen.
