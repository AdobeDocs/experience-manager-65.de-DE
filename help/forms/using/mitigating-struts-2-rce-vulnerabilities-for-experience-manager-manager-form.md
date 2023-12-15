---
title: Abmildern von Struts 2 RCE-Schwachstellen für Experience Manager Forms
description: Abmildern von Struts 2 RCE-Schwachstellen für Experience Manager Forms
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
source-git-commit: 287717e39ff58396de6d63a89e2b3d8fef4e6888
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---


# Abmildern von Struts 2 RCE-Schwachstellen für Experience Manager Forms {#mitigatin-struts2-rce-vulnerabilities-for-aem-forms}

## Problem

Für Struts 2 RCE, ein beliebtes und Open-Source-Webanwendungs-Framework für die Entwicklung von Java EE-Webanwendungen, wurden kritische Sicherheitslücken gemeldet. Die folgenden Schwachstellen wurden untersucht:

| Schwachstelle | Was ist betroffen? | Was ist nicht betroffen? |
|---|---|---|
| [CVE-2023-50164](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2023-50164) | Experience Manager 6.5 Forms on JEE (alle Versionen von 6.5 GA bis 6.5.19.0) | <ul><li> Experience Manager Forms Workbench (alle Versionen)</li> <li> Experience Manager Forms on OSGi (alle Versionen) </li> <li> Experience Manager Forms as a Cloud Service </li> <ul> |

## Auflösung

In der folgenden Tabelle ist die Auflösung für alle betroffenen Versionen aufgeführt:

| Freigabe | Aktuelle Version | Benutzeraktion |
|---|---|---|
| Experience Manager 6.5 Forms on JEE | 6.5.19.0 | [Installieren des neuesten Service Packs](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de) |
| Experience Manager 6.5 Forms on JEE | 6.5.13.0 - 6.5.18.0 | Verwenden Sie eine der folgenden Methoden: <ul><li>  <a href="https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de"> Installieren des neuesten Service Packs </a> </li> <li> <a href ="#use-manual-mitigation-steps"> Manuelle Abhilfemaßnahmen verwenden </a> |
| Experience Manager 6.5 Forms on JEE | 6.5 - 6.5.12.0 | [Installieren des neuesten Service Packs](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de)  </br> </br> **NOTE:** AEM Forms unterstützt derzeit die Versionen 6.5.13.0 bis 6.5.19.0. Wenn Sie eine ältere Version verwenden, empfehlen wir ein Upgrade auf 6.5.13.0 oder eine neuere Version. Anweisungen zur Installation AEM Version 6.5.13.0 oder neuer finden Sie in den Versionshinweisen. |

### Manuelle Abhilfemaßnahmen verwenden {#use-manual-mitigation-steps}

Sie können die manuellen Schadensminderungsschritte verwenden, um das Problem auf AEM 6.5 Form Server mit Service Pack 13 auf AEM 6.5 Form Server mit Service Pack 18 (6.5.13.0 - 6.5.18.0) zu beheben:

1. Fahren Sie alle Serverinstanzen und Locators herunter.
1. Laden Sie die [struts-core 2.5.33 jar](https://repo1.maven.org/maven2/org/apache/struts/struts2-core/2.5.33/struts2-core-2.5.33.jar).
1. Laden Sie das manuelle Patchwerkzeug von AEM Forms on JEE herunter von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/patch_utility/archive-patcher-1.0.0.zip).
1. Dekomprimieren Sie das Archiv des manuellen Patchings-Tools. Es werden die folgenden Dateien extrahiert:
   * archive-patcher-1.0.0.jar
   * patch-archive.bat
   * patch-archive.sh
1. Öffnen Sie das Terminal-Fenster und navigieren Sie zum Ordner mit den extrahierten Dateien.
1. Verwenden Sie das manuelle Patching-Tool, um alle struts2-JAR-Dateien zu suchen, aufzulisten und zu ersetzen. So suchen und ersetzen Sie die JAR-Datei &quot;struts2-core-2.5.30&quot;und &quot;struts2-core.jar&quot;:


>[!BEGINTABS]

>[!TAB Windows]

1. Führen Sie den folgenden Befehl aus, um alle struts2 jar-Dateien aufzulisten:

       &quot;
       
       patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\. .\export -pattern=.*struts2-core-2.5.   30.jar$
       
       &quot;
       
       Ersetzen Sie den Pfad im obigen Befehl durch den Pfad Ihres AEM-Formularservers.
   
1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um rekursiv ersetzende Ersetzungen durchzuführen:

       &quot;
       
       patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\. .\export -pattern=.*struts2-core-2.5.   30.jar$ -action=replace C:\temp\struts2-core-2.5.33.jar
       
       
       patch-archive.bat -root=C:\Users\labuser\Desktop\check -pattern=.         *struts2-core.jar$ -action=replace C:\Users\labuser\Desktop\struts2-core.   jar -action=replace C:\Users\labuser\Desktop\struts2-core.jar
       
       &quot;
       
       Ersetzen Sie den Pfad im obigen Befehl durch den Pfad Ihres AEM-Formularservers und die Datei &quot;struts2-core-2.5.33.jar&quot;.
   
1. Starten Sie Ihren AEM Forms-Server.


>[!TAB Linux]

1. Führen Sie den folgenden Befehl aus, um alle struts2 jar-Dateien aufzulisten:

       &quot;
       
       patch-archive.sh -root=\Users\labuser\Adobe\Adobe_Experience_Man ager_Forms\...\export -pattern=.         *struts2-core-2.5.30.jar$
       
       &quot;
       
       Ersetzen Sie den Pfad im obigen Befehl durch den Pfad Ihres AEM-Formularservers.
   
1. Führen Sie die folgenden Befehle zum rekursiven Ersetzen an Ort und Stelle aus:

       &quot;
       
       patch-archive.sh -root=\Users\labuser\Adobe\Adobe_Experience_Man ager_Forms\...\export -pattern=.         *struts2-core-2.5.30.jar$ -action=replace \temp\struts2-core-2.5.   33.jar
       
       
       patch-archive.sh -root=\Users\labuser\Desktop\check -pattern=.   *struts2-core.jar$ -action=replace \Users\labuser\Desktop\struts2-core.   jar -action=replace \Users\labuser\Desktop\struts2-core.jar
       
       &quot;
       
       Ersetzen Sie den Pfad im obigen Befehl durch den Pfad Ihres AEM-Formularservers und die Datei &quot;struts2-core-2.5.33.jar&quot;.
   
1. Starten Sie Ihren AEM Forms-Server.

>[!ENDTABS]




<!-- 
### Manual patching tool 


>[!BEGINTABS]

>[!TAB Windows]

    ```
    
    patch-archive.bat [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.

>[!TAB macOS]

    ```
    
    patch-archive.sh [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.  

>[!TAB Linux]

    ```
    
    patch-archive.sh [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.  



>[!ENDTABS]









-->