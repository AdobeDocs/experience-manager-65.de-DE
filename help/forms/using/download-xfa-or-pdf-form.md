---
title: Herunterladen von XFA- oder PDF-Formularvorlagen
seo-title: Herunterladen von XFA- oder PDF-Formularvorlagen
description: Sie können aus dem Repository Formulare in das lokale System exportieren und die heruntergeladenen Formulare in ein neues Repository migrieren.
seo-description: Sie können aus dem Repository Formulare in das lokale System exportieren und die heruntergeladenen Formulare in ein neues Repository migrieren.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 89%

---


# Herunterladen von XFA- oder PDF-Formularvorlagen {#download-an-xfa-or-a-pdf-form-template}

Wie der Name schon sagt, können Sie beim Download-Vorgang Formulare aus dem Repository in das lokale System exportieren. In Verbindung mit dem Upload-Vorgang können Sie hierbei Ihre Formulare aus einem Repository in ein anderes migrieren.

In AEM Forms wird der Download-Vorgang für die folgenden Assettypen unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokumente (reduzierte PDF-Dateien)

AEM Forms unterstützt den Download dieser Formulartypen – einzeln oder in einem Ordner mit mindestens einem unterstützten Formular.

Neben diesen Assets können Sie den Asset-Typ `Resource` herunterladen, wenn er in einem Ordner vorhanden ist. Diese Funktion wird bereitgestellt, damit Sie neben dem Formular die Ressource herunterladen können, auf die ein XFA-Formular verweist.

## Herunterladen von einem oder mehreren Formularen {#download-one-or-more-forms}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.

1. Navigieren Sie zum Speicherort des Assets, das Sie herunterladen möchten.

1. Wählen Sie das Asset aus. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Download]** ![aem6forms_download](assets/aem6forms_download.png).

   >[!NOTE]
   >
   >Sie können nur ein Formular zum Herunterladen auswählen. Wenn Sie mehrere Formulare herunterladen möchten, müssen Sie sie als Ordner herunterladen.

1. Klicken Sie im eingeblendeten Dialogfeld auf **[!UICONTROL Herunterladen]**.

   AEM Forms generiert eine ZIP-Datei, die die ausgewählte Datei bzw. den ausgewählten Ordner enthält.

   Wenn Sie einen Ordner herunterladen, werden die unterstützten Elemente innerhalb des Ordners in der vorhandenen Hierarchie heruntergeladen.

   Die ZIP-Datei wird im Ordner `Downloads` auf Ihrem System gespeichert.

## Überlegungen zum Upload-Vorgang {#related-considerations-for-the-upload-operation}

* Sie können die ZIP-Datei in einen beliebigen Speicherort in demselben oder in einem anderen Repository hochladen.
* Die Hierarchie der Assets in einem Ordner wird während des Upload-Vorgangs beibehalten.
* Änderungen, die vor dem Download an den Metadaten der heruntergeladenen Assets vorgenommen werden, werden beim Hochladen angezeigt. 

