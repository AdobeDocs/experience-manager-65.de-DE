---
title: Dieser Artikel enthält die Anleitung zum Deinstallieren des Forms-Add-On-Pakets mit CRX Package Manager.
description: Erfahren Sie mehr über die Schritte zum Deinstallieren des Forms-Add-On-Pakets mit CRX Package Manager.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 2755e414ea23ebc1472e9c08d832eca93f28311b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 1%

---


# Deinstallieren des AEM Forms Add-On-Pakets von AEM Instanz

In diesem Artikel werden die Schritte beschrieben, die zur ordnungsgemäßen Deinstallation des AEM Forms Add-On-Pakets von einer AEM Forms SDK-Instanz erforderlich sind. Führen Sie diese Schritte aus, um sicherzustellen, dass das Forms-Add-On-Paket entfernt wird, und so potenzielle Probleme mit Ihrer AEM-Umgebung vermieden werden.

## Voraussetzung

Stellen Sie sicher, dass Sie eine Sicherung durchführen, um Datenverlust zu vermeiden.

## Deinstallieren des AEM Forms Add-On-Pakets

Um das AEM Forms Add-On-Paket zu deinstallieren, führen Sie die folgenden Schritte aus:

1. **Deinstallieren des AEM Forms Add-On-Pakets:**
   1. Navigieren Sie zu &quot;`http://[host]:[port]/crx/de/index.jsp`&quot;.
   1. Suchen und deinstallieren Sie die `AEM Forms add-on package`.

   ![Paket deinstallieren](/help/forms/using/assets/uninstall-aem-forms-package.png)

1. **Löschen Sie den nativen Ordner aus CRXDE:**
   1. Navigieren Sie zu &quot;`http://[host]:[port]/crx/de/index.jsp`&quot;.
   1. Wechseln Sie zu `/libs/fd/native/install` und löschen Sie den Ordner `native` in CRXDE.

      ![Nativen Knoten aus CRX/de](/help/forms/using/assets/native-install-folder-crxde.png) löschen
   1. Speichern Sie die Änderungen.

1. **Beenden des AEM Forms SDK:**
   1. Beenden Sie die AEM Forms SDK-Instanz mit dem Befehl &quot;Strg + C&quot;.

1. **Suchen Sie nach den Ordnern &quot;bedrock&quot;und installieren Sie sie im Ordner &quot;crx-quickstart&quot;**
   1. Navigieren Sie in der AEM Forms SDK-Instanz zum Ordner &quot;`..author\crx-quickstart`&quot;.
   1. Suchen Sie nach Ordnern mit den Namen `bedrock` und `install`.
Wenn sie gefunden werden, stellen Sie sicher, dass sie aus dem Ordner &quot;`crx-quickstart`&quot;in der AEM Forms SDK-Instanz gelöscht werden.

   >[!NOTE]
   >
   > Der Ordner &quot;`bedrock`&quot; wird beim Neustart der AEM Forms SDK-Instanz automatisch erneut erstellt.

1. **Starten Sie die AEM-Instanz neu:**
   1. Sobald alle vorherigen Schritte abgeschlossen sind, starten Sie [die AEM Forms SDK-Instanz neu](/help/forms/using/restart-aem-sdk.md).




