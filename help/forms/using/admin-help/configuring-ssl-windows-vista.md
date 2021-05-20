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
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 64%

---

# SSL unter Windows Vista konfigurieren {#configuring-ssl-on-windows-vista}

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln zur Authentifizierung. Sie können das Java-Keytool zum Erstellen des Zertifikats verwenden.

>[!NOTE]
>
>Windows Vista kann nicht mit DSA-Schlüsseln verwendet werden.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen von Zertifikat und Keystore erforderlichen Informationen enthält.

**SSL-Zertifikat erstellen**

1. Wechseln Sie an einer Eingabeaufforderung zum Ordner *`[JAVA HOME]`*/bin und geben Sie den folgenden Befehl ein, um das Zertifikat und den Keystore zu erstellen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Host* `, OU=`*NameGroup* `, O=`*NameFirma* `,L=`*NameStadt* `, S=`** `, C=`*NameStateCountry Code* `" -alias`*&quot;LC Cert&quot;* `-keypass` `key`*_* ** `-keystore`*passwordkeystorename* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie kursiv den Text durch die Werte, die Ihrer Umgebung entsprechen.*

1. Geben Sie `changeit` als Kennwort ein. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
