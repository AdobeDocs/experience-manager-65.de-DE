---
title: WebLogic Server starten und beenden
seo-title: WebLogic Server starten und beenden
description: In mehreren Verfahren müssen Sie die Instanz von WebLogic Server, auf der Sie AEM Forms-Module bereitstellen möchten, starten oder beenden. In diesem Dokument wird beschrieben, wie Sie den WebLogic Server starten und stoppen.
seo-description: In mehreren Verfahren müssen Sie die Instanz von WebLogic Server, auf der Sie AEM Forms-Module bereitstellen möchten, starten oder beenden. In diesem Dokument wird beschrieben, wie Sie den WebLogic Server starten und stoppen.
uuid: 957787fe-4cea-4ecd-b49a-c33023c5c309
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c908d064-6596-473a-b218-22a2496c83f7
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 77%

---


# WebLogic Server starten und beenden {#starting-and-stopping-weblogic-server}

In mehreren Verfahren müssen Sie die Instanz von WebLogic Server, auf der Sie AEM Forms-Module bereitstellen möchten, starten oder beenden. Stellen Sie sicher, dass WebLogic Server je nach durchgeführter Aufgabe entweder beendet ist oder ausgeführt wird.

<table>
 <thead>
  <tr>
   <th><p>Aktivität</p></th>
   <th><p>Erforderlicher WebLogic-Status</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>WebLogic-Domäne erstellen</p></td>
   <td><p>Angehalten</p></td>
  </tr>
  <tr>
   <td><p>Erstellen eines neuen WebLogic Managed Server</p></td>
   <td><p>Wird ausgeführt</p></td>
  </tr>
  <tr>
   <td><p>Erhöhen der Thread-Anzahl des Servers</p></td>
   <td><p>Wird ausgeführt</p></td>
  </tr>
  <tr>
   <td><p>AEM Forms-Produkte bereitstellen</p></td>
   <td><p>Wird ausgeführt</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wenn Sie WebLogic Server unter Red Hat® Enterprise Linux Advanced Server 4.0 ausführen, setzen Sie die Umgebungsvariable `LD_ASSUME_KERNEL` mithilfe des Befehls `export LD_ASSUME_KERNEL=2.4.19` auf 2.4.19. Führen Sie anschließend WebLogic Server von der gleichen Shell aus, in der Sie auch die Umgebungsvariable eingerichtet haben.

## WebLogic Server starten {#start-weblogic-server}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[Anwendungsserver-Stammordner]*/user_projects/domains/*[appserverdomain]*.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## WebLogic Server anhalten {#stop-weblogic-server}

1. Starten Sie WebLogic Server Administration Console, indem Sie in die Adresszeile eines Webbrowsers `https://[host name]:7001/console` eingeben.
1. Melden Sie sich an, indem Sie den Benutzernamen und das Kennwort für diese WebLogic-Konfiguration eingeben und auf „Log In“ klicken.
1. Klicken Sie unter „Change Center“ auf Lock &amp; Edit.
1. Klicken Sie im Bereich „Domain Structure“ auf „Environment“ > „Servers“.
1. Klicken Sie auf „AdminServer“ und dann im Bereich „Settings for AdminServer“ auf die Registerkarte „Control“.
1. Stellen Sie sicher, dass „AdminServer“ in der Tabelle „Server Status“ ausgewählt ist, und klicken Sie auf „Shutdown“.
1. Wählen Sie „When work completes“ aus, um den Server ordnungsgemäß herunterzufahren, oder „Force Shutdown Now“, um den Server sofort zu beenden, ohne laufende Vorgänge abschließen zu lassen.
1. Klicken Sie im Bereich „Server LiveCycle Assistant“ auf „Yes“, um das Herunterfahren abzuschließen.

Die WebLogic Server-Verwaltungskonsole wird nicht mehr angezeigt und die Eingabeaufforderung, an der Sie den Startbefehl aufgerufen haben, wird verfügbar.

## WebLogic Administration Console starten  {#start-weblogic-administration-console}

1. Wenn WebLogic Admin Server noch nicht ausgeführt wird, wechseln Sie an einer Eingabeaufforderung zum Ordner *[appserver root]\user_projects\domains\[Domänenname]* und geben Sie den folgenden Befehl ein:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. Greifen Sie auf WebLogic Server Administration Console zu, indem Sie in die Adresszeile eines Webbrowsers `https://[host name]:[port]/console` eingeben, wobei *[port]* der nicht sichere Listener Port ist. Die Standardeinstellung für diesen Anschluss ist 7001.
1. Geben Sie auf dem Anmeldebildschirm Ihren Administrator-Benutzernamen und Ihr Kennwort ein und klicken Sie auf „Log In“.

## Node Manager starten  {#start-node-manager}

1. Stellen Sie sicher, dass WebLogic Server ausgeführt wird.
1. Wechseln Sie an einer neuen Eingabeaufforderung zum Ordner *[appserver root]*/server/bin.
1. Geben Sie den folgenden Befehl ein:

   * (Windows) `startNodeManager.cmd`
   * (Linux, UNIX) `./startNodeManager.sh`

## Node Manager beenden {#stop-node-manager}

Nach dem Herunterfahren von WebLogic Server können Sie die Eingabeaufforderung schließen, an der Sie Node Manager aufgerufen haben.

## Einen verwalteten Server für WebLogic starten  {#start-a-weblogic-managed-server}

>[!NOTE]
>
>Dieser Schritt kann nur ausgeführt werden, nachdem Sie eine WebLogic-Domäne und einen verwalteten Server erstellt haben.

1. Vergewissern Sie sich, dass WebLogic Server und Node Manager ausgeführt werden.
1. Starten Sie WebLogic Server Administration Console, indem Sie in die Adresszeile eines Webbrowsers `https://host name]:[port]`/console eingeben.
1. Klicken Sie im Bereich „Domain Structure“ auf „Environment“ > „Servers“.
1. Klicken Sie im rechten Fenster auf die Registerkarte „Control“.
1. Wählen Sie den verwalteten Server aus, den Sie starten möchten.
1. Klicken Sie neben dem verwalteten Server, den Sie starten möchten, auf die Schaltfläche „Start“.

## Einen verwalteten Server für WebLogic beenden  {#stop-a-weblogic-managed-server}

1. Starten Sie WebLogic Server Administration Console, indem Sie in die Adresszeile eines Webbrowsers `https://`*[Hostname]:[Port ]*`/console` eingeben.
1. Klicken Sie im Bereich „Domain Structure“ auf „Environment“ > „Servers“.
1. Klicken Sie im rechten Fenster auf die Registerkarte „Control“.
1. Wählen Sie den verwalteten Server aus, den Sie beenden möchten.
1. Klicken Sie neben dem verwalteten Server, den Sie beenden möchten, auf die Schaltfläche „Shutdown“.
1. Wählen Sie „When work completes“ aus, um den Server ordnungsgemäß herunterzufahren, oder „Force Shutdown Now“, um den Server sofort zu beenden, ohne laufende Vorgänge abschließen zu lassen.
1. Klicken Sie im Bereich „Server LiveCycle Assistant“ auf „Yes“, um das Herunterfahren abzuschließen.

