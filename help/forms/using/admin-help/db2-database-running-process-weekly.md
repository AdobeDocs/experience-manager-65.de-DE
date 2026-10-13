---
title: 'DB2&reg;-Datenbank: Einen Prozess wöchentlich ausführen'
description: Erfahren Sie, wie Sie die Leistung Ihrer AEM Forms DB2&reg;-Datenbank verbessern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ca2cfe35-b602-4ef8-b4e3-af846105d4de
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 85%
---
# DB2®-Datenbank: Wöchentliche Ausführung eines Prozesses{#db-database-running-a-process-weekly}

Wenn Ihre AEM Forms-DB2®-Datenbank langsam wird, kann die Ausführung des folgenden wöchentlichen Prozesses die Leistung verbessern:

1. Starten Sie das DB2® Control Center:

   (Windows) Wählen Sie „Start“ > „Programme“ > „IBM DB2®“ > „Allgemeine Administrations-Tools“ > „Control Center“.

   (Linux® und UNIX®) Geben Sie in einer Eingabeaufforderung den Befehl `db2jcc` ein.

1. Klicken Sie in der Objektstruktur des DB2® Control Center auf „Alle Datenbanken“.
1. Klicken Sie auf die Datenbank, die Sie für AEM Forms erstellt haben, und klicken Sie auf den Ordner „Tabellen“.
1. Wählen Sie alle Datenbanktabellen im Inhaltsbereich aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie „Statistiken ausführen“.
1. Gehen Sie zu „Statistiken“ > „Indexstatistiken“.
1. Wählen Sie „Statistik für alle Indizes sammeln“, wählen Sie „Statistik für Indizes mit erweiterter detaillierter Statistik sammeln“ und klicken Sie dann auf „OK“.

Nach Abschluss des Vorgangs wird eine entsprechende Meldung angezeigt. Schließen Sie die Meldung.
