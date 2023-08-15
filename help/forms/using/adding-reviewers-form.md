---
title: Verknüpfen von Übermittlungs-Reviewern mit einem Formular
seo-title: Associating submission reviewers with a form
description: Erfahren Sie, wie Sie Reviewer mit einem Formular in AEM Forms für die Übermittlung verknüpfen. Verknüpfte Reviewer überprüfen ein Formular, das über das Formularportal übermittelt wurde.
seo-description: Learn how to associate submission reviewers with a form in AEM Forms. Associated reviewers review a form submitted via forms portal.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
docset: aem65
feature: Adaptive Forms
exl-id: 46e7b858-44d1-41c8-9f44-4e959e593dc1
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 73%

---

# Zuweisen von Übermittlungsprüfern mit einem Formular {#associating-submission-reviewers-with-a-form}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

Wenn Sie ein Formular erstellen, können Sie Benutzer angeben, die die Übermittlungen des Formulars über das Formularportal überprüfen und Feedback geben. Ihr Unternehmen kann Feedback erfassen und die gesendeten Formulare überarbeiten.

Mit AEM Forms können Sie eine Reviewer-Gruppe mit einem Formular verknüpfen. Benutzer, die einer Reviewer-Gruppe eines Formulars hinzugefügt wurden, können Übermittlungen dieses Formulars sehen und Feedback hinterlassen.

Die Reviewer-Gruppen, die mit einem Formular verknüpft sind, können nur die Übermittlungen der angegebenen Formulare überprüfen.

## Voraussetzung {#prerequisite}

### Aktivieren der Eigenschaft für Reviewer-Gruppen für adaptive Formulare mithilfe des Metadatenschema-Editors {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Um eine Reviewer-Gruppe mit einem Formular zu verknüpfen, bearbeiten Sie das Metadatenschema der adaptiven Formulare. Standardmäßig können Sie eine Reviewer-Gruppe nicht zu einem übermittelten Formular hinzufügen.

So bearbeiten Sie das Metadatenschema:

1. Klicken Sie im Autorenmodus unter Experience Manager auf **Extras** > **Assets** > **Metadatenschemas**.
1. Navigieren Sie auf der Seite für die Schemaformulare zu **Formulare** > **Formularen, die in AEM verfasst wurden.**

   Die URL der Seite lautet:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Wählen Sie **adaptives Formular** und klicken Sie auf **Bearbeiten**.
1. Klicken Sie auf der Seite „Formular bearbeiten“ auf **Erweitert**.
1. Ziehen Sie die Komponente **Einzeiliger Text**, die unter „Formular erstellen“ verfügbar ist, auf die Registerkarte „Erweitert“ und legen Sie sie dort ab.
1. Wählen Sie die hinzugefügte Textkomponente aus, um die Einstellungen zu überprüfen.

   Geben Sie unter „Einstellungen“ im Feld „Zu Eigenschaft zuordnen“ `./jcr:content/metadata/form-submission-reviewer-group` ein.

   Das Feld für die Reviewer-Gruppe-Gruppenfeld in den erweiterten Eigenschaften des adaptiven Formulars wird mit dem Namen aktiviert, den Sie unter „Feldbezeichnung“ angeben.

## Verknüpfen von Übermittlungs-Reviewern mit einem Formular {#associating-submission-reviewers-with-a-form-1}

Um Reviewer für die Übermittlung mit einem adaptiven Formular zu verknüpfen, erstellen Sie eine Reviewer-Gruppe und fügen Sie ihr Benutzer hinzu. Fügen Sie die erstellte Reviewer-Gruppe unter dem Reviewer-Feld für Formularübermittlungen in den erweiterten Eigenschaften des Formulars hinzu.
Mit Benutzergruppen können Sie verschiedene Sätze von Reviewern für Übermittlungen mit verschiedenen adaptiven Formularen hinzufügen. Diese Funktion verhindert eine Übermittlungsüberprüfung durch nicht autorisierte Benutzer.

Bevor Sie folgende Schritte ausführen, lesen Sie die [Voraussetzung](../../forms/using/adding-reviewers-form.md#prerequisite).

Um eine Gruppe zu erstellen und ihr Mitglieder hinzuzufügen, navigieren Sie zu **Tools** > **Vorgänge** > **Sicherheit** > **Gruppen**.
Weitere Informationen finden Sie unter [Benutzerverwaltung und Services](/help/sites-administering/security.md).
Stellen Sie sicher, dass Sie die von Ihnen erstellte Gruppe als Mitglied der standardmäßigen Benutzergruppe hinzufügen: **forms-submission-reviewers**. Diese Benutzergruppe ist bereits in AEM Forms vorhanden. Mit ihr wird sichergestellt, dass Benutzer als Übermittlungs-Reviewer hinzugefügt werden.

So verknüpfen Sie Benutzergruppen mit einem adaptiven Formular:

1. Navigieren Sie im Bearbeitungsmodus zu **Formulare** > **Formulare und Dokumente**.
1. Verwenden Sie die Option „Auswählen“, um ein adaptives Formular auszuwählen, und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie im Fenster „Eigenschaften“ des Formulars auf **Bearbeiten** und dann auf **ERWEITERT**.
1. Geben Sie die Gruppe im Feld „Übermittlungs-Reviewer-Gruppe“ ein und klicken Sie auf **Fertig**.

   Das Feld „Übermittlungs-Reviwer-Gruppe“ wird mit dem Namen angezeigt, den Sie im bearbeiteten Metadatenschema von adaptiven Formularen angegeben haben.

>[!NOTE]
>
>Replizieren Sie Benutzer und Formulare, um die Verfügbarkeit der Benutzer und Formulare in der Remote-Implementierung von AEM Forms sicherzustellen.
>
>Stellen Sie sicher, dass alle Benutzer als Review-Mitglieder der Benutzergruppen in der Remote-Implementierung repliziert werden.
