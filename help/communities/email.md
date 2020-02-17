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
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Konfigurieren der E-Mail {#configuring-email}

AEM Communities verwendet E-Mail für

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Standardmäßig funktioniert die E-Mail-Funktion nicht, da sie die Angabe eines SMTP-Servers und SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mail für Benachrichtigungen und Abonnements muss nur für den [primären Herausgeber](deploy-communities.md#primary-publisher)konfiguriert werden.

## Standardkonfiguration für den Mail-Dienst {#default-mail-service-configuration}

Der Standard-E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnements erforderlich.

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie die `Day CQ Mail Service`
* Wählen Sie das Bearbeitungssymbol

Dies basiert auf der Dokumentation zum [Konfigurieren der E-Mail-Benachrichtigung](../../help/sites-administering/notification.md), allerdings ist das Feld `"From" address`nicht ** erforderlich und sollte leer bleiben.

Beispiel (nur mit Werten zur Veranschaulichung gefüllt):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL Hostname]** des SMTP-Servers: *(Erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Serveranschluss]** *(erforderlich)* Der SMTP-Serveranschluss muss 25 oder höher sein.

* **[!UICONTROL SMTP-Benutzer]**: *(Erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**: *(erforderlich)* Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL Adresse]**&quot;Von&quot;: Leer lassen
* **[!UICONTROL SMTP verwenden SSL]**: Wenn diese Option aktiviert ist, wird sichere E-Mail gesendet. Stellen Sie sicher, dass der Anschluss auf 465 oder wie für den SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL Debug-E-Mail]**: Wenn diese Option aktiviert ist, wird die Protokollierung von SMTP-Serverinteraktionen aktiviert.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Sobald der [Standard-E-Mail-Dienst](#default-mail-service-configuration) konfiguriert ist, funktionieren die beiden in der Version enthaltenen Instanzen der `AEM Communities Email Reply Configuration` OSGi-Konfiguration.

Nur die Instanz für Abonnements muss weiter konfiguriert werden, wenn eine Antwort per E-Mail möglich ist.

1. ` [email](#configuration-for-notifications)` Veröffentlichungsinstanz

   für Benachrichtigungen, die keine Antwort-E-Mail unterstützen und nicht geändert werden sollten

1. ` [subscriptions-email](#configuration-for-subscriptions)` Veröffentlichungsinstanz

   Konfiguration erforderlich, um die Erstellung von Beiträgen aus Antwortemail vollständig zu aktivieren

So rufen Sie die Communities-E-Mail-Konfigurationsinstanzen auf:

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz der `AEM Communities Email Reply Configuration` OSGi-Konfiguration mit der E-Mail Name ist die Benachrichtigungsfunktion. Diese Funktion umfasst keine E-Mail-Antwort.

Diese Konfiguration sollte nicht geändert werden.

* Suchen Sie die `AEM Communities Email Reply Configuration`
* Wählen Sie das Bearbeitungssymbol
* Überprüfen Sie, ob der **Name**`email`

* Stellen Sie sicher, dass **Beitrag aus E-Mail** erstellen `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Konfiguration für Abonnements {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit zu aktivieren oder zu deaktivieren, dass ein Mitglied Inhalte per E-Mail posten kann.

* Suchen Sie die `AEM Communities Email Reply Configuration`
* Wählen Sie das Bearbeitungssymbol
* Überprüfen Sie, ob der **Name**`subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Name]** : *(erforderlich)*`subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail]** erstellen: Wenn diese Option aktiviert ist, kann der Empfänger der Abonnement-E-Mail Inhalte durch Senden einer Antwort posten. Diese Option ist standardmäßig aktiviert.
* **[!UICONTROL Verfolgte ID zur Kopfzeile]** hinzufügen:Der Standardwert ist `Reply-To`.

* **[!UICONTROL Höchstlänge des Betreffs]**: Wenn der Betreffzeile eine Tracker-ID hinzugefügt wird, ist dies die maximale Länge des Betreffs, mit Ausnahme der verfolgten ID, nach der sie abgeschnitten wird. Beachten Sie, dass dies so klein wie möglich sein sollte, damit verfolgte ID-Informationen nicht verloren gehen. Der Standardwert ist 200.
* **[!UICONTROL E-Mail-Adresse]**&quot;Von&quot;: *(Erforderlich)* Adresse, von der die Benachrichtigungs-E-Mail gesendet wird. Ist wahrscheinlich derselbe **SMTP-Benutzer** , der für den [Standard-E-Mail-Dienst](#configuredefaultmailservice)angegeben wurde. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Antwort-zu-Trennzeichen]**: Wenn die Tracker-ID der Antwort-zu-Kopfzeile hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist `+` (Pluszeichen).

* **[!UICONTROL Präfix der Tracker-ID im Betreff]**: Wenn der Betreffzeile eine Tracker-ID hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Verfolgungs-ID-Präfix im Nachrichtentext]**: Wenn dem Nachrichtentext eine Tracker-ID hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Wenn diese Option aktiviert ist, wird der Content-Type der E-Mail als `"text/html;charset=utf-8"`. Diese Option ist standardmäßig aktiviert.

* **[!UICONTROL Standardbenutzername]**: Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Stammpfad]** der Vorlagen: Die E-Mail wird mit einer Vorlage erstellt, die in diesem Stammpfad gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Importer konfigurieren {#configure-polling-importer}

Damit die E-Mail in das Repository geladen werden kann, müssen Sie einen Abrufimporteur konfigurieren und seine Eigenschaften im Repository manuell konfigurieren.

### Neuen Abruf-Importer hinzufügen {#add-new-polling-importer}

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Wechseln Sie zur Konsole des Abrufs-Importeurs. Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Hinzufügen **[!UICONTROL auswählen]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Typ]**: *(Erforderlich)* Ziehen Sie nach unten, um `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(Erforderlich)* Der ausgehende Mail-Server. Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Zu Pfad]**&amp;amp importieren;ast;: *(erforderlich)* Legen Sie &quot; `/content/usergenerated/mailFolder/postEmails`durch Navigieren zum `postEmails`Ordner auf&quot;fest und wählen Sie **OK**

* **[!UICONTROL Aktualisierungsintervall in Sekunden]**: *(optional)* Der für den Standard-E-Mail-Dienst konfigurierte E-Mail-Server kann Anforderungen hinsichtlich des Zeitintervalls für die Aktualisierung haben. So kann beispielsweise für Google Mail ein Intervall von `300`erforderlich sein.

* **[!UICONTROL Anmelden]**: *(optional)*

* **[!UICONTROL Kennwort]**: *(optional)*

* Wählen Sie **[!UICONTROL OK]** aus

### Protokoll für neuen Abruf-Importer anpassen {#adjust-protocol-for-new-polling-importer}

Nachdem die neue Abrufkonfiguration gespeichert wurde, müssen Sie die Eigenschaften des Abonnement-E-Mail-Importeurs weiter ändern, um das Protokoll von `POP3` in zu ändern `emailreply`

Using [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Im primären Herausgeber
* Mit Administratorrechten angemeldet
* Gehen Sie zu [https://&lt;server>: /crx/de/index.jsp#/etc/importing/polling.](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Wählen Sie die neu erstellte Konfiguration
* Ändern Sie die folgenden Eigenschaften

   * **feedType**: ersetzen `pop3s` durch **`emailreply`**
   * **source**: Quellprotokoll ersetzen `pop3s://` durch **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

Die roten Dreiecke geben die geänderten Eigenschaften an. Speichern Sie die Änderungen unbedingt:

* Select **[!UICONTROL Save All]**

