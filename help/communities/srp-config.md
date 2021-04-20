---
title: Speicher  Konfiguration
seo-title: Speicher  Konfiguration
description: Zugriff auf die Datenspeicherung Configuration Console
seo-description: Zugriff auf die Datenspeicherung Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 5%

---


# Speicherkonfiguration {#storage-configuration}

Die Konfiguration der Datenspeicherung ist das Mittel zur Identifizierung der Datenspeicherung, die für Community-Inhalte gewählt wurde, auch als benutzergenerierte Inhalte (UGC) bezeichnet.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des Datenspeicherung Resource Provider (SRP) beim Zugriff auf UGC verwendet werden soll, und muss die bei der Bereitstellung der AEM festgelegte Topologie widerspiegeln.

Eine Diskussion der Optionen für die Datenspeicherung und der Bereitstellungstopologien finden Sie unter:

* [Community Content Store](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Datenspeicherung Configuration Console {#storage-configuration-console}

![jsrp-configuration](assets/jsrp-configuration.png)

In der Autorenkonfiguration, um die Datenspeicherung-Konfigurationskonsole zu erreichen.

* Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Datenspeicherung Configuration]**

So wählen Sie eine andere Datenspeicherung als die Standard-JCR-Option aus:

* Option auswählen
* Passend konfigurieren

   * Siehe Details zu [Auswahl von MSRP](msrp.md#select-msrp)
   * Siehe Details zur Auswahl von DSRP](dsrp.md#select-dsrp)[
   * Siehe Details zur Auswahl von ASRP](asrp.md#select-asrp)[

* Klicken Sie auf **[!UICONTROL Übermitteln]**.

### Informationen zur JCR-Datenspeicherung {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl das AEM Repository JCR standardmäßig verwendet wird.

JCR ist *nicht* ein gemeinsamer Speicher, der von den Autor- und Veröffentlichungs-Umgebung freigegeben wird. Der Community-Inhalt ist nur von der Autor- oder Veröffentlichungsdatei sichtbar, in der er erstellt wurde.

Weitere Informationen finden Sie unter [JCR Store](jsrp.md).

>[!NOTE]
>
>Das Fehlen des Knotens `srpc` unter `/etc/socialconfig` gibt den standardmäßigen [JCR-Speicher](jsrp.md) an.
