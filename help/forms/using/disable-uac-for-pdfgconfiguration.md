---
title: UAC für PDFG-Konfiguration deaktivieren, die sowohl für JEE als auch für OSGI gilt
description: Schritte zum Deaktivieren der Benutzerkontensteuerung für die PDFG-Konfiguration
source-git-commit: f6dcb488c64dad2d65facc0e8e1d6685b7375a08
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 57%

---

# Konvertieren von Word- oder Excel-Dateien in PDF unter Windows Server nicht möglich {#unable-to-convert-word-excel-files-PDF}

## Problem {#issue}

Wenn der Benutzer versucht, Word- oder Excel-Dateien auf Microsoft Windows Server in PDF zu konvertieren, tritt folgender Fehler auf:

*Fehlermeldung des primären Konverters: ALC-PDG-015-003-Das System kann die Eingabedatei nicht öffnen. Senden Sie Ihre Datei erneut oder kontaktieren Sie Ihren Systemadministrator.*


## Lösung {#solution}

Führen Sie zur Behebung dieses Problems folgende Schritte durch:
1. Sie können auf das Systemkonfigurationsprogramm zugreifen, indem Sie zu **[!UICONTROL Start > Ausführen]** wechseln und dann **[!UICONTROL MSCONFIG]** eingeben.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Tools]**, blättern Sie nach unten und wählen Sie **[!UICONTROL Einstellungen für Benutzerkontensteuerung ändern]**. Klicken Sie auf **[!UICONTROL Starten]**, um den Befehl in einem neuen Fenster auszuführen.
1. Stellen Sie den Schieberegler auf Nie benachrichtigen ein. Schließen Sie nach Abschluss des Vorgangs das Befehlsfenster und das Fenster für die Systemkonfiguration.
1. Überprüfen Sie, ob die Registrierungseinstellung für UAC auf 0 (Null) gesetzt ist. Führen Sie die folgenden Schritte zur Überprüfung durch:

   1. Microsoft® empfiehlt, die Registrierung zu sichern, bevor Sie sie ändern. Detaillierte Informationen zu den Schritten erfahren Sie unter [Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/de-de/help/322756).
   1. Öffnen Sie den Microsoft® Windows Registry-Editor. Um den Registrierungs-Editor zu öffnen, gehen Sie zu „Start“ > „Ausführen“, geben Sie regedit ein und klicken Sie auf „OK“.
   1. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Stellen Sie sicher, dass der Wert EnableLUA auf 0 (null) gesetzt ist. 
   1. Stellen Sie sicher, dass der Wert **EnableLUA** auf 0 (null) gesetzt ist. Wenn der Wert ungleich 0 ist, ändern Sie den Wert auf 0. Schließen Sie den Registrierungseditor.

1. Starten Sie den Computer neu.

## Gilt für {#appliesto}

Diese Lösung gilt für Folgendes:
* AEM Forms on JEE-Server
* AEM Forms auf OSGi-Server