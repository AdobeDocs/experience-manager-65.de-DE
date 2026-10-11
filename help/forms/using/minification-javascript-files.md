---
title: Minimierung der JavaScript-Dateien
description: Anweisungen zum Generieren von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: d88c6831-8ae9-426d-acb5-2a7e066ad158
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 100%
---
# Minimierung der JavaScript-Dateien {#minification-of-the-javascript-files}

Durch die Minimierung werden die redundanten Zeichen, wie Leerzeichen, neue Zeilen und Kommentare, aus dem Quell-code entfernt. Dies verbessert die Leistung, indem die Größe des Codes verringert wird. Die Minimierung wirkt sich zwar nicht auf die Funktionalität aus, verringert jedoch die Lesbarkeit des Codes.

Gehen Sie wie folgt vor, um minimierten Code für semantische Änderungen zu generieren.

1. Kopieren Sie `client-html/src/main/webapp/js` von „src-package“ nach „filesystem“.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Einführung zum Anpassen von AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md) finden Sie weitere Informationen über die Pakete.

1. Aktualisieren Sie die Pfade in `main.js`, die sich unter client-html/src/main/webapp/js befinden, für hinzugefügte bzw. aktualisierte Modelle oder Ansichten.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells wie mySharequeue das Folgende:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   To

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Aktualisieren Sie `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,`, falls es eine Änderung/Hinzufügung des Alias in `main.js` gibt.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells wie mySharequeue das Folgende:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   ```

   To

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Führen Sie unter client-html/src/main/webapp/js/minifier folgenden Befehl aus:

   ```shell
   mvn clean install
   ```

   Unter client-html/src/main/webapp/js wird ein minimierter Dateiordner mit minimierten main.js und registry.js erstellt.

>[!NOTE]
>
>Die Minimierung funktioniert nur auf einer 64-Bit-JVM.

>[!NOTE]
>
>Eine MInimierung wirkt sich auf Ihr Upgrade aus.
