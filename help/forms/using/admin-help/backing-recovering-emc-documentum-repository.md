---
title: Sichern und Wiederherstellen des EMC Documentum-Repositorys
description: In diesem Dokument werden die Aufgaben beschrieben, die zum Sichern und Wiederherstellen des für Ihre AEM Forms-Umgebung konfigurierten EMC Documentum-Repositorys erforderlich sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: bc21659f-88d6-4dff-8baf-12746e1b3ed9
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 18%

---

# Sichern und Wiederherstellen des EMC Documentum-Repositorys {#backing-up-and-recovering-the-emc-documentum-repository}

In diesem Abschnitt werden die Aufgaben beschrieben, die zum Sichern und Wiederherstellen des für Ihre AEM Forms-Umgebung konfigurierten EMC Documentum-Repositorys erforderlich sind.

>[!NOTE]
>
>Bei diesen Anweisungen wird davon ausgegangen, dass AEM Forms mit Connectors für ECM und EMC Documentum Content Server installiert und entsprechend konfiguriert sind.

Für die Sicherungs- und Wiederherstellungsprozesse gibt es zwei Hauptaufgaben:

* Sichern (oder Wiederherstellen) der AEM Formularumgebung
* Sichern (oder Wiederherstellen) des EMC Documentum Content Servers

>[!NOTE]
>
>Sichern Sie Ihre AEM Formulardaten, bevor Sie das EMC Documentum-System sichern, und stellen Sie anschließend das EMC Documentum-System wieder her, bevor Sie die AEM Forms-Umgebung wiederherstellen.

## Softwareanforderungen {#software-requirements}

Um die erforderlichen Backup-Aufgaben auf Ihrem EMC Documentum Content Server durchzuführen, erwerben Sie ein geeignetes Dienstprogramm von Drittanbietern wie EMC NetWorker von EMC oder CYA SmartRecovery für EMC Documentum von CYA. Die folgenden Anweisungen beschreiben die Schritte zur Verwendung des EMC NetWorker-Moduls Version 7.2.2.

Sie benötigen die folgenden EMC NetWorker-Module:

* NetWorker-Modul
* NetWorker Configuration Wizard
* NetWorker Device Configuration Wizard
* NetWorker-Modul für den von Ihrem Content Server verwendeten Datenbanktyp
* NetWorker-Modul für Documentum

## EMC Document Content Server auf Sicherung und Wiederherstellung vorbereiten {#preparing-the-emc-document-content-server-for-backup-and-recovery}

In diesem Abschnitt wird die Installation und Konfiguration der EMC NetWorker-Software auf dem Content Server beschrieben.

**EMC Documentum-Server auf Sicherung vorbereiten**

1. Installieren Sie auf dem EMC Documentum Content Server die EMC NetWorker-Module und akzeptieren Sie alle Standardwerte.

   Während des Installationsprozesses werden Sie aufgefordert, den Servernamen des Content Server-Computers als *NetWorker Server-Name*. Wählen Sie bei der Installation des EMC NetWorker-Moduls für Ihre Datenbank eine &quot;Complete&quot;-Installation.

