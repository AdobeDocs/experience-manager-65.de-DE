---
title: OSGi-Ereignisse für Communities-Komponenten
seo-title: OSGi-Ereignisse für Communities-Komponenten
description: OSGi-Ereignisse werden gesendet, die asynchrone Listener auslösen können
seo-description: OSGi-Ereignisse werden gesendet, die asynchrone Listener auslösen können
uuid: 317e2add-689d-4c99-ae38-0703b6649cb7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 25b7ac08-6cdc-4dd5-a756-d6169b86f9ab
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# OSGi-Ereignisse für Communities-Komponenten {#osgi-events-for-communities-components}

## Überblick {#overview}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden OSGi-Ereignisse gesendet, die asynchrone Listener auslösen können, wie Benachrichtigungen oder Gamification (Scoring und Abzeichen).

Die [SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) -Instanz einer Komponente zeichnet die Ereignisse auf, `actions`die für eine `topic`Komponente auftreten. Das SocialEvent enthält eine Methode, um eine mit der Aktion `verb`verbundene Aktion zurückzugeben. Es gibt eine *n-1* Beziehung zwischen `actions`und `verbs`.

Die folgenden Tabellen beschreiben die `verbs`Definition für die in der Version bereitgestellten Communities-Komponenten, die für die einzelnen `topic`verfügbaren Komponenten definiert sind.

## Themen und Verben {#topics-and-verbs}

[Kalenderkomponente](calendar-basics-for-developers.md)SocialEvent `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Kalenderereignis |
| HINZUFÜGEN | Mitgliederkommentare für ein Kalenderereignis |
| UPDATE | Kalenderereignis oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Kalenderereignis oder Kommentar des Mitglieds wird gelöscht |

[Kommentarkomponente](essentials-comments.md)SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Antworten des Mitglieds auf Kommentar |
| UPDATE | Kommentar des Mitglieds wird bearbeitet |
| DELETE | Kommentar des Mitglieds wird gelöscht |

[File Library Component](essentials-file-library.md)SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Ordner |
| ANLAGE | Mitglied lädt eine Datei hoch |
| UPDATE | Mitglied aktualisiert einen Ordner oder eine Datei |
| DELETE | löscht einen Ordner oder eine Datei |

[Forum Component](essentials-forum.md)SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumthema |
| HINZUFÜGEN | Mitgliederantworten zum Forenthema |
| UPDATE | Forenthema oder Antwort des Mitglieds wird bearbeitet |
| DELETE | Forenthema oder Antwort des Mitglieds wird gelöscht |

[Journal Component](blog-developer-basics.md)SocialEvent `topic`= com/adobe/cq/social/Journal

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blog-Artikel |
| HINZUFÜGEN | Kommentare zu einem Blog-Artikel |
| UPDATE | Blog-Artikel oder Kommentar des Mitglieds wird bearbeitet |
| DELETE | Blog-Artikel oder Kommentar des Mitglieds wird gelöscht |

[QnA Component](qna-essentials.md)SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine QnA-Frage |
| HINZUFÜGEN | Mitglied erstellt eine QnA-Antwort |
| UPDATE | Frage oder Antwort des Mitglieds zur Servicequalität des Mitglieds wird bearbeitet |
| SELECT | Antwort des Mitglieds ausgewählt |
| AUSWAHL aufheben | Die Antwort des Mitglieds wird deaktiviert |
| DELETE | Frage oder Antwort des Mitglieds zur Servicequalitätsprüfung wird gelöscht |

[Reviews Component](reviews-basics.md)SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Review |
| UPDATE | Überprüfung des Mitglieds wird bearbeitet |
| DELETE | Überprüfung des Mitglieds wird gelöscht |

[Bewertungskomponente](rating-basics.md)SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| RATING HINZUFÜGEN | Der Inhalt des Mitglieds wurde bewertet |
| RATING ENTFERNEN | der Inhalt des Mitglieds wurde heruntergesetzt |

[Komponente](essentials-voting.md)SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| ABSTIMMUNG HINZUFÜGEN | Der Inhalt des Mitglieds wurde abgestimmt |
| ABSTIMMUNG ENTFERNEN | Inhalt des Mitglieds wurde abgelehnt |

**Moderationsaktivierte Komponenten** SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| DENY | Inhalt des Mitglieds wird verweigert |
| FLAG-AS-INAPPROPRIATE | Inhalt des Mitglieds wird markiert |
| UNFLAG-AS-INAPPROPRIATE | Der Inhalt des Mitglieds ist unmarkiert |
| AKZEPT | Der Inhalt des Mitglieds wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| OPEN | Mitglied öffnet Kommentar erneut |

## Ereignisse für benutzerdefinierte Komponenten {#events-for-custom-components}

Bei einer benutzerdefinierten Komponente muss die abstrakte [SocialEvent-Klasse](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) erweitert werden, um die Ereignisse der Komponente als `actions`die Ereignisse für eine `topic`Komponente aufzuzeichnen.

Das benutzerspezifische Ereignis setzt die Methode außer Kraft, `getVerb()` sodass jeweils ein passender Wert zurückgegeben `verb`wird `action`. Die für eine Aktion `verb` zurückgegebene kann eine häufig verwendete (z. B. `POST`) oder eine für die Komponente spezialisierte (z. B. `ADD RATING`) Aktion sein. Es gibt eine *n-1* Beziehung zwischen `actions`und `verbs`.

>[!NOTE]
>
>Stellen Sie sicher, dass eine benutzerdefinierte Erweiterung mit einer niedrigeren Rangfolge registriert ist als jede vorhandene Implementierung im Produkt.

### Pseudo-Code für benutzerdefiniertes Komponentenereignis {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.Event](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);
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

## Beispiel für EventListener zum Filtern von Aktivitäts-Stream-Daten {#sample-eventlistener-to-filter-activity-stream-data}

Es ist möglich, Ereignisse zu überwachen, um zu ändern, was im Aktivitätsstream angezeigt wird.

Im folgenden Beispiel für Pseudo-Code werden DELETE-Ereignisse für die Kommentarkomponente aus dem Aktivitätsstream entfernt.

### Pseudo-Code für EventListener {#pseudo-code-for-eventlistener}

Erfordert das [neueste Feature Pack](deploy-communities.md#latestfeaturepack).

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

