---
title: Das Arbeiten mit Formularsätzen in AEM Forms Workspace
seo-title: Das Arbeiten mit Formularsätzen in AEM Forms Workspace
description: Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Erfahren Sie, wie Sie mit Formularsätzen in AEM Forms Workspace arbeiten können.
seo-description: Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Erfahren Sie, wie Sie mit Formularsätzen in AEM Forms Workspace arbeiten können.
uuid: 1a5f3ce8-1d6a-497e-90d0-49765e40cf3b
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: f550b747-2def-4317-9ef7-dc6c1e7bb404
docset: aem65
exl-id: 76a8f93f-eb8a-4e68-8626-efa6dc67668f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 73%

---

# Das Arbeiten mit Formularsätzen in AEM Forms Workspace{#working-with-formsets-in-aem-forms-workspace}

Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Wenn der Benutzer einen Formularsatz ausfüllt, werden diese Informationen von einem Formular auf ein anderes übertragen. Der Formularsatz kann dann mit nur einem Klick gesendet werden. Weitere Informationen zu Formularsätzen und deren Einrichtung finden Sie unter [Formularsatz in AEM Forms](../../forms/using/formset-in-aem-forms.md).

AEM Forms Workspace unterstützt Formularsätze. Mit Formularsätzen können mehrere Formulare, die zu einem Dienst oder Prozess gehören, gruppiert werden, um einen Geschäftsprozess zu automatisieren und sie den Endbenutzern zu präsentieren. In einem solchen Fall können die Benutzer den gesamten Formularsatz als einzelnes Formular ausfüllen und es besteht keine Notwendigkeit, einzelne Formulare oder Prozesse zu archivieren, zu versenden oder nachzuverfolgen.

## Ein Formularsatz in der AEM Forms Workspace-App dem Startpunkt zuweisen{#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br} 

1. Erstellen Sie den Geschäftsprozess-Arbeitsablauf in Workbench. Weitere Informationen finden Sie unter [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Wählen Sie in den Prozesseigenschaften des Startpunkts **Verwenden Sie ein CRX-Asset** in Präsentation und Daten.

   ![1-3](assets/1-3.png)

1. Klicken Sie neben dem CRX-Asset-Pfad auf ![Durchsuchen](assets/browse.png) (Durchsuchen). Das Dialogfeld „Formularelement“ wird angezeigt.

   ![2-1](assets/2-1.png)

1. Klicken Sie auf die Registerkarte **Formularsatz**, wählen Sie den entsprechenden Formularsatz aus der Liste aus und klicken Sie dann auf **OK**.

1. Stellen Sie die Anwendung bereit, nachdem Sie andere relevante Prozesseigenschaften aktualisiert haben.

## Die Verwendung von Formularsätzen in AEM Forms Workspace {#using-formset-in-nbsp-aem-forms-workspace}

Sobald ein Formularsatz an einen Startpunkt angehängt ist, kann der Startpunkt wie jeder andere Startpunkt auch über den AEM Forms-Arbeitsbereich aufgerufen werden.

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
