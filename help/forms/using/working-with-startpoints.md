---
title: Arbeiten mit Startpunkten
description: Schritte zum Arbeiten mit einem Adobe Experience Manager Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: d5970f90-2899-43a5-a3a0-61a2c844d919
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: dd8748cee7a4b3ba91795a51928bd8590c47ef27
workflow-type: ht
source-wordcount: '235'
ht-degree: 100%

---


# Arbeiten mit Startpunkten{#working-with-startpoints}

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird.

>[!NOTE]
>
>Die Begriffe „Startpunkte“, „Startprozess“ und „Formular“ werden wechselweise verwendet, wenn von diesem Konzept die Rede ist.

Um einen Prozess aus der Adobe Experience Manager Forms-Anwendung zu initiieren, müssen Sie einen Startpunkt des Typs **Arbeitsbereich** in Ihrem Prozess haben. Außerdem müssen Sie für den Startpunkt die Option **[!UICONTROL In Mobile Workspace sichtbar]** auswählen.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-Anwendung verfügbaren Startpunkte anzuzeigen, navigieren Sie zum [Startbildschirm](../../forms/using/home-screen.md).
1. Auf dem Bildschirm **[!UICONTROL Startseite]** wird standardmäßig die Liste **[!UICONTROL Alle Formulare]** angezeigt.

   Der Startpunkt ist mit einem Formular verknüpft. Wählen Sie in der Liste das mit dem Startpunkt verknüpfte Formular aus, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Geben Sie die Details in das Formular für den **[!UICONTROL Startpunkt]** ein.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](../../forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, wählen Sie die Schaltfläche **[!UICONTROL Absenden]** aus.

Wenn die App offline ist, werden das Formular und die Daten im Ordner „Postausgang“ gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM-Formular-Server synchronisiert und der im Prozess angegebenen Person zugewiesen.

Informationen zum Bearbeiten der Aufgabe in Ihrer Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).
