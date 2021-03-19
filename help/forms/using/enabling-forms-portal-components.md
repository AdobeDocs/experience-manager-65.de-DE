---
title: Aktivieren der Komponenten im Forms Portal
seo-title: Aktivieren der Komponenten im Forms Portal
description: Standardmäßig sind Forms Portal-Komponenten deaktiviert. Aktivieren Sie die Gruppen „“ und „Dokumentdienst-Eigenschaften“, um Forms Portal-Komponenten zu aktivieren.
seo-description: Standardmäßig sind Forms Portal-Komponenten deaktiviert. Aktivieren Sie die Gruppen „“ und „Dokumentdienst-Eigenschaften“, um Forms Portal-Komponenten zu aktivieren.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Formularportal
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 48%

---


# Aktivieren der Komponenten im Forms Portal {#enabling-forms-portal-components}

Standardmäßig sind die Forms Portal-Komponenten nicht verfügbar. So zeigen Sie die Komponenten in der Liste der verfügbaren Komponenten im Sidekick AEM an:

1. Melden Sie sich bei der Autoreninstanz Ihrer Website an und öffnen Sie eine AEM Sites-Seite.

1. Für Seiten, die eine statische Vorlage verwenden, führen Sie die folgenden Schritte aus:

   1. Tippen Sie in der Kopfzeile der Seite auf ![canvas-drop-down](assets/canvas-drop-down.png) > **Design**, um die Seite im Designmodus zu öffnen.
   1. Tippen Sie auf eine beliebige Komponente (mit einem blauen Rand) und dann auf ![Feldebene](assets/field-level.png), um das Absatzsystem auszuwählen, das die aktuelle Komponente enthält.
   1. Tippen Sie im Absatzsystem auf ![settings_icon](assets/settings_icon.png), um das Dialogfeld &quot;Bearbeiten&quot;für das Absatzsystem zu öffnen.
   1. Aktivieren Sie in der Liste **[!UICONTROL Zugelassene Komponenten]** die Kontrollkästchen für die Komponenten **** und **[!UICONTROL Dokumentdienst-Eigenschaften]**. Tippen Sie auf **[!UICONTROL OK]**.

1. Für Seiten, die eine dynamische Vorlage verwenden, führen Sie die folgenden Schritte aus:

   1. Tippen Sie in der Kopfzeile der Seite auf ![properties](assets/properties.png) > **Vorlage bearbeiten**, um die Vorlage der Seite zu öffnen.
   1. Tippen Sie auf **Layout-Container** und dann auf ![FeedManagement](/help/forms/using/assets/feedmanagement.png). Aktivieren Sie auf der Registerkarte **Zulässige Komponenten** die Optionen **Dokument Services and Dokument Services Predicates** und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>Sie können bestimmte Komponenten aus diesen Kategorien auch aktivieren, indem Sie die Komponenten auswählen. Weitere Informationen zu den Komponenten und ihrer Verwendung finden Sie unter[ Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md) und[ Einbetten einer Verknüpfungskomponente in eine Seite](/help/forms/using/embedding-link-component-page.md).

Jetzt sind die Komponentenkategorien „Document Services“ und „Document Services Predicates“ im Komponenten-Browser verfügbar. Die Komponenten sind für alle Seiten aktiviert, die dieselbe Vorlage verwenden.

## Verwandte Artikel

* [Aktivieren der Forms Portal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-Seite erstellen](/help/forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Komponente &quot;Drafts and Submissions&quot;verwenden](/help/forms/using/draft-submission-component.md)
* [Anpassen der Datenspeicherung von Entwürfen und gesendeten Formularen](/help/forms/using/draft-submission-component.md)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md)
