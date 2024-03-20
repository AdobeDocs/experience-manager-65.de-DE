---
title: Authoring
description: Konzepte zum Erstellen und Veröffentlichen in Adobe Experience Manager 6.5.
exl-id: dcda537a-1bb2-4ce3-9904-40d158b47556
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 38%

---

# Authoring{#authoring}

## Konzept der Bearbeitung (und Veröffentlichung) {#concept-of-authoring-and-publishing}

AEM bietet Ihnen zwei Umgebungen:

* Autor
* Veröffentlichung

Diese interagieren und ermöglichen es Ihnen, Inhalte auf Ihrer Website verfügbar zu machen, damit Ihre Besucher sie lesen können.

Die Autorenumgebung bietet die Mechanismen zum Erstellen, Aktualisieren und Überprüfen dieses Inhalts, bevor er tatsächlich veröffentlicht wird.

* Ein Autor erstellt und überprüft den Inhalt (dies kann verschiedene Arten von Inhalten sein, z. B. Seiten, Assets, Veröffentlichungen usw.)
* der zu einem späteren Zeitpunkt auf Ihrer Website veröffentlicht wird.

![Übersicht über Umgebungen](assets/chlimage_1-132.png)

In der Autorenumgebung wird die Funktionalität von AEM über zwei Benutzeroberflächen bereitgestellt. In der Publishing-Umgebung entwerfen Sie das Aussehen der Oberfläche, die Sie Ihren Benutzenden zur Verfügung stellen.

### Authoring-Umgebung {#author-environment}

Die Autorin bzw. der Autor arbeitet in der sogenannten **Authoring-Umgebung**. Dies bietet eine einfach zu verwendende Benutzeroberfläche (grafische Benutzeroberfläche (GUI oder UI)) zum Erstellen des Inhalts. Es befindet sich hinter der Firewall eines Unternehmens, die vollen Schutz bietet und die Anmeldung des Autors erfordert, wobei ein Konto verwendet wird, dem die entsprechenden Zugriffsrechte zugewiesen wurden.

>[!NOTE]
>
>Ihr Konto muss über die entsprechenden Zugriffsrechte verfügen, um Inhalte zu erstellen, zu bearbeiten oder zu veröffentlichen.

Je nachdem, wie Ihre Instanz und Ihre persönlichen Zugriffsrechte konfiguriert sind, können Sie viele Aufgaben in Bezug auf Ihre Inhalte durchführen, unter anderem:

* Erstellen neuer Inhalte oder Bearbeiten vorhandener Inhalte auf einer Seite
* Verwenden vordefinierter Vorlagen zum Erstellen neuer Inhaltsseiten
* Erstellen, Bearbeiten und Verwalten von Assets und Sammlungen
* Erstellen, Bearbeiten und Verwalten von Veröffentlichungen
* Entwickeln von Kampagnen und damit zusammenhängenden Ressourcen
* Entwickeln und Verwalten von Community-Sites
* Verschieben, Kopieren oder Löschen von Inhaltsseiten, Assets usw.
* Veröffentlichen (oder Aufheben der Veröffentlichung) von Seiten, Assets usw.

Außerdem gibt es administrative Aufgaben, die Sie beim Verwalten des Inhalts unterstützen:

* Workflows, die steuern, wie Änderungen verwaltet werden, z. B. das Erzwingen einer Überprüfung vor der Veröffentlichung
* Projekte zur Koordinierung einzelner Aufgaben

>[!NOTE]
>
>AEM [verabreicht](/help/sites-administering/home.md) (für die meisten Aufgaben) aus der Autorenumgebung.

#### Veröffentlichungsumgebung {#publish-environment}

Wenn die Inhalte der AEM-Site fertig sind, werden sie in der **Veröffentlichungsumgebung** veröffentlicht. Hier werden die Seiten der Website in Übereinstimmung mit dem Aussehen der entworfenen Oberfläche der vorgesehenen Zielgruppe bereitgestellt.

Normalerweise befindet sich die Veröffentlichungsumgebung innerhalb der demilitarisierten Zone, d. h. sie steht dem Internet zur Verfügung, aber nicht mehr unter dem vollen Schutz des internen Netzwerks.

Wenn die AEM Site ein [Community-Site](/help/communities/overview.md)oder enthält [Communities-Komponenten](/help/communities/author-communities.md), können angemeldete Site-Besucher (Mitglieder) mit Communities-Funktionen interagieren. Sie können beispielsweise in einem Forum posten, Kommentare abgeben oder anderen Mitgliedern folgen. Mitglieder können die Erlaubnis erhalten, Aktivitäten durchzuführen, die normalerweise auf die Autorenumgebung beschränkt sind, z. B. das Erstellen neuer Seiten (Community-Gruppen), Blogartikel und das Moderieren von Beiträgen anderer Mitglieder.

>[!NOTE]
>
>Leider gibt es manchmal Überschneidungen in der verwendeten Terminologie. Dies kann passieren mit:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
>  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
>  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
>
>* **Replizieren/Replikation**
>  Dies sind die technischen Begriffe, die dazu dienen, die Verschiebung von Daten (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere anzuzeigen, d. h. bei der Veröffentlichung oder umgekehrten Replizierung von Benutzerkommentaren.
>

#### Dispatcher {#dispatcher}

Um die Leistung für Besucher Ihrer Website zu optimieren, muss die Variable **[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de)** implementiert Lastenausgleich und Caching.
