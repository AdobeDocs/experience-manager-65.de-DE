---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über die Funktionen und die Einrichtung von AEM Communities
seo-description: Überblick über die Funktionen und die Einrichtung von AEM Communities
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
translation-type: tm+mt
source-git-commit: 4533fa42fa3fa9f157d5ca8fee1251005b1d587e
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

* **Datendurchlauf-** Blogs, Fragen und Antworten und Ereignis-Kalender,
* Während **durch Foren, Kommentare und andere Community-Inhalte Einblicke gewinnen, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.**
* Es ermöglicht die Moderation **durch vertrauenswürdige Mitglieder in der Umgebung zum Veröffentlichen,**
* **Social-** Anmeldung bei Twitter und Facebook,
* **Inline-** Übersetzung von Community-Inhalten,
* **Community-Gruppen-** Erstellung über die veröffentlichte Community-Site,
* **** Scoringto-Auszeichnungen,
* **Dateifreigabe**,
* **** Meldungen und  **Aktivitäten**,
* Ermöglicht **Tagging** (@Erwähnung) anderer registrierter Mitglieder in &quot;Benutzergenerierter Inhalt&quot;, um deren Aufmerksamkeit zu erhalten.
* Unterstützt **Tastaturnavigation** bei Aktivierungskomponenten (z. B. Katalog- und Kurswiedergabe, Zuweisungen, Dateibibliothek).

