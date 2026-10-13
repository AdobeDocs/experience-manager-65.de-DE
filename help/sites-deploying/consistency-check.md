---
title: Konsistenz- und Durchlaufprüfungen
description: Erfahren Sie, wie Sie Konsistenz- und Durchlaufprüfungen durchführen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
exl-id: 10dde29b-5dc7-4d4e-80ae-3d4fd0397f7e
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 523b1ccd-901e-5e3b-9fa7-f3dfd82463d5
    internal-label: Configuring
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 100%
---
# Konsistenz- und Durchlaufprüfungen{#consistency-and-traversal-checks}

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

Navigieren Sie zum Ausführen einer Konsistenzüberprüfung zur Verwaltungsseite für das JMX MBean **com.adobe.granite (Repository)**. Wechseln Sie auf dem AEM-Hauptbildschirm zu:

**Tools > Web-Konsole > Haupt (auf der Menüleiste) > JMX > com.adobe.granite (Repository)**

In einer Standardinstallation befindet er sich hier: **[|Anzeigen|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

Im Abschnitt **Vorgänge** der Seite finden Sie zwei Methoden: **`traversalCheck`** und **`consistencyCheck`**. Klicken Sie zum Ausführen einer Überprüfung auf den Vorgang und geben Sie die gewünschten Parameter ein.

![chlimage_1-117](assets/chlimage_1-117.png)
