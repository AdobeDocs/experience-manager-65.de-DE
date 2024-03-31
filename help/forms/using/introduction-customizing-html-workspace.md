---
title: Einführung zur Anpassung von AEM Forms Workspace
description: Eine kurze Einführung mit konzeptuellen und technischen Informationen zur Anpassung von LiveCycle AEM Forms Workspace für die Prozessverwaltung.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: b183d42f-343c-4acb-bc73-f80ad72e54df
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 100%

---

# Einführung zur Anpassung von AEM Forms Workspace{#introduction-to-customizing-aem-form-workspace}

AEM Forms Workspace bietet Funktionen zum Ändern der Darstellung und der Funktionen der Benutzeroberfläche. Die Anpassungen zum Ändern des Stils, des Layouts, der Formatierung, des Branding und der Kernfunktion werden unten beschrieben.

![cu_customized_workspace_example](assets/cu_customized_workspace_example.png)

Beispiel für einen benutzerdefinierten Workspace

## Arten der Anpassung {#types-of-customizations}

AEM Forms Workspace unterstützt viele Anpassungen, mit denen das Layout, die Darstellung, die Funktionalität und andere Aspekte der Benutzeroberfläche aktualisiert werden können. Bei den Anpassungen wird mindestens einer der folgenden Faktoren aktualisiert:

* Aussehen der Benutzeroberfläche
* Funktionen mithilfe der semantischen Anpassungen
* Wiederverwenden von HTML-Komponenten in anderen Anwendungen

### Änderungen der Benutzeroberfläche {#user-interface-changes}

Sie können das Aussehen, Layout und andere Darstellungsfaktoren von AEM Forms Workspace ändern. Ändern Sie den Workspace durch Anpassen der CSS- und HTML-Vorlagen und JavaScript™-Dateien. Alle Standarddateien werden in der Standardinstallation bereitgestellt.

Die am häufigsten angewandten Schritte werden in [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) beschrieben. Einzelne Beispiele für Anpassungen, einschließlich der ausführlichen Schritte, finden Sie in den jeweiligen Artikeln am Ende des Artikels.

#### Grundlagen des Stylesheets {#understanding-the-style-sheet}

Bevor Sie Workspace anpassen, sollten Sie sich mit dem Standard-Stylesheet vertraut machen, das mit AEM Forms unter /libs/ws/css/style.css bereitgestellt wird.

Zur Anpassung des Workspace wird empfohlen, dass Sie sich mit dem vorhandenen Stylesheet „style.css“ im Ordner /libs/ws/css vertraut machen. Einige wichtige Komponenten werden im Folgenden beschrieben.

<table>
 <tbody>
  <tr>
   <th><p>CSS-Element</p> </th>
   <th><p>Geänderte Benutzeroberflächenkomponente</p> </th>
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
   <td><p>Header der Kategorienliste</p> </td>
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
   <td><p>Ausgewählte Kategorie und Mouseover-Stil der Kategorie</p> </td>
  </tr>
  <tr>
   <td><p>categoryListBar .tool, categoryListBar .content</p> </td>
   <td><p>Seite für den Startprozess (geschlossene Kategorienliste)</p> </td>
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
   <td><p>Der Header einer Startpunktliste oder einer Aufgabenliste</p> </td>
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
   <td><p>Benutzer-Dropdown-Komponente im Header</p> </td>
  </tr>
  <tr>
   <td><p>.sortDrop dd ul</p> </td>
   <td><p>Dropdown-Komponente für Sortieraufgabe</p> </td>
  </tr>
 </tbody>
</table>

#### CSS {#css}

Das Erscheinungsbild von AEM Forms Workspace wird aus einer CSS übernommen. Durch Anpassen der CSS können Sie die Darstellungseigenschaften des Workspace ändern, z. B. Schriftarten, Farben, Branding und Layout.

Die wesentlichen Schritte für die CSS-Anpassung sind:

* Erstellen Sie die eine CSS-Datei.
* Fügen Sie der CSS-Datei Stilelemente hinzu. Weitere Informationen finden Sie im entsprechenden Artikel zum Thema CSS-Stile.
* Aktualisieren Sie die betreffenden Verweise in der Datei `html.jsp`.

Die ausführlichen Schritte zur Umsetzung dieser Anpassungen finden Sie unter [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md). Die mit AEM Forms Workspace bereitgestellte CSS-Datei ist unter /libs/ws/css/ zu finden. Verwenden Sie für diese CSS-Anpassungen das [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p). Einzelne Beispiele für CSS-Anpassungen finden Sie in den jeweiligen Hilfethemen am Ende des Artikels.

#### Bild {#image}

Sie können AEM Forms Workspace anpassen, um Avatare von Benutzern oder das Logo Ihres Unternehmens hinzuzufügen. Verwenden Sie für diese Anpassungen das [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).

