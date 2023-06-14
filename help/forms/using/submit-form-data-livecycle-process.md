---
title: Konfigurieren von AEM Forms zum Senden von Daten an einen AEM Forms on JEE-Prozess
description: Integrieren Sie adaptive Formulare in AEM Forms on JEE-Prozesse zur Verarbeitung von Formulardaten.
uuid: 71a894d7-7c0a-43a6-afe5-40c4a15c66d6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: ff97424d-b384-4149-9a3c-b4f00aaa1def
docset: aem65
role: Admin
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 28%

---

# Konfigurieren von AEM Forms zum Übermitteln von Formulardaten an einen AEM in JEE-Prozess{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptive Formulare unterstützen das Senden von Daten an AEM Forms on JEE zur weiteren Verarbeitung. Damit können Sie einen AEM Forms on JEE-Prozess mit den im gesendeten Formular verfügbaren Daten Trigger. Führen Sie die folgenden Schritte aus, damit Sie Ihre AEM Forms-Instanz aktivieren können, um ein adaptives Formular an den AEM Forms on JEE-Prozess zu senden:

## Konfigurieren des AEM Forms-Servers {#configure-your-aem-forms-server}

Führen Sie die folgenden Schritte aus, damit Sie Ihren AEM Forms-Server aktivieren können, um Daten an einen AEM Forms on JEE-Server zu senden:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Klicken Sie auf die **Adobe LiveCycle Client SDK-Konfigurationskomponente.**
1. Klicken Sie auf , um die Konfigurationsserver-URL, den Benutzernamen und das Kennwort für den AEM Forms on JEE-Server zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Adobe LiveCycle Client SDK-Konfiguration](assets/clientsdkconfiguration.jpg)

## Zuordnung von Daten mit Verarbeitungsfeldern {#map-data-with-process-fields}

Nachdem Sie AEM Forms konfiguriert haben, ordnen Sie die Daten-XML und Anlagen aus dem gesendeten Formular den Feldern im AEM Forms on JEE-Prozess zu. Gehen Sie folgendermaßen vor:

1. Klicken Sie in der AEM Web-Konfigurationskonsole auf , um die **Guide LiveCycle Process Locator and Invoker** Konfiguration.
1. Geben Sie die folgenden Parameter an:

   * **Name des Daten-XML-Parameters** (erforderlich): Geben Sie die XML-Eigenschaftendatei des AEM Forms on JEE-Prozesses an, der die gesendeten Daten verarbeiten muss. Der Standardwert lautet **dataxml**.

   * **Name des Dateianlagen-Parameters** (optional): Geben Sie die Liste der Dokumentobjekte an, die der AEM Forms on JEE-Prozess verarbeiten muss. Der Standardwert lautet **fileAttachmentsList**.

1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Guide LiveCycle Process Locator and Invoker](assets/test3.jpg)

Nachdem die Konfiguration abgeschlossen ist, listet die Aktion Senden an Formular-Arbeitsablauf die AEM Forms on JEE-Serverprozesse mit den angegebenen Daten-XML-Parametern.
