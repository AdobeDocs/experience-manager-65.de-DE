---
title: Importieren und Exportieren der Konfigurationsdatei
description: Erfahren Sie, wie Sie die Konfigurationsdatei importieren und exportieren, damit Sie Server-Voreinstellungen bearbeiten oder eine andere AEM Forms-Produktinstanz konfigurieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 225dbeb5-a21c-4338-98c7-e10c32973721
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '252'
ht-degree: 100%

---

# Importieren und Exportieren der Konfigurationsdatei {#importing-and-exporting-the-configuration-file}

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
