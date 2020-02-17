---
title: Upgrade auf AEM 6.5 Communities
seo-title: Upgrade auf AEM 6.5 Communities
description: Aktualisierung von einer früheren Version auf AEM 6.4 Communities
seo-description: Aktualisierung von einer früheren Version auf AEM 6.4 Communities
uuid: 929c3892-1b3b-46a7-8e70-fa6864125911
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: abe5a998-bbe3-4a2b-bcf7-b490a8275219
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Upgrade auf AEM 6.5 Communities{#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Sites können die folgenden Aktionen erforderlich sein, wenn Sie auf AEM Communities 6.5 aktualisieren oder das neueste Feature Pack installieren.

Dieser Abschnitt ist spezifisch für Communities und ergänzt die Informationen unter [Aktualisierung auf AEM 6.5](/help/sites-deploying/upgrade.md) (Plattform).

## Aktualisieren von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Wenn Sie ein neues Communities Feature Pack in einer mit MSRP konfigurierten Bereitstellung installieren, müssen Sie

1. installieren Sie das [neueste Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack)
1. installieren Sie die [neuesten Solr-Konfigurationsdateien](/help/communities/msrp.md#upgrading)
1. reindex MSRPsiehe Abschnitt [MSRP Reindex Tool](/help/communities/msrp.md#msrp-reindex-tool)

### Enablement 2.0 {#enablement}

Ab AEM 6.3 speichern die Aktivierungsfunktionen keine Berichtsdaten mehr in MySQL. MySQL wird nur noch für die Nachverfolgung von SCORM-Inhalten benötigt.

Bitte wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html) , um Hilfe bei der Migration von Inhalten aus Version 1.0 zu erhalten.

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandene UGC beibehalten werden müssen, hängt die Vorgehensweise davon ab, ob die Bereitstellung UGC [lokal](#on-premise-storage) oder in der [Adobe Cloud](#adobe-cloud-storage)gespeichert hat.

### Adobe Cloud-Speicher {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung des Adobe-Cloud-Speichers konfiguriert wurde, wird sie möglicherweise (falsch) so angezeigt, als wäre das gesamte UGC verloren gegangen, da die SRP-Methoden die bereits vorhandene UGC nicht am alten Speicherort finden können.

So gibt es die Möglichkeit, ASRP anzuweisen, auf UGC `AEM 6.0 compatability-mode` zuzugreifen.

Für alle Autoren- und Veröffentlichungsinstanzen von AEM 6.3

* Melden Sie sich mit Administratorrechten an.
* ASRP konfigurieren [](/help/communities/asrp.md)
* Führen Sie die folgenden Schritte aus, um das bereits vorhandene UGC sichtbar zu machen:

   * zur Webkonsole navigieren

      * Beispiel: [https://&lt;Host>:&lt;Port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * AEM Communities Utilities ****-Konfiguration suchen
   * zum Erweitern des Konfigurationsbedienfelds auswählen

      * *uncheck ***`Cloud Storage`**

      * Wählen Sie **Save** aus.


![chlimage_1-176](assets/chlimage_1-176.png)

### Vor-Ort-Speicher {#on-premise-storage}

Wenn die aktualisierte Site keinen Cloud-Speicher verwendet hat, müssen alle bereits vorhandenen UGC konvertiert werden, um der neuen Struktur zu entsprechen, die in AEM 6.1 Communities zur Unterstützung des gemeinsamen Speichers eingeführt wurde.

Zu diesem Zweck ist ein Open Source-Migrationswerkzeug auf GitHub verfügbar:
UGC-Migrationswerkzeug für[AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Beachten Sie bei der Aktualisierung von AEM 6.0 Social Communities auf AEM 6.3 Communities, dass viele APIs in verschiedene Pakete neu organisiert wurden. Die meisten Probleme sollten bei der Verwendung einer IDE zur Anpassung der Communities-Funktionen einfach gelöst werden.

Weitere Informationen zum nicht mehr unterstützten SocialUtils-Paket finden Sie unter [SocialUtils Refactoring](/help/communities/socialutils.md).

Siehe auch [Verwenden von Maven für Communities](/help/communities/maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Social-Komponenten-Framework](/help/communities/scf.md) (SCF) verwendet die Vorlagensprache [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Speicherort, wobei sich die HBS-Komponenten in der Regel in Unterordnern mit dem Namen &quot;hbs&quot;befinden.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, alle JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Das UGC-Migrationswerkzeug für [](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) AEM Communities ist ein Open Source-Migrationswerkzeug, das auf GitHub verfügbar ist und angepasst werden kann, um UGC aus früheren Versionen von AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC von früheren Versionen ist es auch möglich, UGC von einem [SRP](/help/communities/working-with-srp.md) zu einem anderen zu verschieben, z. B. von MSRP zu DSRP.

## Aktualisieren von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Grundsätzlich gibt es drei Generationen von Komponenten aus Gemeinden:

**Gen 1** : ca. CQ 5.4 bis AEM 5.6.0 - dies sind die **Collab** -Komponenten, die UGC im lokalen Repository unter Verwendung der Replikation als Möglichkeit zur plattformübergreifenden Synchronisierung gespeichert haben. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) sowie die Blog-Funktion, die nur in der Autorenumgebung besteht.

**Gen 2** : von AEM 5.6.1 bis AEM 6.1 - dies ist eine Mischung aus **Collab** - und **Social** -Komponenten. Mit AEM 6.0 wurde das neue [Social-Komponenten-Framework](/help/communities/scf.md) (SCF) eingeführt und mit AEM 6.2 wurde ein [gemeinsamer UGC-Store](/help/communities/working-with-srp.md) eingeführt, auf den über einen [Speicherressourcenanbieter](/help/communities/srp.md) (SRP) zugegriffen wird.

**Gen 3** : Ab AEM 6.2 gibt es nur **Social** -Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind und eine Auswahl an SRP für UGC erfordern.
