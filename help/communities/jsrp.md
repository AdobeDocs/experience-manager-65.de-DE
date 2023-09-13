---
title: JSRP - JCR Storage Resource Provider
description: JSRP ist am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 873e013c-a2da-4b37-b0e3-56bdf240004a
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 1%

---

# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Über JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Speicheroption (Standard) verwendet, werden Community-Inhalte im JCR gespeichert und benutzergenerierte Inhalte (UGC) können nur von der Autoren- oder Veröffentlichungsinstanz aufgerufen werden, in der sie veröffentlicht wurden.

Aufgrund der Einfachheit der Implementierung ist JSRP am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](topologies.md).

## Konfiguration {#configuration}

### JSRP auswählen {#select-jsrp}

Standardmäßig ist JSRP die Speicheroption für UGC.

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

Um in der Autorenumgebung auf die Speicherkonfigurationskonsole zuzugreifen

* Über die globale Navigation: **[!UICONTROL Instrumente]** > **[!UICONTROL Communities]** > **[!UICONTROL Speicherkonfiguration]**

* Auswählen **[!UICONTROL JCR Storage Resource Provider (JSRP)]**

* Klicken Sie auf **[!UICONTROL Übermitteln]**

![jsrp-configuration](assets/jsrp-configuration.png)

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, um sicherzustellen, dass die identische Konfiguration in der Veröffentlichungsumgebung festgelegt ist:

* Über die globale Navigation: **[!UICONTROL Instrumente]** > **[!UICONTROL Implementierung]** > **[!UICONTROL Replikation]**
* Auswählen **[!UICONTROL Baum aktivieren]** > **[!UICONTROL Startpfad]**:

   * Navigieren Sie zu `/conf/global/settings/community/srpc/`

* Auswählen **[!UICONTROL Aktivieren]**

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, die häufig in die Veröffentlichungsumgebung eingegeben werden, besuchen Sie:

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC nicht in JCR sichtbar {#ugc-not-visible-in-jcr}

Stellen Sie sicher, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicher-Ressourcenanbieter JSRP.

Rufen Sie auf allen Instanzen im Autoren- und Veröffentlichungsmodus AEM die Konsole Speicherkonfiguration erneut auf oder überprüfen Sie das AEM Repository:

* Wenn in JCR [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Sie enthält keine [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) Knoten bedeutet dies, dass der Speicheranbieter JSRP ist.
   * Wenn der Knoten srpc vorhanden ist und den Knoten enthält [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration)festgelegt ist, sollten die Eigenschaften der Standardkonfiguration JSRP als Standardanbieter definieren.

### UGC in Autoreninstanz nicht sichtbar {#ugc-not-visible-on-author-instance}

Das ist kein Fehler. Ein Merkmal von JSRP ist, dass in der Veröffentlichungsumgebung eingegebene Community-Inhalte nur in der Veröffentlichungsumgebung sichtbar sind.

### UGC in Veröffentlichungsinstanz nicht sichtbar {#ugc-not-visible-on-publish-instance}

Wenn eine einzelne Veröffentlichungsinstanz oder ein Veröffentlichungscluster bereitgestellt ist, befolgen Sie die Anweisungen für [UGC nicht in JCR sichtbar](#ugc-not-visible-in-jcr).

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur in der Veröffentlichungsinstanz sichtbar sind, in der sie veröffentlicht wurde.

Damit UGC in jeder Veröffentlichungsinstanz sichtbar ist, ist ein Veröffentlichungscluster erforderlich.
