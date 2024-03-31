---
title: Synchronisieren von Verzeichnissen
description: Erfahren Sie, wie Sie die User Management-Datenbank mit Änderungen an den Quellordner-Servern mithilfe einer manuellen oder geplanten Synchronisierung synchronisieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: cb642289-4137-4ba7-8bde-0e458c8c94fe
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 100%

---

# Synchronisieren von Verzeichnissen {#synchronizing-directories}

Für die Synchronisierung von Domains haben Sie die Wahl zwischen manueller und geplanter Synchronisierung. Bei *der manuellen Synchronisierung werden* ausgewählte Domains synchronisiert. Die *geplante Synchronisierung* synchronisiert alle Domains.

Die Ordnersynchronisierung wird verwendet, um Details von den Ordner-Servern, die Sie in Ihren Ordnereinstellungen angegeben haben, in die User Management-Datenbank zu ziehen. Später können Sie auch eine manuelle Synchronisierung durchführen, wenn Änderungen oder Aktualisierungen auf den Ordner-Servern auftreten. Beispielsweise können Sie eine manuelle Synchronisierung durchführen, wenn Benutzende und Gruppen hinzugefügt oder Änderungen am Benutzerkonto vorgenommen werden.

Sie können auch einen täglichen Synchronisierungszeitplan festlegen, um die User Management-Datenbank automatisch mit Änderungen oder Aktualisierungen an den Quellordner-Servern zu synchronisieren. Dieser Prozess verwendet jedoch Netzwerk- und Server-Ressourcen. Wählen Sie Zeiträume mit geringer Auslastung aus und vermeiden Sie die Planung unnötiger Synchronisierungen, die System- und Netzwerkressourcen binden. Um unnötige Synchronisierungen zu minimieren, verwenden Sie stattdessen die Option zur sofortigen Synchronisierung.

Sie können auch angeben, ob ein Push von Benutzer- und Gruppeninformationen in Adobe LiveCycle Content Services 9 (nicht mehr unterstützt) ausgeführt wird, wenn Domains synchronisiert werden.

>[!NOTE]
>
>Erstellen Sie nicht mehrere lokale Benutzende und Gruppen, während eine LDAP-Ordnersynchronisierung läuft. Wird dies dennoch versucht, können Fehler auftreten.

>[!NOTE]
>
>Wird der Domain-Namenssynchronisierungsprozess unterbrochen (z. B. wenn der Anwendungsserver während des Prozesses heruntergefahren wird), warten Sie kurze Zeit, bevor Sie die die Synchronisierung der Domain erneut versuchen. Um den Status der Synchronisierung auszuwerten, sehen Sie sich den Status an. Falls User Management vor dem Herunterfahren eine Sperre aktiviert hatte, warten Sie 10 Minuten nach dem Neustart des Servers bis zur Freigabe der Sperre. Lautet der Synchronisierungsstatus „Wird ausgeführt“, obwohl die Synchronisierung unterbrochen oder angehalten wurde, unternimmt User Management nach 3 Minuten einen erneuten Versuch. Nach drei fehlgeschlagenen Versuchen deklariert User Management die Synchronisation als fehlgeschlagen und gibt die Sperre frei.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content-Management-System, das mit LiveCycle installiert wird. Es ermöglicht Benutzenden, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe [Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).

## Aktivieren der Delta-Ordnersynchronisierung {#enable-delta-directory-synchronization}

Die Delta-Ordnersynchronisierung verbessert die Effizienz der Ordnersynchronisierung. Wenn die Delta-Ordnersynchronisierung aktiviert ist, synchronisiert User Management nur Benutzende und Gruppen, die seit der letzten Synchronisierung hinzugefügt oder aktualisiert wurden.

Das User Management führt die folgenden Schritte aus, wenn die Delta-Ordnersynchronisierung aktiviert ist:

* Abruf aller Benutzenden von den Ordner-Servern, aber Aktualisierung der User Management-Datenbank nur mit den Benutzenden, deren Zeitstempel sich geändert hat.
* Abruf aller Gruppen, aber Aktualisierung der User Management-Datenbank nur mit den Gruppen, deren Zeitstempel sich geändert hat.
* Abruf der Gruppenmitglieder nur für die Gruppen, deren Zeitstempel sich geändert haben, und Aktualisierung der User Management-Datenbank mit diesen Informationen.

