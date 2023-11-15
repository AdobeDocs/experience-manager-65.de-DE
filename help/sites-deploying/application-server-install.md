---
title: Installation des Anwendungs-Servers
description: Erfahren Sie, wie Sie Adobe Experience Manager mit einem Anwendungsserver installieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 3a90f1d2-e53f-4cc4-8122-024ad6500de0
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 44%

---

# Installation des Anwendungs-Servers{#application-server-install}

>[!NOTE]
>
>`JAR` und `WAR` sind die Dateitypen, in denen Adobe Experience Manager (AEM) veröffentlicht wird. Diese Formate unterliegen einer Qualitätssicherung, um den Support-Level zu berücksichtigen, zu denen sich Adobe verpflichtet hat.
>

In diesem Abschnitt erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit einem Anwendungsserver installieren. Lesen Sie die [Unterstützte Plattformen](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) Informationen zu den spezifischen Unterstützungsebenen für die einzelnen Anwendungsserver.

Es werden die Installationsschritte der folgenden Anwendungsserver beschrieben:

* [WebSphere](#websphere)
* [JBoss](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Lesen Sie die entsprechende Anwendungsserverdokumentation, um weitere Informationen über das Installieren von Webanwendungen, Serverkonfigurationen und darüber zu erhalten, wie der Server gestartet und angehalten wird.

>[!NOTE]
>
>Wenn Sie Dynamic Media in einer WAR-Bereitstellung verwenden, lesen Sie [Dynamic Media-Dokumentation](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Allgemeine Beschreibung {#general-description}

### Standardverhalten beim Installieren von AEM auf einem Anwendungsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wird als einzelne WAR-Datei bereitgestellt.

Bei Bereitstellung geschieht standardmäßig Folgendes:

* Der Ausführungsmodus lautet `author`.
* Die Instanz (Repository, Felix OSGI-Umgebung, Bundles usw.) wird in installiert. `${user.dir}/crx-quickstart`where `${user.dir}` das aktuelle Arbeitsverzeichnis ist, wird dieser Pfad zu crx-quickstart aufgerufen `sling.home`

* Der Kontextstamm ist beispielsweise der Name der WAR-Datei.  `aem-6`

#### Konfiguration {#configuration}

Sie können das Standardverhalten wie folgt ändern:

* Ausführungsmodus: Konfigurieren Sie den Parameter `sling.run.modes` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* sling.home: Konfigurieren Sie den Parameter `sling.home` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* Kontextstamm: Benennen Sie die AEM-WAR-Datei um.

#### Installationsveröffentlichung {#publish-installation}

Um eine Veröffentlichungsinstanz bereitzustellen, müssen Sie den Ausführungsmodus auf &quot;publish&quot;festlegen:

* Entpacken Sie WEB-INF/web.xml aus der WAR-Datei AEM
* Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
* Datei &quot;web.xml&quot;in AEM WAR-Datei replizieren
* Stellen Sie die AEM-WAR-Datei bereit.

#### Installationsprüfung {#installation-check}

Um zu überprüfen, ob alle installiert sind, können Sie Folgendes tun:

* Untersuchen der Datei `error.log`, um anzuzeigen, ob der gesamte Inhalt installiert ist.
* Überprüfen in `/system/console`, ob alle Bundles installiert sind

#### Zwei Instanzen auf demselben Anwendungsserver {#two-instances-on-the-same-application-server}

Zu Demonstrationszwecken kann es sinnvoll sein, die Autoren- und Veröffentlichungsinstanz auf einem Anwendungsserver zu installieren. Gehen Sie dazu wie folgt vor:

1. Ändern Sie die Variablen „sling.home“ und „sling.run.modes“ der Veröffentlichungsinstanz.
1. Entpacken Sie die Datei „WEB-INF/web.xml“ aus der AEM-WAR-Datei.
1. Ändern Sie den Parameter sling.home in einen anderen Pfad (absolute und relative Pfade sind möglich).
1. Ändern Sie „sling.run.modes“ für die Veröffentlichungsinstanz in „publish“ (veröffentlichen).
1. Packen Sie die Datei „web.xml“ erneut.
1. Benennen Sie die WAR-Dateien um, sodass sie unterschiedliche Namen haben. Beispielsweise wird ein Name in aemauthor.war und ein anderer in aempublish.war umbenannt.
1. Verwenden Sie höhere Speichereinstellungen. Beispiel: Standardinstanzen verwenden AEM `-Xmx3072m`
1. Stellen Sie die beiden Webanwendungen bereit.
1. Halten Sie nach der Bereitstellung die beiden Webanwendungen an.
1. Stellen Sie in den Erstellungs- und Veröffentlichungsinstanzen sicher, dass in den „sling.properties“-Dateien die Eigenschaft „felix.service.urlhandlers=false“ auf „false“ festgelegt ist (standardmäßig ist der Wert auf „true“ gesetzt).
1. Starten Sie die beiden Webanwendungen erneut.

## Installationsverfahren für Anwendungsserver {#application-servers-installation-procedures}

### WebSphere® 8.5 {#websphere}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**Servervorbereitung**

* Lassen Sie einfache Auth-Header durchgehen:

   * Eine Möglichkeit, AEM Benutzer authentifizieren zu können, besteht darin, die globale Verwaltungssicherheit des WebSphere®-Servers zu deaktivieren. Gehen Sie dazu zu Sicherheit > Globale Sicherheit und deaktivieren Sie das Kontrollkästchen Enable administrative security , speichern und starten Sie den Server neu.

* set `"JAVA_OPTS= -Xmx2048m"`
* Wenn Sie AEM mit Kontextstamm = / installieren möchten, ändern Sie den Kontextstamm der vorhandenen Standard-Webanwendung.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Nehmen Sie bei Bedarf Konfigurationen in web.xml vor (siehe oben in der allgemeinen Beschreibung).

   * Entpacken Sie die Datei „WEB-INF/web.xml“.
   * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
   * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
   * Packen Sie die Datei „web.xml“ erneut.

* Bereitstellen der AEM-WAR-Datei

   * Wählen Sie einen Kontextstamm aus (wenn Sie die Sling-Ausführungsmodi festlegen möchten, müssen Sie die detaillierten Schritte des Bereitstellungsassistenten auswählen und dann in Schritt 6 des Assistenten angeben)

* AEM Webanwendung starten

#### JBoss® EAP 6.3.0/6.4.0 {#jboss-eap}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**Vorbereiten des JBoss®-Servers**

Legen Sie Memory-Argumente in Ihrer conf-Datei fest (z. B. `standalone.conf`)

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Wenn Sie den Bereitstellungsscanner verwenden, um die AEM Webanwendung zu installieren, kann es sinnvoll sein, die `deployment-timeout,` für die `deployment-timeout` -Attribut in der XML-Datei Ihrer Instanz (z. B. `configuration/standalone.xml)`:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM Webanwendung in Ihre JBoss® Administration Console hoch.

* Aktivieren Sie die AEM-Webanwendung.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

Hierbei wird ein einfaches Server-Layout mit nur einem Admin-Server verwendet.

**WebLogic Server-Vorbereitung**

* Fügen Sie in `${myDomain}/config/config.xml` Folgendes zum Abschnitt „security-configuration“ hinzu:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` – auf [https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) finden Sie die richtige Position (standardmäßig ist es in Ordnung, die Positionierung am Ende des Abschnitts vorzunehmen).

* Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

   * open `${myDomain}/bin/setDomainEnv.cmd` (bzw. .sh) Suchen Sie nach WLS_MEM_ARGS, legen Sie beispielsweise `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m`
   * Starten Sie WebLogic Server neu.

* Erstellen Sie unter `${myDomain}` einen Ordner „packages“ und darin einen Ordner „cq“ mit einem Ordner „Plan“.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Legen Sie die AEM-WAR-Datei im Ordner „${myDomain}/packages/cq“ ab.
* Nehmen Sie bei Bedarf Konfigurationen in `WEB-INF/web.xml` vor (siehe oben unter „Allgemeine Beschreibung“).

   * Entpacken Sie die Datei `WEB-INF/web.xml`.
   * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
   * Entfernen Sie die Kommentarzeichen für den anfänglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest (siehe „Allgemeine Beschreibung“).
   * Packen Sie die Datei „web.xml“ erneut.

* Bereitstellen der AEM-WAR-Datei als Anwendung (für die anderen Einstellungen verwenden Sie die Standardeinstellungen)
* Die Installation kann einige Zeit dauern...
* Vergewissern Sie sich, dass die Installation wie oben in der allgemeinen Beschreibung beschrieben abgeschlossen ist (z. B. durch Aufrufen der Datei error.log).
* Sie können den Kontextstamm auf der Konfigurationsregisterkarte der Webanwendung in der WebLogic-`/console` ändern.

#### Tomcat 8/8.5 {#tomcat}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

* **Tomcat-Servervorbereitung**

   * Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

      * In `bin/catalina.bat` (resp `catalina.sh` Fügen Sie unter UNIX® die folgende Einstellung hinzu:
      * `set "JAVA_OPTS= -Xmx2048m`

   * Tomcat ermöglicht bei der Installation keinen Admin- oder Manager-Zugriff. Daher müssen Sie die `tomcat-users.xml` um Zugriff auf diese Konten zu gewähren:

      * Bearbeiten Sie `tomcat-users.xml`, um den Zugriff für Admin und Managerin bzw. Manager einzuschließen. Die Konfiguration sollte dem folgenden Beispiel ähneln:

        ```xml
        <?xml version='1.0' encoding='utf-8'?>
        <tomcat-users>
        role rolename="manager"/>
        role rolename="tomcat"/>
        <role rolename="admin"/>
        <role rolename="role1"/>
        <role rolename="manager-gui"/>
        <user username="both" password="tomcat" roles="tomcat,role1"/>
        <user username="tomcat" password="tomcat" roles="tomcat"/>
        <user username="admin" password="admin" roles="admin,manager-gui"/>
        <user username="role1" password="tomcat" roles="role1"/>
        </tomcat-users>
        ```

   * Wenn Sie AEM mit dem Kontextstamm &quot;/&quot;bereitstellen möchten, müssen Sie den Kontextstamm der vorhandenen ROOT-Webanwendung ändern:

      * Stoppen und Aufheben der Bereitstellung der ROOT-Webapp
      * Umbenennen des Ordners &quot;ROOT.war&quot;im Ordner &quot;webapps&quot;von Tomcat
      * Webapp erneut starten

   * Wenn Sie die AEM-Web-Anwendung mithilfe der manager-gui installieren, müssen Sie die maximale Größe einer hochgeladenen Datei erhöhen, da die Standardeinstellung nur eine Upload-Größe von 50 MB zulässt. Öffnen Sie dafür die Datei „web.xml“ der Manager-Webanwendung

     `webapps/manager/WEB-INF/web.xml`

     und erhöhen Sie die maximale Dateigröße und die maximale Anforderungsgröße auf mindestens 500 MB, siehe Folgendes `multipart-config` Beispiel eines solchen `web.xml` -Datei.

     ```xml
     <multipart-config>
     <!-- 500MB max -->
     <max-file-size>524288000</max-file-size>
     <max-request-size>524288000</max-request-size>
     <file-size-threshold>0</file-size-threshold>
     </multipart-config>
     ```

* **Bereitstellung der AEM-Webanwendung**

   * Laden Sie die AEM-WAR-Datei herunter.
   * Nehmen Sie bei Bedarf Konfigurationen in web.xml vor (siehe oben in der allgemeinen Beschreibung).

      * Entpacken Sie die Datei „WEB-INF/web.xml“.
      * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
      * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
      * Packen Sie die Datei „web.xml“ erneut.

   * Benennen Sie AEM WAR-Datei in ROOT.war um, wenn Sie sie als Root-Webapp bereitstellen möchten. Benennen Sie sie beispielsweise in aemauthor.war um, wenn Sie aemauthor als Kontextstamm verwenden möchten.
   * Kopieren Sie es in den Ordner webapps von Tomcat.
   * warten, bis AEM installiert ist

## Fehlerbehebung {#troubleshooting}

Informationen zum Umgang mit Problemen, die während der Installation auftreten können, finden Sie unter:

* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
