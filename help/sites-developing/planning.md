---
title: Planung
seo-title: Planung
description: Was Sie wissen müssen, um für Ihren Test zu planen
seo-description: Was Sie wissen müssen, um für Ihren Test zu planen
uuid: 29b1127a-da85-46ed-98e7-1c983eb40cfe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 12268c43-93f9-42c1-8dd7-f17f9ae2219b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 59%

---


# Planung{#planning}

In diesem Dokument wird beschrieben, was Sie wissen müssen, um für Ihren Test zu planen. Außerdem sollten Sie die folgenden Fragen beantworten, bevor Sie Ihre Tests durchführen:

* [Welche Testumgebung benötigen Sie?](/help/sites-developing/test-environments.md)
* [Definieren der Testfälle](/help/sites-developing/test-cases.md)
* [Testen – wann und mit wem?](/help/sites-developing/when-who.md)

## Bevor Sie beginnen {#before-you-start}

Bevor Sie mit der eigentlichen Analyse und Definition der Tests beginnen, lesen Sie die folgenden Informationen durch:

**AEM Architektur**  - Siehe Grundkonzepte, um sich der Architektur und den Grundprinzipien der AEM vorzustellen.

**Dokumentation**  - Weitere Informationen finden Sie in den einzelnen Dokumentationsabschnitten oder in &quot;How To&quot;-Artikeln.

**Grundlegende Testprinzipien**  - Sie sollten sich der Grundprinzipien der Softwareprüfung und Qualitätssicherung bewusst sein. Vorzugsweise sollten Sie bereits Erfahrung mit Projekttests haben.

Es gibt viele Websites, Bücher und Kurse, die solche Prinzipien behandeln. Deshalb werden wir sie in diesem Dokument nicht besprechen.

**Annahmen zur Vermeidung**  - Die größte Annahme (regelmäßig gemacht) ist, dass Ihre Website täglich Millionen von Anfragen bearbeiten muss. Unter bestimmten Umständen kann dies zutreffen, Sie sollten es jedoch nicht grundsätzlich voraussetzen.

Zukünftige Werte können zwar nicht 100 % genau vorausgesagt werden, aber Sie erhalten einen guten Anhaltspunkt, indem Sie Ihre aktuelle Website und den Besucher-Traffic beobachten. Sie können dann anhand des Faktors, um den der Besucher-Traffic erwartungsgemäß/hoffentlich wachsen wird, Schätzungen aufstellen.

**Bekenntnis zur Qualität**  - Es ist von größter Bedeutung, dass jeder, der Tests durchführt, neutral bleibt und einfach die Ergebnisse der durchgeführten Tests meldet.

Es liegt in der Verantwortung des Projektmanagers, abhängig von den Ergebnissen Handlungen zu bestimmen und zu veranlassen.

**Einbindung**  - Obwohl es Aufgabe des Projektmanagers ist sicherzustellen, dass alle Beteiligten an allen Sitzungen (Status, Workshops usw.) umfassend beteiligt sind, sollten Sie auch versuchen, so früh wie möglich in den Projektzyklus einbezogen zu werden, einschließlich der Informationserfassung und der erforderlichen Analyse.

**Beziehen Sie den Kunden**  ein: Versuchen Sie, den Kunden (soweit möglich) bei der Definition Ihrer Testfälle und Planung einzubeziehen.

## Testarten {#types-of-tests}

Es gibt verschiedene Standardklassifikationen von Tests, die sich zum Testen von AEM-Projekten eignen. Sie sollten mit ihnen vertraut sein, um zu entscheiden, welche Sie verwenden möchten:

>[!NOTE]
>
>Sie werden in ihrer chronologischen Durchführungsreihenfolge aufgeführt.

**Einheiten Tests**  - Tests (in der Regel), die vom Entwicklungsteam durchgeführt werden, um sicherzustellen, dass sich die einzelnen Elemente korrekt verhalten - wenn auch isoliert.

**Integrationstests**  - Testen von Modulen bei Kombination. Diese Tests werden nach Unit-Tests, aber vor Systemtests durchgeführt.

**Rauch-Tests**  - Diese sind schnelle und schmutzige Tests, die belegen, dass die Software läuft und eine hohe Funktionalität zur Verfügung steht. Es werden keine Detailtests durchgeführt.

**Funktionstests**  - Diese werden verwendet, um die Funktionalität der Software zu testen. Eine Testreihe wird konzipiert, die alle Funktionsdetails mit vorgesehenen, nicht vorgesehenen und/oder fehlerhaften Eingaben abdeckt.

