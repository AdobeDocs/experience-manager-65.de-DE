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
ht-degree: 59%

---

# Planung{#planning}

In diesem Dokument wird beschrieben, was Sie wissen müssen, um für Ihren Test zu planen. Außerdem sollten Sie die folgenden Fragen beantworten, bevor Sie Ihre Tests durchführen:

* [Welche Testumgebungen sind erforderlich?](/help/sites-developing/test-environments.md)
* [Definieren von Testfällen](/help/sites-developing/test-cases.md)
* [Testen – wann und mit wem?](/help/sites-developing/when-who.md)

## Bevor Sie beginnen {#before-you-start}

Bevor Sie mit der eigentlichen Analyse und Definition der Tests beginnen, lesen Sie die folgenden Informationen durch:

**AEM Architektur** - Siehe Grundkonzepte , um sich mit der Architektur und den Grundprinzipien der AEM vertraut zu machen.

**Dokumentation** - Weitere Informationen finden Sie in einem der Dokumentationsabschnitte oder in den Anleitungsartikeln .

**Grundprinzipien der Prüfung** - Sie sollten sich der Grundprinzipien der Softwaretests und Qualitätssicherung bewusst sein. Vorzugsweise sollten Sie bereits Erfahrung mit Projekttests haben.

Es gibt viele Websites, Bücher und Kurse, die solche Prinzipien behandeln. Deshalb werden wir sie in diesem Dokument nicht besprechen.

**Zu vermeidende Annahmen** - Die größte Annahme (regelmäßig gemacht) ist, dass Ihre Website täglich Millionen von Anfragen bearbeiten muss. Unter bestimmten Umständen kann dies zutreffen, Sie sollten es jedoch nicht grundsätzlich voraussetzen.

Zukünftige Werte können zwar nicht 100 % genau vorausgesagt werden, aber Sie erhalten einen guten Anhaltspunkt, indem Sie Ihre aktuelle Website und den Besucher-Traffic beobachten. Sie können dann anhand des Faktors, um den der Besucher-Traffic erwartungsgemäß/hoffentlich wachsen wird, Schätzungen aufstellen.

**Qualitätsverpflichtung** - Es ist von größter Bedeutung, dass jeder, der die Tests durchführt, neutral bleibt und lediglich die Ergebnisse der durchgeführten Tests meldet.

Es liegt in der Verantwortung des Projektmanagers, abhängig von den Ergebnissen Handlungen zu bestimmen und zu veranlassen.

**Werden Sie involviert** - Obwohl es in der Verantwortung des Projektmanagers liegt, sicherzustellen, dass alle Parteien umfassend an allen Sitzungen (Status, Workshops usw.) beteiligt sind, sollten Sie auch versuchen, so früh wie möglich am Projektzyklus beteiligt zu werden, einschließlich der Prozesse zur Informationserfassung und Anforderungsanalyse.

**Einbeziehung des Kunden** - Bei einem ähnlichen Thema versuchen Sie, den Kunden (wo möglich) bei der Definition Ihrer Testfälle und Ihres Plans einzubeziehen.

## Testarten {#types-of-tests}

Es gibt verschiedene Standardklassifikationen von Tests, die sich zum Testen von AEM-Projekten eignen. Sie sollten mit ihnen vertraut sein, um zu entscheiden, welche Sie verwenden möchten:

>[!NOTE]
>
>Sie werden in ihrer chronologischen Durchführungsreihenfolge aufgeführt.

**Einheiten-Tests** - Tests (in der Regel), die vom Entwicklungsteam durchgeführt werden, um sicherzustellen, dass sich die einzelnen Elemente korrekt verhalten - wenn auch isoliert.

**Integrationstests** - Testt Module bei Kombination. Diese Tests werden nach Unit-Tests, aber vor Systemtests durchgeführt.

**Rauchtests** - Hierbei handelt es sich um schnelle und schmutzige Tests, die belegen, dass die Software läuft und hochwertige Funktionen verfügbar sind. Es werden keine Detailtests durchgeführt.

**Funktionstests** - Diese werden verwendet, um die Funktionalität der Software zu testen. Eine Testreihe wird konzipiert, die alle Funktionsdetails mit vorgesehenen, nicht vorgesehenen und/oder fehlerhaften Eingaben abdeckt.

