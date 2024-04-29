---
title: Messen und Verbessern der Effektivität und Konvertierung von Formularen
description: AEM Forms lässt sich in Adobe Target und Adobe Analytics integrieren, sodass Sie die Leistung und Konversionsrate Ihrer Formulare messen und verbessern können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: 4f45ad22-611b-4b4f-8e89-cb64a122b70a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1274'
ht-degree: 100%

---

# Messen und Verbessern der Effektivität und Konvertierung von Formularen{#measure-and-improve-effectiveness-and-conversion-of-forms}

## Die Herausforderung {#the-challenge-br}

Unternehmen geben ihren Kunden zunehmend die Möglichkeit, ihre Transaktionen mithilfe digitaler Self Services über mehrere Kanäle auszuführen. In Ermangelung eines unmittelbaren Feedbacks stellt es jedoch eine Herausforderung dar, den Erfolg zu messen und mit digitalen Formularen zu experimentieren, um das Kundenerlebnis zu verbessern und Konversionen zu erhöhen.

Um den ROI zu maximieren, müssen Unternehmen überwachen, wie ihre Kundinnen und Kunden mit Diensten interagieren, und mit ihren digitalen Artefakten (Formularen) experimentieren, um die Kundenerlebnisse zu verbessern. Um den Erfolg zu messen und eine Strategie zur Verbesserung zu definieren, müssen Unternehmen Antworten auf Fragen finden wie:

* Wie viele Kundinnen und Kunden haben versucht, auf meine Formulare zuzugreifen oder damit Transaktionen durchzuführen?
* Wie viele davon haben die Transaktion erfolgreich abgeschlossen?
* Wie viele davon haben das Formular verlassen?
* Mit welchen Problemen werden die Kundinnen und Kunden konfrontiert?
* Welche Änderungen kann ich einführen und wie teste ich, was zu einer höheren Konversion führt?

## Die Lösung {#the-solution}

