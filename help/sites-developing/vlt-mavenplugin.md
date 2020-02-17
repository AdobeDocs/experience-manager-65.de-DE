---
title: Verwalten von Paketen mithilfe von Maven
seo-title: Verwalten von Paketen mithilfe von Maven
description: Verwenden Sie das Inhaltspaket-Maven-Plug-in zum Integrieren von Paketverwaltungsaufgaben in Ihre Maven-Projekte
seo-description: Verwenden Sie das Inhaltspaket-Maven-Plug-in zum Integrieren von Paketverwaltungsaufgaben in Ihre Maven-Projekte
uuid: fa73f0d6-8848-4911-9b96-311c875b45be
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 943de371-0149-4307-be3a-b11c590b3451
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Verwalten von Paketen mithilfe von Maven{#managing-packages-using-maven}

Verwenden Sie das Inhaltspaket-Maven-Plug-in zum Integrieren von Paketverwaltungsaufgaben in Ihre Maven-Projekte. Die Plug-in-Ziele und -Parameter ermöglichen Ihnen die Automatisierung der Aufgaben, die Sie für gewöhnlich auf der Seite „Paketmanager“ oder an der FileVault-Befehlszeile ausführen würden:

* Erstellen Sie neue Pakete anhand der Dateien im Dateisystem.
* Installieren und deinstallieren Sie Pakete auf dem CRX- oder CQ-Server.
* Erstellen Sie bereits auf dem Server definierte Pakete.
* Rufen Sie eine Liste der auf dem Server installierten Pakete ab.
* Entfernen Sie ein Paket vom Server.

## Hinzufügen des Inhaltspaket-Maven-Plug-ins zur POM-Datei {#adding-the-content-package-maven-plugin-to-the-pom-file}

Fügen Sie zum Verwenden des Inhaltspaket-Maven-Plug-ins das folgende Plug-in-Element im Buid-Element Ihrer POM-Datei hinzu:

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Verwenden Sie das im Abschnitt [Abrufen des Inhaltspaket-Maven-Plug-ins](#obtaining-the-content-package-maven-plugin) auf dieser Seite angegebene Profil, um Maven für das Herunterladen des Plug-ins zu aktivieren.

## Ziele des Inhaltspaket-Maven-Plug-ins {#goals-of-the-content-package-maven-plugin}

Die durch das Inhaltspaket-Plug-in bereitgestellten Ziele und Zielparameter werden in den folgenden Abschnitten beschrieben. Die im Abschnitt „Allgemeine Parameter“ beschriebenen Parameter können für die meisten der Ziele verwendet werden. Parameter, die für ein Ziel zutreffen, werden im Abschnitt für das jeweilige Ziel beschrieben.

**Plug-in-Präfix**

Das Plug-in-Präfix lautet „content-package“. Verwenden Sie dieses Präfix, um ein Ziel über die Befehlszeile auszuführen, wie dies im folgenden Beispiel gezeigt wird:

```shell
mvn content-package:build
```

**Parameterpräfix**

Soweit nicht anderweitig gekennzeichnet, verwenden die Plug-in-Ziele und -Parameter das Präfix „vault“. Dies gilt auch für das folgende Beispiel:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

**Proxys**

Ziele, die Proxys für den CRX- oder CQ-Server verwenden, verwenden die erste in den Maven-Einstellungen gefundene gültige Proxykonfiguration. Wenn keine Proxykonfiguration gefunden wird, wird kein Proxy verwendet. Siehe hierzu den Parameter „useProxy“ im Abschnitt „Allgemeine Einstellungen“.

### Allgemeine Parameter {#common-parameters}

Die Parameter in der folgenden Tabelle gelten für alle Ziele, sofern kein entsprechender Hinweis in der Spalte „Ziele“ vorliegt.

<table>
 <tbody>
  <tr>
   <th>Name</th>
   <th>Typ</th>
   <th>Erforderlich</th>
   <th>Standardwert</th>
   <th>Beschreibung</th>
   <th>Ziele</th>
  </tr>
  <tr>
   <td>failOnError</td>
   <td>Boolesch</td>
   <td>Nein</td>
   <td>false</td>
   <td>Der Wert <code>true</code> führt zum Fehlschlagen des Builds, wenn ein Fehler auftritt. Der Wert <code>false</code> führt dazu, dass der Build den Fehler ignoriert.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>name</td>
   <td>Zeichenfolge</td>
   <td>build: Ja<br /> Installation: No<br /> rm:Ja</td>
   <td>Erstellen: Kein Standard.<br /> install: Der Wert der Eigenschaft „artifactId“ des Maven-Projekts.</td>
   <td>Der Name des zu bearbeitenden Pakets.</td>
   <td>Alle Ziele mit Ausnahme von „Is“.</td>
  </tr>
  <tr>
   <td>password</td>
   <td>Zeichenfolge</td>
   <td>Ja</td>
   <td>admin</td>
   <td>Das für die Authentifizierung am CRX-Server verwendete Kennwort.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>serverId</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td></td>
   <td>Die Server-ID, über die der Benutzername und das Kennwort für die Authentifizierung abgerufen werden.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>targetURL</td>
   <td>Zeichenfolge</td>
   <td>Ja</td>
   <td>http://localhost:4502/<br /> crx/packmgr/<br /> service.jsp</td>
   <td>Die URL der HTTP-Dienst-API des CRX-Paketmanagers.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>Zeitüberschreitung</td>
   <td>int</td>
   <td>Nein</td>
   <td>5</td>
   <td>Die Verbindungs-Zeitüberschreitung für die Kommunikation mit dem Paketmanagerdienst in Sekunden.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>useProxy</td>
   <td>Boolesch</td>
   <td>Nein</td>
   <td>true</td>
   <td>Bestimmt, ob Proxykonfigurationen aus der Maven-Einstellungsdatei verwendet werden sollen. A value of <code>true</code> causes the use of the first active proxy configuration found to proxy requests to the package manager. Der Wert „false“ führt dazu, dass kein Proxy verwendet wird.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>userId</td>
   <td>Zeichenfolge</td>
   <td>Ja</td>
   <td>admin</td>
   <td>Der am CRX-Server zu authentifizierende Benutzername.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
  <tr>
   <td>verbose</td>
   <td>Boolesch</td>
   <td>Nein</td>
   <td>false</td>
   <td>Aktiviert oder deaktiviert die ausführliche Protokollierung. Der Wert <code>true</code> aktiviert die ausführliche Protokollierung.</td>
   <td>Alle Ziele mit Ausnahme von „package“.</td>
  </tr>
 </tbody>
</table>

### Build {#build}

Erstellt ein Inhaltspaket, das bereits auf einer AEM-Instanz definiert ist.

>[!NOTE]
>
>Dieses Ziel muss nicht in einem Maven-Projekt ausgeführt werden.

#### Parameter {#parameters}

Alle Parameter für das Buildziel werden im Abschnitt [Allgemeine Parameter](#common-parameters) beschrieben.

#### Beispiel {#example}

Im folgenden Beispiel wird das Workflow-mbean-Paket erstellt, das auf der AEM-Instanz mit der IP-Adresse 10.36.79.223 installiert ist. Das Ziel wird mit dem folgenden Befehl ausgeführt:

```shell
mvn content-package:build
```

Die folgende POM-Datei befindet sich im aktuellen Verzeichnis des Befehlszeilentools. Der POM gibt den Paketnamen und die URL des Paketdiensts an.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### install {#install}

Installiert ein Paket im Repository. Für die Ausführung dieses Ziels ist kein Maven-Projekt erforderlich. Das Ziel ist an die Installationsphase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-1}

In addition to the following parameters, see the descriptions in the [Common Parameters](#common-parameters) section.

<table>
 <tbody>
  <tr>
   <th>Name</th>
   <th>Typ</th>
   <th>Erforderlich</th>
   <th>Standardwert</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Artefakt</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td>Der Wert der Eigenschaft „artifactId“ des Maven-Projekts.</td>
   <td>Eine Zeichenfolge in der Form groupId:artifactId:version[:packaging].</td>
  </tr>
  <tr>
   <td>artifactId</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td></td>
   <td>Die ID des einzubettenden Artefakts.</td>
  </tr>
  <tr>
   <td>groupId</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td></td>
   <td>Die Gruppen-ID des zu installierenden Artefakts.</td>
  </tr>
  <tr>
   <td>Installieren</td>
   <td>Boolesch</td>
   <td>Nein</td>
   <td>true</td>
   <td>Bestimmt, ob das Paket beim Hochladen automatisch entpackt werden soll. Wenn der Wert „true“ vorliegt, wird das Paket entpackt. Liegt hingegen der Wert „false“ vor, wird das Paket nicht entpackt.</td>
  </tr>
  <tr>
   <td>localRepository</td>
   <td>org.apache.maven.<br /> Artefakt. repository.<br /> ArtifactRepository</td>
   <td>Nein</td>
   <td>Der Wert der Systemvariablen „localRepository“.</td>
   <td>Das lokale Maven-Repository. Sie können diesen Parameter nicht mithilfe der Plug-in-Konfiguration konfigurieren. Die Systemeigenschaft wird immer verwendet.</td>
  </tr>
  <tr>
   <td>packageFile</td>
   <td>java.io.File</td>
   <td>Nein</td>
   <td>Das für das Maven-Projekt definierte primäre Artefakt.</td>
   <td>Der Name der zu installierenden Paketdatei.</td>
  </tr>
  <tr>
   <td>packaging</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td>zip</td>
   <td>Der Verpackungstyp des zu installierenden Artefakts.</td>
  </tr>
  <tr>
   <td>pomRemoteRepositories</td>
   <td>java.util.List</td>
   <td>Ja</td>
   <td>Der Wert der für das Maven-Projekt definierten Eigenschaft „remoteAtifactRepositories“.</td>
   <td>Dieser Wert kann nicht mithilfe der Plugin-Konfiguration konfiguriert werden. Der Wert muss im Projekt angegeben werden. </td>
  </tr>
  <tr>
   <td>Projekt</td>
   <td>org.apache.maven.<br /> project.MavenProject</td>
   <td>Ja</td>
   <td>Das Projekt, für das das Plugin konfiguriert ist.</td>
   <td>Das Maven-Projekt. Das Projekt ist implizit, da das Projekt die Plug-in-Konfiguration aufweist.</td>
  </tr>
  <tr>
   <td>repositoryId <i>(POM)</i><br /> repoID <i>(Befehlszeile)</i></td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td>temp</td>
   <td>Die ID des Repositorys, vom dem das Artefakt abgerufen wird. Verwenden Sie „repositoryID“ in einem POM. Verwenden Sie „repoID“ an einer Befehlszeile.</td>
  </tr>
  <tr>
   <td>repositoryUrl <i>(POM)</i><br /> repoURL <i>(Befehlszeile)</i></td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td></td>
   <td>Die URL des Repositorys, vom dem das Artefakt abgerufen wird. Verwenden Sie „repositoryURL“ in einem POM. Verwenden Sie „repoURL“ an einer Befehlszeile.</td>
  </tr>
  <tr>
   <td>Version</td>
   <td>Zeichenfolge</td>
   <td>Nein</td>
   <td></td>
   <td>Die Version des zu installierenden Artefakts.</td>
  </tr>
 </tbody>
</table>

#### Beispiel {#example-1}

Im folgenden Beispiel wird ein Paket erstellt, in dem das workflow-mbean OSGi-Bundle (siehe hierzu das Beispiel für das [Build](#build)-Ziel) enthalten ist. Anschließend wird das Paket installiert. Da das Installationsziel an die Paketinstallationsphase gebunden ist, führt der folgende Befehl das Installationsziel aus:

```shell
mvn install
```

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

### ls {#ls}

Führt die im Paketmanager bereitgestellten Pakete auf.

#### Parameter {#parameters-2}

All parameters of the ls goal are described in the [Common Parameters](#common-parameters) section.

#### Beispiel {#example-2}

Im folgenden Beispiel werden die auf der AEM-Instanz installierten Pakete mit der IP-Adresse 10.36.79.223 aufgeführt. Das Ziel wird mit dem folgenden Befehl ausgeführt:

```shell
mvn content-package:ls
```

Die folgende POM-Datei befindet sich im aktuellen Verzeichnis des Befehlszeilentools. Der POM gibt die URL des Paketdiensts an.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### rm {#rm}

Entfernt ein Paket aus dem Paketmanager.

#### Parameter {#parameters-3}

All parameters of the rm goal are described in the [Common Parameters](#common-parameters) section.

#### Beispiel {#example-3}

Im folgenden Beispiel wird das Paket workfow-mbean entfernt, das auf der AEM-Instanz mit der IP-Adresse 10.36.79.223 installiert ist. Das Ziel wird mit dem folgenden Befehl ausgeführt:

```shell
mvn content-package:rm
```

Die folgende POM-Datei befindet sich im aktuellen Verzeichnis des Befehlszeilentools. Der POM gibt die URL des Paketdiensts und den Namen des Pakets an.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
                    <name>workflow-mbean</name>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### uninstall {#uninstall}

Deinstalliert ein Paket. Das Paket verbleibt auf dem Server mit dem deinstallierten Status.

#### Parameter {#parameters-4}

All parameters of the uninstall goal are described in the [Common Parameters](#common-parameters) section.

#### Beispiel {#example-4}

Im folgenden Beispiel wird das Workflow-mbean-Paket deinstalliert, das auf der AEM-Instanz mit der IP-Adresse 10.36.79.223 installiert ist. Das Ziel wird mit dem folgenden Befehl ausgeführt:

```shell
mvn content-package:uninstall
```

Die folgende POM-Datei befindet sich im aktuellen Verzeichnis des Befehlszeilentools. Der POM gibt den Paketnamen und die URL des Paketdiensts an.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### package {#package}

Erstellt ein Inhaltspaket. Die Standardkonfiguration des Paketziels umfasst die Inhalte des Verzeichnisses, in dem kompilierte Dateien gespeichert sind. Für die Ausführung des Paketziels muss die Phase der Build-Kompilierung abgeschlossen sein. Das Paketziel ist an die Paketphase des Maven-Build-Lebenszyklus gebunden.

#### Parameter {#parameters-5}

In addition to the following parameters, see the description of the `name` parameter in the [Common Parameters](#common-parameters) section.

<table>
 <tbody>
  <tr>
   <th>Name</th>
   <th>Typ</th>
   <th>Erforderlich</th>
   <th>Standardwert</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>archive</td>
   <td>org.apache.maven.<br /> archiver.<br /> MavenArchiveConfiguration</td>
   <td>Nein</td>
   <td></td>
   <td>Die zu verwendende Archivkonfiguration. Siehe die <a href="https://maven.apache.org/shared/maven-archiver/index.html">Dokumentation für Maven Archiver</a>.</td>
  </tr>
  <tr>
   <td>builtContentDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>Der Wert des Ausgabeverzeichnisses des Maven-Builds.</td>
   <td>Das Verzeichnis mit den in das Paket einzuschließenden Inhalten.</td>
  </tr>
  <tr>
   <td>dependencies</td>
   <td>java.util.List</td>
   <td>Nein</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>embeddedTarget</td>
   <td>java.lang.String</td>
   <td>Nein</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>embeddeds</td>
   <td>java.util.List</td>
   <td>Nein</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>failOnMissingEmbed</td>
   <td>Boolesch</td>
   <td>Ja</td>
   <td>false</td>
   <td>Der Wert "true"führt dazu, dass der Build fehlschlägt, wenn kein eingebettetes Artefakt in den Projektabhängigkeiten gefunden wird. Ein Wert löst aus, dass der Build den Fehler ignoriert.</td>
  </tr>
  <tr>
   <td>filterSource</td>
   <td>java.io.File</td>
   <td>Nein</td>
   <td></td>
   <td>Eine die Quelle des Arbeitsbereichsfilters angebende Datei. Die in der Konfiguration angegebenen und über Einbettungen oder Teilpakete eingefügten Filter werden mit dem Dateiinhalt zusammengeführt.</td>
  </tr>
  <tr>
   <td>filters</td>
   <td>com.day.jcr.<br /> vault.maven.pack.impl.<br /> DefaultWorkspaceFilter</td>
   <td>Nein</td>
   <td></td>
   <td>Enthält Filterelemente, die den Paketinhalt definieren. Bei der Ausführung werden die Filter in der Datei „filter.xml“ eingeschlossen. Siehe hierzu im Folgenden den Abschnitt „Verwenden von 'filters'“.</td>
  </tr>
  <tr>
   <td>finalName</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>Der im Maven-Projekt definierte finalName (Build-Phase).</td>
   <td>Der Name der generierten ZIP-Paketdatei ohne ZIP-Dateierweiterung.</td>
  </tr>
  <tr>
   <td>group</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>Die im Maven-Projekt definierte groupID.</td>
   <td>Die groupID des generierten Inhaltspakets. Dieser Wert ist Bestandteil des Zielinstallationspfads für das Inhaltspaket.</td>
  </tr>
  <tr>
   <td>outputDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>Das im Maven-Projekt definierte Build-Verzeichnis.</td>
   <td>Das lokale Verzeichnis, in dem das Inhaltspaket gespeichert ist.</td>
  </tr>
  <tr>
   <td>prefix</td>
   <td>java.lang.String</td>
   <td>Nein</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>Projekt</td>
   <td>org.apache.maven.<br /> project.MavenProject</td>
   <td>Ja</td>
   <td></td>
   <td>Das Maven-Projekt.</td>
  </tr>
  <tr>
   <td>properties</td>
   <td>java.util.Map</td>
   <td>Nein</td>
   <td></td>
   <td>Zusätzliche Eigenschaften, die Sie in der Datei „properties.xml“ festlegen können. Diese Eigenschaften können die folgenden vordefinierten Eigenschaften nicht außer Kraft setzen:
    <ul>
     <li>Gruppe: Verwenden Sie den Gruppenparameter</li>
     <li>name: Parameter name verwenden, um</li>
     <li>Version: Verwenden Sie den Parameter version, um</li>
     <li>description: Aus Projektbeschreibung auswählen</li>
     <li>groupId: Die groupId des Maven-Projektdeskriptors</li>
     <li>artifactId: Die artifactId des Maven-Projektdeskriptors</li>
     <li>Abhängigkeiten: Abhängigkeitsparameter verwenden, um</li>
     <li>createdBy: Der Wert der Systemeigenschaft user.name</li>
     <li>erstellt: Die aktuelle Systemzeit</li>
     <li>requireRoot: Verwenden Sie den Parameter requireRoot, um</li>
     <li>packagePath: Automatisch aus dem Gruppen- und Paketnamen generiert</li>
    </ul> </td>
  </tr>
  <tr>
   <td>requiresRoot</td>
   <td>Boolesch</td>
   <td>Ja</td>
   <td>false</td>
   <td>Definiert, ob für das Paket „root“ erforderlich ist Dies wird zur Eigenschaft &lt;code&gt;requiresRoot&lt;/code&gt; der Datei „properties.xml“.</td>
  </tr>
  <tr>
   <td>subPackages</td>
   <td>java.util.List</td>
   <td>Nein</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>Version</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>Die im Maven-Projekt definierte Version</td>
   <td>Die Version des Inhaltspakets</td>
  </tr>
  <tr>
   <td>workDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>Das im Maven-Projekt (Build-Phase) definierte Verzeichnis.</td>
   <td>Das Verzeichnis mit den in das Paket einzuschließenden Inhalten.</td>
  </tr>
 </tbody>
</table>

#### Verwenden von „filters“{#using-filters}

Verwenden Sie das Element „filters“ zum Definieren des Paketinhalts. Die Filter werden zum Element „workspaceFilter“ in der Datei `META-INF/vault/filter.xml` des Pakets hinzugefügt.

Im folgenden Filterbeispiel wird die zu verwendende XML-Struktur gezeigt:

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

**Importieren von „mode“**

Das Element `mode` definiert, wie sich das Importieren des Pakets auf den Inhalt im Repository auswirkt. Die folgenden Werte können verwendet werden:

* **Merge:** Inhalt im Paket, der sich nicht bereits im Repository befindet, wird hinzugefügt. Inhalt, der sich im Paket und Repository befindet, verbleibt unverändert. Es wird kein Inhalt aus dem Repository entfernt.
* **** Ersetzen: Inhalte im Paket, die sich nicht im Repository befinden, werden dem Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Inhalt wird aus dem Repository entfernt, wenn er im Paket nicht vorhanden ist.
* **Update:** Inhalt im Paket, der sich nicht im Repository befindet, wird zum Repository hinzugefügt. Inhalt im Repository wird durch übereinstimmenden Inhalt im Paket ersetzt. Vorhandener Inhalt wird aus dem Repository entfernt.

Wenn der Filter kein `mode`-Element aufweist, wird der Standardwert `replace` verwendet.

#### Beispiel {#example-5}

Im folgenden Beispiel wird ein Paket erstellt, das das workflow-mbean OSGi-Bundle enthält. Die POM-Datei identifiziert das Verzeichnis „jcr_root“ als den Wert der Eigenschaft „builtContentDirectory“. Das Verzeichnis „jcr_root“ enthält die Bundle-JAR-Datei in der Verzeichnisstruktur, die das Repository spiegelt:

`jcr_root/apps/myapp/install/workflow-mbean-0.03-SNAPSHOT.jar`

Da das Ziel an die Paket-Build-Phase gebunden ist, führt der folgende Befehl das Paketziel aus:

`mvn package`

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

Instead of expressing the `package` goal in the plugin `executions` section, you can use `content-package` as the value of the project `packaging` element:

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
  <packaging>content-package</packaging>
  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

### help {#help}

#### Parameter {#parameters-6}

| Name | Typ | Erforderlich | Standardwert | Beschreibung |
|---|---|---|---|---|
| detail | Boolesch | Nein | false | Bestimmt, ob alle festlegbaren Eigenschaften für jedes Ziel angezeigt werden sollen. Der Wert „true“ zeigt alle festlegbaren Eigenschaften an. |
| goal | Zeichenfolge | Nein |  | Der Name des Ziels, für das die Hilfe angezeigt werden soll. Wenn kein Wert angegeben wird, wird die Hilfe für alle Ziele angezeigt. |
| indentSize | int | Nein | 2 | Die Anzahl der für die Einrückung jeder Ebene zu verwendenden Leerzeichen. Wenn Sie einen Wert angeben, sollte dieser positiv sein. |
| lineLength | int | Nein | 80 | Die maximale Länge einer Anzeigezeile. Wenn Sie einen Wert angeben, sollte dieser positiv sein. |

## Abrufen des Inhaltspaket-Maven-Plug-ins {#obtaining-the-content-package-maven-plugin}

Das Plug-in steht über das öffentliche Adobe-Repository zur Verfügung. Fügen Sie zum Herunterladen des Plug-ins Ihrer Maven-Einstellungsdatei das folgende Maven-Profil hinzu und aktivieren Sie es. Beim Verwenden eines Maven-Befehls wird das Plug-in bei Bedarf in Ihr lokales Repository heruntergeladen.

>[!NOTE]
>
>Das Adobe Public Releases-Repository kann nicht durchsucht werden. Wenn Sie mithilfe Ihres Webbrowsers zur Repository-URL navigieren, führt dies demnach zum Fehler „Nicht gefunden“. Maven kann jedoch auf Repository-Verzeichnisse zugreifen.

```xml
<profile>
    <id>adobe-public</id>
    <activation>
         <activeByDefault>false</activeByDefault>
    </activation>
    <properties>
         <releaseRepository-Id>adobe-public-releases</releaseRepository-Id>
         <releaseRepository-Name>Adobe Public Releases</releaseRepository-Name>
         <releaseRepository-URL>https://repo.adobe.com/nexus/content/groups/public</releaseRepository-URL>
    </properties>
    <repositories>
         <repository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </repository>
     </repositories>
     <pluginRepositories>
         <pluginRepository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </pluginRepository>
     </pluginRepositories>
</profile>
```

## Einbetten von OSGi-Bundles in einem Inhaltspaket {#embedding-osgi-bundles-in-a-content-package}

Verwenden Sie das Inhaltspaket-Maven-Plug-in, um OSGi-Bundles in Ihrem Inhaltspaket einzubetten. Implementieren Sie zum Einbetten des Bundles die folgenden Konfigurationen:

* Das Bundle muss als eine Abhängigkeit des Maven-Projekts deklariert werden.
* Die Plug-in-Konfiguration verweist unter Verwendung des gewünschten Pfads des Bundles im Paket auf das Bundle.

Der folgende Beispiel-POM erstellt ein Paket, das das Bundle „Apache Sling JCR UserManager“ enthält. In the package, the bundle JAR is located in the `jcr_root/apps/myapp/install` folder:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0"
             xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
             https://maven.apache.org/maven-v4_0_0.xsd">
 <modelVersion>4.0.0</modelVersion>
   <groupId>com.adobe.example.myapp</groupId>
 <artifactId>embedded-example</artifactId>
 <packaging>content-package</packaging>
 <version>1.0.0-SNAPSHOT</version>

   <build>
 <plugins>
     <plugin>
        <groupId>com.day.jcr.vault</groupId>
      <artifactId>content-package-maven-plugin</artifactId>
      <version>0.0.24</version>
      <extensions>true</extensions>
      <configuration>
   <filters>
       <filter>
    <root>/apps/myapp</root>
       </filter>
    </filters>
    <embeddeds>
       <embedded>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
    <target>/apps/myproject/install</target>
        </embedded>
    </embeddeds>
       </configuration>
  </plugin>
    </plugins>
    </build>
    <dependencies>
 <dependency>
      <groupId>org.apache.sling</groupId>
      <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
      <version>2.2.0</version>
 </dependency>
    </dependencies>
</project>
```

## Einbeziehen eines Miniaturbilds oder einer Eigenschaftsdatei im Paket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Ersetzen Sie die standardmäßigen Paketkonfigurationsdateien, um die Paketeigenschaften anzupassen. Verwenden Sie beispielsweise ein Miniaturbild, um das Paket im Paketmanager und in Package Share voneinander zu unterscheiden.

Im Paket befinden sich die FileVault-spezifischen Dateien im Ordner „/META-INF/vault“. Die Quelldateien können sich überall in Ihrem Dateisystem befinden. Definieren Sie in der POM-Datei die Build-Ressourcen, um die Quelldateien nach „target/vault-work/META-INF“ zu kopieren, um sie ins Paket einzuschließen.

Im folgenden POM-Code werden die Dateien im Ordner „META-INF“ der Projektquelle zum Paket hinzugefügt:

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Im folgenden POM-Code wird nur ein Miniaturbild zum Paket hinzugefügt. Das Miniaturbild muss „thumbnail.png“ benannt werden und sich im Ordner „META-INF/vault/definition“ des Pakets befinden. In diesem Beispiel befindet sich die Quelldatei im Ordner „/src/main/content/META-INF/vault/definition“ des Projekts:

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## Using Archetypes To Generate AEM Projects {#using-archetypes-to-generate-aem-projects}

Es stehen verschiedene Maven-Archetypen zum Generieren von AEM-Projekten zur Verfügung. Verwenden Sie den Archetyp, der Ihren Entwicklungszielen entspricht:

* A content package that installs resources for a AEM application: [simple-content-package-archetype](#simple-content-package-archetype)
* Ein Inhaltspaket mit Drittanbieterartefakten: [simple-content-package-with-embedded-archetype](#simple-content-package-with-embedded-archetype).
* Eine Anwendung mit mehreren Modulen, die die Entwicklung von Java-Klassen und Einheitentests vereint: [multimodule-content-package-archetype](#multimodule-content-package-archetype).

>[!NOTE]
>
>Das Apache Sling-Projekt bietet außerdem Archetypen, die für die AEM-Entwicklung nützlich sind. These are documented at [https://sling.apache.org/site/maven-archetypes.html](https://sling.apache.org/documentation/development/maven-archetypes.html).

Jeder Archetyp generiert die folgenden Elemente:

* die Projektordnerstruktur
* POM-Dateien
* FileVault-Konfigurationsdateien

Archetypartefakte stehen über das öffentliche Maven-Repository von Adobe zur Verfügung. Ermitteln Sie zum Herunterladen und Ausführen eines Archetyps den Archetyp und das Adobe-Repository mithilfe der Parameter des Maven-Befehls „archetype:generate“:

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId={id_of_archetype} -DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

Das Maven-Archetyp-Plug-in verwendet den interaktiven Modus in der Shell oder Eingabeaufforderung, um Informationen über Ihr Projekt zu sammeln. Die von Ihnen bereitgestellten Informationen werden zum Konfigurieren verschiedener Projekteigenschaften verwendet. Dazu zählen beispielsweise Ordnernamen und Artefakt-IDs.

**POM-Dateien**

Die erzeugten POM-Dateien enthalten Befehle zum Kompilieren von Code, zum Erstellen von Bundles und zum Bereitstellen in AEM in Paketen. The `groupID`, `artifactId`, `version`, and `name` properties of the Maven project are automatically populated using the values that you provide to the Maven `archetype:generate` interactive prompt.

Sie können die folgenden Standardwerte in der generierten Datei &quot;pom.xml&quot;ändern:

* The CQ server name or IP address: The default value is `localhost`. The `crx.host` element below `project/properties` contains this value.

* Die Portnummer für den CQ-Server: Der Standardwert ist `4502`. The `crx.port` element below `project/properties` contains this value.

* Die des Inhaltspaket-Maven-Plug-ins: Verwenden Sie die neueste Version als Inhalt des Elements `version`version für das Plug-in mit der `artifactId` `content-package-maven-plugin`. Der Standardwert ist `0.0.24`.

**Verwenden der Archetypen**

1. Geben Sie in einem Shell-Fenster oder an einer Eingabeaufforderung den Maven-Befehl `archetype:generate` ein. Geben Sie bei einer entsprechenden Aufforderung die Werte für die verbleibenden Parameter an.

   Informationen zu den einzelnen Parametern finden Sie im Abschnitt zum verwendeten Archetyp.

1. Verwenden Sie einen Text-Editor zum Öffnen der Datei „pom.xml“ und Bearbeiten der Standardwerte entsprechend Ihren Anforderungen.
1. Füllen Sie die generierten Ordner mit Ressourcen auf.
1. Geben Sie den `mvn clean install` Befehl ein.

### simple-content-package-archetype {#simple-content-package-archetype}

Erstellt ein Maven-Projekt, das zum Installieren von Ressourcen für eine einfache AEM-Anwendung geeignet ist. The folder structure is that used below the `/apps` folder of the AEM repository. Das POM definiert Befehle zum Verpacken der Ressourcen, die Sie in den Ordnern platzieren, und zum Installieren der Pakete auf der AEM-Instanz.

**Archetypartefakteigenschaften:**

* Gruppen-ID: `com.day.jcr.vault`
* Artefakt-ID: `simple-content-package-archetype`
* Version: `1.0.2`
* Repository: `adobe-public-releases`

**Maven-Befehl:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Archetypparameter:**

* groupId: Die groupId des durch Maven generierten Inhaltspakets. Der Wert wird automatisch in der POM-Datei verwendet.
* artifactId: Der Name des Inhaltspakets. Der Wert wird auch als der Name des Projektordners verwendet.
* version: Die Version des Inhaltspakets.
* package: Dieser Wert wird für „simple-content-package-archetype“ nicht verwendet.
* appsFolderName: Der Name des Ordners unter /apps.
* artifactName: Die Beschreibung des Inhaltspakets.
* packageGroup: Der Name der Inhaltspaketgruppe. Dieser Wert konfiguriert den Parameter „group“ für das Paketziel des Inhaltspaket-Maven-Plug-ins.

**Ordnerstruktur:**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components
                               |- .content.xml
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
                        |- .content.xml
```

### simple-content-package-with-embedded-archetype {#simple-content-package-with-embedded-archetype}

Führt dieselben Aufgaben wie „simple-content-package-archetype“ aus und lädt zudem ein Artefakt aus einem öffentlichen Maven-Repository herunter und schließt es ein.

**Archetyp-Bundle-Eigenschaften:**

* Gruppen-ID: `com.day.jcr.vault`
* Artefakt-ID: `simple-content-package-with-embedded-archetype`
* Version: `1.0.2`
* Repository: `adobe-public-releases`

**Maven-Befehl:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-with-embedded-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Archetypparameter:**

* groupId: Die groupId des durch Maven generierten Inhaltspakets. Der Wert wird automatisch in der POM-Datei verwendet.
* artifactId: Der Name des Inhaltspakets. Der Wert wird auch als der Name des Projektordners verwendet.
* version: Die Version des Inhaltspakets.
* package: Dieser Parameter wird nicht verwendet.
* appsFolderName: Der Name des Ordners unter /apps.
* artifactName: Die Beschreibung des Inhaltspakets.
* embeddedArtifactId: Die ID des in das Inhaltspaket einzubettenden Artefakts.
* embeddedGroupId: Die Gruppen-ID des einzubettenden Artefakts.
* embeddedVersion: Die Version des einzubettenden Artefakts.
* packageGroup: Der Name der Inhaltspaketgruppe. Dieser Wert konfiguriert den Parameter „group“ für das Paketziel des Inhaltspaket-Maven-Plug-ins.

**Ordnerstruktur:**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
```

### multimodule-content-package-archetype {#multimodule-content-package-archetype}

Erstellt ein Masterprojekt, das die Ordnerstruktur zum Entwickeln einer AEM-Anwendung und Installieren von Ressourcen auf dem Server enthält.

Der Ordner `bundle` enthält die Ordnerstruktur, in der die Java- und JUnit-Quelldateien gespeichert sind, die Sie entwickeln. Die Datei „pom.xml“ in diesem Ordner erstellt das OSGi-Bundle. Die folgenden Werte im POM ermitteln das Artefakt und das Bundle:

* artifactID: `${artifactID}-bundle`.
* Bundle-SymbolicName: `${groupId}.${artifactId}-bundle`.

`${artifactID}` und `${groupId}` sind die Werte, die Sie bei der Ausführung der Archetypen für diese Parameter angeben.

The `content` folder contains the resources that are installed to the AEM instance. The value of artifactID is `${artifactID}multimodule-bundle`.

Der übergeordnete Ordner enthält den übergeordneten POM, der Maven-Plug-ins und -Abhängigkeiten verwaltet.

**Archetyp-Bundle-Eigenschaften:**

* Gruppen-ID: `com.day.jcr.vault`
* Artefakt-ID: `multimodule-content-package-archetype`
* Version: `1.0.2`
* Repository: `adobe-public-releases`

**Maven-Befehl:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=multimodule-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Archetypparameter:**

* groupId: Die groupId des durch Maven generierten Inhaltspakets. Der Wert wird automatisch in der POM-Datei verwendet.
* artifactId: Der Name des Inhaltspakets. Der Wert wird auch als der Name des Projektordners verwendet.
* version: Die Version des Inhaltspakets.
* package: Dieser Wert wird für „multimodule-content-package-archetype“ nicht verwendet.
* appsFolderName: Der Name des Ordners unter /apps.
* artifactName: Die Beschreibung des Inhaltspakets.
* packageGroup: Der Name der Inhaltspaketgruppe. Dieser Wert konfiguriert den Parameter „group“ für das Paketziel des Inhaltspaket-Maven-Plug-ins.

**Ordnerstruktur:**

```xml
${artifactId}
   |- pom.xml
   |- bundle
      |- pom.xml
      |- src
         |- main
            |- java
               |- ${groupId}
                  |- SimpleDSComponent.java
         |- test
            |- java
               |- ${groupId}
                  |- SimpleUnitTest.java
   |- content
      |- pom.xml
      |- src
         |- main
            |- content
               |- jcr_root
                  |- apps
                     |- ${appsFolderName}
                            |- config
                            |- install
                  |- META-INF
                      |- vault
                         |- config.xml
                         |- filter.xml
                         |- nodetypes.cnd
                         |- properties.xml
                         |- definition
                            |- .content.xml
```

