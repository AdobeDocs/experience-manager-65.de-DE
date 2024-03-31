---
title: Arbeiten mit angehaltenen Vorgängen und Zweigen
description: Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Verzweigungen“ werden die Prozesse angezeigt, die angehalten haben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c96faae0-2b0f-4334-b61c-f13b2d1ec179
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 100%

---

# Arbeiten mit angehaltenen Vorgängen und Zweigen {#working-with-stalled-operations-and-branches}

Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Verzweigungen“ werden die Prozesse angezeigt, die angehalten haben. Ein Prozess kann anhalten, wenn ein Fehler während oder nach der Ausführung eines Vorgangs auftritt, oder wegen eines absichtlichen Anhaltevorgangs im Prozess:

* Vorgänge können aufgrund eines nicht vorhergesehenen Fehlers anhalten. Eine „Verzweigung anhalten“-Vorgang in einem Prozess beendet absichtlich die weitere Ausführung eines Prozesses und erfordert das Eingreifen von Admins.
* Verzweigungen können zwischen Vorgängen während einer Regelauswertung anhalten.

Wenn ein Prozess anhält, werden keine weiteren Vorgänge ausgeführt, bis das Problem behoben und der Vorgang oder die Verzweigung neu gestartet wurde.

Für jedes angehaltene Element werden in der Liste die folgenden Informationen angezeigt:

**Vorgangsname oder Zweigname**: Der Name des Vorgangs oder Zweigs.

**Status**: Für angehaltene Elemente immer ANGEHALTEN.

**Fehler**: Eine kurze Beschreibung des Problems.

**Prozess-ID**: Die positive Ganzzahl, die der Formular-Workflow zuweist, wenn der Prozess instanziiert wird (d. h. wenn ein Benutzer oder ein automatisierter Schritt einen Prozess initiiert). Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname/-version**: Der Name des in Workbench zugewiesenen Prozesses.

**Anhalte-Datum**: Datum und Uhrzeit des Anhaltens des Vorgangs oder Zweigs.

Sie können auf den Seiten „Angehaltene Vorgänge“ bzw. „Angehaltene Verzweigungen“ folgende Aufgaben durchführen:

* Einen Fehler auswählen, um Details dazu anzuzeigen. Wenn Sie einen Fehler auswählen, wird die Seite „Fehlerdetails“ angezeigt.
* Angehaltene Vorgänge beenden oder wiederholen oder angehaltene Verzweigungen wiederholen

## Angehaltene Vorgänge oder Verzweigungen beenden oder wiederholen. {#terminating-or-retrying-stalled-operations-or-branches}

Auf der Seite „Angehaltene Vorgänge“ können Sie die angezeigten Prozessinstanzen beenden.

Wenn Sie eine Prozessinstanz beenden, wird deren Ausführung beendet und es werden keine weiteren Vorgänge ausgeführt. Normalerweise beenden Sie einen Prozess nur dann, wenn er blockiert oder aufgrund eines Fehlers unbrauchbar geworden ist und weder korrigiert noch erneut gestartet werden kann.

Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Verzweigungen“ können Sie den Vorgang oder die Verzweigung wiederholen.

Wenn Sie einen Vorgang wiederholen, wird Forms Workflow eine Aufforderung zum Neustart des Vorgangs gesendet. Wenn der Fehler, der das Anhalten des Prozesses verursacht hat, behoben und die Wiederholungsanfrage erfolgreich ausgeführt wurde, wird der Prozess von dem Punkt an erneut ausgeführt, an dem er angehalten hatte, und der Status ändert sich in WIRD AUSGEFÜHRT. Wenn der Vorgang nicht neu gestartet werden kann, bleibt er ANGEHALTEN und Sie müssen ihn möglicherweise beenden.

### Beenden eines angehaltenen Vorgangs {#terminate-a-stalled-operation}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Fehler – Angehaltene Vorgänge“.
1. Wählen Sie auf der Seite „Angehaltene Vorgänge“ das Element aus, das beendet werden soll, und klicken Sie auf „Beenden“.

### Wiederholen eines angehaltenen Vorgangs oder einer angehaltenen Verzweigung {#retry-a-stalled-operation-or-branch}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ und dann auf „Fehler – Angehaltene Vorgänge“ oder „Fehler – Angehaltene Verzweigung“.
1. Wählen Sie auf der Seite „Angehaltene Vorgänge“ oder „Angehaltene Verzweigungen“ die Elemente aus, die wiederholt werden sollen, und klicken Sie auf „Erneut versuchen“.

## Anzeigen von Fehlerdetails zu angehaltenen Vorgängen oder Verzweigungen {#viewing-error-details-about-stalled-operations-or-branches}

Wenn Sie auf der Seite „Angehaltene Vorgänge“ oder „Angehaltene Verzweigungen“ einen Fehler in der Liste der angehaltenen Elemente auswählen, wird die Seite „Fehlerdetails“ angezeigt, auf der Details zu dem Fehler angezeigt werden, die Ihnen bei der Behebung des Problems helfen können.

Der Text der Fehlermeldung wird in dem Feld am unteren Rand der Seite angezeigt.

Sie können auf der Seite „Fehlerdetails“ ebenfalls angehaltene Vorgänge beenden oder wiederholen und angehaltene Verzweigungen wiederholen.

## Bei nicht vorhandener Eskalationsbenutzerin bzw. nicht vorhandenem Eskalationsbenutzer wird der Prozess nicht angehalten. {#process-does-not-stall-when-escalation-user-does-not-exist}

Fehler treten auf, wenn der Vorgang „Aufgabe zuweisen“ im AEM Forms-Benutzerdienst so konfiguriert ist, dass die Aufgabe nach einem bestimmten Zeitraum an eine andere Person eskaliert wird und die Eskalationsbenutzerin bzw. der Eskalationsbenutzer gelöscht wird, nachdem der Vorgang „Aufgabe zuweisen“ ausgeführt wird, aber bevor die Eskalation eintritt.

Wenn diese Situation eintritt, ändert sich der Zustand des Prozesses und der Aufgabe nicht zur konfigurierten Eskalationszeit und die Eskalation wird nicht durchgeführt, aber der Vorgang wird nicht angehalten. Im Server-Protokoll wird die folgende Meldung angezeigt:

„Der für die Eskalation angegebene Prinzipal ist nicht gültig für taskID: *Nummer*, angegebene Warteschlange: *Nummer*.“

Wenn die Eskalationsbenutzerin bzw. der Eskalationsbenutzer gelöscht wird, bevor die Aufgabe erzeugt wurde (bevor der Vorgang „Aufgabe zuweisen“ ausgeführt wird), wird der Prozess angehalten oder das „InvalidPrincipal“-Ausnahmeereignis wird ausgelöst.

Um dieses Problem zu vermeiden, sollten Sie, bevor Sie eine Person löschen, nach Aufgaben suchen, die zu dieser Person gehören, und sie entsprechend bearbeiten. (Siehe [Arbeiten mit Aufgaben](/help/forms/using/admin-help/tasks.md#working-with-tasks).)
