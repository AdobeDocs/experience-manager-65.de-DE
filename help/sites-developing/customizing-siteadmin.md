---
title: Anpassen der Websites-Konsole (klassische Benutzeroberfläche)
description: Die Websites-Administrationskonsole kann um die Anzeige benutzerdefinierter Spalten erweitert werden
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: 2b9b4857-821c-4f2f-9ed9-78a1c9f5ac67
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 100%

---

# Anpassen der Websites-Konsole (klassische Benutzeroberfläche){#customizing-the-websites-console-classic-ui}

## Hinzufügen einer benutzerdefinierten Spalte zur Websites-(SiteAdmin)-Konsole. {#adding-a-custom-column-to-the-websites-siteadmin-console}

Die Websites-Administrationskonsole kann um die Anzeige benutzerdefinierter Spalten erweitert werden. Die Konsole basiert auf einem JSON-Objekt, das erweitert werden kann, indem ein OSGi-Dienst erstellt wird, der die Schnittstelle `ListInfoProvider` implementiert. Ein solcher Dienst modifiziert das JSON-Objekt, das an den Client gesendet wird, um die Konsole zu erstellen.

In diesem Schritt-für-Schritt-Tutorial wird erläutert, wie Sie eine neue Spalte in der Websites-Administrationskonsole anzeigen, indem Sie die Schnittstelle `ListInfoProvider` implementieren. Es besteht aus folgenden Schritten:

1. [Erstellen des OSGi-Dienstes](#creating-the-osgi-service) und Bereitstellen des Pakets, das ihn enthält, auf dem AEM-Server.
1. (Optional) [ Testen des neuen Dienstes](#testing-the-new-service) durch Ausgabe eines JSON-Aufrufs, um das JSON-Objekt anzufordern, das zum Erstellen der Konsole verwendet wird.
1. [Anzeigen der neuen Spalte](#displaying-the-new-column) durch Erweitern der Knotenstruktur der Konsole im Repository

>[!NOTE]
>
>Dieses Tutorial kann auch zur Erweiterung der folgenden Administrationskonsolen verwendet werden:
>
>* die Digital Assets-Konsole
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

Es folgt eine Beispielimplementierung unten:

* Es wird eine Eigenschaft *starred* für jedes Element hinzugefügt, deren Wert auf `true` festgelegt ist, wenn der Seitenname mit *e* beginnt. Andernfalls ist der Wert auf `false` festgelegt.

* Es wird die Eigenschaft *starredCount* hinzugefügt, die für die Liste global ist und die Anzahl der markierten Listenelemente enthält.

So erstellen Sie den OSGi-Dienst:

1. [Erstellen Sie ein Bundle](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle) in CRXDE Lite.
1. Fügen Sie den Beispiel-Code unten hinzu.
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
>* Wenn Ihre `ListInfoProvider`-Implementierung eine Eigenschaft definiert, die bereits im Antwortobjekt vorhanden ist, wird ihr Wert durch den von Ihnen angegebenen Wert überschrieben.
>
>  Sie können [service ranking](https://docs.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) verwenden, um die Ausführungsreihenfolge mehrerer `ListInfoProvider` Implementierungen zu verwalten.

### Testen des neuen Dienstes {#testing-the-new-service}

Wenn Sie die Websites-Administrationskonsole öffnen und Ihre Site durchsuchen, gibt der Browser einen Ajax-Aufruf aus, um das JSON-Objekt abzurufen, das zum Erstellen der Konsole verwendet wird. Wenn Sie beispielsweise zum Ordner `/content/geometrixx` navigieren, wird die folgende Anforderung an den AEM-Server gesendet, um die Konsole zu erstellen:

[https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Gehen Sie wie folgt vor, um sicherzustellen, dass der neue Dienst nach der Bereitstellung des Bundles, das ihn enthält, ausgeführt wird:

1. Lassen Sie Ihren Browser auf die folgende URL verweisen:
   [https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. Die Antwort sollte die neuen Eigenschaften wie folgt anzeigen:

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### Anzeigen neuer Spalten {#displaying-the-new-column}

Der letzte Schritt besteht darin, die Knotenstruktur der Websites-Administrationskonsole so anzupassen, dass die neue Eigenschaft für alle Geometrixx-Seiten durch Überlagerung von `/libs/wcm/core/content/siteadmin` angezeigt wird. Gehen Sie wie folgt vor:

1. Erstellen Sie in CRXDE Lite die Knotenstruktur `/apps/wcm/core/content` mit Knoten des Typs `sling:Folder`, um die Struktur `/libs/wcm/core/content` widerzuspiegeln.

1. Kopieren Sie den Knoten `/libs/wcm/core/content/siteadmin` und fügen Sie ihn unter `/apps/wcm/core/content` ein.

1. Kopieren Sie den Knoten `/apps/wcm/core/content/siteadmin/grid/assets` nach `/apps/wcm/core/content/siteadmin/grid/geometrixx` und ändert seine Eigenschaften:

   * Entfernen Sie **pageText**.

   * Legen Sie **pathRegex** auf `/content/geometrixx(/.*)?` fest
Dadurch wird die Rasterkonfiguration für alle Geometrixx-Websites aktiviert.

   * Legen Sie **storeProxySuffix** auf `.pages.json` fest

   * Bearbeiten Sie die mehrwertige Eigenschaft **storeReaderFields** und fügen Sie den Wert `starred` hinzu.

   * Um die MSM-Funktion zu aktivieren, fügen Sie die folgenden MSM-Parameter zu der aus mehreren Zeichenfolgen bestehenden Eigenschaft **storeReaderFields** hinzu:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Fügen Sie einen Knoten `starred` (des Typs **nt:unstructured**) unter `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` mit den folgenden Eigenschaften hinzu:

   * **dataIndex**: `starred` des Typs „String“

   * **header**: `Starred` des Typs „String“

   * **xtype**: `gridcolumn` des Typs „String“

1. (optional) Verschieben Sie die Spalten, die Sie nicht anzeigen möchten, per Drag-and-Drop nach `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` ist ein Vanity-Pfad, der standardmäßig auf `/libs/wcm/core/content/siteadmin` verweist.
Um ihn an Ihre SiteAdmin-Version auf `/apps/wcm/core/content/siteadmin` umzuleiten, definieren Sie die Eigenschaft `sling:vanityOrder` so, dass sie einen höheren Wert aufweist, als auf `/libs/wcm/core/content/siteadmin` definiert ist. Der Standardwert lautet 300, also sind alle höheren Werte geeignet.

1. Wechseln Sie zu Websites-Administrationskonsole und navigieren Sie zur folgenden Geometrixx-Website:
   [https://localhost:4502/siteadmin#/content/geometrixx](https://localhost:4502/siteadmin#/content/geometrixx).

1. Die neue Spalte **Starred** ist nun verfügbar und zeigt benutzerdefinierte Informationen wie folgt an:

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Wenn mehrere Rasterkonfigurationen mit dem von der **pathRegex**-Eigenschaft angeforderten Pfad übereinstimmen, wird die erste verwendet und nicht die spezifischste, was bedeutet, dass die Reihenfolge der Konfigurationen wichtig ist.

### Beispielpaket {#sample-package}

Das Ergebnis dieses Tutorials ist im Paket [Anpassen der Website-Administrationskonsole](https://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) bei Package Share verfügbar.
