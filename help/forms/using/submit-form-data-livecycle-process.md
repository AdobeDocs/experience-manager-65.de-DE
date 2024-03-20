---
title: Konfigurieren von AEM Forms zum Senden von Daten an einen AEM Forms auf JEE-Prozess
description: Integrieren Sie adaptive Formulare in AEM Forms auf JEE-Prozesse zur Verarbeitung von Formulardaten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: 025a3314-8b9d-48e1-a74f-ea0c933e21e3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '318'
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

Nachdem die Konfiguration abgeschlossen ist, listet die Aktion Senden an Formular-Arbeitsablauf die AEM Forms on JEE-Serverprozesse mit den angegebenen Daten-XML-Parametern.
