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
exl-id: d121dc05-7d15-44ba-8d2d-b59d6c6480c8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 13%

---

# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen in Foren und Kommentaren ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann eingeschlossen werden, wenn eine [Community-Site](/help/communities/overview.md#communitiessites) erstellt wird.

Die Messaging-Funktion bietet folgende Möglichkeiten:

**A**  - Senden einer Nachricht an ein oder mehrere Community-Mitglieder

**B**  - Senden von Direktnachrichten  [stapelweise an Community-Mitgliedergruppen](/help/communities/messaging.md#group-messaging)

**C**  - Senden einer Nachricht mit Anhängen

**D**  - Weiterleiten einer Nachricht

**E**  - Antwort auf eine Nachricht

**F**  - Nachricht löschen

**G**  - Gelöschte Nachricht wiederherstellen

![messaging-section](assets/messaging-section.png)

![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Konfigurieren der ](/help/communities/messaging.md) Nachrichten für Administratoren
* [Messaging-](/help/communities/essentials-messaging.md) Grundlagen für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List`-Komponenten (in `Communities`Komponentengruppe) zu einer Seite im Bearbeitungsmodus für Autoren hinzuzufügen.

## Messaging-Komponenten {#configure-messaging-components} konfigurieren

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Konfiguration der Nachrichtenliste für die Seiten **Inbox**, **Gesendete Elemente** und **Papierkorb** der Nachrichtenfunktion zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im Modus `Preview` den Link **Nachrichten** aus, um die Hauptnachrichten-Seite zu öffnen. Wählen Sie dann entweder **Posteingang**, **Gesendete Elemente** oder **Papierkorb** aus, um die Komponente für diese Nachrichtenliste zu konfigurieren.

1. Wählen Sie im Modus `Edit` die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie auf das Symbol `link` klicken.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![configure-message-list](assets/configure-message-list.png)

#### Einfache Registerkarte {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**

   (*Erforderlich*) Setzen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** aus dem [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

* **Seite erstellen**

   (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die Schaltfläche **`Reply`** klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Antwort/Ansicht als Ressource**

   Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Anzeigen-URL auf eine Ressource. Andernfalls werden Daten als Abfrageparameter in der URL übergeben.

* **Formular zur Profilanzeige**

   Das Profilformular, das zum Anzeigen des Senderprofils verwendet werden soll.

* **Ordner löschen**

   Wenn diese Option aktiviert ist, zeigt diese Komponente nur Nachrichten an, die als gelöscht (Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

   (*Erforderlich*) Referenzierung der Werte für **inbox.path.name** und **sentitems.path.name** im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service). Fügen Sie bei der Konfiguration für `Inbox` einen Eintrag mit dem Wert **inbox.path.name** hinzu. Fügen Sie bei der Konfiguration für `Outbox` einen Eintrag mit dem Wert **sentitems.path.name** hinzu. Fügen Sie bei der Konfiguration für `Trash` zwei Einträge mit beiden Werten hinzu.

#### Registerkarte Anzeige {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Schaltfläche &quot;Lesen&quot;**

   Wenn diese Option aktiviert ist, wird eine Schaltfläche `Read`angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche &quot;Ungelesen markieren&quot;**

   Wenn diese Option aktiviert ist, wird eine Schaltfläche `Mark Unread` angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche „Löschen“**

   Wenn diese Option aktiviert ist, wird eine Schaltfläche `Delete` angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Dupliziert die Löschfunktion, wenn auch **`Message Options`** aktiviert ist.

* **Nachrichtenoptionen**

   Wenn diese Option aktiviert ist, werden die Schaltflächen **`Reply`**, **`Reply All`**, **`Forward`** und **`Delete`** angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Dupliziert die Löschfunktion, wenn auch **`Delete Button`** aktiviert ist.

* **Nachrichten pro Seite**

   Die angegebene Anzahl entspricht der maximalen Anzahl an Nachrichten, die pro Seite in einem Paginierungsschema angezeigt werden. Ist keine Anzahl festgelegt (leeres Feld), werden alle Nachrichten auf einer Seite angezeigt.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.

* **Benutzer anzeigen**

   Wählen Sie entweder **`Sender`** oder **`Recipients`** aus, um zu bestimmen, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht erstellen konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite mit der Komprimierungsnachricht zu ändern, öffnen Sie die Website im Bearbeitungsmodus [Autor](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im Modus `Preview` den Link **Nachrichten** aus, um die Hauptnachrichten-Seite zu öffnen. Wählen Sie dann die Schaltfläche Neue Nachricht aus, um die Seite `Compose Message` zu öffnen.

* Wählen Sie im Modus `Edit` die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![config-compse-message](assets/config-compose-message.png)

#### Einfache Registerkarte {#basic-tab-1}

![basic-tab-compse](assets/basic-tab-compose.png)

* **Umleitungs-URL**

   Geben Sie die URL der Seite ein, die nach dem Versand der Nachricht angezeigt wird. Beispiel: `../messaging.html`.

* **URL abbrechen**

   Geben Sie die URL der Seite ein, die angezeigt wird, wenn der Absender die Nachricht abbricht. Beispiel: `../messaging.html`.

* **Maximale Länge des Nachrichtenbetreffs**

   Die maximal zulässige Anzahl von Zeichen im Feld &quot;Betreff&quot;. Beispiel: 500. Der Standardwert ist keine Begrenzung.

* **Maximale Länge des Nachrichtentextes**

   Die maximal zulässige Anzahl von Zeichen im Feld Inhalt . Beispielsweise 10000. Der Standardwert ist keine Begrenzung.

* **Dienstauswahl**

   (*Erforderlich*) Setzen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** aus dem [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

#### Registerkarte Anzeige {#display-tab-1}

![display-tab-compse](assets/display-tab-compose.png)

* **Feld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Subject` an und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Betreffbezeichnung**

   Geben Sie den Text ein, der neben dem Feld `Subject` angezeigt werden soll. Der Standardwert ist `Subject`.

* **Angehängtes Dateifeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Attachment` an und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Diese Option ist standardmäßig deaktiviert.

* **Dateietikett anhängen**

   Geben Sie den Text ein, der neben dem Feld `Attachment` angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie das Feld `Content` an und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Diese Option ist standardmäßig deaktiviert.

* **Inhaltsbezeichnung**

   Geben Sie den Text ein, der neben dem Feld `Content` angezeigt werden soll. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor**

   Ist diese Option aktiviert, wird die Verwendung eines benutzerdefinierten Textfelds &quot;Inhalt&quot;mit einem eigenen Rich-Text-Editor angezeigt. Diese Option ist standardmäßig deaktiviert.

* **Zeitstempelmuster**

   Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Standardmäßig sind diese für die Sprachen en, de, fr, it, ja, zh_CN und ko_KR verfügbar.
