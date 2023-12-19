---
title: APIs in AEM Forms Workspace
description: Öffentliche Java®- und JavaScript-APIs und Methoden von LiveCycle AEM Forms Workspace zur Anpassung und Automatisierung.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 9034f73a-83f3-498e-b6a6-ad6577aa1a3a
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 99%

---

# APIs in AEM Forms Workspace {#apis-used-in-aem-forms-workspace}

Die folgenden APIs werden in AEM Forms Workspace verwendet.

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
   <td>Sucht nach Gruppen. Gibt eine Liste aller Gruppen zurück, wenn kein Name angegeben ist. Andernfalls werden Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getUsersAndGroups</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersAndGroups</td>
   <td>Sucht nach Benutzenden und Gruppen. Gibt eine Liste aller Benutzenden und Gruppen zurück, wenn kein Name angegeben ist. Andernfalls werden Benutzende und Gruppen mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>prepareForSubmit</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>prepareForSubmit</td>
   <td>Wird aufgerufen, bevor das Formular über DocumentSubmitServlet gesendet wird. Legt die Aufgaben-ID in einer Sitzungsvariablen fest (zusammen mit der Ablaufzeit), die beim tatsächlichen Senden abgerufen wird.</td>
  </tr>
  <tr>
   <td>submitTask</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>absenden</td>
   <td>Sendet das Dokumentobjekt, das einer Aufgabe zugeordnet ist (und damit einem Absendeprozess).</td>
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
   <td>Ruft alle direkt untergeordneten Elemente für eine Kategorie ab.</td>
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
   <td>Dies ruft einen Startpunkt auf und erstellt eine Aufgabe, die einem Startpunkt zugeordnet ist.</td>
  </tr>
  <tr>
   <td>getAllTasks</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableTasks</td>
   <td>Ruft alle Aufgaben auf, die für die angemeldete Person erstellt, weitergeleitet, verwendet, zugewiesen oder gespeichert werden.</td>
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
   <td>Gibt eine Aufgabe wieder und gibt bei Bedarf Informationen zurück, die erforderlich sind, um das Formular zu rendern, wie Formular-URL, Formulartyp und Daten-URL.</td>
  </tr>
  <tr>
   <td>submitWithPriorData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithPriorData</td>
   <td>Gibt das Ergebnis der Submit-API von TaskManager mithilfe des Ergebnisschlüssels zurück.</td>
  </tr>
  <tr>
   <td>submitWithData</td>
   <td>ProcessManagementTaskService</td>
   <td>submitWithData</td>
   <td>Sendet die mit der Aufgabe verknüpften Formulardaten (übergeben als Zeichenfolge) mithilfe der Submit-API von TaskManager. Wird für Flex-Formulare verwendet, die nicht die Submit-API von TaskManager aufrufen.</td>
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
   <td>Schließt eine Aufgabe ab, die dann gemäß dem Prozess-Design an den nächsten Schritt übergeben wird.</td>
  </tr>
  <tr>
   <td>getAttachment</td>
   <td>ProcessManagementTaskService</td>
   <td>getAttachment</td>
   <td>Gibt eine URL eines Anhangs zurück, unter der der Anhang verfügbar ist.</td>
  </tr>
  <tr>
   <td>getAllAttachments</td>
   <td>ProcessManagementTaskService</td>
   <td>getAllActionableAttachments</td>
   <td>Ruft alle Anhänge und Hinweise für eine Aufgabe ab.</td>
  </tr>
  <tr>
   <td>Netzwerkfreigabe,</td>
   <td>ProcessManagementTaskService</td>
   <td>Netzwerkfreigabe,</td>
   <td>Gibt eine Aufgabe für eine andere Person frei. Eine andere Person kann die Aufgabe anfordern und wird Eigentümerin bzw. Eigentümer der Aufgabe.</td>
  </tr>
  <tr>
   <td>forward</td>
   <td>ProcessManagementTaskService</td>
   <td>forward</td>
   <td>Leitet eine Aufgabe an eine andere Person weiter.</td>
  </tr>
  <tr>
   <td>consult</td>
   <td>ProcessManagementTaskService</td>
   <td>consult</td>
   <td>Stimmt eine Aufgabe mit einer anderen Person ab.</td>
  </tr>
  <tr>
   <td>claim</td>
   <td>ProcessManagementTaskService</td>
   <td>claim</td>
   <td>Fordert eine Aufgabe an, die in einer freigegebenen Warteschlange verfügbar ist.</td>
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
   <td>Sperrt eine Aufgabe, die dadurch von anderen Benutzenden nicht angefordert werden kann, wenn sie freigegeben wird.</td>
  </tr>
  <tr>
   <td>Ablehnen der Bedingungen</td>
   <td>ProcessManagementTaskService</td>
   <td>Ablehnen der Bedingungen</td>
   <td>Gibt eine Aufgabe an die Person zurück, die zuvor deren Eigentümerin bzw. Eigentümer war.</td>
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
   <td>Legt die Sichtbarkeit einer Aufgabe fest. Wenn die Sichtbarkeit auf „false“ gesetzt ist, ist die Aufgabe für die Person danach nicht mehr sichtbar.</td>
  </tr>
  <tr>
   <td>getUsers</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsers</td>
   <td>Wird für die Suche nach Benutzenden verwendet. Gibt alle Benutzenden zurück, wenn kein Name angegeben ist, sonst werden die Benutzenden mit dem angegebenen Namen zurückgegeben.</td>
  </tr>
  <tr>
   <td>getUsersInGroup</td>
   <td>ProcessManagementUserProxyService</td>
   <td>getUsersInGroupByName</td>
   <td>Gibt alle Benutzenden in einer Gruppe zurück.</td>
  </tr>
  <tr>
   <td>grantQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>grantQueueAccess</td>
   <td>Gewährt einer angegebenen Person Zugriff auf die Warteschlange der angemeldeten Person. Im Grunde wird dadurch Ihre eigene Warteschlange für eine andere Person freigegeben.</td>
  </tr>
  <tr>
   <td>requestQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>requestQueueAccess</td>
   <td>Stellt für die angemeldete Person die Zugriffsanfrage für die Warteschlange einer bestimmten Person. Wenn die Person die Anfrage genehmigt, wird ihre Warteschlange für die angemeldete Person freigegeben.</td>
  </tr>
  <tr>
   <td>getGrantedUsers</td>
   <td>ProcessManagementQueueService</td>
   <td>getGrantedUsers</td>
   <td>Gibt alle Benutzenden zurück, die Zugriff auf die Warteschlange der angemeldeten Person haben.</td>
  </tr>
  <tr>
   <td>getUsersForAccessibleQueues</td>
   <td>ProcessManagementQueueService</td>
   <td>getUsersForAccessibleQueues</td>
   <td>Gibt alle Benutzenden zurück, deren Warteschlange für eine Person zugänglich ist.</td>
  </tr>
  <tr>
   <td>cancelQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>cancelQueueAccess</td>
   <td>Entfernt eine Person aus der Liste der Benutzenden, die Zugriff auf die Warteschlange der angemeldeten Person haben.</td>
  </tr>
  <tr>
   <td>removeQueueAccess</td>
   <td>ProcessManagementQueueService</td>
   <td>removeQueueAccess</td>
   <td>Entfernt eine Person aus der Liste der Benutzenden, deren Warteschlange für die angemeldete Person zugänglich ist.</td>
  </tr>
  <tr>
   <td>getAllQueues<br /> </td>
   <td>ProcessManagementQueueService<br /> </td>
   <td>getAllQueues<br /> </td>
   <td>Ruft alle Warteschlangen (eigene, freigegebene und Gruppenwarteschlangen) ab, die für die angemeldete Person zugänglich sind.<br /> </td>
  </tr>
  <tr>
   <td>getOutOfOfficeSettings</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>getOutOfOfficeSettings</td>
   <td>Ruft Abwesenheitseinstellungen einer Benutzerin oder eines Benutzers ab.</td>
  </tr>
  <tr>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>ProcessManagementOutOfOfficeService</td>
   <td>saveOutOfOfficeSettingsJson</td>
   <td>Speichert die Abwesenheitseinstellungen einer Benutzerin oder eines Benutzers.</td>
  </tr>
  <tr>
   <td>getAllProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getAllProcesses</td>
   <td>Gibt eine Liste aller Prozesse zurück.</td>
  </tr>
  <tr>
   <td>getParticipatedProcesses</td>
   <td>ProcessManagementProcessService</td>
   <td>getParticipatedProcesses</td>
   <td>Gibt eine Liste aller Prozessnamen zurück, an denen die angemeldete Person beteiligt ist.</td>
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
   <td>Gibt eine Liste aller Suchvorlagen zurück.</td>
  </tr>
  <tr>
   <td>getTemplate</td>
   <td>ProcessManagementQueryService</td>
   <td>getTemplate</td>
   <td>Gibt den Inhalt für eine Suchvorlage zurück.</td>
  </tr>
  <tr>
   <td>findTasksJson<br /> </td>
   <td>ProcessManagementQueryService</td>
   <td>findTasksJson</td>
   <td>Sucht und gibt alle Aufgaben zurück, die alle Bedingungen einer Suchvorlage erfüllen.</td>
  </tr>
  <tr>
   <td>getAssignmentsForTask</td>
   <td>ProcessManagementTaskService</td>
   <td>getAssignmentsForTask</td>
   <td>Ruft alle Zuweisung für eine Aufgabe ab. Beispiel: Wenn eine Benutzerin oder ein Benutzer eine Aufgabe an eine andere Person weiterleitet oder sich mit ihr darüber abstimmt, dann handelt es sich dabei um eine Aufgabenzuweisung.</td>
  </tr>
  <tr>
   <td>deleteAttachment </td>
   <td>TaskManagerService</td>
   <td>deleteAttachment</td>
   <td>Löscht einen Anhang.</td>
  </tr>
  <tr>
   <td>initialize</td>
   <td>ProcessManagementClientSessionService</td>
   <td>initialize</td>
   <td>Erneuert die Assertion, falls erforderlich. Authentifiziert die Benutzerin bzw. den Benutzer. Legt Sitzungsparameter für Server-/Client-Informationen fest. Gibt Benutzerinformation und Abrufintervall zurück.</td>
  </tr>
  <tr>
   <td>getTasksForDirectReports</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getTasksForDirectReports</td>
   <td>Gibt alle Aufgaben der Personen zurück, die dem angemeldeten Manager direkt unterstellt sind.</td>
  </tr>
  <tr>
   <td>getTaskOfDirectReport<br /> </td>
   <td>ProcessManagementTeamTasksService</td>
   <td>getDirectReportTask</td>
   <td>Gibt eine Aufgabe der angegebenen Person zurück, die dem angemeldeten Manager direkt unterstellt ist.</td>
  </tr>
  <tr>
   <td>forwardTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>forwardTaskOfDirectReport</td>
   <td>Leitet eine Aufgabe einer direkt unterstellten Person an eine andere Person weiter.</td>
  </tr>
  <tr>
   <td>rejectTaskOfDirectReport</td>
   <td>ProcessManagementTeamTasksService</td>
   <td>rejectTaskOfDirectReport</td>
   <td>Gibt eine Aufgabe einer direkt unterstellten Person an die vorherige Person zurück.</td>
  </tr>
  <tr>
   <td>getProperty</td>
   <td>WorkspacePropertyService</td>
   <td>getProperty</td>
   <td>Ruft eine Workspace-Eigenschaft für eine Person ab.</td>
  </tr>
  <tr>
   <td>removeProperty</td>
   <td>WorkspacePropertyService</td>
   <td>Löschen Sie</td>
   <td>Löscht eine Workspace-Eigenschaft für eine Benutzerin bzw. einen Benutzer.</td>
  </tr>
  <tr>
   <td>getProperties</td>
   <td>WorkspacePropertyService</td>
   <td>getPropertiesAsMap</td>
   <td>Gibt alle Workspace-Eigenschaften für eine Benutzerin bzw. einen Benutzer zurück.</td>
  </tr>
  <tr>
   <td>setProperty</td>
   <td>WorkspacePropertyService</td>
   <td>setProperty</td>
   <td>Legt eine Workspace-Eigenschaft für eine Benutzerin bzw. einen Benutzer fest.</td>
  </tr>
  <tr>
   <td>getCurrentUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getCurrentUserImageUrl</td>
   <td>Ruft die Bild-URL der Person für die angemeldete Person ab.</td>
  </tr>
  <tr>
   <td>getUserImageUrl</td>
   <td>ProcessManagementClientSessionService</td>
   <td>getUserImageUrl</td>
   <td>Ruft die Bild-URL der Person für die angegebene Person ab.</td>
  </tr>
  <tr>
   <td>uploadNote</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadNote</td>
   <td>Lädt eine Notiz für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>uploadRMAToServer (es wird auch direkt von der HTML-Vorlage aufgerufen)<br /> </td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>uploadAttachment</td>
   <td>Lädt einen Anhang für eine Aufgabe auf den Server hoch.</td>
  </tr>
  <tr>
   <td>getImageURL (wird auch direkt über die HTML-Vorlage aufgerufen)</td>
   <td>ProcessManagementDocumentHandlingService</td>
   <td>getImage</td>
   <td>Ruft das Bild für einen Prozess ab.</td>
  </tr>
 </tbody>
</table>
