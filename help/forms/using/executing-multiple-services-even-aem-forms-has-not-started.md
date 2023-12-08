---
title: Die Ausführung mehrerer Dienste trotz AEM Forms wurde noch nicht gestartet.
description: Auch wenn die AEM Forms noch nicht vollständig gestartet wurde, werden mehrere Dienste verarbeitet.
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%

---

# Ausführung mehrerer Dienste, obwohl AEM Forms noch nicht vollständig gestartet wurde{#steps-to-resolve-error-after-installing-service-pack}


## Problem {#issue}

Wenn der Benutzer AEM Forms neu startet, werden die aktuellen Aufrufprozesse wie das Rendern von PDF-Dokumenten und mehr fortgesetzt. Dadurch wird der Neustart des AEM Forms-Servers nicht ordnungsgemäß gestartet.

## Gilt für {#applies-to}

Die Lösung gilt für AEM Forms on JEE Server und AEM Forms on OSGi Server.

## Lösung {#solution}

Um das Problem zu beheben, fügen Benutzer ein -Argument hinzu `Dcom.adobe.livecycle.dsc.deferServiceStart=true` nach [Batch-Datei](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) während des Serverstarts.





