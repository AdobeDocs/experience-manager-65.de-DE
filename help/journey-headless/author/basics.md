---
title: Grundlagen zur Inhaltserstellung
description: Erfahren Sie mehr über die Konzepte und Methoden der Inhaltserstellung für Ihr Headless-CMS mit Inhaltsfragmenten.
index: true
hide: false
hidefromtoc: false
source-git-commit: 9661061a98c31fbb74bd0716dbedc7abef298f44
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 6%

---

# Authoring Grundlagen für Headless mit AEM {#author-headless-basics}

## Die Geschichte so weit {#story-so-far}

Am Anfang des [AEM Headless Content Author-Journey](overview.md) die [Einführung](introduction.md) die grundlegenden Konzepte und Terminologie für das Headless-Authoring behandelt.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie eigene Inhalte für Ihr AEM Headless-Projekt erstellen können.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung in die Grundlagen der Headless-CMS-Bearbeitung:
   * Einführung in das Authoring mit AEMaaCS
   * Einführung in Inhaltsfragmente

## Grundlegende Handhabung {#basic-handling}

Bevor Sie mit Inhaltsfragmenten umgehen, hier eine (sehr) kurze Einführung in die Verwendung von AEM....aber nichts ersetzt die Erfahrung, sich anzumelden und zu versuchen, das System zu verwenden.

### Authoring und Veröffentlichen {#author-preview-publish}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichung

Sie melden sich an und verwenden die Autorenumgebung, um Ihren Inhalt zu generieren. Wenn Sie bereit sind, veröffentlichen Sie Ihren Inhalt, damit er allgemein verfügbar wird. Für Headless wäre dies für andere Anwendungen, für Web-Seiten wäre dies für Leser im Internet.

Weitere Informationen finden Sie unter Authoring - Konzepte .

### Anmeldung {#signing-in}

Wie bei den meisten Systemen müssen Sie sich anmelden. Als Autor erhalten Sie Folgendes:

* Name des Benutzers (Konto)
* Passwort
* Link zum Zugriff auf den Anmeldebildschirm

Ihr Konto wurde mit den erforderlichen Berechtigungen konfiguriert. Sollten Sie Probleme haben, empfehlen wir Ihnen, sich an Ihr internes Projektunterstützungsteam zu wenden.

### Navigation {#navigation}

Wenn Sie sich zum ersten Mal in einem kleinen Online-Tutorial anmelden, werden einige der wichtigsten Funktionen der Benutzeroberfläche hervorgehoben.

Sie können dann über das Navigationsfenster auf wichtige Bereiche von AEM zugreifen. Für Inhaltsfragmente verwenden Sie die **Konsole &quot;Assets&quot;**.

Das Navigationsfenster kann geöffnet werden, indem Sie links oben das Symbol Adobe und dann das kleine Kompasssymbol auswählen:

![Navigationsfenster](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)

>[!NOTE]
>Inhaltsfragmente sind zwar eine Funktion von AEM **Sites**, finden Sie sie im **Assets** Konsole. Dies ist ein technisches Detail, das sich nicht auf Sie auswirken sollte, das jedoch nützlich sein könnte, um es zu erfahren.

In der Konsole können Sie Ordner auswählen, um zu Ihrem Inhaltsfragment zu navigieren, oder die Breadcrumbs (in der Kopfzeile), um in der Baumstruktur nach oben zu navigieren.

![Breadcrumb](/help/journey-headless/author/assets/headless-journey-author-navigation-02.png)

### Aktionen, Auswählen, Anzeigen {#actions-selecting-viewing}

Die **Assets** -Konsole **Aktionssymbole** und **Schnellaktionen** die Sie nach Auswahl einer Ressource verwenden können (z. B. einen Ordner oder ein Inhaltsfragment).

Schnellaktionen sind für eine einzelne Ressource verfügbar, siehe **Basel** im folgenden Beispiel:

