---
title: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste ausgeführt werden.
description: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste auf dem JEE- und OSGi-Server ausgeführt werden.
exl-id: 1a1bc1cb-e0ce-49a0-9b05-ae59f900cfb2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '111'
ht-degree: 100%

---

# Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste ausgeführt werden.{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Problem {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Der AEM Forms-Server beginnt, noch bevor er vollständig eingerichtet ist und alle Anwendungen ausgeführt werden, mit der Verarbeitung der Dokumente.


## Gilt für {#applies-to}

Diese Lösung gilt für AEM Forms on JEE-Server und AEM Forms on OSGi-Server.

## Lösung {#solution}

Um das Problem zu beheben, fügen Sie während des Server-Starts das Argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` zur [Batch-Datei](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html?lang=de#windows-platform-start-bat-script-example) hinzu.
