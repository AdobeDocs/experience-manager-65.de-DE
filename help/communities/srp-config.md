---
title: Speicherkonfiguration
description: Erfahren Sie mehr über die Speicherkonfigurationskonsole , um den für Community-Inhalte ausgewählten Speicher zu identifizieren (auch als benutzergenerierte Inhalte bezeichnet).
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
solution: Experience Manager
feature: Communities
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 4%
---
# Speicherkonfiguration {#storage-configuration}

Die Speicherkonfiguration ist das Mittel zur Identifizierung des Speichers, der für Community-Inhalte ausgewählt wird, auch als benutzergenerierter Inhalt (User-Generated Content, UGC) bezeichnet.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des SRP (Storage Resource Provider) beim Zugriff auf UGC verwendet wird. Sie muss die Topologie widerspiegeln, die bei der Bereitstellung von Adobe Experience Manager (AEM) festgelegt wurde.

Eine Erläuterung der Speicheroptionen und Bereitstellungstopologien finden Sie unter:

* [Community-Inhaltsspeicher](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Speicherkonfigurationskonsole {#storage-configuration-console}

![jsrp-configuration](assets/jsrp-configuration.png)

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Speicherkonfigurationskonsole zu gelangen.

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**

So wählen Sie eine andere Speicheroption als die standardmäßige JCR aus:

* Option auswählen
* Richtig konfigurieren

  * Siehe Details für [Auswahl von MSRP](msrp.md#select-msrp)
  * Siehe Details zur [Auswahl von DSRP](dsrp.md#select-dsrp)
  * Siehe Details für [Auswählen von ASRP](asrp.md#select-asrp)

* Wählen Sie **[!UICONTROL Absenden]**.

### Über den JCR-Speicher {#about-jcr-storage}

Wenn keine Auswahl getroffen wird, ist die Standardeinstellung das AEM-Repository JCR.

JCR *kein* Speicher, der von der Autoren- und Veröffentlichungsumgebung gemeinsam genutzt wird. Community-Inhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Weitere Informationen finden Sie [JCR](jsrp.md)Store).

>[!NOTE]
>
>Das Fehlen des `srpc` unter `/etc/socialconfig` zeigt den standardmäßigen [JCR-Speicher](jsrp.md) an.
