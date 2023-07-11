---
title: Definieren von Testfällen
description: Ihre Testfälle sollten auf den Anwendungsfällen und der detaillierten Anforderungsspezifikation basieren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
exl-id: c09cde0d-401c-437f-9ec8-a0530c1312d5
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 22%

---

# Definieren von Testfällen{#defining-your-test-cases}

Ihre Testfälle sollten auf Folgendem basieren:

**Anwendungsfälle**

* Diese definieren die erforderliche Funktionalität in Bezug auf die Interaktion zwischen Akteuren (Rollen, die bestimmte Aktionen auslösen) und dem System.
* Die Anwendungsfälle sollten vom Kunden definiert werden.

**Detaillierte Anforderungsspezifikation**

* Alle funktionalen und leistungsbezogenen Anforderungen sollten getestet werden.

Die Tests sollten klar definieren:

* Voraussetzungen; Diese können bestimmte Systeme, Konfigurationen oder Testerlebnisse abdecken.
* Schritte, die zu befolgen sind; auf einer geeigneten Detailebene.
* Erwartete Ergebnisse.
* Klare Kriterien für Bestehen oder Fehlschlagen.

Die Möglichkeit der Automatisierung von Testfällen ist attraktiv, da sich wiederholende Aufgaben entfallen.

## Vergleich von manuellen und automatisierten Tests {#manual-versus-automated-tests}

Die Automatisierung von Testfällen ist jedoch eine wichtige Investition, daher sollten bestimmte Aspekte berücksichtigt werden:

* Sie benötigen Zeit, Mühe und Erlebnis für die Einrichtung und Konfiguration.
* Wenn Browser-basiert sind, besteht ein erhöhtes Risiko von Problemen bei der Installation von Browseraktualisierungen. weitere Korrekturzeit erforderlich machen.
* Nur bei großen Projekten machbar.
* Gut, wenn mehrere Versionen entweder zum Testen oder im langfristigen Release-Plan generiert werden.

## Testen von spezifischen Aspekten {#testing-specific-aspects}

Beim AEM sind einige spezifische Details von besonderem Interesse:

**Autor- und Veröffentlichungsumgebung**

Auch wenn in [Umgebungen](/help/sites-developing/the-basics.md#environments), ist es sinnvoll, einen entscheidenden AEM in Bezug auf Tests hervorzuheben.

Betrachten Sie AEM als zwei Anwendungen:

* die *Autorenumgebung*
Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.
Dies umfasst einen kleinen (er), vorhersehbaren Satz von Benutzern, für die spezifische Funktionalität und Leistung von entscheidender Bedeutung sind.

* die *Veröffentlichen* Umgebung Diese Instanz präsentiert die Website in ihrer veröffentlichten Form für den Zugriff durch Besucher.
Dies umfasst normalerweise eine größere Gruppe von Benutzern, bei denen das Traffic-Volumen nicht immer zu 100 % vorhersehbar ist. Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Erwägen Sie auch Zwischenspeicherung und Lastenausgleich.

Obwohl dieselbe Software als solche:

* unterschiedliche Zwecke nutzen
* verschiedene Anforderungen an Funktionalität und Leistung haben
* unterschiedlich konfiguriert sind
* separat eingestellt werden
* jeder hat seine eigenen Abnahmeprüfungen

Mit anderen Worten, sie müssen separat und mit verschiedenen Testfällen getestet werden.

**Personalisierung**

Beim Testen der Personalisierung sollte jeder einzelne Anwendungsfall mit mehreren Benutzerkonten wiederholt werden, um das Verhalten zu überprüfen.

Überprüfen Sie auch die Zwischenspeicherung auf korrektes Verhalten.

**Der Dispatcher**

Bei den meisten Projekten wird der Dispatcher für die Zwischenspeicherung und den Lastenausgleich installiert.

Das Testen ist schwierig (Zwischenspeicherung erfolgt auf verschiedenen Ebenen und an verschiedenen Orten) und muss auf Blackbox-Basis durchgeführt werden. Die wichtigsten Aspekte, auf die getestet werden muss:

* **Genauigkeit**
Stellt sicher, dass der Besucher der Website Inhaltsaktualisierungen sieht.

* **Kontinuität**
Stellen Sie sicher, dass die Website weiterhin verfügbar ist, wenn ein Server heruntergefahren wird.

* **Cluster**
Wird verwendet, um Folgendes bereitzustellen:

   * **Failover**
Wenn ein Server ausfällt, übernehmen andere Server im Cluster die Verarbeitung.

   * **Leistung**
Lastenausgleich mit vollständigem Failover erhöht die Leistung eines Clusters.
Wenn dies für ein Kundenprojekt verwendet wird, muss der Cluster getestet werden, um den korrekten Ablauf der Konfiguration zu bestätigen.

## Testen von Software von Drittanbietern {#testing-third-party-software}

Jede Software von Drittanbietern, die mit AEM verbunden ist, wird in den detaillierten Anforderungsspezifikationen aufgeführt.

Sämtliche erforderlichen Tests (abhängig vom definierten Umfang) müssen analysiert werden und als sauber getestet werden.
