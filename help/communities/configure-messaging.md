---
title: Messaging-Funktion
seo-title: Messaging-Funktion
description: Konfigurieren von Messaging-Komponenten
seo-description: Konfigurieren von Messaging-Komponenten
uuid: 8b99ded1-aec2-40c9-82d5-e2e404f614ca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9d952604-f9ef-498f-937b-871817c80226
docset: aem65
translation-type: tm+mt
source-git-commit: e8d8bf89971d3d9d5ec150308dda247aa53c77bb

---


# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren auftreten, ermöglicht die Messaging-Funktion von AEM Communities Community es Community-Mitgliedern, privat miteinander zu interagieren.

This feature can be included when a [community site](/help/communities/overview.md#communitiessites) is created.

Die Messaging-Funktion bietet folgende Funktionen:

**A** - Senden Sie eine Nachricht an einen oder mehrere Community-Mitglieder **B** - senden Sie [Bulk-Direktnachrichten an Community-Mitglieder](/help/communities/messaging.md#group-messaging)C **- senden Sie eine Nachricht mit Anlagen** D **- Weiterleiten einer Nachricht** E - Antwort auf eine NachrichtFLöschen Sie eine Nachricht **E** E **E****** ENachricht - Wiederherstellen einer Nachricht

![messaging-section](assets/messaging-section.png) ![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Messaging](/help/communities/messaging.md) für Administratoren konfigurieren
* [Messaging Essentials](/help/communities/essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List` Komponenten (in der `Communities`Komponentengruppe) einer Seite im Bearbeitungsmodus des Autors hinzuzufügen.

## Messaging-Komponenten konfigurieren {#configure-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Liste der Nachricht konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Konfiguration der Liste der Nachrichten für **Posteingänge**, **Gesendete Elemente** und **Papierkorbseiten** der Nachrichtenfunktion zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im `Preview`Modus den Link &quot; **Nachrichten** &quot;, um die Hauptnachrichtenseite zu öffnen. Wählen Sie dann entweder &quot; **Posteingang**&quot;, &quot; **Gesendete Elemente** &quot;oder &quot; **Papierkorb** &quot;, um die Liste für diese Nachricht zu konfigurieren.

1. Wählen Sie im `Edit` Modus die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie auf das `link`Symbol klicken.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link` Symbols wiederhergestellt werden.

![configure-message-Liste](assets/configure-message-list.png)

#### Basic tab {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**

   (*Required*) Set this to the value of the property **`serviceSelector.name`** from the [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

* **Seite erstellen**

   (*Erforderlich*) Die Seite, die geöffnet wird, wenn ein Mitglied auf die **`Reply`** Schaltfläche klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Antwort/Ansicht als Ressource**

   Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Ansicht-URL auf eine Ressource, andernfalls werden die Daten als Abfragen-Parameter in der URL weitergeleitet.

* **Profil-Anzeigeformular**

   Das Profil-Formular, das zum Anzeigen des Profils des Absenders verwendet wird.

* **Papierkorb**

   Wenn diese Option aktiviert ist, zeigt diese Komponente nur Meldungen an, die als &quot;Gelöscht&quot;(Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

   (*Erforderlich*) Verweisen auf die für **inbox.path.name** und **sentitems.path.name** festgelegten Werte im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service). Bei der Konfiguration für einen `Inbox`Eintrag fügen Sie einen Eintrag mit dem Wert **inbox.path.name** hinzu. Bei der Konfiguration für einen `Outbox`Eintrag fügen Sie einen Eintrag mit dem Wert von **sentitems.path.name** hinzu. Fügen Sie beim Konfigurieren für `Trash`zwei Einträge mit beiden Werten hinzu.

#### Registerkarte anzeigen {#display-tab}

![display-tab-message-Liste](assets/display-tab-message-list.png)

* **Schaltfläche &quot;Gelesen&quot;**

   If checked, displays a `Read`button allowing a message to be marked as read.

* **Schaltfläche &quot;Ungelesen markieren&quot;**

   If checked, displays a `Mark Unread` button allowing a message to be marked as read.

* **Schaltfläche &quot;Löschen&quot;**

   If checked, displays a `Delete`button allowing a message to be marked as read. Will duplicate the delete functionality if **`Message Options`** is also checked.

* **Nachrichtenoptionen**

   Wenn diese Option aktiviert ist, werden Schaltflächen **`Reply`**, **`Reply All`** und **`Forward`** **`Delete`** Schaltflächen angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Will duplicate the delete functionality if **`Delete Button`** is also checked.

* **Nachrichten pro Seite**

   Die angegebene Zahl ist die maximale Anzahl von Meldungen, die pro Seite in einem Paginierungsschema angezeigt werden. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **Benutzer anzeigen**

   Wählen Sie entweder **`Sender`** oder **`Recipients`** , um festzulegen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im `Preview` Modus den Link &quot; **Nachrichten** &quot;, um die Haupt-Messaging-Seite zu öffnen. Klicken Sie dann auf &quot;Neue Nachricht&quot;, um die `Compose Message` Seite zu öffnen.

* Wählen Sie im `Edit` Modus die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie auf das `link` Symbol klicken.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link` Symbols wiederhergestellt werden.

![config-component-message](assets/config-compose-message.png)

#### Basic tab {#basic-tab-1}

![basic-tab-compse](assets/basic-tab-compose.png)

* **Umleitungs-URL**

   Geben Sie die URL der Seite ein, die nach dem Senden der Nachricht angezeigt wird. Beispiel: `../messaging.html`. 

* **URL abbrechen**

   Geben Sie die URL der Seite ein, die angezeigt wird, wenn der Absender die Nachricht abbricht. Beispiel: `../messaging.html`. 

* **Maximale Länge des Nachrichtenbetreffs**

   Die maximal zulässige Anzahl von Zeichen im Feld &quot;Betreff&quot;. Beispiel: 500. Der Standardwert ist nicht begrenzt.

* **Maximale Länge des Nachrichtentextes**

   Die maximal zulässige Anzahl von Zeichen im Feld &quot;Inhalt&quot;. Beispielsweise 10000. Der Standardwert ist nicht begrenzt.

* **Dienstauswahl**

   (*Required*) Set this to the value of the property **`serviceSelector.name`** from the [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

#### Registerkarte anzeigen {#display-tab-1}

![display-tab-component](assets/display-tab-compose.png)

* **Themenfeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das `Subject` Feld an und aktivieren Sie die Option Betreff zur Nachricht hinzufügen. Diese Option ist standardmäßig deaktiviert.

* **Subject Label**

   Geben Sie den Text ein, der neben dem `Subject` Feld angezeigt werden soll. Der Standardwert ist `Subject`.

* **Angehängtes Dateifeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das `Attachment` Feld an und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Dateietikett anhängen**

   Geben Sie den Text ein, der neben dem `Attachment` Feld angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das `Content` Feld an und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Diese Option ist standardmäßig deaktiviert.

* **Inhaltsbeschriftung**

   Geben Sie den Text ein, der neben dem `Content` Feld angezeigt werden soll. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor**

   Wenn diese Option aktiviert ist, wird die Verwendung eines benutzerdefinierten Textfelds mit einem eigenen Rich-Text-Editor angezeigt. Diese Option ist standardmäßig deaktiviert.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

