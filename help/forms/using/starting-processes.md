---
title: Starten von Prozessen
description: Verwenden von LiveCycle AEM Forms Workspace – Auswählen von Prozessen, Hinzufügen von Notizen und Anhängen, Speichern von Entwurfskopien und Hinzufügen zu Favoriten.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b2a6ba3a-0f4c-44b1-8f9a-c15c6fb8c305
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 100%

---

# Starten von Prozessen {#starting-processes}

In AEM Forms Workspace werden Prozesse aufgrund der vom Administrator oder Prozessentwickler festgelegten Kategorien organisiert. Sie können häufig verwendete Prozesse auch in der Kategorie „Favoriten“ platzieren, um den Zugriff zu erleichtern.

Beim Starten eines Prozesses müssen Sie eventuell ein Formular ausfüllen, um einen von AEM Forms gesteuerten Geschäftsprozess zu starten. Wenn ein Formular den vorbereitenden Datenprozess verwendet, können einige Informationen in einem leeren Formular zuvor ausgefüllt werden, wenn ein neuer Prozess initiiert wird.

Beispiel: Sie möchten einen neuen Computer-Monitor kaufen und starten deshalb einen Prozess namens *Bestellung*. Beim Starten des Prozesses wird ein Formular geöffnet, das Sie zur Eingabe von Details über den zu bestellenden Artikel auffordert. Eventuell sind Ihr Name, Ihre Mitarbeiternummer sowie der Name Ihrer bzw. Ihres Vorgesetzten bereits vorab in das Formular eingetragen. Wenn Sie die Anfrage absenden, wird ein Geschäftsprozess initiiert. Der Server leitet die Anfrage anhand der Prozessdefinition automatisch an Ihre Vorgesetzte bzw. Ihren Vorgesetzten weiter. Die Aufgabe wird in der Aufgabenliste Ihrer bzw. Ihres Vorgesetzten angezeigt. Wenn dieser Mensch die Anforderung genehmigt, leitet der Forms-Workflow die Anfrage an die Einkaufsabteilung weiter und sendet Ihnen eine E-Mail-Benachrichtigung.

## Auswählen der zu startenden Prozesse {#selecting-processes-to-start}

Sie können einen Prozess auswählen, um ihn zu starten oder weitere Informationen dazu anzuzeigen.

Bei der Auswahl eines zu startenden Prozesses müssen Sie eventuell ein Formular ausfüllen, das dem Prozess zugeordnet ist. Durch Absenden des Formulars wird der Prozess gestartet.

Formulare in verschiedenen Arten von Dateiformaten werden unterstützt, einschließlich Adobe PDF-, HTML- und SWF-Dateien. Bei einem Formular kann es sich um ein herkömmliches druckbares oder Web-basiertes Formular oder um einen Formular-Guide handeln, der Sie durch eine Reihe assistentenähnlicher Felder führt, um Informationen zu erfassen.

Sie können das Formular auch offline speichern, ausfüllen und dann zum Abschließen der Aufgabe absenden, sofern dies für das Formular und den Prozess zulässig ist. Wenn das Formular abgesendet wird, wird Ihr E-Mail-Client mit der entsprechenden Server-E-Mail-Adresse gestartet, falls ein E-Mail-Endpunkt konfiguriert ist. Sie können das ausgefüllte Formular dann per E-Mail an den Server senden.

Wenn Sie einen Prozess auswählen, werden die Registerkarten „Formular“ und „Details“ eingeblendet. Falls der Prozess das Hinzufügen von Anmerkungen oder Anhängen zulässt, werden auch die Registerkarten „Anhänge“ und „Anmerkungen“ angezeigt. Wenn Sie die Zusammenfassungs-URL mit dem Prozess konfiguriert haben, wird die Registerkarte Zusammenfassung ebenfalls angezeigt. Auf der Registerkarte „Formulare“ wird das zugeordnete Formular angezeigt. Auf der Registerkarte „Details“ werden Informationen über die aktuelle Aufgabe und den Prozess angezeigt, zu dem sie gehört.

### Starten eines Geschäftsprozesses {#start-a-business-process}

