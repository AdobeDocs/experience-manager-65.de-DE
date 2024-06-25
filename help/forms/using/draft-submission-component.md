---
title: Komponente „Drafts and Submissions“
description: Mit der Komponente „Drafts and Submissions“ können Sie Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden. Sie können das Erscheinungsbild und den Stil der Komponente anpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: f3f013a7-a399-4178-a901-d4a8c65ddbd3
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '744'
ht-degree: 100%

---

# Komponente „Drafts and Submissions“{#drafts-and-submissions-component}

Mit der Komponente „Drafts &amp;Submissions“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden. Die Komponente bietet separate Bereiche (Registerkarten) für Entwürfe und für gesendete Formulare. Die Benutzenden können nur ihre Entwürfe und übermittelten Formulare anzeigen.

## Konfigurieren der Komponente {#configuring-the-component}

In der Komponente „Entwürfe und Sendungen“ stehen zwei Registerkarten zur Verfügung: „Entwürfe“ und „Übermittlungen“.

Damit ein übermitteltes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, definieren Sie als **Übermittlungsaktion** die Option **[Übermittlungsaktion für Formularportal](../../forms/using/configuring-submit-actions.md). Sie können stattdessen auch die** Option „Forms Portal Submit“ aktivieren. Wenn ein Benutzer das Formular übermittelt, wird dieses der Registerkarte „Submissions“ hinzugefügt.

Die Entwurfsfunktion ist standardmäßig aktiviert. Wenn eine Benutzerin oder ein Benutzer in einem adaptiven Formular auf **Speichern** klickt, wird das Formular zur Registerkarte „Entwürfe“ hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine Komponente „Entwürfe und Sendungen“ hinzuzufügen und zu konfigurieren:

1. Ziehen Sie die Komponente **Entwürfe und Sendungen** unter der Kategorie „Dokumentendienste“ im Komponenten-Browser auf Ihre Seite.
1. Wählen Sie die Komponente und dann ![settings_icon](assets/settings_icon.png) aus, um das Dialogfeld „Bearbeiten“ für die Komponente zu öffnen.

   ![Komponente „Drafts &amp; Submissions“](assets/drafts-submissions-edit.png)

1. Geben Sie im Dialogfeld „Bearbeiten“ die folgenden Details an und wählen Sie **Fertig** aus, um die Einstellungen zu speichern.

