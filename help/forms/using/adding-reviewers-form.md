---
title: Verknüpfen von Reviewer mit einem Formular für die Übermittlung
seo-title: Verknüpfen von Reviewer mit einem Formular für die Übermittlung
description: Erfahren Sie, wie Sie Reviewer mit einem Formular in AEM Forms für die Übermittlung verknüpfen. Verknüpfte Reviewer überprüfen ein Formular, das über Formularportal übermittelt wurde.
seo-description: Erfahren Sie, wie Sie Reviewer mit einem Formular in AEM Forms für die Übermittlung verknüpfen. Verknüpfte Reviewer überprüfen ein Formular, das über Formularportal übermittelt wurde.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 76%

---


# Verknüpfen von Reviewer mit einem Formular für die Übermittlung {#associating-submission-reviewers-with-a-form}

Wenn Sie ein Formular erstellen, können Sie Benutzer angeben, die die Übermittlungen des Formulars über das Formularportal überprüfen und Feedback geben. Ihr Unternehmen kann Feedback erfassen und in die übermittelten Formularen einarbeiten.

Mit AEM Forms können Sie eine Reviewer-Gruppe mit einem Formular verknüpfen. Benutzer, die zu einer Reviewer-Gruppe eines Formulars hinzugefügt wurden, sehen die Übermittlungen dieses Formulars und geben Feedback.

Die Reviewer-Gruppen, die mit einem Formular verknüpft sind, können nur die Übertragungen der angegebenen Formulare überprüfen.

## Voraussetzung {#prerequisite}

### Aktivieren der Eigenschaft für Reviewer-Gruppen für adaptive Formulare mithilfe von Metadatenschemaeditoren {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Um eine Reviewer-Gruppe mit einem Formular zu verknüpfen, bearbeiten Sie das Metadatenschema adaptiver Formulare. Standardmäßig können Sie eine Reviewer-Gruppe nicht zu einem eingereichten Formular hinzufügen.

Bearbeiten des Metadatenschemas:

1. Klicken Sie im Autorenmodus unter Experience Manager auf **Extras** >**Assets** >**Metadatenschemas**.
1. Navigieren Sie auf der Seite für die Schemaformulare zu **Formulare** >**Formularen, die in AEM verfasst wurden.** 

   Die URL der Seite lautet:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Wählen Sie **Adaptives Formular** und klicken Sie auf **Bearbeiten**.
1. Wählen Sie auf der Seite „Formular bearbeiten“ **Erweitert**.
1. Ziehen Sie auf der Registerkarte &quot;Erweitert&quot;die Komponente **Einzelzeilentext**, die unter &quot;Formular erstellen&quot;verfügbar ist.
1. Wählen Sie die hinzugefügte Textkomponente aus, um die Einstellungen zu überprüfen.

   Geben Sie unter &quot;Einstellungen&quot;im Feld &quot;Zu Eigenschaft zuordnen&quot;`./jcr:content/metadata/form-submission-reviewer-group` ein.

   Das Feld für die Reviewer-Gruppe-Gruppenfeld in den erweiterten Eigenschaften des adaptiven Formulars wird mit dem Namen aktiviert, den Sie unter „Feldbezeichnung“ angeben.

## Verknüpfen von Reviewer mit einem Formular für die Übermittlung {#associating-submission-reviewers-with-a-form-1}

Um Reviewer mit einem adaptiven Formular zu verknüpfen, erstellen Sie eine Reviewer-Gruppe und fügen Sie Benutzer hinzu. Fügen Sie die erstellte Reviewer-Gruppe unter dem Reviewer-Feld für Formularübermittlungen in den erweiterten Eigenschaften des Formulars hinzu.
Mit Benutzergruppen können Sie verschiedene Sätze von Reviewern für Übermittlungen mit verschiedenen adaptiven Formularen hinzufügen. Diese Funktion verhindert einen Übermittlungsreview von einem nicht autorisierten Benutzer.

Bevor Sie die folgenden Schritte ausführen, lesen Sie die [ Voraussetzungen](../../forms/using/adding-reviewers-form.md#prerequisite).

Um eine Gruppe zu erstellen und ihr Mitglieder hinzuzufügen, navigieren Sie zu **Tools** > **Vorgänge** > **Sicherheit** > **Gruppen**.
Weitere Informationen finden Sie unter [Benutzerverwaltung und Dienste](/help/sites-administering/security.md).
Stellen Sie sicher, dass Sie die erstellte Gruppe als Mitglied der vordefinierten Benutzergruppe hinzufügen: **forms-submission-reviewers**. Diese Benutzergruppe wird mit AEM Forms ausgeliefert und stellt sicher, dass Benutzer als Übermittlungsreviewer hinzugefügt werden.

Verknüpfen von Benutzergruppen mit einem adaptiven Formular:

1. Navigieren Sie im Bearbeitungsmodus zu **Formulare** >**Formulare und Dokumente**.
1. Wählen Sie mit der Option **Select **ein adaptives Formular aus und klicken Sie auf **Ansicht Properties**.
1. Klicken Sie im Fenster „Eigenschaften“ des Formulars auf **Bearbeiten** und dann auf **ERWEITERT**.
1. Geben Sie die Gruppe im Feld „Übermittlungs-Reviewer-Gruppe“ ein und klicken Sie auf **Fertig**.

   Das Feld „Übermittlungs-Reviwer-Gruppe“ wird mit dem Namen angezeigt, den Sie im bearbeiteten Metadatenschema von adaptiven Formularen angegeben haben.

>[!NOTE]
>
>Replizieren Sie Benutzer und Formulare, um die Verfügbarkeit der Benutzer und Formulare in der Remote-Implementierung von AEM Forms sicherzustellen.
>
>Stellen Sie sicher, dass alle Benutzer als Review-Mitglieder der Benutzergruppen in der Remote-Implementierung repliziert werden.

