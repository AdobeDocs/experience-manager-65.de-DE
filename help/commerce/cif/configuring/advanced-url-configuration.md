---
title: Erweiterte URL-Konfigurationen
description: Informationen dazu, wie Sie die URLs für Produkt- und Kategorien-Seiten anpassen. Dies ermöglicht es, dass Implementierungen URLs für Suchmaschinen optimieren und ihr Auffinden fördern.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 0125021a-1c00-4ea3-b7fb-1533b7b9f4f2
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 100%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
>Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Deshalb müssen SEO-Thematiken bei vielen AEM-Projekten berücksichtigt werden. Weitere Informationen finden Sie unter [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-65/managing/managing-further-reference/seo-and-url-management.html?lang=de).

Die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) ermöglichen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten. Bei vielen Implementierungen werden diese URLs zwecks Suchmaschinen-Optimierung (Search Engine Optimization, SEO) angepasst. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren können, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den `UrlProvider`-Dienst entsprechend den SEO-Anforderungen und -Bedürfnissen konfigurieren zu können, muss ein Projekt eine OSGI-Konfiguration für die CIF-URL-Anbieter-Konfiguration bereitstellen.

>[!NOTE]
>
>Seit Version 2.0.0 der CIF-Kernkomponenten von AEM bietet die URL-Anbieter-Konfiguration nur vordefinierte URL-Formate anstelle der von den Versionen 1.x bekannten, mit Freitext konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format von Produktseiten {#product}

Dies konfiguriert die URLs der Produktseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (Standard)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Wenn ein [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) vorhanden ist:

* `{{page}}` wird durch `/content/venia/us/en/products/product-page` ersetzt
* wird `{{sku}}` durch die Produkt-SKU ersetzt, z. B. `VP09`
* wird `{{url_key}}` wird durch die `url_key`-Eigenschaft des Produkts ersetzt, z. B. `lenora-crochet-shorts`
* wird `{{url_path}}` durch den `url_path` des Produkts ersetzt, z. B. `venia-bottoms/venia-pants/lenora-crochet-shorts`
* wird `{{variant_sku}}` wird durch die aktuell ausgewählte Variante ersetzt, z. B. `VP09-KH-S`

Da der `url_path` veraltet ist, verwenden die vordefinierten Formate für Produkt-URLs die `url_rewrites` eines Produkts und wählen das Format mit den meisten Pfadsegmenten als Alternative, wenn der `url_path` nicht verfügbar ist.

Mit den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Produktvarianten-URL wie folgt aus: `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### URL-Format von Kategorieseiten {#product-list}

Dies konfiguriert die URLs der Kategorieseiten und unterstützt die folgenden Optionen:

* `{{page}}.html/{{url_path}}.html` (Standard)
* `{{page}}.html/{{url_key}}.html`

Wenn ein [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) vorhanden ist:

* `{{page}}` wird durch `/content/venia/us/en/products/category-page` ersetzt
* wird `{{url_key}}` durch die `url_key`-Eigenschaft der Kategorie ersetzt
* wird `{{url_path}}` durch den `url_path` der Kategorie ersetzt

Mit den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Kategorieseiten-URL wie folgt aus: `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
>Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key` des Produkts oder der Kategorie, getrennt durch Schrägstrich `/`.

### Spezifische Kategorie-/Produktseiten {#specific-pages}

Es ist möglich, [mehrere Kategorie- und Produktseiten](multi-template-usage.md) für nur eine bestimmte Untermenge von Kategorien oder Produkten eines Katalogs zu erstellen.

`UrlProvider` ist so vorkonfiguriert, dass Deep-Links zu bestimmten Kategorie- und Produktseiten in Instanzen der Autorenebene zu erzeugt werden. Dies ist für Editoren nützlich, die eine Site im Vorschaumodus durchsuchen, zu einer bestimmten Produkt- oder Kategorieseite navigieren und zurück in den Bearbeitungsmodus wechseln, um die Seite zu bearbeiten.

Auf Instanzen der Veröffentlichungsebene hingegen sollten Katalogseiten-URLs stabil bleiben, um beispielsweise Verbesserungen bei Suchmaschinen-Rankings nicht zu verlieren. Deshalb rendern Instanzen der Veröffentlichungsebene standardmäßig keine Deep-Links von bestimmten Katalogseiten. Um dieses Verhalten zu ändern, kann die _spezifische Seitenstrategie des CIF-URL-Providers_ so konfiguriert werden, dass immer bestimmte Seiten-URLs erzeugt werden.

## Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt die Service-Schnittstelle [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) oder [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) implementieren und die Implementierung als OSGi-Service registrieren. Diese Implementierungen ersetzen das konfigurierte, vordefinierte Format, sofern verfügbar. Wenn mehrere Implementierungen registriert sind, ersetzt die Implementierung mit dem höheren Service-Ranking die mit dem niedrigeren Service-Ranking.

Die Implementierungen des benutzerdefinierten URL-Formats müssen ein Methodenpaar implementieren, um eine URL aus den angegebenen Parametern zu erstellen bzw. eine URL zu analysieren, um dieselben Parameter zurückzugeben.

## Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetypen-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichung) und Port 80 (Dispatcher).

## Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Beispiel

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. So können für jedes Projekt individuelle URL-Strukturen für Produkt- und Kategorieseiten entsprechend den SEO-Anforderungen eingerichtet werden. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Bereitstellung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=de)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
