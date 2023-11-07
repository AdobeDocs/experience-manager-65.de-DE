---
title: Konfigurieren von SSL für WebLogic Server
seo-title: Configuring SSL for WebLogic Server
description: Erfahren Sie, wie Sie eine SSL-Berechtigung für die Verwendung auf WebLogic-Server erstellen und SSL für WebLogic Server konfigurieren.
seo-description: Learn how to create an SSL credential for use on WebLogic server and how to configure SSL for WebLogic Server.
uuid: 8ee979fd-2615-451b-a607-4f73ecfed4f9
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 968c2574-ec9a-45ca-9c64-66f4caeec285
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 35%

---


# Konfigurieren von SSL für WebLogic Server {#configuring-ssl-for-weblogic-server}

Zum Konfigurieren von SSL auf WebLogic Server benötigen Sie eine SSL-Berechtigung für die Authentifizierung. Sie können das Java-Keytool verwenden, um die folgenden Aufgaben zum Erstellen einer Berechtigung auszuführen:

* Erstellen Sie ein Schlüsselpaar aus öffentlichem/privatem Schlüssel, schließen Sie den öffentlichen Schlüssel in ein selbst signiertes Zertifikat aus X.509 v1 ein, das als Zertifikatskette mit einem einzelnen Element gespeichert wird, und speichern Sie dann die Zertifikatskette und den privaten Schlüssel in einem neuen Keystore. Dieser Keystore ist der benutzerdefinierte Identitäts-Keystore des Anwendungsservers.
* Extrahieren Sie das Zertifikat und fügen Sie es in einen neuen Keystore ein. Dieser Keystore ist der benutzerdefinierte Trust-Keystore des Anwendungsservers.

Konfigurieren Sie dann WebLogic so, dass der von Ihnen erstellte benutzerdefinierte Identitäts-Keystore und der benutzerdefinierte Trust-Keystore verwendet werden. Deaktivieren Sie außerdem die Überprüfungsfunktion für Hostnamen in WebLogic, da der Distinguished Name zum Erstellen der Keystore-Dateien nicht den Namen des Computers enthält, der als Host für WebLogic dient.

## SSL-Berechtigung zur Verwendung auf WebLogic Server erstellen {#creating-an-ssl-credential-for-use-on-weblogic-server}

Der Keytool-Befehl befindet sich normalerweise im Ordner &quot;Java jre/bin&quot;und muss mehrere Optionen und Optionswerte enthalten, die in der folgenden Tabelle aufgeführt sind.

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
   <td><p>Der Algorithmus zum Generieren des Schlüsselpaars.</p></td>
   <td><p>RSA</p><p>Je nach Richtlinie Ihres Unternehmens können Sie einen anderen Algorithmus verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-keystore</p></td>
   <td><p>Speicherort und Name der Keystore-Datei.</p><p>Der Speicherort kann den absoluten Pfad der Datei enthalten. Oder sie kann relativ zum aktuellen Verzeichnis der Eingabeaufforderung sein, an der der Keytool-Befehl eingegeben wird.</p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: <code>[</code><i>appserverdomain<code>]</code></i><code>/adobe/</code><i>[Server-Name]</i><code>/ads-ssl.jks</code></p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: <code>[</code><i>appserverdomain<code>]</code></i><code>/adobe/</code><i>[Server-Name]</i><code>/ads-ca.jks</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-file</p></td>
   <td><p>Speicherort und Name der Zertifikatdatei.</p></td>
   <td><code> ads-ca.cer</code></td>
  </tr>
  <tr>
   <td><p>-validity</p></td>
   <td><p>Die Anzahl der Tage, in denen das Zertifikat als gültig betrachtet wird.</p></td>
   <td><p>3650</p><p>Sie können je nach Richtlinie Ihres Unternehmens einen anderen Wert verwenden.</p></td>
  </tr>
  <tr>
   <td><p>-storepass</p></td>
   <td><p>Das Kennwort, das den Inhalt des Keystore schützt. </p></td>
   <td>
    <ul>
     <li><p>Benutzerdefinierter Identitäts-Keystore: Das Keystore-Kennwort muss mit dem SSL-Berechtigungskennwort übereinstimmen, das für die Trust Store-Komponente in Administration Console angegeben wurde.</p></li>
     <li><p>Benutzerdefinierter Trust-Keystore: Verwenden Sie dasselbe Kennwort wie für den benutzerdefinierten Identitäts-Keystore.</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keypass</p></td>
   <td><p>Das Kennwort, das den privaten Schlüssel des Schlüsselpaars schützt.</p></td>
   <td><p>Verwenden Sie das gleiche Kennwort wie für die Option <code>-storepass</code>. Das Schlüsselkennwort muss mindestens sechs Zeichen lang sein.</p></td>
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

Weitere Informationen zur Verwendung des Keytool-Befehls finden Sie in der Datei &quot;keytool.html&quot;, die Teil Ihrer JDK-Dokumentation ist.

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

