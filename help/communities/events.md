---
title: OSGi-Ereignis für Communities-Komponenten
seo-title: OSGi-Ereignis für Communities-Komponenten
description: OSGi-Ereignis werden gesendet, die asynchrone Listener auslösen können
seo-description: OSGi-Ereignis werden gesendet, die asynchrone Listener auslösen können
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 5%

---


# OSGi-Ereignis für Communities-Komponenten {#osgi-events-for-communities-components}

## Überblick {#overview}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden OSGi-Ereignis gesendet, die asynchrone Listener auslösen können, z. B. Benachrichtigungen oder Gamification (Scoring und Abzeichen).

Die [SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html)-Instanz einer Komponente zeichnet die Ereignis als `actions` auf, die für ein `topic` auftreten. Das SocialEvent enthält eine Methode, um eine `verb` zurückzugeben, die der Aktion zugeordnet ist. Es besteht eine *n-1*-Beziehung zwischen `actions` und `verbs`.

Die folgenden Tabellen beschreiben für die in der Version ausgelieferten Communities-Komponenten die für jedes `topic` definierte `verbs`, das zur Verwendung verfügbar ist.

## Themen und Verben {#topics-and-verbs}

[Calendar ](calendar-basics-for-developers.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Ereignis im Kalender |
| HINZUFÜGEN | Anmerkungen zu einem Ereignis |
| UPDATE | Ereignis oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Ereignis oder Kommentar des Mitglieds wird gestrichen |

[Kommentare ](essentials-comments.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Antworten des Mitglieds auf Bemerkungen |
| UPDATE | Kommentar des Mitglieds wird bearbeitet |
| DELETE | Anmerkung des Mitglieds wird gestrichen |

[File Library ](essentials-file-library.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Ordner |
| ANLAGE | Mitglied lädt eine Datei hoch |
| UPDATE | Mitglied aktualisiert einen Ordner oder eine Datei |
| DELETE | Mitglied löscht Ordner oder Dateien |

[Forum ](essentials-forum.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumthema |
| HINZUFÜGEN | Antworten der Mitglieder auf das Forenthema |
| UPDATE | Forenthema oder Antwort des Mitglieds wird bearbeitet |
| DELETE | Forenthema oder Antwort des Mitglieds wird gelöscht |

[Protokoll ](blog-developer-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/Protokoll

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blog-Artikel |
| HINZUFÜGEN | Kommentare zu Mitgliedern in einem Blog-Artikel |
| UPDATE | Blog-Artikel oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Blog-Artikel oder Kommentar des Mitglieds wird gelöscht |

[QnA ](qna-essentials.md)
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine Frage zur QnA |
| HINZUFÜGEN | Mitglied erstellt eine QnA-Antwort |
| UPDATE | Die Frage oder Antwort des Mitglieds zur Servicequalität wird bearbeitet |
| SELECT | Antwort des Mitglieds ausgewählt |
| AUSWAHL aufheben | Antwort des Mitglieds wird deaktiviert |
| DELETE | Frage oder Antwort des Mitglieds zur Servicequalität wird gelöscht |

[Reviews ](reviews-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied prüft |
| UPDATE | Überprüfung durch die Mitglieder wird bearbeitet |
| DELETE | Überprüfung durch das Mitglied wird gestrichen |

[Rating ](rating-basics.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| hinzufügen | Der Inhalt des Mitglieds wurde bewertet |
| RATING ENTFERNEN | Der Inhalt des Mitglieds wurde herabgesetzt |

[Voting ](essentials-voting.md)
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| hinzufügen ABSTIMMUNG | Der Inhalt des Mitglieds wurde zur Abstimmung gestellt |
| ABSTIMMUNG ENTFERNEN | Der Inhalt des Mitglieds wurde abgelehnt |

**Moderationsaktivierte**
KomponentenSocialEvent  `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| DENY | Inhalt des Mitglieds wird verweigert |
| FLAG-AS-INAPPROPRIATE | Der Inhalt des Mitglieds wird markiert |
| UNFLAG-AS-INAPPROPRIATE | Der Inhalt des Mitglieds ist unmarkiert |
| AKZEPT | Der Inhalt des Mitglieds wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| OPEN | Mitglied öffnet Kommentar erneut |

## Ereignis für benutzerdefinierte Komponenten {#events-for-custom-components}

Bei einer benutzerdefinierten Komponente muss die abstrakte [SocialEvent-Klasse](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) erweitert werden, um die Ereignis der Komponente als `actions`aufzuzeichnen, die für ein `topic` auftreten.

Das benutzerdefinierte Ereignis setzt die Methode `getVerb()` außer Kraft, sodass für jedes `action` ein entsprechendes `verb`zurückgegeben wird. Das für eine Aktion zurückgegebene `verb` kann eine häufig verwendete (z. B. `POST`) oder eine für die Komponente spezialisierte (z. B. `ADD RATING`) sein. Es besteht eine *n-1*-Beziehung zwischen `actions`und `verbs`.

>[!NOTE]
>
>Stellen Sie sicher, dass eine benutzerdefinierte Erweiterung mit einer niedrigeren Rangfolge registriert ist als jede vorhandene Implementierung im Produkt.

### Pseudo-Code für das Ereignis für benutzerdefinierte Komponenten {#pseudo-code-for-custom-component-event}

[org.osgi.service.Ereignis.Ereignis](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html); 
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html); 
[com.adobe.granite.activitystreams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html); 
[com.adobe.granite.activitystreams.Verbs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

```java
package com.mycompany.recipe;

import org.osgi.service.event.Event;
import com.adobe.cq.social.scf.core.SocialEvent;
import com.adobe.granite.activitystreams.ObjectTypes;
import com.adobe.granite.activitystreams.Verbs;

/*
 * The Recipe type, passed to RecipeEvent(), would be a custom Recipe class
 * that extends either
 * com.adobe.cq.social.scf.SocialComponent
 * or
 * com.adobe.cq.social.scf.SocialCollectionComponent
 * See https://docs.adobe.com/docs/en/aem/6-2/develop/communities/scf/server-customize.html
 */

/**
 * Defines events that are triggered on a custom component, "Recipe".
 */
public class RecipeEvent extends SocialEvent<RecipeEvent.RecipeActions> {

    private static final long serialVersionUID = 1L;
    protected static final String PARENT_PATH = "PARENT_PATH";

    /**
     * The event topic suffix for Recipe events
     */
    public static final String RECIPE_TOPIC = "recipe";

    /**
     * @param recipe - the recipe resource on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final Recipe recipe, final String userId, final RecipeEvent.RecipeActions action) {
        String recipePath = recipe.getResource().getPath();
        String parentPath = (recipe.getParentComponent() != null) ?
                             recipe.getParentComponent().getResource().getPath() :
                             recipe.getSourceComponentId();
        this(recipePath, userId, parentPath, action);
    }

    /**
     * @param recipePath - the path to the recipe resource (jcr node) on which the event was triggered
     * @param userId - the user id of the user who triggered the action
     * @param parentPath - the path to the parent node of the recipe resource
     * @param action - the recipe action that triggered this event
     */
    public RecipeEvent(final String recipePath, final String userId, final String parentPath) {
        super(RECIPE_TOPIC, recipePath, userId, action,
              new BaseEventObject(recipePath, ObjectTypes.ARTICLE),
              new BaseEventObject(parentPath, ObjectTypes.COLLECTION),
              new HashMap<String, Object>(1) {
            private static final long serialVersionUID = 1L;
            {
                if (parentPath != null) {
                    this.put(PARENT_PATH, parentPath);
                }

            }
        });
    }

    private RecipeEvent (final Event event) {
      super(event);
    }

    /**
     * List of available recipe actions that can trigger a recipe event.
     */
    public static enum RecipeActions implements SocialEvent.SocialActions {
        RecipeAdded,
        RecipeModified,
        RecipeDeleted;

        @Override
        public String getVerb() {
            switch (this) {
                case RecipeAdded:
                    return Verbs.POST;
                case RecipeModified:
                    return Verbs.UPDATE;
                case RecipeDeleted:
                    return Verbs.DELETE;
                default:
                    throw new IllegalArgumentException("Unsupported action");
            }
        }
    }

}
```

## Beispiel für EventListener zum Filtern von Aktivität-Stream-Daten {#sample-eventlistener-to-filter-activity-stream-data}

Es ist möglich, auf Ereignis zu hören, um zu ändern, was im Aktivitäten-Stream angezeigt wird.

Im folgenden Pseudo-Codebeispiel werden DELETE-Ereignis für Kommentarkomponente aus dem Aktivitäten-Stream entfernt.

### Pseudo-Code für EventListener {#pseudo-code-for-eventlistener}

Erfordert [das neueste Feature Pack](deploy-communities.md#latestfeaturepack).

```java
package my.company.comments;

import java.util.Collections;
import java.util.Map;

import org.apache.commons.lang.StringUtils;
import org.apache.felix.scr.annotations.Activate;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Modified;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.osgi.PropertiesUtil;
import org.osgi.service.component.ComponentContext;

import com.adobe.cq.social.activitystreams.listener.api.ActivityStreamProviderExtension;
import com.adobe.cq.social.commons.events.CommentEvent.CommentActions;
import com.adobe.cq.social.scf.core.SocialEvent;

@Service
@Component(metatype = true, label = "My Comment Delete Event Filter",
        description = "Prevents comment DELETE events from showing up in activity streams")
public class CommentDeleteEventActivityFilter implements ActivityStreamProviderExtension {

    @Property(name = "ranking", intValue = 10)
    protected int ranking;

    @Activate
    public void activate(final ComponentContext ctx) {
        ranking = PropertiesUtil.toInteger(ctx.getProperties().get("ranking"), 10);
    }

    @Modified
    public void update(final Map<String, Object> props) {
        ranking = PropertiesUtil.toInteger(props.get("ranking"), 10);
    }

    @Override
    public boolean evaluate(final SocialEvent<?> evt, final Resource resource) {
        if (evt.getAction() != null && evt.getAction() instanceof SocialEvent.SocialActions) {
            final SocialEvent.SocialActions action = evt.getAction();
            if (StringUtils.equals(action.getVerb(), CommentActions.DELETED.getVerb())) {
                return false;
            }
        }
        return true;
    }

    @Override
    public Map<String, ? extends Object> getActivityProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public Map<String, ? extends Object> getActorProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String getName() {
        return "My Comment Delete Event Filter";
    }

    @Override
    public Map<String, ? extends Object> getObjectProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    /* Ensure a custom extension is registered with a ranking lower than any existing implementation in the product. */
    @Override
    public int getRanking() {
        return this.ranking;
    }

    @Override
    public Map<String, ? extends Object> getTargetProperties(final SocialEvent<?> arg0, final Resource arg1) {
        return Collections.<String, Object>emptyMap();
    }

    @Override
    public String[] getStreamProviderPid() {
        return new String[]{"*"};
    }

}
```

