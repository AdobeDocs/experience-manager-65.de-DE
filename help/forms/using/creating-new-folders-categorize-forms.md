---
title: Erstellen neuer Ordner für die Formularkategorisierung
seo-title: Erstellen neuer Ordner für die Formularkategorisierung
description: Verwenden Sie Ordner, um die Formularvorlagen, PDFs, Ressourcen und adaptiven Formulare zu organisieren.
seo-description: Verwenden Sie Ordner, um die Formularvorlagen, PDFs, Ressourcen und adaptiven Formulare zu organisieren.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Administrator
exl-id: f8af1ac3-6a95-4f91-8979-6b41a7e02ca4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 81%

---

# Erstellen neuer Ordner für die Formularkategorisierung {#create-new-folders-to-categorize-forms}

Sie können Ihre Assets mithilfe von Ordnern besser organisieren. Da AEM Forms mehrere Asset-Typen (Formularvorlagen, PDFs, Dokumente, Ressourcen und adaptive Formulare mit verschiedenen Metadaten) unterstützt, können Sie Ordner verwenden, um Formulare basierend auf den gewünschten Kriterien zu kategorisieren.

In AEM Forms können Sie den Titel eines Ordners ändern. Der Titel ist nicht mit den Namen des Knotens identisch, unter dem der Ordner im Repository gespeichert ist. Stattdessen wird der Titel als Metadaten für den Ordner beibehalten. Wenn Sie den Titel eines Ordners ändern, ist der Pfad der Assets, die sich im Ordner befinden, davon nicht betroffen.

## Erstellen von Ordnern {#create-a-folder}

Sie können einen Ordner in AEM Forms auf eine der folgenden Arten erstellen:

* Laden Sie eine ZIP-Datei hoch, die Assets in der gewünschten Ordnerstruktur enthält (siehe [Einbinden von XDP- und PDF-Dokumenten in AEF Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Erstellen eines neuen leeren Ordners

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.
1. Navigieren Sie zum Speicherort, unter dem Sie einen Ordner erstellen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol ![aem6forms_add](assets/aem6forms_add.png) und wählen Sie dann **[!UICONTROL Ordner erstellen]** aus.

1. Geben Sie die folgenden Details ein:

   * **Titel:** Anzeigename für den Ordner
   * **Name:***(Obligatorisch)* Der Knotenname, unter dem Sie den Ordner im Repository speichern möchten

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch aus dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Andere Sonderzeichen, die in den Titel eingegeben wurden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können mit dem vorgeschlagenen Namen fortfahren oder diesen weiter bearbeiten.

1. Klicken Sie auf **[!UICONTROL Übermitteln].**

   Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

   Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt die Übermittlung mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie den Mauszeiger über das Fehlersymbol ![aem6forms_error_alert](assets/aem6forms_error_alert.png) bewegen, das neben dem Namensfeld angezeigt wird.

### Bearbeiten des Ordnertitels {#edit-the-folder-title-br}

1. Wählen Sie den Ordner aus, dessen Namen Sie bearbeiten möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol ![aem6forms_edit](assets/aem6forms_edit.png) Bearbeiten .
1. Geben Sie den neuen Titel ein. Das Textfeld wird vorab mit dem aktuellen Wert des Ordnertitels gefüllt. Sie können diesen in einen neuen Wert ändern.
1. Klicken Sie auf **[!UICONTROL Übermitteln].**
