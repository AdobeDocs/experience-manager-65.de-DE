---
title: Arbeiten mit Aufgabenlisten
description: Öffnen, Bearbeiten und Abschließen von Aufgaben nach Bedarf, beispielsweise Anfragen genehmigen bzw. ablehnen oder weitere Informationen hinzufügen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: c80bf347-d1ed-488f-a41a-ceb05a6df9e4
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '4024'
ht-degree: 100%

---

# Arbeiten mit Aufgabenlisten{#working-with-to-do-lists}

Beim Aufrufen Ihrer Aufgabenlisten sehen Sie möglicherweise Aufgaben aus einem Geschäftsprozess, die Ihnen oder Gruppen, denen Sie angehören, zugewiesen sind oder bei denen es sich um freigegebene Aufgaben von anderen Benutzenden handelt. Indem Sie beispielsweise eine Anforderung genehmigen bzw. ablehnen oder neue Informationen hinzufügen, können Sie die Aufgaben je nach Bedarf öffnen, bearbeiten oder abschließen. Wenn Sie eine Aufgabe abgeschlossen haben, wird sie an die nächste Person im Geschäftsprozess gesendet.

## Grundlegendes zu Aufgabenlisten {#about-todo-lists}

AEM Forms Workspace verfügt über die drei folgenden Typen von Aufgabenlisten:

* Persönliche Listen enthalten Aufgaben, die Ihnen direkt zugewiesen sind.
* Gruppenlisten enthalten Aufgaben, die einer Gruppe zugewiesen sind. Ein beliebiges Gruppenmitglied kann die Aufgaben öffnen und erledigen. Um eine Aufgabe zu öffnen, muss ein Mitglied einer Gruppe die Aufgabe zuerst anfordern.
* Freigegebene Listen enthalten Aufgaben, die einer Benutzerin oder einem Benutzer zugewiesen sind, die oder der die eigene Aufgabenliste für Sie und möglicherweise auch für andere Benutzende freigegeben hat. Alle Benutzenden, für die eine Liste freigegeben ist, können freigegebene Aufgaben anfordern, öffnen und erledigen.

Sie können bestimmte Aktionen durchführen, ohne die Aufgabe zu öffnen, indem Sie auf die Symbole klicken, die angezeigt werden, wenn Sie den Mauszeiger über eine Aufgabe bewegen.

>[!NOTE]
>
>Ein Ausrufezeichen zeigt an, dass die Aufgabe eine hohe Priorität hat.

## Typische Aufgaben {#typical-tasks}

Welche Werkzeuge Ihnen beim Öffnen und Bearbeiten von Aufgaben zur Verfügung stehen, hängt von der jeweiligen Aufgabe ab. Für unterschiedliche Aufgaben müssen Sie unterschiedliche Aktionen durchführen. Aus diesem Grund steht Ihnen eine entsprechende Auswahl von Werkzeuge zur Verfügung. Im Folgenden sind die typischen Aufgaben, die Sie möglicherweise erhalten, beschrieben.

* **Informationen bereitstellen**: Sie erhalten eine Aufgabe, bei der Sie ein Formular ausfüllen und übermitteln müssen.

* **Informationen überprüfen**: Sie erhalten eine Aufgabe, bei der Sie die Informationen überprüfen und den Inhalt abzeichnen müssen.

* **Überprüfung durch mehrere Benutzer**: Sie erhalten eine Aufgabe gleichzeitig mit anderen Benutzenden. Sie und die anderen Benutzer müssen Informationen eingeben, den Inhalt überprüfen oder beides. Für diesen Aufgabentyp stehen die folgenden Werkzeuge zur Verfügung:

   * Anzeigen der Aufgabenanweisungen
   * Anzeigen des Fertigstellungsstatus aller Benutzenden, denen die Aufgabe zugewiesen wurde
   * Anzeigen der Kommentare aller Benutzenden, denen die Aufgabe zugewiesen wurde
   * Hinzufügen eigener Kommentare zu der Aufgabe

Weitere Werkzeuge, die bei den oben angegebenen Aufgaben verfügbar sind:

* Weiterleiten
* Link freigeben
* Besprechen
* Zurückgeben
* Anmerkungen
* Anhänge

## Öffnen von Aufgaben {#opening-tasks}

Sie können Aufgaben aus Ihrer Aufgabenliste öffnen und sperren oder Aufgaben von einer Gruppenaufgabenliste bzw. einer freigegebenen Aufgabenliste anfordern und öffnen. Wenn Sie eine Aufgabe öffnen, wird diese im Hauptbereich angezeigt. Die anderen Aufgaben werden in der Vorgangsliste neben der Aufgabenliste angezeigt.

Wenn eine Aufgabenzusammenfassungs-URL vorhanden ist, wird standardmäßig die Ansicht „Aufgabenzusammenfassung“ statt des Formulars, das einer Aufgabe zugeordnet ist, geöffnet. Auch wenn eine Benutzerin oder ein Benutzer unter „Aufgabe zuweisen“ die Option zum Öffnen des Formulars im maximierten Modus aktiviert, wird das Formular nicht im maximierten Modus geöffnet.

