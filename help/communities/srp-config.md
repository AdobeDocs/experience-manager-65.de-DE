---
title: Speicherkonfiguration
description: Erfahren Sie mehr über die Speicherkonfigurationskonsole als Möglichkeit, den für Community-Inhalte ausgewählten Speicher zu identifizieren, der auch als benutzergenerierte Inhalte bezeichnet wird.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 4%

---

# Speicherkonfiguration {#storage-configuration}

Die Speicherkonfiguration dient der Identifizierung des für Community-Inhalte ausgewählten Speichers, auch als benutzergenerierte Inhalte (UGC) bezeichnet.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des SRP (Storage Resource Provider) beim Zugriff auf UGC verwendet wird. Sie muss die bei der Bereitstellung von Adobe Experience Manager (AEM) festgelegte Topologie widerspiegeln.

Eine Diskussion der Speicheroptionen und Bereitstellungstopologien finden Sie unter:

* [Community-Inhaltsspeicher](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Speicherkonfigurationskonsole {#storage-configuration-console}

![jsrp-configuration](assets/jsrp-configuration.png)

In der Autorenumgebung, um die Speicherkonfigurationskonsole zu erreichen.

* Wählen Sie in der globalen Navigation die Option **[!UICONTROL Instrumente]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**

So wählen Sie eine andere Speicheroption als das standardmäßige JCR aus:

* Option auswählen
* Geeignete Konfiguration

   * Siehe Details für [Auswählen von MSRP](msrp.md#select-msrp)
   * Siehe Details für [Auswahl von DSRP](dsrp.md#select-dsrp)
   * Siehe Details für [Auswählen von ASRP](asrp.md#select-asrp)

* Wählen Sie **[!UICONTROL Absenden]**.

### Über JCR-Speicher {#about-jcr-storage}

Wenn keine Auswahl getroffen wurde, ist der Standardwert das AEM-Repository, JCR.

JCR ist *not* ein gemeinsamer Speicher, der von der Autoren- und Veröffentlichungsumgebung freigegeben wird. Community-Inhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Besuch [JCR-Store](jsrp.md) für weitere Informationen.

>[!NOTE]
>
>Das Fehlen des Knotens `srpc` under `/etc/socialconfig` gibt den Standardwert an [JCR-Store](jsrp.md).
