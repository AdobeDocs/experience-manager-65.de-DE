---
title: ASRP - Adobe Datenspeicherung Resource Provider
seo-title: ASRP - Adobe Datenspeicherung Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
uuid: abe47ad9-9f72-4dad-a5e9-6d621a9722d4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 3e81b519-57ca-4ee1-94bd-7adac4605407
docset: aem65
translation-type: tm+mt
source-git-commit: 85f3b8f2a5f079954f4907037c1c722a6b25fd91

---


# ASRP - Adobe Datenspeicherung Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities so konfiguriert ist, dass ASRP als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](/help/communities/working-with-srp.md#characteristics-of-srp-options) und der [empfohlenen Topologien](/help/communities/topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Site für die Verwendung von ASRP für UGC zu konfigurieren.

* Datenzentrum-URL (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Die Verbraucher- und geheimen Schlüssel werden für alle Report Suites für eine Firma freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration{#configuration}

### ASRP auswählen {#select-asrp}

Die [Datenspeicherung Configuration Console](/help/communities/srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die festlegt, welche SRP-Implementierung verwendet werden soll.

**Auf AEM-Autoreninstanz:**

* Navigieren Sie zur globalen Navigation zu **[!UICONTROL Extras > Communities > Datenspeicherung Configuration]** und wählen Sie **[!UICONTROL Adobe Datenspeicherung Resource Provider (ASRP)]**.

![chlimage_1-30](assets/chlimage_1-30.png)

Die folgenden Informationen stammen aus dem Bereitstellungsprozess:

* **Datenzentrum-URL**: Ziehen Sie den Mauszeiger, um das von Ihrem Kundenbetreuer identifizierte Produktionsdatencenter auszuwählen.
* **Standard-Report Suite**: Geben Sie den Namen der Standard-Report Suite ein.
* **Consumer key**: Geben Sie die Consumer key ein.
* **Geheim**: Geben Sie das Geheimnis ein.
* Klicken Sie auf **Übermitteln**.

Vorbereiten der Veröffentlichungsinstanzen:

* [Kryptoschlüssel replizieren](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Nach dem Senden der Konfiguration die Verbindung testen:

* Wählen Sie **Testkonfiguration**.

   Testen Sie für jede Instanz im Autorenmodus und für jede Instanz im Veröffentlichungsmodus die Datenspeicherung Configuration Console.

* Stellen Sie sicher, dass die Site-URLs für Profil-Daten vom Rechenzentrum routingfähig sind, indem Sie Links [externalisieren](#externalize-links).

### Crypto-Schlüssel replizieren {#replicate-the-crypto-key}

Die Consumer key und der Geheimschlüssel sind verschlüsselt. Damit die Schlüssel richtig verschlüsselt/entschlüsselt werden können, muss der Master-Granite-Crypto-Schlüssel auf allen AEM-Instanzen gleich sein.

Befolgen Sie die Anweisungen unter Crypto-Schlüssel [replizieren](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Links externalisieren {#externalize-links}

Stellen Sie für korrekte Profil- und Profil-Bildverknüpfungen sicher, dass Sie den Link Externalizer ordnungsgemäß [konfigurieren](/help/sites-developing/externalizer.md).

Stellen Sie sicher, dass es sich bei den Domänen um URLs handelt, die über die Data Center-URL (ASRP-Endpunkt) routingfähig sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihre gehosteten AEM Communities ausgeführt werden, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;zur Verfügung:

Auf AEM-Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools > Vorgänge > Replikation]**.
* Baumstruktur **aktivieren**
* **Pfad** des Beginns: zu `/etc/socialconfig/srpc/`
* Auswahl **nur geändert aufheben**
* Aktivieren **auswählen**

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [JCR](/help/communities/jsrp.md) gespeicherte UGC nicht mehr sichtbar, da keine Synchronisierung der Daten zwischen der lokalen Datenspeicherung und der Cloud-Datenspeicherung erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud-Dienst eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Datenspeicherung Configuration Console](/help/communities/srp-config.md).

Aufgrund der neuen Datenspeicherung müssen Sie bei der Aktualisierung von Social Communities auf Communities die [Upgrade](/help/communities/upgrade.md#adobe-cloud-storage) -Anweisungen befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Profilen* und *Benutzergruppen*, die häufig in der Umgebung zur Veröffentlichung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC wird nach der Aktualisierung ausgeblendet {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer vorhandenen AEM 6.0 Social Community-Site durchführen, befolgen Sie die [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage). Andernfalls scheint UGC verloren zu gehen.

### Authentifizierungsfehler {#authentication-errors}

Wenn beim Empfang von Authentifizierungsfehlern für die Data Center-URL die Datei &quot;AEM error.log&quot;Meldungen über statische Zeitstempel enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Verwenden Sie ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) , um alle AEM-Autor- und -Veröffentlichungsserver zeitlich zu synchronisieren.

### Neue Inhalte werden in Suchvorgängen nicht angezeigt {#new-content-does-not-appear-in-searches}

Die Adobe Cloud-Datenspeicherung-Infrastruktur verwendet *letztendlich Konsistenz* , um ihre Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert einige Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die spätere Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte in Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Vergewissern Sie sich, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfigurationsoption der Datenspeicherung überprüfen. Standardmäßig ist der Datenspeicherung Resource Provider JSRP, nicht ASRP.

Rufen Sie bei allen Autoren- und Veröffentlichungsinstanzen von AEM erneut die Datenspeicherung Configuration Console auf oder überprüfen Sie das AEM-Repository.

In JCR, if [/etc/socialconfig](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Enthält keinen [srpc](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten, bedeutet dies, dass der Datenspeicherung-Provider JSRP ist.
* Wenn der Knoten srpc vorhanden ist und die Node- [Standardkonfiguration](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)enthält, definieren die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter.