1. Wählen Sie auf der Seite „Prozess starten“ in der Liste auf der linken Seite eine Kategorie aus. Alle Prozesse in dieser Kategorie, auf die Sie Zugriff haben, werden rechts angezeigt.

   >[!NOTE]
   >
   >Wenn der Kategorienbereich ausgeblendet ist, klicken Sie auf „Kategorien öffnen“ im linken oberen Bereich von AEM Forms Workspace, um den Bereich zu öffnen.

1. Wählen Sie einen Prozess aus, indem Sie auf eine Aufgabe klicken. Auf der Registerkarte „Formulare“ wird das Formular geöffnet, das dem Prozess zugeordnet ist.

   Jedes Formular in einem Prozess hat eine eindeutige URL. Sie können die eindeutige URL verwenden, um den HTML Workspace direkt mit dem spezifischen Prozess und Formular zu starten. Das Format der URL lautet https://&lt;server>:&lt;port>/lc/libs/ws/index.html#/startprocess/&lt;ApplicationName>%2F&lt;ProcessName>. Die Zeichenfolge &lt;ApplicationName>%2F&lt;ProcessName> ist immer URL-kodiert. Eine Beispiel-URL ist http://localhost:8080/lc/libs/ws/index.html#/startprocess/MyApplication%2FNewProcess. Die Zeichenfolge ApplicationName%2FProcessName im Beispiel ist URL-kodiert.

1. Füllen Sie das Formular entsprechend den zugehörigen Anweisungen aus. Klicken Sie ggf. auf **Maximieren**, um den sichtbaren Bereich des Formulars zu vergrößern.
1. Wenn die Registerkarte „Anhänge“ verfügbar ist, fügen Sie nach Bedarf Anhänge hinzu.
1. Wenn die Registerkarte „Anmerkungen“ verfügbar ist, geben Sie nach Bedarf Anmerkungen an.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie im Formular auf die Schaltfläche „Absenden“, wenn das Formular eine solche hat.
   * Klicken Sie auf „Vervollständigen“ unterhalb des Formulars, wenn das Formular keine Schaltfläche „Senden“ hat.

   Die Prozessverwaltung startet den Prozess und leitet das Formular in die Aufgabenlisten der entsprechenden Personen weiter, die die nächste Aufgabe im Prozess ausführen müssen.

   Wenn Sie ein Formular vor dem Absenden schließen müssen und die eingegebenen Daten nicht verlieren möchten, speichern Sie es als Entwurf und stellen Sie es später fertig, wenn es der Prozess gestattet. Sie können auch auf **Offline** klicken und das Formular dann später von Adobe® Reader® oder Adobe® Acrobat® Professional bzw. Acrobat Standard aus absenden, sofern dies für das Formular und den Prozess zulässig ist.

   >[!NOTE]
   >
   >Die Offline-Option ist nur für PDF-Formulare verfügbar.

## Hinzufügen von Anmerkungen und Anhängen {#adding-notes-and-attachments}

Sie können einem Prozess Anmerkungen und Dateianhänge hinzufügen, wenn dies für den Prozess zulässig ist. Sie können Berechtigungen für andere Benutzende gewähren, die am Prozess teilnehmen, um die Anmerkungen oder Anhänge anzuzeigen, zu aktualisieren und zu löschen.

### Hinzufügen einer Anmerkung {#add-a-note}

Sie können mehrere Anmerkungen hinzufügen, die schriftlichen Anmerkungen bearbeiten und diese löschen. Jeder Anmerkung ist ein Titel, eine Beschreibung und eine Zugriffsberechtigung zugeordnet. Sie können eine der folgenden Zugriffsberechtigungen für eine Anmerkung festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Öffnen Sie eine Aufgabe und klicken Sie auf die Registerkarte **Notizen**, wenn der Prozess es zulässt.
1. Geben Sie einen Titel für die Anmerkung in das Feld **Titel** ein und den Text der Anmerkung in das Feld **Anmerkung** ein.
1. Wählen Sie für andere am Prozess teilnehmende Benutzende die Ebene **Berechtigungen** für die Anmerkung aus.
1. Klicken Sie auf **OK**. An das Formular wird eine Textdatei mit Ihrer Notiz angehängt. Sie können eine Anmerkung aktualisieren, indem Sie darauf klicken und den Text direkt ändern. Sie können eine Notiz löschen, indem Sie auf die Schaltfläche **Löschen** ![Image of a trash can](assets/icondelete.png) neben der Notiz klicken.

