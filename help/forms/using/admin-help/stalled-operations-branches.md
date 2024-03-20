---
title: Arbeiten mit angehaltenen Vorgängen und Zweigen
description: Auf der Seite "Angehaltene Vorgänge"und auf der Seite "Angehaltene Zweige"werden die Prozesse angezeigt, die angehalten wurden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c96faae0-2b0f-4334-b61c-f13b2d1ec179
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 14%

---

# Arbeiten mit angehaltenen Vorgängen und Zweigen {#working-with-stalled-operations-and-branches}

Auf der Seite &quot;Angehaltene Vorgänge&quot;und auf der Seite &quot;Angehaltene Zweige&quot;werden die Prozesse angezeigt, die angehalten wurden. Ein Prozess kann anhalten, wenn während oder nach der Ausführung eines Vorgangs ein Fehler auftritt oder wenn im Prozess ein absichtlicher Unterbrechungsvorgang stattfindet:

* Vorgänge können aufgrund eines unvorhergesehenen Fehlers anhalten. Ein Vorgang &quot;Zweig anhalten&quot;in einem Prozess stoppt jedoch absichtlich die Ausführung eines Prozesses und erfordert, dass der Administrator eingreift.
* Verzweigungen können während einer Regelauswertung zwischen Vorgängen anhalten.

Wenn ein Prozess angehalten wird, werden keine weiteren Vorgänge ausgeführt, bis das Problem behoben und der Vorgang oder Zweig neu gestartet wurde.

Für jedes angehaltene Element werden in der Liste die folgenden Informationen angezeigt:

**Vorgangsname oder Zweigname**: Der Name des Vorgangs oder Zweigs.

**Status**: Für angehaltene Elemente immer ANGEHALTEN.

**Fehler**: Eine kurze Beschreibung des Problems.

**Prozess-ID**: Die positive Ganzzahl, die der Formular-Workflow zuweist, wenn der Prozess instanziiert wird (d. h. wenn ein Benutzer oder ein automatisierter Schritt einen Prozess initiiert). Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname/-version**: Der Name des in Workbench zugewiesenen Prozesses.

**Anhalte-Datum**: Datum und Uhrzeit des Anhaltens des Vorgangs oder Zweigs.

Sie können die folgenden Aufgaben auf der Seite &quot;Angehaltene Vorgänge&quot;oder &quot;Angehaltene Zweige&quot;ausführen:

* Wählen Sie einen Fehler aus, um Details dazu anzuzeigen. Wenn Sie einen Fehler auswählen, wird die Seite Fehlerdetails angezeigt.
* Angehaltene Vorgänge beenden oder wiederholen oder angehaltene Zweige wiederholen

## Beenden oder Wiederholen angehaltener Vorgänge oder Zweige {#terminating-or-retrying-stalled-operations-or-branches}

Auf der Seite &quot;Angehaltene Vorgänge&quot;können Sie die angezeigten Prozessinstanzen beenden.

Wenn Sie eine Prozessinstanz beenden, wird sie nicht mehr ausgeführt und es werden keine weiteren Vorgänge ausgeführt. Normalerweise beenden Sie einen Prozess nur, wenn er aufgrund eines Fehlers blockiert oder unbrauchbar wird und nicht repariert und neu gestartet werden kann.

Auf der Seite &quot;Angehaltene Vorgänge&quot;oder &quot;Angehaltene Zweige&quot;können Sie den Vorgang oder Zweig erneut versuchen.

Wenn Sie einen Vorgang wiederholen, wird eine Anforderung zum Neustart des Vorgangs an den Forms-Workflow gesendet. Wenn der Fehler, der zum Anhalten des Prozesses geführt hat, behoben wurde und die Wiederholungsanforderung erfolgreich war, wird der Prozess ab dem Zeitpunkt, zu dem er angehalten wurde, erneut ausgeführt, und sein Status wechselt zu WIRD AUSGEFÜHRT. Wenn der Vorgang nicht neu gestartet werden kann, bleibt er ANGEHALTEN und Sie müssen ihn möglicherweise beenden.

### Angehaltener Vorgang beenden {#terminate-a-stalled-operation}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Fehler - Angehaltene Vorgänge&quot;.
1. Wählen Sie auf der Seite &quot;Angehaltene Vorgänge&quot;das Element aus, das beendet werden soll, und klicken Sie auf Beenden .

### Wiederholen eines angehaltenen Vorgangs oder Zweigs {#retry-a-stalled-operation-or-branch}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;und dann auf &quot;Fehler - Angehaltene Vorgänge&quot;oder &quot;Fehler - Angehaltene Verzweigung&quot;.
1. Wählen Sie auf der Seite &quot;Angehaltene Vorgänge&quot;oder &quot;Angehaltene Zweige&quot;das Element aus, das Sie erneut versuchen möchten, und klicken Sie auf &quot;Wiederholen&quot;.

## Anzeigen von Fehlerdetails zu angehaltenen Vorgängen oder Zweigen {#viewing-error-details-about-stalled-operations-or-branches}

Wenn Sie auf der Seite &quot;Angehaltene Vorgänge&quot;oder &quot;Angehaltene Verzweigungen&quot;einen Fehler aus der Liste der angehaltenen Elemente auswählen, wird die Seite &quot;Fehlerdetails&quot;angezeigt, auf der Details zum Fehler angezeigt werden, die Ihnen bei der Problembehebung helfen können.

Das Feld am unteren Rand der Seite enthält die Fehlerinformationen.

Sie können auf der Seite &quot;Fehlerdetails&quot;auch angehaltene Vorgänge beenden oder wiederholen und angehaltene Zweige wiederholen.

## Der Prozess wird nicht angehalten, wenn kein Eskalationsbenutzer vorhanden ist {#process-does-not-stall-when-escalation-user-does-not-exist}

Fehler treten auf, wenn der Vorgang &quot;Assign Task&quot;im AEM forms User-Dienst so konfiguriert ist, dass die Aufgabe nach einem bestimmten Zeitraum an einen anderen Benutzer eskaliert wird und der Eskalationsbenutzer gelöscht wird, nachdem der Vorgang &quot;Assign Task&quot;ausgeführt wurde, aber bevor die Eskalation erfolgt.

Wenn diese Situation eintritt, ändert sich der Status des Prozesses und der Aufgabe zum konfigurierten Eskalationszeitpunkt nicht und die Eskalation erfolgt nicht, aber der Prozess wird nicht angehalten. Die folgende Meldung wird im Serverprotokoll angezeigt:

&quot;Der für die Eskalation angegebene Prinzipal ist für taskID ungültig: *number*, angegebene Warteschlange: *number*.&quot;

Wenn der Eskalationsbenutzer gelöscht wird, bevor die Aufgabe generiert wird (bevor der Vorgang &quot;Assign Task&quot;ausgeführt wird), wird der Prozess angehalten oder das Ereignis &quot;InvalidPrincipal&quot;-Ausnahme wird ausgelöst.

Um dieses Problem zu vermeiden, suchen Sie beim Löschen eines Benutzers nach Aufgaben, die zu diesem Benutzer gehören, und behandeln Sie diese entsprechend. (Siehe [Arbeiten mit Aufgaben](/help/forms/using/admin-help/tasks.md#working-with-tasks).)
