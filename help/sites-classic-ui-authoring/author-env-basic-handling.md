---
title: Grundlegende Handhabung
description: Eine Übersicht über die grundlegende Handhabung bei der Verwendung der Adobe Experience Manager-Autorenumgebung. Als Grundlage wird die Sites-Konsole verwendet.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 2981dc20-b2ba-4ea2-a53b-8b5fe526aa9c
source-git-commit: 3885cc51f7e821cdb352737336a29f9c4f0c2f41
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 56%

---

# Grundlegende Handhabung{#basic-handling}

>[!NOTE]
>
>* Auf dieser Seite erhalten Sie einen Überblick über die grundlegende Handhabung der Adobe Experience Manager (AEM)-Autorenumgebung. Als Grundlage wird die **Sites-Konsole** verwendet.
>
>* Einige Funktionen sind nicht in allen Konsolen verfügbar und in einigen Konsolen sind zusätzliche Funktionen verfügbar. Spezifische Informationen zu den einzelnen Konsolen und den zugehörigen Funktionen werden auf anderen Seiten ausführlicher behandelt.
>* In AEM stehen verschiedene Tastaturbefehle zur Verfügung, insbesondere bei [der Verwendung von Konsolen](/help/sites-classic-ui-authoring/author-env-keyboard-shortcuts.md) und [der Bearbeitung von Seiten](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md).
>

## Der Begrüßungsbildschirm {#the-welcome-screen}

