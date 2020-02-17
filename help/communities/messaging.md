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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Nachrichten konfigurieren{#configure-messaging}

## Überblick {#overview}

Die Messaging-Funktion für AEM Communities bietet Besuchern (Mitgliedern) der angemeldeten Site die Möglichkeit, Nachrichten miteinander zu senden, auf die beim Anmelden der Site zugegriffen werden kann.

Die Messaging-Funktion wird für eine Community-Site aktiviert, indem während der Erstellung[](/help/communities/sites-console.md)einer Community-Site ein Kästchen markiert wird.

Diese Seite enthält Informationen zur Standardkonfiguration und möglichen Anpassungen.

For additional information for developers, see [Messaging Essentials](/help/communities/essentials-messaging.md).

## Messaging-Dienst {#messaging-operations-service}

Der [AEM Communities Messaging Operations-Dienst](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identifiziert den Endpunkt, der Messaging-bezogene Anforderungen verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden sollte, und wenn Meldungen Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit dem erstellt wurden, `Communities Sites console`ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/inbox`festgelegt ist.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Site-Erstellungsassistenten](/help/communities/sites-console.md)erstellt wurden. Die Konfiguration kann angezeigt oder bearbeitet werden, indem Sie auf das Stiftsymbol neben der Konfiguration klicken.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine neue Konfiguration hinzuzufügen, klicken Sie auf das Plus-Symbol **+** neben dem Dienstnamen:

* **Whitelist für Nachrichtenfelder** Gibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Der Standardwert ist zwei Einträge: *Betreff* und *Inhalt*.

* **Begrenzung** der Größe des Meldungsfelds Die maximale Anzahl von Byte im Meldungsfeld jedes Benutzers. Der Standardwert ist *1073741824 *(1 GB).

* **Begrenzung** der Nachrichtenanzahl Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist *10000* (10 k).

* **Benachrichtigt einen Lieferfehler** Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn die Nachrichtenübermittlung bei einigen Empfängern fehlschlägt. Default is *checked*.

* **Fehler-Absender-ID** Name des Absenders, der in der Meldung über den Lieferfehler angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Fehlermeldungsvorlagenpfad** Absoluter Pfad zum Stammordner für die ausgelieferte Meldung. Der Standardwert ist */etc/notification/messaging/default*.

* **Anzahl der Wiederholungen** Anzahl der Male, die eine erneute Meldung versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.

* **Warten Sie zwischen Wiederholungen** Anzahl der Sekunden, die zwischen Versuchen, eine Nachricht erneut zu senden, zu warten sind, wenn das Senden fehlgeschlagen ist. Der Standardwert ist *100 *(Sekunden).

* **Anzahl der Updatepool-Größe** Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist *10*.

* **Posteingangspfad**(*Erforderlich*) Der Pfad relativ zum Benutzerknoten (/home/users/*username*), der für den **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox.*

* **Pfad** der gesendeten Elemente (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`send items`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .

* **Unterstützung von Anlagen** Wenn diese aktiviert sind, können Benutzer ihren Nachrichten Anlagen hinzufügen. Default is *checked*.

* **Gruppennachrichten** aktivieren Wenn diese Option aktiviert ist, können registrierte Benutzer eine Massennachricht an eine Gruppe von Mitgliedern senden. &quot;Standard&quot;ist *deaktiviert*.

* **Maximale Anzahl der Gesamtzahl der Empfänger** Wenn Gruppennachrichten aktiviert ist, geben Sie die maximale Anzahl der Empfänger an, an die eine Gruppennachricht gleichzeitig gesendet werden kann. Der Standardwert ist *100*.

* **Stapelgröße** Anzahl der Meldungen, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist *100*.

* **Gesamtgröße** der Anlage Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Default is *104857600* (100 MB).

* **Attachment type black list** Eine schwarze Liste mit Dateinamenerweiterungen, mit dem Präfix &#39;**.**&quot;, die vom System abgelehnt werden. Falls nicht auf der schwarzen Liste aufgeführt, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden.

* **Zulässige Anlagentypen**
   **(*Aktion erforderlich*)** Eine Whitelist der Dateinamenerweiterungen, das Gegenteil der schwarzen Liste. Um alle Dateierweiterungen mit Ausnahme der auf der schwarzen Liste aufgeführten zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um den einzelnen leeren Eintrag zu entfernen.

* **Dienstauswahl**(*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der OSGi-Konfiguration für die *Ausführungspfade* enthalten sein [ wie `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`und `/apps/``/services/`. Zur Auswahl dieser Konfiguration für die Messaging-Funktion einer Site wird dieser Endpunkt als **`Service selector`** Wert für die `Message List and Compose Message components` (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)) bereitgestellt.
Die Standardeinstellung ist */bin/messaging* .

* **Whitelist für Felder mit****Meldungsfeldern verwenden**.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service` Konfiguration zur Bearbeitung geöffnet wird und sie entfernt `allowedAttachmentTypes.name` wurde, wird ein leerer Eintrag erneut hinzugefügt, damit die Eigenschaft konfiguriert werden kann. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateinamenerweiterungen mit Ausnahme der auf der schwarzen Liste aufgeführten zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **Speichern** klicken.

## Group Messaging {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, stellen Sie sicher, dass Sie **Gruppennachrichten aktivieren **in den folgenden beiden Instanzen der Konfiguration von **Messaging-Vorgangsdiensten** aktivieren:

* com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console
* com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging

**Messaging-Dienst: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging-Dienst: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit zur Fehlerbehebung besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](/help/sites-administering/troubleshooting.md)

Siehe auch [Anmelder und Autoren für individuelle Services](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
