---
title: SSL unter Windows Vista konfigurieren
seo-title: SSL unter Windows Vista konfigurieren
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren.
seo-description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e

---


# SSL unter Windows Vista konfigurieren {#configuring-ssl-on-windows-vista}

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln zur Authentifizierung. Sie können das Java-Keytool zum Erstellen des Zertifikats verwenden.

>[!NOTE]
>
>Windows Vista kann nicht mit DSA-Schlüsseln verwendet werden.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen von Zertifikat und Keystore erforderlichen Informationen enthält.

**SSL-Zertifikat erstellen**

1. In a command prompt, navigate to *`[JAVA HOME]`*/bin and type the following command to create the certificate and keystore:

   `keytool -genkey -keyalg RSA -dname "CN=`*Hostname *`, OU=`*Gruppenname* `, O=`*Firmenname *`,L=`*Stadt* `, S=`*Land *`, C=`** `" -alias`**`-keypass``key`** ** `-keystore`**Land CodeLayout&quot;LC-Zertifikat&quot;_Kennwortkeystorename`.keystore`

   >[!NOTE]
   >
   >Replace *`[JAVA_HOME]`with the directory where the JDK is installed, and replace the text in italic with values that correspond with your environment.*

1. Type `changeit` as the password. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.

