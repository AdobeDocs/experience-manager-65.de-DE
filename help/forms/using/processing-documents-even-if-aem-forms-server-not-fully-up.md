---
title: AEM Forms Server beginnt mit der Verarbeitung der Dokumente, bevor alle Dienste ausgeführt werden.
description: AEM Forms Server startet die Verarbeitung der Dokumente, bevor alle Dienste auf dem JEE-Server und OSGi-Server ausgeführt werden.
exl-id: 1a1bc1cb-e0ce-49a0-9b05-ae59f900cfb2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 3%

---

# AEM Forms Server beginnt mit der Verarbeitung der Dokumente, bevor alle Dienste ausgeführt werden{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Problem {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Bevor der AEM Forms-Server vollständig eingerichtet ist und alle Anwendungen ausgeführt werden, beginnt der AEM Forms-Server mit der Verarbeitung der Dokumente.


## Gilt für {#applies-to}

Die Lösung gilt für AEM Forms on JEE Server und AEM Forms on OSGi Server.

## Lösung {#solution}

Um das Problem zu beheben, fügen Sie ein -Argument hinzu `Dcom.adobe.livecycle.dsc.deferServiceStart=true` der [Batch-Datei](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) während des Serverstarts.
