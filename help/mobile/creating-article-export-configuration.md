---
title: Erstellen der Konfiguration von Artikelexporten
seo-title: Erstellen der Konfiguration von Artikelexporten
description: Auf dieser Seite erfahren Sie mehr über den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.
seo-description: Auf dieser Seite erfahren Sie mehr über den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
exl-id: 5295f383-3b46-4456-9177-65de68e39a85
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
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
>Bevor Sie mehr über das Erstellen und Ändern freigegebener Ressourcen erfahren, finden Sie unter [Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md) grundlegende Konzepte.

AEM Mobile-Benutzer verwenden die Inhaltssynchronisierung, um Live-Inhalte für die Verwendung in mobilen Apps in statische Inhalte zu exportieren. Dieser Export erfolgt beim Hochladen von Inhalten in Mobile On-Demand Services von AEM Mobile.

Die in der obigen Tabelle erwähnte Eigenschaft ***dps-exportTemplate*** definiert den Pfad zu den Exportkonfigurationen der App. Legen Sie diese Eigenschaft fest, um freigegebene Ressourcen zu erstellen und zu ändern.

Die folgenden Ressourcen beschreiben den Export von Inhalten aus Adobe Experience Manager (AEM) zum Hochladen in AEM Mobile.

Artikel enthalten Inhalte, die exportiert und hochgeladen werden müssen. Ein Teil dieses Inhalts kann zwischen Artikeln freigegeben werden.

Verwenden Sie [ContentSync](/help/mobile/mobile-ondemand-contentsync.md), um den Inhalt zusammenzustellen und ein ***Shared Resources*** -Paket zu erstellen.

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

1. Öffnen Sie die CRXDE Lite auf Ihrem AEM.
1. Navigieren Sie zu diesem Pfad [/etc/contentsync/templates/dps-we-unlimited-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article), um die gemeinsamen Beispielressourcen anzuzeigen.

   Sie können alle Eigenschaften anzeigen, die für die Erstellung Ihrer freigegebenen Ressourcen erforderlich sind, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikel sollten hochgeladen oder nach AEM Mobile On-demand Services exportiert werden, wenn sich der Artikelinhalt ändert.
