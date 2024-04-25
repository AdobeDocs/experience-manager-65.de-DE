---
title: Grundlagen zu Messaging
description: Erfahren Sie mehr über die Funktionsweise und Verwendung der Messaging-Komponente, um eine Messaging-Funktion auf einer Website hinzuzufügen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: b941b5e0-f768-4393-9a9d-ded2cd7d10c4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# Grundlagen zu Messaging {#messaging-essentials}

Auf dieser Seite werden die Details zum Arbeiten mit der Messaging-Komponente beschrieben, um eine Messaging-Funktion auf einer Website einzubinden.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

**Nachricht erstellen**

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/composemessage</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientllibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td>
  </tr>
  <tr>
   <td><strong>css</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="/help/communities/configure-messaging.md" target="_blank">Messaging konfigurieren</a></td>
  </tr>
  <tr>
   <td><strong>Administratorkonfiguration</strong></td>
   <td><a href="/help/communities/messaging.md">Messaging konfigurieren</a></td>
  </tr>
 </tbody>
</table>

**Nachrichtenliste**

(Für Posteingang, Gesendet und Papierkorb)

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/messagebox</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientllibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td>
  </tr>
  <tr>
   <td><strong>css</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="/help/communities/configure-messaging.md" target="_blank">Messaging konfigurieren</a></td>
  </tr>
  <tr>
   <td><strong>Administratorkonfiguration</strong></td>
   <td><a href="/help/communities/messaging.md" target="_blank">Messaging konfigurieren</a></td>
  </tr>
 </tbody>
</table>

Siehe auch [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Messaging konfigurieren](/help/communities/configure-messaging.md)
* [Messaging-Client-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) für SCF-Komponenten
* [Messaging-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) für den Dienst
* [Messaging-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)
* [Serverseitige Anpassungen](/help/communities/server-customize.md)

>[!CAUTION]
>
>Der String-Parameter muss *not* einen Schrägstrich (/) für die folgenden MessageBuilder-Methoden enthalten:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>Zum Beispiel:
>
>```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### Community-Site {#community-site}

Eine Community-Site-Struktur, die mithilfe des Assistenten erstellt wurde, enthält die Messaging-Funktion, falls ausgewählt. Siehe `User Management` Einstellungen von [Community-Sites-Konsole](/help/communities/sites-console.md#user-management).

### Beispielcode: Nachricht erhalten Benachrichtigung {#sample-code-message-received-notification}

Die Funktion Social Messaging gibt Ereignisse für Vorgänge aus, z. B. `send`, `marking read`, `marking delete`. Diese Ereignisse können erfasst und Aktionen für die im Ereignis enthaltenen Daten durchgeführt werden.

Das folgende Beispiel zeigt einen Ereignis-Handler, der auf die `message sent` -Ereignis ein und sendet eine E-Mail an alle Empfänger, die die `Day CQ Mail Service`.

Zum Testen des serverseitigen Beispielskripts benötigen Sie eine Entwicklungsumgebung und die Möglichkeit, ein OSGi-Bundle zu erstellen:

1. Melden Sie sich bei ` [CRXDE|Lite](https://localhost:4502/crx/de)`.
1. Erstellen Sie eine `bundle node`in `/apps/engage/install` mit beliebigen Namen wie:

   * Symbolischer Name: `com.engage.media.social.messaging.MessagingNotification`
   * Name: Erste Schritte - Benachrichtigung zu Tutorial-Nachrichten
   * Beschreibung: Ein Beispieldienst zum Senden einer E-Mail-Benachrichtigung an Benutzer, wenn diese eine Nachricht erhalten
   * Package: `com.engage.media.social.messaging.notification`

1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`und dann:

   1. Löschen Sie die `Activator.java` automatisch erstellte Klasse.
   1. Klasse erstellen `MessageEventHandler.java`.
   1. Kopieren Sie den unten stehenden Code und fügen Sie ihn in `MessageEventHandler.java`.

1. Klicken Sie auf **Alle speichern**.
1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd`und fügen Sie alle Importanweisungen hinzu, wie in der Datei `MessageEventHandler.java` Code.
1. Erstellen Sie das Bundle.
1. Sichern `Day CQ Mail Service`Der OSGi-Dienst ist konfiguriert.
1. Melden Sie sich als Demobenutzer an und senden Sie eine E-Mail an einen anderen Benutzer.
1. Der Empfänger erhält eine E-Mail bezüglich einer neuen Nachricht.

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site,
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
