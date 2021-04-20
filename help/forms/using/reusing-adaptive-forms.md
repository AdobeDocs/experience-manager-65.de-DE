---
title: Wiederverwenden adaptiver Formulare
seo-title: Wiederverwenden adaptiver Formulare
description: Sie können ein vorhandenes adaptives Formular verwenden, um neue adaptive Formulare zu erstellen.
seo-description: Sie können ein vorhandenes adaptives Formular verwenden, um neue adaptive Formulare zu erstellen.
uuid: f1d0fb70-e255-4dd9-8e6d-fd65eaf2e81a
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: ef564750-f107-41cb-887e-fc6d22b7d32e
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 75%

---


# Wiederverwenden adaptiver Formulare {#reusing-adaptive-forms}

## Einführung {#introduction}

Wenn Sie für ein neues adaptives Formular einige der Eigenschaften eines vorhandenen adaptiven Formulars verwenden möchten, können Sie einfach die Kopieren/Einfügen-Funktion verwenden. Darüber hinaus können Sie das neue adaptive Formular in den gewünschten Ordnerpfad einfügen. Alle Metadateneigenschaften werden repliziert und die XFAs und XSDs für XFA- und XSD-basierte adaptive Formulare werden ebenfalls kopiert.

>[!NOTE]
>
>Der Status- und die Prüfungsdetails werden nicht kopiert. Wenn Ihr adaptives Formular zum Beispiel veröffentlicht wird und Sie es dann kopieren, befindet sich das eingefügte adaptive Formular im unveröffentlichten Status. Ebenso wenig wird, wenn ein kopiertes Asset geprüft wird, das eingefügte Asset derselben Prüfung unterzogen.

### Kopieren adaptiver Formulare {#copy-an-adaptive-form}

Kopieren Sie ein adaptives Formular mithilfe eines der folgenden Verfahren:

1. Klicken Sie auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) aus Schnellaktionen kopieren.

   >[!NOTE]
   >
   >Schnelle Aktionen sind die Aktionselemente, die über einer Miniatur angezeigt werden, wenn Sie darauf mit der Maus zeigen.

1. Wählen Sie das adaptive Formular aus. Der Auswahlprozess unterscheidet sich je nach Ansicht.

   Wenn Sie sich in der Ansicht befinden, wechseln Sie zum Auswahlmodus, indem Sie auf das Symbol ![aem6forms_check-circle](assets/aem6forms_check-circle.png) klicken und dann auf alle adaptiven Formulare klicken, die Sie kopieren möchten.

   Wenn Sie sich in der Listenansicht befinden, aktivieren Sie die Kontrollkästchen der gewünschten adaptiven Formulare, um sie auszuwählen.

   >[!NOTE]
   >
   >Alle ausgewählten Assets müssen adaptive Formulare sein, da die Kopieren/Einfügen-Funktion nur bei adaptiven Formularen unterstützt wird. Außerdem müssen sich alle ausgewählten Elemente in demselben Ordner befinden.

   Klicken Sie nach Auswahl der Assets auf das Symbol ![aem6forms_copy](assets/aem6forms_copy.png) in der Symbolleiste, um das ausgewählte adaptive Formular zu kopieren.

### Einfügen adaptiver Formulare {#paste-an-adaptive-form}

Durch Klicken auf die Kopieraktion wird der Auswahlmodus automatisch beendet und das Symbol ![aem6forms_paste](assets/aem6forms_paste.png) wird angezeigt. Wechseln Sie nun zum gewünschten Ordnerpfad und klicken Sie auf das Symbol ![aem6forms_paste](assets/aem6forms_paste.png) einfügen, um das kopierte adaptive Formular einzufügen.

Wenn Sie in denselben Ordner einfügen oder sich im Zielordner eine weitere Datei mit demselben Knotennamen (mit dem sie im CRX-Repository gespeichert ist) befindet, wird am Suffix „1“ angehängt (zum Beispiel wird „myaf“ zu „myaf1“ und wenn sich „myaf1“ in demselben Speicherort befindet, wird „myaf“ zu „myaf2“). Alle anderen Eigenschaften bleiben genauso wie beim ursprünglichen adaptiven Formular.

Nach dem Klicken auf das Symbol ![aem6forms_paste](assets/aem6forms_paste.png) einfügen wird es wieder ausgeblendet. Sie können jeweils nur einmal einfügen. Wenn Sie von demselben Asset erneut eine Kopie erstellen möchten, kopieren Sie es erneut.

### Ändern der Inhalte eines neuen adaptiven Formulars {#change-contents-of-new-adaptive-form}

Wenn Sie eingefügte adaptive Formulare anders als das kopierte Formular gestalten möchten, können ihre Inhalte mithilfe der folgenden Methoden geändert werden:

1. **Ändern der Metadateneigenschaften:**

   Sie können die Metadateneigenschaften des adaptiven Formulars ändern, z. B. Titel und Beschreibung. Weitere Informationen zu Metadateneigenschaften und dazu, wie sie geändert werden können, finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md)

1. **XFA/XSD für XFA/XSD-basiertes adaptives Forms ändern:**

   Sie können die in adaptiven Formularen verwendete XFA/XSD ändern. Informationen zum Ändern dieser adaptiven Formulare finden Sie unter [Verwalten von Formularmetadaten](/help/forms/using/manage-form-metadata.md).

1. **Neu veröffentlichen:**

   Das eingefügte Asset unterscheidet sich vom kopierten. Sie können es als neues Asset veröffentlichen, um es Endbenutzern zur Verfügung zu stellen. Informationen zum Veröffentlichen von Assets finden Sie unter [Veröffentlichen von Formularen und Veröffentlichungen rückgängig machen](/help/forms/using/publishing-unpublishing-forms.md).

