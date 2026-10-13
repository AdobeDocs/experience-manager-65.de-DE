---
title: Installieren von Feature Pack 18912 für die Massenmigration von Assets
description: Mit Feature Pack 18912 können Sie Assets entweder per FTP stapelweise erfassen oder Assets aus Dynamic Media Classic in Dynamic Media in Adobe Experience Manager migrieren. Dieses optionale Feature Pack ist über den Adobe-Support verfügbar.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 53ea2cf7-d633-4ab9-a869-ce76eb1c01e5
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%
---
# Installieren von Feature Pack 18912 für die Massenmigration von Assets{#installing-feature-pack-for-bulk-asset-migration}

Die Installation von Feature Pack 18912 ist *optional*.

Mit Feature Pack 18912 können Sie Assets per FTP stapelweise direkt in den Dynamic Media-Scene7-Modus in Adobe Experience Manager aufnehmen. Außerdem können Sie Assets aus Dynamic Media Classic in den Dynamic Media-Scene7-Modus in Experience Manager migrieren. Das Feature Pack erhalten Sie von [Adobe Professional Services](https://business.adobe.com/de/customers/consulting-services/main.html).

>[!IMPORTANT]
>
>Mit dem Feature Pack können Sie Assets eigenständig von Dynamic Media Classic in den Dynamic Media-Scene7-Modus in Experience Manager migrieren. Sie können Assets auch per Massenmigration mithilfe der FTP-Funktion in Dynamic Media Classic migrieren. Adobe empfiehlt jedoch aufgrund der Komplexität *nicht*, eine dieser Methoden zu verwenden.
>
>Daher wird dieses Feature Pack für die Migration *ausschließlich* im Rahmen eines Migrationsprojekts über [Adobe Professional Services](https://business.adobe.com/de/customers/consulting-services/main.html) unterstützt.

Erstellen Sie vor der Installation des Feature Packs einen Service-Benutzer und stellen Sie diese Informationen für den Adobe-Support bereit.

Siehe auch [Konfigurieren von Dynamic Media – Scene7-Modus](/help/assets/config-dms7.md).

**Gehen Sie zur Installation von Feature Pack 18912 für die Massenmigration von Assets wie folgt vor:**

1. Navigieren Sie in Ihrer Experience Manager-Instanz zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]** und wählen Sie **[!UICONTROL Benutzer erstellen]** aus. Dieser Dienstbenutzer benötigt *Lese-/Schreibberechtigungen* für `/content/dam.`
1. Geben Sie in den Feldern **[!UICONTROL ID]** und **[!UICONTROL Kennwort]** einen Benutzernamen und ein Kennwort ein, z. B. **FTP-Benutzer**. Dieser Name wird in der Timeline als der Benutzer angezeigt, der das Asset erstellt hat. Wenn ein Asset über FTP hochgeladen wird, gilt es als erstellt, sobald es auf den FTP-Server hochgeladen und in Experience Manager gepusht wurde.
1. Kontaktieren Sie den [Kunden-Support von Adobe für Experience Manager](https://experienceleague.adobe.com/de?support-solution=General&lang=de#support), um den Download von Feature Pack 18912 anzufordern. Sie benötigen möglicherweise die folgenden Informationen, wenn Sie sich an den Support wenden:

   * Server-IP-Adresse für die Autoreninstanz einschließlich der Port-Nummer (standardmäßig 4502).
   * Benutzername und Kennwort des Experience Manager-Service-Benutzers aus dem vorherigen Schritt.

1. Der Kunden-Support von Adobe für Experience Manager teilt Ihnen die FTP-Anmeldedaten für den Zugriff auf Feature Pack 18912 mit.
1. Installieren Sie Feature Pack 18912 nach dem Herunterladen.

   Weitere Informationen zur Verwendung von Software Distribution und Paketen in Experience Manager finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).
