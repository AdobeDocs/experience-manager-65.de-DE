---
title: Aktualisieren von allgemeinen Einstellungen
description: Aktualisieren von AEM Forms-App-Einstellungen wie für den Startbildschirm und Abrufen von Optionen für Startpunkte und Anlagen
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 3e74cda2-ba3e-4ee9-b7d0-76a804232199
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Aktualisieren von allgemeinen Einstellungen{#updating-general-settings}

In den allgemeinen Einstellungen der AEM Forms-App können Sie Einstellungen wie das Abrufen von Anlagen, den Offline-Modus, den Landingscreen, die Standardkategorie und die Häufigkeit der automatischen Speicherung festlegen.

## Aktualisieren von allgemeinen Einstellungen in der App {#working-with-the-form}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden alle Formulare und definierten Aufgaben auf Ihr Mobilgerät heruntergeladen.

Die sofort einsatzbereite Mobile App von AEM Forms lädt die mit den einzelnen Formularen verbundenen Anhänge nicht herunter, wenn Ihre Mobile App synchronisiert wird.

Ändern Sie auf der Registerkarte „Allgemein“ die Einstellungen für das Herunterladen von Anlagen, für den Offline-Modus, den Einstiegsbildschirm, die automatische Speicherung und die Synchronisierung. Sie können den [Startbildschirm](../../forms/using/home-screen.md) der App ändern.

**Navigieren Sie auf dem Startbildschirm zur Registerkarte „General“ (Allgemein)**

1. Um zum Einstellungsbildschirm zu gelangen, wählen Sie oben links im Startbildschirms die Menüschaltfläche und dann **Settings** (Einstellungen) aus.
1. Wählen Sie im Einstellungsbildschirm die Registerkarte „Allgemein“ aus.

   ![Allgemeine Einstellungen in der AEM Forms-App](assets/gen-settings-1.png)

   Bildschirm mit den allgemeinen Einstellungen

   >[!NOTE]
   >
   >Die Optionen werden auf verschiedenen Mobilgeräten möglicherweise unterschiedlich angezeigt.

### Allgemeine Einstellungen {#general-settings}

Sie können folgende Änderungen an den Einstellungen der App vornehmen.

* **Fetch attachments**: Mit dieser Option geben Sie an, ob die verknüpften Anlagen heruntergeladen werden sollen, wenn eine Aufgabe in Ihre App heruntergeladen wird.
* **Offline mode**: Hiermit aktivieren bzw. deaktivieren Sie den Offlinedienst für die AEM Forms-App. Weitere Informationen finden Sie unter [Arbeiten im Offline-Modus](/help/forms/using/work-offline-mode.md).
* **Landing screen**: Mit dieser Option legen Sie die Startposition ([Home screen](../../forms/using/home-screen.md)) für die App fest.
Verfügbare Optionen:

   * Formulare
   * Aufgaben
   * Favoriten

* **Default category (Standardkategorie)**: Mit dieser Option wählen Sie die Kategorie der Formulare aus, die auf dem Startbildschirm angezeigt wird. Wenn Sie „All“ (Alle) auswählen, können Sie alle Formulare auf dem Startbildschirm sehen. Kategorien werden basierend auf den Formularen ausgefüllt, die in der App geladen werden. Formulare sind in der App je nach den Formulareinstellungen im AEM Forms-Server verfügbar.

* **Häufigkeit der automatischen Speicherung**: Mit dieser Option legen Sie fest, wie häufig die [Mobile App Formulardaten lokal speichert](../../forms/using/autosave-data-app.md).
* **Synchronisierungsfrequenz**: Mit dieser Option legen Sie fest, wie häufig die [Mobile App im Online-Modus mit dem AEM Forms-Server synchronisiert wird](../../forms/using/sync-app.md).
  **Clear Local Data**: Löscht die Datenbank, einschließlich Einstellungen und lokaler Daten für alle Benutzer und Dateispeicher auf dem Gerät.

>[!NOTE]
>
>Das Löschen des Zwischenspeichers führt dazu, dass Sie sofort von der App abgemeldet werden.
>
>Sie erhalten jedoch eine Aufforderung zum Bestätigen des Cache-Löschvorgangs.
