---
title: Starten und Beenden von WebLogic Server
description: In mehreren Verfahren müssen Sie die WebLogic Server-Instanz starten oder beenden, in der Sie AEM Forms-Module bereitstellen möchten. In diesem Dokument wird beschrieben, wie Sie WebLogic Server starten und beenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 100%

---


# Starten und Beenden von WebLogic Server {#starting-and-stopping-weblogic-server}

In mehreren Verfahren müssen Sie die WebLogic Server-Instanz starten oder beenden, in der Sie AEM Forms-Module bereitstellen möchten. Stellen Sie sicher, dass WebLogic Server je nach durchgeführtem Vorgang entweder beendet ist oder ausgeführt wird.

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
   <td><p>Erhöhen der Thread-Anzahl des Servers</p></td>
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
>Wenn Sie WebLogic Server unter Red Hat® Enterprise Linux Advanced Server 4.0 ausführen, legen Sie die Umgebungsvariable `LD_ASSUME_KERNEL` unter Verwendung des Befehls `export LD_ASSUME_KERNEL=2.4.19` auf 2.4.19 fest. Führen Sie anschließend WebLogic Server von der gleichen Shell aus, in der Sie diese Umgebungsvariable eingerichtet haben.

## Starten von WebLogic Server {#start-weblogic-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung zu *[Anwendungsserver-Stammordner]*/user_projects/domains/*[appserverdomain]*.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## WebLogic Server anhalten {#stop-weblogic-server}

1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://[host name]:7001/console` eingeben.
1. Melden Sie sich an, indem Sie den Benutzernamen und das Kennwort für diese WebLogic-Konfiguration eingeben und auf „Log In“ (Anmelden) klicken.
1. Klicken Sie im Change Center auf „Sperren und bearbeiten“.
1. Klicken Sie im Bereich „Domain Structure“ (Domain-Struktur) auf „Environment“ (Umgebung) > „Servers“ (Server).
1. Klicken Sie auf „AdminServer“ und dann im Bereich „Settings for AdminServer“ (Einstellungen für AdminServer) auf die Registerkarte „Control“ (Steuerung).
1. Stellen Sie sicher, dass „AdminServer“ in der Tabelle „Server Status“ (Server-Status) ausgewählt ist, und klicken Sie auf „Shutdown“ (Herunterfahren).
1. Wählen Sie „When work completes“ (Bei Arbeitsabschluss) aus, um den Server ordnungsgemäß herunterzufahren, oder „Force Shutdown Now“ (Herunterfahren jetzt erzwingen), um den Server sofort zu beenden, ohne laufende Vorgänge abschließen zu lassen.
1. Klicken Sie im Bereich „Server LiveCycle Assistant“ (Server LiveCycle-Assistent) auf „Yes“ (Ja), um das Herunterfahren abzuschließen.

Die WebLogic Server-Administrationskonsole ist nicht mehr verfügbar, dafür aber die Eingabeaufforderung, an der Sie den Startbefehl aufgerufen haben.

## Starten der WebLogic-Administrationskonsole {#start-weblogic-administration-console}

1. Wenn WebLogic Administration Server nicht bereits ausgeführt wird, wechseln Sie ausgehend von einer Eingabeaufforderung zum Verzeichnis *[Anwendungsserver-Stammordner]\user_projects\domains\[Domain-Name]*, und geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. Greifen Sie auf WebLogic Server Administration-Console zu, indem Sie in die URL-Zeile eines Webbrowsers `https://[host name]:[port]/console` eingeben, wobei *[Port]* der nicht sichere Überwachungs-Port ist. Standardmäßig ist dieser Port-Wert auf 7001 eingestellt.
1. Geben Sie auf dem Anmeldebildschirm Ihren Administrator-Benutzernamen und Ihr Kennwort ein und klicken Sie auf „Log In“ (Anmelden).

## Starten von Node Manager {#start-node-manager}

1. Stellen Sie sicher, dass WebLogic Server ausgeführt wird.
1. Wechseln Sie bei einer neuen Eingabeaufforderung in das Verzeichnis *[Anwendungsserver-Stammordner]*/server/bin.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startNodeManager.cmd`
   * (Linux, UNIX) `./startNodeManager.sh`

## Beenden von Node Manager {#stop-node-manager}

Nachdem Sie WebLogic Server heruntergefahren haben, können Sie die Eingabeaufforderung schließen, an der Sie Node Manager aufgerufen haben.

## Starten eines verwalteten WebLogic-Servers {#start-a-weblogic-managed-server}

>[!NOTE]
>
>Dieser Schritt kann nur ausgeführt werden, nachdem Sie eine WebLogic-Domain und einen verwalteten Server erstellt haben.

1. Vergewissern Sie sich, dass WebLogic Server und Node Manager ausgeführt werden.
1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://host name]:[port]/console` eingeben.
1. Klicken Sie im Bereich „Domain Structure“ (Domain-Struktur) auf „Environment“ (Umgebung) > „Servers“ (Server).
1. Klicken Sie im rechten Bereich auf die Registerkarte „Control“ (Steuerung).
1. Wählen Sie den verwalteten Server aus, der gestartet werden soll.
1. Klicken Sie unter dem verwalteten Server, der gestartet werden soll, auf die Schaltfläche „Start“ (Starten).

## Beenden eines verwalteten WebLogic-Servers {#stop-a-weblogic-managed-server}

1. Starten Sie WebLogic Server Administration-Console, indem Sie in die URL-Zeile eines Webbrowsers `https://`*[Host-name]:[Port ]*`/console` eingeben.
1. Klicken Sie im Bereich „Domain Structure“ (Domain-Struktur) auf „Environment“ (Umgebung) > „Servers“ (Server).
1. Klicken Sie im rechten Bereich auf die Registerkarte „Control“ (Steuerung).
1. Wählen Sie den verwalteten Server aus, der beendet werden soll.
1. Klicken Sie unter dem verwalteten Server, der beendet werden soll, auf die Schaltfläche „Shutdown“ (Herunterfahren).
1. Wählen Sie „When work completes“ (Bei Arbeitsabschluss) aus, um den Server ordnungsgemäß herunterzufahren, oder „Force Shutdown Now“ (Herunterfahren jetzt erzwingen), um den Server sofort zu beenden, ohne laufende Vorgänge abschließen zu lassen.
1. Klicken Sie im Bereich „Server LiveCycle Assistant“ (Server LiveCycle-Assistent) auf „Yes“ (Ja), um das Herunterfahren abzuschließen.

