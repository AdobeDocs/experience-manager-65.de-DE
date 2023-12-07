---
title: WebLogic Server starten und beenden
description: In mehreren Verfahren müssen Sie die Instanz von WebLogic Server, auf der Sie AEM Formularmodule bereitstellen möchten, starten oder stoppen. In diesem Dokument wird beschrieben, wie Sie WebLogic Server starten und beenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 32%

---


# WebLogic Server starten und beenden {#starting-and-stopping-weblogic-server}

In mehreren Verfahren müssen Sie die Instanz von WebLogic Server, auf der Sie AEM Formularmodule bereitstellen möchten, starten oder stoppen. Stellen Sie sicher, dass WebLogic Server je nach der von Ihnen ausgeführten Aufgabe angehalten oder ausgeführt wird.

<table>
 <thead>
  <tr>
   <th><p>Aktivität</p></th>
   <th><p>Erforderlicher WebLogic-Status</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Erstellen einer WebLogic-Domain</p></td>
   <td><p>Beendet</p></td>
  </tr>
  <tr>
   <td><p>Erstellen eines verwalteten WebLogic-Servers</p></td>
   <td><p>Ausführung läuft</p></td>
  </tr>
  <tr>
   <td><p>Erhöhung der Server-Thread-Anzahl</p></td>
   <td><p>Ausführung läuft</p></td>
  </tr>
  <tr>
   <td><p>Bereitstellen von AEM Forms-Produkten</p></td>
   <td><p>Ausführung läuft</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wenn Sie WebLogic Server unter Red Hat® Enterprise Linux Advanced Server 4.0 ausführen, legen Sie die Umgebungsvariable `LD_ASSUME_KERNEL` unter Verwendung des Befehls `export LD_ASSUME_KERNEL=2.4.19` auf 2.4.19 fest. Führen Sie anschließend WebLogic Server von der Shell aus, in der Sie diese Umgebungsvariable festlegen.

## WebLogic Server starten {#start-weblogic-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung zu *[Anwendungsserver-Stammordner]*/user_projects/domains/*[appserverdomain]*.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## WebLogic Server anhalten {#stop-weblogic-server}

1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://[host name]:7001/console` eingeben.
1. Melden Sie sich an, indem Sie den Benutzernamen und das Kennwort eingeben, die bei der Erstellung dieser WebLogic-Konfiguration verwendet wurden, und klicken Sie dann auf Anmelden.
1. Klicken Sie im Change Center auf „Sperren und bearbeiten“.
1. Klicken Sie unter &quot;Domain Structure&quot;auf Environment > Servers.
1. Klicken Sie auf AdminServer und anschließend im Bereich Einstellungen für AdminServer auf die Registerkarte Control .
1. Stellen Sie sicher, dass AdminServer in der Tabelle &quot;Serverstatus&quot;ausgewählt ist, und klicken Sie auf &quot;Herunterfahren&quot;.
1. Wählen Sie Bei Abschluss der Arbeit , um den Server ordnungsgemäß herunterzufahren, oder wählen Sie Jetzt herunterfahren erzwingen , um den Server sofort zu beenden, ohne laufende Aufgaben abzuschließen.
1. Klicken Sie im Bereich &quot;Server Life Cycle Assistant&quot;auf Yes , um das Herunterfahren abzuschließen.

Die WebLogic Server Administration Console ist nicht mehr verfügbar und die Eingabeaufforderung, über die Sie den Startbefehl ausgeführt haben, ist verfügbar.

## WebLogic Administration Console starten {#start-weblogic-administration-console}

1. Wenn WebLogic Administration Server nicht bereits ausgeführt wird, wechseln Sie ausgehend von einer Eingabeaufforderung zum Verzeichnis *[Anwendungsserver-Stammordner]\user_projects\domains\[Domain-Name]*, und geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. Greifen Sie auf WebLogic Server Administration-Console zu, indem Sie in die URL-Zeile eines Webbrowsers `https://[host name]:[port]/console` eingeben, wobei *[Port]* der nicht sichere Überwachungs-Port ist. Standardmäßig ist dieser Anschlusswert 7001.
1. Geben Sie auf dem Anmeldebildschirm Ihren Administrator-Benutzernamen und Ihr Kennwort ein und klicken Sie auf Anmelden.

## Node Manager starten {#start-node-manager}

1. Stellen Sie sicher, dass WebLogic Server ausgeführt wird.
1. Wechseln Sie bei einer neuen Eingabeaufforderung in das Verzeichnis *[Anwendungsserver-Stammordner]*/server/bin.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startNodeManager.cmd`
   * (Linux, UNIX) `./startNodeManager.sh`

## Node Manager beenden {#stop-node-manager}

Nachdem Sie WebLogic Server heruntergefahren haben, können Sie die Eingabeaufforderung schließen, an der Sie Node Manager aufgerufen haben.

## WebLogic Managed Server starten {#start-a-weblogic-managed-server}

>[!NOTE]
>
>Dieser Schritt kann nur ausgeführt werden, nachdem Sie eine WebLogic-Domain und einen verwalteten Server erstellt haben.

1. Stellen Sie sicher, dass WebLogic Server und Node Manager ausgeführt werden.
1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://host name]:[port]/console` eingeben.
1. Klicken Sie unter &quot;Domain Structure&quot;auf Environment > Servers.
1. Klicken Sie im rechten Bereich auf die Registerkarte Kontrolle .
1. Wählen Sie den verwalteten Server aus, den Sie starten möchten.
1. Klicken Sie auf die Schaltfläche Starten unter dem verwalteten Server, den Sie starten möchten.

## Einen verwalteten WebLogic-Server stoppen {#stop-a-weblogic-managed-server}

1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://`*[Host-name]:[Port ]*`/console` eingeben.
1. Klicken Sie unter &quot;Domain Structure&quot;auf Environment > Servers.
1. Klicken Sie im rechten Bereich auf die Registerkarte Kontrolle .
1. Wählen Sie den verwalteten Server aus, den Sie stoppen möchten.
1. Klicken Sie auf die Schaltfläche Herunterfahren unter dem verwalteten Server, den Sie stoppen möchten.
1. Wählen Sie Bei Abschluss der Arbeit , um den Server ordnungsgemäß herunterzufahren, oder wählen Sie Jetzt herunterfahren erzwingen , um den Server sofort zu beenden, ohne laufende Aufgaben abzuschließen.
1. Klicken Sie im Bereich &quot;Server Life Cycle Assistant&quot;auf Yes , um das Herunterfahren abzuschließen.

