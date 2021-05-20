---
title: Mit Aufgaben arbeiten
seo-title: Mit Aufgaben arbeiten
description: Verwenden Sie die Seite „Aufgabensuche“ für die Suche nach Aufgaben anhand von Benutzername oder Aufgaben-ID. Erfahren Sie mehr über die Arbeit mit Aufgaben.
seo-description: Verwenden Sie die Seite „Aufgabensuche“ für die Suche nach Aufgaben anhand von Benutzername oder Aufgaben-ID. Erfahren Sie mehr über die Arbeit mit Aufgaben.
uuid: 630372d5-255f-4ea8-974d-d4f923108673
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9161c8ca-ef33-4ec9-affc-94b5b3e48a4c
exl-id: 375376d1-60b3-49a4-8893-ba9336e6bf7b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 68%

---

# Mit Aufgaben arbeiten {#working-with-tasks}

Verwenden Sie die Seite „Aufgabensuche“ für die Suche nach Aufgaben anhand von Benutzername oder Aufgaben-ID. Die Suchergebnisse werden auf der Seite „Aufgabenliste“ angezeigt. Hier können Sie den Verlauf von Aufgaben aufrufen. Sie können Aufgaben auch neu zuweisen, z. B., wenn einem Benutzer zu viele Aufgaben zugewiesen wurden oder wenn ein Benutzer eine Aufgabenzuweisung fälschlicherweise erhalten hat.

