---
title: Verfassen von kontextsensitiver Hilfe für Formularfelder
description: Mit AEM Forms können Sie kontextbezogene Hilfe zu Feldern und Panels in adaptiven Formularen als Text oder Rich Media, einschließlich Videos, hinzufügen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 6569bfba-9af5-4060-8640-e51d7af46614
solution: Experience Manager, Experience Manager Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 7da902b6-fe94-5180-8e7c-f6d1e38d01d5
    internal-label: Foundation Components
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 95%
---
# Verfassen von kontextsensitiver Hilfe für Formularfelder{#authoring-in-context-help-for-form-fields}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Einführung {#introduction}

Es gibt Situationen, in denen sich Endbenutzer, die ein Formular ausfüllen, nicht sicher sind, wie Informationen in ein bestimmtes Formularfeld einzugeben sind. Für solche Fälle bieten adaptive Formulare die Möglichkeit, Text oder dynamische kontextbezogene Hilfe zu einem Formularfeld hinzuzufügen. Dadurch werden das Ausfüllen des Formulars erleichtert und potenzielle Uneindeutigkeiten für Endbenutzende vermieden.

Dieser Artikel erläutert, wie Autorinnen und Autoren von Formularen kontextbezogene Hilfe beim Erstellen adaptiver Formulare hinzufügen können.

## Hinzufügen kontextbezogener Hilfe {#add-in-context-help}

Sie können kontextbezogene Hilfe mit den folgenden Optionen im Abschnitt „Hilfeinhalt“ der Registerkarte „Eigenschaften“ in der Seitenleiste angeben.

* [Kurzbeschreibung](../../forms/using/authoring-in-field-help.md#p-short-description-p)
* [Lange Beschreibung](../../forms/using/authoring-in-field-help.md#p-long-description-p)

![Kontextbezogene Hilfe für Formularfelder](assets/descriptions.png)

>[!NOTE]
>
>Die lange Beschreibung überschreibt die Kurzbeschreibung. Wenn Sie beide Optionen angegeben haben, wird nur die lange Beschreibung angezeigt.

### Kurzbeschreibung {#short-description}

Das Feld „Kurzbeschreibung“ ermöglicht die Angabe schneller und kurzer Hinweise zum Ausfüllen eines Formularfelds. Der im Feld „Kurzbeschreibung“ eingegebene Text wird beim Bewegen des Mauszeigers über das Feld als QuickInfo angezeigt.

![Kurzbeschreibung zum Hinzufügen von kontextbezogener Hilfe für Formularfelder](assets/tooltip.png)

>[!NOTE]
>
>Wählen Sie **Kurzbeschreibung immer anzeigen** aus, um den Hilfetext unterhalb des Felds immer anzuzeigen.

![Dauerhafte kontextbezogene kurze Hilfe unter dem Feld](assets/short1.png)

### Lange Beschreibung {#long-description}

Sie können das Feld „Lange Beschreibung“ verwenden, um langen Text anzugeben oder Rich-Media-Inhalte (einschließlich Videos) als kontextbezogene Hilfe einzubetten. Beispiel: Das folgende Bild zeigt, wie Sie ein Video als kontextbezogene Hilfe einbetten können.

![Hinzufügen von Rich-Media als kontextbezogene Hilfe für Formularfelder](assets/long-descriptions.png)

Durch Hinzufügen einer langen Beschreibung wird ein **angezeigt?** Symbol neben dem Feld. Durch Klicken auf dieses Symbol wird der Inhalt angezeigt, der im Abschnitt „Lange Beschreibung“ hinzugefügt wurde.

![Beispiel für kontextbezogene Rich-Media-Hilfe](assets/photoshop.png)

### Hilfe auf Bereichsebene {#panel-level-help}

Zusätzlich zur kontextbezogenen Hilfe für Formularfelder können Sie auf der Registerkarte „Hilfeinhalt“ des Dialogfelds zum Bearbeiten von Bereichen auch Hilfe auf Bereichsebene angeben.

![Hinzufügen von kontextbezogener Hilfe für einen Formularbereich](assets/panel-level-help.png)

Beim Hinzufügen der Hilfe für das Bedienfeld wird ein **angezeigt?** Symbol neben der Beschreibung des Bedienfelds. Durch Klicken auf das Symbol wird der Inhalt angezeigt, der im Abschnitt „Hilfeinhalt“ des Dialogfelds zur Bearbeitung des Panels hinzugefügt wurde.

![Beispiel für kontextbezogene Hilfe auf Formularbereichsebene](assets/photoshop-1.png)
