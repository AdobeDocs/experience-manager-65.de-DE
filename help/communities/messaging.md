---
title: Nachrichten konfigurieren
seo-title: Messaging konfigurieren
description: Communities-Messaging
seo-description: Communities-Messaging
uuid: 159dcf9d-7948-4a3d-9f51-a5b4d03e172b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 232a0ec1-8dfc-41ec-84cc-69f9db494ea0
docset: aem65
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 2%

---


# Messaging {#configure-messaging} konfigurieren

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities ermöglicht es Besuchern (Teilnehmern) mit angemeldeten Sites, Nachrichten an andere zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Die Messaging-Funktion ist für eine Community-Site aktiviert, indem Sie bei [Community-Site-Erstellung](/help/communities/sites-console.md) ein Kontrollkästchen aktivieren.

Diese Seite enthält Informationen zur Standardkonfiguration und möglichen Anpassungen.

Weitere Informationen für Entwickler finden Sie unter [Messaging Essentials](/help/communities/essentials-messaging.md).

## Messaging Operations Service {#messaging-operations-service}

Die Konfiguration [AEM Communities Messaging Operations Service](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der mit Messaging zusammenhängende Anfragen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden sollte, und wenn Meldungen Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit `Communities Sites console` erstellt wurden, ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/inbox` eingestellt ist.

### Community Messaging Operations Service {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Assistenten zum Erstellen der Site](/help/communities/sites-console.md) erstellt wurden. Die Konfiguration kann angezeigt oder bearbeitet werden, indem Sie auf das Stiftsymbol neben der Konfiguration klicken.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine neue Konfiguration hinzuzufügen, wählen Sie neben dem Dienstnamen das Pluszeichen &quot;**+**&quot;aus:

* **Zulassungsliste der Nachrichtenfelder**

   Gibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Die Standardeinstellung sind zwei Einträge: *subject* und *content*.

* **Begrenzung der Größe des Meldungsfelds**

   Die maximale Anzahl von Bytes im Meldungsfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).

* **Begrenzung der Nachrichtenanzahl**

   Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist *10000* (10k).

* **Versand-Fehler benachrichtigen**

   Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn der Versand in einigen Empfängern fehlschlägt. Die Standardeinstellung ist *markiert*.

* **Versand-Absender-ID versagen**

   Name des Absenders, der in der Fehlermeldung angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Fehlermeldungsvorlagenpfad**

   Absoluter Pfad zum Fehlermeldungsvorlagenstamm des Versands. Der Standardwert ist */etc/notification/messaging/default*.

* **Anzahl der weitere Zustellversuche**

   Anzahl der Male, die eine erneute Meldung versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.

* **Zwischen weiteren Zustellversuchen warten**

   Anzahl der Sekunden, die zwischen Versuchen, eine Nachricht erneut zu senden, zu warten sind, wenn das Senden fehlgeschlagen ist. Der Standardwert ist *100* (Sekunden).

* **Anzahl der Updatepoolgröße**

   Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist *10*.

* **Posteingangspfad**

   (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*Benutzername*), der für den Ordner `inbox` verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox*.

* **Pfad zu gesendeten Elementen**

   (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*Benutzername*), der für den Ordner `sent items` verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .

* **Unterstützungsanlagen**

   Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Die Standardeinstellung ist *markiert*.

* **Aktivieren der Gruppennachrichten**

   Wenn diese Option aktiviert ist, können registrierte Benutzer eine Massennachricht an eine Gruppe von Mitgliedern senden. Die Standardeinstellung ist *deaktiviert*.

* **Maximale Anzahl der Gesamtzahl der Empfänger**

   Wenn Gruppennachrichten aktiviert ist, geben Sie die maximale Anzahl von Empfängern an, an die eine Gruppennachricht gleichzeitig gesendet werden kann. Der Standardwert ist *100*.

* **Batch-Größe**

   Anzahl der Nachrichten, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist *100*.

* **Anlagengröße insgesamt**

   Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Der Standardwert ist *104857600* (100 MB).

* **Blockierungsliste zum Anlagentyp**

   Eine Blockierungsliste von Dateinamenerweiterungen mit dem Präfix &quot;**.**&quot;, die vom System abgelehnt werden. Wenn sie nicht auf die Blockierungsliste gesetzt wird, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &quot;**+**&quot;und &quot;**-**&quot;hinzugefügt oder entfernt werden.

* **Zulässige Anlagentypen**

   **(*Aktion erforderlich*)** Eine Zulassungsliste von Dateinamenerweiterungen, die der Blockierungsliste entgegengesetzt ist. Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &quot;**-**&quot;, um den einzelnen leeren Eintrag zu entfernen.

* **Dienstauswahl**

   (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der Konfigurationseinstellung *Ausführungspfade* von OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), wie `/bin/`, `/apps/` und `/services/` enthalten sein. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`**-Wert für `Message List and Compose Message components` bereitgestellt (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)).

   Die Standardeinstellung ist */bin/messaging* .

* **Feld-Zulassungsliste**

   Verwenden Sie die Zulassungsliste **Nachrichtenfelder**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service`-Konfiguration zur Bearbeitung geöffnet wird und `allowedAttachmentTypes.name` entfernt wurde, wird ein leerer Eintrag erneut hinzugefügt, um die Eigenschaft konfigurierbar zu machen. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateierweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &quot;**-**&quot;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **Speichern** klicken.

## Gruppennachrichten {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, vergewissern Sie sich, dass Sie in den folgenden beiden Instanzen der Konfiguration **Nachrichtenoperationsdienste** die Option **Gruppennachrichten aktivieren:**

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Messaging-Dienst: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging-Dienst: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit zur Fehlerbehebung besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](/help/sites-administering/troubleshooting.md)

Siehe auch [Anmelder und Autoren für individuelle Dienste](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
