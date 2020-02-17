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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Speicherkonfiguration {#storage-configuration}

Die Speicherkonfiguration ist das Mittel zur Identifizierung des Speicherplatzes, der für Community-Inhalte ausgewählt wurde, auch als benutzergenerierter Inhalt (UGC) bezeichnet.

Diese Einstellung informiert den AEM Communities-Code darüber, welche Implementierung des SRP (Storage Resource Provider) beim Zugriff auf UGC verwendet werden soll, und muss die bei der Bereitstellung von AEM festgelegte Topologie widerspiegeln.

Eine Diskussion der Speicheroptionen und Bereitstellungstopologien finden Sie unter

* [Community Content Store](working-with-srp.md)
* [Empfohlene Topologien](topologies.md)

## Speicherkonfigurationskonsole {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

In der Autorenumgebung zur Speicherkonfigurationskonsole

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Speicherkonfiguration]**

So wählen Sie eine andere Speicheroption als die Standard-JCR-Option aus:

* Option auswählen
* Passend konfigurieren

   * Siehe Details zur [Auswahl von MSRP](msrp.md#select-msrp)
   * Siehe Details zur [Auswahl von DSRP](dsrp.md#select-dsrp)
   * Siehe Details zur [Auswahl von ASRP](asrp.md#select-asrp)

* Klicken Sie auf **[!UICONTROL Übermitteln]**

### JCR-Speicher {#about-jcr-storage}

Beachten Sie, dass bei fehlender Auswahl standardmäßig das AEM-Repository JCR verwendet wird.

JCR ist *kein* gemeinsamer Speicher für Autor- und Veröffentlichungsumgebungen. Gemeinschaftsinhalte sind nur in der Autoren- oder Veröffentlichungsumgebung sichtbar, in der sie erstellt wurden.

Weitere Informationen finden Sie im [JCR Store](jsrp.md) .

>[!NOTE]
>
>Das Fehlen des Knotens `srpc`unter `/etc/socialconfig` gibt den standardmäßigen [JCR-Store](jsrp.md)an.

