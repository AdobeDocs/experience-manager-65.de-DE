---
title: AEM Forms mit der JavaAPI aufrufen
description: Verwenden Sie die AEM Forms Java API für das RMI-Transportprotokoll für die Fernsteuerung, den VM-Transport für den lokalen Aufruf, SOAP für den Fernaufruf, verschiedene Authentifizierungen wie Benutzername und Passwort sowie synchrone und asynchrone Aufrufanforderungen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
exl-id: 036c35c1-1be7-4825-bbb6-ea025e49c6f6
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '5393'
ht-degree: 47%

---

# AEM Forms mit der JavaAPI aufrufen {#invoking-aem-forms-using-the-javaapi}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

AEM Forms kann mithilfe der AEM Forms Java-API aufgerufen werden. Bei Verwendung der AEM Forms Java-API können Sie entweder die Aufruf-API oder die Java-Client-Bibliotheken verwenden. Java-Client-Bibliotheken sind für Dienste wie den Rights Management-Dienst verfügbar. Mit diesen stark typisierten APIs können Sie Java-Anwendungen entwickeln, die AEM Forms aufrufen.

Die Aufruf-API sind Klassen, die sich im `com.adobe.idp.dsc` Paket. Mithilfe dieser Klassen können Sie eine Aufrufanforderung direkt an einen Dienst senden und eine zurückgegebene Aufrufantwort verarbeiten. Verwenden Sie die Aufruf-API, um kurzlebige oder langlebige Prozesse aufzurufen, die mithilfe von Workbench erstellt wurden.

Die empfohlene Methode zum programmgesteuerten Aufrufen eines Dienstes besteht darin, eine Java-Client-Bibliothek zu verwenden, die dem Dienst und nicht der Aufruf-API entspricht. Um beispielsweise den Encryption-Dienst aufzurufen, verwenden Sie die Client-Bibliothek des Encryption-Dienstes. Rufen Sie eine Methode auf, die zum Client-Objekt des Encryption-Dienstes gehört, um einen Vorgang des Encryption-Dienstes durchzuführen. Sie können ein PDF-Dokument mit einem Kennwort verschlüsseln, indem Sie die `EncryptionServiceClient` -Objekt `encryptPDFUsingPassword` -Methode.

Die Java-API unterstützt die folgenden Funktionen:

