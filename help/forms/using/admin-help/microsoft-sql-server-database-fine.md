---
title: "Microsoft SQL Server-Datenbank: Konfiguration optimieren"
description: Erfahren Sie, wie Sie die Konfiguration Ihrer Microsoft SQL Server-Datenbank anpassen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS, SG_AEMFORMS
exl-id: 9c570827-86e2-47d5-b8ae-66c0767bff2e
source-git-commit: 10227bcfcfd5a9b0f126fee74dce6ec7842f5e95
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 4%

---

# Microsoft SQL Server-Datenbank: Konfiguration optimieren {#microsoft-sql-server-database-fine-tuning-the-configuration}

Bei Verwendung von Microsoft SQL Server sollten Sie die Standardkonfigurationseinstellungen ändern. Klicken Sie mit der rechten Maustaste auf den lokalen Server in Oracle Enterprise Manager, um auf das Dialogfeld &quot;Eigenschaften&quot;zuzugreifen.

## Speichereinstellungen {#memory-settings}

Ändern Sie die minimale Speicherzuordnung in eine möglichst große Zahl. Wenn die Datenbank auf einem separaten Computer ausgeführt wird, verwenden Sie den gesamten Speicher. Die Standardeinstellungen weisen nicht aggressiv Speicher zu, was die Leistung in fast allen Datenbanken behindert. Sie sollten am aggressivsten sein, wenn es darum geht, Speicher auf Produktionsmaschinen zuzuweisen.

## Prozessoreinstellungen {#processor-settings}

Ändern Sie die Prozessoreinstellungen und aktivieren Sie vor allem das Kontrollkästchen SQL Server Priority On Windows aktivieren , damit der Server so viele Zyklen wie möglich verwendet. Die Einstellung &quot;NT Fibers verwenden&quot;ist weniger wichtig, Sie können sie jedoch auch auswählen.

## Datenbankeinstellungen {#database-settings}

Ändern Sie die Datenbankeinstellungen. Die wichtigste Einstellung ist das Wiederherstellungsintervall , das die maximale Wartezeit auf die Wiederherstellung nach einem Absturz angibt. Die Standardeinstellung ist eine Minute. Die Verwendung eines größeren Werts von 5 bis 15 Minuten verbessert die Leistung, da der Server mehr Zeit hat, Änderungen aus dem Datenbankprotokoll wieder in die Datenbankdateien zu schreiben.

>[!NOTE]
>
>Diese Einstellung beeinträchtigt das Transaktionsverhalten nicht, da nur die Länge der Wiederholung der Protokolldatei geändert wird, die beim Start durchgeführt werden muss.

Legen Sie die Größe von &quot;Zugewiesener Speicherplatz&quot;sowohl für das Protokoll als auch für die Datendatei auf einen viel größeren Wert fest als die Anfangsdatenbank. Überlegen Sie, wie stark die Datenbank im Laufe eines Jahres wachsen kann. Idealerweise werden die Protokoll- und Datendateien zusammenhängend zugeordnet, sodass die Daten nicht auf der gesamten Festplatte fragmentiert werden.