AEM Forms ermöglicht die Integration in [Adobe Marketing Cloud](https://www.adobe.com/marketing-cloud.html)-Lösungen – [Adobe Analytics](https://www.adobe.com/marketing-cloud/web-analytics.html) und [Adobe Target](https://www.adobe.com/marketing-cloud/testing-targeting.html) – die Ihnen helfen, die Leistung Ihrer Formulare zu überwachen und zu analysieren und ein Vorgehen zu ermitteln, das zu einer besseren Konversionsrate führt.

## Der Workflow {#the-workflow}

Kommen wir zur genauen Vorgehensweise, wie Sie die Leistung messen und Konversionsraten für Formulare erhöhen können.

### Zielgruppe {#target-audience}

* Business-Anwenderinnen und -Anwender sowie Analystinnen und Analysten, die für Marketing-Strategien und Erfolge verantwortlich sind
* IT-Teams, die für Einrichtung und Wartung der Infrastruktur und Lösungen verantwortlich sind

### Beteiligte AEM Forms-Komponenten und -Funktionen {#aem-forms-components-and-features-involved}

* Adaptive Formulare
* Integration in Adobe Analytics zum Erfassen, Organisieren und Berichten von Kundeninteraktionen mit Ihren adaptiven Formularen
* Integration in Adobe Target, um A/B-Tests für adaptive Formulare durchzuführen

### Annahmen {#assumptions}

* Sie haben bereits ein Adobe Marketing Cloud-Konto und sich für Analytics- und Target-Lösungen registriert.
* Sie verfügen über ein veröffentlichtes adaptives Formular, auf das die Kundinnen und Kunden zugreifen können.

### Arbeitsablaufschritte {#workflow-steps}

#### Schritt 1: Konfigurieren von Analytics und Target in AEM Forms  {#step-configure-analytics-and-target-in-aem-forms-br}

**Konfigurieren Sie Analytics**

Um umfassende Erkenntnisse zu den Interaktionen der Kundinnen und Kunden mit Ihren Formularen zu erhalten, müssen Sie zunächst Analytics in AEM Forms konfigurieren. Führen Sie die folgenden Schritte durch:

1. Erstellen einer Report Suite in Adobe Analytics
1. Cloud Service-Konfiguration in AEM erstellen
1. Cloud Service-Framework in AEM erstellen
1. AEM Forms-Analytics-Konfigurationsdienst konfigurieren
1. Analytics im Formular in AEM aktivieren

Ausführliche Anweisungen finden Sie unter [Konfigurieren von Analysen und Berichten für adaptive Formulare](../../forms/using/configure-analytics-forms-documents.md).

**Target konfigurieren**

Um A/B-Tests für Ihre adaptiven Formulare zu erstellen und durchzuführen, konfigurieren Sie Target in AEM Forms, wie unter [Einrichten und Integrieren von Target in AEM Forms](../../forms/using/ab-testing-adaptive-forms.md#p-set-up-and-integrate-target-in-aem-forms-p) beschrieben. 

#### Schritt 2: Anzeigen des Analyseberichts {#step-view-analytics-report-br}

Wenn Ihre Kundinnen und Kunden auf Formulare zugreifen und mit Formularen interagieren, für die Sie Analytics aktiviert haben, werden ihre Interaktionen in streng geschützten Analytics-Datenbanken erfasst. Die Datenbanken werden nach Clients segmentiert, und der Zugriff erfolgt über sichere Verbindungen.

Sie können einen Bericht aus AEM für Formulare mit aktivierter Analyse-Funktion anzeigen und Daten analysieren. So zeigen Sie den Bericht an:

1. Navigieren Sie auf dem AEM-Server zu **Formulare > Formulare und Dokumente**.
1. Wählen Sie das Formular aus, für das der Analysebericht erstellt werden soll.
1. Klicken Sie auf das Symbol für den Analysebericht. Der Bericht wird angezeigt.

Werfen wir einen Blick auf die Datenpunkte, die von Analytics für Formulare erfasst und gemeldet werden.

**Formularanalysebericht**

Der Analysebericht für adaptive Formulare erfasst die folgenden wichtigen Leistungsindikatoren (Key Performance Indicators, KPIs) auf Formularebene:

* **Durchschnittliche Füllzeit**: Gibt die durchschnittliche Zeit für das Ausfüllen des Formulars an.
* **Impressionen**: Gibt an, wie oft das Formular in den Suchergebnissen angezeigt wurde

* **Ausgabeformate**: Gibt an, wie oft das Formular wiedergegeben oder geöffnet wurde
* **Entwürfe**: Gibt an, wie oft das Formular als Entwurf gespeichert wurde.

* **Übermittlungen**: Gibt an, wie oft das Formular übermittelt wurde.
* **Abbrechen**: Gibt an, wie oft Benutzende das Formular verlassen haben, ohne es auszufüllen.
* **Besuche/Übermittlungen**: Gibt das Verhältnis der Besuche pro Übermittlung an.

Darüber hinaus erhalten Sie die folgenden Details zu jedem Panel in folgender Form:

* **Uhrzeit**: Durchschnittliche Zeit (Sekunden), die im Bereich und den zugehörigen Feldern verbracht wurde

* **Fehler**: Anzahl der Fehler im Bereich und dessen Feldern pro 1000 Formularwiedergaben

* **Hilfe**: Gibt an, wie oft Benutzer auf die kontextbezogene Hilfe für den Bereich und dessen Felder pro 1000 Formularwiedergaben zugegriffen haben

![Ein Beispielanalysebericht für ein adaptives Formular](assets/summary-report.png)

Weitere Informationen zu Formularanalyseberichten finden Sie unter [Anzeigen und Verstehen der Analyseberichte in AEM Forms](../../forms/using/view-understand-aem-forms-analytics-reports.md).

>[!NOTE]
>
>Über Ihr Analytics-Konto auf Adobe Marketing Cloud können Sie ausführliche Berichte anzeigen und tiefere Einblicke über Ihre Kunden und ihre Interaktionen mit Ihren Formularen erhalten.

#### Schritt 3: Analysieren der Datenpunkte {#step-analyze-data-points}

In diesem Schritt analysieren Sie Datenpunkte im Analysebericht und schließen auf die Leistung des Formulars. Wenn es Ihre Erfolgs-KPIs nicht erfüllt, erstellen Sie auf Daten basierende Hypothesen und finden mögliche Lösungen, um die Probleme zu beheben. Beispiel:

* Wenn die durchschnittliche Ausfüllzeit für das Formular länger als erwartet ist, ist es möglich, dass Ihr Formular für die Kundinnen und Kunden kompliziert zu verstehen ist, keine Standardterminologie verwendet, zu lang ist usw. In diesem Fall sollten Sie die Formularstruktur und -felder vereinfachen, das Formular-Design überarbeiten, das Formular kürzen oder Hilfebeschreibungen und Beispiele für nicht standardmäßige Formularfelder hinzufügen.
* Wenn die Daten zeigen, dass die meisten Kundinnen und Kunden auf die Hilfe für ein bestimmtes Formular-Panel zugreifen, ist es offensichtlich, dass ihnen nicht klar ist, welche Informationen sie eingeben sollen. Sie sollten dann eine alternative Terminologie verwenden oder einige Beispieleingaben und Hilfebeschreibung für dieses Panel hinzufügen.
* Wenn die Abbruchrate für ein Formular höher als erwartet ist, kann es daran liegen, dass die Wiedergabe des Formulars zu lange dauert, Kundinnen und Kunden es versehentlich aufrufen oder es zu schwierig ist. In diesem Fall sollten Sie die Formularbeschreibung optimieren, die in den Suchergebnissen angezeigt wird, das Formular vereinfachen, es für eine schnellere Ladezeit optimieren usw.

Nachdem Sie diese Datenpunkte analysiert und eine Hypothese entwickelt haben, nehmen Sie die erforderlichen Änderungen im Formular vor.

#### Schritt 4: Validieren Ihrer Analyse und Korrekturen {#step-validate-your-analysis-and-fixes}

In diesem Schritt validieren Sie die Änderungen, die Sie im Formular vorgenommen haben, und überprüfen, ob sie Auswirkungen auf die Konversionsrate haben.

**Durchführen eines A/B-Tests**

Die Integration von AEM Forms in Target ermöglicht das Erstellen von A/B-Tests für adaptive Formulare. In A/B-Tests präsentieren Sie Ihren Kundinnen und Kunden nach dem Zufallsprinzip verschiedene Versionen eines Formulars in Echtzeit, um zu erfahren, was besser funktioniert oder zu mehr Konversionen führt. Sobald Ihnen aussagekräftige Daten vorliegen, dass eine bestimmte Version mit einer höheren Konversionsrate verbunden ist als eine andere, ist diese Version der „Gewinner“ und Sie können sie als Standarderlebnis für alle Kundinnen und Kunden festlegen.

Weitere Informationen zum Erstellen eines A/B-Tests für ein adaptives Formular finden Sie unter [A/B-Tests für adaptive Formulare](../../forms/using/ab-testing-adaptive-forms.md).

![Ein Beispielzusammenfassungsbericht von A/B-Tests für ein adaptives Formular](assets/ab-test-report-4.png)

## Best Practices {#best-practices}

Wirklich gut sind die Best Practices, mit denen Sie sich bei der Ausführung dieses Workflows selbst identifizieren. Sie beziehen sich speziell auf Ihre Umgebung und Anforderungen. Erfassen Sie Ihre Lernfortschritte im Laufe des Workflows und dokumentieren Sie sie als Best Practices.

Nachfolgend finden Sie einige Empfehlungen zum Entwerfen von Formularen und zum Durchführen von A/B-Tests:

**Formular-Design**

* Gestalten Sie das Formular einfach, kurz und mit benutzerfreundlicher Navigation. Verwenden Sie Richtungshinweise zur Navigation.
* Verwenden Sie Standard- oder allgemeine Terminologie für Formularfelder.
* Erklären Sie das Feld und die erforderliche Eingabe mit Beispielen oder Hilfe in Fällen, in denen der Benutzer durcheinanderkommen könnte.
* Validieren Sie Benutzereingaben nach Möglichkeit gleich während des Tippens, um Fehler bei der Formularübermittlung zu vermeiden.
* Optimieren Sie Layouts für Desktop-Computer und Mobilgeräte.
* Lassen Sie Informationen für schon bekannte Benutzerinnen und Benutzer automatisch ausfüllen.

**A/B-Tests**

* Erstellen Sie vor dem Durchführen des A/B-Tests eine Hypothese und identifizieren Sie Erfolgsmetriken.
* Führen Sie geringfügige Abweichungen (idealerweise nur eine zu einem gegebenen Zeitpunkt) in die alternative Version ein, um zu ermitteln, wodurch die Konvertierungsrate beeinflusst wurde.
* Testen Sie regelmäßig, um Ineffizienz zu vermeiden.
