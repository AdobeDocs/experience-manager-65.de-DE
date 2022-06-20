---
title: Erzeugen von FPO (For Placement Only)-Ausgabedarstellungen (also nur für die Platzierung) für Adobe InDesign
description: Erzeugen Sie FPO-Ausgabedarstellungen neuer und vorhandener Assets mithilfe des Experience Manager Assets-Workflows und ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 1e4ddd73-a31c-4ddd-94eb-1dac6a4835b3
source-git-commit: 9d5440747428830a3aae732bec47d42375777efd
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 24%

---

# Erzeugen von FPO (For Placement Only)-Ausgabedarstellungen (also nur für die Platzierung) für Adobe InDesign {#fpo-renditions}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/configure-fpo-renditions.html?lang=en) |
| AEM 6.5 | Dieser Artikel |

Wenn großformatige Assets von Experience Manager in Adobe InDesign-Dokumente einfügt werden, muss der Kreativprofi nach dem [Platzieren eines Assets](https://helpx.adobe.com/de/indesign/using/placing-graphics.html) eine beträchtliche Zeit warten. In der Zwischenzeit kann der Benutzer InDesign nicht verwenden. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe ermöglicht die zeitweilige Platzierung kleinformatiger Ausgabedarstellungen in InDesign-Dokumenten. Wenn die endgültige Ausgabe erforderlich ist, z. B. für Druck- und Veröffentlichungs-Workflows, ersetzen die Original-Assets mit voller Auflösung im Hintergrund die temporäre Ausgabedarstellung. Diese asynchrone Aktualisierung im Hintergrund beschleunigt den Designprozess, um die Produktivität zu steigern, und behindert nicht den kreativen Prozess.

Adobe Experience Manager (AEM) bietet Ausgabedarstellungen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Ausgabedarstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf. Wenn für ein Asset keine FPO-Ausgabedarstellung verfügbar ist, verwendet Adobe InDesign stattdessen das Original-Asset. Dieser Fallback-Mechanismus stellt sicher, dass der kreative Workflow ohne Unterbrechung fortgesetzt wird.

## Vorgehensweise zum Generieren von FPO-Ausgabeformaten {#approach-to-generate-fpo-renditions}

Experience Manager ermöglicht eine Vielzahl von Methoden zur Verarbeitung von Bildern, die zum Generieren der FPO-Ausgabedarstellungen verwendet werden können. Die beiden gängigsten Methoden sind die Verwendung von integrierten Experience Manager-Workflows und die Verwendung von ImageMagick. Mit diesen beiden Methoden konfigurieren Sie die Ausgabegenerierung neu hochgeladener Assets und der in Experience Manager vorhandenen Assets.

Sie können ImageMagick verwenden, um Bilder zu verarbeiten, einschließlich zum Generieren von FPO-Ausgabedarstellungen. Solche Ausgabedarstellungen werden heruntergesampelt, d. h. die Pixelabmessungen der Ausgabedarstellung werden proportional reduziert, wenn das Originalbild PPI größer als 72 hat. Siehe [Installieren und Konfigurieren von ImageMagick für die Verwendung mit Experience Manager Assets](best-practices-for-imagemagick.md).

|  | Verwenden des integrierten Workflows von Experience Manager | Workflow &quot;ImageMagick&quot;verwenden | Bemerkungen |
|--- |--- |---|--- |
| Für neue Assets | FPO-Ausgabe aktivieren ([help](#generate-renditions-of-new-assets-using-aem-workflow)) | Hinzufügen der ImageMagick-Befehlszeile im Experience Manager-Workflow ([help](#generate-renditions-of-new-assets-using-imagemagick)) | Experience Manager führt den Workflow DAM-Update-Assets für jeden Upload aus. |
| Für vorhandene Assets | Aktivieren Sie die FPO-Ausgabedarstellung in einem neuen, dedizierten Experience Manager-Workflow ([help](#generate-renditions-of-existing-assets-using-aem-workflow)) | Fügen Sie die ImageMagick-Befehlszeile in einem neuen, dedizierten Experience Manager-Workflow hinzu ([help](#generate-renditions-of-existing-assets-using-imagemagick)) | FPO-Ausgabedarstellungen der vorhandenen Assets können bei Bedarf oder stapelweise erstellt werden. |

>[!CAUTION]
>
>Erstellen Sie die Workflows, um Ausgabedarstellungen zu generieren, indem Sie eine Kopie der Standard-Workflows ändern. Dadurch wird verhindert, dass Ihre Änderungen überschrieben werden, wenn der Experience Manager aktualisiert wird, beispielsweise durch die Installation eines neuen Service Packs.

## Generieren von Ausgabeformaten neuer Assets mit dem Experience Manager-Workflow {#generate-renditions-of-new-assets-using-aem-workflow}

Im Folgenden werden die Schritte zum Konfigurieren des Workflow-Modells DAM Update Asset beschrieben, um die Ausgabegenerierung zu aktivieren:

1. Klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**. Auswählen **[!UICONTROL DAM-Update-Asset]** Modell und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Auswählen **[!UICONTROL Prozessminiaturansichten]** Schritt und Klicken **[!UICONTROL Konfigurieren]**.

1. Klicken **[!UICONTROL FPO-Ausgabe]** Registerkarte. Auswählen **[!UICONTROL Erstellen von FPO-Ausgabedarstellungen aktivieren]**.

   ![fpo_rendition_damupdateasset_model](assets/fpo_rendition_damupdateasset_model.png)

1. Passen Sie die **[!UICONTROL Qualität]** und hinzufügen oder ändern **[!UICONTROL Formatliste]** Werte nach Bedarf. Standardmäßig ist die Liste der MIME-Typen, die die FPO-Ausgabedarstellung generieren sollen, pjpeg, jpeg, jpg, gif, png, x-png und tiff. Klicken Sie auf **[!UICONTROL Fertig]**.

   >[!NOTE]
   >
   >Die Generierung von Ausgabedarstellungen wird für Dateitypen JPEG, GIF, PNG, TIFF, PSD und BMP unterstützt.

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.

>[!NOTE]
>
>Bei Bildern, die auf einer Seite größer als 1280 Pixel sind, werden die Pixelabmessungen in der FPO-Ausgabedarstellung nicht beibehalten.

## Generieren von Ausgabeformaten neuer Assets mit ImageMagick {#generate-renditions-of-new-assets-using-imagemagick}

In Experience Manager wird der Workflow DAM-Update-Asset ausgeführt, wenn ein neues Asset hochgeladen wird. Um ImageMagick zur Verarbeitung von Ausgabedarstellungen neu hochgeladener Assets zu verwenden, fügen Sie dem Workflow-Modell einen neuen Befehl hinzu.

1. Klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Auswählen **[!UICONTROL DAM-Update-Asset]** Modell und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Klicken **[!UICONTROL Seitliches Bedienfeld ein/aus]** in der oberen linken Ecke und suchen Sie nach Befehlszeilenschritt.

1. Ziehen Sie die **[!UICONTROL Befehlszeile]** und fügen Sie ihn vor dem **[!UICONTROL Prozessminiaturansichten]** Schritt.

1. Auswählen **[!UICONTROL Befehlszeile]** Schritt und Klicken **[!UICONTROL Konfigurieren]**.

1. Fügen Sie die gewünschten Informationen als benutzerdefiniert hinzu **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]**. Beispielsweise FPO-Ausgabedarstellung (unterstützt von ImageMagick).

1. Im **[!UICONTROL Argumente]** Registerkarte, relevante hinzufügen **[!UICONTROL MIME-Typen]** um eine Liste der Dateiformate anzugeben, für die der Befehl gilt.

   ![imagemagick-mimetype](assets/imagemagick-mimetype.png)

1. Im **[!UICONTROL Argumente]** im **[!UICONTROL Befehle]** Fügen Sie einen relevanten ImageMagick-Befehl hinzu, um FPO-Ausgabedarstellungen zu generieren.

   Nachfolgend finden Sie ein Beispielbefehl, der FPO-Ausgabedarstellungen im JPEG-Format generiert, auf 72 PPI heruntergesampelt und bei einer Qualitätseinstellung von 10 % verarbeitet und mehrschichtige Adobe Photoshop-Dateien verarbeitet, indem die Ausgabe reduziert wird:

   `convert -quality 10% -units PixelsPerInch ${filename} -resample 72 -flatten cq5dam.fpo.jpeg`

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.

Detaillierte Informationen zu den Befehlszeilenfunktionen von ImageMagick finden Sie unter [https://imagemagick.org](https://imagemagick.org).

## Generieren von Ausgabeformaten vorhandener Assets mithilfe des Experience Manager-Workflows {#generate-renditions-of-existing-assets-using-aem-workflow}

Um mithilfe des Experience Manager-Workflows die FPO-Ausgabe der vorhandenen Assets zu generieren, erstellen Sie ein dediziertes Workflow-Modell, das die integrierte FPO-Ausgabedarstellungsoption verwendet.

1. Klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Um ein Modell zu erstellen, klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Modell erstellen]**.

1. Fügen Sie eine aussagekräftige **[!UICONTROL Titel]** und **[!UICONTROL Name]**.

1. Wählen Sie das Modell aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. Klicken **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Eigenschaften öffnen]** und wählen Sie **[!UICONTROL Übergangs-Workflow]**. Dies verbessert die Skalierbarkeit und Leistung.

1. Klicken Sie auf ******[!UICONTROL Speichern und schließen]**.

1. Klicken **[!UICONTROL Seitliches Bedienfeld ein/aus]** in der oberen linken Ecke und suchen Sie nach Schritt &quot;Miniaturansichten verarbeiten&quot;.

1. Auswählen **[!UICONTROL Prozessminiaturansichten]** und klicken Sie auf **[!UICONTROL Konfigurieren]**. Befolgen Sie die [Konfiguration zum Generieren der Ausgabedarstellung für neue Assets mithilfe des Experience Manager-Workflows](#generate-renditions-of-new-assets-using-aem-workflow).

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.


## Generieren von Ausgabeformaten vorhandener Assets mit ImageMagick {#generate-renditions-of-existing-assets-using-imagemagick}

Um mithilfe der Bildmagick-Verarbeitungsfunktionen die FPO-Ausgabe der vorhandenen Assets zu generieren, erstellen Sie ein dediziertes Workflow-Modell, das dazu die ImageMagick-Befehlszeile verwendet.

1. Schritt 1 bis Schritt 3 von [Konfiguration zum Generieren der Ausgabedarstellung vorhandener Assets mithilfe des Experience Manager-Workflows](#generate-renditions-of-existing-assets-using-aem-workflow) Abschnitt.

1. Schritt 4 bis Schritt 8 von [Konfiguration zum Generieren der Ausgabedarstellung neuer Assets mit ImageMagick](#generate-renditions-of-new-assets-using-imagemagick) Abschnitt.


## Anzeigen von FPO-Ausgabedarstellungen {#view-fpo-renditions}

Sie können die erzeugten FPO-Ausgabedarstellungen überprüfen, nachdem der Workflow abgeschlossen ist. Klicken Sie in der Experience Manager Assets-Benutzeroberfläche auf das Asset, um eine große Vorschau zu öffnen. Öffnen Sie die linke Leiste und wählen Sie Ausgabedarstellungen aus. Alternativ können Sie den Tastaturbefehl `Alt + 3` verwenden, wenn die Vorschau geöffnet ist.

Klicken Sie auf **[!UICONTROL FPO-Ausgabedarstellung]**, um die Vorschau zu laden. Optional können Sie mit der rechten Maustaste auf die Ausgabedarstellung klicken und sie in Ihrem Dateisystem speichern.

![rendition_list](assets/rendition_list.png)


## Tipps und Einschränkungen {#tips-limitations}

* Um die ImageMagick-basierte Konfiguration zu verwenden, installieren Sie ImageMagick auf demselben Computer wie Experience Manager.
* Um FPO-Ausgabedarstellungen vieler Assets oder des gesamten Repositorys zu generieren, planen und führen Sie die Workflows während der Dauer des niedrigen Traffic aus. Die Generierung von FPO-Ausgabedarstellungen für eine große Anzahl von Assets ist eine ressourcenintensive Aktivität und die Experience Manager-Server müssen über ausreichend Verarbeitungsleistung und Arbeitsspeicher verfügen.
* Informationen zur Leistung und Skalierbarkeit finden Sie unter [ImageMagick optimieren](performance-tuning-guidelines.md).
* Informationen zur allgemeinen Befehlszeilenverarbeitung von Assets finden Sie unter [Befehlszeilen-Handler zur Verarbeitung von Assets](media-handlers.md).