* RMI-Transportprotokoll für Remote-Aufruf
* VM-Transport für lokalen Aufruf
* SOAP für Remote-Aufruf
* Andere Authentifizierung, z. B. Benutzername und Kennwort
* Synchrone und asynchrone Aufrufanforderungen

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](#including-aem-forms-java-library-files)

[An Menschen orientierte langlebige Prozesse aufrufen](invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[AEM Forms mit Web Services aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md)

[Verbindungseigenschaften festlegen](#setting-connection-properties)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](#invoking-a-service-using-a-java-client-library)

[Aufruf eines kurzlebigen Prozesses mithilfe der Aufruf-API](#invoking-a-short-lived-process-using-the-invocation-api)

[Erstellen einer Java-Web-Anwendung, die einen langlebigen, an Menschen orientierten Prozess aufruft](/help/forms/developing/invoking-human-centric-long-lived.md)

## Einbeziehen von AEM Forms Java-Bibliotheksdateien {#including-aem-forms-java-library-files}

Um mithilfe der Java-API einen AEM Forms-Dienst programmgesteuert aufzurufen, fügen Sie die erforderlichen Bibliotheksdateien (JAR-Dateien) in den Klassenpfad Ihres Java-Projekts ein. Die JAR-Dateien, die Sie in den Klassenpfad Ihrer Clientanwendung einbeziehen, hängen von mehreren Faktoren ab:

* Der aufzurufende AEM Forms-Dienst. Eine Clientanwendung kann einen oder mehrere Dienste aufrufen.
* Der Modus, in dem Sie einen AEM Forms-Dienst aufrufen möchten. Sie können den EJB- oder SOAP-Modus verwenden. (Siehe [Einstellen von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>(Nur Turnkey) Starten Sie den AEM Forms-Server mit dem Befehl `standalone.bat -b <Server IP> -c lc_turnkey.xml` zum Angeben einer Server-IP für EJB

* Der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt wird.

### Dienstspezifische JAR-Dateien {#service-specific-jar-files}

In der folgenden Tabelle sind die JAR-Dateien aufgeführt, die zum Aufrufen der AEM Forms-Dienste erforderlich sind.

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
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-usermanager-client.jar</p></td>
   <td><p>Muss immer im Klassenpfad einer Java-Client-Anwendung enthalten sein.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-utilities.jar</p></td>
   <td><p>Muss immer im Klassenpfad einer Java-Client-Anwendung enthalten sein.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk//client-libs/&lt;app server=""&gt;</p></td>
  </tr>
  <tr>
   <td><p>adobe-applicationmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Application Manager-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-assembler-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Assembler-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-backup-restore-client-sdk.jar</p></td>
   <td><p>Erforderlich zum Aufrufen der Sicherungs- und Wiederherstellungsdienst-API.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-barcodedforms-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Barcoded Forms-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-convertpdf-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Convert PDF-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-distiller-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Distiller-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-docconverter-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des DocConverter-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-contentservices-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Document Management-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-encryption-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Verschlüsselungsdienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-forms-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Forms-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-formdataintegration-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Formulardatenintegrationsdienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generatepdf-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Generate PDF-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generate3dpdf-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Generate 3D PDF-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-jobmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Job Manager-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-output-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Output-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-pdfutility-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des PDF Utilities- oder XMP Utilities-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-reader-extensions-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Acrobat Reader DC Extensions-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-repository-client.jar</p><p>commons-codec-1.3.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Repository-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs\thirdparty</p></td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>adobe-rightsmanagement-client.jar</p></li>
     <li><p>namespace.jar </p></li>
     <li><p>jaxb-api.jar</p></li>
     <li><p>jaxb-impl.jar</p></li>
     <li><p>jaxb-libs.jar</p></li>
     <li><p>jaxb-xjc.jar</p></li>
     <li><p>relaxngDatatype.jar</p></li>
     <li><p>xsdlib.jar</p></li>
    </ul></td>
   <td><p>Erforderlich zum Aufrufen des Rights Management-Dienstes.</p><p>Wenn AEM Forms auf JBoss bereitgestellt wird, schließen Sie alle diese Dateien ein. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p><p>JBoss-spezifischer Bibliotheksordner</p></td>
  </tr>
  <tr>
   <td><p>adobe-signatures-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Signature-Dienstes.</p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-taskmanager-client-sdk.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Task Manager-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-truststore-client.jar</p></td>
   <td><p>Erforderlich zum Aufrufen des Trust Store-Dienstes. </p></td>
   <td><p>&lt;<i>Installationsordner</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
 </tbody>
</table>

### Verbindungsmodus und JAR-Dateien der J2EE-Anwendung {#connection-mode-and-j2ee-application-jar-files}

In der folgenden Tabelle sind die JAR-Dateien aufgeführt, die vom Verbindungsmodus und dem J2EE-Anwendungsserver abhängen, auf dem AEM Forms bereitgestellt wird.

<table>
 <thead>
  <tr>
   <th><p>File</p> </th>
   <th><p>Beschreibung</p> </th>
   <th><p>Ort</p> </th>
  </tr>
 &lt;/thead align="left"&gt;
 <tbody>
  <tr>
   <td>
    <ul>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
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
   <td><p>Wenn AEM Forms im SOAP-Modus aufgerufen wird, schließen Sie diese JAR-Dateien ein.</p> </td>
   <td><p>&lt;<em>Installationsordner</em>&gt;/sdk/client-libs/thirdparty</p> </td>
  </tr>
  <tr>
   <td><p> jboss-client.jar</p> </td>
   <td><p>wenn AEM Forms auf JBoss-Anwendungsserver bereitgestellt wird, schließen Sie diese JAR-Datei ein.</p> <p>Erforderliche Klassen werden vom Classloader nicht gefunden, wenn sich jboss-client.jar und die referenzierten Jars nicht an derselben Stelle befinden.</p> </td>
   <td><p>JBoss-Client-Bibliotheksordner</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Datei nicht einschließen.</p> </td>
  </tr>
  <tr>
   <td><p>wlclient.jar</p> </td>
   <td><p>Wenn AEM Forms auf BEA WebLogic Server® bereitgestellt wird, schließen Sie diese JAR-Datei ein.</p> </td>
   <td><p>WebLogic-spezifischer Bibliotheksordner</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Datei nicht einschließen.</p> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>com.ibm.ws.admin.client_6.1.0.jar</p> </li>
     <li><p>com.ibm.ws.webservices.thinclient_6.1.0.jar</p> </li>
    </ul> </td>
   <td>
    <ul>
     <li><p>Wenn AEM Forms auf WebSphere Application Server bereitgestellt wird, schließen Sie diese JAR-Dateien ein.</p> </li>
     <li><p>(com.ibm.ws.webservices.thinclient_6.1.0.jar ist für den Webdienstaufruf erforderlich).</p> </li>
    </ul> </td>
   <td><p>WebSphere-spezifischer Lib-Ordner (<em>[WAS_HOME]</em>/runtimes)</p> <p>Wenn Sie Ihre Clientanwendung auf demselben J2EE-Anwendungsserver bereitstellen, müssen Sie diese Dateien nicht einschließen.</p> </td>
  </tr>
 </tbody>
</table>

### Aufrufen von Szenarien {#invoking-scenarios}

In der folgenden Tabelle werden die Aufrufszenarien aufgeführt und die erforderlichen JAR-Dateien aufgelistet, um AEM Forms erfolgreich aufzurufen.

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

### JAR-Dateien aktualisieren {#upgrading-jar-files}

Wenn Sie von LiveCycle auf AEM Forms aktualisieren, wird empfohlen, die AEM Forms-JAR-Dateien in den Klassenpfad Ihres Java-Projekts einzuschließen. Wenn Sie beispielsweise Dienste wie den Rights Management-Dienst verwenden, tritt ein Kompatibilitätsproblem auf, wenn Sie keine AEM Forms-JAR-Dateien in Ihren Klassenpfad einbeziehen.

Angenommen, Sie aktualisieren auf AEM Forms. Um eine Java-Anwendung zu verwenden, die den Rights Management-Dienst aufruft, schließen Sie die AEM Forms-Versionen der folgenden JAR-Dateien ein:

* adobe-rightsmanagement-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Festlegen von Verbindungseigenschaften {#setting-connection-properties}

Sie legen Verbindungseigenschaften fest, um AEM Forms bei Verwendung der Java-API aufzurufen. Geben Sie beim Festlegen der Verbindungseigenschaften an, ob Dienste remote oder lokal aufgerufen werden sollen, und geben Sie außerdem den Verbindungsmodus und Authentifizierungswerte an. Authentifizierungswerte sind erforderlich, wenn die Dienstsicherheit aktiviert ist. Wenn die Servicesicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.

Der Verbindungsmodus kann entweder SOAP- oder EJB-Modus sein. Der EJB-Modus verwendet das RMI/IIOP-Protokoll und die Leistung des EJB-Modus ist besser als die Leistung des SOAP-Modus. Der SOAP-Modus wird verwendet, um eine Abhängigkeit vom J2EE-Anwendungsserver zu beseitigen oder wenn sich eine Firewall zwischen AEM Forms und der Clientanwendung befindet. Der SOAP-Modus verwendet das HTTPS-Protokoll als zugrunde liegenden Transport und kann über Firewall-Grenzen hinweg kommunizieren. Wenn weder eine Abhängigkeit vom J2EE-Anwendungsserver noch eine Firewall ein Problem darstellt, wird empfohlen, den EJB-Modus zu verwenden.

Um einen AEM Forms-Dienst erfolgreich aufzurufen, legen Sie die folgenden Verbindungseigenschaften fest:

* **DSC_DEFAULT_EJB_ENDPOINT:** Wenn Sie den EJB-Verbindungsmodus verwenden, stellt dieser Wert die URL des J2EE-Anwendungsservers dar, auf dem AEM Forms bereitgestellt wird. Um AEM Forms remote aufzurufen, geben Sie den Namen des J2EE-Anwendungsservers an, auf dem AEM Forms bereitgestellt wird. Wenn sich Ihre Client-Anwendung auf demselben J2EE-Anwendungsserver befindet, können Sie `localhost`angeben. Geben Sie abhängig davon, auf welchem J2EE-Anwendungs-Server AEM Forms bereitgestellt ist, einen der folgenden Werte an:

   * JBoss: `https://<ServerName>:8080 (default port)`
   * WebSphere: `iiop://<ServerName>:2809 (default port)`
   * WebLogic: `t3://<ServerName>:7001 (default port)`

* **DSC_DEFAULT_SOAP_ENDPOINT**: Wenn Sie den SOAP-Verbindungsmodus verwenden, stellt dieser Wert den Endpunkt dar, an den eine Aufrufanforderung gesendet wird. Um AEM Forms remote aufzurufen, geben Sie den Namen des J2EE-Anwendungsservers an, auf dem AEM Forms bereitgestellt wird. Wenn sich Ihre Client-Anwendung auf demselben J2EE-Anwendungsserver befindet, können Sie `localhost`angeben (z. B. `http://localhost:8080`.)

   * Der Portwert `8080` gilt, wenn die J2EE-Anwendung JBoss ist. Wenn der J2EE-Anwendungsserver IBM WebSphere ist, verwenden Sie Port `9080`. Wenn der J2EE-Anwendungsserver WebLogic ist, verwenden Sie Port `7001`. (Diese Werte sind standardmäßige Anschlusswerte. Wenn Sie den Anschlusswert ändern, verwenden Sie die entsprechende Anschlussnummer.)

* **DSC_TRANSPORT_PROTOCOL**: Wenn Sie den EJB-Verbindungsmodus verwenden, geben Sie `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` für diesen Wert an. Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL` an.
* **DSC_SERVER_TYPE**: Der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt wird. Gültige Werte sind `JBoss`, `WebSphere`, `WebLogic`.

   * Wenn Sie diese Verbindungseigenschaft auf `WebSphere` setzen, wird der Wert `java.naming.factory.initial` auf `com.ibm.ws.naming.util.WsnInitCtxFactory` gesetzt.
   * Wenn Sie diese Verbindungseigenschaft auf `WebLogic` setzen, wird der Wert `java.naming.factory.initial` auf `weblogic.jndi.WLInitialContextFactory` gesetzt.
   * Wenn Sie diese Verbindungseigenschaft auf `JBoss` setzen, wird der Wert `java.naming.factory.initial` ebenfalls auf `org.jnp.interfaces.NamingContextFactory` gesetzt.
   * Sie können die Eigenschaft `java.naming.factory.initial` auf einen Wert setzen, der Ihren Anforderungen entspricht, wenn Sie die Standardwerte nicht verwenden möchten.

  >[!NOTE]
  >
  >Anstatt eine Zeichenfolge zu verwenden, um die `DSC_SERVER_TYPE` Verbindungseigenschaft zu setzen, können Sie ein statisches Mitglied der `ServiceClientFactoryProperties` Klasse verwenden. Die folgenden Werte können verwendet werden: `ServiceClientFactoryProperties.DSC_WEBSPHERE_SERVER_TYPE`, `ServiceClientFactoryProperties.DSC_WEBLOGIC_SERVER_TYPE`, oder `ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE`.

* **DSC_CREDENTIAL_USERNAME:** Gibt den Benutzernamen der AEM Formulare an. Damit ein Benutzer erfolgreich einen AEM Forms-Dienst aufrufen kann, benötigt er die Rolle &quot;Dienstbenutzer&quot;. Ein Benutzer kann auch über eine andere Rolle verfügen, die die Berechtigung Dienst aufrufen enthält. Andernfalls wird eine Ausnahme ausgelöst, wenn versucht wird, einen Dienst aufzurufen. Wenn die Servicesicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.
* **DSC_CREDENTIAL_PASSWORD:** Gibt den entsprechenden Kennwortwert an. Wenn die Service-Sicherheit jedoch deaktiviert ist, müssen keine Authentifizierungswerte angegeben werden.
* **DSC_REQUEST_TIMEOUT:** Das Standardlimit für Anforderungszeitlimits für die SOAP-Anforderung beträgt 1200000 Millisekunden (20 Minuten). Manchmal kann es länger dauern, bis eine Anfrage abgeschlossen ist. Beispielsweise kann eine SOAP-Anforderung, die eine große Menge von Datensätzen abruft, eine längere Zeitüberschreitungsbegrenzung erfordern. Mit `ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT` können Sie das Zeitlimit für Anforderungsaufrufe für die SOAP-Anforderungen erhöhen.

  **Hinweis**: Nur SOAP-basierte Aufrufe unterstützen die DSC_REQUEST_TIMEOUT Eigenschaft.

Führen Sie die folgenden Aufgaben aus, um Verbindungseigenschaften festzulegen:

1. Erstellen Sie ein Objekt `java.util.Properties`, indem Sie den Konstruktor verwenden.
1. Um die `DSC_DEFAULT_EJB_ENDPOINT` Verbindungseigenschaft, rufen Sie die `java.util.Properties` -Objekt `setProperty` -Methode verwenden und die folgenden Werte übergeben:

   * Der `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT`-Enumerationswert
   * Ein string-Wert, der die URL des J2EE-Anwendungsservers angibt, der AEM Forms hostet

   >[!NOTE]
   >
   >Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie den Aufzählungswert `ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT` anstelle des Aufzählungswerts `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` an.

1. Um die `DSC_TRANSPORT_PROTOCOL` Verbindungseigenschaft, rufen Sie die `java.util.Properties` -Objekt `setProperty` -Methode verwenden und die folgenden Werte übergeben:

   * Der Aufzählungswert `ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL`
   * Der Aufzählungswert `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL`

   >[!NOTE]
   >
   >Wenn Sie den SOAP-Verbindungsmodus verwenden, geben Sie den Aufzählungswert `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL` anstelle des Aufzählungswerts `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` an.

1. Um die `DSC_SERVER_TYPE` Verbindungseigenschaft, rufen Sie die `java.util.Properties` -Objekt `setProperty` -Methode verwenden und die folgenden Werte übergeben:

   * Der Aufzählungswert `ServiceClientFactoryProperties.DSC_SERVER_TYPE`
   * Ein string-Wert, der den J2EE-Anwendungs-Server angibt, auf dem AEM Forms gehostet wird. (wenn beispielsweise AEM Forms auf bereitgestellt wird, geben Sie `JBoss`JBoss an.)

      1. Um die `DSC_CREDENTIAL_USERNAME` Verbindungseigenschaft, rufen Sie die `java.util.Properties` -Objekt `setProperty` -Methode verwenden und die folgenden Werte übergeben:

   * Der Aufzählungswert `ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME`
   * Ein Zeichenfolgenwert, der den Benutzernamen angibt, der zum Aufrufen von AEM Forms erforderlich ist

      1. Um die `DSC_CREDENTIAL_PASSWORD` Verbindungseigenschaft, rufen Sie die `java.util.Properties` -Objekt `setProperty` -Methode verwenden und die folgenden Werte übergeben:

   * Der Aufzählungswert `ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD`
   * Ein Zeichenfolgenwert, der den entsprechenden Kennwortwert angibt.

**Einstellen des EJB-Verbindungsmodus für JBoss**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, das auf JBoss bereitgestellt wird und den EJB-Verbindungsmodus verwendet.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "https://<hostname>:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DOCUMENT_HTTP_ENDPOINT,"https://<hostname>:8080");
```

**Einrichten des EJB-Verbindungsmodus für WebLogic**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, das auf WebLogic bereitgestellt wird und den EJB-Verbindungsmodus verwendet.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "t3://localhost:7001");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebLogic");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**EJB-Verbindungsmodus für WebSphere festlegen**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften festgelegt, um AEM Forms aufzurufen, das auf WebSphere bereitgestellt wird und den EJB-Verbindungsmodus verwendet.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "iiop://localhost:2809");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebSphere");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**SOAP-Verbindungsmodus festlegen**

Im folgenden Java-Codebeispiel werden Verbindungseigenschaften im SOAP-Modus festgelegt, um AEM Forms aufzurufen, der auf JBoss bereitgestellt wird.

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
>Wenn Sie den SOAP-Verbindungsmodus auswählen, stellen Sie sicher, dass Sie zusätzliche JAR-Dateien in den Klassenpfad Ihrer Client-Anwendung aufnehmen.

**Verbindungseigenschaften festlegen, wenn die Dienstsicherheit deaktiviert ist**

Im folgenden Java-Codebeispiel werden die Verbindungseigenschaften festgelegt, die zum Aufrufen von AEM Forms, das auf dem JBoss-Anwendungsserver bereitgestellt wird, und bei deaktivierter Dienstsicherheit erforderlich sind.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
```

>[!NOTE]
>
>Alle mit der Programmierung mit AEM Forms verknüpften Java-Schnellstarts zeigen sowohl EJB- als auch SOAP-Verbindungseinstellungen an.

**SOAP-Verbindungsmodus mit benutzerdefiniertem Zeitlimit für Anfragen festlegen**

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT, "1800000"); // Request timeout limit 30 Minutes
```

**Verwenden eines Context-Objekts zum Aufrufen von AEM Forms**

Sie können ein Objekt. `com.adobe.idp.Context` verwenden, um einen AEM Forms-Dienst mit einem authentifizierten Benutzer aufzurufen (das Objekt `com.adobe.idp.Context` steht für einen authentifizierten Benutzer). Wenn Sie ein `com.adobe.idp.Context`-Objekt verwenden, müssen Sie die Eigenschaften `DSC_CREDENTIAL_USERNAME` oder `DSC_CREDENTIAL_PASSWORD` nicht einstellen. Sie können eine `com.adobe.idp.Context` -Objekt bei der Authentifizierung von Benutzern mithilfe der `AuthenticationManagerServiceClient` -Objekt `authenticate` -Methode.

Die `authenticate`-Methode gibt ein Objekt `AuthResult` zurück, das das Ergebnis der Authentifizierung enthält. Sie können ein `com.adobe.idp.Context`-Objekt erstellen, indem Sie seinen Konstruktor aufrufen. Rufen Sie dann die `com.adobe.idp.Context` -Objekt `initPrincipal` -Methode und übergeben Sie `AuthResult` -Objekt, wie im folgenden Code gezeigt:

```java
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
```

Anstatt die `DSC_CREDENTIAL_USERNAME` oder `DSC_CREDENTIAL_PASSWORD` -Eigenschaften, können Sie die `ServiceClientFactory` -Objekt `setContext` -Methode und übergeben Sie `com.adobe.idp.Context` -Objekt. Wenn Sie einen AEM Forms-Benutzer zum Aufrufen eines Dienstes verwenden, stellen Sie sicher, dass ihm die Rolle mit dem Namen `Services User` , die zum Aufrufen eines AEM Forms-Dienstes erforderlich ist.

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
>Ausführliche Informationen zur Authentifizierung eines Benutzers finden Sie unter [Benutzer authentifizieren](/help/forms/developing/users.md#authenticating-users).

### Aufrufen von Szenarien {#invoking_scenarios-1}

Die folgenden Aufrufszenarien werden in diesem Abschnitt erläutert:

* Eine Client-Anwendung, die in einer eigenen Java Virtual Machine (JVM) ausgeführt wird, ruft eine eigenständige AEM Forms-Instanz auf.
* Eine Client-Anwendung, die in ihrer eigenen JVM ausgeführt wird, ruft geclusterte AEM Forms-Instanzen auf.

### Clientanwendung, die eine eigenständige AEM Forms-Instanz aufruft {#client-application-invoking-a-stand-alone-aem-forms-instance}

Das folgende Diagramm zeigt eine Client-Anwendung, die in ihrer eigenen JVM ausgeführt wird und eine eigenständige AEM Forms-Instanz aufruft.

In diesem Szenario wird eine Client-Anwendung in ihrer eigenen JVM ausgeführt und ruft AEM Forms-Dienste auf.

>[!NOTE]
>
>Dieses Szenario ist das Aufrufszenario, auf dem alle Schnellstarts basieren.

### Clientanwendung, die Clusterinstanzen von AEM Forms aufruft {#client-application-invoking-clustered-aem-forms-instances}

Das folgende Diagramm zeigt eine Client-Anwendung, die in ihrer eigenen JVM ausgeführt wird und AEM Forms-Instanzen in einem Cluster aufruft.

Dieses Szenario ähnelt einer Client-Anwendung, die eine eigenständige AEM Forms-Instanz aufruft. Die Anbieter-URL ist jedoch anders. Wenn eine Client-Anwendung eine Verbindung zu einem bestimmten J2EE-Anwendungsserver herstellen möchte, muss die Anwendung die URL ändern, um auf den spezifischen J2EE-Anwendungsserver zu verweisen.

Die Referenzierung eines bestimmten J2EE-Anwendungsservers wird nicht empfohlen, da die Verbindung zwischen der Clientanwendung und AEM Forms beendet wird, wenn der Anwendungsserver beendet wird. Es wird empfohlen, dass die Anbieter-URL auf einen JNDI-Manager auf Zellenebene verweist und nicht auf einen bestimmten J2EE-Anwendungsserver.

Client-Anwendungen, die den SOAP-Verbindungsmodus verwenden, können den HTTP-Lastenausgleichsanschluss für den Cluster verwenden. Clientanwendungen, die den EJB-Verbindungsmodus verwenden, können eine Verbindung zum EJB-Port eines bestimmten J2EE-Anwendungsservers herstellen. Diese Aktion verarbeitet den Lastenausgleich zwischen Clusterknoten.

**WebSphere**

Das folgende Beispiel zeigt den Inhalt einer Datei &quot;jndi.properties&quot;, die verwendet wird, um eine Verbindung mit AEM Forms herzustellen, die auf WebSphere bereitgestellt wird.

```ini
 java.naming.factory.initial=com.ibm.websphere.naming.
 WsnInitialContextFactory
 java.naming.provider.url=corbaloc::appserver1:9810,:appserver2:9810
```

**WebLogic**

Das folgende Beispiel zeigt den Inhalt einer Datei &quot;jndi.properties&quot;, die verwendet wird, um eine Verbindung mit AEM Forms herzustellen, die auf WebLogic bereitgestellt wird.

```ini
 java.naming.factory.initial=weblogic.jndi.WLInitialContextFactory
 java.naming.provider.url=t3://appserver1:8001, appserver2:8001
```

**JBoss**

Das folgende Beispiel zeigt den Inhalt einer Datei &quot;jndi.properties&quot;, die verwendet wird, um eine Verbindung mit AEM Forms herzustellen, die auf JBoss bereitgestellt wird.

```ini
 java.naming.factory.initial= org.jnp.interfaces.NamingContextFactory
 java.naming.provider.url= jnp://appserver1:1099, appserver2:1099,
 appserver3:1099
```

>[!NOTE]
>
>Wenden Sie sich an Ihren Administrator, um den J2EE-Anwendungsservernamen und die Anschlussnummer zu ermitteln.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Übergeben von Daten an AEM Forms-Dienste mithilfe der Java-API {#passing-data-to-aem-forms-services-using-the-java-api}

Vorgänge des AEM Forms-Dienstes verbrauchen normalerweise PDF-Dokumente oder erstellen sie. Beim Aufrufen eines Dienstes ist es manchmal erforderlich, ein PDF-Dokument (oder andere Dokumenttypen wie XML-Daten) an den Dienst zu übergeben. Ebenso ist es manchmal erforderlich, ein vom Dienst zurückgegebenes PDF-Dokument zu verarbeiten. Die Java-Klasse, mit der Sie Daten an und von AEM Forms-Diensten übertragen können, ist `com.adobe.idp.Document`.

AEM Forms-Dienste akzeptieren ein PDF-Dokument nicht als andere Datentypen, wie z. B. ein Objekt `java.io.InputStream` oder ein Byte-Array. Ein `com.adobe.idp.Document`-Objekt kann auch verwendet werden, um andere Datentypen, z. B. XML-Daten, an Dienste zu übergeben.

Das Objekt `com.adobe.idp.Document` ist ein serialisierbarer Java-Typ, sodass es über einen RMI-Aufruf übergeben werden kann. Die empfangende Seite kann zusammengefasst werden (gleicher Host, derselbe Klassenlader), lokal (gleicher Host, unterschiedlicher Klassenlader) oder remote (anderer Host). Die Übergabe von Dokumentinhalten ist für jeden Fall optimiert. Wenn sich beispielsweise der Absender und der Empfänger auf demselben Host befinden, wird der Inhalt über ein lokales Dateisystem übergeben. (In einigen Fällen können Dokumente im Speicher übergeben werden.)

Abhängig von der Objektgröße `com.adobe.idp.Document`, werden die Daten innerhalb des Objekts `com.adobe.idp.Document` befördert oder im Dateisystem des Servers gespeichert. Alle temporären Speicherressourcen, die vom Objekt `com.adobe.idp.Document` belegt sind, werden nach der Entsorgung von `com.adobe.idp.Document` automatisch entfernt. (Siehe [Dokumentobjekte entsorgen](invoking-aem-forms-using-java.md#disposing-document-objects).)

Manchmal ist es erforderlich, den Inhaltstyp eines `com.adobe.idp.Document`-Objekts zu kennen, bevor Sie es an einen Dienst übergeben können. Wenn für einen Vorgang beispielsweise ein bestimmter Inhaltstyp erforderlich ist, z. B. `application/pdf`, wird empfohlen, den Inhaltstyp zu bestimmen. (Siehe [Festlegen des Inhaltstyps eines Dokuments](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document).)

Das Objekt `com.adobe.idp.Document` versucht, den Inhaltstyp anhand der bereitgestellten Daten zu ermitteln. Wenn der Inhaltstyp nicht aus den bereitgestellten Daten abgerufen werden kann (z. B. wenn die Daten als Byte-Array bereitgestellt wurden), legen Sie den Inhaltstyp fest. Um den Inhaltstyp festzulegen, rufen Sie die `com.adobe.idp.Document` -Objekt `setContentType` -Methode. (Siehe [Festlegen des Inhaltstyps eines Dokuments](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document))

Wenn Begleitdateien sich im selben Dateisystem befinden, ist das Erstellen eines `com.adobe.idp.Document` schneller. Wenn sich Begleitdateien auf Remote-Dateisystemen befinden, muss ein Kopiervorgang ausgeführt werden, der die Leistung beeinträchtigt.

Eine Anwendung kann sowohl `com.adobe.idp.Document` als auch `org.w3c.dom.Document` Datentypen enthalten. Stellen Sie jedoch sicher, dass Sie den Datentyp `org.w3c.dom.Document` vollständig qualifizieren. Informationen zum Konvertieren eines `org.w3c.dom.Document`-Objekts in ein `com.adobe.idp.Document`-Objekt finden Sie unter [Schnellstart (EJB-Modus): Formulare mit flexiblen Layouts mithilfe der Java-API vorbefüllen](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api).

>[!NOTE]
>
>Um einen Speicherverlust in WebLogic bei der Verwendung eines `com.adobe.idp.Document`-Objekts zu vermeiden, lesen Sie die Dokumentinformationen in Schritten von 2048 Byte oder weniger. Beispielsweise liest der folgende Code die Dokumentinformationen in Blöcken von 2048 Byte:

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

### Dokumente erstellen {#creating-documents}

Erstellen Sie ein `com.adobe.idp.Document`-Objekt, bevor Sie einen Dienstvorgang aufrufen, für den ein PDF-Dokument (oder andere Dokumenttypen) als Eingabewert erforderlich sind. Die Klasse `com.adobe.idp.Document` stellt Konstruktoren bereit, mit denen Sie ein Dokument aus den folgenden Inhaltstypen erstellen können:

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

#### Erstellen eines Dokuments basierend auf einem anderen Dokument {#creating-a-document-based-on-another-document}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einem anderen `com.adobe.idp.Document`-Objekt basiert.

**Erstellen eines Dokumentobjekts, das auf einem anderen Dokument basiert**

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

#### Auf einer Datei basierendes Dokument erstellen {#creating-a-document-based-on-a-file}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf eine PDF-Datei *map.pdf basiert*. Diese Datei befindet sich im Stammverzeichnis der C-Festplatte. Dieser Konstruktor versucht, den MIME-Inhaltstyp des `com.adobe.idp.Document`-Objekts mithilfe der Dateinamenerweiterung festzulegen.

Der `com.adobe.idp.Document`Konstruktor, der ein `java.io.File`-Objekt akzeptiert, akzeptiert auch einen Booleschen Parameter. Wenn Sie diese Parameter auf `true` setzen, löscht das `com.adobe.idp.Document`-Objekt die Datei. Diese Aktion bedeutet, dass Sie die Datei nicht entfernen müssen, nachdem Sie sie an den `com.adobe.idp.Document`-Konstruktor übergeben haben.

Wenn Sie diesen Parameter auf `false` setzen, behalten Sie den Besitz dieser Datei bei. Das Einstellen dieses Parameters auf `true` ist effizienter. Der Grund ist, dass das `com.adobe.idp.Document`-Objekt die Datei direkt in den lokalen verwalteten Bereich verschieben kann, anstatt sie zu kopieren (was langsamer ist).

**Erstellen eines Dokumentobjekts basierend auf einer PDF-Datei**

```java
 //Create a Document object based on the map.pdf source file
 File mySourceMap = new File("C:\\map.pdf");
 Document myPDFDocument = new Document(mySourceMap,true);
```

#### Erstellen eines Dokuments basierend auf einem InputStream-Objekt {#creating-a-document-based-on-an-inputstream-object}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einem`java.io.InputStream`-Objekt basiert.

**Erstellen eines Dokuments basierend auf einem InputStream-Objekt**

```java
 //Create a Document object based on an InputStream object
 InputStream is = new FileInputStream("C:\\Map.pdf");
 Document myPDFDocument = new Document(is);
```

#### Erstellen eines Dokuments basierend auf Inhalten, auf die über eine URL zugegriffen werden kann {#creating-a-document-based-on-content-accessible-from-an-url}

Im folgenden Codebeispiel wird ein `com.adobe.idp.Document`-Objekt erstellt, das auf einer PDF-Datei *map.pdf basiert*. Diese Datei befindet sich in einer Web-Anwendung namens `WebApp`, die auf `localhost` läuft. Dieser Konstruktor versucht, die `com.adobe.idp.Document` den MIME-Inhaltstyp des Objekts unter Verwendung des Inhaltstyps, der mit dem URL-Protokoll zurückgegeben wird.

Die URL des `com.adobe.idp.Document`-Objekts wird immer an der Seite gelesen, an der das ursprüngliche `com.adobe.idp.Document`-Objekt erstellt wird, wie in diesem Beispiel gezeigt:

```java
     Document doc = new Document(new java.net.URL("file:c:/temp/input.pdf"));
```

Die Datei c:/temp/input.pdf muss sich auf dem Client-Computer (nicht auf dem Servercomputer) befinden. Auf dem Client-Computer wird die URL gelesen und das `com.adobe.idp.Document`-Objekt wurde erstellt.

**Erstellen eines Dokuments basierend auf Inhalten, auf die über eine URL zugegriffen werden kann**

```java
 //Create a Document object based on a java.net.URL object
 URL myURL = new URL("http", "localhost", 8080,"/WebApp/map.pdf");
 
 //Create another Document object
 Document myPDFDocument = new Document(myURL);
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Umgang mit zurückgegebenen Dokumenten {#handling-returned-documents}

Dienstvorgänge, die ein PDF-Dokument (oder andere Datentypen wie XML-Daten) als Ausgabewert zurückgeben, geben ein `com.adobe.idp.Document`-Objekt zurück. Nachdem Sie ein `com.adobe.idp.Document`-Objekt erhalten haben, können Sie es in die folgenden Formate konvertieren:

* Ein `java.io.File`-Objekt
* Ein `java.io.InputStream`-Objekt
* Ein Byte-Array

Die folgende Codezeile konvertiert ein `com.adobe.idp.Document`-Objekt in ein `java.io.InputStream`-Objekt. Angenommen, dass `myPDFDocument` ein `com.adobe.idp.Document`-Objekt darstellt:

```java
     java.io.InputStream resultStream = myDocument.getInputStream();
```

Ebenso können Sie den Inhalt eines `com.adobe.idp.Document` in eine lokale Datei kopieren, indem Sie die folgenden Aufgaben ausführen:

1. Erstellen Sie ein `java.io.File`-Objekt.
1. Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf und übergeben Sie das `java.io.File`-Objekt.

Das folgende Codebeispiel kopiert den Inhalt eines `com.adobe.idp.Document`-Objekts in eine Datei namens *AnotherMap.pdf*.

**Kopieren des Inhalts eines Dokumentobjekts in eine Datei**

```java
 File outFile = new File("C:\\AnotherMap.pdf");
 myDocument.copyToFile (outFile);
```

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindungseigenschaften festlegen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Festlegen des Inhaltstyps eines Dokuments {#determining-the-content-type-of-a-document}

Bestimmen Sie den MIME-Typ eines `com.adobe.idp.Document` -Objekt durch Aufrufen der `com.adobe.idp.Document` -Objekt `getContentType` -Methode. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Inhaltstyp des Objekts `com.adobe.idp.Document` angibt. In der folgenden Tabelle werden die verschiedenen Inhaltstypen beschrieben, die AEM Forms zurückgibt.

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
   <td><p>Forms Data Format (XFDF), das für exportierte Acrobat-Formulare verwendet wird</p></td>
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

### Abschaffung von Dokumentobjekten {#disposing-document-objects}

Wenn Sie ein `Document`-Objekt nicht mehr benötigen, wird empfohlen, dass Sie es durch Aufrufen der `dispose`-Methode entsorgen. Jeder `Document` -Objekt verbraucht einen Dateideskriptor und bis zu 75 MB RAM-Speicherplatz auf der Hostplattform Ihrer Anwendung. Wenn ein `Document`-Objekt nicht bereitgestellt wird, wird es vom Java Garage-Erfassungsprozess bereitgestellt. Durch eine frühere Entsorgung mit der `dispose`-Methode können Sie jedoch den Speicherplatz freigeben, der vom `Document`-Objekt belegt wird.

**Siehe auch**

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Aufrufen eines Dienstes mithilfe einer Java-Client-Bibliothek {#invoking-a-service-using-a-java-client-library}

AEM Forms-Dienstvorgänge können über die stark typisierte API eines Dienstes, die als Java-Client-Bibliothek bezeichnet wird, aufgerufen werden. A *Java-Client-Bibliothek* ist eine Reihe konkreter Klassen, die Zugriff auf Dienste bieten, die im Dienstcontainer bereitgestellt werden. Sie instanziieren ein Java-Objekt, das den Dienst zum Aufrufen darstellt, anstelle dass ein `InvocationRequest`-Objekt durch die Verwendung der Aufruf-API erstellt wird. Die Aufruf-API wird zum Aufrufen von Prozessen wie langlebigen Prozessen verwendet, die in Workbench erstellt wurden. (Siehe [An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Um einen Dienstvorgang auszuführen, rufen Sie eine Methode auf, die zum Java-Objekt gehört. Eine Java-Client-Bibliothek enthält Methoden, die normalerweise Eins-zu-Eins-Dienstvorgänge zuordnen. Legen Sie bei Verwendung einer Java-Client-Bibliothek die erforderlichen Verbindungseigenschaften fest. (Siehe [Festlegen von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)

Nachdem Sie die Verbindungseigenschaften festgelegt haben, erstellen Sie ein `ServiceClientFactory`-Objekt, mit dem ein Java-Objekt instanziiert wird, mit dem Sie einen Service aufrufen können. Jeder Dienst, der über eine Java-Client-Bibliothek verfügt, verfügt über ein entsprechendes Client-Objekt. Um zum Beispiel den Repository-Dienst aufzurufen, erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Das `ServiceClientFactory`-Objekt ist für die Verwaltung der Verbindungseinstellungen verantwortlich, die zum Aufrufen von AEM Forms-Diensten erforderlich sind.

Obwohl das Beziehen eines `ServiceClientFactory` normalerweise schnell ist, ist ein gewisser Aufwand erforderlich, wenn die Factory zum ersten Mal verwendet wird. Dieses Objekt ist für die Wiederverwendung optimiert. Wenn Sie mehrere Java-Client-Objekte erstellen, verwenden Sie dasselbe `ServiceClientFactory`-Objekt. Das heißt, erstellen Sie kein separates `ServiceClientFactory`-Objekt für jedes Client-Bibliothekobjekt, das Sie erstellen.

Es gibt eine Benutzer-Manager-Einstellung, die die Lebensdauer der SAML-Assertion steuert, die innerhalb des `com.adobe.idp.Context`-Objekt ist, das das `ServiceClientFactory`-Objekt beeinflusst. Diese Einstellung steuert die Gültigkeitsdauer des Authentifizierungskontexts in AEM Forms, einschließlich aller Aufrufe, die mit der Java-API ausgeführt werden. Standardmäßig beträgt der Zeitraum, in dem ein `ServiceCleintFactory`-Objekt verwendet werden kann, zwei Stunden.

>[!NOTE]
>
>Um zu erklären, wie ein Dienst mithilfe der Java-API aufgerufen wird, muss der Repository-Dienst die `writeResource` -Vorgang aufgerufen wird. Durch diesen Vorgang wird eine neue Ressource in das Repository eingefügt.

Sie können den Repository-Dienst mithilfe einer Java-Client-Bibliothek aufrufen, indem Sie die folgenden Schritte ausführen:

1. Schließen Sie Client-JAR-Dateien wie adobe-repository-client.jar in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehen von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Legen Sie Verbindungseigenschaften fest, die zum Aufrufen eines Dienstes erforderlich sind.
1. Erstellen Sie eine `ServiceClientFactory` -Objekt durch Aufrufen der `ServiceClientFactory` Statisches Objekt `createInstance` -Methode und Übergabe der `java.util.Properties` -Objekt, das Verbindungseigenschaften enthält.
1. Erstellen Sie ein `ResourceRepositoryClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Verwenden Sie das `ResourceRepositoryClient`-Objekt, um Repository-Dienstvorgänge aufzurufen.
1. Erstellen Sie ein `RepositoryInfomodelFactoryBean`-Objekt, indem Sie seinen Konstruktor verwenden, und übergeben Sie `null`. Mit diesem Objekt können Sie ein `Resource`-Objekt erstellen, das den Inhalt darstellt, der dem Repository hinzugefügt wird.
1. Erstellen Sie eine `Resource` -Objekt durch Aufrufen der `RepositoryInfomodelFactoryBean` -Objekt `newImage` -Methode verwenden und die folgenden Werte übergeben:

   * Ein eindeutiger ID-Wert durch Angabe von `new Id()`.
   * Ein eindeutiger UUID-Wert durch Angabe von `new Lid()`.
   * Der Name der Ressource. Sie können den Dateinamen der XDP-Datei angeben.

   Wandeln Sie den Rückgabewert in `Resource` um.

1. Erstellen Sie eine `ResourceContent` -Objekt durch Aufrufen der `RepositoryInfomodelFactoryBean` -Objekt `newImage` Methode und Konvertieren des Rückgabewerts in `ResourceContent`. Dieses Objekt stellt den Inhalt dar, der dem Repository hinzugefügt wird.
1. Erstellen Sie ein `com.adobe.idp.Document`-Objekt indem Sie ein `java.io.FileInputStream`Objekt übergeben, das die XDP-Datei speichert, die dem Repository hinzugefügt werden soll. (Siehe [Erstellen eines Dokuments basierend auf einem InputStream-Objekt](invoking-aem-forms-using-java.md#creating-a-document-based-on-an-inputstream-object).)
1. Inhalt der `com.adobe.idp.Document` -Objekt `ResourceContent` -Objekt durch Aufrufen der `ResourceContent` -Objekt `setDataDocument` -Methode. Übergeben Sie das `com.adobe.idp.Document`-Objekt.
1. Legen Sie den MIME-Typ der XDP-Datei fest, die zum Repository hinzugefügt werden soll, indem Sie die `ResourceContent` -Objekt `setMimeType` Methode und Übergabe `application/vnd.adobe.xdp+xml`.
1. Inhalt der `ResourceContent` -Objekt `Resource` -Objekt durch Aufrufen der `Resource` -Objekt `setContent` -Methode und Übergabe der `ResourceContent` -Objekt.
1. Fügen Sie durch Aufrufen der `Resource` -Objekt `setDescription` -Methode verwenden und einen string -Wert übergeben, der eine Beschreibung der Ressource darstellt.
1. Fügen Sie den Formularentwurf zum Repository hinzu, indem Sie die `ResourceRepositoryClient` -Objekt `writeResource` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string-Wert, der den Pfad zur Ressourcensammlung angibt, die die neue Ressource enthält
   * Das erstellte `Resource`-Objekt

**Siehe auch**

[Schnellstart (EJB-Modus): Schreiben einer Ressource mithilfe der Java-API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[AEM Forms mit der JavaAPI aufrufen](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

## Aufrufen eines kurzlebigen Prozesses mithilfe der Aufruf-API {#invoking-a-short-lived-process-using-the-invocation-api}

Sie können einen kurzlebigen Prozess mithilfe der Java-Aufruf-API aufrufen. Wenn Sie einen kurzlebigen Prozess mit der Aufruf-API aufrufen, übergeben Sie die erforderlichen Parameterwerte mithilfe eines `java.util.HashMap`-Objekts. Rufen Sie für jeden Parameter, der an einen Dienst übergeben werden soll, die `java.util.HashMap` -Objekt `put` -Methode und geben Sie das Name-Wert-Paar an, das vom Dienst für die Ausführung des angegebenen Vorgangs benötigt wird. Geben Sie den genauen Namen der Parameter an, die zum kurzlebigen Prozess gehören.

>[!NOTE]
>
>Informationen zum Aufrufen eines langlebigen Prozesses finden Sie unter [Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

In der folgenden Diskussion geht es um die Verwendung der Aufruf-API, um den folgenden kurzlebigen AEM Forms-Prozess namens `MyApplication/EncryptDocument` aufzurufen.

>[!NOTE]
>
>Dieser Prozess basiert nicht auf einem vorhandenen AEM Forms-Prozess. Um dem Codebeispiel zu folgen, erstellen Sie einen Prozess mit dem Namen `MyApplication/EncryptDocument` in Workbench. (Siehe [Verwenden von Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

Wenn dieser Prozess aufgerufen wird, führt er die folgenden Aktionen aus:

1. Ruft das ungesicherte PDF-Dokument ab, das an den Prozess übergeben wird. Diese Aktion basiert auf dem Vorgang `SetValue`. Der Eingangsparameter für diesen Prozess ist eine `document`-Prozessvariable mit dem Namen `inDoc`.
1. Sie verschlüsselt das PDF-Dokument mit einem Kennwort. Diese Aktion basiert auf dem Vorgang `PasswordEncryptPDF`. Das kennwortverschlüsselte PDF-Dokument wird in einer Prozessvariablen namens `outDoc` zurückgegeben.

### Rufen Sie den kurzlebigen Prozess „MyApplication/EncryptDocument“ mithilfe der Java-Aufruf-API auf {#invoke-the-myapplication-encryptdocument-short-lived-process-using-the-java-invocation-api}

Rufen Sie den kurzlebigen Prozess `MyApplication/EncryptDocument` mithilfe der Java-Aufruf-API auf:

1. Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-livecycle-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein. (Siehe [Einbeziehen von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)
1. Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Erstellen Sie ein `ServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben. Mit einem `ServiceClient` -Objekt können Sie einen Dienstvorgang aufrufen. Es erledigt Aufgaben wie das Auffinden, Versenden und Weiterleiten von Aufrufanforderungen.
1. Erstellen Sie ein Objekt `java.util.HashMap`, indem Sie den Konstruktor verwenden.
1. Rufen Sie die `java.util.HashMap` -Objekt `put` -Methode für jeden Eingabeparameter, der an den langlebigen Prozess übergeben wird. Da der kurzlebige Prozess `MyApplication/EncryptDocument` einen Eingabeparameter des Typs `Document` erfordert, müssen Sie nur die `put`-Methode einmal aufrufen, wie im folgenden Beispiel gezeigt.

   ```java
    //Create a Map object to store the parameter value for inDoc
    Map params = new HashMap();
    InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf");
    Document inDoc = new Document(inFile);
    params.put("inDoc", inDoc);
   ```

1. Erstellen Sie eine `InvocationRequest` -Objekt durch Aufrufen der `ServiceClientFactory` -Objekt `createInvocationRequest` -Methode verwenden und die folgenden Werte übergeben:

   * Ein string-Wert, der den Namen des langlebigen aufzurufenden Prozesses angibt. Geben Sie `MyApplication/EncryptDocument` an, um den `MyApplication/EncryptDocument`-Prozess aufzurufen.
   * Ein string-Wert, der den Prozessvorgangsnamen darstellt. Typischerweise ist der Name eines kurzlebigen Prozessvorgangs `invoke`.
   * Das `java.util.HashMap`-Objekt, das die Parameterwerte enthält, die für den Dienstvorgang erforderlich sind.
   * Ein boolescher Wert, der `true`angibt, wodurch eine synchrone Anforderung erstellt wird (dieser Wert kann für den Aufruf eines kurzlebigen Prozesses verwendet werden).

1. Senden Sie die Aufrufanforderung an den Dienst, indem Sie die `ServiceClient` -Objekt `invoke` -Methode und Übergabe der `InvocationRequest` -Objekt. Die Methode `invoke` gibt ein `InvocationReponse`-Objekt zurück.

   >[!NOTE]
   >
   >Ein langlebiger Prozess kann aufgerufen werden, indem der Wert `false` als vierter Parameter der `createInvocationRequest`-Methode übergeben wird. Wenn Sie den Wert `false`*übergeben, wird eine asynchrone Anforderung erstellt.*

1. Abrufen des Rückgabewerts des Prozesses durch Aufrufen der `InvocationReponse` -Objekt `getOutputParameter` -Methode verwenden und einen string -Wert übergeben, der den Namen des Ausgabeparameters angibt. Geben Sie in dieser Situation `outDoc` an (`outDoc` ist der Name des Ausgabeparameters für den Prozess `MyApplication/EncryptDocument` ). Wandeln Sie den Rückgabewert in `Document` um, wie im folgenden Beispiel gezeigt.

   ```java
    InvocationResponse response = myServiceClient.invoke(request);
    Document encryptDoc = (Document) response.getOutputParameter("outDoc");
   ```

1. Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
1. Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `com.adobe.idp.Document` -Objekt in die Datei ein. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `getOutputParameter`-Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstart: Hervorrufen eines kurzlebigen Prozesses mit der Aufruf-API](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-using-the-invocation-api)

[An Menschen orientierte langlebige Prozesse aufrufen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
