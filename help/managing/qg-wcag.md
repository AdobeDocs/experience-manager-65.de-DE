---
title: Kurzanleitung zu WCAG 2.1
description: Kurzanleitung zu WCAG 2.1
translation-type: tm+mt
source-git-commit: a8e7fe89376b30df0b1c5403aabea6862cef09fc
workflow-type: tm+mt
source-wordcount: '1770'
ht-degree: 86%

---


# Kurzanleitung zu WCAG 2.1{#quick-guide-to-wcag}

Adobe Experience Manager (AEM) wurde entwickelt, um die Einhaltung der Richtlinien zur Barrierefreiheit für Webinhalte zu maximieren.

The [Web Content Accessibility Guidelines (WCAG) version 2.1](https://www.w3.org/TR/WCAG/) are a set of internationally recognized guidelines developed by the [World Wide Web Consortium (W3C)](https://www.w3.org/) under their [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/).

>[!NOTE]
> 
> WCAG 2.1 aktualisiert ab 2008 die vorherige Version WCAG 2.0. Siehe [WCAG 2.1 – Vergleich mit WCAG 2.0](https://www.w3.org/TR/WCAG21/#comparison-with-wcag-2-0).

>[!NOTE]
> 
>Eine [aktualisierte Version der Richtlinien (WCAG 2.2)](https://www.w3.org/TR/WCAG22/) befindet sich derzeit in der Entwicklung, wird aber noch nicht berücksichtigt.

WCAG 2.1 umfasst eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Web-Inhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind. Es werden Ratschläge für Autoren, Designer und Entwickler von Web-Inhalten geboten, wie sichergestellt werden kann, dass die von ihnen produzierten Ressourcen für möglichst viele Menschen so barrierefrei wie möglich sind, und zwar unabhängig von ihrer Behinderung, z. B. Sehbehinderung, Hörverlust, Lernschwächen, altersbedingte Einschränkungen u. Ä.

Die Beschreibung eines Bildes (oder anderer Nicht-Text-Inhalte) mithilfe des `alt`-Attributs in HTML ist zum Beispiel für Blinde und Sehbehinderte von großem Nutzen. Die textliche Beschreibung im `alt`-Attribut kann entweder in eine Sprachausgabe umgewandelt oder an elektronisch aktualisierbare Braillezeilen übertragen werden.

Additionally, WCAG 2.1 can result in advantages for other beneficiaries, including people who may be considered *situationally disabled*. Also Personen, die aufgrund von Faktoren wie Browser-Technologie, Geschwindigkeit der Netzwerkverbindung oder Browser-Umgebung auf ähnliche Hindernisse stoßen können wie Menschen mit Behinderungen.

Mit Adobe Experience Manager können Inhaltsautoren und/oder Website-Betreiber Web-Inhalte erstellen, die den Erfolgskriterien der WCAG 2.1 Level A und Level AA entsprechen.

Daher ist das Verständnis der Ziele von WCAG 2.1 und der Struktur der Richtlinien ein wichtiger Teil des Verständnisses von Barrierefreiheit im Web und wie die Richtlinien bei der Erstellung barrierefreier Web-Inhalte helfen können.

Absicht von WCAG 2.1 ist es, Richtlinien mit folgenden Merkmalen bereitzustellen:

* **Technologieunabhängig:** Mit anderen Worten Richtlinien, die auf eine Reihe von Web-Inhaltsformaten und nicht nur auf HTML angewendet werden können. So kann WCAG 2.1 Inhalte abdecken, die in den Formaten PDF, Flash, JavaScript und anderen aktuellen und künftigen Web-Technologien generiert oder bereitgestellt werden.

* **Testfähig:** Jede Richtlinie ist so formuliert, dass sie objektiv getestet werden kann, um sicherzustellen, dass eine Gruppe von Fachleuten für Barrierefreiheit generell zustimmt, dass die Richtlinie eingehalten wird. Eine der Herausforderungen bei Richtlinien zur Barrierefreiheit besteht darin, dass einige zwar technisch prüfbar sind, andere jedoch menschliches Urteilsvermögen erfordern, um festzustellen, ob die Richtlinie erfolgreich umgesetzt wurde oder nicht.

* Support **prioritized and contextual implementation:**
WCAG 2.1 guidelines are given priorities, relating to the likely impact of not following a guideline on a particular group of users with disabilities. Dies ermöglicht es Autoren, eine fundierte Entscheidung zu den wichtigsten Richtlinien für ihre jeweilige Situation zu treffen. Außerdem wird das Konzept *Barrierefreiheit unterstützend* eingeführt. Dadurch können Autoren Entscheidungen dazu treffen, wie sie Webtechnologien am besten nutzen können, die möglicherweise nicht vollständig barrierefrei sind, oder ggf. Von Anwendern verlangen, dass sie über spezielle assistierenden Techniken und/oder Browser verfügen, um von Barrierefreiheitsfunktionen zu profitieren.

Diese Ziele haben die Struktur von WCAG 2.1 wesentlich beeinflusst.

>[!NOTE]
>
>Es ist nicht möglich, eine Website zu erstellen, die für alle denkbaren Behinderungen oder Personentypen geeignet ist. Zweck von WCAG 2.1 ist es, Web-Autoren bei der Erstellung von Websites zu unterstützen, die so umfassend wie möglich unter bestimmten Bedingungen und in vertretbarem Rahmen barrierefrei sind.

## Struktur {#structure}

WCAG 2.1 ist so strukturiert, dass Konzepte der barrierefreien Erstellung von Web-Inhalten schrittweise und detailliert umgesetzt werden. Dies mag den Eindruck erwecken, dass es sich bei WCAG 2.1 um eine sehr komplexe Zusammenstellung miteinander verknüpfter Dokumente handelt. Doch das eigentliche Ziel ist es, (nach und nach) detailliertere Informationen zur Verfügung zu stellen, wenn die Autoren sie benötigen, anstatt sie alle in einem sehr großen Dokument bereitzustellen.

WCAG 2.1 besteht aus vier Grundprinzipien für barrierefreies Design, die manchmal mit dem Akronym **POUR** bezeichnet werden. Diese sind:

1. **Wahrnehmbar**: Kann ein Anwender den betreffenden Webinhalt nachvollziehen?
1. **Bedienbar**: Kann ein Anwender navigieren, Daten eingeben oder anderweitig mit den Webinhalten interagieren?
1. **Verständlich**: Kann ein Anwender die ihm präsentierten Webinhalte verarbeiten und verstehen?
1. **Robust**: Sind die Webinhalte in der beabsichtigten Weise in einer entsprechend breiten Palette von Browserumgebungen verfügbar, einschließlich älterer und neuer Browserumgebungen?

Zur Erklärung:
* Zu jedem **Prinzip** gehören eine oder mehrere **Richtlinien**.

* Richtlinien sind als Anweisungen formuliert, die entweder positiv oder negativ sind.
* Die Richtlinien sind von 1.1 bis 4.1 nummeriert, wobei die erste Zahl dem übergeordneten Prinzip entspricht.
* Jede Richtlinie besteht aus einem oder mehreren **Erfolgskriterien**.
* Erfolgskriterien werden als Aussagen geschrieben, die für eine bestimmte Web-Seite entweder `True` oder `False` sind.
* Erfolgskriterien können Entweder/Oder-Entscheidungen oder Ausnahmen vorsehen, d. h. Situationen, in denen die Erfolgskriterien nicht erfüllt sein müssen.
* Erfolgskriterien sind gemäß der übergeordneten Richtlinie und dem Prinzip von 1.1.1 bis 4.1.1 nummeriert. Sie haben auch einen Kurznamen, der zur besseren Orientierung die Absicht des Kriteriums zusammenfasst. For example, success criterion [1.1.1 is Non-text Content](https://www.w3.org/TR/WCAG/#non-text-content).
* Zu den Erfolgskriterien gehört eine Liste zugehöriger **Techniken** (siehe unten).

## Unterstützende Ressourcen {#supporting-resources}

Zusätzlich zu den WCAG 2.1-Hauptkomponenten (Prinzipien, Richtlinien und Erfolgskriterien) gibt es eine Reihe unterstützender Dokumente. Einige davon bieten spezifische Ratschläge dazu, wie Aspekte der Richtlinien erfüllt werden können. Andere sind allgemeinere Hinweise, die Web-Autoren, -Designern und -Entwicklern aller Fachrichtungen helfen, WCAG 2.1 so effektiv wie möglich zu verstehen und zu nutzen.

WCAG 2.1 selbst ist ein stabiles Dokument und wird sich nicht ändern, aber die meisten dieser Hilfsmittel sind dynamische Dokumente. Sie werden sich mit der Zeit verändern und wachsen, wenn neue Technologien entstehen, und es werden neue Beispiele dafür gefunden, wie die Zugänglichkeit von Websites erreicht werden kann.

### WCAG 2.1-Ressourcen {#wcag-resources}

Diese Liste erhebt keinen Anspruch auf Vollständigkeit, sondern bietet eine Einführung in die verfügbaren Ressourcen:
* [Eine Übersicht über alle zu WCAG gehörigen Dokumente](https://www.w3.org/WAI/standards-guidelines/wcag/)
* [Eine Zusammenfassung der verschiedenen Dokumente](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)
* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/)
* [Neu in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/)
* [Kurzanleitung zum Erfüllen von WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [Häufig gestellte Fragen zu WCAG 2](https://www.w3.org/WAI/standards-guidelines/wcag/faq/)


### Neue Funktionen in WCAG 2.1 {#what-is-new}

Die Leitlinien enthalten Informationen zu den neuen Funktionen in WCAG 2.1:

* [Was ist neu in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/) bietet wertvolle Informationen über das Delta zwischen WCAG 2.0 und WCAG 2.1.

* In den Abschnitten [WCAG 2.0 und 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/#versions) wird der Status ihrer Beziehungen näher erläutert.

### Techniken für WCAG 2.1 {#techniques-for-wcag}

Techniken für WCAG 2.1 sind auf der englischsprachigen Seite [Techniques for WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/) verfügbar.

**Techniken** bilden in der WCAG 2.1-Hierarchie die Ebene unterhalb der Erfolgskriterien. Sie werden von der WAI als informativ, nicht als normativ eingestuft. Das heißt, dass eine bestimmte Technik nicht befolgt werden muss, damit eine Ressource WCAG 2.1 entspricht.

Da Techniken weitaus spezifischer als Erfolgskriterien sind, beziehen sie sich in der Regel auf eine bestimmte Technologie oder einen bestimmten Inhaltstyp (z. B. HTML oder Video) oder eine bestimmte Anwendung (z. B. für E-Commerce oder E-Learning). Sie können sich Techniken als bewährte Beispiele dafür vorstellen, wie spezifische Richtlinien und Erfolgskriterien erfüllt werden können, sodass sie für Autoren und Entwickler, die in bestimmten Kontexten arbeiten, hilfreich sind.

So kann auf Techniken zugegriffen werden:

* Nach Sammlung (Techniken können allgemein sein oder sich auf eine bestimmte Technologie oder ein bestimmtes Format beziehen – wie HTML, Cascading Style Sheets oder Client-seitiges Scripting) oder
* Anhand zugehöriger Erfolgskriterien. Techniken können für mehr als ein Erfolgskriterium gelten.

Jede Technik hat eine eindeutige Zahl, die auf ihre Sammlung verweist. For example, one of the ARIA techniques is [Technique ARIA2: Identifying a required field with the aria-required property](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA2.html).

Techniken können „ausreichend“, „empfohlen“ oder ein Fehler sein:

* Eine *ausreichende Technik* ist eine, die bei Befolgung ausreicht, um ein bestimmtes Erfolgskriterium zu erfüllen.
* Eine *empfohlene Technik* hat bei Befolgung einen positiven Einfluss auf die Barrierefreiheit, ist aber möglicherweise allein nicht ausreichend, um sicherzustellen, dass ein bestimmtes Erfolgskriterium erfüllt wird.
* Ein *Fehler* ist eine Technik, die ein konkretes Beispiel dafür beschreibt, wann ein Erfolgskriterium nicht erfüllt ist.

Zu den Details der Techniken gehören eine Beschreibung, Anwendbarkeit, Beispiele, Ressourcen mit weiteren Informationen und Angaben, wie Autoren die Anwendung der Technik erfolgreich testen können.

Die Liste der Techniken ist nicht vollständig. Die WAI aktualisiert die Liste ständig mit neuen Beispielen, die Entwicklungen in den Bereichen Webtechnologie, Designkonzepte und Forschungsergebnisse widerspiegeln. Es lohnt sich daher, die Liste der Techniken regelmäßig auf neue Einträge zu überprüfen.

### Grundlegendes zu WCAG 2.1 {#understanding-wcag}

Hier finden sich verschiedene Dokumente, die Lesern helfen, den Zweck bestimmter Richtlinien und Erfolgskriterien zu verstehen. Sie können eine [Einführung und Links zu weiterführenden Informationen herunterladen](https://www.w3.org/WAI/WCAG21/Understanding/).

Zu allen einzelnen Richtlinien und Erfolgskriterien gibt es auch eine eigene Seite des Typs „Grundlagen“, auf der Sie sich über Folgendes informieren können:

* Den Zweck der Richtlinie
* Spezifische Erfolgskriterien
* Empfohlene Techniken, die helfen, die Anforderungen der Richtlinie zu erfüllen, aber nicht unter ein bestimmtes Erfolgskriterium fallen.

Zu allen Erfolgskriterien gibt es auch eine eigene Seite des Typs „Grundlagen“ mit Informationen zu folgenden Themen:

* Zweck des Erfolgskriteriums
* Gängige Beispiele, wie das Erfolgskriterium erfüllt werden kann
* Verwandte (nicht W3C-) Ressourcen mit Informationen, wie das Erfolgskriterium erfüllt wird
* Techniken und Fehler: Konkrete und detaillierte Beispiele, wie das Erfolgskriterium erfüllt werden kann (im Folgenden näher beschrieben)
* Schlüsselbegriffe: Ein Glossar von Begriffen, die für das Verständnis des Erfolgskriteriums wichtig sind.

Ein Beispiel finden Sie unter: [Erfolgskriterium 1.1.1 verstehen (Nichttextlicher Inhalt)](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content).

### Erfüllen von WCAG 2.1 {#how-to-meet-wcag}

Der Abschnitt „Erfüllen von“ befindet sich auf der Seite [Erfüllen von WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/). Dieser Abschnitt bietet eine alternative Präsentation der WCAG, die es Lesern ermöglicht, den Inhalt der Richtlinien auf diejenigen zu verfeinern, die für ihre eigenen Interessen und/oder Umstände am relevantesten sind. Leser können die Erfolgskriterien filtern, die sie einsehen möchten, indem sie bestimmte Webinhaltstechnologien wie Cascading Style Sheets oder Skripts oder bestimmte Prioritätsstufen angeben.

Ohne Filterung liefert diese Ressource alle Erfolgskriterien, nach Richtlinien gruppiert. Für jedes Erfolgskriterium wird Folgendes angegeben:

* Text des Erfolgskriteriums
* Link zum entsprechenden Dokument des Typs „Grundlagen“
* Liste zugehöriger „ausreichender“ Techniken mit Links zu Details jeder Technik
* Liste zugehöriger „empfohlener“ Techniken mit Links zu Details jeder Technik (sofern vorhanden)
* Liste zugehöriger Fehler mit Links zu Details zu jedem Fehler
