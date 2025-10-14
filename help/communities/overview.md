---
title: Übersicht über AEM Communities
description: Erfahren Sie mehr über die Grundlagen der Funktionen und der Einrichtung von Adobe Experience Manager Communities.
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

Mit Adobe Experience Manager (AEM) Communities können Sie schnell eine lokale Community-Site erstellen, die die Leistung verbessert, die Site-Verwaltung verbessert und die Konvertierung von Site-Besuchern zu wertvollen Community-Mitgliedern fördert.

## Communities-Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die:

* **Informiert** durch Blogs, Fragen und Antworten sowie Veranstaltungskalender,
* Beim **Gewinnen von** durch Foren, Kommentare und andere Community-Inhalte, die oft als benutzergenerierte Inhalte (User-Generated Content, UGC) bezeichnet werden.
* Sie ermöglicht **Moderation** durch vertrauenswürdige Mitglieder in der Publish-Umgebung,
* **Social-** mit Twitter und Facebook,
* **Inline-Übersetzung** von Community-Inhalten,
* **Erstellung von Community** Gruppen von der veröffentlichten Community-Site aus,
* **Scoring** um Abzeichen zu vergeben,
* **Dateifreigabe**,
* **Benachrichtigungen** und **Aktivitäts-**)
* Ermöglicht **Tagging** (@mention) anderen registrierten Mitgliedern in benutzergenerierten Inhalten, um ihre Aufmerksamkeit zu erregen.

Communities-Funktionen können mit dem [AEM-Demomaschine demonstriert werden](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) der öffentlich auf GitHub.com oder mit der neuen `We.Retail`-Referenzimplementierung verfügbar ist.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM-Site, die mithilfe eines einfachen Assistenten erstellt wurde und zu einer Website mit vielen allgemeinen Funktionen führt, die vorab in die Site verkabelt sind.

Der [Assistent zur Site-Erstellung](/help/communities/sites-console.md):

