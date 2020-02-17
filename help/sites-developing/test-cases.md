---
title: Definieren von Testfällen
seo-title: Definieren von Testfällen
description: Ihre Testfälle sollten auf den Anwendungsfällen und der detaillierten Anforderungsspezifikation basieren
seo-description: Ihre Testfälle sollten auf den Anwendungsfällen und der detaillierten Anforderungsspezifikation basieren
uuid: daaa5370-bcd3-45a6-9974-f9b5af6a1529
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: f01eb2aa-6891-4f5d-8a4a-43fc1534c222
docset: aem65
translation-type: tm+mt
source-git-commit: da08613be784f43ad3e3c3652b7e015640a48a9d

---


# Definieren von Testfällen{#defining-your-test-cases}

Ihre Testfälle sollten auf Folgendem basieren:

**Nutzungsszenarien**

* Diese definieren die erforderliche Funktionalität in Bezug auf die Interaktion zwischen Akteuren (Rollen, die bestimmte Aktionen auslösen) und dem System.
* Die Nutzungsszenarios sollten vom Kunden definiert werden.

**Detaillierte Anforderungsspezifikation**

* Alle Funktions- und Leistungsanforderungen sollten getestet werden.

Die Tests sollten eindeutig definieren:

* Voraussetzungen; diese umfassen möglicherweise bestimmte Systeme, Konfigurationen oder Testerfahrung.
* Schritte die zu befolgen sind; in angemessenen Details.
* Erwartete Ergebnisse.
* Klare Kriterien für Bestehen/Nichtbestehen.

Die Aussicht, Testfälle zu automatisieren, ist offensichtlich attraktiv, da dadurch repetititve Aufgaben eliminiert werden können.

## Manuelle und automatisierte Tests {#manual-versus-automated-tests}

Die Automatisierung von Testfällen ist jedoch eine erhebliche Investition, daher sollten bestimmte Aspekte berücksichtigt werden:

* Benötigen Zeit, Mühe und Erfahrung beim Einrichten und Konfigurieren.
* Wenn sie browserbasiert sind, besteht ein erhöhtes Risiko für Probleme, wenn Browser-Updates installiert werden; es bedarf weiterer Korrekturzeit.
* Nur tatsächlich praktikabel für große Projekte.
* Gut, wenn mehrere Versionen entweder zum Testen oder im langfristigen Freigabeplan generiert werden.

## Testen spezifischer Aspekte {#testing-specific-aspects}

Beim Testen von AEM sind einige spezifische Details von besonderem Interesse:

**Autor- und Veröffentlichungsumgebung**

Although, covered in [Environments](/help/sites-developing/the-basics.md#environments) it is worth highlighting a deciding factor of AEM with regard to testing.

Sie müssen AEM als zwei Anwendungen betrachten:

* die *Authoring* -UmgebungDiese Instanz ermöglicht Autoren die Eingabe und Veröffentlichung von Inhalten.
Sie hat einen klein(er)en, vorhersehbaren Benutzerkreis, für den spezielle Funktionen und Leistung äußerst wichtig sind.

* die *Veröffentlichungsumgebung*
Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.
Daraus ergibt sich meist ein größerer Benutzerkreis und das Traffic-Volumen ist nicht immer zu 100 % vorhersehbar. Leistung ist immer noch entscheidend - wenn auf Anfragen reagiert wird. Caching und Lastenausgleich müssen ebenfalls berücksichtigt werden.

Zwar handelt es sich um dieselbe Software, doch die Umgebungen:

* dienen verschiedenen Zwecken
* haben unterschiedliche Anforderungen hinsichtlich Funktionalität und Leistung
* sind unterschiedlich konfiguriert
* werden separat eingestellt
* haben jeweils einen eigenen Satz von Funktionstests

Mit anderen Worten, sie müssen separat und mit verschiedenen Testfällen getestet werden.

**Personalisierung**

Beim Testen der Personalisierung sollte jeder einzelne Anwendungsfall mit mehreren Benutzerkonten wiederholt werden, um das Verhalten nachzuweisen.

Caching muss auch auf korrektes Verhalten geprüft werden.

**Der Dispatcher**

Bei den meisten Projekte installieren Sie den Dispatcher für Caching und Lastenausgleich.

Das Testen ist schwierig (Caching tritt auf unterschiedlichen Ebenen und in verschiedenen Orten auf) und muss auf Blackboxbasis vorgenommen werden. Die zu prüfenden Hauptaspekte sind:

* **Genauigkeit** stellt sicher, dass Inhaltsaktualisierungen vom Website-Besucher angezeigt werden.

* **Kontinuität** gewährleistet, dass die Website weiterhin verfügbar ist, wenn ein Server heruntergefahren wird.

* **Cluster** werden verwendet, um Folgendes bereitzustellen:

   * **Failover** Wenn ein Server ausfällt, übernehmen andere Server im Cluster die Verarbeitung.

   * **Performance**-Lastenausgleich mit vollständigem Failover erhöht die Leistung eines Clusters.
Wenn dies für ein Kundenprojekt verwendet wird, muss der Cluster getestet werden, um den korrekten Ablauf der Konfiguration zu bestätigen.

## Testen von Software von Drittanbietern {#testing-third-party-software}

Jede Software von Drittanbietern, die mit AEM verbunden ist, wird in den detaillierten Anforderungsspezifikationen referenziert.

Sämtliche erforderlichen Tests (abhängig vom definierten Umfang) müssen analysiert werden und als sauber getestet werden.
