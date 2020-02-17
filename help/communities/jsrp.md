---
title: JSRP - JCR Storage Resource Provider
seo-title: JSRP - JCR Storage Resource Provider
description: JSRP ist im Allgemeinen am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet
seo-description: JSRP ist im Allgemeinen am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
translation-type: tm+mt
source-git-commit: aa2c75e061e00ba74d54843a5f35bb7d82d12a92

---


# JSRP - JCR Storage Resource Provider {#jsrp-jcr-storage-resource-provider}

## Informationen zu JSRP {#about-jsrp}

Wenn AEM Communities JSRP als Speicheroption (Standard) verwendet, werden Community-Inhalte in JCR gespeichert. Benutzergenerierte Inhalte (UGC) können nur von der Autor- oder Veröffentlichungsinstanz aufgerufen werden, in der sie veröffentlicht wurden.

Aufgrund der einfachen Bereitstellung ist JSRP im Allgemeinen am besten für Demonstrations- oder Entwicklungsumgebungen einer Veröffentlichungsinstanz und einer Autoreninstanz geeignet.

Siehe auch [Eigenschaften der SRP-Optionen](working-with-srp.md#characteristics-of-srp-options) und der [empfohlenen Topologien](topologies.md).

## Konfiguration{#configuration}

### JSRP auswählen {#select-jsrp}

Standardmäßig ist JSRP die Speicheroption für UGC.

Die [Speicherkonfigurationskonsole](srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die festlegt, welche SRP-Implementierung verwendet werden soll.

In der Autorenumgebung zur Speicherkonfigurationskonsole

* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Communities > Speicherkonfiguration]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Select **[!UICONTROL JCR Storage Resource Provider (JSRP)]**
* Klicken Sie auf **[!UICONTROL Übermitteln]**

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

Während JSRP die Standardkonfiguration ist, stellen Sie sicher, dass die gleiche Konfiguration in der Veröffentlichungsumgebung festgelegt ist:

* Beim Autor:

   * Aus globaler Navigation: **[!UICONTROL Werkzeuge > Bereitstellung > Replikation]**
   * Baumstruktur **[!UICONTROL aktivieren]**
   * **[!UICONTROL Startpfad]**:

      * Navigieren zu `/conf/global/settings/community/srpc/`
   * Aktivieren **[!UICONTROL auswählen]**


## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](sync.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)

## Fehlerbehebung {#troubleshooting}

### UGC in JCR nicht sichtbar {#ugc-not-visible-in-jcr}

Vergewissern Sie sich, dass JSRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Der Speicherressourcenanbieter ist standardmäßig JSRP.

Gehen Sie bei allen Autoren- und Veröffentlichungsinstanzen von AEM erneut zur Speicherkonfigurationskonsole oder überprüfen Sie das AEM-Repository:

* in JCR, if [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * Enthält keinen [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) -Knoten, d. h. der Speicheranbieter ist JSRP
   * Wenn der Knoten srpc vorhanden ist und die Node- [Standardkonfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration)enthält, sollten die Eigenschaften der Standardkonfiguration JSRP als Standardanbieter definieren

### UGC auf Autoreninstanz nicht sichtbar {#ugc-not-visible-on-author-instance}

Das ist kein Fehler. Charakteristisch für JSRP ist, dass in der Veröffentlichungsumgebung eingegebene Community-Inhalte nur in der Veröffentlichungsumgebung sichtbar sind.

### UGC in Veröffentlichungsinstanz nicht sichtbar {#ugc-not-visible-on-publish-instance}

Wenn eine einzelne Veröffentlichungsinstanz oder ein Veröffentlichungscluster bereitgestellt ist, befolgen Sie die Anweisungen für [UGC in JCR](#ugc-not-visible-in-jcr)nicht sichtbar.

Wenn eine Veröffentlichungsfarm bereitgestellt wird, ist ein Merkmal von JSRP, dass Community-Inhalte nur auf der Veröffentlichungsinstanz sichtbar sind, auf der sie veröffentlicht wurden.

Damit UGC von jeder Veröffentlichungsinstanz aus sichtbar sein kann, ist ein Veröffentlichungscluster erforderlich.
