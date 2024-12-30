---
title: Communities-Sites
description: Erfahren Sie mehr über die Grundlagen von Adobe Experience Manager (AEM) Communities für Administratoren, die bereits mit den grundlegenden Funktionen vertraut sind.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: e3ffc73e-2bc5-492d-b64b-750cc7d8ab9b
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# Communities-Sites {#communities-sites}

Dieser Abschnitt richtet sich an alle, die AEM Communities verwalten, und geht von ihrer Vertrautheit mit AEM Communities-Funktionen aus.

## Überblick {#overview}

Einen Überblick und Tutorials zu den ersten Schritten finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Erste Schritte mit AEM Communities](getting-started.md)

## Administrations- und Konfigurationsthemen {#administration-and-configuration-topics}

### Erstellen und Verwalten von Communities-Sites {#communities-site-creation-and-management}

* Communities [Konsolen](consoles.md)

   * [Sites](sites-console.md)

      * [Gruppen (Untergruppen)](groups.md)

   * [Moderation](moderation.md)
   * [Mitglieder- und Gruppenverwaltung](members.md)
   * [Berichte](reports.md)

* Communities [*Tools*](tools.md):

   * [Site-Vorlagen](sites.md)
   * [Gruppenvorlagen](tools-groups.md)
   * [Community-Funktionen](functions.md)
   * [Speicherkonfiguration](srp-config.md)
   * [Komponenten-Leitfaden](components-guide.md)
   * [Zeichen](badges.md)


### Benutzergenerierte Inhalte {#user-generated-content}

Eine wichtige Funktion von AEM Communities ist die Generierung benutzergenerierter Inhalte (User Generated Content, UGC) durch angemeldete Site-Besucher (Mitglieder). Weitere Informationen zum Arbeiten mit benutzergenerierten Inhalten finden Sie unter:

* [Common UGC Store](working-with-srp.md): Auswahl von SRP für die gemeinsame Speicherung von UGC
* [Moderieren von UGC](moderate-ugc.md): vertrauenswürdige Mitglieder können UGC massenweise oder im Kontext moderieren
* [Tagging von UGC](tag-ugc.md): Funktionen können so konfiguriert werden, dass Mitglieder Inhalte mit Tags versehen können
* [UGC übersetzen](translate-ugc.md): Funktionen können so konfiguriert werden, dass alle UGC übersetzt werden oder Mitgliedern die Übersetzung ausgewählter Beiträge ermöglicht wird
* [Analytics-Konfiguration](analytics.md): Ermöglicht es Adobe Analytics, Berichte zu verschiedenen Metriken bezüglich der Mitgliederaktivität zu erstellen

### Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md): Details zu Community-Mitgliedern und Mitgliedergruppen, einschließlich privilegierter Mitglieder.
* [Beitragsbeschränkungen](limits.md): Möglichkeit, die Entsendung neuer Mitglieder einzuschränken.
* [Tunneldienst](deploy-communities.md#tunnel-service-on-author): Ermöglicht den Zugriff auf Mitglieder und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenumgebung.
* [Mitglieder- und Gruppenkonsolen](members.md): Ermöglicht die Erstellung und Verwaltung von Mitgliedern auf der Veröffentlichungsseite und von der Autorenumgebung aus.
* [Benutzersynchronisierung](sync.md): für die Synchronisierung von Mitgliedern und Mitgliedergruppen über mehrere Veröffentlichungsinstanzen hinweg.
* [Social-Media-Anmeldung mit Facebook und Twitter](social-login.md): Möglichkeit für Site-Besuchende, mit ihren Facebook- oder Twitter-Anmeldeinformationen Community-Mitglied zu werden.
* [Punktzahl und Abzeichen](implementing-scoring.md): Möglichkeit, Abzeichen zuzuweisen, um die Rollen eines Mitglieds zu identifizieren und Abzeichen durch die Teilnahme an der Community zu erwerben.
* [Benachrichtigungen](notifications.md): Möglichkeit für Mitglieder, über Aktivitäten benachrichtigt zu werden, denen sie folgen.
* [Abonnements](subscriptions.md): Möglichkeit für Mitglieder, über externe E-Mails mit der Community zu interagieren.
* [Messaging](messaging.md): Möglichkeit für Mitglieder, mithilfe interner Nachrichten mit der Community zu interagieren.

### Bereitstellung {#deployment}

Der Abschnitt Bereitstellung enthält spezifische Informationen zu AEM Communities.

Die Art der Arbeit mit Community-Inhalten beeinflusst die Struktur der Bereitstellung:

* [Empfohlene Topologien für Communities](topologies.md)

Es ist wichtig, die neueste Communities-Version auf der AEM-Plattform zu installieren:

* [Neuestes Communities Feature Pack](deploy-communities.md#latestfeaturepack)

Auf der Bereitstellungsseite finden Sie weitere Communities-spezifische Informationen, z. B. für [Upgrade](upgrade.md), [Dispatcher](dispatcher.md) und [Replikation](deploy-communities.md#replication-agents-on-author).

## Verwandte Communities-Dokumentation {#related-communities-documentation}

* Unter [Bereitstellen von Communities](deploy-communities.md) erfahren Sie mehr über empfohlene Bereitstellungen.

* Unter [Entwicklung von Communities](communities.md) können Sie sich mit dem Social Component Framework (SCF) vertraut machen und Communities-Komponenten und -Funktionen anpassen.

* Unter [Authoring von Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten verwenden und konfigurieren können.
