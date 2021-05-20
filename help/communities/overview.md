---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über AEM Communities-Funktionen und -Einrichtung
seo-description: Überblick über AEM Communities-Funktionen und -Einrichtung
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
exl-id: d6243dff-a067-455c-a326-5f451f225efd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1446'
ht-degree: 5%

---

# Übersicht über AEM Communities {#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities lässt sich leicht eine interne Communitysite erstellen, die verbesserte Leistung und optimierte Siteverwaltung bietet und aus Besuchern wertvolle Communitymitglieder macht.

<!--
Contact your account representative for information regarding licensing of AEM Communities as well as additional licensing for enablement features and Adobe Analytics.
-->

## Communities-Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die:

* **** Informationen zu Blogs, Fragen und Antworten und Ereigniskalendern,
* Während **Insights** durch Foren, Kommentare und andere Community-Inhalte gewinnen, werden diese häufig als benutzergenerierte Inhalte (UGC) bezeichnet.
* Sie ermöglicht **Moderation** durch vertrauenswürdige Mitglieder in der Veröffentlichungsumgebung,
* **Social-** Anmeldung mit Twitter und Facebook,
* **Inline-** Übersetzung von Community-Inhalten,
* **Erstellung von Community-Gruppen** über die veröffentlichte Community-Site,
* **** Scoringto-Auszeichnung,
* **Dateifreigabe**,
* **** Benachrichtigungen und  **Aktivitäts-Streams**,
* Ermöglicht das **Tagging** (@mention) anderer registrierter Mitglieder in benutzergenerierten Inhalten, deren Aufmerksamkeit zu erregen.
* Unterstützt **Tastaturnavigation** bei Aktivierungskomponenten (z. B. Katalog- und Kurswiedergabe, Zuweisungen, Dateibibliothek) .

Communities-Funktionen können mit der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki), die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, was zu einer Website mit vielen allgemeinen Funktionen führt, die vorab an die Site angeschlossen sind.

