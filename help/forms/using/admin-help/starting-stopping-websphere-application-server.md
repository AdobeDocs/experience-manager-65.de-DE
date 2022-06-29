---
title: Starten und Beenden von WebSphere Application Server
seo-title: Starting and stopping WebSphere Application Server
description: In mehreren Verfahren müssen Sie die Instanz von WebSphere, auf der Sie AEM Forms-Produkte bereitstellen möchten, starten oder beenden. In diesem Dokument wird beschrieben, wie Sie WebSphere Application Server starten und anhalten.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 1a4e8f20-0644-4c96-9f52-f7a59521eac9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '189'
ht-degree: 100%

---

# Starten und Beenden von WebSphere Application Server {#starting-and-stopping-websphere-application-server}

In mehreren Verfahren müssen Sie die Instanz von WebSphere, auf der Sie AEM Forms-Produkte bereitstellen möchten, starten oder beenden. Wenn Sie nicht sicher sind, ob der Anwendungsserver gestartet wurde, können Sie zunächst den Status von WebSphere Application Server anzeigen.

## Status des WebSphere Application Server anzeigen {#view-the-status-of-websphere-application-server}

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
