---
title: '"Microsoft SQL Server-Datenbank : Konfiguration optimieren"'
seo-title: '"Microsoft SQL Server-Datenbank : Konfiguration optimieren"'
description: Erfahren Sie, wie Sie die Konfiguration Ihrer Microsoft SQL Server-Datenbank optimieren können.
seo-description: Erfahren Sie, wie Sie die Konfiguration Ihrer Microsoft SQL Server-Datenbank optimieren können.
uuid: 2d618aab-3c67-4edb-a28f-a20904689e6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS, SG_AEMFORMS
discoiquuid: 70559a94-42ea-411a-a32f-5f38bc17ff96
exl-id: 9c570827-86e2-47d5-b8ae-66c0767bff2e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 100%

---

# Microsoft SQL Server-Datenbank : Konfiguration optimieren {#microsoft-sql-server-database-fine-tuning-the-configuration}

Bei Verwendung von Microsoft SQL Server empfiehlt es sich, die Standardkonfigurationseinstellungen zu ändern. Klicken Sie in Oracle Enterprise Manager mit der rechten Maustaste auf den lokalen Server, um auf das Eigenschaftendialogfeld zuzugreifen.

## Arbeitsspeichereinstellungen {#memory-settings}

Ändern Sie die minimale Arbeitsspeicherzuweisung in einen möglichst großen Wert. Wenn die Datenbank auf einem gesonderten Computer ausgeführt wird, weisen Sie den gesamten Arbeitsspeicher zu. Die Standardeinstellungen weisen Arbeitsspeicher nicht optimal zu, wodurch die Leistung nahezu aller Datenbanken beeinträchtigt wird. Auf Computern in Produktionsumgebungen muss Arbeitsspeicher im höchstmöglichen Maß zugeordnet werden.

## Prozessoreinstellungen {#processor-settings}

Ändern Sie die Prozessoreinstellungen und aktivieren Sie unbedingt das Kontrollkästchen „SQL Server-Priorität unter Windows höher stufen“, damit der Server möglichst viele Zyklen nutzen kann. Die Einstellung „Windows NT-Fibers verwenden“ ist weniger wichtig, sollte aber dennoch aktiviert werden.

## Datenbankeinstellungen {#database-settings}

Ändern Sie die Datenbankeinstellungen. Die wichtigste Einstellung ist „Wiederherstellungsintervall“, das die maximale Wartezeit bis zu einer Wiederherstellung nach einem Datenbankabsturz angibt. Die Standardeinstellung ist eine Minute. Das Verwenden eines höheren Wertes (von 5 bis 15 Minuten) verbessert die Leistung, da dadurch der Server mehr Zeit hat, Änderungen aus dem Datenbankprotokoll zurück in die Datenbankdateien zu schreiben.

>[!NOTE]
>
>Diese Einstellung hat keinen negativen Einfluss auf das Transaktionsverhalten, da dadurch nur die Dauer des Zurückspielens der Protokolldatei geändert wird, das beim Systemstart erfolgen muss.

Legen Sie die Größe von „Reservierter Speicherplatz“ sowohl für die Protokoll- als auch für die Datendatei auf einen wesentlich höheren Wert fest als in der Ausgangsdatenbank. Berücksichtigen Sie, wie stark die Datenbank im Verlauf eines Jahres anwachsen kann. Im Idealfall werden die Protokoll- und Datenbankdateien einem zusammenhängenden Block zugeordnet, damit die Daten nicht fragmentiert auf dem gesamten Datenträger verteilt werden.
