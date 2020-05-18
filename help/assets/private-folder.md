---
title: Erstellen und Freigeben eines privaten Ordners in AEM
description: Erfahren Sie, wie Sie in Adobe Experience Manager (AEM) Assets einen privaten Ordner erstellen, ihn mit anderen Benutzern teilen und ihnen verschiedene Berechtigungen zuweisen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 02bd337271f0039b354ada2899198f5654f9e8bf
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 71%

---


# Freigeben privater Ordner {#private-folder-sharing}

Sie können einen privaten Ordner in der Adobe Experience Manager (AEM) Assets-Benutzeroberfläche erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

>[!NOTE]
>
> Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;.


1. Klicken oder tippen Sie in der Konsole „Assets“ von der Symbolleiste aus auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Ordner]** aus dem Menü aus.

   ![Asset-Ordner erstellen](assets/Create-folder.png)

1. In the **[!UICONTROL Create Folder]** dialog, enter a title and name (optional) for the folder, and select **[!UICONTROL Private]**.

   ![Aktivieren Sie das Kontrollkästchen &quot;Privat&quot;, um den Ordner privat zu machen](assets/private-folder.png)

1. Tippen oder klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird auf der Assets-Benutzeroberfläche erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Um den Ordner für andere Benutzer freizugeben und ihnen Berechtigungen zuzuweisen, wählen Sie den Ordner aus und tippen/klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]** in der Symbolleiste.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. In the **[!UICONTROL Folder Properties]** page, select a user from the **[!UICONTROL Add User]** list, assign a role to the user on your private folder, and click **[!UICONTROL Add]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie Bearbeiter, Eigentümer oder Betrachter. Wenn Sie dem Benutzer eine Eigentümerrolle zuweisen, hat der Benutzer Editor-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle „Editor“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets im privaten Ordner lediglich anzeigen.

   >[!NOTE]
   >
   > Der private Ordner hat mindestens ein Mitglied mit der Rolle &quot;Inhaber&quot;. Daher kann der Administrator nicht alle Inhaber-Mitglieder aus einem privaten Ordner entfernen. Um jedoch vorhandene Inhaber (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Inhaber hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer einen Satz Berechtigungen für den privaten Ordner, wenn er sich bei AEM Assets anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei AEM Assets mit den Anmeldedaten des Benutzers an, um die Benachrichtigungen anzuzeigen.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Tippen/klicken Sie auf das Symbol „Benachrichtigungen“, um eine Liste der Benachrichtigungen zu öffnen.

   ![Liste der Meldungen](assets/Assets-Notification.png)

1. Klicken oder tippen Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die Berechtigungen „Lesen“ und „ACL bearbeiten“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. If you are not an administrator, these permissions are not enabled for you by default on `/content/dam`. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.
