---
title: Synchronisieren der App
description: Synchronisieren Sie die AEM Forms-App auf Ihrem Mobilgerät mit dem AEM-Formular-Server.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 6bb1d6df-b322-4112-bc25-6300877ee146
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
source-wordcount: '388'
ht-degree: 92%
---
# Synchronisieren der App{#synchronizing-the-app}

>[!NOTE]
>
>Die AEM Forms-App wird derzeit nicht mehr unterstützt. Bei Fragen oder Hilfe wenden Sie sich an [aemformsapp-android@adobe.com](mailto:aemformsapp-android@adobe.com).

## Synchronisieren der App {#synchronizing-the-app-1}

Die Formulare in Ihrer App werden vom AEM Forms-Server heruntergeladen. Die Formulare werden unter den Registerkarten „Aufgaben“ und „Formulare“ heruntergeladen. Aus Formularen erstellte Entwürfe werden auf der Registerkarte „Entwürfe“ heruntergeladen, und aus Aufgaben erstellte Entwürfe werden auf der Registerkarte „Aufgaben“ heruntergeladen. Für ein eigenständiges Formular auf dem OSGi-Server werden Formulare und Entwürfe auf den Registerkarten „Formulare“ bzw. „Entwürfe“ heruntergeladen.

Wenn Sie ein Formular ausfüllen und absenden, wird das Formular sofort wieder auf den AEM-Formular-Server hochgeladen, sofern die App online ist. Die Formulare werden beim Synchronisieren der App vom Server abgerufen. Die Entwürfe werden jedoch sofort mit dem Server synchronisiert, wenn die App online ist.

Wenn Sie mit dem AEM Forms-Server online sind, wird Ihre App standardmäßig alle 15 Minuten synchronisiert. Sie haben jedoch die Möglichkeit, die Synchronisierungsfrequenz zu ändern. Alternativ können Sie die Anwendung jederzeit manuell synchronisieren.

**Manuelles Synchronisieren der App**

Wählen Sie in der rechten unteren Ecke des Startbildschirms die Synchronisierungsschaltfläche ![App synchronisieren](assets/sync-app.png) aus.

**Ändern der Synchronisierungsfrequenz**

1. Um zum Einstellungsbildschirm zu gelangen, wählen Sie in der linken oberen Ecke des Startbildschirms die Menüschaltfläche und dann **Einstellungen** aus.
1. Wählen Sie im Einstellungsbildschirm die Registerkarte „Allgemein“ aus.

   ![Einstellung der Synchronisierungsfrequenz im Fenster „Allgemeine Einstellungen“](assets/gen-settings-2.png)

1. Wählen Sie unter der Option „Synchronisierungsfrequenz“ den Wert rechts neben der Synchronisierungsfrequenz aus.
1. Wählen Sie in der Dropdown-Liste die neue Synchronisierungsfrequenz aus.

### Technische Spezifikationen {#technical-specifications}

* Die Hauptlogik für die Übermittlung der Offline-App-Daten an den AEM-Formular-Server ist in „runtime/offline/util/offline.js“ enthalten.
* In der .js-Datei der Aufruf von processOfflineSubmittedSavedTasks(..) sendet die gespeicherten/gesendeten Aufgaben an den Server. Er behandelt auch etwaige Fehler oder Konflikte im Synchronisierungsprozess. Wenn die Übermittlung einer Aufgabe fehlschlägt, wird die Aufgabe in der App als fehlgeschlagen markiert. Darüber hinaus verbleibt die Aufgabe in Ihrem Postausgang.
* Die Funktionen „syncSubmittedTask()“ und „syncSavedTask()“ führen Vorgänge für einzelne Aufgaben durch.
* Der Aufruf der Funktion „processOfflineSubmittedSavedTasks()“ wird von der Aufgabenlistenkomponente initiiert, nachdem jemand die Synchronisierung des Offline-Status mit dem Server auswählt oder eine automatische Synchronisierung durch den Hintergrund-Thread erfolgt.
