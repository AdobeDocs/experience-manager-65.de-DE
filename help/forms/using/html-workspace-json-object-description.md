---
title: AEM Forms Workspace JSON-Objektbeschreibung
seo-title: AEM Forms Workspace JSON-Objektbeschreibung
description: Grundlegende Informationen zu JSON JavaScript-Objekten, die in LiveCycle AEM Forms Workspace zur Anpassung, Erweiterung, Änderung und erneuten Verwendung dienen.
seo-description: Grundlegende Informationen zu JSON JavaScript-Objekten, die in LiveCycle AEM Forms Workspace zur Anpassung, Erweiterung, Änderung und erneuten Verwendung dienen.
uuid: 91c923c8-144a-4453-ba91-6a5193f1c4c4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 61b7246d-ed28-4470-a0a2-a4aaf1a061a4
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 93%

---


# AEM Forms Workspace JSON-Objektbeschreibung {#aem-forms-workspace-json-object-description}

JSON-Objekte, die in AEM Forms Workspace verwendet werden, sind unten beschrieben.

1. Kategorie

   Kategorien sind auf der Workspace-Registerkarte „Prozess starten“ zu finden. Diese Kategorien werden verwendet, um die Startpunkte zu klassifizieren.

<table>
 <tbody>
  <tr>
   <td><strong>Property</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>name</td>
   <td>F</td>
   <td>Kategoriename</td>
  </tr>
  <tr>
   <td>id</td>
   <td>F</td>
   <td>Kategorien-ID<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Kategorienbeschreibung<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>parentOid<br type="_moz" /> </td>
   <td>F</td>
   <td>Enthält OID der übergeordneten Kategorie<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>startPointsList<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält eine Liste aller Startpunkte, die in einer Kategorie vorhanden sind</td>
  </tr>
  <tr>
   <td>categoryList</td>
   <td>T</td>
   <td>Enthält eine Liste der direkt untergeordneten Kategorien einer Kategorie<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Alle Startpunkte und Favoriten sind Kategorien, die clientseitig definiert werden. Die Kategorie „Favoriten“ enthält alle Startpunkte, die der Benutzer als Favorit markiert. Die Kategorie „Alle Startpunkte“ enthält alle Startpunkte.

1. Startpunkt

   Ein Startpunkt wird verwendet, um einen Prozess aus dem Arbeitsbereich zu starten, wenn dieser aufgerufen wird.

   | **Eigenschaft** | **Nur Client** | **Kommentare** |
   |---|---|---|
   | categoryId | F | Es enthält die ID der Kategorie, zu der der Startpunkt gehört. |
   | description | F | Es enthält die Beschreibung eines Startpunkts. |
   | name | F | Es enthält den Namen des Startpunkts. |
   | serializedImageTicket | F | Es enthält das Bild-Ticket, das dem Startpunkt entspricht. Dieses Bild-Ticket wird im imageUrl-Feld des Startpunkts verwendet, um vom Server ein Bild für den Startpunkt zu erhalten. |
   | serviceName | F | Es enthält den Namen des Diensts des Startpunkts. |
   | startpointId | F | Es enthält die ID des Startpunkts. |
   | isFavorite | T | Gibt an, ob der Startpunkt ein Favorit ist. „true“, wenn der Startpunkt ein Favorit ist, andernfalls „false“. |
   | isDefaultImage | T | Gibt an, ob für einen Prozess ein Bild festgelegt ist. „true“, wenn kein Bild mit dem Prozess verknüpft ist, andernfalls „false“. |
   | Aufgabe | T | Es enthält die Aufgabe, die beim Aufrufen des Startpunkts erstellt wird. |
   | imageUrl | T | Es enthält die URL des Bildes, das dem Startpunkt entspricht. |

1. Aufgabe

   Aufgaben werden Benutzern/einer Gruppe zugewiesen und enthalten eine Benutzeroberfläche – ein Formular oder ein Guide (nicht mehr unterstützt) – die mit Daten aufgefüllt werden. Wenn Benutzer einer Aufgabe zugewiesen sind, erhalten sie das Formular oder den Guide, die ausgefüllt und abgesendet werden müssen.

