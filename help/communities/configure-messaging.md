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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Messaging-Funktion{#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren auftreten, ermöglicht die Messaging-Funktion von**** AEM Communities Community Mitgliedern der Community, privat miteinander zu interagieren.

This feature can be included when a [community site](/help/communities/overview.md#communitiessites) is created.

Die Messaging-Funktion bietet folgende Funktionen:

**A** - eine Nachricht an ein oder mehrere Mitglieder **B** senden - Direktnachrichten [stapelweise an Community-Mitgliedsgruppen](/help/communities/messaging.md#group-messaging)**C** senden - eine Nachricht mit Anlagen **D** senden - eine Nachricht senden**E - **Antwort auf eine Nachricht **** F- eine Nachricht löschen**G **- eine gelöschte Nachricht wiederherstellen

![messaging-section](assets/messaging-section.png) ![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Messaging](/help/communities/messaging.md) für Administratoren konfigurieren
* [Messaging Essentials](/help/communities/essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List` Komponenten (in der `Communities`Komponentengruppe) einer Seite im Bearbeitungsmodus des Autors hinzuzufügen.

## Messaging-Komponenten konfigurieren {#configure-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Konfiguration der Liste der Nachrichten für **Posteingang**, **Gesendete Elemente** und **Papierkorb **Seiten der Nachrichtenfunktion zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im `Preview`Modus den Link **Nachrichten **aus, um die Haupt-Nachrichten-Seite zu öffnen. Wählen Sie dann **Posteingang**, **Gesendete Elemente **oder **Papierkorb **aus, um die Komponente für diese Nachrichtenliste zu konfigurieren.

1. Wählen Sie im `Edit` Modus die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie auf das `link`Symbol klicken.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link` Symbols wiederhergestellt werden.

![configure-message-list](assets/configure-message-list.png)

#### Basic tab {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**(*Erforderlich*) Legen Sie diesen Wert auf den Wert der Eigenschaft**`serviceSelector.name`** vom [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service)fest.

* **Seite** erstellen (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die Schaltfläche **`Reply`**klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Als Ressource antworten/anzeigen** Ist diese Option aktiviert, verweisen die Antwort- und Ansichts-URL auf eine Ressource. Ist sie nicht aktiviert, werden Daten als Abfrageparameter in der URL übermittelt. 

* **Anzeigeform für Profil** Das Profilformular zur Anzeige des Absenderprofils.

* **Papierkorb-Ordner** Ist die Option aktiviert, zeigt diese Nachrichtenlisten-Komponente lediglich Nachrichten an, die als gelöscht markiert wurden (Papierkorb).

* **Ordnerpfade**(*Erforderlich*) Verweis auf die für **inbox.path.name** und **sentitems.path.name **im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service)festgelegten Werte. Bei der Konfiguration für einen `Inbox`Eintrag fügen Sie einen Eintrag mit dem Wert **inbox.path.name** hinzu. Bei der Konfiguration für einen `Outbox`Eintrag fügen Sie einen Eintrag mit dem Wert von **sentitems.path.name** hinzu. Fügen Sie beim Konfigurieren für `Trash`zwei Einträge mit beiden Werten hinzu.

#### Registerkarte anzeigen {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Markieren Sie die Leseschaltfläche** Wenn diese aktiviert ist, wird eine `Read`Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **&quot;Ungelesen markieren&quot;** Wenn diese Option aktiviert ist, wird eine `Mark Unread` Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche**&quot;Löschen&quot;Wenn diese Option aktiviert ist, wird eine `Delete`Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Will duplicate the delete functionality if **`Message Options`** is also checked.

* **Nachrichtenoptionen** Wenn aktiviert, werden Schaltflächen **`Reply`**, **`Reply All`**, **`Forward`**und **`Delete`**angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Will duplicate the delete functionality if **`Delete Button`** is also checked.

* **Nachrichten pro Seite** Die angegebene Zahl entspricht der maximalen Anzahl von Nachrichten, die bei einer Aufteilung in Seiten pro Seite angezeigt wird. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **Zeitstempelmuster** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **Benutzer** anzeigen Wählen Sie entweder **`Sender`** oder **`Recipients`**aus, um zu bestimmen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site im [Autorenbearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im `Preview`Modus den Link **Nachrichten **aus, um die Haupt-Nachrichten-Seite zu öffnen. Klicken Sie dann auf &quot;Neue Nachricht&quot;, um die `Compose Message` Seite zu öffnen.

* Wählen Sie im `Edit` Modus die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das `link`Symbol auswählen.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des `broken link`Symbols wiederhergestellt werden.

![config-component-message](assets/config-compose-message.png)

#### Basic tab {#basic-tab-1}

![basic-tab-compse](assets/basic-tab-compose.png)

* **URL-Weiterleitung** Geben Sie die URL der Seite ein, die nach dem Versenden der Nachricht angezeigt werden soll. Beispiel, `../messaging.html`.

* **URL abbrechen** Geben Sie die URL der Seite ein, die angezeigt werden soll, wenn der Sender das Verfassen einer Nachricht abbricht. Beispiel, `../messaging.html`.

* **Maximale Länge des Nachrichtenbetreffs** Die maximal zulässige Anzahl der Zeichen im Feld „Betreff“. Beispiel: 500. Der Standardwert ist nicht begrenzt.

* **Maximale Länge des Nachrichtentextes** Die maximal zulässige Anzahl der Zeichen im Feld „Inhalt“. Beispielsweise 10000. Der Standardwert ist nicht begrenzt.

* **Dienstauswahl**(*Erforderlich*) Legen Sie diesen Wert auf den Wert der Eigenschaft**`serviceSelector.name`** vom [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service)fest.

#### Registerkarte anzeigen {#display-tab-1}

![display-tab-component](assets/display-tab-compose.png)

* **&quot;Betrefffeld** anzeigen&quot; `Subject` Wenn aktiviert, zeigen Sie das Feld an und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Betreffbeschriftung** Geben Sie den Text ein, der neben dem `Subject` Feld angezeigt werden soll. Der Standardwert ist `Subject`.

* **Dateifeld** anhängen anzeigen Wenn aktiviert, zeigen Sie das Feld an und aktivieren Siedas Hinzufügen von Dateianlagen zur Nachricht. `Attachment` Diese Option ist standardmäßig deaktiviert.

* **Dateibeschriftung** anhängen Geben Sie den Text ein, der neben dem `Attachment` Feld angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld** anzeigen Wenn aktiviert, zeigen Sie das Feld an und aktivieren Sie das Hinzufügen eines Nachrichtentextes `Content` . Diese Option ist standardmäßig deaktiviert.

* **Inhaltsbeschriftung** Geben Sie den Text ein, der neben dem `Content` Feld angezeigt werden soll. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor** Ist diese Option aktiviert, kann ein benutzerdefiniertes „Inhalt“-Textfeld verwendet werden, das über einen eigenen Rich-Text-Editor verfügt. Diese Option ist standardmäßig deaktiviert.

* **Zeitstempelmuster** Stellen Sie für eine oder mehrere Sprachen Zeitstempelmuster bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

