---
title: AEM Forms mit der JavaAPI aufrufen
seo-title: AEM Forms mit der JavaAPI aufrufen
description: Verwenden Sie die AEM Forms Java API für das RMI-Transportprotokoll für Remote-Aufrufe, VM-Transport für lokalen Aufruf, SOAP für Remote-Aufruf, verschiedene Authentifizierungen wie Benutzername und Kennwort sowie synchrone und asynchrone Aufrufanforderungen.
seo-description: Verwenden Sie die AEM Forms Java API für das RMI-Transportprotokoll für Remote-Aufrufe, VM-Transport für lokalen Aufruf, SOAP für Remote-Aufruf, verschiedene Authentifizierungen wie Benutzername und Kennwort sowie synchrone und asynchrone Aufrufanforderungen.
uuid: 5e2fef2a-05f3-4283-8fd3-2d7dca411000
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 0e6e7850-6137-42c5-b8e2-d4e352fddae2
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '5495'
ht-degree: 88%

---


# AEM Forms mit der JavaAPI aufrufen {#invoking-aem-forms-using-the-javaapi}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

AEM Forms kann mit der AEM Forms Java API aufgerufen werden. Bei Verwendung der AEM Forms-Java-API können Sie entweder die Aufruf-API oder Java-Client-Bibliotheken verwenden. Java-Client-Bibliotheken sind für Dienste wie den Rights Management-Dienst verfügbar. Mit diesen stark typisierten APIs können Sie Java-Anwendungen entwickeln, die AEM Forms aufrufen.

Die Aufruf-API sind Klassen, die sich im Paket `com.adobe.idp.dsc`befinden. Mit diesen Klassen können Sie eine Aufrufanforderung direkt an einen Dienst senden und eine zurückgegebene Aufruf-Antwort verarbeiten. Verwenden Sie die Aufruf-API, um kurzlebige oder langlebige Prozesse aufzurufen, die mit Workbench erstellt wurden.

Die empfohlene Methode zum programmgesteuerten Aufrufen eines Dienstes ist die Verwendung einer Java-Client-Bibliothek, die dem Dienst und nicht der Aufruf-API entspricht. Verwenden Sie zum Aufrufen des Verschlüsselungsdienstes beispielsweise die Client-Bibliothek des Verschlüsselungsdiensts. Rufen Sie zum Ausführen eines Verschlüsselungsdienstvorgangs eine Methode auf, die zu dem Client-Objekt des Verschlüsselungsdiensts gehört. Sie können ein PDF-Dokument mit einem Kennwort verschlüsseln, indem Sie die Methode `EncryptionServiceClient`des Objekts `encryptPDFUsingPassword` aufrufen.

Die Java-API unterstützt die folgenden Funktionen:

* RMI-Transportprotokoll für den Remote-Aufruf
* VM-Transport für den lokalen Aufruf
* SOAP für den Remote-Aufruf
* Unterschiedliche Authentifizierung, wie z. B. Benutzername und Kennwort
* Synchrone und asynchrone Aufrufanforderungen

**Website für Adobe-Entwickler**

Die Website für Adobe-Entwickler enthält die folgenden Artikel, in denen der Aufruf von AEM Forms-Diensten über die Java-API beschrieben wird:

