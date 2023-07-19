---
title: Erzeugen von FPO (For Placement Only)-Ausgabedarstellungen (also nur für die Platzierung) für Adobe InDesign
description: Erzeugen Sie FPO-Ausgabedarstellungen neuer und vorhandener Assets mithilfe des Experience Manager Assets-Workflows und ImageMagick.
contentOwner: Vishabh Gupta
role: Admin
feature: Renditions
exl-id: 1e4ddd73-a31c-4ddd-94eb-1dac6a4835b3
hide: true
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 98%

---

# Erzeugen von FPO (For Placement Only)-Ausgabedarstellungen (also nur für die Platzierung) für Adobe InDesign {#fpo-renditions}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/configure-fpo-renditions.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Wenn großformatige Assets von Experience Manager in Adobe InDesign-Dokumente einfügt werden, muss der Kreativprofi nach dem [Platzieren eines Assets](https://helpx.adobe.com/de/indesign/using/placing-graphics.html) eine beträchtliche Zeit warten. In der Zwischenzeit kann der Benutzer InDesign nicht verwenden. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe ermöglicht die zeitweilige Platzierung kleinformatiger Ausgabedarstellungen in InDesign-Dokumenten. Wenn die endgültige Ausgabe erforderlich ist, z. B. für Druck- und Veröffentlichungs-Workflows, ersetzen die Original-Assets mit voller Auflösung im Hintergrund die temporäre Ausgabedarstellung. Diese asynchrone Aktualisierung im Hintergrund beschleunigt den Designprozess, um die Produktivität zu steigern, und behindert nicht den kreativen Prozess.

Adobe Experience Manager (AEM) bietet Ausgabedarstellungen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Ausgabedarstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf. Wenn für ein Asset keine FPO-Ausgabedarstellung verfügbar ist, verwendet Adobe InDesign stattdessen das Original-Asset. Dieser Fallback-Mechanismus stellt sicher, dass der kreative Workflow ohne Unterbrechung fortgesetzt wird.

## Vorgehensweise zum Erzeugen von FPO-Ausgabedarstellungen {#approach-to-generate-fpo-renditions}

Experience Manager ermöglicht eine Vielzahl von Methoden zur Verarbeitung von Bildern, die zum Erzeugen der FPO-Ausgabedarstellungen verwendet werden können. Die beiden gängigsten Methoden sind die Verwendung von integrierten Experience Manager-Workflows und die Verwendung von ImageMagick. Mit diesen beiden Methoden konfigurieren Sie die Erzeugung von Ausgabedarstellungen für neu hochgeladene Assets und für die in Experience Manager vorhandenen Assets.

Sie können ImageMagick verwenden, um Bilder zu verarbeiten, einschließlich zum Erzeugen von FPO-Ausgabedarstellungen. Solche Ausgabedarstellungen werden heruntergerechnet, d. h. die Pixelabmessungen der Ausgabedarstellung werden proportional reduziert, wenn das Originalbild einen PPI-Wert von mehr als 72 hat. Siehe [Installieren und Konfigurieren von ImageMagick für die Arbeit mit Experience Manager Assets](best-practices-for-imagemagick.md).

