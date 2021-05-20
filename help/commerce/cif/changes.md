---
title: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Wesentliche Änderungen des Commerce Integration Framework (CIF)-Add-ons im Vergleich zu alten CIF-Versionen.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 3%

---

# Wesentliche Änderungen am Add-on für das Commerce Integration Framework (CIF){#notable-changes}

In diesem Dokument werden die wichtigen Unterschiede zwischen dem Commerce Integration Framework (CIF)-Add-on und alten CIF-Versionen, hauptsächlich CIF Classic (Quickstart) und CIF Open Source, erläutert.

## Installation und Updates

Das AEM CIF-Add-On-Paket wird installiert und mit AEM Package Manager aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Schnellstarts. CIF-Aktualisierungen waren Teil regelmäßiger AEM- oder Service Pack-Aktualisierungen
* CIF Open Source: Installation über GitHub. Aktualisierungen waren Teil der manuellen Aktualisierung/Wartung.

## Endpunktkonfiguration

Der Endpunkt wird über die OSGi-Konsole konfiguriert.

**Vorherige CIF-Versionen**

* CIF Classic: Über die OSGi-Konfiguration in AEM
* CIF Open Source: Über den CIF-Konfigurationsbrowser

## Implementierung des CIF-Venia-Projekts

Projekt verfügbar unter [GitHub AEM Guides - CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) und Bereitstellung über AEM Package Manager.

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Paketinstallation

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt angefordert, der die erforderlichen GraphQL-APIs unterstützt. Diese APIs unterstützen den Zugriff auf Live- oder Staging-Daten zu einem beliebigen Zeitpunkt. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und gestaffelte Produktdaten werden in JCR in der AEM-Autoreninstanz über den vollständigen oder Delta-Produktimport importiert und beibehalten. Live-Produktdaten werden in AEM Publish repliziert.

## Produktkatalogerlebnisse mit AEM Rendering

AEM rendert Produktkatalog-Erlebnisse direkt mithilfe AEM Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Die AEM-Autoreninstanz erstellt mit dem Katalog-Blueprint-Tool eine AEM für jede Kategorie/jedes Produkt. Diese Seiten werden in AEM Publish repliziert.

>[!NOTE]
>
>Weitere Informationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
