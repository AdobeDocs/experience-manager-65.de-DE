---
title: Erfahren Sie mehr über Headless-Inhalte und wie Sie sie in AEM übersetzen können.
description: Lernen Sie die Headless-Konzepte, ihre Zuordnung zu AEM und die Theorie der Übersetzung in AEM kennen.
exl-id: cb2e2d89-e2d2-462f-8fff-b201847d0641
source-git-commit: ed11891c27910154df1bfec6225aecd8a9245bff
workflow-type: tm+mt
source-wordcount: '727'
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

In einem Full-Stack-CMS befindet sich die gesamte Funktionalität zum Bearbeiten Ihrer Inhalte im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stack eingefügt werden und es gibt nur einen Ort, an dem Änderungen vorgenommen werden können.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stacks wird jedoch schnell deutlich, da andere Elemente im Stack möglicherweise angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, Progressive Web Apps (PWAs) usw. – nehmen Inhalte aus dem Headless-CMS auf und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Übersetzen von Headless-Inhalten in AEM {#translating-in-aem}

Zusätzlich zu den robusten Tools zum Erstellen, Verwalten und Bereitstellen herkömmlicher Web-Seiten im Full-Stack-Modus bietet AEM auch die Möglichkeit, eigenständige Inhaltsauswahlen zu erstellen und diese „headless“ bereitzustellen.

Die Leistungsfähigkeit von AEM ermöglicht es, Inhalte entweder „headless“, im Full Stack oder in beiden Modellen gleichzeitig bereitzustellen. Der Übersetzungsspezialisten kannn die gleichen Übersetzungs-Tools auf beide Inhaltstypen anwenden, sodass er einen einheitlichen Ansatz für die Übersetzung seiner Inhalte erhält.

Im weiteren Verlauf der Tour erfahren Sie mehr darüber, wie AEM Inhalte übersetzt, aber im Prinzip ist das Konzept ganz einfach:

1. Eine Verbindung zu einem Übersetzungsdienst wird definiert, indem das Translation Integration Framework (TIF) konfiguriert wird.
1. Mithilfe von Übersetzungsregeln wird festgelegt, welche Inhalte übersetzt werden sollen.
1. Ein Übersetzungsprojekt wird erstellt, um die Inhalte zu erfassen, sie an den Übersetzungsdienst zu senden und die Ergebnisse zu erhalten.
1. Die übersetzten Inhalte werden überprüft und veröffentlicht.

## Wie geht es weiter {#what-is-next}

Danke für Ihren Einstieg in die AEM Headless-Übersetzungs-Tour! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* die grundlegenden Konzepte der Headless-Bereitstellung von Inhalten verstehen,
* damit vertraut sein, wie AEM Headless und Übersetzung unterstützt.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM Headless-Übersetzungs-Tour fort, indem Sie als Nächstes das Dokument [Erste Schritte mit der AEM Headless-Übersetzung](getting-started.md) lesen, in dem Sie einen Überblick darüber erhalten, wie AEM Headless-Inhalte verwaltet und die Übersetzungs-Tools kennenlernen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, mit dem nächsten Teil der Headless-Übersetzungs-Tour fortzufahren, indem Sie das Dokument [Erste Schritte mit der AEM Headless-Übersetzung](getting-started.md) lesen. Im Folgenden finden Sie jedoch einige zusätzliche, optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen, die aber nicht erforderlich sind, um mit der Headless-Tour fortzufahren.

* [MSM und Übersetzung](/help/sites-administering/msm-and-translation.md) – Die Details des Multi-Site-Managers von AEM und wie er mit seinen Übersetzungs-Tools zusammenarbeitet.
