---
title: AEM Adobe PhoneGap
seo-title: AEM Adobe PhoneGap
description: AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. Auf dieser Seite erhalten Sie Informationen zu den ersten Schritten mit Adobe PhoneGap Enterprise.
seo-description: AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. Auf dieser Seite erhalten Sie Informationen zu den ersten Schritten mit Adobe PhoneGap Enterprise.
uuid: bdd90cda-2489-4763-a90a-9c409d6e68ae
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: fbcdea8a-72e9-431b-9c32-dc02d4cdb9c8
exl-id: d989e235-5993-4738-8523-5b9a5f6bf712
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 15%

---

# AEM Adobe PhoneGap{#aem-adobe-phonegap}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. PhoneGap ermöglicht dem Benutzer das Erstellen von Dienstprogramm-Apps, mit denen der Benutzer mit dem Inhalt arbeiten kann. „Content Sync“ ermöglicht Ihnen, versionierte Archive der Seiten für das Bundling mit Apps zu erstellen. 

In der Regel ist ein ***AEM Administrator*** für das Hinzufügen einer neuen Anwendung zum AEM Mobile-Katalog verantwortlich, entweder durch Erstellen einer neuen App mithilfe des Erstellungsassistenten oder durch Importieren einer bestehenden Anwendung.

Von hier aus kann ein ***AEM-Autor*** (oder *Marketer*) jetzt die nativen Vorlagen und Komponenten verwenden, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag-and-Drop zu verschieben und Medien aller Typen aus dem DAM hinzuzufügen, einschließlich Bildern, Videos und Textfragmenten (Inhaltsfragmente).

Die wahre Stärke von AEM Mobile besteht darin, dass ein *savvy* ***AEM-Entwickler*** benutzerdefinierte Webvorlagen und -komponenten erweitern und erstellen kann, damit der *AEM-Autor* attraktive mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die App-Welt optimiert. kommunizieren jedoch sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server) mit kanalübergreifenden Service-Endpunkten.

>[!NOTE]
>
>Wenn die *AEM-Autoreninstanz* glaubt, dass die App bereit ist, können sie ihre Stakeholder zunächst dazu anhalten, die App mit **[Adobe Verify](/help/mobile/phonegap-mobile-quickstart.md)** (verfügbar im AppStore und im PlayStore) zur Überprüfung und Genehmigung herunterzuladen. Sobald der Benutzer die grüne Ampel erhalten hat, kann er diese neuen oder aktualisierten Inhalte direkt über das AEM Mobile ContentSync-Release-Management-Dashboard für Inhalte an seine Benutzer freigeben. Eine Person kann eine beliebige Anzahl von Rollen übernehmen, das liegt an Ihnen und Ihren Governance-Richtlinien.

## Voraussetzungen {#prerequisites}

AEM Mobile ist nur eine Säule, die die gesamte AEM bildet.

Bevor Sie mit AEM Mobile arbeiten und die Schritte in diesem Erste-Schritte-Handbuch befolgen, sollten die Benutzer mit AEM und dem AEM Mobile Control Center vertraut sein. Siehe:

[Erste Schritte mit AEM](/help/sites-deploying/deploy.md)

[Eine exemplarische Vorgehensweise des AEM Mobile Control Centers](/help/mobile/phonegap-authoring-apps.md)

## QuickLinks für Autoren {#quicklinks-for-authors}

Weitere Informationen zu den Rollen und Zuständigkeiten eines Autors finden Sie unter [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md) .

## QuickLinks für Entwickler {#quicklinks-for-developers}

Es gibt Beispielanwendungen, die in AEM Mobile integriert und vom Entwickler angepasst werden können. Klicken Sie auf [Entwickeln von Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md).

In den folgenden Kapiteln erfahren Sie mehr über erweiterte Konzepte wie die White-Beschriftung Ihrer Anwendung, Lokalisierung, Internationalisierung, ContentSync, Targeting, Analytics und mehr.

## QuickLinks für Administratoren {#quicklinks-for-administrators}

Informationen zum Einrichten und Verwalten Ihrer Mobile App finden Sie unter [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md).

>[!NOTE]
>
>Mithilfe hybrider mobiler Technologien können Sie Rich-Mobile-Apps erstellen, die mit AEM Mobile offline und online ausgeführt werden.*Tatsächlich entscheiden sich viele Kunden dafür, Apps zu erstellen, die überprüfen, wann sie online oder offline sind, und sich entsprechend zu verhalten.*
