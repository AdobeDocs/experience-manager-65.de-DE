---
title: Komponentenübersicht
seo-title: Komponenten
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
seo-description: Komponenten sind modulare Einheiten, die spezielle Funktionen zur Darstellung Ihrer Inhalte auf Ihrer Website implementieren.
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
translation-type: tm+mt
source-git-commit: 5597fb39500ac1f85d03263bfa1e5239d35d2a2c

---


# Komponentenübersicht{#components-overview}

Diese Seite enthält eine Übersicht über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-authoring/default-components-foundation.md).

## Was sind Komponenten? {#what-exactly-is-a-component}

* Modulare Einheiten, die spezielle Funktionen zur Darstellung Ihrer Inhalte auf Ihrer Website implementieren.
* Wiederverwendbar.
* Entwickelt als eigenständige Einheiten in einem Ordner des Repositorys.
* Verfügen nicht über ausgeblendete Konfigurationsdateien.
* Können andere Komponenten enthalten.
* Können an beliebigen Stellen eines AEM-Systems ausgeführt werden. Können auch auf die Ausführung unter bestimmten Komponenten beschränkt werden.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Sie können das Bearbeitungsverhalten konfigurieren.
* Verwenden von Dialogfeldern, die mit Unterelementen basierend auf Granite UI-Komponenten erstellt wurden
* Are developed using [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) (recommended) or JSP.
* Können für die Erstellung von angepassten Komponenten entwickelt werden, mit denen die Standardfunktionalität erweitert wird.

Da die Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln einer neuen Komponente auf Ihrer lokalen Instanz
* Stellen Sie es in Ihrer Testumgebung bereit.
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Stellen Sie sie in Ihrer (den) Live-Veröffentlichungsumgebung(en) bereit, in der (denen) sie zum Rendern von Inhalten für Besucher Ihrer Website verwendet werden. Bestimmte Komponenten, z. B. für Communitys, akzeptieren auch Eingaben von Ihren Benutzern.

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Can function in *isolation*, meaning either within AEM or a portal.

## Im Lieferumfang von AEM enthaltene Komponenten {#out-of-the-box-components-within-aem}

AEM verfügt über verschiedene [im Lieferumfang enthaltene Komponenten](/help/sites-authoring/default-components.md) mit umfassender Funktionalität, z. B.:

* Absatzsystem ( `parsys`)
* Page ( `responsivegrid` - touch-enabled UI only)
* Text
* Bild mit Begleittext
* Symbolleiste

Mit den bereitgestellten Komponenten und deren Nutzung auf den bereitgestellten [We.Retail-Beispiel-Websites](/help/sites-developing/we-retail.md) wird veranschaulicht, wie Sie sie implementieren und verwenden können. Die Komponenten werden mit dem gesamten Quellcode bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Kernkomponenten und Foundation-Komponenten {#core-components-and-foundation-components}

Von Adobe werden zwei Sätze mit AEM-Komponenten bereitgestellt:

* [Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md)

**Die Kernkomponenten** wurden mit AEM 6.3 eingeführt und bieten flexible und funktionsreiche Authoring-Funktionen. The [We.Retail reference site](/help/sites-developing/we-retail.md) illustrates how the core components can be used and represent the current best-practices of component development.

**Foundation-Komponenten** gehören in vielen Versionen von AEM zur Grundausstattung und sind direkt nach einer Standardinstallation verfügbar. Obwohl sie noch unterstützt werden, wurden die meisten nicht mehr unterstützt, wurden nicht mehr verbessert und basieren auf alten Technologien.

>[!NOTE]
>
>[Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) sind die derzeit beste Vorgehensweise für den Entwurf und die Entwicklung von Komponenten und dienen als Referenzimplementierungen.
>
>[AEM-Modernisierungstools](modernization-tools.md) können die Migration zu Kernkomponenten unterstützen.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Eine Übersicht über alle verfügbaren Komponenten Ihrer AEM-Instanz erhalten Sie in der [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

Alternativ hierzu können Sie auch CRXDE Lite verwenden, um eine Liste mit allen Komponenten abzurufen, die im Repository verfügbar sind.

1. In **[!UICONTROL CRXDE Lite]**, select **[!UICONTROL Tools]** from the toolbar, then **[!UICONTROL Query]**, which opens the **[!UICONTROL Query]** tab.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Query]** (Abfrage) für `XPath`Type **[!UICONTROL (Typ) die Option]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Click **[!UICONTROL Execute]** and the components are listed.

## Zusätzliche Ressourcen {#further-reading}

Auf den folgenden Seiten finden Sie detaillierte Informationen zur Entwicklung dieser und anderer Komponenten:

* [AEM-Komponenten – Grundlagen](/help/sites-developing/components-basics.md)
* [Entwickeln von AEM-Komponenten](/help/sites-developing/developing-components.md)
* [Entwickeln von AEM-Komponenten – Codebeispiele](/help/sites-developing/developing-components-samples.md)
* [Konfigurieren mehrerer Editoren für Bearbeitung im Kontext](/help/sites-developing/multiple-inplace-editors.md)
* [Entwicklermodus](/help/sites-developing/developer-mode.md)
* [Testen der Benutzeroberfläche](/help/sites-developing/hobbes.md)
* [Komponenten für Inhaltsfragmente](/help/sites-developing/components-content-fragments.md)
* [Ermitteln von Seiteninformationen im JSON-Format](/help/sites-developing/pageinfo.md)
* [Internationalisieren von Komponenten](/help/sites-developing/i18n.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [Verwenden von Bedingungen zum Ausblenden](/help/sites-developing/hide-conditions.md)
* Klassische Benutzeroberfläche

   * [AEM-Komponenten (klassische Benutzeroberfläche)](/help/sites-developing/developing-components-classic.md)
   * [Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)](/help/sites-developing/widgets.md)
   * [Verwenden von xtypes (klassische Benutzeroberfläche)](/help/sites-developing/xtypes.md)
   * [Entwicklung von Formularen (klassische Benutzeroberfläche)](/help/sites-developing/developing-forms.md)

