---
title: Anmelden bei AEM Forms Workflows
seo-title: Anmelden bei AEM Forms Workflows
description: Verwenden Sie Protokolle, um Probleme mit dem AEM Forms-Workflow zu debuggen.
seo-description: Verwenden Sie Protokolle, um Probleme mit dem AEM Forms-Workflow zu debuggen.
uuid: 869d0271-c7e3-4b6d-8e63-893dc6af8b8a
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 14bb521a-42ea-4fe2-90fb-202e7ddf917a
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---


# Anmeldung bei AEM Forms Workflows{#logging-in-aem-forms-workflows}

Die Arbeitsablaufschritte von Forms enthalten detaillierte Protokolle zum bequemen Debuggen von Problemen im Zusammenhang mit dem Arbeitsablauf. Aktivieren Sie die Debug-Protokollierung für AEM Forms Workflows, um die Protokolle Ansicht.

Standardmäßig sind alle Protokollinformationen in der Datei **error.log** im Ordner */crx-repository/logs/* verfügbar.

Die Debug-Protokolle für Formulare Workflows:

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

   ```verilog
      [DEBUG] Successfully written variable <variable name> into meta data node at <JCR path where meta data is being written>
   ```

* Ausnahmemeldungen mit vollständiger Stapelablaufverfolgung. Beispiel:\
   `[DEBUG] Exception in Adobe Sign Service <complete stack trace>`

* Parameter für dynamische Step-Metadaten. Beispiel:

   ```verilog
   [DEBUG] Document of Record to be generated for adaptive form <path of adaptive form>
    [DEBUG] Locale to be used for Document of Record is <locale>
   ```

Im folgenden Beispiel werden die Protokolle für den Schritt &quot;Dokument signieren&quot;veranschaulicht:

```verilog
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
* Der Adobe Sign-Dienst wird beendet, nachdem ein Vertrag erfolgreich erstellt wurde.
* Der Schritt Dokument signieren wird mit einer Erfolgsmeldung beendet.

Wenn eine Ausnahme vorliegt, können Sie die gesamte Stapelablaufverfolgung zur Auswertung der Fehlerursache Ansicht haben.

## Debugging-Protokollierung für AEM Forms Workflows {#enable-debug-logging-for-aem-forms-workflows} aktivieren

Führen Sie die folgenden Schritte aus, um die Debug-Protokollierung für AEM Forms Workflows zu aktivieren:

1. Gehen Sie zu AEM Web Console Configuration Manager unter:

   https://&#39;[server]:[port]&#39;/system/console/configMgr

1. Wählen Sie **[!UICONTROL Sling]** > **[!UICONTROL Protokollunterstützung]**.
1. Tippen Sie auf **[!UICONTROL Hinzufügen neue Protokollfunktion.]**
1. Wählen Sie **[!UICONTROL Debug]** als **[!UICONTROL Protokollierungsstufe]**.
1. Geben Sie den Speicherort der Protokolldatei an. Der Standardspeicherort für die Protokolldatei lautet: *logs\error.log*
1. Geben Sie in der Spalte **[!UICONTROL Logger]** den Namen des Pakets als **com.adobe.granite.workflow.core** ein.

   Wenn Sie diese Schritte ausführen, können Sie die Debug-Protokolle für das **com.adobe.granite.workflow.core**-Paket speichern. Tippen Sie auf **[!UICONTROL +]** und fügen Sie der Liste die folgenden Paketnamen hinzu:

   * com.adobe.fd.workflow
   * com.adobe.fd.workspace