|  | Verwenden des integrierten Workflows von Experience Manager | Verwenden des Workflows „ImageMagick“ | Bemerkungen |
|--- |--- |---|--- |
| Für neue Assets | Aktivieren der FPO-Ausgabedarstellung ([Hilfe](#generate-renditions-of-new-assets-using-aem-workflow)) | Hinzufügen der ImageMagick-Befehlszeile im Experience Manager-Workflow ([Hilfe](#generate-renditions-of-new-assets-using-imagemagick)) | Experience Manager führt den Workflow DAM-Update-Assets für jeden Upload aus. |
| Für vorhandene Assets | Aktivieren Sie die FPO-Ausgabedarstellung in einem neuen, dedizierten Experience Manager-Workflow ([Hilfe](#generate-renditions-of-existing-assets-using-aem-workflow)) | Fügen Sie die ImageMagick-Befehlszeile in einen neuen, dedizierten Experience Manager-Workflow hinzu ([Hilfe](#generate-renditions-of-existing-assets-using-imagemagick)) | FPO-Ausgabedarstellungen der vorhandenen Assets können bei Bedarf oder massenweise erstellt werden. |

>[!CAUTION]
>
>Erstellen Sie die Workflows zur Erstellung von Ausgabedarstellungen, indem Sie eine Kopie der Standard-Workflows ändern. Damit wird verhindert, dass Ihre Änderungen überschrieben werden, wenn Experience Manager aktualisiert wird, z. B. durch das Installieren eines neuen Service Packs.

## Erzeugen von Ausgabedarstellungen neuer Assets mit dem Experience Manager-Workflow {#generate-renditions-of-new-assets-using-aem-workflow}

Im Folgenden werden die Schritte zum Konfigurieren des DAM Update Asset-Workflow-Modells beschrieben, um das Erzeugen von Ausgabedarstellungen zu aktivieren:

1. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**. Wählen sie das Modell **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Wählen Sie den Schritt **[!UICONTROL Miniaturansichten verabeiten]** aus und klicken Sie auf **[!UICONTROL Konfigurieren]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL FPO-Ausgabedarstellung]**. Wählen sie **[!UICONTROL FPO-Ausgabedarstellung aktivieren]** aus.

   ![fpo_rendition_damupdateasset_model](assets/fpo_rendition_damupdateasset_model.png)

1. Passen Sie die **[!UICONTROL Qualität]** an und fügen Sie Werte für die **[!UICONTROL Formatliste]** hinzu oder ändern Sie sie nach Bedarf. Standardmäßig ist die Liste der MIME-Typen für das Erzeugen der FPO-Ausgabedarstellungen pjpeg, jpeg, jpg, gif, png, x-png und tiff. Klicken Sie auf **[!UICONTROL Fertig]**.

   >[!NOTE]
   >
   >Das Erzeugen von Ausgabedarstellungen wird für die Dateitypen JPEG, GIF, PNG, TIFF, PSD und BMP unterstützt.

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.

>[!NOTE]
>
>Bei Bildern, die auf einer Seite größer als 1280 Pixel sind, werden die Pixelmaße in der FPO-Ausgabedarstellung nicht beibehalten.

## Erzeugen von Ausgabedarstellungen neuer Assets mit ImageMagick {#generate-renditions-of-new-assets-using-imagemagick}

In Experience Manager wird der Workflow „DAM Update Asset“ ausgeführt, wenn ein neues Asset hochgeladen wird. Um ImageMagick für die Verarbeitung von Ausgabedarstellungen neu hochgeladener Assets zu verwenden, fügen Sie dem Workflow-Modell einen neuen Befehl hinzu.

1. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Wählen sie das Modell **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Klicken Sie auf **[!UICONTROL Seitliches Bedienfeld ein/aus]** in der oberen linken Ecke und suchen Sie nach dem Schritt „Befehlszeile“.

1. Ziehen Sie den Schritt **[!UICONTROL Befehlszeile]** und fügen Sie ihn vor dem Schritt **[!UICONTROL Miniaturansichten verarbeiten]** ein.

1. Wählen Sie den Schritt **[!UICONTROL Befehlszeile]** aus und klicken sie auf **[!UICONTROL Konfigurieren]**.

1. Fügen Sie die gewünschten Informationen als benutzerdefinierte **[!UICONTROL Titel]** und **[!UICONTROL Beschreibung]** hinzu. Beispielsweise „FPO-Ausgabedarstellung (unterstützt von ImageMagick)“.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Argumente]** die entsprechenden **[!UICONTROL Mime Typen]** hinzu, um eine Liste der Dateiformate zu erstellen, für die der Befehl gilt.

   ![imagemagick-mimetype](assets/imagemagick-mimetype.png)

1. Fügen Sie auf der Registerkarte **[!UICONTROL Argumente]** im Abschnitt **[!UICONTROL Befehle]** einen entsprechenden ImageMagick-Befehl hinzu, um FPO-Ausgabedarstellungen zu erzeugen.

   Nachfolgend finden Sie einen Beispielbefehl, der FPO-Ausgabedarstellungen im JPEG-Format erzeugt, mit einer Qualitätseinstellung von 10 % auf 72 PPI heruntergerechnet, und der mehrschichtige Adobe Photoshop-Dateien durch Reduzierung der Ausgabe verarbeitet:

   `convert -quality 10% -units PixelsPerInch ${filename} -resample 72 -flatten cq5dam.fpo.jpeg`

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.

Detaillierte Informationen zu den Befehlszeilenfunktionen von ImageMagick finden Sie unter [https://imagemagick.org](https://imagemagick.org).

## Erzeugen von Ausgabeformaten vorhandener Assets mithilfe des Experience Manager-Workflows {#generate-renditions-of-existing-assets-using-aem-workflow}

Um mithilfe des Experience Manager-Workflows FPO-Ausgabedarstellungen der vorhandenen Assets zu generieren, erstellen Sie ein dediziertes Workflow-Modell, das die integrierte FPO-Ausgabedarstellungsoption verwendet.

1. Klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Um ein Modell zu erstellen, klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Modell erstellen]**.

1. Fügen Sie einen aussagekräftigen **[!UICONTROL Titel]** und **[!UICONTROL Namen]** hinzu.

1. Wählen Sie das Modell aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. Klicken Sie auf **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Eigenschaften öffnen]**, und wählen Sie dann **[!UICONTROL Übergangs-Workflow]** aus. Dies verbessert die Skalierbarkeit und Leistung.

1. Klicken Sie auf **[!UICONTROL Speichern]** und **[!UICONTROL schließen]**.

1. Klicken Sie auf **[!UICONTROL Seitliches Bedienfeld ein/aus]** in der oberen linken Ecke und suchen Sie nach dem Schritt „Miniaturansichten verarbeiten“.

1. Wählen Sie **[!UICONTROL Miniaturansichten verarbeiten]** aus und klicken Sie auf **[!UICONTROL Konfigurieren]**. Befolgen Sie die [Konfiguration zum Erzeugen von Ausgabedarstellungen für neue Assets mithilfe des Experience Manager-Workflows](#generate-renditions-of-new-assets-using-aem-workflow).

1. Um die Änderungen zu aktivieren, klicken Sie auf **[!UICONTROL Synchronisieren]**.


## Erzeugen von Ausgabedarstellungen vorhandener Assets mit ImageMagick {#generate-renditions-of-existing-assets-using-imagemagick}

Um mithilfe der Bildmagick-Verarbeitungsfunktionen FPO-Ausgabedarstellungen von vorhandenen Assets zu erzeugen, erstellen Sie ein dediziertes Workflow-Modell, das dazu die ImageMagick-Befehlszeile verwendet.

1. Führen Sie die Schritte 1 bis 3 aus dem Abschnitt [Konfiguration zum Erzeugen von Ausgabedarstellungen vorhandener Assets mit dem Experience Manager-Workflow](#generate-renditions-of-existing-assets-using-aem-workflow) aus.

1. Führen Sie die Schritte 4 bis 8 des Abschnitts [Konfiguration zur Erzeugung von Ausgabedarstellungen neuer Assets mit ImageMagick](#generate-renditions-of-new-assets-using-imagemagick) aus.


## Anzeigen von FPO-Ausgabedarstellungen {#view-fpo-renditions}

Sie können die erzeugten FPO-Ausgabedarstellungen überprüfen, nachdem der Workflow abgeschlossen ist. Klicken Sie in der Experience Manager Assets-Benutzeroberfläche auf das Asset, um eine große Vorschau zu öffnen. Öffnen Sie die linke Leiste und wählen Sie Ausgabedarstellungen aus. Alternativ können Sie den Tastaturbefehl `Alt + 3` verwenden, wenn die Vorschau geöffnet ist.

Klicken Sie auf **[!UICONTROL FPO-Ausgabedarstellung]**, um die Vorschau zu laden. Optional können Sie mit der rechten Maustaste auf die Ausgabedarstellung klicken und sie in Ihrem Dateisystem speichern.

![rendition_list](assets/rendition_list.png)


## Tipps und Einschränkungen {#tips-limitations}

* Um die auf ImageMagick basierende Konfiguration zu verwenden, installieren Sie ImageMagick auf demselben Computer wie Experience Manager.
* Um FPO-Ausgabedarstellungen vieler Assets oder des gesamten Repositorys zu erzeugen, sollten Sie die Workflows während einer Zeit mit geringem Traffic planen und ausführen. Das Erzeugen von FPO-Ausgabedarstellungen für eine große Anzahl von Assets ist eine ressourcenintensive Tätigkeit, und die Experience Manager-Server müssen über ausreichend Rechenleistung und Speicher verfügen.
* Informationen zur Leistung und Skalierbarkeit finden Sie unter [Optimieren von ImageMagick](performance-tuning-guidelines.md).
* Informationen zur allgemeinen Befehlszeilenverarbeitung von Assets finden Sie unter [Befehlszeilen-Handler zur Verarbeitung von Assets](media-handlers.md).
