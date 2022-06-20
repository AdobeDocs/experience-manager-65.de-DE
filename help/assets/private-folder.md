---
title: Private Ordner zum Freigeben von Assets
description: Erfahren Sie, wie Sie einen privaten Ordner in [!DNL Adobe Experience Manager Assets] erstellen, diesen mit anderen Benutzern teilen und ihm verschiedene Berechtigungen zuweisen können.
contentOwner: AG
role: User
feature: Collaboration
exl-id: c1aece06-7c1c-43a0-bea0-6f11ecda7e68
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 69%

---

# Privater Ordner in [!DNL Adobe Experience Manager Assets] {#private-folder}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/private-folder.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/managing/private-folder.html?lang=en) |

Sie können in der Benutzeroberfläche von [!DNL Adobe Experience Manager Assets] einen privaten Ordner erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner auch für andere Benutzer freigeben und diesen Benutzern verschiedene Berechtigungen zuweisen. Je nach zugewiesenenr Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner durchführen, wie z.B. Assets innerhalb des Ordners anzeigen oder Assets bearbeiten.

>[!NOTE]
>
>Der private Ordner hat mindestens einen Benutzer mit der Rolle „Eigentümer“.

## Erstellung und Freigabe privater Ordner {#create-share-private-folder}

So erstellen und teilen Sie einen privaten Ordner:

1. Im [!DNL Assets] Console, klicken Sie auf **[!UICONTROL Erstellen]** Wählen Sie in der Symbolleiste und anschließend **[!UICONTROL Ordner]** aus dem Menü.

   ![Asset-Ordner erstellen](assets/Create-folder.png)

1. Im **[!UICONTROL Ordner erstellen]** ein, geben Sie einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie **[!UICONTROL Privat]** -Option.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Um den Ordner für andere Benutzer freizugeben und ihnen Berechtigungen zuzuweisen, wählen Sie den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]** aus der Symbolleiste.

   ![Info-Option](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. Im **[!UICONTROL Ordnereigenschaften]** Seite, wählen Sie einen Benutzer aus der **[!UICONTROL Benutzer hinzufügen]** auflisten, dem Benutzer in Ihrem privaten Ordner eine Rolle zuweisen und auf **[!UICONTROL Hinzufügen]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie z.B. `Editor`, `Owner` oder `Viewer`. Wenn Sie dem Benutzer die Rolle `Owner` zuweisen, hat der Benutzer `Editor`-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle `Editor` zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner lediglich anzeigen.

   >[!NOTE]
   >
   >Mindestens ein Benutzer des privaten Ordners verfügt über die Rolle `Owner`. Daher kann der Administrator nicht alle Mitglieder des Eigentümers aus einem privaten Ordner entfernen. Um jedoch die vorhandenen Eigentümer (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Eigentümer hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach zugewiesener Rolle erhält der Benutzer eine Reihe von Berechtigungen für den privaten Ordner, wenn er sich bei [!DNL Assets] anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]**, um die Bestätigungsmeldung zu schließen.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Anmelden bei [!DNL Assets] mit den Anmeldeinformationen des Benutzers zum Anzeigen der Benachrichtigung.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klicken Sie auf [!UICONTROL Benachrichtigungen], um eine Liste der Benachrichtigungen zu öffnen.

   ![Benachrichtigungsliste](assets/Assets-Notification.png)

1. Klicken Sie auf den Eintrag für den vom Administrator freigegebenen privaten Ordner, um den Ordner zu öffnen.

>[!NOTE]
>
>Zum Erstellen eines privaten Ordners benötigen Sie Lesen und Ändern [Zugriffssteuerungsberechtigungen](/help/sites-administering/security.md#permissions-in-aem) im übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie kein Administrator sind, sind diese Berechtigungen standardmäßig für Sie nicht aktiviert. `/content/dam`. In diesem Fall brauchen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.

## Löschen eines privaten Ordners {#delete-private-folder}

Sie können einen Ordner löschen, indem Sie ihn auswählen und die Option [!UICONTROL Löschen] auswählen oder die Rücktaste auf der Tastatur drücken.

![Löschoption im oberen Menü](assets/delete-option.png)

>[!CAUTION]
>
>Wenn Sie einen privaten Ordner aus CRXDE Lite löschen, verbleiben redundante Benutzergruppen im Repository.

>[!NOTE]
>
>Wenn Sie einen Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht.
>
>Die vorhandenen redundanten, nicht verwendeten und automatisch generierten Benutzergruppen können jedoch mithilfe der `clean`-Methode in JMX in der Autoreninstanz (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`) entfernt werden.
