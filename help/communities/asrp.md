---
title: ASRP - Adobe Storage Resource Provider
description: Einrichten von AEM Communities zur Verwendung einer relationalen Datenbank als gemeinsamen Speicher
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 6430ed96-5d96-41b6-866f-90b34ff84f7a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '792'
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

**In AEM Autoreninstanz:**

* Navigieren Sie in der globalen Navigation zu **[!UICONTROL Tools > Communities > Speicherkonfiguration]** und wählen Sie **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

Die folgenden Informationen stammen aus dem Bereitstellungsprozess:

* **Data Center URL**: Rufen Sie die Seite ab, um das von Ihrem Kundenbetreuer identifizierte Produktionsdatencenter auszuwählen.
* **Standard-Report Suite**: Geben Sie den Namen der Standard-Report Suite ein.
* **Consumer Key**: Geben Sie den Consumer Key ein.
* **Geheimnis**: Geben Sie den geheimen Schlüssel ein.
* Wählen Sie **Absenden**.

Bereiten Sie die Veröffentlichungsinstanzen vor:

* [Replizieren des Kryptoschlüssels](#replicate-the-crypto-key)
* [Konfiguration replizieren](#publishing-the-configuration)

Testen Sie nach dem Senden der Konfiguration die Verbindung:

* Wählen Sie **Testkonfiguration** aus.

  Testen Sie für jede Autoren- und Veröffentlichungsinstanz die Verbindung zum Rechenzentrum über die Konsole Speicherkonfiguration .

* Stellen Sie sicher, dass die Site-URLs für Profildaten vom Rechenzentrum routbar sind, indem Sie [Links externalisieren](#externalize-links).

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Der Consumer Key und der Secret Key sind verschlüsselt. Damit die Schlüssel ordnungsgemäß verschlüsselt/entschlüsselt werden können, muss der primäre Granite-Crypto-Schlüssel auf allen AEM Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Replizieren des Crypto-Schlüssels](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Externe Links {#externalize-links}

Stellen Sie sicher, dass Sie für korrekte Profil- und Profilbildlinks [Link Externalizer konfigurieren](/help/sites-developing/externalizer.md).

Stellen Sie sicher, dass die Domänen URLs sind, die über die Data Center URL (ASRP-Endpunkt) routbar sind.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen Ihr gehosteter AEM Communities ausgeführt wird, zeitsynchronisiert sein, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss in allen Autoren- und Veröffentlichungsinstanzen als gemeinsamer Speicher identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

In AEM Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** .
* Wählen Sie **Baum aktivieren**
* **Startpfad**: Navigieren Sie zu `/conf/global/settings/communities/srpc/`
* Deaktivieren Sie **Nur geändert** .
* Wählen Sie **Activate** aus.

## Upgrade von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind bereits in [JCR](/help/communities/jsrp.md) gespeicherte benutzergenerierte Inhalte nicht mehr sichtbar, da keine Synchronisierung von Daten zwischen On-Premise-Speicher und Cloud-Speicher erfolgt.

**`AEM Communities Extension`** wurde zuvor in AEM 6.0 Social Communities als Cloud-Service eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](/help/communities/srp-config.md) aus.

Aufgrund der neuen Speicherstruktur müssen Sie bei der Aktualisierung von Social Communities auf Communities die Anweisungen für das [Upgrade](/help/communities/upgrade.md#adobe-cloud-storage) befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in die Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach der Aktualisierung {#ugc-disappears-after-upgrade}

Wenn Sie von einer bestehenden Social Community-Site AEM 6.0 aktualisieren, folgen Sie den [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage). Andernfalls scheint UGC verloren zu sein.

### Authentifizierungsfehler {#authentication-errors}

Wenn Authentifizierungsfehler für die Data Center-URL empfangen und die AEM error.log Meldungen zu veralteten Zeitstempeln enthält, überprüfen Sie, ob eine Zeitsynchronisierung stattfindet.

Verwenden Sie ein Tool wie das [Network Time Protocol (NTP)](https://www.ntp.org/), um die Zeitsynchronisierung aller AEM Autoren- und Veröffentlichungsserver zu ermöglichen.

### Neue Inhalte werden nicht in Suchvorgängen angezeigt {#new-content-does-not-appear-in-searches}

Die Adobe-Cloud-Speicherinfrastruktur verwendet *letztendlich Konsistenz*, um Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert mehrere Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als einige Sekunden dauert, bis neue Inhalte bei Suchvorgängen angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Stellen Sie sicher, dass der ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption aktivieren. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Rufen Sie auf allen Autoren- und Veröffentlichungsinstanzen AEM die Konsole Speicherkonfiguration erneut auf oder überprüfen Sie das AEM Repository.

Wenn in JCR [/conf/global/settings/communities](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Enthält keinen Knoten [srpc](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp) , bedeutet dies, dass der Speicheranbieter JSRP ist.
* Wenn der Knoten srpc vorhanden ist und den Knoten [defaultconfiguration](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration) enthält, definieren die Eigenschaften der Standardkonfiguration ASRP als Standardanbieter.
