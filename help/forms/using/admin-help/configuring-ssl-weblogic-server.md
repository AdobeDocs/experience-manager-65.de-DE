---
title: SSL für WebLogic Server konfigurieren
seo-title: SSL für WebLogic Server konfigurieren
description: Erfahren Sie, wie Sie eine SSL-Berechtigung für die Verwendung auf dem WebLogic Server erstellen und wie Sie SSL für WebLogic Server konfigurieren.
seo-description: Erfahren Sie, wie Sie eine SSL-Berechtigung für die Verwendung auf dem WebLogic Server erstellen und wie Sie SSL für WebLogic Server konfigurieren.
uuid: 8ee979fd-2615-451b-a607-4f73ecfed4f9
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 968c2574-ec9a-45ca-9c64-66f4caeec285
translation-type: tm+mt
source-git-commit: 06335b9a85414b6b1141dd19c863dfaad0812503

---


# SSL für WebLogic Server konfigurieren {#configuring-ssl-for-weblogic-server}

Zum Konfigurieren von SSL unter WebLogic Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool zum Ausführen der folgenden Aufgaben zum Erstellen einer Berechtigung verwenden:

* Erstellen Sie ein Schlüsselpaar (öffentlich/privat) und fügen Sie den öffentlichen Schlüssel in ein selbst signiertes Zertifikat des Typs X.509 v1 ein, das als eingliedrige Zertifikatskette gespeichert wird. Speichern Sie die Zertifikatskette und den privaten Schlüssel in einem neuen Keystore. Bei diesem Keystore handelt es sich um den benutzerdefinierten Identitäts-Keystore des Anwendungsservers.
* Extrahieren Sie das Zertifikat und fügen Sie es in einen neuen Keystore ein. Bei diesem Keystore handelt es sich um den benutzerdefinierten Trust-Keystore des Anwendungsservers.

Konfigurieren Sie WebLogic anschließend so, dass Ihr benutzerdefinierter Identitäts-Keystore und Ihr benutzerdefinierter Trust-Keystore verwendet werden. Deaktivieren Sie außerdem die Überprüfungsfunktion des Hostnamens in WebLogic, da der Name des Computers, der als Host für WebLogic dient, nicht in dem eindeutigen Namen enthalten ist, mit dem die Keystore-Dateien erstellt wurden.

## SSL-Berechtigung für die Verwendung unter WebLogic Server erstellen {#creating-an-ssl-credential-for-use-on-weblogic-server}

Der Keytool-Befehl befindet sich in der Regel im Java-Ordner „jre/bin“ und muss mehrere Optionen und Optionswerte enthalten, die in der folgenden Tabelle aufgeführt sind.

