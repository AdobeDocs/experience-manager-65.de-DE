---
title: Überlegungen und Anforderungen zum Netzwerk
description: Erörtert Überlegungen zum Netzwerk bei der Planung einer Bereitstellung von [!DNL Adobe Experience Manager Assets] .
contentOwner: AG
role: Architect, Admin
feature: Developer Tools
exl-id: 1313842c-18b1-4727-ba63-b454d0f5a2cc
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 51%

---

# Überlegungen zum Netzwerk für [!DNL Assets] {#assets-network-considerations}

Sie müssen Ihr Netzwerk ebenso gut verstehen wie [!DNL Adobe Experience Manager Assets]. Das Netzwerk kann sich auf das Upload-, Download- und Benutzererlebnis auswirken. Die Abbildung Ihrer Netzwerktopologie hilft dabei, Engpässe und unteroptimierte Bereiche im Netzwerk zu identifizieren, die Sie beheben müssen, um die Netzwerkleistung und das Benutzererlebnis zu verbessern.

Stellen Sie sicher, dass Sie Folgendes in Ihr Netzwerkdiagramm aufnehmen:

* Verbindung vom Client-Gerät (z. B. Computer, Mobilgerät und Tablet) zum Netzwerk.
* Topologie des Unternehmensnetzwerks.
* Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung.
* Topologie der [!DNL Experience Manager]-Umgebung.
* Definition gleichzeitiger Verbraucher und Verbraucherinnen der [!DNL Experience Manager]-Netzwerkschnittstelle.
* Definierte Workflows der [!DNL Experience Manager]-Bereitstellung.

## Möglichkeit der Verbindung des Client-Geräts mit dem Unternehmensnetzwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Erstellen Sie zunächst eine Grafik der Verbindung zwischen den einzelnen Client-Geräten und dem Unternehmensnetzwerk. Identifizieren Sie in dieser Phase freigegebene Ressourcen, z. B. WLAN-Verbindungen, bei denen mehrere Benutzer auf denselben Punkt oder Ethernet-Switch zugreifen, um Assets hochzuladen und herunterzuladen.

![chlimage_1-353](assets/chlimage_1-353.png)

Client-Geräte stellen auf verschiedene Arten eine Verbindung mit einem Unternehmensnetzwerk her, z. B. über freigegebenes WLAN, Ethernet mit gemeinsam genutztem Switch und VPN. Das Erkennen und Verstehen von Engpässen in diesem Netzwerk ist für die Planung von [!DNL Assets] und für die Netzwerkmodifizierung unerlässlich.

Oben links im Diagramm werden drei Geräte als WiFi-Zugangspunkt mit 48 MBit/s dargestellt. Wenn alle Geräte gleichzeitig hochgeladen werden, wird die WiFi-Netzwerkbandbreite von den Geräten gemeinsam genutzt. Im Vergleich zu dem System als Ganzem können Benutzende auf unterschiedliche Engpässe stoßen, die daraus resultieren, dass die drei Clients diesen Kanal gemeinsam nutzen.

Es ist eine Herausforderung, die wahre Geschwindigkeit eines WLAN-Netzwerks zu messen, da ein langsames Gerät andere Clients auf den Zugangspunkt beeinflussen kann. Wenn Sie beabsichtigen, WLAN für Asset-Interaktionen zu verwenden, führen Sie einen Geschwindigkeitstest von mehreren Clients gleichzeitig durch, um den Durchsatz zu bewerten.

Unten links im Diagramm sind zwei Geräte dargestellt, die über unabhängige Kanäle mit dem Unternehmensnetzwerk verbunden sind. Daher kann jedes Gerät eine Mindestgeschwindigkeit von 10 Mbit/s und 100 Mbit/s nutzen.

Der rechts angezeigte Computer verfügt über eine begrenzte Upstream-Funktionalität über einen VPN mit einer Geschwindigkeit von 1 MBit/s. Das Benutzererlebnis bei der 1 MBit/s schnellen Verbindung unterscheidet sich erheblich vom Benutzererlebnis bei der 1 GBit/s schnellen Verbindung. Je nach Größe der Assets, mit denen Benutzer interagieren, kann ihr VPN-Uplink für die Aufgabe unzureichend sein.

## Topologie des Unternehmensnetzwerks  {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Das Diagramm zeigt höhere Uplink-Geschwindigkeiten innerhalb des Unternehmensnetzwerks, als im Allgemeinen üblich sind. Diese Pipe sind gemeinsame Ressourcen. Wenn erwartet wird, dass ein freigegebener Switch die Vorgänge von 50 Clients abwickelt, kann es hier möglicherweise zu einem Engpass kommen. Im anfangs gezeigten Diagramm nutzen nur zwei Computer die betreffende Verbindung.

## Uplink zum Internet vom Unternehmensnetzwerk und von der [!DNL Experience Manager]-Umgebung {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Es ist wichtig, unbekannte Faktoren im Internet und in der VPC-Verbindung zu berücksichtigen, da die Bandbreite im Internet durch Spitzenlasten oder Ausfälle bei großen Anbietern beeinträchtigt werden kann. Im Allgemeinen ist die Internetverbindung zuverlässig. Manchmal kann es jedoch zu Engpässen kommen.

