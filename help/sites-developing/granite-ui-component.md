---
title: Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche
description: Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten, die für die Verwendung in Formularen entwickelt wurden, so genannte Felder
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e4820330-2ee6-4eca-83fd-462aa0b83647
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 22%

---

# Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche{#creating-a-new-granite-ui-field-component}

Die Granite-Benutzeroberfläche bietet eine Reihe von Komponenten, die für die Verwendung in Formularen entwickelt wurden. Diese werden als *fields* im Vokabular der Granite-Benutzeroberfläche. Die standardmäßigen Granite-Formularkomponenten sind unter verfügbar:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Diese Formularfelder der Granite-Benutzeroberfläche sind von besonderem Interesse, da sie für [Komponentendialogfelder](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Ausführliche Informationen zu Feldern finden Sie im Abschnitt [Dokumentation zur Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Verwenden Sie das Foundation-Framework der Granite-Benutzeroberfläche, um Granite-Komponenten zu entwickeln und/oder zu erweitern. Dies umfasst zwei Elemente:

* Server-seitig:

   * eine Sammlung von Foundation-Komponenten

      * foundation - modular, zusammenstellbar, schichtfähig, wiederverwendbar
      * Komponenten – Sling-Komponenten

   * Helfer zur Unterstützung der Anwendungsentwicklung

* clientseitig:

   * eine Sammlung von Clientlibs, die ein Vokabular bereitstellen (d. h. eine Erweiterung der HTML), um generische Interaktionsmuster über eine durch Hypermedia gesteuerte Benutzeroberfläche zu erreichen.

Die generische Komponente `field` der Granite-Benutzeroberfläche beinhaltet zwei wichtige Dateien:

* `init.jsp`: verarbeitet die generische Verarbeitung, Beschriftung und Beschreibung und stellt den Formularwert bereit, den Sie beim Rendern Ihres Felds benötigen.
* `render.jsp`: Hier wird das tatsächliche Rendering des Felds durchgeführt und muss für Ihr benutzerdefiniertes Feld überschrieben werden. Ist enthalten von `init.jsp`.

Siehe [Granite-UI-Dokumentation - Feld](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) für Details.

Beispiele finden Sie hier:

* `cqgems/customizingfield/components/colorpicker`

   * im Abschnitt [Codebeispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Da dieser Mechanismus JSP verwendet, werden i18n und XSS nicht nativ bereitgestellt. Dies bedeutet, dass Sie Ihre Zeichenfolgen internationalisieren und maskieren müssen. Das folgende Verzeichnis enthält die generischen Felder einer Standardinstanz, die Sie als Referenz verwenden können:
>
>`/libs/granite/ui/components/foundation/form`-Verzeichnis

## Erstellen des serverseitigen Skripts für die Komponente {#creating-the-server-side-script-for-the-component}

Das benutzerdefinierte Feld sollte das `render.jsp`-Skript nur überschreiben, wenn Sie das Markup für die Komponente angeben. Sie können die JSP (das Rendering-Skript) als Wrapper für Ihr Markup betrachten.

1. Erstellen Sie eine Komponente, die die `sling:resourceSuperType` -Eigenschaft, von der erbt wird:

   `/libs/granite/ui/components/foundation/form/field`

1. Überschreiben Sie das Skript:

   `render.jsp`

   Generieren Sie in diesem Skript das Hypermedia-Markup (d. h. das angereicherte Markup, das die Hypermedia-Bezahlbarkeit enthält), damit der Client weiß, wie er mit dem generierten Element interagieren kann. Dies sollte dem serverseitigen Kodierungsstil der Granite-Benutzeroberfläche entsprechen.

   Bei der Anpassung *müssen* Sie nur festlegen, dass der (in `init.jsp` initialisierte) Formularwert wie folgt aus der Anforderung gelesen wird:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Weitere Informationen finden Sie in der Implementierung von nativen Feldern der Granite-Benutzeroberfläche, z. B.: `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Derzeit ist JSP die bevorzugte Skriptmethode, da die Übergabe von Informationen von einer Komponente an eine andere (die häufig im Kontext von Formular/Feldern vorkommt) in HTL nicht einfach möglich ist.

## Erstellen der Client-Bibliothek für die Komponente {#creating-the-client-library-for-the-component}

Gehen Sie wie folgt vor, um der Komponente ein bestimmtes Client-seitiges Verhalten hinzuzufügen:

1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog`.
1. Erstellen Sie eine Client-Bibliothek der Kategorie `cq.authoring.dialog` und definieren Sie darin Ihr `JS`/ `CSS` darin.

   Definieren Sie Ihr `JS`/ `CSS` in der Client-Bibliothek.

   >[!NOTE]
   >
   >Derzeit bietet die Granite-Benutzeroberfläche keine nativen Listener oder Hooks, die Sie direkt zum Hinzufügen von JS-Verhalten verwenden können. Um Ihrer Komponente also zusätzliches JS-Verhalten hinzuzufügen, müssen Sie einen JS-Hook in eine benutzerdefinierte Klasse implementieren, die Sie dann während der Markup-Generierung Ihrer Komponente zuweisen.