1. Erstellen Sie mithilfe des unten stehenden Beispielinhalts eine Konfigurationsdatei mit dem Namen *nsrnmd_win.cfg* und speichern Sie sie an einem zugänglichen Speicherort auf dem Content Server. Diese Datei wird von den Sicherungs- und Wiederherstellungsbefehlen aufgerufen.

   Der folgende Text enthält Formatierungszeichen für Zeilenumbrüche. Wenn Sie diesen Text an eine Stelle außerhalb dieses Dokuments kopieren, kopieren Sie jeweils einen Teil und entfernen Sie die Formatierungszeichen, wenn Sie ihn an der neuen Position einfügen.

   ```shell
    ################################################
    # NetWorker Module for Documentum v1.2 nsrnmd_win.cfg D5.3+ example with
    # typical set of working parameters.  THIS FILE MUST BE SITE-CUSTOMISED.
    #
    # Parameters not shown can be set in this file (as per site customisation) #or from the command-line.
    #
    # See the user Guides for details on all parameters, including
    # those not listed below.
    # Note: DCTM environment for D6 is slightly different from D5, refer to D6
    # Installation Guide to update the values.
    ################################################
    #Can get values for most of below from doing as the dctm inst owner: cmd> set DOCUMENTUM=C:\Documentum
    DM_HOME=C:\Documentum\product\6.0
    JAVA_HOME=C:\Progra~1\Documentum\java\1.5.0_12
    JAVA_PATH=C:\Progra~1\Documentum\java\1.5.0_12\bin
    PATH=C:\WINNT\system32;C:\WINNT;C:\WINNT\system32\WBEM;C:\Documentum\product\6.0\bin;C:\Documentum\fulltext\fast;C:\Documentum\product\6.0\fusion;C:\Program Files\Documentum\Shared;C:\Program Files\Legato\nsr\bin;C:\Program Files\Microsoft SQL Server\80\Tools\Binn;C:\Program Files\Microsoft SQL Server\90\DTS\Binn\;C:\Program Files\Microsoft SQL Server\90\Tools\binn;C:\Program Files\Microsoft SQL Server\90\Tools\Binn\VSShell\Common7\IDE;C:\Program Files\Documentum\java\1.5.0_12\bin;C:\Documentum\config;C:\Documentum
    #See also manifest dctm.jar file for class path locations
    CLASSPATH=.;C:\Program Files\Legato\nsr\bin;C:\Program Files\Legato\nsr\bin\nsrnmdde.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\tools.jar;C:\Program Files\Documentum\Shared\dfc.jar;C:\Program Files\Documentum\Shared\aspectjrt.jar;C:\Program Files\Documentum\dctm.jar;C:\Program Files\Documentum\Shared\workflow.jar;C:\Program Files\Documentum\Shared\log4j.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\dt.jar;C:\Documentum\config
   
    ################################################
    #If not using nsrnmdsv -m ALL|DB|DB_LOG|FTI|FTI_ALL|ICF|SA|SA_ALL, set #for backup
    NMD_SCOPE=ALL
    #Mandatory when scope (backup or restore) is FTI/SA without -a option
    #NMD_OBJECT_NAME=filestore_01
    ################################################
    NMDDE_DM_DOCBASE=Docbase
    NMDDE_DM_USER=Administrator
    #NMDDE_DM_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd>.
    ################################################
    #DB related hooks to invoke arbitrary scripts:
    #Set if DB is on a remote host
    #NMD_DB_HOST=dbhost
    #Pure basename implies remote host execution; absolute path ... local
    #execution as in NMD v1.0.
    #
    #Remote execution requires script be put in remote nsrexecd bin directory
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd recycled
    #
    #Refer to user Guides for sample script code.
    NMD_DB_FULL_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbf.bat
    NMD_DB_LOG_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbl.bat
    NMD_DB_INCR_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbi.bat
    ################################################
    #For D5.3+ only: NMD_FTI_INCLUDED, NMD_FTI_HOST, NMD_FTI_USER,
    #NMD_FTI_PASSWD & NMD_FTI_SUBDIRS.
    #Optional for remote D5.3+ FTI server
    NMD_FTI_INCLUDED=no
    #NMD_FTI_HOST=ftihost
    #Recommended for D5.3+ FTI server quiesce/unquiesce
    #NMD_FTI_USER=ftiadmin
    #The index name: optional for D5.3+ FTI server, used with -M FTI_ALL or
    #-M ALL
    #NMD_FTI_NAME=rep_name_ftindex_01
    #Recommended for D5.3+ FTI server quiesce/unquiesce
    #NMDDE_FTI_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd>
    #-M FTI.
    #Pure basename implies remote host execution; absolute path ... local execution
    #as in NMD v1.0.
    #
    #Remote execution requires script be put in remote nsrexecd bin directory
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd
    #recycled.
    #
    #See example nsrnmdfti*.bat examples.
    #
    #Mandatory for D5.3+
    #NMD_BACKUP_FTI_QUIESCE=nsrnmdftiq.bat
    #NMD_BACKUP_FTI_UNQUIESCE=nsrnmdftiu.bat
    #Used for D5.3+ to get InstallProfile.xml FTI file in multinode
    #discovery.
    #Optional, if not specified, will treat as single-node FTI.
    #NMD_FTI_GET_INSTPROF=nsrnmdfti_instprof.bat
    #Mandatory for D5.3+. No spaces in paths or around comma separators.
    #For remote FTI, paths must be valid at the FTI host.
    #NMD_FTI_SUBDIRS=F:\Documentum_idx\data\fulltext\fixml,F:\Documentum_idx
    #\data\fulltext\index
    ################################################
    #Mandatory. No spaces in paths or before comma
    #separators in NMD_ICF_SUBDIRS_xxx:
    #NMD_ICF_INCLUDED=yes
    #NMD_ICF_SUBDIRS=C:\Documentum\dba,C:\Documentum\product\5.3
    ################################################
    NMD_FILEREPORT_INCLUDED=yes
    NMDDE_METADATA_OUTPUT_DEST=C:\docbase_freports\
    ################################################
    #Other misc recommended NMD_xxx parameters
    #Recommended to get more meaningful saveset names
    NMD_USE_DEFAULT_SAVESET_NAMES=yes
    #Use following to skip unwanted ICF, FTI and non-SnapImage SA dirs/files.
    #For example, "<</>> +skip: dm_ftwork_dir" line will skip non-data
    #files.
    #
    #The path will be the same and must exist on D5.3+, remote FTI host, and
    #RCS hosts correspondingly if used.
    #NMD_DIRECTIVES_FILE=E:\Program Files\Legato\nsr\res\nsrnmddirectives.txt
    #For non-SnapImage SA backup
    #NMD_SA_FULL_NUM_SAVESET=16
    #NMD_SA_INCR_NUM_SAVESET=4
    #NMD_USE_SNAPIMAGE=yes
    ################################################
    # DSA setup
    ################################################
    # Name of the config file at the remote sites;
    # Mandatory, listed in the config file at the primary host.
    # (if skipped, backup is treated as local)
    # NMD_RCS_CFG_FILE=rep_name_rcs.cfg
   
    # SA-host mapping add, optional, will override far-store list info.
    # No space around comma.
    # NMD_HOST_SAS_MAP=host01,sa_01,sa_02
    # NMD_HOST_SAS_MAP=host02,sa_03
    ################################################
    NSR_SERVER=con-dctm
    #NSR_CLIENT=d5svrhost
    NSR_GROUP=Default
    NSR_DATA_VOLUME_POOL=Default
    #NSR_SNAPIMAGE_DATA_VOLUME_POOL=Default
    #Relocation dir will be the same on D5+ and remote FTI/SA hosts.
    NSR_RELOCATION=C:\reloc
    #NSR_PARALLELISM=16
    NSR_DEBUG_FILE=C:\Program Files\Legato\nsr\applogs\nmd.log
    NSR_DEBUG_LEVEL=9
    ################################################
    NMDDE_DM_PASSWD=XAtup9pl
   ```

   Lassen Sie das Feld für das Passwort der Konfigurationsdatei `NMDDE_DM_PASSWD` leer. Sie legen das Kennwort im nächsten Schritt fest.

