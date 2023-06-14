---
title: Test- und Tracking-Tools
description: AEM bietet ein Framework zum Testen der Komponentenbenutzeroberfläche und einen Mechanismus zum Testen und Debuggen von Komponenten
uuid: 12abedb5-4ee7-4389-9340-e628adbbc053
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3cf0fd8d-7fc8-468a-bb1e-1debb68a82a5
docset: aem65
exl-id: bb5d1c7c-56ce-4d1e-a3cb-4e74d6922137
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 20%

---

# Test- und Tracking-Tools{#testing-and-tracking-tools}

## Testen {#testing}

AEM bietet:

* [ein Framework für das Testen von Komponentenbenutzeroberflächen](/help/sites-developing/hobbes.md).
* [einen Mechanismus zum Testen und Debuggen von Komponenten](/help/sites-developing/developer-mode.md).

Im Folgenden finden Sie zwei Open Source-Testtools:

**Selenium**

Selenium wird für Funktionstests in einem Browser mit einem Benutzer pro Aktivität verwendet. Testschritte (Klicks) werden entweder als HTML-Tabellen oder als Java™-Klassen aufgezeichnet.

Weitere Informationen finden Sie unter [https://www.selenium.dev/](https://www.selenium.dev/).

**JMeter**

JMeter wird zur Nachverfolgung von Anforderungen verwendet und kann für Funktions-, Leistungs- und Stresstests verwendet werden.

Weitere Informationen finden Sie unter [https://jmeter.apache.org/](https://jmeter.apache.org/).

Es gibt auch viele proprietäre Tools für die Automatisierung von Tests und die Verwaltung von Testplänen.

### Tracking {#tracking}

Die folgenden Tools sind einfach verfügbar. Ein zentrales Problem ist jedoch in allen Fällen die Verfügbarkeit der Daten für alle Mitglieder des Projektteams - Partner und Kunde.

**Bugzilla**

Ein Bug-Tracking-System, das für Ihre eigenen Anforderungen konfiguriert werden kann.

**Tabellen**

Tabellen sind zwar nicht als Bugtracker gedacht, werden aber oft als solche *miss* braucht, da sie leicht verständlich sind und viele Benutzer Erfahrung mit ihrer Verwendung haben.

Wenn diese Tabellen zur Verfolgung verwendet werden, gehen Sie folgendermaßen vor:

* sie sollten einfach gehalten werden.
* die Anzahl der einzelnen Tabellen sollte auf ein Minimum beschränkt werden.
* sie müssen regelmäßig aktualisiert werden.
* Es sollte nur eine Primärkopie aufbewahrt werden und jeder sollte wissen, wo die Primärkopie ist.
* sie sollten für alle Projektmitglieder zugänglich sein.
* Wenn Sicherheit ein Problem ist (häufig bei großen Unternehmen auftritt) und ein gemeinsamer Zugriff nicht möglich ist, können Kopien verteilt werden, solange alle verstehen, dass diese Tabellen Kopien sind und nicht aktualisiert werden können.

Auch für das Tracking von Bugs und Funktionsanforderungen sind proprietäre Tools vorhanden.
