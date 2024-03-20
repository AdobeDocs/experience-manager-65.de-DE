---
title: Hardware-Skalierungsrichtlinien
description: Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Bereitstellung eines AEM-Projekts erforderlich sind.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
docset: aem65
exl-id: 5837ef4f-d4e0-49d7-a671-87d5547e0d98
solution: Experience Manager, Experience Manager 6.5
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '2833'
ht-degree: 44%

---

# Hardware-Skalierungsrichtlinien{#hardware-sizing-guidelines}

Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Bereitstellung eines AEM-Projekts erforderlich sind. Die Größenschätzungen hängen von der Architektur des Projekts, der Komplexität der Lösung, dem erwarteten Traffic und den Projektanforderungen ab. Dieser Leitfaden hilft Ihnen, den Hardwarebedarf für eine bestimmte Lösung zu ermitteln oder eine obere und untere Schätzung für die Hardwareanforderungen zu finden.

Grundlegende Faktoren sind (in dieser Reihenfolge):

* **Netzwerkgeschwindigkeit**

   * Netzwerklatenz
   * Verfügbare Bandbreite

* **Rechengeschwindigkeit**

   * Caching-Effizienz
   * Erwarteter Traffic
   * Komplexität von Vorlagen, Anwendungen und Komponenten
   * Gleichzeitige Autoren
   * Komplexität des Bearbeitungsvorgangs (einfache Inhaltsbearbeitung, MSM-Rollout usw.)

* **I/O-Leistung**

   * Leistung und Effizienz des Datei- oder Datenbankspeichers

* **Festplatte**

   * mindestens zwei- oder dreimal größer als die Größe des Repositorys

* **Arbeitsspeicher**

   * Größe der Website (Anzahl der Inhaltsobjekte, Seiten und Benutzer)
   * Anzahl der gleichzeitig aktiven Benutzer/Sitzungen

## Architektur {#architecture}

Ein typisches AEM-Setup besteht aus einer Autoren- und einer Veröffentlichungsumgebung. Diese Umgebungen haben unterschiedliche Anforderungen hinsichtlich der zugrunde liegenden Hardwaregröße und Systemkonfiguration. Detaillierte Überlegungen zu beiden Umgebungen finden sich in den Abschnitten [Autorenumgebung](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) und [Veröffentlichungsumgebung](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations).

In einem typischen Projekt-Setup stehen Ihnen mehrere Umgebungen zur Verfügung, in denen Sie Projektphasen inszenieren können:

* **Entwicklungsumgebung** Um neue Funktionen zu entwickeln oder wesentliche Änderungen vorzunehmen. Best Practice ist die Verwendung einer Entwicklungsumgebung pro Entwickler (lokale Installationen auf ihren persönlichen Systemen).

* **Autoren-Testumgebung**
Um Änderungen zu verifizieren. Die Anzahl der Testumgebungen kann je nach Projektanforderungen variieren (z. B. getrennt für QA, Integrationstests oder Benutzerakzeptanztests).

* **Veröffentlichungs-Testumgebung** Hauptsächlich zum Testen von Anwendungsfällen der Zusammenarbeit in sozialen Netzwerken und/oder der Interaktion zwischen Autor und mehreren Veröffentlichungsinstanzen.

* **Autoren-Bearbeitungsumgebung** Für Autoren zum Bearbeiten von Inhalten

* **Veröffentlichungs-Bearbeitungsumgebung** Um veröffentlichte Inhalte bereitzustellen.

Außerdem können die Umgebungen variieren, von einem Einzelserver-System mit AEM und einem Anwendungsserver bis hin zu einem hochskalierten Satz von Multi-Server- und Multi-CPU-Clusterinstanzen. Adobe empfiehlt, für jedes Produktionssystem einen separaten Computer zu verwenden und keine anderen Anwendungen auf diesen Computern auszuführen.

## Überlegungen zur allgemeinen Hardwaredimensionierung {#generic-hardware-sizing-considerations}

Die folgenden Abschnitte enthalten Hinweise zur Berechnung der Hardwareanforderungen, wobei verschiedene Aspekte berücksichtigt werden. Bei großen Systemen deutet Adobe darauf hin, dass Sie eine einfache Reihe interner Benchmarktests an einer Referenzkonfiguration durchführen.

Performance-Optimierung ist eine grundlegende Aufgabe, die durchgeführt werden muss, bevor ein Benchmarking für ein bestimmtes Projekt durchgeführt werden kann. Stellen Sie sicher, dass Sie die in der [Dokumentation zur Leistungsoptimierung](/help/sites-deploying/configuring-performance.md) vor Durchführung von Benchmarktests und Verwendung der Ergebnisse für Berechnungen der Hardwaredimensionierung.

Die Anforderungen an die Hardwaredimensionierung für erweiterte Anwendungsfälle müssen auf einer detaillierten Leistungsbewertung des Projekts basieren. Zu den Merkmalen fortgeschrittener Anwendungsfälle, die außergewöhnliche Hardware-Ressourcen erfordern, zählen Kombinationen aus:

* hohe Payload/Durchsatzleistung
* umfangreicher Einsatz von benutzerdefiniertem Code, benutzerdefinierten Workflows oder Software-Bibliotheken von Drittanbietern
* Integration mit nicht unterstützten externen Systemen

### Festplattenspeicher/Festplatte {#disk-space-hard-drive}

Der erforderliche Speicherplatz hängt stark vom Volumen und Typ Ihrer Webanwendung ab. Die Berechnungen sollten Folgendes berücksichtigen:

* die Menge und Größe von Seiten, Assets und anderen im Repository gespeicherten Entitäten wie Workflows, Profilen usw.
* die geschätzte Häufigkeit von Inhaltsänderungen und damit die Erstellung von Inhaltsversionen
* das Volumen der DAM-Asset-Ausgabedarstellungen, die generiert werden
* das Gesamtwachstum von Inhalten im Zeitverlauf

Der Festplattenspeicher wird während der Online- und Offline-Revisionsbereinigung kontinuierlich überwacht. Wenn der verfügbare Speicherplatz unter einen kritischen Wert fällt, wird der Prozess abgebrochen. Der kritische Wert beträgt 25 % des aktuellen Speicherplatzbedarfs des Repositorys und kann nicht konfiguriert werden. Adobe empfiehlt, die Größe der Festplatte mindestens zwei- oder dreimal größer als die Repository-Größe einschließlich des geschätzten Wachstums zu ändern.

Erwägen Sie die Einrichtung redundanter Arrays unabhängiger Festplatten (RAID, z. B. RAID10) zur Datenredundanz.

>[!NOTE]
>
>Der temporäre Ordner einer Produktionsinstanz sollte über mindestens 6 GB verfügbaren Speicherplatz verfügen.

#### Virtualisierung {#virtualization}

AEM funktionieren in virtualisierten Umgebungen gut, es kann jedoch Faktoren wie CPU oder I/O geben, die nicht direkt mit physischer Hardware gleichgesetzt werden können. Es wird empfohlen, eine höhere I/O-Geschwindigkeit (im Allgemeinen) zu wählen, da dies normalerweise ein kritischer Faktor ist. Ein Benchmarking Ihrer Umgebung ist erforderlich, um ein präzises Verständnis der erforderlichen Ressourcen zu erhalten.

#### Parallelisierung AEM Instanzen {#parallelization-of-aem-instances}

**Ausfallsicherheit**

Eine ausfallsichere Website wird auf mindestens zwei getrennten Systemen bereitgestellt. Wenn ein System ausfällt, kann ein anderes System übernehmen und so den Systemausfall kompensieren.

**Skalierbarkeit der Systemressourcen**

Während alle Systeme laufen, steht eine erhöhte Rechenleistung zur Verfügung. Diese zusätzliche Leistung ist nicht unbedingt linear mit der Anzahl der Clusterknoten, da die Beziehung in hohem Maße von der technischen Umgebung abhängig ist. Siehe [Clusterdokumentation](/help/sites-deploying/recommended-deploys.md) für weitere Informationen.

Die Schätzung der erforderlichen Anzahl von Clusterknoten basiert auf den grundlegenden Anforderungen und spezifischen Anwendungsfällen des jeweiligen Webprojekts:

* Aus Sicht der Ausfallsicherheit muss für alle Umgebungen bestimmt werden, wie kritisch ein Fehler ist und wie lange es dauert, bis ein Clusterknoten wiederhergestellt ist.
* Für den Aspekt der Skalierbarkeit ist die Anzahl der Schreiboperationen grundsätzlich der wichtigste Faktor; siehe [Paralleles Arbeiten von Autoren](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) für die Autorenumgebung, und [Zusammenarbeit in sozialen Netzwerken](/help/managing/hardware-sizing-guidelines.md#socialcollaborationspecificconsiderations) für die Veröffentlichungsumgebung. Der Lastausgleich kann für Operationen eingerichtet werden, die nur auf das System zugreifen, um Lesevorgänge zu verarbeiten; siehe [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) für Details.

## Umgebungsspezifische Berechnungen für Autoren {#author-environment-specific-calculations}

Für Benchmarking-Zwecke hat Adobe einige Benchmarktests für eigenständige Autoreninstanzen entwickelt.

* **Benchmarktest 1** Berechnung des maximalen Durchsatzes eines Lastprofils, bei dem Benutzer eine einfache Erstellung einer Seite auf einer Grundlast von 300 vorhandenen Seiten durchführen, die alle von ähnlicher Art sind. Die Schritte bestanden darin, sich bei der Website anzumelden, eine Seite mit einer SWF und Bild/Text zu erstellen, eine Tag-Cloud hinzuzufügen und die Seite zu aktivieren.

   * **Ergebnis**
Der maximale Durchsatz für eine einfache Seitenerstellung, wie oben beschrieben (als eine Transaktion betrachtet), beträgt 1730 Transaktionen/Stunde.

* **Benchmarktest 2** Berechnung des maximalen Durchsatzes, wenn das Lastprofil eine Mischung aus frischer Seitenerstellung (10 %), Änderung einer bestehenden Seite (80 %) und anschließender Änderung einer Seite in Folge (10 %) aufweist. Die Komplexität der Seiten bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Auch hier wurde die Übung auf einer Grundlast von 300 Seiten mit derselben Komplexität wie im Benchmarktest 1 definiert durchgeführt.

   * **Ergebnis** Der maximale Durchsatz für ein solches Mischbetriebsszenario lag bei 3252 Transaktionen pro Stunde.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der zur Messung des Durchsatzes verwendete Ansatz stellt sicher, dass ein fester Anteil jedes Transaktionstyps in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass der Durchsatz je nach Betriebsart variiert. Verwenden Sie die Aktivitäten in Ihrer Umgebung als Grundlage für die Dimensionierung Ihres Systems. Sie erhalten einen besseren Durchsatz durch weniger intensive Aktionen wie Ändern (was auch häufiger vorkommt).

### Caching {#caching}

In der Autorenumgebung ist die Effizienz der Zwischenspeicherung in der Regel deutlich geringer, da Änderungen an der Website häufiger auftreten und auch die Inhalte sehr interaktiv und personalisiert sind. Mithilfe des Dispatchers können Sie AEM Bibliotheken, JavaScript-, CSS-Dateien und Layoutbilder zwischenspeichern. Dies beschleunigt manche Aspekte des Bearbeitungsprozesses. Durch die Konfiguration des Webservers werden auch Kopfzeilen für die Browserzwischenspeicherung in diesen Ressourcen festgelegt, die Anzahl der HTTP-Anfragen verringert und die Reaktionsfähigkeit des Systems, wie sie von den Autoren erfahren wird, verbessert.

### Paralleles Arbeiten von Autoren {#authors-working-in-parallel}

In der Autorenumgebung sind die Anzahl der parallel arbeitenden Autoren und das Laden ihrer Interaktionen, die zum System hinzugefügt werden, die wichtigsten Begrenzungsfaktoren. Daher empfiehlt Adobe, dass Sie Ihr System basierend auf dem gemeinsamen Datendurchsatz skalieren.

In solchen Fällen führte Adobe Benchmarktests auf einem Cluster mit freigegebenen ohne zwei Knoten von Autoreninstanzen durch.

* **Benchmarktest 1a** Mit einem aktiv-aktiven Shared-Nothing-Cluster von 2 Autoreninstanzen berechnen Sie den maximalen Durchsatz mit einem Lastprofil, bei dem Benutzer eine einfache Seitenübung auf einer Grundlast von 300 vorhandenen Seiten durchführen, die alle von ähnlicher Art sind.

   * **Ergebnis**
Der maximale Durchsatz für eine einfache Seitenerstellungs-Übung, wie oben beschrieben (als eine Transaktion betrachtet), beträgt 2016 Transaktionen/Stunde. Dies ist eine Steigerung von ca. 16 % im Vergleich zu einer eigenständigen Autoreninstanz für den gleichen Benchmarktest.

* **Benchmarktest 2b**
Bei einem aktiv-aktiven Shared-Nothing-Cluster von 2 Autoreninstanzen wird der maximale Durchsatz berechnet, wenn das Lastprofil einen Mix aus frischer Seitenerstellung (10 %), Änderung einer bestehenden Seite (80 %) und Erstellung und Änderung einer Seite in Folge (10 %) aufweist. Die Komplexität der Seite bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Auch hier wurde die Übung auf einer Grundlast von 300 Seiten mit Komplexität durchgeführt, die der Definition im Benchmarktest 1 entspricht.

   * **Ergebnis** Der maximale Durchsatz für ein solches Mischbetriebsszenario lag bei 6288 Transaktionen/Stunde. Dies ist eine Steigerung von ca. 93 % im Vergleich zu einer eigenständigen Autoreninstanz für den gleichen Benchmark-Test.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der zur Messung des Durchsatzes verwendete Ansatz stellt sicher, dass ein fester Anteil jedes Transaktionstyps in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass AEM für Autoren, die grundlegende Bearbeitungen mit AEM durchführen, gut skalierbar ist. Im Allgemeinen ist AEM am effektivsten bei der Skalierung von Lesevorgängen.

Auf einer typischen Website erfolgt das meiste Authoring während der Projektphase. Nachdem die Website live geschaltet wurde, sinkt die Anzahl der parallel arbeitenden Autoren in der Regel auf einen niedrigeren Durchschnitt (Betriebsmodus).

Sie können die Anzahl der Computer (oder CPUs), die für die Autorenumgebung benötigt werden, wie folgt berechnen:

`n = numberOfParallelAuthors / 30`

Diese Formel kann als allgemeine Richtlinie für die Skalierung von CPUs dienen, wenn Autoren grundlegende Vorgänge mit AEM durchführen. Es wird davon ausgegangen, dass das System und die Anwendung optimiert sind. Die Formel gilt jedoch nicht für erweiterte Funktionen wie MSM oder Assets (siehe die folgenden Abschnitte).

Siehe auch [Parallelisierung](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) und [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md).

### Hardware-Recommendations {#hardware-recommendations}

In der Regel können Sie dieselbe Hardware für Ihre Autorenumgebung verwenden, wie für Ihre Veröffentlichungsumgebung empfohlen wird. In der Regel ist der Website-Traffic auf Authoring-Systemen geringer, aber auch die Cache-Effizienz ist geringer. Entscheidend ist jedoch die Anzahl der parallel arbeitenden Autoren und die Art der Aktionen, die am System vorgenommen werden. Im Allgemeinen ist AEM Clustering (der Autorenumgebung) am effektivsten bei der Skalierung von Lesevorgängen, d. h. ein AEM Cluster skaliert gut mit Autoren, die grundlegende Bearbeitungsvorgänge durchführen.

Die Benchmarktests an Adobe wurden mit dem Betriebssystem Red Hat® 5.5 durchgeführt, das auf einer Hewlett-Packard ProLiant DL380 G5-Hardwareplattform mit folgender Konfiguration ausgeführt wird:

* Zwei Intel Xeon® X5450 Quadcore-Prozessoren mit 3,00 GHz
* 8 GB RAM
* Broadcom NetXtreme II BCM5708 Gigabit-Ethernet
* HP Smart Array RAID Controller, 256 MB Cache
* Zwei 146 GB 10.000-RPM SAS-Festplatten, die als RAID0-Streifen konfiguriert sind
* SPEC CINT2006 Rate Benchmark-Wert ist 110

AEM Instanzen wurden mit einer minimalen Heap-Größe von 256M ausgeführt, einer maximalen Heap-Größe von 1024M.

## Umgebungsspezifische Berechnungen veröffentlichen {#publish-environment-specific-calculations}

### Caching-Effizienz und -Traffic {#caching-efficiency-and-traffic}

Die Cache-Effizienz ist für die Geschwindigkeit der Website von entscheidender Bedeutung. Die folgende Tabelle zeigt, wie viele Seiten pro Sekunde ein optimiertes AEM mit einem Reverse-Proxy wie dem Dispatcher verarbeiten kann:

| Cache-Verhältnis | Seiten/Sek (Spitzenwert) | Millionen Seiten/Tag (Durchschnitt) |
|---|---|---|
| 100 % | 1000–2000 | 35–70 |
| 99 % | 910 | 32 |
| 95 % | 690 | 25 |
| 90 % | 520 | 18 |
| 60 % | 220 | 8 |
| 0 % | 100 | 3,5 |

>[!CAUTION]
>
>Haftungsausschluss: Die Zahlen basieren auf einer standardmäßigen Hardwarekonfiguration und können je nach verwendeter Hardware variieren.

Das Cache-Verhältnis ist der Prozentsatz der Seiten, die der Dispatcher zurückgeben kann, ohne auf AEM zugreifen zu müssen. 100 % bedeutet, dass der Dispatcher alle Anforderungen beantwortet, 0 % bedeutet, dass AEM jede Seite berechnet.

### Komplexität von Vorlagen und Anwendungen {#complexity-of-templates-and-applications}

Wenn Sie komplexe Vorlagen verwenden, benötigt AEM mehr Zeit zum Rendern einer Seite. Seiten aus dem Zwischenspeicher sind davon nicht betroffen, aber die Seitengröße ist für die gesamte Antwortzeit relevant. Das Rendern einer komplexen Seite kann sehr einfach zehnmal länger dauern als das Rendern einer einfachen Seite.

### Formel {#formula}

Mit der folgenden Formel können Sie eine Schätzung der Gesamtkomplexität Ihrer AEM-Lösung berechnen:

`complexity = applicationComplexity + ((1-cacheRatio) * templateComplexity)`

Aufgrund der Komplexität können Sie die Anzahl der Server (oder CPU-Kerne), die Sie für die Veröffentlichungsumgebung benötigen, wie folgt bestimmen:

`n = (traffic * complexity / 1000 ) * activations`

Die Variablen in der Gleichung lauten wie folgt:

<table>
 <tbody>
  <tr>
   <td>Traffic</td>
   <td>Der erwartete Spitzentraffic pro Sekunde. Sie können dies als die Anzahl der Seitentreffer pro Tag dividieren durch 35.000 schätzen.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Verwenden Sie 1 für eine einfache Anwendung, 2 für eine komplexe Anwendung oder einen Wert dazwischen:</p>
    <ul>
     <li>1 – eine vollständig anonyme, inhaltsorientierte Website</li>
     <li>1,1 – eine vollständig anonyme, inhaltsorientierte Website mit Client-seitiger/Target-Personalisierung</li>
     <li>1,5 – eine inhaltsorientierte Website mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitiger/Target-Personalisierung</li>
     <li>1,7 – für eine inhaltsorientierte Website mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitiger/Target-Personalisierung und einigen nutzergenerierten Inhalten</li>
     <li>2 - wo die gesamte Site angemeldet werden muss, mit umfangreichem Einsatz benutzergenerierter Inhalte und verschiedenen Personalisierungstechniken</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Der Prozentsatz der Seiten, die aus dem Dispatcher-Cache stammen. Verwenden Sie 1, wenn alle Seiten aus dem Cache kommen, oder 0, wenn jede Seite von AEM berechnet wird.</td>
  </tr>
  <tr>
   <td>templateComplexity</td>
   <td>Verwenden Sie einen Wert zwischen 1 und 10, um die Komplexität Ihrer Vorlagen anzugeben. Höhere Zahlen zeigen komplexere Vorlagen an, wobei der Wert 1 für Sites mit durchschnittlich 10 Komponenten pro Seite, der Wert 5 für einen Seitendurchschnitt von 40 Komponenten und 10 für einen Durchschnitt von über 100 Komponenten verwendet wird.</td>
  </tr>
  <tr>
   <td>activations</td>
   <td>Anzahl der durchschnittlichen Aktivierungen (Replikation von Seiten und Assets durchschnittlicher Größe von der Autoren- zur Veröffentlichungsebene) pro Stunde geteilt durch x, wobei x die Anzahl der Aktivierungen ist, die auf einem System ohne Leistungseinbußen auf andere vom System verarbeitete Aufgaben durchgeführt werden. Sie können einen pessimistischen Anfangswert wie x = 100 vordefinieren.<br /> </td>
  </tr>
 </tbody>
</table>

Wenn Sie eine komplexere Website haben, benötigen Sie auch leistungsfähigere Webserver, damit AEM eine Anfrage in akzeptabler Zeit beantworten kann.

* Komplexität unter 4:
   * 1024 MB JVM RAM&#42;
   * Geringe bis mittlere CPU-Leistung

* Komplexität von 4 bis 8:
   * 2048 MB JVM RAM&#42;
   * Mid to high-performance CPU

* Komplexität über 8:
   * 4096 MB JVM RAM&#42;
   * CPU mit hoher bis hoher Leistung

>[!NOTE]
>
>&#42; Reservieren Sie genügend RAM für Ihr Betriebssystem zusätzlich zu dem für Ihre JVM benötigten Arbeitsspeicher.

## Zusätzliche anwendungsspezifische Berechnungen {#additional-use-case-specific-calculations}

Berücksichtigen Sie neben der Berechnung für eine Standard-Webanwendung spezifische Faktoren für die folgenden Anwendungsfälle. Die berechneten Werte werden der Standardberechnung hinzugefügt.

### Asset-spezifische Überlegungen {#assets-specific-considerations}

Eine umfassende Verarbeitung digitaler Assets erfordert optimierte Hardware-Ressourcen. Die wichtigsten Faktoren sind die Bildgröße und der maximale Durchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset] so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

>[!NOTE]
>
Ein höherer Bilddurchsatz bedeutet, dass die Rechenressourcen mit den System-I/O und umgekehrt Schritt halten müssen. Wenn beispielsweise Workflows durch den Import von Bildern gestartet werden, kann das Hochladen vieler Bilder über WebDAV zu einem Rückstau der Workflows führen.
>
Die Verwendung separater Festplatten für TarPM, Datenspeicher und Suchindex kann dazu beitragen, das E/A-Verhalten des Systems zu optimieren (in der Regel ist es jedoch sinnvoll, den Suchindex lokal zu halten).

>[!NOTE]
>
Siehe auch [Asset-Leistungsleitfaden](/help/sites-deploying/assets-performance-sizing.md).

### Multi-Site-Manager {#multi-site-manager}

Der Ressourcenverbrauch bei der Verwendung AEM MSM in einer Authoring-Umgebung hängt stark von den jeweiligen Anwendungsfällen ab. Grundlegende Faktoren sind:

* Anzahl der Live Copies
* Häufigkeit der Rollouts
* Größe der Inhaltsstruktur für das Rollout
* Verbundene Funktionalität der Rollout-Aktionen

Das Testen des geplanten Anwendungsfalles mit einem repräsentativen Inhaltsauszug kann Ihnen helfen, den Ressourcenverbrauch besser zu verstehen. Wenn Sie die Ergebnisse mit dem geplanten Durchsatz hochrechnen, können Sie den zusätzlichen Ressourcenbedarf für das MSM in AEM einschätzen.

Berücksichtigen Sie auch Autoren, die parallel arbeiten. Sie erkennen Leistungsbeeinträchtigungen, wenn AEM MSM-Anwendungsfälle mehr Ressourcen verbrauchen als geplant.

### Überlegungen zur Größe von AEM Communities {#aem-communities-sizing-considerations}

AEM Sites, die Funktionen von AEM Communities (Community-Sites) enthalten, erleben ein hohes Maß an Interaktion von Seitenbesuchern (Mitgliedern) in der Veröffentlichungsumgebung.

Die Größenüberlegungen für eine Community-Site hängen von der erwarteten Interaktion der Community-Mitglieder ab und davon, ob eine optimale Leistung für Seiteninhalte von höherer Bedeutung ist.

Vom Benutzer generierte Inhalte (UGC) werden separat vom Seiteninhalt gespeichert. Während die AEM-Plattform einen Knotenspeicher verwendet, der Website-Inhalte von der Autoren- in die Veröffentlichungsumgebung repliziert, verwendet AEM Communities einen einzigen, gemeinsamen Speicher für UGC, der nie repliziert wird.

Für den UGC-Speicher ist es notwendig, einen Speicherressourcenanbieter (SRP = Storage Resource Provider) zu wählen, der die gewählte Bereitstellung beeinflusst.
Siehe

* [Speicherung von Community-Inhalten](/help/communities/working-with-srp.md)
* [Empfohlene Topologien für Communities](/help/communities/topologies.md)
