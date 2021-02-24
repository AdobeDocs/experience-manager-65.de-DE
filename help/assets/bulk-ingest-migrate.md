---
title: Installieren von Feature Pack 18912 für die Migration von Massenelementen
description: Mit Feature Pack 18912 können Sie Assets per FTP stapelweise erfassen oder Assets von Dynamic Media Classic auf AEM nach Dynamic Media migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
translation-type: tm+mt
source-git-commit: 18e62f8fb46de20e1668b2dcdcedf68fe4622b50
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 23%

---


# Installieren von Feature Pack 18912 für Massenmigration von Assets{#installing-feature-pack-for-bulk-asset-migration}

Die Installation von Feature Pack 18912 ist *optional*.

Mit Feature Pack 18912 können Sie Assets per FTP AEM direkt in den Dynamic Media - Scene7-Modus importieren oder Assets von Dynamic Media Classic in den Dynamic Media - Scene7-Modus migrieren, AEM. Das Feature Pack ist unter [Adobe Professional Services](https://www.adobe.com/de/experience-cloud/consulting-services.html) verfügbar.

>[!NOTE]
>
>Obwohl Sie das Feature Pack verwenden können, um Assets von Dynamic Media Classic in den Dynamic Media - Scene7-Modus zu migrieren, AEM Assets mit der FTP-Funktion in Dynamic Media Classic stapelweise zu migrieren, empfiehlt die Adobe diese Methode aufgrund der Komplexität, die damit verbunden ist, nicht.**
>
>Daher werden Migrationspaket wie dieses nur als Teil eines Migrationsprojekts unterstützt, wenn es über [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html) durchgeführt wird.**

Bevor Sie das Feature Pack installieren können, müssen Sie zunächst einen Dienstbenutzer erstellen und diese Informationen zur Unterstützung der Adobe bereitstellen.

Siehe auch [Konfigurieren von Dynamic Media - Scene7-Modus](/help/assets/config-dms7.md).

**So installieren Sie Feature Pack 18912 für die Massenmigration von Assets**

1. Navigieren Sie in Ihrer AEM-Instanz zu **[!UICONTROL Tools > Sicherheit > Benutzer]** und wählen Sie **[!UICONTROL Benutzer erstellen]**. Dieser Dienstbenutzer benötigt *Lese-/Schreibberechtigungen* für `/content/dam.`
1. Geben Sie in den Feldern **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein, z. B. **FTP-Benutzer**. Dieser Name wird in der Zeitleiste als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, wenn es auf den FTP-Server hochgeladen und in AEM gepusht wurde.
1. Wenden Sie sich an den [Adobe Enterprise-Kundendienst für Experience Manager](https://experienceleague.adobe.com/?support-solution=General#support), um Zugriff auf Feature Pack 18912 zum Herunterladen anzufordern. Möglicherweise benötigen Sie beim Kontakt mit dem Support die folgenden Informationen:

   * Server-IP-Adresse für Ihre Autoreninstanz, einschließlich der Anschlussnummer (standardmäßig ist die Anschlussnummer 4502).
   * AEM Dienstbenutzer-Benutzername und Kennwort aus dem vorherigen Schritt.

1. Adobe Enterprise-Kundendienst für AEM bietet Ihnen die FTP-Anmeldeinformationen und Zugriff auf Feature Pack 18912.
1. Wenn Sie das Feature Pack 18912 erhalten, installieren Sie es.

   Weitere Informationen zur Verwendung von Software-Distribution und -Paketen in AEM finden Sie unter [Wie mit Paketen funktioniert](/help/sites-administering/package-manager.md).
