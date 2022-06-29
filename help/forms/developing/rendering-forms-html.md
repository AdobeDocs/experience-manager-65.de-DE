---
title: Rendern von Formularen als HTML
seo-title: Rendering Forms as HTML
description: Verwenden Sie den Forms-Dienst, um Formulare als Antwort auf eine HTTP-Anforderung von einem Webbrowser als HTML zu rendern. Sie können die Java-API und die Web Service-API verwenden, um Formulare als HTML wiederzugeben.
seo-description: Use the Forms service to render forms as HTML in response to an HTTP request from a web browser. You can use the Java API and Web Service API to render forms as HTML.
uuid: bd8edb6f-333b-4ceb-9877-618f5377f56f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 669ede46-ea55-444b-a23f-23a86e5aff8e
role: Developer
exl-id: e6887e45-a472-41d4-9620-c56fd5b72b4c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '4150'
ht-degree: 100%

---

# Rendern von Formularen als HTML {#rendering-forms-as-html}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Der Forms-Dienst rendert Formulare als HTML aufgrund einer HTTP-Anforderung eines Webbrowsers. Ein Vorteil der Wiedergabe eines Formulars als HTML besteht darin, dass der Computer, auf dem sich der Client-Webbrowser befindet, keine Adobe Reader, Acrobat oder Flash Player benötigt (für Formular-Guides (nicht mehr unterstützt)).

Um ein Formular als HTML wiederzugeben, muss der Formularentwurf als XDP-Datei gespeichert werden. Ein Formularentwurf, der als PDF-Datei gespeichert wird, kann nicht als HTML gerendert werden. Beachten Sie bei der Entwicklung eines Formularentwurfs in Designer, der als HTML wiedergegeben wird, die folgenden Kriterien:

* Verwenden Sie keine Objektbegrenzungseigenschaften, um Linien, Felder oder Raster auf dem Formular zu zeichnen. Bei einigen Browsern werden die Ränder möglicherweise nicht genau so ausgerichtet, wie sie in der Vorschau angezeigt werden. Die Objekte erscheinen eventuell übereinander oder schieben andere Objekte von ihren vorgesehenen Positionen.
* Sie können Linien, Rechtecke und Kreise verwenden, um den Hintergrund zu definieren.
* Zeichnen Sie den Text etwas größer, als es für die Unterbringung des Textes erforderlich zu sein scheint. In einigen Webbrowsern wird der Text nicht leserlich angezeigt.

>[!NOTE]
>
>Wenn ein Formular, das TIFF-Bilder enthält, mit den Methoden `(Deprecated) renderHTMLForm` und `renderHTMLForm2` des `FormServiceClient`-Objekts gerendert wird, sind die TIFF-Bilder in dem gerenderten HTML-Formular, das in den Browsern Internet Explorer oder Mozilla Firefox angezeigt wird, nicht sichtbar. Diese Browser bieten keine native Unterstützung für TIFF-Images.

## HTML-Seiten {#html-pages}

Wenn ein Formularentwurf als HTML-Formular wiedergegeben wird, wird jedes Teilformular der zweiten Ebene als HTML-Seite (Bedienfeld) wiedergegeben. Sie können die Hierarchie eines Teilformulars in Designer anzeigen. Untergeordnete Unterformulare, die zum Stammunterformular gehören (der Standardname eines Stammunterformulars ist form1), sind die Panel-Unterformulare. Das folgende Beispiel zeigt die Unterformulare eines Formularentwurfs.

```java
     form1
         Master Pages
         PanelSubform1
             NestedDynamicSubform
                 TextEdit1
         PanelSubform2
             TextEdit1
         PanelSubform3
             TextEdit1
         PanelSubform4
             TextEdit1
```

Wenn Formularentwürfe als HTML-Formulare gerendert werden, sind die Felder nicht an eine bestimmte Seitengröße gebunden. Wenn Sie dynamische Unterformulare haben, sollten diese in das Panel-Unterformular verschachtelt werden. Dynamische Unterformulare können auf eine unbegrenzte Anzahl von HTML-Seiten erweitert werden.

