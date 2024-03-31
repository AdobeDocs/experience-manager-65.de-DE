---
title: Konfigurieren von Abwesenheitseinstellungen
description: Die Abwesenheitsfunktion ermöglicht es Ihnen, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1c8ad09b-d44a-4d90-86d5-d4c66cf5c57c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 100%

---

# Konfigurieren von Abwesenheitseinstellungen {#configuring-out-of-office-settings}

Die Abwesenheitsfunktion ermöglicht es Benutzern und Administratoren, Zeiträume anzugeben, in denen ein Benutzer nicht im Hause und deshalb nicht in der Lage ist, vom Arbeitsablauf für AEM Forms zugewiesene Aufgaben auszuführen. Wenn eine Benutzerin oder ein Benutzer als abwesend festgelegt ist, werden die zugehörigen Aufgaben einer oder mehreren anderen angegebenen Personen zugewiesen. Benutzende können ihre Abwesenheitseinstellungen in Workspace ändern, oder Admins können die Einstellungen im Namen einer Person in Forms Workflow ändern.

Beim Erstellen eines Prozesses können Workbench-Benutzende festlegen, ob eine Aufgabe aufgrund von Abwesenheitseinstellungen weitergeleitet werden darf.

## Anzeigen der Abwesenheitsinformationen von Benutzenden {#view-a-user-s-out-of-office-information}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Abwesenheit“.
1. Sie haben im Feld oben auf der Seite „Abwesenheit“ folgende Möglichkeiten:

   **Nach Namen suchen**

   Wählen Sie die Option „Nach Namen suchen“ aus. Geben Sie den Benutzernamen vollständig oder teilweise ein und klicken Sie auf „Suchen“. Wenn Sie das Feld leer lassen, gibt Forms Workflow eine Liste aller Benutzenden zurück.

   **Suche nach Datumsbereich**

   Wählen Sie die Option „Suche nach Datumsbereich“ aus. Geben Sie die Daten „Von“ und „Bis“ und die gewünschten Zeitstempel ein, um die Suchergebnisse einzugrenzen. Klicken Sie auf „Suchen“.

1. Klicken Sie auf einen Benutzernamen, um die Abwesenheitsinformationen dieser Person unterhalb der Liste der Benutzenden anzuzeigen.

## Ändern des Abwesenheitsstatus von Benutzenden {#change-a-user-s-out-of-office-status}

1. Suchen Sie die Person, wie unter [Anzeigen der Abwesenheitsinformationen von Benutzenden](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
1. Klicken Sie auf den Namen der Person, für die Änderungen vorgenommen werden sollen.
1. Wählen Sie in der Liste der aktuellen *Benutzernamen* entweder „Im Hause“ oder „Nicht im Hause“ aus.
1. Klicken Sie auf Speichern.

## Hinzufügen eines Abwesenheitsdatumsbereichs für Benutzende {#add-an-out-of-office-date-range-for-a-user}

1. Suchen Sie die Person, wie unter [Anzeigen der Abwesenheitsinformationen von Benutzenden](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
1. Klicken Sie auf den Namen der Person, für die Änderungen vorgenommen werden sollen.
1. Klicken Sie auf „Datumsbereich hinzufügen“.
1. Geben Sie eine Startzeit und Endzeit ein. Sie können zum Auswählen eines Datums auf das Kalendersymbol klicken. Wenn Sie keine Endzeit angeben, wird der Abwesenheitszeitraum der Person auf unbefristet festgelegt.
1. Klicken Sie auf Speichern.

## Zuweisen von Benutzenden für Aufgaben bei Abwesenheit {#assign-a-user-for-out-of-office-tasks}

Wenn jemand abwesend ist, können Sie eine oder mehrere Personen zuweisen, die alle neuen Aufgaben für diese Person übernimmt. Sie können die folgenden Konfigurationen einrichten:

* Alle neuen Aufgaben werden einer bestimmten Person zugewiesen.
* Weisen Sie Aufgaben nicht neu zu. Neue Aufgaben bleiben der abwesenden Person zugewiesen.
* Eine Standardperson zuweisen, die die meisten Aufgaben der abwesenden Person erhält, aber festlegen, dass Aufgaben aus bestimmten Prozessen anderen Benutzenden neu zugewiesen werden oder der abwesenden Person zugewiesen bleiben.
* Es wird keine Standardperson zugewiesen, aber bestimmte Aufgaben von speziellen Prozessen werden spezifischen Benutzenden zugewiesen.

   1. Suchen Sie die Person, wie unter [Anzeigen der Abwesenheitsinformationen von Benutzenden](configuring-out-office-settings.md#view-a-user-s-out-of-office-information) beschrieben.
   1. Klicken Sie auf den Namen der Person, für die Änderungen vorgenommen werden sollen.
   1. Wählen Sie in der Liste „Standardbenutzer für Abwesenheitsaufgaben“ eine Person aus. Wenn keine Standardperson für die Annahme neu zugewiesener Elemente festgelegt werden soll, wählen Sie „Nicht zuweisen“ aus.

      Wenn der gewünschte Benutzername nicht in der Liste aufgeführt wird, klicken Sie auf „Benutzer suchen“ und führen Sie dann im Dialogfeld „Benutzer suchen“ eine Suche nach der Person durch. Wählen Sie die gewünschte Person aus der Liste aus und klicken Sie auf „Benutzer auswählen“. Sie können im Dialogfeld „Benutzer suchen“ auch auf „Zeitplan des Benutzers anzeigen“ klicken, um den Abwesenheitszeitplan der ausgewählten Person anzuzeigen.

   1. Wenn Prozesse vorhanden sind, die nicht an die Standardperson gesendet werden sollen, klicken Sie auf „Ausnahme hinzufügen“, wählen Sie den Prozess und dann eine andere Person aus der Liste aus. Sie können auch „Nicht zuweisen“ auswählen, damit die Aufgabe der abwesenden Person zugewiesen bleibt.
   1. Klicken Sie auf Speichern.
