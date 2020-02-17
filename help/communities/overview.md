---
title: Übersicht über AEM Communities
seo-title: Übersicht über AEM Communities
description: Überblick über die Funktionen und Einrichtung von AEM Communities
seo-description: Überblick über die Funktionen und Einrichtung von AEM Communities
uuid: 14405847-36ae-4958-bdc6-d799ecd05f06
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 44374006-f711-4af8-a1fe-f89164f79581
docset: aem65
translation-type: tm+mt
source-git-commit: 70e6f2d8366456e5091b7b775dc40914948921ab

---


# Übersicht über AEM Communities{#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities lässt sich leicht eine interne Communitysite erstellen, die verbesserte Leistung und optimierte Siteverwaltung bietet und aus Besuchern wertvolle Communitymitglieder macht.

Wenden Sie sich an Ihren Kundenbetreuer, um Informationen zur Lizenzierung von AEM Communities sowie zu zusätzlichen Lizenzierungen für Aktivierungsfunktionen und Adobe Analytics zu erhalten.

## Communities - Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die:

* **Informationen** über Blogs, Fragen und Antworten und Ereigniskalender,
* während **Gewinnen von Einblicken **durch Foren, Kommentare und andere Community-Inhalte, häufig als benutzergenerierte Inhalte (UGC) bezeichnet.
* Es ermöglicht** Moderation **durch vertrauenswürdige Mitglieder in der Veröffentlichungsumgebung,
* **Social Login **mit Twitter und Facebook,
* **Inline-Übersetzung** von Community-Inhalten,
* **Community-Gruppen erstellen **aus der veröffentlichten Community-Site,
* **Punktwertung **zur Vergabe von Ausweisen,
* **Dateifreigabe**,
* **Benachrichtigungen **und **Aktivitäten**,

* ermöglicht das **Tagging** (@Erwähnung) anderer registrierter Mitglieder in &quot;Benutzergenerierter Inhalt&quot;, um deren Aufmerksamkeit zu erregen.
* Unterstützung der **Tastaturnavigation** für Aktivierungskomponenten (z. B. Katalogwiedergabe und Kurswiedergabe, Zuweisungen, Dateibibliothek).

Communities-Funktionen können mithilfe der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) , die auf GitHub.com öffentlich verfügbar ist, oder mit der neuen We.Retail-Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM-Site, die mit einem einfachen Assistenten erstellt wurde und zu einer Website mit vielen häufig verwendeten Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](/help/communities/sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md) :

   * aus [Community-Funktionen](#community-functions)
   * optionale [Community-Gruppen](#communitygroups) -Funktion

* verwendet Einstellungen zum Konfigurieren:

   * Moderation
   * anmelden
   * Übersetzung

* bietet wesentliche Funktionen:

   * reaktionsfähiges Design:
verwendet [Twitter-Bootstrap-Designs](https://getbootstrap.com)

   * login :
Selbstregistrierung, [Social-Anmeldung](/help/communities/social-login.md), Benutzerprofile

   * Benachrichtigungen:
Mitglieder sehen Ereignisse, die für sie relevant sind, und vom Benutzer erstellte Inhalte, in denen sie [@erwähnt](/help/communities/overview.md#mentionssupport)sind.

   * Messaging:
Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen
   * suchen:
Möglichkeit, innerhalb der Community-Site zu suchen
   * Sprachwechsel:
Möglichkeit zur Auswahl einer Sprache für eine [mehrsprachige Site](/help/sites-administering/translation.md)

   * Verwaltung:
Zugriff für autorisierte Mitglieder zur Moderation und Verwaltung von Benutzern auf der Community-Site

* beseitigt viele Authoring-Schritte auf Seitenebene:

   * Branding:
optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü:
Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind.

Informationen zum schnellen Erstellen einer neuen Community-Site finden Sie unter [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Persistenz von Gemeinschaftsinhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, erfordert AEM Communities einen gemeinsamen Store speziell für benutzerdefinierte Inhalte (UGC), die von allen AEM-Instanzen (Autoren- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Speicher-Ressourcenanbieter (SRP), der eine Ebene bereitstellt, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community Content Storage](/help/communities/working-with-srp.md), der die verfügbaren SRP-Speicheroptionen für UGC erörtert.
* [Empfohlene Topologien](/help/communities/topologies.md), die Topologien auf Basis von Anwendungsfällen und SRP-Auswahl behandeln.
* [Aktualisierung auf AEM 6.5 Communities](/help/communities/upgrade.md), das nützliche Informationen zu UGC beim Wechsel zu AEM 6.5 bietet.

## Communities Konsolen {#communities-consoles}

In der Autorenumgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](/help/communities/consoles.md), die Folgendes enthält:

* [Sites-Konsole](/help/communities/sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community Groups](/help/communities/groups.md) Console

* [Moderatoren-Konsole](/help/communities/moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autor- und Veröffentlichungsumgebungen
   * neue Filterkriterien

* [Mitglieder und Gruppen](/help/communities/members.md) - Verwaltungskonsolen

   * bietet die Möglichkeit, Benutzer (Mitglieder) auf der Seite der Veröffentlichung in der Autorenumgebung zu erstellen und zu verwalten
   * ermöglicht das Verbot von Mitgliedern
   * ermöglicht die Erstellung und Verwaltung von Gruppen (Mitgliedsgruppen) auf der Seite der Veröffentlichung in der Autorenumgebung

* [Report](/help/communities/reports.md) Console

   * bietet die Möglichkeit, Berichte zu Zuweisungen, Beiträgen und Ansichten zu erstellen

* [Ressourcenkonsole](/help/communities/resources.md)

   * bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen.
   * bietet Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden

Die Konsole der globalen Tools bietet Zugriff auf die folgenden Communities-Tools:

* [Site-Vorlagenkonsole](/help/communities/tools.md#sitetemplatesconsole)

   * Erstellen und Verwalten von Community-Site-Vorlagen

* [Gruppenvorlagen](/help/communities/tools.md#grouptemplatesconsole) -Konsole

   * Erstellen und Verwalten von Gruppenvorlagen

* [Community Functions](/help/communities/tools.md#communityfunctionsconsole) Console

   * Community-Funktionen erstellen und verwalten

* [Speicherkonfigurationskonsole](/help/communities/tools.md#storageconfiguratonconsole)

   * den [gemeinsamen Store](/help/communities/working-with-srp.md) für die Site auswählen und konfigurieren

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * eine Beispielsite, [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit bietet, mit ihnen zu experimentieren

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerprofile, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Bei AEM Communities sind diese Funktionen als Bausteine, auch als Community-Funktionen bezeichnet, verfügbar.

Community-Funktionen sind normale AEM-Seiten enthalten Komponenten, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

See the [Community Functions console](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern und Community-Mitgliedern aus Autoren- und Veröffentlichungsumgebungen erstellt zu werden.

In der Autorenumgebung können Community-Gruppen (Unter-Communities) innerhalb einer bestehenden Community-Site oder in einer vorhandenen Gruppe verschachtelt erstellt werden, wenn die Struktur der Vorlage die Funktion [Gruppen enthält](/help/communities/functions.md#groups-function).

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppenkonsole](/help/communities/groups.md) zum Erstellen von Unter-Communities in der Autorenumgebung
* [Gruppenvorlagen-Konsole](/help/communities/tools-groups.md) zum Erstellen der Sitestruktur für Gruppen
* [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) für ein Tutorial zum schnellen Erstellen einer Community-Site mit verschachtelten Gruppen

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md) , aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM-Site hinzuzufügen.

Der Leitfaden[ zu ](/help/communities/components-guide.md)Community-Komponenten steht zur interaktiven Erforschung der Komponenten zur Verfügung.

## Communities {#types-of-communities}

### Einsatzgemeinschaft {#engagement-community}

Eine Interaktionsgemeinschaft ist eine Community-Site, auf der Kunden zur Information, zum Abrufen von Feedback und zur Interaktion mit Community-Mitgliedern eingeladen werden.

Zu den Funktionen einer Interaktionsgemeinschaft zählen:

* anmelden
* Messaging
* foren
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
* Zeichen und Abzeichen
* Analyseberichte

Informationen zum schnellen Erstellen einer neuen Interaktionsgemeinschaft finden Sie unter [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

### Aktivierungsgemeinschaft {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community)
* Möglichkeit, Mitgliedern und Mitgliedsgruppen Inhalte und Lernressourcen zuzuweisen
* unterstützt SCORM-Inhalte wie Quiz und Tests
* Nachverfolgung des Zuweisabschlusses
* Zugriff auf Reports &amp; Analysen
* die Möglichkeit, über eine Lernressource in Foren, Nachrichten, Kommentaren und Bewertungen zu sprechen

Wenn das [Enablement-Add-on konfiguriert](/help/communities/enablement.md)ist, kann eine Community für die Aktivierung erstellt werden. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung. Eine Community-Site für die Aktivierung enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

## AEM-Democomputer {#aem-demo-machine}

Die [AEM-Demomaschine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM- [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)undFormsaus, die häufig mehr Setup erfordern, als eine QuickStart-Instanz zu starten. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server ein.

Der AEM-Democomputer umfasst:

* eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface)
* Apache ANT-Skripten mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line)

* Pakete installieren

Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM-Lizenz erforderlich.

>[!NOTE]
>
>Sehen Sie sich eine [Videoeinführung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&feature=youtu.be) zum AEM Demo Machine an (13:26).

## Dokumentation zu AEM Communities {#aem-communities-documentation}

* Visit [Deploying Communities](/help/communities/deploy-communities.md) to learn about recommended deployments.
* Besuchen Sie [Administering Communities Sites](/help/communities/administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Tagging, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.
* Visit [Developing Communities](/help/communities/communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.
* Unter [Authoring Communities-Komponenten](/help/communities/author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

