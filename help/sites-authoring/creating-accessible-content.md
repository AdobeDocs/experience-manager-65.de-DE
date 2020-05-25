---
title: Barrierefreie Inhalte für Adobe Experience Manager erstellen (WCAG 2.1-Konformität)
description: Verwenden Sie AEM, um Menschen mit Behinderungen den Zugang zu Webinhalten und deren Nutzung zu erleichtern.
translation-type: tm+mt
source-git-commit: cb7df7301364eb1ce3a1ca376256d2cd5afcb2c8
workflow-type: tm+mt
source-wordcount: '13956'
ht-degree: 49%

---


# Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.1-Richtlinien) {#creating-accessible-content-wcag-conformance}

Die [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/), die von [einer Arbeitsgruppe des World Wide Wec Consortiums](https://www.w3.org/Konsortium/Aktivitäten#Accessibility_Guidelines_Working_Group)erarbeitet wurden, bestehen aus einer Reihe von technologieunabhängigen Leitlinien und Erfolgskriterien, die helfen, Web-Inhalte für Menschen mit Behinderungen zugänglich und nutzbar zu machen.

Als Einführung bietet das Konsortium eine Reihe von Abschnitten und unterstützende Dokumente an:

* [Neue Funktionen in WCAG 2.1](https://www.w3.org/TR/WCAG/#new-features-in-wcag-2-1)
* [Erfüllen von WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [Grundlegendes zu WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/)
* [Techniken für WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/)
* [Die WCAG-Dokumente](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)

Siehe auch:
* Our [Quick Guide to WCAG 2.1](/help/managing/qg-wcag.md).
* Die Berichte zur [Barrierefreiheitskonformität für Adobe-Lösungen](https://www.adobe.com/accessibility/compliance.html).
* [Konfigurieren des Rich-Text-Editors zum Erstellen barrierefreier Inhalte](/help/sites-administering/rte-accessible-content.md)

Die Leitlinien werden nach drei Konformitätsstufen eingestuft: Stufe A (niedrigste), Stufe AA und Kategorie AAA (höchste). Die Levels sind kurz definiert wie folgt:

* **Stufe A:** Ihre Site erreicht eine einfache, minimale Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-Erfolgskriterien erfüllt.
* **Stufe AA:** Dies ist ein idealer Grad an Barrierefreiheit, nach dem Sie streben können, in dem Ihre Site ein grundlegendes Niveau der Barrierefreiheit erreicht, sodass sie für die meisten Menschen in den meisten Situationen mit den meisten Technologien zugänglich ist. Bei Erreichen dieser Stufe sind alle Kategorie-A- und -AA-Erfolgskriterien erfüllt.
* **Stufe AAA:** Ihre Site erreicht eine sehr hohe Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-, -AA- und -AAA-Erfolgskriterien erfüllt.

Bei der Erstellung der Site sollten Sie festlegen, welchen Level Ihre Site insgesamt erfüllen soll.

The following section presents [layers of the WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) with related success criteria for Level A and Level AA [conformance levels](https://www.w3.org/TR/WCAG/#conformance-to-wcag-2-1).

>[!NOTE]
>
>In diesem Dokument verwenden wir Folgendes:
>
>* The [short names for the WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance).
>* The [numbering used in the WCAG 2.1 Guidelines](https://www.w3.org/TR/WCAG/#numbering-in-wcag-2-1) to aid cross-referencing with the WCAG website.


## Grundsatz 1: Erkennbar     {#principle-perceivable}

[Grundsatz 1: Erkennbar – Informationen und Komponenten der Benutzeroberfläche müssen für die Benutzer so dargestellt sein, dass sie sie erkennen können.](https://www.w3.org/TR/WCAG/#perceivable)

### Textalternativen (1.1)     {#text-alternatives}

[Richtlinie 1.1 Textalternativen: Bieten Sie Textalternativen für nichttextliche Inhalte, damit sie in andere Formate geändert werden, die von bestimmten Personen benötigt werden, wie zum Beispiel Großdruck, Braille, Sprache, Symbole oder einfachere Sprache.](https://www.w3.org/TR/WCAG/#text-alternatives)

### Nichttextlicher Inhalt (1.1.1)     {#non-text-content}

* Erfolgskriterium 1.1.1
* Level A
* Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzern präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen.

#### Zweck: Nichttextlicher Inhalt (1.1.1) {#purpose-non-text-content}

Informationen auf einer Webseite können in vielen verschiedenen nichttextlichen Formaten dargestellt werden, wie zum Beispiel als Bilder, Videos, Animationen und Diagramme. Menschen, die blind sind oder deren Sicht erheblich eingeschränkt ist, können nichttextliche Inhalte nicht sehen, doch sie können Textinhalte erfassen, wenn sie ihnen von einem Bildschirmleser vorgelesen oder in haptischer Form auf einem Braille-Anzeigegerät präsentiert werden. Somit kann es durch Bereitstellung von Textalternativen zu Inhalten in grafischem Format ermöglicht werden, dass Menschen, die die grafischen Inhalte nicht sehen können, auf eine gleichwertige Version der Informationen des Inhalts zugreifen können.

Ein nützlicher weiterer Vorteil besteht darin, dass es durch Textalternativen möglich ist, nichttextliche Inhalte durch die Suchmaschinentechnologie zu indizieren.

#### Erfüllen: Nichttextlicher Inhalt (1.1.1)     {#how-to-meet-non-text-content}

Bei statischen Grafiken besteht die Grundanforderung darin, eine gleichwertige Textalternative für die Grafik bereitzustellen. Dies kann im Feld **Alternativer Text** erfolgen. siehe zum Beispiel das **[Bild](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/image.html)**der Hauptkomponente.

>[!NOTE]
>
>Einige vordefinierte Kernkomponenten, wie **[Karussell](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/components/carousel.html)**, bieten kein Feld für den**Alternativtext **zum Hinzufügen von alternativen Textbeschreibungen zu einzelnen Bildern, obwohl das Feld &quot;**Beschriftung **&quot;(Registerkarte &quot;**[Ein-/Ausgabehilfe](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/carousel.html#accessibility-tab)** &quot;) für die gesamte Komponente vorhanden ist.
>
>When implementing versions of these for your AEM instance, your development team will need to configure such components to support the `alt` attribute so that authors can add it to the content (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

In AEM muss das Feld **Alternativtext** standardmäßig ausgefüllt werden. If the image is purely decorative and alternative text would be unnecessary, the **Image is decorative** option can be checked.

#### Erstellen guter Textalternativen {#creating-good-text-alternatives}

Es gibt verschiedene Arten von nichttextlichem Inhalt. Daher hängt der Wert der Textalternative von der Rolle ab, die die Grafik auf der Webseite spielt. Nachfolgend sehen Sie einige Faustregeln:

* Textalternativen sollten kurz und bündig sein, aber dennoch klar die wesentlichen Informationen erfassen, die der nichttextliche Inhalt vermittelt.
* Übermäßig lange Beschreibungen (mit mehr als 100 Zeichen) sollten vermieden werden. Wenn für eine Textalternative mehr Details erforderlich sind:
   * Geben Sie im Alternativtext eine kurze Beschreibung an
   * und fügen Sie irgendwo anders auf der entsprechenden Seite oder auf einer anderen Webseite eine längere Beschreibung ein. Verlinken Sie auf diese separate Beschreibung, indem Sie das Bild mit einem Link unterlegen oder indem Sie neben das Bild einen Textlink platzieren.
* Alternativtext sollte keinen Inhalt replizieren, der bereits in Textform auf derselben Seite vorhanden ist. Denken Sie daran, dass viele Bilder Darstellungen von Punkten sind, die bereits der Text einer Seite abdeckt. Somit ist möglicherweise bereits eine Textalternative vorhanden.
* Wenn es sich bei dem nichttextlichen Inhalt um einen Link zu einer anderen Seite oder einem anderen Dokument handelt und kein anderer Text vorhanden ist, der Teil desselben Links ist, dann muss der Alternativtext für das Bild das Ziel des Links angeben und braucht das Bild nicht zu beschreiben.
* Wenn sich der nichttextliche Inhalt in einem Schaltflächenelement befindet und kein Text vorhanden ist, der Teil derselben Schaltfläche ist, dann muss der Alternativtext des Bildes die Funktion der Schaltfläche angeben statt das Bild zu beschreiben.
* Es ist durchaus akzeptabel, dass einem Bild ein leerer alternativer Text (null) zugewiesen wird, jedoch nur, wenn das Bild keinen alternativen Text benötigt (z. B. eine rein dekorative Grafik) oder wenn der entsprechende Text bereits im Seitentext vorhanden ist.

<!--
The [W3C draft: HTML5 Techniques for providing useful text alternatives](https://dev.w3.org/html5/alt-techniques/) has more details and examples of appropriate alternative text provision for images of different types.
-->

Bestimmte Arten von nichttextlichem Inhalt, für den Textalternativen erforderlich sind:

* Veranschaulichende Fotos:
Hierbei handelt es sich um Bilder von Menschen, Objekten oder Orten. Es ist wichtig, über die Rolle des Fotos auf der Seite nachzudenken und generell die Beschreibung des Bildinhalts zu empfehlen, da Hilfstechnologie den Elementtyp ankündigt (z. B. `graphic` oder `image`); Es kann mehr Klarheit in der Verwendung `screenshot` oder `illustration` in den alternativen Textbeschreibungen, aber dies hängt vom Kontext. Konsistenz ist ein wichtiger Faktor, eine Entscheidung sollte für ein gesamtes Autorenteam getroffen werden, und dies gilt für die gesamte Benutzererfahrung.
* Symbole: Hierbei handelt es sich um kleine Piktogramme (Grafiken), die bestimmte Informationen vermitteln. Sie müssen durchgängig auf einer Seite und Site verwendet werden. Alle Instanzen des Symbols auf einer Seite oder Site sollten dieselbe kurze und knappe Textalternative aufweisen, es sei denn, dass dadurch eine unnötige Verdoppelung von bereits vorhandenem Text erzeugt würde.
* Diagramme: Normalerweise werden dadurch numerische Daten dargestellt. So könnte als eine Möglichkeit zur Bereitstellung von Alternativtext eine kurze Zusammenfassung der im Diagramm gezeigten Haupt-Trends eingefügt werden. Fall nötig, können Sie eine detailliertere Textbeschreibung im Feld **Beschreibung** auf der Registerkarte **Erweiterte Bildeigenschaften** einfügen. Außerdem könnten Sie die Quelldaten an anderer Stelle auf der Seite oder Site als Tabelle zur Verfügung stellen.
* Karten, Diagramme, Flussdiagramme: Stellen Sie bei Grafiken, die räumliche Daten bereitstellen (um z. B. das Beschreiben von Beziehungen zwischen Objekten oder einem Prozess zu unterstützen) sicher, dass die Schlüsselmeldung im Textformat bereitgestellt wird und dass diese Textinformationen in der Nähe jedes verknüpften Datenpunkts positioniert werden. Bei Maps ist die Bereitstellung eines Volltextäquivalents wahrscheinlich nicht praktikabel, aber wenn die Map bereitgestellt wird, um den Weg zu einer bestimmten Position zu erleichtern, kann der Alternativtext des Map Image kurz die *Zuordnung von X* angeben und dann Anweisungen für diese Position im Text an einer anderen Stelle auf der Seite oder über das Feld **Beschreibung** auf der Registerkarte **Erweitert** der Komponente **Bild** geben.
* CAPTCHAs: Ein CAPTCHA ist ein *vollautomatischer öffentlicher Turing-Test zur Unterscheidung zwischen Computern und Menschen*. Es handelt sich um eine Sicherheitsprüfung auf Web-Seiten, um Menschen von schädlicher Software zu unterscheiden, die allerdings die Barrierefreiheit einschränken kann. Sie besteht aus Bildern, bei denen Benutzer beschreiben sollen, was sie sehen, um den Sicherheitstest zu bestehen. Die Bereitstellung einer Textalternative für das Bild ist offensichtlich nicht möglich; daher müssen Sie alternative nichtgrafische Lösungen in Betracht ziehen. Das W3C bietet eine Reihe von Vorschlägen wie. Diese Ansätze haben jedoch sowohl Vor- als auch Nachteile.
   * Logik-Puzzles
   * Audio statt Bilder
   * Eingeschränkte Benutzerkonten und Spam-Filter
* Hintergrundbilder: Diese werden anhand von Cascading Style Sheets (CSS) statt HTML erstellt. Dies bedeutet, dass es nicht möglich ist, einen Wert für Alternativtext anzugeben. Daher sollten Hintergrundbilder keine wichtigen textlichen Informationen enthalten. Falls sie es doch tun, müssen diese Informationen auch im Text der Seite vorhanden sein. Es ist jedoch wichtig, dass ein alternativer Hintergrund angezeigt wird, wenn das Bild nicht angezeigt werden kann.

>[!NOTE]
>
>Es sollte ein Mindestmaß an Kontrast zwischen dem Hintergrund- und dem Vordergrundtext vorhanden sein; weitere Details hierzu finden Sie unter [Kontrast (Minimum) (1.4.3)](#contrast-minimum).

#### Weitere Informationen: Nichttextlicher Inhalt (1.1.1)     {#more-information-non-text-content}

* [Erfolgskriterien 1.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html)
* [Erfolgskriterien 1.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#non-text-content)
* [W3C-Erklärung und Alternativen zu CAPTCHAs](https://www.w3.org/TR/turingtest/)

<!--
* [W3C: HTML5 Techniques for providing useful text alternatives (draft)](https://dev.w3.org/html5/alt-techniques/)
-->

### Zeitbasierte Medien (1.2)     {#time-based-media}

[Richtlinie 1.2 Zeitbasierte Medien: Bereitstellung von Alternativen für zeitbasierte Medien.](https://www.w3.org/TR/WCAG/#time-based-media)

This deals with web content that is *time-based*. This covers content that the user can play (such as video, audio, and animated content) and may be prerecorded or a live stream.

### Audio-only and Video-only (Prerecorded) (1.2.1) {#audio-only-and-video-only-prerecorded}

* Erfolgskriterium 1.2.1
* Level A
* Nur-Audio und Nur-Video (aufgezeichnet): Für aufgezeichnete Nur-Audio und Nur-Video-Medien gilt Folgendes, außer wenn das Audio oder Video eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist:
   * Aufgezeichnetes Nur-Audio: Eine Alternative für zeitbasierte Medien wird bereitgestellt, die gleichwertige Informationen für aufgezeichnete Nur-Audio-Inhalte darstellt.
   * Aufgezeichnetes Nur-Video: Es wird entweder eine Alternative für zeitbasierte Medien oder ein Audio-Track bereitgestellt, die/der gleichwertige Informationen für aufgezeichnete Nur-Video-Inhalte darstellt.

#### Purpose - Audio-only and Video-only (Prerecorded) (1.2.1) {#purpose-audio-only-and-video-only-prerecorded}

Für folgende Personen kann der barrierefreie Zugang für Video und Audio eingeschränkt sein:

* Personen mit eingeschränktem Sehvermögen, wenn es keinen Soundtrack gibt oder wenn der Soundtrack nicht ausreicht, um sie über die Vorgänge im Video oder in der Animation zu informieren;
* Personen mit eingeschränktem Hörvermögen oder gehörlose Personen, die den Soundtrack nicht hören können.
* Personen, die den Soundtrack zwar hören können, doch den gesprochenen Inhalt nicht verstehen (weil er beispielsweise in einer Sprache aufgezeichnet ist, die sie nicht verstehen).

Video oder Audio kann auch für Personen unzugänglich sein, die Browser oder Geräte verwenden, die die Wiedergabe von Inhalt in bestimmten Medienformaten wie zum Beispiel Adobe Flash nicht unterstützen.

Wenn diese Informationen in einem anderen Format bereitgestellt werden, wie zum Beispiel als Text (oder Audio für Video ohne Audio), können die Informationen für die Personen barrierefrei zugänglich sein, die nicht auf den ursprünglichen Inhalt zugreifen können

#### How to Meet - Audio-only and Video-only (Prerecorded) (1.2.1) {#how-to-meet-audio-only-and-video-only-prerecorded}

* Wenn der Inhalt vorab aufgezeichnetes Audio ohne Video ist (z. B. ein Podcast):
   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einem Texttranskript des Audioinhalts bereit. Das Transkript sollte eine HTML-Seite mit einer Textentsprechung aller gesprochenen und wichtigen nicht gesprochenen Inhalte sein und den Sprecher, eine Beschreibung der Szenerie, sprachliche Ausdrücke sowie eine Beschreibung anderer wichtiger Audioinhalte angeben.
* Wenn der Inhalt eine Animation oder ein vorab aufgezeichnetes Video ohne Audio ist:
   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einer entsprechenden Textbeschreibung der Informationen im Video bereit.
   * Es kann auch eine entsprechende Audiobeschreibung in einem häufig verwendeten Audioformat wie MP3 sein.

>[!NOTE]
>
>Wenn der Audio- oder Videoinhalt als Alternative zu Inhalten bereitgestellt wird, die bereits in einem anderen Format auf derselben Webseite vorhanden sind, ist möglicherweise keine zusätzliche Alternative erforderlich.
>
>Die Leitlinien, [Verständigung WCAG 1.2.1](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html), enthalten weitere Informationen.

Das Einfügen von Multimedia in Ihre AEM-Webseiten ist ähnlich wie das Einfügen eines Bildes. Da Multimedia jedoch weit mehr ist als ein Standbild, gibt es eine Vielzahl von verschiedenen Einstellungen und Optionen zur Steuerung wie die Multimedia-Inhalte abgespielt werden.

>[!NOTE]
>
>Wenn Sie Multimedia mit informativem Inhalt verwenden, müssen Sie auch Links zu Alternativen erstellen. Beispielsweise müssen Sie zum Hinzufügen eines Texttranskripts eine HTML-Seite für die Anzeige des Transkripts erstellen und dann neben oder unter dem Audioinhalt einen Link hinzufügen.

#### More Information - Audio-only and Video-only (Prerecorded) (1.2.1) {#more-information-audio-only-and-video-only-prerecorded}

* [Erfolgskriterien 1.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)
* [Erfolgskriterien 1.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-only-and-video-only-prerecorded)

### Beschriftungen (vorgezeichnet) (1.2.2) {#captions-prerecorded}

* Erfolgskriterium 1.2.2
* Level A
* Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck - Beschriftungen (vorab aufgezeichnet) (1.2.2) {#purpose-captions-prerecorded}

Menschen, die Taub oder schwerhörig sind, werden nicht auf Audioinhalte zugreifen können oder große Schwierigkeiten haben. Beschriftungen sind Textäquivalente für gesprochene und nicht gesprochene Audiodaten, die zur richtigen Zeit während des Videos auf dem Bildschirm angezeigt werden. Sie ermöglichen es Menschen, die das Audio nicht hören können, zu verstehen, was passiert.

#### How to Meet - Captions (Prerecorded) (1.2.2) {#how-to-meet-captions-prerecorded}

Es gibt zwei Arten von Untertiteln:

* Öffnen: immer sichtbar, wenn das Video wiedergegeben wird
* Geschlossen: Benutzer können die Untertitel ein- oder ausschalten

Verwenden Sie möglichst geschlossene Untertitel, da Benutzer so wählen können, ob die Untertitel angezeigt werden.

For closed captions, you will need to create and provide a synchronized caption file in an appropriate format (such as [SMIL](https://www.w3.org/AudioVideo/)) alongside the video file (details on how to do this are beyond the scope of this guide, but we have provided links to some tutorials under [More Information - Captions (Prerecorded) (1.2.2)](#more-information-captions-prerecorded). Stellen Sie sicher, dass Sie eine Notiz bereitstellen oder die Untertitel-Funktion im Videoplayer aktivieren, damit Benutzer wissen, dass Untertitel für das Video verfügbar sind.

Wenn Sie offene Untertitel verwenden müssen, betten Sie den Text im Videotrack ein. Dies erreichen Sie mithilfe von Anwendungen zur Videobearbeitung, die die Überlagerung von Untertiteln im Video ermöglichen.

#### More Information - Captions (Prerecorded) (1.2.2) {#more-information-captions-prerecorded}

* [Erfolgskriterium 1.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded.html)
* [Erfolgskriterien 1.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#captions-prerecorded)

<!--
* [W3C: Synchronized Multimedia](https://www.w3.org/AudioVideo/)
* [Captions, Transcripts, and Audio Descriptions - by WebAIM](https://webaim.org/techniques/captions/)
-->

### Audio Description or Media Alternative (Prerecorded) (1.2.3) {#audio-description-or-media-alternative-prerecorded}

* Erfolgskriterium 1.2.3
* Level A
* Audiobeschreibung oder Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien oder eine Audiobeschreibung des aufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Purpose - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#purpose-audio-description-or-media-alternative-prerecorded}

Blinde Menschen oder Menschen mit eingeschränktem Sehvermögen haben keinen Zugang zu Informationen in einem Video oder einer Animation, wenn diese nur visuell vermittelt werden oder wenn der Soundtrack nicht genügend Informationen bietet, damit sie verstehen können, was visuell gezeigt wird.

#### How to Meet - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-prerecorded}

Es gibt zwei Ansätze zur Erfüllung dieses Erfolgskriteriums. Beide sind akzeptabel:

1. Hinzufügen einer weiteren Audiobeschreibung für den Videoinhalt. Hierzu gibt es drei verschiedene Möglichkeiten:
   * Fügen Sie in Pausen im vorhandenen Dialog Informationen zu den Änderungen der Szene ein, die nicht als Teil des vorhandenen Audiotracks präsentiert werden:
   * Stellen Sie einen neuen, zusätzlichen und optionalen Audio-Track bereit, der den ursprünglichen Soundtrack und zudem weitere Audioinformationen zu den Änderungen in der Szene enthält.
      * Dadurch können Benutzer zwischen dem vorhandenen Audio-Track (der *keine* Audiobeschreibung enthält) und dem neuen Audio-Track (*mit* einer Audiobeschreibung) wechseln.
      * Dadurch wird verhindert, dass Benutzer, die die zusätzliche Beschreibung nicht benötigen, gestört werden.
   * Erstellen Sie eine zweite Version des Videoinhalts, um erweiterte Audiobeschreibungen zu ermöglichen. Dies verringert die Schwierigkeiten, die sich durch Einfügen von detaillierten Audiobeschreibungen in Lücken zwischen dem vorhandenen Dialog ergeben, weil das Audio und Video an passenden Stellen unterbrochen werden muss. Als Ergebnis kann eine viel längere Audiobeschreibung gegeben werden, bevor die Aktion erneut startet. Wie im vorigen Beispiel wird dies am besten als optionaler eigener Audio-Track bereitgestellt, um eine Störung der Benutzer zu verhindern, die keine zusätzliche Beschreibung benötigen.
1. Stellen Sie ein Text-Transkript bereit, das eine angemessene Textentsprechung der Audio- und Bildelemente des Videos oder der Animation ist. Dies sollte gegebenenfalls einen Hinweis darauf enthalten, wer spricht, eine Beschreibung der Einstellung, Ereignisse oder Informationen, die visuell präsentiert werden, sowie Ausdrücke zur Stimmabgabe. Abhängig von der Länge können Sie das Transkript auf derselben Seite wie das Video oder die Animation einfügen, oder auch auf einer separaten Seite. In diesem Fall müssen Sie einen Link zu dem Transkript neben dem Video oder der Animation bereitstellen.

Genaue Details zur Erstellung von Audiobeschreibungen für Video würden den Rahmen dieses Leitfadens sprengen. Die Erstellung von Audiobeschreibungen können zeitaufwändig sein, doch andere Adobe-Produkte helfen Ihnen bei diesen Aufgaben.

#### More Information - Audio Description or Media Alternative (Prerecorded) (1.2.3) {#more-information-audio-description-or-media-alternative-prerecorded}

* [Erfolgskriterien 1.2.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-or-media-alternative-prerecorded.html)
* [Erfolgskriterien 1.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)

<!--
* [Adobe Encore](https://www.adobe.com/products/encore.html) - a DVD authoring software tool
-->

### Untertitel (live) (1.2.4)          {#captions-live}

* Erfolgskriterium 1.2.4
* Level AA
* Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Untertitel (Live) (1.2.4)     {#purpose-captions-live}

This success criterion is identical to [Captions (Prerecorded)](#captions-prerecorded) in that it addresses accessibility barriers experienced by people who are deaf or hearing-impaired, except that this success criterion deals with live presentations such as webcasts.

#### Erfüllen: Untertitel (Live) (1.2.4) {#how-to-meet-captions-live}

Follow the guidance provided for [Captions (Prerecorded)](#captions-prerecorded) above. However, due to the live nature of the media, caption provision has to be created as quickly as possible and in response to what is happening. Therefore, you should consider using real time captioning or speech-to-text tools.

Detaillierte Anweisungen dazu würden den Rahmen dieses Dokuments sprengen, doch in den folgenden Ressourcen finden Sie nützliche Informationen:

* [WebAIM: Echtzeit-Untertitelung](https://www.webaim.org/techniques/captions/realtime.php)

* [AccessComputing-Projekt (University of Washington): Können Beschriftungen automatisch mit Spracherkennung erstellt werden?](https://www.washington.edu/accesscomputing/can-captions-be-generated-automatically-using-speech-recognition)

#### Weitere Informationen: Untertitel (Live) (1.2.4)     {#more-information-captions-live}

* [Erfolgskriterien 1.2.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/captions-live.html)
* [Erfolgskriterien 1.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#captions-live)

### Audiobeschreibung (vorab aufgezeichnet) (1.2.5)  {#audio-description-prerecorded}

* Erfolgskriterium 1.2.5
* Level AA
* Audiobeschreibung (aufgezeichnet): Audiobeschreibungen werden für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt.

#### Purpose - Audio Description (Prerecorded) (1.2.5) {#purpose-audio-description-prerecorded}

This success criterion is identical to [Audio Description or Media Alternative (Prerecorded)](#audio-description-or-media-alternative-prerecorded), except that authors must provide a much more detailed audio description to conform to Level AA.

#### How to Meet - Audio Description (Prerecorded) (1.2.5) {#how-to-meet-audio-description-prerecorded}

Follow the guidance provided for [Audio Description or Media Alternative (Prerecorded)](#audio-description-or-media-alternative-prerecorded).

#### More Information - Audio Description (Prerecorded) (1.2.5) {#more-information-audio-description-prerecorded}

* [Erfolgskriterien 1.2.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-prerecorded.html)
* [Erfolgskriterien 1.2.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-prerecorded)

### Anpassbar (1.3)     {#adaptable}

[Richtlinie 1.3 Anpassbar: Erstellen von Inhalten, die auf verschiedene Arten präsentiert werden können (zum Beispiel mit einfacherem Layout) ohne Informationen oder die Struktur zu verlieren.](https://www.w3.org/TR/WCAG/#adaptable)

Diese Richtlinie behandelt die Anforderungen zur Unterstützung folgender Personen:

* kann möglicherweise nicht auf Informationen zugreifen, die von einem Autor in der Standarddarstellung dieses Inhalts dargestellt werden (z. B. ein mehrspaltiges Layout oder eine Seite mit starker Verwendung von Farbe und/oder Bildern).

* kann nur Audio oder eine alternative visuelle Anzeige wie z. B. großen Text oder hohen Kontrast verwenden.

### Informationen und Beziehungen (1.3.1)          {#info-and-relationships}

* Erfolgskriterium 1.3.1
* Level A
* Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmatisch festgelegt werden oder sind im Text verfügbar.

#### Zweck: Informationen und Beziehungen (1.3.1)     {#purpose-info-and-relationships}

Many assistive technologies used by people with disabilities rely on structural information in order to effectively display or *understand* content. Diese Strukturinformationen können in Form von Seitenüberschriften, Tabellenzeilen und Spaltenüberschriften sowie Listentypen vorliegen. Beispielsweise könnte ein Benutzer mit einem Bildschirmleser von Überschrift zu Überschrift durch eine Seite navigieren. Wenn Seiteninhalte jedoch nur über visuelles Styling statt das zugrundeliegende HTML strukturiert wurden, stehen den Hilfstechnologien keine Strukturinformationen zur Verfügung und deren Fähigkeit zur Unterstützung eines leichteren Browsings ist erheblich eingeschränkt.

Dieses Erfolgskriterium besteht darin sicherzustellen, dass solche Strukturinformationen programmgesteuert über HTML oder andere Kodierungstechniken bereitgestellt werden, damit Browser und Hilfstechnologien auf die Informationen zugreifen und diese nutzen können.

#### Erfüllen: Informationen und Beziehungen (1.3.1)     {#how-to-meet-info-and-relationships}

Mit AEM ist es ganz einfach, semantisch aussagekräftige Webinhalte mit den entsprechenden HTML-Elementen zu erstellen. Öffnen Sie Ihren Seiteninhalt im RTE (einer Textkomponente) und geben Sie im Menü **Paraformat** (Absatzsymbol) das entsprechende Strukturelement (zum Beispiel Absatz, Überschrift usw.) an.

Sie können sicherstellen, dass Ihre Webseiten die richtige Struktur erhalten, indem Sie gegebenenfalls die folgenden Elemente verwenden:

* **Überschriften:** Solange die Barrierefreiheitsfunktionen der RTE aktiviert sind, werden in AEM Angebots 3 die Seitenüberschriften angezeigt. Sie können diese verwenden, um Abschnitte und Unterabschnitte des Inhalts zu identifizieren. Überschrift 1 ist die höchste Überschriftenstufe und Stufe 3 die niedrigste. Der Systemadministrator kann das System so konfigurieren, dass mehr Überschriftenstufen verwendet werden können.

* **Listen**: Sie können HTML verwenden, um drei verschiedene Arten von Listen anzugeben:
   * Das Element `<ul>` wird für *nicht geordnete* Listen (Aufzählungslisten) verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet. Verwenden Sie in RTE das Symbol **Aufzählungsliste**.
   * Das Element `<ol>` wird für *nummerierte* Listen verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet. Verwenden Sie in RTE das Symbol **Nummerierte Liste**.
   Wenn Sie Inhalt in einen Listentyp ändern möchten, markieren Sie den entsprechenden Text und wählen Sie den jeweiligen Listentyp aus. Wie im obigen Beispiel, in dem gezeigt wird, wie Absatztext eingegeben wird, werden die entsprechenden Listenelemente automatisch zum HTML-Code hinzugefügt.

   Im Vollbildmodus sind die einzelnen Symbole **Aufzählungsliste** und **Nummerierte Liste** sichtbar. Wenn Sie sich nicht im Vollbildmodus befinden, sind die beiden Optionen hinter dem einzelnen Symbol **Listen** verfügbar.

* **Tabellen**: Datentabellen müssen anhand von HTML-Tabellenelementen identifiziert werden:
   * Ein Element `<table>`
   * Ein Element `<tr>` für jede Tabellenzeile
   * Ein Element `<th>` für jede Zeilen- und Spaltenüberschrift
   * Ein Element `<td>` für jede Datenzelle
   Außerdem nutzen barrierefrei zugängliche Tabellen die folgenden Elemente und Attribute:

   * Das Element `<caption>` wird verwendet, um für die Tabelle eine sichtbare Tabellenbeschriftung bereitzustellen. Beschriftungen werden standardmäßig zentriert über der Tabelle angezeigt, können jedoch mit CSS entsprechend positioniert werden. Die Beschriftung ist programmatisch mit der Tabelle verknüpft und ist daher eine nützliche Methode zur Angabe einer Einführung in den Inhalt.
   * Das Element `<summary>` unterstützt blinde Benutzer dabei, die in einer Tabelle dargestellten Informationen zu verstehen, weil ihnen damit eine Inhaltsangabe dessen geboten wird, was sehende Benutzer sehen können. Dies ist besonders nützlich bei komplexen oder unkonventionellen Tabellen-Layouts (dieses Attribut wird nicht im Browser angezeigt, sondern nur für Hilfstechnologien ausgelesen).
   * Das Attribut `scope` des Elements `<th>` wird verwendet, um anzugeben, ob eine Zelle eine Überschrift für eine bestimmte Zeile oder eine bestimmte Spalte darstellt. Auf ähnliche Weise können die Überschrift und ID-Attribute in komplexen Tabellen verwendet werden, bei denen Datenzellen mit einer oder mehreren Überschriften verknüpft sein können.
   >[!NOTE]
   >
   >By default, these elements and attributes are not directly available, though it is possible for the system administrator to add support for these values in the **Table properties** dialog box (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes).

   So öffnen Sie das Dialogfeld **Tabelle**, in dem Sie die Registerkarte **Tabelleneigenschaften** auswählen können:

   * Definieren Sie eine entsprechende **Beschriftung**.
   * Im Idealfall entfernen Sie alle Standardwerte für **Breite**, **Höhe**, **Rand**, **Zellauffüllung**, **Zellabstand**, da diese Eigenschaften in einem globalen Stylesheet festgelegt werden können.
   Sie können dann die **Zellen-Eigenschaften** verwenden, um festzulegen, ob es sich bei der Zelle um eine Daten- oder Kopfzeilenzelle handelt:  

* **Betonung**: Verwenden Sie das `<strong>` Element oder `<em>` das Element, um die Hervorhebung anzugeben. Verwenden Sie keine Überschriften zum Hervorheben von Text in Absätzen.
   * Markieren Sie den Text, den Sie hervorheben möchten.
   * Klicken Sie auf das Symbol **B** (für `<strong>`) oder das Symbol **I** (für `<em>`), die im Bereich **Eigenschaften** angezeigt werden (vergewissern Sie sich, dass HTML ausgewählt ist).

      >[!NOTE]
      >
      >RTE ist in einer Standardinstallation von AEM mit den folgenden Symbolen eingerichtet:
      >
      >* `<b>` für `<strong>`
      >* `<i>` für `<em>`
      >
      >Sie haben die gleiche Wirkung, doch sollten `<strong>` und `<em>` bevorzugt werden, weil sie für HTML semantisch korrekt sind. Bei der Entwicklung Ihrer Projektinstanz kann das Entwicklungs-Team den RTE zur Verwendung von `<strong>` und `<em>` (anstelle von `<b>` und `<i>`) konfigurieren.


* **Komplexe Datentabellen**: In einigen Fällen, in denen komplexe Tabellen mit zwei oder mehr Überschriftebenen vorhanden sind, reicht das normale Dialogfeld „Tabelleneigenschaften“ nicht aus, um alle benötigten Strukturinformationen anzugeben. Für diese Arten von komplexen Tabellen müssen direkte Beziehungen zwischen den Überschriften und deren dazugehörigen Zellen erstellt werden. Zu diesem Zweck werden die Attribute **Überschrift** und **ID** verwendet.

   >[!NOTE]
   >
   >Das ID-Attribut ist in Standardinstallationen nicht verfügbar. Es kann durch Konfigurieren von HTML-Regeln und des Serialisierungsprogramms im RTE aktiviert werden.

   Beispielsweise werden in der Tabelle unten Kopfzeilen und IDs zugeordnet, um eine programmatische Verbindung für Benutzer von Hilfstechnologien herzustellen.

   ```xml
     <table>
       <tr>
         <th rowspan="2" id="h">Homework</th>
         <th colspan="3" id="e">Exams</th>
         <th colspan="3" id="p">Projects</th>
       </tr>
       <tr>
         <th id="e1" headers="e">1</th>
         <th id="e2" headers="e">2</th>
         <th id="ef" headers="e">Final</th>
         <th id="p1" headers="p">1</th>
         <th id="p2" headers="p">2</th>
         <th id="pf" headers="p">Final</th>
       </tr>
       <tr>
         <td headers="h">15%</td>
         <td headers="e e1">15%</td>
         <td headers="e e2">15%</td>
         <td headers="e ef">20%</td>
         <td headers="p p1">10%</td>
         <td headers="p p2">10%</td>
         <td headers="p pf">15%</td>
       </tr>
     </table>
   ```

   Um dies in AEM zu erreichen, müssen Sie das Markup hinzufügen, indem Sie direkt den Modus zur Bearbeitung des Quellcodes verwenden.

   >[!NOTE]
   >
   >Diese Funktion ist in einer Standardinstallation nicht sofort verfügbar. Dazu ist die Konfiguration des RTE, der HTML-Regeln und des Serialisierungsprogramms erforderlich.

#### Weitere Informationen: Informationen und Beziehungen (1.3.1) {#more-information-info-and-relationships}

* [Erfolgskriterien 1.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)
* [Erfolgskriterien 1.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#info-and-relationships)

### Sinnvolle Sequenz (1.3.2)  {#meaningful-sequence}

* Erfolgskriterium 1.3.2
* Level A
* Sinnvolle Sequenz: Wenn die Reihenfolge, in der Inhalte präsentiert werden, ihre Bedeutung beeinflusst, kann eine korrekte Lesesequenz programmgesteuert bestimmt werden.

#### Zweck - Bedeutende Sequenz (1.3.2) {#purpose-meaningful-sequence}

Das Ziel dieses Erfolgskriteriums besteht darin, einem Benutzeragent die Möglichkeit zu geben, eine alternative Darstellung des Inhalts bereitzustellen und dabei die Leserichtung zu erhalten, die zum Verständnis der Bedeutung erforderlich ist. Es ist wichtig, dass es möglich ist, mindestens eine sinnvolle Inhaltssequenz programmatisch zu bestimmen. Inhalte, die dieses Erfolgskriterium nicht erfüllen, können Benutzer verwirren oder disorisieren, wenn die Hilfstechnologie den Inhalt in der falschen Reihenfolge liest oder wenn alternative Stylesheets oder andere Formatierungsänderungen angewendet werden.

#### Wie wird eine sinnvolle Sequenz erreicht (1.3.2) {#how-to-meet-meaningful-sequence}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 1.3.2](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence).

#### Weitere Informationen - Bedeutende Sequenz (1.3.2) {#more-information-meaningful-sequence}

* [Erfolgskriterien 1.3.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/meaningful-sequence.html)
* [Erfolgskriterien 1.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)

### Sensorische Eigenschaften (1.3.3)          {#sensory-characteristics}

* Erfolgskriterium 1.3.3
* Level A
* Sensorische Eigenschaften: Anweisungen, die zum Verstehen und Bedienen von Inhalt verfügbar sind, beziehen sich nicht nur auf sensorische Eigenschaften der Komponenten wie Form, Größe, visuelle Position, Ausrichtung oder Klang.

#### Zweck: Sensorische Eigenschaften (1.3.3)     {#purpose-sensory-characteristics}

Entwickler konzentrieren sich bei der Präsentation von Informationen oft auf visuelle Design-Funktionen wie Farbe, Form, Textstil oder die absolute oder relative Position eines Inhaltselements. Dabei kann es sich um sehr leistungsstarke Designtechniken zur Informationsübermittlung handeln (und die allgemeine Zugänglichkeit für sehbehinderte Benutzer mit kognitiven Zugänglichkeitsanforderungen verbessern), aber blinde oder sehbehinderte Menschen können möglicherweise nicht auf Informationen zugreifen, die eine visuelle Identifizierung von Attributen wie Position, Farbe oder Form erfordern.

Entsprechend sind Informationen, für die zwischen verschiedenen Klängen (z. B. Inhalte, die von einer Frau oder einem Mann gesprochen werden) unterschieden werden muss, für Menschen mit eingeschränktem Hörvermögen nicht verfügbar, wenn sie nicht in Textalternativen für den Audioinhalt umgesetzt wurden.

>[!NOTE]
>
>Die Anforderungen, die sich auf die Alternativen für Farben beziehen, finden Sie unter [Verwendung von Farbe](#use-of-color).

#### Erfüllen: Sensorische Eigenschaften (1.3.3)     {#how-to-meet-sensory-characteristics}

Stellen Sie sicher, dass Informationen, die sich auf visuelle Eigenschaften von Seiteninhalten beziehen, auch in alternativen Formaten präsentiert werden.

* Verlassen Sie sich nicht auf die visuelle Position, um Informationen bereitzustellen. Wenn Sie beispielsweise Benutzer auf ein Menü rechts auf der Seite verweisen möchten, über das sie auf weitere Informationen zugreifen können, beziehen Sie sich nicht auf *das Menü rechts*, sondern geben Sie den Namen für das Menü an (zum Beispiel über eine Überschrift) und beziehen Sie sich im Text auf diesen Namen.
* Verlassen Sie sich nicht auf den Textstil (z. B. fett oder kursiv gedruckter Text) als einzige Methode zur Vermittlung von Informationen.

>[!NOTE]
>
>Die Verwendung beschreibender Begriffe ist dann akzeptabel, wenn diese auch in einem nicht visuellen Kontext eine Bedeutung haben. So ist z. B. die Verwendung von *oben* und *unten* in der Regel akzeptabel, da diese jeweils Inhalt vor und nach einem bestimmten Inhaltselement implizieren. Dabei bleibt die Bedeutung auch erhalten, wenn der Inhalt laut ausgesprochen wird.

#### Weitere Informationen – Sensorische Eigenschaften (1.3.3) {#more-information-sensory-characteristics}

* [Erfolgskriterien 1.3.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/sensory-characteristics.html)
* [Erfolgskriterien 1.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#sensory-characteristics)

### Unterscheidbar (1.4)     {#distinguishable}

[Richtlinie 1.4 Unterscheidbar: Erleichtern Sie den Benutzern das Sehen und Hören von Inhalt einschließlich der Unterscheidung von Vorder- und Hintergrund.](https://www.w3.org/TR/WCAG/#distinguishable)

### Verwendung von Farbe (1.4.1)          {#use-of-color}

* Erfolgskriterium 1.4.1
* Level A
* Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel eingesetzt, um Informationen zu vermitteln, eine Aktion zu kennzeichnen, eine Antwort einzuholen oder ein visuelles Element zu unterscheiden.

>[!NOTE]
>
>Dieses Erfolgskriterium bezieht sich speziell auf die Farbwahrnehmung. Andere Wahrnehmungsformen werden unter [Anpassbar (1.3)](#adaptable) behandelt. Hierzu gehören der programmtechnische Zugriff auf Farbe und andere visuelle Darstellungskodierungen.

#### Zweck - Verwendung von Farbe (1.4.1)     {#purpose-use-of-color}

Farbe bietet sichtbar eine effektive Möglichkeit, die Ästhetik von Webseiten zu verbessern, und kann auch die Vermittlung von Informationen unterstützen. Es gibt jedoch eine Vielzahl visueller Beeinträchtigungen, von Farbenblindheit bis zur Beeinträchtigung der Farbwahrnehmung, die dazu führt, dass manche Menschen zwischen bestimmten Farben nicht unterscheiden können. Aus diesem Grund ist die farbliche Kodierung ein unzuverlässiges Mittel für die Bereitstellung von Informationen.

Jemand mit einer Rot-Grün-Sehschwäche kann z. B. nicht zwischen Grünschattierungen und Rotschattierungen unterscheiden. Er sieht möglicherweise beide Farben als eine dritte Farbe (z. B. braun) und kann daher nicht zwischen rot, grün und braun unterscheiden.

Außerdem können Menschen, die einen reinen Textbrowser, monochrome Anzeigen oder einen Schwarzweiß-Ausdruck auf Papier nutzen, keine Farben wahrnehmen.

Ein weiterer Aspekt ist der *ausgewählte* Status eines Schnittstellenelements (z. B. Registerkarten, Schaltflächen zum Umschalten), das auf eine andere Weise übertragen werden muss als nur mit Farbe und über eine visuelle Darstellung hinaus. Bei solchen Elementen ist die zusätzliche Verwendung von Mustern, Formen und programmatischen Informationen hilfreich, wenn ein vollständig inklusives Benutzererlebnis erstellt wird, das sich nicht auf einen bestimmten Sinn stützt.

#### Erfüllen - Verwendung von Farbe (1.4.1)     {#how-to-meet-use-of-color}

Immer wenn Farbe verwendet wird, um Informationen zu vermitteln, müssen Sie sicherstellen, dass die verfügbaren Informationen auch verfügbar sind, wenn die Farbe nicht sichtbar ist.

Stellen Sie z. B. sicher, dass die durch die Farbe vermittelte Information auch explizit im Text enthalten ist.

Wenn Farbe als Hinweis für Informationen verwendet wird, sollten Sie für einen zusätzlichen visuellen Hinweis sorgen, z. B. durch Ändern des Stils (z. B. fett, kursiv) oder der Schriftart. So können auch Personen mit Seh- oder Farbschwäche die Informationen erkennen. Man darf sich jedoch nicht vollständig auf diese Maßnahmen verlassen, da sie für Menschen, die die Seite überhaupt nicht sehen können, keine Hilfe bieten. Daher ist es (manchmal) nützlich, versteckten Text bereitzustellen oder programmatische Lösungen wie die [Accessible Rich Internet Applications (ARIA) Suite von Webstandards](https://www.w3.org/WAI/standards-guidelines/aria/)zu verwenden, um diese Informationen an nicht sichtbare Benutzer zu übermitteln.

#### Weitere Informationen – Verwendung von Farbe (1.4.1) {#more-information-use-of-color}

* [Erfolgskriterien 1.4.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
* [Erfolgskriterien 1.4.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#use-of-color)

### Audiosteuerung (1.4.2)  {#audio-control}

* Erfolgskriterium 1.4.2
* Level A
* Audiosteuerung: Wenn Audio auf einer Webseite länger als 3 Sekunden automatisch abgespielt wird, steht entweder ein Mechanismus zum Anhalten oder Anhalten der Audiowiedergabe zur Verfügung, oder es ist ein Mechanismus verfügbar, mit dem die Lautstärke unabhängig vom Gesamtsystem gesteuert werden kann.

#### Zweck - Audiosteuerung (1.4.2) {#purpose-audio-control}

Personen, die Bildschirmlesehilfen verwenden, können es schwer finden, die Sprachausgabe zu hören, wenn gleichzeitig andere Audiodateien abgespielt werden. Diese Schwierigkeit wird noch verschärft, wenn die Sprachausgabe des Bildschirmlesehilfen auf Software basiert (wie die meisten heute) und über die gleiche Lautstärkeregelung wie der Sound gesteuert wird. Darüber hinaus können einige Menschen mit kognitiven Behinderungen und Menschen, die neurodivergierend sind, eine Schallempfindlichkeit haben. Diese Personen werden feststellen, dass die Lautstärke von Audioinhalten nicht mehr verändert werden kann, was sehr störend ist.

Daher ist es wichtig, dass der Benutzer den Hintergrundton ausschalten kann.

>[!NOTE]
>
>Die Steuerung des Volumens beinhaltet die Möglichkeit, sein Volumen auf Null zu reduzieren.

#### Erfüllung - Audio-Steuerung (1.4.2) {#how-to-meet-audio-control}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 1.4.2](https://www.w3.org/WAI/WCAG21/quickref/#audio-control).

#### Weitere Informationen - Audiosteuerung (1.4.2) {#more-information-audio-control}

* [Erfolgskriterien 1.4.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-control.html)
* [Erfolgskriterien 1.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)

### Kontrast (Minimum) (1.4.3)     {#contrast-minimum}

* Erfolgskriterium 1.4.3
* Level AA
* Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1 mit folgenden Ausnahmen:
   * Großer Text: Großer Text und Bilder von großem Text haben ein Kontrastverhältnis von mindestens 3:1.
   * Incidental: Text or images of text that are part of an inactive user interface component, that are [pure decoration](https://www.w3.org/TR/WCAG/#dfn-pure-decoration), that are not visible to anyone, or that are part of a picture that contains significant other visual content, have no contrast requirement.
   * Firmenschriftzüge: Für Text, der Teil eines Logos oder eines Markennamens ist, gibt es keine Kontrastanforderungen.
   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Informationen zu Nicht-Text-Kontrast](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html) , um sicherzustellen, dass Autoren von Inhalten die zusätzlichen Anforderungen an Nicht-Text-Elemente verstehen (einschließlich Symbole, Oberflächenelemente usw.).

#### Zweck - Kontrast (Minimum) (1.4.3)     {#purpose-contrast-minimum}

Manche Menschen mit einem beeinträchtigten Sehvermögen können nicht zwischen bestimmten Farbpaaren mit geringem Kontrast unterscheiden. Die Barrierefreiheit ist für diese Menschen in folgenden Situationen eingeschränkt:

* Wenn zwischen dem Text und der Hintergrundfarbe nur wenig Kontrast besteht.
* Wenn die Farbkodierung des Textes (wie Link-Text und Text ohne Link) für die Unterscheidung der Informationen wichtig ist.

>[!NOTE]
>
>Text, der ausschließlich zu dekorativen Zwecken verwendet wird, ist von diesem Erfolgskriterium nicht betroffen.

#### Erfüllen - Kontrast (Minimum) (1.4.3)     {#how-to-meet-contrast-minimum}

Stellen Sie sicher, dass zwischen dem Text und der Hintergrundfarbe ausreichend Kontrast besteht. Das Kontrastverhältnis hängt von der Größe und dem Schriftschnitt des betroffenen Textes ab:

* Für Text mit einer Größe von weniger als 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis zwischen Text/Bildern mit Text und dem Hintergrund mindestens 4,5:1 betragen.
* Für Text mit einer Größe von mindestens 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis mindestens 3:1 betragen.
* Falls der Hintergrund gemustert ist, sollte der Hintergrund um alle Texte abgestuft sein, damit das Verhältnis von 4,5:1 oder 3:1 beibehalten wird.

>[!NOTE]
>
>Bitte beachten Sie, dass Schriftarten sich hinsichtlich der Darstellung der entsprechenden PT/PX/EM-Größe unterscheiden können.
>
>Es wird empfohlen, bei der Auswahl der passenden Schriften und der Größenanpassung für Webinhalte gutes Urteilsvermögen und Fehler auf der Seite der Lesbarkeit und Benutzerfreundlichkeit zu verwenden.

>[!NOTE]
>
>Die folgenden Sites können bei Konvertierungen in andere Einheiten hilfreich sein:
>
>* [Px to Em Calculater - Omni](https://www.omnicalculator.com/conversion/px-to-em)
>* [Schriftartgrößenkonvertierung: pixel-point-em-rem-percent](https://websemantics.uk/tools/font-size-conversion-pixel-point-em-rem-percent/)
>* [PMtoEM.com: PX-to-EM-Konvertierung einfach](http://pxtoem.com)


Verwenden Sie ein Farbkontrasttool, um das Kontrastverhältnis zu prüfen, z. B. den [Color Contrast Analyser von Paciello Group](https://www.paciellogroup.com/resources/contrast-analyser.html) oder den [Color Contrast Checker von WebAIM](https://www.webaim.org/resources/contrastchecker/). Mit diesen Tools können Sie Farbpaare prüfen und erkennen mögliche Kontrastprobleme.

Wenn es für Sie nicht so wichtig ist, das Aussehen Ihrer Seite festzulegen, können Sie alternativ keine Farben für den Hintergrund und den Text im Vordergrund festlegen. Dann brauchen Sie den Kontrast nicht zu prüfen, weil der Browser des Benutzers die Farbe für den Text und den Hintergrund ermittelt.

Falls es nicht möglich ist, die geforderten Kontraststufen zu erfüllen, müssen Sie einen Link zu einer alternativen, identischen Version der Seite bereitstellen (auf der keine Farbkontrastprobleme vorliegen) oder dem Benutzer die Anpassung des Kontrasts des Farbschemas der Seite an seine eigenen Anforderungen ermöglichen.

#### Weitere Informationen - Kontrast (Minimum) (1.4.3)     {#more-information-contrast-minimum}

* [Erfolgskriterien 1.4.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
* [Erfolgskriterien 1.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum)

### Textgröße ändern (1.4.4)  {#resize-text}

* Erfolgskriterium 1.4.4
* Level A
* Textgröße ändern: Mit Ausnahme von Bildunterschriften und Bildern von Text kann die Größe von Text ohne Hilfstechnologie bis zu 200 Prozent ohne Verlust von Inhalt und Funktionalität angepasst werden.

#### Zweck - Schriftgröße ändern (1.4.4) {#purpose-resize-text}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass visuell gerenderter Text, einschließlich textbasierter Steuerelemente (Textzeichen, die angezeigt wurden, damit sie angezeigt werden können, [im Vergleich zu Textzeichen, die noch in Datenform wie ASCII]sind), erfolgreich skaliert werden kann, sodass er von Personen mit leichten Sehbehinderungen direkt gelesen werden kann, ohne dass dazu Hilfstechnologien wie eine Vergrößerung erforderlich sind. Benutzer können von der Skalierung des gesamten Inhalts auf der Webseite profitieren, doch der Text ist äußerst wichtig.

#### Wie Sie mit Text übereinstimmen - Größe ändern (1.4.4) {#how-to-meet-resize-text}

Neben den Richtlinien unter [Erfolgskriterien 1.4.4.4](https://www.w3.org/WAI/WCAG21/quickref/#resize-text) können Sie Autoren von Inhalten empfehlen, fließende, flexible Breiten und Höhen in ihren Seitenentwürfen und Schriftgrößen (z. B. Responsive Web Design) zu verwenden, um Lesern die Möglichkeit zu geben, die Größe von Text zu ändern.

#### Weitere Informationen - Ändern der Textgröße (1.4.4) {#more-information-resize-text}

* [Erfolgskriterien 1.4.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
* [Erfolgskriterien 1.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#resize-text)

### Bilder von Text (1.4.5)     {#images-of-text}

* Erfolgskriterium 1.4.5
* Level AA
* Bilder von Text: Falls die verwendeten Technologien die visuelle Präsentation realisieren können, wird für die Vermittlung von Informationen Text verwendet – keine Bilder von Text. Dabei gelten folgende Ausnahmen:
   * Anpassbar: Das Bild des Texts kann visuell an die Anforderungen des Benutzers angepasst werden.
   * Erforderlich: Eine bestimmte Präsentation von Text ist für die zu vermittelnden Informationen erforderlich.

>[!NOTE]
>
>Firmenschriftzüge (Texte, die Teil eines Logos oder eines Markennamens sind) werden als erforderlich angesehen.

#### Zweck - Bilder von Text (1.4.5)     {#purpose-images-of-text}

Bilder von Text werden häufig verwendet, wenn ein bestimmter Textstil bevorzugt wird. Z. B. bei einem Firmenschriftzug oder wenn der Text aus einer anderen Quelle generiert wurde (z. B. ein eingescanntes Papierdokument). Im Vergleich mit in HTML dargestelltem Text, dessen Stil mittels CSS festgelegt wird, fehlt Bildern von Text jedoch die Flexibilität, die Größe oder das Erscheinungsbild zu ändern, was für Menschen mit Beeinträchtigungen der Sehfähigkeit oder mit Leseschwäche erforderlich sein kann.

#### Erfüllen - Bilder von Text (1.4.5)     {#how-to-meet-images-of-text}

Wenn Bilder von Text verwendet werden müssen, nutzen Sie CSS, um die Bilder von Text in HTML durch einen identischen Text zu ersetzen, damit der Text in einer anpassbaren Version verfügbar ist. Ein Beispiel hierfür finden Sie unter [C30: Verwenden von CSS, um Text durch Bilder von Text zu ersetzen und ein Steuerelement zum Umschalten auf der Benutzeroberfläche bereitzustellen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Weitere Informationen - Bilder von Text (1.4.5)     {#more-information-images-of-text}

* [Erfolgskriterien 1.4.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/images-of-text.html)
* [Erfolgskriterien 1.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#images-of-text)

## Grundsatz 2: Bedienbar     {#principle-operable}

[Grundsatz 2: Bedienbar – Komponenten der Benutzerschnittstelle und der Navigation müssen bedienbar sein.](https://www.w3.org/TR/WCAG/#operable)

### Barrierefreie Tastatur (2.1) {#keyboard-accessible}

[Leitlinie 2.1 Barrierefreie Tastatur: Stellen Sie alle Funktionen über eine Tastatur zur Verfügung.](https://www.w3.org/TR/WCAG/#keyboard-accessible)

Dadurch wird sichergestellt, dass Benutzer über eine Tastatur auf alle Funktionen zugreifen können.

### Tastatur (2.1.1)  {#keyboard}

* Erfolgskriterium 2.1.1
* Level A
* Tastatur: Alle Funktionen des Inhalts können über eine Tastatur ausgeführt werden, ohne dass für einzelne Tastenanschläge bestimmte Zeitpunkte erforderlich sind, es sei denn, die zugrunde liegende Funktion erfordert Eingaben, die vom Pfad der Bewegung des Benutzers und nicht nur von den Endpunkten abhängen.

#### Zweck - Tastatur (2.1.1) {#purpose-keyboard}

Ziel dieses Erfolgskriteriums ist es, sicherzustellen, dass Inhalte, wo immer möglich, über eine Tastatur- oder Tastatur-Schnittstelle bedient werden können (sodass eine alternative Tastatur verwendet werden kann). Wenn Inhalte über eine Tastatur oder eine alternative Tastatur bedient werden können, können sie auch von Personen ohne Sehvermögen (die keine Geräte wie Mäuse verwenden können, die eine augenblickliche Koordination erfordern) sowie von Personen, die alternative Tastaturen oder Eingabegeräte verwenden müssen, die als Tastaturemulatoren fungieren, verwendet werden. Zu den Keyboard-Emulatoren gehören Spracheingabe-Software, Sip-and-Puff-Software, On-Screen-Tastaturen, Scan-Software und eine Vielzahl von Hilfstechnologien und alternative Tastaturen. Personen mit niedrigem Sehvermögen haben möglicherweise auch Schwierigkeiten, einen Zeiger zu verfolgen und die Verwendung von Software viel einfacher (oder nur möglich) zu finden, wenn sie ihn über die Tastatur steuern können.

#### Treffen - Tastatur (2.1.1) {#how-to-meet-keyboard}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.1.1](https://www.w3.org/WAI/WCAG21/quickref/#keyboard).

#### Weitere Informationen - Tastatur (2.1.1) {#more-information-keyboard}

* [Erfolgskriterien 2.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Erfolgskriterien 2.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)

### Keine Tastaturbelegung (2.1.2)  {#no-keyboard-trap}

* Erfolgskriterium 2.1.2
* Level A
* Keine Tastaturfüllung: Wenn der Tastaturfokus über eine Tastatur auf eine Komponente der Seite verschoben werden kann, kann der Fokus mithilfe einer Tastatur von dieser Komponente weg verschoben werden. Wenn Sie dazu über eine Tastatur verfügen, wird dem Benutzer empfohlen, den Fokus über die Methode zum Entfernen des Fokus zu verschieben.

#### Zweck - Keine Tastatureingabe (2.1.2) {#purpose-no-keyboard-trap}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass der Tastaturfokus in Unterabschnitten des Inhalts einer Webseite nicht *aufgefangen* wird. Dies ist ein häufig auftretendes Problem, wenn mehrere Formate innerhalb einer Seite kombiniert und mithilfe von Plug-Ins oder eingebetteten Anwendungen wiedergegeben werden.

Es kann vorkommen, dass die Funktionalität der Webseite den Fokus auf einen Unterabschnitt des Inhalts beschränkt (z. B. ein modaler Dialog). In solchen Fällen sollten Sie eine Methode bereitstellen, mit der ein Benutzer aus diesem Inhaltsunterabschnitt aussteigen kann (z. B. schließt die Esc-Taste den modalen Dialog oder eine Schließen-Schaltfläche den modalen Dialog).

#### Wie man mit - Keine Tastaturfalle (2.1.2) {#how-to-meet-no-keyboard-trap}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.1.2](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap).

#### Weitere Informationen - Keine Tastaturbelegung (2.1.2) {#more-information-no-keyboard-trap}

* [Erfolgskriterien 2.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Erfolgskriterien 2.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)

### genügend Zeit (2.2) {#enough-time}

[Leitlinie 2.2 Genug Zeit: Geben Sie Benutzern genügend Zeit, um Inhalte zu lesen und zu verwenden.](https://www.w3.org/TR/WCAG/#enough-time)

Dadurch wird sichergestellt, dass die Benutzer genügend Zeit zum Lesen und Handeln haben.

### Zeitverstellbar (2.2.1)  {#timing-adjustable}

* Erfolgskriterium 2.2.1
* Level A
* Tastatur: Geben Sie Benutzern genügend Zeit, um Inhalte zu lesen und zu verwenden.

#### Zweck - zeitanpassbar (2.2.1) {#purpose-timing-adjustable}

Ziel dieses Erfolgskriteriums ist es, sicherzustellen, dass Benutzer mit Behinderungen ausreichend Zeit haben, mit Webinhalten zu interagieren, wann immer dies möglich ist. Menschen mit Behinderungen wie Blindheit, Sehschwäche, Beeinträchtigung der Geschicklichkeit und kognitive Einschränkungen benötigen unter Umständen mehr Zeit, um Inhalte zu lesen oder Funktionen wie das Ausfüllen von Online-Formularen auszuführen. Wenn Webfunktionen zeitabhängig sind, ist es für einige Benutzer schwierig, die erforderliche Aktion auszuführen, bevor eine Zeitbegrenzung eintritt. Dadurch kann der Zugriff auf den Dienst für sie unzugänglich werden. Die Entwicklung von nicht zeitabhängigen Funktionen wird Menschen mit Behinderungen dabei helfen, diese Funktionen zu erfüllen. Die Bereitstellung von Optionen zum Deaktivieren von Zeitbegrenzungen, Anpassen der Zeitbegrenzungen oder zum Anfordern von mehr Zeit bis zum Eintreten einer Zeitbegrenzung hilft Benutzern, die mehr Zeit benötigen, als erwartet, um Aufgaben erfolgreich abzuschließen. Diese Optionen werden in der Reihenfolge aufgeführt, die für den Benutzer am nützlichsten ist. Die Deaktivierung von Zeitbegrenzungen ist besser als die Anpassung der Zeitbegrenzungen, was besser ist als die Anforderung von mehr Zeit, bevor eine Zeitbegrenzung eintritt.

#### Anpassbare Zeiteinstellung (2.2.1) {#how-to-meet-timing-adjustable}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.2.1](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable).

#### Weitere Informationen - zeitanpassbar (2.2.1) {#more-information-timing-adjustable}

* [Erfolgskriterien 2.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/timing-adjustable.html)
* [Erfolgskriterien 2.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)

### Pausieren, Beenden, Ausblenden (2.2.2)          {#pause-stop-hide}

* Erfolgskriterium 2.2.2
* Level A
* Pausieren, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln:
   * Sich bewegend, blinkend, scrollend: Für alle sich bewegenden, blinkenden oder scrollenden Informationen, die (a) automatisch starten, (b) länger als 5 Sekunden dauern und (c) parallel zu anderen Inhalten dargestellt werden, muss es einen Mechanismus für den Benutzer geben, um diese zu pausieren, zu beenden oder auszublenden, sofern die Bewegung, das Blinken oder das Scrollen nicht Teil einer Aktivität ist, bei der dies erforderlich ist.
   * Automatische Aktualisierung: Für alle sich automatisch aktualisierenden Informationen, die (a) automatisch starten und (b) parallel mit anderen Inhalten dargestellt werden, muss es einen Mechanismus geben, damit der Benutzer die Aktualisierung pausieren, beenden oder ausblenden oder die Häufigkeit der Aktualisierung kontrollieren kann, sofern die automatische Aktualisierung nicht Teil einer Aktivität ist, bei der dies erforderlich ist.

Folgendes sollte beachtet werden:

1. Die Anforderungen für flackernden oder blinkenden Inhalt finden Sie unter „Gestalten Sie Inhalte nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen“ (2.3).
1. Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Webseite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhalt, der regelmäßig durch Software aktualisiert wird oder der auf den Benutzer-Agenten gestreamt wird, darf keine Informationen bewahren oder darstellen, die zwischen dem Initiieren des Anhaltens und dem Fortsetzen der Darstellung generiert oder empfangen wurden, da dies technisch möglicherweise nicht machbar ist und in vielen Situationen irreführend sein kann.
1. Eine Animation, die Teil einer Ladephase oder eines ähnlichen Szenarios ist, kann als erforderlich erachtet werden, wenn während dieser Phase keine Benutzerinteraktion möglich ist und wenn das Fehlen einer Fortschrittsanzeige Benutzer verwirren oder zu der Annahme verleiten kann, der Inhalt sei eingefroren oder beschädigt.

#### Zweck - Pausieren, Beenden, Ausblenden (2.2.2)     {#purpose-pause-stop-hide}

Bestimmte Benutzer finden möglicherweise Inhalte, die verschoben werden, ablenkend oder sogar physisch schmerzhaft, was es schwierig macht, sich auf andere Teile der Seite zu konzentrieren. Darüber hinaus sind solche Inhalte für Menschen schwierig, die beim Lesen Probleme haben, sich bewegendem Text zu folgen.

#### Erfüllen - Pausieren, Beenden, Ausblenden (2.2.2)     {#how-to-meet-pause-stop-hide}

Abhängig von der Art des Inhalts können Sie beim Erstellen von Webseiten mit sich bewegendem, blitzendem oder blinkendem Inhalt die folgenden Empfehlungen beachten:

* Bieten Sie die Möglichkeit, das Scrollen des Inhalts anzuhalten, um Benutzern Zeit zum Lesen zu geben. Beispielsweise News-Ticker, automatisch aktualisierter Text und Bildkarusselle, die automatisch weitergeleitet werden.
* Stellen Sie sicher, dass blinkende Inhalte maximal fünf Sekunden lang blinken.
* Verwenden Sie geeignete Technologien, um bewegte oder blinkende Inhalte anzuzeigen, die vom Browser deaktiviert werden können. Z. B. Dateien im GIF- (Graphics Interchange Format) oder APNG-Format (Animated Portable Network Graphics).
* Stellen Sie ein Formularsteuerelement auf der Webseite bereit, damit der Benutzer alle bewegten oder blinkenden Inhalte auf der Seite deaktivieren kann.
* Wenn eine der oben genannten Optionen nicht möglich ist, stellen Sie einen Link zu einer Seite bereit, die den gesamten Inhalt enthält, jedoch ohne dass verschoben oder blinkt werden muss.

#### Weitere Informationen - Pausieren, Beenden, Ausblenden (2.2.2)     {#more-information-pause-stop-hide}

* [Erfolgskriterium 2.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html)
* [Erfolgskriterium 2.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#pause-stop-hide)

### Krampfanfälle und physikalische Reaktionen (2.3) {#seizures-and-physcial-reactions}

[Leitlinie 2.3 Krampfanfälle: Entwerfen Sie den Inhalt nicht so, dass es bekanntermaßen zu Krämpfen oder körperlichen Reaktionen kommt.](https://www.w3.org/TR/WCAG/#seizures-and-physical-reactions)

### Grenzwert von maximal dreimaligem Blitzen (2.3.1)     {#three-flashes-or-below-threshold}

* Erfolgskriterium 2.3.1
* Level A
* Grenzwert von maximal dreimaligem Blitzen: Webseiten dürfen nichts enthalten, das in einem Zeitraum von einer Sekunde öfter als dreimal blitzt oder dessen Blitz unterhalb der allgemeinen Grenzwerte für Blitze und rote Blitze liegt.

>[!NOTE]
>
>Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Webseite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG/#cc5).

#### Zweck – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bestimmten Fällen können blitzende Inhalte photosensitive Anfälle auslösen. Dieses Erfolgskriterium ermöglicht Benutzern den Zugriff und die Nutzung des gesamten Inhalts ohne Beeinträchtigung durch blitzende Inhalte.

#### Erfüllen - Grenzwert von maximal dreimaligem Blitzen (2.3.1)     {#how-to-meet-three-flashes-or-below-threshold}

Stellen Sie sicher, dass die folgenden Techniken zur Anwendung kommen:

* Stellen Sie sicher, dass Komponenten in einem Zeitraum von einer Sekunde nicht öfter als dreimal blitzen.
* Falls die obige Bedingung nicht erfüllt werden kann, platzieren Sie den blitzenden Inhalt in einem *kleinen sicheren Bereich* in Pixel auf dem Bildschirm. Dieser Bereich wird anhand einer komplexen Formel berechnet, die unter [G176: Blitzende Bereiche ausreichend klein halten](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176) behandelt wird. Diese Technik sollte ausschließlich dann angewendet werden, wenn ein blitzender Inhalt *unbedingt* erforderlich ist.

#### Weitere Informationen – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Erfolgskriterium 2.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/three-flashes-or-below-threshold.html)
* [Erfolgskriterium 2.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#three-flashes-or-below-threshold)

### Navigierbar (2.4) {#navigable}

[Leitlinie 2.4 Navigierbar: Bieten Sie Möglichkeiten, Benutzern beim Navigieren, Suchen von Inhalten und Bestimmen, wo sie sich befinden.](https://www.w3.org/TR/WCAG/#navigable)

Dadurch wird sichergestellt, dass der Inhalt einfach und einfach zu navigieren ist.

### Blöcke umgehen (2.4.1)  {#bypass-blocks}

* Erfolgskriterium 2.4.1
* Level A
* Blöcke umgehen: Es gibt einen Mechanismus, mit dem Inhaltsblöcke umgangen werden können, die auf mehreren Webseiten wiederholt werden.

#### Zweck - Umgehungsblöcke (2.4.1) {#purpose-bypass-blocks}

Ziel dieses Erfolgskriteriums ist es, Personen, die sequenziell durch Inhalte navigieren, einen direkteren Zugriff auf den primären Inhalt der Webseite zu ermöglichen. Webseiten und Anwendungen enthalten oft Inhalte, die auf anderen Seiten oder Bildschirmen angezeigt werden. Beispiele für wiederholte Inhaltsblöcke sind unter anderem Navigationslinks, Kopfzeilengrafiken, Menüs und Anzeigenrahmen. Kleine wiederholte Abschnitte wie einzelne Wörter, Wortgruppen oder einzelne Links werden für die Zwecke dieser Bestimmung nicht als Blöcke angesehen.

#### Wie man mit Blöcken umgeht (2.4.1) {#how-to-meet-bypass-blocks}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.4.1](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks).

#### Weitere Informationen - Umgehungsblöcke (2.4.1) {#more-information-bypass-blocks}

* [Erfolgskriterien 2.4.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
* [Erfolgskriterien 2.4.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)

### Seite mit Titel versehen (2.4.2)          {#page-titled}

* Erfolgskriterium 2.4.2
* Level A
* Seite mit Titel versehen: Webseiten haben einen Titel, der das Thema oder den Zweck beschreibt

#### Zweck - Seite mit Titel versehen (2.4.2)     {#purpose-page-titled}

Dieses Erfolgskriterium ist für alle Benutzer hilfreich - unabhängig von etwaigen Beeinträchtigungen - um schnell den Inhalt einer Webseite zu ermitteln, ohne die Seite vollständig zu lesen. Dies ist insbesondere dann nützlich, wenn mehrere Webseiten in Browsertabs geöffnet sind, da der Seitentitel auf den Tabs angezeigt wird, was die Seiten schnell auffindbar macht.

#### Erfüllen - Seite mit Titel versehen (2.4.2)     {#how-to-meet-page-titled}

Wenn Sie im AEM eine neue HTML-Seite erstellen, können Sie den Seitentitel angeben. Stellen Sie sicher, dass der Titel den Inhalt und Zweck der Seite, insbesondere individuelle Aspekte, angemessen beschreibt, damit Besucher schnell erkennen können, ob der Inhalt tatsächlich für ihre Bedürfnisse relevant ist.

Sie können während der Bearbeitung einer Seite auch den Seitentitel ändern. Öffnen Sie dazu **Seiteninformationen** > **Eigenschaften**.

#### Weitere Informationen – Seite mit Titel versehen (2.4.2) {#more-information-page-titled}

* [Erfolgskriterium 2.4.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
* [Erfolgskriterium 2.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#page-titled)

### Fokusreihenfolge (2.4.3)  {#focus-order}

* Erfolgskriterium 2.4.3
* Level A
* Fokusreihenfolge: Wenn eine Webseite sequenziell navigiert werden kann und die Navigationssequenzen die Bedeutung oder den Betrieb beeinflussen, erhalten fokussierbare Komponenten den Fokus in einer Reihenfolge, die Bedeutung und Operativität beibehält.

#### Zweck - Fokusreihenfolge (2.4.3) {#purpose-focus-order}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass Benutzer, die nacheinander durch Inhalte navigieren, auf Informationen in einer Reihenfolge stoßen, die der Bedeutung des Inhalts entspricht und von der Tastatur aus bedient werden kann. Dadurch wird Verwirrung verringert, da Benutzer ein konsistentes mentales Modell des Inhalts bilden können. Es kann verschiedene Bestellungen geben, die logische Beziehungen im Inhalt widerspiegeln. Beispielsweise spiegelt der Wechsel durch Komponenten in einem Online-Formular, das aus mehreren Feldern und/oder Schritten besteht, die logischen Beziehungen im Inhalt wider.

#### Treffen mit der Fokusreihenfolge (2.4.3) {#how-to-meet-focus-order}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.4.3](https://www.w3.org/WAI/WCAG21/quickref/#focus-order).

#### Weitere Informationen - Fokusreihenfolge (2.4.3) {#more-information-focus-order}

* [Erfolgskriterien 2.4.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/focus-order.html)
* [Erfolgskriterien 2.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)

### Link-Zweck (im Kontext) (2.4.4)          {#link-purpose-in-context}

* Erfolgskriterium 2.4.4
* Level A
* Linkzweck (im Kontext): Der Zweck jedes Links kann allein durch den Linktext oder durch den Linktext zusammen mit dem programmatisch festgelegten Linkkontext bestimmt werden. Ausgenommen sind Fälle, in denen der Zweck des Links für Benutzer generell mehrdeutig ist.

#### Zweck - Link-Zweck (im Kontext) (2.4.4)     {#purpose-link-purpose-in-context}

Unabhängig von etwaigen Beeinträchtigungen ist es für alle Benutzer von entscheidender Bedeutung, dass durch einen passenden Linktext klar erkenntlich ist wohin ein Link führt. Dies erleichtert Benutzern die Entscheidung, ob sie einem Link folgen möchten oder nicht. Für sehende Benutzer ist ein aussagekräftiger Linktext ausgesprochen nützlich, wenn sich auf einer Seite mehrere Links befinden (vor allem, wenn eine Seite sehr viel Text enthält), da ein aussagekräftiger Linktext einen deutlicheren Hinweis auf die Funktion der Zielseite liefert. Benutzer einiger Hilfstechnologien, die eine Liste aller Links auf einer Seite generieren können, können den Linktext einfacher aus dem Kontext verstehen, wenn der Linktext sowohl eindeutig als auch informativ ist. Sehbehinderte Personen mit kognitiven Behinderungen können jedoch verwirrt werden, wenn ein Link nicht genügend Informationen bereitstellt, um genau zu beschreiben, wohin der Link führt.

#### Erfüllen - Link-Zweck (im Kontext) (2.4.4)     {#how-to-meet-link-purpose-in-context}

Stellen Sie vor allem sicher, dass der Link-Text den Zweck eines Links eindeutig beschreibt.

* Schlechtes Beispiel:
   * Text: Einzelheiten zu unseren Abendkursen im Herbst 2010 finden Sie hier.
   * Grund: Es geht nicht deutlich und unmissverständlich hervor wohin der Link führt.
* Gutes Beispiel:
   * Text: Abendkurse im Herbst 2010 – Details.
   * Grund: Durch eine kleine Anpassung des Textes und der Position des Linkelements lässt sich der Linktext verbessern:

Links sollten auf den Seiten eine konsistente Bezeichnung erhalten. Dies gilt insbesondere für Navigationsleisten. Wenn ein Link zu einer bestimmten Seite z. B. auf einer Seite **Publikationen** heißt, dann sollte er auch auf allen anderen Seiten denselben Namen erhalten.

Zum Zeitpunkt des Schreibens gibt es einige Probleme mit der Verwendung von Titelattributen, um sicherzustellen, dass ähnliche Links auf einer Seite eindeutige Informationen über das Ziel liefern (z. B. &quot;mehr lesen&quot;bezieht sich oft auf eine Reihe unterschiedlicher Ziele):

* Der im Titelattribut enthaltene Text steht im Allgemeinen nur Mausbenutzern als QuickInfo-Popup zur Verfügung und kann nicht konsistent über die Tastatur oder von mobilen Benutzern aufgerufen werden.
* Die Sprachausgabe kann Title-Attribute auslesen, diese Funktion ist jedoch nicht unbedingt standardmäßig aktiviert. Daher ist es für Benutzer eventuell nicht ersichtlich, dass ein Title-Attribut vorhanden ist.
* Es ist schwierig das Erscheinungsbild des Titeltextes anzupassen, weshalb es für manche Menschen schwierig oder unmöglich sein kann, diesen zu lesen.

Das Title-Attribut kann also genutzt werden, um zusätzlichen Kontext zu einem Link bereitzustellen, Sie sollten aber diese Einschränkungen bedenken und es daher nicht als Alternative für einen geeigneten Linktext nutzen.

Wenn ein Link aus einem Bild besteht, müssen Sie sicherstellen, dass der alternative Text für das Bild das Ziel des Links beschreibt. Wenn z. B. ein Bild eines Bücherregals als Link zu den Publikationen einer Person festgelegt wird, sollte der alternative Text **Publikationen von John Smith** lauten und nicht **Bücherregal**.

Falls der Link-Anker Text enthält, der ergänzend zum Bildelement den Zweck des Links beschreibt (und dieser Text neben dem Bild angezeigt wird), können Sie für das Bild alternativ ein leeres Alt-Attribut verwenden:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
>
>Der obige Ausschnitt dient der Illustration. Es wird empfohlen, die Komponente **Bild** zu verwenden.

Es ist zwar ratsam, Linktext bereitzustellen, der den Zweck des Links ohne zusätzlichen Kontext identifiziert, doch ist dies nicht immer möglich. Links ohne Kontext können in den folgenden Fällen verwendet werden. HTML-Beispiele hierzu finden Sie unter [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context).

* Wenn der Link-Text zu einer Liste eng zusammenhängender Links gehört und das den Link umgebende Listenelement ausreichend Kontext liefert.
* Wenn der Zweck eines Links aus dem *vorangehenden* (nicht dem nachfolgenden) Text des Absatzes klar hervorgeht.
* Wenn der Link in einer Datentabelle enthalten ist und der Zweck über die zugehörigen Überschriften deutlich erkennbar ist.
* Wenn eine Liste mit Links in einem Satz Überschriften enthalten ist und die Überschrift einen ausreichenden Kontext liefert.
* Wenn eine Liste mit Links in einem geschachtelten Link enthalten ist und das übergeordnete Listenelement des geschachtelten Links einen ausreichenden Kontext liefert.

In einigen Fällen, in denen sich mehrere Links auf einer Seite befinden (von denen jeder das Ziel des Links durch komplexe, aber erforderliche Details angibt), kann es sinnvoll sein, eine alternative Version der Webseite anzubieten, die denselben Inhalt anzeigt, auf der der Linktext jedoch weniger ausführlich ist.

Alternativ können Skripts verwendet werden. Dabei wird im Link selbst ein minimaler Text bereitgestellt. Bei der Aktivierung des entsprechenden Steuerelements im oberen Bereich der Seite wird der Link-Text jedoch *erweitert* und es werden mehr Details angezeigt. Einen ähnlichen Ansatz bietet die Verwendung von CSS, um den vollständigen Link für sehende Benutzer *auszublenden*, ihn für Benutzer der Sprachausgabe jedoch auszugeben. Dies überschreitet jedoch den Rahmen dieses Dokuments; weitere Informationen hierzu finden Sie jedoch unter [Weitere Informationen – Link-Zweck (im Kontext) (2.4.4)](#more-information-link-purpose-in-context).

#### Weitere Informationen – Link-Zweck (im Kontext) (2.4.4) {#more-information-link-purpose-in-context}

* [Erfolgskriterium 2.4.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html)
* [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)

<!--
* [C7: Using CSS to hide a portion of the link text](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)
-->

### Mehrere Möglichkeiten (2.4.5)  {#multiple-ways}

* Erfolgskriterium 2.4.5
* Level AA
* Mehrere Möglichkeiten: Es gibt mehrere Möglichkeiten, um eine Webseite innerhalb eines Satzes von Webseiten zu finden, es sei denn, die Webseite ist das Ergebnis eines Prozesses oder ein Schritt in diesen Prozess.

#### Zweck - Mehrere Möglichkeiten (2.4.5) {#purpose-multiple-ways}

Ziel dieses Erfolgskriteriums ist es, Benutzern die Möglichkeit zu geben, Inhalte so zu finden, dass sie ihren Bedürfnissen am besten entsprechen. Benutzer können eine Technik leichter oder verständlicher als eine andere finden.

Auch kleine Sites sollten den Benutzern Orientierungshilfen bieten. Für eine dreigliedrige oder vierseitige Site mit allen von der Startseite verknüpften Seiten kann es ausreichen, einfach Links von und zur Startseite anzugeben, in der die Links auf der Startseite auch als Sitemap dienen können.

#### Wie Sie sich auf verschiedene Arten treffen können (2.4.5) {#how-to-meet-multiple-ways}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.4.5](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways).

#### Weitere Informationen - Mehrere Möglichkeiten (2.4.5) {#more-information-multiple-ways}

* [Erfolgskriterien 2.4.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/multiple-ways.html)
* [Erfolgskriterien 2.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)

### Überschriften und Etiketten (2.4.6)  {#headings-and-labels}

* Erfolgskriterium 2.4.6
* Level AA
* Überschriften und Etiketten: Überschriften und Beschriftungen beschreiben Thema oder Zweck.

#### Zweck - Überschriften und Etiketten (2.4.6) {#purpose-headings-and-labels}

Das Ziel dieses Erfolgskriteriums ist es, Benutzern dabei zu helfen, zu verstehen, welche Informationen in Webseiten enthalten sind und wie diese Informationen organisiert sind. Wenn Überschriften klar und beschreibend sind, können Benutzer die Informationen, die sie suchen, leichter finden und die Beziehungen zwischen verschiedenen Teilen des Inhalts besser verstehen. Beschreibende Beschriftungen helfen Benutzern, bestimmte Komponenten im Inhalt zu identifizieren.

#### Wie man mit Überschriften und Etiketten umgeht (2.4.6) {#how-to-meet-headings-and-labels}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.4.6](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels).

#### Weitere Informationen - Überschriften und Etiketten (2.4.6) {#more-information-headings-and-labels}

* [Erfolgskriterien 2.4.6 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels.html)
* [Erfolgskriterien 2.4.6 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)

### Fokus sichtbar (2.4.7)  {#focus-visible}

* Erfolgskriterium 2.4.7
* Level AA
* Fokus sichtbar: Jede Tastatur-funktionsfähige Benutzeroberfläche verfügt über einen Betriebsmodus, bei dem der Tastaturfokusindikator sichtbar ist.

#### Zweck - Sichtbarer Fokus (2.4.7) {#purpose-focus-visible}

Der Zweck dieses Erfolgskriteriums ist es, einer Person zu helfen, zu wissen, welches Element den Tastaturfokus hat.

Es muss möglich sein, dass eine Person weiß, welches Element von mehreren Elementen den Tastaturfokus hat. Wenn auf dem Bildschirm nur eine mit Tastaturbefehlen umsetzbare Steuerung vorhanden ist, wird das Erfolgskriterium erfüllt, da das visuelle Design nur ein mit Tastaturbefehlen umsetzbares Element enthält.

Wenn im Erfolgskriterium &quot;Betriebsart&quot;steht, ist dies für Plattformen zu berücksichtigen, die möglicherweise nicht immer einen Fokusindikator anzeigen. In den meisten Fällen gibt es nur eine Betriebsart, sodass diese Erfolgskriterien gelten.

#### Meet - Focus Visible (2.4.7) {#how-to-meet-focus-visible}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 2.4.7](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible).

#### Weitere Informationen - Fokus sichtbar (2.4.7) {#more-information-focus-visible}

* [Erfolgskriterien 2.4.7 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
* [Erfolgskriterien 2.4.7 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)

## Grundsatz 3: Verständlich     {#principle-understandable}

[Grundsatz 3: Verständlich – Informationen und die Bedienung der Benutzerschnittstelle müssen verständlich sein.](https://www.w3.org/TR/WCAG/#understandable)

### Machen Sie Inhalt lesbar und verständlich (3.1)     {#make-text-content-readable-and-understandable}

[Richtlinie 3.1 Lesbar: Machen Sie Inhalt lesbar und verständlich.](https://www.w3.org/TR/WCAG/#readable)

### Sprache der Seite (3.1.1)     {#language-of-page}

* Erfolgskriterium 3.1.1
* Level A
* Sprache der Seite: Die voreingestellte menschliche Sprache einer Webseite kann programmatisch bestimmt werden.

#### Zweck - Sprache der Seite (3.1.1)     {#purpose-language-of-page}

Der Zweck dieses Erfolgskriteriums besteht darin, sicherzustellen, dass Texte und andere linguistische Inhalte fehlerfrei gerendert werden. Für Benutzer der Sprachausgabe stellt dies sicher, dass der Inhalt korrekt ausgesprochen wird, während bei visuellen Browsern die Wahrscheinlichkeit höher ist, dass bestimmte Zeichensätze richtig angezeigt werden.

#### Erfüllen - Sprache der Seite (3.1.1)     {#how-to-meet-language-of-page}

Um dieses Erfolgskriterium zu erfüllen, kann die Standardsprache einer Web-Seite über das Attribut `lang` innerhalb des Elements `<html>` am Anfang der Seite festgelegt werden. Beispiel:

* If a page is written in English, the `<html>` element should read:
   `<html lang = “en”>`

* Eine auf Spanisch wiederzugebende Seite sollte folgende Norm annehmen:
   `<html lang = “es”>`

In AEM, the default language of your page is set when creating the page, but may also be changed when editing [Page Properties](/help/sites-authoring/editing-page-properties.md).

>[!NOTE]
>
>AEM bietet eine weitere Feinabstimmung für Variationen einer Stammsprache; Beispielsweise American Engish - en-us, British English - en-gb und Canadian English - en-ca. Diese Detailstufe ist für Hilfstechnologien oft überflüssig, kann aber auch für regionale Variationen des Seiteninhalts verwendet werden.

#### Weitere Informationen – Sprache der Seite (3.1.1) {#more-information-language-of-page}

* [Erfolgskriterium 3.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
* [Erfolgskriterium 3.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#language-of-page)
* Die Codes basieren auf ISO 639-1. Eine umfangreichere Liste der Codes für die einzelnen Sprachen finden Sie auf der [W3 Schools-Website](https://www.w3schools.com/tags/ref_language_codes.asp).

### Sprache von Teilen (3.1.2)          {#language-of-parts}

* Erfolgskriterium 3.1.2
* Level AA
* Sprache von Teilen: Die menschliche Sprache aller Abschnitte und Sätze im Inhalt kann programmatisch bestimmt werden. Ausgenommen sind Eigennamen, technische Fachbegriffe, Wörter einer unbestimmten Sprache und Wörter oder Wendungen, die Teil des Jargons des direkt umliegenden Textes sind.

#### Zweck - Sprache von Teilen (3.1.2)     {#purpose-language-of-parts}

Der Zweck dieses Erfolgskriteriums ähnelt dem Zweck des Erfolgskriteriums [Sprache der Seite](#language-of-page). Es gilt jedoch für Webseiten, die auf einer Seite Inhalte im mehreren Sprachen enthalten (z. B. in Form von Zitaten oder wenig geläufigen Lehnwörtern).

Seiten, die dieses Erfolgskriterium erfüllen, bieten folgende Möglichkeiten:

* Software für die Braille-Übersetzung kann akzentuierte Zeichen einfügen.
* Bildschirmlesehilfen können Wörter aussprechen, die Sonderzeichen enthalten oder nicht in der auf Seitenebene festgelegten Standardsprache enthalten sind.
* Übersetzungstools wie der Google Übersetzer können Inhalt korrekt von einer Sprache in eine andere übersetzen.

#### Erfüllen - Sprache von Teilen (3.1.2)     {#how-to-meet-language-of-parts}

Mit dem Attribut `lang` können Änderungen der Sprache des Inhalts ermittelt werden. Ein deutschsprachiges Zitat (ISO 639-1-Code “de”) kann z. B. wie folgt angezeigt werden:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
>
>Blockzitate werden in standardmäßigen Instanzen nicht unterstützt. Sie können eine benutzerdefinierte Komponente entwickeln, um dieses Feature zu unterstützen.

Auf ähnliche Weise kann der Browser ein wenig geläufiges Lehnwort oder eine Redewendung korrekt rendern, wenn das Element `span` wie folgt verwendet wird:

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</code>.</p>
```

>[!NOTE]
>
>Dieses Erfolgskriterium muss nicht beachtet werden, wenn Namen oder Städte in verschiedenen Sprachen vorkommen oder wenn Sie Lehnwörter oder Redewendungen nutzen, die in der Standardsprache gängig geworden sind (wie *Schadenfreude* im Englischen).

Um ein span-Element mit der entsprechenden Sprache hinzuzufügen, können Sie Ihren HTML-Code im Bearbeitungsmodus für den Quelltext im RTE manuell bearbeiten, damit er wie oben aussieht. Alternatively the `lang` attribute can be included in the RTE by a system administrator (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

#### Weitere Informationen – Sprache von Teilen (3.1.2) {#more-information-language-of-parts}

* [Erfolgskriterium 3.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/language-of-parts.html)
* [Erfolgskriterium 3.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#language-of-parts)

### Vorhersagbar (3.2) {#predictable}

[Leitlinie 3.2 Vorhersagbar: Webseiten erscheinen und funktionieren auf vorhersehbare Weise.](https://www.w3.org/TR/WCAG/#predictable)

Dadurch soll sichergestellt werden, dass die Webseiten einheitlich aussehen und funktionieren.

### Fokus (3.2.1)  {#on-focus}

* Erfolgskriterium 3.2.1
* Level A
* Fokus: Wenn eine Komponente der Benutzeroberfläche den Fokus erhält, wird keine Änderung des Kontexts ausgelöst.

#### Zweck - Fokus (3.2.1) {#purpose-on-focus}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass die Funktionalität vorhersehbar ist, wenn Besucher durch ein Dokument navigieren. Jede Komponente, die ein Ereignis auslösen kann, wenn sie den Fokus erhält, darf den Kontext nicht ändern. Beispiele zum Ändern des Kontexts, wenn eine Komponente den Fokus erhält, sind:

* Formulare, die automatisch gesendet werden, wenn eine Komponente den Fokus erhält;
* neue Fenster, die gestartet werden, wenn eine Komponente den Fokus erhält;
* der Fokus wird zu einer anderen Komponente geändert, wenn diese Komponente den Fokus erhält;

Der Fokus kann entweder über die Tastatur (z. B. mit der Tabulatortaste zu einem Steuerelement) oder über die Maus (z. B. durch Klicken auf ein Textfeld) auf ein Steuerelement verschoben werden. Wenn Sie die Maus über ein Steuerelement bewegen, wird der Fokus nur dann verschoben, wenn Skripterstellung dieses Verhalten implementiert. Beachten Sie, dass bei einigen Steuerelementen durch Klicken auf ein Steuerelement auch das Steuerelement aktiviert werden kann (z.B. Schaltfläche), was wiederum eine Änderung im Kontext auslösen kann.

#### Treffen - fokus (3.2.1) {#how-to-meet-on-focus}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.2.1](https://www.w3.org/WAI/WCAG21/quickref/#on-focus).

#### Weitere Informationen - Schwerpunkt (3.2.1) {#more-information-on-focus}

* [Erfolgskriterien 3.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/on-focus.html)
* [Erfolgskriterien 3.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)

### Beim Eingang (3.2.2)  {#on-input}

* Erfolgskriterium 3.2.2
* Level A
* Bei Eingabe: Eine Änderung der Einstellung einer Komponente der Benutzeroberfläche führt nicht automatisch zu einer Änderung des Kontexts, es sei denn, der Benutzer wurde über das Verhalten vor der Verwendung der Komponente informiert.

#### Zweck - Ein Eingang (3.2.2) {#purpose-on-input}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass die Eingabe von Daten oder die Auswahl eines Formularsteuerelements vorhersehbare Auswirkungen hat. Wenn Sie die Einstellung einer Komponente der Benutzeroberfläche ändern, ändert sich ein Aspekt im Steuerelement, der beibehalten wird, wenn der Benutzer nicht mehr damit interagiert. Wenn Sie also ein Kontrollkästchen aktivieren, Text in ein Textfeld eingeben oder die Liste ändern, ändert sich deren Einstellung, aber die Aktivierung eines Links oder einer Schaltfläche nicht. Änderungen im Kontext können Benutzer verwirren, die die Änderung nicht leicht wahrnehmen oder leicht von Änderungen ablenken. Kontextänderungen sind nur dann angemessen, wenn klar ist, dass eine solche Änderung als Reaktion auf die Aktion des Benutzers erfolgt.

#### Meet - On Input (3.2.2) {#how-to-meet-on-input}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.2.2](https://www.w3.org/WAI/WCAG21/quickref/#on-input).

#### Weitere Informationen - Bei Eingabe (3.2.2) {#more-information-on-input}

* [Erfolgskriterien 3.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html)
* [Erfolgskriterien 3.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-input)

### Konsistente Navigation (3.2.3)  {#consistent-navigation}

* Erfolgskriterium 3.2.3
* Level AA
* Konsistente Navigation: Navigationsmechanismen, die auf mehreren Webseiten innerhalb einer Gruppe von Webseiten wiederholt werden, werden bei jeder Wiederholung in derselben relativen Reihenfolge angezeigt, es sei denn, der Benutzer initiiert eine Änderung.

#### Zweck - Konsistente Navigation (3.2.3) {#purpose-consistent-navigation}

Ziel dieses Erfolgskriteriums ist es, Benutzer, die mit wiederholten Inhalten auf einer Reihe von Webseiten interagieren und mehrmals nach bestimmten Informationen oder Funktionen suchen müssen, zur Verwendung einer konsistenten Darstellung und eines einheitlichen Layouts zu ermutigen. Personen mit geringer Sehschärfe, die eine Vergrößerung des Bildschirms verwenden, um einen kleinen Teil des Bildschirms gleichzeitig anzuzeigen, verwenden häufig visuelle Hinweise und Seitengrenzen, um wiederholten Inhalt schnell zu finden. Die Darstellung wiederholter Inhalte in derselben Reihenfolge ist auch für visuelle Benutzer wichtig, die räumliche Speicher oder visuelle Hinweise im Entwurf verwenden, um wiederholten Inhalt zu finden.

Beachten Sie, dass die Verwendung des Wortes &quot;gleiche Reihenfolge&quot;in diesem Abschnitt nicht bedeutet, dass Unternavigationsmenüs nicht verwendet werden können oder dass Blöcke der sekundären Navigation oder der Seitenstruktur nicht verwendet werden können. Stattdessen soll dieses Erfolgskriterium Benutzern helfen, die mit wiederholten Inhalten auf verschiedenen Webseiten interagieren, um den Speicherort der gesuchten Inhalte vorhersagen und schneller finden zu können, wenn sie erneut darauf treffen.

Benutzer können eine Änderung der Reihenfolge durch Verwendung von Benutzeragenten für adaptive Benutzer oder durch Festlegen von Voreinstellungen vornehmen, damit die Informationen so dargestellt werden, dass sie für sie am nützlichsten sind.

#### Konsistente Navigation (3.2.3) {#how-to-meet-consistent-navigation}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.2.3](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation).

#### Weitere Informationen - Konsistente Navigation (3.2.3) {#more-information-consistent-navigation}

* [Erfolgskriterien 3.2.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/consistent-navigation.html)
* [Erfolgskriterien 3.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)

### Konsistente Identifizierung (3.2.4)  {#consistent-identification}

* Erfolgskriterium 3.2.4
* Level A
* Konsistente Identifizierung: Komponenten, die innerhalb einer Reihe von Webseiten die gleiche Funktionalität aufweisen, werden konsistent identifiziert.

#### Zweck - Konsistente Identifizierung (3.2.4) {#purpose-consistent-identification}

Ziel dieses Erfolgskriteriums ist die einheitliche Identifizierung funktionaler Komponenten, die wiederholt in einer Reihe von Webseiten angezeigt werden. Eine Strategie, die Benutzer von Bildschirmlesehilfen beim Betrieb einer Website verwenden, besteht darin, sich stark auf ihre Kenntnis der Funktionen zu verlassen, die auf verschiedenen Webseiten angezeigt werden können. Wenn identische Funktionen auf verschiedenen Webseiten unterschiedliche Bezeichnungen (oder allgemein einen anderen leicht zugänglichen Namen) aufweisen, wird die Verwendung der Site erheblich schwieriger. Es kann auch verwirrend sein und die kognitive Last für Menschen mit kognitiven Einschränkungen erhöhen. Daher wird eine einheitliche Kennzeichnung hilfreich sein.

Diese Konsistenz erstreckt sich auch auf Textalternativen. Wenn Symbole oder andere Elemente, die keine Textelemente sind, die gleiche Funktion haben, sollten auch deren Textalternativen konsistent sein.

Wenn es zwei Komponenten auf einer Webseite gibt, die beide die gleiche Funktionalität wie eine Komponente auf einer anderen Seite in einem Satz von Webseiten haben, müssen alle 3 konsistent sein. Daher sind die beiden auf derselben Seite konsistent.

Obwohl es wünschenswert und Best Practice ist, immer innerhalb einer einzelnen Webseite konsistent zu sein, befasst sich 3.2.4 nur mit Konsistenz innerhalb einer Reihe von Webseiten, bei denen etwas auf mehr als einer Seite im Satz wiederholt wird.

#### Wie wird eine konsistente Identifizierung erreicht (3.2.4) {#how-to-meet-consistent-identification}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.2.4](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification).

#### Weitere Informationen - Konsistente Identifizierung (3.2.4) {#more-information-consistent-identification}

* [Erfolgskriterien 3.2.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/consistent-identification.html)
* [Erfolgskriterien 3.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)

### Input Assistance (3.3) {#input-assistance}

[Richtlinie 3.3 Hilfestellung bei der Eingabe: Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren.](https://www.w3.org/TR/WCAG/#input-assistance)

### Fehlerkennung (3.3.1)  {#error-identification}

* Erfolgskriterium 3.3.1
* Level A
* Fehlerkennung: Wird automatisch ein Eingabefehler erkannt, wird das fehlerhafte Element identifiziert und der Fehler wird dem Benutzer im Text beschrieben.

#### Zweck - Fehlererkennung (3.3.1) {#purpose-error-identification}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass die Benutzer wissen, dass ein Fehler aufgetreten ist, und feststellen können, was falsch ist. Die Fehlermeldung sollte so spezifisch wie möglich sein. Bei einer fehlgeschlagenen Formularübermittlung reicht die erneute Anzeige des Formulars und die Angabe der fehlerhaften Felder nicht aus, um festzustellen, dass ein Fehler aufgetreten ist. Bildschirmlesehilfen-Benutzer wissen beispielsweise erst dann, wenn sie auf einen der Indikatoren stoßen. Sie können das Formular ganz verlassen, bevor sie auf die Fehleranzeige stoßen, weil sie der Ansicht sind, dass die Seite einfach nicht funktionsfähig ist. Gemäß der Definition in WCAG ist ein [Eingabefehler](https://www.w3.org/TR/WCAG/#dfn-input-error) vom Benutzer bereitgestellte Informationen, die nicht akzeptiert werden. Hierzu gehört Folgendes:

Informationen, die für die Webseite erforderlich sind, vom Benutzer jedoch nicht angegeben werden, oder Informationen, die vom Benutzer bereitgestellt werden, aber nicht dem erforderlichen Datenformat oder den zulässigen Werten entsprechen.
Beispiel:

* der Benutzer nicht die richtige Abkürzung in Bundesland, Provinz, Region usw. eingeben kann. field;
* der Benutzer eine Statusabkürzung eingibt, die kein gültiger Status ist;
* der Benutzer eine nicht vorhandene Postleitzahl oder Postleitzahl eingibt;
* der Benutzer ein Geburtsdatum von 2 Jahren in der Zukunft einträgt;
* der Benutzer in sein Telefonnummernfeld Buchstaben oder Klammern eingibt, die nur Zahlen akzeptieren;
* der Benutzer ein Angebot eingibt, das unter dem vorherigen Angebot oder dem Mindestangebot liegt.

#### Erfüllung - Fehlererkennung (3.3.1) {#how-to-meet-error-identification}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.3.1](https://www.w3.org/WAI/WCAG21/quickref/#error-identification).

#### Weitere Informationen - Fehlererkennung (3.3.1) {#more-information-error-identification}

* [Erfolgskriterien 3.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-identification.html)
* [Erfolgskriterien 3.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)

### Beschriftungen oder Anweisungen (3.3.2)     {#labels-or-instructions}

* Erfolgskriterium 3.3.2
* Level A
* Beschriftungen oder Anweisungen: Wenn der Inhalt eine Eingabe durch den Benutzer erfordert, werden Beschriftungen oder Anweisungen bereitgestellt.

#### Zweck - Beschriftungen oder Anweisungen (3.3.2)     {#purpose-labels-or-instructions}

Das Bereitstellen von Anweisungen, die Menschen beim Ausfüllen von Formularen unterstützen, bildet einen entscheidenden Bestandteil der bewährten Verfahrenspraxis für eine benutzerfreundliche Oberfläche. Dies ist insbesondere für Menschen mit visuellen oder kognitiven Einschränkungen hilfreich, die das Layout eines Formulars und die Art der in einem bestimmten Formularfeld anzugebenden Daten andernfalls nur schwer nachvollziehen können.

##### Forms

In the AEM WKND demo project a default label is added when you add a form component, such as a **Text Field**, to the page. Dieser Standardtitel beruht auf dem Typ der Komponente. Auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds für das Feld können Sie Ihren eigenen Titel angeben. Es ist wichtig, dass Sie sicherstellen, dass Benutzer mithilfe von Beschriftungen leichter nachvollziehen können welche Daten in den einzelnen Formularkomponenten erwartet werden.

Das Feld **Titel** muss für Feldelemente verwendet werden, weil es eine Beschriftung bereitstellt, die für Sprachausgabetechnologien verfügbar ist. Es reicht nicht aus, einfach nur eine Beschriftung im Text neben dem Feld anzugeben.

Für einige Komponenten können Beschriftungen auch über das Kontrollkästchen **Titel ausblenden** ausgeblendet werden. Auf diesem Weg ausgeblendete Beschriftungen sind für Sprachausgabetechnologien weiterhin verfügbar, werden auf dem Bildschirm jedoch nicht angezeigt. Auch wenn dies in einigen Situationen einen guten Ansatz bilden kann, ist es in der Regel besser, möglichst immer eine sichtbare Beschriftung hinzuzufügen, da manche Benutzer nur einen sehr kleinen Ausschnitt des Bildschirms sehen (jeweils ein Feld) und die Felder nur anhand der Beschriftung richtig zuordnen können.

###### Bild-Schaltflächen {#image-buttons}

Where image buttons are used (for example, the **Image Button** component of the WKND project) the **Title** field in the **Title and Text** tab of the edit dialog actually provides the alt text for the image, rather than the label. Im folgenden Beispiel wurde daher für das Bild mit dem Text `Submit` im Bearbeitungsdialogfeld der Alt-Text `Submit` über das Feld **Titel** hinzugefügt.

###### Gruppen von Formularfeldern {#groups-of-form-fields}

In the WKND project, where there is a group of related controls, such as **Radio Group**, a title may be needed for the group, as well as individual controls. Wenn Sie einen Satz Optionsfelder in AEM hinzufügen, wird dieser Gruppentitel im Feld **Titel** bereitgestellt, während einzelne Titel als Optionsschaltflächen (**Elemente**) angegeben werden.

Es gibt jedoch keine programmatische Zuordnung zwischen dem Gruppentitel und den Optionsschaltflächen. Der Titel muss beim Bearbeiten der Vorlage in die erforderlichen Tags `fieldset` und `legend` gesetzt werden, um diese Zuordnung herzustellen. Dies kann ausschließlich über die Bearbeitung des Seitenquell-Codes erfolgen. Alternativ kann ein Systemadministrator die Unterstützung für diese Elemente hinzufügen, damit sie im Dialogfeld **Feldeigenschaften** angezeigt werden (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

###### Weitere Aspekte für Formulare {#additional-considerations-for-forms}

Wenn Daten in einem bestimmten Format eingegeben werden müssen, sollten Sie dies in der Beschriftung deutlich machen. Wenn z. B. ein Datum im Format `DD-MM-YYYY` eingegeben werden soll, fügen Sie diese Angabe in die Beschriftung ein. Dies führt dazu, dass die Beschriftung automatisch zusammen mit dem gewünschten Format ausgegeben wird, wenn Benutzer der Sprachausgabe auf das Feld treffen.

Wenn die Eingabe für ein Formularfeld obligatorisch ist, machen Sie dies deutlich, indem Sie das erforderliche Wort als Teil der Bezeichnung verwenden. AEM fügt ein Sternchen hinzu, wenn ein Feld erforderlich ist. Idealerweise sollte jedoch das Wort `required` (erforderlich) direkt in die Beschriftung eingefügt werden (im Feld **Titel** im Bearbeitungsdialogfeld).

Auch die Positionierung von Beschriftungen ist wichtig, da sie das Auffinden der entsprechenden Felder erleichtert. Dies ist besonders wichtig, wenn es sich um komplexe Formulare handelt. Halten Sie sich an folgende Richtlinien:

* Kontrollkästchen oder Optionsschaltflächen: 
Beschriftungen direkt rechts neben dem Feld platzieren.
* Alle anderen Formularkomponenten (z. B. Textfelder, Kombinationsfelder): 
Beschriftungen entweder direkt über dem Feld oder direkt links vom Feld platzieren.

In einfachen Formularen mit wenigen Funktionen kann die Beschriftung einer Schaltfläche mit `Submit` als Beschriftung für das angrenzende Feld dienen (z. B. `Search`). Dies ist in Situationen nützlich, in denen wenig Platz für die Beschriftung vorhanden ist.

#### Weitere Informationen – Beschriftungen oder Anweisungen (3.3.2)     {#more-information-labels-or-instructions}

* [Erfolgskriterium 3.3.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html)
* [Erfolgskriterium 3.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#labels-or-instructions)

### Fehlervorschläge (3.3.3)  {#error-suggestion}

* Erfolgskriterium 3.3.3
* Level AA
* Tastatur: Wenn automatisch ein Eingabefehler erkannt wird und Korrekturvorschläge bekannt sind, werden die Vorschläge dem Benutzer bereitgestellt, es sei denn, dies würde die Sicherheit oder den Zweck des Inhalts gefährden.

#### Zweck - Fehlervorschlag (3.3.3) {#purpose-error-suggestion}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass Benutzer geeignete Vorschläge zur Korrektur eines Eingabefehlers erhalten, wenn dies möglich ist. Die WCAG-Definition des [Eingabefehlers](https://www.w3.org/TR/WCAG/#dfn-input-error) besagt, dass es sich um &quot;vom Benutzer bereitgestellte Informationen, die nicht akzeptiert werden&quot; vom System handelt. Einige Beispiele für Informationen, die nicht akzeptiert werden, umfassen Informationen, die vom Benutzer benötigt, aber nicht angegeben werden, sowie Informationen, die vom Benutzer bereitgestellt werden, aber nicht dem erforderlichen Datenformat oder zulässigen Werten entsprechen.

Erfolgskriterium 3.3.1 sieht die Benachrichtigung über Fehler vor. Personen mit kognitiven Einschränkungen können jedoch schwer verstehen, wie die Fehler zu korrigieren sind. Sehbehinderte Menschen können möglicherweise nicht genau herausfinden, wie der Fehler zu korrigieren ist. Bei einer nicht erfolgreichen Formularübermittlung können Benutzer das Formular verlassen, da sie möglicherweise nicht sicher sind, wie der Fehler zu korrigieren ist, obwohl sie wissen, dass er aufgetreten ist.

Der Autor des Inhalts kann die Beschreibung des Fehlers angeben, oder der Benutzeragent kann die Beschreibung des Fehlers basierend auf technologiespezifischen, programmgesteuert bestimmten Informationen bereitstellen.

#### Erfüllung - Fehlervorschläge (3.3.3) {#how-to-meet-error-suggestion}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.3.3](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion).

#### Weitere Informationen - Fehlervorschläge (3.3.3) {#more-information-error-suggestion}

* [Erfolgskriterien 3.3.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-suggestion.html)
* [Erfolgskriterien 3.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)

### Fehlervermeidung (Rechts-, Finanz- und Datenrecht) (3.3.4)  {#error-prevention-legal-financial-data}

* Erfolgskriterium 3.3.4
* Level AA
* Fehlervermeidung (Recht, Finanzen, Daten): Bei Webseiten, die rechtliche Verpflichtungen oder Finanztransaktionen für den Datenspeicherung-Benutzer eingehen, die benutzersteuerbare Daten in Datensystemen ändern oder löschen oder Benutzertestantworten senden, ist mindestens einer der folgenden Punkte zutreffend:

   * ReversibleSubmissions sind reversibel.
   * CheckedData, die vom Benutzer eingegeben wurden, wird auf Eingabefehler überprüft und dem Benutzer die Möglichkeit gegeben, diese zu berichtigen.
   * BestätigterEin Mechanismus steht zur Überprüfung, Bestätigung und Korrektur von Informationen zur Verfügung, bevor die Übermittlung abgeschlossen wird.

#### Zweck - Fehlervermeidung (Recht, Finanzen, Daten) (3.3.4) {#purpose-error-prevention-legal-financial-data}

Ziel dieses Erfolgskriteriums ist es, Benutzern mit Behinderungen zu helfen, schwerwiegende Folgen zu vermeiden, die durch einen Fehler entstehen, wenn eine Aktion durchgeführt wird, die nicht rückgängig gemacht werden kann. So sind beispielsweise der Kauf von nicht rückzahlbaren Flugtickets oder die Bestellung des Aktienkaufs auf einem Maklerkonto Finanztransaktionen mit schwerwiegenden Folgen. Hat ein Benutzer am Tag der Flugreise einen Fehler gemacht, könnte er am Ende ein Ticket für den falschen Tag erhalten, das nicht ausgetauscht werden kann. Wenn der Benutzer einen Fehler bei der Anzahl der zu kaufenden Aktien machte, könnte er am Ende mehr Aktien kaufen als beabsichtigt. Beide Arten von Fehlern beinhalten Transaktionen, die sofort stattfinden und danach nicht mehr geändert werden können und sehr kostspielig sein können. Gleichermaßen kann es sich um einen nicht behebbaren Fehler handeln, wenn Benutzer versehentlich Daten ändern oder löschen, die in einer Datenbank gespeichert sind, auf die sie später zugreifen müssen, z. B. ihr gesamtes Profil für Reisen auf einer Website für Reiseleistungen. Bei der Bezugnahme auf die Änderung oder Löschung von &quot;benutzersteuerbaren&quot;Daten besteht die Absicht, einen Massenverlust von Daten wie das Löschen einer Datei oder eines Datensatzes zu verhindern. Es ist nicht beabsichtigt, eine Bestätigung für jeden Speicherbefehl oder die einfache Erstellung oder Bearbeitung von Dokumenten, Datensätzen oder anderen Daten zu verlangen.

Benutzer mit Behinderungen können möglicherweise Fehler machen. Menschen mit Leseschwächen können Zahlen und Buchstaben umsetzen, und Menschen mit motorischen Behinderungen können versehentlich Schlüssel treffen. Wenn Benutzer die Möglichkeit erhalten, Aktionen rückgängig zu machen, können sie einen Fehler korrigieren, der schwerwiegende Folgen haben könnte. Die Möglichkeit, Informationen zu überprüfen und zu korrigieren, gibt dem Benutzer die Möglichkeit, einen Fehler zu erkennen, bevor er eine Maßnahme ergreift, die schwerwiegende Folgen hat.

Benutzersteuerbare Daten sind benutzerfreundliche Daten, die der Benutzer durch eine absichtliche Aktion ändern und/oder löschen kann. Beispiele für Benutzer, die diese Daten kontrollieren, wären die Aktualisierung der Telefonnummer und -adresse für das Benutzerkonto oder das Löschen eines Datensatzes über frühere Rechnungen von einer Website. Es wird nicht auf Dinge wie Internetprotokolle und Suchmaschinen-Überwachungsdaten verwiesen, mit denen der Benutzer nicht direkt Ansicht oder Interaktion durchführen kann.

#### Vorgehensweise - Fehlervermeidung (Recht, Finanzen, Daten) (3.3.4) {#how-to-meet-error-prevention-legal-financial-data}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 3.3.4](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data).

#### Weitere Informationen - Fehlervermeidung (Recht, Finanzen, Daten) (3.3.4) {#more-information-error-prevention-legal-financial-data}

* [Erfolgskriterien 3.3.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-prevention-legal-financial-data.html)
* [Erfolgskriterien 3.3.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)

## Grundsatz 4: Robuste {#principle-robust}

[Grundsatz 4: Robust - Inhalte müssen robust genug sein, damit sie von einer Vielzahl von Benutzeragenten interpretiert werden können, einschließlich Hilfstechnologien.](https://www.w3.org/TR/WCAG/#robust)

### Compatible (4.1) {#compatible}

[Leitlinie 4.1 Kompatibel: Maximieren Sie die Kompatibilität mit aktuellen und zukünftigen Benutzeragenten, einschließlich Hilfstechnologien.](https://www.w3.org/TR/WCAG/#compatible)

Maximieren Sie die Kompatibilität mit aktuellen und zukünftigen Benutzeragenten, einschließlich Hilfstechnologien.

### Analyse (4.1.1)  {#parsing}

* Erfolgskriterium 4.1.1
* Level A
* Parsing: Bei Inhalten, die mit Markup-Sprachen implementiert wurden, haben Elemente vollständige Beginn- und End-Tags, Elemente werden gemäß ihren Spezifikationen verschachtelt, Elemente enthalten keine Duplikat-Attribute und IDs sind eindeutig, es sei denn, die Spezifikationen lassen diese Funktionen zu.

#### Zweck - Analyse (4.1.1) {#purpose-parsing}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass Benutzeragenten, einschließlich Hilfstechnologien, Inhalte exakt interpretieren und analysieren können. Wenn der Inhalt nicht in eine Datenstruktur analysiert werden kann, kann es vorkommen, dass andere Benutzeragenten ihn anders darstellen oder vollständig nicht analysieren können. Einige Benutzeragenten verwenden &quot;Reparaturtechniken&quot;, um schlecht kodierte Inhalte wiederzugeben.

Da die Reparaturverfahren je nach Benutzeragent unterschiedlich sind, können Autoren nicht davon ausgehen, dass Inhalte in einer Datenstruktur genau analysiert werden oder dass sie von spezialisierten Benutzeragenten, einschließlich Hilfstechnologien, korrekt wiedergegeben werden, es sei denn, der Inhalt wird gemäß den in der formalen Grammatik für diese Technologie festgelegten Regeln erstellt. In Markup-Sprachen führen Fehler in der Element- und Attributsyntax und Fehler bei der Bereitstellung ordnungsgemäß verschachtelter Beginn-/End-Tags zu Fehlern, die eine zuverlässige Analyse des Inhalts durch Benutzeragenten verhindern. Daher erfordert das Erfolgskriterium, dass der Inhalt nur anhand der Regeln der formalen Grammatik analysiert werden kann.

#### Treffen - Analyse (4.1.1) {#how-to-meet-parsing}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 4.1.1](https://www.w3.org/WAI/WCAG21/quickref/#parsing).

#### Weitere Informationen - Analyse (4.1.1) {#more-information-parsing}

* [Erfolgskriterien 4.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/parsing.html)
* [Erfolgskriterien 4.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#parsing)

### Name, Rolle, Wert (4.1.2)  {#name-role-value}

* Erfolgskriterium 4.1.2
* Level A
* Name, Rolle, Wert: Für alle Komponenten der Benutzeroberfläche (einschließlich, jedoch nicht beschränkt auf: Formularelemente, Links und Komponenten, die von Skripten generiert werden), der Name und die Rolle können programmgesteuert bestimmt werden; Status, Eigenschaften und Werte, die vom Benutzer festgelegt werden können, können programmgesteuert festgelegt werden. und die Benachrichtigung über Änderungen an diesen Elementen ist für Benutzeragenten, einschließlich Hilfstechnologien, verfügbar.

#### Zweck - Name, Rolle, Wert (4.1.2) {#purpose-ame-role-value}

Ziel dieses Erfolgskriteriums ist es sicherzustellen, dass Hilfstechnologien (AT) Informationen über die Benutzeroberflächen-Steuerelemente im Inhalt sammeln, aktivieren oder einstellen und über den Status der Benutzeroberflächensteuerelemente auf dem Laufenden halten können.

Wenn Standardsteuerelemente von zugänglichen Technologien verwendet werden, ist dieser Prozess einfach. Werden die Elemente der Benutzeroberfläche gemäß der Spezifikation verwendet, so sind die Bedingungen dieser Bestimmung erfüllt. (Siehe Beispiele für das Erfolgskriterium 4.1.2 unten)

Werden jedoch benutzerdefinierte Steuerelemente erstellt oder Schnittstellenelemente (in Code oder Skript) so programmiert, dass sie eine andere Rolle und/oder Funktion haben als üblich, müssen zusätzliche Maßnahmen getroffen werden, um sicherzustellen, dass die Steuerelemente wichtige Informationen für Hilfstechnologien bereitstellen und sich durch Hilfstechnologien steuern lassen.

Ein besonders wichtiger Status eines Benutzeroberflächensteuerelements ist, ob es den Fokus hat oder nicht. Der Fokuszustand eines Steuerelements kann programmgesteuert bestimmt werden, und Benachrichtigungen über eine Fokusänderung werden an Benutzeragenten und Hilfstechnologien gesendet. Ein weiteres Beispiel für den Status der Benutzeroberflächensteuerung ist, ob ein Kontrollkästchen oder ein Optionsfeld ausgewählt wurde oder ob ein ausblendbarer Baum- oder Liste-Knoten erweitert oder reduziert wird.

#### Erfüllung - Name, Rolle, Wert (4.1.2) {#how-to-meet-ame-role-value}

Befolgen Sie die Richtlinien unter [How to Meet Success Criteria 4.1.2](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value).

#### Weitere Informationen - Name, Rolle, Wert (4.1.2 {#more-information-ame-role-value}

* [Erfolgskriterien 4.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
* [Erfolgskriterien 4.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)
