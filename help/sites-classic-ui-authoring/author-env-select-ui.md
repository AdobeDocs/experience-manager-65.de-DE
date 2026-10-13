---
title: Auswahl der Benutzeroberfläche
description: Zur Vereinfachung von Bearbeitungsvorgängen können Benutzende bei Bedarf von der Touch-optimierten Benutzeroberfläche zur klassischen Benutzeroberfläche wechseln.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 57d45b06-e76e-420c-8cd0-389bd9f811af
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '199'
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
