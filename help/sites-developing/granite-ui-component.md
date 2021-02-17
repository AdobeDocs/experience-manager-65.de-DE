---
title: Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche
seo-title: Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche
description: Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten für die Verwendung in Formularen, die in Granite als „Felder“ bezeichnet werden.
seo-description: Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten für die Verwendung in Formularen, die in Granite als „Felder“ bezeichnet werden.
uuid: cf26e057-4b0c-45f4-8975-2c658517f20e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 94b9eeee-aae3-4b28-9d6f-1be0e4acd982
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 91%

---


# Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche{#creating-a-new-granite-ui-field-component}

Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten für die Verwendung in Formularen, die im Granite-Vokabular als *Felder* bezeichnet werden. Die Standard-Formularkomponenten in Granite sind verfügbar unter:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Die Formularfelder der Granite-Benutzeroberfläche sind besonders interessant, da sie für [Komponenten-Dialoge](/help/sites-developing/developing-components.md) verwendet werden.

>[!NOTE]
>
>Vollständige Informationen zu Feldern finden Sie in der [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html).

Verwenden Sie das Foundation-Framework der Granite-Benutzeroberfläche zum Entwickeln bzw. Erweitern von Granite-Komponenten. Dieses umfasst zwei Elemente:

* Serverseitig:

   * eine Reihe von Foundation-Komponenten

      * Foundation – modular, zusammensetzbar, schichtfähig, wiederverwendbar
      * Komponenten – Sling-Komponenten
   * Hilfsprogramme für die Anwendungsentwicklung


* Clientseitig:

   * eine Sammlung von Client-Bibliotheken mit Vokabular (d. h. einer Erweiterung der HTML-Sprache) für generische Interaktionsmuster in einer von Hypermedia gesteuerten Benutzeroberfläche

Die generische Komponente `field` der Granite-Benutzeroberfläche beinhaltet zwei wichtige Dateien:

* `init.jsp`: Übernimmt die generische Verarbeitung sowie Beschriftung und Beschreibung und liefert den für das Rendern des Felds erforderlichen Formularwert.
* `render.jsp`: Übernimmt das tatsächliche Rendern des Felds und muss für das benutzerdefinierte Feld überschrieben werden; ist in `init.jsp` enthalten.

Weitere Informationen finden Sie in der [Dokumentation zur Granite-Benutzeroberfläche im Abschnitt zu Feldern](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html).

Beispiele finden Sie hier:

* `cqgems/customizingfield/components/colorpicker`

   * im Abschnitt [Codebeispiele](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Da dieser Mechanismus JSP verwendet, werden i18n und XSS nicht vorgefertigt bereitgestellt. Daher müssen Sie die Zeichenfolgen internationalisieren und durch Anführungszeichen schützen. Das folgende Verzeichnis enthält die generischen Felder aus einer Standardinstanz, die Sie als Referenz verwenden können:
>
>`/libs/granite/ui/components/foundation/form`.

## Erstellen des serverseitigen Skripts für die Komponente {#creating-the-server-side-script-for-the-component}

Das benutzerdefinierte Feld sollte das `render.jsp`-Skript nur überschreiben, wenn Sie das Markup für die Komponente angeben. Das JSP (d. h. das Render-Skript) ist dabei quasi der Wrapper für das Markup.

1. Erstellen Sie eine neue Komponente, die die `sling:resourceSuperType`-Eigenschaft zum Erben aus

   `/libs/granite/ui/components/foundation/form/field`

1. Überschreiben Sie das Skript:

   `render.jsp`

   In diesem Skript müssen Sie das Hypermedia-Markup (d. h. das erweiterte Markup mit Hypermedia-Angebot) erzeugen, damit der Client Anweisungen erhält, wie er mit dem erstellten Element interagieren soll. Verwenden Sie dabei den serverseitigen Code-Stil der Granite-Benutzeroberfläche

   Bei der Anpassung *müssen* Sie nur festlegen, dass der (in `init.jsp` initialisierte) Formularwert wie folgt aus der Anforderung gelesen wird:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Weitere Informationen finden Sie in der Implementierung der vordefinierten Granite-UI-Felder. zum Beispiel `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Derzeit ist JSP die bevorzugte Methode für die Skripterstellung, da die Weitergabe von Daten von einer Komponente an die andere (die bei Formularen/Feldern häufig erfolgt) mit HTL schwierig zu bewerkstelligen ist.

## Erstellen der Client-Bibliothek für die Komponente {#creating-the-client-library-for-the-component}

Gehen Sie wie folgt vor, um der Komponente ein bestimmtes clientseitiges Verhalten hinzuzufügen:

1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog`.
1. Erstellen Sie eine clientlib der Kategorie `cq.authoring.dialog` und definieren Sie `JS`/ `CSS` darin.

   Definieren Sie `JS`/ `CSS` innerhalb der clientlib.

   >[!NOTE]
   >
   >Derzeit stellt die Granite-Benutzeroberfläche keine vorgefertigten Listener oder Hooks bereit, die Sie direkt zum Hinzufügen von JS-Verhalten verwenden können. Um der JS-Komponente zusätzliches Verhalten hinzuzufügen, müssen Sie daher einen JS-Hook in einer benutzerdefinierten Klasse implementieren, die Sie der Komponente bei der Markup-Erzeugung zuweisen.

