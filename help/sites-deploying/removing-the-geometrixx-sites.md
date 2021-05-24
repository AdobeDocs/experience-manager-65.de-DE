---
title: Entfernen der Geometrixx-Websites
seo-title: Entfernen der Geometrixx-Websites
description: Erfahren Sie, wie Sie den Geometrixx-Beispielinhalt entfernen.
seo-description: Erfahren Sie, wie Sie den Geometrixx-Beispielinhalt entfernen.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
source-git-commit: 1f7a45adc73b407c402a51b061632e72d97ca306
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 100%

---


# Entfernen der Geometrixx-Websites{#removing-the-geometrixx-sites}

AEM enthält standardmäßig eine Auswahl an Geometrixx-Beispielwebsites. Sie können diese Beispielinhalte über den **Paketmanager** entfernen.

Die einzelnen Geometrixx-bezogenen Pakete sind:

* `cq-geometrixx-outdoors-ugc-pkg-<version>.zip`
* `cq-geometrixx-pkg-<version>.zip`
* `cq-content-mac-<version>.zip`
* `cq-geometrixx-login-pkg-<version>.zip`
* `cq-geometrixx-users-pkg-<version>.zip`
* `cq-geometrixx-workflow-pkg-<version>.zip`
* `cq-geometrixx-outdoors-pkg-<version>.zip`
* `cq-geometrixx-commons-pkg-<version>.zip`
* `cq-geometrixx-media-pkg-<version>.zip`

Entfernen Sie einzelne Pakete, indem Sie dafür auf **Deinstallieren** klicken.

Darüber hinaus gibt es noch ein Gesamtpaket:

* `cq-geometrixx-all-pkg-5.6.12.zip`

Dieses Paket enthält sämtliche oben genannten Einzelpakete. Sie können sämtliche Geometrixx-bezogenen Inhalte auf einmal entfernen, indem Sie bei diesem Paket auf **Deinstallieren** klicken. Das Gesamtpaket wechselt in den Zustand „Deinstalliert“ und alle Einzelpakete verschwinden aus der Paketmanageransicht.

Sie verfügen nun über eine leere AEM-Instanz ohne jegliche Beispielwebsites.

>[!NOTE]
>
>Bei einem Upgrade werden alle Geometrixx-Websites automatisch neu installiert. Sollten Sie diese Beispieldateien nicht wünschen, können Sie die Geometrixx-Websites nach dem Upgrade erneut entfernen.

