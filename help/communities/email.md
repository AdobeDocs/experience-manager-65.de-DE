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
ht-degree: 4%

---

# E-Mail konfigurieren {#configuring-email}

AEM Communities verwendet E-Mail für:

* [Communities-Benachrichtigungen](notifications.md)
* [Communities-Abonnements](subscriptions.md)

Die E-Mail-Funktion ist standardmäßig nicht funktionsfähig, da sie die Angabe eines SMTP-Servers und eines SMTP-Benutzers erfordert.

>[!CAUTION]
>
>E-Mails für Benachrichtigungen und Abonnements dürfen nur auf dem [primären Herausgeber“ konfiguriert ](deploy-communities.md#primary-publisher).

## Standardkonfiguration für den E-Mail-Dienst {#default-mail-service-configuration}

Der standardmäßige E-Mail-Dienst ist sowohl für Benachrichtigungen als auch für Abonnements erforderlich.

* Melden Sie sich beim primären Herausgeber mit Administratorberechtigung an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu:

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie die `Day CQ Mail Service`.
* Wählen Sie das Bearbeitungssymbol aus.

Dies basiert auf der Dokumentation zum [Konfigurieren von E-Mail](../../help/sites-administering/notification.md)Benachrichtigungen. Der Unterschied besteht jedoch darin, dass das Feld `"From" address` (*)* ist und leer gelassen werden sollte.

Beispiel (nur zur Veranschaulichung mit Werten ausgefüllt):

![email-config](assets/email-config.png)

* **[!UICONTROL SMTP-Server-Hostname]**

  *(Erforderlich)* Der zu verwendende SMTP-Server.

* **[!UICONTROL SMTP-Server-Port]**

  *(Erforderlich)* Der SMTP-Server-Port muss 25 oder höher sein.

* **[!UICONTROL SMTP-Benutzer]**

  *(Erforderlich)* Der SMTP-Benutzer.

* **[!UICONTROL SMTP-Kennwort]**

  *(Erforderlich)* Das Kennwort des SMTP-Benutzers.

* **[!UICONTROL „Von“-Adresse]**

  Leer lassen
* **[!UICONTROL SMTP - SSL verwenden]**

  Wenn diese Option aktiviert ist, wird eine sichere E-Mail gesendet. Stellen Sie sicher, dass der Port auf 465 oder wie für einen SMTP-Server erforderlich eingestellt ist.
* **[!UICONTROL E-Mail debuggen]**

  Wenn diese Option aktiviert ist, können SMTP-Server-Interaktionen protokolliert werden.

## AEM Communities-E-Mail-Konfiguration {#aem-communities-email-configuration}

Sobald der [Standard-E-](#default-mail-service-configuration)-Service) konfiguriert ist, werden die beiden vorhandenen Instanzen der `AEM Communities Email Reply Configuration` OSGi-Konfiguration, die in der Version enthalten sind, funktionsfähig.

Nur die Instanz für Abonnements muss weiter konfiguriert werden, wenn Antworten per E-Mail zugelassen werden.

1. [E-Mail](#configuration-for-notifications)-Instanz:

   Für Benachrichtigungen, die keine Antwort-E-Mails unterstützen und nicht geändert werden sollten.

1. [Subscriptions-email](#configuration-for-subscriptions)-Instanz:

   Erfordert eine Konfiguration, um das Erstellen von POST aus einer Antwort-E-Mail vollständig zu aktivieren.

So erreichen Sie die Instanzen der Communities-E-Mail-Konfiguration:

* Melden Sie sich beim primären Herausgeber mit Administratorberechtigung an und greifen Sie auf die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) zu

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie `AEM Communities Email Reply Configuration`.

![email-reply-config](assets/email-reply-config.png)

### Konfiguration für Benachrichtigungen {#configuration-for-notifications}

Die Instanz `AEM Communities Email Reply Configuration` OSGi-Konfiguration mit dem Namen email ist die Funktion forenotifications . Diese Funktion umfasst keine E-Mail-Antwort.

Ändern Sie diese Konfiguration nicht.

* Suchen Sie die `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Überprüfen Sie, ob **Name** `email` ist.

* Stellen Sie sicher **dass „Beitrag aus Antwort-E** Mail erstellen“ `unchecked` ist.

![configure-email-reply](assets/configure-email-reply.png)

### Konfiguration für Abonnements {#configuration-for-subscriptions}

Bei Communities-Abonnements ist es möglich, die Möglichkeit für ein Mitglied zu aktivieren oder zu deaktivieren, Inhalte zu veröffentlichen, indem es auf eine E-Mail antwortet.

* Suchen Sie die `AEM Communities Email Reply Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.
* Überprüfen Sie, ob **Name** `subscriptions-email` ist.

  ![configure-email-subscription](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

  *(erforderlich)* `subscriptions-email`. Nicht bearbeiten.

* **[!UICONTROL Beitrag aus Antwort-E-Mail erstellen]**

  Wenn diese Option aktiviert ist, kann der Empfänger einer Abonnement-E-Mail Inhalt posten, indem er eine Antwort sendet. Die Standardeinstellung ist aktiviert.
* **[!UICONTROL Verfolgte ID zur Kopfzeile hinzufügen]**

  Der Standardwert ist `Reply-To`.

* **[!UICONTROL Maximale Länge des Betreffs]**

  Wenn der Betreffzeile eine Tracker-ID hinzugefügt wird, ist dies die maximale Länge des Betreffs, mit Ausnahme der getrackten ID, nach der er gekürzt wird. Dieser sollte so klein wie möglich sein, um zu verhindern, dass getrackte ID-Informationen verloren gehen. Der Standardwert lautet 200.

* **[!UICONTROL E-Mail-Adresse „Antwort an“]**

  Adresse, die als Antwortadresse verwendet wird. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Trennzeichen für Antworten]**

  Wenn der Antwortkopfzeile eine Tracker-ID hinzugefügt wird, wird dieses Trennzeichen verwendet. Der Standardwert ist `+` (Pluszeichen).

* **[!UICONTROL Tracker-ID-Präfix im Betreff]**

  Wenn die Tracker-ID zur Betreffzeile hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `post#`.

* **[!UICONTROL Tracker-ID-Präfix im Nachrichtentext]**

  Wenn die Tracker-ID zum Nachrichtentext hinzugefügt wird, wird dieses Präfix verwendet. Der Standardwert ist `Please do not remove this:`.

* **[!UICONTROL E-Mail als HTML]**: Wenn diese Option aktiviert ist, wird der Inhaltstyp der E-Mail als `"text/html;charset=utf-8"` festgelegt. Die Standardeinstellung ist aktiviert.

* **[!UICONTROL Standardbenutzername]**

  Dieser Name wird für Benutzer ohne Namen verwendet. Der Standardwert ist `no-reply@example.com`.

* **[!UICONTROL Vorlagen-Stammpfad]**

  Die E-Mail wird mithilfe einer Vorlage erstellt, die unter diesem Stammpfad gespeichert ist. Der Standardwert ist `/etc/community/templates/subscriptions-email`.

## Abruf-Import-Tool konfigurieren {#configure-polling-importer}

Damit die E-Mail in das Repository importiert werden kann, muss ein Abruf-Import-Tool konfiguriert und seine Eigenschaften im Repository manuell konfiguriert werden.

### Neues Abruf-Import-Tool hinzufügen {#add-new-polling-importer}

* Melden Sie sich beim primären Herausgeber mit Administratorberechtigung an und wechseln Sie zur Konsole des Abruf-Importtools:

  Beispiel: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Wählen Sie **[!UICONTROL Hinzufügen]** aus

  ![polling-importer](assets/polling-importer.png)

* **[!UICONTROL Typ]**

  *(Erforderlich)* Pulldown zur Auswahl von `POP3 (over SSL)`.

* **[!UICONTROL URL]**

  *(Erforderlich)* Der Postausgangsserver. Zum Beispiel: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`.

* **[!UICONTROL In Pfad importieren]**&amp;ast;

  *(Erforderlich)* Auf `/content/usergenerated/mailFolder/postEmails` festgelegt
Navigieren Sie zum Ordner `postEmails` und wählen Sie **OK** aus.

* **[!UICONTROL Aktualisierungsintervall in Sekunden]**

  *(Optional)* Der für den Standard-E-Mail-Service konfigurierte E-Mail-Server kann Anforderungen an den Wert für das Aktualisierungsintervall haben. Für Gmail kann beispielsweise ein Intervall von `300` erforderlich sein.

* **[!UICONTROL Anmelden]**

  *(optional)*

* **[!UICONTROL Kennwort]**

  *(optional)*

* Wählen Sie **[!UICONTROL OK]** aus.

### Protokoll für neuen Abruf-Importer anpassen {#adjust-protocol-for-new-polling-importer}

Nachdem die neue Abrufkonfiguration gespeichert wurde, müssen die Eigenschaften des Abonnement-E-Mail-Importtools weiter geändert werden, um das Protokoll von `POP3` in `emailreply` zu ändern.

Verwendet [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Melden Sie sich beim primären Herausgeber mit Administratorberechtigung an und navigieren Sie zu [https://&lt;Server>:&lt;Port>/crx/de/index.jsp#/etc/importers/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling).
* Wählen Sie die neu erstellte Konfiguration aus und ändern Sie die folgenden Eigenschaften:

   * **feedType**: Ersetzen Sie `pop3s` durch **`emailreply`**
   * **source**: Ersetzen Sie die `pop3s://` der Quelle durch **`emailreply://`**

![polling-protocol](assets/polling-protocol.png)

Die roten Dreiecke zeigen die geänderten Eigenschaften an. Denken Sie daran, die Änderungen zu speichern:

* Klicken Sie auf **[!UICONTROL Alle speichern]**.
