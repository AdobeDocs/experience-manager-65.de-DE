---
title: Arbeiten mit Startpunkten
description: Schritte zum Arbeiten mit einem Adobe Experience Manager Forms-Prozess von Ihrem in Workbench definierten Mobilgerät aus.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: d5970f90-2899-43a5-a3a0-61a2c844d919
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 31%

---

# Arbeiten mit Startpunkten{#working-with-startpoints}

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird.

>[!NOTE]
>
>Die Begriffe &quot;Startpunkte&quot;, &quot;Startprozess&quot;und &quot;Formular&quot;werden synonym verwendet, wenn auf dieses Konzept verwiesen wird.

Um einen Prozess aus der Adobe Experience Manager (AEM) Forms App zu starten, benötigen Sie einen Startpunkt vom Typ **Arbeitsbereich** in Ihrem Prozess. Außerdem müssen Sie die **[!UICONTROL In Mobile Workspace sichtbar]** -Option für den Startpunkt.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-App verfügbaren Startpunkte anzuzeigen, navigieren Sie zu [Startbildschirm](../../forms/using/home-screen.md).
1. Auf dem Bildschirm **[!UICONTROL Startseite]** wird standardmäßig die Liste **[!UICONTROL Alle Formulare]** angezeigt.

   Der Startpunkt ist mit einem Formular verknüpft. Wählen Sie in der Liste das mit dem Startpunkt verknüpfte Formular aus, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Geben Sie die Details in das Formular für den **[!UICONTROL Startpunkt]** ein.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](../../forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, wählen Sie die **[!UICONTROL Einsenden]** Schaltfläche.

Wenn die App offline ist, werden das Formular und die zugehörigen Daten im Ordner &quot;Outbox&quot;gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM Forms-Server synchronisiert und dem im Prozess angegebenen Benutzer zugewiesen.

Informationen zum Arbeiten mit der Aufgabe in der Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).
