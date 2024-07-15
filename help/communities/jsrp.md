---
title: JSRP - JCR Storage Resource Provider
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

# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Über JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Speicheroption (Standard) verwendet, werden Community-Inhalte im JCR gespeichert und benutzergenerierte Inhalte (UGC) können nur von der Autoren- oder Veröffentlichungsinstanz aufgerufen werden, in der sie veröffentlicht wurden.

Aufgrund der Einfachheit der Implementierung ist JSRP am besten für Demonstrations- oder Entwicklungsumgebungen einer Publish-Instanz und einer Autoreninstanz geeignet.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Konfiguration {#configuration}

### JSRP auswählen {#select-jsrp}

Standardmäßig ist JSRP die Speicheroption für UGC.

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Um in der Autorenumgebung auf die Speicherkonfigurationskonsole zuzugreifen

* Von der globalen Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**

* Wählen Sie **[!UICONTROL JCR Storage Resource Provider (JSRP)]** aus

* Klicken Sie auf **[!UICONTROL Übermitteln]**

![jsrp-configuration](assets/jsrp-configuration.png)

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, um sicherzustellen, dass die identische Konfiguration in der Veröffentlichungsumgebung festgelegt ist:

* Von der globalen Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
* Wählen Sie **[!UICONTROL Baum aktivieren]** > **[!UICONTROL Startpfad]**:

   * Navigieren zu `/conf/global/settings/community/srpc/`

* Wählen Sie **[!UICONTROL Activate]** aus.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in die Veröffentlichungsumgebung eingegeben werden, finden Sie unter:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC nicht in JCR sichtbar {#ugc-not-visible-in-jcr}

Stellen Sie sicher, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicher-Ressourcenanbieter JSRP.

Rufen Sie auf allen Autoren- und Publish-AEM-Instanzen erneut die Speicherkonfigurationskonsole auf oder überprüfen Sie das AEM Repository:

* Wenn in JCR [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Er enthält keinen Knoten [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) , d. h. der Speicheranbieter ist JSRP.
   * Wenn der Knoten srpc vorhanden ist und den Knoten [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration) enthält, sollten die Eigenschaften der Standardkonfiguration JSRP als Standardanbieter definieren.

### UGC in Autoreninstanz nicht sichtbar {#ugc-not-visible-on-author-instance}

Das ist kein Fehler. Ein Merkmal von JSRP ist, dass in der Veröffentlichungsumgebung eingegebene Community-Inhalte nur in der Publish-Umgebung sichtbar sind.

### UGC in Publish-Instanz nicht sichtbar {#ugc-not-visible-on-publish-instance}

Wenn eine einzelne Publish-Instanz oder ein Veröffentlichungscluster bereitgestellt ist, befolgen Sie die Anweisungen für &quot;[UGC nicht in JCR](#ugc-not-visible-in-jcr) sichtbar&quot;.

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur auf der Publish-Instanz sichtbar sind, auf der sie veröffentlicht wurde.

Damit UGC in jeder Publish-Instanz sichtbar ist, ist ein Veröffentlichungscluster erforderlich.
