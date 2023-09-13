---
title: APIs in AEM Forms Workspace
description: Public Java&trade sowie JavaScript-APIs und Methoden von LiveCycle AEM Forms Workspace, die zur Anpassung und Automatisierung verfügbar gemacht werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 9034f73a-83f3-498e-b6a6-ad6577aa1a3a
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 3%

---

# APIs in AEM Forms Workspace {#apis-used-in-aem-forms-workspace}

Die folgenden APIs werden im AEM Forms-Arbeitsbereich verwendet.

<table>
 <tbody>
  <tr>
   <td><strong>JavaScript-Methode</strong></td>
   <td><strong>Service-Name</strong></td>
   <td><strong>API-Name</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>getGroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getGroups</td>
   <td>Suchgruppen. Gibt eine Liste aller Gruppen zurück, wenn nichts angegeben ist. Andernfalls werden Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getUsersAndGroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersAndGroups</td>
   <td>Sucht Benutzer und Gruppen. Wenn nichts angegeben ist, wird eine Liste aller Benutzer und Gruppen zurückgegeben. Andernfalls werden Benutzer und Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>prepareForSubmit</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>prepareForSubmit</td>
   <td>Sie wird aufgerufen, bevor ein Formular über DocumentSubmitServlet gesendet wird. Legt die Aufgaben-ID in einer Sitzungsvariablen fest (zusammen mit der Ablaufzeit), die während der tatsächlichen Übermittlung abgerufen wird.</td>
  </tr>
  <tr>
   <td>submitTask</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>absenden</td>
   <td>Sendet das Dokumentobjekt, das mit einer Aufgabe verknüpft ist (und der Sendeprozess wiederum).</td>
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
   <td>Ruft alle direkten untergeordneten Elemente für eine Kategorie ab.</td>
  </tr>
  <tr>
   <td>getAllStartpoints</td>
   <td>ProcessManagementStartpointService</td>
   <td>getAllStartpoints</td>
   <td>Ruft alle Startpunkte ab, die auf dem Server unter allen Kategorien vorhanden sind.</td>
  </tr>
  <tr>
   <td>invokeStartpoint</td>
   <td>ProcessManagementStartpointService</td>
   <td>invokeStartpoint</td>
   <td>Dadurch wird ein Startpunkt aufgerufen und eine Aufgabe erstellt, die einem Startpunkt entspricht.</td>
  </tr>
  <tr>
   <td>getAllTasks</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableTasks</td>
   <td>Ruft alle Aufgaben ab, die für den angemeldeten Benutzer erstellt, weitergeleitet oder konsultiert, gespeichert, zugewiesen, zugewiesen und gespeichert werden.</td>
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
   <td>Gibt eine Aufgabe wieder und gibt bei Bedarf Informationen zurück, die erforderlich sind, um das Formular wie Formular-URL, Formulartyp und Daten-URL wiederzugeben.</td>
  </tr>
  <tr>
   <td>submitWithPriorData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithPriorData</td>
   <td>Es wird das Ergebnis der Senden-API von TaskManager mithilfe des Ergebnisschlüssels zurückgegeben.</td>
  </tr>
  <tr>
   <td>submitWithData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithData</td>
   <td>Sendet die mit der Aufgabe verknüpften Formulardaten (übergeben als Zeichenfolge) mithilfe der Senden-API von TaskManager. Sie wird für Flex-Formulare verwendet, die nicht die Senden-API von TaskManager aufrufen.</td>
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
   <td>Er schließt eine Aufgabe ab und die Aufgabe wird gemäß dem Prozessentwurf an den nächsten Schritt übergeben.</td>
  </tr>
  <tr>
   <td>getAttachment</td>
   <td>ProcessManagementTaskService</td>
   <td>getAttachment</td>
   <td>Es wird eine URL eines Anhangs zurückgegeben, in dem der Anhang verfügbar ist.</td>
  </tr>
  <tr>
   <td>getAllAttachments</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableAttachments</td>
   <td>Ruft alle Anlagen und Notizen für eine Aufgabe ab.</td>
  </tr>
  <tr>
   <td>Netzwerkfreigabe,</td>
   <td>ProcessManagementTaskService</td>
   <td>Netzwerkfreigabe,</td>
   <td>Teilt eine Aufgabe mit einem anderen Benutzer. Ein anderer Benutzer kann die Aufgabe anfordern und wird Eigentümer der Aufgabe.</td>
  </tr>
  <tr>
   <td>Vorwärts</td>
   <td>ProcessManagementTaskService</td>
   <td>Vorwärts</td>
   <td>Leitet eine Aufgabe an einen anderen Benutzer weiter.</td>
  </tr>
  <tr>
   <td>konsultieren</td>
   <td>ProcessManagementTaskService</td>
   <td>konsultieren</td>
   <td>Er prüft eine Aufgabe mit einem anderen Benutzer.</td>
  </tr>
  <tr>
   <td>claim</td>
   <td>ProcessManagementTaskService</td>
   <td>claim</td>
   <td>Er beansprucht eine Aufgabe, die in einer freigegebenen Warteschlange verfügbar ist.</td>
  </tr>
  <tr>
   <td>entsperren</td>
   <td>ProcessManagementTaskService</td>
   <td>entsperren</td>
   <td>Entsperrt eine Aufgabe.</td>
  </tr>
  <tr>
   <td>lock</td>
   <td>ProcessManagementTaskService</td>
   <td>lock</td>
   <td>Sperrt eine Aufgabe und die Aufgabe kann von einem anderen Benutzer nicht angefordert werden, wenn sie freigegeben wurde.</td>
  </tr>
  <tr>
   <td>Ablehnen der Bedingungen</td>
   <td>ProcessManagementTaskService</td>
   <td>Ablehnen der Bedingungen</td>
   <td>Gibt eine Aufgabe an den vorherigen Eigentümer der Aufgabe zurück.</td>
  </tr>
  <tr>
   <td>abandon</td>
   <td>ProcessManagementTaskService</td>
   <td>abandon</td>
   <td>Löscht eine Aufgabe.</td>
  </tr>
  <tr>
   <td>setVisibility</td>
   <td>ProcessManagementTaskService</td>
   <td>setVisibility</td>
   <td>Er legt die Sichtbarkeit einer Aufgabe fest. Wenn Sichtbarkeit auf "false"gesetzt ist, ist die Aufgabe für den Benutzer danach nicht mehr sichtbar.</td>
  </tr>
  <tr>
   <td>getUsers</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsers</td>
   <td>Sie wird für die Suche nach Benutzern verwendet. Gibt alle Benutzer zurück, wenn kein Name angegeben ist, sonst werden Benutzer mit einem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getUsersInGroup</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersInGroupByName</td>
   <td>Es werden alle Benutzer einer Gruppe zurückgegeben.</td>
  </tr>
  <tr>
   <td>grantQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>grantQueueAccess</td>
   <td>Gewährt einem angegebenen Benutzer Zugriff auf die Warteschlange des angemeldeten Benutzers. Im Grunde wird Ihre eigene Warteschlange für einen anderen Benutzer freigegeben.</td>
  </tr>
  <tr>
   <td>requestQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>requestQueueAccess</td>
   <td>Stellt die Zugriffsanfrage einer Warteschlange eines bestimmten Benutzers für den angemeldeten Benutzer. Wenn der Benutzer die Anforderung genehmigt, wird die Warteschlange des Benutzers für den angemeldeten Benutzer freigegeben.</td>
  </tr>
  <tr>
   <td>getGrantedUsers</td>
   <td>ProcessManagementQueueService</td>
   <td>getGrantedUsers</td>
   <td>Es werden alle Benutzer zurückgegeben, die Zugriff auf die Warteschlange des angemeldeten Benutzers haben.</td>
  </tr>
  <tr>
   <td>getUsersForAccessibleQueues</td>
   <td>ProcessManagementQueueService</td>
   <td>getUsersForAccessibleQueues</td>
   <td>Gibt alle Benutzer zurück, deren Warteschlange für einen Benutzer zugänglich ist.</td>
  </tr>
  <tr>
   <td>cancelQueueAccess</td>
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
   <td>Ruft alle Warteschlangen (eigene, freigegebene und Gruppenwarteschlangen) ab, auf die der angemeldete Benutzer zugreifen kann.<br /> </td>
  </tr>
  <tr>
   <td>getOutOfOfficeSettings</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>getOutOfOfficeSettings</td>
   <td>Ruft die Abwesenheitseinstellungen eines Benutzers ab.</td>
  </tr>
  <tr>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>Speichert die Abwesenheitseinstellungen eines Benutzers.</td>
  </tr>
  <tr>
   <td>getAllProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getAllProcesses</td>
   <td>Es wird eine Liste aller Prozesse zurückgegeben.</td>
  </tr>
  <tr>
   <td>getParticipatedProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getParticipatedProcesses</td>
   <td>Es wird eine Liste aller Prozessnamen zurückgegeben, die vom angemeldeten Benutzer verwendet wurden.</td>
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
   <td>Es wird eine Liste aller Suchvorlagen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getTemplate</td>
   <td>ProcessManagementQueryService</td>
   <td>getTemplate</td>
   <td>Es werden Inhalte für eine Suchvorlage zurückgegeben.</td>
  </tr>
  <tr>
   <td>findTasksJson<br /> </td>
   <td>ProcessManagementQueryService</td>
   <td>findTasksJson</td>
   <td>Es werden alle Aufgaben gesucht und zurückgegeben, die alle Bedingungen einer Suchvorlage erfüllen.</td>
  </tr>
  <tr>
   <td>getAssignmentsForTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getAssignmentsForTask</td>
   <td>Ruft alle Zuweisungen für eine Aufgabe ab. Wenn ein Benutzer beispielsweise eine Aufgabe an einen anderen Benutzer weiterleitet oder sie mit ihm bespricht, ist dies eine Zuweisung für eine Aufgabe.</td>
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
   <td>Bei Bedarf wird die Bestätigung erneuert. Authentifiziert den Benutzer. Legt Sitzungsparameter für Server-/Client-Informationen fest. Gibt Benutzerinformationen und Abrufintervall zurück.</td>
  </tr>
  <tr>
   <td>getTasksForDirectReports</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getTasksForDirectReports</td>
   <td>Es werden alle Aufgaben der direkten Berichte des angemeldeten Managers zurückgegeben.</td>
  </tr>
  <tr>
   <td>getTaskOfDirectReport<br /> </td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getDirectReportTask</td>
   <td>Es wird eine Aufgabe eines bestimmten Direktberichts des angemeldeten Managers zurückgegeben.</td>
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
   <td>Es wird eine Aufgabe eines direkt unterstellten Mitarbeiters an den vorherigen Benutzer zurückgegeben.</td>
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
   <td>Entfernt eine Workspace-Eigenschaft für einen Benutzer.</td>
  </tr>
  <tr>
   <td>getProperties</td>
   <td>WorkspacePropertyService</td>
   <td>getPropertiesAsMap</td>
   <td>Es werden alle Workspace-Eigenschaften für einen Benutzer zurückgegeben.</td>
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
   <td>Ruft die Bild-URL des Benutzers für den angemeldeten Benutzer ab.</td>
  </tr>
  <tr>
   <td>getUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getUserImageUrl</td>
   <td>Ruft die Bild-URL des Benutzers für den angegebenen Benutzer ab.</td>
  </tr>
  <tr>
   <td>uploadNote</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadNote</td>
   <td>Er lädt eine Notiz für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>uploadRMAToServer (es wird auch direkt von der HTML-Vorlage aufgerufen)<br /> </td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadAttachment</td>
   <td>Er lädt eine Anlage für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>getImageURL (auch direkt über die HTML-Vorlage aufgerufen)</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>getImage</td>
   <td>Ruft das Bild für einen Prozess ab.</td>
  </tr>
 </tbody>
</table>
