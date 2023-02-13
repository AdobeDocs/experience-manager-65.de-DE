---
title: Aktualisieren auf AEM 6.5
seo-title: Upgrading to AEM 6.5
description: Erfahren Sie mehr über die Grundlagen der Aktualisierung einer älteren AEM-Installation auf AEM 6.5.
seo-description: Learn about the basics of upgrading an older AEM installation to AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: 722d544c-c342-4c1c-80e5-d0a1244f4d36
source-git-commit: 02fc145d5ec1458d1f71a2f353b56b944a267f3e
workflow-type: ht
source-wordcount: '694'
ht-degree: 100%

---

# Aktualisieren auf AEM 6.5 {#upgrading-to-aem}

In diesem Abschnitt wird das Aktualisieren einer AEM-Installation auf AEM 6.5 beschrieben:

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

* Bei der *Quell* instanz handelt es sich um die AEM-Instanz, von der aus die Aktualisierung durchgeführt wird.
* Bei der *Ziel* instanz handelt es sich um die Instanz, auf die die Aktualisierung durchgeführt wird.

>[!NOTE]
>
>Als Teil der Bemühungen, die Zuverlässigkeit von Upgrades zu verbessern, wurde AEM einer umfassenden Repository-Neustrukturierung unterzogen. Weitere Informationen, wie die neue Struktur angepasst wird, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

## Was wurde geändert? {#what-has-changed}

Nachfolgend sind die wichtigsten Änderungen im Vergleich zu den letzten AEM-Versionen aufgeführt:

In AEM 6.0 wurde das neue Jackrabbit-Oak-Repository eingeführt. Persistenz-Manager wurden durch [Mikrokernel](/help/sites-deploying/platform.md#contentbody_title_4) ersetzt. Ab Version 6.1 wird CRX2 nicht mehr unterstützt. Ein Migrationstool mit der Bezeichnung CRX2OAK muss ausgeführt werden, um CRX2-Repositorys von 5.6.1-Instanzen zu migrieren. Weitere Informationen finden Sie unter [Verwenden des CRX2OAK-Migrationstools](/help/sites-deploying/using-crx2oak.md).

Wenn Asset Insights verwendet werden soll und Sie ein Upgrade von einer Version vor AEM 6.2 durchführen, müssen Assets migriert und IDs für diese über ein JMX-Bean generiert werden. In internen Tests wurden 125.000 Assets in einer TarMK-Umgebung innerhalb einer Stunde migriert. Ihre Ergebnisse können jedoch möglicherweise abweichen.

Mit AEM 6.3 wurde ein neues Format für den `SegmentNodeStore` eingeführt, der die Basis für die TarMK-Implementierung bildet. Wenn Sie eine Version vor AEM 6.3 aktualisieren, muss beim Upgrade eine Migration des Repositorys durchgeführt werden, während der das System nicht verfügbar ist.

Adobe Engineering schätzt, dass diese Ausfallzeit ca. 20 Minuten beträgt. Beachten Sie, dass keine Neuindizierung erforderlich ist. Darüber hinaus wurde eine neue Version des CRX2OAK-Tools für das neue Repository-Format veröffentlicht.

**Diese Migration ist nicht erforderlich, wenn Sie von AEM 6.3 auf AEM 6.5 aktualisieren.**

Die Wartungsaufgaben vor einem Upgrade wurden optimiert, um die Automatisierung zu unterstützen.

Die Befehlszeilenoptionen für die Verwendung des CRX2OAK-Tools wurden geändert, um diese automatisierungsfreundlich zu machen und mehr Upgrade-Pfade zu unterstützen.

Die Prüfungen nach einem Upgrade wurden ebenfalls automatisierungsfreundlich gestaltet.

Zu den regelmäßig durchzuführenden Routinewartungsaufgaben gehören jetzt die regelmäßige Revisionsbereinigung und die Bereinigung des Datenspeichers. Mit der Einführung von AEM 6.3 unterstützt und empfiehlt Adobe die Online-Revisionsbereinigung. Weitere Informationen zum Konfigurieren dieser Aufgaben finden Sie unter [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).

Neu in AEM ist der [Musterdetektor](/help/sites-deploying/pattern-detector.md), mit dem Sie bei der Planung des Upgrades die Komplexität der Aktualisierung ermitteln können. In 6.5 liegt der Fokus auf der [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) der Funktionen. Außerdem wurden Best Practices für [nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md) hinzugefügt.

Einzelheiten zu weiteren Änderungen in den neuen AEM-Versionen finden Sie in den vollständigen Versionshinweisen:

* [Allgemeine Versionshinweise zu Adobe Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/release-notes.html?lang=de)
* [Versionshinweise zum neuesten Service Pack von Adobe Experience Manager 6.5](/help/release-notes/release-notes.md)

## Überblick über das Upgrade {#upgrade-overview}

Die Aktualisierung von AEM ist ein mehrstufiger Prozess, der in manchen Fällen mehrere Monate dauert. Die nachfolgende Darstellung gibt einen Überblick über die Bestandteile eines Upgrade-Projekts und die entsprechenden Inhalte, die in dieser Dokumentation enthalten sind:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Ablauf des Upgrades {#upgrade-overview-1}

Das folgende Diagramm zeigt den für das Upgrade empfohlenen Ablauf. Beachten Sie den Verweis auf die neu eingeführten Funktionen. Das Upgrade sollte damit starten, dass mit dem Musterdetektor ein Bericht über vorhandene Muster erstellt wird (siehe [Bewertung der Komplexität des Upgrades mit dem Musterdetektor](/help/sites-deploying/pattern-detector.md)), mit dessen Hilfe Sie entscheiden können, welchem Pfad Sie für die Kompatibilität mit AEM 6.4 folgen möchten.

In 6.5 haben wir einen starken Fokus darauf gelegt, alle neuen Funktionen abwärtskompatibel zu gestalten. In Fällen, in denen mit der Abwärtskompatibilität weiterhin Probleme auftreten, können Sie notwendige Entwicklungsarbeiten jedoch mit dem Kompatibilitätsmodus aufschieben und so Ihren benutzerdefinierten Code vorübergehend mit 6.5 kompatibel halten. Mit diesem Ansatz vermeiden Sie sofort nach dem Upgrade jeden erforderlichen Entwicklungsaufwand (siehe [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md)).

In Ihrem 6.5-Entwicklungszyklus helfen Ihnen abschließend die unter „Nachhaltige Upgrades“ eingeführten Funktionen (siehe [Nachhaltige Upgrades](/help/sites-deploying/sustainable-upgrades.md)), Best Practices einzuhalten, um zukünftige Upgrades sogar noch effizienter und nahtloser durchzuführen.

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
