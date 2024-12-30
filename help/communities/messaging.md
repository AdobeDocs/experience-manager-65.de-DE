---
title: Konfigurieren von Messaging
description: Erfahren Sie mehr über die Messaging-Funktion in AEM Communities, die es angemeldeten Site-Besuchern (Mitgliedern) ermöglicht, Nachrichten an einander zu senden.
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

# Konfigurieren von Messaging {#configure-messaging}

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities bietet den angemeldeten Site-Besuchern (Mitgliedern) die Möglichkeit, Nachrichten an einander zu senden, auf die bei der Anmeldung bei der Site zugegriffen werden kann.

Messaging ist für eine Community-Site aktiviert, indem Sie beim Erstellen einer Community[Site ein Kontrollkästchen ](/help/communities/sites-console.md).

Auf dieser Seite finden Sie Informationen zur Standardkonfiguration und zu möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Messaging Essentials](/help/communities/essentials-messaging.md).

## Messaging Operations Service {#messaging-operations-service}

Die Konfiguration [AEM Communities Messaging Operations Service](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Service zum Speichern von Nachrichten verwenden soll, und wenn Nachrichten Dateianhänge enthalten können, welche Dateitypen zulässig sind.

Für Community-Sites, die mit dem `Communities Sites console` erstellt wurden, gibt es eine Instanz des Service, wobei der Posteingang auf `/mail/inbox` gesetzt ist.

### Community Messaging Operations Service {#community-messaging-operations-service}

Wie unten gezeigt, gibt es eine Konfiguration des Services für Sites, die mit dem [Site-Erstellungsassistenten“ erstellt ](/help/communities/sites-console.md). Sie können die Konfiguration anzeigen oder bearbeiten, indem Sie auf das Stiftsymbol neben der Konfiguration klicken.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine Konfiguration hinzuzufügen, klicken Sie auf das Pluszeichen &quot;**+**&quot; neben dem Namen des Services :

* auf die Zulassungsliste setzen **Nachrichtenfelder**

  Gibt die Eigenschaften der Komponente Nachricht erstellen an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, wenn sie in SRP gespeichert werden soll. Der Standardwert ist zwei Einträge *„Betreff* und *Inhalt*.

* **Größenbeschränkung für Nachrichtenfelder**

  Die maximale Anzahl von Byte im Meldungsfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).

* **Maximale Nachrichtenanzahl**

  Die Gesamtzahl der zulässigen Nachrichten pro Benutzer. Der Wert &quot;-1“ bedeutet, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, je nach der Größenbeschränkung des Nachrichtenfelds. Der Standardwert ist *10000* (10k).

* **Benachrichtigung über fehlgeschlagene Sendungen**

  Wenn diese Option aktiviert ist, muss der Absender benachrichtigt werden, wenn der Nachrichtenversand an einige Empfänger fehlschlägt. Der Standardwert ist *aktiviert*.

* **Fehlgeschlagene Versand-Absender-ID**

  Name des Absenders, der in der Fehlernachricht des Versands angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Pfad der Fehlernachrichtenvorlage**

  Absoluter Pfad zum Stamm der fehlgeschlagenen Nachrichtenvorlage für den Versand. Die Standardeinstellung ist */etc/notification/messaging/default*.

* **Anzahl weiterer Versuche**

  Häufigkeit, mit der der erneute Versand einer nicht zugestellten Nachricht versucht wird. Der Standardwert lautet *3*.

* **Warten zwischen weiteren Zustellversuchen**

  Anzahl der Sekunden, die zwischen Versuchen gewartet werden soll, eine Nachricht bei fehlgeschlagenem Senden erneut zu senden. Der Standardwert ist *100* (Sekunden).

* **Anzahl der Poolgrößen aktualisieren**

  Anzahl der gleichzeitigen Threads, die für die Aktualisierung der Zählung verwendet werden Der Standardwert lautet *10*.

* **Pfad des Posteingangs**

  (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den `inbox` Ordner verwendet werden soll. Der Pfad darf NICHT mit einem Schrägstrich (/) enden. Die Standardeinstellung ist */mail/inbox*.

* **Pfad der gesendeten Elemente**

  (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den `sent items` Ordner verwendet werden soll. Der Pfad darf NICHT mit einem Schrägstrich (/) enden. Der Standardwert lautet */mail/sentitems* .

* **Support-Anhänge**

  Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anhänge hinzufügen. Der Standardwert ist *aktiviert*.

* **Gruppennachrichten aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Benutzer Massennachrichten an eine Gruppe von Mitgliedern senden. Der Standardwert lautet *deselected*.

* **Maximale Anzahl der Empfänger insgesamt**

  Wenn Gruppennachrichten aktiviert sind, geben Sie die maximale Anzahl an Empfängern an, an die Gruppennachrichten gleichzeitig gesendet werden können. Der Standardwert lautet *100*.

* **Batch-Größe**

  Anzahl an Nachrichten, die für einen Versand bei Versand an eine große Empfängergruppe im Batch-Modus erstellt werden sollen. Der Standardwert lautet *100*.

* **Gesamtgröße des Anhangs**

  Wenn „supportAttachments“ aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist *104857600* (100 MB).

* auf die Blockierungsliste setzen **Anhangtyp**

  Eine Blockierungsliste von Dateinamenerweiterungen mit dem Präfix &quot;**.**&#39;, das vom System abgelehnt wird. Auf die Blockierungsliste setzen Wenn dies nicht der Fall ist, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &quot;**+**&quot; und &quot;**-**&quot; hinzugefügt oder entfernt werden.

* **Zulässige Anlagentypen**

  **(*Aktion erforderlich*)** Eine Zulassungsliste auf die Blockierungsliste setzte von Dateinamenerweiterungen, das Gegenteil der. Um alle Dateinamenerweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, entfernen Sie mit dem Symbol &quot;**-**&quot; den einzelnen leeren Eintrag.

* **Dienstauswahl**

  (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Service aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der Konfigurationseinstellung *Ausführungspfade* von OSGi-[`Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver) wie `/bin/`, `/apps/` und `/services/` enthalten sein. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** für die `Message List and Compose Message components` bereitgestellt (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)).

  Der Standardwert lautet */bin/messaging* .

* auf die Zulassungsliste setzen **Feld**

  Auf die Zulassungsliste setzen Verwenden Sie **Nachrichtenfelder**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service` zur Bearbeitung geöffnet wird und `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag eingefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianhänge effektiv.
>
>Um alle Dateinamenerweiterungen, mit Ausnahme der auf die Blockierungsliste gesetzt, zuzulassen, entfernen Sie mithilfe des Symbols &quot;**-**&quot; (erneut) den leeren Eintrag, bevor Sie auf **Speichern** klicken.

## Gruppen-Messaging {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, stellen Sie sicher, dass Sie **Gruppennachrichten aktivieren** in den folgenden beiden Instanzen der Konfiguration **Messaging Operation Services** aktivieren:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Messaging Operations Service: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging Operations Service: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit, Probleme zu beheben, besteht darin, [Debugging-Meldungen im Protokoll“ zu aktivieren](/help/sites-administering/troubleshooting.md)

Siehe auch [Logger und Writer für einzelne Services](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
