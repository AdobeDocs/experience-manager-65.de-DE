---
title: Anwendungsserver-Installation
seo-title: Anwendungsserver-Installation
description: Erfahren Sie, wie Sie AEM auf einem Anwendungsserver installieren können.
seo-description: Erfahren Sie, wie Sie AEM auf einem Anwendungsserver installieren können.
uuid: c9571f80-6ed1-46fe-b7c3-946658dfc3f4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6fdce35d-2709-41cc-87fb-27a4b867e960
exl-id: 3a90f1d2-e53f-4cc4-8122-024ad6500de0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 66%

---

# Anwendungsserver-Installation{#application-server-install}

>[!NOTE]
>
>`JAR` und `WAR` sind die Dateitypen, in denen AEM veröffentlicht wird. Diese Formate unterliegen einer Qualitätssicherung, mit der die von Adobe zugesicherten Supportstufen sichergestellt werden.


In diesem Abschnitt erfahren Sie, wie Sie Adobe Experience Manager (AEM) mit einem Anwendungsserver installieren. Lesen Sie den Abschnitt [Unterstützte Plattformen](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers), um die spezifischen Unterstützungsebenen anzuzeigen, die für die einzelnen Anwendungsserver bereitgestellt werden.

Es werden die Installationsschritte der folgenden Anwendungsserver beschrieben:

