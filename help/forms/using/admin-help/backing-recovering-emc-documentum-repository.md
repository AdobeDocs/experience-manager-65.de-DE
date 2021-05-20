---
title: EMC Documentum-Repository sichern und wiederherstellen
seo-title: EMC Documentum-Repository sichern und wiederherstellen
description: In diesem Dokument werden die Aufgaben zum Sichern und Wiederherstellen des EMC Documentum-Repositorys beschrieben, das für Ihre AEM Forms-Umgebung konfiguriert ist.
seo-description: In diesem Dokument werden die Aufgaben zum Sichern und Wiederherstellen des EMC Documentum-Repositorys beschrieben, das für Ihre AEM Forms-Umgebung konfiguriert ist.
uuid: ab3b1fb1-25b3-4c95-801f-82d4b58f05ff
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f146202f-25f1-46a0-9943-c483f5f09f9f
exl-id: bc21659f-88d6-4dff-8baf-12746e1b3ed9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 88%

---

# EMC Documentum-Repository sichern und wiederherstellen {#backing-up-and-recovering-the-emc-documentum-repository}

In diesem Abschnitt werden die Aufgaben zum Sichern und Wiederherstellen des EMC Documentum-Repositorys beschrieben, das für Ihre AEM Forms-Umgebung konfiguriert ist.

>[!NOTE]
>
>Diese Anweisungen setzen voraus, dass AEM Forms mit Connectors für ECM und EMC Documentum Content Server ordnungsgemäß installiert und konfiguriert wurden.

Bei der Sicherung und Wiederherstellung gibt es zwei Hauptaufgaben:

* Sichern (oder Wiederherstellen) der AEM Forms-Umgebung
* Sichern (oder Wiederherstellen) von EMC Documentum Content Server

>[!NOTE]
>
>Sichern Sie die AEM Forms-Daten vor der Sicherung des EMC Documentum-Systems und stellen Sie anschließend das EMC Documentum-System vor der AEM Forms-Umgebung wieder her.

## Software-Anforderungen {#software-requirements}

Zum Durchführen der erforderlichen Sicherungsaufgaben auf dem Computer mit EMC Documentum Content Server erwerben Sie ein geeignetes Dienstprogramm wie EMC NetWorker von EMC oder CYA SmartRecovery(tm) for EMC Documentum von CYA. In den folgenden Anweisungen werden die Schritte für EMC NetWorker Module 7.2.2 beschrieben.

Sie benötigen die folgenden EMC NetWorker-Module:

* NetWorker Module
* NetWorker Configuration Wizard
* NetWorker Device Configuration Wizard
* NetWorker Module für den von Ihrem Content Server verwendeten Datenbanktyp
* NetWorker Module for Documentum

## EMC Document Content Server-Sicherung und -Wiederherstellung vorbereiten {#preparing-the-emc-document-content-server-for-backup-and-recovery}

In diesem Abschnitt wird die Installation und Konfiguration der EMC NetWorker-Software auf dem Server mit Content Server beschrieben.

**EMC Documentum-Server auf die Sicherung vorbereiten**

1. Installieren Sie auf EMC Documentum Content Server die EMC NetWorker-Module und übernehmen Sie alle Standardeinstellungen.

   Während des Installationsvorgangs werden Sie aufgefordert, den Namen des Servers, auf dem Content Server ausgeführt wird, als *NetWorker-Servernamen* einzugeben. Wählen Sie bei der Installation des EMC NetWorker-Moduls für Ihre Datenbank den Installationstyp „Complete“ aus.

