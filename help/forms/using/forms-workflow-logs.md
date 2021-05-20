---
title: Protokollierung in AEM Forms-Workflows
seo-title: Protokollierung in AEM Forms-Workflows
description: Verwenden Sie Protokolle, um Probleme mit dem AEM Forms-Workflow zu beheben.
seo-description: Verwenden Sie Protokolle, um Probleme mit dem AEM Forms-Workflow zu beheben.
uuid: 869d0271-c7e3-4b6d-8e63-893dc6af8b8a
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 14bb521a-42ea-4fe2-90fb-202e7ddf917a
docset: aem65
exl-id: 601c8d95-0d1a-4945-a522-e85d3e9fc4ae
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# Protokollierung in AEM Forms-Workflows{#logging-in-aem-forms-workflows}

Die Workflow-Schritte von Forms enthalten detaillierte Protokolle, mit denen Sie Probleme im Zusammenhang mit Workflows bequem beheben können. Aktivieren Sie die Debug-Protokollierung für AEM Forms-Workflows, um die Protokolle anzuzeigen.

Standardmäßig sind alle Protokollinformationen in der Datei **error.log** im Ordner */crx-repository/logs/* verfügbar.

Zu den Debug-Protokollen für Arbeitsabläufe für Formulare gehören:

* Einstieg in jeden Workflow-Schritt. Beispiel:\
   `[DEBUG] "Executing Invoke DDX Process step"`

* Beenden Sie jeden Workflow-Schritt. Beispiel:\
   `[DEBUG] "Successfully finished Invoke DDX Process step"`

* Meldungen zu Dienstaufrufen. Beispiel:\
   `[DEBUG] Invoking Adobe Sign Service for creating agreement`

* Ausstiegsmeldungen des Dienstes. Beispiel:\
   `[DEBUG] Agreement created successfully with agreement id <agreement id>`

* Variablen, die aus der Metadatenzuordnung gelesen werden. Beispiel:\
   `[DEBUG] Successfully retrieved variable <variable name> from workflow meta data map`

* Variablen, die im JCR-Repository geschrieben wurden. Beispiel:

   ```verilog
      [DEBUG] Successfully written variable <variable name> into meta data node at <JCR path where meta data is being written>
   ```

* Ausnahmemeldungen mit vollständiger Stapelablaufverfolgung. Beispiel:\
   `[DEBUG] Exception in Adobe Sign Service <complete stack trace>`

* Dynamische Schritt-Metadatenparameter. Beispiel:

   ```verilog
   [DEBUG] Document of Record to be generated for adaptive form <path of adaptive form>
    [DEBUG] Locale to be used for Document of Record is <locale>
   ```

Das folgende Beispiel zeigt die Protokolle für den Schritt &quot;Dokument unterschreiben&quot;:

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

* Sie verwenden eine korrekte Adobe Sign-Konfiguration.
* Der Adobe Sign-Dienst wird beendet, nachdem eine Vereinbarung erfolgreich erstellt wurde.
* Der Schritt Dokument unterschreiben wird mit einer Erfolgsmeldung beendet.

Wenn eine Ausnahme vorliegt, können Sie den vollständigen Stacktrace anzeigen, um die Fehlerursache zu bewerten.

## Aktivieren Sie die Debug-Protokollierung für AEM Forms-Workflows {#enable-debug-logging-for-aem-forms-workflows}

Führen Sie die folgenden Schritte aus, um die Debug-Protokollierung für AEM Forms-Workflows zu aktivieren:

1. Gehen Sie zu AEM Konfigurationsmanager der Web-Konsole unter:

   https://&#39;[server]:[port]&#39;/system/console/configMgr

1. Wählen Sie **[!UICONTROL Sling]** > **[!UICONTROL Log Support]** aus.
1. Tippen Sie auf **[!UICONTROL Neue Protokollierung hinzufügen.]**
1. Wählen Sie **[!UICONTROL Debug]** als **[!UICONTROL Protokollebene]** aus.
1. Geben Sie den Speicherort der Protokolldatei an. Der Standardspeicherort für die Protokolldatei lautet: *logs\error.log*
1. Geben Sie den Namen des Pakets als **com.adobe.granite.workflow.core** in der Spalte **[!UICONTROL Logger]** an.

   Wenn Sie diese Schritte ausführen, können Sie die Debug-Protokolle für das Paket **com.adobe.granite.workflow.core** speichern. Tippen Sie auf **[!UICONTROL +]** und fügen Sie der Liste die folgenden Paketnamen hinzu:

   * com.adobe.fd.workflow
   * com.adobe.fd.workspace
