---
title: AEM Forms Workspace – JSON-Objektbeschreibung
description: Grundlegende Informationen zu JSON-JavaScript-Objekten, die in LiveCycle AEM Forms Workspace zur Anpassung, Erweiterung, Änderung und erneuten Verwendung dienen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: f837a2b3-4650-4261-84c6-291bb2a46dc7
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2144'
ht-degree: 100%

---

# AEM Forms Workspace – JSON-Objektbeschreibung {#aem-forms-workspace-json-object-description}

JSON-Objekte, die in AEM Forms Workspace verwendet werden, werden unten beschrieben.

1. Kategorie

   Kategorien sind auf der Workspace-Registerkarte „Prozess starten“ zu finden. Diese Kategorien werden verwendet, um die Startpunkte zu klassifizieren.

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
   <td>Kategoriename.</td>
  </tr>
  <tr>
   <td>id</td>
   <td>F</td>
   <td>Kategorie-ID.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Kategoriebeschreibung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>parentOid<br type="_moz" /> </td>
   <td>F</td>
   <td>Enthält die OID der übergeordneten Kategorie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>startPointsList<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält eine Liste aller Startpunkte, die in einer Kategorie vorhanden sind.</td>
  </tr>
  <tr>
   <td>categoryList</td>
   <td>T</td>
   <td>Enthält eine Liste der direkt untergeordneten Kategorien einer Kategorie.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Alle Startpunkte und Favoriten sind Kategorien, die Client-seitig definiert werden. Die Kategorie „Favoriten“ enthält alle Startpunkte, die Benutzende als Favoriten markieren. Die Kategorie „Alle Startpunkte“ enthält alle Startpunkte.

1. Startpoint

   Ein Startpunkt wird verwendet, um einen Prozess aus dem Arbeitsbereich zu starten, wenn er aufgerufen wird.

   | **Eigenschaft** | **Nur Client** | **Kommentare** |
   |---|---|---|
   | categoryId | F | Enthält die ID der Kategorie, zu der der Startpunkt gehört. |
   | description | F | Enthält die Beschreibung eines Startpunkts. |
   | name | F | Enthält den Namen des Startpunkts. |
   | serializedImageTicket | F | Es enthält das Bild-Ticket, das dem Startpunkt entspricht. Dieses Bild-Ticket wird im imageUrl-Feld des Startpunkts verwendet, um vom Server ein Bild für den Startpunkt zu erhalten. |
   | serviceName | F | Enthält den Namen des Dienstes für den Startpunkt. |
   | startpointId | F | Enthält die ID des Startpunkts. |
   | isFavorite | T | Gibt an, ob der Startpunkt ein Favorit ist oder nicht. „True“, wenn der Startpunkt ein Favorit ist, sonst „false“. |
   | isDefaultImage | T | Gibt an, ob für den Prozess ein Bild angegeben wurde oder nicht. „True“, wenn dem Prozess kein Bild zugeordnet ist, sonst „false“. |
   | task | T | Enthält eine Aufgabe, die beim Aufrufen des Startpunkts erstellt wird. |
   | imageUrl | T | Enthält die URL des Bildes, das dem Startpunkt entspricht. |

