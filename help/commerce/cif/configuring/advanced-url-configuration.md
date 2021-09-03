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
source-git-commit: fd973cb3693872e4850f860a625cab70553d2754
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 46%

---

# Erweiterte URL-Konfigurationen {#url}

>[!NOTE]
>
> Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Deshalb müssen SEO-Thematiken bei vielen AEM-Projekten berücksichtigt werden. Weitere Informationen finden Sie unter [Best Practices für SEO und URL-Verwaltung](https://experienceleague.adobe.com/docs/experience-manager-65/managing/managing-further-reference/seo-and-url-management.html) .

[AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) stellen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten bereit. Viele Implementierungen passen diese URLs für die Suchmaschinen-Optimierung (SEO) an. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den Dienst `UrlProvider` gemäß den SEO-Anforderungen zu konfigurieren, muss ein Projekt eine OSGi-Konfiguration für die &quot;CIF URL Provider-Konfiguration&quot;bereitstellen.

>[!NOTE]
>
> Seit Version 2.0.0 der AEM CIF-Kernkomponenten bietet die URL-Provider-Konfiguration nur vordefinierte URL-Formate anstelle der von 1.x-Versionen bekannten Freitext-konfigurierbaren Formate. Darüber hinaus wurde die Verwendung von Selektoren zur Übergabe von Daten in URLs durch Suffixe ersetzt.

### URL-Format der Produktseite {#product}

Dadurch werden die URLs der Produktseiten konfiguriert und die folgenden Optionen unterstützt:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (default)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Im Fall von [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` ersetzt durch  `/content/venia/us/en/products/product-page`
* `{{sku}}` wird durch die SKU des Erzeugnisses ersetzt, z. B.  `VP09`
* `{{url_key}}` durch die  `url_key` Eigenschaft des Produkts ersetzt werden, z. B.  `lenora-crochet-shorts`
* `{{url_path}}` durch die des Produkts ersetzt werden,  `url_path`z. B.  `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wird durch die aktuell ausgewählte Variante ersetzt, z. B.  `VP09-KH-S`

Bei den obigen Beispieldaten sieht eine mit dem Standard-URL-Format formatierte Produktvarianten-URL wie `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S` aus.

### URL-Format der Kategorieseite {#product-list}

Dadurch werden die URLs der Kategorie- oder Produktlistenseiten konfiguriert und die folgenden Optionen unterstützt:

* `{{page}}.html/{{url_path}}.html` (Standard)
* `{{page}}.html/{{url_key}}.html`

Im Fall von [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` ersetzt durch  `/content/venia/us/en/products/category-page`
* `{{url_key}}` wird durch die  `url_key` Eigenschaft der Kategorie ersetzt
* `{{url_path}}` wird durch die Kategorie  `url_path`

Bei den obigen Beispieldaten sieht eine Kategorieseiten-URL, die mit dem Standard-URL-Format formatiert ist, wie `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html` aus.

>[!NOTE]
> 
> Der `url_path` ist eine Verkettung aus dem `url_keys` der Vorgänger eines Produkts oder einer Kategorie und dem `url_key`-Schrägstrich des Produkts oder der Kategorie, getrennt durch `/`.

## Benutzerdefinierte URL-Formate {#custom-url-format}

Um ein benutzerdefiniertes URL-Format bereitzustellen, kann ein Projekt die [`UrlFormat`-Schnittstelle](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/UrlFormat.html) implementieren und die Implementierung als OSGi-Dienst registrieren, wobei es entweder als Kategorie- oder Produktseiten-URL-Format verwendet wird. Die Diensteigenschaft `UrlFormat#PROP_USE_AS` gibt an, welche der konfigurierten vordefinierten Formate ersetzt werden sollen:

* `useAs=productPageUrlFormat`ersetzt das konfigurierte URL-Format der Produktseite
* `useAs=categoryPageUrlFormat`ersetzt das konfigurierte Kategorieseiten-URL-Format

Wenn es mehrere Implementierungen von `UrlFormat` gibt, die als OSGi-Dienste registriert sind, ersetzt die Implementierung mit dem höheren Service-Rang die Implementierung mit dem (den) niedrigeren Service-Rang.

Der `UrlFormat` muss ein Paar von Methoden implementieren, um eine URL aus einer gegebenen Parameterzuordnung zu erstellen und eine URL zu analysieren, um dieselbe Parameterzuordnung zurückzugeben. Die Parameter sind dieselben wie oben beschrieben. Nur für Kategorien wird ein zusätzlicher Parameter `{{uid}}` für `UrlFormat` bereitgestellt.

## Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetyp-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichungsinstanz) und Port 80 (Dispatcher).

## Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Beispiel

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Dadurch kann jedes Projekt individuelle URL-Muster für Produkt- und Kategorieseiten entsprechend ihren SEO-Anforderungen einrichten. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Implementierung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
