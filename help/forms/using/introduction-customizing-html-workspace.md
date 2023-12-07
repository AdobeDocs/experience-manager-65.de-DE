---
title: Einführung zur Anpassung von AEM Forms Workspace
description: Eine kurze Einführung mit konzeptionellen und technischen Informationen zur Anpassung von LiveCycle AEM Forms Workspace für die Prozessverwaltung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: b183d42f-343c-4acb-bc73-f80ad72e54df
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 30%

---

# Einführung zur Anpassung von AEM Forms Workspace{#introduction-to-customizing-aem-form-workspace}

AEM Forms Workspace bietet Funktionen zum Ändern der Darstellung und der Funktionen der Benutzeroberfläche. Die Anpassungen zum Ändern des Stils, des Layouts, der Formatierung, des Branding und der Kernfunktion werden unten beschrieben.

![cu_customized_workspace_example](assets/cu_customized_workspace_example.png)

Beispiel für einen benutzerdefinierten Arbeitsbereich

## Arten von Anpassungen {#types-of-customizations}

AEM Forms Workspace unterstützt viele Anpassungen, mit denen das Layout, die Darstellung, die Funktionalität und andere Aspekte der Benutzeroberfläche aktualisiert werden können. Die Anpassungen umfassen die Aktualisierung einer oder mehrerer der folgenden Elemente:

* Erscheinungsbild der Benutzeroberfläche
* Funktionalität mithilfe semantischer Anpassungen
* Wiederverwenden von HTML-Komponenten in anderen Anwendungen

### Änderungen an der Benutzeroberfläche {#user-interface-changes}

Sie können das Aussehen, Layout und andere Darstellungsfaktoren von AEM Forms Workspace ändern. Ändern Sie den Workspace durch Anpassen der CSS- und HTML-Vorlagen und JavaScript™-Dateien. Alle Standarddateien werden in der Standardinstallation bereitgestellt.

Die am häufigsten angewandten Schritte werden in [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) beschrieben. Spezifische Beispiele für solche Anpassungen, einschließlich der detaillierten Schritte, finden Sie in den entsprechenden Artikeln am Ende dieses Artikels.

#### Grundlagen zum Stylesheet {#understanding-the-style-sheet}

Machen Sie sich vor dem Anpassen von Workspace mit dem Standard-Stylesheet vertraut, das unter /libs/ws/css/style.css mit AEM Forms bereitgestellt wird.

Um den Arbeitsbereich anzupassen, sollten Sie sich mit dem vorhandenen Stylesheet style.css im Ordner /libs/ws/css vertraut machen. Nachfolgend werden einige wichtige Komponenten beschrieben.

