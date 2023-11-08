---
title: Häufig gestellte Fragen (FAQ) für HTML5-Formulare
seo-title: Frequently asked questions (FAQ) for HTML5 forms
description: Häufig gestellte Fragen (FAQ) zu Layout, Skriptunterstützung und dem Umfang von HTML5-Formularen.
seo-description: Frequently Asked Questions (FAQ) about layout, scripting support, and scope of HTML5 forms.
uuid: 398e31de-3e46-4288-b3cd-39d51fa17abc
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 4b676e7e-191f-4a19-8b8f-fc3e30244b59
docset: aem65
feature: Mobile Forms
exl-id: 85c9315e-1bc8-44a9-937e-af6fc7cf54d1
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '2005'
ht-degree: 63%

---


# Häufig gestellte Fragen (FAQ) für HTML5-Formulare{#frequently-asked-questions-faq-for-html-forms}

Es gibt einige häufig gestellte Fragen (FAQ) zu Layout, Skriptunterstützung und dem Umfang von HTML5-Formularen.

## Layout {#layout}

1. Warum werden Barcodes und das Unterschriftsfeld in meinem Formular nicht angezeigt?

   Antwort: Barcodes und Unterschriftsfelder sind in HTML- oder Mobilgerät-Szenarien nicht wichtig. Diese Felder erscheinen als nicht interaktiver Bereich. AEM Forms Designer bietet allerdings ein neues Scribble-Unterschriftsfeld, das anstelle des Unterschriftsfeldes verwendet werden kann. Sie können auch ein [benutzerdefiniertes Widget](../../forms/using/custom-widgets.md) für Barcodes hinzufügen und integrieren.

1. Wird Rich Text für das XFA-Textfeld unterstützt?

   Antwort: Das XFA-Feld, das umfangreiche Inhalte in AEM Forms Designer zulässt, wird nicht unterstützt, sondern als normaler Text dargestellt, der nicht über die Benutzeroberfläche formatiert werden kann. Außerdem werden XFA-Felder mit Kombinationseigenschaft als normales Feld angezeigt, auch wenn die Anzahl der zulässigen Zeichen basierend auf dem Wert der Kombinationszahlen immer noch eingeschränkt ist.

1. Gibt es Einschränkungen bei der Verwendung wiederholbarer Teilformulare?

   Antwort: Wiederholbare Teilformulare sollten eine Anfangszahl von 1 oder mehr haben. Wiederholbare Teilformulare mit einer Anfangszahl von null werden nicht unterstützt. Sie können auch ein wiederholbares Teilformular verwenden und es beim Laden des Formulars nicht anzeigen. Um den Anwendungsfall zu erreichen: 

   1. Legen Sie die Anfangszahl des wiederholbaren Teilformulars auf 1 fest.

      ![intial-count](assets/intial-count.png)

   1. Verwenden Sie das initialize-Ereignis des Formulars, um die primäre Instanz des Teilformulars auszublenden. Beispielsweise blendet der folgende Code die primäre Instanz des Teilformulars bei der Formularinitialisierung aus. Außerdem überprüft es den App-Typ, um sicherzustellen, dass das Skript nur auf der Clientseite ausgeführt wird: 

      ```javascript
      if ((xfa.host.appType == "HTML 5" || xfa.host.appType == "Exchange-Pro" || xfa.host.appType == "Reader")&&(_RepeatSubform.count == 1)&&(form1.Page1.Subform1.RepeatSubform.Key.rawValue == null)) {
      RepeatSubform.presence = "hidden";
      }
      ```

   1. Öffnen Sie das Skript zum Hinzufügen einer Instanz des Teilformulars zur Bearbeitung. Fügen Sie den folgenden Code hinzu, um eine Instanz des Teilformularskripts hinzuzufügen.

      Der folgende Code überprüft die ausgeblendete Instanz des Teilformulars. Wenn die ausgeblendete Instanz des Teilformulars gefunden wird, löschen Sie die ausgeblendete Instanz des Teilformulars und fügen Sie eine neue Instanz des Teilformulars ein. Wenn die ausgeblendete Instanz des Teilformulars nicht gefunden wird, fügen Sie einfach eine neue Instanz des Teilformulars ein.

      ```javascript
      if (RepeatSubform.presence == "hidden")
      {
      RepeatSubform.instanceManager.insertInstance(0);
      RepeatSubform.instanceManager.removeInstance(1);
      }
      else
      {
      RepeatSubform.instanceManager.addInstance(1);
      }
      ```

   1. Öffnen Sie das Skript zum Entfernen einer Instanz des Teilformulars zum Bearbeiten. Fügen Sie Code ähnlich dem folgenden zum Entfernen einer Instanz des Teilformulars hinzu.

      Der Code überprüft die Anzahl der Teilformulare. Wenn die Anzahl des Teilformulars 1 erreicht hat, blendet der Code das Teilformular aus, anstatt das Teilformular zu löschen.

      ```javascript
      if (RepeatSubform.instanceManager.count == 1) {
      RepeatSubform.presence = "hidden";
      } else {
      RepeatSubform.instanceManager.removeInstance(RepeatSubform.instanceManager.count - 1);
      }
      ```

   1. Öffnen Sie das Ereignis presubmit des Formulars zur Bearbeitung. Fügen Sie dem Ereignis das folgende Skript hinzu, um die ausgeblendete Instanz des Skripts vor der Bearbeitung zu entfernen. Dadurch wird verhindert, dass Daten des ausgeblendeten Teilformulars bei der Übermittlung gesendet werden.

      ```javascript
      if(RepeatSubform.instanceManager.count == 1 && RepeatSubform.presence == "hidden") {
      RepeatSubform.instanceManager.removeInstance(0);
      }
      ```

