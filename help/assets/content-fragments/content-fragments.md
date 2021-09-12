---
title: Arbeiten mit Inhaltsfragmenten
description: Erfahren Sie, wie Sie mit Inhaltsfragmenten in Adobe Experience Manager (AEM) seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und verwenden können, die sich ideal für die Headless-Bereitstellung eignen.
feature: Content Fragments
role: User
exl-id: 0ee883c5-0cea-46b7-a759-600b8ea3bc3e
source-git-commit: b5cf18d8e83786a23005aadf8aafe43d006a2e67
workflow-type: tm+mt
source-wordcount: '1989'
ht-degree: 94%

---

# Arbeiten mit Inhaltsfragmenten {#working-with-content-fragments}

Mit Adobe Experience Manager (AEM) können Sie mit Inhaltsfragmenten seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und [veröffentlichen](/help/sites-authoring/content-fragments.md) Diese ermöglichen die Vorbereitung von Inhalten für die Verwendung an mehreren Orten/über mehrere Kanäle, ideal für die Headless-Bereitstellung.

Inhaltsfragmente enthalten strukturierten Inhalt:

* Sie basieren auf einem [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md), das eine Struktur für das daraus entstehende Fragment vordefiniert.
* Die Struktur kann variieren:
   * Einfach
      * Beispiel: ein einzelnes, mehrzeiliges Textfeld.
      * Kann verwendet werden, um einfache Inhalte für die Verwendung bei der Seitenerstellung vorzubereiten.
   * Komplex
      * Eine Kombination aus vielen Feldern unterschiedlicher Datentypen, u. a. Text, Zahl, boolesch, Daten und Zeit.
      * Kann entweder zur Vorbereitung von strukturierteren Inhalten für die Seitenerstellung oder zur Bereitstellung für Ihr Programm verwendet werden.
   * Verschachtelt
      * Mit den verfügbaren Referenzdatentypen können Sie Ihre Inhalte verschachteln.
      * Wird in der Regel für die Bereitstellung an Ihr Programm verwendet.

Mit der Sling Model (JSON)-Exportfunktion der AEM-Kernkomponenten können Inhaltsfragmente auch im JSON-Format bereitgestellt werden. Diese Form der Bereitstellung:

* bietet Ihnen die Möglichkeit, mithilfe der Komponente zu bestimmen, welche Fragmentelemente bereitgestellt werden sollen
* ermöglicht durch das Hinzufügen mehrerer Inhaltsfragment-Kernkomponenten auf der für die API-Bereitstellung verwendeten Seite eine Bereitstellung in größerem Umfang

Hier und auf den folgenden Seiten werden die Aufgaben zum Erstellen, Konfigurieren, Verwalten und Verwenden von Inhaltsfragmenten beschrieben:

* [Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md) – Aktivieren, Erstellen und Definieren Ihrer Modelle
* [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md) – Erstellen Sie Ihre Inhaltsfragmente; anschließend können Sie sie bearbeiten, veröffentlichen und Verweise erstellen
* [Varianten – Erstellen von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-variations.md) – Erstellen Sie das Inhaltsfragment und erstellen Sie Varianten der Vorlage
* [Markdown](/help/assets/content-fragments/content-fragments-markdown.md) – Verwendung der Markdown-Syntax für Ihr Fragment
* [Verwenden verknüpfter Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md) – Hinzufügen verknüpfter Inhalte
* [Metadaten – Fragmenteigenschaften](/help/assets/content-fragments/content-fragments-metadata.md) – Anzeigen und Bearbeiten der Fragmenteigenschaften
* Verwenden Sie [Inhaltsfragmente zusammen mit GraphQL, um Inhalte](/help/assets/content-fragments/content-fragments-graphql.md) für die Verwendung in Ihren Programmen bereitzustellen. Dabei kann es Ihnen helfen, die [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md) in der Vorschau anzeigen.