1. Aufgabe

   Aufgaben werden Benutzenden/Gruppen zugewiesen und umfassen eine Benutzeroberfläche – ein Formular oder einen Leitfaden (veraltet) –, die mit Daten gefüllt werden kann. Wenn Benutzenden eine Aufgabe zugewiesen wird, erhalten sie das Formular bzw. den Leitfaden zum Ausfüllen und Absenden.

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
   <td>Die Aufgabenklasse ist „LC8“, wenn es sich um eine LC8-Aufgabe handelt, andernfalls „Standard“.<br /> </td>
  </tr>
  <tr>
   <td>completeTime<br /> </td>
   <td>F</td>
   <td>Enthält den Zeitstempel, wenn die Aufgabe abgeschlossen ist.<br /> </td>
  </tr>
  <tr>
   <td>consultGroupId<br /> </td>
   <td>F</td>
   <td>Enthält die ID einer Gruppe, für die die Aufgabe konsultiert werden kann. Wird während des Prozessentwurfs festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>createTime<br /> </td>
   <td>F</td>
   <td>Enthält den Zeitstempel, wenn die Aufgabe erstellt wird.<br /> </td>
  </tr>
  <tr>
   <td>creationId<br /> </td>
   <td>F</td>
   <td>Enthält die ID der Person, die die Aufgabe erstellt hat.<br /> </td>
  </tr>
  <tr>
   <td>currentAssignment<br /> </td>
   <td>F</td>
   <td>Enthält Details zur aktuellen Aufgabenzuweisung.<br /> </td>
  </tr>
  <tr>
   <td>deadline<br /> </td>
   <td>F</td>
   <td>Enthält den Zeitstempel, wann eine Aufgabe ihre Frist erreicht.<br /> </td>
  </tr>
  <tr>
   <td>description<br /> </td>
   <td>F</td>
   <td>Enthält die Beschreibung der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>displayName<br /> </td>
   <td>F</td>
   <td>Enthält den Anzeigenamen der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td>
   <td>F</td>
   <td>Enthält die ID einer Gruppe, an die die Aufgabe weitergeleitet werden kann.  Wird während des Prozessentwurfs festgelegt.<br /> </td>
  </tr>
  <tr>
   <td>instructions<br /> </td>
   <td>F</td>
   <td>Enthält Anweisungen für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>isLocked<br /> </td>
   <td>F</td>
   <td>„True“, wenn die Aufgabe gesperrt ist.<br /> </td>
  </tr>
  <tr>
   <td>isMustOpenToComplete<br /> </td>
   <td>F</td>
   <td>„True“, wenn das Aufgabenformular geöffnet werden muss, um die Aufgabe abzuschließen.<br /> </td>
  </tr>
  <tr>
   <td>isOpenFullScreen<br /> </td>
   <td>F</td>
   <td>Wenn „true“, nimmt das Formular beim erstmaligen Öffnen den vollständigen Bildschirm ein.<br /> </td>
  </tr>
  <tr>
   <td>isRouteSelectionRequired<br /> </td>
   <td>F</td>
   <td>Wenn „true“, muss die Route ausgewählt werden, um die Aufgabe abzuschließen.<br /> </td>
  </tr>
  <tr>
   <td>isShowAttachments<br /> </td>
   <td>F</td>
   <td>Wenn „true“, werden Anhänge angezeigt.<br /> </td>
  </tr>
  <tr>
   <td>isStartTask<br /> </td>
   <td>F</td>
   <td>Wenn „true“, wird die Aufgabe vom Startpunkt aus erstellt.<br /> </td>
  </tr>
  <tr>
   <td>isVisible<br /> </td>
   <td>F</td>
   <td>„True“, wenn die Aufgabe im Arbeitsbereich sichtbar ist.<br /> </td>
  </tr>
  <tr>
   <td>nextReminder<br /> </td>
   <td>F</td>
   <td>Zeitstempel für die nächste Erinnerung.<br /> </td>
  </tr>
  <tr>
   <td>priority<br /> </td>
   <td>F</td>
   <td>Enthält die Priorität der Aufgabe.<br /> 1 = höchste Priorität<br /> 2 = Hohe Priorität<br /> 3 = Mittlere Priorität<br /> 4 = Niedrige Priorität<br /> 5 = Niedrigste Priorität<br />  </td>
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
   <td>Enthält die Anzahl der Erinnerungen für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>routeList<br /> </td>
   <td>F</td>
   <td>Enthält eine Liste der mit der Aufgabe verbundenen Routen.  Benutzende können die Aufgabe abschließen, indem sie eine Route aus der Liste der Routen auswählen.<br /> </td>
  </tr>
  <tr>
   <td>selectedRoute<br /> </td>
   <td>F</td>
   <td>Enthält den Namen der Route, die beim Abschließen der Aufgabe ausgewählt wurde.<br /> </td>
  </tr>
  <tr>
   <td>serializedImageTicket<br /> </td>
   <td>F</td>
   <td>Enthält das Bild-Ticket, das der Aufgabe entspricht. Dieses Bild-Ticket wird im imageUrl-Feld der Aufgabe verwendet, um vom Server ein Bild für die Aufgabe zu erhalten.<br /> <br /> </td>
  </tr>
  <tr>
   <td>serviceName<br /> </td>
   <td>F</td>
   <td>Enthält den Namen des Dienstes für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>serviceTitel<br /> </td>
   <td>F</td>
   <td>Enthält den Titel des Dienstes für die Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>status<br /> </td>
   <td>F</td>
   <td>1 = Erstellt (Aufgabe wird vom Startpunkt erstellt.)<br />2 = Erstellt und gespeichert (Aufgabe wird vom Startpunkt erstellt und gespeichert.)<br />3 = Zugewiesen (Aufgabe wird der Person zugewiesen, nachdem der Prozess gestartet wurde.)<br />4 = Zugewiesen und gespeichert (Aufgabe wird zugewiesen und gespeichert.)<br />100 = Abgeschlossen (Aufgabe wird abgeschlossen.)<br />101 = Termin erreicht (Aufgabe hat den Termin erreicht.)<br />102 = Beendet<br /> </td>
  </tr>
  <tr>
   <td>stepName<br /> </td>
   <td>F</td>
   <td>Enthält den Namen der Aufgabe, die während der Entwicklung des Prozesses festgelegt wurde.<br /> </td>
  </tr>
  <tr>
   <td>summaryUrl<br /> </td>
   <td>F</td>
   <td>Enthält die Aufgabenzusammenfassungs-URL.<br /> </td>
  </tr>
  <tr>
   <td>taskACL<br /> </td>
   <td>F</td>
   <td>Die Zugriffssteuerungsliste für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskId<br /> </td>
   <td>F</td>
   <td>Die ID einer Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>updateTime<br /> </td>
   <td>F</td>
   <td>Der Zeitstempel der letzten Aufgabenaktualisierung.<br /> </td>
  </tr>
  <tr>
   <td>formUrl<br /> </td>
   <td>T</td>
   <td>Enthält die URL des Formulars für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>taskFormType<br /> </td>
   <td>T</td>
   <td>Enthält den Formulartyp der Aufgabe. Wenn dieses Feld verwendet wird, wird die Aufgabe auf dem Client als PDF-Formular, SWF-Formular usw. gerendert.<br /> </td>
  </tr>
  <tr>
   <td>showDirectActions<br /> </td>
   <td>T</td>
   <td>Wenn „true“, sind Route-Aktionen in Workspace sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>showACLActions<br /> </td>
   <td>T</td>
   <td>Wenn „true“, sind Aktionen wie Weiterleiten, Beraten und Freigeben in Workspace sichtbar.<br /> </td>
  </tr>
  <tr>
   <td>supportsOffline<br /> </td>
   <td>T</td>
   <td>Wenn „true“, kann das Formular offline verwendet werden. Dies gilt nur für PDF-Formulare.<br /> </td>
  </tr>
  <tr>
   <td>supportsSave<br /> </td>
   <td>T</td>
   <td>Wenn „true“, können Benutzende die Aufgabe speichern.<br /> </td>
  </tr>
  <tr>
   <td>readerSubmitOptions<br /> </td>
   <td>T</td>
   <td>Dieses Objekt enthält Optionen, die verwendet werden, um PDF-Formulare über den Reader zu senden, wenn das PDF-Formular keine Schaltfläche zum Senden enthält.<br /> </td>
  </tr>
  <tr>
   <td>isDefaultImage<br /> </td>
   <td>T</td>
   <td>Gibt an, ob für den Prozess ein Bild angegeben wurde oder nicht. „true“, wenn kein Bild mit dem Prozess verknüpft ist, andernfalls „false“.<br /> </td>
  </tr>
  <tr>
   <td>historyTaskList<br /> </td>
   <td>T</td>
   <td>Enthält eine Liste von Aufgaben, die auf der Verlaufsregisterkarte der Aufgabendetails verwendet werden.<br /> </td>
  </tr>
  <tr>
   <td>isOwner<br /> </td>
   <td>T</td>
   <td>„true“, wenn die angemeldete Person für die Aufgabe verantwortlich ist.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands<br /> </td>
   <td>T</td>
   <td>Enthält alle Aktionen, die für eine Aufgabe ausgeführt werden können.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.directCommands<br /> </td>
   <td>T</td>
   <td>Enthält alle Route-Aktionen, die für eine Aufgabe verfügbar sind.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.taskACLCommands<br /> </td>
   <td>T</td>
   <td>Enthält Befehle wie „Weiterleiten“, „Freigeben“ und „Besprechen“, wenn sie für eine Aufgabe verfügbar sind.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.otherCommands<br /> </td>
   <td>T</td>
   <td>Enthält Befehle wie „Sperren“, „Sperre aufheben“, „Abbrechen“, „Zurückgeben“ und „Anfordern“ usw.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceInfo<br /> </td>
   <td>T</td>
   <td>Enthält Informationen über die Prozessinstanz der Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>processVariables<br /> </td>
   <td>T<br /> </td>
   <td>Enthält ein Array von Objekten aus Prozessvariablen, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>pendingTasks<br /> </td>
   <td>T</td>
   <td>Enthält eine Liste der ausstehenden Aufgaben für die Aufgabenprozessinstanz.<br /> </td>
  </tr>
  <tr>
   <td>userActions<br /> </td>
   <td>T</td>
   <td>Ein Array von Objekten. Jedes Objekt enthält Informationen über eine Route und die entsprechende Bestätigungsmeldung, sofern vorhanden.<br /> </td>
  </tr>
  <tr>
   <td>dataUrl<br /> </td>
   <td>T</td>
   <td>Die URL für die Daten eines Aufgabenformulars.<br /> </td>
  </tr>
  <tr>
   <td>externalAppConfig<br /> </td>
   <td>T</td>
   <td>Dies ist die Konfiguration für Anwendungsformulare von Drittanbietern.<br /> </td>
  </tr>
  <tr>
   <td>submitted<br /> </td>
   <td>T</td>
   <td>„True“, wenn die Aufgabe übermittelt wird.<br /> </td>
  </tr>
  <tr>
   <td>attachments<br /> </td>
   <td>T</td>
   <td>Liste der Anhänge für eine Aufgabe.<br /> </td>
  </tr>
  <tr>
   <td>assignments<br /> </td>
   <td>T</td>
   <td>Liste der Zuweisungen einer Aufgabe.<br /> </td>
  </tr>
 </tbody>
</table>

1. Filter

   „Filter“ ist im Grunde eine Warteschlange von Benutzenden oder Gruppen. Wenn eine Aufgabe einer Person oder einer Gruppe zugewiesen wird, wird die Aufgabe zur entsprechenden Warteschlange hinzugefügt.

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
   <td>„True“, wenn die Warteschlange die Standardwarteschlange der angemeldeten Person ist, sonst „false“.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>name<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der Inhaberin oder des Inhabers der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>qid</td>
   <td>F</td>
   <td>ID der Warteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Typ</td>
   <td>F</td>
   <td>Enthält den Typ der Warteschlange.<br />0 – Benutzerwarteschlange.<br /> 1. Freigegebene Warteschlange.<br /> 2. Gruppenwarteschlange.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>query</td>
   <td>T</td>
   <td>Enthält eine Abfrage, die einem Filter zugeordnet ist.  Diese Abfrage wird verwendet, um Aufgaben aus der vollständigen Aufgabenliste zu durchsuchen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>tasks</td>
   <td>T</td>
   <td>Enthält eine Liste aller Aufgaben, die zu einem Filter gehören.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Out-of-Office

   Sie können Ihren Abwesenheitsplan verwalten und den Ablauf der Ihnen zugewiesenen Aufgaben während Ihrer Abwesenheit steuern.

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
   <td>Enthält Array-Objekte von Abwesenheitsplänen von Benutzenden. In jedem Zeitplanobjekt enthält das Feld startDate das Startdatum des Zeitplans und endDate das Enddatum des Zeitplans. Wenn im Zeitplan das Feld endDate den Wert Null enthält, bedeutet dies, dass der Benutzer das Enddatum des Abwesenheitszeitplans nicht geplant hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isNoPrimaryDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>„True“, wenn es keine primären Beauftragten gibt, falls die Person nicht im Büro ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>„True“, wenn die Person nicht im Büro ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>Enthält Details zur Person, die als primär Beauftragte zugewiesen wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processSpecificDesignates<br type="_moz" /> </td>
   <td>F</td>
   <td>Enthält eine Reihe von Objekten für prozessspezifische Abwesenheitsnotizen.  In jedem prozessspezifischen designierten Objekt enthält processName den Namen des Prozesses; isNotDesignated hat den Wert „true“, wenn dem entsprechenden Prozess kein Benutzer zugeordnet ist; userDesignated hat den Wert Null, wenn kein Benutzer Details dem Benutzer zugeordnet hat, der für den entsprechenden Vorgang vorgesehen war.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processes<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält eine Liste aller Prozesse, die der Person stehen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält anfängliche Abwesenheitseinstellungen der Person, die zunächst abgerufen werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält geänderte Abwesenheitseinstellungen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userSearchHistory<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält eine Liste der Benutzenden, die von einer angemeldeten Person bis zum Datum gesucht wurden.<br type="_moz" /> </td>
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
   <td>initiator</td>
   <td>F</td>
   <td>Name der Initiatorin bzw. des Initiators einer Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>F</td>
   <td>ID der Initiatorin bzw. des Initiators der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processCompleteTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel, wenn der Prozess abgeschlossen ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Prozessinstanz.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Initiiert<br /> 1 = Wird ausgeführt<br /> 2 = Abgeschlossen<br /> 3 = Wird abgeschlossen<br /> 4 = Beendet<br /> 5 = Wird beendet<br /> 6 = Ausgesetzt<br /> 7 = Wird ausgesetzt<br /> 8 = Aussetzung wird aufgehoben<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Prozesses.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processStartTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel des Prozessstarts.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processVariables<br type="_moz" /> </td>
   <td>F</td>
   <td>Array von Objekten aus Prozessvariablen. Jedes Objekt einer Prozessvariable enthält name, den Namen der Prozessvariable, value, den Wert der Prozessvariable und type, den Typ der Prozessvariable.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>tasklist<br type="_moz" /> </td>
   <td>T</td>
   <td>Von dieser Prozessinstanz generierte Aufgaben.<br type="_moz" /> </td>
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
   <td>0 = Erste Zuweisung<br /> 1 = Weiterleiten (Aufgabe wurde an die aktuell für die Aufgabe verantwortliche Person weitergeleitet.)<br />2 = Zurückgegeben (Die zuvor für die Aufgabe verantwortliche Person hat die Aufgabe der aktuell für die Aufgabe verantwortlichen Person zurückgegeben.)<br />3 = Angefordert (Aufgabe wurde von der aktuell für die Aufgabe verantwortlichen Person angefordert.)<br />4 = Eskalation (Aufgabe wurde nach der Eskalation der aktuell für die Aufgabe verantwortlichen Person zugewiesen.)<br />5 = Administratorseitig zugewiesen (Admin hat die Aufgabe der aktuell für die Aufgabe verantwortlichen Person zugewiesen.)<br />6 = Besprechen (Aufgabe wurde der aktuell für die Aufgabe verantwortlichen Person zum Besprechen zugewiesen.)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignmentUpdateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Zeitstempel, wenn diese Zuweisung einer Aufgabe aktualisiert wird.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Warteschlange der aktuellen Inhaberin bzw. des aktuellen Inhabers der Aufgabe.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwner<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der aktuellen Inhaberin bzw. des aktuellen Inhabers der Aufgabe.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwnerId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der aktuellen Inhaberin bzw. des aktuellen Inhabers der Aufgabe.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Aufgaben-ACL-Objekt

   Das Aufgaben-ACL-Objekt enthält Informationen zu Berechtigungen wie Weiterleiten, Freigeben und Konsultieren einer Aufgabe. Im Folgenden sind die Eigenschaften der ACL der Aufgabe aufgeführt.

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
   <td>Wenn „true“, können Anhänge zur Aufgabe hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canAddNotes<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, können der Aufgabe Anmerkungen hinzugefügt werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canClaim<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“ kann die Aufgabe beansprucht werden.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canConsult<br type="_moz" /> </td>
   <td>F</td>
   <td>Wenn „true“, kann die Aufgabe konsultiert werden.<br type="_moz" /> </td>
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

