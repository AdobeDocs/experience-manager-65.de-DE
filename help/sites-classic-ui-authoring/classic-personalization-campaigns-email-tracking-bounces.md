---
title: Nachverfolgen nicht zugestellter E-Mails
seo-title: Nachverfolgen nicht zugestellter E-Mails
description: Wenn Sie einen Newsletter an viele Benutzer senden, sind in der Liste im Allgemeinen einige ungültige E-Mail-Adressen enthalten. Newsletter, die an diese Adressen gesendet werden, können nicht zugestellt werden. AEM kann diese nicht zugestellten E-Mails verwalten und den Versand von Newslettern an diese Adressen einstellen, wenn die festgelegte Anzahl nicht erfolgreicher Zustellversuche überschritten wird.
seo-description: Wenn Sie einen Newsletter an viele Benutzer senden, sind in der Liste im Allgemeinen einige ungültige E-Mail-Adressen enthalten. Newsletter, die an diese Adressen gesendet werden, können nicht zugestellt werden. AEM kann diese nicht zugestellten E-Mails verwalten und den Versand von Newslettern an diese Adressen einstellen, wenn die festgelegte Anzahl nicht erfolgreicher Zustellversuche überschritten wird.
uuid: 749959f2-e6f8-465f-9675-132464c65f11
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: fde9027b-9057-48c3-ae34-3f3258c5b371
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Nachverfolgen nicht zugestellter E-Mails{#tracking-bounced-emails}

>[!NOTE]
>
>Adobe plant nicht, die Verfolgung von durch den AEM SMTP-Dienst gesendeten/abgeschnittenen E-Mails weiter zu verbessern.
>
>Es wird empfohlen, Adobe Campaign und seine AEM-Integration [zu nutzen](/help/sites-administering/campaign.md).

Wenn Sie einen Newsletter an viele Benutzer senden, sind in der Liste im Allgemeinen einige ungültige E-Mail-Adressen enthalten. Newsletter, die an diese Adressen gesendet werden, können nicht zugestellt werden. AEM kann diese nicht zugestellten E-Mails verwalten und den Versand von Newslettern an diese Adressen einstellen, wenn die festgelegte Anzahl nicht erfolgreicher Zustellversuche überschritten wird. Der Standardwert für fehlgeschlagene Zustellversuche beträgt 3, er kann jedoch angepasst werden.

Wenn Sie AEM so einrichten möchten, dass nicht zugestellte E-Mails nachverfolgt werden, müssen Sie festlegen, dass AEM vorhandene Postfächer abfragt, an die E-Mails nicht zugestellt werden können (im Allgemeinen handelt es sich dabei um die E-Mail-Adresse, die Sie für den Versand des Newsletters angegeben haben). AEM fragt diesen Posteingang ab und importiert alle E-Mails in das in den Abrufeinstellungen festgelegte Verzeichnis. Anschließend wird ein Arbeitsablauf ausgelöst, um nach den abgeschnittenen E-Mail-Adressen innerhalb der Benutzer zu suchen und den Wert der Eigenschaft &quot;bounceCounter&quot;des Benutzers entsprechend zu aktualisieren. Wenn der festgelegte Maximalwert für fehlgeschlagene Zustellversuche überschritten wird, wird der Benutzer aus der Newsletter-Liste gelöscht.

## Konfigurieren des Feed Importers {#configuring-the-feed-importer}

Mit dem Feed Importer können Sie wiederholt Inhalte aus externen Quellen in Ihr Repository importieren. Bei dieser Konfiguration des Feed Importers prüft AEM den Posteingang des Absenders auf nicht zugestellte E-Mails.

So konfigurieren Sie den Feed Importer für das Nachverfolgen nicht zugestellter E-Mails:

1. Wählen Sie unter **Tools** die Option „Feed Importer“.

1. Klicken Sie auf **Hinzufügen**, um eine neue Konfiguration zu erstellen.

   ![chlimage_1](assets/chlimage_1a.png)

1. Fügen Sie eine neue Konfiguration hinzu, indem Sie den Typ wählen und Informationen zur Abruf-URL angeben, um so den Host und den Port zu konfigurieren. Außerdem müssen Sie der URL-Abfrage einige Mail- und Protokoll-spezifische Parameter hinzufügen. Richten Sie die Konfiguration so ein, dass der Abruf mindestens einmal pro Tag erfolgt.

   Sämtliche Konfigurationen benötigen in der Abruf-URL Informationen zu folgenden Bereichen:

   `username`: Der Benutzername für die Verbindung

   `password`: Das Kennwort für die Verbindung

   Außerdem können Sie je nach Protokoll bestimmte Einstellungen konfigurieren.

   **Eigenschaften der POP3-Konfiguration:**

   `pop3.leave.on.server`: Definiert, ob Meldungen auf dem Server bleiben sollen. Wählen Sie „true“, wenn Nachrichten auf dem Server bleiben sollen, bzw. „false“, wenn dies nicht der Fall sein soll. Der Standardwert ist „true“.

   **POP3-Beispiele:**

   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret | Verwendung von pop3 über SSL, um an Port 995 eine Verbindung zu GMail mit dem Konto user/secret herzustellen, Nachrichten bleiben standardmäßig auf dem Server |
   |---|---|
   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false |

   **Eigenschaften der IMAP-Konfiguration:**

   Bietet Ihnen die Möglichkeit, Kennzeichnungen zu setzen, nach denen Sie suchen können. 

   `imap.flag.SEEN`:Wählen Sie „false“ für eine neue/nicht gelesene Nachricht und „true“ für bereits gelesene Nachrichten

   See [https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html](https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html) for the full list of flags.

   **IMAP-Beispiele:**

   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret | Verwendung von IMAP über SSL, um an Port 993 eine Verbindung zu GMail mit dem Konto user/secret herzustellen. Standardmäßig werden nur neue Nachrichten empfangen. |
   |---|---|
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true | Verwendung von IMAP über SSL, um an Port 993 eine Verbindung zu GMail mit dem Konto user/secret herzustellen. Es werden nur bereits gelesene Nachrichten abgerufen. |
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true&amp;imap.flag.SEEN=false | Verwendung von IMAP über SSL, um an Port 993 eine Verbindung zu GMail mit dem Konto user/secret herzustellen. Es werden bereits gelesene ODER neue Nachrichten abgerufen. |

1. Speichern Sie die Konfiguration.

## Konfigurieren der Newsletter-Dienstkomponente {#configuring-the-newsletter-service-component}

Nachdem Sie den Feed Importer konfiguriert haben, müssen Sie die Absenderadresse und den Zähler für nicht erfolgreiche Zustellversuche konfigurieren.

So konfigurieren Sie den Newsletter-Dienst:

1. In the OSGi console at `<host>:<port>/system/console/configMgr` and navigate to **MCM Newsletter**.

1. Konfigurieren Sie den Dienst und speichern Sie anschließend die Änderungen.

   ![chlimage_1-1](assets/chlimage_1-1a.png)

   Die folgenden Konfigurationen können angepasst werden:

   | Bounce Counter Maximum (max.bounce.count) | Bestimmt, nach wie vielen erfolglosen Zustellversuchen ein Benutzer beim Versand eines Newsletters nicht mehr berücksichtigt wird. Wenn Sie diesen Wert auf 0 einstellen, wird die Prüfung erfolgloser Zustellversuche komplett deaktiviert. |
   |---|---|
   | Activity No Cache (sent.activity.nocache) | Definiert die Cache-Einstellung, die für die Aktivität „Newsletter gesendet“ verwendet werden soll |

   Nach dem Speichern führt der Newsletter-MCM-Dienst die folgenden Funktionen aus:

   * Schreibt nach dem erfolgreichen Versand eines Newsletters eine Aktivität in den verborgenen Stream des Benutzers.
   * Schreibt eine Aktivität, wenn eine nicht zugestellte Nachricht ermittelt wird und die Anzahl der nicht zugestellten Nachrichten für einen Benutzer sich ändert.
