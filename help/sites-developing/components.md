---
title: Komponentenübersicht
seo-title: Components
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
seo-description: Components are modular units which realize specific functionality to present your content on your website
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
exl-id: 9e30c969-2692-4380-943a-b022ee900ce8
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 76%

---

# Komponentenübersicht{#components-overview}

Diese Seite enthält einen Überblick über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-authoring/default-components-foundation.md).

## Was sind Komponenten? {#what-exactly-is-a-component}

* Sind modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
* Sind wiederverwendbar.
* Werden als eigenständige Einheiten innerhalb eines Ordners des Repositorys entwickelt.
* Es gibt keine ausgeblendeten Konfigurationsdateien.
* Kann andere Komponenten enthalten.
* Kann überall in einem beliebigen AEM ausgeführt werden. Sie können auch auf die Ausführung unter bestimmten Komponenten beschränkt werden.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Verfügen über ein konfigurierbares Bearbeitungsverhalten.
* Verwenden Dialogfelder, die basierend auf Granite-UI-Komponenten mit Unterelementen erstellt werden
* Werden per [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) (empfohlen) oder JSP entwickelt.
* Kann entwickelt werden, um benutzerdefinierte Komponenten zu erstellen, die die Standardfunktion erweitern.

Da Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln Sie eine neue Komponente auf Ihrer lokalen Instanz.
* Bereitstellen dieser Komponente in Ihrer Testumgebung
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Bereitstellen in Ihren Live-Veröffentlichungsumgebungen, in denen sie zum Rendern von Inhalten für Besucher Ihrer Website verwenden können Bestimmte Komponenten, z. B. für Communities, akzeptieren auch Eingaben von Ihren Benutzern.

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Funktioniert auch *isoliert* (also in AEM oder einem Portal).

## Vordefinierte Komponenten in AEM {#out-of-the-box-components-within-aem}

AEM enthält eine Vielzahl von [vordefinierte Komponenten](/help/sites-authoring/default-components.md) , die eine umfassende Funktionalität bieten, darunter:

* Absatzsystem ( `parsys`)
* Seite ( `responsivegrid` – nur für Touch-optimierte Benutzeroberfläche)
* Text
* Bild mit Begleittext
* Symbolleiste

Die bereitgestellten Komponenten und ihre Verwendung innerhalb der [Beispiel-We.Retail-Websites](/help/sites-developing/we-retail.md) zeigt, wie Komponenten implementiert und verwendet werden. Die Komponenten werden mit dem gesamten Quell-Code bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Kernkomponenten und Foundation-Komponenten {#core-components-and-foundation-components}

Es stehen zwei vom Adobe bereitgestellte AEM zur Verfügung:

* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md)

Die **Kernkomponenten** wurden mit AEM 6.3 eingeführt und bieten flexible und umfangreiche Bearbeitungsfunktionen. Auf der [We.Retail-Referenzsite](/help/sites-developing/we-retail.md) ist dargestellt, wie die Kernkomponenten verwendet werden. Dies entspricht derzeit den Best Practices für die Komponentenentwicklung.

**Foundation-Komponenten** gehören in vielen Versionen von AEM zur Grundausstattung und sind direkt nach einer Standardinstallation verfügbar. Die meisten sind veraltet, werden zwar noch unterstützt, aber nicht mehr erweitert. Sie basieren auf früheren Technologieversionen.

>[!NOTE]
>
>[Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind die derzeit beste Vorgehensweise für den Entwurf und die Entwicklung von Komponenten und dienen als Referenzimplementierungen.
>
>[AEM-Modernisierungs-Tools](modernization-tools.md) können die Migration zu Kernkomponenten unterstützen.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Einen Überblick über alle verfügbaren Komponenten Ihrer AEM-Instanz erhalten Sie in der [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

Alternativ können Sie auch CRXDE Lite verwenden, um eine Liste aller im Repository verfügbaren Komponenten zu erhalten.

1. Wählen Sie in **[!UICONTROL CRXDE Lite]** in der Symbolleiste die Option **[!UICONTROL Tools]** und dann **[!UICONTROL Abfrage]**, um die Registerkarte **[!UICONTROL Abfrage]** zu öffnen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Abfrage]** die Option `XPath` als **[!UICONTROL Typ]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Wenn Sie auf **[!UICONTROL Ausführen]** klicken, werden die Komponenten aufgelistet.

## Zusätzliche Ressourcen {#further-reading}

Die folgenden Seiten enthalten detailliertere Informationen zur Entwicklung dieser – und anderer – Komponenten:

* [AEM-Komponenten – Grundlagen](/help/sites-developing/components-basics.md)
* [Entwickeln von AEM-Komponenten](/help/sites-developing/developing-components.md)
* [Entwickeln von AEM-Komponenten – Code-Beispiele](/help/sites-developing/developing-components-samples.md)
* [Konfigurieren mehrerer Editoren für Bearbeitung im Kontext](/help/sites-developing/multiple-inplace-editors.md)
* [Entwicklermodus](/help/sites-developing/developer-mode.md)
* [Testen der Benutzeroberfläche](/help/sites-developing/hobbes.md)
* [Komponenten für Inhaltsfragmente](/help/sites-developing/components-content-fragments.md)
* [Ermitteln von Seiteninformationen im JSON-Format](/help/sites-developing/pageinfo.md)
* [Internationalisieren von Komponenten](/help/sites-developing/i18n.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Verwenden von Bedingungen zum Ausblenden](/help/sites-developing/hide-conditions.md)
* Klassische Benutzeroberfläche

   * [AEM-Komponenten (klassische Benutzeroberfläche)](/help/sites-developing/developing-components-classic.md)
   * [Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)](/help/sites-developing/widgets.md)
   * [Verwenden von xtypes (klassische Benutzeroberfläche)](/help/sites-developing/xtypes.md)
   * [Entwicklung von Formularen (klassische Benutzeroberfläche)](/help/sites-developing/developing-forms.md)
