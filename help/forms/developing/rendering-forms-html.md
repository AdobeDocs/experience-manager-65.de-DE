---
title: Rendern von Forms als HTML
seo-title: Rendern von Forms als HTML
description: Verwenden Sie den Forms-Dienst, um Formulare als HTML-Antwort auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können die Java-API und die Web-Service-API verwenden, um Formulare als HTML wiederzugeben.
seo-description: Verwenden Sie den Forms-Dienst, um Formulare als HTML-Antwort auf eine HTTP-Anforderung eines Webbrowsers wiederzugeben. Sie können die Java-API und die Web-Service-API verwenden, um Formulare als HTML wiederzugeben.
uuid: bd8edb6f-333b-4ceb-9877-618f5377f56f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 669ede46-ea55-444b-a23f-23a86e5aff8e
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '4188'
ht-degree: 1%

---


# Rendern von Forms als HTML {#rendering-forms-as-html}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

Der Forms-Dienst rendert Formulare als HTML, wenn ein Webbrowser eine HTTP-Anforderung sendet. Ein Vorteil der Wiedergabe eines Formulars im HTML-Format besteht darin, dass auf dem Computer, auf dem sich der Client-Webbrowser befindet, kein Adobe Reader, Acrobat oder Flash Player erforderlich ist (bei Formularleitfäden (nicht mehr unterstützt).

Um ein Formular als HTML wiederzugeben, muss der Formularentwurf als XDP-Datei gespeichert werden. Ein Formularentwurf, der als PDF-Datei gespeichert wird, kann nicht als HTML wiedergegeben werden. Berücksichtigen Sie beim Entwickeln eines Formularentwurfs in Designer, der als HTML wiedergegeben wird, die folgenden Kriterien:

* Verwenden Sie keine Objektbegrenzungseigenschaften, um Linien, Felder oder Raster auf dem Formular zu zeichnen. Bei einigen Browsern werden die Ränder möglicherweise nicht genau so angeordnet, wie sie in einer Vorschau angezeigt werden. Die Objekte erscheinen eventuell übereinander oder schieben andere Objekte von ihren vorgesehenen Positionen.
* Sie können Linien, Rechtecke und Kreise verwenden, um den Hintergrund zu definieren.
* Zeichnen Sie den Text etwas größer, als es für die Aufnahme des Textes erforderlich scheint. In einigen Webbrowsern wird der Text nicht leserlich angezeigt.

>[!NOTE]
>
>Beim Rendern eines Formulars, das TIFF-Bilder enthält, mit den Methoden `FormServiceClient` und `(Deprecated) renderHTMLForm` des Objekts sind die TIFF-Bilder nicht im gerenderten HTML-Formular sichtbar, das in Internet Explorer oder Mozilla Firefox angezeigt wird. `renderHTMLForm2` Diese Browser bieten keine native Unterstützung für TIFF-Bilder.

## HTML-Seiten {#html-pages}

Wenn ein Formularentwurf als HTML-Formular wiedergegeben wird, wird jedes Teilformular der zweiten Ebene als HTML-Seite (Bedienfeld) wiedergegeben. Die Hierarchie eines Teilformulars kann in Designer Ansicht werden. Untergeordnete Teilformulare, die zum Stammteilformular gehören (der Standardname eines Stammteilformulars ist form1), sind die Teilformulare des Bedienfelds. Das folgende Beispiel zeigt die Teilformulare eines Formularentwurfs.

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

Wenn Formularentwürfe als HTML-Formulare wiedergegeben werden, sind die Bedienfelder nicht auf ein bestimmtes Seitenformat beschränkt. Wenn Sie dynamische Teilformulare haben, sollten diese innerhalb des Teilformulars des Bereichs verschachtelt sein. Dynamische Teilformulare können auf unendliche HTML-Seiten erweitert werden.

Wenn ein Formular als HTML-Formular wiedergegeben wird, haben Seitengrößen (erforderlich für die Paginierung von Formularen, die als PDF wiedergegeben werden) keine Bedeutung. Da ein Formular mit flexiblem Layout auf unendliche HTML-Seiten erweitert werden kann, ist es wichtig, Fußzeilen auf der Seite Übergeordnet zu vermeiden. Eine Fußzeile unter dem Inhaltsbereich auf einer Übergeordnet angezeigten Seite kann HTML-Inhalte überschreiben, die über eine Seitenbegrenzung hinausfließen.

Mit den Methoden `xfa.host.pageUp` und `xfa.host.pageDown` müssen Sie explizit zwischen den Bereichen wechseln. Sie ändern die Seiten, indem Sie ein Formular an den Forms-Dienst senden und den Forms-Dienst das Formular wieder auf dem Client-Gerät wiedergeben, normalerweise in einem Webbrowser.

>[!NOTE]
>
>Der Vorgang, bei dem ein Formular an den Forms-Dienst gesendet und dann der Forms-Dienst das Formular wieder an das Client-Gerät zurückgibt, wird als Rundflugdaten an den Server bezeichnet.

>[!NOTE]
>
>Wenn Sie das Erscheinungsbild der Schaltfläche &quot;Digitale HTML-Signatur&quot;in einem HTML-Formular anpassen möchten, müssen Sie die folgenden Eigenschaften in der Datei &quot;fscdigsig.css&quot;ändern (innerhalb der Datei &quot;adobe-forms-ds.ear&quot;> &quot;adobe-forms-ds.war&quot;):

**.fsc-ds-ssb**: Dieses Stylesheet gilt für ein leeres Zeichenfeld.

**.fsc-ds-ssv**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld.

**.fsc-ds-ssc**: Dieses Stylesheet gilt für ein gültiges Zeichenfeld, aber die Daten wurden geändert.

**.fsc-ds-ssi**: Dieses Stylesheet gilt für ungültige Zeichenfelder.

**.fsc-ds-popup-bg**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

**.fsc-ds-popup-btn**: Diese Stylesheet-Eigenschaft wird nicht verwendet.

## Ausführen von Skripten {#running-scripts}

Ein Formularersteller gibt an, ob ein Skript auf dem Server oder auf dem Client ausgeführt wird. Der Forms-Dienst erstellt eine verteilte Umgebung zur Verarbeitung von Ereignissen zur Ausführung von Formularintelligenz, die mithilfe des Attributs `runAt` zwischen Client und Server verteilt werden kann. Weitere Informationen zu diesem Attribut oder zum Erstellen von Skripten in Formularentwürfen finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Der Forms-Dienst kann Skripten ausführen, während das Formular wiedergegeben wird. Daher können Sie ein Formular mit Daten vorab ausfüllen, indem Sie eine Verbindung zu einer Datenbank oder zu Webdiensten herstellen, die möglicherweise nicht auf dem Client verfügbar sind. Sie können auch das `Click`-Ereignis einer Schaltfläche so festlegen, dass es auf dem Server ausgeführt wird, sodass der Client Daten auf den Server umgerundet. Dadurch kann der Client Skripten ausführen, die möglicherweise Serverressourcen erfordern, wie z. B. eine Unternehmensdatenbank, während ein Benutzer mit einem Formular interagiert. Bei HTML-Formularen können formcalc-Skripten nur auf dem Server ausgeführt werden. Daher müssen Sie diese Skripten markieren, um unter `server` oder `both` ausgeführt zu werden.

Sie können Formulare entwerfen, die zwischen Seiten (Bedienfeldern) wechseln, indem Sie die Methoden `xfa.host.pageUp` und `xfa.host.pageDown` aufrufen. Dieses Skript wird im Ereignis `Click` einer Schaltfläche platziert und das Attribut `runAt` ist auf `Both` eingestellt. Der Grund, warum Sie &quot;`Both`&quot;wählen, ist, dass Adobe Reader oder Acrobat (für Formulare, die als PDF wiedergegeben werden) Seiten ändern können, ohne zum Server wechseln zu müssen, und dass HTML-Formulare Seiten ändern können, indem Daten auf den Server gerundet werden. Das heißt, ein Formular wird an den Forms-Dienst gesendet und ein Formular wird als HTML wiedergegeben, wobei die neue Seite angezeigt wird.

Es wird empfohlen, Skriptvariablen und Formularfeldern nicht dieselben Namen wie Element zuzuweisen. In einigen Webbrowsern, wie z. B. Internet Explorer, wird eine Variable möglicherweise nicht mit demselben Namen wie ein Formularfeld initialisiert, was zu einem Skriptfehler führt. Es empfiehlt sich, Formularfeldern und Skriptvariablen unterschiedliche Namen zuzuweisen.

Beim Rendern von HTML-Formularen, die sowohl Seitennavigationsfunktionen als auch Formularskripte enthalten (z. B. wenn ein Skript Felddaten jedes Mal aus einer Datenbank abruft, wenn das Formular wiedergegeben wird), stellen Sie sicher, dass sich das Formularskript im Ereignis form:calculate anstelle von form:readyevent befindet.

Formularskripte, die sich im Ereignis form:ready befinden, werden nur einmal während der anfänglichen Wiedergabe des Formulars ausgeführt und nicht für nachfolgende Seitenabrufe ausgeführt. Im Gegensatz dazu wird das form:calculate-Ereignis für jede Seitennavigation ausgeführt, bei der das Formular wiedergegeben wird.

>[!NOTE]
Auf einem mehrseitigen Formular werden Änderungen, die von JavaScript an einer Seite vorgenommen wurden, nicht beibehalten, wenn Sie zu einer anderen Seite wechseln.

Sie können benutzerdefinierte Skripten aufrufen, bevor Sie ein Formular senden. Diese Funktion funktioniert in allen verfügbaren Browsern. Sie kann jedoch nur verwendet werden, wenn Benutzer das HTML-Formular wiedergeben, für das die `Output Type`-Eigenschaft auf `Form Body` eingestellt ist. Es funktioniert nicht, wenn `Output Type` `Full HTML` ist. Anweisungen zum Konfigurieren dieser Funktion finden Sie in der Administration-Hilfe unter Konfigurieren von Formularen.

Sie müssen zuerst eine Rückruffunktion definieren, die vor dem Senden des Formulars aufgerufen wird, wobei der Name der Funktion `_user_onsubmit` lautet. Es wird davon ausgegangen, dass die Funktion keine Ausnahme auslöst, oder wenn dies der Fall ist, wird die Ausnahme ignoriert. Es wird empfohlen, die JavaScript-Funktion im Kopfabschnitt des HTML-Dokuments zu platzieren. Sie können es jedoch an einer beliebigen Stelle vor dem Ende der Skript-Tags deklarieren, die `xfasubset.js` enthalten.

Wenn der Formularserver eine XDP-Datei wiedergibt, die eine Dropdown-Liste enthält, erstellt er neben der Erstellung der Dropdown-Liste auch zwei unsichtbare Textfelder. Diese Textfelder speichern die Daten der Dropdown-Liste (einer speichert den Anzeigenamen der Optionen und andere speichert den Wert der Optionen). Daher werden bei jedem Senden des Formulars durch den Benutzer alle Daten der Dropdown-Liste gesendet. Wenn Sie nicht immer so viele Daten senden möchten, können Sie ein benutzerdefiniertes Skript schreiben, um dies zu deaktivieren. Beispiel: Der Name der Dropdown-Liste ist `drpOrderedByStateProv` und wird in die Teilformular-Kopfzeile eingeschlossen. Der Name des HTML-Eingabeelements ist `header[0].drpOrderedByStateProv[0]`. Der Name der verborgenen Felder, in denen die Daten des Dropdown-Menüs gespeichert und gesendet werden, hat folgende Namen: `header[0].drpOrderedByStateProv_DISPLAYITEMS_[0] header[0].drpOrderedByStateProv_VALUEITEMS_[0]`

Sie können diese Eingabefelder wie folgt deaktivieren, wenn Sie die Daten nicht veröffentlichen möchten. `var __CUSTOM_SCRIPTS_VERSION = 1; //enabling the feature function _user_onsubmit() { var elems = document.getElementsByName("header[0].drpOrderedByStateProv_DISPLAYITEMS_[0]"); elems[0].disabled = true; elems = document.getElementsByName("header[0].drpOrderedByStateProv_VALUEITEMS_[0]"); elems[0].disabled = true; }`

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

## XFA-Untergruppen {#xfa-subsets}

Beim Erstellen von Formularentwürfen zur Wiedergabe als HTML müssen Sie die Skripterstellung auf die XFA-Untergruppe für Skripten in JavaScript beschränken.

Skripten, die auf dem Client ausgeführt werden oder sowohl auf dem Client als auch auf dem Server ausgeführt werden, müssen in die XFA-Untergruppe geschrieben werden. Skripten, die auf dem Server ausgeführt werden, können das vollständige XFA-Skriptmodell verwenden und auch FormCalc verwenden. Informationen zur Verwendung von JavaScript finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Beim Ausführen von Skripten auf dem Client kann nur das aktuelle Bedienfeld, das angezeigt wird, Skript verwenden. Sie können beispielsweise keine Skripten für Felder erstellen, die sich im Bereich A befinden, wenn Bereich B angezeigt wird. Beim Ausführen von Skripten auf dem Server können alle Bedienfelder aufgerufen werden.

Vorsicht ist auch geboten, wenn Sie SOM-Ausdruck (Scripting Object Model) in Skripten verwenden, die auf dem Client ausgeführt werden. Nur eine vereinfachte Untergruppe von SOM-Ausdrücken wird von Skripten unterstützt, die auf dem Client ausgeführt werden.

## Ereignis-Timing {#event-timing}

Die XFA-Untergruppe definiert die XFA-Ereignis, die HTML-Ereignissen zugeordnet werden. Es gibt einen geringfügigen Unterschied im Verhalten beim Timing von Ereignissen zur Berechnung und Validierung. In einem Webbrowser wird beim Beenden eines Felds ein Ereignis zur vollständigen Berechnung ausgeführt. Berechnete Ereignis werden nicht automatisch ausgeführt, wenn Sie eine Änderung an einem Feldwert vornehmen. Sie können ein calculate-Ereignis erzwingen, indem Sie die `xfa.form.execCalculate`-Methode aufrufen.

In einem Webbrowser werden validate-Ereignis nur ausgeführt, wenn ein Feld verlassen oder ein Formular gesendet wird. Sie können ein validate-Ereignis mithilfe der `xfa.form.execValidate`-Methode erzwingen.

Forms, das in einem Webbrowser angezeigt wird (im Gegensatz zu Adobe Reader oder Acrobat), entspricht dem XFA-Null-Test (Fehler oder Warnungen) für Pflichtfelder.

* Wenn der Null-Test einen Fehler auslöst und Sie ein Feld verlassen, ohne einen Wert anzugeben, wird ein Meldungsfeld angezeigt und Sie werden nach dem Klicken auf OK erneut in das Feld positioniert.
* Wenn ein Null-Test eine Warnung auslöst und Sie ein Feld verlassen, ohne einen Wert anzugeben, werden Sie aufgefordert, entweder auf &quot;OK&quot;oder auf &quot;Abbrechen&quot;zu klicken, damit Sie fortfahren können, ohne einen Wert anzugeben, oder zum Feld zurückkehren, um einen Wert einzugeben.

Weitere Informationen zu einem Null-Test finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Formularschaltflächen {#form-buttons}

Durch Klicken auf eine Senden-Schaltfläche werden Formulardaten an den Forms-Dienst gesendet und das Ende der Formularverarbeitung markiert. Das Ereignis `preSubmit` kann so eingestellt werden, dass es auf dem Client oder Server ausgeführt wird. Das Ereignis `preSubmit` wird vor der Formularübermittlung ausgeführt, wenn es für die Ausführung auf dem Client konfiguriert ist. Andernfalls wird das Ereignis `preSubmit` während der Formularübermittlung auf dem Server ausgeführt. Weitere Informationen zum Ereignis `preSubmit` finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

Wenn einer Schaltfläche kein clientseitiges Skript zugeordnet ist, werden Daten an den Server gesendet, Berechnungen auf dem Server durchgeführt und das HTML-Formular neu generiert. Wenn eine Schaltfläche ein clientseitiges Skript enthält, werden keine Daten an den Server gesendet und das clientseitige Skript wird im Webbrowser ausgeführt.

## HTML 4.0 Webbrowser {#html-4-0-web-browser}

Ein Webbrowser, der nur HTML 4.0 unterstützt, kann das clientseitige XFA-Skriptmodell der Untergruppe nicht unterstützen. Beim Erstellen eines Formularentwurfs, der sowohl in HTML 4.0 als auch in MSDHTML oder CSS2HTML ausgeführt werden soll, wird ein Skript, das für die Ausführung auf dem Client markiert ist, tatsächlich auf dem Server ausgeführt. Angenommen, ein Benutzer klickt auf eine Schaltfläche in einem Formular, das in einem HTML 4.0-Webbrowser angezeigt wird. In diesem Fall werden die Formulardaten an den Server gesendet, auf dem das clientseitige Skript ausgeführt wird.

Es wird empfohlen, die Formularlogik in calculate-Ereignis einzufügen, die auf dem Server in HTML 4.0 und auf dem Client für MSDHTML oder CSS2HTML ausgeführt werden.

## Beibehalten von Präsentationsänderungen {#maintaining-presentation-changes}

Beim Wechsel zwischen HTML-Seiten (Bedienfeldern) wird nur der Status der Daten beibehalten. Einstellungen wie die Hintergrundfarbe oder obligatorische Feldeinstellungen werden nicht beibehalten (sofern diese von den ursprünglichen Einstellungen abweichen). Um den Präsentationsstatus beizubehalten, müssen Sie Felder erstellen, die den Präsentationsstatus der Felder darstellen (normalerweise ausgeblendet). Wenn Sie dem Ereignis `Calculate` eines Felds ein Skript hinzufügen, das die Darstellung basierend auf ausgeblendeten Feldwerten ändert, können Sie den Präsentationsstatus beibehalten, während Sie zwischen HTML-Seiten (Bedienfeldern) hin- und herwechseln.

Das folgende Skript behält das `fillColor` eines Felds auf der Grundlage des Werts von `hiddenField` bei. Angenommen, dieses Skript befindet sich im Ereignis `Calculate` eines Felds.

```java
     If (hiddenField.rawValue == 1)
         this.fillColor = "255,0,0"
     else
         this.fillColor = "0,255,0"
```

>[!NOTE]
Statische Objekte werden nicht in einem gerenderten HTML-Formular angezeigt, wenn sie in einer Tabellenzelle verschachtelt sind. Beispielsweise werden in einer Tabellenzelle verschachtelte Kreise und Rechtecke nicht in einem Render-HTML-Formular angezeigt. Diese statischen Objekte werden jedoch korrekt angezeigt, wenn sie sich außerhalb der Tabelle befinden.

## Digitales Signieren von HTML-Formularen {#digitally-signing-html-forms}

Sie können kein HTML-Formular mit einem digitalen Unterschriftsfeld signieren, wenn das Formular als eine der folgenden HTML-Transformationen wiedergegeben wird:

* AHTML
* HTML4
* StaticHTML
* NoScriptXHTML

Weitere Informationen zum digitalen Signieren eines Dokuments finden Sie unter [Digitales Signieren und Zertifizieren von Dokumenten](/help/forms/developing/digitally-signing-certifying-documents.md)

## Rendern eines barrierefreien, nach Richtlinien kompatiblen XHTML-Formulars {#rendering-an-accessibility-guidelines-compliant-xhtml-form}

Sie können ein vollständiges HTML-Formular wiedergeben, das den Richtlinien für Barrierefreiheit entspricht. Das heißt, das Formular wird in vollständigen HTML-Tags wiedergegeben, nicht in HTML-Formularen, die in body-Tags wiedergegeben werden (nicht in einer vollständigen HTML-Seite).

## Validieren von Formulardaten {#validating-form-data}

Es wird empfohlen, die Verwendung von Validierungsregeln für Formularfelder bei der Wiedergabe des Formulars als HTML-Formular einzuschränken. Einige Validierungsregeln werden für HTML-Formulare möglicherweise nicht unterstützt. Wenn beispielsweise ein Überprüfungsmuster vom Typ MM-TT-JJJJ auf ein `Date/Time`-Feld angewendet wird, das sich in einem Formularentwurf befindet, der als HTML-Formular wiedergegeben wird, funktioniert es nicht ordnungsgemäß, auch wenn das Datum korrekt eingegeben wurde. Dieses Überprüfungsmuster funktioniert jedoch ordnungsgemäß für Formulare, die als PDF wiedergegeben werden.

>[!NOTE]
Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein HTML-Formular:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Legen Sie HTML-Laufzeitoptionen fest.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie Daten programmgesteuert in eine PDF formClient-API importieren können, müssen Sie einen Client des Formulardatenintegrationsdienstes erstellen. Beim Erstellen eines Dienstclients definieren Sie Verbindungseinstellungen, die zum Aufrufen eines Dienstes erforderlich sind.

**Festlegen von HTML-Laufzeitoptionen**

Beim Rendern eines HTML-Formulars legen Sie HTML-Laufzeitoptionen fest. Sie können beispielsweise eine Symbolleiste zu einem HTML-Formular hinzufügen, um Benutzern zu ermöglichen, Dateianlagen auf dem Clientcomputer auszuwählen oder Dateianlagen abzurufen, die mit dem HTML-Formular wiedergegeben werden. Standardmäßig ist eine HTML-Symbolleiste deaktiviert. Um einem HTML-Formular eine Symbolleiste hinzuzufügen, müssen Sie programmgesteuert Laufzeitoptionen festlegen. Standardmäßig besteht eine HTML-Symbolleiste aus den folgenden Schaltflächen:

* `Home`: Stellt eine Verknüpfung zum Webstamm der Anwendung bereit.
* `Upload`: Stellt eine Benutzeroberfläche zur Auswahl der Dateien bereit, die an das aktuelle Formular angehängt werden sollen.
* `Download`: Stellt eine Benutzeroberfläche zum Anzeigen der angehängten Dateien bereit.

Wenn eine HTML-Symbolleiste in einem HTML-Formular angezeigt wird, kann ein Benutzer maximal zehn Dateien auswählen, die zusammen mit Formulardaten gesendet werden sollen. Sobald die Dateien übermittelt wurden, kann der Forms-Dienst die Dateien abrufen.

Bei der Wiedergabe eines Formulars als HTML können Sie einen Wert für den Benutzeragenten angeben. Ein Benutzeragenten-Wert enthält Browser- und Systeminformationen. Dies ist ein optionaler Wert, und Sie können einen leeren Zeichenfolgenwert übergeben. Der Beginn &quot;Wiedergabe eines HTML-Formulars mit dem Java-API-Schnellbefehl&quot;zeigt, wie ein Benutzeragentenwert abgerufen und verwendet wird, um ein Formular als HTML wiederzugeben.

HTTP-URLs, an die Formulardaten gesendet werden, können durch Festlegen der Zielgruppen-URL mithilfe der Forms Service Client-API angegeben werden oder in der Senden-Schaltfläche im XDP-Formularentwurf angegeben werden. Wenn die Zielgruppen-URL im Formularentwurf angegeben ist, legen Sie keinen Wert mit der Forms Service Client-API fest.

>[!NOTE]
Die Wiedergabe eines HTML-Formulars mit einer Symbolleiste ist optional.

>[!NOTE]
Wenn Sie ein AHTML-Formular wiedergeben, sollten Sie dem Formular keine Symbolleiste hinzufügen.

**HTML-Formular wiedergeben**

Zur Wiedergabe eines HTML-Formulars müssen Sie einen Formularentwurf angeben, der in Designer erstellt und als XDP-Datei gespeichert wurde. Sie müssen auch einen HTML-Konvertierungstyp auswählen. Sie können beispielsweise den HTML-Umwandlungstyp angeben, der ein dynamisches HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte, die zum Rendern anderer Formulartypen erforderlich sind.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie an den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das HTML-Formular für den Benutzer sichtbar.

**Siehe auch**

[Formular mit der Java-API als HTML wiedergeben](#render-a-form-as-html-using-the-java-api)

[Formular mit der Webdienst-API als HTML wiedergeben](#render-a-form-as-html-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von HTML Forms mit benutzerdefinierten Symbolleisten](/help/forms/developing/rendering-html-forms-custom-toolbars.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formular mit der Java-API {#render-a-form-as-html-using-the-java-api} als HTML wiedergeben

Wiedergabe eines HTML-Formulars mit der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec`-Methode des Objekts `setHTMLToolbar` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die `setLocale`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Gebietsschemawert angibt. `HTMLRenderSpec` (Dies ist eine optionale Einstellung.)
   * Um das HTML-Formular mit vollständigen HTML-Tags wiederzugeben, rufen Sie die `setOutputType`-Methode des Objekts auf und übergeben Sie `OutputType.FullHTMLTags`. `HTMLRenderSpec` (Dies ist eine optionale Einstellung.)

   >[!NOTE]
   Forms wird nicht erfolgreich in HTML wiedergegeben, wenn die `StandAlone`-Option `true` lautet und `ApplicationWebRoot` auf einen anderen Server als den J2EE-Anwendungsserver verweist, der AEM Forms hostet (der `ApplicationWebRoot`-Wert wird mit dem `URLSpec`-Objekt angegeben, das an die `FormsServiceClient`-Objektmethode `(Deprecated) renderHTMLForm` übergeben wird). Wenn `ApplicationWebRoot` ein anderer Server des Hosts AEM Forms ist, muss der Wert des Webstamm-URI in Administration Console als URI-Wert der Webanwendung des Formulars festgelegt werden. Dazu müssen Sie sich bei Administration Console anmelden, auf &quot;Dienste&quot;> &quot;Forms&quot;klicken und den Webstamm-URI auf &quot;https://server-name:port/FormServer&quot;setzen. Speichern Sie dann Ihre Einstellungen.

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt; zum Beispiel `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `(Deprecated) renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden kann.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms als HTML](#rendering-forms-as-html)

[Quick Beginn (SOAP-Modus): Wiedergabe eines HTML-Formulars mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formular mit der Webdienst-API {#render-a-form-as-html-using-the-web-service-api} als HTML wiedergeben

Wiedergabe eines HTML-Formulars mit der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Festlegen von HTML-Laufzeitoptionen

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec`-Methode des Objekts `setHTMLToolbar` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Um den Gebietsschemawert für das HTML-Formular festzulegen, rufen Sie die `setLocale`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Gebietsschemawert angibt. `HTMLRenderSpec` Weitere Informationen finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Um das HTML-Formular mit vollständigen HTML-Tags wiederzugeben, rufen Sie die `setOutputType`-Methode des Objekts auf und übergeben Sie `OutputType.FullHTMLTags`.`HTMLRenderSpec`

   >[!NOTE]
   Forms wird nicht erfolgreich in HTML wiedergegeben, wenn die `StandAlone`-Option `true` lautet und `ApplicationWebRoot` auf einen anderen Server als den J2EE-Anwendungsserver verweist, der AEM Forms hostet (der `ApplicationWebRoot`-Wert wird mit dem `URLSpec`-Objekt angegeben, das an die `FormsServiceClient`-Objektmethode `(Deprecated) renderHTMLForm` übergeben wird). Wenn `ApplicationWebRoot` ein anderer Server des Hosts AEM Forms ist, muss der Wert des Webstamm-URI in Administration Console als URI-Wert der Webanwendung des Formulars festgelegt werden. Dazu müssen Sie sich bei Administration Console anmelden, auf &quot;Dienste&quot;> &quot;Forms&quot;klicken und den Webstamm-URI auf &quot;https://server-name:port/FormServer&quot;setzen. Speichern Sie dann Ihre Einstellungen.

1. HTML-Formular wiedergeben

   Rufen Sie die `(Deprecated) renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`. (Siehe [Vorausfüllen von Forms mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md#prepopulating-forms-with-flowable-layouts).)
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt; zum Beispiel `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Sie können eine leere Zeichenfolge übergeben, wenn Sie diesen Wert nicht festlegen möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind. (Siehe [Geben Sie URI-Werte](/help/forms/developing/rendering-interactive-pdf-forms.md) an.)
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten. (Siehe [Anhängen von Dateien an das Formular](/help/forms/developing/rendering-interactive-pdf-forms.md).)
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Renderwert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `(Deprecated) renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms als HTML](#rendering-forms-as-html)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

