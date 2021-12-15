---
title: Erfahren Sie mehr über Headless Content und wie Sie ihn in AEM übersetzen können.
description: Lernen Sie Headless-Konzepte kennen, wie sie AEM zugeordnet sind und die Theorie AEM Übersetzung.
index: true
hide: false
hidefromtoc: false
source-git-commit: 7cf68868e0963930bde9fcda647822a03914b61d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 32%

---

# Erfahren Sie mehr über Headless Content und wie Sie ihn in AEM übersetzen können. {#learn-about}

Lernen Sie Headless-Konzepte kennen, wie sie AEM zugeordnet sind und die Theorie AEM Übersetzung.

## Ziel {#objective}

Dieses Dokument hilft Ihnen, die Headless-Content-Bereitstellung zu verstehen, wie AEM Headless-Unterstützung und wie solche Inhalte übersetzt werden können. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den grundlegenden Konzepten der Headless Content-Bereitstellung vertraut.
* Machen Sie sich damit vertraut, wie AEM Headless- und Übersetzungsfunktionen unterstützen.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

In einem Full-Stack-CMS befindet sich die gesamte Funktionalität zum Bearbeiten von Inhalten im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stapel eingefügt werden und es gibt nur einen Ort, an dem Änderungen vorgenommen werden können.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stapels wird jedoch schnell sichtbar, da andere Elemente im Stapel angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Dienste, seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, progressive Web-Apps (PWA) usw., nehmen Inhalte aus dem Headless-CMS auf und bieten ihr eigenes Rendering. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Übersetzen von Headless Content in AEM {#translating-in-aem}

Zusätzlich zu den robusten Tools zum Erstellen, Verwalten und Bereitstellen herkömmlicher Webseiten im Vollstapelmodus bietet AEM auch die Möglichkeit, eigenständige Inhaltsauswahlen zu erstellen und diese Headless-Legs bereitzustellen.

Die Leistungsfähigkeit von AEM ermöglicht es, Inhalte entweder Headless, Full Stack oder in beiden Modellen gleichzeitig bereitzustellen. Für den Übersetzer-Spezialisten können die gleichen Übersetzungstools auf beide Inhaltstypen angewendet werden, sodass Sie einen einheitlichen Ansatz für die Übersetzung Ihrer Inhalte erhalten.

Auf der Journey erfahren Sie mehr darüber, wie AEM Inhalte übersetzt, aber auf hoher Ebene ist das Konzept einfach:

1. Definieren Sie eine Verbindung zu einem Übersetzungsdienst, indem Sie das Framework für die Übersetzungsintegration konfigurieren.
1. Definieren Sie mithilfe von Übersetzungsregeln, welche Inhalte übersetzt werden sollen.
1. Erstellen Sie ein Übersetzungsprojekt, um den Inhalt zu sammeln, an den Übersetzungsdienst zu senden und die Ergebnisse zu erhalten.
1. Überprüfen und veröffentlichen Sie den übersetzten Inhalt.

## Wie geht es weiter {#what-is-next}

Vielen Dank für den Einstieg in Ihre AEM Headless Translation Journey! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Machen Sie sich mit den grundlegenden Konzepten der Headless Content-Bereitstellung vertraut.
* Machen Sie sich damit vertraut, wie AEM Headless- und Übersetzungsfunktionen unterstützen.

Auf diesen Erkenntnissen aufbauen und Ihre Journey-zur Headless-AEM-Übersetzung fortsetzen, indem Sie das Dokument erneut überprüfen. [Erste Schritte mit AEM Headless-Übersetzung](getting-started.md) Hier erhalten Sie einen Überblick darüber, wie AEM Headless Content verwaltet und die Übersetzungs-Tools kennenlernen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, zum nächsten Teil der Headless-Übersetzungs-Journey zu wechseln, indem Sie das Dokument lesen [Erste Schritte mit AEM Headless-Übersetzung](getting-started.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einen tieferen Einblick in einige der in diesem Dokument erwähnten Konzepte ermöglichen, aber nicht auf der Headless-Journey weiterarbeiten müssen.

* [MSM und Übersetzung](/help/sites-administering/msm-and-translation.md) - Die Details AEM Multi-Site-Managers und wie er mit seinen Übersetzungs-Tools funktioniert
