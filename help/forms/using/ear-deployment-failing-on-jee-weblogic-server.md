---
title: EAR-Bereitstellung auf JEE WebLogic-Server fehlgeschlagen
seo-title: EAR Deployment failing on JEE Weblogic Server
description: Schritte zum Beheben eines Fehlers bei der EAR-Bereitstellung auf JEE-WebLogic-Server
exl-id: 109d9182-5e3f-477e-9417-abc83d5ea3bc
source-git-commit: 04cdc51ea2059daed6573987052feb893bd5f634
workflow-type: ht
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
