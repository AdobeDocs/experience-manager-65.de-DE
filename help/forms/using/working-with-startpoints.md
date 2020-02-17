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
translation-type: tm+mt
source-git-commit: d9975c0dcc02ae71ac64aadb6b4f82f7c993f32c

---


# Arbeiten mit Startpunkten{#working-with-startpoints}

Ein Startpunkt ruft einen in der Workbench erstellten Prozess auf. Ein ist mit einem Formular verknüpft, über das der Prozess aufgerufen wird, wenn das Formular gesendet wird. Genauere Informationen zu Prozessen finden Sie unter [Schrittweise Anleitung für die Geometrixx Finance-Referenz-Website](../../forms/using/finance-reference-site-walkthrough.md).

>[!NOTE]
>
>Die Begriffe „Startpunkte“, „Startprozess“ und „Formular“ werden wechselweise verwendet, wenn von diesem Konzept die Rede ist.

Um einen Prozess aus der AEM Forms-App zu starten, müssen Sie einen Startpunkt des Typs **Workspace **in Ihrem Prozess haben. Außerdem müssen Sie für den Startpunkt die Option **[!UICONTROL Visible in Mobile Workspace]** auswählen.

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**Starten eines in Workbench definierten Prozesses**

1. Um die in der AEM Forms-App verfügbaren Startpunkte anzuzeigen, gehen Sie zum [Startbildschirm](../../forms/using/home-screen.md).
1. On the **[!UICONTROL Home]**screen, by default, the **[!UICONTROL All Forms]**list is displayed.

   Der Startpunkt ist mit einem Formular verknüpft. Tippen Sie auf das mit dem Startpunkt verknüpfte Formular in der Liste, um es zu öffnen.

   Das mit dem Startpunkt verknüpfte Formular wird geöffnet.

1. Enter the details in the **[!UICONTROL Startpoint]**form.

   Sie können dieser Aufgabe mithilfe der Schaltfläche[ Anlage](../../forms/using/add-attachments.md) Anmerkungen hinzufügen.

1. Nachdem Sie das Formular ausgefüllt haben, tippen Sie auf **Senden.**

Wenn die App offline ist, werden das Formular und die Daten im Ordner „Outbox“ gespeichert.

Wenn die App online ist, wird die Aufgabe mit dem AEM Forms-Server synchronisiert und dem im Prozess angegebenen Benutzer zugewiesen.

Informationen zum Bearbeiten der Aufgabe in Ihrer Aufgabenliste finden Sie unter [Öffnen einer Aufgabe](/help/forms/using/open-task.md).

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
