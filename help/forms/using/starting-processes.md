---
title: Starten von Prozessen
description: Verwendung von LiveCycle AEM Forms Workspace - Auswahl von Prozessen, Hinzufügen von Notizen und Anlagen, Speichern von Entwurfskopien und Hinzufügen zu Favoriten.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: b2a6ba3a-0f4c-44b1-8f9a-c15c6fb8c305
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1334'
ht-degree: 28%

---

# Starten von Prozessen {#starting-processes}

In AEM Forms Workspace werden Prozesse aufgrund der vom Administrator oder Prozessentwickler festgelegten Kategorien organisiert. Sie können häufig verwendete Prozesse auch in die Kategorie Favoriten einfügen, damit Sie sie schnell finden können.

Beim Starten eines Prozesses müssen Sie eventuell ein Formular ausfüllen, um einen von AEM Forms gesteuerten Geschäftsprozess zu starten. Wenn in einem Formular die Option &quot;Prepare Data Process&quot;verwendet wird, können einige Informationen vorab in ein leeres Formular eingefügt werden, wenn ein neuer Prozess initiiert wird.

Sie möchten beispielsweise einen neuen Computermonitor kaufen und starten daher einen Prozess mit dem Namen *Bestellung*. Wenn Sie den Prozess starten, wird ein Formular geöffnet, in dem Sie zur Eingabe von Details zum zu bestellenden Artikel aufgefordert werden. Ihr Name, Ihre Mitarbeiternummer und der Name des Vorgesetzten sind möglicherweise bereits im Formular vorausgefüllt. Wenn Sie die Anfrage senden, wird ein Geschäftsprozess initiiert. Basierend auf der Prozessdefinition leitet der Server die Anfrage automatisch an Ihren Manager weiter. Die Aufgabe wird in der Aufgabenliste Ihres Managers angezeigt. Wenn Ihr Manager die Anforderung genehmigt, leitet der Arbeitsablauf für Formulare die Anforderung an die Einkaufsabteilung weiter und sendet Ihnen eine E-Mail-Benachrichtigung.

## Zu startende Prozesse auswählen {#selecting-processes-to-start}

Sie können einen Prozess auswählen, um ihn zu starten oder weitere Informationen dazu anzuzeigen.

Wenn Sie einen zu startenden Prozess auswählen, müssen Sie möglicherweise ein Formular ausfüllen, das diesem Prozess zugeordnet ist. Durch Senden des Formulars wird der Prozess gestartet.

Formulare in verschiedenen Arten von Dateiformaten werden unterstützt, einschließlich Adobe PDF-, HTML- und SWF-Dateien. Ein Formular kann wie ein herkömmliches druckbares oder webbasiertes Formular aussehen oder Sie durch eine Reihe von Bereichen im Assistentenformat führen, um Informationen zu sammeln.

Wenn das Formular und der Prozess dies zulassen, können Sie das Formular auch offline speichern, ausfüllen und dann senden, um die Aufgabe abzuschließen. Wenn das Formular gesendet wird, wird Ihr E-Mail-Client mit der entsprechenden Server-E-Mail-Adresse gestartet, wenn der E-Mail-Endpunkt konfiguriert ist. Sie können das ausgefüllte Formular dann per E-Mail an den Server senden.

Wenn Sie einen Prozess auswählen, werden die Registerkarte Formular und Details angezeigt. Wenn der Prozess es Ihnen ermöglicht, Notizen oder Anlagen hinzuzufügen, werden auch die Registerkarten &quot;Anlagen&quot;und &quot;Notizen&quot;angezeigt. Wenn Sie die Zusammenfassungs-URL mit dem Prozess konfiguriert haben, wird die Registerkarte Zusammenfassung ebenfalls angezeigt. Auf der Registerkarte Forms wird das zugehörige Formular angezeigt. Auf der Registerkarte Details werden Informationen über die aktuelle Aufgabe und den Prozess angezeigt, zu dem sie gehört.

### Geschäftsprozess starten {#start-a-business-process}

