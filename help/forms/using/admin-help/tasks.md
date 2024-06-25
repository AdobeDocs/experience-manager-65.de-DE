---
title: Arbeiten mit Aufgaben
description: Verwenden Sie die Seite „Aufgabensuche“ für die Suche nach Aufgaben anhand von Benutzername oder Aufgaben-ID. Erfahren Sie mehr über die Arbeit mit Aufgaben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 375376d1-60b3-49a4-8893-ba9336e6bf7b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Arbeiten mit Aufgaben {#working-with-tasks}

Verwenden Sie die Seite „Aufgabensuche“ für die Suche nach Aufgaben anhand von Benutzername oder Aufgaben-ID. Die Suchergebnisse werden auf der Seite „Aufgabenliste“ angezeigt. Hier können Sie den Verlauf von Aufgaben aufrufen. Sie können Aufgaben auch neu zuweisen, z. B. wenn Benutzenden zu viele Aufgaben zugewiesen wurden oder wenn sie eine Aufgabenzuweisung fälschlicherweise erhalten haben.

>[!NOTE]
>
>Beim Durchführen von Aufgabensuchen werden für Benutzernamen, die mit einem Nummernzeichen (#) beginnen, keine Ergebnisse zurückgegeben. Vermeiden Sie möglichst das Erstellen von Benutzernamen, die mit einem Nummernzeichen beginnen.

## Suchen nach Aufgaben, die mit einer Person verknüpft sind {#search-for-tasks-associated-with-a-user}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Aufgabensuche“.
1. Wählen Sie für „Suchen nach“ die Option „Benutzername“. Wenn Sie einen Teil des gesuchten Benutzernamens kennen, geben Sie ihn in das Feld ein. Klicken Sie auf „Benutzer suchen“.
1. Die Seite „Benutzer suchen“ wird angezeigt. Sie können Ihre Suche weiter verfeinern, indem Sie nach Benutzername oder E-Mail suchen. Wenn Sie die gesuchte Person gefunden haben, aktivieren Sie das Optionsfeld neben dem Namen und klicken Sie auf „OK“.
1. Die Aufgabensuche sucht standardmäßig nach Aufgaben, die Benutzenden aktuell zugewiesen sind. Wenn Sie auch nach Aufgaben suchen möchten, die Benutzenden zuvor zugewiesen waren, wählen Sie „Nicht zugewiesene Aufgabe anzeigen“. Um auch nach Aufgaben zu suchen, die Benutzende abgeschlossen haben, wählen Sie „Abgeschlossene Aufgabe anzeigen“.
1. Klicken Sie auf Suchen. Die Seite „Aufgabenliste“ wird mit einer Liste der Suchergebnisse angezeigt.

## Suchen nach einer Aufgabe, wenn Sie die Aufgaben-ID kennen {#search-for-a-task-when-you-know-its-task-id}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Aufgabensuche“.
1. Wählen Sie in „Suchen nach“ den Eintrag „Aufgaben-ID“ aus und geben Sie die ID der Aufgabe in das Feld ein.
1. Klicken Sie auf Suchen. Die Seite „Aufgabenliste“ wird mit einer Liste der Suchergebnisse angezeigt.

## Arbeiten mit der Aufgabenliste {#working-with-the-task-list}

Die Ergebnisse der Suche nach Aufgaben werden auf der Seite „Aufgabenliste“ angezeigt. Sie können eine Aufgabe auswählen, um die Seite „Aufgabenverlauf“ zu öffnen. Von hier aus können Sie die Aufgabe einer anderen Person zuweisen.

Die Aufgaben werden mit den folgenden Informationen angezeigt:

**Aufgaben-ID**: Die positive Ganzzahl, die vom Arbeitsablauf für Formulare zugewiesen wird, wenn die Aufgabe instanziiert (von einem Benutzer initiiert) wird. Anhand dieser ID können Sie die Aufgabe während ihres gesamten Lebenszyklus verfolgen. Klicken Sie auf eine Aufgaben-ID, um Informationen zum Aufgabenverlauf anzuzeigen oder die Aufgabe einer anderen Person zuweisen.

**Status**: Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war. Möglich ist auch der Status Abgeschlossen.

**Aktivität**: Zeigt das Formular und den Namen für einen anfänglichen Vorgang oder den Prozessvorgang an, der die Aufgabe generiert hat.

**Prozess-ID**: Die positive Ganzzahl, die vom Arbeitsablauf für Formulare zugewiesen wird, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname/-version**: Der Name des Prozesses, wie in Workbench definiert.

**Programm**: Der Name des Programms, zu dem der Vorgang gehört, wie in Workbench definiert.

**Erstellungsdatum**: Das Datum und die Uhrzeit, zu der die Aufgabe erstellt wurde.

## Anzeigen des Aufgabenverlaufs und Neuzuweisen von Aufgaben {#viewing-task-history-and-reassigning-tasks}

Auf der Seite „Aufgabenverlauf“ wird eine Liste der Benutzenden und Gruppen angezeigt, die einer bestimmten Aufgabe zugewiesen sind.

Für jede Aufgabenzuweisung werden in der Liste die folgenden Informationen angezeigt:

**Name**: Der Name des Benutzers.

**Status**: Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war.

**Arbeitslisten-ID**: Die numerische Kennung der Benutzerwarteschlange, zu der die Aufgabe gehört. Ein Prozess kann von mehreren Benutzern gemeinsam verwendet werden.

**Typ**: Gibt an, wie die Aufgabe zugewiesen wurde:

**Anfänglich**: Dem Benutzer wurde die Aufgabe ursprünglich zugewiesen.

**Weiterleiten**: Der ursprüngliche Aufgabenbesitzer hat die Aufgabe einem anderen Benutzer zugewiesen.

**Ablehnen**: Eine weitergeleitete Aufgabe wurde abgelehnt, oder eine Aufgabe wurde an eine Arbeitsliste zurückgegeben, ohne erledigt worden zu sein.

**Anfordern**: Der Benutzer hat die Aufgabe in einer freigegebenen Arbeitsliste angefordert.

**Eskalation**: Ein zuvor festgelegter Zeitraum (wie in der Benutzeraktion in Workbench festgelegt) ist ohne Benutzerinteraktion verstrichen, und die Aufgabe wurde einem anderen Benutzer zugewiesen..

**Besprechen**: Der Aufgabenbesitzer hat diese Aufgabe zur Besprechung an einen anderen Benutzer weitergeleitet, der das Formular öffnen, Daten speichern und die Anlagen und Notizen bearbeiten, jedoch nicht den Schritt abschließen darf. Der Benutzer muss die Aufgabe an den Aufgabenbesitzer zurückgeben, der sich mit dem Benutzer besprochen hat.

**Admin-Neuzuweisung**: Die Aufgabe wurde von einem Administrator neu zugewiesen.

**Zuweisungsdatum**: Das Datum und die Uhrzeit, zu der die Aufgabe dem Benutzer zugewiesen wurde.

### Zuweisen einer neuen Person zu einer Aufgabe {#assigning-a-new-user-to-a-task}

Auf der Seite „Benutzer zuweisen“ werden die Benutzenden aufgeführt, die einer Aufgabe zugewiesen werden können. Zugriff auf die Seite „Benutzer zuweisen“ erhalten Sie, indem Sie auf der Seite „Aufgabenverlauf“ auf „Neue Benutzer zuweisen“ klicken.

1. Geben Sie auf der Seite „Benutzer zuweisen“ in das Feld „Suchen“ den gewünschten Benutzernamen oder die E-Mail-Adresse vollständig oder zum Teil ein.
1. Wählen Sie unter „mit“ den Eintrag „Name“ oder „E-Mail-Adresse“ aus und klicken Sie auf „Suchen“. Die Benutzenden, die mit der Suche übereinstimmen, werden angezeigt.
1. Wählen Sie die Person aus der Liste aus und klicken Sie auf „OK“. Die Seite „Aufgabenverlauf“ wird mit der neuen Benutzerzuweisung angezeigt.
