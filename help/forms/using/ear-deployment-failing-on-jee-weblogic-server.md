---
title: EAR-Bereitstellung auf JEE WebLogic-Server fehlgeschlagen
seo-title: EAR Deployment failing on JEE Weblogic Server
description: Schritte zum Beheben eines Fehlers bei der EAR-Bereitstellung auf JEE-WebLogic-Server
exl-id: 109d9182-5e3f-477e-9417-abc83d5ea3bc
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e14eb250-3c22-4a07-9061-a78112b2b826
    internal-label: Experience Manager 6.5
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '98'
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
