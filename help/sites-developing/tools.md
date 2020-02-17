---
title: Test- und Tracking-Tools
seo-title: Test- und Tracking-Tools
description: AEM bietet ein Framework für das Testen von Komponentenbenutzeroberflächen und einen Mechanismus zum Testen und Debuggen von Komponenten.
seo-description: AEM bietet ein Framework für das Testen von Komponentenbenutzeroberflächen und einen Mechanismus zum Testen und Debuggen von Komponenten.
uuid: 12abedb5-4ee7-4389-9340-e628adbbc053
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3cf0fd8d-7fc8-468a-bb1e-1debb68a82a5
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Test- und Tracking-Tools{#testing-and-tracking-tools}

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden werden zwei Open-Source-Test-Tools vorgestellt:

**Selenium**

Selenium wird für Funktionstests im Browser mit einem Benutzer pro Aktivität verwendet. Das Tool zeichnet Prüfungsschritte (Klicks) entweder als HTML-Tabellen oder Java-Klassen auf.

For more information see [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter wird für das Tracking von Anfragen verwendet und kann für die Automatisierung von Funktions-, Leistungs- und Belastungstests verwendet werden.

For more information see [https://jakarta.apache.org/jmeter/](https://jakarta.apache.org/jmeter).

Außerdem sind viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen verfügbar.

### Tracking {#tracking}

Die folgenden Tools stehen zur Verfügung. Eine wichtige Angelegenheit ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projektteams, also Partner und Kunde.

**Bugzilla**

Ein Bugtracker, der Ihren eigenen Anforderungen entsprechend konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht als Bugtracker gedacht, werden aber oft als solche *miss* braucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn Tabellen als Bugtracker verwendet werden, dann:

* sollten sie einfach gehalten werden.
* sollte die Anzahl der einzelnen Tabellen möglichst gering gehalten werden.
* müssen sie regelmäßig aktualisiert werden.
* sollte nur eine Master-Kopie gepflegt werden, deren Speicherort allen bekannt ist.
* sollten sie allen Projektmitgliedern zugänglich sein.
* dürfen, falls Sicherheit ein Anliegen (oft in großen Unternehmen) und gemeinsamer Zugriff nicht möglich ist, Kopien verteilt werden, solange alle verstehen, dass es sich um Kopien handelt, die nicht aktualisiert werden können.

Auch für das Tracking von Bugs und Funktionsanforderungen sind proprietäre Tools vorhanden.
