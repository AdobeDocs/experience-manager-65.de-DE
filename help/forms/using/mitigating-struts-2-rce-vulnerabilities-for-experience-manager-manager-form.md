---
title: Behebung von Struts 2 Schwachstellen für Experience Manager Forms auf JEE
description: Behebung von Struts 2 Schwachstellen für Experience Manager Forms auf JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 73b5aff2-1320-4d9a-8972-54c4fdd3a2c2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, Troubleshooting
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 100%

---

# Behebung von Struts 2 Schwachstellen für Experience Manager Forms {#mitigatin-struts2-rce-vulnerabilities-for-aem-forms}

## Problem

In Struts 2, einem beliebten Open-Source-Framework für die Entwicklung von Java EE-Webanwendungen, wurden kritische Sicherheitslücken entdeckt. Die folgenden Schwachstellen wurden analysiert:

| Schwachstelle | Was ist betroffen? | Was ist nicht betroffen? |
|---|---|---|
| [CVE-2023-50164](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2023-50164) | Experience Manager 6.5 Forms auf JEE (alle Versionen von 6.5 GA bis 6.5.19.0) | <ul><li> Experience Manager Forms Workbench (alle Versionen)</li> <li> Experience Manager Forms auf OSGi (alle Versionen) </li> <li> Experience Manager Forms as a Cloud Service </li> <ul> |

## Auflösung

In der folgenden Tabelle ist die Auflösung für alle betroffenen Versionen aufgeführt:

| Freigabe | Aktuelle Version | Benutzeraktion |
|---|---|---|
| Experience Manager 6.5 Forms auf JEE | 6.5.19.0 | [Installieren Sie die neueste Version des Service Packs](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de) |
| Experience Manager 6.5 Forms auf JEE | 6.5.13.0 – 6.5.18.0 | Wenden Sie eine der folgenden Methoden an: <ul><li>  <a href="https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de">Installieren Sie die neueste Version des Service Packs </a> </li> <li> <a href ="#use-manual-mitigation-steps"> Verwenden Sie manuelle Abhilfemaßnahmen </a> |
| Experience Manager 6.5 Forms auf JEE | 6.5 – 6.5.12.0 | [Installieren Sie die neueste Version des Service Packs](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de)  </br> </br> **HINWEIS:** AEM Forms unterstützt derzeit die Versionen 6.5.13.0 bis 6.5.19.0. Wenn Sie eine ältere Version verwenden, empfehlen wir ein Upgrade auf 6.5.13.0 oder eine spätere Version. Anweisungen zur Installation von AEM 6.5.13.0 oder einer späteren Version finden Sie in den Versionshinweisen. |

### Verwenden manueller Abhilfemaßnahmen {#use-manual-mitigation-steps}

Sie können die manuellen Abhilfemaßnahmen verwenden, um das Problem auf AEM 6.5 Form Server mit Service Pack 13 auf AEM 6.5 Form Server mit Service Pack 18 (6.5.13.0 – 6.5.18.0) zu beheben:

1. Laden Sie die Datei [struts-core 2.5.33 jar](https://repo1.maven.org/maven2/org/apache/struts/struts2-core/2.5.33/struts2-core-2.5.33.jar) in einen lokalen Ordner. Beispiel: C:\Users\labuser\Desktop\struts2-core-2.5.33.jar.
1. Laden Sie das manuelle Patching Tool für AEM Forms auf JEE von der [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/patch_utility/archive-patcher-1.0.0.zip) herunter.
1. Entpacken Sie das Archiv des manuellen Patching Tools.  Extrahieren Sie es beispielsweise in den `/Users/labuser/Desktop/archive-patcher-1.0.0 folder`. Die folgenden Dateien werden extrahiert:
   * archive-patcher-1.0.0.jar
   * patch-archive.bat
   * patch-archive.sh

>[!BEGINTABS]

>[!TAB Windows]

1. Fahren Sie alle Server-Instanzen und Locator herunter.

1. Öffnen Sie das Terminal-Fenster und navigieren Sie zu dem Ordner mit dem AEM Forms on JEE Manual Patching Tool (extrahierte Dateien). 

1. Führen Sie den folgenden Befehl aus, um alle Dateien mit älteren struts2-Bibliotheken zu durchsuchen. Ersetzen Sie vor Ausführung des Befehls den Pfad im Befehl durch den Pfad Ihres AEM Forms-Servers:


   ```
   patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\configurationManager\export -pattern=.*struts2-core.*jar$
   ```

   >[!NOTE]
   >
   >
   >Das Tool benötigt eine Internet-Verbindung, da es Abhängigkeiten zur Laufzeit herunterlädt. Stellen Sie daher vor Ausführung des Tools sicher, dass Sie mit dem Internet verbunden sind.

1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um rekursive In-place-Ersetzungen durchzuführen. Ersetzen Sie vor Ausführung des Befehls den Pfad im Befehl durch den Pfad Ihres AEM Forms-Servers und die Datei `struts2-core-2.5.33.jar`.



   ```
   patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\configurationManager\export -pattern=.*struts2-core.*jar$ -action=replace C:\Users\labuser\Desktop\struts2-core-2.5.33.jar
   ```

   Mit den obigen Schritten werden alle EAR-Dateien mit älteren struts2-Bibliotheken gepatcht.

1. Heben Sie die Bereitstellung der älteren EAR-Datei auf und stellen Sie die gepatchte EAR-Datei im Ordner „export“ auf Ihrem Anwendungs-Server bereit.

1. Starten Sie den AEM Forms-Server.

>[!TAB Linux]

1. Fahren Sie alle Server-Instanzen und Locator herunter.

1. Öffnen Sie das Terminal-Fenster und navigieren Sie zu dem Ordner mit dem AEM Forms on JEE Manual Patching Tool (extrahierte Dateien). 

1. Führen Sie den folgenden Befehl aus, um alle Dateien mit älteren struts2-Bibliotheken zu durchsuchen. Ersetzen Sie vor Ausführung des Befehls den Pfad im Befehl durch den Pfad Ihres AEM Forms-Servers:


   ```
   ./patch-archive.sh -root=/opt/Adobe/Adobe_Experience_Manager_Forms/configurationManager/export/ -pattern=.*struts2-core.*jar$
   ```

   >[!NOTE]
   >
   >
   >Das Tool benötigt eine Internet-Verbindung, da es Abhängigkeiten zur Laufzeit herunterlädt. Stellen Sie daher vor Ausführung des Tools sicher, dass Sie mit dem Internet verbunden sind.

1. Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um rekursive In-place-Ersetzungen durchzuführen. Ersetzen Sie vor Ausführung des Befehls den Pfad im Befehl durch den Pfad Ihres AEM Forms-Servers und die Datei `struts2-core-2.5.33.jar`.



   ```
   ./patch-archive.sh -root=/opt/Adobe/Adobe_Experience_Manager_Forms/configurationManager/export/ -pattern=.*struts2-core.*jar$ -action=replace /opt/struts2-core-2.5.33.jar
   ```

   Mit den obigen Schritten werden alle EAR-Dateien mit älteren struts2-Bibliotheken gepatcht.

1. Heben Sie die Bereitstellung der älteren EAR-Datei auf und stellen Sie die gepatchte EAR-Datei im Ordner „export“ auf Ihrem Anwendungs-Server bereit.

1. Starten Sie den AEM Forms-Server.

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
