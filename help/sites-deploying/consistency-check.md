---
title: Konsistenz- und Ausnahmeprüfungen
seo-title: Konsistenz- und Ausnahmeprüfungen
description: Erfahren Sie, wie Sie Konsistenz- und Ausnahmeprüfungen durchführen.
seo-description: Erfahren Sie, wie Sie Konsistenz- und Ausnahmeprüfungen durchführen.
uuid: 0304e378-7c60-4bf5-9052-d01149d2a6df
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: af9a3e9d-194a-42e5-be28-b238e0c1e55e
feature: Konfiguration
exl-id: 10dde29b-5dc7-4d4e-80ae-3d4fd0397f7e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 84%

---

# Konsistenz- und Ausnahmeprüfungen{#consistency-and-traversal-checks}

Beim Aktualisieren können aufgrund von Arbeitsbereichsinkonsistenzen Probleme auftreten. Sie können eine Testaktualisierung ausführen, um anzuzeigen, ob dies ein Problem darstellt, oder Konsistenzüberprüfungen als Präventivmaßnahme ausführen.

Wenn Sie eine Testaktualisierung ausführen, die aufgrund von Arbeitsbereichsinkonsistenzen fehlschlägt, werden in der Datei „crx-quickstart/logs/crx/error.log“ Einträge angezeigt, die den folgenden ähneln:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Ausführen einer Konsistenzüberprüfung {#perform-a-consistency-check}

Um eine Konsistenzprüfung durchzuführen, navigieren Sie zur Administrationsseite für das JMX Mbean** com.adobe.granite (Repository)**. Wechseln Sie auf dem AEM-Hauptbildschirm zu:

**Tools > Web-Konsole > Haupt(in Menüleiste) > JMX > com.adobe.granite (Repository)**

In einer Standardinstallation befindet er sich hier: **[|Anzeigen|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

Im Abschnitt **Vorgänge** der Seite finden Sie zwei Methoden: **`traversalCheck`** und **`consistencyCheck`** Klicken Sie zum Ausführen einer Überprüfung auf den Vorgang und geben Sie die gewünschten Parameter ein.

![chlimage_1-117](assets/chlimage_1-117.png)