Der [Website-Erstellungsassistent](/help/communities/sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md), die:

   * aus [Community-Funktionen](#community-functions) erstellt wurde
   * optionale Funktion [Community-Gruppen](#communitygroups)

* Verwendet Einstellungen zum Konfigurieren von:

   * Moderation
   * anmelden
   * Übersetzung

* Bietet wichtige Funktionen:

   * Responsives Design: verwendet [Twitter-Bootstrap-Designs](https://getbootstrap.com)

   * Anmelden : Selbstregistrierung, [Social Login](/help/communities/social-login.md), Benutzerprofile

      * Benachrichtigungen:
-Mitglieder sehen Ereignisse, die für sie relevant sind, und benutzergenerierte Inhalte, in denen sie [@named](/help/communities/overview.md#mentionssupport) sind.

      * Messaging: -Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen.
      * Suchen: Möglichkeit, innerhalb der Community-Site zu suchen.
      * Sprachwechsel: Möglichkeit, eine Sprache für eine [mehrsprachige Site](/help/sites-administering/translation.md) auszuwählen.

      * Administration: Zugriff für autorisierte Mitglieder, um Benutzer innerhalb der Community-Site zu moderieren und zu verwalten.

* Beseitigt viele Bearbeitungsschritte auf Seitenebene:

   * Branding: optionaler Upload eines Bannerbilds für die Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigations-Links werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind.

Um die schnelle Erstellung einer neuen Community-Site zu erleben, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Community-Inhaltsbeständigkeit {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Speicher, der speziell für benutzergenerierte Inhalte (UGC) verwendet wird, die von allen AEM (Autoren- und Veröffentlichungsinstanzen) gemeinsam verwendet werden.

Der Zugriff auf Community-Inhalte erfolgt über den Speicher-Ressourcenanbieter (SRP), der eine Ebene bereitstellt, um den Zugriff von der zugrunde liegenden Topologie zu trennen, und einen gemeinsamen Speicher für benutzergenerierte Inhalte unterstützt.

Weitere Informationen zur Persistenz von Community-Inhalten und zu empfohlenen Bereitstellungen finden Sie unter:

* [Community-Inhaltsspeicher](/help/communities/working-with-srp.md), in dem die verfügbaren SRP-Speicheroptionen für UGC erläutert werden.
* [Empfohlene Topologien](/help/communities/topologies.md), die Topologien basierend auf Anwendungsfällen und SRP-Auswahl diskutieren.
* [Upgrade auf AEM 6.5 Communities](/help/communities/upgrade.md), die nützliche Informationen über UGC beim Wechsel zu AEM 6.5 bietet.

## Communities-Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](/help/communities/consoles.md), die Folgendes enthält:

* [Sites-Konsole](/help/communities/sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community-](/help/communities/groups.md) Gruppenkonsole

* [Moderatoren-Konsole](/help/communities/moderation.md)

   * Allgemeine Massenmoderations-Benutzeroberfläche für Autoren- und Veröffentlichungsumgebungen.
   * Neue Filterkriterien.

* [Mitglieder und ](/help/communities/members.md) Groupsmanagement-Konsolen

   * Bietet die Möglichkeit, in der Autorenumgebung veröffentlichungsseitige Benutzer (Mitglieder) zu erstellen und zu verwalten.
   * Bietet die Möglichkeit, Mitglieder zu verbieten.
   * Bietet die Möglichkeit, in der Autorenumgebung veröffentlichungsseitige Benutzergruppen (Mitgliedergruppen) zu erstellen und zu verwalten.

* [](/help/communities/reports.md) ReportConsole

   * Ermöglicht die Erstellung von Berichten über Zuweisungen, Beiträge und Ansichten.

* [](/help/communities/resources.md) Ressourcenkonsole

   * Bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen.
   * Bietet Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden.

Die globale Tools-Konsole bietet Zugriff auf die folgenden Communities-Tools:

* [Site-](/help/communities/tools.md#sitetemplatesconsole) Vorlagenkonsole

   * Erstellen und verwalten Sie Community-Site-Vorlagen.

* [Gruppenvorlagen-](/help/communities/tools.md#grouptemplatesconsole) Konsole

   * Erstellen und verwalten Sie Community-Gruppenvorlagen.

* [Community ](/help/communities/tools.md#communityfunctionsconsole) Functions Console

   * Erstellen und verwalten Sie Community-Funktionen.

* [Speicherkonfigurationskonsole ](/help/communities/tools.md#storageconfiguratonconsole) 

   * Wählen Sie den [gemeinsamen Speicher](/help/communities/working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * Eine Beispielsite [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html), die ein Beispiel aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bietet, mit ihnen zu experimentieren.

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung von Community-Sites basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage bestehend aus Community-Funktionen und Community-Gruppenvorlagen bietet die Struktur für eine Community-Site, einschließlich Anmelde-, Benutzer-, Messaging-, Site-Menü-, Such-, Themen- und Branding-Funktionen.

Siehe [Site-Vorlagen-Konsole](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die von einer Community-Erfahrung erwarteten Funktionen sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, die als Community-Funktionen bezeichnet werden.

Community-Funktionen sind normale AEM Seiten enthalten Komponenten, die zu einer Funktion verknüpft sind, die einfach in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community Functions Console](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Unter-Community auf einer Community-Site durch autorisierte Benutzer und Community-Mitglieder aus der Autoren- und Veröffentlichungsumgebung.

In der Autorenumgebung können Community-Gruppen (Untergruppen) innerhalb einer vorhandenen Community-Site erstellt oder in einer vorhandenen Gruppe verschachtelt werden, wenn die Struktur der Vorlage die [Gruppenfunktion](/help/communities/functions.md#groups-function) enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Gruppenfunktion einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben oder zum Zeitpunkt der Erstellung einer neuen Community-Gruppe eine Auswahl an Vorlagen bereitgestellt wird.

Siehe auch:

* [Site-Gruppen ](/help/communities/groups.md) zur Erstellung von Untergruppen in der Autorenumgebung.
* [Gruppenvorlagen-Konsole ](/help/communities/tools-groups.md) zum Erstellen der Site-Struktur für Gruppen.
* [Erste Schritte mit AEM ](/help/communities/getting-started.md) Communities für ein Tutorial zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen.

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md), aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Das [Handbuch zu Community-Komponenten](/help/communities/components-guide.md) ist für die interaktive Untersuchung der Komponenten verfügbar.

## Communities-Typen {#types-of-communities}

### Interaktionsgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abruf von Feedback und zur Interaktion als Community-Mitglieder angesprochen werden.

Zu den Funktionen einer Interaktionsgemeinschaft zählen:

* Anmeldung
* Messaging
* Foren
* Kommentare
* Reviews
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

Um schnell eine neue Interaktionsgemeinschaft zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

### Aktivierungs-Community {#enablement-community}

Eine Aktivierungs-Community ist eine Community-Site, die Funktionen für Online-Lernen enthält.

Zu den Funktionen einer Aktivierungs-Community zählen:

* Alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community).
* Möglichkeit, Inhalt und Lernen zuzuweisen. Ressourcen für Mitglieder und Mitgliedergruppen.
* Unterstützt SCORM-Inhalte wie Quizze und Tests.
* Nachverfolgen der Fertigstellung von Zuweisungen.
* Zugriff auf Reporting und Analysen.
* Die Möglichkeit, über Foren, Nachrichten, Kommentare und Bewertungen über eine Lernressource zu sprechen.

Eine Aktivierungs-Community kann erstellt werden, wenn das [Aktivierungs-Add-on](/help/communities/enablement.md) konfiguriert ist. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung. Eine Aktivierungs-Community-Site enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Aktivierungs-Community zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

## AEM Demomaschine {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, die häufig mehr Setup erfordern als lediglich eine QuickStart-Instanz. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) ein, wie MongoDB-, Solr-, MySQL-, FFmpeg- und E-Mail-Server.

Die AEM Demomaschine umfasst:

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-Skripte mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Zu installierende Pakete.

Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Zeigen Sie eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) zur AEM Demomaschine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Besuchen Sie [Communities bereitstellen](deploy-communities.md) , um mehr über empfohlene Bereitstellungen zu erfahren.
* Besuchen Sie [Verwalten von Communities-Sites](administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, Tagging, Benachrichtigungen, Scoring und Abzeichen zu erfahren.
* Besuchen Sie [Communities entwickeln](communities.md) , um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.
* Besuchen Sie [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
