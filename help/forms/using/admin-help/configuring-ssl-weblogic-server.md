---
title: Konfigurieren von SSL für WebLogic Server
description: Erfahren Sie, wie Sie eine SSL-Berechtigung für WebLogic Server erstellen und SSL für WebLogic Server konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 100%

---


# Konfigurieren von SSL für WebLogic Server {#configuring-ssl-for-weblogic-server}

Zum Konfigurieren von SSL unter WebLogic Server benötigen Sie eine SSL-Berechtigung zur Authentifizierung. Sie können mit dem Java-Keytool folgende Aufgaben ausführen, um eine Berechtigung zu erstellen:

* Erstellen Sie ein öffentlich-privates Schlüsselpaar und fügen Sie den öffentlichen Schlüssel in ein selbst signiertes Zertifikat vom Typ X.509 v1 ein, das als eingliedrige Zertifikatkette gespeichert wird. Speichern Sie die Zertifikatkette und den privaten Schlüssel in einem neuen Keystore. Bei diesem Keystore handelt es sich um den benutzerdefinierten Identitäts-Keystore des Anwendungs-Servers.
* Extrahieren Sie das Zertifikat und fügen Sie es in einen neuen Keystore ein. Dieser Keystore ist der benutzerdefinierte Trust-Keystore des Anwendungs-Servers.

Konfigurieren Sie WebLogic anschließend so, dass Ihr benutzerdefinierter Identitäts-Keystore und Ihr benutzerdefinierter Trust-Keystore verwendet werden. Deaktivieren Sie außerdem die Überprüfungsfunktion für Host-Namen in WebLogic, da der zum Erstellen der Keystore-Dateien verwendete Distinguished Name nicht den Namen des Host-Computers für WebLogic enthält.

## Erstellen einer SSL-Berechtigung für WebLogic Server {#creating-an-ssl-credential-for-use-on-weblogic-server}

Der Keytool-Befehl befindet sich in der Regel im Java-Ordner „jre/bin“ und muss verschiedene Optionen und Optionswerte enthalten, die in der folgenden Tabelle aufgeführt sind.

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
   <td><p>Der Alias des Keystores.</p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: <code>ads-credentials</code></p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: <code>bedrock</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keyalg</p></td>
   <td><p>Der Algorithmus zum Generieren des Schlüsselpaars.</p></td>
   <td><p>RSA</p><p>Sie können abhängig von den Richtlinien in Ihrem Unternehmen einen anderen Algorithmus verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-keystore</p></td>
   <td><p>Der Speicherort und Name der Keystore-Datei.</p><p>Der Speicherort kann den absoluten Pfad der Datei enthalten. Er kann auch relativ zum aktuellen Verzeichnis der Eingabeaufforderung angegeben werden, an der der Keytool-Befehl eingegeben wird.</p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: <code>[</code><i>appserverdomain<code>]</code></i><code>/adobe/</code><i>[Server-Name]</i><code>/ads-ssl.jks</code></p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: <code>[</code><i>appserverdomain<code>]</code></i><code>/adobe/</code><i>[Server-Name]</i><code>/ads-ca.jks</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-file</p></td>
   <td><p>Der Speicherort und Name der Zertifikatdatei.</p></td>
   <td><code> ads-ca.cer</code></td>
  </tr>
  <tr>
   <td><p>-validity</p></td>
   <td><p>Die Gültigkeitsdauer des Zertifikats (in Tagen).</p></td>
   <td><p>3650</p><p>Sie können abhängig von den Richtlinien in Ihrem Unternehmen einen anderen Wert verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-storepass</p></td>
   <td><p>Das Kennwort, das den Keystore-Inhalt schützt. </p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: Das Keystore-Kennwort muss mit dem SSL-Berechtigungskennwort übereinstimmen, das für die Trust Store-Komponente von Administration-Console festgelegt wurde.</p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: Verwenden Sie dasselbe Kennwort wie für den benutzerdefinierten Identitäts-Keystore.</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keypass</p></td>
   <td><p>Das Kennwort, das den privaten Schlüssel des Schlüsselpaars schützt.</p></td>
   <td><p>Verwenden Sie das gleiche Kennwort wie für die Option <code>-storepass</code>. Das Schlüsselkennwort muss mindestens sechs Zeichen aufweisen.</p></td>
  </tr>
  <tr>
   <td><p>-dname</p></td>
   <td><p>Der Distinguished Name, der die Person identifiziert, der der Keystore gehört.</p></td>
   <td><p><code>"CN=</code><code>[User name]</code><code>,OU=</code><code>[Group Name]</code><code>, O=</code><code>[Company Name]</code><code>, L=</code><code>[City Name]</code><code>, S=</code><code>[State or province]</code><code>, C=</code><code>[Country Code]</code><code>"</code></p>
    <ul>
     <li><p><code><i>[User name]</i></code> ist die Kennung des Benutzers, dem der Keystore gehört.</p></li>
     <li><p><code><i>[Group Name]</i></code> ist die Kennung der Unternehmensgruppe, der der Keystore-Besitzer angehört.</p></li>
     <li><p><code><i>[Company Name]</i></code> ist der Name Ihres Unternehmens.</p></li>
     <li><p><code><i>[City Name]</i></code> ist der Ort, an dem Ihr Unternehmen seinen Sitz hat.</p></li>
     <li><p><code><i>[State or province]</i></code> ist das Bundesland, in dem Ihr Unternehmen seinen Sitz hat.</p></li>
     <li><p><code><i>[Country Code]</i></code> ist der aus zwei Buchstaben bestehende Code für das Land, in dem Ihr Unternehmen seinen Sitz hat.</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