>[!NOTE]
>
>Diese Seiten können in Verbindung mit Folgendem gelesen werden:
>
>* [Seitenbearbeitung mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md).
>* [Anpassen und Erweitern von Inhaltsfragmenten](/help/sites-developing/customizing-content-fragments.md)
>* [Inhaltsfragmente, die Komponenten für die Wiedergabe konfigurieren](/help/sites-developing/content-fragments-config-components-rendering.md)
>* [Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/assets-api-content-fragments.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md)


Die Anzahl der Kommunikationskanäle nimmt jährlich zu. Typischerweise beziehen sich Kanäle auf den Bereitstellungsmechanismus, und zwar wie folgt:

* Physische Kanäle, z. B. Desktop, Mobilgerät
* Bereitstellung in einem physischen Kanal, z. B. als „Produktdetailseite“ oder „Produktkategorieseite“ für Desktops bzw. als „mobiles Internet“ oder „Mobile App“ für mobile Geräte

Wahrscheinlich möchten Sie jedoch nicht dieselben Inhalte für alle Kanäle verwenden. Daher müssen Sie Ihre Inhalte je nach Kanal optimieren.

Inhaltsfragmente ermöglichen Ihnen Folgendes:

* Erwägen, wie sich Zielgruppen effizient kanalübergreifend erreichen lassen
* Kanalneutrale redaktionelle Inhalte erstellen und verwalten
* Inhaltspools für mehrere Kanäle erstellen
* Inhaltsvarianten für bestimmte Kanäle entwerfen
* Bilder durch Einfügen von Assets (Fragmente mit gemischten Medien) zu Texten hinzufügen
* Erstellen Sie verschachtelte Inhalte, um die Komplexität Ihrer Daten widerzuspiegeln.

Diese Inhaltsfragmente können dann zusammengestellt werden, um Erlebnisse über verschiedene Kanäle bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-authoring/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte, mit denen u. a. auf strukturierte Daten wie Texte, Zahlen und Daten zugegriffen werden kann. Es handelt sich um reine Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.

>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

>[!NOTE]
>
>Vor AEM 6.3 wurden Inhaltsfragmente mit Vorlagen anstelle von Modellen erstellt. Vorlagen sind nicht mehr zum Erstellen neuer Fragmente verfügbar, aber alle mit einer solchen Vorlage erstellten Fragmente werden weiterhin unterstützt.

## Inhaltsfragmente und Content Services {#content-fragments-and-content-services}

Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Web-Seiten hinweg generalisiert werden.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Web-Seiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Single Page Applications (SPA)
* native Mobile Apps
* weitere AEM-externe Kanäle und Touchpoints

Der Versand erfolgt im JSON-Format mit dem JSON-Exporter.

AEM-Inhaltsfragmente können zur Beschreibung und Verwaltung strukturierter Inhalte verwendet werden. Strukturierter Inhalt wird in Modellen definiert, die eine Vielzahl von Inhaltstypen enthalten können, darunter Text, numerische Daten, boolesche Ausdrücke, Datum und Uhrzeit und mehr.

Zusammen mit der JSON-Exportfunktion der AEM-Kernkomponenten kann dieser strukturierte Inhalt dann zur Bereitstellung von AEM-Inhalten auf anderen Kanälen als AEM-Seiten verwendet werden.

<!--
>[!NOTE]
>
>See [Headless and AEM](/help/implementing/developing/headless/introduction.md) for an introduction to Headless Development for AEM Sites.
-->

>[!NOTE]
>
>AEM unterstützt auch die Übersetzung von Fragmentinhalten.

<!--
>[!NOTE]
>
>AEM also supports the translation of fragment content. See [Translating Assets](/help/assets/translate-assets.md) for further information.
-->

## Inhaltstyp {#content-type}

Inhaltsfragmente werden:

* als **Assets** gespeichert:

   * Inhaltsfragmente (und deren Varianten) können in der Konsole **Assets** erstellt und verwaltet werden.
   * Im Inhaltsfragment-Editor erstellt und bearbeitet.

