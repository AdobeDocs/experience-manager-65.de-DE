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
exl-id: 8eb4f691-a66b-498e-8114-307221f63718
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 51%

---

# SSL für JBoss Application Server konfigurieren {#configuring-ssl-for-jboss-application-server}

Zum Konfigurieren von SSL unter JBoss Application Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool zum Erstellen einer Berechtigung oder zum Anfordern und Importieren einer Berechtigung von einer Zertifizierungsstelle verwenden. Anschließend müssen Sie SSL unter JBoss aktivieren.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Keystore erforderlichen Informationen enthält.

In diesem Verfahren gilt:

* `[appserver root]` ist der Basisordner des Anwendungsservers, auf dem AEM Formulare ausgeführt werden.
* `[type]` ist ein Ordnername, der je nach Art der von Ihnen ausgeführten Installation variiert.

## SSL-Berechtigung erstellen {#create-an-ssl-credential}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[JAVA HOME]*/bin und geben Sie den folgenden Befehl ein, um die Berechtigung und den Keystore zu erstellen:

   `keytool -genkey -dname "CN=`*Host* `, OU=`*NameGroup* `, O=`*NameFirma* `,L=`*NameStadt* `, S=`** `, C=`NameStateCountry Code&quot;  `-alias "AEMForms Cert"` `-keyalg RSA -keypass`*key_* `-keystore`*passwordkeystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen. Der Hostname ist der voll qualifizierte Domänenname des Anwendungsservers.

1. Geben Sie `keystore_password` ein, wenn Sie zur Eingabe eines Kennworts aufgefordert werden. Das Kennwort für den Keystore und der Schlüssel müssen identisch sein.

   >[!NOTE]
   >
   >Das in diesem Schritt eingegebene `keystore_password` *Kennwort kann mit dem in Schritt 1 eingegebenen Kennwort (key_password) übereinstimmen oder anders sein.*

1. Kopieren Sie den Ordner *keystorename*.keystore in den Ordner `[appserver root]/server/[type]/conf` , indem Sie einen der folgenden Befehle eingeben:

   * (Windows Einzelserver) `copy` `keystorename.keystore[appserver root]\standalone\configuration`
   * (Windows Server Cluster) Kopieren Sie `keystorename.keystore[appserver root]\domain\configuration`
   * (Linux Einzelserver) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Linux-Servercluster) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exportieren Sie die Zertifikatdatei durch Eingabe des folgenden Befehls:

   * (Einzelserver) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Servercluster) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Geben Sie das *keystore_Kennwort* ein, wenn Sie zur Eingabe eines Kennworts aufgefordert werden.
1. Kopieren Sie die Datei AEMForms_cert.cer in den Ordner *[appserver root] \conf* , indem Sie den folgenden Befehl eingeben:

   * (Windows Einzelserver) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Windows Server Cluster) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Linux Einzelserver) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Linux-Servercluster) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Zeigen Sie den Inhalt des Zertifikats durch Eingabe des folgenden Befehls an:

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. Um ggf. Schreibzugriff auf die Datei &quot;cacerts&quot;in `[JAVA_HOME]\jre\lib\security` zu gewähren, führen Sie die folgende Aufgabe aus:

   * (Windows) Klicken Sie mit der rechten Maustaste auf die Datei „cacerts“, wählen Sie „Eigenschaften“ und deaktivieren Sie das Attribut „Schreibgeschützt“.
   * (Linux) Typ `chmod 777 cacerts`

1. Importieren Sie das Zertifikat durch Eingabe des folgenden Befehls:

   `keytool -import -alias “AEMForms Cert” -file`*AEMForms_* `.cer -keystore`*certJAVA_HOME* `\jre\lib\security\cacerts`