1. Wählen Sie auf der Seite Prozess starten in der Liste auf der linken Seite eine Kategorie aus. Alle Prozesse, auf die Sie in der Kategorie Zugriff haben, werden rechts angezeigt.

   >[!NOTE]
   >
   >Wenn der Kategorienbereich ausgeblendet ist, klicken Sie auf „Kategorien öffnen“ im linken oberen Bereich von AEM Forms Workspace, um den Bereich zu öffnen.

1. Wählen Sie einen Prozess durch Klicken auf eine Aufgabe aus. Das dem Prozess zugeordnete Formular wird auf der Registerkarte Formular geöffnet.

   Jedes Formular in einem Prozess hat eine eindeutige URL. Sie können die eindeutige URL verwenden, um den HTML Workspace direkt mit dem spezifischen Prozess und Formular zu starten. Das Format der URL lautet https://&lt;server>:&lt;port>/lc/libs/ws/index.html#/startprocess/&lt;ApplicationName>%2F&lt;ProcessName>. Die Zeichenfolge &lt;ApplicationName>%2F&lt;ProcessName> ist immer URL-kodiert. Eine Beispiel-URL ist http://localhost:8080/lc/libs/ws/index.html#/startprocess/MyApplication%2FNewProcess. Die Zeichenfolge ApplicationName%2FProcessName im Beispiel ist URL-kodiert.

1. Füllen Sie das Formular entsprechend den zugehörigen Anweisungen aus. Klicken Sie ggf. auf **Maximieren**, um den sichtbaren Bereich des Formulars zu vergrößern.
1. Wenn die Registerkarte &quot;Anlagen&quot;verfügbar ist, fügen Sie nach Bedarf Anlagen hinzu.
1. Wenn die Registerkarte &quot;Notizen&quot;verfügbar ist, geben Sie bei Bedarf Notizen an.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf die Schaltfläche Senden im Formular, wenn das Formular über eine Senden -Schaltfläche verfügt.
   * Klicken Sie auf „Vervollständigen“ unterhalb des Formulars, wenn das Formular keine Schaltfläche „Senden“ hat.

   Process Management startet den Prozess und leitet das Formular an die Aufgabenlisten der entsprechenden Personen weiter, die die nächste Aufgabe im Prozess abschließen müssen.

   Wenn Sie ein Formular schließen müssen, bevor Sie es senden, und ohne die eingegebenen Daten zu verlieren, speichern Sie den Entwurf und schließen Sie es später ab, wenn der Prozess dies zulässt. Wenn das Formular und der Prozess dies zulassen, können Sie auch auf **Offline** und senden Sie es später von Adobe® Reader® oder Adobe® Acrobat® Professional oder Acrobat Standard.

   >[!NOTE]
   >
   >Die Offline-Option ist nur für PDF forms verfügbar.

## Notizen und Anlagen hinzufügen {#adding-notes-and-attachments}

Sie können einem Prozess Notizen und Dateianlagen hinzufügen, wenn der Prozess dies zulässt. Sie können anderen Benutzern Berechtigungen erteilen, die am Prozess teilnehmen, um die Notizen oder Anlagen anzuzeigen, zu aktualisieren und zu löschen.

### Notiz hinzufügen {#add-a-note}

Sie können mehrere Notizen hinzufügen, die geschriebenen Notizen bearbeiten und sie löschen. Jeder Notiz sind ein Titel, eine Beschreibung und eine Zugriffsberechtigung zugeordnet. Sie können eine der folgenden Zugriffsberechtigungen für eine Notiz festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Öffnen Sie eine Aufgabe und klicken Sie auf die Registerkarte **Notizen**, wenn der Prozess es zulässt.
1. Geben Sie einen Titel für die Notiz im **Titel** und geben Sie den Text der Notiz im **Hinweis** ankreuzen.
1. Wählen Sie die **Berechtigungen** -Ebene für die Notiz für andere Benutzer, die am Prozess teilnehmen.
1. Klicken Sie auf **OK**. An das Formular wird eine Textdatei mit Ihrer Notiz angehängt. Sie können eine Notiz aktualisieren, indem Sie darauf klicken und den Text direkt ändern. Sie können eine Notiz löschen, indem Sie auf die Schaltfläche **Löschen** ![Image of a trash can](assets/icondelete.png) neben der Notiz klicken.

### Anlage hinzufügen {#add-an-attachment}

