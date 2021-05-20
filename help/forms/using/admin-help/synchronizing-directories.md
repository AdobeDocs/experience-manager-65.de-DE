---
title: Ordner synchronisieren
seo-title: Ordner synchronisieren
description: Erfahren Sie, wie Sie die User Management-Datenbank mit Änderungen an den Quellordnerservern mithilfe der manuellen oder geplanten Synchronisierung synchronisieren.
seo-description: Erfahren Sie, wie Sie die User Management-Datenbank mit Änderungen an den Quellordnerservern mithilfe der manuellen oder geplanten Synchronisierung synchronisieren.
uuid: 71cbc04d-6172-49b7-a490-ff3233c1b2bb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7ec0698a-9e6e-48d4-bba2-5a6eee313900
exl-id: cb642289-4137-4ba7-8bde-0e458c8c94fe
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 97%

---

# Ordner synchronisieren {#synchronizing-directories}

Für die Synchronisierung von Domänen haben Sie die Wahl zwischen manueller und geplanter Synchronisierung. Bei *der manuellen Synchronisierung werden* ausgewählte Domänen synchronisiert. Die *geplante Synchronisierung* synchronisiert alle Domänen.

Durch die Ordnersynchronisierung werden Details aus den Ordnerservern, die Sie in Ihren Ordnereinstellungen angegeben haben, in die User Management-Datenbank abgerufen. Später können Sie auch eine manuelle Synchronisierung durchführen, falls Änderungen oder Aktualisierungen der Ordnerserver erfolgt sind. Sie können beispielsweise eine manuelle Synchronisierung durchführen, wenn Benutzer und Gruppen hinzugefügt oder Änderungen an einem Benutzerkonto vorgenommen wurden.

Sie können außerdem einen täglichen Synchronisierungszeitplan einrichten, um die User Management-Datenbank automatisch mit Änderungen oder Aktualisierungen der Quellordnerserver zu synchronisieren. Dabei sollten Sie allerdings bedenken, dass dieser Prozess Netzwerk- und Serverressourcen belegt. Wählen Sie Zeiträume mit geringer Systemauslastung und planen Sie keine unnötigen Synchronisierungen, die System- und Netzwerkressourcen binden. Um die Anzahl unnötiger Synchronisierungen zu minimieren, verwenden Sie am besten die Option für die sofortige Synchronisierung.

Sie können auch angeben, ob ein Push von Benutzer- und Gruppeninformationen in Adobe LiveCycle Content Services 9 (nicht mehr unterstützt) ausgeführt wird, wenn Domänen synchronisiert werden.

>[!NOTE]
>
>Erstellen Sie nicht mehrere lokale Benutzer und Gruppen, während eine LDAP-Ordnersynchronisierung läuft. Wird dies dennoch versucht, können Fehler auftreten.

