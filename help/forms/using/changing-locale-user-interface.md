---
title: Ändern des Gebietsschemas der Benutzeroberfläche von AEM Forms Workspace
description: Anpassen von AEM Forms Workspace zum Lokalisieren von Text, ausgeblendeten Kategorien, Warteschlangen, Prozessen und der Datumsauswahl auf der Benutzeroberfläche.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 9a069486-02a8-4058-adfb-4e0e49d8c0cf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 96%

---

# Ändern des Gebietsschemas der Benutzeroberfläche von AEM Forms Workspace{#changing-the-locale-of-aem-forms-workspace-user-interface}

AEM Forms Workspace unterstützt standardmäßig die Sprachen Englisch, Französisch, Deutsch und Japanisch. Darüber hinaus besteht die Möglichkeit, die AEM Forms Workspace-Benutzeroberfläche in einer beliebigen anderen Sprache zu lokalisieren.

Zum Lokalisieren der AEM Forms Workspace-Benutzeroberfläche in einer Sprache Ihrer Wahl gehört:

* Lokalisieren des Texts von AEM Forms Workspace
* Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen
* Lokalisieren der Datumsauswahl

Bevor Sie die obengenannten Schritte ausführen, achten Sie darauf, die hier aufgeführten Schritte durchzuführen: [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Informationen zum Ändern der Sprache des Anmeldebildschirms von AEM Forms Workspace finden Sie unter [Anmeldebildschirm erstellen](../../forms/using/creating-new-login-screen.md).

## Lokalisieren von Text {#localizing-text}

Führen Sie die folgenden Schritte aus, um Unterstützung für eine Sprache namens *New* und den Browser-Gebietsschema-Code *nw* hinzuzufügen.

1. Melden Sie sich bei CRXDE Lite an.
Die Standard-URL von CRXDE Lite lautet `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Navigieren Sie zum Speicherort `apps/ws/locales` und erstellen Sie einen neuen Ordner `nw.`
1. Kopieren Sie die Datei `translation.json` vom Speicherort `/apps/ws/locales/en-US` zum Speicherort `/apps/ws/locales/nw`.
1. Navigieren Sie zu `/apps/ws/locales/nw` und öffnen Sie `translation.json` zur Bearbeitung. Nehmen Sie gebietsschemaspezifische Änderungen an der Datei „translation.json“ vor.

   Die folgenden Beispiele enthalten die Datei „translation.json“ für die englischen und französischen Gebietsschemata von AEM Forms Workspace.

   ![translation_json_in_en](assets/translation_json_in_en.png) ![translation_json_in_fr](assets/translation_json_in_fr.png)

## Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen {#localizing-collapsed-categories-queues-and-processes}

AEM Forms Workspace verwendet Bilder, um Kopfzeilen von Kategorien, Warteschlangen und Prozessen anzuzeigen. Sie benötigen ein Entwicklungspaket, um diese Kopfzeilen zu lokalisieren. Ausführliche Informationen zum Erstellen eines Entwicklungspakets finden Sie unter [Erstellen von Code für AEM Forms Workspace](introduction-customizing-html-workspace.md#building-html-workspace-code).

In den folgenden Schritten wird davon ausgegangen, dass es sich bei den neuen lokalisierten Bilddateien um *Categories_nw.png*, *Queue_nw.png* und *Processes_nw.png* handelt. Die empfohlene Breite der Bilder sollte auf 19 px festgelegt werden.

>[!NOTE]
>
>Den Browser-Sprachschema-Code Ihres Browsers finden. Öffnen Sie `https://'[server]:[port]'/lc/libs/ws/Locale.html`.

![collapsing_panels_image](assets/collapsing_panels_image.png)

Um die Bilder zu lokalisieren, führen Sie die folgenden Schritte aus:

1. Platzieren Sie mit einem WebDAV-Client die Bilddateien im Ordner */apps/ws/images*.
1. Navigieren Sie zu */apps/ws/css*. Öffnen Sie *newStyle.css* zur Bearbeitung und fügen Sie die folgenden Einträge hinzu:

   ```css
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Führen Sie alle semantischen Änderungen durch, die im Artikel [Anpassung von Workspace](../../forms/using/introduction-customizing-html-workspace.md) aufgeführt sind.
1. Navigieren Sie zum Ordner */js/runtime/utility* und öffnen Sie die Datei *usersession.js* zur Bearbeitung.
1. Suchen Sie den Code, der im ursprünglichen Code-Block aufgeführt ist und fügen Sie die folgende Bedingung hinzu: *lang !== &#39;nw&#39;* to the if statement:

   ```javascript
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```javascript
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Datumsauswahl lokalisieren {#localizing-date-picker}

Sie benötigen ein Entwicklungspaket, um die *Datumsauswahl*-API zu lokalisieren. Ausführliche Informationen zum Erstellen eines Entwicklungspakets finden Sie unter [Erstellen von Code für AEM Forms Workspace](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Laden Sie das [jQuery UI Package](https://jqueryui.com/download/all/) herunter und extrahieren Sie es, navigieren Sie zu *&lt;extrahiertes jQuery UI Package>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Kopieren Sie die Datei „jquery.ui.datepicker-nw.js“ für Gebietsschema-Code „nw“ nach „apps/ws/js/libs/jqueryui“ und nehmen Sie gebietsschemaspezifische Änderungen an der Datei vor.
1. Navigieren Sie zu `apps/ws/js` und öffnen Sie die Datei`jquery.ui.datepicker-nw.js` zur Bearbeitung.
1. Erstellen Sie in der Datei main.js einen Alias für `jquery.ui.datepicker-nw.js.`. Der Code zum Erstellen eines Alias für die Datei `jquery.ui.datepicker-nw.js` ist:

   ```javascript
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Verwenden Sie den Alias `jqueryuidatepickernw`, um die Datei `jquery.ui.datepicker-nw.js` in allen Dateien einzubinden, die die Datumsauswahl verwenden. Die Datumsauswahl wird in den folgenden Dateien verwendet:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   Der Beispiel-Code unten zeigt, wie Sie den Eintrag aus „jquery.ui.datepicker-nw.js“ hinzufügen:

   ```json
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```json
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. In allen Dateien, die die Datumsauswahl-API verwenden, ändern Sie die Standardeinstellungen der Datumsauswahl-API. Die Datumsauswahl-API wird in den folgenden Dateien verwendet:

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Ändern Sie den folgenden Code, um das neue Gebietsschema hinzuzufügen:

   ```javascript
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

   ```javascript
   if (locale === 'ja-JP') {
       $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
       $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
       $.datepicker.setDefaults($.datepicker.regional.fr);
   } else if (locale === 'nw') {
       $.datepicker.setDefaults($.datepicker.regional.nw);
   } else {
       $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```