1. Gibt es Einschränkungen bei der Verwendung ausgeblendeter Teilformulare?

   Antwort: Ein ausgeblendetes Teilformular mit einer komplexen Hierarchie, die auf mehrere Seiten aufgeteilt ist, führt zu Problemen mit dem Layout. Eine Option besteht darin, das Teilformular am Anfang als sichtbar zu markieren und es anschließend in einem auf Logik oder Daten basierenden Initialisierungsskript auszublenden.

1. Warum sind einige Textteile abgeschnitten oder werden in HTML5 nicht korrekt angezeigt?

   Antwort: Wenn nicht genügend Platz zum Anzeigen des Inhalts eines Zeichnungs- oder Beschriftungs-Textelements vorhanden ist, werden manche Texte im Rendering von Mobile Forms abgeschnitten angezeigt. Diese Kürzung ist dann auch in der Designansicht von AEM Forms Designer sichtbar. Zwar kann eine solche Kürzung im PDF-Format bearbeitet werden, in HTML5-Formularen ist dies jedoch nicht möglich. Um das Problem zu vermeiden, stellen Sie genügend Platz zum Zeichnen oder für Beschriftungen zur Verfügung, damit der Text im Designmodus von AEM Forms Designer nicht abgeschnitten wird.

1. Ich beobachte Layout-Probleme im Zusammenhang mit fehlenden oder überlappenden Inhalten. Was ist der Grund?

   Antwort: Wenn sich ein Text- oder Bildzeichnungselement an derselben Position befindet wie ein überlagertes Element (z. B. ein Rechteck), ist der Inhalt des Textzeichnungselements nicht sichtbar, wenn dieses in der Dokumentreihenfolge später kommt (in der Hierarchieansicht des AEM Forms Designer). PDF unterstützt eine transparente Überlagerung, HTML/Browser unterstützen jedoch keine transparente Überlagerung.

1. Warum werden einige Schriften im HTML-Formular in einer anderen Form angezeigt als beim Entwerfen des Formulars?

   Antwort: HTML5-Formulare erlauben keine Einbettung von Schriftarten (im Gegensatz zu PDF-Formularen, bei denen Schriftarten innerhalb des Formulars eingebettet sind). Damit die HTML-Version eines Formulars wie erwartet gerendert wird, stellen Sie sicher, dass die Schriftarten im CRX-Repository (AEM Content-Repository) Ihres AEM Forms-Servers und auf dem Rechner, auf dem AEM Designer installiert ist, verfügbar sind. Wenn die Schriftarten im CRX-Repository Ihres AEM Forms-Servers oder an dem Ort, an dem AEM Designer installiert ist, nicht verfügbar sind, wird das Formular mit Ersatzschriftarten gerendert.

