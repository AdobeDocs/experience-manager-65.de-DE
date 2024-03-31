---
title: Vewenden des VLT-Tools
description: Das Jackrabbit FileVault Tool (VLT) wurde von The Apache Foundation entwickelt und ordnet den Inhalt einer Jackrabbit/AEM-Instanz Ihrem Dateisystem zu
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: efbba312-9fc8-4670-b8f1-d2a86162d075
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2687'
ht-degree: 100%

---

# Vewenden des VLT-Tools {#how-to-use-the-vlt-tool}

Das Jackrabbit FileVault Tool (VLT) ist ein von [The Apache Foundation](https://www.apache.org/) entwickeltes Tool, das den Inhalt einer Jackrabbit/AEM-Instanz Ihrem Dateisystem zuordnet. Das VLT-Tool hat ähnliche Funktionen wie der Quellkontrollsystem-Client (z. B. ein Subversion (SVN)-Client) und bietet normale Eincheck-, Auscheck- und Verwaltungsvorgänge sowie Konfigurationsoptionen für die flexible Darstellung des Projektinhalts.

Sie führen das VLT-Tool über die Befehlszeile aus. In diesem Dokument wird beschrieben, wie Sie das Tool verwenden, einschließlich der ersten Schritte und der Hilfe sowie einer Liste aller [Befehle](#vlt-commands) und verfügbaren [Optionen](#vlt-global-options).

## Konzepte und Architektur {#concepts-and-architecture}

Einen umfassenden Überblick über die Konzepte und die Struktur des Filevault-Tools finden Sie auf der Seite [Überblick über Filevault](https://jackrabbit.apache.org/filevault/overview.html) and [Vault FS](https://jackrabbit.apache.org/filevault/vaultfs.html) der offiziellen [Apache Jackrabbit Filevault-Dokumentation](https://jackrabbit.apache.org/filevault/index.html).

## Erste Schritte mit dem VLT {#getting-started-with-vlt}

Um das VLT verwenden zu können, müssen Sie folgende Schritte ausführen:

1. Installieren Sie das VLT, aktualisieren Sie die Umgebungsvariablen und aktualisieren Sie die global ignorierten Subversion-Dateien.
1. Richten Sie das AEM-Repository ein (falls Sie dies nicht bereits getan haben).
1. Checken Sie das AEM-Repository aus.
1. Synchronisieren Sie mit dem Repository.
1. Testen Sie, ob die Synchronisierung funktioniert hat.

### Installieren des VLT-Tools {#installing-the-vlt-tool}

Um das VLT-Tool zu verwenden, müssen Sie zunächst das Programm installieren. Es ist nicht standardmäßig installiert, da es sich um ein zusätzliches Tool handelt. Außerdem müssen Sie die Umgebungsvariable Ihres Systems festlegen.

1. Laden Sie die FileVault-Archivdatei aus dem [Maven-Artefakt-Repository](https://repo1.maven.org/maven2/org/apache/jackrabbit/vault/vault-cli/).
   >[!NOTE]
   >
   >Die Quelle des VLT-Tools ist [auf GitHub verfügbar](https://github.com/apache/jackrabbit-filevault).
1. Entpacken Sie das Archiv.
1. Fügen Sie `<archive-dir>/vault-cli-<version>/bin` in Ihrer Umgebung `PATH` hinzu, sodass die Befehlsdateien `vlt` oder `vlt.bat` entsprechend aufgerufen werden können. Beispiel:

   `<aem-installation-dir>/crx-quickstart/opt/helpers/vault-cli-3.1.16/bin>`

1. Öffnen Sie eine Befehlszeilen-Shell und führen Sie `vlt --help` aus. Stellen Sie sicher, dass die Ausgabe dem folgenden Hilfebildschirm ähnelt:

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
* Zeilen von Dateien, die unter Linux/Unix überprüft wurden, enden auf `LF`
* Zeilen von Dateien, die an das Repository übergeben werden, enden auf `LF`

Um zu gewährleisten, dass VLT- und SVN-Konfiguration übereinstimmen, sollten Sie die Eigenschaft `svn:eol-style` für die Erweiterung der im Repository gespeicherten Dateien auf `native` festlegen. Bearbeiten Sie Ihre SVN-Einstellungen und fügen Sie Folgendes hinzu:

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

### Überprüfen des Repositorys {#checking-out-the-repository}

Überprüfen Sie das Repository mithilfe des Quell-Code-Verwaltungssystems. Im SVN geben Sie beispielsweise Folgendes ein (ersetzen Sie den URI und den Pfad mit Ihrem Repository):

```shell
svn co https://svn.server.com/repos/myproject
```

### Synchronisieren mit dem Repository {#synchronizing-with-the-repository}

Sie müssen filevault mit dem Repository synchronisieren. Gehen Sie hierfür wie folgt vor:

1. Klicken Sie in der Befehlszeile `content/jcr_root`.
1. Überprüfen Sie das Repository, indem Sie Folgendes eingeben (ersetzen Sie Ihre Port-Nummer durch **4502** und Ihre Admin-Kennwörter):

   ```shell
   vlt --credentials admin:admin co --force http://localhost:4502/crx
   ```

   >[!NOTE]
   >
   >Die Anmeldedaten müssen nur einmal nach dem ersten Auschecken angegeben werden. Sie werden dann im Hauptverzeichnis in `.vault/auth.xml` gespeichert.

### Es wird geprüft, ob die Synchronisierung funktioniert hat {#testing-whether-the-synchronization-worked}

Nachdem Sie das Repository überprüft und synchronisiert haben, sollten Sie testen, ob alles ordnungsgemäß funktioniert. Eine einfache Möglichkeit, dies zu tun, ist eine **.jsp**-Datei zu bearbeiten und zu sehen, ob Ihre Änderungen nach Übermittlung der Änderungen übergeben wurden.

So testen Sie die Synchronisierung:

1. Navigieren Sie zu `.../jcr_content/libs/foundation/components/text`.
1. Bearbeiten Sie etwas in `text.jsp`.
1. Sehen Sie die geänderten Dateien, indem Sie `vlt st` eingeben
1. Zeigen Sie die Änderungen an, indem Sie `vlt diff text.jsp` eingeben
1. Übergeben Sie die Änderungen: `vlt ci test.jsp`.
1. Laden Sie die Seite neu, die eine Textkomponente enthält, und prüfen Sie, ob Ihre Änderungen noch vorhanden sind.

## Hilfe mit dem VLT {#getting-help-with-the-vlt-tool}

Wenn Sie das VLT installiert haben, können Sie die Hilfedatei über die Befehlszeile aufrufen:

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
  Export the Vault filesystem mounted at <uri> to the local filesystem at <local-path>. An optional <jcr-path> can be specified to export just a sub tree.
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

## Allgemeine im VLT ausgeführte Aufgaben {#common-tasks-performed-in-vlt}

Die Folgenden finden Sie einige allgemeine Aufgaben, die in VLT ausgeführt werden. Ausführliche Informationen zu den einzelnen Befehlen finden Sie unter den einzelnen [Befehlen](#vlt-commands).

### Überprüfen einer Unterstruktur {#checking-out-a-subtree}

Wenn Sie nur eine Unterstruktur des Repositorys überprüfen möchten, wie z. B. `/apps/geometrixx`, können Sie dies tun, indem Sie Folgendes eingeben:

```shell
vlt co http://localhost:4502/crx/-/jcr:root/apps/geometrixx geo
```

Dadurch wird ein neuer Exportstamm `geo` mit einem `META-INF`- und `jcr_root`-Verzeichnis erstellt und alle Dateien werden unter `/apps/geometrixx` in `geo/jcr_root` abgelegt.

### Durchführen eines gefilterten Auscheckens {#performing-a-filtered-checkout}

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

### Mit der Import/Exportfunktion statt .vlt-Steuerung {#using-import-export-instead-of-vlt-control}

Sie können Inhalte zwischen einem JCR-Repository und dem lokalen Dateisystem importieren und exportieren, ohne Steuerdateien zu verwenden.

So importieren bzw. exportieren Sie Inhalt ohne die Verwendung der `.vlt`-Steuerung:

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
| `-Xjcrlog <arg>` | Erweiterte JcrLog-Optionen |
| `-Xdavex <arg>` | Erweiterte JCR-Fernsteuerungsoptionen |
| `--credentials <arg>` | Die zu verwendenden Standardanmeldedaten |
| `--config <arg>` | Die zu verwendende JcrFs-Konfiguration |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--version` | Druckt die Versionsinformationen und beendet VLT |
| `--log-level <level>` | Gibt die Protokollebene an, z. B. die Protokollebene log4j. |
| `-h (--help) <command>` | Druckt Hilfe für diesen bestimmten Befehl |

## VLT-Befehle {#vlt-commands}

Die folgende Tabelle beschreibt alle verfügbaren VLT-Befehle. Detaillierte Informationen zu Syntax sowie verfügbaren Optionen und Beispielen finden Sie in den einzelnen Befehlen.

|  |  |  |
|--- |--- |--- |
| Befehl | Abgekürzter Befehl | Beschreibung |
| `export` |  | Exportiert aus einem JCR-Repository (Vault-Dateisystem) in das lokale Dateisystem ohne Kontrolldateien. |
| `import` |  | Importiert ein lokales Dateisystem in ein JCR-Repository (Vault-Dateisystem). |
| `checkout` | `co` | Checkt ein Vault-Dateisystem aus. Verwenden Sie dies für ein Anfangs-JCR-Repository für das lokale Dateisystem. (Hinweis: Sie müssen zuerst das Repository in der Unterversion überprüfen.) |
| `analyze` |  | Analysiert Pakete. |
| `status` | `st` | Druckt den Status von Arbeitskopiedateien und Verzeichnissen. |
| `update` | `up` | Importiert Änderungen aus dem Repository in die Arbeitskopie. |
| `info` |  | Zeigt Informationen über eine lokale Datei an. |
| `commit` | `ci` | Sendet Änderungen von Ihrer Arbeitskopie zum Repository. |
| `revert` | `rev` | Stellt die Arbeitskopie-Datei in ihren ursprünglichen Zustand zurück und macht die meisten lokalen Änderungen rückgängig. |
| `resolved` | `res` | Entfernt den Konfliktstatus in Arbeitskopie-Dateien oder Verzeichnissen. |
| `propget` | `pg` | Druckt den Wert einer Eigenschaft auf Dateien oder Verzeichnisse. |
| `proplist` | `pl` | Druckt die Eigenschaften von Dateien oder Verzeichnissen. |
| `propset` | `ps` | Legt den Wert einer Eigenschaft in Dateien oder Verzeichnissen fest. |
| `add` |  | Stellt Dateien und Ordner unter Versionskontrolle. |
| `delete` | `del` oder `rm` | Entfernt Dateien und Verzeichnisse aus der Versionskontrolle. |
| `diff` | `di` | Zeigt die Unterschiede zwischen zwei Pfaden an. |
| `console` |  | Führt eine interaktive Konsole aus. |
| `rcp` |  | Kopiert einen Knotenbaum von einem Remote-Repository in ein anderes. |
| `sync` |  | Ermöglicht die Steuerung des Vault-Synchronisierungsdienstes. |

### Export {#export}

Exportiert das unter &lt;uri> bereitgestellte Vault-Dateisystem in das lokale Dateisystem unter &lt;local-path>. Ein optionaler &lt;jcr-path> kann angegeben werden, um nur eine Unterstruktur zu exportieren.

#### Syntax {#syntax}

```shell
export -v|-t <arg>|-p <uri> <jcr-path> <local-path>
```

#### Optionen {#options}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-t (--type) <arg>` | gibt den Exporttyp an, entweder Plattform oder JAR. |
| `-p (--prune-missing)` | gibt an, ob fehlende lokale Dateien gelöscht werden sollen |
| `<uri>` | Bereitstellungspunkt-URI |
| `<jcrPath>` | JCR-Pfad |
| `<localPath>` | lokaler Pfad |

#### Beispiele {#examples}

```shell
vlt export http://localhost:4502/crx /apps/geometrixx myproject
```

### Importieren {#import}

Importiert das lokale Dateisystem (beginnend bei `<local-path>`) in das Vault Dateisystem unter `<uri>`. Sie können einen `<jcr-path>` als Importstamm angeben. Wenn `--sync` angegeben wird, werden die importierten Dateien automatisch unter Vault-Kontrolle gestellt.

#### Syntax {#syntax-1}

```shell
import -v|-s <uri> <local-path> <jcr-path>
```

#### Optionen {#options-1}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-s (-- sync)` | Stellt die lokalen Dateien unter Vault-Kontrolle |
| `<uri>` | Bereitstellungspunkt-URI |
| `<jcrPath>` | JCR-Pfad |
| `<localPath>` | lokaler Pfad |

#### Beispiele {#examples-1}

```shell
vlt import http://localhost:4502/crx . /
```

### Auschecken (co) {#checkout-co}

Führt ein erstes Auschecken von einem JCR-Repository zum lokalen Dateisystem durch, beginnend bei &lt;uri> zum lokalen Dateisystem unter &lt;local-path>. Sie können auch ein &lt;jcrPath>-Argument hinzufügen, um ein Unterverzeichnis der Remote-Struktur zu überprüfen. Es können Arbeitsplatzfilter angegeben werden, die in das Verzeichnis META-INF kopiert werden.

#### Syntax {#syntax-2}

```shell
checkout --force|-v|-q|-f <file> <uri> <jcrPath> <localPath>  
```

#### Optionen {#options-2}

|  |  |
|--- |--- |
| `--force` | erzwingt, dass beim Auschecken lokale Dateien überschrieben werden, sofern sie bereits vorhanden sind |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-f (--filter) <file>` | gibt automatische Filter an, wenn keine definiert ist |
| `<uri>` | Bereitstellungspunkt-URI |
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
| `-l (--linkFormat) <format>` | printf-Format für Hotfix-Links (name,id), z. B. `[CQ520_HF_%s|%s]` |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `<localPaths> [<localPaths> ...]` | lokaler Pfad |

### Status {#status}

Druckt den Status von Arbeitskopiedateien und Verzeichnissen.

Wenn `--show-update` angegeben ist, wird jede Datei gegen die Remote-Version geprüft. Der zweite Buchstabe gibt dann an, welche Aktion von einer Aktualisierungsoperation ausgeführt würde.

#### Syntax {#syntax-4}

```shell
status -v|-q|-u|-N <file1> [<file2> ...]
```

#### Optionen {#options-4}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-u (--show-update)` | zeigt Aktualisierungsinformationen an |
| `-N (--non-recursive)` | wird nur in einem Verzeichnis ausgeführt |
| `<file> [<file> ...]` | Datei oder Verzeichnis zur Statusanzeige |

### Aktualisieren {#update}

Kopiert Änderungen aus dem Repository in die Arbeitskopie.

#### Syntax {#syntax-5}

```shell
update -v|-q|--force|-N <file1> [<file2> ...]
```

#### Optionen {#options-5}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt das Überschreiben lokaler Dateien |
| `-N (--non-recursive)` | wird nur in einem Verzeichnis ausgeführt |
| `<file> [<file> ...]` | zu aktualisierende Datei oder Verzeichnis |

### Info {#info}

Zeigt Informationen über eine lokale Datei an.

#### Syntax {#syntax-6}

```shell
info -v|-q|-R <file1> [<file2> ...]
```

#### Optionen {#options-6}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | wird rekursiv ausgeführt |
| `<file> [<file> ...]` | Datei oder Verzeichnis, für die/das Informationen angezeigt werden sollen |

### Commit {#commit}

Sendet Änderungen von Ihrer Arbeitskopie zum Repository.

#### Syntax {#syntax-7}

```shell
commit -v|-q|--force|-N <file1> [<file2> ...]
```

#### Optionen {#options-7}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt die Übergabe, auch wenn die Remote-Kopie geändert wird |
| `-N (--non-recursive)` | wird nur in einem Verzeichnis ausgeführt |
| `<file> [<file> ...]` | zu übergebende Datei oder Verzeichnis |

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
| `-R (--recursive)` | rekursiv absteigend |
| `<file> [<file> ...]` | zu übergebende Datei oder Verzeichnis |

### Gelöst {#resolved}

Entfernt den **Konfliktstatus** in Arbeitskopie-Dateien oder Verzeichnissen.

>[!NOTE]
>
>Mit diesem Befehl werden Konflikte nicht semantisch gelöst oder Konfliktmarken entfernt. Es werden lediglich die konfliktbezogenen Artefaktdateien entfernt, sodass PATH erneut übertragen werden kann.

#### Syntax {#syntax-9}

```shell
resolved -q|-R|--force <file1> [<file2> ...]  
```

#### Optionen {#options-9}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | rekursiv absteigend |
| `--force` | löst auf, auch wenn Konfliktmarkierungen vorhanden sind |
| `<file> [<file> ...]` | Datei oder Verzeichnis, die/das aufgelöst werden soll |

### Propget {#propget}

Druckt den Wert einer Eigenschaft von Dateien oder Verzeichnissen.

#### Syntax {#syntax-10}

```shell
propget -q|-R <propname> <file1> [<file2> ...]
```

#### Optionen {#options-10}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | rekursiv absteigend |
| `<propname>` | der Eigenschaftsname |
| `<file> [<file> ...]` | Datei oder Verzeichnis, aus der/dem die Eigenschaft abgerufen werden soll |

### Proplist {#proplist}

Druckt die Eigenschaften von Dateien oder Verzeichnissen.

#### Syntax {#syntax-11}

```shell
proplist -q|-R <file1> [<file2> ...]
```

#### Optionen {#options-11}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | rekursiv absteigend |
| `<file> [<file> ...]` | Datei oder Verzeichnis, aus der/dem die Eigenschaften aufgelistet werden sollen |

### Propset {#propset}

Legt den Wert einer Eigenschaft in Dateien oder Verzeichnissen fest.

>[!NOTE]
>
>VLT erkennt die folgenden speziellen versionierten Eigenschaften:
>
>`vlt:mime-type`
>
>Der mime-Typ der Datei. Wird verwendet, um festzustellen, ob die Datei zusammengeführt werden soll. Ein MIME-Typ, der mit „text/“ beginnt (oder ein fehlender MIME-Typ), wird als Text behandelt. Alles andere wird als binär behandelt.

#### Syntax {#syntax-12}

```shell
propset -q|-R <propname> <propval> <file1> [<file2> ...]
```

#### Optionen {#options-12}

|  |  |
|--- |--- |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-R (--recursive)` | rekursiv absteigend |
| `<propname>` | der Eigenschaftsname |
| `<propval>` | der Eigenschaftswert |
| `<file> [<file> ...]` | Datei oder Verzeichnis, auf das die Eigenschaft festgelegt werden soll |

### Hinzufügen {#add}

Stellt Dateien und Verzeichnisse unter Versionskontrolle und plant sie für das Hinzufügen zum Repository. Sie werden bei der nächsten Bestätigung hinzugefügt.

#### Syntax {#syntax-13}

```shell
add -v|-q|-N|--force <file1> [<file2> ...]
```

#### Optionen {#options-13}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `-N (--non-recursive)` | wird nur in einem Verzeichnis ausgeführt |
| `--force` | erzwingt die Ausführung des Vorgangs |
| `<file> [<file> ...]` | lokale Datei oder Verzeichnis, die/das hinzugefügt werden soll |

### Löschen {#delete}

Entfernt Dateien und Verzeichnisse aus der Versionskontrolle.

#### Syntax {#syntax-14}

```shell
delete -v|-q|--force <file1> [<file2> ...]
```

#### Optionen {#options-14}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe |
| `-q (--quiet)` | druckt so wenig wie möglich |
| `--force` | erzwingt die Ausführung des Vorgangs |
| `<file> [<file> ...]` | zu löschende lokale Datei oder Verzeichnis |

### Diff {#diff}

Zeigt die Unterschiede zwischen zwei Pfaden an.

#### Syntax {#syntax-15}

```shell
diff -N <file1> [<file2> ...]
```

#### Optionen {#options-15}

|  |  |
|--- |--- |
| `-N (--non-recursive)` | wird nur in einem Verzeichnis ausgeführt |
| `<file> [<file> ...]` | Datei oder Verzeichnis, deren Unterschiede angezeigt werden sollen |

### Konsole {#console}

Führt eine interaktive Konsole aus.

#### Syntax {#syntax-16}

```shell
console -F <file>
```

#### Optionen {#options-16}

|  |  |
|--- |--- |
| `-F (--console-settings) <file>` | gibt die Datei mit den Konsoleneinstellungen an. Die Standarddatei ist console.properties. |

### Rcp {#rcp}

Kopiert einen Knotenbaum von einem Remote-Repository in ein anderes. `<src>` zeigt auf den Quellknoten und `<dst>` gibt den Zielpfad an, in dem der übergeordnete Knoten vorhanden sein muss. Rcp verarbeitet die Knoten durch Streaming der Daten.

#### Syntax {#syntax-17}

```shell
rcp -q|-r|-b <size>|-t <seconds>|-u|-n|-e <arg1> [<arg2> ...] <src> <dst>
```

#### Optionen {#options-17}

|  |  |
|--- |--- |
| `-q (--quiet)` | Druckt so wenig wie möglich. |
| `-r (--recursive)` | Rekursiv absteigend. |
| `-b (--batchSize) <size>` | Anzahl der Knoten, die vor einer Zwischenspeicherung verarbeitet werden sollen. |
| `-t (--throttle) <seconds>` | Anzahl der Sekunden, die nach einer Zwischenspeicherung gewartet werden soll. |
| `-u (--update)` | Überschreiben/Löschen vorhandener Knoten. |
| `-n (--newer)` | Beachten von lastModified-Eigenschaften zur Aktualisierung. |
| `-e (--exclude) <arg> [<arg> ...]` | Reguläre Ausdrücke ausgeschlossener Quellpfade. |
| `<src>` | Die Repository-Adresse des Quellbaums. |
| `<dst>` | Die Repository-Adresse des Zielknotens. |

#### Beispiele {#examples-3}

```shell
vlt rcp http://localhost:4502/crx/-/jcr:root/content  https://admin:admin@localhost:4503/crx/-/jcr:root/content_copy  
```

>[!NOTE]
>
>Vor den `<src>`- und `<dst>`-Argumenten muss auf die`--exclude`-Optionen eine andere Option folgen. Beispiel:
>
>`vlt rcp -e ".*\.txt" -r`

### Sync {#sync}

Ermöglicht die Steuerung des Vault-Synchronisierungsdienstes. Dieser Befehl versucht ohne Argumente, das aktuelle Arbeitsverzeichnis unter Sync-Kontrolle zu stellen. Wenn er innerhalb des vlt-Checkouts ausgeführt wird, verwendet er den entsprechenden Filter und den Host, um die Synchronisierung zu konfigurieren. Bei einer Ausführung außerhalb eines vlt-Checkouts wird der aktuelle Ordner nur dann zur Synchronisierung registriert, wenn das Verzeichnis leer ist.

#### Syntax {#syntax-18}

```shell
sync -v|--force|-u <uri> <command> <localPath>
```

#### Optionen {#options-18}

|  |  |
|--- |--- |
| `-v (--verbose)` | ausführliche Ausgabe. |
| `--force` | erzwingt die Ausführung bestimmter Befehle. |
| `-u (--uri) <uri>` | gibt den URI des Synchronisierungs-Hosts an. |
| `<command>` | auszuführender Synchronisierungsbefehl. |
| `<localPath>` | lokaler Ordner, der synchronisiert werden soll. |

### Status-Codes {#status-codes}

Die Status-Codes, die durch VLT verwendet werden, sind:

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

## Einrichten von FileVault-Synchronisierung {#setting-up-filevault-sync}

Der Vault-Synchronisierungsdienst wird zum Synchronisieren des Repository-Inhalts mit einer lokalen Dateisystemdarstellung verwendet, und umgekehrt. Dies wird durch die Installation eines OSGi-Dienstes erreicht, der auf Änderungen des Repositorys wartet und den Inhalt des Dateisystems regelmäßig überprüft. Es verwendet dasselbe Serialisierungsformat wie Vault zum Zuordnen des Repository-Inhalts zur Festplatte.

>[!NOTE]
>
>Der Vault-Synchronisierungsdienst ist ein Entwicklungstool und es wird dringend davon abgeraten, ihn in einem produktiven System zu verwenden. Der Dienst kann außerdem nur mit dem lokalen Dateisystem synchronisiert und nicht für die Remote-Entwicklung verwendet werden.

### Dienstinstallation mit dem VLT {#installing-the-service-using-vlt}

Der Befehl `vlt sync install` kann verwendet werden, um das Paket und die Konfiguration des Vault-Synchronisierungsdienstes automatisch zu installieren.

Das Bundle wird unter `/libs/crx/vault/install` installiert und der config-Knoten wird unter `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl` erstellt. Zunächst ist der Dienst aktiviert, aber es werden keine Synchronisierungsstämme konfiguriert.

Im folgenden Beispiel wird der Synchronisierungsdienst mit der CRX-Instanz installiert, auf die der angegebene URI zugreifen kann.

```shell
$ vlt --credentials admin:admin sync --uri http://localhost:4502/crx install
```

### Anzeigen des Dienststatus {#displaying-the-service-status}

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
>Der Befehl `status` ruft keine Live-Daten vom Dienst ab, sondern liest die Konfiguration unter `/libs/crx/vault/com.day.jcr.sync.impl.VaultSyncServiceImpl`.

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

#### Dienstkonfiguration {#service-configuration}

Sobald der Dienst ausgeführt wird, kann er mit folgenden Parametern konfiguriert werden:

* `vault.sync.syncroots`: Einer oder mehrere lokale Dateisystempfade, die die Synchronisierungsstämme definieren.

* `vault.sync.fscheckinterval`: Häufigkeit (in Sekunden), mit der das Dateisystem auf Änderungen überprüft werden soll. Standard ist 5 Sekunden.
* `vault.sync.enabled`: Allgemeine Markierung, die den Dienst aktiviert/deaktiviert.

>[!NOTE]
>
>Der Dienst kann mit der Web-Konsole oder einem `sling:OsgiConfig`-Knoten (mit dem Namen `com.day.jcr.sync.impl.VaultSyncServiceImpl`) im Repository konfiguriert werden.
>
>In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

#### Synchronisierungsordnerkonfiguration {#sync-folder-configuration}

Jeder Synchronisierungsordner speichert Konfiguration und Status in drei Dateien:

* `.vlt-sync-config.properties`: Konfigurationsdatei.

* `.vlt-sync.log`: Protokolldatei, die Informationen über die Vorgänge enthält, die beim Synchronisieren durchgeführt werden.
* `.vlt-sync-filter.xml`: Filter, die definieren, welche Teile des Repositorys synchronisiert werden. Das Format dieser Datei wird im Abschnitt [Durchführen eines gefilterten Auscheckens](#performing-a-filtered-checkout) beschrieben.

Die Datei `.vlt-sync-config.properties` ermöglicht es Ihnen, die folgenden Eigenschaften zu konfigurieren:

**Deaktiviert** Schaltet die Synchronisierung ein oder aus. Standardmäßig ist dieser Parameter auf false gesetzt, um die Synchronisierung zu ermöglichen.

**Einmalige Synchronisation** Wenn nicht leer, synchronisiert der folgende Scan den Ordner in der angegebenen Richtung und dann wird der Parameter gelöscht. Zwei Werte werden unterstützt:

* `JCR2FS`: exportiert alle Inhalte im JCR-Repository und schreibt auf die lokale Festplatte.
* `FS2JCR`: Importiert den gesamten Inhalt von der Festplatte in das JCR-Repository.

**Synchronisierungsprotokoll** Definiert den Dateinamen des Protokolls. Standardmäßig ist der Wert .vlt-sync.log

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

1. Bearbeiten Sie die versteckte Datei `.vlt-sync-config.properties` und konfigurieren Sie die Synchronisierung, um den Inhalt Ihres Repository zu synchronisieren:

   ```xml
   sync-once=JCR2FS
   ```

   >[!NOTE]
   >
   >Dieser Schritt lädt das gesamte Repository gemäß Ihrer Filterkonfiguration herunter.

1. Überprüfen Sie die Protokolldatei `.vlt-sync.log`, um den Fortschritt zu sehen:

   ```xml
   ***
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/
   30.04.2017 14:39:10 A file:///Users/trushton/Applications/aem/vltsync/sandbox/dev/jcr_root/apps/geometrixx-outdoors/src/core/src/main/java/info/geometrixx/outdoors/core/product/GeoProduct.java
   ***
   ```

Ihr lokaler Ordner ist jetzt mit dem Repository synchronisiert. Die Synchronisierung erfolgt bidirektional, sodass Änderungen aus dem Repository auf Ihren lokalen Synchronisierungsordner angewendet werden und umgekehrt.

>[!NOTE]
>
>Die VLT-Synchronisierungsfunktion unterstützt nur einfache Dateien und Ordner, erkennt jedoch spezielle serialisierte Vault-Dateien (.content.xml, dialog.xml usw.) und ignoriert sie stillschweigend. So ist es möglich, die Vault-Synchronisierung bei einem standardmäßigen VLT-Auschecken zu verwenden.