* [WebSphere 8.5](#websphere)
* [JBoss EAP 6.3.0/6.4.0](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Lesen Sie die entsprechende Anwendungsserverdokumentation, um weitere Informationen über das Installieren von Webanwendungen, Serverkonfigurationen und darüber zu erhalten, wie der Server gestartet und angehalten wird.

>[!NOTE]
>
>Wenn Sie Dynamic Media in einer WAR-Bereitstellung verwenden, lesen Sie die [Dynamic Media-Dokumentation](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Allgemeine Beschreibung {#general-description}

### Standardverhalten bei der Installation von AEM in einem Anwendungsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wird als eine einzelne bereitzustellende WAR-Datei geliefert.

Nach der Bereitstellung erfolgt standardmäßig Folgendes:

* Der Ausführungsmodus lautet `author` .
* die Instanz (Repository, Felix OSGI-Umgebung, Bundles usw.) wird in `${user.dir}/crx-quickstart`installiert, wobei `${user.dir}` das aktuelle Arbeitsverzeichnis ist, dieser Pfad zu crx-quickstart heißt `sling.home`

* Der Kontextstamm ist der Name der WAR-Datei, z. B. : `aem-6`

#### Konfiguration {#configuration}

Sie können das Standardverhalten wie folgt ändern:

* Ausführungsmodus: Konfigurieren Sie den Parameter `sling.run.modes` in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* : Konfigurieren Sie den Parameter `sling.home`sling.home in der Datei `WEB-INF/web.xml` der AEM-WAR-Datei vor der Bereitstellung.

* Kontextstamm: Benennen Sie die AEM-WAR-Datei um.

#### Installationsveröffentlichung {#publish-installation}

Um eine Veröffentlichungsinstanz bereitzustellen, müssen Sie den Ausführungsmodus auf „publish“ (veröffentlichen) festlegen:

* Entpacken Sie die Datei „WEB-INF/web.xml“ aus der AEM-WAR-Datei.
* Ändern Sie den Parameter „sling.run.modes“ zu „publish“ (veröffentlichen).
* Packen Sie die Datei „web.xml“ erneut in die AEM-WAR-Datei.
* Stellen Sie die AEM-WAR-Datei bereit.

#### Installationsüberprüfung {#installation-check}

Um zu überprüfen, ob alles installiert ist, haben Sie folgende Möglichkeiten:

* Untersuchen der Datei `error.log`, um anzuzeigen, ob der gesamte Inhalt installiert ist.
* Suchen Sie in `/system/console` , ob alle Pakete installiert sind.

#### Zwei Instanzen desselben Anwendungsservers {#two-instances-on-the-same-application-server}

Zu Demonstrationszwecken kann es angemessen sein, die Erstellungs- und Veröffentlichungsinstanzen auf einem Anwendungsserver zu installieren. Dafür müssen Sie wie folgt vorgehen:

1. Ändern Sie die Variablen sling.home und sling.run.modes der Veröffentlichungsinstanz.
1. Entpacken Sie die Datei WEB-INF/web.xml aus der AEM WAR-Datei.
1. Ändern Sie den Parameter „sling.home“ in einen anderen Pfad (absolute und relative Pfade sind möglich).
1. Ändern Sie sling.run.modes in Veröffentlichungsinstanz.
1. Replizieren Sie die Datei &quot;web.xml&quot;.
1. Benennen Sie die WAR-Dateien um, sodass sie unterschiedliche Namen haben: Beispiel: Eine Umbenennung erfolgt in aemauthor.war und die andere in aempublish.war.
1. Verwenden Sie höhere Speichereinstellungen, z. B. für Standard-AEM-Instanzen, z. B.: -Xmx3072m
1. Stellen Sie die beiden Webanwendungen bereit.
1. Halten Sie nach der Bereitstellung die zwei Webanwendungen an.
1. Sowohl in der Autoren- als auch in der Veröffentlichungsinstanz stellen Sie sicher, dass in den sling.properties-Dateien die Eigenschaft felix.service.urlhandlers=false auf false festgelegt ist (standardmäßig ist true festgelegt).
1. Starten Sie die zwei Webanwendungen erneut.

## Installationsverfahren für Anwendungsserver  {#application-servers-installation-procedures}

### WebSphere 8.5 {#websphere}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**Servervorbereitung**

* Lassen Sie Standardauthentifizierungsheader durchlaufen:

   * Eine Möglichkeit für die Authentifizierung eines Benutzers durch AEM besteht in der Deaktivierung der globalen Verwaltungssicherheit des WebSphere-Servers. Wechseln Sie dafür zu „Security“ > „Global Security“ und deaktivieren Sie das Kontrollkästchen „Enable administrative security“. Speichern Sie den Vorgang und starten Sie den Server neu.

* set `"JAVA_OPTS= -Xmx2048m"`
* Wenn Sie AEM mithilfe des Kontextstamms =/ installieren möchten, müssen Sie zunächst den Kontextstamm der vorhandenen standardmäßigen Webanwendung ändern.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Nehmen Sie bei Bedarf Konfigurationen in der Datei „web.xml“ vor (siehe oben unter „Allgemeine Beschreibung“).

   * WEB-INF/web.xml Datei entpacken
   * Parameter sling.run.modes zum Veröffentlichen ändern
   * Entfernen Sie den Kommentar für den anfänglichen Parameter sling.home und legen Sie diesen Pfad nach Bedarf fest.
   * Datei &quot;web.xml&quot;replizieren

* Stellen Sie die AEM-WAR-Datei bereit.

   * Wählen Sie einen Kontextstamm. (Wenn Sie den Parameter „sling.run.modes“ festlegen möchten, müssen Sie die ausführlichen Schritte des Bereitstellungsassistenten durchführen und dann den Parameter in Schritt 6 des Assistenten angeben.)

* Starten Sie die AEM-Webanwendung.

#### JBoss EAP 6.3.0/6.4.0  {#jboss-eap}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

**JBoss-Servervorbereitung**

Legen Sie Speicherargumente in Ihrer conf-Datei fest (z. B. `standalone.conf`)

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Wenn Sie den Bereitstellungsscanner für die Installation der AEM Webanwendung verwenden, kann es sinnvoll sein, das `deployment-timeout,` für dieses Attribut zu erhöhen, indem Sie ein `deployment-timeout` -Attribut in der XML-Datei Ihrer Instanz festlegen (z. B. `configuration/standalone.xml)`:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-Webanwendung in Ihre JBoss-Verwaltungskonsole hoch.

* Aktivieren Sie die AEM-Webanwendung.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

Hierbei wird ein einfaches Serverlayout mit nur einem Administratorserver verwendet.

**WebLogic-Servervorbereitung**

* Fügen Sie in `${myDomain}/config/config.xml`zum Abschnitt &quot;security-configuration&quot;hinzu:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` die richtige Position auf  [https://xmlns.oracle.com/weblogic/domain/1.0/domain.](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) xsdsdf anzeigen (standardmäßig ist es ok, sie am Ende des Abschnitts zu positionieren)

* Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

   * Öffnen Sie `${myDomain}/bin/setDomainEnv.cmd` (bzw. .sh) die Suche nach WLS_MEM_ARGS, setzen Sie z. B. `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m`
   * WebLogic Server neu starten

* Erstellen Sie in `${myDomain}` einen Paketordner und in einem cq-Ordner und darin einen Planordner.

**Bereitstellung der AEM-Webanwendung**

* Laden Sie die AEM-WAR-Datei herunter.
* Platzieren Sie die AEM WAR-Datei in den Ordner ${myDomain}/packages/cq .
* Nehmen Sie bei Bedarf Ihre Konfigurationen in `WEB-INF/web.xml` vor (siehe oben in der allgemeinen Beschreibung).

   * Entpacken Sie die Datei `WEB-INF/web.xml`a
   * Parameter sling.run.modes zum Veröffentlichen ändern
   * Entfernen Sie den Kommentar für den anfänglichen Parameter sling.home und legen Sie diesen Pfad nach Bedarf fest (siehe Allgemeine Beschreibung).
   * Datei &quot;web.xml&quot;replizieren

* Stellen Sie die AEM-WAR-Datei als eine Anwendung bereit (verwenden Sie für andere Einstellungen die Standardeinstellungen).
* Die Installation kann einige Zeit dauern.
* Überprüfen Sie, ob die Installation wie oben unter „Allgemeine Beschreibung“ beschrieben abgeschlossen wurde (beispielsweise durch Untersuchen der Datei „error.log“).
* Sie können den Kontextstamm auf der Registerkarte &quot;Konfiguration&quot;der Webanwendung in der WebLogic `/console` ändern

#### Tomcat 8/8.5 {#tomcat}

Lesen Sie oben [Allgemeine Beschreibung](#general-description), bevor Sie eine Bereitstellung vornehmen.

* **Tomcat-Servervorbereitung**

   * Erhöhen Sie den für die virtuelle Maschine eingestellten Arbeitsspeicherwert:

      * Fügen Sie in `bin/catalina.bat` (bzw. `catalina.sh` unter Unix) die folgende Einstellung hinzu:
      * `set "JAVA_OPTS= -Xmx2048m`
   * Tomcat ermöglicht weder dem Administrator noch dem Manager bei der Installation den Zugriff. Daher müssen Sie `tomcat-users.xml` manuell bearbeiten, um den Zugriff für diese Konten zuzulassen:

      * Bearbeiten Sie `tomcat-users.xml`, um den Zugriff für Administrator und Manager einzuschließen. Die Konfiguration sollte dem folgenden Beispiel ähneln:

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
   * Wenn Sie AEM mit dem Kontextstamm „/“ bereitstellen möchten, müssen Sie den Kontextstamm der vorhandenen „ROOT webapp“ ändern:

      * Halten Sie „ROOT webapp“ an und heben Sie ihre Bereitstellung auf.
      * Benennen Sie den Ordner „ROOT.war“ in den Ordner „webapps“ von Tomcat um.
      * Starten Sie webapp erneut.
   * Wenn Sie die AEM-Webanwendung mithilfe der manager-gui installieren, müssen Sie die maximale Größe einer hochgeladenen Datei erhöhen, da die Standardeinstellung nur eine Uploadgröße von 50 MB zulässt. Öffnen Sie dazu die Datei web.xml der Manager-Webanwendung,

      `webapps/manager/WEB-INF/web.xml`

      und erhöhen Sie „max-file-size“ und „max-request-size“ auf mindestens „500 MB“. Im folgenden `multipart-config`-Beispiel finden Sie eine derartige `web.xml`-Datei.

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
   * Nehmen Sie bei Bedarf Konfigurationen in der Datei „web.xml“ vor (siehe oben unter „Allgemeine Beschreibung“).

      * WEB-INF/web.xml Datei entpacken
      * Parameter sling.run.modes zum Veröffentlichen ändern
      * Entfernen Sie den Kommentar für den anfänglichen Parameter sling.home und legen Sie diesen Pfad nach Bedarf fest.
      * Datei &quot;web.xml&quot;replizieren
   * Benennen Sie die AEM-WAR-Datei in „ROOT.war“ um, wenn Sie sie als „ROOT webapp“ bereitstellen möchten. Benennen Sie sie beispielsweise in „aemauthor.war“ um, wenn „aemauthor“ als Kontextstamm fungieren soll.
   * Kopieren Sie sie in den Ordner „webapps“ von Tomcat.
   * Warten Sie, bis AEM installiert wurde.


## Fehlerbehebung {#troubleshooting}

Informationen zur Behebung von Problemen, die bei der Installation möglicherweise auftreten, finden Sie unter:

* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
