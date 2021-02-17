---
title: AEM Forms für Sicherung vorbereiten
seo-title: AEM Forms für Sicherung vorbereiten
description: Erfahren Sie, wie Sie den Sicherungs- und Wiederherstellungsdienst verwenden, um den Sicherungsmodus für AEM Forms-Server mit der Java-API und der Web-Service-API zu starten und zu deaktivieren.
seo-description: Erfahren Sie, wie Sie den Sicherungs- und Wiederherstellungsdienst verwenden, um den Sicherungsmodus für AEM Forms-Server mit der Java-API und der Web-Service-API zu starten und zu deaktivieren.
uuid: b8ef2bed-62e2-4000-b55a-30d2fc398a5f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e747147e-e96d-43c7-87b3-55947eef81f5
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '2540'
ht-degree: 2%

---


# Vorbereiten von AEM Forms für Sicherung {#preparing-aem-forms-for-backup}

## Info zum Sicherungs- und Wiederherstellungsdienst {#about-the-backup-and-restore-service}

Mit dem Sicherungs- und Wiederherstellungsdienst können Sie AEM Forms in den Sicherungsmodus *setzen, der die Ausführung von Hot Backups ermöglicht.* Der Backup and Restore-Dienst führt keine Sicherung von AEM Forms durch oder stellt Ihr System wieder her. Stattdessen versetzt es Ihren Server in einen Status für konsistente und zuverlässige Backups, während der Server weiterhin ausgeführt werden kann. Sie sind für die Aktionen zur Sicherung der Datenspeicherung des globalen Dokuments (GDS) und der mit dem Formularserver verbundenen Datenbank verantwortlich. Der globale Dokumentenspeicher ist ein Ordner zum Speichern von Dateien, die in einem Prozess mit langer Lebensdauer verwendet werden.

Der Sicherungsmodus ist ein vom Server eingegebener Zustand, sodass Dateien im globalen Dokumentenspeicher nicht bereinigt werden, während ein Sicherungsvorgang stattfindet. Stattdessen werden Unterordner im Ordner des globalen Dokumentenspeichers erstellt, um einen Datensatz der Dateien zu verwalten, die nach Beendigung des Sicherungsmodus bereinigt werden sollen. Eine Datei soll Systemneustarts überleben und kann Tage oder sogar Jahre umfassen. Diese Dateien sind ein wichtiger Bestandteil des Gesamtstatus des Formularservers und können PDF-Dateien, Richtlinien oder Formularvorlagen enthalten. Wenn eine dieser Dateien verloren geht oder beschädigt wird, können die Prozesse auf dem Formularserver instabil werden und Daten verloren gehen.

Sie können Snapshot-Sicherungen durchführen, bei denen Sie in der Regel für einen bestimmten Zeitraum in den Sicherungsmodus wechseln und dann den Sicherungsmodus deaktivieren, nachdem Sie die Backup-Aktivitäten abgeschlossen haben. Der Sicherungsmodus muss beendet werden, damit Dateien aus dem globalen Dokumentenspeicher entfernt werden können, um sicherzustellen, dass sie nicht unnötig groß werden. Sie können den Sicherungsmodus entweder explizit deaktivieren oder auf den Ablauf einer Sicherungsmodussitzung warten.

Sie können Ihren Server auch im kontinuierlichen Sicherungsmodus belassen, was typischerweise für Sicherungsstrategien für kontinuierliche Sicherungen oder kontinuierliche Systemabdeckung gilt. Der kontinuierliche Sicherungsmodus gibt an, dass sich das System immer im Sicherungsmodus befindet, wobei eine neue Sicherungsmodussitzung ausgelöst wird, sobald die vorherige Sitzung beendet ist. Im kontinuierlichen Sicherungsmodus wird eine Datei nach zwei Sicherungsmodussitzungen bereinigt und nicht mehr referenziert.

Sie können den Sicherungs- und Wiederherstellungsdienst verwenden, um bestehenden Anwendungen oder neuen Anwendungen, die Sie erstellen, hinzuzufügen, um Sicherungen des globalen Dokumentenspeichers oder der Datenbank durchzuführen, die mit dem Formularserver verbunden sind.

>[!NOTE]
>
>Wie bei allen anderen Aspekten Ihrer AEM Forms-Implementierung sollte Ihre Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Staging-Umgebung entwickelt und getestet werden, bevor sie in der Produktion verwendet wird, um sicherzustellen, dass die gesamte Lösung erwartungsgemäß und ohne Datenverlust funktioniert.

