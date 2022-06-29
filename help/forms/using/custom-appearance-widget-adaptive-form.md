---
title: Erstellen von benutzerdefinierten Erscheinungsbildern für adaptive Formularfelder
seo-title: Create custom appearances for adaptive form fields
description: Passen Sie das Erscheinungsbild einsatzbereiter Komponenten in adaptiven Formularen an.
seo-description: Customize appearance of out-of-the-box components in Adaptive Forms.
uuid: 1aa36443-774a-49fb-b3d1-d5a2d5ff849a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: d388acef-7313-4e68-9395-270aef6ef2c6
docset: aem65
exl-id: 770e257a-9ffd-46a4-9703-ff017ce9caed
source-git-commit: 8a24ca02762e7902b7d0033b36560629ee711de1
workflow-type: ht
source-wordcount: '1713'
ht-degree: 100%

---

# Erstellen von benutzerdefinierten Erscheinungsbildern für adaptive Formularfelder{#create-custom-appearances-for-adaptive-form-fields}

## Einführung {#introduction}

Adaptive Formulare nutzen das [Framework für Erscheinungsbild](/help/forms/using/introduction-widgets.md), um Ihnen beim Erstellen von benutzerdefinierten Erscheinungsbildern für adaptive Formularfelder zu helfen und eine neuartige Benutzerfreundlichkeit zu bieten. Ersetzen Sie zum Beispiel Optionsfelder und aktivieren Sie Felder mit Schaltflächen oder verwenden Sie benutzerdefinierte jQuery-Plugins, um Benutzereingaben in Feldern wie Telefonnummern oder E-Mail-ID einzuschränken.

In diesem Dokument wird erläutert, wie ein jQuery-Plugin verwendet wird, um diese alternativen Erfahrungen für adaptive Formularfelder zu erstellen. Darüber hinaus demonstriert es ein Beispiel dafür, wie ein benutzerdefiniertes Erscheinungsbild für numerische Feldkomponente erstellt wird, damit es als numerischer Schritt oder Schieberegler dargestellt wird.

Werfen wir einen Blick auf die in diesem Artikel verwendeten Schlüsselbegriffe und Konzepte.

**Erscheinungsbild** Bezieht sich auf den Stil, das Aussehen und die Anordnung verschiedener Elemente eines adaptiven Formularfelds. Es umfasst in der Regel eine Beschriftung, einen interaktiven Bereich für Eingaben, ein Hilfesymbol und kurze und lange Beschreibungen des Feldes. Die in diesem Artikel besprochene Anpassung des Erscheinungsbilds gilt für das Erscheinungsbild des Feld-Eingabebereichs.

**jQuery-Plug-in** Stellt einen Standardmechanismus basierend auf dem jQuery-Widget-Framework bereit, um ein alternatives Erscheinungsbild zu implementieren.

**ClientLib** Ein Client-seitiges Bibliothekensystem in Client-seitiger AEM-Verarbeitung, das von komplexem JavaScript- und CSS-Code gesteuert wird. Weitere Informationen finden Sie unter Verwenden Client-seitiger Bibliotheken.

**Archetyp** Das Vorlagenerstellungs-Toolkit eines Maven-Projekts, das als Originalmuster oder -modell für Maven-Projekte festgelegt wird. Weitere Informationen finden Sie unter Einführung in Archetypen.

**Benutzerkontrolle** Bezieht sich auf das Hauptelement in einem Widget, das den Wert des Felds enthält; es wird vom Framework für das Erscheinungsbild verwendet, um die benutzerdefinierte Widget-Benutzeroberfläche mit dem adaptiven Formularmodell zu verbinden.

## Schritte zum Erstellen eines benutzerdefinierten Erscheinungsbilds {#steps-to-create-a-custom-appearance}

Die Schritte zum Erstellen eines benutzerdefinierten Erscheinungsbilds auf höherer Ebene sind wie folgt:

1. **Projekt erstellen**: Erstellen Sie ein Maven-Projekt, das ein Inhaltspaket generiert, das in AEM bereitgestellt wird.
1. **Vorhandene Widget-Klasse erweitern**: Erweitern Sie eine vorhandene Widget-Klasse und überschreiben Sie die erforderlichen Klassen.
1. **Client-Bibliothek erstellen**: Erstellen Sie eine `clientLib: af.customwidget`-Bibliothek und fügen Sie die erforderlichen JavaScript- und CSS-Dateien hinzu.

