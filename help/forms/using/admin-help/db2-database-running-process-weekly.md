---
title: "Datenbank DB2: Einen Prozess wöchentlich ausführen"
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms DB2-Datenbank verbessern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ca2cfe35-b602-4ef8-b4e3-af846105d4de
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 26%

---

# DB2-Datenbank: Einen Prozess wöchentlich ausführen{#db-database-running-a-process-weekly}

Wenn Ihre AEM Forms DB2-Datenbank langsam ausgeführt wird, kann die Ausführung des folgenden wöchentlichen Prozesses die Leistung verbessern:

1. Starten Sie das DB2 Control Center:

   (Windows) Wählen Sie Start > Programme > IBM DB2 > Allgemeine Administrationstools > Kontrollzentrum.

   (Linux und UNIX) Geben Sie an einer Eingabeaufforderung den Befehl `db2jcc` ein.

1. Klicken Sie in der Objektstruktur des DB2 Control Center auf Alle Datenbanken.
1. Klicken Sie auf die Datenbank, die Sie für AEM Formulare erstellt haben, und klicken Sie auf den Ordner Tabellen .
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie &quot;Run Statistics&quot;.
1. Gehen Sie zu Statistiken > Indexstatistiken .
1. Wählen Sie &quot;Collect Statistics For All Indexes&quot;, &quot;Collect Statistics For Indexes With Extended Detailed Statistics&quot;und klicken Sie auf &quot;OK&quot;.

Nach Abschluss des Vorgangs wird eine Meldung angezeigt. Schließen Sie die Meldung.
