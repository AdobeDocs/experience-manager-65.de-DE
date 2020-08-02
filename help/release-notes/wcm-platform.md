---
title: AEM Foundation und Repository
description: Versionshinweise für die Adobe Experience Manager-Plattform und das Repository.
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 55%

---


# AEM Foundation und Repository {#aem-foundation-repository}

## Liste der Änderungen      {#list-of-changes}

### Repository {#repository}

* Die Foundation-Komponente von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository Apache Jackrabbit Oak 1.10.2.
* Eine Übersicht über behobene Probleme finden Sie unter [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) und [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt).

>[!CAUTION]
>
>Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Migration auf Oak-Segment-TAR – Häufig gestellte Fragen (FAQ)](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).

### Java-Unterstützung {#java-support}

* Neue Unterstützung für Java 11 sowie das bereits unterstützte Java 8.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Wartungs-Updates für Java 11 und Java 8 werden von der Adobe für die Kundennutzung in AEM-bezogenen Projekten bereitgestellt, wenn sie nicht von Oracle öffentlich verfügbar sind.

### OSGI {#osgi}

* OSGi-Versprechungen und Konverter-Dienstprogramm-Bibliotheken hinzugefügt.

### Projekte und Workflows {#projects-and-workflows}

* New Workflow Model editor introduced in 6.4 has been improved to include more operations like Copy and Publish, Variable support in Workflow steps and enhanced `OR` and `AND` splits.

### Suche {#searching}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste in der Asset-Suche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert, um Ergebnisse mit dynamischen Facetten bereitzustellen.

### Sicherheit {#security}

* Passwörter von Administratoren laufen nun ab.

### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* AEM 6.5 bietet eine neue UI zur Verwaltung von Berechtigungen von Anwendern und Gruppen, die die Anzeige und Konfiguration kompletter Berechtigungs- und Einschränkungssätze vereinfacht. Eine Navigation zu CRXDE ist dabei nicht erforderlich.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4)..
* Spalten-Ansichten enthalten jetzt den Workflow-Status für Seiten/Assets, sofern zutreffend.
* Mit der Aktion &quot;Alles auswählen&quot;können Sie schnell eine Aktion mit allen Seiten/Assets im selben Ordner ausführen.
* Mit der Aktion Alle auswählen wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Wenn die Aktion nicht aktualisiert wurde, um Massenaktionen zu verarbeiten, wird eine Warnung angezeigt.

>[!CAUTION]
>
>Die klassische Benutzeroberfläche wird durch Adobe nicht weiter verbessert. Experience Manager 6.5 enthält die klassische Benutzeroberfläche für Abwärtskompatibilität. Classic UI remains fully supported while being deprecated [Read more](/help/sites-deploying/ui-recommendations.md).

### Aktualisierung {#upgrade}

* Das Aktualisierungsverfahren bleibt in 6.5 größtenteils unverändert.
* Wir unterstützen weiterhin die in 6.4 eingeführten Funktionen „Abwärtskompatibilität“, „Bewertung der Aktualisierungskomplexität“ und „Nachhaltige Aktualisierungen“. Für diese Bereiche wurden nach Bedarf versionsspezifische Aktualisierungen durchgeführt.
* Das Pattern Detector-Paket wurde vereinfacht und es gibt ein Paket, das Aktualisierungen auf 6.5 für die verfügbaren Quellversionen bewertet.
* Weitere Informationen zum Aktualisierungsverfahren finden Sie in der [Aktualisierungsdokumentation](/help/sites-deploying/upgrade.md).

### Webserver {#web-server}

* Die Quickstart-Distribution verwendet Eclipse Jetty 9.4.15 als Servlet-Engine (AEM 6.4 im Lieferumfang 9.3.22 enthalten).
