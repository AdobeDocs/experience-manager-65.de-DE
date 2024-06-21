---
title: Sichern und Wiederherstellen des EMC Documentum-Repositorys
description: In diesem Dokument werden die Aufgaben zum Sichern und Wiederherstellen des EMC Documentum-Repositorys beschrieben, das für Ihre AEM Forms-Umgebung konfiguriert ist.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: bc21659f-88d6-4dff-8baf-12746e1b3ed9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 100%

---

# Sichern und Wiederherstellen des EMC Documentum-Repositorys {#backing-up-and-recovering-the-emc-documentum-repository}

In diesem Abschnitt werden die Aufgaben zum Sichern und Wiederherstellen des EMC Documentum-Repositorys beschrieben, das für Ihre AEM Forms-Umgebung konfiguriert ist.

>[!NOTE]
>
>Diese Anweisungen setzen voraus, dass AEM Forms mit Connectoren für ECM und EMC Documentum Content Server ordnungsgemäß installiert und konfiguriert wurde.

Bei der Sicherung und Wiederherstellung gibt es zwei Hauptaufgaben:

* Sichern (oder Wiederherstellen) der AEM Forms-Umgebung
* Sichern (oder Wiederherstellen) von EMC Documentum Content Server

>[!NOTE]
>
>Sichern Sie die AEM Forms-Daten vor der Sicherung des EMC Documentum-Systems und stellen Sie später das EMC Documentum-System vor der AEM Forms-Umgebung wieder her.

## Software-Anforderungen {#software-requirements}

Zum Durchführen der erforderlichen Sicherungsaufgaben auf dem EMC Documentum Content Server-Computer erwerben Sie ein geeignetes Drittanbieter-Dienstprogramm wie EMC NetWorker von EMC oder CYA SmartRecovery for EMC Documentum von CYA. In den folgenden Anweisungen werden die Schritte für EMC NetWorker Module 7.2.2 beschrieben.

Sie benötigen die folgenden EMC NetWorker-Module:

* NetWorker Module
* NetWorker Configuration Wizard
* NetWorker Device Configuration Wizard
* NetWorker Module für den von Ihrem Content Server verwendeten Datenbanktyp
* NetWorker Module for Documentum

## Vorbereiten der EMC Document Content Server-Sicherung und -Wiederherstellung {#preparing-the-emc-document-content-server-for-backup-and-recovery}

In diesem Abschnitt wird die Installation und Konfiguration der EMC NetWorker-Software auf dem Content Server-Computer beschrieben.

**Vorbereiten des EMC Documentum-Servers auf die Sicherung**

1. Installieren Sie auf dem EMC Documentum Content Server-Computer die EMC NetWorker-Module und übernehmen Sie alle Standardeinstellungen.

   Während der Installation werden Sie aufgefordert, den Server-Namen des Content Server-Computers als *NetWorker-Server-Namen* einzugeben. Wählen Sie bei der Installation des EMC NetWorker-Moduls für Ihre Datenbank eine vollständige Installation aus.

1. Erstellen Sie anhand des folgenden Beispiels eine Konfigurationsdatei mit dem Namen *nsrnmd_win.cfg* und speichern Sie sie an einem zugänglichen Speicherort auf dem Content Server-Computer. Diese Datei wird von den Sicherungs- und Wiederherstellungsbefehlen aufgerufen.

   Der folgende Text enthält Formatierungszeichen für Zeilenwechsel. Wenn dieser Text an eine Stelle außerhalb dieses Dokuments kopiert wird, kopieren Sie die Teile einzeln nacheinander und entfernen Sie die Formatierungszeichen, wenn Sie den Text an der neuen Stelle einfügen.

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

   Lassen Sie das Feld für das Passwort der Konfigurationsdatei `NMDDE_DM_PASSWD` leer. Das Kennwort wird im nächsten Schritt festgelegt.

1. Legen Sie das Kennwort wie folgt in der Konfigurationsdatei fest:

   * Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
   * Führen Sie den folgenden Befehl aus: `-nsrnmdsv.exe -f`*&lt;path_to_cfg_file> -P &lt;password>*