1. Werden die Attribute „vAlign“ und „hAlign“ in HTML-Formularen unterstützt?

   Antwort: Ja, die Attribute „vAlign“ und „hAlign“ werden unterstützt. Das Attribut „vAlign“ wird in Internet Explorer und mehrzeiligen Feldern nicht unterstützt.

1. Unterstützen HTML5-Formulare hebräische Zeichen?

   Antwort: HTML5-Formulare unterstützen hebräische Zeichen in allen Browsern außer Microsoft Internet Explorer.

1. Gibt es in HTML5-Formularen Beschränkungen für numerische Felder?

   Antwort: Ja, HTML5-Formulare weisen einige Einschränkungen auf. Wenn die Anzahl der Ziffern die in der Picture-Klausel festgelegte Anzahl überschreitet, werden die Zahlen nicht lokalisiert, sondern im englischen Gebietsschema angezeigt.

1. Warum sind HTML-Formulare größer als PDF-Formulare?

   Antwort: Um ein XDP-Formular in ein HTML-Formular umzuwandeln, sind viele zwischengeschaltete Datenstrukturen und Objekte wie Formular-DOM, Daten-DOM und Layout-DOM erforderlich.

   Für PDF forms verfügt Adobe Acrobat über eine integrierte XTG-Engine zum Erstellen von Zwischendatenstrukturen und -objekten. Acrobat übernimmt auch Layout und Skripte.

   Für HTML5-Formulare verfügen Browser nicht über eine integrierte XTG-Engine zum Erstellen von Zwischendatenstrukturen und Objekten aus rohen XDP-Bytes. Für HTML5-Formulare werden also Zwischenstrukturen auf dem Server generiert und an den Client gesendet. Auf dem Client verwenden ein JavaScript-basiertes Skript und die Layout-Engine diese Zwischenstrukturen.

   Die Größe der Zwischenstruktur hängt von der Größe der Original-XDP und der mit der XDP zusammengeführten Daten ab.

1. Gibt es Einschränkungen bei der Verwendung von Tabellen in meinem XDP?

   Antwort: Beim Rendering komplexer Tabellen treten Probleme auf.

   * Abschnitte (SubformSet) innerhalb einer Tabelle werden nicht unterstützt.
   * In einigen Tabellen sind Kopf- oder Fußzeilen zur Wiederholung markiert. Die Aufteilung solcher Tabellen auf mehrere Seiten kann zu Problemen führen.

1. Gibt es Einschränkungen bei barrierefreien Tabellen?

   Antwort: Ja barrierefreie Tabellen haben die folgenden Einschränkungen:

   * Verschachtelte Tabellen und Teilformulare in einer Tabelle werden nicht unterstützt.
   * Kopfzeilen werden nur für die obere oder linke Spalte der Tabelle unterstützt. Kopfzeilen werden für Elemente der mittleren Tabelle nicht unterstützt. Sie können Kopfzeilen auf mehrere Zeilen anwenden und Spaltenüberschriften und Spaltenüberschriften werden unterstützt, wenn alle derartigen Zeilen und Spalten auf der obersten Zeile oder in der ganz linken Spalte der Tabelle sind. 
   * `Rowspan` und`colspan` von einer beliebigen Stelle in der Tabelle wird nicht unterstützt. 

   * Sie können Instanzen von Zeilen, die Elemente mit rowspan-Werten größer als 1 enthalten, nicht dynamisch hinzufügen oder entfernen.

1. Was ist die Lesereihenfolge der QuickInfo und Beschriftung für Bildschirmleseprogramme?

   Antwort:
   * Wird QuickInfo und Beschriftung vorhanden sind, wird nur die Beschriftung gelesen. Wenn die Beschriftung nicht verfügbar ist, wird die QuickInfo gelesen. Sie können auch die Priorität für das Lesen in einer XDP mit dem Formularentwickler angeben
   * Wenn Sie den Mauszeiger über ein Element bewegen, wird eine QuickInfo angezeigt. Wenn keine QuickInfo verfügbar ist, wird Sprachtext angezeigt. Wenn kein Sprachtext verfügbar ist, wird der Feldname angezeigt.

