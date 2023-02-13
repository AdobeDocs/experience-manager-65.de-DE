---
title: Konfigurieren der Server-Einstellungen
seo-title: Configuring Server Settings
description: 'Auf der Seite „Servereinstellungen“ erhalten Sie Zugriff auf verschiedene Einstellungen für E-Mails, Aufgaben- und Administratorbenachrichtigungen:'
seo-description: The Server Settings page provides access to email, task notification and administrator notification settings.
uuid: 73b51ac0-56e5-4748-bb33-e3986c69eb2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e047a95e-0acb-438a-8d27-f005c0adc508
exl-id: 362b7b91-c58b-4e47-a6ef-56a4b54a100c
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: ht
source-wordcount: '2625'
ht-degree: 100%

---

# Konfigurieren der Server-Einstellungen {#configuring-server-settings}

Auf der Seite „Servereinstellungen“ erhalten Sie Zugriff auf verschiedene Einstellungen für den Arbeitsablauf für Formulare:

* **E-Mail-Einstellungen**, die ausgehende E-Mail-Nachrichten zusammen mit den für diese Nachrichten verwendeten E-Mail-Servereinstellungen aktivieren. (Siehe [E-Mail-Einstellungen konfigurieren](configuring-server-settings.md#configuring-email-settings).)
* **Aufgabenbenachrichtigungseinstellungen,** die mit E-Mail-Benachrichtigungen an Endbenutzer und Gruppen gesendeten Nachrichten zu Aufgaben aktivieren, deaktivieren oder ändern. (Siehe [Benachrichtigungen für Benutzer und Gruppen konfigurieren](configuring-server-settings.md#configuring-notifications-for-users-and-groups).)
* **Administratorbenachrichtigungseinstellungen,** die mit E-Mail-Benachrichtigungen gesendeten Nachrichten zu Verwaltungsaufgaben aktivieren, deaktivieren oder ändern. (Siehe [Benachrichtigungen für Administratoren konfigurieren](configuring-server-settings.md#configuring-notifications-for-administrators).)

## E-Mail-Einstellungen konfigurieren {#configuring-email-settings}

Sie können ein E-Mail-Konto für den Formularserver angeben, über das dieser E-Mail-Nachrichten an AEM Forms-Benutzer und -Administratoren sendet und von diesen empfängt. Mit diesen E-Mail-Nachrichten werden Benutzer über auszuführende Aufgaben benachrichtigt bzw. daran erinnert. Außerdem wird der Benutzer auf Aufgaben, für die ein Termin fällig geworden ist, hingewiesen und der Administrator wird über aufgetretene Fehler im Prozess informiert.

Um das Senden von E-Mail-Nachrichten zwischen AEM Forms und Benutzern zu aktivieren, konfigurieren Sie die Einstellungen für ausgehende E-Mail auf der Seite „E-Mail-Einstellungen“. Für ausgehende E-Mail muss ein SMTP-Server verwendet werden.

Damit AEM Forms eingehende E-Mail-Nachrichten von Benutzern empfangen und verarbeiten kann, müssen Sie einen E-Mail-Endpunkt für den Complete Task-Dienst erstellen. (Siehe [E-Mail-Endpunkt für den Complete Task-Dienst erstellen](/help/forms/using/admin-help/configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service)).

Wenn Ihre Prozesse so entworfen und implementiert sind, dass sie keine E-Mail benötigen, müssen keine der Optionen auf der Seite „E-Mail-Einstellungen“ konfiguriert werden.

### Einstellungen für ausgehende E-Mail konfigurieren {#configure-outgoing-email-settings}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „E-Mail-Einstellungen“.
1. Wählen Sie „Ausgehende Nachrichten aktivieren“.
1. Geben Sie in das Feld „SMTP-Server“ den Namen oder die IP-Adresse des E-Mail-Servers ein. Alle E-Mail-Nachrichten für Benachrichtigungen vom Arbeitsablauf für Formulare werden von diesem E-Mail-Server gesendet.
1. Geben Sie in die Felder „Benutzername“ und „Kennwort“ den Anmeldenamen und das Kennwort ein, die verwendet werden sollen, wenn der SMTP-Server eine Authentifizierung erfordert. Um anonyme Anmeldungen zuzulassen, lassen Sie die Felder unausgefüllt.
1. Geben Sie im Feld „E-Mail-Adresse“ die E-Mail-Adresse ein, die als Antwortadresse für E-Mail-Nachrichten verwendet werden soll, die vom Arbeitsablauf für Formulare gesendet werden.

   >[!NOTE]
   >
   >Wenn Sie Microsoft Exchange Server verwenden und die E-Mail-Adresse eine ungültige E-Mail-Adresse ist, kann der Microsoft Exchange Server keine E-Mail an die Verteilerliste senden. Um dieses Problem zu beheben, aktivieren Sie die Option **Externe Kommunikation aktivieren** separat für jede Verteilerliste auf Microsoft Exchange Server. 

1. Klicken Sie auf Speichern.

>[!NOTE]
>
>Wenn Sie falsche Informationen eingeben, können Sie durch Klicken auf „Abbrechen“ zur vorher angezeigten Seite zurückkehren.

### Konfigurieren von E-Mail-Vorlagen für die Verwendung von AEM Forms Workspace {#configuring-email-templates-to-use-html-workspace}

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Standardmäßig enthalten die E-Mails, die von AEM Forms gesendet werden, Links zu Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE). Sie können AEM Forms so konfigurieren, das E-Mails mit Links zu AEM Forms Workspace gesendet werden. Um mehr über die Vorteile von AEM Forms Workspace gegenüber Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) zu erfahren, lesen Sie [diesen Artikel](/help/forms/using/features-html-workspace-available-flex.md).

1. Klicken Sie in Administration Console auf „Startseite“ > „Dienste“ > „Arbeitsablauf für Formulare“ > „Aufgabenbenachrichtigungen“.
1. Öffnen Sie Aufgabenzuweisungsvorlage.
1. Legen Sie die Vorlage in den Aufgabenbenachrichtigungen auf folgendes fest:  `https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@`

   ```java
   https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@
   ```

## Benachrichtigungen für Benutzer und Gruppen konfigurieren {#configuring-notifications-for-users-and-groups}

Auf der Seite „Aufgabenbenachrichtigung“ können Sie Vorlagen konfigurieren, die der Arbeitsablauf für Formulare nutzt, um E-Mail-Benachrichtigungen zu generieren, die an Benutzer und Gruppen gesendet werden. Sie können die Benachrichtigungen mithilfe von Variablen des Arbeitsablaufs für Formulare anpassen und formatieren.

Folgende Benachrichtigungstypen können für Benutzer und Gruppen konfiguriert werden:

* Erinnerungen
* Aufgabenzuweisungen
* Termine

Um E-Mail-Benachrichtigungen für eine Gruppe zu generieren, müssen Sie in User Management eine E-Mail-Adresse für die Gruppe angeben. <!--Fix broken link See Setting up and organizing users -->Wenn der Arbeitsablauf für Formulare eine E-Mail-Benachrichtigung an eine Gruppe sendet, geht die Benachrichtigung an jedes Mitglied der Gruppe, dessen E-Mail-Adresse angegeben ist. Wenn ein Mitglied der Gruppe eine E-Mail-Benachrichtigung erhält und die Aufgabe anfordern möchte, muss auf die in der E-Mail-Benachrichtigung enthaltene Anforderungsverknüpfung klicken, wodurch die Seite mit den Aufgabendetails in Workspace geöffnet wird. Dort kann das Mitglied das Arbeitselement entweder anfordern oder anfordern und öffnen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

### Erinnerungen für Benutzer oder Gruppen konfigurieren {#configure-reminders-for-users-or-groups}

Sie können Erinnerungsbenachrichtigungen an den zugewiesenen Benutzer bzw. die Gruppe senden, wenn ein Termin zum Durchführen einer Aufgabe heranrückt. Die Regeln zum Ermitteln des genauen Zeitpunktes, zu dem eine Erinnerungsbenachrichtigung zu senden ist, werden vom Entwickler des Prozesses festgelegt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „Aufgabenbenachrichtigungen“.
1. Klicken Sie unter „Benachrichtigungstyp“ für Benutzer auf „Erinnerung“ bzw. für Gruppen auf „Gruppe - Erinnerung“.
1. Wählen Sie „Erinnerung aktivieren“ bzw. „Gruppe - Erinnerung aktivieren“.
1. (Nur für Benutzerbenachrichtigungen) Um das Formular mit Daten als Anlage in die E-Mail-Erinnerungsnachricht zu übernehmen, aktivieren Sie „Formulardaten aufnehmen“.
1. Geben Sie in das Feld „Betreff“ den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie in das Feld „Benachrichtigungsvorlage“ den Text für den Nachrichtentext der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste „Nachrichtenformat“ das Format aus, in dem die E-Mail-Nachricht gesendet werden soll, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste „E-Mail-Kodierung“ das für die E-Mail-Nachricht zu verwendende Kodierformat aus. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in Japan wählen eher ISO2022-JP.
1. Klicken Sie auf Speichern.

### Benachrichtigungen über Aufgabenzuweisungen für Benutzer und Gruppen konfigurieren {#configure-task-assignment-notifications-for-users-or-groups}

Sie können Benachrichtigungen über Aufgabenzuweisungen an Benutzer oder eine Gruppe senden, wenn diesen eine Aufgabe zugewiesen wird.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „Aufgabenbenachrichtigungen“.
1. Klicken Sie unter „Benachrichtigungstyp“ für Benutzer auf Aufgabenzuweisung bzw. für Gruppen auf Gruppe - Aufgabenzuweisung.
1. Wählen Sie für Benutzer „Aufgabenzuweisung aktivieren“ bzw. für Gruppen „Gruppe - Aufgabenzuweisung aktivieren“.
1. (Nur für Benutzerbenachrichtigungen) Um das Formular mit Daten als Anlage in die E-Mail-Aufgabenzuweisungsnachricht zu übernehmen, aktivieren Sie „Formulardaten aufnehmen“.
1. Geben Sie in das Feld „Betreff“ den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie in das Feld „Benachrichtigungsvorlage“ den Text für den Nachrichtentext der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste „Nachrichtenformat“ das Format aus, in dem die E-Mail-Nachricht gesendet werden soll, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste „E-Mail-Kodierung“ das für die E-Mail-Nachricht zu verwendende Kodierformat aus. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in Japan wählen eher ISO2022-JP.
1. Klicken Sie auf Speichern.

### Terminbenachrichtigungen für Benutzer und Gruppen konfigurieren {#configure-deadline-notifications-for-users-or-groups}

Sie können Terminbenachrichtigungen an Benutzer und Gruppen senden, wenn der Termin für die Durchführung einer Aufgabe verstrichen ist. Eine Terminbenachrichtigung hat normalerweise reinen Informationscharakter, weil der Benutzer die zugewiesene Aufgabe nicht mehr ausführen kann.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „Aufgabenbenachrichtigungen“.
1. Klicken Sie unter „Benachrichtigungstyp“ für Benutzer auf „Termin“ bzw. für Gruppen auf „Gruppe - Termin“.
1. Wählen Sie „Erinnerung aktivieren“ bzw. „Gruppe - Erinnerung aktivieren“.
1. Geben Sie in das Feld „Betreff“ den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie in das Feld „Benachrichtigungsvorlage“ den Text für den Nachrichtentext der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste „Nachrichtenformat“ das Format aus, in dem die E-Mail-Nachricht gesendet werden soll, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste „E-Mail-Kodierung“ das für die E-Mail-Nachricht zu verwendende Kodierformat aus. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in Japan wählen eher ISO2022-JP.
1. Klicken Sie auf Speichern.

### Blenden Sie das Tag „DO NOT DELETE“ für alle E-Mails aus. {#hide-the-do-not-delete-tag-for-all-emails}

Sie können die E-Mails so konfigurieren, dass der Verfolgungstag „DO NOT DELETE“ in allen E-Mails ausgeblendet wird, die in einem am Menschen orientierten Prozess gesendet werden.

<!-- 
For details, see [How to hide the 'DO-NOT-DELETE' tag with CSS](https://blogs.adobe.com/LiveCycleHelp/2013/09/how-to-hide-the-do-not-delete-tag-with-css.html) 
-->

## Benachrichtigungen für Administratoren konfigurieren {#configuring-notifications-for-administrators}

Sie können Vorlagen konfigurieren, die der Arbeitsablauf für Formulare nutzt, um E-Mail-Benachrichtigungen zu generieren, die an Administratoren gesendet werden.

Folgende Benachrichtigungstypen können für Administratoren konfiguriert werden:

* Angehaltener Zweig
* Angehaltener Vorgang

### Benachrichtigungen bei angehaltenen Zweigen konfigurieren {#configure-stalled-branch-notifications}

Wenn ein Zweig anhält (also dessen Fortsetzung absichtlich oder wegen eines Fehlers beendet wird), können Sie veranlassen, dass eine E-Mail-Benachrichtigung an einen Administrator oder einen anderen Benutzer gesendet wird, der das Problem untersuchen kann.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „Administratorbenachrichtigungen“.
1. Klicken Sie unter Benachrichtigungstyp auf Angehaltener Zweig.
1. Wählen Sie „&#39;Angehaltener Zweig&#39; aktivieren“.
1. Geben Sie in das Feld „E-Mail-Adresse“ die Adressen der Benutzer ein, die benachrichtigt werden sollen, wenn ein Zweig anhält. Sie müssen das Format „Benutzer@Domain.com“ verwenden und jede Adresse durch ein Komma abtrennen. Normalerweise handelt es sich hierbei um die E-Mail-Adresse eines Administrators.
1. Geben Sie in das Feld „Betreff“ den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie in das Feld „Benachrichtigungsvorlage“ den Text für den Nachrichtentext der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Wählen Sie in der Liste „Nachrichtenformat“ das Format aus, in dem die E-Mail-Nachricht gesendet werden soll, entweder HTML oder Text. Das Standardformat ist HTML.
1. Wählen Sie in der Liste „E-Mail-Kodierung“ das für die E-Mail-Nachricht zu verwendende Kodierformat aus. Der Standardwert ist UTF-8, der von den meisten Benutzern außerhalb von Japan benutzt wird. Benutzer in Japan wählen eher ISO2022-JP.
1. Klicken Sie auf Speichern.

### Benachrichtigungen bei angehaltenen Vorgängen konfigurieren {#configure-stalled-operation-notifications}

Wenn ein Vorgang anhält (also dessen Fortsetzung absichtlich oder wegen eines Fehlers beendet wird), können Sie veranlassen, dass eine E-Mail-Benachrichtigung an einen Administrator oder einen anderen Benutzer gesendet wird, der das Problem untersuchen kann.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „Administratorbenachrichtigungen“.
1. Klicken Sie unter „Benachrichtigungstyp“ auf „Angehaltener Vorgang“.
1. Wählen Sie „Angehaltener Vorgang aktivieren“.
1. Geben Sie in das Feld „E-Mail-Adresse“ die Adressen der Benutzer ein, die benachrichtigt werden sollen, wenn ein Vorgang anhält. Sie müssen das Format „Benutzer@Domain.com“ verwenden und jede Adresse durch ein Komma abtrennen. Normalerweise handelt es sich hierbei um die E-Mail-Adresse eines Administrators.
1. Geben Sie in das Feld „Betreff“ den Text für die Betreffzeile der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Geben Sie in das Feld „Benachrichtigungsvorlage“ den Text für den Nachrichtentext der E-Mail-Nachricht ein. Dieses Feld ist bereits vorab mit Standardtext ausgefüllt. Detaillierte Informationen zum Anpassen dieses Felds finden Sie unter [Inhalt von Nachrichten anpassen](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Klicken Sie auf Speichern.

## Anpassen des Inhalts von Benachrichtigungen {#customizing-the-content-of-notifications}

Auf den Seiten „Aufgabenbenachrichtigungen“ und „Administratorbenachrichtigungen“ stehen mehrere Funktionen zur Verfügung, mit deren Hilfe Benachrichtigungsmeldungen angepasst werden können:

* Rich-Text-Editor
* Variablenauswahl
* URL-Erzeugung

### Rich-Text-Editor {#rich-text-editor}

Der Bereich „Benachrichtigungsvorlage“ ist ein Rich-Text-Editor, in dem Sie HTML-Code für die E-Mail-Benachrichtigungsmeldungen erzeugen können. Es stehen dort Optionen für die Schriftarten- und Absatzformatierung zur Verfügung, die unterhalb des Feldes „Benachrichtigungsvorlage“ zu finden sind. Diese Optionen umfassen Schriftart, -grad, -stil und -farbe sowie Absatzausrichtung und Aufzählungszeichen.

### URL-Erzeugung {#url-generation}

Nur für Aufgabenbenachrichtigungen: Der Arbeitsablauf für Formulare enthält zwei vordefinierte URL-Konfigurationen, die aus der Liste „URL-Erzeugung“ in das Feld „Benachrichtigungsvorlage “ gezogen und dann angepasst werden können:

* OpenTask ist für die Benachrichtigungstypen „Erinnerung“ und „Aufgabenzuweisung“ verfügbar. Diese URL bietet eine Verknüpfung mit der Aufgabe in Workspace, wodurch der Benutzer schnell aus der E-Mail-Benachrichtigung heraus auf die Aufgabe zugreifen kann. Wenn Sie die OpenTask-URL in das Feld „Benachrichtigungsvorlage“ ziehen, ist die URL im folgenden Format:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

* „ClaimTask“ ist für die Benachrichtigungstypen „Gruppe - Erinnerung“ und „Gruppe - Aufgabenzuweisung“ verfügbar. Diese URL bietet eine Verknüpfung mit der Seite „Aufgabendetails“ in Workspace, auf der der Benutzer das Arbeitselement entweder anfordern oder anfordern und öffnen kann. Wenn Sie die ClaimTask-URL in das Feld „Benachrichtigungsvorlage“ ziehen, ist die URL im folgenden Format:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Wenn Ihre Lösung in einer Cluster-Umgebung bereitgestellt wird, ersetzen Sie `@@notification-host@@` durch die Cluster-Adresse.

`<`*PORT* `>` ist die Port-Nummer des HTTP-Listeners für den Programm-Server. Der Standardanschluss für HTTP-Listener für die unterstützten Anwendungsserver lautet wie folgt:

**JBoss:** 8080

**Oracle WebLogic Server**: 7001

**IBM WebSphere**: 9080

Damit diese URLs korrekt funktionieren, müssen Sie `<`*PORT* `>` durch die Port-Nummer ersetzen, die für Ihre Umgebung geeignet ist.

>[!NOTE]
>
>Wenn Sie mithilfe einer benutzerdefinierten anderen Webanwendung als Forms Benutzern den Zugriff auf die Aufgaben ermöglichen, müssen Sie stattdessen ein URL-Format verwenden, das dem der benutzerdefinierten Anwendung entspricht.

### Variablenauswahl {#variable-picker}

Die Liste „Variablenauswahl“ bietet nützliche Variablen, die in die Felder „Betreff“ und „Benachrichtigungsvorlage“ gezogen und dort abgelegt werden können. Beim Ablegen einer Variablen in einem der Felder „Betreff“ oder „Benachrichtigungsvorlage“ ändert sich deren Name in den tatsächlichen Namen der Variablen des Workflows für Formulare mit je zwei führenden und nachfolgenden @-Symbolen, z. B. `@@taskid@@`.

Für Erinnerungen, Aufgabenzuweisungen und Termine für Benutzer und Gruppen können Sie die folgenden Variablen in den Feldern „Betreff“ und „Benachrichtigungsvorlage“ verwenden:

**description** Der Inhalt der Eigenschaft „Beschreibung“, wie in Workbench im Benutzervorgang (Startpunkt oder Vorgang zum Zuweisen einer oder mehrerer Aufgaben) für den Prozess definiert.

**instructions**: Der Inhalt der Eigenschaft „Aufgabenanweisungen“, wie in Workbench im Benutzervorgang für den Prozess definiert.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

**process-name** Der Name des Vorgangs.

**operation-name** Der Name des Schritts.

**taskid** Die eindeutige Kennung der aktuellen Aufgabe.

**actions** Erzeugt eine nummerierte Liste gültiger Routen (z. B. Genehmigen, Ablehnen), auf die der Empfänger klicken kann.

Zusätzlich können für Gruppenerinnerungen, Gruppenaufgabenzuweisungen und Gruppentermine folgende Variablen verwendet werden:

**group-name** Der Name der Gruppe, der das Arbeitselement zugeordnet ist.

>[!NOTE]
>
>Wenn eine Variable keinen Wert hat, wird nichts zurückgegeben.

Für angehaltene Zweige können Sie die folgenden Variablen in den Feldern „Betreff“ und „Benachrichtigungsvorlage“ verwenden:

**branch-id** Die Zweig-ID.

**process-id** Die Prozessinstanz-ID.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

Für angehaltene Vorgänge können Sie die folgenden Variablen in den Feldern „Betreff“ und „Benachrichtigungsvorlage“ verwenden:

**action-id** Die Vorgangs-ID.

**branch-id** Die Zweig-ID.

**process-id** Die Prozessinstanz-ID.

**notification-host** Der Host-Name des AEM Forms-Programm-Servers.

### Variable im Feld „Betreff“ verwenden {#using-a-variable-in-the-subject-box}

Wenn Sie den folgenden Text für Benachrichtigungen über Aufgabenzuweisungen in das Feld „Betreff“ eingeben:

`Please complete task @@taskid@@`

Erhält der Benutzer eine E-Mail-Nachricht mit dem folgenden Betreff, wenn die Aufgabe 376 zugewiesen ist:

`Please complete task 376`

### Verwenden von Variablen im Feld „Benachrichtigungsvorlage“ {#using-variables-in-the-notification-template-box}

Wenn Sie den folgenden Text für Benachrichtigungen bei angehaltenen Zweigen in das Feld „Benachrichtigungsvorlage“ eingeben:

`Branch @@branch-id@@ has stalled! You have received this notification from @@notification-host@@.`

Erhält der Administrator eine E-Mail-Nachricht mit folgendem Inhalt, wenn die Zweignummer „4868“ und der Name des Servers `ServerXYZ` ist:

`Branch 4868 has stalled! You have received this notification from ServerXYZ.`

## Business Activity Monitoring-Verbindungen konfigurieren {#configuring-business-activity-monitoring-connections}

Business Activity Monitoring, ein optionales Modul, bietet eine Reihe von Betriebsdashboards, mit denen Ihre Vorgänge und wichtige Leistungsindikatoren in Echtzeit visualisiert werden.

Auf der Seite „BAM-Konfigurationseinstellungen“ können Sie die Verbindungen mit dem Server festlegen, auf dem BAM ausgeführt wird, sodass prozessbezogene Ereignisse verfolgt und an diesen Server übermittelt werden können.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Servereinstellungen“ > „BAM-Konfigurationseinstellungen“.
1. Geben Sie in das Feld „BAM-Host“ den Namen des Servers ein, auf dem BAM ausgeführt wird. Der Standardwert ist localhost.
1. Geben Sie in das Feld „BAM-Anschluss“ den Anschluss ein, über den die Verbindung mit dem Server hergestellt werden soll, auf dem BAM ausgeführt wird. Der BAM-Standardanschluss für JBoss ist 8080, für WebLogic 7001 und für WebSphere 9080.
1. Geben Sie in das Feld „Serverhost“ den Namen oder die IP-Adresse des Host-Formularservers ein. Der Standardwert lautet localhost.
1. Geben Sie in das Feld „Serveranschluss“ die vom Formularserver verwendete Anschlussnummer ein.
1. Geben Sie in die Felder „Benutzername“ und „Kennwort“ die entsprechende Benutzer-ID und das Kennwort für den Zugriff auf den BAM-Server ein. Der Standardbenutzername ist „CognosNowAdmin“, das Standardkennwort „manager“.
1. Klicken Sie auf Speichern.
