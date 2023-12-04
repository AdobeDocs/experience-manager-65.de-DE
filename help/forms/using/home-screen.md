---
title: Startbildschirm
description: Beschreibung der Komponenten des Startbildschirms der AEM Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 6c6fb516-1b11-4da4-b638-4388a070e397
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 12%

---

# Startbildschirm{#home-screen}

Wenn Sie sich bei der AEM Forms-App anmelden, werden Sie zum Startbildschirm weitergeleitet.

## Standardstartbildschirm {#default-home-screen}

Standardmäßig werden auf dem Startbildschirm alle Formulare einschließlich Startpunkten und Aufgaben (wenn der verbundene Server AEM Forms Workflow aktiviert ist) zusammen mit den zugehörigen Miniaturansichten angezeigt. Sie können die Miniaturansichten auf dem AEM Forms-Server angeben.

In der folgenden Abbildung werden die wichtigsten Komponenten auf dem standardmäßigen Startbildschirm mit Anmerkungen erläutert.

![Startbildschirm der Forms-App](assets/home-screen-1.png)

<!--Click to enlarge

![home-screen-1-1](assets/home-screen-1-1.png)-->

1. **Menüschaltfläche**: Wählen Sie die **Menü** Schaltfläche zum Navigieren zu Aufgaben, Forms, Postausgang und Einstellungen. Wenn Ihre AEM Forms-App mit einem AEM Forms JEE-Server verbunden ist, wird die Option &quot;Aufgaben&quot;angezeigt. Die Option Aufgaben speichert auch die Entwürfe, die aus Aufgaben in einem Prozess erstellt wurden. Bei AEM Forms OSGi-Servern ist die Option Aufgaben ausgeblendet. Der Postausgang speichert die gespeicherten Formulare und Entwürfe, bevor sie mit dem Server synchronisiert werden. Alle im Postausgang gespeicherten Formulare und Entwürfe werden beim Hochladen der App auf den AEM Forms-Server hochgeladen [mit dem Server synchronisiert](../../forms/using/sync-app.md). Weitere Informationen zu den Einstellungen finden Sie unter [Aktualisieren allgemeiner Einstellungen](../../forms/using/update-general-settings.md).
1. **Aufgabe oder Formular**: Wählen Sie die aufgelistete Aufgabe oder das Formular aus, mit der Sie arbeiten möchten.
1. **Horizontale Ellipse**: Gibt an, dass Aktionen für das Formular verfügbar sind. Durch Tippen auf die Auslassungspunkte werden die vom Autor bereitgestellten Aktionen und Beschreibungen angezeigt. Die **Entwurf löschen** und **Fertig** angezeigt, wenn Sie die Auslassungspunkte auswählen.
1. **Aktualisierungssymbol**: Wählen Sie das Aktualisierungssymbol aus, damit Sie Ihre App mit dem AEM Forms-Server synchronisieren können.

### Anpassen des Startbildschirms {#customizing-the-home-screen}

![Allgemeine Einstellungen](assets/gen-settings.png)

Sie können den Standardstartbildschirm der App entweder über die Registerkarte **[Allgemeine Einstellungen](../../forms/using/update-general-settings.md)** der App oder über die Registerkarte **Einstellungen** in HTML Workspace ändern.

Die Änderung an der Einstellung des Startbildschirms in der App wirkt sich auf den Startbildschirm des aktuell angemeldeten Benutzers oder des Benutzers auf dem aktuellen Mobilgerät aus.

Die in HTML Workspace vorgenommene Änderung wirkt sich jedoch auf alle AEM Forms-App-Benutzer aus, die beim AEM Forms-Server angemeldet sind.