1. **Projekt erstellen und installieren**: Erstellen Sie das Maven-Projekt und installieren Sie den generierten Inhalt in AEM.
1. **Adaptives Formular aktualisieren**: Aktualisieren Sie die Eigenschaften adaptiver Formularfelder zur Nutzung des benutzerdefinierten Erscheinungsbilds.

### Projekt erstellen {#create-a-project}

Ein Maven-Archetyp bildet den Ausgangspunkt zum Erstellen eines benutzerdefinierten Erscheinungsbilds. Die Details des zu verwendenden Archetyps lauten folgendermaßen:

* **Repository**: https://repo1.maven.org/maven2/com/adobe/
* **Artefakt-ID**: custom-appearance-archetype
* **Gruppen-ID**: com.adobe.aemforms
* **Version**: 1.0.4

Führen Sie den folgenden Befehl aus, um ein lokales Projekt basierend auf dem Archetyp zu erstellen:

`mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

Mit dem Befehl werden die Maven-Plugins und Archetypinformationen aus dem Repository heruntergeladen und ein Projekt basierend auf den folgenden Informationen generiert:

* **groupId**: vom generierten Maven-Projekt verwendete Gruppen-ID
* **artifactId**: vom generierten Maven-Projekt verwendete Artefakt-ID.
* **version**: Version für das generierte Maven-Projekt.
* **package**: für die Dateistruktur verwendetes Paket.
* **artifactName**: Artefaktname des generierten AEM-Pakets.
* **packageGroup**: Paketgruppe des generierten AEM-Pakets.
* **widgetName**: zu Referenzzwecken verwendeter Name des Erscheinungsbilds.

Das generierte Projekt hat die folgende Struktur:

```java
─<artifactId>

 └───src

     └───main

         └───content

             └───jcr_root

                 └───etc

                     └───clientlibs

                         └───custom

                             └───<widgetName>

                                 ├───common [client library - af.customwidgets which encapsulates below clientLibs]

                                 ├───integration [client library - af.customwidgets.<widgetName>_widget which contains template files for integrating a third-party plugin with Adaptive Forms]

                                 │   ├───css

                                 │   └───javascript

                                 └───jqueryplugin [client library - af.customwidgets.<widgetName>_plugin which holds the third-party plugins and related dependencies]

                                     ├───css

                                     └───javascript
