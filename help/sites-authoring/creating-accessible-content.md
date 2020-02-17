---
title: Erstellung barrierefrei zugänglicher Inhalte
seo-title: Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien)
description: Barrierefreies Nutzen von Webinhalten durch Personen mit Behinderungen
seo-description: Barrierefreies Nutzen von Webinhalten durch Personen mit Behinderungen
uuid: e2653a46-fd55-407b-b331-8a684fbfd041
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 0aa18f7d-76a8-4c51-9e17-da50ae065fe8
docset: aem65
translation-type: tm+mt
source-git-commit: aaabef9d51e333003385709045e2249a10eb34aa

---


# Erstellung barrierefrei zugänglicher Inhalte (in Übereinstimmung mit den WCAG 2.0-Richtlinien){#creating-accessible-content-wcag-conformance}

WCAG 2.0 umfasst eine Reihe von technologieunabhängigen Richtlinien und Erfolgskriterien, die Sie bei der Erstellung von Webinhalten, die für Personen mit Behinderungen barrierefrei zugänglich sind, unterstützen.

>[!NOTE]
>
>Siehe auch:
>
>* den [Quick Guide zu WCAG 2.0](/help/managing/qg-wcag.md), um weitere Details zu erhalten.
>* [Konfigurieren des Rich-Text-Editors (RTE) für die Erstellung von barrierefrei zugänglichen Inhalten](/help/sites-administering/rte-accessible-content.md)
>



Diese sind in drei Konformitätslevel abgestuft: Level A (niedrigstes), Level AA und Level AAA (höchstes). Die Levels sind kurz definiert wie folgt:

* **Level A:** Ihre Site erreicht ein allgemeines Mindestmaß an Barrierefreiheit. Zur Erreichung dieses Levels müssen alle Erfolgskriterien von Level A erfüllt sein.
* **** Stufe AA: Dies ist ein idealer Barrierefreiheitsgrad, nach dem Sie streben können und in dem Ihre Site ein verbessertes Maß an Barrierefreiheit erreicht, sodass sie für die meisten Menschen in den meisten Situationen mit den meisten Technologien zugänglich ist. Um dieses Niveau zu erreichen, sind alle Erfolgskriterien der Stufen A und AA erfüllt.
* **Level AAA:** Ihre Site erreicht ein sehr hohes Maß an Barrierefreiheit. Zur Erreichung dieses Levels müssen alle Erfolgskriterien von Level A, Level AA und Level AAA erfüllt sein.

Bei der Erstellung Ihrer Site sollten Sie das Gesamtlevel festlegen, dem Ihre Site entsprechen sollte.

Im folgenden Abschnitt finden Sie die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) mit den entsprechenden Erfolgskriterien für die [Konformitätslevels](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html) Level A und Level AA.

>[!NOTE]
>
>Da bestimmte Inhalte die Erfolgskriterien von Level AAA unmöglich erreichen können, ist es nicht empfehlenswert, dieses Konformitätslevel als allgemeine Richtlinie festzulegen.

