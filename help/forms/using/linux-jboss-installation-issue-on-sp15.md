---
title: Installationsproblem mit dem AEM Forms JEE 6.5.15.0 Service Pack in der JBoss® Linux®-Umgebung
description: Das AEM Forms JEE 6.5.15.0 Service Pack wird nicht ordnungsgemäß in der JBoss® Linux®-Umgebung installiert. Patchänderungen werden nicht auf den Anwendungsserver angewendet. Fügen Sie die Datei "RUP_BOM.xml"zum XML-Verzeichnis hinzu.
source-git-commit: 76a3a87408ceb13023737379c20fb44ce5fb180a
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 7%

---


# Installationsproblem mit dem AEM Forms 6.5.15.0 JEE Service Pack in der JBoss®-Umgebung {#aem-forms-installation-issue-environment}

## Problem {#issue}

Das AEM Forms JEE 6.5.15.0 Service Pack wird in der JBoss® Linux®-Umgebung nicht ordnungsgemäß installiert. In `PatchInstallerProcessing[1-9*].log` Datei des Protokolleintrags, `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component isn't in the installation. Skipping Processing`, wird protokolliert. Dieser Eintrag zeigt an, dass die Installation des AEM Forms JEE 6.5.15.0 Service Packs nicht erfolgreich war.

## Gilt für {#applies-to}

Diese Lösung gilt für:
* JBoss® Linux®-Umgebung

>[!NOTE]
>
> Stellen Sie sicher, dass das AEM Forms JEE 6.5.15.0 Service Pack mindestens einmal auf dem Anwendungsserver installiert ist, bevor Sie die Schritte von [Hinzufügen der Datei RUP_BOM.xml zum XML-Verzeichnis](#solution-solution).

## Lösung {#solution}

Um das Installationsproblem mit dem AEM Forms JEE 6.5.15.0 Service Pack zu beheben, fügen Sie das `RUP_BOM.xml` Datei in das XML-Verzeichnis:
1. Navigieren Sie zum Ordner, in den Sie den Patch extrahiert haben. `AEMForms-6.5.0-0057_jboss_linux.tar.gz`.
1. Navigieren Sie zu `/CDROM_Installers/Linux/Disk1/InstData` und suchen Sie nach `Resource1.zip` -Datei.
1. Kopieren Sie die `Resource1.zip` Datei an einem anderen Speicherort außerhalb des extrahierten Ordners speichern und die ZIP-Datei dekomprimieren `Resource1.zip` -Datei.
1. Navigieren Sie zu `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` und kopieren Sie die `RUP_BOM.xml` -Datei.
1. Fügen Sie die Datei RUP_BOM.xml unter `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml`.
1. Installieren Sie die [AEM Forms JEE 6.5.15.0 Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).