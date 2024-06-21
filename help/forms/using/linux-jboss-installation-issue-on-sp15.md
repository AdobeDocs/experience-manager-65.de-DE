---
title: Installationsproblem mit dem Service Pack von AEM Forms JEE 6.5.15.0 in der JBoss® Linux®-Umgebung
description: Das Service Pack von AEM Forms JEE 6.5.15.0 wird nicht ordnungsgemäß in der JBoss® Linux®-Umgebung installiert. Patch-Änderungen werden nicht auf den Anwendungs-Server angewendet. Fügen Sie die Datei „RUP_BOM.xml“ zum XML-Verzeichnis hinzu.
exl-id: 96ecbe58-a859-4432-a2d8-3d5dc0eaf989
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, Troubleshooting
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 100%

---

# Installationsproblem mit dem Service Pack von AEM Forms 6.5.15.0 JEE in der JBoss®-Umgebung {#aem-forms-installation-issue-environment}

## Problem {#issue}

Das Service Pack von AEM Forms JEE 6.5.15.0 wird in der JBoss® Linux®-Umgebung nicht ordnungsgemäß installiert. In der `PatchInstallerProcessing[1-9*].log`-Datei wird der Protokolleintrag, `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component is not in the installation. Skipping Processing`, protokolliert. Dieser Eintrag zeigt an, dass die Installation des Service Packs von AEM Forms JEE 6.5.15.0 nicht erfolgreich war.

## Gilt für {#applies-to}

Diese Lösung gilt für:
* JBoss® Linux®-Umgebung

>[!NOTE]
>
> Stellen Sie sicher, dass das Service Pack von AEM Forms JEE 6.5.15.0 mindestens einmal auf dem Anwendungs-Server installiert ist, bevor Sie die Schritte von [Hinzufügen der Datei RUP_BOM.xml zum XML-Verzeichnis](#solution-solution) ausführen.

## Lösung {#solution}

Um das Installationsproblem mit dem Service Pack von AEM Forms JEE 6.5.15.0 zu beheben, fügen Sie die `RUP_BOM.xml`-Datei zum XML-Verzeichnis hinzu:
1. Navigieren Sie zum Ordner, in den Sie den Patch `AEMForms-6.5.0-0057_jboss_linux.tar.gz` extrahiert haben.
1. Navigieren Sie zu `/CDROM_Installers/Linux/Disk1/InstData` und suchen Sie nach der `Resource1.zip`-Datei.
1. Kopieren Sie die Datei `Resource1.zip` an einen anderen Speicherort außerhalb des extrahierten Ordners und entpacken Sie die Datei `Resource1.zip`.
1. Navigieren Sie zu `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` und kopieren Sie die Datei `RUP_BOM.xml`.
1. Fügen Sie die Datei RUP_BOM.xml unter `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml` ein.
1. Installieren Sie das [Service Pack von AEM Forms JEE 6.5.15.0](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).
