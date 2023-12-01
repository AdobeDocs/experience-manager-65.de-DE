---
title: AEM Forms Workspace – JSON-Objektbeschreibung
description: Grundlegende Informationen zu den JSON JavaScript-Objekten, die in LiveCycle AEM Forms Workspace zur Anpassung, Erweiterung, Änderung und Wiederverwendung verwendet werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: f837a2b3-4650-4261-84c6-291bb2a46dc7
source-git-commit: 5e56441d2dc9b280547c91def8d971e7b1dfcfe3
workflow-type: tm+mt
source-wordcount: '2115'
ht-degree: 14%

---

# AEM Forms Workspace – JSON-Objektbeschreibung {#aem-forms-workspace-json-object-description}

Die in AEM Forms Workspace verwendeten JSON-Objekte werden unten beschrieben.

1. Kategorie

   Kategorien sind auf der Registerkarte &quot;Startprozess&quot;des Arbeitsbereichs vorhanden. Diese Kategorien werden verwendet, um die Startpunkte zu klassifizieren.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
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
   <td>Kategorie-ID<br type="_moz" /> </td>
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
   <td>Enthält eine Liste aller in einer Kategorie vorhandenen Startpunkte</td>
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
>Alle Startpunkte und Favoriten sind Kategorien, die clientseitig definiert werden. Die Kategorie &quot;Favorit&quot;enthält alle Startpunkte, die vom Benutzer als Favorit markiert werden. Die Kategorie &quot;Alle Startpunkte&quot;enthält alle Startpunkte.

1. Startpunkt

   Startpunkt wird verwendet, um einen Prozess aus dem Arbeitsbereich zu starten, wenn er aufgerufen wird.

   | **Eigenschaft** | **Nur Client** | **Kommentare** |
   |---|---|---|
   | categoryId | F | Sie enthält die ID der Kategorie, zu der der Startpunkt gehört. |
   | description | F | Es enthält eine Beschreibung für einen Startpunkt. |
   | name | F | Es enthält den Namen des Startpunkts. |
   | serializedImageTicket | F | Es enthält das Bild-Ticket, das dem Startpunkt entspricht. Dieses Bild-Ticket wird im imageUrl-Feld des Startpunkts verwendet, um vom Server ein Bild für den Startpunkt zu erhalten. |
   | serviceName | F | Es enthält den Namen des Diensts für den Startpunkt. |
   | startpointId | F | Es enthält die ID des Startpunkts. |
   | isFavorite | T | Gibt an, ob der Startpunkt ein Favorit ist oder nicht. True , wenn der Startpunkt der Favorit ist, sonst false. |
   | isDefaultImage | T | Gibt an, ob für den Prozess ein Bild angegeben ist oder nicht. &quot;True&quot;, wenn kein Bild mit dem Prozess verknüpft ist, andernfalls &quot;false&quot;. |
   | Aufgabe | T | Sie enthält Aufgaben, die beim Aufrufen des Startpunkts erstellt werden. |
   | imageUrl | T | Sie enthält die URL des Bildes, das dem Startpunkt entspricht. |

