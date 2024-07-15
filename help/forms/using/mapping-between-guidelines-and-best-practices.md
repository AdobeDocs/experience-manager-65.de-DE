---
title: Richtlinien und Best Practices für die Barrierefreiheit beim Erstellen von Formularen in Forms Designer
description: Best Practices und Richtlinien für Barrierefreiheit bei der Entwicklung von Formularen in Forms Designer.
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 38fb132f0eb5b710745db11e7ddf59efc0f0ae95
workflow-type: tm+mt
source-wordcount: '3366'
ht-degree: 2%

---

# Zuordnung zwischen Richtlinien und Best Practices

In den folgenden Abschnitten werden die Richtlinien zu Abschnitt 508 und WCAG den in diesem Handbuch beschriebenen Best Practices zugeordnet.

## § 1194.21 Leitlinie Beschreibung und Best Practices

### Abschnitt 508 §1194.21: Software-Anwendungen und Betriebssysteme

| § 1194.21 Leitlinie | Leitlinienbeschreibung | Erforderliche LiveCycle Designer Best Practices für die Einhaltung von Vorschriften | Anmerkungen |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| a) | Wenn Software für die Ausführung auf einem System mit Tastatur entwickelt wird, müssen Produktfunktionen von einer Tastatur ausgeführt werden können, bei der die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell erkennbar ist. | <li> 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind </li><li> 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind</li> | |
| b) | Anwendungen dürfen aktivierte Funktionen anderer Produkte, die als Barrierefreiheitsfunktionen gekennzeichnet sind, nicht stören oder deaktivieren, wenn diese Funktionen gemäß Industriestandards entwickelt und dokumentiert werden. Anwendungen dürfen auch aktivierte Funktionen von Betriebssystemen, die als Funktionen zur Barrierefreiheit gekennzeichnet sind, nicht stören oder deaktivieren, wenn die Programmschnittstelle für diese Funktionen der Barrierefreiheit vom Hersteller des Betriebssystems dokumentiert wurde und dem Produktentwickler zur Verfügung steht. | Keine LiveCycle Designer-spezifische Techniken - diese Richtlinie wird von Adobe Reader für PDF forms gehandhabt. | |
| c) | Es ist eine klar definierte Bildschirmanzeige des aktuellen Fokus anzugeben, die sich zwischen interaktiven Schnittstellenelementen bewegt, wenn sich der Eingabefokus ändert. Der Fokus muss programmatisch offen gelegt werden, damit Hilfstechnologien Fokus- und Fokusänderungen nachverfolgen können. | 2.3 Wählen Sie die richtigen Steuerelemente aus, um sicherzustellen, dass der Fokus sowohl programmatisch als auch visuell offen gelegt wird. Verwenden Sie immer die Standardsteuerungen. | |
| d) | Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein. | <ul><li>2.1 Formulare einfach und benutzerfreundlich halten</li> <li>2.1.1 Verschieben, Blinken oder Blinken von Inhalten vermeiden</li> <li>2.2 Formulareigenschaften zum Generieren von Informationen zur Barrierefreiheit konfigurieren</li> <li>2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente</li></ul> | |
| e) | Wenn Bitmapbilder verwendet werden, um Steuerelemente, Statusanzeigen oder andere programmatische Elemente zu identifizieren, muss die diesen Bildern zugewiesene Bedeutung während der gesamten Leistung einer Anwendung konsistent sein. | <ul><li>2.4 Textäquivalente für Bilder angeben</li><li> 2.5 Anzugeben richtige Beschriftungen für Formularsteuerelemente Dieser Standard gilt nur, wenn Sie dasselbe Bild an mehreren Stellen in einem Formular verwenden. Die Verwendung bildbasierter benutzerdefinierter Steuerelemente wird nicht empfohlen. Verwenden Sie stattdessen nur die von LiveCycle Designer bereitgestellten Standardsteuerelemente. Wenn Sie in Ihren Steuerelementen Bilder verwenden, stellen Sie immer sicher, dass sie konsistent verwendet werden.</li> | |
| f) | Über die Funktionen des Betriebssystems für die Textdarstellung werden Textinformationen bereitgestellt. Die Mindestinformationen, die bereitgestellt werden müssen, sind Textinhalt, Texteingabe-Caret-Position und Textattribute. | 2.3 Wählen Sie die richtigen Steuerelemente Vermeiden Sie die Verwendung von Bildern zur Vermittlung von Textinformationen. Verwenden Sie nicht benutzerdefinierte Eingabekomponenten, die die Texteigenschaften möglicherweise nicht ordnungsgemäß für das Betriebssystem verfügbar machen, sondern immer die Standardsteuerelemente. | |
| g) | Die Anwendungen dürfen vom Benutzer ausgewählte Kontrastmittel und Farbauswahlen sowie andere individuelle Anzeigenattribute nicht außer Kraft setzen. | Keine LiveCycle Designer-spezifische Techniken | Verwenden Sie nach Möglichkeit die standardmäßigen Standardfarben des Systems. |
| h) | Wenn Animationen angezeigt werden, müssen die Informationen nach Wahl des Nutzers mindestens in einem nicht animierten Präsentationsmodus angezeigt werden können. | 2.1 Formulare einfach und einfach zu verwenden Vermeiden Sie die Verwendung von Animationen in Ihren Formularen oder stellen Sie separate Versionen bereit, in denen Animationen durch statische Bilder ersetzt werden. | |
| i) | Farbkodierung darf nicht als einziges Mittel zur Informationsübermittlung, zur Angabe einer Aktion, zur Aufforderung einer Antwort oder zur Unterscheidung eines visuellen Elements verwendet werden. | 2.8 verantwortungsvolle Verwendung der Farbe | |
| j) | Wenn ein Produkt es einem Benutzer ermöglicht, die Farb- und Kontrasteinstellungen anzupassen, ist eine Vielzahl von Farbauswahlen anzugeben, die einen Bereich von Kontrastwerten erzeugen können. | Nicht zutreffend | Diese Funktion wird im Allgemeinen von Adobe Reader und nicht vom Formularentwickler bereitgestellt. |
| k) | Die Software darf keine blinkenden oder blinkenden Texte, Objekte oder andere Elemente mit einer Blinkfrequenz größer als 2 Hz und kleiner als 55 Hz verwenden. | 2.1.1 Verschieben, Blinken oder Blinken von Inhalten vermeiden | |
| l) | Wenn elektronische Formulare verwendet werden, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf die Informationen, Feldelemente und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars, einschließlich aller Richtungen und Hinweise, erforderlich sind. | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |

### § 508 § 11942: Internetbasierte Intranet- und Internetinformationen und Anwendungen

| §11942 Leitlinie | Leitlinienbeschreibung | Erforderliche LiveCycle Designer Best Practices für die Einhaltung von Vorschriften | Anmerkungen |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| a) | Für jedes nichttextliche Element ist ein Textäquivalent anzugeben (z. B. über &quot;alt&quot;, &quot;long desc&quot; oder im Elementinhalt). | 2.4 Textäquivalente für Bilder angeben | |
| b) | Gleichwertige Alternativen für alle multimedialen Darstellungen sind mit der Präsentation zu synchronisieren. | 2.12 Alle Multimedia-Inhalte zugänglich machen | |
| c) | Webseiten sind so zu gestalten, dass alle farblich vermittelten Informationen auch farblos verfügbar sind, beispielsweise aus Kontext oder Markup. | 2.8 verantwortungsvolle Verwendung der Farbe | |
| d) | Die Dokumente sind so anzuordnen, dass sie lesbar sind, ohne dass ein entsprechendes Stylesheet erforderlich ist. | Nicht zutreffend | |
| e) | Redundante Textlinks sind für jeden aktiven Bereich einer serverseitigen Imagemap bereitzustellen. | Nicht zutreffend | |
| f) | Clientseitige Imagemaps sind anstelle von serverseitigen Imagemaps bereitzustellen, es sei denn, die Bereiche können nicht mit einer verfügbaren geometrischen Form definiert werden. | Nicht zutreffend | |
| g) | Zeilen- und Spaltenüberschriften werden für Datentabellen angegeben. | 2.9 Überschriftzellen für Tabellen bereitstellen | |
| h) | Markup wird verwendet, um Datenzellen und Kopfzeilenzellen für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften zuzuordnen. | 2.9 Überschriftzellen für Tabellen bereitstellen | |
| i) | Die Bilder werden mit Text beschriftet, der die Identifizierung und Navigation von Rahmen erleichtert. | Nicht zutreffend | |
| j) | Seiten müssen so ausgelegt sein, dass sie ein Flackern des Bildschirms mit einer Frequenz von mehr als 2 Hz und weniger als 55 Hz vermeiden. | 2.1 Formulare einfach und benutzerfreundlich halten | |
| k) | Es ist eine reine Textseite mit entsprechenden Informationen oder Funktionen bereitzustellen, damit eine Website den Bestimmungen dieses Teils entspricht, wenn die Einhaltung nicht auf andere Weise erreicht werden kann. Der Inhalt der reinen Textseite wird aktualisiert, sobald sich die primäre Seite ändert. | Nicht zutreffend | |
| l) | Wenn Seiten Skriptsprachen verwenden, um Inhalte anzuzeigen oder Schnittstellenelemente zu erstellen, müssen die vom Skript bereitgestellten Informationen mit funktionalem Text identifiziert werden, der von Hilfstechnologien gelesen werden kann. | 2.11 Unterbrechungsskripten vermeiden | |
| m) | Wenn eine Webseite erfordert, dass ein Applet, ein Plug-in oder eine andere Anwendung im Client-System vorhanden ist, um Seiteninhalte zu interpretieren, muss die Seite einen Link zu einem Plug-in oder Applet bereitstellen, das den Bestimmungen von §1194.21(a) bis (l) entspricht. | Nicht zutreffend | Webseiten, die auf PDF forms verlinken, sollten einen Link zu Adobe Reader enthalten. |
| n) | Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugang zu den Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Richtungen und Hinweise. | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |
| o) | Es ist ein Verfahren vorzusehen, das es den Nutzern ermöglicht, sich wiederholende Navigationslinks zu überspringen. | 2.10 Navigierbare Formularstruktur bereitstellen | |
| p) | Wenn eine zeitgesteuerte Antwort erforderlich ist, muss der Benutzer benachrichtigt werden und genügend Zeit haben, um anzugeben, dass mehr Zeit erforderlich ist. | 2.11 Unterbrechungsskripten vermeiden | |

