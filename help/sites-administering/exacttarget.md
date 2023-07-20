---
title: Integrieren mit ExactTarget
description: Erfahren Sie, wie Sie Adobe Experience Manager mit ExactTarget integrieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 4183fe78-5055-4b77-8a54-55666e86a04e
source-git-commit: 3885cc51f7e821cdb352737336a29f9c4f0c2f41
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 26%

---

# Integrieren mit ExactTarget{#integrating-with-exacttarget}

Durch die Integration von Adobe Experience Manager (AEM) in Exact Target können Sie in AEM erstellte E-Mails über Exact Target verwalten und versenden. Außerdem können Sie die Lead-Management-Funktionen von ExactTarget über AEM Formulare auf AEM Seiten verwenden.

Die Integration bietet die folgenden Funktionen:

* Die Möglichkeit, E-Mails in AEM zu erstellen und in ExactTarget zur Verteilung zu veröffentlichen.
* Die Möglichkeit, die Aktion eines AEM Formulars festzulegen, um einen ExactTarget-Abonnenten zu erstellen.

Nachdem ExactTarget konfiguriert wurde, können Sie Newsletter oder E-Mails in ExactTarget veröffentlichen. Siehe [Veröffentlichen von Newslettern in einem E-Mail-Dienst](/help/sites-authoring/personalization.md).

## Erstellen einer ExactTarget-Konfiguration {#creating-an-exacttarget-configuration}

ExactTarget-Konfigurationen können über Cloud Services oder Tools hinzugefügt werden. Beide Methoden werden in diesem Abschnitt beschrieben.

### Konfigurieren von ExactTarget über Cloud Services {#configuring-exacttarget-via-cloudservices}

So erstellen Sie eine ExactTarget-Konfiguration in Cloud Services:

1. Klicken Sie auf der Begrüßungsseite auf **Cloud Services**. (Oder gehen Sie direkt zu `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klicken Sie auf **ExactTarget** und dann auf **Konfigurieren**. Das ExactTarget-Konfigurationsfenster wird geöffnet.

   ![chlimage_1-19](assets/chlimage_1-19.png)

1. Geben Sie einen Titel und optional einen Namen ein und klicken Sie auf **Erstellen**. Das Konfigurationsfenster **ExactTarget-Einstellungen** wird geöffnet.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Geben Sie den Benutzernamen und das Kennwort ein und wählen Sie einen API-Endpunkt aus (z. B. **https://webservice.exacttarget.com/Service.asmx**).
1. Klicken **Verbindung zu ExactTarget herstellen.** Wenn Sie eine erfolgreiche Verbindung hergestellt haben, wird ein Dialogfeld angezeigt. Kästchen Klicken **OK** , um das Fenster zu verlassen.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Wählen Sie ein Konto aus, falls verfügbar. Das Konto richtet sich an Kunden von Enterprise 2.0. Klicken Sie auf **OK**.

   ExactTarget wurde konfiguriert. Sie können die Konfiguration bearbeiten, indem Sie auf **Bearbeiten** klicken. Sie können auf ExactTarget zugreifen, indem Sie auf **Wechseln zu ExactTarget** klicken.

1. AEM bietet jetzt eine Datenerweiterungsfunktion. Sie können Spalten zur Datenerweiterung in ExactTarget importieren. Sie können sie konfigurieren, indem Sie auf das &quot;+&quot;-Zeichen klicken, das neben der erfolgreich erstellten ExactTarget-Konfiguration angezeigt wird. Jede der vorhandenen Datenerweiterungen kann aus der Dropdown-Liste ausgewählt werden. Weitere Informationen zum Konfigurieren von Datenerweiterungen finden Sie unter [ExactTarget-Dokumentation](https://help.salesforce.com/s/articleView?id=sf.mc_es_data_extension_data_relationships_classic.htm&amp;type=5).

   Importierte Datenerweiterungsspalten können später über die **Text und Personalisierung** -Komponente.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

### Konfigurieren von ExactTarget mithilfe von Tools {#configuring-exacttarget-via-tools}

So erstellen Sie eine ExactTarget-Konfiguration in Tools:

1. Klicken Sie auf der Begrüßungsseite auf **Instrumente**. Oder navigieren Sie über `https://<hostname>:<port>/misadmin#/etc` direkt dorthin.
1. Wählen Sie **Tools** > **Cloud Service-Konfigurationen** > **ExactTarget** aus.
1. Klicken Sie auf **Neu**, um das Fenster **Seite erstellen** zu öffnen.

   ![chlimage_1-34](assets/chlimage_1-3.jpeg)

1. Geben Sie die **Titel** und optional die **Name** und klicken Sie auf **Erstellen**.
1. Geben Sie die Konfigurationsinformationen ein, wie in Schritt 4 des vorherigen Verfahrens beschrieben. Führen Sie dieses Verfahren aus, um die Konfiguration von ExactTarget abzuschließen.

### Hinzufügen mehrerer Konfigurationen {#adding-multiple-configurations}

So fügen Sie mehrere Konfigurationen hinzu:

1. Klicken Sie auf der Begrüßungsseite auf **Cloud Services** und klicken Sie auf **ExactTarget**. Klicken **Konfigurationen anzeigen** wird angezeigt, wenn eine oder mehrere ExactTarget-Konfigurationen verfügbar sind. Alle verfügbaren Konfigurationen werden aufgelistet.
1. Klicken Sie auf das Pluszeichen **(+)** neben „Verfügbare Konfigurationen“. Dadurch wird die **Erstellen von Konfigurationen** Fenster. Gehen Sie wie zuvor beschrieben vor, um eine Konfiguration zu erstellen.
