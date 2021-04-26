---
title: We.Retail-Referenzimplementierung
seo-title: We.Retail-Referenzimplementierung
description: We.Retail ist eine Technologievorschau einer Referenzimplementierung, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit AEM veranschaulicht.
seo-description: We.Retail ist eine Technologievorschau einer Referenzimplementierung, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit AEM veranschaulicht.
uuid: d8833192-b592-4812-bf9b-bd882e8ee7f0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: f50150af-deff-4c29-bfe0-1cfc67b29d51
exl-id: 504c61c7-dcd3-412c-9239-d24a2b78e4b9
translation-type: tm+mt
source-git-commit: 1cef6f87fa66fd78d439c23e6ac907f9531b8fd6
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 89%

---

# We.Retail-Referenzimplementierung{#we-retail-reference-implementation}

## Einführung {#introduction}

We.Retail ist eine Referenzimplementierung mit Beispielinhalten, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit Adobe Experience Manager veranschaulicht.

We.Retail greift auf die neuesten AEM-Technologien zurück, darunter HTL, responsive Layouts, bearbeitbare Vorlagen und Kernkomponenten.

Die Vorgehensweisen werden zwar an Beispielen aus dem Einzelhandel erläutert, aber die Art und Weise, wie die Website eingerichtet ist, lässt sich auch auf jede andere Branche anwenden, lediglich die Produktkatalog- und Warenkorbfunktionen sind einzelhandelsspezifisch.

## Funktionen {#features}

Als standardmäßige AEM-Referenzimplementierung demonstriert We.Retail einige der leistungsstärksten Funktionen von AEM.

