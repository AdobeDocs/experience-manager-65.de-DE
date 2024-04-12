---
title: Optional - Erstellen von Einzelseiten-Apps (SPA) mit Adobe Experience Manager
description: In dieser optionalen Fortsetzung der Adobe Experience Manager (AEM) Headless-Entwickler-Journey erfahren Sie, wie AEM Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen können.
exl-id: 91eadda2-b881-4e4a-867f-8c5c54e8f8b4
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 76%

---

# Erstellen von Single Page Applications (SPAs) mit AEM {#create-spa}

In dieser fakultativen Fortsetzung der [AEM Headless-Developer-Journey](overview.md) Hier erfahren Sie, wie Adobe Experience Manager (AEM) die Headless-Bereitstellung mit herkömmlichen Full-Stack-CMS-Funktionen kombinieren kann und wie Sie bearbeitbare SPA mit AEM Editor-Framework erstellen und externe SPA integrieren können, um Bearbeitungsfunktionen nach Bedarf zu ermöglichen.

## Die bisherige Entwicklung {#story-so-far}

An dieser Stelle sollten Sie die gesamte [AEM Headless-Entwickler-Tour](overview.md) abgeschlossen haben und die Grundlagen der Headless-Bereitstellung in AEM verstehen, einschließlich folgender Punkte:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt

Also sind Sie jetzt entweder mit Ihrem ersten AEM Headless-Projekt live gegangen oder haben das Wissen, dies zu tun. Herzlichen Glückwunsch!