1. Aufgabe

   Aufgaben werden Benutzern/Gruppen zugewiesen und enthalten eine Benutzeroberfläche - ein Formular oder ein Guide (nicht mehr unterstützt) -, die mit Daten gefüllt werden kann. Wenn Benutzern eine Aufgabe zugewiesen wird, erhalten sie das Formular oder den Guide zum Ausfüllen und Senden.

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
   <td>Die Aufgabenklasse ist "LC8", wenn die Aufgabe lc8 ist, sonst "Standard".<br /> </td>
  </tr>
  <tr>
   <td>completeTime<br /> </td>
   <td>F</td>
   <td>Sie enthält den Zeitstempel, mit dem die Aufgabe abgeschlossen ist.<br /> </td>
  </tr>
  <tr>
   <td>consultGroupId<br /> </td>
   <td>F</td>
   <td>Es enthält die Kennung einer Gruppe, zu der die Aufgabe gehört werden kann. Sie wird während der Prozessentwicklung festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>createTime<br /> </td>
   <td>F</td>
   <td>Sie enthält den Zeitstempel, mit dem die Aufgabe erstellt wird.<br /> </td>
  </tr>
  <tr>
   <td>creationId<br /> </td>
   <td>F</td>
   <td>Es enthält die ID des Benutzers, der die Aufgabe erstellt hat.<br /> </td>
  </tr>
  <tr>
   <td>currentAssignment<br /> </td>
   <td>F</td>
   <td>Es enthält Details zur aktuellen Zuweisung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>deadline<br /> </td>
   <td>F</td>
   <td>Er enthält den Zeitstempel, der angibt, wann eine Aufgabe ihren Termin erreicht.<br /> </td>
  </tr>
  <tr>
   <td>description<br /> </td>
   <td>F</td>
   <td>Es enthält eine Beschreibung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>displayName<br /> </td>
   <td>F</td>
   <td>Es enthält den Anzeigenamen der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td>
   <td>F</td>
   <td>Es enthält die Kennung einer Gruppe, an die die Aufgabe weitergeleitet werden kann. Sie wird während der Prozessentwicklung festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>instructions<br /> </td>
   <td>F</td>
   <td>Es enthält Anweisungen für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>isLocked<br /> </td>
   <td>F</td>
   <td>True , wenn die Aufgabe gesperrt ist.<br /> </td>
  </tr>
  <tr>
   <td>isMustOpenToComplete<br /> </td>
   <td>F</td>
   <td>True , wenn das Aufgabenformular zum Abschließen der Aufgabe geöffnet werden muss.<br /> </td>
  </tr>
  <tr>
   <td>isOpenFullScreen<br /> </td>
   <td>F</td>
   <td>Wenn "true", nimmt das Formular beim Öffnen der Aufgabe beim ersten Mal den Vollbildmodus vor.<br /> </td>
  </tr>
  <tr>
   <td>isRouteSelectionRequired<br /> </td>
   <td>F</td>
   <td>Wenn "true", muss die Route ausgewählt werden, um die Aufgabe abzuschließen.<br /> </td>
  </tr>
  <tr>
   <td>isShowAttachments<br /> </td>
   <td>F</td>
   <td>Anlagen werden angezeigt, wenn sie wahr sind.<br /> </td>
  </tr>
  <tr>
   <td>isStartTask<br /> </td>
   <td>F</td>
   <td>Wenn "true", wird die Aufgabe vom Startpunkt aus erstellt.<br /> </td>
  </tr>
  <tr>
   <td>isVisible<br /> </td>
   <td>F</td>
   <td>True , wenn die Aufgabe im Arbeitsbereich sichtbar ist.<br /> </td>
  </tr>
  <tr>
   <td>nextReminder<br /> </td>
   <td>F</td>
   <td>Zeitstempel für die nächste Erinnerung.<br /> </td>
  </tr>
  <tr>
   <td>priority<br /> </td>
   <td>F</td>
   <td>Sie enthält die Priorität der Aufgabe.<br /> 1 = höchste Priorität<br /> 2 = Hohe Priorität<br /> 3 = Mittlere Priorität<br /> 4 = Niedrige Priorität<br /> 5 = Niedrigste Priorität<br />  </td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>F</td>
   <td>ID der Prozessinstanz, zu der die Aufgabe gehört.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br /> </td>
   <td>F</td>
   <td>Status der Prozessinstanz der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>reminderCount<br /> </td>
   <td>F</td>
   <td>Es enthält die Anzahl der Erinnerungen für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>routeList<br /> </td>
   <td>F</td>
   <td>Es enthält eine Liste der Routen, die mit der Aufgabe verknüpft sind. Der Benutzer kann die Aufgabe abschließen, indem er eine der Routen aus der Routenliste auswählt.<br /> </td>
  </tr>
  <tr>
   <td>selectedRoute<br /> </td>
   <td>F</td>
   <td>Es enthält den Namen der Route, die zum Zeitpunkt der Aufgabenfertigstellung ausgewählt wurde.<br /> </td>
  </tr>
  <tr>
   <td>serializedImageTicket<br /> </td>
   <td>F</td>
   <td>Es enthält ein Bild-Ticket, das der Aufgabe entspricht. Dieses Bild-Ticket wird im imageUrl-Feld der Aufgabe verwendet, um vom Server ein Bild für die Aufgabe zu erhalten.<br /> <br /> </td>
  </tr>
  <tr>
   <td>serviceName<br /> </td>
   <td>F</td>
   <td>Es enthält den Namen des Diensts für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>serviceTitle<br /> </td>
   <td>F</td>
   <td>Es enthält den Titel des Diensts für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>status<br /> </td>
   <td>F</td>
   <td>1 = Erstellt (Aufgabe wird vom Startpunkt erstellt.)<br /> 2 = Erstellt und gespeichert (Aufgabe wird vom Startpunkt erstellt und gespeichert.)<br /> 3 = Zugewiesen (Aufgabe wird dem Benutzer zugewiesen, nachdem der Prozess gestartet wurde.)<br /> 4 = Zugeordnet und gespeichert (Aufgabe wird zugewiesen und gespeichert.)<br /> 100 = Abgeschlossen (Aufgabe ist abgeschlossen.)<br /> 101 = Terminiert (Aufgabe hat den Termin erreicht.)<br /> 102 = Beendet<br /> </td>
  </tr>
  <tr>
   <td>stepName<br /> </td>
   <td>F</td>
   <td>Es enthält den Namen der Aufgabe, die während der Prozessgestaltung festgelegt wurde.<br /> </td>
  </tr>
  <tr>
   <td>summaryUrl<br /> </td>
   <td>F</td>
   <td>Sie enthält die Aufgabenzusammenfassungs-URL.<br /> </td>
  </tr>
  <tr>
   <td>taskACL<br /> </td>
   <td>F</td>
   <td>Es handelt sich um eine Zugriffssteuerungsliste für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskId<br /> </td>
   <td>F</td>
   <td>ID einer Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>updateTime<br /> </td>
   <td>F</td>
   <td>Zeitstempel der letzten Aktualisierung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>formUrl<br /> </td>
   <td>T</td>
   <td>Sie enthält die URL des Formulars für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskFormType<br /> </td>
   <td>T</td>
   <td>Enthält den Aufgabenformulartyp. Mithilfe dieses Felds wird die Aufgabe auf dem Client als PDF-Datei, als SWF-Formular usw. wiedergegeben.<br /> </td>
  </tr>
  <tr>
   <td>showDirectActions<br /> </td>
   <td>T</td>
   <td>Wenn "true", sind Route-Aktionen im Arbeitsbereich sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>showACLActions<br /> </td>
   <td>T</td>
   <td>Wenn "true", sind Aktionen wie "forward", "consult", "share"im Arbeitsbereich sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>supportsOffline<br /> </td>
   <td>T</td>
   <td>Wenn "true", kann das Formular offline geschaltet werden. Dies gilt nur für PDF-Formulare.<br /> </td>
  </tr>
  <tr>
   <td>supportsSave<br /> </td>
   <td>T</td>
   <td>Wenn "true", kann der Benutzer die Aufgabe speichern.<br /> </td>
  </tr>
  <tr>
   <td>readerSubmitOptions<br /> </td>
   <td>T</td>
   <td>Dieses Objekt enthält Optionen, die zum Senden von PDF-Formularen per Leser verwendet werden, falls das PDF-Formular keine Senden-Schaltfläche enthält.<br /> </td>
  </tr>
  <tr>
   <td>isDefaultImage<br /> </td>
   <td>T</td>
   <td>Gibt an, ob für den Prozess ein Bild angegeben ist oder nicht. "True", wenn kein Bild mit dem Prozess verknüpft ist, andernfalls "false".<br /> </td>
  </tr>
  <tr>
   <td>historyTaskList<br /> </td>
   <td>T</td>
   <td>Er enthält eine Liste der Aufgaben, die auf der Registerkarte Verlauf der Aufgabendetails verwendet werden.<br /> </td>
  </tr>
  <tr>
   <td>isOwner<br /> </td>
   <td>T</td>
   <td>True , wenn der angemeldete Benutzer Eigentümer der Aufgabe ist.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands<br /> </td>
   <td>T</td>
   <td>Es enthält alle Aktionen, die für die Aufgabe ausgeführt werden können.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.directCommands<br /> </td>
   <td>T</td>
   <td>Sie enthält alle Route-Aktionen, die für eine Aufgabe verfügbar sind.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.taskACLCommands<br /> </td>
   <td>T</td>
   <td>Es enthält Befehle wie Weiterleiten, Freigeben und Besprechen, falls für eine Aufgabe verfügbar.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.otherCommands<br /> </td>
   <td>T</td>
   <td>Sie enthält Befehle wie Sperren, Entsperren, Abbrechen, Zurückgeben, Anfordern usw., sofern verfügbar.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceInfo<br /> </td>
   <td>T</td>
   <td>Es enthält Informationen zur Prozessinstanz der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>processVariables<br /> </td>
   <td>T<br /> </td>
   <td>Es enthält ein Array von Objekten aus Prozessvariablen, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>pendingTasks<br /> </td>
   <td>T</td>
   <td>Sie enthält eine Liste der ausstehenden Aufgaben für die Prozessinstanz der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>userActions<br /> </td>
   <td>T</td>
   <td>Es handelt sich um eine Gruppe von Objekten. Jedes Objekt enthält Details zur Route und die entsprechende Bestätigungsmeldung, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>dataUrl<br /> </td>
   <td>T</td>
   <td>Dies ist die URL für die Daten des Aufgabenformulars.<br /> </td>
  </tr>
  <tr>
   <td>externalAppConfig<br /> </td>
   <td>T</td>
   <td>Dies ist die Konfiguration für Formulare von Drittanbieteranwendungen.<br /> </td>
  </tr>
  <tr>
   <td>Gesendet<br /> </td>
   <td>T</td>
   <td>True , wenn die Aufgabe gesendet wird.<br /> </td>
  </tr>
  <tr>
   <td>Anlagen<br /> </td>
   <td>T</td>
   <td>Liste der Anlagen für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>Zuweisungen<br /> </td>
   <td>T</td>
   <td>Liste der Zuweisungen einer Aufgabe<br /> </td>
  </tr>
 </tbody>