<table>
 <tbody>
  <tr>
   <th>Tab</th>
   <th>Konfiguration</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Allgemein</td>
   <td>Gesamtergebnis</td>
   <td>Gibt die maximal mögliche Anzahl anzuzeigender Ergebnisse an. Sind mehr Ergebnisse vorhanden, als für Gesamtergebnis angegeben wurde, wird am unteren Ende der Komponente der Link <strong>Mehr</strong> angezeigt. Klicken Sie auf <strong>Mehr</strong>, um alle Formulare anzuzeigen. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Stiltyp</td>
   <td>Legt den Stil der Komponente fest. Sie können entweder <strong>No Style</strong> (Kein Stil), <strong>Default Style</strong> (Standardstil) oder <strong>Custom Style </strong>(Benutzerdefinierter Stil) für die Liste der Formulare angeben. Für die Option „Custom Style“ können Sie den Pfad zu Ihrem benutzerdefinierten CSS im Feld <strong>Custom Style Path</strong> angeben<strong>.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Custom Style Path (Pfad für benutzerdefinierten Stil)</td>
   <td>Wenn Sie die Option <strong>Custom Style</strong> im Feld <strong>Style Type</strong> gewählt haben, geben Sie im Feld <strong>Custom Style Path</strong> den Pfad zu Ihrer benutzerdefinierten CSS-Datei an. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Anzeigeoptionen</td>
   <td><p>Gibt die anzuzeigenden Registerkarten an. Sie können festlegen, ob Formularentwürfe, übermittelte Formulare oder beides angezeigt werden soll. </p> <p><strong>Hinweis</strong>:<em> Wenn Sie für <strong>Anzeigeoptionen</strong> eine andere Option als <strong>Beide</strong> wählen, wird die Feldoption <strong>Standardregisterkarte</strong> nicht verwendet.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Standard-Registerkarte</td>
   <td>Gibt an, welche Registerkarte beim Laden der Forms Portal-Seite angezeigt werden soll. Sie können zwischen <strong>Registerkarte für Formularentwürfe</strong> und <strong>Registerkarte für übermittelte Formulare</strong> wählen.</td>
  </tr>
  <tr>
   <td>Konfiguration der Registerkarte für Formularentwürfe</td>
   <td>Benutzerdefinierter Titel</td>
   <td>Geben Sie den Titel der Registerkarte für <strong>Formularentwürfe</strong> an. Der Standardwert ist <strong>Formularentwürfe</strong>.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Layout-Vorlage</td>
   <td>Gibt das für die Liste „Formularentwürfe“ zu verwendende Layout an.</td>
  </tr>
  <tr>
   <td>Konfiguration der Registerkarte für übermittelte Formulare</td>
   <td>Benutzerdefinierter Titel </td>
   <td>Geben Sie den Titel der Registerkarte für <strong>übermittelte Formulare</strong> an. Der Standardwert ist <strong>Übermittelte Formulare</strong>.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Layout-Vorlage</td>
   <td>Gibt das für die Liste der übermittelten Formulare zu verwendende Layout <strong> </strong>an.  </td>
  </tr>
 </tbody>
</table>

## Anpassung des Speicherorts {#customizing-the-storage}

Wenn Sie die Forms Portal Aktion-Übermittlungsaktion verwenden oder die Store-Daten über die Forms-Portal-Optionen im adaptiven Formular aktivieren, werden die Formulardaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. Stattdessen müssen Sie die Entwurfs- und Übermittlungskomponente mit einem sicheren Speicher wie der Unternehmensdatenbank integrieren, um Entwürfe und übermittelte Formulardaten zu speichern.

Mit dem Formularportal können Sie Daten im lokalen AEM-Repository, im AEM-Remote-Repository oder in einer Datenbank speichern. Mit AEM Forms haben Sie die Möglichkeit, die Implementierung der Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anzupassen. Sie können Standardmethoden überschreiben, um festzulegen, wie Entwurfs- und Übermittlungsdaten an einem Speicherort Ihrer Wahl gespeichert werden. Beispiel: Sie können die Daten in einem Datenspeicher speichern, der derzeit in Ihrem Unternehmen implementiert ist.

Das Forms-Portal bietet vordefinierte Services (APIs) zum Speichern von Daten im CRX-Repository lokaler und entfernter Instanzen für die Veröffentlichung von AEM Forms. Sie können die Standardimplementierungen durch benutzerdefinierte Implementierungen ersetzen, wie es im Artikel [Konfiguration von Services für die Speicherung von Entwürfem und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md) beschrieben wird, um die standardmäßige Funkion zu ersetzen. Detaillierte Informationen zu den Methoden, die für eine benutzerdefinierte Implementierung zum Speichern von Inhalten an einem gesicherten Speicherort erforderlich sind, finden Sie unter [Anpassen von Services für Entwurfs- und Übermittlungsdaten](/help/forms/using/custom-draft-submission-data-services.md) und [Benutzerdefinierter Speicher für die Komponente der Entwürfe und Übermittlungen.](/help/forms/using/adding-custom-storage-provider-forms.md)

Die AEM Forms-Dokumentation bietet ein [Beispiel für die Integration der Komponente der Entwürfe und Übermittlungen in die Datenbank](integrate-draft-submission-database.md). Sie können die als Beispiel dargestellte Implementierung verwenden, um Ihre eigene Implementierung zu entwickeln.

## Ähnliche Artikel

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
