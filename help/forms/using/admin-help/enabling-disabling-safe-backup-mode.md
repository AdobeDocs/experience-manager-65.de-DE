---
title: Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus
description: Auf der Seite „Sicherungseinstellungen“ können Sie AEM Forms im abgesicherten Sicherungsmodus ausführen, sodass die Datenbank und der Ordner des globalen Dokumentenspeichers zuverlässig gesichert werden können. Erfahren Sie mehr über die Aktivierung und Deaktivierung des Sicherungsmodus.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f0ab712f-ecd9-4be8-a7a5-fd1a7a8c9a0b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus {#enabling-and-disabling-safe-backup-mode}

Auf der Seite „Sicherungseinstellungen“ können Sie AEM Forms im abgesicherten Sicherungsmodus ausführen, sodass die Datenbank und der Ordner des globalen Dokumentenspeichers zuverlässig gesichert werden können.

Im abgesicherten Sicherungsmodus wird AEM Forms normal ausgeführt, mit der einzigen Ausnahme, dass keine Dateien aktiv aus dem Ordner des globalen Dokumentenspeichers entfernt werden.

>[!NOTE]
>
>Durch das Festlegen dieser Option wird keine Sicherung Ihres Systems ausgeführt, aber Ihr System wird für die Sicherung vorbereitet.

## Aktivieren des abgesicherten Sicherungsmodus {#enable-safe-backup-mode}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungseinstellungen“.
1. Aktivieren Sie auf der Seite „Sicherungseinstellungen“ die Option „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

>[!NOTE]
>
>Wenn das System bereits im abgesicherten Sicherungsmodus ausgeführt wird, wird keine neue Reservierung erstellt, wenn Sie auf „OK“ klicken.

## Deaktivieren des abgesicherten Sicherungsmodus {#disable-safe-backup-mode}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungseinstellungen“.
1. Deaktivieren Sie auf der Seite „Sicherungseinstellungen“ die Option „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.
