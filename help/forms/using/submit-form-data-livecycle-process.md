---
title: Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms on JEE-Prozess
seo-title: Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms on JEE-Prozess
description: Mit AEM Forms können Sie adaptive Formulare in AEM Forms on JEE-Prozesse integrieren, um Formulardaten zu verarbeiten.
seo-description: Mit AEM Forms können Sie adaptive Formulare in AEM Forms on JEE-Prozesse integrieren, um Formulardaten zu verarbeiten.
uuid: 71a894d7-7c0a-43a6-afe5-40c4a15c66d6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: ff97424d-b384-4149-9a3c-b4f00aaa1def
docset: aem65
role: Administrator
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 89%

---

# Konfigurieren von AEM Forms zum Senden von Formulardaten an einen AEM Forms on JEE-Prozess{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptive Formulare unterstützen die Übermittlung von Daten an einen AEM Forms on JEE-Prozess zur weiteren Verarbeitung. Dadurch können Sie einen AEM Forms-Prozess mit den Daten aus dem gesendeten Formular auslösen. Führen Sie die folgenden Schritte aus, damit Ihre AEM Forms-Instanz ein adaptives Formular an den AEM Forms on JEE-Prozess senden kann:

## Konfigurieren Sie Ihren AEM Forms-Server {#configure-your-aem-forms-server}

Führen Sie die folgenden Schritte aus, damit Ihr AEM Forms-Server Daten an einen AEM Forms on JEE-Server senden kann:

1. Rufen Sie AEM Web-Konfigurationskonsole unter https://[*host*]:[*port*]/system/console/configMgr auf.

1. Klicken Sie auf die **Adobe LiveCycle Client SDK-Konfigurationskomponente.**
1. Klicken Sie auf die Komponente, um URL, Benutzernamen und das Kennwort des AEM Forms on JEE-Servers zu bearbeiten.
1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Adobe LiveCycle Client SDK-Konfiguration](assets/clientsdkconfiguration.jpg)

## Zuordnung von Daten mit Verarbeitungsfeldern {#map-data-with-process-fields}

Nachdem der AEM Forms konfiguriert ist, ordnen Sie die Daten-XML und Anhänge vom gesendeten Formular den Feldern im AEM Forms-Prozess zu. Gehen Sie hierfür wie folgt vor:

1. In der AEM-Web-Konfigurationskonsole klicken Sie auf **Guide LiveCycle Process Locator and Invoker**, um die Konfiguration zu bearbeiten.
1. Geben Sie die folgenden Parameter an:

   * **Name des Daten-XML-Parameters**  (erforderlich): Geben Sie die XML-Eigenschaftendatei des AEM Forms on JEE-Prozesses an, der die gesendeten Daten verarbeiten soll. Der Standardwert lautet **dataxml**.

   * **Name des Dateianlagenparameters**(optional): Geben Sie die Liste der Dokumentobjekte an, die der AEM Forms on JEE-Prozess verarbeiten muss. Der Standardwert lautet **fileAttachmentsList**.

1. Überprüfen Sie die Einstellungen und klicken Sie auf **Speichern**.

![Guide LiveCycle Process Locator and Invoker](assets/test3.jpg)

Nachdem die Konfiguration abgeschlossen ist, listet die Aktion Senden an Formular-Arbeitsablauf die AEM Forms on JEE-Serverprozesse mit den angegebenen Daten-XML-Parametern.
