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
source-git-commit: df59879cfa6b0bc7eba13f679e833fabbcbe92f2
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 2%

---


# Nachrichten konfigurieren {#configure-messaging}

## Übersicht {#overview}

Die Messaging-Funktion für AEM Communities ermöglicht es Besuchern mit angemeldeten Sites (Mitgliedern), Nachrichten an andere zu senden, auf die bei der Anmeldung auf der Site zugegriffen werden kann.

Die Messaging-Funktion wird für eine Community-Site aktiviert, indem während der Erstellung [](/help/communities/sites-console.md)einer Community-Site ein Kästchen markiert wird.

Diese Seite enthält Informationen zur Standardkonfiguration und möglichen Anpassungen.

For additional information for developers, see [Messaging Essentials](/help/communities/essentials-messaging.md).

## Messaging-Dienst {#messaging-operations-service}

Der Nachrichtendienst [&quot;Messaging Operations&quot;](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) AEM Communities zur Konfiguration identifiziert den Endpunkt, der mit Anfragen im Zusammenhang mit Nachrichten verarbeitet, die Ordner, die der Dienst zum Speichern von Nachrichten verwenden sollte, und wenn Meldungen Dateianhänge enthalten können, welche Dateitypen sind zulässig.

Für Community-Sites, die mit dem erstellt wurden, `Communities Sites console`ist bereits eine Instanz des Dienstes vorhanden, wobei der Posteingang auf `/mail/inbox`festgelegt ist.

### Community Messaging-Dienst {#community-messaging-operations-service}

Wie unten gezeigt, existiert eine Konfiguration des Dienstes für Sites, die mit dem [Site-Erstellungsassistenten](/help/communities/sites-console.md)erstellt wurden. Die Konfiguration kann angezeigt oder bearbeitet werden, indem Sie auf das Stiftsymbol neben der Konfiguration klicken.

![messaging-operations](assets/messaging-operations.png)

### Neue Konfiguration hinzufügen {#add-new-configuration}

Um eine neue Konfiguration hinzuzufügen, klicken Sie auf das Plus-Symbol **+** neben dem Dienstnamen:

* **Nachrichtenfelder Zulassungsliste**

   Gibt die Eigenschaften der Komponente &quot;Nachricht erstellen&quot;an, die Benutzer bearbeiten und beibehalten können. Wenn neue Formularelemente hinzugefügt werden, muss die Element-ID hinzugefügt werden, falls gewünscht, damit sie in SRP gespeichert werden kann. Die Standardeinstellung sind zwei Einträge: *Betreff* und *Inhalt*.

* **Begrenzung der Größe des Meldungsfelds**

   Die maximale Anzahl von Bytes im Meldungsfeld jedes Benutzers. Der Standardwert ist *1073741824* (1 GB).

* **Begrenzung der Nachrichtenanzahl**

   Die Gesamtzahl der pro Benutzer zulässigen Nachrichten. Der Wert -1 gibt an, dass eine unbegrenzte Anzahl von Nachrichten zulässig ist, sofern die Größe des Meldungsfelds begrenzt ist. Der Standardwert ist *10000* (10 k).

* **Versand-Fehler benachrichtigen**

   Wenn diese Option aktiviert ist, benachrichtigen Sie den Absender, wenn der Versand in einigen Empfängern fehlschlägt. Default is *checked*.

* **Versand-Absender-ID versagen**

   Name des Absenders, der in der Fehlermeldung angezeigt wird. Der Standardwert ist *failureNotifier*.

* **Fehlermeldungsvorlagenpfad**

   Absoluter Pfad zum Fehlermeldungsvorlagenstamm des Versands. Der Standardwert ist */etc/notification/messaging/default*.

* **Anzahl der weitere Zustellversuche**

   Anzahl der Male, die eine erneute Meldung versucht werden soll, die nicht zugestellt werden kann. Der Standardwert ist *3*.

* **Zwischen weiteren Zustellversuchen warten**

   Anzahl der Sekunden, die zwischen Versuchen, eine Nachricht erneut zu senden, zu warten sind, wenn das Senden fehlgeschlagen ist. Default is *100* (seconds).

* **Anzahl der Updatepoolgröße**

   Anzahl der gleichzeitigen Threads, die für die Zähleraktualisierung verwendet werden. Der Standardwert ist *10*.

