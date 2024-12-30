---
title: Best Practices zum Erstellen von Formularen in Forms Designer
description: Informieren Sie sich über die Best Practices für Barrierefreiheit beim Erstellen von Formularen in Forms Designer
feature: Adaptive Forms, Forms Designer
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 3a9d7943-2c34-4e0a-9803-7ce1ef40f676
source-git-commit: 0d491be4fb2605220b1558c8c877151ab4405978
workflow-type: tm+mt
source-wordcount: '11687'
ht-degree: 100%

---

# Best Practices zum Erstellen von Formularen in Forms Designer

Mit LiveCycle Designer können Sie unter Einhaltung der Richtlinien aus Abschnitt 508 Rich-Form-Inhalte erstellen. Dieses Handbuch enthält einen Überblick über die Best Practices für die Erstellung eines barrierefreien Formulars und Richtlinien für die Implementierung dieser Best Practices mit LiveCycle Designer. Die folgenden Best Practices werden behandelt:

1. [Einfache und benutzerfreundliche Gestaltung von Formularen](#keep-simple)
1. [Konfigurieren von Formulareigenschaften zum Generieren von Barrierefreiheits-Informationen](#configure-form-properties)
1. [Auswählen der richtigen Steuerelemente](#choose-right-controls)
1. [Angeben von Textäquivalenten für Bilder](#provide-text-equivalents)
1. [Angeben angemessener Beschriftungen für Formularsteuerelemente](#provide-proper-labels)
1. [Sicherstellen, dass Leserichtung und Registerkarten-Reihenfolge korrekt sind](#ensure-reading-tab-order)
1. [Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können](#ensure-keyboard-accessible)
1. [Verantwortungsvoller Umgang mit Farben](#use-color-responsibly)
1. [Bereitstellen von Überschriftzellen für Tabellen](#provide-heading-cells)
1. [Bereitstellen einer navigierbaren Formularstruktur](#provide-navigable-form)
1. [Vermeiden von störendem Scripting](#avoid-disruptive-scripting)
1. [Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann](#ensure-audio-video-accessible)
1. [Kennzeichnen natürlicher Sprache und aller Sprachänderungen](#identify-natural-language)

## Einfache und benutzerfreundliche Gestaltung von Formularen {#keep-simple}

Ein Formular gilt als nicht barrierefrei, wenn es nicht einfach zu verwenden ist. Sie sollten versuchen, simple und einfach nutzbare Formulare zu entwerfen. Ein einfaches Layout mit Steuerelementen und Feldern mit klaren, aussagekräftigen Beschriftungen und QuickInfos erleichtert allen Benutzenden die Verwendung des Formulars.
Übersichtlich und logisch aufgebaute Formulare, die klare und einfache Anweisungen enthalten, können von allen Benutzenden so leicht wie nur möglich ausgefüllt werden. Navigationsfunktionen wie die Registerkarten-Reihenfolge und Tastaturbefehle sollten der logischen Reihenfolge der Objekte im Formular zuträglich sein.

### Vermeiden von blinkenden, blitzenden oder sich bewegenden Inhalten

Bei manchen Menschen mit lichtempfindlicher Epilepsie kann ein Anfall auftreten, der durch Bewegungen mit einer Frequenz von mehr als 2 Hz (1 Hz bedeutet 1 Hertz pro Sekunde) und weniger als 55 Hz (55 pro Sekunde) ausgelöst wird.

Bewegungen mit weniger als 2 Hz gelten als langsam genug, um für Personen mit lichtempfindlicher Epilepsie sicher zu sein. Bewegungen mit mehr als 55 Hz werden als nicht wahrnehmbar angesehen.

Entwickelnde sollten sich dieser Parameter bewusst sein, wenn sie bei Web-Inhalten Bewegungen einsetzen.

Andere Benutzende haben möglicherweise kognitive Behinderungen, weswegen es durch animierte oder blinkende Inhalte in einem Formular schwerfällt, sich zu konzentrieren.

Versuchen Sie generell, optische Effekte, die von Skripten eingefügt werden (z. B. blinkender Text oder Animation), in interaktiven Formularen zu vermeiden. Solche Effekte verringern die Benutzerfreundlichkeit der Formulare für bestimmte Personen.

Verwandte Prüfpunkte
* Abschnitt 508 § 11934.21

   * (h) Bei der Darstellung einer Animation müssen die Informationen nach Wahl der Benutzenden in mindestens einer nicht animierten Darstellungsform angezeigt werden können.
   * (k) Bei der Software dürfen keine blinkenden oder aufblitzenden Texte, Objekte oder andere Elemente mit einer Blink-/Blitzfrequenz von mehr als 2 Hz und weniger als 55 Hz zum Einsatz kommen.
* Abschnitt 508 §11934.22
   * (j) Seiten dürfen nicht so ausgelegt sein, dass der Bildschirm mit einer Frequenz von mehr als 2 Hz oder weniger als 55 Hz flackern kann.
* WCAG 1.0
   * 7.1 Solange nicht Benutzeragenten den Benutzenden die Kontrolle über das Flackern ermöglichen, sollte ein Flackern des Bildschirms vermieden werden. (P1)
   * 7.2 Solange nicht Benutzeragenten den Benutzenden die Kontrolle über das Blinken ermöglichen, sollte das Blinken von Inhalten (d. h. regelmäßiges Ändern der Darstellung, etwa durch Ein- und Ausschalten) vermieden werden (P2).
   * 7.3 Solange nicht Benutzeragenten den Benutzenden das Einfrieren bewegter Inhalte ermöglichen, sollten Bewegungen auf den Seiten vermieden werden.
   * 14.1 Verwenden Sie die klarste und einfachste, für den Inhalt einer Website passende Sprache.
* WCAG 2.0
   * 2.2.2 Pausieren, Anhalten, Ausblenden: Für sich bewegende, blinkende, scrollende oder sich automatisch aktualisierende Informationen gelten folgenden Regeln (Stufe A):
   * 2.3.1 Schwellenwert von maximal dreimaligem Aufblitzen: Web-Seiten enthalten keine Elemente, die innerhalb einer Sekunde mehr als dreimal aufblitzen, bzw. die Blitzfrequenz liegt unter den allgemeinen Schwellenwerten für Blitze und rote Blitze. (Stufe A)
   * 2.3.2 Dreimaliges Aufblitzen: Webseiten enthalten nichts, das in einem Zeitraum von einer Sekunde mehr als dreimal blinkt. (Stufe AAA)


## Konfigurieren von Formulareigenschaften zum Generieren von Barrierefreiheits-Informationen {#configure-form-properties}

Damit ein Formular barrierefrei ist, muss es von Hilfstechnologien [wahrnehmbar](https://www.w3.org/TR/WCAG20/#perceivable) sein. Die meisten Bildschirmlesehilfen berücksichtigen beispielsweise nicht das visuelle Layout des Formulars, sondern die zugrunde liegende Struktur.

Um diese zugrunde liegende Struktur mithilfe von LiveCycle Designer zu implementieren, müssen Sie ein PDF-Formular mit Barrierefreiheitsinformationen (manchmal auch als „Tags“ bezeichnet) erstellen, damit die Sprachausgabe oder andere Hilfstechnologien den Formulartext und die Formularkomponenten lesen können. In einem Formular mit Barrierefreiheitsinformationen enthält jedes Element Informationen über seine eigene Struktur sowie Informationen darüber, wie es mit anderen Elementen verbunden oder von ihnen abhängig ist. Nur in PDF-Dateien mit enthaltenen Barrierefreiheitsinformationen können Bildschirmlesehilfen den Inhalt eines Dokuments genau identifizieren und beschreiben.

Um ein barrierefreies Formular zu erstellen, müssen Sie die Formulareigenschaften so konfigurieren, dass LiveCycle Designer beim Speichern des Formularentwurfs als PDF-Datei Barrierefreiheitsinformationen generiert:
1. Klicken Sie auf „Datei“ > „Formulareigenschaften“.
1. Klicken Sie auf die Registerkarte „Speicheroptionen“ und stellen Sie im Bereich PDF sicher, dass die Option „Barrierefreiheitsinformationen (Tags) für Acrobat generieren“ ausgewählt ist.
1. Klicken Sie auf „OK“.

In LiveCycle Designer ist diese Option standardmäßig aktiviert.

>[!NOTE]
> Diese Optionen gelten nur beim Speichern des Formularentwurfs als PDF-Datei. Sie gelten nicht für PDF-Dateien, die mit LiveCycle Forms erstellt wurden und über Konfigurationsoptionen verfügen, die in LiveCycle Designer von dieser Option unabhängig sind.

**Verwandte Prüfpunkte**

* Section 508 §1194.21
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.
* Section 508 §1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.


## Auswählen der richtigen Steuerelemente {#choose-right-controls}

Verwenden Sie beim Entwerfen Ihrer Formulare Entwicklungsobjekte aus den Registerkarten der Objektbibliothek von LiveCycle Designer. Sie können dieses Bedienfeld anzeigen, indem Sie „Fenster“ > „Objektbibliothek“ wählen oder Umschalt+F12 drücken (siehe Abbildung 1).

![Objektbibliothek-Bedienfeld](/help/forms/using/assets/image-1.png)

Abbildung 1: **Objektbibliothek-Bedienfeld**

Wenn Sie andere Objekte verwenden, werden diese möglicherweise von Hilfstechnologien ignoriert. Wenn Sie nur Standardobjekte verwenden, spart Ihnen dies den zusätzlichen Aufwand beim Definieren der Barrierefreiheitseigenschaften für Objekte, die Sie selbst erstellt haben. Wenn Sie eigene benutzerdefinierte Objekte erstellen und verwenden, stellen Sie sicher, dass Sie die Palette „Ein-/Ausgabehilfe“ verwenden, um Barrierefreiheitseigenschaften wie Rolle, QuickInfo, Bildschirmlesehilfen-Rangfolge und benutzerdefinierten Text für Bildschirmlesehilfen festlegen. Um die Palette „Ein-/Ausgabehilfe“ anzuzeigen, wählen Sie „Fenster“ > „Barrierefreiheit“.

**Verwandte Checkpoints**
* Section 508 §1194.21
   * c) Es ist eine klar definierte Bildschirmanzeige des aktuellen Fokus anzugeben, die sich zwischen den interaktiven Schnittstellenelementen bewegt, wenn sich der Eingabefokus ändert. Der Fokus muss programmatisch offen gelegt werden, damit Hilfstechnologien den Fokus und Fokusänderungen nachverfolgen können.
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.
* Section 508 §1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.

* WCAG 2.0
   * 3.2.4 Konsistente Erkennung: Komponenten mit der gleichen Funktionalität innerhalb eines Satzes von Web-Seiten werden konsistent erkannt. (Stufe AA)
   * 4.1.2 Name, Rolle, Wert: Für alle Komponenten der Benutzeroberfläche (einschließlich u. a. Formularelemente, durch Skripte generierte Links und Komponenten) können Name und Rolle programmgesteuert bestimmt werden. Zustände, Eigenschaften und Werte, die von den Benutzenden festgelegt werden können, können programmgesteuert festgelegt sein, und eine Benachrichtigung über Änderungen an diesen Elementen steht den Benutzeragenten zur Verfügung, einschließlich Hilfstechnologien. (Stufe A)


## Angeben von Textäquivalenten für Bilder {#provide-text-equivalents}

Bilder können für Benutzende mit bestimmten Behinderungen zu einem besseren Verständnis beitragen. Für Benutzende von Bildschirmlesehilfen verringern Bilder jedoch die Barrierefreiheit Ihres Formulars, wenn Sie keine Textalternative bereitstellen.

Wenn Sie Bilder verwenden möchten, geben Sie deswegen Textbeschreibungen für alle Bilder an. Stellen Sie sicher, dass der Text das Objekt und seinen Zweck im Formular beschreibt. Wenn Sie eine Textalternative definieren, liest die Bildschirmlesehilfe diese Alternative, wenn sie auf das Bild trifft. Daher muss für ein Bild, das Informationen enthält, immer eine Textalternative angegeben werden.

Sie können Textbeschreibungen mithilfe der Eigenschaften „QuickInfo“ oder „Benutzerdefinierter Text für Bildschirmlesehilfen“ in der Palette „Ein-/Ausgabehilfe“ oder über Textfelder, Beschriftungen und Objektnamen bereitstellen, wie in der Option „Name“ auf der Registerkarte „Bindung“ angegeben. Abbildung 2 zeigt etwa ein Beispiel für ein Bild, das den Text „Get Adobe Reader“ enthält. Da eine Bildschirmlesehilfe keinen Text lesen kann, der Teil eines Bildes ist, sollten Sie in der Palette „Ein-/Ausgabehilfe“ für dieses Objekt eine Textalternative in das Feld „Benutzerdefinierter Text für Bildschirmlesehilfen“ hinzufügen. In den meisten Fällen sollte der Alternativtext mit dem im Bild sichtbaren Text übereinstimmen (siehe Abbildung 2).

![Angeben von Alternativtext für ein Bild mithilfe der Palette „Ein-/Ausgabehilfe“](/help/forms/using/assets/image-2.png)

Abbildung 2: **Angeben von Alternativtext für ein Bild mithilfe der Palette „Ein-/Ausgabehilfe“**

Beachten Sie beim Festlegen des Alternativtexts Folgendes:
* Wenn das Bildobjekt oder gescannte Bild wichtige Informationen für das Formular enthält, erstellen Sie in der Palette „Ein-/Ausgabehilfe“ einen Text für das Bild, der das Objekt und seinen Zweck beschreibt. Der Text für ein Firmenlogo könnte beispielsweise aus den Worten „Firmenlogo“ und dem Namen des Unternehmens bestehen.
* Wenn das Bildobjekt semantische Farbinformationen enthält, fügen Sie dies ebenfalls in die Beschreibung ein. Eine Beschreibung einer grünen Ampel könnte beispielsweise „Übertragung erfolgreich“ lauten und die Beschreibung einer roten Ampel könnte „Übertragung fehlgeschlagen“ lauten.
* Wenn Sie komplexe Grafiken wie Balkendiagramme verwenden, geben Sie die Informationen in einer alternativen, zugänglichen Version an, z. B. in einer Tabelle oder in einer längeren Textbeschreibung.
* Erstellen Sie keine Textbeschreibungen für statische Bilder, die nur zur Dekoration verwendet werden.
* Verwenden Sie keine gescannten Daten als Hintergrundinformationen. Dies kann vorkommen, wenn eine Designerin oder ein Designer ein Druckformular scannt und Adobe LiveCycle Designer verwendet, um dem Formular neue Felder hinzuzufügen. Bildschirmlesehilfen können die gescannten Daten in diesem Zustand nicht erkennen.

Wenn Sie rein dekorative grafische Inhalte in Ihre Formulare aufnehmen, sollten Sie sicherstellen, dass Bildschirmlesehilfen die Präsenz des Bildes nicht ankündigen. Für die meisten Bildschirmlesehilfen kann dies erreicht werden, indem Sie in der Palette „Ein-/Ausgabehilfe“ die Eigenschaft „Bildschirmlesehilfen-Text“ auf „Keiner“ setzen. Wenn Sie dies nicht tun, könnten einige Bildschirmlesehilfen das Vorhandensein einer Grafik ankündigen, ohne anzugeben, was die Grafik darstellt. Stellen Sie bei dynamischen Bildern wie Bildfeldobjekten sicher, dass die Textalternativen beim Ändern des Bildes ordnungsgemäß aktualisiert werden. Erstellen Sie keine Textbeschreibungen für Bildfeldobjekte, die nur zur Dekoration verwendet werden. Sie können die FormCalc-Skriptsprache verwenden, um einem Bildfeldobjekt dynamisch Textbeschreibungen zuzuweisen. FormCalc ist die Standard-Skriptsprache von Adobe LiveCycle Designer. Betrachten Sie beispielsweise ein Formular mit einem Bildfeld namens „ImageField1“ und verknüpftem Text im Bildknoten der Laufzeitdaten. Sie können Skripte verwenden, um diesen Text wie folgt in einem entsprechenden Ereignis (z. B. `form:ready`) weiterzugeben:

`ImageField1.assist.toolTip = $record.imagetext.value`

Verwandte Prüfpunkte
* Section 508 §1194.22
   * a) Für jedes nichttextliche Element ist ein Textäquivalent anzugeben (z. B. über „alt“, „longdesc“ oder im Elementinhalt).
* WCAG 1.0
   * 1.1 Geben Sie für jedes nichttextliche Element ein Textäquivalent an (z. B. über „alt“, „longdesc“ oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIFs), Applets und programmatische Objekte, ASCII-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Töne (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audiospuren von Videos und Video (P1).
* WCAG 2.0
   * 1.1.1 Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzenden präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen. (Stufe A)


## Angeben angemessener Beschriftungen für Formularsteuerelemente{#provide-proper-labels}

Die Beschriftung oder der Untertitel eines Formularsteuerelements gibt an, was das Formularsteuerelement darstellen soll. Der Text „Vorname“ weist Benutzende zum Beispiel darauf hin, dass sie ihren Vornamen in ein Textfeld eingeben müssen. Damit Bildschirmlesehilfen darauf zugreifen können, muss die Beschriftung programmgesteuert mit dem Formularsteuerelement verknüpft sein oder das Formularsteuerelement muss mit zusätzlichen Barrierefreiheitsinformationen über die Palette „Ein-/Ausgabehilfe“ konfiguriert werden. Es reicht nicht aus, einfach ein Textobjekt neben dem Steuerelement zu platzieren. Sowohl für sehende als auch für sehbehinderte Benutzende ist es wichtig, dass die Beschriftung korrekt neben dem Steuerelement platziert wird. Beide Techniken werden in den folgenden Abschnitten besprochen.

### Festlegen des Textes für die barrierefreie Beschriftung über die Palette „Ein-/Ausgabehilfe“

Die Beschriftung, die von Bildschirmlesehilfen wahrgenommen wird, muss nicht unbedingt mit der visuellen Beschriftung übereinstimmen. In einigen Fällen möchten Sie den Zweck des Steuerelements möglicherweise genauer angeben.
Für jedes Feldobjekt in einem Formular können die Barrierefreiheitsoptionen (s. Bild 3) verwendet werden, um anzugeben, wie das Bildschirmlesegerät das entsprechende Formularfeld identifizieren soll.

Gehen Sie wie folgt vor, um die Palette „Ein-/Ausgabehilfe“ zu verwenden:

1. Zeigen Sie die Palette „Ein-/Ausgabehilfe“ an, indem Sie „Fenster“ > „Ein-/Ausgabehilfe“ wählen oder Umschalt+F6 drücken.
1. Wählen Sie ein Objekt im Formular aus. In der Palette werden die Barrierefreiheitseigenschaften des Objekts angezeigt.

![Die Palette „Ein-/Ausgabehilfe“](/help/forms/using/assets/image-3.png)

Abbildung 3: **Die Palette „Ein-/Ausgabehilfe“**

Wenn das Formular als PDF gespeichert wird, durchsucht LiveCycle Designer das Formular nach den Eigenschaften „Benutzerdefinierter Text“, „QuickInfo“, „Beschriftung“ und „Name“, und zwar in dieser Reihenfolge, um nach Text zu suchen, der von Bildschirmlesehilfen gelesen werden kann. Diese Standardreihenfolge können Sie über die Option „Bildschirmlesehilfen-Rangfolge“ in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.

1. Wählen Sie das Objekt im Formularentwurf aus.
1. Klicken Sie auf die Palette „Ein-/Ausgabehilfe“.
1. Wählen Sie eine andere Option als „Keine“ für Bildschirmlesehilfen-Rangfolge“ aus.

Die folgenden Optionen sind verfügbar:

* **Benutzerdefinierter Text**, den Sie im Feld „Benutzerdefinierter Bildschirmlesehilfen-Text“ der  Palette „Ein-/Ausgabehilfe“ festlegen. Mit dieser Option können Sie jeden Text angeben, der von Hilfstechnologien wie Bildschirmlesehilfen verwendet werden soll. Die Verwendung der Einstellung „Beschriftung“ ist in den meisten Fällen am besten. Das Erstellen von benutzerdefiniertem Bildschirmtext sollte nur dann als Option in Betracht gezogen werden, wenn die Verwendung der Beschriftung oder einer QuickInfo nicht möglich ist.
* **QuickInfo**, die Sie im Feld „QuickInfo“ der Palette „Ein-/Ausgabehilfe“ festlegen. Bei den meisten Objekten werden QuickInfos zur Laufzeit angezeigt, wenn Benutzende den Mauszeiger über das Objekt bewegen. QuickInfos werden für einige schreibgeschützte Objekte wie etwa das Barcode-Objekt eines Papierformulars nur angezeigt, wenn eine Bildschirmlesehilfe verwendet wird.
* **Beschriftung**, wodurch LiveCycle Designer die zugehörige (visuelle) Beschriftung des Formularfelds als Text für Bildschirmlesehilfen verwendet.
* **Name**, den Sie im Feld „Name“ der Registerkarte „Bindung“ festlegen. Beachten Sie, dass dieser Name keine Leerzeichen enthalten darf.
* **Kein**, wodurch das Objekt keinen Namen hat. Dies wird für Formularsteuerelemente niemals empfohlen.

Beachten Sie Folgendes beim Verwenden der Palette „Ein-/Ausgabehilfe“ für die Beschriftung von Formularsteuerelementen:

* Wenn die Beschriftung des Formularsteuerelements das Steuerelement ordnungsgemäß beschreibt, ist sie für Bildschirmlesehilfen verfügbar. Lassen Sie in diesem Fall entweder die Felder „Benutzerdefinierter Text“ und „QuickInfo“ in der Palette „Ein-/Ausgabehilfe“ leer oder ändern Sie die Priorität in der Rangfolge der Bildschirmlesehilfe in „Beschriftung“.
* Bei der Ausrichtung auf Bildschirmlesehilfen ergibt es keinen Sinn, für dasselbe Formularsteuerelement verschiedene Textbeschreibungen anzugeben, da nur eine verwendet wird, nämlich die im ersten nicht-leeren Feld in der Bildschirmlesehilfen-Rangfolge. Beispielsweise gibt es keinen Grund, sowohl benutzerdefinierten Text als auch QuickInfo-Text für eine Bildschirmlesehilfe anzugeben.
* Standardmäßig liest die Bildschirmlesehilfe die Beschriftung, wenn im Feld „QuickInfo“ oder im Feld „Benutzerdefinierter Bildschirmlesehilfen-Text“ nichts angegeben ist.
* Verwenden Sie die Palette „Ein-/Ausgabehilfe“ nicht, um Beschreibungen für unsichtbare Felder oder Bereiche zu erstellen.
* Wenn Sie eine Beschreibung mithilfe der Optionen „QuickInfo“ oder „Benutzerdefinierter Bildschirmlesehilfe-Text“ erstellen müssen, fügen Sie immer die Beschriftung ein, die im Formular sichtbar ist, es sei denn, die sichtbare Beschriftung ist nicht aussagekräftig, z. B. wenn die Beschriftung selbst abgekürzt ist. Dies hilft Benutzenden der Bildschirmlesehilfe, effektiv mit anderen Benutzenden über Benutzeroberflächenelemente zu kommunizieren. Diese unterschiedlichen Benutzergruppen hätten Schwierigkeiten, dasselbe Element der Benutzeroberfläche zu identifizieren, wenn sich der Beschriftungstext von der QuickInfo oder dem benutzerdefiniferten Bildschirmlesehilfen-Text unterscheidet.
* Bei Steuerelementen wie Kontrollkästchen und Dropdown-Listen in Tabellenzellen gibt die Bildschirmlesehilfe an, was immer Sie als Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text für das Objekt angeben. Wenn Sie für diese Objekte bei Platzierung in einer Tabelle die Spaltenüberschrift als Alternativtext verwenden möchten, geben Sie weder Beschriftung noch QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text an.
* Wenn das Steuerelement zusätzliche Anweisungen erfordert, stellen Sie sicher, dass diese ebenfalls in der Textalternative enthalten sind. Geben Sie genügend gesprochene Informationen an, damit die Benutzenden wissen, welche Eingabe erwartet wird und wie das Feld korrekt ausgefüllt werden soll. Vermeiden Sie es jedoch, sie mit redundanten Informationen zu überhäufen.
* Geben Sie keine unnötigen Informationen an, die beschreiben, wie Steuerelemente verwendet werden. Überlassen Sie diese Aufgabe den Hilfstechnologien der Benutzenden. Benutzende können die Ausführlichkeit entsprechend ihrer Komfortstufe selbst konfigurieren.

Abbildung 4 zeigt ein Beispiel für ein Textfeld mit einer visuellen Beschriftung, die für einige Benutzende einer Bildschirmlesehilfe möglicherweise unklar ist. In diesem Beispiel ist „Benutzerdefinierter Bildschirmlesehilfen-Text“ auf „Anzahl der Seiten“ und „Bildschirmlesehilfen-Rangfolge“ auf „Benutzerdefinierter Text“ eingestellt. Daher wird der tatsächliche (visuelle) Beschriftungstext („Anzahl der Seiten“) nicht von der Bildschirmlesehilfe verwendet. Alternativ hätte eine QuickInfo angegeben werden können.

![Festlegen von benutzerdefiniertem Bildschirmlesehilfe-Text, wenn die sichtbare Beschriftung unzureichend ist](/help/forms/using/assets/image-4.png)

Abbildung 4: **Festlegen von benutzerdefiniertem Bildschirmlesehilfe-Text, wenn die sichtbare Beschriftung unzureichend ist**

### Beschriften von Optionsfeldern

Wenn sehbehinderte Benutzende mit der Tabulatortaste in ein Optionsfeld wechseln, muss die Bildschirmlesehilfe zwei Dinge vorlesen:
* Eine Angabe des Zwecks der Gruppe von Optionsfeldern
* Eine aussagekräftige Beschriftung für jedes Optionsfeld
So werden Optionsfelder mithilfe der Schaltflächenbeschriftungen barrierefrei gemacht:
   1. Wählen Sie in der Palette „Hierarchie“ die Ausschlussgruppe aus.
   1. Klicken Sie auf die Palette „Ein-/Ausgabehilfe“ und geben Sie im Feld „Benutzerdefinierter Bildschirmlesehilfen-Text“ den Text ein, der für diese Gruppe vorgelesen werden soll. Geben Sie beispielsweise für eine Ausschlussgruppe, die Optionen für die Zahlung mit verschiedenen Kreditkarten angibt, „Zahlungsmethode auswählen“ ein.
   1. Wenn die Beschriftungen für jedes Optionsfeld einen Text enthalten, der beim Aussprechen durch eine Bildschirmlesehilfe aussagekräftig ist, wählen Sie in der Palette „Objekt“ die Registerkarte „Bindung“ aus und deaktivieren Sie die Option „Elementwert angeben“.

  So werden Optionsfelder mithilfe eines angegebenen Elementwerts barrierefrei gemacht:
   1. Wählen Sie in der Palette „Hierarchie“ die Ausschlussgruppe aus.
   1. Klicken Sie auf die Palette „Ein-/Ausgabehilfe“ und geben Sie im Feld „Benutzerdefinierter Bildschirmlesehilfen-Text“ den Text ein, der für diese Gruppe vorgelesen werden soll. Geben Sie beispielsweise für eine Ausschlussgruppe, die Optionen für die Zahlung mit verschiedenen Kreditkarten angibt, „Zahlungsmethode auswählen“ ein.
   1. Wählen Sie in der Palette „Hierarchie“ das erste Optionsfeld in der Gruppe aus.
   1. Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Feld“. Doppelklicken Sie im Bereich „Element“ auf das Element und geben Sie einen aussagekräftigen Wert für das ausgewählte Optionsfeld ein. Beispielsweise könnten Sie für die erste Schaltfläche in einer Gruppe von Zahlungsmethoden „Bargeld“ eingeben.
   1. Wiederholen Sie die Schritte 3 und 4 für jedes Optionsfeld in der Ausschlussgruppe.

### Beschriften benutzerdefinierter Steuerelemente

Es wird dringend empfohlen, Standardkomponenten und keine benutzerdefinierten Komponenten zu verwenden, da erstere der Hilfstechnologie standardmäßig die richtigen Hinweise und Informationen liefern. Falls jedoch benutzerdefinierte Steuerelemente verwendet werden, beachten Sie Folgendes:
* Der Status von Kontrollkästchen und Optionsfeldern muss angekündigt werden.
* In Listenfeldern und Dropdown-Listen muss angekündigt werden, welches Element in der Liste standardmäßig ausgewählt ist. Stellen Sie sicher, dass die Benutzenden mithilfe der Pfeiltasten nach oben und unten durch die Listenelemente navigieren können und dies wissen. Merken Sie an, dass durch Drücken der Tabulatortaste oder der Eingabetaste das Element in der Liste ausgewählt wird. Mithilfe von Skripten können Sie das Änderungsereignis des Objekts so einstellen, dass angekündigt wird, welches Element in der Liste ausgewählt wurde.
* Lassen Sie alle speziellen Tastatureingaben ansagen, die die Benutzenden für eine Funktion benötigen, z. B. das Drücken der Leertaste, um eine Schaltfläche auszuwählen, oder der Nach-unten-Taste, um ein Element aus einem Listenfeld auszuwählen.

### Korrektes Positionieren der Beschriftung eines Steuerelements

Die Platzierung einer Beschriftung ist wichtig, da Benutzende davon ausgehen, sie neben einem Steuerelement zu finden. Für Benutzende mit Bildschirmvergrößerung ist dies umso wichtiger, da sie möglicherweise nicht in der Lage sind, sowohl das Steuerelement als auch die Beschriftung gleichzeitig anzuzeigen, wenn beide zu weit voneinander entfernt sind.

Wenn Sie ein Objekt erstellen, positioniert LiveCycle Designer die Beschriftung automatisch so wie durch den Objekttyp angegeben. Die Beschriftungen von Optionsfeldern werden beispielsweise rechts von ihnen platziert. Diese Standardplatzierung ist immer die beste Position für eine barrierefreie Beschriftung. Wenn Sie die Position des Beschriftungstextes jedoch ändern müssen, führen Sie die folgenden Schritte aus:
1. Wählen Sie das Objekt aus, indem Sie den Fokus darauf verschieben.
1. Wählen Sie in der Palette „Layout“ die Position der Beschriftung Ihres Objekts mithilfe der Option „Position“ im Abschnitt „Beschriftung“ am Ende der Palette aus.

Das Beispiel in Abbildung 5 zeigt ein Textfeld mit einer Beschriftung darüber. Die Position in der Palette „Layout“ ist auf „Oben“ eingestellt. Die Standardposition der Beschriftung ist links neben dem Textfeld.

![Ändern der Positionierung von Beschriftungen mithilfe der Palette „Layout“](/help/forms/using/assets/image-5.png)

Abbildung 5: **Ändern der Positionierung von Beschriftungen mithilfe der Palette „Layout“**

Die folgende Tabelle bietet einen Überblick über die Platzierungsregeln für häufig verwendete Steuerelemente.

| Typ des Steuerelements | Platzierungsregeln |
|--------------|-----------------|
| Texteingabe (einschließlich Felder für Datum, Uhrzeit und Kennwort) | Platzieren Sie die Beschriftung links neben dem Steuerelement (Standard). Ist dies nicht möglich, platzieren Sie sie direkt oberhalb oder unterhalb davon. Beschriftungen sollten für Benutzende mit stärkerer Vergrößerung in der Nähe des Kontrollelements positioniert werden, damit die Beschriftung und die Steuerung auch in der vergrößerten Ansicht mit höherer Wahrscheinlichkeit zusammen zu sehen sind. |
| Kontrollkästchen | Platzieren Sie die Beschriftung rechts neben dem Kontrollkästchen (Standard). Bei Kontrollkästchen-Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe an, was immer Sie als Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für ein Kontrollkästchen in einer Tabelle verwenden möchten, geben Sie weder Beschriftung noch QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text an. |
| Optionsfeldgruppe | Erstellen Sie einen sichtbaren Titel für die Optionsfeldgruppe, indem Sie ein statisches Textelement erstellen und links von der Gruppe oder über ihr platzieren. Platzieren Sie die Beschriftung für jedes einzelne Optionsfeld rechts daneben (Standard). |
| Dropdown-Liste | Platzieren Sie die Beschriftung links neben dem Objekt (Standard). Ist dies nicht möglich, platzieren Sie sie direkt darüber. Bei Dropdown-Listen-Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe bekannt, was immer Sie als Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für diese Objekte in einer Tabelle verwenden möchten, geben Sie weder Beschriftung noch QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text an. |
| Listenfeld | Die Beschriftung wird bei der Erstellung des Listenfelds standardmäßig über ihm positioniert. |
| Schaltfläche | Die Beschriftung wird automatisch auf die Schaltfläche gesetzt und muss nicht manuell positioniert werden. Stellen Sie sicher, dass der Zweck der Schaltfläche durch den Beschriftungstext richtig beschrieben wird. |


### Dynamisches Ausfüllen einer QuickInfo oder von benutzerdefiniertem Bildschirmlesehilfen-Text

Sie können auch die Textalternative eines Formularsteuerelements, z. B. die QuickInfo, dynamisch mit einem Wert aus einer Datenquelle ausfüllen. Sie können beispielsweise eine benutzerdefinierte QuickInfo für ein Objekt anzeigen, das in französischer Sprache ist.
Das Schema, zu dem Sie eine Verbindung herstellen, könnte die folgende Definition für eine QuickInfo enthalten:


```html
<form>
<tooltip dp_tt="tooltip1"/>
</form>
```


Die Datendatei, auf die Sie verweisen, könnte die folgende Definition für eine QuickInfo enthalten:

```html
<form>
<tooltip dp_tt="Quantité - Entrez un nombre inférieur ou égal à 100."/>
</form>
```

1. Klicken Sie in der Palette „Objektbibliothek“ auf die Kategorie „Standard“ und ziehen Sie ein Objekt auf den Formularentwurf. Fügen Sie beispielsweise ein Textfeld-Objekt ein.
1. (Optional) Klicken Sie in der Palette „Objekt“ auf die Registerkarte „Feld“ und geben Sie im Feld „Beschriftung“ eine Beschriftung für das Objekt ein. Geben Sie beispielsweise „Quantité“ ein.
1. Klicken Sie in der Palette „Ein-/Ausgabehilfe“ auf die aktive QuickInfo-Beschriftung.
1. Wählen Sie die Datenverbindung aus.
1. Klicken Sie auf das Dreieck neben dem Feld „Bindung“ und wählen Sie eine Bindung aus. Wählen Sie beispielsweise „QuickInfo > @dp_tt“ aus.

Die folgende Zeichenfolge wird im Feld „Bindung“ angezeigt: $record.tooltip.dp_tt Tipp: Sie können diese Zeichenfolge auch in das Feld „Elemente“ eingeben, anstatt sie auszuwählen.
1. Klicken Sie auf „OK“.
1. Zeigen Sie das Formular auf der Registerkarte „PDF-Vorschau“ an.

### Bereitstellen von Link-Text

Benutzende von Hilfstechnologien können unterschiedliche Methoden haben, um verknüpften Text zu lesen. Beispielsweise verwenden Benutzende von Bildschirmlesehilfen häufig eine Liste mit Links, wie in Abbildung 6 dargestellt, um die auf einer Seite verfügbaren Links schnell durchzugehen.

![Das Dialogfeld „JAWS-Links-Liste“](/help/forms/using/assets/image-6.png)

Abbildung 6: **Das Dialogfeld „JAWS-Links-Liste“**

Aus diesem Grund müssen Links selbstbeschreibend sein, d. h. ihre Bedeutung sollte nicht von ihrem Kontext (dem umgebenden Text) abhängen. Beispielsweise könnten die Wörter „Hier klicken“ eigentlich das Link-Element im Satz „Hier klicken, um unser Antragsformular herunterzuladen“ meinen. Ein solcher Link wäre beim Durchlesen einer Link-Liste schwierig zu verstehen, insbesondere wenn mehrere Links denselben Text enthalten.

Achten Sie bei der Verwendung von Links in Ihrem Formular darauf, dass jeder Link seinen Zweck ordnungsgemäß beschreibt, ohne dass dies vom umgebenden Text oder von der Position auf der Seite abhängt. Anstatt einen Satz wie „Hier klicken“ als Link-Text zu verwenden, verwenden Sie also beispielsweise „Anwendungsformular herunterladen“ als Link-Text.

**Verwandte Prüfpunkte**

* Section 508 §1194.21
   * d) Für Hilfstechnologien müssen ausreichende Informationen über ein Element der Benutzeroberfläche, einschließlich Identität, Betrieb und Zustand des Elements, verfügbar sein. Wenn ein Bild ein Programmelement darstellt, müssen die vom Bild vermittelten Informationen auch im Text verfügbar sein.
   * l) Bei der Verwendung elektronischer Formulare muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.
* Section 508 §1194.22
   * n) Wenn elektronische Formulare für das Online-Ausfüllen konzipiert sind, muss das Formular Personen, die Hilfstechnologien verwenden, den Zugriff auf alle Informationen, Feldelementen und Funktionen ermöglichen, die für das Ausfüllen und Übermitteln des Formulars erforderlich sind, einschließlich aller Anweisungen und Hinweise.
* WCAG 1.0
   * 12.4 Verknüpfen Sie Beschriftungen explizit mit ihren Steuerelementen (P2).
   * 13.1 Identifizieren Sie eindeutig das Ziel jedes Links (P2).
* WCAG 2.0
   * 1.1.1 Nichttextlicher Inhalt: Alle nichttextlichen Inhalte, die Benutzenden präsentiert werden, haben eine Textalternative, die dem jeweiligen Zweck entspricht, ausgenommen die unten aufgeführten Situationen. (Stufe A)
   * 2.4.6 Überschriften und Beschriftungen: Überschriften und Beschriftungen beschreiben ein Thema oder einen Zweck. (Stufe AA)
   * 3.2.4 Konsistente Erkennung: Komponenten mit der gleichen Funktionalität innerhalb eines Satzes von Web-Seiten werden konsistent erkannt. (Stufe AA)
   * 3.3.2 Beschriftungen oder Anweisungen: Beschriftungen oder Anweisungen werden bereitgestellt, wenn Inhalte eine Benutzereingabe erfordern. (Stufe A)
   * 4.1.2 Name, Rolle, Wert: Für alle Komponenten der Benutzeroberfläche (einschließlich u. a. Formularelemente, durch Skripte generierte Links und Komponenten) können Name und Rolle programmgesteuert bestimmt werden. Zustände, Eigenschaften und Werte, die von den Benutzenden festgelegt werden können, können programmgesteuert festgelegt sein, und eine Benachrichtigung über Änderungen an diesen Elementen steht den Benutzeragenten zur Verfügung, einschließlich Hilfstechnologien. (Stufe A)


## Sicherstellen, dass Leserichtung und Registerkarten-Reihenfolge korrekt sind {#ensure-reading-tab-order}

Das Sicherstellen einer sinnvollen Leserichtung ist bei der Erstellung von Formularen sehr wichtig, die für Benutzende mit Sehbehinderung oder anderen Behinderungen zugänglich sein sollen. Diese Benutzenden verwenden normalerweise keine Maus, um durch ein Formular zu navigieren, sodass sie von der Tastatur abhängig sind. Die Leserichtung bestimmt die Reihenfolge, in der die Benutzenden der Bildschirmlesehilfe das Formular durchlesen. Darüber hinaus ermöglicht die Tabulatorreihenfolge den Benutzende, schnell von einem interaktiven Formularsteuerelement zum nächsten zu wechseln, indem sie die Tabulatortaste oder Umschalt+Tabulatortaste drücken. Eine logische Tab-Reihenfolge stellt sicher, dass sie Zugriff auf alle Felder im Formular haben und dass sie im Formular auf eine sinnvolle und effiziente Weise navigieren können.

Die Leserichtung des Formulars umfasst alle statischen Objekte (wie Text und Bilder) und Feldobjekte, aber nur die interaktiven Formularsteuerelemente sind Teil der Tab-Reihenfolge.

>[!NOTE]
> In vielen Fällen hängt die Tab-Reihenfolge eng mit der Leserichtung zusammen. Der Einfachheit halber wird in diesem Handbuch der Begriff „Tab-Reihenfolge“ anstelle von „Tab- oder Lesereihenfolge“ verwendet.

### Die standardmäßige Tab-Reihenfolge in LiveCycle Designer-Formularen

Die standardmäßige Tab-Reihenfolge wird automatisch erstellt, wenn Sie Ihr Formular als getaggtes PDF speichern. Zunächst wird die Tab-Reihenfolge in einem Formular anhand der lokalen Position der Objekte mithilfe der folgenden Regeln bestimmt:

* Alle Objekte werden von links nach rechts und von oben nach unten (lokale Reihenfolge) angeordnet, beginnend mit der linken oberen Ecke des Formulars.
* Alle von Ihnen erstellten Teilformulare werden als eigenständige Einheiten behandelt, durch die ebenfalls von links nach rechts sowie von oben nach unten navigiert wird. Wenn sich zwei Teilformulare nebeneinander befinden, die beide Objekte enthalten, navigiert die Leserichtung erst durch alle Objekte im ersten Teilformular, bevor zum nächsten Teilformular gewechselt wird.

Bei einfachen Formularen (d. h. bei Formularen mit einem Layout von links nach rechts und von oben nach unten) ist die standardmäßige Tab-Reihenfolge in der Regel korrekt. Um dies zu überprüfen, sollten Sie die standardmäßige Tab-Reihenfolge vor der Veröffentlichung des Formulars überprüfen. Sie können die Tab-Reihenfolge mit einer der folgenden Methoden sichtbar machen:

* Wählen Sie „Ansicht“ > „Tab-Reihenfolge anzeigen“.
* Klicken Sie in der Palette „Tab-Reihenfolge“ auf „Reihenfolge anzeigen“.

Alle Objekte werden mit einer Zahl in der oberen rechten Ecke angezeigt, die die Position des Objekts in der standardmäßigen Registerkartenreihenfolge angibt. Die interaktiven Objekte in dieser Sequenz bilden die Tab-Reihenfolge. Abbildung 7 zeigt die Visualisierung der Leserichtung für ein einfaches Formular.

![Visualisierung der standardmäßigen Leserichtung für ein typisches Bestellformular](/help/forms/using/assets/image-7.png)

Abbildung 7: **Visualisierung der standardmäßigen Leserichtung für ein typisches Bestellformular**

Jede Nummer der Tab-Reihenfolge wird mit einer farbigen Form dargestellt. Die Formen haben die folgende Bedeutung:
* Graue Kreise (Nr. 1 und Nr. 4) werden für Objekte im Inhaltsbereich verwendet.
* Grüne Kreise (Nr. 6 und Nr. 7) werden für Musterseitenobjekte verwendet.
* Lila Quadrate (Nr. 2 und Nr. 3) werden für Objekte in einem Fragment verwendet.

Sie haben die Wahl, dass nur interaktive Formularsteuerelemente (die die Registerkartenreihenfolge bilden) oder alle Objekte in der Leserichtung angezeigt werden (einschließlich statischer Objekte wie Text und Bilder). Um diese Voreinstellung zu ändern, wählen Sie „Tools“ > „Optionen“ > „Tab-Reihenfolge“ und dann „Tab-Reihenfolge nur für Felder anzeigen“.

In einem komplexen Formular kann es schwierig sein zu erkennen, wie die Tab-Reihenfolge von einem Objekt zum nächsten verläuft. Sie können visuelle Hilfen verwenden, um den Tab-Fluss im Formular anzuzeigen. Wenn die visuellen Hilfen aktiviert sind und Sie den Mauszeiger über das Objekt bewegen, zeigen die blauen Pfeile den Tab-Fluss für die beiden vorangehenden und die beiden nachfolgenden Objekte in der Tab-Reihenfolge an (siehe Abbildung 8).

![Visuelle Hilfen zum Hervorheben der Tab-Reihenfolge](/help/forms/using/assets/image-8.png)

Abbildung 8: **Visuelle Hilfen heben die Tab-Reihenfolge hervor**

Verwenden Sie die folgenden Methoden, um die visuellen Hilfsmittel zu aktivieren:
* Wählen Sie „Tools“ > „Optionen“ > „Tab-Reihenfolge“ aus und dann im Bereich „Tab-Reihenfolge“ die Option „Visuelle Hilfen für Tab-Reihenfolge anzeigen“.
* Wählen Sie im Menü der Palette „Tab-Reihenfolge“ die Option „Visuelle Hilfen anzeigen“ aus.

### Verwenden der Position, um die standardmäßige Tab-Reihenfolge zu beeinflussen

Um die standardmäßige Tab-Reihenfolge zu beeinflussen, können Sie die Koordinaten eines Objekts ändern, indem Sie es an eine andere Position verschieben. Beispiel: In Abbildung 9 tritt das Feld „Produktname“ in der Tab-Reihenfolge vor dem Feld „Menge“ auf. Um diese Reihenfolge zu ändern, können Sie das Feld „Produktname“ so verschieben, dass es unter dem Feld „Menge“ oder rechts von ihm platziert wird.

![Die standardmäßige Tab-Reihenfolge ist von links nach rechts](/help/forms/using/assets/image-9.png)

Abbildung 9: **Die standardmäßige Tab-Reihenfolge ist von links nach rechts**

Sie können die Position eines Objekts auf eine der folgenden Weisen ändern:
* Es mit der Maus ziehen
* Es auswählen und mithilfe der Tastaturpfeile verschieben.

>[!NOTE]
> Es kann hilfreich sein, die Objektausrichtung beizubehalten, indem Sie „Ansicht“ > „Am Raster ausrichten“ auswählen.

Mithilfe der Palette „Layout“ können Sie die Koordinaten eines Objekts präziser ändern (siehe Abbildung 10). In dieser Palette können Sie die X- und Y-Koordinaten sowie die Breite und Höhe des Objekts angeben.

![Verwenden von Koordinaten zum präzisen Positionieren eines Objekts mit der Palette „Layout“](/help/forms/using/assets/image-10.png)

Abbildung 10: **Verwenden von Koordinaten zum präzisen Positionieren eines Objekts mit der Palette „Layout“**

>[!NOTE]
> Wenn die Beschriftung und das Steuerelement nicht zusammengeführt werden, ist die Position der Beschriftung eines Formularsteuerelements unabhängig von der Reihenfolge, in der Bildschirmlesehilfen das Objekt und seine Elemente lesen. Weitere Informationen zu Beschriftungen finden Sie in diesem Handbuch im Abschnitt 2.5 „Angeben angemessener Beschriftungen für Formularsteuerelemente“.

### Verwenden von Teilformularen, um die standardmäßige Tab-Reihenfolge zu beeinflussen

Wie oben erwähnt, können Sie mit Teilformularen Gruppen von Objekten einfügen, die eine eigene Tab-Reihenfolge aufweisen. Sie können ein Teilformular auch erstellen, indem Sie einen der folgenden Schritte ausführen:
* Wählen Sie „Einfügen“ > „Standard“ > „Teilformular“ aus.
* Wählen Sie die Objekte in der Palette „Hierarchie“ aus und gruppieren Sie sie in einem Teilformular, indem Sie „Einfügen“ > „Umschließen mit Teilformular“ auswählen.
* Wählen Sie die Objekte im eigentlichen Formular aus, klicken Sie mit der rechten Maustaste auf die Auswahl und wählen Sie „Umschließen mit Teilformular“ aus.

Wenn zwei Teilformulare, die Feldobjekte enthalten, nebeneinander positioniert sind, durchläuft die Tab-Reihenfolge erst die Felder im ersten Teilformular, bevor sie zum nächsten wechselt. Dies wird in Abbildung 11 veranschaulicht, in der zwei Teilformulare verwendet werden, um standardmäßig eine spaltenbasierte Tab-Reihenfolge zu erstellen.

![Standardmäßige Tab-Reihenfolge bei Verwendung von Teilformularen](/help/forms/using/assets/image-11.png)

Abbildung 11: **Standardmäßige Tab-Reihenfolge bei Verwendung von Teilformularen**

Teilformulare, Optionsfelder und Inhaltsbereiche wirken sich alle zusammen mit der vertikalen Position der Objekte auf einer Seite und ihrer Musterseite auf die Tab-Reihenfolge aus.

### Erstellen einer benutzerdefinierten Tab-Reihenfolge mithilfe der Palette „Tab-Reihenfolge“

Sie können die standardmäßige Tab-Reihenfolge ändern, wenn Sie eine andere Reihenfolge im Formular benötigen und die Änderung nicht durch Positionieren oder Gruppieren in Teilformularen erreicht werden kann. Um die standardmäßige Tab-Reihenfolge zu ändern, können Sie über die Palette „Tab-Reihenfolge“ eine benutzerdefinierte Tab-Reihenfolge erstellen.
Über die Palette „Tab-Reihenfolge“ (siehe Abbildung 12) können Sie die Reihenfolge überprüfen und ändern, in der die Objekte in Ihrem Formular mithilfe von Hilfstechnologien gelesen werden und in der mit der Tabulatortaste navigiert wird.

![Palette „Tab-Reihenfolge“](/help/forms/using/assets/image-12.png)

Abbildung 12: **Palette „Tab-Reihenfolge“**

Die Palette „Tab-Reihenfolge“ bietet eine alternative Ansicht der Tab-Reihenfolge im Formular. Sie zeigt alle Objekte im Formular als nummerierte Liste an, wobei jede Zahl die Position des Objekts im Tab-Fluss darstellt.
Um die Palette „Tab-Reihenfolge“ zu öffnen, wählen Sie „Fenster“ > „Tab-Reihenfolge“ aus.


Die Palette „Tab-Reihenfolge“ enthält die folgenden visuellen Marken:
* Eine graue Leiste markiert jede Seite des Formulars. Die Tab-Reihenfolge auf jeder Seite beginnt mit der Zahl 1.
* Der Buchstabe M in einem grünen Kreis kennzeichnet Musterseitenobjekte (nur sichtbar, wenn das Formular auf der Registerkarte „Design-Ansicht“ angezeigt wird).
* Ein Zahlenbereich gibt Objekte in einem Fragment an.
* Ein gelber Hintergrund kennzeichnet das aktuell ausgewählte Element.
* Ein Schloss-Symbol neben dem ersten Objekt auf der Seite bedeutet, dass das Objekt innerhalb der Tab-Reihenfolge nicht verschoben werden kann (nur sichtbar, wenn das Formular auf der Registerkarte „Musterseiten“ angezeigt wird).

Die Liste zeigt dieselben Zahlen für die Tab-Reihenfolge an wie die Zahlen, die im Formular selbst angezeigt werden, wenn Sie „Ansicht“ > „Tab-Reihenfolge einblenden“ auswählen. Sie ändern die Position eines Objekts innerhalb der Tab-Reihenfolge, indem Sie das Objekt auf der Palette „Tab-Reihenfolge“ in der Liste nach oben oder unten verschieben. Sie können ein einzelnes Objekt oder eine Gruppe von Objekten verschieben. Dies kann mit einer der folgenden Methoden erreicht werden:

* Ziehen Sie das ausgewählte Objekt in der Liste nach oben oder unten und platzieren Sie es an der gewünschten Position. Ein schwarzer Griff kennzeichnet die aktuelle Position in der Liste, bevor Sie das Objekt platzieren.
* Klicken Sie in der Palette „Tab-Reihenfolge“ auf die Nach-oben- oder Nach-unten-Taste, bis sich das ausgewählte Objekt an der richtigen Position befindet. Drücken Sie alternativ Strg+Nach-oben-Taste oder Strg+Nach-unten-Taste.
* Wählen Sie im Menü der Palette „Tab-Reihenfolge“ die Option „Nach oben“ oder „Nach unten“ aus.
* Klicken Sie in der Liste der Palette „Tab-Reihenfolge“ auf das ausgewählte Objekt (oder wählen Sie es aus und drücken Sie F2), damit die Zahl neben dem Objektnamen bearbeitbar ist. Geben Sie dann die Zahl ein, die die neue Position des Objekts in der Tab-Reihenfolge angibt, und drücken Sie die Eingabetaste.
* Wählen Sie im Menü der Palette „Tab-Reihenfolge“ die Option „Kopieren“ aus, wählen Sie in der Liste das Objekt aus, über dem das zu verschiebende Objekt platziert werden soll, und wählen Sie dann im Menü die Option „Einfügen“ aus.

Wenn Sie das Objekt an eine neue Position in der Reihenfolge verschieben, ordnet LiveCycle Designer die Zahlen der Tab-Reihenfolge neu zu. Obwohl die Tab-Reihenfolge der Objekte auf einer Musterseite auf der Registerkarte „Design-Ansicht“ angezeigt wird, können Sie die Reihenfolge für diese Objekte nur auf der Registerkarte „Musterseiten“ ändern. Falls Sie Fragmentreferenzen in Ihrem Formular verwenden, ist die Tab-Reihenfolge in einem Fragment sichtbar, wenn Sie die Reihenfolge für das Formular anzeigen. Um die Tab-Reihenfolge in einem Fragment zu ändern, müssen Sie die Quelldatei des Fragments zur Bearbeitung öffnen, die Änderung vornehmen und die Datei speichern. Alle Formulare, die dieses Fragment verwenden, sind von dieser Änderung betroffen.

Wenn Sie die angepasste Tab-Reihenfolge in Ihrem Formular nicht übernehmen möchten, können Sie schnell zur automatischen (standardmäßigen) Tab-Reihenfolge zurückkehren, indem Sie die folgenden Schritte ausführen (dabei gehen alle Änderungen an der Tab-Reihenfolge verloren):
1. Wählen Sie auf der Palette „Tab-Reihenfolge“ die Option „Automatisch“ aus.
1. Klicken Sie im angezeigten Meldungsfeld auf „Ja“, um das Entfernen der benutzerdefinierten Tab-Reihenfolge zu bestätigen.

**Verwandte Prüfpunkte**
* Section 508 §1194.21
   * (a) Wenn eine Software für die Ausführung auf einem System mit einer Tastatur konzipiert ist, müssen alle Produktfunktionen mit einer Tastatur ausführbar sein, wobei die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell wahrnehmbar ist.
* WCAG 1.0
   * 9.2 Stellen Sie sicher, dass jedes Element, das über eine eigene Benutzeroberfläche verfügt, geräteunabhängig betrieben werden kann.
* WCAG 2.0
   * 1.3.2 Bedeutungstragende Reihenfolge: Wenn die Reihenfolge, in der Inhalte präsentiert werden, sich auf deren Bedeutung auswirkt, kann die korrekte Leseabfolge programmgesteuert bestimmt werden. (Stufe A)
   * 2.1.1 Tastatur: Alle Funktionen des Inhalts sind durch eine Tastaturschnittstelle bedienbar, ohne dass für die einzelnen Tastenanschläge spezifische Zeitvorgaben erforderlich sind, es sei denn, die zugrunde liegende Funktion erfordert Eingaben, die vom Pfad der Bewegung der Benutzenden und nicht nur von den Endpunkten abhängig sind. (Stufe A)
   * 2.1.3 Tastatur (keine Ausnahme): Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für die einzelnen Tastenanschläge spezifische Zeitvorgaben erforderlich sind. (Stufe AAA)
   * 2.4.3 Fokus-Reihenfolge: Wenn auf einer Web-Seite in einer Reihenfolge navigiert werden kann und die Reihenfolge der Navigation die Bedeutung oder Bedienung beeinflusst, erhalten die fokussierbaren Komponenten den Fokus in einer Reihenfolge, welche die Bedeutung und Bedienbarkeit aufrechterhält. (Stufe A)


## Sicherstellen, dass Formularsteuerelemente mit der Tastatur aufgerufen werden können{#ensure-keyboard-accessible}

Benutzende müssen das Formular vollständig mit der Tastatur oder einem gleichwertigen alternativen Eingabegerät ausfüllen können. Benutzende mit eingeschränkter Mobilität oder Sehfähigkeit haben möglicherweise keine andere Wahl, als die Tastatur zu verwenden, und auch viele Benutzende, die eine Maus verwenden könnten, bevorzugen die Eingabe über die Tastatur. Indem Sie mehrere Eingabeverfahren ermöglichen, erstellen Sie Formulare, die nicht nur barrierefrei sind, sondern auch den Vorlieben von allen Benutzenden entgegenkommen.

In LiveCycle Designer können Sie am einfachsten sicherstellen, dass Ihre Steuerelemente über die Tastatur zugänglich sind, indem Sie die auf der Registerkarte „Allgemein“ in der Palette „Objektbibliothek“ aufgelisteten Steuerelemente verwenden. Diese Steuerelemente reagieren standardmäßig sowohl auf Maus- als auch auf Tastatureingaben. Weitere Informationen finden Sie im Abschnitt 2.3 „Auswählen der richtigen Steuerelemente“ in diesem Handbuch.

Ein weiterer wichtiger Aspekt der Barrierefreiheit über die Tastatur besteht darin, sicherzustellen, dass jedes interaktive Element Teil der Tab-Reihenfolge des Formulars ist. Dadurch können Benutzende den Cursor mit den Tasten Tab und Umschalt+Tab vorwärts bzw. rückwärts durch das Formular bewegen. Achten Sie darauf, eine logische Tab-Reihenfolge festzulegen, die alle Felder und Schaltflächen einschließt. Weitere Informationen finden Sie im Abschnitt 2.6 „Sicherstellen, dass Leserichtung und Tab-Reihenfolge korrekt sind“ in diesem Handbuch.

Schließlich muss sichergestellt werden, dass das skriptgesteuerte Verhalten ebenfalls über die Tastatur zugänglich ist und nicht von gerätespezifischen Ereignissen abhängt. Das Mausereignis MouseEnter kann beispielsweise nicht über die Tastatur ausgeführt werden. Außerdem dürfen solche Ereignis-Handler die Barrierefreiheit über die Tastatur nicht beeinträchtigen. Achten Sie beispielsweise darauf, dass in Dropdown-Listen oder Listenfeldern verwendete Änderungs-Ereignisse keine unerwarteten Aktionen auslösen.

**Verwandte Prüfpunkte**
* Section 508 §1194.21
   * (a) Wenn eine Software für die Ausführung auf einem System mit einer Tastatur konzipiert ist, müssen alle Produktfunktionen mit einer Tastatur ausführbar sein, wobei die Funktion selbst oder das Ergebnis der Ausführung einer Funktion textuell wahrnehmbar ist.
* WCAG 1.0
   * 6.4 Stellen Sie bei Skripten und Applets sicher, dass Ereignis-Handler geräteunabhängig eingegeben werden (P2).
   * 9.2 Stellen Sie sicher, dass jedes Element, das über eine eigene Benutzeroberfläche verfügt, geräteunabhängig betrieben werden kann (P2).
   * 9.3 Geben Sie für Skripte logische Ereignis-Handler statt geräteabhängige Ereignis-Handler an (P2).
* WCAG 2.0
   * 2.1.1 Tastatur: Alle Funktionen des Inhalts sind durch eine Tastaturschnittstelle bedienbar, ohne dass für die einzelnen Tastenanschläge spezifische Zeitvorgaben erforderlich sind, es sei denn, die zugrunde liegende Funktion erfordert Eingaben, die vom Pfad der Bewegung der Benutzenden und nicht nur von den Endpunkten abhängig sind. (Stufe A)
   * 2.1.2 Keine Tastaturfalle: Wenn der Tastaturfokus durch eine Tastaturschnittstelle auf einen Bestandteil der Seite bewegt werden kann, kann der Fokus von diesem Bestandteil weg bewegt werden, indem man nur die Tastaturschnittstelle verwendet. Falls man dazu mehr als nicht modifizierte Pfeil- oder Tabulatortasten oder andere übliche Ausstiegsmethoden verwenden muss, werden die Benutzenden über die Methode zum Bewegen des Fokus informiert. (Stufe A)
   * 2.1.3 Tastatur (keine Ausnahme): Alle Funktionen des Inhalts sind über eine Tastaturschnittstelle bedienbar, ohne dass für die einzelnen Tastenanschläge spezifische Zeitvorgaben erforderlich sind. (Stufe AAA)


## Verantwortungsvoller Umgang mit Farben{#use-color-responsibly}

Beim Entwerfen von Formularen für Barrierefreiheit sind einige zusätzliche Richtlinien für die Verwendung von Farben zu beachten. Entwicklerinnen und Entwickler verwenden Farben, um das Erscheinungsbild von Formularen zu verbessern, indem sie verschiedene Formularkomponenten hervorheben. Eine unsachgemäße Verwendung von Farben kann jedoch dazu führen, dass Informationen in Ihrem Formular für Menschen mit Behinderungen schlecht oder gar nicht lesbar sind.

### Vermitteln von Informationen nicht ausschließlich mit Farben

Farben können bestimmte Teile Ihres Formulars hervorheben und verdeutlichen, allerdings sollten nicht die Farben allein Träger der Information sein.

Jegliche Informationen, die ausschließlich in Farben vermittelt werden (Farben mit einer semantischen Rolle), sind für blinde Benutzende nicht zugänglich. Dasselbe gilt für Benutzende mit einer beeinträchtigten Farbwahrnehmung oder Benutzende, die andere Farbschemata verwenden, z. B. einen Bildschirm mit hohem Farbkontrast mit weißem Text oder Vordergrund auf einem schwarzen Hintergrund. Beachten Sie auch, dass Bildschirmlesehilfen Farbinformationen nicht automatisch erkennen können.

Abbildung 13 zeigt beispielsweise ein Formularfeld mit einer roten Beschriftung (angegeben über die Palette „Schrift“), um zu kennzeichnen, dass das Formularfeld erforderlich ist. In diesem Beispiel ist die Farbe das einzige Zeichen für den Unterschied zwischen erforderlichen und optionalen Eingabefeldern. Dies macht es blinden Benutzenden oder Benutzenden mit bestimmten Arten von Farbblindheit unmöglich, sie voneinander zu unterscheiden.

![Informationsübermittlung nur mit Farben](/help/forms/using/assets/image-13.png)

Abbildung 13: **Informationsübermittlung nur mit Farben**

Um dieses Problem zu beheben, geben Sie den Status „erforderlich“ des Formulars auch im Alternativtext des Formularsteuerelements an (wie in Abschnitt 2.5 „Angeben angemessener Beschriftungen für Formularsteuerelemente“ beschrieben). Sie können beispielsweise den Text der Bildschirmlesehilfe auf „Postleitzahl (erforderlich)“ festlegen. Für Benutzende mit Sehschwächen bei Farben in bestimmten Kombinationen wird empfohlen, den Textfeldtyp auf „Benutzereingabe – Erforderlich“ in der Palette „Objekt“ festzulegen. Zusätzlich wird ein alternativer Text empfohlen, der angibt, dass das Feld erforderlich ist. Alternativ können Sie andere Hinweise als Farben verwenden, z. B. visuellen Text, Textstile und Rahmenstile. Für Benutzende von Bildschirmlesehilfen müssen Sie jedoch weiterhin die erforderlichen Informationen über die Palette „Ein-/Ausgabehilfe“ vermitteln.

Beachten Sie außerdem beim Angeben von Beschreibungen oder Anweisungen für Formularbenutzende, dass Anweisungen, die nur auf der Farbe basieren, für Benutzende mit Sehbehinderung nicht ausreichend sind. Anstelle einer Aussage wie „Klicken Sie auf die grüne Schaltfläche, um fortzufahren“ verwenden Sie beispielsweise eine Textbeschreibung für Aktionen wie „Klicken Sie auf die Schaltfläche „Weiter“, um fortzufahren“.

>[!NOTE]
> Diese Best Practice verbietet nicht die Verwendung von Farbe als solche. Sie verbietet die Verwendung von Farbe als einziges Mittel zum Vermitteln wichtiger Informationen. Wenn für diese Art von Informationen weiterhin ein visueller Hinweis gewünscht ist, könnte etwa ein Sternchen oder ein ähnliches visuelles Zeichen verwendet werden, um die erforderlichen Felder zu kennzeichnen.

### Sicherstellen von ausreichendem Farbkontrast

Viele Benutzende mit Sehbehinderung benötigen einen hohen Kontrast zwischen Text und Hintergrund, um Formulare lesen zu können. Wenn der Kontrast zwischen Hintergrund- und Vordergrundfarben nicht ausreicht, kann es für einige Benutzende schwierig oder gar unmöglich werden, ein Formular zu lesen. Abbildung 14 zeigt ein Beispiel für ein Formular mit unzureichendem Kontrast.

![Ein Formular mit unzureichendem Farbkontrast](/help/forms/using/assets/image-14.png)

Abbildung 14: **Ein Formular mit unzureichendem Farbkontrast**

Es wird dringend empfohlen, die standardmäßigen Schrift- und Hintergrundfarben zu verwenden: schwarz auf einem weißen Hintergrund. Wenn Sie diese Standardfarben ändern müssen, wählen Sie eine geeignete Kombination aus kontrastreichen Farben. Verwenden Sie entweder eine dunkle Vordergrundfarbe auf einer hellen Hintergrundfarbe oder umgekehrt. Verwenden Sie ein Tool wie den WAT-C-Farbkontrast-Analyzer, um sicherzustellen, dass der Kontrast ausreichend ist.

Mit Adobe Reader und Adobe Acrobat können Benutzende festlegen, ob Farben ersetzt werden müssen, um die visuellen Anforderungen zu erfüllen. Die Benutzenden können ihr eigenes Kontrastschema angeben oder ein vom Betriebssystem bereitgestelltes Schema verwenden. Darüber hinaus verfügen Adobe Reader und Adobe Acrobat über ein eigenes Kontrastschema, das aktiviert werden kann. Damit diese Optionen erfolgreich sind, sollten Sie immer Standardfarben verwenden.

Beim Entwerfen Ihres Formulars sollten Sie dieses häufig mit einem Farbschema testen, wie es viele sehbehinderte Benutzende beim Ausfüllen verwenden. Dadurch können Sie beim Entwurf frühzeitig Probleme erkennen und beheben.

Empfehlungen zur Verwendung von Farben:
* Achten Sie darauf, dass keine Informationen verloren gehen, wenn die semantische Farbe nicht sichtbar ist.
* Falls Sie keine Standardfarben verwenden können, stellen Sie sicher, dass Ihre Farben einen hohen Kontrast aufweisen, z. B. schwarz auf einem hellen (weißen) Hintergrund. Sehendbehinderte Benutzende benötigen im Allgemeinen einen hohen Kontrast zwischen dem Text und seinem Hintergrund, um den Text lesen zu können.
* Testen Sie die Lesbarkeit Ihrer Formulare, indem Sie Ihren Bildschirm in Windows und in Adobe Reader oder Adobe Acrobat auf eine kontrastreiche Anzeige umstellen. Mac OSX bietet nur einen einfachen Graustufenfilter für hohen Kontrast, was für Tests nicht ausreicht.
* Vermitteln Sie keine Informationen ausschließlich auf der Grundlage von Farben. Verwenden Sie beispielsweise nicht nur Farben, um wichtige Textteile hervorzuheben. Verwenden Sie auch andere Methoden zur Hervorhebung sowie Textbeschreibungen.
* Verwenden Sie nicht zu viele Farben, da dies das Lesen der eigentlichen Informationen im Inhalt erschweren kann. Verleihen Sie der Lesbarkeit der Informationen immer oberste Priorität, wenn Sie entscheiden, welche Farben verwendet werden sollen.

**Verwandte Prüfpunkte**
* Section 508 §1194.21
   * (i) Die Farbcodierung darf nicht als einziges Mittel zur Übermittlung von Informationen, zur Anzeige einer Aktion, zur Aufforderung zu einer Reaktion oder zur Unterscheidung eines visuellen Elements verwendet werden.
* WCAG 1.0
   * 2.1 Stellen Sie sicher, dass alle Informationen, die durch Farben vermittelt werden, auch ohne Farben verfügbar sind, z. B. über Kontext oder Markup.
   * 2.2 Stellen Sie sicher, dass die Kombinationen aus Vordergrund- und Hintergrundfarben einen ausreichenden Kontrast bieten, wenn sie von einer Person mit Farbenblindheit oder auf einem Schwarzweißbildschirm angezeigt werden. [Priorität 2 für Bilder, Priorität 3 für Text] (P2).
* WCAG 2.0
   * 1.4.1 Verwendung von Farben: Farben werden nicht als einziges visuelles Mittel eingesetzt, um Informationen zu vermitteln, eine Aktion zu kennzeichnen, eine Antwort einzuholen oder ein visuelles Element zu unterscheiden. (Stufe A)
   * 1.4.3 Kontrast (Minimum): Die visuelle Darstellung von Text und Bildern von Text hat ein Kontrastverhältnis von mindestens 4,5:1 mit folgenden Ausnahmen: (Stufe AA)
   * 1.4.6 Kontrast (Erweitert): Die visuelle Darstellung von Text und Abbildungen von Text hat ein Kontrastverhältnis von mindestens 7:1, mit den folgenden Ausnahmen: (Stufe AAA)


## Bereitstellen von Überschriftzellen für Tabellen{#provide-heading-cells}

Tabellen sind eine effektive Möglichkeit, Inhalte in barrierefreien Formularen zu organisieren und darzustellen. Bei entsprechender Verwendung bieten die Zeilen und Spalten einer Tabelle eine vorhersehbare und konsistente Struktur für Formularinhalte. Wenn Benutzende einer Bildschirmlesehilfe beispielsweise zu einer Textzeilenzelle navigieren, gibt die Bildschirmlesehilfe die Zellenposition an und liest dann den Zelleninhalt. Die Zellenposition wird von der Bildschirmlesehilfe mithilfe einer Kombination aus Zeilen- und Spaltenüberschriften oder Zeilen- und Spaltennummern bestimmt. Da Bildschirmlesehilfen Informationen liefern, mit deren Hilfe die Benutzenden sich im Inhalt der Tabelle orientieren können, hat das Layout unmittelbare Auswirkungen auf die Barrierefreiheit der Tabelle.

Sie können beim Erstellen von Tabellen die folgenden Rollen für Tabellenelemente festlegen. Diese Rollen ermöglichen es Bildschirmlesehilfen, mithilfe spezieller Tastaturbefehle in der Tabellenstruktur zu navigieren, und vermitteln den Benutzenden die Beziehung zwischen Tabellenzellen und den entsprechenden Kopfzeilenzellen.
* Tabelle
Weist dem ausgewählten Teilformular die Rolle einer Tabelle zu. Wenn Benutzende zu diesem Teilformular navigieren, erkennen die meisten Bildschirmlesehilfen es als Tabelle und geben die Anzahl der Zeilen und Spalten an.
* Kopfzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Rolle einer Kopfzeile zu. Beim Lesen des Inhalts einer Textzeilenzelle wird von den meisten Bildschirmlesehilfen zunächst der Inhalt der zugehörigen Kopfzeilenzelle bestimmt.
* Textzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Rolle einer Textzeile zu. Enthält eine Zelle ein Teilformular, lesen Bildschirmlesehilfen normalerweise den Inhalt der zugehörigen Zelle in der Kopfzeile und anschließend die Felder im Teilformular.
* Fußzeile
Weist dem ausgewählten Teilformular bzw. der ausgewählten Tabellenzeile die Rolle einer Fußzeile zu.
* (Keine)
Gibt eine Zeile an, die Informationen über die Tabelle oder ihren Inhalt vermittelt. Die Zeile wird nicht als Teil der Tabelle angesehen, ihr Inhalt wird jedoch von der Bildschirmlesehilfe vorgelesen.

Bei entsprechender Verwendung bieten Tabellen eine effektive Möglichkeit, tabellarische Informationen zu organisieren und darzustellen. Vermeiden Sie übermäßig komplexe Tabellen, etwa Tabellen, die verschachtelte Tabellen und Abschnitte enthalten.

### Barrierefreies Gestalten einfacher Tabellen

Es werden Tabellen mit einfachen Layouts empfohlen. Einfache Tabellen beginnen mit einer einzelnen Kopfzeile, gefolgt von den Textzeilen.

Beachten Sie beim Entwerfen einfacher Tabellen für Barrierefreiheit folgende Richtlinien:

* Die Tab-Reihenfolge für eine Tabelle ist die geografische Reihenfolge, die auch für das Formular selbst gilt. Der Tabelleninhalt sollte so angeordnet sein, dass er beim Lesen der Tabelle von links nach rechts und von oben nach unten problemlos erfasst werden kann.
* Die meisten Bildschirmlesehilfen interpretieren die erste Zeile einer Tabelle als Kopfzeile. Beim Lesen des Inhalts einer Textzeilenzelle mit einer Bildschirmlesehilfe wird zunächst der Inhalt der zugehörigen Kopfzeilenzelle gelesen. Jede Kopfzeilenzelle sollte daher eine aussagekräftige Beschreibung des Spalteninhalts enthalten. 
* Vermeiden Sie Zellen, die zwei oder mehrere Spalten umfassen, sowie verschachtelte Tabellen oder Tabellenabschnitte. Diese Funktionen werden von einigen Bildschirmlesehilfen oft nicht korrekt interpretiert und daher möglicherweise ignoriert. Wenn z. B. eine Zelle in einer Textzeile zwei Spalten umfasst, können Bildschirmlesehilfen möglicherweise beim Lesen der nächsten Zelle in der Zeile den korrekten Zelleninhalt in der Kopfzeile nicht referenzieren.

### Barrierefreies Gestalten komplexer Tabellen

Wenn Sie Tabellen für Barrierefreiheit entwerfen, versuchen Sie, das Tabellen-Layout einfach zu halten, wobei auf eine Kopfzeile Textzeilen folgen. Natürlich können manche Inhalte ein komplexeres Tabellen-Layout erfordern. Beispielsweise müssen Sie möglicherweise eine Zelle verwenden, die sich über mehrere Kopfzeilen erstreckt, um den Inhalt effektiv zu vermitteln.

Sie können komplexe Tabellen erstellen, indem Sie das Tabellenobjekt verwenden oder Teilformularobjekte kombinieren. Das Tabellenobjekt enthält Funktionen zur Unterstützung des Design-Prozesses, z. B. Optionen zum Einfügen und Ändern der Größe von Spalten und Zeilen.

Mithilfe der Palette „Ein-/Ausgabehilfe“ können Sie tabellenbezogene Rollen für Teilformulare festlegen, um eine barrierefreie komplexe Tabelle zu erstellen. Abhängig von Ihrer Erfahrung mit Designs und Ihren Präferenzen können Sie zum Erstellen komplexer Tabellen Teilformularobjekte kombinieren. Sie können z. B. ein Teilformular mit zwei Zeilen erstellen, dieses Teilformular als Kopfzeile für die Tabelle festlegen und dann ein anderes Teilformular für die Tabellentextzeilen definieren.

Bei der Erstellung von Tabellen mit Teilformularobjekten anstelle von Tabellenobjekten sind einige zusätzliche Schritte erforderlich:
* Legen Sie auf der Registerkarte „Teilformular“ für jedes Teilformular den Typ auf „Position“ fest.
* Legen Sie in der Palette „Ein-/Ausgabehilfe“ für jedes Teilformular der Tabelle eine geeignete Teilformularrolle fest. Weisen Sie z. B. dem Teilformular, das als Tabellenüberschrift dienen soll, die Rolle „Kopfzeile“ zu. 
* Weisen Sie Zeilen, die Informationen über die Tabelle oder deren Inhalt enthalten, aber nicht als Teil der Tabelle anzusehen sind, die Teilformularrolle „Keine“ zu. Die Bildschirmlesehilfe liest den Zeileninhalt.

Die von der Bildschirmlesehilfe unterstützten Funktionen bestimmen, welche Informationen für eine komplexe Tabelle gelesen werden. Betrachten Sie beispielsweise eine Tabelle, die eine Kopfzeile und einen Abschnitt mit einer Kopfzeile enthält. Wenn Benutzende zu einer Textzeilenzelle im Tabellenabschnitt navigieren, lesen Bildschirmlesehilfen normalerweise den folgenden Inhalt in dieser Reihenfolge:
* Inhalt der entsprechenden Zelle in der Kopfzeile der Tabelle
* Inhalt der entsprechenden Zelle in der Kopfzeile des Abschnitts
* Inhalt der ausgewählten Zelle
Einige Bildschirmlesehilfen lesen jedoch möglicherweise nicht den Inhalt der beiden Kopfzeilen.

Erstellen Sie aussagekräftige, sichtbare Namen oder Titel für Ihre Tabellen. Sie können einen Tabellennamen als statischen Text in Adobe LiveCycle Designer erstellen und ihn vor der Tabelle platzieren. Sie können eine Tabelle und ihren Namen in einem Teilformular gruppieren. Teilformulare sind besonders nützlich, wenn Sie verknüpfte Objekte in einem Layout kombinieren möchten.

Bei Steuerelementen in Tabellenzellen gibt die Bildschirmlesehilfe an, was immer Sie als Beschriftung, QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text für das Objekt angeben. Wenn Sie die Spaltenüberschrift als Alternativtext für ein Steuerelement in einer Tabelle verwenden möchten, geben Sie weder Beschriftung noch QuickInfo oder benutzerdefinierten Bildschirmlesehilfen-Text an. Beachten Sie jedoch, dass diese Strategie für Benutzende von Bildschirmlesehilfen nicht immer eindeutig ist, da Bildschirmlesehilfen die Spaltenüberschrift möglicherweise nur dann mit dem Steuerelement verknüpfen, wenn sich die Benutzenden nicht im Formularinteraktionsmodus der Bildschirmlesehilfe befinden.

**Verwandte Prüfpunkte**
* Section 508 §1194.22
   * (g) Für Datentabellen werden Zeilen- und Spaltenüberschriften angegeben.
   * (h) Es wird Markup verwendet, um Datenzellen und Überschriftenzellen für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften zuzuordnen.
* WCAG 1.0
   * 5.1 Identifizieren Sie bei Datentabellen die Zeilen- und Spaltenüberschriften (P1).
   * 5.2 Für Datentabellen mit zwei oder mehr logischen Ebenen von Zeilen- oder Spaltenüberschriften verwenden Sie Markup, um Datenzellen und Überschriftenzellen zuzuordnen (P1)
* WCAG 2.0
   * 1.3.1 Informationen und Beziehungen: Informationen, Struktur und Beziehungen, die durch die Präsentation vermittelt werden, können programmgesteuert festgelegt werden oder sind im Text verfügbar. (Stufe A)


## Bereitstellen einer navigierbaren Formularstruktur{#provide-navigable-form}

Wenn ein Formular lang und komplex wird, wird seine Benutzerfreundlichkeit durch die Struktur stark beeinflusst. So wie ein Buch leichter zu verstehen ist, wenn es in Kapitel und Abschnitte unterteilt ist, ist ein Formular leichter verwendbar, wenn es in Überschriften und Unterüberschriften unterteilt ist. Diese Partitionierung ist aus den folgenden Gründen besonders für Benutzende von Bildschirmlesehilfen nützlich:
* Jede Überschrift teilt den Benutzenden der Bildschirmlesehilfe mit, was im Abschnitt nach der Überschrift zu erwarten ist.
* Bildschirmlesehilfen bieten Tastaturbefehle, mit denen schnell zwischen den verschiedenen Überschriften im Formular hin- und hergesprungen werden kann. Außerdem können die Benutzenden auf eine Liste von Überschriften zugreifen, die ihnen einen Überblick über die Dokumentstruktur bietet und eine schnelle Navigation ermöglicht.

Durch die Bereitstellung von Mechanismen, die es den Benutzenden ermöglichen, zu anderen Bereichen des Formulars zu springen, kann das Formular praktischer werden. Sie können Ihrem Formular mithilfe der Palette „Ein-/Ausgabehilfe“ in LiveCycle Designer eine Überschriftenstruktur hinzufügen.

### Bereitstellung von Mechanismen zum Überspringen

Sehende Benutzende können eine Seite in beliebiger Reihenfolge überfliegen. Sie können etwa beginnen, indem sie sich die rechte untere Ecke der Seite ansehen und den Inhalt dann rückwärts überfliegen. Benutzende einer Bildschirmlesehilfe haben diese Option nicht, da die Bildschirmlesehilfe mit dem Lesen der Seite oben links (wie im Quell-Code dargestellt) beginnt und sich in einer linearen Reihenfolge bewegt. Darüber hinaus können sehende Benutzende die Seite nach interessanten Links durchsuchen und diese mit der Maus aktivieren. Benutzende der Bildschirmlesehilfe müssen sich der Reihe nach durch die Seite bewegen.

Die einfachste und effektivste Methode, eine navigierbare Formularstruktur zu bieten, besteht darin, Strukturüberschriften und richtig definierte Listen im Formular zu verwenden.
Sie können auch Mechanismen bereitstellen, mit denen Benutzende zu anderen Bereichen des Formulars springen können, z. B. durch Hinzufügen von Navigationsschaltflächen oben und unten im Formular. Am Anfang Ihres Formulars könnten Sie folgende Schaltflächen einfügen: „Datendatei öffnen“, „Vorherige Seite“ oder „Nächste Seite“. Am Formularende könnten z. B. folgende Schaltflächen verwendet werden: „Daten speichern“, „Daten per E-Mail senden“, „Zum Anfang“ oder „Drucken“.

Intelligente Felder können das Ausfüllen einiger Formulare erleichtern. So kann z. B. ein Formular für die Reisekostenabrechnung über mehrere Zeilen und Spalten von Feldern verfügen. Wenn eine bestimmte Zeile leer bleibt, kann das Drücken der Tabulatortaste für das letzte Element in dieser Zeile den Sprung zum nächsten Abschnitt des Formulars bewirken, anstatt weiterhin durch eine Reihe von Feldern zu springen, die leer sind.

### Hinzufügen von Überschriften mithilfe der Palette „Ein-/Ausgabehilfe“

Mithilfe der Palette „Ein-/Ausgabehilfe“ können Sie Objekten je nach Verwendungszweck des Objekts Rollen zuweisen. Diese Rollen können angewendet werden, um Überschriften auf unterschiedlichen Ebenen zu erstellen.

![Festlegen einer Überschriftenrolle in der Palette „Ein-/Ausgabehilfe“](/help/forms/using/assets/image-15.png)
Abbildung 15: **Festlegen einer Überschriftenrolle in der Palette „Ein-/Ausgabehilfe“**

Führen Sie die folgenden Schritte aus, um eine Überschrift in Ihrem Formular zu erstellen:

1. Identifizieren Sie den Anfang jedes logischen Segments Ihres Formulars mithilfe von statischen Textbeschriftungen,
1. Wählen Sie für jede Bezeichnung eine der Überschriftoptionen in der Palette „Ein-/Ausgabehilfe“ als Rolle aus. Die verschiedenen Überschriftebenen (1 bis 6) ermöglichen es Ihnen, eine Überschriftenstruktur in Ihrem Formular zu erstellen. Beginnen Sie mit Ebene 1 und verwenden Sie dann Ebene 2 und so weiter für verschachtelte Unterabschnitte.

Die meisten Bildschirmlesehilfen ermöglichen es Benutzenden, je nach Ebene schnell zwischen Überschriftelementen zu navigieren. Abbildung 16 zeigt ein Formular, das mithilfe von Überschriften in kleinere Segmente unterteilt ist. In diesem Beispiel wird die folgende Überschriftstruktur verwendet:

* Überschriftebene 1: Produktanfrage
   * Überschriftebene 2: Bestelldetails
      * Überschriftebene 3: Lieferoptionen
* Überschriftebene 2: Zusätzliche Informationen
   * Überschriftebene 3: Persönliche Daten
   * Überschriftebene 3: Adresse

![Strukturieren eines Formulars mithilfe von Überschriften](/help/forms/using/assets/image-16.png)

Abbildung 16: **Strukturieren eines Formulars mithilfe von Überschriften**

Diese Überschriften sind nur statische Textelemente, denen eine bestimmte Schriftgröße und eine Überschriftenrolle mit der entsprechenden Ebene zugewiesen wurde.

>[!NOTE]
> Wenn Sie einfach das Erscheinungsbild einer Textbeschriftung so ändern, dass sie wie eine Überschrift aussieht, wird sie von Bildschirmlesehilfen nicht als Überschrift erkannt. Sie müssen deswegen eine Überschriftenrolle anwenden.

Stellen Sie stets sicher, dass die Reihenfolge der Überschriftebenen logisch ist. So muss beispielsweise ein Unterabschnitt einer Überschrift der Stufe 2 stets eine Überschrift der Stufe 3 sein. Sie sollten beim Markieren von Unterabschnitten nie Ebenen überspringen. Benutzende von Bildschirmlesehilfen verwenden die verschiedenen Ebenen, um die Struktur des Formulars besser zu verstehen. Wenn Benutzende beispielsweise auf eine Überschrift der Ebene 2 stoßen, können sie einen Tastaturbefehl verwenden, um nach Überschriften der Ebene 3 zu suchen und festzustellen, ob es Unterabschnitte gibt. Wenn Sie jedoch Ebenen überspringen, haben die Benutzenden Schwierigkeiten, diese Unterabschnitte zu identifizieren.

### Markieren von Listen

Manchmal kann es auch nützlich sein, dem Formular Listeninhalte hinzuzufügen. Listen sind nützlich, um verwandte Elemente zusammenzufassen, und sie ermöglichen es Benutzenden von Bildschirmlesehilfen, zu erfahren, wie viele Elemente in einer Liste enthalten sind, und ggf. schnell daran vorbeizunavigieren. Durch die korrekte Markierung von Listen wird die Struktur Ihres Formulars für Benutzende von Bildschirmlesehilfen klarer.

In LiveCycle Designer erstellen Sie Listen mit Unterformularen mit den folgenden Schritten:

1. Wählen Sie ein Unterformular aus, das den Inhalt enthält, der als Listenelement markiert werden soll.
1. Wählen Sie in der Palette „Barrierefreiheit“ die Rolle „Liste“ aus.
1. Wählen Sie jedes verschachtelte Unterformular im Unterformular „Liste“ aus und legen Sie seine Rolle auf „Listenelement“ fest.

>[!NOTE]
> Die Rolle „Listenelement“ kann nur einem Unterformular zugewiesen werden, das in einem Unterformular enthalten ist, für das eine Listenrolle angegeben ist. Sie können eine Tabelle oder Tabellenzeile nicht als Liste oder Listenelement definieren. Ein Listenelement kann jedoch eine Tabelle enthalten.

**Verwandte Prüfpunkte**
* Abschnitt 508 §11934.22
   * (o) Es muss eine Methode bereitgestellt werden, die es den Benutzenden ermöglicht, sich wiederholende Navigationslinks zu überspringen.
* WCAG 1.0
   * 3.5 Verwenden Sie Header-Elemente, um die Dokumentstruktur zu vermitteln, und verwenden Sie sie gemäß den Spezifikationen (P2).
   * 3.6 Markieren Sie Listen und Listenelemente ordnungsgemäß. (P2).
   * 12.3 Teilen Sie große Informationsblöcke in handlichere Gruppen auf, wo immer dies auf natürliche Weise möglich und zweckmäßig ist. (P2).
   * 13.3 Stellen Sie Informationen über das allgemeine Layout einer Website bereit (z. B. eine Sitemap oder ein Inhaltsverzeichnis).
   * 13.4 Verwenden Sie Navigationsmechanismen auf konsistente Weise (P2).
* WCAG 2.0
   * 1.3.2 Bedeutungstragende Reihenfolge: Wenn die Reihenfolge, in der Inhalte präsentiert werden, sich auf deren Bedeutung auswirkt, kann die korrekte Leseabfolge programmgesteuert bestimmt werden. (Stufe A)
   * 2.4.1 Blöcke umgehen: Es gibt einen Mechanismus, um Inhaltsblöcke zu umgehen, die auf verschiedenen Web-Seiten wiederholt werden. (Stufe A)
   * 2.4.5 Verschiedene Methoden: Es gibt mehr als eine Methode, um eine Web-Seite innerhalb eines Satzes von Web-Seiten zu finden, es sei denn, die Web-Seite ist das Ergebnis oder ein Schritt innerhalb eines Prozesses. (Stufe AA)
   * 2.4.6 Überschriften und Beschriftungen: Überschriften und Beschriftungen beschreiben ein Thema oder einen Zweck. (Stufe AA)
   * 2.4.10 Abschnittsüberschriften: Abschnittsüberschriften dienen zur Organisation des Inhalts. (Stufe AAA)
   * 3.2.3 Konsistente Navigation: Navigationsmechanismen, die auf mehreren Web-Seiten innerhalb eines Satzes von Web-Seiten wiederholt werden, treten jedes Mal, wenn sie wiederholt werden, in der gleichen relativen Reihenfolge auf, es sei denn, eine Änderung wird durch Benutzende ausgelöst. (Stufe AA)


## Vermeiden von störendem Scripting{#avoid-disruptive-scripting}

Im Rahmen des Formularentwurfsprozesses können Skripte verwendet werden, um ein besseres Anwendererlebnis zu bieten. Sie können Skripte zu den meisten Formularfeldern und -objekten hinzufügen. Beispielsweise können Sie einfache Skripte erstellen, um Werte in einem interaktiven Formular als Reaktion auf Benutzereingaben dynamisch zu aktualisieren.

Beachten Sie beim Entwerfen von Skripten für die Barrierefreiheit die folgenden allgemeinen Richtlinien:

* Der Formularinhalt sollte keine optischen Störungen enthalten. Vermeiden Sie beispielsweise Funktionen, die dazu führen, dass Inhalte flackern, blinken oder sich bewegen.
* Stellen Sie sicher, dass Popup-Fenster nur bei von Benutzenden ausgelösten Aktionen angezeigt werden. Ebenso sollten Sie nicht zulassen, dass sich der aktuelle Fokus des Formulars (die aktuelle Ansicht der Benutzenden) ändert oder Inhalte erneut angezeigt werden, es sei denn, dies wird von den Benutzenden initiiert. Wenn die Benutzenden beispielsweise Felder in der unteren Hälfte des Formulars ausfüllen, sollte der Fokus sich nicht in die obere linke Ecke des Formulars verschieben, es sei denn, die Benutzenden entscheiden sich, zu dieser Stelle zu navigieren.
* Benutzende mit Einschränkungen benötigen möglicherweise mehr Zeit, um Eingaben in Feldern vorzunehmen. Geben Sie keine zeitbasierten Antworten für Eingabefelder an.
* Beachten Sie, dass Client-seitige Skripte mit Bildschirmlesehilfen und Tastaturen in Konflikt geraten können, wenn das Skript den Fokus der Client-Anwendung ändert. Zum Beispiel können die Ereignisse „change“ und „mouseEnter“ bei Verwendung mit Dropdown-Listen oder Listenfeldern unerwartete Aktionen auslösen. Stellen Sie sicher, dass Ihre Client-seitigen Skripte keine Probleme für Benutzende von Bildschirmlesehilfen und Benutzende, die nur die Tastatur verwenden, verursachen.
* Benutzende von Hilfstechnologien benötigen manchmal zusätzliche Zeit, um Aufgaben zu erledigen. Zeigen Sie in jedem Fall, in dem eine zeitgesteuerte Routine bald abläuft, eine zugängliche Meldung an, um eine Verlängerung zu ermöglichen. Über JavaScript erstellte Warnfelder können mithilfe von Hilfstechnologien verwendet werden. Es kann auch ein neues Fenster mit einer Meldung angezeigt werden, die die Benutzenden auf eine bevorstehende Zeitüberschreitung hinweist.

**Verwandte Prüfpunkte**:
* Section 508 §1194.22
   * (l) Wenn Seiten Skriptsprachen verwenden, um Inhalte anzuzeigen oder Schnittstellenelemente zu erstellen, werden die vom Skript bereitgestellten Informationen mit funktionalem Text identifiziert, der von Hilfstechnologien gelesen werden kann.
   * (p) Wenn eine zeitgesteuerte Antwort erforderlich ist, sollten die Benutzenden benachrichtigt werden und ausreichend Zeit erhalten, um anzugeben, dass mehr Zeit benötigt wird.
* WCAG 1.0
   * 1.4 Bei zeitbasierten Multimedia-Präsentationen (z. B. einem Film oder einer Animation) sollten entsprechende Alternativen (z. B. Untertitel oder akustische Beschreibungen der visuellen Spur) mit der Präsentation synchronisiert werden (P1).
   * 6.2 Stellen Sie sicher, dass Äquivalente für dynamische Inhalte aktualisiert werden, wenn sich der dynamische Inhalt ändert.
   * 6.3 Stellen Sie sicher, dass die Seiten auch dann nutzbar sind, wenn Skripte, Applets oder andere programmatische Objekte deaktiviert sind oder nicht unterstützt werden. Ist dies nicht möglich, stellen Sie gleichwertige Informationen auf einer alternativ zugänglichen Seite bereit.
   * 6.5 Stellen Sie sicher, dass dynamischer Inhalt zugänglich ist, oder bieten Sie eine alternative Präsentation bzw. Seite an (P2).
   * 8.1 Ermöglichen Sie den direkten Zugriff auf programmatische Elemente wie Skripte und Applets oder machen Sie sie mit unterstützenden Technologien kompatibel[. Priorität 1, wenn die Funktionalität wichtig ist und nicht an anderer Stelle dargestellt wird], andernfalls (P2).
   * 9.3 Geben Sie für Skripte logische Ereignis-Handler statt geräteabhängige Ereignis-Handler an (P2).
   * 10.1 Solange Benutzeragenten es Benutzenden ermöglichen, erzeugte Fenster zu deaktivieren, sollten Sie keine Pop-ups oder andere Fenster erscheinen lassen und das aktuelle Fenster nicht ändern, ohne die Benutzenden darüber zu informieren.
* WCAG 2.0
   * 3.2.1 Im Fokus: Wenn eine Komponente in den Fokus rückt, löst dies keine Kontextänderung aus. (Stufe A)
   * 3.2.2 Bei Eingabe: Das Ändern der Einstellung einer beliebigen Komponente der Benutzerschnittstelle führt nicht automatisch zu einer Änderung des Kontexts, es sei denn, die Benutzenden wurden vor der Verwendung der Komponente über das Verhalten informiert. (Stufe A)
   * 3.2.5 Änderung auf Anfrage: Kontextänderungen werden nur auf Anfrage von Benutzenden initiiert oder es ist ein Mechanismus verfügbar, um solche Änderungen zu deaktivieren. (Stufe AAA)

## Sicherstellen, dass auf alle Audio- und Videoinhalte zugegriffen werden kann{#ensure-audio-video-accessible}

Wenn Ihre Formulare Audio- oder Videoinhalte enthalten, einschließlich Audio- und Video-Clips, müssen Sie sicherstellen, dass diese Inhalte zugänglich sind. Achten Sie insbesondere darauf, dass in Formulare integrierte Video-Clips Untertitel für gehörlose und schwerhörige Benutzende sowie Videobeschreibungen für blinde Benutzende enthalten. Für Audiodateien, die nicht mit Videoinhalten synchronisiert werden, reicht ein einfaches Transkript aus.
Informationen zur Bereitstellung von Untertiteln für Flash-basierte Medien finden Sie unter diesem [Link](/help/forms/using/best-practices-for-creating-forms-in-designer.md).

**Verwandte Prüfpunkte**:
* Section 508 §1194.22
   * (b) Entsprechende Alternativen für alle multimedialen Darstellungen werden mit der Präsentation synchronisiert.
* WCAG 1.0
   * 1.1 Geben Sie für jedes nichttextliche Element ein Textäquivalent an (z. B. über „alt“, „longdesc“ oder im Elementinhalt). Dazu gehören Bilder, grafische Darstellungen von Text (einschließlich Symbolen), Imagemap-Bereiche, Animationen (z. B. animierte GIFs), Applets und programmatische Objekte, ASCII-Grafiken, Frames, Skripte, als Aufzählungszeichen verwendete Bilder, Abstände, grafische Schaltflächen, Töne (mit oder ohne Benutzerinteraktion wiedergegeben), eigenständige Audiodateien, Audiospuren von Videos und Video (P1).
   * 1.3 Bis Benutzeragenten automatisch das Textäquivalent einer visuellen Spur vorlesen können, stellen Sie eine auditive Beschreibung der wichtigen Informationen der visuellen Spur einer Multimedia-Präsentation bereit (P1).
   * 1.4 Bei zeitbasierten Multimedia-Präsentationen (z. B. einem Film oder einer Animation) sollten entsprechende Alternativen (z. B. Untertitel oder akustische Beschreibungen der visuellen Spur) mit der Präsentation synchronisiert werden (P1).
* WCAG 2.0
   * 1.2.1 Nur-Audio und Nur-Video (voraufgezeichnet): Für voraufgezeichnete Nur-Audio- und Nur-Video-Medien gilt Folgendes, es sei denn, es handelt sich bei dem Audio- oder Videomaterial um eine Medienalternative für Text und diese ist eindeutig als solche gekennzeichnet: (Stufe A)
   * 1.2.2 Untertitel (voraufgezeichnet): Für alle voraufgezeichneten Audioinhalte in synchronisierten Medien werden Untertitel bereitgestellt, es sei denn, es handelt sich bei dem Medium um eine Medienalternative für Text, die eindeutig als solche gekennzeichnet ist. (Stufe A)
   * 1.2.3 Audiobeschreibung oder Medienalternative (voraufgezeichnet): Eine Alternative für zeitbasierte Medien oder eine Audiobeschreibung des voraufgezeichneten Videoinhalts wird für synchronisierte Medien bereitgestellt, es sei denn, es handelt sich bei dem Medium um eine Medienalternative für Text, die eindeutig als solche gekennzeichnet ist. (Stufe A)
   * 1.2.4 Untertitel (Live): Untertitel werden für alle Live-Audioinhalte in synchronisierten Medien bereitgestellt. (Stufe AA)
   * 1.2.5 Audiobeschreibung (voraufgezeichnet): Für alle voraufgezeichneten Audioinhalte in synchronisierten Medien wird eine Audiobeschreibung bereitgestellt. (Stufe AA)
   * 1.2.6 Gebärdensprache (voraufgezeichnet): Für alle voraufgezeichneten Audioinhalte in synchronisierten Medien wird eine Übersetzung in Gebärdensprache bereitgestellt. (Stufe AAA)
   * 1.2.7 Erweiterte Audiobeschreibung (voraufgezeichnet): Wenn Pausen im Vordergrund-Audio nicht ausreichen, um mit Audiobeschreibungen den Sinn des Videos zu vermitteln, wird für alle vorgezeichneten Videoinhalte in synchronisierten Medien eine erweiterte Audiobeschreibung bereitgestellt. (Stufe AAA)
   * 1.2.8 Alternative für Medien (voraufgezeichnet): Eine Alternative für zeitbasierte Medien wird für alle voraufgezeichneten synchronisierten Medien und für alle voraufgezeichneten Nur-Video-Medien bereitgestellt. (Stufe AAA)
   * 1.2.9 Nur-Audio (live): Es wird eine Alternative für zeitbasierte Medien bereitgestellt, die gleichwertige Informationen für live übertragene Audioinhalte bietet. (Stufe AAA)

## Kennzeichnen natürlicher Sprache und aller Sprachänderungen{#identify-natural-language}

Der Inhalt von Formularen wird von unterstützenden Technologien vorgelesen, die sprachspezifische Sprach-Synthesizer verwenden. Daher ist es wichtig, die Hauptsprache des Formulars korrekt zu identifizieren, um sicherzustellen, dass die Formulare auch in der vorgesehenen Sprache vorgelesen werden.

Wenn der Text (oder Alternativtext) in Ihren Formularen in mehr als einer Sprache vorliegt, müssen Sie die Bereiche Ihres Formulars kennzeichnen, in denen von einer Sprache in eine andere gewechselt wird.

In LiveCycle Designer wird die primäre Sprache festgelegt, indem die Gebietsschema-Eigenschaft des Formulars und die Gebietsschema-Eigenschaft für das Unterformular der obersten Ebene festgelegt werden. Um Änderungen an der Primärsprache zu identifizieren, ändern Sie die Gebietsschema-Eigenschaft für Objekte, die eine andere Sprache als die Sprache des Formulars verwenden.

So legen Sie die Gebietsschema-Eigenschaft eines Formulars fest:
1. Wählen Sie „Datei“ > „Formulareigenschaften“ und dann die Registerkarte „Standard“.
2. Wählen Sie die entsprechende Sprache für das Formulargebietsschema aus (siehe Abbildung 17).
3. Klicken Sie auf „OK“.

![Ändern der Formulargebietsschema-Einstellungen im Dialogfeld „Formulareigenschaften“](/help/forms/using/assets/image-17.png)

Abbildung 17: **Ändern der Formulargebietsschema-Einstellungen im Dialogfeld „Formulareigenschaften“**

So legen Sie die Gebietsschema-Eigenschaft des obersten Unterformulars oder eines Objekts fest, das eine andere Sprache erfordert:
1. Auswählen des obersten Unterformulars oder Objekts in der Designansicht
1. Anzeige der Objektpalette über „Fenster“ > „Objekt“
1. Wählen Sie in der Objektpalette die Registerkarte „Feld“ aus und wählen Sie in der Liste „Gebietsschema“ die Sprache aus, die für das Objekt verwendet werden soll (siehe Abbildung 18). Wenn Sie verschiedene Gebietsschemaoptionen auf einzelne Objekte anwenden, beachten Sie, dass die Objekte, die sich in Tabellen und Unterformularen befinden, automatisch dieselbe Gebietsschema-Einstellung wie das Tabellen- und Unterformularobjekt erhalten.

![Ändern des Gebietsschemas eines Objekts](/help/forms/using/assets/image-18.png)

Abbildung 18: **Ändern des Gebietsschemas eines Objekts**

**Verwandte Prüfpunkte**:
* WCAG 1.0
   * 4.1 Identifizieren Sie Änderungen in der natürlichen Sprache des Textes eines Dokuments und in allen Textäquivalenten (z. B. Bildunterschriften) eindeutig.
* WCAG 2.0
   * 3.1.1 Sprache der Seite: Die Standardsprache jeder Web-Seite kann programmgesteuert festgelegt werden. (Stufe A)
   * 3.1.2 Sprache von Teilen: Die menschliche Sprache jedes Abschnitts oder Satzes im Inhalt kann programmgesteuert bestimmt werden, mit Ausnahme von Eigennamen, technischen Begriffen, Wörtern unbestimmter Sprache und Wörtern oder Formulierungen, die Teil der Fachsprache des unmittelbar umgebenden Textes geworden sind. (Stufe AA)
