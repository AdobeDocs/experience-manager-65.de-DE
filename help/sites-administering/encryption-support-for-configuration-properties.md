---
title: Verschlüsselungsunterstützung für Konfigurationseigenschaften
description: Erfahren Sie mehr über die Verschlüsselungsunterstützung für Konfigurationseigenschaften, die in AEM bereitgestellt werden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: security
exl-id: 3c3db1c8-5b22-45dd-aeaf-5cf830a9486b
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 34%

---

# Verschlüsselungsunterstützung für Konfigurationseigenschaften{#encryption-support-for-configuration-properties}

## Übersicht {#overview}

Unterstützung für die Speicherung aller OSGi-Konfigurationseigenschaften in sicherer, verschlüsselter Form anstatt als Klartext. Das Formular in der Web-Konsolen-Benutzeroberfläche dient zum Erstellen von verschlüsseltem Text aus unverschlüsseltem Text mit dem systemweiten Verschlüsselungs-Zentralschlüssel.

Die Unterstützung für das OSGi-Konfigurations-Plugin wurde hinzugefügt, um die Eigenschaft zu entschlüsseln, bevor sie von einem Dienst verwendet wird.

>[!NOTE]
>
>Dienste, die einen verschlüsselten Wert erwarten, müssen die IsProtected-Prüfung verwenden, um zu sehen, ob der Wert verschlüsselt ist, bevor versucht wird, ihn zu entschlüsseln, da er möglicherweise bereits entschlüsselt wurde.

## Verschlüsselungsunterstützung aktivieren {#enabling-encryption-support}

Diese Schritte zeigen, wie Sie das SMTP-Kennwort für den Mail-Dienst verschlüsseln. Sie können diese Schritte für eine OSGi-Eigenschaft ausführen, die verschlüsselt werden soll.

1. Navigieren Sie zur AEM-Web-Konsole unter *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr*
1. Gehen Sie in der oberen linken Ecke zu **Main - Crypto-Unterstützung.**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Die Seite **Adobe Experience Manager Web Console Crypto Support** wird angezeigt.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. Im **Nur Text** den Text der sensiblen Daten eingeben, die Sie schützen möchten.
1. Auswählen **Protect**. Der geschützte Text wird als verschlüsselter Text angezeigt.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Kopieren Sie den geschützten Text aus Schritt 5 und fügen Sie ihn in den Wert des OSGi-Formulars ein. In diesem Beispiel wurde die **SMTP-Kennwort** wird zum *Day CQ Mail Service*.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Speichern Sie die Eigenschaften des Day CQ Mail Service. Das SMTP-Kennwort wird jetzt als verschlüsselter Wert gesendet.

## Entschlüsselungsunterstützung {#decryption-support}

AEM stellt jetzt ein Configuration Plugin zum Entschlüsseln von Konfigurationseigenschaften bereit. Dieses AEM-Plug-in entschlüsselt und ruft automatisch die Klartext-Eigenschaften ab.
