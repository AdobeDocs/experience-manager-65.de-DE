---
title: Private Ordner zum Freigeben von Assets
description: Erfahren Sie, wie Sie einen privaten Ordner im Ordner  [!DNL Adobe Experience Manager Assets] erstellen und ihn für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen.
contentOwner: AG
role: Business Practitioner
feature: Zusammenarbeit
exl-id: c1aece06-7c1c-43a0-bea0-6f11ecda7e68
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 12%

---

# Privater Ordner in [!DNL Adobe Experience Manager Assets] {#private-folder}

Sie können einen privaten Ordner in der Benutzeroberfläche [!DNL Adobe Experience Manager Assets] erstellen, der ausschließlich für Sie verfügbar ist. Sie können diesen privaten Ordner für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

>[!NOTE]
>
>Der private Ordner hat mindestens ein Mitglied mit der Eigentümerrolle.

## Erstellung und Freigabe privater Ordner {#create-share-private-folder}

So erstellen und teilen Sie einen privaten Ordner:

1. Klicken Sie in der [!DNL Assets]-Konsole in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Ordner]** aus dem Menü aus.

   ![Erstellen von Asset-Ordnern](assets/Create-folder.png)

1. Geben Sie im Dialogfeld **[!UICONTROL Ordner erstellen]** einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie die Option **[!UICONTROL Privat]** aus.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Um den Ordner für andere Benutzer freizugeben und ihnen Berechtigungen zuzuweisen, wählen Sie den Ordner aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]** .

   ![Info-Option](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. Wählen Sie auf der Seite **[!UICONTROL Ordnereigenschaften]** einen Benutzer aus der Liste **[!UICONTROL Benutzer hinzufügen]** aus, weisen Sie dem Benutzer eine Rolle in Ihrem privaten Ordner zu und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, z. B. `Editor`, `Owner` oder `Viewer`. Wenn Sie dem Benutzer die Rolle `Owner` zuweisen, hat der Benutzer die Berechtigung `Editor` für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle `Editor` zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie eine Viewer-Rolle zuweisen, kann der Benutzer die Assets nur in Ihrem privaten Ordner anzeigen.

   >[!NOTE]
   >
   >Der private Ordner hat mindestens ein Mitglied mit der Rolle `Owner`. Daher kann der Administrator nicht alle Mitglieder des Eigentümers aus einem privaten Ordner entfernen. Um jedoch die vorhandenen Eigentümer (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Eigentümer hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer eine Reihe von Berechtigungen für Ihren privaten Ordner, wenn sich der Benutzer bei [!DNL Assets] anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei [!DNL Assets] mit den Anmeldeinformationen des Benutzers an, um die Benachrichtigung anzuzeigen.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klicken Sie auf [!UICONTROL Benachrichtigungen] , um eine Liste mit Benachrichtigungen zu öffnen.

   ![Benachrichtigungsliste](assets/Assets-Notification.png)

1. Klicken Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

>[!NOTE]
>
>Zum Erstellen eines privaten Ordners benötigen Sie Lese- und Änderungsberechtigungen für [Zugriffskontrolle](/help/sites-administering/security.md#permissions-in-aem) für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie kein Administrator sind, sind diese Berechtigungen für Sie standardmäßig nicht unter `/content/dam` aktiviert. Rufen Sie in diesem Fall zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe ab, bevor Sie versuchen, private Ordner zu erstellen.

## Löschen privater Ordner {#delete-private-folder}

Sie können einen Ordner löschen, indem Sie ihn auswählen und im oberen Menü die Option [!UICONTROL Löschen] auswählen oder indem Sie die Rücktaste auf Ihrer Tastatur verwenden.

![Löschoption im oberen Menü](assets/delete-option.png)

>[!CAUTION]
>
>Wenn Sie einen privaten Ordner aus CRXDE Lite löschen, bleiben redundante Benutzergruppen im Repository.

>[!NOTE]
>
>Wenn Sie einen Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht.
>
>Die vorhandenen redundanten, nicht verwendeten und automatisch generierten Benutzergruppen können jedoch mithilfe der `clean`-Methode in JMX in der Autoreninstanz (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`) aus dem Repository entfernt werden.
