---
title: Die Ausführung mehrerer Dienste trotz AEM Forms wurde noch nicht gestartet.
description: Auch wenn die AEM Forms noch nicht vollständig gestartet wurde, werden mehrere Dienste verarbeitet.
exl-id: 4ec40412-15b1-434b-a919-2cf23f48077c
source-git-commit: faa628ac4a4631564141f68f3efc9d69a67e5c40
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---

# Ausführung mehrerer Dienste, obwohl AEM Forms noch nicht vollständig gestartet wurde{#steps-to-resolve-error-after-installing-service-pack}


## Problem {#issue}

Wenn der Benutzer AEM Forms neu startet, werden die aktuellen Aufrufprozesse wie das Rendern von PDF-Dokumenten und mehr fortgesetzt. Dadurch wird der Neustart des AEM Forms-Servers nicht ordnungsgemäß gestartet.

## Gilt für {#applies-to}

Die Lösung gilt für AEM Forms on JEE Server und AEM Forms on OSGi Server.

## Lösung {#solution}

Um das Problem zu beheben, fügen Sie ein -Argument hinzu `Dcom.adobe.livecycle.dsc.deferServiceStart=true` nach [Batch-Datei](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) während des Serverstarts.
