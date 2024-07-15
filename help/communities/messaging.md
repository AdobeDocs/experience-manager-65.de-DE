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

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities bietet angemeldeten Site-Besuchern (Mitgliedern) die Möglichkeit, Nachrichten miteinander zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Das Messaging für eine Community-Site wird aktiviert, indem während der [Erstellung der Community-Site](/help/communities/sites-console.md) ein Kontrollkästchen aktiviert wird.

Diese Seite enthält Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Messaging Essentials](/help/communities/essentials-messaging.md).

## Messaging Operations-Dienst {#messaging-operations-service}

Die Konfiguration [AEM Communities Messaging Operations Service](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden soll, und wenn Nachrichten Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit dem Wert `Communities Sites console` erstellt wurden, ist eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/inbox` gesetzt ist.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Website-Erstellungsassistenten](/help/communities/sites-console.md) erstellt wurden. Die Konfiguration kann durch Auswahl des Stiftsymbols neben der Konfiguration angezeigt oder bearbeitet werden.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine Konfiguration hinzuzufügen, wählen Sie das Pluszeichen &quot;**+**&quot;neben dem Namen des Dienstes aus:

* **Nachrichtenfelder - Zulassungsliste**

  Gibt die Eigenschaften der Komponente Nachricht erstellen an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie im SRP gespeichert werden kann. Der Standardwert ist zwei Einträge: *subject* und *content*.

* **Größenbeschränkung für Nachrichtenfelder**

  Die maximale Anzahl von Bytes im Nachrichtenfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).

* **Begrenzung der Nachrichtenanzahl**

  Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 zeigt an, dass vorbehaltlich der Begrenzung der Nachrichtenfeldgröße eine unbegrenzte Anzahl von Nachrichten zulässig ist. Der Standardwert ist *10000* (10 k).

* **Versandfehler benachrichtigen**

  Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn der Nachrichtenversand bei einigen Empfängern fehlschlägt. Der Standardwert ist *markiert*.

* **Versandabsender-ID eines fehlgeschlagenen Versands**

  Name des Absenders, der in der Nachricht mit fehlgeschlagenen Sendungen angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Pfad der Fehlermeldungsvorlage**

  Absoluter Pfad zum Stamm der fehlgeschlagenen Nachrichtenvorlage für den Versand. Der Standardwert ist */etc/notification/messaging/default*.

* **Anzahl weiterer Versuche**

  Gibt an, wie oft eine erneute Nachricht versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.

* **Warten zwischen Wiederholungen**

  Anzahl der Sekunden, die zwischen Versuchen gewartet werden soll, die Nachricht bei fehlgeschlagenem Versand erneut zu senden. Der Standardwert ist *100* (Sekunden).

* **Anzahl der aktualisierten Poolgröße**

  Anzahl der gleichzeitigen Threads, die für die Aktualisierung der Anzahl verwendet werden. Der Standardwert ist *10*.

* **Posteingangspfad**

  (*Erforderlich*) Der Pfad, der relativ zum Knoten des Benutzers (/home/users/*Benutzername*) für den Ordner `inbox` verwendet wird. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/inbox*.

* **Pfad der gesendeten Elemente**

  (*Erforderlich*) Der Pfad, der relativ zum Knoten des Benutzers (/home/users/*Benutzername*) für den Ordner `sent items` verwendet wird. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich ( &#39;/&#39;) enden. Der Standardwert ist */mail/sentitems* .

* **Anlagen unterstützen**

  Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Der Standardwert ist *markiert*.

* **Aktivieren Sie Gruppennachrichten**

  Wenn diese Option aktiviert ist, können registrierte Benutzer eine Massennachricht an eine Gruppe von Mitgliedern senden. Der Standardwert ist *nicht ausgewählt*.

* **Maximum no. der Gesamt-Empfänger**

  Wenn Gruppennachrichten aktiviert sind, geben Sie die maximale Anzahl von Empfängern an, an die Gruppennachrichten gleichzeitig gesendet werden können. Der Standardwert ist *100*.

* **Stapelgröße**

  Anzahl der Nachrichten, die im Batch-Vorgang an eine große Empfängergruppe gesendet werden. Der Standardwert ist *100*.

* **Gesamtgröße des Anhangs**

  Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist *104857600* (100 MB).

* **Blockierungsliste des Anlagentyps**

  Eine Blockierungsliste von Dateinamenerweiterungen mit dem Präfix &quot;**&quot;.**&#39;, der vom System abgelehnt wird. Wenn die Erweiterung nicht auf die Blockierungsliste gesetzt wird, ist sie zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden.

* **Zulässige Anlagentypen**

  **(*Aktion erforderlich*)** Eine Zulassungsliste von Dateinamenerweiterungen, die der Blockierungsliste entgegensteht. Um alle Dateinamenerweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie das Symbol &quot;**-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **Service selector**

  (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der Konfigurationseinstellung *Ausführungspfade* der OSGi-Konfiguration [`Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver) enthalten sein, z. B. `/bin/`, `/apps/` und `/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** -Wert für den `Message List and Compose Message components` bereitgestellt (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)).

  Der Standardwert ist */bin/messaging* .

* **Feld-Zulassungsliste**

  Verwenden Sie die Zulassungsliste **Nachrichtenfelder-**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service` -Konfiguration zur Bearbeitung geöffnet wird und `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateinamenerweiterungen zuzulassen, mit Ausnahme der auf die Blockierungsliste gesetzt, verwenden Sie das Symbol &quot;**-**&quot;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **Speichern** klicken.

## Gruppennachrichten {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, stellen Sie sicher, dass Sie **Gruppennachrichten aktivieren** in den beiden folgenden Instanzen der Konfiguration von **Messaging Operation Services** aktivieren:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Messaging Operations Service: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging Operations Service: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit, Probleme zu beheben, besteht darin, das [Debugging von Meldungen im Protokoll zu aktivieren.](/help/sites-administering/troubleshooting.md)

Siehe auch [Logger und Writer für einzelne Dienste](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
