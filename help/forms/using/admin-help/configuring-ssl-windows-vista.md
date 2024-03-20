---
title: Konfigurieren von SSL unter Windows Vista
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren. Verwenden Sie das Java-Keytool und führen Sie es aus, um das SSL-Zertifikat mit RSA-Schlüsseln für die Authentifizierung zu generieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '173'
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