Wenn ein Formular als HTML-Formular gerendert wird, haben die Seitengrößen (die für paginierende Formulare, die als PDF gerendert werden, erforderlich sind) keine Bedeutung. Da sich ein Formular mit einem fließenden Layout auf eine unendliche Anzahl von HTML-Seiten ausdehnen kann, ist es wichtig, Fußzeilen auf der Hauptseite zu vermeiden. Eine Fußzeile unterhalb des Inhaltsbereichs auf einer Musterseite kann HTML-Inhalte überschreiben, die über eine Seitengrenze hinausgehen.

Sie müssen sich explizit mit den Methoden `xfa.host.pageUp` und `xfa.host.pageDown` von Bedienfeld zu Bedienfeld bewegen. Sie wechseln die Seiten, indem Sie ein Formular an den Forms-Dienst senden und der Forms-Dienst das Formular an das Client-Gerät, in der Regel einen Webbrowser, zurückgibt.

>[!NOTE]
>
>Der Prozess des Sendens eines Formulars an den Forms-Dienst und das anschließende Zurückgeben des Formulars durch den Forms-Dienst an das Client-Gerät wird als Round-Tripping von Daten an den Server bezeichnet.

>[!NOTE]
>
>Wenn Sie das Aussehen der Schaltfläche für die digitale HTML-Signatur in einem HTML-Formular anpassen möchten, müssen Sie die folgenden Eigenschaften in der Datei fscdigsig.css (innerhalb der Datei adobe-forms-ds.ear > adobe-forms-ds.war) ändern:

**.fsc-ds-ssb**: Dieses Stylesheet gilt für Felder mit Leerzeichen.

**.fsc-ds-ssv**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld.

**.fsc-ds-ssc**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld, auch wenn die Daten geändert wurden.

**.fsc-ds-ssi**: Dieses Stylesheet gilt für ungültige Zeichenfelder.

**.fsc-ds-popup-bg**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

**.fsc-ds-popup-btn**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

## Scripts ausführen {#running-scripts}

Ein Formularautor gibt an, ob ein Skript auf dem Server oder Client ausgeführt wird. Der Forms-Dienst schafft eine verteilte, ereignisverarbeitende Umgebung für die Ausführung von Formularintelligenz, die mit Hilfe des Attributs `runAt` zwischen dem Client und dem Server verteilt werden kann. Weitere Informationen zu diesem Attribut oder zum Erstellen von Skripten in Formularentwürfen finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de)

Der Forms-Dienst kann Skripten ausführen, während das Formular wiedergegeben wird. Daher können Sie ein Formular mit Daten vorab ausfüllen, indem Sie eine Verbindung zu einer Datenbank oder zu Webdiensten herstellen, die auf dem Client möglicherweise nicht verfügbar sind. Sie können auch das `Click`-Ereignis einer Schaltfläche so einstellen, dass es auf dem Server ausgeführt wird, so dass der Client die Daten an den Server weiterleitet. Dadurch kann der Client Skripte ausführen, die möglicherweise Serverressourcen benötigen, wie z. B. eine Unternehmensdatenbank, während ein Benutzer mit einem Formular interagiert. Bei HTML-Formularen können formcalc-Skripte nur auf dem Server ausgeführt werden. Daher müssen Sie diese Skripte für die Ausführung unter `server` oder `both` markieren.

Sie können Formulare entwerfen, die sich zwischen Seiten (Bedienfeldern) bewegen, indem Sie die Methoden `xfa.host.pageUp` und `xfa.host.pageDown` aufrufen. Dieses Skript wird in das `Click`-Ereignis einer Schaltfläche eingefügt und das `runAt`-Attribut wird auf `Both` gesetzt. Der Grund dafür, dass Sie `Both` wählen, ist, dass Adobe Reader oder Acrobat (für Formulare, die als PDF gerendert werden) die Seiten ändern können, ohne zum Server zu gehen, und dass HTML-Formulare die Seiten ändern können, indem sie die Daten zum Server weiterleiten. Das heißt, ein Formular wird an den Forms-Dienst gesendet, und ein Formular wird als HTML zurückgegeben, wobei die neue Seite angezeigt wird.

