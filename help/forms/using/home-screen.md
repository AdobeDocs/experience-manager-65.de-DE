---
title: Startbildschirm
seo-title: Startbildschirm
description: Beschreibung der Komponenten des Startbildschirms in der AEM Forms-App
seo-description: Beschreibung der Komponenten des Startbildschirms in der AEM Forms-App
uuid: abc95e58-a685-42a9-82ab-4990155945d3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: ba79479b-4159-4a39-95eb-2285e7ece9d4
docset: aem65
exl-id: 6c6fb516-1b11-4da4-b638-4388a070e397
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 85%

---

# Startbildschirm{#home-screen}

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardstartbildschirm {#default-home-screen}

Auf dem Startbildschirm werden standardmäßig alle Formulare einschließlich Startpunkte und Aufgaben (wenn der verknüpfte Server mit dem Arbeitsablauf für AEM Forms aktiviert ist) zusammen mit den zugehörigen Miniaturbildern angezeigt. Sie können die Miniaturen im AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.

![Startbildschirm der Forms-App](assets/home-screen-1.png)

<!--Click to enlarge

![home-screen-1-1](assets/home-screen-1-1.png)-->

1. **Menüschaltfläche**: Tippen Sie auf die  **** Schaltfläche &quot;Menubution&quot;, um zu Aufgaben, Forms, Postausgang und Einstellungen zu navigieren. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option „Aufgaben“ angezeigt. Die Option „Aufgaben“ speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Beim AEM Forms OSGi-Server ist die Option „Aufgaben“ ausgeblendet. Im Postausgang werden die gespeicherten Formulare und Entwürfe vor der Synchronisierung mit dem Server abgelegt. Alle im Postausgang gespeicherten Formulare und Entwürfe werden auf den AEM Forms-Server hochgeladen, wenn die App [mit dem Server](../../forms/using/sync-app.md) synchronisiert wird. Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](../../forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Tippen Sie auf die aufgeführte Aufgabe oder das Formular, mit denen Sie arbeiten möchten.
1. **Horizontale Auslassungspunkte**: gibt an, dass Aktionen für das Formular zur Verfügung stehen. Beim Tippen auf die Auslassungspunkte werden die Aktionen und Beschreibungen angezeigt, die vom Autor angegeben wurden. Die Option **Entwurf löschen** und **Umfassend** ist sichtbar, wenn Sie auf die Auslassungspunkte tippen.
1. **Aktualisieren-Symbol**: Tippen Sie auf dieses Symbol, um Ihre App mit dem AEM Forms-Server zu synchronisieren.

### Anpassen des Startbildschirms  {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](../../forms/using/update-general-settings.md)** der App oder über die Registerkarte **Einstellungen** in HTML Workspace ändern.

Die Änderung an den Einstellungen des Startbildschirms der App hat Auswirkungen auf den Startbildschirm für den derzeit angemeldeten Benutzer oder den Benutzer am aktuellen Mobilgerät.

Die in HTML Workspace vorgenommene Änderung hingegen hat Auswirkungen für alle AEM Forms-App-Benutzer, die beim AEM Forms-Server angemeldet sind.
