---
title: Prozesse verwalten
seo-title: Managing Processes
description: Auf der Seite „Prozessliste“ werden die Prozesse angezeigt, die von einem Benutzer initiiert oder automatisch gestartet wurden. Erfahren Sie mehr über die Verwaltung der Prozesse.
seo-description: The Process List page shows the processes that a user has initiated or that were started automatically. Learn more about managing the processes.
uuid: 4cd17400-681a-4e40-996c-7dda57ce449a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 37e702c2-8716-4360-a3eb-d9877b28cc86
exl-id: 21a2317d-3542-4ccb-98db-3cedf20c89ea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1631'
ht-degree: 100%

---

# Prozesse verwalten {#managing-processes}

Auf der Seite „Prozessliste“ werden die Prozesse angezeigt, die von einem Benutzer initiiert oder automatisch gestartet wurden.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“. In der Prozessliste werden die folgenden Informationen angezeigt:

   **Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

   **Anwendung:** Die Anwendung, zu der der Prozess gehört, wie in Workbench definiert.

   **Status:** Aktiv bedeutet, dass es sich um den Prozess handelt, der für die Prozessversion aktiviert wurde. Inaktiv bedeutet, dass der Prozess eine alte Version ist, von der immer noch Prozessinstanzen vorhanden sind.

   **Erstellungsdatum:** Datum und Uhrzeit der Bereitstellung des Prozesses.

1. Klicken Sie auf einen Prozessnamen, um dessen Prozessinstanzen auf der Seite „Prozessinstanz“ anzuzeigen.

## Mit Prozessinstanzen arbeiten {#working-with-process-instances}

Wenn Sie über die Seite „Prozessliste“ auf die Seite „Prozessinstanz“ zugreifen, werden alle Prozessinstanzen des ausgewählten Prozesses aufgelistet. Wenn Sie nach einem Suchvorgang auf die Seite „Prozessinstanz“ zugreifen, werden nur die gefundenen Prozessinstanzen aufgeführt.

Für jede Prozessinstanz werden in der Liste die folgenden Informationen angezeigt:

**Prozess-ID:** Dieser Bezeichner wird vom Formular-Workflow zugewiesen, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

**Status:** Zeigt an, ob die Prozessinstanz normal ausgeführt wird, den Status wechselt oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Erstellungsdatum:** Datum und die Uhrzeit, zu der die Prozessinstanz erstellt wurde.

**Aktualisierungsdatum:** Datum und Uhrzeit der letzten Änderung des Status der Prozessinstanz.

Sie können folgende Aufgaben auf der Seite „Prozessinstanz“ ausführen:

* Eine Prozessinstanz auswählen, um Detailinformationen dazu anzuzeigen, wie z. B. Vorgänge und Teilprozesse. Wenn Sie eine Prozessinstanz auswählen, wird die Seite „Prozessinstanzdetail“ angezeigt.
* Prozessinstanzen aussetzen, deren Aussetzung aufheben oder beenden.
* Nach einer Prozessinstanz suchen. Klicken Sie zum Starten einer Suche auf „Suchen“.

### Informationen zum Status von Prozessinstanzen {#about-process-instance-statuses}

Eine Prozessinstanz, einschließlich ihrer Teilprozesse, kann folgende Status haben:

**ABGESCHLOSSEN:** Alle Zweige und Vorgänge in der Prozessinstanz wurden abgeschlossen. Dies ist der endgültige Status einer Prozessinstanz.

**ABSCHLIESSEND:** Der Status der Prozessinstanz ist dabei, auf ABGESCHLOSSEN zu wechseln.

**INITIALISIERT:** Die Prozessinstanz wurde erstellt, wird aber noch nicht ausgeführt. Dies ist der erste Status einer Prozessinstanz.

**WIRD AUSGEFÜHRT:** Die Prozessinstanz wird normal ausgeführt. Möglicherweise ist ein automatischer Schritt aktiv oder die Prozessinstanz empfängt eventuell Benutzereingaben bzw. wartet auf Benutzerinteraktion.

**AUSGESETZT:** Die Prozessinstanz wurde von einem Administrator oder einem Schritt im Prozess ausgesetzt. Bis zur Änderung des Status werden keine weiteren Vorgänge ausgeführt.

**AUSSETZEND:** Der Status ist dabei, auf AUSGESETZT zu wechseln. Wenn ein Vorgang so angelegt wurde, dass er Aussetzanforderungen ignoriert, und dieser noch nicht abgeschlossen ist, muss dieser Vorgang zuerst abgeschlossen werden, damit die Prozessinstanz ausgesetzt werden kann.

**BEENDET:** Die Prozessinstanz wurde von einem Administrator beendet.

**ABSCHLIESSEND:** Der Status ist dabei, auf BEENDET zu wechseln. Wenn ein Vorgang so angelegt wurde, dass er Beenden-Anforderungen ignoriert, und dieser noch nicht abgeschlossen ist, muss dieser Vorgang zuerst abgeschlossen werden, damit die Prozessinstanz beendet werden kann.

