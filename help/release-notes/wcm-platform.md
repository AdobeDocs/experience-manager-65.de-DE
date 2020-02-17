---
title: AEM Foundation und Repository
description: Spezifische Versionshinweise zur Plattform und zum Repository von Adobe Experience Manager 6.3
uuid: 70626eda-c514-44bd-9f28-ff7abdc22f53
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 66ecf4c5-6d0f-4586-880d-7d1c8a5a5614
docset: aem65
translation-type: tm+mt
source-git-commit: 4dc4a518c212555b7833ac27de02087a403d3517

---


# AEM Foundation und Repository{#aem-foundation-repository}

## Liste der Änderungen   {#list-of-changes}

### Repository {#repository}

* Die Foundation-Komponente von Adobe Experience Manager 6.5 basiert auf aktualisierten Versionen des OSGi-basierten Frameworks (Apache Sling und Apache Felix) und dem Java Content Repository Apache Jackrabbit Oak 1.10.2.
* Please see [Apache Jackrabbit Oak Jira v. 1.10.0](https://archive.apache.org/dist/jackrabbit/oak/1.10.0/RELEASE-NOTES.txt), [Apache Jackrabbit Oak Jira v. 1.10.1](https://archive.apache.org/dist/jackrabbit/oak/1.10.1/RELEASE-NOTES.txt) and [Apache Jackrabbit Oak Jira v. 1.10.2](https://archive.apache.org/dist/jackrabbit/oak/1.10.2/RELEASE-NOTES.txt) for a full overview of fixed issues.

>[!CAUTION]
>
>* Aufgrund der neuen Version von Oak Segment Tar, die mit AEM 6.3 eingeführt wurde, ist eine Repository-Migration erforderlich. Dieser Schritt ist obligatorisch, wenn Sie eine Aktualisierung von einer älteren TarMK-Version durchführen oder von einem anderen Persistenztyp zum neuen Segment-TAR-Format wechseln möchten. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Migration auf Oak-Segment-TAR – Häufig gestellte Fragen (FAQ)](/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar).
>



### Java-Unterstützung {#java-support}

* Neben der bereits unterstützten Java 8-Version wird nun auch Java 11 unterstützt.
* Um eine optimale Leistung zu erzielen, überschreiben Sie die GC-Standardwerte mit anderen Werten. Weitere Informationen finden Sie im Abschnitt [Installieren und Aktualisieren](/help/sites-deploying/custom-standalone-install.md).
* Java 11- und Java 8-Wartungsupdates werden Kunden von Adobe zur Nutzung in AEM-bezogenen Projekten bereitgestellt, sofern diese nicht bei Oracle öffentlich zugänglich sind.

### OSGI {#osgi}

* Es wurden OSGi Promises- und Converter-Dienstprogramm-Bibliotheken hinzugefügt

### Projekte und Workflows {#projects-and-workflows}

* Der neue in Version 6.4 eingeführte Workflow-Modell-Editor wurde verbessert. Neben einer größeren Anzahl von Vorgängen wie Kopieren und Veröffentlichen werden nun Variablen in Workflowschritten unterstützt. Außerdem wurden ODER- und UND-Teilungen optimiert.

### Suche{#searching}

* Die Suche in Oak unterstützt jetzt dynamische Facetten. Beispielsweise zeigt die Filterleiste in der Asset-Suche die geschätzte Ergebnismenge an.
* QueryBuilder wurde erweitert und liefert nun Ergebnisse mit dynamischen Facetten.

### Sicherheit {#security}

* Passwörter von Administratoren laufen nun ab.

### Benutzeroberfläche {#user-interface}

Die Benutzeroberfläche wurde verbessert, um sie effizienter und anwenderfreundlicher zu gestalten.

* AEM 6.5 bietet eine neue UI zur Verwaltung von Berechtigungen von Anwendern und Gruppen, die die Anzeige und Konfiguration kompletter Berechtigungs- und Einschränkungssätze vereinfacht. Eine Navigation zu CRXDE ist dabei nicht erforderlich.
* In Spaltenansichten werden nun auch nur noch die Einträge geladen, die auf dem Bildschirm sichtbar sind. Weitere Einträge werden lediglich geladen, wenn der Anwender einen Bildlauf durchführt. In der Listen- und Kartenansicht wurde so bereits seit Version 6.0 verfahren (verbessert in Version 6.4).
* Spaltenansichten enthalten nun ggf. den Workflowstatus für Seiten/Assets.
* Die Aktion „Alle auswählen“ ist eine schnelle Möglichkeit, eine Aktion mit allen Seiten/Assets im selben Ordner auszuführen.
* Mit der Aktion „Alle auswählen“ wird versucht, die Aktion für alle Seiten/Assets durchzuführen, nicht nur für die geladenen Elemente. Es wird ein Warndialogfeld angezeigt, wenn die Aktion nicht für Massenaktionen aktualisiert wurde.

>[!CAUTION]
>
>* Adobe plant keine weiteren Verbesserungen an der klassischen UI. In AEM 6.5 ist die klassische UI integriert und Kunden, die auf diese Version aktualisieren, können diese wie gehabt verwenden. Note that Classic UI remains fully supported while being deprecated [Read more](/help/sites-deploying/ui-recommendations.md).
>



### Aktualisierung {#upgrade}

* Das Aktualisierungsverfahren bleibt in 6.5 größtenteils unverändert.
* Wir unterstützen weiterhin die in 6.4 eingeführten Funktionen „Abwärtskompatibilität“, „Bewertung der Aktualisierungskomplexität“ und „Nachhaltige Aktualisierungen“. Für diese Bereiche wurden nach Bedarf versionsspezifische Aktualisierungen durchgeführt.
* Das Pattern Detector-Paket wurde vereinfacht und es gibt ein Paket, das Aktualisierungen auf 6.5 für die verfügbaren Quellversionen bewertet.
* Please see the [Upgrade documentation](/help/sites-deploying/upgrade.md) for more details on upgrade procedure.

### Webserver {#web-server}

* Die Quickstart-Distribution verwendet Eclipse Jetty 9.4.15 als Servlet-Engine (AEM 6.4 im Lieferumfang von 9.3.22)

