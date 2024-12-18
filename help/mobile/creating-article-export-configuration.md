---
title: Erstellen der Konfiguration von Artikelexporten
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

# Erstellen der Konfiguration von Artikelexporten{#creating-article-export-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>**Voraussetzung**:
>
>Bevor Sie mehr über das Erstellen und Ändern freigegebener Ressourcen erfahren, lesen Sie den Abschnitt [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md) , um die grundlegenden Konzepte zu verstehen.

AEM Mobile-Benutzer verwenden die Inhaltssynchronisierung, um Live-Inhalte für die Verwendung in mobilen Apps in statische Inhalte zu exportieren. Dieser Export erfolgt beim Hochladen von Inhalten in Mobile On-Demand Services von AEM Mobile.

Die in der obigen Tabelle erwähnte Eigenschaft ***dps-exportTemplate*** definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

Die folgenden Ressourcen beschreiben den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.

Artikel enthalten Inhalte, die exportiert und hochgeladen werden müssen. Ein Teil dieses Inhalts kann zwischen Artikeln freigegeben werden.

Verwenden Sie [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) , um den Inhalt zusammenzustellen und ein Paket mit den ***freigegebenen Ressourcen*** zu erstellen.

Die Konfiguration ContentSync unter **&lt;dps-exportTemplate>/dps-article>** sollte so konfiguriert werden, dass alle Inhalte und Artikel exportiert werden, die für das statische Rendering der Eigenschaften auf dem Gerät erforderlich sind.

>[!CAUTION]
>
>Sie können die folgenden Schritte ausführen, um Beispiel für freigegebene Ressourcen anzuzeigen, nur wenn Sie über Folgendes verfügen:
>
>* den Beispielinhalt installiert hat
>* AEM
>* kein konfigurierter benutzerdefinierter Kontext oder ein anderer Port
>

Informationen zum Anzeigen einer gemeinsam genutzten Beispielressource finden Sie in den folgenden Schritten:

1. Öffnen Sie CRXDE Lite auf Ihrem AEM.
1. Navigieren Sie zu diesem Pfad [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), um die gemeinsamen Beispielressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die für die Erstellung Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikel sollten hochgeladen oder nach AEM Mobile On-demand Services exportiert werden, wenn sich der Artikelinhalt ändert.
