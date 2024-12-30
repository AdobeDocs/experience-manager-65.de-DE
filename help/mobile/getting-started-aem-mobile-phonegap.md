---
title: AEM Adobe PhoneGap
description: AEM kann in PhoneGap integriert werden, damit Sie mithilfe von AEM-Seiten problemlos Apps erstellen können. Auf dieser Seite finden Sie Informationen zu den ersten Schritten mit Adobe PhoneGap Enterprise.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
exl-id: d989e235-5993-4738-8523-5b9a5f6bf712
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 10%

---

# AEM Adobe PhoneGap{#aem-adobe-phonegap}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM kann in PhoneGap integriert werden, damit Sie mithilfe von AEM-Seiten problemlos Apps erstellen können. Mit PhoneGap können Benutzer Dienstprogramm-Apps erstellen, mit denen Benutzer mit dem Inhalt arbeiten können. Mit der Inhaltssynchronisierung können Sie versionierte Archive von Seiten erstellen, die mit -Programmen gebündelt werden.

In der Regel ist ein ***AEM*** Administrator dafür verantwortlich, dem AEM Mobile-Katalog eine neue Anwendung hinzuzufügen, entweder indem er eine Anwendung mit dem Erstellungsassistenten erstellt oder indem er eine bestehende Anwendung importiert.

Von hier aus kann ein ***AEM-Autor*** (oder *Marketer*) jetzt die vordefinierten Vorlagen und Komponenten verwenden, um Seiten hinzuzufügen und zu bearbeiten, Komponenten per Drag-and-Drop zu verschieben und Medien aller Art aus dem DAM hinzuzufügen, einschließlich Bildern, Videos und Textfragmenten (Inhaltsfragmenten).

Die eigentliche Stärke von AEM Mobile besteht darin, dass ein *versierter* ***AEM-Entwickler*** benutzerdefinierte Web-Vorlagen und -Komponenten erweitern und erstellen kann, damit der *AEM-Autor* ansprechende mobile Erlebnisse erstellen kann. Diese Vorlagen und Komponenten sind nicht nur für die Welt der mobilen App optimiert, sondern kommunizieren sowohl mit dem Gerät als auch mit dem AEM-Server (einem beliebigen Remote-Server) an Omni-Channel-Service-Endpunkte.

>[!NOTE]
>
>Wenn der *AEM-Autor* der Meinung ist, dass die App bereit ist, kann er die App zunächst mit **[Adobe Verify](/help/mobile/phonegap-mobile-quickstart.md)** (im AppStore und im PlayStore verfügbar) zur Überprüfung und Genehmigung herunterladen. Sobald sie grünes Licht erhalten haben, können sie diese neuen oder aktualisierten Inhalte direkt über das Dashboard der Inhaltsveröffentlichungsverwaltung von AEM Mobile ContentSync für ihre Benutzer veröffentlichen. Eine Person kann beliebig viele Rollen übernehmen, das liegt an Ihnen und Ihren Governance-Richtlinien.

## Voraussetzungen {#prerequisites}

AEM Mobile ist nur eine Säule der gesamten AEM-Plattform.

Bevor Sie mit AEM Mobile arbeiten und die Schritte in diesem Erste-Schritte-Handbuch befolgen, sollten Benutzerinnen und Benutzer mit AEM und dem AEM Mobile Control Center vertraut sein. Siehe:

[Erste Schritte mit AEM](/help/sites-deploying/deploy.md)

[Eine exemplarische Vorgehensweise des AEM Mobile Control Centers](/help/mobile/phonegap-authoring-apps.md)

## Schnelllinks für Autoren {#quicklinks-for-authors}

Unter [Authoring für Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md) erfahren Sie mehr über die Rollen und Zuständigkeiten eines Autors.

## Schnelllinks für Entwickler {#quicklinks-for-developers}

Es gibt Beispielanwendungen, die in AEM Mobile integriert werden und vom Entwickler angepasst werden können. Klicken Sie auf [Entwickeln von Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md).

In den folgenden Kapiteln erfahren Sie mehr über erweiterte Konzepte wie White Labeling für Ihre Anwendung, Lokalisierung, Internationalisierung, ContentSync, Targeting, Analytics und mehr.

## Schnelllinks für Administratoren {#quicklinks-for-administrators}

Informationen [ Einrichten und Verwalten Ihrer Mobile App finden Sie unter Verwalten von Inhalten ](/help/mobile/administer-phonegap.md) Adobe PhoneGap Enterprise mit AEM .

>[!NOTE]
>
>AEM Mobile Mit hybriden Mobiltechnologien können Sie umfangreiche Mobile Apps erstellen, die *offline und online ausgeführt*. Tatsächlich entscheiden sich viele Kunden für die Erstellung von Apps, die prüfen, ob sie online oder offline sind, und sich entsprechend verhalten.
