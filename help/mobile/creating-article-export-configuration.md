---
title: Erstellen der Konfiguration für den Artikelexport
description: Auf dieser Seite erfahren Sie mehr über den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 5295f383-3b46-4456-9177-65de68e39a85
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 7%

---

# Erstellen der Konfiguration für den Artikelexport{#creating-article-export-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>**Voraussetzung**:
>
>Bevor Sie mehr über das Erstellen und Ändern freigegebener Ressourcen erfahren, lesen Sie [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md) um die grundlegenden Konzepte zu verstehen.

AEM Mobile-Benutzende verwenden die Inhaltssynchronisierung, um Live-Inhalte zur Verwendung in Mobile Apps in statische Inhalte zu exportieren. Dieser Export erfolgt, wenn Inhalte von AEM Mobile in Mobile On-Demand Services hochgeladen werden.

Die Eigenschaft ***dps-exportTemplate*** die in der obigen Tabelle erwähnt wird, definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

In den folgenden Ressourcen wird das Exportieren von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile beschrieben.

Artikel enthalten Inhalte, die exportiert und hochgeladen werden müssen. Ein Teil dieses Inhalts kann von Artikeln gemeinsam genutzt werden.

Verwenden Sie [ContentSync](/help/mobile/mobile-ondemand-contentsync.md), um den Inhalt zusammenzuführen und ein Paket ***Freigegebene Ressourcen*** zu erstellen.

Die ContentSync-Konfiguration unter **&lt;dps-exportTemplate>/dps-article>** sollte so konfiguriert sein, dass der gesamte Inhalt eines Artikels exportiert wird, der für das statische Rendern der Eigenschaft auf dem Gerät erforderlich ist.

>[!CAUTION]
>
>Sie können die folgenden Schritte ausführen, um Beispiele für freigegebene Ressourcen anzuzeigen, sofern Sie über Folgendes verfügen:
>
>* Beispielinhalt installiert
>* AEM-Instanz wird ausgeführt
>* Kein konfigurierter benutzerdefinierter Kontext oder ein anderer Port
>

Gehen Sie wie folgt vor, um eine Beispiel-freigegebene Ressource anzuzeigen:

1. Öffnen Sie CRXDE Lite auf Ihrem AEM-Server.
1. Navigieren Sie zu diesem Pfad [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), um die Beispiel-freigegebenen Ressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die zum Erstellen Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikel sollten in AEM Mobile On-demand Services hochgeladen oder exportiert werden, wenn sich der Inhalt eines Artikels ändert.
