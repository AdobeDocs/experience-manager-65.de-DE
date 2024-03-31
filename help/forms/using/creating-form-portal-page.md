---
title: Anpassen einer Formularportal-Seite
description: Das Formularportal bietet Web-Entwicklerinnen und Web-Entwicklern Komponenten zum Erstellen und Anpassen von Formularportalen für Websites, die mit Adobe Experience Manager (AEM) erstellt wurden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
feature: Forms Portal
exl-id: 22d7c24e-7a77-4324-afdf-74c1fbf15773
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 100%

---

# Anpassen einer Formularportal-Seite{#creating-a-forms-portal-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Forms Portal-Komponenten bieten Webentwicklern Komponenten zum Erstellen und Anpassen von Formularportalen auf mit Adobe Experience Manager (AEM) erstellten Websites. Einen kurzen Überblick über das Formularportal finden Sie in der [Einführung in das Veröffentlichen von Formularen in einem Portal](../../forms/using/introduction-publishing-forms.md).

## Voraussetzungen {#prerequisites}

Formularportal-Komponenten sind nicht standardmäßig verfügbar. Stellen Sie sicher, dass die folgenden Formularportal-Komponentenkategorien aktiviert sind, wie unter [Aktivieren von Formularportal-Komponenten](/help/forms/using/enabling-forms-portal-components.md) beschrieben.

**Dokumenten-Services**: Umfasst die Komponenten „Suche und Auflister“, „Link“ und „Entwürfe und Übermittlungen“.

**Dokumentdienst-Eigenschaften**: Umfasst die Komponenten „Datumseigenschaft“, „Eigenschaft von komplettem Text“, „Eigenschaftsprädikat“ und „Tag-Eigenschaft“. Diese Komponenten werden zum Konfigurieren der Suche in der Komponente „Suche und Auflister“ verwendet.

Sobald sie auf einer AEM Sites-Seite aktiviert sind, stehen diese Komponentenkategorien für die Verwendung im Komponenten-Browser zur Verfügung.

![AEM Forms Portal-Komponenten im Komponenten-Browser](assets/component-categories.png)

Formularportal-Komponentenkategorien

## Komponente „Search &amp; Lister“ {#search-amp-lister-component}

Die Komponente „Suche und Auflister“, die in der Dokumentendienste-Komponentenkategorie verfügbar ist, dient zum Auflisten von Formularen auf einer Seite und zum Implementieren der Suche in den aufgelisteten Formularen. Die Komponente umfasst zwei Bereiche:

* Listenbereich, in dem die Formulare aufgeführt sind
* Suchbereich, in dem Sie die Suchfunktion hinzufügen

Sie können die Komponente „Suche und Auflister“ aus der Komponentenkategorie des Dokumenten-Services im Komponenten-Browser per Drag-und-Drop auf die Seite ziehen. Ist die Komponente hinzugefügt, sieht sie beispielsweise wie folgt aus.

![Komponente „Search &amp; Lister“ auf einer Seite](assets/fp-grid-viw.png)

Komponente „Suche und Auflister“ auf einer Seite mit Raster-Layout

### Listenbereich {#list-pane}

Im Listenbereich werden die Formulare aufgeführt. Die Komponente „Search &amp; Lister“ bietet unterschiedliche Konfigurationsoptionen, mit denen Sie die Anzeige von Formularen im Listenbereich steuern können.

Um den Listenbereich zu konfigurieren, wählen Sie die Komponente „Suche und Auflister“ und dann ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld **[!UICONTROL Komponente bearbeiten]** wird geöffnet.

![Listenbereich im Bearbeitungsmodus](assets/edit-list.png)

Listenbereich im Bearbeitungsmodus

Das Dialogfeld **Bearbeiten** enthält mehrere Registerkarten mit Konfigurationsoptionen (siehe Tabelle unten). Wählen Sie abschließend **OK**, um die Konfiguration zu speichern.