Die wesentlichen Schritte für die Anpassungen der Bilder sind:

* Installieren und konfigurieren Sie WebDAV.
* Fügen Sie neue Bilder hinzu.
* Fügen Sie neue Stile entsprechend den hinzugefügten Bildern hinzu.
* Stellen Sie eine Verknüpfung zu der neuen CSS-Datei in der Datei `html.jsp` her.

Um mit der Anpassung der Bilder in AEM Forms Workspace zu beginnen, führen Sie die [Generischen Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) aus. Einzelne Beispiele für Bildanpassungen finden Sie in den jeweiligen Hilfethemen am Ende des Artikels.

#### HTML-Vorlage {#html-template}

HTML-Vorlagen dienen dazu, das Erscheinungsbild und Layout der Benutzeroberfläche des Arbeitsbereichs zu definieren. Indem Sie die Standard-HTML-Vorlagen aktualisieren, können Sie das Layout der Standard-Benutzeroberfläche anpassen.

Die wesentlichen Schritte für die Anpassungen der HTML-Vorlagen sind:

* Erstellen Sie in einem benutzerdefinierten Ordner die Kopien von den erforderlichen Standarddateien.
* Fügen Sie dem benutzerdefinierten Ordner neue Vorlagen hinzu.
* Nehmen Sie an den kopierten Dateien die entsprechenden Aktualisierungen vor, z. B. die Aktualisierung des Pfads der neuen Vorlage.

Einzelne Beispiele für diese Anpassungen finden Sie in den jeweiligen Hilfethemen am Ende des Artikels. Wählen Sie je nach der anzupassenden Vorlage das [Ship-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) oder das [Dev-Paket](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).

### Semantikänderungen {#semantic-changes}

Verändern Sie den JavaScript Quell-Code, um die AEM Forms Workspace-Funktionen zu ändern. Änderungen in der Kernfunktion werden als Semantikänderungen bezeichnet. Ändern Sie Modelle, Ansichten und Vorlagen, die als Teil des Quell-Codes von AEM Forms Workspace bereitgestellt werden.

Die wesentlichen Schritte zur Änderung der Semantik und damit zur Änderung der Funktionen von AEM Forms Workspace sind:

* Erstellen Sie in einem benutzerdefinierten Ordner die Kopien von den entsprechenden Standarddateien.
* Fügen Sie dem benutzerdefinierten Ordner neue Modelle und Ansichten hinzu.
* Nehmen Sie die erforderlichen Aktualisierungen vor, z. B. die Aktualisierung der Pfade der neu hinzugefügten Modelle und Ansichten in den Standard-JavaScript-Dateien.
* Minimieren Sie das Paket zum Optimieren der Leistung.

Weitere grundlegende Informationen zu den Komponenten, die Teil des Quellcodes sind, finden Sie unter [Beschreibung wiederverwendbarer Komponenten](/help/forms/using/description-reusable-components.md). Verwenden Sie für diese Anpassungen das Dev-Paket.

### Wiederverwendbare Komponenten {#reusable-components}

Da AEM Forms Workspace eine komponentenbasierte Software ist, lässt sich diese einfach anpassen und wiederverwenden. Integrieren Sie mühelos die Workspace-Komponenten in Ihre Webanwendungen.

Weitere grundlegende Informationen finden Sie unter der [Beschreibung wiederverwendbarer Komponenten](/help/forms/using/description-reusable-components.md). Anweisungen zum Verwenden der Komponenten sind unter [Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen](/help/forms/using/description-reusable-components.md) aufgeführt.

## Erstellen von AEM Forms Workspace-Code {#building-html-workspace-code}

### SDK-Paket {#sdk-package}

Das Paket enthält den Quellcode von AEM Forms Workspace. Das Paket ist verfügbar unter `[LC root]\sdk\html-workspace\adobe-lc-workspace-src.zip`.

Es dient vor allem der Anpassung, denn es bietet Funktionen, um Folgendes zu generieren:

* CRX-Pakete für Ship-, Debug- und Dev-Profile (siehe unten unter [CRX-Pakete](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p)).
* Minimierte Version des benutzerspezifischen Codes (für Semantikänderungen).

#### WS-Inhalt {#ws-content}

* client-pkg:

   * src – Enthält die Artefakte, die erforderlich sind, um CRX-Knoten zu erstellen.
   * pom.xml – Das Skript zum Erstellen von Bereitstellungspaketen für ein WS-Deploy-Paket mit verschiedenen Profilen

