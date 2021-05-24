---
title: Verschlüsselungsunterstützung für Konfigurationseigenschaften
seo-title: Verschlüsselungsunterstützung für Konfigurationseigenschaften
description: Verschlüsselungsunterstützung für Konfigurationseigenschaften
seo-description: 'null'
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
exl-id: 3c3db1c8-5b22-45dd-aeaf-5cf830a9486b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 87%

---

# Verschlüsselungsunterstützung für Konfigurationseigenschaften{#encryption-support-for-configuration-properties}

## Überblick {#overview}

Unterstützung für die Speicherung aller OSGi-Konfigurationseigenschaften in sicherer, verschlüsselter Form anstatt als Klartext. Das Formular in der Web Console-Benutzeroberfläche wird verwendet, um verschlüsselten Text aus Klartext mithilfe des systemweiten Übergeordneten Verschlüsselungsschlüssels zu erstellen.

Die Unterstützung für das OSGi-Konfigurations-Plug-in wurde hinzugefügt, um die Eigenschaft zu entschlüsseln, bevor sie von einem Dienst verwendet wird.

>[!NOTE]
>
>Dienste, die einen verschlüsselten Wert erwarten, müssen die isProtected-Prüfung verwenden, um zu sehen, ob der Wert verschlüsselt ist, bevor die Entschlüsselung begonnen werden kann, da dieser bereits zuvor entschlüsselt worden sein könnte.

## Aktivieren von Verschlüsselungsunterstützung  {#enabling-encryption-support}

Diese Schritte zeigen, wie das SMTP-Kennwort für den Mail-Dienst verschlüsselt wird. Sie können diese Schritte für eine OSGI-Eigenschaft ausführen, die verschlüsselt werden soll.

1. Wechseln Sie zur AEM Web-Konsole unter *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Gehen Sie in der oberen linken Ecke zu **Main - Crypto-Unterstützung.**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Die Seite **Adobe Experience Manager Web Console Crypto Support** wird angezeigt.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. Geben Sie im Feld **Normaltext** den Text der sensiblen Daten ein, die geschützt werden sollen.
1. Wählen Sie **Schützen**. Der geschützte Text wird als verschlüsselter Text angezeigt.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Kopieren Sie den geschützten Text aus Schritt 5 und fügen Sie ihn in den OSGI-Formularwert ein. In diesem Beispiel wird das verschlüsselte **SMTP-Kennwort** dem *Day CQ Mail Service* hinzugefügt.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Speichern Sie die Eigenschaften von „Day CQ Mail Service“. Das SMTP-Kennwort wird jetzt als verschlüsselter Wert gesendet.

## Entschlüsselungsunterstützung  {#decryption-support}

AEM bietet jetzt ein Konfigurations-Plug-in zur Entschlüsselung von Konfigurationseigenschaften. Dieses AEM-Plug-in entschlüsselt automatisch und ruft die Klartext-Eigenschaften ab.
