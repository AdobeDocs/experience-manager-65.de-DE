---
title: Starten von Prozessen
seo-title: Starten von Prozessen
description: Verwendung von LiveCycle AEM Forms Workspace – Auswählen von Prozessen, Hinzufügen von Notizen und Anlagen, Speichern von Entwurfskopien und Hinzufügen zu Favoriten.
seo-description: Verwendung von LiveCycle AEM Forms Workspace – Auswählen von Prozessen, Hinzufügen von Notizen und Anlagen, Speichern von Entwurfskopien und Hinzufügen zu Favoriten.
uuid: a61da785-25b4-4482-bd72-02e250d35dc7
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c9d3f369-3744-41d5-b340-390ab7e03f36
exl-id: b2a6ba3a-0f4c-44b1-8f9a-c15c6fb8c305
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 90%

---

# Starten von Prozessen {#starting-processes}

In AEM Forms Workspace werden Prozesse aufgrund der vom Administrator oder Prozessentwickler festgelegten Kategorien organisiert. Sie können häufig verwendete Prozesse auch in der Kategorie „Favoriten“ platzieren, um den Zugriff zu erleichtern.

Beim Starten eines Prozesses müssen Sie eventuell ein Formular ausfüllen, um einen von AEM Forms gesteuerten Geschäftsprozess zu starten. Wenn ein Formular den vorbereitenden Datenprozess verwendet, können einige Informationen in einem leeren Formular zuvor ausgefüllt werden, wenn ein neuer Prozess initiiert wird.

Beispiel: Sie möchten einen neuen Computermonitor kaufen und starten deshalb einen Prozess namens *Bestellung*. Beim Starten des Prozesses wird ein Formular geöffnet, das Sie zur Eingabe von Details über den zu bestellenden Artikel auffordert. Eventuell sind Ihr Name, Ihre Mitarbeiternummer sowie der Name Ihres Vorgesetzten bereits vorab in das Formular eingetragen. Wenn Sie die Anforderung senden, wird ein Geschäftsprozess initiiert. Der Server leitet die Anforderung anhand der Prozessdefinition automatisch an Ihren Manager weiter. Die Aufgabe wird nun in der Aufgabenliste Ihres Managers angezeigt. Wenn Ihr Manager die Anforderung genehmigt, leitet der Formular-Workflow die Anforderung an die Einkaufsabteilung weiter und sendet Ihnen eine E-Mail-Benachrichtigung.

## Zu startende Prozesse auswählen  {#selecting-processes-to-start}

Sie können einen Prozess auswählen, um ihn zu starten oder weitere Informationen dazu anzuzeigen.

Bei der Auswahl eines zu startenden Prozesses müssen Sie eventuell ein Formular ausfüllen, das dem Prozess zugeordnet ist. Durch Senden des Formulars wird der Prozess gestartet.

Formulare in verschiedenen Arten von Dateiformaten werden unterstützt, einschließlich Adobe PDF-, HTML- und SWF-Dateien. Bei einem Formular kann es sich um ein herkömmliches druckbares oder webbasiertes Formular oder um einen Formular-Guide handeln, der Sie durch eine Reihe assistentenähnlicher Felder führt, um Angaben zu erfassen.

Sie können das Formular auch offline speichern, ausfüllen und dann zum Abschließen der Aufgabe senden, sofern dies für das Formular und den Prozess zulässig ist. Wenn das Formular gesendet wird, wird Ihr E-Mail-Client mit der entsprechenden Server-E-Mail-Adresse gestartet, falls ein E-Mail-Endpunkt konfiguriert ist. Sie können das ausgefüllte Formular dann per E-Mail an den Server senden.

Wenn Sie einen Prozess auswählen, werden die Registerkarten „Formular“ und „Details“ eingeblendet. Falls der Prozess das Hinzufügen von Notizen oder Anlagen zulässt, werden auch die Registerkarten „Anlagen“ und „Notizen“ angezeigt. Wenn Sie die Zusammenfassungs-URL mit dem Prozess konfiguriert haben, wird die Registerkarte „Zusammenfassung ebenfalls angezeigt. Auf der Registerkarte „Formulare“ wird das zugeordnete Formular angezeigt. Auf der Registerkarte „Details“ werden Informationen über die aktuelle Aufgabe und den Prozess angezeigt, zu dem sie gehört.

