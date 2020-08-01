---
title: '[!DNL Assets] Netzwerküberlegungen und -anforderungen.'
description: Discusses network considerations when designing an [!DNL Adobe Experience Manager Assets] deployment.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 72%

---


# [!DNL Assets] Netzwerküberlegungen {#assets-network-considerations}

Das Verstehen Ihres Netzwerks ist ebenso wichtig wie das Verstehen [!DNL Adobe Experience Manager Assets]. Das Netzwerk kann Uploads, Downloads und Benutzererlebnisse beeinflussen. Eine grafische Darstellung Ihrer Netzwerktopologie hilft bei der Erkennung von Engpässen und unzureichend optimierten Bereichen im Netzwerk, die Sie beseitigen bzw. korrigieren müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihre Netzwerkgrafik einbeziehen:

* Möglichkeit der Verbindung des Client-Geräts (z. B. Computer, Mobilgerät oder Tablet) mit dem Netzwerk.
* Topologie des Unternehmensnetzwerks.
* Uplink to the internet from the corporate network and the [!DNL Experience Manager] environment.
* Topology of the [!DNL Experience Manager] environment.
* Define simultaneous consumers of the [!DNL Experience Manager] network interface.
* Definierte Workflows der [!DNL Experience Manager] Bereitstellung.

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Beginnen Sie, indem Sie die Verbindungsmöglichkeit zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk grafisch darstellen. In dieser Phase ermitteln Sie gemeinsam genutzte Ressourcen wie WLAN-Verbindungen, bei denen mehrere Benutzer Zugriff auf denselben Punkt oder Ethernet-Switch haben, wodurch sie Assets hoch- bzw. herunterladen können.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Identifying and understanding chokepoints on this network is important for [!DNL Assets] planning and to modify the network.

Oben links im Diagramm sind drei Geräte dargestellt, die gemeinsam einen 48 MBit/s schnellen WLAN-Zugangspunkt nutzen. Wenn alle Geräte gleichzeitig hochladen, wird die WLAN-Netzbandbreite von den Geräten gemeinsam genutzt. Verglichen mit dem System als Ganzes, kann ein Benutzer auf einen anderen Choke-Point für die drei Clients über diesen geteilten Kanal stoßen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzes zu messen, weil ein langsames Gerät die Leistung anderer Clients am Zugangspunkt beeinträchtigen kann. Wenn Sie beabsichtigen, WLAN für Asset-Interaktionen zu verwenden, führen Sie einen Geschwindigkeitstest mit mehreren Clients gleichzeitig durch, um die Leistung zu bewerten.

Unten links im Diagramm sind zwei Geräte dargestellt, die mit dem Unternehmensnetzwerk über unabhängige Kanäle verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 MBit/s und 100 MBit/s nutzen.

Der rechts gezeigte Computer hat einen begrenzten Upstream zum Unternehmensnetzwerk über eine VPN-Verbindung mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzer interagieren, kann ihr VPN-Uplink für die Aufgabe nicht ausreichend sein.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplinkgeschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Leitungen sind freigegebene Ressourcen. Wenn erwartet wird, dass der freigegebene Switch 50 Clients verarbeitet, kann es sich dabei möglicherweise um einen Choke-Point handeln. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink to the internet from the corporate network and [!DNL Experience Manager] environment {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren des Internets und der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder umfangreiche Anbieterausfälle verringert werden kann. Im Allgemeinen ist eine Internetverbindung zuverlässig. Manchmal kann es allerdings zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet können andere Dienste die Bandbreite nutzen. Es ist wichtig, zu verstehen, wie viel Bandbreite für Assets bereitgestellt oder priorisiert werden kann. For example, if a 1 Gbps link is already at 80% utilization, you can only allocate a maximum of 20% of the bandwidth for [!DNL Experience Manager Assets].

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Diese Geräteart kann Bandbreite mithilfe der Dienstgüte, der Bandbreitenbeschränkungen pro Benutzer oder der Bitratenbeschränkungen pro Host priorisieren. These are important chokepoints to examine as they can significantly impact [!DNL Assets] user experience.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Hostgeschwindigkeit auf 10 MBit/s. Diese Beschränkung kann möglicherweise den Traffic zu einem einzelnen Host bis auf 10 MBit/s drosseln, obwohl der Uplink zum Internet auf 10 GBit/s ausgelegt ist.

Dies ist der kleinste kundenorientierte Choke-Point. Sie können jedoch eine Änderung oder Konfiguration einer Zulassungsliste mit der für diese Firewall zuständigen Netzwerkbetriebengruppe vornehmen.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Je nach Größe der genutzten Assets reicht dies möglicherweise aus, um die Erwartungen der Benutzer zu erfüllen.

## Topology of the [!DNL Experience Manager] environment {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Designing the topology of the [!DNL Experience Manager] environment requires detailed knowledge of the system configuration and how the network is connected within the user environment.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern, einen S3-Binärspeicher und konfigurierte Dynamic Media.

The dispatcher shares it&#39;s 100Mbps connection with two entities, the outside world and the [!DNL Experience Manager] deployment. Für gleichzeitiges Hoch- und Herunterladen sollten Sie diesen Wert durch zwei teilen. Der zugeordnete externe Speicher verwendet eine separate Verbindung.

The [!DNL Experience Manager] deployment shares it&#39;s 1Gbps connection with multiple services. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Reviewing the network from the client device to the [!DNL Experience Manager] deployment, the smallest choke-point appears to be the 10 Mbit enterprise firewall throttle. Sie können diese Werte in der in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager] Bereitstellung {#defined-workflows-of-the-aem-deployment}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Um Prozesse zu optimieren, die mit der Asset-Aufnahme zu tun haben (insbesondere, wenn eine große Anzahl von Assets hochgeladen wird), sind die Asset-Workflows zu untersuchen, um mehr über ihre Konfiguration zu erfahren.

Bei der Untersuchung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die ausgelöst werden, wenn Assets/Metadaten geändert werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* XMP Metadaten lesen/schreiben-back
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Unter-Asset-Aufnahme/Seitenextraktion
* Überlappende Workflows

Es folgt ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
