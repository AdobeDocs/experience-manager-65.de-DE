---
title: Systeminformationen anzeigen
seo-title: Systeminformationen anzeigen
description: Erfahren Sie, wie Sie Diagramme zur Ressourcenüberwachung und Informationen über den Server anzeigen, der AEM Forms ausführt.
seo-description: Erfahren Sie, wie Sie Diagramme zur Ressourcenüberwachung und Informationen über den Server anzeigen, der AEM Forms ausführt.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Systeminformationen anzeigen {#view-system-information}

Auf der Registerkarte „System“ werden Diagramme zur Ressourcenüberwachung und Informationen über den Server angezeigt, der AEM Forms ausführt. Klicken Sie in Administration Console in der rechten oberen Ecke der Seite auf „Health Monitor“, um diese Informationen anzuzeigen. Wenn Sie AEM Forms in einer Clusterumgebung ausführen, gelten die angezeigten Informationen für den auf der Serverliste ausgewählten Knoten.

Um die aktuellen Systeminformationen als Eigenschaftendatei zu speichern, klicken Sie auf „Speichern“.

Im rechten Bereich der Registerkarte „System“ werden die folgenden Informationen grafisch angezeigt:

* Anzahl der Auftrags- und Arbeitselemente
* Heap- und zugesicherte Heap-Auslastung
* Nicht-Heap- und zugesicherte Nicht-Heap-Auslastung

Sie können Ihren Zeiger auf der Zeitachse verschieben, um Werte für einen bestimmten Zeitpunkt abzurufen.

>[!NOTE]
>
>Die Diagrammdaten, Serverinformationswerte und die Uhrzeit werden alle 10 Minuten aktualisiert. Die Informationen werden nicht in Echtzeit angezeigt.

Im linken Bereich der Registerkarte „System“ werden die folgenden Informationen zum Server oder Knoten angezeigt:

**** Virtuelle Maschine: Java Virtual Machine (JVM)-Version auf dem Server.

**** Hersteller der virtuellen Maschine: Hersteller der JVM.

**** Virtual Machine-Version: JVM-Versionsnummer

**** Computername: Hostname des Servers, auf dem AEM Forms installiert ist.

**** Up Time: Die Zeit in Stunden und Minuten, die der Server ausgeführt wurde.

**** Just-in-time-Compiler: Der Name des verwendeten Compilers.

**** Kompilierungszeit: Die Zeit, die beim Kompilieren verbracht wurde.

**** Anzahl der Live-Threads: Die Gesamtzahl der Threads, die derzeit im AEM Forms-System vorhanden sind.

**** Anzahl Threads Spitze: Größte Anzahl Live-Threads, die je im System aufgezeichnet wurden.

**** Anzahl der geladenen Klassen: Anzahl der Klassen, die in die JVM geladen wurden.

**** Anzahl der nicht geladenen Klassen: Anzahl der Klassen, die aus der JVM entfernt wurden.

**** Mindest-Heap: Die Mindestmenge des verwendeten Heap.

**** Maximum Heap: Die maximal verwendete Heap-Menge.

**** Betriebssystemname: Der Name des Betriebssystems, das auf dem AEM Forms-Server ausgeführt wird.

**** Betriebssystemversion: Versionsnummer des Betriebssystems, das auf dem AEM Forms-Server ausgeführt wird.

**** Betriebssystem-Arch: Die Betriebssystemarchitektur, auf der die JVM ausgeführt wird.

**** Anzahl Prozessoren: Die Anzahl der Prozessoren im System.

**** Argumente der virtuellen Maschine: Das von der JVM verwendete Argument.

**** Klassenpfad: Der von der JVM verwendete Klassenpfad.

**** Bibliothekspfad: Der von der JVM verwendete Bibliothekspfad.

**** Boot-Klassen-Pfad: Der von der JVM verwendete Bootklassenpfad.

**** Anwendungsservertyp: Typ des Anwendungsservers, der zum Ausführen von AEM Forms verwendet wird.

**** Anwendungsserverversion: Versionsnummer des Anwendungsservers, der zum Ausführen von AEM Forms verwendet wird.

**** Anwendungsserver-Anbieter: Hersteller des Anwendungsservers, der zum Ausführen von AEM Forms verwendet wird.

**** Installationsdatum: Datum (im Format JJJ-MM-TT), an dem AEM Forms installiert wurde.

**** AEM Forms-Version: Version von AEM Forms, die installiert wird.

**** Patch-Version: AEM Forms-Patch-Nummer.

**** Datenbankname: Von AEM Forms verwendeter Datenbanktyp.

**** Datenbankversion: Versionsnummer der von AEM Forms verwendeten Datenbank.

**** Name des Datenbanklaufwerks: Der Name des Treibers, der von der JVM verwendet wird, um eine Verbindung zur Datenbank herzustellen.

**** Datenbanktreiberversion: Die Version des Treibers, mit dem die JVM eine Verbindung zur Datenbank herstellt.

Mit der Schaltfläche **Speichern** können Sie diese Systeminformationen in einer Eigenschaftendatei speichern.
