---
title: Minimierung der JavaScript-Dateien
description: Anweisungen zum Generieren von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: d88c6831-8ae9-426d-acb5-2a7e066ad158
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '188'
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
