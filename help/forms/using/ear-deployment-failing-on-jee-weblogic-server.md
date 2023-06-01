---
title: EAR-Bereitstellung auf JEE WebLogic Server fehlgeschlagen
seo-title: EAR Deployment failing on JEE Weblogic Server
description: Schritte zum Beheben eines Fehlers bei der EAR-Bereitstellung auf JEE WebLogic Server
seo-description: Steps to resolve EAR Deployment failing on JEE Weblogic Server
source-git-commit: 45bb54a2666c2c196a8fb52795a7f428aa751e4d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 10%

---


# Fehler bei der EAR-Bereitstellung auf JEE WebLogic Server {#ear-deployment-failing-on-jee-weblogic-server}

## Problem {#issue}

Wenn ein Benutzer versucht, die `adobe-livecycle-weblogic.ear`, die `Null Pointer` Ausnahmefehler .

## Gilt für {#applies-to}

Diese Lösung gilt für:

* AEM Forms auf WebLogic JEE-Server, Version 12.2.1.x.

## Lösung {#solution}

Gehen Sie wie folgt vor, um das Problem zu beheben:

1. Navigieren Sie zu `<domain_home>\bin` Ordner des installierten WebLogic JEE-Servers.

1. Bearbeiten Sie die `setDomainEnv.cmd` oder `setDomainEnv.sh` als `applicable`.

1. Suchen Sie nach dem letzten Vorkommen von `JAVA_OPTS` und hinzufügen `-DANTLR_USE_DIRECT_CLASS_LOADING=true` zu. Die aktualisierte Zeichenfolge wird beispielsweise wie folgt angezeigt:

       set `JAVA_OPTIONS=%JAVA_OPTIONS% -DANTLR_USE_DIRECT_CLASS_LOADING=true`
   
1. Speichern Sie die Änderungen.


