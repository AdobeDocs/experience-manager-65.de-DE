---
title: Upgrade auf AEM 6.5 Communities
description: Upgrade von einer früheren Version auf AEM 6.5 Communities
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: ea41d35c-967c-4606-b4ec-377e817902e4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Upgrade auf AEM 6.5 Communities {#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Websites können beim Upgrade auf AEM Communities 6.5 oder bei der Installation des neuesten Feature Packs die folgenden Aktionen erforderlich sein:

Dieser Abschnitt ist spezifisch für Communities und ergänzt die Informationen unter [Aktualisierung auf AEM 6.5.1} (Plattform).](/help/sites-deploying/upgrade.md)

## Upgrade von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Bei der Installation eines neuen Communities Feature Packs in einer mit MSRP konfigurierten Implementierung ist Folgendes erforderlich:

1. Installieren Sie das [neueste Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack).
1. Installieren Sie die [neuesten Solr-Konfigurationsdateien](/help/communities/msrp.md#upgrading).
1. Reindex MSRP
Siehe Abschnitt [MSRP-Neuindizierungs-Tool](/help/communities/msrp.md#msrp-reindex-tool).

## Upgrade von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandenes UGC beibehalten werden muss, hängt die Vorgehensweise davon ab, ob die Bereitstellung UGC [On-Premise](#on-premise-storage) oder in der [Adobe-Cloud](#adobe-cloud-storage) gespeichert hat.

### Adobe Cloud Storage {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung des Adobe-Cloud-Speichers konfiguriert wurde, kann es (falsch) so aussehen, als wäre alles UGC verloren gegangen, da die SRP-Methoden die bereits vorhandene benutzergenerierte Seite am alten Speicherort nicht finden können.

Somit besteht die Möglichkeit, ASRP anzuweisen, `AEM 6.0 compatability-mode` für den Zugriff auf UGC zu verwenden.

Für alle AEM 6.3 Autoren- und Veröffentlichungsinstanzen:

* Melden Sie sich mit Administratorrechten an.
* Konfigurieren Sie [ASRP](/help/communities/asrp.md).
* Führen Sie die folgenden Schritte aus, um bereits vorhandene benutzergenerierte Inhalte sichtbar zu machen:

   * Navigieren Sie zur Web-Konsole:

      * Beispiel: [https://&lt;Host>:&lt;Port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)

      * Suchen Sie die Konfiguration **AEM Communities Utilities** .
      * Wählen Sie zum Erweitern des Konfigurationsbereichs aus:

         * *Uncheck* `Cloud Storage`

         * Wählen Sie **Speichern** aus

     ![utilities](assets/utilities.png)

### On-Premise-Speicher {#on-premise-storage}

Wenn die aktualisierte Site keinen Cloud-Speicher verwendet, muss jeder bereits vorhandene benutzergenerierte Speicher entsprechend der neuen Struktur konvertiert werden, die in AEM 6.1 Communities eingeführt wurde, um den gemeinsamen Speicher zu unterstützen.

Zu diesem Zweck ist ein Open-Source-Migrationstool auf GitHub verfügbar:
[AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Beim Upgrade von AEM 6.0 Social Communities auf AEM 6.3 Communities wurden viele APIs in verschiedene Pakete neu organisiert. Die meisten sollten leicht gelöst werden, wenn eine IDE zur Anpassung von Communities-Funktionen verwendet wird.

Weitere Informationen zum veralteten SocialUtils-Paket finden Sie unter [SocialUtils-Refaktorierung](/help/communities/socialutils.md).

Siehe auch [Verwenden von Maven für Communities](/help/communities/maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Social Component Framework](/help/communities/scf.md) (SCF) verwendet die Vorlagensprache [HandlebarsJS](https://handlebarsjs.com/) (HBS) anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Speicherort, wobei die HBS-Komponenten in der Regel in Unterordnern namens &quot;hbs&quot;enthalten waren.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, die gesamte Verwendung von JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein auf GitHub verfügbares Open-Source-Migrationstool, das angepasst werden kann, um benutzergenerierte Inhalte aus früheren Versionen AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC aus früheren Versionen ist es auch möglich, UGC mit dem Tool von einem [SRP](/help/communities/working-with-srp.md) in einen anderen zu verschieben, z. B. von MSRP zu DSRP.

## Upgrade von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Grundsätzlich gibt es drei Generationen von Communities-Komponenten:

**Gen 1**: Ungefähr CQ 5.4 bis AEM 5.6.0 sind dies die **collab** -Komponenten, die UGC im lokalen Repository gespeichert haben, indem sie die Replikation als Möglichkeit zur plattformübergreifenden Synchronisierung von benutzergenerierten Inhalten nutzen. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) und die Blog-Funktion, die nur aus der Autorenumgebung besteht.

**Gen 2**: Von AEM 5.6.1 bis AEM 6.1 ist dies eine Mischung aus **collab** und **social** -Komponenten. Mit AEM Version 6.0 wurde das neue [Social-Komponenten-Framework](/help/communities/scf.md) (SCF) eingeführt und AEM 6.2 wurde ein [gemeinsamer UGC-Speicher](/help/communities/working-with-srp.md) eingeführt, auf den über einen [Speicherressourcenanbieter](/help/communities/srp.md) (SRP) auf UGC zugegriffen wird.

**Gen 3**: Ab AEM 6.2 gibt es nur noch **Social** -Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind und eine Auswahl von SRP für benutzergenerierte Inhalte erfordern.
