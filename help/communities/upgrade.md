---
title: Aktualisieren auf AEM 6.5 Communities
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

# Aktualisieren auf AEM 6.5 Communities {#upgrading-to-aem-communities}

Je nach Topologie und Funktionen der einzelnen Sites sind beim Upgrade auf AEM Communities 6.5 oder beim Installieren des neuesten Feature Packs möglicherweise die folgenden Aktionen erforderlich.

Dieser Abschnitt gilt speziell für Communities und ergänzt die Informationen unter [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md) (Plattform).

## Aktualisieren von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Solr neu indizieren {#reindex-solr}

Bei der Installation eines neuen Communities Feature Packs auf einer mit MSRP konfigurierten Bereitstellung müssen folgende Schritte ausgeführt werden:

1. Installieren Sie [neueste Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack).
1. Installieren Sie die [neuesten Solr-Konfigurationsdateien](/help/communities/msrp.md#upgrading).
1. MSRP neu indizieren
Siehe Abschnitt [MSRP Reindex Tool](/help/communities/msrp.md#msrp-reindex-tool).

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandener benutzergenerierter Inhalt beibehalten werden muss, hängt die Möglichkeit dazu davon ab, ob der benutzergenerierte Inhalt in der Bereitstellung [On-Premise](#on-premise-storage) oder in der [Adobe-Cloud gespeichert &#x200B;](#adobe-cloud-storage).

### Adobe-Cloud-Speicher {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung des Adobe-Cloud-Speichers konfiguriert wurde, kann sie (falsch) so aussehen, als ob der gesamte benutzergenerierte Inhalt (UGC) verloren gegangen ist, da die SRP-Methoden den bereits vorhandenen benutzergenerierten Inhalt (UGC) nicht am alten Speicherort finden können.

Daher besteht die Möglichkeit, ASRP anzuweisen, `AEM 6.0 compatability-mode` für den Zugriff auf benutzergenerierten Inhalt zu verwenden.

Für alle AEM 6.3-Autoren- und Veröffentlichungsinstanzen:

* Melden Sie sich mit Administratorrechten an.
* Konfigurieren Sie [ASRP](/help/communities/asrp.md).
* Führen Sie die folgenden Schritte aus, um bereits vorhandenen benutzergenerierten Inhalt sichtbar zu machen:

   * Navigieren Sie zur Web-Konsole:

      * Beispiel: [https://&lt;Host>:&lt;Port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)

      * Suchen Sie die Konfiguration für **AEM Communities Utilities**.
      * Wählen Sie aus, um das Konfigurationsbedienfeld zu erweitern:

         * *Deaktivieren* `Cloud Storage`

         * Wählen Sie **Speichern** aus

     ![Dienstprogramme](assets/utilities.png)

### On-Premise-Speicher {#on-premise-storage}

Wenn die aktualisierte Site keinen Cloud-Speicher verwendete, müssen alle bereits vorhandenen benutzergenerierten Inhalte konvertiert werden, damit sie der neuen Struktur entsprechen, die in AEM 6.1 Communities zur Unterstützung des gemeinsamen Speichers eingeführt wurde.

Zu diesem Zweck ist auf GitHub ein Open-Source-Migrations-Tool verfügbar:
[AEM Communities UGC-Migrations-Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Nach der Aktualisierung von AEM 6.0 Social Communities auf AEM 6.3 Communities wurden viele APIs in verschiedene Pakete neu organisiert. Die meisten Probleme sollten bei der Verwendung einer IDE zur Anpassung von Communities-Funktionen einfach behoben werden können.

Weitere Informationen zum veralteten SocialUtils-Paket finden Sie unter [SocialUtils-Refaktorierung](/help/communities/socialutils.md).

Siehe auch [Verwenden von Maven für Communities](/help/communities/maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Social Component Framework](/help/communities/scf.md) (SCF) verwendet die Vorlagensprache [HandlebarsJS](https://handlebarsjs.com/) (HBS) anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten zusammen mit den neuen HBS-Framework-Komponenten am selben Speicherort, wobei die HBS-Komponenten normalerweise in Unterordnern namens „hbs“ enthalten sind.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, alle Verwendungen von JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC-Migrations-Tool {#aem-communities-ugc-migration-tool}

Das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein auf GitHub verfügbares Open-Source-Migrations-Tool, das so angepasst werden kann, dass es UGC aus früheren Versionen von AEM Social Communities exportiert und in AEM Communities 6.1 oder höher importiert.

Zusätzlich zum Verschieben von benutzergenerierten Inhalten aus früheren Versionen ist es auch möglich, mit dem Tool benutzergenerierten Inhalt von einem [SRP](/help/communities/working-with-srp.md) in ein anderes zu verschieben, z. B. von MSRP in DSRP.

## Upgrade von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Konzeptionell gibt es drei Generationen von Communitys :

**Gen 1**: Zwischen CQ 5.4 und AEM 5.6.0 sind dies die **collab**-Komponenten, die UGC im lokalen Repository mithilfe von Replikation zur plattformübergreifenden Synchronisierung von UGC gespeichert haben. Weitere Unterschiede bestehen in der Implementierung mithilfe von Java Server Pages (JSP) und der Blog-Funktion, die das Authoring nur in der Autorenumgebung umfasst.

**Gen 2**: Von AEM 5.6.1 bis AEM 6.1 ist dies eine Mischung aus **collab** und **social** Komponenten. Mit AEM 6.0 wurde das neue [Social Component Framework](/help/communities/scf.md) (SCF) eingeführt, und mit AEM 6.2 wurde ein [gemeinsamer UGC-Speicher](/help/communities/working-with-srp.md) eingeführt, dem der UGC über einen [Speicherressourcenanbieter](/help/communities/srp.md) (SRP) aufgerufen wird.

**Gen 3**: Ab AEM 6.2 gibt es nur noch **Social-**-Komponenten, die in SCF als Handlebars-Komponenten (HBS) implementiert sind und eine Auswahl von SRP für UGC erfordern.
