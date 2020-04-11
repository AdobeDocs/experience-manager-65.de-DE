---
title: Minimierung der JavaScript-Dateien
seo-title: Minimierung der JavaScript-Dateien
description: Anweisungen zur Generierung von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
seo-description: Anweisungen zur Generierung von minimiertem Code nach AEM Forms Workspace-Anpassungen zur Optimierung der JS-Dateien für das Web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Minimierung der JavaScript-Dateien {#minification-of-the-javascript-files}

Durch die Minimierung werden die redundanten Zeichen im Quellcode, wie Leerzeichen, neue Zeile und Kommentare, entfernt. Dies verbessert die Leistung, da die Größe des Codes verringert wird. Minimierung wirkt sich nicht auf die Funktion aus, verringert jedoch die Lesbarkeit des Codes.

Um minimierten Code für semantische Änderungen zu generieren, führen Sie folgende Schritte aus.

1. Copy `client-html/src/main/webapp/js` from src-package on filesystem.

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Einführung zum Anpassen von AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md) finden Sie weitere Informationen über die Pakete.

1. Update paths in `main.js` located under client-html/src/main/webapp/js, for added/updated models/views.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells mySharequeue:

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Aktualisieren `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` bei Änderung/Hinzufügen eines Alias in `main.js`.

   Ändern Sie zum Beispiel nach Hinzufügen eines neuen Sharequeue-Modells mySharequeue:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Führen Sie unter client-html/src/main/webapp/js/minifier folgenden Befehl aus:

   ```shell
   mvn clean install
   ```

   Es wird ein Ordner minified-files unter client-html/src/main/webapp/js mit minimierten Dateien main.js und registry.js generiert.

>[!NOTE]
>
>Die Minimierung funktioniert nur auf 64-Bit-JVM.

>[!NOTE]
>
>Wenn Sie minimieren, wirkt sich dies auf das Upgrade aus.