Es wird empfohlen, Skriptvariablen und Formularfeldern nicht dieselben Namen zu geben, wie z. B. Element. In einigen Webbrowsern wie Internet Explorer wird eine Variable möglicherweise nicht mit demselben Namen wie ein Formularfeld initialisiert, was zu einem Skriptfehler führt. Es empfiehlt sich, Formularfelder und Skriptvariablen unterschiedliche Namen zu geben.

Achten Sie beim Rendern von HTML-Formularen, die sowohl Seitennavigationsfunktionen als auch Formularskripte enthalten (z. B. wenn ein Skript Felddaten jedes Mal aus einer Datenbank abruft, wenn das Formular wiedergegeben wird) darauf, dass sich das Formularskript im form:calculate -Ereignis und nicht im form:readyevent befindet.

Formularskripte, die sich im form:ready-Ereignis befinden, werden nur einmal während der ersten Wiedergabe des Formulars ausgeführt und nicht für nachfolgende Seitenabrufe. Im Gegensatz dazu wird das form:calculate-Ereignis für jede Seitennavigation ausgeführt, in der das Formular wiedergegeben wird.

>[!NOTE]
In einem mehrseitigen Formular werden Änderungen, die von JavaScript an einer Seite vorgenommen werden, nicht beibehalten, wenn Sie zu einer anderen Seite wechseln.

Sie können benutzerdefinierte Skripte vor dem Senden eines Formulars aufrufen. Diese Funktion funktioniert in allen verfügbaren Browsern. Sie kann jedoch nur verwendet werden, wenn Benutzer das HTML-Formular wiedergeben, dessen `Output Type`-Eigenschaft auf `Form Body` gesetzt ist. Dies wird nicht funktionieren, wenn `Output Type` `Full HTML` ist. Die Schritte zur Konfiguration dieser Funktion finden Sie unter Konfigurieren von Formularen in der Administrationshilfe.

Sie müssen zunächst eine Callback-Funktion definieren, die vor dem Absenden des Formulars aufgerufen wird, wobei der Name der Funktion `_user_onsubmit` lautet. Es wird davon ausgegangen, dass die Funktion keine Ausnahme auslöst, oder falls doch, wird die Ausnahme ignoriert. Es wird empfohlen, die JavaScript-Funktion im Head-Abschnitt der HTML-Datei zu platzieren. Sie können sie jedoch auch an einer beliebigen Stelle vor dem Ende der Skript-Tags deklarieren, die `xfasubset.js` enthalten.

Wenn der Formularserver eine XDP-Datei rendert, die eine Dropdown-Liste enthält, werden neben der Erstellung der Dropdown-Liste auch zwei ausgeblendete Textfelder erstellt. Diese Textfelder speichern die Daten der Dropdown-Liste (eines speichert den Anzeigenamen der Optionen, das andere speichert den Wert für die Optionen). Daher werden jedes Mal, wenn ein Benutzer das Formular sendet, alle Daten der Dropdown-Liste gesendet. Wenn Sie nicht jedes Mal so viele Daten senden möchten, können Sie ein benutzerdefiniertes Skript schreiben, um dies zu deaktivieren. Beispiel: Der Name der Dropdown-Liste lautet `drpOrderedByStateProv` und wird in die Kopfzeile des Teilformulars eingeschlossen. Der Name des HTML-Eingabeelements lautet `header[0].drpOrderedByStateProv[0]`. Der Name der ausgeblendeten Felder, die die Daten der Dropdown-Liste speichern und senden, hat die folgenden Namen: `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

Sie können diese Eingabeelemente wie folgt deaktivieren, wenn Sie die Daten nicht posten möchten. `var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature function _user_onsubmit() { var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); elems[0].disabled = true; elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); elems[0].disabled = true; }`

```java
header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]
```

```java
var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature
    function _user_onsubmit() {
    var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]");
    elems[0].disabled = true;
    elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]");
    elems[0].disabled = true;
    }
