---
title: Ersatzschriftarten konfigurieren
seo-title: Configuring fallback fonts
description: Erfahren Sie, wie Sie Ersatzschriftarten konfigurieren.
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 76dd2b0c-9f16-47bf-a565-99277be750fb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 100%

---

# Ersatzschriftarten konfigurieren {#configuring-fallback-fonts}

Sie können die Datei „FontManagerResources.properties“ zum Zuordnen der AEM Forms-Standardschriftarten zu Ersatzschriftarten manuell konfigurieren, falls die Standardschriftarten auf dem Server nicht verfügbar sind. Diese Eigenschaftendatei ist in der Datei „adobe-fontmanager.jar“ enthalten.

>[!NOTE]
>
>Die Konfiguration der Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Wechseln Sie im Ordner „*`[aem-forms root]`*/configurationManager/export“ zur Datei „adobe-livecycle-*`[appserver]`*.ear“, erstellen Sie eine Sicherungskopie und dekomprimieren Sie die Originaldatei.
1. Suchen Sie die Datei „adobe-fontmanager.jar“ und dekomprimieren Sie sie.
1. Suchen Sie die Datei „FontManagerResources.properties“ und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der Standard- und Ersatzschriftarten den Anforderungen entsprechend und speichern Sie die Datei.

   Die Schriftarteinträge in der Datei „FontManagerResources.properties“ sind relativ zum Ordner „*`[aem-forms root]`*/fonts“. Wenn Sie Schriftarten angeben, die keine AEM Forms-Standardschriftarten sind, müssen Sie diese in dieser Ordnerstruktur installieren (entweder in einem vorhandenen oder einem neu erstelltem Ordner).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart bzw. Standardschriftart kein spezifisches Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität in einer Ersatzschriftart ausgewählt:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn kein Gebietsschema festgelegt ist
   * Allgemeine Schriftart, die gemäß der in der Tabelle mit den Ersatzschriftarten festgelegten Reihenfolge gesucht wird

1. Komprimieren Sie die Datei „adobe-fontmanager.jar“ neu.
1. Komprimieren Sie die Datei „adobe-livecycle-*`[appserver]`*.ear“ neu und stellen Sie sie anschließend manuell oder durch Ausführen von Configuration Manager erneut bereit.

>[!NOTE]
>
>Komprimieren Sie die Datei „adobe-livecycle-`[appserver]`.ear“ nicht mit Configuration Manager, da dadurch Ihre Änderungen mit den AEM Forms-Standardwerten überschrieben würden.