* client-html:

   * assembly – Enthält die zip.xml, die vom Skript zum Erstellen von AEM Forms Workspace SDK verwendet wird.
   * src/main/webapp -

      * css – Enthält Stylesheets für AEM Forms Workspace.
      * images – Enthält Bilder, die in AEM Forms Workspace verwendet werden.
      * js:

         * libs – Enthält alle Drittanbieterbibliotheken, die in AEM Forms Workspace verwendet werden.
         * licenses – Enthält Lizenzen für HTML- und JS-Dateien sowie den Code, der als Präfix für diese Lizenzen dient und sie den entsprechenden Quelldateien zuordnet.
         * minifier – Wird für die Kombination, Minimierung und Verschleierung des benutzerdefinierten JavaScript-Codes verwendet.
         * resourcejs_optimizer – Wird für die Kombination, Minimierung und Verschleierung der JavaScript-Quelle verwendet.
         * resource_generator – Wird für die Generierung von register.js und modelcontrollerpath.js verwendet.
         * runtime:

            * initializer - Enthält initializer.js, das zum Initialisieren der Backbone-Ansichten und -Modelle in AEM Forms Workspace verwendet wird.
            * models – Enthält Backbone-Modelle aller Komponenten in AEM Forms Workspace.
            * routes – Enthält JavaScript-Dateien und HTML-Dateien, die den Startvorgang, Aufgaben, Verfolgung und Einstellungen in AEM Forms Workspace laden.
            * services - Enthält in AEM Forms Workspace verwendete service.js. Alle Server-Aufrufe erfolge über service.js.
            * templates – Enthält alle Vorlagen, d. h. HTML-Dateien aller Ansichten in AEM Forms Workspace.
            * util – Enthält alle in AEM Forms Workspace verwendeten Dienstprogrammdateien (JavaScript).
            * views – Enthält Backbone-Ansichten aller Komponenten in AEM Forms Workspace.

         * main.js
         * router.js

      * libs/ws: pdf.html und pluginPing.pdf werden zum Laden von PDF-Formularen in AEM Forms Workspace verwendet. WSNextAdapter.swf wird verwendet, um SWF-Formulare und -Guides in AEM Forms Workspace zu laden.
      * locales:

         * de-DE - Enthält translation.json für Deutsch.
         * en-US - Enthält translation.json für Englisch.
         * fr-FR - Enthält translation.json für Französisch.
         * ja-JP - Enthält translation.json für Japanisch.
         * html.jsp - Enthält Code, um das aktuelle Browser-Gebietsschema zu ermitteln.


      * html.jsp
      * GET.jsp

### CRX-Paket {#crx-package}

Das CRX-Paket kann auf dem CRX™-Repository bereitgestellt werden. Diese sind verfügbar unter `[LC root]\crx-repository\install\adobe-lc-workspace-pkg.zip`.

Dieses Paket kann mithilfe der drei folgenden Profile erstellt werden, die nachstehend beschrieben werden.

| **Profil** | **Beschreibung** | **Nutzung** |
|---|---|---|
| Ship-Profil | Dieses Profil erstellt ein CRX-Paket der kleinstmöglichen Größe mittels Minimierung. Dieses Paket ist das effizienteste. Alle JavaScript™-Dateien werden zusammengefasst und zu einer JS-Datei minimiert. | Verwenden Sie dieses Profil, wenn keine weiteren Semantikänderungen in den JS-Dateien erforderlich sind. |
| Debug-Profil | Dieses Profil erstellt ein mitteleffizientes CRX-Paket. Das Paket ist etwas größer als das mit dem Ship-Profil erstellte Paket. Dieses Paket fasst die meisten JavaScript-Dateien in einer JS-Datei zusammen. | Verwenden Sie dieses Profil zum Debugging. |
| Dev-Profil | Dieses Profil erstellt ein CRX-Paket der größtmöglichen Größe. Alle JavaScript-Dateien sind separat verfügbar, wie im SDK-Paket. | Verwenden Sie dieses Profil, wenn Semantikänderungen notwendig sind. |

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
   * html.jsp - Enthält Code, um das aktuelle Browser-Gebietsschema zu ermitteln.

* Index – Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Debug-Profil {#debug-profile}

#### Befehl {#command-1}

* mvn clean -P Debug install auf client-pkg
* Befehlsausführung von Debug-Profil funktioniert nur auf 64-Bit-JVM.

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
   * html.jsp - Enthält Code, um das aktuelle Browser-Gebietsschema zu ermitteln.

* Index – Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Dev-Profil {#dev-profile}

#### Befehl {#command-2}

mvn clean -P Dev-Installation auf Client-Paket

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
      * util – Enthält alle in AEM Forms Workspace verwendeten Dienstprogrammdateien (JavaScript).
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
   * html.jsp - Enthält Code, um das aktuelle Browser-Gebietsschema zu ermitteln.

* Index – Enthält .content.xml
* profile - Enthält offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml
