---
title: Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang
seo-title: Manage Forms applications and tasks in AEM Inbox
description: Mit dem AEM-Posteingang können Sie formularzentrierte Workflows starten, indem Sie Anwendungen senden und Aufgaben verwalten.
seo-description: AEM Inbox allows you to launch Forms-centric workflows through submitting applications and manage tasks.
uuid: c6c0d8ea-743f-4852-99d1-69fd50a0994e
contentOwner: vishgupt
topic-tags: document_services, publish
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dd11fd83-3df1-4727-8340-8c5426812823
docset: aem65
exl-id: 8d17194b-8baf-4878-b3ae-d351a056aebf
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 47%

---

# Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang {#manage-forms-applications-and-tasks-in-aem-inbox}

Eine der vielen Möglichkeiten, einen Forms-orientierten Workflow zu starten oder Trigger, besteht darin, Anwendungen in AEM Posteingang zu verwenden. Um einen Forms-Workflow als Anwendung im Posteingang verfügbar zu machen, erstellen Sie eine Workflow-Anwendung. Weitere Informationen zu Workflow-Anwendungen und anderen Möglichkeiten zum Starten von Forms-Workflows finden Sie unter [Starten eines formularzentrierten Workflow auf OSGi](../../forms/using/aem-forms-workflow.md#launch).

Darüber hinaus konsolidiert AEM Posteingang Benachrichtigungen und Aufgaben aus verschiedenen AEM Komponenten, einschließlich Forms-Workflows. Wenn ein Arbeitsablauf für Formulare ausgelöst wird, der einen Schritt &quot;Aufgabe zuweisen&quot;enthält, wird die zugehörige Anwendung als Aufgabe im Posteingang des Empfängers aufgeführt. Wenn der Bevollmächtigte eine Gruppe ist, wird die Aufgabe im Posteingang aller Gruppenmitglieder angezeigt, bis eine Person die Aufgabe beansprucht oder delegiert.

Die Benutzeroberfläche des Posteingangs bietet Listen- und Kalenderansichten zum Anzeigen von Aufgaben. Sie können auch die Anzeigeeinstellungen konfigurieren. Sie können Aufgaben anhand verschiedener Parameter filtern. Weitere Informationen zum Anzeigen und Filtern finden Sie unter [Ihr Posteingang](/help/sites-authoring/inbox.md).

Kurz zusammengefasst: Mit dem Posteingang können Sie neue Anwendungen erstellen und zugewiesene Aufgaben verwalten.

>[!NOTE]
>
>Sie müssen Mitglied der Gruppe &quot;workflow-users&quot;sein, um AEM Posteingang verwenden zu können.

## Anwendung erstellen {#create-application}

1. Wechseln Sie zum AEM-Posteingang unter https://&#39;[server]:[port]&#39;/aem/inbox.
1. Tippen Sie in der Benutzeroberfläche des Posteingangs auf **[!UICONTROL Erstellen > Programm]**. Die Seite „Programm auswählen“ wird angezeigt.
1. Wählen Sie ein Programm aus und klicken Sie auf **[!UICONTROL Erstellen]**. Das zu dem Programm gehörige adaptive Formular wird geöffnet. Füllen Sie die Informationen im adaptiven Formular aus und tippen Sie auf **[!UICONTROL Senden]**. Der dazugehörige Workflow wird gestartet und erstellt eine Aufgabe im Posteingang des Empfängers.

## Aufgaben verwalten {#manage-tasks}

Wenn ein Forms-Workflow-Trigger und Sie ein Bevollmächtigter oder eine Gruppe von Bevollmächtigten sind, wird eine Aufgabe in Ihrem Posteingang angezeigt. Sie können Aufgabendetails anzeigen und verfügbare Aktionen für die Aufgabe im Posteingang durchführen.

### Aufgaben annehmen oder delegieren {#claim-or-delegate-tasks}

Aufgaben, die einer Gruppe zugewiesen sind, werden im Posteingang aller Gruppenmitglieder angezeigt. Jedes Gruppenmitglied kann diese Aufgabe anfordern oder an ein anderes Gruppenmitglied delegieren. Gehen Sie dazu wie folgt vor:

1. Tippen Sie, um die Miniaturansicht der Aufgabe auszuwählen. Optionen zum Öffnen oder Delegieren der Aufgabe werden oben angezeigt.

   ![select-task](assets/select-task.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Aufgabe zuzuweisen, tippen Sie auf **[!UICONTROL Delegieren]**. Das Dialogfeld Element delegieren wird geöffnet. Wählen Sie einen Benutzer aus, fügen Sie optional einen Kommentar ein und tippen Sie auf **[!UICONTROL OK]**.

   ![delegate](assets/delegate.png)

   * Um die Aufgabe anzufordern, tippen Sie auf **[!UICONTROL Öffnen]**. Das Dialogfeld &quot;Assign to Self&quot;wird geöffnet. Tippen Sie auf **[!UICONTROL Weiter]**, um die Aufgabe anzunehmen. Die angeforderte Aufgabe wird mit Ihnen als Verantwortlicher in Ihrem Posteingang angezeigt.

   ![claim](assets/claim.png)

### Aufgabendetails anzeigen und Aktionen für Aufgaben durchführen {#view-details-and-perform-actions-on-tasks}

Wenn Sie eine Aufgabe öffnen, können Sie Aufgabendetails anzeigen und verfügbare Aktionen ausführen. Die für eine Aufgabe verfügbaren Aktionen werden im Schritt Aufgabe zuweisen des zugehörigen Forms-Workflows definiert.

1. Tippen Sie, um die Miniaturansicht der Aufgabe auszuwählen. Die Optionen zum Öffnen oder Delegieren der ausgewählten Aufgabe werden oben angezeigt.
1. Tippen **Öffnen** , um Aufgabendetails anzuzeigen. Die detaillierte Aufgabenansicht wird geöffnet. In dieser Ansicht können Sie Aufgabendetails anzeigen und an der Aufgabe arbeiten.

   >[!NOTE]
   >
   >Wenn eine Aufgabe einer Gruppe zugewiesen ist, müssen Sie sie anfordern, um sie in der Detailansicht öffnen zu können.

![task-details](assets/task-details.png)

Die detaillierte Aufgabenansicht umfasst die folgenden Abschnitte:

* Aufgabendetails
* Formular
* Workflow-Details
* Aktionssymbolleiste

#### Aufgabendetails {#task-details}

Der Abschnitt „Aufgabendetails“ zeigt Informationen zur Aufgabe an. Welche Informationen angezeigt werden, hängt von den Konfigurationseinstellungen aus dem Schritt [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) im Workflow ab.. Im obigen Beispiel werden die Beschreibung, der Status, das Startdatum und der Workflow angezeigt, die für die Aufgabe verwendet werden. Sie können auch eine Datei an die Aufgabe anhängen.

#### Formular {#form}

Auf der Registerkarte „Formular“ im Hauptinhaltsbereich werden das übermittelte Formular und gegebenenfalls Anhänge für einzelne Felder angezeigt.

#### Workflow-Details {#workflow-details}

Die Registerkarte Workflow-Details oben zeigt den Fortschritt der Aufgabe in verschiedenen Phasen des Workflows an. Es werden die abgeschlossenen, aktuellen und ausstehenden Phasen der Aufgabe angezeigt. Die Phasen für einen Workflow werden im Schritt [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) des dazugehörigen Workflows definiert.

Darüber hinaus zeigt die Registerkarte den Aufgabenverlauf für jede abgeschlossene Phase im Workflow an. Sie können auf **[!UICONTROL Details anzeigen]** für eine abgeschlossene Phase, um Details zu dieser Phase zu erfahren. Es werden Kommentare, Formular- und Aufgabenanlagen, Status, Start- und Enddaten usw. zu der Aufgabe angezeigt.

![workflow-details](assets/workflow-details.png)

#### Aktionssymbolleiste {#actions-toolbar}

In der Aktionssymbolleiste werden alle verfügbaren Optionen für die Aufgabe angezeigt. Während &quot;Speichern&quot;, &quot;Zurücksetzen&quot;und &quot;Delegieren&quot;Standardaktionen sind, werden andere verfügbare Aktionen in [Schritt &quot;Aufgabe zuweisen&quot;](/help/sites-developing/workflows-step-ref.md). Im obigen Beispiel werden Genehmigen und Ablehnen im Workflow konfiguriert.

Während Sie an der Aufgabe arbeiten, wird sie im Workflow weiter ausgeführt.

### Abgeschlossene Aufgaben anzeigen {#view-completed-tasks}

AEM Posteingang zeigt nur aktive Aufgaben an. Abgeschlossene Aufgaben werden nicht in der Liste angezeigt. Sie können jedoch Posteingangsfilter verwenden, um Aufgaben anhand verschiedener Parameter zu filtern, z. B. nach Aufgabentyp, Status sowie Start- und Enddatum. Abgeschlossene Aufgaben anzeigen:

1. Tippen Sie im AEM-Posteingang auf ![toggle-side-panel1](assets/toggle-side-panel1.png), um die Filterauswahl zu öffnen.
1. Tippen Sie auf das Akkordeon **[!UICONTROL Aufgabenstatus]** und wählen Sie **[!UICONTROL Fertig stellen]**. Alle abgeschlossenen Aufgaben werden angezeigt.

   ![filter](assets/filter.png)

1. Wählen Sie eine Aufgabe durch Tippen aus und klicken Sie auf **[!UICONTROL Öffnen]**.

Die Aufgabe wird geöffnet und das dazugehörige Dokument oder adaptive Formular wird angezeigt. Bei einem adaptiven Formular wird das schreibgeschützte adaptive Formular oder dessen PDF-Datensatzdokument wie auf der Registerkarte „Formular“/„Dokument“ des [Workflow-Schritts „Aufgabe zuweisen“](/help/sites-developing/workflows-step-ref.md) konfiguriert angezeigt.

Im Abschnitt mit den Aufgabendetails werden Informationen wie die durchgeführte Aktion, der Aufgabenstatus, das Startdatum und das Enddatum angezeigt.

![completed-task](assets/completed-task.png)

Auf der Registerkarte **[!UICONTROL Workflow-Details]** werden alle Schritte des Workflows angezeigt. Tippen Sie bei einem Schritt auf **[!UICONTROL Details anzeigen]**, um detaillierte Informationen zu erhalten.

![completed-task-workflow](assets/completed-task-workflow.png)

## Fehlerbehebung {#troubleshooting-workflows}

### Elemente eines AEM-Workflows im AEM-Posteingang werden nicht angezeigt {#unable-to-see-aem-worklow-items}

Dem Eigentümer eines Workflow-Modells können die Elemente eines AEM-Workflows im AEM-Posteingang nicht angezeigt werden. Um das Problem zu beheben, fügen Sie die unten aufgeführten Indizes zu Ihrem AEM-Repository hinzu und erstellen Sie den Index neu.

1. Verwenden Sie eine der folgenden Methoden, um Indizes hinzuzufügen:

   * Erstellen Sie die folgenden Knoten in CRX DE bei `/oak:index/workflowDataLucene/indexRules/granite:InboxItem/properties` mit den entsprechenden Eigenschaften, die in folgender Tabelle angegeben sind:

      | Knoten | Eigenschaft | Typ |
      |---|---|---|
      | sharedWith | sharedWith | ZEICHENFOLGE |
      | locked | locked | BOOLESCH |
      | returned | returned | BOOLESCH |
      | allowInboxSharing | allowInboxSharing | BOOLESCH |
      | allowExplicitSharing | allowExplicitSharing | BOOLESCH |


   * Stellen Sie die Indizes über ein AEM-Paket bereit. Sie können ein implementierbares AEM-Paket mithilfe eines [AEM-Archteyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de)-Projekts erstellen. Verwenden Sie den folgenden Beispiel-Code, um einem AEM-Archetyp-Projekt Indizes hinzuzufügen:

   ```Java
      .property("sharedWith", "sharedWith").type(TYPENAME_STRING).propertyIndex()
      .property("locked", "locked").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("returned", "returned").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowInboxSharing", "allowInboxSharing").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowExplicitSharing", "allowExplicitSharing").type(TYPENAME_BOOLEAN).propertyIndex()
   ```

1. [Erstellen Sie einen Eigenschaftsindex und weisen Sie ihm „true“ zu](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=de#the-property-index).

1. Nachdem Sie Indizes in CRX DE konfiguriert oder über ein Paket bereitgestellt haben, indizieren Sie das Repository [erneut.](https://helpx.adobe.com/de/experience-manager/kb/HowToCheckLuceneIndex.html#Completelyrebuildtheindex)

https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=de
