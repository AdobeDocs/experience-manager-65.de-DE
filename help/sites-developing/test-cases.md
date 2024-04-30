---
title: Definieren von Testfällen
description: Ihre Testfälle sollten auf den Anwendungsfällen und der detaillierten Anforderungsspezifikation basieren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
exl-id: c09cde0d-401c-437f-9ec8-a0530c1312d5
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 100%

---

# Definieren von Testfällen{#defining-your-test-cases}

Ihre Testfälle sollten auf Folgendem basieren:

**Anwendungsfälle**

* Diese definieren die erforderliche Funktionalität in Bezug auf die Interaktion zwischen Akteuren (Rollen, die bestimmte Aktionen auslösen) und dem System.
* Die Anwendungsfälle sollten auf Kundenseite definiert werden.

**Detaillierte Anforderungsspezifikation**

* Alle Funktions- und Leistungsanforderungen sollten getestet werden.

Die Tests sollten Folgendes eindeutig definieren:

* Voraussetzungen; diese umfassen möglicherweise bestimmte Systeme, Konfigurationen oder Testererfahrung.
* Schritte, die zu befolgen sind (auf einer angemessenen Ebene der Ausführlichkeit).
* Erwartete Ergebnisse.
* Klare Kriterien für Bestehen/Nichtbestehen.

Die Aussicht, Testfälle zu automatisieren, ist attraktiv, da dadurch repetitive Aufgaben eliminiert werden können.

## Manuelle im Vergleich zu automatisierten Tests {#manual-versus-automated-tests}

Die Automatisierung von Testfällen ist jedoch eine erhebliche Investition, daher sollten bestimmte Aspekte berücksichtigt werden:

* Sie benötigen Zeit, Mühe und Erfahrung beim Einrichten und Konfigurieren.
* Wenn sie Browser-basiert sind, besteht ein erhöhtes Risiko für Probleme, wenn Browser-Updates installiert werden, sodass es möglicherweise weiterer Korrekturzeit bedarf.
* Nur praktikabel für große Projekte.
* Gut, wenn mehrere Versionen entweder zum Testen oder im langfristigen Freigabeplan generiert werden.

## Testen von spezifischen Aspekten {#testing-specific-aspects}

Beim Testen von AEM sind einige spezifische Details von besonderem Interesse:

**Autoren- und Veröffentlichungsumgebungen**

Auch wenn dies unter [Umgebungen](/help/sites-developing/the-basics.md#environments) erläutert wird, lohnt es sich, einen entscheidenden Faktor von AEM in Bezug auf Tests noch einmal hier hervorzuheben.

Betrachten Sie AEM als zwei Anwendungen:

* die *Autorenumgebung*
Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.
Sie hat einen klein(er)en, vorhersehbaren Benutzerkreis, für den spezielle Funktionen und Leistung äußerst wichtig sind.

* die *Veröffentlichungsumgebung*
Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucherinnen und Besucher zugreifen können.
Daraus ergibt sich meist ein größerer Benutzerkreis und das Traffic-Volumen ist nicht immer zu 100 % vorhersehbar.  Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Erwägen Sie auch Caching und Lastenausgleich.

Zwar handelt es sich um dieselbe Software, doch die Umgebungen:

* dienen verschiedenen Zwecken
* haben unterschiedliche Anforderungen hinsichtlich Funktionalität und Leistung
* sind unterschiedlich konfiguriert
* werden separat eingestellt
* haben jeweils einen eigenen Satz von Funktionstests

Mit anderen Worten, sie müssen separat und mit verschiedenen Testfällen getestet werden.

**Personalisierung**

Beim Testen der Personalisierung sollte jeder einzelne Anwendungsfall mit mehreren Benutzerkonten wiederholt werden, um das Verhalten nachzuweisen.

Überprüfen Sie auch das Caching auf korrektes Verhalten.

**Der Dispatcher**

Bei den meisten Projekten installieren Sie den Dispatcher für Caching und Lastenausgleich.

Das Testen ist schwierig (Caching tritt auf unterschiedlichen Ebenen und in verschiedenen Orten auf) und muss auf Blackbox-Basis vorgenommen werden.  Die zu testenden Hauptaspekte sind:

* **Genauigkeit**
Stellen Sie sicher, dass den Besucherinnen und Besuchern der Website Inhaltsaktualisierungen angezeigt werden.

* **Kontinuität**
Stellen Sie sicher, dass die Website auch dann noch verfügbar ist, wenn ein Server abgeschaltet ist.

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
