---
title: Anpassen der Websites-Konsole (klassische Benutzeroberfläche)
seo-title: Anpassen der Websites-Konsole (klassische Benutzeroberfläche)
description: Die Websites-Administrationskonsole kann zum Anzeigen benutzerdefinierter Spalten erweitert werden.
seo-description: Die Websites-Administrationskonsole kann zum Anzeigen benutzerdefinierter Spalten erweitert werden.
uuid: 9163fdff-5351-477d-b91c-8a74f8b41d34
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: aeb37103-541d-4235-8a78-980b78c8de66
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 64%

---


# Anpassen der Websites-Konsole (klassische Benutzeroberfläche){#customizing-the-websites-console-classic-ui}

## Hinzufügen benutzerdefinierter Spalten zur Websites-Konsole (SiteAdmin){#adding-a-custom-column-to-the-websites-siteadmin-console}

Die Websites-Administrationskonsole kann zum Anzeigen benutzerdefinierter Spalten erweitert werden. Die Konsole basiert auf einem JSON-Objekt, das erweitert werden kann, indem ein OSGi-Dienst erstellt wird, der die Schnittstelle `ListInfoProvider` implementiert. Ein solcher Dienst modifiziert das JSON-Objekt, das an den Client gesendet wird, um die Konsole zu erstellen.

In diesem Schritt-für-Schritt-Tutorial wird erläutert, wie Sie eine neue Spalte in der Websites-Administrationskonsole anzeigen, indem Sie die Schnittstelle `ListInfoProvider` implementieren. Dieser Vorgang umfasst die folgenden Schritte:

1. [Erstellen des OSGi-Diensts](#creating-the-osgi-service) und Bereitstellen des Bundles, das ihn enthält, auf dem AEM-Server
1. (optional) [Testen des neuen Diensts](#testing-the-new-service) durch einen JSON-Aufruf, um das JSON-Objekt anzufordern, das zum Aufbau der Konsole verwendet wird
1. [Anzeigen der neuen Spalte](#displaying-the-new-column) durch Erweitern der Knotenstruktur der Konsole im Repository

>[!NOTE]
>
>Mithilfe dieses Tutorials können auch die folgenden Administrationskonsolen erweitert werden:
>
>* die Konsole für digitale Assets
>* die Community-Konsole

>



### Erstellen von OSGi-Diensten {#creating-the-osgi-service}

Die Schnittstelle `ListInfoProvider` definiert zwei Methoden:

* `updateListGlobalInfo`, um die globalen Eigenschaften der Liste zu aktualisieren,
* `updateListItemInfo`, um ein einzelnes Listenelement zu aktualisieren.

Die Argumente für beide Methoden lauten:

* `request`, das zugeordnete Sling-HTTP-Anforderungsobjekt,
* `info`, das zu aktualisierende JSON-Objekt, bei dem es sich um die globale Liste bzw. das aktuelle Listenelement handelt,
* `resource`, eine Sling-Ressource.

Mit der unten aufgeführten Beispielimplementierung wird Folgendes erreicht:

* Es wird eine Eigenschaft *starred* für jedes Element hinzugefügt, deren Wert auf `true` festgelegt ist, wenn der Seitenname mit *e* beginnt. Andernfalls ist der Wert auf `false` festgelegt.

* Es wird eine Eigenschaft *starredCount* hinzugefügt, die global für die Liste gilt und die Anzahl der Listenelemente mit der Eigenschaft „starred“ enthält.

Gehen Sie wie folgt vor, um den OSGi-Dienst zu erstellen:

1. Wechseln Sie zu CRXDE Lite und [erstellen Sie ein Bundle](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
1. Fügen Sie den unten aufgeführten Beispielcode ein.
1. Erstellen Sie das Bundle.

Der neue Dienste wird ordnungsgemäß ausgeführt.

```java
package com.test;

import com.day.cq.commons.ListInfoProvider;
import com.day.cq.i18n.I18n;
import com.day.cq.wcm.api.Page;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

@Component(metatype = false)
@Service(value = ListInfoProvider.class)
public class StarredListInfoProvider implements ListInfoProvider {

    private int count = 0;

    public void updateListGlobalInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        info.put("starredCount", count);
        count = 0; // reset for next execution
    }

    public void updateListItemInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        Page page = resource.adaptTo(Page.class);
        if (page != null) {
            // Consider starred if page name starts with 'e'
            boolean starred = page.getName().startsWith("e");
            if (starred) {
                count++;
            }
            I18n i18n = new I18n(request);
            info.put("starred", starred ? i18n.get("Yes") : i18n.get("No"));
        }
    }

}
```

>[!CAUTION]
>
>* Ihre Implementierung sollte anhand der bereitgestellten Anforderung und/oder Ressource bestimmen, ob die Informationen zum JSON-Objekt hinzugefügt werden sollen.
>* Wenn Ihre `ListInfoProvider`-Implementierung eine Eigenschaft definiert, die bereits im Antwortobjekt vorhanden ist, wird deren Wert durch den von Ihnen angegebenen Wert überschrieben.

>
>  
Sie können [service ranking](https://www.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) verwenden, um die Ausführungsreihenfolge mehrerer `ListInfoProvider` Implementierungen zu verwalten.

### Testen neuer Dienste {#testing-the-new-service}

Wenn Sie die Website-Administrationskonsole öffnen und durch Ihre Website navigieren, gibt der Browser einen AJAX-Aufruf aus, um das JSON-Objekt zu erhalten, das zum Erstellen der Konsole verwendet wird. For example, when you browse to the `/content/geometrixx` folder, the following request is sent to the AEM server to build the console:

[https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Gehen Sie wie folgt vor, um sicherzustellen, dass der neue Dienst nach der Bereitstellung des Bundles, das ihn enthält, ausgeführt wird:

1. Verweisen Sie Ihren Browser auf die folgende URL:
   [https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. Die Antwort sollte die neuen Eigenschaften wie folgt anzeigen:

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### Anzeigen neuer Spalten {#displaying-the-new-column}

The last step consists in adapting the nodes structure of the Websites Administration console to display the new property for all the Geometrixx pages by overlaying `/libs/wcm/core/content/siteadmin`. Gehen Sie wie folgt vor:

1. In CRXDE Lite, create the nodes structure `/apps/wcm/core/content` with nodes of type `sling:Folder` to reflect the structure `/libs/wcm/core/content`.

1. Kopieren Sie den Knoten `/libs/wcm/core/content/siteadmin` und fügen Sie ihn unten ein `/apps/wcm/core/content`.

1. Kopieren Sie den Knoten `/apps/wcm/core/content/siteadmin/grid/assets` in `/apps/wcm/core/content/siteadmin/grid/geometrixx` und ändern Sie seine Eigenschaften:

   * Entfernen Sie **pageText**.

   * Set **pathRegex** to `/content/geometrixx(/.*)?`
This will make the grid configuration active for all geometrixx websites.

   * Set **storeProxySuffix** to `.pages.json`

   * Bearbeiten Sie die mehrwertige Eigenschaft **storeReaderFields** und fügen Sie den Wert `starred` hinzu.

   * To activate MSM functionality add the following MSM parameters to the multi-String property **storeReaderFields**:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Add a `starred` node (of type **nt:unstructured**) below `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` with the following properties:

   * **dataIndex**: `starred` vom Typ String

   * **header**: `Starred` vom Typ String

   * **xtype**: `gridcolumn` vom Typ String

1. (optional) Drop the columns you do not want to display at `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` ist ein Eitelkeitspfad, der standardmäßig auf `/libs/wcm/core/content/siteadmin`verweist.
To redirect this to your version of siteadmin on `/apps/wcm/core/content/siteadmin` define the property `sling:vanityOrder` to have a value higher than that defined on `/libs/wcm/core/content/siteadmin`. Der Standardwert lautet 300, also sind alle höheren Werte geeignet.

1. Wechseln Sie zur Website Websites Administration Console und navigieren Sie zur Website Geometrixx:
   [https://localhost:4502/siteadmin#/content/geometrixx](https://localhost:4502/siteadmin#/content/geometrixx).

1. Die neue Spalte **Starred** ist nun verfügbar und zeigt benutzerdefinierte Informationen wie folgt an:

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Wenn mehrere Rasterkonfigurationen mit dem durch die Eigenschaft **pathRegex** definierten Pfad übereinstimmen, wird die erste und nicht die spezifischste Eigenschaft verwendet, was bedeutet, dass die Reihenfolge der Konfigurationen wichtig ist.

### Beispielpaket {#sample-package}

The outcome of this tutorial is available in the [Customizing the Websites Administration Console](https://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) package on Package Share.