</table>

1. Filter

   Der Filter ist im Grunde eine Benutzerwarteschlange oder eine Gruppe. Wenn eine Aufgabe einem Benutzer/einer Gruppe zugewiesen wird, wird die Aufgabe der entsprechenden Warteschlange hinzugefügt.

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
   <td>True , wenn die Warteschlange die Standardwarteschlange des angemeldeten Benutzers ist, andernfalls false.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>name<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Eigentümers der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>qid</td>
   <td>F</td>
   <td>Kennung der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Typ</td>
   <td>F</td>
   <td>Enthält den Typ der Warteschlange.<br /> 0 - Benutzerwarteschlange.<br /> 1. Freigegebene Warteschlange.<br /> 2. Gruppenwarteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Abfrage</td>
   <td>T</td>
   <td>Dies enthält eine Abfrage, die mit einem Filter verknüpft ist. Diese Abfrage wird verwendet, um Aufgaben aus der vollständigen Aufgabenliste zu durchsuchen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Aufgaben</td>
   <td>T</td>
   <td>Er enthält eine Liste aller Aufgaben, die zu einem Filter gehören.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Abwesenheit

   Sie können Ihren Abwesenheitszeitplan verwalten und den Ablauf der Ihnen zugewiesenen Aufgaben in Ihrer Abwesenheit steuern.

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
   <td>Sie enthält Array-Objekte aus Abwesenheitszeitplänen eines Benutzers. In jedem Zeitplanobjekt enthält das Feld startDate das Startdatum des Zeitplans und endDate das Enddatum des Zeitplans. Wenn im Zeitplan das Feld endDate den Wert Null enthält, bedeutet dies, dass der Benutzer das Enddatum des Abwesenheitszeitplans nicht geplant hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isNoPrimaryDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>"true", wenn kein primärer Vertreter vorhanden ist, falls der Benutzer abwesend ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>"true", wenn der Benutzer abwesend ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>Es enthält Details zu Benutzern, die vom Benutzer als primäre Benennung zugewiesen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processSpecificDesignates<br type="_moz" /> </td>
   <td>F</td>
   <td>Sie enthält eine Gruppe von Objekten für prozessspezifische Abwesenheitsvertretungen. In jedem prozessspezifischen designierten Objekt enthält processName den Namen des Prozesses; isNotDesignated hat den Wert „true“, wenn dem entsprechenden Prozess kein Benutzer zugeordnet ist; userDesignated hat den Wert Null, wenn kein Benutzer Details dem Benutzer zugeordnet hat, der für den entsprechenden Vorgang vorgesehen war.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Prozesse<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält eine Liste aller Prozesse, die für den Benutzer verfügbar sind.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Sie enthält die anfänglichen Abwesenheitseinstellungen des Benutzers, die zunächst abgerufen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Sie enthält geänderte Abwesenheitseinstellungen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userSearchHistory<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält eine Liste von Benutzern, die von einem angemeldeten Benutzer bis zum Datum durchsucht werden.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Prozessinstanz

   Eine Prozessinstanz wird erstellt, wenn ein Prozess über Workspace oder Workbench aufgerufen wird.

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
   <td>Beschreibung der Prozessinstanz<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Initiator</td>
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
   <td>Zeitstempel zum Zeitpunkt, zu dem der Prozess abgeschlossen ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Initiiert<br /> 1 = Läuft<br /> 2 = Abgeschlossen<br /> 3 = Abgeschlossen<br /> 4 = Beendet<br /> 5 = Beenden<br /> 6 = Ausgesetzt<br /> 7 = Aussetzen<br /> 8 = Aufhebung der Aussetzung<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Prozesses.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processStartTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel zum Zeitpunkt, zu dem der Prozess gestartet wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processVariables<br type="_moz" /> </td>
   <td>F</td>
   <td>Array von Objekten aus Prozessvariablen. Jedes Objekt einer Prozessvariable enthält name, den Namen der Prozessvariable, value, den Wert der Prozessvariable und type, den Typ der Prozessvariable.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>tasklist<br type="_moz" /> </td>
   <td>T</td>
   <td>Von dieser Prozessinstanz erzeugte Aufgaben.<br type="_moz" /> </td>
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
   <td>Name des Prozesses.<br type="_moz" /> </td>
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

   Das Aufgabenzuweisungsobjekt enthält Informationen zur Aufgabenzuweisung. Im Folgenden finden Sie die Eigenschaften der Aufgabenzuweisung.

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
   <td>Zeitstempel der Erstellung dieser Aufgabenzuweisung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignmentType<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Erstzuweisung<br /> 1 = Weiterleiten (Aufgabe wurde an den aktuellen Eigentümer der Aufgabe weitergeleitet.)<br /> 2 = Zurückgegeben (Aufgabe wurde vom vorherigen Eigentümer der Aufgabe an den aktuellen Eigentümer der Aufgabe zurückgegeben.)<br /> 3 = Angefordert (Aufgabe wurde vom aktuellen Eigentümer der Aufgabe angefordert.)<br /> 4 = Eskalation (Aufgabe wurde nach der Eskalation dem aktuellen Eigentümer der Aufgabe zugewiesen.)<br /> 5 = Zugewiesener Administrator (Administrator hat die Aufgabe dem aktuellen Eigentümer der Aufgabe zugewiesen.)<br /> 6 = Consulted (Aufgabe wurde zum aktuellen Eigentümer der Aufgabe konsultiert.)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignmentUpdateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der Aktualisierung dieser Aufgabenzuweisung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td>
   <td>F</td>
   <td>Kennung der Warteschlange des aktuellen Eigentümers der Aufgabe.<br type="_moz" /> </td>
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