>[!NOTE]
>
>Wenn Sie eine Aufgabe öffnen, wird das zugehörige Formular je nach Standardeinstellungen der Aufgabe in einer Vollbildansicht angezeigt.

### Öffnen und Sperren einer Aufgabe aus der Liste {#open-and-lock-a-task-from-your-list}

Wenn Sie eine Aufgabe aus Ihrer Aufgabenliste öffnen und Ihre Liste freigegeben ist, können Sie die Aufgabe sperren, um zu verhindern, dass sie von anderen Benutzenden bearbeitet wird, die Zugriff auf Ihre Liste haben.

1. Wählen Sie auf der Aufgabenseite im linken Bereich Ihre persönliche Aufgabenliste aus. Alle Ihre Aufgaben werden im mittleren Bereich angezeigt.

   >[!NOTE]
   >
   >Sie können die Aufgaben filtern, indem Sie den Prozesstyp innerhalb der Aufgabenliste auswählen. Sie können Ihre Aufgabenliste auswählen, um alle Aufgaben in der Liste erneut anzuzeigen.

1. Sperren Sie ggf. Ihre Aufgabe. Um eine Aufgabe zu sperren, klicken Sie auf das Symbol „Alle Optionen“ für die Aufgabe und wählen Sie „Sperren“ aus. Bewegen Sie den Zeiger über die Aufgabe, damit die Option verfügbar ist.

   >[!NOTE]
   >
   >Sie können eine Aufgabe auch auf jeder Registerkarte sperren oder entsperren, wenn die Aufgabe geöffnet ist.

   ![lock_task](assets/lock_task.png)

   Menü „Alle Optionen“ für eine Aufgabe

1. Öffnen Sie die Aufgabe, indem Sie darauf klicken.

### Öffnen und Anfordern einer Aufgabe aus einer freigegebenen Liste oder Gruppenliste {#open-and-claim-a-task-from-a-shared-or-group-list}

Wenn Sie eine Aufgabe von einer Gruppenliste oder freigegebenen Liste anfordern, wird die Aufgabe aus der Gruppenliste bzw. freigegebenen Liste in Ihre persönliche Aufgabenliste verschoben. Andere Benutzende mit Zugriff auf die Liste können die Aufgabe nicht bearbeiten.

1. Wählen Sie auf der Aufgabenseite im linken Bereich eine Gruppenaufgabenliste bzw. eine freigegebene Aufgabenliste aus. Alle Aufgaben werden im mittleren Bereich angezeigt.
1. Führen Sie einen der folgenden Schritte aus:

   * Um eine Aufgabe aus einer Gruppenaufgabenliste bzw. einer freigegebenen Aufgabenliste anzufordern, ohne sie zu öffnen, klicken Sie auf **Anfordern**, indem Sie den Zeiger über der Aufgabe bewegen. Wenn die Aufgabe geöffnet ist, ist alternativ die Schaltfläche „Anfordern“ in der Aktionsleiste unter dem Aufgabenfenster verfügbar. Beim Anfordern wird eine Aufgabe aus der Gruppenaufgabenliste bzw. freigegebenen Aufgabenliste in Ihre Liste verschoben.
   * Um eine Aufgabe aus einer Gruppenaufgabenliste bzw. einer freigegebenen Aufgabenliste anzufordern und zu öffnen, klicken Sie auf **Anfordern und öffnen**.

## Arbeiten mit Aufgaben {#working-with-tasks}

Nach dem Öffnen einer Aufgabe hängt es von der Aufgabe ab, welche Registerkarten im Hauptbereich angezeigt werden und welche Werkzeuge Ihnen zur Verfügung stehen. Die entsprechenden Registerkarten werden unten beschrieben:

* **Aufgabenzusammenfassung**: Wenn eine Aufgabe geöffnet wird, können Sie im Bereich „Aufgabenzusammenfassung“ Informationen zur Aufgabe, falls vorhanden, über eine URL anzeigen, die im Prozess im Schritt „Aufgabe zuweisen“ angegeben wurde. Mithilfe dieser Aufgabenzusammenfassung können zusätzliche und wichtige Informationen zu einer Aufgabe angezeigt werden, die für den Endbenutzer von AEM Forms Workspace nützlich sind. Diese Registerkarte ist nicht verfügbar, wenn die URL zur Aufgabenzusammenfassung nicht vorhanden ist.

* **Details**: Bietet einige Informationen zur aktuellen Aufgabe und zum Prozess, zu dem sie gehört.

* **Formular**: Zeigt das Formular an, das der Aufgabe zugeordnet ist. Formulare können in vielen verschiedenen Dateiformaten wie PDF, HTML, Guide und SWF vorliegen. Das Formular kann wie ein normales druckbares oder Web-basiertes Formular aussehen oder Sie durch eine Folge von Bedienfeldern im Assistentenformat führen, um Informationen zu erfassen.

