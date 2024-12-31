---
title: Richtlinien und Best Practices für die Barrierefreiheit beim Erstellen von Formularen in Forms Designer
description: Best Practices und Richtlinien für die Barrierefreiheit bei der Entwicklung von Formularen in Forms Designer.
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 0948231a-bd9e-4d29-946d-2d8c17e27c28
source-git-commit: 16b46340c5e0775d19f22f57bca5ea9ab584c51e
workflow-type: tm+mt
source-wordcount: '3366'
ht-degree: 100%

---

# Zuordnung zwischen Richtlinien und Best Practices

In den folgenden Abschnitten werden die Richtlinien zu Section 508 und WCAG den in diesem Handbuch beschriebenen Best Practices zugeordnet.

## § 1194.21 Richtlinienbeschreibung und Best Practices

### Section 508 §1194.21: Software-Anwendungen und Betriebssysteme

| § 1194.21 Richtlinie | Richtlinienbeschreibung | Erforderliche Best Practices für LiveCycle Designer zur Einhaltung der Richtlinien | Anmerkungen |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| (a) | Wenn Software für die Ausführung auf einem System mit Tastatur entwickelt wird, müssen die Produktfunktionen von einer Tastatur ausgeführt werden können, bei der die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell erkennbar ist. | <li> 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können </li><li> 2.6 Sicherstellen, dass die Leserichtung und die Tab-Reihenfolge korrekt sind</li> | |
| (b) | Anwendungen dürfen aktivierte Funktionen anderer Produkte, die als Barrierefreiheitsfunktionen gekennzeichnet sind, nicht stören oder deaktivieren, wenn diese Funktionen gemäß Industriestandards entwickelt und dokumentiert worden sind. Anwendungen dürfen auch aktivierte Funktionen von Betriebssystemen, die als Barrierefreiheitsfunktionen gekennzeichnet sind, nicht stören oder deaktivieren, wenn die Programmschnittstelle für diese Barrierefreiheitsfunktionen vom Hersteller des Betriebssystems dokumentiert wurde und den Entwickelnden des Produkts zur Verfügung steht. | Keine für den LiveCycle Designer spezifische Techniken – diese Richtlinie wird vom Adobe Reader für PDF-Formulare gehandhabt. | |
| (c) | Es ist eine klar definierte Bildschirmanzeige des aktuellen Fokus anzugeben, die sich zwischen interaktiven Schnittstellenelementen bewegt, wenn sich der Eingabefokus ändert. Der Fokus muss programmatisch offen gelegt werden, damit Hilfstechnologien den Fokus und Fokusänderungen nachverfolgen können. | 2.3 Wählen Sie die richtigen Steuerelemente aus, um sicherzustellen, dass der Fokus sowohl programmatisch als auch visuell offen gelegt wird. Verwenden Sie immer die Standardsteuerelemente. | |
| (d) | Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Funktionsweise und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein. | <ul><li>2.1 Formulare sind einfach und benutzerfreundlich zu halten</li> <li>2.1.1 Sich bewegende, blinkende oder aufblitzende Inhalte sind zu vermeiden</li> <li>2.2 Konfigurieren von Formulareigenschaften zum Generieren von Barrierefreiheits-Informationen</li> <li>2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente</li></ul> | |
| (e) | Wenn Bitmap-Bilder zur Identifizierung von Steuerelementen, Statusanzeigen oder anderen programmatischen Elementen verwendet werden, muss die diesen Bildern zugewiesene Bedeutung während der gesamten Ausführung einer Anwendung konsistent sein. | <ul><li>2.4 Angeben von Textäquivalenten für Bilder</li><li> 2.5 Formulare mit den richtigen Steuerelementen versehen: Dieser Standard gilt nur, wenn Sie dasselbe Bild an mehreren Stellen in einem Formular verwenden. Die Verwendung bildbasierter benutzerdefinierter Steuerelemente wird nicht empfohlen. Verwenden Sie stattdessen nur die von LiveCycle Designer bereitgestellten Standardsteuerelemente. Wenn Sie in Ihren Steuerelementen doch Bilder verwenden, stellen Sie immer sicher, dass sie konsistent verwendet werden.</li> | |
| (f) | Über die Funktionen des Betriebssystems für die Textdarstellung werden Textinformationen bereitgestellt. Die Mindestinformationen, die bereitgestellt werden müssen, sind Textinhalt, Caret-Position zur Texteingabe und Textattribute. | 2.3 Wählen Sie die richtigen Steuerelemente: Vermeiden Sie die Verwendung von Bildern zum Vermitteln von Textinformationen. Verwenden Sie keine benutzerdefinierten Eingabekomponenten, die die Texteigenschaften möglicherweise nicht ordnungsgemäß für das Betriebssystem verfügbar machen, sondern immer die Standardsteuerelemente. | |
| (g) | Anwendungen dürfen die von den Benutzenden gewählten Kontrast- und Farboptionen sowie andere individuelle Anzeigeattribute nicht außer Kraft setzen. | Keine LiveCycle Designer-spezifischen Techniken | Verwenden Sie nach Möglichkeit die grundlegenden Standardfarben des Systems. |
| (h) | Wenn Animationen angezeigt werden, müssen die Benutzenden die Möglichkeit haben, die Informationen in mindestens einer nicht animierten Darstellungsform anzuzeigen. | 2.1 Halten Sie Formulare einfach und benutzerfreundlich. Vermeiden Sie Animationen in Ihren Formularen oder stellen Sie separate Versionen bereit, in denen Animationen durch statische Bilder ersetzt werden. | |
| (i) | Eine Farbcodierung darf nicht als einziges Mittel zur Übermittlung von Informationen, zur Anzeige einer Aktion, zur Aufforderung zu einer Reaktion oder zur Unterscheidung eines visuellen Elements verwendet werden. | 2.8 Verantwortungsvolle Verwendung von Farben | |
| (j) | Wenn ein Produkt es den Benutzenden ermöglicht, die Farb- und Kontrasteinstellungen anzupassen, sollte eine Vielzahl von Farbauswahlmöglichkeiten zur Verfügung stehen, die eine Reihe von Kontraststufen erzeugen können. | Nicht zutreffend | Diese Funktion wird im Allgemeinen von Adobe Reader und nicht von der Formularentwicklung bereitgestellt. |
| (k) | Bei der Software dürfen keine blinkenden oder aufblitzenden Texte, Objekte oder andere Elemente mit einer Blink-/Blitzfrequenz von mehr als 2 Hz und weniger als 55 Hz zum Einsatz kommen. | 2.1.1 Sich bewegende, blinkende oder aufblitzende Inhalte sind zu vermeiden | |
| (l) | Bei der Verwendung elektronischer Formulare muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise. | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |

### Abschnitt 508 § 11942: Web-basierte Intranet- und Internet-Informationen und -anwendungen

| § 11942 Richtlinie | Richtlinienbeschreibung | Erforderliche Best Practices für LiveCycle Designer zur Einhaltung der Richtlinien | Anmerkungen |
|-----------|-----------------------|-----------------------------------------------------------|-------|
| (a) | Für jedes nichttextliche Element ist ein Textäquivalent anzugeben (z. B. über „alt“, „longdesc“ oder im Elementinhalt). | 2.4 Angeben von Textäquivalenten für Bilder | |
| (b) | Entsprechende Alternativen für alle multimedialen Darstellungen müssen mit der Präsentation synchronisiert sein. | 2.12 Zugänglichmachen von allen Multimedia-Inhalten | |
| (c) | Web-Seiten müssen so gestaltet sein, dass alle durch Farben übermittelten Informationen auch ohne Farben verfügbar sind, z. B. über Kontext oder Markup. | 2.8 Verantwortungsvolle Verwendung von Farben | |
| (d) | Dokumente müssen so organisiert sein, dass sie ohne zugehörige Formatvorlage lesbar sind. | Nicht zutreffend | |
| (e) | Für jede aktive Region einer Server-seitigen Imagemap sind redundante Text-Links bereitzustellen. | Nicht zutreffend | |
| (f) | Anstelle von Server-seitigen Imagemaps sind Client-seitige Imagemaps bereitzustellen, es sei denn, die Regionen können nicht mit einer verfügbaren geometrischen Form definiert werden. | Nicht zutreffend | |
| (g) | Für Datentabellen müssen Zeilen- und Spaltenüberschriften angegeben werden. | 2.9 Bereitstellen von Überschriftzellen für Tabellen | |
| (h) | Es wird Markup verwendet, um Datenzellen und Überschriftenzellen für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften zuzuordnen. | 2.9 Bereitstellen von Überschriftzellen für Tabellen | |
| (i) | Frames werden mit Text beschriftet, der die Identifizierung und Navigation von Frames erleichtert. | Nicht zutreffend | |
| (j) | Seiten dürfen nicht so ausgelegt sein, dass der Bildschirm mit einer Frequenz von mehr als 2 Hz oder weniger als 55 Hz flackern kann. | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| (k) | Es ist eine reine Textseite mit entsprechenden Informationen oder Funktionen bereitzustellen, damit eine Website den Bestimmungen dieses Teils entspricht, wenn die Einhaltung nicht auf andere Weise erreicht werden kann. Der Inhalt der reinen Textseite wird aktualisiert, sobald sich die primäre Seite ändert. | Nicht zutreffend | |
| (l) | Wenn Seiten Skriptsprachen verwenden, um Inhalte anzuzeigen oder Schnittstellenelemente zu erstellen, werden die vom Skript bereitgestellten Informationen durch funktionalen Text identifiziert, der von Hilfstechnologien gelesen werden kann. | 2.11 Vermeiden von störenden Skripten | |
| (m) | Wenn eine Webseite erfordert, dass ein Applet, Plug-in oder eine andere Anwendung auf dem Client vorhanden ist, um den Seiteninhalt zu interpretieren, muss die Seite einen Link zu einem Plug-in oder Applet enthalten, das den Anforderungen von §1194.21(a) bis (l) entspricht. | Nicht zutreffend | Webseiten, die auf PDF-Formulare verlinken, sollten einen Link zu Adobe Reader enthalten. |
| (n) | Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugang zu den Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise. | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |
| (o) | Es muss eine Methode bereitgestellt werden, die es den Benutzenden ermöglicht, sich wiederholende Navigations-Links zu überspringen. | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| (p) | Wenn eine zeitgesteuerte Antwort erforderlich ist, sollten die Benutzenden gewarnt werden und ausreichend Zeit erhalten, um ggf. anzugeben, dass mehr Zeit benötigt wird. | 2.11 Vermeiden von störenden Skripten | |