```

## XFA-Teilmengen {#xfa-subsets}

Beim Erstellen von Formularentwürfen, die als HTML wiedergegeben werden sollen, müssen Sie die Skripterstellung auf die XFA-Untergruppe für Skripte in JavaScript beschränken.

Skripte, die auf dem Client oder sowohl auf dem Client als auch auf dem Server ausgeführt werden, müssen in die XFA-Teilmenge geschrieben werden. Skripte, die auf dem Server ausgeführt werden, können das vollständige XFA-Skriptmodell verwenden und auch FormCalc verwenden. Informationen zur Verwendung von JavaScript finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

Beim Ausführen von Skripten auf dem Client kann nur das aktuelle Bedienfeld, das angezeigt wird, das Skript verwenden. Sie können beispielsweise kein Skript für Felder erstellen, die sich im Bereich A befinden, wenn Bereich B angezeigt wird. Beim Ausführen von Skripten auf dem Server können alle Bedienfelder aufgerufen werden.

Außerdem müssen Sie bei der Verwendung von SOM-Ausdrücken (Scripting Object Model) in Skripten, die auf dem Client ausgeführt werden, vorsichtig sein. Nur eine vereinfachte Untergruppe von SOM-Ausdrücken wird von Skripten unterstützt, die auf dem Client ausgeführt werden.

## Ereigniszeitpunkt {#event-timing}

Die XFA-Teilmenge definiert die XFA-Ereignisse, die HTML-Ereignissen zugeordnet sind. Es gibt einen geringfügigen Unterschied im Verhalten hinsichtlich des Timings von calculate- und validate-Ereignissen. In einem Webbrowser wird beim Beenden eines Felds ein vollständiges calculate-Ereignis ausgeführt. Berechnete Ereignisse werden nicht automatisch ausgeführt, wenn Sie einen Feldwert ändern. Sie können ein calculate-Ereignis erzwingen, indem Sie die Methode `xfa.form.execCalculate` aufrufen.

In einem Webbrowser werden Validierungs-Ereignisse nur ausgeführt, wenn ein Feld beendet oder ein Formular gesendet wird. Sie können ein validate-Ereignis erzwingen, indem Sie die Methode `xfa.form.execValidate` verwenden.

Forms, das in einem Webbrowser angezeigt wird (im Gegensatz zu Adobe Reader oder Acrobat), entspricht dem XFA-Null-Test (Fehler oder Warnungen) für Pflichtfelder.

* Wenn der Null-Test einen Fehler erzeugt und Sie ein Feld verlassen, ohne einen Wert anzugeben, wird ein Meldungsfeld angezeigt und Sie werden nach dem Klicken auf OK zum Feld neu positioniert.
* Wenn ein Null-Test eine Warnung erzeugt und Sie ein Feld verlassen, ohne einen Wert anzugeben, werden Sie aufgefordert, entweder auf OK oder auf Abbrechen zu klicken. Dort haben Sie die Möglichkeit, den Vorgang fortzusetzen, ohne einen Wert anzugeben, oder zum Feld zurückzukehren, um einen Wert einzugeben.

Weitere Informationen zu einem Null-Test finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

## Formularschaltflächen {#form-buttons}

Wenn Sie auf eine Senden-Schaltfläche klicken, werden Formulardaten an den Forms-Dienst gesendet und stellen das Ende der Formularverarbeitung dar. Das Ereignis `preSubmit` kann auf dem Client oder dem Server ausgeführt werden. Das Ereignis `preSubmit` wird vor dem Absenden des Formulars ausgeführt, wenn es so konfiguriert ist, dass es auf dem Client ausgeführt wird. Andernfalls wird das Ereignis `preSubmit` auf dem Server während der Übermittlung des Formulars ausgeführt. Weitere Informationen zum `preSubmit`-Ereignis finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de).

Wenn einer Schaltfläche kein clientseitiges Skript zugeordnet ist, werden die Daten an den Server übermittelt, die Berechnungen werden auf dem Server durchgeführt und das HTML-Formular wird neu generiert. Wenn eine Schaltfläche ein clientseitiges Skript enthält, werden keine Daten an den Server gesendet und das clientseitige Skript wird im Webbrowser ausgeführt.

## HTML 4.0-Webbrowser {#html-4-0-web-browser}

Ein Webbrowser, der nur HTML 4.0 unterstützt, kann das clientseitige Skriptmodell der XFA-Teilmenge nicht unterstützen. Beim Erstellen eines Formularentwurfs für die Verwendung sowohl in HTML 4.0 als auch in MSDHTML oder CSS2HTML wird ein Skript, das für die Ausführung auf dem Client markiert ist, tatsächlich auf dem Server ausgeführt. Angenommen, ein Benutzer klickt auf eine Schaltfläche in einem Formular, das in einem Webbrowser mit HTML 4.0 angezeigt wird. In diesem Fall werden die Formulardaten an den Server gesendet, auf dem das clientseitige Skript ausgeführt wird.

Es wird empfohlen, die Formularlogik in calculate -Ereignissen zu platzieren, die auf dem Server in HTML 4.0 und auf dem Client für MSDHTML oder CSS2HTML ausgeführt werden.

## Änderungen in der Präsentation beibehalten {#maintaining-presentation-changes}

Wenn Sie zwischen HTML-Seiten (Bedienfeldern) wechseln, wird nur der Status der Daten beibehalten. Einstellungen wie die Hintergrundfarbe oder die obligatorischen Feldeinstellungen werden nicht beibehalten (wenn sie sich von den ursprünglichen Einstellungen unterscheiden). Um den Präsentationsstatus beizubehalten, müssen Sie Felder (normalerweise ausgeblendet) erstellen, die den Präsentationsstatus von Feldern darstellen. Wenn Sie dem `Calculate`-Ereignis eines Feldes ein Skript hinzufügen, das die Darstellung auf der Grundlage von ausgeblendeten Feldwerten ändert, können Sie den Zustand der Darstellung beibehalten, wenn Sie zwischen HTML-Seiten (Panels) hin- und herwechseln.

Das folgende Skript erhält die `fillColor` eines Feldes auf der Grundlage des Wertes von `hiddenField`. Angenommen, dieses Skript befindet sich im `Calculate`-Ereignis.

```java
     If (hiddenField.rawValue == 1)
         this.fillColor = "255,0,0"
     else
         this.fillColor = "0,255,0"