* **Verlauf**: Listet die Aufgaben, die Teil der Prozessinstanz sind, sowie das zugeordnete Formular, die Zuweisungen und Anhänge für jede Aufgabe auf.

* **Anhänge**: Zeigt vorhandene Anhänge an, die der Aufgabe zugeordnet sind, und fügt ggf. Anhänge hinzu.

* **Anmerkungen**: Zeigt die vorhandenen Anmerkungen an, die der Aufgabe zugeordnet sind, und fügt ggf. Anmerkungen hinzu.

Die Werkzeuge, die Ihnen angezeigt werden, und die Aktionen, die sie ausführen können, wenn Sie an einer Aufgabe arbeiten, werden unten beschrieben.

### Weiterleiten, Freigeben oder Besprechen von Aufgaben {#forward-share-or-consult-on-a-task}

Sie können eine Aufgabe zusammen mit Notizen oder Anlagen an einen anderen Benutzer weiterleiten, die Aufgabe freigeben oder sie mit einem anderen Benutzer besprechen. Wenn Sie Änderungen an den Formulardaten vornehmen, die einer Aufgabe zugeordnet sind, müssen Sie das Formular als Entwurf speichern, bevor Sie die Aufgabe weiterleiten, freigeben oder besprechen. Anderenfalls wird die Aufgabe ohne das aktualisierte Formular gesendet. Nachdem Sie eine Aufgabe weitergeleitet und freigegeben haben, kann der Benutzer, der die Aufgabe empfangen hat, diese entweder anfordern und abschließen oder sie wieder an Sie übergeben. Wenn Sie sich bezüglich einer Aufgabe beraten haben, kann die Benutzerin oder der Benutzer diese nur an Sie zurückgeben.

1. Wenn Sie ein Formular ändern, das einer Aufgabe zugeordnet ist und das Sie behalten möchten, klicken Sie auf **Speichern**. Die Option „Speichern“ ist in der Aktionsleiste unten auf jeder Registerkarte verfügbar. Anderenfalls wird die Aufgabe ohne das aktualisierte Formular gesendet.

   >[!NOTE]
   >
   >Abhängig von der Aufgabe, an der Sie gerade arbeiten, steht für einige Formulare die Schaltfläche „Speichern“ nicht zur Verfügung.

1. Klicken Sie auf einer beliebigen Registerkarte auf eine der folgenden Schaltflächen:

   * **Weiterleiten**
   * **Link freigeben**
   * **Besprechen**

   >[!NOTE]
   >
   >Abhängig von der Aufgabe können Sie diese Aktionen ggf. auch über die Aufgabenliste durchführen, ohne die Aufgabe zu öffnen.

1. Suchen Sie im Popup-Dialogfenster den Namen der Benutzerin oder des Benutzers für die Weiterleitung, Freigabe oder Besprechung der Aufgabe und wählen Sie sie oder ihn aus.

### Zurückgeben von Aufgaben {#return-a-task}

1. Klicken Sie auf einer beliebigen Registerkarte auf **Zurückgeben**. Die Aufgabe wird wieder an die Aufgabenliste der Benutzerin oder des Benutzers zurückgegeben, die oder der die Aufgabe zuvor an Sie weitergeleitet, für Sie freigegeben oder mit Ihnen besprochen hat.

### Online-Schalten von Aufgaben {#take-a-task-offline}

Sie haben ggf. die Möglichkeit, eine Aufgabe offline zu bearbeiten und das entsprechende Formular später über Adobe® Reader®, Adobe® Acrobat® Professional oder Adobe® Acrobat® Standard zu übermitteln. Beim Senden des Formulars wird Ihr E-Mail-Client mit der entsprechenden Server-E-Mail-Adresse gestartet. Sie können das ausgefüllte Formular dann per E-Mail an den Server senden.

1. Klicken Sie auf einer beliebigen Registerkarte auf **Offline**.
1. Geben Sie einen Dateinamen an, unter dem Sie das Formular gespeichert werden soll, und klicken Sie dann auf **Speichern**. Das der Aufgabe zugeordnete Formular wird lokal gespeichert und die Aufgabe bleibt in Ihrer Aufgabenliste, bis das Formular übermittelt wird.

### Arbeiten mit Anhängen {#work-with-attachments}

Sie haben ggf. die Möglichkeit, Anhänge lokal hinzuzufügen, zu aktualisieren, zu löschen oder zu speichern

**Hinzufügen von Anhängen**

1. Klicken Sie auf der Registerkarte **Anhänge** auf **Durchsuchen**, um die anzufügende Datei auszuwählen.
1. Wählen Sie die **Berechtigungsebene** des Anhangs für andere Benutzende aus, die an dem Prozess beteiligt sind. Wenn Sie die **Leseberechtigung** aktivieren, können andere Benutzende die Datei lokal speichern. Wenn Sie eine der Bearbeitungsberechtigungen auswählen, können andere Benutzende auch eine neue Datei hochladen, um Ihren Anhang durch sie zu ersetzen.

   >[!NOTE]
   >
   >Sie können auch Kommentare mit Ihren Anhänge hinzufügen.

