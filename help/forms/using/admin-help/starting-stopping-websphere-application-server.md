---
title: Starten und Anhalten des WebSphere-Anwendungs-Servers
description: Bei mehreren Verfahren müssen Sie die WebSphere-Instanz stoppen oder starten, für die Sie AEM Forms-Produkte bereitstellen möchten. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und stoppen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1a4e8f20-0644-4c96-9f52-f7a59521eac9
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '180'
ht-degree: 100%

---

# Starten und Anhalten des WebSphere-Anwendungs-Servers {#starting-and-stopping-websphere-application-server}

Bei mehreren Verfahren müssen Sie die WebSphere-Instanz stoppen oder starten, für die Sie AEM Forms-Produkte bereitstellen möchten. Wenn Sie nicht sicher sind, ob der Anwendungs-Server gestartet wurde, können Sie zunächst den WebSphere Application Server-Status anzeigen.

## Anzeigen des WebSphere Application Server-Status {#view-the-status-of-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## WebSphere Application Server starten {#start-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## WebSphere Application Server beenden {#stop-websphere-application-server}

1. Wechseln Sie ausgehend von einer Eingabeaufforderung in das Verzeichnis `[appserver root]/bin`.
1. Geben Sie den folgenden Befehl ein. Ersetzen Sie dabei *Servername* durch den Namen Ihres WebSphere Application Servers:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
