---
title: Test- und Tracking-Tools
description: AEM bietet ein Framework zum Testen der Benutzeroberfläche der Komponenten und einen Mechanismus zum Testen und Debuggen von Komponenten
uuid: 12abedb5-4ee7-4389-9340-e628adbbc053
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3cf0fd8d-7fc8-468a-bb1e-1debb68a82a5
docset: aem65
exl-id: bb5d1c7c-56ce-4d1e-a3cb-4e74d6922137
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: ht
source-wordcount: '292'
ht-degree: 100%

---

# Test- und Tracking-Tools{#testing-and-tracking-tools}

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden finden Sie zwei Open-Source-Test-Tools:

**Selenium**

Selenium wird für Funktionstests in einem Browser mit einer Benutzerin bzw. einem Benutzer pro Aktivität verwendet. Das Tool zeichnet Testschritte (Klicks) entweder als HTML-Tabellen oder als Java™-Klassen auf.

Weitere Informationen finden Sie unter [https://www.selenium.dev/](https://www.selenium.dev/).

**JMeter**

JMeter wird für das Tracking von Anfragen verwendet und kann für Funktions-, Leistungs- und Belastungstests verwendet werden.

Weitere Informationen finden Sie unter [https://jmeter.apache.org/](https://jmeter.apache.org/).

Außerdem sind viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen verfügbar.

### Tracking {#tracking}

Die folgenden Tools stehen zur Verfügung. Eine wichtige Angelegenheit ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projekt-Teams, sowohl auf Partner- als auch auf Kundenseite.

**Bugzilla**

Ein Bugtracker, der Ihren eigenen Anforderungen entsprechend konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht als Bugtracker gedacht, werden aber oft als solche *miss* braucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn Tabellen als Tracker verwendet werden, dann:

* sollten sie einfach gehalten werden.
* sollte die Anzahl der einzelnen Tabellen möglichst gering gehalten werden.
* müssen sie regelmäßig aktualisiert werden.
* sollte nur eine Primärkopie gepflegt werden, deren Speicherort allen bekannt ist.
* sollten sie allen Projektmitgliedern zugänglich sein.
* dürfen Kopien verteilt werden, falls Sicherheit ein Anliegen ist (oft in großen Unternehmen) und ein gemeinsamer Zugriff nicht möglich ist, solange alle verstehen, dass es sich bei den Tabellen um Kopien handelt, die nicht aktualisiert werden können.

Auch für das Tracking von Bugs und Funktionsanforderungen sind proprietäre Tools vorhanden.
