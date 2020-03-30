---
title: Protokolldateien
seo-title: Protokolldateien
description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
seo-description: Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben, die mithilfe eines Texteditors geöffnet werden können.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Protokolldateien {#log-files}

Ereignisse wie Laufzeit- oder Startfehler werden in die Protokolldateien des Anwendungsservers geschrieben. Wenn bei der Bereitstellung auf dem Anwendungsserver Probleme auftreten, können Sie diese mithilfe der Protokolldateien ermitteln. Sie können die Protokolldateien in einem beliebigen Texteditor öffnen.

(JBoss) Die folgenden Protokolldateien befinden sich im `[appserver root]/server/'server'/log` Ordner:

* boot.log
* server.log.*[jjjj-mm-tt]*
* server.log

(WebLogic) Protokolldateien für Domänen befinden sich im `[appserverdomain]` Ordner, und die Protokolldateien für Server befinden sich im `[appserverdomain]/servers/[appserver name]/logs` Ordner:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) Die folgenden Protokolldateien befinden sich im `[appserver root]/profiles/default/logs/[appserver name]` Ordner:

* SystemErr.log
* SystemOut.log
* StartServer.log

