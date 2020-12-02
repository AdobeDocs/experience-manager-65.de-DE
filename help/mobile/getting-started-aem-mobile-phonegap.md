---
title: AEM Adobe PhoneGap
seo-title: AEM Adobe PhoneGap
description: AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. Folgen Sie dieser Seite, um mit Adobe PhoneGap Enterprise zu beginnen.
seo-description: AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. Folgen Sie dieser Seite, um mit Adobe PhoneGap Enterprise zu beginnen.
uuid: bdd90cda-2489-4763-a90a-9c409d6e68ae
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: fbcdea8a-72e9-431b-9c32-dc02d4cdb9c8
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 15%

---


# AEM Adobe PhoneGap{#aem-adobe-phonegap}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM kann mit PhoneGap integriert werden, damit Sie mithilfe der AEM-Seiten problemlos Apps erstellen können. PhoneGap ermöglicht dem Benutzer das Erstellen von Dienstprogramm-Apps, mit denen der Benutzer den Inhalt bearbeiten kann. „Content Sync“ ermöglicht Ihnen, versionierte Archive der Seiten für das Bundling mit Apps zu erstellen. 

Normalerweise ist ein ***AEM Administrator*** dafür verantwortlich, dem AEM Mobile-Katalog eine neue Anwendung hinzuzufügen, entweder durch Erstellen einer neuen App mit dem Erstellungsassistenten oder durch Importieren einer vorhandenen Anwendung.

Von hier aus kann ein ***AEM-Autor*** (oder *Marketer*) die vordefinierten Vorlagen und Komponenten verwenden, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag &amp; Drop zu verschieben und Medien aller Typen aus dem DAM hinzuzufügen, einschließlich Bilder, Videos und Textfragmente (Inhaltsfragmente).

Die wahre Stärke von AEM Mobile besteht darin, dass ein *versierter* ***AEM-Entwickler*** benutzerdefinierte Webvorlagen und -Komponenten erweitern und erstellen kann, damit der *AEM-Autor* schöne und ansprechende mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die mobile App-Welt optimiert. Sie können jedoch sowohl mit dem Gerät als auch mit dem AEM Server (einem beliebigen Remote-Server) kommunizieren, um Endpunkte des Omniture Kanal-Dienstes zu erreichen.

>[!NOTE]
>
>Wenn der *AEM-Autor* glaubt, dass die App fertig ist, können die Beteiligten die App zunächst mit **[Adobe Verify](/help/mobile/phonegap-mobile-quickstart.md)** (verfügbar im AppStore und im PlayStore) zur Überprüfung und Genehmigung herunterladen. Sobald sie die grüne Ampel erhalten haben, können sie diese neuen oder aktualisierten Inhalte über das AEM Mobile ContentSync Content Release Management Dashboard direkt an ihre Benutzer freigeben. Eine Person kann eine beliebige Anzahl von Rollen übernehmen, das liegt an Ihnen und Ihren Führungsrichtlinien.

## Voraussetzungen {#prerequisites}

AEM Mobile ist nur eine Säule, die die gesamte AEM Plattform ausmacht.

Bevor Sie mit AEM Mobile arbeiten und den Schritten in diesem Handbuch folgen, sollten Sie mit AEM und dem AEM Mobile Control Center vertraut sein. Siehe:

[Erste Schritte mit AEM](/help/sites-deploying/deploy.md)

[Eine exemplarische Vorgehensweise des AEM Mobile-Kontrollzentrums](/help/mobile/phonegap-authoring-apps.md)

## QuickLinks für Autoren {#quicklinks-for-authors}

Informationen zu Rollen und Verantwortlichkeiten eines Autors finden Sie unter [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md).

## QuickLinks für Entwickler {#quicklinks-for-developers}

Es gibt Beispielanwendungen, die in AEM Mobile integriert werden und vom Entwickler angepasst werden können. Klicken Sie auf [Entwickeln von Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md).

In den folgenden Kapiteln erfahren Sie mehr über erweiterte Konzepte wie White Labelling Ihrer Anwendung, Lokale Anpassung, Internationalisierung, ContentSync, Targeting, Analytics und mehr.

## QuickLinks für Administratoren {#quicklinks-for-administrators}

Siehe [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md), um Ihre Mobilanwendung einzurichten und zu verwalten.

>[!NOTE]
>
>Mithilfe von Hybrid-Mobiltechnologien können Sie Rich-Mobil-Anwendungen erstellen, die offline und online mit AEM Mobile ausgeführt werden. Viele Kunden entscheiden sich dafür, Apps zu erstellen, die prüfen, ob sie online oder offline sind, und sich entsprechend verhalten.**
