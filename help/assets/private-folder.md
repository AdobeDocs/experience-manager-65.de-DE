---
title: Private Ordner zum Freigeben von Assets
description: Erfahren Sie, wie Sie einen privaten Ordner in [!DNL Adobe Experience Manager Assets] erstellen, diesen mit anderen Benutzern teilen und ihm verschiedene Berechtigungen zuweisen können.
contentOwner: AG
role: User
feature: Collaboration
exl-id: c1aece06-7c1c-43a0-bea0-6f11ecda7e68
source-git-commit: 3d713021ac410ca2925a282c5dfca98ed4e483ee
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 97%

---

# Privater Ordner in [!DNL Adobe Experience Manager Assets] {#private-folder}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/private-folder.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Sie können in der Benutzeroberfläche von [!DNL Adobe Experience Manager Assets] einen privaten Ordner erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner auch für andere Benutzer freigeben und diesen Benutzern verschiedene Berechtigungen zuweisen. Je nach zugewiesenenr Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner durchführen, wie z.B. Assets innerhalb des Ordners anzeigen oder Assets bearbeiten.

>[!NOTE]
>
>Der private Ordner hat mindestens einen Benutzer mit der Rolle „Eigentümer“.

## Erstellung und Freigabe privater Ordner {#create-share-private-folder}

So erstellen Sie einen privaten Ordner und geben ihn frei:

1. Klicken Sie in der [!DNL Assets]-Konsole von der Symbolleiste aus auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Ordner]** aus dem Menü aus.

   ![Asset-Ordner erstellen](assets/Create-folder.png)

1. Geben Sie in das Dialogfeld **[!UICONTROL Ordner anlegen]** einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie die Option **[!UICONTROL Privat]** aus.

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird erstellt.

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Um den Ordner für andere Benutzer freizugeben und ihnen Berechtigungen zuzuweisen, wählen Sie den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]** in der Symbolleiste.

   ![Info-Option](assets/do-not-localize/info-circle-icon.png)

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. Wählen Sie auf der Seite **[!UICONTROL Ordnereigenschaften]** einen Benutzer in der Liste **[!UICONTROL Benutzer hinzufügen]** aus, weisen Sie dem Benutzer eine Rolle für den privaten Ordner zu und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie z.B. `Editor`, `Owner` oder `Viewer`. Wenn Sie dem Benutzer die Rolle `Owner` zuweisen, hat der Benutzer `Editor`-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle `Editor` zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner lediglich anzeigen.

   >[!NOTE]
   >
   >Mindestens ein Benutzer des privaten Ordners verfügt über die Rolle `Owner`. Daher kann die bzw. der Admin nicht alle Mitglieder mit der Rolle „Eigentümer“ aus einem privaten Ordner entfernen. Um jedoch die vorhandenen Eigentümer (und die bzw. den Admin selbst) aus dem privaten Ordner zu entfernen, muss die bzw. der Admin eine andere Benutzerin oder einen anderen Benutzer als Eigentümerin bzw. Eigentümer hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach zugewiesener Rolle erhält der Benutzer eine Reihe von Berechtigungen für den privaten Ordner, wenn er sich bei [!DNL Assets] anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]**, um die Bestätigungsmeldung zu schließen.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei [!DNL Assets] mit den Anmeldedaten des Benutzers an, um die Benachrichtigung anzuzeigen.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Klicken Sie auf [!UICONTROL Benachrichtigungen], um eine Liste der Benachrichtigungen zu öffnen.

   ![Benachrichtigungsliste](assets/Assets-Notification.png)

1. Klicken Sie auf den Eintrag für den vom Adminseite freigegebenen privaten Ordner, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die [Zugriffssteuerungsberechtigungen](/help/sites-administering/security.md#permissions-in-aem) „Lesen“ und „Ändern“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie nicht Admin sind, werden diese Berechtigungen auf `/content/dam` nicht standardmäßig für Sie aktiviert. In diesem Fall brauchen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.

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
