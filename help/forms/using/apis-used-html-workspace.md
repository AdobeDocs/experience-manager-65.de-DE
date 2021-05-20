---
title: APIs in AEM Forms Workspace
seo-title: APIs im AEM-Formulararbeitsbereich
description: Öffentliche Java- und JavaScript-APIs und Methoden von LiveCycle AEM Forms Workspace zur Anpassung und Automatisierung.
seo-description: Öffentliche Java- und JavaScript-APIs und Methoden von LiveCycle AEM Forms Workspace zur Anpassung und Automatisierung.
uuid: 9602990e-8ac7-42eb-b507-50b3594055ba
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 4a73a973-fccf-466b-b4a0-47652a14a080
exl-id: 9034f73a-83f3-498e-b6a6-ad6577aa1a3a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 100%

---

# APIs im AEM-Formulararbeitsbereich {#apis-used-in-aem-forms-workspace}

Die folgenden APIs werden in AEM FormsWorkspace verwendet.

<table>
 <tbody>
  <tr>
   <td><strong>JavaScript-Methode</strong></td>
   <td><strong>Dienstname</strong></td>
   <td><strong>API-Name</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>getGroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getGroups</td>
   <td>Sucht nach Gruppen. Gibt eine Liste aller Gruppen zurück, wenn kein Name angegeben ist. Andernfalls werden Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getUsersAndGroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersAndGroups</td>
   <td>Sucht nach Benutzern und Gruppen. Gibt eine Liste aller Benutzer und Gruppen zurück, wenn kein Name angegeben ist. Andernfalls werden Benutzer und Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>prepareForSubmit</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>prepareForSubmit</td>
   <td>Wird aufgerufen, bevor das Formular über DocumentSubmitServlet gesendet wird. Stellt die Aufgaben-ID in einer Sitzungsvariable ein (zusammen mit der Ablaufzeit), die beim eigentlichen Senden abgerufen wird.</td>
  </tr>
  <tr>
   <td>submitTask</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>submit</td>
   <td>Sendet das Dokumentobjekt, das einer Aufgabe zugeordnet ist (und wiederum einem Sendeprozess).</td>
  </tr>
  <tr>
   <td>getRootEndpointCategories</td>
   <td>ProcessManagementStartpointService</td>
   <td>getRootEndpointCategories</td>
   <td>Ruft alle Stammkategorien ab, die auf dem Server vorhanden sind.</td>
  </tr>
  <tr>
   <td>getDirectChildCategories</td>
   <td>ProcessManagementStartpointService</td>
   <td>getDirectChildCategories2</td>
   <td>Ruft alle direkt untergeordneten Objekte für eine Kategorie ab.</td>
  </tr>
  <tr>
   <td>getAllStartpoints</td>
   <td>ProcessManagementStartpointService</td>
   <td>getAllStartpoints</td>
   <td>Ruft alle Startpunkte ab, die auf dem Server in allen Kategorien vorhanden sind.</td>
  </tr>
  <tr>
   <td>invokeStartpoint</td>
   <td>ProcessManagementStartpointService</td>
   <td>invokeStartpoint</td>
   <td>Dies ruft einen Startpunkt auf und erstellt eine neue Aufgabe, die einem Startpunkt zugeordnet ist.</td>
  </tr>
  <tr>
   <td>getAllTasks</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableTasks</td>
   <td>Ruft alle Aufgaben auf, die für den angemeldeten Benutzer erstellt und weitergeleitet oder verwendet, gespeichert, zugewiesen, zugewiesen und gespeichert werden.</td>
  </tr>
  <tr>
   <td>getTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getTask</td>
   <td>Ruft eine bestimmte Aufgabe ab.</td>
  </tr>
  <tr>
   <td>renderTask</td>
   <td>ProcessManagementTaskService</td>
   <td>render</td>
   <td>Gibt eine Aufgabe wieder und gibt die Informationen zurück, die erforderlich sind, um wenn nötig Formulare wie Formular-URL, Formulartyp, Daten-URL usw. wiederzugeben.</td>
  </tr>
  <tr>
   <td>submitWithPriorData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithPriorData</td>
   <td>Gibt das Ergebnis der Senden-API des TaskManagers zurück.</td>
  </tr>
  <tr>
   <td>submitWithData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithData</td>
   <td>Sendet die mit der Aufgabe verknüpften Formulardaten (übergeben als String) mithilfe der Senden-API des TaskManagers. Wird für Flex-Formulare verwendet, die nicht die Senden-API von TaskManager aufrufen.</td>
  </tr>
  <tr>
   <td>Speichern</td>
   <td>ProcessManagementTaskService</td>
   <td>Speichern</td>
   <td>Speichert eine Aufgabe auf dem Server.</td>
  </tr>
  <tr>
   <td>complete</td>
   <td>ProcessManagementTaskService</td>
   <td>complete</td>
   <td>Schließt eine Aufgabe ab und die Aufgabe wird an den nächsten Schritt gemäß dem Prozessdesign übergeben.</td>
  </tr>
  <tr>
   <td>getAttachment</td>
   <td>ProcessManagementTaskService</td>
   <td>getAttachment</td>
   <td>Gibt URL einer Anlage zurück, unter der die Anlage verfügbar ist.</td>
  </tr>
  <tr>
   <td>getAllAttachments</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableAttachments</td>
   <td>Ruft alle Anlagen und Hinweise für eine Aufgabe ab.</td>
  </tr>
  <tr>
   <td>Netzwerkfreigabe,</td>
   <td>ProcessManagementTaskService</td>
   <td>Netzwerkfreigabe,</td>
   <td>Gibt eine Aufgabe für einen anderen Benutzer frei. Ein anderer Benutzer kann die Aufgabe anfordern und wird Eigentümer der Aufgabe.</td>
  </tr>
  <tr>
   <td>forward</td>
   <td>ProcessManagementTaskService</td>
   <td>forward</td>
   <td>Leitet eine Aufgabe an einen anderen Benutzer weiter.</td>
  </tr>
  <tr>
   <td>consult</td>
   <td>ProcessManagementTaskService</td>
   <td>konsultieren</td>
   <td>Bespricht eine Aufgabe mit einem anderen Benutzer.</td>
  </tr>
  <tr>
   <td>claim</td>
   <td>ProcessManagementTaskService</td>
   <td>claim</td>
   <td>Fordert eine Aufgabe an, die in der freigegebenen Warteschlange verfügbar ist.</td>
  </tr>
  <tr>
   <td>unlock</td>
   <td>ProcessManagementTaskService</td>
   <td>unlock</td>
   <td>Entsperrt eine Aufgabe.</td>
  </tr>
  <tr>
   <td>lock</td>
   <td>ProcessManagementTaskService</td>
   <td>lock</td>
   <td>Sperrt er eine Aufgabe. Diese kann nicht von einem anderen Benutzer angefordert werden, wenn sie freigegeben wird.</td>
  </tr>
  <tr>
   <td>Ablehnen der Bedingungen</td>
   <td>ProcessManagementTaskService</td>
   <td>Ablehnen der Bedingungen</td>
   <td>Gibt die Aufgabe an den vorherigen Eigentümer der Aufgabe zurück.</td>
  </tr>
  <tr>
   <td>abandon</td>
   <td>ProcessManagementTaskService</td>
   <td>Abbruch</td>
   <td>Löscht eine Aufgabe.</td>
  </tr>
  <tr>
   <td>setVisibility</td>
   <td>ProcessManagementTaskService</td>
   <td>setVisibility</td>
   <td>Legt die Sichtbarkeit einer Aufgabe fest. Wenn Sichtbarkeit auf „false“ gesetzt ist, ist die Aufgabe für Benutzer anschließend nicht mehr sichtbar.</td>
  </tr>
  <tr>
   <td>getUsers</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsers</td>
   <td>Wird zum Suchen von Benutzern verwendet. Gibt alle Benutzer zurück, wenn kein Name angegeben ist, oder alle Nutzer mit dem angegebenen Namen.</td>
  </tr>
  <tr>
   <td>getUsersInGroup</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersInGroupByName</td>
   <td>Gibt alle Benutzer in einer Gruppe zurück.</td>
  </tr>
  <tr>
   <td>grantQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>grantQueueAccess</td>
   <td>Gewährt festgelegtem Benutzer Zugriff auf die Warteschlange des angemeldeten Benutzers. Generell wird die eigene Warteschlange für einen anderen Benutzer freigegeben.</td>
  </tr>
  <tr>
   <td>requestQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>requestQueueAccess</td>
   <td>Stellt für den angemeldeten Benutzer eine Zugriffsanforderung für die Warteschlange des angegebenen Benutzers. Wenn der Benutzer die Anforderung genehmigt, wird die Warteschlange des Benutzers für den angemeldeten Benutzer freigegeben.</td>
  </tr>
  <tr>
   <td>getGrantedUsers</td>
   <td>ProcessManagementQueueService</td>
   <td>getGrantedUsers</td>
   <td>Gibt alle Benutzer zurück, die Zugriff auf die Warteschlange des angemeldeten Benutzers haben.</td>
  </tr>
  <tr>
   <td>getUsersForAccessibleQueues</td>
   <td>ProcessManagementQueueService</td>
   <td>getUsersForAccessibleQueues</td>
   <td>Gibt alle Benutzer zurück, deren Warteschlange für einen Benutzer zugänglich ist.</td>
  </tr>
  <tr>
   <td>revokeQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>cancelQueueAccess</td>
   <td>Entfernt einen Benutzer aus der Liste der Benutzer, die Zugriff auf die Warteschlange des angemeldeten Benutzers haben.</td>
  </tr>
  <tr>
   <td>removeQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>removeQueueAccess</td>
   <td>Entfernt einen Benutzer aus der Liste der Benutzer, deren Warteschlange für den angemeldeten Benutzer zugänglich ist.</td>
  </tr>
  <tr>
   <td>getAllQueues<br /> </td>
   <td>ProcessManagementQueueService<br /> </td>
   <td>getAllQueues<br /> </td>
   <td>Ruft alle Warteschlangen (eigene, freigegebene und Gruppenwarteschlangen) ab, die für den angemeldeten Benutzer zugänglich sind.<br /> </td>
  </tr>
  <tr>
   <td>getOutOfOfficeSettings</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>getOutOfOfficeSettings</td>
   <td>Ruft Abwesenheitseinstellungen eines Benutzers ab.</td>
  </tr>
  <tr>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>Speichert Abwesenheitseinstellungen eines Benutzers.</td>
  </tr>
  <tr>
   <td>getAllProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getAllProcesses</td>
   <td>Es gibt Liste aller Prozesse zurück.</td>
  </tr>
  <tr>
   <td>getParticipatedProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getParticipatedProcesses</td>
   <td>Gibt eine Liste aller Prozessnamen zurück, an denen der angemeldeten Benutzer beteiligt ist.</td>
  </tr>
  <tr>
   <td>getProcessInstance<br /> </td>
   <td>ProcessManagementProcessService<br /> </td>
   <td>getProcessInstance<br /> </td>
   <td>Ruft Details einer Prozessinstanz ab.<br /> </td>
  </tr>
  <tr>
   <td>getProcessInstances</td>
   <td>ProcessManagementQueryService</td>
   <td>getProcessInstances</td>
   <td>Ruft alle Prozessinstanzen für einen Prozess ab.</td>
  </tr>
  <tr>
   <td>getPendingTasksForProcessInstance</td>
   <td>ProcessManagementQueryService</td>
   <td>getPendingTasksForProcessInstance</td>
   <td>Ruft ausstehende Aufgaben für eine Prozessinstanz ab.</td>
  </tr>
  <tr>
   <td>getTasksForProcessInstance</td>
   <td>ProcessManagementQueryService</td>
   <td>getTasksForProcessInstance</td>
   <td>Ruft alle Aufgaben für eine Prozessinstanz ab.</td>
  </tr>
  <tr>
   <td>getAllSearchTemplates</td>
   <td>ProcessManagementQueryService</td>
   <td>getAllSearchTemplates</td>
   <td>Gibt Liste aller Suchvorlagen zurück.</td>
  </tr>
  <tr>
   <td>getTemplate</td>
   <td>ProcessManagementQueryService</td>
   <td>getTemplate</td>
   <td>Es gibt Inhalt für eine Suchvorlage zurück.</td>
  </tr>
  <tr>
   <td>findTasksJson<br /> </td>
   <td>ProcessManagementQueryService</td>
   <td>findTasksJson</td>
   <td>Durchsucht und gibt alle Aufgaben zurück, die alle Bedingungen einer Suchvorlage erfüllen.</td>
  </tr>
  <tr>
   <td>getAssignmentsForTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getAssignmentsForTask</td>
   <td>Ruft alle Zuweisungen für eine Aufgabe ab. Beispiel: - Wenn ein Benutzer eine Aufgabe an einen anderen Benutzer weiterleitet oder sie mit ihm bespricht, dann ist dies eine Aufgabenzuweisung.</td>
  </tr>
  <tr>
   <td>deleteAttachment </td>
   <td>TaskManagerService</td>
   <td>deleteAttachment</td>
   <td>Löscht eine Anlage.</td>
  </tr>
  <tr>
   <td>initialize</td>
   <td>ProcessManagementClientSessionService</td>
   <td>initialize</td>
   <td>Erneuert Einstellung falls erforderlich. Authentifiziert den Benutzer. Legt Sitzungsparameter für Server-/Client-Informationen fest. Gibt Benutzerinformation und Abfrageintervall zurück.</td>
  </tr>
  <tr>
   <td>getTasksForDirectReports</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getTasksForDirectReports</td>
   <td>Es gibt alle Aufgaben von direkt unterstellten Mitarbeitern des angemeldeten Managers zurück.</td>
  </tr>
  <tr>
   <td>getTaskOfDirectReport<br /> </td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getDirectReportTask</td>
   <td>Gibt Aufgabe des angegebenen direkt unterstellten Mitarbeiters des angemeldeten Managers zurück.</td>
  </tr>
  <tr>
   <td>forwardTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>forwardTaskOfDirectReport</td>
   <td>Leitet eine Aufgabe eines direkt unterstellten Mitarbeiters an einen anderen Benutzer weiter.</td>
  </tr>
  <tr>
   <td>rejectTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>rejectTaskOfDirectReport</td>
   <td>Gibt eine Aufgabe eines direkt unterstellten Mitarbeiters an den vorherigen Benutzer zurück.</td>
  </tr>
  <tr>
   <td>getProperty</td>
   <td>WorkspacePropertyService</td>
   <td>getProperty</td>
   <td>Ruft eine Workspace-Eigenschaft für einen Benutzer ab.</td>
  </tr>
  <tr>
   <td>removeProperty</td>
   <td>WorkspacePropertyService</td>
   <td>Löschen Sie</td>
   <td>Löscht eine Workspace-Eigenschaft für einen Benutzer.</td>
  </tr>
  <tr>
   <td>getProperties</td>
   <td>WorkspacePropertyService</td>
   <td>getPropertiesAsMap</td>
   <td>Gibt alle Workspace-Eigenschaften für einen Benutzer zurück.</td>
  </tr>
  <tr>
   <td>setProperty</td>
   <td>WorkspacePropertyService</td>
   <td>setProperty</td>
   <td>Legt eine Workspace-Eigenschaft für einen Benutzer fest.</td>
  </tr>
  <tr>
   <td>getCurrentUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getCurrentUserImageUrl</td>
   <td>Ruft Bild-URL des Benutzers für den angemeldeten Benutzer ab.</td>
  </tr>
  <tr>
   <td>getUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getUserImageUrl</td>
   <td>Ruft Bild-URL des Benutzers für den angegebenen Benutzer ab.</td>
  </tr>
  <tr>
   <td>uploadNote</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadNote</td>
   <td>Lädt eine Notiz für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>uploadRMAToServer (es wird auch direkt von HTML-Vorlage aufgerufen)<br /> </td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadAttachment</td>
   <td>Lädt eine Anlage für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>getImageURL (es wird auch direkt von HTML-Vorlage aufgerufen)</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>getImage</td>
   <td>Ruft Bild für einen Prozess ab.</td>
  </tr>
 </tbody>
</table>
