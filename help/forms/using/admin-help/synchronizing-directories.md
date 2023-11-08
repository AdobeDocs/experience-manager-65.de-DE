---
title: Synchronisieren von Verzeichnissen
seo-title: Synchronizing directories
description: Erfahren Sie, wie Sie die User Management-Datenbank mit Änderungen an den Quellordnerservern mithilfe einer manuellen oder geplanten Synchronisierung synchronisieren.
seo-description: Learn how to synchronize the User Management database with changes to the source directory servers using manual or scheduled synchronization.
uuid: 71cbc04d-6172-49b7-a490-ff3233c1b2bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7ec0698a-9e6e-48d4-bba2-5a6eee313900
exl-id: cb642289-4137-4ba7-8bde-0e458c8c94fe
source-git-commit: e2a3470784beb04c2179958ac6cb98861acfaa71
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 27%

---

# Synchronisieren von Verzeichnissen {#synchronizing-directories}

Für die Synchronisierung von Domains haben Sie die Wahl zwischen manueller und geplanter Synchronisierung. Bei *der manuellen Synchronisierung werden* ausgewählte Domains synchronisiert. Die *geplante Synchronisierung* synchronisiert alle Domains.

Die Ordnersynchronisierung wird verwendet, um Details von den Ordnerservern, die Sie in Ihren Ordnereinstellungen angegeben haben, in die User Management-Datenbank zu ziehen. Später können Sie auch eine manuelle Synchronisierung durchführen, wenn Änderungen oder Aktualisierungen auf den Ordnerservern auftreten. Beispielsweise können Sie eine manuelle Synchronisierung durchführen, wenn Benutzer und Gruppen hinzugefügt oder Änderungen am Benutzerkonto vorgenommen werden.

Sie können auch einen täglichen Synchronisierungszeitplan festlegen, um die User Management-Datenbank automatisch mit Änderungen oder Aktualisierungen an den Quellordnerservern zu synchronisieren. Dieser Prozess verwendet jedoch Netzwerk- und Serverressourcen. Wählen Sie Zeiträume mit geringer Auslastung aus und vermeiden Sie die Planung unnötiger Synchronisierungen, die System- und Netzwerkressourcen binden. Um unnötige Synchronisierungen zu minimieren, verwenden Sie stattdessen die sofortige Synchronisierungsoption.

Sie können auch angeben, ob ein Push von Benutzer- und Gruppeninformationen in Adobe LiveCycle Content Services 9 (nicht mehr unterstützt) ausgeführt wird, wenn Domains synchronisiert werden.

>[!NOTE]
>
>Erstellen Sie nicht mehrere lokale Benutzer und Gruppen, während eine LDAP-Ordnersynchronisierung läuft. Wird dies dennoch versucht, können Fehler auftreten.

>[!NOTE]
>
>Wird der Domain-Namenssynchronisierungsprozess unterbrochen (z. B. wenn der Anwendungsserver während des Prozesses heruntergefahren wird), warten Sie kurze Zeit, bevor Sie die die Synchronisierung der Domain erneut versuchen. Um den Status der Synchronisierung zu bewerten, sehen Sie sich den Status an. Wenn User Management vor dem Herunterfahren eine Sperre erworben hat, warten Sie 10 Minuten, bis die Sperre nach dem Neustart des Servers freigegeben wird. Wenn der Synchronisierungsstatus &quot;Wird ausgeführt&quot;lautet, die Synchronisierung jedoch unterbrochen oder angehalten wurde, versucht User Management erneut, die Synchronisation nach 3 Minuten durchzuführen. Nach drei fehlgeschlagenen Versuchen deklariert User Management die Synchronisation als fehlgeschlagen und gibt die Sperre frei.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content Management System, das mit LiveCycle installiert wird. Sie ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe [Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).

## Delta-Ordnersynchronisierung aktivieren {#enable-delta-directory-synchronization}

Die Delta-Ordnersynchronisierung verbessert die Effizienz der Ordnersynchronisierung. Wenn die Delta-Ordnersynchronisierung aktiviert ist, synchronisiert User Management nur Benutzer und Gruppen, die seit der letzten Synchronisierung hinzugefügt oder aktualisiert wurden.

User Management führt die folgenden Schritte aus, wenn die Delta-Ordnersynchronisierung aktiviert ist:

* Rufen Sie alle Benutzer von den Ordnerservern ab, aktualisieren Sie jedoch die User Management-Datenbank nur mit den Benutzern, deren Zeitstempel sich geändert hat.
* Rufen Sie alle Gruppen ab, aktualisieren Sie jedoch die User Management-Datenbank nur mit den Gruppen, deren Zeitstempel sich geändert hat.
* Rufen Sie Gruppenmitglieder nur für die Gruppen ab, deren Zeitstempel sich geändert haben, und aktualisieren Sie die User Management-Datenbank mit diesen Informationen.

