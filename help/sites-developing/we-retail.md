---
title: We.Retail-Referenzimplementierung
description: We.Retail ist eine Technologievorschau einer Referenzimplementierung, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit AEM veranschaulicht.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 504c61c7-dcd3-412c-9239-d24a2b78e4b9
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 100%

---

# We.Retail-Referenzimplementierung{#we-retail-reference-implementation}

## Einführung {#introduction}

We.Retail ist eine Referenzimplementierung mit Beispielinhalten, die die empfohlene Vorgehensweise zum Einrichten einer Online-Präsenz mit Adobe Experience Manager veranschaulicht.

We.Retail nutzt die neuesten Adobe Experience Manager(AEM)-Technologien, darunter HTL, responsive Layouts, bearbeitbare Vorlagen und Kernkomponenten.

Die Vorgehensweisen werden zwar an Beispielen aus dem Einzelhandel erläutert, aber die Art und Weise, wie die Site eingerichtet ist, lässt sich auch auf jede andere Branche anwenden. Lediglich die Produktkatalog- und Warenkorbfunktionen sind spezifisch für den Einzelhandel.

## Funktionen {#features}

Als standardmäßige AEM-Referenzimplementierung zeigt We.Retail einige der leistungsstärksten Funktionen von AEM.

| **Funktion** | **Beschreibung** | **Interessiert?** |
|---|---|---|
| [Globalisierte Site-Struktur](/help/sites-administering/tc-bp.md) | We.Retail enthält Sprachprimäre, die live in länderspezifische Sites kopiert werden. | [Jetzt testen!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [Responsives Layout](/help/sites-authoring/responsive-layout.md) | Alle Seiten verfügen über ein responsives Layout, das sich dynamisch an die Bildschirm- und Gerätegröße anpasst. | [Jetzt testen!](/help/sites-developing/we-retail-responsive-layout.md) |
| [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md) | Alle Seiten basieren auf bearbeitbaren Vorlagen, sodass auch Benutzende ohne Entwicklerkenntnisse die Vorlagen anpassen können. | [Jetzt testen!](/help/sites-developing/we-retail-editable-templates.md) |
| [HTML-Vorlagensprache](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) | Alle Komponenten basieren auf HTL. |  |
| [E-Commerce-Funktionen](/help/commerce/cif-classic/developing/ecommerce.md) | Hierzu gehört ein Produktkatalog. |  |
| [Community-Sites](/help/communities/overview.md) | Besucherinnen und Besucher können an Community-Diskussionen teilnehmen, Blogs lesen und vieles mehr. |  |
| [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) | Alle Komponenten basieren auf den neuen Kernkomponenten und sind standardmäßig noch benutzerfreundlicher und einfacher konfigurierbar. | [Jetzt testen!](/help/sites-developing/we-retail-core-components.md) |
| [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) | Der Abschnitt „We.Retail Experiences“ veranschaulicht, wie sich Inhalte mithilfe von Inhaltsfragmenten wirkungsvoll wiederverwenden lassen. | [Jetzt testen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Experience Fragments](/help/sites-authoring/experience-fragments.md) | Ein Experience Fragment ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. | [Jetzt testen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Erste Schritte {#getting-started}

We.Retail wird als AEM-Beispielinhalt bereitgestellt. Um den Inhalt zu verwenden, [starten Sie AEM einfach wie gewohnt](/help/sites-deploying/deploy.md#getting-started). Stellen Sie dabei sicher, dass die Beispielinhalte nicht deaktiviert sind.

>[!CAUTION]
>
>Installieren Sie We.Retail nicht in Produktionsinstanzen. Produktionsinstanzen sollten im [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) `nosamplecontent` gestartet werden.

>[!CAUTION]
>
>We.Retail basiert auf der neuesten AEM-Technologie und bietet daher keine Unterstützung für [die Inhaltserstellung mit der klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/classic-page-author-first-steps.md).

### Neueste Version {#latest-version}

Obwohl We.Retail mit dem der AEM-Version bereitgestellt wird, werden die Inhalte und ihre Funktionen ggf. nach deren Veröffentlichung aktualisiert. Daher können Sie [die neueste Version von GitHub herunterladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) und anschließend als Paket [hochladen](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) und auf Ihrer AEM-Instanz [installieren](/help/sites-administering/package-manager.md#installing-packages).

### Erste Schritte {#first-steps}

1. Sobald AEM gestartet wurde (und/oder We.Retail installiert ist), ist die Site **We.Retail** in der [Sites-Konsole](/help/sites-authoring/basic-handling.md#global-navigation) verfügbar.
1. Beispielsweise kann die folgende Seite geöffnet werden und sollte so aussehen, wie sie unten im [Anhang](#appendix) angezeigt wird:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## We.Retail und Geometrixx {#we-retail-geometrixx}

Geometrixx und seine vielen Varianten dienten als Beispielinhalte in früheren Versionen von AEM. Seit Version 6.3 ist We.Retail der mit AEM bereitgestellte Beispielinhalt und dient als neue standardmäßige Referenzimplementierung.

We.Retail ist technisch robuster und nutzt die neueste AEM-Technologie, um mehr Flexibilität und Skalierbarkeit zu bieten und gleichzeitig die neuesten Funktionen des Produkts zu demonstrieren.

### Funktionsvergleich {#feature-comparison}

Die folgende Tabelle stellt einen Überblick über die wichtigsten Funktionen bereit, die in We.Retail im Vergleich zu Geometrixx verfügbar sind.

* **Verfügbar** bedeutet, dass Beispiele der Funktion in den Beispielinhalten zu finden sind.
* **Nicht verfügbar** bedeutet, dass Beispiele der Funktion nicht in den Beispielinhalten vorhanden sind, aber nicht, dass die Funktion selbst nicht vorhanden ist.

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
| Karussell-Viewer, Downloads und Diagrammkomponenten | Nicht verfügbar | Verfügbar |
| Spalten-Steuerung | Ersetzt durch Layout-Container | Verfügbar |
| Formulare | Nicht verfügbar | Verfügbar |
| Campaign | Keine E-Mail-Beispiele | Verfügbar |

>[!NOTE]
>
>Diese Liste erhebt keinen Anspruch auf Vollständigkeit.

## Beitragen {#contribute}

We.Retail wurde als Open-Source-Projekt veröffentlicht. Die neueste Version des Quell-Codes kann von GitHub heruntergeladen werden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen des Projekts aem-sample-we-retail auf GitHub.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Laden Sie das Projekt als [ZIP-Datei](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master) herunter.

Die neueste Version kann auch [direkt als installierbares Paket heruntergeladen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) werden.

Wenn Sie auf Probleme stoßen, öffnen Sie ein [GitHub-Ticket](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Mit [Pull-Requests](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) können Sie weiter ins Detail gehen und eigene Beiträge veröffentlichen.

## Vorschau {#preview}

Vorschau der We.Retail-Begrüßungsseite:

![screenCapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
