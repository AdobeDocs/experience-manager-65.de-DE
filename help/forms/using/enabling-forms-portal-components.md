---
title: Aktivieren der Komponenten im Forms Portal
seo-title: Enabling forms portal components
description: Standardmäßig sind Forms Portal-Komponenten deaktiviert. Aktivieren Sie die Gruppen „“ und „Dokumentdienst-Eigenschaften“, um Forms Portal-Komponenten zu aktivieren.
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: ht
source-wordcount: '320'
ht-degree: 100%

---


# Aktivieren der Komponenten im Forms Portal {#enabling-forms-portal-components}

Standardmäßig sind die Forms Portal-Komponenten nicht verfügbar. Führen Sie die folgenden Schritte aus, damit die Komponenten in der Liste der verfügbaren Komponenten in AEM Sidekick angezeigt werden:

1. Melden Sie sich bei der Autoreninstanz Ihrer Website an und öffnen Sie eine AEM Sites-Seite.

1. Führen Sie für die Seiten, die eine statische Vorlage verwenden, die folgenden Schritte aus:

   1. Tippen Sie in der Kopfzeile der Seite auf ![canvas-drop-down](assets/canvas-drop-down.png) > **Design**, um die Seite im Designmodus zu öffnen.
   1. Tippen Sie auf eine beliebige Komponente (mit blauem Rahmen) und dann auf ![field-level](assets/field-level.png), um das Absatzsystem auszuwählen, das die aktuelle Komponente enthält.
   1. Tippen Sie im Absatzsystem auf ![settings_icon](assets/settings_icon.png), um den Bearbeitungsdialog für das Absatzsystem zu öffnen.
   1. Aktivieren Sie in der Liste **[!UICONTROL Zugelassene Komponenten]** die Kontrollkästchen für die Komponenten **[!UICONTROL Dokumentdienst]** und **[!UICONTROL Dokumentdienst-Eigenschaften]**. Tippen Sie auf **[!UICONTROL OK]**.

1. Führen Sie für die Seiten, die eine dynamische Vorlage verwenden, die folgenden Schritte aus:

   1. Tippen Sie in der Kopfzeile der Seite auf ![Eigenschaften](assets/properties.png) > **Vorlage bearbeiten**, um die Vorlage der Seite zu öffnen.
   1. Tippen Sie auf **Layout-Container** und dann auf ![FeedManagement](/help/forms/using/assets/feedmanagement.png). Aktivieren Sie auf der Registerkarte **Zugelassene Komponenten** die Optionen **Dokumentendienste und Dokumentendienste-Eigenschaften** und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>Sie können bestimmte Komponenten aus diesen Kategorien auch aktivieren, indem Sie die Komponenten auswählen. Weitere Informationen zu den Komponenten und ihrer Verwendung finden Sie unter[ Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md) und[ Einbetten einer Verknüpfungskomponente in eine Seite](/help/forms/using/embedding-link-component-page.md).

Jetzt sind die Komponentenkategorien „Document Services“ und „Document Services Predicates“ im Komponenten-Browser verfügbar. Die Komponenten sind für alle Seiten aktiviert, die dieselbe Vorlage verwenden.

## Ähnliche Artikel

* [Aktivieren von Formularportalkomponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](/help/forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