Black-Box-Tests sind Funktionsprüfungen einer vollständigen Einheit/Komponente/eines Moduls und werden ohne Kenntnis der internen Funktionsweise des betreffenden Elements durchgeführt.

**Systemtests**  - Diese testen das gesamte System, sobald es vollständig integriert und auf einer geeigneten Plattform installiert ist.

Sie testen die Funktionalität nach dem Black-Box-Prinzip.

**Leistungstests**  - Leistungstests sind bei AEM von entscheidender Bedeutung.

Sie zeigen die Leistung unter verschiedenen Bedingungen auf:

* Normal

   Bedingungen, die in etwa 90 % aller Fälle gegeben sind. Beispielsweise verwendet nur ein Teil der Autoren das System.

* Spitze

   Bedingungen, die während relativ kurzer Zeitspannen aufgrund besonderer Umstände auftreten – zum Beispiel, wenn alle Autoren gleichzeitig das System verwenden oder wenn neue Inhalte veröffentlicht werden und eine größere Anzahl von Besuchern Ihre Website nutzt.

* Extrem

   Kann verwendet werden, um die prognostizierte Leistung zu simulieren, wenn neue, besonders interessante Inhalte auf Ihrer Website veröffentlicht werden. In diesem Fall kann eine extreme Spitze auftreten; dies ist jedoch nicht immer vorhersehbar.

   Solche Situationen können auftreten, wenn Karten für bestimmte Ereignisse in den Verkauf gehen oder eine heiß erwartete Website zum ersten Mal live geschaltet wird.

Die Ergebnisse werden dann verwendet, um die Anwendung zu optimieren.

**Stresstests**  - Stresstests werden durchgeführt, um zu bestätigen, wie sich eine Komponente oder Anwendung unter extremen Bedingungen verhält. Insbesondere werden diese Tests verwendet, um zu zeigen, wie sich das Verhalten verschlechtert, wenn das Element fehlschlägt.

**Regressionstests**  - Regressionstests werden verwendet, um zu bestätigen, dass die Funktionalität, die bereits in einer früheren Version der Software nachgewiesen wurde, weiterhin korrekt funktioniert.

Regressionstests eignen sich gut für Automatisierung (sofern möglich), um sicherzustellen, dass sie schnell und konsistent wiederholt werden können.

**Akzeptanztests**  - Akzeptanztests sind eine besondere Kategorie, da sie dazu dienen, die Akzeptanz des Projektes durch den Kunden zu zeigen.

Die Akzeptanztests umfassen möglicherweise einige Tests aus den oben aufgeführten Kategorien. Sie werden ausgewählt, um sicherzustellen, dass das Projekt die Anforderungen des Kunden erfüllt

Weitere Informationen finden Sie unter [Akzeptanz und Abnahme](/help/sites-developing/acceptance-signoff.md).

## Erste Schritte {#getting-started}

Bevor Sie mit Ihren detaillierten Testfällen und Ihrem Testplan beginnen, können Sie Folgendes tun:

**Definieren Sie die Ziele**  - Definieren Sie Ihre übergeordneten Ziele, um als Ausgangspunkt für die Feinabstimmung zu fungieren, während der Test fortgesetzt wird. Sie sollten Folgendes tun:

* Testen Sie die Funktion anhand der detaillierten Anforderungsspezifikationen.
* Testen Sie die Leistung anhand der [Zielmetriken](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

Diese Liste ist nicht erschöpfend.

**Traffic-Statistiken von der vorhandenen Website**  erfassen - Diese Informationen können aus den Protokolldateien extrahiert werden - weitere Informationen finden Sie unter Leistungsüberwachung.

Diese Zahlen geben einen Überblick über den aktuellen Traffic (Menge und Verteilung) auf der vorhandenen Website und können als Ausgangspunkt für die neue Website verwendet werden.

**Traffic-Statistiken von externen Websites**  erfassen - Wenn möglich können Sie versuchen, Traffic-Statistiken von anderen Websites zum Vergleich zu erfassen, aber diese Zahlen werden nicht immer veröffentlicht.

**Metriken**  zur Zielgruppe bestätigen: Metriken werden zur Definition quantitativer Messungen für die Qualität der Website verwendet, da sie die zu erreichenden Leistungsziele darstellen.

Sie sollten zu Beginn des Projekts gemeinsam mit dem Kunden definiert werden. Weitere Informationen finden Sie unter [Zielmetriken](/help/sites-developing/planning.md).