>[!NOTE]
>
>Benutzer und Gruppen, die aus dem Ordner entfernt wurden, werden erst dann aus der User Management-Datenbank gelöscht, wenn Sie eine vollständige Ordnersynchronisierung durchführen.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Aktivieren Sie unter &quot;Delta-Synchronisation&quot;das Kontrollkästchen und klicken Sie auf &quot;Speichern&quot;.
1. Bearbeiten Sie die Ordnereinstellungen für jede Unternehmens-Domain, die die Delta-Ordnersynchronisierungsfunktion verwenden soll. Suchen Sie auf der Seite „Benutzereinstellungen“ und auf der Seite „Gruppeneinstellungen“ die Einstellung „Zeitstempel ändern“ und geben Sie den Wert `modify TimeStamp` ein. Weitere Einzelheiten über das Bearbeiten von Unternehmens-Domains finden Sie unter [Bestehende Domains bearbeiten und konvertieren](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).

## Aktivieren oder Deaktivieren der detaillierten Protokollierung während der Synchronisierung {#enable-or-disable-detailed-logging-during-synchronization}

Standardmäßig protokolliert User Management während des Synchronisierungsprozesses detaillierte Statistiken.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Deaktivieren Sie unter Protokollierung der Synchronisationsstatistiken das Kontrollkästchen zum Deaktivieren der detaillierten Protokollierung oder wählen Sie sie aus, um die Protokollierung zu aktivieren, und klicken Sie dann auf Speichern.

## Wiederholungsoption für die Ordnersynchronisierung konfigurieren {#configure-the-directory-synchronization-retry-option}

Sie können User Management so konfigurieren, dass regelmäßig nach fehlgeschlagenen Versuchen zur Ordnersynchronisierung gesucht wird. User Management versucht dann, die fehlgeschlagenen Synchronisierungen abzuschließen.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Geben Sie unter Synch Finisher Cron Expression einen Cron-Ausdruck ein, der das Intervall darstellt, in dem User Management fehlgeschlagene Synchronisierungen wiederholt. Die Verwendung von Cron-Ausdrücken basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

   Der Standardwert ist 0 0/13 &amp;ast; ? &amp;ast;, was bedeutet, dass die Prüfung alle 13 Minuten durchgeführt wird.

## Ordner manuell synchronisieren {#manually-synchronize-directories}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. (Optional) Um Benutzer- und Gruppeninformationen per Push an Content Services (nicht mehr unterstützt) zu senden, wählen Sie die Option Diese Option auswählen, um Benutzer und Gruppen in registrierte externe Principal Storage Provider zu pushen. Diese Option gilt auch für das Hinzufügen neuer Benutzer und Gruppen über die Seite &quot;Benutzer und Gruppen&quot;.
1. Aktivieren Sie die Kontrollkästchen der zu synchronisierenden Unternehmens-Domains und klicken Sie auf „Jetzt synchronisieren“.

   Wenn Sie mehrere Domains auswählen, wird die Domain-Synchronisierung für alle Domains gleichzeitig ausgeführt. Wählen Sie die Domains dagegen einzeln aus, wird nur jeweils eine Domain-Synchronisierung ausgeführt.

## Ordnersynchronisierung planen {#schedule-directory-synchronization}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Synchronisation planen:

   * Um die automatische tägliche Synchronisierung zu aktivieren, wählen Sie unter &quot;Planung&quot;die Option Vorfälle aus. Wählen Sie Täglich aus der Liste aus und geben Sie die Uhrzeit im 24-Stunden-Format in das entsprechende Feld ein. Wenn Sie Ihre Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck konvertiert, der im Feld Cron-Ausdruck angezeigt wird.
   * Um die Synchronisation an einem bestimmten Wochentag oder Monat oder in einem bestimmten Monat zu planen, wählen Sie Cron Expression aus und geben Sie den entsprechenden Ausdruck in das Feld ein. Synchronisieren Sie beispielsweise am letzten Freitag des Monats um 1:30 Uhr.

Die Verwendung von Cron-Ausdrücken basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

* Um die automatische Synchronisierung zu deaktivieren, wählen Sie Vorfälle und dann Nie aus der Liste aus.
* (Optional) Um Benutzer- und Gruppeninformationen per Push an Content Services (nicht mehr unterstützt) zu senden, wählen Sie die Option Diese Option auswählen, um Benutzer und Gruppen in registrierte externe Principal Storage Provider zu pushen. Diese Option gilt auch für das Hinzufügen neuer Benutzer und Gruppen über die Seite &quot;Benutzer und Gruppen&quot;.
* Klicken Sie auf Speichern.

## Alle laufenden Ordnersynchronisierungen beenden {#stop-all-directory-synchronizations-currently-in-progress}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf Abbrechen. Diese Schaltfläche wird nur angezeigt, während eine Ordnersynchronisierung ausgeführt wird.