* Assembliert Funktionen der Site basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md) die:

   * Erstellt aus [Community-Funktionen](#community-functions)
   * Optionale [Community-](#communitygroups))

* Verwendet Einstellungen zum Konfigurieren von:

   * Mäßigung
   * Login
   * Übersetzung

* Bietet grundlegende Funktionen:

   * Responsives Design: Verwendet [Twitter-Bootstrap-Designs](https://getbootstrap.com)

   * Anmelden : Selbstregistrierung, [Social-](/help/communities/social-login.md)-Benutzerprofile

      * Benachrichtigungen:
Mitglieder sehen Ereignisse, die für sie relevant sind, sowie benutzergenerierte Inhalte, bei denen sie [@mentioned](/help/communities/overview.md#mentionssupport) sind.

      * Messaging: Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen.
      * Suche: Möglichkeit, innerhalb der Community-Site zu suchen.
      * Sprachwechsel: Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Website](/help/sites-administering/translation.md).

      * Administration: Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern innerhalb der Community-Site.

* Beseitigt viele Bearbeitungsschritte auf Seitenebene:

   * Branding: Optionaler Upload eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks sind für die Funktionen in der Community-Site-Vorlage verfügbar.

Um zu erfahren, wie einfach es ist, schnell eine Community-Site zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Community-Inhaltspersistenz {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Speicher speziell für benutzergenerierte Inhalte, die von allen AEM-Instanzen (Autoren- und Veröffentlichungsinstanzen) gemeinsam genutzt werden.

Der Zugriff auf Community-Inhalte ist einfach über den Speicherressourcenanbieter (SRP) möglich, der eine Ebene bereitstellt, um den Zugriff von der zugrunde liegenden Topologie zu trennen, und einen gemeinsamen Speicher für benutzergenerierten Inhalt unterstützt.

Weitere Informationen zur Persistenz von Community-Inhalten und empfohlenen Bereitstellungen finden Sie unter:

* [Community-Inhaltsspeicher](/help/communities/working-with-srp.md) - Erläutert die verfügbaren SRP-Speicheroptionen für UGC.
* [Empfohlene Topologien](/help/communities/topologies.md) - Erläutert Topologien basierend auf Anwendungsfall und SRP-Auswahl.
* [Upgrade auf AEM 6.5 Communities](/help/communities/upgrade.md) liefert nützliche Informationen über benutzergenerierten Inhalt beim Wechsel zu AEM 6.5.

## Communities-Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](/help/communities/consoles.md) die Folgendes enthält:

* [Sites](/help/communities/sites-console.md)-Konsole

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community-](/help/communities/groups.md)-Konsole

* [Moderation](/help/communities/moderation.md)-Konsole

   * Allgemeine Benutzeroberfläche für die Massenmoderation für Authoring- und Publish-Umgebungen.
   * Neue Filterkriterien.

* [Mitglieder und Gruppen](/help/communities/members.md) Verwaltungskonsolen

   * Ermöglicht das Erstellen und Verwalten von veröffentlichungsseitigen Benutzern (Mitgliedern) aus der Autorenumgebung.
   * Ermöglicht das Verbot von Mitgliedern.
   * Ermöglicht das Erstellen und Verwalten von Benutzergruppen auf der Veröffentlichungsseite (Mitgliedsgruppen) in der Autorenumgebung.

* [Reports](/help/communities/reports.md)-Konsole

   * Ermöglicht die Erstellung von Berichten zu Arbeitsaufträgen, Beiträgen und Ansichten.

Die globale Tools-Konsole bietet Zugriff auf die folgenden Communities-Tools:

* [Site-Vorlagen](/help/communities/tools.md#sitetemplatesconsole)-Konsole

   * Erstellen und Verwalten von Community-Site-Vorlagen.

* [Gruppenvorlagen](/help/communities/tools.md#grouptemplatesconsole)-Konsole

   * Erstellen und Verwalten von Community-Gruppenvorlagen.

* [Community-Funktionen](/help/communities/tools.md#communityfunctionsconsole) Konsole

   * Community-Funktionen erstellen und verwalten

* [Speicherkonfiguration](/help/communities/tools.md#storageconfiguratonconsole) Konsole

   * Wählen Sie den [Common Store](/help/communities/working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * Eine Beispiel-Website [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html) bietet ein Beispiel für alle Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit, mit ihnen zu experimentieren.

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, stellt die Struktur für eine Community-Site bereit. Dazu gehören Anmeldung, Benutzerprofile, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe die [Site-Vorlagenkonsole](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die von einem Community-Erlebnis erwarteten Funktionen sind bekannt. In AEM Communities sind diese Funktionen als Bausteine verfügbar, die als Community-Funktionen bezeichnet werden.

Community-Funktionen sind normale AEM-Seiten und enthalten Komponenten, die zu einer Funktion verkabelt sind, die einfach in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community-Funktionskonsole](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion „Community-Gruppen“ bietet die Möglichkeit, dass autorisierte Benutzende und Community-Mitglieder der Autoren- und Veröffentlichungsumgebung innerhalb einer Community-Site eine Untergemeinschaft dynamisch erstellen.

Aus der Autorenumgebung heraus können Community-Gruppen (Untergruppen) innerhalb einer vorhandenen Community-Site erstellt oder innerhalb einer vorhandenen Gruppe verschachtelt werden, wenn die Struktur der Vorlage die Funktion [Gruppen](/help/communities/functions.md#groups-function) enthält.

Um eine Community-Gruppe zu erstellen, müssen Sie eine Community-Gruppenvorlage auswählen, die das Design der Community-Gruppenseiten bereitstellt. Wenn eine Gruppenfunktion zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass sie entweder eine Gruppenvorlage angibt oder zum Zeitpunkt der Erstellung einer neuen Community-Gruppe eine Auswahl von Vorlagen bereitstellt.

Siehe auch:

* [Site Groups-Konsole](/help/communities/groups.md) zum Erstellen von Untergruppen in der Autorenumgebung.
* [Gruppenvorlagen-Konsole](/help/communities/tools-groups.md) zum Erstellen von Site-Strukturen für Gruppen.
* [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) für ein Tutorial zum schnellen Erstellen einer Community-Site, einschließlich verschachtelter Gruppen.

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md) aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM-Site hinzuzufügen.

Das [Community-Komponentenhandbuch](/help/communities/components-guide.md) ist für die interaktive Untersuchung der Komponenten verfügbar.

## Engagement-Community {#engagement-community}

Eine Interaktions-Community ist eine Community-Site, die Kundinnen und Kunden dazu anregt, Informationen zu erhalten, Feedback zu erhalten und es ihnen zu ermöglichen, als Community-Mitglieder zu interagieren.

Zu den Funktionen einer Interaktionsgemeinschaft können gehören:

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
* Punktzahl und Abzeichen
* Analytics-Reporting

Um zu erfahren, wie einfach es ist, schnell eine Interaktions-Community aufzubauen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## AEM-Demomaschine {#aem-demo-machine}

Der [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, für die häufig mehr Setup erforderlich ist als das einfache Starten einer QuickStart-Instanz. Der AEM-Demomaschine richtet zusätzliche [Infrastrukturen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server ein.

Der AEM-Demomaschine umfasst:

* Eine [grafische &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-Skripte mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Zu installierende Pakete.

Der AEM-Demomaschine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, macOS und Linux® getestet.

Für den AEM-Demomaschine ist eine gültige AEM-Lizenz erforderlich.

>[!NOTE]
>
>Sehen Sie sich eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) zum AEM-Demomaschine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Unter [Bereitstellen von Communities](deploy-communities.md) erfahren Sie mehr über empfohlene Bereitstellungen.
* Unter [Verwalten von Communities-Sites](administer-landing.md) erfahren Sie mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, Tagging, Benachrichtigungen, Bewertung und Abzeichen.
* Unter [Entwicklung von Communities](communities.md) können Sie sich mit dem Social Component Framework (SCF) vertraut machen und Communities-Komponenten und -Funktionen anpassen.
* Unter [Authoring von Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten verwenden und konfigurieren können.
