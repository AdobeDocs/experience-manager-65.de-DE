---
title: Erstellen Sie einen privaten Ordner in Adobe Experience Manager und geben Sie ihn frei.
description: Erfahren Sie, wie Sie einen privaten Ordner in den Assets des Adobe Experience Managers erstellen und ihn für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 45%

---


# Freigeben privater Ordner {#private-folder-sharing}

Sie können in der Benutzeroberfläche &quot;Adobe Experience Manager Assets&quot;einen privaten Ordner erstellen, der ausschließlich für Sie verfügbar ist. Sie können diesen privaten Ordner für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

>[!NOTE]
>
>Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;.

1. In the Assets console, click **[!UICONTROL Create]** from the toolbar and then choose **[!UICONTROL Folder]** from the menu.

   ![Asset-Ordner erstellen](assets/Create-folder.png)

1. In the **[!UICONTROL Create Folder]** dialog, enter a title and name (optional) for the folder, and select **[!UICONTROL Private]**.

   ![Aktivieren Sie das Kontrollkästchen &quot;Privat&quot;, um den Ordner privat zu machen](assets/private-folder.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird auf der Assets-Benutzeroberfläche erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. To share the folder with other users and the assign privileges to them, select the folder, and click **[!UICONTROL Properties]** from the toolbar.

   ![chlimage_1-414](assets/chlimage_1-414.png)

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
   > Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;. Daher kann der Administrator nicht alle Inhaber-Mitglieder aus einem privaten Ordner entfernen. Um jedoch vorhandene Inhaber (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Inhaber hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer einen Satz Berechtigungen für den privaten Ordner, wenn er sich bei  Assets anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei Assets mit den Anmeldedaten des Benutzers an, um die Benachrichtigungen anzuzeigen.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klicken Sie auf Benachrichtigungen, um die Liste der Benachrichtigungen zu öffnen.

   ![Liste der Meldungen](assets/Assets-Notification.png)

1. Klicken Sie auf den Eintrag für den vom Administrator freigegebenen privaten Ordner, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die Berechtigungen „Lesen“ und „ACL bearbeiten“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. If you are not an administrator, these permissions are not enabled for you by default on `/content/dam`. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.