### Geschäftsprozess starten  {#start-a-business-process}

1. Wählen Sie auf der Seite „Startprozess“ in der Liste auf der linken Seite eine Kategorie aus. Alle Prozesse, auf die Sie in dieser Kategorie Zugriff haben, werden rechts angezeigt.

   >[!NOTE]
   >
   >Wenn der Kategorienbereich ausgeblendet ist, klicken Sie auf „Kategorien öffnen&quot; im linken oberen Bereich von AEM Forms Workspace, um den Bereich zu öffnen.

1. Wählen Sie einen Prozess aus, indem Sie auf eine Aufgabe klicken. Auf der Registerkarte „Formulare“ wird das Formular geöffnet, das dem Prozess zugeordnet ist.

   Jedes Formular in einem Prozess hat eine eindeutige URL. Sie können die eindeutige URL verwenden, um den HTML-Arbeitsbereich direkt mit dem spezifischen Prozess und Formular zu starten. Das Format der URL lautet https://&lt;Server>:&lt;Port>/lc/libs/ws/index.html#/startprocess/&lt;ApplicationName>%2F&lt;ProcessName>. Die Zeichenfolge &lt;ApplicationName>%2F&lt;ProcessName> ist immer URL-kodiert. Eine Beispiel-URL ist http://localhost:8080/lc/libs/ws/index.html#/startprocess/MyApplication%2FNewProcess. Die Zeichenfolge ApplicationName%2FPprocessName im Beispiel ist URL-kodiert.

1. Füllen Sie das Formular entsprechend den zugehörigen Anweisungen aus. Klicken Sie bei Bedarf auf **Maximieren** , um den sichtbaren Bereich des Formulars zu vergrößern.
1. Wenn die Registerkarte „Anlagen“ verfügbar ist, fügen Sie nach Bedarf Anlagen hinzu.
1. Wenn die Registerkarte „Notizen“ verfügbar ist, geben Sie nach Bedarf Notizen an.
1. Führen Sie einen der folgenden Schritte durch:

   * Klicken Sie auf die Schaltfläche „Senden“ im Formular, wenn das Formular eine Schaltfläche „Senden“ hat.
   * Klicken Sie auf „Vervollständigen&quot; unterhalb des Formulars, wenn das Formular keine Schaltfläche „Senden“ hat.

   Process Management startet den Prozess und leitet das Formular in die Aufgabenlisten der entsprechenden Personen weiter, die die nächste Aufgabe im Prozess ausführen müssen.

   Wenn Sie ein Formular vor dem Senden schließen müssen und die eingegebenen Daten nicht verlieren möchten, speichern Sie es als Entwurf und stellen Sie es später fertig, wenn es der Prozess gestattet. Sofern dies für das Formular und den Prozess zulässig ist, können Sie auch auf **Offline** klicken und es dann später von Adobe® Reader® oder Adobe® Acrobat® Professional oder Acrobat Standard aus senden.

   >[!NOTE]
   >
   >Die Offline-Option ist nur für PDF-Formulare verfügbar.

## Notizen und Anlagen hinzufügen  {#adding-notes-and-attachments}

Sie können einem Prozess Notizen und Dateianlagen hinzufügen, wenn dies für den Prozess zulässig ist. Sie können Berechtigungen für andere Benutzer bereitstellen, die am Prozess teilnehmen, um die Notizen oder Anlagen anzuzeigen, zu aktualisieren und zu löschen.

### Notizen hinzufügen  {#add-a-note}

Sie können mehrere Notizen hinzufügen, die schriftlichen Notizen bearbeiten und diese löschen. Jeder Notiz ist ein Titel, eine Beschreibung und eine Zugriffsberechtigung zugeordnet. Sie können eine der folgenden Zugriffsberechtigungen für eine Notiz festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Öffnen Sie eine Aufgabe und klicken Sie auf die Registerkarte **Notizen**, wenn der Prozess es zulässt.
1. Geben Sie einen Titel für die Notiz in das Feld **Titel** ein und geben Sie den Text der Notiz in das Feld **Notiz** ein.
1. Wählen Sie für andere am Prozess teilnehmende Benutzer die Ebene **Berechtigungen** für die Notiz aus.
1. Klicken Sie auf **OK**. An das Formular wird eine Textdatei mit Ihrer Notiz angehängt . Sie können eine Notiz aktualisieren, indem Sie darauf klicken und den Text direkt ändern. Sie können eine Notiz löschen, indem Sie auf die Schaltfläche **Löschen** ![Bild eines Papierkorbs](assets/icondelete.png) neben der Notiz klicken.

