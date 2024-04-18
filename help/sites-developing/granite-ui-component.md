---
title: Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche
description: Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten für die Verwendung in Formularen, die in Granite als „Felder“ bezeichnet werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e4820330-2ee6-4eca-83fd-462aa0b83647
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 100%

---

# Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche{#creating-a-new-granite-ui-field-component}

Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten für die Verwendung in Formularen, die im Vokabular der Granite-Benutzeroberfläche als *Felder* bezeichnet werden. Die Standard-Formularkomponenten in Granite sind verfügbar unter:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Die Formularfelder der Granite-Benutzeroberfläche sind von besonderem Interesse, da sie für [Komponenten-Dialogfelder](/help/sites-developing/developing-components.md) verwendet werden.

>[!NOTE]
>
>Vollständige Informationen zu Feldern finden Sie in der [Dokumentation zur Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Verwenden Sie das Foundation-Framework der Granite-Benutzeroberfläche zum Entwickeln und/oder Erweitern von Granite-Komponenten.  Dieses umfasst zwei Elemente:

* Server-seitig:

   * eine Reihe von Foundation-Komponenten

      * Foundation – modular, zusammensetzbar, schichtfähig, wiederverwendbar
      * Komponenten – Sling-Komponenten

   * Hilfsprogramme für die Anwendungsentwicklung

* Client-seitig:

   * eine Sammlung von Client-Bibliotheken mit Vokabular (das heißt, einer Erweiterung der HTML-Sprache) für generische Interaktionsmuster in einer von Hypermedia gesteuerten Benutzeroberfläche.

Die generische Komponente `field` der Granite-Benutzeroberfläche beinhaltet zwei wichtige Dateien:

* `init.jsp`: Übernimmt die generische Verarbeitung sowie Beschriftung und Beschreibung und liefert den für das Rendern des Felds erforderlichen Formularwert.
* `render.jsp`: Übernimmt das tatsächliche Rendern des Felds und muss für das benutzerdefinierte Feld überschrieben werden; ist in `init.jsp` enthalten.

Weitere Informationen finden Sie in der [Dokumentation zur Granite-Benutzeroberfläche – Feld](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html).

Beispiele finden Sie hier:

* `cqgems/customizingfield/components/colorpicker`

   * im Abschnitt [Codebeispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Da dieser Mechanismus JSP verwendet, werden i18n und XSS nicht vorgefertigt bereitgestellt.  Daher müssen Sie die Zeichenfolgen internationalisieren und mit Escape-Zeichen versehen.  Das folgende Verzeichnis enthält die generischen Felder aus einer Standardinstanz, die Sie als Referenz verwenden können:
>
>`/libs/granite/ui/components/foundation/form`-Verzeichnis

## Erstellen des serverseitigen Skripts für die Komponente {#creating-the-server-side-script-for-the-component}

Das benutzerdefinierte Feld sollte das `render.jsp`-Skript nur überschreiben, wenn Sie das Markup für die Komponente angeben. Das JSP (das heißt das Render-Skript) ist dabei quasi der Wrapper für das Markup.

1. Erstellen Sie eine Komponente, die die Eigenschaft `sling:resourceSuperType` zum Erben aus Folgendem verwendet:

   `/libs/granite/ui/components/foundation/form/field`

1. So überschreiben Sie das Skript:

   `render.jsp`

   In diesem Skript müssen Sie das Hypermedia-Markup (das heißt das erweiterte Markup mit Hypermedia-Angebot) erzeugen, damit der Client Anweisungen erhält, wie er mit dem erstellten Element interagieren soll.  Verwenden Sie dabei den Server-seitigen Code-Stil der Granite-Benutzeroberfläche.

   Bei der Anpassung *müssen* Sie nur festlegen, dass der (in `init.jsp` initialisierte) Formularwert wie folgt aus der Anforderung gelesen wird:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Weitere Informationen finden Sie im Abschnitt zur Implementierung von vorkonfigurierten Feldern der Granite-Benutzeroberfläche, beispielsweise `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Derzeit ist JSP die bevorzugte Methode für die Skripterstellung, da die Weitergabe von Daten von einer Komponente an die andere (die bei Formularen/Feldern häufig erfolgt) mit HTL schwierig zu bewerkstelligen ist.

## Erstellen der Client-Bibliothek für die Komponente {#creating-the-client-library-for-the-component}

Gehen Sie wie folgt vor, um der Komponente ein bestimmtes Client-seitiges Verhalten hinzuzufügen:

1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog`.
1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog` und definieren Sie darin Ihr `JS`/ `CSS` darin.

   Definieren Sie Ihr `JS`/ `CSS` in der Client-Bibliothek.

   >[!NOTE]
   >
   >Derzeit stellt die Granite-Benutzeroberfläche keine vorgefertigten Listener oder Hooks bereit, die Sie direkt zum Hinzufügen von JS-Verhalten verwenden können.  Um der JS-Komponente zusätzliches Verhalten hinzuzufügen, müssen Sie daher einen JS-Hook in einer benutzerdefinierten Klasse implementieren, die Sie der Komponente bei der Markup-Erzeugung zuweisen.
