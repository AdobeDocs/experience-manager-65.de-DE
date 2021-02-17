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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 13%

---


# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren auftreten, ermöglicht die Messaging-Funktion von AEM Communities Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann einbezogen werden, wenn eine [Community-Site](/help/communities/overview.md#communitiessites) erstellt wird.

Die Messaging-Funktion bietet folgende Funktionen:

**A** : Senden Sie eine Nachricht an einen oder mehrere Community-Mitglieder

**B** - Direktnachrichten  [stapelweise an Community-Mitgliedsgruppen senden](/help/communities/messaging.md#group-messaging)

**C** - Nachricht mit Anlagen senden

**D**  - Weiterleiten einer Nachricht

**E** - Antwort auf eine Nachricht

**F**  - Löschen einer Nachricht

**G** - gelöschte Meldung wiederherstellen

![messaging-section](assets/messaging-section.png)

![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Konfigurieren der ](/help/communities/messaging.md) Nachrichten für Administratoren
* [Messaging ](/help/communities/essentials-messaging.md) Essentials für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List`-Komponenten (in `Communities`Komponentengruppe gefunden) zu einer Seite im Autorenbearbeitungsmodus hinzuzufügen.

## Messaging-Komponenten {#configure-messaging-components} konfigurieren

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Message-Liste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Liste der Nachrichten für **Inbox**-, **Gesendete Elemente**- und **Papierkorb**-Seiten der Nachrichtenfunktion zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im Modus `Preview` den Link **Nachrichten**, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann entweder **Inbox**, **Gesendete Elemente** oder **Papierkorb** aus, um die Liste für diese Nachricht zu konfigurieren.

1. Wählen Sie im Modus `Edit` die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie auf das Symbol `link` klicken.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![configure-message-Liste](assets/configure-message-list.png)

#### Einfache Registerkarte {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**

   (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** vom [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service) fest.

* **Seite erstellen**

   (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die Schaltfläche **`Reply`** klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Antwort/Ansicht als Ressource**

   Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Ansicht-URL auf eine Ressource, andernfalls werden die Daten als Abfragen-Parameter in der URL weitergeleitet.

* **Profil-Anzeigeformular**

   Das Profil-Formular, das zum Anzeigen des Profils des Absenders verwendet wird.

* **Papierkorb**

   Wenn diese Option aktiviert ist, zeigt diese Komponente nur Meldungen an, die als &quot;Gelöscht&quot;(Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

   (*Erforderlich*) Verweis auf die Werte, die für **inbox.path.name** und **sentitems.path.name** im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service) festgelegt wurden. Bei der Konfiguration für ein `Inbox` fügen Sie einen Eintrag mit dem Wert **inbox.path.name** hinzu. Bei der Konfiguration für ein `Outbox` fügen Sie einen Eintrag mit dem Wert **sentitems.path.name** hinzu. Fügen Sie bei der Konfiguration für `Trash` zwei Einträge mit beiden Werten hinzu.

#### Display tab {#display-tab}

![display-tab-message-Liste](assets/display-tab-message-list.png)

* **Schaltfläche &quot;Gelesen&quot;**

   Wenn diese Option aktiviert ist, wird die Schaltfläche `Read`angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche &quot;Ungelesen markieren&quot;**

   Wenn diese Option aktiviert ist, wird die Schaltfläche `Mark Unread` angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche „Löschen“**

   Wenn diese Option aktiviert ist, wird die Schaltfläche `Delete` angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Wird die Funktion zum Löschen Duplikat, wenn **`Message Options`** ebenfalls aktiviert ist.

* **Nachrichtenoptionen**

   Wenn diese Option aktiviert ist, werden die Schaltflächen **`Reply`**, **`Reply All`**, **`Forward`** und **`Delete`** angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Wird die Funktion zum Löschen Duplikat, wenn **`Delete Button`** ebenfalls aktiviert ist.

* **Nachrichten pro Seite**

   Die angegebene Zahl ist die maximale Anzahl von Meldungen, die pro Seite in einem Paginierungsschema angezeigt werden. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **Benutzer anzeigen**

   Wählen Sie entweder **`Sender`** oder **`Recipients`**, um festzulegen, ob der Sender oder die Empfänger angezeigt werden sollen.

### Konfigurieren Sie die Nachricht &#39;Erstellen&#39; {#configure-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im Modus `Preview` den Link **Nachrichten**, um die Hauptseite der Nachrichten zu öffnen. Klicken Sie dann auf &quot;Neue Nachricht&quot;, um die Seite `Compose Message` zu öffnen.

* Wählen Sie im Modus `Edit` die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Nach dem Abbrechen der Vererbung können Sie das Symbol &quot;Konfigurieren&quot;auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![config-component-message](assets/config-compose-message.png)

#### Einfache Registerkarte {#basic-tab-1}

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

   (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** vom [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service) fest.

#### Display tab {#display-tab-1}

![display-tab-component](assets/display-tab-compose.png)

* **Themenfeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Subject` an und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Subject Label**

   Geben Sie den Text ein, der neben dem Feld `Subject` angezeigt werden soll. Der Standardwert ist `Subject`.

* **Angehängtes Dateifeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Attachment` an und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Dateietikett anhängen**

   Geben Sie den Text ein, der neben dem Feld `Attachment` angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Content` an und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Diese Option ist standardmäßig deaktiviert.

* **Inhaltsbeschriftung**

   Geben Sie den Text ein, der neben dem Feld `Content` angezeigt werden soll. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor**

   Wenn diese Option aktiviert ist, wird die Verwendung eines benutzerdefinierten Textfelds mit einem eigenen Rich-Text-Editor angezeigt. Diese Option ist standardmäßig deaktiviert.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