1. Kopieren Sie die Datei &quot;ads-ca.cer&quot;auf alle Hostcomputer, die sichere Kommunikation mit dem Anwendungsserver benötigen.
1. Fügen Sie das Zertifikat in eine neue Keystore-Datei (den benutzerdefinierten Trust-Keystore) ein, indem Sie den folgenden Befehl eingeben:

   [JAVA_HOME] `/bin/keytool -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass store_password -keypass key_password`

   >[!NOTE]
   >
   >Ersetzen Sie `[JAVA_HOME]` durch das Verzeichnis, in dem das JDK installiert ist, und ersetzen Sie `store`*_* `password` und `key`*_* `password` *durch Ihre eigenen Passwörter.*

   Beispiel:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass Password1 -keypass Password1
   ```

Die benutzerdefinierte Trust-Keystore-Datei „ads-ca.jks“ wird im Verzeichnis [appserverdomain]/adobe/[Server] erstellt.

Konfigurieren Sie WebLogic so, dass es den von Ihnen erstellten benutzerdefinierten Identitäts-Keystore und benutzerdefinierten Trust-Keystore verwendet. Deaktivieren Sie außerdem die Überprüfungsfunktion für Hostnamen in WebLogic, da der Distinguished Name zum Erstellen der Keystore-Dateien nicht den Namen des Computers enthält, der als Host für WebLogic Server dient.

## WebLogic für die Verwendung von SSL konfigurieren {#configure-weblogic-to-use-ssl}

1. Starten Sie die WebLogic Server-Administrationskonsole, indem Sie `https://`*[Host-Name ]*`:7001/console` in die URL-Zeile eines Webbrowsers eingeben.
1. Wählen Sie unter „Umgebung“ in „Domain-Konfigurationen“ die Option **Server > [Server] > Konfiguration > Allgemein**.
1. Stellen Sie unter &quot;Allgemein&quot;in &quot;Konfiguration&quot;sicher, dass **Listen Port Enabled** und **SSL Listen Port aktiviert** ausgewählt sind. Wenn diese Option nicht aktiviert ist, gehen Sie wie folgt vor:

   1. Klicken Sie im Change Center auf **Sperren und bearbeiten**, um Auswahlen und Werte zu ändern.
   1. Überprüfen Sie die **Listen Port Enabled** und **SSL Listen Port aktiviert** aktivieren.

1. Wenn es sich bei diesem Server um einen verwalteten Server handelt, ändern Sie Listen Port in einen nicht verwendeten Anschlusswert (z. B. 8001) und SSL Listen Port in einen nicht verwendeten Anschlusswert (z. B. 8002). Auf einem eigenständigen Server ist der standardmäßige SSL-Anschluss 7002.
1. Klicks **Versionskonfiguration**.
1. Klicken Sie unter „Umgebung“ in „Domain-Konfigurationen“ auf **Server > [*Managed Server*] > Konfiguration > Allgemein**.
1. Wählen Sie in den Konfigurationen unter „Allgemein“ die Option **Keystores**.
1. Klicken Sie im Change Center auf **Sperren und bearbeiten**, um Auswahlen und Werte zu ändern.
1. Klicks **Änderung** , um die Keystore-Liste als Dropdown-Liste abzurufen, und wählen Sie **Benutzerdefinierte Identität und benutzerdefinierter Vertrauen**.
1. Geben Sie unter Identität die folgenden Werte an:

   **Bennitzerdefinierter Identitäts-Keystore**: *[appserverdomain]*/adobe/*[Server-Nname]*/ads-credentials.jks, wobei *[appserverdomain] *der aktuelle Pfad und *[Server-Name]* der Name des Anwendungs-Servers ist.

   **Art des benutzerdefinierten Identitäts-Keystores**: JKS

   **Custom Identity Keystore Passphrase**: *mypassword*  (Custom Identity Keystore Password)

1. Geben Sie unter &quot;Trust&quot;die folgenden Werte an:

   **Benutzerdefinierter Trust-Keystore-Dateiname**: `*[appserverdomain]*/adobe/*'server'*/ads-ca.jks`, wobei `*[appserverdomain]*` der tatsächliche Pfad ist

   **Art des benutzerdefinierten Trust-Keystores**: JKS

   **Custom Trust Keystore Pass Phrase**: *mypassword*  (Custom Trust Key Password)

1. Wählen Sie unter &quot;Allgemein&quot;unter &quot;Konfiguration&quot;die Option **SSL**.
1. Standardmäßig ist Keystore für Identity and Trust Locations ausgewählt. Wenn nicht, ändern Sie es in Keystore.
1. Geben Sie unter Identität die folgenden Werte an:

   **Alias für privaten Schlüssel**: ads-credentials

   **Passphrase**: *mypassword*

1. Klicks **Versionskonfiguration**.

## Überprüfungsfunktion für Hostnamen deaktivieren {#disable-the-hostname-verification-feature}

1. Klicken Sie auf der Registerkarte Configuration auf SSL.
1. Wählen Sie unter &quot;Erweitert&quot;in der Liste &quot;Überprüfung des Hostnamens&quot;die Option Keine aus.

   Wenn die Überprüfung des Hostnamens nicht deaktiviert ist, muss der allgemeine Name (CN) den Hostnamen des Servers enthalten.

1. Klicken Sie unter &quot;Change Center&quot;auf Lock &amp; Edit , um Auswahlen und Werte zu ändern.
1. Starten Sie den Anwendungs-Server neu.

