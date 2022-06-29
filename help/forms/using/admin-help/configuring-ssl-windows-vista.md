---
title: SSL unter Windows Vista konfigurieren
seo-title: Configuring SSL on Windows Vista
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '155'
ht-degree: 100%

---

# SSL unter Windows Vista konfigurieren {#configuring-ssl-on-windows-vista}

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln zur Authentifizierung. Sie können das Java-Keytool zum Erstellen des Zertifikats verwenden.

>[!NOTE]
>
>Windows Vista kann nicht mit DSA-Schlüsseln verwendet werden.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen von Zertifikat und Keystore erforderlichen Informationen enthält.

**SSL-Zertifikat erstellen**

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[JAVA HOME]`*/bin“ und geben Sie den folgenden Befehl ein, um das Zertifikat und den Keystore zu erstellen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Host-Name* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Stadt* `, S=`*Bundesland* `, C=`*Ländercode* `" -alias`*„LC Cert“* `-keypass` `key`*_* *Passwort* `-keystore`*Keystore-Name* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.

1. Geben Sie `changeit` als Kennwort ein. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
