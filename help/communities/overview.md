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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 5%

---


# Übersicht über AEM Communities {#aem-communities-overview}

Mit Adobe Experience Manager (AEM) Communities lässt sich leicht eine interne Communitysite erstellen, die verbesserte Leistung und optimierte Siteverwaltung bietet und aus Besuchern wertvolle Communitymitglieder macht.

Wenden Sie sich an Ihren Kundenbetreuer, um Informationen zur Lizenzierung von AEM Communities sowie zu zusätzlichen Lizenzierungen für Aktivierungsfunktionen und Adobe Analytics zu erhalten.

## Communities - Funktionen {#communities-features}

AEM Communities ermöglicht die Entwicklung einer Beziehung zu Site-Besuchern, die:

* **Informationen** über Blogs, Fragen und Antworten und Ereignis-Kalender,
* Beim **Sammeln von Einblicken** durch Foren, Kommentare und andere Community-Inhalte, die häufig als benutzergenerierte Inhalte (UGC) bezeichnet werden.
* Es ermöglicht die **Moderation** durch vertrauenswürdige Mitglieder in der Veröffentlichungs-Umgebung,
* **Social-Anmeldung** bei Twitter und Facebook,
* **Inline-Übersetzung** von Community-Inhalten,
* **Community-Gruppen, die auf der veröffentlichten Community-Site entstehen** ,
* **Bewertung** zu Auszeichnungen,
* **Dateifreigabe**,
* **Benachrichtigungen** und **Aktivitäten**,
* Ermöglicht das **Taggen** (@Erwähnung) anderer registrierter Mitglieder in &quot;Benutzergenerierter Inhalt&quot;, um deren Aufmerksamkeit zu erregen.
* Unterstützung der **Tastaturnavigation** für Aktivierungskomponenten (z. B. Katalogwiedergabe und Kurswiedergabe, Zuweisungen, Dateibibliothek).

Communities Features können mithilfe der [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) , die öffentlich auf GitHub.com verfügbar ist, oder mit der neuen We.Retail Referenzimplementierung demonstriert werden.

## Community-Sites {#community-sites}

Eine Community-Site ist eine AEM Site, die mit einem einfachen Assistenten erstellt wurde, der zu einer Website mit vielen allgemeinen Funktionen führt, die bereits mit der Site verkabelt sind.

Der [Site-Erstellungsassistent](/help/communities/sites-console.md):

* Assembliert Funktionen der Site, basierend auf der ausgewählten [Community-Site-Vorlage](/help/communities/sites.md) :

   * aus [Community-Funktionen](#community-functions)
   * optionale [Community-Gruppen](#communitygroups) -Funktion

* Verwendet Einstellungen zum Konfigurieren:

   * Moderation
   * anmelden
   * Übersetzung

* Bietet wichtige Funktionen:

   * Responsive Design: verwendet [Twitter-Bootstrap-Themen](https://getbootstrap.com)

   * Anmelden: Selbstregistrierung, [Anmeldung](/help/communities/social-login.md)in sozialen Netzwerken, Profile von Benutzern

      * Benachrichtigungen:
-Mitglieder sehen Ereignis, die für sie relevant sind, und benutzergenerierte Inhalte, in denen sie [@erwähnt](/help/communities/overview.md#mentionssupport)werden.

      * Messaging: Mitglieder können Nachrichten innerhalb der Community-Site senden oder empfangen.
      * Suchen: Möglichkeit, innerhalb der Community-Site zu suchen.
      * Sprachwechsel: Möglichkeit, eine Sprache für eine [mehrsprachige Site](/help/sites-administering/translation.md)auszuwählen.

      * Verwaltung: Zugriff für autorisierte Mitglieder, um Benutzer innerhalb der Community-Site zu moderieren und zu verwalten.

* Dadurch werden viele Authoring-Schritte auf Seitenebene vermieden:

   * Branding: optionales Hochladen eines Bannerbilds zur Anzeige auf allen Seiten der Community-Site
   * Navigationsmenü: Navigationslinks werden für die Funktionen bereitgestellt, die in der Community-Site-Vorlage enthalten sind.

Um eine neue Community-Site schnell zu erstellen, besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md).

## Persistenz von Gemeinschaftsinhalten {#community-content-persistence}

Um die Leistung und Synchronisierung von Community-Inhalten zu verbessern, benötigt AEM Communities einen gemeinsamen Store speziell für benutzergenerierte Inhalte (UGC), die von allen AEM (Autor- und Veröffentlichungsinstanzen) freigegeben werden.

Der Zugriff auf Community-Inhalte erfolgt über den Datenspeicherung Resource Provider (SRP), eine Ebene, die den Zugriff von der zugrunde liegenden Topologie trennt und einen gemeinsamen Speicher für UGC unterstützt.

Weitere Informationen über die Persistenz von Community-Inhalten und empfohlene Bereitstellungen finden Sie unter:

* [Community Content Datenspeicherung](/help/communities/working-with-srp.md), in der die verfügbaren SRP-Datenspeicherung für UGC diskutiert werden.
* [Empfohlene Topologien](/help/communities/topologies.md), die Topologien auf Basis von Anwendungsfällen und SRP-Auswahl behandeln.
* [Upgrade auf AEM 6.5 Communities](/help/communities/upgrade.md), die nützliche Informationen über UGC beim Wechsel zu AEM 6.5 bietet.

## Communities Konsolen {#communities-consoles}

In der Authoring-Umgebung bietet die globale Navigationskonsole Zugriff auf die [Communities-Konsole](/help/communities/consoles.md), die Folgendes enthält:

* [Sites-Konsole](/help/communities/sites-console.md)

   * Site-Erstellung
   * Site-Bearbeitung
   * Site-Management
   * [Community Groups](/help/communities/groups.md) Console

* [Moderatoren-Konsole](/help/communities/moderation.md)

   * Allgemeine Benutzeroberfläche für Massenmoderation für Autoren- und Veröffentlichungsfunktionen.
   * Neue Filterkriterien.

* [Mitglieder und Gruppen](/help/communities/members.md) - Verwaltungskonsolen

   * Ermöglicht das Erstellen und Verwalten von Benutzern (Mitgliedern) auf der Veröffentlichungsseite aus der Autorenbenutzeroberfläche.
   * Bietet die Möglichkeit, Mitglieder zu verbieten.
   * Bietet die Möglichkeit, aus der Umgebung &quot;Autor&quot;aus Veröffentlichungsgruppen (Mitgliedsgruppen) zu erstellen und diese zu verwalten.

* [Report](/help/communities/reports.md) Console

   * Ermöglicht die Erstellung von Berichten zu Zuweisungen, Beiträgen und Ansichten.

* [Ressourcenkonsole](/help/communities/resources.md)

   * Bietet die Möglichkeit, Aktivierungsressourcen und Lernpfade zu erstellen.
   * Bietet Zugriff auf Berichte zu Aktivierungsressourcen und Lernpfaden.

Die Konsole für globale Tools bietet Zugriff auf die folgenden Communities-Tools:

* [Site-Vorlagenkonsole](/help/communities/tools.md#sitetemplatesconsole)

   * Erstellen und verwalten Sie Vorlagen für Community-Sites.

* [Gruppenvorlagen](/help/communities/tools.md#grouptemplatesconsole) -Konsole

   * Erstellen und verwalten Sie Community-Gruppenvorlagen.

* [Community Functions](/help/communities/tools.md#communityfunctionsconsole) Console

   * Erstellen und verwalten Sie Community-Funktionen.

* [Datenspeicherung Configuration](/help/communities/tools.md#storageconfiguratonconsole) Console

   * Wählen Sie den [gemeinsamen Store](/help/communities/working-with-srp.md) für die Site aus und konfigurieren Sie ihn.

* [Komponenten-Leitfaden](/help/communities/components-guide.md)

   * Eine Beispielsite, [Community-Komponenten](https://localhost:4502/editor.html/content/community-components/en.html), die eine Stichprobe aller Communities-Komponenten mit ihrer Standardkonfiguration und der Möglichkeit, mit ihnen zu experimentieren, bereitstellt.

## Community-Site-Vorlagen {#community-site-templates}

Die Erstellung einer Community-Site basiert auf der Auswahl einer Community-Site-Vorlage, um schnell eine Community-Site einzurichten, die unabhängig von einer Beispiel-Site ist.

Eine Community-Site-Vorlage, die aus Community-Funktionen und Community-Gruppenvorlagen besteht, bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerdaten, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

Siehe [Site-Vorlagenkonsole](/help/communities/sites.md).

## Community-Funktionen {#community-functions}

Die zu erwartenden Merkmale einer Community-Erfahrung sind bekannt. Mit AEM Communities sind diese Funktionen als Bausteine verfügbar, auch als Community-Funktionen bezeichnet.

Community-Funktionen sind normale AEM Seiten enthalten Komponenten, die zu einer Funktion verdrahtet sind, die leicht in eine Community-Site-Vorlage integriert werden kann.

See the [Community Functions console](/help/communities/functions.md).

## Community-Gruppen und Gruppenvorlagen {#community-groups-and-group-templates}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern und Community-Mitgliedern aus Autor- und Veröffentlichungsbenutzern erstellt zu werden.

Aus der Autorenfunktion können Community-Gruppen (Untergruppen) innerhalb einer bestehenden Community-Umgebung erstellt oder in einer vorhandenen Gruppe verschachtelt werden, wenn die Vorlagenstruktur die [Gruppenfunktion](/help/communities/functions.md#groups-function)enthält.

Das Erstellen einer Community-Gruppe erfordert die Auswahl einer Community-Gruppenvorlage, die das Design der Community-Gruppen-Seite(n) bereitstellt. Wenn eine Funktion &quot;Gruppen&quot;zu einer Vorlagenstruktur hinzugefügt wird, ist sie so konfiguriert, dass entweder eine Gruppenvorlage angegeben wird oder eine Auswahl von Vorlagen zum Zeitpunkt der Erstellung einer neuen Community-Gruppe bereitgestellt wird.

Siehe auch:

* [Site-Gruppenkonsole](/help/communities/groups.md) zum Erstellen von Unter-Communities in der Authoring-Umgebung.
* [Gruppenvorlagen-Konsole](/help/communities/tools-groups.md) zum Erstellen der Sitestruktur für Gruppen.
* [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) für ein Tutorial zur schnellen Erstellung einer Community-Site mit verschachtelten Gruppen.

## Community-Komponenten {#community-components}

Die [Community-Komponenten](/help/communities/author-communities.md) , aus denen eine Community-Site erstellt wird, können verwendet werden, um Communities-Funktionen zu jeder AEM Site hinzuzufügen.

Der Leitfaden [zu](/help/communities/components-guide.md) Community-Komponenten steht zur interaktiven Erforschung der Komponenten zur Verfügung.

## Arten von Gemeinschaften {#types-of-communities}

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

Besuchen Sie [Erste Schritte mit AEM Communities](/help/communities/getting-started.md), um schnell eine neue Interaktionsgemeinschaft zu erstellen.

### Aktivierungsgemeinschaft {#enablement-community}

Eine Community-Community ist eine Community-Site, die Funktionen zum Online-Lernen enthält.

Zu den Funktionen einer Community für die Aktivierung gehören:

* Alle Funktionen einer [Interaktionsgemeinschaft](#engagement-community).
* Fähigkeit, Inhalt und Lernen zuzuweisen. Ressourcen für Mitglieder und Mitgliedsgruppen.
* Unterstützt SCORM-Inhalte wie Quiz und Tests.
* Verfolgung des Abschlusses von Zuweisungen.
* Zugriff auf Berichte und Analysen.
* Die Fähigkeit, eine Unterhaltung über eine Lernressource durch Foren, Nachrichten, Kommentare und Bewertungen.

Wenn das [Enablement-Add-on konfiguriert](/help/communities/enablement.md)ist, kann eine Community für die Aktivierung erstellt werden. Dies erfordert zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung. Eine Community-Site für die Aktivierung enthält die [Zuweisungsfunktion](#community-functions).

Um die Erstellung einer neuen Community für die Aktivierung zu vereinfachen, besuchen Sie [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

## AEM {#aem-demo-machine}

Die [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine) verwaltet und führt Demos für AEM [Sites](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Sites), [Assets](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Assets), [Communities](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Communities), [Apps](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Apps) [](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Scenario%20Forms)undFormsaus, die häufig mehr Setup erfordern als das Starten einer QuickStart-Instanz. Die AEM Demo Machine richtet zusätzliche [Infrastruktur](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Infrastructure) wie MongoDB, Solr, MySQL, FFmpeg und E-Mail-Server ein.

Die AEM Demo-Maschine umfasst:

* Eine [grafische Benutzeroberfläche](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/User%20Interface).
* Apache ANT-Skripten mit konfigurierbaren [Eigenschaften](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Properties) und [Zielgruppen](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki/Command%20Line).

* Zu installierende Pakete.

Die AEM Demo Machine wurde erfolgreich mit CQ 5.5, CQ 5.6.1, AEM 6.0, AEM 6.1, AEM 6.2, AEM 6.3 und AEM 6.4 unter Windows, MacOS und Linux getestet.

Für AEM Demo Machine ist eine gültige AEM Lizenz erforderlich.

>[!NOTE]
>
>Ansicht einer [Videovorstellung](https://www.youtube.com/watch?v=zEE_zkR9fVQ&amp;feature=youtu.be) zur AEM Demomaschine (13:26).

## AEM Communities-Dokumentation {#aem-communities-documentation}

* Visit [Deploying Communities](deploy-communities.md) to learn about recommended deployments.
* Besuchen Sie [Administering Communities Sites](administer-landing.md) , um mehr über das Erstellen einer Community-Site, das Hinzufügen von Community-Gruppen, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern, das Tagging, Benachrichtigungen, das Scoring und Abzeichen zu erfahren.
* Visit [Developing Communities](communities.md) to learn about the social component framework (SCF) and customizing Communities components and features.
* Unter [Authoring Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.

