---
title: Verfassen einer Seite für Mobilgeräte
seo-title: Verfassen einer Seite für Mobilgeräte
description: Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um festzustellen, welche Darstellung der Endbenutzer sieht.
seo-description: Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um festzustellen, welche Darstellung der Endbenutzer sieht.
uuid: a7a1ba68-d608-4819-88d1-0dab5955d3f4
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9554cdb3-b604-4d50-9760-89b9e7a7755f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 89%

---


# Verfassen einer Seite für Mobilgeräte{#authoring-a-page-for-mobile-devices}

Wenn Sie eine Seite für Mobilgeräte bearbeiten, wird die Seite so angezeigt, dass das Mobilgerät emuliert wird. Beim Bearbeiten der Seite können Sie zwischen verschiedenen Emulatoren wechseln, um zu sehen, was der Endbenutzer sieht, wenn auf er die Seite zugreift.

Geräte sind entsprechend ihrer Fähigkeit zur Wiedergabe einer Seite in die Kategorien „Feature“, „Smart“ und „Touch“ eingeteilt. Wenn der Endbenutzer auf eine Seite für Mobilgeräte zugreift, ermittelt AEM das entsprechende Gerät und sendet die zu der entsprechenden Gerätegruppe gehörige Version der Seite.

>[!NOTE]
>
>Zur Erstellung einer Website für Mobilgeräte auf der Grundlage einer bestehenden Standard-Site erstellen Sie eine Live Copy der Standard-Site. (Siehe [Erstellen einer Live-Kopie für verschiedene Kanal](/help/sites-administering/msm-livecopy.md).)
>
>AEM-Entwickler können neue Gerätegruppen erstellen. (Siehe [Erstellen von Filtern für Gerätegruppen](/help/sites-developing/groupfilters.md).)

Gehen Sie wie folgt vor, um eine Seite für Mobilgeräte zu erstellen:

1. Öffnen Sie ausgehend von der globalen Navigation die **Sites-Konsole**.
1. Öffnen Sie die Seite **We.Retail** -> **Vereinigte Staaten** -> **Englisch**.

1. Wechseln Sie in den Modus **Vorschau**.
1. Wechseln Sie durch Klicken auf das Gerätesymbol am oberen Seitenrand zum gewünschten Emulator.
1. Verschieben Sie per Drag-and-Drop Komponenten aus dem Komponenten-Browser auf die Seite.

Die Seite sieht ähnlich wie die folgende aus:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>Die Emulatoren sind deaktiviert, wenn eine Seite in der Autoreninstanz von einem Mobilgerät aus aufgerufen wird.

