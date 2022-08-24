---
title: Speicherkonfiguration
seo-title: Storage Configuration
description: Zugriff auf die Speicherkonfigurationskonsole
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 4%

---

# Speicherkonfiguration {#storage-configuration}

Mit der Speicherkonfiguration wird der für Community-Inhalte ausgewählte Speicher identifiziert, der auch als benutzergenerierte Inhalte (UGC) bezeichnet wird.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des Speicherressourcenanbieters (SRP) beim Zugriff auf UGC verwendet werden soll, und muss die bei der Bereitstellung von AEM festgelegte Topologie widerspiegeln.

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

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Über JCR-Speicher {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl das AEM-Repository JCR standardmäßig verwendet wird.

JCR ist *not* ein gemeinsamer Speicher, der von der Autoren- und Veröffentlichungsumgebung gemeinsam genutzt wird. Community-Inhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Besuch [JCR-Store](jsrp.md) für weitere Informationen.

>[!NOTE]
>
>Das Fehlen des Knotens `srpc` under `/etc/socialconfig` gibt den Standardwert an [JCR-Store](jsrp.md).
