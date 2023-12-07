---
title: Auswahl der Benutzeroberfläche
description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzende bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 57d45b06-e76e-420c-8cd0-389bd9f811af
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# Auswahl der Benutzeroberfläche{#selecting-your-ui}

Da die Touch-optimierte Benutzeroberfläche die klassische Benutzeroberfläche ersetzt, müssen Anwenderinnen und Anwender oder Admins der AEM-Instanz sich aktiv dafür entscheiden, die klassische Benutzeroberfläche weiterhin zu verwenden. Da die klassische Benutzeroberfläche nicht weiterentwickelt wird, können Anwenderinnen und Anwender während der Bearbeitung nicht einfach von der klassischen Benutzeroberfläche zum Äquivalent in der Touch-optimierten Benutzeroberfläche wechseln.

Zur Vereinfachung von Bearbeitungsvorgängen können Benutzerinnen und Benutzer bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln. Weitere Informationen finden Sie unter [Auswählen Ihrer Benutzeroberfläche](/help/sites-authoring/select-ui.md) in der Dokumentation zum standardmäßigen Authoring.

>[!NOTE]
>
>Instanzen, bei denen ein Upgrade von einer früheren Version durchgeführt wurde, behalten die klassische Benutzeroberfläche für die Seitenbearbeitung bei.
>
>Nach dem Upgrade wechselt die Seitenbearbeitung nicht automatisch zur Touch-optimierten Benutzeroberfläche. Sie können dies aber mit der [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des **WCM Authoring UI Mode Service** (`AuthoringUIMode`-Service) konfigurieren. Weitere Informationen dazu finden Sie unter [Benutzeroberflächenüberschreibung für den Editor](#uioverridesfortheeditor).

## Konfigurieren der Standard-Benutzeroberfläche für Ihre Instanz {#configuring-the-default-ui-for-your-instance}

Systemadmins können die Benutzeroberfläche konfigurieren, die beim Start und bei der Anmeldung angezeigt wird, indem sie die [Stammzuordnung](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) verwenden.

Dies kann durch Benutzerstandardeinstellungen oder Sitzungseinstellungen überschrieben werden.
