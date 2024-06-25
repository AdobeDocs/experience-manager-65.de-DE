---
title: Dieser Artikel enthält die Anleitung zum Deinstallieren des Forms-Add-On-Pakets mit CRX Package Manager.
description: Erfahren Sie mehr über die Schritte zum Deinstallieren des Forms-Add-On-Pakets mit CRX Package Manager.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 975f1f580404ea1f2940aec5981f5668dced4b95
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 1%

---


# Deinstallieren des AEM Forms Add-On-Pakets von AEM Instanz

In diesem Artikel werden die Schritte beschrieben, die zur ordnungsgemäßen Deinstallation des AEM Forms Add-On-Pakets von einer AEM Forms SDK-Instanz erforderlich sind. Führen Sie diese Schritte aus, um das Entfernen des Forms-Add-On-Pakets sicherzustellen und potenzielle Probleme mit Ihrer AEM-Umgebung zu vermeiden.

## Voraussetzungen

Stellen Sie sicher, dass Sie Formulare und Daten sichern, um Datenverlust zu vermeiden.

## Deinstallieren des AEM Forms Add-On-Pakets

Um das AEM Forms Add-On-Paket zu deinstallieren, führen Sie die folgenden Schritte aus:

1. **Deinstallieren Sie das AEM Forms Add-On-Paket:**
   1. Navigieren Sie zum `http://[host]:[port]/crx/de/index.jsp`.
   1. Suchen und deinstallieren Sie die `AEM Forms add-on package`.

   ![Paket deinstallieren](/help/forms/using/assets/uninstall-aem-forms-package.png)

1. **Löschen Sie den nativen Ordner aus CRXDE:**
   1. Navigieren Sie zum `http://[host]:[port]/crx/de/index.jsp`.
   1. Navigieren Sie zu `/libs/fd/native/install` und löschen `native` Ordner in CRXDE.

      ![Löschen Sie den nativen Knoten aus CRX/de.](/help/forms/using/assets/native-install-folder-crxde.png)
   1. Speichern Sie die Änderungen.

1. **Beenden Sie das AEM Forms SDK:**
   1. Beenden Sie die AEM Forms SDK-Instanz mit dem Befehl &quot;Strg + C&quot;.

1. **Suchen Sie nach dem Grundgestein und installieren Sie die Ordner im Ordner crx-quickstart .**
   1. Navigieren Sie zu `..author\crx-quickstart` Ordner in der AEM Forms SDK-Instanz.
   1. Suchen Sie nach Ordnern mit dem Namen `bedrock` und `install`.
Wenn sie gefunden werden, müssen Sie sie aus der `crx-quickstart` Ordner in der AEM Forms SDK-Instanz.

   >[!NOTE]
   >
   > Die `bedrock` wird beim Neustart der AEM Forms SDK-Instanz automatisch neu erstellt.

1. **Starten Sie die AEM-Instanz neu:**
   1. Sobald alle vorherigen Schritte abgeschlossen sind, [Starten Sie die AEM Forms SDK-Instanz neu](/help/forms/using/restart-aem-sdk.md).




