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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 100%
---
# Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus {#enabling-and-disabling-safe-backup-mode}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

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
