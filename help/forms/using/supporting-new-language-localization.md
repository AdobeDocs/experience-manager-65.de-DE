---
title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
seo-title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemata sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
seo-description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemata sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
uuid: 7f9fab6b-8d93-46bb-8c7c-7b723d5159ea
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: d4e2acb0-8d53-4749-9d84-15b8136e610b
docset: aem65
translation-type: tm+mt
source-git-commit: 1a4bfc91cf91b4b56cc4efa99f60575ac1a9a549
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 53%

---


# Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen{#supporting-new-locales-for-adaptive-forms-localization}

## Informationen zu Gebietsschemawörterbüchern {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschemawörterbüchern:

**Formularspezifisches Wörterbuch** Enthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Beispielsweise Beschriftungen, Feldnamen, Fehlermeldungen, Hilfebeschreibungen usw. It is managed as a set of XLIFF files for each locale and you can access it at `https://<host>:<port>/libs/cq/i18n/translator.html`.

**Globale Wörterbücher** Es gibt zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden, in AEM Client-Bibliothek. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Sie können diese Wörterbücher in CRXDe Lite finden Sie unter /libs/fd/xfaforms/clientlibs/I18N. Diese Speicherorte enthalten für jedes Gebietsschema separate Ordner. Da globale Wörterbücher in der Regel nicht oft aktualisiert werden, können Browser separate JavaScript-Dateien für jedes Gebietsschema im Cache zwischenspeichern und die Beanspruchung der Netzwerkbandbreite reduzieren, wenn auf demselben Server auf verschiedene adaptive Formulare zugegriffen wird.

### Funktionsweise der Lokalisierung von adaptiven Formularen {#how-localization-of-adaptive-form-works}

Es gibt zwei Methoden, um das Gebietsschema des adaptiven Formulars zu identifizieren. Wenn ein adaptives Formular wiedergegeben wird, identifiziert es das angeforderte Gebietsschema durch:

* Überprüfen Sie die `[local]` Auswahl in der URL des adaptiven Formulars. The format of the URL is `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Mithilfe der `[local]` Auswahl können adaptive Formulare zwischengespeichert werden.

* Überprüfen Sie die folgenden Parameter in der angegebenen Reihenfolge:

   * Abfrageparameter `afAcceptLang`Um das Browser-Gebietsschema der Benutzer zu überschreiben, können Sie die Variable 
`afAcceptLang` -Abfrageparameter, um das Gebietsschema zu erzwingen. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im japanischen Gebietsschema:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * Das für den Benutzer festgelegte Browser-Gebietsschema, das in der Abfrage mit dem `Accept-Language`-Header angegeben ist.

   * Die in AEM angegebene Spracheinstellung des Benutzers.

   * Das Browser-Gebietsschema ist standardmäßig aktiviert. So ändern Sie die Browser-Spracheinstellung
      * Öffnen Sie den Konfigurationsmanager. The URL is `http://[server]:[port]/system/console/configMgr`
      * Locate and open the **[!UICONTROL Adaptive Form and Interactive Communication Web Channel]** configuration.
      * Ändern Sie den Status der Option &quot;Gebietsschema **[!UICONTROL des Browsers]** verwenden&quot;und **[!UICONTROL speichern]** Sie die Konfiguration.

Sobald das Gebietsschema definiert ist, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, verwendet es das Wörterbuch für die Sprache, in der das adaptive Formular verfasst wurde.

Wenn keine Sprachinformationen vorhanden sind, wird das adaptive Formular in der Originalsprache des Formulars bereitgestellt. Die Originalsprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wird.

Wenn keine Client-Bibliothek für das angeforderte Gebietsschema vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprachcode gesucht. Beispiel: Wenn das angeforderte Gebietsschema `en_ZA` (Südafrikanisches Englisch) lautet und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch), sofern vorhanden. Wenn jedoch keine der Sprachen vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.

## Lokalisierungsunterstützung für nicht unterstützte Gebietsschemata hinzufügen {#add-localization-support-for-non-supported-locales}

AEM Forms unterstützt derzeit die lokale Anpassung von Inhalten für adaptive Formulare in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (es), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR), Chinesisch (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie Unterstützung für ein neues Gebietsschema während der Laufzeit adaptiver Formulare hinzu:

1. [Gebietsschema zum GuideLocalizationService-Dienst hinzufügen](../../forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [XFA-Clientbibliothek für ein Gebietsschema hinzufügen](../../forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen](../../forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Gebietsschema-Unterstützung für das Wörterbuch hinzufügen](../../forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Starten Sie den Server neu](../../forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Add a locale to the Guide Localization service {#add-a-locale-to-the-guide-localization-service-br}

1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf.
1. Klicken Sie, um die Komponente **Handbuch-Lokalisierungsdienst** zu bearbeiten.
1. Fügen Sie der Liste der unterstützen Gebietsschemata das gewünschte Gebietsschema hinzu.

![GuideLocalizationSevice](assets/configservice.png)

### XFA-Clientbibliothek für ein Gebietsschema hinzufügen {#add-xfa-client-library-for-a-locale-br}

Erstellen Sie einen Knoten des Typs `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>`, mit Kategorie `xfaforms.I18N.<locale>`und fügen Sie der Client-Bibliothek die folgenden Dateien hinzu:

* **I18N.js** definieren `xfalib.locale.Strings` für die `<locale>` , wie in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt**, die Folgendes enthält:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen {#add-adaptive-form-client-library-for-a-locale-br}

Erstellen Sie einen Knoten des Typs `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>`, mit Kategorie `guides.I18N.<locale>` und Abhängigkeiten wie `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`. &quot;

Fügen Sie der Clientbibliothek folgende Dateien hinzu:

* **i18n.js** definieren `guidelib.i18n`, mit Mustern von &quot;calendarSymbols&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` für die `<locale>` [](https://helpx.adobe.com/content/dam/de/Adobe/specs/xfa_spec_3_3.pdf)gemäß den XFA-Spezifikationen, die unterLocale Set Specification beschrieben werden. You can also see how it is defined for other supported locales in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.
* **LogMessages.js** definieren `guidelib.i18n.strings` und `guidelib.i18n.LogMessages` für die `<locale>` , wie in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.
* **js.txt**, die Folgendes enthält:

```text
i18n.js
LogMessages.js
```

### Gebietsschema-Unterstützung für das Wörterbuch hinzufügen {#add-locale-support-for-the-dictionary-br}

Perform this step only if the `<locale>` you are adding is not among `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Create an `nt:unstructured` node `languages` under `etc`, if not present already.

1. Fügen Sie dem Knoten eine Zeichenfolgeneigenschaft mit mehreren Eigenschaften, `languages`, hinzu, falls nicht bereits vorhanden.
1. hinzufügen die `<locale>` Standardgebietsschemawerte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, falls nicht bereits vorhanden.

1. Add the `<locale>` to the values of the `languages` property of `/etc/languages`.

Das `<locale>` erscheint am `https://'[server]:[port]'/libs/cq/i18n/translator.html`.

### Starten Sie den Server neu {#restart-the-server}

Starten Sie den AEM-Server neu, damit das hinzugefügte Gebietsschema in Kraft tritt.

## Beispielbibliotheken zum Hinzufügen der Unterstützung für Spanisch {#sample-libraries-for-adding-support-for-spanish}

Client-Beispielbibliotheken zum Hinzufügen der Unterstützung für Spanisch

[Datei laden](assets/sample.zip)