>[!NOTE]
>
>Benutzende und Gruppen, die aus dem Ordner entfernt wurden, werden erst dann aus der User Management-Datenbank gelöscht, wenn Sie eine vollständige Ordnersynchronisierung durchführen.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Aktivieren Sie unter „Delta-Synchronisation“ das Kontrollkästchen und klicken Sie auf „Speichern“.
1. Bearbeiten Sie die Ordnereinstellungen für jede Unternehmens-Domain, die die Delta-Ordnersynchronisierungsfunktion verwenden soll. Suchen Sie auf der Seite „Benutzereinstellungen“ und auf der Seite „Gruppeneinstellungen“ die Einstellung „Zeitstempel ändern“ und geben Sie den Wert `modify TimeStamp` ein. Weitere Einzelheiten über das Bearbeiten von Unternehmens-Domains finden Sie unter [Bestehende Domains bearbeiten und konvertieren](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).

## Aktivieren oder Deaktivieren der detaillierten Protokollierung während der Synchronisierung {#enable-or-disable-detailed-logging-during-synchronization}

Standardmäßig protokolliert User Management während des Synchronisierungsprozesses detaillierte Statistiken.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Deaktivieren Sie unter „Protokollierung der Synchronisationsstatistiken“ das Kontrollkästchen, um die detaillierte Protokollierung zu deaktivieren, oder aktivieren Sie das Kontrollkästchen, um die detaillierte Protokollierung zu aktivieren. Klicken Sie dann auf „Speichern“.

## Konfigurieren der Wiederholungsoptionen für die Ordnersynchronisierung {#configure-the-directory-synchronization-retry-option}

Sie können das User Management so konfigurieren, dass regelmäßige Prüfungen auf fehlgeschlagene Versuche zur Ordnersynchronisierung erfolgen. User Management versucht dann, die fehlgeschlagenen Synchronisierungen fertigzustellen.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Geben Sie unter „Synch Finisher Cron Expression“ einen Cron-Ausdruck ein, der das Intervall, in dem User Management die fehlgeschlagenen Synchronisierungen erneut auszuführen versucht, angibt. Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Vorgangsplanungssystem Quartz, Version 1.4.0.

   Der Standardwert ist 0 0/13 &amp;ast; ? &amp;ast;, was bedeutet, dass die Prüfung alle 13 Minuten durchgeführt wird.

## Manuelles Synchronisieren von Verzeichnissen {#manually-synchronize-directories}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. (Optional) Um Benutzer- und Gruppeninformationen im Push-Verfahren an Content Services (veraltet) zu senden, wählen Sie die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“ aus. Diese Option gilt auch, wenn neue Benutzende und Gruppen über die Seite „Benutzer und Gruppen“ hinzugefügt werden.
1. Aktivieren Sie die Kontrollkästchen der zu synchronisierenden Unternehmens-Domains und klicken Sie auf „Jetzt synchronisieren“.

   Wenn Sie mehrere Domains auswählen, wird die Domain-Synchronisierung für alle Domains gleichzeitig ausgeführt. Wählen Sie die Domains dagegen einzeln aus, wird nur jeweils eine Domain-Synchronisierung ausgeführt.

## Planen der Verzeichnissynchronisierung {#schedule-directory-synchronization}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. So planen Sie die Synchronisierung:

   * Wählen Sie zum Aktivieren der automatischen täglichen Synchronisierung unter „Zeitplanung“ die Option „Häufigkeit“ aus. Wählen Sie aus der Liste die Option „Täglich“ aus und geben Sie in das entsprechende Feld die Zeit im 24-Stunden-Format ein. Wenn Sie die Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck konvertiert, der im Feld „Cron-Ausdruck“ angezeigt wird.
   * Um die Synchronisierung für einen bestimmten Tag der Woche bzw. des Monats oder in einem bestimmten Monat zu planen, wählen Sie „Cron-Ausdruck“ aus und geben Sie den entsprechenden Ausdruck in das Feld ein. Sie könnten die Synchronisierung beispielsweise für 1:30 Uhr am letzten Freitag im Monat planen. 

Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Vorgangsplanungssystem Quartz, Version 1.4.0.

* Zum Ausschalten der automatischen Synchronisierung wählen Sie „Häufigkeit“ und anschließend in der Liste die Option „Nie“ aus.
* (Optional) Um Benutzer- und Gruppeninformationen im Push-Verfahren an Content Services (veraltet) zu senden, wählen Sie die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“ aus. Diese Option gilt auch, wenn neue Benutzende und Gruppen über die Seite „Benutzer und Gruppen“ hinzugefügt werden.
* Klicken Sie auf Speichern.

## Stoppen aller aktiven Verzeichnissynchronisierungen {#stop-all-directory-synchronizations-currently-in-progress}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf „Abbrechen“. Diese Schaltfläche wird nur während einer aktiven Verzeichnissynchronisierung angezeigt.
