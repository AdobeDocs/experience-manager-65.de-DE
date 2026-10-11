---
title: Installationsproblem mit dem Service Pack von AEM Forms JEE 6.5.15.0 in der JBoss® Linux®-Umgebung
description: AEM Forms JEE 6.5.15.0 Service Pack ist nicht ordnungsgemäß in der JBoss® Linux®-Umgebung installiert. Patch-Änderungen werden nicht auf den Anwendungs-Server angewendet. Fügen Sie die Datei „RUP_BOM.xml“ zum XML-Verzeichnis hinzu.
SEO Description: AEM Forms JEE 6.5.15.0 service pack  is not installed properly on the JBoss Linux environment.
exl-id: 96ecbe58-a859-4432-a2d8-3d5dc0eaf989
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 94663796-0ee7-58b9-84f4-b425ebb69e83
    internal-label: AEM Forms on JEE
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 45%
---
# Installationsproblem mit dem Service Pack von AEM Forms 6.5.15.0 JEE in der JBoss®-Umgebung {#aem-forms-installation-issue-environment}

## Problem {#issue}

Das Service Pack von AEM Forms JEE 6.5.15.0 wird in der JBoss® Linux®-Umgebung nicht ordnungsgemäß installiert. In der `PatchInstallerProcessing[1-9*].log`-Datei wird der Protokolleintrag, `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component is not in the installation. Skipping Processing`, protokolliert. Dieser Eintrag zeigt an, dass die Installation des AEM Forms JEE 6.5.15.0 Service Pack nicht erfolgreich war.

## Gilt für {#applies-to}

Diese Lösung gilt für:
* JBoss® Linux®-Umgebung

>[!NOTE]
>
> Stellen Sie sicher, dass das Service Pack von AEM Forms JEE 6.5.15.0 mindestens einmal auf dem Anwendungsserver installiert ist, bevor Sie die Schritte ausführen [Hinzufügen der Datei RUP_BOM.xml zum XML-Verzeichnis](#solution-solution).

## Lösung {#solution}

Um das Installationsproblem mit dem Service Pack von AEM Forms JEE 6.5.15.0 zu beheben, fügen Sie die `RUP_BOM.xml`-Datei zum XML-Verzeichnis hinzu:
1. Navigieren Sie zum Ordner, in den Sie den Patch `AEMForms-6.5.0-0057_jboss_linux.tar.gz` extrahiert haben.
1. Navigieren Sie zu `/CDROM_Installers/Linux/Disk1/InstData` und suchen Sie nach der `Resource1.zip`-Datei.
1. Kopieren Sie die Datei `Resource1.zip` an einen anderen Speicherort außerhalb des extrahierten Ordners und entpacken Sie die Datei `Resource1.zip`.
1. Navigieren Sie zu `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` und kopieren Sie die Datei `RUP_BOM.xml`.
1. Fügen Sie die Datei RUP_BOM.xml unter `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml` ein.
1. Installieren Sie das [AEM Forms JEE 6.5.15.0 Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) neu.
