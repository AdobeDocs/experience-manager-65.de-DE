---
title: Planung
seo-title: Planning
description: Was Sie wissen müssen, um für Ihren Test zu planen
seo-description: What you need to know to plan for your test
uuid: 29b1127a-da85-46ed-98e7-1c983eb40cfe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 12268c43-93f9-42c1-8dd7-f17f9ae2219b
exl-id: ed662279-0679-4ba3-b744-6649fb8dda17
source-git-commit: ed11891c27910154df1bfec6225aecd8a9245bff
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 100%

---

# Planung{#planning}

In diesem Dokument wird beschrieben, was Sie wissen müssen, um für Ihren Test zu planen. Außerdem sollten Sie die folgenden Fragen beantworten, bevor Sie Ihre Tests durchführen:

* [Welche Testumgebungen sind erforderlich?](/help/sites-developing/test-environments.md)
* [Definieren von Testfällen](/help/sites-developing/test-cases.md)
* [Testen – wann und mit wem?](/help/sites-developing/when-who.md)

## Bevor Sie beginnen {#before-you-start}

Bevor Sie mit der eigentlichen Analyse und Definition der Tests beginnen, lesen Sie die folgenden Informationen durch:

**AEM-Architektur**: Lesen Sie „Grundlegende Konzepte“, um sich mit der Architektur und den Grundprinzipien von AEM vertraut zu machen.

**Dokumentation**: In der Dokumentation und den Anleitungsartikeln erhalten Sie weitere Informationen.

**Grundlegende Prinzipien des Testens**: Sie sollten die Grundlagen von Softwaretests und Qualitätssicherung kennen. Vorzugsweise sollten Sie bereits Erfahrung mit Projekttests haben.

Es gibt viele Websites, Bücher und Kurse, die solche Prinzipien behandeln. Deshalb werden wir sie in diesem Dokument nicht besprechen.

**Zu vermeidende Annahmen**: Die größte gängige Annahme ist die, dass Ihre Website täglich Millionen von Anfragen bedienen muss. Unter bestimmten Umständen kann dies zutreffen, Sie sollten es jedoch nicht grundsätzlich voraussetzen.

Zukünftige Werte können zwar nicht 100 % genau vorausgesagt werden, aber Sie erhalten einen guten Anhaltspunkt, indem Sie Ihre aktuelle Website und den Besucher-Traffic beobachten. Sie können dann anhand des Faktors, um den der Besucher-Traffic erwartungsgemäß/hoffentlich wachsen wird, Schätzungen aufstellen.

**Verpflichtung zur Qualität**: Es ist äußerst wichtig, dass jeder, der am Test teilnimmt, neutral bleibt und nur die Ergebnisse der durchgeführten Tests berichtet.

Es liegt in der Verantwortung des Projekt-Managers, abhängig von den Ergebnissen Handlungen zu bestimmen und zu veranlassen.

**Sich einbringen**: Obwohl es in der Verantwortung des Projekt-Managers liegt, sicherzustellen, dass alle Betroffenen an allen Meetings beteiligt sind (Status, Workshops usw.), sollten auch Sie versuchen, sich so früh wie möglich in den Projektzyklus einzubinden. Dazu gehören Informationssammlung und Anforderungsanalyse.

**Den Kunden einbinden**: In ähnlicher Weise sollten Sie auch versuchen, beim Definieren Ihrer Testfälle und des Testplans nach Möglichkeit den Kunden einzubeziehen.

## Testarten {#types-of-tests}

Es gibt verschiedene Standardklassifikationen von Tests, die sich zum Testen von AEM-Projekten eignen. Sie sollten mit ihnen vertraut sein, um zu entscheiden, welche Sie verwenden möchten:

>[!NOTE]
>
>Sie werden in ihrer chronologischen Durchführungsreihenfolge aufgeführt.

**Komponententests**: Tests werden (in der Regel) vom Entwicklungs-Team durchgeführt, um sicherzustellen, dass sich die einzelnen Elemente korrekt verhalten (wenn auch isoliert).

**Integrationstests**: Testet Module in Kombination. Diese Tests werden nach Komponententests, aber vor Systemtests durchgeführt.

**Smoke-Tests**: Hierbei handelt es sich um Schnelltests, um zu überprüfen, ob die Software ausgeführt wird und allgemeine Funktionen verfügbar sind. Es werden keine Detailtests durchgeführt.

**Funktionstests**: Diese Tests werden verwendet, um die Funktionalität der Software zu testen. Eine Testreihe wird konzipiert, die alle Funktionsdetails mit vorgesehenen, nicht vorgesehenen und/oder fehlerhaften Eingaben abdeckt.

