---
title: Ressourcenzuordnung
description: Erfahren Sie, wie Sie mithilfe der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für Adobe Experience Manager definieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
exl-id: 3eebdd38-da5b-4c38-868a-22c3c7a97b66
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 523b1ccd-901e-5e3b-9fa7-f3dfd82463d5
    internal-label: Configuring
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 81%
---
# Ressourcenzuordnung{#resource-mapping}

Die Ressourcenzuordnung wird verwendet, um Umleitungen, Vanity-URLs und virtuelle Hosts für Adobe Experience Manager (AEM) zu definieren.

Diese Zuordnungen können Sie beispielsweise verwenden, um:

* Allen Anfragen das Präfix `/content` voranzustellen, sodass die interne Struktur für Besucher Ihrer Website ausgeblendet wird.
* Eine Umleitung zu definieren, sodass alle Anfragen an die Seite `/content/en/gateway` Ihrer Website zu `https://gbiv.com/` umgeleitet werden.

Bei einer möglichen HTTP-Zuordnung wird allen Anfragen an `localhost:4503` das Präfix `/content` vorangestellt. Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/we-retail/en/products.html`

über:

`localhost:4503/we-retail/en/products.html`

erlaubt, da bei der Zuordnung automatisch das Präfix `/content` zu `/we-retail/en/products.html` hinzufügt wird.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) und [Ressourcen](https://sling.apache.org/documentation/the-sling-engine/resources.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR-Ressourcen-Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

Diese Listen können (zusammen mit Konfigurationsinformationen) unter der Option **JCR ResourceResolver** der Felix-Konsole angezeigt werden. Beispiel: `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Konfiguration
Zeigt die aktuelle Konfiguration (wie für den [Apache Sling Resource Resolver) &#x200B;](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver).

* Konfigurationstest
Auf diese Weise können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries**
Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet werden.

* **Zuordnungseinträge zuordnen**
Die Liste der Einträge, die von den ResourceResolver.map-Methoden zum Zuordnen von Ressourcenpfaden zu URLs verwendet werden.

Die beiden Listen enthalten verschiedene Einträge, darunter die Einträge, die von den Anwendungen als Standardwerte definiert sind. Diese zielen häufig darauf ab, URLs für Benutzende zu vereinfachen.

Das Listen paaren ein **Muster**, d. h. einen regulären Ausdruck, der mit der Anfrage übereinstimmt, mit einem **Ersatz**, der die Umleitung definiert, die durchgesetzt werden soll.

Zum Beispiel löst das

**Muster** `^[^/]+/[^/]+/welcome$`

den

**Ersatz** `/libs/cq/core/content/welcome.html`.

aus, zur Umleitung der Anfrage

`https://localhost:4503/welcome` &grave;&grave;

an:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Neue Zuordnungsdefinitionen werden im Repository erstellt.

>[!NOTE]
>
>Es steht eine Vielzahl von Ressourcen zur Verfügung, die das Definieren regulärer Ausdrücke erläutern, z. B. [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

In einer Standardinstallation von AEM finden Sie den Ordner:

`/etc/map/http`

Dies ist die Struktur, die beim Definieren von Zuordnungen für das HTTP-Protokoll verwendet wird. Wenn Sie Zuordnungen für weitere Protokolle erstellen möchten, können unter `/etc/map` weitere Ordner (`sling:Folder`) erstellt werden.

#### Konfigurieren einer internen Umleitung an /content {#configuring-an-internal-redirect-to-content}

So erstellen Sie eine Zuordnung, die allen Anfragen an https://localhost:4503/ das Präfix `/content`:

1. Navigieren Sie mithilfe von CRXDE zu `/etc/map/http`.

1. Erstellen Sie einen Knoten:

   * **Typ** `sling:Mapping`
     Dieser Knotentyp ist für diese Zuordnungen vorgesehen, seine Verwendung ist jedoch nicht obligatorisch.

   * **Name** `localhost_any`

1. Klicken Sie auf **Alle speichern**.
1. **Fügen Sie diesem Knoten die folgenden Eigenschaften hinzu:**

   * **Name** `sling:match`

     * **Typ** `String`

     * **Wert** `localhost.4503/`

   * **Name** `sling:internalRedirect`

     * **Typ** `String[]`

     * **Wert** `/content/`

1. Klicken Sie auf **Alle speichern**.

Damit wird eine Anfrage wie die folgende verarbeitet:
`localhost:4503/geometrixx/en/products.html`
Als ob:
`localhost:4503/content/geometrixx/en/products.html`
wurde angefordert.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren Sling-Eigenschaften und dazu, wie diese konfiguriert werden können, finden Sie in der Sling-Dokumentation unter [Ressourcen](https://sling.apache.org/documentation/the-sling-engine/resources.html)

>[!NOTE]
>
>Die Konfigurationen für die Veröffentlichungsumgebung können unter `/etc/map.publish` gespeichert werden. Diese müssen repliziert und der neue Speicherort (`/etc/map.publish`) muss für den **Zuordnungs-Speicherort** des [Apache Sling Resource Resolver](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) der Veröffentlichungsumgebung konfiguriert werden.
