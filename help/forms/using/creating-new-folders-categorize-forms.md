---
title: Erstellen neuer Ordner für die Formularkategorisierung
description: Verwenden Sie Ordner zum Organisieren von Formularvorlagen, PDF, Ressourcen und adaptiven Formularen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin
exl-id: f8af1ac3-6a95-4f91-8979-6b41a7e02ca4
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 65%

---

# Erstellen neuer Ordner für die Formularkategorisierung {#create-new-folders-to-categorize-forms}

Sie können Ihre Assets mithilfe von Ordnern besser organisieren. Da AEM Forms verschiedene Asset-Typen unterstützt - Formularvorlagen, PDF, Dokumente, Ressourcen und adaptive Formulare mit verschiedenen Metadaten - können Sie Ordner verwenden, um Formulare anhand der gewünschten Kriterien zu kategorisieren.

In AEM Forms können Sie den Titel eines Ordners ändern. Der Titel ist nicht mit dem Namen des Knotens identisch, unter dem der Ordner im Repository gespeichert ist. Stattdessen wird der Titel als Metadaten für den Ordner beibehalten. Wenn Sie den Titel eines Ordners ändern, hat dies keine Auswirkungen auf den Pfad eines Assets, das im Ordner vorhanden ist.

## Erstellen von Ordnern {#create-a-folder}

Sie können einen Ordner in AEM Forms auf eine der folgenden Arten erstellen:

* Laden Sie eine ZIP-Datei hoch, die Assets in der gewünschten Ordnerstruktur enthält (siehe [Einbinden von XDP- und PDF-Dokumenten in AEM Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Leeren Ordner erstellen

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.
1. Navigieren Sie zu dem Speicherort, unter dem Sie einen Ordner erstellen möchten.
1. Klicken Sie auf das Symbol ![aem6forms_add](assets/aem6forms_add.png) in der Symbolleiste und wählen Sie **[!UICONTROL Ordner erstellen]** aus.

1. Geben Sie die folgenden Details ein:

   * **Titel**: Anzeigename für den Ordner
   * **Name**: *(obligatorisch)* Der Knotenname, unter dem Sie den Ordner im Repository speichern möchten

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch mit dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Alle anderen Sonderzeichen, die im Titel eingegeben werden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können den vorgeschlagenen Namen verwenden oder ihn weiter bearbeiten.

1. Klicken Sie auf **[!UICONTROL Senden].**

   Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

   Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt das Senden mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie die Maus über das Fehlersymbol ![aem6forms_error_alert](assets/aem6forms_error_alert.png) bewegen, das neben dem Namensfeld angezeigt wird.

### Bearbeiten des Ordnertitels {#edit-the-folder-title-br}

1. Wählen Sie den Ordner aus, dessen Namen Sie bearbeiten möchten.
1. Klicken Sie auf das Symbol ![aem6forms_edit](assets/aem6forms_edit.png) in der Symbolleiste.
1. Geben Sie den neuen Titel ein. Das Textfeld wird vorab mit dem aktuellen Wert des Ordnertitels gefüllt. Sie können diesen in einen neuen Wert ändern.
1. Klicken Sie auf **[!UICONTROL Senden].**
