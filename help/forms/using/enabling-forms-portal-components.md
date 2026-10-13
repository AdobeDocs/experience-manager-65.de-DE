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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: fa155e29-cba2-5e77-9efd-4824be5ce4c8
    internal-label: Forms Portal
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '354'
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
