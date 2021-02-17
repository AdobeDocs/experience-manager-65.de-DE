---
title: Vewenden des VLT-Tools
seo-title: Vewenden des VLT-Tools
description: Das Jackrabbit FileVault Tool (VLT) wurde von The Apache Foundation entwickelt und ordnet den Inhalt einer Jackrabbit/AEM-Instanz Ihrem Dateisystem zu
seo-description: Das Jackrabbit FileVault Tool (VLT) wurde von The Apache Foundation entwickelt und ordnet den Inhalt einer Jackrabbit/AEM-Instanz Ihrem Dateisystem zu
uuid: 579e7785-8b50-4366-b562-8e79b6451464
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a76425e9-fd3b-4c73-80f9-0ebabb8fd94f
translation-type: tm+mt
source-git-commit: 2da3da1a36f074593e276ddd15ed8331239ab70f
workflow-type: tm+mt
source-wordcount: '2748'
ht-degree: 62%

---


# Verwendung des VLT-Tools {#how-to-use-the-vlt-tool}

Das Jackrabbit FileVault Tool (VLT) ist ein von [The Apache Foundation](https://www.apache.org/) entwickeltes Tool, das den Inhalt einer Jackrabbit/AEM-Instanz Ihrem Dateisystem zuordnet. Das VLT-Tool hat ähnliche Funktionen wie der Quellkontrollsystem-Client (z. B. ein Subversion (SVN)-Client) und bietet normale Eincheck-, Auscheck- und Verwaltungsvorgänge sowie Konfigurationsoptionen für die flexible Darstellung des Projektinhalts.

Sie führen das VLT-Tool von der Befehlszeile aus. In diesem Dokument wird beschrieben, wie Sie das Tool verwenden, einschließlich der ersten Schritte und der Hilfe sowie einer Liste aller [Befehle](#vlt-commands) und verfügbaren [Optionen](#vlt-global-options).

## Konzepte und Architektur {#concepts-and-architecture}

Eine ausführliche Übersicht über die Konzepte und die Struktur des Filevault-Werkzeugs finden Sie auf den Seiten [Filevault-Übersicht](https://jackrabbit.apache.org/filevault/overview.html) und [Vault FS](https://jackrabbit.apache.org/filevault/vaultfs.html) in der offiziellen [Apache Jackrabbit Filevault-Dokumentation](https://jackrabbit.apache.org/filevault/index.html).

## Erste Schritte mit VLT {#getting-started-with-vlt}

Um VLT verwenden zu können, müssen Sie folgende Schritte ausführen:

1. Installieren Sie VLT, aktualisieren Sie die Umgebungsvariablen und aktualisieren Sie die global ignorierten Subversion-Dateien.
1. Richten Sie das AEM-Repository ein (falls Sie dies nicht bereits getan haben).
1. Überprüfen Sie das AEM-Repository.
1. Synchronisieren Sie mit dem Repository.
1. Testen Sie, ob die Synchronisierung funktioniert hat.

### Installieren des VLT-Tools {#installing-the-vlt-tool}

Um das VLT-Tool zu verwenden, müssen Sie zunächst das Programm installieren. Es wird nicht standardmäßig installiert, da es sich um ein zusätzliches Tool handelt. Außerdem müssen Sie die Umgebungsvariable Ihres Systems festlegen.

1. Laden Sie die Archivdatei FileVault aus dem Archiv [Maven Artefaktrepository herunter.](https://repo1.maven.org/maven2/org/apache/jackrabbit/vault/vault-cli/)
   >[!NOTE]
   >
   >Die Quelle des VLT-Tools ist [auf GitHub verfügbar.](https://github.com/apache/jackrabbit-filevault)
1. Entpacken Sie das Archiv.
1. hinzufügen `<archive-dir>/vault-cli-<version>/bin` auf Ihre Umgebung `PATH`, damit die Befehlsdateien `vlt` oder `vlt.bat` entsprechend aufgerufen werden. Beispiel:

   `<aem-installation-dir>/crx-quickstart/opt/helpers/vault-cli-3.1.16/bin>`

1. Öffnen Sie eine BefehlszeilenShell und führen Sie `vlt --help` aus. Stellen Sie sicher, dass die Ausgabe dem folgenden Hilfebildschirm ähnelt:

   ```shell
   vlt --help
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   Jackrabbit FileVault [version 3.1.16] Copyright 2013 by Apache Software Foundation. See LICENSE.txt for more information.
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   Usage:
     vlt [options] <command> [arg1 [arg2 [arg3] ..]]
   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   
   Global options:
   
     -Xjcrlog <arg>           Extended JcrLog options (omit argument for help)
     -Xdavex <arg>            Extended JCR remoting options (omit argument for help)
     --credentials <arg>      The default credentials to use
     --update-credentials     if present the credentials-to-host list is updated in the ~/.vault/auth.xml
     --config <arg>           The JcrFs config to use
     -v (--verbose)           verbose output
     -q (--quiet)             print as little as possible
     --version                print the version information and exit
     --log-level <level>      the log4j log level
     -h (--help) <command>    print this help
   ```

Nachdem Sie es installiert haben, müssen Sie global ignorierte Subversion-Dateien aktualisieren. Bearbeiten Sie Ihre SVN-Einstellungen und fügen Sie Folgendes hinzu:

```xml
[miscellany]
### Set global-ignores to a set of whitespace-delimited globs
### which Subversion will ignore in its 'status' output, and
### while importing or adding files and directories.
global-ignores = .vlt
```

### Konfigurieren des Zeilenendezeichens {#configuring-the-end-of-line-character}

VLT handhabt Zeilenende (End Of Line - EOF) gemäß der folgenden Regeln automatisch:

* Zeilen von Dateien, die unter Windows überprüft wurden, enden auf `CRLF`
* Zeilen mit Dateien, die am Linux/Unix-Ende mit einem `LF` ausgecheckt wurden
* Zeilen von Dateien, die an das Repository übergeben werden, enden auf `LF`

Um sicherzustellen, dass VLT- und SVN-Konfigurationsübereinstimmung vorliegen, sollten Sie die `svn:eol-style`-Eigenschaft für die Erweiterung der im Repository gespeicherten Dateien auf `native` festlegen. Bearbeiten Sie Ihre SVN-Einstellungen und fügen Sie Folgendes hinzu:

```xml
[auto-props]
*.css = svn:eol-style=native
*.cnd = svn:eol-style=native
*.java = svn:eol-style=native
*.js = svn:eol-style=native
*.json = svn:eol-style=native
*.xjson = svn:eol-style=native
*.jsp = svn:eol-style=native
*.txt = svn:eol-style=native
*.html = svn:eol-style=native
*.xml = svn:eol-style=native
*.properties = svn:eol-style=native
```

### Auschecken des Repositorys {#checking-out-the-repository}

Überprüfen Sie das Repository mithilfe des Quellcode-Verwaltungssystems. Im SVN geben Sie beispielsweise Folgendes ein (ersetzen Sie den URI und den Pfad mit Ihrem Repository):

```shell
svn co https://svn.server.com/repos/myproject
```

### Synchronisieren mit dem Repository {#synchronizing-with-the-repository}

Sie müssen filevault mit dem Repository synchronisieren. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie in der Befehlszeile zu `content/jcr_root`.
1. Überprüfen Sie das Repository, indem Sie Folgendes eingeben (ersetzen Sie Ihre Portnummer mit **4502** und Ihre admin-Passwörter):

   ```shell
   vlt --credentials admin:admin co --force http://localhost:4502/crx
   ```

   >[!NOTE]
   >
   >Die Anmeldedaten müssen nur einmal nach dem ersten Auschecken angegeben werden. Sie werden dann in Ihrem Stammverzeichnis unter `.vault/auth.xml` gespeichert.

### Testen, ob die Synchronisierung funktioniert hat {#testing-whether-the-synchronization-worked}

Nachdem Sie das Repository überprüft und synchronisiert haben, sollten Sie testen, ob alles ordnungsgemäß funktioniert. Eine einfache Möglichkeit, dies zu tun, ist eine **.jsp**-Datei zu bearbeiten und zu sehen, ob Ihre Änderungen nach Übermittelung der Änderungen übernommen wurden.

So testen Sie die Synchronisierung:

1. Navigieren Sie zu `.../jcr_content/libs/foundation/components/text`.
1. Bearbeiten Sie etwas in `text.jsp`.
1. Sehen Sie sich die geänderten Dateien an, indem Sie `vlt st` eingeben
1. Sehen Sie sich die Änderungen an, indem Sie `vlt diff text.jsp` eingeben
1. Änderungen übernehmen: `vlt ci test.jsp`.
1. Laden Sie die Seite neu, die eine Textkomponente enthält, und prüfen Sie, ob Ihre Änderungen noch vorhanden sind.

## Hilfe mit dem VLT-Tool {#getting-help-with-the-vlt-tool}

Nach der Installation des VLT-Tools können Sie die Hilfedatei über die Befehlszeile aufrufen:

```shell
vlt --help
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Jackrabbit FileVault [version 3.1.16] Copyright 2013 by Apache Software Foundation. See LICENSE.txt for more information.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Usage:
  vlt [options] <command> [arg1 [arg2 [arg3] ..]]
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Global options:
  -Xjcrlog <arg>           Extended JcrLog options (omit argument for help)
  -Xdavex <arg>            Extended JCR remoting options (omit argument for help)
  --credentials <arg>      The default credentials to use
  --update-credentials     if present the credentials-to-host list is updated in the ~/.vault/auth.xml
  --config <arg>           The JcrFs config to use
  -v (--verbose)           verbose output
  -q (--quiet)             print as little as possible
  --version                print the version information and exit
  --log-level <level>      the log4j log level
  -h (--help) <command>    print this help
Commands:
  export                   Export the Vault filesystem
  import                   Import a Vault filesystem
  checkout (co)            Checkout a Vault file system
  status (st)              Print the status of working copy files and directories.
  update (up)              Bring changes from the repository into the working copy.
  info                     Displays information about a local file.
  commit (ci)              Send changes from your working copy to the repository.
  revert (rev)             Restore pristine working copy file (undo most local edits).
  resolved (res)           Remove 'conflicted' state on working copy files or directories.
  propget (pg)             Print the value of a property on files or directories.
  proplist (pl)            Print the properties on files or directories.
  propset (ps)             Set the value of a property on files or directories.
  add                      Put files and directories under version control.
  delete (del,rm)          Remove files and directories from version control.
  diff (di)                Display the differences between two paths.
  rcp                      Remote copy of repository content.
  sync                     Control vault sync service
  console                  Run an interactive console
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

Um Hilfe für einen bestimmten Befehl zu erhalten, geben Sie den Hilfe-Befehl ein, gefolgt vom Namen des Befehls ein. Beispiel:

```shell
vlt --help export
Usage:
 export -v|-t <arg>|-p <uri> <jcr-path> <local-path>

Description:
  Export the Vault filesystem mounted at <uri> to the local filesystem at <local-path>. An optional <jcr-path> can be specified in order to export just a sub tree.
  Example:
    vlt export http://localhost:4502/crx /apps/geometrixx myproject

Options:
  -v (--verbose)          verbose output
  -t (--type) <arg>       specifies the export type. either 'platform' or 'jar'.
  -p (--prune-missing)    specifies if missing local files should be deleted.
  <uri>                   mountpoint uri
  <jcr-path>              the jcr path
  <local-path>            the local path
```

## Allgemeine in VLT ausgeführte Aufgaben  {#common-tasks-performed-in-vlt}

Die Folgenden finden Sie einige allgemeine Aufgaben, die in VLT ausgeführt werden. Ausführliche Informationen zu den einzelnen Befehlen finden Sie unter den einzelnen [Befehlen](#vlt-commands).

### Auschecken eines Unterbaums {#checking-out-a-subtree}

Wenn Sie beispielsweise nur einen Unterbaum des Repositorys (z. B. `/apps/geometrixx`) auschecken möchten, geben Sie dazu Folgendes ein:

```shell
vlt co http://localhost:4502/crx/-/jcr:root/apps/geometrixx geo
```

Dadurch wird ein neuer Exportstamm `geo` mit einem Ordner `META-INF` und `jcr_root` erstellt und alle Dateien unterhalb von `/apps/geometrixx` in `geo/jcr_root` platziert.

### Durchführen eines gefilterten Checkout {#performing-a-filtered-checkout}

Wenn Sie über einen vorhandenen Arbeitsbereichsfilter verfügen und diesen zum Auschecken verwenden möchten, können Sie entweder zuerst das Verzeichnis `META-INF/vault` erstellen und den Filter dort platzieren oder ihn in der Befehlszeile wie folgt angeben:

```shell
$ vlt co --filter filter.xml http://localhost:4502/crx/-/jcr:root geo
```

Ein Beispielfilter:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/etc/designs/geometrixx" />
    <filter root="/apps/geometrixx"/>
</workspaceFilter>
```

### Verwenden von Import/Export anstelle von .vlt Control {#using-import-export-instead-of-vlt-control}

Sie können Inhalte zwischen einem JCR-Repository und dem lokalen Dateisystem importieren und exportieren, ohne Steuerdateien zu verwenden.

So importieren und exportieren Sie Inhalte ohne Verwendung des Steuerelements `.vlt`

1. Richten Sie zunächst das Repository ein:

   ```shell
   $ cd /projects
   $ svn mkdir https://svn.server.com/repos/myproject
   $ svn co https://svn.server.com/repos/myproject
   $ vlt export -v http://localhost:4502/crx /apps/geometrixx geometrixx
   $ cd geometrixx/
   $ svn add META-INF/ jcr_root/
   $ svn ci
   ```

1. Ändern Sie die Remote-Kopie und aktualisieren Sie JCR:

   ```shell
   $ cd /projects/geometrixx
   $ vlt -v import http://localhost:4502/crx . /
   ```

1. Ändern Sie die Remote-Kopie und aktualisieren Sie den Dateiserver:

   ```shell
   $ cd /projects/geometrixx
   $ vlt export -v http://localhost:4502/crx /apps/geometrixx .
   $ svn st
   M      META-INF/vault/properties.xml
   M      jcr_root/apps/geometrixx/components/contentpage/.content.xml
   $ svn ci
   ```

## Verwenden von VLT {#using-vlt}

Um Befehle in VLT abzusetzen, geben Sie Folgendes in der Befehlszeile ein:

```shell
vlt [options] <command> [arg1 [arg2 [arg3] ..]]  
```

Optionen und Befehle werden im Detail in den folgenden Abschnitten beschrieben.

## Globale VLT-Optionen {#vlt-global-options}

Im Folgenden finden Sie eine Liste mit VLT-Optionen, die für alle Befehle verfügbar sind. Informationen zu weiteren verfügbaren Optionen finden Sie in den einzelnen Befehlen.

|  |  |
|--- |--- |
| Option | Beschreibung |
| `-Xjcrlog <arg>` | Erweiterte JCRlog-Optionen |
| `-Xdavex <arg>` | Erweiterte JCR-Entfernungsoptionen |
| `--credentials <arg>` | Die zu verwendenden Standardberechtigungen |
| `--config <arg>` | Die zu verwendende JcrFs-Konfiguration |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | so wenig wie möglich drucken |
| `--version` | Druckt die Versionsinformationen und verlässt VLT |
| `--log-level <level>` | Gibt die Protokollebene an, z. B. die Protokollebene log4j. |
| `-h (--help) <command>` | Druckt Hilfe für diesen Befehl |

## VLT-Befehle {#vlt-commands}

Die folgende Tabelle beschreibt alle verfügbaren VLT-Befehle. Detaillierte Informationen zu Syntax, verfügbaren Optionen und Beispielen finden Sie in den einzelnen Befehlen.

|  |  |  |
|--- |--- |--- |
| Befehl | Abgekürzter Befehl | Beschreibung |
| `export` |  | Exportiert von einem JCR-Repository (Standarddateisystem) in das lokale Dateisystem ohne Steuerungsdateien. |
| `import` |  | Importiert ein lokales Dateisystem in ein JCR-Repository (Standarddateisystem). |
| `checkout` | `co` | Prüft ein Vault-Dateisystem. Verwenden Sie dies für ein Anfangs-JCR-Repository für das lokale Dateisystem. (Hinweis: Zunächst müssen Sie das Repository in Subversion auschecken.) |
| `analyze` |  | Analysiert Pakete. |
| `status` | `st` | Druckt den Status von Arbeitskopiedateien und Verzeichnissen. |
| `update` | `up` | Importiert Änderungen vom Repository in die Arbeitskopie. |
| `info` |  | Zeigt Informationen über eine lokale Datei an. |
| `commit` | `ci` | Sendet Änderungen von Ihrer Arbeitskopie zum Repository. |
| `revert` | `rev` | Stellt den Originalzustand der Arbeitskopiedatei wieder her und macht die meisten lokalen Änderungen rückgängig. |
| `resolved` | `res` | Entfernt den Status &quot;Konflikt&quot;bei Dateien oder Ordnern mit Arbeitskopien. |
| `propget` | `pg` | Druckt den Wert einer Eigenschaft auf Dateien oder Verzeichnisse. |
| `proplist` | `pl` | Druckt die Eigenschaften von Dateien oder Verzeichnissen. |
| `propset` | `ps` | Legt den Wert einer Eigenschaft in Dateien oder Verzeichnissen fest. |
| `add` |  | Legt Dateien und Ordner unter Versionskontrolle. |
| `delete` | `del` oder `rm` | Entfernt Dateien und Verzeichnisse aus der Versionskontrolle. |
| `diff` | `di` | Zeigt die Unterschiede zwischen zwei Pfaden an. |
| `console` |  | Führt eine interaktive Konsole aus. |
| `rcp` |  | Kopiert einen Knotenbaum von einem Remote-Repository in ein anderes. |
| `sync` |  | Ermöglicht die Steuerung des Vault-Synchronisierungsdiensts. |

### Export {#export}

Exportiert das unter &lt;uri> bereitgestellte Vault-Dateisystem in das lokale Dateisystem unter &lt;local-path>. Ein optionaler &lt;jcr-path> kann angegeben werden, um nur eine Unterstruktur zu exportieren.

#### Syntax {#syntax}

```shell
export -v|-t <arg>|-p <uri> <jcr-path> <local-path>
```

#### Optionen {#options}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-t (--type) <arg>` | gibt den Exporttyp entweder Plattform oder JAR an. |
| `-p (--prune-missing)` | gibt an, ob fehlende lokale Dateien gelöscht werden sollen |
| `<uri>` | Mountpoint uri |
| `<jcrPath>` | JCR-Pfad |
| `<localPath>` | lokaler Pfad |

#### Beispiele {#examples}

```shell
vlt export http://localhost:4502/crx /apps/geometrixx myproject
```

### Import {#import}

Importiert das lokale Dateisystem (beginnend bei `<local-path>` in das Vault-Dateisystem unter `<uri>`. Sie können ein `<jcr-path>` als Importstamm angeben. Wenn `--sync` angegeben ist, werden die importierten Dateien automatisch der Vault-Kontrolle unterworfen.

#### Syntax {#syntax-1}

```shell
import -v|-s <uri> <local-path> <jcr-path>
```

#### Optionen {#options-1}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-s (-- sync)` | legt die lokalen Dateien unter die Standardkontrolle |
| `<uri>` | Mountpoint uri |
| `<jcrPath>` | JCR-Pfad |
| `<localPath>` | lokaler Pfad |

#### Beispiele {#examples-1}

```shell
vlt import http://localhost:4502/crx . /
```

### Auschecken (co) {#checkout-co}

Führt ein erstes Auschecken von einem JCR-Repository zum lokalen Dateisystem durch, beginnend bei &lt;uri> zum lokalen Dateisystem unter &lt;local-path>. Sie können auch ein &lt;jcrPath>-Argument hinzufügen, um ein Unterverzeichnis der Remote-Struktur zu überprüfen. Arbeitsplatzfilter können angegeben werden, die in das META-INF Verzeichnis kopiert werden.

#### Syntax  {#syntax-2}

```shell
checkout --force|-v|-q|-f <file> <uri> <jcrPath> <localPath>  
```

#### Optionen {#options-2}

|  |  |
|--- |--- |
| `--force` | erzwingt das Checkout, lokale Dateien zu überschreiben, wenn sie bereits vorhanden sind |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-f (--filter) <file>` | gibt automatische Filter an, wenn keine definiert ist |
| `<uri>` | Mountpoint uri |
| `<jcrPath>` | (optional) Remote-Pfad |
| `<localPath>` | (optional) lokaler Pfad |

#### Beispiele {#examples-2}

Verwenden von JCR-Remoting:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx/server/crx.default/jcr_root/
```

Mit dem Standardarbeitsbereich:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx/server/-/jcr_root/
```

Wenn der URI unvollständig ist, wird er erweitert:

```shell
vlt --credentials admin:admin co http://localhost:8080/crx
```

### Analysieren {#analyze}

Analysiert Pakete.

#### Syntax {#syntax-3}

```shell
analyze -l <format>|-v|-q <localPaths1> [<localPaths2> ...]
```

#### Optionen {#options-3}

|  |  |
|--- |--- |
| `-l (--linkFormat) <format>` | printf-Format für Hotfix-Links (name,id), z. B. `[CQ520_HF_%s|%s]` |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `<localPaths> [<localPaths> ...]` | lokaler Pfad |

### Status{#status}

Druckt den Status von Arbeitskopiedateien und Verzeichnissen.

Wenn `--show-update` angegeben ist, wird jede Datei mit der Remote-Version verglichen. Der zweite Brief gibt dann an, welche Aktion von einem Aktualisierungsvorgang ausgeführt wird.

#### Syntax {#syntax-4}

```shell
status -v|-q|-u|-N <file1> [<file2> ...]
```

#### Optionen {#options-4}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-u (--show-update)` | zeigt Aktualisierungsinformationen an |
| `-N (--non-recursive)` | auf einem einzelnen Verzeichnis ausgeführt wird |
| `<file> [<file> ...]` | Datei oder Verzeichnis zur Anzeige des Status |

### Aktualisieren {#update}

Kopiert Änderungen aus dem Repository in die Arbeitskopie.

#### Syntax {#syntax-5}

```shell
update -v|-q|--force|-N <file1> [<file2> ...]
```

#### Optionen {#options-5}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt das Überschreiben lokaler Dateien |
| `-N (--non-recursive)` | auf einem einzelnen Verzeichnis ausgeführt wird |
| `<file> [<file> ...]` | zu aktualisierende Datei oder Verzeichnis |

### Info {#info}

Zeigt Informationen über eine lokale Datei an.

#### Syntax  {#syntax-6}

```shell
info -v|-q|-R <file1> [<file2> ...]
```

#### Optionen {#options-6}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | arbeitet rekursiv |
| `<file> [<file> ...]` | Datei oder Verzeichnis, in dem Informationen angezeigt werden |

### Bestätigen {#commit}

Sendet Änderungen von Ihrer Arbeitskopie zum Repository.

#### Syntax  {#syntax-7}

```shell
commit -v|-q|--force|-N <file1> [<file2> ...]
```

#### Optionen {#options-7}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt die Bindung, selbst wenn die Remote-Kopie geändert wird |
| `-N (--non-recursive)` | auf einem einzelnen Verzeichnis ausgeführt wird |
| `<file> [<file> ...]` | -Datei oder -Verzeichnis, die |

### Zurück zur letzten Version {#revert}

Stellt die Arbeitskopiedatei in den Originalzustand zurück und macht die meisten lokalen Änderungen rückgängig.

#### Syntax {#syntax-8}

```shell
revert -q|-R <file1> [<file2> ...]
```

#### Optionen {#options-8}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | absteigend rekursiv |
| `<file> [<file> ...]` | -Datei oder -Verzeichnis, die |

### Gelöst {#resolved}

Entfernt den Status **konfliktbehaftet** in Dateien oder Ordnern von Arbeitskopien.

>[!NOTE]
>
>Dieser Befehl löst Konflikte nicht semantisch auf und entfernt Konfliktmarker nicht. Es entfernt lediglich die Artefakte, die mit Konflikten zusammenhängen, und ermöglicht, dass PATH erneut bestätigt wird.

#### Syntax  {#syntax-9}

```shell
resolved -q|-R|--force <file1> [<file2> ...]  
```

#### Optionen {#options-9}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | absteigend rekursiv |
| `--force` | löst, auch wenn es Konfliktmarkierungen gibt |
| `<file> [<file> ...]` | aufzulösende Datei oder Verzeichnis |

### Propget {#propget}

Druckt den Wert einer Eigenschaft auf Dateien oder Verzeichnisse.

#### Syntax  {#syntax-10}

```shell
propget -q|-R <propname> <file1> [<file2> ...]
```

#### Optionen {#options-10}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | absteigend rekursiv |
| `<propname>` | der Eigenschaftsname |
| `<file> [<file> ...]` | Datei oder Verzeichnis, aus der die Eigenschaft abgerufen werden soll |

### Proplist {#proplist}

Druckt die Eigenschaften von Dateien oder Verzeichnissen.

#### Syntax  {#syntax-11}

```shell
proplist -q|-R <file1> [<file2> ...]
```

#### Optionen {#options-11}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | absteigend rekursiv |
| `<file> [<file> ...]` | Datei oder Verzeichnis zur Liste der Eigenschaften |

### Propset {#propset}

Legt den Wert einer Eigenschaft in Dateien oder Verzeichnissen fest.

>[!NOTE]
>
>VLT erkennt die folgenden Eigenschaften der speziellen Version:
>
>`vlt:mime-type`
>
>Der mime-Typ der Datei. Wird verwendet, um festzustellen, ob die Datei zusammengeführt werden soll. Ein mime-Typ, der mit &#39;text/‘ beginnt (oder ein fehlender mimetype), wird als Text behandelt. Alles andere wird als binär behandelt.

#### Syntax {#syntax-12}

```shell
propset -q|-R <propname> <propval> <file1> [<file2> ...]
```

#### Optionen {#options-12}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | absteigend rekursiv |
| `<propname>` | der Eigenschaftsname |
| `<propval>` | der Eigenschaftswert |
| `<file> [<file> ...]` | Datei oder Verzeichnis, um die Eigenschaft auf |

### Fügen Sie {#add}

Stellt Dateien und Verzeichnisse unter Versionskontrolle und plant sie für das Hinzufügen zum Repository. Sie werden bei der nächsten Bestätigung hinzugefügt.

#### Syntax {#syntax-13}

```shell
add -v|-q|-N|--force <file1> [<file2> ...]
```

#### Optionen {#options-13}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-N (--non-recursive)` | auf einem einzelnen Verzeichnis ausgeführt wird |
| `--force` | erzwingt die Durchführung der Operation |
| `<file> [<file> ...]` | hinzuzufügende lokale Datei oder Verzeichnis |

### Löschen {#delete}

Entfernt Dateien und Verzeichnisse aus der Versionskontrolle.

#### Syntax  {#syntax-14}

```shell
delete -v|-q|--force <file1> [<file2> ...]
```

#### Optionen {#options-14}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt die Durchführung der Operation |
| `<file> [<file> ...]` | zu löschende lokale Datei oder Verzeichnis |

### Differenz {#diff}

Zeigt die Unterschiede zwischen zwei Pfaden an.

#### Syntax  {#syntax-15}

```shell
diff -N <file1> [<file2> ...]
```

#### Optionen {#options-15}

|  |  |
|--- |--- |
| `-N (--non-recursive)` | auf einem einzelnen Verzeichnis ausgeführt wird |
| `<file> [<file> ...]` | Datei oder Verzeichnis, um die Unterschiede von |

### -Konsole{#console}

Führt eine interaktive Konsole aus.

#### Syntax {#syntax-16}

```shell
console -F <file>
```

#### Optionen {#options-16}

|  |  |
|--- |--- |
| `-F (--console-settings) <file>` | gibt die Datei mit den Konsoleneinstellungen an. Die Standarddatei lautet console.properties. |

### Rcp {#rcp}

Kopiert einen Knotenbaum von einem Remote-Repository in ein anderes. `<src>` verweist auf den Quellknoten und  `<dst>` gibt den Zielpfad an, wo der übergeordnete Knoten vorhanden sein muss. Rcp verarbeitet die Knoten durch Streaming der Daten.

#### Syntax {#syntax-17}

```shell
rcp -q|-r|-b <size>|-t <seconds>|-u|-n|-e <arg1> [<arg2> ...] <src> <dst>
```

#### Optionen {#options-17}

|  |  |
|--- |--- |
| `-q (--quiet)` | Druckt so wenig wie möglich. |
| `-r (--recursive)` | Verringert rekursiv. |
| `-b (--batchSize) <size>` | Anzahl der Knoten, die vor einer Zwischenspeicherung verarbeitet werden sollen. |
| `-t (--throttle) <seconds>` | Anzahl der Sekunden, die nach einer Zwischenspeicherung gewartet werden soll. |
| `-u (--update)` | Vorhandene Knoten überschreiben/löschen |
| `-n (--newer)` | Übernehmen Sie lastModified-Eigenschaften für die Aktualisierung. |
| `-e (--exclude) <arg> [<arg> ...]` | Entfernen von ausgeschlossenen Quellpfaden. |
| `<src>` | Die Repository-Adresse des Quellbaums. |
| `<dst>` | Die Repository-Adresse des Zielknotens. |

#### Beispiele {#examples-3}

```shell
vlt rcp http://localhost:4502/crx/-/jcr:root/content  https://admin:admin@localhost:4503/crx/-/jcr:root/content_copy  
```

>[!NOTE]
>
>Auf die Optionen `--exclude` muss eine weitere Option vor den Argumenten `<src>` und `<dst>` folgen. Beispiel:
>
>`vlt rcp -e ".*\.txt" -r`

### Sync {#sync}

Ermöglicht die Steuerung des Vault-Synchronisierungsdiensts. Dieser Befehl versucht ohne Argumente, das aktuelle Arbeitsverzeichnis unter Sync-Kontrolle zu stellen. Wenn es innerhalb des vlt-Auscheckens ausgeführt wird, verwendet es den entsprechenden Filter und den Host, um die Synchronisierung zu konfigurieren. Wenn es außerhalb des vlt-Auscheckens ausgeführt wird, registriert es den aktuellen Ordner nur zur Synchronisierung, wenn das Verzeichnis leer ist.

#### Syntax  {#syntax-18}

```shell
sync -v|--force|-u <uri> <command> <localPath>
```

#### Optionen {#options-18}

|  |  |
|--- |--- |
| `-v (--verbose)` | verbose Ausgabe. |
| `--force` | bestimmte Befehle erzwingen. |
| `-u (--uri) <uri>` | gibt den URI des Synchronisierungshosts an. |
| `<command>` | ausführen. |
| `<localPath>` | zu synchronisierender lokaler Ordner. |

### Statuscodes {#status-codes}

Die Statuscodes, die durch VLT verwendet werden, sind:

* „ “ Keine Änderungen
* „A“ hinzugefügt
* „C“ steht in Konflikt
* „D“ gelöscht
* „I“ ignoriert
* „M“ geändert
* „R“ ersetzt
* „?“ Element steht nicht unter Versionskontrolle
* „!“ Das Element fehlt (wird mit dem Befehl non-svn entfernt) oder ist unvollständig
* „~“ versioniertes Element, das durch ein Element anderer Art behindert wird

## Einrichten der FileVault-Synchronisierung {#setting-up-filevault-sync}

Der Vault-Synchronisierungsdienst wird zum Synchronisieren des Repository-Inhalts mit einer lokalen Dateisystemdarstellung und umgekehrt verwendet. Dies wird durch die Installation eines OSGi-Dienstes erreicht, der auf Änderungen des Repositorys wartet und den Inhalt des Dateisystems regelmäßig überprüft. Es verwendet dasselbe Serialisierungsformat wie Vault zum Zuordnen des Repository-Inhalts zur Festplatte.

>[!NOTE]
>
>Der Vault-Synchronisierungsdienst ist ein Entwicklungstool und es wird dringend davon abgeraten, ihn in einem produktiven System zu verwenden. Beachten Sie außerdem, dass der Service nur mit dem lokalen Dateisystem synchronisiert und nicht für die Remote-Entwicklung verwendet werden kann.

### Installieren des Diensts mit vlt  {#installing-the-service-using-vlt}

Der Befehl `vlt sync install` kann verwendet werden, um das Paket und die Konfiguration des Vault-Synchronisierungsdienstes automatisch zu installieren.

Das Bundle wird unter `/libs/crx/vault/install` installiert und der config-Knoten wird unter `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl` erstellt. Zunächst wird der Dienst aktiviert, aber es werden keine Synchronisierungsstämme konfiguriert.

Im folgenden Beispiel wird der Synchronisierungsdienst für die CRX-Instanz installiert, auf die vom angegebenen URI zugegriffen werden kann.

```shell
$ vlt --credentials admin:admin sync --uri http://localhost:4502/crx install
```

### Anzeigen des Dienststatus  {#displaying-the-service-status}

Der Befehl `status` kann verwendet werden, um Informationen über den aktuellen Synchronisierungsdienst anzuzeigen. ``

```shell
$ vlt sync status --uri http://localhost:4502/crx
Connecting via JCR remoting to http://localhost:4502/crx/server
Listing sync status for http://localhost:4502/crx/server/-/jcr:root
- Sync service is enabled.
- No sync directories configured.
```

>[!NOTE]
>
>Der Befehl `status` ruft keine Live-Daten vom Dienst ab, sondern liest die Konfiguration bei `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl`.

### Hinzufügen eines Synchronisierungsordners {#adding-a-sync-folder}

Der Befehl `register` wird verwendet, um einen Ordner zur Synchronisierung mit der Konfiguration hinzuzufügen.

```shell
$ vlt sync register
Connecting via JCR remoting to http://localhost:4502/crx/server
Added new sync directory: /tmp/workspace/vltsync/jcr_root
```

>[!NOTE]
>
>Der Befehl `register` löst erst dann eine Synchronisierung aus, wenn Sie die Konfiguration `sync-once` konfiguriert haben.

### Entfernen eines Synchronisierungsordners {#removing-a-sync-folder}

Der Befehl `unregister` wird verwendet, um einen zu synchronisierenden Ordner aus der Konfiguration zu entfernen.

```shell
$  vlt sync unregister
Connecting via JCR remoting to http://localhost:4502/crx/server
Removed sync directory: /tmp/workspace/vltsync/jcr_root
```

>[!NOTE]
>
>Sie müssen die Registrierung eines Synchronisierungsordners aufheben, bevor Sie den Ordner selbst löschen.

### Konfigurieren der Synchronisierung {#configuring-synchronization}

#### Servicekonfiguration {#service-configuration}

Nachdem der Dienst ausgeführt wird, kann sie mit den folgenden Parametern konfiguriert werden:

* `vault.sync.syncroots`: Einer oder mehrere lokale Dateisystempfade, die die Synchronisierungsstämme definieren.

* `vault.sync.fscheckinterval`: Häufigkeit (in Sekunden), mit der das Dateisystem auf Änderungen überprüft werden soll. Standard ist 5 Sekunden.
* `vault.sync.enabled`: Allgemeine Markierung, die den Dienst aktiviert/deaktiviert.

>[!NOTE]
>
>Der Dienst kann mit der Web-Konsole oder einem `sling:OsgiConfig`-Knoten (mit dem Namen `com.day.jcr.sync.impl.VaultSyncServiceImpl`) im Repository konfiguriert werden.
>
>In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

#### Synchronisierungsordnerkonfiguration  {#sync-folder-configuration}

Jeder Synchronisierungsordner speichert Konfiguration und Status in drei Dateien:

* `.vlt-sync-config.properties`: Konfigurationsdatei.

* `.vlt-sync.log`: Protokolldatei, die Informationen über die Vorgänge enthält, die beim Synchronisieren durchgeführt werden.
* `.vlt-sync-filter.xml`: Filter, die definieren, welche Teile des Repositorys synchronisiert werden. Das Format dieser Datei wird im Abschnitt [Durchführen eines gefilterten Kassengangs](#performing-a-filtered-checkout) beschrieben.

Mit der Datei `.vlt-sync-config.properties` können Sie die folgenden Eigenschaften konfigurieren:

**** disabledAktiviert oder deaktiviert die Synchronisierung. Standardmäßig ist dieser Parameter auf false gesetzt, um die Synchronisierung zu ermöglichen.

**sync-** onceWenn nicht leer die nächste Überprüfung wird den Ordner in der angegebenen Richtung synchronisieren, dann wird der Parameter gelöscht. Zwei Werte werden unterstützt:

* `JCR2FS`: exportiert alle Inhalte im JCR-Repository und schreibt auf die lokale Festplatte.
* `FS2JCR`: Importiert den gesamten Inhalt von der Festplatte in das JCR-Repository.

**sync-** logDefiniert den Protokolldateinamen. Standardmäßig ist der Wert .vlt-sync.log

### Verwenden der VLT-Synchronisierung für die Entwicklung {#using-vlt-sync-for-development}

Um eine Entwicklungsumgebung auf Basis eines Synchronisierungsordners einzurichten, gehen Sie wie folgt vor:

1. Checken Sie Ihr Repository mit der vlt-Befehlszeile aus:

   ```shell
   $ vlt --credentials admin:admin co --force http://localhost:4502/crx dev
   ```

   >[!NOTE]
   >
   >Sie können Filter verwenden, um nur die entsprechenden Pfade auszuchecken. Informationen finden Sie im Abschnitt [Durchführen eines gefilterten Auscheckens](#performing-a-filtered-checkout).

1. Gehen Sie zum Stammordner Ihrer Arbeitskopie:

   ```shell
   $ cd dev/jcr_root/
   ```

1. Installieren Sie den Synchronisierungsservice auf Ihrem Repository:

   ```xml
   $ vlt sync install
   Connecting via JCR remoting to http://localhost:4502/crx/server
   Preparing to install vault-sync-2.4.24.jar...
   Updated bundle: vault-sync-2.4.24.jar
   Created new config at /libs/crx/vault/config/com.day.jcr.sync.impl.VaultSyncServiceImpl
   ```

1. Initialisieren Sie den Synchronisierungsservice:

   ```shell
   $ vlt sync
   Connecting via JCR remoting to http://localhost:4502/crx/server
   Starting initialization of sync service in existing vlt checkout /Users/colligno/Applications/cq5/vltsync/sandbox/dev/jcr_root for http://localhost:4502/crx/server/-/jcr:root
   Added new sync directory: /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root
   
   The directory /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root is now enabled for syncing.
   You might perform a 'sync-once' by setting the
   appropriate flag in the /Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/.vlt-sync-config.properties file.
   ```

1. Bearbeiten Sie die ausgeblendete Datei `.vlt-sync-config.properties` und konfigurieren Sie die Synchronisierung, um den Inhalt Ihres Repositorys zu synchronisieren:

   ```xml
   sync-once=JCR2FS
   ```

   >[!NOTE]
   >
   >Dieser Schritt lädt das gesamte Repository gemäß Ihrer Filterkonfiguration herunter.

1. Überprüfen Sie die Protokolldatei `.vlt-sync.log`, um den Fortschritt anzuzeigen:

   ```xml
   ***
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/GeoProduct.java
   ***
   ```

Ihr lokaler Ordner ist jetzt mit dem Repository synchronisiert. Die Synchronisierung erfolgt bidirektional, sodass Änderungen aus dem Repository auf Ihren lokalen Synchronisierungsordner und umgekehrt angewendet werden.

>[!NOTE]
>
>Die VLT -Synchronisierungsfunktion unterstützt nur einfache Dateien und Ordner, erkennt jedoch spezielle serialisierte Vault-Dateien (.content.xml, dialog.xml usw.) und ignoriert sie im Hintergrund. So ist es möglich, die Vault-Synchronisierung bei einem Standard-vlt-Auschecken zu verwenden.
