---
title: Vorbereiten von AEM Forms für eine Sicherung
description: Erfahren Sie, wie Sie den Sicherungs- und Wiederherstellungs-Service verwenden, um den Sicherungsmodus für AEM Forms-Server mithilfe der Java-API und der Web Service-API zu starten und zu beenden.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: aeab003d-ba64-4760-9c56-44638501e9ff
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2484'
ht-degree: 82%

---

# Vorbereiten von AEM Forms für eine Sicherung {#preparing-aem-forms-for-backup}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Informationen zum Sicherungs- und Wiederherstellungs-Service {#about-the-backup-and-restore-service}

Mit dem Sicherungs- und Wiederherstellungs-Service können Sie AEM Forms in den *Sicherungsmodus* versetzen, wodurch Hot-Backups durchgeführt werden können. Der Sicherungs- und Wiederherstellungs-Service führt keine Sicherung von AEM Forms durch und stellt das System auch nicht wieder her. Stattdessen versetzt er den Server in einen Zustand, der konsistente und zuverlässige Sicherungen ermöglicht, während der Server weiterhin ausgeführt wird. Sie sind für die Aktionen zum Sichern des globalen Dokumentenspeichers (GDS) und der mit dem Forms-Server verbundenen Datenbank verantwortlich. Der globale Dokumentenspeicher ist ein Ordner zum Speichern von Dateien, die in einem langlebigen Prozess genutzt werden.

Der Sicherungsmodus ist ein Zustand, in den der Server versetzt wird, damit Dateien im globalen Dokumentenspeicher während eines Sicherungsverfahrens nicht bereinigt werden. Stattdessen werden Unterverzeichnisse im Ordner des globalen Dokumentenspeichers erstellt, um einen Datensatz der Dateien zu speichern, die nach Beendigung des Speichersicherungsmodus bereinigt werden sollen. Eine Datei soll Systemneustarts überdauern und kann Tage oder sogar Jahre umfassen. Diese Dateien sind ein wichtiger Bestandteil des Gesamtstatus des Forms-Servers und können PDF-Dateien, Richtlinien oder Formularvorlagen enthalten. Wenn eine dieser Dateien verloren geht oder beschädigt wird, können die Prozesse auf dem Forms-Server instabil werden und Daten gehen verloren.

Sie können Snapshot-Sicherungen durchführen, bei denen Sie in der Regel über einen bestimmten Zeitraum in den Sicherungsmodus wechseln und diesen beenden, nachdem Sie die Sicherungsaktivitäten abgeschlossen haben. Der Sicherungsmodus muss deaktiviert werden, damit Dateien aus dem globalen Dokumentenspeicher gelöscht werden können, sodass dieser nicht unnötig groß wird. Sie können den Sicherungsmodus entweder explizit beenden oder auf den Ablauf einer Sicherungsmodussitzung warten.

Sie können Ihren Server auch im permanenten Sicherungsmodus belassen, was typisch für Sicherungsstrategien für kontinuierliche Sicherungen oder eine kontinuierliche Systemabdeckung ist. Der kontinuierliche Sicherungsmodus gibt an, dass das System stets im Sicherungsmodus ist, wobei eine neue Sicherungsmodussitzung ausgelöst wird, sobald die vorherige Sitzung freigegeben wurde. Im permanenten Sicherungsmodus wird eine Datei nach zwei Sicherungsmodussitzungen bereinigt und nicht mehr referenziert.

Sie können den Sicherungs- und Wiederherstellungsdienst verwenden, um bestehende Anwendungen oder neue Anwendungen hinzuzufügen, die Sie erstellen, um Sicherungen des globalen Dokumentenspeichers oder der mit dem Forms-Server verbundenen Datenbank durchzuführen.

>[!NOTE]
>
>Wie auch bei allen anderen Aspekten einer AEM Forms-Implementierung gilt, dass die Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Testumgebung entwickelt und getestet werden muss, bevor sie in der Produktion zum Einsatz kommt. So wird sichergestellt, dass die gesamte Lösung wie erwartet und ohne Datenverlust funktioniert.

Sie können folgende Aufgaben mit dem Sicherungs- und Wiederherstellungs-Service ausführen:

* Aktivieren Sie den Sicherungsmodus.
* Deaktivieren Sie den Sicherungsmodus.

