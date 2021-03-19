---
title: Löschen von Formularen und zugehörigen Ressourcen
seo-title: Löschen von Formularen und zugehörigen Ressourcen
description: Informationen zum Löschen eines Formular oder Assets in AEM Forms und die Auswirkungen auf referenzierte und verweisende Assets und XFA-Formulare.
seo-description: Informationen zum Löschen eines Formular oder Assets in AEM Forms und die Auswirkungen auf referenzierte und verweisende Assets und XFA-Formulare.
uuid: df522b87-59d8-4678-922d-c9aab82b1381
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: c8519eec-f841-4867-baa9-a9e03042755e
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 94%

---


# Löschen von Formularen und zugehörigen Ressourcen {#deleting-forms-and-related-resources}

Sie können Formulare und Assets löschen, um diese Assets aus dem Repository zu entfernen. Der Löschvorgang funktioniert bei allen Asset-Typen und -Ordnern.

Wenn Sie ein Asset aus der Authoring-Instanz löschen, wird das Asset auch aus der Veröffentlichungsinstanz gelöscht. Der AEM Forms-Server besteht aus der Authoring- und der Veröffentlichungsinstanz. Die Authoring-Instanz dient zum Erstellen und Verwalten von Formular-Assets und Ressourcen. Die Veröffentlichungsinstanz enthält die veröffentlichten Formular-Assets und zugehörigen Ressourcen, die für Endbenutzer verfügbar sind.

## Löschen eines Formulars {#how-to-delete-a-form}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche an, indem Sie auf `https://[hostname]:'port'/aem/forms.html.` zugreifen
1. Navigieren Sie zum Formular, das Sie löschen möchten, und wählen Sie es aus. Klicken Sie in der Symbolleiste auf ![aem6forms_delete2](assets/aem6forms_delete2.png) löschen und bestätigen Sie den Löschvorgang.

   >[!NOTE]
   >
   >Sie können jeweils nur ein Formular löschen. Löschen Sie mehrere Formulare einzeln oder löschen Sie den übergeordneten Ordner.

1. Bevor Sie ein Asset löschen, sucht AEM Forms nach Verweisen und fordert eine explizite Bestätigung an. Klicken Sie auf „Löschen erzwingen“, wenn Sie das Asset unabhängig vom Beziehungsstatus löschen möchten.

   >[!NOTE]
   >
   >Wenn Sie ein Asset löschen, auf das andere Assets verweisen, kann dies zu Funktionsproblemen führen.

   >[!NOTE]
   >
   >Wenn das ausgewählte Asset ein Ordner ist und ein derartiges Asset in der Hierarchie enthält, löschen Sie andere Assets einzeln oder löschen Sie den gesamten Ordner.

## Auswirkungen beim Löschen eines referenzierten XFA-Formulars  {#impact-of-deleting-a-referenced-xfa-form}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Des Weiteren kann eine Vorlage auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Es wird nicht empfohlen, ein XFA-Formular zu löschen, das von einem adaptiven Formular referenziert wird, da das adaptive Formular dadurch beschädigt werden kann. Wenn ein adaptives Formular auf ein XFA-Formular verweist, sind ihre Felder gebunden. Nach dem Löschen des XFA-Formulars kann das adaptive Formular seine Felder nicht mit den XFA-Feldern synchronisieren. Für diese Felder wird eine Fehlermeldung angezeigt. Weitere Informationen zur Auswirkung beim Löschen referenzierter XFA-Formulare und zu beschädigten adaptiven Formularen finden Sie unter [Aktualisieren referenzierter XFA-Formulare](/help/forms/using/get-xdp-pdf-documents-aem.md#p-updating-referenced-xfa-forms-p).

Um ein solches XFA-Formular zu löschen, aktualisieren Sie das adaptive Formular und entfernen Sie die Bindungen mit den XFA-Feldern.
