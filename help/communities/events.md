---
title: OSGi-Ereignisse für Communities-Komponenten
description: OSGi-Ereignisse werden gesendet, die asynchrone Listener zum Trigger bringen können
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8049d797-e758-44c2-a89b-51d2b2fca8dc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 6%

---

# OSGi-Ereignisse für Communities-Komponenten  {#osgi-events-for-communities-components}

## Überblick {#overview}

Wenn Mitglieder mit Communities-Funktionen interagieren, werden OSGi-Ereignisse gesendet, die asynchrone Listener wie Benachrichtigungen oder gamification (Bewertung und Badging) zum Trigger bringen können.

Die Instanz [SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) einer Komponente zeichnet die Ereignisse als `actions` auf, die für eine `topic` auftreten. SocialEvent enthält eine Methode zum Zurückgeben eines der Aktion zugeordneten `verb`. Es besteht eine *n-1*-Beziehung zwischen `actions` und `verbs`.

Für die in der Version bereitgestellten Communities-Komponenten beschreiben die folgenden Tabellen die `verbs`, die für jede verfügbare `topic` definiert sind.

## Themen und Verben {#topics-and-verbs}

[Kalenderkomponente](calendar-basics-for-developers.md)
SocialEvent `topic`= com/adobe/cq/social/calendar

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt ein Kalenderereignis |
| HINZUFÜGEN | Kommentar eines Mitglieds zu einem Kalenderereignis |
| AKTUALISIEREN | Kalenderereignis oder Kommentar des Nutzers wird bearbeitet |
| LÖSCHEN | Kalenderereignis oder Kommentar des Nutzers wird gelöscht |

[Komponente „Kommentare](essentials-comments.md)
SocialEvent `topic`= com/adobe/cq/social/comment

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Kommentar |
| HINZUFÜGEN | Antworten des Mitglieds auf den Kommentar |
| AKTUALISIEREN | Kommentar des Nutzers wird bearbeitet |
| LÖSCHEN | Kommentar des Nutzers wird gelöscht |

[Dateibibliothekskomponente](essentials-file-library.md)
SocialEvent `topic`= com/adobe/cq/social/fileLibrary

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Ordner |
| ANHÄNGEN | Mitglied lädt eine Datei hoch |
| AKTUALISIEREN | Mitglied aktualisiert Ordner oder Datei |
| LÖSCHEN | Mitglied löscht einen Ordner oder eine Datei |

[Forenkomponente](essentials-forum.md)
SocialEvent `topic`= com/adobe/cq/social/forum

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Forumsthema |
| HINZUFÜGEN | Antworten von Mitgliedern auf das Forumsthema |
| AKTUALISIEREN | Das Forumsthema oder die Antwort des Mitglieds wurde bearbeitet |
| LÖSCHEN | Das Forumsthema oder die Antwort des Mitglieds wird gelöscht |

[Journalkomponente](blog-developer-basics.md)
SocialEvent `topic`= com/adobe/cq/social/journal

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt einen Blog-Artikel |
| HINZUFÜGEN | Mitgliederkommentare zu einem Blog-Artikel |
| AKTUALISIEREN | Artikel oder Kommentar des Nutzers im Blog bearbeitet |
| LÖSCHEN | Blog-Artikel oder Kommentar des Nutzers wird gelöscht |

[QnA-Komponente](qna-essentials.md)
SocialEvent `topic` = com/adobe/cq/social/qna

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt eine QnA-Frage |
| HINZUFÜGEN | Mitglied erstellt eine QnA-Antwort |
| AKTUALISIEREN | Eine Frage oder Antwort eines Mitglieds wird bearbeitet |
| AUSWÄHLEN | Antwort des Nutzers ist ausgewählt |
| UNSELECT | Die Antwort des Nutzers wurde deaktiviert |
| LÖSCHEN | Eine Frage oder Antwort eines Mitglieds wird gelöscht |

[Reviews-Komponente](reviews-basics.md)
SocialEvent `topic`= com/adobe/cq/social/review

| **Verb** | **Beschreibung** |
|---|---|
| POST | Mitglied erstellt Überprüfung |
| AKTUALISIEREN | Mitgliederbewertung wird bearbeitet |
| LÖSCHEN | Mitgliederbewertung wird gelöscht |

[Bewertungskomponente](rating-basics.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| BEWERTUNG HINZUFÜGEN | Der Inhalt des Abonnenten wurde aktualisiert |
| WERTUNG ENTFERNEN | Der Inhalt des Nutzers wurde als unzureichend eingestuft |

[Abstimmungskomponente](essentials-voting.md)
SocialEvent `topic`= com/adobe/cq/social/tally

| **Verb** | **Beschreibung** |
|---|---|
| ABSTIMMUNG HINZUFÜGEN | Der Inhalt des Mitglieds wurde zur Abstimmung gestellt |
| ABSTIMMUNG ENTFERNEN | Der Inhalt des Mitglieds wurde abgelehnt |

**Moderationsfähige Komponenten**
SocialEvent `topic`= com/adobe/cq/social/moderation

| **Verb** | **Beschreibung** |
|---|---|
| ABLEHNEN | Der Inhalt des Nutzers wird abgelehnt |
| ALS UNGEEIGNET MARKIEREN | Inhalt des Nutzers ist gekennzeichnet |
| UNFLAG-AS-INPROPRIATE | Der Inhalt des Nutzers ist nicht gekennzeichnet |
| AKZEPTIEREN | Der Inhalt des Nutzers wird vom Moderator genehmigt |
| SCHLIESSEN | Mitglied schließt Kommentar zu Bearbeitungen und Antworten |
| ÖFFNEN | Mitglied öffnet Kommentar erneut |

## Ereignisse für benutzerdefinierte Komponenten {#events-for-custom-components}

Für eine benutzerdefinierte Komponente muss die [Abstrakte Klasse SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html) erweitert werden, um die Ereignisse der Komponente als (`actions`, die für eine `topic` auftreten) aufzuzeichnen.

Das benutzerdefinierte Ereignis würde die `getVerb()` überschreiben, sodass für jede `action` ein entsprechender `verb` zurückgegeben wird. Die für eine Aktion zurückgegebene `verb` kann eine häufig verwendete (z. B. `POST`) oder eine für die Komponente spezialisierte (z. B. `ADD RATING`) sein. Es besteht eine *n-1*-Beziehung zwischen `actions`und `verbs`.

>[!NOTE]
>
>Stellen Sie sicher, dass eine benutzerdefinierte Erweiterung mit einem niedrigeren Rang als jede vorhandene Implementierung im Produkt registriert ist.

### Pseudo-Code für benutzerdefiniertes Komponentenereignis {#pseudo-code-for-custom-component-event}

[org.osgi.service.event.](https://osgi.org/javadoc/r4v41/org/osgi/service/event/Event.html);
[com.adobe.cq.social.scf.core.SocialEvent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/scf/core/SocialEvent.html);
[com.adobe.granite.activityStreams.ObjectTypes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ObjectTypes.html);
[com.adobe.granite.activityStreams.Verbs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/Verbs.html);

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

Es ist möglich, Ereignisse zu überwachen, um zu ändern, was im Aktivitäts-Stream angezeigt wird.

Im folgenden Pseudo-Code-Beispiel werden DELETE-Ereignisse für die Komponente „Kommentare“ aus dem Aktivitäts-Stream entfernt.

### Pseudocode für EventListener {#pseudo-code-for-eventlistener}

Erfordert [neuestes Feature Pack](deploy-communities.md#latestfeaturepack).

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
