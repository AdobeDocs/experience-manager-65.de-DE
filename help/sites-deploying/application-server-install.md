---
title: Installation des Anwendungs-Servers
description: Erfahren Sie, wie Sie Adobe Experience Manager mit einem Anwendungs-Server installieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 3a90f1d2-e53f-4cc4-8122-024ad6500de0
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 98%

---

# Installation des Anwendungs-Servers{#application-server-install}

>[!NOTE]
>
>`JAR` und `WAR` sind die Dateitypen, in denen Adobe Experience Manager (AEM) veröffentlicht wird. Diese Formate unterliegen einer Qualitätssicherung, mit der die von Adobe zugesicherten Unterstützungsebenen sichergestellt werden.
>

In diesem Abschnitt erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit einem Anwendungs-Server installieren. Lesen Sie den Abschnitt [Unterstützte Plattformen](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers), um mehr über die spezifischen Unterstützungsebenen für die einzelnen Anwendungs-Server zu erfahren.

Es werden die Installationsschritte der folgenden Anwendungs-Server beschrieben:

* [WebSphere](#websphere)
* [JBoss](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Lesen Sie die entsprechende Anwendungsserverdokumentation, um weitere Informationen über das Installieren von Webanwendungen, Serverkonfigurationen und darüber zu erhalten, wie der Server gestartet und angehalten wird.

>[!NOTE]
>
>Wenn Sie Dynamic Media in einer WAR-Bereitstellung verwenden, finden Sie in der [Dokumentation zu Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media) weitere Informationen dazu.

## Allgemeine Beschreibung {#general-description}

### Standardverhalten beim Installieren von AEM auf einem Anwendungsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wird als eine einzelne bereitzustellende WAR-Datei geliefert.

Nach der Bereitstellung geschieht standardmäßig Folgendes:

* Der Ausführungsmodus lautet `author`.
* Die Instanz (Repository, Felix OSGI-Umgebung, Bundles usw.) wird in `${user.dir}/crx-quickstart` installiert, wobei `${user.dir}` das aktuelle Arbeitsverzeichnis ist. Dieser Pfad zu „crx-quickstart“ wird als `sling.home` bezeichnet.

* Der Kontextstamm ist der Name der WAR-Datei, z. B. `aem-6`.

#### Konfiguration {#configuration}

Sie können das Standardverhalten wie folgt ändern:

* Ausführungsmodus: Konfigurieren Sie den Parameter `sling.run.modes` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* sling.home: Konfigurieren Sie den Parameter `sling.home` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* Kontextstamm: Benennen Sie die AEM-WAR-Datei um.

#### Installationsveröffentlichung {#publish-installation}

Um eine Veröffentlichungsinstanz bereitzustellen, müssen Sie den Ausführungsmodus auf „publish“ (veröffentlichen) festlegen:

* Entpacken Sie die WEB-INF/web.xml-Datei aus der AEM-WAR-Datei.
* Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
* Packen Sie die Datei „web.xml“ erneut in die AEM-WAR-Datei.
* Stellen Sie die AEM-WAR-Datei bereit.

#### Installationsprüfung {#installation-check}

Um zu überprüfen, ob alles installiert ist, haben Sie folgende Möglichkeiten:

* Untersuchen der Datei `error.log`, um anzuzeigen, ob der gesamte Inhalt installiert ist.
* Überprüfen in `/system/console`, ob alle Bundles installiert sind

#### Zwei Instanzen auf demselben Anwendungs-Server {#two-instances-on-the-same-application-server}

Zu Demonstrationszwecken kann es sinnvoll sein, die Autoren- und Veröffentlichungsinstanzen auf einem selben Anwendungs-Server zu installieren. Gehen Sie dazu wie folgt vor:

1. Ändern Sie die Variablen „sling.home“ und „sling.run.modes“ der Veröffentlichungsinstanz.
1. Entpacken Sie die Datei „WEB-INF/web.xml“ aus der AEM-WAR-Datei.
1. Ändern Sie den Parameter „sling.home“ in einen anderen Pfad (absolute und relative Pfade sind möglich).
1. Ändern Sie „sling.run.modes“ für die Veröffentlichungsinstanz in „publish“ (veröffentlichen).
1. Packen Sie die Datei „web.xml“ erneut.
1. Benennen Sie die WAR-Dateien um, damit sie verschiedene Namen aufweisen. So können Sie eine beispielsweise in „aemauthor.war“ und die andere in „aempublish.war“ umbenennen.
1. Verwenden Sie die Einstellungen für den höheren Arbeitsspeicher. Beispielsweise verwenden AEM-Standardinstanzen `-Xmx3072m`.
1. Stellen Sie die beiden Web-Anwendungen bereit.
1. Stoppen Sie nach der Bereitstellung die zwei Web-Anwendungen.
1. Stellen Sie in den Erstellungs- und Veröffentlichungsinstanzen sicher, dass in den „sling.properties“-Dateien die Eigenschaft „felix.service.urlhandlers=false“ auf „false“ festgelegt ist (standardmäßig ist der Wert auf „true“ gesetzt).
1. Starten Sie die zwei Web-Anwendungen erneut.

## Installationsverfahren für Anwendungs-Server {#application-servers-installation-procedures}

### WebSphere® 8.5 {#websphere}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**Vorbereitung des Servers**

* So lassen Sie Standard-Authentifizierungs-Header durchlaufen:

   * Eine Möglichkeit für die Authentifizierung von Benutzenden durch AEM besteht in der Deaktivierung der globalen Verwaltungssicherheit des WebSphere®-Servers. Wechseln Sie dafür zu „Sicherheit“ > „Globale Sicherheit“ und deaktivieren Sie das Kontrollkästchen „Verwaltungssicherheit aktivieren“. Speichern Sie den Vorgang und starten Sie den Server neu.

* `"JAVA_OPTS= -Xmx2048m"` festlegen
* Wenn Sie AEM mithilfe des Kontextstamms = / installieren möchten, ändern Sie den Kontextstamm der vorhandenen standardmäßigen Web-Anwendung.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Nehmen Sie bei Bedarf Ihre Konfigurationen in der Datei „web.xml“ vor (siehe oben unter „Allgemeine Beschreibung“).

   * Entpacken Sie die Datei „WEB-INF/web.xml“.
   * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
   * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
   * Packen Sie die Datei „web.xml“ erneut.

* Bereitstellen der AEM-WAR-Datei

   * Wählen Sie einen Kontextstamm. (Wenn Sie „sling.run.modes“ festlegen möchten, müssen Sie die ausführlichen Schritte des Bereitstellungsassistenten durchführen und dann die Angabe in Schritt 6 des Assistenten vornehmen.)

* Starten der AEM-Web-Anwendung

#### JBoss® EAP 6.3.0/6.4.0 {#jboss-eap}

Lesen Sie die [allgemeine Beschreibung](#general-description) oben, bevor Sie eine Bereitstellung vornehmen.

**Vorbereiten des JBoss®-Servers**

Legen Sie die „Memory“-Argumente in Ihrer Konfigurationsdatei (z. B. `standalone.conf`) fest.

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Wenn Sie die Bereitstellungsüberprüfung zum Installieren der AEM-Web-Anwendung verwenden, empfiehlt es sich möglicherweise, den Wert für `deployment-timeout,` zu erhöhen. Legen Sie dafür das Attribut `deployment-timeout` in der XML-Datei Ihrer Instanz (z. B. `configuration/standalone.xml)`) fest:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**Bereitstellung der AEM-Web-Anwendung**

* Laden Sie die AEM-Web-Anwendung in Ihre JBoss®-Administrationskonsole hoch.

* Aktivieren Sie die AEM-Webanwendung.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

Hierbei wird ein einfaches Server-Layout mit nur einem Administrator-Server verwendet.

**Vorbereitung des WebLogic-Servers**

* Fügen Sie in `${myDomain}/config/config.xml` Folgendes zum Abschnitt „security-configuration“ hinzu:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` – auf [https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) finden Sie die richtige Position (standardmäßig ist es in Ordnung, die Positionierung am Ende des Abschnitts vorzunehmen).

* Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

   * Öffnen Sie `${myDomain}/bin/setDomainEnv.cmd` (bzw. .sh). Suchen Sie nach „WLS_MEM_ARGS“ und legen Sie z. B. `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m` fest.
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

* AEM-WAR-Datei als Anwendung bereitstellen (für die anderen Einstellungen die Standardeinstellungen verwenden)
* Die Installation kann einige Zeit dauern …
* Überprüfen Sie, ob die Installation wie oben unter „Allgemeine Beschreibung“ abgeschlossen wurde (beispielsweise durch Untersuchen der Datei „error.log“).
* Sie können den Kontextstamm auf der Konfigurationsregisterkarte der Webanwendung in der WebLogic-`/console` ändern.

#### Tomcat 8/8.5 {#tomcat}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

* **Tomcat-Servervorbereitung**

   * Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

      * Fügen Sie in `bin/catalina.bat` (bzw. `catalina.sh` unter UNIX®) die folgende Einstellung hinzu:
      * `set "JAVA_OPTS= -Xmx2048m`

   * Tomcat ermöglicht weder Admin- noch Manager-Zugriff bei der Installation. Daher müssen Sie `tomcat-users.xml` manuell bearbeiten, um den Zugriff für diese Konten zuzulassen:

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

   * Wenn Sie AEM mit dem Kontextstamm „/“ bereitstellen möchten, müssen Sie den Kontextstamm der vorhandenen „ROOT webapp“ (Stamm-Web-Anwendung) ändern:

      * Stoppen Sie „ROOT webapp“ und heben Sie ihre Bereitstellung auf.
      * Benennen Sie den Ordner „ROOT.war“ in den Tomcat-Ordner „webapps“ um.
      * Starten Sie webapp erneut.

   * Wenn Sie die AEM-Web-Anwendung mithilfe der manager-gui installieren, müssen Sie die maximale Größe einer hochgeladenen Datei erhöhen, da die Standardeinstellung nur eine Upload-Größe von 50 MB zulässt. Öffnen Sie dafür die Datei „web.xml“ der Manager-Webanwendung

     `webapps/manager/WEB-INF/web.xml`

     Erhöhen Sie dann „max-file-size“ und „max-request-size“ auf mindestens 500 MB. Im folgenden Beispiel für `multipart-config` finden Sie eine derartige `web.xml`-Datei.

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
   * Nehmen Sie bei Bedarf Ihre Konfigurationen in der Datei „web.xml“ vor (siehe oben unter „Allgemeine Beschreibung“).

      * Entpacken Sie die Datei „WEB-INF/web.xml“.
      * Ändern Sie den Parameter „sling.run.modes“ in „publish“ (veröffentlichen).
      * Entfernen Sie die Kommentarzeichen für den ursprünglichen Parameter „sling.home“ und legen Sie diesen Pfad nach Bedarf fest.
      * Packen Sie die Datei „web.xml“ erneut.

   * Benennen Sie die AEM-WAR-Datei in „ROOT.war“ um, wenn Sie sie als „root webapp“ bereitstellen möchten. Benennen Sie sie beispielsweise in „aemauthor.war“ um, wenn „aemauthor“ als Kontextstamm fungieren soll.
   * Kopieren Sie sie in den Tomcat-Ordner „webapps“.
   * Warten Sie, bis AEM installiert ist.

## Fehlerbehebung {#troubleshooting}

Informationen zur Behebung von Problemen, die möglicherweise bei der Installation auftreten, finden Sie unter:

* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