### Anlagen hinzufügen {#add-an-attachment}

Sie können auch eigene Kommentare über die Anlage hinzufügen. Sie können eine der folgenden Zugriffsberechtigungen für eine Anlage festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Klicken Sie auf die Registerkarte **Anlagen** und wählen Sie **Anlage**.
1. Klicken Sie auf **Durchsuchen**, um die anzuhängende Datei auszuwählen.
1. Wählen Sie für andere am Prozess teilnehmende Benutzer die Ebene **Berechtigungen** für die Anlage aus. Wenn Sie die **Leseberechtigung** aktivieren, können andere Benutzer die Datei lokal speichern. Wenn Sie eine der Bearbeitungsberechtigungen auswählen, können andere Benutzer auch eine neue Datei hochladen, um Ihre Anlage durch sie zu ersetzen.
1. Klicken Sie auf **OK**. Die Datei wird an das Formular angehängt. Sie können eine Datei löschen, indem Sie neben der Anlage auf die Schaltfläche **Löschen** ![Bild eines Papierkorbs](assets/icondelete.png) klicken.

## Entwurfskopien von Formularen speichern {#saving-draft-copies-of-forms}

Wenn Sie ein Formular zu einem späteren Zeitpunkt abschließen und senden müssen, können Sie es als Entwurf speichern, damit Sie die eingegebenen Daten nicht verlieren. Entwürfe werden zur Kategorie „Entwürfe“ auf der Seite „Aufgaben“ hinzugefügt.

Nachdem die Entwurfskopie eines Formulars erneut geöffnet und gesendet wurde, wird der Entwurf aus der Kategorie „Entwürfe“ entfernt.

Außerdem können Sie Workspace so konfigurieren, dass Informationen, die von einem Benutzer als Entwurf eingegeben wurden, automatisch gespeichert werden. Weitere Informationen finden Sie unter [Voreinstellungen verwalten](/help/forms/using/getting-started-livecycle-html-workspace.md).

>[!NOTE]
>
>Abhängig vom zugeordneten Prozess ist in einigen Formularen die Schaltfläche „Speichern“ nicht verfügbar.

### Entwurfskopien speichern  {#save-a-draft-copy}

1. Klicken Sie in der linken unteren Ecke einer Registerkarte auf **Speichern**. Das Formular wird zur Kategorie „Entwurf“ auf der Seite „Aufgaben“ hinzugefügt. Alle Änderungen, die Sie am Formular vorgenommen haben, werden gespeichert.

### Erneutes Öffnen von Entwurfskopien  {#reopen-a-draft-copy}

1. Wählen Sie auf der Seite „Aufgaben“ die Warteschlange **Entwürfe** aus und klicken Sie auf die Entwurfskopie des Formulars.

   Wenn das Formular eine Reihe von Feldern enthält, müssen Sie eventuell zu dem Feld navigieren, bei dem Sie die letzte Sitzung beendet haben.

## Prozesse zur Kategorie „Favoriten“ hinzufügen  {#adding-processes-to-the-favorites-category}

Sie können Prozesse zu Ihrer Kategorie „Favoriten“ hinzufügen. Durch das Festlegen von Favoriten können Sie alle Prozesse, die Sie häufig starten, in einer Kategorie gruppieren und sich so den Zugriff erleichtern.

>[!NOTE]
>
>Wenn Sie Prozesse meist beim Arbeiten mit AEM Forms Workspace starten, können Sie die Voreinstellung „Startposition“ so einstellen, dass beim Starten von AEM Forms Workspace automatisch die Kategorie „Favoriten“ angezeigt wird. Weitere Informationen finden Sie unter „Voreinstellungen verwalten“ in [Erste Schritte mit AEM Forms Workspace](/help/forms/using/getting-started-livecycle-html-workspace.md).

Um einen Prozess als Favoriten zu markieren, wählen Sie die Aufgabe in der Kategorie aus und klicken Sie auf den ungefüllten Stern. Der Stern wird golden. Um die Markierung eines Prozesses als Favorit zu entfernen, klicken Sie erneut auf den goldenen Stern.
