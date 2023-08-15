---
title: Upgrade auf Adobe Experience Manager 6.5
description: Erfahren Sie mehr über die Grundlagen des Upgrades einer älteren Adobe Experience Manager-AEM-Installation auf AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: 722d544c-c342-4c1c-80e5-d0a1244f4d36
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 63%

---

# Upgrade auf Adobe Experience Manager (AEM) 6.5 {#upgrading-to-aem}

Dieser Abschnitt behandelt die Aktualisierung einer AEM auf AEM 6.5:

* [Planung von Upgrades](/help/sites-deploying/upgrade-planning.md)
* [Bewertung der Komplexität des Upgrades mit dem Musterdetektor ](/help/sites-deploying/pattern-detector.md)
* [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  <!--* [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->
* [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md)
* [Upgrades von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Wartungsaufgaben vor einem Upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Durchführen eines In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md)
* [Prüfungen und Fehlerbehebung nach einem Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md)
* [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md)

Für ein einfacheres Verständnis der in diesen Verfahren verwendeten AEM-Instanzen werden die folgenden Begriffe in diesen Artikeln verwendet:

* Die Instanz *Quelle* ist die AEM-Instanz, von der Sie aktualisieren.
* Die Instanz *Ziel* ist diejenige, auf die Sie aktualisieren.

>[!NOTE]
>
>Als Teil der Bemühungen, die Zuverlässigkeit von Upgrades zu verbessern, wurde AEM einer umfassenden Repository-Neustrukturierung unterzogen. Weitere Informationen zur Anpassung an die neue Struktur finden Sie unter [Repository-Neustrukturierung in AEM.](/help/sites-deploying/repository-restructuring.md)

## Was hat sich geändert? {#what-has-changed}

Im Folgenden werden die wichtigsten Änderungen der letzten Versionen von AEM beschrieben:

In AEM 6.0 wurde das neue Jackrabbit-Oak-Repository eingeführt. Persistenz-Manager wurden durch [Mikrokernel](/help/sites-deploying/platform.md#contentbody_title_4) ersetzt. Ab Version 6.1 wird CRX2 nicht mehr unterstützt. Ein Migrationstool namens crx2oak muss ausgeführt werden, um CRX2-Repositorys von 5.6.1-Instanzen zu migrieren. Weitere Informationen finden Sie unter [Verwenden des CRX2OAK-Migrations-Tools](/help/sites-deploying/using-crx2oak.md).

Wenn Assets Insights verwendet wird und Sie von einer Version aktualisieren, die älter als AEM 6.2 ist, müssen Assets migriert werden und IDs über ein JMX-Bean generiert werden. Für interne Adobe-Tests wurden 125.000 Assets in einer TarMK-Umgebung in einer Stunde migriert, die Ergebnisse können jedoch variieren.

Mit AEM 6.3 wurde ein neues Format für den `SegmentNodeStore` eingeführt, der die Basis für die TarMK-Implementierung bildet. Wenn Sie von einer Version aktualisieren, die älter als AEM 6.3 ist, ist im Rahmen der Aktualisierung eine Repository-Migration erforderlich, die Systemausfälle mit sich bringt.

Adobe Engineering schätzt, dass diese Ausfallzeit ca. 20 Minuten beträgt. Eine Neuindizierung ist nicht erforderlich. Außerdem wurde eine neue Version des crx2oak-Tools veröffentlicht, die mit dem neuen Repository-Format verwendet werden kann.

**Diese Migration ist nicht erforderlich, wenn Sie von AEM 6.3 auf AEM 6.5 aktualisieren.**

Die Wartungsaufgaben vor einem Upgrade wurden optimiert, um die Automatisierung zu unterstützen.

Die Befehlszeilenverwendungsoptionen des CRX2OAK-Tools wurden geändert, um automatisierungsfreundlich zu sein und weitere Aktualisierungspfade zu unterstützen.

Die Prüfungen nach einem Upgrade wurden ebenfalls automatisierungsfreundlich gestaltet.

Regelmäßige Speicherbereinigung von Revisionen und Datenspeicherbereinigung sind jetzt routinemäßige Wartungsaufgaben, die regelmäßig durchgeführt werden müssen. Mit der Einführung von AEM 6.3 unterstützt und empfiehlt Adobe die Online-Revisionsbereinigung. Siehe [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md) für Informationen zur Konfiguration dieser Aufgaben.

Neu in AEM ist der [Musterdetektor](/help/sites-deploying/pattern-detector.md), mit dem Sie bei der Planung des Upgrades die Komplexität der Aktualisierung ermitteln können. In 6.5 liegt der Fokus auf der [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) der Funktionen. Außerdem wurden Best Practices für [nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md) hinzugefügt.

Weitere Informationen zu den Änderungen der letzten AEM Versionen finden Sie in den vollständigen Versionshinweisen:

* [Versionshinweise zum neuesten Service Pack von Adobe Experience Manager 6.5](/help/release-notes/release-notes.md)

## Überblick über das Upgrade {#upgrade-overview}

Die Aktualisierung von AEM ist ein mehrstufiger Prozess, der in manchen Fällen mehrere Monate dauert. Die nachfolgende Darstellung gibt einen Überblick über die Bestandteile eines Upgrade-Projekts und die entsprechenden Inhalte, die in dieser Dokumentation enthalten sind:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Ablauf des Upgrades {#upgrade-overview-1}

Das folgende Diagramm zeigt den für das Upgrade empfohlenen Ablauf. Beachten Sie den Verweis auf die neuen Funktionen, die Adobe eingeführt hat. Das Upgrade sollte damit starten, dass mit dem Musterdetektor ein Bericht über vorhandene Muster erstellt wird (siehe [Bewertung der Komplexität des Upgrades mit dem Musterdetektor](/help/sites-deploying/pattern-detector.md)), mit dessen Hilfe Sie entscheiden können, welchem Pfad Sie für die Kompatibilität mit AEM 6.4 folgen möchten.

In Version 6.5 wurde der Fokus darauf gelegt, alle neuen Funktionen abwärtskompatibel zu halten. In Fällen, in denen jedoch noch einige Abwärtskompatibilitätsprobleme auftreten, können Sie mit dem Kompatibilitätsmodus die Entwicklung zeitweise verschieben, um Ihren benutzerdefinierten Code mit Version 6.5 konform zu halten. Dieser Ansatz hilft Ihnen, Entwicklungsaufwand unmittelbar nach der Aktualisierung zu vermeiden (siehe [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md)).

In Ihrem 6.5-Entwicklungszyklus helfen Ihnen abschließend die unter „Nachhaltige Upgrades“ eingeführten Funktionen (siehe [Nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md)), Best Practices einzuhalten, um zukünftige Upgrades sogar noch effizienter und nahtloser durchzuführen.

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
