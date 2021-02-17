---
title: Cloud Service-Konfigurationen
seo-title: Cloud Service-Konfigurationen
description: Sie können die vorhandenen Instanzen erweitern und Ihre eigenen Konfigurationen erstellen.
seo-description: Sie können die vorhandenen Instanzen erweitern und Ihre eigenen Konfigurationen erstellen.
uuid: 9d20c3a4-2a12-4d3c-80c3-fcac3137a675
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d25c03bf-6eaa-45f4-ab60-298865935a62
translation-type: tm+mt
source-git-commit: 801d57bbe8a1bede6dcb4bf7884e5f71ddea1e83
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 66%

---


# Cloud Service-Konfigurationen{#cloud-service-configurations}

Konfigurationen sollen die Logik und Struktur für die Speicherung von Dienstkonfigurationen bereitstellen.

Sie können die vorhandenen Instanzen erweitern und Ihre eigenen Konfigurationen erstellen.

## Konzepte {#concepts}

Die Prinzipien, die bei der Entwicklung von Konfigurationen zum Einsatz kommen, basieren auf den folgenden Konzepten:

* Mit Diensten/Adaptern werden die Konfigurationen abgerufen.
* Konfigurationen (z. B. Eigenschaften/Absätze) werden von den übergeordneten Elementen geerbt.
* Die Verweise erfolgen von Analyseknoten nach Pfad.
* Sie sind einfach erweiterbar.
* Hat die Flexibilität, komplexere Konfigurationen zu berücksichtigen, wie z. B. [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Unterstützung für Abhängigkeiten (z. [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)-Plugins benötigen eine [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)-Konfiguration).

## Struktur {#structure}

Der Basispfad von Konfigurationen ist:

`/etc/cloudservices`.

Für jeden Konfigurationstyp werden eine Vorlage und eine Komponente bereitgestellt. Auf diese Weise können Konfigurationsvorlagen nach der Anpassung die meisten Anforderungen erfüllen.

So stellen Sie eine Konfiguration für neue Dienste bereit:

* Erstellen Sie eine Service-Seite in

   `/etc/cloudservices`

* und darunter:

   * eine Konfigurationsvorlage und
   * eine Konfigurationskomponente erstellen.

Die Vorlage und die Komponente müssen `sling:resourceSuperType` von der Basisvorlage erben:

`cq/cloudserviceconfigs/templates/configpage`

bzw. von der Basiskomponente:

`cq/cloudserviceconfigs/components/configpage`

Der Dienstanbieter sollte auch die Dienstseite bereitstellen:

`/etc/cloudservices/<service-name>`

### Vorlage {#template}

Ihre Vorlage erweitert die Basisvorlage:

`cq/cloudserviceconfigs/templates/configpage`

und definiert einen `resourceType`, der auf die angepasste Komponente verweist.

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

Nach dem Einrichten der Vorlage und der Komponente können Sie Ihre Konfiguration hinzufügen, indem Sie unter folgendem Pfad untergeordnete Seiten hinzufügen:

`/etc/cloudservices/<service-name>`

### Inhaltsmodelle {#content-model}

Das Inhaltsmodell wird als `cq:Page` unter:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

Die Konfigurationen werden unter dem Unterknoten `jcr:content` gespeichert.

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

Die Referenzdokumentation zur API finden Sie unter [com.day.cq.wcm.webservicesupport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM-Integration {#aem-integration}

Die verfügbaren Dienste werden auf der Registerkarte **Cloud Services** des Dialogfelds **Seiteneigenschaften** aufgeführt (auf allen Seiten, die von `foundation/components/page` oder `wcm/mobile/components/page` erben).

Die Registerkarte bietet zusätzlich:

* einen Link zu dem Verzeichnis, in dem Sie den Dienst aktivieren können
* die Auswahl einer Konfiguration (untergeordneter Knoten des Dienstes) aus einem Pfad-Feld

#### Kennwortverschlüsselung {#password-encryption}

Beim Speichern der Anmeldedaten der Benutzer für den Dienst sollten alle Kennwörter verschlüsselt werden.

Zu diesem Zweck können Sie ein ausgeblendetes Formularfeld hinzufügen. Dieses Feld sollte die Anmerkung `@Encrypted` im Eigenschaftsnamen enthalten. d. h. für das Feld `password` würde der Name wie folgt geschrieben:

`password@Encrypted`

Diese Eigenschaft wird dann automatisch (mit dem `CryptoSupport`-Dienst) durch den `EncryptionPostProcessor` verschlüsselt.

>[!NOTE]
>
>Dies ist mit den standardmäßigen ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)`-Anmerkungen vergleichbar.

>[!NOTE]
>
>Standardmäßig verschlüsselt `EcryptionPostProcessor` nur `POST`-Anforderungen, die an `/etc/cloudservices` gesendet wurden.

#### Zusätzliche Eigenschaften für die jcr:content-Knoten der Dienstseite {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Referenzpfad zu einer Komponente, die automatisch in die Seite eingefügt werden soll.<br /> Dies wird für zusätzliche Funktionen und JS-Einschlüsse genutzt.<br /> Dazu gehört die Komponente auf der Seite, <br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> auf der sie enthalten ist (normalerweise vor dem  <code>body</code> Tag).<br /> Bei Analytics und Target schließen wir damit zusätzliche Funktionen ein, z. B. JavaScript-Aufrufe, um das Verhalten der Besucher nachzuverfolgen.</td>
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
   <td>Ranking</td>
   <td>Service-Ranking zur Verwendung in Listen.</td>
  </tr>
  <tr>
   <td>selzableChildren</td>
   <td>Filter für die Anzeige von Konfigurationen im Dialogfeld "Seiteneigenschaften".</td>
  </tr>
  <tr>
   <td>serviceUrl</td>
   <td>URL zur Dienst-Website.</td>
  </tr>
  <tr>
   <td>serviceUrlLabel</td>
   <td>Bezeichnung für Dienst-URL.</td>
  </tr>
  <tr>
   <td>thumbnailPath</td>
   <td>Pfad zur Miniaturansicht für den Dienst.</td>
  </tr>
  <tr>
   <td>visible</td>
   <td>Sichtbarkeit im Dialogfeld "Seiteneigenschaften" visible standardmäßig (optional)</td>
  </tr>
 </tbody>
</table>

### Anwendungsfälle {#use-cases}

Diese Dienste werden standardmäßig bereitgestellt:

* [Tracker Snippets](/help/sites-administering/external-providers.md) (Google, WebTrends usw.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [Test&amp;Target](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
* [Search&amp;Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote)
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Siehe auch [Erstellen eines benutzerdefinierten Cloud-Dienstes](/help/sites-developing/extending-cloud-config-custom-cloud.md).

