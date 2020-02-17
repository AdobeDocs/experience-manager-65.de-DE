---
title: Anmelden bei AEM Forms-Arbeitsabläufen
seo-title: Anmelden bei AEM Forms-Arbeitsabläufen
description: Verwenden Sie Protokolle, um AEM Forms-Workflow-Probleme zu debuggen.
seo-description: Verwenden Sie Protokolle, um AEM Forms-Workflow-Probleme zu debuggen.
uuid: 869d0271-c7e3-4b6d-8e63-893dc6af8b8a
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 14bb521a-42ea-4fe2-90fb-202e7ddf917a
docset: aem65
translation-type: tm+mt
source-git-commit: 8e724af4d69cb859537dd088119aaca652ea3931

---


# Anmelden bei AEM Forms-Arbeitsabläufen{#logging-in-aem-forms-workflows}

Schritte zum Arbeitsablauf für Formulare bieten detaillierte Protokolle zum bequemen Debuggen von Problemen mit dem Arbeitsablauf. Aktivieren Sie die Debug-Protokollierung für AEM Forms-Workflows, um die Protokolle anzuzeigen.

By default, all logging information is available in the **error.log** file at the */crx-repository/logs/* directory.

Die Debug-Protokolle für Arbeitsabläufe für Formulare umfassen:

* Einstieg in jeden Workflow-Schritt. Beispiel:\
   `[DEBUG] "Executing Invoke DDX Process step"`

* Beenden Sie jeden Workflow-Schritt. Beispiel:\
   `[DEBUG] "Successfully finished Invoke DDX Process step"`

* Dienstaufrufsmeldungen. Beispiel:\
   `[DEBUG] Invoking Adobe Sign Service for creating agreement`

* Ausstiegsmeldungen des Dienstes. Beispiel:\
   `[DEBUG] Agreement created successfully with agreement id <agreement id>`

* Variablen, die aus der Metadaten-Map gelesen werden. Beispiel:\
   `[DEBUG] Successfully retrieved variable <variable name> from workflow meta data map`

* Variablen, die im JCR-Repository geschrieben wurden. Beispiel:

   ```
      [DEBUG] Successfully written variable <variable name> into meta data node at <JCR path where meta data is being written>
   ```

* Ausnahmemeldungen mit vollständiger Stapelablaufverfolgung. Beispiel:\
   `[DEBUG] Exception in Adobe Sign Service <complete stack trace>`

* Parameter für dynamische Step-Metadaten. Beispiel:

   ```
   [DEBUG] Document of Record to be generated for adaptive form <path of adaptive form>
    [DEBUG] Locale to be used for Document of Record is <locale>
   ```

Im folgenden Beispiel werden die Protokolle für den Schritt Dokument unterschreiben veranschaulicht:

```xml
[DEBUG] Executing sign document step.
[DEBUG] Using adobe sign configuration: <path of adobe sign configuration>
[DEBUG] Invoking Adobe Sign Service for creating agreement
[DEBUG] Agreement created successfully with agreement id <agreement id>
[DEBUG] Exception in Adobe Sign Service <complete stack trace>
[ERROR] Exception in Adobe Sign Service
[DEBUG] Successfully finished sign document step
```

Verwenden Sie die Protokolle, um Folgendes zu bewerten:

* Sie verwenden eine korrekte Adobe-Signaturkonfiguration.
* Der Adobe Sign-Dienst wird beendet, nachdem eine Vereinbarung erfolgreich erstellt wurde.
* Der Schritt Dokument unterschreiben wird mit einer Erfolgsmeldung beendet.

Wenn eine Ausnahme vorliegt, können Sie die gesamte Stapelablaufverfolgung anzeigen, um die Fehlerursache zu bewerten.

## Aktivieren der Debug-Protokollierung für AEM Forms-Workflows {#enable-debug-logging-for-aem-forms-workflows}

Führen Sie die folgenden Schritte aus, um die Debug-Protokollierung für AEM Forms-Workflows zu aktivieren:

1. Gehen Sie zu AEM Web Console Configuration Manager unter:

   https://[server]:[port]/system/console/configMgr

1. Wählen Sie **[!UICONTROL Sling]** > **[!UICONTROL Protokollunterstützung]**.
1. Tippen Sie auf Neue Protokollfunktion **[!UICONTROL hinzufügen.]**
1. Wählen Sie **[!UICONTROL Debug]** als **[!UICONTROL Protokollierungsstufe]**.
1. Geben Sie den Speicherort der Protokolldatei an. Der Standardspeicherort für die Protokolldatei lautet: *logs\error.log*
1. Geben Sie den Namen des Pakets als **com.adobe.granite.workflow.core** in der Spalte **[!UICONTROL Logger]** an.

   Wenn Sie diese Schritte ausführen, können Sie die Debug-Protokolle für das **com.adobe.granite.workflow.core** -Paket speichern. Tippen Sie auf **[!UICONTROL +]** und fügen Sie der Liste die folgenden Paketnamen hinzu:

   * com.adobe.fd.workflow
   * com.adobe.fd.workspace

