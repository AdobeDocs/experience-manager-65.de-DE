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
feature: Konfiguration
exl-id: 3eebdd38-da5b-4c38-868a-22c3c7a97b66
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 66%

---

# Ressourcenzuordnung{#resource-mapping}

Die Ressourcenzuordnung wird zur Definition von Umleitungen, Vanity-URLs und virtuellen Hosts für AEM verwendet.

Diese Zuordnungen können Sie beispielsweise folgendermaßen verwenden:

* Setzen Sie allen Anforderungen das Präfix `/content` voran, damit die interne Struktur für die Besucher Ihrer Website ausgeblendet wird.
* Definieren Sie eine Umleitung, damit alle Anforderungen an die `/content/en/gateway`-Seite Ihrer Website an `https://gbiv.com/` umgeleitet werden.

Eine mögliche HTTP-Zuordnung präfixiert alle Anforderungen an `localhost:4503` mit `/content`. Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/we-retail/en/products.html`

mithilfe von:

`localhost:4503/we-retail/en/products.html`

da durch die Zuordnung automatisch das Präfix `/content` zu `/we-retail/en/products.html` hinzugefügt wird.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/site/resources.html) und [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR-Ressourcen-Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

Diese Listen können (zusammen mit Konfigurationsinformationen) unter der Option **JCR ResourceResolver** der Felix-Konsole angezeigt werden. Beispiel: `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuration Zeigt die aktuelle Konfiguration (wie für den [Apache Sling-Ressourcen-Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) definiert) an.

* Configuration Test Hiermit können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries** Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet wird.

* **Mapping Map Entries** Die Liste der Einträge, die von den ResourceResolver.map-Methoden für die Zuordnung von Ressourcenpfaden zu URLs verwendet wird.

Die beiden Listen enthalten verschiedene Einträge, darunter die von der/den Anwendung/en als Standardwerte definierten. Sie dienen häufig dazu, URLs für die Benutzer zu vereinfachen.

Die Listen verbinden ein **Muster**, d. h. einen auf die Anforderung abgestimmten regulären Ausdruck, mit einer **Ersetzung**, die die anzuwendende Umleitung definiert.

So löst beispielsweise das

**Muster** `^[^/]+/[^/]+/welcome$`

das

**Ersatz** `/libs/cq/core/content/welcome.html`.

aus, um die Anforderung

`https://localhost:4503/welcome` &quot;

in:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Neue Zuordnungsdefinitionen werden im Repository erstellt.

>[!NOTE]
>
>Es stehen viele Ressourcen zur Verfügung, mit denen erläutert wird, wie reguläre Ausdrücke definiert werden. zum Beispiel [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

Eine Standardinstallation von AEM umfasst folgenden Ordner:

`/etc/map/http`

Dies ist die Struktur, die beim Definieren von Zuordnungen für das HTPP-Protokoll verwendet wird. Andere Ordner ( `sling:Folder`) können unter `/etc/map` für alle anderen Protokolle erstellt werden, die Sie zuordnen möchten.

#### Konfigurieren einer internen Umleitung an „/content“{#configuring-an-internal-redirect-to-content}

So erstellen Sie die Zuordnung, die einer Anforderung an https://localhost:4503/ mit `/content` vorangestellt ist:

1. Navigieren Sie mit CRXDE zu `/etc/map/http`.

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

Dadurch wird eine Anfrage verarbeitet, z. B.:
`localhost:4503/geometrixx/en/products.html`
wie wenn:
`localhost:4503/content/geometrixx/en/products.html`
wurden beantragt.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren Sling-Eigenschaften und wie diese konfiguriert werden können, finden Sie in der Sling-Dokumentation unter [Ressourcen](https://sling.apache.org/site/mappings-for-resource-resolution.html)

>[!NOTE]
>
>Sie können `/etc/map.publish` verwenden, um die Konfigurationen für die Veröffentlichungsumgebung zu speichern. Diese müssen dann repliziert werden und der neue Speicherort ( `/etc/map.publish`) muss für den **Zuordnungs-Speicherort** des [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) der Veröffentlichungsumgebung konfiguriert sein.
