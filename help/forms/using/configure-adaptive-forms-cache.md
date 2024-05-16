---
title: Konfigurieren des Caches für adaptive Formulare
description: Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente konzipiert. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: 153986f0-b6ff-4278-8bb6-70c320a4e539
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '857'
ht-degree: 100%

---

# Cache für adaptive Formulare konfigurieren {#configure-adaptive-forms-cache}

Cachen ist ein Mechanismus zum Verkürzen von Datenzugriffszeiten, zur Reduktion von Wartezeiten und zur Steigerung der Geschwindigkeit der Eingabe/Ausgabe (I/O). Der Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, und zwar ohne die vorausgefüllten Daten. Die Zeit, die benötigt wird, um ein adaptives Formular auf dem Client zu rendern, wird dadurch reduziert. Er wurde speziell für adaptive Formulare konzipiert.

## Konfigurieren des Cache für adaptive Formulare bei Autoren- und Veröffentlichungsinstanzen {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld zum [!UICONTROL Bearbeiten der Konfigurationswerte] die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM [!DNL Forms]-Servers im Feld für die **[!UICONTROL Anzahl adaptiver Formulare]** zwischenspeichern kann. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, legen Sie den Wert im Feld für die Anzahl adaptiver Formulare auf **0** fest. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld für HTML-Cache für adaptive Formulare konfigurieren](assets/cache-configuration-edit.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

Ihre Umgebung ist für die Nutzung des Cache für adaptive Formulare und zugehörige Assets konfiguriert.


## (Optional) Konfigurieren des Dispatcher-Caches für adaptive Formulare {#configure-the-cache}

Um die Leistung zu verbessern, können Sie die Dispatcher-Caching-Funktion für adaptive Formulare konfigurieren.

### Voraussetzungen {#pre-requisites}