[Verwenden von Java-Servlets zum Aufrufen von AEM Forms-Prozessen](https://www.adobe.com/devnet/livecycle/articles/java_servlets.html)

[Aufrufen der AEM Forms Distiller-API von Java](https://www.adobe.com/devnet/livecycle/articles/distiller_java_03.html)

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](#including-aem-forms-java-library-files)

[An Menschen orientierte langlebige Prozesse aufrufen](invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md)

[Verbindungseigenschaften festlegen](#setting-connection-properties)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](#invoking-a-service-using-a-java-client-library)

[Aufruf eines kurzlebigen Prozesses mithilfe der Aufruf-API](#invoking-a-short-lived-process-using-the-invocation-api)

[Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](/help/forms/developing/invoking-human-centric-long-lived.md)

## Einbeziehung von AEM Forms Java-Bibliotheksdateien {#including-aem-forms-java-library-files}

Um einen AEM Forms-Dienst mithilfe der Java-API programmgesteuert aufzurufen, fügen Sie die erforderlichen Bibliotheksdateien (JAR-Dateien) in den Klassenpfad Ihres Java-Projekts ein. Die JAR-Dateien, die Sie in den Klassenpfad Ihrer Client-Anwendung aufnehmen, hängen von mehreren Faktoren ab:

* Der aufzurufende AEM Forms-Dienst. Eine Client-Anwendung kann einen oder mehrere Dienste aufrufen.
* Der Modus, in dem Sie einen AEM Forms-Dienst aufrufen möchten. Sie können den EJB- oder SOAP-Modus verwenden. (Siehe [Einstellung von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>(Nur Turnkey) Beginn des AEM Forms-Servers mit dem Befehl `standalone.bat -b <Server IP> -c lc_turnkey.xml`, um eine Server-IP für EJB anzugeben

* Der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt wird.

### Servicespezifische JAR-Dateien  {#service-specific-jar-files}

In der folgenden Tabelle sind die JAR-Dateien aufgeführt, die zum Aufrufen von AEM Forms-Diensten erforderlich sind.

<table>
 <thead>
  <tr>
   <th><p>File</p></th>
   <th><p>Beschreibung</p></th>
   <th><p>Ort</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>adobe-livecycle-client.jar</p></td>
   <td><p>Muss immer im Klassenpfad einer Java-Client-Anwendung enthalten sein.</p></td>
   <td><p>&lt;<i>install directory</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-usermanager-client.jar</p></td>
   <td><p>Muss immer im Klassenpfad einer Java-Client-Anwendung enthalten sein.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-utilities.jar</p></td>
   <td><p>Muss immer im Klassenpfad einer Java-Client-Anwendung enthalten sein.</p></td>
   <td><p>&lt;<i>install directory</i>&gt;/sdk//client-libs/&lt;app server&gt;</p></td>
  </tr>
  <tr>
   <td><p>adobe-applicationmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich, um den Application Manager-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-assembler-client.jar</p></td>
   <td><p>Erforderlich, um den Assembler-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-backup-restore-client-sdk.jar</p></td>
   <td><p>Erforderlich zum Aufrufen der Backup- und Wiederherstellungsdienst-API.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-barcodedforms-client.jar</p></td>
   <td><p>Erforderlich, den Barcoded Forms-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-convertpdf-client.jar</p></td>
   <td><p>Erforderlich, um den Convert PDF-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-distiller-client.jar</p></td>
   <td><p>Erforderlich, um den Distiller-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-docconverter-client.jar</p></td>
   <td><p>Erforderlich, um den DocConverter-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-contentservices-client.jar</p></td>
   <td><p>Erforderlich, um den Document Management-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-encryption-client.jar</p></td>
   <td><p>Erforderlich, um den Verschlüsselungsdienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-forms-client.jar</p></td>
   <td><p>Erforderlich, um den Forms-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-formdataintegration-client.jar</p></td>
   <td><p>Erforderlich, um den Form Data Integration-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-generatepdf-client.jar</p></td>
   <td><p>Erforderlich, um den Generate PDF-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-generate3dpdf-client.jar</p></td>
   <td><p>Erforderlich, um den Generate 3D PDF-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-jobmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich, um den Job Manager-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-output-client.jar</p></td>
   <td><p>Erforderlich, um den Output-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-pdfutility-client.jar</p></td>
   <td><p>Erforderlich, um den PDF Utilities- oder XMP Utilities-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-reader-extensions-client.jar</p></td>
   <td><p>Erforderlich, um den Acrobat Reader DC Extensions-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-repository-client.jar</p><p>commons-codec-1.3.jar</p></td>
   <td><p>Erforderlich, um den Repository-Dienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p><p>&lt;<i>install directory</i>&gt;/sdk/client-libs\thirdparty</p></td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>adobe-rightsmanagement-client.jar</p></li>
     <li><p>namespace.jar</p></li>
     <li><p>jaxb-api.jar</p></li>
     <li><p>jaxb-impl.jar</p></li>
     <li><p>jaxb-libs.jar</p></li>
     <li><p>jaxb-xjc.jar</p></li>
     <li><p>relaxngDatatype.jar</p></li>
     <li><p>xsdlib.jar</p></li>
    </ul></td>
   <td><p>Erforderlich, um den Rights Management-Dienst aufzurufen.</p><p>Wenn AEM Forms auf JBoss bereitgestellt wird, schließen Sie alle diese Dateien ein. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p><p>JBoss-spezifisches lib-Verzeichnis</p></td>
  </tr>
  <tr>
   <td><p>adobe-signatures-client.jar</p></td>
   <td><p>Erforderlich, um den Signaturdienst aufzurufen.</p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-taskmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich, um den Task Manager-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
  <tr>
   <td><p>adobe-truststore-client.jar</p></td>
   <td><p>Erforderlich, um den Trust Store-Dienst aufzurufen. </p></td>
   <td><p>&lt;&gt;install directory</i>&gt;/sdk/client-libs/common<i></i></p></td>
  </tr>
 </tbody>
</table>

### Verbindungsmodus und J2EE-Anwendungs-JAR-Dateien  {#connection-mode-and-j2ee-application-jar-files}

In der folgenden Tabelle sind die JAR-Dateien aufgeführt, die vom Verbindungsmodus und dem J2EE-Anwendungsserver abhängen, auf dem AEM Forms bereitgestellt wird.

<table>
 <thead>
  <tr>
   <th><p>Datei</p> </th>
   <th><p>Beschreibung</p> </th>
   <th><p>Ort</p> </th>
  </tr>
 &lt;/thead align="left"&gt;
 <tbody>
  <tr>
   <td>
    <ul>
     <li><p>activation.jar</p> </li>
     <li><p>achse.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jaxen-1.1-beta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
    </ul>
    <ul>
     <li>xercesImpl.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul> <p> </p> </td>
   <td><p>wenn AEM Forms im SOAP-Modus aufgerufen wird, schließen Sie diese JAR-Dateien ein.</p> </td>
   <td><p>&lt;<em>install directory</em>&gt;/sdk/client-libs/thirdparty</p> </td>
  </tr>
  <tr>
   <td><p> jboss-client.jar</p> </td>
   <td><p>wenn AEM Forms auf JBoss-Anwendungsserver bereitgestellt wird, schließen Sie diese JAR-Datei ein.</p> <p>Erforderliche Klassen werden vom Classification-Loader nicht gefunden, wenn jboss-client.jar und die referenzierten JARs nicht nebeneinander angeordnet sind.</p> </td>
   <td><p>JBoss-Client-Lib-Verzeichnis</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Datei nicht einschließen.</p> </td>
  </tr>
  <tr>
   <td><p>wlclient.jar</p> </td>
   <td><p>Wenn AEM Forms auf BEA WebLogic Server® bereitgestellt wird, fügen Sie diese JAR-Datei ein.</p> </td>
   <td><p>WebLogic-spezifisches Bibliotheksverzeichnis</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Datei nicht einschließen.</p> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>com.ibm.ws.admin.client_6.1.0.jar</p> </li>
     <li><p>com.ibm.ws.webservices.thinclient_6.1.0.jar</p> </li>
    </ul> </td>
   <td>
    <ul>
     <li><p>wenn AEM Forms auf WebSphere-Anwendungsserver implementiert ist, schließen Sie diese JAR-Dateien ein.</p> </li>
     <li><p>(com.ibm.ws.webservices.thinclient_6.1.0.jar ist für den Webdienstaufruf erforderlich).</p> </li>
    </ul> </td>
   <td><p>WebSphere-spezifisches lib-Verzeichnis (<em>[WAS_HOME]</em>/runtimes)</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Datei nicht einschließen.</p> </td>
  </tr>
 </tbody>
</table>

### Aufrufen von Szenarien  {#invoking-scenarios}

In der folgenden Tabelle werden die Aufrufszenarien angegeben und die zum erfolgreichen Aufrufen von AEM Forms erforderlichen JAR-Dateien aufgeführt.

<table>
 <thead>
  <tr>
   <th><p>Dienste</p> </th>
   <th><p>Aufrufmodus</p> </th>
   <th><p>J2EE-Anwendungsserver</p> </th>
   <th><p>Erforderliche JAR-Dateien</p> </th>
  </tr>
 &lt;/thead align="left"&gt;
 <tbody>
  <tr>
   <td><p>Forms-Dienst</p> </td>
   <td><p>EJB</p> </td>
   <td><p>JBoss</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
    </ul>
    <ul>
     <li>jboss-client.jar</li>
    </ul>
    <ul>
     <li>adobe-forms-client.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-Dienst</p> <p>Acrobat Reader DC Extensions-Dienst</p> <p>Signature-Dienst</p> </td>
   <td><p>EJB</p> </td>
   <td><p>JBoss</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
    </ul>
    <ul>
     <li>jboss-client.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul>
    <ul>
     <li><p>adobe-forms-client.jar</p> </li>
     <li><p>adobe-reader-extensions-client.jar</p> </li>
     <li><p>adobe-signatures-client.jar</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-Dienst</p> </td>
   <td><p>SOAP</p> </td>
   <td><p>WebLogic</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
     <li><p>wlclient.jar</p> </li>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jai_imageio.jar</p> </li>
     <li><p>jaxen-1.1-beta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
     <li><p>xercesImpl.jar</p> </li>
     <li><p>adobe-forms-client.jar</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-Dienst</p> <p>Acrobat Reader DC Extensions-Dienst</p> <p>Signature-Dienst</p> </td>
   <td><p>SOAP</p> </td>
   <td><p>WebLogic</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
     <li><p>wlclient.jar</p> </li>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jai_imageio.jar</p> </li>
     <li><p>jaxen-1.1-beta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
     <li><p>xercesImpl.jar</p> </li>
     <li><p>adobe-forms-client.jar</p> </li>
     <li><p>adobe-reader-extensions-client.jar</p> </li>
     <li><p>adobe-signatures-client.jar</p> </li>
    </ul> </td>
  </tr> xmp-uti
 </tbody>
</table>

### Aktualisieren von JAR-Dateien {#upgrading-jar-files}

Wenn Sie ein Upgrade von LiveCycle auf AEM Forms durchführen, wird empfohlen, dass Sie die AEM Forms-JAR-Dateien in den Klassenpfad Ihres Java-Projekts aufnehmen. Wenn Sie beispielsweise Dienste wie den Rights Management-Dienst verwenden, tritt ein Kompatibilitätsproblem auf, wenn Sie keine AEM Forms-JAR-Dateien in Ihren Klassenpfad aufnehmen.

Angenommen, dass Sie auf AEM Forms aktualisieren Um eine Java-Anwendung zu verwenden, die den Rights Management-Dienst aufruft, schließen Sie die AEM Forms-Versionen der folgenden JAR-Dateien ein:

* adobe-rightsmanagement-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Verbindungseigenschaften festlegen  {#setting-connection-properties}

Sie legen Verbindungseigenschaften fest, um AEM Forms bei Verwendung der Java-API aufzurufen. Geben Sie beim Festlegen von Verbindungseigenschaften an, ob Dienste remote oder lokal aufgerufen werden sollen, sowie den Verbindungsmodus und die Authentifizierungswerte. Authentifizierungswerte sind erforderlich, wenn die Dienstsicherheit aktiviert ist. Wenn die Servicesicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.

Der Verbindungsmodus kann entweder der SOAP- oder der EJB-Modus sein. Der EJB-Modus verwendet das RMI/IIOP-Protokoll, und die Leistung des EJB-Modus ist besser als die des SOAP-Modus. Der SOAP-Modus wird verwendet, um die Abhängigkeit eines J2EE-Anwendungsservers zu beseitigen oder wenn sich eine Firewall zwischen AEM Forms und der Client-Anwendung befindet. Der SOAP-Modus verwendet das https-Protokoll als zugrunde liegenden Transport und kann über Firewall-Grenzen hinweg kommunizieren. Wenn weder eine Abhängigkeit des J2EE-Anwendungsservers noch eine Firewall ein Problem darstellt, wird empfohlen, den EJB-Modus zu verwenden.

Um einen AEM Forms-Dienst erfolgreich aufzurufen, legen Sie die folgenden Verbindungseigenschaften fest:

* **DSC_DEFAULT_EJB_ENDPOINT:** Wenn Sie den EJB-Verbindungsmodus verwenden, stellt dieser Wert die URL des J2EE-Anwendungsservers dar, auf dem AEM Forms implementiert ist. Um AEM Forms aus der Ferne aufzurufen, geben Sie den Namen des J2EE-Anwendungsservers an, auf dem AEM Forms implementiert ist. Wenn sich Ihre Client-Anwendung auf demselben J2EE-Anwendungsserver befindet, können Sie `localhost`angeben. Geben Sie abhängig davon, auf welchem &#x200B;&#x200B;J2EE-Anwendungsserver AEM Forms implementiert ist, einen der folgenden Werte an:

   * JBoss: `https://<ServerName>:8080 (default port)`
   * WebSphere: `iiop://<ServerName>:2809 (default port)`
   * WebLogic: `t3://<ServerName>:7001 (default port)`

* **DSC_DEFAULT_SOAP_ENDPOINT**: Wenn Sie den SOAP-Verbindungsmodus verwenden, stellt dieser Wert den Endpunkt dar, an den eine Aufrufanforderung gesendet wird. Um AEM Forms aus der Ferne aufzurufen, geben Sie den Namen des J2EE-Anwendungsservers an, auf dem AEM Forms implementiert ist. Wenn sich Ihre Client-Anwendung auf demselben J2EE-Anwendungsserver befindet, können Sie `localhost`angeben (z. B. `http://localhost:8080`.)

   * Der Portwert `8080` gilt, wenn die J2EE-Anwendung JBoss ist. Wenn der J2EE-Anwendungsserver IBM WebSphere ist, verwenden Sie Port `9080`. Wenn der J2EE-Anwendungsserver IBM WebSphere ist, verwenden Sie Port `7001`. (Diese Werte sind Standardportwerte. Wenn Sie den Portwert ändern, verwenden Sie die entsprechende Portnummer.)

* **DSC_TRANSPORT_PROTOCOL**: Wenn Sie den EJB-Verbindungsmodus verwenden, geben Sie `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` für diesen Wert an. Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL` an.
* **DSC_SERVER_TYPE**: Der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt wird. Gültige Werte sind `JBoss`, `WebSphere`, `WebLogic`.

   * Wenn Sie diese Verbindungseigenschaft auf `WebSphere` festlegen, wird der Wert `java.naming.factory.initial` auf `com.ibm.ws.naming.util.WsnInitCtxFactory` eingestellt.
   * Wenn Sie diese Verbindungseigenschaft auf `WebLogic` festlegen, wird der Wert `java.naming.factory.initial` auf `weblogic.jndi.WLInitialContextFactory` eingestellt.
   * Wenn Sie diese Verbindungseigenschaft auf `JBoss` festlegen, wird der Wert `java.naming.factory.initial` auf `org.jnp.interfaces.NamingContextFactory` eingestellt.
   * Sie können die Eigenschaft `java.naming.factory.initial` auf einen Wert setzen, der Ihren Anforderungen entspricht, wenn Sie die Standardwerte nicht verwenden möchten.

   >[!NOTE]
   >
   >Anstatt eine Zeichenfolge zum Festlegen der Verbindungseigenschaft `DSC_SERVER_TYPE` zu verwenden, können Sie ein statisches Element der `ServiceClientFactoryProperties`-Klasse verwenden. Folgende Werte können verwendet werden: `ServiceClientFactoryProperties.DSC_WEBSPHERE_SERVER_TYPE`, `ServiceClientFactoryProperties.DSC_WEBLOGIC_SERVER_TYPE` oder `ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE`.

* **DSC_CREDENTIAL_USERNAME:** Gibt den AEM Forms-Benutzernamen an. Damit ein Benutzer erfolgreich einen AEM Forms-Dienst aufrufen kann, benötigen Sie die Rolle „Dienstbenutzer“. Ein Benutzer kann auch eine andere Rolle haben, die die Berechtigung zum Service-Aufruf enthält. Andernfalls wird eine Ausnahme ausgelöst, wenn versucht wird, einen Dienst aufzurufen. Wenn die Servicesicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.
* **DSC_CREDENTIAL_PASSWORD:** Gibt den entsprechenden Kennwortwert an. Wenn die Servicesicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.
* **DSC_REQUEST_TIMEOUT:** Das Standardlimit für Anforderungszeitlimits für die SOAP-Anforderung beträgt 1200000 Millisekunden (20 Minuten). Manchmal kann eine Anfrage länger dauern, um den Vorgang abzuschließen. Beispielsweise kann eine SOAP-Anforderung, die eine große Menge von Datensätzen abruft, ein längeres Zeitlimit erfordern. Mit `ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT`   können Sie das Zeitlimit für Anforderungsaufrufe für die SOAP-Anforderungen erhöhen.

   **Hinweis**: Nur SOAP-basierte Aufrufe unterstützen die DSC_REQUEST_TIMEOUT Eigenschaft.

Führen Sie die folgenden Aufgaben aus, um Verbindungseigenschaften festzulegen:

1. Erstellen Sie ein Objekt `java.util.Properties`, indem Sie den Konstruktor verwenden.
1. Um die Verbindungseigenschaft `DSC_DEFAULT_EJB_ENDPOINT` festzulegen, rufen Sie die `java.util.Properties`-Methode des Objekts `setProperty` auf und übergeben Sie die folgenden Werte:

   * Der Wert für die Auflistung `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT`
   * Ein string-Wert, der die URL des J2EE-Anwendungsservers angibt, der AEM Forms hostet

   >[!NOTE]
   >
   >Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie den Wert für die Auflistung `ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT` anstelle der Auflistung `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` an.

1. Um die Verbindungseigenschaft `DSC_TRANSPORT_PROTOCOL` festzulegen, rufen Sie die `java.util.Properties`-Methode des Objekts `setProperty` auf und übergeben Sie die folgenden Werte:

   * Der Wert für die Auflistung `ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL`
   * Der Wert für die Auflistung `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL`

   >[!NOTE]
   >
   >Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie den Wert `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL`Auflistung anstelle des Werts `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` Auflistung an.

1. Um die Verbindungseigenschaft `DSC_SERVER_TYPE` festzulegen, rufen Sie die `java.util.Properties`-Methode des Objekts `setProperty` auf und übergeben Sie die folgenden Werte:

   * Der Wert `ServiceClientFactoryProperties.DSC_SERVER_TYPE`Auflistung
   * Ein string-Wert, der den J2EE-Anwendungsserver angibt, auf dem AEM Forms gehostet wird. (wenn beispielsweise AEM Forms auf implementiert wird, geben Sie `JBoss`JBoss an.

      1. Um die Verbindungseigenschaft `DSC_CREDENTIAL_USERNAME` festzulegen, rufen Sie die `java.util.Properties`-Methode des Objekts `setProperty` auf und übergeben Sie die folgenden Werte:
   * Der Wert für die Auflistung `ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME`
   * Ein Zeichenfolgenwert, der den Benutzernamen angibt, der zum Aufrufen von AEM Forms erforderlich ist

      1. Um die Verbindungseigenschaft `DSC_CREDENTIAL_PASSWORD` festzulegen, rufen Sie die `java.util.Properties`-Methode des Objekts `setProperty` auf und übergeben Sie die folgenden Werte:
   * Der Wert für die Auflistung `ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD`
   * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt.



**Einstellen des EJB-Verbindungsmodus für JBoss**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, die auf JBoss implementiert sind und den EJB-Verbindungsmodus verwenden.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "https://<hostname>:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DOCUMENT_HTTP_ENDPOINT,"https://<hostname>:8080");
```

**EJB-Verbindungsmodus für WebLogic festlegen**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, die auf WebLogic implementiert sind und den EJB-Verbindungsmodus verwenden.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "t3://localhost:7001");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebLogic");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**Einstellung des EJB-Anschlussmodus für WebSphere**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, die auf WebSphere implementiert sind und den EJB-Verbindungsmodus verwenden.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "iiop://localhost:2809");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebSphere");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**SOAP-Verbindungsmodus festlegen**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften im SOAP-Modus festgelegt, um AEM Forms aufzurufen, was auf JBoss bereitgestellt ist.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

>[!NOTE]
>
>Wenn Sie den SOAP-Verbindungsmodus auswählen, müssen Sie sicherstellen, dass zusätzliche JAR-Dateien in den Klassenpfad Ihrer Clientanwendung aufgenommen werden.

**Festlegen der Verbindungseigenschaften bei deaktivierter Dienstsicherheit**

Im folgenden Java-Codebeispiel werden die Verbindungseigenschaften festgelegt, die zum Aufrufen von AEM Forms, das auf dem JBoss-Anwendungsserver bereitgestellt wird, und bei deaktivierter Dienstsicherheit erforderlich sind.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
```

>[!NOTE]
>
>Alle mit dem Programmieren mit AEM Forms verbundenen Java-Schnellstarts zeigen sowohl EJB- als auch SOAP-Verbindungseinstellungen.

**SOAP-Verbindungsmodus mit benutzerdefiniertem Timeout-Limit für den Aufruf festlegen**

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT, "1800000"); // Request timeout limit 30 Minutes
```

**Verwendung eines Kontextobjekts zum Aufrufen von AEM Forms**

Sie können ein Objekt. `com.adobe.idp.Context` verwenden, um einen AEM Forms-Dienst mit einem authentifizierten Benutzer aufzurufen (das Objekt `com.adobe.idp.Context` steht für einen authentifizierten Benutzer). Bei Verwendung eines `com.adobe.idp.Context`-Objekts müssen Sie die `DSC_CREDENTIAL_USERNAME`- oder `DSC_CREDENTIAL_PASSWORD`-Eigenschaften nicht festlegen. Sie können ein `com.adobe.idp.Context`-Objekt abrufen, wenn Sie Benutzer mit der `AuthenticationManagerServiceClient`-Methode des Objekts `authenticate` authentifizieren.

Die `authenticate`-Methode gibt ein Objekt `AuthResult` zurück, das das Ergebnis der Authentifizierung enthält. Sie können ein `com.adobe.idp.Context`-Objekt erstellen, indem Sie seinen Konstruktor aufrufen. Rufen Sie dann die Methode `com.adobe.idp.Context` des Objekts `initPrincipal`  auf, und übergeben Sie das Objekt `AuthResult` wie im folgenden Code gezeigt:

```java
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
```

Anstatt die Eigenschaften `DSC_CREDENTIAL_USERNAME` oder `DSC_CREDENTIAL_PASSWORD` festzulegen, können Sie die `ServiceClientFactory`-Methode des Objekts aufrufen und das `com.adobe.idp.Context`-Objekt übergeben. `setContext` Wenn Sie einen AEM Forms-Benutzer zum Aufrufen eines Dienstes verwenden, stellen Sie sicher, dass diese die Rolle `Services User` haben, die zum Aufrufen eines AEM Forms-Dienstes erforderlich ist.

Das folgende Codebeispiel zeigt, wie ein `com.adobe.idp.Context`-Objekt in Verbindungseinstellungen verwendet wird, die zum Erstellen eines `EncryptionServiceClient` -Objekts verwendet werden.

```java
 //Authenticate a user and use the Context object within connection settings
 // Authenticate the user
 String username = "wblue";
 String password = "password";
 AuthResult authResult = authClient.authenticate(username, password.getBytes());
 
 //Set a Content object that represents the authenticated user
 //Use the Context object to invoke the Encryption service
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
 
 //Set connection settings
 Properties connectionProps = new Properties();
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://<server>:1099");
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE);
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DOCUMENT_HTTP_ENDPOINT,"jnp://<server>:1099");

 
 //Create a ServiceClientFactory object
 ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 myFactory.setContext(myCtx);
 
 //Create an EncryptionServiceClient object
 EncryptionServiceClient encryptClient  = new EncryptionServiceClient(myFactory);
```

>[!NOTE]
>
>Vollständige Informationen zum Authentifizieren eines Benutzers finden Sie unter [Benutzer authentifizieren](/help/forms/developing/users.md#authenticating-users).

### Aufrufen von Szenarien  {#invoking_scenarios-1}

Die folgenden Aufrufszenarien werden in diesem Abschnitt behandelt:

* Eine Client-Anwendung, die in einer eigenen Java Virtual Machine (JVM) ausgeführt wird, ruft eine eigenständige AEM Forms-Instanz auf.
* Eine Client-Anwendung, die in ihrer eigenen JVM ausgeführt wird, ruft AEM Forms-Clusterinstanzen auf.

### Die Client-Anwendung, die eine eigenständige AEM Forms-Instanz aufruft  {#client-application-invoking-a-stand-alone-aem-forms-instance}

Das folgende Diagramm zeigt eine Client-Anwendung, die in einer eigenen JVM ausgeführt wird und eine eigenständige AEM Forms-Instanz aufruft.

In diesem Szenario wird eine Client-Anwendung in einer eigenen JVM ausgeführt und ruft AEM Forms-Dienste auf.

>[!NOTE]
>
>Dieses Szenario ist das Aufrufszenario, auf dem alle Schnellstarts basieren.

### Client-Anwendung, die geclusterte AEM Forms-Instanzen aufruft  {#client-application-invoking-clustered-aem-forms-instances}

Das folgende Diagramm zeigt eine Client-Anwendung, die in einer eigenen JVM ausgeführt wird und eine eigenständige AEM Forms-Instanz in einem Cluster aufruft.

Dieses Szenario ähnelt der Client-Anwendung, die eine eigenständige AEM Forms-Instanz aufruft. Die Provider-URL ist jedoch unterschiedlich. Wenn eine Client-Anwendung eine Verbindung zu einem bestimmten J2EE-Anwendungsserver herstellen möchte, muss die Anwendung die URL ändern, um auf den jeweiligen J2EE-Anwendungsserver zu verweisen.

Der Verweis auf einen bestimmten J2EE-Anwendungsserver wird nicht empfohlen, da die Verbindung zwischen der Client-Anwendung und AEM Forms beendet wird, wenn der Anwendungsserver beendet wird. Es wird empfohlen, dass die Provider-URL anstelle eines bestimmten J2EE-Anwendungsservers auf einen JNDI-Manager auf Zellenebene verweist.

Client-Anwendungen, die den SOAP-Verbindungsmodus verwenden, können den HTTP-Load-Balancer-Port für das Cluster verwenden. Client-Anwendungen, die den EJB-Verbindungsmodus verwenden, können eine Verbindung zum EJB-Port eines bestimmten J2EE-Anwendungsservers herstellen. Diese Aktion behandelt den Lastausgleich zwischen Clusterknoten.

**WebSphere**

Das folgende Beispiel zeigt den Inhalt einer Datei „jndi.properties“, die zum Herstellen einer Verbindung mit AEM Forms verwendet wird, das in WebSphere implementiert wird.

```ini
 java.naming.factory.initial=com.ibm.websphere.naming.
 WsnInitialContextFactory
 java.naming.provider.url=corbaloc::appserver1:9810,:appserver2:9810
```

**WebLogic**

Das folgende Beispiel zeigt den Inhalt einer Datei „jndi.properties“, die zum Herstellen einer Verbindung mit AEM Forms verwendet wird, das in WebLogic implementiert wird.

```ini
 java.naming.factory.initial=weblogic.jndi.WLInitialContextFactory
 java.naming.provider.url=t3://appserver1:8001, appserver2:8001
```

**JBoss**

Das folgende Beispiel zeigt den Inhalt einer Datei „jndi.properties“, die zum Herstellen einer Verbindung mit AEM Forms verwendet wird, das in JBoss implementiert wird.

```ini
 java.naming.factory.initial= org.jnp.interfaces.NamingContextFactory
 java.naming.provider.url= jnp://appserver1:1099, appserver2:1099,
 appserver3:1099
```

>[!NOTE]
>
>Wenden Sie sich an Ihren Administrator, um den Namen und die Portnummer des J2EE-Anwendungsservers zu ermitteln.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API  {#passing-data-to-aem-forms-services-using-the-java-api}

AEM Forms-Dienstvorgänge verwenden normalerweise PDF-Dokumente oder erzeugen diese. Wenn Sie einen Dienst aufrufen, ist es manchmal erforderlich, ein PDF-Dokument (oder andere Dokumenttypen wie XML-Daten) an den Dienst zu übergeben. Ebenso ist es manchmal notwendig, ein vom Dienst zurückgegebenes PDF-Dokument zu verwenden. Die Java-Klasse, mit der Sie Daten an und von AEM Forms-Diensten übertragen können, ist `com.adobe.idp.Document`.

AEM Forms-Dienste akzeptieren ein PDF-Dokument nicht als andere Datentypen, wie z. B. ein Objekt `java.io.InputStream` oder ein Byte-Array. Ein `com.adobe.idp.Document`-Objekt kann auch verwendet werden, um andere Datentypen, z. B. XML-Daten, an Dienste zu übergeben.

Das Objekt `com.adobe.idp.Document` ist ein serialisierbarer Java-Typ, sodass es über einen RMI-Aufruf übergeben werden kann. Die Empfangsseite kann zusammengestellt werden (gleicher Host, gleiches Klassenladeprogramm), lokal (gleicher Host, anderes Klassenladeprogramm) oder Remote (anderer Host). Die Weitergabe von Dokumenteninhalten wird für jeden Fall optimiert. Befinden sich Sender und Empfänger beispielsweise auf demselben Host, wird der Inhalt über ein lokales Dateisystem übergeben. (In einigen Fällen können Dokumente im Speicher übergeben werden.)

Abhängig von der Objektgröße `com.adobe.idp.Document`, werden die Daten innerhalb des Objekts `com.adobe.idp.Document` befördert oder im Dateisystem des Servers gespeichert. Alle temporären Speicherressourcen, die vom Objekt `com.adobe.idp.Document`   belegt sind, werden nach der Entsorgung von `com.adobe.idp.Document` automatisch entfernt. (Siehe [ Dokumentobjekte entsorgen](invoking-aem-forms-using-java.md#disposing-document-objects).)

Manchmal ist es erforderlich, den Inhaltstyp eines `com.adobe.idp.Document` --Objekts zu kennen, bevor Sie es an einen Dienst übergeben können. Wenn für einen Vorgang beispielsweise ein bestimmter Inhaltstyp erforderlich ist, z. B. `application/pdf`, wird empfohlen, den Inhaltstyp zu bestimmen. (Siehe [Festlegen des Inhaltstyps eines Dokuments](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document).)

Das Objekt `com.adobe.idp.Document`   versucht, den Inhaltstyp anhand der bereitgestellten Daten zu ermitteln. Wenn der Inhaltstyp nicht aus den bereitgestellten Daten abgerufen werden kann (z. B. wenn die Daten als Byte-Array bereitgestellt wurden), legen Sie den Inhaltstyp fest. Um den Inhaltstyp festzulegen, rufen Sie die `com.adobe.idp.Document`-Methode des Objekts `setContentType` auf. (Siehe [Festlegen des Inhaltstyps eines Dokuments](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document))

Wenn Begleitdateien sich im selben Dateisystem befinden, ist das Erstellen eines `com.adobe.idp.Document` schneller. Wenn sich Begleitdateien auf Remote-Dateisystemen befinden, muss ein Kopiervorgang ausgeführt werden, der die Leistung beeinträchtigt.

Eine Anwendung kann sowohl die Datentypen `com.adobe.idp.Document` als auch `org.w3c.dom.Document` enthalten. Stellen Sie jedoch sicher, dass Sie den Datentyp `org.w3c.dom.Document` vollständig qualifizieren. Informationen zum Konvertieren eines `org.w3c.dom.Document` --Objekts in ein `com.adobe.idp.Document`-Objekt finden Sie unter [Schnellstart (EJB-Modus): Formulare mit flexiblen Layouts mithilfe der Java-API vorbefüllen](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api).

>[!NOTE]
>
>Um einen Speicherverlust in WebLogic bei der Verwendung eines `com.adobe.idp.Document`-Objekts zu vermeiden, lesen Sie die Dokumentinformationen in Schritten von 2048 Byte oder weniger. Mit dem folgenden Code werden beispielsweise die Dokumentinformationen in 2048-Byte-Blöcken gelesen:

```java
        // Set up the chunk size to prevent a potential memory leak
        int buffSize = 2048;
 
        // Determine the total number of bytes to read
        int docLength = (int) inDoc.length();
        byte [] byteDoc = new byte[docLength];
 
        // Set up the reading position
        int pos = 0;
 
        // Loop through the document information, 2048 bytes at a time
        while (docLength > 0) {
      // Read the next chunk of information
            int toRead = Math.min(buffSize, docLength);
            int bytesRead = inDoc.read(pos, byteDoc, pos, toRead);
 
            // Handle the exception in case data retrieval failed
            if (bytesRead == -1) {
 
                inDoc.doneReading();
                inDoc.dispose();
                throw new RuntimeException("Data retrieval failed!");
 
            }
 
             // Update the reading position and number of bytes remaining
             pos += bytesRead;
             docLength -= bytesRead;
 
        }
 
        // The document information has been successfully read
        inDoc.doneReading();
        inDoc.dispose();
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Dokumente erstellen  {#creating-documents}

Erstellen Sie ein `com.adobe.idp.Document`-Objekt, bevor Sie einen Dienstvorgang aufrufen, für den ein PDF-Dokument (oder andere Dokumenttypen) als Eingabewert erforderlich sind. Die Klasse `com.adobe.idp.Document`   stellt Konstruktoren bereit, mit denen Sie ein Dokument aus den folgenden Inhaltstypen erstellen können:

* Ein Byte-Array
* Ein vorhandenes `com.adobe.idp.Document`-Objekt
* Ein `java.io.File`-Objekt
* Ein `java.io.InputStream`-Objekt
* Ein `java.net.URL`-Objekt

#### Erstellen eines Dokuments basierend auf einem Byte-Array {#creating-a-document-based-on-a-byte-array}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einem Byte-Array basiert.

**Erstellen eines Dokumentobjekts basierend auf einem Byte-Array**

```java
 Document myPDFDocument = new Document(myByteArray);
```

#### Das Erstellen eines Dokuments basiert auf einem anderen Dokument  {#creating-a-document-based-on-another-document}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einem anderen `com.adobe.idp.Document`-Objekt basiert.

**Erstellen eines Dokumentobjekts basierend auf einem anderen Dokument**

```java
 //Create a Document object based on a byte array
 InputStream is = new FileInputStream("C:\\Map.pdf");
 int len = is.available();
 byte [] myByteArray = new byte[len];
 int i = 0;
 while (i < len) {
       i += is.read(myByteArray, i, len);
 }
 Document myPDFDocument = new Document(myByteArray);
 
 //Create another Document object
 Document anotherDocument = new Document(myPDFDocument);
```

#### Erstellen eines Dokuments basierend auf einer Datei  {#creating-a-document-based-on-a-file}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf eine PDF-Datei *map.pdf basiert*. Diese Datei befindet sich im Stammverzeichnis der C-Festplatte. Dieser Konstruktor versucht, den MIME-Inhaltstyp des `com.adobe.idp.Document`-Objekts mithilfe der Dateinamenerweiterung festzulegen.

Der `com.adobe.idp.Document`Konstruktor, der ein `java.io.File`-Objekt akzeptiert, akzeptiert auch einen Booleschen Parameter. Wenn Sie diese Parameter auf `true` setzen, löscht das `com.adobe.idp.Document`-Objekt die Datei. Diese Aktion bedeutet, dass Sie die Datei nicht entfernen müssen, nachdem Sie sie an den `com.adobe.idp.Document`-Konstruktor übergeben haben.

Wenn Sie diesen Parameter auf `false` setzen, behalten Sie den Besitz dieser Datei bei. Das Einstellen dieses Parameters auf `true` ist effizienter. Der Grund ist, dass das `com.adobe.idp.Document`-Objekt die Datei direkt in den lokalen verwalteten Bereich verschieben kann, anstatt sie zu kopieren (was langsamer ist).

**Erstellen eines Dokumentobjekts basierend auf einer PDF-Datei**

```java
 //Create a Document object based on the map.pdf source file
 File mySourceMap = new File("C:\\map.pdf");
 Document myPDFDocument = new Document(mySourceMap,true);
```

#### Erstellen eines Dokuments basierend auf einem InputStream-Objekt  {#creating-a-document-based-on-an-inputstream-object}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einem`java.io.InputStream`-Objekt basiert.

**Erstellen eines Dokuments basierend auf einem InputStream-Objekt**

```java
 //Create a Document object based on an InputStream object
 InputStream is = new FileInputStream("C:\\Map.pdf");
 Document myPDFDocument = new Document(is);
```

#### Erstellen eines Dokuments basierend auf Inhalt, auf den über eine URL zugegriffen werden kann  {#creating-a-document-based-on-content-accessible-from-an-url}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einer PDF-Datei *map.pdf basiert*. Diese Datei befindet sich in einer Web-Anwendung namens `WebApp`,  , die auf `localhost` läuft. Dieser Konstruktor versucht, den MIME-Inhaltstyp des `com.adobe.idp.Document`-Objekts mithilfe des mit dem URL-Protokoll zurückgegebenen Inhaltstyps festzulegen.

Die URL des `com.adobe.idp.Document`-Objekts wird immer an der Seite gelesen, an der das ursprüngliche `com.adobe.idp.Document`-Objekt erstellt wird, wie in diesem Beispiel gezeigt:

```java
     Document doc = new Document(new java.net.URL("file:c:/temp/input.pdf"));
```

Die Datei c:/temp/input.pdf muss sich auf dem Client-Computer (nicht auf dem Servercomputer) befinden. Auf dem Client-Computer wird die URL gelesen und das `com.adobe.idp.Document`-Objekt wurde erstellt.

**Erstellen eines Dokuments basierend auf Inhalt, auf den über eine URL zugegriffen werden kann**

```java
 //Create a Document object based on a java.net.URL object
 URL myURL = new URL("http", "localhost", 8080,"/WebApp/map.pdf");
 
 //Create another Document object
 Document myPDFDocument = new Document(myURL);
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Umgang mit zurückgegebenen Dokumenten  {#handling-returned-documents}

Dienstvorgänge, die ein PDF-Dokument (oder andere Datentypen wie XML-Daten) als Ausgabewert zurückgeben, geben ein `com.adobe.idp.Document`-Objekt zurück . Nachdem Sie ein `com.adobe.idp.Document`-Objekt erhalten haben , können Sie es in die folgenden Formate konvertieren:

* Ein `java.io.File`-Objekt
* Ein `java.io.InputStream`-Objekt
* Ein Byte-Array

Die folgende Codezeile konvertiert ein `com.adobe.idp.Document`-Objekt in ein `java.io.InputStream`-Objekt. Angenommen, `myPDFDocument` stellt ein `com.adobe.idp.Document`-Objekt dar:

```java
     java.io.InputStream resultStream = myDocument.getInputStream();
```

Ebenso können Sie den Inhalt eines `com.adobe.idp.Document` in eine lokale Datei kopieren, indem Sie die folgenden Aufgaben ausführen:

1. Erstellen Sie ein `java.io.File`-Objekt.
1. Rufen Sie die `copyToFile`-Methode des Objekts auf und übergeben Sie das `java.io.File`Objekt.`com.adobe.idp.Document`

Das folgende Codebeispiel kopiert den Inhalt eines `com.adobe.idp.Document`-Objekts in eine Datei namens *AnotherMap.pdf*.

**Kopieren des Inhalts eines Dokumentobjekts in eine Datei**

```java
 File outFile = new File("C:\\AnotherMap.pdf");
 myDocument.copyToFile (outFile);
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Festlegen des Inhaltstyps eines Dokuments  {#determining-the-content-type-of-a-document}

Ermitteln Sie den MIME-Typ eines `com.adobe.idp.Document`-Objekts, indem Sie die `getContentType`-Methode des Objekts aufrufen. `com.adobe.idp.Document` Diese Methode gibt einen Zeichenfolgenwert zurück, der den Inhaltstyp des Objekts `com.adobe.idp.Document` angibt. In der folgenden Tabelle werden die verschiedenen Inhaltstypen beschrieben, die AEM Forms zurückgibt.

<table>
 <thead>
  <tr>
   <th><p>MIME-Typ</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>application/pdf</code></p></td>
   <td><p>PDF-Dokument</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.adobe.xdp+xml</code></p></td>
   <td><p>XML Data Packaging (XDP), das für exportierte XFA-Formulare (XML Forms Architecture) verwendet wird</p></td>
  </tr>
  <tr>
   <td><p><code>text/xml</code></p></td>
   <td><p>Lesezeichen, Anhänge oder andere XML-Dokumente</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.fdf</code></p></td>
   <td><p>Forms Data Format (FDF), das für exportierte Acrobat-Formulare verwendet wird</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.adobe.xfdf</code></p></td>
   <td><p>Forms Data Format (FDF), das für exportierte Acrobat-Formulare verwendet wird</p></td>
  </tr>
  <tr>
   <td><p><code>application/rdf+xml</code></p></td>
   <td><p>Aussagekräftiges Datenformat und XML</p></td>
  </tr>
  <tr>
   <td><p><code>application/octet-stream</code></p></td>
   <td><p>Generisches Datenformat</p></td>
  </tr>
  <tr>
   <td><p><code>NULL</code></p></td>
   <td><p>Nicht angegebener MIME-Typ</p></td>
  </tr>
 </tbody>
</table>

Das folgende Codebeispiel bestimmt den Inhaltstyp eines `com.adobe.idp.Document`-Objekts.

**Festlegen des Inhaltstyps eines Dokumentobjekts**

```java
 //Determine the content type of the Document object
 String ct = myDocument.getContentType();
 System.out.println("The content type of the Document object is " +ct);
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Abschaffung von Dokumentobjekten  {#disposing-document-objects}

Wenn Sie ein `Document`-Objekt nicht mehr benötigen, wird empfohlen, dass Sie es durch Aufrufen der `dispose`-Methode entsorgen. Jedes `Document`-Objekt benötigt einen Dateideskriptor und bis zu 75 MB RAM-Speicherplatz auf der Hostplattform Ihrer Anwendung. Wenn ein `Document`-Objekt nicht bereitgestellt wird, wird es vom Java Garage-Erfassungsprozess bereitgestellt. Durch eine frühere Entsorgung mit der `dispose`-Methode können Sie jedoch den Speicherplatz freigeben, der vom `Document`-Objekt belegt wird.

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek  {#invoking-a-service-using-a-java-client-library}

AEM Forms-Dienstvorgänge können mithilfe der stark typisierten API eines Diensts aufgerufen werden, die als Java-Clientbibliothek bezeichnet wird. Eine *Java-Client-Bibliothek* ist eine Reihe konkreter Klassen, die den Zugriff auf Dienste ermöglichen, die im Dienstcontainer bereitgestellt werden. Sie instanziieren ein Java-Objekt, das den Dienst zum Aufrufen darstellt, anstelle dass ein `InvocationRequest`-Objekt durch die Verwendung der Aufruf-API erstellt wird. Die Aufruf-API wird zum Aufrufen von Prozessen wie langlebigen Prozessen verwendet, die in Workbench erstellt wurden. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Rufen Sie zum Ausführen eines Dienstvorgangs eine Methode auf, die zu dem Java-Objekt gehört. Eine Java-Client-Bibliothek enthält Methoden, die in der Regel Eins-zu-Eins-Serviceoperationen zuordnen. Legen Sie bei Verwendung einer Java-Client-Bibliothek die erforderlichen Verbindungseigenschaften fest. (Siehe [Einstellung von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)

Nachdem Sie die Verbindungseigenschaften festgelegt haben, erstellen Sie ein `ServiceClientFactory`-Objekt, mit dem ein Java-Objekt instanziiert wird, mit dem Sie einen Service aufrufen können. Jeder Dienst, der über eine Java-Client-Bibliothek verfügt, verfügt über ein entsprechendes Client-Objekt. Um zum Beispiel den Repository-Dienst aufzurufen, erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Das `ServiceClientFactory`-Objekt ist für die Verwaltung der Verbindungseinstellungen verantwortlich, die zum Aufrufen von AEM Forms-Diensten erforderlich sind.

Obwohl das Beziehen eines `ServiceClientFactory` normalerweise schnell ist, ist ein gewisser Aufwand erforderlich, wenn die Factory zum ersten Mal verwendet wird. Dieses Objekt ist für die Wiederverwendung optimiert. Wenn Sie mehrere Java-Client-Objekte erstellen, verwenden Sie dasselbe `ServiceClientFactory`-Objekt. Das heißt, erstellen Sie kein separates `ServiceClientFactory`-Objekt für jedes Client-Bibliothekobjekt, das Sie erstellen.

Es gibt eine Benutzer-Manager-Einstellung, die die Lebensdauer der SAML-Assertion steuert, die innerhalb des `com.adobe.idp.Context`-Objekt ist, das das `ServiceClientFactory`-Objekt beeinflusst. Diese Einstellung steuert die Gültigkeitsdauer des Authentifizierungskontexts in AEM Forms, einschließlich aller Aufrufe, die mit der Java-API ausgeführt werden. Standardmäßig beträgt der Zeitraum, in dem ein `ServiceCleintFactory`-Objekt verwendet werden kann, zwei Stunden.

>[!NOTE]
>
>Um zu erläutern, wie ein Dienst mithilfe der Java-API aufgerufen wird, wird der Vorgang `writeResource` aufgerufen. Durch diesen Vorgang wird eine neue Ressource in das Repository eingefügt.

Sie können den Repository-Dienst mithilfe einer Java-Clientbibliothek aufrufen und die folgenden Schritte ausführen:

1. Fügen Sie Client-JAR-Dateien wie „adobe-repository-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Legen Sie die Verbindungseigenschaften fest, die zum Aufrufen eines Dienstes erforderlich sind.
1. Erstellen Sie ein `ServiceClientFactory`-Objekt, indem Sie die statische `ServiceClientFactory`-Methode des Objekts `createInstance` aufrufen und das `java.util.Properties`-Objekt übergeben, das Verbindungseigenschaften enthält.
1. Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Verwenden Sie das `ResourceRepositoryClient`-Objekt, um Repository-Dienstvorgänge aufzurufen.
1. Erstellen Sie ein `RepositoryInfomodelFactoryBean`-Objekt, indem Sie seinen Konstruktor verwenden, und übergeben Sie `null`. Mit diesem Objekt können Sie ein `Resource`-Objekt erstellen, das den Inhalt darstellt, der dem Repository hinzugefügt wird.
1. Erstellen Sie ein `Resource`-Objekt, indem Sie die `RepositoryInfomodelFactoryBean`-Objektmethode `newImage` aufrufen und die folgenden Werte übergeben:

   * Ein eindeutiger ID-Wert durch Angabe von `new Id()`.
   * Ein eindeutiger UUID-Wert durch Angabe von `new Lid()`.
   * Der Name der Ressource. Sie können den Dateinamen der XDP-Datei angeben.

   Wandeln Sie den Rückgabewert in `Resource` um.

1. Erstellen Sie ein `ResourceContent`-Objekt, indem Sie die `RepositoryInfomodelFactoryBean`-Methode des Objekts `newImage` aufrufen und den Rückgabewert in `ResourceContent` konvertieren. Dieses Objekt stellt den Inhalt dar, der dem Repository hinzugefügt wird.
1. Erstellen Sie ein `com.adobe.idp.Document`-Objekt indem Sie ein `java.io.FileInputStream`Objekt übergeben, das die XDP-Datei speichert, die dem Repository hinzugefügt werden soll. (Siehe [Erstellen eines Dokuments basierend auf einem InputStream-Objekt.](invoking-aem-forms-using-java.md#creating-a-document-based-on-an-inputstream-object)
1. hinzufügen Sie den Inhalt des Objekts `com.adobe.idp.Document` auf das Objekt `ResourceContent`, indem Sie die `ResourceContent`-Methode des Objekts aufrufen. `setDataDocument` Übergeben Sie das `com.adobe.idp.Document`-Objekt.
1. Legen Sie den MIME-Typ der XDP-Datei fest, die dem Repository hinzugefügt werden soll, indem Sie die `setMimeType`-Methode des Objekts aufrufen und `application/vnd.adobe.xdp+xml` übergeben.`ResourceContent`
1. hinzufügen Sie den Inhalt des Objekts `ResourceContent` an das Objekt `Resource`, indem Sie das Objekt `Resource` &quot;s `setContent`&quot;aufrufen und das Objekt `ResourceContent` übergeben.
1. Fügen Sie eine Beschreibung der Ressource hinzu, indem Sie die Methode `Resource` des Objekts `setDescription` aufrufen und einen string-Wert übergeben, der eine Beschreibung der Ressource darstellt.
1. Fügen Sie den Formularentwurf in das Repository, indem Sie die Methode `ResourceRepositoryClient` des Objekts `writeResource` aufrufen und die folgenden Werte übergeben:

   * Ein string-Wert, der den Pfad zur Ressourcensammlung angibt, die die neue Ressource enthält
   * Das erstellte `Resource` --Objekt

**Siehe auch**

[Schnellstart (EJB-Modus): Schreiben einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

## Aufruf eines kurzlebigen Prozesses mithilfe der Aufruf-API  {#invoking-a-short-lived-process-using-the-invocation-api}

Sie können einen kurzlebigen Prozess mithilfe der Java Aufruf-API aufrufen. Wenn Sie einen kurzlebigen Prozess mit der Aufruf-API aufrufen, übergeben Sie die erforderlichen Parameterwerte mithilfe eines `java.util.HashMap`-Objekts. Für jeden Parameter, der an einen Dienst übergeben werden soll, rufen Sie die Methode `java.util.HashMap` des Objekts `put` auf und geben Sie das Namen-Wertpaar an, das durch den Dienst erforderlich ist, um den angegebenen Vorgang durchzuführen. Geben Sie den genauen Namen der Parameter an, die zu dem kurzlebigen Prozess gehören.

>[!NOTE]
>
>Informationen zum Aufrufen eines langlebigen Prozesses finden Sie unter [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

In der folgenden Diskussion geht es um die Verwendung der Aufruf-API, um den folgenden kurzlebigen AEM Forms-Prozess namens `MyApplication/EncryptDocument` aufzurufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

### Rufen Sie den kurzlebigen Prozess MyApplication/EncryptDocument mithilfe der Java-Aufruf-API auf {#invoke-the-myapplication-encryptdocument-short-lived-process-using-the-java-invocation-api}

Rufen Sie den kurzlebigen Prozess `MyApplication/EncryptDocument` mithilfe der Java-Aufruf-API auf:

1. Fügen Sie Client-JAR-Dateien wie „adobe-livecycle-client.jar“ in den Klassenpfad Ihres Java-Projekts ein. (Siehe [Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)
1. Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Erstellen Sie ein `ServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Mit einem `ServiceClient` -Objekt können Sie einen Dienstvorgang aufrufen. Es erledigt Aufgaben wie das Auffinden, Versenden und Weiterleiten von Aufrufanforderungen.
1. Erstellen Sie ein Objekt `java.util.HashMap`, indem Sie den Konstruktor verwenden.
1. Rufen Sie die Methode `java.util.HashMap` des `put`-Objekts für jeden Eingabeparameter auf, der an den langlebigen Prozess übergeben erden soll. Da der kurzlebige Prozess `MyApplication/EncryptDocument` einen Eingabeparameter des Typs `Document` erfordert, müssen Sie nur die `put`-Methode einmal aufrufen, wie im folgenden Beispiel gezeigt.

   ```java
    //Create a Map object to store the parameter value for inDoc
    Map params = new HashMap();
    InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf");
    Document inDoc = new Document(inFile);
    params.put("inDoc", inDoc);
   ```

1. Erstellen Sie ein `InvocationRequest`-Objekt, indem Sie die `ServiceClientFactory`-Methode des Objekts `createInvocationRequest` aufrufen und die folgenden Werte übergeben:

   * Ein string-Wert, der den Namen des langlebigen aufzurufenden Prozesses angibt. Um den `MyApplication/EncryptDocument`-Prozess aufzurufen, geben Sie `MyApplication/EncryptDocument` an.
   * Ein string-Wert, der den Prozessvorgangsnamen darstellt. Typischerweise ist der Name eines kurzlebigen Prozessvorgangs `invoke`.
   * Das `java.util.HashMap`-Objekt, das die Parameterwerte enthält, die für den Dienstvorgang erforderlich sind.
   * Ein boolescher Wert, der `true`angibt , wodurch eine synchrone Anforderung erstellt wird (dieser Wert kann für den Aufruf eines kurzlebigen Prozesses verwendet werden).

1. Senden Sie die Aufrufanforderung an den Dienst, indem Sie die Methode `ServiceClient` des Objekts `invoke` aufrufen und das `InvocationRequest`-Objekt übergeben. Die `invoke`-Methode gibt ein `InvocationReponse`-Objekt zurück.

   >[!NOTE]
   >
   >Ein langlebiger Prozess kann aufgerufen werden, indem der Wert `false` als vierter Parameter der `createInvocationRequest`-Methode übergeben wird. Wenn Sie den Wert `false`*übergeben, wird eine asynchrone Anforderung erstellt.*

1. Rufen Sie den der Rückgabewert des Verfahrens ab, indem Sie die Methode `InvocationReponse` des Objekts `getOutputParameter` aufrufen und übergeben Sie einen string-Wert, der den Namen des Ausgangsparameters angibt. Geben Sie in diesem Fall `outDoc` ( `outDoc` ist der Name des Ausgabeparameters für den `MyApplication/EncryptDocument`-Prozess) an. Wandeln Sie den Rückgabewert in `Document` um, wie im folgenden Beispiel gezeigt.

   ```java
    InvocationResponse response = myServiceClient.invoke(request);
    Document encryptDoc = (Document) response.getOutputParameter("outDoc");
   ```

1. Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
1. Rufen Sie die `copyToFile`-Methode des Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. `com.adobe.idp.Document` Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `getOutputParameter`-Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstart: Hervorrufen eines kurzlebigen Prozesses mit der Aufruf-API](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-using-the-invocation-api)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)