<table>
 <tbody>
  <tr>
   <td>Eigenschaft<br /> </td>
   <td>Nur Client<br /> </td>
   <td>Kommentare<br /> </td>
  </tr>
  <tr>
   <td>classOfTask</td>
   <td>F</td>
   <td>Die Klasse der Aufgabe ist „LC8“, wenn die Aufgabe lc8 ist, andernfalls „Standard“.<br /> </td>
  </tr>
  <tr>
   <td>completeTime<br /> </td>
   <td>F</td>
   <td>Es enthält den Zeitstempel, wenn die Aufgabe abgeschlossen ist.<br /> </td>
  </tr>
  <tr>
   <td>consultGroupId<br /> </td>
   <td>F</td>
   <td>Es enthält die ID einer Gruppe, zu der Aufgabe überprüft werden kann. Es wird während der Prozessentwicklung festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>createTime<br /> </td>
   <td>F</td>
   <td>Es enthält den Zeitstempel, wenn die Aufgabe erstellt wird.<br /> </td>
  </tr>
  <tr>
   <td>creationId<br /> </td>
   <td>F</td>
   <td>Es enthält die ID des Benutzers, der die Aufgabe erstellt hat.<br /> </td>
  </tr>
  <tr>
   <td>currentAssignment<br /> </td>
   <td>F</td>
   <td>Es enthält Informationen über die aktuelle Zuweisung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>deadline<br /> </td>
   <td>F</td>
   <td>Er enthält den Zeitstempel vom Zeitpunkt, zu dem der Fälligkeitstermin einer Aufgabe abgelaufen ist.<br /> </td>
  </tr>
  <tr>
   <td>description<br /> </td>
   <td>F</td>
   <td>Es enthält die Beschreibung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>displayName<br /> </td>
   <td>F</td>
   <td>Es enthält den Anzeigenamen der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td>
   <td>F</td>
   <td>Es enthält die ID einer Gruppe, an die Aufgabe weitergeleitet werden der kann. Es wird während der Prozessentwicklung festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>instructions<br /> </td>
   <td>F</td>
   <td>Es enthält die Anweisungen zu einer Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>isLocked<br /> </td>
   <td>F</td>
   <td>„true“, wenn die Aufgabe gesperrt ist.<br /> </td>
  </tr>
  <tr>
   <td>isMustOpenToComplete<br /> </td>
   <td>F</td>
   <td>„true“, wenn das Aufgabenformular geöffnet sein muss, um die Aufgabe abzuschließen.<br /> </td>
  </tr>
  <tr>
   <td>isOpenFullScreen<br /> </td>
   <td>F</td>
   <td>Wenn „true“, dann wird beim Öffnen der Aufgabe das Formular beim ersten Mal als Vollbild angezeigt.<br /> </td>
  </tr>
  <tr>
   <td>isRouteSelectionRequired<br /> </td>
   <td>F</td>
   <td>Wenn „true“, muss die Route muss ausgewählt sein, um die Aufgabe abzuschließen.<br /> </td>
  </tr>
  <tr>
   <td>isShowAttachments<br /> </td>
   <td>F</td>
   <td>Anlagen werden angezeigt, wenn auf „true“ gesetzt.<br /> </td>
  </tr>
  <tr>
   <td>isStartTask<br /> </td>
   <td>F</td>
   <td>Wenn „true“, wird die Aufgabe vom Startpunkt aus erstellt.<br /> </td>
  </tr>
  <tr>
   <td>isVisible<br /> </td>
   <td>F</td>
   <td>„true“, wenn die Aufgabe im Workspace sichtbar ist.<br /> </td>
  </tr>
  <tr>
   <td>nextReminder<br /> </td>
   <td>F</td>
   <td>Zeitstempel für die nächste Erinnerung<br /> </td>
  </tr>
  <tr>
   <td>priority<br /> </td>
   <td>F</td>
   <td>Es enthält die Priorität der Aufgabe.<br />1 = höchste Priorität<br /> 2 = Hohe Priorität<br /> 3 = Mittlere Priorität<br /> 4 = Niedrige Priorität<br /> 5 = Niedrigste Priorität<br />  </td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>F</td>
   <td>ID der Prozessinstanz, zu der die Aufgabe gehört.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br /> </td>
   <td>F</td>
   <td>Status der Prozessinstanzaufgabe.<br /> </td>
  </tr>
  <tr>
   <td>reminderCount<br /> </td>
   <td>F</td>
   <td>Es enthält die Anzahl der Erinnerungen zu der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>routeList<br /> </td>
   <td>F</td>
   <td>Es enthält die Liste der Routen, die zu der Aufgabe gehören. Benutzer können die Aufgabe abschließen, indem sie eine Route aus der Liste der Routen auswählen.<br /> </td>
  </tr>
  <tr>
   <td>selectedRoute<br /> </td>
   <td>F</td>
   <td>Es enthält den Namen der Route, die beim Abschließen der Aufgabe ausgewählt wurde.<br /> </td>
  </tr>
  <tr>
   <td>serializedImageTicket<br /> </td>
   <td>F</td>
   <td>Es enthält das Bild-Ticket, das der Aufgabe entspricht. Dieses Bild-Ticket wird im imageUrl-Feld der Aufgabe verwendet, um vom Server ein Bild für die Aufgabe zu erhalten.<br /> <br /> </td>
  </tr>
  <tr>
   <td>serviceName<br /> </td>
   <td>F</td>
   <td>Es enthält den Namen des Diensts der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>serviceTitle<br /> </td>
   <td>F</td>
   <td>Es enthält den Titel des Diensts der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>status<br /> </td>
   <td>F</td>
   <td>1 = Erstellt (Aufgabe wird vom Startpunkt erstellt.)<br /> 2 = Erstellt und gespeichert (Aufgabe wird vom Startpunkt erstellt und gespeichert.)<br /> 3 = Zugewiesen (Aufgabe wird dem Benutzer zugewiesen, nachdem der Prozess gestartet wurde.)<br /> 4 = Zugewiesen und gespeichert (Aufgabe wird zugewiesen und gespeichert.)<br /> 100 = Abgeschlossen (Aufgabe wurde abgeschlossen.)<br /> 101 = Termin erreicht (Aufgabe hat den Termin erreicht.)<br /> 102 = Beendet<br /> </td>
  </tr>
  <tr>
   <td>stepName<br /> </td>
   <td>F</td>
   <td>Er enthält den Namen der Aufgabe, die während der Prozessentwicklung gesetzt wurde.<br /> </td>
  </tr>
  <tr>
   <td>summaryUrl<br /> </td>
   <td>F</td>
   <td>Es enthält die Aufgabenzusammenfassungs-URL.<br /> </td>
  </tr>
  <tr>
   <td>taskACL<br /> </td>
   <td>F</td>
   <td>Es ist die Zugriffssteuerungsliste für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskId<br /> </td>
   <td>F</td>
   <td>Es ist die ID einer Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>updateTime<br /> </td>
   <td>F</td>
   <td>Der Zeitstempel der letzten Aufgabenaktualisierung.<br /> </td>
  </tr>
  <tr>
   <td>formUrl<br /> </td>
   <td>T</td>
   <td>Es enthält die URL des Formulars für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskFormType<br /> </td>
   <td>T</td>
   <td>Es enthält den Aufgabenformularart. Wenn dieses Feld verwendet wird, wird die Aufgabe auf dem Client als PDF-Formular, SWF-Formular usw. wiedergegeben.<br /> </td>
  </tr>
  <tr>
   <td>showDirectActions<br /> </td>
   <td>T</td>
   <td>Wenn „true“, sind Route-Aktionen im Arbeitsbereich sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>showACLActions<br /> </td>
   <td>T</td>
   <td>Wenn „true“, sind Aktionen wie Weiterleiten, Lesen und Freigeben im Arbeitsbereich sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>supportsOffline<br /> </td>
   <td>T</td>
   <td>Wenn „true“, kann das Formular offline verwendet werden. Dies ist nur für PDF-Formulare.<br /> </td>
  </tr>
  <tr>
   <td>supportsSave<br /> </td>
   <td>T</td>
   <td>Wenn „true“, können Benutzer die Aufgabe speichern.<br /> </td>
  </tr>
  <tr>
   <td>readerSubmitOptions<br /> </td>
   <td>T</td>
   <td>Dieses Objekt enthält Optionen, die verwendet werden, um PDF-Formulare über Reader zu senden, wenn das PDF-Formular keine Schaltfläche zum Senden enthält.<br /> </td>
  </tr>
  <tr>
   <td>isDefaultImage<br /> </td>
   <td>T</td>
   <td>Gibt an, ob für einen Prozess ein Bild festgelegt ist. „true“, wenn kein Bild mit dem Prozess verknüpft ist, andernfalls „false“.<br /> </td>
  </tr>
  <tr>
   <td>historyTaskList<br /> </td>
   <td>T</td>
   <td>Es enthält eine Liste von Aufgaben, die auf der Verlaufs-Registerkarte in den Aufgabeninformationen verwendet werden.<br /> </td>
  </tr>
  <tr>
   <td>isOwner<br /> </td>
   <td>T</td>
   <td>„true“, wenn angemeldeter Benutzer Eigentümer der Aufgabe ist.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands<br /> </td>
   <td>T</td>
   <td>Sie enthält alle Aktionen, die für eine Aufgabe ausgeführt werden können.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.directCommands<br /> </td>
   <td>T</td>
   <td>Es enthält alle Route-Aktionen, die für eine Aufgabe verfügbar sind.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.taskACLCommands<br /> </td>
   <td>T</td>
   <td>Es enthält die Befehle wie „Weiterleiten“, „Freigeben“ und „Besprechen“, wenn sie für eine Aufgabe verfügbar sind.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.otherCommands<br /> </td>
   <td>T</td>
   <td>Es enthält die Befehle wie „Sperren“, „Sperre aufheben“, „Abbrechen“, „Zurückgeben“ und „Anfordern“ usw.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceInfo<br /> </td>
   <td>T</td>
   <td>Es enthält Informationen über die Prozessinstanz der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>processVariables<br /> </td>
   <td>T<br /> </td>
   <td>Es enthält ein Array von Objekten aus Prozessvariablen, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>pendingTasks<br /> </td>
   <td>T</td>
   <td>Es enthält eine Liste der ausstehenden Aufgaben für die Aufgabenprozessinstanz.<br /> </td>
  </tr>
  <tr>
   <td>userActions<br /> </td>
   <td>T</td>
   <td>Es ist Array von Objekten. Jedes Objekt enthält Informationen über eine Route und die entsprechende Bestätigungsmeldung, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>dataUrl<br /> </td>
   <td>T</td>
   <td>Es ist die URL für die Daten eines Aufgabenformulars.<br /> </td>
  </tr>
  <tr>
   <td>externalAppConfig<br /> </td>
   <td>T</td>
   <td>Das ist die Konfiguration für die Formulare von Drittanbieteranwendungen.<br /> </td>
  </tr>
  <tr>
   <td>Gesendet<br /> </td>
   <td>T</td>
   <td>„true“, wenn eine Aufgabe gesendet wird.<br /> </td>
  </tr>
  <tr>
   <td>Anlagen<br /> </td>
   <td>T</td>
   <td>Eine Liste der Anlagen für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>Zuweisungen<br /> </td>
   <td>T</td>
   <td>Eine Liste der Zuweisungen einer Aufgabe.<br /> </td>
  </tr>
 </tbody>
