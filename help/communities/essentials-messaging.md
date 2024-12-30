---
title: Messaging Essentials
description: Erfahren Sie mehr über die Einzelheiten der Arbeit mit und die Verwendung der Komponente Messaging , um eine Messaging-Funktion auf einer Website einzuschließen.
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

# Messaging Essentials {#messaging-essentials}

Auf dieser Seite werden die Details der Arbeit mit dokumentiert, die mit der Messaging-Komponente durchgeführt wird, um eine Messaging-Funktion in eine Website einzuschließen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

**Nachricht erstellen**

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/composemessage</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientlibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="/help/communities/configure-messaging.md" target="_blank">Konfigurieren von Messaging</a></td>
  </tr>
  <tr>
   <td><strong>Admin-Konfiguration</strong></td>
   <td><a href="/help/communities/messaging.md">Konfigurieren von Messaging</a></td>
  </tr>
 </tbody>
</table>

**Nachrichtenliste**

(Für Posteingang, gesendet und Papierkorb)

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td><p>social/messaging/components/hbs/messageBox</p> </td>
  </tr>
  <tr>
   <td> <a href="/help/communities/client-customize.md#clientlibs-for-scf" target="_blank"><strong>clientlibs</strong></a></td>
   <td><p>cq.social.hbs.messaging</p> </td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="/help/communities/configure-messaging.md" target="_blank">Konfigurieren von Messaging</a></td>
  </tr>
  <tr>
   <td><strong>Admin-Konfiguration</strong></td>
   <td><a href="/help/communities/messaging.md" target="_blank">Konfigurieren von Messaging</a></td>
  </tr>
 </tbody>
</table>

Siehe auch [Client-seitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Konfigurieren von Nachrichten](/help/communities/configure-messaging.md)
* [Messaging-Client-](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html)) für SCF-Komponenten
* [Messaging-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) für den Service
* [Messaging-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)
* [Server-seitige Anpassungen](/help/communities/server-customize.md)

>[!CAUTION]
>
>Der Zeichenfolgenparameter darf *keinen* Schrägstrich &quot;/&quot; für die folgenden MessageBuilder-Methoden enthalten:
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

Eine Community-Site-Struktur, die mithilfe des Assistenten erstellt wurde, enthält die Messaging-Funktion, wenn sie ausgewählt wird. Siehe `User Management` Einstellungen der [Community Sites-Konsole](/help/communities/sites-console.md#user-management).

### Beispielcode: Benachrichtigung über empfangene Nachricht {#sample-code-message-received-notification}

Die Social-Messaging-Funktion löst Ereignisse für Vorgänge aus, z. B. `send`, `marking read`, `marking delete`. Diese Ereignisse können erfasst und Aktionen für die im Ereignis enthaltenen Daten durchgeführt werden.

Das folgende Beispiel zeigt einen Ereignis-Handler, der auf das `message sent`-Ereignis wartet und mithilfe der `Day CQ Mail Service` eine E-Mail an alle Nachrichtenempfänger sendet.

Um das Server-seitige Beispielskript auszuprobieren, benötigen Sie eine Entwicklungsumgebung und die Möglichkeit, ein OSGi-Bundle zu erstellen:

1. Melden Sie sich als Administrator bei ` [CRXDE|Lite](https://localhost:4502/crx/de)` an.
1. Erstellen Sie eine `bundle node`-`/apps/engage/install` mit beliebigen Namen, z. B.:

   * Symbolischer Name: `com.engage.media.social.messaging.MessagingNotification`
   * Name: Erste Schritte Tutorial-Benachrichtigung
   * Beschreibung: Ein Beispiel-Service für das Senden einer E-Mail-Benachrichtigung an Benutzer, wenn sie eine Nachricht erhalten
   * Paket: `com.engage.media.social.messaging.notification`

1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification` und dann:

   1. Löschen Sie die automatisch erstellte `Activator.java`.
   1. Erstellen Sie `MessageEventHandler.java`.
   1. Kopieren Sie den unten stehenden Code und fügen Sie ihn in `MessageEventHandler.java` ein.

1. Klicken Sie auf **Alle speichern**.
1. Navigieren Sie zu `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` und fügen Sie alle Importanweisungen hinzu, wie sie im `MessageEventHandler.java`-Code geschrieben sind.
1. Erstellen Sie das Bundle.
1. Stellen Sie sicher`Day CQ Mail Service` dass der OSGi-Dienst konfiguriert ist.
1. Melden Sie sich als Demobenutzer an und senden Sie eine E-Mail an einen anderen Benutzer.
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
