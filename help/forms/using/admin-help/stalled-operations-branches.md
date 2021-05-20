---
title: Arbeiten mit angehaltenen Vorgängen und Zweigen
seo-title: Arbeiten mit angehaltenen Vorgängen und Zweigen
description: Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Zweige“ werden die Prozesse angezeigt, die angehalten haben.
seo-description: Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Zweige“ werden die Prozesse angezeigt, die angehalten haben.
uuid: 5f6202b0-79c2-4c3c-847a-236c0366e60b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8c2567f3-7220-436a-b9f2-2824a98c1ccc
exl-id: c96faae0-2b0f-4334-b61c-f13b2d1ec179
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 89%

---

# Arbeiten mit angehaltenen Vorgängen und Zweigen {#working-with-stalled-operations-and-branches}

Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Zweige“ werden die Prozesse angezeigt, die angehalten haben. Ein Prozess kann anhalten, wenn ein Fehler während oder nach der Ausführung eines Vorgangs auftritt, oder wegen eines absichtlichen Anhaltevorgangs im Prozess:

* Vorgänge können aufgrund eines nicht vorhergesehenen Fehlers anhalten. Ein „Zweig anhalten“-Vorgang in einem Prozess beendet absichtlich die weitere Ausführung eines Prozesses und erfordert das Eingreifen des Administrators.
* Zweige können zwischen Vorgängen während einer Regelauswertung anhalten.

Wenn ein Prozess anhält, werden weitere Vorgänge erst wieder ausgeführt, wenn das Problem behoben ist und der Vorgang oder Zweig erneut gestartet wurde.

Für jedes angehaltene Element werden in der Liste die folgenden Informationen angezeigt:

**Vorgangsname oder Verzweigungsname:** Der Name des Vorgangs oder Zweigs.

**Status:** Für angehaltene Elemente immer ANGEHALTEN.

**Fehler:** Eine kurze Beschreibung des Problems.

**Prozess-ID:** Die positive ganze Zahl, die der Arbeitsablauf für Formulare beim Instanziieren des Prozesses zuweist (d. h. wenn ein Benutzer oder ein automatisierter Schritt einen Prozess initiiert). Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Name des in Workbench zugewiesenen Prozesses.

**Angehaltenes Datum:** Datum und Uhrzeit der Unterbrechung des Vorgangs oder Zweigs.

Sie können auf den Seiten „Angehaltene Vorgänge“ bzw. „Angehaltene Zweige“ folgende Aufgaben durchführen:

* Einen Fehler auswählen, um Details dazu anzuzeigen. Wenn Sie einen Fehler auswählen, wird die Seite „Fehlerdetails“ angezeigt.
* Angehaltene Vorgänge beenden oder wiederholen bzw. angehaltene Zweige wiederholen

## Angehaltene Vorgänge oder Zweige beenden oder wiederholen {#terminating-or-retrying-stalled-operations-or-branches}

Auf der Seite „Angehaltene Vorgänge“ können Sie die angezeigten Prozessinstanzen beenden.

Wenn Sie eine Prozessinstanz beenden, wird deren Ausführung beendet und es werden keine weiteren Vorgänge ausgeführt. Normalerweise beenden Sie einen Prozess nur dann, wenn er blockiert oder aufgrund eines Fehlers unbrauchbar geworden ist und weder korrigiert noch erneut gestartet werden kann.

Auf den Seiten „Angehaltene Vorgänge“ und „Angehaltene Zweige“ können Sie den Vorgang oder Zweig wiederholen.

Wenn Sie einen Vorgang wiederholen, wird eine Anforderung zum erneuten Starten des Vorgangs an den Arbeitsablauf für Formulare gesendet. Wenn der Fehler, der das Anhalten des Prozesses verursacht hat, behoben und die Wiederholungsanforderung erfolgreich ausgeführt wurde, wird der Prozess von dem Punkt an erneut ausgeführt, an dem er angehalten hatte, und der Status ändert sich in WIRD AUSGEFÜHRT. Wenn der Vorgang nicht neu gestartet werden kann, bleibt er ANGEHALTEN und Sie müssen ihn möglicherweise beenden.

### Einen angehaltenen Vorgang beenden  {#terminate-a-stalled-operation}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Fehler - Angehaltene Vorgänge“.
1. Wählen Sie auf der Seite „Angehaltene Vorgänge“ das Element aus, das beendet werden soll, und klicken Sie auf „Beenden“.

### Einen angehaltenen Vorgang oder Zweig wiederholen  {#retry-a-stalled-operation-or-branch}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ und dann auf „Fehler - Angehaltene Vorgänge“ oder „Fehler - Angehaltener Zweig“.
1. Wählen Sie auf der Seite „Angehaltene Vorgänge“ oder „Angehaltene Zweige“ die Elemente aus, die wiederholt werden sollen, und klicken Sie auf „Erneut versuchen“.

## Fehlerdetails zu angehaltenen Vorgängen oder Zweigen anzeigen  {#viewing-error-details-about-stalled-operations-or-branches}

Wenn Sie auf der Seite „Angehaltene Vorgänge“ oder „Angehaltene Zweige“ einen Fehler in der Liste angehaltener Elemente auswählen, wird die Seite „Fehlerdetails“ angezeigt, auf der Detailinformationen zu dem Fehler angezeigt werden, die Ihnen bei der Behebung des Problems helfen können.

Der Text der Fehlermeldung wird in dem Feld am unteren Rand der Seite angezeigt.

Sie können auf der Seite „Fehlerdetails“ ebenfalls angehaltene Vorgänge beenden oder wiederholen und angehaltene Zweige wiederholen.

## Bei nicht vorhandenem Eskalationsbenutzer wird der Prozess nicht angehalten  {#process-does-not-stall-when-escalation-user-does-not-exist}

Fehler treten auf, wenn der Vorgang „Aufgabe zuweisen“ im AEM Forms-User-Dienst so konfiguriert ist, dass die Aufgabe nach einem bestimmten Zeitraum an einen anderen Benutzer eskaliert wird und der Eskalationsbenutzer gelöscht wird, nachdem der Vorgang „Aufgabe zuweisen“ ausgeführt wird, aber bevor die Eskalation eintritt.

Wenn diese Situation eintritt, ändert sich der Zustand des Prozesses und der Aufgabe nicht zur konfigurierten Eskalationszeit und die Eskalation wird nicht durchgeführt, aber der Vorgang wird nicht angehalten. Im Serverprotokoll wird eine Meldung wie die folgende angezeigt:

„Der für die Eskalation angegebene Prinzipal ist nicht gültig für taskID: *Nummer*, angegebene Warteschlange: *Nummer*.“

Wenn der Eskalationsbenutzer gelöscht wird, bevor die Aufgabe erzeugt wurde (bevor der Vorgang „Aufgabe zuweisen“ ausgeführt wird), wird der Prozess angehalten oder das „InvalidPrincipal“-Ausnahmeereignis wird erzeugt.

Um dieses Problem zu vermeiden, sollten Sie, bevor Sie einen Benutzer löschen, nach Aufgaben suchen, die zu diesem Benutzer gehören und sie entsprechend bearbeiten. (Siehe [Mit Aufgaben arbeiten](/help/forms/using/admin-help/tasks.md#working-with-tasks).)
