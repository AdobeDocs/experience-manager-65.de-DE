---
title: ASRP - Adobe Datenspeicherung Resource Provider
seo-title: ASRP - Adobe Datenspeicherung Resource Provider
description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
seo-description: AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher einrichten
uuid: abe47ad9-9f72-4dad-a5e9-6d621a9722d4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 3e81b519-57ca-4ee1-94bd-7adac4605407
docset: aem65
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 1%

---


# ASRP - Adobe Datenspeicherung Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities so konfiguriert ist, dass ASRP als gemeinsamer Speicher verwendet wird, können vom Benutzer generierte Inhalte (UGC) von allen Autor- und Veröffentlichungsinstanzen aus aufgerufen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](/help/communities/working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](/help/communities/topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Site für die Verwendung von ASRP für UGC zu konfigurieren.

* Datenzentrum-URL (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Die Verbraucher- und geheimen Schlüssel werden für alle Report Suites für eine Firma freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration {#configuration}

### ASRP {#select-asrp}

Die [Datenspeicherung Configuration Console](/help/communities/srp-config.md) ermöglicht die Auswahl der Standardkonfiguration der Datenspeicherung, die die zu verwendende Implementierung von SRP identifiziert.

**Auf AEM-Autoreninstanz:**

* Navigieren Sie in der globalen Navigation zu **[!UICONTROL Tools > Communities > Datenspeicherung Configuration]** und wählen Sie **[!UICONTROL Adobe Datenspeicherung Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

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

* Stellen Sie sicher, dass die Site-URLs für Profil-Daten vom Rechenzentrum routinemäßig durch [Externalisieren von Links](#externalize-links) ausgeführt werden können.

### Crypto-Schlüssel {#replicate-the-crypto-key} replizieren

Die Consumer key und der Geheimschlüssel sind verschlüsselt. Damit die Schlüssel richtig verschlüsselt/entschlüsselt werden können, muss der primäre Granite Crypto-Schlüssel auf allen AEM Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Crypto-Schlüssel replizieren](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Externalisieren von Links {#externalize-links}

Stellen Sie für korrekte Profil- und Profil-Bildverknüpfungen sicher, dass Sie [Link Externalizer konfigurieren](/help/sites-developing/externalizer.md) richtig konfigurieren.

Stellen Sie sicher, dass es sich bei den Domänen um URLs handelt, die über die Data Center-URL (ASRP-Endpunkt) routingfähig sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen das gehostete AEM Communities ausgeführt wird, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die gleiche Konfiguration in der Umgebung &quot;Veröffentlichen&quot;zur Verfügung:

Auf AEM-Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**
* Wählen Sie **Baum aktivieren**
* **Pfad** des Beginns: zu  `/conf/global/settings/communities/srpc/`
* Deaktivieren Sie **Nur geändert**
* Wählen Sie **Aktivieren**

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [JCR](/help/communities/jsrp.md) gespeicherte UGC nicht mehr sichtbar, da keine Synchronisierung der Daten zwischen der lokalen Datenspeicherung und der Cloud-Datenspeicherung erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud-Dienst eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Datenspeicherung-Konfigurationskonsole](/help/communities/srp-config.md).

Aufgrund der neuen Datenspeicherung müssen Sie bei der Aktualisierung von Social Communities auf Communities die [upgrade](/help/communities/upgrade.md#adobe-cloud-storage)-Anweisungen befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzergruppen*, *Benutzergruppen* und *die häufig in die Umgebung &quot;Veröffentlichen&quot;eingegeben wurden, finden Sie unter*

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer bestehenden Social Community-Site AEM 6.0 durchführen, befolgen Sie die [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage), sonst scheint UGC verloren zu gehen.

### Authentifizierungsfehler {#authentication-errors}

Wenn beim Empfang von Authentifizierungsfehlern für die Data Center-URL die Datei &quot;error.log&quot;Meldungen über statische Zeitstempel enthält, stellen Sie sicher, dass eine Synchronisierung durchgeführt wird.

Verwenden Sie ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/), um alle AEM Autor- und Veröffentlichungsserver zeitlich zu synchronisieren.

### Neuer Inhalt wird nicht in Suchvorgängen {#new-content-does-not-appear-in-searches} angezeigt

Die Infrastruktur für die Adobe Cloud-Datenspeicherung verwendet *letztendlich Konsistenz*, um ihre Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert einige Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die spätere Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als ein paar Sekunden dauert, bis neue Inhalte in Suchvorgängen angezeigt werden.

### UGC nicht sichtbar in ASRP {#ugc-not-visible-in-asrp}

Vergewissern Sie sich, dass ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfigurationsoption der Datenspeicherung überprüfen. Standardmäßig ist der Datenspeicherung Resource Provider JSRP, nicht ASRP.

Rufen Sie auf allen Instanzen im Autorenmodus AEM Veröffentlichungsmodus erneut die Datenspeicherung Configuration Console auf oder überprüfen Sie das AEM Repository.

Wenn in JCR [/conf/global/settings/Communities](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Enthält keinen [srpc](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp)-Knoten, d. h., der Datenspeicherung-Provider ist JSRP.
* Wenn der Knoten srpc vorhanden ist und den Knoten [defaultconfiguration](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration) enthält, definieren die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter.