>[!NOTE]
>
>Weitere Informationen dazu, was bei der Durchführung von Sicherungen für AEM Forms zu beachten ist, finden Sie unter [Hilfe zur Administration](https://www.adobe.com/go/learn_aemforms_admin_63_de).

>[!NOTE]
>
>Weitere Informationen über den Service „Backup und Wiederherstellung“ finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Aufrufen des Sicherungsmodus auf dem Forms-Server {#entering-backup-mode-on-the-forms-server}

Sie wechseln in den Sicherungsmodus, um Hot-Backups eines Forms-Servers zu ermöglichen. Wenn Sie in den Sicherungsmodus wechseln, geben Sie die folgenden Informationen basierend auf den Sicherungsverfahren Ihres Unternehmens an:

* Eine eindeutige Beschriftung zur Identifizierung der Sicherungsmodussitzung, die für Ihre Sicherungsprozesse nützlich sein kann.
* Der Zeitpunkt, zu dem das Sicherungsverfahren abgeschlossen sein soll.
* Ein Flag, das angibt, ob der permanente Sicherungsmodus ausgeführt werden soll. Dies ist nur nützlich, wenn Sie fortlaufende Sicherungen durchführen.

Bevor Sie Anwendungen schreiben, um in den Sicherungsmodus zu wechseln, sollten Sie die Sicherungsverfahren verstehen, die nach dem Versetzen des Forms-Servers in den Sicherungsmodus angewendet werden. Weitere Informationen dazu, was bei der Durchführung von Backups für AEM Forms zu beachten ist, finden Sie unter [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).

>[!NOTE]
>
>Weitere Informationen über den Service „Backup und Wiederherstellung“ finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie eine Anwendung, die den Sicherungsmodus aktiviert:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Definieren Sie eine eindeutige Beschriftung, die Dauer der Sicherung und ob der permanente Sicherungsmodus aktiviert werden soll.
1. Aktivieren Sie den Sicherungsmodus.
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung auf dem Server ab.
1. Führen Sie ein Backup des globalen Dokumentenspeichers (GDS) und der Datenbank durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien müssen in Ihr Projekt aufgenommen werden, damit Sie Ihren Code ordnungsgemäß kompilieren und die Backup- und Wiederherstellungs-Service-API verwenden können.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Backup-Modus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, das die Backup- und Wiederherstellungs-Service-API verwendet.

**Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer für die Durchführung des Backups und entscheiden Sie, ob der kontinuierliche Backup-Modus ausgeführt werden soll.**

Bevor Sie in den Sicherungsmodus wechseln, sollten Sie sich für eine eindeutige Beschriftung entscheiden, die Zeitdauer festlegen, die Sie für die Durchführung der Sicherung zuweisen möchten, und entscheiden, ob der Forms-Server im Sicherungsmodus verbleiben soll. Diese wichtigen Überlegungen sollten unbedingt in die von Ihrem Unternehmen eingerichteten Backup-Verfahren integriert werden. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).)

**Backup-Modus aktivieren**

Wechseln Sie in den Backup-Modus mit den Parametern, die den Backup-Verfahren in Ihrem Unternehmen entsprechen.

**Abrufen von Informationen zur Backup-Modus-Sitzung auf dem Server**

Nachdem Sie den Backup-Modus gestartet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Ihre Backup-Verfahren verwendet werden.

**Durchführen des Backups des globalen Dokumentenspeichers (GDS) und der Datenbank**

Nachdem Sie den Sicherungsmodus erfolgreich aktiviert haben, können Sie eine Sicherung des globalen Dokumentenspeichers (GDS) und der Datenbank durchführen, mit der der Forms-Server verbunden ist. Dieser Schritt ist für Ihr Unternehmen spezifisch, da Sie diesen Schritt manuell ausführen können oder andere Werkzeuge zum Ausführen des Backup-Verfahrens nutzen können.

### Wechseln in den Backup-Modus mithilfe der Java-API {#enter-backup-mode-using-the-java-api}

So wechseln Sie mithilfe der Backup- und Wiederherstellungs-Service-API in den Backup-Modus:

1. Projektdateien einschließen

   Schließen Sie die erforderlichen Client-JAR-Dateien wie adobe-backup-restore-client-sdk.jar in den Klassenpfad Ihres Java-Projekts ein. Um die Java-Clientanwendung zu erstellen, müssen die folgenden JAR-Dateien zum Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService-Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory` -Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen einer eindeutigen Beschriftung, Bestimmen der Zeitdauer für die Durchführung des Backups und Entscheidung, ob der kontinuierliche Backup-Modus ausgeführt werden soll

   Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer, die Sie für die Durchführung der Sicherung zuweisen möchten, und entscheiden Sie, ob der Forms-Server im kontinuierlichen Sicherungsmodus bleiben soll.

1. Aktivieren des Sicherungsmodus

   Sp wechseln Sie in den Backup-Modus, indem Sie die `enterBackupMode`-Methode mit den folgenden Parametern aufrufen:

   * Einen `String`-Wert, der eine eindeutige, für Menschen lesbare Bezeichnung angibt, die die Backup-Modus-Sitzung benennt. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Einen `int`-Wert, der die Anzahl der Minuten angibt, die im Backup-Modus verblieben werden soll. Sie können einen Wert zwischen `1` und `10080` angeben (Anzahl der Minuten in einer Woche). Dieser Wert wird bei Verwendung des kontinuierlichen Backup-Modus ignoriert.
   * Einen `Boolean`-Wert, der angibt, ob der kontinuierliche Backup-Modus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Backup-Modus ausgeführt werden soll. Im kontinuierlichen Backup-Modus wird der Wert ignoriert, den Sie für die Anzahl der Minuten angeben, die im Backup-Modus verblieben werden soll.

     Der kontinuierliche Backup-Modus bedeutet, dass eine neue Backup-Modus-Sitzung gestartet wird, nachdem die aktuelle Sitzung abgeschlossen ist. Der Wert `False` bedeutet, dass der kontinuierliche Backup-Modus nicht verwendet wird und die Bereinigung der Dateien aus dem globalen Dokumentenspeicher (GDS) nach dem Verlassen des Backup-Modus fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen mithilfe des `BackupModeEntryResult`-Objekts ab, das nach dem Aufrufen der `enterBackupMode` -Methode zurückgegeben wird. Die Informationen, die Sie nach der Aktivierung des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Beschriftung, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

1. Durchführen des Backups des globalen Dokumentenspeichers und der Datenbank

   Sichern Sie den globalen Dokumentenspeicher (GDS) und die Datenbank, mit der Ihr Forms-Server verbunden ist. Die Aktionen zum Ausführen des Backups sind nicht Teil des AEM Forms-SDK und können sogar manuelle Schritte für die Backup-Verfahren in Ihrem Unternehmen enthalten.

### Starten des Backup-Modus mithilfe der Web-Service-API {#enter-backup-mode-using-the-web-service-api}

So wechseln Sie mithilfe des von der Backup- und Wiederherstellungs-Service-API bereitgestellten Web-Services in den Backup-Modus:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Sicherungs- und Wiederherstellungs-Service-API-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines BackupService-Client-API-Objekts

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `BackupServiceService`-Objekt durch Aufrufen des Standardkonstruktors und geben Sie die Anmeldeinformationen mithilfe der `Credentials`-Methode an.

1. Festlegen einer eindeutigen Beschriftung, Bestimmen der Zeitdauer für die Durchführung des Backups und Entscheidung, ob der kontinuierliche Backup-Modus ausgeführt werden soll

   Legen Sie eine eindeutige Beschriftung fest, bestimmen Sie die Zeitdauer, die Sie für die Durchführung der Sicherung zuweisen möchten, und entscheiden Sie, ob der Forms-Server im kontinuierlichen Sicherungsmodus bleiben soll.

1. Aktivieren des Sicherungsmodus

   Um in den Backup-Modus zu wechseln, rufen Sie die Methode enterBackupMode auf und übergeben Sie die folgenden Werte:

   * Einen `String`-Wert, der eine eindeutige, für Menschen lesbare Bezeichnung angibt, die die Backup-Modus-Sitzung benennt. Es wird empfohlen, keine Leerzeichen oder Zeichen zu verwenden, die nicht im XML-Format kodiert werden können.
   * Einen `Uint32`-Wert, der die Anzahl der Minuten angibt, die im Backup-Modus verblieben werden soll. Sie können einen Wert zwischen `1` und `10080` festlegen (Anzahl der Minuten in einer Woche). Dieser Wert wird bei Verwendung des kontinuierlichen Backup-Modus ignoriert.
   * Einen `Boolean`-Wert, der angibt, ob der kontinuierliche Backup-Modus ausgeführt werden soll. Der Wert `True` gibt an, dass der kontinuierliche Backup-Modus ausgeführt werden soll. Im kontinuierlichen Backup-Modus wird der Wert, den Sie für die Anzahl der Minuten angeben, die im Backup-Modus verbieben werden soll, ignoriert. Der kontinuierliche Backup-Modus bedeutet, dass eine neue Backup-Modus-Sitzung gestartet wird, nachdem die aktuelle Sitzung abgeschlossen ist.

     Der Wert `False` bedeutet, dass der kontinuierliche Backup-Moduss nicht verwendet wird und die Bereinigung der Dateien aus dem globalen Dokumentenspeicher nach dem Verlassen des Backup-Modus fortgesetzt wird.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie Informationen zur Backup-Modus-Sitzung ab, nachdem Sie die Methode enterBackupMode aus dem zurückgegebenen BackupModeEntryResult aufgerufen haben, um zu überprüfen, ob es erfolgreich war. Die Informationen, die Sie nach der Aktivierung des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Beschriftung, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

1. Durchführen des Backups des globalen Dokumentenspeichers und der Datenbank

   Sichern Sie den globalen Dokumentenspeicher (GDS) und die Datenbank, mit der Ihr Forms-Server verbunden ist. Die Aktionen zum Ausführen des Backups sind nicht Teil des AEM Forms-SDK und können sogar manuelle Schritte für die Backup-Verfahren in Ihrem Unternehmen enthalten.

## Sicherungsmodus auf dem Forms-Server beenden {#leaving-backup-mode-on-the-forms-server}

Sie verlassen den Sicherungsmodus, damit der Forms-Server das Bereinigen von Dateien aus dem globalen Dokumentenspeicher (GDS) auf dem Forms-Server fortsetzt.

Bevor Sie Programme schreiben, um in den Modus „Verlassen“ zu wechseln, sollten Sie die Backup-Verfahren verstehen, die mit AEM Forms verwendet werden. Weitere Informationen dazu, was bei der Durchführung von Backups für AEM Forms zu beachten ist, finden Sie unter [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63_de).

>[!NOTE]
>
>Weitere Informationen über den Service „Backup und Wiederherstellung“ finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um den Backup-Modus zu verlassen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein BackupService-Client-Objekt.
1. Deaktivieren Sie den Sicherungsmodus.
1. (Optional) Rufen Sie Informationen zur Sicherungsmodussitzung ab, die auf dem Forms-Server ausgeführt wurde.

**Projektdateien einschließen**

Schließen Sie alle erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Diese Dateien sind wichtig, um Ihren Code ordnungsgemäß zu kompilieren und die Backup- und Wiederherstellungs-Service-API verwenden zu können.

Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines BackupService Client-API-Objekts**

Um den Backup-Modus programmgesteuert zu deaktivieren, erstellen Sie ein BackupService-Client-Objekt, das die Backup- und Wiederherstellungs-Service-API verwendet.

**Sicherungsmodus beenden**

Beenden Sie den Sicherungsmodus, um die normale Bereinigung der Dateien aus dem globalen Dokumentenspeicher (GDS) fortzusetzen. Bevor Sie den Sicherungsmodus beenden, sollten Sie sicherstellen, dass die Sicherungsverfahren abgeschlossen sind.

**Abrufen von Informationen zur beendeten Sicherungsmodussitzung**

Nachdem Sie den Sicherungsmodus beendet haben, können Sie Informationen zur Sitzung abrufen. Diese Informationen können zur Integration in Sicherungsverfahren verwendet werden.

### Beenden des Sicherungsmodus mithilfe der Java-API {#leave-backup-mode-using-the-java-api}

Deaktivieren Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungs-Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie die erforderlichen Client-JAR-Dateien wie adobe-backup-restore-client-sdk.jar in den Klassenpfad Ihres Java-Projekts ein. Zum Erstellen der Java-Clientanwendung müssen die folgenden JAR-Dateien zum Klassenpfad Ihres Projekts hinzugefügt werden:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)
   * jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss Application Server bereitgestellt wird)

1. Erstellen eines BackupService-Client-API-Objekts

   Sie verwenden ein `ServiceClientFactory` -Objekt und das BackupService-Client-API-Objekt zusammen.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `BackupService`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Aktivieren des Sicherungsmodus

   Deaktivieren Sie den Sicherungsmodus durch Aufrufen der `leaveBackupMode`-Methode.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie unter Verwendung des `BackupModeResult`-Objekts, das zurückgegeben wird, Informationen zum Vorgang ab. Die Informationen, die Sie nach der Aktivierung des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein. Beispielsweise können Beschriftung, Backup-ID und Startzeit als Eingabe für Dateinamen für Ihr Sicherungsverfahren nützlich sein.

### Beenden des Sicherungsmodus unter Verwendung der Web-Service-API {#leave-backup-mode-using-the-web-service-api}

Beenden Sie den Sicherungsmodus mithilfe der Sicherungs- und Wiederherstellungs-Service-API (Web-Service):

1. Projektdateien einschließen

   Um Web-Services zu verwenden, müssen Sie sicherstellen, dass Sie die Proxy-Dateien einbinden. Führen Sie diese Schritte aus, um das Projekt für die Verwendung der Sicherungs- und Wiederherstellungs-Service-API als Web-Service zu konfigurieren.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Sicherungs- und Wiederherstellungs-Service-API-WSDL verwendet.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen eines BackupService-Client-API-Objekts

   Erstellen Sie mithilfe der Microsoft .NET-Client-Assembly ein `BackupServiceService`-Objekt, indem Sie den Standardkonstruktor aufrufen.

1. Aktivieren des Sicherungsmodus

   Beenden Sie den Sicherungsmodus, indem Sie den Web-Service-Vorgang `leaveBackupMode` aufrufen.

1. Abrufen von Informationen zur Sicherungsmodussitzung auf dem Server

   Rufen Sie die Sicherungsmoduskennung nach dem Vorgang ab, um sich zu vergewissern, dass er erfolgreich war. Die Informationen, die Sie nach dem Beenden des Sicherungsmodus abrufen können, können für die Integration in Ihre Sicherungsverfahren nützlich sein.