```

### Vorhandene Widget-Klasse erweitern {#extend-an-existing-widget-class}

Nehmen Sie nach Erstellen der Projektvorlage bei Bedarf die folgenden Änderungen vor:

1. Schließen Sie die Plugin-Abhängigkeit des Fremdanbieters in das Projekt ein.

   1. Platzieren Sie die Fremdanbieter- oder benutzerdefinierten jQuery-Plug-ins im Ordner `jqueryplugin/javascript` und zugehörige CSS-Dateien im Ordner `jqueryplugin/css`. Weitere Informationen finden Sie in den JS- und CSS-Dateien im Ordner `jqueryplugin/javascript and jqueryplugin/css`.

   1. Ändern Sie die Dateien `js.txt` und `css.txt`, um jede zusätzliche JavaScript- und CSS-Datei des jQuery-Plugins einzuschließen.

1. Integrieren Sie das Drittanbieter-Plug-In mit dem Framework, um die Interaktion zwischen dem benutzerdefinierten Framework des Erscheinungsbilds und dem jQuery-Plugin zu aktivieren. Das neue Widget funktioniert erst, wenn Sie die folgenden Funktionen erweitern oder überschreiben.

<table>
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><code>render</code></td>
   <td>Die Renderfunktion gibt das jQuery-Objekt für das standardmäßige HTML-Element des Widgets zurück. Das standardmäßige HTML-Element sollte fokussierbar sein. Zum Beispiel <code>&lt;a&gt;</code>, <code>&lt;input&gt;</code> und <code>&lt;li&gt;</code>. Das zurückgegebene Element wird als <code>$userControl</code> verwendet. Wenn <code>$userControl</code> die oben stehende Bedingung angibt, funktioniert die Klasse <code>AbstractWidget</code> erwartungsgemäß. Ansonsten müssen einige allgemeine APIs (focus, click) geändert werden. </td>
  </tr>
  <tr>
   <td><code>getEventMap</code></td>
   <td>Gibt eine Zuordnung zur Konvertierung von HTML-Elementen zu XFA-Ereignissen zurück. <br /> <code class="code">{
      blur: XFA_EXIT_EVENT,
      }</code><br /> Dieses Beispiel zeigt, dass <code>blur</code> ein HTML-Ereignis und <code>XFA_EXIT_EVENT</code> das entsprechende XFA-Ereignis ist. </td>
  </tr>
  <tr>
   <td><code>getOptionsMap</code></td>
   <td>Gibt eine Zuordnung mit detaillierten Informationen zurück, wie eine Option geändert werden kann. Die Schlüssel sind die Optionen des Widgets und die Werte sind die Funktionen, die aufgerufen werden, sobald eine Änderung in dieser Option erkannt wird. Das Widget verfügt über Handler für alle allgemeinen Optionen (außer <code>value</code> und <code>displayValue</code>).</td>
  </tr>
  <tr>
   <td><code>getCommitValue</code></td>
   <td>Das jQuery-Widget-Framework lädt Funktionen, sobald der Wert des jQuery-Widgets im XFA-Modell gespeichert wird (beispielsweise bei einem exit-Ereignis eines Textfelds). Die Implementierung sollte den Wert zurückgeben, der im Widget gespeichert wird. Der Handler erhält den neuen Wert für die Option.</td>
  </tr>
  <tr>
   <td><code>showValue</code></td>
   <td>Standardmäßig wird in XFA beim Ereignis „enter“ der <code>rawValue</code> des Felds angezeigt. Diese Funktion wird aufgerufen, um dem Benutzer den <code>rawValue</code> zu zeigen. </td>
  </tr>
  <tr>
   <td><code>showDisplayValue</code></td>
   <td>Standardmäßig wird in XFA beim Ereignis „exit“ der <code>formattedValue</code> des Felds angezeigt. Diese Funktion wird aufgerufen, um dem Benutzer den <code>formattedValue</code> zu zeigen. </td>
  </tr>
 </tbody>
</table>

1. Aktualisieren Sie bei Bedarf die JavaScript-Datei im Ordner `integration/javascript`.

   * Ersetzen Sie den Text `__widgetName__` durch den tatsächlichen Widget-Namen.
   * Erweitern Sie das Widget aus einer geeigneten, sofort einsetzbaren Widget-Klasse. In den meisten Fällen handelt es sich dabei um die Widget-Klasse, die mit dem vorhandenen Widget übereinstimmt, das ersetzt wird. Der Name der übergeordneten Klasse wird an mehreren Standorten verwendet, daher wird empfohlen, nach allen Instanzen der Zeichenfolge `xfaWidget.textField` in der Datei zu suchen und sie durch die eigentliche übergeordnete Klasse zu ersetzen, die verwendet wird.
   * Erweitern Sie die Methode `render`, um eine alternative UI bereitzustellen. Das ist der Standort, von dem aus das jQuery-Plugin aufgerufen wird, um die UI oder das Interaktionsverhalten zu aktualisieren. Die Methode `render` sollte ein Benutzersteuerelement zurückgeben.

   * Erweitern Sie die Methode `getOptionsMap`, um alle Optionseinstellungen zu überschreiben, die durch Änderungen am Widget beeinflusst wurden. Die Funktion gibt eine Zuordnung zurück, die Informationen bereitstellt, damit die Aktion nach Änderung einer Option durchgeführt werden kann. Die Schlüssel sind die Optionen des Widgets und die Werte sind die Funktionen, die aufgerufen werden, sobald eine Änderung in dieser Option erkannt wird.
   * Die Methode `getEventMap` ordnet durch das Widget ausgelöste Ereignisse den Ereignissen zu, die durch das adaptive Formularmodell benötigt werden. Der Standardwert ordnet Standard-HTML-Ereignisse für das Standard-Widget zu. Es muss aktualisiert werden, falls ein alternatives Widget ausgelöst wird.
   * `showDisplayValue` und `showValue` wenden die Display- und Edit-Picture-Klausel an und können überschrieben werden, um ein alternatives Verhalten zu erzielen.

   * Die Methode `getCommitValue` wird durch das Framework für adaptive Formulare aufgerufen, wenn das Ereignis `commit` auftritt. Im Allgemeinen handelt es sich um das exit-Ereignis, mit Ausnahme von Dropdown-Liste, Optionsfeld und Elementen des Kontrollkästchens, wenn es bei einer Änderung auftritt. Weitere Informationen finden Sie unter[ Adaptive Formularausdrücke](../../forms/using/adaptive-form-expressions.md#p-value-commit-script-p).

   * Die Vorlagendatei bietet Beispielimplementierung für verschiedene Methoden. Entfernen Sie Methoden, die nicht erweitert werden sollen.

### Client-Bibliothek erstellen {#create-a-client-library}

Das durch den Maven-Archetyp generierte Beispielprojekt erstellt automatisch erforderliche Client-Bibliotheken und legt sie in eine Client-Bibliothek mit der Kategorie `af.customwidgets` ab. Die in`af.customwidgets` verfügbaren JavaScript- und CSS-Dateien werden zur Laufzeit automatisch eingefügt.

### Erstellen und Installieren {#build-and-install}

Führen Sie zum Erstellen des Projekts den folgenden Befehl im Shell aus, um ein CRX-Paket zu generieren, das auf einem AEM-Server installiert werden muss.

`mvn clean install`

>[!NOTE]
>
>Das Maven-Projekt bezieht sich auf ein Remote-Repository in der POM-Datei. Dies dient nur zu Referenzzwecken und die Repository-Informationen werden gemäß Maven-Standards in der Datei `settings.xml` erfasst.

### Adaptives Formular aktualisieren {#update-the-adaptive-form}

So wenden Sie das benutzerdefinierte Erscheinungsbild auf ein adaptives Formularfeld an:

1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus.
1. Öffnen Sie das Dialogfeld **Eigenschaft** für das Feld, auf das Sie das benutzerdefinierte Erscheinungsbild anwenden möchten.
1. Aktualisieren Sie auf der Registerkarte **Stile** die Eigenschaft `CSS class`, um den Namen des Erscheinungsbilds zum Format `widget_<widgetName>` hinzufügen. Beispiel: **widget_numericstepper**

## Beispiel: Benutzerspezifische Berichte erstellen   {#sample-create-a-custom-appearance-nbsp}

Werfen wir nun einen Blick auf ein Beispiel, um ein benutzerdefiniertes Erscheinungsbild für ein numerisches Feld zu erstellen, damit es als numerischer Schritt oder Schieberegler dargestellt wird. Führen Sie die folgenden Schritte durch:

1. Führen Sie den folgenden Befehl aus, um ein lokales Projekt basierend auf dem Maven-Archetyp zu erstellen:

   `mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

   Es fordert Sie auf, Werte für die folgenden Parameter anzugeben.
   *Die in diesem Beispiel verwendeten Werte werden fett markiert*.

   `Define value for property 'groupId': com.adobe.afwidgets`

   `Define value for property 'artifactId': customWidgets`

   `Define value for property 'version': 1.0.1-SNAPSHOT`

   `Define value for property 'package': com.adobe.afwidgets`

   `Define value for property 'artifactName': customWidgets`

   `Define value for property 'packageGroup': adobe/customWidgets`

   `Define value for property 'widgetName': numericStepper`

