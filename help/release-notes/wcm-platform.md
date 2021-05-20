---
title: AEM Foundation und Repository
description: Versionshinweise für die Adobe Experience Manager-Plattform und das -Repository.
exl-id: 06938419-392b-432d-ba0c-ba444b3e141c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 55%

---

# AEM Foundation und Repository {#aem-foundation-repository}

## Liste der Änderungen {#list-of-changes}

### Repository {#repository}

* Die Foundation-Komponente von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository Apache Jackrabbit Oak 1.10.2.
* Einen Überblick über behobene Probleme finden Sie unter [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt) .

>[!CAUTION]
>
>Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Migration auf Oak-Segment-TAR – Häufig gestellte Fragen (FAQ)](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

### Java-Unterstützung {#java-support}

* Neue Unterstützung für Java 11 sowie für bereits unterstützte Java 8.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Java 11- und Java 8-Wartungsupdates werden von Adobe für die Kundennutzung in AEM-bezogenen Projekten verteilt, wenn sie nicht über Oracle öffentlich verfügbar sind.

### OSGI {#osgi}

* OSGi Promises- und Converter-Dienstprogrammbibliotheken wurden hinzugefügt.

### Projekte und Workflows {#projects-and-workflows}

* Der neue Workflow-Modell-Editor, der in Version 6.4 eingeführt wurde, wurde verbessert und umfasst jetzt weitere Vorgänge wie Kopieren und Veröffentlichen, Variablenunterstützung in Workflow-Schritten und erweiterte Aufspaltungen für `OR` und `AND`.

### Suchen {#searching}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste bei der Asset-Suche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert, um Ergebnisse mit dynamischen Facetten bereitzustellen.

### Sicherheit {#security}

* Passwörter von Administratoren laufen nun ab.

### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* AEM 6.5 bietet eine neue UI zur Verwaltung von Berechtigungen von Anwendern und Gruppen, die die Anzeige und Konfiguration kompletter Berechtigungs- und Einschränkungssätze vereinfacht. Eine Navigation zu CRXDE ist dabei nicht erforderlich.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4)..
* Spaltenansichten enthalten jetzt ggf. den Workflow-Status für Seiten/Assets.
* Die Aktion &quot;Alle auswählen&quot;bietet eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion Alle auswählen wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Wenn die Aktion nicht für die Verarbeitung von Massenaktionen aktualisiert wird, wird ein Warnhinweis angezeigt.

>[!CAUTION]
>
>Adobe bietet keine weiteren Verbesserungen an der klassischen Benutzeroberfläche. Experience Manager 6.5 beinhaltet die klassische Benutzeroberfläche zur Abwärtskompatibilität. Die klassische Benutzeroberfläche wird weiterhin vollständig unterstützt, obwohl sie veraltet ist [mehr dazu](/help/sites-deploying/ui-recommendations.md).

### Aktualisierung {#upgrade}

* Das Aktualisierungsverfahren bleibt in 6.5 größtenteils unverändert.
* Wir unterstützen weiterhin die in 6.4 eingeführten Funktionen „Abwärtskompatibilität“, „Bewertung der Aktualisierungskomplexität“ und „Nachhaltige Aktualisierungen“. Für diese Bereiche wurden nach Bedarf versionsspezifische Aktualisierungen durchgeführt.
* Das Pattern Detector-Paket wurde vereinfacht und es gibt ein Paket, das Aktualisierungen auf 6.5 für die verfügbaren Quellversionen bewertet.
* Weitere Informationen zum Upgrade-Verfahren finden Sie in der [Upgrade-Dokumentation](/help/sites-deploying/upgrade.md).

### Webserver {#web-server}

* Die Quickstart-Verteilung verwendet Eclipse Jetty 9.4.15 als Servlet-Engine (AEM 6.4 im Lieferumfang von 9.3.22 enthalten).
