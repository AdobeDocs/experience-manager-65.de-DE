---
title: Erstellen von benutzerspezifischen Erscheinungsbildern in HTML5-Formularen
seo-title: Create custom appearances in HTML5 forms
description: Sie können benutzerdefinierte Widgets mit einer mobilen Forms einbinden. Sie können vorhandene jQuery Widgets erweitern oder eigene benutzerdefinierte Widgets entwickeln.
seo-description: You can plug in custom widgets to a Mobile Forms. You can extend existing jQuery Widgets or develop your own custom widgets.
uuid: a9013c3d-20c7-45c9-be24-8e9d4525eff8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 17a86543-30d3-4e16-a373-67b46d551da9
docset: aem65
feature: Mobile Forms
exl-id: 76bd1e2d-9e65-452c-8cef-123d28886a62
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 50%

---

# Erstellen von benutzerspezifischen Erscheinungsbildern in HTML5-Formularen{#create-custom-appearances-in-html-forms}

Sie können benutzerdefinierte Widgets mit einer mobilen Forms einbinden. Sie können mithilfe des Erscheinungsbild-Framework vorhandene jQuery Widgets erweitern oder Ihre eigenen benutzerdefinierten Widgets entwickeln. Die XFA-Engine verwendet verschiedene Widgets. Detaillierte Informationen finden Sie unter [Erscheinungsbild-Framework für adaptive und HTML5-Formulare](/help/forms/using/introduction-widgets.md).

![Beispiel für ein standardmäßiges und benutzerdefiniertes Widget](assets/custom-widgets.jpg)

Beispiel für ein standardmäßiges und ein benutzerdefiniertes Widget

## Integrieren benutzerdefinierter Widgets mit HTML5-Formularen {#integrating-custom-widgets-with-html-forms}

### Profil erstellen  {#create-a-profile-nbsp}

Sie können ein Profil erstellen oder ein vorhandenes Profil auswählen, um ein benutzerdefiniertes Widget hinzuzufügen. Weitere Informationen zum Erstellen von Profilen finden Sie unter [Erstellen eines benutzerdefinierten Profils](/help/forms/using/custom-profile.md).

### Erstellen eines Widgets {#create-a-widget}

HTML5-Formulare bieten eine Implementierung des Widget-Frameworks, die zum Erstellen neuer Widgets erweitert werden kann. Die Implementierung ist ein jQuery-Widget *abstractWidget* , die erweitert werden können, um ein neues Widget zu schreiben. Das neue Widget kann nur durch Erweitern/Überschreiben der unten genannten Funktionen funktionieren.

<table>
 <tbody>
  <tr>
   <td>Funktion/Klasse</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td>render</td>
   <td>Die Renderfunktion gibt das jQuery-Objekt für das standardmäßige HTML-Element des Widgets zurück. Das standardmäßige HTML-Element sollte fokussierbar sein. Beispiel: &lt;a&gt;, &lt;input&gt;, und &lt;li&gt;. Das zurückgegebene Element wird als $userControl verwendet. Wenn $userControl die oben stehende Bedingung erfüllt, laufen die Funktionen der Klasse „AbstractWidget“ ordnungsgemäß. Ansonsten müssen einige allgemeine APIs (focus, click) geändert werden. </td>
  </tr>
  <tr>
   <td>getEventMap</td>
   <td>Gibt eine Zuordnung zur Konvertierung von HTML-Elementen zu XFA-Ereignissen zurück.  <br /> {<br /> blur: XFA_EXIT_EVENT,<br /> }<br /> Dieses Beispiel zeigt, dass „blur“ ein HTML-Ereignis und XFA_EXIT_EVENT das entsprechende XFA-Ereignis ist. </td>
  </tr>
  <tr>
   <td>getOptionsMap</td>
   <td>Gibt eine Zuordnung zurück, die detailliert beschreibt, welche Aktion bei Änderung einer Option ausgeführt werden soll. Die Schlüssel sind die Optionen, die dem Widget übergeben werden, und die Werte sind die Funktionen, die aufgerufen werden, wenn eine Änderung in der jeweiligen Option erkannt wird. Das Widget bietet Handler für alle allgemeinen Optionen (außer value und displayValue)</td>
  </tr>
  <tr>
   <td>getCommitValue</td>
   <td>Das Widget-Framework lädt die Funktion jedes Mal, wenn der Wert des Widgets im XFAModel gespeichert wird (z. B. beim exit-Ereignis eines textField). Die Implementierung sollte den Wert zurückgeben, der im Widget gespeichert wird. Der Handler erhält den neuen Wert für die Option.</td>
  </tr>
  <tr>
   <td>showValue</td>
   <td>Standardmäßig wird in XFA beim enter-Ereignis der rawValue des Felds angezeigt. Diese Funktion wird aufgerufen, um dem Benutzer den rawValue anzuzeigen. </td>
  </tr>
  <tr>
   <td>showDisplayValue</td>
   <td>Standardmäßig wird in XFA beim exit-Ereignis der formattedValue des Felds angezeigt. Diese Funktion wird aufgerufen, um dem Benutzer den formattedValue anzuzeigen. </td>
  </tr>
 </tbody>
</table>

Um ein eigenes Widget im oben erstellen Profil zu erstellen, müssen Sie die Verweise der JavaScript-Datei einschließen, die die überschriebenen und neu hinzugefügten Funktionen enthält. Das *sliderNumericFieldWidget* ist beispielsweise ein Widget für numerische Felder. Um das Widget in Ihrem Profil im Kopfzeilenabschnitt zu verwenden, fügen Sie die folgende Zeile ein:

```javascript
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Registrieren von benutzerdefinierten Widgets mit XFA Scripting Engine  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Wenn der Code des benutzerdefinierten Widgets fertig ist, registrieren Sie das Widget mit der Skripterstellungs-Engine, indem Sie die `registerConfig`-API für [Form Bridge](/help/forms/using/form-bridge-apis.md) verwenden. Es erfordert widgetConfigObject als Eingabe.

```javascript
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

Die Widget-Konfiguration wird als JSON-Objekt (eine Sammlung von Schlüssel-Wert-Paaren) bereitgestellt, bei dem der Schlüssel die Felder identifiziert und der Wert das Widget darstellt, das mit diesen Feldern verwendet werden soll. Eine Beispielkonfiguration sieht wie folgt aus:

```
*{*

*"identifier1" : "customwidgetname",
"identifier2" : "customwidgetname2",
..
}*
```

wobei „Kennung“ eine jQuery-CSS-Auswahl ist, die ein bestimmtes Feld, eine Gruppe von Feldern eines bestimmten Typs oder alle Felder darstellt. Im Folgenden ist der Wert des Bezeichners in verschiedenen Fällen aufgeführt:

| Typ des Bezeichners | ID | Beschreibung |
|---|---|---|
| Bestimmtes Feld mit name fieldname | Bezeichner:&quot;div.fieldname&quot; | Alle Felder mit dem Namen &quot;fieldname&quot;werden mithilfe des Widgets gerendert. |
| Alle Felder des Typs „type“ („type“ ist hier „NumericField“, „DateField“ usw.): | Bezeichner: &quot;div.type&quot; | Für „TimeField“ und „DateTimeField“ ist der Typ „textfield“, da diese Felder nicht unterstützt werden. |
| Alle Felder | Kennung: &quot;div.field&quot; |  |
