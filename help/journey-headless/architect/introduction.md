---
title: Adobe Experience Manager Headless-Tour für Inhaltsarchitektinnen und -architekten
description: Eine Einführung in die leistungsstarken und flexiblen Headless-Funktionen von Adobe Experience Manager und in die Modellierung von Content für Ihr Projekt.
exl-id: 49ba0d6d-dde4-42e2-92fd-c7655c0eebc0
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 96%
---
# Inhaltsmodellierung für Headless mit AEM – Einführung {#architect-headless-introduction}

In diesem Teil der [AEM Headless-Inhaltsarchitekten-Tour](overview.md) können Sie sich mit den (grundlegenden) Konzepten und der erforderlichen Terminologie vertraut machen, um die Inhaltsmodellierung für die Headless-Inhaltsbereitstellung mit Adobe Experience Manager (AEM) zu verstehen.

Dieses Dokument hilft Ihnen dabei, die Bereitstellung von Headless-Inhalten zu verstehen, und wie AEM Headless unterstützt und wie Inhalte für Headless modelliert werden. Nach dem Lesen sollten Sie:

* die grundlegenden Konzepte der Headless-Bereitstellung von Inhalten verstehen,
* damit vertraut sein, wie AEM Headless und Inhaltsmodellierung unterstützt.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung der Konzepte und Terminologie für die Headless-Inhaltsmodellierung.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

Bei einem Full-Stack-CMS befindet sich all die Funktionalität zum Bearbeiten Ihrer Inhalte im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Das Content-Authoring ist reibungslos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stack eingefügt werden, und Änderungen müssen nur an einer einzigen Stelle vorgenommen werden.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stacks wird jedoch schnell deutlich, da andere Elemente im Stack möglicherweise angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS den Content und stellt ihn für die Verbrauchenden bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Dienste – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, Progressive Web Apps (PWAs) usw. – beziehen Content aus dem Headless-CMS und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihren Content.

Das Weglassen des Head vereinfacht das CMS, indem die Komplexität reduziert wird. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Inhaltsmodellierung {#content-modeling}

Content-Modellierung (auch als Datenmodellierung bezeichnet) ist Ihre Spezialität. Was muss daher bei der Modellierung für Headless berücksichtigt werden?

Damit die Headless-Anwendungen auf Ihren Content zugreifen und etwas damit anfangen können, muss der Content wirklich über eine vordefinierte Struktur verfügen. Es wäre möglich, Ihre Inhalte frei zu gestalten, aber das würde das Leben für die Anwendungen *sehr* kompliziert machen.

Für AEM führen Sie als Inhaltsarchitekt die Inhaltsmodellierung durch, um eine Reihe von **Inhaltsfragmentmodellen** zu entwerfen. Diese definieren die Struktur, die verwendet wird, wenn Ihre Inhaltsautoren die **Inhaltsfragmente** erstellen, die die Inhalte enthalten.

### Zugreifen auf die Inhalte {#access-content}

Das ist eher ein Entwicklungsdetail – aber es könnte Sie interessieren, nur um das Gesamtbild zu vervollständigen.

Nachdem Sie die Inhaltsfragmentmodelle erstellt haben und Ihre Autorinnen und Autoren sie zur Erstellung des Content verwendet haben, müssen die Headless-Anwendungen auf diesen Content zugreifen.

Mit Adobe Experience Manager (AEM) können Sie über die AEM-GraphQL-API selektiv auf Ihre Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Mithilfe der API kann ein Entwickler Abfragen formulieren, die bestimmte Inhalte auswählen.Dieser Auswahlprozess basiert auf *Ihren* Inhaltsfragmentmodellen.

Dies bedeutet, dass Ihr Projekt die Headless-Bereitstellung strukturierter Inhalte zur Verwendung in Ihren Anwendungen realisieren kann.

## Wie geht es weiter {#whats-next}

Jetzt, da Sie die Konzepte und Terminologie gelernt haben, lautet der nächste Schritt [Kennenlernen der Grundlagen der Modellierung mit Inhaltsfragmentmodellen](basics.md).

## Zusätzliche Ressourcen {#additional-resources}

* AEM Headless-Entwickler-Tour
  * [Grundlegendes zur CMS-Headless-Entwicklung](/help/journey-headless/developer/learn-about.md)
  * [Erfahren Sie, wie Sie Ihr Content-Modell erstellen](/help/journey-headless/developer/model-your-content.md)
* [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)
* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Headless-Tutorials für AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