1. Klicken Sie auf **Hochladen**. Die Datei wird an das Formular angefügt.

**Anzeigen von Anhängen**

1. Klicken Sie auf der Registerkarte **Anhänge** auf den Dateinamen des Anhangs, der angezeigt werden soll.

**Lokales Speichern von Anhängen**

1. Klicken Sie auf einen Anhang, um ihn zu öffnen. Speichern Sie den geöffneten Anhang lokal.

**Aktualisieren von Anhängen**

1. Klicken Sie für den Anhang auf **Bearbeiten**. Wählen Sie die Datei aus, die den vorhandenen Anhang ersetzen soll, indem Sie auf **Durchsuchen** klicken.

**Löschen von Anhängen**

1. Klicken Sie für einen Anhang auf **Löschen**.

### Speichern Ihrer Arbeit ohne Abschließen der Aufgabe {#save-your-work-without-completing-the-task}

1. Wählen Sie auf einer beliebigen Registerkarte **Speichern** aus.

   Das Dialogfeld „Als Entwurf speichern“ wird angezeigt. Der Standardname des Entwurfs entspricht dem der Aufgabe aus der Aufgabenvorlage.

   ![saveasdraftdialog](assets/saveasdraftdialog.png)

   >[!NOTE]
   >
   >Sie können Workspace so konfigurieren, dass Informationen, die von einem Benutzer als Entwurf eingegeben wurden, von Zeit zu Zeit automatisch gespeichert werden. Wenn die automatische Speicherung aktiviert ist und ein Benutzer an einem Entwurf arbeitet, wird der Entwurf in regelmäßigen Abständen gespeichert. Bei der automatischen Speicherung wird der Standardname der Aufgabe automatisch übernommen.
   >
   >
   >Weitere Informationen finden Sie unter „Entwurf regelmäßig speichern“ unter [Verwalten von Voreinstellungen](/help/forms/using/getting-started-livecycle-html-workspace.md).

1. Geben Sie im Dialogfeld „Als Entwurf speichern“ einen eindeutigen Namen für die Aufgabe ein und wählen Sie **OK** aus.

   ![saveasdraftdialog_name](assets/saveasdraftdialog_name.png)

   Der Entwurf wird mit dem eingegebenen Namen gespeichert. Die Aufgabe bleibt in Ihrer Aufgabenliste und alle Änderungen, die Sie im Formular vorgenommen haben, werden im Ordner „Entwürfe“ gespeichert. In der Aufgabenliste können Sie mit dem Namen nach dem Entwurf suchen, um diesen weiterzubearbeiten.

   ![searchfortask](assets/searchfortask.png)

## Abschließen von Aufgaben {#completing-tasks}

Die Erledigung einer Aufgabe hängt von der Aufgabe und Ihrer Rolle im Prozess ab. Sie werden ggf. aufgefordert, eine Anfrage zu genehmigen oder abzulehnen, Inhalte bereitzustellen, Informationen zu prüfen und zu bestätigen oder anzugeben, dass Sie gehandelt haben.

Sie können eine Aufgabe auf verschiedene Weise abschließen:

* mit den Aktionen auf einer der Registerkarten
* mit den im Formular integrierten Aktionen
* über Ihre Aufgabenliste, ohne die Aufgabe zu öffnen

>[!NOTE]
>
>Diese Option ist verfügbar, wenn beim Entwerfen eines Prozesses in Workbench das Feld `isMustOpenToComplete` im Schritt `Assign Task` nicht ausgewählt ist.

* per E-Mail, wenn Sie E-Mail-Benachrichtigungen erhalten

Wenn Sie eine Aufgabe abschließen, wird je nach Aufgabe möglicherweise ein Dialogfeld zum Bestätigen der Aktion angezeigt. Beispielsweise kann ein Dialogfeld angezeigt werden, in dem Sie aufgefordert werden, die Gültigkeit der eingegebenen Informationen zu bestätigen.

>[!NOTE]
>
>Wenn Sie eine Aufgabe geändert haben, jedoch noch nicht bereit sind, die Aufgabe abzuschließen, können Sie Ihre Arbeit als Entwurf speichern, indem Sie auf „Speichern“ klicken und später daran weiterarbeiten.

### Abschließen von Aufgaben {#complete-a-task}

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie die Aufgabe aus und klicken Sie unten in der Liste auf die entsprechende Schaltfläche, um den nächsten im Prozess erforderlichen Schritt einzuleiten.
   * Wenn das Formular keine Schaltflächen aufweist und die Schaltfläche „Abschließen“ in AEM Forms Workspace zur Verfügung steht, klicken Sie auf **Abschließen**.
   * Wenn das Formular Schaltflächen enthält und die Schaltfläche „Abschließen“ in AEM Forms Workspace nicht zur Verfügung steht, klicken Sie im Formular auf die entsprechende Schaltfläche für den nächsten im Prozess erforderlichen Schritt.

   Wenn das Formular keine Schaltflächen enthält und die Schaltfläche „Abschließen“ in AEM Forms Workspace nicht zur Verfügung steht, wird eine Meldung angezeigt, die Sie darauf hinweist, dass das Formular nicht übermittelt werden kann.

