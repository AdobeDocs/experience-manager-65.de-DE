---
title: Aktivieren von Formularportal-Komponenten
description: Standardmäßig sind Formularportal-Komponenten deaktiviert. Aktivieren Sie die Gruppen „Dokumentendienste“ und „Dokumentendienste-Prädikate“, um Formularportal-Komponenten zu aktivieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
feature: Forms Portal
exl-id: 572194b7-063b-4c38-af43-aba78e9c51c6
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '332'
ht-degree: 100%

---

# Aktivieren von Formularportal-Komponenten {#enabling-forms-portal-components}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Standardmäßig sind Formularportal-Komponenten nicht verfügbar. Führen Sie die folgenden Schritte aus, damit die Komponenten in der Liste der verfügbaren Komponenten in AEM Sidekick angezeigt werden:

1. Melden Sie sich bei der Autoreninstanz Ihrer Website an und öffnen Sie eine AEM Sites-Seite.

1. Führen Sie für die Seiten, die eine statische Vorlage verwenden, die folgenden Schritte aus:

   1. Tippen Sie in der Kopfzeile der Seite auf ![canvas-drop-down](assets/canvas-drop-down.png) > **Design**, um die Seite im Design-Modus zu öffnen.
   1. Wählen Sie eine beliebige Komponente (mit blauem Rahmen) und dann ![field-level](assets/field-level.png) aus, um das Absatzsystem auszuwählen, das die aktuelle Komponente enthält.
   1. Wählen Sie im Absatzsystem ![settings_icon](assets/settings_icon.png) aus, um das Dialogfeld „Bearbeiten“ für das Absatzsystem zu öffnen.
   1. Aktivieren Sie in der Liste **[!UICONTROL Zugelassene Komponenten]** die Kontrollkästchen für die Komponenten **[!UICONTROL Dokumentdienst]** und **[!UICONTROL Dokumentdienst-Eigenschaften]**. Wählen Sie **[!UICONTROL OK]** aus.

1. Führen Sie für die Seiten, die eine dynamische Vorlage verwenden, die folgenden Schritte aus:

   1. Wählen Sie in der Kopfzeile der Seite ![Eigenschaften](assets/properties.png) > **Vorlage bearbeiten** aus, um die Vorlage der Seite zu öffnen.
   1. Wählen Sie **Layout-Container** und![FeedManagement](/help/forms/using/assets/feedmanagement.png) aus. Aktivieren Sie auf der Registerkarte **Zugelassene Komponenten** die Optionen **Dokumentendienste und Dokumentendienste-Eigenschaften** und dann ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>Sie können auch bestimmte Komponenten aus diesen Kategorien aktivieren, indem Sie die Komponenten auswählen. Weitere Informationen zu den Komponenten und ihrer Verwendung finden Sie unter [Erstellen einer Formularportalseite](/help/forms/using/creating-form-portal-page.md) und [Einbetten einer Verknüpfungskomponente in eine Seite](/help/forms/using/embedding-link-component-page.md).

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
