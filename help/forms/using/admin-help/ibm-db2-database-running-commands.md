---
title: "IBM DB2-Datenbank: Befehle zur regelmäßigen Wartung ausführen"
description: Das Dokument listet IBM DB2-Befehle auf, die für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7a4281e7-1544-473a-a471-e9a4c2819a58
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '391'
ht-degree: 100%

---

# IBM DB2-Datenbank: Ausführen von Befehlen zur regelmäßigen Wartung {#ibm-db-database-running-commands-for-regular-maintenance}

Die folgenden IBM DB2-Befehle werden für die regelmäßige Wartung Ihrer AEM Forms-Datenbank empfohlen. Detaillierte Informationen zur Wartung und Leistungsoptimierung Ihrer DB2-Datenbank finden Sie unter *IBM DB2-Administrationshandbuch*.

* **runstats:** Dieser Befehl aktualisiert Statistiken, die die physischen Merkmale einer Datenbanktabelle sowie der dazugehörigen Indizes beschreiben. Von AEM Forms generierte dynamische SQL-Anweisungen verwenden automatisch diese aktualisierten Statistiken. Für statische SQL-Anweisungen, die innerhalb einer Datenbank erstellt wurden, muss jedoch auch der Befehl `db2rbind` ausgeführt werden.
* **db2rbind**: Dieser Befehl bindet alle Pakete in der Datenbank erneut. Rufen Sie diesen Befehl nach Ausführung des Dienstprogramms `runstats` aus, um alle Pakete in der Datenbank erneut zu überprüfen.
* **reorg table oder index**: Dieser Befehl überprüft, ob eine Reorganisation von Tabellen oder Indizes erforderlich ist.

  Da Datenbanken anwachsen und sich verändern, ist die Neuberechnung von Tabellenstatistiken wichtig für die Datenbankleistung und muss deshalb regelmäßig durchgeführt werden. Diese Befehle können entweder manuell mithilfe von Skripten oder mithilfe eines Cron-Auftrags ausgeführt werden.

>[!NOTE]
>
>Vor Ausführung des Befehls `runstats` ist es erforderlich, dass die Datenbank Daten enthält und mindestens eine Synchronisierung erfolgt ist.

Bei einer kleinen Datenbank (z. B. 10000 Benutzer oder 2500 Gruppen) reicht es aus, den Befehl `runstats` aufzurufen, um die für Synchronisierungen erforderliche Zeit zu reduzieren.

Führen Sie bei größeren Datenbanken (z. B. 100000 Benutzer oder 10000 Gruppen) den Befehl `reorg` aus, bevor Sie den Befehl `runstats` ausführen.

## Befehl „runstats“ auf die AEM Forms-Datenbank anwenden {#use-the-runstats-command-on-your-aem-forms-database}

Führen Sie den Befehl `runstats` für die folgenden AEM Forms-Datenbanktabellen und -indizes aus.

>[!NOTE]
>
>Der Befehl `runstats` muss nur während der ersten Datenbanksynchronisation ausgeführt werden. Er sollte jedoch während dieses Prozesses zweimal ausgeführt werden: einmal während der Synchronisation von „Benutzende und Gruppen“ und anschließend während der Synchronisation von „Gruppenmitglieder“. Stellen Sie sicher, dass das Skript bei jeder Ausführung vollständig ausgeführt wird.

Die ordnungsgemäße Syntax und Verwendung wird in der Dokumentation des Datenbankherstellers beschrieben. Im Folgenden wird `<schema>` verwendet, um das Schema zu bezeichnen, das Ihrem DB2-Benutzernamen zugeordnet ist. Wenn Sie eine einfache DB2-Standardinstallation haben, ist dies der Datenbankschemaname.

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

## Anwenden des Befehls „reorg“ auf die AEM Forms-Datenbank {#run-the-reorg-command-on-your-aem-forms-database}

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