**AUSSETZUNG WIRD AUFGEHOBEN:** Der Status ist dabei, von AUSGESETZT auf WIRD AUSGEFÜHRT zu wechseln.

>[!NOTE]
>
>Wenn eine Anforderung zum Wechseln des Status einer Prozessinstanz gesendet wird (z. B. Aussetzen oder Beenden), wird die Anforderung in die Befehlswarteschlange für den Arbeitsablauf für Formulare eingereiht. In Abhängigkeit von der Größe der Warteschlange und der allgemeinen Systemverarbeitungsgeschwindigkeit ändert sich der angezeigte Status möglicherweise erst, nachdem die Seite mehrmals neu geladen wurde.

### Prozessinstanzen aussetzen oder die Aussetzung aufheben {#suspend-or-unsuspend-process-instances}

Wenn Sie ein Problem beheben müssen oder wissen, dass es bei einem späteren Schritt in einer Prozessinstanz aufgrund externer Bedingungen zu Problemen kommt, können Sie die Prozessinstanz vorübergehend aussetzen.

Sie können Prozessinstanzen mit dem Status WIRD AUSGEFÜHRT aussetzen.

Nach dem Aussetzen einer Prozessinstanz wechselt deren Status zuerst auf WIRD AUSGESETZT, dann auf AUSGESETZT, und der Prozess hält beim aktuellen Vorgang an. Die Prozessinstanz bleibt in diesem Status, bis dieser auf AUSSETZEN WIRD AUFGEHOBEN geändert wird.

Nur Prozessinstanzen mit dem Status AUSGESETZT können auf AUSSETZEN WIRD AUFGEHOBEN geändert werden.

Wenn Sie die Aussetzung einer Prozessinstanz aufheben, wechselt deren Status auf WIRD AUSGEFÜHRT und der Prozess fährt mit dem Vorgang fort, bei dem er ausgesetzt wurde.

Wenn Sie eine Prozessinstanz aussetzen, die andere (untergeordnete) Prozesse mithilfe ihres jeweiligen Aufrufvorgangs aufgerufen hat, werden die untergeordneten Prozesse ebenfalls ausgesetzt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“.
1. Wählen Sie auf der Seite „Prozessinstanz“ den Prozess aus und klicken Sie auf „Aussetzen“ oder „Aussetzen aufheben“.

### Prozessinstanzen beenden {#terminate-a-process-instances}

Wenn ein Vorgang einer Prozessinstanz angehalten hat oder ein anderer Fehlerzustand eingetreten ist, bzw. wenn Sie die Beendigung der Ausführung einer Prozessinstanz erzwingen müssen, können Sie die Prozessinstanz beenden.

Sie können Prozessinstanzen mit beliebigem Status beenden.

Wenn Sie eine Prozessinstanz beenden, wechselt deren Status zuerst auf WIRD BEENDET, dann auf BEENDET, und der Prozess wird an der aktuellen Position beendet. Es werden keine weiteren Vorgänge ausgeführt und alle zugeordneten Vorgänge und Aufgaben werden beendet.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“.
1. Wählen Sie auf der Seite „Prozessinstanz“ den Prozess aus und klicken Sie auf „Beenden“.

## Mit Prozessinstanzdetails arbeiten {#working-with-process-instance-details}

Auf der Seite „Prozessinstanzdetail“ wird der Verlauf einer Prozessinstanz angezeigt.

Im Bereich „Zusammenfassung“ werden grundlegende Informationen zur Prozessinstanz angezeigt.

Auf der Registerkarte „Vorgänge“ werden die Vorgänge für die Prozessinstanz beginnend mit dem ersten nacheinander in der Reihenfolge angezeigt, in der sie abgeschlossen wurden. Die folgenden Informationen werden angezeigt:

**Vorgangsnamen:** Der Name des Vorgangs, wie in Workbench definiert.

**Status:** Zeigt an, ob der Vorgang normal ausgeführt wird oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Zweigname:** Der Name des Zweigs, wie in Workbench definiert.

**Startdatum:** Datum und Uhrzeit des Starts des Vorgangs.

**Abschlussdatum:** Datum und Uhrzeit des Abschlusses des Vorgangs.

Ein Teilprozess ist eine Prozessinstanz, die von einem anderen Prozess gestartet und unabhängig von diesem anderen Prozess ausgeführt wird. Teilprozesse werden nur angezeigt, wenn sie als Teil des Prozesses in Workbench angelegt wurden. Auf der Registerkarte „Teilprozesse“ wird jeder Teilprozess mit den folgenden Informationen angezeigt:

**Prozess-ID:** Diese positive Ganzzahl wird vom Formular-Workflow zugewiesen, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname - Version:** Der Prozessname, wie in Designer definiert.

**Status:** Zeigt an, ob die Prozessinstanz normal ausgeführt wird, den Status wechselt oder beendet wurde. (Siehe Informationen zum Status von Prozessinstanzen.)

**Erstellungsdatum:** Datum und Uhrzeit der Erstellung des Teilprozesses.

**Aktualisierungsdatum:** Datum und Uhrzeit, zu der der Status des Unterprozesses zuletzt geändert wurde.