### Hinzufügen von Anhängen {#add-an-attachment}

Sie können auch eigene Anmerkungen über den Anhang hinzufügen. Sie können eine der folgenden Zugriffsberechtigungen für einen Anhang festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Klicken Sie auf die Registerkarte **Anlagen** und wählen Sie **Anlage**.
1. Klicken Sie auf **Durchsuchen**, um die anzuhängende Datei auszuwählen.
1. Wählen Sie die **Berechtigungsebene** des Anhangs für andere Benutzende aus, die an dem Prozess beteiligt sind. Wenn Sie die **Leseberechtigung** aktivieren, können andere Benutzende die Datei lokal speichern. Wenn Sie eine der Bearbeitungsberechtigungen auswählen, können andere Benutzende auch eine neue Datei hochladen, um Ihren Anhang durch sie zu ersetzen.
1. Klicken Sie auf **OK**. Die Datei wird an das Formular angefügt. Sie können eine Datei löschen, indem Sie auf die Schaltfläche **Löschen** ![Image of a trash can](assets/icondelete.png) neben dem Anhang klicken.

## Speichern von Entwurfskopien von Formularen {#saving-draft-copies-of-forms}

Wenn Sie ein Formular zu einem späteren Zeitpunkt abschließen und absenden müssen, können Sie es als Entwurfskopie speichern, damit Sie die eingegebenen Daten nicht verlieren. Entwürfe werden zur Kategorie „Entwürfe“ auf der Seite „Aufgaben“ hinzugefügt.

Nachdem Sie einen Formularentwurf erneut geöffnet und abgesendet haben, wird der Entwurf aus der Kategorie „Entwürfe“ entfernt.

Außerdem können Sie Workspace so konfigurieren, dass Informationen, die von einem Benutzer als Entwurf eingegeben wurden, automatisch gespeichert werden. Weitere Informationen finden Sie unter [Verwalten der Voreinstellungen](/help/forms/using/getting-started-livecycle-html-workspace.md).

>[!NOTE]
>
>Abhängig vom zugeordneten Prozess ist in einigen Formularen die Schaltfläche „Speichern“ nicht verfügbar.

### Speichern einer Entwurfskopie {#save-a-draft-copy}

1. Klicken Sie auf **Speichern** in der linken unteren Ecke einer beliebigen Registerkarte. Das Formular wird zur Kategorie „Entwürfe“ auf der Seite „Aufgaben“ hinzugefügt. Alle Änderungen, die Sie am Formular vorgenommen haben, werden gespeichert.

### Erneutes Öffnen einer Entwurfskopie {#reopen-a-draft-copy}

1. Wählen Sie auf der Seite „Aufgaben“ die Warteschlange der **Entwürfe** aus und klicken Sie auf die Entwurfskopie des Formulars.

   Wenn das Formular eine ganze Reihe von Feldern enthält, müssen Sie eventuell zu dem Feld navigieren, bei dem Sie die letzte Sitzung beendet haben.

## Hinzufügen von Prozessen zur Kategorie „Favoriten“ {#adding-processes-to-the-favorites-category}

Sie können beliebig Prozesse zu Ihrer Kategorie „Favoriten“ hinzufügen. Durch das Festlegen von Favoriten können Sie alle Prozesse, die Sie häufig starten, in einer Kategorie gruppieren und sich so den Zugriff erleichtern.

>[!NOTE]
>
>Wenn Sie Prozesse meist beim Arbeiten mit AEM Forms Workspace starten, können Sie die Voreinstellung „Startposition“ so einstellen, dass beim Starten von AEM Forms Workspace automatisch die Kategorie „Favoriten“ angezeigt wird. Weitere Informationen finden Sie unter „Verwalten von Voreinstellungen“ in [Erste Schritte mit AEM Forms Workspace](/help/forms/using/getting-started-livecycle-html-workspace.md).

Um einen Prozess als Favoriten zu markieren, wählen Sie die Aufgabe in der Kategorie aus und klicken Sie auf den ungefüllten Stern. Der Stern wird golden. Um die Markierung eines Prozesses als Favorit zu entfernen, klicken Sie erneut auf den goldenen Stern.