Sie können diese Aufgaben mit dem Backup and Restore-Dienst ausführen:

* Starten Sie den Sicherungsmodus.
* Sicherungsmodus deaktivieren

>[!NOTE]
>
>Weitere Informationen dazu, was Sie bei der Durchführung von Sicherungen für AEM Forms beachten sollten, finden Sie unter [Administration help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Eingeben des Sicherungsmodus auf dem Formularserver {#entering-backup-mode-on-the-forms-server}

Sie wechseln in den Sicherungsmodus, um Hot Backups des Formularservers zuzulassen. Wenn Sie in den Sicherungsmodus wechseln, geben Sie die folgenden Informationen basierend auf den Sicherungsvorgängen in Ihrem Unternehmen an:

* Eine eindeutige Bezeichnung zur Identifizierung der Sicherungsmodussitzung, die für Ihre Sicherungsvorgänge nützlich sein kann.
* Die Zeit, die für den Abschluss des Sicherungsverfahrens erforderlich ist.
* Eine Flag, die angibt, ob Sie sich im kontinuierlichen Sicherungsmodus befinden, was nur nützlich ist, wenn Sie rollierende Sicherungen durchführen.

Bevor Sie Anwendungen schreiben, die in den Sicherungsmodus versetzt werden, sollten Sie sich mit den Sicherungsverfahren vertraut machen, die nach dem Versetzen des Formularservers in den Sicherungsmodus verwendet werden. Weitere Informationen dazu, was Sie bei der Durchführung von Sicherungen für AEM Forms beachten sollten, finden Sie unter [Administration help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie eine Anwendung, die in den Sicherungsmodus wechselt:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Legen Sie eine eindeutige Beschriftung fest, wie lange die Sicherung durchgeführt werden soll und ob sie sich im kontinuierlichen Sicherungsmodus befindet.
1. Starten Sie den Sicherungsmodus.
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung auf dem Server ab.
1. Führen Sie eine Sicherung des globalen Dokumentenspeichers (Globaler Datenspeicher) und der Datenbank durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien sind wichtig, damit sie in Ihr Projekt aufgenommen werden können, damit Sie Ihren Code ordnungsgemäß kompilieren und die Sicherungs- und Wiederherstellungs-Dienst-API verwenden können.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Sicherungsmodus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, um die Sicherungs- und Wiederherstellungs-Dienst-API zu verwenden.

**Entscheiden Sie über eine eindeutige Beschriftung, bestimmen Sie die Zeitdauer für die Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.**

Bevor Sie in den Sicherungsmodus wechseln, sollten Sie sich für eine eindeutige Beschriftung entscheiden, die Zeitdauer festlegen, die Sie für die Durchführung der Sicherung zuweisen möchten, und entscheiden, ob der Formularserver im Sicherungsmodus bleiben soll. Diese Überlegungen sind wichtig, um sie in die von Ihrem Unternehmen eingerichteten Sicherungsverfahren zu integrieren. (Siehe [Administration help](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Sicherungsmodus aktivieren**

Starten Sie den Sicherungsmodus mit den Parametern, die mit den Sicherungsverfahren in Ihrem Unternehmen übereinstimmen.

**Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server**

Nachdem Sie den Sicherungsmodus gestartet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Ihre Sicherungsverfahren verwendet werden

**Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen**

Nach erfolgreichem Starten des Sicherungsmodus können Sie eine Sicherung der Datenspeicherung des globalen Dokuments (GDS) und der Datenbank durchführen, mit der der Formularserver verbunden ist. Dieser Schritt ist für Ihr Unternehmen spezifisch, da Sie diesen Schritt manuell durchführen können oder andere Werkzeuge zum Durchführen des Sicherungsverfahrens ausführen können.

### Starten Sie den Sicherungsmodus mit der Java-API {#enter-backup-mode-using-the-java-api}

Starten Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungs-Dienst-API:

1. Projektdateien einschließen

   Schließen Sie die erforderlichen JAR-Clientdateien, wie z. B. adobe-backup-restore-client-sdk.jar, in den Klassenpfad Ihres Java-Projekts ein. Um die Java-Clientanwendung zu erstellen, müssen die folgenden JAR-Dateien zum Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory`-Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Entscheiden Sie über eine eindeutige Beschriftung, bestimmen Sie die Zeitdauer für die Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.

   Entscheiden Sie sich für eine eindeutige Beschriftung, bestimmen Sie die Zeitdauer, die Sie für die Sicherung zuweisen möchten, und entscheiden Sie, ob der Formularserver im kontinuierlichen Sicherungsmodus bleiben soll.

1. Sicherungsmodus aktivieren

   Starten Sie den Sicherungsmodus, indem Sie die `enterBackupMode`-Methode mit den folgenden Parametern aufrufen:

   * Ein `String`-Wert, der eine eindeutige, für Menschen lesbare Beschriftung angibt, die die Sicherungsmodussitzung identifiziert. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Ein `int`-Wert, der die Anzahl der Minuten angibt, die im Sicherungsmodus verbleiben sollen. Sie können einen Wert zwischen `1` und `10080` (die Anzahl der Minuten in einer Woche) angeben. Dieser Wert wird bei Verwendung des kontinuierlichen Sicherungsmodus ignoriert.
   * Ein `Boolean`-Wert, der angibt, ob der kontinuierliche Sicherungsmodus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Sicherungsmodus aktiviert ist. Im kontinuierlichen Sicherungsmodus wird der Wert ignoriert, den Sie für die Anzahl der Minuten angeben, die im Sicherungsmodus verbleiben sollen.

      Der kontinuierliche Sicherungsmodus bedeutet, dass eine neue Sicherungsmodussitzung nach Abschluss der aktuellen Sitzung gestartet wird. Der Wert `False` bedeutet, dass der kontinuierliche Sicherungsmodus nicht verwendet wird und das Bereinigen von Dateien aus dem globalen Dokumentenspeicher nach dem Verlassen des Sicherungsmodus fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen mit dem `BackupModeEntryResult`-Objekt ab, das nach dem Aufrufen der `enterBackupMode`-Methode zurückgegeben wird. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können die Beschriftung, die Sicherungs-ID und die Beginn-Zeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

1. Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen

   Sichern Sie die Datenspeicherung des globalen Dokuments (GDS) und die Datenbank, mit der der Formularserver verbunden ist. Die Aktionen zum Durchführen der Sicherung sind nicht Teil des AEM Forms SDK und können sogar manuelle Schritte für die Sicherungsabläufe in Ihrem Unternehmen enthalten.

### Starten Sie den Sicherungsmodus mithilfe der Webdienst-API {#enter-backup-mode-using-the-web-service-api}

Starten Sie den Sicherungsmodus mithilfe des Webdiensts, der von der Sicherungs- und Wiederherstellungs-Dienst-API bereitgestellt wird:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL der Sicherungs- und Wiederherstellungs-Dienst-API verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines BackupService Client-API-Objekts

   Erstellen Sie mit der Microsoft .NET-Clientassembly ein `BackupServiceService`-Objekt, indem Sie den Standardkonstruktor aufrufen, und geben Sie die Anmeldeinformationen mit der `Credentials`-Methode an.

1. Entscheiden Sie über eine eindeutige Beschriftung, bestimmen Sie die Zeitdauer für die Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.

   Entscheiden Sie sich für eine eindeutige Beschriftung, bestimmen Sie die Zeitdauer, die Sie für die Sicherung zuweisen möchten, und entscheiden Sie, ob der Formularserver im kontinuierlichen Sicherungsmodus bleiben soll.

1. Sicherungsmodus aktivieren

   Um in den Sicherungsmodus zu wechseln, rufen Sie die Methode enterBackupMode auf und übergeben Sie die folgenden Werte:

   * Ein `String`-Wert, der eine eindeutige, für Menschen lesbare Beschriftung angibt, die die Sicherungsmodussitzung identifiziert. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Ein `Uint32`-Wert, der die Anzahl der Minuten angibt, die im Sicherungsmodus verbleiben sollen. Sie können einen Wert zwischen `1` und `10080` (Anzahl der Minuten in einer Woche) angeben. Dieser Wert wird bei Verwendung des kontinuierlichen Sicherungsmodus ignoriert.
   * Ein `Boolean`-Wert, der angibt, ob der kontinuierliche Sicherungsmodus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Sicherungsmodus aktiviert ist. Im kontinuierlichen Sicherungsmodus wird der Wert ignoriert, den Sie für die Anzahl der Minuten angeben, die im Sicherungsmodus verbleiben sollen. Der kontinuierliche Sicherungsmodus bedeutet, dass eine neue Sicherungsmodussitzung nach Abschluss der aktuellen Sitzung gestartet wird.

      Der Wert `False` bedeutet, dass der kontinuierliche Sicherungsmodus nicht verwendet wird und das Bereinigen von Dateien aus dem globalen Dokumentenspeicher nach dem Verlassen des Sicherungsmodus fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen zur Sicherungsmodussitzung ab, nachdem Sie die Methode enterBackupMode aus dem zurückgegebenen BackupModeEntryResult aufgerufen haben, um sicherzustellen, dass sie erfolgreich war. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können die Beschriftung, die Sicherungs-ID und die Beginn-Zeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

1. Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen

   Sichern Sie die Datenspeicherung des globalen Dokuments (GDS) und die Datenbank, mit der der Formularserver verbunden ist. Die Aktionen zum Durchführen der Sicherung sind nicht Teil des AEM Forms SDK und können sogar manuelle Schritte für die Sicherungsabläufe in Ihrem Unternehmen enthalten.

## Sicherungsmodus auf dem Formularserver {#leaving-backup-mode-on-the-forms-server} verlassen

Sie können den Sicherungsmodus deaktivieren, damit der Formularserver das Bereinigen der Dateien aus der Datenspeicherung des globalen Dokuments (GDS) auf dem Formularserver wieder aufnimmt.

Bevor Sie Anwendungen schreiben, die in den Urlaubsmodus wechseln, sollten Sie sich mit den Sicherungsverfahren vertraut machen, die mit AEM Forms verwendet werden. Weitere Informationen dazu, was Sie bei der Durchführung von Sicherungen für AEM Forms beachten sollten, finden Sie unter [Administration help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Gehen Sie wie folgt vor, um den Sicherungsmodus zu deaktivieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Sicherungsmodus deaktivieren
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung ab, die auf dem Formularserver ausgeführt wurde.

**Projektdateien einschließen**

Schließen Sie alle erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien sind wichtig für die korrekte Kompilierung Ihres Codes und die Verwendung der Sicherungs- und Wiederherstellungs-Dienst-API.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Sicherungsmodus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, um die Sicherungs- und Wiederherstellungs-Dienst-API zu verwenden.

**Sicherungsmodus verlassen**

Lassen Sie den Sicherungsmodus beendet, um das normale Bereinigen von Dateien aus der Datenspeicherung des globalen Dokuments (GDS) fortzusetzen. Bevor Sie den Sicherungsmodus beenden, sollten Sie sicherstellen, dass die Sicherungsverfahren abgeschlossen sind.

**Abrufen von Informationen zur beendeten Sicherungsmodussitzung**

Nachdem Sie den Sicherungsmodus beendet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Ihre Sicherungsverfahren verwendet werden.

### Sicherungsmodus mit der Java-API {#leave-backup-mode-using-the-java-api} deaktivieren

Beenden Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungs-Dienst-API (Java):

1. Projektdateien einschließen

   Schließen Sie die erforderlichen JAR-Clientdateien, wie z. B. adobe-backup-restore-client-sdk.jar, in den Klassenpfad Ihres Java-Projekts ein. Um eine Java-Clientanwendung zu erstellen, müssen die folgenden JAR-Dateien dem Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory`-Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt als Parameter übergeben.

1. Sicherungsmodus aktivieren

   Lassen Sie den Sicherungsmodus, indem Sie die `leaveBackupMode`-Methode aufrufen.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen zum Vorgang mit dem zurückgegebenen `BackupModeResult`-Objekt ab. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können die Beschriftung, die Sicherungs-ID und die Beginn-Zeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

### Sicherungsmodus mithilfe der Webdienst-API {#leave-backup-mode-using-the-web-service-api} deaktivieren

Beenden Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungs-Dienst-API (Webdienst):

1. Projektdateien einschließen

   Um Webdienste verwenden zu können, müssen Sie sicherstellen, dass die Proxydateien einbezogen werden. Führen Sie die folgenden Schritte aus, um Ihr Projekt für die Verwendung der Sicherungs- und Wiederherstellungs-Dienst-API als Webdienst zu konfigurieren.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL der Sicherungs- und Wiederherstellungs-Dienst-API verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines BackupService Client-API-Objekts

   Erstellen Sie mit der Microsoft .NET-Clientassembly ein `BackupServiceService`-Objekt, indem Sie dessen Standardkonstruktor aufrufen.

1. Sicherungsmodus aktivieren

   Lassen Sie den Sicherungsmodus, indem Sie den Webdienstvorgang `leaveBackupMode` aufrufen.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie die ID des Sicherungsmodus nach dem Vorgang ab, um sicherzustellen, dass sie erfolgreich war. Die Informationen, die Sie nach dem Verlassen des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein.

