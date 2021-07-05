---
title: Erste Schritte mit AEM Content and Commerce
description: Erfahren Sie, wie Sie ein AEM Content and Commerce-Projekt bereitstellen.
topics: Commerce
feature: Commerce Integration Framework
source-git-commit: 1b200ea21709cd9234c92da8a8ef6145d2c2f635
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 38%

---


# Erste Schritte mit AEM Content and Commerce {#start}

Um mit AEM Content and Commerce zu beginnen, müssen Sie das AEM Content and Commerce Add-On für AEM 6.5 installieren.

## Mindestanforderung an Software

[AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 oder höher ist erforderlich.

## Einstieg {#onboarding}

Das Onboarding für AEM Content and Commerce erfolgt in zwei Schritten:

1. Installieren Sie das AEM Content and Commerce Add-On für AEM 6.5

2. AEM mit Ihrer Commerce-Lösung verbinden

### Installieren Sie das AEM Content and Commerce Add-On für AEM 6.5 {#install-add-on}

Laden Sie das AEM Commerce Add-On für AEM 6.5 vom [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)-Portal herunter und installieren Sie es.

Starten und installieren Sie das erforderliche AEM 6.5 Service Pack. Es wird empfohlen, das letzte verfügbare Service Pack zu installieren.

>[!NOTE]
>
>Dies wird vom CSE für AEM Managed Service-Kunden durchgeführt.

### AEM mit Ihrem Commerce-System verbinden {#connect}

AEM können mit jedem Commerce-System verbunden werden, das über einen zugänglichen GraphQL-Endpunkt für AEM verfügt. Diese Endpunkte sind in der Regel öffentlich verfügbar oder können je nach Projekteinrichtung über private VPN- oder lokale Verbindungen verbunden werden.

Optional kann ein Authentifizierungs-Header bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Projekte, die vom [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) und vom [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) generiert wurden, der bereits in der [standardmäßigen Konfiguration](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) enthalten ist, müssen angepasst werden.

Ersetzen Sie den Wert von `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` durch den GraphQL-Endpunkt Ihres Commerce-Systems. Diese Konfiguration kann über die OSGi-Konsole oder durch Bereitstellung der OSGi-Konfiguration über das Projekt durchgeführt werden. Verschiedene Konfigurationen für Staging- und Produktionssysteme werden mit verschiedenen AEM Ausführungsmodi unterstützt.

Die AEM Content- und Commerce-Add-On- und CIF-Kernkomponenten verwenden sowohl AEM serverseitige als auch Client-seitige Verbindungen. Clientseitige CIF-Kernkomponenten und CIF-Add-On-Authoring-Tools verbinden sich standardmäßig mit `/api/graphql`. Dies kann bei Bedarf über die CIF-Cloud Service-Konfiguration angepasst werden (siehe unten).

Das CIF-Add-on stellt ein GraphQL-Proxy-Servlet unter `/api/graphql` bereit, das optional für [lokale Entwicklung](develop.md) verwendet werden kann. Bei Produktionsbereitstellungen wird dringend empfohlen, einen Reverse-Proxy zum Commerce-GraphQL-Endpunkt über den AEM Dispatcher oder auf anderen Netzwerkschichten (wie CDN) einzurichten.

## Konfigurieren von Stores und Katalogen {#catalog}

Das Add-On und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM Site-Strukturen verwendet werden, die mit verschiedenen Commerce-Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer Standardkonfiguration bereitgestellt, die mit dem Standardspeicher und -katalog von Adobe Commerce (Magento) verbunden ist.

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie in AEM zu „Tools“ > „Cloud Services“ > „CIF-Konfiguration“

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten

3. Öffnen Sie die Konfigurationseigenschaften über die Symbolleiste

![CIF-Cloud Services-Konfiguration](/help/commerce/cif/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL-Client – Wählen Sie den konfigurierten GraphQL-Client für die Commerce-Back-End-Kommunikation aus. Dies sollte normalerweise auf der Standardeinstellung bleiben.
- Shop-Ansicht – die Kennung der (Magento-)Shop-Ansicht. Wenn leer, wird die standardmäßige Shop-Ansicht verwendet.
- GraphQL-Proxy-Pfad – der URL-Pfad des GraphQL-Proxy in AEM, der als Proxy für Anfragen an den Commerce-Back-End-GraphQL-Endpunkt verwendet wird.
   >[!NOTE]
   >
   > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Nur komplexere Setups, die nicht den bereitgestellten GraphQL-Proxy verwenden, sollten diese Einstellung ändern.
- Unterstützung der Catalog-UID aktivieren – aktiviert die Unterstützung für UID anstelle von ID in den Commerce-Back-End-GraphQL-Aufrufen.
   >[!NOTE]
   >
   > Die Unterstützung für UIDs wurde in Adobe Commerce (Magento) 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Back-End ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Kennung der Stammkategorie des Katalogs – die Kennung (UID oder ID) des Stammverzeichnisses des Shops
   >[!CAUTION]
   >
   > Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Wenn Ihr Projekt Version 2.0.0 der CIF-Kernkomponenten verwendet, müssen Sie die Unterstützung der Catalog-UID aktivieren und eine gültige Kategorie-UID als &quot;Katalogstamm-Kategorienkennung&quot;verwenden.

Die oben dargestellte Konfiguration dient als Referenz. Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Komplexere Setups mit mehreren AEM-Website-Strukturen in Kombination mit verschiedenen Commerce-Katalogen finden Sie im Tutorial [Einrichten von mehreren Commerce-Shops](configuring/multi-store-setup.md).

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Einrichten von mehreren Commerce-Shops](configuring/multi-store-setup.md)
