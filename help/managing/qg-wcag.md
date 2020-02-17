---
title: Kurzanleitung zu WCAG 2.0
seo-title: Kurzanleitung zu WCAG 2.0
description: Hier finden Sie einen kurzen Überblick über die WCAG 2.0-Richtlinien zur Barrierefreiheit.
seo-description: Hier finden Sie einen kurzen Überblick über die WCAG 2.0-Richtlinien zur Barrierefreiheit.
uuid: a5cf463e-89e9-4cc0-9c91-69a1fd3d8ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing-accessibility
content-type: reference
discoiquuid: 3cac0e34-7514-48ce-a93b-592bbdbcd252
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Kurzanleitung zu WCAG 2.0{#quick-guide-to-wcag}

AEM wurde mit Blick auf eine maximale Umsetzung der Content Accessibility Guidelines entwickelt:

Die [Web Content Accessibility Guidelines, Version 2.0 (WCAG2)](https://www.w3.org/TR/WCAG/) sind eine vom [World Wide Web Consortium (W3C)](https://www.w3.org/) im Rahmen seiner [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/) entwickelte Zusammenstellung international anerkannter Richtlinien.

WCAG 2.0 umfasst eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Webinhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind. Es werden Ratschläge für Autoren, Designer und Entwickler von Webinhalten geboten, wie sichergestellt werden kann, dass die von ihnen produzierten Ressourcen für möglichst viele Menschen so barrierefrei wie möglich sind, und zwar unabhängig von ihrer Behinderung, z. B. Sehbehinderung, Hörverlust, Lernschwächen, altersbedingte Einschränkungen u. Ä.

Die Beschreibung eines Bilds (oder anderer Nicht-Text-Inhalte) mithilfe des `alt`-Attributs in HTML ist zum Beispiel für Blinde und Sehbehinderte von großem Nutzen. Die textliche Beschreibung im `alt`-Attribut kann entweder in eine Sprachausgabe umgewandelt oder an elektronisch aktualisierbare Braillezeilen übertragen werden.

Darüber hinaus kann WCAG 2.0 Vorteile für andere Bedürftige bringen, so z. B. für Personen, die ggf. als *situationsabhängig* behindert gelten. Also Personen, die aufgrund von Faktoren wie Browsertechnologie, Geschwindigkeit der Netzwerkverbindung oder Browserumgebung auf ähnliche Hindernisse stoßen können wie Menschen mit Behinderungen.

Mit Adobe Experience Manager können Inhaltsautoren und/oder Websitebetreiber Webinhalte erstellen, die den Erfolgskriterien der WCAG 2.0 Level A und Level AA entsprechen.

Daher ist das Verständnis der Ziele von WCAG 2.0 und der Struktur der Richtlinien ein wichtiger Teil des Verständnisses von Barrierefreiheit im Web und wie die Richtlinien bei der Erstellung barrierefreier Webinhalte helfen können.

Absicht von WCAG 2.0 ist es, Richtlinien mit folgenden Merkmalen bereitzustellen:

* Sind **technologieunabhängig:**

   Mit anderen Worten, Richtlinien, die auf eine Reihe von Webinhalt-Formaten angewendet werden können, nicht nur HTML. So kann WCAG 2.0 Inhalte abdecken, die in den Formaten PDF, Flash, JavaScript und anderen aktuellen und künftigen Webtechnologien generiert oder bereitgestellt werden. Damit soll eine erkannte Schwäche von WCAG 1.0 behoben werden, denn hier lag der Fokus auf HTML auf Kosten anderer Webinhaltsformate.

* Sind **testbar:**

   Jede Leitlinie wird so geschrieben, dass sie objektiv getestet werden kann, um sicherzustellen, dass eine Gruppe von Zugänglichkeitsexperten generell zustimmt, dass die Leitlinie eingehalten wurde. Eine der Herausforderungen bei Richtlinien zur Barrierefreiheit besteht darin, dass einige zwar technisch prüfbar sind, andere jedoch menschliches Urteilsvermögen erfordern, um festzustellen, ob die Richtlinie erfolgreich umgesetzt wurde oder nicht. WCAG 2.0 wurde mit dem Ziel verfasst, die Subjektivität zu reduzieren, die in einigen der WCAG 1.0-Richtlinien und -Kontrollpunkte vorhanden war.

* Unterstützung **priorisierter und kontextbezogener Implementierung:**

   Wie bei WCAG 1.0 werden die WCAG 2.0-Richtlinien in Bezug auf die voraussichtlichen Auswirkungen, die sich aus der Nichtbefolgung einer Leitlinie auf eine bestimmte Gruppe von Benutzern mit Behinderungen ergeben, vorrangig behandelt. Dies ermöglicht es Autoren, eine fundierte Entscheidung zu den wichtigsten Richtlinien für ihre jeweilige Situation zu treffen. Außerdem wird das Konzept *Barrierefreiheit unterstützend* eingeführt. Dadurch können Autoren Entscheidungen dazu treffen, wie sie Webtechnologien am besten nutzen können, die möglicherweise nicht vollständig barrierefrei sind, oder ggf. Von Anwendern verlangen, dass sie über spezielle assistierenden Techniken und/oder Browser verfügen, um von Barrierefreiheitsfunktionen zu profitieren.

Diese Ziele haben die Struktur von WCAG 2.0 wesentlich beeinflusst.

>[!NOTE]
>
>Es ist nicht möglich, eine Website zu erstellen, die für alle denkbaren Behinderungen oder Personentypen geeignet ist. Zweck von WCAG 2.0 ist es, Webautoren bei der Erstellung von Websites zu unterstützen, die so umfassend wie möglich unter bestimmten Bedingungen und in vertretbarem Rahmen barrierefrei sind.

>[!NOTE]
>
>Wenn Sie mit WCAG 1.0 vertraut sind, werden Sie einige Änderungen in WCAG 2.0 feststellen, die sich auf Umfang, Organisation und Zielsetzung beziehen.

## Struktur {#structure}

WCAG 2.0 ist so strukturiert, dass Konzepte der barrierefreien Erstellung von Webinhalten schrittweise und detailliert umgesetzt werden. Dies mag den Eindruck erwecken, dass es sich bei WCAG 2.0 um eine sehr komplexe Zusammenstellung miteinander verknüpfter Dokumente handelt. Doch das eigentliche Ziel ist es, (nach und nach) detailliertere Informationen zur Verfügung zu stellen, wenn die Autoren sie benötigen, anstatt sie alle in einem sehr großen Dokument bereitzustellen.

WCAG 2.0 besteht aus vier Grundprinzipien für barrierefreies Design.Diese sind:

1. **Wahrnehmbar**: Kann ein Anwender den betreffenden Webinhalt nachvollziehen?
1. **Bedienbar**: Kann ein Anwender navigieren, Daten eingeben oder anderweitig mit den Webinhalten interagieren?
1. **Verständlich**: Kann ein Anwender die ihm präsentierten Webinhalte verarbeiten und verstehen?
1. **Robust**: Sind die Webinhalte in der beabsichtigten Weise in einer entsprechend breiten Palette von Browserumgebungen verfügbar, einschließlich älterer und neuer Browserumgebungen?

Diese Prinzipien werden im Englischen gelegentlich mit dem Akronym POUR bezeichnet.

* Zu jedem **Prinzip** gehören eine oder mehrere **Richtlinien**.

   * Richtlinien sind als Anweisungen formuliert, die entweder positiv oder negativ sind.
   * Die Richtlinien sind von 1.1 bis 4.1 nummeriert, wobei die erste Zahl dem übergeordneten Prinzip entspricht.

* Jede Richtlinie besteht aus einem oder mehreren **Erfolgskriterien**.

   * Success criteria are written as statements, which are either `True` or `False` for any given web page.
   * Erfolgskriterien können Entweder/Oder-Entscheidungen oder Ausnahmen vorsehen, d. h. Situationen, in denen die Erfolgskriterien nicht erfüllt sein müssen.
   * Erfolgskriterien sind gemäß der übergeordneten Richtlinie und dem Prinzip von 1.1.1 bis 4.1.1 nummeriert. Sie haben auch einen Kurznamen, der zur besseren Orientierung die Absicht des Kriteriums zusammenfasst. Beispielsweise heißt das Erfolgskriterium 1.1.1 „Textalternativen“.
   * Success criteria include a list of related **techniques** (described in more detail below).

## Unterstützende Ressourcen {#supporting-resources}

Zusätzlich zu den WCAG 2.0-Hauptkomponenten (Prinzipien, Richtlinien und Erfolgskriterien) gibt es eine Reihe unterstützender Dokumente. Einige davon bieten spezifische Ratschläge dazu, wie Aspekte der Richtlinien erfüllt werden können. Andere sind allgemeinere Hinweise, die Webautoren, -designern und -entwicklern aller Fachrichtungen helfen, WCAG 2.0 so effektiv wie möglich zu verstehen und zu nutzen.

Während WCAG 2.0 ein statisches Dokument ist und sich nicht ändern wird, sind die meisten dieser unterstützenden Ressourcen dynamisch. Sie werden sich im Laufe der Zeit ändern und umfassender werden, sobald neue Technologien auftauchen und neue Beispiele dafür gefunden werden, wie Barrierefreiheit im Internet erreicht werden kann.

### WCAG 2.0-Ressourcen {#wcag-resources}

* [Eine Übersicht über alle zu WCAG 2.0 gehörigen Dokumente](https://www.w3.org/WAI/intro/wcag.php)
* [Erläuterung der Zusammenhänge zwischen den einzelnen Komponenten](https://www.w3.org/WAI/intro/wcag20)
* [Häufig gestellte Fragen zu WCAG 2.0](https://www.w3.org/WAI/WCAG20/wcag2faq.html)

### Techniken für WCAG 2.0 {#techniques-for-wcag}

Techniken für WCAG 2.0 sind auf der englischsprachigen Seite [Techniques for WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/) verfügbar.

**Techniken** bilden in der WCAG 2.0-Hierarchie die Ebene unterhalb der Erfolgskriterien. Sie werden von der WAI als informativ, nicht als normativ eingestuft. Das heißt, dass eine bestimmte Technik nicht befolgt werden muss, damit eine Ressource WCAG 2.0 entspricht.

Da Techniken weitaus spezifischer als Erfolgskriterien sind, beziehen sie sich in der Regel auf eine bestimmte Technologie oder einen bestimmten Inhaltstyp (z. B. HTML oder Video) oder eine bestimmte Anwendung (z. B. für E-Commerce oder E-Learning). Sie können sich Techniken als bewährte Beispiele dafür vorstellen, wie spezifische Richtlinien und Erfolgskriterien erfüllt werden können, sodass sie für Autoren und Entwickler, die in bestimmten Kontexten arbeiten, hilfreich sind.

So kann auf Techniken zugegriffen werden:

* Durch Erfassung (Techniken können allgemein sein oder sich auf eine bestimmte Technologie oder ein bestimmtes Format beziehen - wie HTML, CSS oder clientseitige Skripterstellung) oder
* Anhand zugehöriger Erfolgskriterien. Techniken können für mehr als ein Erfolgskriterium gelten.

Jede Technik hat eine eindeutige Zahl, die auf ihre Sammlung verweist. Eine der ARIA-Techniken ist beispielsweise die *Technik ARIA2: Identifizieren von Pflichtfeldern mit der Eigenschaft „required“*.

Techniken können „ausreichend“, „empfohlen“ oder ein Fehler sein:

* Eine *ausreichende Technik* ist eine, die bei Befolgung ausreicht, um ein bestimmtes Erfolgskriterium zu erfüllen.
* Eine *empfohlene Technik* hat bei Befolgung einen positiven Einfluss auf die Barrierefreiheit, ist aber möglicherweise allein nicht ausreichend, um sicherzustellen, dass ein bestimmtes Erfolgskriterium erfüllt wird.
* Ein *Fehler* ist eine Technik, die ein konkretes Beispiel dafür beschreibt, wann ein Erfolgskriterium nicht erfüllt ist.

Zu den Details der Techniken gehören eine Beschreibung, Anwendbarkeit, Beispiele, Ressourcen mit weiteren Informationen und Angaben, wie Autoren die Anwendung der Technik erfolgreich testen können.

Die Liste der Techniken ist nicht vollständig. Die WAI aktualisiert die Liste ständig mit neuen Beispielen, die Entwicklungen in den Bereichen Webtechnologie, Designkonzepte und Forschungsergebnisse widerspiegeln. Es lohnt sich daher, die Liste der Techniken regelmäßig auf neue Einträge zu überprüfen.

### Grundlegendes zu WCAG 2.0 {#understanding-wcag}

Hier finden sich verschiedene Dokumente, die Lesern helfen, den Zweck bestimmter Richtlinien und Erfolgskriterien zu verstehen. Sie können eine [Einführung und Links zu weiterführenden Informationen herunterladen](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/Overview.html).

Zu allen einzelnen Richtlinien und Erfolgskriterien gibt es auch eine eigene Seite des Typs „Grundlagen“, auf der Sie sich über Folgendes informieren können:

* Den Zweck der Richtlinie
* Spezifische Erfolgskriterien
* Empfohlene Techniken, die helfen, die Anforderungen der Richtlinie zu erfüllen, aber nicht unter ein bestimmtes Erfolgskriterium fallen.

Zu allen Erfolgskriterien gibt es auch eine eigene Seite des Typs „Grundlagen“ mit Informationen zu folgenden Themen:

* Zweck des Erfolgskriteriums
* Gängige Beispiele, wie das Erfolgskriterium erfüllt werden kann
* Verwandte (nicht W3C-) Ressourcen mit Informationen, wie das Erfolgskriterium erfüllt wird
* Techniken und Fehler: spezifische und detaillierte Beispiele, wie das Erfolgskriterium erfüllt werden kann (weiter unten beschrieben)
* Schlüsselbegriffe - ein Glossar von Begriffen, die für das Verständnis des Erfolgskriteriums wichtig sind.

Ein Beispiel finden Sie unter: [Non-text Content – Understanding SC 1.1.1](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/text-equiv-all.html).

### Erfüllen von WCAG 2.0 {#how-to-meet-wcag}

Der Abschnitt „How to Meet“ befindet sich auf der Seite [How To Meet WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/). Dieser Abschnitt bietet eine alternative Darstellung der WCAG, die es erlaubt, den Inhalt der Richtlinien auf die für die eigenen Interessen oder Gegebenheiten des Lesers relevantesten zu präzisieren. Leser können die Erfolgskriterien filtern, die sie einsehen möchten, indem sie bestimmte Webinhaltstechnologien wie Cascading Style Sheets oder Skripts oder bestimmte Prioritätsstufen angeben.

Ohne Filterung liefert diese Ressource alle Erfolgskriterien, nach Richtlinien gruppiert. Für jedes Erfolgskriterium wird Folgendes angegeben:

* Text des Erfolgskriteriums
* Link zum entsprechenden Dokument des Typs „Grundlagen“
* Liste zugehöriger „ausreichender“ Techniken mit Links zu Details jeder Technik
* Liste zugehöriger „empfohlener“ Techniken mit Links zu Details jeder Technik (sofern vorhanden)
* Liste zugehöriger Fehler mit Links zu Details zu jedem Fehler