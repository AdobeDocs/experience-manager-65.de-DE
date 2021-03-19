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
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 23%

---


# Cache für adaptive Formulare konfigurieren {#configure-adaptive-forms-cache}

Eine Cache ist ein Vorgang, um Datenzugriffzeiten zu verkürzen, die Wartezeit zu reduzieren, und die Geschwindigkeit von Eingabe/Ausgabe (I/A) zu verbessern. Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Dies hilft, die für die Wiedergabe eines adaptiven Formulars auf dem Client erforderliche Zeit zu verkürzen. Es wurde speziell für adaptive Formulare entwickelt.

## Cache für adaptive Formulare bei Autoren- und Veröffentlichungsinstanzen {#configure-adaptive-forms-caching-at-author-and-publish-instances} konfigurieren

1. Gehen Sie zu AEM Web Console Configuration Manager unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiver Kommunikationswebkanal]**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld [!UICONTROL Konfigurationswerte bearbeiten] die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM [!DNL Forms]-Servers im Feld **[!UICONTROL Anzahl der adaptiven Forms]** zwischenspeichern kann. Der Standardwert ist 100. 

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

Ihre Umgebung ist so konfiguriert, dass sie adaptive Formulare und zugehörige Elemente im Cache verwendet.


## (Optional) Konfigurieren Sie den Cache für adaptive Formulare beim Dispatcher {#configure-the-cache}

Sie können auch die Zwischenspeicherung adaptiver Formulare beim Dispatcher konfigurieren, um die Leistung zu erhöhen.

### Voraussetzungen {#pre-requisites}

