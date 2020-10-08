---
title: Private Ordner zum Freigeben von Assets
description: Learn how to create a private folder in the [!DNL Adobe Experience Manager Assets] and share it with other users and the assign various privileges to them.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 21%

---


# Privater Ordner in [!DNL Adobe Experience Manager Assets] {#private-folder}

You can create a private folder in the [!DNL Adobe Experience Manager Assets] user interface that is available exclusively to you. Sie können diesen privaten Ordner für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

>[!NOTE]
>
>Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;.

## Erstellen und Freigeben von privaten Ordnern {#create-share-private-folder}

So erstellen Sie einen privaten Ordner und geben ihn frei:

1. In the [!DNL Assets] console, click **[!UICONTROL Create]** from the toolbar and then choose **[!UICONTROL Folder]** from the menu.

   ![Asset-Ordner erstellen](assets/Create-folder.png)

1. In the **[!UICONTROL Create Folder]** dialog, enter a title and name (optional) for the folder, and select **[!UICONTROL Private]** option.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. To share the folder with other users and the assign privileges to them, select the folder, and click **[!UICONTROL Properties]** from the toolbar.

   ![Info, Option](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. In the **[!UICONTROL Folder Properties]** page, select a user from the **[!UICONTROL Add User]** list, assign a role to the user on your private folder, and click **[!UICONTROL Add]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie Bearbeiter, Eigentümer oder Betrachter. Wenn Sie dem Benutzer eine Eigentümerrolle zuweisen, hat der Benutzer Editor-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle „Editor“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie eine Viewer-Rolle zuweisen, können die Assets nur in Ihrem privaten Ordner Ansicht werden.

   >[!NOTE]
   >
   >Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;. Daher kann der Administrator nicht alle Inhaber-Mitglieder aus einem privaten Ordner entfernen. Um jedoch vorhandene Inhaber (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Inhaber hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Depending on the role you assign, the user is assigned a set of privileges on your private folder when the user logs in to [!DNL Assets].
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Log in to [!DNL Assets] with the credentials of the user to view the notification.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klicken Sie auf Benachrichtigungen, um die Liste der Benachrichtigungen zu öffnen.

   ![Liste der Meldungen](assets/Assets-Notification.png)

1. Klicken Sie auf den Eintrag für den vom Administrator freigegebenen privaten Ordner, um den Ordner zu öffnen.

>[!NOTE]
>
>To create a private folder, you require Read and Modify [access control permissions](/help/sites-administering/security.md#permissions-in-aem) on the parent folder under which you want to create a private folder. If you are not an administrator, these permissions are not enabled for you by default on `/content/dam`. In diesem Fall sollten Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe abrufen, bevor Sie versuchen, private Ordner zu erstellen.

## Löschen von privaten Ordnern {#delete-private-folder}

Sie können einen Ordner löschen, indem Sie den Ordner auswählen und im oberen Menü die Option &quot; [!UICONTROL Löschen] &quot;wählen oder die Rücktaste auf der Tastatur verwenden.

![Option &quot;Löschen&quot;im oberen Menü](assets/delete-option.png)

>[!CAUTION]
>
>Wenn Sie einen Privatordner aus der CRXDE Lite löschen, bleiben redundante Benutzergruppen im Repository.

>[!NOTE]
>
>Wenn Sie einen Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht.
>
>Vorhandene redundante, nicht verwendete und automatisch generierte Benutzergruppen können jedoch mithilfe der `clean` JMX-Methode in Ihrer Autoreninstanz (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`) aus dem Repository bereinigt werden.
