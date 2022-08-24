---
title: Integration mit ExactTarget
seo-title: Integrating with ExactTarget
description: Erfahren Sie, wie Sie AEM mit ExactTarget integrieren.
seo-description: Learn how to integrate AEM with ExactTarget.
uuid: a53bbdaa-98f7-4035-b842-aa7ea63712ca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 5b2f624d-e5b8-4484-a773-7784ebce58bd
docset: aem65
exl-id: 4183fe78-5055-4b77-8a54-55666e86a04e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 78%

---

# Integration mit ExactTarget{#integrating-with-exacttarget}

Durch die Integration von AEM in Exact Target können Sie in AEM erstellten E-Mails verwalten und senden. Außerdem können Sie die Lead-Management-Funktionen von ExactTarget über AEM Formulare auf AEM Seiten verwenden.

Mit der Integration verfügen Sie über die folgenden Funktionen:

* die Möglichkeit, E-Mails in AEM zu erstellen und sie für ExactTarget für den Versand zu veröffentlichen
* die Möglichkeit, die Aktion für ein AEM-Formular festzulegen, einen ExactTarget-Abonnenten zu erstellen

Nach der Konfiguration von ExactTarget können Sie Newsletter oder E-Mails für ExactTarget veröffentlichen. Siehe [Veröffentlichen von Newslettern für einen E-Mail-Dienst](/help/sites-authoring/personalization.md).

## Erstellen einer ExactTarget-Konfiguration {#creating-an-exacttarget-configuration}

Sie können ExactTarget-Konfigurationen über Cloud-Services oder über die Tools hinzufügen. Beide Möglichkeiten werden in diesem Abschnitt beschrieben.

### Konfigurieren von ExactTarget über Cloud-Services {#configuring-exacttarget-via-cloudservices}

So erstellen Sie eine ExactTarget-Konfiguration über Cloud-Services:

1. Klicken Sie auf der Willkommensseite auf **Cloud-Services**. (Oder direkt auf unter `https://<hostname>:<port>/etc/cloudservices.html`.
1. Klicken **ExactTarget** und dann **Konfigurieren**. Das ExactTarget-Konfigurationsfenster wird geöffnet.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Geben Sie einen Titel und optional einen Namen ein und klicken Sie auf **Erstellen**. Das Konfigurationsfenster **ExactTarget-Einstellungen** wird geöffnet.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Geben Sie den Benutzernamen und das Kennwort ein und wählen Sie einen API-Endpunkt aus (z. B. **https://webservice.exacttarget.com/Service.asmx**).
1. Klicken Sie auf **Mit ExactTarget verbinden.** Wenn die Verbindung erfolgreich hergestellt wurde, wird ein Dialogfeld mit dem entsprechenden Hinweis angezeigt. Klicken Sie auf **OK**, um das Fenster zu beenden.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Wählen Sie ein Konto aus, falls verfügbar. Das Konto ist für Enterprise 2.0-Kunden. Klicken Sie auf **OK**.

   ExactTarget wurde konfiguriert. Sie können die Konfiguration bearbeiten, indem Sie auf **Bearbeiten** klicken. Sie können ExactTarget aufrufen, indem Sie auf **Zu ExactTarget wechseln**.

1. AEM bietet jetzt eine Datenerweiterungsfunktion. Sie können ExactTarget-Datenerweiterungsspalten importieren. Klicken Sie zur Konfiguration auf das Pluszeichen (+), das neben der erfolgreich erstellten ExactTarget-Konfiguration angezeigt wird. Aus der Dropdown-Liste können Sie jede vorhandene Datenerweiterung auswählen. Weitere Informationen zur Konfiguration von Datenerweiterungen finden Sie in der [ExactTarget-Dokumentation](https://help.exacttarget.com/en/documentation/exacttarget/subscribers/data_extensions_and_data_relationships).

   Importierte Datenerweiterungsspalten können Sie später über die Komponente **Text und Personalisierung** nutzen.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

### Konfigurieren von ExactTarget über die Tools {#configuring-exacttarget-via-tools}

So erstellen Sie eine ExactTarget-Konfiguration über die Tools:

1. Klicken Sie auf der Willkommensseite auf **Tools**. Oder navigieren Sie direkt dorthin, indem Sie `https://<hostname>:<port>/misadmin#/etc`.
1. Wählen Sie **Tools** > **Cloud Service-Konfigurationen** > **ExactTarget** aus.
1. Klicken **Neu** , um das Fenster &quot;Seite erstellen&quot;zu öffnen.

   ![chlimage_1-34](assets/chlimage_1-3.jpeg)

1. Geben Sie den **Titel** und optional den **Namen** ein und klicken Sie auf **Erstellen**.
1. Geben Sie die Konfigurationsinformationen ein, wie in Schritt 4 des vorherigen Verfahrens beschrieben. Befolgen Sie diesen Vorgang, um die Konfiguration von ExactTarget abzuschließen.

### Hinzufügen mehrerer Konfigurationen {#adding-multiple-configurations}

So fügen Sie mehrere Konfigurationen hinzu:

1. Klicken Sie auf der Willkommensseite auf **Cloud-Services** und dann auf **ExactTarget**. Klicken Sie auf **Konfigurationen anzeigen** -Schaltfläche, die angezeigt wird, wenn eine oder mehrere ExactTarget-Konfigurationen verfügbar sind. Alle verfügbaren Konfigurationen werden aufgeführt.
1. Klicken Sie auf das Pluszeichen (**+**) neben „Verfügbare Konfigurationen“. Das Fenster **Konfiguration erstellen** wird geöffnet. Führen Sie die Schritte des vorherigen Konfigurationsverfahrens aus, um eine neue Konfiguration zu erstellen.