<table>
 <tbody>
  <tr>
   <th><p>CSS-Element</p> </th>
   <th><p>Änderung der Benutzeroberflächenkomponente</p> </th>
  </tr>
  <tr>
   <td><p>#header</p> </td>
   <td><p>Header von AEM Forms Workspace</p> </td>
  </tr>
  <tr>
   <td><p>.categoryList</p> </td>
   <td><p>Kategorienliste</p> </td>
  </tr>
  <tr>
   <td><p>.categoryList .header</p> </td>
   <td><p>Kopfzeile der Kategorienliste</p> </td>
  </tr>
  <tr>
   <td><p>.categories, .filters</p> </td>
   <td><p>Platz unterhalb der Kategorienliste</p> </td>
  </tr>
  <tr>
   <td><p>.category, .filter</p> </td>
   <td><p>Kategorie</p> </td>
  </tr>
  <tr>
   <td><p>.category:hover, .category.selected, .filter:hover, .filter.selected</p> </td>
   <td><p>Ausgewählte Kategorie und Mauszeiger über die Kategorie</p> </td>
  </tr>
  <tr>
   <td><p>categoryListBar .tool, categoryListBar .content</p> </td>
   <td><p>Prozessseite starten (geschlossene Kategorienliste)</p> </td>
  </tr>
  <tr>
   <td><p>filterListBar .tool, filterListBar .content</p> </td>
   <td><p>Aufgabenseite (geschlossene Filterliste)</p> </td>
  </tr>
  <tr>
   <td><p>processNameListBar .tool, processNameListBar .content</p> </td>
   <td><p>Tracking-Seite (geschlossene Prozessnamenliste)</p> </td>
  </tr>
  <tr>
   <td><p>.startPointList, .tasklist</p> </td>
   <td><p>Die Startpunktliste oder die Aufgabenliste</p> </td>
  </tr>
  <tr>
   <td><p>.startPointList .header, .tasklist .header</p> </td>
   <td><p>Die Kopfzeile einer Startpunktliste oder einer Aufgabenliste</p> </td>
  </tr>
  <tr>
   <td><p>.startpoint.selected, .task.selected</p> </td>
   <td><p>Der ausgewählte Startpunkt oder die ausgewählte Aufgabe</p> </td>
  </tr>
  <tr>
   <td><p>.startpoint.selected .description, .task.selected .description</p> </td>
   <td><p>Beschreibung des ausgewählten Startpunkts oder der ausgewählten Aufgabe</p> </td>
  </tr>
  <tr>
   <td><p>#taskarea</p> </td>
   <td><p>Der Aufgabenbereich</p> </td>
  </tr>
  <tr>
   <td><p>#header .dropdown</p> </td>
   <td><p>Benutzer-Dropdown in der Kopfzeile</p> </td>
  </tr>
  <tr>
   <td><p>.sortDrop dd ul</p> </td>
   <td><p>Dropdown-Liste "Sortieraufgabe"</p> </td>
  </tr>
 </tbody>
</table>

#### CSS {#css}

Das Erscheinungsbild von AEM Forms Workspace wird aus einer CSS übernommen. Durch die Anpassung des CSS können Sie die Darstellungssemantik von Workspace wie Schriftarten, Farben, Branding und Layout ändern.

Die wichtigsten Schritte zur CSS-Anpassung sind:

* Erstellen Sie eine CSS-Datei.
* Fügen Sie diesem CSS Stilelemente hinzu. Weitere Informationen finden Sie unter Grundlagen zu CSS-Stilen .
* Aktualisieren Sie die betreffenden Verweise in der Datei `html.jsp`.

Die ausführlichen Schritte zur Umsetzung dieser Anpassungen finden Sie unter [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md). Die mit AEM Forms Workspace bereitgestellte CSS-Datei ist unter /libs/ws/css/ zu finden. Verwenden Sie für diese CSS-Anpassungen das [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p). Spezifische Beispiele für CSS-bezogene Anpassungen finden Sie in den entsprechenden Hilfethemen am Ende dieses Artikels.

#### Bild {#image}

Sie können AEM Forms Workspace anpassen, um Avatare von Benutzern oder das Logo Ihres Unternehmens hinzuzufügen. Verwenden Sie für diese Anpassungen [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).

Die wichtigsten Schritte zur Anpassung der Bilder sind:

* WebDAV installieren und konfigurieren
* Fügen Sie neue Bilder hinzu.
* Fügen Sie neue Stile hinzu, die den hinzugefügten Bildern entsprechen.
* Stellen Sie eine Verknüpfung zu der neuen CSS-Datei in der Datei `html.jsp` her.

Um mit der Anpassung der Bilder in AEM Forms Workspace zu beginnen, führen Sie die [Generischen Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) aus. Spezifische Beispiele für bildbezogene Anpassungen finden Sie in den entsprechenden Hilfethemen am Ende dieses Artikels.

#### HTML-Vorlage {#html-template}

HTML-Vorlagen dienen dazu, das Erscheinungsbild und Layout der Benutzeroberfläche des Arbeitsbereichs zu definieren. Durch die Aktualisierung der Standard-HTML-Vorlagen können Sie die Standard-Benutzeroberfläche des Layouts anpassen.

