---
title: Messaging-Funktion
description: Erfahren Sie, wie Sie die Messaging-Funktion von AEM Communities so konfigurieren, dass Community-Mitglieder privat miteinander interagieren können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: d121dc05-7d15-44ba-8d2d-b59d6c6480c8
source-git-commit: b8887b4a6f757352e9dbfdf074c10e9ccd6dbd4f
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 5%

---

# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen in Foren und Kommentaren ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann bei einer [Community-Site](/help/communities/overview.md#communitiessites) erstellt wird.

Mit der Messaging-Funktion haben Sie folgende Möglichkeiten:

**A** - Senden einer Nachricht an ein oder mehrere Community-Mitglieder

**B** - Direktnachrichten senden in [Anzahl an Community-Mitgliedergruppen](/help/communities/messaging.md#group-messaging)

**C** - Senden einer Nachricht mit Anhängen

**D** - Weiterleiten einer Nachricht

**E** - Antwort auf eine Nachricht

**F** - Nachricht löschen

**G** - gelöschte Nachricht wiederherstellen

![messaging-section](assets/messaging-section.png)

![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Messaging konfigurieren](/help/communities/messaging.md) für Administratoren
* [Grundlagen zu Messaging](/help/communities/essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Das Hinzufügen von `Compose Message, Message, or Message List` Komponenten (gefunden in `Communities`Komponentengruppe) auf eine Seite im Bearbeitungsmodus &quot;Autor&quot;klicken.

## Messaging-Komponenten konfigurieren {#configure-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

So ändern Sie die Konfiguration der Nachrichtenliste für **Posteingang**, **Gesendete Elemente**, und **Papierkorb** Seiten der Messaging-Funktion öffnen Sie die Site in [Bearbeitungsmodus des Autors](/help/communities/sites-console.md#authoring-site-content).

1. In `Preview` -Modus, wählen Sie die **Nachrichten** -Link, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie anschließend **Posteingang**, **Gesendete Elemente** oder **Papierkorb** , um die Komponente für diese Nachrichtenliste zu konfigurieren.

1. In `Edit` -Modus die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie `link` Symbol.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl der `broken link` Symbol.

![configure-message-list](assets/configure-message-list.png)

#### Registerkarte „Allgemein“ {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**

  (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest. **`serviceSelector.name`** aus dem [AEM Communities Messaging-Dienst](/help/communities/messaging.md#messaging-operations-service).

* **Seite erstellen**

  (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die **`Reply`** Schaltfläche. Die Zielseite sollte die **Nachricht erstellen** Formular.

* **Antwort/Ansicht als Ressource**

  Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Anzeigen-URL auf eine Ressource. Andernfalls werden Daten als Abfrageparameter in der URL übergeben.

* **Formular zur Profilanzeige**

  Das Profilformular, das zum Anzeigen des Senderprofils verwendet werden soll.

* **Ordner löschen**

  Wenn diese Option aktiviert ist, zeigt diese Komponente nur Nachrichten an, die als gelöscht (Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

  (*Erforderlich*) Referenzieren der für **inbox.path.name** und **sentitems.path.name** im [AEM Communities Messaging-Dienst](/help/communities/messaging.md#messaging-operations-service). Beim Konfigurieren von `Inbox`, fügen Sie einen Eintrag mit dem Wert von **inbox.path.name**. Beim Konfigurieren von `Outbox`, fügen Sie einen Eintrag mit dem Wert von **sentitems.path.name**. Bei der Konfiguration für `Trash`, fügen Sie zwei Einträge mit beiden Werten hinzu.

#### Registerkarte &quot;Anzeige&quot; {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Schaltfläche &quot;Lesen&quot;**

  Wenn diese Option aktiviert ist, zeigt eine `Read`-Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann.

* **Schaltfläche &quot;Ungelesen markieren&quot;**

  Wenn diese Option aktiviert ist, zeigt eine `Mark Unread` -Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann.

* **Schaltfläche „Löschen“**

  Wenn diese Option aktiviert ist, zeigt eine `Delete` -Schaltfläche, über die eine Nachricht als gelesen gekennzeichnet werden kann. Dupliziert die Löschfunktion, wenn **`Message Options`** ebenfalls aktiviert ist.

* **Nachrichtenoptionen**

  Wenn diese Option aktiviert ist, wird angezeigt **`Reply`**, **`Reply All`**, **`Forward`**, und **`Delete`** Schaltflächen zum erneuten Senden oder Löschen einer Nachricht. Dupliziert die Löschfunktion, wenn **`Delete Button`** ebenfalls aktiviert ist.

* **Nachrichten pro Seite**

  Die angegebene Anzahl entspricht der maximalen Anzahl an Nachrichten, die pro Seite in einem Paginierungsschema angezeigt werden. Wenn keine Zahl angegeben (leer gelassen) wird, werden alle Nachrichten angezeigt und es wird keine Paginierung durchgeführt.

* **Zeitstempelmuster**

  Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Der Standardwert ist für en, de, fr, es, ja, zh_CN, ko_KR.

* **Benutzer anzeigen**

  Wählen Sie entweder **`Sender`** oder **`Recipients`** damit Sie bestimmen können, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht erstellen konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite mit der Nachricht zum Erstellen zu ändern, öffnen Sie die Site in [Bearbeitungsmodus des Autors](/help/communities/sites-console.md#authoring-site-content).

* In `Preview` -Modus, wählen Sie die **Nachrichten** -Link, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann die Schaltfläche Neue Nachricht aus, damit Sie die `Compose Message` Seite.

* In `Edit` -Modus wählen Sie die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie `link` Symbol.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl der `broken link` Symbol.

![config-compse-message](assets/config-compose-message.png)

#### Registerkarte „Allgemein“ {#basic-tab-1}

![basic-tab-compse](assets/basic-tab-compose.png)

* **Umleitungs-URL**

  Geben Sie die URL der Seite ein, die nach dem Versand der Nachricht angezeigt wird. Zum Beispiel: `../messaging.html`.

* **URL abbrechen**

  Geben Sie die URL der Seite ein, die angezeigt wird, wenn der Absender die Nachricht abbricht. Zum Beispiel: `../messaging.html`.

* **Maximale Länge des Nachrichtenbetreffs**

  Die maximal zulässige Anzahl von Zeichen im Feld Betreff. Beispiel: 500. Der Standardwert ist keine Begrenzung.

* **Maximale Länge des Nachrichtentextes**

  Die maximal zulässige Anzahl von Zeichen im Feld Inhalt . Beispiel: 10000. Der Standardwert ist keine Begrenzung.

* **Dienstauswahl**

  (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest. **`serviceSelector.name`** aus dem [AEM Communities Messaging-Dienst](/help/communities/messaging.md#messaging-operations-service).

#### Registerkarte &quot;Anzeige&quot; {#display-tab-1}

![display-tab-compse](assets/display-tab-compose.png)

* **Feld anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie die `Subject` und aktivieren Sie die Option Betreff zur Nachricht hinzufügen. Die Option Standard ist nicht aktiviert.

* **Betreff-Bezeichnung**

  Geben Sie den Text ein, der neben dem `Subject` -Feld. Der Standardwert ist `Subject`.

* **Angehängtes Dateifeld anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie die `Attachment` und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Die Option Standard ist nicht aktiviert.

* **Dateietikett anhängen**

  Geben Sie den Text ein, der neben dem `Attachment` -Feld. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie die `Content` und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Die Option Standard ist nicht aktiviert.

* **Inhaltsbezeichnung**

  Geben Sie den Text ein, der neben dem `Content` -Feld. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor**

  Ist diese Option aktiviert, wird die Verwendung eines benutzerdefinierten Textfelds &quot;Inhalt&quot;mit einem eigenen Rich-Text-Editor angezeigt. Die Option Standard ist nicht aktiviert.

* **Zeitstempelmuster**

  Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Der Standardwert ist für en, de, fr, es, ja, zh_CN, ko_KR.
