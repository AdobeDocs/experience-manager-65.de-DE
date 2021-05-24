---
title: Replizieren mit MSSL
seo-title: Replizieren mit MSSL
description: Erfahren Sie, wie Sie AEM so konfigurieren, dass ein Replikationsagent auf der Autoreninstanz gegenseitiges SSL (MSSL) für die Verbindung mit der Veröffentlichungsinstanz verwendet. Bei MSSL verwenden der Replikationsagent und der HTTP-Dienst auf der Veröffentlichungsinstanz Zertifikate für die gegenseitige Authentifizierung.
seo-description: Erfahren Sie, wie Sie AEM so konfigurieren, dass ein Replikationsagent auf der Autoreninstanz gegenseitiges SSL (MSSL) für die Verbindung mit der Veröffentlichungsinstanz verwendet. Bei MSSL verwenden der Replikationsagent und der HTTP-Dienst auf der Veröffentlichungsinstanz Zertifikate für die gegenseitige Authentifizierung.
uuid: f4bc5e61-a58c-4fd2-9a24-b31e0c032c15
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 8bc307d9-fa5c-44c0-bff9-2d68d32a253b
feature: Konfiguration
exl-id: 0a8d7831-d076-45cf-835c-8063ee13d6ba
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1457'
ht-degree: 93%

---

# Replizieren mit MSSL{#replicating-using-mutual-ssl}

Konfigurieren Sie AEM so, dass ein Replikationsagent auf der Autoreninstanz gegenseitiges SSL (MSSL) für die Verbindung mit der Veröffentlichungsinstanz verwendet Bei MSSL verwenden der Replikationsagent und der HTTP-Dienst auf der Veröffentlichungsinstanz Zertifikate für die gegenseitige Authentifizierung.

Das Konfigurieren von MSSL für die Replikation beinhaltet folgende Schritte:

1. Erstellen oder rufen Sie private Schlüssel und Zertifikate für die Autoren- und Veröffentlichungsinstanz ab.
1. Installieren Sie die Schlüssel und Zertifikate auf der Autoren- und Veröffentlichungsinstanz:

   * Autor: Der private Schlüssel des Autors und das Zertifikat der Veröffentlichung.
   * Veröffentlichung: Der private Schlüssel der Veröffentlichung und das Zertifikat des Autors. Das Zertifikat ist mit dem Benutzerkonto verknüpft, das mit dem Replikationsagenten authentifiziert wird.

1. Konfigurieren Sie den Jetty-basierten HTTP-Dienst auf der Veröffentlichungsinstanz.
1. Konfigurieren Sie die Transport- und SSL-Eigenschaften des Replikationsagenten.

![chlimage_1-64](assets/chlimage_1-64.png)

Sie müssen festlegen, mit welchem Benutzerkonto die Replikation ausgeführt wird. Wenn Sie das Zertifikat des vertrauenswürdigen Autors auf der Veröffentlichungsinstanz installieren, wird das Zertifikat mit diesem Benutzerkonto verknüpft.

## Abrufen oder Erstellen von Anmeldeinformationen für MSSL {#obtaining-or-creating-credentials-for-mssl}

Sie benötigen einen privaten Schlüssel und ein öffentliches Zertifikat für die Autoren- und Veröffentlichungsinstanz:

* Private Schlüssel müssen im PKCS#12- oder JKS-Format vorliegen.
* Zertifikate müssen im PKCS#12- oder JKS-Format enthalten sein. Zertifikate im CER-Format können ebenfalls zu Granite Truststore hinzugefügt werden.
* Zertifikate können von einer anerkannten Zertifizierungsstelle (Certification Authority, CA) selbst signiert oder signiert werden.

### JKS-Format  {#jks-format}

