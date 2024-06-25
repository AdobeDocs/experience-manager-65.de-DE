---
title: Anzeigen von Systeminformationen
description: Erfahren Sie, wie Sie Diagramme zur Ressourcenüberwachung und Informationen über den Server anzeigen, der AEM Forms ausführt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 27a2e81c-47b0-4de8-95bd-7cb34b9450da
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '541'
ht-degree: 100%

---

# Anzeigen von Systeminformationen {#view-system-information}

Auf der Registerkarte „System“ werden Diagramme zur Ressourcenüberwachung und Informationen über den Server angezeigt, der AEM Forms ausführt.  Klicken Sie in der Administrationskonsole in der rechten oberen Ecke der Seite auf „Health Monitor“, um diese Informationen anzuzeigen.  Wenn Sie AEM Forms in einer Cluster-Umgebung ausführen, gelten die angezeigten Informationen für den auf der Server-Liste ausgewählten Knoten.

Um die aktuellen Systeminformationen als Eigenschaftendatei zu speichern, klicken Sie auf „Speichern“.

Im rechten Bereich der Registerkarte „System“ werden die folgenden Informationen grafisch angezeigt:

* Anzahl der Auftrags- und Arbeitselemente
* Heap- und zugesicherte Heap-Auslastung
* Nicht-Heap- und zugesicherte Nicht-Heap-Auslastung

Sie können Ihren Zeiger auf der Zeitachse verschieben, um Werte für einen bestimmten Zeitpunkt abzurufen.

>[!NOTE]
>
>Die Diagrammdaten, Werte zu Server-Informationen und die Uhrzeit werden alle 10 Minuten aktualisiert.  Die Informationen werden nicht in Echtzeit angezeigt.

Im linken Bereich der Registerkarte „System“ werden die folgenden Informationen zum Server oder Knoten angezeigt:

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
