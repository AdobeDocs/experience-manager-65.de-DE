---
title: Communities Sites
seo-title: Communities Sites
description: Übersicht über die Dokumentation zur AEM Communities
seo-description: Übersicht über die Dokumentation zur AEM Communities
uuid: 9842ce6c-1af8-4b27-b199-07410e797ab2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 8799386a-c3b8-43cf-9f71-580ff2a81abc
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 9%

---


# Communities Sites {#communities-sites}

Dieser Abschnitt richtet sich an diejenigen, die AEM Communities verwalten und mit AEM Communities-Funktionen vertraut sind.

## Überblick {#overview}

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Einstieg in AEM Communities](getting-started.md)
* [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md)

## Administrations- und Konfigurationsthemen {#administration-and-configuration-topics}

### Communities - Site-Erstellung und -Verwaltung {#communities-site-creation-and-management}

* Communities [Konsolen](consoles.md)

   * [Sites](sites-console.md)

      * [Gruppen (Untergruppen)](groups.md)
   * [Moderation](moderation.md)
   * [Mitglieder- und Gruppenverwaltung](members.md)
   * [Aktivierungsressourcen](resources.md)
   * [Berichte](reports.md)


* Communities [*tools*](tools.md):

   * [Site-Vorlagen](sites.md)
   * [Gruppenvorlagen](tools-groups.md)
   * [Community-Funktionen](functions.md)
   * [Speicherkonfiguration](srp-config.md)
   * [Komponenten-Leitfaden](components-guide.md)
   * [Zeichen](badges.md)


### Benutzergenerierte Inhalte {#user-generated-content}

Eine wichtige Funktion von AEM Communities ist die Erstellung benutzergenerierter Inhalte (UGC), die von Besuchern der Site (Mitglieder) unterzeichnet wurden. Weitere Informationen zur Arbeit mit UGC finden Sie unter:

* [Häufig: ](working-with-srp.md) Auswahl von SRP für die gemeinsame Datenspeicherung von UGC
* [Moderation der Benutzerkontensteuerung](moderate-ugc.md): Vertrauenswürdige Mitglieder können UGC in loser Schüttung oder im Kontext moderieren
* [Tagging-UGC](tag-ugc.md): Funktionen können so konfiguriert werden, dass Mitglieder Inhalte taggen können
* [UGC](translate-ugc.md) übersetzen: kann so konfiguriert sein, dass alle UGC übersetzt werden oder dass Mitglieder ausgewählte Beiträge übersetzen können
* [Analytics-Konfiguration](analytics.md): Ermöglicht Adobe Analytics die Berichterstattung über verschiedene Metriken in Bezug auf die Aktivität der Mitglieder

### Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md): Details zu Mitgliedern und Mitgliedsgruppen, einschließlich privilegierter Mitglieder.
* [Beitragsbeschränkungen](limits.md): Möglichkeit, die Veröffentlichung durch neue Mitglieder zu beschränken.
* [Tunneldienst](deploy-communities.md#tunnel-service-on-author): ermöglicht den Zugriff auf Mitglieder und Mitgliedergruppen auf der Veröffentlichungsseite von der Autorendatei aus.
* [Mitglieder und Gruppen-Konsolen](members.md): ermöglicht das Erstellen und Verwalten von Mitgliedern und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenversion-Umgebung.
* [Benutzersynchronisierung](sync.md): zum Synchronisieren von Mitgliedern und Mitgliedergruppen über mehrere Instanzen im Veröffentlichungsmodus.
* [Social-Anmeldung bei Facebook und Twitter](social-login.md): Möglichkeit für Site-Besucher, mit ihren Facebook- oder Twitter-Anmeldeinformationen Community-Mitglied zu werden.
* [Bewertung und Abzeichen](implementing-scoring.md): Fähigkeit, Abzeichen zuzuweisen, um die Rolle(en) eines Mitglieds zu identifizieren und Abzeichen durch seine Teilnahme an der Gemeinschaft zu verdienen.
* [Benachrichtigungen](notifications.md): die Möglichkeit, die Mitglieder über die Aktivität zu informieren, die sie befolgen.
* [Abonnements](subscriptions.md): Möglichkeit für Mitglieder, mit der Community per externer E-Mail zu interagieren.
* [Messaging](messaging.md): Fähigkeit von Mitgliedern, mit der Community mithilfe interner Nachrichten zu interagieren.

### Aktivierungsfunktionen {#enablement-features}

* [Aktivierung](enablement.md) konfigurieren: erforderliche Informationen zum korrekten Einrichten der Aktivierungsfunktionen.
* [Analytics-Konfiguration](analytics.md): erforderliche Informationen zur Aktivierung der Funktionen von Adobe Analytics for Communities.
* [Tagging-Aktivierungsressourcen](tag-resources.md): erforderlich, um Aktivierungskataloge zu erstellen.

### Bereitstellung {#deployment}

Der Abschnitt &quot;Bereitstellung&quot;enthält spezifische Informationen zu AEM Communities.

Die Art der Arbeit mit Gemeinschaftsinhalten beeinflusst die Struktur der Bereitstellung:

* [Empfohlene Topologien für Communities](topologies.md)

Es ist wichtig, die neueste Version von Communities auf der AEM zu installieren:

* [Neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack)

Auf der Bereitstellungsseite finden Sie weitere Communities-spezifische Informationen, z. B. für [Upgrading](upgrade.md), [Dispatcher](dispatcher.md) und [Replication](deploy-communities.md#replication-agents-on-author).

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Weitere Informationen zu empfohlenen Bereitstellungen finden Sie unter [Bereitstellen von Communities](deploy-communities.md).

* Besuchen Sie [Developing Communities](communities.md), um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Unter [Komponenten für Authoring-Communities](author-communities.md) erfahren Sie, wie Sie mit Communities-Komponenten erstellen und konfigurieren.