Die wichtigsten Schritte zur Anpassung der HTML-Vorlage sind:

* Erstellen Sie in einem vom Benutzer erstellten Ordner Kopien der erforderlichen Standarddateien.
* Fügen Sie neue Vorlagen im benutzerdefinierten Ordner hinzu.
* Nehmen Sie relevante Aktualisierungen an den kopierten Dateien vor, z. B. den Pfad der neuen Vorlage.

Spezifische Beispiele für solche Anpassungen finden Sie in den Hilfethemen am Ende dieses Artikels. Wählen Sie zwischen [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) oder [Entwicklungspaket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), abhängig von der anzupassenden Vorlage.

### Semantische Änderungen {#semantic-changes}

Verändern Sie den JavaScript Quell-Code, um die AEM Forms Workspace-Funktionen zu ändern. Änderungen an der Kernfunktion werden als Semantische Änderungen bezeichnet. Sie ändern Modelle, Ansichten und Vorlagen, die im Quellcode von AEM Forms Workspace bereitgestellt werden.

Die wesentlichen Schritte zur Änderung der Semantik und damit zur Änderung der Funktionen von AEM Forms Workspace sind:

* Erstellen Sie in einem vom Benutzer erstellten Ordner Kopien der entsprechenden Standarddateien.
* Fügen Sie im benutzerdefinierten Ordner neue Modelle und Ansichten hinzu.
* Nehmen Sie relevante Aktualisierungen vor, z. B. Aktualisieren von Pfaden neu hinzugefügter Modelle und Ansichten in den standardmäßigen JavaScript-Dateien.
* Minimieren Sie das Paket zur Leistungsoptimierung.

Weitere grundlegende Informationen zu den Komponenten, die Teil des Quellcodes sind, finden Sie unter [Beschreibung wiederverwendbarer Komponenten](/help/forms/using/description-reusable-components.md). Verwenden Sie für diese Anpassungen das Entwicklungspaket .

### Wiederverwendbare Komponenten {#reusable-components}

Da AEM Forms Workspace eine komponentenbasierte Software ist, lässt sich diese einfach anpassen und wiederverwenden. Integrieren Sie mühelos die Workspace-Komponenten in Ihre Webanwendungen.

Weitere grundlegende Informationen finden Sie unter der [Beschreibung wiederverwendbarer Komponenten](/help/forms/using/description-reusable-components.md). Anweisungen zum Verwenden der Komponenten sind unter [Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen](/help/forms/using/description-reusable-components.md) aufgeführt.

## Erstellen von AEM Forms Workspace-Code {#building-html-workspace-code}

### SDK-Paket {#sdk-package}

Das Paket enthält den Quellcode von AEM Forms Workspace. Das Paket ist verfügbar unter `[LC root]\sdk\html-workspace\adobe-lc-workspace-src.zip`.

Sie ist in erster Linie für Anpassungen vorgesehen, da sie folgende Funktionen bietet:

* CRX-Pakete für Ship-, Debug- und Dev-Profile (siehe unten unter [CRX-Pakete](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p)).
* Minimierte Version des benutzerdefinierten Codes (für semantische Änderungen).

#### WS-Inhalt {#ws-content}

* client-pkg:

   * src - Enthält Artefakte, die zum Erstellen von CRX-Knoten erforderlich sind.
   * pom.xml - Skript zum Erstellen von Bereitstellungspaketen für verschiedene Profile WS-Bereitstellungspaket