1. Legen Sie das Kennwort für die Konfigurationsdatei wie folgt fest:

   * Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
   * Führen Sie den folgenden Befehl aus: `-nsrnmdsv.exe -f`*&lt;path_to_cfg_file> -P &lt;password>*

1. Erstellen Sie die ausführbaren Batch-Dateien (.bat), die zum Sichern der Datenbank verwendet werden. (Siehe NetWorker-Dokumentation.) Legen Sie die Details in den Batch-Dateien entsprechend Ihrer Installation fest.

   * Vollständige Datenbanksicherung (nsrnmddbf.bat):

     `NetWorker_database_module_root` `-s`*&lt;networker_server_name>* `-U``[username]` `-P`*[password ]*`-l full`*&lt;database_name>*

   * Inkrementelle Datenbanksicherung (nsrnmddbi.bat):

     `[NetWorker_database_module_root]` `-s`*&lt;NetWorker_Server_Name>* `-U``[username]` `-P``[password]` `-l 1 -R`*&lt;database_name>*

   * Datenbankprotokollsicherung (nsrnmddbl.bat):

     `[NetWorker_database_module_root]` `-s``<NetWorker_Server_Name>` `-U``[username]` `-P``[password]` `-l incr -R`*&lt;database_name>*

     Dabei gilt:

     `[NetWorker_database_module_root]` ist der Installationsordner des NetWorker-Moduls. Der standardmäßige Installationsordner von NetWorker Module für SQL Server heißt „C:\Programme\Legato\nsr\bin\nsrsqlsv“.

     `NetWorker_Server_Name` ist der Server, auf dem NetWorker installiert ist.

     `username` &amp; `password` sind der Benutzername und das Kennwort des Datenbankadministrator-Benutzers.

     `database_name` ist der Name der Datenbank, die gesichert werden soll.

