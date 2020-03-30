---
title: SSL für JBoss Application Server konfigurieren
seo-title: SSL für JBoss Application Server konfigurieren
description: Erfahren Sie, wie Sie SSL für JBoss Application Server konfigurieren.
seo-description: Erfahren Sie, wie Sie SSL für JBoss Application Server konfigurieren.
uuid: 7c13cf00-ea89-4894-a4fc-aaeec7ae9f66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c187daa4-41b7-47dc-9669-d7120850cafd
translation-type: tm+mt
source-git-commit: e4d84b5c6f7d2bfcac942b0b685a8f1fd11274f0

---


# SSL für JBoss Application Server konfigurieren {#configuring-ssl-for-jboss-application-server}

Zum Konfigurieren von SSL unter JBoss Application Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool zum Erstellen einer Berechtigung oder zum Anfordern und Importieren einer Berechtigung von einer Zertifizierungsstelle verwenden. Anschließend müssen Sie SSL unter JBoss aktivieren.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Keystore erforderlichen Informationen enthält.

In diesem Verfahren gilt:

* `[appserver root]` ist der Basisordner des Anwendungsservers, auf dem AEM Forms ausgeführt wird.
* `[type]` ist ein Ordnername, der je nach der von Ihnen ausgeführten Installation variiert.

## SSL-Berechtigung erstellen {#create-an-ssl-credential}

1. In a command prompt, navigate to *[JAVA HOME]*/bin and type the following command to create the credential and keystore:

   `keytool -genkey -dname "CN=`*Hostname *`, OU=`*Gruppenname* `, O=`*Firma Name *`,L=`*Stadt* `, S=`*Land *`, C=``-alias "AEMForms Cert"``-keyalg RSA -keypass`** `-keystore`**Ländercode&quot;key_passwordkeystorename`.keystore`

   >[!NOTE]
   >
   >Replace `[JAVA_HOME]` with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment. Der Hostname ist der voll qualifizierte Domänenname des Anwendungsservers.

1. Enter the `keystore_password` when prompted for a password. Das Kennwort für den Keystore und der Schlüssel müssen identisch sein.

   >[!NOTE]
   >
   >The `keystore_password` *ntered at this step may be the same password (key_password) that you entered in step 1, or it may be different.*

1. Copy the *keystorename*.keystore to the `[appserver root]/server/[type]/conf` directory by typing one of the following commands:

   * (Windows-Einzelserver) `copy``keystorename.keystore[appserver root]\standalone\configuration`
   * (Windows-Servercluster) copy `keystorename.keystore[appserver root]\domain\configuration`
   * (Linux Einzelserver) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Linux-Servercluster) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exportieren Sie die Zertifikatdatei durch Eingabe des folgenden Befehls:

   * (Einzelserver) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Servercluster) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Geben Sie das *keystore_Kennwort* ein, wenn Sie zur Eingabe eines Kennworts aufgefordert werden.
1. Copy the AEMForms_cert.cer file to the *[appserver root]\conf *directory by typing the following command:

   * (Windows-Einzelserver) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Windows-Servercluster) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Linux Einzelserver) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Linux-Servercluster) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Zeigen Sie den Inhalt des Zertifikats durch Eingabe des folgenden Befehls an:

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. To provide write access to the cacerts file in `[JAVA_HOME]\jre\lib\security`, if required, perform the following task:

   * (Windows) Klicken Sie mit der rechten Maustaste auf die Datei „cacerts“, wählen Sie „Eigenschaften“ und deaktivieren Sie das Attribut „Schreibgeschützt“.
   * (Linux) Typ `chmod 777 cacerts`

1. Importieren Sie das Zertifikat durch Eingabe des folgenden Befehls:

   `keytool -import -alias “AEMForms Cert” -file`*AEMForms_cert *`.cer -keystore`*JAVA_HOME*`\jre\lib\security\cacerts`