* **Posteingangspfad**

   (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`inbox`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/inbox*.

* **Pfad zu gesendeten Elementen**

   (*Erforderlich*) Der Pfad relativ zum Knoten des Benutzers (/home/users/*username*), der für den **`send items`** Ordner verwendet werden soll. Der Pfad darf NICHT mit einem nachfolgenden Schrägstrich (/) enden. Der Standardwert ist */mail/sentitems* .

* **Unterstützungsanlagen**

   Wenn diese Option aktiviert ist, können Benutzer ihren Nachrichten Anlagen hinzufügen. Default is *checked*.

* **Aktivieren der Gruppennachrichten**

   Wenn diese Option aktiviert ist, können registrierte Benutzer eine Massennachricht an eine Gruppe von Mitgliedern senden. Die Option &quot;Standard&quot;ist *deaktiviert*.

* **Maximale Anzahl der Empfänger insgesamt**

   Wenn Gruppennachrichten aktiviert ist, geben Sie die maximale Anzahl von Empfängern an, an die eine Gruppennachricht gleichzeitig gesendet werden kann. Der Standardwert ist *100*.

* **Batch-Größe**

   Anzahl der Nachrichten, die zusammen für einen Senden gesendet werden, wenn sie an eine große Gruppe von Empfängern gesendet werden. Der Standardwert ist *100*.

* **Anlagengröße insgesamt**

   Wenn supportAttachments aktiviert ist, gibt dieser Wert die maximal zulässige Gesamtgröße (in Byte) aller Anlagen an. Default is *104857600* (100 MB).

* **blockierungsliste des Anlagentyps**

   Eine blockierungsliste von Dateinamenerweiterungen mit dem Präfix &quot;**.**&quot;, die vom System abgelehnt werden. Wenn kein auf die Blockierungsliste gesetzt wird, ist die Erweiterung zulässig. Erweiterungen können mit den Symbolen &#39;**+**&#39; und &#39;**-**&#39; hinzugefügt oder entfernt werden.

* **Zulässige Anlagentypen**

   **(*Aktion erforderlich*)** Eine zulassungsliste von Dateinamenerweiterungen im , das Gegenteil der blockierungsliste. Um alle Dateinamenerweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um den einzelnen leeren Eintrag zu entfernen.

* **Dienstauswahl**

   (*Erforderlich*) Ein absoluter Pfad (Endpunkt), über den der Dienst aufgerufen wird (eine virtuelle Ressource). Der Stamm des ausgewählten Pfads muss in der OSGi-Konfiguration für die *Ausführungspfade* enthalten sein [ wie `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`und `/apps/``/services/`. Um diese Konfiguration für die Messaging-Funktion einer Site auszuwählen, wird dieser Endpunkt als **`Service selector`** Wert für die `Message List and Compose Message components` (siehe [Nachrichtenfunktion](/help/communities/configure-messaging.md)) bereitgestellt.

   Die Standardeinstellung ist */bin/messaging* .

* **Zulassungsliste-**

   Verwenden Sie **die Zulassungsliste**&quot;Nachrichtenfelder&quot;.

>[!CAUTION]
>
>Jedes Mal, wenn eine `Messaging Operations Service` Konfiguration zur Bearbeitung geöffnet wird und sie entfernt `allowedAttachmentTypes.name` wurde, wird ein leerer Eintrag erneut hinzugefügt, damit die Eigenschaft konfiguriert werden kann. Ein einzelner leerer Eintrag deaktiviert Dateianlagen effektiv.
>
>Um alle Dateinamenerweiterungen mit Ausnahme der auf die Blockierungsliste gesetzt zuzulassen, verwenden Sie das Symbol &#39;**-**&#39;, um (erneut) den einzelnen leeren Eintrag zu entfernen, bevor Sie auf **Speichern** klicken.


## Group Messaging {#group-messaging}

Damit registrierte Benutzer Direktnachrichten stapelweise an Benutzergruppen senden können, müssen Sie sicherstellen, dass Sie in den beiden folgenden Instanzen der Konfiguration von **Messaging Operation Services** die Gruppennachrichten **** aktivieren:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Messaging-Dienst: Social Console**

![social-console-op-service](assets/social-console-op-service.png)

**Messaging-Dienst: Social Messaging**

![social-message-op-service](assets/social-message-op-service.png)

## Fehlerbehebung {#troubleshooting}

Eine Möglichkeit zur Fehlerbehebung besteht darin, [Debugging-Meldungen im Protokoll zu aktivieren.](/help/sites-administering/troubleshooting.md)

Siehe auch [Anmelder und Autoren für individuelle Services](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Das zu überwachende Paket ist `com.adobe.cq.social.messaging`.
