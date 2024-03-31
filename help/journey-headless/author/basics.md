---
title: Grundlagen zum Authoring
description: Erfahren Sie mehr über die Konzepte und Mechanismen sw Authoring für Ihr Headless-CMS mithilfe von Inhaltsfragmenten.
exl-id: 125c4d0b-1572-4dba-823d-cdef2778f275
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1694'
ht-degree: 98%

---

# Grundlagen zum Authoring für Headless mit AEM {#author-headless-basics}

## Die bisherige Entwicklung {#story-so-far}

Zu Beginn der [AEM Headless-Inhaltsautoren-Tour](overview.md) wurden in der [Einführung](introduction.md) die grundlegenden Konzepte und die Terminologie für das Authoring für Headless behandelt.

Dieser Artikel baut auf diesen auf, damit Sie verstehen, wie Sie eigene Inhalte für Ihr AEM Headless-Projekt erstellen und bearbeiten können.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung in die Grundlagen das Headless-CMS-Authoring:
   * Einführung in das Authoring mit AEMaaCS
   * Einführung in Inhaltsfragmente

## Grundlegende Handhabung {#basic-handling}

Bevor Sie mit Inhaltsfragmenten umgehen, hier eine (sehr) kurze Einführung in die Verwendung von AEM...aber nichts ersetzt das Erlebnis, sich anzumelden und zu versuchen, das System zu verwenden.

### Authoring und Veröffentlichen {#author-preview-publish}

Eine AEM-Installation besteht im Allgemeinen aus mindestens zwei Umgebungen:

* Autor
* Veröffentlichung

Sie melden sich an und verwenden die Autorenumgebung, um Ihre Inhalte zu erzeugen. Wenn Sie fertig sind, veröffentlichen Sie Ihre Inhalte, damit sie allgemein verfügbar werden. Für Headless wäre dies für andere Anwendungen, für Web-Seiten wäre dies für Leser im Internet.

Weitere Informationen finden Sie unter „Authoring-Konzepte“.

### Anmeldung {#signing-in}

Wie bei den meisten Systemen müssen Sie sich anmelden. Als Autor erhalten Sie Folgendes:

* Name des Benutzers (Konto)
* Passwort
* Link zum Zugriff auf den Anmeldebildschirm

Ihr Konto wurde mit den erforderlichen Berechtigungen konfiguriert. Sollten Sie Probleme haben, empfiehlt Adobe Ihnen, sich an Ihr internes Projektunterstützungs-Team zu wenden.

### Navigation {#navigation}

Wenn Sie sich zum ersten Mal anmelden, wird ein kleines Online-Tutorial einige der wichtigsten Funktionen der Benutzeroberfläche vorstellen.

Sie können dann über das Navigationsfenster auf wichtige Bereiche von AEM zugreifen. Für Inhaltsfragmente verwenden Sie die **Assets-Konsole**.

Das Navigationsfenster kann geöffnet werden, indem Sie links oben auf das Adobe-Symbol und dann auf das kleine Kompasssymbol klicken:

![Navigationsfenster](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)

>[!NOTE]
>Inhaltsfragmente sind zwar eine Funktion von AEM **Sites**, Sie finden sie jedoch in der **Assets**-Konsole. Dies ist ein technisches Detail, das Sie nicht beeinträchtigen sollte, aber es könnte nützlich sein, es zu wissen.

In der Konsole können Sie Ordner auswählen, um zu Ihrem Inhaltsfragment zu gelangen, oder auf die Breadcrumbs (in der Kopfzeile) klicken, um in der Baumstruktur nach oben zu navigieren.

![Breadcrumb](/help/journey-headless/author/assets/headless-journey-author-navigation-02.png)

### Aktionen, Auswählen, Anzeigen {#actions-selecting-viewing}

Die **Assets**-Konsole verfügt über spezielle **Aktionssymbolleisten** und **Schnellaktionen**, die Sie nach der Auswahl einer Ressource (z. B. eines Ordners oder Inhaltsfragments) verwenden können.

