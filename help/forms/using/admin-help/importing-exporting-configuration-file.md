---
title: Importieren und Exportieren der Konfigurationsdatei
description: Erfahren Sie, wie Sie die Konfigurationsdatei importieren und exportieren, damit Sie Server-Voreinstellungen bearbeiten oder eine andere AEM Forms-Produktinstanz konfigurieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 225dbeb5-a21c-4338-98c7-e10c32973721
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
source-wordcount: '264'
ht-degree: 100%
---
# Importieren und Exportieren der Konfigurationsdatei {#importing-and-exporting-the-configuration-file}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Auf der Seite „Manuelle Konfiguration“ können Sie eine Kopie der Konfigurationseinstellungen im XML-Format herunterladen. Die Einstellungen in dieser Datei steuern sämtliche Server-Voreinstellungen. Sie können die Datei dann bearbeiten und wieder auf den Server hochladen. Sie können die Datei auch zum Konfigurieren einer weiteren AEM Forms-Produktinstanz verwenden.

Um Sicherheitsrisiken zu vermeiden, ist der Wert für das Bindungskennwort des Verzeichnis-Servers nicht in einer exportierten Konfigurationsdatei enthalten. Aktualisieren Sie das Kennwort in der XML-Datei, bevor Sie die Datei in ein neues System importieren.

>[!NOTE]
>
>Beim Importieren der Konfigurationsdatei wird AEM Forms basierend auf den Informationen in der Datei neu konfiguriert. Nur Systemadmins oder versierte IT-Beraterinnen und -Berater, die mit dem Produkt AEM Forms und XML vertraut sind, sollte die Konfigurationsdatei ändern. Es kann beispielsweise eine Bearbeitung der Konfigurationsdatei erforderlich sein, um eine fehlerhafte Einstellung neu zu konfigurieren.

**Exportieren der Konfigurationsinformationen**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Exportieren“. Wenn Sie Microsoft Internet Explorer verwenden, werden Sie aufgefordert, einen Speicherort für die Datei anzugeben. Bei Verwendung von Firefox wird die Datei auf dem Desktop gespeichert.

**Importieren der Konfigurationsinformationen**

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Konfigurationsdatei zu suchen, dann auf „Importieren“ und schließlich auf „OK“.
