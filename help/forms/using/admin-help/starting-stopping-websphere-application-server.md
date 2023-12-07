---
title: Starten und Anhalten des WebSphere-Anwendungs-Servers
description: In mehreren Verfahren müssen Sie die Instanz von WebSphere, in der Sie AEM Forms-Produkte bereitstellen möchten, stoppen oder starten. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und beenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1a4e8f20-0644-4c96-9f52-f7a59521eac9
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 56%

---

# Starten und Anhalten des WebSphere-Anwendungs-Servers {#starting-and-stopping-websphere-application-server}

In mehreren Verfahren müssen Sie die Instanz von WebSphere, in der Sie AEM Forms-Produkte bereitstellen möchten, stoppen oder starten. Wenn Sie nicht sicher sind, ob der Anwendungsserver gestartet wurde, können Sie zunächst den Status von WebSphere Application Server anzeigen.

## Status von WebSphere Application Server anzeigen {#view-the-status-of-websphere-application-server}

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
