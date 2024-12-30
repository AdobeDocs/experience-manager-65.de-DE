---
title: Hardware-Skalierungsrichtlinien
description: Diese Skalierungsrichtlinien bieten eine Annäherung an die Hardware-Erfordernisse, die für die Bereitstellung eines AEM-Projekts erforderlich sind.
exl-id: 5837ef4f-d4e0-49d7-a671-87d5547e0d98
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 658e1f6e07fb1219ba186137eb8403bf85383723
workflow-type: tm+mt
source-wordcount: '1351'
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

## Festplattenspeicher/Festplatte {#disk-space-hard-drive}

Der benötigte Speicherplatz hängt stark vom Volumen und vom Typ Ihrer Web-Anwendung ab. Die Berechnungen sollten Folgendes berücksichtigen:

* die Anzahl und Größe von Seiten, Assets und anderen im Repository gespeicherten Einheiten wie Workflows und Profilen.
* die geschätzte Häufigkeit von Inhaltsänderungen und damit die Erstellung von Inhaltsversionen.
* das Volumen der DAM-Asset-Ausgaben, die generiert werden sollen.
* das Gesamtwachstum aller Inhalte im Laufe der Zeit.

Der Speicherplatz wird während der Online- und Offline-Revisionsbereinigung kontinuierlich überwacht. Wenn der verfügbare Speicherplatz unter einen kritischen Wert fällt, wird der Prozess abgebrochen. Dieser kritische Wert beträgt 25 % des aktuell belegten Speicherplatzes des Repositorys und kann nicht konfiguriert werden. Adobe empfiehlt, eine Festplatte zu verwenden, die mindestens zwei- bis dreimal größer als das Repository ist, einschließlich erwartetem Wachstum.

### Virtualisierung {#virtualization}

AEM läuft gut in virtualisierten Umgebungen, aber es kann Faktoren wie CPU oder E/A geben, die nicht direkt mit physischer Hardware gleichgesetzt werden können. Allgemein empfehlenswert ist die Wahl einer höheren E/A-Geschwindigkeit, da dies in der Regel ein kritischer Faktor ist. Vergleichswerte für Ihre Umgebung sind erforderlich, um ein genaues Verständnis dafür zu erhalten, welche Ressourcen erforderlich sind.

### Parallelisierung von AEM-Instanzen {#parallelization-of-aem-instances}

**Ausfallsicherheit**

Eine ausfallsichere Website wird auf mindestens zwei getrennten Systemen bereitgestellt. Fällt ein System aus, kann ein anderes System übernehmen und so den Systemausfall kompensieren.

**Skalierbarkeit der Systemressourcen**

Während alle Systeme laufen, steht eine erhöhte Rechenleistung zur Verfügung. Diese zusätzliche Leistung wächst nicht unbedingt linear mit der Anzahl der Cluster-Knoten, da die Beziehung stark von der technischen Umgebung abhängt. Weitere Informationen finden Sie in der [Cluster-Dokumentation](/help/sites-deploying/recommended-deploys.md).

Die Abschätzung, wie viele Cluster-Knoten notwendig sind, basiert auf den grundlegenden Anforderungen und spezifischen Anwendungsfällen des jeweiligen Web-Projektes:

* Aus Sicht der Ausfallsicherheit ist es notwendig, für alle Umgebungen zu bestimmen, wie kritisch ein Ausfall ist und wie lange es dauert, bis ein Cluster-Knoten wiederhergestellt ist.
* Im Hinblick auf die Skalierbarkeit ist die Anzahl der Schreibvorgänge der wichtigste Faktor. Der Lastausgleich kann für Operationen eingerichtet werden, die nur auf das System zugreifen, um Lesevorgänge zu verarbeiten; siehe [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) für Details.

### Hardware-Empfehlungen {#hardware-recommendations}

Sie können für Ihre Autorenumgebung normalerweise die gleiche Hardware verwenden, die für Ihre Veröffentlichungsumgebung empfohlen wird. Normalerweise ist der Website-Traffic auf Autorensystemen geringer, aber auch die Cache-Effizienz ist geringer. Entscheidend ist jedoch die Anzahl der parallel arbeitenden Autoren und die Art der Aktionen, die am System vorgenommen werden. Im Allgemeinen ist AEM-Clustering (der Autorenumgebung) am effektivsten bei der Skalierung von Lesevorgängen. Mit anderen Worten: Ein AEM-Cluster lässt sich gut bei Autorinnen und Autoren skalieren, die grundlegende Bearbeitungsvorgänge ausführen.

## Zusätzliche anwendungsspezifische Berechnungen {#additional-use-case-specific-calculations}

Berücksichtigen Sie neben der Berechnung für eine standardmäßige Web-Anwendung spezifische Faktoren für die folgenden Anwendungsfälle. Die berechneten Werte werden der Standardberechnung hinzugefügt.

### Asset-spezifische Hinweise {#assets-specific-considerations}

Zur umfangreichen Verarbeitung digitaler Assets sind optimierte Hardware-Ressourcen erforderlich. Die wichtigsten Faktoren hierbei sind die Bildgröße und der Spitzendurchsatz verarbeiteter Bilder.

Weisen Sie mindestens 16 GB Heap zu und konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset] so, dass Rohbilder mit dem [Camera Raw-Paket](/help/assets/camera-raw.md) aufgenommen werden.

>[!NOTE]
>
>Ein höherer Datendurchsatz bedeutet, dass die Rechenressourcen mit der System-E/A Schritt halten müssen und umgekehrt. Wenn beispielsweise Workflows durch den Import von Bildern gestartet werden, kann das Hochladen vieler Bilder über WebDAV zu einem Rückstau von Workflows führen.
>
>Die Verwendung von separaten Festplatten für TarPM, Datenspeicher und Suchindex kann helfen, das E/A-Verhalten des Systems zu optimieren (in der Regel ist es jedoch sinnvoll, den Suchindex lokal zu halten).

>[!NOTE]
>
>Siehe auch [Handbuch zur Leistung von Assets](/help/sites-deploying/assets-performance-sizing.md).

### Multi-Site-Manager {#multi-site-manager}

Der Ressourcenverbrauch beim Einsatz von MSM in AEM in einer Authoring-Umgebung hängt stark von den jeweiligen Anwendungsfällen ab. Grundlegende Faktoren sind:

* Anzahl der Live Copies
* Häufigkeit der Rollouts
* Größe der Inhaltsstruktur, die bereitgestellt werden soll
* Verbundene Funktionalität der Rollout-Aktionen

Das Testen des geplanten Anwendungsfalles mit einem repräsentativen Inhaltsauszug kann Ihnen helfen, den Ressourcenverbrauch besser zu verstehen. Wenn Sie die Ergebnisse mit dem geplanten Durchsatz hochrechnen, können Sie den zusätzlichen Ressourcenbedarf für das MSM in AEM einschätzen.

Berücksichtigen Sie auch, dass Autorinnen und Autoren parallel arbeiten können. Diese nehmen Leistungsbeeinträchtigungen wahr, wenn AEM-MSM-Anwendungsfälle mehr Ressourcen verbrauchen als geplant.

### Hinweise zur Dimensionierung von AEM Communities {#aem-communities-sizing-considerations}

AEM-Sites, die Funktionen von AEM Communities (Community-Sites) enthalten, erleben ein hohes Maß an Interaktion von Seitenbesuchenden (Mitgliedern) in der Veröffentlichungsumgebung.

Die Größenüberlegungen für eine Community-Site hängen von der zu erwartenden Interaktion der Community-Mitglieder ab und davon, ob eine optimale Leistung für den Seiteninhalt von höherer Bedeutung ist.

Nutzergenerierte Inhalte (User-Generated Content, UGC) werden getrennt vom Seiteninhalt gespeichert. Während die AEM-Plattform einen Knotenspeicher verwendet, der Website-Inhalte von der Autoren- in die Veröffentlichungsumgebung repliziert, verwendet AEM Communities einen einzigen, gemeinsamen Speicher für UGC, der nie repliziert wird.

Für den UGC-Speicher ist es notwendig, einen Speicherressourcenanbieter (SRP = Storage Resource Provider) zu wählen, der die gewählte Bereitstellung beeinflusst.
Siehe

* [Speicherung von Community-Inhalten](/help/communities/working-with-srp.md)
* [Empfohlene Topologien für Communities](/help/communities/topologies.md)