Communities-Funktionen können mit der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki), die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, der zu einer Website mit vielen allgemeinen Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](/help/communities/sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md), die:

   * erstellt aus [Community-Funktionen](#community-functions)
   * optionale [Community-Gruppen](#communitygroups)-Funktion

* Verwendet Einstellungen zum Konfigurieren:

   * Moderation
   * anmelden
   * Übersetzung

* Bietet wichtige Funktionen:

   * Responsive Design: verwendet [Twitter-Bootstrap-Themen](https://getbootstrap.com)

   * Anmelden: Selbstregistrierung, [Social-Anmeldung](/help/communities/social-login.md), Profil des Benutzers

      * Benachrichtigungen:
-Member sehen Ereignis, die für sie relevant sind, und benutzergenerierte Inhalte, bei denen sie [@named](/help/communities/overview.md#mentionssupport) sind.

      * Messaging: Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen.
      * Suchen: Möglichkeit, innerhalb der Community-Site zu suchen.
      * Sprachwechsel: Möglichkeit, eine Sprache für eine [mehrsprachige Site](/help/sites-administering/translation.md) auszuwählen.

      * Verwaltung: Zugriff für autorisierte Mitglieder, um Benutzer innerhalb der Community-Site zu moderieren und zu verwalten.

* Dadurch werden viele Authoring-Schritte auf Seitenebene vermieden:

   * Branding: optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind.

Um eine neue Community-Site schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Persistenz von Community-Inhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, benötigt AEM Communities einen gemeinsamen Store speziell für benutzergenerierte Inhalte (UGC), die von allen AEM (Autor- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Datenspeicherung Resource Provider (SRP), eine Ebene, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community Content Datenspeicherung](/help/communities/working-with-srp.md), in der die verfügbaren SRP-Datenspeicherung für UGC diskutiert werden.
* [Empfohlene Topologien](/help/communities/topologies.md), die Topologien auf Basis von Anwendungsfällen und SRP-Auswahl behandeln.
* [Upgrade auf AEM 6.5 Communities](/help/communities/upgrade.md), die nützliche Informationen über UGC beim Wechsel zu AEM 6.5 bietet.

## Communities Konsolen {#communities-consoles}

In der Authoring-Umgebung bietet die globale Navigationskonsole Zugriff auf die Konsole [Communities](/help/communities/consoles.md), die Folgendes enthält:

* [Sites-Konsole](/help/communities/sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community ](/help/communities/groups.md) Groupsconsole

* [Moderatoren-Konsole](/help/communities/moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autoren- und Veröffentlichungsfunktionen.
   * Neue Filterkriterien.

* [Mitglieder und ](/help/communities/members.md) Groupsmanagement-Konsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite aus der Autorenbenutzeroberfläche.
   * Bietet die Möglichkeit, Mitglieder zu verbieten.
   * Bietet die Möglichkeit, aus der Umgebung &quot;Autor&quot;aus Veröffentlichungsgruppen (Mitgliedsgruppen) zu erstellen und diese zu verwalten.

* [](/help/communities/reports.md) ReportConsole

   * Ermöglicht die Erstellung von Berichten zu Zuweisungen, Beiträgen und Ansichten.

* [](/help/communities/resources.md) ResourceConsole

   * Bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen.
   * Bietet Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden.

Die Konsole für globale Tools bietet Zugriff auf die folgenden Communities-Tools:

* [Site-](/help/communities/tools.md#sitetemplatesconsole) Vorlagenkonsole

   * Erstellen und verwalten Sie Vorlagen für Community-Sites.

* [Group ](/help/communities/tools.md#grouptemplatesconsole) TemplatesConsole

   * Erstellen und verwalten Sie Community-Gruppenvorlagen.

* [Community ](/help/communities/tools.md#communityfunctionsconsole) FunctionsConsole

   * Erstellen und verwalten Sie Community-Funktionen.

* [Datenspeicherung ](/help/communities/tools.md#storageconfiguratonconsole) ConfigurationConsole

   * Wählen Sie den [gemeinsamen Speicher](/help/communities/working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit, mit ihnen zu experimentieren, bereitstellt.

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerdaten, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, auch als Community-Funktionen bezeichnet.

Community-Funktionen sind normale AEM Seiten enthalten Komponenten, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

Siehe [Community Functions console](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern und Community-Mitgliedern aus Autor- und Veröffentlichungsbenutzern erstellt zu werden.

Aus der Umgebung des Autors können Community-Gruppen (Untergruppen) innerhalb einer bestehenden Community-Site erstellt oder innerhalb einer vorhandenen Gruppe verschachtelt werden, wenn die Vorlagenstruktur die Funktion [Groups](/help/communities/functions.md#groups-function) enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppen-](/help/communities/groups.md) Konsolen zum Erstellen von Unter-Communities in der Autor-Umgebung.
* [Gruppenvorlagen ](/help/communities/tools-groups.md) Konsolen zum Erstellen der Sitestruktur für Gruppen.
* [Erste Schritte mit AEM ](/help/communities/getting-started.md) Communitys für ein Tutorial zur schnellen Erstellung einer Community-Site mit verschachtelten Gruppen.

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md), aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Das Handbuch [Community-Komponenten](/help/communities/components-guide.md) steht für die interaktive Erforschung der Komponenten zur Verfügung.

## Communities-Typen {#types-of-communities}

### Einsatzgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abrufen von Feedback und zur Interaktion mit Community-Mitgliedern eingeladen werden.

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
* Bewertung und Abzeichen
* Analytics-Berichte

Um eine neue Interaktionsgemeinschaft schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

### Aktivierungs-Community {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* Alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community).
* Fähigkeit, Inhalt und Lernen zuzuweisen. Ressourcen für Mitglieder und Mitgliedsgruppen.
* Unterstützt SCORM-Inhalte wie Quiz und Tests.
* Verfolgung des Abschlusses von Zuweisungen.
* Zugriff auf Berichte und Analysen.
* Die Fähigkeit, eine Unterhaltung über eine Lernressource durch Foren, Nachrichten, Kommentare und Bewertungen.

Eine Aktivierungs-Community kann erstellt werden, wenn das [Enablement-Add-on](/help/communities/enablement.md) konfiguriert ist. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung. Eine Community-Site für Aktivierungszwecke enthält die Funktion [Zuweisungen](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

## AEM Demo-Maschine {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) und [Forms](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms) aus, die oft mehr Setup erfordern als eine QuickStart-Instanz. Die AEM Demo Machine richtet weitere [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) ein, wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server.

Die AEM Demo-Maschine umfasst:

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-Skripten mit konfigurierbaren [properties](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties)- und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Zu installierende Pakete.

Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Ansicht a [video introduction](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) to the AEM Demo Machine (13:26).

## AEM Communities-Dokumentation {#aem-communities-documentation}

* Weitere Informationen zu empfohlenen Bereitstellungen finden Sie unter [Bereitstellen von Communities](deploy-communities.md).
* Besuchen Sie [Sites für Administrationsgemeinschaften](administer-landing.md), um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Taggen, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.
* Besuchen Sie [Developing Communities](communities.md), um mehr über das Social-Komponenten-Framework (SCF) zu erfahren und Communities-Komponenten und -Funktionen anzupassen.
* Unter [Komponenten für Authoring-Communities](author-communities.md) erfahren Sie, wie Sie mit Communities-Komponenten erstellen und konfigurieren.

