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

Dieser Abschnitt richtet sich an diejenigen, die AEM Communities verwalten und mit AEM Communities-Funktionen vertraut sind.

## Überblick {#overview}

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

* [Allgemeiner UGC-Store](working-with-srp.md): Auswahl von SRP für freigegebenen Speicher von UGC
* [Moderieren von benutzergenerierten Inhalten](moderate-ugc.md): vertrauenswürdige Mitglieder können benutzergenerierte Inhalte in großen Mengen oder im Kontext moderieren
* [Tagging von UGC](tag-ugc.md): Funktionen können so konfiguriert sein, dass Mitglieder Inhalte taggen können.
* [UGC übersetzen](translate-ugc.md): Funktionen können so konfiguriert sein, dass alle benutzergenerierten Inhalte übersetzt werden oder es Mitgliedern gestattet ist, ausgewählte Beiträge zu übersetzen
* [Analytics-Konfiguration](analytics.md): Aktivierung von Adobe Analytics für Berichte zu verschiedenen Metriken zur Mitgliederaktivität

### Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md): Details zu Community-Mitgliedern und Mitgliedergruppen, einschließlich privilegierter Mitglieder.
* [Beitragsbeschränkungen](limits.md): Möglichkeit, die Veröffentlichung durch neue Mitglieder zu beschränken.
* [Tunneldienst](deploy-communities.md#tunnel-service-on-author): ermöglicht den Zugriff auf Mitglieder und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenumgebung.
* [Mitglieder und Gruppen-Konsolen](members.md): Ermöglicht die Erstellung und Verwaltung von Mitgliedern und Mitgliedergruppen auf der Veröffentlichungsseite über die Autorenumgebung.
* [Benutzersynchronisierung](sync.md): zum Synchronisieren von Mitgliedern und Mitgliedergruppen über mehrere Veröffentlichungsinstanzen hinweg.
* [Social-Anmeldung bei Facebook und Twitter](social-login.md): Möglichkeit für Site-Besucher, mit ihren Facebook- oder Twitter-Anmeldeinformationen Community-Mitglied zu werden.
* [Scoring und Badges](implementing-scoring.md): Möglichkeit, Abzeichen zuzuweisen, um Rollen eines Mitglieds zu identifizieren, und Abzeichen zu sammeln, indem Mitglieder an der Community teilnehmen.
* [Benachrichtigungen](notifications.md): Möglichkeit für Mitglieder, über die ihnen anschließende Aktivität informiert zu werden.
* [Abonnements](subscriptions.md): Möglichkeit für Mitglieder, mit der Community per externer E-Mail zu interagieren.
* [Messaging](messaging.md): Möglichkeit für Mitglieder, mithilfe interner Nachrichten mit der Community zu interagieren.

### Bereitstellung {#deployment}

Der Abschnitt &quot;Bereitstellung&quot;enthält AEM Communities-spezifische Informationen.

Die Art der Arbeit mit Community-Inhalten beeinflusst die Struktur der Implementierung:

* [Empfohlene Topologien für Communities](topologies.md)

Es ist wichtig, die neueste Communities-Version auf der AEM zu installieren:

* [Neuestes Communities Feature Pack](deploy-communities.md#latestfeaturepack)

Auf der Bereitstellungsseite finden Sie weitere Communities-spezifische Informationen, z. B. für die [Aktualisierung](upgrade.md), [Dispatcher](dispatcher.md) und die [Replikation](deploy-communities.md#replication-agents-on-author).

## Verwandte Communities - Dokumentation {#related-communities-documentation}

* Besuchen Sie [Communities bereitstellen](deploy-communities.md) , wo Sie Informationen zu empfohlenen Bereitstellungen erhalten.

* Besuchen Sie [Entwickeln von Communities](communities.md) , wo Sie mehr über das Social-Komponenten-Framework (SCF) und die Anpassung von Communities-Komponenten und -Funktionen erfahren.

* Besuchen Sie [Authoring von Communities-Komponenten](author-communities.md) , wo Sie erfahren können, wie Sie Communities-Komponenten erstellen und konfigurieren.
