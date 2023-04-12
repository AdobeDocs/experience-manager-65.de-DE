---
title: Nachverfolgen nicht zugestellter E-Mails
seo-title: Tracking Bounced Emails
description: Wenn Sie einen Newsletter an viele Benutzer senden, sind in der Liste im Allgemeinen einige ungültige E-Mail-Adressen enthalten. Newsletter, die an diese Adressen gesendet werden, können nicht zugestellt werden. AEM können diese Bounces verwalten und den Versand von Newslettern an diese Adressen einstellen, nachdem der konfigurierte Bounce-Zähler überschritten wurde.
seo-description: When you send a newsletter to many users, there are usually some invalid emails addresses in the list. Sending newsletters to those addresses bounce back. AEM is capable of managing those bounces and can stop sending newsletters to those addresses after the configured bounce counter is exceeded.
uuid: 749959f2-e6f8-465f-9675-132464c65f11
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: fde9027b-9057-48c3-ae34-3f3258c5b371
exl-id: 6cda0a68-0df9-44e7-ae4f-9951411af6dd
source-git-commit: e05f6cd7cf17f4420176cf76f28cb469bcee4a0a
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 28%

---

# Nachverfolgen nicht zugestellter E-Mails{#tracking-bounced-emails}

>[!NOTE]
>
>Adobe plant nicht, die Verfolgung von über den AEM-SMTP-Dienst gesendeten offenen/zurückgesendeten E-Mails weiter auszubauen.
>
>Die Empfehlung lautet: [Verwenden von Adobe Campaign und seiner AEM](/help/sites-administering/campaign.md).

Wenn Sie einen Newsletter an viele Benutzer senden, sind in der Liste im Allgemeinen einige ungültige E-Mail-Adressen enthalten. Newsletter, die an diese Adressen gesendet werden, können nicht zugestellt werden. AEM können diese Bounces verwalten und den Versand von Newslettern an diese Adressen einstellen, nachdem der konfigurierte Bounce-Zähler überschritten wurde. Der Standardwert für fehlgeschlagene Zustellversuche beträgt 3, er kann jedoch angepasst werden.

Um AEM zur Verfolgung nicht zugestellter E-Mails einzurichten, richten Sie AEM ein, um ein bestehendes Postfach zu abfragen, an das nicht zugestellte E-Mails gesendet werden. Normalerweise ist dieser Ort die &quot;Von&quot;-E-Mail-Adresse, die Sie angeben, wo Sie den Newsletter versenden. AEM fragt diesen Posteingang ab und importiert alle E-Mails in das in den Abrufeinstellungen festgelegte Verzeichnis. Dann wird ein Workflow gestartet, bei dem in den Benutzern nach den E-Mail-Adressen gesucht wird, an die keine Zustellung erfolgen konnte, und der Eigenschaftswert „bounceCounter“ des Benutzers entsprechend aktualisiert wird. Nachdem die konfigurierten maximalen Absprünge überschritten wurden, wird der Benutzer aus der Newsletter-Liste entfernt.

## Konfigurieren des Feed-Importtools {#configuring-the-feed-importer}

Mit dem Feed Importer können Sie wiederholt Inhalte aus externen Quellen in Ihr Repository importieren. Mit dieser Konfiguration des Feed-Importtools überprüft AEM das Postfach des Absenders auf Bounce-E-Mails.

Gehen Sie wie folgt vor, um das Feed-Importtool zum Verfolgen nicht zugestellter E-Mails zu konfigurieren:

1. In **Instrumente**, wählen Sie den Feed-Importtool aus.

1. Klicken **Hinzufügen** , um eine Konfiguration zu erstellen.

   ![chlimage_1](assets/chlimage_1a.png)

