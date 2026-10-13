---
title: Erfahren Sie mehr über Headless-Inhalte und wie Sie sie in AEM übersetzen können.
description: Lernen Sie die Headless-Konzepte, ihre Zuordnung zu AEM und die Theorie der Übersetzung in AEM kennen.
exl-id: cb2e2d89-e2d2-462f-8fff-b201847d0641
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Developer, User, Leader
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
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 100%
---
# Erfahren Sie mehr über Headless-Inhalte und wie Sie sie in AEM übersetzen können. {#learn-about}

Lernen Sie die Headless-Konzepte, ihre Zuordnung zu AEM und die Theorie der Übersetzung in AEM kennen.

## Ziel {#objective}

Dieses Dokument hilft Ihnen, die Bereitstellung von Headless-Inhalten zu verstehen, wie AEM Headless unterstützt und wie solche Inhalte übersetzt werden können. Nach dem Lesen sollten Sie:

* die grundlegenden Konzepte der Headless-Bereitstellung von Inhalten verstehen,
* damit vertraut sein, wie AEM Headless und Übersetzung unterstützt.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

Bei einem Full-Stack-CMS befindet sich all die Funktionalität zum Bearbeiten Ihrer Inhalte im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stack eingefügt werden und es gibt nur einen Ort, an dem Änderungen vorgenommen werden können.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stacks wird jedoch schnell deutlich, da andere Elemente im Stack möglicherweise angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS den Content und stellt ihn für die Verbrauchenden bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse oder Progressive Web-Apps (PWAs) – nehmen Inhalte aus dem Headless-CMS auf und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Weglassen des Head vereinfacht das CMS, indem die Komplexität reduziert wird. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Übersetzen von Headless-Inhalten in AEM {#translating-in-aem}

Zusätzlich zu den robusten Tools zum Erstellen, Verwalten und Bereitstellen herkömmlicher Web-Seiten im Full-Stack-Modus bietet AEM auch die Möglichkeit, eigenständige Inhaltsauswahlen zu erstellen und diese „headless“ bereitzustellen.

Die Leistungsfähigkeit von AEM ermöglicht es, Inhalte entweder „headless“, im Full Stack oder in beiden Modellen gleichzeitig bereitzustellen. Der Übersetzungsspezialisten kannn die gleichen Übersetzungs-Tools auf beide Inhaltstypen anwenden, sodass er einen einheitlichen Ansatz für die Übersetzung seiner Inhalte erhält.

Im weiteren Verlauf der Tour erfahren Sie mehr darüber, wie AEM Inhalte übersetzt, aber im Prinzip ist das Konzept ganz einfach:

1. Eine Verbindung zu einem Übersetzungsdienst wird definiert, indem das Translation Integration Framework (TIF) konfiguriert wird.
1. Mithilfe von Übersetzungsregeln wird festgelegt, welche Inhalte übersetzt werden sollen.
1. Ein Übersetzungsprojekt wird erstellt, um die Inhalte zu erfassen, sie an den Übersetzungsdienst zu senden und die Ergebnisse zu erhalten.
1. Die übersetzten Inhalte werden überprüft und veröffentlicht.

## So geht es weiter {#what-is-next}

Danke für Ihren Einstieg in die AEM Headless-Übersetzungs-Tour! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* die grundlegenden Konzepte der Headless-Bereitstellung von Inhalten verstehen,
* damit vertraut sein, wie AEM Headless und Übersetzung unterstützt.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM Headless-Übersetzungs-Tour fort, indem Sie als Nächstes das Dokument [Erste Schritte mit der AEM Headless-Übersetzung](getting-started.md) lesen, in dem Sie einen Überblick darüber erhalten, wie AEM Headless-Inhalte verwaltet und die Übersetzungs-Tools kennenlernen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Headless-Übersetzungs-Tour fortzufahren, indem Sie das Dokument [Erste Schritte mit der AEM Headless-Übersetzung](getting-started.md) lesen. Im Folgenden finden Sie jedoch einige zusätzliche, optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen, die aber nicht erforderlich sind, um mit der Headless-Tour fortzufahren.

* [MSM und Übersetzung](/help/sites-administering/msm-and-translation.md) – Die Details des Multi-Site-Managers von AEM und wie er mit seinen Übersetzungs-Tools zusammenarbeitet.
* Eine [Einführung in AEM als Headless-CMS](/help/sites-developing/headless/introduction.md)
* Das [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Headless-Tutorials für AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
