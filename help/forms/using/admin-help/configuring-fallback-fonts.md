---
title: Ersatzschriftarten konfigurieren
seo-title: Ersatzschriftarten konfigurieren
description: Erfahren Sie, wie Sie Ersatzschriftarten konfigurieren.
seo-description: Erfahren Sie, wie Sie Ersatzschriftarten konfigurieren.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e

---


# Ersatzschriftarten konfigurieren {#configuring-fallback-fonts}

Sie können die Datei „FontManagerResources.properties“ zum Zuordnen der AEM Forms-Standardschriftarten zu Ersatzschriftarten manuell konfigurieren, falls die Standardschriftarten auf dem Server nicht verfügbar sind. Diese Eigenschaftendatei ist in der Datei „adobe-fontmanager.jar“ enthalten.

>[!NOTE]
>
>Die Konfiguration der Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Navigate to the adobe-livecycle-*`[appserver]`*.ear file in the *`[aem-forms root]`*/configurationManager/export directory, make a backup copy, and unpackage the original.
1. Suchen Sie die Datei „adobe-fontmanager.jar“ und dekomprimieren Sie sie.
1. Suchen Sie die Datei „FontManagerResources.properties“ und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der Standard- und Ersatzschriftarten den Anforderungen entsprechend und speichern Sie die Datei.

   The font entries in the FontManagerResources.properties file are relative to the *`[aem-forms root]`*/fonts directory. Wenn Sie Schriftarten angeben, die keine AEM Forms-Standardschriftarten sind, müssen Sie diese in dieser Ordnerstruktur installieren (entweder in einem vorhandenen oder einem neu erstelltem Ordner).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart bzw. Standardschriftart kein spezifisches Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität in einer Ersatzschriftart ausgewählt:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn kein Gebietsschema festgelegt ist
   * Allgemeine Schriftart, die gemäß der in der Tabelle mit den Ersatzschriftarten festgelegten Reihenfolge gesucht wird

1. Komprimieren Sie die Datei „adobe-fontmanager.jar“ neu.
1. Repackage the adobe-livecycle-*`[appserver]`*.ear file and then redeploy it either manually or by running Configuration Manager.

>[!NOTE]
>
>Do not use Configuration Manager to repackage the adobe-livecycle-`[appserver]`.ear file because it will overwrite your modifications with the AEM forms default values.

