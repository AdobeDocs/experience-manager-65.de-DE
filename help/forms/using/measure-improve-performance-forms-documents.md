---
title: Messen und Verbessern der Effektivität und Konvertierung von Formularen
seo-title: Measure and improve effectiveness and conversion of forms
description: AEM Forms ist mit Adobe Target- und Adobe Analytics-Lösungen integriert, mit denen Sie die Leistung und Konvertierungsrate Ihrer Formulare messen und verbessern können.
seo-description: AEM Forms integrates with Adobe Target and Adobe Analytics solutions that lets you measure and improve the performance and conversion rate of your forms.
uuid: fd2f087c-39f5-457d-8b44-c3ec4400b3fc
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: a128877d-239c-4272-99c2-72d6486d5703
docset: aem65
exl-id: 4f45ad22-611b-4b4f-8e89-cb64a122b70a
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1275'
ht-degree: 34%

---

# Messen und Verbessern der Effektivität und Konvertierung von Formularen{#measure-and-improve-effectiveness-and-conversion-of-forms}

## Die Herausforderung {#the-challenge-br}

Unternehmen geben ihren Kunden zunehmend die Möglichkeit, ihre Transaktionen mithilfe digitaler Self Services über mehrere Kanäle auszuführen. Da jedoch kein 1:1-Feedback-Mechanismus zur Verfügung steht, wird es schwierig, den Erfolg zu messen und mit digitalen Formularen zu experimentieren, um das Kundenerlebnis zu verbessern und Konversionen zu steigern.

Um den ROI zu maximieren, müssen Unternehmen überwachen, wie ihre Kunden mit Diensten interagieren, und mit ihren digitalen Artefakten (Formularen) experimentieren, um die Kundenerlebnisse zu verbessern. Um den Erfolg zu messen und eine Strategie für Verbesserungen zu definieren, müssen Unternehmen Antworten auf Fragen wie folgende finden:

* Wie viele Kunden haben versucht, auf meine Formulare zuzugreifen oder mit ihnen zu handeln?
* Wie viele davon haben die Transaktion erfolgreich abgeschlossen?
* Wie viele von ihnen haben das Formular verlassen?
* Welche Problembereiche bestehen für Kunden?
* Welche Änderungen bringe ich ein und wie teste ich, was zu einer besseren Konversion führt?

## Die Lösung {#the-solution}

AEM Forms ermöglicht die Integration in [Adobe Marketing Cloud](https://www.adobe.com/marketing-cloud.html)-Lösungen – [Adobe Analytics](https://www.adobe.com/marketing-cloud/web-analytics.html) und [Adobe Target](https://www.adobe.com/marketing-cloud/testing-targeting.html) – die Ihnen helfen, die Leistung Ihrer Formulare zu überwachen und zu analysieren und ein Vorgehen zu ermitteln, das zu einer besseren Konversionsrate führt.

## Der Workflow {#the-workflow}

Kommen wir zu den Details, wie Sie die Leistung messen und Konversionsraten für Formulare verbessern können.

### Zielgruppe {#target-audience}

* Geschäftsbenutzer und -analysten, die für Marketingstrategien und Erfolg verantwortlich sind
* IT-Mitarbeiter, die sich um die Einrichtung und Wartung von Infrastruktur und Lösungen kümmern

### Beteiligte AEM Forms-Komponenten und -Funktionen {#aem-forms-components-and-features-involved}

* Adaptive Formulare
* Integration in Adobe Analytics zum Erfassen, Organisieren und Berichten von Kundeninteraktionen mit Ihren adaptiven Formularen
* Integration mit Adobe Target zum Ausführen von A/B-Tests für adaptive Formulare

### Annahmen {#assumptions}

* Sie haben bereits ein Adobe Marketing Cloud-Konto und sich für Analytics- und Target-Lösungen registriert.
* Sie verfügen über ein veröffentlichtes adaptives Formular, auf das Kunden zugreifen können.

### Arbeitsablaufschritte {#workflow-steps}

#### Schritt 1: Konfigurieren von Analytics und Target in AEM Forms  {#step-configure-analytics-and-target-in-aem-forms-br}

**Konfigurieren Sie Analytics**

Um tiefe Einblicke in die Interaktionen Ihrer Kunden mit Ihren Formularen zu erhalten, müssen Sie zunächst Analytics in AEM Forms konfigurieren. Führen Sie die folgenden Schritte durch:

1. Erstellen einer Report Suite in Adobe Analytics
1. Cloud Service-Konfiguration in AEM erstellen
1. Cloud Service-Framework in AEM erstellen
1. AEM Forms-Analytics-Konfigurationsdienst konfigurieren
1. Analytics im Formular in AEM aktivieren

Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analysen und Berichten für adaptive Formulare](../../forms/using/configure-analytics-forms-documents.md).

