---
title: Konfigurieren von SSL unter Windows Vista
description: Erfahren Sie, wie Sie SSL unter Windows Vista konfigurieren. Verwenden Sie das Java-Keytool und führen Sie es aus, um das SSL-Zertifikat mit RSA-Schlüsseln für die Authentifizierung zu generieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 36c4300d-7a44-41f4-b294-06f32bb01686
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 100%
---
# Konfigurieren von SSL unter Windows Vista {#configuring-ssl-on-windows-vista}

Zum Konfigurieren von SSL unter Windows Vista™ benötigen Sie ein SSL-Zertifikat mit RSA-Schlüsseln zur Authentifizierung. Sie können das Java-Keytool zum Erstellen des Zertifikats verwenden.

>[!NOTE]
>
>Windows Vista kann nicht mit DSA-Schlüsseln verwendet werden.

Sie können das Keytool mit einem einzelnen Befehl ausführen, der alle zum Erstellen von Zertifikat und Keystore erforderlichen Informationen enthält.

**Erstellen eines SSL-Zertifikats**

1. Wechseln Sie in einer Eingabeaufforderung zum Ordner „*`[JAVA HOME]`*/bin“ und geben Sie den folgenden Befehl ein, um das Zertifikat und den Keystore zu erstellen:

   `keytool -genkey -keyalg RSA -dname "CN=`*Host-Name* `, OU=`*Gruppenname* `, O=`*Firmenname* `,L=`*Stadt* `, S=`*Bundesland* `, C=`*Ländercode* `" -alias`*„LC Cert“* `-keypass` `key`*_* *Passwort* `-keystore`*Keystore-Name* `.keystore`

   >[!NOTE]
   >
   >Ersetzen Sie *`[JAVA_HOME]`* durch den Ordner, in dem das JDK installiert ist, und ersetzen Sie die kursiv gedruckten Werte durch die für Ihre Umgebung zutreffenden Werte.

1. Geben Sie `changeit` als Kennwort ein. Dies ist das Standardkennwort für Java-Installationen. Eventuell wurde es von Ihrem Systemadministrator geändert.
