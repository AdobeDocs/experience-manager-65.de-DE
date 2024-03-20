---
title: Protokolldateien
description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 23a65be4-3277-4c73-9189-a9b4d7be73cd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 26%

---

# Protokolldateien {#log-files}

Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers aufgenommen. Wenn bei der Bereitstellung auf dem Anwendungsserver Probleme auftreten, können Sie die Protokolldateien verwenden, um das Problem zu beheben. Sie können die Protokolldateien mit einem beliebigen Texteditor öffnen.

(JBoss) Die folgenden Protokolldateien befinden sich im `[appserver root]/server/'server'/log` directory:

* boot.log
* server.log.*[jjjj-mm-tt]*
* server.log

(WebLogic) Protokolldateien für Domänen befinden sich im Ordner `[appserverdomain]` -Ordner und die Protokolldateien des Servers befinden sich im `[appserverdomain]/servers/[appserver name]/logs` directory:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) Die folgenden Protokolldateien befinden sich im `[appserver root]/profiles/default/logs/[appserver name]` directory:

* SystemErr.log
* SystemOut.log
* StartServer.log
