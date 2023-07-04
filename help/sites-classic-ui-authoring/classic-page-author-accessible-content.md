---
title: Erstellen barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien)
seo-title: Creating Accessible Content (WCAG 2.0 Conformance)
description: WCAG 2.0 umfasst eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Web-Inhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind.
seo-description: WCAG 2.0 consists of a set of technology independent guidelines and success criteria to help make web content accessible to, and usable by, persons with disabilities.
page-status-flag: de-activated
uuid: c2c0cac0-2a9f-478d-8261-e8cc894aae34
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 378bc33d-ab6c-4651-9688-102c961561fc
exl-id: 01c69aa9-2623-42dc-9e2d-62bc5e01cf0e
source-git-commit: ce6d24e53a27b64a5d0a9db2e4b6672bd77cf9ec
workflow-type: ht
source-wordcount: '9153'
ht-degree: 100%

---

# Erstellen barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien){#creating-accessible-content-wcag-conformance}

>[!CAUTION]
>
>Da in AEM 6.4 die klassische Benutzeroberfläche veraltet ist, wurde der Inhalt auf dieser Seite nicht für WCAG 2.1 aktualisiert.
>
>Auf den folgenden Seiten finden Sie Details zu AEM und WCAG 2.1:
>
>* [AEM und die Richtlinien für barrierefreies Webdesign](/help/managing/web-accessibility.md)
>* [Kurzanleitung zu WCAG 2.1](/help/managing/qg-wcag.md)
>* [Erstellen barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.1-Richtlinien)](/help/sites-authoring/creating-accessible-content.md)


WCAG 2.0 umfasst eine Reihe technologieunabhängiger Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Web-Inhalten unterstützen, die für Personen mit Behinderungen barrierefrei zugänglich sind.

>[!NOTE]
>
>Siehe auch:
>
>* [Kurzanleitung zu WCAG 2.0](/help/managing/qg-wcag.md)
>* [Konfigurieren des Rich-Text-Editors (RTE) für die Erstellung von barrierefrei zugänglichen Inhalten](/help/sites-administering/rte-accessible-content.md)
>


Diese Richtlinien sind nach drei Konformitätsebenen abgestuft: Stufe A (niedrigste), Stufe AA und Stufe AAA (höchste). Die Ebenen werden kurz wie folgt definiert:

* **Stufe A:** Ihre Site erreicht eine einfache, minimale Barrierefreiheit. Bei Erreichen dieser Stufe sind alle Kategorie-A-Erfolgskriterien erfüllt.
* **Stufe AA:** Dies ist ein idealer Barrierefreiheitsgrad, der angestrebt werden sollte und mit dem Ihre Site eine erhöhte Zugänglichkeitsstufe ermöglicht, sodass sie für die meisten Menschen in den meisten Situationen mit den meisten Technologien zugänglich ist. Bei Erreichen dieser Stufe sind alle Erfolgskriterien der Ebenen A und AA erfüllt.
* **Ebene AAA:** Ihre Site erreicht ein sehr hohes Maß an Barrierefreiheit. Um diese Stufe zu erreichen, müssen alle Erfolgskriterien der Stufen A, AA und AAA erfüllt sein.

Bei der Erstellung der Site sollten Sie festlegen, welchen Level Ihre Site insgesamt erfüllen soll.

Im folgenden Abschnitt finden Sie die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) mit den entsprechenden Erfolgskriterien für die [Konformitäts-Level](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html) Level A und Level AA.

>[!NOTE]
>
>Da es für bestimmte Inhaltstypen nicht möglich ist, alle Erfolgskriterien der Stufe AAA zu erfüllen, wird davon abgeraten, diese Konformität als allgemeine Richtlinie zu verlangen.

>[!NOTE]
>
>Dieses Dokument verwendet Folgendes:
>
>* Die Kurznamen für die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines).
>* Die Nummerierung der [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) zur Erleichterung von Querverweisen zur WCAG-Website.
>


## Grundsatz 1: Erkennbar     {#principle-perceivable}

