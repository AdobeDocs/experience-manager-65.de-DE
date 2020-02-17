---
title: Cache für adaptive Formulare konfigurieren
seo-title: Cache für adaptive Formulare konfigurieren
description: 'Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entworfen. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist. '
seo-description: 'Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente entworfen. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist. '
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
docset: aem65
translation-type: tm+mt
source-git-commit: 76908a565bf9e6916db39d7db23c04d2d40b3247

---


# Cache für adaptive Formulare konfigurieren{#configure-adaptive-forms-cache}

Eine Cache ist ein Vorgang, um Datenzugriffzeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular oder ein Dokument auf dem Client zu rendern, wird reduziert. Es wurde speziell für adaptive Formulare und adaptive Dokumente entworfen.

>[!NOTE]
>
>Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-Dispatcher, um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars oder Dokuments zwischenzuspeichern.

>[!NOTE]
>
>Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.

## Cache konfigurieren  {#configure-the-cache}

Führen Sie die folgenden Schritte aus, um den Cache für adaptive Formulare zu konfigurieren:

1. Go to AEM web console configuration manager at https://[server]:[port]/system/console/configMgr.
1. Klicken Sie auf **Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal**, um die Konfigurationswerte zu bearbeiten.
1. In the edit configuration values dialog, specify the maximum number of forms or documents an instance of the AEM Forms server can cache in the **Number of Adaptive Forms** field. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **Speichern**, um die Konfiguration zu speichern.