1. Wenn Sie den Mauszeiger über ein Feld bewegen, wird eine QuickInfo angezeigt. Wie kann ich sie deaktivieren?

   Antwort: Um den Tooltip beim Daraufzeigen zu deaktivieren, wählen Sie im Bedienfeld „Barrierefreiheit“ von Designer die Option „Keine“.

1. In Designer kann ein Benutzer benutzerdefinierte Erscheinungsbildeigenschaften von Optionsfeldern und Kontrollkästchen konfigurieren. Berücksichtigen HTML5-Formulare beim Rendern von Formularen auch diese benutzerdefinierten Erscheinungsbildeigenschaften?

   Antwort: HTML5-Formulare ignorieren die benutzerdefinierten Erscheinungsbildeigenschaften von Optionsfeldern und Kontrollkästchen. Die Optionsfelder und Kontrollkästchen werden gemäß den Spezifikationen des zugrunde liegenden Browsers angezeigt.

1. Wenn ein HTML5-Formular in einem unterstützten Browser geöffnet wird, wird der Rand der angrenzenden Felder nicht richtig ausgerichtet oder die Teilformulare erscheinen überlappend. Wenn dasselbe HTML5-Formular in Forms Designer in der Vorschau angezeigt wird, erscheinen die Felder und das Layout nicht falsch ausgerichtet und die Teilformulare erscheinen an der richtigen Position. Wie lässt sich das Problem beheben?

   Antwort: Wenn ein Unterformular auf Flussinhalt eingestellt ist und das Unterformular ein ausgeblendetes Randelement hat, wird der Rand der nebeneinander platzierten Felder nicht richtig ausgerichtet oder die Unterformulare erscheinen überlappend. Um das Problem zu beheben, können Sie die versteckten &lt;border>-Elemente aus dem entsprechenden XDP entfernen oder mit Kommentaren versehen. Beispielsweise wird das folgende &lt;border>-Element als Kommentar markiert:

   ```xml
               <!--<border>
                  <edge presence="hidden"/>
                  <corner thickness="0.175mm" presence="hidden"/>
               </border> -->
   ```

1. Warum funktionieren Bildschirmlesehilfen nicht ordnungsgemäß mit dem Datums-/Uhrzeitfeldobjekt?

   Antwort: Bildschirmlesehilfen unterstützen keine Datums-/Zeitfelder. Sie können jedoch manuell Datum/Uhrzeit in das Feld eingeben, damit die Bildschirmlesehilfe dies liest. Verwenden Sie eine QuickInfo oder Text der Bildschirmlesehilfe, um den Benutzer anzuweisen, Datum/Uhrzeit für das Feld manuell auszuwählen.

1. Unterstützen HTML5-Formulare Anzeigemuster für schwebende Felder?

   Antwort: HTML5-Formulare unterstützen keine Anzeigemuster für schwebende Felder.

1. Welches Format hat das Datumsfeld in HTML5-Formularen?

Antwort: Das Datumsfeld akzeptiert das ISO-Format JJJJ-MM-TT. Wenn Sie ein Datum in einem anderen Format angeben, übernimmt das Datumsfeld die Formatierung erst, wenn der Benutzer das Feld mit der Tabulatortaste verlässt.

### Skripterstellung {#scripting}

1. Gibt es Einschränkungen bei der JavaScript-Implementierung für HTML Forms?

   Antwort:

   * Das Skript xfa.connectionSet wird nur eingeschränkt unterstützt. Für „connectionSet“ werden nur Server-seitige Webservice-Aufrufe unterstützt. Detaillierte Informationen finden Sie unter [Skriptunterstützung](/help/forms/using/scripting-support.md).
   * In clientseitigen Skripten werden $record und $data nicht unterstützt. Wenn die Skripte jedoch in einen „formReady“-, „layoutReady“-Block geschrieben werden, funktionieren diese Skripte weiterhin, da die Ereignisse auf der Server-Seite ausgelöst werden.
   * XFA Zeichnen elementspezifische Skripte wie das Ändern des Zeichnungstextes (oder des Beschriftungstextes, wenn Felder vorhanden sind) werden nicht unterstützt.