* im [Seiteneditor anhand der Komponente Inhaltsfragment verwendet](/help/sites-authoring/content-fragments.md) (Verweiskomponente):

   * Die Komponente **Inhaltsfragment** steht für Seitenautoren zur Verfügung. Sie ermöglicht das Erstellen von Verweisen für sowie das Bereitstellen des erforderlichen Inhaltsfragments im HTML- oder JSON-Format.

* Abrufbar mit der [AEM-GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md).

Inhaltsfragmente sind eine Inhaltsstruktur mit folgenden Eigenschaften:

* Sie weisen kein Layout oder Design auf (gewisse Textformatierung ist im Rich-Text-Modus möglich).
* Enthalten mindestens einen [Bestandteil](#constituent-parts-of-a-content-fragment).
* Kann Bilder [enthalten oder mit Bildern verbunden sein](#fragments-with-visual-assets).
* Bei Referenzierung auf einer Seite können [Übergangsinhalte](#in-between-content-when-page-authoring-with-content-fragments) verwendet werden.

* Sie sind unabhängig vom Bereitstellungsmechanismus (d. h. Seite, Kanal).

### Fragmente mit visuellen Assets {#fragments-with-visual-assets}

Um Autoren eine bessere Kontrolle über eigene Inhalte zu ermöglichen, können Bilder zu einem Inhaltsfragment hinzugefügt und/oder darin integriert werden.

Assets können auf verschiedene Weise mit einem Inhaltsfragment verwendet werden – mit jeweiligen Vorteilen:

* In ein Fragment **eingefügte Assets** (Fragmente mit gemischten Medien)

   * sind ein integraler Bestandteil des Fragments (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment));
   * definieren die Position des Assets;
   * Weitere Informationen finden Sie unter [Einfügen von Assets in Fragmente](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) im Fragment-Editor.

   >[!NOTE]
   >
   >Die in das Inhaltsfragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz verbunden. Beim Hinzufügen des Fragments zu einer Seite werden diese Assets in Beziehung zu diesem Absatz verschoben, wenn Übergangsinhalte hinzugefügt werden.

* **Zugehörige Inhalte**

   * sind zwar mit einem Fragment verbunden, stellen aber keinen festen Bestandteil des Fragments dar (siehe [Bestandteile von Inhaltsfragmenten](#constituent-parts-of-a-content-fragment));
   * ermöglichen eine gewisse Flexibilität bei der Positionierung;
   * sind problemlos verfügbar (als Übergangsinhalte), wenn das Fragment auf einer Seite verwendet wird;
   * weitere Informationen finden Sie unter [Zugehörige Inhalte](/help/assets/content-fragments/content-fragments-assoc-content.md).

* Im Seiten-Editor verfügbare Assets im **Asset-Browser**

   * bieten vollständige Flexibilität bei der Asset-Auswahl;
   * ermöglichen eine gewisse Flexibilität bei der Positionierung;
   * liefern nicht die Möglichkeit, für ein bestimmtes Fragment genehmigt zu werden;

<!--
  * See [Assets Browser](/help/sites-authoring/environment-tools.md#assets-browser) for more information.
-->

### Bestandteile von Inhaltsfragmenten {#constituent-parts-of-a-content-fragment}

Inhaltsfragment-Assets setzen sich aus folgenden Teilen zusammen (entweder direkt oder indirekt):

* **Fragmentelementen**

   * Elemente korrelieren mit den Datenfeldern, die Inhalte enthalten.
   * Sie verwenden ein Inhaltsmodell, um das Inhaltsfragment zu erstellen. Die im Modell angegebenen Elemente (Felder) definieren die Struktur des Fragments. Bei diesen Elementen (Feldern) gibt es verschiedene Datentypen.

* **Fragmentabsätze**

   * Textblöcke, häufig mehrzeilig, die als einzelne Entitäten getrennt sind.

   * In den Modi [Rich-Text](/help/assets/content-fragments/content-fragments-variations.md#rich-text) und [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kann ein Absatz als Kopfzeile formatiert werden. In diesem Fall gehören dieser und der folgende Absatz als eine Einheit zusammen.

   * Ermöglichen die Inhaltssteuerung während der Seitenbearbeitung

* **In ein Fragment eingefügte Assets (Fragmente mit gemischten Medien)**

   * Assets (Bilder), die in das eigentliche Fragment eingefügt und als interne Inhalte eines Fragments verwendet werden;
   * sind in das Absatzsystem des Fragments eingebettet;
   * können formatiert werden, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-authoring/content-fragments.md);
   * können nur über den Fragment-Editor einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden; diese Aktionen können nicht im Seiten-Editor durchgeführt werden;
   * können nur durch das [Rich-Text-Format im Fragment-Editor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) einem Fragment hinzugefügt, daraus gelöscht oder darin verschoben werden;
   * können nur zu mehrzeiligen Textelementen hinzugefügt werden (beliebiger Fragmenttyp);
   * werden mit dem vorangehenden Text (Absatz) verbunden;

      >[!CAUTION]
      >
      >Assets können (versehentlich) aus dem Fragment gelöscht werden, wenn in das Nur-Text-Format gewechselt wird.

      >[!NOTE]
      >
      >Assets können auch als [zusätzlicher (Übergangs) Inhalt](/help/sites-authoring/content-fragments.md#using-associated-content) hinzugefügt werden, wenn ein Fragment auf einer Seite verwendet wird (bei Nutzung von zugehörigen Inhalten oder Assets aus dem Assets-Browser).

* **Zugehörige Inhalte**

   * Hierbei handelt es sich um externen Inhalt für das Fragment, der jedoch von redaktioneller Relevanz ist. In der Regel sind dies Bilder, Videos oder andere Fragmente.
   * Die einzelnen Assets innerhalb der Sammlung können mit dem Fragment im Seiten-Editor verwendet werden, wenn es einer Seite hinzugefügt wird. Zugehörige Inhalte sind also optional, abhängig von den Anforderungen des jeweiligen Kanals.
   * Die Assets sind [mit Fragmenten über Sammlungen verknüpft](/help/assets/content-fragments/content-fragments-assoc-content.md). Mithilfe verknüpfter Sammlungen kann der Autor entscheiden, welche Assets beim Bearbeiten einer Seite verwendet werden sollen.

      * Sammlungen können mit Fragmenten als Standardinhalt oder von Autoren während der Fragmentbearbeitung verbunden werden.
      * [Asset (DAM)-Sammlungen](/help/assets/manage-collections.md) sind die Basis für die zugehörigen Inhalte von Fragmenten.
   * Sie können auch das eigentliche Fragment zu einer Sammlung hinzufügen und so die Nachverfolgung unterstützen.

* **Fragmentmetadaten**

   * Verwendung der [Assets-Metadatenschemata](/help/assets/metadata-schemas.md)
   * Tag-Erstellung möglich:

      * Beim Erstellen und Bearbeiten des Fragments
      * Oder später:

         * Durch Anzeigen/Bearbeiten der **Fragmenteigenschaften** über die Konsole
         * Durch Bearbeiten der **Metadaten** im Fragment-Editor

   >[!CAUTION]
   >
   >Profile für die Metadatenverarbeitung sind nicht für Inhaltsfragmente geeignet.

* **Vorlage**

   * Integraler Bestandteil des Fragments:

      * Jedes Inhaltsfragment hat eine Vorlageninstanz.
      * Die Vorlage kann gelöscht werden.
   * Auf die primäre Vorlage kann über den Fragment-Editor unter **[Varianten](/help/assets/content-fragments/content-fragments-variations.md)** zugegriffen werden.
   * Die Vorlage ist keine Variante an sich, sondern die Grundlage aller Varianten.


* **Varianten**

   * Ausgabedarstellungen von Fragmenttext, eigens zu redaktionellen Zwecken. Diese können mit einem Kanal verbunden sein, doch ist dies nicht obligatorisch; auch für lokale Ad-hoc-Änderungen geeignet;
   * werden als Kopien von der **Vorlage** erstellt, können dann aber nach Bedarf bearbeitet werden; gewöhnlich kommt es zu einer Inhaltsüberlappung zwischen den Varianten;
   * können beim Erstellen von Fragmenten definiert werden;
   * werden im Fragment gespeichert, um die Streuung von Inhaltskopien zu vermeiden;
   * können mit der Vorlage [synchronisiert](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) werden, wenn der Vorlageninhalt aktualisiert wurde;
   * können [zusammengefasst](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) werden, um Text schnell auf eine vordefinierte Länge zu kürzen;
   * sind auf der Registerkarte [Varianten](/help/assets/content-fragments/content-fragments-variations.md) des Fragment-Editors verfügbar.

### Übergangsinhalte bei der Seitenerstellung mit Inhaltsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Übergangsinhalte:

* Sind für die Verwendung im Seiteneditor bei der Arbeit mit Inhaltsfragmenten verfügbar.
* Hierbei handelt es sich um [zusätzlichen Inhalt, der im Fluss eines Fragments hinzugefügt wird](/help/sites-authoring/content-fragments.md#adding-in-between-content), sobald dieses auf einer Seite verwendet/referenziert wird.
* Sind für die Verwendung im [Seiteneditor bei der Arbeit mit Inhaltsfragmenten](/help/sites-authoring/content-fragments.md) verfügbar.
* Übergangsinhalte können zu jedem beliebigen Fragment hinzugefügt werden, in dem nur ein Element sichtbar ist.
* Zugehörige Inhalte sowie Assets und/oder Komponenten des entsprechenden Browsers können eingesetzt werden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

### Voraussetzungen für Fragmente {#required-by-fragments}

Das Erstellen von Inhaltsfragmenten erfordert Folgendes:

* **Inhaltsmodelle**

   * werden [mithilfe des Konfigurations-Browsers aktiviert](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * werden [mithilfe von Tools erstellt](/help/assets/content-fragments/content-fragments-models.md).
   * Erforderlich zum [Erstellen eines Fragments](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definiert die Struktur eines Fragments (Titel, Inhaltselemente, Tag-Definitionen).
   * Inhaltsmodelldefinitionen erfordern einen Titel und ein Datenelement. Alle weiteren Elemente sind optional.
   * Das Modell kann Standardinhalte definieren – sofern zutreffend.
   * Autoren können die definierte Struktur nicht ändern, wenn sie den Fragmentinhalt erstellen.
   * Änderungen, die nach dem Erstellen von abhängigen Inhaltsfragmenten an einem Modell vorgenommen wurden, können sich auf diese Inhaltsfragmente auswirken.

Um Ihre Inhaltsfragmente zum Erstellen von Seiten zu verwenden, benötigen Sie außerdem Folgendes:

* **Inhaltsfragment-Komponente**

   * Hilft bei der Bereitstellung des Fragments im HTML- und/oder JSON-Format.
   * Erforderlich zum [Referenzieren des Fragments auf einer Seite](/help/sites-authoring/content-fragments.md).
   * Zuständig für das Layout und die Bereitstellung eines Fragments, d. h. Kanäle.
   * Fragmente benötigen eine oder mehrere dedizierte Komponenten zur Definition des Layouts sowie zur Bereitstellung einiger oder aller Elemente/Varianten und zugehörigen Inhalte.
   * Durch Ziehen eines Fragments auf eine Seite während der Bearbeitung wird die erforderliche Komponente automatisch zugewiesen.

## Anwendungsbeispiel {#example-usage}

Ein Fragment samt seinen Elementen und Varianten kann zur Erstellung von kohärentem Inhalt für verschiedene Kanäle verwendet werden. Beim Entwurf eines Fragments muss berücksichtigt werden, welche Elemente wo verwendet werden.
