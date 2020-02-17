---
title: Messaging Essentials
seo-title: Messaging Essentials
description: Übersicht über die Messaging-Komponente
seo-description: Übersicht über die Messaging-Komponente
uuid: e0dad45e-d84d-4b28-b357-aded1c5d2605
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 98f70093-e786-4555-8aaa-d0df4c977dc0
docset: aem65
translation-type: tm+mt
source-git-commit: a3ccb1ffe2b2e24c453afac8cf3efc098f393030

---


# Messaging Essentials{#messaging-essentials}

Diese Seite dokumentiert die Details zum Arbeiten mit der Messaging-Komponente, um eine Messaging-Funktion auf einer Website einzuschließen.

## Grundlagen für clientseitige {#essentials-for-client-side}

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
   <td>siehe <a href="/help/communities/configure-messaging.md" target="_blank">Messaging konfigurieren</a></td>
  </tr>
  <tr>
   <td><strong>Admin-Konfiguration</strong></td>
   <td><a href="/help/communities/messaging.md">Nachrichten konfigurieren</a></td>
  </tr>
 </tbody>
</table>

**Nachrichtenliste**

(für &quot;Posteingang&quot;, &quot;Gesendet&quot;und &quot;Papierkorb&quot;)

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
   <td>siehe <a href="/help/communities/configure-messaging.md" target="_blank">Messaging konfigurieren</a></td>
  </tr>
  <tr>
   <td><strong>Admin-Konfiguration</strong></td>
   <td><a href="/help/communities/messaging.md" target="_blank">Nachrichten konfigurieren</a></td>
  </tr>
 </tbody>
</table>

Siehe auch [clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Messaging konfigurieren](/help/communities/configure-messaging.md)
* [Messaging-Client-APIs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) für SCF-Komponenten
* [Messaging-APIs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) für den Dienst
* [Messaging-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)
* [Serverseitige Anpassungen](/help/communities/server-customize.md)

>[!CAUTION]
>
>Der String-Parameter darf für die folgenden MessageBuilder-Methoden *keinen *folgenden Schrägstrich (/) enthalten:
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>
Beispiel:
>
>
```>
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```>



### Community-Site {#community-site}

Eine mit dem Assistenten erstellte Community-Site-Struktur enthält die Nachrichtenfunktion, wenn diese ausgewählt ist. Siehe `User Management` Einstellungen der [Community-Sites-Konsole](/help/communities/sites-console.md#user-management).

### Beispielcode: Benachrichtigung erhalten {#sample-code-message-received-notification}

Die Social Messaging-Funktion gibt Ereignisse für Vorgänge aus, z. B. `send``marking read`, `marking delete`. Diese Ereignisse können abgefangen und Aktionen für die im Ereignis enthaltenen Daten durchgeführt werden.

Das folgende Beispiel zeigt einen Ereignishandler, der auf das `message sent` Ereignis überwacht und eine E-Mail an alle Empfänger mit dem `Day CQ Mail Service`Ereignis sendet.

Zum Testen des serverseitigen Beispielskripts benötigen Sie eine Entwicklungsumgebung und die Möglichkeit zum Erstellen eines OSGi-Bundles:

1. Melden Sie sich als Administrator an, um ` [CRXDE|Lite](https://localhost:4502/crx/de).`
1. Erstellen Sie ein `bundle node`in `/apps/engage/install` mit beliebigen Namen, z. B.:

   * Symbolischer Name: com.engagement.media.social.messaging.MessagingNotification
   * Name: Benachrichtigung über Erste Schritte - Benachrichtigung
   * Beschreibung: ein Beispieldienst zum Senden einer E-Mail-Benachrichtigung an Benutzer, die eine Nachricht erhalten
   * Paket: com.engagement.media.social.messaging.notification

1. Navigieren Sie zu /apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engagement/media/social/messaging/notification und dann:

   1. Löschen Sie die automatisch erstellte Activator.java-Klasse.
   1. Erstellen Sie die Klasse MessageEventHandler.java.
   1. Kopieren Sie den unten stehenden Code und fügen Sie ihn in MessageEventHandler.java ein.

1. Klicken Sie auf **Alle speichern.**
1. Navigieren Sie zu /apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd und fügen Sie alle Importanweisungen wie im MessageEventHandler.java-Code geschrieben hinzu.
1. Erstellen Sie das Bundle.
1. Stellen Sie sicher, dass der `Day CQ Mail Service`OSGi-Dienst konfiguriert ist.
1. Melden Sie sich als Demo-Benutzer an und senden Sie eine E-Mail an einen anderen Benutzer.
1. Der Empfänger erhält eine E-Mail zu einer neuen Nachricht.

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

