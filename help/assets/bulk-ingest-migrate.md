---
title: Installieren von Feature Pack 18912 für die Massenmigration von Assets
description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets von Dynamic Media Classic AEM in Dynamic Media migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
feature: Asset-Management
role: User, Admin
exl-id: 53ea2cf7-d633-4ab9-a869-ce76eb1c01e5
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 24%

---

# Installieren von Feature Pack 18912 für die Massenmigration von Assets{#installing-feature-pack-for-bulk-asset-migration}

Die Installation von Feature Pack 18912 ist *optional*.

Mit Feature Pack 18912 können Sie Assets entweder per FTP AEM direkt in Dynamic Media - Scene7 aufnehmen oder Assets aus Dynamic Media Classic in den Modus Dynamic Media - Scene7 AEM migrieren. Das Feature Pack ist unter [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html) verfügbar.

>[!NOTE]
>
>Sie können das Feature Pack zwar verwenden, um Assets eigenständig von Dynamic Media Classic in den Dynamic Media-Scene7-Modus zu migrieren, AEM Assets mit der FTP-Funktion in Dynamic Media Classic stapelweise migrieren. Aufgrund der Komplexität empfiehlt die Adobe jedoch *nicht* diese Methode.
>
>Daher werden Migrationspaket-Packs wie dieses *nur* als Teil eines Migrationsprojekts unterstützt, wenn sie über [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html) durchgeführt werden.

Bevor Sie das Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen für die Adobe-Unterstützung bereitstellen.

Siehe auch [Konfigurieren von Dynamic Media - Scene7-Modus](/help/assets/config-dms7.md).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets**

1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Tools > Sicherheit > Benutzer]** und wählen Sie **[!UICONTROL Benutzer erstellen]**. Dieser Dienstbenutzer benötigt *Lese-/Schreibberechtigungen* für `/content/dam.`
1. Geben Sie in den Feldern **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein, z. B. **FTP-Benutzer**. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Wenden Sie sich an [Adobe Enterprise Customer Care für Experience Manager](https://experienceleague.adobe.com/?support-solution=General#support), um Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Sie benötigen möglicherweise die folgenden Informationen, wenn Sie sich an den Support wenden:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Portnummer (standardmäßig ist die Portnummer 4502.)
   * Benutzername und Kennwort AEM Dienstbenutzers aus dem vorherigen Schritt.

1. Adobe Enterprise-Kundenunterstützung für AEM bietet Ihnen die FTP-Anmeldedaten und Zugriff auf Feature Pack 18912.
1. Wenn Sie das Feature Pack 18912 erhalten, installieren Sie es.

   Weitere Informationen zur Verwendung von Softwareverteilung und -paketen in AEM finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md) .
