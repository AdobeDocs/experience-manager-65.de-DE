---
title: Ändern der Reihenfolge der Auswertung für die Authentifizierung
description: Sie können die Reihenfolge ändern, in der AEM Forms mehrere Authentifizierungsanbieter auswertet.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7e29c9d4-fb82-4308-aac7-0f5cb1f4aef2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: ht
source-wordcount: '159'
ht-degree: 100%

---

# Ändern der Reihenfolge der Auswertung für die Authentifizierung {#change-the-order-of-evaluation-for-authentication}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Wenn Sie mehrere Authentifizierungsanbieter konfiguriert haben, können Sie die Reihenfolge ändern, in der AEM Forms diese Anbieter zur Authentifizierung auswertet. Die Reihenfolge, in der die Authentifizierungsanbieter in der Datei „config.xml“ aufgelistet werden, bestimmt die Reihenfolge der Auswertung für die Authentifizierung.

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf „Exportieren“ und speichern Sie die Konfigurationsdatei an einem anderen Speicherort.
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

   Bearbeiten Sie unter `<entry key="order" value="3" />` den Wert für jeden Knoten, um die Reihenfolge der Authentifizierungsbewertung festzulegen.

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf „Konfiguration“ > „Konfigurationsdateien importieren und exportieren“.
1. Klicken Sie auf „Durchsuchen“, um die Datei zu suchen, dann auf „Importieren“ und anschließend auf „OK“.
