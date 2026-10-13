---
title: Herunterladen von XFA- oder PDF-Formularvorlagen
description: Sie können Formulare aus dem Repository in das lokale System exportieren und die heruntergeladenen Formulare in ein neues Repository migrieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
exl-id: 5b7b9816-38c1-4780-b1fc-8184971f3772
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: aa28c6c8-3ede-445b-a351-eeb0c9f9aec4
    internal-label: Interactive Communication
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%
---
# Herunterladen von XFA- oder PDF-Formularvorlagen {#download-an-xfa-or-a-pdf-form-template}

Mit dem Download-Vorgang können Sie, wie der Name schon sagt, Formulare aus dem Repository in das lokale System exportieren. In Kombination mit dem Upload-Vorgang hilft Ihnen dieser Vorgang bei der Migration Ihrer Formulare von einem Repository in ein anderes.

In AEM Forms wird der Download-Vorgang für die folgenden Asset-Typen unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokumente (reduzierte PDF-Dateien)

AEM Forms unterstützt das Herunterladen dieser Formulartypen einzeln oder in einem Ordner, der ein oder mehrere unterstützte Formulare enthält.

Abgesehen von diesen Elementen können Sie den `Resource`-Elementtyp herunterladen, wenn er in einem Ordner vorhanden ist. Diese Funktion wird bereitgestellt, damit Sie neben dem Formular die Ressource herunterladen können, auf die ein XFA-Formular verweist.

## Herunterladen von einem oder mehreren Formularen {#download-one-or-more-forms}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.

1. Navigieren Sie zum Speicherort des Assets, das Sie herunterladen möchten.

1. Wählen Sie das Asset aus. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Herunterladen]** ![aem6forms_download](assets/aem6forms_download.png).

   >[!NOTE]
   >
   >Sie können nur ein Formular zum Herunterladen auswählen. Wenn Sie mehrere Formulare herunterladen möchten, müssen Sie diese als einen Ordner herunterladen.

1. Klicken Sie im eingeblendeten Dialogfeld auf **[!UICONTROL Herunterladen]**.

   AEM Forms generiert eine ZIP-Datei, die die ausgewählte Datei oder den ausgewählten Ordner enthält.

   Wenn Sie einen Ordner herunterladen, werden die unterstützten Assets im Ordner in ihrer vorhandenen Hierarchie heruntergeladen.

   Die ZIP-Datei wird im Ordner `Downloads` auf Ihrem System gespeichert.

## Überlegungen zum Upload-Vorgang {#related-considerations-for-the-upload-operation}

* Sie können die ZIP-Datei in einen beliebigen Speicherort in demselben oder in einem anderen Repository hochladen
* Die Hierarchie der Assets in einem Ordner wird während des Upload-Vorgangs beibehalten
* Änderungen, die vor dem Download an den Metadaten der heruntergeladenen Assets vorgenommen werden, werden beim Hochladen angezeigt.
