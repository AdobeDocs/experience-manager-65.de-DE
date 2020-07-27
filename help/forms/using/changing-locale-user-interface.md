---
title: Ändern des Gebietsschemas der AEM Forms Workspace-Benutzeroberfläche
seo-title: Ändern des Gebietsschemas der AEM Forms Workspace-Benutzeroberfläche
description: AEM Forms Workspace anpassen zum Lokalisieren von Text, ausgeblendeten Kategorien, Warteschlangen, Prozessen und der Datumsauswahl auf der Benutzeroberfläche.
seo-description: AEM Forms Workspace anpassen zum Lokalisieren von Text, ausgeblendeten Kategorien, Warteschlangen, Prozessen und der Datumsauswahl auf der Benutzeroberfläche.
uuid: c89ff150-a36e-45cc-99a6-8768dbe58eab
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 89f9d666-28e2-4201-8467-ae90693ca5d2
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 63%

---


# Ändern des Gebietsschemas der AEM Forms Workspace-Benutzeroberfläche{#changing-the-locale-of-aem-forms-workspace-user-interface}

AEM Forms Workspace bietet standardmäßig Unterstützung für Englisch, Französisch, Deutsch und Japanisch. Es bietet außerdem die Möglichkeit, die Benutzeroberfläche von AEM Forms Workspace in jeder anderen Sprache zu lokalisieren.

So lokalisieren Sie die Benutzeroberfläche von AEM Forms Workspace in die gewünschte Sprache:

* Lokalisieren des Texts von AEM Forms Workspace
* Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen
* Lokalisieren der Datumsauswahl

Before performing above steps, ensure that you follow the steps listed at [Generic steps for AEM Forms workspace customization](../../forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Informationen zum Ändern der Sprache des Anmeldebildschirms von AEM Forms Workspace finden Sie unter [Erstellen eines neuen Anmeldebildschirms](../../forms/using/creating-new-login-screen.md).

## Text lokalisieren {#localizing-text}

Perform the following steps to add support for a language *New* and the browser locale code *nw*.

1. Melden Sie sich bei CRXDE Lite an.
The default URL of CRXDE Lite is `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Navigate to the location `apps/ws/locales` and create a new folder `nw.`
1. Kopieren Sie die Datei `translation.json`vom Speicherort `/apps/ws/locales/en-US` zum Speicherort `/apps/ws/locales/nw` .
1. Navigate to `/apps/ws/locales/nw` and open `translation.json` for editing. Nehmen Sie gebietsschemaspezifische Änderungen an der Datei „translation.json“ vor.

   Die folgenden Beispiele enthalten die Datei „translation.json“ für die englischen und französischen Gebietsschemata von AEM Forms Workspace.

   ![translation_json_in_de](assets/translation_json_in_en.png) ![translation_json_in_fr](assets/translation_json_in_fr.png)

## Lokalisieren von ausgeblendeten Kategorien, Warteschlangen und Prozessen {#localizing-collapsed-categories-queues-and-processes}

AEM Forms Workspace verwendet Bilder, um Kopfzeilen von Kategorien, Warteschlangen und Prozessen anzuzeigen. Sie benötigen das Entwicklungspaket um diese Kopfzeilen zu lokalisieren. For detailed information about creating development package, see [Building AEM Forms workspace code.](introduction-customizing-html-workspace.md#building-html-workspace-code)

In den folgenden Schritten wird davon ausgegangen, dass es sich bei den neuen lokalisierten Bilddateien um *Categories_nw.png*, *Queue_nw.png* und *Processes_nw.png* handelt. Die empfohlene Breite der Bilder ist 19 px.

>[!NOTE]
>
>Den Browser-Sprachschema-Code Ihres Browsers finden Öffnen Sie `https://'[server]:[port]'/lc/libs/ws/Locale.html`.

![collapse_panels_image](assets/collapsing_panels_image.png)

Führen Sie die folgenden Schritte aus, um die Bilder zu lokalisieren:

1. Mit einem WebDAV-Client platzieren Sie die Bilddateien im Ordner */apps/ws/images*.
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

1. Perform all the semantic changes listed in the [Workspace Customization](../../forms/using/introduction-customizing-html-workspace.md) article.
1. Navigieren Sie zum Ordner */js/runtime/utility* und öffnen Sie die Datei *usersession.js* zur Bearbeitung.
1. Suchen Sie den Code, der im ursprünglichen Codeblock aufgeführt ist und fügen Sie die folgende Bedingung hinzu: *lang !== &#39;nw&#39;* to the if statement:

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

Sie benötigen das Entwicklungspaket, um die *Datumsauswahl*-API zu lokalisieren. For detailed information about creating development package, see [Building AEM Forms workspace code](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Laden Sie das [jQuery UI Package](https://jqueryui.com/download/all/) herunter und extrahieren Sie es, navigieren Sie zu *&lt;extrahiertes jQuery UI Package>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Kopieren Sie die Datei „jquery.ui.datepicker-nw.js“ für Gebietsschema-Code „nw“ nach „apps/ws/js/libs/jqueryui“ und nehmen Sie gebietsschemaspezifische Änderungen an der Datei vor.
1. Navigate to `apps/ws/js` and open the `jquery.ui.datepicker-nw.js` file for editing.
1. Erstellen Sie in der Datei &quot;main.js&quot;einen Alias für `jquery.ui.datepicker-nw.js.` Der Code zum Erstellen eines Alias für die `jquery.ui.datepicker-nw.js` Datei lautet:

   ```javascript
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Use alias `jqueryuidatepickernw` to include the `jquery.ui.datepicker-nw.js` file in all the files that use datepicker. Die Datumsauswahl wird in den folgenden Dateien verwendet:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   Der Beispielcode unten zeigt, wie Sie den Eintrag aus „jquery.ui.datepicker-nw.js“ hinzufügen:

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