1. Erstellen Sie anhand des folgenden Beispiels eine Konfigurationsdatei mit dem Namen *nsrnmd_win.cfg* und speichern Sie sie an einem freigegebenen Speicherort auf dem Computer mit Content Server. Diese Datei wird von den Sicherungs- und Wiederherstellungsbefehlen aufgerufen.

   Der folgende Text enthält Formatierungszeichen für Zeilenwechsel. Wenn dieser Text an eine Stelle außerhalb dieses Dokuments kopiert wird, kopieren Sie die Teile einzeln nacheinander und entfernen Sie die Formatierungszeichen, wenn der Text an der neuen Stelle eingefügt wird.

   ```shell
    ################################################
    # NetWorker Module for Documentum v1.2 nsrnmd_win.cfg D5.3+ example with
    # typical set of working parameters.  THIS FILE MUST BE SITE-CUSTOMISED.
    #
    # Parameters not shown can be set in this file (as per site customisation) #or from the command-line.
    #
    # Please refer to the user Guides for details on all parameters, including
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

   Lassen Sie das Kennwortfeld für die Konfigurationsdatei `NMDDE_DM_PASSWD` leer. Das Kennwort wird im nächsten Schritt festgelegt.

1. Legen Sie das Kennwort wie folgt in der Konfigurationsdatei fest:

   * Öffnen Sie eine Eingabeaufforderung und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
   * Führen Sie den folgenden Befehl aus: `-nsrnmdsv.exe -f`*&lt;path_to_cfg_file> -P &lt;password>*

1. Erstellen Sie die ausführbaren Batch-Dateien (.bat) zum Sichern der Datenbank. (Weitere Informationen finden Sie in der NetWorker-Dokumentation.) Legen Sie die Details in den Batch-Dateien gemäß Ihrer Installation fest.

   * Vollständige Datenbanksicherung (nsrnmddbf.bat):

      `NetWorker_database_module_root` `-s`*&lt;networker_server_name>* `-U``[username]` `-P`*[password ]*`-l full`*&lt;database_name>*

   * Inkrementelle Datenbanksicherung (nsrnmddbi.bat):

      `[NetWorker_database_module_root]` `-s`*&lt;networker_server_name>* `-U``[username]` `-P``[password]` `-l 1 -R`*&lt;database_name>*

   * Datenbankprotokollsicherung (nsrnmddbl.bat):

      `[NetWorker_database_module_root]` `-s``<NetWorker_Server_Name>` `-U``[username]` `-P``[password]` `-l incr -R`*&lt;database_name>*

      wobei:

      `[NetWorker_database_module_root]` ist der Installationsordner des NetWorker-Moduls. Der standardmäßige Installationsordner von NetWorker Module für SQL Server heißt „C:\Programme\Legato\nsr\bin\nsrsqlsv“.

      `NetWorker_Server_Name` ist der Server, auf dem NetWorker installiert ist.

      `username` &amp;  `password` sind der Benutzername und das Kennwort des Datenbankadministrator-Benutzers.

      `database_name` ist der Name der zu sichernden Datenbank.

**Sicherungsgerät erstellen**

1. Erstellen Sie auf dem Server mit EMC Documentum einen neuen Ordner und geben Sie den Ordner unter Erteilung voller Zugriffsrechte für alle Benutzer frei.
1. Starten Sie EMC NetWorker Administrator und klicken Sie auf „Media Management“ > „Devices“.
1. Klicken Sie mit der rechten Maustaste auf „Geräte“ und wählen Sie „Erstellen“ aus.
1. Geben Sie die folgenden Werte ein und klicken Sie auf „OK“:

   **Name:** Der vollständige Pfad des freigegebenen Ordners

   **Medientyp:** `File`

1. Klicken Sie mit der rechten Maustaste auf das neue Gerät und wählen Sie Operations aus.
1. Klicken Sie auf „Label“, geben Sie einen Namen ein, klicken Sie auf „OK“ und klicken Sie dann auf „Mount“.

Ein Gerät wird hinzugefügt, auf dem die gesicherten Dateien gespeichert werden. Sie können mehrere Geräte mit verschiedenen Formaten hinzufügen.

## EMC Documentum Content Server sichern  {#back-up-the-emc-documentum-content-server}

Führen Sie die folgenden Schritte aus, nachdem Sie eine vollständige Sicherung Ihrer AEM Forms-Daten erstellt haben. (Siehe [Sichern der AEM Forms-Daten](/help/forms/using/admin-help/backing-aem-forms-data.md#backing-up-the-aem-forms-data).)

>[!NOTE]
>
>Für die Befehlsskripts ist der vollständige Pfad der Datei „nsrnmd_win.cfg“ erforderlich, die Sie unter [EMC Document Content Server-Sicherung und -Wiederherstellung vorbereiten](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery) erstellt haben.

1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
1. Führen Sie folgenden Befehl aus:

   ```shell
    - nsrnmdsv.exe -f <path_to_cfg_file>
   ```

## EMC Documentum Content Server wiederherstellen  {#restore-the-emc-documentum-content-server}

Führen Sie vor der Wiederherstellung der AEM Forms-Daten die folgenden Aufgaben aus: (Siehe[ Wiederherstellen der AEM Forms-Daten](/help/forms/using/admin-help/recovering-aem-forms-data.md#recovering-the-aem-forms-data).)

>[!NOTE]
>
>Für die Befehlsskripts ist der vollständige Pfad der Datei „nsrnmd_win.cfg“ erforderlich, die Sie unter [EMC Document Content Server-Sicherung und -Wiederherstellung vorbereiten](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery) erstellt haben.

1. Beenden Sie den Docbase-Dienst, den Sie wiederherstellen.
1. Starten Sie das NetWorker User-Dienstprogramm für Ihr Datenbankmodul (z. B. *NetWorker User for SQL Server*).
1. Klicken Sie auf die Option „Restore“ und wählen Sie „Normal“ aus.
1. Wählen Sie auf der linken Bildschirmseite die Datenbank für Ihren Docbase-Dienst aus und klicken Sie in der Symbolleiste auf „Start“.
1. Starten Sie, nachdem die Datenbank wiederhergestellt wurde, den Docbase-Dienst.
1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zu *[NetWorker_root]*\Legato\nsr\bin
1. Führen Sie folgenden Befehl aus:

   ```shell
    - nsrnmdrs.exe -B <docbase_name> -f <path_to_cfg_file> -C SA
   ```