Black-Box-Tests sind Funktionsprüfungen einer vollständigen Einheit/Komponente/eines Moduls und werden ohne Kenntnis der internen Funktionsweise des betreffenden Elements durchgeführt.

**Systemtests**: Hierbei wird das gesamte System getestet, nachdem es vollständig auf einer geeigneten Plattform integriert und installiert wurde.

Sie testen die Funktionalität nach dem Black-Box-Prinzip.

**Leistungstests**: Leistungstests sind beim Testen von AEM äußerst wichtig.

Sie zeigen die Leistung unter verschiedenen Bedingungen auf:

* Normal

   Bedingungen, die in etwa 90 % aller Fälle gegeben sind. Beispielsweise verwendet nur ein Teil der Autoren das System.

* Spitze

   Bedingungen, die während relativ kurzer Zeitspannen aufgrund besonderer Umstände auftreten – zum Beispiel, wenn alle Autoren gleichzeitig das System verwenden oder wenn neue Inhalte veröffentlicht werden und eine größere Anzahl von Besuchern Ihre Website nutzt.

* Extrem

   Kann verwendet werden, um die prognostizierte Leistung zu simulieren, wenn neue, besonders interessante Inhalte auf Ihrer Website veröffentlicht werden. In diesem Fall kann eine extreme Spitze auftreten; dies ist jedoch nicht immer vorhersehbar.

   Solche Situationen können auftreten, wenn Karten für bestimmte Ereignisse in den Verkauf gehen oder eine heiß erwartete Website zum ersten Mal live geschaltet wird.

Die Ergebnisse werden dann verwendet, um die Anwendung zu optimieren.

**Belastungstest**: Belastungstests werden durchgeführt, um zu prüfen, wie sich eine Komponente oder Anwendung unter Extrembedingungen verhält. Insbesondere werden diese Tests verwendet, um zu zeigen, wie sich das Verhalten verschlechtert, wenn das Element fehlschlägt.

**Regressionstests**: Regressionstests werden verwendet, um zu bestätigen, ob Funktionen, die bereits in einer vorherigen Version der Software getestet wurden, weiterhin ordnungsgemäß funktionieren.

Regressionstests eignen sich gut für Automatisierung (sofern möglich), um sicherzustellen, dass sie schnell und konsistent wiederholt werden können.

**Akzeptanztests**: Akzeptanztests sind eine spezielle Kategorie, da sie verwendet werden, um die Akzeptanz des Projekts beim Kunden zu prüfen.

Die Akzeptanztests umfassen möglicherweise einige Tests aus den oben aufgeführten Kategorien. Sie werden ausgewählt, um sicherzustellen, dass das Projekt die Anforderungen des Kunden erfüllt

Weitere Informationen finden Sie unter [Akzeptanz und Abnahme](/help/sites-developing/acceptance-signoff.md).

## Erste Schritte {#getting-started}

Bevor Sie mit Ihren detaillierten Testfällen und Ihrem Testplan beginnen, können Sie Folgendes tun:

**Definieren der Ziele**: Definieren Sie Ihre allgemeinen Ziele, die im Laufe der Tests als Ausgangspunkt für die Feinabstimmung dienen. Sie sollten Folgendes tun:

* Testen Sie die Funktion anhand der detaillierten Anforderungsspezifikationen.
* Testen Sie die Leistung anhand der [Zielmetriken](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

Diese Liste ist nicht erschöpfend.

**Sammeln von Traffic-Statistiken von der bestehenden Website**: Diese Informationen können aus den Protokolldateien extrahiert werden. Weitere Informationen finden Sie unter „Leistungsüberwachung“.

Diese Zahlen geben einen Überblick über den aktuellen Traffic (Menge und Verteilung) auf der vorhandenen Website und können als Ausgangspunkt für die neue Website verwendet werden.

**Sammeln von Traffic-Statistiken von externen Websites**: Wenn möglich, können Sie zum Vergleich Traffic-Statistiken zu anderen Websites heranziehen. Diese Zahlen werden jedoch nicht immer veröffentlicht.

**Bestätigen von Zielmetriken**: Metriken werden zum Festlegen quantitativer Messwerte für die Qualität der Website verwendet, da sie Leistungsziele darstellen.

Sie sollten zu Beginn des Projekts gemeinsam mit dem Kunden definiert werden. Weitere Informationen finden Sie unter [Zielmetriken](/help/sites-developing/planning.md).
