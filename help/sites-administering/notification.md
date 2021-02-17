---
title: Konfigurieren von E-Mail-Benachrichtigungen
seo-title: Konfigurieren von E-Mail-Benachrichtigungen
description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen in AEM konfigurieren können.
seo-description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen in AEM konfigurieren können.
uuid: 6cbdc312-860b-4a69-8bbe-2feb32204a27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6466d7b8-e308-43c5-acdc-dec15f796f64
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 76%

---


# Konfigurieren von E-Mail-Benachrichtigungen{#configuring-email-notification}

AEM sendet E-Mail-Benachrichtigungen an Benutzer, die:

* Seitenereignisse wie Änderungen oder Replikationen abonniert haben. Im Abschnitt [Benachrichtigungs-Posteingang](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) ist beschrieben, wie solche Ereignisse abonniert werden können.

* Forenereignisse abonniert haben.
* einen Schritt innerhalb eines Workflows durchführen müssen. Im Abschnitt [Teilnehmer-Schritt](/help/sites-developing/workflows-step-ref.md#participant-step) ist beschreiben, wie E-Mail-Benachrichtigungen in einem Workflow ausgelöst werden können.

Voraussetzungen:

* Benutzer müssen über eine in ihrem Profil festgelegte, gültige E-Mail-Adresse verfügen.
* Der **Day CQ Mail Service** muss ordnungsgemäß konfiguriert sein.

Wenn ein Benutzer benachrichtigt wird, erhält er eine E-Mail in der Sprache, die in seinem Profil festgelegt ist. Jede Sprache verfügt über eine eigene, anpassbare Vorlage. Für neue Sprachen können neue E-Mail-Vorlagen hinzugefügt werden.

>[!NOTE]
>
>Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Konfigurieren des E-Mail-Diensts {#configuring-the-mail-service}

Damit AEM E-Mails versenden kann, muss der **Day CQ Mail Service** ordnungsgemäß konfiguriert sein. Sie können die Konfiguration in der Web-Konsole anzeigen. Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Es gelten die folgenden Beschränkungen:

* Der **SMTP-Server-Anschluss** muss 25 oder höher sein.

* Der Hostname des **SMTP-Servers** darf nicht leer sein.
* Die **„Von“-Adresse** darf nicht leer sein.

Zum Debuggen eines Problems mit dem **Day CQ Mail Service** können Sie die Protokolle des Diensts betrachten:

`com.day.cq.mailer.DefaultMailService`

Die Konfiguration sieht in der Web-Konsole wie folgt aus:

![chlimage_1-276](assets/chlimage_1-276.png)

## Konfigurieren des E-Mail-Benachrichtigungskanals {#configuring-the-email-notification-channel}

Wenn Sie entweder Benachrichtigungen zu Seiten- oder Forenereignissen abonniert haben, ist die „Von“-E-Mail-Adresse standardmäßig auf `no-reply@acme.com` eingestellt. Sie können diesen Wert durch die Konfiguration des Diensts **Benachrichtigungs-E-Mail-Kanal** in der Web-Konsole ändern.

Fügen Sie zum Konfigurieren der „Von“-E-Mail-Adresse einen `sling:OsgiConfig`-Knoten zum Repository hinzu. Verwenden Sie das folgende Verfahren, um den Knoten direkt mithilfe von CRXDE Lite hinzuzufügen:

1. Fügen Sie in CRXDE Lite einen Ordner mit dem Namen `config` unter Ihrem Anwendungsordner hinzu.
1. Fügen Sie im Ordner &quot;config&quot;einen Knoten mit dem Namen:

   `com.day.cq.wcm.notification.email.impl.EmailChannel` vom Typ `sling:OsgiConfig`

1. hinzufügen Sie eine `String`-Eigenschaft auf den Knoten `email.from`. Legen Sie zu dem Wert die E-Mail-Adresse fest, die Sie verwenden möchten.

1. Klicken Sie auf **Alle speichern**.

Gehen Sie wie folgt vor, um den Knoten in den Inhaltspaketen Ihrer Quellordner festzulegen:

1. Erstellen Sie in Ihrer `jcr_root/apps/*app_name*/config folder`-Datei eine Datei mit dem Namen `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`

1. Fügen Sie die folgende XML für den Knoten hinzu:

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. Ersetzen Sie den Wert des Attributs `email.from` (`name@server.com`) durch Ihre E-Mail-Adresse.

1. Speichern Sie die Datei.

## Konfigurieren des Workflow-E-Mail-Benachrichtigungsdiensts  {#configuring-the-workflow-email-notification-service}

Wenn Sie Workflow-E-Mail-Benachrichtigungen erhalten, sind beide „Von“-E-Mail-Adressen und das Host-URL-Präfix auf Standardwerte eingestellt. Sie können diese Werte ändern, indem Sie den **Day CQ Workflow Email Notification Service** in der Web-Konsole konfigurieren. Wenn Sie dies tun, wird empfohlen, die Änderung im Repository beizubehalten.

Die Standardkonfiguration sieht in der Web-Konsole wie folgt aus:

![chlimage_1-277](assets/chlimage_1-277.png)

### E-Mail-Vorlagen für die Seitenbenachrichtigung {#email-templates-for-page-notification}

E-Mail-Vorlagen für die Seitenbenachrichtigungen sind zu finden unter:

`/etc/notification/email/default/com.day.cq.wcm.core.page`

Die standardmäßige englische Vorlage (`en.txt`) wird wie folgt definiert:

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Seitenbenachrichtigung {#customizing-email-templates-for-page-notification}

Die englische E-Mail-Vorlage für die Seitenbenachrichtigung können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/etc/notification/email/default/com.day.cq.wcm.core.page/en.txt`

1. Passen Sie die Datei an Ihre Anforderungen an.
1. Speichern Sie die Änderungen.

Die Vorlage muss folgendes Format aufweisen:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Dabei kann &lt;text_x> ein Mix von statischem Text und dynamischen Stringvariablen sein. Die folgenden Variablen können innerhalb der E-Mail-Vorlage für Seitenbenachrichtigungen verwendet werden:

* `${time}`, Ereignis und Uhrzeit.

* `${userFullName}`, der vollständige Name des Benutzers, der das Ereignis ausgelöst hat.

* `${userId}`, die ID des Benutzers, der das Ereignis ausgelöst hat.
* `${modifications}`, beschreibt den Typ des Seiten-Ereignisses und den Seitenpfad im Format:

   &lt;page event=&quot;&quot; type=&quot;&quot;> =>  &lt;page path=&quot;&quot;>

   Beispiel:

   PageModified => /content/geometrixx/de/products

### E-Mail-Vorlagen für die Forumsbenachrichtigung {#email-templates-for-forum-notification}

E-Mail-Vorlagen für die Forumsbenachrichtigungen sind zu finden unter:

`/etc/notification/email/default/com.day.cq.collab.forum`

Die standardmäßige englische Vorlage (`en.txt`) wird wie folgt definiert:

```xml
subject=[CQ Forum Notification]

header=-------------------------------------------------------------------------------------\n \
Time: Time: ${time}\n \
Forum Page Path: ${forum.path}\n \
-------------------------------------------------------------------------------------\n\n

message=Page: ${host.prefix}${forum.path}.html\n

footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Forumsbenachrichtigung {#customizing-email-templates-for-forum-notification}

Die englische E-Mail-Vorlage für die Forumsbenachrichtigung können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/etc/notification/email/default/com.day.cq.collab.forum/en.txt`

1. Passen Sie die Datei an Ihre Anforderungen an.
1. Speichern Sie die Änderungen.

Die Vorlage muss folgendes Format aufweisen:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Dabei kann `<text_x>` eine Mischung aus statischem Text und dynamischen Zeichenfolgenvariablen sein.

Die folgenden Variablen können innerhalb der E-Mail-Vorlage für Forumsbenachrichtigungen verwendet werden:

* `${time}`, Ereignis und Uhrzeit.

* `${forum.path}`, der Pfad zur Forumsseite.

### E-Mail-Vorlagen für die Workflow-Benachrichtigung {#email-templates-for-workflow-notification}

Die (englische) Vorlage für die Workflow-Benachrichtigungen befindet sich unter:

`/etc/workflow/notification/email/default/en.txt`

Sie wird wie folgt definiert:

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### Anpassen von E-Mail-Vorlagen für die Workflow-Benachrichtigung  {#customizing-email-templates-for-workflow-notification}

Die englische E-Mail-Vorlage für die Benachrichtigung über ein Workflow-Ereignis können Sie wie folgt anpassen:

1. Öffnen Sie in CRXDE die Datei:

   `/etc/workflow/notification/email/default/en.txt`

1. Passen Sie die Datei an Ihre Anforderungen an.
1. Speichern Sie die Änderungen.

Die Vorlage muss folgendes Format aufweisen:

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>Dabei kann `<text_x>` eine Mischung aus statischem Text und dynamischen Zeichenfolgenvariablen sein. Jede Zeile eines Elements `<text_x>` muss mit einem umgekehrten Schrägstrich ( `\`) beendet werden, mit Ausnahme der letzten Instanz, wenn das Fehlen des umgekehrten Schrägstrichs das Ende der Zeichenfolgenvariablen `<text_x>` angibt.
>
>Weitere Informationen zum Vorlagenformat werden von der Methode [javadocs der Properties.load()](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-)-Methode bereitgestellt.

Die Methode `${payload.path.open}` zeigt den Pfad zur Nutzlast des Arbeitselements an. Beispiel: Für eine Seite in Sites wäre `payload.path.open` ähnlich wie `/bin/wcmcommand?cmd=open&path=…`.; dies ohne den Servernamen ist, weshalb die Vorlage dieser mit `${host.prefix}` voranstellt.

Die folgenden Variablen können innerhalb der E-Mail-Vorlage verwendet werden:

* `${event.EventType}`, Typ des Ereignisses
* `${event.TimeStamp}`, Datum und Uhrzeit des Ereignisses
* `${event.User}`, der Benutzer, der das Ereignis ausgelöst hat
* `${initiator.home}`, der Pfad des Initiator-Knotens

* `${initiator.name}`, der Name des Initiators

* `${initiator.email}`, die E-Mail-Adresse des Initiators
* `${item.id}`, die ID des Arbeitselements
* `${item.node.id}`, ID des Knotens innerhalb des Workflow-Modells, das mit diesem Arbeitselement verknüpft ist
* `${item.node.title}`, Titel des Arbeitselements
* `${participant.email}`, E-Mail-Adresse des Teilnehmers
* `${participant.name}`, Name des Teilnehmers
* `${participant.familyName}`, Familienname des Teilnehmers
* `${participant.id}`, ID des Teilnehmers
* `${participant.language}`, die Teilnehmersprache
* `${instance.id}`, die Workflow-ID
* `${instance.state}`, den Workflow-Status
* `${model.title}`, Titel des Workflow-Modells
* `${model.id}`, die ID des Workflow-Modells

* `${model.version}`, die Version des Workflow-Modells
* `${payload.data}`, Nutzlast

* `${payload.type}`, den Nutzlasttyp
* `${payload.path}`, Pfad der Payload
* `${host.prefix}`, Host-Präfix, z. B. http://localhost:4502

### Hinzufügen einer E-Mail-Vorlage in einer neuen Sprache {#adding-an-email-template-for-a-new-language}

Sie können wie folgt eine Vorlage in einer neuen Sprache hinzufügen:

1. Fügen Sie in CRXDE eine Datei `<language-code>.txt` unten hinzu:

   * `/etc/notification/email/default/com.day.cq.wcm.core.page` : für Seitenbenachrichtigungen
   * `/etc/notification/email/default/com.day.cq.collab.forum` : Forumsbenachrichtigungen
   * `/etc/workflow/notification/email/default` : für Workflow-Benachrichtigungen

1. Passen Sie die Datei an die Sprache an.
1. Speichern Sie die Änderungen.

>[!NOTE]
>
>Der als Dateiname für die E-Mail-Vorlage verwendete `<language-code>` muss ein aus zwei Buchstaben bestehender Sprachcode sein, der von AEM erkannt wird. AEM nutzt die Sprachcodes gemäß ISO-639-1.

## Konfigurieren von E-Mail-Benachrichtigungen für AEM Assets {#assetsconfig}

Wenn Sammlungen in AEM Assets freigegeben werden oder ihre Freigabe aufgehoben wird, können Benutzer E-Mail-Benachrichtigungen von AEM erhalten. Um E-Mail-Benachrichtigungen zu konfigurieren, führen Sie diese Schritte aus.

1. Konfigurieren Sie den E-Mail-Dienst, wie oben unter [Konfigurieren des E-Mail-Diensts](/help/sites-administering/notification.md#configuring-the-mail-service) beschrieben.
1. Melden Sie sich in AEM als Administrator an. Klicken Sie auf **Tools**> **Vorgänge**> **Web-Konsole**, um die Konfiguration der Web-Konsole zu öffnen.
1. Bearbeiten Sie das **Day CQ DAM-Ressourcensammlungs-Servlet**. Wählen Sie **E-Mail senden**. Klicken Sie auf **Speichern**.

