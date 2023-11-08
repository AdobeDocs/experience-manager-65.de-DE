---
title: Anzeigen von Systeminformationen
seo-title: View system information
description: Erfahren Sie, wie Sie Diagramme zur Ressourcenüberwachung und Informationen über den Server anzeigen können, auf dem AEM Formulare ausgeführt werden.
seo-description: Learn how you can view resource monitoring charts and information about the server that is running AEM forms.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
exl-id: 27a2e81c-47b0-4de8-95bd-7cb34b9450da
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 62%

---

# Anzeigen von Systeminformationen {#view-system-information}

Auf der Registerkarte System werden Diagramme zur Ressourcenüberwachung und Informationen über den Server angezeigt, auf dem AEM Formulare ausgeführt werden. Um auf diese Informationen zuzugreifen, klicken Sie in Administration Console oben rechts auf der Seite auf Health Monitor . Wenn Sie AEM Formulare in einer Clusterumgebung ausführen, werden die angezeigten Informationen für den Knoten angezeigt, der aus der Serverliste ausgewählt wurde.

Um die aktuellen Systeminformationen als Eigenschaftendatei zu speichern, klicken Sie auf Speichern.

Im rechten Bereich der Registerkarte System werden die folgenden Informationen grafisch dargestellt:

* Auftrags- und Arbeitzählungselemente
* Heap- und zugesicherte Heap-Nutzung
* Nicht-Heap- und zugesicherte Nicht-Heap-Nutzung

Sie können Ihren Mauszeiger auf die Timeline ziehen, um Werte für einen bestimmten Zeitpunkt abzurufen.

>[!NOTE]
>
>Die Diagrammdaten, Server-Informationswerte und die Uhrzeit werden alle 10 Minuten aktualisiert. Die Informationen werden nicht in Echtzeit angezeigt.

Im linken Bereich der Registerkarte System werden die folgenden Informationen zum Server oder Knoten angezeigt:

**Virtual Machine:** Version von Java Virtual Machine (JVM) auf dem Server.

**Anbieter der virtuellen Maschine:** Hersteller von JVM.

**Version der virtuellen Maschine:** JVM-Versionsnummer

**Maschinenname:** Hostname des Servers, auf dem AEM Forms installiert ist.

**Betriebszeit:** Die Zeit in Stunden und Minuten, die der Server schon ausgeführt wird.

**Just-In-Time Compiler:** Der Name des Compilers, der verwendet wird.

**Kompilierungsdauer:** Die zum Kompilieren aufgewendete Zeit.

**Anzahl der Live-Threads:** Die Gesamtzahl der Threads, die derzeit im AEM Forms-System vorhanden sind.

**Spitzenwert der Anzahl von Threads:** Größte Anzahl Live-Threads, die je im System erfasst wurde.

**Anzahl geladener Klassen:** Anzahl der Klassen, die in JVM geladen wurden.

**Anzahl entfernter Klassen:** Anzahl der Klassen, die aus JVM entfernt wurden.

**Mindest-Heap-Größe:** Die Mindestgröße des verwendeten Heap.

**Maximale Heap-Größe:** Die maximale Größe des verwendeten Heap.

**Betriebssystemname:** Der Name des Betriebssystems, das auf dem AEM Forms-Server ausgeführt wird.

**Betriebssystemversion:** Versionsnummer des Betriebssystems, das auf dem AEM Forms-Server ausgeführt wird.

**Betriebssystem-Arch:** Die Betriebssystemarchitektur, auf der JVM ausgeführt wird.

**Anzahl der Prozessoren:** Die Anzahl der Prozessoren im System.

**Argumente der virtuellen Maschine:** Das von JVM verwendete Argument.

**Klassenpfad:** Der von JVM verwendete Klassenpfad.

**Bibliothekspfad:** Der von JVM verwendete Bibliothekspfad.

**Pfad der Boot-Klasse:** Der Pfad für die von der JVM verwendete Boot-Klasse.

**Anwendungsservertyp:** Typ des Anwendungsservers, der zum Ausführen AEM Forms verwendet wird.

**Anwendungsserverversion:** Versionsnummer des Anwendungsservers, der zum Ausführen von AEM Forms verwendet wird.

**Anwendungsserveranbieter:** Hersteller des Anwendungsservers, der zum Ausführen von AEM Forms verwendet wird.

**Installationsdatum:** Datum (im Format jjjj-mm-tt), an dem AEM Forms installiert wurde.

**AEM Forms-Version:** Installierte Version von AEM Forms.

**Patch-Version:** Patch-Nummer von AEM Forms.

**Datenbankname:** Von AEM Forms verwendeter Datenbanktyp.

**Datenbankversion:** Versionsnummer der von AEM Forms verwendeten Datenbank.

**Datenbanktreibername:** Der Name des Treibers, der von JVM verwendet wird, um eine Verbindung zur Datenbank herzustellen.

**Datenbanktreiberversion**: Die Version des Treibers, der von JVM verwendet wird, um eine Verbindung zur Datenbank herzustellen.

Mit der Schaltfläche **Speichern** können Sie diese Systeminformationen in einer Eigenschaftendatei speichern.