Weitere Informationen zum Verwenden des Keytool-Befehls finden Sie in der Datei „keytool.html“ der JDK-Dokumentation.

## Erstellen von benutzerdefinierten Identitäts- und Trust-Keystores {#create-the-custom-identity-and-trust-keystores}

1. Navigieren Sie in einer Eingabeaufforderung zu *[appserverdomain]*/adobe/*[Server-Name]*.
1. Geben Sie den folgenden Befehl ein:

   `[JAVA_HOME]/bin/keytool -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass store_password -keypass key_password -dname "CN=Hostname, OU=Group Name, O=Company Name, L=City Name, S=State,C=Country Code`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch das Verzeichnis, in dem das JDK installiert ist, und ersetzen Sie den kursiv gedruckten Text durch Werte, die Ihrer Umgebung entsprechen.

   Beispiel:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass P@ssw0rd -keypass P@ssw0rd -dname "CN=wasnode01, OU=LC, O=Adobe, L=Noida, S=UP,C=91
   ```

   Die benutzerdefinierte Identitäts-Keystore-Datei „ads-credentials.jks“ wird im Verzeichnis [appserverdomain]/adobe/[Server-Name] erstellt.

1. Extrahieren Sie das Zertifikat aus dem Keystore „ads-credentials“, indem Sie den folgenden Befehl eingeben:

   [JAVA_HOME]`/bin/keytool -export -v -alias ads-credentials`

   `-file "ads-ca.cer" -keystore "ads-credentials.jks"`

   `-storepass` `*store*`*_**Passwort**

   >[!NOTE]
   >
   >Ersetzen Sie `[JAVA_HOME]` durch das Verzeichnis, in dem das JDK installiert ist, und ersetzen Sie `store`*_* `password`* durch das Kennwort für den benutzerdefinierten Identitäts-Keystore.*

   Beispiel:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -export -v -alias ads-credentials -file "ads-ca.cer" -keystore "ads-credentials.jks" -storepass P@ssw0rd
   ```

   Die Zertifikatsdatei mit dem Namen „ads-ca.cer“ wird im Verzeichnis [appserverdomain]/adobe/[*Server-Name*] erstellt.

1. Kopieren Sie die Datei „ads-ca.cer“ auf alle Host-Computer, für die eine sichere Kommunikation mit dem Anwendungs-Server erforderlich ist.
1. Fügen Sie das Zertifikat mit dem folgenden Befehl in eine neue Keystore-Datei ein (d. h. in den benutzerdefinierten Trust-Keystore):

   [JAVA_HOME] `/bin/keytool -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass store_password -keypass key_password`

   >[!NOTE]
   >
   >Ersetzen Sie `[JAVA_HOME]` durch das Verzeichnis, in dem das JDK installiert ist, und ersetzen Sie `store`*_* `password` und `key`*_* `password` *durch Ihre eigenen Passwörter.*

   Beispiel:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass Password1 -keypass Password1
   ```

Die benutzerdefinierte Trust-Keystore-Datei „ads-ca.jks“ wird im Verzeichnis [appserverdomain]/adobe/[Server] erstellt.

Konfigurieren Sie WebLogic so, dass Ihr benutzerdefinierter Identitäts-Keystore und Ihr benutzerdefinierter Trust-Keystore verwendet werden. Deaktivieren Sie außerdem die Überprüfungsfunktion für Host-Namen in WebLogic, da der zum Erstellen der Keystore-Dateien verwendete Distinguished Name nicht den Namen des Host-Computers für WebLogic Server enthält.

## Konfigurieren von WebLogic für SSL {#configure-weblogic-to-use-ssl}

1. Starten Sie die WebLogic Server-Administrationskonsole, indem Sie `https://`*[Host-Name ]*`:7001/console` in die URL-Zeile eines Webbrowsers eingeben.
1. Wählen Sie unter „Umgebung“ in „Domain-Konfigurationen“ die Option **Server > [Server] > Konfiguration > Allgemein**.
1. Vergewissern Sie sich, dass unter „General“ (Allgemein) im Bereich „Configuration“ (Konfiguration) die Optionen **Listen Port Enabled** (Überwachungs-Port aktiviert) und **SSL Listen Port Enabled** (SSL-Überwachungs-Port aktiviert) ausgewählt sind. Gehen Sie wie folgt vor, wenn diese Optionen nicht aktiviert sind:

   1. Klicken Sie im Change Center auf **Sperren und bearbeiten**, um Auswahlen und Werte zu ändern.
   1. Aktivieren Sie die Kontrollkästchen **Listen Port Enabled** (Überwachungs-Port aktiviert) und **SSL Listen Port Enabled** (SSL-Überwachungs-Port aktiviert).

1. Wenn es sich hierbei um einen Managed Server handelt, ändern Sie den Wert für den Überwachungs-Port in einen nicht verwendeten Port-Wert (z. B. 8001) und für den SSL-Überwachungs-Port ebenfalls in einen nicht verwendeten Port-Wert (z. B. 8002). Bei einem eigenständigen Server ist der standardmäßige SSL-Port 7002.
1. Klicken Sie auf **Release Configuration** (Versionskonfiguration).
1. Klicken Sie unter „Umgebung“ in „Domain-Konfigurationen“ auf **Server > [*Managed Server*] > Konfiguration > Allgemein**.
1. Wählen Sie in den Konfigurationen unter „Allgemein“ die Option **Keystores**.
1. Klicken Sie im Change Center auf **Sperren und bearbeiten**, um Auswahlen und Werte zu ändern.
1. Klicken Sie auf **Change** (Ändern), um eine Keystore-Liste als Dropdown-Liste anzuzeigen und wählen Sie **Custom Identity And Custom Trust** (Benutzerdefinierte Identität und benutzerdefinierte Vertrauensstellung) aus.
1. Geben Sie unter „Identity“ (Identität) die folgenden Werte an:

   **Bennitzerdefinierter Identitäts-Keystore**: *[appserverdomain]*/adobe/*[Server-Nname]*/ads-credentials.jks, wobei *[appserverdomain] *der aktuelle Pfad und *[Server-Name]* der Name des Anwendungs-Servers ist.

   **Art des benutzerdefinierten Identitäts-Keystores**: JKS

   **Kennwort für benutzerdefinierten Identitäts-Keystore**: *mypassword* (Kennwort für benutzerdefinierten Identitäts-Keystore)

