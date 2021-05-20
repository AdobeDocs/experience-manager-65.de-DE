---
title: E-Mail konfigurieren
seo-title: E-Mail konfigurieren
description: E-Mail-Konfiguration für Communities
seo-description: E-Mail-Konfiguration für Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Administrator
exl-id: bf97d388-f8ca-4e37-88e2-0c536834311e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 7%

---

# Konfigurieren von E-Mail {#configuring-email}

AEM Communities verwendet E-Mail für:

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Standardmäßig ist die E-Mail-Funktion nicht funktionsfähig, da sie die Spezifikation eines SMTP-Servers und SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mail für Benachrichtigungen und Abonnements darf nur für den [primären Herausgeber](deploy-communities.md#primary-publisher) konfiguriert werden.

## Standard-Mail-Dienstkonfiguration {#default-mail-service-configuration}

Der Standard-E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnements erforderlich.

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu:

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie nach `Day CQ Mail Service`.
* Wählen Sie das Bearbeitungssymbol aus.

Dies basiert auf der Dokumentation für [Konfigurieren der E-Mail-Benachrichtigung](../../help/sites-administering/notification.md), allerdings mit einem Unterschied, dass das Feld `"From" address` *nicht* erforderlich ist und leer bleiben sollte.

Beispiel: (nur zu Veranschaulichungszwecken mit Werten gefüllt):

![email-config](assets/email-config.png)

* **[!UICONTROL Hostname des SMTP-Servers]**

   *(Erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Server-Anschluss]**

   *(Erforderlich)* Der SMTP-Server-Port muss mindestens 25 betragen.

* **[!UICONTROL SMTP-Benutzer]**

   *(Erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**

   *(Erforderlich)* Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL &quot;Von&quot;-Adresse]**

   Leer lassen
* **[!UICONTROL SMTP SSL verwenden]**

   Wenn diese Option aktiviert ist, wird sichere E-Mail gesendet. Stellen Sie sicher, dass der Port auf 465 oder wie für den SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL Debug-E-Mail]**

   Ist diese Option aktiviert, wird die Protokollierung von SMTP-Serverinteraktionen aktiviert.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Sobald der [Standard-E-Mail-Dienst](#default-mail-service-configuration) konfiguriert ist, funktionieren die beiden vorhandenen Instanzen der `AEM Communities Email Reply Configuration`-OSGi-Konfiguration, die in der Version enthalten ist, weiter.

Nur die Instanz für Abonnements muss weiter konfiguriert werden, wenn E-Mail-Antworten zugelassen werden.

1. [](#configuration-for-notifications) Emailinstanz:

   Bei Benachrichtigungen, die keine Antwort-E-Mail unterstützen und nicht geändert werden sollten.

1. [Subscriptions-](#configuration-for-subscriptions) emailinstance:

   Erfordert eine Konfiguration, um die Erstellung von Beiträgen aus einer Antwort-E-Mail vollständig zu aktivieren.

So greifen Sie auf die Communities-E-Mail-Konfigurationsinstanzen zu:

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu.

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie `AEM Communities Email Reply Configuration`.

![email-response-config](assets/email-reply-config.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz der OSGi-Konfiguration `AEM Communities Email Reply Configuration` mit der E-Mail-Adresse Name ist die Funktion für Benachrichtigungen. Diese Funktion enthält keine E-Mail-Antwort.

Diese Konfiguration sollte nicht geändert werden.

* Suchen Sie nach `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass **Name** `email` ist.

* Stellen Sie sicher, dass **Beitrag aus Antwort-E-Mail erstellen** `unchecked` ist.

![configure-email-response](assets/configure-email-reply.png)

### Konfiguration für Abonnements {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit für ein Mitglied zu aktivieren oder zu deaktivieren, Inhalte zu posten, indem es auf eine E-Mail antwortet.

* Suchen Sie nach `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Stellen Sie sicher, dass **Name** `subscriptions-email` ist.

   ![configure-email-subscription](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

   *(Erforderlich)* `subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail erstellen]**

   Wenn diese Option aktiviert ist, kann der Empfänger der Abonnement-E-Mail Inhalte durch Senden einer Antwort posten. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Getrackte ID zur Kopfzeile hinzufügen]**

   Der Standardwert ist `Reply-To`.

* **[!UICONTROL Maximale Länge des Betreffs]**

   Wenn die Tracker-ID zur Betreffzeile hinzugefügt wird, ist dies die maximale Länge des Betreffs, ausgenommen die verfolgte ID, nach der sie abgeschnitten wird. Beachten Sie, dass dies so klein wie möglich sein sollte, um zu verhindern, dass getrackte ID-Informationen verloren gehen. Der Standardwert ist 200.

* **[!UICONTROL E-Mail-Adresse &quot;Antwort an&quot;]**

   Adresse, die als E-Mail-Adresse &quot;Antwort&quot; verwendet wird. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Antwort an Trennzeichen]**

   Wenn die Tracker-ID zur Kopfzeile Antwort hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist `+` (Pluszeichen).

* **[!UICONTROL Tracker-ID-Präfix im Betreff]**

   Wenn die Tracker-ID der Betreffzeile hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Tracker-ID-Präfix im Nachrichtentext]**

   Wenn die Tracker-ID zum Nachrichtentext hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Wenn diese Option aktiviert ist, wird der Inhaltstyp der E-Mail auf  `"text/html;charset=utf-8"` gesetzt. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Standardbenutzername]**

   Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Vorlagen-Stammpfad]**

   Die E-Mail wird mithilfe der Vorlage erstellt, die in diesem Stammverzeichnis gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Importtool konfigurieren {#configure-polling-importer}

Damit die E-Mail in das Repository geladen werden kann, muss ein Abruf-Importtool konfiguriert und die Eigenschaften im Repository manuell konfiguriert werden.

### Hinzufügen eines neuen Abruf-Importtools {#add-new-polling-importer}

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und navigieren Sie zur Abruf-Importtool-Konsole:

   Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Wählen Sie **[!UICONTROL Hinzufügen]**

   ![olling-importer](assets/polling-importer.png)

* **[!UICONTROL Typ]**

   *(Erforderlich)* Pulldown zum Auswählen  `POP3 (over SSL)`.

* **[!UICONTROL URL]**

   *(Erforderlich)* Der ausgehende Mail-Server. Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`.

* **[!UICONTROL Import in Pfad]**&amp;ast;

   *(Erforderlich)* Legen Sie diese Einstellung  `/content/usergenerated/mailFolder/postEmails`
fest, indem Sie zum  `postEmails`Ordner navigieren und  **OK** auswählen.

* **[!UICONTROL Intervall in Sekunden aktualisieren]**

   *(Optional)* Der für den Standard-E-Mail-Dienst konfigurierte Mailserver kann Anforderungen in Bezug auf den Wert des Aktualisierungsintervalls haben. Gmail erfordert beispielsweise möglicherweise ein Intervall von `300`.

* **[!UICONTROL Anmeldung]**

   *(Optional)*

* **[!UICONTROL Kennwort]**

   *(Optional)*

* Wählen Sie **[!UICONTROL OK]** aus.

### Anpassen des Protokolls für den neuen Abruf-Importtool {#adjust-protocol-for-new-polling-importer}

Nachdem die neue Abruffunktion gespeichert wurde, müssen die Eigenschaften des E-Mail-Importtools für Abonnements weiter geändert werden, um das Protokoll von `POP3` in `emailreply` zu ändern.

Verwenden von [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Melden Sie sich mit Administratorrechten beim primären Herausgeber an und navigieren Sie zu [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/poling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling).
* Wählen Sie die neu erstellte Konfiguration aus und ändern Sie die folgenden Eigenschaften:

   * **feedType**: Ersetzen  `pop3s` durch  **`emailreply`**
   * **source**: Quellprotokoll ersetzen  `pop3s://` durch  **`emailreply://`**

![Polling-Protokoll](assets/polling-protocol.png)

Die roten Dreiecke geben die geänderten Eigenschaften an. Achten Sie darauf, die Änderungen zu speichern:

* Wählen Sie **[!UICONTROL Alle speichern]** aus.
