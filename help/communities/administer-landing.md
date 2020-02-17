---
title: Communities Sites
seo-title: Communities Sites
description: Übersicht über die Dokumentation zu AEM Communities
seo-description: Übersicht über die Dokumentation zu AEM Communities
uuid: 9842ce6c-1af8-4b27-b199-07410e797ab2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 8799386a-c3b8-43cf-9f71-580ff2a81abc
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Communities Sites {#communities-sites}

Dieser Abschnitt richtet sich an diejenigen, die AEM Communities verwalten und mit AEM Communities-Funktionen vertraut sind.

## Überblick {#overview}

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Einstieg in AEM Communities](getting-started.md)
* [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md)

## Verwaltungs- und Konfigurationsthemen {#administration-and-configuration-topics}

### Communities Site-Erstellung und -Verwaltung {#communities-site-creation-and-management}

* Communities [Konsolen](consoles.md)

   * [Sites](sites-console.md)

      * [Gruppen (Untergruppen)](groups.md)
   * [Moderation](moderation.md)
   * [Mitglieder- und Gruppenverwaltung](members.md)
   * [Aktivierungsressourcen](resources.md)
   * [Berichte](reports.md)


* Communities- [*Tools *](tools.md):

   * [Site-Vorlagen](sites.md)
   * [Gruppenvorlagen](tools-groups.md)
   * [Community-Funktionen](functions.md)
   * [Speicherkonfiguration](srp-config.md)
   * [Komponenten-Leitfaden](components-guide.md)
   * [Zeichen](badges.md)


### Benutzergenerierte Inhalte {#user-generated-content}

Eine wichtige Funktion von AEM Communities ist die Erstellung benutzergenerierter Inhalte (UGC) durch angemeldete Site-Besucher (Mitglieder). Weitere Informationen zur Arbeit mit UGC finden Sie unter:

* [Häufig:](working-with-srp.md)Auswahl des SRP für die gemeinsame Speicherung von UGC
* [Moderation der Benutzerkontensteuerung](moderate-ugc.md): Vertrauenswürdige Mitglieder können UGC in loser Schüttung oder im Kontext moderieren
* [Tagging-UGC](tag-ugc.md): Funktionen können so konfiguriert werden, dass Mitglieder Inhalte taggen können
* [UGC](translate-ugc.md)übersetzen: kann so konfiguriert sein, dass alle UGC übersetzt werden oder dass Mitglieder ausgewählte Beiträge übersetzen können
* [Analytics-Konfiguration](analytics.md): Aktivierung von Adobe Analytics zur Berichterstattung über verschiedene Metriken zur Mitgliederaktivität

### Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md): Details zu Mitgliedern und Mitgliedsgruppen der Gemeinschaft, einschließlich privilegierter Mitglieder
* [Beitragsbeschränkungen](limits.md): Möglichkeit zur Beschränkung der Entsendung durch neue Mitglieder
* [Tunneldienst](deploy-communities.md#tunnel-service-on-author): ermöglicht den Zugriff auf Mitglieder und Mitgliedergruppen auf Veröffentlichungsseiten aus der Autorenumgebung
* [Mitglieder und Gruppen-Konsolen](members.md): ermöglicht das Erstellen und Verwalten von Mitgliedern und Mitgliedergruppen auf der Seite der Veröffentlichung in der Autorenumgebung
* [Benutzersynchronisierung](sync.md): zum Synchronisieren von Mitgliedern und Mitgliedergruppen über mehrere Instanzen im Veröffentlichungsmodus
* [Social-Anmeldung bei Facebook und Twitter](social-login.md): Fähigkeit von Site-Besuchern, mit ihren Facebook- oder Twitter-Anmeldeinformationen Community-Mitglied zu werden
* [Bewertung und Abzeichen](implementing-scoring.md): Fähigkeit, Abzeichen zuzuweisen, um die Rolle(en) eines Mitglieds zu identifizieren, und Abzeichen zu verdienen, durch ihre Teilnahme am Gemeinwesen
* [Benachrichtigungen](notifications.md): Fähigkeit der Mitglieder, über die Tätigkeit, die sie verfolgen, zu informieren
* [Abonnements](subscriptions.md): Fähigkeit von Mitgliedern, mit der Community per externer E-Mail zu interagieren
* [Messaging](messaging.md): Fähigkeit von Mitgliedern, mit der Community mithilfe interner Nachrichten zu interagieren

### Aktivierungsfunktionen {#enablement-features}

* [Aktivierung](enablement.md)konfigurieren: erforderliche Informationen zum korrekten Einrichten der Aktivierungsfunktionen
* [Analytics-Konfiguration](analytics.md): erforderliche Informationen zur Aktivierung der Funktionen von Adobe Analytics for Communities
* [Tagging-Aktivierungsressourcen](tag-resources.md): zum Erstellen von Erweiterungskatalogen erforderlich

### Bereitstellung {#deployment}

Der Abschnitt &quot;Bereitstellung&quot;enthält spezifische Informationen zu AEM Communities.

Die Art der Arbeit mit Gemeinschaftsinhalten beeinflusst die Struktur der Bereitstellung:

* [Empfohlene Topologien für Communities](topologies.md)

Es ist wichtig, die neueste Version von Communities auf der AEM-Plattform zu installieren:

* [Neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack)

Auf der Bereitstellungsseite finden Sie weitere Communities-spezifische Informationen, z. B. zur [Aktualisierung](upgrade.md), zum [Dispatcher](dispatcher.md) und zur [Replikation](deploy-communities.md#replication-agents-on-author).

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.

* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.

* Unter [Authoring Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.