<table>
 <tbody>
  <tr>
   <th>Tab</th>
   <th>Konfiguration</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Asset-Ordner</strong></code></td>
   <td>Element hinzufügen</td>
   <td>Konfiguriert die Ordner, in die Assets mit der AEM Forms-Benutzeroberfläche hochgeladen werden. Standardmäßig werden alle hochgeladenen Assets aufgeführt. Weitere Informationen zur AEM Forms-Benutzeroberfläche finden Sie in der <a href="../../forms/using/introduction-managing-forms.md" target="_blank">Einführung in das Verwalten von Formularen</a>.</td>
  </tr>
  <tr>
   <td><p><span class="uicontrol"><strong>Anzeige</strong></code></p> </td>
   <td>Titeltext</td>
   <td>Titel für die Komponente „Suche und Auflister“. Der Standardtitel lautet <strong>Formularportal</strong>.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Layout-Vorlage</td>
   <td>Layout der Assets. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Erweiterte Suche deaktivieren</td>
   <td>Wenn diese Option aktiviert ist, wird das Symbol für die erweiterte Suche ausgeblendet.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Textsuche deaktivieren</td>
   <td>Wenn diese Option aktiviert ist, wird die Suchleiste für die Volltextsuche ausgeblendet.</td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Ergebnis</strong></code></td>
   <td>Anzahl der Ergebnisse pro Seite</td>
   <td>Konfiguriert die maximale Anzahl von Formularen, die auf einer Seite angezeigt werden sollen.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Ergebnistext</td>
   <td><p>Konfiguriert den Ergebnistext (z. B. 1–12 von 601 <strong>Ergebnissen</strong>). Der Standardwert lautet <strong>Ergebnisse</strong>.</p> <p>Wenn Sie beispielsweise in diesem Feld <strong>Formulare</strong> angeben und es insgesamt 601 Formulare gibt, wird der Ergebnistext in „1-12 von 601 <strong>Formularen</strong>“ geändert.</p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Seitentext</td>
   <td><p>Konfiguriert den Seitentext (zum Beispiel <strong>Seite</strong> 1 von 51). Der Standardwert ist <strong>Seite</strong>.</p> <p>Wenn Sie zum Beispiel in diesem Feld <strong>Antragsformular</strong> angeben und es gibt 51 Seiten, ändert sich der Seitentext in „<strong>Antragsformular</strong> 1 von 51“.</p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Text für „Von“</td>
   <td><p>Ersetzt das Wort <strong>von</strong> durch den angegebenen Text (Seite 1 <strong>von </strong>51). Der Standardwert ist <strong>von</strong>.</p> <p>Wenn Sie zum Beispiel in diesem Feld <strong>von insgesamt</strong> angeben, ändert sich der Text in „Seite 1 <strong>von insgesamt</strong> 51“.</p> </td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Formular-Link</strong></code></td>
   <td>Render-Typ</td>
   <td>Steuert die Auflistung von Formularen, die auf dem angegebenen Rendertyp basieren. Die verfügbaren Optionen sind PDF und HTML. Wenn Sie beispielsweise nur HTML als Rendertyp angeben, werden die PDF-Formulare herausgefiltert.</td>
  </tr>
  <tr>
   <td> </td>
   <td>HTML-Profil</td>
   <td>Konfiguriert das HTML-Profil, das für das Rendern verwendet werden soll. Alle verfügbaren Profile werden in der Dropdown-Liste aufgeführt.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Übermittlungs-URL</td>
   <td><p>Konfiguriert ein Servlet, an das die Formulardaten gesendet werden.</p> <p><strong>Hinweis:</strong> <em>Die Sende-URL für ein Formular kann an mehreren Stellen angegeben werden und die Rangfolge lautet wie folgt:</em></p>
    <ol>
     <li><em>Die Sende-URL, die in das Formular eingebettet wird (in der Senden-Schaltfläche), hat die höchste Priorität.</em></li>
     <li><em>Die Sende-URL, die in der AEM Forms -Benutzeroberfläche erwähnt wird, hat die zweithöchste Priorität.</em></li>
     <li><em>Die Sende-URL, die im Forms Portal erwähnt wird, hat die niedrigste Priorität.</em></li>
    </ol> </td>
  </tr>
  <tr>
   <td> </td>
   <td>QuickInfo zum HTML-Rendervorgang</td>
   <td>Konfiguriert den Text für die QuickInfo, die angezeigt wird, wenn sich der Mauszeiger über <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> (das HTML5-Symbol) bewegt.</td>
  </tr>
  <tr>
   <td> </td>
   <td>QuickInfo zum PDF-Rendervorgang</td>
   <td>Konfiguriert den Text für die QuickInfo, die angezeigt wird, wenn sich der Mauszeiger über <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> (das PDF-Symbol) bewegt.</td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Stil</strong></code></td>
   <td>Style Type (Stiltyp)</td>
   <td>Hier können Sie <strong>Kein Stil, Standardstil</strong> oder <strong>Benutzerdefinierter Stil </strong> für die Auflistung der Formulare angeben.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Pfad für benutzerdefinierten Stil</td>
   <td>Wenn Sie „Benutzerdefiniert“ als Stiltyp ausgewählt haben, geben Sie den Pfad zum benutzerdefinierten CSS an, andernfalls wählen Sie „Standard“.</td>
  </tr>
 </tbody>
