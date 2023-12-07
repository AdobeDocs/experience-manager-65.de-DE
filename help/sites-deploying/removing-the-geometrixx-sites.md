---
title: Entfernen der Geometrixx-Sites
description: Erfahren Sie, wie Sie den Geometrixx-Beispielinhalt entfernen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 100%

---


# Entfernen der Geometrixx-Sites{#removing-the-geometrixx-sites}

AEM enthält standardmäßig eine Auswahl an Geometrixx-Beispiel-Websites. Sie können diese Beispielinhalte über den **Paket-Manager** entfernen.

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

Es gibt auch ein Super-Paket:

* `cq-geometrixx-all-pkg-5.6.12.zip`

Dieses Paket enthält alle oben genannten individuellen Pakete. Sie können sämtliche Geometrixx-bezogenen Inhalte auf einmal entfernen, indem Sie bei diesem Paket auf **Deinstallieren** klicken. Das Super-Paket wechselt dann in den Zustand „Deinstalliert“, und alle Einzelpakete verschwinden aus der Package Manager-Ansicht.

Sie verfügen nun über eine leere AEM-Instanz ohne jegliche Beispiel-Websites.

>[!NOTE]
>
>Beim Aktualisieren werden Geometrixx-Sites automatisch neu installiert. Entfernen Sie Geometrixx-Websites nach der Aktualisierung, wenn Sie diese Beispiele nicht benötigen.