1. Wenn ein Dialogfeld zur Bestätigung angezeigt wird, führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf **OK**, wenn Sie die Aufgabe abgeschlossen haben und nun bereit sind, sie abzuzeichnen.
   * Klicken Sie auf **Abbrechen**, wenn Sie zu der Aufgabe zurückkehren möchten und nicht bereit sind, sie abzuzeichnen.

>[!NOTE]
>
>Es wird möglicherweise eine Schaltfläche „Senden“ in den HTML-Formularen angezeigt, wenn Prozesseigenschaften in einem Formular verwendet werden. Diese Schaltfläche wird nicht angezeigt, wenn dasselbe Formular als PDF-Datei gerendert wird. Um eine Aufgabe abzuschließen, klicken Sie auf die Schaltfläche „Senden“ unten in AEM Forms Workspace (außerhalb des Formulars) und nicht auf die Schaltfläche „Senden“ im Formular.

### Genehmigen mehrerer Aufgaben {#bulk-approve-tasks}

Sie können mehrere Aufgaben aus Ihrer Aufgabenliste auf einmal senden. Es können nur Aufgaben desselben Prozesses mit denselben Aufgabennamen und denselben Routenoptionen zusammen gesendet werden.

>[!NOTE]
>
>Diese Option ist verfügbar, wenn in Workbench beim Entwerfen eines Prozesses im Schritt „Aufgabe zuweisen“ das Feld „isMustOpenToComplete“ nicht ausgewählt ist.

1. Wählen Sie auf der Aufgabenseite im linken Bereich Ihre persönliche Aufgabenliste aus. Alle Ihre Aufgaben werden im mittleren Bereich angezeigt.
1. Wählen Sie die Option **Massenmodus aktivieren** aus. Vor den Aufgaben in der Liste werden Kontrollkästchen angezeigt.

   >[!NOTE]
   >
   >Diese Option ist nicht verfügbar für Aufgaben, für die beim Entwerfen eines Prozesses in Workbench das Feld „isMustOpenToComplete“ im Schritt „Aufgabe zuweisen“ ausgewählt wurde. Kontrollkästchen solcher Aufgaben in der Aufgabenliste sind immer deaktiviert.

1. Wählen Sie die Aufgaben aus, die gleichzeitig genehmigt werden sollen. Es können mehrere Aufgaben desselben Prozesses mit denselben Aufgabennamen und denselben Routenoptionen ausgewählt werden. Wenn Sie eine Aufgabe zur Genehmigung auswählen, bleiben nur Aufgaben desselben Prozesses mit denselben Aufgabennamen und denselben Routenoptionen aktiviert. Die anderen Aufgaben werden deaktiviert.

   ![1_bulkapproval](assets/1_bulkapproval.png)

1. Klicken Sie auf die verfügbare Sendeoption. Die ausgewählten Aufgaben werden gesendet.

   ![bulkapproval](assets/bulkapproval.png)

## Beteiligen an Aufgaben per E-Mail {#participating-in-tasks-through-email}

Sie können Aufgaben per E-Mail empfangen und abschließen. Durch die Beteiligung an Aufgaben per E-Mail erübrigt sich das routinemäßige Prüfen Ihrer Aufgabenliste auf neue Aufgaben bzw. das Prüfen des Status einer Aufgabe auf der Tracking-Seite.

Zunächst müssen Sie Voreinstellungen für AEM Forms Workspace festlegen, um E-Mail-Benachrichtigungen zu erhalten. AEM Forms Workspace kann E-Mail-Benachrichtigungen für Aufgaben in Ihrer Aufgabenliste oder einer beliebigen Gruppen-Aufgabenliste, der Sie angehören, senden. Das Administrator-Team legt fest, wann und an wen E-Mail-Benachrichtigungen gesendet werden.

Die E-Mail-Nachrichten können einen Link, über den die Aufgabe in AEM Forms Workspace geöffnet wird, einen Anhang mit dem Formular, das für die Aufgabe verwendet wird, oder Aktionen zum Abschließen der Aufgabe per E-Mail enthalten. Wenn die E-Mail-Nachricht ein Formular mit integrierten Schaltflächen zum Abschließen der Aufgabe enthält, können Sie das Formular öffnen und die Aufgabe abschließen. Wenn die E-Mail-Nachricht Aktionen zum Abschließen der Aufgabe enthält, können Sie die Aufgabe abschließen, indem Sie auf die Aktionen in der E-Mail klicken oder die E-Mail beantworten und die entsprechende Aktion als erste Zeile des E-Mail-Textes eingeben.

