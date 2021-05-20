---
title: Freigegebene Warteschlangen konfigurieren
seo-title: Freigegebene Warteschlangen konfigurieren
description: Mithilfe von freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Erfahren Sie, wie Sie geteilte Warteschlangen konfigurieren.
seo-description: Mithilfe von freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Erfahren Sie, wie Sie geteilte Warteschlangen konfigurieren.
uuid: 69ab611d-334b-40a5-bd2d-533d4cb25eda
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fc403a60-b635-4334-9bf8-2f3d2036b2f3
exl-id: 5f4467c1-0f3f-4dc6-9bd5-98259f327295
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 97%

---

# Freigegebene Warteschlangen konfigurieren{#configuring-shared-queues}

Mithilfe von freigegebenen Warteschlangen können Sie Benutzerwarteschlangen effektiv konfigurieren und verwalten. Eine Benutzerwarteschlange sind alle einem Benutzer zugeordneten Aufgaben. Weitere Informationen finden Sie unter [Aufgabenlisten](https://help.adobe.com/en_US/livecycle/11.0/WorkspaceHelp/WS92d06802c76abadb-2b6ab502126beb6ba2f-7ffc.2.html). Sie können Benutzerwarteschlangen entsprechend den Anforderungen Ihres Unternehmens zuordnen, die Zuordnungen aufheben oder erneut zuordnen. Sie können freigegebene Warteschlangen auf zwei Arten verwalten:

**Zugriff auf einen Benutzer verwalten**

Sie können Zugriff auf eine ausgewählte Benutzerwarteschlange mit dieser Option verwalten.

**Zugriff von einem Benutzer verwalten**

Sie können freigegebene Warteschlangen, die einem ausgewählten Benutzer zugewiesen sind, mit dieser Option verwalten.

## Zugriff auf ausgewählte Benutzerwarteschlangen verwalten {#managing-access-to-a-selected-user-queue}

Mit der Funktion „Zugriff auf einen Benutzer verwalten“ können Sie den Zugriff auf eine ausgewählte Benutzerwarteschlange verwalten. Sie können Zugriff auf eine ausgewählte Benutzerwarteschlange für andere Benutzer in Ihrem Unternehmen gewähren oder sperren. Z. B. Kara Bowman ist außer Haus. Mit der Funktion „Zugriff auf einen Benutzer verwalten“ kann ihre Warteschlange zur Fertigstellung für Akira Tanaka und John Jacobs freigegeben werden. Wenn sich Kara Bowman später wieder im Büro befindet, können Sie den Zugriff auf ihre Warteschlage für Akira Tanaka und John Jacobs wieder sperren.

Nachdem diese Aufgaben freigegeben wurden, können Sie vom Benutzer, der Zugriff auf die Warteschlange hat, mithilfe von Workspace fertiggestellt werden.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

### Zugriff auf ausgewählte Benutzerwarteschlangen konfigurieren  {#configuring-access-to-a-selected-user-queue}

1. Melden Sie sich bei Administration Console mithilfe eines Administratorkontos an.
1. Wählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte „Zugriff auf einen Benutzer verwalten“ den Benutzer aus, dessen Warteschlange sie freigeben möchten. Das untere rechte Fenster zeigt die Liste von Benutzern an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Wählen Sie im unteren linken Fenster den Benutzer aus. Klicken Sie auf Freigeben.
1. Klicken Sie dann auf „Speichern“.

### Zugriff auf ausgewählte Benutzerwarteschlangen sperren  {#revoking-access-to-a-selected-user-queue}

1. Melden Sie sich bei Administration Console mithilfe eines Administratorkontos an.
1. Wählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte „Zugriff auf einen Benutzer verwalten“ den Benutzer aus, dessen Warteschlange sie verwalten möchten.
1. Das untere rechte Fenster zeigt die Liste von Benutzern an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben. Wählen Sie den Benutzer und klicken Sie auf „Sperren“.
1. Klicken Sie dann auf „Speichern“.

## Einem Benutzer zugewiesene Warteschlangen verwalten  {#managing-queues-assigned-to-a-user}

Mit der Funktion „Zugriff von einem Benutzer verwalten“ können Sie Warteschlangen verwalten, die einem ausgewählten Benutzer zugewiesen sind. Sie können Zugriff auf Benutzerwarteschlagen für einen ausgewählten Benutzer einzeln gewähren oder sperren. Z. B., wenn Sie Kara Bowman die Benutzerwarteschlangen von Akira Tanaka und John Jacobs zuweisen möchten. Mit der Funktion „Zugriff von einem Benutzer verwalten“ können Sie nach Kara Bowman suchen und Zugriff auf Aufgaben gewähren, die Akira Tanaka und John Jacobs zugewiesen sind. Später können Sie den Zugriff von Kara Bowman auf diese Benutzerwarteschlangen löschen.

Nachdem diese Aufgaben zugewiesen wurden, können sie vom Benutzer, der Workspace verwendet, fertiggestellt werden.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

### Zugriff auf ausgewählte Benutzerwarteschlangen gewähren  {#granting-access-to-a-selected-user-queue}

1. Melden Sie sich bei Administration Console mithilfe eines Administratorkontos an.
1. Wählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte „Zugriff auf einen Benutzer verwalten“ den Benutzer aus, dessen Warteschlange sie freigeben möchten. Das untere rechte Fenster zeigt die Liste von Benutzern an, die Zugriff auf die ausgewählte Benutzerwarteschlange haben.
1. Wählen Sie im unteren linken Fenster Benutzerwarteschlangen, die Sie für die ausgewählten Benutzer freigeben möchten. Klicken Sie auf Freigeben.
1. Klicken Sie dann auf „Speichern“.

### Zugriff auf ausgewählte Benutzerwarteschlangen sperren  {#revoking_access_to_a_selected_user_queue-1}

1. Melden Sie sich bei Administration Console mithilfe eines Administratorkontos an.
1. Wählen **Dienste** > **Arbeitsablauf für Formulare** > **Freigegebene Warteschlange**.

1. Wählen Sie auf der Registerkarte „Zugriff von einem Benutzer verwalten“ den Benutzer aus, dessen Warteschlange sie verwalten möchten.
1. Das untere rechte Fenster zeigt die Liste von Benutzerwarteschlangen an, die dem ausgewählten Benutzer zugewiesen sind. Wählen Sie die Benutzerwarteschlange und klicken Sie auf „Sperren“.
1. Klicken Sie dann auf „Speichern“.
