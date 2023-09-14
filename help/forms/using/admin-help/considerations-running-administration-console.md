---
title: Überlegungen beim Ausführen von Administration Console
description: In diesem Dokument werden einige Punkte aufgeführt, die beim Ausführen von Administration Console zu beachten sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e15dae6f-d30d-4770-a5ca-34f522a01d31
source-git-commit: e33816b3b8d190e185d2b23dad3a05aca272f01c
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 11%

---

# Überlegungen beim Ausführen von Administration Console {#considerations-when-running-administrationconsole}

Beachten Sie Folgendes beim Ausführen von Administration Console:

* Wenn Sie über die URL `https://[hostname]:'port'/adminui` auf die Administration-Console zugreifen, darf der angegebene Host-Name keine Unterstrichzeichen enthalten. Andernfalls funktionieren Links zu einigen Bereichen der Administration Console möglicherweise nicht ordnungsgemäß.
* Wenn Sie eine Administration Console in Windows Explorer unter einem japanischen Betriebssystem ausführen, kann es zu folgenden Problemen kommen:

   * Wenn Sie auf einen Link klicken, kehren Sie zur Anmeldeseite zurück und nicht zum erwarteten Link.
   * Wenn Sie auf einen Link klicken, wird ein Berechtigungsfehler angezeigt.

  Es wird empfohlen, die Administration Console über einen anderen Browser wie Mozilla Firefox auszuführen, um sicherzustellen, dass keine Links fehlschlagen.

* Verwenden Sie bei Suchvorgängen in der Administration Console keine umgekehrten Schrägstriche ().
