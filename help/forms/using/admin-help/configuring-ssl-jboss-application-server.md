---
title: Konfigurieren von SSL für JBoss Application Server
description: Hier finden Sie Informationen dazu, wie Sie SSL für den JBoss-Anwendungs-Server konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 8eb4f691-a66b-498e-8114-307221f63718
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '904'
ht-degree: 100%

---

# Konfigurieren von SSL für JBoss Application Server {#configuring-ssl-for-jboss-application-server}

Zum Konfigurieren von SSL auf dem JBoss-Anwendungs-Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool zum Erstellen einer Berechtigung oder zum Anfordern und Importieren einer Berechtigung von einer Zertifizierungsstelle verwenden. Aktivieren Sie anschließend SSL unter JBoss.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Keystore erforderlichen Informationen enthält.

In diesem Verfahren gilt:

* `[appserver root]` ist der Basisordner des Anwendungs-Servers, auf dem AEM Forms ausgeführt wird.
* `[type]` ist ein Ordnername, der von der von Ihnen ausgeführten Installation abhängig ist.

## SSL-Berechtigung erstellen {#create-an-ssl-credential}

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*[JAVA HOME]*/bin“ und geben Sie den folgenden Befehl ein, um die Berechtigung und den Keystore zu erstellen:

   `keytool -genkey -dname "CN=`*Host-Name* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Stadt* `, S=`*Bundesland* `, C=`Ländercode `-alias "AEMForms Cert"` `-keyalg RSA -keypass`*Schlüssel_passwort* `-keystore`*Keystore-Name* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte. Der Hostname ist der voll qualifizierte Domain-Name des Anwendungsservers.

1. Geben Sie das `keystore_password` ein, wenn Sie zur Eingabe eines Passworts aufgefordert werden. Das Kennwort für den Keystore und der Schlüssel müssen identisch sein.

   >[!NOTE]
   >
   >Das in diesem Schritt eingegebene `keystore_password` *kann dem in Schritt 1 eingegebenen Passwort (Schlüssel-Passwort) entsprechen oder anders lauten.*

1. Kopieren Sie „*Keystore-Name*.keystore“ durch Eingabe eines der folgenden Befehle in den Ordner `[appserver root]/server/[type]/conf`:

   * (Windows-Einzel-Server) `copy` `keystorename.keystore[appserver root]\standalone\configuration`
   * (Windows Servercluster) Koporieren Sie `keystorename.keystore[appserver root]\domain\configuration`
   * (Linux-Einzel-Server) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Linux-Servercluster) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exportieren Sie die Zertifikatdatei durch Eingabe des folgenden Befehls:

   * (Einzel-Server) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Servercluster) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Geben Sie das *keystore_Kennwort* ein, wenn Sie zur Eingabe eines Kennworts aufgefordert werden.
1. Kopieren Sie die Datei „AEMForms_cert.cer“ durch Eingabe des folgenden Befehls in den Ordner „*[Anwendungs-Server-Stammordner]\conf*“:

   * (Windows-Einzel-Server) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Windows Servercluster) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Linux-Einzel-Server) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Linux-Servercluster) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Zeigen Sie den Inhalt des Zertifikats durch Eingabe des folgenden Befehls an:

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. Um ggf. Schreibzugriff auf die Datei „cacerts“ in `[JAVA_HOME]\jre\lib\security` zu ermöglichen, führen Sie die folgende Aufgabe aus:

   * (Windows) Klicken Sie mit der rechten Maustaste auf die Datei „cacerts“, wählen Sie „Eigenschaften“ und deaktivieren Sie das Attribut „Schreibgeschützt“.
   * (Linux) Typ `chmod 777 cacerts`

1. Importieren Sie das Zertifikat durch Eingabe des folgenden Befehls:

   `keytool -import -alias "AEMForms Cert" -file`*AEMForms_cert* `.cer -keystore`*JAVA_HOME* `\jre\lib\security\cacerts`