>[!NOTE]
>
>Beim Durchführen von Aufgabensuchen werden für Benutzernamen, die mit einem Nummernzeichen beginnen, keine Ergebnisse zurückgegeben (#). Vermeiden Sie möglichst das Erstellen von Benutzernamen, die mit einem Nummernzeichen beginnen.

## Nach den zu einem Benutzer gehörigen Aufgaben suchen {#search-for-tasks-associated-with-a-user}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Aufgabensuche“.
1. Wählen Sie für „Suchen nach“ die Option „Benutzername“. Wenn Sie einen Teil des gesuchten Benutzernamens kennen, geben Sie ihn in das Feld ein. Klicken Sie auf „Benutzer suchen“.
1. Die Seite „Benutzer suchen“ wird angezeigt. Sie können die Suche weiter optimieren, indem Sie nach Benutzernamen oder E-Mail suchen. Wenn Sie den gesuchten Benutzer gefunden haben, aktivieren Sie das Optionsfeld neben seinem Namen und klicken Sie auf „OK“.
1. Die Aufgabensuche sucht standardmäßig nach Aufgaben, die dem Benutzer aktuell zugewiesen sind. Wenn Sie auch nach Aufgaben suchen möchten, die dem Benutzer zuvor zugewiesen waren, wählen Sie „Nicht zugewiesene Aufgabe anzeigen“. Um auch nach Aufgaben zu suchen, die der Benutzer abgeschlossen hat, wählen Sie „Abgeschlossene Aufgabe anzeigen“.
1. Klicken Sie auf Suchen. Die Seite „Aufgabenliste“ wird mit einer Liste der Suchergebnisse angezeigt.

## Nach einer Aufgabe suchen, wenn Sie die Aufgaben-ID kennen  {#search-for-a-task-when-you-know-its-task-id}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Aufgabensuche“.
1. Wählen Sie in „Suchen nach“ den Eintrag „Aufgaben-ID“ aus und geben Sie die ID der Aufgabe in das Feld ein.
1. Klicken Sie auf Suchen. Die Seite „Aufgabenliste“ wird mit einer Liste der Suchergebnisse angezeigt.

## Mit der Aufgabenliste arbeiten  {#working-with-the-task-list}

Die Ergebnisse der Suche nach Aufgaben werden auf der Seite „Aufgabenliste“ angezeigt. Sie können eine Aufgabe auswählen, um die Seite „Aufgabenverlauf“ zu öffnen. Von hier aus können Sie die Aufgabe einem anderen Benutzer zuweisen.

Die Aufgaben werden mit folgenden Informationen angezeigt:

**Aufgabe-ID:** Die positive Ganzzahl, die der Arbeitsablauf für Formulare zuweist, wenn die Aufgabe instanziiert (von einem Benutzer initiiert) wird. Anhand dieser ID können Sie die Aufgabe während ihres gesamten Lebenszyklus verfolgen. Klicken Sie auf eine Aufgaben-ID, um Informationen zum Aufgabenverlauf anzuzeigen oder die Aufgabe einem anderen Benutzer zuweisen.

**Status:** Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war. Möglich ist auch der Status Abgeschlossen.

**Aktivität:** Zeigt das Formular und den Namen für einen ersten Vorgang oder den Prozessvorgang an, der die Aufgabe generiert hat.

**Prozess-ID:** Diese positive Ganzzahl, die vom Arbeitsablauf für Formulare zugewiesen wird, wenn der Prozess instanziiert wird (d. h. wenn ein Benutzer oder ein automatisierter Schritt einen Prozess initiiert). Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

**Anwendung:** Der Name der Anwendung, zu der der Prozess gehört, wie in Workbench definiert.

**Erstellungsdatum:** Datum und Uhrzeit der Erstellung der Aufgabe.

## Aufgabenverlauf anzeigen und Aufgaben neu zuweisen {#viewing-task-history-and-reassigning-tasks}

Auf der Seite „Aufgabenverlauf“ wird eine Liste der Benutzer und Gruppen angezeigt, die einer bestimmten Aufgabe zugewiesen sind.

Für jede Aufgabenzuweisung werden in der Liste die folgenden Informationen angezeigt:

**Name:** Der Name des Benutzers.

**Status:** Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war.

**Arbeitslisten-ID:** Die numerische Kennung der Benutzerwarteschlange, zu der die Aufgabe gehört. Ein Prozess kann von mehreren Benutzern gemeinsam verwendet werden.

**Typ:** Gibt an, wie die Aufgabe zugewiesen wurde:

**Anfänglich:** Dem Benutzer wurde die Aufgabe ursprünglich zugewiesen.

**Weiterleiten:** Der ursprüngliche Aufgabenbesitzer hat die Aufgabe einem anderen Benutzer zugewiesen.

**Ablehnen:** Eine weitergeleitete Aufgabe wurde abgelehnt oder eine Aufgabe wurde an eine Arbeitsliste zurückgegeben, ohne abgeschlossen zu sein.

**Anspruch:** Der Benutzer hat die Aufgabe in einer freigegebenen Arbeitsliste angefordert.

**Eskalation:** Eine vordefinierte Zeit (wie in der Benutzeraktion in Workbench festgelegt) ohne Benutzerinteraktion verstrichen und einem anderen Benutzer wurde die Aufgabe zugewiesen.

**Besprechen:** Der Aufgabenbesitzer hat diese Aufgabe an einen anderen Benutzer weitergeleitet, der das Formular öffnen, Daten speichern und die Anlagen und Notizen ändern kann, den Schritt jedoch nicht abschließen kann. Der Benutzer muss die Aufgabe an den Aufgabenbesitzer zurückgeben, der sich mit dem Benutzer besprochen hat.

**Admin-Neuzuweisung:** Die Aufgabe wurde von einem Administrator neu zugewiesen.

**Zuweisungsdatum:** Datum und Uhrzeit der Zuweisung der Aufgabe an den Benutzer.

### Einer Aufgabe einen neuen Benutzer zuweisen {#assigning-a-new-user-to-a-task}

Auf der Seite „Benutzer zuweisen“ werden die Benutzer aufgeführt, die einer Aufgabe zugewiesen werden können. Zugriff auf die Seite „Benutzer zuweisen“ erhalten Sie, indem Sie auf der Seite „Aufgabenverlauf“ auf „Neuen Benutzer zuweisen“ klicken.

1. Geben Sie auf der Seite „Benutzer zuweisen“ in das Feld „Suche nach“ den gewünschten Benutzernamen oder die E-Mail-Adresse vollständig oder zum Teil ein.
1. Wählen Sie unter „mit“ den Eintrag „Name“ oder „E-Mail-Adresse“ aus und klicken Sie auf „Suchen“. Die Benutzer, die der Suche entsprechen, werden angezeigt.
1. Wählen Sie den Benutzer in der Liste aus und klicken Sie auf „OK“. Die Seite „Aufgabenverlauf“ wird mit der neuen Benutzerzuweisung angezeigt.
