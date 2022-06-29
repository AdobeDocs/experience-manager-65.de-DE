---
title: Das Arbeiten mit Formularsätzen in AEM Forms Workspace
seo-title: Working with Formsets in AEM Forms workspace
description: Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Erfahren Sie, wie Sie mit Formularsätzen in AEM Forms Workspace arbeiten können.
seo-description: A formset is a collection of HTML5 forms grouped and presented as a single set of forms to end users. Learn how you can work with formsets in AEM Forms workspace.
uuid: 1a5f3ce8-1d6a-497e-90d0-49765e40cf3b
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: f550b747-2def-4317-9ef7-dc6c1e7bb404
docset: aem65
exl-id: 76a8f93f-eb8a-4e68-8626-efa6dc67668f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '346'
ht-degree: 100%

---

# Das Arbeiten mit Formularsätzen in AEM Forms Workspace{#working-with-formsets-in-aem-forms-workspace}

Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Wenn der Benutzer einen Formularsatz ausfüllt, werden diese Informationen von einem Formular auf ein anderes übertragen. Der Formularsatz kann dann mit nur einem Klick gesendet werden. Weitere Informationen zu Formularsätzen und dazu, wie sie eingerichtet werden, finden Sie unter [Formularsätze in AEM Forms](../../forms/using/formset-in-aem-forms.md).

AEM Forms Workspace unterstützt Formularsätze. Mit Formularsätzen können mehrere Formulare, die zu einem Dienst oder Prozess gehören, gruppiert werden, um einen Geschäftsprozess zu automatisieren und sie den Endbenutzern zu präsentieren. In einem solchen Fall können die Benutzer den gesamten Formularsatz als einzelnes Formular ausfüllen und es besteht keine Notwendigkeit, einzelne Formulare oder Prozesse zu archivieren, zu versenden oder nachzuverfolgen.

## Ein Formularsatz in der AEM Forms Workspace-App dem Startpunkt zuweisen  {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Erstellen Sie den Geschäftsprozess-Arbeitsablauf in Workbench. Weitere Informationen finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).
1. In den Prozesseigenschaften des Startpunkts wählen Sie **Ein CRX-Element verwenden** in „Präsentation und Daten“ aus.

   ![1-3](assets/1-3.png)

1. Klicken Sie ![Durchsuchen](assets/browse.png) (Durchsuchen) neben dem CRX-Elementpfad. Das Dialogfeld „Formularelement“ wird angezeigt.

   ![2-1](assets/2-1.png)

1. Klicken Sie auf die Registerkarte **Formularsatz**, wählen Sie in der Liste den betreffenden Formularsatz aus und klicken Sie dann auf **OK**.

1. Stellen Sie das Programm bereit, nachdem Sie andere relevante Prozesseigenschaften aktualisiert haben. 

## Die Verwendung von Formularsätzen in AEM Forms Workspace {#using-formset-in-nbsp-aem-forms-workspace}

Sobald einem Startpunkt ein Formularsatz zugewiesen wurde, kann der Startpunkt wie jeder andere Startpunkt über AEM Forms Workspace aufgerufen werden.

Folgende Vorgänge von Formularsätzen werden von AEM Forms Workspace unterstützt:

* Als Entwurf speichern
* Sperren
* Abbrechen
* Absenden
* Add Attachments
* Anmerkungen hinzufügen
* Wechseln Sie zwischen den Formularen in einem Formularsatz mit den Schaltflächen „Zurück“ und „Weiter“

![3-1](assets/3-1.png)

>[!NOTE]
>
>Um eine Leistungsverbesserung zu erreichen, sind alle Workspace-Schaltflächen (Zurück, Weiter, Speichern, Senden und weitere) während des Wechselns zwischen Formularen innerhalb eines Formularsatzes deaktiviert, bis das entsprechende Formular vollständig generiert wird.
