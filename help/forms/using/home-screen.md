---
title: Startbildschirm
description: Beschreibung der Komponenten des Startbildschirms der AEM Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 6c6fb516-1b11-4da4-b638-4388a070e397
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 96%
---
# Startbildschirm{#home-screen}

>[!NOTE]
>
>Die AEM Forms-App wird derzeit nicht mehr unterstützt. Bei Fragen oder Hilfe wenden Sie sich an [aemformsapp-android@adobe.com](mailto:aemformsapp-android@adobe.com).

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardmäßiger Startbildschirm {#default-home-screen}

Standardmäßig werden auf dem Startbildschirm alle Formulare einschließlich Startpunkten und Aufgaben (wenn der verbundene Server für den AEM Forms-Workflow aktiviert ist) zusammen mit den zugehörigen Miniaturansichten angezeigt. Sie können die Miniaturansichten auf dem AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.

![Startbildschirm der Forms-App](assets/home-screen-1.png)

<!--
Click to enlarge

![home-screen-1-1](assets/home-screen-1-1.png)
-->

1. **Menüschaltfläche**: Wählen Sie die Schaltfläche **Menü**, um zu Aufgaben, Formularen, Posteingang und Einstellungen zu navigieren. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option „Aufgaben“ angezeigt. Die Option „Aufgaben“ speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Bei AEM Forms-OSGi-Servern ist die Option „Aufgaben“ ausgeblendet. Der Postausgang speichert die gespeicherten Formulare und Entwürfe, bevor sie mit dem Server synchronisiert werden. Alle im Postausgang gespeicherten Formulare und Entwürfe werden auf den AEM Forms-Server hochgeladen, wenn die App [mit dem Server synchronisiert wird](../../forms/using/sync-app.md). Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](../../forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Wählen Sie die aufgelistete Aufgabe oder das Formular, mit dem Sie arbeiten möchten.
1. **Horizontale Auslassungspunkte**: Gibt an, dass Aktionen für das Formular verfügbar sind. Durch Tippen auf die Auslassungspunkte werden die von der Autorin oder dem Autor bereitgestellten Aktionen und Beschreibungen angezeigt. Die Optionen **Entwurf löschen** und **Abgeschlossen** sind nur sichtbar, wenn Sie die Auslassungspunkte auswählen.
1. **Aktualisierungssymbol**: Wählen Sie das Aktualisierungssymbol, damit Sie Ihre App mit dem AEM Forms-Server synchronisieren können.

### Anpassen des Startbildschirms {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](../../forms/using/update-general-settings.md)** der App oder über die Registerkarte **Einstellungen** in HTML Workspace ändern.

Die Änderung an der Einstellung des Startbildschirms in der App wirkt sich auf den Startbildschirm der aktuell angemeldeten Person auf dem aktuellen Mobilgerät aus.

Die in HTML Workspace vorgenommene Änderung hingegen hat Auswirkungen für alle Benutzenden der AEM Forms-App, die beim AEM Forms-Server angemeldet sind.
