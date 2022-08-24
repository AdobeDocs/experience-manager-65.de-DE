---
title: Aktualisieren von allgemeinen Einstellungen
seo-title: Updating general settings
description: AEM Forms-App-Einstellungen wie den Startbildschirm aktualisieren und Optionen für Startpunkte und Anlagen abrufen
seo-description: Update AEM Forms app settings such as the Home screen and fetch Startpoints and attachments options
uuid: 650d677e-2b3c-498e-9e46-fa659af934ca
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 7fdb9fab-6bae-49b8-86b6-66138a2a6cd3
docset: aem65
exl-id: 3e74cda2-ba3e-4ee9-b7d0-76a804232199
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Aktualisieren von allgemeinen Einstellungen{#updating-general-settings}

Allgemeine Einstellungen des AEM Forms App können Sie die Einstellungen, z. B. Abrufen von Anlagen, running, von Landungsbildschirm, Standardkategorie und autsave Frequenz angeben.

## Aktualisieren von allgemeinen Einstellungen in der App {#working-with-the-form}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden alle Formulare und definierten Aufgaben auf Ihr mobiles Gerät heruntergeladen.

Die sofort einsatzbereite Mobile App von AEM Forms lädt die mit den einzelnen Formularen verbundenen Anhänge nicht herunter, wenn Ihre Mobile App synchronisiert wird.

Ändern Sie auf der Registerkarte „Allgemein“ die Einstellungen für das Herunterladen von Anlagen, für den Offline-Modus, den Einstiegsbildschirm, die automatische Speicherung und die Synchronisierung. Sie können den [Startbildschirm](../../forms/using/home-screen.md) der App ändern.

**Navigieren Sie zur Registerkarte „General“ auf dem Startbildschirm.**

1. Um den Einstellungsbildschirm aufzurufen, tippen Sie links unten auf dem Startbildschirm auf die Schaltfläche „Menü“ und dann auf **Einstellungen**.
1. Tippen Sie auf dem Bildschirm „Settings“ auf die Registerkarte „General“.

   ![Allgemeine Einstellungen in der AEM Forms-App](assets/gen-settings-1.png)

   Bildschirm „General Settings“ 

   >[!NOTE]
   >
   >Die Optionen werden auf verschiedenen Mobilgeräten möglicherweise unterschiedlich angezeigt.

### Allgemeine Einstellungen {#general-settings}

Sie können folgende Änderungen an den Einstellungen der App vornehmen.

* **Fetch attachments**: Mit dieser Option geben Sie an, ob die verknüpften Anlagen heruntergeladen werden sollen, wenn eine Aufgabe in Ihre App heruntergeladen wird.
* **Offline mode**: Hiermit aktivieren bzw. deaktivieren Sie den Offlinedienst für die AEM Forms-App. Weitere Informationen finden Sie unter [Arbeiten im Offlinemodus](/help/forms/using/work-offline-mode.md).
* **Landing screen**: Mit dieser Option legen Sie die Startposition ([Home screen](../../forms/using/home-screen.md)) für die App fest.
Verfügbare Optionen:

   * Formulare
   * Aufgaben
   * Favoriten

* **Default category**: Wählen Sie hier die Kategorie der Formulare aus, die auf dem Startbildschirm angezeigt wird. Wenn Sie „All“ auswählen, können Sie alle Formulare auf dem Startbildschirm sehen. Kategorien werden basierend auf den Formularen ausgefüllt, die in der App geladen werden. Formulare sind in der App je nach den Formulareinstellungen im AEM Forms-Server verfügbar.

* **Häufigkeit der automatischen Speicherung**: Mit dieser Option legen Sie fest, wie häufig die [Mobile App Formulardaten lokal speichert](../../forms/using/autosave-data-app.md).
* **Synchronisierungsfrequenz**: Mit dieser Option legen Sie fest, wie häufig die [Mobile App im Online-Modus mit dem AEM Forms-Server synchronisiert wird](../../forms/using/sync-app.md).
   **Clear Local Data**: Löscht die Datenbank, einschließlich Einstellungen und lokaler Daten für alle Benutzer und Dateispeicher auf dem Gerät.

>[!NOTE]
>
>Das Löschen des Zwischenspeichers führt dazu, dass Sie sofort von der App abgemeldet werden.
>
>Sie erhalten jedoch eine Aufforderung zum Bestätigen des Cache-Löschvorgangs.
