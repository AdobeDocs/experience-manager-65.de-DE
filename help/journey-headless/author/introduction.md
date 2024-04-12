---
title: Authoring für Headless mit Adobe Experience Manager
description: Eine Einführung in die leistungsstarken und flexiblen, Headless-Funktionen von Adobe Experience Manager und die Erstellung von Inhalten für Ihr Projekt.
exl-id: 39d2218a-4f11-459d-8514-cfd312246be5
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Architect,Data Architect,Developer,User,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 96%

---

# Authoring für Headless mit AEM – Einführung {#author-headless-introduction}

In diesem Teil der [AEM Headless-Inhaltsautoren-Tour](overview.md) können Sie sich mit den (grundlegenden) Konzepten und der erforderlichen Terminologie vertraut machen, um die Erstellung von Inhalten für die Headless-Inhaltsbereitstellung mit Adobe Experience Manager (AEM) zu verstehen..

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung der Konzepte und der Terminologie für Headless-Authoring.

## Content Management System (CMS) {#content-management-system}

Was ist ein Content Management System?

Ein Content Management System (CMS) ist genau das, was es sagt – ein Computersystem, das zum Verwalten von Inhalten verwendet wird. Das ist etwas allgemein, genauer gesagt wird es (normalerweise) für die Verwaltung von Inhalten verwendet, die Sie auf Ihren Websites zur Verfügung stellen möchten.

## Headless-CMS {#headless-cms}

Der Begriff „Headless“ bezeichnet Systeme, bei denen der Inhalt von der Art und Weise, wie er im Web angezeigt wird, getrennt wird.

Üblicherweise würden Sie Ihre Inhalte in einem CMS verwalten und dasselbe CMS wäre für die Wiedergabe dieser Inhalte auf Ihren Webseiten verantwortlich.

Headless bedeutet jetzt, dass Ihr Content-Set im CMS verwaltet und dann von einer oder mehreren (unabhängigen) Anwendungen aufgerufen werden kann.

Das bedeutet, dass Ihre Inhalte auf jedem Gerät und in einer Vielzahl von Formaten bereitgestellt werden können. Dadurch wird der gesamte Prozess viel flexibler und Sie müssen sich auch keine Gedanken über Layout und Formatierung machen.

>[!NOTE]
>
>Wenn Sie mehr über die technischen Details von Headless-CMS erfahren möchten, können Sie weitere Informationen unter „Grundlegendes zur CMS-Headless-Entwicklung“ lesen.

## Adobe Experience Manager {#aem-cms}

Was ist AEM?

Zunächst einmal ist AEM ein Content Management System mit einer Vielzahl von Funktionen, die auch an Ihre Anforderungen angepasst werden können.

Dies bedeutet, dass es wie folgt verwendet werden kann:

* Headless-CMS
   * Bei Headless können Ihre Inhalte als **Inhaltsfragmente** verfasst werden.
Hierbei handelt es sich um eigenständige Inhaltselemente, auf die von einer Reihe von Anwendungen direkt zugegriffen werden kann, da sie eine vordefinierte Struktur aufweisen, die auf **Inhaltsfragmentmodellen** basiert.
Das bedeutet, dass Ihre Inhalte eine breite Palette von Geräten in einer Vielzahl von Formaten und mit einer großen Auswahl an Funktionen erreichen können.
(Und als Doppelvorteil können diese Fragmente auch beim Erstellen von AEM-Web-Seiten verwendet werden – falls gewünscht.)

* „Traditionelles“ CMS
   * Inhalte werden für Web-Seiten erstellt, wobei eine Reihe von Komponenten verwendet wird, die definieren, wie der Inhalt auf Ihrer Website dargestellt wird. Auch hier ist AEM äußerst flexibel, da Ihr Projektteam benutzerdefinierte Komponenten entwickeln kann.

## Inhaltsmodellierung {#content-modeling}

Die Inhaltsmodellierung (auch als Datenmodellierung bezeichnet) ist ein weiterer technischer Begriff. Warum sollte sie Sie als Autor interessieren?

Damit die Headless-Anwendungen auf Ihre Inhalte zugreifen und etwas damit anfangen können, muss Ihr Inhalt wirklich über eine vordefinierte Struktur verfügen. Es wäre möglich, Ihre Inhalte frei zu gestalten, aber das würde das Leben für die Anwendungen *sehr* kompliziert machen.

Grundsätzlich umfasst der Prozess der Definition der Struktur für Ihre Inhalte das Entwerfen eines Modells – das als Datenmodellierung bezeichnet wird.

In AEM übernimmt die Rolle des Inhaltsarchitekten (oft eine andere Person) die Datenmodellierung, um eine Reihe von **Inhaltsfragmentmodellen** zu entwerfen, die Sie dann mit Hilfe von **Inhaltsfragmenten** als Grundlage für Ihre Inhalte verwenden.

>[!NOTE]
>
>Wenn Sie mehr über die Datenmodellierung erfahren möchten, können Sie unter der AEM Headless-Inhaltsarchitekten-Tour mehr darüber lesen.

## Wie geht es weiter {#whats-next}

Jetzt, da Sie die Konzepte und Terminologie gelernt haben, lautet der nächste Schritt: [Erfahren Sie mehr über die Grundlagen zum Erstellen von Inhaltsfragmenten](basics.md). Dies stellt die grundlegende Handhabung von AEM zusammen mit der Erstellung von Inhaltsfragmenten vor.

## Zusätzliche Ressourcen {#additional-resources}

* AEM Headless-Entwickler-Tour
   * [Grundlegendes zur CMS-Headless-Entwicklung](/help/journey-headless/developer/learn-about.md)

* [AEM Headless-Inhaltsarchitekten-Tour](/help/journey-headless/architect/overview.md)

* [AEM Headless-Übersetzungs-Tour](/help/journey-headless/translation/overview.md)

* [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)

* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)

* [Headless-Tutorials für AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