Am Uplink von einem Unternehmensnetzwerk zum Internet kann es andere Dienste geben, die die Bandbreite nutzen. Es ist wichtig, zu verstehen, wie viel Bandbreite für Assets bereitgestellt oder priorisiert werden kann. Beispielsweise können Sie bei einer 1 GBit/s schnellen Verbindung mit 80 % Auslastung nur maximal 20 % der Bandbreite für [!DNL Experience Manager Assets] zuteilen.

Unternehmens-Firewalls und Proxys können Bandbreite zudem auf vielfältige Weise anpassen. Bei diesem Gerätetyp kann die Bandbreite anhand der Dienstqualität, der Bandbreitenbeschränkungen pro Benutzer oder der Bitratenbeschränkungen pro Host priorisiert werden. Dies sind wichtige Engpässe, die zu untersuchen sind, da sie das [!DNL Assets]-Benutzererlebnis erheblich beeinträchtigen können.

In diesem Beispiel nutzt das Unternehmen einen 10 GBit/s schnellen Uplink. Dieser sollte für mehrere Clients ausreichen. Außerdem beschränkt die Firewall die Host-Geschwindigkeit auf 10 MBit/s. Durch diese Beschränkung kann der Traffic auf einen einzelnen Host auf 10 MBit/s drosseln, auch wenn der Uplink zum Internet bei 10 GBit/s liegt.

Dies ist der kleinste Engpass in Bezug auf Clients. Sie können jedoch die für die Firewall verantwortliche Netzwerkbetriebsgruppe kontaktieren, um festzustellen, ob eine Änderung oder ein Eintrag in die Zulassungsliste infrage kommt.

Aus den Beispieldiagrammen ist ersichtlich, dass sechs Geräte einen konzeptionellen, 10 MBit/s schnellen Kanal gemeinsam nutzen. Abhängig von der Größe der verwendeten Assets ist dies möglicherweise nicht ausreichend, um die Erwartungen der Benutzer zu erfüllen.

## Topologie der [!DNL Experience Manager]-Umgebung {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Das Entwerfen der Topologie der [!DNL Experience Manager]-Umgebung erfordert detaillierte Kenntnisse der Systemkonfiguration sowie der Art der Netzwerkverbindung innerhalb der Benutzerumgebung.

Das Beispielszenario umfasst eine Veröffentlichungsfarm mit fünf Servern und einem binären S3-Speicher. Dynamic Media ist ebenfalls konfiguriert.

Der Dispatcher teilt seine 100 MBit/s-Verbindung mit zwei Entitäten, der Außenwelt und der [!DNL Experience Manager] Implementierung. Bei gleichzeitigen Upload- und Download-Vorgängen sollte diese Zahl durch zwei dividiert werden. Der angehängte externe Speicher verwendet eine separate Verbindung.

Die [!DNL Experience Manager] -Implementierung teilt seine 1 Gbit/s-Verbindung mit mehreren Diensten. Aus Sicht der Netzwerktopologie entspricht das der Nutzung eines einzelnen Kanals mit verschiedenen Diensten.

Was das Netzwerk zwischen Client-Gerät und [!DNL Experience Manager]-Bereitstellung angeht, so scheint der kleinste Engpass die Beschränkung auf 10 MBit/s durch die Unternehmens-Firewall zu sein. Sie können diese Werte für die in der [Anleitung zur Dimensionierung in Assets](assets-sizing-guide.md) beschriebenen Größenberechnung verwenden, um das Benutzererlebnis zu bestimmen.

## Definierte Workflows der [!DNL Experience Manager]-Bereitstellung {#defined-workflows-of-the-aem-deployment}

Bei Überlegungen zur Netzwerkleistung ist es möglicherweise wichtig, die Workflows und die im System stattfindenden Veröffentlichungen zu berücksichtigen. Außerdem beanspruchen S3 oder Speicher, der im Netzwerk zugeteilt ist und von Ihnen verwendet wird, und I/O-Anforderungen Netzwerkbandbreite. Daher wird die Leistung selbst in einem voll optimierten Netzwerk durch die Anzahl der Datenträger-I/O beschränkt.

Zur Optimierung von Prozessen rund um die Asset-Erfassung (insbesondere beim Hochladen einer großen Anzahl von Assets) sollten Sie Asset-Workflows untersuchen und mehr über deren Konfiguration erfahren.

Bei der Auswertung der internen Workflow-Topologie sollten Sie Folgendes analysieren:

* Verfahren zum Schreiben eines Assets
* Workflows/Ereignisse, die beim Ändern von Assets/Metadaten Trigger werden
* Verfahren zum Lesen eines Assets

Es folgen einige Punkte, die zu berücksichtigen sind:

* Lesen/Rückgabe von XMP-Metadaten
* Automatische Aktivierung und Replikation
* Wasserzeichen  
* Aufnahme von Unter-Assets/Seitenextraktion
* Überlappende Workflows

Im Folgenden finden Sie ein Kundenbeispiel für die Definition eines Asset-Workflows.

![chlimage_1-357](assets/chlimage_1-357.png)