* client-html:

   * assembly – Enthält die zip.xml, die vom Skript zum Erstellen von AEM Forms Workspace SDK verwendet wird.
   * src/main/webapp -

      * css - Enthält Stylesheets für AEM Forms Workspace.
      * images - Enthält Bilder, die in AEM Forms Workspace verwendet werden.
      * js:

         * libs - Enthält alle Bibliotheken von Drittanbietern, die in AEM Forms Workspace verwendet werden.
         * licenses - Enthält Lizenzen für HTML- und JS-Dateien und -Code, um diese Lizenzen den jeweiligen Quelldateien vorzustellen.
         * minifier – Wird für die Kombination, Minimierung und Verschleierung des benutzerdefinierten JavaScript-Codes verwendet.
         * resourcejs_optimizer – Wird für die Kombination, Minimierung und Verschleierung der JavaScript-Quelle verwendet.
         * resource_generator – Wird für die Generierung von register.js und modelcontrollerpath.js verwendet.
         * runtime:

            * initializer - Enthält initializer.js , das zum Initialisieren von Backbone-Ansichten und -Modellen verwendet wird, die in AEM Forms Workspace verwendet werden.
            * models - Enthält Backbone-Modelle aller Komponenten, die in AEM Forms Workspace vorhanden sind.
            * routes – Enthält JavaScript-Dateien und HTML-Dateien, die den Startvorgang, Aufgaben, Verfolgung und Einstellungen in AEM Forms Workspace laden.
            * services - Enthält in AEM Forms Workspace verwendete service.js. Alle Server-Aufrufe erfolgen über service.js.
            * templates - Enthält alle Vorlagen, d. h. HTML-Dateien aller Ansichten in AEM Forms Workspace.
            * util - Enthält alle in AEM Forms Workspace verwendeten Dienstprogrammdateien (JavaScript).
            * views - Enthält Backbone-Ansichten aller Komponenten in AEM Forms Workspace.

         * main.js
         * router.js

      * libs/ws: pdf.html und pluginPing.pdf werden zum Laden von PDF-Formularen in AEM Forms Workspace verwendet. WSNextAdapter.swf wird verwendet, um SWF-Formulare und -Guides in AEM Forms Workspace zu laden.
      * locales:

         * de-DE - Enthält translation.json für Deutsch.
         * en-US - Enthält translation.json für Englisch.
         * fr-FR - Enthält translation.json für Französisch.
         * ja-JP - Enthält translation.json für Japanisch.
         * html.jsp - Enthält Code, um das aktuelle Browsergebietsschema zu ermitteln.

      * html.jsp
      * GET.jsp

### CRX-Paket {#crx-package}

Das CRX-Paket kann auf dem CRX™-Repository bereitgestellt werden. Diese sind verfügbar unter `[LC root]\crx-repository\install\adobe-lc-workspace-pkg.zip`.

Dieses Paket kann mithilfe der drei folgenden Profile erstellt werden, die nachstehend beschrieben werden.

| **Profil** | **Beschreibung** | **Nutzung** |
|---|---|---|
| Ship-Profil | Dieses Profil erstellt ein CRX-Paket der kleinstmöglichen Größe mithilfe der Minimierung. Dieses Paket ist das effizienteste. Alle JavaScript™-Dateien werden kombiniert und in eine JS-Datei minimiert. | Verwenden Sie dieses Profil, wenn keine weiteren semantischen Änderungen in JS-Dateien erforderlich sind. |
| Debug-Profil | Dieses Profil erstellt ein mäßig effizientes CRX-Paket. Die Größe des Pakets ist etwas größer als das mit dem Ship-Profil erstellte Paket. Dieses Paket enthält die meisten JavaScript-Dateien, die zu einer JS-Datei zusammengefasst sind. | Verwenden Sie dieses Profil zum Debugging. |
| Entwicklungsprofil | Dieses Profil erstellt ein CRX-Paket der größtmöglichen Größe. Alle JavaScript-Dateien sind separat verfügbar, da sie sich im SDK-Paket befinden. | Verwenden Sie dieses Profil, wenn Sie semantische Änderungen einbinden. |

#### Ship-Profil {#ship-profile}

#### Befehl {#command}

* mvn clean -P Ship install auf client-pkg Ordner des Quellpakets, das an den Client geliefert wurde.
* Befehlsausführung von Ship-Profil funktioniert nur auf einer 64-Bit-JVM.

#### WS-Inhalt {#ws-content-1}

