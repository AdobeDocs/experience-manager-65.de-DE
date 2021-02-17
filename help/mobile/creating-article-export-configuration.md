---
title: Artikelexportkonfiguration erstellen
seo-title: Artikelexportkonfiguration erstellen
description: Auf dieser Seite erfahren Sie, wie Sie Inhalte aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile exportieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie Inhalte aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile exportieren.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 6%

---


# Erstellen der Artikelexportkonfiguration{#creating-article-export-configuration}

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

Die folgenden Ressourcen beschreiben den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen nach AEM Mobile.

Artikel enthalten Inhalte, die exportiert und hochgeladen werden müssen. Einige dieser Inhalte können für Artikel freigegeben werden.

Verwenden Sie [ContentSync](/help/mobile/mobile-ondemand-contentsync.md), um den Inhalt zusammenzutragen und ein ***Freigegebene Ressourcen***-Paket zu erstellen.

Die unter **&lt;dps-exportTemplate>/dps-article>** gefundene ContentSync-Konfiguration sollte so konfiguriert werden, dass der gesamte Inhalt eines Artikels exportiert wird, der für das statische Rendern der Eigenschaft auf dem Gerät erforderlich ist.

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
1. Navigieren Sie zu diesem Pfad [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), um die gemeinsamen Beispielressourcen Ansicht.

   Sie können alle zum Erstellen der freigegebenen Ressourcen erforderlichen Eigenschaften wie in der folgenden Abbildung dargestellt Ansicht haben:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikel sollten nach AEM Mobile On-demand Services hochgeladen oder exportiert werden, wenn sich der Artikelinhalt ändert.

