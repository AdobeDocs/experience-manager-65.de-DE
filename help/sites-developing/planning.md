---
title: Planung
description: Erfahren Sie, was Sie für die Planung Ihrer Adobe Experience Manager-Tests wissen müssen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: ed662279-0679-4ba3-b744-6649fb8dda17
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 49%

---

# Planung{#planning}

In diesem Dokument wird beschrieben, was Sie für die Planung Ihres Tests wissen müssen. Darüber hinaus sollten Sie diese Fragen beantworten, bevor Sie Ihre Tests durchführen:

* [Welche Testumgebungen sind erforderlich?](/help/sites-developing/test-environments.md)
* [Definieren von Testfällen](/help/sites-developing/test-cases.md)
* [Testen – wann und mit wem?](/help/sites-developing/when-who.md)

## Bevor Sie beginnen {#before-you-start}

Bevor Sie mit der eigentlichen Analyse und Definition von Tests beginnen, lesen Sie die folgenden Informationen durch:

**AEM-Architektur**: Lesen Sie „Grundlegende Konzepte“, um sich mit der Architektur und den Grundprinzipien von AEM vertraut zu machen.

**Dokumentation**: In der Dokumentation und den Anleitungsartikeln erhalten Sie weitere Informationen.

**Grundlegende Prinzipien des Testens**: Sie sollten die Grundlagen von Softwaretests und Qualitätssicherung kennen. Vorzugsweise sollten Sie Erfahrung mit dem Testen von Projekten haben.

Es gibt viele Websites, Bücher und Kurse, die sich mit solchen Grundsätzen befassen, und deshalb werden sie in diesem Dokument nicht ausführlich behandelt.

**Zu vermeidende Annahmen** - Die größte Annahme ist, dass Ihre Website täglich Millionen von Anfragen bearbeiten muss. Unter bestimmten Umständen mag dies wahr sein, kann aber nicht angenommen werden.

Zukünftige Werte können zwar nicht 100 % genau vorausgesagt werden, aber Sie erhalten einen guten Anhaltspunkt, indem Sie Ihre aktuelle Website und den Besucher-Traffic beobachten. Sie können dann Schätzungen abhängig von dem Faktor machen, mit dem Sie erwarten / hoffen, dass der Traffic zunehmen wird.

**Verpflichtung zur Qualität**: Es ist äußerst wichtig, dass jeder, der am Test teilnimmt, neutral bleibt und nur die Ergebnisse der durchgeführten Tests berichtet.

Es liegt in der Verantwortung des Projekt-Managers, abhängig von den Ergebnissen Handlungen zu bestimmen und zu veranlassen.

**Werden Sie involviert** - Obwohl es in der Verantwortung des Projektmanagers liegt, sicherzustellen, dass alle Parteien umfassend an allen Sitzungen (Status, Workshops usw.) beteiligt sind, sollten Sie auch versuchen, so früh wie möglich am Projektzyklus beteiligt zu werden, einschließlich der Prozesse zur Informationserfassung und Anforderungsanalyse.

**Den Kunden einbinden**: In ähnlicher Weise sollten Sie auch versuchen, beim Definieren Ihrer Testfälle und des Testplans nach Möglichkeit den Kunden einzubeziehen.

## Testtypen {#types-of-tests}

Es gibt verschiedene Standardklassifizierungen von Tests, die zum Testen eines AEM-Projekts geeignet sind. Sie sollten mit diesen vertraut sein, um zu entscheiden, welche Sie verwenden:

>[!NOTE]
>
>Diese werden in ihrer chronologischen Reihenfolge ihrer Anwendung aufgelistet.

**Komponententests**: Tests werden (in der Regel) vom Entwicklungs-Team durchgeführt, um sicherzustellen, dass sich die einzelnen Elemente korrekt verhalten (wenn auch isoliert).

**Integrationstests**: Testet Module in Kombination. Diese Tests werden nach Komponententests, aber vor Systemtests durchgeführt.

**Smoke-Tests**: Hierbei handelt es sich um Schnelltests, um zu überprüfen, ob die Software ausgeführt wird und allgemeine Funktionen verfügbar sind. Es werden keine Detailtests durchgeführt.

**Funktionstests**: Diese Tests werden verwendet, um die Funktionalität der Software zu testen. Eine Reihe von Tests soll alle Funktionsdetails abdecken, mit erwarteten und unerwarteten bzw. fehlerhaften Eingaben.

