---
title: Optional – Erstellen von Single Page Applications (SPAs) mit AEM
description: In dieser optionalen Fortsetzung der AEM Headless-Entwickler-Tour erfahren Sie, wie AEM Headless-Bereitstellungen mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann und wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen können.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
source-git-commit: 7b97bc0ffb0df6641ae71fa36c459f1368052e12
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 100%

---

# Erstellen von Single Page Applications (SPAs) mit AEM {#create-spa}

In dieser optionalen Fortsetzung der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie AEM Headless-Bereitstellungen mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann und wie Sie mit dem SPA-Editor-Framework von AEM bearbeitbare SPAs erstellen sowie externe SPAs integrieren können, um nach Bedarf Bearbeitungen zu ermöglichen.

## Die bisherige Entwicklung {#story-so-far}

An dieser Stelle sollten Sie die gesamte [AEM Headless-Entwickler-Tour](overview.md) abgeschlossen haben und die Grundlagen der Headless-Bereitstellung in AEM verstehen, einschließlich folgender Punkte:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt

Sie haben inzwischen Ihr ersten AEM Headless-Projekt live geschaltet bzw. verfügen über die entsprechenden Kenntnisse. Herzlichen Glückwunsch!

Warum lesen Sie also diese optionale Fortsetzung der Tour? Wahrscheinlich erinnern Sie sich daran, dass wir in [Erste Schritte](getting-started.md#integration-levels) kurz besprochen haben, wie AEM nicht nur die Headless-Bereitstellung und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützen kann, die die Vorteile beider Modelle kombinieren. Obwohl es sich hierbei nicht um das traditionelle Headless-Modell handelt, können derartige Hybridmodelle für bestimmten Projekte eine beispiellose Flexibilität bieten.

Dieser Artikel baut auf Ihren Kenntnissen über AEM Headless auf und erläutert eingehend, wie Sie Ihre eigenen SPAs erstellen können, die in AEM bearbeitbar sind. Auf diese Weise können Sie Inhalte erstellen und „headless“ für SPAs bereitstellen, wobei diese SPAs jedoch in AEM bearbeitbar bleiben.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Single Page Applications mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach Lesen dieses Dokuments sollten Sie über Folgendes verfügen:

* Verständnis der grundlegenden Funktion des SPA-Editors
* Kenntnis der Anforderungen zum Erstellen vollständig bearbeitbarer SPAs für AEM
* Kenntnis darüber, wie externe SPAs in AEM integriert werden können
* Verständnis, wie das Server-seitige Rendering implementiert werden sollte oder nicht

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Bevor Sie in AEM mit SPAs arbeiten, müssen Sie eine Reihe von Anforderungen erfüllen.

### Kenntnisse {#knowledge}

* Entwicklungserlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM-Kenntnisse zum Erstellen von Inhaltsfragmenten und Verwenden des Editors
* Lesen Sie das Dokument [Headful und Headless in AEM](/help/sites-developing/headful-headless.md), um die verschiedenen Ebenen der SPA-Integration zu verstehen.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Implementierung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

So wird der Bedarf nach Seitenaktualisierungen reduziert und dem Benutzer ein Erlebnis präsentiert, das nahtlos und schnell ist und eher wie eine native App funktioniert.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklern, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautoren SPA-Inhalte so einfach bearbeiten können wie andere AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da SPAs schneller, nahtloser und eher wie ein natives Programm sind, sind sie nicht nur für Besucher der Web-Seite, sondern auch für Marketing-Experten und Entwickler attraktiv. Das hängt mit der Art und Weise zusammen, wie SPAs funktionieren.

Eine vollständige Beschreibung von SPAs sowie Gründe für ihre Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie AEM SPAs verarbeitet

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices sowie einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und seinen Inhaltserstellungsfunktionen zusammenarbeiten.

* **Portabilität**: Wie alle anderen Komponenten auch sollten die SPA-Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur**: Der Frontend-Entwickler erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich bei der Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung, wie AEM SPAs verarbeitet, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Der SPA-Editor von AEM {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON und weisen nicht die HTML-Struktur auf, die für den Seiteneditor von AEM erforderlich ist, um Steuerelemente zur Bearbeitung platzieren zu können.

Um die Bearbeitung von SPAs innerhalb von AEM zu ermöglichen, ist eine Zuordnung zwischen der JSON-Ausgabe der SPA und dem Inhaltsmodell im AEM-Repository erforderlich, damit Änderungen am Inhalt gespeichert werden können.

Mit der SPA-Unterstützung wird in AEM ein JS-Thin Layer eingeführt. Dieses interagiert mit dem SPA-JS-Code, wenn es in den Seiten-Editor geladen wird, mit dem Ereignisse gesendet und der Speicherort für die Steuerelemente zur Bearbeitung aktiviert werden kann, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Content Services API Endpoint-Konzept auf, da die Inhalte aus der SPA über Content Services geladen werden müssen.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Berücksichtigung vorhandener SPAs {#existing-spas}

Wenn Sie über eine vorhandene SPA verfügen, unterstützt AEM das Einbetten in AEM, damit diese für Ihre Inhaltsautoren im AEM-Editor sichtbar ist. Dies kann sehr nützlich sein, um die Inhalte anzuzeigen, die über Inhaltsfragmente im Kontext des Endprogramms erstellt werden, in dem sie verwendet werden.

Darüber hinaus können Sie mit nur kleinen Änderungen bestimmte Bearbeitungsmöglichkeiten für die externe SPA im AEM-Editor aktivieren.

Die RemotePage-Komponente ermöglicht das Rendern externer SPAs in AEM.

Eine vollständige Beschreibung dazu, wie sich externe SPAs in AEM bearbeiten lassen, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie geht es weiter {#what-is-next}

Lesen Sie die folgenden Dokumente, um mit der Entwicklung Ihrer eigenen SPAs für AEM zu beginnen:

* [SPA-WKND-Tutorial](/help/sites-developing/spa-wknd.md)
* [Erste Schritte mit React](/help/sites-developing/spa-getting-started-react.md)
* [Erste Schritte mit Angular](/help/sites-developing/spa-getting-started-angular.md)

Wenn Sie eine vorhandene SPA anpassen müssen, um sie in AEM zu verwenden, lesen Sie die folgenden Dokumente:

* [Die RemotePage-Komponente](/help/sites-developing/spa-remote-page.md)
* [Bearbeiten einer externen SPA in AEM](/help/sites-developing/spa-edit-external.md)

Nachfolgend finden Sie [zusätzliche Ressourcen](#additional-resources) mit weiterführenden Informationen zu SPA-Themen in AEM.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie einige zusätzliche Ressourcen, die näher auf einige der in diesem Dokument erwähnten Konzepte eingehen.

* [Headful und Headless in AEM](/help/sites-developing/headful-headless.md) – eine Beschreibung der verschiedenen in AEM verfügbaren Bereitstellungsmodelle
* [SPA-Einführung und exemplarische Vorgehensweise.](/help/sites-developing/spa-walkthrough.md) – eine Einführung zu SPAs in AEM
* [Entwickeln von SPAs für AEM](/help/sites-developing/spa-architecture.md) – Orientierungshilfe für die Entwicklung von SPAs für AEM
* [SPA-Editor – Überblick](/help/sites-developing/spa-overview.md) – Details zur Funktionsweise des SPA-Editors
* [Server-seitiges Rendering](/help/sites-developing/spa-ssr.md) – Anleitung zum Konfigurieren von SSR für SPAs in AEM
* [Single Page Applications (SPAs) und Server-seitiges Rendering](/help/sites-developing/spa-reference-materials.md) – JavaScript-API-Referenzen und Links zu den Open-Source-Projekten in GitHub für SPAs in AEM
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) –Anleitung zur Erstellung von Inhaltsfragmenten
* Der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) ist eine Maven-Vorlage, anhand derer ein minimales, auf Best Practices basierendes Adobe Experience Manager (AEM)-Projekt als Ausgangspunkt für Ihre Website erstellt wird.