1. Gibt es Einschränkungen bei der Verwendung von formCalc?

   Antwort: Derzeit ist nur eine Teilmenge der formCalc-Skripte implementiert. Detaillierte Informationen finden Sie unter [Skriptunterstützung](/help/forms/using/scripting-support.md).

1. Gibt es eine empfohlene Benennungskonvention und gibt es reservierte Schlüsselwörter, die vermieden werden sollten?

   Antwort:
   * In AEM Forms Designer wird empfohlen, den Namen eines Objekts (z. B. eines Unterformulars oder eines Textfelds) nicht mit einem Unterstrich (_) zu beginnen. Um einen Unterstrich am Anfang des Namens zu verwenden, fügen Sie ein Präfix nach dem Unterstrich hinzu,_&lt;prefix>&lt;objectname>.
   * Alle HTML5-Formular-APIs sind reservierte Schlüsselwörter. Bei benutzerdefinierten APIs/Funktionen müssen Sie einen Namen verwenden, der nicht mit den [HTML5 Forms APIs](/help/forms/using/scripting-support.md) identisch ist.

1. Unterstützen HTML5-Formulare schwebende Felder?

   Antwort: Ja, HTML5-Forms unterstützen schwebende Felder. Um schwebende Felder zu aktivieren, fügen Sie dem Renderprofil die folgende Eigenschaft hinzu:

   >[!NOTE]
   >
   >Standardmäßig sind die Felder nicht für schwebende Felder aktiviert. Sie können Forms Designer verwenden, um die schwebende Eigenschaft der Felder festzulegen.

   1. Öffnen Sie CRXDE Lite und navigieren Sie zum Knoten `/content/xfaforms/profiles/default`.
   1. Fügen Sie eine `mfDataDependentFloatingField`-Eigenschaft mit dem Typ „Zeichenfolge“ hinzu und legen Sie den Wert der Eigenschaft auf `true` fest.
   1. Klicken Sie auf **Alle speichern**. Jetzt sind die schwebenden Felder für die HTML-Formulare mit dem aktualisierten Renderprofil aktiviert.

      >[!NOTE]
      >
      >Um schwebende Felder für ein spezifisches Formular zu aktivieren, ohne das Renderprofil zu aktualisieren, geben Sie die Eigenschaft „mfDataDependentFloatingField=true“ als URL-Parameter weiter.

1. Führt HTML5 Forms das Initialisierungsskript und das formularbereite Ereignis mehrmals aus?

   Antwort: Ja, die Initialisierungsskripte und Formularbereitschaftsereignisse werden mehrfach ausgeführt, mindestens einmal auf dem Server und einmal auf der Client-Seite. Es wird empfohlen, Skripte wie „initialize“ oder „form:ready“-Ereignisse basierend auf einer Geschäftslogik (Formular- oder Felddaten) zu schreiben, sodass die Aktion basierend auf dem Status der Daten und „idempotent“ (wenn die Daten gleich sind) ausgeführt wird.

### XDP entwerfen {#designing-xdp}

1. Gibt es reservierte Schlüsselwörter in HTML5-Formularen?

   Antwort: Alle HTML5 Forms-APIs sind reservierte Schlüsselwörter. Bei benutzerdefinierten APIs/Funktionen müssen Sie einen Namen verwenden, der nicht mit den [HTML5 Forms APIs](/help/forms/using/scripting-support.md) identisch ist. Wenn Sie, abgesehen von reservierten Schlüsselwörtern, Objektnamen verwenden, die mit einem Unterstrich (_) beginnen, wird empfohlen, nach dem Unterstrich ein Präfix einzufügen. Das Einfügen eines Präfix verhindert mögliche Konflikte mit HTML5-Formular-internen APIs. Beispiel: `_fpField1`
