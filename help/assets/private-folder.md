---
title: Privater Ordner in [!DNL Adobe Experience Manager Assets]
description: Learn how to create a private folder in the [!DNL Adobe Experience Manager Assets] and share it with other users and the assign various privileges to them.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b676f73a800c45be12de70b8ba57a332563a49a4
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 23%

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
>Zum Erstellen eines privaten Ordners benötigen Sie die Zugriffsrechte zum Lesen und Bearbeiten von ACL für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. If you are not an administrator, these permissions are not enabled for you by default on `/content/dam`. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.

## Löschen von privaten Ordnern {#delete-private-folder}

Sie können einen privaten Ordner löschen, indem Sie den Ordner auswählen und im oberen Menü die Option &quot; [!UICONTROL Löschen] &quot;wählen oder die Rücktaste auf der Tastatur verwenden.

### Entfernen von Benutzergruppen beim Löschen von Ordnern {#group-removal-on-folder-deletion}

Wenn Sie einen privaten Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht. Vorhandene redundante, nicht verwendete und automatisch generierte Benutzergruppen können jedoch mithilfe von [JMX](#group-clean-up-jmx)aus dem Repository bereinigt werden.

>[!CAUTION]
>
>Wenn Sie einen Privatordner aus der CRXDE Lite löschen, bleiben redundante Benutzergruppen im Repository.

### Verwenden Sie JMX, um nicht verwendete Benutzergruppen zu bereinigen {#group-clean-up-jmx}

So bereinigen Sie das Repository nicht verwendeter Benutzergruppen:

1. Öffnen Sie die JMX-Datei, um redundante Gruppen für Assets zu reinigen von `http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`.

1. Rufen Sie die `clean` Methode aus dieser JMX-Datei auf.

Sie können sehen, dass alle redundanten Benutzergruppen oder die automatisch generierten Gruppen (die beim Erstellen eines privaten Ordners mit demselben Namen wie eine zuvor gelöschte Gruppe erstellt werden) aus dem Pfad entfernt werden `/home/groups/mac/default/<user_name>/<folder_name>`.
