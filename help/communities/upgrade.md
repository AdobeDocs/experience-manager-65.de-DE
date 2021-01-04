---
title: Upgrade auf AEM 6.5 Communities
seo-title: Upgrade auf AEM 6.5 Communities
description: Upgrade von einer früheren Version auf AEM 6.5 Communities
seo-description: Upgrade von einer früheren Version auf AEM 6.5 Communities
uuid: 929c3892-1b3b-46a7-8e70-fa6864125911
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: abe5a998-bbe3-4a2b-bcf7-b490a8275219
docset: aem65
translation-type: tm+mt
source-git-commit: 612d102b5925704ce459ad818554e487ec0d5355
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 4%

---


# Upgrade auf AEM 6.5 Communities {#upgrading-to-aem-communities}

Abhängig von der Topologie und den Funktionen der einzelnen Sites können die folgenden Aktionen erforderlich sein, wenn Sie auf AEM Communities 6.5 aktualisieren oder das neueste Feature Pack installieren.

Dieser Abschnitt ist spezifisch für Communities und ergänzt die Informationen unter [Upgrade auf AEM 6.5](/help/sites-deploying/upgrade.md) (Plattform).

## Aktualisieren von AEM 6.1 oder höher {#upgrading-from-aem-or-later}

### Reindex Solr {#reindex-solr}

Wenn Sie ein neues Communities Feature Pack in einer mit MSRP konfigurierten Bereitstellung installieren, müssen Sie Folgendes tun:

1. Installieren Sie das [aktuelle Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack).
1. Installieren Sie die [neuesten Solr-Konfigurationsdateien](/help/communities/msrp.md#upgrading).
1. Reindex MSRP
siehe Abschnitt [MSRP Reindex Tool](/help/communities/msrp.md#msrp-reindex-tool).

### Aktivierung 2.0 {#enablement}

Ab AEM 6.3 werden in den Aktivierungsfunktionen keine Informationen mehr zum Berichte in MySQL gespeichert. MySQL wird nur noch für die Nachverfolgung von SCORM-Inhalten benötigt.

Bitte wenden Sie sich an [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), um Hilfe bei der Migration von Inhalten aus Version 1.0 zu erhalten.

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

Wenn bereits vorhandene UGC beibehalten werden müssen, hängt die Vorgehensweise davon ab, ob die Bereitstellung UGC [lokal](#on-premise-storage) oder in der [Adobe Cloud](#adobe-cloud-storage) gespeichert hat.

### Adobe Cloud-Datenspeicherung {#adobe-cloud-storage}

Wenn die aktualisierte Site für die Verwendung der Adobe Cloud-Datenspeicherung konfiguriert wurde, wird sie möglicherweise (falsch) so angezeigt, als wäre der gesamte UGC verloren gegangen, da die SRP-Methoden nicht in der Lage sind, die bereits vorhandene UGC am alten Speicherort zu finden.

So gibt es die Möglichkeit, ASRP anzuweisen, `AEM 6.0 compatability-mode` für den Zugriff auf UGC zu verwenden.

Für alle AEM 6.3 Autoren- und Veröffentlichungsinstanzen:

* Melden Sie sich mit Administratorrechten an.
* Konfigurieren Sie [ASRP](/help/communities/asrp.md).
* Führen Sie die folgenden Schritte aus, um das bereits vorhandene UGC sichtbar zu machen:

   * Gehen Sie zur Webkonsole:

      * Beispiel: [https://&lt;host>:&lt;port>/system/console/configMgr](https://localhost:4502/system/console/configMgr)

      * Suchen Sie nach der Konfiguration **AEM Communities Utilities**.
      * Zum Erweitern des Konfigurationsbedienfelds wählen:

         * *Deaktivieren* `Cloud Storage`

         * Wählen Sie **Speichern** aus

      ![utilities](assets/utilities.png)


### Lokale Datenspeicherung {#on-premise-storage}

Wenn die aktualisierte Site keine Cloud-Datenspeicherung verwendet hat, müssen alle bereits vorhandenen UGC entsprechend der neuen Struktur konvertiert werden, die in AEM 6.1 Communities eingeführt wurde, um den gemeinsamen Speicher zu unterstützen.

Zu diesem Zweck ist ein Open Source-Migrationswerkzeug auf GitHub verfügbar:
[AEM Communities UGC-Migrationswerkzeug](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java-APIs {#java-apis}

Beachten Sie bei der Aktualisierung von AEM 6.0 Social Communities auf AEM 6.3 Communities, dass viele APIs in verschiedene Pakete umstrukturiert wurden. Die meisten Probleme sollten bei der Verwendung einer IDE zur Anpassung der Communities-Funktionen einfach gelöst werden.

Weitere Informationen zum nicht mehr unterstützten SocialUtils-Paket finden Sie unter [SocialUtils Refactoring](/help/communities/socialutils.md).

Siehe auch [Verwenden von Maven für Communities](/help/communities/maven.md).

### Keine JSP-Komponentenvorlagen {#no-jsp-component-templates}

Das [Framework für soziale Komponenten](/help/communities/scf.md) (SCF) verwendet die Vorlagensprache [HandlebarsJS](https://www.handlebarsjs.com/) (HBS) anstelle von Java Server Pages (JSP), die vor AEM 6.0 verwendet wurden.

In AEM 6.0 blieben die JSP-Komponenten neben den neuen HBS-Framework-Komponenten am selben Ort, wobei sich die HBS-Komponenten in der Regel in Unterordnern mit dem Namen &quot;hbs&quot;befanden.

Ab AEM 6.1 wurden die JSP-Komponenten vollständig entfernt. Für Communities wird empfohlen, alle JSP-Komponenten durch SCF-Komponenten zu ersetzen.

## AEM Communities UGC Migration Tool {#aem-communities-ugc-migration-tool}

Das [AEM Communities UGC Migration Tool](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) ist ein Open-Source-Migrationswerkzeug, das auf GitHub verfügbar ist und angepasst werden kann, um UGC aus früheren Versionen AEM Social Communities zu exportieren und in AEM Communities 6.1 oder höher zu importieren.

Zusätzlich zum Verschieben von UGC von früheren Versionen ist es auch möglich, UGC von [SRP](/help/communities/working-with-srp.md) in eine andere zu verschieben, z. B. von MSRP zu DSRP.

## Aktualisieren von AEM 5.6.1 oder früher {#upgrading-from-aem-or-earlier}

Grundsätzlich gibt es drei Generationen von Komponenten aus Gemeinden:

**Gen 1**: Ungefähr zwischen CQ 5.4 und AEM 5.6.0 sind dies die  **** Kollaborkomponenten, die UGC im lokalen Repository gespeichert haben, wobei die Replikation als Möglichkeit zur plattformübergreifenden Synchronisierung von UGC genutzt wird. Weitere Unterschiede betreffen die Implementierung mit Java Server Pages (JSP) sowie die Blog-Funktion, die nur das Authoring in der Authoring-Umgebung beinhaltet.

**Gen 2**: Von AEM 5.6.1 bis AEM 6.1 ist das eine Mischung aus  **** Kollaborateuren und  **** Social-Komponenten. AEM 6.0 wurde das neue [Social-Komponenten-Framework](/help/communities/scf.md) (SCF) eingeführt und AEM 6.2 hat einen [Common UGC-Speicher](/help/communities/working-with-srp.md) eingeführt, auf den mit einem [Datenspeicherung-Ressourcenanbieter](/help/communities/srp.md) (SRP) auf UGC zugegriffen wird.

**Gen 3**: Ab AEM 6.2 gibt es nur noch  **** Social-Komponenten, die in SCF als Handlebars (HBS)-Komponenten implementiert sind und eine Auswahl an SRP für UGC erfordern.
