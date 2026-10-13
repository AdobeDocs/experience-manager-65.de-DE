---
title: Wie Sie ausgewählten Benutzergruppen Zugriff auf den Regeleditor gewähren
description: Gewähren Sie ausgewählten Benutzergruppen eingeschränkten Zugriff auf den Regeleditor.
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: a1a2b277-3133-404b-a7fc-337cedddb12c
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
source-wordcount: '386'
ht-degree: 100%
---
# Ausgewählten Benutzergruppen Zugriff auf den Regel-Editor gewähren{#grant-rule-editor-access-to-select-user-groups}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird ein älterer Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Übersicht {#overview}

Möglicherweise haben Sie mit unterschiedlichen Typen von Benutzenden mit unterschiedlichen Fähigkeiten zu tun, die mit adaptiven Formularen arbeiten. Während professionelle Benutzer möglicherweise über die nötigen Kenntnisse zum Arbeiten mit Skripten und komplexen Regeln verfügen, genügt es für Benutzer, die nur über Grundkenntnisse verfügen, mit dem Layout und einfachen Eigenschaften adaptiver Formulare zu arbeiten.

AEM Forms ermöglicht es Ihnen, den Zugriff auf den Regeleditor anhand der Rolle oder Funktion der Benutzenden einzuschränken. In den Einstellungen für den Konfigurationsdienst für adaptive Formulare können Sie festlegen, welche [Benutzergruppen](/help/sites-administering/security.md) den Regeleditor anzeigen und auf ihn zugreifen können.

## Angeben von Benutzergruppen für Zugriff auf Regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Melden Sie sich bei AEM Forms als Admin an.
1. Klicken Sie in der Autoreninstanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png)„Adobe Experience Manager“ > „Tools“ ![hammer](assets/hammer.png) > „Vorgänge“ > „Web-Konsole“. Die Web-Konsole wird in einem neuen Fenster geöffnet.

   ![1–2](assets/1-2.png)

1. Suchen Sie im Fenster „Web-Konsole“ nach **[!UICONTROL Konfiguration des Web-Kanals für adaptive Formulare und interaktive Kommunikation]** und klicken Sie darauf. Das Dialogfeld **[!UICONTROL Konfiguration des Web-Kanals für adaptive Formulare und interaktive Kommunikation]** wird angezeigt. Behalten Sie die Werte bei und klicken Sie auf **Speichern**.

   Die Datei „/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config“ im CRX-Repository wird erstellt.

1. Melden Sie sich als Administrator bei CRXDE an. Öffnen Sie die Datei „/apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config“ zum Bearbeiten.
1. Geben Sie mithilfe folgender Eigenschaft den Namen einer Gruppe an, die auf den Regeleditor zugreifen kann (z. B. RuleEditorsUserGroup), und klicken Sie auf **Alle speichern**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Um den Zugriff für mehrere Gruppen zu ermöglichen, geben Sie eine Liste mit kommagetrennten Werten an:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![Benutzer erstellen](assets/create_user_new.png)

   Wenn jetzt eine Person, die nicht zur angegebenen Benutzergruppe (hier: RuleEditorsUserGroup) gehört, auf ein Feld tippt, ist das Symbol „Regel bearbeiten“ (![edit-rules1](assets/edit-rules1.png)) für sie nicht in der Komponenten-Symbolleiste verfügbar:

   ![componentstoolbarwithre](assets/componentstoolbarwithre.png)

   Komponentensymbolleiste für Benutzer mit Zugriff auf Regeleditor

   ![componentstoolbarwithoutre](assets/componentstoolbarwithoutre.png)

   Komponentensymbolleiste für Benutzer ohne Zugriff auf Regeleditor:

   Anweisungen zum Hinzufügen von Benutzern zu Gruppen finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).
