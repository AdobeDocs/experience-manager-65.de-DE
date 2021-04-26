---
title: Erste Schritte mit AEM Content und Commerce
description: Erfahren Sie, wie Sie ein AEM Content and Commerce-Projekt bereitstellen.
topics: Commerce
feature: Commerce Integration Framework
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: 8ead3d1b24177effa4d40141408c5676eaabcc30
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 6%

---

# Erste Schritte mit AEM Content and Commerce {#start}

Um mit AEM Content and Commerce beginnen zu können, müssen Sie das AEM Content and Commerce Hinzufügen-On für AEM 6.5 installieren.

## Mindestanforderungen an die Software

[AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)  7 oder höher ist erforderlich.

## Einstieg {#onboarding}

Die Onboarding für AEM Content and Commerce ist ein zweistufiger Prozess:

1. Installieren Sie das AEM Content and Commerce Hinzufügen-On für AEM 6.5

2. AEM mit Ihrer Commerce-Lösung verbinden

### Installieren Sie das Add-on AEM Content and Comemerce für AEM 6.5

Laden Sie das AEM Commerce Hinzufügen-On für AEM 6.5 aus dem [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Portal herunter und installieren Sie es.

Beginn und installieren Sie das erforderliche AEM 6.5 Service Pack. Es wird empfohlen, das letzte verfügbare Service Pack zu installieren.

    >[!HINWEIS]
    >
    >Dies wird von der CSE für AEM Managed Service-Kunden durchgeführt.

### AEM an Ihr Commerce-System anschließen

AEM können mit jedem Commerce-System verbunden werden, das über einen zugänglichen GraphQL-Endpunkt für AEM verfügt. Diese Endpunkte sind in der Regel öffentlich verfügbar oder können je nach Projekteinrichtung über private VPN oder lokale Verbindungen verbunden werden.

Optional kann ein Authentifizierungsheader zur Verwendung zusätzlicher CIF-Funktionen bereitgestellt werden, für die eine Authentifizierung erforderlich ist.

Projekte, die vom [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) und dem [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) generiert wurden, der bereits in der [Standardkonfiguration](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) enthalten ist, müssen angepasst werden.

Ersetzen Sie den Wert von `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` durch den GraphQL-Endpunkt Ihres Commerce-Systems. Diese Konfiguration kann über die OSGI-Konsole oder durch Bereitstellung der OSGI-Konfiguration über das Projekt durchgeführt werden. Verschiedene Konfigurationen für Staging- und Produktionssysteme werden unter Verwendung verschiedener AEM Ausführungsmodi unterstützt.

Die AEM Content- und Commerce-Hinzufügen-On- und CIF-Core-Komponenten verwenden sowohl AEM serverseitige als auch clientseitige Verbindungen. Clientseitige CIF-Kernkomponenten und CIF-Hinzufügen-On-Authoring-Werkzeuge verbinden sich standardmäßig mit `/api/graphql`. Dies kann bei Bedarf über die CIF-Cloud Service-Konfiguration angepasst werden (siehe unten).

Das CIF-Add-on stellt ein GraphQL-Proxy-Servlet bei `/api/graphql` bereit, das optional für [lokale Entwicklung](develop.md) verwendet werden kann. Bei Produktionsbereitstellungen wird dringend empfohlen, einen Reverse-Proxy zum Commerce-GraphQL-Endpunkt über den AEM Dispatcher oder auf anderen Netzwerkebenen (wie CDN) einzurichten.

## Konfigurieren von Stores und Katalogen {#catalog}

Das Add-on und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM Site-Strukturen verwendet werden, die mit verschiedenen Commerce-Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer Standardkonfiguration bereitgestellt, die mit dem Standardspeicher und -katalog von Adobe Commerce (Magento) verbunden ist.

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie AEM zu Tools -> Cloud Services -> CIF-Konfiguration

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten

3. Öffnen Sie die Konfigurationseigenschaften über die Aktionsleiste

![CIF-Cloud Services-Konfiguration](/help/commerce/cif/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL Client - Wählen Sie den konfigurierten GraphQL Client für Commerce Backend Kommunikation. Dies sollte in der Regel standardmäßig beibehalten werden.
- Store-Ansicht - die Kennung der (Magento-)Store-Ansicht. Wenn leer, wird die standardmäßige Store-Ansicht verwendet.
- GraphQL Proxy Path - der URL-Pfad GraphQL Proxy in AEM Verwendung, um Anforderungen an den Commerce Backend GraphQL Endpunkt zu projizieren.
   >[!NOTE]
   >
   > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Diese Einstellung sollte nur durch erweiterte Einstellungen geändert werden, die nicht den bereitgestellten GraphQL-Proxy verwenden.
- Unterstützung für Katalog-UID aktivieren: Aktivieren Sie die Unterstützung für UID anstelle von ID in den Commerce-Backend-GraphQL-Aufrufen.
   >[!NOTE]
   >
   > Die Unterstützung für UIDs wurde in Adobe Commerce (Magento) 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Katalogstamm-Kategorien-ID - die Kennung (UID oder ID) des Stammkatalogs

Die oben dargestellte Konfiguration dient als Referenz. Die Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Für komplexere Setups mit mehreren AEM Site-Strukturen kombiniert mit verschiedenen Commerce-Katalogen lesen Sie das Lernprogramm [Commerce Multi-Store Setup](configuring/multi-store-setup.md).

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce-Multi-Store-Einrichtung](configuring/multi-store-setup.md)
