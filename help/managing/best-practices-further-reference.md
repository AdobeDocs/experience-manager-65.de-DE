---
title: Die Checkliste – Weitere Referenzen
description: Erfahren Sie mehr über weitere Details, die die Dokumente und Grundsätze der Checkliste „Verwalten von Projekten – Best Practices“ erläutern und/oder ergänzen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing-checklist
content-type: reference
exl-id: 36620e3e-ecdf-4062-bbef-65513362d691
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '3699'
ht-degree: 100%

---

# Die Checkliste – Weitere Referenzen{#the-checklist-further-reference}

Auf dieser Seite finden Sie weitere Details, die die Dokumente und Grundsätze erläutern und/oder ergänzen, die die in der [Checkliste „Verwalten von Projekten – Best Practices“](/help/managing/best-practices.md) behandelt werden.

## AEM – Was werden Sie verwenden? {#aem-what-will-you-be-using}

>[!CAUTION]
>
>Die Listen in diesem Unterabschnitt sind nicht vollständig, sollen jedoch als Einführung dienen.

### Funktionen in AEM {#features-within-aem}

Bei der Implementierung von AEM (insbesondere beim ersten Mal) müssen Sie die [Funktionen und Workflows von AEM](https://business.adobe.com/de/products/experience-manager/adobe-experience-manager.html) überprüfen, um sicher zu sein, welche Bereiche Sie haben möchten oder benötigen.

Überlegen Sie, welche Funktionen von AEM sie verwenden und welche Auswirkungen sie auf Ihr Design haben; zum Beispiel:

* [Commerce](/help/commerce/cif-classic/administering/ecommerce.md)
* [Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de)
* [Assets](/help/assets/assets.md)
* [Tags](/help/sites-administering/tags.md)
* [Multi-Site-Management und Übersetzung](/help/sites-administering/msm-and-translation.md)
* [Formulare](/help/forms/home.md)
* [Communities](/help/communities/deploy-communities.md)

Überprüfen Sie außerdem die [Versionshinweise](/help/release-notes/release-notes.md) für die verschiedenen Versionen von AEM, um zu sehen, wann neue Funktionen hinzugefügt wurden.

### Integrationen {#integrations}

AEM kann mit anderen Adobe-Produkten oder mit Drittanbieterdiensten oder beidem integriert werden. Diese Workflows können Leistung und Funktionalität steigern, die Ihnen zur Verfügung steht.

Siehe [Lösungsintegration](/help/sites-administering/integration.md), um die vollständigen Informationen zu erhalten.

## Migration oder Upgrade? {#migrate-or-upgrade}

Eine wichtige Überlegung ist, ob Sie:

* ein Upgrade Ihrer vorhandenen Version durchführen möchten.
* den Inhalt aus dem aktuellen System in eine neue Installation migrieren möchten.

Beim Übergang von einer früheren Version zur aktuellen Version gibt es zwei Optionen:

* Verwendung des [Package Manager](/help/sites-administering/package-manager.md), um den gesamten Inhalt und Anwendungscode aus dem alten System in das neue zu exportieren.
* Durchführung eines [Upgrade](/help/sites-deploying/upgrade.md) für das alte System. Diese Methode wird in der Regel empfohlen.

## Grundregeln {#basic-ground-rules}

Wie bei jedem Projekt ist es von entscheidender Bedeutung, so bald wie möglich Grundregeln festzulegen. Zu diesen Regeln gehören:

>[!NOTE]
>
>Diese Punkte sind allgemein gehalten, die [Checkliste mit Best Practices](/help/managing/best-practices.md) behandelt Besonderheiten in Bezug auf AEM.

* **Rollen**

  Rollen sollten klar definiert und allen am Projekt beteiligten Personen bekannt gemacht werden. Außerdem ist es ratsam, Folgendes hervorzuheben:

   * Entscheidungsträger
   * Kontaktstellen

* **Zuständigkeiten**

   * Es hilft, für jede Rolle eine klare Definition der Verantwortlichkeiten in Bezug auf Ihr Projekt zu haben, um Verwirrung zu vermeiden.

* **Beteiligung**

  Wenn Sie alle Beteiligten so bald wie möglich einbinden, können Sie sie ermutigen, *Stakeholder* des Projekts zu werden. Dadurch sind sie stärker am Erfolg des Projekts interessiert.

   * Auf Kundenseite umfasst diese Rolle die Autorinnen und Autoren, die täglich mit dem System arbeiten
   * In Ihrem eigenen Projektteam gehören dazu auch die Verantwortlichen für die Qualitätssicherung. Je besser sie die Anforderungen des Kunden bzw. der Kundin verstehen, desto besser können sie die Tests planen.

* **Kommunikationswege**

   * Auch wenn die Kommunikationswege nicht übermäßig formalisiert werden sollten, sollten spezifische Definitionen gewährleisten, dass die Schlüsselpersonen stets informiert werden und somit auf dem neuesten Stand gehalten werden. Besonderes Augenmerk sollte auf die Kommunikation mit externen Parteien gelegt werden.

* **Prozesse**

  Die definierten Prozesse hängen von Ihrem jeweiligen Projekt ab. Denken Sie daran, diese Prozesse einfach zu halten, wobei Sie Folgendes berücksichtigen sollten:

   * Die Definition von Prozessen (und Kommunikationswegen) für die Interaktion mit Dritten, z. B. Design-Agenturen und Software-Drittanbietern.
   * Kundinnen und Kunden verfügen häufig über ein eigenes Projekt-Management sowie eigene Verfahren und Werkzeuge für die Berichterstellung.

* **Tracking-Tools**

  Es gibt viele Tools zur Nachverfolgung von Informationen zu Fehlern, Aufgaben und anderen Aspekten Ihres Projekts – siehe [Übersicht der möglichen Tools](#overview-of-potential-tools), um weitere Details zu erhalten.

   * Dabei ist es wichtig, nur eine Kopie der Informationen aufzubewahren und die Informationen (und damit den Zugriff auf das verwendete Tool) zu teilen. Dieser Workflow vereinfacht die Wartung und hilft, Unstimmigkeiten zu vermeiden.

* **Umfang**

  Definieren Sie klar, was das Projekt auf verschiedenen Ebenen abdecken soll:

   * die einzelnen Versionen (wenn ein iterativer Freigabeprozess verwendet wird und unabhängig davon, ob sie an Kundinnen und Kunden oder Ihr internes Test-Team ausgeliefert werden).
   * das AEM-Projekt.
   * das gesamte Projekt, einschließlich Drittanbieter-Software, Auswirkungen auf Tests, organisatorische Fragen und vieles andere.
   * Für bestimmte Aspekte kann es auch sinnvoll sein anzugeben, was *nicht* im Projektumfang enthalten ist. Dies kann dazu beitragen, Verwirrung und falsche Annahmen zu vermeiden, sollte aber auf grundlegende Fragen beschränkt bleiben.

* **Reporting**

  Definieren Sie klar, welche Informationen berichtet werden sollen, in welcher Form, wie oft und an wen.

* **Terminologie**

   * Definieren Sie die zu verwendenden Abkürzungen und/oder kundenspezifischen Begriffe.

* **Annahmen**

   * Definieren Sie mögliche Annahmen, die gemacht werden.

Diese Informationen können in einem Projekthandbuch definiert werden; die Verwendung eines Wikis kann auch dazu beitragen, dass laufende Änderungen effizient behandelt werden. Wo immer diese Annahmen definiert werden, sind die Schlüsselfaktoren die folgenden:

* Informationen werden definiert und gepflegt
* Die Informationen werden allen beteiligten Personen klar mitgeteilt. Auch wenn es Standardpraxis des Projekt-Managements ist, kann nicht oft genug wiederholt werden, dass eine klare Rollendefinition und eine gute Kommunikation über den Erfolg und Misserfolg eines Projekts entscheiden kann.
* Es wird nur eine Version der verfolgten Informationen aufbewahrt, z. B. Fehlerverfolgung und Problemverfolgung.

## Wichtige Leistungsindikatoren und Zielmetriken {#key-performance-indicators-and-target-metrics}

Unternehmen verwenden Key Performance Indicators (KPIs), um ihren Erfolg bei der Erreichung von Zielen zu bewerten. Diese Indikatoren sind messbare Werte, anhand derer nachgewiesen werden kann, wie effektiv bestimmte Ziele erreicht werden.

Diese Indikatoren können sein:

* Geschäft:

   * Verwendung zum Messen wichtiger Unternehmensziele.
   * Es ist wichtig, KPIs auszuwählen, die für Ihr Unternehmen/Szenario geeignet sind, wobei klar definiert sein sollte, um was für KPIs es sich handelt, wie sie verwendet werden und von wem.

* Leistung:

   * Definieren, wie die Leistung des Systems gemessen wird.
   * Einige Beispiele sind die Seitenladezeit, die Antwortzeit des Servers und die Leistung der Datenbankabfrage.

Einige, aber nicht alle Indikatoren können auf den Zielmetriken basieren, die Sie identifizieren und definieren.

### Zielmetriken {#target-metrics}

Metriken dienen zur Definition quantitativer Messungen für die Qualität Ihrer Website. Sie sind im Grunde eine Definition der Leistungsziele, die Sie erreichen möchten, und können für die Definition Ihrer [KPIs (Key Performance Indicators)](#key-performance-indicators-and-target-metrics) verwendet werden.

Sie können eine Vielzahl von Metriken definieren, die meisten decken jedoch die Ziele für Leistung und Gleichzeitigkeit ab. Es geht insbesondere um Faktoren, die schwer zu quantifizieren und häufig anfällig für *emotionale* Bewertungen sind:

* „Die Website ist heute *viel zu langsam*“ – Was gilt als *langsam*?

* „Alles *kommt zum Stillstand*, wenn meine Kollegin sich anmeldet“ – wie viele gleichzeitige Benutzerinnen und Benutzer kann das System verkraften?
* „Wenn ich suche, *friert das System ein*“ – welche Suchanfragen wirken sich auf das System aus?
* „Es dauert *ewig*, die Datei herunterzuladen“ – welche Download-Zeiten sind akzeptabel (unter normalen Netzwerkbedingungen)?

Zielmetriken werden zu Beginn eines Projekts definiert, um:

* die erwarteten Abmessungen der Website anzugeben, die Sie anbieten können
* die Mindestqualität anzugeben, die Sie erreichen möchten
* zu bestimmen, wie diese Faktoren gemessen werden
* als Grundlage für die [Key Performance Indicators](#key-performance-indicators-and-target-metrics) verwendet zu werden

Wie immer ist bei der Definition der Zielmetriken Vorsicht geboten:

* wenn sie zu hoch eingestellt sind, können sie unerreichbar sein
* bei zu niedriger Einstellung werden zu niedrige Schwankungen eventuell nicht hervorgehoben
* um sicherzustellen, dass sie wiederholt und konsistent gemessen werden können
* um eine Balance zwischen den verschiedenen gemessenen Faktoren zu bieten
* bestimmte Metriken beziehen sich auf eine Testumgebung, wobei einige jedoch reale Szenarien widerspiegeln sollten, da sie auf Ihrer Produktions-Website messbar und reproduzierbar sein müssen
* die Metriken entsprechend ihrer Bedeutung für die Website zu priorisieren
* die Metriken auf einen Satz zu beschränken, der überwacht werden kann

Während der Entwicklung des Projekts können sie aktualisiert und nach Bedarf angepasst werden. Nachdem das Projekt erfolgreich implementiert wurde, können sie verwendet werden, um Sie bei der Kontrolle Ihrer Installation und der Überwachung/Aufrechterhaltung der erforderlichen Servicestufe für den laufenden Betrieb zu unterstützen.

Bei richtiger Anwendung können diese Metriken ein nützliches Werkzeug sein; bei unverantwortlicher Anwendung können sie eine zeitraubende Ablenkung darstellen. Wie immer sollten Sie verstehen, was Sie messen, wie Sie es messen und warum.

>[!NOTE]
>
>In diesem Abschnitt werden die Grundprinzipien und zu bedenkende Punkte diskutiert. Jede Installation ist anders, sodass die tatsächlichen Werte, die gemessen werden, unterschiedlich sein können.

### Alles hängt von Ihrem Projektdesign ab {#everything-rests-on-your-project-design}

Alle gemessenen Metriken sind vom Design Ihres Projekts betroffen. Umgekehrt lassen sich viele Probleme am besten durch Design-Änderungen lösen.

Deshalb sollten Sie Ihre Zielmetriken definieren, *bevor* Sie sich für Ihr Design entscheiden. Auf diese Weise können Sie Ihr Design anhand dieser Faktoren optimieren. Wenn Ihr Projekt entwickelt wurde, ist es schwierig, die grundlegenden Design-Prinzipien zu ändern.

Wenn Sie die Struktur für die Website erstellen, folgen Sie der empfohlenen Struktur für AEM Sites. Vergewissern Sie sich, dass Sie die folgenden Punkte und/oder Prinzipien verstehen:

* Wie Website-Inhalte strukturiert werden.
* Die Funktionsweise von Vorlagen und Komponenten.
* Wie funktioniert das Zwischenspeichern?
* Wie sich personalisierte Inhalte auswirken.
* Wie die Suchfunktion funktioniert.
* Wie CSS und zugehörige Technologien verwendet werden können, um kompakten, nicht redundanten HTML-Code zu erstellen.

Wenn Sie der Meinung sind, dass Ihr Design nicht den Richtlinien entspricht, oder wenn Sie sich bezüglich einiger der Auswirkungen nicht sicher sind, klären Sie diese Punkte. Führen Sie diese Schritte aus, bevor Sie mit der Programmierung oder dem Ausfüllen des Inhalts beginnen.

### Infrastruktur {#infrastructure}

Für die Definition oder Bewertung der Infrastruktur ist es hilfreich, Zielwerte zu definieren, z. B.:

* Besuchende/Tag; sowohl im Durchschnitt als auch zu Spitzenzeiten
* Treffer/Tag; sowohl im Durchschnitt als auch zu Spitzenzeiten
* Anzahl der verfügbaren Web-Seiten
* Volumen des Web-Inhalts

Je nach Ihrer Situation und der strategischen Bedeutung der Website können Sie mithilfe der Definition der Infrastruktur Ihre Infrastruktur bewerten und auswählen:

* Anzahl der Server
* Anzahl von AEM-Instanzen (Authoring- und Publishing-Instanz)

### Leistung {#performance}

Es gibt verschiedene Leistungsfaktoren, die ausgewertet werden können:

* Antwortzeiten für einzelne Seiten, unter Berücksichtigung von:

   * Antwortzeiten in einer Authoring-Umgebung
   * Antwortzeiten in der Publishing-Umgebung

* Antwortzeiten für Suchanfragen

Dieser Abschnitt kann in Verbindung mit dem Abschnitt [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) gelesen werden, in dem die technischen Details der eigentlichen Leistungsmessung näher erläutert werden.

#### Reaktionszeiten einzelner Seiten {#response-times-for-individual-pages}

Ein wichtiger Faktor ist die Zeit, die Ihre Website benötigt, um auf Anfragen durch Besucherinnen und Besucher zu reagieren.

Auch wenn dieser Wert für jede Anfrage unterschiedlich ist, kann ein durchschnittlicher Zielwert definiert werden. Sobald sich gezeigt hat, dass dieser Wert sowohl erreichbar ist als auch beibehalten werden kann, kann er verwendet werden, um die Leistung der Website zu überwachen und die Entwicklung potenzieller Probleme anzuzeigen.

Unterschiedliche Ziele in Authoring- und Publishing-Umgebungen

Die Antwortzeiten, die Sie anstreben, unterscheiden sich in der Authoring- und der Publishing-Umgebung und spiegeln die Zielgruppe wider:

* **Autorenumgebung**

  Diese Umgebung wird von Autorinnen und Autoren verwendet, die Inhalte eingeben und aktualisieren. Daher muss sie:

   * einige wenige Benutzerinnen und Benutzer bedienen können, die beim Aktualisieren von Inhaltsseiten und einzelnen Elementen auf diesen Seiten eine hohe Anzahl von Anforderungen generieren
   * so schnell wie möglich sein, um die Produktivität bei der Bereitstellung Ihrer Inhalte auf der Website zu maximieren

* **Veröffentlichungsumgebung**

  Diese Umgebung enthält Inhalte, die Sie Ihren Benutzerinnen und Benutzern zur Verfügung stellen:

   * Die Geschwindigkeit ist auch hier wichtig, darf aber gewöhnlich langsamer sein als in der Authoring-Umgebung
   * Häufig werden zusätzliche leistungssteigernde Mechanismen angewendet:

      * Der Inhalt wird zwischengespeichert
      * Lastenausgleich wird angewendet

#### Zielantwortzeiten werden festgelegt {#setting-target-response-times}

Wie können Sie über erreichbare (durchschnittliche) Antwortzeiten entscheiden? Die Frage und Antwort ist oft eine Frage der Erfahrung:

* Bisherige Erfahrungen auf Ihrer Website
* Erfahrung mit AEM
* Das Erkennen komplexer Seiten mit überdurchschnittlichen Antwortzeiten (diese Seiten sollten nach Möglichkeit einzeln optimiert werden)

Unter kontrollierten Umständen können immerhin die folgenden Leitlinien angewendet werden:

* 70 % der Seitenanfragen sollten in weniger als 100 ms beantwortet werden.
* 25 % der Seitenanfragen sollten in 100 ms bis 300 ms beantwortet werden.
* 4 % der Seitenanfragen sollten in 300 ms bis 500 ms beantwortet werden.
* 1 % der Seitenanfragen sollten in 500 ms bis 1000 ms beantwortet werden.
* Keine Seite sollte langsamer als 1 Sekunde reagieren.

Die obigen Zahlen gehen von folgenden Bedingungen aus:

* gemessen bei der Veröffentlichung (kein Mehraufwand durch eine Authoring-Umgebung und/oder CFC)
* gemessen auf dem Server (kein Netzwerkaufwand)
* nicht zwischengespeichert (kein AEM-Ausgabe-Cache, kein Dispatcher-Cache)
* nur für komplexe Elemente mit vielen Abhängigkeiten (HTML, JS, PDF usw.)
* keine andere Last auf dem System

Es gibt verschiedene Mechanismen, mit denen Sie die Antwortzeiten überwachen können:

* **Überwachen der Antwortzeiten mit „request.log“ von AEM**

  Ein guter Ausgangspunkt für Leistungsanalysen ist das Anforderungsprotokoll. Neben anderen Informationen können Sie die Antwortzeiten einzelner Anfragen einsehen. Siehe [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) für weitere Informationen.

* **Überwachen von Antwortzeiten mit HTML-Kommentaren**

  HTML-Kommentare können verwendet werden, um Informationen zur Antwortzeit in die Quelle jeder Seite einzufügen:

  `</body> </html>v <-- Page took 58 milliseconds to be rendered by the server --> Response times for search requests`

#### Suchanfragen {#search-requests}

Suchanfragen können erhebliche Auswirkungen auf Ihre Website haben, im Hinblick auf:

* die Antwortzeit der tatsächlichen Suche

   * Eine schnelle Suchfunktion ist ein Qualitätsziel für Ihre Website.

* die Auswirkungen auf die allgemeine Leistung

   * Da eine Suchfunktion (potenziell große) Abschnitte des Inhalts oder einen speziell extrahierten Index scannen muss, kann diese Funktion die Leistung des gesamten Systems beeinträchtigen, wenn sie nicht optimiert wird.

Das Festlegen von Zielen für Suchanfragen ist wiederum eine Frage der Erfahrung, die von mehreren Faktoren abhängt:

* Erfahrung mit AEM
* eine Einschätzung, wie oft die Suche im Vergleich zu anderen Zielen verwendet wird
* Ihr Persistenzmanager
* Ihr Suchindex
* die Komplexität Ihrer Suchfunktion; eine einfache Suchfunktion, die die Eingabe eines Suchbegriffs ermöglicht, ist schneller als eine erweiterte Suche, mit der der Benutzer bzw. die Benutzerin komplexe Suchanweisungen mit „UND/ODER/NICHT“ erstellen kann.

Diese Suchanfragen sollten von Anfang an in Ihr Projekt integriert und eingeplant werden. Zu den für die Überwachung verfügbaren Mechanismen gehören:

* **Überwachen der Suchantwortzeiten mit „request.log“ von AEM**

  Auch hier kann „request.log“ verwendet werden, um die Antwortzeiten für Suchanfragen zu überwachen; siehe [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) für weitere Details.

* **Programmierte Mechanismen zur Messung der Suchantwortzeiten**

  Um die von Ihnen erfassten Informationen zu Suchanfragen und deren Leistung anzupassen, wird empfohlen, die Informationserfassung in Ihren Projekt-Quell-Code aufzunehmen; siehe [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) für weitere Details.

### Parallelität {#concurrency}

Stellen Sie Ihre Website einigen Benutzer bzw. Benutzerinnen und Besuchern bzw. Besucherinnen in der Authoring- und Publishing-Umgebung zur Verfügung. Die Zahlen sind oft höher als beim Testen, aber auch schwankend und schwer vorhersehbar. Gestalten Sie Ihre Website für eine durchschnittliche Anzahl gleichzeitiger Benutzer bzw. Benutzerinnen und Besucher bzw. Besucherinnen, ohne dass sich dies auf die Leistung auswirkt. Auch hier verwenden Sie die `request.log`, um Parallelitätstests durchzuführen. Siehe [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) für weitere Informationen.

Ziele für die Anzahl gleichzeitiger Benutzer bzw. Benutzerinnen hängen vom Umgebungstyp ab:

* **Autorenumgebung**

   * Normalerweise kann die Anzahl der gleichzeitigen Benutzer bzw. Benutzerinnen genau geschätzt werden. Sie können ermitteln, wie viele Autoren und Autorinnen insgesamt vorhanden sind, obwohl (wahrscheinlich) nicht alle gleichzeitig aktiv sind.

* **Publishing-Umgebung**

   * Die Vorhersage der Publishing-Umgebung ist schwieriger, daher müssen Sie einen Zielwert auswählen. Auch hier sollte es auf den Erfahrungen Ihrer aktuellen Website und realistischen Erwartungen Ihrer neuen Website basieren.
   * Sonderveranstaltungen (z. B. bei der Veröffentlichung neuer beliebter Inhalte) können die Erwartungen oder sogar die Fähigkeiten übertreffen (wie manchmal in der Presse berichtet wird, wenn Tickets für bestimmte Veranstaltungen zum Verkauf angeboten werden).

### Kapazität und Volumen {#capacity-and-volume}

Bevor wir die entsprechenden Metriken besprechen, eine schnelle Definition der Begriffe:

* **Volumen**

   * Die Menge an Ausgabedaten, die vom System verarbeitet und geliefert wird.

* **Kapazität**

   * Die Fähigkeit des Systems, das Volumen bereitzustellen.
   * Bei jedem Schritt werden Kapazität und Volumen unterschiedlich gemessen, wie in der folgenden Tabelle dargestellt. Um eine optimale Leistung zu erzielen, stellen Sie sicher, dass die Kapazität dem Volumen in jedem Schritt entspricht und dass sowohl Kapazität als auch Volumen in allen Schritten gemeinsam genutzt werden. Beispielsweise können Sie die Navigation auf dem Client-Computer berechnen oder in den Cache legen, anstatt sie für jede Anfrage auf dem Server zu berechnen.

* **Kapazität und Volumen**

  | Was/Wo | Kapazität | Volumen |
  |---|---|---|
  | Client | Rechenleistung des Computers des Benutzers bzw. der Benutzerin. | Komplexität des Seiten-Layouts. |
  | Netzwerk | Netzwerkbandbreite. | Größe der Seite (Code, Bilder usw.). |
  | Dispatcher-Cache | Server-Speicher des Webservers (Hauptspeicher und Festplatte). | Webserver (Hauptspeicher und Festplatte). Anzahl und Größe der zwischengespeicherten Seiten. |
  | Ausgabe-Cache | Server-Speicher des AEM-Servers (Hauptspeicher und Festplatte). | Anzahl und Größe der Seiten im Ausgabe-Cache, die Anzahl der Abhängigkeiten pro Seite. Der Dispatcher-Cache verringert dieses Volumen. |
  | Webserver | Rechenleistung des Webservers. | Anzahl der Anfragen. Der Cache verringert dieses Volumen. |
  | Vorlage | Rechenleistung des Webservers. | Komplexität der Vorlagen. |
  | Repository | Leistung des Repositorys. | Anzahl der aus dem Repository geladenen Seiten. |

### Andere Metriken {#other-metrics}

In den vorherigen Abschnitten werden die zu definierenden Hauptmetriken beschrieben.

Je nach Ihren spezifischen Anforderungen kann es nützlich sein, zusätzliche Metriken zu definieren, entweder isoliert oder unter Berücksichtigung der oben genannten Klassifizierungen.

Es empfiehlt sich jedoch, einen kleinen Satz genauer, zentraler Metriken zu verwenden, die einfach und zuverlässig funktionieren, anstatt jeden Aspekt Ihrer Website zu messen und zu definieren. Es liegt in der Natur der Sache, dass sich Ihre Website verändert und weiterentwickelt, sobald sie an Ihre Benutzenden übergeben wird.

## Sicherheit {#security}

Sicherheit ist entscheidend und eine immer größere Herausforderung. Sie ***muss*** von Anfang an berücksichtigt und geplant werden.

Die [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md) beschreibt die Schritte, die Sie unternehmen sollten, um sicherzustellen, dass Ihre AEM-Installation bei der Bereitstellung sicher ist. Weitere Sicherheitsaspekte werden unter [Sicherheit (bei der Entwicklung)](/help/sites-developing/security.md) und [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md) behandelt.

## Parallele und iterative Aufgaben {#parallel-and-iterative-tasks}

>[!NOTE]
>
>Das Folgende:
>
>* Bietet einen Überblick über die *erste* Implementierung eines AEM-Projekts.
>* Ist als abstrakte Übersicht gedacht. Siehe die [Projekt-Checkliste](/help/managing/best-practices.md) für bestimmte Phasen/Milestones/Aufgaben.
>* Jede Zeitskala ist theoretisch.
>

Für eine neue Implementierung eines standardmäßigen AEM-Projekts sollten Sie folgende Aufgaben berücksichtigen:

* Übergabe aus dem Verkaufsprozess.
* Implementierung der Kundenanwendung (**Entwicklung**).
* Installation und Konfiguration der Infrastruktur (und der damit verbundenen Prozesse) auf der Kunden-Site (**Infrastruktur**).
* Erstellung (oder Migration) des Inhalts (**Inhalt**).
* Übergabe an den Betrieb (**Wartung/Support**).
* Folgeversionen.

![chlimage_1-2](assets/chlimage_1-2.png)

Für alle Aspekte wird ein periodischer Ansatz empfohlen:

![chlimage_1-3](assets/chlimage_1-3.png)

>[!NOTE]
>
>Um eine Abstimmung, Optimierung und Benutzerschulung unter realistischen Bedingungen in der Produktionsumgebung zu ermöglichen, unterteilen Sie den Projektstart in **Soft-Launch** (reduzierte Verfügbarkeit, mehrere Iterationen) und **Hard-Launch** (volle Verfügbarkeit – Live).

>[!NOTE]
>
>In der [Projekt-Checkliste](/help/managing/best-practices.md) finden Sie Beispiele für Aufgaben, die Sie während des Lebenszyklus Ihres Projekts durchführen (oder bewerten) sollten.

Einige Punkte, die für jede Kategorie zu beachten sind:

* **Entwicklung**

   * Definieren Sie zuerst die Basisarchitektur.
   * Verwenden Sie mehrere Iterationen (Sprints) für die Entwicklung:

      * Der erste Sprint entspricht dem ersten vollständigen Entwicklungszyklus.
      * Der erste Sprint führt zur ersten Bereitstellung in Ihrer Testumgebung.
      * Jeder Sprint hat ein lauffähiges Ergebnis.
      * Für jeden Sprint erfolgt eine Kundenabnahme (mindestens ein strukturierter Test mit Feedback).

   * Planen Sie den Fall eines Updates der verfügbaren AEM-Version während des Projekts mit ein.
   * Planen Sie Tests und Optimierungen während des Sprints ein.
   * Planen Sie Stabilisierungs- und Optimierungsphasen ein.
   * Erstellen Sie ein Protokoll mit Elementen, die für weitere Versionen geplant werden sollten.
   * Planen Sie die Partnerbeteiligung und -übergabe. ein

* **Infrastruktur**

   * Definieren Sie zuerst die Basisarchitektur:

      * Definieren Sie die Leistungsanforderungen.
      * Definieren Sie Leistungsziele (d. h. Erwartungen klar definieren).
      * Definieren Sie die Architektur von Hardware und Infrastruktur, einschließlich der Größenbestimmung.
      * Definieren Sie die Bereitstellung

   * Verwenden Sie mehrere Durchgänge. Bereiten Sie für den ersten Sprint und die erste Konfiguration Folgendes vor:

      * Entwicklungsumgebung.
      * Entwicklungsprozess.
      * Testumgebung.
      * Bereitstellungsprozess (einschließlich Konfigurationsverwaltung).

   * Planen Sie mehrere Belastungstests.
   * Planen Sie Tests und Optimierungen während des Sprints ein.
   * Planen Sie eine Stabilisierungs- und Optimierungsphase.
   * Stellen Sie das System so früh wie möglich in der Produktionsumgebung bereit (lassen Sie es vom Betriebs-Team einrichten, um Erfahrungen zu sammeln).
   * Verwenden Sie so früh wie möglich benannte Benutzende und definierte Rollen.
   * Planen Sie Schulungen (z. B. Admin-Schulungen).
   * Planen Sie die Übergabe an den Betrieb.

* **Inhalt**

   * Die Basisarchitektur:
      * Steuert die Inhaltshierarchie.
      * Hilft bei der Definition des Inhaltskonzepts.
      * Definiert die Verwendung und das Layout von MSM.
      * Definiert Rollen, Gruppen, Workflows und Berechtigungen.
   * Überlegen Sie, ob eine Offline-Seitenerstellung sinnvoll ist.
   * Planen Sie die frühzeitige Erstellung von ersten Seiten und Inhalten (zur Verwendung in Tests und Feedback).
   * Planen Sie die Migration vorhandener Inhalte.
   * Planen Sie „In-Sprint-Migration“ nach der Überarbeitung.
   * Planen Sie „Inhalts-Burndown“ (Sitemap für Go-Live-Inhalte).

## Schätzung von Zeit und Aufwand {#estimating-time-and-effort}

Abhängig von Ihrer resultierenden Aufgabenliste können Sie dann erste Schätzungen der Zeit und des Aufwands für (allgemeine) Aufgabendefinitionen vornehmen. Diese Schätzungen sollten einen Hinweis darauf enthalten, wer (Kunde bzw. Kundin oder Partner bzw. Partnerin) was und wann tut.

Die folgende Liste zeigt Standardannäherungen und Zusammenhänge des Aufwands und damit der Kosten:

>[!CAUTION]
>
>Diese Zahlen können nur für erste Schätzungen verwendet werden. Die detaillierte Analyse muss von einer erfahrenen AEM-Entwicklungsfachkraft durchgeführt werden.

| Phase | Aufwand |
|---|---|
| Entwicklung | Eine grobe Schätzung von zwei bis vier Stunden für jeden Komponentenknoten, der alle Entwicklungsanforderungen abdeckt. |
| Entwicklertests | 15 % der Entwicklung |
| Folgemaßnahmen | 10 % der Entwicklung |
| Dokumentation | 15 % der Entwicklung |
| JavaDoc-Dokumentation | 10 % der Entwicklung |
| Fehlerbehebung | 15 % der Entwicklung |
| Projekt-Management | 20 % der Projektkosten für laufende Projektverwaltung und Nutzerrechte |

Eine detaillierte Planung kann dann verfügbare oder erforderliche Ressourcen mit Terminen und Kosten verknüpfen.

## Referenzarchitektur {#reference-architecture}

Die Referenzarchitektur dient als Vorlage für die AEM-Architektur. Die Referenzarchitektur behandelt Probleme, die üblicherweise für Unternehmenssysteme auftreten, einschließlich Skalierung, Zuverlässigkeit und Sicherheit.

Die folgenden Site-Metriken sollten definiert werden:

| Klassifizierung | Definition |
|---|---|
| Anzahl der Websites |  |
| Anzahl der Intranet-Sites |  |
| Anzahl der Code-Basen (z. B. wenn Internet und Intranet unterschiedlich sind) |  |
| Anzahl der einzelnen Seiten |  |
| Anzahl der Site-Besuche/Tag |  |
| Anzahl der Seitenaufrufe/Tag |  |
| Umfang der Datenübertragung (in GB)/Tag |  |
| Anzahl gleichzeitiger Benutzer (geschlossene Benutzergruppe) |  |
| Anzahl gleichzeitiger Besucher (Veröffentlichung) |  |
| Anzahl gleichzeitiger Autoren |  |
| Anzahl registrierter Autoren |  |
| Anzahl der Seitenaktivierungen/Arbeitstag |  |
| Anzahl der Seitenaktivierungen während der Bereitstellung |  |

## Übersicht der möglichen Werkzeuge {#overview-of-potential-tools}

Die folgende Liste informiert Sie über die verwendbaren Werkzeuge. Sie ist als Einführung, nicht als umfassende Empfehlungsliste gedacht und sollte Sie nicht davon abhalten, andere Tools zu verwenden.

<table>
 <tbody>
  <tr>
   <td><strong>Produkt</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>AEM</td>
   <td><p>AEM bietet eine Reihe von Mechanismen, mit denen Sie Ihre Applikation überwachen, testen, untersuchen und debuggen können, darunter folgende:</p>
    <ul>
     <li><a href="/help/sites-developing/developer-mode.md">Entwicklermodus</a></li>
     <li>Die <a href="/help/sites-developing/hobbes.md">Testkonsole</a></li>
     <li><a href="/help/sites-administering/operations-dashboard.md">Vorgangs-Dashboard</a></li>
     <li><a href="/help/sites-authoring/content-insights.md">Inhaltseinblick</a></li>
     <li>Die <a href="/help/sites-authoring/author-environment-tools.md#content-tree">Inhaltsstruktur</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Selenium</td>
   <td><a href="https://www.selenium.dev/">Selenium</a> ist ein Open Source-Test-Tool. Die Tests laufen direkt im Browser ab und emulieren, wie Ihre Benutzer arbeiten.</td>
  </tr>
  <tr>
   <td>Microsoft® Project</td>
   <td>Ein häufig verwendetes Projekt-Management-Tool.</td>
  </tr>
  <tr>
   <td>Jira</td>
   <td><a href="https://www.atlassian.com/software/jira">Jira</a> ist ein Open Source-Tool zum Verfolgen und Verwalten von Details Ihrer Softwarefehler. Workflows können bei Bedarf auf die Fehlerdetails angewendet werden.</td>
  </tr>
  <tr>
   <td>Git</td>
   <td><a href="https://git-scm.com/">Git</a> ist eine Software für die Revisionskontrolle.</td>
  </tr>
  <tr>
   <td>Eclipse</td>
   <td><p>Eclipse ist eine Open Source-IDE, die aus verschiedenen Projekten besteht. Diese konzentrieren sich auf den Aufbau einer offenen Entwicklungsplattform, die aus erweiterbaren Frameworks, Tools und Laufzeiten für die Erstellung, Bereitstellung und Verwaltung von Software über den gesamten Lebenszyklus besteht.</p> <p>Weitere Informationen finden Sie unter <a href="/help/sites-developing/howto-projects-eclipse.md">Entwickeln von AEM-Projekten mit Eclipse</a>.</p> </td>
  </tr>
  <tr>
   <td>IntelliJ</td>
   <td><p>Eine professionelle (und damit lizenzkostenpflichtige) IDE mit einem umfassenden Funktionsumfang. </p> <p>Weitere Informationen finden Sie unter <a href="/help/sites-developing/ht-intellij.md">Entwickeln von AEM-Projekten mit IntelliJ IDEA</a>.</p> </td>
  </tr>
  <tr>
   <td>Maven</td>
   <td><a href="https://maven.apache.org/">Maven</a> ist ein Softwaretool für Projekt-Management und Analysen, das den Build-Prozess eines Projekts (Software und Dokumentation) verwalten kann.</td>
  </tr>
 </tbody>
</table>

## Weiterführende Literatur {#further-reading}

Darüber hinaus sind die folgenden Abschnitte von besonderem Interesse:

* [Erste Schritte](/help/sites-deploying/deploy.md#getting-started)
* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Überwachung und Pflege Ihrer Instanz](/help/sites-deploying/monitoring-and-maintaining.md)

### Best Practices {#best-practices}

Adobe bietet weitere Best Practices für alle Phasen und Zielgruppen:

* [Bereitstellen](/help/sites-deploying/best-practices.md)
* [Authoring](/help/sites-authoring/best-practices.md)
* [Verwalten](/help/sites-administering/administer-best-practices.md)
* [Entwickeln](/help/sites-developing/best-practices.md)
* [Projekt-Management](/help/managing/best-practices.md)
