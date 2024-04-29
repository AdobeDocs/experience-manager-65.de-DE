---
title: Backup-Beschränkungen für PDF Generator
description: Erfahren Sie mehr über die Backup-Beschränkungen für PDF Generator. Das von PDF Generator verwendete temporäre Verzeichnis kann nicht gesichert werden, da der Inhalt in festgelegten Zeitabständen gelöscht wird.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
exl-id: a23db58d-1236-4689-93fc-dea508f8eb81
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '73'
ht-degree: 100%

---

# Backup-Beschränkungen für PDF Generator {#pdf-generator-backup-limitations}

Der temporäre Ordner, der von PDF Generator zum Konvertieren von Dateien verwendet wird, kann nicht gesichert werden. Auch wenn der Dienst ordnungsgemäß wiederhergestellt wird, können dennoch Daten verloren gehen, weil PDF Generator den Inhalt des temporären Ordners in festgelegten Zeitabständen prüft und löscht.
