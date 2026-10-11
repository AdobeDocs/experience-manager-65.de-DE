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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 83%
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

* die *Autoren*Umgebung
Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.
Sie hat einen klein(er)en, vorhersehbaren Benutzerkreis, für den spezielle Funktionen und Leistung äußerst wichtig sind.

* die *Veröffentlichungs*Umgebung
Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.
Daraus ergibt sich meist ein größerer Benutzerkreis und das Traffic-Volumen ist nicht immer zu 100 % vorhersehbar. Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Erwägen Sie auch Caching und Lastenausgleich.

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

Das Testen ist schwierig (Caching tritt auf unterschiedlichen Ebenen und in verschiedenen Orten auf) und muss auf Blackbox-Basis vorgenommen werden. Die zu testenden Hauptaspekte sind:

* **&#x200B;**
Stellt sicher, dass dem Website-Besucher Inhaltsaktualisierungen angezeigt werden.

* **Continuity**
Stellen Sie sicher, dass die Website auch dann noch verfügbar ist, wenn ein Server heruntergefahren wird.

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
