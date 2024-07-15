---
title: Übersicht über AEM Communities
description: Erfahren Sie mehr über die Grundlagen der Funktionen und Einrichtung von Adobe Experience Manager Communities.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
exl-id: d6243dff-a067-455c-a326-5f451f225efd
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 2%

---

# Übersicht über AEM Communities {#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities können Sie schnell eine On-Premise-Community-Site erstellen, die die Leistung verbessert, das Site-Management verbessert und die Konversion von Site-Besuchern in wertvolle Community-Mitglieder fördert.

## Communities-Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die:

* **Informationen** durch Blogs, Fragen und Antworten und Ereigniskalender,
* Während **durch Foren, Kommentare und andere Community-Inhalte Einblicke gewinnen konnte, werden diese oft als benutzergenerierte Inhalte (UGC) bezeichnet.**
* Dies ermöglicht die **Moderation** durch vertrauenswürdige Mitglieder in der Publish-Umgebung,
* **Anmeldung in Social** mit Twitter und Facebook,
* **Inline-Übersetzung** des Community-Inhalts,
* **Erstellung von Community-Gruppen** von der veröffentlichten Community-Site aus,
* **Scoring** zur Vergabe von Abzeichen,
* **Dateifreigabe**,
* **Benachrichtigungen** und **Aktivitäts-Streams**,
* Ermöglicht das **Tagging** (@mention) anderer registrierter Mitglieder in benutzergenerierten Inhalten, deren Aufmerksamkeit zu erregen.

Communities-Funktionen können mit der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) demonstriert werden, die öffentlich unter GitHub.com verfügbar ist, oder mit der neuen `We.Retail` Referenzimplementierung.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, was zu einer Website mit vielen allgemeinen Funktionen führt, die vorab an die Site angeschlossen sind.

