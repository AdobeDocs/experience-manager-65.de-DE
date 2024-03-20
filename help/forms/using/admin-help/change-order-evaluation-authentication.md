---
title: Ändern der Reihenfolge der Auswertung für die Authentifizierung
description: Sie können die Reihenfolge ändern, in der AEM Formulare mehrere Authentifizierungsanbieter auswertet.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7e29c9d4-fb82-4308-aac7-0f5cb1f4aef2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 59%

---

# Ändern der Reihenfolge der Auswertung für die Authentifizierung {#change-the-order-of-evaluation-for-authentication}

Wenn Sie mehrere Authentifizierungsanbieter konfiguriert haben, können Sie die Reihenfolge ändern, in der AEM Formulare sie zur Authentifizierung auswertet. Die Reihenfolge der Authentifizierungsanbieter, die in der Datei config.xml aufgeführt sind, bestimmt die Reihenfolge der Auswertung für die Authentifizierung.

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
