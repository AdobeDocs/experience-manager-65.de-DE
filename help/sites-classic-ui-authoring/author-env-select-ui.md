---
title: Auswahl der Benutzeroberfläche
seo-title: Selecting your UI
description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzende bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 57d45b06-e76e-420c-8cd0-389bd9f811af
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '195'
ht-degree: 100%

---

# Auswahl der Benutzeroberfläche{#selecting-your-ui}

Da die Touch-optimierte Benutzeroberfläche die klassische Benutzeroberfläche ersetzt, müssen Anwenderinnen und Anwender oder Admins der AEM-Instanz sich aktiv dafür entscheiden, die klassische Benutzeroberfläche weiterhin zu verwenden. Da die klassische Benutzeroberfläche nicht weiterentwickelt wird, können Anwenderinnen und Anwender während der Bearbeitung nicht einfach von der klassischen Benutzeroberfläche zum Äquivalent in der Touch-optimierten Benutzeroberfläche wechseln.

Zur Vereinfachung von Bearbeitungsvorgängen können Benutzerinnen und Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln. Weitere Informationen dazu finden Sie unter [Auswahl der Benutzeroberfläche](/help/sites-authoring/select-ui.md) in der Standarddokumentation zur Bearbeitung.

>[!NOTE]
>
>Instanzen, bei denen ein Upgrade von einer früheren Version durchgeführt wurde, behalten die klassische Benutzeroberfläche für die Seitenbearbeitung bei.
>
>Nach dem Upgrade wechselt die Seitenbearbeitung nicht automatisch zur Touch-optimierten Benutzeroberfläche. Sie können dies aber mit der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** (`AuthoringUIMode`-Service) konfigurieren. Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#uioverridesfortheeditor).

## Konfigurieren der Standard-Benutzeroberfläche für Ihre Instanz {#configuring-the-default-ui-for-your-instance}

Ein Systemadministrator kann die bei Start und Anmeldung angezeigte Benutzeroberfläche mit der [Root-Zuordnung](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) konfigurieren.

Diese Einstellungen kann durch Benutzerstandards oder Sitzungseinstellungen überschrieben werden.