* css - Enthält style.css, ie.css und jquery-ui.css.
* images - Enthält alle Bilder.
* js:

   * libs:

      * require - Enthält require.js.
      * jqueryui - Enthält jquery.ui.datepicker.ja.js.

   * runtime:

      * templates - Enthält alle Vorlagen, d. h. HTML-Dateien aller Komponenten in AEM Forms Workspace.

   * main.js (kombiniert, minimiert und verschleiert).
   * registry.js

* libs:

   * ws - Enthält pluginPing.pdf, pdf.html und WSNextAdapter.swf.

* Locale - Enthält .content.xml.
* locales:

   * de-DE - Enthält translation.json für Deutsch.
   * en-US - Enthält translation.json für Englisch.
   * fr-FR - Enthält translation.json für Französisch.
   * ja-JP - Enthält translation.json für Japanisch.
   * html.jsp - Enthält Code, um das aktuelle Browsergebietsschema zu ermitteln.

* Index - Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Debug-Profil {#debug-profile}

#### Befehl {#command-1}

* mvn clean -P Debug install on client-pkg
* Die Befehlsausführung des Debug-Profils funktioniert nur auf 64-Bit-JVM.

#### WS-Inhalt {#ws-content-2}

* css - Enthält style.css, ie.css und jqueri-ui.css.
* images - Enthält alle Bilder.
* js:

   * libs:

      * require - Enthält require.js.
      * jqueryui - Enthält jquery.ui.datepicker.ja.js.

   * runtime:

      * templates - Enthält alle Vorlagen, d. h. HTML-Dateien aller Komponenten in AEM Forms Workspace.

   * main.js (kombiniert).
   * registry.js

* libs:

   * ws - Enthält pluginPing.pdf, pdf.html und WSNextAdapter.swf.

* Locale - Enthält .content.xml.
* locales:

   * de-DE - Enthält translation.json für Deutsch.
   * en-US - Enthält translation.json für Englisch.
   * fr-FR - Enthält translation.json für Französisch.
   * ja-JP - Enthält translation.json für Japanisch.
   * html.jsp - Enthält Code, um das aktuelle Browsergebietsschema zu ermitteln.

* Index - Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Entwicklungsprofil {#dev-profile}

#### Befehl {#command-2}

mvn clean -P Dev install on client-pkg

#### WS-Inhalt {#ws-content-3}

* css - Enthält style.css, ie.css und jqueri-ui.css.
* images - Enthält alle Bilder.
* js:

   * libs - Enthält alle in AEM Forms Workspace verwendeten Bibliotheken.
   * require - Enthält require.js
   * jqueryui - Enthält jquery.ui.datepicker.ja.js
   * runtime:

      * initializer - Enthält initializer.js und modelcontrollerpath.js.
      * models - Enthält Modelle aller Komponenten in AEM Forms Workspace.
      * routes – Enthält JavaScript-Dateien und HTML-Dateien, die den Startvorgang, Aufgaben, Verfolgung und Einstellungen in AEM Forms Workspace laden.
      * services - Enthält die in AEM Forms Workspace verwendete service.js.
      * templates - Enthält alle Vorlagen, d. h. HTML-Dateien aller Komponenten in AEM Forms Workspace.
      * util - Enthält alle in AEM Forms Workspace verwendeten Dienstprogrammdateien (JavaScript).
      * views - Enthält Ansichten aller Komponenten in AEM Forms Workspace.

   * main.js
   * registry.js
   * router.js

* libs:

   * ws - Enthält pluginPing.pdf, pdf.html und WSNextAdapter.swf.

* Locale - Enthält .content.xml.
* locales:

   * de-DE - Enthält translation.json für Deutsch.
   * en-US - Enthält translation.json für Englisch.
   * fr-FR - Enthält translation.json für Französisch.
   * ja-JP - Enthält translation.json für Japanisch.
   * html.jsp - Enthält Code, um das aktuelle Browsergebietsschema zu ermitteln.

* Index - Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml
