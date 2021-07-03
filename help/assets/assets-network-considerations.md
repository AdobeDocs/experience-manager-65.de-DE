---
title: Netzwerküberlegungen und Anforderungen
description: Erläutert Netzwerküberlegungen bei der Erstellung einer [!DNL Adobe Experience Manager Assets] Bereitstellung.
contentOwner: AG
role: Architect, Admin
feature: Entwickler-Tools
exl-id: 1313842c-18b1-4727-ba63-b454d0f5a2cc
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 72%

---

# [!DNL Assets] Netzwerküberlegungen {#assets-network-considerations}

Das Verständnis Ihres Netzwerks ist so wichtig wie das Verständnis von [!DNL Adobe Experience Manager Assets]. Das Netzwerk kann Uploads, Downloads und Benutzererlebnisse beeinflussen. Eine grafische Darstellung Ihrer Netzwerktopologie hilft bei der Erkennung von Engpässen und unzureichend optimierten Bereichen im Netzwerk, die Sie beseitigen bzw. korrigieren müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihre Netzwerkgrafik einbeziehen:

* Möglichkeit der Verbindung des Client-Geräts (z. B. Computer, Mobilgerät oder Tablet) mit dem Netzwerk.
* Topologie des Unternehmensnetzwerks.
* Uplink zum Internet vom Unternehmensnetzwerk und der [!DNL Experience Manager] Umgebung.
* Topologie der [!DNL Experience Manager]-Umgebung.
* Definieren Sie gleichzeitige Verbraucher der [!DNL Experience Manager]-Netzwerkschnittstelle.
* Definierte Workflows der [!DNL Experience Manager]-Implementierung.

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Beginnen Sie, indem Sie die Verbindungsmöglichkeit zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk grafisch darstellen. In dieser Phase ermitteln Sie gemeinsam genutzte Ressourcen wie WLAN-Verbindungen, bei denen mehrere Benutzer Zugriff auf denselben Punkt oder Ethernet-Switch haben, wodurch sie Assets hoch- bzw. herunterladen können.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Das Ermitteln und Verstehen von Engpässen in diesem Netzwerk ist für die [!DNL Assets] Planung und Änderung des Netzwerks wichtig.

Oben links im Diagramm sind drei Geräte dargestellt, die gemeinsam einen 48 MBit/s schnellen WLAN-Zugangspunkt nutzen. Wenn alle Geräte gleichzeitig hochladen, wird die WLAN-Netzbandbreite von den Geräten gemeinsam genutzt. Verglichen mit dem System als Ganzes kann ein Benutzer bei den drei Clients über diesen geteilten Kanal auf einen anderen Heckpunkt stoßen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzes zu messen, weil ein langsames Gerät die Leistung anderer Clients am Zugangspunkt beeinträchtigen kann. Wenn Sie beabsichtigen, WLAN für Asset-Interaktionen zu verwenden, führen Sie einen Geschwindigkeitstest mit mehreren Clients gleichzeitig durch, um die Leistung zu bewerten.

Unten links im Diagramm sind zwei Geräte dargestellt, die mit dem Unternehmensnetzwerk über unabhängige Kanäle verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 MBit/s und 100 MBit/s nutzen.

Der rechts gezeigte Computer hat einen begrenzten Upstream zum Unternehmensnetzwerk über eine VPN-Verbindung mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzer interagieren, kann ihr VPN-Uplink für die Aufgabe nicht ausreichend sein.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplinkgeschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Leitungen sind freigegebene Ressourcen. Wenn erwartet wird, dass der gemeinsam genutzte Switch 50 Clients verarbeitet, kann es sich möglicherweise um einen Engpass handeln. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink zum Internet vom Unternehmensnetzwerk und der [!DNL Experience Manager] Umgebung {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren des Internets und der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder umfangreiche Anbieterausfälle verringert werden kann. Im Allgemeinen ist eine Internetverbindung zuverlässig. Manchmal kann es allerdings zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet können andere Dienste die Bandbreite nutzen. Es ist wichtig, zu verstehen, wie viel Bandbreite für Assets bereitgestellt oder priorisiert werden kann. Wenn beispielsweise eine 1-Gbit/s-Verbindung bereits zu 80 % genutzt wird, können Sie für [!DNL Experience Manager Assets] nur maximal 20 % der Bandbreite zuweisen.

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Diese Geräteart kann Bandbreite mithilfe der Dienstgüte, der Bandbreitenbeschränkungen pro Benutzer oder der Bitratenbeschränkungen pro Host priorisieren. Diese wichtigen Checkpoints sollten untersucht werden, da sie sich erheblich auf das [!DNL Assets]-Benutzererlebnis auswirken können.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Hostgeschwindigkeit auf 10 MBit/s. Diese Beschränkung kann möglicherweise den Traffic zu einem einzelnen Host bis auf 10 MBit/s drosseln, obwohl der Uplink zum Internet auf 10 GBit/s ausgelegt ist.

Dies ist der kleinste Client-orientierte Choke-Point. Sie können jedoch eine Änderung vornehmen oder eine Zulassungsliste mit der für diese Firewall verantwortlichen Netzwerkbetriebsgruppe konfigurieren.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Je nach Größe der genutzten Assets reicht dies möglicherweise aus, um die Erwartungen der Benutzer zu erfüllen.

## Topologie der [!DNL Experience Manager]-Umgebung {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Die Erstellung der Topologie der [!DNL Experience Manager]-Umgebung erfordert detaillierte Kenntnisse der Systemkonfiguration und der Art und Weise, wie das Netzwerk in der Benutzerumgebung verbunden ist.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern, einen S3-Binärspeicher und Dynamic Media konfiguriert.

Der Dispatcher teilt seine 100 MBit/s-Verbindung mit zwei Entitäten, der Außenwelt und der [!DNL Experience Manager]-Implementierung. Für gleichzeitiges Hoch- und Herunterladen sollten Sie diesen Wert durch zwei teilen. Der zugeordnete externe Speicher verwendet eine separate Verbindung.

Die [!DNL Experience Manager]-Bereitstellung teilt die 1 Gbit/s-Verbindung mit mehreren Diensten. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Wenn Sie das Netzwerk vom Client-Gerät bis zur [!DNL Experience Manager]-Bereitstellung überprüfen, scheint der kleinste Schokoladepunkt die Firewall-Drosselklappe von 10 Mbit für Unternehmen zu sein. Sie können diese Werte in der in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager]-Implementierung {#defined-workflows-of-the-aem-deployment}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Um Prozesse zu optimieren, die mit der Asset-Aufnahme zu tun haben (insbesondere, wenn eine große Anzahl von Assets hochgeladen wird), sind die Asset-Workflows zu untersuchen, um mehr über ihre Konfiguration zu erfahren.

Bei der Untersuchung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die ausgelöst werden, wenn Assets/Metadaten geändert werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* XMP Metadaten lesen/schreiben
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Unter-Asset-Aufnahme/Seitenextraktion
* Überlappende Workflows

Es folgt ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
