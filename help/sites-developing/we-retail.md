---
title: We.Retail-Referenzimplementierung
description: We.Retail ist eine Technologievorschau einer Referenzimplementierung, die die empfohlene Methode zur Einrichtung einer Online-Präsenz mit AEM veranschaulicht.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 504c61c7-dcd3-412c-9239-d24a2b78e4b9
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 39%

---

# We.Retail-Referenzimplementierung{#we-retail-reference-implementation}

## Einführung {#introduction}

We.Retail ist eine Referenzimplementierung und Beispielinhalte, die die empfohlene Methode zur Einrichtung einer Online-Präsenz mit Adobe Experience Manager veranschaulicht.

We.Retail verwendet die neuesten AEM Technologien wie HTL, responsive Layouts, bearbeitbare Vorlagen, Kernkomponenten und vieles mehr.

Obwohl es eine Einzelhandelsbranche veranschaulicht, kann die Einrichtung der Site auf jede Vertikale angewendet werden, und nur die Produktkatalog- und Warenkorbfunktionen sind für den Einzelhandel spezifisch.

## Funktionen {#features}

Als AEM standardmäßige Referenzimplementierung zeigt We.Retail einige der leistungsstärksten Funktionen von AEM.

| **Funktion** | **Beschreibung** | **Interessiert?** |
|---|---|---|
| [Globalisierte Site-Struktur](/help/sites-administering/tc-bp.md) | We.Retail enthält Sprach-Master, die live in länderspezifische Sites kopiert werden. | [Jetzt testen!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Responsives Layout](/help/sites-authoring/responsive-layout.md) | Alle Seiten verfügen über ein responsives Layout, um sich dynamisch an die Bildschirm- und Gerätegröße anzupassen. | [Jetzt testen!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) | Alle Seiten basieren auf bearbeitbaren Vorlagen, sodass Nicht-Entwickler die Vorlagen anpassen und anpassen können. | [Jetzt testen!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML-Vorlagensprache](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) | Alle Komponenten basieren auf HTL |  |
| [eCommerce-Funktionen](/help/commerce/cif-classic/developing/ecommerce.md) | Produktkatalog |  |
| [Communities-Sites](/help/communities/overview.md) | Besucher können an Community-Diskussionen teilnehmen, Blogs lesen und vieles mehr |  |
| [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) | Alle Komponenten basieren auf den neuen Kernkomponenten und sind benutzerfreundlicher und benutzerkonfigurierbarer | [Jetzt testen!](/help/sites-developing/we-retail-core-components.md) |
| [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) | Der Abschnitt &quot;We.Retail-Erlebnisse&quot;zeigt die Möglichkeiten der Wiederverwendung von Inhalten über Inhaltsfragmente. | [Jetzt testen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Experience Fragments](/help/sites-authoring/experience-fragments.md) | Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. | [Jetzt testen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Erste Schritte {#getting-started}

We.Retail wird als AEM Beispielinhalt bereitgestellt. Zur Verwendung einfach [AEM wie gewohnt](/help/sites-deploying/deploy.md#getting-started), um sicherzustellen, dass der Beispielinhalt nicht deaktiviert ist.

>[!CAUTION]
>
>Installieren Sie We.Retail nicht auf Produktionsinstanzen. Produktionsinstanzen sollten in gestartet werden `nosamplecontent` [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md).

>[!CAUTION]
>
>We.Retail basiert auf der neuesten AEM-Technologie und bietet daher keine Unterstützung für [die Inhaltserstellung mit der klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/home.md).

### Neueste Version {#latest-version}

Obwohl We.Retail mit dem der AEM-Version bereitgestellt wird, werden die Inhalte und ihre Funktionen ggf. nach deren Veröffentlichung aktualisiert. Daher können Sie [die neueste Version von GitHub herunterladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) und anschließend als Paket [hochladen](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) und auf Ihrer AEM-Instanz [installieren](/help/sites-administering/package-manager.md#installing-packages).

### Erste Schritte {#first-steps}

1. Nachdem AEM gestartet wurde (und/oder We.Retail installiert ist), wird die Site **We.Retail** ist im Abschnitt [Sites-Konsole](/help/sites-authoring/basic-handling.md#global-navigation).
1. Die folgende Seite kann beispielsweise geöffnet werden und sollte so aussehen, wie sie in der [Anhang](#appendix) unten:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## We.Retail &amp; Geometrixx {#we-retail-geometrixx}

Geometrixx und seine vielen Nelken dienten in früheren Versionen von AEM als Beispielinhalt. Seit Version 6.3 ist We.Retail der mit AEM bereitgestellte Beispielinhalt und dient als neue standardmäßige Referenzimplementierung.

We.Retail ist technisch robuster und nutzt die neueste AEM-Technologie, um flexibler und skalierbarer zu werden, während gleichzeitig die neuesten Funktionen des Produkts demonstriert werden.

### Funktionsvergleich {#feature-comparison}

Die folgende Tabelle bietet einen Überblick über die wichtigsten Funktionen, die in We.Retail im Vergleich zu Geometrixx verfügbar sind.

* **Verfügbar** bedeutet, dass im Beispielinhalt Beispiele für die Funktion gefunden werden.
* **Nicht verfügbar** bedeutet, dass Beispiele für die Funktion nicht im Beispielinhalt verfügbar sind, aber nicht, dass die Funktion selbst nicht verfügbar ist.

| **Funktion** | **We.Retail** | **Geometrixx** |
|---|---|---|
| Globalisierte Site-Struktur | Primäre Sprachen werden live in länderspezifische Sites kopiert | Nicht verfügbar |
| Inhaltsfragmente | Verfügbar | Nicht verfügbar |
| Experience Fragments  | Verfügbar | Nicht verfügbar |
| Responsives Layout | Für alle Seiten | Nur Geometrixx Media |
| Bearbeitbare Vorlagen | Für alle Seiten | Nicht verfügbar |
| HTL | Alle Komponenten | Limited |
| Targeting | Für alle Seiten | Nur Geometrixx Outdoors |
| Screens | Verfügbar | Nicht verfügbar |
| Mobilgerät | Nicht verfügbar | Verfügbar |
| Manuskripte | Nicht verfügbar | Verfügbar |
| Karussell, Download, Diagrammkomponenten | Nicht verfügbar | Verfügbar |
| Spalten-Steuerung | Ersetzt durch Layout-Container | Verfügbar |
| Formulare | Nicht verfügbar | Verfügbar |
| Campaign | Keine E-Mail-Beispiele | Verfügbar |

>[!NOTE]
>
>Diese Liste ist vollständig, sollte jedoch nicht als vollständig betrachtet werden.

## Beitragen {#contribute}

We.Retail wurde als Open-Source-Projekt veröffentlicht und die neueste Version des Quellcodes kann von GitHub heruntergeladen werden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen des Projekts aem-sample-we-retail auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Laden Sie das Projekt als [ZIP-Datei](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master) herunter.

Die neueste Version kann auch [direkt als installierbares Paket heruntergeladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) werden.

Wenn Probleme auftreten, müssen Sie eine [GitHub-Problem](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Mit [Pull-Requests](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) können Sie weiter ins Detail gehen und eigene Beiträge veröffentlichen.

## Vorschau {#preview}

Vorschau der We.Retail-Begrüßungsseite:

![screenCapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
