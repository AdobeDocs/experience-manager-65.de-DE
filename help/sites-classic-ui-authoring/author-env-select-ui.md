---
title: Festlegen der Benutzeroberfläche
seo-title: Auswahl der Benutzeroberfläche
description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
seo-description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 57d45b06-e76e-420c-8cd0-389bd9f811af
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 60%

---

# Auswahl der Benutzeroberfläche{#selecting-your-ui}

Da die Touch-optimierte Benutzeroberfläche die klassische Benutzeroberfläche ersetzt, muss der Benutzer oder Administrator der AEM-Instanz aktiv entscheiden, die klassische Benutzeroberfläche weiterhin zu verwenden. Da die klassische Benutzeroberfläche nicht mehr gepflegt wird, ist es für den Autoren nicht möglich, einfach von der klassischen Benutzeroberfläche zur entsprechenden in der Touch-optimierten Benutzeroberfläche zu wechseln.

Zur Vereinfachung von Bearbeitungsvorgängen können Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln. Weitere Informationen dazu finden Sie unter [Auswahl der Benutzeroberfläche](/help/sites-authoring/select-ui.md) in der Standarddokumentation zur Bearbeitung.

>[!NOTE]
>
>Instanzen, bei denen ein Upgrade aus einer früheren Version durchgeführt wurde, behalten die klassische Benutzeroberfläche bei der Seitenbearbeitung bei.
>
>Nach der Aktualisierung wird die Seitenbearbeitung nicht automatisch auf die Touch-optimierte Benutzeroberfläche umgestellt. Sie können dies jedoch mit der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** ( `AuthoringUIMode`-Service) konfigurieren. Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#uioverridesfortheeditor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

Ein Systemadministrator kann die bei Start und Anmeldung angezeigte Benutzeroberfläche mit der [Root-Zuordnung](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) konfigurieren.

Diese Einstellungen kann durch Benutzerstandards oder Sitzungseinstellungen überschrieben werden.
