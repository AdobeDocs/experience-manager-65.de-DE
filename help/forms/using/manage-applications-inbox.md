---
title: Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang
seo-title: Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang
description: Mit dem AEM-Posteingang können Sie formularzentrierte Workflows starten, indem Sie Anwendungen senden und Aufgaben verwalten.
seo-description: Mit dem AEM-Posteingang können Sie formularzentrierte Workflows starten, indem Sie Anwendungen senden und Aufgaben verwalten.
uuid: c6c0d8ea-743f-4852-99d1-69fd50a0994e
contentOwner: vishgupt
topic-tags: document_services, publish
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dd11fd83-3df1-4727-8340-8c5426812823
docset: aem65
exl-id: 8d17194b-8baf-4878-b3ae-d351a056aebf
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 70%

---

# Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang{#manage-forms-applications-and-tasks-in-aem-inbox}

Zu den vielen Möglichkeiten, einen formularzentrierten Workflow zu starten oder auszulösen, gehören Anwendungen im AEM-Posteingang. Sie müssen eine Workflow-Anwendung erstellen, um einen Forms-Workflow als Anwendung im Posteingang verfügbar zu machen. Weitere Informationen zur Workflow-Anwendung und anderen Möglichkeiten zum Starten von Forms-Workflows finden Sie unter [Starten eines Forms-zentrierten Workflows unter OSGi](../../forms/using/aem-forms-workflow.md#launch).

Darüber hinaus führt der AEM-Posteingang Benachrichtigungen und Aufgaben aus verschiedenen AEM-Komponenten einschließlich Forms-Workflows zusammen. Wenn ein Forms-Workflow ausgelöst wird, der einen Schritt zur Zuweisung einer Aufgabe enthält, wird die dazugehörige Anwendung als Aufgabe im Posteingang der zugewiesenen Person angezeigt. Wenn der Empfänger eine Gruppe ist, wird die Aufgabe im Posteingang aller Gruppenmitglieder angezeigt, bis eine Person die Aufgabe beansprucht oder delegiert.

In der Benutzeroberfläche des Posteingangs können die Aufgaben in einer Listen- oder einer Kalenderansicht angezeigt werden. Sie können außerdem die Einstellungen für die Anzeige konfigurieren. Sie können die Aufgaben nach verschiedenen Parametern filtern. Weitere Informationen zu Ansicht und Filtern finden Sie unter [Ihr Posteingang](/help/sites-authoring/inbox.md).

Kurz zusammengefasst: Mit dem Posteingang können Sie neue Anwendungen erstellen und zugewiesene Aufgaben verwalten.

>[!NOTE]
>
>Damit Sie den AEM-Posteingang verwenden können, müssen Sie der Gruppe „workflow-users“ angehören.

## Anwendung erstellen {#create-application}

1. Gehen Sie zum AEM Posteingang unter https://&#39;[server]:[port]&#39;/aem/inbox.
1. Tippen Sie in der Benutzeroberfläche des Posteingangs auf **[!UICONTROL Erstellen > Anwendung]**. Die Seite Anwendung auswählen wird angezeigt.
1. Wählen Sie eine Anwendung aus und klicken Sie auf **[!UICONTROL Erstellen]**. Das mit der Anwendung verknüpfte adaptive Formular wird geöffnet. Füllen Sie die Informationen im adaptiven Formular aus und tippen Sie auf **[!UICONTROL Senden]**. Der dazugehörige Workflow wird gestartet und erstellt eine Aufgabe im Posteingang des Empfängers.

## Aufgaben verwalten {#manage-tasks}

Wenn ein Forms-Workflow ausgelöst wird und Sie der Empfänger sind oder einer Empfängergruppe angehören, wird eine Aufgabe in Ihrem Posteingang angezeigt. Sie können im Posteingang Aufgabendetails anzeigen und verfügbare Aktionen für die Aufgabe ausführen.

### Aufgaben annehmen oder delegieren  {#claim-or-delegate-tasks}

Aufgaben, die einer Gruppe zugewiesen sind, werden im Posteingang aller Gruppenmitglieder angezeigt. Jedes Gruppenmitglied kann diese Aufgabe annehmen oder an ein anderes Gruppenmitglied delegieren. Gehen Sie dazu wie folgt vor:

1. Tippen Sie auf die Miniaturansicht der Aufgabe, um sie auszuwählen. Optionen zum Öffnen oder Delegieren der Aufgabe werden oben angezeigt.

   ![select-task](assets/select-task.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Aufgabe delegieren, tippen Sie auf **[!UICONTROL Delegieren]**. Das Dialogfeld „Element delegieren“ wird geöffnet. Wählen Sie einen Benutzer aus, fügen Sie optional einen Kommentar ein und tippen Sie auf **[!UICONTROL OK]**.

   ![delegate](assets/delegate.png)

   * Um die Aufgabe anzunehmen, tippen Sie auf **[!UICONTROL Öffnen]**. Das Dialogfeld „Selbst zuweisen“ wird geöffnet. Tippen Sie auf **[!UICONTROL Fortfahren]**, um die Aufgabe anzunehmen. Die angenommene Aufgabe wird mit Ihnen als Empfänger in Ihrem Posteingang angezeigt.

   ![claim](assets/claim.png)

### Aufgabendetails anzeigen und Aktionen für Aufgaben durchführen {#view-details-and-perform-actions-on-tasks}

Wenn Sie eine Aufgabe öffnen, können Sie Aufgabendetails anzeigen und verfügbare Aktionen durchführen. Die für eine Aufgabe verfügbaren Aktionen werden im Schritt „Aufgabe zuweisen“ des dazugehörigen Forms-Workflows definiert.

1. Tippen Sie auf die Miniaturansicht der Aufgabe, um sie auszuwählen. Optionen zum Öffnen oder Delegieren der ausgewählten Aufgabe werden oben angezeigt.
1. Tippen Sie auf **Öffnen**, um die Aufgabendetails anzuzeigen und Aktionen auszuführen. Die detaillierte Aufgabenansicht wird geöffnet. In dieser Ansicht können Sie Aufgabendetails anzeigen und verfügbare Aktionen für die Aufgabe ausführen.

   >[!NOTE]
   >
   >Wenn eine Aufgabe einer Gruppe zugewiesen ist, müssen Sie sie annehmen, damit Sie sie in der detaillierten Ansicht anzeigen können.

![Aufgabendetails](assets/task-details.png)

Die detaillierte Aufgabenansicht umfasst die folgenden Abschnitte:

* Aufgabendetails
* Formular- 
* Workflow-Details
* Aktionssymbolleiste

#### Aufgabendetails {#task-details}

Der Abschnitt „Aufgabendetails“ zeigt Informationen zur Aufgabe an. Die angezeigten Informationen hängen von den Konfigurationseinstellungen des Schritts [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) im Workflow ab. Das Beispiel oben zeigt die Beschreibung, den Status, das Startdatum und den verwendeten Workflow für die Aufgabe an. Es ist außerdem möglich, Dateien an Aufgaben anzuhängen.

#### Formular-  {#form}

Auf der Registerkarte „Formular“ im Hauptinhaltsbereich werden das übermittelte Formular und gegebenenfalls Anhänge für einzelne Felder angezeigt.

#### Workflow-Details {#workflow-details}

Die Registerkarte „Workflow-Details“ oben zeigt den Fortschritt der Aufgabe in verschiedenen Phasen des Workflows an. Sie zeigt abgeschlossene, aktuelle und ausstehende Phasen der Aufgabe. Die Phasen eines Workflows werden im Schritt [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) des zugehörigen Workflows definiert.

Darüber hinaus wird auf der Registerkarte der Aufgabenverlauf für jede abgeschlossene Phase im Workflow angezeigt. Sie können auf **[!UICONTROL Details anzeigen]** für eine abgeschlossene Phase tippen, um Details zu dieser Phase anzuzeigen. Dies zeigt Kommentare, Formular- und Aufgabenanhänge, Status, Start- und Enddatum usw. für die Aufgabe an.

![workflow-details](assets/workflow-details.png)

#### Aktionssymbolleiste {#actions-toolbar}

Die Aktionssymbolleiste zeigt alle verfügbaren Optionen für die Aufgabe. Speichern, Zurücksetzen und Delegieren sind Standardaktionen, andere verfügbare Aktionen werden dagegen im Schritt [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) konfiguriert. Im obigen Beispiel sind „Genehmigen“ und „Ablehnen“ im Workflow konfiguriert.

Wenn Sie eine Aktion für die Aufgabe ausführen, wird diese im Workflow weitergeleitet.

### Abgeschlossene Aufgaben anzeigen  {#view-completed-tasks}

Im AEM-Posteingang werden nur aktive Aufgaben angezeigt. Abgeschlossene Aufgaben werden nicht in der Liste aufgeführt. Sie können jedoch mithilfe von Posteingangsfiltern Aufgaben basierend auf verschiedenen Parametern filtern, z. B. Aufgabentyp, Status, Start- und Enddatum usw. Abgeschlossene Aufgaben anzeigen:

1. Tippen Sie in AEM Posteingang auf ![Umschalter-Seitenbereich1](assets/toggle-side-panel1.png) , um die Filterauswahl zu öffnen.
1. Tippen Sie auf das Akkordion **[!UICONTROL Aufgabenstatus]** und wählen Sie **[!UICONTROL Abgeschlossen]**. Alle Ihre abgeschlossenen Aufgaben werden angezeigt.

   ![filter](assets/filter.png)

1. Wählen Sie eine Aufgabe und klicken Sie auf **[!UICONTROL Öffnen]**.

Die Aufgabe wird geöffnet und das dazugehörige Dokument oder adaptive Formular wird angezeigt. Bei adaptiven Formularen zeigt die Aufgabe das schreibgeschützte adaptive Formular oder das PDF-Datensatzdokument an, das auf der Registerkarte Formular/Dokument des [Workflow-Schritts &quot;Aufgabe zuweisen&quot;](/help/sites-developing/workflows-step-ref.md) konfiguriert wurde.

Im Abschnitt mit den Aufgabendetails werden Informationen wie die durchgeführte Aktion, der Aufgabenstatus, das Startdatum und das Enddatum angezeigt.

![completed-task](assets/completed-task.png)

Die Registerkarte **[!UICONTROL Workflow-Details]** zeigt jeden Schritt des Workflows an. Tippen Sie auf **[!UICONTROL Details anzeigen]** , um einen Schritt mit detaillierten Informationen anzuzeigen.

![completed-task-workflow](assets/completed-task-workflow.png)

## Fehlerbehebung {#troubleshooting-workflows}

### Elemente im Zusammenhang mit AEM Workflow können nicht in AEM Posteingang {#unable-to-see-aem-worklow-items} angezeigt werden.

Ein Eigentümer eines Workflow-Modells kann Elemente im Zusammenhang mit AEM Workflow in AEM Posteingang nicht anzeigen. Um das Problem zu beheben, fügen Sie die unten aufgeführten Indizes zu Ihrem AEM-Repository hinzu und erstellen Sie den Index neu.

1. Verwenden Sie eine der folgenden Methoden, um Indizes hinzuzufügen:

   * Erstellen Sie die folgenden Knoten in CRX DE unter `/oak:index/workflowDataLucene/indexRules/granite:InboxItem/properties` mit den entsprechenden Eigenschaften, wie in der folgenden Tabelle angegeben:

      | Node | Eigenschaft | Typ |
      |---|---|---|
      | sharedWith | sharedWith | ZEICHENFOLGE |
      | locked | locked | BOOLESCH |
      | zurückgegeben | zurückgegeben | BOOLESCH |
      | allowInboxSharing | allowInboxSharing | BOOLESCH |
      | allowExplicitSharing | allowExplicitSharing | BOOLESCH |


   * Stellen Sie die Indizes über ein AEM bereit. Sie können ein [AEM Archetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype)-Projekt verwenden, um ein bereitstellbares AEM-Paket zu erstellen. Verwenden Sie den folgenden Beispielcode, um einem AEM Archetyp-Projekt Indizes hinzuzufügen:

   ```Java
      .property("sharedWith", "sharedWith").type(TYPENAME_STRING).propertyIndex()
      .property("locked", "locked").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("returned", "returned").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowInboxSharing", "allowInboxSharing").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowExplicitSharing", "allowExplicitSharing").type(TYPENAME_BOOLEAN).propertyIndex()
   ```

1. [Erstellen Sie einen Eigenschaftsindex und legen Sie ihn auf &quot;true&quot;](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/queries-and-indexing.html#the-property-index) fest.

1. Nachdem Sie Indizes in CRX DE konfiguriert oder über ein Paket bereitgestellt haben, indizieren Sie [das Repository](https://helpx.adobe.com/in/experience-manager/kb/HowToCheckLuceneIndex.html#Completelyrebuildtheindex) erneut.

https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/queries-and-indexing.html
