---
title: Protokolldateien
description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 23a65be4-3277-4c73-9189-a9b4d7be73cd
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '115'
ht-degree: 100%

---

# Protokolldateien {#log-files}

Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungs-Servers geschrieben. Wenn bei der Bereitstellung auf dem Anwendungs-Server Probleme auftreten, können Sie diese mithilfe der Protokolldateien ermitteln. Sie können die Protokolldateien in einem beliebigen Texteditor öffnen.

(JBoss) Die folgenden Protokolldateien befinden sich im Verzeichnis `[appserver root]/server/'server'/log`:

* boot.log
* server.log.*[jjjj-mm-tt]*
* server.log

(WebLogic) Protokolldateien für Domains befinden sich im Verzeichnis `[appserverdomain]` und Protokolldateien des Servers im Verzeichnis `[appserverdomain]/servers/[appserver name]/logs`:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) Die folgenden Protokolldateien befinden sich im Verzeichnis `[appserver root]/profiles/default/logs/[appserver name]`:

* SystemErr.log
* SystemOut.log
* StartServer.log
