---
title: Messaging-Funktion
description: Erfahren Sie, wie Sie die Messaging-Funktion von AEM Communities konfigurieren, damit Community-Mitglieder vertraulicher miteinander interagieren können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: d121dc05-7d15-44ba-8d2d-b59d6c6480c8
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 1%

---

# Messaging-Funktion {#messaging-feature}

Zusätzlich zu den öffentlich sichtbaren Interaktionen, die in Foren und Kommentaren stattfinden, ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privater miteinander zu interagieren.

Diese Funktion kann beim Erstellen einer [Community-Site](/help/communities/overview.md#communitiessites) einbezogen werden.

Mit der Messaging-Funktion können Sie Folgendes tun:

**A** - Senden einer Nachricht an ein oder mehrere Community-Mitglieder

**B** - Senden Sie Direktnachrichten massenweise [an Community-Mitgliedergruppen](/help/communities/messaging.md#group-messaging)

**C** - Senden einer Nachricht mit Anhängen

**D** - Nachricht weiterleiten

**E** - Antwort auf eine Nachricht

**F** - Nachricht löschen

**G** - Gelöschte Nachricht wiederherstellen

![messaging-section](assets/messaging-section.png)

![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Konfigurieren von Messaging](/help/communities/messaging.md) für Administratoren
* [Messaging Essentials](/help/communities/essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Es wird nicht unterstützt, `Compose Message, Message, or Message List` Komponenten (in `Communities`Komponentengruppe) zu einer Seite im Authoring-Bearbeitungsmodus hinzuzufügen.

## Konfigurieren von Messaging-Komponenten {#configure-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, wird sie ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn eine Änderung der Standardkonfiguration erforderlich ist.

### Nachrichtenliste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Konfiguration der Nachrichtenliste für die Seiten **Posteingang**, **Gesendete Elemente** und **Papierkorb** der Nachrichtenfunktion zu ändern, öffnen Sie die Site im [Bearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im `Preview`-Modus den **Nachrichten**, um die Hauptseite für Nachrichten zu öffnen. Wählen Sie dann entweder **Posteingang**, **Gesendete Elemente** oder **Papierkorb**, um die Komponente für diese Nachrichtenliste zu konfigurieren.

1. Wählen Sie im `Edit` die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Sobald die Vererbung abgebrochen wurde, können Sie das Symbol „Konfigurieren“ auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration müssen Sie die Vererbung wiederherstellen, indem Sie auf das Symbol `broken link` klicken.

![configure-message-list](assets/configure-message-list.png)

#### Registerkarte „Allgemein“ {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Dienstauswahl**

  (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest, die vom [AEM Communities Messaging Operations Service **`serviceSelector.name`** wird](/help/communities/messaging.md#messaging-operations-service).

* **Seite erstellen**

  (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die Schaltfläche &quot;**`Reply`**&quot; klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Antwort/Als Ressource anzeigen**

  Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Ansicht-URL auf eine Ressource, andernfalls werden Daten als Abfrageparameter in der URL übergeben.

* **Anzeigeformular für Profile**

  Das Profilformular, das zur Anzeige des Absenderprofils verwendet werden soll.

* **Papierkorb-Ordner**

  Wenn diese Option aktiviert ist, zeigt diese Nachrichtenlisten-Komponente nur Nachrichten an, die als gelöscht (Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

  (*Erforderlich*) Verweisen auf die Werte, die für **inbox.path.name** und **sentitems.path.name** im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service) festgelegt sind. Fügen Sie beim Konfigurieren von für eine `Inbox` einen Eintrag mit dem Wert von **inbox.path.name** hinzu. Fügen Sie beim Konfigurieren von für eine `Outbox` einen Eintrag mit dem Wert von &quot;**.path.name“**. Fügen Sie bei der Konfiguration für `Trash` zwei Einträge mit beiden Werten hinzu.

#### Registerkarte „Anzeige“ {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Markieren Sie die Schaltfläche Lesen**

  Wenn diese Option aktiviert ist, wird eine `Read`Schaltfläche“ angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche „Ungelesen markieren**

  Wenn diese Option aktiviert ist, wird eine `Mark Unread`-Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche „Löschen**

  Wenn diese Option aktiviert ist, wird eine `Delete`-Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Dupliziert die Löschfunktion, wenn **`Message Options`** ebenfalls aktiviert ist.

* **Nachrichtenoptionen**

  Wenn diese Option aktiviert ist, werden die Schaltflächen **`Reply`**, **`Reply All`**, **`Forward`** und **`Delete`** angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Dupliziert die Löschfunktion, wenn **`Delete Button`** ebenfalls aktiviert ist.

* **Nachrichten pro Seite**

  Die angegebene Zahl ist die maximale Anzahl von Nachrichten, die pro Seite in einem Paginierungsschema angezeigt wird. Wenn keine Zahl angegeben wird (leer gelassen), werden alle Nachrichten angezeigt und es gibt keine Paginierung.

* **Zeitstempelmuster**

  Zeitstempelmuster für eine oder mehrere Sprachen angeben. Die Standardeinstellung ist für en, de, fr, it, es, ja, zh_CN, ko_KR.

* **Benutzer anzeigen**

  Wählen Sie entweder **`Sender`** oder **`Recipients`** aus, damit Sie bestimmen können, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht erstellen konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite „Nachricht erstellen“ zu ändern, öffnen Sie die Site im [Autoren-Bearbeitungsmodus](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im `Preview`-Modus den **Nachrichten**, um die Hauptseite für Nachrichten zu öffnen. Wählen Sie dann die Schaltfläche Neue Nachricht aus, um die Seite `Compose Message` zu öffnen.

* Wählen Sie im `Edit`-Modus die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Sobald die Vererbung abgebrochen wurde, können Sie das Symbol „Konfigurieren“ auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration müssen Sie die Vererbung wiederherstellen, indem Sie auf das Symbol `broken link` klicken.

![config-compose-message](assets/config-compose-message.png)

#### Registerkarte „Allgemein“ {#basic-tab-1}

![basic-tab-compose](assets/basic-tab-compose.png)

* **Umleitungs-URL**

  Geben Sie die URL der Seite ein, die angezeigt wird, nachdem die Nachricht gesendet wurde. Zum Beispiel: `../messaging.html`.

* **URL abbrechen**

  Geben Sie die URL der Seite ein, wenn der Absender die Nachricht abbricht. Zum Beispiel: `../messaging.html`.

* **Maximale Länge des Nachrichtenbetreffs**

  Die maximal zulässige Anzahl von Zeichen im Feld Betreff . Beispiel: 500. Der Standardwert ist keine Beschränkung.

* **Maximale Länge des Nachrichtentextes**

  Die maximal zulässige Anzahl von Zeichen im Feld Inhalt . Beispiel: 10000. Der Standardwert ist keine Beschränkung.

* **Dienstauswahl**

  (*Erforderlich*) Legen Sie dies auf den Wert der Eigenschaft fest, die vom [AEM Communities Messaging Operations Service **`serviceSelector.name`** wird](/help/communities/messaging.md#messaging-operations-service).

#### Registerkarte „Anzeige“ {#display-tab-1}

![display-tab-compose](assets/display-tab-compose.png)

* **Betrefffeld anzeigen**

  Wenn diese Option aktiviert ist, wird das `Subject` angezeigt und ein Betreff zur Nachricht hinzugefügt. Standard ist nicht aktiviert.

* **Betreffskennzeichnung**

  Geben Sie den Text ein, der neben dem Feld `Subject` angezeigt werden soll. Der Standardwert ist `Subject`.

* **Feld für angehängte Dateien anzeigen**

  Wenn diese Option aktiviert ist, wird das `Attachment` angezeigt und das Hinzufügen von Dateianlagen zur Nachricht aktiviert. Standard ist nicht aktiviert.

* **Dateibezeichnung anhängen**

  Geben Sie den Text ein, der neben dem Feld `Attachment` angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

  Wenn diese Option aktiviert ist, wird das `Content` angezeigt und der Nachrichtentext kann hinzugefügt werden. Standard ist nicht aktiviert.

* **Inhaltsbeschriftung**

  Geben Sie den Text ein, der neben dem Feld `Content` angezeigt werden soll. Der Standardwert ist **`Body`**.

* **mit Rich-Text-Editor**

  Wenn diese Option aktiviert ist, wird ein benutzerdefiniertes Textfeld für Inhalte mit einem eigenen Rich-Text-Editor verwendet. Standard ist nicht aktiviert.

* **Zeitstempelmuster**

  Zeitstempelmuster für eine oder mehrere Sprachen angeben. Die Standardeinstellung ist für en, de, fr, it, es, ja, zh_CN, ko_KR.
