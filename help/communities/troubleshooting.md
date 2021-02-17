---
title: Fehlerbehebung
seo-title: Fehlerbehebung
description: Fehlerbehebung in der Community einschließlich bekannter Probleme
seo-description: Fehlerbehebung in der Community einschließlich bekannter Probleme
uuid: 99225430-fa2a-4393-ae5a-18b19541c358
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cdb2d80a-2fbf-4ee6-b89b-b5d74e6d3bfc
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 1%

---


# Fehlerbehebung {#troubleshooting}

Dieser Abschnitt enthält allgemeine Bedenken und bekannte Probleme.

## Bekannte Probleme {#known-issues}

### Dispatcher-Refetch ist fehlgeschlagen {#dispatcher-refetch-fails}

Wenn Sie Dispatcher 4.1.5 mit einer neueren Version von Jetty verwenden, kann eine Reflektion dazu führen, dass &quot;Antwort von Remote-Server kann nicht empfangen werden&quot;angezeigt wird, nachdem auf die Anfrage zum Timeout gewartet wurde.

Dieses Problem kann durch die Verwendung von Dispatcher 4.1.6 oder höher behoben werden.

### Kein Zugriff auf Forumsbeiträge nach einem Upgrade von CQ 5.4 {#cannot-access-forum-post-after-upgrading-from-cq}

Wenn ein Forum für CQ 5.4 und veröffentlichte Themen erstellt wurde und die Site dann auf AEM 5.6.1 oder höher aktualisiert wurde, kann der Versuch, die vorhandenen Beiträge Ansicht, zu einem Fehler auf der Seite führen:

Ungültiges Musterzeichen &#39;a&#39;
Anfrage kann nicht an `/content/demoforums/forum-test.html` auf diesem Server gesendet werden, und die Protokolle enthalten Folgendes:

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException:
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

Das Problem besteht darin, dass die Formatzeichenfolge für com.day.cq.commons.date.RelativeTimeFormat zwischen 5.4 und 5.5 geändert wurde, sodass das &quot;a&quot;für &quot;ago&quot;nicht mehr akzeptiert wird.

Daher muss jeder Code, der die RelativeTimeFormat()-API verwendet, Folgendes ändern:

* Von: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* An: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

Der Fehler ist beim Erstellen und Veröffentlichen anders. Beim Autor schlägt er leise fehl und zeigt die Forenthemen einfach nicht an. Beim Veröffentlichen wird der Fehler auf der Seite ausgegeben.

Weitere Informationen finden Sie in der API [com.day.cq.commons.date.RelativeTimeFormat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html).

## Häufige Bedenken {#common-concerns}

### Warnung in Protokollen: Handlebars nicht mehr unterstützt{#warning-in-logs-handlebars-deprecated}

Während des Starts (nicht der 1., sondern danach alle) kann die folgende Warnung in den Protokollen angezeigt werden:

* `11.04.2014 08:38:07.223 WARN [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper 'i18n'` wurde ersetzt durch  `com.adobe.cq.social.handlebars.I18nHelper@15bac645`

Diese Warnung kann unbedenklich ignoriert werden, da `jknack.handlebars.Handlebars`, verwendet von [SCF](scf.md#handlebarsjavascripttemplatinglanguage), mit einem eigenen i18n-Hilfsprogramm geliefert wird. Beim Beginn wird er durch einen AEM spezifischen Helfer [i18n](handlebars-helpers.md#i-n) ersetzt. Diese Warnung wird von der Drittanbieter-Bibliothek generiert, um die Außerkraftsetzung eines vorhandenen Helfers zu bestätigen.

### Warnung in Protokollen: OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

Das Posten einer Reihe von Forumsthemen zu Social Communities kann zu einer enormen Menge an Warn- und Info-Protokollen aus OakResourceListener processOsgiEventQueue führen.

Diese Warnungen können unbedenklich ignoriert werden.

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### Fehler in Protokollen: NoClassDefFoundError für IndexElementFactory {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

Die Aktualisierung von AEM 5.6.1 GA auf die neueste Version von cq-socialgroups-pkg-1.4.x oder auf AEM 6.0 führt zu Fehlern in der Protokolldatei während des Starts für eine Bedingung, die sich selbst löst, wie der Fehler zeigt, der beim Neustart nicht erkannt wird.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