1. Navigieren Sie zum Verzeichnis `customWidgets` (angegebener Wert für die Eigenschaft `artifactID`) und führen Sie den folgenden Befehl durch, um ein Eclipse-Projekt zu generieren:

   `mvn eclipse:eclipse`

1. Öffnen Sie das Eclipse-Tool und führen Sie zum Importieren des Eclipse-Projekts die folgenden Schritte durch:

   1. Wählen Sie **[!UICONTROL Datei > Importieren > Vorhandene Projekte in den Arbeitsbereich]**.

   1. Suchen Sie den Ordner aus, in dem Sie den Befehl `archetype:generate` durchgeführt haben.

   1. Klicken Sie auf **[!UICONTROL Beenden]**.

      ![eclipse-screenshot](assets/eclipse-screenshot.png)

1. Wählen Sie das Widget aus, das für das benutzerdefinierte Erscheinungsbild verwendet werden soll. In diesem Beispiel wird das Widget für numerische Schritte verwendet:

   [https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html](https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html)

   Überprüfen Sie im Eclipse-Projekt die Datei `plugin.js`, um sicherzustellen, dass sie mit den Anforderungen für das Erscheinungsbild übereinstimmt. In diesem Beispiel erfüllt das Erscheinungsbild die folgenden Anforderungen:

   * Die numerischen Schritte sollten über `- $.xfaWidget.numericInput` erweitert werden.
   * Die Methode `set value` des Widgets legt den Wert fest, nachdem der Fokus auf das Feld festgelegt wurde. Es ist eine obligatorische Anforderung für das Widget eines adaptiven Formulars.
   * Die Methode `render` muss überschrieben werden, um die Methode `bootstrapNumber` aufzurufen.

   * Mit Ausnahme des Haupt-Quellcodes gibt es für das Plugin keine zusätzliche Abhängigkeit.
   * In dem Beispiel werden keine Stile auf die Schritte angewendet und daher ist kein zusätzliches CSS erforderlich.
   * Das `$userControl`-Objekt sollte in der `render`-Methode verfügbar sein. Es ist ein Feld vom Typ `text`, das mit dem Plugin-Typ geklont wird.

   * Die Schaltflächen **+** und **-** sollten deaktiviert werden, wenn das Feld deaktiviert wird.