### WCAG 1.0 – Prüfpunkte der Priorität 1

| Prüfpunkt | Beschreibung des Prüfpunkts | Erforderliche Best Practices für LiveCycle Designer zur Einhaltung der Richtlinien | Anmerkungen |
|------------|------------------------|-----------------------------------------------------------|-------|
| [1.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-text-equivalent) | Geben Sie für jedes nichttextliche Element ein Textäquivalent an (z. B. über „alt“, „longdesc“ oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIFs), Applets und programmatische Objekte, ASCII-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Töne (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audiospuren von Videos und Video. | <ul><li>2.4 Angeben von Textäquivalenten für Bilder</li> <li>2.12 Zugänglichmachen von allen Multimedia-Inhalten</li> | |
|  [1.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-redundant-server-links) | Stellen Sie redundante Text-Links für jede aktive Region einer Server-seitigen Imagemaps bereit. | Nicht zutreffend | |
| [1.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-auditory-descriptions) | Bis Benutzeragenten automatisch das Textäquivalent einer visuellen Spur vorlesen können, stellen Sie eine auditive Beschreibung der wichtigen Informationen der visuellen Spur einer Multimedia-Präsentation bereit. | 2.12 Zugänglichmachen von allen Multimedia-Inhalten | |
| [1.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-synchronize-equivalents) | Bei zeitbasierten Multimedia-Präsentationen (z. B. einem Film oder einer Animation) sollten entsprechende Alternativen (etwa Untertitel oder akustische Beschreibungen der visuellen Spur) mit der Präsentation synchronisiert werden. | 2.12 Zugänglichmachen von allen Multimedia-Inhalten | |
| [2.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-color-convey) | Stellen Sie sicher, dass alle Informationen, die durch Farben vermittelt werden, auch ohne Farben verfügbar sind, z. B. über Kontext oder Markup. | 2.8 Verantwortungsvolle Verwendung von Farben | |
| [4.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-identify-changes) | Deutliche Kennzeichnung von Änderungen in der natürlichen Sprache des Textes eines Dokuments und in allen Textäquivalenten (z. B. Bildunterschriften). | 2.13 Kennzeichnen von sprachlichen Änderungen | |
| [5.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-table-headers) | Bei Datentabellen sind die Zeilen- und Spaltenüberschriften zu kennzeichnen. | 2.9 Bereitstellen von Überschriftzellen für Tabellen | |
| [5.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-table-structure) | Bei Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften verwenden Sie Markup, um Datenzellen und Überschriftszellen zu verknüpfen. | 2.9 Bereitstellen von Überschriftzellen für Tabellen | |
| [6.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-order-style-sheets) | Organisieren Sie Dokumente so, dass sie ohne Formatvorlagen gelesen werden können. Wenn beispielsweise ein HTML-Dokument ohne zugehörige Formatvorlagen dargestellt wird, muss es dennoch möglich sein, das Dokument zu lesen. | Nicht zutreffend | |
| [6.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-dynamic-source) | Stellen Sie sicher, dass Äquivalente für dynamische Inhalte aktualisiert werden, wenn sich der dynamische Inhalt ändert. | 2.11 Vermeiden von störenden Skripten | |
| [6.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-scripts) | Stellen Sie sicher, dass die Seiten auch dann nutzbar sind, wenn Skripte, Applets oder andere programmatische Objekte deaktiviert sind oder nicht unterstützt werden. Ist dies nicht möglich, stellen Sie gleichwertige Informationen auf einer alternativ zugänglichen Seite bereit. | 2.11 Vermeiden von störenden Skripten | |
| [7.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-flicker) | Solange Benutzeragenten es den Benutzenden nicht ermöglichen, das Flackern zu kontrollieren, sollte das Flackern des Bildschirms vermieden werden. | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| [9.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-client-side-maps) | Verwenden Sie Client-seitige Imagemaps anstelle von Server-seitigen Imagemaps, es sei denn, die Regionen können nicht mit einer verfügbaren geometrischen Form definiert werden. | Nicht zutreffend | |
| [11.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-alt-pages) | Wenn Sie trotz größter Bemühungen keine barrierefreie Seite erstellen können, stellen Sie einen Link zu einer alternativen Seite bereit, die W3C-Technologien verwendet, barrierefrei ist, über gleichwertige Informationen (oder Funktionen) verfügt und genauso oft aktualisiert wird wie die nicht barrierefreie (ursprüngliche) Seite. | Nicht zutreffend | |
| [12.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-frame-titles) | Geben Sie jedem Frame einen Titel, um die Identifizierung und Navigation von Frames zu erleichtern. | Nicht zutreffend | |
| [14.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-simple-and-straightforward) | Verwenden Sie eine klare und einfache Sprache, die zum Inhalt der Website passt. | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |

### WCAG 1.0 – Prüfpunkte der Priorität 2

| Prüfpunkte der Priorität 2 | Beschreibung des Prüfpunkts | Erforderliche Best Practices für LiveCycle zur Einhaltung der Richtlinien | Anmerkungen |
|------------|------------------------|-------------------------------------------------|-------|
| [2.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-color-contrast) | Stellen Sie sicher, dass die Kombinationen aus Vordergrund- und Hintergrundfarben einen ausreichenden Kontrast bieten, wenn sie von einer Person mit Farbenblindheit oder auf einem Schwarzweißbildschirm angezeigt werden. [Priorität 2 für Bilder, Priorität 3 für Text]. | 2.8 Verantwortungsvolle Verwendung von Farben | |
| [3.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-use-markup) | Wenn eine geeignete Markup-Sprache vorhanden ist, verwenden Sie Markup anstelle von Bildern, um Informationen zu vermitteln. | <ul><li>2.1 Formulare sind einfach und benutzerfreundlich zu halten</li><li> 2.1.1 Sich bewegende, blinkende oder aufblitzende Inhalte sind zu vermeiden</li> <li>2.2 Konfigurieren Sie Formulareigenschaften so, dass sie Barrierefreiheitsinformationen generieren. Verwenden Sie immer tatsächlichen Text anstelle von Textbildern.</li> | |
| [3.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-identify-grammar) | Erstellen Sie Dokumente, die veröffentlichten formalen Grammatiken entsprechen. | | PDF-Formulare müssen der veröffentlichten PDF-Spezifikation entsprechen, um in Adobe Reader dargestellt werden zu können. |
| [3.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-style-sheets) | Verwenden Sie Formatvorlagen, um das Layout und die Darstellung zu steuern. | Nicht zutreffend | |
| [3.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-relative-units) | Verwenden Sie relative anstelle absoluter Einheiten in den Markup-Sprachattributwerten und den Eigenschaftswerten von Formatvorlagen. | Nicht zutreffend | |
| [3.5](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-logical-headings) | Verwenden Sie Header-Elemente, um die Dokumentstruktur zu vermitteln, und verwenden Sie sie gemäß den Spezifikationen. | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| [3.6](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-list-structure) | Markieren Sie Listen und Listenelemente ordnungsgemäß. | 2.10.3 Listen als solche kennzeichnen: Kennzeichnen Sie listenbasierte Inhalte mithilfe der Rollen „Liste“ und „Listenelement“ als Listen. | |
| [3.7](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-quotes) | Markieren Sie Zitate. Verwenden Sie keine Anführungszeichen für Formatierungseffekte wie Einzug. | Nicht zutreffend | |
| [5.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-table-for-layout) | Verwenden Sie keine Tabellen für das Layout, es sei denn, die Tabelle ist sinnvoll, wenn sie linearisiert wird. Wenn die Tabelle andernfalls keinen Sinn ergibt, geben Sie ein alternatives Äquivalent an (bei dem es sich um eine linearisierte Version handeln kann). | Keine spezifischen LiveCycle-Techniken | Es gibt keinen Grund, Tabellen für das Layout in LiveCycle-Formularen zu verwenden. Verwenden Sie stattdessen die Palette „Layout“, um die Formularfelder in einem Rastermuster zu positionieren. Verwenden Sie eine Tabelle nur, wenn Sie tabellenspezifische Funktionen wie Tabellenkopfzeilen verwenden. |
| [5.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-table-layout) | Wenn eine Tabelle für das Layout verwendet wird, dürfen Sie für die visuelle Formatierung keine strukturellen Markierungen verwenden. | Keine spezifischen LiveCycle-Techniken | |
| [6.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-keyboard-operable-scripts) | Stellen Sie bei Skripten und Applets sicher, dass Ereignis-Handler unabhängig von den Eingabegeräten sind. | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| [6.5](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-fallback-page) | Stellen Sie sicher, dass dynamische Inhalte zugänglich sind, oder bieten Sie eine alternative Präsentation oder Seite an. | 2.11 Vermeiden von störenden Skripten | |
| [7.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-blinking) | Solange Benutzeragenten es den Benutzenden nicht ermöglichen, das Blinken zu kontrollieren, sollte das Blinken von Inhalten vermieden werden (d. h. die Darstellung in regelmäßigen Abständen zu ändern, etwa ein- und auszuschalten). | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| [7.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-movement) | Solange Benutzeragenten es den Benutzenden nicht ermöglichen, bewegte Inhalte einzufrieren, sollten Sie Bewegungen auf Seiten vermeiden. | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| [7.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-no-periodic-refresh) | Solange Benutzeragenten es den Benutzenden nicht ermöglichen, die Aktualisierung zu stoppen, sollten Sie keine Seiten erstellen, die sich regelmäßig automatisch aktualisieren. | Nicht zutreffend | |
| [7.5](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-no-auto-forward) | Solange Benutzeragenten es den Benutzenden nicht ermöglichen, die automatische Umleitung zu stoppen, verwenden Sie kein Markup, um Seiten automatisch umzuleiten. Konfigurieren Sie stattdessen den Server so, dass er Umleitungen vornimmt. | Nicht zutreffend | |
| [8.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-directly-accessible) | Machen Sie programmatische Elemente wie Skripte und Applets direkt zugänglich oder mit unterstützenden Technologien kompatibel[. Priorität 1, wenn die Funktionalität wichtig ist und nicht an anderer Stelle angeboten wird, andernfalls Priorität 2.] | 2.11 Vermeiden von störenden Skripten | |
| [9.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-keyboard-operable) | Stellen Sie sicher, dass jedes Element, das über eine eigene Schnittstelle verfügt, geräteunabhängig betrieben werden kann. | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| [9.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-device-independent-events) | Geben Sie für Skripte logische Ereignis-Handler anstelle geräteabhängiger Ereignis-Handler an. | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| [10.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-pop-ups) | Solange Benutzeragenten es Benutzenden ermöglichen, erzeugte Fenster zu deaktivieren, sollten Sie keine Pop-ups oder andere Fenster erscheinen lassen und das aktuelle Fenster nicht ändern, ohne die Benutzenden darüber zu informieren. | 2.11 Vermeiden von störenden Skripten | |
| [10.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-unassociated-labels) | Solange Benutzeragenten keine expliziten Zuordnungen zwischen Beschriftungen und Formularsteuerelementen unterstützen, stellen Sie bei allen Formularsteuerelementen mit implizit zugeordneten Beschriftungen sicher, dass die Beschriftung richtig positioniert ist. | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |
| [11.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-latest-w3c-specs) | Verwenden Sie W3C-Technologien, wenn sie verfügbar und für eine Aufgabe geeignet sind, und verwenden Sie die neuesten Versionen, wenn sie unterstützt werden. | Nicht zutreffend | |
| [11.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-avoid-deprecated) | Vermeiden Sie veraltete Funktionen von W3C-Technologien. | Nicht zutreffend | |
| [12.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-frame-longdesc) | Beschreiben Sie den Zweck der Frames und wie die Frames miteinander in Beziehung stehen, wenn dies nicht allein durch die Frame-Titel offensichtlich ist. | Nicht zutreffend | |
| [12.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-group-information) | Teilen Sie große Informationsblöcke in besser überschaubare Gruppen auf, wo dies natürlich und angemessen ist. | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| [12.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-associate-labels) | Verknüpfen Sie Beschriftungen explizit mit ihren Steuerelementen. | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |
| [13.1](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-meaningful-links) | Identifizieren Sie eindeutig das Ziel jedes Links. | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente 2.5.6 Bereitstellen von Link-Text | |
| [13.2](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-use-metadata) | Stellen Sie Metadaten bereit, um semantische Informationen zu Seiten und Sites hinzuzufügen. | Nicht zutreffend | |
| [13.3](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-site-description) | Stellen Sie Informationen über das allgemeine Layout einer Website bereit (z. B. eine Sitemap oder ein Inhaltsverzeichnis). | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| [13.4](https://www.w3.org/TR/WCAG10/wai-pageauth.html?lang=de#tech-clear-nav-mechanism) | Verwenden Sie die Navigationsmechanismen auf konsistente Art und Weise. | 2.10 Bereitstellen einer navigierbaren Formularstruktur | Verwenden Sie Musterseiten, um konsistente Navigationsinhalte zu erstellen. |

### WCAG 2.0-Erfolgskriterien

| Prüfpunkte der Priorität 1 G 2 | Erforderliche Best Practices für LiveCycle zur Einhaltung der Richtlinien | Anmerkungen |
| --- | --- | --- |
| 1.1 [Textalternativen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv.html?lang=de) | | |
| 1.1.1 [Nichttextlicher Inhalt](https://www.w3.org/TR/UNDERSTANDING-WCAG20/text-equiv-all.html?lang=de) | 2.4 Angeben von Textäquivalenten für Bilder | |
| | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |
| 1.2 [Zeitbasierte Medien](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv.html?lang=de) | | |
| 1.2.1 [Nur-Audio und Nur-Video (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-av-only-alt.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.2 [Untertitel (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-captions.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.3 [Audiobeschreibung oder Medienalternative (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.4 [Untertitel (Live)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-real-time-captions.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.5 [Audiobeschreibung (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-audio-desc-only.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.6 [Gebärdensprache (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-sign.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.7 [Erweiterte Audiobeschreibung (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-extended-ad.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.8 [Medienalternative (voraufgezeichnet)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-text-doc.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.2.9 [Nur-Audio (Live)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/media-equiv-live-audio-only.html?lang=de) | 2.12 Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann | |
| 1.3 [Anpassbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation.html?lang=de) | | |
| 1.3.1 [Informationen und Beziehungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html?lang=de) | 2.9 Bereitstellen von Überschriftzellen für Tabellen | |
| 1.3.2 [Bedeutungstragende Reihenfolge](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-sequence.html?lang=de) | 2.6 Sicherstellen, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| 1.3.3 [Sensorische Eigenschaften](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-understanding.html?lang=de) | 2.8 Verantwortungsvolle Verwendung von Farben | |
| 1.4 [Unterscheidbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast.html?lang=de) | | |
| 1.4.1 [Verwendung von Farben](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-without-color.html?lang=de) | 2.8 Verantwortungsvolle Verwendung von Farben | |
| 1.4.2 [Audio-Steuerelement](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-dis-audio.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.3 [Kontrast (Minimum)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html?lang=de) | 2.8 Verantwortungsvolle Verwendung von Farben | |
| 1.4.4 [Textgröße ändern](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.5 [Bilder von Text](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-presentation.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.6 [Kontrast (erweitert)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast7.html?lang=de) | 2.8 Verantwortungsvolle Verwendung von Farben | |
| 1.4.7 [Wenig oder kein Hintergrund-Audio](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-noaudio.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 1.4.9 [Bilder von Text (keine Ausnahme)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-text-images.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.1 [Per Tastatur zugänglich](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation.html?lang=de) | | |
| 2.1.1 [Tastatur](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-keyboard-operable.html?lang=de) | 2.6 Sicherstellen, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| 2.1.2 [Keine Tastaturfalle](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-trapping.html?lang=de) | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| 2.1.3 [Tastatur (keine Ausnahme)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-all-funcs.html?lang=de) | 2.6 Sicherstellen, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| | 2.7 Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können | |
| 2.2 [ Ausreichend Zeit](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits.html?lang=de) | | |
| 2.2.1 [Zeiteinteilung anpassbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.2 [Anhalten, Beenden, Ausblenden](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-pause.html?lang=de) | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| 2.2.3 [Keine Zeitplanung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-no-exceptions.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.4 [Unterbrechungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.2.5 [Erneute Authentifizierung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-server-timeout.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.3 [Anfälle] | | |
| 2.3.1 [Grenzwert von maximal dreimaligem Aufblitzen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-does-not-violate.html?lang=de) | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| 2.3.2 [Dreimaliges Aufblitzen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/seizure-three-times.html?lang=de) | 2.1 Formulare sind einfach und benutzerfreundlich zu halten | |
| 2.4 [Navigierbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms.html?lang=de) | | |
| 2.4.1 [Umgehen von Blöcken](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html?lang=de) | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| 2.4.2 [Seite mit Titel](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-title.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 2.4.3 [Fokus-Reihenfolge](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-order.html?lang=de) | 2.6 Sicherstellen, dass die Leserichtung und die Tab-Reihenfolge korrekt sind | |
| 2.4.4 [Link-Zweck (im Kontext)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-refs.html?lang=de) | Keine spezifischen LiveCycle-Techniken | Der Link-Zweck ist davon abhängig, dass Autorinnen und Autoren sinnvollen Text für verknüpfte Elemente auswählen. |
| 2.4.5 [Verschiedene Methoden](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-mult-loc.html?lang=de) | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| 2.4.6 [Überschriften und Beschriftungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-descriptive.html?lang=de) | <ul><li>2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente</li><li>2.10 Bereitstellen einer navigierbaren Formularstruktur</li> | |
| 2.4.7 [Fokus sichtbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-focus-visible.html?lang=de) | Keine spezifischen LiveCycle-Techniken | Der Standardfokus in LiveCycle-Formularen wird angezeigt. |
| 2.4.8 [Position](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-location.html?lang=de) | Keine spezifischen LiveCycle-Techniken | Nicht anwendbar: Für LiveCycle-Formulare sind keine Navigationssysteme erforderlich. |
| 2.4.9 [Link-Zweck (nur Link)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-link.html?lang=de) | Keine spezifischen LiveCycle-Techniken | Der Link-Zweck ist davon abhängig, dass Autorinnen und Autoren sinnvollen Text für verknüpfte Elemente auswählen. |
| 2.4.10 [Abschnittsüberschriften](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-headings.html?lang=de) | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| 3.1 [Lesbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning.html?lang=de) | | |
| 3.1.1 [Sprache der Seite](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html?lang=de) | 2.13 Kennzeichnen natürlicher Sprache und aller Sprachänderungen | |
| 3.1.2 [Sprache von Teilen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-other-lang-id.html?lang=de) | 2.13 Kennzeichnen natürlicher Sprache und aller Sprachänderungen | |
| 3.1.3 [Ungewöhnliche Wörter](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-idioms.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.4 [Abkürzungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-located.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.5 [Lesestufe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-supplements.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.1.6 [Aussprache](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-pronunciation.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.2 [Vorhersehbar](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior.html?lang=de) | | |
| 3.2.1 [Im Fokus](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-receive-focus.html?lang=de) | 2.11 Vermeiden von störenden Skripten | |
| 3.2.2 [Bei Eingabe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-unpredictable-change.html?lang=de) | 2.11 Vermeiden von störenden Skripten | |
| 3.2.3 [Konsistente Navigation](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-locations.html?lang=de) | 2.10 Bereitstellen einer navigierbaren Formularstruktur | |
| 3.2.4 [Konsistente Erkennung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-functionality.html?lang=de) | <ul><li>2.3 Auswählen der richtigen Steuerelemente</li><li>2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente</li> | |
| 3.2.5 [Änderung auf Anforderung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html?lang=de) | 2.11 Vermeiden von störenden Skripten | |
| 3.3 [Hilfestellung bei der Eingabe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error.html?lang=de) | | |
| 3.3.1 [Fehlererkennung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-identified.html?lang=de) |  | LiveCycle Designer bietet Tools zum Markieren von Formularfeldern nach Bedarf und zum Durchführen einer Überprüfung der Formulareingabe. |
| 3.3.2 [Beschriftungen oder Anweisungen](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html?lang=de) | 2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente | |
| 3.3.3 [Fehlerempfehlung](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-suggestions.html?lang=de) |  | LiveCycle Designer bietet Tools zum Markieren von Formularfeldern nach Bedarf und zum Durchführen einer Überprüfung der Formulareingabe. |
| 3.3.4 [Fehlervermeidung (rechtlich, finanziell, Daten)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.3.5 [Hilfe](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-context-help.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 3.3.6 [Fehlervermeidung (alle)](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-reversible-all.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 4.1 [Kompatibel](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat.html?lang=de) | | |
| 4.1.1 [Parsing](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-parses.html?lang=de) | Keine spezifischen LiveCycle-Techniken | |
| 4.1.2 [Name, Rolle, Wert](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html?lang=de) | <ul><li>2.3 Auswählen der richtigen Steuerelemente</li> <li>2.5 Angeben angemessener Beschriftungen für Formularsteuerelemente</li> | |
