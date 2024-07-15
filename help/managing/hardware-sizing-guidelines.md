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
feature: Compliance
role: Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '2833'
ht-degree: 100%

---

# Hardware-Skalierungsrichtlinien{#hardware-sizing-guidelines}

Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Bereitstellung eines AEM-Projekts erforderlich sind. Die geschätzte Skalierung hängt von der Architektur des Projekts, der Komplexität der Lösung, dem erwarteten Traffic und den Projektanforderungen ab. Dieser Leitfaden hilft Ihnen, den Hardwarebedarf für eine bestimmte Lösung zu ermitteln oder eine obere und untere Schätzung für die Hardwareanforderungen zu finden.

Grundlegende Faktoren sind (in dieser Reihenfolge):

* **Netzwerkgeschwindigkeit**

   * Netzwerklatenz
   * Verfügbare Bandbreite

* **Rechengeschwindigkeit**

   * Caching-Effizienz
   * Erwarteter Traffic
   * Komplexität von Vorlagen, Anwendungen und Komponenten
   * Gleichzeitig arbeitende Autorinnen und Autoren
   * Komplexität der Authoring-Vorgangs (einfache Inhaltsbearbeitung, MSM-Rollout usw.)

* **E/A-Performance**

   * Performance und Effizienz der Datei- oder Datenbankspeicherung

* **Festplatte**

   * mindestens zwei- oder dreimal größer als die Größe des Repositorys

* **Arbeitsspeicher**

   * Größe der Website (Anzahl der Inhaltsobjekte, Seiten und Benutzenden)
   * Anzahl der gleichzeitig aktiven Benutzenden/Sitzungen

## Architektur {#architecture}

Ein typisches AEM-Setup besteht aus einer Autoren- und einer Veröffentlichungsumgebung. Diese Umgebungen haben unterschiedliche Anforderungen bezüglich der zugrunde liegenden Hardware-Größe und Systemkonfiguration. Detaillierte Überlegungen zu beiden Umgebungen finden sich in den Abschnitten [Autorenumgebung](/help/managing/hardware-sizing-guidelines.md#author-environment-specific-calculations) und [Veröffentlichungsumgebung](/help/managing/hardware-sizing-guidelines.md#publish-environment-specific-calculations).

In einem typischen Projekt-Setup stehen Ihnen mehrere Umgebungen zur Verfügung, in denen Sie Projektphasen inszenieren können:

* **Entwicklungsumgebung** Um neue Funktionen zu entwickeln oder wesentliche Änderungen vorzunehmen. Am besten arbeitet man mit einer Entwicklungsumgebung pro entwickelnder Person (lokale Installationen auf den jeweiligen persönlichen Systemen).

* **Autoren-Testumgebung**
Um Änderungen zu verifizieren. Die Anzahl der Testumgebungen kann je nach Projektanforderungen variieren (z. B. getrennt für QA, Integrationstests oder Benutzerakzeptanztests).

* **Veröffentlichungs-Testumgebung** Hauptsächlich zum Testen von Anwendungsfällen der Zusammenarbeit in sozialen Netzwerken und/oder der Interaktion zwischen Autor und mehreren Veröffentlichungsinstanzen.

* **Autoren-Bearbeitungsumgebung** Für Autoren zum Bearbeiten von Inhalten

* **Veröffentlichungs-Bearbeitungsumgebung** Um veröffentlichte Inhalte bereitzustellen.

Die Umgebungen können zudem variieren, von einem Single-Server-System mit AEM und einem Anwendungs-Server bis hin zu einem hochskalierten Satz von Multi-Server- und Multi-CPU-Clustern. Adobe empfiehlt, je einen separaten Computer für ein Produktionssystem zu verwenden und auf diesen Rechnern keine anderen Anwendungen auszuführen.

## Allgemeine Hinweise zur Hardware-Skalierung {#generic-hardware-sizing-considerations}

Die folgenden Abschnitte enthalten Hinweise zur Berechnung der Hardware-Anforderungen unter Berücksichtigung verschiedener Aspekte. Für große Systeme empfiehlt Adobe, einen einfachen Satz von internen Benchmark-Tests an einer Referenzkonfiguration durchzuführen.

Die Performance-Optimierung ist eine grundlegende Aufgabe, die durchgeführt werden muss, bevor ein Benchmarking für ein bestimmtes Projekt durchgeführt werden kann. Beachten Sie die Hinweise in der [Dokumentation zur Leistungsoptimierung](/help/sites-deploying/configuring-performance.md), bevor Sie Benchmark-Tests durchführen und deren Ergebnisse zur Berechnung der Hardware-Skalierung nutzen.

Die Hardware-Skalierung für fortgeschrittene Anwendungsfälle sollte auf einer detaillierten Leistungsbewertung des Projekts basieren. Zu den Merkmalen fortgeschrittener Anwendungsfälle, die außergewöhnliche Hardware-Ressourcen erfordern, zählen Kombinationen folgender Aspekte:

* hohe Payload/Durchsatzleistung
* umfangreicher Einsatz von benutzerdefiniertem Code, eigenen Workflows oder Software-Bibliotheken von Drittanbietern
* Integration in nicht unterstützte externe Systeme

### Festplattenspeicher/Festplatte {#disk-space-hard-drive}

Der benötigte Speicherplatz hängt stark vom Volumen und vom Typ Ihrer Web-Anwendung ab. Die Berechnungen sollten Folgendes berücksichtigen:

* die Anzahl und Größe von Seiten, Assets und anderen im Repository gespeicherten Einheiten wie Workflows und Profilen.
* die geschätzte Häufigkeit von Inhaltsänderungen und damit die Erstellung von Inhaltsversionen.
* das Volumen der DAM-Asset-Ausgaben, die generiert werden sollen.
* das Gesamtwachstum aller Inhalte im Laufe der Zeit.

Der Speicherplatz wird während der Online- und Offline-Revisionsbereinigung kontinuierlich überwacht. Wenn der verfügbare Speicherplatz unter einen kritischen Wert fällt, wird der Prozess abgebrochen. Dieser kritische Wert beträgt 25 % des aktuell belegten Speicherplatzes des Repositorys und kann nicht konfiguriert werden. Adobe empfiehlt, eine Festplatte zu verwenden, die mindestens zwei- bis dreimal größer als das Repository ist, einschließlich erwartetem Wachstum.

Für die Datenredundanz sind redundante Arrays unabhängiger Festplatten (RAID, z. B. RAID10) eine gute Wahl.

>[!NOTE]
>
>Das temporäre Verzeichnis einer Produktionsinstanz sollte mindestens 6 GB freien Speicherplatz vorhalten.

#### Virtualisierung {#virtualization}

AEM läuft gut in virtualisierten Umgebungen, aber es kann Faktoren wie CPU oder E/A geben, die nicht direkt mit physischer Hardware gleichgesetzt werden können. Allgemein empfehlenswert ist die Wahl einer höheren E/A-Geschwindigkeit, da dies in der Regel ein kritischer Faktor ist. Vergleichswerte für Ihre Umgebung sind erforderlich, um ein genaues Verständnis dafür zu erhalten, welche Ressourcen erforderlich sind.

#### Parallelisierung von AEM-Instanzen {#parallelization-of-aem-instances}

**Ausfallsicherheit**

Eine ausfallsichere Website wird auf mindestens zwei getrennten Systemen bereitgestellt. Fällt ein System aus, kann ein anderes System übernehmen und so den Systemausfall kompensieren.

**Skalierbarkeit der Systemressourcen**

Während alle Systeme laufen, steht eine erhöhte Rechenleistung zur Verfügung. Diese zusätzliche Leistung wächst nicht unbedingt linear mit der Anzahl der Cluster-Knoten, da die Beziehung stark von der technischen Umgebung abhängt. Weitere Informationen finden Sie in der [Cluster-Dokumentation](/help/sites-deploying/recommended-deploys.md).

Die Abschätzung, wie viele Cluster-Knoten notwendig sind, basiert auf den grundlegenden Anforderungen und spezifischen Anwendungsfällen des jeweiligen Web-Projektes:

* Aus Sicht der Ausfallsicherheit ist es notwendig, für alle Umgebungen zu bestimmen, wie kritisch ein Ausfall ist und wie lange es dauert, bis ein Cluster-Knoten wiederhergestellt ist.
* Für den Aspekt der Skalierbarkeit ist die Anzahl der Schreiboperationen grundsätzlich der wichtigste Faktor; siehe [Paralleles Arbeiten von Autoren](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel) für die Autorenumgebung, und [Zusammenarbeit in sozialen Netzwerken](/help/managing/hardware-sizing-guidelines.md#socialcollaborationspecificconsiderations) für die Veröffentlichungsumgebung. Der Lastausgleich kann für Operationen eingerichtet werden, die nur auf das System zugreifen, um Lesevorgänge zu verarbeiten; siehe [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) für Details.

## Spezielle Berechnungen für die Autorenumgebung {#author-environment-specific-calculations}

Für Benchmarking-Zwecke hat Adobe einige Benchmark-Tests für eigenständige Autoreninstanzen entwickelt.

* **Benchmarktest 1** Berechnung des maximalen Durchsatzes eines Lastprofils, bei dem Benutzer eine einfache Erstellung einer Seite auf einer Grundlast von 300 vorhandenen Seiten durchführen, die alle von ähnlicher Art sind. Die Schritte bestanden darin, sich bei der Website anzumelden, eine Seite mit einer SWF und Bild/Text zu erstellen, eine Tag-Cloud hinzuzufügen und die Seite zu aktivieren.

   * **Ergebnis** 
Der maximale Durchsatz für eine einfache Seitenerstellung wie oben beschrieben – als eine Transaktion betrachtet – betrug 1730 Transaktionen/Stunde.

* **Benchmarktest 2** Berechnung des maximalen Durchsatzes, wenn das Lastprofil eine Mischung aus frischer Seitenerstellung (10 %), Änderung einer bestehenden Seite (80 %) und anschließender Änderung einer Seite in Folge (10 %) aufweist. Die Komplexität der Seiten bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Die Übung wurde erneut auf einer Grundlast von 300 Seiten mit der gleichen Komplexität wie in Benchmark-Test 1 durchgeführt.

   * **Ergebnis** Der maximale Durchsatz für ein solches Mischbetriebsszenario lag bei 3252 Transaktionen pro Stunde.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der Ansatz zur Messung des Durchsatzes stellt sicher, dass ein fester Anteil jeder Art von Transaktion in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass der Durchsatz je nach Betriebsart variiert. Verwenden Sie die Aktivitäten in Ihrer Umgebung als Grundlage für die Dimensionierung Ihres Systems. Sie erhalten einen besseren Durchsatz mit weniger intensiven Aktionen wie z. B. Modifizieren (was auch häufiger vorkommt).

### Caching {#caching}

In der Autorenumgebung ist die Effizienz der Zwischenspeicherung in der Regel deutlich geringer, da Änderungen an der Website häufiger auftreten und auch die Inhalte sehr interaktiv und personalisiert sind. Mit dem Dispatcher können Sie AEM-Bibliotheken, JavaScripts, CSS-Dateien und Layout-Bilder zwischenspeichern. Dies beschleunigt manche Aspekte des Bearbeitungsprozesses. Die Konfiguration des Webservers, um zusätzliche Header für das Browser-Caching auf diesen Ressourcen zu setzen, reduziert die Anzahl der HTTP-Anfragen und verbessert somit die Reaktionsfähigkeit des Systems, wie sie von den Autorinnen und Autoren erfahren wird.

### Paralleles Arbeiten von Autorinnen und Autoren {#authors-working-in-parallel}

In der Autorenumgebung sind die Anzahl der parallel arbeitenden Autorinnen und Autoren und die Belastung des Systems durch ihre Interaktionen die wichtigsten limitierenden Faktoren. Adobe empfiehlt Ihnen daher, Ihr System auf Basis des gemeinsamen Datendurchsatzes zu skalieren.

Für solche Szenarien hat Adobe Benchmark-Tests auf einem Cluster mit zwei Knoten durchgeführt, die von Autoreninstanzen genutzt werden, welche nichts gemeinsam nutzen.

* **Benchmarktest 1a**
Mit einem aktiv-aktiven Shared-Nothing-Cluster von 2 Autoreninstanzen berechnen Sie den maximalen Durchsatz mit einem Lastprofil, bei dem Benutzer eine einfache Seitenübung auf einer Grundlast von 300 vorhandenen Seiten durchführen, die alle von ähnlicher Art sind.

   * **Ergebnis** 
Der maximale Durchsatz für eine einfache Seitenerstellung wie oben beschrieben – als eine Transaktion betrachtet – betrug 2016 Transaktionen/Stunde.  Dies ist eine Steigerung von ca. 16 % im Vergleich zu einer eigenständigen Autoreninstanz für den gleichen Benchmarktest.

* **Benchmarktest 2b**
Bei einem aktiv-aktiven Shared-Nothing-Cluster von 2 Autoreninstanzen wird der maximale Durchsatz berechnet, wenn das Lastprofil einen Mix aus frischer Seitenerstellung (10 %), Änderung einer bestehenden Seite (80 %) und Erstellung und Änderung einer Seite in Folge (10 %) aufweist. Die Komplexität der Seite bleibt gleich wie im Profil des Benchmarktests 1. Die grundlegende Änderung der Seite erfolgt durch Hinzufügen eines Bildes und Ändern des Textinhalts. Auch hier wurde die Übung auf einer Grundlast von 300 Seiten mit derselben Komplexität wie im Benchmark-Test 1 durchgeführt.

   * **Ergebnis** Der maximale Durchsatz für ein solches Mischbetriebsszenario lag bei 6288 Transaktionen/Stunde. Dies ist eine Steigerung von ca. 93 % im Vergleich zu einer eigenständigen Autoreninstanz für den gleichen Benchmark-Test.

>[!NOTE]
>
>Die Durchsatzrate unterscheidet nicht zwischen Bewegungsarten innerhalb eines Lastprofils. Der Ansatz zur Messung des Durchsatzes stellt sicher, dass ein fester Anteil jeder Art von Transaktion in die Arbeitslast einbezogen wird.

Die beiden oben genannten Tests zeigen deutlich, dass AEM für Autoren, die grundlegende Bearbeitungen mit AEM durchführen, gut skalierbar ist. Im Allgemeinen ist AEM am effektivsten bei der Skalierung von Lesevorgängen.

Auf einer typischen Website geschieht das meiste Authoring während der Projektphase. Nach dem Start der Website sinkt die Anzahl der parallel arbeitenden Autorinnen und Autoren in der Regel auf einen niedrigeren Durchschnitt (im Regelbetrieb).

Sie können die Anzahl der Computer (oder CPUs), die für die Autorenumgebung benötigt werden, wie folgt berechnen:

`n = numberOfParallelAuthors / 30`

Diese Formel kann als allgemeine Richtlinie für die Skalierung von CPUs dienen, wenn Autorinnen und Autoren grundlegende Vorgänge mit AEM ausführen. Es wird davon ausgegangen, dass das System und die Anwendung optimiert sind. Die Formel gilt jedoch nicht für erweiterte Funktionen wie MSM oder Assets (siehe unten).

Siehe auch [Parallelisierung](/help/managing/hardware-sizing-guidelines.md#parallelization-of-aem-instances) und [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md).

### Hardware-Empfehlungen {#hardware-recommendations}

Sie können für Ihre Autorenumgebung normalerweise die gleiche Hardware verwenden, die für Ihre Veröffentlichungsumgebung empfohlen wird. Normalerweise ist der Website-Traffic auf Autorensystemen geringer, aber auch die Cache-Effizienz ist geringer. Entscheidend ist jedoch die Anzahl der parallel arbeitenden Autoren und die Art der Aktionen, die am System vorgenommen werden. Im Allgemeinen ist AEM-Clustering (der Autorenumgebung) am effektivsten bei der Skalierung von Lesevorgängen. Mit anderen Worten: Ein AEM-Cluster lässt sich gut bei Autorinnen und Autoren skalieren, die grundlegende Bearbeitungsvorgänge ausführen.

Die Benchmark-Tests bei Adobe wurden mit dem Betriebssystem RedHat® 5.5 durchgeführt, das auf einer Hardware-Plattform Hewlett-Packard ProLiant DL380 G5 mit folgender Konfiguration lief:

* Zwei Quad Core Intel Xeon® X5450 CPUs mit 3,00 GHz
* 8 GB RAM
* Broadcom NetXtreme II BCM5708 Gigabit Ethernet
* HP Smart Array RAID-Controller, 256 MB Cache
* Zwei SAS-Festplatten mit je 146 GB und 10.000 RPM, die als RAID0-Stripe-Set konfiguriert sind
* SPEC CINT2006 Raten-Benchmark-Score ist 110

AEM-Instanzen liefen mit einer minimalen Heap-Größe von 256 M und einer maximalen Heap-Größe von 1024 M.

## Veröffentlichung von umgebungsspezifischen Berechnungen {#publish-environment-specific-calculations}

### Caching-Effizienz und Traffic {#caching-efficiency-and-traffic}

Die Caching-Effizienz ist für die Geschwindigkeit einer Website von entscheidender Bedeutung. Die folgende Tabelle zeigt, wie viele Seiten pro Sekunde ein optimiertes AEM-System mit einem Reverse-Proxy wie dem Dispatcher verarbeiten kann:

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
>Anmerkung: Die Zahlen basieren auf einer standardmäßigen Hardware-Konfiguration und können je nach verwendeter Hardware variieren.

Die Cache-Quote gibt den Prozentsatz an Seiten an, die der Dispatcher zurückgeben kann, ohne auf AEM zuzugreifen. 100 % bedeutet, dass der Dispatcher alle Anfragen beantwortet. 0 % bedeutet, dass AEM jede einzelne Seite berechnet. 

### Komplexität von Vorlagen und Anwendungen {#complexity-of-templates-and-applications}

Wenn Sie komplexe Vorlagen verwenden, benötigt AEM mehr Zeit, um eine Seite zu rendern. Seiten aus dem Zwischenspeicher sind davon nicht betroffen, aber die Seitengröße ist für die gesamte Antwortzeit relevant. Das Rendern einer komplexen Seite kann ohne Weiteres zehnmal länger dauern als das Rendern einer einfachen Seite.

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
   <td>Der erwartete Spitzentraffic pro Sekunde. Man kann dies als die Anzahl der Seitenaufrufe pro Tag, geteilt durch 35.000, schätzen.</td>
  </tr>
  <tr>
   <td>applicationComplexity</td>
   <td><p>Verwenden Sie 1 für eine einfache Anwendung, 2 für eine komplexe Anwendung oder einen Wert dazwischen:</p>
    <ul>
     <li>1 – eine vollständig anonyme, inhaltsorientierte Website</li>
     <li>1,1 – eine vollständig anonyme, inhaltsorientierte Website mit Client-seitiger/Target-Personalisierung</li>
     <li>1,5 – eine inhaltsorientierte Website mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitiger/Target-Personalisierung</li>
     <li>1,7 – für eine inhaltsorientierte Website mit sowohl anonymen als auch angemeldeten Abschnitten, Client-seitiger/Target-Personalisierung und einigen nutzergenerierten Inhalten</li>
     <li>2 – Anmeldung für die gesamte Site erforderlich, mit umfangreichem Einsatz nutzergenerierter Inhalte und verschiedenen Personalisierungstechniken</li>
    </ul> </td>
  </tr>
  <tr>
   <td>cacheRatio</td>
   <td>Der Prozentsatz der Seiten, die aus dem Dispatcher-Cache stammen. Verwenden Sie 1, wenn alle Seiten aus dem Cache kommen, oder 0, wenn jede Seite von AEM berechnet wird.</td>
  </tr>
  <tr>
   <td>templateComplexity</td>
   <td>Verwenden Sie einen Wert von 1 bis 10, um die Komplexität Ihrer Vorlagen anzugeben. Höhere Zahlen zeigen komplexere Vorlagen an, wobei der Wert 1 für Sites mit durchschnittlich 10 Komponenten pro Seite, der Wert 5 für einen Seitendurchschnitt von 40 Komponenten und 10 für einen Durchschnitt von über 100 Komponenten verwendet wird.</td>
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
   * Niedrige bis mittlere CPU-Leistung

* Komplexität von 4 bis 8:
   * 2048 MB JVM RAM&#42;
   * Mittlere bis hohe CPU-Leistung

* Komplexität über 8:
   * 4096 MB JVM RAM&#42;
   * Hohe bis extrem hohe CPU-Leistung

>[!NOTE]
>
>&#42; Reservieren Sie genügend RAM für Ihr Betriebssystem zusätzlich zu dem für Ihre JVM benötigten Arbeitsspeicher.

## Zusätzliche anwendungsspezifische Berechnungen {#additional-use-case-specific-calculations}

Berücksichtigen Sie neben der Berechnung für eine standardmäßige Web-Anwendung spezifische Faktoren für die folgenden Anwendungsfälle. Die berechneten Werte werden der Standardberechnung hinzugefügt.

### Asset-spezifische Hinweise {#assets-specific-considerations}

Zur umfangreichen Verarbeitung digitaler Assets sind optimierte Hardware-Ressourcen erforderlich. Die wichtigsten Faktoren hierbei sind die Bildgröße und der Spitzendurchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset] so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

>[!NOTE]
>
Ein höherer Datendurchsatz bedeutet, dass die Rechenressourcen mit der System-E/A Schritt halten müssen und umgekehrt. Wenn beispielsweise Workflows durch den Import von Bildern gestartet werden, kann das Hochladen vieler Bilder über WebDAV zu einem Rückstau von Workflows führen.
>
Die Verwendung von separaten Festplatten für TarPM, Datenspeicher und Suchindex kann helfen, das E/A-Verhalten des Systems zu optimieren (in der Regel ist es jedoch sinnvoll, den Suchindex lokal zu halten).

>[!NOTE]
>
Siehe auch [Handbuch zur Leistung von Assets](/help/sites-deploying/assets-performance-sizing.md).

### Multi-Site-Manager {#multi-site-manager}

Der Ressourcenverbrauch beim Einsatz von MSM in AEM in einer Authoring-Umgebung hängt stark von den jeweiligen Anwendungsfällen ab. Grundlegende Faktoren sind:

* Anzahl der Live Copies
* Häufigkeit der Rollouts
* Größe der Inhaltsstruktur, die bereitgestellt werden soll
* Verbundene Funktionalität der Rollout-Aktionen

Das Testen des geplanten Anwendungsfalles mit einem repräsentativen Inhaltsauszug kann Ihnen helfen, den Ressourcenverbrauch besser zu verstehen. Wenn Sie die Ergebnisse mit dem geplanten Durchsatz hochrechnen, können Sie den zusätzlichen Ressourcenbedarf für das MSM in AEM einschätzen.

Berücksichtigen Sie auch, dass Autorinnen und Autoren parallel arbeiten können. Diese nehmen Leistungsbeeinträchtigungen wahr, wenn AEM-MSM-Anwendungsfälle mehr Ressourcen verbrauchen als geplant.

### Hinweise zur Dimensionierung von AEM Communities {#aem-communities-sizing-considerations}

AEM Sites, die Funktionen von AEM Communities (Community-Sites) enthalten, erleben ein hohes Maß an Interaktion von Seitenbesuchern (Mitgliedern) in der Veröffentlichungsumgebung.

Die Größenüberlegungen für eine Community-Site hängen von der zu erwartenden Interaktion der Community-Mitglieder ab und davon, ob eine optimale Leistung für den Seiteninhalt von höherer Bedeutung ist.

Nutzergenerierte Inhalte (User-Generated Content, UGC) werden getrennt vom Seiteninhalt gespeichert. Während die AEM-Plattform einen Knotenspeicher verwendet, der Website-Inhalte von der Autoren- in die Veröffentlichungsumgebung repliziert, verwendet AEM Communities einen einzigen, gemeinsamen Speicher für UGC, der nie repliziert wird.

Für den UGC-Speicher ist es notwendig, einen Speicherressourcenanbieter (SRP = Storage Resource Provider) zu wählen, der die gewählte Bereitstellung beeinflusst.
Siehe

* [Speicherung von Community-Inhalten](/help/communities/working-with-srp.md)
* [Empfohlene Topologien für Communities](/help/communities/topologies.md)