Black-Box-Tests sind Funktionstests einer kompletten Einheit/Komponente/eines Moduls, die ohne Kenntnis der internen Funktionsweise des betreffenden Elements durchgeführt werden.

**Systemtests**: Hierbei wird das gesamte System getestet, nachdem es vollständig auf einer geeigneten Plattform integriert und installiert wurde.

Sie testen die Funktionalität nach dem Black-Box-Prinzip.

**Leistungstests**: Leistungstests sind beim Testen von AEM äußerst wichtig.

Sie dienen zur Veranschaulichung der Leistung unter verschiedenen Bedingungen:

* Normal

  Bedingungen, die die Site in etwa 90 % der Zeit erleben wird. Wenn beispielsweise nur ein Teil der Autoren das System verwendet.

* Spitze

  Bedingungen, die aufgrund besonderer Umstände für eine verhältnismäßig kurze Zeit gelten, z. B. wenn alle Autoren das System gleichzeitig verwenden oder wenn neue Inhalte veröffentlicht werden und eine größere Anzahl von Besuchern Ihre Site anzeigt.

* Extrem

  Kann verwendet werden, um die Leistungsvorhersage zu simulieren, wenn neue, extrem interessante Inhalte auf Ihrer Website veröffentlicht werden. Dann kann ein extremer Höhepunkt zu sehen sein - auch wenn dies möglicherweise nicht immer vollständig vorhersehbar ist.

  Diese Umstände treten manchmal auf, wenn Eintrittskarten für bestimmte Veranstaltungen zur Verfügung gestellt oder zum ersten Mal eine Website veröffentlicht wird, die viel erwartet wird.

Die Ergebnisse werden dann zur Abstimmung der Anwendung verwendet.

**Belastungstest**: Belastungstests werden durchgeführt, um zu prüfen, wie sich eine Komponente oder Anwendung unter Extrembedingungen verhält. Insbesondere werden diese Tests verwendet, um zu zeigen, wie sich das Verhalten verschlechtert, wenn das Element fehlschlägt.

**Regressionstests**: Regressionstests werden verwendet, um zu bestätigen, ob Funktionen, die bereits in einer vorherigen Version der Software getestet wurden, weiterhin ordnungsgemäß funktionieren.

Regressionstests eignen sich gut für Automatisierung (sofern möglich), um sicherzustellen, dass sie schnell und konsistent wiederholt werden können.

**Akzeptanztests**: Akzeptanztests sind eine spezielle Kategorie, da sie verwendet werden, um die Akzeptanz des Projekts beim Kunden zu prüfen.

Die Liste der Annahmeprüfungen kann eine Kombination von Tests aus den oben genannten Kategorien enthalten und wird ausgewählt, um zu überprüfen, ob das Projekt die Anforderungen des Kunden erfüllt

Siehe [Akzeptanz und Abnahme](/help/sites-developing/acceptance-signoff.md) für weitere Details.

## Erste Schritte {#getting-started}

Bevor Sie mit Ihren detaillierten Testfällen und Testplänen beginnen, können Sie:

**Definieren der Ziele**: Definieren Sie Ihre allgemeinen Ziele, die im Laufe der Tests als Ausgangspunkt für die Feinabstimmung dienen. Sie haben folgende Möglichkeiten:

* Testen Sie die Funktionalität gemäß der detaillierten Anforderungsspezifikation.
* Testleistung gemäß [Zielmetriken](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

unter anderem.

**Sammeln von Traffic-Statistiken von der bestehenden Website**: Diese Informationen können aus den Protokolldateien extrahiert werden. Weitere Informationen finden Sie unter „Leistungsüberwachung“.

Diese Zahlen geben einen Überblick über den aktuellen Traffic (Menge und Verteilung) auf der vorhandenen Website und können als Ausgangspunkt für die neue Website verwendet werden.

**Sammeln von Traffic-Statistiken von externen Websites**: Wenn möglich, können Sie zum Vergleich Traffic-Statistiken zu anderen Websites heranziehen. Diese Zahlen werden jedoch nicht immer veröffentlicht.

**Bestätigen von Zielmetriken**: Metriken werden zum Festlegen quantitativer Messwerte für die Qualität der Website verwendet, da sie Leistungsziele darstellen.

Sie sollten zu Beginn des Projekts gemeinsam mit dem Kunden definiert werden. Siehe [Zielmetriken](/help/sites-developing/planning.md) für weitere Informationen.