1. Fügen Sie eine Konfiguration hinzu, indem Sie den Typ auswählen und der Abruf-URL Informationen hinzufügen, damit Sie den Host und Port konfigurieren können. Fügen Sie außerdem einige Mail- und protokollspezifische Parameter zur URL-Abfrage hinzu. Stellen Sie die Konfiguration so ein, dass mindestens einmal täglich eine Abfrage durchgeführt wird.

   Alle Konfigurationen benötigen Informationen über Folgendes in der Abruf-URL:

   `username`: Der Benutzername, der zum Verbinden verwendet wird

   `password`: Das Kennwort für die Verbindung

   Darüber hinaus können Sie je nach Protokoll bestimmte Einstellungen konfigurieren.

   **Eigenschaften der POP3-Konfiguration:**

   `pop3.leave.on.server`: Legt fest, ob Nachrichten auf dem Server bleiben. Wählen Sie „true“, wenn Nachrichten auf dem Server bleiben sollen, bzw. „false“, wenn dies nicht der Fall sein soll. Standardwert ist „true“.

   **POP3-Beispiele:**

   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret | Verwenden von pop3 über SSL zur Verbindung mit GMail an Port 995 mit Benutzer/geheim, sodass Nachrichten standardmäßig auf dem Server bleiben |
   |---|---|
   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false |

   **Eigenschaften der IMAP-Konfiguration:**

   Hier können Sie Flags festlegen, nach denen gesucht werden soll.

   `imap.flag.SEEN`: Wählen Sie „false“ für eine neue/nicht gelesene Nachricht und „true“ für bereits gelesene Nachrichten aus.

   Siehe [https://javaee.github.io/javamail/docs/api/index.html?javax/mail/Flags.Flag.html](https://javaee.github.io/javamail/docs/api/index.html?javax/mail/Flags.Flag.html) für die vollständige Liste der Flaggen.

   **IMAP-Beispiele:**

   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret | Verwendung von IMAP über SSL, um an Port 993 eine Verbindung zu GMail mit dem Konto user/secret herzustellen. Standardmäßig werden neue Nachrichten abgerufen. |
   |---|---|
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true | Verwendung von IMAP über SSL zur Verbindung mit GMail 993 mit dem Benutzer/Geheimnis, nur Anzeige der Nachricht. |
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true&amp;imap.flag.SEEN=false | Verwendung von IMAP über SSL zur Verbindung mit GMail 993 mit Benutzer/Geheimnis, bereits gelesene ODER neue Nachrichten. |

1. Speichern Sie die Konfiguration.

## Konfigurieren der Komponente des Newsletter-Dienstes {#configuring-the-newsletter-service-component}

Konfigurieren Sie nach der Konfiguration des Feed-Importtools die Absenderadresse und den Bounce-Zähler.

So konfigurieren Sie den Newsletter-Dienst:

1. In der OSGi-Konsole unter `<host>:<port>/system/console/configMgr`, navigieren Sie zu **MCM-Newsletter**.

1. Konfigurieren Sie den Dienst und speichern Sie anschließend die Änderungen.

   ![chlimage_1-1](assets/chlimage_1-1a.png)

   Die folgenden Konfigurationen können festgelegt werden, um das Verhalten anzupassen:

   | Bounce-Zählermaximum (max.bounce.count) | Definiert die Anzahl der Bounces, bis ein Benutzer beim Senden eines Newsletters weggelassen wird. Wenn Sie diesen Wert auf 0 setzen, wird die Bounce-Prüfung vollständig deaktiviert. |
   |---|---|
   | Aktivitäts-No-Cache (sent.activity.nocache) | Definiert die Cache-Einstellung, die für die Aktivität &quot;Newsletter gesendet&quot;verwendet werden soll |

   Nach dem Speichern führt der MCM-Dienst für den Newsletter Folgendes aus:

   * Schreibt eine Aktivität in den verborgenen Stream der Benutzer nach erfolgreichem Versand eines Newsletters.
   * Schreibt eine Aktivität, wenn ein Bounce erkannt wird und sich der Bounce-Zähler der Benutzer ändert.
