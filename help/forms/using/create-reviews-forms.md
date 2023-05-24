---
title: Erstellen und Verwalten von Überprüfung in Formularen
seo-title: Creating and managing reviews in forms
description: Eine Überprüfung ist ein Mechanismus, mit dem ein oder mehrere Überprüfer zu einem Formular Kommentare abgeben können.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on a form.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
feature: Adaptive Forms
source-git-commit: 0ca7d76d0f5a3e440e5df9c986e3bb0efec368c1
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 44%

---

# Erstellen und Verwalten von Überprüfungen von Formularen{#creating-and-managing-reviews-to-forms}

## Überprüfung {#review}

Bei einer Überprüfung handelt es sich um einen Mechanismus, mit dem ein oder mehrere Überprüfer Formulare kommentieren können.

## Einrichten einer Überprüfung {#setting-up-a-review}

1. Navigieren Sie zum Formularbrowser und wählen Sie ein zu überprüfendes Formular aus.
1. Wenn für das Formular keine Überprüfung durchgeführt wird, wird ein **Prüfung starten** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) in der Symbolleiste angezeigt. Klicken Sie auf **Prüfung starten** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) Symbol.
1. Geben Sie folgende Informationen ein:

   * **Titel**: Obligatorisch, kann alphanumerische Zeichen, Bindestriche und Unterstriche enthalten.
   * **Beschreibung**: Optional, Beschreibung des Zwecks/Inhalts für die Überprüfung.
   * **Termin**: Optional: das Datum, an dem die Überprüfung endet. Wenn die Frist bereits abgelaufen ist, wird die Aufgabe als „überfällig“ angezeigt.
   * **Überprüfungsname**: Es ist mindestens 1 erforderlich. Verwenden Sie das Kombinationsfeld, um Überprüfer hinzuzufügen, indem Sie eine Namensliste mit allen übereinstimmenden Namen eingeben. einen Namen auswählen und auf **Hinzufügen**. Im nächsten Abschnitt der **Überprüfer** zeigt den Namen aller validierungsverantwortlichen Benutzer an.

1. Klicken Sie auf **Starten** , um eine Überprüfung zu starten.

   >[!NOTE]
   >
   >* Der Administrator kann auf alle Gruppen zugreifen, die mit den Formularbenutzern verknüpft sind.
   >* Die Gruppe der Dienstbenutzenden steht für die Überprüfung nicht zur Auswahl.


### Aktionen beim Einrichten von Überprüfungen {#actions-that-occur-when-a-review-is-set-up}

In diesem Abschnitt wird beschrieben, was passiert, wenn eine Überprüfung erstellt bzw. eingerichtet wird.

1. Eine neue Überprüfungsaufgabe wird erstellt und dem/der ausgewählten Überprüfenden zugewiesen.
1. Allen Reviewern wird eine Überprüfungsaufgabe zugeteilt. Die Aufgabe wird im Abschnitt Benachrichtigungen angezeigt. Reviewer können auf eine Benachrichtigung klicken oder zum Posteingang wechseln, um die Aufgabe anzuzeigen. Reviewer können per Klick die Überprüfungsaufgabe öffnen, das Formular anzeigen und Kommentare hinzufügen.

   ![Warnung bei Reviewerbenachrichtigungen](assets/review-notification-img.png)

   Warnung bei Reviewerbenachrichtigungen

1. Das Kommentarfeld steht den Validierern des Formulars zur Verfügung. Andere können die Kommentare lesen, aber keine eigenen hinzufügen.

## Verwalten einer Überprüfung {#managing-a-review}

>[!NOTE]
>
>* Nur laufende Überprüfungen können geändert werden.
>* Abgeschlossene Überprüfungen können nicht geändert werden.


1. Navigieren Sie zur Registerkarte &quot;Formulare&quot;und wählen Sie ein Formular aus.

1. Wenn in einem Formular eine Überprüfung ausgeführt wird und Sie der Initiator der Überprüfung sind, wird eine **Prüfung verwalten** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) in der Symbolleiste angezeigt. Nur Initiierende von Überprüfungen können die Überprüfung verwalten (aktualisieren/beenden).

   Klicken Sie auf **Prüfung verwalten** ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png)Symbol.

   Für Benutzer, die nicht der Initiator sind, ist das Symbol zum Verwalten von Überprüfungen deaktiviert.

1. Jetzt wird ein Bildschirm mit Informationen angezeigt:

   * **Überprüfungsname**: Kann nicht bearbeitet werden.

   * **Überprüfungsbeschreibung**: Kann bearbeitet werden.

   * **Überprüfungstermin**: Kann bearbeitet werden. Die Werte für Datum und Uhrzeit des Termins können geändert werden, wenn sie in der Zukunft liegen.

   * **Reviewer**: Kann bearbeitet werden. Sie können Reviewer hinzufügen oder entfernen. Wenn eine Aufgabe überfällig ist, können Sie Reviewer erst hinzufügen, wenn Sie den Termin verlängern und er über das aktuelle Datum hinausgeht.

1. Um die Überprüfung zu beenden, klicken Sie auf **Ende**.

### Aktionen beim Ändern einer Überprüfung {#actions-that-occur-when-a-review-is-modified}

In diesem Abschnitt wird beschrieben, was passiert **Überprüfungsaktualisierung/-ende**:

1. Wenn die Überprüfungsbeschreibung geändert wird, wird die entsprechende Aufgabe der Überprüfer und des Initiators aktualisiert.
1. Wenn die Überprüfungsfrist geändert wird, wird die entsprechende Aufgabe für die Überprüfer mit dem neuen Datum aktualisiert.

1. Wenn ein Reviewer entfernt wird:

   ![Entfernen eines Reviewers](assets/removeduser.png)

   Entfernen eines Reviewers

   1. Wenn die zugewiesene Aufgabe unvollständig ist, wird sie beendet.
   1. Der/die Überprüfende kann das Formular nicht mehr kommentieren.

1. Wenn ein Reviewer hinzugefügt wird:

   ![Hinzufügen eines Reviewers](assets/addedreviewer.png)

   Hinzufügen eines Reviewers

   1. Eine Überprüfungsaufgabe wird erstellt und dem neu hinzugefügten Reviewer zugewiesen.
   1. Der/die neu hinzugefügte Überprüfende kann Kommentare zum Formular hinzufügen.

1. Wenn eine Überprüfung abgeschlossen wird:

   1. **Reviewer**: Bei allen Reviewern werden zugewiesene unvollständige Aufgaben beendet. Die Aufgabe wird im Benachrichtigungsabschnitt des Reviewers nicht mehr als „Ausstehend“ angezeigt.
   1. **Initiator**: Die dem Initiator der Überprüfung zugewiesene Aufgabe ist als abgeschlossen markiert. Die Aufgabe wird aus dem Benachrichtigungsabschnitt des Initiators der Überprüfung entfernt.
   1. **Alle**: Die Überprüfung wird im Abschnitt Frühere Prüfungen angezeigt. Es können keine weiteren Kommentare hinzugefügt werden.
   ![Überprüfung abgeschlossen](assets/review-complete-imgg.png)