Sie können folgende Aufgaben auf der Seite „Prozessinstanzdetail“ ausführen:

* Einen Vorgang auswählen, um Details dazu anzuzeigen. Wenn Sie einen Vorgang auswählen, wird die Seite „Vorgangsdetails“ angezeigt.
* Einen Teilprozess auswählen, um Details dazu anzuzeigen. Wenn Sie einen Teilprozess auswählen, wird die Seite „Prozessinstanzdetail“ angezeigt.
* Vorgänge oder Teilprozesse in Abhängigkeit von deren Status beenden oder wiederholen

### Informationen zum Vorgangsstatus {#about-operation-statuses}

Ein Vorgang (ein Schritt in einem Prozess) kann folgende Status haben:

**ABGESCHLOSSEN:** Der Vorgang wurde abgeschlossen.

**WIRD AUSGEFÜHRT:** Der Vorgang wird normal ausgeführt. Möglicherweise empfängt er Benutzereingaben oder wartet auf Benutzerinteraktion oder ein automatischer Schritt kann aktiv sein.

**VERZÖGERT:** Während der Verarbeitung des Prozesses ist ein Problem aufgetreten. Auf der Seite „Angehaltene Vorgänge“ können Sie den Fehler oder die Ausnahme überprüfen.

**BEENDET:** Der Vorgang wurde von einem Administrator beendet.

### Vorgänge oder Teilprozesse beenden {#terminate-operations-or-subprocesses}

Wenn ein Vorgang oder Teilprozess angehalten hat oder ein anderer Fehlerzustand eingetreten ist bzw. wenn Sie die Beendigung der Ausführung eines Vorgangs oder Teilprozesses erzwingen müssen, können Sie diesen beenden.

Sie können Vorgänge mit dem Status WIRD AUSGEFÜHRT beenden.

Wenn Sie einen Vorgang beenden, wechselt dessen Status auf BEENDET. Der Vorgang wird nicht abgeschlossen und die Ausführung der Prozessinstanz wird beendet.

Sie können einen Teilprozess mit beliebigem Status beenden.

Wenn Sie einen Teilprozess beenden, wechselt dessen Status zuerst auf WIRD BEENDET, dann auf BEENDET, und die Prozessinstanz wird bei den aktuellen Vorgängen beendet. Es werden keine weiteren Vorgänge im Teilprozess ausgeführt, obwohl die übergeordnete Prozessinstanz weiterhin ausgeführt wird.

Sie können keine Prozesse mit Knotenelementen im Prozessdiagramm beenden. Wenn Sie versuchen, diese Prozesstypen zu beenden, sind die Vorgänge innerhalb der Knotenelemente nicht betroffen. Um Vorgänge zu beenden, die sich in einem Knotenelement befinden, müssen Sie diese direkt beenden.

1. Klicken Sie auf der Seite „Prozessinstanzdetail“ auf die Registerkarte „Vorgänge“ oder „Teilprozesse“.
1. Wählen Sie den zu beendenden Vorgang oder Teilprozess aus und klicken Sie auf „Beenden“.

### Einen Vorgang wiederholen {#retry-an-operation}

Sie können Vorgänge mit dem Status ANGEHALTEN wiederholen.

Wenn Sie einen Vorgang wiederholen, wird eine Anforderung zum erneuten Starten des Vorgangs an den Arbeitsablauf für Formulare gesendet. Ist die Anforderung erfolgreich, wechselt der Status auf WIRD AUSGEFÜHRT. Wenn der Vorgang nicht wiederholt werden kann, bleibt er ANGEHALTEN und Sie müssen ihn möglicherweise beenden.

1. Klicken Sie auf der Seite „Prozessinstanzdetail“ auf die Registerkarte „Vorgänge“.
1. Wählen Sie den Vorgang aus und klicken Sie auf „Erneut versuchen“.

## Mit Vorgängen arbeiten {#working-with-operations}

Auf der Seite „Vorgangsdetails“ wird die Zusammenfassung eines in einem Prozess enthaltenen Vorgangs mit seinen aktuellen Benutzerzuweisungen angezeigt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Arbeitsablauf für Formulare“.
1. Durch Klicken auf den Namen eines Prozesses können Sie die dazugehörigen Prozessinstanzen anzeigen. Klicken Sie auf eine Prozessinstanz, um die Seite „Prozessinstanzdetails“ anzuzeigen, und wählen Sie einen Vorgang aus, um die Seite „Vorgangsdetails“ anzuzeigen.

   Für jede Aufgabe werden in der Liste die folgenden Informationen angezeigt:

   **Prozessname - Version:** Der Name des Prozesses, wie in Workbench definiert.

   **Anwendung:** Die Anwendung, zu der der Prozess gehört, wie in Workbench definiert.

   **Status:** Aktiv bedeutet, dass es sich um den Prozess handelt, der für die Prozessversion aktiviert wurde. Inaktiv bedeutet, dass der Prozess eine alte Version ist, von der immer noch Prozessinstanzen vorhanden sind.

   **Ertsllungsdatum:** Datum und Uhrzeit der Bereitstellung des Prozesses.
