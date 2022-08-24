---
title: Implementieren serverseitiger Seitennamen für Analytics
seo-title: Implementing Server-Side Page Naming for Analytics
description: Adobe Analytics verwendet die Eigenschaft „pageName“, um Seiten eindeutig zu identifizieren und die Daten, die für die Seiten erfasst werden, zu verknüpfen.
seo-description: Adobe Analytics uses the s.pageName property to uniquely identify pages and to associate the data that is collected for the pages
uuid: 37b92099-0cce-4b2d-b55c-928f636dbd7e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: be2aa297-5b78-4b1d-8ff1-e6a585a177dd
exl-id: 17a4e4dc-804e-44a9-9942-c37dbfc8016f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 72%

---

# Implementieren serverseitiger Seitennamen für Analytics{#implementing-server-side-page-naming-for-analytics}

Adobe Analytics verwendet die `s.pageName` -Eigenschaft zum eindeutigen Identifizieren von Seiten und zum Verknüpfen der für die Seiten erfassten Daten. Normalerweise führen Sie in AEM die folgenden Aufgaben aus, um dieser Eigenschaft, die AEM an Analytics übermittelt, einen Wert zuzuordnen:

* Verwenden Sie das Framework des Analytics-Cloud-Service, um der Analytics-Eigenschaft `s.pageName` eine CQ-Variable zuzuordnen. (Siehe [Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften](/help/sites-administering/adobeanalytics-mapping.md).

* Gestalten Sie die Seitenkomponente so, dass sie die CQ-Variable enthält, die Sie der Eigenschaft `s.pageName` zuordnen. (Siehe [Implementieren des Adobe Analytics-Trackings für benutzerdefinierte Komponenten](/help/sites-developing/extending-analytics-components.md).

Um Analytics-Berichtsdaten in der Sites-Konsole und in Inhaltseinblicken anzuzeigen, benötigt AEM den Wert der Eigenschaft `s.pageName` für jede Seite. Die AEM Analytics Java-API definiert die `AnalyticsPageNameProvider` -Schnittstelle, die Sie implementieren, um die Sites-Konsole und Inhaltseinblicke mit dem Wert der `s.pageName` -Eigenschaft. Ihr Dienst `AnaltyicsPageNameProvider` löst die Eigenschaft „pageName“ auf dem Server zu Berichtszwecken auf, da sie dynamisch mittels JavaScript auf dem Client aus Gründen der Nachverfolgung festgelegt werden kann.

## Der standardmäßige AnalyticsPageNameProvider-Dienst {#the-default-analytics-page-name-provider-service}

Die `DefaultPageNameProvider` -Dienst ist der Standarddienst, der den Wert der `s.pageName` -Eigenschaft zum Abrufen von Analytics-Daten für eine Seite verwenden. Der Dienst funktioniert in Verbindung mit der AEM Foundation-Seitenkomponente ( `/libs/foundation/components/page`). Diese Seitenkomponente definiert die folgenden CQ-Variablen, die für die Zuordnung zur Eigenschaft `s.pageName` vorgesehen sind:

* `pagedata.path`: Der Wert wird auf den Seitenpfad festgelegt.
* `pagedata.title`: Der Wert wird auf den Seitentitel festgelegt.
* `pagedata.navTitle`: Der Wert wird auf den Seitennavigationstitel festgelegt.

Die `DefaultPageNameProvider` -Dienst bestimmt, welche dieser CQ-Variablen dem `s.pageName` -Eigenschaft im Analytics-Cloud-Service-Framework. Der Dienst bestimmt dann die entsprechende Seiteneigenschaft, die für das Abrufen von Analytics-Berichtsdaten verwendet werden soll:

* `pagedata.path`: Der Dienst verwendet `page.getPath()`

* `pagedata.title`: Der Dienst verwendet `page.getTitle()`

* `pagedata.navTitle`: Der Dienst verwendet `page.getNavigationTitle()`

Die `page` -Objekt ist, ist das [ `com.day.cq.wcm.api.Page`](https://helpx.adobe.com/experience-manager/6-3/sites-developing/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) Java-Objekt für die Seite.

Wenn Sie eine CQ-Variable nicht dem `s.pageName` -Eigenschaft im Framework, der Wert für `s.pageName` wird aus dem Seitenpfad generiert. Beispielsweise die Seite mit dem Pfad `/content/geometrixx/en` verwendet den Wert `content:geometrixx:en` für `s.pageName`.

>[!NOTE]
>
>Der DefaultPageNameProvider-Dienst verwendet das Dienstranking 100.

## Wahren der Kontinuität bei der Analytics-Berichterstellung {#maintaining-continuity-in-analytics-reporting}

Ein vollständiger Verlauf der Analysedaten für eine Seite erfordert, dass sich der Wert der Eigenschaft „s.pageName“ nicht ändert, die für eine Seite verwendet wird. Die Analtyics-Eigenschaften, die die Foundation-Seitenkomponente definiert, können jedoch problemlos geändert werden. Beispielsweise ändert das Verschieben einer Seite den Wert von `pagedata.path`. Damit ist die Kontinuität des Berichtsverlaufs nicht mehr gewahrt:

* Daten, die für den vorherigen Pfad erfasst wurden, sind nicht mehr mit der Seite verknüpft.
* Wenn eine andere Seite den Pfad verwendet, den zuvor eine weitere Seite verwendet hat, erbt die andere Seite die Daten für diesen Pfad.

Um die Kontinuität der Berichterstellung zu wahren, sollte der Wert von `s.pageName` die folgenden Merkmale aufweisen:

* Eindeutig
* Stabil
* Für Menschen lesbar

Beispielsweise kann eine benutzerdefinierte Seitenkomponente eine Seiteneigenschaft enthalten, mit der Autoren eine eindeutige ID für die Seite angeben, die als Wert für die Eigenschaft `s.pageProperties` verwendet wird:

* Die Seite enthält eine Analytics-Variable, die auf den Wert der eindeutigen ID festgelegt ist, die in der Seiteneigenschaft gespeichert ist.
* Die Analytics-Variable ist der Eigenschaft `s.pageProperties` im Analytics-Framework zugeordnet.
* Ihre Implementierung der Schnittstelle „AnalyticsPageNameProvider“ ruft den Wert der Seiteneigenschaft ab, die zum Abfragen der Analytics-Daten der Seite verwendet wird.

>[!NOTE]
>
>Wenden Sie sich an Ihren Analytics-Berater, um Unterstützung beim Entwickeln einer effektiven Strategie für Ihren Wert `s.pageName` zu erhalten.

### Implementieren von AnalyticsPageNameProvider-Diensten {#implementing-an-analytics-page-name-provider-service}

Implementieren Sie die Schnittstelle `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameProvider``s.pageName` als OSGi-Dienst, um die Logik anzupassen, die den Wert der Eigenschaft „“ abruft. Die Sites-Seitenanalyse und Inhaltseinblicke verwenden den Dienst zum Abrufen der Berichtsdaten von Analytics.

Die Schnittstelle „AnalyticsPageNameProvider“ definiert zwei Methoden, die Sie implementieren müssen:

* `getPageName`: Gibt eine `String` -Wert, der den Wert darstellt, der als `s.pageName` -Eigenschaft.

* `getResource`: Gibt eine `org.apache.sling.api.resource.Resource` -Objekt, das die Seite darstellt, die mit dem `s.pageName` -Eigenschaft.

Beide Methoden verwenden `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext` -Objekt als Parameter. Die `AnalyticsPageNameContext`-Klasse stellt Informationen zum Kontext der Analytics-Aufrufe bereit:

* Der Basispfad der Seitenressource.
* Das `Framework`-Objekt für die Konfiguration des Analytics-Cloud-Service.
* Das `Resource`-Objekt für die Seite.
* Das `ResourceResolver`-Objekt für die Seite.

Die Klasse stellt auch einen Setter für den Seitennamen zur Verfügung.

### AnalyticsPageNameProvider-Beispielimplementierung {#example-analyticspagenameprovider-implementation}

Die folgende `AnalyticsPageNameProvider`-Beispielimplementierung unterstützt eine Seitenkomponente:

* Die Komponente erweitert die Foundation-Seitenkomponente.
* Das Dialogfeld enthält ein Feld, mit dem Autoren den Wert der `s.pageName` -Eigenschaft.
* Der Wert der Eigenschaft wird in der Eigenschaft „pageName“ des Knotens `jcr:content` der Seiteninstanzen gespeichert.
* Die Analytics-Eigenschaft, die die Eigenschaft `s.pageName` speichert, hat den Namen `pagedata.pagename`. Die Eigenschaft ist der Eigenschaft `s.pageName` im Analytics-Framework zugeordnet.

Die folgende Implementierung der Methode `getPageName` gibt den Wert der Knoteneigenschaft „pageName“ zurück, wenn die Framework-Zuordnung korrekt konfiguriert ist:

```java
public String getPageName(AnalyticsPageNameContext context) {
        String pageName = null;

        Framework framework = context.getFramework();
        Resource resource = context.getResource();

        if (resource != null && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            Page page = resource.adaptTo(Page.class);
            if (cqVar.equals("pagedata.pagename")) {
                pageName = page.getProperties().get("pageName",null);
            }
        }
        return pageName;
    }
```

Die folgende Implementierung der Methode „getResource“ gibt das Resource-Objekt für die Seite zurück:

```java
     public Resource getResource(AnalyticsPageNameContext context) {
        Resource res = null;

        Framework framework = context.getFramework();
        ResourceResolver resolver = context.getResourceResolver();
        String pageName = context.getPageName();
        String basePath = context.getBasePath();

        if (pageName != null && basePath != null && resolver != null
                && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            if (cqVar.equals("pagedata.pagename")) {
             Iterator<Resource>
             hits = resolver.findResources(createQuery(pageName, basePath, "pagename"), Query.JCR_SQL2);
             if (hits.hasNext()) {
              res = hits.next();
              res = res.getParent();
             }
            }
        }
        return res;
    }

    private String createQuery(String pageName, String basePath, String propName) {
        return "SELECT * FROM [cq:PageContent] WHERE ISDESCENDANTNODE(["
                + basePath + "]) and [" + propName + "] = \"" + pageName + "\"";
    }
```

Der folgende Code repräsentiert die gesamte Klasse, einschließlich der SCR-Anmerkungen, die den Dienst konfigurieren. Beachten Sie, dass der Dienstrang 200 lautet, womit der standardmäßige Dienst überschrieben wird.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2019 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.day.cq.analytics.sitecatalyst;

import java.util.Iterator;

import javax.jcr.query.Query;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.osgi.framework.Constants;
import org.osgi.service.component.annotations.Component;

import com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext;
import com.day.cq.analytics.sitecatalyst.AnalyticsPageNameProvider;
import com.day.cq.analytics.sitecatalyst.Framework;
import com.day.cq.wcm.api.Page;

import static com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext.S_PAGE_NAME;

/**
 * Default implementation of {@link AnalyticsPageNameProvider} that resolves
 * page title, path or navTitle if mapped in {@link Framework}.
 */
@Component(
    service = { AnalyticsPageNameProvider.class },
    property = {
        Constants.SERVICE_DESCRIPTION + "=Example Page Name Resolver implementation",
        Constants.SERVICE_RANKING + ":Integer=200"
    }
)
public class ExamplePageNameProvider implements AnalyticsPageNameProvider {
    public String getPageName(AnalyticsPageNameContext context) {
        String pageName = null;

        Framework framework = context.getFramework();
        Resource resource = context.getResource();

        if (resource != null && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            Page page = resource.adaptTo(Page.class);
            if (cqVar.equals("pagedata.path")) {
                pageName = page.getProperties().get("pageName",null);
            }
        }
        return pageName;
    }

    public Resource getResource(AnalyticsPageNameContext context) {
        Resource res = null;

        Framework framework = context.getFramework();
        ResourceResolver resolver = context.getResourceResolver();
        String pageName = context.getPageName();
        String basePath = context.getBasePath();

        if (pageName != null && basePath != null && resolver != null
                && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            if (cqVar.equals("pagedata.pagename")) {
                Iterator<Resource>
                hits = resolver.findResources(createQuery(pageName, basePath, "pagename"), Query.JCR_SQL2);
                if (hits.hasNext()) {
                    res = hits.next();
                    res = res.getParent();
                }
            }
        }
        return res;
    }

    private String createQuery(String pageName, String basePath, String propName) {
        return "SELECT * FROM [cq:PageContent] WHERE ISDESCENDANTNODE(["
                + basePath + "]) and [" + propName + "] = \"" + pageName + "\"";
    }
}
```