* Aktivieren Sie die Option [Zusammenführen oder Vorausfüllen von Daten auf Client](prepopulate-adaptive-form-fields.md#prefill-at-client). Dadurch können eindeutige Daten für jede Instanz eines vorausgefüllten Formulars zusammengeführt werden.

### Überlegungen zum Zwischenspeichern adaptiver Formulare auf einem Dispatcher {#considerations}

* Verwenden Sie bei Verwendung des Cache für adaptive Formulare die AEM [!DNL Dispatcher], um Clientbibliotheken (CSS und JavaScript) eines adaptiven Formulars zu zwischenspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.
* URLs ohne Erweiterung werden nicht zwischengespeichert. Beispiel: URL mit Mustermuster`/content/forms/[folder-structure]/[form-name].html` werden zwischengespeichert, und die Zwischenspeicherung ignoriert URLs mit Muster `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content`. Verwenden Sie daher URLs mit Erweiterungen, um die Vorteile der Zwischenspeicherung zu nutzen.
* Überlegungen zu lokalisierten adaptiven Formularen:
   * Verwenden Sie das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html`, um anstelle von `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` eine lokalisierte Version eines adaptiven Formulars anzufordern.
   * [Deaktivieren Sie die Verwendung des Browser-](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) Gebietsschemas für URLs mit Format  `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` und **[!UICONTROL Browser-Gebietsschema]** im Configuration Manager verwenden deaktiviert haben, wird die nicht lokalisierte Version des adaptiven Formulars bereitgestellt. Die nicht lokalisierte Sprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wird. Das für Ihren Browser konfigurierte Gebietsschema (Browser-Gebietsschema) wird nicht berücksichtigt und es wird eine nicht lokalisierte Version des adaptiven Formulars bereitgestellt.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` und **[!UICONTROL Browser-Gebietsschema]** im Konfigurationsmanager verwenden aktiviert haben, wird eine lokalisierte Version des adaptiven Formulars bereitgestellt, sofern verfügbar. Die Sprache des lokalisierten adaptiven Formulars basiert auf dem für Ihren Browser konfigurierten Gebietsschema (Browser-Gebietsschema). Dies kann dazu führen, dass nur die erste Instanz eines adaptiven Formulars [zwischengespeichert wird. ] Um zu verhindern, dass das Problem auf Ihrer Instanz auftritt, lesen Sie [Fehlerbehebung](#only-first-insatnce-of-adptive-forms-is-cached).

### Zwischenspeicherung beim Dispatcher aktivieren

Führen Sie die folgenden Schritte aus, um die Zwischenspeicherung adaptiver Formulare beim Dispatcher zu aktivieren und zu konfigurieren:

1. Öffnen Sie die folgende URL für jede Instanz im Veröffentlichungsmodus Ihrer Umgebung und [aktivieren Sie den Flush-Agent für Instanzen im Veröffentlichungsmodus Ihrer Umgebung](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance):
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [hinzufügen Sie Folgendes zu Ihrer Datei](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#automatically-invalidating-cached-files) dispatcher.any:

   ```JSON
      /invalidate
      {
      /0000
      {
      /glob "*"
      /type "deny"
      }
      /0001
      {
      # Consider all HTML files stale after an activation.
      /glob "*.html"
      /type "allow"
      }
      /0002
      {
      # Exclude htmls present in AF directories
      /glob "/content/forms/**/*.html"
      /type "deny"
      }
   ```

   Wenn Sie Folgendes hinzufügen:

   * Ein adaptives Formular bleibt im Cache, bis eine aktualisierte Version des Formulars nicht veröffentlicht wird.

   * Wenn eine neuere Version der Ressource veröffentlicht wird, auf die in einem adaptiven Formular verwiesen wird, werden die betroffenen adaptiven Formulare automatisch ungültig. Es gibt einige Ausnahmen von der automatischen Ungültigmachung referenzierter Ressourcen. Eine Problemumgehung zu Ausnahmen finden Sie im Abschnitt [Fehlerbehebung](#troubleshooting).
1. [hinzufügen Sie die folgende Regeldatei](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-documents-to-cache) dispatcher.any oder benutzerdefinierte Regeldatei. Die URLs, die keine Zwischenspeicherung unterstützen, werden ausgeschlossen. Zum Beispiel Interaktive Kommunikation.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Don't cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Don't cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Don't cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [hinzufügen Sie die folgenden Parameter an die Liste](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#ignoring-url-parameters) &quot;URL-Parameter ignorieren&quot;:

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Ihre AEM Umgebung ist so konfiguriert, dass adaptive Formulare zwischengespeichert werden. Es speichert alle Arten adaptiver Formulare zwischen. Wenn Sie vor der Bereitstellung der zwischengespeicherten Seite die Benutzerzugriffsberechtigungen für eine Seite überprüfen müssen, lesen Sie [Zwischenspeichern geschützter Inhalte](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/permissions-cache.html).

## Fehlerbehebung {#troubleshooting}

### Einige adaptive Formulare, die Bilder oder Videos enthalten, werden nicht automatisch aus dem Dispatcher-Cache {#videos-or-images-not-auto-invalidated} ungültig gemacht

#### Problem {#issue1}

Wenn Sie Bilder oder Videos über den Asset-Browser auswählen und zu einem adaptiven Formular hinzufügen und diese Bilder und Videos im Assets-Editor bearbeitet werden, werden adaptive Formulare, die solche Bilder enthalten, nicht automatisch vom Dispatcher-Cache ungültig gemacht.

#### Lösung {#Solution1}

Nach dem Veröffentlichen der Bilder und Videos müssen Sie die Veröffentlichung der adaptiven Formulare, die auf diese Assets verweisen, explizit rückgängig machen und veröffentlichen.

### Es wird nur die erste Instanz eines adaptiven Formulars zwischengespeichert {#only-first-instance-of-adaptive-forms-is-cached}

#### Problem {#issue3}

Wenn die URL des adaptiven Formulars keine Informationen zur lokale Anpassung enthält und **[!UICONTROL Browsergebietsschema verwenden]** im Konfigurationsmanager aktiviert ist, wird eine lokalisierte Version des adaptiven Formulars bereitgestellt und nur die erste Instanz des adaptiven Formulars wird zwischengespeichert und an jeden nachfolgenden Benutzer gesendet.

#### Lösung {#Solution3}

Führen Sie zur Behebung dieses Problems folgende Schritte durch:

1. Öffnen Sie die Datei &quot;conf.d/httpd-dispatcher.conf&quot;oder eine andere Konfigurationsdatei, die zur Laufzeit geladen werden soll.

1. hinzufügen Sie den folgenden Code in Ihrer Datei und speichern Sie ihn. Es handelt sich dabei um einen Beispielcode, mit dem Sie ihn an Ihre Umgebung anpassen können.

```XML
   <VirtualHost *:80>
        # Set log level high during development / debugging and then turn it down to whatever is appropriate
    LogLevel rewrite:trace6
        # Start Rewrite Engine
    RewriteEngine On
        # Handle actual URL convention (just pass through)
        RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
 
        # Handle selector based redirection basded on browser language
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two character which most likely will be the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```
