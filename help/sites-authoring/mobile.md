---
title: Verfassen einer Inhaltsseite für Mobilgeräte
description: Beim Verfassen für Mobilgeräte können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was die Endbenutzenden sehen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 9c6c6386-5ffd-4fa6-9aa1-f5b0e31d1046
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
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
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 100%
---
# Verfassen einer Seite für Mobilgeräte{#authoring-a-page-for-mobile-devices}

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen mehreren Emulatoren wechseln, um zu sehen, was die Endbenutzerinnen und -benutzer beim Zugriff auf die Seite sehen.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn die Endbenutzerinnen und -benutzer auf eine mobile Seite zugreifen, erkennt AEM das Gerät und übermittelt die Darstellung, die der Gerätegruppe entspricht.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. (Siehe [Erstellen einer Live Copy für unterschiedliche Kanäle](/help/sites-administering/msm-livecopy.md).)
>
>AEM-Entwickler können neue Gerätegruppen erstellen. (Siehe [Erstellen von Gerätegruppen-Filtern](/help/sites-developing/groupfilters.md).)

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Öffnen Sie ausgehend von der globalen Navigation die **Sites-Konsole**.
1. Öffnen Sie die Seite **We.Retail** > **Vereinigte Staaten** > **Englisch**.

1. Wechseln Sie in den **Vorschaumodus**.
1. Wechseln Sie durch Klicken auf das Gerätesymbol am oberen Seitenrand zum gewünschten Emulator.
1. Ziehen Sie Komponenten per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.

Die Seite sieht ähnlich wie die folgende aus:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird.