1. Geben Sie `changeit` als Passwort ein. Dieses Kennwort ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
1. Wird die Eingabeaufforderung `Trust this certificate? [no]` angezeigt, geben Sie `yes` ein. Daraufhin wird die Bestätigung „Certificate was added to keystore“ angezeigt.
1. Installieren Sie das Zertifikat auf dem Workbench-Computer, wenn Sie die Verbindung über SSL von Workbench aus herstellen.
1. Öffnen Sie in einem Texteditor die folgende Dateien zur Bearbeitung:

   * Einzel-Server – `[appserver root]`/standalone/configuration/lc_&lt;dbname/turnkey>.xml

   * Servercluster – `[appserver root]`/domain/configuration/host.xml

   * Servercluster – `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. &#x200B;
   * **Für Einzelserver** Fügen Sie in der Datei „lc_&lt;dbaname/tunkey>.xml“ Folgendes nach dem Abschnitt „&lt;security-realms>“ ein:

   ```xml
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMformsCert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Suchen Sie den Abschnitt `<server>`, der sich im Anschluss an folgendem Code befindet:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```xml
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * Fügen Sie **für Servercluster** in „[Anwendungs-Server-Stammordner]\domain\configuration\host.xml“ auf allen Knoten den Abschnitt &lt;security-realms> hinzu:

   ```xml
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Suchen Sie auf dem Hauptknoten des Serverclusters in „[Anwendungs-Server-Stammordner]\domain\configuration\domain_&lt;dbname>.xml“ den Abschnitt &lt;server>, der nach dem folgenden Code steht:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```xml
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

1. Ändern Sie die Werte für die Attribute `keystoreFile` und `keystorePass` in das Keystore-Kennwort, das Sie beim Erstellen des Keystore festgelegt haben.
1. So starten Sie den Anwendungs-Server neu:

   * Für Turnkey-Installationen:

      * Klicken Sie in der Windows-Systemsteuerung Panel auf „Verwaltung“ und dann auf „Dienste“.
      * Wählen Sie JBoss für Adobe Experience Manager-Formulare.
      * Wählen Sie „Aktion“ > „Anhalten“.
      * Warten Sie, bis als Status des Dienstes „Angehalten“ angezeigt wird.
      * Wählen Sie „Aktion“ > „Starten“.

   * Für von Adobe vorkonfigurierte oder manuell konfigurierte JBoss-Installationen:

      * Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[appserver root]`*/bin“.
      * Beenden Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`

      * Warten Sie, bis der JBoss-Prozess vollständig heruntergefahren wurde. (Dies ist der Fall, wenn der JBoss-Prozess die Kontrolle wieder an das Terminal übergibt, in dem er gestartet wurde.)
      * Starten Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`

1. Um mithilfe von SSL auf Administration Console zuzugreifen, geben Sie `https://[host name]:'port'/adminui` in einem Webbrowser ein:

   Der SSL-Standard-Port für JBoss ist 8443.  Geben Sie von hier an beim Zugriff auf AEM Forms diesen Port an.

## Anfordern einer Berechtigung von einer Zertifizierungsstelle {#request-a-credential-from-a-ca}

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*[JAVA HOME]*/bin“ und geben Sie den folgenden Befehl ein, um den Keystore und den Schlüssel zu erstellen:

   `keytool -genkey -dname "CN=`*Host-Name* `, OU=`*Gruppenname* `, O=`*Firmenname* `, L=`*Stadt* `, S=`*Bundesland* `, C=`*Ländercode* `-alias "AEMForms Cert"` `-keyalg RSA -keypass`-*Schlüssel-Passwort* `-keystore`*Keystore-Name* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.

1. Geben Sie den folgenden Befehl ein, um eine Zertifikatanforderung an die Zertifizierungsstelle zu erzeugen:

   `keytool -certreq -alias` „AEMForms Cert“ `-keystore`*Keystore-Name* `.keystore -file`*AEMFormscertRequest.csr*

1. Wenn Ihre Anforderung einer Zertifikatsdatei erfüllt wurde, führen Sie die Schritte im nächsten Verfahren durch.

## Verwenden einer Berechtigung von einer Zertifizierungsstelle zum Aktivieren von SSL {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[JAVA HOME]`*/bin“ und geben Sie den folgenden Befehl ein, um das Stammzertifikat der Zertifizierungsstelle, mit dem die CSR-Datei signiert wurde, zu importieren:

   `keytool -import -trustcacerts -file` rootcert.pem -Keystore` keystorename.keystore -alias root`

   Wenn sich das Stammzertifikat nicht im Browser befindet, importieren Sie es ebenfalls dorthin.

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[JAVA HOME]`*/bin“ und geben Sie den folgenden Befehl ein, um die Berechtigung in den Keystore zu importieren:

   `keytool -import -trustcacerts -file`*CACertificateName* `.crt -keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >* Ersetzen Sie `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.
   >* Das importierte, von der Zertifizierungsstelle signierte Zertifikat ersetzt ein selbst signiertes Zertifikat (sofern vorhanden).

1. Führen Sie die Schritte 13 bis 18 im Abschnitt „Erstellen einer SSL-Berechtigung“ durch.