1. Ersetzen Sie den Inhalt des `bootstrap-number-input.js` (jQuery-Plugin) mit dem Inhalt der `numericStepper-plugin.js`-Datei.
1. Fügen Sie in der Datei `numericStepper-widget.js` den folgenden Code hinzu, um die Render-Methode zum Aufrufen des Plug-ins und Zurückgeben des `$userControl`-Objekts zu überschreiben:

   ```javascript
   render : function() {
        var control = $.xfaWidget.numericInput.prototype.render.apply(this, arguments);
        var $control = $(control);
        var controlObject;
        try{
            if($control){
            $control.bootstrapNumber();
            var id = $control.attr("id");
            controlObject = $("#"+id);
            }
        }catch (exc){
             console.log(exc);
        }
        return controlObject;
   }
   ```

1. Überschreiben Sie in der Datei `numericStepper-widget.js` die Eigenschaft `getOptionsMap`, um die Zugriffsoption zu überschreiben, und blenden Sie die Schaltflächen „+“ und „-“ im deaktivierten Modus aus.

   ```javascript
   getOptionsMap: function(){
       var parentOptionsMap = $.xfaWidget.numericInput.prototype.getOptionsMap.apply(this,arguments),
   
       newMap = $.extend({},parentOptionsMap,
   
        {
   
              "access": function(val) {
              switch(val) {
                 case "open" :
                   this.$userControl.removeAttr("readOnly");
                   this.$userControl.removeAttr("aria-readonly");
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
                 case "nonInteractive" :
                 case "protected" :
                   this.$userControl.attr("disabled", "disabled");
                   this.$userControl.attr("aria-disabled", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
                case "readOnly" :
                   this.$userControl.attr("readOnly", "readOnly");
                   this.$userControl.attr("aria-readonly", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
               default :
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
             }
          },
      });
      return newMap;
    }
   ```

1. Speichern Sie die Änderungen, navigieren Sie zum Ordner mit der Datei `pom.xml` und führen Sie folgenden Maven-Befehl aus, um das Projekt zu erstellen:

   `mvn clean install`

1. Installieren Sie das Paket mit dem AEM Package Manager.

1. Öffnen Sie das adaptive Formular im Bearbeitungsmodus, auf das Sie das benutzerdefinierte Erscheinungsbild anwenden möchten, und führen Sie die folgenden Schritte durch:

   1. Klicken Sie mit der rechten Maustaste auf das Feld, auf das Sie das Erscheinungsbild anwenden möchten, und klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Dialogfeld „Komponente bearbeiten“ zu öffnen.

   1. Aktualisieren Sie in der Registerkarte „Stile“ die Eigenschaft **[!UICONTROL CSS-Klasse]**, um `widget_numericStepper` hinzuzufügen.

Das gerade erstellte, neue Erscheinungsbild ist jetzt verfügbar.
