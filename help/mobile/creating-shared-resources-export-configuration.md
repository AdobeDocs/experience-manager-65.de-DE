---
title: Erstellen der Exportkonfiguration für freigegebene Ressourcen
description: Auf dieser Seite erfahren Sie mehr über den Export freigegebener Ressourcen aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 576b4567-c7b6-4196-84e7-47e980637540
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 7%

---

# Erstellen der Exportkonfiguration für freigegebene Ressourcen{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>**Voraussetzung**:
>
>Bevor Sie mehr über das Erstellen und Ändern freigegebener Ressourcen erfahren, lesen Sie [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md) um die grundlegenden Konzepte zu verstehen.

Adobe Experience Manager (AEM)-Mobilbenutzer verwenden Content Sync , um Live-Inhalte in statische Inhalte zur Verwendung in Mobile Apps zu exportieren. Dieser Export erfolgt, wenn Inhalte von AEM Mobile in Mobile On-Demand Services hochgeladen werden.

Die Eigenschaft ***dps-exportTemplate*** die in der obigen Tabelle erwähnt wird, definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

Die folgenden Ressourcen beschreiben den Export freigegebener Ressourcen aus AEM zum Hochladen in AEM Mobile.

Freigegebene HTML-Ressourcen ermöglichen es Artikeln, HTML-Ressourcen freizugeben, die andernfalls für alle Artikel dupliziert würden, und können Symbole, Schriftarten, JavaScript und CSS enthalten.

Die Konfiguration der Inhaltssynchronisierung unter **&lt;dps-exportTemplate>/dps-HTMLResources>** sollte so konfiguriert werden, dass der gesamte Inhalt eines Artikels, der für das statische Rendern von Eigenschaften auf dem Gerät erforderlich ist, exportiert wird.

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
1. Navigieren Sie zu diesem Pfad *[/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*, um die Beispiele für freigegebene Ressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die zum Erstellen Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>Freigegebene Ressourcen sollten in AEM Mobile On-demand Services hochgeladen oder exportiert werden, wenn sich eine der freigegebenen Ressourcen ändert.
