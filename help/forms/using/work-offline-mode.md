---
title: Arbeiten im Offline-Modus
description: Schalten Sie Ihr Mobilgerät außerhalb der Reichweite Ihres AEM Forms-Netzwerks offline oder in einen kompletten Offline-Modus und arbeiten Sie mit der AEM Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: ba4ceef1-510d-41ef-94b8-4834fb7de804
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 100%

---

# Arbeiten im Offline-Modus {#working-in-the-offline-mode}

Der Offline-Modus der AEM Forms-Mobile-App ermöglicht es, die Arbeit nahtlos fortzusetzen, selbst wenn die Mobile App offline geht. Sie können ein Formular öffnen, aktualisieren und senden, ohne dass eine Netzwerkverbindung erforderlich ist.

Sie beginnen Ihre Arbeit mit der AEM Forms-Mobile-App, indem Sie die Mobile App mit dem AEM Forms-Server synchronisieren. Alle Ihnen zugewiesenen Formulare werden in Ihrer App heruntergeladen.  Für AEM Forms auf JEE werden Aufgaben auf der Registerkarte „Aufgaben“ und mit Startpunkten verknüpfte Formulare sowie andere Formulare auf der Registerkarte „Formulare“ abgerufen.  Für AEM Forms auf OSGi werden nur Formulare auf der Registerkarte „Formulare“ geladen.

Ausführliche Informationen zum Synchronisieren der App finden Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md).

## Wie Sie Formulare offline verfügbar machen {#making-forms-available-offline}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden die Formulare auf Ihr mobiles Gerät heruntergeladen. Die mit der Aufgabe verknüpften Anhänge werden jedoch standardmäßig nicht heruntergeladen. Das bedeutet, dass Sie die Anhänge nur anzeigen können, wenn Sie online sind.  Um jedoch sicherzustellen, dass Sie den Anhang im Offline-Modus anzeigen können, ändern Sie die Standardeinstellungen in Ihrer App.

Um sicherzustellen, dass die zugehörigen Anhänge mit jedem Formular heruntergeladen werden, setzen Sie „Anhänge abrufen“ auf „EIN“.  Einzelheiten finden Sie unter [Aktualisieren von allgemeinen Einstellungen](/help/forms/using/update-general-settings.md).

Da das Herunterladen von Daten die Leistung des mobilen Geräts beeinträchtigen kann, ist die Option „Fetch attachments“ standardmäßig auf „OFF“ gesetzt. Wenn diese Einstellung auf „ON“ gesetzt wird, werden die Anlagen für alle Aufgaben, die danach vom Server heruntergeladen werden, auf das mobile Gerät geladen. Der Benutzer kann im Offline-Modus alle Aufgaben bearbeiten, die auf das Gerät heruntergeladen wurden, nachdem die Option **Fetch attachments** auf „ON“ gesetzt wurde.

## Konfiguration des Offlinedienstes für die AEM Forms-App {#configuring-offline-service-for-aem-forms-app-br}

Der Dienst für die AEM Forms Offline-App identifiziert die in einem Formular verwendeten Ressourcen. Die AEM Forms-App nutzt diesen Dienst zum Abrufen von Informationen zu Formularabhängigkeiten. Informationen zu Formularabhängigkeiten sind erforderlich, um Offline-Funktionalitäten zu ermöglichen.  Der Offline-Dienst für die AEM Forms-App legt die Pfade oder URLs der in einem Formular verwendeten Ressourcen im Cache ab.  Der Cache wird anhand der Änderungen im Formular und der für den Offlinedienst konfigurierten Gültigkeitsdauer aktualisiert. Durch das Zwischenspeichern der Pfa oder URLs der in einem Formular verwendeten Ressourcen wird die serverseitige Leistung verbessert.

Serverseitige Offlinekomponente der AEM Forms-App konfigurieren:

1. Navigieren Sie auf der Autoreninstanz zu **Adobe Experience Manager** > **Werkzeuge** > **Formulare** > **Offline-Service für Forms-Mobile- App konfigurieren**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Unter „Allgemeine Einstellungen“ können Sie Folgendes durchführen:

   * **Cache leeren**: Löscht den Server-seitigen Cache von den Formularabhängigkeiten.
   * **Konfiguration zurücksetzen**: Setzt die Offline-Konfiguration der AEM Forms-Mobile-App zurück.
   * **Cache-Gültigkeit**: Gibt den Gültigkeitszeitraum für den Server-seitigen Offline-Cache an.
   * **Ressourcenbeobachtungspfade**: Gibt die Pfade an, für die der Offline-Dienst Ressourcenänderungen überwacht.  Wenn in den angegebenen Pfaden Änderungen auftreten, wird der Offline-Cache aller abhängigen Formulare aktualisiert.  Beispiel: `/etc/clientlibs/fd,/content/dam/images`.

1. Geben Sie auf der Registerkarte **Manueller Ressourcen-Cache** die Formularabhängigkeiten an, die der Offline-Dienst nicht identifizieren kann. Sie können Ressourcen wie etwa Bilder angeben, die aus JavaScript geladen werden.  Die AEM Forms-App lädt diese Ressourcen auch für den Offline-Modus herunter.
