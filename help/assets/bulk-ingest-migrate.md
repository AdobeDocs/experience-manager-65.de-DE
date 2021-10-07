---
title: Feature Pack 18912 für Massenmigration von Assets installieren
description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in Dynamic Media in Adobe Experience Manager migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 53ea2cf7-d633-4ab9-a869-ce76eb1c01e5
source-git-commit: b2faf81983216bef9151548d90ae86f1c26a9f91
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 13%

---

# Feature Pack 18912 für Massenmigration von Assets installieren{#installing-feature-pack-for-bulk-asset-migration}

Die Installation von Feature Pack 18912 ist *optional*.

Mit Feature Pack 18912 können Sie Assets per FTP direkt in den Dynamic Media-Scene7-Modus in Adobe Experience Manager aufnehmen. Außerdem können Sie Assets von Dynamic Media Classic in den Modus Dynamic Media - Scene7 auf dem Experience Manager migrieren. Das Feature Pack ist unter [Adobe Professional Services](https://business.adobe.com/de/customers/consulting-services/main.html) verfügbar.

>[!IMPORTANT]
>
>Sie können das Feature Pack verwenden, um Assets in Experience Manager eigenständig von Dynamic Media Classic in den Dynamic Media-Scene7-Modus zu migrieren. Sie können Assets auch per Massen-Migration mithilfe der FTP-Funktion in Dynamic Media Classic migrieren. Aufgrund der Komplexität wird jedoch von Adobe *not* empfohlen, eine dieser Methoden zu verwenden.
>
>Daher wird dieses Feature Pack für die Migration *nur* im Rahmen eines Migrationsprojekts unterstützt, wenn es über [Adobe Professional Services](https://business.adobe.com/customers/consulting-services/main.html) durchgeführt wird.

Erstellen Sie vor der Installation des Feature Packs einen Dienstbenutzer und stellen Sie diese Informationen für die Adobe-Unterstützung bereit.

Siehe auch [Konfigurieren von Dynamic Media - Scene7 mode](/help/assets/config-dms7.md).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets:**

1. Navigieren Sie in Ihrer Experience Manager-Instanz zu **[!UICONTROL Tool]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]** und wählen Sie **[!UICONTROL Benutzer erstellen]**. Dieser Dienstbenutzer benötigt *Lese-/Schreibberechtigungen* für `/content/dam.`
1. Geben Sie in den Feldern **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein, z. B. **FTP-Benutzer**. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset aus FTP hochgeladen wird, gilt ein Asset als erstellt, wenn es auf den FTP-Server hochgeladen und an den Experience Manager gesendet wird.
1. Wenden Sie sich an den [Adobe-Support für Experience Manager](https://experienceleague.adobe.com/?support-solution=General#support), um Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Sie benötigen möglicherweise die folgenden Informationen, wenn Sie sich an den Support wenden:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Portnummer (standardmäßig ist die Portnummer 4502.)
   * Benutzername und Kennwort des Experience Manager-Dienstbenutzers aus dem vorherigen Schritt.

1. Der Adobe-Kundensupport für Experience Manager bietet Ihnen die FTP-Anmeldedaten und Zugriff auf Feature Pack 18912.
1. Wenn Sie das Feature Pack 18912 erhalten, installieren Sie es.

   Weitere Informationen zur Verwendung von Softwareverteilung und -paketen in Experience Manager finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md) .