Schnellaktionen sind für eine einzelne Ressource verfügbar, siehe **Basel** im folgenden Beispiel:

![Schnellaktionen](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

Die Aktionssymbolleiste ermöglicht den Zugriff auf die gesamte Palette der Aktionen, die für das aktuelle Szenario gelten. Die verfügbaren Aktionen können sich ändern, z. B. abhängig von Ihrem Standort oder davon, ob Sie mehrere Ressourcen ausgewählt haben:

![Aktionssymbolleiste](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

Mit dem Ansichtselektor können Sie das Format für die Anzeige Ihrer Ressourcen auswählen:

![Ansichtselektor](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

Mit der Leistenauswahl können Sie zusätzliche Informationen zu Elementen anzeigen. Dadurch erhalten Sie auch Zugriff auf zusätzliche Aktionen.

![Linke Leiste](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)

## Authoring mit Inhaltsfragmenten {#authoring-content-fragments}

Das war eine sehr schnelle Einführung in die AEM-Benutzeroberfläche und hoffentlich hatten Sie die Möglichkeit, es auszuprobieren. Jetzt kommen wir zu Ihrem echten Interesse – Inhaltsfragmente für Headless.

Wir müssen die Dinge von Anfang bis Ende durchgehen, aber in Ihrer Instanz wurden möglicherweise bereits Ordner und/oder Fragmente erstellt, die sich an verschiedenen Stellen befinden. Die Prinzipien sind dieselben.

### Organisieren und Navigieren {#organizing-and-navigating}

Wenn Sie nicht gerade sehr wenige Inhaltsfragmente haben, werden Sie sie organisieren wollen – damit Sie (und andere) sie wiederfinden können.

#### Erstellen eines Ordners {#creating-folder}

Dazu können Sie im Abschnitt **Dateien** der Assets-Konsole eine Reihe von Ordnern erstellen. Wählen Sie die Option **Erstellen** (oben rechts), gefolgt von **Ordner**:

![Option „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Daraufhin wird ein Dialogfeld geöffnet, in dem Sie die Details eingeben und dann mit **Erstellen** bestätigen können:

![Dialogfeld „Ordner erstellen“](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Verwenden von Pfaden und Tags zur Beschränkung von Inhaltsfragmentmodellen, die im Ordner verfügbar sind {#tags-paths-for-models-in-folder}

Dieser Abschnitt ist etwas komplexer. Sie benötigen ihn nicht wirklich, wenn Sie gerade erst anfangen und Dinge ausprobieren, aber er ist äußerst nützlich, wenn Sie viele Fragmente haben. Also ist es gut, ihn zu kennen – auch wenn man ihn noch nicht wirklich benutzt.

Ihr Inhaltsarchitekt hat alle Inhaltsfragmentmodelle erstellt, die für Ihr aktuelles Projekt erforderlich sind, und möglicherweise auch für einige andere Projekte. Um Ihnen und anderen Autoren die Arbeit zu erleichtern, können Sie die Liste der für einen bestimmten Ordner verfügbaren Modelle einschränken.

Nach dem Erstellen des Ordners können Sie die **Eigenschaften** des Ordners öffnen. Hier finden Sie verschiedene Registerkarten mit Informationen und Konfigurationsdetails zum Ordner. Insbesondere für Inhaltsfragmente können Sie die Registerkarte **Richtlinien** verwenden, um bestimmte Pfade und/oder Tags für diesen Ordner zu definieren. Dadurch werden die für die Verwendung im Ordner verfügbaren Inhaltsfragmentmodelle eingeschränkt, da dies bedeutet, dass Inhaltsfragmentmodelle diese Anforderungen erfüllen müssen, bevor sie zum Erzeugen von Fragmenten in diesem Ordner verwendet werden können.

![Erstellen von Ordnereigenschaften – Richtlinien](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Inhaltsfragmentmodelle – Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner“.

Navigieren Sie dann durch diese Ordner, um Ihre Inhaltsfragmente zu erstellen und zu bearbeiten.

#### Nur für den Fall – Konfiguration von Ordner-Cloud-Services {#cloud-services-folder}

Nur für den Fall...

Sie erhalten wahrscheinlich einen ersten Ordner, unter dem Sie Ihre Ordner erstellen können. Dies liegt daran, dass einige Konfigurationsdetails (normalerweise von einem Entwickler oder Systemadministrator) auf den Stammordner angewendet werden müssen. Dies ist wahrscheinlich nicht von Interesse für Sie, aber bei Bedarf können Sie die **Konfiguration** im **Cloud Service** der Ordner **Eigenschaften**:

![Erstellen von Ordnereigenschaften – Konfiguration](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Anwenden der Konfiguration auf Ihren Assets-Ordner“.

### Erstellen eines Inhaltsfragments {#creating-fragment}

Das Erstellen eines Inhaltsfragments ist sehr ähnlich –Sie verwenden stattdessen einfach die Option **Inhaltsfragment**:

![Option „Erstellen von Inhaltsfragmentmodellen“](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

Dieses Mal öffnet sich ein Assistent. Der erste Schritt besteht darin, das Inhaltsfragmentmodell auszuwählen, auf dem Ihr Fragment basieren soll:

![Inhaltsfragment erstellen – Modell auswählen](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

Nach dem Fortfahren mit **Weiter** können Sie die Details (**Standard** und **Erweitert**) für Ihr Fragment angeben:

![Inhaltsfragment erstellen – Name angeben](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Bestätigen Sie mit **Erstellen** und Sie können dann Ihr Fragment im Editor **Öffnen**.

### Fragment bearbeiten {#editing-fragment}

Sie können ein Fragment unmittelbar nach seiner Erstellung öffnen oder indem Sie es in der Assets-Konsole auswählen.

Wenn der Editor zum ersten Mal geöffnet wird, sehen Sie Folgendes:

* Eine Liste von Symbolen auf der linken Seite – diese bietet Ihnen Zugriff auf verschiedene Funktionsbereiche. Der Editor öffnet sich auf der Registerkarte **Varianten**, auf der der größte Teil der Bearbeitung stattfindet. Vielleicht interessieren Sie sich auch für die Registerkarten **Anmerkungen** und **Metadaten**.

* Eine Kopfzeile mit Informationen zum Fragment und Zugriff auf verschiedene Aktionen.

* Hauptbearbeitungsbereich – dieser hängt von dem Modell ab, das zum Erstellen des Fragments verwendet wurde.

Beispiele:

* Ein Fragment, für das nur mehrere Informationen erforderlich sind, von denen einige einen bestimmten Typ aufweisen. Für Headless-Inhalte sind Verweise von zentraler Bedeutung. Sie werden später in Ihrer Tour mehr darüber erfahren.

  ![Inhaltsfragmente-Editor – Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Ein Fragment, mit dem Sie einen langen Textabschnitt schreiben können. Hier finden Sie zusätzliche Optionen zum Verwalten und Formatieren des Textes. Sie können die einzelnen Textfelder auch in einem Vollbild-Editor öffnen (mithilfe des kleinen bildschirmähnlichen Symbols auf der rechten Seite).

  ![Inhaltsfragmente-Editor – Alaska Spirits](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Möglicherweise ist eine projektspezifische Dokumentation erforderlich, um Autoren dabei zu helfen, einige Felder erfolgreich auszufüllen.
>
>Allgemeine Informationen finden Sie unter „Inhaltsfragmentmodelle – Datentypen und Eigenschaften“.

Bestätigen Sie Ihre Aktualisierungen mit **Speichern** oder **Speichern und schließen**.

>[!NOTE]
>
>Weitere Informationen finden Sie unter „Varianten – Authoring von Inhaltsfragmenten“.

#### Worüber Sie sich (wahrscheinlich) keine Sorgen machen müssen {#what-you-probably-do-not-need-to-worry-about}

OK, dies mag ein etwas seltsamer Abschnitt sein, aber sobald Sie den Inhaltsfragment-Editor öffnen und beginnen, ihn zu erkunden, sehen Sie verschiedene Optionen, die (wahrscheinlich) nicht für Ihre Headless-Inhaltsautoren-Tour relevant sind. Dies ist also nur ein kurzer Hinweis darauf, was man im Headless-Kontext ignorieren kann:

* **Inhaltsfragmentmodelle**

  Der Name des Inhaltsfragmentmodells wird oben im Editor angezeigt – direkt unter dem Namen des Fragments. Dies ist auch ein Link, über den Sie zum Modell-Editor gelangen.
Inhaltsfragmentmodelle sind für Ihre Inhaltsfragmente von entscheidender Bedeutung, da sie die zu verwendende Struktur definieren. Für die Erstellung und Bearbeitung ist jedoch (in der Regel) eine andere Rolle, der Inhaltsarchitekt, verantwortlich.

  >[!NOTE]
  >
  >Wenn Sie mehr darüber erfahren möchten, können Sie die Journey AEM Headless-Inhaltsarchitekten-Tour lesen.

* **Zugehörige Inhalte**

  Dies ist ziemlich offensichtlich, da es sich um eine Registerkarte im Editor handelt.

  Inhaltsfragmente sind in AEM seit einigen Versionen verfügbar. Ursprünglich wurden sie für die „traditionelle“ Verwendung beim Authoring von Seiten zur Verfügung gestellt...und werden weiterhin in diesem Zusammenhang verwendet. Dazu kann es gehören, Assets (z. B. Bilder) zuzuordnen, die zwar nicht in das Fragment eingebettet sind, die aber für die Autorin bzw. den Autor beim Verfassen einer Seite verfügbar sein müssen.

* **Vorschau**

  Dies ist eine weitere Registerkarte im Editor und bietet eine technische Ansicht, die hauptsächlich für Entwickler gedacht ist.

* **Seitenverweise aktualisieren**

  Diese Aktion ist im Dropdown-Menü **…** (Auslassungspunkte) verfügbar. Es ist für Headless-Autoren nicht interessant, da es sich auf die Seitenbearbeitung bezieht.

### Veröffentlichung {#publishing}

<!-- needs more details -->

Nachdem Sie Ihr Fragment fertig gestellt haben, können Sie es **Veröffentlichen**, sodass es für die Headless-Anwendungen verfügbar ist.

Die Veröffentlichungsaktionen sind im Editor (oder in der Symbolleiste der **Assets**-Konsole) verfügbar:

![Inhaltsfragmente-Editor – Mein Fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## Wie geht es weiter {#whats-next}

Nachdem Sie nun die Grundlagen gelernt haben, lautet der nächste Schritt: [Erfahren Sie mehr über Verweise](references.md). Darin werden die verschiedenen verfügbaren Verweise vorgestellt und besprochen und die Erstellung von Strukturebenen mit den Fragmentverweisen beschrieben – ein wichtiger Bestandteil des Authoring für Headless.

## Zusätzliche Ressourcen {#additional-resources}

* [Authoring – Konzepte](/help/sites-authoring/author.md)

* [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md): Diese Seite basiert hauptsächlich auf der **Sites**-Konsole, aber viele / die meisten Funktionen sind auch für das Authoring von **Inhaltsfragmenten** unter der **Assets**-Konsole relevant.

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

   * [Varianten – Authoring von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md)

   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

      * [Inhaltsfragmentmodelle – Datentypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Inhaltsfragmentmodelle – Eigenschaften](/help/assets/content-fragments/content-fragments-models.md#properties)

      * [Inhaltsfragmentmodelle – Zulassen von Inhaltsfragmentmodellen für Ihren Assets-Ordner](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

* Anleitungen für den Einstieg
   * [Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [AEM Headless-Inhaltsarchitekten-Tour](/help/journey-headless/architect/overview.md)

* [AEM Headless-Übersetzungs-Tour](/help/journey-headless/translation/overview.md)
