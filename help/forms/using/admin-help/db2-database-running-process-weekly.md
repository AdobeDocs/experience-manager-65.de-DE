---
title: "DB2&reg; Datenbank: Prozess wöchentlich ausführen"
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms DB2&reg; -Datenbank verbessern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ca2cfe35-b602-4ef8-b4e3-af846105d4de
solution: Experience Manager, Experience Manager Forms
source-git-commit: bf99ad3710638ec823d3b17967e1c750d0405c77
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 23%

---

# DB2®-Datenbank: Wöchentliche Ausführung eines Prozesses{#db-database-running-a-process-weekly}

Wenn Ihre AEM Forms DB2®-Datenbank langsam ausgeführt wird, kann die Ausführung des folgenden wöchentlichen Vorgangs die Leistung verbessern:

1. Starten Sie das DB2® Control Center:

   (Windows) Wählen Sie Start > Programme > IBM® DB2® > Allgemeine Administrationstools > Kontrollzentrum.

   (Linux® und UNIX®) Geben Sie an einer Eingabeaufforderung den `db2jcc` Befehl.

1. Klicken Sie in der Objektstruktur des DB2® Control Center auf Alle Datenbanken.
1. Klicken Sie auf die für AEM Forms erstellte Datenbank und dann auf den Ordner Tabellen .
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie dann Statistiken ausführen aus.
1. Gehen Sie zu „Statistiken“ > „Indexstatistiken“.
1. Wählen Sie „Statistik für alle Indizes sammeln“, wählen Sie „Statistik für Indizes mit erweiterter detaillierter Statistik sammeln“ und klicken Sie dann auf „OK“.

Nach Abschluss des Vorgangs wird eine entsprechende Meldung angezeigt. Schließen Sie die Meldung.
