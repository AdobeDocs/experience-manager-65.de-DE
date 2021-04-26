---
title: Wichtige Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Im Vergleich zu alten CIF-Versionen wurden beim Commerce Integration Framework (CIF)-Add-On merkliche Änderungen vorgenommen.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
translation-type: tm+mt
source-git-commit: a8dba82029168660b84b085ab46d0406b19961ef
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 9%

---

# Wichtige Änderungen am CIF-Add-on für das Commerce Integration Framework{#notable-changes}

Dieses Dokument hebt die wichtigen Unterschiede zwischen dem Commerce Integration Framework (CIF) Add-On und alten CIF-Versionen hervor, die hauptsächlich CIF Classic (Quickstart) und CIF Open-Source genannt werden.

## Installation und Updates

Das AEM CIF-Add-On-Paket wird installiert und mit AEM Package Manager aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Quickstart. CIF-Aktualisierungen waren Teil regelmäßiger AEM- oder Service Pack-Aktualisierungen.
* CIF Open Source: Installation über GitHub. Aktualisierungen waren Teil der manuellen Aktualisierungs-/Wartungsarbeiten.

## Endpunktkonfiguration

Der Endpunkt wird über die OSGi-Konsole konfiguriert.

**Vorherige CIF-Versionen**

* CIF Classic: Über OSGi-Konfiguration in AEM
* CIF Open Source: Über den CIF-Konfigurationsbrowser

## Bereitstellung des CIF-Venia-Projekts

Projekt verfügbar unter [GitHub AEM Guides - CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) und Bereitstellung über Package AEM Manager

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Paketinstallation

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt angefordert, der die erforderlichen GraphQL-APIs unterstützt. Diese APIs unterstützen den Zugriff auf Live- oder Stage-Daten zu jedem beliebigen Datum. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und Stage-Produktdaten werden über den vollständigen oder Delta-Produktimport in JCR unter AEM Author importiert und beibehalten. Live-Produktdaten werden in AEM Publish repliziert.

## Produktkatalog-Erlebnisse mit AEM Rendering

AEM rendert Produktkatalog-Erlebnisse spontan mit AEM Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: AEM Author erstellt mithilfe des Katalogentwurfstools eine AEM für jede Kategorie/jedes Produkt. Diese Seiten werden in AEM Publish repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
