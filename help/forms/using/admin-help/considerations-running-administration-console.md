---
title: Erwägungen beim Ausführen der Administrationskonsole
description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administrationskonsole aufgeführt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e15dae6f-d30d-4770-a5ca-34f522a01d31
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Erwägungen beim Ausführen der Administrationskonsole {#considerations-when-running-administrationconsole}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Administratorberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Folgendes sollte beim Ausführen der Administrationskonsole beachtet werden:

* Wenn Sie über die URL `https://[hostname]:'port'/adminui` auf die Administration-Console zugreifen, darf der angegebene Host-Name keine Unterstrichzeichen enthalten. Andernfalls funktionieren Links zu einigen Bereichen der Administrationskonsole eventuell nicht ordnungsgemäß.
* Wenn Sie eine Administrationskonsole in Windows Explorer unter einem japanischen Betriebssystem ausführen, können Sie auf folgende Probleme stoßen:

   * Beim Klicken auf einen Link werden Sie zur Anmeldeseite zurückgeleitet, nicht zum erwarteten Ziel des Links.
   * Beim Klicken auf einen Link wird ein Berechtigungsfehler angezeigt.

  Es wird empfohlen, die Administrationskonsole in einem anderen Browser auszuführen, z. B. Mozilla Firefox, um sicherzustellen, dass keine Links fehlerhaft sind.

* Verwenden Sie bei Suchvorgängen in der Administrationskonsole keine umgekehrten Schrägstriche (\).