| **Funktion** | **Beschreibung** | **Interessiert?** |
|---|---|---|
| [Globalisierte Site-Struktur](/help/sites-administering/tc-bp.md) | We.Retail beinhaltet Sprach-Master, die als Live Copy in länderspezifische Sites kopiert werden. | [Jetzt testen!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Responsives Layout](/help/sites-authoring/responsive-layout.md) | Alle Seiten verfügen über ein responsives Layout, das sich dynamisch an die Bildschirm- und Gerätegröße anpasst. | [Jetzt testen!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) | Alle Seiten basieren auf bearbeitbaren Vorlagen, sodass auch Benutzer, die keine Entwickler sind, die Vorlagen anpassen können. | [Jetzt testen!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML-Vorlagensprache](https://docs.adobe.com/content/help/de/experience-manager-htl/using/overview.html) | Alle Komponenten basieren auf HTL. |  |
| [eCommerce-Funktionen](/help/commerce/cif-classic/developing/ecommerce.md) | Umfassen einen Produktkatalog. |  |
| [Communities-Sites](/help/communities/overview.md) | Besucher können an Community-Diskussionen teilnehmen, Blogs lesen und vieles mehr. |  |
| [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) | Alle Komponenten basieren auf den neuen Kernkomponenten und sind standardmäßig benutzerfreundlicher und konfigurierbarer. | [Jetzt testen!](/help/sites-developing/we-retail-core-components.md) |
| [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) | Der Abschnitt „We.Retail Experiences“ veranschaulicht, wie sich über Inhalte mithilfe von Inhaltfragmenten wirkungsvoll wiederverwenden lassen. | [Jetzt testen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Experience Fragments](/help/sites-authoring/experience-fragments.md) | Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. | [Jetzt testen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Erste Schritte {#getting-started}

We.Retail wird als AEM-Beispielinhalte bereitgestellt. Um die Inhalte zu verwenden, [starten Sie AEM einfach wie gewohnt](/help/sites-deploying/deploy.md#getting-started). Stellen Sie dabei sicher, dass die Beispielinhalte nicht deaktiviert sind.

>[!CAUTION]
>
>We.Retail sollte nicht auf Produktionsinstanzen installiert werden. Produktionsinstanzen sollten in `nosamplecontent` [runmode](/help/sites-deploying/configure-runmodes.md) gestartet werden.

>[!CAUTION]
>
>We.Retail basiert auf der neuesten AEM-Technologie und bietet daher keine Unterstützung für [die Inhaltserstellung mit der klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/home.md).

### Neueste Version {#latest-version}

Obwohl We.Retail mit dem der AEM-Version bereitgestellt wird, werden die Inhalte und ihre Funktionen ggf. nach deren Veröffentlichung aktualisiert. Daher ist es möglich, [die neueste Version von GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) und [upload](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) und [install](/help/sites-administering/package-manager.md#installing-packages) als Paket auf Ihrer AEM Instanz herunterzuladen.

### Erste Schritte {#first-steps}

1. Sobald Sie AEM gestartet haben (und/oder We.Retail installiert ist), ist die Site **We.Retail** in der [Sites-Konsole](/help/sites-authoring/basic-handling.md#global-navigation) verfügbar.
1. Beispielsweise kann die folgende Seite geöffnet werden und sollte so aussehen, wie sie unten im [Anhang](#appendix) angezeigt wird:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## We.Retail und Geometrixx {#we-retail-geometrixx}

Geometrixx und seine vielen Varianten dienten als Beispielinhalte in früheren Versionen von AEM. Seit Version 6.3 stellt We.Retail die Beispielinhalte für AEM bereit und dient als neue standardmäßige Referenzimplementierung.

We.Retail ist technisch robuster und nutzt die neueste AEM-Technologie, um mehr Flexibilität und Skalierbarkeit zu bieten und gleichzeitig die neuesten Funktionen des Produkts zu demonstrieren.

### Funktionsvergleich {#feature-comparison}

Die folgende Tabelle stellt einen Überblick über die wichtigsten Funktionen bereit, die in We.Retail im Vergleich zu Geometrixx verfügbar sind.

* **Verfügbar** bedeutet, dass Beispiele der Funktion in den Beispielinhalten zu finden sind.
* **Nicht verfügbar** bedeutet, dass Beispiele der Funktion nicht in den Beispielinhalten vorhanden sind, aber nicht, dass die Funktion selbst nicht vorhanden ist.

| **Funktion** | **We.Retail** | **Geometrixx** |
|---|---|---|
| Globalisierte Site-Struktur | Sprachmaster live kopiert in länderspezifische Sites | Nicht verfügbar |
| Inhaltsfragmente | Verfügbar | Nicht verfügbar |
| Experience Fragments | Verfügbar | Nicht verfügbar |
| Responsives Layout   | Für alle Seiten | Nur Geometrixx Media |
| Bearbeitbare Vorlagen | Für alle Seiten | Nicht verfügbar |
| HTL | Alle Komponenten | Limited |
| Targeting | Für alle Seiten | Nur Geometrixx Outdoors |
| Screens | Verfügbar | Nicht verfügbar |
| Mobilgerät | Nicht verfügbar | Verfügbar |
| Manuskripte | Nicht verfügbar | Verfügbar |
| Karussell, Download, Diagrammkomponenten | Nicht verfügbar | Verfügbar |
| Spaltensteuerung | Ersetzt durch Layout-Container | Verfügbar |
| Formulare | Nicht verfügbar | Verfügbar |
| Campaign | Keine E-Mail-Beispiele | Verfügbar |

>[!NOTE]
>
>Diese Liste erhebt keinen Anspruch auf Vollständigkeit.

## Beitragen {#contribute}

We.Retail wurde als Open-Source-Projekt veröffentlicht und die neueste Version des Quellcodes kann von GitHub heruntergeladen werden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Open aem-sample-we-trading project on GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/archive/master.zip) herunter.

Die neueste Version kann auch [direkt als installierbares Paket heruntergeladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/latest) werden.

Sollten Sie Probleme haben, schreiben Sie bitte [GitHub-Probleme](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Mit [Pull-Requests](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) können Sie weiter ins Detail gehen und eigene Beiträge veröffentlichen.

## Vorschau {#preview}

Vorschau der We.Retail-Begrüßungsseite:

![screencapture-localhost-4502-editor-html-content-we-retail-us-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