1. Type `changeit` as the password. Dieses Kennwort ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
1. Geben Sie bei Aufforderung `Trust this certificate? [no]`: `yes`ein. Daraufhin wird die Bestätigung „Certificate was added to keystore“ angezeigt.
1. Wenn Sie die Verbindung über SSL von Workbench aus herstellen, müssen Sie das Zertifikat auf dem Workbench-Computer installieren.
1. Öffnen Sie in einem Texteditor die folgende Dateien zur Bearbeitung:

   * Single Server - `[appserver root]`/standalone/configuration/lc_&lt;dbname/turnkey>.xml

   * Servercluster - `[appserver root]`/domain/configuration/host.xml

   * Server Cluster - `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. 
   * **Für Einzelserver** Fügen Sie in der Datei „lc_&lt;dbaname/tunkey>.xml“ Folgendes nach dem Abschnitt „&lt;security-realms>“ ein:

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMformsCert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Locate the `<server>` section present after the following code:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * **Fügen Sie für Servercluster** im [Anwendungsserver-Stammordner]\domain\configuration\host.xml auf allen Knoten den folgenden Abschnitt hinzu:

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   On the master node of the Server Cluster, in the [appserver root]\domain\configuration\domain_&lt;dbname>.xml, locate the &lt;server> section present after the following code:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

1. Ändern Sie die Werte für die Attribute `keystoreFile` und `keystorePass` in das Keystore-Kennwort, das Sie beim Erstellen des Keystore festgelegt haben.
1. Starten Sie den Anwendungsserver neu.

   * Für Turnkey-Installationen:

      * Klicken Sie in der Windows-Systemsteuerung auf Verwaltung und dann auf Dienste.
      * Wählen Sie JBoss für Adobe Experience Manager Forms.
      * Wählen Sie Aktion > Anhalten.
      * Warten Sie, bis als Status des Dienstes „Angehalten“ angezeigt wird.
      * Wählen Sie Aktion > Starten.
   * Für von Adobe vorkonfigurierte oder manuell konfigurierte JBoss-Installationen:

      * From a command prompt, navigate to *`[appserver root]`*/bin.
      * Beenden Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`
      * Warten Sie, bis der JBoss-Prozess vollständig heruntergefahren wurde. (Dies ist der Fall, wenn der JBoss-Prozess die Kontrolle wieder an das Terminal übergibt, in dem er gestartet wurde.)
      * Starten Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`



1. Um mit SSL auf Administration Console zuzugreifen, geben Sie `https://[host name]:'port'/adminui` in einen Webbrowser ein:

   Der SSL-Standardanschluss für JBoss ist 8443. Geben Sie von hier an beim Zugriff auf AEM Forms diesen Anschluss an.

## Berechtigung von einer Zertifizierungsstelle anfordern {#request-a-credential-from-a-ca}

1. In a command prompt, navigate to *[JAVA HOME]*/bin and type the following command to create the keystore and the key:

   `keytool -genkey -dname "CN=`*Hostname *`, OU=`*Gruppe Name* `, O=`*Firma Name *`, L=`*Stadt* `, S=`*Land *Code&quot;`, C=`**`-alias "AEMForms Cert"` `-keyalg RSA -keypass`** `-keystore`**-Schlüssel KennwortKeystorename`.keystore`

   >[!NOTE]
   >
   >Replace *`[JAVA_HOME]`* with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment.

1. Geben Sie den folgenden Befehl ein, um eine Zertifikatanforderung an die Zertifizierungsstelle zu erzeugen:

   `keytool -certreq -alias` &quot;AEMForms Cert&quot; `-keystore`*keystorename *`.keystore -file`*AEMFormscertRequest.csr*

1. Wenn Ihre Anforderung einer Zertifikatdatei erfüllt wurde, führen Sie die Schritte im nächsten Verfahren durch.

## Berechtigung von einer Zertifizierungsstelle zum Aktivieren von SSL verwenden {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. In a command prompt, navigate to *`[JAVA HOME]`*/bin and type the following command to import the root certificate of the CA with which the CSR has been signed:

   `keytool -import -trustcacerts -file` rootcert.pem -keystore` keystorename.keystore -alias root`

   Wenn sich das Stammzertifikat nicht im Browser befindet, importieren Sie es ebenfalls dorthin.

   >[!NOTE]
   >
   >Replace *`[JAVA_HOME]`with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment.*

1. In a command prompt, navigate to *`[JAVA HOME]`*/bin and type the following command to import the credential into the keystore:

   `keytool -import -trustcacerts -file`*CACertificateName *`.crt -keystore`*keystorename*`.keystore`

   >[!NOTE]
   >
   >* Replace `[JAVA_HOME]` with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment.
   >* Das importierte, von der Zertifizierungsstelle signierte Zertifikat ersetzt ein selbst signiertes Zertifikat (sofern vorhanden).


1. Führen Sie die Schritte 13 bis 18 im Abschnitt „SSL-Berechtigung erstellen“ durch.