Black-Box-Tests sind Funktionsprüfungen einer vollständigen Einheit/Komponente/eines Moduls und werden ohne Kenntnis der internen Funktionsweise des betreffenden Elements durchgeführt.

**Systemtests** - Diese testen das gesamte System, sobald es vollständig integriert und auf einer geeigneten Plattform installiert ist.

Sie testen die Funktionalität nach dem Black-Box-Prinzip.

**Leistungstests** - Leistungstests sind bei AEM von entscheidender Bedeutung.

Sie zeigen die Leistung unter verschiedenen Bedingungen auf:

* Normal

   Bedingungen, die in etwa 90 % aller Fälle gegeben sind. Beispielsweise verwendet nur ein Teil der Autoren das System.

* Spitze

   Bedingungen, die während relativ kurzer Zeitspannen aufgrund besonderer Umstände auftreten – zum Beispiel, wenn alle Autoren gleichzeitig das System verwenden oder wenn neue Inhalte veröffentlicht werden und eine größere Anzahl von Besuchern Ihre Website nutzt.

* Extrem

   Kann verwendet werden, um die prognostizierte Leistung zu simulieren, wenn neue, besonders interessante Inhalte auf Ihrer Website veröffentlicht werden. In diesem Fall kann eine extreme Spitze auftreten; dies ist jedoch nicht immer vorhersehbar.

   Solche Situationen können auftreten, wenn Karten für bestimmte Ereignisse in den Verkauf gehen oder eine heiß erwartete Website zum ersten Mal live geschaltet wird.

Die Ergebnisse werden dann verwendet, um die Anwendung zu optimieren.

**Belastungstests** - Stresstests werden durchgeführt, um zu überprüfen, wie sich eine Komponente oder Anwendung unter extremen Bedingungen verhält. Insbesondere werden diese Tests verwendet, um zu zeigen, wie sich das Verhalten verschlechtert, wenn das Element fehlschlägt.

**Regressionstests** - Regressionstests werden verwendet, um zu überprüfen, ob die Funktionalität, die bereits in einer früheren Version der Software bewiesen wurde, weiterhin ordnungsgemäß funktioniert.

Regressionstests eignen sich gut für Automatisierung (sofern möglich), um sicherzustellen, dass sie schnell und konsistent wiederholt werden können.

**Akzeptanztests** - Akzeptanztests sind eine besondere Kategorie, da sie dazu dienen, die Akzeptanz des Projekts durch den Kunden anzuzeigen.

Die Akzeptanztests umfassen möglicherweise einige Tests aus den oben aufgeführten Kategorien. Sie werden ausgewählt, um sicherzustellen, dass das Projekt die Anforderungen des Kunden erfüllt

Weitere Informationen finden Sie unter [Akzeptanz und Abnahme](/help/sites-developing/acceptance-signoff.md).

## Erste Schritte {#getting-started}

Bevor Sie mit Ihren detaillierten Testfällen und Ihrem Testplan beginnen, können Sie Folgendes tun:

**Ziele definieren** - Definieren Sie Ihre allgemeinen Ziele, um als Ausgangspunkt für die Feinabstimmung beim Testen zu dienen. Sie sollten Folgendes tun:

* Testen Sie die Funktion anhand der detaillierten Anforderungsspezifikationen.
* Testen Sie die Leistung anhand der [Zielmetriken](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

Diese Liste ist nicht erschöpfend.

**Traffic-Statistiken von der vorhandenen Website abrufen** - Diese Informationen können aus den Protokolldateien extrahiert werden. Weitere Informationen finden Sie unter Leistungsüberwachung .

Diese Zahlen geben einen Überblick über den aktuellen Traffic (Menge und Verteilung) auf der vorhandenen Website und können als Ausgangspunkt für die neue Website verwendet werden.

**Traffic-Statistiken von externen Websites erfassen** - Wenn möglich, können Sie versuchen, Traffic-Statistiken von anderen Websites zum Vergleich, aber diese Zahlen werden nicht immer veröffentlicht.

**Target-Metriken bestätigen** - Metriken werden zur Definition quantitativer Messungen für die Qualität der Website verwendet, da sie die zu erreichenden Leistungsziele darstellen.

Sie sollten zu Beginn des Projekts gemeinsam mit dem Kunden definiert werden. Weitere Informationen finden Sie unter [Zielmetriken](/help/sites-developing/planning.md).
