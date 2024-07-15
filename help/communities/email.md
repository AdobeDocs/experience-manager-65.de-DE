---
title: E-Mail konfigurieren
description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen und -Abonnements für Adobe Experience Manager Communities konfigurieren.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
pagetitle: Configuring Email
role: Admin
exl-id: bf97d388-f8ca-4e37-88e2-0c536834311e
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 3%

---

# E-Mail konfigurieren {#configuring-email}

AEM Communities verwendet E-Mail für:

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Standardmäßig ist die E-Mail-Funktion nicht funktionsfähig, da sie die Spezifikation eines SMTP-Servers und SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mail für Benachrichtigungen und Abonnements darf nur für den [primären Herausgeber](deploy-communities.md#primary-publisher) konfiguriert werden.

## Standard-E-Mail-Dienstkonfiguration {#default-mail-service-configuration}

Der Standard-E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnements erforderlich.

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu:

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie den `Day CQ Mail Service`.
* Wählen Sie das Bearbeitungssymbol aus.

Dies basiert auf der Dokumentation für [Konfigurieren der E-Mail-Benachrichtigung](../../help/sites-administering/notification.md), allerdings mit einem Unterschied, dass das Feld `"From" address` den Wert *nicht* aufweist und leer gelassen werden sollte.

Beispiel: (nur zu Veranschaulichungszwecken mit Werten gefüllt):

![email-config](assets/email-config.png)

* **[!UICONTROL SMTP-Server-Hostname]**

  *(Erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Server-Port]**

  *(Erforderlich)* Der SMTP-Server-Port muss 25 oder höher sein.

* **[!UICONTROL SMTP-Benutzer]**

  *(Erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**

  *(Erforderlich)* Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL &quot;From&quot; address]**

  Leer lassen
* **[!UICONTROL SMTP verwenden SSL]**

  Wenn diese Option aktiviert ist, wird eine sichere E-Mail gesendet. Stellen Sie sicher, dass der Port auf 465 oder wie für einen SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL E-Mail debuggen]**

  Wenn diese Option aktiviert ist, ermöglicht dies die Protokollierung von SMTP-Serverinteraktionen.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Sobald der [Standard-E-Mail-Dienst](#default-mail-service-configuration) konfiguriert ist, funktionieren die beiden vorhandenen Instanzen der in der Version enthaltenen `AEM Communities Email Reply Configuration` OSGi-Konfiguration.

Nur die Instanz für Abonnements muss weiter konfiguriert werden, wenn E-Mail-Antworten zugelassen werden.

1. Instanz [E-Mail](#configuration-for-notifications) :

   Bei Benachrichtigungen, die keine Antwort-E-Mail unterstützen und nicht geändert werden sollten.

1. Instanz [Abonnements-email](#configuration-for-subscriptions) :

   Erfordert eine Konfiguration, um die Erstellung von Beiträgen aus einer Antwort-E-Mail vollständig zu aktivieren.

So greifen Sie auf die Communities-E-Mail-Konfigurationsinstanzen zu:

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie `AEM Communities Email Reply Configuration`.

![email-response-config](assets/email-reply-config.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz der OSGi-Konfiguration `AEM Communities Email Reply Configuration` mit der E-Mail-Adresse Name ist die Funktion für Benachrichtigungen. Diese Funktion enthält keine E-Mail-Antwort.

Ändern Sie diese Konfiguration nicht.

* Suchen Sie den `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass der **Name** `email` ist.

* Stellen Sie sicher, dass **Beitrag aus Antwort-E-Mail erstellen** `unchecked` ist.

![configure-email-response](assets/configure-email-reply.png)

### Konfiguration für Abonnements {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit für ein Mitglied zu aktivieren oder zu deaktivieren, Inhalte zu posten, indem es auf eine E-Mail antwortet.

* Suchen Sie den `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass der **Name** `subscriptions-email` ist.

  ![configure-email-subscription](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

  *(Erforderlich)* `subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail erstellen]**

  Wenn diese Option aktiviert ist, kann der Empfänger einer Abonnement-E-Mail Inhalte durch Senden einer Antwort posten. Die Option Standard ist aktiviert.
* **[!UICONTROL Hinzufügen der getrackten ID zur Kopfzeile]**

  Der Standardwert ist `Reply-To`.

* **[!UICONTROL Maximale Länge des Betreffs]**

  Wenn die Tracker-ID zur Betreffzeile hinzugefügt wird, ist dies die maximale Länge des Betreffs, ausgenommen die verfolgte ID, nach der sie abgeschnitten wird. Dies sollte so klein wie möglich sein, um zu verhindern, dass getrackte ID-Informationen verloren gehen. Der Standardwert lautet 200.

* **[!UICONTROL &quot;Antwort-auf&quot; E-Mail-Adresse]**

  Adresse, die als &quot;Antwort&quot;-E-Mail-Adresse verwendet wird. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Antwort an Trennzeichen]**

  Wenn die Tracker-ID zur Kopfzeile Antwort hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist &quot;`+`&quot;(Pluszeichen).

* **[!UICONTROL Präfix der Tracker-ID im Betreff]**

  Wenn die Tracker-ID der Betreffzeile hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Präfix der Tracker-ID im Nachrichtentext]**

  Wenn die Tracker-ID zum Nachrichtentext hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Ist diese Option aktiviert, wird der Inhaltstyp der E-Mail auf `"text/html;charset=utf-8"` gesetzt. Die Option Standard ist aktiviert.

* **[!UICONTROL Standardbenutzername]**

  Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Stammpfad der Vorlagen]**

  Die E-Mail wird mithilfe einer Vorlage erstellt, die in diesem Stammverzeichnis gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Importtool konfigurieren {#configure-polling-importer}

Damit die E-Mail in das Repository geladen werden kann, muss ein Abruf-Importtool konfiguriert und die Eigenschaften im Repository manuell konfiguriert werden.

### Neuen Abruf-Importtool hinzufügen {#add-new-polling-importer}

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und navigieren Sie zur Abruf-Importtool-Konsole:

  Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Wählen Sie **[!UICONTROL Hinzufügen]**

  ![olling-importer](assets/polling-importer.png)

* **[!UICONTROL Typ]**

  *(Erforderlich)* Pulldown zum Auswählen `POP3 (over SSL)`.

* **[!UICONTROL URL]**

  *(Erforderlich)* Der ausgehende Mail-Server. Zum Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`.

* **[!UICONTROL Import to Path]**&amp;ast;

  *(Erforderlich)* Auf `/content/usergenerated/mailFolder/postEmails` setzen
indem Sie zum Ordner `postEmails`navigieren und **OK** auswählen.

* **[!UICONTROL Intervall in Sekunden aktualisieren]**

  *(Optional)* Der für den Standard-E-Mail-Dienst konfigurierte Mailserver kann Anforderungen hinsichtlich des Aktualisierungsintervallwerts haben. Gmail erfordert beispielsweise möglicherweise ein Intervall von `300`.

* **[!UICONTROL Anmelden]**

  *(Optional)*

* **[!UICONTROL Kennwort]**

  *(Optional)*

* Wählen Sie **[!UICONTROL OK]** aus.

### Anpassen des Protokolls für den neuen Abruf-Importtool {#adjust-protocol-for-new-polling-importer}

Nachdem die neue Abruffunktion gespeichert wurde, müssen die Eigenschaften des E-Mail-Importtools für Abonnements weiter geändert werden, um das Protokoll von `POP3` in `emailreply` zu ändern.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Melden Sie sich mit Administratorberechtigungen beim primären Herausgeber an und navigieren Sie zu &quot;[https://&lt;Server>:&lt;Port>/crx/de/index.jsp#/etc/importers/olling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)&quot;.
* Wählen Sie die neu erstellte Konfiguration aus und ändern Sie die folgenden Eigenschaften:

   * **feedType**: Ersetzen Sie `pop3s` durch **`emailreply`**
   * **source**: Ersetzen Sie das Quellprotokoll `pop3s://` durch **`emailreply://`**

![Polling-protocol](assets/polling-protocol.png)

Die roten Dreiecke geben die geänderten Eigenschaften an. Achten Sie darauf, die Änderungen zu speichern:

* Klicken Sie auf **[!UICONTROL Alle speichern]**.