**Erstellen eines Sicherungsgeräts**

1. Erstellen Sie einen Ordner auf dem EMC Documentum-Server und geben Sie den Ordner frei, indem Sie allen Benutzern volle Berechtigungen erteilen.
1. Starten Sie EMC NetWorker Administrator und klicken Sie auf Media Management > Geräte.
1. Klicken Sie mit der rechten Maustaste auf Geräte und wählen Sie Erstellen aus.
1. Geben Sie die folgenden Werte ein und klicken Sie auf OK:

   **Name:** Der vollständige Pfad des freigegebenen Ordners

   **Medientyp:** `File`

1. Klicken Sie mit der rechten Maustaste auf das neue Gerät und wählen Sie &quot;Vorgänge&quot;.
1. Klicken Sie auf &quot;Titel&quot;, geben Sie einen Namen ein, klicken Sie auf &quot;OK&quot;und anschließend auf &quot;Bereiten&quot;.

Ein Gerät wird hinzugefügt, auf dem die gesicherten Dateien gespeichert werden. Sie können mehrere Geräte mit verschiedenen Formaten hinzufügen.

## EMC Documentum Content Server sichern {#back-up-the-emc-documentum-content-server}

Führen Sie die folgenden Aufgaben aus, nachdem Sie eine vollständige Sicherung der AEM Formulardaten abgeschlossen haben. (Siehe [Sichern der AEM Formulardaten](/help/forms/using/admin-help/backing-aem-forms-data.md#backing-up-the-aem-forms-data).

>[!NOTE]
>
>Die Befehlsskripte erfordern den vollständigen Pfad zur Datei &quot;nsrnmd_win.cfg&quot;, die Sie in der [EMC Document Content Server auf Sicherung und Wiederherstellung vorbereiten](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
1. Führen Sie den folgenden Befehl aus:

   ```shell
    - nsrnmdsv.exe -f <path_to_cfg_file>
   ```

## EMC Documentum Content Server wiederherstellen {#restore-the-emc-documentum-content-server}

Führen Sie die folgenden Aufgaben aus, bevor Sie Ihre AEM Formulardaten wiederherstellen. (Siehe [Wiederherstellen der AEM Formulardaten](/help/forms/using/admin-help/recovering-aem-forms-data.md#recovering-the-aem-forms-data).

>[!NOTE]
>
>Die Befehlsskripte erfordern den vollständigen Pfad zur Datei &quot;nsrnmd_win.cfg&quot;, die Sie in der [EMC Document Content Server auf Sicherung und Wiederherstellung vorbereiten](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Beenden Sie den Docbase-Dienst, den Sie wiederherstellen.
1. Starten Sie das NetWorker User-Dienstprogramm für Ihr Datenbankmodul (beispielsweise *NetWorker User for SQL Server*).
1. Klicken Sie auf das Tool Wiederherstellen und wählen Sie dann Normal aus.
1. Wählen Sie auf der linken Bildschirmseite die Datenbank für Ihre Docbase aus und klicken Sie in der Symbolleiste auf die Schaltfläche Starten .
1. Starten Sie nach der Wiederherstellung der Datenbank den Docbase-Dienst neu.
1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zum Ordner „*[NetWorker-Stammordner]*\Legato\nsr\bin“
1. Führen Sie den folgenden Befehl aus:

   ```shell
    - nsrnmdrs.exe -B <docbase_name> -f <path_to_cfg_file> -C SA
   ```