</table>

### Suchbereich {#search-pane}

Über den Suchbereich können Sie die Komponenten „Date Predicate“, „Full Text Predicate“, „Properties Predicate“ und „Tags Predicate“ aus der Kategorie „Document Services Predicates“ im AEM Sidekick hinzufügen. Diese Komponenten implementieren die Suchfunktion, mit der Benutzer nach den aufgeführten Formularen suchen können.

**Tipp:** *Sie können anhand vorgegebener Kriterien die Liste der Formulare festlegen, die im Formularportal angezeigt werden, und die Suchfunktion für Endbenutzer ausblenden. Um die Formularliste zu steuern, verwenden Sie die Prädikatkomponenten, um Suchfilter anzuwenden. Sie können auch die Standardfilterwerte angeben und die Suche über die Registerkarte „Anzeige“ im Dialogfeld „Komponente bearbeiten“ deaktivieren.*

![Suchbereich mit den Eigenschaften für Datum, Volltext, Eigenschaften und Tags](assets/search-with-predicates.png)

Suchbereich mit den Eigenschaften für Datum, Volltext, Eigenschaften und Tags

#### Datumseigenschaft {#date-predicate}

Die Komponente „Datumseigenschaft“ ermöglicht die Suche nach aufgeführten Formularen, die während eines festgelegten Zeitraums geändert wurden.

So konfigurieren Sie die Komponente „Datumseigenschaft“:

1. Wählen Sie die Komponente und dann ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld „Bearbeiten“ wird geöffnet.
1. Geben Sie Folgendes an:

   * **Typ:** Die einzige verfügbare Option ist **Last Modified Date** (Letztes Änderungsdatum).

   * **Text:** Beschriftung der Komponente „Date Predicate“. Der Standardwert ist **Last Modified Date (Letztes Änderungsdatum).**

   * **Start Date Label (Startdatumsbeschriftung):** Beschriftung des Feldes „Startdatum“.
   * **End Date Label (Enddatumsbeschriftung):** Beschriftung des Feldes „Enddatum“.
   * **Ausblenden:** Damit wird der Standarddatumsfilter für die Auflistung von Formularen erzwungen. 

1. Wählen Sie **OK** aus.

#### Vollständige Texteigenschaft {#full-text-predicate}

Die Komponente „Volltexteigenschaft“ implementiert die Volltextsuche nach Formulardaten, zum Beispiel Name und Beschreibung. Benutzende können eine beliebige Textzeichenfolge suchen, um Formulare zu finden, die den Text in ihrem Namen oder ihrer Beschreibung enthalten.

So konfigurieren Sie die Komponente „Volltexteigenschaft“:

1. Wählen Sie die Komponente und dann ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld „Bearbeiten“ wird geöffnet.
1. Geben Sie den Titel im Feld **Haupttitel** an.
1. Wählen Sie **OK** aus.

#### Eigenschaften-Eigenschaft {#properties-predicate}

Die Komponente „Eigenschaftsprädikat“ implementiert die Suche nach Formularen anhand von Formulareigenschaften, wie Titel, Autorin bzw. Autor und Beschreibung.

So konfigurieren Sie die Komponente „Eigenschaftsprädikat“:

1. Wählen Sie die Komponente und dann ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld „Bearbeiten“ wird geöffnet.
1. Geben Sie auf der Registerkarte „Allgemein“ die Suchbeschriftung an. Der Standardwert ist **Eigenschaften**. 

1. Wählen Sie auf der Registerkarte „Optionen“ **Element hinzufügen** aus.
1. Wählen Sie eine Eigenschaft in der Dropdownliste aus und geben Sie für die Eigenschaft eine Suchbeschriftung im Feld unter der Dropdown-Liste an.
1. Wiederholen Sie Schritt 4, um weitere Eigenschaften hinzuzufügen. Sie können auch einen Standardfilterwert für die Auflistung von Formularen anhand der angegebenen Kriterien festlegen und die Eigenschaft für die Suche durch Endbenutzer ausblenden. Aktivieren Sie das Kontrollkästchen „Ausblenden“ für eine Eigenschaft und legen Sie den Standardfilterwert fest.
 Wenn Sie beispielsweise Formulare anzeigen möchten, die „Reise“ in ihrem Titel enthalten, wählen Sie „Ausblenden“ neben der Eigenschaft „Titel“. Geben Sie außerdem „Reise“ im Textfeld des Standardfilterwerts an.

