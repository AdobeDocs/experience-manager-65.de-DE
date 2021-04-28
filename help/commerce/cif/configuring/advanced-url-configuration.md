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
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 91%

---

# Erweiterte URL-Konfigurationen {#url}

[AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) stellen erweiterte Konfigurationen zum Anpassen der URLs für Produkt- und Kategorieseiten bereit. Viele Implementierungen passen diese URLs für die Suchmaschinen-Optimierung (SEO) an. Im folgenden Video wird beschrieben, wie Sie den `UrlProvider`-Service und die Funktionen der [Sling-Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfigurieren, um die URLs für Produkt- und Kategorieseiten anzupassen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Konfiguration {#configuration}

Um den Dienst `UrlProvider` gemäß den SEO-Anforderungen zu konfigurieren und ein Projekt muss eine OSGI-Konfiguration für die &quot;CIF URL Provider-Konfiguration&quot;bereitstellen und den Dienst wie unten beschrieben konfigurieren.

>[!NOTE]
>
> Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) (siehe unten) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren.

### URL-Vorlage der Produktseite {#product}

Damit werden die URLs der Produktseiten mit den folgenden Eigenschaften konfiguriert:

* **Produkt-URL-Vorlage**: definiert das Format von URLs mit einer Reihe von Platzhaltern. Der Standardwert ist `{{page}}.{{url_key}}.html#{{variant_sku}}`, wodurch letztendlich URLs generiert werden, z. B. `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange`, wobei
   * `{{page}}` durch `/content/venia/us/en/products/product-page` ersetzt wurde,
   * `{{url_key}}` durch die `url_key`-Eigenschaft von Magento des Produkts ersetzt wurde, hier `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` durch die aktuell ausgewählte Variante ersetzt wurde, hier `MH01-M-Orange`
* **Speicherort der Produktkennung**: definiert den Speicherort der Kennung, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert lautet `SELECTOR`, der andere mögliche Wert `SUFFIX`. In Bezug auf die vorherige Beispiel-URL bedeutet dies, dass die Kennung `chaz-kangeroo-hoodie` zum Abrufen der Produktdaten verwendet wird.
* **Produktkennungstyp**: definiert den Speicherort der Kennung, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert lautet `URL_KEY`, der andere mögliche Wert `SKU`. In Bezug auf die vorherige Beispiel-URL bedeutet dies, dass die Produktdaten mit einem Magento-GraphQL-Filter wie `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}` abgerufen werden.

### URL-Vorlage für Produktseiten-Listen {#product-list}

Damit werden die URLs der Kategorie- oder Produktlistenseiten mit den folgenden Eigenschaften konfiguriert:

* **Kategorie-URL-Vorlage**: definiert das Format von URLs mit einer Reihe von Platzhaltern. Der Standardwert ist `{{page}}.{{id}}.html`, wodurch letztendlich URLs generiert werden, z. B. `/content/venia/us/en/products/category-page.3.html`, wobei
   * `{{page}}` durch `/content/venia/us/en/products/category-page` ersetzt wurde,
   * `{{id}}` durch die `id`-Eigenschaft von Magento der Kategorie ersetzt wurde, hier `3`
* **Speicherort der Kategoriekennung**: definiert den Speicherort der Kennung, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert lautet `SELECTOR`, der andere mögliche Wert `SUFFIX`. In Bezug auf die vorherige Beispiel-URL bedeutet dies, dass die Kennung `3` zum Abrufen der Produktdaten verwendet wird.
* **Kategoriekennungstyp**: definiert den Speicherort der Kennung, die zum Abrufen der Produktdaten verwendet wird. Der Standardwert und derzeit einzige unterstützte Wert ist `ID`. In Bezug auf die vorherige Beispiel-URL bedeutet dies, dass die Kategoriedaten mit einem Magento-GraphQL-Filter wie `category(id:3)` abgerufen werden.

Es ist möglich, benutzerdefinierte Eigenschaften für jede Vorlage hinzuzufügen, sofern die entsprechenden Daten von den Komponenten, die die Vorlage verwenden, mithilfe des `UrlProvider` festgelegt werden. Überprüfen Sie beispielsweise den Code der Klasse `ProductListItemImpl`, um herauszufinden, wie dieser implementiert wird.

Es ist auch möglich, den `UrlProvider`-Service durch einen vollständig benutzerdefinierten OSGi-Service zu ersetzen. In diesem Fall muss die `UrlProvider`-Oberfläche implementiert und mit einem höheren Service-Rang registriert werden, um die Standardimplementierung zu ersetzen.

## Kombinieren mit Sling-Zuordnungen {#sling-mapping}

Neben `UrlProvider` können auch [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) konfiguriert werden, um URLs neu zu schreiben und zu verarbeiten. Das AEM-Archetyp-Projekt bietet außerdem [eine Beispielkonfiguration](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) zum Konfigurieren einiger Sling-Zuordnungen für Port 4503 (Veröffentlichungsinstanz) und Port 80 (Dispatcher).

## Kombinieren mit AEM Dispatcher {#dispatcher}

URL-Neuschreibungen können auch mithilfe des AEM Dispatcher-HTTP-Servers mit dem Modul `mod_rewrite` erreicht werden. Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) stellt eine AEM Dispatcher-Referenzkonfiguration bereit, die bereits grundlegende [Neuschreibungsregeln](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) für die generierte Größe enthält.

## Beispiel

Das Projekt [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) enthält Beispielkonfigurationen, um die Verwendung benutzerdefinierter URLs für Produkt- und Kategorienseiten zu demonstrieren. Dadurch kann jedes Projekt individuelle URL-Muster für Produktseiten und Kategorien entsprechend ihren SEO-Anforderungen einrichten. Es wird eine Kombination aus CIF-`UrlProvider` und Sling-Zuordnungen verwendet, wie oben beschrieben.

>[!NOTE]
>
>Diese Konfiguration muss an die externe Domain angepasst werden, die vom Projekt verwendet wird. Die Sling-Zuordnungen funktionieren auf Grundlage des Host-Namens und der Domain. Daher ist diese Konfiguration standardmäßig deaktiviert und muss vor der Implementierung aktiviert werden. Benennen Sie dazu den Ordner `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` entsprechend dem verwendeten Domain-Namen um und aktivieren Sie diese Konfiguration, indem Sie `resource.resolver.map.location="/etc/map.publish"` zur `JcrResourceResolver`-Konfiguration des Projekts hinzufügen.

## Zusätzliche Ressourcen

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [AEM-Ressourcenzuordnung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling-Zuordnungen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