1. Geben Sie `changeit` als Kennwort ein. Dieses Kennwort ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
1. Wenn Sie nach `Trust this certificate? [no]`: gefragt werden, geben Sie `yes` ein. Daraufhin wird die Bestätigung „Certificate was added to keystore“ angezeigt.
1. Wenn Sie die Verbindung über SSL von Workbench aus herstellen, müssen Sie das Zertifikat auf dem Workbench-Computer installieren.
1. Öffnen Sie in einem Texteditor die folgende Dateien zur Bearbeitung:

   * Einzelserver - `[appserver root]`/standalone/configuration/lc_&lt;dbname/turnkey>.xml

   * Servercluster - `[appserver root]`/domain/configuration/host.xml

   * Servercluster - `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. 
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

   Suchen Sie den Abschnitt `<server>` , der nach dem folgenden Code vorhanden ist:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```xml
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * **Fügen Sie für Servercluster** im  [Anwendungsserver-Stammordner]\domain\configuration\host.xml auf allen Knoten den folgenden  &lt;security-realms> Abschnitt hinzu:

   ```xml
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Suchen Sie auf dem primären Knoten des Serverclusters im Ordner [appserver root]\domain\configuration\domain_&lt;dbname>.xml den Abschnitt &lt;server> , der nach dem folgenden Code vorhanden ist:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Fügen Sie Folgendes dem &lt;server>-Abschnitt hinzu, der nach dem obigen Code steht:

   ```xml
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

      * Navigieren Sie an einer Eingabeaufforderung zu *`[appserver root]`*/bin.
      * Beenden Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`
      * Warten Sie, bis der JBoss-Prozess vollständig heruntergefahren wurde. (Dies ist der Fall, wenn der JBoss-Prozess die Kontrolle wieder an das Terminal übergibt, in dem er gestartet wurde.)
      * Starten Sie den Server durch Eingabe des folgenden Befehls:

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`



1. Um mithilfe von SSL auf Administration Console zuzugreifen, geben Sie in einem Webbrowser `https://[host name]:'port'/adminui` ein:

   Der SSL-Standardanschluss für JBoss ist 8443. Geben Sie von hier an beim Zugriff auf AEM Forms diesen Anschluss an.

## Berechtigung von einer Zertifizierungsstelle anfordern {#request-a-credential-from-a-ca}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *[JAVA HOME]*/bin und geben Sie den folgenden Befehl ein, um den Keystore und den Schlüssel zu erstellen:

   `keytool -genkey -dname "CN=`*Host* `, OU=`*NameGroup* `, O=`*NameFirma* `, L=`*NameStadt* `, S=`** `, C=`*NameStateCountry Code*&quot;  `-alias "AEMForms Cert"` `-keyalg RSA -keypass`-*key_* `-keystore`*passwordkeystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.

1. Geben Sie den folgenden Befehl ein, um eine Zertifikatanforderung an die Zertifizierungsstelle zu erzeugen:

   `keytool -certreq -alias` &quot;AEMForms Cert&quot;  `-keystore`** `.keystore -file`*keystorenameAEMFormscertRequest.csr*

1. Wenn Ihre Anforderung einer Zertifikatdatei erfüllt wurde, führen Sie die Schritte im nächsten Verfahren durch.

## Berechtigung von einer Zertifizierungsstelle zum Aktivieren von SSL verwenden  {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *`[JAVA HOME]`*/bin und geben Sie den folgenden Befehl ein, um das Stammzertifikat der Zertifizierungsstelle zu importieren, mit der die CSR-Datei signiert wurde:

   `keytool -import -trustcacerts -file` rootcert.pem -keystore` keystorename.keystore -alias root`

   Wenn sich das Stammzertifikat nicht im Browser befindet, importieren Sie es ebenfalls dorthin.

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.*

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *`[JAVA HOME]`*/bin und geben Sie den folgenden Befehl ein, um die Berechtigung in den Keystore zu importieren:

   `keytool -import -trustcacerts -file`** `.crt -keystore`*CACertificateNamekeystorename* `.keystore`

   >[!NOTE]
   >
   >* Ersetzen Sie `[JAVA_HOME]` durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.
   >* Das importierte, von der Zertifizierungsstelle signierte Zertifikat ersetzt ein selbst signiertes Zertifikat (sofern vorhanden).


1. Führen Sie die Schritte 13 bis 18 im Abschnitt „SSL-Berechtigung erstellen“ durch.
