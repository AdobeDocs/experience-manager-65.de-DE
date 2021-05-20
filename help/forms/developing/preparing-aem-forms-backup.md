---
title: Vorbereiten von AEM Forms für das Backup
seo-title: Vorbereiten von AEM Forms für das Backup
description: Erfahren Sie, wie Sie den Sicherungs- und Wiederherstellungsdienst verwenden, um den Sicherungsmodus für AEM Forms-Server mithilfe der Java-API und der Web Service-API zu starten und zu verlassen.
seo-description: Erfahren Sie, wie Sie den Sicherungs- und Wiederherstellungsdienst verwenden, um den Sicherungsmodus für AEM Forms-Server mithilfe der Java-API und der Web Service-API zu starten und zu verlassen.
uuid: b8ef2bed-62e2-4000-b55a-30d2fc398a5f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e747147e-e96d-43c7-87b3-55947eef81f5
role: Developer
exl-id: aeab003d-ba64-4760-9c56-44638501e9ff
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2554'
ht-degree: 2%

---

# Vorbereiten von AEM Forms für das Backup {#preparing-aem-forms-for-backup}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Über den Sicherungs- und Wiederherstellungsdienst {#about-the-backup-and-restore-service}

Mit dem Sicherungs- und Wiederherstellungsdienst können Sie AEM Forms in den Sicherungsmodus *stellen, der die Durchführung von Hot-Backups ermöglicht.* Der Sicherungs- und Wiederherstellungsdienst führt keine Sicherung von AEM Forms durch oder stellt das System wieder her. Stattdessen versetzt es Ihren Server in einen Status, der konsistente und zuverlässige Backups ermöglicht, während der Server weiterhin ausgeführt werden kann. Sie sind für die Aktionen zum Sichern des globalen Dokumentenspeichers (GDS) und der mit dem Formularserver verbundenen Datenbank verantwortlich. Der globale Dokumentenspeicher ist ein Ordner zum Speichern von Dateien, die in einem langlebigen Prozess verwendet werden.

Der Sicherungsmodus ist ein Status, in den der Server wechselt, sodass Dateien im globalen Dokumentenspeicher während eines Sicherungsverfahrens nicht bereinigt werden. Stattdessen werden Unterverzeichnisse im Ordner des globalen Dokumentenspeichers erstellt, um einen Datensatz mit Dateien zu speichern, die nach Abschluss des Speichersicherungsmodus bereinigt werden sollen. Eine Datei soll Systemneustarts überleben und kann Tage oder sogar Jahre umfassen. Diese Dateien sind ein wichtiger Teil des Gesamtstatus des Formularservers und können PDF-Dateien, Richtlinien oder Formularvorlagen enthalten. Wenn eine dieser Dateien verloren geht oder beschädigt wird, können die Prozesse auf dem Formularserver instabil werden und Daten gehen verloren.

Sie können Snapshot-Sicherungen durchführen, bei denen Sie in der Regel für einen bestimmten Zeitraum in den Sicherungsmodus wechseln und dann den Sicherungsmodus beenden, nachdem Sie Ihre Backup-Aktivitäten abgeschlossen haben. Der Sicherungsmodus muss deaktiviert werden, damit Dateien aus dem globalen Dokumentenspeicher gelöscht werden können, damit sie nicht unnötig groß werden. Sie können den Sicherungsmodus entweder explizit beenden oder auf den Ablauf einer Sicherungsmodussitzung warten.

Sie können Ihren Server auch im kontinuierlichen Sicherungsmodus belassen, was typisch für Sicherungsstrategien für kontinuierliche Sicherungen oder kontinuierliche Systemabdeckung ist. Der kontinuierliche Sicherungsmodus zeigt an, dass sich das System immer im Sicherungsmodus befindet, wobei eine neue Sicherungsmodussitzung ausgelöst wird, sobald die vorherige Sitzung veröffentlicht wurde. Im kontinuierlichen Sicherungsmodus wird eine Datei nach zwei Sicherungsmodussitzungen bereinigt und nicht mehr referenziert.

Sie können den Sicherungs- und Wiederherstellungsdienst verwenden, um bestehende Anwendungen oder neue Anwendungen hinzuzufügen, die Sie erstellen, um Sicherungen des GDS oder der Datenbank durchzuführen, die mit dem Formularserver verbunden ist.