>[!NOTE]
>
>Wird der Domänensynchronisierungsprozess unterbrochen (z. B. wenn der Anwendungsserver während des Prozesses heruntergefahren wird), warten Sie kurze Zeit, bevor Sie die die Synchronisierung der Domäne erneut versuchen. Prüfen Sie den Status der Synchronisierung. Falls User Management vor dem Herunterfahren eine Sperre aktiviert hatte, warten Sie 10 Minuten nach dem Neustart des Servers bis zur Freigabe der Sperre. Lautet der Synchronisierungsstatus „Wird ausgeführt“, obwohl die Synchronisierung unterbrochen oder angehalten wurde, unternimmt User Management nach 3 Minuten einen erneuten Versuch. Nach drei fehlgeschlagenen Versuchen erklärt User Management die Synchronisierung für gescheitert und gibt die Sperre frei.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Inhaltsverwaltungssystem, das mit LiveCycle installiert wird. Es ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe[ Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html). Informationen zum Konfigurieren von Content Services (nicht mehr unterstützt) finden Sie unter [Content Services verwalten](https://help.adobe.com/en_US/livecycle/9.0/admin_contentservices.pdf).

## Delta-Ordnersynchronisierung aktivieren {#enable-delta-directory-synchronization}

Delta-Ordnersynchronisierung verbessert die Effizienz der Ordnersynchronisierung. Wenn Delta-Ordnersynchronisierung aktiviert ist, synchronisiert User Management nur Benutzer und Gruppen, die seit der letzten Synchronisierung hinzugefügt oder aktualisiert wurden.

User Management führt folgende Schritte aus, wenn Delta-Ordnersynchronisierung aktiviert ist:

* Abrufen aller Benutzer von den Ordnerservern, aber Aktualisieren der User Management-Datenbank nur bei den Benutzern, bei denen sich der Zeitstempel geändert hat.
* Abrufen aller Gruppen, aber Aktualisieren der User Management-Datenbank nur bei den Gruppen, bei denen sich der Zeitstempel geändert hat.
* Abrufen von Gruppenmitgliedern nur für die Gruppen, bei denen sich der Zeitstempel geändert hat, und Aktualisieren der User Management-Datenbank mit diesen Informationen.

>[!NOTE]
>
>Benutzer und Gruppen, die aus dem Ordner gelöscht wurden, werden erst beim Ausführen einer vollständigen Ordnersynchronisierung aus der User Management-Datenbank gelöscht.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Aktivieren Sie unter „Delta-Synchronisation“ das Kontrollkästchen und klicken Sie auf „Speichern“.
1. Bearbeiten Sie die Ordnereinstellungen für jede Unternehmensdomäne, die die Delta-Ordnersynchronisierungsfunktion verwenden soll. Suchen Sie auf der Seite „Benutzereinstellungen“ und auf der Seite „Gruppeneinstellungen“ die Einstellung „Zeitstempel ändern“ und geben Sie den Wert `modify TimeStamp` ein. Weitere Einzelheiten über das Bearbeiten von Unternehmensdomänen finden Sie unter [Bestehende Domänen bearbeiten und konvertieren](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).

## Detaillierte Protokollierung während der Synchronisierung aktivieren oder deaktivieren  {#enable-or-disable-detailed-logging-during-synchronization}

Standardmäßig protokolliert User Management während des Synchronisierungsprozesses detaillierte Statistiken.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Deaktivieren Sie unter „Protokollierung der Synchronisationsstatistiken“ das Kontrollkästchen, um die detaillierte Protokollierung zu deaktivieren, oder aktivieren Sie das Kontrollkästchen, um die detaillierte Protokollierung zu aktivieren. Klicken Sie dann auf „Speichern“.

## Die Wiederholungsoptionen für die Ordnersynchronisierung konfigurieren  {#configure-the-directory-synchronization-retry-option}

Sie können User Management so konfigurieren, dass regelmäßige Prüfungen auf fehlgeschlagene Versuche zur Ordnersynchronisierung erfolgen. User Management versucht dann, die fehlgeschlagenen Synchronisierungen fertigzustellen.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Geben Sie unter „Synchronisations-Finisher Cron Expression“ einen Cron-Ausdruck ein, der das Intervall, in dem User Management die fehlgeschlagenen Synchronisierungen erneut auszuführen versucht, angibt. Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

   Der Standardwert ist 0/13 &amp;ast; ? &amp;ast; , was bedeutet, dass die Prüfung alle 13 Minuten durchgeführt wird.

## Ordner manuell synchronisieren {#manually-synchronize-directories}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. (Optional) Um Benutzer- und Gruppeninformationen im Push-Verfahren an Content Services (nicht mehr unterstützt) zu senden, wählen Sie die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“. Diese Option gilt auch, wenn neue Benutzer und Gruppen über die Seite „Benutzer und Gruppen“ hinzugefügt werden.
1. Aktivieren Sie die Kontrollkästchen der zu synchronisierenden Unternehmensdomänen und klicken Sie auf „Jetzt synchronisieren“.

   Wenn Sie mehrere Domänen auswählen, wird die Domänensynchronisierung für alle Domänen gleichzeitig ausgeführt. Wählen Sie die Domänen dagegen einzeln aus, wird nur jeweils eine Domänensynchronisierung ausgeführt.

## Ordnersynchronisierung planen  {#schedule-directory-synchronization}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Synchronisierungsprobleme:

   * Wählen Sie zum Aktivieren der automatischen täglichen Synchronisierung unter „Zeitplaner“ die Option „Häufigkeit“ aus. Wählen Sie aus der Liste die Option „Täglich“ aus und geben Sie in das entsprechende Feld die Zeit im 24-Stunden-Format ein. Wenn Sie die Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck konvertiert, der im Feld „Cron-Ausdruck“ angezeigt wird.
   * Um die Synchronisierung an einem bestimmten Tag der Woche bzw. des Monats oder in einem bestimmten Monat zu planen, wählen Sie „Cron-Ausdruck“ aus und geben Sie den entsprechenden Ausdruck in das Feld ein. Sie könnten die Synchronisierung beispielsweise für 1:30 Uhr am letzten Freitag im Monat planen.

Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

* Zum Ausschalten der automatischen Synchronisierung wählen Sie „Häufigkeit“ und anschließend in der Liste „Nie“ aus.
* (Optional) Um Benutzer- und Gruppeninformationen im Push-Verfahren an Content Services (nicht mehr unterstützt) zu senden, wählen Sie die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“. Diese Option gilt auch, wenn neue Benutzer und Gruppen über die Seite „Benutzer und Gruppen“ hinzugefügt werden.
* Klicken Sie auf Speichern.

## Alle aktiven Ordnersynchronisierungsprozesse beenden  {#stop-all-directory-synchronizations-currently-in-progress}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf „Beenden“. Diese Schaltfläche wird nur während einer aktiven Ordnersynchronisierung angezeigt.