Erstellen Sie einen privaten Schlüssel und ein Zertifikat im JKS-Format. Der private Schlüssel wird in einer KeyStore-Datei, das Zertifikat in einer TrustStore-Datei gespeichert. Verwenden Sie [Java `keytool`](https://docs.oracle.com/javase/7/docs/technotes/tools/solaris/keytool.html), um beide zu erstellen.

Führen Sie mit dem Java-`keytool` folgende Schritte aus, um den privaten Schlüssel und die Anmeldedaten zu erstellen:

1. Generieren Sie ein privat/öffentliches Schlüsselpaar in einem KeyStore.
1. Erstellen oder rufen Sie das Zertifikat ab:

   * Selbstsigniert: Exportieren Sie das Zertifikat aus dem KeyStore.
   * CA-signiert: Generieren Sie eine Zertifikatanforderung und senden Sie diese an die CA.

1. Importieren Sie das Zertifikat in einen TrustStore.

Gehen Sie wie folgt vor, um einen privaten Schlüssel und ein selbstsigniertes Zertifikat für die Autoren- und Veröffentlichungsinstanz zu erstellen. Verwenden Sie unterschiedliche Werte für die Befehlsoptionen.

1. Öffnen Sie eine Befehlszeile oder ein Terminal. Um das privat/öffentliche Schlüsselpaar zu erstellen, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   keytool -genkeypair -keyalg RSA -validity 3650 -alias alias -keystore keystorename.keystore  -keypass key_password -storepass  store_password -dname "CN=Host Name, OU=Group Name, O=Company Name,L=City Name, S=State, C=Country_ Code"
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -alias | author | publish |
   | -keystore | author.keystore | publish.keystore |

1. Um das Zertifikat zu exportieren, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   keytool -exportcert -alias alias -file cert_file -storetype jks -keystore keystore -storepass store_password
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -alias | author | publish |
   | -file | author.cer | publish.cer |
   | -keystore | author.keystore | publish.keystore |

### PKCS#12-Format {#pkcs-format}

Generieren Sie einen privaten Schlüssel und ein Zertifikat im PKCS#12-Format. Verwenden Sie[ openSSL](https://www.openssl.org/), um diese zu generieren. Gehen Sie wie folgt vor, um einen privaten Schlüssel und eine Zertifikatanforderung zu generieren. Um das Zertifikat zu erhalten, müssen Sie die Anforderung mit Ihrem privaten Schlüssel (selbstsigniertem Zertifikat) signieren oder die Anforderung an die Zertifizierungsstelle senden. Generieren Sie danach das PKCS#12-Archiv, das den privaten Schlüssel und das Zertifikat enthält.

1. Öffnen Sie eine Befehlszeile oder ein Terminal. Um den privaten Schlüssel zu erstellen, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   openssl genrsa -out keyname.key 2048
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -out | author.key | publish.key |

1. Um eine Zertifikatanforderung zu generieren, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   openssl req -new -key keyname.key -out key_request.csr
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -key | author.key | publish.key |
   | -out | author_request.csr | publish_request.csr |

   Signieren Sie die Zertifikatanforderung oder senden Sie die Anforderung an die Zertifizierungsstelle.

1. Um die Zertifikatanforderung zu signieren, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   openssl x509 -req -days 3650 -in key_request.csr -signkey keyname.key -out certificate.cer
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -signkey | author.key | publish.key |
   | -in | author_request.csr | publish_request.csr |
   | -out | author.cer | publish.cer |

1. Um den privaten Schlüssel und das signierte Zertifikat einer PKCS#12-Datei hinzuzufügen, geben Sie folgenden Befehl anhand der Optionswerte in der nachfolgenden Tabelle ein:

   ```shell
   openssl pkcs12 -keypbe PBE-SHA1-3DES -certpbe PBE-SHA1-3DES -export -in certificate.cer -inkey keyname.key -out pkcs12_archive.pfx -name "alias"
   ```

   | Option | Autor | Veröffentlichung |
   |---|---|---|
   | -inkey | author.key | publish.key |
   | -out | author.pfx | publish.pfx |
   | -in | author.cer | publish.cer |
   | -name | author | veröffentlichen |

## Installieren von privatem Schlüssel und TrustStore auf der Autoreninstanz {#install-the-private-key-and-truststore-on-author}

Installieren Sie Folgendes auf der Autoreninstanz:

* Den privaten Schlüssel der Autoreninstanz.
* Das Zertifikat der Veröffentlichungsinstanz.

Um folgende Schritte ausführen, müssen Sie als Administrator der Autoreninstanz angemeldet sein.

### Installieren des privaten Schlüssels der Autoreninstanz  {#install-the-author-private-key}

1. Öffnen Sie die Seite „Benutzerverwaltung“ für die Autoreninstanz. ([http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html))
1. Klicken oder tippen Sie auf Ihren Benutzernamen, um die Eigenschaften Ihres Benutzerkontos zu öffnen.
1. Wenn der Link „KeyStore erstellen“ im Bereich mit den Kontoeinstellungen angezeigt wird, klicken Sie auf diesen Link. Konfigurieren Sie ein Kennwort und klicken Sie auf „OK“.
1. Klicken Sie im Bereich mit den Kontoeinstellungen auf „KeyStore verwalten“.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Klicken Sie auf „Privaten Schlüssel aus KeyStore-Datei hinzufügen“.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Klicken Sie auf „KeyStore-Datei auswählen“. Suchen Sie dann nach der Datei „author.keystore“ (oder nach der Datei „author.pfx“ bei Verwendung von PKCS#12) und wählen Sie diese aus. Klicken Sie auf „Öffnen“.
1. Geben Sie einen Alias und das Kennwort für den KeyStore ein. Geben Sie den Alias und das Kennwort für den privaten Schlüssel ein. Klicken Sie anschließend auf „Übermitteln“.
1. Schließen Sie das Dialogfeld „KeyStore-Verwaltung“.

   ![chlimage_1-67](assets/chlimage_1-67.png)

### Installieren des Veröffentlichungszertifikats {#install-the-publish-certificate}

1. Öffnen Sie die Seite „Benutzerverwaltung“ für die Autoreninstanz. ([http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html))
1. Klicken oder tippen Sie auf Ihren Benutzernamen, um die Eigenschaften Ihres Benutzerkontos zu öffnen.
1. Wenn der Link „KeyStore erstellen“ im Bereich mit den Kontoeinstellungen angezeigt wird, klicken Sie auf diesen Link. Konfigurieren Sie ein Kennwort für den TrustStore und klicken Sie auf „OK“.
1. Klicken Sie im Bereich mit den Kontoeinstellungen auf „TrustStore verwalten“.
1. Klicken Sie auf „Zertifikat aus CER-Datei hinzufügen“.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. Deaktivieren Sie die Option „Benutzer Zertifikat zuordnen“. Klicken Sie auf „Zertifikatsdatei auswählen“ und wählen Sie „publish.cer“ aus. Klicken Sie auf „Öffnen“.
1. Schließen Sie das Dialogfeld „TrustStore-Verwaltung“.

   ![chlimage_1-69](assets/chlimage_1-69.png)

## Installieren von privatem Schlüssel und TrustStore auf der Veröffentlichungsinstanz {#install-private-key-and-truststore-on-publish}

Installieren Sie Folgendes auf der Veröffentlichungsinstanz:

* Den privaten Schlüssel der Veröffentlichungsinstanz.
* Das Zertifikat der Autoreninstanz. Verknüpfen Sie das Zertifikat mit dem Benutzer, über den Replikationsanforderungen ausgeführt werden.

Um die folgenden Schritte auszuführen, müssen Sie als Administrator der Veröffentlichungsinstanz angemeldet sein.

### Installieren des privaten Schlüssels der Veröffentlichungsinstanz  {#install-the-publish-private-key}

1. Öffnen Sie die Seite „Benutzerverwaltung“ für die Veröffentlichungsinstanz. ([http://localhost:4503/libs/granite/security/content/useradmin.html](http://localhost:4503/libs/granite/security/content/useradmin.html))
1. Klicken oder tippen Sie auf Ihren Benutzernamen, um die Eigenschaften Ihres Benutzerkontos zu öffnen.
1. Wenn der Link „KeyStore erstellen“ im Bereich mit den Kontoeinstellungen angezeigt wird, klicken Sie auf diesen Link. Konfigurieren Sie ein Kennwort und klicken Sie auf „OK“.
1. Klicken Sie im Bereich mit den Kontoeinstellungen auf „KeyStore verwalten“.
1. Klicken Sie auf „Privaten Schlüssel aus KeyStore-Datei hinzufügen“.
1. Klicken Sie auf „KeyStore-Datei auswählen“. Suchen Sie dann nach der Datei „publish.keystore“ (oder nach der Datei „publish.pfx“ bei Verwendung von PKCS#12) und wählen Sie diese aus. Klicken Sie dann auf „Öffnen“.
1. Geben Sie einen Alias und das Kennwort für den KeyStore ein. Geben Sie den Alias und das Kennwort für den privaten Schlüssel ein. Klicken Sie anschließend auf „Übermitteln“.
1. Schließen Sie das Dialogfeld „KeyStore-Verwaltung“.

### Installieren des Autorenzertifikats  {#install-the-author-certificate}

1. Öffnen Sie die Seite „Benutzerverwaltung“ für die Veröffentlichungsinstanz. ([http://localhost:4503/libs/granite/security/content/useradmin.html](http://localhost:4503/libs/granite/security/content/useradmin.html))
1. Suchen Sie nach dem Benutzerkonto, das zum Ausführen von Replikationsanforderungen verwendet wird, und klicken oder tippen Sie auf den Benutzernahmen.
1. Wenn der Link „KeyStore erstellen“ im Bereich mit den Kontoeinstellungen angezeigt wird, klicken Sie auf diesen Link. Konfigurieren Sie ein Kennwort für den TrustStore und klicken Sie auf „OK“.
1. Klicken Sie im Bereich mit den Kontoeinstellungen auf „TrustStore verwalten“.
1. Klicken Sie auf „Zertifikat aus CER-Datei hinzufügen“.
1. Stellen Sie sicher, dass die Option „Benutzer Zertifikat zuordnen“ ausgewählt ist. Klicken Sie auf „Zertifikatsdatei auswählen“ und wählen Sie „author.cer“ aus. Klicken Sie auf „Öffnen“.
1. Klicken Sie auf „Übermitteln“ und schließen Sie dann das Dialogeld „TrustStore-Verwaltung“.

## Konfigurieren des HTTP-Dienstes auf der Veröffentlichungsinstanz  {#configure-the-http-service-on-publish}

Konfigurieren Sie die Eigenschaften des Apache Felix Jetty-basierten HTTP-Dienstes auf der Veröffentlichungsinstanz so, dass beim Zugriff auf Granite KeyStore HTTPS verwendet wird. Die PID des Dienstes ist `org.apache.felix.http`.

In der folgenden Tabelle sind die OSGi-Eigenschaften aufgeführt, die Sie konfigurieren müssen, wenn Sie die Web-Konsole verwenden.

| Eigenschaftsname in der Web-Konsole | OSGi-Eigenschaftsname | Wert |
|---|---|---|
| HTTPS aktivieren | org.apache.felix.https.enable | true |
| Aktivieren Sie HTTPS zur Verwendung von Granite KeyStore. | org.apache.felix.https.use.granite.keystore | true |
| HTTPS-Port | org.osgi.service.http.port.secure | 8443 (oder anderer gewünschter Anschluss) |
| Client-Zertifikat | org.apache.felix.https.clientcertificate | &quot;Client-Zertifikat gewünscht&quot; |

## Konfigurieren des Replikationsagenten auf der Autoreninstanz {#configure-the-replication-agent-on-author}

Konfigurieren Sie den Replikationsagenten auf der Autoreninstanz so, dass das HTTPS-Protokoll beim Herstellen einer Verbindung mit der Veröffentlichungsinstanz verwendet wird. Weitere Informationen zum Konfigurieren von Replikationsagenten finden Sie unter [Konfigurieren der Replikationsagenten](/help/sites-deploying/replication.md#configuring-your-replication-agents).

Um MSSL zu aktivieren, konfigurieren Sie die Eigenschaften auf der Registerkarte „Transport“ entsprechend der folgenden Tabelle:

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>URI</td>
   <td><p>https://server_name:SSL_port/bin/receive?sling:authRequestLogin=1</p> <p>Beispiel:</p> <p>http://localhost:8443/bin/receive?sling:authRequestLogin=1</p> </td>
  </tr>
  <tr>
   <td>User</td>
   <td>Kein Wert</td>
  </tr>
  <tr>
   <td>Passwort</td>
   <td>Kein Wert</td>
  </tr>
  <tr>
   <td>SSL</td>
   <td>Client-Auth.</td>
  </tr>
 </tbody>
</table>

![chlimage_1-70](assets/chlimage_1-70.png)

Wenn Sie den Replikationsagenten konfiguriert haben, testen Sie die Verbindung, um zu überprüfen, ob MSSL richtig konfiguriert ist.

```xml
29.08.2014 14:02:46 - Create new HttpClient for Default Agent
29.08.2014 14:02:46 - * HTTP Version: 1.1
29.08.2014 14:02:46 - * Using Client Auth SSL configuration *
29.08.2014 14:02:46 - adding header: Action:Test
29.08.2014 14:02:46 - adding header: Path:/content
29.08.2014 14:02:46 - adding header: Handle:/content
29.08.2014 14:02:46 - deserialize content for delivery
29.08.2014 14:02:46 - No message body: Content ReplicationContent.VOID is empty
29.08.2014 14:02:46 - Sending POST request to http://localhost:8443/bin/receive?sling:authRequestLogin=1
29.08.2014 14:02:46 - sent. Response: 200 OK
29.08.2014 14:02:46 - ------------------------------------------------
29.08.2014 14:02:46 - Sending message to localhost:8443
29.08.2014 14:02:46 - >> POST /bin/receive HTTP/1.0
29.08.2014 14:02:46 - >> Action: Test
29.08.2014 14:02:46 - >> Path: /content
29.08.2014 14:02:46 - >> Handle: /content
29.08.2014 14:02:46 - >> Referer: about:blank
29.08.2014 14:02:46 - >> Content-Length: 0
29.08.2014 14:02:46 - >> Content-Type: application/octet-stream
29.08.2014 14:02:46 - --
29.08.2014 14:02:46 - << HTTP/1.1 200 OK
29.08.2014 14:02:46 - << Connection: Keep-Alive
29.08.2014 14:02:46 - << Server: Day-Servlet-Engine/4.1.64
29.08.2014 14:02:46 - << Content-Type: text/plain;charset=utf-8
29.08.2014 14:02:46 - << Content-Length: 26
29.08.2014 14:02:46 - << Date: Fri, 29 Aug 2014 18:02:46 GMT
29.08.2014 14:02:46 - << Set-Cookie: login-token=3529326c-1500-4888-a4a3-93d299726f28%3ac8be86c6-04bb-4d18-80d6-91278e08d720_98797d969258a669%3acrx.default; Path=/; HttpOnly; Secure
29.08.2014 14:02:46 - << Set-Cookie: cq-authoring-mode=CLASSIC; Path=/; Secure
29.08.2014 14:02:46 - <<
29.08.2014 14:02:46 - << R
29.08.2014 14:02:46 - << eplicationAction TEST ok.
29.08.2014 14:02:46 - Message sent.
29.08.2014 14:02:46 - ------------------------------------------------
29.08.2014 14:02:46 - Replication (TEST) of /content successful.
Replication test succeeded
```