**Target konfigurieren**

Um A/B-Tests für Ihre adaptiven Formulare zu erstellen und durchzuführen, konfigurieren Sie Target in AEM Forms, wie unter [Einrichten und Integrieren von Target in AEM Forms](../../forms/using/ab-testing-adaptive-forms.md#p-set-up-and-integrate-target-in-aem-forms-p) beschrieben. 

#### Schritt 2: Anzeigen des Analyseberichts {#step-view-analytics-report-br}

Wenn Ihre Kunden auf Formulare zugreifen und mit ihnen interagieren, für die Sie Analytics aktiviert haben, werden ihre Interaktionen in hochgesicherten Analytics-Datenbanken erfasst. Die Datenbanken werden von Clients segmentiert und sind über sichere Verbindungen zugänglich.

Sie können einen Bericht aus AEM für Formulare mit aktivierter Analyse-Funktion anzeigen und Daten analysieren. Anzeigen des Berichts:

1. Navigieren Sie auf AEM Server zu **Forms > Forms und Dokumente**.
1. Wählen Sie das Formular aus, für das Sie den Analysebericht erstellen möchten.
1. Klicken Sie auf das Symbol Analytics-Berichte . Der Bericht wird angezeigt.

Sehen wir uns die Datenpunkte an, die von Analytics für Formulare erfasst und berichtet werden.

**Forms-Analysebericht**

Der Analysebericht für adaptive Formulare erfasst die folgenden wichtigen Leistungsindikatoren (KPIs) auf Formularebene:

* **Durchschnittliche Füllzeit**: Durchschnittliche Zeit für das Ausfüllen des Formulars
* **Impressionen**: Gibt an, wie oft das Formular in den Suchergebnissen angezeigt wurde

* **Ausgabeformate**: Gibt an, wie oft das Formular wiedergegeben oder geöffnet wurde
* **Entwürfe**: Gibt an, wie oft das Formular als Entwurf gespeichert wurde

* **Einsendungen**: Gibt an, wie oft das Formular gesendet wurde
* **Abbruch**: Gibt an, wie oft Benutzer das Formular verlassen haben, ohne es auszufüllen
* **Besuche/Übermittlungen**: Verhältnis der Besuche pro Übermittlung

Darüber hinaus erhalten Sie die folgenden Details zu jedem Bedienfeld im Formular:

* **Uhrzeit**: Durchschnittliche Zeit (Sekunden), die im Bereich und den zugehörigen Feldern verbracht wurde

* **Fehler**: Anzahl der Fehler im Bereich und dessen Feldern pro 1000 Formularwiedergaben

* **Hilfe**: Gibt an, wie oft Benutzer auf die kontextbezogene Hilfe für den Bereich und dessen Felder pro 1000 Formularwiedergaben zugegriffen haben

![Ein Beispielanalysebericht für ein adaptives Formular](assets/summary-report.png)

Weitere Informationen zu Formularanalyseberichten finden Sie unter [Anzeigen und Verstehen der Analyseberichte in AEM Forms](../../forms/using/view-understand-aem-forms-analytics-reports.md).

>[!NOTE]
>
>Über Ihr Analytics-Konto auf Adobe Marketing Cloud können Sie ausführliche Berichte anzeigen und tiefere Einblicke über Ihre Kunden und ihre Interaktionen mit Ihren Formularen erhalten.

#### Schritt 3: Analysieren der Datenpunkte {#step-analyze-data-points}

In diesem Schritt analysieren Sie Datenpunkte im Analysebericht und erkennen die Leistung des Formulars. Wenn es Ihre Erfolgs-KPIs nicht erfüllt, erstellen Sie Hypothesen basierend auf Daten und finden mögliche Lösungen, um die Probleme zu beheben. Beispiel:

* Wenn die durchschnittliche Füllzeit für das Formular höher als erwartet ist, könnte Ihr Formular für die Kunden zu schwer verständlich sein, keine Standardterminologie enthalten, zu lang sein und so weiter. In diesem Fall sollten Sie die Formularstruktur und -felder vereinfachen, den Formularentwurf überarbeiten, die Länge des Formulars verkürzen oder Hilfebeschreibungen und Beispiele für nicht standardmäßige Formularfelder hinzufügen.
* Wenn Daten darauf hindeuten, dass die meisten Kunden auf die Hilfe für ein Formularbedienfeld zugreifen, ist es offensichtlich, dass Kunden verwirrt sind, welche Informationen ausgefüllt werden sollen. Möglicherweise möchten Sie eine alternative Terminologie verwenden oder Beispieleingaben und Hilfebeschreibung für dieses Bedienfeld hinzufügen.
* Wenn die Abbruch- oder Abbruchrate für ein Formular höher ist als erwartet, kann dies daran liegen, dass die Wiedergabe des Formulars lange dauert, Kunden versehentlich das Formular ankommen oder es zu kompliziert ist. In diesem Fall sollten Sie die in den Suchergebnissen angezeigte Formularbeschreibung optimieren, das Formular vereinfachen, das Formular für schnelleres Laden optimieren usw.

Nachdem Sie diese Datenpunkte analysiert und zu einer Hypothese gelangt sind, nehmen Sie die erforderlichen Änderungen im Formular vor.

#### Schritt 4: Analyse validieren und Fehlerbehebungen {#step-validate-your-analysis-and-fixes}

In diesem Schritt validieren Sie die Änderungen, die Sie im Formular vorgenommen haben, und überprüfen, ob sich dies auf die Konversionsrate auswirkt.

**Durchführen eines A/B-Tests**

Die Integration von AEM Forms mit Target ermöglicht die Erstellung von A/B-Tests für adaptive Formulare. In A/B-Tests können Sie Ihren Kunden nach dem Zufallsprinzip verschiedene Erlebnisse eines Formulars in Echtzeit präsentieren, um zu erfahren, welches Erlebnis besser funktioniert oder mehr Konversionen verursacht. Sobald Ihnen wichtige Daten vorliegen, die darauf hinweisen, dass ein Erlebnis bessere Konversionen liefert als das andere, können Sie dieses Erlebnis als Gewinner erklären und in Zukunft wird es zum Standarderlebnis, das für alle Kunden sichtbar ist.

Weitere Informationen zum Erstellen eines A/B-Tests für ein adaptives Formular finden Sie unter [A/B-Tests für adaptive Formulare](../../forms/using/ab-testing-adaptive-forms.md).

![Ein Beispielzusammenfassungsbericht von A/B-Tests für ein adaptives Formular](assets/ab-test-report-4.png)

## Best Practices {#best-practices}

Die echten Best Practices sind diejenigen, die Sie sich bei der Durchführung dieses Workflows identifizieren. Sie sind für Ihre Umgebung und Ihre Anforderungen einzigartig. Erfassen Sie Ihre Lernergebnisse im Laufe des Workflows und dokumentieren Sie sie als Best Practices.

Einige Empfehlungen zum Entwerfen von Formularen und zum Durchführen von A/B-Tests:

**Forms-Design**

* Gestalten Sie das Formular einfach, kurz und mit benutzerfreundlicher Navigation. Verwenden Sie Richtungshinweise zur Navigation.
* Verwenden Sie Standard- oder allgemeine Terminologie für Formularfelder.
* Erklären Sie das Feld und die erforderliche Eingabe mit Beispielen oder Hilfe in Fällen, in denen der Benutzer durcheinanderkommen könnte.
* Validieren Sie Benutzereingaben bei der Eingabe, wann immer möglich, um Fehler bei der Formularübermittlung zu vermeiden.
* Optimieren Sie Layouts für Desktop- und Mobilgeräte.
* Informationen für bekannte Benutzer automatisch ausfüllen.

**A/B-Tests**

* Erstellen Sie eine Hypothese und identifizieren Sie Erfolgsmetriken, bevor Sie den A/B-Test durchführen.
* Führen Sie geringfügige Abweichungen (idealerweise eine nach der anderen) in Ihrem alternativen Erlebnis aus, um zu erfahren, welche Auswirkungen die Konversionsrate hatte.
* Testen Sie regelmäßig, um Ineffizienzen zu vermeiden.
