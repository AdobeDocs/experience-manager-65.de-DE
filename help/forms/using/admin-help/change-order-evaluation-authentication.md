---
title: Die Reihenfolge der Auswertung für die Authentifizierung ändern
seo-title: Die Reihenfolge der Auswertung für die Authentifizierung ändern
description: Sie können die Reihenfolge ändern, in der AEM Forms mehrere Anbieter zur Authentifizierung auswertet.
seo-description: Sie können die Reihenfolge ändern, in der AEM Forms mehrere Anbieter zur Authentifizierung auswertet.
uuid: c2693e5b-cf09-4bb8-815a-2b20ebf6eea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5434df9c-ecf6-450a-aa7e-d9ab69b66fe6
exl-id: 7e29c9d4-fb82-4308-aac7-0f5cb1f4aef2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 91%

---

# Die Reihenfolge der Auswertung für die Authentifizierung ändern {#change-the-order-of-evaluation-for-authentication}

Wenn Sie mehrere Authentifizierungsanbieter konfiguriert haben, können Sie die Reihenfolge ändern, in der AEM Forms diese Anbieter zur Authentifizierung auswertet. Die Reihenfolge, in der die Authentifizierungsanbieter in der Datei „config.xml“ aufgelistet werden, bestimmt die Reihenfolge der Auswertung für die Authentifizierung.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. Suchen Sie den folgenden Knoten in der Datei:

   ```xml
    <node name="AuthSchemes">
        <map />
            <node name="CertificateAuth">
                <map>
                    <entry key="order" value="3" />
                    <entry key="name" value="edc.server.auth.scheme.certificate" />
                </map>
        </node>
        <node name="Kerberos">
            <map>
                <entry key="kerberosSPN" value="defaultSPN" />
                <entry key="order" value="1" />
                <entry key="name" value="edc.server.auth.scheme.kerberos" />
            </map>
    </node>
   ```

   Bearbeiten Sie in `<entry key="order" value="3" />` den Wert für jeden Knoten, um die Reihenfolge der Authentifizierungsauswertung festzulegen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in User Management auf „Konfiguration“ > „Konfigurationsdateien im- und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, klicken Sie dann auf „Importieren“ und anschließend auf „OK“.