>[!NOTE]
>
>Wie bei allen anderen Aspekten Ihrer AEM Forms-Implementierung sollte Ihre Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Staging-Umgebung entwickelt und getestet werden, bevor sie in der Produktion verwendet wird, um sicherzustellen, dass die gesamte Lösung erwartungsgemäß und ohne Datenverlust funktioniert.

Sie können diese Aufgaben mit dem Backup and Restore-Dienst ausführen:

* Wechseln Sie in den Sicherungsmodus.
* Deaktivieren Sie den Sicherungsmodus.

>[!NOTE]
>
>Weitere Informationen dazu, was bei der Durchführung von Sicherungen für AEM Forms zu beachten ist, finden Sie unter [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Wechseln zum Sicherungsmodus auf dem Formularserver {#entering-backup-mode-on-the-forms-server}

Sie wechseln in den Sicherungsmodus, um Hot-Backups eines Formularservers zu ermöglichen. Wenn Sie in den Sicherungsmodus wechseln, geben Sie die folgenden Informationen basierend auf den Sicherungsverfahren Ihres Unternehmens an:

* Eine eindeutige Beschriftung zur Identifizierung der Sicherungsmodussitzung, die für Ihre Sicherungsprozesse nützlich sein kann.
* Der Zeitpunkt, zu dem das Backup-Verfahren abgeschlossen sein soll.
* Ein Flag, das angibt, ob der kontinuierliche Sicherungsmodus ausgeführt werden soll. Dies ist nur nützlich, wenn Sie rollierende Sicherungen durchführen.

Bevor Sie Anwendungen schreiben, um in den Sicherungsmodus zu wechseln, sollten Sie die Sicherungsverfahren verstehen, die nach dem Versetzen des Formularservers in den Sicherungsmodus verwendet werden. Weitere Informationen dazu, was bei der Durchführung von Sicherungen für AEM Forms zu beachten ist, finden Sie unter [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie eine Anwendung, die in den Sicherungsmodus wechselt:

1. Projektdateien einschließen.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Bestimmen Sie einen eindeutigen Titel, die Dauer der Sicherung und ob der kontinuierliche Sicherungsmodus aktiviert ist.
1. Wechseln Sie in den Sicherungsmodus.
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung auf dem Server ab.
1. Führen Sie eine Sicherung des globalen Dokumentenspeichers (GDS) und der Datenbank durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien müssen in Ihr Projekt aufgenommen werden, damit Sie Ihren Code ordnungsgemäß kompilieren und die Sicherungs- und Wiederherstellungsdienst-API verwenden können.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Sicherungsmodus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, das die Sicherungs- und Wiederherstellungsdienst-API verwendet.

**Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer für die Durchführung der Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.**

Bevor Sie in den Sicherungsmodus wechseln, sollten Sie sich für eine eindeutige Beschriftung entscheiden, die Zeitdauer festlegen, die Sie für die Durchführung der Sicherung zuweisen möchten, und entscheiden, ob der Formularserver im Sicherungsmodus verbleiben soll. Diese Überlegungen sind wichtig, um sie in die von Ihrem Unternehmen eingerichteten Sicherungsverfahren zu integrieren. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Sicherungsmodus aktivieren**

Wechseln Sie in den Sicherungsmodus mit den Parametern, die den Sicherungsverfahren in Ihrem Unternehmen entsprechen.

**Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server**

Nachdem Sie den Sicherungsmodus gestartet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Ihre Sicherungsverfahren verwendet werden.

**Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen**

Nachdem Sie den Sicherungsmodus erfolgreich aktiviert haben, können Sie eine Sicherung des globalen Dokumentenspeichers (GDS) und der Datenbank durchführen, mit der der Formularserver verbunden ist. Dieser Schritt ist für Ihr Unternehmen spezifisch, da Sie diesen Schritt manuell ausführen können oder andere Tools zum Ausführen des Sicherungsverfahrens ausführen können.

### Wechseln Sie mithilfe der Java-API {#enter-backup-mode-using-the-java-api} in den Sicherungsmodus.

Wechseln Sie mithilfe der Sicherungs- und Wiederherstellungsdienst-API in den Sicherungsmodus:

1. Projektdateien einschließen

   Schließen Sie die erforderlichen Client-JAR-Dateien wie adobe-backup-restore-client-sdk.jar in den Klassenpfad Ihres Java-Projekts ein. Um die Java-Client-Anwendung zu erstellen, müssen die folgenden JAR-Dateien zum Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory`-Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer für die Durchführung der Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.

   Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer, die Sie für die Sicherung zuweisen möchten, und entscheiden Sie, ob der Formularserver im kontinuierlichen Sicherungsmodus verbleiben soll.

1. Sicherungsmodus aktivieren

   Wechseln Sie in den Sicherungsmodus, indem Sie die Methode `enterBackupMode` mit den folgenden Parametern aufrufen:

   * Ein `String` -Wert, der eine eindeutige, für Menschen lesbare Bezeichnung angibt, die die Sicherungsmodussitzung identifiziert. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Ein `int` -Wert, der die Anzahl der Minuten angibt, die im Sicherungsmodus verbleiben sollen. Sie können einen Wert von `1` bis `10080` (die Anzahl der Minuten in einer Woche) angeben. Dieser Wert wird bei Verwendung des kontinuierlichen Sicherungsmodus ignoriert.
   * Ein `Boolean` -Wert, der angibt, ob der kontinuierliche Sicherungsmodus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Sicherungsmodus aktiviert ist. Im kontinuierlichen Sicherungsmodus wird der Wert ignoriert, den Sie für die Anzahl der Minuten angeben, die im Sicherungsmodus verbleiben sollen.

      Der kontinuierliche Sicherungsmodus bedeutet, dass eine neue Sicherungsmodussitzung gestartet wird, nachdem die aktuelle Sitzung abgeschlossen ist. Der Wert `False` bedeutet, dass der kontinuierliche Sicherungsmodus nicht verwendet wird und dass nach dem Verlassen des Sicherungsmodus das Bereinigen von Dateien aus dem globalen Dokumentenspeicher fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen mit dem `BackupModeEntryResult` -Objekt ab, das nach dem Aufrufen der `enterBackupMode` -Methode zurückgegeben wird. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Titel, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Backup-Verfahren nützlich sein.

1. Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen

   Sichern Sie den globalen Dokumentenspeicher (GDS) und die Datenbank, mit der Ihr Formularserver verbunden ist. Die Aktionen zum Ausführen der Sicherung sind nicht Teil des AEM Forms SDK und können sogar manuelle Schritte für die Sicherungsverfahren in Ihrem Unternehmen enthalten.

### Wechseln Sie mithilfe der Webdienst-API {#enter-backup-mode-using-the-web-service-api} in den Sicherungsmodus.

Wechseln Sie mithilfe des von der Sicherungs- und Wiederherstellungsdienst-API bereitgestellten Webdienstes in den Sicherungsmodus:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Sicherungs- und Wiederherstellungs-Service-API-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines BackupService Client-API-Objekts

   Erstellen Sie mit der Microsoft .NET-Clientassembly ein `BackupServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen und die Anmeldeinformationen mithilfe der `Credentials`-Methode angeben.

1. Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer für die Durchführung der Sicherung und entscheiden Sie, ob Sie sich im kontinuierlichen Sicherungsmodus befinden.

   Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer, die Sie für die Sicherung zuweisen möchten, und entscheiden Sie, ob der Formularserver im kontinuierlichen Sicherungsmodus verbleiben soll.

1. Sicherungsmodus aktivieren

   Um in den Sicherungsmodus zu wechseln, rufen Sie die Methode enterBackupMode auf und übergeben Sie die folgenden Werte:

   * Ein `String` -Wert, der eine eindeutige, für Menschen lesbare Bezeichnung angibt, die die Sicherungsmodussitzung identifiziert. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Ein `Uint32` -Wert, der die Anzahl der Minuten angibt, die im Sicherungsmodus verbleiben sollen. Sie können einen Wert von `1` bis `10080` (Anzahl der Minuten in einer Woche) angeben. Dieser Wert wird bei Verwendung des kontinuierlichen Sicherungsmodus ignoriert.
   * Ein `Boolean` -Wert, der angibt, ob der kontinuierliche Sicherungsmodus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Sicherungsmodus aktiviert ist. Im kontinuierlichen Sicherungsmodus wird der Wert ignoriert, den Sie für die Anzahl der Minuten angeben, die im Sicherungsmodus verbleiben sollen. Der kontinuierliche Sicherungsmodus bedeutet, dass eine neue Sicherungsmodussitzung gestartet wird, nachdem die aktuelle Sitzung abgeschlossen ist.

      Der Wert `False` bedeutet, dass der kontinuierliche Sicherungsmodus nicht verwendet wird und dass nach dem Verlassen des Sicherungsmodus das Bereinigen von Dateien aus dem globalen Dokumentenspeicher fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen zur Sicherungsmodussitzung ab, nachdem Sie die Methode &quot;enterBackupMode&quot;aus dem zurückgegebenen BackupModeEntryResult aufgerufen haben, um zu überprüfen, ob es erfolgreich war. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Titel, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Backup-Verfahren nützlich sein.

1. Sicherung des globalen Dokumentenspeichers und der Datenbank durchführen

   Sichern Sie den globalen Dokumentenspeicher (GDS) und die Datenbank, mit der Ihr Formularserver verbunden ist. Die Aktionen zum Ausführen der Sicherung sind nicht Teil des AEM Forms SDK und können sogar manuelle Schritte für die Sicherungsverfahren in Ihrem Unternehmen enthalten.

## Verlassen des Sicherungsmodus auf dem Formularserver {#leaving-backup-mode-on-the-forms-server}

Sie verlassen den Sicherungsmodus, damit der Formularserver die Bereinigung der Dateien aus dem globalen Dokumentenspeicher (GDS) auf dem Formularserver fortsetzt.

Bevor Sie Anwendungen schreiben, um in den Urlaubsmodus zu wechseln, sollten Sie die Sicherungsverfahren verstehen, die mit AEM Forms verwendet werden. Weitere Informationen dazu, was bei der Durchführung von Sicherungen für AEM Forms zu beachten ist, finden Sie unter [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Weitere Informationen zum Sicherungs- und Wiederherstellungsdienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um den Sicherungsmodus zu beenden, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Deaktivieren Sie den Sicherungsmodus.
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung ab, die auf dem Formularserver ausgeführt wurde.

**Projektdateien einschließen**

Schließen Sie alle erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien sind wichtig, um Ihren Code ordnungsgemäß zu kompilieren und die Sicherungs- und Wiederherstellungsdienst-API zu verwenden.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Sicherungsmodus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, das die Sicherungs- und Wiederherstellungsdienst-API verwendet.

**Sicherungsmodus beenden**

Behalten Sie den Sicherungsmodus bei, um die normale Bereinigung der Dateien aus dem globalen Dokumentenspeicher (GDS) fortzusetzen. Bevor Sie den Sicherungsmodus beenden, sollten Sie sicherstellen, dass Ihre Sicherungsverfahren abgeschlossen sind.

**Abrufen von Informationen zur beendeten Sicherungsmodussitzung**

Nachdem Sie den Sicherungsmodus beendet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Ihre Sicherungsverfahren verwendet werden.

### Den Sicherungsmodus mithilfe der Java-API deaktivieren {#leave-backup-mode-using-the-java-api}

Deaktivieren Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungsdienst-API (Java):

1. Projektdateien einschließen

   Schließen Sie die erforderlichen Client-JAR-Dateien wie adobe-backup-restore-client-sdk.jar in den Klassenpfad Ihres Java-Projekts ein. Zum Erstellen der Java-Clientanwendung müssen die folgenden JAR-Dateien zum Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory`-Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService` -Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory` -Objekt als Parameter übergeben.

1. Sicherungsmodus aktivieren

   Behalten Sie den Sicherungsmodus bei, indem Sie die Methode `leaveBackupMode` aufrufen.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen über den Vorgang mit dem zurückgegebenen `BackupModeResult` -Objekt ab. Die Informationen, die Sie nach dem Starten des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Titel, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Backup-Verfahren nützlich sein.

### Behalten Sie den Sicherungsmodus mithilfe der Webdienst-API {#leave-backup-mode-using-the-web-service-api} bei.

Verlassen Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungsdienst-API (Webdienst):

1. Projektdateien einschließen

   Um Webdienste zu verwenden, müssen Sie sicherstellen, dass Sie die Proxy-Dateien einschließen. Führen Sie diese Schritte aus, um Ihr Projekt für die Verwendung der Sicherungs- und Wiederherstellungsdienst-API als Webdienst zu konfigurieren.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Sicherungs- und Wiederherstellungs-Service-API-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. Erstellen eines BackupService Client-API-Objekts

   Erstellen Sie mit der Microsoft .NET-Clientassembly ein `BackupServiceService`-Objekt, indem Sie seinen Standardkonstruktor aufrufen.

1. Sicherungsmodus aktivieren

   Deaktivieren Sie den Sicherungsmodus, indem Sie den Webdienstvorgang `leaveBackupMode` aufrufen.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie die Sicherungsmoduskennung nach dem Vorgang ab, um sicherzustellen, dass sie erfolgreich war. Die Informationen, die Sie nach dem Verlassen des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein.
