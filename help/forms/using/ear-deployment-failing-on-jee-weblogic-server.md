---
title: EAR-Bereitstellung auf JEE WebLogic-Server fehlgeschlagen
description: Schritte zum Beheben eines Fehlers bei der EAR-Bereitstellung auf JEE-WebLogic-Server
exl-id: b87a9eee-ee56-4dca-b4a3-a42c91db0b4f
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# Fehler bei der EAR-Bereitstellung auf JEE-WebLogic-Server {#ear-deployment-failing-on-jee-weblogic-server}

## Problem {#issue}

Bei dem Versuch, die `adobe-livecycle-weblogic.ear` bereitzustellen, tritt die `Null Pointer`-Ausnahme auf.

## Gilt für {#applies-to}

Diese Lösung gilt für:

* AEM Forms auf WebLogic-JEE-Server, Version 12.2.1.x.

## Lösung {#solution}

Gehen Sie wie folgt vor, um das Problem zu beheben:

1. Wechseln Sie in das Verzeichnis `<domain_home>\bin` des installierten WebLogic-JEE-Servers.

1. Bearbeiten Sie die Datei `setDomainEnv.cmd` oder `setDomainEnv.sh` als `applicable`.

1. Suchen Sie das letzte Vorkommen von `JAVA_OPTS` und fügen Sie `-DANTLR_USE_DIRECT_CLASS_LOADING=true` hinzu. Die aktualisierte Zeichenfolge wird beispielsweise wie folgt angezeigt:

       set `JAVA_OPTIONS=%JAVA_OPTIONS% -DANTLR_USE_DIRECT_CLASS_LOADING=true`
   
1. Speichern Sie die Änderungen.