```

>[!NOTE]
Statische Objekte werden nicht in einem wiedergegebenen HTML-Formular angezeigt, wenn sie in einer Tabellenzelle verschachtelt sind. Beispielsweise werden ein in einer Tabellenzelle verschachtelter Kreis und Rechteck nicht in einem Render-HTML-Formular angezeigt. Dieselben statischen Objekte werden jedoch korrekt angezeigt, wenn sie sich außerhalb der Tabelle befinden.

## HTML-Formulare digital signieren {#digitally-signing-html-forms}

Sie können kein HTML-Formular signieren, das ein digitales Signaturfeld enthält, wenn das Formular als eine der folgenden HTML-Transformationen wiedergegeben wird:

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Informationen zum digitalen Signieren eines Dokuments finden Sie unter [Digitales Signieren und Zertifizieren von Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md)

## Rendern eines barrierefreien, richtlinienkonformen XHTML-Formulars {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

Sie können ein vollständiges HTML-Formular wiedergeben, das den Richtlinien für Barrierefreiheit entspricht. Das heißt, das Formular wird innerhalb vollständiger HTML-Tags wiedergegeben, anstatt dass das HTML-Formular innerhalb von body-Tags wiedergegeben wird (keine vollständige HTML-Seite).

## Validieren von Formulardaten {#validating-form-data}

Es wird empfohlen, die Verwendung von Validierungsregeln für Formularfelder bei der Wiedergabe des Formulars als HTML-Formular zu beschränken. Einige Validierungsregeln werden für HTML-Formulare möglicherweise nicht unterstützt. Wenn beispielsweise ein Validierungsmuster MM-TT-JJJJ auf ein `Date/Time`-Feld angewendet wird, das sich in einem Formularentwurf befindet, der als HTML-Formular wiedergegeben wird, funktioniert es nicht richtig, selbst wenn das Datum richtig eingegeben wird. Bei Formularen, die im PDF-Format dargestellt werden, funktioniert dieses Validierungsmuster jedoch ordnungsgemäß.

>[!NOTE]
Weitere Informationen über den Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

Um ein HTML-Formular wiederzugeben, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Festlegen von HTML-Laufzeitoptionen.
1. Rendern Sie ein HTML-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie Daten programmgesteuert in eine PDF formClient-API importieren können, müssen Sie einen Client für den Formulardatenintegrationsdienst erstellen. Beim Erstellen eines Service-Clients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Services erforderlich sind.

**Festlegen von HTML-Laufzeitoptionen**

Sie legen beim Rendern eines HTML-Formulars HTML-Laufzeitoptionen fest. So können Sie beispielsweise einem HTML-Formular eine Symbolleiste hinzufügen, damit die Benutzer Dateianhänge auf dem Client-Computer auswählen oder Dateianhänge abrufen können, die mit dem HTML-Formular gerendert werden. Standardmäßig ist eine HTML-Symbolleiste deaktiviert. Um einem HTML-Formular eine Symbolleiste hinzuzufügen, müssen Sie programmgesteuert Laufzeitoptionen festlegen. Standardmäßig besteht eine HTML-Symbolleiste aus den folgenden Schaltflächen:

* `Home`: Stellt einen Link zum Webstamm der Anwendung bereit.
* `Upload`: Bietet eine Benutzeroberfläche zum Auswählen von Dateien, die an das aktuelle Formular angehängt werden sollen.
* `Download`: Bietet eine Benutzeroberfläche zum Anzeigen der angehängten Dateien.

Wenn eine HTML-Symbolleiste auf einem HTML-Formular erscheint, kann ein Benutzer maximal zehn Dateien auswählen, die zusammen mit den Formulardaten übermittelt werden sollen. Nachdem die Dateien übermittelt wurden, kann der Forms-Dienst die Dateien abrufen.

Wenn Sie ein Formular als HTML wiedergeben, können Sie einen User-Agent-Wert angeben. Ein User-Agent-Wert liefert Browser- und Systeminformationen. Dies ist ein optionaler Wert, und Sie können einen leeren Zeichenfolgenwert übergeben. Die Kurzanleitung zum Rendern eines HTML-Formulars mithilfe der Java-API zeigt, wie ein Benutzeragentenwert abgerufen und zum Rendern eines Formulars als HTML verwendet wird.

HTTP-URLs, an die Formulardaten gesendet werden, können durch Festlegen der Ziel-URL mithilfe der Forms Service Client-API angegeben werden oder in der im XDP-Formularentwurf enthaltenen Senden-Schaltfläche angegeben werden. Wenn die Ziel-URL im Formularentwurf angegeben ist, legen Sie einen Wert nicht mithilfe der Forms Service Client-API fest.

>[!NOTE]
Das Rendern eines HTML-Formulars mit einer Symbolleiste ist optional.

>[!NOTE]
Wenn Sie ein AHTML-Formular rendern, wird empfohlen, keine Symbolleiste zum Formular hinzuzufügen.

**Rendern eines HTML-Formulars**

Um ein HTML-Formular zu rendern, müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Transformationstyp auswählen. Sie können beispielsweise den HTML-Transformationstyp angeben, der dynamische HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben des Formulardaten-Streams in den Client-Webbrowser**

Wenn der Forms-Service ein HTML-Formular rendert, wird ein Formulardaten-Stream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Nach dem Schreiben in den Client-Webbrowser ist das HTML-Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe eines Formulars als HTML mithilfe der Java-API](#render-a-form-as-html-using-the-java-api)

[Wiedergabe eines Formulars als HTML mithilfe der Webservice-API](#render-a-form-as-html-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von HTML-Formularen mit benutzerdefinierten Symbolleisten](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

## Wiedergabe eines Formulars als HTML mithilfe der Java-API {#render-a-form-as-html-using-the-java-api}

So rendern Sie ein HTML-Formular mithilfe der Forms-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Um ein HTML-Formular mit einer Symbolleiste zu rendern, rufen Sie die Methode `setHTMLToolbar` des `HTMLRenderSpec`-Objekts auf und übergeben einen `HTMLToolbar`-Auflistungswert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die Methode `setLocale` des `HTMLRenderSpec`-Objekts auf und übergeben einen Zeichenfolgenwert, der den Wert des Gebietsschemas angibt. (Diese Einstellung ist optional.)
   * Um das HTML-Formular innerhalb vollständiger HTML-Tags zu rendern, rufen Sie die Methode `setOutputType` des `HTMLRenderSpec`-Objekts auf und übergeben `OutputType.FullHTMLTags`. (Diese Einstellung ist optional.)

   >[!NOTE]
   Formulare werden nicht erfolgreich in HTML gerendert, wenn die Option `StandAlone` `true` ist und `ApplicationWebRoot` auf einen anderen Server als den J2EE-Programm-Server verweist, auf dem AEM Forms gehostet wird (der Wert von `ApplicationWebRoot` wird mithilfe des `URLSpec`-Objekts angegeben, das an die Methode `FormsServiceClient` des `(Deprecated) renderHTMLForm`-Objekts übergeben wird). Wenn die `ApplicationWebRoot` ein anderer Server ist, der als Host für AEM Forms dient, muss der URI-Wert des Web-Stamms in der Administration Console als URI-Wert für das Web-Programm des Formulars festgelegt werden. Dazu können Sie sich bei Administration Console anmelden, auf „Services“ > „Forms“ klicken und den URI des Web-Stamms auf https://server-name:port/FormServer setzen. Speichern Sie dann Ihre Einstellungen.

1. Rendern Sie ein HTML-Formular

   Rufen Sie die Methode `(Deprecated) renderHTMLForm` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Auflistungswert, der den Präferenztyp für HTML angibt. Um beispielsweise ein HTML-Formular zu rendern, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `(Deprecated) renderHTMLForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die Methode `getInputStream` des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardaten-Stream, indem Sie die Methode `read` des `InputStream`-Objekts aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die Methode `write` des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen als HTML](#rendering-forms-as-html)

[Kurzanleitung (SOAP-Modus): Rendern eines HTML-Formulars mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Wiedergabe eines Formulars als HTML mithilfe der Webservice-API {#render-a-form-as-html-using-the-web-service-api}

So rendern Sie ein HTML-Formular mithilfe der Forms-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Um ein HTML-Formular mit einer Symbolleiste zu rendern, rufen Sie die Methode `setHTMLToolbar` des `HTMLRenderSpec`-Objekts auf und übergeben einen `HTMLToolbar`-Auflistungswert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die Methode `setLocale` des `HTMLRenderSpec`-Objekts auf und übergeben einen Zeichenfolgenwert, der den Wert des Gebietsschemas angibt. Weitere Informationen finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Um das HTML-Formular innerhalb vollständiger HTML-Tags zu rendern, rufen Sie die Methode `setOutputType` des `HTMLRenderSpec`-Objekts auf und übergeben `OutputType.FullHTMLTags`.

   >[!NOTE]
   Formulare werden nicht erfolgreich in HTML gerendert, wenn die Option `StandAlone` `true` ist und `ApplicationWebRoot` auf einen anderen Server als den J2EE-Programm-Server verweist, auf dem AEM Forms gehostet wird (der Wert von `ApplicationWebRoot` wird mithilfe des `URLSpec`-Objekts angegeben, das an die Methode `(Deprecated) renderHTMLForm` des `FormsServiceClient`-Objekts übergeben wird). Wenn es sich bei `ApplicationWebRoot` um einen anderen Server als den handelt, auf dem AEM Forms gehostet wird, muss der der URI-Wert des Web-Stamms in der Administration Console als URI-Wert für das Web-Programm des Formulars festgelegt werden. Dazu können Sie sich bei Administration Console anmelden, auf „Services“ > „Forms“ klicken und den URI des Web-Stamms auf https://server-name:port/FormServer setzen. Speichern Sie dann Ihre Einstellungen.

1. Rendern Sie ein HTML-Formular

   Rufen Sie die Methode `(Deprecated) renderHTMLForm` des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Auflistungswert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular zu rendern, das mit Dynamic HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Formularen mit fließfähigen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Wert der `HTTP_USER_AGENT`-Kopfzeile angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * Ein `URLSpec`-Objekt, das die zum Rendern eines HTML-Formulars erforderlichen URI-Werte speichert. (Siehe [Angeben von URI-Werten](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * Ein `java.util.HashMap`-Objekt, das Dateianhänge speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten. (Siehe [Anhängen von Dateien an das Formular](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode ausgefüllt wird. Dieser Parameterwert speichert das gerenderte Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode ausgefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das von der Methode ausgefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode ausgefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode ausgefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die Methode `(Deprecated) renderHTMLForm` füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardaten-Stream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des Datenelements `value` des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Inhaltstyp des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Stream in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Rendern von Formularen als HTML](#rendering-forms-as-html)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