</table>

1. Filter

   Ein Filter ist im Allgemeinen eine Benutzer- oder Gruppenwarteschlange. Wenn eine Aufgabe einem Benutzer/einer Gruppe zugewiesen wird, wird die Aufgabe der entsprechenden Warteschlange hinzugefügt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>isDefault <br type="_moz" /> </td>
   <td>F</td>
   <td>„true“, wenn die Warteschlange die Standardwarteschlange des angemeldeten Benutzers ist, andernfalls „false“.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>name<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Eigentümers der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>qid</td>
   <td>F</td>
   <td>ID der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type</td>
   <td>F</td>
   <td>Dieser enthält den Typ der Warteschlange.<br /> 0 – Benutzerwarteschlange.<br /> 1. Freigegebene Warteschlange.<br /> 2. Gruppenwarteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Abfrage</td>
   <td>T</td>
   <td>Diese enthält eine Abfrage, die mit dem Filter verknüpft ist. Diese Abfrage wird verwendet, um Aufgaben in der gesamten Tasklist zu suchen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Aufgaben</td>
   <td>T</td>
   <td>Dies enthält eine Liste aller Aufgaben, die zu einem Filter gehört.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Abwesenheit

   Sie können Ihren Abwesenheitszeitplan verwalten und die Menge der Aufgaben kontrollieren, die Ihnen in Ihrer Abwesenheit zugewiesen werden.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong><br type="_moz" /> </td>
   <td><strong>Nur Client</strong><br type="_moz" /> </td>
   <td><strong>Kommentare</strong><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>dateRanges<br type="_moz" /> </td>
   <td>F</td>
   <td>Es enthält Array-Objekte aus Abwesenheitszeitplänen eines Benutzers. In jedem Zeitplanobjekt enthält das Feld startDate das Beginn des Zeitplans und endDate das Enddatum des Zeitplans. Wenn endDate im Zeitplan null ist, bedeutet dies, dass der Benutzer das Enddatum des Abwesenheitszeitplans nicht geplant hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isNoPrimaryDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>„true“, wenn es in Abwesenheit des Benutzers keinen primären Vertreter gibt.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>„true“, wenn der Benutzer abwesend ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>Es enthält die Details zu dem Benutzer, der vom Benutzer als primärer Vertreter vorgesehen wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processSpecificDesignates<br type="_moz" /> </td>
   <td>F</td>
   <td>Es enthält ein Array von Objekten für prozessspezifische Vertreter für den Abwesenheitszeitraum. In jedem prozessspezifischen designierten Objekt enthält processName den Namen des Prozesses, isNotDesignated ist "true", wenn keinem Benutzer der entsprechende Prozess zugewiesen ist, und userDesignated ist "null", wenn keinem Benutzer weitere Details des für den entsprechenden Prozess zugewiesenen Benutzers zugewiesen wurden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Prozesse<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält eine Liste aller Prozesse, die dem Benutzer zur Verfügung stehen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält die Anfangseinstellungen des Benutzers für die Abwesenheit, die zuerst abgerufen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält geänderte Abwesenheitseinstellungen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userSearchHistory<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält eine Liste von Benutzern, die der angemeldete Benutzer bisher gesucht hat.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Prozessinstanz

   Eine Prozessinstanz wird erstellt, wenn ein Prozess über die Workspace oder Workbench aufgerufen wird.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschreibung der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>F</td>
   <td>Name des Initiators einer Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>F</td>
   <td>ID des Initiators der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processCompleteTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel zum Zeitpunkt, als der Vorgang abgeschlossen wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Initiiert<br /> 1 = Wird ausgeführt<br /> 2 = Abgeschlossen<br /> 3 = Wird abgeschlossen<br />4 = Beendet<br /> 5 = Wird beendet<br /> 6 = Ausgesetzt<br /> 7 = Wird ausgesetzt<br /> 8 = Aussetzen wird aufgehoben<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Der Name des Vorgangs.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processStartTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel zum Zeitpunkt, als der Prozess gestartet wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processVariables<br type="_moz" /> </td>
   <td>F</td>
   <td>Array von Objekten aus Prozessvariablen Jedes Objekt einer Prozessvariable enthält den Namen der Prozessvariable, den Wert der Prozessvariable und den Typ der Prozessvariable.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>tasklist<br type="_moz" /> </td>
   <td>T</td>
   <td>Aufgaben, die von dieser Prozessinstanz generiert werden.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Prozessname

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>processMajorVersion<br type="_moz" /> </td>
   <td>F</td>
   <td>Hauptversion eines Prozesses.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processMinorVersion<br type="_moz" /> </td>
   <td>F</td>
   <td>Nebenversion eines Prozesses.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Der Name des Vorgangs.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processTitle<br type="_moz" /> </td>
   <td>F</td>
   <td>Titel des Prozesses.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceList<br type="_moz" /> </td>
   <td>T</td>
   <td>Liste der Prozessinstanzen für diesen Prozess.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Aufgabenzuweisungsobjekt

   Ein Aufgabenzuweisungsobjekt enthält Informationen über die Zuweisung einer Aufgabe. Im Folgenden sind die Eigenschaften der Zuweisung einer Aufgabe aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>assignmentCreateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der Erstellung einer Aufgabenzuweisung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignmentType<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Erste Zuweisung<br /> 1 = Weiterleiten (Aufgabe wurde an den aktuellen Eigentümer der Aufgabe weitergeleitet.)<br /> 2 = Zurückgegeben (Der vorherige Eigentümer der Aufgabe hat die Aufgabe dem aktuellen Eigentümer der Aufgabe zurückgegeben.)<br /> 3 = Angefordert (Aufgabe wurde vom aktuellen Eigentümer der Aufgabe angefordert.)<br /> 4 = Eskalation (Aufgabe wurde nach der Eskalation dem aktuellen Eigentümer der Aufgabe zugewiesen.)<br /> 5 = Zugewiesener Administrator (Administrator hat die Aufgabe dem aktuellen Eigentümer der Aufgabe zugewiesen.)<br /> 6 = Besprechen (Aufgabe wurde dem aktuellen Eigentümer der Aufgabe zum Besprechen zugewiesen.)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignmentUpdateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der Aktualisierung einer Aufgabenzuweisung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Warteschlange des aktuellen Eigentümers der Aufgabe.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwner<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des aktuellen Eigentümers der Aufgabe.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwnerId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID des aktuellen Eigentümers der Aufgabe.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Aufgaben-ACL-Objekt

   Ein Aufgaben-ACL-Objekt enthält Informationen über Berechtigungen wie z. B. zum Weiterleiten, Freigeben, Besprechen usw. einer Aufgabe. Im Folgenden sind die Eigenschaften der Zugriffssteuerungsliste (ACL) einer Aufgabe aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>canAddAttachments<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, können der Aufgabe Anlagen hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canAddNotes<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, können der Aufgabe Notizen hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canClaim<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, kann die Aufgabe angefordert werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canConsult<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, kann die Aufgabe besprochen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canForward<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, kann die Aufgabe weitergeleitet werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canShare<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, kann die Aufgabe freigegeben werden.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Aufgabenanlage

   Anlagen können einer Aufgabe hinzugefügt werden. Eine Anlage kann eine Anlage und Notiz sein. Im Folgenden sind die Eigenschaften eines Anlagenobjekts aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>creationDate<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der Anlagenerstellung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID des Benutzers, der die Anlage hinzugefügt hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Benutzers, der die Anlage hinzugefügt hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschreibung der Anlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>fileName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der Anlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>id<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Anlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastModifiedDate<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der letzten Anlagenänderung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>noteExtended<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, ist die Notiz eine erweiterte (lange) Notiz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Berechtigungen<br type="_moz" /> </td>
   <td>F</td>
   <td>Berechtigungen, die mit einer Anlage verknüpft sind allowRead-Feld ist für Leseberechtigung, allowWrite für Schreibberechtigung, allowDelete für Löschberechtigung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>size<br type="_moz" /> </td>
   <td>F</td>
   <td>Größe der Anlage in Byte.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taskId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Aufgabe, der die Anlage hinzugefügt wird.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type<br type="_moz" /> </td>
   <td>F</td>
   <td>Typ ist Anhang für Dateien und Typ Notiz für Notizen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedCreationDate<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält das Erstellungsdatum der Anlage, nach den Benutzeroberflächeneinstellungen des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedDescription<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierte Anlagenbeschreibung Wird verwendet, um Sonderzeichen in der Anlagenbeschreibung in AEM Forms Workspace anzuzeigen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedFileName<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierter Anlagenname Wird verwendet, um Sonderzeichen im Anlagennamen in AEM FormsWorkspace anzuzeigen. Dies ist nur für Notizen verfügbar.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. User

   Im Folgenden sind die Eigenschaften des Benutzerobjekts aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Nur Client</strong></td>
   <td><strong>Kommentare</strong></td>
  </tr>
  <tr>
   <td>Adresse<br type="_moz" /> </td>
   <td>F</td>
   <td>Adresse des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>commonName<br type="_moz" /> </td>
   <td>F</td>
   <td>Allgemeiner Name des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschreibung des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>directGroupMemberships<br type="_moz" /> </td>
   <td>F</td>
   <td>Liste der Benutzergruppe.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>displayName<br type="_moz" /> </td>
   <td>F</td>
   <td>Anzeigename des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>email<br type="_moz" /> </td>
   <td>F</td>
   <td>E-Mail-ID des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>„true“, wenn der Benutzer abwesend ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastName<br type="_moz" /> </td>
   <td>F</td>
   <td>Nachname des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>firstName<br type="_moz" /> </td>
   <td>F</td>
   <td>Vorname des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>oid<br type="_moz" /> </td>
   <td>F</td>
   <td>ID des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Firma<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der Firma des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>postalAddress<br type="_moz" /> </td>
   <td>F</td>
   <td>Postanschrift des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Telefonnummer<br type="_moz" /> </td>
   <td>F</td>
   <td>Kontaktnummer des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>telephoneNumber<br type="_moz" /> </td>
   <td>F</td>
   <td>Kontaktnummer des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userid<br type="_moz" /> </td>
   <td>F</td>
   <td>Anmelde-ID des Benutzers.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>
