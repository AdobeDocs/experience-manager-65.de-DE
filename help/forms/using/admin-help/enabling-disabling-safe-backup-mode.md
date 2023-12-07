---
title: Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus
description: Auf der Seite "Sicherungseinstellungen"können Sie AEM Formulare im abgesicherten Sicherungsmodus ausführen, damit Sie die Datenbank und den Ordner des globalen Dokumentenspeichers (GDS) zuverlässig sichern können. Erfahren Sie, wie Sie den abgesicherten Sicherungsmodus aktivieren und deaktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f0ab712f-ecd9-4be8-a7a5-fd1a7a8c9a0b
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 6%

---

# Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus {#enabling-and-disabling-safe-backup-mode}

Auf der Seite &quot;Sicherungseinstellungen&quot;können Sie AEM Formulare im abgesicherten Sicherungsmodus ausführen, damit Sie die Datenbank und den Ordner des globalen Dokumentenspeichers (GDS) zuverlässig sichern können.

Während AEM Formulare im abgesicherten Sicherungsmodus ausgeführt werden, funktioniert sie normal, mit der Ausnahme, dass sie keine Dateien aktiv aus dem Ordner des globalen Dokumentenspeichers entfernen.

>[!NOTE]
>
>Durch das Festlegen dieser Option wird Ihr System nicht gesichert, sondern das System auf die Sicherung vorbereitet.

## Aktivieren des abgesicherten Sicherungsmodus {#enable-safe-backup-mode}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Sicherungseinstellungen&quot;.
1. Wählen Sie auf der Seite &quot;Sicherungseinstellungen&quot;die Option &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.

>[!NOTE]
>
>Wenn das System bereits im abgesicherten Sicherungsmodus ausgeführt wird, wird keine neue Reservierung erstellt, wenn Sie auf OK klicken.

## Abgesicherten Sicherungsmodus deaktivieren {#disable-safe-backup-mode}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Core-Systemeinstellungen&quot;> &quot;Sicherungseinstellungen&quot;.
1. Deaktivieren Sie auf der Seite &quot;Sicherungseinstellungen&quot;die Option Im abgesicherten Sicherungsmodus arbeiten und klicken Sie auf OK.
