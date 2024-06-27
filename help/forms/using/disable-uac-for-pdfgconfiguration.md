---
title: Deaktivieren von UAC für eine PDFG-Konfiguration, die sowohl für JEE als auch für OSGI gilt
description: Erfahren Sie, mit welchen Schritten Sie UAC für die PDFG-Konfiguration deaktivieren können, um die Konvertierung von Word in PDF zu korrigieren.
exl-id: 785b7bb4-7158-45ea-a1e5-eebf3dc3ebc3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '265'
ht-degree: 100%

---

# Konvertieren von Word- oder Excel-Dateien in PDF ist unter Windows Server nicht möglich {#unable-to-convert-word-excel-files-PDF}

## Problem {#issue}

Wenn Benutzende versuchen, Word- oder Excel-Dateien unter Microsoft® Windows Server in PDF zu konvertieren, tritt folgender Fehler auf:

*Fehlermeldung des primären Konverters:*
*ALC-PDG-015-003-Das System kann die Eingabedatei nicht öffnen. Senden Sie Ihre Datei erneut ab oder kontaktieren Sie Ihren System-Admin.*


## Lösung {#solution}

Gehen Sie folgendermaßen vor:

1. Sie können auf das Systemkonfigurationsprogramm zugreifen, indem Sie zu **[!UICONTROL Start > Ausführen]** wechseln und dann **[!UICONTROL MSCONFIG]** eingeben.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Tools]**, blättern Sie nach unten und wählen Sie **[!UICONTROL Einstellungen für Benutzerkontensteuerung ändern]**. Klicken Sie auf **[!UICONTROL Starten]**, um den Befehl in einem neuen Fenster auszuführen.
1. Stellen Sie den Schieberegler auf Nie benachrichtigen ein. Schließen Sie nach Abschluss des Vorgangs das Befehlsfenster und das Fenster für die Systemkonfiguration.
1. Überprüfen Sie, ob die Registrierungseinstellung für UAC auf 0 (Null) gesetzt ist. Führen Sie die folgenden Schritte zur Überprüfung durch:

   1. Microsoft® empfiehlt, eine Sicherungskopie der Registrierung zu erstellen, bevor Sie sie ändern. Detaillierte Informationen zu den Schritten erfahren Sie unter [Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/de-de/help/322756).
   1. Öffnen Sie den Microsoft® Windows Registrierungs-Editor. Um den Registrierungs-Editor zu öffnen, gehen Sie zu „Start“ > „Ausführen“, geben Sie „regedit“ ein und klicken Sie auf „OK“.
   1. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Stellen Sie sicher, dass der Wert von EnableLUA auf 0 (null) gesetzt ist. 
   1. Stellen Sie sicher, dass der Wert **EnableLUA** auf 0 (null) gesetzt ist. Wenn der Wert ungleich 0 ist, ändern Sie den Wert auf 0. Schließen Sie den Registrierungseditor.

1. Starten Sie den Computer neu.

## Gilt für {#appliesto}

Diese Lösung gilt für AEM Forms auf JEE Server und AEM Forms auf OSGi Server.
