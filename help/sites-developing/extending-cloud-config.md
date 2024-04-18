---
title: Cloud Service-Konfigurationen
description: Sie können vorhandene Instanzen erweitern, um eigene Konfigurationen zu erstellen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 20a19ee5-7113-4aca-934a-a42c415a8d93
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 44%

---

# Cloud Service-Konfigurationen{#cloud-service-configurations}

Konfigurationen dienen dazu, die Logik und Struktur zum Speichern von Dienstkonfigurationen bereitzustellen.

Sie können die vorhandenen Instanzen erweitern, um Ihre eigenen Konfigurationen zu erstellen.

## Konzepte {#concepts}

Die bei der Entwicklung der Konfigurationen verwendeten Prinzipien basieren auf folgenden Konzepten:

* Dienste/Adapter werden zum Abrufen der Konfigurationen verwendet.
* Konfigurationen (z. B. Eigenschaften/Absätze) werden von den übergeordneten Elementen übernommen.
* Referenziert von Analyseknoten nach Pfad.
* Einfach erweiterbar.
* Sie können auch komplexere Konfigurationen unterstützen, z. B. [Adobe Analytics ](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Unterstützung für Abhängigkeiten (z. B. [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) -Plug-ins benötigen eine [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) Konfiguration).

## Struktur {#structure}

Der Basispfad der Konfigurationen lautet:

`/etc/cloudservices`.

Für jeden Konfigurationstyp werden eine Vorlage und eine Komponente bereitgestellt. Dies ermöglicht Konfigurationsvorlagen, die nach der Anpassung die meisten Anforderungen erfüllen können.

Gehen Sie wie folgt vor, um eine Konfiguration für neue Dienste bereitzustellen:

* Erstellen Sie eine Service-Seite in

  `/etc/cloudservices`

* Darunter:

   * eine Konfigurationsvorlage
   * eine Konfigurationskomponente

Die Vorlage und die Komponente müssen `sling:resourceSuperType` von der Basisvorlage erben:

`cq/cloudserviceconfigs/templates/configpage`

Oder die Basiskomponente

`cq/cloudserviceconfigs/components/configpage`

Der Dienstanbieter sollte auch die Dienstseite bereitstellen:

`/etc/cloudservices/<service-name>`

### Vorlage {#template}

Ihre Vorlage erweitert die Basisvorlage:

`cq/cloudserviceconfigs/templates/configpage`

Und definieren Sie eine `resourceType` , der auf die benutzerdefinierte Komponente verweist.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Komponenten {#components}

Ihre Komponente sollte die Basiskomponente erweitern:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Nachdem Sie Ihre Vorlage und Komponente eingerichtet haben, können Sie Ihre Konfiguration hinzufügen, indem Sie Unterseiten hinzufügen unter:

`/etc/cloudservices/<service-name>`

### Inhaltsmodell {#content-model}

Das Inhaltsmodell wird als `cq:Page` in folgendem Verzeichnis gespeichert:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

Die Konfigurationen werden unter dem untergeordneten Knoten `jcr:content` gespeichert.

* Feste Eigenschaften, die in einem Dialogfeld definiert wurden, sollten direkt auf dem Knoten `jcr:node` gespeichert werden.
* Dynamische Elemente (die `parsys` oder `iparsys` nutzen) speichern die Komponentendaten auf einem untergeordneten Knoten.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Referenzdokumentation zur API finden Sie unter [com.day.cq.wcm.webservicesupport](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM-Integration {#aem-integration}

Verfügbare Dienste sind auf der Registerkarte **Cloud-Services** des Dialogfelds **Seiteneigenschaften** aufgeführt (bei jeder Seite, die von `foundation/components/page` oder `wcm/mobile/components/page` erbt).

Die Registerkarte bietet außerdem Folgendes:

* einen Link zum Speicherort, an dem Sie den Dienst aktivieren können
* eine Konfiguration (Unterknoten des Dienstes) aus einem Pfadfeld auswählen

#### Kennwortverschlüsselung {#password-encryption}

Beim Speichern von Benutzeranmeldeinformationen für den Dienst sollten alle Kennwörter verschlüsselt werden.

Sie können dies erreichen, indem Sie ein ausgeblendetes Formularfeld hinzufügen. Dieses Feld sollte eine Anmerkung enthalten. `@Encrypted` im Eigenschaftsnamen, d. h. für die `password` -Feld würde der Name wie folgt geschrieben:

`password@Encrypted`

Diese Eigenschaft wird dann automatisch (mit dem `CryptoSupport`-Dienst) durch den `EncryptionPostProcessor` verschlüsselt.

>[!NOTE]
>
>Dies ist mit den standardmäßigen ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)`-Anmerkungen vergleichbar.

>[!NOTE]
>
>Standardmäßig verschlüsselt der `EcryptionPostProcessor` nur `POST`-Anfragen an `/etc/cloudservices`.

#### Zusätzliche Eigenschaften für die jcr:content-Knoten der Dienstseite {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Referenzpfad zu einer Komponente, die automatisch in die Seite aufgenommen werden soll.<br /> Dies wird für zusätzliche Funktionen und JS-Einschlüsse genutzt.<br /> Dazu gehört die Komponente auf der Seite, auf der <br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> enthalten ist (normalerweise vor dem <code>body</code>-Tag).<br /> Im Falle von Adobe Analytics und Adobe Target verwenden wir dies, um zusätzliche Funktionen wie JavaScript-Aufrufe zur Verfolgung des Besucherverhaltens einzuschließen.</td>
  </tr>
  <tr>
   <td>description</td>
   <td>Kurze Beschreibung des Dienstes.<br /> </td>
  </tr>
  <tr>
   <td>descriptionExtended</td>
   <td>Erweiterte Beschreibung des Dienstes.</td>
  </tr>
  <tr>
   <td>ranking</td>
   <td>Position des Dienstes in der Rangfolge zur Verwendung in Listen.</td>
  </tr>
  <tr>
   <td>selectableChildren</td>
   <td>Filter zum Anzeigen von Konfigurationen im Dialogfeld „Seiteneigenschaften“</td>
  </tr>
  <tr>
   <td>serviceUrl</td>
   <td>URL zur Website des Dienstes.</td>
  </tr>
  <tr>
   <td>serviceUrlLabel</td>
   <td>Titel für Dienst-URL.</td>
  </tr>
  <tr>
   <td>thumbnailPath</td>
   <td>Pfad zur Miniaturansicht für den Dienst.</td>
  </tr>
  <tr>
   <td>visible</td>
   <td>Sichtbarkeit im Dialogfeld „Seiteneigenschaften“, standardmäßig sichtbar (optional)</td>
  </tr>
 </tbody>
</table>

### Anwendungsfälle {#use-cases}

Diese Dienste werden standardmäßig bereitgestellt:

* [Tracker-Snippets](/help/sites-administering/external-providers.md) (Google, Webtrends usw.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
<!-- Search&Promote is end of life as of September 1, 2022 * [Search&Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote) -->
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Siehe auch [Erstellen eines benutzerdefinierten Cloud-Dienstes](/help/sites-developing/extending-cloud-config-custom-cloud.md).
