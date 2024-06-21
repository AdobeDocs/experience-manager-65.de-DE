---
title: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste ausgeführt werden.
description: Der AEM Forms-Server beginnt mit der Verarbeitung der Dokumente, noch bevor alle Dienste auf dem JEE- und OSGi-Server ausgeführt werden.
exl-id: 1a1bc1cb-e0ce-49a0-9b05-ae59f900cfb2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, Troubleshooting
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
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