![Schnellaktionen](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

Die Symbolleiste &quot;Aktionen&quot;bietet Zugriff auf alle Aktionen, die für das aktuelle Szenario gelten. Die verfügbaren Aktionen können sich ändern. zum Beispiel abhängig von Ihrem Standort oder davon, ob Sie mehrere Ressourcen ausgewählt haben:

![Aktionssymbolleiste](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

Mit der Ansichtauswahl können Sie das Format für die Anzeige Ihrer Ressourcen auswählen:

![Ansichtselektor](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

Mit der Schienenauswahl können Sie zusätzliche Informationen zu Elementen anzeigen. Dadurch erhalten Sie auch Zugriff auf zusätzliche Aktionen.

![Linke Leiste](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)

## Erstellen von Inhaltsfragmenten {#authoring-content-fragments}

Das war eine sehr schnelle Einführung in die AEM Benutzeroberfläche, aber hoffentlich hatten Sie die Möglichkeit, es auszuprobieren. Jetzt kommen wir zu Ihrem echten Interesse - Inhaltsfragmente für Headless.

Wir müssen die Dinge von Anfang bis Ende durchgehen, aber Ihre Instanz hat möglicherweise bereits Ordner und/oder Fragmente erstellt, die sich an verschiedenen Stellen befinden. Die Prinzipien sind dieselben.

### Organisieren und Navigieren {#organizing-and-navigating}

Wenn Sie nicht über sehr wenige Inhaltsfragmente verfügen, sollten Sie diese organisieren, damit Sie (und andere) sie erneut finden können.

#### Erstellen eines Ordners {#creating-folder}

Erstellen Sie dazu eine Reihe von Ordnern in **Dateien** -Abschnitt der Assets-Konsole. Wählen Sie die **Erstellen** Option (oben rechts), gefolgt von **Ordner**:

![Option &quot;Ordner erstellen&quot;](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Details eingeben und dann mit **Erstellen**:

![Dialogfeld &quot;Ordner erstellen&quot;](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Verwenden von Pfaden und Tags zur Beschränkung von Inhaltsfragmentmodellen, die im Ordner verfügbar sind {#tags-paths-for-models-in-folder}

Dieser Abschnitt ist etwas erweiterter. Man braucht es nicht wirklich, wenn man gerade erst anfängt und Dinge ausprobiert, aber es ist *very* nützlich, wenn Sie viele Fragmente haben. Also ist es gut, darüber zu wissen - auch wenn man es noch nicht ganz benutzt.

Ihr Inhaltsarchitekt hat alle Inhaltsfragmentmodelle erstellt, die für Ihr aktuelles Projekt erforderlich sind, und möglicherweise auch einige andere Projekte. Um Ihnen und anderen Autoren die Arbeit zu erleichtern, können Sie die Liste der für einen bestimmten Ordner verfügbaren Modelle einschränken.

Nach dem Erstellen des Ordners können Sie den Ordner öffnen **Eigenschaften**. Hier finden Sie verschiedene Registerkarten mit Informationen und Konfigurationsdetails zum Ordner. Insbesondere für Inhaltsfragmente können Sie die **Richtlinien** -Registerkarte, um bestimmte Pfade und/oder Tags für diesen Ordner zu definieren. Dadurch werden die für die Verwendung im Ordner verfügbaren Inhaltsfragmentmodelle eingeschränkt, da dies bedeutet, dass Inhaltsfragmentmodelle diese Anforderungen erfüllen müssen, bevor sie zum Generieren von Fragmenten in diesem Ordner verwendet werden können.

![Erstellen von Ordnereigenschaften - Richtlinien](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter Inhaltsfragmentmodelle - Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner.

Navigieren Sie dann durch diese Ordner, um Ihre Inhaltsfragmente zu erstellen und zu bearbeiten.

#### Just in case - Konfiguration von Folder Cloud Services {#cloud-services-folder}

Nur für den Fall...

Sie erhalten wahrscheinlich einen ersten Ordner, in dem Sie Ihre Ordner erstellen können. Dies liegt daran, dass einige Konfigurationsdetails (normalerweise von einem Entwickler oder Systemadministrator) auf den Stammordner angewendet werden müssen. Dies wird Sie wahrscheinlich nicht interessieren, aber bei Bedarf können Sie die **Konfiguration** im **Cloud Services** des Ordners **Eigenschaften**:

![Erstellen von Ordnereigenschaften - Konfiguration](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter Anwenden der Konfiguration auf Ihren Assets-Ordner .

### Erstellen eines Inhaltsfragments {#creating-fragment}

Das Erstellen eines Inhaltsfragments ist sehr ähnlich - Sie verwenden einfach das **Inhaltsfragment** stattdessen:

![Option &quot;Inhaltsfragment erstellen&quot;](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

Dieses Mal öffnet sich ein Assistent. Der erste Schritt besteht darin, das Inhaltsfragmentmodell auszuwählen, auf dem Ihr Fragment basieren soll:

![Inhaltsfragment erstellen - Modell auswählen](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

Nach dem Fortfahren mit **Nächste** Sie können Details angeben (**Allgemein** und **Erweitert**) für Ihr Fragment:

![Inhaltsfragment erstellen - Name angeben](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Bestätigen mit **Erstellen** und Sie können **Öffnen** Ihr Fragment im Editor.

### Bearbeiten eines Fragments {#editing-fragment}

Sie können ein Fragment unmittelbar nach seiner Erstellung öffnen oder indem Sie es in der Konsole &quot;Assets&quot;auswählen.

Wenn der Editor zum ersten Mal geöffnet wird, sehen Sie Folgendes:

* Eine Liste von Symbolen auf der linken Seite - bietet Ihnen Zugriff auf verschiedene Funktionsbereiche. Der Editor wird im **Varianten** -Registerkarte, wo die meisten Bearbeitungen vorgenommen werden. Sie können sich auch für die **Anmerkungen** und **Metadaten** Registerkarten.

* Eine Kopfzeile mit Informationen zum Fragment und Zugriff auf verschiedene Aktionen.

* Hauptbearbeitungsbereich - dies hängt von dem Modell ab, das zum Erstellen des Fragments verwendet wird.

Beispiele:

* Ein Fragment, für das nur mehrere Informationen erforderlich sind, von denen einige einen bestimmten Typ aufweisen. Für Headless-Inhalte sind Verweise von zentraler Bedeutung. Sie werden später in Ihrer Journey darüber erfahren.

   ![Inhaltsfragmente-Editor - Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Ein Fragment, mit dem Sie einen langen Abschnitt mit Text schreiben können. Hier finden Sie zusätzliche Optionen zum Verwalten und Formatieren des Textes. Sie können die einzelnen Textfelder auch in einem Vollbild-Editor öffnen (mithilfe des kleinen Bildschirmähnlichen Symbols auf der rechten Seite)

   ![Inhaltsfragmente-Editor - Alaska-Spirituosen](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Möglicherweise ist eine projektspezifische Dokumentation erforderlich, um Autoren dabei zu helfen, einige Felder erfolgreich auszufüllen.
>
>Allgemeine Informationen finden Sie unter Inhaltsfragmentmodelle - Datentypen und Eigenschaften .

Bestätigen Sie Ihre Aktualisierungen mit **Speichern** oder **Speichern und schließen**.

>[!NOTE]
>
>Weitere Informationen finden Sie unter Varianten - Inhaltsfragmente erstellen .

#### Was Sie (wahrscheinlich) nicht benötigen {#what-you-probably-do-not-need-to-worry-about}

OK, dies mag ein etwas seltsamer Abschnitt sein, aber sobald Sie den Inhaltsfragment-Editor öffnen und mit der Untersuchung beginnen, sehen Sie verschiedene Optionen, die (wahrscheinlich) nicht für Ihre Headless-Journey als Inhaltsautor gelten. Das ist also nur ein kurzer Sprung nach dem, was man im Headless-Kontext ignorieren kann:

* **Inhaltsfragmentmodelle**

   Der Name des Inhaltsfragmentmodells wird oben im Editor angezeigt - direkt unter dem Fragmentnamen. Dies ist auch ein Link, über den Sie zum Modell-Editor gelangen.
Inhaltsfragmentmodelle sind für Ihre Inhaltsfragmente von entscheidender Bedeutung, da sie die von Ihnen verwendete Struktur definieren. Für die Erstellung und Bearbeitung ist jedoch (in der Regel) eine andere Person, der Inhaltsarchitekte, verantwortlich.

   >[!NOTE]
   >
   >Wenn Sie mehr erfahren möchten, können Sie die Journey AEM Headless Content Architect lesen.

* **Zugehörige Inhalte**

   Das ist ganz offensichtlich, da es sich um einen Tab im Editor handelt.

   Inhaltsfragmente sind in AEM seit einigen Versionen verfügbar. Ursprünglich wurden sie für die &quot;traditionelle&quot;Verwendung bei der Seitenbearbeitung zur Verfügung gestellt....und werden weiterhin in diesem Zusammenhang verwendet. Dazu kann es gehören, Assets (z. B. Bilder) zuzuordnen, die zwar nicht in das Fragment eingebettet sind, aber für den Autor beim Erstellen einer Seite verfügbar sein müssen.

* **Vorschau**

   Dies ist eine weitere Registerkarte im Editor und bietet eine technische Ansicht, die hauptsächlich für Entwickler gedacht ist.

* **Seitenverweise aktualisieren**

   Diese Aktion ist im Abschnitt **...** (Ellipsen). Es ist für Headless-Autoren nicht interessant, da es sich auf die Seitenbearbeitung bezieht.

### Veröffentlichung {#publishing}

<!-- needs more details -->

Nachdem Sie Ihr Fragment fertig gestellt haben, können Sie **Veröffentlichen** es so, dass es für die Headless-Anwendungen verfügbar ist.

Die Veröffentlichungsaktionen sind im Editor (oder in der Symbolleiste des **Assets** console):

![Inhaltsfragmente-Editor - Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie nun die Grundlagen gelernt haben, besteht der nächste Schritt darin, [Erfahren Sie mehr über Verweise](references.md). Dadurch werden die verschiedenen verfügbaren Verweise vorgestellt und besprochen und die Erstellung von Strukturelementen mit den Fragmentverweisen beschrieben - ein wichtiger Bestandteil der Headless-Bearbeitung.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-authoring/author.md)

* [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md) - Diese Seite basiert hauptsächlich auf der **Sites** -Konsole, aber viele/die meisten Funktionen sind auch für das Authoring relevant **Inhaltsfragmente** unter **Assets** Konsole.

   * [Navigationsfenster](/help/sites-authoring/basic-handling.md#navigation-panel)

   * [Die Kopfzeile](/help/sites-authoring/basic-handling.md#the-header)

   * [Aktionssymbolleiste](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)

   * [Anzeigen und Auswählen von Ressourcen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Schienenauswahl](/help/sites-authoring/basic-handling.md#rail-selector)

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)

      * [Anwenden der Konfiguration auf Ihren Assets-Ordner](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Erstellen eines Inhaltsfragments](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [Varianten - Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Inhaltsfragmentmodelle - Datentypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Inhaltsfragmentmodelle - Eigenschaften](/help/assets/content-fragments/content-fragments-models.md#properties)

      * [Inhaltsfragmentmodelle - Zulassen von Inhaltsfragmentmodellen für Ihren Asset-Ordner](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)


* Anleitungen für den Einstieg
   * [Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [Journey AEM Headless Content Architect](/help/journey-headless/architect/overview.md)

* [AEM Headless Translation Journey](/help/journey-headless/translation/overview.md)
