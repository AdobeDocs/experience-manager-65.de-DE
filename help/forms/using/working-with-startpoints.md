---
title: Arbeiten mit Startpunkten
seo-title: Arbeiten mit Startpunkten
description: Schritte zum Arbeiten mit einem AEM Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
seo-description: Schritte zum Arbeiten mit einem AEM Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
uuid: 1c4b4c86-cbdb-4e72-b0eb-7f8a2f5dcdde
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 1ea60fb2-cf9f-4a87-bd8e-98150e668456
docset: aem65
exl-id: d5970f90-2899-43a5-a3a0-61a2c844d919
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 81%

---

# Arbeiten mit Startpunkten{#working-with-startpoints}

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird.

>[!NOTE]
>
>Die Begriffe „Startpunkte“, „Startprozess“ und „Formular“ werden wechselweise verwendet, wenn von diesem Konzept die Rede ist.

Um einen Prozess über die AEM Forms-App zu initiieren, muss Ihr Prozess einen Startpunkt vom Typ **Workspace** enthalten. Außerdem müssen Sie für den Startpunkt die Option **[!UICONTROL Visible in Mobile Workspace]** auswählen.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-App verfügbaren Startpunkte anzuzeigen, gehen Sie zum [Startbildschirm](../../forms/using/home-screen.md).
1. Auf dem Bildschirm **[!UICONTROL Home]** wird standardmäßig die Liste **[!UICONTROL Alle Forms]** angezeigt.

   Der Startpunkt ist mit einem Formular verknüpft. Tippen Sie in der Liste auf das mit dem Startpunkt verknüpfte Formular, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Geben Sie die Details in das Formular für den **[!UICONTROL Startpunkt]** ein.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](../../forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, tippen Sie auf **[!UICONTROL Senden.]**

Wenn die App offline ist, werden das Formular und die Daten im Ordner „Outbox“ gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM Forms-Server synchronisiert und dem im Prozess angegebenen Benutzer zugewiesen.

Informationen zum Bearbeiten der Aufgabe in Ihrer Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).