<table>
 <thead>
  <tr>
   <th><p>Keytool-Option</p></th>
   <th><p>Beschreibung</p></th>
   <th><p>Optionswert</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>-alias</p></td>
   <td><p>Der Alias des Keystore.</p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: <code>ads-credentials</code></p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: <code>bedrock</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keyalg</p></td>
   <td><p>Der zum Erstellen des Schlüsselpaars zu verwendende Algorithmus.</p></td>
   <td><p>RSA</p><p>Sie können abhängig von den firmeninternen Richtlinien einen anderen Algorithmus verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-keystore</p></td>
   <td><p>Der Speicherort und der Name der Keystore-Datei.</p><p>Der Speicherort kann den absoluten Pfad der Datei enthalten. Er kann auch relativ zum aktuellen Ordner der Eingabeaufforderung angegeben werden, an der der Keytool-Befehl eingegeben wird.</p></td>
   <td>
    <ul>
     <li><p>Custom Identity keystore: <code>[</code><i>appserverdomain]</i><code>/adobe/</code><i>[server name]</i><code>/ads-ssl.jks</code></p></li>
     <li><p>Custom Trust keystore: <code>[</code><i>appserverdomain]</i><code>/adobe/</code><i>[server name]</i><code>/ads-ca.jks</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-file</p></td>
   <td><p>Der Speicherort und der Name der Zertifikatdatei.</p></td>
   <td><code> ads-ca.cer</code></td>
  </tr>
  <tr>
   <td><p>-validity</p></td>
   <td><p>Die Gültigkeitsdauer des Zertifikats (in Tagen).</p></td>
   <td><p>3650</p><p>Sie können abhängig von den firmeninternen Richtlinien einen anderen Wert verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-storepass</p></td>
   <td><p>Das Kennwort, das den Keystore-Inhalt schützt. </p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: Das Keystore-Kennwort muss mit dem SSL-Berechtigungskennwort übereinstimmen, das für die Trust Store-Komponente von Administration Console festgelegt wurde.</p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: Verwenden Sie dasselbe Kennwort wie für den benutzerdefinierten Identitäts-Keystore.</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keypass</p></td>
   <td><p>Das Kennwort, das den privaten Schlüssel des Schlüsselpaars schützt.</p></td>
   <td><p>Use the same password that you used for the <code>-storepass</code> option. Das Schlüsselkennwort muss mindestens sechs Zeichen aufweisen.</p></td>
  </tr>
  <tr>
   <td><p>-dname</p></td>
   <td><p>Der Distinguished Name, der den Eigentümer des Keystore kennzeichnet.</p></td>
   <td><p><code>"CN=</code><code>[User name]</code><code>,OU=</code><code>[Group Name]</code><code>, O=</code><code>[Company Name]</code><code>, L=</code><code>[City Name]</code><code>, S=</code><code>[State or province]</code><code>, C=</code><code>[Country Code]</code><code>"</code></p>
    <ul>
     <li><p><code><i>[User name]</i></code> ist die Identifizierung des Benutzers, dem der Keystore gehört.</p></li>
     <li><p><code><i>[Group Name]</i></code> ist die Kennung der Unternehmensgruppe, der der Keystore-Eigentümer angehört.</p></li>
     <li><p><code><i>[Company Name]</i></code> ist der Name Ihrer Organisation.</p></li>
     <li><p><code><i>[City Name]</i></code> ist die Stadt, in der sich Ihr Unternehmen befindet.</p></li>
     <li><p><code><i>[State or province]</i></code> ist der Staat oder die Provinz, in dem/der sich Ihr Unternehmen befindet.</p></li>
     <li><p><code><i>[Country Code]</i></code> ist der aus zwei Buchstaben bestehende Code für das Land, in dem sich Ihr Unternehmen befindet.</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

Weitere Informationen zum Verwenden des Keytool-Befehls finden Sie in der Datei „keytool.html“, die sich in der JDK-Dokumentation befindet.

## Benutzerdefinierte Identitäts- und Trust-Keystores erstellen {#create-the-custom-identity-and-trust-keystores}

