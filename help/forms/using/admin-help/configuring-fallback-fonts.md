---
title: Konfigurieren von Ersatzschriftarten
description: Erfahren Sie, wie Sie Fallback-Schriftarten für AEM Forms konfigurieren. Sie können die Datei "FontManagerResources.properties"verwenden, um die Standardschriftarten den Fallback-Schriftarten manuell zuzuordnen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 76dd2b0c-9f16-47bf-a565-99277be750fb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 29%

---

# Konfigurieren von Ersatzschriftarten {#configuring-fallback-fonts}

Sie können die Datei &quot;FontManagerResources.properties&quot;manuell konfigurieren, um die standardmäßigen AEM Forms-Schriftarten Fallback (oder Ersatz) zuzuordnen, wenn die Standardschriftarten nicht auf dem Server verfügbar sind. Diese Eigenschaftendatei befindet sich in der Datei &quot;adobe-fontmanager.jar&quot;.

>[!NOTE]
>
>Die Konfiguration von Ersatzschriftarten gilt auch für den Assembler-Dienst.

1. Wechseln Sie im Ordner „*`[aem-forms root]`*/configurationManager/export“ zur Datei „adobe-livecycle-*`[appserver]`*.ear“, erstellen Sie eine Sicherungskopie und dekomprimieren Sie die Originaldatei.
1. Suchen Sie die Datei &quot;adobe-fontmanager.jar&quot;und dekomprimieren Sie sie.
1. Suchen Sie die Datei &quot;FontManagerResources.properties&quot;und öffnen Sie sie in einem Texteditor.
1. Ändern Sie die Speicherorte und Namen der generischen und Fallback-Schriftart nach Bedarf und speichern Sie die Datei.

   Die Schriftarteinträge in der Datei „FontManagerResources.properties“ sind relativ zum Ordner „*`[aem-forms root]`*/fonts“. Wenn Sie Schriftarten angeben, die keine standardmäßigen AEM Forms-Schriftarten sind, müssen Sie diese Schriftarten in dieser Ordnerstruktur installieren (entweder in einem vorhandenen Ordner oder in einem neu erstellten Ordner).

   >[!NOTE]
   >
   >Wenn die angegebene Schriftart oder Standardschriftart kein bestimmtes Unicode-Zeichen enthält oder nicht verfügbar ist, wird das Zeichen gemäß der folgenden Priorität aus einer Fallback-Schriftart übernommen:

   * Gebietsschemaspezifische Schriftart
   * ROOT-Schriftart, wenn Gebietsschema nicht festgelegt ist
   * Generische Schriftart, nach Reihenfolge durchsucht in der Fallback-Tabelle

1. Komprimieren Sie die Datei &quot;adobe-fontmanager.jar&quot;neu.
1. Komprimieren Sie die Datei „adobe-livecycle-*`[appserver]`*.ear“ neu und stellen Sie sie anschließend manuell oder durch Ausführen von Configuration Manager erneut bereit.

>[!NOTE]
>
>Komprimieren Sie die Datei „adobe-livecycle-`[appserver]`.ear“ nicht mit Configuration Manager, da dadurch Ihre Änderungen mit den AEM Forms-Standardwerten überschrieben würden.
