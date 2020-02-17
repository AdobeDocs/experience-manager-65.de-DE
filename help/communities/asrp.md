---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# ASRP - Adobe Storage Resource Provider{#asrp-adobe-storage-resource-provider}

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

Die privaten und geheimen Schlüssel werden für alle Report Suites eines Unternehmens freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration{#configuration}

### ASRP auswählen {#select-asrp}

Die [Speicherkonfigurationskonsole](/help/communities/srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die festlegt, welche SRP-Implementierung verwendet werden soll.

**Auf AEM-Autoreninstanz:**

* Wählen Sie in der globalen Navigation (Tools, Communities, Speicherkonfiguration) die Option** Adobe Storage Resource Provider (ASRP).**

![chlimage_1-30](assets/chlimage_1-30.png)

Die folgenden Informationen stammen aus dem Bereitstellungsprozess:

* **Datenzentrum-URL. **Ziehen Sie nach unten, um das von Ihrem Kundenbetreuer identifizierte Produktionsdatencenter auszuwählen.
* **Standard-Berichtssuite. **Geben Sie den Namen der Standard-Report Suite ein.
* **Verbraucherschlüssel**. Geben Sie den Verbraucherschlüssel ein.
* **Geheimnis. **Geben Sie das Geheimnis ein.
* Klicken Sie auf **Übermitteln.**

Vorbereiten der Veröffentlichungsinstanzen:

* [Verschlüsselungsschlüssel replizieren](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Nach dem Senden der Konfiguration die Verbindung testen:

* Wählen Sie **Testkonfiguration**. Testen Sie für jede Autoren- und Veröffentlichungsinstanz die Verbindung zum Rechenzentrum über die Speicherkonfigurationskonsole.

* Stellen Sie sicher, dass die Site-URLs für Profildaten vom Rechenzentrum durch [Externalisierung der Links](#externalize-links)routinemäßig zugänglich sind.

### Crypto-Schlüssel replizieren {#replicate-the-crypto-key}

Der Consumer Key und der Secret Key sind verschlüsselt. Damit die Schlüssel richtig verschlüsselt/entschlüsselt werden können, muss der Master-Granite-Crypto-Schlüssel auf allen AEM-Instanzen gleich sein.

Befolgen Sie die Anweisungen unter Crypto-Schlüssel [replizieren](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Links externalisieren {#externalize-links}

Für korrekte Profil- und Profilbild-Links müssen Sie den Link Externalizer ordnungsgemäß [konfigurieren](/help/sites-developing/externalizer.md).

Stellen Sie sicher, dass es sich bei den Domänen um URLs handelt, die über die Data Center-URL (ASRP-Endpunkt) routingfähig sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihre gehosteten AEM Communities ausgeführt werden, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

Auf AEM-Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu `Tools > Operations > Replication.`
* Wählen Sie **Baum aktivieren.**
* **Startpfad:
**navigieren Sie zu /etc/socialconfig/srpc/
* Deaktivieren Sie die Option **Nur geändert.**
* Wählen Sie **Aktivieren.**

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [](/help/communities/jsrp.md)JCR gespeicherte UGC nicht mehr sichtbar, da keine Synchronisierung der Daten zwischen lokalen Speicher und Cloud-Speicherung stattfindet.

**`AEM Communities Extension`**wurde zuvor in AEM 6.0 Social Communities als Cloud-Dienst eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](/help/communities/srp-config.md).

Aufgrund der neuen Speicherstruktur müssen Sie bei der Aktualisierung von Social Communities auf Communities die [Upgrade](/help/communities/upgrade.md#adobe-cloud-storage) -Anweisungen befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC wird nach der Aktualisierung ausgeblendet {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer vorhandenen AEM 6.0 Social Community-Site durchführen, befolgen Sie die [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage). Andernfalls scheint UGC verloren zu gehen.

### Authentifizierungsfehler {#authentication-errors}

Wenn beim Empfang von Authentifizierungsfehlern für die Data Center-URL die Datei &quot;AEM error.log&quot;Meldungen über statische Zeitstempel enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Verwenden Sie ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) , um alle AEM-Autor- und -Veröffentlichungsserver zeitlich zu synchronisieren.

### Neue Inhalte werden in Suchvorgängen nicht angezeigt {#new-content-does-not-appear-in-searches}

Die Adobe Cloud-Speicherinfrastruktur verwendet *letztendlich Konsistenz* , um ihre Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert einige Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die spätere Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte in Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Vergewissern Sie sich, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Rufen Sie bei allen Autoren- und Veröffentlichungsinstanzen von AEM erneut die Speicherkonfigurationskonsole auf oder überprüfen Sie das AEM-Repository.

In JCR, if [/etc/socialconfig](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* enthält keinen [srpc](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) -Knoten, d. h. der Speicheranbieter ist JSRP.
* Wenn der Knoten srpc vorhanden ist und die Node- [Standardkonfiguration](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)enthält, definieren die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter.

