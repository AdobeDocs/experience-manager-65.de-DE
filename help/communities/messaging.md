---
title: Messaging konfigurieren
description: Erfahren Sie mehr über die Messaging-Funktion in AEM Communities, mit der angemeldete Site-Besucher (Mitglieder) Nachrichten miteinander senden können.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: ee94f093-fd14-49f2-9990-fbe853d924b1
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Messaging konfigurieren {#configure-messaging}

## Übersicht {#overview}

Die Messaging-Funktion für AEM Communities bietet angemeldeten Site-Besuchern (Mitgliedern) die Möglichkeit, Nachrichten miteinander zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Messaging wird für eine Community-Site aktiviert, indem Sie ein Kästchen bei [Community-Site-Erstellung](/help/communities/sites-console.md).

Diese Seite enthält Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Grundlagen zu Messaging](/help/communities/essentials-messaging.md).

## Messaging Operations-Dienst {#messaging-operations-service}

Die Konfiguration [AEM Communities Messaging-Dienst](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden soll, und wenn Nachrichten Dateianlagen enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit der `Communities Sites console`, eine Instanz des Dienstes vorhanden ist, wobei der Posteingang auf `/mail/inbox`.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit der [Assistent zur Site-Erstellung](/help/communities/sites-console.md). Die Konfiguration kann durch Auswahl des Stiftsymbols neben der Konfiguration angezeigt oder bearbeitet werden.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine Konfiguration hinzuzufügen, wählen Sie das Pluszeichen &quot;**+**&#39; neben dem Namen des Dienstes :

* **Zulassungsliste der Nachrichtenfelder**

  Gibt die Eigenschaften der Komponente Nachricht erstellen an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie im SRP gespeichert werden kann. Der Standardwert ist zwei Einträge: *subject* und *content*.

* **Größenbeschränkung für Nachrichtenfelder**

  Die maximale Anzahl von Bytes im Nachrichtenfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).

* **Begrenzung der Nachrichtenanzahl**

  Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 zeigt an, dass vorbehaltlich der Begrenzung der Nachrichtenfeldgröße eine unbegrenzte Anzahl von Nachrichten zulässig ist. Der Standardwert ist *10000* (10k).

* **Versandfehler benachrichtigen**

  Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn der Nachrichtenversand bei einigen Empfängern fehlschlägt. Der Standardwert ist *aktiviert*.

* **Versandabsender-ID eines fehlgeschlagenen Versands**

  Name des Absenders, der in der Nachricht mit fehlgeschlagenen Sendungen angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Pfad der Fehlermeldungsvorlage**

  Absoluter Pfad zum Stamm der fehlgeschlagenen Nachrichtenvorlage für den Versand. Der Standardwert ist */etc/notification/messaging/default*.

* **Anzahl weiterer Versuche**

  Gibt an, wie oft eine erneute Nachricht versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.

* **Warten zwischen Wiederholungen**

  Anzahl der Sekunden, die zwischen Versuchen gewartet werden soll, die Nachricht bei fehlgeschlagenem Versand erneut zu senden. Der Standardwert ist *100* (Sekunden).

* **Anzahl der Aktualisierungspool-Größe**

  Anzahl der gleichzeitigen Threads, die für die Aktualisierung der Anzahl verwendet werden. Der Standardwert ist *10*.

* **Posteingangspfad**

  (*Erforderlich*) Der Pfad, relativ zum Knoten des Benutzers (/home/users/*Benutzername*), um für die `inbox` Ordner. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/inbox*.

* **Pfad für gesendete Elemente**

  (*Erforderlich*) Der Pfad, relativ zum Knoten des Benutzers (/home/users/*Benutzername*), um für die `sent items` Ordner. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/sentitems* .

* **Anlagen unterstützen**

  Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist *aktiviert*.

* **Gruppennachrichten aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Benutzer eine Massennachricht an eine Gruppe von Mitgliedern senden. Der Standardwert ist *ungewählt*.

* **Maximale Anzahl Gesamtzahl der Empfänger**

  Wenn Gruppennachrichten aktiviert sind, geben Sie die maximale Anzahl von Empfängern an, an die Gruppennachrichten gleichzeitig gesendet werden können. Der Standardwert ist *100*.

* **Stapelgröße**

  Anzahl der Nachrichten, die im Batch-Vorgang an eine große Empfängergruppe gesendet werden. Der Standardwert ist *100*.

* **Gesamtgröße der Anlage**

  Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist *104857600* (100 MB).

* **Blockierungsliste zum Anlagentyp**

  Eine Blockierungsliste von Dateinamenerweiterungen mit dem Präfix &quot;**.**&#39;, das vom System abgelehnt wird. Wenn die Erweiterung nicht auf die Blockierungsliste gesetzt wird, ist sie zulässig. Erweiterungen können mit dem **+**&#39; und &#39;**-**&quot;.

* **Zulässige Anlagentypen**

  **(*Erforderliche Aktion*)** Eine Zulassungsliste von Dateinamenerweiterungen, das Gegenteil von der Blockierungsliste. Um alle Dateinamenerweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie die **-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **Dienstauswahl**

  (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss einen im *Ausführungspfade* Konfigurationseinstellung der OSGi-Konfiguration [`Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), beispielsweise `/bin/`, `/apps/`, und `/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** Wert für `Message List and Compose Message components` (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)).

  Der Standardwert ist */bin/messaging* .

* **Feld-Zulassungsliste**

  Verwendung **Zulassungsliste der Nachrichtenfelder**.

>[!CAUTION]
>
>Jedes Mal, wenn ein `Messaging Operations Service` -Konfiguration zur Bearbeitung geöffnet ist, wenn `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateinamenerweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie die **-**&quot;(erneut) Symbol, um den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **Speichern**.

## Gruppennachrichten {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, stellen Sie sicher, dass **Gruppennachrichten aktivieren** in den beiden folgenden Instanzen von **Messaging-Vorgangsdienste** Konfiguration:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Messaging Operations Service: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging Operations Service: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit, Probleme zu beheben, besteht darin, [Debugging von Meldungen im Protokoll.](/help/sites-administering/troubleshooting.md)

Siehe auch [Logger und Writer für einzelne Dienste](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