1. Task ACL Object

   Das Task ACL-Objekt enthält Informationen zu Berechtigungen wie Weiterleiten, Freigeben, Besprechen und so weiter. Im Folgenden finden Sie die Eigenschaften der ACL der Aufgabe.

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
   <td>Wenn "true", können der Aufgabe Anlagen hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canAddNotes<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", können der Aufgabe Notizen hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canClaim<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", kann die Aufgabe angefordert werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canConsult<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", kann die Aufgabe besprochen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canForward<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", kann die Aufgabe weitergeleitet werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canShare<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", kann die Aufgabe freigegeben werden.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Aufgabenanlage

   Anlagen können einer Aufgabe hinzugefügt werden. Anlage kann vom Typ Anlage und Notiz sein. Im Folgenden finden Sie die Eigenschaften des Anlagenobjekts.

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
   <td>Kennung des Benutzers, der die Anlage hinzugefügt hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Benutzers, der den Anhang hinzugefügt hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschreibung der Anlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>fileName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Anhangs.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>id<br type="_moz" /> </td>
   <td>F</td>
   <td>Kennung des Anhangs.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastModifiedDate<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel der letzten Anlagenänderung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>noteExtended<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn "true", ist die Notiz eine erweiterte (lange) Notiz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Berechtigungen<br type="_moz" /> </td>
   <td>F</td>
   <td>Berechtigungen, die mit einer Anlage verknüpft sind. Das Feld allowRead steht für die Leseberechtigung; allowWrite steht für die Schreibberechtigung, allowDelete steht für die Berechtigung zum Löschen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>size<br type="_moz" /> </td>
   <td>F</td>
   <td>Größe des Anhangs in Byte.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taskId<br type="_moz" /> </td>
   <td>F</td>
   <td>Kennung der Aufgabe, der ein Anhang hinzugefügt wird.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Typ<br type="_moz" /> </td>
   <td>F</td>
   <td>Der Typ ist „attachment“ für Dateien und „note“ für Anmerkungen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedCreationDate<br type="_moz" /> </td>
   <td>T</td>
   <td>Es enthält das Erstellungsdatum des Anhangs entsprechend den Benutzeroberflächeneinstellungen des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedDescription<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierte Anlagenbeschreibung Wird verwendet, um Sonderzeichen anzuzeigen, die in der Anlagenbeschreibung in AEM Forms Workspace vorhanden sind.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedFileName<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierter Anlagenname Wird verwendet, um Sonderzeichen im Anlagennamen in AEM Forms Workspace anzuzeigen. Dies gilt nur für Notizen.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. User

   Im Folgenden finden Sie die Eigenschaften des Benutzerobjekts.

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
   <td>"true", wenn der Benutzer abwesend ist.<br type="_moz" /> </td>
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
   <td>Kennung des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>org<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der Organisation des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>postalAddress<br type="_moz" /> </td>
   <td>F</td>
   <td>Postanschrift des Benutzers.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Telefon<br type="_moz" /> </td>
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