[Grundsatz 1: Erkennbar – Informationen und Komponenten der Benutzeroberfläche müssen für die Benutzer so dargestellt sein, dass sie sie erkennen können.](https://www.w3.org/TR/WCAG20/#perceivable)

### Textalternativen (1.1) {#text-alternatives}

[Richtlinie 1.1 Textalternativen: Bieten Sie Textalternativen für nichttextliche Inhalte, damit sie in andere Formate geändert werden können, die von bestimmten Personen benötigt werden, wie zum Beispiel Großdruck, Braille, Sprache, Symbole oder einfachere Sprache.](https://www.w3.org/TR/WCAG20/#text-equiv)

### Nichttextlicher Inhalt (1.1.1) {#non-text-content}

* Erfolgskriterium 1.1.1
* Level A
* Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzern präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen.

#### Zweck: Nichttextliche Inhalte (1.1.1) {#purpose-non-text-content}

Informationen auf einer Web-Seite können in vielen verschiedenen nichttextlichen Formaten bereitgestellt werden, z. B. in Bildern, Videos, Animationen, Diagrammen und Graphen. Blinde Personen oder Personen mit schweren Sehbehinderungen können nichttextlichen Inhalt nicht sehen, sie können jedoch auf Textinhalte zugreifen, indem sie sie von einer Bildschirmlesehilfe lesen lassen oder von einem Braille-Anzeigegerät in taktiler Form präsentiert bekommen. Indem Sie also zu Inhalten in grafischem Format Textalternativen bereitstellen, können Personen, die diesen grafischen Inhalt nicht sehen können, auf eine äquivalente Version der Informationen zugreifen, die im Inhalt geboten werden.

Ein nützlicher weiterer Vorteil besteht darin, dass Textalternativen es ermöglichen, nichttextliche Inhalte durch Suchmaschinentechnologie zu indizieren.

#### Erfüllen: Nichttextlicher Inhalt (1.1.1) {#how-to-meet-non-text-content}

Bei statischen Grafiken besteht die Grundanforderung darin, eine gleichwertige Textalternative für die Grafik bereitzustellen. Diese Methode erfolgt im Feld **Alt-Text**:

>[!NOTE]
>
>Einige integrierte Komponenten wie **Karussell** und **Dia-Show** bieten keine Möglichkeit zum Hinzufügen von alternativen Textbeschreibungen zu Bildern. Wenn Sie Versionen dieser Komponenten für Ihre AEM-Instanz implementieren, sollte Ihr Entwicklungs-Team diese Komponenten so konfigurieren, dass sie das Attribut `alt` unterstützen. Dadurch wird sichergestellt, dass Autorinnen und Autoren es zum Inhalt hinzufügen können (siehe [Hinzufügen von Unterstützung für weitere HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

Das Feld **ALT-Text** ist im Komponentendialogfeld **Bild** auf der Registerkarte **Erweitert** verfügbar:

![Das Dialogfeld „Bearbeiten“ der Komponente „Bild“ in der klassischen Benutzeroberfläche zeigt das Feld „ALT-Text“.](assets/chlimage_1-17a.png)

AEM fügt Ihren Bildern standardmäßig einen **ALT-Text** hinzu. Für die klassische Benutzeroberfläche gibt es zwei verschiedene Szenarien, wie das Standardattribut erstellt wird, wobei der Standardwert als Alternative möglicherweise nicht ausreicht und wahrscheinlich in der Registerkarte **Erweitert** der Bildeigenschaften bearbeitet werden muss:

* Datei:

Ein Bild wird von der Festplatte der Benutzerin bzw. des Benutzers hochgeladen. Wenn Sie einer Seite eine Bildkomponente hinzufügen und dann ein Bild von Ihrer Festplatte oder einer anderen Quelle auswählen, lautet der Standardwert für **Alt-Text** `file`. Dieser Wert muss auf der Registerkarte **Erweitert** der Bildeigenschaften geändert werden. Dieser Wert wird wiederum nicht im Feld **Alternativtext** angezeigt, doch wenn der Wert geändert wird, ist der neue Wert im Feld zu sehen.

* Asset:

Ein Bild wird aus dem digitalen Asset-Repository hinzugefügt. Wenn Sie ein Bild aus dem Repository der digitalen Assets auf eine Web-Seite ziehen, werden die Werte für **Titel** und **Alternativtext** für dieses Bild aus den Metadaten des Bildes übernommen.

>[!NOTE]
>
>In beiden oben genannten Szenarien ist der Wert **ALT-Text** nicht auf der Registerkarte **Erweiterte Bildeigenschaften** sichtbar. Geben Sie zur Änderung des Standardwerts im Feld **ALT-Text** einfach einen neuen Wert ein.

>[!NOTE]
>
>Wenn Ihr Bild nur Dekorationszwecken dient (siehe [Erstellen guter Textalternativen](#creating-good-text-alternatives)), dann können Sie im Feld **ALT-Text** durch Drücken der Leertaste ein Leerzeichen einfügen. Dadurch wird ein leeres `alt`-Attribut erstellt, das eine Bildschirmlesehilfe auffordert, das Bild zu ignorieren.

#### Erstellen guter Textalternativen {#creating-good-text-alternatives}

Es gibt verschiedene Arten von nichttextlichem Inhalt. Daher hängt der Wert der Textalternative von der Rolle ab, die die Grafik auf der Web-Seite spielt. Zu den allgemeinen Faustregeln gehören:

* Textalternativen sollten kurz sein, doch sollten sie die wesentlichen Informationen, die durch den nichttextlichen Inhalt bereitgestellt werden, eindeutig erfassen.
* Übermäßig lange Beschreibungen (über 100 Zeichen) sollten vermieden werden. Wenn eine Textalternative mehr Details erfordert:

   * Geben Sie im Alternativtext eine kurze Beschreibung an
   * und fügen Sie irgendwo anders auf der entsprechenden Seite oder auf einer anderen Web-Seite eine längere Beschreibung ein. Verlinken Sie zu dieser separaten Beschreibung, indem Sie das Bild zu einem Link machen, oder indem Sie einen Text-Link neben dem Bild platzieren.

* Alternativtext sollte keine Inhalte replizieren, die in Textformularen bereitgestellt werden, die sich in der Nähe auf derselben Seite befinden. Denken Sie daran, dass viele Bilder Illustrationen von Punkten sind, die bereits im Text einer Seite behandelt werden, sodass eine detaillierte Textalternative bereits vorhanden sein kann.
* Wenn es sich bei dem nichttextlichen Inhalt um einen Link zu einer anderen Seite oder einem anderen Dokument handelt und es keinen anderen Text-bildenden Teil desselben Links gibt, muss der Alternativtext für das Bild das Ziel des Links angeben. Er darf nicht das Bild beschreiben.
* Wenn der nichttextliche Inhalt in einem Schaltflächenelement enthalten ist und es keinen andern textbildenden Teil derselben Schaltfläche gibt, muss der Alternativtext des Bildes die Funktionalität der Schaltfläche angeben, nicht das Bild beschreiben.
* Es ist akzeptabel, dass ein Bild mit einem leeren Alternativtext (null) versehen wird, aber nur, wenn das Bild keinen Alternativtext hat. Beispielsweise, wenn es sich um eine rein dekorative Grafik handelt. Oder wenn der entsprechende Text bereits im Seitentext vorhanden ist.

Der [W3C-Entwurf: HTML5-Techniken zur Bereitstellung nützlicher Textalternativen](https://html.spec.whatwg.org/multipage/images.html#alt) verfügt über weitere Details und Beispiele für die Bereitstellung geeigneter Alternativtexte für Bilder unterschiedlicher Typen.

Bestimmte Arten von nichttextlichem Inhalt, für den Textalternativen erforderlich sind:

* Veranschaulichende Fotos:

Hierbei handelt es sich um Bilder von Menschen, Objekten oder Orten. Überlegen Sie, welche Rolle das Foto auf der Seite spielt. Ein geeignetes Textäquivalent ist wahrscheinlich *Foto von [Objekt]*, es kann jedoch vom Text neben dem Bild abhängen.

* Symbole:

Kleine Piktogramme (Grafiken), die bestimmte Informationen vermitteln. Sie müssen konsistent auf einer Seite und einer Site verwendet werden. Alle Instanzen des Symbols auf einer Seite oder einer Site sollten dieselbe kurze und knappe Textalternative haben, es sei denn, dies führt zu einer unnötigen Duplizierung von angrenzendem Text.

* Diagramme:

Diese stellen normalerweise numerische Daten dar. So könnte als eine Möglichkeit zur Bereitstellung von Alternativtext eine kurze Zusammenfassung der im Diagramm gezeigten Haupttrends eingefügt werden. Fall nötig, können Sie eine detailliertere Beschreibung im Text im Feld **Beschreibung** auf der Registerkarte **Erweiterte Bildeigenschaften** einfügen. Außerdem könnten Sie die Quelldaten an anderer Stelle auf der Seite oder Site als Tabelle zur Verfügung stellen.

![Beispiel eines Diagramms. Nachfolgend sehen Sie einen bewährten Ansatz zur Bereitstellung einer Alternative.](assets/chlimage_1-2a.jpeg)

Zur Bereitstellung einer Alternative für dieses Beispieldiagramm können Sie dem Bild selbst einen knappen `alt`-Text hinzufügen und dann dem Bild eine vollständige Textalternative folgen lassen.

```xml
<p><img src="figure1.gif" alt="Figure 1" ></p>
<p> Figure 1. Distribution of Articles by Journal Category.
Pie chart: Language=68%, Education=14% and Science=18%.</p>
```

>[!NOTE]
>
>Der obige Ausschnitt dient nur zur Veranschaulichung der Reihenfolge. Verwenden Sie die **Bildkomponente** anstatt der oben verwendeten `img src`-Referenz.

In AEM können Sie dies anhand einer Kombination der Felder **Alt-Text** und **Beschreibung** im Konfigurationsdialogfeld des Bildes erreichen, wie in [Erfüllen: Nichttextlicher Inhalt (1.1.1)](#how-to-meet-non-text-content).

* Karten, Diagramme, Flussdiagramme:

Für Grafiken mit räumlichen Daten (z. B. um Beziehungen zwischen Objekten oder einem Prozess zu beschreiben), stellen Sie sicher, dass die Schlüsselmeldung im Textformat bereitgestellt wird. Bei Karten ist die Bereitstellung eines Volltextäquivalents wahrscheinlich nicht sinnvoll. Wenn aber eine Karte den Weg zu einem bestimmten Ort zeigen soll, kann der Alternativtext des Kartenbildes kurz *Karte von X* einblenden und dann an einer anderen Stelle auf der Seite oder im Feld **Beschreibung** auf der Registerkarte **Erweitert** der **Bildkomponente** eine Wegbeschreibung zu dem Ort bereitstellen.

* CAPTCHAs:

Ein CAPTCHA ist ein *vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen*. Es handelt sich dabei um eine Sicherheitsprüfung, die auf Web-Seiten verwendet wird, um Menschen von böswilliger Software zu unterscheiden. Dies kann jedoch die Barrierefreiheit einschränken. Hierbei handelt es sich um Bilder, bei denen Benutzende beschreiben müssen, was sie sehen, um einen Sicherheitstest bestehen zu können. Es ist nicht möglich, eine Textalternative für so ein Bild bereitzustellen. Daher müssen Sie stattdessen alternative, nichtgrafische Lösungen in Betracht ziehen.

Das W3C bietet verschiedene Vorschläge, wie z. B. die folgenden. Jeder dieser Ansätze hat seine eigenen Vorteile und Nachteile.

    * Logische Puzzles
    * Verwendung von Tonausgabe anstelle von Bildern
    * Eingeschränkte Benutzerkonten und Spam-Filter.

* Hintergrundbilder:

Diese Bilder werden anhand von Cascading Style Sheets (CSS) statt HTML erstellt. Dies bedeutet, dass es nicht möglich ist, einen Wert für Alternativtext anzugeben. Daher sollten Hintergrundbilder keine wichtigen textlichen Informationen angeben. Falls sie es doch tun, müssen diese Informationen auch im Text der Seite vorhanden sein.

Es ist jedoch wichtig, dass ein alternativer Hintergrund angezeigt wird, wenn das Bild nicht angezeigt werden kann.

>[!NOTE]
>
>Es sollte ein angemessenes Kontrastniveau zwischen dem Hintergrund und dem Vordergrundtext vorhanden sein. Dieser Kontrast wird im Abschnitt [Kontrast (Minimum) (1.4.3)](#contrast-minimum) detaillierter behandelt.

#### Weitere Informationen: Nichttextlicher Inhalt (1.1.1) {#more-information-non-text-content}

* [Erfolgskriterien 1.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)
* [Erfolgskriterien 1.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#text-alternatives)
* [W3C: HTML5-Techniken zur Bereitstellung nützlicher Textalternativen](https://html.spec.whatwg.org/multipage/images.html#alt)
* [W3C-Erklärung und Alternativen zu CAPTCHAs](https://www.w3.org/TR/turingtest/)

### Zeitbasierte Medien (1.2) {#time-based-media}

[Richtlinie 1.2 Zeitbasierte Medien: Bereitstellen von Alternativen für zeitbasierte Medien.](https://www.w3.org/TR/WCAG20/#text-equiv)

Diese Informationen behandeln Web-Inhalte, die *zeitbasiert* sind. Hier werden Inhalte behandelt, die die Benutzerin oder der Benutzer abspielen kann (z. B. Video, Audio und animierte Inhalte) und die entweder voraufgezeichnet sind oder als Live-Stream wiedergegeben werden.

### Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#audio-only-and-video-only-pre-recorded}

* Erfolgskriterium 1.2.1
* Level A
* Nur-Audio- und Nur-Video-Medien (voraufgezeichnet): Für voraufgezeichnete Nur-Audio- und Nur-Video-Medien gilt Folgendes, es sei denn, das Audio oder Video ist eine Medienalternative für Text und wird deutlich als solche gekennzeichnet:

   * Nur voraufgezeichnetes Audio: Es wird eine Alternative für zeitbasierte Medien bereitgestellt, die gleichwertige Informationen für aufgezeichnete Nur-Audio-Inhalte bereitstellt.
   * Nur voraufgezeichnetes Video: Es wird entweder eine Alternative für zeitbasierte Medien oder ein Audio-Track mit gleichwertigen Informationen für aufgezeichnete Nur-Video-Inhalte bereitgestellt.

#### Zweck: Nur-Audio und Nur-Video (voraufgezeichnet) (1.2.1) {#purpose-audio-only-and-video-only-pre-recorded}

Probleme bei der Barrierefreiheit von Video und Audio können auftreten bei:

* Personen mit eingeschränkter Sehkraft, wenn kein Soundtrack vorhanden ist oder der Soundtrack nicht ausreicht, um sie über die Ereignisse im Video oder der Animation zu informieren;
* Personen mit eingeschränktem Hörvermögen oder gehörlose Personen, die den Soundtrack nicht hören können.
* Personen, die den Soundtrack zwar hören können, doch den gesprochenen Inhalt nicht verstehen (weil er beispielsweise in einer Sprache aufgezeichnet ist, die sie nicht verstehen).

Video oder Audio kann auch für Personen unzugänglich sein, die Browser oder Geräte verwenden, die die Wiedergabe von Inhalt in bestimmten Medienformaten, wie zum Beispiel Adobe Flash, nicht unterstützen.

Wenn Sie diese Informationen in einem anderen Format bereitstellen, z. B. Text (oder Audio für Video ohne Audio), können Sie sie für Personen verfügbar machen, die nicht auf den ursprünglichen Inhalt zugreifen können.

#### Erfüllen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1)     {#how-to-meet-audio-only-and-video-only-pre-recorded}

* Wenn es sich bei dem Inhalt um aufgezeichnetes Audio ohne Video (wie zum Beispiel einen Podcast) handelt:

   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einem Texttranskript des Audioinhalts bereit.

   Das Transkript sollte eine HTML-Seite mit einem Textäquivalent zu allen gesprochenen und wichtigen nicht-gesprochenen Inhalten sein. Es sollte auch angeben, wer spricht, eine Beschreibung der Szene, Stimmausdrücke und eine Beschreibung anderer wichtiger Audioinhalte.

* Wenn der Inhalt eine Animation oder eine Videoaufzeichnung ohne Audio ist:

   * Stellen Sie unmittelbar vor oder nach dem Inhalt einen Link zu einer entsprechenden Textbeschreibung der vom Video bereitgestellten Informationen bereit
   * Oder eine gleichwertige Audiobeschreibung in einem häufig verwendeten Audioformat wie MP3.

>[!NOTE]
>
>Wenn der Audio- oder Videoinhalt als Alternative zu Inhalten bereitgestellt wird, die in einem anderen Format auf einer Web-Seite vorhanden sind, müssen die oben genannten Anforderungen nicht erfüllt werden. Wenn ein Video beispielsweise eine Liste von Textanweisungen veranschaulicht, ist für dieses Video keine Alternative erforderlich, da die Textanweisungen bereits als Alternative zum Video dienen.

Das Einfügen von Multimedia-Inhalten, insbesondere von Flash-Inhalten, in Ihren AEM-Web-Seiten ist ähnlich wie das Einfügen eines Bildes. Da Multimedia-Inhalte jedoch sehr viel mehr sind als ein Standbild, gibt es verschiedene Einstellungen und Optionen, um zu steuern, wie Multimedia-Inhalte wiedergegeben werden.

>[!NOTE]
>
>Wenn Sie Multimedia mit informativem Inhalt verwenden, müssen Sie auch Links zu Alternativen erstellen. Beispielsweise müssen Sie zum Hinzufügen eines Texttranskripts eine HTML-Seite für die Anzeige des Transkripts erstellen und dann neben oder unter dem Audioinhalt einen Link hinzufügen.

#### Weitere Informationen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#more-information-audio-only-and-video-only-pre-recorded}

* [Erfolgskriterien 1.2.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
* [Erfolgskriterien 1.2.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#time-based-media)

### Untertitel (aufgezeichnet) (1.2.2)     {#captions-pre-recorded}

* Erfolgskriterium 1.2.2
* Level A
* Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Untertitel (aufgezeichnet) (1.2.2)     {#purpose-captions-pre-recorded}

Menschen, die taub oder schwerhörig sind, können Audioinhalte überhaupt nicht oder nur mit großen Schwierigkeiten aufrufen. Untertitel sind Textäquivalente für gesprochene und nicht-gesprochene Audioinhalte, die zum entsprechenden Zeitpunkt während des Videos auf dem Bildschirm angezeigt werden. Sie ermöglichen es Menschen, die das Audio nicht hören können, zu verstehen, was passiert.

>[!NOTE]
>
>Untertitel sind nicht erforderlich, wenn auf derselben Seite wie das Video oder die Animation geeignete Text- oder Nicht-Text-Entsprechungen (die direkt gleichwertige Informationen bereitstellen) verfügbar sind.

#### Erfüllen: Untertitel (aufgezeichnet) (1.2.2)     {#how-to-meet-captions-pre-recorded}

Es gibt zwei Arten von Untertiteln:

* Offen: Immer sichtbar, wenn das Video abgespielt wird
* Geschlossen: Benutzer können die Untertitel ein- oder ausschalten

Verwenden Sie nach Möglichkeit verdeckte Untertitel. Benutzerinnen und Benutzer können damit wählen, ob Untertitel angezeigt werden sollen.

Erstellen Sie für verdeckte Untertitel eine synchronisierte Untertiteldatei in einem geeigneten Format, wie etwa [SMIL](https://www.w3.org/AudioVideo/), und stellen Sie sie zusammen mit der Videodatei bereit.

Weitere Informationen finden Sie in den Tutorials unter [Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2)](#more-information-captions-pre-recorded). Stellen Sie sicher, dass Sie einen Hinweis geben, um den Benutzerinnen und Benutzern mitzuteilen, dass Untertitel für das Video verfügbar sind.

Wenn Sie offene Untertitel verwenden müssen, betten Sie den Text in die Videospur ein. Diese Methode wird mit Anwendungen zur Videobearbeitung erreicht, die das Überblenden von Titeln auf dem Video ermöglichen.

#### Weitere Informationen: Untertitel (voraufgezeichnet) (1.2.2) {#more-information-captions-pre-recorded}

* [Erfolgskriterium 1.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html):
* [Erfolgskriterien 1.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#time-based-media)
* [W3C: Synchronisiertes Multimedia](https://www.w3.org/AudioVideo/)
* [Untertitel, Transkripte und Audiobeschreibungen – mit WebAIM](https://webaim.org/techniques/captions/)

### Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3)     {#audio-description-or-media-alternative-pre-recorded}

* Erfolgskriterium 1.2.3
* Level A
* Audiobeschreibung oder Medienalternative (voraufgezeichnet): Eine Alternative für zeitbasierte Medien oder Audiobeschreibung des voraufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, es sei denn, das Medium ist eine Medienalternative für Text und ist als solche eindeutig gekennzeichnet.

#### Zweck: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3)     {#purpose-audio-description-or-media-alternative-pre-recorded}

Für Blinde oder sehbehinderte Menschen ist die Barrierefreiheit eingeschränkt, wenn die Informationen in einem Video oder einer Animation nur visuell bereitgestellt werden. Oder wenn der Soundtrack nicht genügend Informationen bereitstellt, um zu verstehen, was visuell geschieht.

#### Erfüllen: Audiobeschreibung oder Medienalternative (voraufgezeichnet) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-pre-recorded}

Es gibt zwei Ansätze, die angewendet werden können, um dieses Erfolgskriterium zu erfüllen. Beide sind zulässig:

1. Fügen Sie zusätzliche Audiobeschreibungen für den Videoinhalt hinzu. Sie können diesen Ansatz auf eine von drei Arten durchführen:

   * Geben Sie während der Pausen im vorhandenen Dialogfeld Informationen zu Änderungen in der Szene an, die nicht als Teil der vorhandenen Audiospur angezeigt werden;
   * Stellen Sie eine neue, zusätzliche und optionale Audiospur bereit, die den ursprünglichen Soundtrack und zudem weitere Audioinformationen zu den Änderungen in der Szene enthält.

      * Benutzerinnen und Benutzer können zwischen der vorhandenen Audiospur (die *keine* Audiobeschreibung enthält) und der neuen Audiospur (die *eine Audiobeschreibung enthält*) wechseln.
      * Diese Methode verhindert Unterbrechungen für Benutzerinnen und Benutzer, die die zusätzliche Beschreibung nicht benötigen.
   * Erstellen Sie eine zweite Version des Videoinhalts, um erweiterte Audiobeschreibungen zu ermöglichen. Dadurch werden die Schwierigkeiten bei der Bereitstellung detaillierter Audiobeschreibungen innerhalb der Lücken zwischen dem bestehenden Dialog verringert, indem Audio und Video an geeigneten Punkten vorübergehend angehalten werden. Dadurch kann eine wesentlich längere Audiobeschreibung gegeben werden, bevor die Aktion erneut gestartet wird. Wie im vorherigen Beispiel wird dies am besten als optionale zusätzliche Audiospur bereitgestellt, um Störungen für Benutzende zu vermeiden, die die zusätzliche Beschreibung nicht benötigen.


1. Geben Sie ein Text-Transkript an, das den Audio- und visuellen Elementen des Videos oder der Animation entspricht. Es sollte gegebenenfalls eine Beschreibung der Sprechenden, der Szene und von Stimmausdrücken enthalten sein. Je nach Länge können Sie das Transkript auf derselben Seite wie das Video bzw. die Animation oder auf einer separaten Seite platzieren. Wenn Sie die zweite Option wählen, geben Sie einen Link zum Transkript neben dem Video bzw. der Animation an.

Genaue Details zum Erstellen von Audiobeschreibungen für Videos würden den Rahmen dieses Handbuchs sprengen. Die Erstellung von Audiobeschreibungen kann zeitaufwendig sein, doch andere Adobe-Produkte helfen Ihnen bei diesen Aufgaben. Wenn Sie Inhalte in Adobe Flash Professional erstellen, sollten Sie auch ein Skript erstellen, um den Benutzer aufzufordern, das entsprechende Plug-in herunterzuladen. Zudem sollten Sie eine Textalternative anhand des Elements `<noscript>` bereitstellen.

#### Weitere Informationen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#more-information-audio-description-or-media-alternative-pre-recorded}

* [Erfolgskriterien 1.2.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html):
* [Erfolgskriterien 1.2.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-media-equiv-audio-desc)
* [Adobe Encore CS5](https://helpx.adobe.com/de/premiere-pro/using/whats-new.html)

### Untertitel (live) (1.2.4)          {#captions-live}

* Erfolgskriterium 1.2.4
* Level AA
* Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Untertitel (Live) (1.2.4) {#purpose-captions-live}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Untertitel (aufgezeichnet)](#captions-pre-recorded) insofern, als es Zugangsbarrieren behandelt, die gehörlose oder schwerhörige Menschen erfahren; der Unterschied besteht darin, dass dieses Erfolgskriterium Live-Präsentationen wie Webcasts behandelt.

#### Erfüllen: Untertitel (Live) (1.2.4) {#how-to-meet-captions-live}

Befolgen Sie die Anleitungen, die oben unter [Untertitel (voraufgezeichnet)](#captions-pre-recorded) genannt wurden. Da die Medien live übermittelt werden, muss die Bereitstellung der Untertitel so schnell wie möglich erfolgen und sofort auf das reagieren, was passiert. Daher sollten Sie Tools für die Echtzeit-Untertitelung oder für „Sprache in Text“ in Erwägung ziehen.

Detaillierte Anweisungen dazu würden den Rahmen dieses Dokuments sprengen, doch in den folgenden Ressourcen finden Sie nützliche Informationen:

* [WebAIM: Echtzeit-Untertitelung](https://webaim.org/techniques/captions/realtime)
* [AccessIT (University of Washington): Können Untertitel automatisch über die Spracherkennung erstellt werden?](https://www.washington.edu/doit/programs/accessit?1209)

#### Weitere Informationen: Untertitel (Live) (1.2.4)     {#more-information-captions-live}

* [Erfolgskriterien 1.2.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html)
* [Erfolgskriterien 1.2.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-media-equiv-real-time-captions)

### Audiobeschreibung (aufgezeichnet) (1.2.5)          {#audio-description-pre-recorded}

* Erfolgskriterium 1.2.5
* Level AA
* Audiobeschreibung (aufgezeichnet): Audiobeschreibung wird für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#purpose-audio-description-pre-recorded}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-pre-recorded), mit dem Unterschied, dass Autoren eine wesentlich detailliertere Audiobeschreibung verfassen müssen, um Level AA zu erfüllen.

#### Erfüllen: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#how-to-meet-audio-description-pre-recorded}

Befolgen Sie die Anweisungen für [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audio-description-or-media-alternative-pre-recorded).

#### Weitere Informationen: Audiobeschreibung (aufgezeichnet) (1.2.5)     {#more-information-audio-description-pre-recorded}

* [Erfolgskriterien 1.2.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html)
* [Erfolgskriterien 1.2.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-media-equiv-audio-desc-only)

### Anpassbar (1.3) {#adaptable}

[Richtlinie 1.3 Anpassbar: Erstellen Sie Inhalte, die auf unterschiedliche Weise präsentiert werden können (z. B. einfacheres Layout), ohne Informationen oder Struktur zu verlieren.](https://www.w3.org/TR/WCAG20/#content-structure-separation)

Diese Richtlinie deckt die Anforderungen ab, die zur Unterstützung der folgenden Personen erforderlich sind:

* Personen, die möglicherweise nicht in der Lage sind, auf Informationen zuzugreifen, die von einem Autor oder einer Autorin in einem *standardmäßigen* zweidimensionalen, mehrspaltigen, farbigen Web-Seiten-Layout präsentiert werden

* Personen, die eine Nur-Audio-Darstellung oder alternative visuelle Darstellung wie Großdruck oder hohen Kontrast verwenden wollen.

### Informationen und Beziehungen (1.3.1)              {#info-and-relationships}

* Erfolgskriterium 1.3.1
* Level A
* Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmgesteuert bestimmt werden oder sind im Text verfügbar.

#### Zweck: Informationen und Beziehungen (1.3.1) {#purpose-info-and-relationships}

Viele Hilfstechnologien, die von Menschen mit Behinderungen genutzt werden, sind auf strukturelle Informationen angewiesen, damit Inhalte effektiv angezeigt oder ausgegeben werden können. Diese Strukturinformationen können in Form von Seitenüberschriften, Tabellenzeilen und Spaltenüberschriften sowie Listentypen vorliegen. Beispielsweise könnte eine Bildschirmlesehilfe einer Benutzerin bzw. einem Benutzer die Navigation durch eine Seite von einer Überschrift zur nächsten ermöglichen. Wenn Seiteninhalte jedoch nur über visuelles Design und nicht über das zugrunde liegende HTML strukturiert zu sein scheinen, stehen für Hilfstechnologien keine Strukturinformationen zur Verfügung, was Fähigkeit einschränkt, ihnen das Browsen zu erleichtern.

Dieses Erfolgskriterium besteht, um sicherzustellen, dass derartige Strukturinformationen über HTML bereitgestellt werden, damit die Browser und Hilfstechnologien auf die Informationen zugreifen und davon profitieren können.

#### Erfüllen: Informationen und Beziehungen (1.3.1)       {#how-to-meet-info-and-relationships}

AEM erleichtert den Aufbau von Web-Seiten mit den entsprechenden HTML-Elementen. Öffnen Sie Ihren Seiteninhalt im RTE (eine Text-Komponente), und geben Sie im Menü **Format** das entsprechende Strukturelement (zum Beispiel Absatz und Überschrift) an.

Das folgende Bild zeigt einen Text, der als Absatztext formatiert wurde. Der verwendete Quell-Code zeigt die korrekten Anfangs- und End-Tags &lt;p> und &lt;/p>.

![Ein Beispiel des Absatz-Elements im Modus zur Bearbeitung des Quell-Codes (klassische Benutzeroberfläche).](assets/chlimage_1-18a.png)

Sie können folgendermaßen sicherstellen, dass Ihre Web-Seiten die entsprechende Struktur erhalten:

* **Verwendung von Überschriften:**

Sofern Sie die Funktionen für Barrierefreiheit des RTE aktiviert haben (siehe [AEM und Barrierefreiheit](/help/sites-administering/rte-accessible-content.md)), bietet AEM drei Ebenen für Seitenüberschriften. Sie können diese verwenden, um Abschnitte und Unterabschnitte des Inhalts zu identifizieren. Überschrift 1 ist die höchste Überschriftenstufe und Stufe 3 die niedrigste. Der Systemadministrator kann das System so konfigurieren, dass mehr Überschriftenstufen verwendet werden können.

Im folgenden Bild ist ein Beispiel der verschiedenen Überschriftentypen zu sehen.

![Überschrift H1 bis H3 in der Dropdown-Auswahl (klassische Benutzeroberfläche).](assets/chlimage_1-19a.png)

* **Hervorgehobener Text**:

Verwenden Sie das Element &lt;strong> oder &lt;em>, um eine Hervorhebung anzugeben. Verwenden Sie keine Überschriften zum Hervorheben von Text in Absätzen.

    * Markieren Sie den Text, den Sie hervorheben möchten;
    * Klicken Sie auf das **B**-Symbol (für &lt;strong>) oder das **I**-Symbol (für &lt;em>), das im Fenster **Eigenschaften** angezeigt wird (stellen Sie sicher, dass HTML ausgewählt ist).

>[!NOTE]
>
>RTE ist in einer Standardinstallation von AEM wie folgt eingerichtet:
>
>* &lt;b> für &lt;strong>
* &lt;i> für &lt;em>
  >
Sie haben die gleiche Wirkung, doch &lt;strong> und &lt;em> sollten bevorzugt werden, weil sie semantisch korrekt für HTML sind. Bei der Entwicklung Ihrer Projektinstanz kann Ihr Entwicklungs-Team den RTE so konfigurieren, dass er &lt;strong> und &lt;em> (anstelle von &lt;b> und &lt;i>) verwendet.

* **Listen verwenden**: Mit HTML können Sie drei verschiedene Arten von Listen angeben:

   * Das Element `<ul>` wird für *nicht geordnete* Listen (Aufzählungslisten) verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet.

   Verwenden Sie in RTE das Symbol **Aufzählung**.

   * Das Element `<ol>` wird für *nummerierte* Listen verwendet. Einzelne Listenelemente werden mit dem Element `<li>` gekennzeichnet.

   Verwenden Sie in RTE das Symbol **Nummerierte Liste**.

Wenn Sie vorhandene Inhalte in einen bestimmten Listentyp ändern möchten, markieren Sie den entsprechenden Text und wählen Sie den entsprechenden Listentyp aus. Wie im vorherigen Beispiel, das zeigt, wie Absatztext eingegeben wird, werden die entsprechenden Listenelemente automatisch zu Ihrem HTML hinzugefügt. Sie können dies jedoch in der Ansicht der Quellbearbeitung anzeigen.

>[!NOTE]
Das Element `<dl>` wird vom RTE nicht unterstützt.

* **Verwenden von Tabellen**:

Datentabellen müssen mit HTML-Tabellenelementen gekennzeichnet sein:

    * ein Element `&lt;table>`
    * ein Element `&lt;tr>` für jede Zeile der Tabelle
    * ein Element `&lt;th>` für jede Zeilen- und Spaltenüberschrift
    * ein Element `&lt;td>` für jede Datenzelle

>[!NOTE]
Tabellen sollten mit der Komponente **Tabelle** umgesetzt werden. Obwohl Tabellen in der Textkomponente erstellt werden können, wird dieses Verfahren nicht empfohlen.

Barrierefreie Tabellen verwenden außerdem die folgenden Elemente und Attribute:

    * Das Element `&lt;caption>` wird verwendet, um eine sichtbare Beschriftung für die Tabelle zu liefern. Beschriftungen werden standardmäßig zentriert über der Tabelle angezeigt, können jedoch mithilfe von CSS entsprechend positioniert werden. Die Beschriftung wird programmgesteuert mit der Tabelle verknüpft. Daher ist sie eine nützliche Methode, um eine Einführung in Inhalte zu bieten.
    * Das Element `&lt;h3 class=&quot;summary&quot;>` hilft nicht sehenden Benutzerinnen und Benutzern, die in einer Tabelle dargestellten Informationen leichter zu verstehen, indem es eine Zusammenfassung dessen liefert, was sehende Menschen sehen können. Dies ist besonders nützlich bei komplexen oder unkonventionellen Tabellen-Layouts (dieses Attribut wird nicht im Browser angezeigt, sondern nur für Hilfstechnologien ausgelesen).
    * Das Attribut `scope` des Elements `&lt;th>` wird verwendet, um anzugeben, ob eine Zelle eine Überschrift für eine bestimmte Zeile oder eine bestimmte Spalte darstellt. Auf ähnliche Weise können die Überschrift und ID-Attribute in komplexen Tabellen verwendet werden, bei denen Datenzellen mit einer oder mehreren Überschriften verknüpft sein können.

>[!NOTE]
Diese Elemente und Attribute sind standardmäßig nicht direkt verfügbar, doch Systemadmins können Unterstützung für diese Werte im Dialogfeld **Tabelleneigenschaften** hinzufügen (siehe [Hinzufügen von Unterstützung für zusätzliche HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

Beim Hinzufügen einer **Tabelle** können Sie die **Tabelleneigenschaften** über das Dialogfeld konfigurieren.

    * eine geeignete **Beschriftung**.
    * Entfernen Sie idealerweise alle Standardwerte für **Breite**, **Höhe**, **Rahmen**, **Zellenauffüllung**, **Zellenabstand**, da diese Eigenschaften in einem globalen Stylesheet festgelegt werden können.

![Dialogfeld „Tabelleneigenschaften“](assets/chlimage_1-20a.png)

Anschließend können Sie im Dialogfeld **Zelleneigenschaften** auswählen, ob die Zelle eine Daten- oder Überschriftzelle ist und ob im Fall einer Überschriftzelle sich diese auf eine Zeile oder Spalte oder beides bezieht:

![Dialogfeld „Zelleneigenschaften“; Festlegen einer Zeile (normalerweise die erste Zeile) als Überschriftzeile.](assets/chlimage_1-21a.png)

* **Komplexe Datentabellen:**

In einigen Fällen, in denen komplexe Tabellen mit zwei oder mehr Überschriftenebenen vorhanden sind, reicht das normale Dialogfeld „Tabelleneigenschaften“ nicht aus, um alle benötigten Strukturinformationen anzugeben. Für diese Art von komplexen Tabellen müssen direkte Beziehungen zwischen den Überschriften und den zugehörigen Zellen mithilfe der Attribute **Überschrift** und **ID** hergestellt werden. Beispielsweise werden in der Tabelle unten Überschriften und IDs zugeordnet, um eine programmgesteuerte Verbindung für Benutzer von Hilfstechnologien herzustellen.

>[!NOTE]
Das ID-Attribut ist in einer vorkonfigurierten Installation nicht verfügbar. Es kann durch die Konfiguration von HTML-Regeln und des Serialisierungsprogramms im RTE aktiviert werden.

>[!NOTE]
Tabellen sollten mit der Komponente **Tabelle** umgesetzt werden. Obwohl Tabellen in der Textkomponente erstellt werden können, wird dieses Verfahren nicht empfohlen.

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
Diese Funktion ist in einer Standardinstallation nicht sofort verfügbar. Sie erfordert die Konfiguration des RTE, HTML-Regeln und ein Serialisierungsprogramm.

#### Weitere Informationen: Informationen und Beziehungen (1.3.1) {#more-information-info-and-relationships}

* [Erfolgskriterien 1.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
* [Erfolgskriterien 1.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-content-structure-separation-programmatic)

### Sensorische Eigenschaften (1.3.3)          {#sensory-characteristics}

* Erfolgskriterium 1.3.3
* Level A
* Sensorische Eigenschaften: Anweisungen, die zum Verstehen und Bedienen von Inhalt verfügbar sind, beziehen sich nicht nur auf sensorische Eigenschaften der Komponenten wie Form, Größe, visuelle Position, Ausrichtung oder Klang.

#### Zweck: Sensorische Eigenschaften (1.3.3) {#purpose-sensory-characteristics}

Entwickler nutzen bei der Präsentation von Informationen oft visuelle Design-Mittel wie Farbe, Form, Textstil oder die absolute oder relative Position eines Inhaltselements. Hierbei kann es sich um leistungsstarke Design-Techniken zur Informationsübermittlung handeln. Blinde oder sehbehinderte Personen können möglicherweise nicht auf Informationen zugreifen, die eine visuelle Identifizierung von Attributen wie Position, Farbe oder Form erfordern.

Entsprechend sind Informationen, für die zwischen verschiedenen Klängen unterschieden werden muss (z. B. Inhalte, die von einer Frau oder einem Mann gesprochen werden), für Menschen mit eingeschränktem Hörvermögen nicht verfügbar, wenn sie nicht in Textalternativen für den Audioinhalt umgesetzt wurden.

>[!NOTE]
Die Anforderungen, die sich auf die Alternativen für Farben beziehen, finden Sie unter [Verwendung von Farbe](#use-of-color).

#### Erfüllen: Sensorische Eigenschaften (1.3.3) {#how-to-meet-sensory-characteristics}

Stellen Sie sicher, dass alle Informationen, die sich auf visuelle Eigenschaften des Seiteninhalts stützen, auch in einem alternativen Format angezeigt werden.

* Verlassen Sie sich nicht auf die visuelle Position, um Informationen anzugeben. Wenn Sie beispielsweise Benutzerinnen und Benutzer auf ein Menü rechts auf der Seite verweisen möchten, über das sie auf weitere Informationen zugreifen können, verweisen Sie nicht auf *das Menü rechts*, sondern benennen Sie stattdessen das Menü (z. B. mit einer Überschrift) und verweisen Sie im Text auf diesen Namen.
* Verlassen Sie sich nicht auf den Textstil (z. B. fett oder kursiv gedruckter Text) als einzige Methode zur Vermittlung von Informationen.

>[!NOTE]
Die Verwendung beschreibender Begriffe ist zulässig, wenn sie in einem nicht visuellen Kontext eine Bedeutung haben. Beispielsweise ist die Verwendung von *über* und *unter* im Allgemeinen akzeptabel, da sie jeweils Inhalte vor und nach einem bestimmten Inhaltselement implizieren. Es wäre immer noch sinnvoll, wenn der Inhalt laut gesprochen wird.

#### Weitere Informationen – Sensorische Eigenschaften (1.3.3) {#more-information-sensory-characteristics}

* [Erfolgskriterien 1.3.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html)
* [Erfolgskriterien 1.3.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-content-structure-separation-understanding)

### Unterscheidbar (1.4) {#distinguishable}

[Richtlinie 1.4 Unterscheidbar: Erleichtern Sie den Benutzern das Sehen und Hören von Inhalt einschließlich der Unterscheidung von Vorder- und Hintergrund.](https://www.w3.org/TR/WCAG20/#visual-audio-contrast)

### Verwendung von Farbe (1.4.1)  {#use-of-color}

* Erfolgskriterium 1.4.1
* Level A
* Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel zur Informationsübermittlung, zur Angabe einer Aktion, zur Aufforderung einer Antwort oder zur Unterscheidung eines visuellen Elements verwendet.

>[!NOTE]
Dieses Erfolgskriterium bezieht sich speziell auf die Farbwahrnehmung. Andere Wahrnehmungsformen werden in [Anpassbar (1.3)](#adaptable) behandelt, einschließlich des programmgesteuerten Zugriffs auf Farbe und andere visuelle Darstellungscodierungen.

#### Zweck - Verwendung von Farbe (1.4.1) {#purpose-use-of-color}

Farbe bietet eine effektive Möglichkeit, die Ästhetik von Web-Seiten zu verbessern, und kann auch die Vermittlung von Informationen unterstützen. Es gibt jedoch eine Reihe visueller Beeinträchtigungen, von Blindheit bis hin zu Farbsehschwächen, was bedeutet, dass einige Menschen nicht in der Lage sind, zwischen bestimmten Farben zu unterscheiden. Dieses Problem macht die Farbcodierung zu einer unzuverlässigen Methode bei der Bereitstellung von Informationen.

So kann beispielsweise jemand mit einer Rot-Grün-Sehschwäche nicht zwischen Grün- und Rottönen unterscheiden. Sie sehen möglicherweise beide Farben als eine dritte Farbe (z. B. Braun) und können in diesem Fall nicht zwischen Rot, Grün und Braun unterscheiden.

Außerdem kann Farbe nicht von Personen wahrgenommen werden, die reine Text-Browser oder monochrome Anzeigegeräte verwenden oder einen Schwarz-Weiß-Ausdruck der Seite betrachten.

#### Erfüllen: Verwendung von Farbe (1.4.1) {#how-to-meet-use-of-color}

Immer wenn Farbe verwendet wird, um Informationen zu vermitteln, müssen Sie sicherstellen, dass die verfügbaren Informationen auch verfügbar sind, wenn die Farbe nicht sichtbar ist.

Stellen Sie z. B. sicher, dass die durch die Farbe vermittelte Information auch explizit im Text enthalten ist. Die folgende Abbildung zeigt, wie sowohl Farbe als auch Text die Verfügbarkeit von Sitzplätzen für eine Aufführung anzeigen:

<table>
 <tbody>
  <tr>
   <td><p><strong>Leistung</strong></p> </td>
   <td><p><strong>Verfügbarkeit</strong></p> </td>
  </tr>
  <tr>
   <td><p>Dienstag, 16. März<sup></sup></p> </td>
   <td><p>SITZPLÄTZE VERFÜGBAR</p> </td>
  </tr>
  <tr>
   <td><p>Mittwoch, 17. März<sup></p> </td>
   <td><p>SITZPLÄTZE VERFÜGBAR</p> </td>
  </tr>
  <tr>
   <td><p>Donnerstag, 18. März<sup></sup></p> </td>
   <td><p>AUSVERKAUFT</p> </td>
  </tr>
 </tbody>
</table>

Wenn Farbe als Hinweis für die Bereitstellung von Informationen verwendet wird, sollten Sie einen weiteren visuellen Hinweis einsetzen, etwa durch Änderung des Stils (z. B. fett, kursiv) oder der Schriftart. Dies hilft Menschen mit schlechtem Sehvermögen oder einer beeinträchtigten Farbwahrnehmung, die Information zu erkennen. Man darf sich jedoch nicht vollständig auf diese Maßnahmen verlassen, da sie für Menschen, die die Seite überhaupt nicht sehen können, keine Hilfe bieten.

#### Weitere Informationen – Verwendung von Farbe (1.4.1) {#more-information-use-of-color}

* [Erfolgskriterien 1.4.1 verstehen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Erfolgskriterien 1.4.1 erfüllen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Anleitung für das Erzielen eines Kontrastverhältnisses von 3:1 mit einer Liste Web-sicherer Farben](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)

### Kontrast (Minimum) (1.4.3) {#contrast-minimum}

* Erfolgskriterium 1.4.3
* Level AA
* Kontrast (Minimum): Die visuelle Darstellung von Text und Abbildungen von Text hat ein Kontrastverhältnis von mindestens 4,5:1, mit den folgenden Ausnahmen:

   * Großer Text: Großformatiger Text und Bilder von großformatigem Text weisen ein Kontrastverhältnis von mindestens 3:1 auf.
   * Beiläufig: Für Text oder Textbilder, die Teil einer inaktiven Komponente der Benutzeroberfläche sind, die reine Dekoration darstellen, die für niemanden sichtbar sind oder die Teil eines Bildes sind, das signifikanten anderen visuellen Inhalt enthält, ist kein Kontrast erforderlich.
   * Firmenschriftzüge: Für Text, der Teil eines Logos oder eines Markennamens ist, gibt es keine Kontrastanforderungen.

#### Zweck - Kontrast (Minimum) (1.4.3)       {#purpose-contrast-minimum}

Menschen mit bestimmten Sehbehinderungen können möglicherweise nicht zwischen bestimmten Farbpaaren mit geringem Kontrast unterscheiden. Diese Menschen können Barrierefreiheitsprobleme haben, wenn:

* Wenn zwischen dem Text und der Hintergrundfarbe nur wenig Kontrast besteht.
* Die Farbcodierung von Text (z. B. Link-Text und Nicht-Link-Text) für die Unterscheidung von Informationen wichtig ist.

>[!NOTE]
Text, der für rein dekorative Zwecke verwendet wird, ist von diesem Erfolgskriterium ausgeschlossen.

#### Erfüllen - Kontrast (Minimum) (1.4.3) {#how-to-meet-contrast-minimum}

Achten Sie darauf, dass der Text einen ausreichenden Kontrast zu seinem Hintergrund aufweist. Die Kontrastverhältnisse hängen von der Größe und dem Stil des jeweiligen Textes ab:

* Für Text mit einer Größe von weniger als 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis zwischen Text/Bildern mit Text und dem Hintergrund mindestens 4,5:1 betragen.
* Bei Text mit einer Größe von mindestens 18 Punkten (oder 14 Punkten und fett) sollte das Kontrastverhältnis mindestens 3:1 betragen.
* Wenn ein Hintergrund gemustert ist, sollte der Hintergrund um jeden Text schattiert werden, sodass das Verhältnis von 4,5:1 bzw. 3:1 beibehalten wird.

Verwenden Sie ein Farbkontrast-Tool, um das Kontrastverhältnis zu prüfen, z. B. den [Farbkontrast-Analysator der Paciello Group](https://www.paciellogroup.com/resources/contrast-analyser.html) oder den [Farbkontrast-Checker von WebAIM](https://webaim.org/resources/contrastchecker/). Diese Tools können Farbpaare überprüfen und über eventuelle Kontrastprobleme berichten.

Wenn Sie weniger daran interessiert sind, das Erscheinungsbild Ihrer Seite festzulegen, können Sie auch wählen, dass keine Farben für Hintergrund- und Vordergrundtext festgelegt werden. Es ist keine Kontrastprüfung erforderlich, da es der Browser der Benutzerin bzw. des Benutzers ist, der die Farben für den Text und den Hintergrund bestimmt.

Wenn es nicht möglich ist, die empfohlenen Kontraststufen zu erreichen, stellen Sie einen Link zu einer alternativen, gleichwertigen Version der Seite bereit (die keine Farbkontrastprobleme aufweist). Oder lassen Sie die Benutzenden den Kontrast des Seitenfarbschemas an ihre eigenen Anforderungen anpassen.

#### Weitere Informationen - Kontrast (Minimum) (1.4.3) {#more-information-contrast-minimum}

* [Erfolgskriterien 1.4.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)
* [Erfolgskriterien 1.4.3 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-visual-audio-contrast-contrast)

### Bilder von Text (1.4.5)     {#images-of-text}

* Erfolgskriterium 1.4.5
* Level AA
* Bilder von Text: Falls die verwendeten Technologien die visuelle Präsentation realisieren können, wird für die Vermittlung von Informationen Text verwendet – keine Bilder von Text. Dabei gelten folgende Ausnahmen:

   * Anpassbar: Das Textbild kann visuell an die Anforderungen der Benutzerin bzw. des Benutzers angepasst werden.
   * Wesentlich: Eine besondere Textdarstellung ist für die vermittelte Information von wesentlicher Bedeutung.

>[!NOTE]
Logotypen (Text, der Teil eines Logos oder Markennamen ist) werden als wesentlich betrachtet.

#### Zweck - Bilder von Text (1.4.5) {#purpose-images-of-text}

Bilder von Text werden häufig verwendet, wenn ein bestimmter Textstil bevorzugt wird, z. B. bei einem Firmenschriftzug oder wenn der Text aus einer anderen Quelle generiert wurde (etwa ein eingescanntes Papierdokument). Im Vergleich zu Text, der in HTML präsentiert und mit CSS formatiert wird, haben Textbilder jedoch nicht die Flexibilität, ihre Größe oder ihr Erscheinungsbild zu ändern, was für Menschen mit Sehbehinderungen oder Leseschwächen erforderlich sein kann.

#### Erfüllen - Bilder von Text (1.4.5) {#how-to-meet-images-of-text}

Wenn Bilder von Text verwendet werden müssen, nutzen Sie CSS, um die Bilder von Text in HTML durch einen identischen Text zu ersetzen, damit der Text in einer anpassbaren Version verfügbar ist. Ein Beispiel finden Sie unter [C30: Verwenden von CSS zum Ersetzen von Text durch Bilder von Text und Bereitstellen von Steuerelementen für die Benutzeroberfläche zum Umschalten](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Weitere Informationen: Bilder von Text (1.4.5) {#more-information-images-of-text}

* [Erfolgskriterien 1.4.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html)
* [Erfolgskriterien 1.4.5 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-visual-audio-contrast-text-presentation)

## Grundsatz 2: Bedienbar {#principle-operable}

[Grundsatz 2: Bedienbar – Komponenten der Benutzerschnittstelle und der Navigation müssen bedienbar sein.](https://www.w3.org/TR/WCAG20/#operable)

### Pausieren, Beenden, Ausblenden (2.2.2)          {#pause-stop-hide}

* Erfolgskriterium 2.2.2
* Level A
* Pausieren, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln:

   * Bewegt, blinkend, rollend: Für bewegte, blinkende oder rollende Informationen, die (a) automatisch gestartet werden, (b) länger als fünf Sekunden dauern und (c) parallel zu anderen Inhalten präsentiert werden, gibt es einen Mechanismus, mit dem Benutzende sie pausieren, beenden oder ausblenden können, es sei denn, die Bewegung, das Blinken bzw. das Rollen ist ein wesentlicher Teil einer Aktivität.
   * Automatische Aktualisierung: Für alle automatisch aktualisierten Informationen, die (a) automatisch gestartet und (b) parallel zu anderen Inhalten angezeigt werden, gibt es einen Mechanismus, mit dem Benutzende sie pausieren, beenden oder ausblenden oder die Häufigkeit der Aktualisierung steuern können, es sei denn, die automatische Aktualisierung ist ein wesentlicher Teil einer Aktivität.

Beachten Sie Folgendes:

1. Die Anforderungen für flackernden oder blinkenden Inhalt finden Sie unter [Gestalten Sie Inhalte nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen (2.3)](#seizures).
1. Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Web-Seite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht-Interferenz](https://www.w3.org/TR/WCAG20/#cc5).
1. Für Inhalte, die regelmäßig durch Software aktualisiert werden oder an den Benutzeragenten gestreamt werden, müssen Informationen, die zwischen der Initiierung der Pause und der Wiederaufnahme der Präsentation generiert oder empfangen wurden, nicht beibehalten oder präsentiert werden, da dies möglicherweise technisch nicht möglich ist und in vielen Situationen sogar irreführend sein könnte.
1. Eine Animation, die im Rahmen einer Vorausladephase oder einer ähnlichen Situation auftritt, kann als wesentlich angesehen werden, wenn während dieser Phase keine Interaktion für alle Benutzenden stattfinden kann und wenn eine Nichtanzeige des Fortschritts die Benutzenden verwirren oder zu der Annahme führen könnte, dass der Inhalt eingefroren oder unterbrochen ist.

#### Zweck - Pausieren, Beenden, Ausblenden (2.2.2) {#purpose-pause-stop-hide}

Bestimmte Benutzerinnen oder Benutzer empfinden bewegte Inhalte als störend und haben Schwierigkeiten, sich auf andere Bereiche der Seite zu konzentrieren. Darüber hinaus sind solche Inhalte für Menschen schwierig, die beim Lesen Probleme haben, bewegtem Text zu folgen.

#### Erfüllen: Pausieren, Beenden, Ausblenden (2.2.2) {#how-to-meet-pause-stop-hide}

Abhängig von der Art des Inhalts können Sie beim Erstellen von Web-Seiten mit sich bewegendem, aufblitzendem oder blinkendem Inhalt die folgenden Empfehlungen beachten:

* Bieten Sie die Möglichkeit, das Scrollen von Inhalten anzuhalten, damit Benutzerinnen und Benutzer genügend Zeit zum Lesen haben. Beispielsweise Nachrichten-Ticker oder automatisch aktualisierter Text.
* Stellen Sie sicher, dass blinkende Inhalte maximal fünf Sekunden lang blinken.
* Nutzen Sie Technologien, mit denen die Anzeige von blinkenden Inhalten im Browser deaktiviert werden kann, z. B. Dateien im GIF- (Graphics Interchange Format) oder APNG-Format (Animated Portable Network Graphics).
* Stellen Sie ein Formularsteuerelement auf der Web-Seite bereit, mit dem Benutzerinnen und Benutzer alle blinkenden Inhalte auf der Seite deaktivieren können.
* Wenn dies nicht möglich ist, geben Sie einen Link zu einer Seite an, die den gesamten Inhalt enthält, aber ohne Blinken.

#### Weitere Informationen - Pausieren, Beenden, Ausblenden (2.2.2)       {#more-information-pause-stop-hide}

* [Erfolgskriterium 2.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)
* [Erfolgskriterium 2.2.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-time-limits-pause)

### Anfälle (2.3)     {#seizures}

[Richtlinie 2.3 Anfälle: Gestalten Sie Inhalt nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen.](https://www.w3.org/TR/WCAG20/#seizure)

### Grenzwert von maximal dreimaligem Blitzen (2.3.1)     {#three-flashes-or-below-threshold}

* Erfolgskriterium 2.3.1
* Level A
* Drei Blitze oder Unterschreitung des Schwellenwerts: Web-Seiten enthalten keine Elemente, die innerhalb einer Sekunde mehr als dreimal aufblitzen, oder die Aufblitzfrequenz liegt unter den Schwellenwerten für allgemeines Blitzen und rotes Blitzen.

>[!NOTE]
Da jeder Inhalt, der dieses Erfolgskriterium nicht erfüllt, die Fähigkeit der Benutzenden beeinträchtigen kann, die gesamte Seite zu nutzen, müssen alle Inhalte auf der Web-Seite (unabhängig davon, ob sie zur Erfüllung anderer Erfolgskriterien verwendet werden oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht-Interferenz](https://www.w3.org/TR/WCAG20/#cc5).

#### Zweck – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bestimmten Fällen können aufblitzende Inhalte photosensitive Anfälle auslösen. Dieses Erfolgskriterium ermöglicht Benutzenden den Zugriff und die Nutzung des gesamten Inhalts ohne Beeinträchtigung durch aufblitzende Inhalte.

#### Erfüllen - Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Gehen Sie wie folgt vor:

* Stellen Sie sicher, dass Komponenten in einem Zeitraum von einer Sekunde nicht mehr als dreimal aufblitzen.
* Wenn die obige Bedingung nicht erfüllt werden kann, sollte der aufblitzende Inhalt innerhalb eines *kleinen sicheren Bereichs* in Pixeln auf dem Bildschirm angezeigt werden. Dieser Bereich wird anhand einer komplexen Formel berechnet, die unter [G176: Aufblitzende Bereiche ausreichend klein halten](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176) behandelt wird. Daher sollte diese Technik nur angewendet werden, wenn aufblitzende Inhalte erforderlich sind.

#### Weitere Informationen – Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Erfolgskriterium 2.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html)
* [Erfolgskriterium 2.3.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#seizure)

### Seite mit Titel versehen (2.4.2)          {#page-titled}

* Erfolgskriterium 2.4.2
* Level A
* Seite mit Titel versehen: Web-Seiten haben einen Titel, der das Thema oder den Zweck beschreibt

#### Zweck - Seite mit Titel versehen (2.4.2) {#purpose-page-titled}

Dieses Erfolgskriterium ist – unabhängig von etwaigen Beeinträchtigungen – für alle Benutzenden hilfreich, um schnell den Inhalt einer Web-Seite zu ermitteln, ohne die Seite vollständig zu lesen. Dieses Design ist nützlich, wenn mehrere Web-Seiten in Browser-Registerkarten geöffnet sind, da der Seitentitel auf den Registerkarten angezeigt wird, was die Seiten schnell auffindbar macht.

#### Erfüllen: Seite mit Titel versehen (2.4.2) {#how-to-meet-page-titled}

Wenn Sie in AEM eine neue HTML-Seite erstellen, können Sie den Seitentitel angeben. Achten Sie darauf, dass der Titel den Inhalt der Seite angemessen beschreibt, damit die Besuchenden schnell erkennen können, ob der Inhalt für ihre Bedürfnisse relevant ist.

Sie können den Seitentitel auch gemeinsam mit der Seite bearbeiten, indem Sie **Sidekick** > Registerkarte **Seite** > **Seiteneigenschaften...** auswählen.

#### Weitere Informationen – Seite mit Titel versehen (2.4.2) {#more-information-page-titled}

* [Erfolgskriterium 2.4.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html)
* [Erfolgskriterium 2.4.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-navigation-mechanisms-title)

### Link-Zweck (im Kontext) (2.4.4)          {#link-purpose-in-context}

* Erfolgskriterium 2.4.4
* Level A
* Link-Zweck (im Kontext): Der Zweck jedes Links kann allein durch den Link-Text oder durch den Link-Text zusammen mit dem programmgesteuert festgelegten Link-Kontext bestimmt werden. Eine Ausnahme bilden Fälle, in denen der Zweck des Links für Benutzende im Allgemeinen mehrdeutig ist.

#### Zweck: Link-Zweck (im Kontext) (2.4.4) {#purpose-link-purpose-in-context}

Unabhängig von etwaigen Beeinträchtigungen ist es für alle Benutzerinnen und Benutzer von entscheidender Bedeutung, dass durch einen passenden Link-Text klar erkenntlich ist, wohin ein Link führt. Dieses Design hilft Benutzenden bei der Entscheidung, ob sie einem Link tatsächlich folgen möchten. Für sehende Personen ist ein aussagekräftiger Link-Text nützlich, wenn sich auf einer Seite mehrere Links befinden (vor allem, wenn eine Seite sehr viel Text enthält), da ein aussagekräftiger Link-Text einen deutlicheren Hinweis auf die Funktion der Zielseite liefert. Benutzende von Hilfstechnologien, die eine Liste aller Links auf einer Seite erstellen können, können den Linktext hingegen leichter aus dem Kontext heraus verstehen.

#### Erfüllen - Link-Zweck (im Kontext) (2.4.4)       {#how-to-meet-link-purpose-in-context}

Stellen Sie vor allem sicher, dass der Link-Text den Zweck eines Links eindeutig beschreibt.

* Schlechtes Beispiel:

   * Text: Einzelheiten zu unseren Abendkursen im Herbst 2010 finden Sie hier.
   * Grund: Es geht nicht deutlich und unmissverständlich hervor wohin der Link führt.

* Gutes Beispiel:

   * Text: Abendkurse im Herbst 2010 – Details.
   * Grund: Durch eine kleine Anpassung des Textes und der Position des Linkelements lässt sich der Link-Text verbessern:

Links sollten auf den Seiten eine konsistente Bezeichnung erhalten. Dies gilt insbesondere für Navigationsleisten. Wenn ein Link zu einer bestimmten Seite z. B. auf einer Seite **Publikationen** heißt, dann sollte er auch auf allen anderen Seiten denselben Namen erhalten.

Zum Zeitpunkt des Schreibens gibt es jedoch einige Probleme im Zusammenhang mit der Verwendung von Titeln:

* Im Title-Attribut enthaltener Text ist in der Regel nur für Mausbenutzer als QuickInfo-Popup verfügbar. Über eine Tastatur ist kein Zugriff möglich.
* Bildschirmlesehilfen können Titelattribute vorlesen, diese Funktion ist jedoch möglicherweise nicht standardmäßig aktiviert, sodass Benutzende vielleicht nicht wissen, dass ein Titelattribut vorhanden ist.
* Es ist schwierig, das Erscheinungsbild des Titeltextes zu ändern, was bedeutet, dass es für einige Personen schwierig oder unmöglich sein könnte, ihn zu lesen.

Das Title-Attribut kann also genutzt werden, um zusätzlichen Kontext zu einem Link bereitzustellen, Sie sollten aber diese Einschränkungen bedenken und es daher nicht als Alternative für einen geeigneten Link-Text nutzen.

Wenn ein Link aus einem Bild besteht, müssen Sie sicherstellen, dass der Alternativtext für das Bild tatsächlich das Ziel des Links beschreibt. Wenn z. B. ein Bild eines Bücherregals als Link zu den Publikationen einer Person festgelegt wird, sollte der Alternativtext **Publikationen von John Smith** lauten und nicht **Bücherregal**.

Wenn der Link-Anker alternativ Text enthält, der den Zweck des Links zusätzlich zum Bildelement beschreibt (und der Text daher neben dem Bild angezeigt wird), verwenden Sie ein leeres Alternativattribut für das Bild:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith's publications
</a>
```

>[!NOTE]
Das obige Snippet ist eine Illustration. Es wird empfohlen, die **Bildkomponente** zu verwenden.

Auch wenn empfohlen wird, einen Link-Text bereitzustellen, der den Zweck des Links verdeutlicht, ohne zusätzlichen Kontext zu benötigen, gibt es Fälle, in denen dies nicht möglich ist. Links ohne Kontext können in den folgenden Fällen verwendet werden. HTML-Beispiele hierzu finden Sie unter [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-navigation-mechanisms-refs).

* Wenn der Link-Text zu einer Liste eng zusammenhängender Links gehört und das den Link umgebende Listenelement ausreichend Kontext liefert.
* Wenn der Zweck eines Links aus dem *vorangehenden* (nicht dem nachfolgenden) Text des Absatzes klar hervorgeht.
* Wenn der Link in einer Datentabelle enthalten ist und der Zweck daher anhand der zugehörigen Überschriften eindeutig identifiziert werden kann.
* Wenn eine Liste von Links in einem Satz von Überschriften enthalten ist und die Überschrift selbst den passenden Kontext bietet.
* Wenn eine Liste von Links in einem verschachtelten Link enthalten ist und das dem verschachtelten Link übergeordnete Listenelement den passenden Kontext bietet.

In einigen Fällen, in denen sich mehrere Links auf einer Seite befinden (von denen jeder das Ziel des Links durch komplexe, aber erforderliche Details angibt), kann es sinnvoll sein, eine alternative Version der Web-Seite anzubieten, die denselben Inhalt anzeigt, auf der der Link-Text jedoch weniger ausführlich ist.

Alternativ können Skripte verwendet werden. Dabei wird im Link selbst ein minimaler Text bereitgestellt. Bei der Aktivierung des entsprechenden Steuerelements im oberen Bereich der Seite wird der Link-Text jedoch *erweitert* und es werden mehr Details angezeigt. Einen ähnlichen Ansatz bietet die Verwendung von CSS, um den vollständigen Link für sehende Benutzerinnen und Benutzer *auszublenden*, ihn jedoch für Menschen, die die Sprachausgabe nutzen, auszugeben. Dies überschreitet den Rahmen dieses Dokuments, doch finden Sie weitere Informationen hierzu unter [Weitere Informationen: Link-Zweck (im Kontext) (2.4.4)](#more-information-link-purpose-in-context).

#### Weitere Informationen – Link-Zweck (im Kontext) (2.4.4) {#more-information-link-purpose-in-context}

* [Erfolgskriterium 2.4.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html)
* [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-navigation-mechanisms-refs)
* [C7: Verwendung von CSS, um einen Teil des Link-Textes auszublenden](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)

## Grundsatz 3: Verständlich     {#principle-understandable}

[Grundsatz 3: Verständlich – Informationen und die Bedienung der Benutzerschnittstelle müssen verständlich sein.](https://www.w3.org/TR/WCAG20/#understandable)

### Machen Sie Inhalt lesbar und verständlich (3.1) {#make-text-content-readable-and-understandable}

[Richtlinie 3.1 Lesbar: Machen Sie Inhalt lesbar und verständlich.](https://www.w3.org/TR/WCAG20/#meaning)

### Sprache der Seite (3.1.1) {#language-of-page}

* Erfolgskriterium 3.1.1
* Level A
* Sprache der Seite: Die voreingestellte menschliche Sprache einer Web-Seite kann programmatisch bestimmt werden.

#### Zweck - Sprache der Seite (3.1.1) {#purpose-language-of-page}

Mit diesem Erfolgskriterium soll sichergestellt werden, dass Text und andere sprachliche Inhalte korrekt wiedergegeben werden. Für Menschen, die eine Bildschirmlesehilfe nutzen, wird dadurch sichergestellt, dass der Inhalt korrekt ausgesprochen wird, während bei visuellen Browsern die Wahrscheinlichkeit höher ist, dass bestimmte Zeichensätze korrekt angezeigt werden.

#### Erfüllen - Sprache der Seite (3.1.1) {#how-to-meet-language-of-page}

Um dieses Erfolgskriterium zu erfüllen, kann die Standardsprache einer Web-Seite über das Attribut `lang` innerhalb des Elements `<html>` am Anfang der Seite festgelegt werden. Beispiel:

* Wenn eine Seite z. B. in britischem Englisch verfasst ist, sollte das Element `<html>` wie folgt angegeben werden:

`<html lang = "en-gb">`

* Wenn eine Seite hingegen als Seite in US-Englisch gerendert werden soll, ist folgende Angabe erforderlich:

`<html lang = "en-us">`

In AEM wird die Standardsprache einer Seite bei ihrer Erstellung festgelegt, kann aber auch bei ihrer Bearbeitung geändert werden. Öffnen Sie dazu den **Sidekick** > Registerkarte **Seite** > **Seiteneigenschaften…** > Registerkarte **Erweitert**.

#### Weitere Informationen – Sprache der Seite (3.1.1) {#more-information-language-of-page}

* [Erfolgskriterium 3.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html)
* [Erfolgskriterium 3.1.1 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-meaning-doc-lang-id)
* Die Codes basieren auf ISO 639-1. Eine ausführlichere Liste der Codes für jede Sprache finden Sie auf der [Website von W3 Schools](https://www.w3schools.com/tags/ref_language_codes.asp).

### Sprache von Teilen (3.1.2)  {#language-of-parts}

* Erfolgskriterium 3.1.2
* Level AA
* Sprache von Teilen: Die menschliche Sprache aller Abschnitte und Sätze im Inhalt kann programmatisch bestimmt werden. Ausgenommen sind Eigennamen, technische Fachbegriffe, Wörter einer unbestimmten Sprache und Wörter oder Wendungen, die Teil des Jargons des direkt umliegenden Textes sind.

#### Zweck - Sprache von Teilen (3.1.2) {#purpose-language-of-parts}

Der Zweck dieses Erfolgskriteriums ähnelt dem Zweck des Erfolgskriteriums [Sprache der Seite](#language-of-page). Es gilt jedoch für Web-Seiten, die auf einer Seite Inhalte im mehreren Sprachen enthalten (z. B. in Form von Zitaten oder wenig geläufigen Lehnwörtern).

Seiten, die dieses Erfolgskriterium anwenden, ermöglichen Folgendes:

* Braille-Transitions-Software zum Einfügen von Zeichen mit Akzenten.
* Bildschirmlesehilfen können Wörter, die nicht in der Standardsprache enthalten sind, korrekt aussprechen.
* Übersetzungs-Tools wie der Google Übersetzer können Inhalt korrekt von einer Sprache in eine andere übersetzen.

#### Erfüllen - Sprache von Teilen (3.1.2) {#how-to-meet-language-of-parts}

Mit dem `lang`-Attribut können Änderungen in Bezug auf die Sprache des Inhalts ermittelt werden. Ein deutschsprachiges Zitat (ISO 639-1-Code „de“) kann z. B. wie folgt angezeigt werden:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
Blockzitate werden in einer nativen Instanz nicht unterstützt. Es könnte eine benutzerdefinierte Komponente entwickelt werden, um diese Funktion zu unterstützen.

Auf ähnliche Weise kann der Browser ein wenig geläufiges Lehnwort oder eine Redewendung korrekt rendern, wenn das Element `span` wie folgt verwendet wird:

```xml
<p>The only French phrase I know is <span lang = "fr">je ne sais quoi</span>.</p>
```

>[!NOTE]
Dieses Erfolgskriterium muss nicht beachtet werden, wenn Namen oder Städte in verschiedenen Sprachen vorkommen oder wenn Sie Lehnwörter oder Redewendungen nutzen, die in der Standardsprache gängig geworden sind (wie *Schadenfreude* im Englischen).

Um ein span-Element mit der entsprechenden Sprache hinzuzufügen, können Sie Ihren HTML-Code im Bearbeitungsmodus für den Quelltext im RTE manuell bearbeiten, damit er wie oben aussieht. Alternativ kann ein Systemadministrator das `lang`-Attribut im RTE einfügen (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

#### Weitere Informationen – Sprache von Teilen (3.1.2) {#more-information-language-of-parts}

* [Erfolgskriterium 3.1.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.html)
* [Erfolgskriterium 3.1.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-meaning-other-lang-id)

### Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren (3.3)     {#help-users-avoid-and-correct-mistakes}

[Richtlinie 3.3 Hilfestellung bei der Eingabe: Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren.](https://www.w3.org/TR/WCAG20/#minimize-error)

### Beschriftungen oder Anweisungen (3.3.2)     {#labels-or-instructions}

* Erfolgskriterium 3.3.2
* Level A
* Kennzeichnungen oder Anweisungen: Kennzeichnungen oder Anweisungen werden bereitgestellt, wenn Inhalte Benutzereingaben erfordern.

#### Zweck - Beschriftungen oder Anweisungen (3.3.2) {#purpose-labels-or-instructions}

Die Bereitstellung von Anweisungen, die den Personen beim Ausfüllen von Formularen helfen, ist ein grundlegender Bestandteil der bewährten Verfahren für die Benutzerfreundlichkeit der Benutzeroberfläche. Dies ist hilfreich für Menschen mit visuellen oder kognitiven Beeinträchtigungen, die andernfalls Schwierigkeiten haben könnten, das Layout eines Formulars und die Art der Daten zu verstehen, die in einem bestimmten Formularfeld bereitgestellt werden sollen.

In AEM wird eine Standardbeschriftung eingefügt, wenn Sie eine Formularkomponente zur Seite hinzufügen, z. B. ein **Textfeld**. Dieser Standardtitel hängt vom Komponententyp ab. Sie können für dieses Feld einen eigenen Titel auf der Registerkarte **Titel und Text** des Dialogfelds „Bearbeiten“ hinzufügen. Es ist wichtig sicherzustellen, dass Benutzerinnen und Benutzer anhand von Kennzeichnungen die mit den einzelnen Formularkomponenten verknüpften Daten besser verstehen können.

![Registerkarte „Titel und Text“ (Dialogfeld „Bearbeiten“). Der Titel „Beschreibung“ wurde hinzugefügt.](assets/chlimage_1-22a.png)

Dieses Feld **Titel** muss für Feldelemente verwendet werden, da es eine Kennzeichnung bereitstellt, die für Hilfstechnologien verfügbar ist. Das einfache Schreiben einer Kennzeichnung in Text neben dem Feld reicht nicht aus.

Bei einigen Formularkomponenten ist es auch möglich, Kennzeichnungen mithilfe des Kontrollkästchens **Titel ausblenden** unsichtbar zu machen. Auf diese Weise ausgeblendete Kennzeichnungen sind weiterhin für Hilfstechnologien verfügbar, werden jedoch nicht auf dem Bildschirm angezeigt. Auch wenn dies in einigen Fällen ein guter Ansatz sein kann, ist es am besten, möglichst eine visuelle Bezeichnung einzufügen. Einige Benutzerinnen und Benutzer betrachten möglicherweise nur einen kleinen Bereich des Bildschirms (ein Feld nach dem anderen) und benötigen die Kennzeichnungen, um das Feld korrekt zu identifizieren.

#### Bild-Schaltflächen {#image-buttons}

Wenn Bild-Schaltflächen verwendet werden (z. B. die Komponente **Bild-Schaltfläche**) liefert das Feld **Titel** auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds den Alt-Text für das Bild und nicht die Beschriftung. Im folgenden Beispiel wurde daher für das Bild mit dem Text `Submit` im Bearbeitungsdialogfeld der Alt-Text `Submit` über das Feld **Titel** hinzugefügt.

![Schaltfläche „Bild“ mit im Feld „Titel“ festgelegtem Alt-Text (Dialogfeld „Bearbeiten“).](assets/chlimage_1-23a.png)

#### Gruppen von Formularfeldern {#groups-of-form-fields}

Bei einer Gruppe zusammengehöriger Steuerelemente, z. B. **Optionsfeldgruppe**, kann sowohl ein Titel für die Gruppe als auch für einzelne Steuerelemente erforderlich sein. Wenn Sie einen Satz Optionsfelder in AEM hinzufügen, gibt das Feld **Titel** diesen Gruppentitel an, während die einzelnen Titel beim Erstellen der Optionsfelder (**Elemente**) angegeben werden.

![Hinzufügen von Elementen zur Optionsfeldgruppe. Der Gruppentitel lautet „Contact me by“ - im Titel-Feld definiert.](assets/chlimage_1-24a.png)

Es gibt jedoch keine programmgesteuerte Zuordnung zwischen dem Gruppentitel und den Optionsschaltflächen. Der Titel muss beim Bearbeiten der Vorlage in die erforderlichen Tags `fieldset` und `legend` gesetzt werden, um diese Zuordnung herzustellen. Dies kann ausschließlich über die Bearbeitung des Quell-Codes der Seite erfolgen. Alternativ können Systemadmins die Unterstützung für diese Elemente hinzufügen, damit sie im Dialogfeld **Feldeigenschaften** angezeigt werden (siehe [Hinzufügen von Unterstützung für zusätzliche HTML-Elemente und -Attribute](/help/sites-administering/rte-accessible-content.md#add-support-for-more-html-elements-and-attributes)).

#### Weitere Aspekte für Formulare {#additional-considerations-for-forms}

Wenn Daten in einem bestimmten Format eingegeben werden müssen, sollten Sie dies in der Beschriftung deutlich machen. Wenn z. B. ein Datum im Format `DD-MM-YYYY` eingegeben werden soll, fügen Sie diese Angabe in die Beschriftung ein. Wenn Menschen, die eine Bildschirmlesehilfe nutzen, auf das Feld stoßen, wird daher automatisch die Kennzeichnung zusammen mit den zusätzlichen Informationen zum Format angezeigt.

Wenn die Eingabe für ein Formularfeld obligatorisch ist, machen Sie dies deutlich, indem Sie das erforderliche Wort als Teil der Bezeichnung verwenden. AEM fügt ein Sternchen hinzu, wenn ein Feld erforderlich ist. Idealerweise sollte jedoch das Wort `required` (erforderlich) direkt in die Beschriftung eingefügt werden (im Feld **Titel** im Bearbeitungsdialogfeld).

![ Hinzufügen zusätzlicher Informationen (das Wort „erforderlich“) für Menschen, die eine Bildschirmlesehilfe nutzen, im Feld „Titel“ ](assets/chlimage_1-25a.png)

Die Positionierung von Kennzeichnungen ist ebenfalls wichtig, da sie beim Suchen nach geeigneten Feldern hilft. Dies ist besonders wichtig, wenn die Person mit einem komplexen Formular konfrontiert ist. Befolgen Sie die nachstehende Konvention:

* Kontrollkästchen oder Optionsfelder:

Beschriftungen werden direkt rechts neben dem Feld positioniert.

* Alle anderen Formularkomponenten (z. B. Textfelder, Kombinationsfelder):

Kennzeichnungen werden entweder direkt über dem Feld oder direkt links vom Feld platziert.

In einfachen Formularen mit wenigen Funktionen kann eine passende Kennzeichnung einer `Submit`-Schaltfläche auch als Kennzeichnung für das angrenzende Feld dienen (z. B. `Search`). Dies ist in Situationen nützlich, in denen wenig Platz für die Beschriftung vorhanden ist.

#### Weitere Informationen – Beschriftungen oder Anweisungen (3.3.2) {#more-information-labels-or-instructions}

* [Erfolgskriterium 3.3.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)
* [Erfolgskriterium 3.3.2 erfüllen](https://www.w3.org/WAI/WCAG21/quickref/?versions=2.0#qr-minimize-error-cues)
