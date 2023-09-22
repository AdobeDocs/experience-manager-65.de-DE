---
title: Konsistenz- und Durchlaufprüfungen
description: Erfahren Sie, wie Sie Konsistenz- und Durchlaufprüfungen durchführen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
exl-id: 10dde29b-5dc7-4d4e-80ae-3d4fd0397f7e
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 31%

---

# Konsistenz- und Durchlaufprüfungen{#consistency-and-traversal-checks}

Bei der Aktualisierung kann es aufgrund von Arbeitsbereichsinkonsistenzen zu Problemen kommen. Sie können entweder ein Testupgrade durchführen, um zu sehen, ob dies ein Problem darstellt, oder die Konsistenzprüfungen als Präventivmaßnahme ausführen.

Wenn Sie eine Testaktualisierung durchführen, die aufgrund von Arbeitsbereichsinkonsistenzen fehlschlägt, werden in crx-quickstart/logs/crx/error.log Einträge ähnlich den folgenden angezeigt:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Ausführen einer Konsistenzüberprüfung {#perform-a-consistency-check}

Um eine Konsistenzprüfung durchzuführen, navigieren Sie zur Administrationsseite für das JMX-MBean **com.adobe.granite (Repository)**. Wechseln Sie auf dem AEM-Hauptbildschirm zu:

**Tools > Webkonsole > Haupt (auf der Menüleiste) > JMX > com.adobe.granite (Repository)**

In einer Standardinstallation befindet er sich hier: **[|Anzeigen|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

Im **Aktivitäten** zwei Methoden finden: **`traversalCheck`** und **`consistencyCheck`**. Um eine Prüfung auszuführen, klicken Sie auf den Vorgang und geben Sie die gewünschten Parameter ein.

![chlimage_1-117](assets/chlimage_1-117.png)
