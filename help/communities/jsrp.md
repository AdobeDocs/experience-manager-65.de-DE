---
title: JSRP - JCR-Speicherressourcenanbieter
description: JSRP eignet sich am besten für Demonstrations- oder Entwicklungsumgebungen einer Publish-Instanz und einer Autoreninstanz
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 873e013c-a2da-4b37-b0e3-56bdf240004a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---

# JSRP - JCR-Speicherressourcenanbieter {#jsrp-jcr-storage-resource-provider}

## Über JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Speicheroption (Standard) verwendet, werden Community-Inhalte im JCR gespeichert und benutzergenerierte Inhalte (User-Generated Content, UGC) sind nur über die Autoren- oder Veröffentlichungsinstanz zugänglich, an die sie gesendet wurden.

Aufgrund der Einfachheit der Bereitstellung eignet sich JSRP am besten für Demonstrations- oder Entwicklungsumgebungen einer Publish-Instanz und einer Autoreninstanz.

Siehe auch [Merkmale von SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Konfiguration {#configuration}

### JSRP auswählen {#select-jsrp}

Standardmäßig ist JSRP die Speicheroption für benutzergenerierten Inhalt.

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen -Speicherkonfiguration, die angibt, welche Implementierung von SRP verwendet werden soll.

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Speicherkonfigurationskonsole zu gelangen

* Über die globale Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**

* Wählen Sie **[!UICONTROL JCR-Speicherressourcenanbieter (JSRP)]**

* Klicken Sie auf **[!UICONTROL Übermitteln]**

![jsrp-configuration](assets/jsrp-configuration.png)

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, stellen Sie sicher, dass in der Veröffentlichungsumgebung eine identische Konfiguration festgelegt ist:

* Über die globale Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
* Wählen Sie **[!UICONTROL Baum aktivieren]** > **[!UICONTROL Startpfad]**:

   * Navigieren zu `/conf/global/settings/community/srpc/`

* Wählen Sie **[!UICONTROL Aktivieren]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC nicht im JCR sichtbar {#ugc-not-visible-in-jcr}

Stellen Sie sicher, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Standardmäßig ist der Speicherressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Publish AEM-Instanzen die Speicherkonfigurationskonsole erneut auf, oder überprüfen Sie das AEM-Repository:

* Im JCR, wenn [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Er enthält keinen &quot;[&quot;-](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc), was bedeutet, dass der Speicheranbieter JSRP ist.
   * Wenn der srpc-Knoten vorhanden ist und den Knoten [defaultConfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der defaultConfiguration JSRP als Standardanbieter definieren.

### UGC in der Autoreninstanz nicht sichtbar {#ugc-not-visible-on-author-instance}

Das ist kein Bug. Ein Merkmal von JSRP ist, dass Community-Inhalte, die in die Publishing-Umgebung eingegeben werden, nur in der Publish-Umgebung sichtbar sind.

### UGC ist auf der Publish-Instanz nicht sichtbar {#ugc-not-visible-on-publish-instance}

Wenn eine einzelne Publish-Instanz oder ein Veröffentlichungs-Cluster bereitgestellt wird, befolgen Sie die Anweisungen für [UGC nicht im JCR sichtbar](#ugc-not-visible-in-jcr).

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur in der Publish-Instanz sichtbar sind, auf der sie veröffentlicht wurden.

Damit UGC in jeder Publish-Instanz sichtbar ist, ist ein Veröffentlichungs-Cluster erforderlich.
