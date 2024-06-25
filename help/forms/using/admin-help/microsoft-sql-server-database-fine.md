---
title: "Microsoft SQL Server-Datenbank: Konfiguration optimieren"
description: Erfahren Sie, wie Sie die Konfiguration Ihrer Microsoft SQL Server-Datenbank optimieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS, SG_AEMFORMS
exl-id: 9c570827-86e2-47d5-b8ae-66c0767bff2e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '295'
ht-degree: 100%

---

# Microsoft SQL Server-Datenbank: Konfiguration optimieren {#microsoft-sql-server-database-fine-tuning-the-configuration}

Bei Verwendung von Microsoft SQL Server sollten Sie die Standardkonfigurationseinstellungen ändern. Klicken Sie in Oracle Enterprise Manager mit der rechten Maustaste auf den lokalen Server, um auf das Eigenschaftendialogfeld zuzugreifen.

## Speichereinstellungen {#memory-settings}

Ändern Sie die minimale Arbeitsspeicherzuweisung in einen möglichst großen Wert. Wenn die Datenbank auf einem separaten Computer ausgeführt wird, weisen Sie den gesamten Arbeitsspeicher zu. Die Standardeinstellungen weisen Arbeitsspeicher nicht offensiv zu, wodurch die Leistung nahezu aller Datenbanken beeinträchtigt wird. Auf Computern in Produktionsumgebungen muss Arbeitsspeicher im höchstmöglichen Maß zugeordnet werden.

## Prozessoreinstellungen {#processor-settings}

Ändern Sie die Prozessoreinstellungen und aktivieren Sie unbedingt das Kontrollkästchen „SQL Server-Priorität unter Windows höher stufen“, damit der Server möglichst viele Zyklen nutzen kann. Die Einstellung „Windows NT-Fibers verwenden“ ist weniger wichtig, sollte aber dennoch aktiviert werden.

## Datenbankeinstellungen {#database-settings}

Ändern Sie die Datenbankeinstellungen. Die wichtigste Einstellung ist „Wiederherstellungsintervall“. Damit wird die maximale Wartezeit bis zur Wiederherstellung nach einem Datenbankabsturz angegeben. Die Standardeinstellung ist eine Minute. Ein höherer Wert (von 5 bis 15 Minuten) verbessert die Leistung, da dadurch der Server mehr Zeit hat, Änderungen aus dem Datenbankprotokoll zurück in die Datenbankdateien zu schreiben.

>[!NOTE]
>
>Diese Einstellung hat keinen negativen Einfluss auf das Transaktionsverhalten, da dadurch nur die Dauer des Zurückspielens der Protokolldatei geändert wird, das beim Systemstart erfolgen muss.

Legen Sie die Größe von „Reservierter Speicherplatz“ sowohl für die Protokoll- als auch für die Datendatei auf einen wesentlich höheren Wert fest als in der Ausgangsdatenbank. Berücksichtigen Sie, wie stark die Datenbank im Verlauf eines Jahres anwachsen kann. Im Idealfall werden die Protokoll- und Datenbankdateien einem zusammenhängenden Block zugeordnet, damit die Daten nicht fragmentiert auf dem gesamten Datenträger verteilt werden.
