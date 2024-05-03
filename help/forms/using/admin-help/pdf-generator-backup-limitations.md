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
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 100%

---

# Backup-Beschränkungen für PDF Generator {#pdf-generator-backup-limitations}

Der temporäre Ordner, der von PDF Generator zum Konvertieren von Dateien verwendet wird, kann nicht gesichert werden. Auch wenn der Dienst ordnungsgemäß wiederhergestellt wird, können dennoch Daten verloren gehen, weil PDF Generator den Inhalt des temporären Ordners in festgelegten Zeitabständen prüft und löscht.