### WCAG 1.0 - Checkpoints der Priorität 1

| Checkpoint | Checkpoint-Beschreibung | Erforderliche LiveCycle Designer Best Practices für die Einhaltung von Vorschriften | Anmerkungen |
|------------|------------------------|-----------------------------------------------------------|-------|
| [1.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-text-equivalent) | Geben Sie ein Textäquivalent für jedes Nicht-Text-Element an (z. B. über &quot;alt&quot;, &quot;longdesc&quot;oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIF), Applets und programmatische Objekte, ASCII-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Töne (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audio-Tracks von Videos und Videos. | <ul><li>2.4 Textäquivalente für Bilder angeben</li> <li>2.12 Alle Multimedia-Inhalte zugänglich machen</li> | |
| [1.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-redundant-server-links) | Stellen Sie redundante Textlinks für jeden aktiven Bereich einer serverseitigen Imagemap bereit. | Nicht zutreffend | |
| [1,3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-auditory-descriptions) | Bevor Benutzeragenten automatisch das Textäquivalent eines visuellen Tracks vorlesen können, geben Sie eine auditive Beschreibung der wichtigen Informationen des visuellen Tracks einer Multimedia-Präsentation. | 2.12 Alle Multimedia-Inhalte zugänglich machen | |
| [1,4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-synchronize-equivalents) | Synchronisieren Sie für jede zeitbasierte Multimedia-Präsentation (z. B. einen Film oder eine Animation) gleichwertige Alternativen (z. B. Untertitel oder auditive Beschreibungen der visuellen Spur) mit der Präsentation. | 2.12 Alle Multimedia-Inhalte zugänglich machen | |
| [2.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-convey) | Stellen Sie sicher, dass alle mit Farbe vermittelten Informationen auch ohne Farbe verfügbar sind, z. B. aus Kontext oder Markup. | 2.8 verantwortungsvolle Verwendung der Farbe | |
| [4.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-changes) | Identifizieren Sie eindeutig Änderungen in der natürlichen Sprache des Textes eines Dokuments und von Textäquivalenten (z. B. Beschriftungen). | 2.13 Sprachänderungen identifizieren | |
| [5.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-headers) | Identifizieren Sie für Datentabellen Zeilen- und Spaltenüberschriften. | 2.9 Überschriftzellen für Tabellen bereitstellen | |
| [5.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-structure) | Verwenden Sie für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften Markup, um Datenzellen und Kopfzeilenzellen zuzuordnen. | 2.9 Überschriftzellen für Tabellen bereitstellen | |
| [6.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-order-style-sheets) | Organisieren Sie Dokumente, damit sie ohne Stylesheets gelesen werden können. Wenn beispielsweise ein HTML-Dokument ohne verknüpfte Stylesheets gerendert wird, muss es dennoch möglich sein, das Dokument zu lesen. | Nicht zutreffend | |
| [6.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-dynamic-source) | Stellen Sie sicher, dass Äquivalente für dynamische Inhalte aktualisiert werden, wenn sich der dynamische Inhalt ändert. | 2.11 Unterbrechungsskripten vermeiden | |
| [6.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-scripts) | Stellen Sie sicher, dass Seiten verwendet werden können, wenn Skripte, Applets oder andere programmatische Objekte deaktiviert sind oder nicht unterstützt werden. Ist dies nicht möglich, stellen Sie gleichwertige Informationen auf einer alternativ zugänglichen Seite bereit. | 2.11 Unterbrechungsskripten vermeiden | |
| [7.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-flicker) | Solange Benutzeragenten es Benutzern erlauben, das Flackern zu kontrollieren, sollten Sie vermeiden, dass der Bildschirm flackert. | 2.1 Formulare einfach und benutzerfreundlich halten | |
| [9.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-client-side-maps) | Stellen Sie clientseitige Imagemaps anstelle serverseitiger Imagemaps bereit, es sei denn, die Regionen können nicht mit einer verfügbaren geometrischen Form definiert werden. | Nicht zutreffend | |
| [11.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-alt-pages) | Wenn Sie nach besten Kräften keine barrierefreie Seite erstellen können, stellen Sie einen Link zu einer alternativen Seite bereit, die W3C-Technologien verwendet, auf die zugegriffen werden kann, gleichwertige Informationen (oder Funktionen) aufweist und so oft wie die nicht zugängliche (ursprüngliche) Seite aktualisiert wird. | Nicht zutreffend | |
| [12.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-titles) | Geben Sie jedem Frame einen Titel, um die Identifizierung und Navigation von Frames zu erleichtern. | Nicht zutreffend | |
| [14.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-simple-and-straightforward) | Verwenden Sie die für den Inhalt einer Site am einfachsten geeignete Sprache. | 2.1 Formulare einfach und benutzerfreundlich halten | |

### WCAG 1.0 Priorität 2 - Checkpoints

| Priorität 2 Prüfpunkt | Checkpoint-Beschreibung | Erforderliche LiveCycle Best Practices für die Einhaltung von | Anmerkungen |
|------------|------------------------|-------------------------------------------------|-------|
| [2.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-color-contrast) | Stellen Sie sicher, dass Vordergrund- und Hintergrundfarbkombinationen einen ausreichenden Kontrast bieten, wenn sie von einer Person mit Farbdefiziten angezeigt werden oder auf einem Schwarzweißbildschirm angezeigt werden. [Priorität 2 für Bilder, Priorität 3 für Text]. | 2.8 verantwortungsvolle Verwendung der Farbe | |
| [3.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-markup) | Wenn eine geeignete Markup-Sprache vorhanden ist, verwenden Sie Markup anstelle von Bildern, um Informationen zu vermitteln. | <ul><li>2.1 Formulare einfach und benutzerfreundlich halten</li><li> 2.1.1 Verschieben, Blinken oder Blinken von Inhalten vermeiden</li> <li>2.2 Konfigurieren Sie Formulareigenschaften zum Generieren von Barrierefreiheitsinformationen Verwenden Sie immer tatsächlichen Text anstelle von Textbildern.</li> | |
| [3.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-identify-grammar) | Erstellen Sie Dokumente, die auf veröffentlichte formale Grammatiken überprüfen. | | PDF forms müssen mit der veröffentlichten PDF-Spezifikation übereinstimmen, damit sie in Adobe Reader gerendert werden können. |
| [3.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-style-sheets) | Mit Stylesheets können Sie Layout und Präsentation steuern. | Nicht zutreffend | |
| [3.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-relative-units) | Verwenden Sie relative anstelle absoluter Einheiten in den Markup-Sprachattributwerten und den Stylesheet-Eigenschaftswerten. | Nicht zutreffend | |
| [3,5](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-logical-headings) | Verwenden Sie Kopfzeilenelemente, um die Dokumentstruktur zu vermitteln und sie gemäß Spezifikation zu verwenden. | 2.10 Navigierbare Formularstruktur bereitstellen | |
| [3,6](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-list-structure) | Markieren Sie Listen und Listenelemente ordnungsgemäß. | 2.10.3 Markieren von Listen Markieren von listenbasiertem Inhalt als Listen mit den Rollen Liste und Listenelement . | |
| [3,7](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-quotes) | Markieren Sie Zitate. Verwenden Sie kein Anführungszeichen für Formatierungseffekte wie Einzüge. | Nicht zutreffend | |
| [5,3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-table-for-layout) | Verwenden Sie keine Tabellen für das Layout, es sei denn, die Tabelle ist bei der Linearisierung sinnvoll. Wenn die Tabelle andernfalls keinen Sinn ergibt, geben Sie ein alternatives Äquivalent an (bei dem es sich um eine linearisierte Version handeln kann). | Keine spezifischen LiveCycle-Techniken | Es gibt keinen Grund, Tabellen für das Layout in LiveCycle-Formularen zu verwenden. Verwenden Sie stattdessen die Palette &quot;Layout&quot;, um die Formularfelder in einem Rastermuster zu positionieren. Verwenden Sie eine Tabelle nur, wenn Sie tabellenspezifische Funktionen wie Tabellenüberschriften verwenden. |
| [5,4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-table-layout) | Wenn eine Tabelle für das Layout verwendet wird, dürfen Sie für die visuelle Formatierung keine strukturellen Markierungen verwenden. | Keine spezifischen LiveCycle-Techniken | |
| [6.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-operable-scripts) | Stellen Sie bei Skripten und Applets sicher, dass Ereignishandler geräteunabhängig eingegeben werden. | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| [6.5](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-fallback-page) | Stellen Sie sicher, dass dynamische Inhalte zugänglich sind, oder stellen Sie eine alternative Präsentation oder Seite bereit. | 2.11 Unterbrechungsskripten vermeiden | |
| [7.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-blinking) | Solange Benutzeragenten es Benutzern nicht ermöglichen, das Blinken zu steuern, vermeiden Sie, dass Inhalte blinken (d. h. ändern Sie die Präsentation regelmäßig, z. B. ein- und ausschalten). | 2.1 Formulare einfach und benutzerfreundlich halten | |
| [7.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-movement) | Solange Benutzeragenten es Benutzern ermöglichen, bewegte Inhalte einzufrieren, sollten Sie das Verschieben von Seiten vermeiden. | 2.1 Formulare einfach und benutzerfreundlich halten | |
| [7,4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-periodic-refresh) | Bevor Benutzeragenten die Möglichkeit bieten, die Aktualisierung zu stoppen, erstellen Sie keine regelmäßig automatisch aktualisierten Seiten. | Nicht zutreffend | |
| [7,5](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-no-auto-forward) | Solange Benutzeragenten nicht die Möglichkeit bieten, die automatische Weiterleitung zu stoppen, sollten Sie Markup nicht verwenden, um Seiten automatisch umzuleiten. Konfigurieren Sie stattdessen den Server für Umleitungen. | Nicht zutreffend | |
| [8.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-directly-accessible) | Stellen Sie programmatische Elemente wie Skripte und Applets direkt barrierefrei oder mit Hilfstechnologien kompatibel [Priorität 1 ein, wenn Funktionalität wichtig ist und nicht an anderer Stelle angezeigt wird, andernfalls Priorität 2.] | 2.11 Unterbrechungsskripten vermeiden | |
| [9.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-keyboard-operable) | Stellen Sie sicher, dass jedes Element, das über eine eigene Schnittstelle verfügt, geräteunabhängig betrieben werden kann. | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| [9.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-device-independent-events) | Geben Sie für Skripte logische Ereignishandler anstelle geräteabhängiger Ereignishandler an. | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| [10.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-pop-ups) | Solange Benutzeragenten es Benutzern nicht erlauben, erstellte Fenster zu deaktivieren, werden keine Popups oder andere Fenster angezeigt und das aktuelle Fenster wird nicht geändert, ohne den Benutzer darüber zu informieren. | 2.11 Unterbrechungsskripten vermeiden | |
| [10.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-unassociated-labels) | Bevor Benutzeragenten explizite Verknüpfungen zwischen Beschriftungen und Formularsteuerelementen unterstützen, stellen Sie für alle Formularsteuerelemente mit implizit verknüpften Beschriftungen sicher, dass die Beschriftung richtig positioniert ist. | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |
| [11.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-latest-w3c-specs) | Verwenden Sie W3C-Technologien, wenn sie für eine Aufgabe verfügbar und geeignet sind, und verwenden Sie die neuesten Versionen, wenn sie unterstützt werden. | Nicht zutreffend | |
| [11.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-avoid-deprecated) | Vermeiden Sie veraltete Funktionen von W3C-Technologien. | Nicht zutreffend | |
| [12.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-frame-longdesc) | Beschreiben Sie den Zweck von Frames und die Art und Weise, in der Frames miteinander in Beziehung stehen, wenn dies nicht allein durch Frame-Titel erkennbar ist. | Nicht zutreffend | |
| [12.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-group-information) | Teilen Sie große Informationsblöcke in besser verwaltbare Gruppen auf, wo es sich als normal und angemessen erweist. | 2.10 Navigierbare Formularstruktur bereitstellen | |
| [12.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-associate-labels) | Verknüpfen Sie Beschriftungen explizit mit ihren Steuerelementen. | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |
| [13.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-meaningful-links) | Identifizieren Sie eindeutig die Zielgruppe jedes Links. | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente 2.5.6 Linktext bereitstellen | |
| [13.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-use-metadata) | Stellen Sie Metadaten bereit, um semantische Informationen zu Seiten und Sites hinzuzufügen. | Nicht zutreffend | |
| [13.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-site-description) | Geben Sie Informationen zum allgemeinen Layout einer Site (z. B. eine Sitemap oder ein Inhaltsverzeichnis) an. | 2.10 Navigierbare Formularstruktur bereitstellen | |
| [13.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html#tech-clear-nav-mechanism) | Verwenden Sie die Navigationsmechanismen konsistent. | 2.10 Navigierbare Formularstruktur bereitstellen | Verwenden Sie Masterseiten, um konsistente Navigationsinhalte zu erstellen. |

### WCAG 2.0-Erfolgskriterien

| Prioritätsachse 1 G 2 Prüfpunkte | Erforderliche LiveCycle Best Practices für die Einhaltung von | Anmerkungen |
| --- | --- | --- |
| 1.1 [Textalternativen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv.html) | | |
| 1.1.1 [Nichttextlicher Inhalt](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html) | 2.4 Textäquivalente für Bilder angeben | |
| | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |
| 1.2 [Zeitbasierte Medien](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv.html) | | |
| 1.2.1 [Nur-Audio und Nur-Video (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.2 [Untertitel (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.3 [Audiobeschreibung oder Medienalternative (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.4 [Untertitel (Live)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.5 [Audiobeschreibung (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.6 [Signatursprache (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-sign.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.7 [Erweiterte Audiobeschreibung (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-extended-ad.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.8 [Medienalternative (aufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-text-doc.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.2.9 [Nur-Audio (Live)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-live-audio-only.html) | 2.12 Stellen Sie sicher, dass alle Audio- und Videoinhalte verfügbar sind. | |
| 1.3 [Anpassbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation.html) | | |
| 1.3.1 [Informationen und Beziehungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html) | 2.9 Überschriftzellen für Tabellen bereitstellen | |
| 1.3.2 [Bedeutungstragende Reihenfolge](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-sequence.html) | 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.10 Navigierbare Formularstruktur bereitstellen | |
| 1.3.3 [Sensorische Eigenschaften](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html) | 2.8 verantwortungsvolle Verwendung der Farbe | |
| 1.4 [Unterscheidbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast.html) | | |
| 1.4.1 [Verwendung von Farbe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-without-color.html) | 2.8 verantwortungsvolle Verwendung der Farbe | |
| 1.4.2 [Audio-Steuerelement](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-dis-audio.html) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.3 [Kontrast (Minimum)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) | 2.8 verantwortungsvolle Verwendung der Farbe | |
| 1.4.4 [Textgröße ändern](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.5 [Bilder von Text](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.6 [Kontrast (erweitert)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast7.html) | 2.8 verantwortungsvolle Verwendung der Farbe | |
| 1.4.7 [Geringer oder kein Hintergrundaudio](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-noaudio.html) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.9 [Bilder von Text (keine Ausnahme)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-images.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.1 [Auf Tastatur zugreifen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation.html) | | |
| 2.1.1 [Tastatur](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-keyboard-operable.html) | 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| 2.1.2 [Keine Tastaturfalle](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-trapping.html) | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| 2.1.3 [Tastatur (keine Ausnahme)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-all-funcs.html) | 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.7 Sicherstellen, dass Formularsteuerelemente über die Tastatur zugänglich sind | |
| 2.2 [ Ausreichend Zeit](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits.html) | | |
| 2.2.1 [Zeiteinteilung anpassbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.2 [ Anhalten, Beenden, Ausblenden](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html) | 2.1 Formulare einfach und benutzerfreundlich halten | |
| 2.2.3 [Keine Zeit](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-no-exceptions.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.4 [Unterbrechungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.5 [Erneute Authentifizierung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-server-timeout.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.3 [Anfälle] | | |
| 2.3.1 [Grenzwert von 3 Flash oder darunter](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html) | 2.1 Formulare einfach und benutzerfreundlich halten | |
| 2.3.2 [Drei Flash](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-three-times.html) | 2.1 Formulare einfach und benutzerfreundlich halten | |
| 2.4 [Navigierbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms.html) | | |
| 2.4.1 [ Blöcke umgehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html) | 2.10 Navigierbare Formularstruktur bereitstellen | |
| 2.4.2 [Seite mit Titel versehen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html) | Keine spezifischen LiveCycle-Techniken | |
| 2.4.3 [Fokus-Reihenfolge](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-order.html) | 2.6 Stellen Sie sicher, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| 2.4.4 [Link-Zweck (im Kontext)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html) | Keine spezifischen LiveCycle-Techniken | Der Linkzweck hängt davon ab, ob Autoren sinnvollen Text für verknüpfte Elemente auswählen. |
| 2.4.5 [Verschiedene Methoden](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-mult-loc.html) | 2.10 Navigierbare Formularstruktur bereitstellen | |
| 2.4.6 [Überschriften und Beschriftungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-descriptive.html) | <ul><li>2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente</li><li>2.10 Navigierbare Formularstruktur bereitstellen</li> | |
| 2.4.7 [Fokus sichtbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-visible.html) | Keine spezifischen LiveCycle-Techniken | Der Standardfokus in LiveCycle-Formularen wird angezeigt. |
| 2.4.8 [Position](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-location.html) | Keine spezifischen LiveCycle-Techniken | Nicht anwendbar: Für LiveCycle-Formulare sind keine Navigationssysteme erforderlich. |
| 2.4.9 [Link-Zweck (nur Link)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-link.html) | Keine spezifischen LiveCycle-Techniken | Der Linkzweck hängt davon ab, ob Autoren sinnvollen Text für verknüpfte Elemente auswählen. |
| 2.4.10 [Abschnittsüberschriften](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-headings.html) | 2.10 Navigierbare Formularstruktur bereitstellen | |
| 3.1 [Lesbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning.html) | | |
| 3.1.1 [Sprache der Seite](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html) | 2.13 Identifizieren der natürlichen Sprache und aller Sprachänderungen | |
| 3.1.2 [Sprache von Teilen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.html) | 2.13 Identifizieren der natürlichen Sprache und aller Sprachänderungen | |
| 3.1.3 [Ungewöhnliche Wörter](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-idioms.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.4 [Abkürzungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-located.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.5 [Lesestufe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-supplements.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.6 [Straffreiheit](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-pronunciation.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.2 [Vorhersehbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior.html) | | |
| 3.2.1 [Auf Fokus](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-receive-focus.html) | 2.11 Unterbrechungsskripten vermeiden | |
| 3.2.2 [Bei Eingabe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-unpredictable-change.html) | 2.11 Unterbrechungsskripten vermeiden | |
| 3.2.3 [Konsistente Navigation](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-locations.html) | 2.10 Navigierbare Formularstruktur bereitstellen | |
| 3.2.4 [Konsistente Erkennung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-functionality.html) | <ul><li>2.3 Auswählen der richtigen Steuerelemente</li><li>2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente</li> | |
| 3.2.5 [Änderung bei Anforderung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html) | 2.11 Unterbrechungsskripten vermeiden | |
| 3.3 [Hilfestellung bei der Eingabe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error.html) | | |
| 3.3.1 [Fehlererkennung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-identified.html) |  | LiveCycle Designer bietet Tools zum Markieren von Formularfeldern nach Bedarf und zum Durchführen der Überprüfung der Formulareingabe. |
| 3.3.2 [Beschriftungen oder Anweisungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html) | 2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente | |
| 3.3.3 [Fehlerempfehlung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-suggestions.html) |  | LiveCycle Designer bietet Tools zum Markieren von Formularfeldern nach Bedarf und zum Durchführen der Überprüfung der Formulareingabe. |
| 3.3.4 [Fehlervermeidung (rechtliche, finanzielle, Daten)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.3.5 [Hilfe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-context-help.html) | Keine spezifischen LiveCycle-Techniken | |
| 3.3.6 [Fehlervermeidung (alle)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible-all.html) | Keine spezifischen LiveCycle-Techniken | |
| 4.1 [Kompatibel](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat.html) | | |
| 4.1.1 [Parsing](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-parses.html) | Keine spezifischen LiveCycle-Techniken | |
| 4.1.2 [Name, Rolle, Wert](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html) | <ul><li>2.3 Auswählen der richtigen Steuerelemente</li> <li>2.5 Angeben der richtigen Beschriftungen für Formularsteuerelemente</li> | |



