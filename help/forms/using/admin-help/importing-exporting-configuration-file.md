---
title: Importieren und Exportieren der Konfigurationsdatei
description: Erfahren Sie, wie Sie die Konfigurationsdatei importieren und exportieren, um Servervoreinstellungen zu bearbeiten oder eine andere AEM Forms-Produktinstanz zu konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 225dbeb5-a21c-4338-98c7-e10c32973721
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 4%

---

# Importieren und Exportieren der Konfigurationsdatei {#importing-and-exporting-the-configuration-file}

Verwenden Sie die Seite Manuelle Konfiguration , um eine Kopie der Konfigurationseinstellungen im XML-Format herunterzuladen. Die Einstellungen in dieser Datei steuern alle Servervoreinstellungen. Sie können die Datei dann bearbeiten und wieder auf den Server hochladen. Sie können die Datei auch verwenden, um eine andere AEM Forms-Produktinstanz zu konfigurieren.

Um Sicherheitsrisiken zu vermeiden, ist der Wert des Bindungskennworts für den Ordnerserver nicht in einer exportierten Konfigurationsdatei enthalten. Aktualisieren Sie das Kennwort in der XML-Datei, bevor Sie die Datei in ein neues System importieren.

>[!NOTE]
>
>Beim Import der Konfigurationsdatei werden AEM Formulare anhand der Informationen in der Datei neu konfiguriert. Nur ein Systemadministrator oder ein Professional Services-Berater, der mit dem AEM Forms-Produkt und XML vertraut ist, sollte eine Änderung der Konfigurationsdatei in Erwägung ziehen. Möglicherweise müssen sie die Konfigurationsdatei bearbeiten, um beispielsweise eine beschädigte Einstellung neu zu konfigurieren.

**Konfigurationsinformationen exportieren**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;.
1. Klicken Sie auf Exportieren. Wenn Sie Microsoft Internet Explorer verwenden, werden Sie aufgefordert, einen Speicherort für die Datei anzugeben. Wenn Sie Firefox verwenden, wird die Datei auf Ihrem Desktop gespeichert.

**Konfigurationsinformationen importieren**

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Konfigurationsdateien importieren und exportieren&quot;.
1. Klicken Sie auf Durchsuchen , um die Konfigurationsdatei zu suchen, klicken Sie auf Importieren und dann auf OK.
