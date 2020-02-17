---
title: Installieren von Feature Pack 18912 für die Migration von Massenelementen
description: Mit Feature Pack 18912 können Sie Assets per FTP stapelweise erfassen oder Assets von Dynamic Media Classic in dynamische Medien auf AEM migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Installing feature pack 18912 for bulk asset migration{#installing-feature-pack-for-bulk-asset-migration}

The installation of feature pack 18912 is *optional*.

Mit Feature Pack 18912 können Sie Assets entweder per FTP direkt in den Modus &quot;Dynamische Medien - Scene7&quot;in AEM stapeln oder Assets aus &quot;Dynamische Medien Classic&quot;in den Modus &quot;Dynamische Medien - Scene7&quot;in AEM migrieren. Das Feature Pack ist bei [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)erhältlich.

>[!NOTE]
>
>Obwohl Sie das Feature Pack verwenden können, um Assets von Dynamische Medien Classic in den Dynamischen Medien - Scene7-Modus in AEM zu migrieren oder Assets per Massen-Massen-Migration mithilfe der FTP-Funktion in Dynamischen Medien Classic durchzuführen, empfiehlt Adobe diese Methode aufgrund der damit verbundenen Komplexität *nicht* .
>
>Daher werden Migrationspaket, wie dieses, *nur* im Rahmen eines Migrationsprojekts unterstützt, wenn es über [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html)durchgeführt wird.

Bevor Sie das Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen dem Adobe-Support bereitstellen.

See also [Configuring Dynamic Media - Scene7 mode](/help/assets/config-dms7.md).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets**

1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Tools > Sicherheit > Benutzer]** und wählen Sie **[!UICONTROL Benutzer erstellen]**. Dieser Dienstbenutzer benötigt *Lese-/Schreibberechtigungen* für `/content/dam.`
1. Geben Sie in den Feldern **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein, z. B. **FTP-Benutzer**. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Wenden Sie sich an den [Adobe Enterprise-Support für Experience Manager](https://helpx.adobe.com/contact/enterprise-support.ec.html) , um Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Möglicherweise benötigen Sie beim Kontakt mit dem Support die folgenden Informationen:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Anschlussnummer (standardmäßig ist die Anschlussnummer 4502)
   * Benutzername und Kennwort des AEM-Dienstbenutzers aus dem vorherigen Schritt.

1. Der Adobe Enterprise Support für AEM bietet die FTP-Anmeldeinformationen und Zugriff auf Feature Pack 18912.
1. Wenn Sie das Feature Pack 18912 erhalten, installieren Sie es.

   See [How to Work with Packages](/help/sites-administering/package-manager.md) for more information on using Package Share and packages in AEM.

