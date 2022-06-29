---
title: Konfigurieren von Abwesenheitseinstellungen
seo-title: Configuring Out of Office Settings
description: Die Abwesenheitsfunktion ermöglicht es Ihnen, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen.
seo-description: The Out of Office feature enables you to specify when a user will be out of the office and unable to complete tasks assigned by AEM forms.
uuid: 0d01df0a-aa6a-40e5-bf24-423ed1c932cc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 30312159-58a5-4781-b554-29dcbce696cb
exl-id: 1c8ad09b-d44a-4d90-86d5-d4c66cf5c57c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '659'
ht-degree: 100%

---

# Konfigurieren von Abwesenheitseinstellungen {#configuring-out-of-office-settings}

Die Abwesenheitsfunktion ermöglicht es Benutzern und Administratoren, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen. Während ein Benutzer auf „Abwesenheit“ festgelegt ist, werden dessen Aufgaben einem oder mehreren anderen festgelegten Benutzern zugewiesen. Benutzer können ihre Abwesenheitseinstellungen in Workspace ändern bzw. Administratoren können die Einstellungen im Auftrag eines Benutzers im Arbeitsablauf für Formulare ändern.

Beim Erstellen eines Prozesses kann der Workbench-Benutzer festlegen, ob eine Aufgabe aufgrund von Abwesenheitseinstellungen weitergeleitet werden darf.

## Die Abwesenheitsinformationen eines Benutzers anzeigen {#view-a-user-s-out-of-office-information}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Abwesenheit“.
1. Sie haben auf der Seite „Abwesenheit“ im Feld am oberen Rand folgende Möglichkeiten:

   **Suche nach Namen**

   Wählen Sie die Option „Suche nach Namen“. Geben Sie den gesamten oder einen Teil des Benutzernamens ein und klicken Sie auf „Suchen“. Wenn Sie das Feld unausgefüllt lassen, gibt der Arbeitsablauf für Formulare eine Liste aller Benutzer zurück.

   **Suche nach Datumsbereich**

   Wählen Sie die Option „Suche nach Datumsbereich“. Geben Sie die Daten „Von“ und „Bis“ und die gewünschten Zeitstempel ein, um die Suchergebnisse einzugrenzen. Klicken Sie auf „Suchen“.

1. Klicken Sie auf einen Benutzernamen, um die Abwesenheitsinformationen dieses Benutzers unterhalb der Liste der Benutzer anzuzeigen.

## Den Abwesenheitsstatus eines Benutzers ändern {#change-a-user-s-out-of-office-status}

1. Suchen Sie nach dem Benutzer, wie unter [Die Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
1. Klicken Sie auf den Namen des Benutzers, der geändert werden soll.
1. Wählen Sie in der Liste „*Benutzername* ist aktuell“ entweder „Im Hause“ oder „Nicht im Hause“ aus.
1. Klicken Sie auf Speichern.

## Einen Abwesenheitsdatumsbereich für einen Benutzer hinzufügen {#add-an-out-of-office-date-range-for-a-user}

1. Suchen Sie nach dem Benutzer, wie unter [Die Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
1. Klicken Sie auf den Namen des Benutzers, der geändert werden soll.
1. Klicken Sie auf „Datumsbereich hinzufügen“.
1. Geben Sie eine Startzeit und Endzeit ein. Sie können zum Auswählen eines Datums auf das Kalendersymbol klicken. Wenn Sie keine Endzeit angeben, wird der Abwesenheitszeitraum des Benutzers auf unbefristet festgelegt.
1. Klicken Sie auf Speichern.

## Einen Benutzer für Abwesenheitsaufgaben zuweisen {#assign-a-user-for-out-of-office-tasks}

Während ein Benutzer nicht im Hause ist, können Sie einen oder mehrere Benutzer zuweisen, die alle neuen Aufgaben für den Benutzer ausführen. Sie können die folgenden Konfigurationen einrichten:

* Zuweisen aller neuen Aufgaben zu einem festgelegten Standardbenutzer.
* Keine Aufgaben werden neu zugewiesen. Neue Aufgaben bleiben dem abwesenden Benutzer zugewiesen.
* Zuweisen eines Standardbenutzers, der die meisten der Aufgaben des Benutzers erhält. Gleichzeitig wird festgelegt, dass Aufgaben von bestimmten Prozessen anderen Benutzern neu zugewiesen werden oder dem abwesenden Benutzer zugewiesen bleiben.
* Es wird kein Standardbenutzer zugewiesen, aber bestimmte Aufgaben von speziellen Prozessen werden spezifischen Benutzern zugewiesen.

   1. Suchen Sie nach dem Benutzer, wie unter [Die Abwesenheitsinformationen eines Benutzers anzeigen](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
   1. Klicken Sie auf den Namen des Benutzers, der geändert werden soll.
   1. Wählen Sie in der Liste „Standardbenutzer für Abwesenheitsaufgaben“ einen Benutzer aus. Wenn kein Standardbenutzer für die Annahme neu zugewiesener Elemente festgelegt werden soll, wählen Sie „Nicht zuweisen“.

      Wenn der gewünschte Benutzername nicht in der Liste aufgeführt wird, klicken Sie auf „Benutzer suchen“ und führen Sie dann im Dialogfeld „Benutzer suchen“ eine Suche nach dem Benutzer durch. Wählen Sie den gewünschten Benutzer aus der Liste aus und klicken Sie auf Benutzer auswählen. Sie können im Dialogfeld „Benutzer suchen“ auch auf „Zeitplan des Benutzers anzeigen“ klicken, um den Abwesenheitszeitplan des ausgewählten Benutzers anzuzeigen.

   1. Wenn Prozesse vorhanden sind, die nicht an den Standardbenutzer gesendet werden sollen, klicken Sie auf „Ausnahme hinzufügen“, wählen Sie den Prozess aus und wählen Sie dann einen anderen Benutzer aus der Liste aus. Darüber hinaus können Sie „Nicht zuweisen“ auswählen, damit die Aufgabe dem abwesenden Benutzer zugewiesen bleibt.
   1. Klicken Sie auf Speichern.
