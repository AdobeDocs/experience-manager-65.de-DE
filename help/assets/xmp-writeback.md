---
title: XMP-Writeback zu Ausgabedarstellungen
description: Die Funktion „XMP Writeback“ kopiert die Metadatenänderungen in alle oder nur in bestimmte Ausgabedarstellungen des Assets.
contentOwner: AG
role: User, Admin
feature: Metadata
exl-id: 82148ae5-37e9-4fc5-ada9-db3d91b29c33
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 87%

---

# XMP-Writeback zu Ausgabedarstellungen {#xmp-writeback-to-renditions}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/xmp-metadata.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Die XMP-Writeback-Funktion in [!DNL Adobe Experience Manager Assets] repliziert Änderungen von Metadaten in den Ausgabedarstellungen des Original-Assets. Wenn Sie die Metadaten für ein Asset aus Assets heraus ändern oder das Asset hochladen, werden die Änderungen zuerst im Metadaten-Knoten in der Asset-Hierarchie gespeichert.

Mit der XMP-Writeback-Funktion können Sie die Metadatenänderungen in alle oder nur in bestimmte Ausgabedarstellungen des Assets kopieren. Die Funktion schreibt nur die Metadateneigenschaften zurück, die den Namespace verwenden, d. h. eine Eigenschaft namens `dc:title` wird zurückgeschrieben, eine Eigenschaft namens `mytitle` jedoch nicht.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall speichert [!DNL Experience Manager Assets] die Änderungen an der Eigenschaft **[!UICONTROL Titel]** im Parameter `dc:title` der in der Asset-Hierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

[!DNL Experience Manager Assets] propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabedarstellungen eines Assets. Erfahren Sie, [wie Sie die XMP-Writeback-Funktion aktivieren](#enable-xmp-writeback).

## Aktivieren der XMP-Writeback-Funktion {#enable-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL XMP propagieren]** aus und speichern Sie die Änderungen.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabedarstellungen kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt „XMP-Writeback-Vorgang“ des Workflows [!UICONTROL DAM-Metadaten-Writeback] angeben. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte aus, damit die Funktion „XMP Writeback“ Metadaten in die Miniaturansichten „140.100.png“ und „319.319.png“ der Ausgabedarstellung überträgt.

1. Gehen Sie in der Experience Manager-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Öffnen Sie über die Seite „Modelle“ das Workflow-Modell **[!UICONTROL DAM-Metadaten-Writeback]**.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1. Klicken Sie im Dialogfeld [!UICONTROL Schritteigenschaften] auf die Registerkarte **[!UICONTROL Vorgang]**.
1. Fügen Sie im Feld **Argumente** `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` hinzu und klicken Sie auf **[!UICONTROL OK]**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. Um die Pyramid-TIFF-Ausgabeformate für [!DNL Dynamic Media]-Bilder mit neuen Attributen zu erstellen, fügen Sie den Schritt **[!UICONTROL Verarbeiten von Bild-Assets in Dynamic Media]** zum Workflow [!UICONTROL DAM-Metadaten-Writeback] hinzu.

   PTIFF-Ausgabedarstellung werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate „thumbnail.140.100.png“ und „thumbnail.319.319.png“ des Elements und nicht auf die anderen Ausgabeformate übertragen.

>[!NOTE]
>
>Informationen zu Problemen bezüglich XMP-Writeback unter 64-Bit-Linux finden Sie unter [XMP-Writeback unter 64-Bit-RedHat Linux aktivieren](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>Informationen zu den unterstützten Plattformen finden Sie unter [Voraussetzungen für XMP-Metadaten-Writeback](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] unterstützt das Filtern von Blockierungslisten und Zulassungslisten von Eigenschaften/Knoten nach XMP-Metadaten, die von den Binärdateien des Assets gelesen und in JCR gespeichert werden, wenn Assets aufgenommen werden.

Bei der Filterung über eine Blockierungsliste können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Bei Asset-Typen wie INDD-Dateien mit großen Mengen XMP Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) sind die Namen der zu filternden Knoten jedoch nicht immer im Voraus bekannt. Wenn beim Filtern mit einer Blockierungsliste eine große Anzahl von Assets mit zahlreichen XMP Metadaten importiert werden kann, wird die [!DNL Experience Manager] Bei der Implementierung können Stabilitätsprobleme auftreten, z. B. blockierte Beobachtungswarteschlangen.

Durch Filtern von XMP-Metadaten über die Zulassungsliste wird dieses Problem behoben, indem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Filter hinzufügen, der eine Blockierungsliste verwendet.

>[!NOTE]
>
>Die Filterung funktioniert nur für die Eigenschaften, die aus XMP-Quellen in Asset-Binärdateien abgeleitet wurden. Für Eigenschaften, die aus nicht XMP-Quellen abgeleitet werden, wie etwa EXIF- und IPTC-Formate, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. Experience Manager speichert diesen Wert in einem Metadatenfeld namens `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Um die Filterung mithilfe einer Zulassungsliste anzuwenden, wählen Sie **[!UICONTROL Anwenden der Zulassungsliste auf XMP Eigenschaften]** und geben Sie die Eigenschaften an, die in die **[!UICONTROL Zulässige XML-Namen für XMP Filterung]** ankreuzen.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Um blockierte XMP-Eigenschaften nach dem Anwenden der Filterung über eine Zulassungsliste herauszufiltern, geben Sie diese im Feld **[!UICONTROL Blockierte XML-Namen für die XMP-Filterung]** an.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blockierungsliste auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Mit anderen Worten, das Filtern über eine Blockierungsliste ist standardmäßig aktiviert. Um diese Filterung zu deaktivieren, brechen Sie die Auswahl der Option **[!UICONTROL Anwenden der Blockierungsliste auf XMP Eigenschaften]** ab.

1. Speichern Sie die Änderungen.