Sie können auch Kommentare zum Anhang hinzufügen. Sie können eine der folgenden Zugriffsberechtigungen für einen Anhang festlegen:

* Schreibgeschützt (die Standardberechtigung)
* Lesen/Bearbeiten/Löschen
* Lesen/Bearbeiten
* Lesen/Löschen
* Kein Zugriff

1. Klicken Sie auf die Registerkarte **Anlagen** und wählen Sie **Anlage**.
1. Klicks **Durchsuchen** , um die anzuhängende Datei auszuwählen.
1. Wählen Sie die **Berechtigungsebene** des Anhangs für andere Benutzende aus, die an dem Prozess beteiligt sind. Wenn Sie die **Leseberechtigung** aktivieren, können andere Benutzende die Datei lokal speichern. Wenn Sie eine der Bearbeitungsberechtigungen auswählen, können andere Benutzende auch eine neue Datei hochladen, um Ihren Anhang durch sie zu ersetzen.
1. Klicken Sie auf **OK**. Die Datei wird an das Formular angehängt. Sie können eine Datei löschen, indem Sie auf die Schaltfläche **Löschen** ![Image of a trash can](assets/icondelete.png) neben dem Anhang klicken.

## Speichern von Formularentwürfen {#saving-draft-copies-of-forms}

Wenn Sie ein Formular später ausfüllen und senden müssen, können Sie den Entwurf eines Formulars speichern, damit Sie Ihre vorhandene Arbeit nicht verlieren. Entwurfskopien werden der Kategorie &quot;Entwürfe&quot;auf der Seite &quot;Aufgaben&quot;hinzugefügt.

Nachdem Sie ein Formular erneut öffnen und senden, wird der Entwurf aus der Kategorie &quot;Entwürfe&quot;entfernt.

Außerdem können Sie Workspace so konfigurieren, dass Informationen, die von einem Benutzer als Entwurf eingegeben wurden, automatisch gespeichert werden. Weitere Informationen finden Sie unter [Verwalten von Voreinstellungen](/help/forms/using/getting-started-livecycle-html-workspace.md).

>[!NOTE]
>
>Die Schaltfläche &quot;Speichern&quot;ist für einige Formulare je nach dem Prozess, mit dem sie verknüpft ist, nicht verfügbar.

### Entwurfskopien speichern {#save-a-draft-copy}

1. Klicken Sie auf **Speichern** in der linken unteren Ecke einer beliebigen Registerkarte. Das Formular wird der Kategorie &quot;Entwürfe&quot;auf Ihrer Seite &quot;Aufgaben&quot;hinzugefügt. Alle Änderungen, die Sie am Formular vorgenommen haben, werden gespeichert.

### Entwurfskopien erneut öffnen {#reopen-a-draft-copy}

1. Wählen Sie auf der Seite Aufgaben die **Entwürfe** und klicken Sie auf den Entwurf der Kopie des Formulars.

   Wenn das Formular eine Reihe von Bedienfeldern enthält, müssen Sie möglicherweise zum Bedienfeld wechseln, in dem Sie die letzte Sitzung beendet haben.

## Hinzufügen von Prozessen zur Kategorie &quot;Favoriten&quot; {#adding-processes-to-the-favorites-category}

Sie können beliebige Prozesse zu Ihrer Favoritenkategorie hinzufügen. Durch Festlegen von Favoriten können Sie alle häufig gestarteten Prozesse in einer Kategorie gruppieren, sodass Sie sie schnell finden können.

>[!NOTE]
>
>Wenn Sie Prozesse meist beim Arbeiten mit AEM Forms Workspace starten, können Sie die Voreinstellung „Startposition“ so einstellen, dass beim Starten von AEM Forms Workspace automatisch die Kategorie „Favoriten“ angezeigt wird. Weitere Informationen finden Sie unter Verwalten von Voreinstellungen unter [Erste Schritte mit AEM Forms Workspace](/help/forms/using/getting-started-livecycle-html-workspace.md).

Um einen Prozess als Favoriten zu markieren, wählen Sie die Aufgabe in ihrer Kategorie aus und klicken Sie auf den hohlen Stern. Der Stern wird golden. Um die Markierung eines Prozesses als Favoriten zu entfernen, klicken Sie erneut auf den goldenen Stern.