Der [Assistent zur Site-Erstellung](/help/communities/sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md), d. h.:

   * aus [Community-Funktionen](#community-functions) erstellt wurde
   * optionale Funktion [Community-Gruppen](#communitygroups)

* Verwendet Einstellungen zum Konfigurieren von:

   * Moderation
   * Anmeldung
   * Übersetzung

* Bietet wichtige Funktionen:

   * Responsives Design: verwendet [Twitter Bootstrap themes](https://getbootstrap.com)

   * Anmelden : Selbstregistrierung, [Anmeldung bei sozialen Netzwerken](/help/communities/social-login.md), Benutzerprofile

      * Benachrichtigungen:
-Mitglieder sehen Ereignisse, die für sie relevant sind, und benutzergenerierte Inhalte, in denen sie [@listed](/help/communities/overview.md#mentionssupport) sind.

      * Messaging: Mitglieder können Nachrichten auf der Community-Site senden oder empfangen.
      * Suche: Möglichkeit, innerhalb der Community-Site zu suchen.
      * Sprachwechsel: Möglichkeit, eine Sprache für eine [mehrsprachige Site](/help/sites-administering/translation.md) auszuwählen.

      * Administration: Zugriff für autorisierte Mitglieder, um Benutzer auf der Community-Site zu moderieren und zu verwalten.

* Beseitigt viele Bearbeitungsschritte auf Seitenebene:

   * Branding: optionaler Upload eines Bannerbilds für die Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind.

Um die schnelle Erstellung einer Community-Site zu erleben, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Community-Inhaltspersistenz {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Speicher, der speziell für benutzergenerierte Inhalte (UGC) verwendet wird, die von allen AEM (Autoren- und Veröffentlichungsinstanzen) gemeinsam verwendet werden.

Der Zugriff auf Community-Inhalte erfolgt über den Speicher-Ressourcenanbieter (SRP), der eine Ebene bereitstellt, um den Zugriff von der zugrunde liegenden Topologie zu trennen, und einen gemeinsamen Speicher für benutzergenerierte Inhalte unterstützt.

Weitere Informationen zur Persistenz von Community-Inhalten und zu empfohlenen Bereitstellungen finden Sie unter:

* [Community-Inhaltsspeicher](/help/communities/working-with-srp.md) - beschreibt die verfügbaren SRP-Speicheroptionen für UGC.
* [Empfohlene Topologien](/help/communities/topologies.md) - beschreibt Topologien basierend auf dem Anwendungsfall und der SRP-Auswahl.
* [Aktualisierung auf AEM 6.5 Communities](/help/communities/upgrade.md) - bietet nützliche Informationen zu benutzergenerierten Inhalten beim Wechsel zu AEM 6.5.

## Communities-Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](/help/communities/consoles.md), die Folgendes enthält:

* [Sites](/help/communities/sites-console.md)-Konsole

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * Konsole [Community-Gruppen](/help/communities/groups.md)

* [Moderationskonsole](/help/communities/moderation.md)

   * Allgemeine Massenmoderations-Benutzeroberfläche für Autoren- und Publish-Umgebungen.
   * Neue Filterkriterien.

* Verwaltungskonsolen für [Mitglieder und Gruppen](/help/communities/members.md)

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite über die Autorenumgebung.
   * Ermöglicht es Ihnen, Mitglieder zu verbieten.
   * Ermöglicht die Erstellung und Verwaltung von auf der Veröffentlichungsseite befindlichen Benutzergruppen (Mitgliedergruppen) in der Autorenumgebung.

* Konsole [Berichte](/help/communities/reports.md)

   * Ermöglicht die Erstellung von Berichten über Zuweisungen, Beiträge und Ansichten.

Die globale Tools-Konsole bietet Zugriff auf die folgenden Communities-Tools:

* Konsole [Site-Vorlagen](/help/communities/tools.md#sitetemplatesconsole)

   * Erstellen und verwalten Sie Community-Site-Vorlagen.

* Konsole [Gruppenvorlagen](/help/communities/tools.md#grouptemplatesconsole)

   * Erstellen und verwalten Sie Community-Gruppenvorlagen.

* Konsole [Community-Funktionen](/help/communities/tools.md#communityfunctionsconsole)

   * Erstellen und verwalten Sie Community-Funktionen.

* Konsole [Speicherkonfiguration](/help/communities/tools.md#storageconfiguratonconsole)

   * Wählen Sie den [gemeinsamen Speicher](/help/communities/working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * Auf einer Beispielsite [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html) finden Sie ein Beispiel aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit, mit ihnen zu experimentieren.

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung von Community-Sites basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site. Es umfasst Anmelde-, Benutzerprofile-, Messaging-, Site-Menü-, Such-, Themen- und Branding-Funktionen.

Siehe [Konsole &quot;Site-Vorlagen&quot;](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die von einer Community-Erfahrung erwarteten Funktionen sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, die als Community-Funktionen bezeichnet werden.

Community-Funktionen sind normale AEM Seiten enthalten Komponenten, die zu einer Funktion verknüpft sind, die einfach in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community Functions-Konsole](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Subcommunity auf einer Community-Site durch autorisierte Benutzer und Community-Mitglieder aus der Autoren- und Veröffentlichungsumgebung.

In der Autorenumgebung können Community-Gruppen (Untergruppen) innerhalb einer vorhandenen Community-Site erstellt oder in einer vorhandenen Gruppe verschachtelt werden, wenn die Struktur der Vorlage die [Gruppenfunktion](/help/communities/functions.md#groups-function) enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppenseiten bereitstellt. Wenn eine Gruppenfunktion einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben oder zum Zeitpunkt der Erstellung einer neuen Community-Gruppe eine Auswahl an Vorlagen bereitgestellt wird.

Siehe auch:

* [Site-Gruppen-Konsole](/help/communities/groups.md) zum Erstellen von Untergruppen in der Autorenumgebung.
* [Gruppenvorlagen-Konsole](/help/communities/tools-groups.md) zum Erstellen von Site-Strukturen für Gruppen.
* [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) für ein Tutorial zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen.

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md), aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Der Leitfaden [Community-Komponenten](/help/communities/components-guide.md) ist für die interaktive Untersuchung der Komponenten verfügbar.

## Einsatzgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abruf von Feedback und zur Interaktion als Community-Mitglieder angesprochen werden.

Zu den Funktionen einer Interaktionsgemeinschaft zählen:

* Anmeldung
* Messaging
* Foren
* Kommentare
* Bewertungen
* Bewertungen
* Abstimmung
* Blogs
* Gruppen
* Kalender
* Übersetzung
* Moderation
* Benachrichtigungen
* Scoring und Abzeichen
* Analytics-Reporting

Um die schnelle Erstellung einer Interaktionsgemeinschaft zu erleben, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## AEM Demomaschine {#aem-demo-machine}

Der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, die häufig mehr eingerichtet werden müssen, als einfach eine QuickStart-Instanz zu starten. Der AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) ein, z. B. MongoDB-, Solr-, MySQL-, FFmpeg- und E-Mail-Server.

Die AEM Demomaschine umfasst:

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-Skripte mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Zu installierende Pakete.

Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, macOS und Linux® getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Zeigen Sie eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) auf der AEM Demomaschine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Besuchen Sie [Communities bereitstellen](deploy-communities.md) , wo Sie Informationen zu empfohlenen Bereitstellungen erhalten.
* Besuchen Sie [Verwalten von Communities-Sites](administer-landing.md) , wo Sie mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, Tagging, Benachrichtigungen, Scoring und Abzeichen erfahren können.
* Besuchen Sie [Entwickeln von Communities](communities.md) , wo Sie mehr über das Social-Komponenten-Framework (SCF) und die Anpassung von Communities-Komponenten und -Funktionen erfahren.
* Besuchen Sie [Authoring von Communities-Komponenten](author-communities.md) , wo Sie erfahren können, wie Sie Communities-Komponenten erstellen und konfigurieren.
