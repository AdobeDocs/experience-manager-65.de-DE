---
title: Konfigurieren von SSL unter Windows Vista
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren. Verwenden Sie das Java-Keytool und führen Sie es aus, um das SSL-Zertifikat mit RSA-Schlüsseln für die Authentifizierung zu generieren.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 50%

---

# Konfigurieren von SSL unter Windows Vista {#configuring-ssl-on-windows-vista}

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln für die Authentifizierung. Sie können das Java-Keytool verwenden, um das Zertifikat zu erstellen.

>[!NOTE]
>
>Windows Vista funktioniert nicht mit DSA-Schlüsseln.

Sie können Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen des Zertifikats und Keystore erforderlichen Informationen enthält.

**Erstellen eines SSL-Zertifikats**

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[JAVA HOME]`*/bin“ und geben Sie den folgenden Befehl ein, um das Zertifikat und den Keystore zu erstellen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Host-Name* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Stadt* `, S=`*Bundesland* `, C=`*Ländercode* `" -alias`*„LC Cert“* `-keypass` `key`*_* *Passwort* `-keystore`*Keystore-Name* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.

1. Geben Sie `changeit` als Kennwort ein. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
