---
title: Verschlüsselungsunterstützung für Konfigurationseigenschaften
description: Erfahren Sie mehr über die Verschlüsselungsunterstützung für Konfigurationseigenschaften in AEM.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: security
exl-id: 3c3db1c8-5b22-45dd-aeaf-5cf830a9486b
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
    internal-label: Administration and security
subfeature_v2:
  - id: c35bc059-fd80-4a01-91a6-e48da3c76758
    internal-label: Security practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 100%
---
# Verschlüsselungsunterstützung für Konfigurationseigenschaften{#encryption-support-for-configuration-properties}

## Übersicht {#overview}

Unterstützung für die Speicherung aller OSGi-Konfigurationseigenschaften in sicherer, verschlüsselter Form anstatt als Klartext. Das Formular in der Web-Konsolen-Benutzeroberfläche dient zum Erstellen von verschlüsseltem Text aus unverschlüsseltem Text mit dem systemweiten Verschlüsselungs-Zentralschlüssel.

Die Unterstützung für das OSGi-Konfigurations-Plug-in wurde hinzugefügt, um die Eigenschaft zu entschlüsseln, bevor sie von einem Dienst verwendet wird.

>[!NOTE]
>
>Dienste, die einen verschlüsselten Wert erwarten, müssen anhand der isProtected-Prüfung feststellen, ob der Wert verschlüsselt ist, bevor mit der Entschlüsselung begonnen werden kann. Dieser könnte nämlich bereits zuvor entschlüsselt worden sein.

## Aktivieren der Verschlüsselungsunterstützung {#enabling-encryption-support}

Die folgenden Schritte zeigen, wie das SMTP-Kennwort für den E-Mail-Dienst verschlüsselt wird. Sie können diese Schritte für eine OSGI-Eigenschaft ausführen, die verschlüsselt werden soll.

1. Navigieren Sie zur AEM-Web-Konsole unter *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr*
1. Gehen Sie in der oberen linken Ecke zu **Main - Crypto-Unterstützung.**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Die Seite **Adobe Experience Manager Web Console Crypto Support** wird angezeigt.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. Geben Sie im Feld für **Nur-Text** den Text der sensiblen Daten ein, die geschützt werden sollen.
1. Wählen Sie die **Schaltfläche zum Schützen** aus. Der geschützte Text wird als verschlüsselter Text angezeigt.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Kopieren Sie den geschützten Text aus Schritt 5 und fügen Sie ihn in den OSGI-Formularwert ein. In diesem Beispiel wird das verschlüsselte **SMTP-Kennwort** dem *Day CQ Mail Service* hinzugefügt.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Speichern Sie die Eigenschaften von „Day CQ Mail Service“. Das SMTP-Kennwort wird jetzt als verschlüsselter Wert gesendet.

## Entschlüsselungsunterstützung {#decryption-support}

AEM bietet nun ein Konfigurations-Plug-in zur Entschlüsselung von Konfigurationseigenschaften. Dieses AEM-Plug-in führt eine automatische Entschlüsselung durch und ruft die Klartext-Eigenschaften ab.
