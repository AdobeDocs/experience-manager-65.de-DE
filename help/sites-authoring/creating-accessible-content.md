---
title: Erstellen barrierefreier Inhalte für Adobe Experience Manager (in Übereinstimmung mit WCAG 2.1)
description: Verwenden Sie AEM, um Web-Inhalte für Menschen mit Behinderungen barrierefrei und nutzbar zu machen.
exl-id: 2145d761-f51d-482b-a0e7-ef7500c4872f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '13956'
ht-degree: 99%

---

# Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.1-Richtlinien) {#creating-accessible-content-wcag-conformance}

Die [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/) wurden von [einer Arbeitsgruppe des World Wide Web Consortium](https://www.w3.org/Consortium/activities#Accessibility_Guidelines_Working_Group) entwickelt und umfassen eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Web-Inhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind.

Zur Einführung bietet das Konsortium eine Reihe von Abschnitten und unterstützenden Dokumenten an:

* [Neue Funktionen in WCAG 2.1](https://www.w3.org/TR/WCAG/#new-features-in-wcag-2-1)
* [Erfüllen von WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [Grundlegendes zu WCAG 2.1](https://www.w3.org/WAI/WCAG21/Understanding/)
* [Techniken für WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/)
* [Die WCAG-Dokumente](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)

Siehe auch:
* [Kurzanleitung zu WCAG 2.1](/help/managing/qg-wcag.md)
* [Konformitätsberichte zur Barrierefreiheit für Adobe-Lösungen](https://www.adobe.com/accessibility/compliance.html).
* [Konfigurieren des Rich-Text-Editors für die Erstellung barrierefreier Inhalte](/help/sites-administering/rte-accessible-content.md)

Diese Richtlinien sind in drei Konformitäts-Level abgestuft: Level A (niedrigster), Level AA und Level AAA (höchster). Die Levels sind kurz definiert wie folgt:

* **Stufe A:** Ihre Site erreicht eine einfache, minimale Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-Erfolgskriterien erfüllt.
* **Stufe AA:** Dies ist ein idealer Barrierefreiheitsgrad, der angestrebt werden sollte und mit dem Ihre Site einen grundlegenden Grad der Barrierefreiheit ermöglicht, sodass sie für die meisten Personen in den meisten Situationen mit den meisten Technologien zugänglich ist. Bei Erreichen dieser Stufe sind alle Kategorie-A- und -AA-Erfolgskriterien erfüllt.
* **Stufe AAA:** Ihre Site erreicht eine sehr hohe Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-, -AA- und -AAA-Erfolgskriterien erfüllt.

Bei der Erstellung der Site sollten Sie festlegen, welchen Level Ihre Site insgesamt erfüllen soll.

Im folgenden Abschnitt finden Sie die [Ebenen der WCAG 2.1-Richtlinien](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance) mit den entsprechenden Erfolgskriterien für die [Konformitäts-Level](https://www.w3.org/TR/WCAG/#conformance-to-wcag-2-1) Level A und Level AA.

>[!NOTE]
>
>In diesem Dokument verwenden wir Folgendes:
>
>* Die [Kurznamen für die WCAG 2.1-Richtlinien](https://www.w3.org/TR/WCAG/#wcag-2-layers-of-guidance).
>* Die [Nummerierung der WCAG 2.1-Richtlinien](https://www.w3.org/TR/WCAG/#numbering-in-wcag-2-1) zur Erleichterung von Querverweisen zur WCAG-Website.


## Grundsatz 1: Erkennbar   {#principle-perceivable}

[Grundsatz 1: Erkennbar – Informationen und Komponenten der Benutzeroberfläche müssen für die Benutzer so dargestellt sein, dass sie sie erkennen können.](https://www.w3.org/TR/WCAG/#perceivable)

### Textalternativen (1.1)   {#text-alternatives}

[Richtlinie 1.1 Textalternativen: Bieten Sie Textalternativen für nichttextliche Inhalte, damit sie in andere Formate geändert werden, die von bestimmten Personen benötigt werden, wie zum Beispiel Großdruck, Braille, Sprache, Symbole oder einfachere Sprache.](https://www.w3.org/TR/WCAG/#text-alternatives)

### Nichttextlicher Inhalt (1.1.1)   {#non-text-content}

* Erfolgskriterium 1.1.1
* Level A
* Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzern präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen.

#### Zweck: Nichttextlicher Inhalt (1.1.1) {#purpose-non-text-content}

Informationen auf einer Web-Seite können in vielen verschiedenen nichttextlichen Formaten dargestellt werden, wie zum Beispiel als Bilder, Videos, Animationen und Diagramme. Menschen, die blind sind oder deren Sicht erheblich eingeschränkt ist, können nichttextliche Inhalte nicht sehen, doch sie können Textinhalte erfassen, wenn sie ihnen von einem Bildschirmleser vorgelesen oder in haptischer Form auf einem Braille-Anzeigegerät präsentiert werden. Somit kann es durch Bereitstellung von Textalternativen zu Inhalten in grafischem Format ermöglicht werden, dass Menschen, die die grafischen Inhalte nicht sehen können, auf eine gleichwertige Version der Informationen des Inhalts zugreifen können.

Ein nützlicher weiterer Vorteil besteht darin, dass es durch Textalternativen möglich ist, nichttextliche Inhalte durch die Suchmaschinentechnologie zu indizieren.

#### Erfüllen: Nichttextlicher Inhalt (1.1.1)   {#how-to-meet-non-text-content}

Bei statischen Grafiken besteht die Grundanforderung darin, eine gleichwertige Textalternative für die Grafik bereitzustellen. Dies kann im Feld **Alternativtext** erfolgen. Siehe zum Beispiel die Kernkomponente **[Bild](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/image.html)**.

>[!NOTE]
>
>Einige vordefinierte Kernkomponenten, wie **[Karussell](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/carousel.html)**, bieten kein Feld für den **Alternativtext** zum Hinzufügen von alternativen Textbeschreibungen zu einzelnen Bildern, obwohl es das Feld **Beschriftung** (Registerkarte **[Barrierefreiheit](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/carousel.html#accessibility-tab)**) für die gesamte Komponente gibt.
>
>Wenn Sie Versionen davon für Ihre AEM-Instanz implementieren, muss Ihr Entwickler-Team diese Komponenten so konfigurieren, dass das `alt`-Attribut unterstützt wird, damit Autoren es dem Inhalt hinzufügen können (siehe [Hinzufügen von Support für weitere HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

In AEM muss das Feld **Alternativtext** standardmäßig ausgefüllt werden. Wenn das Bild rein dekorativ ist und Alternativtext unnötig wäre, kann die Option **Bild ist dekorativ** aktiviert werden.

#### Erstellen guter Textalternativen {#creating-good-text-alternatives}

Es gibt verschiedene Arten von nichttextlichem Inhalt. Daher hängt der Wert der Textalternative von der Rolle ab, die die Grafik auf der Web-Seite spielt. Nachfolgend sehen Sie einige Faustregeln:

* Textalternativen sollten kurz und bündig sein, aber dennoch klar die wesentlichen Informationen erfassen, die der nichttextliche Inhalt vermittelt.
* Übermäßig lange Beschreibungen (mit mehr als 100 Zeichen) sollten vermieden werden. Wenn für eine Textalternative mehr Details erforderlich sind:
   * Geben Sie im Alternativtext eine kurze Beschreibung an
   * und fügen Sie irgendwo anders auf der entsprechenden Seite oder auf einer anderen Web-Seite eine längere Beschreibung ein. Verlinken Sie auf diese separate Beschreibung, indem Sie das Bild mit einem Link unterlegen oder indem Sie neben das Bild einen Text-Link platzieren.
* Alternativtext sollte keinen Inhalt replizieren, der bereits in Textform auf derselben Seite vorhanden ist. Denken Sie daran, dass viele Bilder Darstellungen von Punkten sind, die bereits der Text einer Seite abdeckt. Somit ist möglicherweise bereits eine Textalternative vorhanden.
* Wenn es sich bei dem nichttextlichen Inhalt um einen Link zu einer anderen Seite oder einem anderen Dokument handelt und kein anderer Text vorhanden ist, der Teil desselben Links ist, dann muss der Alternativtext für das Bild das Ziel des Links angeben und braucht das Bild nicht zu beschreiben.
* Wenn sich der nichttextliche Inhalt in einem Schaltflächenelement befindet und kein Text vorhanden ist, der Teil derselben Schaltfläche ist, dann muss der Alternativtext des Bildes die Funktion der Schaltfläche angeben statt das Bild zu beschreiben.
* Es ist völlig in Ordnung, wenn für ein Bild ein leerer Alternativtext (null) angegeben wird, allerdings nur dann, wenn das Bild keinen Alternativtext erfordert (wenn es sich beispielsweise nur um eine dekorative Grafik handelt) oder der entsprechende Text bereits im Seitentext vorhanden ist.

<!--
The [W3C draft: HTML5 Techniques for providing useful text alternatives](https://dev.w3.org/html5/alt-techniques/) has more details and examples of appropriate alternative text provision for images of different types.
-->

Bestimmte Arten von nichttextlichem Inhalt, für den Textalternativen erforderlich sind:

* Veranschaulichende Fotos:
Hierbei handelt es sich um Bilder von Menschen, Objekten oder Orten. Es ist wichtig, über die Rolle des Fotos auf der Seite nachzudenken, und es wird allgemein empfohlen, den Bildinhalt zu beschreiben, da die unterstützende Technologie den Elementtyp ankündigt (z. B. `graphic` oder `image`). Es kann die Klarheit erhöhen, `screenshot` oder `illustration` in den alternativen Textbeschreibungen zu verwenden, dies hängt jedoch vom Kontext ab. Konsistenz ist ein wichtiger Faktor. Eine Entscheidung sollte für ein gesamtes Autoren-Team getroffen werden und für das gesamte Kundenerlebnis gelten.
* Symbole: Hierbei handelt es sich um kleine Piktogramme (Grafiken), die bestimmte Informationen vermitteln. Sie müssen durchgängig auf einer Seite und Site verwendet werden. Alle Instanzen des Symbols auf einer Seite oder Site sollten dieselbe kurze und knappe Textalternative aufweisen, es sei denn, dass dadurch eine unnötige Verdoppelung von bereits vorhandenem Text erzeugt würde.
* Diagramme: Normalerweise werden dadurch numerische Daten dargestellt. So könnte als eine Möglichkeit zur Bereitstellung von Alternativtext eine kurze Zusammenfassung der im Diagramm gezeigten Haupt-Trends eingefügt werden. Fall nötig, können Sie eine detailliertere Textbeschreibung im Feld **Beschreibung** auf der Registerkarte **Erweiterte Bildeigenschaften** einfügen. Außerdem könnten Sie die Quelldaten an anderer Stelle auf der Seite oder Site als Tabelle zur Verfügung stellen.
* Karten, Diagramme, Flussdiagramme: Stellen Sie bei Grafiken mit räumlichen Daten (z. B. zur Unterstützung der Beschreibung von Beziehungen zwischen Objekten oder einem Prozess) sicher, dass die Schlüsselbotschaft im Textformat bereitgestellt wird und dass diese Textinformationen in der Nähe jedes zugeordneten Datenpunkts positioniert sind. Bei Karten ist die Bereitstellung eines Volltextäquivalents wahrscheinlich nicht praktikabel, aber wenn die Karte bereitgestellt wird, um den Weg zu einer bestimmten Position zu erleichtern, kann der Alternativtext des Kartenbildes kurz *Karte von X* angeben und dann Anweisungen für diese Position im Text an einer anderen Stelle auf der Seite oder über das Feld **Beschreibung** auf der Registerkarte **Erweitert** der Komponente **Bild** geben.
* CAPTCHAs: Ein CAPTCHA ist ein *vollautomatischer öffentlicher Turing-Test zur Unterscheidung zwischen Computern und Menschen*. Es handelt sich um eine Sicherheitsprüfung auf Web-Seiten, um Menschen von schädlicher Software zu unterscheiden, die allerdings die Barrierefreiheit einschränken kann. Sie besteht aus Bildern, bei denen Benutzer beschreiben sollen, was sie sehen, um den Sicherheitstest zu bestehen. Die Bereitstellung einer Textalternative für das Bild ist offensichtlich nicht möglich; daher müssen Sie alternative nichtgrafische Lösungen in Betracht ziehen. Das W3C bietet eine Reihe von Vorschlägen wie. Diese Ansätze haben jedoch sowohl Vor- als auch Nachteile.
   * Logik-Puzzles
   * Audio statt Bilder
   * Eingeschränkte Benutzerkonten und Spam-Filter
* Hintergrundbilder: Diese werden anhand von Cascading Style Sheets (CSS) statt HTML erstellt. Dies bedeutet, dass es nicht möglich ist, einen Wert für Alternativtext anzugeben. Daher sollten Hintergrundbilder keine wichtigen textlichen Informationen enthalten. Falls sie es doch tun, müssen diese Informationen auch im Text der Seite vorhanden sein. Es ist jedoch wichtig, dass ein alternativer Hintergrund angezeigt wird, wenn das Bild nicht angezeigt werden kann.

>[!NOTE]
>
>Es sollte ein Mindestmaß an Kontrast zwischen dem Hintergrund- und dem Vordergrundtext vorhanden sein; weitere Details hierzu finden Sie unter [Kontrast (Minimum) (1.4.3)](#contrast-minimum).

#### Weitere Informationen: Nichttextlicher Inhalt (1.1.1)   {#more-information-non-text-content}

* [Erfolgskriterien 1.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content.html)
* [Erfolgskriterien 1.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#non-text-content)
* [W3C-Erklärung und Alternativen zu CAPTCHAs](https://www.w3.org/TR/turingtest/)

<!--
* [W3C: HTML5 Techniques for providing useful text alternatives (draft)](https://dev.w3.org/html5/alt-techniques/)
-->

### Zeitbasierte Medien (1.2)   {#time-based-media}

[Richtlinie 1.2 Zeitbasierte Medien: Bereitstellung von Alternativen für zeitbasierte Medien.](https://www.w3.org/TR/WCAG/#time-based-media)

Diese Richtlinie behandelt Web-Inhalte, die *zeitbasiert* sind. Es handelt sich um Inhalte, die der Benutzer abspielen kann (wie Video, Audio und animierte Inhalte) und die entweder vorher aufgezeichnet wurden oder als Live-Stream verfügbar sind.

### Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#audio-only-and-video-only-prerecorded}

* Erfolgskriterium 1.2.1
* Stufe A
* Nur-Audio und Nur-Video (aufgezeichnet): Für aufgezeichnete Nur-Audio und Nur-Video-Medien gilt Folgendes, außer wenn das Audio oder Video eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist:
   * Aufgezeichnetes Nur-Audio: Eine Alternative für zeitbasierte Medien wird bereitgestellt, die gleichwertige Informationen für aufgezeichnete Nur-Audio-Inhalte darstellt.
   * Aufgezeichnetes Nur-Video: Es wird entweder eine Alternative für zeitbasierte Medien oder ein Audio-Track bereitgestellt, die/der gleichwertige Informationen für aufgezeichnete Nur-Video-Inhalte darstellt.

#### Zweck: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#purpose-audio-only-and-video-only-prerecorded}

Für folgende Personen kann der barrierefreie Zugang für Video und Audio eingeschränkt sein:

* Personen mit eingeschränktem Sehvermögen, wenn es keinen Soundtrack gibt oder wenn der Soundtrack nicht ausreicht, um sie über die Vorgänge im Video oder in der Animation zu informieren;
* Personen mit eingeschränktem Hörvermögen oder gehörlose Personen, die den Soundtrack nicht hören können.
* Personen, die den Soundtrack zwar hören können, doch den gesprochenen Inhalt nicht verstehen (weil er beispielsweise in einer Sprache aufgezeichnet ist, die sie nicht verstehen).

Video oder Audio kann auch für Personen unzugänglich sein, die Browser oder Geräte verwenden, die die Wiedergabe von Inhalt in bestimmten Medienformaten wie zum Beispiel Adobe Flash nicht unterstützen.

Wenn diese Informationen in einem anderen Format bereitgestellt werden, wie zum Beispiel als Text (oder Audio für Video ohne Audio), können die Informationen für die Personen barrierefrei zugänglich sein, die nicht auf den ursprünglichen Inhalt zugreifen können

#### Erfüllen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#how-to-meet-audio-only-and-video-only-prerecorded}

* Wenn es sich bei dem Inhalt um aufgezeichnetes Audio ohne Video (wie zum Beispiel einen Podcast) handelt:
   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einem Texttranskript des Audioinhalts bereit. Das Transkript sollte eine HTML-Seite mit einer Textentsprechung aller gesprochenen und wichtigen nicht gesprochenen Inhalte sein und den Sprecher, eine Beschreibung der Szenerie, sprachliche Ausdrücke sowie eine Beschreibung anderer wichtiger Audioinhalte angeben.
* Wenn es sich bei dem Inhalt um eine Animation oder ein aufgezeichnetes Video ohne Audio handelt:
   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einer entsprechenden Textbeschreibung der Informationen im Video bereit.
   * Es kann auch eine entsprechende Audiobeschreibung in einem häufig verwendeten Audioformat wie MP3 sein.

>[!NOTE]
>
>Wenn der Audio- oder Videoinhalt als Alternative zu Inhalten bereitgestellt wird, die bereits in einem anderen Format auf derselben Web-Seite vorhanden sind, ist möglicherweise keine zusätzliche Alternative erforderlich.
>
>Die Richtlinien [Grundlegendes zu WCAG 1.2.1](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html) enthalten weitere Informationen.

Das Einfügen von Multimedia auf Ihren AEM-Web-Seiten entspricht in etwa dem Einfügen eines Bildes. Da Multimedia jedoch weit mehr ist als ein Standbild, gibt es eine Vielzahl von verschiedenen Einstellungen und Optionen zur Steuerung, wie die Multimedia-Inhalte abgespielt werden.

>[!NOTE]
>
>Wenn Sie Multimedia mit informativem Inhalt verwenden, müssen Sie auch Links zu Alternativen erstellen. Beispielsweise müssen Sie zum Hinzufügen eines Texttranskripts eine HTML-Seite für die Anzeige des Transkripts erstellen und dann neben oder unter dem Audioinhalt einen Link hinzufügen.

#### Weitere Informationen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#more-information-audio-only-and-video-only-prerecorded}

* [Erfolgskriterien 1.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-only-and-video-only-prerecorded.html)
* [Erfolgskriterien 1.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-only-and-video-only-prerecorded)

### Untertitel (aufgezeichnet) (1.2.2) {#captions-prerecorded}

* Erfolgskriterium 1.2.2
* Stufe A
* Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Untertitel (aufgezeichnet) (1.2.2) {#purpose-captions-prerecorded}

Gehörlose oder schwerhörige Menschen können Audioinhalte gar nicht oder nur schwer verstehen. Untertitel sind Textentsprechungen für gesprochene und nicht gesprochene Audioinhalte; sie werden im Video zum richtigen Zeitpunkt auf dem Bildschirm angezeigt. Sie ermöglichen es Menschen, die das Audio nicht hören können, zu verstehen, was vor sich geht.

#### Erfüllen: Untertitel (aufgezeichnet) (1.2.2) {#how-to-meet-captions-prerecorded}

Es gibt zwei Arten von Untertiteln:

* Offen: Immer sichtbar, wenn das Video abgespielt wird
* Geschlossen: Benutzer können die Untertitel ein- oder ausschalten

Verwenden Sie möglichst geschlossene Untertitel, da Benutzer so wählen können, ob die Untertitel angezeigt werden.

Für geschlossene Untertitel müssen Sie eine synchronisierte Untertiteldatei in einem entsprechenden Format (wie [SMIL](https://www.w3.org/AudioVideo/)) erstellen und zusammen mit der Videodatei bereitstellen. (Details dazu, wie dieser Vorgang ausgeführt wird, sind im Rahmen dieses Leitfadens nicht möglich, doch wir haben Ihnen Links zu einigen Tutorials unter [Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2)](#more-information-captions-prerecorded) zusammengestellt.) Stellen Sie sicher, dass Sie eine Notiz bereitstellen oder die Untertitelfunktion im Video-Player aktivieren, damit Benutzer wissen, dass Untertitel für das Video verfügbar sind.

Wenn Sie offene Untertitel verwenden müssen, betten Sie den Text im Videotrack ein. Dies erreichen Sie mithilfe von Programmen zur Videobearbeitung, die die Überlagerung von Untertiteln im Video ermöglichen.

#### Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2) {#more-information-captions-prerecorded}

* [Erfolgskriterien 1.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded.html)
* [Erfolgskriterien 1.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#captions-prerecorded)

<!--
* [W3C: Synchronized Multimedia](https://www.w3.org/AudioVideo/)
* [Captions, Transcripts, and Audio Descriptions - by WebAIM](https://webaim.org/techniques/captions/)
-->

### Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#audio-description-or-media-alternative-prerecorded}

* Erfolgskriterium 1.2.3
* Stufe A
* Audiobeschreibung oder Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien oder eine Audiobeschreibung des aufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#purpose-audio-description-or-media-alternative-prerecorded}

Blinde Menschen oder Menschen mit eingeschränktem Sehvermögen haben keinen Zugang zu Informationen in einem Video oder einer Animation, wenn diese nur visuell vermittelt werden oder wenn der Soundtrack nicht genügend Informationen bietet, damit sie verstehen können, was visuell gezeigt wird.

#### Erfüllen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-prerecorded}

Es gibt zwei Ansätze zur Erfüllung dieses Erfolgskriteriums. Beide sind akzeptabel:

1. Hinzufügen einer weiteren Audiobeschreibung für den Videoinhalt. Hierzu gibt es drei verschiedene Möglichkeiten:
   * Fügen Sie in Pausen im vorhandenen Dialog Informationen zu den Änderungen der Szene ein, die nicht als Teil des vorhandenen Audiotracks präsentiert werden:
   * Stellen Sie einen neuen, zusätzlichen und optionalen Audio-Track bereit, der den ursprünglichen Soundtrack und zudem weitere Audioinformationen zu den Änderungen in der Szene enthält.
      * Dadurch können Benutzer zwischen dem vorhandenen Audio-Track (der *keine* Audiobeschreibung enthält) und dem neuen Audio-Track (*mit* einer Audiobeschreibung) wechseln.
      * Dadurch wird verhindert, dass Benutzer, die die zusätzliche Beschreibung nicht benötigen, gestört werden.
   * Erstellen Sie eine zweite Version des Videoinhalts, um erweiterte Audiobeschreibungen zu ermöglichen. Dies verringert die Schwierigkeiten, die sich durch Einfügen von detaillierten Audiobeschreibungen in Lücken zwischen dem vorhandenen Dialog ergeben, weil das Audio und Video an passenden Stellen unterbrochen werden muss. Als Ergebnis kann eine viel längere Audiobeschreibung gegeben werden, bevor die Aktion erneut startet. Wie im vorigen Beispiel wird dies am besten als optionaler eigener Audio-Track bereitgestellt, um eine Störung der Benutzer zu verhindern, die keine zusätzliche Beschreibung benötigen.
1. Stellen Sie ein Text-Transkript bereit, das eine angemessene Textentsprechung der Audio- und Bildelemente des Videos oder der Animation ist. Dies sollte gegebenenfalls einen Hinweis darauf enthalten, wer spricht, eine Beschreibung des Umfelds, alle visuell dargestellten Ereignisse oder Informationen und stimmliche Äußerungen. Abhängig von der Länge können Sie das Transkript auf derselben Seite wie das Video oder die Animation einfügen, oder auch auf einer separaten Seite. In diesem Fall müssen Sie einen Link zu dem Transkript neben dem Video oder der Animation bereitstellen.

Genaue Details zur Erstellung von Audiobeschreibungen für Video würden den Rahmen dieses Leitfadens sprengen. Die Erstellung von Audiobeschreibungen können zeitaufwendig sein, doch andere Adobe-Produkte helfen Ihnen bei diesen Aufgaben.

#### Weitere Informationen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#more-information-audio-description-or-media-alternative-prerecorded}

* [Erfolgskriterien 1.2.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-or-media-alternative-prerecorded.html)
* [Erfolgskriterien 1.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-or-media-alternative-prerecorded)

<!--
* [Adobe Encore](https://www.adobe.com/products/encore.html) - a DVD authoring software tool
-->

### Untertitel (live) (1.2.4)     {#captions-live}

* Erfolgskriterium 1.2.4
* Level AA
* Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Untertitel (Live) (1.2.4)   {#purpose-captions-live}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Untertitel (aufgezeichnet)](#captions-prerecorded) insofern, als es Zugangsbarrieren behandelt, die gehörlose oder schwerhörige Menschen erfahren. Der Unterschied besteht darin, dass dieses Erfolgskriterium Live-Präsentationen wie Webcasts behandelt.

#### Erfüllen: Untertitel (Live) (1.2.4) {#how-to-meet-captions-live}

Befolgen Sie die Anleitungen, die oben unter [Untertitel (aufgezeichnet)](#captions-prerecorded) genannt wurden. Da die Medien live übermittelt werden, muss die Bereitstellung so schnell wie möglich erfolgen und sofort auf das reagieren, was passiert. Daher sollten Sie Tools für die Echtzeit-Untertitelung oder für Speech-to-Text in Erwägung ziehen.

Detaillierte Anweisungen dazu würden den Rahmen dieses Dokuments sprengen, doch in den folgenden Ressourcen finden Sie nützliche Informationen:

* [WebAIM: Echtzeit-Untertitelung](https://www.webaim.org/techniques/captions/realtime.php)

* [AccessComputing-Projekt (University of Washington): Können Untertitel automatisch über die Spracherkennung erstellt werden?](https://www.washington.edu/accesscomputing/can-captions-be-generated-automatically-using-speech-recognition)

#### Weitere Informationen: Untertitel (Live) (1.2.4)   {#more-information-captions-live}

* [Erfolgskriterien 1.2.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/captions-live.html)
* [Erfolgskriterien 1.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#captions-live)

### Audiobeschreibung (aufgezeichnet) (1.2.5) {#audio-description-prerecorded}

* Erfolgskriterium 1.2.5
* Level AA
* Audiobeschreibung (aufgezeichnet): Audiobeschreibungen werden für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Audiobeschreibung (aufgezeichnet) (1.2.5) {#purpose-audio-description-prerecorded}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium für [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-prerecorded), mit dem Unterschied, dass Autoren eine wesentlich detailliertere Audiobeschreibung verfassen müssen, um Level AA zu erfüllen.

#### Erfüllen: Audiobeschreibung (aufgezeichnet) (1.2.5) {#how-to-meet-audio-description-prerecorded}

Befolgen Sie die Anweisungen für [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-prerecorded).

#### Weitere Informationen: Audiobeschreibung (aufgezeichnet) (1.2.5) {#more-information-audio-description-prerecorded}

* [Erfolgskriterien 1.2.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-description-prerecorded.html)
* [Erfolgskriterien 1.2.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-description-prerecorded)

### Anpassbar (1.3)  {#adaptable}

[Richtlinie 1.3 Anpassbar: Erstellen von Inhalten, die auf verschiedene Arten präsentiert werden können (zum Beispiel mit einfacherem Layout) ohne Informationen oder die Struktur zu verlieren.](https://www.w3.org/TR/WCAG/#adaptable)

Diese Richtlinie behandelt die Anforderungen zur Unterstützung folgender Personen:

* Personen, die möglicherweise nicht in der Lage sind, auf Informationen zuzugreifen, wie sie von einem Autor in der Standardpräsentation dieses Inhalts präsentiert werden (z. B. ein mehrspaltiges Layout oder eine Seite mit starkem Einsatz von Farbe und/oder Bildern).

* Personen, die eine Nur-Audio-Darstellung oder alternative visuelle Darstellung wie Großdruck oder hohen Kontrast verwenden wollen.

### Informationen und Beziehungen (1.3.1)     {#info-and-relationships}

* Erfolgskriterium 1.3.1
* Stufe A
* Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmatisch festgelegt werden oder sind im Text verfügbar.

#### Zweck: Informationen und Beziehungen (1.3.1)   {#purpose-info-and-relationships}

Viele Hilfstechnologien, die von Menschen mit Behinderungen genutzt werden, sind auf strukturelle Informationen angewiesen, damit Inhalte effektiv angezeigt oder *verstanden* werden können. Diese Strukturinformationen können in Form von Seitenüberschriften, Tabellenzeilen und Spaltenüberschriften sowie Listentypen vorliegen. Beispielsweise könnte ein Benutzer mit einem Bildschirmleser von Überschrift zu Überschrift durch eine Seite navigieren. Wenn Seiteninhalte jedoch nur über visuelles Styling statt das zugrundeliegende HTML strukturiert wurden, stehen den Hilfstechnologien keine Strukturinformationen zur Verfügung und deren Fähigkeit zur Unterstützung eines leichteren Browsings ist erheblich eingeschränkt.

Dieses Erfolgskriterium besteht, um sicherzustellen, dass derartige Strukturinformationen über HTML bereitgestellt werden, damit die Browser und Hilfstechnologien auf die Informationen zugreifen und davon profitieren können.

#### Erfüllen: Informationen und Beziehungen (1.3.1)   {#how-to-meet-info-and-relationships}

Mit AEM ist es einfach, semantisch sinnvolle Web-Inhalte mit den entsprechenden HTML-Elementen aufzubauen. Öffnen Sie Ihren Seiteninhalt im RTE (eine Textkomponente) und geben Sie im Menü **Paraformat** (Absatzsymbol) das entsprechende Strukturelement (zum Beispiel Absatz, Überschrift usw.) an.

Sie können sicherstellen, dass Ihre Web-Seiten die geeignete Struktur erhalten, indem Sie gegebenenfalls die folgenden Elemente verwenden:

* **Überschriften:** Sofern Sie die Funktionen für Barrierefreiheit des RTE aktiviert haben, bietet AEM drei Ebenen für Seitenüberschriften. Sie können diese verwenden, um Abschnitte und Unterabschnitte des Inhalts zu identifizieren. Überschrift 1 ist die höchste Überschriftenstufe und Stufe 3 die niedrigste. Der Systemadministrator kann das System so konfigurieren, dass mehr Überschriftenstufen verwendet werden können.

* **Listen**: Mit HTML können Sie drei verschiedene Arten von Listen angeben:
   * Das Element `<ul>` wird für *nicht geordnete* Listen (Aufzählungslisten) verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet. Verwenden Sie in RTE das Symbol **Aufzählungsliste**.
   * Das Element `<ol>` wird für *nummerierte* Listen verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet. Verwenden Sie in RTE das Symbol **Nummerierte Liste**.

   Wenn Sie Inhalt in einen Listentyp ändern möchten, markieren Sie den entsprechenden Text und wählen Sie den jeweiligen Listentyp aus. Wie im obigen Beispiel, in dem gezeigt wird, wie Absatztext eingegeben wird, werden die entsprechenden Listenelemente automatisch zum HTML-Code hinzugefügt.

   Im Vollbildmodus sind die einzelnen Symbole **Aufzählungsliste** und **Nummerierte Liste** sichtbar. Wenn Sie sich nicht im Vollbildmodus befinden, sind die beiden Optionen hinter dem einzelnen Symbol **Listen** verfügbar.

* **Tabellen**: Datentabellen müssen mit HTML-Tabellenelementen gekennzeichnet sein:
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
   >Diese Elemente und Attribute sind standardmäßig nicht direkt verfügbar, doch der Systemadministrator kann Support für diese Werte im Dialogfeld **Tabelleneigenschaften** hinzufügen (siehe [Hinzufügen von Support für zusätzliche HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes).

   So öffnen Sie das Dialogfeld **Tabelle**, in dem Sie die Registerkarte **Tabelleneigenschaften** auswählen können:

   * Definieren Sie eine entsprechende **Beschriftung**.
   * Im Idealfall entfernen Sie alle Standardwerte für **Breite**, **Höhe**, **Rand**, **Zellauffüllung**, **Zellabstand**, da diese Eigenschaften in einem globalen Stylesheet festgelegt werden können.

   Sie können dann die **Zellen-Eigenschaften** verwenden, um festzulegen, ob es sich bei der Zelle um eine Daten- oder Kopfzeilenzelle handelt:

* **Hervorhebung**: Verwenden Sie das Element `<strong>` oder `<em>`, um die Hervorhebung vorzunehmen. Verwenden Sie keine Überschriften zum Hervorheben von Text in Absätzen.
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


* **Komplexe Datentabellen**: In einigen Fällen, in denen komplexe Tabellen mit zwei oder mehr Überschriftebenen vorhanden sind, reicht das normale Dialogfeld „Tabelleneigenschaften“ nicht aus, um alle benötigten Strukturinformationen anzugeben. Für diese Arten von komplexen Tabellen müssen direkte Beziehungen zwischen den Überschriften und deren dazugehörigen Zellen erstellt werden. Zu diesem Zweck werden die Attribute **Überschrift** und **ID** verwendet.

   >[!NOTE]
   >
   >Das ID-Attribut ist in Standardinstallationen nicht verfügbar. Es kann durch Konfigurieren von HTML-Regeln und des Serialisierungsprogramms im RTE aktiviert werden.

   Beispielsweise werden in der Tabelle unten Überschriften und IDs zugeordnet, um eine programmatische Verbindung für Benutzer von Hilfstechnologien herzustellen.

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

   Um dies in AEM zu erreichen, müssen Sie das Markup hinzufügen, indem Sie direkt den Modus zur Bearbeitung des Quell-Codes verwenden.

   >[!NOTE]
   >
   >Diese Funktion ist in einer Standardinstallation nicht sofort verfügbar. Dazu ist die Konfiguration des RTE, der HTML-Regeln und des Serialisierungsprogramms erforderlich.

#### Weitere Informationen: Informationen und Beziehungen (1.3.1) {#more-information-info-and-relationships}

* [Erfolgskriterien 1.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/info-and-relationships.html)
* [Erfolgskriterien 1.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#info-and-relationships)

### Bedeutungstragende Reihenfolge (1.3.2) {#meaningful-sequence}

* Erfolgskriterium 1.3.2
* Stufe A
* Bedeutungstragende Reihenfolge: Wenn die Reihenfolge, in der Inhalte präsentiert werden, sich auf deren Bedeutung auswirkt, kann die korrekte Leseabfolge durch Software bestimmt werden.

#### Zweck: Bedeutungstragende Reihenfolge (1.3.2) {#purpose-meaningful-sequence}

Mit diesem Erfolgskriterium soll es einem Benutzeragenten ermöglicht werden, eine alternative Darstellung des Inhalts bereitzustellen und gleichzeitig die Lesesequenz beizubehalten, die zum Verständnis des Inhalts erforderlich ist. Es muss möglich sein, mindestens eine Inhaltsreihenfolge programmgesteuert festzulegen. Inhalte, die dieses Erfolgskriterium nicht erfüllen, können Benutzer verwirren, wenn die Hilfstechnologie den Inhalt in der falschen Reihenfolge liest oder wenn alternative Stylesheets oder andere Formatierungsänderungen angewendet werden.

#### Erfüllen: Bedeutungstragende Reihenfolge (1.3.2) {#how-to-meet-meaningful-sequence}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 1.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence).

#### Weitere Informationen: Bedeutungstragende Reihenfolge (1.3.2) {#more-information-meaningful-sequence}

* [Erfolgskriterien 1.3.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/meaningful-sequence.html)
* [Erfolgskriterien 1.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#meaningful-sequence)

### Sensorische Eigenschaften (1.3.3)     {#sensory-characteristics}

* Erfolgskriterium 1.3.3
* Stufe A
* Sensorische Eigenschaften: Anweisungen, die zum Verstehen und Bedienen von Inhalt verfügbar sind, beziehen sich nicht nur auf sensorische Eigenschaften der Komponenten wie Form, Größe, visuelle Position, Ausrichtung oder Klang.

#### Zweck: Sensorische Eigenschaften (1.3.3)   {#purpose-sensory-characteristics}

Entwickler konzentrieren sich bei der Präsentation von Informationen oft auf visuelle Design-Funktionen wie Farbe, Form, Textstil oder die absolute oder relative Position eines Inhaltselements. Dabei kann es sich um sehr leistungsstarke Design-Techniken zur Informationsübermittlung handeln (die die allgemeine Zugänglichkeit für sehende Benutzer mit kognitiven Zugänglichkeitsanforderungen verbessern), aber blinde oder sehbehinderte Personen können möglicherweise nicht auf Informationen zugreifen, die eine visuelle Identifizierung von Attributen wie Position, Farbe oder Form erfordern.

Entsprechend sind Informationen, für die zwischen verschiedenen Klängen (z. B. Inhalten, die von einer Frau oder einem Mann gesprochen werden) unterschieden werden muss, für Menschen mit eingeschränktem Hörvermögen nicht verfügbar, wenn sie nicht in Textalternativen für den Audioinhalt umgesetzt wurden.

>[!NOTE]
>
>Die Anforderungen, die sich auf die Alternativen für Farben beziehen, finden Sie unter [Verwendung von Farbe](#use-of-color).

#### Erfüllen: Sensorische Eigenschaften (1.3.3)   {#how-to-meet-sensory-characteristics}

Stellen Sie sicher, dass Informationen, die sich auf visuelle Eigenschaften von Seiteninhalten beziehen, auch in alternativen Formaten präsentiert werden.

* Verlassen Sie sich nicht auf die visuelle Position, um Informationen bereitzustellen. Wenn Sie beispielsweise Benutzer auf ein Menü rechts auf der Seite verweisen möchten, über das sie auf weitere Informationen zugreifen können, beziehen Sie sich nicht auf *das Menü rechts*, sondern geben Sie den Namen für das Menü an (zum Beispiel über eine Überschrift) und beziehen Sie sich im Text auf diesen Namen.
* Verlassen Sie sich nicht auf den Textstil (z. B. fett oder kursiv gedruckter Text) als einzige Methode zur Vermittlung von Informationen.

>[!NOTE]
>
>Die Verwendung beschreibender Begriffe ist dann akzeptabel, wenn diese auch in einem nicht visuellen Kontext eine Bedeutung haben. So ist z. B. die Verwendung von *oben* und *unten* in der Regel akzeptabel, da diese jeweils Inhalt vor und nach einem bestimmten Inhaltselement implizieren. Dabei bleibt die Bedeutung auch erhalten, wenn der Inhalt laut ausgesprochen wird.

#### Weitere Informationen – Sensorische Eigenschaften (1.3.3) {#more-information-sensory-characteristics}

* [Erfolgskriterien 1.3.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/sensory-characteristics.html)
* [Erfolgskriterien 1.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#sensory-characteristics)

### Unterscheidbar (1.4)  {#distinguishable}

[Richtlinie 1.4 Unterscheidbar: Erleichtern Sie den Benutzern das Sehen und Hören von Inhalt einschließlich der Unterscheidung von Vorder- und Hintergrund.](https://www.w3.org/TR/WCAG/#distinguishable)

### Verwendung von Farbe (1.4.1)     {#use-of-color}

* Erfolgskriterium 1.4.1
* Stufe A
* Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel eingesetzt, um Informationen zu vermitteln, eine Aktion zu kennzeichnen, eine Antwort einzuholen oder ein visuelles Element zu unterscheiden.

>[!NOTE]
>
>Dieses Erfolgskriterium bezieht sich speziell auf die Farbwahrnehmung. Andere Wahrnehmungsformen werden unter [Anpassbar (1.3)](#adaptable) behandelt. Hierzu gehören der programmtechnische Zugriff auf Farbe und andere visuelle Darstellungskodierungen.

#### Zweck - Verwendung von Farbe (1.4.1)   {#purpose-use-of-color}

Farbe bietet sichtbar eine effektive Möglichkeit, die Ästhetik von Web-Seiten zu verbessern, und kann auch die Vermittlung von Informationen unterstützen. Es gibt jedoch eine Vielzahl visueller Beeinträchtigungen, von Farbenblindheit bis zur Beeinträchtigung der Farbwahrnehmung, die dazu führt, dass manche Menschen zwischen bestimmten Farben nicht unterscheiden können. Aus diesem Grund ist die farbliche Kodierung ein unzuverlässiges Mittel für die Bereitstellung von Informationen.

Jemand mit einer Rot-Grün-Sehschwäche kann z. B. nicht zwischen Grünschattierungen und Rotschattierungen unterscheiden. Er sieht möglicherweise beide Farben als eine dritte Farbe (z. B. braun) und kann daher nicht zwischen rot, grün und braun unterscheiden.

Außerdem können Menschen, die einen reinen Textbrowser, monochrome Anzeigen oder einen Schwarzweiß-Ausdruck auf Papier nutzen, keine Farben wahrnehmen.

Eine weitere Überlegung ist der *ausgewählte* Status für ein Schnittstellenelement (z. B. Registerkarten, Umschalttasten usw.), der auf andere Weise als nur mit Farbe und über eine visuelle Darstellung hinaus vermittelt werden muss. Für solche Elemente ist die zusätzliche Verwendung von Mustern, Formen und programmatischen Informationen hilfreich, wenn ein vollständig integratives Kundenerlebnis erstellt werden soll, das nicht auf einem bestimmten Sinn beruht.

#### Erfüllen - Verwendung von Farbe (1.4.1)   {#how-to-meet-use-of-color}

Immer wenn Farbe verwendet wird, um Informationen zu vermitteln, müssen Sie sicherstellen, dass die verfügbaren Informationen auch verfügbar sind, wenn die Farbe nicht sichtbar ist.

Stellen Sie z. B. sicher, dass die durch die Farbe vermittelte Information auch explizit im Text enthalten ist.

Wenn Farbe als Hinweis für Informationen verwendet wird, sollten Sie für einen zusätzlichen visuellen Hinweis sorgen, z. B. durch Ändern des Stils (z. B. fett, kursiv) oder der Schriftart. So können auch Personen mit Seh- oder Farbschwäche die Informationen erkennen. Man darf sich jedoch nicht vollständig auf diese Maßnahmen verlassen, da sie für Menschen, die die Seite überhaupt nicht sehen können, keine Hilfe bieten. Daher ist es (manchmal) nützlich, versteckten Text bereitzustellen oder programmatische Lösungen wie die [Accessible Rich Internet Applications (ARIA) Suite von Web-Standards](https://www.w3.org/WAI/standards-guidelines/aria/) zu verwenden, um diese Informationen an nicht sehende Benutzer zu übermitteln.

#### Weitere Informationen – Verwendung von Farbe (1.4.1) {#more-information-use-of-color}

* [Erfolgskriterien 1.4.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
* [Erfolgskriterien 1.4.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#use-of-color)

### Audio-Steuerelement (1.4.2) {#audio-control}

* Erfolgskriterium 1.4.2
* Stufe A
* Audio-Steuerung: Wenn Audioinhalt auf einer Web-Seite automatisch für mehr als 3 Sekunden abgespielt wird, gibt es entweder einen Mechanismus, um die Wiedergabe zu pausieren oder zu beenden, oder es gibt einen Mechanismus, um die Lautstärke unabhängig von der allgemeinen Systemlautstärke zu regeln.

#### Zweck: Audio-Steuerelement (1.4.2) {#purpose-audio-control}

Personen, die Bildschirmlesehilfen verwenden, können die Sprachausgabe eventuell nur schwer hören, wenn gleichzeitig anderes Audio abgespielt wird. Diese Schwierigkeit wird noch verstärkt, wenn die Sprachausgabe der Bildschirmlesehilfe Software-basiert ist (was aktuell meistens der Fall ist) und über denselben Lautstärkeregler wie der Ton gesteuert wird. Darüber hinaus können einige Menschen mit kognitiven Behinderungen und Menschen mit Neurodivergenz schallempfindlich sein. Diese Personen werden jede Unfähigkeit, den Lautstärkepegel von Audioinhalten zu ändern, als ziemlich störend empfinden.

Daher ist es wichtig, dass der Benutzer den Hintergrundton ausschalten kann.

>[!NOTE]
>
>Die Lautstärkesteuerung schließt die Möglichkeit ein, die Lautstärke auf null zu reduzieren.

#### Erfüllen: Audio-Steuerelement (1.4.2) {#how-to-meet-audio-control}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 1.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-control).

#### Weitere Informationen: Audio-Steuerelement (1.4.2) {#more-information-audio-control}

* [Erfolgskriterien 1.4.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/audio-control.html)
* [Erfolgskriterien 1.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#audio-control)

### Kontrast (Minimum) (1.4.3)   {#contrast-minimum}

* Erfolgskriterium 1.4.3
* Level AA
* Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1 mit folgenden Ausnahmen:
   * Großer Text: Großer Text und Bilder von großem Text haben ein Kontrastverhältnis von mindestens 3:1.
   * Beiläufig: Für Text oder Textbilder, die Teil einer inaktiven Komponente der Benutzeroberfläche sind, die [reine Dekoration](https://www.w3.org/TR/WCAG/#dfn-pure-decoration) darstellen, die für niemanden sichtbar sind oder die Teil eines Bildes sind, das signifikanten anderen visuellen Inhalt enthält, ist kein Kontrast erforderlich.
   * Firmenschriftzüge: Für Text, der Teil eines Logos oder eines Markennamens ist, gibt es keine Kontrastanforderungen.

   >[!NOTE]
   >
   >Unter [Grundlegendes zu Nicht-Text-Kontrast](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html) finden Sie weitere Informationen, um sicherzustellen, dass Autoren von Inhalten die zusätzlichen Anforderungen an Nicht-Text-Elemente verstehen (einschließlich Symbolen, Oberflächenelementen usw.).

#### Zweck - Kontrast (Minimum) (1.4.3)   {#purpose-contrast-minimum}

Manche Menschen mit einem beeinträchtigten Sehvermögen können nicht zwischen bestimmten Farbpaaren mit geringem Kontrast unterscheiden. Die Barrierefreiheit ist für diese Menschen in folgenden Situationen eingeschränkt:

* Wenn zwischen dem Text und der Hintergrundfarbe nur wenig Kontrast besteht.
* Wenn die Farbkodierung des Textes (wie Link-Text und Text ohne Link) für die Unterscheidung der Informationen wichtig ist.

>[!NOTE]
>
>Text, der ausschließlich zu dekorativen Zwecken verwendet wird, ist von diesem Erfolgskriterium nicht betroffen.

#### Erfüllen - Kontrast (Minimum) (1.4.3)   {#how-to-meet-contrast-minimum}

Stellen Sie sicher, dass zwischen dem Text und der Hintergrundfarbe ausreichend Kontrast besteht. Das Kontrastverhältnis hängt von der Größe und dem Schriftschnitt des betroffenen Textes ab:

* Für Text mit einer Größe von weniger als 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis zwischen Text/Bildern mit Text und dem Hintergrund mindestens 4,5:1 betragen.
* Für Text mit einer Größe von mindestens 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis mindestens 3:1 betragen.
* Falls der Hintergrund gemustert ist, sollte der Hintergrund um alle Texte abgestuft sein, damit das Verhältnis von 4,5:1 oder 3:1 beibehalten wird.

>[!NOTE]
>
>Beachten Sie, dass Schriftarten sich hinsichtlich der Darstellung der entsprechenden PT-/PX-/EM-Größe unterscheiden können.
>
>Es wird empfohlen, bei der Auswahl der geeigneten Schriftarten und der Größe für Web-Inhalte in Bezug auf Lesbarkeit und Benutzerfreundlichkeit den gesunden Menschenverstand walten zu lassen.

>[!NOTE]
>
>Die folgenden Sites können bei der Umrechnung in andere Einheiten helfen:
>
>* [Px-zu-Em-Umrechner – Omni](https://www.omnicalculator.com/conversion/px-to-em)
>* [Schriftgrößenkonvertierung: pixel-point-em-rem-percent](https://websemantics.uk/tools/font-size-conversion-pixel-point-em-rem-percent/)
>* [PMtoEM.com: PX-to-EM-Konvertierung einfach gemacht](http://pxtoem.com)


Verwenden Sie ein Farbkontrast-Tool, um das Kontrastverhältnis zu prüfen, z. B. den [Color Contrast Analyser von Paciello Group](https://www.paciellogroup.com/resources/contrast-analyser.html) oder den [Color Contrast Checker von WebAIM](https://www.webaim.org/resources/contrastchecker/). Mit diesen Tools können Sie Farbpaare prüfen und erkennen mögliche Kontrastprobleme.

Wenn es für Sie nicht so wichtig ist, das Aussehen Ihrer Seite festzulegen, können Sie alternativ keine Farben für den Hintergrund und den Text im Vordergrund festlegen. Dann brauchen Sie den Kontrast nicht zu prüfen, weil der Browser des Benutzers die Farbe für den Text und den Hintergrund ermittelt.

Falls es nicht möglich ist, die geforderten Kontraststufen zu erfüllen, müssen Sie einen Link zu einer alternativen, identischen Version der Seite bereitstellen (auf der keine Farbkontrastprobleme vorliegen) oder dem Benutzer die Anpassung des Kontrasts des Farbschemas der Seite an seine eigenen Anforderungen ermöglichen.

#### Weitere Informationen - Kontrast (Minimum) (1.4.3)   {#more-information-contrast-minimum}

* [Erfolgskriterien 1.4.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html)
* [Erfolgskriterien 1.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#contrast-minimum)

### Textgröße ändern (1.4.4) {#resize-text}

* Erfolgskriterium 1.4.4
* Stufe A
* Textgröße ändern: Mit Ausnahme von Untertiteln und Bildern eines Textes kann Text ohne Hilfstechnologien um bis zu 200 Prozent geändert werden, ohne dass dabei Inhalt oder Funktionalität verloren geht.

#### Zweck: Textgröße ändern (1.4.4) {#purpose-resize-text}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass visuell gerenderter Text, einschließlich textbasierter Steuerelemente (Textzeichen, die so angezeigt wurden, dass sie sichtbar sind, [im Vergleich zu Textzeichen, die noch in Datenform vorliegen, wie z. B. ASCII]), erfolgreich so skaliert werden kann, dass er von Benutzern mit leichten Sehbehinderungen direkt gelesen werden kann, ohne dass der Einsatz von Hilfstechnologien wie z. B. einer Bildschirmlupe erforderlich ist. Benutzer können von der Skalierung aller Inhalte auf der Web-Seite profitieren, aber Text ist am wichtigsten.

#### Erfüllen: Textgröße ändern (1.4.4) {#how-to-meet-resize-text}

Neben den Richtlinien unter [Erfolgskriterien 1.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#resize-text) können Sie Inhaltsautoren dazu ermutigen, flüssige, flexible Breiten und Höhen in ihren Seiten-Designs und Schriftgrößen (z. B. responsives Webdesign) zu verwenden, damit die Leser die Textgröße ändern können.

#### Weitere Informationen: Textgröße ändern (1.4.4) {#more-information-resize-text}

* [Erfolgskriterien 1.4.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/resize-text.html)
* [Erfolgskriterien 1.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#resize-text)

### Bilder von Text (1.4.5)   {#images-of-text}

* Erfolgskriterium 1.4.5
* Level AA
* Bilder von Text: Falls die verwendeten Technologien die visuelle Präsentation realisieren können, wird für die Vermittlung von Informationen Text verwendet – keine Bilder von Text. Dabei gelten folgende Ausnahmen:
   * Anpassbar: Das Bild des Texts kann visuell an die Anforderungen des Benutzers angepasst werden.
   * Erforderlich: Eine bestimmte Präsentation von Text ist für die zu vermittelnden Informationen erforderlich.

>[!NOTE]
>
>Firmenschriftzüge (Texte, die Teil eines Logos oder eines Markennamens sind) werden als erforderlich angesehen.

#### Zweck - Bilder von Text (1.4.5)   {#purpose-images-of-text}

Bilder von Text werden häufig verwendet, wenn ein bestimmter Textstil bevorzugt wird. Z. B. bei einem Firmenschriftzug oder wenn der Text aus einer anderen Quelle generiert wurde (z. B. ein eingescanntes Papierdokument). Im Vergleich mit in HTML dargestelltem Text, dessen Stil mittels CSS festgelegt wird, fehlt Bildern von Text jedoch die Flexibilität, die Größe oder das Erscheinungsbild zu ändern, was für Menschen mit Beeinträchtigungen der Sehfähigkeit oder mit Leseschwäche erforderlich sein kann.

#### Erfüllen - Bilder von Text (1.4.5)   {#how-to-meet-images-of-text}

Wenn Bilder von Text verwendet werden müssen, nutzen Sie CSS, um die Bilder von Text in HTML durch einen identischen Text zu ersetzen, damit der Text in einer anpassbaren Version verfügbar ist. Ein Beispiel hierfür finden Sie unter [C30: Verwenden von CSS, um Text durch Bilder von Text zu ersetzen und ein Steuerelement zum Umschalten auf der Benutzeroberfläche bereitzustellen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Weitere Informationen - Bilder von Text (1.4.5)   {#more-information-images-of-text}

* [Erfolgskriterien 1.4.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/images-of-text.html)
* [Erfolgskriterien 1.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#images-of-text)

## Grundsatz 2: Bedienbar   {#principle-operable}

[Grundsatz 2: Bedienbar – Komponenten der Benutzerschnittstelle und der Navigation müssen bedienbar sein.](https://www.w3.org/TR/WCAG/#operable)

### Per Tastatur zugänglich (2.1) {#keyboard-accessible}

[Richtlinie 2.1 Per Tastatur zugänglich: Sorgen Sie dafür, dass alle Funktionalitäten per Tastatur zugänglich sind.](https://www.w3.org/TR/WCAG/#keyboard-accessible)

Dadurch wird sichergestellt, dass Benutzer über eine Tastatur auf alle Funktionen zugreifen können.

### Tastatur (2.1.1)   {#keyboard}

* Erfolgskriterium 2.1.1
* Stufe A
* Tastatur: Alle Funktionalitäten des Inhalts sind durch eine Tastaturschnittstelle bedienbar, ohne dass eine bestimmte Zeiteinteilung für einzelne Tastenanschläge erforderlich ist, außer wenn die zugrunde liegende Funktion Eingaben verlangt, die vom Pfad der Bewegung des Benutzers und nicht nur von den Endpunkten abhängig sind.

#### Zweck: Tastatur (2.1.1) {#purpose-keyboard}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Inhalte nach Möglichkeit über eine Tastatur- oder eine Tastaturschnittstelle (sodass eine alternative Tastatur verwendet werden kann) bedient werden können. Wenn Inhalte über eine Tastatur oder eine alternative Tastatur bedient werden können, können sie von Personen ohne Sehvermögen (die keine Geräte wie Mäuse verwenden können, für die eine Auge-Hand-Koordination erforderlich ist) sowie von Personen bedient werden, die alternative Tastaturen oder Eingabegeräte verwenden müssen, die als Tastaturemulatoren agieren. Zu den Tastaturemulatoren gehören Spracheingabe-Software, Sip-and-Puff-Software, Bildschirmtastaturen, Scansoftware und eine Vielzahl von Hilfstechnologien und alternative Tastaturen. Personen mit Sehschwäche haben möglicherweise auch Schwierigkeiten, einen Zeiger zu verfolgen, und finden die Verwendung von Software viel einfacher (oder nur möglich), wenn sie diese über die Tastatur steuern können.

#### Erfüllen: Tastatur (2.1.1) {#how-to-meet-keyboard}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#keyboard).

#### Weitere Informationen: Tastatur (2.1.1) {#more-information-keyboard}

* [Erfolgskriterien 2.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Erfolgskriterien 2.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#keyboard)

### Keine Tastaturfalle (2.1.2)  {#no-keyboard-trap}

* Erfolgskriterium 2.1.2
* Stufe A
* Keine Tastaturfalle: Wenn der Tastaturfokus durch eine Tastaturschnittstelle auf einen Bestandteil der Seite bewegt werden kann, kann der Fokus von diesem Bestandteil weg bewegt werden, indem man nur die Tastaturschnittstelle verwendet. Wenn man dazu mehr als nicht modifizierte Pfeil- oder Tabulatortasten oder andere übliche Ausstiegsmethoden verwenden muss, wird der Benutzer über die Methode zum Bewegen des Fokus informiert.

#### Zweck: Keine Tastaturfalle (2.1.2) {#purpose-no-keyboard-trap}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass der Inhalt den Tastaturfokus nicht in Unterabschnitten des Inhalts einer Web-Seite *einfängt*. Dies ist ein häufig auftretendes Problem, wenn mehrere Formate innerhalb einer Seite kombiniert und mithilfe von Plug-ins oder eingebetteten Programmen wiedergegeben werden.

Es kann vorkommen, dass die Funktionalität der Web-Seite den Fokus auf einen Unterabschnitt des Inhalts beschränkt (z. B. ein modales Dialogfeld). In solchen Fällen sollten Sie eine Methode bereitstellen, mit der ein Benutzer aus diesem Inhaltsunterabschnitt aussteigen kann (z. B. schließt die Esc-Taste oder eine Schließen-Schaltfläche das modale Dialogfeld).

#### Erfüllen: Keine Tastaturfalle (2.1.2) {#how-to-meet-no-keyboard-trap}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap).

#### Weitere Informationen: Keine Tastaturfalle (2.1.2) {#more-information-no-keyboard-trap}

* [Erfolgskriterien 2.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/no-keyboard-trap.html)
* [Erfolgskriterien 2.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#no-keyboard-trap)

### Ausreichend Zeit (2.2) {#enough-time}

[Richtlinie 2.2 Ausreichend Zeit: Geben Sie den Benutzern ausreichend Zeit, Inhalte zu lesen und zu benutzen.](https://www.w3.org/TR/WCAG/#enough-time)

Dadurch wird sichergestellt, dass die Benutzer genügend Zeit zum Lesen und Handeln haben.

### Zeiteinteilung anpassbar (2.2.1) {#timing-adjustable}

* Erfolgskriterium 2.2.1
* Stufe A
* Tastatur: Geben Sie den Benutzern ausreichend Zeit, Inhalte zu lesen und zu verwenden.

#### Zweck: Zeiteinteilung anpassbar (2.2.1) {#purpose-timing-adjustable}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Nutzer mit Behinderungen nach Möglichkeit ausreichend Zeit zur Interaktion mit Web-Inhalten erhalten. Personen mit Behinderungen wie Blindheit, Sehschwäche, Beeinträchtigung der Geschicklichkeit und kognitiven Einschränkungen benötigen unter Umständen mehr Zeit, um Inhalte zu lesen oder Funktionen wie das Ausfüllen von Online-Formularen auszuführen. Wenn Web-Funktionen zeitabhängig sind, ist es für einige Benutzer schwierig, die erforderliche Aktion auszuführen, bevor ein Zeitlimit eintritt. Dadurch kann der Zugriff auf den Service für sie unzugänglich werden. Die Entwicklung von nicht zeitabhängigen Funktionen hilft Personen mit Behinderungen dabei, diese Funktionen auszuführen. Die Bereitstellung von Optionen zur Deaktivierung von Zeitlimits, zur Anpassung der Länge von Zeitlimits oder zur Anforderung von mehr Zeit, bevor ein Zeitlimit eintritt, hilft denjenigen Benutzern, die mehr Zeit als erwartet benötigen, Aufgaben erfolgreich zu erledigen. Diese Optionen werden in der Reihenfolge aufgelistet, die für den Benutzer am hilfreichsten ist. Das Deaktivieren von Zeitlimits ist besser als das Anpassen der Länge von Zeitlimits, was wiederum besser ist, als mehr Zeit vor dem Eintreten eines Zeitlimits anzufordern.

#### Erfüllen: Zeiteinteilung anpassbar (2.2.1) {#how-to-meet-timing-adjustable}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable).

#### Weitere Informationen: Zeiteinteilung anpassbar (2.2.1) {#more-information-timing-adjustable}

* [Erfolgskriterien 2.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/timing-adjustable.html)
* [Erfolgskriterien 2.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#timing-adjustable)

### Pausieren, Beenden, Ausblenden (2.2.2)     {#pause-stop-hide}

* Erfolgskriterium 2.2.2
* Stufe A
* Pausieren, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln:
   * Sich bewegend, blinkend, scrollend: Für alle sich bewegenden, blinkenden oder scrollenden Informationen, die (a) automatisch starten, (b) länger als 5 Sekunden dauern und (c) parallel zu anderen Inhalten dargestellt werden, muss es einen Mechanismus für den Benutzer geben, um diese zu pausieren, zu beenden oder auszublenden, sofern die Bewegung, das Blinken oder das Scrollen nicht Teil einer Aktivität ist, bei der dies erforderlich ist.
   * Automatische Aktualisierung: Für alle sich automatisch aktualisierenden Informationen, die (a) automatisch starten und (b) parallel mit anderen Inhalten dargestellt werden, muss es einen Mechanismus geben, damit der Benutzer die Aktualisierung pausieren, beenden oder ausblenden oder die Häufigkeit der Aktualisierung kontrollieren kann, sofern die automatische Aktualisierung nicht Teil einer Aktivität ist, bei der dies erforderlich ist.

Folgendes sollte beachtet werden:

1. Die Anforderungen für flackernden oder blinkenden Inhalt finden Sie unter „Gestalten Sie Inhalte nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen“ (2.3).
1. Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Web-Seite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhalt, der regelmäßig durch Software aktualisiert wird oder der auf den Benutzer-Agenten gestreamt wird, darf keine Informationen bewahren oder darstellen, die zwischen dem Initiieren des Anhaltens und dem Fortsetzen der Darstellung generiert oder empfangen wurden, da dies technisch möglicherweise nicht machbar ist und in vielen Situationen irreführend sein kann.
1. Eine Animation, die Teil einer Ladephase oder eines ähnlichen Szenarios ist, kann als erforderlich erachtet werden, wenn während dieser Phase keine Benutzerinteraktion möglich ist und wenn das Fehlen einer Fortschrittsanzeige Benutzer verwirren oder zu der Annahme verleiten kann, der Inhalt sei eingefroren oder beschädigt.

#### Zweck - Pausieren, Beenden, Ausblenden (2.2.2)   {#purpose-pause-stop-hide}

Manche Benutzer empfinden Inhalte, die sich bewegen, als störend oder sogar körperlich schmerzhaft und haben Schwierigkeiten sich auf andere Bereiche der Seite zu konzentrieren. Darüber hinaus sind solche Inhalte für Menschen schwierig, die beim Lesen Probleme haben, bewegtem Text zu folgen.

#### Erfüllen - Pausieren, Beenden, Ausblenden (2.2.2)   {#how-to-meet-pause-stop-hide}

Abhängig von der Art des Inhalts können Sie beim Erstellen von Web-Seiten mit sich bewegendem, blitzendem oder blinkendem Inhalt die folgenden Empfehlungen beachten:

* Bieten Sie die Möglichkeit, das Scrollen des Inhalts anzuhalten, um Benutzern Zeit zum Lesen zu geben. Zum Beispiel Nachrichten-Ticker, automatisch aktualisierter Text und Bildkarusselle, die automatisch weiterbewegt werden.
* Stellen Sie sicher, dass blinkende Inhalte maximal fünf Sekunden lang blinken.
* Nutzen Sie Technologien, mit denen die Anzeige von bewegten oder blinkenden Inhalten im Browser deaktiviert werden kann. Beispielsweise Dateien im GIF (Graphics Interchange Format)- oder APNG (Animated Portable Network Graphics)-Format.
* Bieten Sie auf der Web-Seite ein Formularsteuerelement an, über das Benutzer sämtliche bewegte oder blinkenden Inhalte auf der Seite deaktivieren können.
* Wenn einer der oben genannten Punkte nicht möglich ist, geben Sie einen Link zu einer Seite an, die alle Inhalte ohne Bewegung und Blinken zeigt.

#### Weitere Informationen - Pausieren, Beenden, Ausblenden (2.2.2)   {#more-information-pause-stop-hide}

* [Erfolgskriterium 2.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html)
* [Erfolgskriterium 2.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#pause-stop-hide)

### Anfälle (2.3) {#seizures-and-physcial-reactions}

[Richtlinie 2.3 Anfälle: Gestalten Sie Inhalt nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen oder körperlichen Reaktionen führen.](https://www.w3.org/TR/WCAG/#seizures-and-physical-reactions)

### Grenzwert von maximal dreimaligem Blitzen (2.3.1)   {#three-flashes-or-below-threshold}

* Erfolgskriterium 2.3.1
* Stufe A
* Grenzwert von maximal dreimaligem Blitzen: Web-Seiten dürfen nichts enthalten, das in einem Zeitraum von einer Sekunde öfter als dreimal blitzt oder dessen Blitz unterhalb der allgemeinen Grenzwerte für Blitze und rote Blitze liegt.

>[!NOTE]
>
>Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Web-Seite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG/#cc5).

#### Zweck – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bestimmten Fällen können blitzende Inhalte photosensitive Anfälle auslösen. Dieses Erfolgskriterium ermöglicht Benutzern den Zugriff und die Nutzung des gesamten Inhalts ohne Beeinträchtigung durch blitzende Inhalte.

#### Erfüllen - Grenzwert von maximal dreimaligem Blitzen (2.3.1)   {#how-to-meet-three-flashes-or-below-threshold}

Stellen Sie sicher, dass die folgenden Techniken zur Anwendung kommen:

* Stellen Sie sicher, dass Komponenten in einem Zeitraum von einer Sekunde nicht öfter als dreimal blitzen.
* Falls die obige Bedingung nicht erfüllt werden kann, platzieren Sie den blitzenden Inhalt in einem *kleinen sicheren Bereich* in Pixel auf dem Bildschirm. Dieser Bereich wird anhand einer komplexen Formel berechnet, die unter [G176: Blitzende Bereiche ausreichend klein halten](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176) behandelt wird. Diese Technik sollte ausschließlich dann angewendet werden, wenn ein blitzender Inhalt *unbedingt* erforderlich ist.

#### Weitere Informationen – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Erfolgskriterium 2.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/three-flashes-or-below-threshold.html)
* [Erfolgskriterium 2.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#three-flashes-or-below-threshold)

### Navigierbar (2.4) {#navigable}

[Richtlinie 2.4 Navigierbar: Stellen Sie Mittel zur Verfügung, um Benutzer dabei zu unterstützen, zu navigieren, Inhalte zu finden und zu bestimmen, wo sie sich befinden.](https://www.w3.org/TR/WCAG/#navigable)

Hiermit wird sichergestellt, dass der Inhalt für Benutzer einfach und unkompliziert zu navigieren ist.

### Blöcke umgehen (2.4.1) {#bypass-blocks}

* Erfolgskriterium 2.4.1
* Stufe A
* Blöcke umgehen: Es gibt einen Mechanismus, um Inhaltsblöcke zu umgehen, die auf verschiedenen Web-Seiten wiederholt werden.

#### Zweck: Blöcke umgehen (2.4.1) {#purpose-bypass-blocks}

Mit diesem Erfolgskriterium sollen Personen, die nacheinander durch Inhalte navigieren, direkteren Zugriff auf den primären Inhalt der Web-Seite erhalten. Web-Seiten und Programme enthalten oft Inhalte, die auf anderen Seiten oder Bildschirmen angezeigt werden. Beispiele für wiederholte Inhaltsblöcke sind unter anderem Navigations-Links, Überschriftengrafiken, Menüs und Werberahmen. Kleine wiederholte Abschnitte wie einzelne Wörter, Wortgruppen oder einzelne Links werden für die Zwecke dieser Bestimmung nicht als Blöcke angesehen.

#### Erfüllen: Blöcke umgehen (2.4.1) {#how-to-meet-bypass-blocks}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.4.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks).

#### Weitere Informationen: Blöcke umgehen (2.4.1) {#more-information-bypass-blocks}

* [Erfolgskriterien 2.4.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/bypass-blocks.html)
* [Erfolgskriterien 2.4.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#bypass-blocks)

### Seite mit Titel versehen (2.4.2)     {#page-titled}

* Erfolgskriterium 2.4.2
* Stufe A
* Seite mit Titel versehen: Web-Seiten haben einen Titel, der das Thema oder den Zweck beschreibt

#### Zweck - Seite mit Titel versehen (2.4.2)   {#purpose-page-titled}

Dieses Erfolgskriterium ist für alle Benutzer hilfreich - unabhängig von etwaigen Beeinträchtigungen - um schnell den Inhalt einer Web-Seite zu ermitteln, ohne die Seite vollständig zu lesen. Dies ist insbesondere dann nützlich, wenn mehrere Web-Seiten in Browsertabs geöffnet sind, da der Seitentitel auf den Tabs angezeigt wird, was die Seiten schnell auffindbar macht.

#### Erfüllen - Seite mit Titel versehen (2.4.2)   {#how-to-meet-page-titled}

Wenn Sie im AEM eine neue HTML-Seite erstellen, können Sie den Seitentitel angeben. Stellen Sie sicher, dass der Titel den Inhalt und den Zweck der Seite (insbesondere alle einzigartigen Aspekte) so beschreibt, dass Besucher schnell feststellen können, ob der Inhalt für ihre Anforderungen relevant ist oder nicht.

Sie können während der Bearbeitung einer Seite auch den Seitentitel ändern. Öffnen Sie dazu **Seiteninformationen** > **Eigenschaften**.

#### Weitere Informationen – Seite mit Titel versehen (2.4.2) {#more-information-page-titled}

* [Erfolgskriterium 2.4.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/page-titled.html)
* [Erfolgskriterium 2.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#page-titled)

### Fokus-Reihenfolge (2.4.3) {#focus-order}

* Erfolgskriterium 2.4.3
* Stufe A
* Fokus-Reihenfolge: Wenn eine Web-Seite der Reihe nach navigiert werden kann und die Reihenfolge der Navigation die Bedeutung oder Bedienung beeinflusst, erhalten fokussierbare Komponenten den Fokus in einer Reihenfolge, die Bedeutung und Bedienbarkeit aufrecht erhält.

#### Zweck: Fokus-Reihenfolge (2.4.3) {#purpose-focus-order}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Benutzer bei der sequenziellen Navigation durch Inhalte auf Informationen in einer Reihenfolge stoßen, die der Bedeutung des Inhalts entspricht und über die Tastatur bedient werden kann. Dadurch wird die Verwirrung verringert, da Benutzer ein konsistentes mentales Modell des Inhalts bilden können. Es kann verschiedene Reihenfolgen geben, die logische Beziehungen im Inhalt widerspiegeln. Das Durchlaufen von Komponenten in einem Online-Formular, das aus mehreren Feldern und/oder Schritten besteht, spiegelt beispielsweise die logischen Beziehungen im Inhalt wider.

#### Erfüllen: Fokus-Reihenfolge (2.4.3) {#how-to-meet-focus-order}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-order).

#### Weitere Informationen: Fokus-Reihenfolge (2.4.3) {#more-information-focus-order}

* [Erfolgskriterien 2.4.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/focus-order.html)
* [Erfolgskriterien 2.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-order)

### Link-Zweck (im Kontext) (2.4.4)     {#link-purpose-in-context}

* Erfolgskriterium 2.4.4
* Stufe A
* Link-Zweck (im Kontext): Der Zweck jedes Links kann allein durch den Link-Text oder durch den Link-Text zusammen mit dem programmatisch festgelegten Link-Kontext bestimmt werden. Ausgenommen sind Fälle, in denen der Zweck des Links für Benutzer generell mehrdeutig ist.

#### Zweck - Link-Zweck (im Kontext) (2.4.4)   {#purpose-link-purpose-in-context}

Unabhängig von etwaigen Beeinträchtigungen ist es für alle Benutzer von entscheidender Bedeutung, dass durch einen passenden Link-Text klar erkenntlich ist wohin ein Link führt. Dies erleichtert Benutzern die Entscheidung, ob sie einem Link folgen möchten oder nicht. Für sehende Benutzer ist ein aussagekräftiger Link-Text ausgesprochen nützlich, wenn sich auf einer Seite mehrere Links befinden (vor allem, wenn eine Seite sehr viel Text enthält), da ein aussagekräftiger Link-Text einen deutlicheren Hinweis auf die Funktion der Zielseite liefert. Benutzer einiger Hilfstechnologien, die eine Liste aller Links auf einer Seite generieren können, können den Link-Text außerhalb des Kontextes leichter verstehen, wenn dieser Link-Text sowohl eindeutig als auch informativ ist. Sehende Personen mit kognitiven Behinderungen können jedoch verwirrt werden, wenn ein Link nicht genügend Informationen enthält, um genau zu beschreiben, wohin der Link sie führen wird.

#### Erfüllen - Link-Zweck (im Kontext) (2.4.4)   {#how-to-meet-link-purpose-in-context}

Stellen Sie vor allem sicher, dass der Link-Text den Zweck eines Links eindeutig beschreibt.

* Schlechtes Beispiel:
   * Text: Einzelheiten zu unseren Abendkursen im Herbst 2010 finden Sie hier.
   * Grund: Es geht nicht deutlich und unmissverständlich hervor wohin der Link führt.
* Gutes Beispiel:
   * Text: Abendkurse im Herbst 2010 – Details.
   * Grund: Durch eine kleine Anpassung des Textes und der Position des Linkelements lässt sich der Link-Text verbessern:

Links sollten auf den Seiten eine konsistente Bezeichnung erhalten. Dies gilt insbesondere für Navigationsleisten. Wenn ein Link zu einer bestimmten Seite z. B. auf einer Seite **Publikationen** heißt, dann sollte er auch auf allen anderen Seiten denselben Namen erhalten.

Zum Zeitpunkt des Verfassens dieses Artikels gibt es einige Probleme im Zusammenhang mit der Verwendung von Titelattributen, um sicherzustellen, dass ähnliche Links, die auf einer Seite präsentiert werden, eindeutige Informationen über das Ziel liefern (z. B. verweist „Weitere Information“ oft auf eine Reihe verschiedener Ziele):

* Im Titelattribut enthaltener Text steht im Allgemeinen nur Mausbenutzern als Tooltip-Popup zur Verfügung und kann weder über die Tastatur noch von Mobilgeräten konsistent aufgerufen werden.
* Die Sprachausgabe kann Title-Attribute auslesen, diese Funktion ist jedoch nicht unbedingt standardmäßig aktiviert. Daher ist es für Benutzer eventuell nicht ersichtlich, dass ein Title-Attribut vorhanden ist.
* Es ist schwierig das Erscheinungsbild des Titeltextes anzupassen, weshalb es für manche Menschen schwierig oder unmöglich sein kann, diesen zu lesen.

Das Title-Attribut kann also genutzt werden, um zusätzlichen Kontext zu einem Link bereitzustellen, Sie sollten aber diese Einschränkungen bedenken und es daher nicht als Alternative für einen geeigneten Link-Text nutzen.

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

Auch wenn es angeraten ist, einen Link-Text bereitzustellen, der den Zweck des Links verdeutlicht, ohne zusätzlichen Kontext zu benötigen, gibt es Fälle, in denen dies nicht möglich ist. Links ohne Kontext können in den folgenden Fällen verwendet werden. HTML-Beispiele hierzu finden Sie unter [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context).

* Wenn der Link-Text zu einer Liste eng zusammenhängender Links gehört und das den Link umgebende Listenelement ausreichend Kontext liefert.
* Wenn der Zweck eines Links aus dem *vorangehenden* (nicht dem nachfolgenden) Text des Absatzes klar hervorgeht.
* Wenn der Link in einer Datentabelle enthalten ist und der Zweck über die zugehörigen Überschriften deutlich erkennbar ist.
* Wenn eine Liste mit Links in einem Satz Überschriften enthalten ist und die Überschrift einen ausreichenden Kontext liefert.
* Wenn eine Liste mit Links in einem geschachtelten Link enthalten ist und das übergeordnete Listenelement des geschachtelten Links einen ausreichenden Kontext liefert.

In einigen Fällen, in denen sich mehrere Links auf einer Seite befinden (von denen jeder das Ziel des Links durch komplexe, aber erforderliche Details angibt), kann es sinnvoll sein, eine alternative Version der Web-Seite anzubieten, die denselben Inhalt anzeigt, auf der der Link-Text jedoch weniger ausführlich ist.

Alternativ können Skripts verwendet werden. Dabei wird im Link selbst ein minimaler Text bereitgestellt. Bei der Aktivierung des entsprechenden Steuerelements im oberen Bereich der Seite wird der Link-Text jedoch *erweitert* und es werden mehr Details angezeigt. Einen ähnlichen Ansatz bietet die Verwendung von CSS, um den vollständigen Link für sehende Benutzer *auszublenden*, ihn für Benutzer der Sprachausgabe jedoch auszugeben. Dies überschreitet jedoch den Rahmen dieses Dokuments; weitere Informationen hierzu finden Sie jedoch unter [Weitere Informationen – Link-Zweck (im Kontext) (2.4.4)](#more-information-link-purpose-in-context).

#### Weitere Informationen – Link-Zweck (im Kontext) (2.4.4) {#more-information-link-purpose-in-context}

* [Erfolgskriterium 2.4.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context.html)
* [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#link-purpose-in-context)

<!--
* [C7: Using CSS to hide a portion of the link text](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)
-->

### Verschiedene Methoden (2.4.5) {#multiple-ways}

* Erfolgskriterium 2.4.5
* Level AA
* Verschiedene Methoden: Es gibt mehr als eine Methode, um eine Web-Seite innerhalb eines Satzes von Web-Seiten zu finden, außer die Web-Seite ist das Ergebnis oder ein Schritt innerhalb eines Prozesses.

#### Zweck: Verschiedene Methoden (2.4.5) {#purpose-multiple-ways}

Mit diesem Erfolgskriterium sollen Benutzer in die Lage versetzt werden, Inhalte so zu finden, dass sie ihren Anforderungen am besten entsprechen. Benutzer finden möglicherweise eine Technik einfacher oder verständlicher als eine andere.

Selbst kleine Websites sollten den Benutzern Orientierungshilfen bieten. Bei einer Website mit drei oder vier Seiten, bei der alle Seiten von der Startseite aus verlinkt sind, kann es ausreichend sein, einfach Links von und zur Startseite bereitzustellen, wobei die Links auf der Startseite auch als Sitemap dienen können.

#### Erfüllen: Verschiedene Methoden (2.4.5) {#how-to-meet-multiple-ways}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways).

#### Weitere Informationen: Verschiedene Methoden (2.4.5) {#more-information-multiple-ways}

* [Erfolgskriterien 2.4.5 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/multiple-ways.html)
* [Erfolgskriterien 2.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#multiple-ways)

### Überschriften und Beschriftungen (2.4.6) {#headings-and-labels}

* Erfolgskriterium 2.4.6
* Level AA
* Überschriften und Beschriftungen: Überschriften und Beschriftungen beschreiben ein Thema oder einen Zweck.

#### Zweck: Überschriften und Beschriftungen (2.4.6) {#purpose-headings-and-labels}

Mit diesem Erfolgskriterium sollen Benutzer verstehen, welche Informationen auf Web-Seiten enthalten sind und wie diese Informationen organisiert sind. Wenn die Überschriften klar und beschreibend sind, können Benutzer die gesuchten Informationen leichter finden und die Beziehungen zwischen verschiedenen Teilen des Inhalts leichter verstehen. Beschreibende Beschriftungen helfen Benutzern, bestimmte Komponenten innerhalb des Inhalts zu identifizieren.

#### Erfüllen: Überschriften und Beschriftungen (2.4.6) {#how-to-meet-headings-and-labels}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.4.6 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels).

#### Weitere Informationen: Überschriften und Beschriftungen (2.4.6) {#more-information-headings-and-labels}

* [Erfolgskriterien 2.4.6 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/headings-and-labels.html)
* [Erfolgskriterien 2.4.6 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#headings-and-labels)

### Fokus sichtbar (2.4.7) {#focus-visible}

* Erfolgskriterium 2.4.7
* Level AA
* Fokus sichtbar: Jede durch die Tastatur bedienbare Benutzerschnittstelle hat einen Bedienmodus, bei dem der Tastaturfokus sichtbar ist.

#### Zweck: Fokus sichtbar (2.4.7) {#purpose-focus-visible}

Mit diesem Erfolgskriterium soll Personen gezeigt werden, welches Element den Tastaturfokus hat.

Eine Person muss wissen können, welches Element unter mehreren Elementen den Tastaturfokus hat. Wenn nur eine Tastatursteuerung auf dem Bildschirm vorhanden ist, wird das Erfolgskriterium erfüllt, da das visuelle Design nur ein Tastatursteuerelement enthält.

Wenn das Erfolgskriterium „Betriebsart“ lautet, werden Plattformen berücksichtigt, auf denen möglicherweise nicht immer ein Fokusindikator angezeigt wird. In den meisten Fällen gibt es nur eine Betriebsart, daher gilt dieses Erfolgskriterium.

#### Erfüllen: Fokus sichtbar (2.4.7) {#how-to-meet-focus-visible}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 2.4.7 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible).

#### Weitere Informationen: Fokus sichtbar (2.4.7) {#more-information-focus-visible}

* [Erfolgskriterien 2.4.7 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/focus-visible.html)
* [Erfolgskriterien 2.4.7 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#focus-visible)

## Grundsatz 3: Verständlich   {#principle-understandable}

[Grundsatz 3: Verständlich – Informationen und die Bedienung der Benutzerschnittstelle müssen verständlich sein.](https://www.w3.org/TR/WCAG/#understandable)

### Machen Sie Inhalt lesbar und verständlich (3.1)   {#make-text-content-readable-and-understandable}

[Richtlinie 3.1 Lesbar: Machen Sie Inhalt lesbar und verständlich.](https://www.w3.org/TR/WCAG/#readable)

### Sprache der Seite (3.1.1)   {#language-of-page}

* Erfolgskriterium 3.1.1
* Stufe A
* Sprache der Seite: Die voreingestellte menschliche Sprache einer Web-Seite kann programmatisch bestimmt werden.

#### Zweck - Sprache der Seite (3.1.1)   {#purpose-language-of-page}

Der Zweck dieses Erfolgskriteriums besteht darin, sicherzustellen, dass Texte und andere linguistische Inhalte fehlerfrei gerendert werden. Für Benutzer der Sprachausgabe stellt dies sicher, dass der Inhalt korrekt ausgesprochen wird, während bei visuellen Browsern die Wahrscheinlichkeit höher ist, dass bestimmte Zeichensätze richtig angezeigt werden.

#### Erfüllen - Sprache der Seite (3.1.1)   {#how-to-meet-language-of-page}

Um dieses Erfolgskriterium zu erfüllen, kann die Standardsprache einer Web-Seite über das Attribut `lang` innerhalb des Elements `<html>` am Anfang der Seite festgelegt werden. Beispiel:

* Wenn eine Seite z. B. in Englisch verfasst ist, sollte das Element `<html>` wie folgt angegeben werden:
   `<html lang = “en”>`

* Wenn eine Seite hingegen als Seite in Spanisch gerendert werden soll, ist folgende Angabe erforderlich:
   `<html lang = “es”>`

Im AEM wird die Standardsprache Ihrer Seite beim Erstellen der Seite festgelegt. Sie kann jedoch beim Bearbeiten der [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) geändert werden.

>[!NOTE]
>
>AEM bietet eine weitere Feinabstimmung für Variationen einer Stammsprache. Zum Beispiel amerikanisches Englisch – en-us, britisches Englisch – en-gb und kanadisches Englisch – en-ca. Dieser Detaillierungsgrad ist für unterstützende Technologien häufig überflüssig, kann jedoch für regionale Unterschiede im Seiteninhalt verwendet werden.

#### Weitere Informationen – Sprache der Seite (3.1.1) {#more-information-language-of-page}

* [Erfolgskriterium 3.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/language-of-page.html)
* [Erfolgskriterium 3.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#language-of-page)
* Die Codes basieren auf ISO 639-1. Eine umfangreichere Liste der Codes für die einzelnen Sprachen finden Sie auf der [W3 Schools-Website](https://www.w3schools.com/tags/ref_language_codes.asp).

### Sprache von Teilen (3.1.2)     {#language-of-parts}

* Erfolgskriterium 3.1.2
* Level AA
* Sprache von Teilen: Die menschliche Sprache aller Abschnitte und Sätze im Inhalt kann programmatisch bestimmt werden. Ausgenommen sind Eigennamen, technische Fachbegriffe, Wörter einer unbestimmten Sprache und Wörter oder Wendungen, die Teil des Jargons des direkt umliegenden Textes sind.

#### Zweck - Sprache von Teilen (3.1.2)   {#purpose-language-of-parts}

Der Zweck dieses Erfolgskriteriums ähnelt dem Zweck des Erfolgskriteriums [Sprache der Seite](#language-of-page). Es gilt jedoch für Web-Seiten, die auf einer Seite Inhalte im mehreren Sprachen enthalten (z. B. in Form von Zitaten oder wenig geläufigen Lehnwörtern).

Seiten, die dieses Erfolgskriterium erfüllen, bieten folgende Möglichkeiten:

* Software für die Braille-Übersetzung kann akzentuierte Zeichen einfügen.
* Bildschirmlesehilfen können Wörter aussprechen, die Sonderzeichen enthalten oder nicht in der auf Seitenebene festgelegten Standardsprache enthalten sind.
* Übersetzungs-Tools wie der Google Übersetzer können Inhalt korrekt von einer Sprache in eine andere übersetzen.

#### Erfüllen - Sprache von Teilen (3.1.2)   {#how-to-meet-language-of-parts}

Mit dem Attribut `lang` können Änderungen der Sprache des Inhalts ermittelt werden. Ein deutschsprachiges Zitat (ISO 639-1-Code „de“) kann z. B. wie folgt angezeigt werden:

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

Um ein span-Element mit der entsprechenden Sprache hinzuzufügen, können Sie Ihren HTML-Code im Bearbeitungsmodus für den Quelltext im RTE manuell bearbeiten, damit er wie oben aussieht. Alternativ kann ein Systemadministrator das `lang`-Attribut im RTE einfügen (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

#### Weitere Informationen – Sprache von Teilen (3.1.2) {#more-information-language-of-parts}

* [Erfolgskriterium 3.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/language-of-parts.html)
* [Erfolgskriterium 3.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#language-of-parts)

### Vorhersehbar (3.2) {#predictable}

[Richtlinie 3.2 Vorhersehbar: Sorgen Sie dafür, dass Web-Seiten vorhersehbar aussehen und funktionieren.](https://www.w3.org/TR/WCAG/#predictable)

Hier geht es darum, sicherzustellen, dass die Web-Seiten in Aussehen und Funktionsweise konsistent sind.

### Bei Fokus (3.2.1) {#on-focus}

* Erfolgskriterium 3.2.1
* Stufe A
* Bei Fokus: Wenn irgendein Bestandteil der Benutzeroberfläche den Fokus erhält, löst dies nicht eine Änderung des Kontextes aus.

#### Zweck: Bei Fokus (3.2.1) {#purpose-on-focus}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass die Funktionalität vorhersehbar ist, wenn Besucher durch ein Dokument navigieren. Keine Komponente, die ein Ereignis auslösen kann, wenn sie den Fokus erhält, darf den Kontext ändern. Beispiele für das Ändern des Kontexts, wenn eine Komponente den Fokus erhält, sind unter anderem:

* Formulare, die automatisch gesendet werden, wenn eine Komponente den Fokus erhält;
* neue Fenster, die gestartet werden, wenn eine Komponente den Fokus erhält;
* der Fokus wird auf eine andere Komponente geändert, wenn diese Komponente den Fokus erhält.

Der Fokus kann entweder über die Tastatur (z. B. Tippen auf ein Steuerelement) oder die Maus (z. B. Klicken auf ein Textfeld) auf ein Steuerelement verschoben werden. Wenn Sie die Maus über ein Steuerelement bewegen, wird der Fokus nur verschoben, wenn die Skripterstellung dieses Verhalten implementiert. Beachten Sie, dass bei einigen Steuerelementtypen durch Klicken auf ein Steuerelement auch das Steuerelement (z. B. die Schaltfläche) aktiviert werden kann, was wiederum eine Änderung des Kontexts auslösen kann.

#### Erfüllen: Bei Fokus (3.2.1) {#how-to-meet-on-focus}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-focus).

#### Weitere Informationen: Bei Fokus (3.2.1) {#more-information-on-focus}

* [Erfolgskriterien 3.2.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/on-focus.html)
* [Erfolgskriterien 3.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-focus)

### Bei Eingabe (3.2.2) {#on-input}

* Erfolgskriterium 3.2.2
* Stufe A
* Bei Eingabe: Die Änderung der Einstellung irgendeines Bestandteils der Benutzerschnittstelle führt nicht automatisch zur Änderung des Kontextes, außer der Benutzer wurde vor Benutzung des Bestandteils auf das Verhalten hingewiesen.

#### Zweck: Bei Eingabe (3.2.2) {#purpose-on-input}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass die Eingabe von Daten oder die Auswahl eines Formularsteuerelements vorhersehbare Auswirkungen hat. Durch Ändern der Einstellung einer Benutzeroberflächenkomponente werden einige Aspekte des Steuerelements geändert, die bestehen bleiben, wenn der Benutzer nicht mehr mit ihr interagiert. Wenn Sie also ein Kontrollkästchen aktivieren, Text in ein Textfeld eingeben oder die ausgewählte Option in einem Listensteuerelement ändern, wird die Einstellung geändert, das Aktivieren eines Links oder einer Schaltfläche jedoch nicht. Änderungen im Kontext können Benutzer verwirren, die die Änderung nicht leicht wahrnehmen oder durch Änderungen leicht abgelenkt werden. Änderungen des Kontexts sind nur dann angemessen, wenn klar ist, dass eine solche Änderung als Reaktion auf die Aktion des Benutzers erfolgt.

#### Erfüllen: Bei Eingabe (3.2.2) {#how-to-meet-on-input}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-input).

#### Weitere Informationen: Bei Eingabe (3.2.2) {#more-information-on-input}

* [Erfolgskriterien 3.2.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html)
* [Erfolgskriterien 3.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#on-input)

### Konsistente Navigation (3.2.3) {#consistent-navigation}

* Erfolgskriterium 3.2.3
* Level AA
* Konsistente Navigation: Navigationsmechanismen, die auf mehreren Web-Seiten innerhalb eines Satzes von Web-Seiten wiederholt werden, treten jedes Mal, wenn sie wiederholt werden, in der gleichen relativen Reihenfolge auf, außer eine Änderung wird durch den Benutzer ausgelöst.

#### Zweck: Konsistente Navigation (3.2.3) {#purpose-consistent-navigation}

Mit diesem Erfolgskriterium soll zur Verwendung einer einheitlichen Darstellung und eines einheitlichen Layouts für Benutzer motiviert werden, die mit wiederholten Inhalten innerhalb einer Reihe von Web-Seiten interagieren und bestimmte Informationen oder Funktionen mehrmals suchen müssen. Personen mit Sehschwäche, die eine Bildschirmvergrößerung verwenden, um jeweils einen kleinen Teil des Bildschirms anzuzeigen, verwenden häufig visuelle Hinweise und Seitengrenzen, um wiederholte Inhalte schnell zu finden. Die Darstellung wiederholter Inhalte in derselben Reihenfolge ist auch für visuelle Benutzer wichtig, die räumliches Gedächtnis oder visuelle Hinweise innerhalb des Designs verwenden, um wiederholte Inhalte zu lokalisieren.

Beachten Sie, dass die Verwendung des Ausdrucks „gleiche Reihenfolge“ in diesem Abschnitt nicht bedeuten soll, dass Unternavigationsmenüs oder Blöcke der sekundären Navigation oder Seitenstruktur nicht verwendet werden können. Stattdessen soll dieses Erfolgskriterium Benutzern, die mit wiederholten Inhalten auf Web-Seiten interagieren, helfen, den Speicherort des gesuchten Inhalts vorherzusagen und ihn schneller zu finden, wenn sie erneut auf ihn stoßen.

Benutzer können eine Änderung der Reihenfolge einleiten, indem sie adaptive Benutzeragenten verwenden oder Einstellungen festlegen, damit die Informationen auf eine Weise dargestellt werden, die für sie am nützlichsten ist.

#### Erfüllen: Konsistente Navigation (3.2.3) {#how-to-meet-consistent-navigation}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation).

#### Weitere Informationen: Konsistente Navigation (3.2.3) {#more-information-consistent-navigation}

* [Erfolgskriterien 3.2.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/consistent-navigation.html)
* [Erfolgskriterien 3.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-navigation)

### Konsistente Erkennung (3.2.4) {#consistent-identification}

* Erfolgskriterium 3.2.4
* Stufe A
* Konsistente Erkennung: Bestandteile mit der gleichen Funktionalität innerhalb eines Satzes von Web-Seiten werden konsistent erkannt.

#### Zweck: Konsistente Erkennung (3.2.4) {#purpose-consistent-identification}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Funktionskomponenten, die wiederholt auf einer Reihe von Web-Seiten angezeigt werden, konsistent erkannt werden. Eine Strategie, die Benutzer von Bildschirmlesehilfen bei der Nutzung einer Website verwenden, besteht darin, sich stark auf ihre Vertrautheit mit Funktionen zu verlassen, die auf verschiedenen Web-Seiten erscheinen können. Wenn identische Funktionen auf verschiedenen Web-Seiten unterschiedliche Bezeichnungen (oder allgemein einen anderen zugänglichen Namen) haben, ist die Website erheblich schwieriger zu benutzen. Es kann auch verwirrend sein und die kognitive Belastung für Menschen mit kognitiven Einschränkungen erhöhen. Daher hilft eine einheitliche Bezeichnung.

Diese Konsistenz erstreckt sich auch auf Textalternativen. Wenn Symbole oder andere Nicht-Textelemente dieselbe Funktionalität haben, sollten auch ihre Textalternativen konsistent sein.

Wenn eine Web-Seite zwei Komponenten enthält, die beide dieselbe Funktionalität wie eine Komponente auf einer anderen Seite einer Reihe von Web-Seiten haben, müssen alle drei konsistent sein. Daher sind die beiden auf derselben Seite konsistent.

Während es wünschenswert und Best Practice ist, immer innerhalb einer einzelnen Web-Seite konsistent zu sein, behandelt 3.2.4 nur die Konsistenz innerhalb einer Reihe von Web-Seiten, bei denen etwas auf mehr als einer Seite in der Reihe wiederholt wird.

#### Erfüllen: Konsistente Erkennung (3.2.4) {#how-to-meet-consistent-identification}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification).

#### Weitere Informationen: Konsistente Erkennung (3.2.4) {#more-information-consistent-identification}

* [Erfolgskriterien 3.2.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/consistent-identification.html)
* [Erfolgskriterien 3.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#consistent-identification)

### Hilfestellung bei der Eingabe (3.3) {#input-assistance}

[Richtlinie 3.3 Hilfestellung bei der Eingabe: Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren.](https://www.w3.org/TR/WCAG/#input-assistance)

### Fehlerkennung (3.3.1) {#error-identification}

* Erfolgskriterium 3.3.1
* Stufe A
* Fehlererkennung: Wenn ein Eingabefehler automatisch erkannt wird, wird das fehlerhafte Element identifiziert und der Fehler wird dem Benutzer in Textform beschrieben.

#### Zweck: Fehlererkennung (3.3.1) {#purpose-error-identification}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Benutzer wissen, dass ein Fehler aufgetreten ist, und dass sie feststellen können, was falsch ist. Die Fehlermeldung sollte so spezifisch wie möglich sein. Im Falle einer nicht erfolgreichen Formularübermittlung reicht es für einige Benutzer nicht aus, das Formular erneut anzuzeigen und die fehlerhaften Felder anzugeben, um zu erkennen, dass ein Fehler aufgetreten ist. Benutzer von Bildschirmlesehilfen wissen beispielsweise erst dann, dass ein Fehler aufgetreten ist, wenn sie auf einen der Indikatoren stoßen. Sie brechen das Formular möglicherweise ab, bevor sie auf die Fehleranzeige stoßen, da sie der Meinung sind, dass die Seite einfach nicht funktionsfähig ist. Gemäß der Definition in WCAG ist ein [Eingabefehler](https://www.w3.org/TR/WCAG/#dfn-input-error) eine vom Benutzer bereitgestellte Information, die nicht akzeptiert wird. Hierzu gehört Folgendes:

Informationen, die von der Web-Seite benötigt, aber vom Benutzer weggelassen werden, oder Informationen, die vom Benutzer bereitgestellt werden, aber außerhalb des erforderlichen Datenformats oder der zulässigen Werte liegen.
Beispiel:

* Der Benutzer gibt nicht die richtige Abkürzung in die Felder für Bundesstaat, Provinz, Region usw. ein.
* Der Benutzer gibt eine Bundesstaatsabkürzung ein, die kein gültiger Bundesstaat ist.
* Der Benutzer gibt eine nicht vorhandene Postleitzahl ein.
* Der Benutzer gibt ein Geburtsdatum ein, das 2 Jahre in der Zukunft liegt.
* Der Benutzer gibt alphabetische Zeichen oder Klammern in das Telefonnummernfeld ein, das nur Zahlen akzeptiert.
* Der Benutzer gibt ein Gebot ein, das unter dem vorherigen Gebot oder dem Mindestinkrement liegt.

#### Erfüllen: Fehlererkennung (3.3.1) {#how-to-meet-error-identification}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-identification).

#### Weitere Informationen: Fehlererkennung (3.3.1) {#more-information-error-identification}

* [Erfolgskriterien 3.3.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-identification.html)
* [Erfolgskriterien 3.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-identification)

### Beschriftungen oder Anweisungen (3.3.2)   {#labels-or-instructions}

* Erfolgskriterium 3.3.2
* Stufe A
* Beschriftungen oder Anweisungen: Wenn der Inhalt eine Eingabe durch den Benutzer erfordert, werden Beschriftungen oder Anweisungen bereitgestellt.

#### Zweck - Beschriftungen oder Anweisungen (3.3.2)   {#purpose-labels-or-instructions}

Das Bereitstellen von Anweisungen, die Menschen beim Ausfüllen von Formularen unterstützen, bildet einen entscheidenden Bestandteil der bewährten Verfahrenspraxis für eine benutzerfreundliche Oberfläche. Dies ist insbesondere für Menschen mit visuellen oder kognitiven Einschränkungen hilfreich, die das Layout eines Formulars und die Art der in einem bestimmten Formularfeld anzugebenden Daten andernfalls nur schwer nachvollziehen können.

##### Formulare

Im AEM WKND-Demoprojekt wird eine Standardbeschriftung eingefügt, wenn Sie eine Formularkomponente (z. B. ein **Textfeld**) zur Seite hinzufügen. Dieser Standardtitel beruht auf dem Typ der Komponente. Auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds für das Feld können Sie Ihren eigenen Titel angeben. Es ist wichtig, dass Sie sicherstellen, dass Benutzer mithilfe von Beschriftungen leichter nachvollziehen können welche Daten in den einzelnen Formularkomponenten erwartet werden.

Das Feld **Titel** muss für Feldelemente verwendet werden, weil es eine Beschriftung bereitstellt, die für Sprachausgabetechnologien verfügbar ist. Es reicht nicht aus, einfach nur eine Beschriftung im Text neben dem Feld anzugeben.

Für einige Komponenten können Beschriftungen auch über das Kontrollkästchen **Titel ausblenden** ausgeblendet werden. Auf diesem Weg ausgeblendete Beschriftungen sind für Sprachausgabetechnologien weiterhin verfügbar, werden auf dem Bildschirm jedoch nicht angezeigt. Auch wenn dies in einigen Situationen einen guten Ansatz bilden kann, ist es in der Regel besser, möglichst immer eine sichtbare Beschriftung hinzuzufügen, da manche Benutzer nur einen sehr kleinen Ausschnitt des Bildschirms sehen (jeweils ein Feld) und die Felder nur anhand der Beschriftung richtig zuordnen können.

###### Bild-Schaltflächen {#image-buttons}

Wenn Bild-Schaltflächen verwendet werden (z. B. die Komponente **Bild-Schaltfläche** des WKND-Projekts), liefert das Feld **Titel** auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds den Alternativtext für das Bild und nicht die Beschriftung. Im folgenden Beispiel wurde daher für das Bild mit dem Text `Submit` im Bearbeitungsdialogfeld der Alt-Text `Submit` über das Feld **Titel** hinzugefügt.

###### Gruppen von Formularfeldern {#groups-of-form-fields}

Bei einer Gruppe miteinander verbundener Steuerelemente (z. B. einer **Optionsfeldgruppe**) im WKND-Projekt kann ein Titel für die Gruppe sowie einzelne Steuerelemente erforderlich sein. Wenn Sie einen Satz Optionsfelder in AEM hinzufügen, wird dieser Gruppentitel im Feld **Titel** bereitgestellt, während einzelne Titel als Optionsschaltflächen (**Elemente**) angegeben werden.

Es gibt jedoch keine programmatische Zuordnung zwischen dem Gruppentitel und den Optionsschaltflächen. Der Titel muss beim Bearbeiten der Vorlage in die erforderlichen Tags `fieldset` und `legend` gesetzt werden, um diese Zuordnung herzustellen. Dies kann ausschließlich über die Bearbeitung des Seitenquell-Codes erfolgen. Alternativ kann ein Systemadministrator die Unterstützung für diese Elemente hinzufügen, damit sie im Dialogfeld **Feldeigenschaften** angezeigt werden (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

###### Weitere Aspekte für Formulare {#additional-considerations-for-forms}

Wenn Daten in einem bestimmten Format eingegeben werden müssen, sollten Sie dies in der Beschriftung deutlich machen. Wenn z. B. ein Datum im Format `DD-MM-YYYY` eingegeben werden soll, fügen Sie diese Angabe in die Beschriftung ein. Dies führt dazu, dass die Beschriftung automatisch zusammen mit dem gewünschten Format ausgegeben wird, wenn Benutzer der Sprachausgabe auf das Feld treffen.

Wenn die Eingabe für ein Formularfeld obligatorisch ist, machen Sie dies deutlich, indem Sie das erforderliche Wort als Teil der Bezeichnung verwenden. AEM fügt ein Sternchen hinzu, wenn ein Feld erforderlich ist. Idealerweise sollte jedoch das Wort `required` (erforderlich) direkt in die Beschriftung eingefügt werden (im Feld **Titel** im Bearbeitungsdialogfeld).

Auch die Positionierung von Beschriftungen ist wichtig, da sie das Auffinden der entsprechenden Felder erleichtert. Dies ist besonders wichtig, wenn es sich um komplexe Formulare handelt. Halten Sie sich an folgende Richtlinien:

* Kontrollkästchen oder Optionsschaltflächen: 
Beschriftungen direkt rechts neben dem Feld platzieren.
* Alle anderen Formularkomponenten (z. B. Textfelder, Kombinationsfelder): 
Beschriftungen entweder direkt über dem Feld oder direkt links vom Feld platzieren.

In einfachen Formularen mit wenigen Funktionen kann die Beschriftung einer Schaltfläche mit `Submit` als Beschriftung für das angrenzende Feld dienen (z. B. `Search`). Dies ist in Situationen nützlich, in denen wenig Platz für die Beschriftung vorhanden ist.

#### Weitere Informationen – Beschriftungen oder Anweisungen (3.3.2)   {#more-information-labels-or-instructions}

* [Erfolgskriterium 3.3.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html)
* [Erfolgskriterium 3.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#labels-or-instructions)

### Fehlerempfehlung (3.3.3) {#error-suggestion}

* Erfolgskriterium 3.3.3
* Level AA
* Tastatur: Wenn ein Eingabefehler automatisch erkannt wird und Korrekturempfehlungen bekannt sind, werden diese Empfehlungen dem Benutzer bereitgestellt, es sei denn, dies würde die Sicherheit oder den Zweck des Inhalts gefährden.

#### Zweck: Fehlerempfehlung (3.3.3) {#purpose-error-suggestion}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Benutzer geeignete Empfehlungen zur Korrektur eines Eingabefehlers erhalten, sofern dies möglich ist. Die WCAG -Definition von [Eingabefehler](https://www.w3.org/TR/WCAG/#dfn-input-error) besagt, dass es sich um „vom Benutzer bereitgestellte Informationen handelt, die vom System nicht akzeptiert werden“. Einige Beispiele für Informationen, die nicht akzeptiert werden, umfassen Informationen, die vom Benutzer benötigt, aber weggelassen werden, und Informationen, die vom Benutzer bereitgestellt werden, aber außerhalb des erforderlichen Datenformats oder der zulässigen Werte liegen.

Das Erfolgskriterium 3.3.1 sieht die Benachrichtigung über Fehler vor. Personen mit kognitiven Einschränkungen können jedoch Schwierigkeiten haben, die Fehler zu korrigieren. Sehbehinderte Menschen können möglicherweise nicht genau herausfinden, wie der Fehler zu korrigieren ist. Im Falle einer nicht erfolgreichen Formularübermittlung können Benutzer das Formular abbrechen, da sie möglicherweise nicht sicher sind, wie der Fehler behoben werden soll, obwohl sie wissen, dass er aufgetreten ist.

Der Inhaltsautor kann die Beschreibung des Fehlers bereitstellen oder der Benutzeragent kann die Beschreibung des Fehlers basierend auf technologiespezifischen, programmgesteuert bestimmten Informationen bereitstellen.

#### Erfüllen: Fehlerempfehlung (3.3.3) {#how-to-meet-error-suggestion}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion).

#### Weitere Informationen: Fehlerempfehlung (3.3.3) {#more-information-error-suggestion}

* [Erfolgskriterien 3.3.3 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-suggestion.html)
* [Erfolgskriterien 3.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-suggestion)

### Fehlervermeidung (rechtliche, finanzielle, Daten) (3.3.4) {#error-prevention-legal-financial-data}

* Erfolgskriterium 3.3.4
* Level AA
* Fehlervermeidung (rechtliche, finanzielle, Daten): Für Web-Seiten, die eine für den Benutzer auftretende rechtliche Verpflichtung oder finanzielle Transaktion zur Folge haben, die Benutzer-gesteuerte Daten in Datenspeicherungssystemen ändern oder löschen oder die Testantworten des Benutzers abschicken, gilt mindestens eines der Folgenden:

   * Reversibel
Versendete Daten sind reversibel.
   * Geprüft
Vom Benutzer eingegebene Daten werden auf Eingabefehler überprüft und der Benutzer erhält die Gelegenheit, diese zu korrigieren.
   * Bestätigt:
Es gibt einen Mechanismus, um Informationen zu überprüfen, zu bestätigen und zu korrigieren, bevor sie endgültig abgesendet werden.

#### Zweck: Fehlervermeidung (rechtliche, finanzielle, Daten) (3.3.4) {#purpose-error-prevention-legal-financial-data}

Mit diesem Erfolgskriterium sollen Benutzer mit Behinderungen dabei unterstützt werden, schwerwiegende Folgen eines Fehlers bei der Ausführung einer Aktion zu vermeiden, die nicht rückgängig gemacht werden kann. Beispielsweise sind der Kauf nicht erstattungsfähiger Flug-Tickets oder die Übermittlung einer Bestellung zum Kauf von Aktien auf einem Maklerkonto Finanztransaktionen mit schwerwiegenden Folgen. Wenn ein Benutzer beim Datum der Flugreise einen Fehler gemacht hat, erhält er möglicherweise ein Ticket für den falschen Tag, das nicht umgetauscht werden kann. Wenn der Benutzer einen Fehler bei der Anzahl der zu kaufenden Aktien gemacht hat, könnte er am Ende mehr Aktien als beabsichtigt kaufen. Beide Arten von Fehlern betreffen Transaktionen, die sofort stattfinden und danach nicht mehr geändert werden und sehr kostspielig sein können. Ebenso kann es sich um einen nicht behebbaren Fehler handeln, wenn Benutzer unbeabsichtigt Daten ändern oder löschen, die in einer Datenbank gespeichert sind, auf die sie später zugreifen müssen, z. B. ihr gesamtes Reiseprofil auf der Website eines Reise-Service. Wenn es um das Ändern oder Löschen von „vom Benutzer steuerbaren“ Daten geht, soll ein Massenverlust von Daten wie das Löschen einer Datei oder eines Datensatzes verhindert werden. Es ist nicht beabsichtigt, eine Bestätigung für jeden Speicherbefehl oder die einfache Erstellung oder Bearbeitung von Dokumenten, Datensätzen oder anderen Daten zu verlangen.

Benutzer mit Behinderungen machen möglicherweise eher Fehler. Personen mit Leseschwäche können Zahlen und Buchstaben vertauschen und Personen mit motorischen Behinderungen können versehentlich Tasten drücken. Wenn Benutzer die Möglichkeit erhalten, Aktionen rückgängig zu machen, können sie einen Fehler korrigieren, der schwerwiegende Folgen haben könnte. Durch die Möglichkeit, Informationen zu überprüfen und zu korrigieren, kann der Benutzer einen Fehler erkennen, bevor er eine Handlung mit schwerwiegenden Folgen vornimmt.

Vom Benutzer steuerbare Daten sind vom Benutzer einsehbare Daten, die der Benutzer durch eine absichtliche Aktion ändern und/oder löschen kann. Beispiele für die Kontrolle solcher Daten durch den Benutzer wären die Aktualisierung der Telefonnummer und Adresse für das Benutzerkonto oder das Löschen eines Datensatzes früherer Rechnungen von einer Website. Es geht hier nicht um Dinge wie Internet-Protokolle und Überwachungsdaten von Suchmaschinen, die der Benutzer nicht direkt einsehen oder mit denen er nicht direkt interagieren kann.

#### Erfüllen: Fehlervermeidung (rechtliche, finanzielle, Daten) (3.3.4) {#how-to-meet-error-prevention-legal-financial-data}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 3.3.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data).

#### Weitere Informationen: Fehlervermeidung (rechtliche, finanzielle, Daten) (3.3.4) {#more-information-error-prevention-legal-financial-data}

* [Erfolgskriterien 3.3.4 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/error-prevention-legal-financial-data.html)
* [Erfolgskriterien 3.3.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#error-prevention-legal-financial-data)

## Grundsatz 4: Robust {#principle-robust}

[Grundsatz 4: Robust – Inhalte müssen robust genug sein, damit sie zuverlässig von einer großen Auswahl an Benutzeragenten einschließlich Hilfstechnologien interpretiert werden können.](https://www.w3.org/TR/WCAG/#robust)

### Kompatibel (4.1) {#compatible}

[Richtlinie 4.1 Kompatibel: Maximieren Sie die Kompatibilität mit aktuellen und zukünftigen Benutzeragenten, einschließlich Hilfstechnologien.](https://www.w3.org/TR/WCAG/#compatible)

Maximieren Sie die Kompatibilität mit aktuellen und zukünftigen Benutzeragenten, einschließlich Hilfstechnologien.

### Syntaxanalyse (4.1.1)   {#parsing}

* Erfolgskriterium 4.1.1
* Stufe A
* Syntaxanalyse: Bei Inhalt, der durch die Benutzung von Auszeichnungssprache implementiert wurde, haben Elemente komplette Start- und End-Tags, werden Elemente entsprechend ihrer Spezifikationen verschachtelt, enthalten Elemente keine doppelten Attribute und alle IDs sind einzigartig, außer wenn die Spezifikationen diese Eigenschaften erlauben.

#### Zweck: Syntaxanalyse (4.1.1) {#purpose-parsing}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Benutzeragenten, einschließlich Hilfstechnologien, Inhalte genau interpretieren und analysieren können. Wenn der Inhalt nicht in eine Datenstruktur analysiert werden kann, kann es vorkommen, dass andere Benutzeragenten ihn anders darstellen oder nicht analysieren können. Einige Benutzeragenten verwenden „Reparaturtechniken“, um schlecht kodierte Inhalte wiederzugeben.

Da die Reparaturtechniken von Benutzeragent zu Benutzeragent unterschiedlich sind, können Autoren nicht davon ausgehen, dass der Inhalt korrekt in eine Datenstruktur analysiert wird oder dass er von spezialisierten Benutzeragenten, einschließlich Hilfstechnologie, korrekt wiedergegeben wird, es sei denn, der Inhalt wird gemäß den in der formalen Grammatik für diese Technologie definierten Regeln erstellt. In Auszeichnungssprachen führen Fehler in der Element- und Attributsyntax und das Fehlen ordnungsgemäß verschachtelter Start-/End-Tags zu Fehlern, die Benutzeragenten daran hindern, den Inhalt zuverlässig zu analysieren. Daher erfordert das Erfolgskriterium, dass der Inhalt nur nach den Regeln der formalen Grammatik analysiert werden kann.

#### Erfüllen: Syntaxanalyse (4.1.1) {#how-to-meet-parsing}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 4.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#parsing).

#### Weitere Informationen: Syntaxanalyse (4.1.1) {#more-information-parsing}

* [Erfolgskriterien 4.1.1 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/parsing.html)
* [Erfolgskriterien 4.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#parsing)

### Name, Rolle, Wert (4.1.2) {#name-role-value}

* Erfolgskriterium 4.1.2
* Stufe A
* Name, Rolle, Wert: Für alle Bestandteile der Benutzerschnittstelle (einschließlich, aber nicht beschränkt auf: Formularelemente, Links und durch Skripte generierte Komponenten) können Name und Rolle durch Software bestimmt werden; Zustände, Eigenschaften und Werte, die vom Benutzer festgelegt werden können, können durch Software festgelegt sein; und die Benachrichtigung über Änderungen an diesen Elementen steht den Benutzeragenten zur Verfügung, einschließlich Hilfstechnologien.

#### Zweck: Name, Rolle, Wert (4.1.2) {#purpose-ame-role-value}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Hilfstechnologien (HT) Informationen über den Status der Steuerelemente der Benutzeroberfläche im Inhalt sammeln, aktivieren (oder festlegen) und auf dem neuesten Stand halten können.

Wenn Standardsteuerungen von zugänglichen Technologien verwendet werden, ist dieser Prozess unkompliziert. Wenn die Elemente der Benutzeroberfläche gemäß Spezifikation verwendet werden, sind die Bedingungen dieser Bestimmung erfüllt. (Siehe Beispiele für Erfolgskriterium 4.1.2 unten)

Wenn jedoch benutzerdefinierte Steuerelemente erstellt oder Schnittstellenelemente (in Code oder Skript) so programmiert werden, dass sie eine andere Rolle und/oder Funktion als üblich haben, müssen zusätzliche Maßnahmen ergriffen werden, um sicherzustellen, dass die Steuerelemente wichtige Informationen für Hilfstechnologien bereitstellen und sich durch Hilfstechnologien steuern lassen.

Ein besonders wichtiger Zustand eines Steuerelements der Benutzerschnittstelle ist, ob es den Fokus hat. Der Fokus-Zustand eines Steuerelements kann programmatisch bestimmt werden. Benachrichtigungen über eine Änderung des Fokus werden an Benutzeragenten und Hilfstechnologien gesendet. Andere Beispiele für den Zustand eines Steuerelements der Benutzerschnittstellen sind, ob ein Kontrollkästchen oder ein Optionsfeld aktiviert wurde oder ob ein reduzierbarer Baum oder Listenknoten erweitert oder reduziert wurde.

#### Erfüllen: Name, Rolle, Wert (4.1.2) {#how-to-meet-ame-role-value}

Befolgen Sie die Richtlinien unter [Erfolgskriterien 4.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value).

#### Weitere Informationen: Name, Rolle, Wert (4.1.2) {#more-information-ame-role-value}

* [Erfolgskriterien 4.1.2 verstehen](https://www.w3.org/WAI/WCAG21/Understanding/name-role-value.html)
* [Erfolgskriterien 4.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/#name-role-value)
