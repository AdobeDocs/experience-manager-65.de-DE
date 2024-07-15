---
title: Problembehebung in der Community
description: Erfahren Sie mehr über die Fehlerbehebung in der Community, einschließlich bekannter Probleme und Probleme.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: ef4f4108-c485-4e2e-a58f-ff64eee9937e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Problembehebung in der Community {#troubleshooting}

Dieser Abschnitt enthält häufige Probleme und bekannte Probleme bei der Fehlerbehebung in der Community.

## Bekannte Probleme {#known-issues}

### Dispatcher-Neuabruf schlägt fehl {#dispatcher-refetch-fails}

Bei Verwendung von Dispatcher 4.1.5 mit einer neueren Jetty-Version kann eine Refektion dazu führen, dass die Antwort vom Remote-Server nicht empfangen werden kann, nachdem auf die Anfrage gewartet wurde, bis eine Zeitüberschreitung auftritt.

Durch die Verwendung von Dispatcher 4.1.6 oder höher wird dieses Problem behoben.

### Zugriff auf Forum Post nach der Aktualisierung von CQ 5.4 nicht möglich {#cannot-access-forum-post-after-upgrading-from-cq}

Wenn ein Forum in CQ 5.4 erstellt wurde und Themen veröffentlicht wurden und die Site dann auf AEM 5.6.1 oder höher aktualisiert wurde, kann der Versuch, die vorhandenen Beiträge anzuzeigen, zu einem Fehler auf der Seite führen:

Unzulässiges Musterzeichen &#39;a&#39;
Anfrage kann nicht an `/content/demoforums/forum-test.html` auf diesem Server gesendet werden und die Protokolle enthalten Folgendes:

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException:
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

Das Problem besteht darin, dass die Formatzeichenfolge für com.day.cq.commons.date.RelativeTimeFormat zwischen 5.4 und 5.5 geändert wurde, sodass das &quot;a&quot;für &quot;ago&quot;nicht mehr akzeptiert wird.

Daher muss jeder Code, der die RelativeTimeFormat()-API verwendet, Folgendes ändern:

* Von: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* Bis: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

Der Fehler unterscheidet sich in der Autoreninstanz und in Publish. In der Autoreninstanz schlägt es still fehl und zeigt die Forenthemen einfach nicht an. In Publish wird der Fehler auf der Seite ausgegeben.

Weitere Informationen finden Sie in der API [com.day.cq.commons.date.RelativeTimeFormat](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) .

## Häufige Bedenken {#common-concerns}

### Warnung in Protokollen: Handlebars Deprecated {#warning-in-logs-handlebars-deprecated}

Während des Starts (nicht beim ersten, sondern bei jedem weiteren Start) kann die folgende Warnung in den Protokollen angezeigt werden:

* `11.04.2014 08:38:07.223 WARN [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper 'i18n'` wurde durch `com.adobe.cq.social.handlebars.I18nHelper@15bac645` ersetzt

Diese Warnung kann sicher ignoriert werden, da `jknack.handlebars.Handlebars`, verwendet von [SCF](scf.md#handlebarsjavascripttemplatinglanguage), mit einem eigenen i18n-Hilfsprogramm geliefert wird. Beim Start wird er durch einen AEM-spezifischen [i18n-Helfer](handlebars-helpers.md#i-n) ersetzt. Diese Warnung wird von der Bibliothek eines Drittanbieters generiert, um das Außerkraftsetzen eines vorhandenen Helfers zu bestätigen.

### Warnung in Protokollen: OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

Das Posten mehrerer Forumsthemen in Social Communities kann zu großen Mengen von Warn- und Infoprotokollen aus OakResourceListener processOsgiEventQueue führen.

Diese Warnungen können ignoriert werden.

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### Fehler in Protokollen: NoClassDefFoundError für IndexElementFactory {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

Die Aktualisierung von AEM 5.6.1 auf die neueste Version von cq-socialcommunities-pkg-1.4.x oder auf AEM 6.0 führt zu Fehlern in der Protokolldatei. Dies tritt beim Start für eine Bedingung auf, die sich löst, wie der Fehler zeigt, der beim Neustart nicht angezeigt wird.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