1. From a command prompt, navigate to *[appserverdomain]*/adobe/*[server name]*.
1. Geben Sie den folgenden Befehl ein:

   `[JAVA_HOME]/bin/keytool -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass store_password -keypass key_password -dname "CN=Hostname, OU=Group Name, O=Company Name, L=City Name, S=State,C=Country Code`

   >[!NOTE]
   >
   >Replace `[JAVA_HOME]`*with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment.*

   Beispiel:

   ```as3
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass P@ssw0rd -keypass P@ssw0rd -dname "CN=wasnode01, OU=LC, O=Adobe, L=Noida, S=UP,C=91
   ```

   The Custom Identity keystore file named ‘‘ads-credentials.jks” is created in the [appserverdomain]/adobe/[server name] directory.

1. Extrahieren Sie das Zertifikat aus dem Keystore „ads-credentials“, indem Sie den folgenden Befehl eingeben:

   [JAVA_HOME]`/bin/keytool -export -v -alias ads-credentials`

   `-file "ads-ca.cer" -keystore "ads-credentials.jks"`

   `-storepass` `*store*`*_**password**

   >[!NOTE]
   >
   >Replace `[JAVA_HOME]` with the directory where the JDK is installed, and replace `store`*_*`password`* with the password for the Custom Identity keystore.*

   Beispiel:

   ```as3
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -export -v -alias ads-credentials -file "ads-ca.cer" -keystore "ads-credentials.jks" -storepass P@ssw0rd
   ```

   The certificate file named “ads-ca.cer” is created in the [appserverdomain]/adobe/[*server name*] directory.

1. Kopieren Sie die Datei „ads-ca.cer“ auf alle Hostcomputer, für die eine sichere Kommunikation mit dem Anwendungsserver erforderlich ist.
1. Fügen Sie das Zertifikat mit dem folgenden Befehl in eine neue Keystore-Datei ein (d. h. in den benutzerdefinierten Trust-Keystore):

   [JAVA_HOME] `/bin/keytool -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass store_password -keypass key_password`

   >[!NOTE]
   >
   >Replace `[JAVA_HOME]` with the directory where the JDK is installed, and replace `store`*_*`password`and`key`*_* `password` *with your own passwords.*

   Beispiel:

   ```as3
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass Password1 -keypass Password1
   ```

The Custom Trust keystore file named ‘‘ads-ca.jks’’ is created in the [appserverdomain]/adobe/[server] directory.

Konfigurieren Sie WebLogic so, dass Ihr benutzerdefinierter Identitäts-Keystore und Ihr benutzerdefinierter Trust-Keystore verwendet werden. Deaktivieren Sie außerdem die Überprüfungsfunktion des Hostnamens in WebLogic, da der Name des Computers, der als Host für WebLogic Server dient, nicht in dem eindeutigen Namen enthalten ist, mit dem die Keystore-Dateien erstellt wurden.

## WebLogic zur Verwendung mit SSL konfigurieren {#configure-weblogic-to-use-ssl}

1. Start the WebLogic Server administration console by typing `https://`*[host name ]*`:7001/console`in the URL line of a web browser.
1. Under Environment, in Domain Configurations, select **Servers >[server]> Configuration > General**.
1. Vergewissern Sie sich, dass unter „General“ im Bereich „Configuration“die Optionen **Listen Port Enabled** und **SSL Listen Port Enabled** ausgewählt sind. Ist es nicht aktiviert, führen Sie folgende Schritte aus:

   1. Klicken Sie im Change Center auf **Lock &amp; Edit**, um Auswahlen und Werte zu ändern.
   1. Vergewissern Sie sich, dass die Kontrollkästchen **Listen Port Enabled** und **SSL Listen Port Enabled** aktiviert sind.

1. Wenn es sich hierbei um einen Managed Server handelt, ändern Sie den Wert für „Listen Port“ in einen nicht verwendeten Anschlusswert (z. B. 8001) und „SSL Listen Port“ in einen nicht verwendeten Anschlusswert (z. B. 8002). Bei einem eigenständigen Server ist der standardmäßige SSL-Anschluss 7002.
1. Klicken Sie auf **Release Configuration**.
1. Under Environment, in Domain Configurations, click **Servers >[*Managed Server*]> Configuration > General**.
1. Wählen Sie in den Konfigurationen unter „General“ **Keystores**.
1. Klicken Sie im Change Center auf **Lock &amp; Edit**, um Auswahlen und Werte zu ändern.
1. Klicken Sie auf **Change**, um eine Keystore-Liste als Dropdown-Liste anzuzeigen und wählen Sie **Custom Identity And Custom Trust**.
1. Geben Sie unter „Identity“ die folgenden Werte an:

   **Benutzerdefinierter Identitäts-Keystore**: *[appserverdomain]*/adobe/*[server name]*/ads-credentials.jks, wobei *[appserverdomain] *der tatsächliche Pfad und der *[Servername]* der Name des Anwendungsservers ist.

   **Custom Identity Keystore Type**: JKS

   **Custom Identity Keystore Passphrase**: *mypassword* (Custom Identity Keystore Password)

1. Geben Sie unter „Trust“ die folgenden Werte an:

   **Benutzerdefinierter Trust Keystore-Dateiname**: `*[appserverdomain]*/adobe/*[server]*/ads-ca.jks`, wobei `*[appserverdomain]*` der tatsächliche Pfad ist

   **Custom Trust Keystore Type**: JKS

   **Custom Trust Keystore Pass Phrase**: *mypassword* (Custom Trust Key Password)

1. Wählen Sie unter „General“ im Bereich „Configuration“ den Eintrag **SSL** aus.
1. Standardmäßig wird für Identity and Trust Locations „Keystore“ ausgewählt. Wenn nicht, ändern Sie es auf Keystore.
1. Geben Sie unter „Identity“ die folgenden Werte an:

   **Private Key Alias**: ads-credentials

   **Passphrase**: *mypassword*

1. Klicken Sie auf **Release Configuration**.

## Überprüfungsfunktion des Hostnamens deaktivieren {#disable-the-hostname-verification-feature}

1. Klicken Sie auf der Registerkarte „Configuration“ auf „SSL“.
1. Wählen Sie unter „Advanced“ in der Liste „Hostname Verification“ den Eintrag „None“.

   Wenn die Überprüfung des Hostnamens nicht deaktiviert wird, muss unter „Common Name (CN)“ der Hostname des Servers angegeben werden.

1. Klicken Sie unter „Change Center“ auf „Lock &amp; Edit“, um Auswahlen und Werte zu ändern.
1. Starten Sie den Anwendungsserver neu.

