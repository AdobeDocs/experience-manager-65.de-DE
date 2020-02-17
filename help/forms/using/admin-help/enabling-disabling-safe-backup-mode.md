---
title: Abgesicherten Sicherungsmodus aktivieren und deaktivieren
seo-title: Abgesicherten Sicherungsmodus aktivieren und deaktivieren
description: Auf der Seite „Sicherungseinstellungen“ können Sie AEM Forms im abgesicherten Sicherungsmodus ausführen, sodass die Datenbank und der Ordner des globalen Dokumentenspeichers zuverlässig gesichert werden können. Erfahren Sie mehr über die Aktivierung und Deaktivierung des Sicherungsmodus.
seo-description: Auf der Seite „Sicherungseinstellungen“ können Sie AEM Forms im abgesicherten Sicherungsmodus ausführen, sodass die Datenbank und der Ordner des globalen Dokumentenspeichers zuverlässig gesichert werden können. Erfahren Sie mehr über die Aktivierung und Deaktivierung des Sicherungsmodus.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Abgesicherten Sicherungsmodus aktivieren und deaktivieren {#enabling-and-disabling-safe-backup-mode}

Auf der Seite „Sicherungseinstellungen“ können Sie AEM Forms im abgesicherten Sicherungsmodus ausführen, sodass die Datenbank und der Ordner des globalen Dokumentenspeichers zuverlässig gesichert werden können.

Im abgesicherten Sicherungsmodus wird AEM Forms normal ausgeführt mit der Ausnahme, dass keine Dateien aktiv aus dem Ordner des globalen Dokumentenspeichers entfernt werden.

>[!NOTE]
>
>Durch das Festlegen dieser Option wird keine Sicherung Ihres Systems ausgeführt. Ihr System wird für die Sicherung vorbereitet.

## Abgesicherten Sicherungsmodus aktivieren {#enable-safe-backup-mode}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungseinstellungen“.
1. Aktivieren Sie auf der Seite „Sicherungseinstellungen“ die Option „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

>[!NOTE]
>
>Wenn das System bereits im abgesicherten Sicherungsmodus ausgeführt wird, wird keine neue Reservierung erstellt, wenn Sie auf OK klicken.

## Abgesicherten Sicherungsmodus deaktivieren {#disable-safe-backup-mode}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungseinstellungen“.
1. Deaktivieren Sie auf der Seite „Sicherungseinstellungen“ die Option „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

