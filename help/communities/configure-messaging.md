---
title: Messaging-Funktion
description: Erfahren Sie, wie Sie die Messaging-Funktion von AEM Communities so konfigurieren, dass Community-Mitglieder privat miteinander interagieren können.
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

Zusätzlich zu den öffentlich sichtbaren Interaktionen in Foren und Kommentaren ermöglicht die Messaging-Funktion von AEM Communities es Community-Mitgliedern, privat miteinander zu interagieren.

Diese Funktion kann eingeschlossen werden, wenn eine [Community-Site](/help/communities/overview.md#communitiessites) erstellt wird.

Mit der Messaging-Funktion haben Sie folgende Möglichkeiten:

**A** - Senden einer Nachricht an ein oder mehrere Community-Mitglieder

**B** - Senden von Direktnachrichten in [Massen an Community-Mitgliedergruppen](/help/communities/messaging.md#group-messaging)

**C** - Senden einer Nachricht mit Anhängen

**D** - Weiterleiten einer Nachricht

**E** - Antwort auf eine Nachricht

**F** - Löschen einer Nachricht

**G** - Wiederherstellen einer gelöschten Nachricht

![messaging-section](assets/messaging-section.png)

![restore-message](assets/restore-message.png)

Informationen zum Aktivieren und Ändern der Messaging-Funktion finden Sie unter:

* [Messaging konfigurieren](/help/communities/messaging.md) für Administratoren
* [Messaging Essentials](/help/communities/essentials-messaging.md) für Entwickler

>[!NOTE]
>
>Das Hinzufügen von `Compose Message, Message, or Message List` -Komponenten (in der `Communities`Komponentengruppe) zu einer Seite im Bearbeitungsmodus für Autoren wird nicht unterstützt.

## Messaging-Komponenten konfigurieren {#configure-messaging-components}

Wenn Messaging für eine Community-Site aktiviert ist, wird es ohne weitere Konfiguration eingerichtet. Die Informationen werden bereitgestellt, wenn die Standardkonfiguration geändert werden muss.

### Nachrichtenliste konfigurieren (Meldungsfeld) {#configure-message-list-message-box}

Um die Konfiguration der Nachrichtenliste für die Seiten **Posteingang**, **Gesendete Elemente** und **Papierkorb** der Messaging-Funktion zu ändern, öffnen Sie die Site im Bearbeitungsmodus [Autor](/help/communities/sites-console.md#authoring-site-content).

1. Wählen Sie im Modus `Preview` den Link **Nachrichten** aus, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann entweder **Posteingang**, **Gesendete Elemente** oder **Papierkorb** aus, um die Komponente für diese Nachrichtenliste zu konfigurieren.

1. Wählen Sie im Modus `Edit` die Komponente auf der Seite aus.
1. Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

1. Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![configure-message-list](assets/configure-message-list.png)

#### Registerkarte &quot;Allgemein&quot; {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Service selector**

  (*Erforderlich*) Setzen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** aus dem [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

* **Seite erstellen**

  (*Erforderlich*) Die Seite, die geöffnet werden soll, wenn ein Mitglied auf die Schaltfläche **`Reply`** klickt. Die Zielseite sollte das Formular **Nachricht erstellen** enthalten.

* **Antworten/Als Ressource anzeigen**

  Wenn diese Option aktiviert ist, verweisen die Antwort-URL und die Anzeigen-URL auf eine Ressource. Andernfalls werden Daten als Abfrageparameter in der URL übergeben.

* **Formular zur Profilanzeige**

  Das Profilformular, das zum Anzeigen des Senderprofils verwendet werden soll.

* **Ordner &quot;Papierkorb&quot;**

  Wenn diese Option aktiviert ist, zeigt diese Komponente nur Nachrichten an, die als gelöscht (Papierkorb) gekennzeichnet sind.

* **Ordnerpfade**

  (*Erforderlich*) Referenzieren der Werte, die für **inbox.path.name** und **sentitems.path.name** im [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service) festgelegt wurden. Fügen Sie bei der Konfiguration für einen `Inbox` einen Eintrag mit dem Wert **inbox.path.name** hinzu. Fügen Sie bei der Konfiguration für einen `Outbox` einen Eintrag mit dem Wert **sentitems.path.name** hinzu. Fügen Sie bei der Konfiguration für `Trash` zwei Einträge mit beiden Werten hinzu.

#### Registerkarte &quot;Anzeige&quot; {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Schaltfläche &quot;Gelesen&quot;markieren**

  Wenn diese Option aktiviert ist, wird eine `Read`Schaltfläche angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche &quot;Ungelesen markieren&quot;**

  Wenn diese Option aktiviert ist, wird eine Schaltfläche `Mark Unread` angezeigt, mit der eine Nachricht als gelesen markiert werden kann.

* **Schaltfläche &quot;Löschen&quot;**

  Wenn diese Option aktiviert ist, wird eine Schaltfläche `Delete` angezeigt, mit der eine Nachricht als gelesen markiert werden kann. Dupliziert die Löschfunktion, wenn auch **`Message Options`** aktiviert ist.

* **Nachrichtenoptionen**

  Falls aktiviert, werden die Schaltflächen **`Reply`**, **`Reply All`**, **`Forward`** und **`Delete`** angezeigt, mit denen eine Nachricht erneut gesendet oder gelöscht werden kann. Dupliziert die Löschfunktion, wenn auch **`Delete Button`** aktiviert ist.

* **Nachrichten pro Seite**

  Die angegebene Anzahl entspricht der maximalen Anzahl an Nachrichten, die pro Seite in einem Paginierungsschema angezeigt werden. Wenn keine Zahl angegeben (leer gelassen) wird, werden alle Nachrichten angezeigt und es wird keine Paginierung durchgeführt.

* **Zeitstempelmuster**

  Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Der Standardwert ist für en, de, fr, es, ja, zh_CN, ko_KR.

* **Benutzer anzeigen**

  Wählen Sie entweder **`Sender`** oder **`Recipients`** aus, damit Sie bestimmen können, ob der Absender oder die Empfänger angezeigt werden sollen.

### Nachricht erstellen konfigurieren {#configure-compose-message}

Um die Konfiguration der Seite mit der Komprimierungsmeldung zu ändern, öffnen Sie die Site im [Bearbeitungsmodus für Autoren](/help/communities/sites-console.md#authoring-site-content).

* Wählen Sie im Modus `Preview` den Link **Nachrichten** aus, um die Hauptseite der Nachrichten zu öffnen. Wählen Sie dann die Schaltfläche Neue Nachricht aus, damit Sie die Seite `Compose Message` öffnen können.

* Wählen Sie im Modus `Edit` die Hauptkomponente auf der Seite aus, die den Nachrichtentext enthält.
* Um auf das Konfigurationsdialogfeld zuzugreifen, brechen Sie die Vererbung ab, indem Sie das Symbol `link` auswählen.
Nachdem die Vererbung abgebrochen wurde, können Sie das Konfigurationssymbol auswählen, um das Konfigurationsdialogfeld zu öffnen.

* Nach Abschluss der Konfiguration muss die Vererbung durch Auswahl des Symbols `broken link` wiederhergestellt werden.

![config-compse-message](assets/config-compose-message.png)

#### Registerkarte &quot;Allgemein&quot; {#basic-tab-1}

![basic-tab-compse](assets/basic-tab-compose.png)

* **Umleitungs-URL**

  Geben Sie die URL der Seite ein, die nach dem Versand der Nachricht angezeigt wird. Zum Beispiel: `../messaging.html`.

* **URL abbrechen**

  Geben Sie die URL der Seite ein, die angezeigt wird, wenn der Absender die Nachricht abbricht. Zum Beispiel: `../messaging.html`.

* **Maximale Länge des Nachrichtenbetreffs**

  Die maximal zulässige Anzahl von Zeichen im Feld Betreff. Beispiel: 500. Der Standardwert ist keine Begrenzung.

* **Maximale Länge des Nachrichtentextes**

  Die maximal zulässige Anzahl von Zeichen im Feld Inhalt . Beispiel: 10000. Der Standardwert ist keine Begrenzung.

* **Service selector**

  (*Erforderlich*) Setzen Sie dies auf den Wert der Eigenschaft **`serviceSelector.name`** aus dem [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

#### Registerkarte &quot;Anzeige&quot; {#display-tab-1}

![display-tab-compse](assets/display-tab-compose.png)

* **Betrefffeld anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie das Feld `Subject` an und aktivieren Sie das Hinzufügen eines Betreffs zur Nachricht. Die Option Standard ist nicht aktiviert.

* **Betreffbezeichnung**

  Geben Sie den Text ein, der neben dem Feld `Subject` angezeigt werden soll. Der Standardwert ist `Subject`.

* **Feld für Dateianhang anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie das Feld `Attachment` an und aktivieren Sie das Hinzufügen von Dateianlagen zur Nachricht. Die Option Standard ist nicht aktiviert.

* **Dateinamen anhängen**

  Geben Sie den Text ein, der neben dem Feld `Attachment` angezeigt werden soll. Der Standardwert ist **`Attach File`**.

* **Inhaltsfeld anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie das Feld `Content` an und aktivieren Sie das Hinzufügen eines Nachrichtentextes. Die Option Standard ist nicht aktiviert.

* **Inhaltsbeschriftung**

  Geben Sie den Text ein, der neben dem Feld `Content` angezeigt werden soll. Der Standardwert ist **`Body`**.

* **Mit Rich-Text-Editor**

  Ist diese Option aktiviert, wird die Verwendung eines benutzerdefinierten Textfelds &quot;Inhalt&quot;mit einem eigenen Rich-Text-Editor angezeigt. Die Option Standard ist nicht aktiviert.

* **Zeitstempelmuster**

  Stellen Sie Zeitstempelmuster für eine oder mehrere Sprachen bereit. Der Standardwert ist für en, de, fr, es, ja, zh_CN, ko_KR.