1. Wählen Sie **OK** aus.

#### Tag-Eigenschaft {#tags-predicate}

Die Komponente „Tag-Eigenschaft“ implementiert die Suche nach Formularen anhand von in Forms Manager definierten Tags.

So konfigurieren Sie die Komponente „Tag-Eigenschaft“:

1. Wählen Sie die Komponente und dann ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld „Bearbeiten“ wird geöffnet.
1. Wählen Sie neben dem Feld „Tags“ die Schaltfläche mit dem Abwärtspfeil aus.
1. Wählen Sie geeignete Tags aus.
1. Wählen Sie **OK** aus.

Die ausgewählten Tags werden im Suchbereich zusammen mit den Kontrollkästchen zur Auswahl angezeigt. Benutzer können ihre Suche nun anhand der Tags eingrenzen.

## Auflisten von Formularen auf einer Seite {#list-forms-on-a-page-br}

Um Formulare auf einer Seite aufzulisten, fügen Sie die Komponente **[!UICONTROL Search &amp; Lister]** der Seite hinzu und konfigurieren Sie den **[!UICONTROL Listenbereich]**. Um den Endbenutzenden die Möglichkeit zu geben, Formulare nach Datum, Text und Tags zu durchsuchen, fügen Sie eine **[!UICONTROL Suchbereichskomponente]** hinzu.

Um einen Link zu einem Formular an einer beliebigen Stelle auf der Seite anzuzeigen, verwenden Sie die Komponente „Link“. Weitere Informationen zu Link-Komponenten finden Sie unter [Einbetten einer Link-Komponente in eine Seite](../../forms/using/embedding-link-component-page.md).

Um die Formulare aufzulisten, die sich im Entwurfsstadium befinden, und die Formulare, die bereits eingereicht wurden, verwenden Sie die Komponente **[!UICONTROL Entwürfe und Übermittlungen]**. Weitere Informationen finden Sie unter [Anpassen der Komponente „Entwürfe und Übermittlungen“](../../forms/using/draft-submission-component.md).

## Eignung für Mobilgeräte {#mobile-device-friendliness}

Die Formularportal-Komponente „Suche und Auflister“ ist für Mobilgeräte geeignet und passt sich entsprechend an. Das Layout aller drei Standardansichten (Raster, Karten, Bedienfeld) wird entsprechend dem Gerät, auf dem die Site geöffnet wird, angepasst, vorausgesetzt, die Webseite passt sich ebenfalls an. Die einfache Tatsache besteht darin, dass „Suche und Auflister“ nur eine Komponente ist und nicht den Seitenstil steuert.

In der folgenden Abbildung wird die Komponente „Suche und Auflister“ angezeigt, wenn sie auf einem Mobilgerät geöffnet wird:

![Screenshot der Komponente „Search und Lister“](assets/search_lister.png)

Komponente „Search &amp; Lister“

## Anpassen einer Forms Portal-Seite {#customizing-a-forms-portal-page-br}

Sie können eine Forms Portal-Seite anpassen und ihr ein unverwechselbares Erscheinungsbild verleihen. Sie können auch Metadaten hinzufügen, um die Suchabfrage zu verbessern, das Layout der Seite zu ändern und benutzerdefinierte CSS-Stile hinzuzufügen. Weitere Informationen finden Sie unter [Anpassen von Vorlagen für Formularportalkomponenten](../../forms/using/customizing-templates-forms-portal-components.md).

In der AEM Forms-Benutzeroberfläche können Sie benutzerdefinierte Metadaten zu Formularen hinzufügen. Benutzerdefinierte Metadaten sind nützlich, wenn Sie den Endbenutzenden die Auflistung und Suche von Formularen ermöglichen möchten. Weitere Informationen zu benutzerdefinierten Metadaten finden Sie unter [Anpassen von Vorlagen für Formularportalkomponenten](../../forms/using/customizing-templates-forms-portal-components.md).

Das Formularportal stellt vorkonfigurierte Render-Aktionen bereit. Sie können das Formularportal anpassen, um weitere Aktionen hinzuzufügen. Weitere Informationen finden Sie unter [ Hinzufügen einer benutzerdefinierten Aktion zu Formularlistenelementen](../../forms/using/add-custom-action-form-lister.md).

## Ähnliche Artikel

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