Die klassische Benutzeroberfläche bietet eine Auswahl an Konsolen, die bekannte Mechanismen zum Navigieren und Initiieren von Aktionen verwenden, einschließlich Klicken, Doppelklicken und [Kontextmenüs](#context-menus).

Nach der Anmeldung wird der Begrüßungsbildschirm angezeigt. Es enthält eine Liste von Links zu Konsolen und Diensten:

![screen_shot_2012-01-30at61745pm](assets/screen_shot_2012-01-30at61745pm.png)

## Konsolen {#consoles}

Die Hauptkonsolen sind: 

<table>
 <tbody>
  <tr>
   <td><strong>Konsole</strong></td>
   <td><strong>Zweck</strong></td>
  </tr>
  <tr>
   <td><strong>Willkommen</strong></td>
   <td>Bietet einen Überblick über und (über Links) direkten Zugriff auf die Hauptfunktionen von AEM.</td>
  </tr>
  <tr>
   <td><strong>Digitale Assets</strong><br /> </td>
   <td>Mit diesen Konsolen können Sie Folgendes importieren: <a href="/help/sites-classic-ui-authoring/classicui-assets.md">Verwalten digitaler Assets</a> wie Bilder, Videos, Dokumente und Audiodateien. Diese Assets können dann von jeder Website verwendet werden, die auf derselben AEM-Instanz ausgeführt wird. </td>
  </tr>
  <tr>
   <td><strong>Launches</strong></td>
   <td>Hier können Sie Ihre <a href="/help/sites-classic-ui-authoring/classic-launches.md">Launches</a> verwalten. Damit können Sie Inhalte für eine künftige Version einer oder mehrerer aktivierter Webseiten entwickeln.<br /> <i>Hinweis: In der Touch-optimierten Benutzeroberfläche sind die meisten der Funktionen in der Sites-Konsole verfügbar ebenso wie die Leiste „Verweise“.</i> <i>Bei Bedarf ist diese Konsole über die Konsole Tools verfügbar. Wählen Sie Vorgänge und dann Starts aus.</i></td>
  </tr>
  <tr>
   <td><strong>Posteingang </strong></td>
   <td>Häufig sind verschiedene Personen an den Unteraufgaben eines Workflows beteiligt und jede Person muss ihren Schritt abschließen, bevor die Arbeit an die nächste Person übergeben wird. Im Posteingang werden Benachrichtigungen zu diesen Aufgaben angezeigt. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>. <br /> </td>
  </tr>
  <tr>
   <td><strong>Tagging</strong></td>
   <td>In der Tagging-Konsole können Sie Tags verwalten. Bei Tags handelt es sich um kurze Namen oder Begriffe, mit denen Sie Inhaltsbereiche kommentieren können, sodass diese leichter gefunden und organisiert werden können. Weitere Informationen finden Sie unter <a href="/help/sites-classic-ui-authoring/classic-feature-tags.md">Verwenden und Verwalten von Tags</a>.</td>
  </tr>
  <tr>
   <td><strong>Tools</strong></td>
   <td>Die <a href="/help/sites-administering/tools-consoles.md">Tools-Konsolen</a> bieten Zugriff auf verschiedene spezialisierte Tools und Konsolen, mit denen Sie Websites, digitale Assets und andere Bereiche Ihres Inhalts-Repositorys verwalten können.</td>
  </tr>
  <tr>
   <td><strong>Benutzer</strong></td>
   <td>In diesen Konsolen können Sie Zugriffsberechtigungen für Benutzerinnen bzw. Benutzer und Gruppen verwalten. Ausführliche Informationen finden Sie unter <a href="/help/sites-administering/security.md">Benutzerverwaltung und Sicherheit</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Websites</strong></td>
   <td>Mit der Konsole "Sites/Websites"können Sie <a href="/help/sites-classic-ui-authoring/classic-page-author.md">Websites erstellen, anzeigen und verwalten</a> auf Ihrer AEM Instanz ausgeführt werden. In diesen Konsolen können Sie Website-Seiten erstellen, kopieren und verschieben, Workflows starten und Seiten aktivieren (veröffentlichen). Sie können eine Seite auch zur Bearbeitung öffnen.<br /> </td>
  </tr>
  <tr>
   <td><strong>Workflows</strong></td>
   <td>Bei einem Workflow handelt es sich um eine definierte Abfolge von Schritten, die zum Ausführen einer bestimmten Aufgabe erforderlich sind. Häufig sind mehrere Personen an einer Aufgabe beteiligt und jede Person muss ihren Schritt abschließen, bevor sie die Arbeit an die nächste Person übergibt. In der Konsole „Workflow“ können Sie Workflow-Modelle erstellen und Workflow-Instanzen verwalten, die ausgeführt werden. Siehe <a href="/help/sites-administering/workflows.md">Arbeiten mit Workflows</a>.<br /> </td>
  </tr>
 </tbody>
</table>

Die Konsole **Websites** bietet zwei Bereiche zum Navigieren und Verwalten Ihrer Seiten:

* Linker Bereich

  Zeigt die Baumstruktur Ihrer Websites und die darin enthaltenen Seiten.

  Es werden auch Informationen zu anderen Aspekten oder AEM, einschließlich Projekten, Blueprints und Assets, angezeigt.

* Rechter Bereich

  Zeigt die Seiten (an der im linken Bereich ausgewählten Stelle) an und kann verwendet werden, um Maßnahmen zu ergreifen.

Von hier aus können Sie [Ihre Seiten verwalten](/help/sites-authoring/managing-pages.md), entweder über die Symbolleiste, ein Kontextmenü oder indem Sie eine Seite für weitere Aktionen öffnen.

>[!NOTE]
>
>Die grundlegende Handhabung ist in allen Konsolen gleich. Dieser Abschnitt konzentriert sich auf die Konsole **Websites**, da dies die primäre Konsole ist, die beim Bearbeiten verwendet wird.

![chlimage_1-9](assets/chlimage_1-9a.png)

## Zugreifen auf die Hilfe {#accessing-help}

In verschiedenen Konsolen (z. B. Websites) wird eine **Hilfe** -Schaltfläche verfügbar. Klicken **Hilfe** öffnet entweder Package Share oder die Dokumentations-Site.

![chlimage_1-10](assets/chlimage_1-10a.png)

Wenn Sie eine Seite bearbeiten, wird die [Sidekick verfügt auch über eine Schaltfläche für den Zugriff auf die Hilfe](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#accessing-help).

## Navigieren mit der Konsole „Websites“ {#navigating-with-the-websites-console}

Die **Websites** Die Konsole listet Ihre Inhaltsseiten in einer Baumstruktur auf (linker Bereich). Um die Navigation zu vereinfachen, können Abschnitte der Baumstruktur nach Bedarf eingeblendet (+) oder ausgeblendet (-) werden:

* Durch Klicken auf den Seitennamen im linken Bereich wird Folgendes ausgeführt:

   * Listet die untergeordneten Seiten im rechten Bereich auf
   * Erweitert die Struktur im linken Bereich.

     Aus Leistungsgründen hängt diese Aktion von der Anzahl der untergeordneten Knoten ab. Bei einer Standardinstallation funktioniert diese Erweiterungsmethode, wenn `30` oder weniger untergeordnete Knoten.

* Durch Doppelklicken auf den Seitennamen (linker Bereich) wird der Baum erweitert, auch wenn die Seite gleichzeitig geöffnet wird. Dieser Effekt ist jedoch nicht so offensichtlich.

>[!NOTE]
>
>Dieser Standardwert ( `30`) kann in den anwendungsspezifischen Konfigurationen des SiteAdmin-Widgets pro Konsole geändert werden:
>
>Führen Sie im SiteAdmin-Knoten folgende Aktionen durch:
>
>Ändern Sie den Wert der Eigenschaft:
>`treeAutoExpandMax`
>in:
>`/apps/wcm/core/content/siteadmin`
>
>Sie können die Einstellung auch global im Thema ändern:
>Ändern Sie den Wert von:
>`TREE_AUTOEXPAND_MAX`
>in:
>`/apps/cq/ui/widgets/themes/default/widgets/wcm/SiteAdmin.js`
>
>Weitere Details finden Sie unter [SiteAdmin in der CQ Widget-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.wcm.SiteAdmin).

## Seiteninformationen in der Konsole „Websites“ {#page-information-on-the-websites-console}

Der rechte Bereich der Konsole **Websites** bietet eine Listenansicht mit Informationen zu Seiten:

![page-info](assets/page-info.png)

Die folgenden sind verfügbar, ein Teil dieser Felder wird standardmäßig angezeigt:

<table>
 <tbody>
  <tr>
   <td><strong>Spalte</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Miniaturansicht</td>
   <td>Zeigt eine Miniaturansicht für die Seite an.</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Der Titel, der auf der Seite angezeigt wird</td>
  </tr>
  <tr>
   <td>Name</td>
   <td>Der Name AEM verweist auf die Seite</td>
  </tr>
  <tr>
   <td>Veröffentlicht</td>
   <td>Gibt an, ob die Seite veröffentlicht wurde, und gibt Datum und Uhrzeit der Veröffentlichung an.</td>
  </tr>
  <tr>
   <td>Geändert</td>
   <td>Gibt an, ob die Seite geändert wurde, und gibt Datum und Uhrzeit der Änderung an. Um Änderungen zu speichern, müssen Sie die Seite aktivieren.</td>
  </tr>
  <tr>
   <td>Scene7 Publish</td>
   <td>Gibt an, ob die Seite in Scene7 veröffentlicht wurde.<br /> </td>
  </tr>
  <tr>
   <td>Status</td>
   <td>Gibt den Status der Seite an, z. B. ob die Seite Teil eines Workflows oder einer Live Copy ist oder ob eine Seite gesperrt ist.</td>
  </tr>
  <tr>
   <td>Impressionen</td>
   <td>Zeigt die Aktivität auf einer Seite in Anzahl der Treffer an.</td>
  </tr>
  <tr>
   <td>Vorlage</td>
   <td>Gibt die Vorlage an, auf der eine Seite basiert.</td>
  </tr>
  <tr>
   <td>In Workflow</td>
   <td>Zeigt an, wenn sich die Seite in einem Workflow befindet.</td>
  </tr>
  <tr>
   <td>Gesperrt durch</td>
   <td>Zeigt an, wann eine Seite gesperrt wurde und welches Benutzerkonto sie gesperrt hat.</td>
  </tr>
  <tr>
   <td>Live Copy</td>
   <td>Zeigt an, wann die Seite Teil einer Live Copy ist.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Um die sichtbaren Spalten auszuwählen, bewegen Sie den Mauszeiger über einen Spaltentitel. Ein Dropdown-Menü wird angezeigt und von hier aus können Sie die **Spalten** -Option.

Die Farben neben den Seiten in den Spalten **Veröffentlicht** und **Geändert** geben den Veröffentlichungsstatus an:

| **Spalte** | **Farbe** | **Beschreibung** |
|---|---|---|
| Veröffentlicht | Grün | Die Veröffentlichung war erfolgreich. Der Inhalt wird veröffentlicht. |
| Veröffentlicht | Gelb | Die Veröffentlichung steht aus. Die Bestätigung der Veröffentlichung ist noch nicht im System eingegangen. |
| Veröffentlicht | Rot | Veröffentlichung fehlgeschlagen. Es besteht keine Verbindung zur Publishing-Instanz. Dies kann auch bedeuten, dass der Inhalt deaktiviert wurde. |
| Veröffentlicht | *blank* | Diese Seite wurde noch nie veröffentlicht. |
| Geändert | Blau | Die Seite wurde seit der letzten Veröffentlichung geändert. |
| Geändert | *blank* | Diese Seite wurde noch nie geändert, auch nicht seit der letzten Veröffentlichung. |

## Kontextmenüs {#context-menus}

Die klassische Benutzeroberfläche nutzt für die Navigation und für das Starten von Aktionen vertraute Mechanismen wie Klicks oder Doppelklicks. Abhängig von der aktuellen Situation stehen auch verschiedene Kontextmenüs zur Verfügung (geöffnet mit der rechten Maustaste):

![chlimage_1-11](assets/chlimage_1-11a.png)