1. Geben Sie unter „Trust“ die folgenden Werte an:

   **Benutzerdefinierter Trust-Keystore-Dateiname**: `*[appserverdomain]*/adobe/*'server'*/ads-ca.jks`, wobei `*[appserverdomain]*` der tatsächliche Pfad ist

   **Art des benutzerdefinierten Trust-Keystores**: JKS

   **Kennwort für benutzerdefinierten Trust-Keystore**: *mypassword* (Kennwort für benutzerdefinierten Trust-Keystore)

1. Wählen Sie unter „General“ (Allgemein) im Bereich „Configuration“ (Konfiguration) den Eintrag **SSL** aus.
1. Standardmäßig ist unter „Identity and Trust Locations“ (Speicherort für Identitäten und Vertrauensstellungen) die Option „Keystore“ ausgewählt. Wenn nicht, ändern Sie die Einstellung zu „Keystore“.
1. Geben Sie unter „Identity“ (Identität) die folgenden Werte an:

   **Private Key Alias** (Alias für privaten Schlüssel): ads-credentials

   **Passphrase**: *mypassword*

1. Klicken Sie auf **Release Configuration** (Versionskonfiguration).

## Deaktivieren der Überprüfungsfunktion für Host-Namen {#disable-the-hostname-verification-feature}

1. Klicken Sie auf der Registerkarte „Configuration“ (Konfiguration) auf „SSL“.
1. Wählen Sie unter „Advanced“ (Erweitert) in der Liste „Hostname Verification“ (Host-Namen-Überprüfung) die Option „None“ (Keine) aus.

   Wenn die Überprüfung des Host-Namens nicht deaktiviert wird, muss unter „Common Name (CN)“ der Host-Name des Servers angegeben werden.

1. Klicken Sie unter „Change Center“ (Änderungszentrum) auf „Lock &amp; Edit“ (Sperren und bearbeiten), um Auswahlen und Werte zu ändern.
1. Starten Sie den Anwendungs-Server neu.

