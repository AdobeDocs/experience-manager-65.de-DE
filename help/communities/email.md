---
title: Konfigurieren der E-Mail
seo-title: Konfigurieren der E-Mail
description: E-Mail-Konfiguration für Communities
seo-description: E-Mail-Konfiguration für Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 7%

---


# Konfigurieren der E-Mail {#configuring-email}

AEM Communities verwendet E-Mail für:

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Standardmäßig funktioniert die E-Mail-Funktion nicht, da sie die Angabe eines SMTP-Servers und SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mail für Benachrichtigungen und Abonnement muss nur für den [primären Herausgeber](deploy-communities.md#primary-publisher) konfiguriert werden.

## Standard-Mail-Dienstkonfiguration {#default-mail-service-configuration}

Der Standard-E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnement erforderlich.

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu:

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie nach `Day CQ Mail Service`.
* Wählen Sie das Bearbeitungssymbol aus.

Dies basiert auf der Dokumentation für [Konfigurieren der E-Mail-Benachrichtigung](../../help/sites-administering/notification.md), jedoch mit einem Unterschied, dass das Feld `"From" address` *nicht* erforderlich ist und leer bleiben sollte.

Beispiel (nur mit Werten zur Veranschaulichung gefüllt):

![email-config](assets/email-config.png)

* **[!UICONTROL Hostname des SMTP-Servers]**

   *(Erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Serveranschluss]**

   *(Erforderlich)*  Der SMTP-Serveranschluss muss mindestens 25 betragen.

* **[!UICONTROL SMTP-Benutzer]**

   *(Erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**

   *(Erforderlich)*  Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL &quot;Von&quot;-Adresse]**

   Leer lassen
* **[!UICONTROL SMTP mit SSL]**

   Wenn diese Option aktiviert ist, wird sichere E-Mail gesendet. Stellen Sie sicher, dass der Anschluss auf 465 oder wie für den SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL Debug-E-Mail]**

   Wenn diese Option aktiviert ist, wird die Protokollierung von SMTP-Serverinteraktionen aktiviert.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Sobald der [Standard-E-Mail-Dienst](#default-mail-service-configuration) konfiguriert ist, funktionieren die beiden vorhandenen Instanzen der in der Version enthaltenen OSGi-Konfiguration.`AEM Communities Email Reply Configuration`

Nur die Instanz für Abonnement muss weiter konfiguriert werden, wenn eine Antwort per E-Mail zulässig ist.

1. [](#configuration-for-notifications) Botschaft:

   Bei Benachrichtigungen, die keine Antwort-E-Mail unterstützen und nicht geändert werden sollten.

1. [Abonnements-](#configuration-for-subscriptions) emailinstance:

   Erfordert eine Konfiguration, um die Erstellung eines Beitrags aus einer Antwort-E-Mail vollständig zu aktivieren.

So rufen Sie die Communities-E-Mail-Konfigurationsinstanzen auf:

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie nach `AEM Communities Email Reply Configuration`.

![email-response-config](assets/email-reply-config.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz von `AEM Communities Email Reply Configuration` OSGi config mit der E-Mail &quot;Name&quot;ist die Benachrichtigungsfunktion. Diese Funktion umfasst keine E-Mail-Antwort.

Diese Konfiguration sollte nicht geändert werden.

* Suchen Sie nach `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass **Name** `email` ist.

* Stellen Sie sicher, dass **Beitrag aus Antwort-E-Mail erstellen** `unchecked` ist.

![configure-email-response](assets/configure-email-reply.png)

### Konfiguration für Abonnement {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit zu aktivieren oder zu deaktivieren, dass ein Mitglied Inhalte per E-Mail posten kann.

* Suchen Sie nach `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass **Name** `subscriptions-email` ist.

   ![configure-email-Abonnement](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

   *(Erforderlich)* `subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail erstellen]**

   Wenn diese Option aktiviert ist, kann der Empfänger der Abonnement-E-Mail Inhalte veröffentlichen, indem er eine Antwort sendet. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL hinzufügen verfolgt ID in Kopfzeile]**

   Der Standardwert ist `Reply-To`.

* **[!UICONTROL Maximale Länge des Betreffs]**

   Wenn der Betreffzeile eine Tracker-ID hinzugefügt wird, ist dies die maximale Länge des Betreffs, mit Ausnahme der verfolgten ID, nach der sie abgeschnitten wird. Beachten Sie, dass dies so klein wie möglich sein sollte, damit verfolgte ID-Informationen nicht verloren gehen. Der Standardwert ist 200.

* **[!UICONTROL E-Mail-Adresse &quot;Antwort an&quot;]**

   Adresse, die als E-Mail-Adresse für Antworten verwendet wird. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Antwort-zu-Trennzeichen]**

   Wenn die Tracker-ID der Antwort-zu-Kopfzeile hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist `+` (Pluszeichen).

* **[!UICONTROL Präfix der Tracker-ID im Betreff]**

   Wenn der Betreffzeile eine Tracker-ID hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Präfix der Tracker-ID im Nachrichtentext]**

   Wenn dem Nachrichtentext eine Tracker-ID hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Wenn diese Option aktiviert ist, wird der Content-Type der E-Mail als  `"text/html;charset=utf-8"`. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Standardbenutzername]**

   Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Stammpfad der Vorlagen]**

   Die E-Mail wird mithilfe der Vorlage erstellt, die in diesem Stammverzeichnis gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Importer {#configure-polling-importer} konfigurieren

Damit die E-Mail in das Repository geladen werden kann, müssen Sie einen Abrufimporteur konfigurieren und seine Eigenschaften im Repository manuell konfigurieren.

### hinzufügen neuer Abruf-Importer {#add-new-polling-importer}

* Melden Sie sich mit Administratorberechtigungen beim primären Herausgeber an und navigieren Sie zur Abstimmungs-Importer-Konsole:

   Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Wählen Sie **[!UICONTROL Hinzufügen]**

   ![Abruferzeuger](assets/polling-importer.png)

* **[!UICONTROL Typ]**

   *(Erforderlich)* Ziehen Sie zur Auswahl nach unten  `POP3 (over SSL)`.

* **[!UICONTROL URL]**

   *(Erforderlich)* Der ausgehende E-Mail-Server. Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`.

* **[!UICONTROL In Pfad]**&amp;Vergangenheit importieren;

   *(Erforderlich)* Legen Sie die Einstellung  `/content/usergenerated/mailFolder/postEmails`
fest, indem Sie zum  `postEmails`Ordner navigieren und  **OK** wählen.

* **[!UICONTROL Intervall in Sekunden aktualisieren]**

   *(Optional)* Der für den Standard-E-Mail-Dienst konfigurierte E-Mail-Server verfügt möglicherweise über Anforderungen hinsichtlich des Zeitintervalls für die Aktualisierung. Beispielsweise kann für Gmail ein Intervall von `300` erforderlich sein.

* **[!UICONTROL Anmeldung]**

   *(Optional)*

* **[!UICONTROL Kennwort]**

   *(Optional)*

* Wählen Sie **[!UICONTROL OK]** aus.

### Anpassen des Protokolls für den neuen Abruf-Importer {#adjust-protocol-for-new-polling-importer}

Nach dem Speichern der neuen Abrufkonfiguration müssen Sie die Eigenschaften des Abonnement-E-Mail-Importeurs weiter ändern, um das Protokoll von `POP3` in `emailreply` zu ändern.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importing/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling).
* Wählen Sie die neu erstellte Konfiguration aus und ändern Sie die folgenden Eigenschaften:

   * **feedType**: Ersetzen  `pop3s` durch  **`emailreply`**
   * **source**: Quellprotokoll ersetzen  `pop3s://` durch  **`emailreply://`**

![Polling-Protokoll](assets/polling-protocol.png)

Die roten Dreiecke geben die geänderten Eigenschaften an. Speichern Sie die Änderungen unbedingt:

* Wählen Sie **[!UICONTROL Alle speichern]**.

