---
title: Betrachtungen beim Ausführen der Administration Console
seo-title: Betrachtungen beim Ausführen der Administration Console
description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administration Console aufgeführt.
seo-description: In diesem Dokument werden einige Erwägungen zum Ausführen der Administration Console aufgeführt.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Erwägungen beim Ausführen von Administration Console {#considerations-when-running-administrationconsole}

Folgendes sollte beim Ausführen von Administration Console beachtet werden:

* If you access administration console using the URL `https://[hostname]:'port'/adminui`, the specified host name cannot contain underscore characters. Andernfalls funktionieren Links zu einigen Bereichen von Administration Console eventuell nicht ordnungsgemäß.
* Wenn Sie Administration Console in Windows Explorer unter einem japanischen Betriebssystem ausführen, können Sie auf folgende Probleme stoßen:

   * Beim Klicken auf einen Link wechseln Sie zur Anmeldeseite zurück, nicht zum erwarteten Ziel des Links.
   * Beim Klicken auf einen Link wird ein Berechtigungsfehler angezeigt.
   Es wird empfohlen, Administration Console in einem anderen Browser auszuführen, z. B. Mozilla Firefox, um sicherzustellen, dass keine Links fehlerhaft funktionieren.

* Verwenden Sie bei Suchvorgängen in Administration Console keine umgekehrten Schrägstriche (\).

