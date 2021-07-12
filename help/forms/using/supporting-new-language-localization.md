---
title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
seo-title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemas sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
seo-description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemas sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
uuid: 7f9fab6b-8d93-46bb-8c7c-7b723d5159ea
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: d4e2acb0-8d53-4749-9d84-15b8136e610b
docset: aem65
feature: Adaptive Formulare
role: Admin
exl-id: 2ed4d99e-0e90-4b21-ac17-aa6707a3ba7d
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 84%

---

# Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen{#supporting-new-locales-for-adaptive-forms-localization}

## Informationen zu Gebietsschema-Wörterbüchern {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschemawörterbüchern:

**Formularspezifische** Wörterbücher Enthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Zum Beispiel Beschriftungen, Feldnamen, Fehlermeldungen, Hilfebeschreibungen usw. Wird für jedes Gebietsschema in Form eines Satzes von XLIFF-Dateien für die einzelnen Gebietsschemas verwaltet und ist unter `https://<host>:<port>/libs/cq/i18n/translator.html` verfügbar.

**Globale Wörterbücher** In der AEM-Client-Bibliothek gibt es zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Diese Wörterbücher finden Sie in CRXDe Lite unter /libs/fd/xfaforms/clientlibs/I18N. Diese Speicherorte enthalten für jedes Gebietsschema separate Ordner. Da globale Wörterbücher in der Regel nicht oft aktualisiert werden, können Browser separate JavaScript-Dateien für jedes Gebietsschema im Cache zwischenspeichern und die Beanspruchung der Netzwerkbandbreite reduzieren, wenn auf demselben Server auf verschiedene adaptive Formulare zugegriffen wird.

### Funktionsweise der Lokalisierung von adaptiven Formularen {#how-localization-of-adaptive-form-works}

Es gibt zwei Methoden, um das Gebietsschema des adaptiven Formulars zu identifizieren. Wenn ein adaptives Formular wiedergegeben wird, identifiziert es das angeforderte Gebietsschema durch :

* Überprüfen Sie den Selektor `[local]` in der URL des adaptiven Formulars. Das Format der URL ist `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Mithilfe des Selektors `[local]` können adaptive Formulare zwischengespeichert werden.

* Überprüfung der folgenden Parameter in der angegebenen Reihenfolge:

   * Abfrageparameter `afAcceptLang`
Um das Browser-Gebietsschema von Benutzern zu überschreiben, können Sie den 
`afAcceptLang`-Abfrageparameter übergeben, um das Gebietsschema zu erzwingen. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im japanischen Gebietsschema:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * Das für den Benutzer festgelegte Browser-Gebietsschema, das in der Abfrage mit dem `Accept-Language`-Header angegeben ist.

   * Die in AEM angegebene Spracheinstellung des Benutzers.

   * Das Browser-Gebietsschema ist standardmäßig aktiviert. Gehen Sie wie folgt vor, um das im Browser eingestellte Gebietsschema zu ändern:
      * Öffnen Sie den Configuration Manager. Die URL lautet `http://[server]:[port]/system/console/configMgr`.
      * Suchen und öffnen Sie die Konfiguration **[!UICONTROL Webkanal für adaptive Formulare und Interaktive Kommunikation]**.
      * Ändern Sie den Status der Option **[!UICONTROL Browser-Gebietsschema verwenden]** und **[!UICONTROL speichern]** Sie die Konfiguration.

Sobald das Gebietsschema definiert ist, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, wird das Wörterbuch für die Sprache verwendet, in der das adaptive Formular erstellt wurde.

Wenn keine Sprachinformationen vorhanden sind, wird das adaptive Formular in der Originalsprache des Formulars bereitgestellt. Die Originalsprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wird.

Wenn für das angeforderte Gebietsschema keine Client-Bibliothek vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprach-Code gesucht. Beispiel: Wenn das angeforderte Gebietsschema `en_ZA` (Südafrikanisches Englisch) lautet und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch), sofern vorhanden. Wenn jedoch keine der Sprachen vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.

## Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemas {#add-localization-support-for-non-supported-locales}

AEM Forms unterstützt derzeit die Lokalisierung von Inhalten für adaptive Formulare in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR), Chinesisch (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie Unterstützung für ein neues Gebietsschema während der Laufzeit adaptiver Formulare hinzu:

1. [Hinzufügen eines Gebietsschemas zum GuideLocalizationService-Service](../../forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Hinzufügen der XFA-Client-Bibliothek für ein Gebietsschema](../../forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen](../../forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Hinzufügen von Gebietsschema-Unterstützung für das Wörterbuch](../../forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Starten Sie den Server neu](../../forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Hinzufügen eines Gebietsschemas zum Guide-Localization-Service {#add-a-locale-to-the-guide-localization-service-br}

1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf.
1. Klicken Sie, um die Komponente **Guide-Localization-Service** zu bearbeiten.
1. Fügen Sie der Liste der unterstützen Gebietsschemas das gewünschte Gebietsschema hinzu.

![GuideLocalizationService](assets/configservice.png)

### Hinzufügen der XFA-Client-Bibliothek für ein Gebietsschema {#add-xfa-client-library-for-a-locale-br}

Erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `xfaforms.I18N.<locale>` und fügen Sie der Client-Bibliothek die folgenden Dateien hinzu:

* **I18N.js**, die `xfalib.locale.Strings` für das `<locale>` definiert, wie in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N` festgelegt.

* **js.txt**, die Folgendes enthält:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Clientbibliothek für adaptive Formulare für ein Gebietsschema hinzufügen {#add-adaptive-form-client-library-for-a-locale-br}

Erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `guides.I18N.<locale>` und den Abhängigkeiten `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`.

Fügen Sie die folgenden Dateien der Client-Bibliothek hinzu:

* **i18n.js** die `guidelib.i18n` definiert, mit Mustern von „calendarSymbols“, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` für das `<locale>` gemäß den XFA-Spezifikationen, die in der [Spezifikation für Gebietsschema-Sätze](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) beschrieben sind. Sie können auch sehen, wie sie für andere unterstützte Gebietsschemas in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js` definiert ist.
* **LogMessages.js**, die `guidelib.i18n.strings` und `guidelib.i18n.LogMessages` für das `<locale>` wie in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` festgelegt definiert.
* **js.txt**, die Folgendes enthält:

```text
i18n.js
LogMessages.js
```

### Hinzufügen von Gebietsschema-Unterstützung für das Wörterbuch {#add-locale-support-for-the-dictionary-br}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht eines der Gebietsschemas `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` ist.

1. Erstellen Sie einen `nt:unstructured`-Knoten `languages` unter `etc`, falls nicht bereits vorhanden.

1. Falls noch nicht vorhanden, fügen Sie dem Knoten eine Eigenschaft `languages` vom Typ „Zeichenfolge“ hinzu, die mehrere Werte aufnehmen kann.
1. Fügen Sie die `<locale>`-Standardgebietsschema-Werte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` und `ko-kr` hinzu, falls noch nicht vorhanden.

1. Fügen Sie das `<locale>` den Werten der Eigenschaft `languages` von `/etc/languages` hinzu.

Das `<locale>` wird unter `https://'[server]:[port]'/libs/cq/i18n/translator.html` angezeigt.

### Starten Sie den Server neu {#restart-the-server}

Starten Sie den AEM-Server neu, damit das hinzugefügte Gebietsschema in Kraft tritt.

## Beispielbibliotheken für das Hinzufügen von Unterstützung für Spanisch {#sample-libraries-for-adding-support-for-spanish}

Client-Beispielbibliotheken für das Hinzufügen von Unterstützung für Spanisch

[Datei laden](assets/sample.zip)
