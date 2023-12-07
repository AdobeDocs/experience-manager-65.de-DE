---
title: Einschränkungen bei der Sicherung von PDF Generator
description: Erfahren Sie mehr über die Backup-Einschränkungen von PDF Generatoren. Das von PDF Generator verwendete temporäre Verzeichnis kann nicht gesichert werden, da es den Inhalt in festgelegten Zeitabständen löscht.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
exl-id: a23db58d-1236-4689-93fc-dea508f8eb81
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '73'
ht-degree: 10%

---

# Einschränkungen bei der Sicherung von PDF Generator {#pdf-generator-backup-limitations}

Der temporäre Ordner, den PDF Generator zum Konvertieren von Dateien verwendet, kann nicht gesichert werden. Obwohl der Dienst ordnungsgemäß wiederhergestellt wird, können Daten verloren gehen, da der PDF Generator den Inhalt des temporären Ordners in festgelegten Zeitabständen überprüft und löscht.