Warum lesen Sie also diese optionale Fortsetzung der Tour? Wahrscheinlich erinnern Sie sich daran in der [Erste Schritte](getting-started.md#integration-levels), gab es eine kurze Diskussion darüber, wie AEM nicht nur Headless-Versand und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützen kann, die die Vorteile beider Modelle kombinieren. Obwohl es sich hierbei nicht um das traditionelle Headless-Modell handelt, können derartige Hybridmodelle für bestimmten Projekte eine beispiellose Flexibilität bieten.

Dieser Artikel baut auf Ihren Kenntnissen über AEM Headless auf und erläutert eingehend, wie Sie Ihre eigenen SPAs (Single Page Applications) erstellen können, die in AEM bearbeitbar sind. Auf diese Weise können Sie Inhalte erstellen und sie an einen SPA senden, dieser SPA bleibt jedoch in AEM bearbeitbar.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Single Page Applications mithilfe des AEM SPA Editor-Frameworks entwickelt werden. Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Verständnis der grundlegenden Funktion des SPA-Editors
* Kenntnis der Anforderungen zum Erstellen vollständig bearbeitbarer SPAs für AEM
* Kenntnis darüber, wie externe SPAs in AEM integriert werden können
* Erfahren Sie, wie serverseitiges Rendering implementiert werden sollte oder nicht.

## Anforderungen und Vorbedingungen {#requirements-prerequisites}

Bevor Sie in AEM mit SPAs arbeiten, müssen Sie einige Anforderungen erfüllen.

### Kenntnisse {#knowledge}

* Entwicklungserlebnis beim Erstellen von SPA mit React- oder Angular-Frameworks
* Grundlegende AEM-Kenntnisse zum Erstellen von Inhaltsfragmenten und Verwenden des Editors
* Überprüfen Sie unbedingt das Dokument. [Headless und Headless in AEM](/help/sites-developing/headful-headless.md) um die verschiedenen Ebenen der möglichen SPA zu verstehen.

### Tools {#tools}

* Sandbox-Zugriff zum Testen der Bereitstellung Ihres Projekts
* Lokale Entwicklungsinstanz für Datenmodellierung und -tests
* Vorhandene externe SPA (optional, je nach ausgewähltem Integrationsmodell)
* AEM-Projektarchetyp

## Was ist eine SPA? {#what-is-a-spa}

Eine Single Page Application (SPA) unterscheidet sich von einer herkömmlichen Seite insofern, als sie Client-seitig gerendert wird und primär JavaScript-gesteuert ist. Dabei wird auf Ajax-Aufrufe zurückgegriffen, um Daten zu laden und die Seite dynamisch zu aktualisieren. Der Großteil der Inhalte oder alle Inhalte werden einmal in einem einzelnen Seiten-Load abgerufen, wobei je nach Benutzerinteraktion mit der Seite asynchron zusätzliche Ressourcen geladen werden.

So wird der Bedarf nach Seitenaktualisierungen reduziert und dem Benutzer ein Erlebnis präsentiert, das nahtlos und schnell ist und eher wie eine native App funktioniert.

Der AEM-SPA-Editor ermöglicht es Frontend-Entwicklungspersonen, SPAs zu erstellen, die sich in eine AEM-Site integrieren lassen, damit Inhaltsautorinnen und -autoren SPA-Inhalte so einfach bearbeiten können wie alle anderen AEM-Inhalte.

## Warum eine SPA? {#why-spa}

Da eine SPA schneller, nahtloser und eher wie eine native Anwendung ist, wird sie nicht nur für den Besucher der Webseite, sondern auch für Marketing-Experten und Entwickler attraktiv, da SPA funktioniert.

Eine vollständige Beschreibung von SPAs sowie Gründe für ihre Verwendung finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Wie AEM SPAs verarbeitet

Bei der Entwicklung von Single Page Applications in AEM wird davon ausgegangen, dass sich der Frontend-Entwickler beim Erstellen einer SPA an die üblichen Best Practices hält. Wenn Sie als Frontend-Entwickler diese allgemeinen Best Practices und einige AEM-spezifische Prinzipien befolgen, wird Ihre SPA mit AEM und den Inhaltsbearbeitungsfunktionen funktionieren.

* **Portabilität**: Wie alle anderen Komponenten auch sollten die SPA-Komponenten so portabel wie möglich gestaltet werden. Die SPA sollte aus portablen und wiederverwendbaren Komponenten bestehen.
* **AEM verwaltet die Site-Struktur**: Die Frontend-Entwicklungsperson erstellt Komponenten und ist für deren interne Struktur verantwortlich, verlässt sich für die Definition der Inhaltsstruktur der Site jedoch auf AEM.
* **Dynamisches Rendering**: Alle Rendering-Vorgänge sollten dynamisch sein.
* **Dynamisches Routing**: Die SPA ist für das Routing verantwortlich; AEM lauscht darauf und ruft Inhalte auf dieser Basis ab. Jegliches Routing sollte ebenfalls dynamisch sein.

Eine vollständige Beschreibung, wie AEM SPAs verarbeitet, finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Der SPA-Editor von AEM {#aem-spa-editor}

Sites, die mit gängigen SPA-Frameworks wie React und Angular erstellt wurden, laden ihren Inhalt über dynamisches JSON und weisen nicht die HTML-Struktur auf, die für den Seiteneditor von AEM erforderlich ist, um Steuerelemente zur Bearbeitung platzieren zu können.

Um die Bearbeitung von SPA in AEM zu aktivieren, ist eine Zuordnung zwischen der JSON-Ausgabe der SPA und dem Inhaltsmodell im AEM-Repository erforderlich, um Änderungen am Inhalt zu speichern.

Die SPA-Unterstützung in AEM führt eine dünne JS-Schicht ein, die mit dem SPA-JS-Code interagiert, wenn dieser in den Seiteneditor geladen wird, mit dem Ereignisse gesendet und die Position für die Bearbeitungssteuerelemente aktiviert werden können, um eine kontextbezogene Bearbeitung zu ermöglichen. Diese Funktion baut auf dem Konzept des Content Services API-Endpunkts auf, da der Inhalt aus der SPA über Content Services geladen werden muss.

Eine vollständige Beschreibung des AEM-SPA-Editors finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) mit Links zu ausführlicheren Dokumentationen.

## Berücksichtigung vorhandener SPAs {#existing-spas}

Wenn Sie bereits über eine SPA verfügen, unterstützt AEM das Einbetten in AEM, damit diese für Ihre Inhaltsautorinnen und -autoren im AEM-Editor sichtbar ist. Dies kann nützlich sein, um die Inhalte anzuzeigen, die über Inhaltsfragmente im Kontext der Endanwendung erstellt werden, in der sie verwendet werden.

Darüber hinaus können Sie im AEM-Editor mit nur kleinen Änderungen bestimmte Bearbeitungsmöglichkeiten für die externe SPA aktivieren.

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
* [Server-seitiges Rendern](/help/sites-developing/spa-ssr.md): So konfigurieren Sie SSR für AEM-SPAs
* [SPA-Referenzdokumente](/help/sites-developing/spa-reference-materials.md): JavaScript-API-Referenzen und Links zu den Open-Source-AEM-SPA-GitHub-Projekten
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) –Anleitung zur Erstellung von Inhaltsfragmenten
* Der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) ist eine Maven-Vorlage, anhand derer ein minimales, auf Best Practices basierendes Adobe Experience Manager (AEM)-Projekt als Ausgangspunkt für Ihre Website erstellt wird.