>[!NOTE]
>
>* Informationen zum Konfigurieren des Arbeitsbereichs für die Verwendung der entsprechenden E-Mail-Vorlagen finden Sie im [Administratorhandbuch zu AEM Forms JEE](https://help.adobe.com/de-DE/AEMForms/6.1/AdminHelp/).
>
>* Wenn Entwürfe nach dem Senden der Aufgabe im AEM Forms-Arbeitsbereich weitergeleitet werden, werden E-Mail-Benachrichtigungen gesendet. Wenn Entwürfe vom Startpunkt des AEM Forms-Arbeitsbereichs weitergeleitet werden, werden keine E-Mail-Benachrichtigungen gesendet.

Wenn Sie eine Aufgabe per E-Mail abschließen, wird die Aufgabe aus Ihrer Aufgabenliste in AEM Forms Workspace entfernt.

>[!NOTE]
>
>Wenn der Benutzer im Browser nicht in AEM Forms Workspace angemeldet ist und einen Link zu einer Aufgabe in der Aufgabenliste öffnet, kann der direkte Link zu der Aufgabe nicht geöffnet werden und es wird eine Ausnahme angezeigt. Melden Sie sich bei AEM Forms Workspace an, bevor Sie auf Links in E-Mails klicken.

>[!NOTE]
>
>Sie können eine E-Mail-Benachrichtigung nicht weiterleiten, um die Aufgabe einem anderen Benutzer zuzuweisen. Sie können Aufgaben an andere Benutzende nur innerhalb von AEM Forms Workspace weiterleiten.

### Empfangen von E-Mail-Benachrichtigungen {#receive-email-notification-messages}

1. Klicken Sie auf **Voreinstellungen**.
1. Wählen Sie in der Liste **Über Aufgabenereignisse per E-Mail benachrichtigen** die Option **Ja** aus.
1. Um das Formular samt Daten in die E-Mail-Nachricht aufzunehmen, wählen Sie in der Liste **Formulare in E-Mail anfügen** die Option **Ja** aus.

## Beteiligen an Aufgaben über Mobilgeräte {#participating-in-tasks-through-mobile-devices}

Mit der AEM Forms Workspace-APP können Sie sich an Aufgaben von Ihrem Mobilgerät aus beteiligen. Wenden Sie sich vor dem Installieren der Anwendung an Ihr Systemadmin-Team, um zu klären, ob Ihre Organisation den Einsatz der AEM Forms Workspace-App unterstützt.

## Grundlegendes zu Terminen und Erinnerungen {#about-deadlines-and-reminders}

Ein *Termin* bestimmt den Zeitpunkt mit Datum und Uhrzeit, zu dem eine Aufgabe erledigt sein muss. Wenn ein Termin verstreicht, leitet der Server die Aufgabe zum nächsten Schritt im Prozess weiter (dies kann die Aufgabenliste eines anderen Benutzers sein) und das Terminsymbol wird für die Aufgabe angezeigt. Das Terminsymbol wird unabhängig von den für den Prozess geltenden Regeln angezeigt.

Eine *Erinnerung* informiert Sie, dass eine Aufgabe Ihre Aufmerksamkeit erfordert. Erinnerungen werden zu einem vordefinierten Zeitpunkt und anschließend in regelmäßigen Abständen angezeigt, bis die dazugehörige Aufgabe erledigt ist. Wenn Sie eine Erinnerung erhalten, wird das Erinnerungssymbol für die Aufgabe angezeigt.

Der Geschäftsprozess bestimmt das Verhalten und die Zeitvorgabe von Terminen und Erinnerungen. Nicht alle Prozesse weisen Termine und Erinnerungen auf. Der Administrator gibt an, ob E-Mail-Benachrichtigungen für Termine und Erinnerungen gesendet werden. Sie können in Ihren Voreinstellungen festlegen, ob Sie E-Mail-Benachrichtigungen empfangen möchten.

## Arbeiten mit Aufgaben aus Gruppen- und freigegebenen Warteschlangen {#working-with-tasks-from-group-and-shared-queues}

Alle Ihnen zugewiesenen Aufgaben werden in Ihrer Aufgabenliste (Warteschlange) angezeigt.

Alle freigegebenen und Gruppenaufgabenlisten, auf die Sie zugreifen können, werden auf der Seite „Aufgaben“ im linken Bereich angezeigt. Sie können Aufgaben aus allen Aufgabenlisten erledigen, auf die Sie Zugriff haben.

Einer Aufgabenliste können mehrere Mitglieder zugewiesen sein. Aufgabenlisten werden von einem Administrator basierend auf den spezifischen Anforderungen des Unternehmens eingerichtet. Gruppenaufgabenlisten sind eine Möglichkeit, Aufgaben auf mehrere Personen mit ähnlichen Zuständigkeiten zu verteilen.

Angenommen, alle Mitglieder Ihres Teams bearbeiten Kreditantragsformulare. Alle diese Aufgaben werden an eine Aufgabenliste gesendet, auf die alle Mitglieder Ihrer Gruppe zugreifen können. Jedes Mitglied Ihrer Gruppe kann auf die Aufgaben in dieser Aufgabenliste zugreifen.

Eine freigegebene Aufgabenliste wird angezeigt, wenn ein anderer Benutzer seine Aufgabenliste für Sie freigibt oder ausdrücklich eine Aufgabe für Sie freigibt. Sie können die Aufgaben in der Aufgabenliste dieses Benutzers anzeigen und sie in seinem Auftrag erledigen. Wenn Sie beispielsweise Urlaub nehmen, können Sie Ihre Aufgabenliste für eine Kollegin bzw. einen Kollegen freigeben, die bzw. der Ihre Aufgaben erledigt, solange Sie abwesend sind.

>[!NOTE]
>
>Sie können auch Abwesenheitseinstellungen festlegen, um Aufgaben während Ihrer Abwesenheit an andere Benutzende weiterzuleiten.

Um eine Aufgabe aus einer Gruppenaufgabenliste oder freigegebenen Aufgabenliste zu bearbeiten, fordern Sie die Aufgabe zuerst an. Die Aufgabe gehört dann Ihnen, bis Sie sie abschließen oder an eine andere Benutzerin bzw. einen anderen Benutzer weiterleiten.

### Freigeben von Warteschlangen {#sharing-queues}

Sie können Ihre Aufgabenliste für andere Benutzer freigeben, die dann alle neuen Aufgaben in Ihrer Aufgabenliste anzeigen und für Sie ausführen können. Aufgaben, die sich schon vor der Freigabe in Ihrer Aufgabenliste befunden haben, können von diesen Benutzern nicht angezeigt werden. Die Benutzerin oder der Benutzer kann nur die Aufgaben anzeigen und anfordern, die in Ihrer Aufgabenliste eintreffen, nachdem Sie den Zugriff darauf gewährt haben.

Beachten Sie, dass eine Benutzerin oder ein Benutzer eine Aufgabe in einer freigegebenen Warteschlange nur anzeigen kann, wenn die Prozess-Designerin bzw. der Prozess-Designer auf der Registerkarte für die Aufgaben-Zugriffssteuerungslisten (Access Control List, ACL) des Benutzerdienstes die Option „ACLs für freigegebene Warteschlangen hinzufügen“ aktiviert hat.

>[!NOTE]
>
>Für geplante Abwesenheitszeiten können Sie auch Abwesenheitseinstellungen festlegen, um Aufgaben während Ihrer Abwesenheit an andere Benutzende weiterzuleiten (anstatt die gesamte Aufgabenliste freizugeben).

**Freigeben Ihrer Warteschlange**

1. Klicken Sie auf der Registerkarte **Warteschlangen** auf der Registerkarte **Voreinstellungen** auf das „+“-Symbol für „Benutzer, für die ‚Meine Warteschlange‘ zurzeit freigegeben ist“.
1. Suchen und wählen Sie den Namen der Benutzerin oder des Benutzers.
1. Klicken Sie auf die Schaltfläche **Freigeben**, um Ihre Warteschlange für die ausgewählte Benutzerin oder den ausgewählten Benutzer freizugeben.
1. Wählen Sie den Namen der Benutzerin oder des Benutzers aus und klicken Sie auf **Freigeben**.

   >[!NOTE]
   >
   >Sie können eine Benutzerin oder einen Benutzer aus der Freigabe Ihrer Aufgabenliste entfernen, indem Sie am Ende der Zeile, in der die Benutzerin oder der Benutzer aufgeführt ist, auf das **X**-Symbol klicken.

### Zugreifen auf andere Warteschlangen {#accessing-other-queues}

Sie können den Zugriff auf die Aufgabenliste einer anderen Benutzerin oder eines anderen Benutzers anfordern, um alle neuen Aufgaben in der Aufgabenliste der Benutzerin oder des Benutzers anzeigen und anfordern zu können.

Wenn Sie den Zugriff auf die Aufgabenliste eines anderen Benutzers anfordern, empfängt dieser in seiner Aufgabenliste eine Aufgabe zum Genehmigen oder Ablehnen Ihrer Anforderung. Nachdem die Benutzerin oder der Benutzer die Aufgabe abgeschlossen hat, erhalten Sie eine Benachrichtigung in Ihrer Aufgabenliste.

Wenn Ihnen der Zugriff auf die Aufgabenliste eines anderen Benutzers gewährt wurde, können Sie keine Aufgaben anzeigen, die sich schon vor der Gewährung des Zugriffs in der Aufgabenliste des Benutzers befunden haben. Sie können nur die Aufgaben anzeigen, die in der Aufgabenliste der Benutzerin oder des Benutzers eintreffen, nachdem Ihnen der Zugriff auf die Liste gewährt wurde.

**Zugreifen auf andere Warteschlangen**

1. Öffnen Sie auf der Registerkarte **Voreinstellungen** die Registerkarte **Warteschlangen**.
1. Klicken Sie auf das „+“-Zeichen für „Benutzerwarteschlangen, auf die ich Zugriff habe“. Suchen Sie den Namen des Benutzers im Popup-Dialogfeld.
1. Wählen Sie den Namen der Benutzerin oder des Benutzers aus und klicken Sie auf **Anfordern**.

   >[!NOTE]
   >
   >Sie können die eigene Zugriffsberechtigung für eine andere Aufgabenliste entfernen, indem Sie den Benutzernamen in der Liste „Benutzerwarteschlangen, auf die ich Zugriff habe“ auswählen und am Ende der Zeile mit dem Benutzernamen auf das **X** klicken. Sie können Ihren Zugriff auf eine andere Aufgabenliste nicht selbst entfernen, solange die Anfrage zum Zugriff auf die Aufgabenliste noch aussteht.

## Einstellen von Abwesenheitseinstellungen {#setting-out-of-office-preferences}

Für geplante Abwesenheitszeiten können Sie festlegen, was während dieser Zeit mit den Ihnen zugeordneten Aufgaben passieren soll.

Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Wenn Sie sich in einer anderen Zeitzone als der Server befinden, wird die Zeitzone des Servers verwendet.

Sie können eine Person festlegen, an die Ihre Aufgaben standardmäßig gesendet werden. Zudem können Sie Ausnahmen für Aufgaben aus speziellen Prozessen festlegen, die an einen anderen Benutzer gesendet oder bis zu Ihrer Rückkehr in Ihrer Aufgabenliste bleiben sollen. Wenn die angegebene Person ebenfalls abwesend ist, werden die Aufgaben an den von dieser Person angegebenen Vertreter weitergeleitet. Wenn es nicht möglich ist, eine Aufgabe einer anderen Person, die nicht abwesend ist, zuzuweisen, bleibt die Aufgabe in Ihrer Aufgabenliste.

>[!NOTE]
>
>Während Ihrer Abwesenheit bleiben alle Aufgaben, die sich bereits zuvor in Ihrer Aufgabenliste befunden haben, genau dort und werden nicht an andere Benutzende weitergeleitet.

### Festlegen von Abwesenheitseinstellungen {#set-out-of-office-preferences}

1. Klicken Sie auf **Voreinstellungen** und dann auf **Abwesenheit**.
1. Um den Zeitraum Ihrer Abwesenheit festzulegen, führen Sie einen der folgenden Schritte aus:

   * Um anzugeben, dass Sie für unbestimmte Zeit abwesend sein werden, wählen Sie in der Liste **Ich bin zurzeit** den Eintrag **Nicht im Hause** aus und geben keinen Datumsbereich an.
   * Um anzugeben, an welchem Datum und zu welcher Uhrzeit Ihre Abwesenheit beginnt, klicken Sie auf das „+“-Symbol für **Abwesenheitszeitplan**. Verwenden Sie die Kalender- und Uhrzeitliste, um das Anfangsdatum und die Anfangsuhrzeit anzugeben. Wenn Sie kein Datum und keine Uhrzeit für das Abwesenheitsende angeben, gelten Sie ab dem Datum und der Uhrzeit des Abwesenheitsbeginns für unbestimmte Zeit als abwesend, bis Sie die Voreinstellungen ändern.

1. Um festzulegen, was standardmäßig mit Ihren Aufgaben passieren soll, wählen Sie in der Liste **Bei Abwesenheit: Standardbenutzer für Abwesenheitsaufgaben** eine der folgenden Optionen aus:

   * Wählen Sie **Nicht zuweisen** aus, um Aufgaben bis zu Ihrer Rückkehr in der Aufgabenliste zu belassen.
   * Wählen Sie **Benutzer suchen** aus, um eine Benutzerin bzw. einen Benutzer zu suchen, der bzw. dem Ihre Aufgabe zugewiesen werden sollen. Wenn Sie eine Benutzerin oder einen Benutzer auswählen, können Sie auch den Abwesenheitszeitplan dieser Person anzeigen.

1. Um Ausnahmen zum Standard festzulegen, klicken Sie auf das „+“-Symbol für **Ausnahmen verarbeiten**, wählen Sie den Prozess aus, für den eine Ausnahme erstellt werden soll, und dann eine andere Benutzerin oder einen anderen Benutzer oder klicken Sie in der Liste **ist zugewiesen zu** auf **Nicht zuweisen**.

   >[!NOTE]
   >
   >Der Prozessentwickler kann festlegen, dass Aufgaben aus bestimmten Prozessen immer privat sind und nicht an andere Benutzer weitergeleitet werden. Diese Einstellung setzt all Ihre Einstellungen außer Kraft.

1. Wenn Sie die gewünschten Voreinstellungen festgelegt haben, klicken Sie auf **Speichern**. Wenn die Einstellungen angeben, dass Sie zurzeit abwesend sind, treten die Änderungen sofort in Kraft. Anderenfalls treten sie am angegebenen Anfangsdatum zur festgelegten Uhrzeit in Kraft. Selbst wenn Sie sich während Ihrer Abwesenheit am System anmelden, gelten Sie erst wieder als anwesend, wenn Sie die Einstellungen ändern.