1. Erstellen Sie die ausführbaren Batch-Dateien (.bat) zum Sichern der Datenbank. (Weitere Informationen finden Sie in der NetWorker-Dokumentation.) Legen Sie die Details in den Batch-Dateien gemäß Ihrer Installation fest.

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

1. Erstellen Sie auf dem Server mit EMC Documentum ein Verzeichnis und geben Sie den Ordner unter Erteilung voller Zugriffsrechte für alle Benutzenden frei.
1. Starten Sie EMC NetWorker Administrator und klicken Sie auf „Medienverwaltung“ > „Geräte“.
1. Klicken Sie mit der rechten Maustaste auf „Geräte“ und wählen Sie „Erstellen“ aus.
1. Geben Sie die folgenden Werte ein und klicken Sie auf „OK“:

   **Name:** Der vollständige Pfad des freigegebenen Verzeichnisses

   **Medientyp:** `File`

1. Klicken Sie mit der rechten Maustaste auf das neue Gerät und wählen Sie „Operationen“ aus.
1. Klicken Sie auf „Bezeichnung“, geben Sie einen Namen ein, klicken Sie auf „OK“ und klicken Sie dann auf „Mounten“.

Es wird ein Gerät hinzugefügt, auf dem die gesicherten Dateien gespeichert werden. Sie können mehrere Geräte mit verschiedenen Formaten hinzufügen.

## Sichern des MC Documentum Content Servers {#back-up-the-emc-documentum-content-server}

Führen Sie die folgenden Schritte aus, nachdem Sie eine vollständige Sicherung Ihrer AEM Forms-Daten erstellt haben. (Siehe [Sichern der AEM Forms-Daten](/help/forms/using/admin-help/backing-aem-forms-data.md#backing-up-the-aem-forms-data).)

>[!NOTE]
>
>Für die Befehlsskripte ist der vollständige Pfad der Datei „nsrnmd_win.cfg“ erforderlich, die Sie unter [Vorbereiten der EMC Document Content Server-Sicherung und -Wiederherstellung](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery) erstellt haben.

1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zu `[NetWorker_root]\Legato\nsr\bin`.
1. Führen Sie den folgenden Befehl aus:

   ```shell
    - nsrnmdsv.exe -f <path_to_cfg_file>
   ```

## Wiederherstellen des EMC Documentum Content Servers {#restore-the-emc-documentum-content-server}

Führen Sie vor der Wiederherstellung der AEM Forms-Daten die folgenden Aufgaben aus: (Siehe [Wiederherstellen der AEM Forms-Daten](/help/forms/using/admin-help/recovering-aem-forms-data.md#recovering-the-aem-forms-data).)

>[!NOTE]
>
>Für die Befehlsskripte ist der vollständige Pfad der Datei „nsrnmd_win.cfg“ erforderlich, die Sie unter [Vorbereiten der EMC Document Content Server-Sicherung und -Wiederherstellung](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery) erstellt haben.

1. Beenden Sie den Docbase-Dienst, den Sie wiederherstellen.
1. Starten Sie das NetWorker User-Dienstprogramm für Ihr Datenbankmodul (z. B. *NetWorker User for SQL Server*).
1. Klicken Sie auf das Tool zum Wiederherstellen und wählen Sie „Normal“ aus.
1. Wählen Sie auf der linken Bildschirmseite die Datenbank für Ihren Docbase-Dienst aus und klicken Sie in der Symbolleiste auf „Start“.
1. Starten Sie, nachdem die Datenbank wiederhergestellt wurde, den Docbase-Dienst.
1. Öffnen Sie eine Eingabeaufforderung und wechseln Sie zum Ordner „*[NetWorker-Stammordner]*\Legato\nsr\bin“
1. Führen Sie den folgenden Befehl aus:

   ```shell
    - nsrnmdrs.exe -B <docbase_name> -f <path_to_cfg_file> -C SA
   ```
