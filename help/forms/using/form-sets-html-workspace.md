---
title: Arbeiten mit Formularsätzen in AEM Forms Workspace
description: Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und Endbenutzenden als einzelner Formularsatz bereitgestellt werden. Erfahren Sie, wie Sie in AEM Forms Workspace mit Formularsätzen arbeiten können.
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 76a8f93f-eb8a-4e68-8626-efa6dc67668f
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 100%
---
# Arbeiten mit Formularsätzen in AEM Forms Workspace{#working-with-formsets-in-aem-forms-workspace}

Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die gruppiert sind und Endbenutzenden als einzelner Formularsatz bereitgestellt werden. Wenn der Benutzer einen Formularsatz ausfüllt, werden diese Informationen von einem Formular auf ein anderes übertragen. Der Formularsatz kann dann mit nur einem Klick gesendet werden. Weitere Informationen zu Formularsätzen und dazu, wie sie eingerichtet werden, finden Sie unter [Formularsätze in AEM Forms](../../forms/using/formset-in-aem-forms.md).

AEM Forms Workspace unterstützt Formularsätze. Mit Formularsätzen können mehrere zu einem Dienst oder Prozess gehörige Formulare gruppiert werden, um einen Geschäftsprozess zu automatisieren, und anschließend für die Endbenutzenden bereitgestellt werden. In einem solchen Fall können die Benutzenden den gesamten Formularsatz als einzelnes Formular ausfüllen. Es besteht zudem keine Notwendigkeit, einzelne Formulare oder Prozesse zu archivieren, zu übermitteln oder nachzuverfolgen.

## Ein Formularsatz in der AEM Forms Workspace-App dem Startpunkt zuweisen {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Erstellen Sie den Geschäftsprozess-Workflow in Workbench. Weitere Informationen finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).
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