>[!NOTE]
>
>In diesem Dokument verwenden wir Folgendes:
>
>* Die Kurznamen für die [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines).
>* Die Nummerierung der [WCAG 2.0-Richtlinien](https://www.w3.org/TR/WCAG20/#guidelines) zur Erleichterung von Querverweisen zur WCAG-Website.
>



## Grundsatz 1: Erkennbar {#principle-perceivable}

[Grundsatz 1: Erkennbar -  Informationen und Komponenten der Benutzeroberfläche müssen für die Benutzer so dargestellt sein, dass sie sie erkennen können.](https://www.w3.org/TR/WCAG20/#perceivable)

### Textalternativen (1.1) {#text-alternatives}

[Richtlinie 1.1 Textalternativen: Bieten Sie Textalternativen für nichttextlichen Inhalt, damit sie in andere Formate geändert werden, die von bestimmten Personen benötigt werden, wie zum Beispiel Großdruck, Braille, Sprache, Symbole oder einfachere Sprache.](https://www.w3.org/TR/WCAG20/#text-equiv)

### Nichttextlicher Inhalt (1.1.1) {#non-text-content}

* Erfolgskriterium 1.1.1
* Level A
* Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzern präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen.

#### Zweck: Nichttextlicher Inhalt (1.1.1) {#purpose-non-text-content}

Informationen auf einer Webseite können in vielen verschiedenen nichttextlichen Formaten dargestellt werden, wie zum Beispiel als Bilder, Videos, Animationen und Diagramme. Menschen, die blind sind oder deren Sicht erheblich eingeschränkt ist, können nichttextliche Inhalte nicht sehen, doch sie können Textinhalte erfassen, wenn sie ihnen von einem Bildschirmleser vorgelesen oder in haptischer Form auf einem Braille-Anzeigegerät präsentiert werden. Somit kann es durch Bereitstellung von Textalternativen zu Inhalten in grafischem Format ermöglicht werden, dass Menschen, die die grafischen Inhalte nicht sehen können, auf eine gleichwertige Version der Informationen des Inhalts zugreifen können.

Ein nützlicher weiterer Vorteil besteht darin, dass es durch Textalternativen möglich ist, nichttextliche Inhalte durch die Suchmaschinentechnologie zu indizieren.

#### Erfüllen: Nichttextlicher Inhalt (1.1.1) {#how-to-meet-non-text-content}

Bei statischen Grafiken besteht die Grundanforderung darin, eine gleichwertige Textalternative für die Grafik bereitzustellen. Dies kann im Feld **ALT-Text** durchgeführt werden:

>[!NOTE]
>
>Einige integrierte Komponenten wie **Karussell** und **Dia-Show** bieten keine Möglichkeit zum Hinzufügen von alternativen Textbeschreibungen zu Bildern. When implementing versions of these for your AEM instance, your development team will need to configure such components to support the `alt` attribute so that authors can add it to the content (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

Das Feld **Alternativtext** ist im Komponentendialogfeld **Bild** der Registerkarte **Metadaten** verfügbar:

![Das Dialogfeld „Bearbeiten“ der Komponente „Bild“ in der Touch-optimierten Benutzeroberfläche zeigt das Feld „ALT-Text“.](assets/screen_shot_2018-03-21at165045.png)

In AEM muss das Feld **Alternativtext** standardmäßig ausgefüllt werden. Wenn das Bild nur dekorativ ist und Alternativtext keinen Sinn ergeben würde, kann die Option **Bild ist dekorativ** aktiviert werden.

#### Creating Good Text Alternatives {#creating-good-text-alternatives}

Es gibt verschiedene Arten von nichttextlichem Inhalt. Daher hängt der Wert der Textalternative von der Rolle ab, die die Grafik auf der Webseite spielt. Nachfolgend sehen Sie einige Faustregeln:

* Textalternativen sollten kurz und bündig sein, aber dennoch klar die wesentlichen Informationen erfassen, die der nichttextliche Inhalt vermittelt.
* Übermäßig lange Beschreibungen (mit mehr als 100 Zeichen) sollten vermieden werden. Wenn für eine Textalternative mehr Details erforderlich sind:

   * Geben Sie im Alternativtext eine kurze Beschreibung ab
   * und fügen Sie irgendwo anders auf der entsprechenden Seite oder auf einer anderen Webseite eine längere Beschreibung ein. Verlinken Sie auf diese separate Beschreibung, indem Sie das Bild mit einem Link unterlegen oder indem Sie neben das Bild einen Textlink platzieren.

* Alternativtext sollte keinen Inhalt replizieren, der bereits in Textform auf derselben Seite vorhanden ist. Denken Sie daran, dass viele Bilder Darstellungen von Punkten sind, die bereits der Text einer Seite abdeckt. Somit ist möglicherweise bereits eine Textalternative vorhanden.
* Wenn es sich bei dem nichttextlichen Inhalt um einen Link zu einer anderen Seite oder einem anderen Dokument handelt und kein anderer Text vorhanden ist, der Teil desselben Links ist, dann muss der Alternativtext für das Bild das Ziel des Links angeben und braucht das Bild nicht zu beschreiben.
* Wenn sich der nichttextliche Inhalt in einem Schaltflächenelement befindet und kein Text vorhanden ist, der Teil derselben Schaltfläche ist, dann muss der Alternativtext des Bildes die Funktion der Schaltfläche angeben statt das Bild zu beschreiben.
* Es ist durchaus akzeptabel, dass einem Bild ein leerer alternativer Text (null) zugewiesen wird, jedoch nur, wenn das Bild keinen alternativen Text enthält (z. B. eine rein dekorative Grafik) oder wenn der entsprechende Text bereits im Seitentext vorhanden ist.

Der [W3C-Entwurf: HTML5-Techniken zur Bereitstellung nützlicher Textalternativen](https://dev.w3.org/html5/alt-techniques/) bietet mehr Details und Beispiele für die Bereitstellung von angemessenem Alternativtext für unterschiedliche Arten von Bildern.

Bestimmte Arten von nichttextlichem Inhalt, für den Textalternativen erforderlich sind:

* Illustrative photos:
These are images of people, objects or places. Think about the role of the photo in the page; an appropriate text equivalent is likely to be *Photo of[object ]*, but may be dependent on the surrounding text.
* Symbole:
Hierbei handelt es sich um kleine Piktogramme (Grafiken), die bestimmte Informationen vermitteln. Sie müssen durchgängig auf einer Seite und Site verwendet werden. Alle Instanzen des Symbols auf einer Seite oder Site sollten dieselbe kurze und knappe Textalternative haben, es sei denn, dass dadurch eine unnötige Verdoppelung von bereits vorhandenem Text erzeugt würde.
* Charts and graphs:
These typically represent numerical data. So one option for providing a text alternative might be to include a brief summary of the main trends shown in the chart or graphic. If necessary, also provide a more detailed description in text using the **Description** field in the **Advanced** image properties tab. Additionally, you could provide the source data in tabular form elsewhere in the page or site.

   ![Beispiel eines Diagramms: Nachfolgend sehen Sie einen bewährten Ansatz zur Bereitstellung einer Alternative.](assets/chlimage_1.jpeg)

   Zur Bereitstellung einer Alternative für dieses Beispieldiagramm können Sie dem Bild selbst einen knappen `alt` -Text hinzufügen und dann dem Bild eine vollständige Textalternative folgen lassen.

   ```xml
   <p><img src="figure1.gif" alt="Figure 1" ></p>
   <p> Figure 1. Distribution of Articles by Journal Category.
   Pie chart: Language=68%, Education=14% and Science=18%.</p>
   ```

   >[!NOTE]
   >
   >Der obige Ausschnitt dient nur zur Veranschaulichung der Reihenfolge. Es wird empfohlen, die Komponente **Bild** (statt des oben verwendeten `img src` -Verweises) zu verwenden.

   In AEM können Sie dies anhand einer Kombination der Felder **ALT-Text** und **Beschreibung** im Konfigurationsdialogfeld des Bildes erreichen, wie in [Erfüllen: Nichttextlicher Inhalt (1.1.1)](#how-to-meet-non-text-content).

* Maps, diagrams, flowcharts:
For graphics providing spatial data (for example. to support describing relationships between objects or a process), ensure that the key message is provided in text format. For maps, providing a full text equivalent is likely to be impractical, but if the map is provided as a way of helping people find their way to a particular location, then the map image’s alternative text can briefly indicate *Map of X*, then provide directions to that location in text elsewhere in the page or through the **Description** field in the **Advanced** tab of the **Image** component.
* CAPTCHAs:
Ein CAPTCHA ist ein *vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen*. Es handelt sich um eine Sicherheitsprüfung auf Webseiten, um Menschen von schädlicher Software zu unterscheiden, die allerdings die Barrierefreiheit einschränken kann. Sie bestehen aus Bildern, bei denen Benutzer beschreiben sollen, was sie sehen, um einen Sicherheitstest zu bestehen. Die Bereitstellung einer Textalternative für das Bild ist offensichtlich nicht möglich, daher müssen Sie stattdessen alternative nichtgrafische Lösungen in Betracht ziehen.
Das W3C bietet eine Reihe von Vorschlägen wie: Diese Ansätze haben jedoch sowohl Vor- als auch Nachteile.

   * Logik-Puzzles
   * Audio statt Bilder
   * Eingeschränkte Benutzerkonten und Spamfilter

* Hintergrundbilder: Diese werden mithilfe von CSS (Cascading Stylesheets) anstelle von HTML erreicht. Das bedeutet, dass es nicht möglich ist, einen alternativen Textwert anzugeben. Daher sollten Hintergrundbilder keine wichtigen Textinformationen liefern - wenn dies der Fall ist, müssen diese Informationen auch im Text der Seite angegeben werden. Es ist jedoch wichtig, dass ein alternativer Hintergrund angezeigt wird, wenn das Bild nicht angezeigt werden kann.

   >[!NOTE]
   >
   >Es sollte ein Mindestmaß an Kontrast zwischen dem Hintergrund- und dem Vordergrundtext vorhanden sein; weitere Details hierzu finden Sie unter [Kontrast (Minimum) (1.4.3)](#contrast-minimum).

#### Weitere Informationen: Nichttextlicher Inhalt (1.1.1) {#more-information-non-text-content}

* [Erfolgskriterium 1.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html)
* [Erfolgskriterien 1.1.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#text-equiv)
* [W3C: HTML5-Techniken zur Bereitstellung nützlicher Textalternativen (Entwurf)](https://dev.w3.org/html5/alt-techniques/)
* [W3C-Erklärung und Alternativen zu CAPTCHAs](https://www.w3.org/TR/turingtest/)

### Zeitbasierte Medien (1.2) {#time-based-media}

[Richtlinie 1.2 Zeitbasierte Medien: Bereitstellung von Alternativen für zeitbasierte Medien.](https://www.w3.org/TR/WCAG20/#text-equiv)

Diese Richtlinie behandelt Webinhalte, die *zeitbasiert* sind. Es handelt sich um Inhalte, die der Benutzer abspielen kann (wie Video, Audio und animierte Inhalte) und die entweder vorher aufgezeichnet wurden oder als Live-Stream verfügbar sind.

### Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#audio-only-and-video-only-pre-recorded}

* Erfolgskriterium 1.2.1
* Level A
* Nur-Audio und Nur-Video (aufgezeichnet): Für aufgezeichnete Nur-Audio und Nur-Video-Medien gilt Folgendes, außer wenn das Audio oder Video eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist:

   * Aufgezeichnetes Nur-Audio: Eine Alternative für zeitbasierte Medien wird bereitgestellt, die gleichwertige Informationen für aufgezeichnete Nur-Audio-Inhalte darstellt.
   * Aufgezeichnetes Nur-Video: Es wird entweder eine Alternative für zeitbasierte Medien oder ein Audio-Track bereitgestellt, die/der gleichwertige Informationen für aufgezeichnete Nur-Video-Inhalte darstellt.

#### Zweck: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#purpose-audio-only-and-video-only-pre-recorded}

Für folgende Personen kann der barrierefreie Zugang für Video und Audio eingeschränkt sein:

* Personen mit eingeschränktem Sehvermögen, wenn es keinen Soundtrack gibt oder wenn der Soundtrack nicht ausreicht, um sie über die Vorgänge im Video oder in der Animation zu informieren;
* Personen mit eingeschränktem Hörvermögen oder gehörlose Personen, die den Soundtrack nicht hören können.
* Personen, die den Soundtrack zwar hören können, doch den gesprochenen Inhalt nicht verstehen (weil er beispielsweise in einer Sprache aufgezeichnet ist, die sie nicht verstehen).

Video oder Audio kann auch für Personen unzugänglich sein, die Browser oder Geräte verwenden, die die Wiedergabe von Inhalt in bestimmten Medienformaten wie zum Beispiel Adobe Flash nicht unterstützen.

Wenn diese Informationen in einem anderen Format bereitgestellt werden, wie zum Beispiel als Text (oder Audio für Video ohne Audio), können die Informationen für die Personen barrierefrei zugänglich sein, die nicht auf den ursprünglichen Inhalt zugreifen können

#### Erfüllen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#how-to-meet-audio-only-and-video-only-pre-recorded}

* Wenn es sich bei dem Inhalt um aufgezeichnetes Audio ohne Video (wie zum Beispiel Podcast) handelt:

   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einem Text-Transkript des Audioinhalts bereit.
Das Transkript sollte eine HTML-Seite mit einer Textentsprechung aller gesprochenen und wichtigen nicht gesprochenen Inhalte sein und den Sprecher, eine Beschreibung der Szenerie, Gesänge und eine Beschreibung anderer wichtiger Audioinhalte angeben.

* Wenn es sich bei dem Inhalt um eine Animation oder ein aufgezeichnetes Video ohne Audio handelt:

   * Stellen Sie direkt vor oder nach dem Inhalt einen Link zu einer entsprechenden Textbeschreibung der Informationen im Video bereit.
   * Es kann auch eine entsprechende Audiobeschreibung in einem häufig verwendeten Audioformat wie MP3 sein.

>[!NOTE]
>
>Wenn der Audio- oder Videoinhalt als Alternative zu Inhalten bereitgestellt wird, die bereits in einem anderen Format auf einer Webseite vorhanden sind, müssen die oben genannten Anforderungen nicht erfüllt werden. Wenn beispielsweise ein Video eine Liste von Textanweisungen veranschaulicht, dann ist für dieses Video kein Alternativtext erforderlich, weil die Textanweisungen bereits als Alternative für das Video dienen.

Das Einfügen von Multimedia wie Flash-Inhalten auf Ihren AEM-Webseiten entspricht in etwa dem Einfügen eines Bildes. Da Multimedia jedoch weit mehr ist als ein Standbild, gibt es eine Vielzahl von verschiedenen Einstellungen und Optionen zur Steuerung wie die Multimedia-Inhalte abgespielt werden.

>[!NOTE]
>
>Wenn Sie Multimedia mit Informationsinhalten verwenden, müssen Sie auch Links zu Alternativen erstellen. Wenn Sie beispielsweise ein Textskript einbeziehen möchten, erstellen Sie eine HTML-Seite, um das Skript anzuzeigen, und fügen Sie dann einen Link neben oder unter dem Audioinhalt hinzu.

#### Weitere Informationen: Nur-Audio und Nur-Video (aufgezeichnet) (1.2.1) {#more-information-audio-only-and-video-only-pre-recorded}

* [Erfolgskriterium 1.2.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html)
* [Erfolgskriterien 1.2.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)

### Untertitel (aufgezeichnet) (1.2.2) {#captions-pre-recorded}

* Erfolgskriterium 1.2.2
* Level A
* Untertitel (aufgezeichnet): Untertitel werden für alle aufgezeichneten Audioinhalte in synchronisierten Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Untertitel (aufgezeichnet) (1.2.2) {#purpose-captions-pre-recorded}

Gehörlose oder schwerhörige Menschen können Audioinhalte gar nicht oder nur schwer verstehen. Untertitel sind Textentsprechungen für gesprochene und nicht gesprochene Audioinhalte; sie werden im Video zum richtigen Zeitpunkt auf dem Bildschirm angezeigt. Sie ermöglichen es Menschen, die das Audio nicht hören können, zu verstehen, was vor sich geht.

>[!NOTE]
>
>Untertitel sind nicht erforderlich, wenn passender Text oder nichttextliche Entsprechungen (die direkt entsprechende Informationen vermitteln) auf derselben Seite wie das Video oder die Animation verfügbar sind.

#### Erfüllen: Untertitel (aufgezeichnet) (1.2.2) {#how-to-meet-captions-pre-recorded}

Es gibt zwei Arten von Untertiteln:

* Offen: Immer sichtbar, wenn das Video abgespielt wird
* Geschlossen:* *Die Beschriftungen können vom Benutzer ein- oder ausgeschaltet werden

Verwenden Sie möglichst geschlossene Untertitel, da Benutzer so wählen können, ob die Untertitel angezeigt werden.

Für geschlossene Untertitel müssen Sie eine synchronisierte Untertiteldatei in einem entsprechenden Format (wie [SMIL](https://www.w3.org/AudioVideo/)) erstellen und zusammen mit der Videodatei bereitstellen (Details dazu, wie dieser Vorgang ausgeführt wird, sind im Rahmen dieses Leitfadens nicht möglich, doch wir haben Ihnen Links zu einigen Lernprogrammen unter [Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2)](#more-information-captions-pre-recorded) zusammengestellt). Geben Sie Benutzern auf jeden Fall einen Hinweis, dass Untertitel für das Video verfügbar sind.

Wenn Sie offene Untertitel verwenden müssen, betten Sie den Text im Videotrack ein. Dies erreichen Sie mithilfe von Anwendungen zur Videobearbeitung, die die Überlagerung von Untertiteln im Video ermöglichen.

#### Weitere Informationen: Untertitel (aufgezeichnet) (1.2.2) {#more-information-captions-pre-recorded}

* [Erfolgskriterium 1.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html):
* [Erfolgskriterien 1.2.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#media-equiv)
* [W3C: Synchronisiertes Multimedia](https://www.w3.org/AudioVideo/)
* [Untertitel, Transkripte und Audiobeschreibungen - mit WebAIM](https://webaim.org/techniques/captions/)

### Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#audio-description-or-media-alternative-pre-recorded}

* Erfolgskriterium 1.2.3
* Level A
* Audiobeschreibung oder Medienalternative (aufgezeichnet): Eine Alternative für zeitbasierte Medien oder eine Audiobeschreibung des aufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, außer wenn das Medium eine Medienalternative für Text und als solche ausdrücklich gekennzeichnet ist.

#### Zweck: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#purpose-audio-description-or-media-alternative-pre-recorded}

Blinde Menschen oder Menschen mit eingeschränktem Sehvermögen haben keinen Zugang zu Informationen in einem Video oder einer Animation, wenn diese nur visuell vermittelt werden oder wenn der Soundtrack nicht genügend Informationen bietet, damit sie verstehen können, was visuell gezeigt wird.

#### Erfüllen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#how-to-meet-audio-description-or-media-alternative-pre-recorded}

Es gibt zwei Ansätze zur Erfüllung dieses Erfolgskriteriums. Beide sind akzeptabel:

1. Hinzufügen einer weiteren Audiobeschreibung für den Videoinhalt. Hierzu gibt es drei verschiedene Möglichkeiten:

   * Fügen Sie in Pausen im vorhandenen Dialog Informationen zu den Änderungen der Szene ein, die nicht als Teil des vorhandenen Audiotracks präsentiert werden:
   * Stellen Sie einen neuen, zusätzlichen und optionalen Audiotrack bereit, der den ursprünglichen Soundtrack und zudem weitere Audioinformationen zu den Änderungen in der Szene enthält.

      * Dadurch können Benutzer zwischen dem vorhandenen Audiotrack (der *keine* Audiobeschreibung enthält) und dem neuen Audiotrack ( *mit* einer Audiobeschreibung) wechseln.

      * Dadurch wird verhindert, dass Benutzer, die die zusätzliche Beschreibung nicht benötigen, gestört werden.
   * Erstellen Sie eine zweite Version des Videoinhalts, um erweiterte Audiobeschreibungen zu ermöglichen. Dies verringert die Schwierigkeiten, die sich durch Einfügen von detaillierten Audiobeschreibungen in Lücken zwischen dem vorhandenen Dialog ergeben, weil das Audio und Video an passenden Stellen unterbrochen werden muss. Als Ergebnis kann eine viel längere Audiobeschreibung gegeben werden, bevor die Aktion erneut startet. Wie im vorigen Beispiel wird dies am besten als optionaler eigener Audio-Track bereitgestellt, um eine Störung der Benutzer zu verhindern, die keine zusätzliche Beschreibung benötigen.


1. Stellen Sie ein Text-Transkript bereit, das eine angemessene Textentsprechung der Audio- und Bildelemente des Videos oder der Animation ist. Es sollte möglichst den Sprecher, eine Beschreibung der Szenerie und den sprachlichen Ausdruck angeben. Abhängig von der Länge können Sie das Transkript auf derselben Seite wie das Video oder die Animation einfügen, oder auch auf einer separaten Seite. In diesem Fall müssen Sie einen Link zu dem Transkript neben dem Video oder der Animation bereitstellen.

Genaue Details zur Erstellung von Audiobeschreibungen für Video würden den Rahmen dieses Leitfadens sprengen. Die Erstellung von Audiobeschreibungen können zeitaufwändig sein, doch andere Adobe-Produkte helfen Ihnen bei diesen Aufgaben. If you create content in Adobe Flash Professional, you should also create a script to prompt the user to download the appropriate plug-in, and provide a text alternative through the `<noscript>` element.

#### Weitere Informationen: Audiobeschreibung oder Medienalternative (aufgezeichnet) (1.2.3) {#more-information-audio-description-or-media-alternative-pre-recorded}

* [Erfolgskriterien 1.2.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html):
* [Erfolgskriterien 1.2.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc)
* [Adobe Encore CS5](https://www.adobe.com/products/premiere/encore/)

### Untertitel (live) (1.2.4)  {#captions-live}

* Erfolgskriterium 1.2.4
* Level AA
* Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Untertitel (Live) (1.2.4) {#purpose-captions-live}

This success criterion is identical to [Captions (Pre-Recorded)](#captionsprerecorded) in that it addresses accessibility barriers experienced by people who are deaf or hearing-impaired, except that this success criterion deals with live presentations such as webcasts.

#### Erfüllen: Untertitel (Live) (1.2.4) {#how-to-meet-captions-live}

Follow the guidance provided for [Captions (Pre-Recorded)](#captionsprerecorded) above. However, due to the live nature of the media, caption provision has to be created as quickly as possible and in response to what is happening. Therefore, you should consider using real time captioning or speech-to-text tools.

Detaillierte Anweisungen dazu würden den Rahmen dieses Dokuments sprengen, doch in den folgenden Ressourcen finden Sie nützliche Informationen:

* [WebAIM: Echtzeit-Untertitelung](https://www.webaim.org/techniques/captions/realtime.php)
* [AccessIT (University of Washington): Können Untertitel automatisch über die Spracherkennung erstellt werden?](https://www.washington.edu/accessit/articles?1209)

#### Weitere Informationen: Untertitel (Live) (1.2.4) {#more-information-captions-live}

* [Erfolgskriterium 1.2.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html)
* [Erfolgskriterien 1.2.4 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-real-time-captions)

### Audiobeschreibung (aufgezeichnet) (1.2.5)  {#audio-description-pre-recorded}

* Erfolgskriterium 1.2.5
* Level AA
* Audiobeschreibung (aufgezeichnet): Audiobeschreibungen werden für alle aufgezeichneten Videoinhalte in synchronisierten Medien bereitgestellt.

#### Zweck: Audiobeschreibung (aufgezeichnet) (1.2.5) {#purpose-audio-description-pre-recorded}

Dieses Erfolgskriterium entspricht dem Erfolgskriterium zu [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audiodescriptionormediaalternativeprerecorded), mit dem Unterschied, dass Autoren eine wesentlich detailliertere Audiobeschreibung verfassen müssen, um Level AA zu erfüllen.

#### Erfüllen: Audiobeschreibung (aufgezeichnet) (1.2.5) {#how-to-meet-audio-description-pre-recorded}

Befolgen Sie die Anweisungen für [Audiobeschreibung oder Medienalternative (aufgezeichnet)](#audiodescriptionormediaalternativeprerecorded).

#### Weitere Informationen: Audiobeschreibung (aufgezeichnet) (1.2.5) {#more-information-audio-description-pre-recorded}

* [Erfolgskriterium 1.2.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html)
* [Erfolgskriterien 1.2.5 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-media-equiv-audio-desc-only)

### Anpassbar (1.3) {#adaptable}

[Richtlinie 1.3 Anpassbar: Erstellen von Inhalten, die auf verschiedene Arten präsentiert werden können (zum Beispiel mit einfacherem Layout) ohne Informationen oder die Struktur zu verlieren.](https://www.w3.org/TR/WCAG20/#content-structure-separation)

Diese Richtlinie behandelt die Anforderungen zur Unterstützung folgender Personen:

* kann möglicherweise nicht auf Informationen zugreifen, die von einem Autor in einem *zweidimensionalen, mehrspaltigen, farbigen Webseitenlayout präsentiert werden

* Personen, die eine Nur-Audio-Darstellung oder alternative visuelle Darstellung wie Großdruck oder hohen Kontrast verwenden wollen.

### Informationen und Beziehungen (1.3.1)  {#info-and-relationships}

* Erfolgskriterium 1.3.1
* Level A
* Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmatisch festgelegt werden oder sind im Text verfügbar.

#### Zweck: Informationen und Beziehungen (1.3.1) {#purpose-info-and-relationships}

Viele Hilfstechnologien, die von Menschen mit Behinderungen verwendet werden, verlassen sich auf Strukturinformationen zur effektiven Anzeige oder Ausgabe von Inhalten. Diese Strukturinformationen können in Form von Seitenüberschriften, Tabellenzeilen und Spaltenüberschriften sowie Listentypen vorliegen. Beispielsweise könnte ein Benutzer mit einem Bildschirmleser von Überschrift zu Überschrift durch eine Seite navigieren. Wenn Seiteninhalte jedoch nur über visuelles Styling statt das zugrundeliegende HTML strukturiert wurden, stehen den Hilfstechnologien keine Strukturinformationen zur Verfügung und deren Fähigkeit zur Unterstützung eines leichteren Browsings ist erheblich eingeschränkt.

Dieses Erfolgskriterium besteht, um sicherzustellen, dass derartige Strukturinformationen über HTML bereitgestellt werden, damit die Browser und Hilfstechnologien auf die Informationen zugreifen und davon profitieren können.

#### Erfüllen: Informationen und Beziehungen (1.3.1) {#how-to-meet-info-and-relationships}

AEM erleichtert den Aufbau von Webseiten mit den entsprechenden HTML-Elementen. Öffnen Sie Ihren Seiteninhalt im RTE (einer Textkomponente) und geben Sie im Menü **Paraformat** (Absatzsymbol) das entsprechende Strukturelement (zum Beispiel Absatz, Überschrift usw.) an.

Im folgenden Bild ist zu sehen, dass der Text als Absatztext gestaltet ist.

![Ein Beispiel des Absatz-Elements im Modus zur Bearbeitung des Quellcodes (klassische Benutzeroberfläche).](assets/screen_shot_2018-03-21at165623.png)

Sie können folgendermaßen sicherstellen, dass Ihre Webseiten die entsprechende Struktur erhalten:

* **Verwendung von Überschriften:**

   As long as you have the accessibility features of the RTE enabled (see [AEM and Accessibility](#adobeexperiencemanagerandaccessibility)), AEM offers 3 levels of page heading. You can use these to identify sections and subsections of content. Heading 1 is the highest level of heading, Heading 3 the lowest. The system administrator can configure the system to allow the use of more heading levels.

   Im folgenden Bild ist ein Beispiel der verschiedenen Überschriftentypen zu sehen.

   ![Überschrift H1 bis H3 in der Dropdown-Auswahl (klassische Benutzeroberfläche).](assets/screen_shot_2018-03-21at165719.png)

* **Hervorgehobener Text**:

   Verwenden Sie das Element &lt;strong> oder &lt;em>, um eine Hervorhebung anzugeben. Verwenden Sie keine Überschriften zum Hervorheben von Text in Absätzen.

   * Markieren Sie den Text, den Sie hervorheben möchten.
   * Click on the **B** icon (for &lt;strong>) or the **I** icon (for &lt;em>) shown within the **Properties** panel (make sure that HTML is selected).
   >[!NOTE]
   >
   >RTE ist in einer Standardinstallation von AEM mit den folgenden Symbolen eingerichtet:
   >
   >    * &lt;b> für &lt;strong>
   * &lt;i> für &lt;em>
   Sie haben die gleiche Wirkung, doch &lt;strong> und &lt;em> sollten bevorzugt werden, weil sie semantisch korrekt für HTML sind. Bei der Entwicklung Ihrer Projektinstanz kann Ihr Entwicklungsteam den RTE zur Verwendung von &lt;strong> und &lt;em> (anstelle von &lt;b> und &lt;i>) konfigurieren.

* **Verwenden Sie Listen**: Mit HTML können Sie drei verschiedene Arten von Listen angeben:

   * The `<ul>` element is used for *unordered* lists (bulleted) lists. Individual list items are identified using the `<li>` element.
Verwenden Sie in RTE das Symbol **Aufzählung**.

   * The `<ol>` element is used for *numbered* lists*. *Individual list items are identified using the `<li>` element.
Verwenden Sie in RTE das Symbol **Nummerierte Liste** .
   Wenn Sie Inhalt in einen Listentyp ändern möchten, markieren Sie den entsprechenden Text und wählen Sie den jeweiligen Listentyp aus. Wie im obigen Beispiel, in dem gezeigt wird, wie Absatztext eingegeben wird, werden die entsprechenden Listenelemente automatisch zum HTML-Code hinzugefügt.

   Im Vollbildmodus sind die Symbole für **Aufzählung** und **Nummerierte Liste** einzeln sichtbar. Außerhalb des Vollbildmodus befinden sich die beiden Optionen unter dem Symbol **Listen**.

   ![](do-not-localize/screen_shot_2018-03-21at165756.png)

   >[!NOTE]
   `<dl>` wird vom RTE nicht unterstützt.

* **Verwenden SIe Tabellen**:

   Datentabellen müssen mit HTML-Tabellenelementen gekennzeichnet sein:

   * one `<table>` element
   * a `<tr>` element for each row of the table
   * a `<th>` element for each row and column heading
   * a `<td>` element for every data cell
   >[!NOTE]
   In der klassischen Benutzeroberfläche sollten Tabellen mit der Komponente **Tabelle** umgesetzt werden.

   Außerdem nutzen barrierefrei zugängliche Tabellen die folgenden Elemente und Attribute:

   * The `<caption>` element is used to provide a visible caption for the table. Beschriftungen werden standardmäßig zentriert über der Tabelle angezeigt, können jedoch mit CSS entsprechend positioniert werden. Die Beschriftung ist programmatisch mit der Tabelle verknüpft und ist daher eine nützliche Methode zur Angabe einer Einführung in den Inhalt.
   * The `<summary>` element assists non-sighted users to more easily understand the information presented within a table, by providing a synopsis of what a sighted user can see. Dies ist besonders nützlich bei komplexen oder unkonventionellen Tabellen-Layouts (dieses Attribut wird nicht im Browser angezeigt, sondern nur für Hilfstechnologien ausgelesen).
   * The `scope` attribute of the `<th>` element is used to indicate whether a cell represents a header for a particular row, or for a particular column. Auf ähnliche Weise können die Überschrift und ID-Attribute in komplexen Tabellen verwendet werden, bei denen Datenzellen mit einer oder mehreren Überschriften verknüpft sein können.
   >[!NOTE]
   By default, these elements and attributes are not directly available, though it is possible for the system administrator to add support for these values in the **Table properties** dialog box (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

   Wenn Sie eine **Tabelle** hinzufügen, können Sie die **Tabelleneigenschaften** im entsprechenden Dialogfeld konfigurieren:

   ![cac-02](assets/cac-02.png)

   So öffnen Sie das Dialogfeld **Tabelle**, in dem Sie die Registerkarte **Tabelleneigenschaften** auswählen können:

   * Definieren Sie eine entsprechende **Beschriftung**.
   * Idealerweise sollten Sie die Standardwerte für **Breite**, **Höhe**, **Rand**, **Textabstand** und **Zellenabstand** entfernen. Alle Eigenschaften können in einem globalen Stylesheet festgelegt werden.
   ![cac-01](assets/cac-01.png)

   Sie können dann die **Zellen-Eigenschaften** verwenden, um festzulegen, ob es sich bei der Zelle um eine Daten- oder Kopfzeilenzelle handelt:  

   ![cac-03](assets/cac-03.png)

* **Komplexe Datentabellen**:

   In some cases, where there are complex tables with two or more levels of headers, then the basic Table Properties may not be enough to provide all the structural information necessary. For these kinds of complex tables, direct relationships need to be created between the headers and their related cells using the **header** and **id** attributes. For example, in the table below headers and ids are matched to make a programmatic association for assistive technology users.

   >[!NOTE]
   Das ID-Attribut ist in Standardinstallationen nicht verfügbar. Es kann durch Konfigurieren von HTML-Regeln und des Serialisierungsprogramms im RTE aktiviert werden.

   >[!NOTE]
   In der klassischen Benutzeroberfläche sollten Tabellen mit der Komponente **Tabelle** umgesetzt werden.

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
   Diese Funktion ist in einer Standardinstallation nicht sofort verfügbar. Dazu ist die Konfiguration des RTE, der HTML-Regeln und des Serialisierungsprogramms erforderlich.

#### Weitere Informationen: Informationen und Beziehungen (1.3.1) {#more-information-info-and-relationships}

* [Erfolgskriterium 1.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
* [Erfolgskriterien 1.3.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-programmatic)

### Sensorische Eigenschaften (1.3.3)  {#sensory-characteristics}

* Erfolgskriterium 1.3.3
* Level A
* Sensorische Eigenschaften: Anweisungen, die zum Verstehen und Bedienen von Inhalt verfügbar sind, beziehen sich nicht nur auf sensorische Eigenschaften der Komponenten wie Form, Größe, visuelle Position, Ausrichtung oder Klang.

#### Zweck: Sensorische Eigenschaften (1.3.3) {#purpose-sensory-characteristics}

Entwickler konzentrieren sich bei der Präsentation von Informationen oft auf visuelle Design-Funktionen wie Farbe, Form, Textstil oder die absolute oder relative Position eines Inhaltselements. Diese können zwar sehr wirkungsvolle Entwicklungsmethoden zur Vermittlung von Informationen sein, doch blinde Menschen oder Menschen mit eingeschränktem Sehvermögen können nicht auf Informationen zugreifen, für die die visuelle Erkennung von Attributen wie Position, Farbe oder Form erforderlich ist.

Entsprechend sind Informationen, für die zwischen verschiedenen Klängen (z. B. Inhalte, die von einer Frau oder einem Mann gesprochen werden) unterschieden werden muss, für Menschen mit eingeschränktem Hörvermögen nicht verfügbar, wenn sie nicht in Textalternativen für den Audioinhalt umgesetzt wurden.

>[!NOTE]
Die Anforderungen, die sich auf die Alternativen für Farben beziehen, finden Sie unter [Verwendung von Farbe](#use-of-color).

#### Erfüllen: Sensorische Eigenschaften (1.3.3) {#how-to-meet-sensory-characteristics}

Stellen Sie sicher, dass Informationen, die sich auf visuelle Eigenschaften von Seiteninhalten beziehen, auch in alternativen Formaten präsentiert werden.

* Verlassen Sie sich nicht auf die visuelle Position, um Informationen bereitzustellen. Wenn Sie beispielsweise Benutzer auf ein Menü rechts auf der Seite verweisen möchten, über das sie auf weitere Informationen zugreifen können, beziehen Sie sich nicht auf *das Menü rechts*, sondern geben Sie den Namen für das Menü an (zum Beispiel über eine Überschrift) und beziehen Sie sich im Text auf diesen Namen.
* Verlassen Sie sich nicht auf den Textstil (z. B. fett oder kursiv gedruckter Text) als einzige Methode zur Vermittlung von Informationen.

>[!NOTE]
Die Verwendung beschreibender Begriffe ist dann akzeptabel, wenn diese auch in einem nicht visuellen Kontext eine Bedeutung haben. So ist z. B. die Verwendung von *oben* und *unten* in der Regel akzeptabel, da diese jeweils Inhalt vor und nach einem bestimmten Inhaltselement implizieren. Dabei bleibt die Bedeutung auch erhalten, wenn der Inhalt laut ausgesprochen wird.

#### Weitere Informationen - Sensorische Eigenschaften (1.3.3) {#more-information-sensory-characteristics}

* [Erfolgskriterium 1.3.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html)
* [Erfolgskriterien 1.3.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-content-structure-separation-understanding)

### Unterscheidbar (1.4) {#distinguishable}

[Richtlinie 1.4 Unterscheidbar: Erleichtern Sie den Benutzern das Sehen und Hören von Inhalt einschließlich der Unterscheidung von Vorder- und Hintergrund.](https://www.w3.org/TR/WCAG20/#visual-audio-contrast)

### Verwendung von Farbe (1.4.1)  {#use-of-color}

* Erfolgskriterium 1.4.1
* Level A
* Verwendung von Farbe: Farbe wird nicht als einziges visuelles Mittel eingesetzt, um Informationen zu vermitteln, eine Aktion zu kennzeichnen, eine Antwort einzuholen oder ein visuelles Element zu unterscheiden.

>[!NOTE]
Dieses Erfolgskriterium bezieht sich speziell auf die Farbwahrnehmung. Andere Wahrnehmungsformen werden unter [Anpassbar (1.3)](#adaptable) behandelt. Hierzu gehören der programmtechnische Zugriff auf Farbe und andere visuelle Darstellungskodierungen.

#### Zweck - Verwendung von Farbe (1.4.1) {#purpose-use-of-color}

Farbe bietet sichtbar eine effektive Möglichkeit, die Ästhetik von Webseiten zu verbessern, und kann auch die Vermittlung von Informationen unterstützen. Es gibt jedoch eine Vielzahl visueller Beeinträchtigungen, von Farbenblindheit bis zur Beeinträchtigung der Farbwahrnehmung, die dazu führt, dass manche Menschen zwischen bestimmten Farben nicht unterscheiden können. Aus diesem Grund ist die farbliche Kodierung ein unzuverlässiges Mittel für die Bereitstellung von Informationen.

Jemand mit einer Rot-Grün-Sehschwäche kann z. B. nicht zwischen Grünschattierungen und Rotschattierungen unterscheiden. Er sieht möglicherweise beide Farben als eine dritte Farbe (z. B. braun) und kann daher nicht zwischen rot, grün und braun unterscheiden.

Außerdem können Menschen, die einen reinen Textbrowser, monochrome Anzeigen oder einen Schwarzweiß-Ausdruck auf Papier nutzen, keine Farben wahrnehmen.

#### Erfüllen - Verwendung von Farbe (1.4.1) {#how-to-meet-use-of-color}

Immer wenn Farbe verwendet wird, um Informationen zu vermitteln, müssen Sie sicherstellen, dass die verfügbaren Informationen auch verfügbar sind, wenn die Farbe nicht sichtbar ist.

Stellen Sie z. B. sicher, dass die durch die Farbe vermittelte Information auch explizit im Text enthalten ist. Die folgende Abbildung zeigt, wie sowohl die Farbe als auch der Text die Verfügbarkeit von Sitzplätzen für eine Vorstellung anzeigen:

<table>
 <tbody>
  <tr>
   <td><p><strong>Leistung</strong></p> </td>
   <td><p><strong>Verfügbarkeit</strong></p> </td>
  </tr>
  <tr>
   <td><p><sup>Dienstag, 16. März</sup></p> </td>
   <td><p>SITZPLÄTZE VERFÜGBAR</p> </td>
  </tr>
  <tr>
   <td><p>Mittwoch, 17. März</p> </td>
   <td><p>SITZPLÄTZE VERFÜGBAR</p> </td>
  </tr>
  <tr>
   <td><p><sup>Donnerstag, 18. März</sup></p> </td>
   <td><p>AUSVERKAUFT</p> </td>
  </tr>
 </tbody>
</table>

Wenn Farbe als Hinweis für die Bereitstellung von Informationen verwendet wird, sollten Sie einen weiteren visuellen Hinweis einsetzen, wie einen anderen Schriftschnitt (z. B. fett, kursiv) oder eine andere Schriftart. Dies hilft Menschen mit schlechtem Sehvermögen oder einer beeinträchtigten Farbwahrnehmung, die Information zu erkennen. Man darf sich jedoch nicht vollständig auf diese Maßnahmen verlassen, da sie für Menschen, die die Seite überhaupt nicht sehen können, keine Hilfe bieten.

#### Weitere Informationen - Verwendung von Farbe (1.4.1) {#more-information-use-of-color}

* [Erfolgskriterium 1.4.1 verstehen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Erfolgskriterien 1.4.1 erfüllen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)
* [Anleitung für das Erzielen eines Kontrastverhältnisses von 3:1 mit einer Liste websicherer Farben](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/working-examples/G183/link-contrast.html)

### Kontrast (Minimum) (1.4.3) {#contrast-minimum}

* Erfolgskriterium 1.4.3
* Level AA
* Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1 mit folgenden Ausnahmen:

   * Großer Text: Großer Text und Bilder von großem Text haben ein Kontrastverhältnis von mindestens 3:1.
   * Nebensächlich: Für Text oder Bilder eines Texts, die Teil einer inaktiven Komponente der Benutzerschnittstelle, reine Dekoration, für niemanden sichtbar oder Teil eines Bildes sind, welches signifikante andere visuelle Inhalte enthält, gibt es keine Kontrastanforderung
   * Firmenschriftzüge: Für Text, der Teil eines Logos oder eines Markennamens ist, gibt es keine Kontrastanforderungen.

#### Zweck - Kontrast (Minimum) (1.4.3) {#purpose-contrast-minimum}

Manche Menschen mit einem beeinträchtigten Sehvermögen können nicht zwischen bestimmten Farbpaaren mit geringem Kontrast unterscheiden. Die Barrierefreiheit ist für diese Menschen in folgenden Situationen eingeschränkt:

* Wenn zwischen dem Text und der Hintergrundfarbe nur wenig Kontrast besteht.
* Wenn die Farbkodierung des Textes (wie Link-Text und Text ohne Link) für die Unterscheidung der Informationen wichtig ist.

>[!NOTE]
Text, der ausschließlich zu dekorativen Zwecken verwendet wird, ist von diesem Erfolgskriterium nicht betroffen.

#### Erfüllen - Kontrast (Minimum) (1.4.3) {#how-to-meet-contrast-minimum}

Stellen Sie sicher, dass zwischen dem Text und der Hintergrundfarbe ausreichend Kontrast besteht. Das Kontrastverhältnis hängt von der Größe und dem Schriftschnitt des betroffenen Textes ab:

* Für Text mit einer Größe von weniger als 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis zwischen Text/Bildern mit Text und dem Hintergrund mindestens 4,5:1 betragen.
* Für Text mit einer Größe von mindestens 18 Punkt (oder 14 Punkt bei Fettschrift) sollte das Kontrastverhältnis mindestens 3:1 betragen.
* Falls der Hintergrund gemustert ist, sollte der Hintergrund um alle Texte abgestuft sein, damit das Verhältnis von 4,5:1 oder 3:1 beibehalten wird.

Verwenden Sie ein Farbkontrasttool, um das Kontrastverhältnis zu prüfen, z. B. den [Color Contrast Analyser von Paciello Group](https://www.paciellogroup.com/resources/contrast-analyser.html) oder den [Color Contrast Checker von WebAIM](https://www.webaim.org/resources/contrastchecker/). Mit diesen Tools können Sie Farbpaare prüfen und erkennen mögliche Kontrastprobleme.

Wenn es für Sie nicht so wichtig ist, das Aussehen Ihrer Seite festzulegen, können Sie alternativ keine Farben für den Hintergrund und den Text im Vordergrund festlegen. Dann brauchen Sie den Kontrast nicht zu prüfen, weil der Browser des Benutzers die Farbe für den Text und den Hintergrund ermittelt.

Falls es nicht möglich ist, die geforderten Kontraststufen zu erfüllen, müssen Sie einen Link zu einer alternativen, identischen Version der Seite bereitstellen (auf der keine Farbkontrastprobleme vorliegen) oder dem Benutzer die Anpassung des Kontrasts des Farbschemas der Seite an seine eigenen Anforderungen ermöglichen.

#### Weitere Informationen - Kontrast (Minimum) (1.4.3) {#more-information-contrast-minimum}

* [Erfolgskriterium 1.4.3 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html)
* [Erfolgskriterien 1.4.3 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast)

### Bilder von Text (1.4.5) {#images-of-text}

* Erfolgskriterium 1.4.5
* Level AA
* Bilder von Text: Falls die verwendeten Technologien die visuelle Präsentation realisieren können, wird für die Vermittlung von Informationen Text verwendet und keine Bilder von Text. Dabei gelten folgende Ausnahmen:

   * Anpassbar: Das Bild des Texts kann visuell an die Anforderungen des Benutzers angepasst werden.
   * Erforderlich: Eine bestimmte Präsentation von Text ist für die zu vermittelnden Informationen erforderlich.

>[!NOTE]
Firmenschriftzüge (Texte, die Teil eines Logos oder eines Markennamens sind) werden als erforderlich angesehen.

#### Zweck - Bilder von Text (1.4.5) {#purpose-images-of-text}

Bilder von Text werden häufig verwendet, wenn ein bestimmter Textstil bevorzugt wird. Z. B. bei einem Firmenschriftzug oder wenn der Text aus einer anderen Quelle generiert wurde (z. B. ein eingescanntes Papierdokument). Im Vergleich mit in HTML dargestelltem Text, dessen Stil mittels CSS festgelegt wird, fehlt Bildern von Text jedoch die Flexibilität, die Größe oder das Erscheinungsbild zu ändern, was für Menschen mit Beeinträchtigungen der Sehfähigkeit oder mit Leseschwäche erforderlich sein kann.

#### Erfüllen - Bilder von Text (1.4.5) {#how-to-meet-images-of-text}

Wenn Bilder von Text verwendet werden müssen, nutzen Sie CSS, um die Bilder von Text in HTML durch einen identischen Text zu ersetzen, damit der Text in einer anpassbaren Version verfügbar ist. Ein Beispiel hierfür finden Sie unter [C30: Verwenden von CSS, um Text durch Bilder von Text zu ersetzen und ein Steuerelement zum Umschalten auf der Benutzeroberfläche bereitzustellen](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C30).

#### Weitere Informationen - Bilder von Text (1.4.5) {#more-information-images-of-text}

* [Erfolgskriterium 1.4.5 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html)
* [Erfolgskriterien 1.4.5 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-text-presentation)

## Grundsatz 2: Bedienbar {#principle-operable}

[Grundsatz 2: Bedienbar - Komponenten der Benutzerschnittstelle und der Navigation müssen bedienbar sein.](https://www.w3.org/TR/WCAG20/#operable)

### Pausieren, Beenden, Ausblenden (2.2.2)  {#pause-stop-hide}

* Erfolgskriterium 2.2.2
* Level A
* Pausieren, Beenden, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln:

   * Sich bewegend, blinkend, scrollend: Für alle sich bewegenden, blinkenden oder scrollenden Informationen, die (a) automatisch starten, (b) länger als 5 Sekunden dauern und (c) parallel zu anderen Inhalten dargestellt werden, muss es einen Mechanismus für den Benutzer geben, um diese zu pausieren, zu beenden oder auszublenden, sofern die Bewegung, das Blinken oder das Scrollen nicht Teil einer Aktivität ist, bei der dies erforderlich ist.
   * Automatische Aktualisierung: Für alle sich automatisch aktualisierenden Informationen, die (a) automatisch starten und (b) parallel mit anderen Inhalten dargestellt werden, muss es einen Mechanismus geben, damit der Benutzer die Aktualisierung pausieren, beenden oder ausblenden oder die Häufigkeit der Aktualisierung kontrollieren kann, sofern die automatische Aktualisierung nicht Teil einer Aktivität ist, bei der dies erforderlich ist.

Folgendes sollte beachtet werden:

1. Die Anforderungen für flackernden oder blinkenden Inhalt finden Sie unter [Gestalten Sie Inhalte nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen (2.3)](#donotdesigncontentinawaythatisknowntocauseseizures23).
1. Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Webseite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG20/#cc5).
1. Inhalt, der regelmäßig durch Software aktualisiert wird oder der auf den Benutzer-Agenten gestreamt wird, darf keine Informationen bewahren oder darstellen, die zwischen dem Initiieren des Anhaltens und dem Fortsetzen der Darstellung generiert oder empfangen wurden, da dies technisch möglicherweise nicht machbar ist und in vielen Situationen irreführend sein kann.
1. Eine Animation, die Teil einer Ladephase oder eines ähnlichen Szenarios ist, kann als erforderlich erachtet werden, wenn während dieser Phase keine Benutzerinteraktion möglich ist und wenn das Fehlen einer Fortschrittsanzeige Benutzer verwirren oder zu der Annahme verleiten kann, der Inhalt sei eingefroren oder beschädigt.

#### Zweck - Pausieren, Beenden, Ausblenden (2.2.2) {#purpose-pause-stop-hide}

Manche Benutzer empfinden Inhalte, die sich bewegen, als störend und haben Schwierigkeiten sich auf andere Bereiche der Seite zu konzentrieren. Darüber hinaus sind solche Inhalte für Menschen schwierig, die beim Lesen Probleme haben, sich bewegendem Text zu folgen.

#### Erfüllen - Pausieren, Beenden, Ausblenden (2.2.2) {#how-to-meet-pause-stop-hide}

Abhängig von der Art des Inhalts können Sie beim Erstellen von Webseiten mit sich bewegendem, blitzendem oder blinkendem Inhalt die folgenden Empfehlungen beachten:

* Bieten Sie die Möglichkeit, das Scrollen des Inhalts anzuhalten, um Benutzern Zeit zum Lesen zu geben. Z. B. Nachrichtenticker oder automatisch aktualisierter Text.
* Stellen Sie sicher, dass blinkende Inhalte maximal fünf Sekunden lang blinken.
* Nutzen Sie Technologien, mit denen die Anzeige von blinkenden Inhalten im Browser deaktiviert werden kann. Z. B. Dateien im GIF- (Graphics Interchange Format) oder APNG-Format (Animated Portable Network Graphics).
* Bieten Sie auf der Webseite ein Formularsteuerelement an, über das Benutzer sämtliche blinkenden Inhalte auf der Seite deaktivieren können.
* Falls eine der obigen Maßnahmen nicht möglich ist, bieten Sie einen Link zu einer Seite, die alle Inhalte ohne Blinken zeigt.

#### Weitere Informationen - Pausieren, Beenden, Ausblenden (2.2.2) {#more-information-pause-stop-hide}

* [Erfolgskriterium 2.2.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html)
* [Erfolgskriterium 2.2.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-time-limits-pause)

### Anfälle (2.3) {#seizures}

[Richtlinie 2.3 Anfälle: Gestalten Sie Inhalt nicht auf Arten, von denen bekannt ist, dass sie zu Anfällen führen.](https://www.w3.org/TR/WCAG20/#seizure)

### Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#three-flashes-or-below-threshold}

* Erfolgskriterium 2.3.1
* Level A
* Grenzwert von maximal dreimaligem Blitzen: Webseiten dürfen nichts enthalten, das in einem Zeitraum von einer Sekunde öfter als dreimal blitzt oder dessen Blitz unterhalb der allgemeinen Grenzwerte für Blitze und rote Blitze liegt.

>[!NOTE]
Jeglicher Inhalt, der dieses Erfolgskriterium nicht erfüllt, kann die Möglichkeit eines Benutzers beeinträchtigen, die gesamte Seite zu nutzen. Daher muss jeglicher Inhalt auf einer Webseite (egal ob er dazu dient, andere Erfolgskriterien zu erfüllen oder nicht) dieses Erfolgskriterium erfüllen. Siehe [Konformitätsanforderung 5: Nicht störend](https://www.w3.org/TR/WCAG20/#cc5).

#### Zweck - Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#purpose-three-flashes-or-below-threshold}

In bestimmten Fällen können blitzende Inhalte photosensitive Anfälle auslösen. Dieses Erfolgskriterium ermöglicht Benutzern den Zugriff und die Nutzung des gesamten Inhalts ohne Beeinträchtigung durch blitzende Inhalte.

#### Erfüllen - Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#how-to-meet-three-flashes-or-below-threshold}

Stellen Sie sicher, dass die folgenden Techniken zur Anwendung kommen:

* Stellen Sie sicher, dass Komponenten in einem Zeitraum von einer Sekunde nicht öfter als dreimal blitzen.
* If the above condition cannot be met, then display flashing content within a *small safe area* in pixels on the screen. This area is calculated using a complex formula, covered in [G176: Keeping the flashing area small enough](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/G176), so this technique should only be followed if flashing content is *absolutely* necessary.

#### Weitere Informationen - Grenzwert von maximal dreimaligem Blitzen (2.3.1) {#more-information-three-flashes-or-below-threshold}

* [Erfolgskriterium 2.3.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html)
* [Erfolgskriterium 2.3.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#seizure)

### Seite mit Titel versehen (2.4.2)  {#page-titled}

* Erfolgskriterium 2.4.2
* Level A
* Seite mit Titel versehen: Webseiten haben einen Titel, der das Thema oder den Zweck beschreibt

#### Zweck - Seite mit Titel versehen (2.4.2) {#purpose-page-titled}

Dieses Erfolgskriterium ist für alle Benutzer hilfreich - unabhängig von etwaigen Beeinträchtigungen - um schnell den Inhalt einer Webseite zu ermitteln, ohne die Seite vollständig zu lesen. Dies ist insbesondere dann nützlich, wenn mehrere Webseiten in Browsertabs geöffnet sind, da der Seitentitel auf den Tabs angezeigt wird, was die Seiten schnell auffindbar macht.

#### Erfüllen - Seite mit Titel versehen (2.4.2) {#how-to-meet-page-titled}

Wenn Sie im AEM eine neue HTML-Seite erstellen, können Sie den Seitentitel angeben. Stellen Sie sicher, dass der Titel den Inhalt der Seite so beschreibt, dass Besucher schnell feststellen können, ob der Inhalt für ihre Anforderungen relevant ist oder nicht.

You can also edit the page title when editing a page, which is accessible by **Page Information** - **Properties.**

#### Weitere Informationen - Seite mit Titel versehen (2.4.2) {#more-information-page-titled}

* [Erfolgskriterium 2.4.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html)
* [Erfolgskriterium 2.4.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-title)

### Linkzweck (im Kontext) (2.4.4)  {#link-purpose-in-context}

* Erfolgskriterium 2.4.4
* Level A
* Linkzweck (im Kontext): Der Zweck jedes Links kann allein durch den Linktext oder durch den Linktext zusammen mit dem programmatisch festgelegten Linkkontext bestimmt werden. Ausgenommen sind Fälle, in denen der Zweck des Links für Benutzer generell mehrdeutig ist.

#### Zweck - Linkzweck (im Kontext) (2.4.4) {#purpose-link-purpose-in-context}

Unabhängig von etwaigen Beeinträchtigungen ist es für alle Benutzer von entscheidender Bedeutung, dass durch einen passenden Linktext klar erkenntlich ist wohin ein Link führt. Dies erleichtert Benutzern die Entscheidung, ob sie einem Link folgen möchten oder nicht. Für sehende Benutzer ist ein aussagekräftiger Linktext ausgesprochen nützlich, wenn sich auf einer Seite mehrere Links befinden (vor allem, wenn eine Seite sehr viel Text enthält), da ein aussagekräftiger Linktext einen deutlicheren Hinweis auf die Funktion der Zielseite liefert. Gleichzeitig können Benutzer von Eingabehilfentechnologien, mit denen eine Liste aller Links auf einer Seite erstellt werden kann, den Linktext außerhalb des Kontextes einfacher nachvollziehen.

#### Erfüllen - Linkzweck (im Kontext) (2.4.4) {#how-to-meet-link-purpose-in-context}

Stellen Sie vor allem sicher, dass der Linktext den Zweck eines Links eindeutig beschreibt.

* Schlechtes Beispiel:

   * Text: Einzelheiten zu unseren Abendkursen im Herbst 2010 finden Sie hier.
   * Grund: Es geht nicht deutlich und unmissverständlich hervor wohin der Link führt.

* Gutes Beispiel:

   * Text: Abendunterricht für Herbst 2010 - Details.
   * Grund: Durch eine kleine Anpassung des Textes und der Position des Linkelements lässt sich der Linktext verbessern:

Links should be phrased consistently across pages, especially for navigation bars. For example, if a link to a specific page is named **Publications** on one page, use that text on other pages to ensure consistency.

Zum Zeitpunkt des Schreibens gibt es jedoch einige Probleme mit der Verwendung von Titeln:

* Im Title-Attribut enthaltener Text ist in der Regel nur für Mausbenutzer als QuickInfo-Popup verfügbar. Über eine Tastatur ist kein Zugriff möglich.
* Die Sprachausgabe kann Title-Attribute auslesen, diese Funktion ist jedoch nicht unbedingt standardmäßig aktiviert. Daher ist es für Benutzer eventuell nicht ersichtlich, dass ein Title-Attribut vorhanden ist.
* Es ist schwierig das Erscheinungsbild des Titeltextes anzupassen, weshalb es für manche Menschen schwierig oder unmöglich sein kann, diesen zu lesen.

Das Title-Attribut kann also genutzt werden, um zusätzlichen Kontext zu einem Link bereitzustellen, Sie sollten aber diese Einschränkungen bedenken und es daher nicht als Alternative für einen geeigneten Linktext nutzen.

Where the link is made up of an image, make sure that the alternative text for the image describes the destination of the link. For example, if an image of a bookshelf is set as a link to a person’s publications, the alternative text should read **John Smith’s publications** and not **Bookshelf**.

Falls der Link-Anker Text enthält, der ergänzend zum Bildelement den Zweck des Links beschreibt (und dieser Text neben dem Bild angezeigt wird), können Sie für das Bild alternativ ein leeres Alt-Attribut verwenden:

```xml
<a href="publications.html">
<img src = "bookshelf.jpg" alt = "" />
John Smith’s publications
</a>
```

>[!NOTE]
Der obige Ausschnitt dient der Illustration. Es wird empfohlen, die Komponente **Bild** zu verwenden.

Auch wenn es angeraten ist, einen Linktext bereitzustellen, der den Zweck des Links verdeutlicht ohne zusätzlichen Kontext zu benötigen, gibt es Fälle, in denen dies nicht möglich ist. Context free links can be used in the following cases, HTML examples of which can be found in [How to Meet Success Criterion 2.4.4](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs).

* Wenn der Linktext zu einer Liste eng zusammenhängender Links gehört und wenn das den Link umgebende Listenelement ausreichend Kontext liefert.
* Where the purpose of a link can be clearly identified from the *preceding* (not the following) paragraph text.
* Wenn der Link in einer Datentabelle enthalten ist und der Zweck über die zugehörigen Überschriften deutlich erkennbar ist.
* Wenn eine Liste mit Links in einem Satz Überschriften enthalten ist und die Überschrift einen ausreichenden Kontext liefert.
* Wenn eine Liste mit Links in einem geschachtelten Link enthalten ist und das übergeordnete Listenelement des geschachtelten Links einen ausreichenden Kontext liefert.

In einigen Fällen, in denen sich mehrere Links auf einer Seite befinden (von denen jeder das Ziel des Links durch komplexe, aber erforderliche Details angibt), kann es sinnvoll sein, eine alternative Version der Webseite anzubieten, die denselben Inhalt anzeigt, auf der der Linktext jedoch weniger ausführlich ist.

Alternatively, scripts can be used so that a minimal amount of text is provided within the link itself, but on activating an appropriate control positioned towards the top of the page, the link text is *expanded* into further detail. A similar approach is to use CSS to *hide* the full link from sighted users, but still output it in full to screen reader users. This falls outside the scope of this document, but more information on how this can be achieved can be found in the [More Information - Link Purpose (In Context) (2.4.4)](#more-information-link-purpose-in-context) section.

#### Weitere Informationen - Linkzweck (im Kontext) (2.4.4) {#more-information-link-purpose-in-context}

* [Erfolgskriterium 2.4.4 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html)
* [Erfolgskriterium 2.4.4 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-navigation-mechanisms-refs)
* [C7: Verwendung von CSS, um einen Teil des Linktextes auszublenden](https://www.w3.org/TR/2008/NOTE-WCAG20-TECHS-20081211/C7)

## Grundsatz 3: Verständlich {#principle-understandable}

[Grundsatz 3: Verständlich - Informationen und die Bedienung der Benutzerschnittstelle müssen verständlich sein.](https://www.w3.org/TR/WCAG20/#understandable)

### Machen Sie Inhalt lesbar und verständlich (3.1) {#make-text-content-readable-and-understandable}

[Richtlinie 3.1 Lesbar: Machen Sie Inhalt lesbar und verständlich.](https://www.w3.org/TR/WCAG20/#meaning)

### Sprache der Seite (3.1.1) {#language-of-page}

* Erfolgskriterium 3.1.1
* Level A
* Sprache der Seite: Die voreingestellte menschliche Sprache einer Webseite kann programmatisch bestimmt werden.

#### Zweck - Sprache der Seite (3.1.1) {#purpose-language-of-page}

Der Zweck dieses Erfolgskriteriums besteht darin, sicherzustellen, dass Texte und andere linguistische Inhalte fehlerfrei gerendert werden. Für Benutzer der Sprachausgabe stellt dies sicher, dass der Inhalt korrekt ausgesprochen wird, während bei visuellen Browsern die Wahrscheinlichkeit höher ist, dass bestimmte Zeichensätze richtig angezeigt werden.

#### Erfüllen - Sprache der Seite (3.1.1) {#how-to-meet-language-of-page}

To meet this success criterion, the default language of a web page can be identified using the `lang` attribute within the `<html>` element at the top of the page. Beispiel:

* If a page is written in British English, the `<html>` element should read:
   `<html lang = “en-gb”>`

* Eine Seite, die als US-Englisch wiedergegeben werden soll, sollte den folgenden Standard annehmen:
   `<html lang = “en-us”>`

**In AEM wird die Standardsprache Ihrer Seite beim Erstellen der Seite festgelegt, kann aber auch beim Bearbeiten einer Seite geändert werden, auf die** Sidekick **- Registerkarte &quot;** Seite **&quot;-** Seiteneigenschaften zugreifen kann... - Registerkarte **Erweitert** .

#### Weitere Informationen - Sprache der Seite (3.1.1) {#more-information-language-of-page}

* [Erfolgskriterium 3.1.1 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html)
* [Erfolgskriterium 3.1.1 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-doc-lang-id)
* Die Codes basieren auf ISO 639-1. Eine umfangreichere Liste der Codes für die einzelnen Sprachen finden Sie auf der [W3 Schools-Website](https://www.w3schools.com/tags/ref_language_codes.asp).

### Sprache von Teilen (3.1.2)  {#language-of-parts}

* Erfolgskriterium 3.1.2
* Level AA
* Sprache von Teilen: Die menschliche Sprache aller Abschnitte und Sätze im Inhalt kann programmatisch bestimmt werden. Ausgenommen sind Eigennamen, technische Fachbegriffe, Wörter einer unbestimmten Sprache und Wörter oder Wendungen, die Teil des Jargons des direkt umliegenden Textes sind.

#### Zweck - Sprache von Teilen (3.1.2) {#purpose-language-of-parts}

Der Zweck dieses Erfolgskriteriums ähnelt dem Zweck des Erfolgskriteriums [Sprache der Seite](#languageofpage). Es gilt jedoch für Webseiten, die auf einer Seite Inhalte im mehreren Sprachen enthalten (z. B. in Form von Zitaten oder wenig geläufigen Lehnwörtern).

Seiten, die dieses Erfolgskriterium erfüllen, bieten folgende Möglichkeiten:

* Software für die Braille-Übersetzung kann akzentuierte Zeichen einfügen.
* Die Sprachausgabe kann betroffene Wörter außerhalb der Standardsprache korrekt aussprechen.
* Übersetzungstools wie der Google Übersetzer können Inhalt korrekt von einer Sprache in eine andere übersetzen.

#### Erfüllen - Sprache von Teilen (3.1.2) {#how-to-meet-language-of-parts}

Mit dem Attribut `lang` können Änderungen der Sprache des Inhalts ermittelt werden. Ein deutschsprachiges Zitat (ISO 639-1-Code “de”) kann z. B. wie folgt angezeigt werden:

```xml
<blockquote cite = "John F. Kennedy" lang = "de">
     <p>Ich bin ein Berliner</p>
 </blockquote>
```

>[!NOTE]
Blockzitate werden in standardmäßigen Instanzen nicht unterstützt. Sie können eine benutzerdefinierte Komponente entwickeln, um dieses Feature zu unterstützen.

Auf ähnliche Weise kann der Browser ein wenig geläufiges Lehnwort oder eine Redewendung korrekt rendern, wenn das Element `span` wie folgt verwendet wird:

```xml
<p>The only French phrase I know is <span lang = “fr”>je ne sais quoi</code>.</p>
```

>[!NOTE]
Dieses Erfolgskriterium muss nicht beachtet werden, wenn Namen oder Städte in verschiedenen Sprachen vorkommen oder wenn Sie Lehnwörter oder Redewendungen verwenden, die in der Standardsprache gängig geworden sind (wie *Schadenfreude* im Englischen).

Um ein span-Element mit der entsprechenden Sprache hinzuzufügen, können Sie Ihren HTML-Code im Bearbeitungsmodus für den Quelltext im RTE manuell bearbeiten, damit er wie oben aussieht. Alternatively the `lang` attribute can be included in the RTE by a system administrator (see [Adding Support for Additional HTML Elements and Attributes](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

#### Weitere Informationen - Sprache von Teilen (3.1.2) {#more-information-language-of-parts}

* [Erfolgskriterium 3.1.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.htm)
* [Erfolgskriterium 3.1.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-meaning-other-lang-id)

### Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren (3.3) {#help-users-avoid-and-correct-mistakes}

[Richtlinie 3.3 Hilfestellung bei der Eingabe: Helfen Sie Benutzern, Fehler zu vermeiden und zu korrigieren.](https://www.w3.org/TR/WCAG20/#minimize-error)

### Beschriftungen oder Anweisungen (3.3.2) {#labels-or-instructions}

* Erfolgskriterium 3.3.2
* Level A
* Beschriftungen oder Anweisungen: Wenn der Inhalt eine Eingabe durch den Benutzer erfordert, werden Beschriftungen oder Anweisungen bereitgestellt.

#### Zweck - Beschriftungen oder Anweisungen (3.3.2) {#purpose-labels-or-instructions}

Das Bereitstellen von Anweisungen, die Menschen beim Ausfüllen von Formularen unterstützen, bildet einen entscheidenden Bestandteil der bewährten Verfahrenspraxis für eine benutzerfreundliche Oberfläche. Dies ist insbesondere für Menschen mit visuellen oder kognitiven Einschränkungen hilfreich, die das Layout eines Formulars und die Art der in einem bestimmten Formularfeld anzugebenden Daten andernfalls nur schwer nachvollziehen können.

Im AEM wird eine Standardbeschriftung eingefügt, wenn Sie eine Formularkomponente zur Seite hinzufügen, z. B. ein **Textfeld.** Dieser Standardtitel beruht auf dem Typ der Komponente. Auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds für das Feld können Sie Ihren eigenen Titel angeben. Es ist wichtig, dass Sie sicherstellen, dass Benutzer mithilfe von Beschriftungen leichter nachvollziehen können welche Daten in den einzelnen Formularkomponenten erwartet werden.

![cac-04](assets/cac-04.png)

Das Feld **Titel** muss für Feldelemente verwendet werden, weil es eine Beschriftung bereitstellt, die für Sprachausgabetechnologien verfügbar ist. Es reicht nicht aus, einfach nur eine Beschriftung im Text neben dem Feld anzugeben.

For some form components it is also possible to visually hide labels using the **Hide Title** checkbox. Labels hidden in this way are still available to assistive technology, but not displayed on the screen. While this can be a good approach in some situations it is usually best to include a visual label wherever possible, as some users may be looking at a very small section of the screen (one field at a time) and need the labels to identify the field correctly.

#### Bild-Schaltflächen {#image-buttons}

Wenn Bild-Schaltflächen verwendet werden (z. B. die Komponente **Bild-Schaltfläche**) liefert das Feld **Titel** auf der Registerkarte **Titel und Text** des Bearbeitungsdialogfelds den Alt-Text für das Bild und nicht die Beschriftung. Im folgenden Beispiel wurde daher für das Bild mit dem Text `Submit` im Bearbeitungsdialogfeld der Alt+Text `Submit` über das Feld **Titel** hinzugefügt.

![cac-05](assets/cac-05.png)

#### Gruppen von Formularfeldern {#groups-of-form-fields}

Wenn es eine Gruppe zusammenhängender Steuerelemente gibt, wie eine **Optionsfeldgruppe**, kann sowohl ein Titel für die Gruppe erforderlich sein als auch für die einzelnen Steuerelemente. Wenn Sie im AEM ein Set Optionsschaltflächen hinzufügen, enthält das Feld **Titel** diesen Gruppentitel, während die Titel der einzelnen Schaltflächen beim Erstellen der Optionsschaltflächen (**Elemente**) angegeben werden.

![cac-06](assets/cac-06.png)

Es gibt jedoch keine programmatische Zuordnung zwischen dem Gruppentitel und den Optionsschaltflächen. Der Titel muss beim Bearbeiten der Vorlage in die erforderlichen Tags `fieldset` und `legend` gesetzt werden, um diese Zuordnung herzustellen. Dies kann ausschließlich über die Bearbeitung des Seitenquellcodes erfolgen. Alternativ kann ein Systemadministrator die Unterstützung für diese Elemente hinzufügen, damit sie im Dialogfeld **Feldeigenschaften** angezeigt werden (siehe [Unterstützung für zusätzliche HTML-Elemente und -Attribute hinzufügen](/help/sites-administering/rte-accessible-content.md#adding-support-for-additional-html-elements-and-attributes)).

#### Weitere Aspekte für Formulare {#additional-considerations-for-forms}

Wenn Daten in einem bestimmten Format eingegeben werden müssen, sollten Sie die in der Beschriftung verdeutlichen. Wenn z. B. ein Datum im Format `DD-MM-YYYY` eingegeben werden soll, fügen Sie diese Angabe in die Beschriftung ein. Dies führt dazu, dass die Beschriftung automatisch zusammen mit dem gewünschten Format ausgegeben wird, wenn Benutzer der Sprachausgabe auf das Feld treffen.

Wenn die Eingabe in ein Feld erforderlich ist, verdeutlichen Sie dies, indem Sie das Wort „erforderlich“ in die Beschriftung einfügen. AEM adds an asterisk when a field is required, but it would be ideal to include the word `required`in the label itself (in the **Title** field in the edit dialog).

![cac-07](assets/cac-07.png)

Auch die Positionierung von Beschriftungen ist wichtig, da sie das Auffinden der entsprechenden Felder erleichtert. Dies ist besonders wichtig, wenn es sich um komplexe Formulare handelt. Halten Sie sich an folgende Richtlinien:

* Kontrollkästchen oder Optionsschaltflächen: 
Beschriftungen direkt rechts neben dem Feld platzieren.
* Alle anderen Formularkomponenten (z. B. Textfelder, Kombinationsfelder): 
Beschriftungen entweder direkt über dem Feld oder direkt links vom Feld platzieren.

In simple forms with very limited functionality, appropriately labelling a `Submit` button can act as a label for the adjacent field (for example `Search`). Dies ist in Situationen nützlich, in denen wenig Platz für die Beschriftung vorhanden ist.

#### Weitere Informationen - Beschriftungen oder Anweisungen (3.3.2) {#more-information-labels-or-instructions}

* [Erfolgskriterium 3.3.2 verstehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)
* [Erfolgskriterium 3.3.2 erfüllen](https://www.w3.org/WAI/WCAG20/quickref/#qr-minimize-error-cues)

