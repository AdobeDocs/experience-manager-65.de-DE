---
title: ASRP - Adobe Storage Resource Provider
seo-title: ASRP - Adobe Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: abe47ad9-9f72-4dad-a5e9-6d621a9722d4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 3e81b519-57ca-4ee1-94bd-7adac4605407
docset: aem65
role: Admin
exl-id: 6430ed96-5d96-41b6-866f-90b34ff84f7a
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 1%

---

# ASRP - Adobe Storage Resource Provider {#asrp-adobe-storage-resource-provider}

## Über ASRP {#about-asrp}

Wenn AEM Communities für die Verwendung von ASRP als gebräuchlicher Speicher konfiguriert ist, kann von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte (UGC) zugegriffen werden, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Eigenschaften der SRP-Optionen](/help/communities/working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](/help/communities/topologies.md).

## Voraussetzungen {#requirements}

Für die Verwendung von ASRP ist eine zusätzliche Lizenz erforderlich.

Wenden Sie sich an Ihren Kundenbetreuer, um Ihre AEM Communities-Website für die Verwendung von ASRP für UGC zu konfigurieren:

* URL des Rechenzentrums (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Der Verbraucher- und der geheime Schlüssel werden für alle Report Suites eines Unternehmens freigegeben. Pro Mandant gibt es eine Report Suite.

## Konfiguration {#configuration}

### ASRP auswählen {#select-asrp}

Die [Speicherkonfigurationskonsole](/help/communities/srp-config.md) ermöglicht die Auswahl der standardmäßigen Speicherkonfiguration, die angibt, welche SRP-Implementierung verwendet werden soll.

**In der AEM-Autoreninstanz:**

* Navigieren Sie von der globalen Navigation zu **[!UICONTROL Tools > Communities > Speicherkonfiguration]** und wählen Sie **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

Die folgenden Informationen stammen aus dem Bereitstellungsprozess:

* **Data Center URL**: Pulldown zur Auswahl des Produktionsdatencenters, das von Ihrem Kundenbetreuer identifiziert wird.
* **Standard-Report Suite**: Geben Sie den Namen der Standard-Report Suite ein.
* **Consumer Key**: Geben Sie den Consumer-Schlüssel ein.
* **Geheimnis**: Geben Sie das Geheimnis ein.
* Klicken Sie auf **Übermitteln**.

Bereiten Sie die Veröffentlichungsinstanzen vor:

* [Replizieren des Kryptoschlüssels](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Testen Sie nach dem Senden der Konfiguration die Verbindung:

* Auswählen **Testkonfiguration**.

   Testen Sie für jede Autoren- und Veröffentlichungsinstanz die Verbindung zum Rechenzentrum über die Konsole Speicherkonfiguration .

* Stellen Sie sicher, dass die Site-URLs für Profildaten vom Rechenzentrum routbar sind durch [Externalisieren von Links](#externalize-links).

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Der Consumer Key und der Secret Key sind verschlüsselt. Damit die Schlüssel ordnungsgemäß verschlüsselt/entschlüsselt werden können, muss der primäre Granite-Crypto-Schlüssel auf allen AEM Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Replizieren des Crypto-Schlüssels](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Externe Links {#externalize-links}

Stellen Sie für korrekte Profil- und Profilbildlinks sicher, dass [Link Externalizer konfigurieren](/help/sites-developing/externalizer.md).

Stellen Sie sicher, dass die Domänen URLs sind, die über die Data Center URL (ASRP-Endpunkt) routbar sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihr gehosteter AEM Communities ausgeführt wird, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

In der AEM-Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Replikation]**
* Auswählen **Baum aktivieren**
* **Startpfad**: Durchsuchen nach `/conf/global/settings/communities/srpc/`
* Auswahl aufheben **Nur geändert**
* Auswählen **Aktivieren**

## Upgrade von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, werden alle bereits in gespeicherten UGCs [JCR](/help/communities/jsrp.md) nicht mehr sichtbar ist, da keine Synchronisierung der Daten zwischen On-Premise-Speicher und Cloud-Speicher erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud Service eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](/help/communities/srp-config.md).

Aufgrund der neuen Speicherstruktur ist es erforderlich, die [Upgrade](/help/communities/upgrade.md#adobe-cloud-storage) Anweisungen für die Aktualisierung von Social Communities auf Communities.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen über *Benutzer*, *Benutzerprofile* und *Benutzergruppen*, häufig in die Veröffentlichungsumgebung eingegeben, Besuch

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Wenn Sie ein Upgrade von einer bestehenden Social Community-Site AEM 6.0 durchführen, folgen Sie dem [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage), andernfalls scheint UGC verloren zu sein.

### Authentifizierungsfehler {#authentication-errors}

Wenn Authentifizierungsfehler für die Data Center-URL empfangen und die AEM error.log Meldungen zu veralteten Zeitstempeln enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Verwenden Sie ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/) , um alle AEM Autoren- und Veröffentlichungsserver zu synchronisieren.

### Neue Inhalte werden nicht in Suchvorgängen angezeigt {#new-content-does-not-appear-in-searches}

Die Cloud-Speicher-Infrastruktur der Adobe verwendet *Konsistenz* , um die Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert mehrere Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als einige Sekunden dauert, bis neue Inhalte bei Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Stellen Sie sicher, dass der ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM die Konsole Speicherkonfiguration erneut auf oder überprüfen Sie das AEM Repository.

Wenn in JCR [/conf/global/settings/communities](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Enthält keine [srpc](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp) Knoten bedeutet dies, dass der Speicheranbieter JSRP ist.
* Wenn der Knoten srpc vorhanden ist und enthält [defaultconfiguration](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration) -Knoten verwenden, definieren die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter.
