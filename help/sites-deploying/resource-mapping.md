---
title: Ressourcenzuordnung
seo-title: Ressourcenzuordnung
description: Erfahren Sie, wie Sie mit der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für AEM definieren.
seo-description: Erfahren Sie, wie Sie mit der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für AEM definieren.
uuid: 2ca2d0e4-6f90-4ecc-82db-26991f08c66f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 3582a4d8-a47b-467a-9e25-cb45f969ec93
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db

---


# Ressourcenzuordnung{#resource-mapping}

Die Ressourcenzuordnung wird zur Definition von Umleitungen, Vanity-URLs und virtuellen Hosts für AEM verwendet.

Diese Zuordnungen können Sie beispielsweise folgendermaßen verwenden:

* Prefix all requests with `/content` so that the internal structure is hidden from the visitors to your website.
* Define a redirect so that all requests to the `/content/en/gateway` page of your website are redirected to `https://gbiv.com/`.

One possible HTTP mapping prefixes all requests to `localhost:4503` with `/content`. Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/we-retail/en/products.html`

mithilfe von:

`localhost:4503/we-retail/en/products.html`

da die Zuordnung automatisch das Präfix `/content` zu `/we-retail/en/products.html`.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/site/resources.html) und [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR-Ressourcen-Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

These lists can be viewed (together with configuration information) under the **JCR ResourceResolver** option of the Felix console; for example, `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuration Zeigt die aktuelle Konfiguration (wie für den [Apache Sling-Ressourcen-Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) definiert) an.

* Configuration Test Hiermit können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries** Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet wird.

* **Mapping Map Entries** Die Liste der Einträge, die von den ResourceResolver.map-Methoden für die Zuordnung von Ressourcenpfaden zu URLs verwendet wird.

Die beiden Listen enthalten verschiedene Einträge, darunter die von der/den Anwendung/en als Standardwerte definierten. Sie dienen häufig dazu, URLs für die Benutzer zu vereinfachen.

Die Listen verbinden ein **Muster**, d. h. einen auf die Anforderung abgestimmten regulären Ausdruck, mit einer **Ersetzung**, die die anzuwendende Umleitung definiert.

So löst beispielsweise das

**Muster**`^[^/]+/[^/]+/welcome$`

das

**Ersatz** `/libs/cq/core/content/welcome.html`.

aus, um die Anforderung

`https://localhost:4503/welcome` ``

wie folgt umzuleiten:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Neue Zuordnungsdefinitionen werden im Repository erstellt.

>[!NOTE]
>
>There are many resources available that help explain how to define regular expressions; for example [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

Eine Standardinstallation von AEM umfasst folgenden Ordner:

`/etc/map/http`

Dies ist die Struktur, die beim Definieren von Zuordnungen für das HTPP-Protokoll verwendet wird. Other folders ( `sling:Folder`) can be created under `/etc/map` for any other protocols that you want to map.

#### Konfigurieren einer internen Umleitung an „/content“{#configuring-an-internal-redirect-to-content}

To create the mapping that prefixes any request to https://localhost:4503/ with `/content`:

1. Using CRXDE navigate to `/etc/map/http`.

1. Erstellen Sie einen neuen Knoten:

   * **Typ** `sling:Mapping` Der Knotentyp ist für diese Zuordnungen bestimmt, seine Verwendung ist jedoch nicht obligatorisch.

   * **Name** `localhost_any`

1. Klicken Sie auf **Alle speichern**.
1. **Fügen Sie** diesem Knoten die folgenden Eigenschaften hinzu:

   * **Name** `sling:match`

      * **Typ** `String`

      * **Wert** `localhost.4503/`
   * **Name** `sling:internalRedirect`

      * **Typ** `String`

      * **Wert** `/content/`


1. Klicken Sie auf **Alle speichern**.

Dies behandelt eine Anforderung wie:
als`localhost:4503/geometrixx/en/products.html`ob:
Sie`localhost:4503/content/geometrixx/en/products.html`wurden beantragt.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren Sling-Eigenschaften und wie diese konfiguriert werden können, finden Sie in der Sling-Dokumentation unter [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html)

>[!NOTE]
>
>You can use `/etc/map.publish` to hold the configurations for the publish environment. These must then be replicated, and the new location ( `/etc/map.publish`) configured for the **Mapping Location** of the [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) of the publish environment.

