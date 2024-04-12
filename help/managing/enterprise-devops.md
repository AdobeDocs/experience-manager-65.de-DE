---
title: DevOp-Strategien für Unternehmen
description: Erfahren Sie mehr über die Prozesse, Methoden und Kommunikation, die zur Vereinfachung von Bereitstellung und Zusammenarbeit nötig sind.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
exl-id: e67f848a-a8cd-4585-a734-e6b1de8a8d74
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 100%

---

# DevOp-Strategien für Unternehmen{#enterprise-devops}

DevOp-Strategien umfassen die notwendigen Prozesse, Methoden und Kommunikation für Folgendes:

* Erleichterung der Bereitstellung der Software über die verschiedenen Umgebungen hinweg;
* Vereinfachung der Zusammenarbeit zwischen der Entwicklungs-, Test- und Bereitstellungs-Teams.

DevOp-Strategien sollen unter anderem zur Vermeidung folgender Probleme beitragen:

* Manuelle Fehler;
* Vergessene Elemente, beispielsweise Dateien, Konfigurationsdetails.
* Diskrepanzen, beispielsweise zwischen der lokalen Umgebung des Entwicklers und anderen Umgebungen.

## Umgebungen {#environments}

Die Bereitstellung von Adobe Experience Manager (AEM) besteht gewöhnlich aus mehreren Umgebungen, die für unterschiedliche Zwecke auf unterschiedlichen Ebenen verwendet werden:

* [Entwicklung](#development)
* [Qualitätssicherung](#quality-assurance)
* [Staging  ](#staging)
* [Produktion](#production-author-and-publish)

>[!NOTE]
>
>Die Produktionsumgebung muss mindestens eine Autoren- und eine Veröffentlichungsumgebung umfassen.
>
>Es wird empfohlen, alle anderen Umgebungen ebenfalls mit einer Autoren- und einer Veröffentlichungsumgebung zu gestalten, um die Produktionsumgebung widerzuspiegeln und frühe Test zu ermöglichen.

### Entwicklung {#development}

Die Entwicklenden sind für die Entwicklung und Anpassung des vorgeschlagenen Projekts mit sämtlichen benötigten Funktionen verantwortlich (z. B. Website, Mobile Apps, DAM-Implementierung). Sie:

* entwickeln und passen die notwendigen Elemente an, beispielsweise Vorlagen, Komponenten, Arbeitsabläufe, Anwendungen;
* setzen das Design um;
* entwickeln die notwendigen Dienste und Skripte, um die geforderten Funktionalitäten umzusetzen.

Die Konfiguration der [Entwicklungsumgebung](/help/sites-developing/best-practices.md) kann von verschiedenen Faktoren abhängen, meist besteht sie jedoch aus:

* einem integrierten Entwicklungssystem mit Versionssteuerung, um eine integrierte Codebasis zur Verfügung zu stellen. Dies wird dazu verwendet, die von den jeweiligen Entwicklern in der jeweiligen Entwicklungsumgebung verwendete Programmierung zusammenzuführen und zu konsolidieren;
* eine persönliche Umgebung für jeden Entwickler, für gewöhnlich auf einem lokalen Rechner. Der Code wird in geeigneten Abständen mit dem Versionskontrollsystem synchronisiert.

Je nach Größe Ihres Systems kann die Entwicklungsumgebung sowohl über Autoren- als auch Veröffentlichungsinstanzen verfügen.

### Qualitätssicherung {#quality-assurance}

Diese Umgebung wird vom Qualitätssicherungs-Team zu umfassenden [Tests](/help/sites-developing/test-plan.md) des neuen Systems, sowohl in Bezug auf Design als auch Funktion, verwendet. Sie sollte über eine Autoren- und eine Veröffentlichungsumgebung mit geeignetem Inhalt verfügen und sämtliche notwendigen Dienste zur Durchführung einer Reihe von Tests bereitstellen.

### Staging   {#staging}

Die Staging-Umgebung sollte ein Spiegelbild der Produktionsumgebung sein – Konfiguration, Code und Inhalte:

* Sie wird zum Testen von Skripten genutzt, die zur Umsetzung der eigentlichen Bereitstellung verwendet werden.
* Sie kann für abschließende Tests (Design, Funktionalität und Schnittstellen) vor der Bereitstellung für die Produktionsumgebungen verwendet werden.
* Obwohl es nicht immer möglich ist, die Staging-Umgebung völlig identisch mit der Produktionsumgebung zu gestalten, sollten die beiden so ähnlich wie möglich sein, um Leistungs- und Belastungstests zu ermöglichen.

### Produktion - Autoren- und Veröffentlichungsumgebung   {#production-author-and-publish}

Die Produktionsumgebung besteht aus den für das tatsächliche [Verfassen und Veröffentlichen](/help/sites-authoring/author.md#concept-of-authoring-and-publishing) der Implementierung notwendigen Umgebungen.

Eine Produktionsumgebung besteht aus mindestens einer Autoreninstanz und einer Veröffentlichungsinstanz:

* [Autoreninstanz](#author) für die Eingabe von Inhalt;
* [Veröffentlichungsinstanz](#publish) für Inhalte, die den Besuchern/Benutzern zugänglich gemacht werden.

Je nach Größe des Projekts besteht sie häufig aus mehreren Autoren- und/oder Veröffentlichungsinstanzen. Auf niedrigerer Ebene kann das Repository in mehrere Instanzen gebündelt werden.

#### Autor {#author}

Autoreninstanzen befinden sich meist hinter der internen Firewall. Das ist die Umgebung, in der Sie und Ihre Kollegen Autorenaufgaben erledigen, wie etwa:

* Verwalten des gesamten Systems;
* Eingeben von Inhalten;
* Konfigurieren des Layouts und Designs des Inhalts;
* Aktivieren der Inhalte in der Veröffentlichungsumgebung.

Aktivierte Inhalte werden gebündelt und in der Replikationswarteschlange der Autorenumgebung abgelegt. Der Replikationsprozess überträgt den Inhalt dann in die Veröffentlichungsumgebung.

Um die in der Veröffentlichungsumgebung erstellten Daten umgekehrt zurück in die Autoreninstanz zu replizieren, durchsucht ein Replikations-Listener in der Autorenumgebung die Veröffentlichungsumgebung und ruft solche Inhalte aus dem Postausgang für die umgekehrte Replikation der Veröffentlichungsumgebung ab.

#### Veröffentlichen {#publish}

Eine Veröffetlichungsumgebung befindet sich normalerweise in der „Demilitarized Zone“ (DMZ). Dies ist die Umgebung, in der die Besucherinnen und Besucher auf Ihren Inhalt zugreifen (beispielsweise über die Website oder über eine App) und damit interagieren, sei es öffentlich oder innerhalb Ihres Intranets. Die Veröffentlichungsumgebung:

* enthält alle aus der Autorenumgebung replizierten Inhalte;
* macht Inhalte für Besucher zugänglich;
* speichert Benutzerdaten, die von den Besuchern erstellt werden, wie Kommentare oder andere Formen von Beiträgen;
* kann so konfiguriert werden, dass solche Benutzerdaten einem Postausgang für die umgekehrte Replikation in die Autorenumgebung hinzugefügt werden.

Die Veröffentlichungsumgebung erzeugt Ihren Inhalt dynamisch in Echtzeit und ermöglicht die Personalisierung des Inhalts für jeden einzelnen Benutzer.

## Code-Verschiebung   {#code-movement}

Propagieren Sie den Code immer von unten nach oben:

* Der Code wird zunächst in der lokalen Umgebung entwickelt und dann in die Entwicklungsumgebungen integriert,
* gefolgt von gründlichen Tests in den QA-Umgebungen,
* und wird dann abermals in den Staging-Umgebungen getestet.
* Der Code sollte erst danach in den Produktionsumgebungen bereitgestellt werden.

Der Code (z. B. angepasste Funktionalitäten von Web-Anwendungen und Design-Vorlagen) wird durch den Export und Import von Datenpaketen zwischen den verschiedenen Inhalts-Repositorys übertragen. Ggf. kann diese Replikation als automatischer Prozess konfiguriert werden.

AEM-Projekte lösen häufig die Bereitstellung von Code aus:

* Automatisch: zur Übertragung an die Entwicklungs- und QA-Umgebungen.
* Manuell: Die Bereitstellung für die Staging- und Produktionsumgebungen erfolgt kontrollierter und häufig manuell. Bei Bedarf ist jedoch eine Automatisierung möglich.

![chlimage_1](assets/chlimage_1.png)

## Inhaltsverschiebung {#content-movement}

Inhalte, die für die Produktion erstellt werden, sollten **immer** in der Autoreninstanz der Produktion verfasst werden.

Die Inhaltsverschiebung sollte nicht der Code-Verschiebung von niedrigeren zu höheren Umgebungen folgen, da die Erstellung von Inhalten durch Autoren auf lokalen Rechnern oder in niedrigeren Umgebungen und die darauffolgende Verschiebung in die Produktionsumgebung kein optimales Verfahren darstellt und wahrscheinlich zu Fehlern und Unstimmigkeiten führt.

Die Produktionsinhalte sollten von der Produktionsumgebung in die Staging-Umgebung verschoben werden, um zu gewährleisten, dass die Staging-Umgebung eine effiziente und genaue Testumgebung bietet.

>[!NOTE]
>
>Dies bedeutet nicht, dass die Staging-Inhalte kontinuierlich mit der Produktion synchronisiert werden müssen. Regelmäßige Updates reichen aus, jedoch sollten diese besonders vor dem Testen einer neuen Code-Iteration erfolgen. Die Inhalte in den Qualitätssicherungs- und Entwicklungsumgebungen müssen nicht gleich häufig aktualisiert werden. Sie sollten die Produktionsinhalte gut widerspiegeln.

Inhalte können übertragen werden:

* zwischen verschiedenen Umgebungen – durch den Export und Import von Paketen;
* zwischen verschiedenen Instanzen – durch direktes Replizieren ([AEM-Replikation](/help/sites-deploying/replication.md)) des Inhalts (mithilfe einer HTTP- oder HTTPS-Verbindung).

![chlimage_1-1](assets/chlimage_1-1.png)
