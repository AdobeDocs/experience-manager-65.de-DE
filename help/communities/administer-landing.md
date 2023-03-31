---
title: Communities-Sites
seo-title: Communities Sites
description: Überblick über die Dokumentation zu AEM Communities
seo-description: Overview of the AEM Communities documentation
uuid: 9842ce6c-1af8-4b27-b199-07410e797ab2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 8799386a-c3b8-43cf-9f71-580ff2a81abc
role: Admin
exl-id: e3ffc73e-2bc5-492d-b64b-750cc7d8ab9b
source-git-commit: 4dbbcc41757843d3b2d5a3bbb2656ef587e83d2c
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 5%

---

# Communities-Sites {#communities-sites}

Dieser Abschnitt richtet sich an diejenigen, die AEM Communities verwalten und mit AEM Communities-Funktionen vertraut sind.

## Übersicht {#overview}

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Erste Schritte mit AEM Communities](getting-started.md)

## Administrations- und Konfigurationsthemen {#administration-and-configuration-topics}

### Communities Site-Erstellung und -Verwaltung {#communities-site-creation-and-management}

* Communities [Konsolen](consoles.md)

   * [Sites](sites-console.md)

      * [Gruppen (Untergruppen)](groups.md)
   * [Moderation](moderation.md)
   * [Mitglieder und Gruppenverwaltung](members.md)
   * [Berichte](reports.md)


* Communities [*tools*](tools.md):

   * [Site-Vorlagen](sites.md)
   * [Gruppenvorlagen](tools-groups.md)
   * [Community-Funktionen](functions.md)
   * [Speicherkonfiguration](srp-config.md)
   * [Komponenten-Leitfaden](components-guide.md)
   * [Zeichen](badges.md)


### Benutzergenerierte Inhalte {#user-generated-content}

Eine wichtige Funktion von AEM Communities ist die Erstellung benutzergenerierter Inhalte (UGC), die von angemeldeten Site-Besuchern (Mitgliedern) erstellt wurden. Weitere Informationen zur Arbeit mit UGC finden Sie unter:

* [Häufiger UGC Store](working-with-srp.md): Auswahl des SRP für die gemeinsame Speicherung von UGC
* [Moderieren von benutzergenerierten Inhalten](moderate-ugc.md): vertrauenswürdige Mitglieder können UGC in großen Mengen oder im Kontext moderieren
* [Tagging von benutzergenerierten Inhalten](tag-ugc.md): -Funktionen so konfiguriert werden, dass Mitglieder Inhalte taggen können
* [UGC übersetzen](translate-ugc.md): -Funktionen können so konfiguriert werden, dass alle UGC-Dateien übersetzt werden oder Mitglieder ausgewählte Beiträge übersetzen können
* [Analytics-Konfiguration](analytics.md): Aktivierung von Adobe Analytics für Berichte zu verschiedenen Metriken zur Mitgliederaktivität

### Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md): Details zu Community-Mitgliedern und Mitgliedergruppen, einschließlich privilegierter Mitglieder.
* [Beitragsbeschränkungen](limits.md): Möglichkeit, die Veröffentlichung durch neue Mitglieder zu beschränken.
* [Tunneldienst](deploy-communities.md#tunnel-service-on-author): ermöglicht den Zugriff auf Mitglieder und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenumgebung.
* [Mitglieder und Gruppenkonsolen](members.md): ermöglicht die Erstellung und Verwaltung von Mitgliedern und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenumgebung.
* [Benutzersynchronisierung](sync.md): zum Synchronisieren von Mitgliedern und Mitgliedergruppen über mehrere Veröffentlichungsinstanzen hinweg.
* [Anmeldung über Social Media mit Facebook und Twitter](social-login.md): Möglichkeit für Site-Besucher, mit ihren Facebook- oder Twitter-Anmeldeinformationen Community-Mitglied zu werden.
* [Scoring und Abzeichen](implementing-scoring.md): Möglichkeit, Abzeichen zuzuweisen, um die Rolle(en) eines Mitglieds zu identifizieren, und Abzeichen zu sammeln, wenn Mitglieder an der Community teilnehmen.
* [Benachrichtigungen](notifications.md): Möglichkeit für Mitglieder, über die von ihnen verfolgte Aktivität informiert zu werden.
* [Abonnements](subscriptions.md): Möglichkeit für Mitglieder, mit der Community über externe E-Mails zu interagieren.
* [Messaging](messaging.md): Möglichkeit für Mitglieder, mithilfe interner Nachrichten mit der Community zu interagieren.

### Implementierung {#deployment}

Der Abschnitt &quot;Bereitstellung&quot;enthält AEM Communities-spezifische Informationen.

Die Art der Arbeit mit Community-Inhalten beeinflusst die Struktur der Implementierung:

* [Empfohlene Topologien für Communities](topologies.md)

Es ist wichtig, die neueste Communities-Version auf der AEM zu installieren:

* [Neuestes Communities Feature Pack](deploy-communities.md#latestfeaturepack)

Auf der Bereitstellungsseite finden Sie weitere Communities-spezifische Informationen, z. B. für [Upgrade](upgrade.md), [Dispatcher](dispatcher.md) und [Replikation](deploy-communities.md#replication-agents-on-author).

## Verwandte Communities - Dokumentation {#related-communities-documentation}

* Besuch [Bereitstellen von Communities](deploy-communities.md) , um mehr über empfohlene Bereitstellungen zu erfahren.

* Besuch [Entwickeln von Communities](communities.md) , um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.

* Besuch [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
