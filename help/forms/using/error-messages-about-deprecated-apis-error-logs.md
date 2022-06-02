---
title: Fehlermeldungen zu veralteten APIs in Fehlerprotokollen
description: Fehlermeldungen zu veralteten APIs in Fehlerprotokollen
source-git-commit: b05666883645ca11784292e4bfb5bf9c1e35a43b
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# Fehlermeldungen zu veralteten APIs in Fehlerprotokollen {#error-messages-about-deprecated-apis-in-error-logs}

Das Problem tritt bei den folgenden Versionen auf:

* Experience Manager 6.5 Forms

## Problem {#issue}

* Die folgenden Fehlermeldungen werden in der Datei error.log angezeigt:
   ` *WARN* [default task-36] org.apache.jackrabbit.oak.spi.security.principal.AclGroupDeprecation use of deprecated java.acl.Group-related API - this method is going to be removed in future Oak releases - see OAK-7358 for details` (NPR-38282)

## Auflösung {#workaround}

1. Installieren [Experience Manager Forms Service Pack 13 oder höher (6.5.13.0 oder höher)](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de)
1. Verwenden Sie den folgenden Link, um das Paket (.jar-Datei mit Auflösung) von Software Distribution herunterzuladen:

   https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]pack/com.adobe.livecycle.dsc.externalloginmodule-4.0.8.jar

1. Öffnen Sie Experience Manager Configuration Manager und installieren Sie die heruntergeladene Datei &quot;com.adobe.livecycle.dsc.externalloginmodule-4.0.8.jar&quot;.

Das Problem wurde behoben.