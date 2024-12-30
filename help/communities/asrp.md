---
title: ASRP - Adobe Storage Resource Provider
description: Einrichten von AEM Communities für die Verwendung einer relationalen Datenbank als gemeinsamen Speicher
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

## Informationen zu ASRP {#about-asrp}

Wenn AEM Communities für die Verwendung von ASRP als gemeinsamen Speicher konfiguriert ist, können Sie von allen Autoren- und Veröffentlichungsinstanzen auf benutzergenerierte Inhalte zugreifen, ohne dass eine Synchronisierung oder Replikation erforderlich ist.

Siehe auch [Merkmale von SRP-Optionen](/help/communities/working-with-srp.md#characteristics-of-srp-options) und [Empfohlene Topologien](/help/communities/topologies.md).

## Voraussetzungen {#requirements}

Für die Nutzung von ASRP ist eine zusätzliche Lizenz erforderlich.

Um Ihre AEM Communities-Site für die Verwendung von ASRP für benutzergenerierten Inhalt zu konfigurieren, wenden Sie sich an Ihren Kundenbetreuer für:

* Datenzentrum-URL (Adresse des ASRP-Endpunkts)
* Verbraucherschlüssel
* Geheimer Schlüssel
* Report Suite-ID(s)

Die Privatkunden- und geheimen Schlüssel werden in allen Report Suites eines Unternehmens gemeinsam genutzt. Pro Mandant gibt es eine Report Suite.

## Konfiguration {#configuration}

### ASRP auswählen {#select-asrp}

Die [Speicherkonfigurationskonsole](/help/communities/srp-config.md) ermöglicht die Auswahl der standardmäßigen -Speicherkonfiguration, die angibt, welche Implementierung von SRP verwendet werden soll.

**Bei AEM-Autoreninstanz:**

* Navigieren Sie in der globalen Navigation zu **[!UICONTROL Tools > Communities > Speicherkonfiguration]** und wählen Sie **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**.

![asrp-default](assets/asrp-default.png)

Die folgenden Informationen stammen aus dem Bereitstellungsprozess:

* **Datenzentrum-URL**: Pulldown zur Auswahl des Produktionsdatenzentrums, das von Ihrem Kundenbetreuer identifiziert wurde.
* **Standard-Report Suite**: Geben Sie den Namen der Standard-Report Suite ein.
* **Consumer Key**: Geben Sie den Consumer Key ein.
* **Geheime Daten**: Geben Sie die geheimen Daten ein.
* Wählen Sie **Absenden**.

Vorbereiten der Veröffentlichungsinstanzen:

* [Replizieren des Kryptoschlüssels](#replicate-the-crypto-key)
* [Replizieren der Konfiguration](#publishing-the-configuration)

Testen Sie nach dem Übermitteln der Konfiguration die Verbindung:

* Wählen **Testkonfiguration** aus.

  Testen Sie für jede Autoren- und Veröffentlichungsinstanz die Verbindung zum Rechenzentrum über die Speicherkonfigurationskonsole.

* Stellen Sie sicher, dass die Site-URLs für Profildaten aus dem Rechenzentrum routbar sind, indem Sie [Links externalisieren](#externalize-links).

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Der Consumer-Schlüssel und der Secret Key werden verschlüsselt. Damit die Schlüssel ordnungsgemäß verschlüsselt/entschlüsselt werden können, muss der Granite-Primärschlüssel auf allen AEM-Instanzen gleich sein.

Befolgen Sie die Anweisungen unter [Replizieren Sie den Crypto-Schlüssel](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Externalisieren von Links {#externalize-links}

Stellen Sie für die richtigen Profil- und Profilbild-Links sicher, dass Sie ordnungsgemäß [Link Externalizer konfigurieren](/help/sites-developing/externalizer.md).

Stellen Sie sicher, dass Sie die Domains als URLs festlegen, die über die Datenzentrum-URL (ASRP-Endpunkt) weitergeleitet werden können.

### Zeitsynchronisierung {#time-synchronization}

Damit die Authentifizierung mit dem ASRP-Endpunkt erfolgreich ist, müssen die Computer, auf denen die gehostete AEM Communities ausgeführt wird, zeitsynchronisiert werden, z. B. mit dem [Network Time Protocol (NTP)](https://www.ntp.org/).

### Veröffentlichen der Konfiguration {#publishing-the-configuration}

ASRP muss auf allen Autoren- und Veröffentlichungsinstanzen als Common Store identifiziert werden.

So stellen Sie die identische Konfiguration in der Veröffentlichungsumgebung zur Verfügung:

In der AEM-Autoreninstanz:

* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]**
* Wählen Sie **Baum aktivieren**
* **Startpfad**: Navigieren Sie zu `/conf/global/settings/communities/srpc/`
* deselect **only modified**
* Wählen Sie **Aktivieren**

## Aktualisieren von AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Wenn Sie ASRP auf einer veröffentlichten Community-Site aktivieren, sind alle bereits in [JCR](/help/communities/jsrp.md) gespeicherten UGC nicht mehr sichtbar, da keine Synchronisierung von Daten zwischen dem On-Premise-Speicher und dem Cloud-Speicher stattfindet.

**`AEM Communities Extension`** wurde zuvor in sozialen Communities von AEM 6.0 als Cloud Service eingeführt. Ab AEM 6.1 Communities ist keine Cloud-Konfiguration mehr erforderlich. Wählen Sie einfach ASRP aus der [Speicherkonfigurationskonsole](/help/communities/srp-config.md).

Aufgrund der neuen Speicherstruktur ist es erforderlich, beim Upgrade von Social Communities [ Communities die ](/help/communities/upgrade.md#adobe-cloud-storage) „Upgrade“ zu befolgen.

## Verwalten von Benutzerdaten {#managing-user-data}

Informationen zu *Benutzern*, *Benutzerprofilen* und *Benutzergruppen*, die häufig in der Veröffentlichungsumgebung eingegeben werden, finden Sie unter

* [Benutzersynchronisierung](/help/communities/sync.md)
* [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md)

## Fehlerbehebung {#troubleshooting}

### UGC verschwindet nach dem Upgrade {#ugc-disappears-after-upgrade}

Wenn Sie von einer bestehenden AEM 6.0 Social-Community-Website aktualisieren, folgen Sie unbedingt den [Upgrade-Anweisungen](/help/communities/upgrade.md#adobe-cloud-storage), da ansonsten der benutzergenerierte Inhalt verloren zu gehen scheint.

### Authentifizierungsfehler {#authentication-errors}

Wenn Authentifizierungsfehler über die Datenzentrum-URL empfangen werden und die Datei „error.log“ des AEM Meldungen zu veralteten Zeitstempeln enthält, überprüfen Sie, ob eine Zeitsynchronisierung erfolgt.

Verwenden Sie ein Tool wie [Network Time Protocol (NTP)](https://www.ntp.org/) zum Synchronisieren aller AEM-Autoren- und Veröffentlichungsserver.

### Neuer Inhalt wird nicht bei Suchvorgängen angezeigt {#new-content-does-not-appear-in-searches}

Die Adobe-Cloud-Speicherinfrastruktur verwendet *mögliche Konsistenz*, um ihre Skalierungs- und Leistungsziele zu erreichen. Aus diesem Grund sind neue Inhalte nicht sofort verfügbar und es dauert mehrere Sekunden, bis sie in den Suchergebnissen angezeigt werden.

Während das Intervall, das sich auf die mögliche Konsistenz auswirkt, überwacht wird, wenden Sie sich an Ihren Kundenbetreuer, wenn es länger als einige Sekunden dauert, bis neue Inhalte bei der Suche angezeigt werden.

### UGC in ASRP nicht sichtbar {#ugc-not-visible-in-asrp}

Stellen Sie sicher, dass das ASRP als Standardanbieter konfiguriert wurde, indem Sie die Konfiguration der Speicheroption überprüfen. Standardmäßig ist der Speicherressourcenanbieter JSRP, nicht ASRP.

Rufen Sie auf allen Autoren- und Veröffentlichungs-AEM-Instanzen die Speicherkonfigurationskonsole erneut auf, oder überprüfen Sie das AEM-Repository.

Im JCR, wenn [/conf/global/settings/Communities](https://localhost:4502/crx/de/index.jsp#/etc/socialconfig/):

* Enthält keinen [srpc](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp)-Knoten. Das bedeutet, dass der Speicheranbieter JSRP ist.
* Wenn der srpc-Knoten vorhanden ist und den [defaultConfiguration](https://localhost:4502/crx/de/index.jsp#/conf/global/settings/communities/srp/defaultconfiguration)-Knoten enthält, definieren die Eigenschaften der defaultConfiguration, dass ASRP der Standardanbieter ist.
