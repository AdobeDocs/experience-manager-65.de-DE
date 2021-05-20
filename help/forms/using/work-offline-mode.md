---
title: Arbeiten im Offlinemodus
seo-title: Arbeiten im Offlinemodus
description: Arbeiten Sie auf Ihrem Mobilgerät offline in der AEM Forms-App, wenn Sie sich außerhalb der Reichweite Ihres AEM Forms-Netzwerks oder vollständig im Offlinemodus befinden.
seo-description: Arbeiten Sie auf Ihrem Mobilgerät offline in der AEM Forms-App, wenn Sie sich außerhalb der Reichweite Ihres AEM Forms-Netzwerks oder vollständig im Offlinemodus befinden.
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
exl-id: ba4ceef1-510d-41ef-94b8-4834fb7de804
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 84%

---

# Arbeiten im Offlinemodus {#working-in-the-offline-mode}

Mit dem Offline-Modus der AEM Forms-App können Sie nahtlos arbeiten, selbst wenn die App offline geht. Sie können ein Formular öffnen, aktualisieren und senden, ohne dass eine Netzwerkverbindung erforderlich ist.

Sie beginnen mit der Arbeit an der AEM Forms-App, indem Sie Ihre App mit dem AEM Forms-Server synchronisieren. Alle Formulare, die Ihnen zugewiesen sind, werden in Ihre App heruntergeladen. Für AEM Forms on JEE werden Aufgaben auf die Registerkarte „Aufgaben“, mit Startpunkten verbundene Formulare sowie sonstige Formulare auf der Registerkarte „Formulare“ abgerufen. Bei AEM Forms on OSGi werden nur Formulare auf die Registerkarte „Formulare“ geladen.

Ausführliche Informationen zum Synchronisieren der App finden Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md).

## Offline-Verfügbarkeit von Formularen  {#making-forms-available-offline}

Wenn Sie die App mit dem AEM Forms-Server synchronisieren, werden die Formulare auf Ihr mobiles Gerät heruntergeladen. Die mit der Aufgabe verknüpften Anhänge werden jedoch standardmäßig nicht heruntergeladen. Dies bedeutet, dass Sie die Anhänge anzeigen können, wenn Sie online sind. Um jedoch sicherzustellen, dass Sie die Anhänge im Offline-Modus anzeigen können, ändern Sie die Standardeinstellungen der App.

Damit die verknüpften Anlagen mit jedem Formular heruntergeladen werden, müssen Sie die Option zum Abrufen der Anhänge auf „ON“ setzen. Ausführliche Informationen finden Sie unter [Aktualisieren von allgemeinen Einstellungen](/help/forms/using/update-general-settings.md).

Da das Herunterladen von Daten die Leistung des mobilen Geräts beeinträchtigen kann, ist die Option „Fetch attachments“ standardmäßig auf „OFF“ gesetzt. Wenn diese Einstellung auf „ON“ gesetzt wird, werden die Anlagen für alle Aufgaben, die danach vom Server heruntergeladen werden, auf das mobile Gerät geladen. Im Offline-Modus kann ein Benutzer dann an allen Aufgaben arbeiten, die auf das Gerät heruntergeladen werden, nachdem die Optionen **Fetch attachments** auf ON gesetzt wurden.

## Konfiguration des Offlinedienstes für die AEM Forms-App {#configuring-offline-service-for-aem-forms-app-br}

Der Dienst für die AEM Forms Offline-App identifiziert die in einem Formular verwendeten Ressourcen. Die AEM Forms-App nutzt diesen Dienst zum Abrufen von Informationen zu Formularabhängigkeiten. Informationen zu Formularabhängigkeiten sind erforderlich, um Offline-Funktionen zu aktivieren. Der Offlinedienst für die AEM Forms-App legt die Pfade oder URLs der in einem Formular verwendeten Ressourcen im Cache ab. Der Cache wird anhand der Änderungen im Formular und der für den Offlinedienst konfigurierten Gültigkeitsdauer aktualisiert. Durch das Zwischenspeichern der Pfa oder URLs der in einem Formular verwendeten Ressourcen wird die serverseitige Leistung verbessert.

Serverseitige Offlinekomponente der AEM Forms-App konfigurieren:

1. Navigieren Sie in der Autoreninstanz zu **Adobe Experience Manager** >**Tools** > **Forms** > **Forms App-Offlinedienst konfigurieren**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Unter „Allgemeine Einstellungen“ können Sie die folgenden Vorgänge ausführen:

   * **Cache löschen**: Löscht die serverseitig im Cache gespeicherten Formularabhängigkeiten.
   * **Konfiguration zurücksetzen**: Setzt die Offline-Konfiguration der AEM Forms-App zurück.
   * **Cache-Gültigkeitsdauer**: Gibt die Gültigkeitsdauer für den serverseitigen Offline-Cache an.
   * **Beobachtungspfade für Ressourcen**: Geben Sie die Pfade an, unter die der Offlinedienst auf Ressourcenänderungen überwachen soll. Wenn Änderungen unter den angegebenen Pfaden auftreten, wird der Offline-Cache aller abhängigen Formulare aktualisiert. Beispiel: `/etc/clientlibs/fd,/content/dam/images`.

1. Geben Sie auf der Registerkarte **Manueller Ressourcen-Cache** die Formularabhängigkeiten an, die vom Offlinedienst nicht erkannt werden. Sie können Ressourcen angeben, z. B. von JavaScript aus geladene Bilder. Die AEM Forms-App lädt dann diese Ressourcen ebenfalls für den Betrieb im Offlinemodus herunter.
