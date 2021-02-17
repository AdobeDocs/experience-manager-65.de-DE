---
title: Erstellen der Exportkonfiguration für gemeinsame Ressourcen
seo-title: Erstellen der Exportkonfiguration für gemeinsame Ressourcen
description: Auf dieser Seite erfahren Sie, wie Sie freigegebene Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile exportieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie freigegebene Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile exportieren.
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 6%

---


# Erstellen der Exportkonfiguration für freigegebene Ressourcen{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>**Voraussetzung**:
>
>Bevor Sie mehr über das Erstellen und Bearbeiten freigegebener Ressourcen erfahren, lesen Sie [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md), um die grundlegenden Konzepte zu verstehen.

AEM Mobile-Benutzer verwenden Content Sync, um Live-Inhalte für die Verwendung in mobilen Apps in statische Inhalte zu exportieren. Dieser Export erfolgt, wenn Inhalte von AEM Mobile in Mobile On-Demand Services hochgeladen werden.

Die in der obigen Tabelle erwähnte Eigenschaft ***dps-exportTemplate*** definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

In den folgenden Ressourcen wird beschrieben, wie Sie freigegebene Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile exportieren.

Freigegebene HTML-Ressourcen ermöglichen es Artikeln, HTML-Ressourcen freizugeben, die andernfalls für alle Artikel dupliziert werden müssten, und können Symbole, Schriftarten, JavaScript und CSS enthalten.

Die unter **&lt;dps-exportTemplate>/dps-HTMLResources>** gefundene Konfiguration für die Inhaltssynchronisierung sollte so konfiguriert werden, dass der gesamte Inhalt eines Artikels exportiert wird, der für das statische Rendern der Eigenschaft auf dem Gerät erforderlich ist.

>[!CAUTION]
>
>Sie können die folgenden Schritte ausführen, um gemeinsam genutzte Ressourcen als Beispiel Ansicht, sofern Sie über Folgendes verfügen:
>
>* Beispielinhalt installiert
>* AEM
>* kein konfigurierter benutzerdefinierter Kontext oder ein anderer Anschluss

>



Informationen zur Ansicht einer gemeinsamen Ressource finden Sie in den folgenden Schritten:

1. Öffnen Sie die CRXDE Lite auf Ihrem AEM.
1. Navigieren Sie zu diesem Pfad *[/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*, um die gemeinsamen Beispielressourcen Ansicht.

   Sie können alle zum Erstellen der freigegebenen Ressourcen erforderlichen Eigenschaften wie in der folgenden Abbildung dargestellt Ansicht haben:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>Freigegebene Ressourcen sollten nach AEM Mobile On-demand Services hochgeladen oder exportiert werden, wenn sich eine der freigegebenen Ressourcen ändert.

