---
title: Löschen von Formularen und zugehörigen Ressourcen
description: Informationen zum Löschen eines Formulars oder Assets in AEM Forms und die Auswirkungen auf referenzierte und verweisende Assets und XFA-Formulare.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
exl-id: b31f9f56-dd33-4478-ad34-01ac7d5a1b40
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '369'
ht-degree: 100%

---

# Löschen von Formularen und zugehörigen Ressourcen {#deleting-forms-and-related-resources}

Sie können Formulare und Assets löschen, um diese Assets aus dem Repository zu entfernen. Der Löschvorgang funktioniert bei allen Asset-Typen und -Ordnern.

Wenn Sie ein Asset aus der Autoreninstanz löschen, wird das Asset auch aus der Veröffentlichungsinstanz gelöscht. Der AEM Forms-Server besteht aus der Authoring- und der Veröffentlichungsinstanz. Die Autoreninstanz dient zum Erstellen und Verwalten von Formular-Assets und Ressourcen. Die Veröffentlichungsinstanz enthält die veröffentlichten Formular-Assets und zugehörigen Ressourcen, die für Endbenutzende verfügbar sind.

## Löschen eines Formulars {#how-to-delete-a-form}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche an, indem Sie auf `https://[hostname]:'port'/aem/forms.html.` zugreifen
1. Navigieren Sie zum Formular, das Sie löschen möchten, und wählen Sie es aus. Klicken Sie in der Symbolleiste auf „Löschen“ ![aem6forms_delete2](assets/aem6forms_delete2.png) und bestätigen Sie den Löschvorgang.

   >[!NOTE]
   >
   >Sie können Formulare nur einzeln löschen. Löschen Sie mehrere Formulare einzeln oder löschen Sie den übergeordneten Ordner.

1. Bevor Sie ein Asset löschen, sucht AEM Forms nach Verweisen und fordert eine explizite Bestätigung an. Klicken Sie auf „Löschen erzwingen“, wenn Sie das Asset unabhängig vom Beziehungsstatus löschen möchten.

   >[!NOTE]
   >
   >Wenn Sie ein Asset löschen, auf das andere Assets verweisen, kann dies zu Funktionsproblemen führen.

   >[!NOTE]
   >
   >Wenn das ausgewählte Asset ein Ordner ist und ein derartiges Asset in der Hierarchie enthält, löschen Sie andere Assets einzeln oder löschen Sie den gesamten Ordner.

## Auswirkungen beim Löschen eines referenzierten XFA-Formulars {#impact-of-deleting-a-referenced-xfa-form}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Des Weiteren kann eine Vorlage auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Es wird davon abgeraten, ein XFA-Formular zu löschen, das von einem adaptiven Formular referenziert wird, da das adaptive Formular dadurch beschädigt werden kann. Wenn ein adaptives Formular auf ein XFA-Formular verweist, sind seine Felder gebunden. Nach dem Löschen des XFA-Formulars kann das adaptive Formular seine Felder nicht mit den XFA-Feldern synchronisieren. Für diese Felder wird eine Fehlermeldung angezeigt. Weitere Informationen zur Auswirkung beim Löschen referenzierter XFA-Formulare und zu beschädigten adaptiven Formularen finden Sie unter [Aktualisieren referenzierter XFA-Formulare](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Um ein solches XFA-Formular zu löschen, aktualisieren Sie das adaptive Formular und entfernen Sie die Bindungen mit den XFA-Feldern.