* Aktivieren Sie die Option zum [Zusammenführen oder Vorausfüllen von Daten auf dem Client](prepopulate-adaptive-form-fields.md#prefill-at-client). Dadurch können eindeutige Daten für jede Instanz eines vorbefüllten Formulars zusammengeführt werden.

### Überlegungen zum Caching von adaptiven Formularen auf einem Dispatcher {#considerations}

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-[!DNL Dispatcher], um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars zu cachen.
* Beim Entwickeln von benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.
* URLs ohne Erweiterung werden nicht zwischengespeichert. Beispiel: URLs mit dem Muster `/content/forms/[folder-structure]/[form-name].html` werden zwischengespeichert, während URLs mit dem Muster `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content` von der Caching-Funktion ignoriert werden. Verwenden Sie daher URLs mit Erweiterungen, um die Caching-Vorteile zu nutzen.
* Überlegungen zu lokalisierten adaptiven Formularen:
   * Verwenden Sie das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html`, um eine lokalisierte Version eines adaptiven Formulars statt `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>` anzufordern.
   * [Deaktivieren Sie die Verwendung des Browser-Gebietsschemas ](supporting-new-language-localization.md#how-localization-of-adaptive-form-works)für URLs mit dem Format `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema]** verwenden und der Konfigurations-Manager deaktiviert ist, wird die nicht lokalisierte Version des adaptiven Formulars bereitgestellt. Die nicht lokalisierte Sprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde. Das für Ihren Browser konfigurierte Gebietsschema (Browser-Gebietsschema) wird nicht berücksichtigt und es wird eine nicht lokalisierte Version des adaptiven Formulars bereitgestellt.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema verwenden]** und der Konfigurations-Manager aktiviert ist, wird, sofern verfügbar, eine lokalisierte Version des adaptiven Formulars bereitgestellt. Die Sprache des lokalisierten adaptiven Formulars basiert auf dem für Ihren Browser konfigurierten Gebietsschema (Browsergebietsschema). Dies kann dazu führen, dass nur [die erste Instanz eines adaptiven Formulars zwischengespeichert wird]. Um zu erfahren, wie Sie diesem Problem vorbeugen können, lesen Sie unter [Fehlerbehebung](#only-first-insatnce-of-adptive-forms-is-cached) nach.

### Aktivieren der Zwischenspeicherung im Dispatcher

Um die Zwischenspeicherung adaptiver Formulare im Dispatcher zu aktivieren und zu konfigurieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die folgende URL für jede Veröffentlichungsinstanz Ihrer Umgebung und [aktivieren Sie den Flush-Agent für Veröffentlichungsinstanzen Ihrer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de#invalidating-dispatcher-cache-from-a-publishing-instance):
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Fügen Sie folgende Zeilen in Ihre Datei dispatcher.any ein](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?land=de#automatically-invalidating-cached-files):

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

   Das Hinzufügen des Obenstehenden bewirkt Folgendes:

   * Ein adaptives Formular bleibt im Cache, bis eine aktualisierte Version des Formulars veröffentlicht wird.

   * Bei Veröffentlichung einer neueren Version der Ressource, auf die in einem adaptiven Formular verwiesen wird, wird das betroffene adaptive Formular automatisch invalidiert. Bei der automatischen Invalidierung referenzierter Ressourcen bestehen jedoch einige Ausnahmen. Informationen dazu, wie Sie diese Ausnahmen vermeiden können, finden Sie im Abschnitt [Fehlerbehebung](#troubleshooting).
1. [Fügen Sie die folgenden Regeln dispatcher.any oder einer benutzerdefinierten Regeldatei hinzu](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#specifying-the-documents-to-cache). Die URLs ohne Cache-Unterstützung werden ausgeschlossen. So zum Beispiel URLs für interaktive Kommunikation.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Do not cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Do not cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Do not cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [Fügen Sie folgende Parameter der Liste „URL-Parameter ignorieren“ hinzu](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#ignoring-url-parameters):

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Ihre AEM-Umgebung ist so konfiguriert, dass adaptive Formulare im Cache abgelegt werden. Es werden alle Arten von adaptiven Formularen gecached. Falls vor der Bereitstellung einer zwischengespeicherten Seite die Zugriffsberechtigungen für diese Seite überprüft werden sollen, finden Sie unter [Caching geschützter Inhalte](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de) weitere Informationen dazu.

## Fehlerbehebung {#troubleshooting}

### Einige adaptive Formulare mit Bildern oder Videos werden nicht automatisch vom Dispatcher-Cache invalidiert {#videos-or-images-not-auto-invalidated}

#### Problem {#issue1}

Wenn Sie Bilder oder Videos über den Asset-Browser auswählen und zu einem adaptiven Formular hinzufügen und diese Bilder und Videos im Assets-Editor bearbeitet werden, werden adaptive Formulare, die diese Bilder enthalten, nicht automatisch vom Dispatcher-Cache invalidiert.

#### Lösung {#Solution1}

Nach dem Veröffentlichen der Bilder und Videos müssen Sie die Veröffentlichung des adaptiven Formulars, das auf diese Assets verweist, rückgängig machen und das Formular erneut veröffentlichen.

### Nur die erste Instanz eines adaptiven Formulars wird zwischengespeichert  {#only-first-instance-of-adaptive-forms-is-cached}

#### Problem {#issue3}

Wenn die URL des adaptiven Formulars keine Lokalisierungsinformationen enthält und im Konfigurations-Manager die Option **[!UICONTROL Browser-Gebietsschema verwenden]** aktiviert ist, wird eine lokalisierte Version des adaptiven Formulars bereitgestellt. Nur die erste Instanz des adaptiven Formulars wird zwischengespeichert und allen nachfolgenden Benutzenden bereitgestellt.

#### Lösung {#Solution3}

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Datei conf.d/httpd-dispatcher.conf oder eine andere Konfigurationsdatei, die für das Laden zur Laufzeit konfiguriert ist.

1. Fügen Sie Ihrer Datei folgenden Code hinzu und speichern Sie die Änderung. Es handelt sich dabei um Beispiel-Code, den Sie an Ihre Umgebung anpassen können.

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
