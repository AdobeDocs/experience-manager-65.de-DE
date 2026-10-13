---
title: Protokollierung in AEM Forms-Workflows
description: Erfahren Sie, wie Sie AEM Forms Workflow-Probleme debuggen und die Debugging-Protokollierung für AEM Forms-Workflows aktivieren, um die Protokolle anzuzeigen.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 601c8d95-0d1a-4945-a522-e85d3e9fc4ae
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
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
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%
---
# Protokollierung in AEM Forms-Workflows{#logging-in-aem-forms-workflows}

Die Forms Workflow-Schritte enthalten detaillierte Protokolle, mit denen Sie Probleme im Zusammenhang mit Workflows bequem beheben können. Aktivieren Sie die Debug-Protokollierung für AEM Forms-Workflows, um die Protokolle anzuzeigen.

Standardmäßig sind alle Protokollierungsinformationen in der Datei **error.log** im Verzeichnis */crx-repository/logs/* verfügbar.

Zu den Debug-Protokollen für Workflows für Formulare gehören:

* Einstieg in jeden Workflow-Schritt. Beispiel:\
  `[DEBUG] "Executing Invoke DDX Process step"`

* Ausstieg aus jedem Workflow-Schritt. Beispiel:\
  `[DEBUG] "Successfully finished Invoke DDX Process step"`

* Meldungen zu Service-Aufrufen. Beispiel:\
  `[DEBUG] Invoking Adobe Sign Service for creating agreement`

* Ausstiegsmeldungen des Services. Beispiel:\
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

Das folgende Beispiel zeigt die Protokolle für den Schritt „Dokument signieren“:

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
* Der Adobe Sign-Service wird beendet, nachdem eine Vereinbarung erfolgreich erstellt wurde.
* Der Schritt „Dokument signieren“ wird mit einer Erfolgsmeldung beendet.

Wenn eine Ausnahme vorliegt, können Sie die vollständige Stapelablaufverfolgung anzeigen, um die Fehlerursache zu ermitteln.

## Aktivieren der Debug-Protokollierung für AEM Forms-Workflows {#enable-debug-logging-for-aem-forms-workflows}

Gehen Sie folgt vor, um die Debugging-Protokollierung für AEM Forms-Workflows zu aktivieren:

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter:

   https://'[server]:[port]'/system/console/configMgr

1. Wählen Sie **[!UICONTROL Sling]** > **[!UICONTROL Protokollunterstützung]**.
1. Wählen Sie **[!UICONTROL Neue Protokollierung hinzufügen]**.
1. Wählen Sie **[!UICONTROL Debugging]** als **[!UICONTROL Protokollebene]**.
1. Geben Sie den Speicherort der Protokolldatei an. Der Standardspeicherort für die Protokolldatei lautet: *logs\error.log*
1. Geben Sie den Namen des Pakets als **com.adobe.granite.workflow.core** in der Spalte **[!UICONTROL Logger]** an.

   Die Ausführung dieser Schritte ermöglicht die Speicherung der Debug-Protokolle für das Paket **com.adobe.granite.workflow.core**. Wählen Sie **[!UICONTROL +]** und fügen Sie die folgenden Paketnamen zur Liste hinzu:

   * com.adobe.fd.workflow
   * com.adobe.fd.workspace
