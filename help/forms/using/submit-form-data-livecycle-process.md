---
title: Konfigurieren von AEM Forms zum Senden von Daten an einen AEM Forms auf JEE-Prozess
description: Integrieren Sie adaptive Formulare in AEM Forms auf JEE-Prozesse zur Verarbeitung von Formulardaten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin, User, Developer
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
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
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 100%
---
# Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms auf JEE-Prozess{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptive Formulare unterstützen das Senden von Daten an AEM Forms auf JEE zur weiteren Verarbeitung. Damit können Sie einen AEM Forms auf JEE-Prozess mit den im gesendeten Formular verfügbaren Daten auslösen. Führen Sie die folgenden Schritte aus, damit Ihre AEM Forms-Instanz ein adaptives Formular an den AEM Forms auf JEE-Prozess senden kann:

## Konfigurieren des AEM Forms-Servers {#configure-your-aem-forms-server}

Führen Sie die folgenden Schritte aus, damit Sie Ihren AEM Forms-Server aktivieren können, um Daten an einen AEM Forms auf JEE-Server zu senden:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Klicken Sie auf die **Adobe LiveCycle Client SDK-Konfigurationskomponente.**
1. Klicken Sie auf die Komponente, um URL, Benutzernamen und das Kennwort des AEM Forms auf JEE-Servers zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Adobe LiveCycle Client SDK-Konfiguration](assets/clientsdkconfiguration.jpg)

## Zuordnung von Daten mit Verarbeitungsfeldern {#map-data-with-process-fields}

Nachdem Sie AEM Forms konfiguriert haben, ordnen Sie die Daten-XML und Anlagen aus dem gesendeten Formular den Feldern im AEM Forms auf JEE-Prozess zu. Gehen Sie folgendermaßen vor:

1. In der AEM-Web-Konfigurationskonsole klicken Sie auf **Guide LiveCycle Process Locator and Invoker**, um die Konfiguration zu bearbeiten.
1. Geben Sie die folgenden Parameter an:

   * **Name der Daten-XML-Parameter** (obligatorisch): Geben Sie die XML-Eigenschaftendatei des AEM Forms auf JEE-Prozesses an, der die gesendeten Daten verarbeiten muss. Der Standardwert lautet **dataxml**.

   * **Name des Dateianlagenparameters** (optional): Geben Sie die Liste der Dokumentobjekte an, die der AEM Forms auf JEE-Prozess verarbeiten muss. Der Standardwert lautet **fileAttachmentsList**.

1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Guide LiveCycle Process Locator and Invoker](assets/test3.jpg)

Nachdem die Konfiguration abgeschlossen ist, listet die Aktion Senden an Formular-Workflow die AEM Forms on JEE-Serverprozesse mit den angegebenen Daten-XML-Parametern.
