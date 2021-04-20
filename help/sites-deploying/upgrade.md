---
title: Aktualisieren auf AEM 6.5
seo-title: Aktualisieren auf AEM 6.5
description: Erfahren Sie mehr über die Grundlagen der Aktualisierung einer älteren AEM-Installation auf AEM 6.5.
seo-description: Erfahren Sie mehr über die Grundlagen der Aktualisierung einer älteren AEM-Installation auf AEM 6.5.
uuid: 45368056-273c-4f1a-9da6-e7ba5c2bbc0d
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: ebd99cc4-8762-4c28-a177-d62dac276afe
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 82%

---


# Aktualisieren auf AEM 6.5 {#upgrading-to-aem}

In diesem Abschnitt wird das Aktualisieren einer AEM-Installation auf AEM 6.5 beschrieben:

* [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md)
* [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor](/help/sites-deploying/pattern-detector.md) 
* [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md)

<!--* [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->
* [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md)
* [Aktualisierung von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Durchführen einer In-Place-Aktualisierung](/help/sites-deploying/in-place-upgrade.md)
* [Prüfungen und Fehlerbehebung nach einer Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Nachhaltige Aktualisierungen](/help/sites-deploying/sustainable-upgrades.md) 
* [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md)
* [Repository-Neustrukturierung in AEM 6.5](/help/sites-deploying/repository-restructuring.md)

Für ein einfacheres Verständnis der in diesen Verfahren verwendeten AEM-Instanzen werden die folgenden Begriffe in diesen Artikeln verwendet:

* Bei der *Quell* instanz handelt es sich um die AEM-Instanz, von der aus die Aktualisierung durchgeführt wird.
* Bei der *Ziel* instanz handelt es sich um die Instanz, auf die die Aktualisierung durchgeführt wird.

>[!NOTE]
>
>Als Teil der Bemühungen, die Zuverlässigkeit von Upgrades zu verbessern, wurde AEM einer umfassenden Repository-Neustrukturierung unterzogen. Weitere Informationen, wie die neue Struktur angepasst wird, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

## Was wurde geändert? {#what-has-changed}

Nachfolgend sind die wichtigsten Änderungen im Vergleich zu den letzten AEM-Versionen aufgeführt:

In AEM 6.0 wurde das neue Jackrabbit-Oak-Repository eingeführt. Persistenz-Manager wurden durch [Mikrokernel](/help/sites-deploying/platform.md#contentbody_title_4) ersetzt. Ab Version 6.1 wird CRX2 nicht mehr unterstützt. Ein Migrationstool mit der Bezeichnung CRX2OAK muss ausgeführt werden, um CRX2-Repositorys von 5.6.1-Instanzen zu migrieren. Weitere Informationen finden Sie unter [Verwenden des CRX2OAK-Migrationstools](/help/sites-deploying/using-crx2oak.md).

Wenn Asset Insights verwendet werden soll und Sie eine Aktualisierung von einer Version vor AEM 6.2 durchführen, müssen Assets migriert und IDs für diese über ein JMX-Bean generiert werden. In internen Tests wurden 125.000 Assets in einer TarMK-Umgebung innerhalb einer Stunde migriert. Ihre Ergebnisse können jedoch möglicherweise abweichen.

Mit AEM 6.3 wurde ein neues Format für den `SegmentNodeStore` eingeführt, der die Basis für die TarMK-Implementierung bildet. Wenn Sie eine Version vor AEM 6.3 aktualisieren, muss bei der Aktualisierung eine Migration des Repositorys durchgeführt werden, während der das System nicht verfügbar ist.

Adobe Engineering schätzt, dass diese Ausfallzeit ca. 20 Minuten beträgt. Beachten Sie, dass keine Neuindizierung erforderlich ist. Darüber hinaus wurde eine neue Version des CRX2OAK-Tools für das neue Repository-Format veröffentlicht.

**Diese Migration ist nicht erforderlich, wenn Sie von AEM 6.3 auf AEM 6.5 aktualisieren.**

Die Wartungsaufgaben vor einer Aktualisierung wurden optimiert, um die Automatisierung zu unterstützen.

Die Befehlszeilenoptionen für die Verwendung des CRX2OAK-Tools wurden geändert, um diese automatisierungsfreundlich zu machen und mehr Aktualisierungspfade zu unterstützen.

Die Prüfungen nach einer Aktualisierung wurden ebenfalls automatisierungsfreundlich gestaltet.

Zu den regelmäßig durchzuführenden Routinewartungsaufgaben gehören jetzt die regelmäßige Revisionsbereinigung und die Bereinigung des Datenspeichers. Mit der Einführung von AEM 6.3 unterstützt und empfiehlt Adobe die Online-Revisionsbereinigung. Weitere Informationen zum Konfigurieren dieser Aufgaben finden Sie unter [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).

Neu in AEM ist der [Musterdetektor](/help/sites-deploying/pattern-detector.md), mit dem Sie bei der Planung der Aktualisierung die Komplexität der Aktualisierung ermitteln können. In 6.5 liegt der Fokus auf der [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) der Funktionen. Außerdem wurden Best Practices für [nachhaltige Aktualisierungen](/help/sites-deploying/sustainable-upgrades.md) hinzugefügt.

Einzelheiten zu weiteren Änderungen in den neuen AEM-Versionen finden Sie in den vollständigen Versionshinweisen:

* [https://helpx.adobe.com/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-4/release-notes.html)
* [https://helpx.adobe.com/de/experience-manager/6-5/release-notes.html](https://helpx.adobe.com/de/experience-manager/6-5/release-notes.html)

## Überblick über die Aktualisierung {#upgrade-overview}

Die Aktualisierung von AEM ist ein mehrstufiger Prozess, der in manchen Fällen mehrere Monate dauert. Die nachfolgende Darstellung gibt einen Überblick über die Bestandteile eines Aktualisierungsprojekts und die entsprechenden Inhalte, die in dieser Dokumentation enthalten sind:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Aktualisierungsablauf {#upgrade-overview-1}

Das folgende Diagramm zeigt den für die Aktualisierung empfohlenen Ablauf. Beachten Sie den Verweis auf die neu eingeführten Funktionen. Die Aktualisierung sollte mit dem Musterdetektor (siehe [Beurteilung der Aktualisierungskomplexität mit dem Musterdetektor](/help/sites-deploying/pattern-detector.md)) Beginn haben. Anhand dieser Informationen können Sie anhand der Muster im erstellten Bericht festlegen, welchen Pfad Sie zur Kompatibilität mit AEM 6.4 verwenden möchten.

In 6.5 wurde der Fokus auf die Abwärtskompatibilität aller neuen Funktionen gelegt. In Fällen, in denen jedoch noch Kompatibilitätsprobleme mit dem Abwärtsmodus auftreten, können Sie die Entwicklung vorübergehend verschieben, um den benutzerdefinierten Code mit 6.5 kompatibel zu halten. Dieser Ansatz hilft Ihnen, Entwicklungsaufwand unmittelbar nach der Aktualisierung zu vermeiden (siehe [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md)).

In Ihrem 6.5-Entwicklungszyklus schließlich helfen Ihnen Funktionen, die unter Nachhaltige Upgrades eingeführt wurden (siehe [Nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md)), Best Practices zu befolgen, um zukünftige Upgrades noch effizienter und nahtloser zu gestalten.

![6_4_upgrade_overviewflow chart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)

