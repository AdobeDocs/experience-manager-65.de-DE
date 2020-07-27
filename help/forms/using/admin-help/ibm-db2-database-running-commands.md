---
title: '"IBM DB2-Datenbank: Befehle zur regelmäßigen Wartung ausführen"'
seo-title: '"IBM DB2-Datenbank: Befehle zur regelmäßigen Wartung ausführen"'
description: Das Dokument listet IBM DB2-Befehle auf, die für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen werden.
seo-description: Das Dokument listet IBM DB2-Befehle auf, die für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen werden.
uuid: 235d59df-b9b9-4770-8b7d-00713701c3c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a62b68b4-7735-49b1-8938-f0d9e4c4a051
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 89%

---


# IBM DB2-Datenbank: Befehle zur regelmäßigen Wartung ausführen {#ibm-db-database-running-commands-for-regular-maintenance}

Die folgenden IBM DB2-Befehle werden für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen. Detaillierte Informationen zur Wartung und Leistungsoptimierung der DB2-Datenbank finden Sie im *IBM DB2 Administration Guide*.

* **runstats:** Dieser Befehl aktualisiert Statistiken, die die physischen Merkmale einer Datenbanktabelle sowie der dazugehörigen Indizes beschreiben. Von AEM Forms generierte dynamische SQL-Anweisungen verwenden automatisch diese aktualisierten Statistiken. Für statische SQL-Anweisungen, die innerhalb einer Datenbank erstellt wurden, muss jedoch auch der Befehl `db2rbind` ausgeführt werden.
* **db2rbind:** Dieser Befehl bindet alle Pakete in der Datenbank erneut. Rufen Sie diesen Befehl nach Ausführung des Dienstprogramms `runstats` aus, um alle Pakete in der Datenbank erneut zu überprüfen.
* **REORG-Tabelle oder -Index:** Mit diesem Befehl wird überprüft, ob eine Neuorganisation bestimmter Tabellen und Indizes erforderlich ist.

   Da Datenbanken anwachsen und sich verändern, ist die Neuberechnung von Tabellenstatistiken wichtig für die Datenbankleistung und muss deshalb regelmäßig durchgeführt werden. Diese Befehle können entweder manuell mithilfe von Skripten oder über einen Cron-Auftrag ausgeführt werden.

>[!NOTE]
>
>Vor Ausführung des Befehls `runstats` ist es erforderlich, dass die Datenbank Daten enthält und mindestens eine Synchronisierung erfolgt ist.

Bei einer kleinen Datenbank (z. B. 10000 Benutzer oder 2500 Gruppen) reicht es aus, den Befehl `runstats` aufzurufen, um die für Synchronisierungen erforderliche Zeit zu reduzieren.

Führen Sie bei größeren Datenbanken (z. B. 100000 Benutzer oder 10000 Gruppen) den Befehl `reorg` aus, bevor Sie den Befehl `runstats` ausführen.

## Befehl „runstats“ auf die AEM Forms-Datenbank anwenden {#use-the-runstats-command-on-your-aem-forms-database}

Führen Sie den Befehl `runstats` für die folgenden AEM Forms-Datenbanktabellen und -indizes aus.

>[!NOTE]
>
>Der Befehl `runstats` muss nur während der ersten Datenbanksynchronisation ausgeführt werden. Er sollte jedoch während dieses Prozesses zweimal ausgeführt werden: einmal während der Synchronisation von „Benutzer und Gruppen“ und anschließend während der Synchronisation von „Gruppenmitglieder“. Stellen Sie sicher, dass das Skript bei jeder Ausführung vollständig ausgeführt wird.

Die ordnungsgemäße Syntax und Verwendung wird in der Dokumentation des Datenbankherstellers beschrieben. Below, `<schema>` is used to denote the schema that is associated with your DB2 user name. Wenn Sie eine einfache DB2-Standardinstallation haben, ist dies der Datenbankschemaname.

```sql
     TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALGROUPENTITY FOR INDEXES ALL
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY FOR INDEXES ALL
```

## Befehl „reorg“ auf die AEM Forms-Datenbank anwenden {#run-the-reorg-command-on-your-aem-forms-database}

Führen Sie den Befehl `reorg` für die folgenden AEM Forms-Datenbanktabellen und -indizes aus. Die ordnungsgemäße Syntax und Verwendung wird in der Dokumentation des Datenbankherstellers beschrieben.

```sql
     TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
 
     TABLE <schema>.EDCPRINCIPALENTITY
 
     TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALEMAILALIASENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALUSERENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGROUPENTITY
 
     INDEXES ALL FOR TABLE <schema>.EDCPRINCIPALGRPCTMNTENTITY
```

