---
title: Speicher  Konfiguration
seo-title: Speicher  Konfiguration
description: Zugriff auf die Speicherkonfigurationskonsole
seo-description: Zugriff auf die Speicherkonfigurationskonsole
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Administrator
exl-id: 67de7e26-3f93-4034-9e3a-5c127f7447bc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 5%

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

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]** aus.

So wählen Sie eine andere Speicheroption als das standardmäßige JCR aus:

* Option auswählen
* Geeignete Konfiguration

   * Siehe Details zu [Auswählen von MSRP](msrp.md#select-msrp)
   * Siehe Details zu [Auswahl von DSRP](dsrp.md#select-dsrp)
   * Siehe Details zu [Auswählen von ASRP](asrp.md#select-asrp)

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Über JCR-Speicher {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl das AEM-Repository JCR standardmäßig verwendet wird.

JCR ist *nicht* ein gemeinsamer Speicher, der von der Autoren- und Veröffentlichungsumgebung gemeinsam genutzt wird. Community-Inhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Weitere Informationen finden Sie unter [JCR Store](jsrp.md) .

>[!NOTE]
>
>Das Fehlen des Knotens `srpc` unter `/etc/socialconfig` zeigt den standardmäßigen [JCR-Store](jsrp.md) an.