1. Aufgabenanhang

   Einer Aufgabe können Anhänge hinzugefügt werden.  Der Anhang kann vom Typ „Anhang“ und „Anmerkung“ sein. Im Folgenden sind die Eigenschaften des Anhangsobjekts aufgeführt.

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
   <td>Zeitstempel, wann der Anhang erstellt wurde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorId<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Person, die den Anhang hinzugefügt hat.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorName<br type="_moz" /> </td>
   <td>F</td>
   <td>Name der Person, die den Anhang hinzugefügt hat.<br type="_moz" /> </td>
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
   <td>Wenn „true“, ist die Anmerkung eine erweiterte (lange) Anmerkung.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Berechtigungen<br type="_moz" /> </td>
   <td>F</td>
   <td>Berechtigungen, die mit einer Anlage verknüpft sind. Das Feld allowRead steht für die Leseberechtigung; allowWrite steht für die Schreibberechtigung, allowDelete steht für die Berechtigung zum Löschen.<br type="_moz" /> </td>
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
   <td>Typ<br type="_moz" /> </td>
   <td>F</td>
   <td>Der Typ ist „attachment“ für Dateien und „note“ für Anmerkungen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedCreationDate<br type="_moz" /> </td>
   <td>T</td>
   <td>Enthält das Erstellungsdatum der Anlage, entsprechend den Benutzeroberflächeneinstellungen der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedDescription<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierte Anlagenbeschreibung. Wird verwendet, um Sonderzeichen in der Anlagenbeschreibung in AEM Forms Workspace anzuzeigen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedFileName<br type="_moz" /> </td>
   <td>T</td>
   <td>Formatierter Anlagenname. Wird verwendet, um Sonderzeichen im Anlagennamen in AEM Forms Workspace anzuzeigen. Dies ist nur für Anmerkungen verfügbar.<br type="_moz" /> </td>
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
   <td>address<br type="_moz" /> </td>
   <td>F</td>
   <td>Adresse der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>commonName<br type="_moz" /> </td>
   <td>F</td>
   <td>Allgemeiner Name der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschreibung der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>directGroupMemberships<br type="_moz" /> </td>
   <td>F</td>
   <td>Liste der Gruppe der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>displayName<br type="_moz" /> </td>
   <td>F</td>
   <td>Anzeigename der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>email<br type="_moz" /> </td>
   <td>F</td>
   <td>E-Mail-ID der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>„True“, wenn die Person nicht im Büro ist.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastName<br type="_moz" /> </td>
   <td>F</td>
   <td>Nachname der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>firstName<br type="_moz" /> </td>
   <td>F</td>
   <td>Vorname der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>oid<br type="_moz" /> </td>
   <td>F</td>
   <td>ID der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>org<br type="_moz" /> </td>
   <td>F</td>
   <td>Name des Unternehmens der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>postalAddress<br type="_moz" /> </td>
   <td>F</td>
   <td>Postanschrift der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>telephone<br type="_moz" /> </td>
   <td>F</td>
   <td>Kontaktnummer der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>telephoneNumber<br type="_moz" /> </td>
   <td>F</td>
   <td>Kontaktnummer der Person.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userid<br type="_moz" /> </td>
   <td>F</td>
   <td>Anmelde-ID der Person.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>
