---
title: Designs und der Designer
seo-title: Designs und der Designer
description: Sie müssen ein Design für Ihre Website erstellen. In AEM verwenden Sie dazu den Designer.
seo-description: Sie müssen ein Design für Ihre Website erstellen. In AEM verwenden Sie dazu den Designer.
uuid: b880ab49-8bea-4925-9b7b-e911ebda14ee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f9bcb6eb-1df4-4709-bcec-bef0931f797a
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 63%

---


# Designs und der Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In diesem Artikel wird beschrieben, wie Sie eine Website basierend auf der klassischen Benutzeroberfläche erstellen. Adobe empfiehlt, die neuesten AEM-Technologien für Ihre Websites zu nutzen, wie ausführlich im Artikel [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md) beschrieben.

Sie müssen ein Design für Ihre Website erstellen. In AEM verwenden Sie dazu den Designer.

>[!NOTE]
>
>Weitere Informationen zum Webzugriff finden Sie unter [AEM und Richtlinien für barrierefreien Webzugang](/help/managing/web-accessibility.md).

## Verwenden des Designers {#using-the-designer}

Ihr Entwurf kann im Abschnitt **Designs** der Registerkarte **Tools** definiert werden:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier erstellen Sie die Struktur, die zum Speichern des Designs erforderlich ist, und laden dann die erforderlichen Cascaded Style Sheet und Bilder hoch.

Entwürfe werden unter `/etc/designs` gespeichert. Der Pfad zu einem Design, das für eine Website verwendet wird, wird anhand der Eigenschaft `cq:designPath` des Knotens `jcr:content` angegeben.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle Änderungen, die im Designmodus an einer Seite vorgenommen werden, werden unterhalb des Designknotens der Website beibehalten und automatisch auf alle Seiten mit demselben Design angewendet.

## Voraussetzungen  {#what-you-will-need}

Zur Realisierung des Design benötigen Sie:

**CSS**  - Die Cascading Stylesheets definieren die Formate bestimmter Bereiche auf Ihren Seiten.
**Bilder** : Alle Bilder, die Sie für Funktionen wie Hintergründe und Schaltflächen verwenden.

### Überlegungen zum Entwurf Ihrer Website {#considerations-when-designing-your-website}

Beim Entwickeln einer Website wird dringend empfohlen, Bilder und CSS-Dateien unter `/etc/design/<project>` zu speichern, damit Sie auf Ihre Ressourcen basierend auf dem aktuellen Design verweisen können, wie im folgenden Codefragment beschrieben.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Im obigen Angebot werden mehrere Leistungen angeboten:

* Je nach Designpfad verschiedener Websites erwecken Komponenten einen anderen Eindruck.
* Die Neugestaltung der Website kann einfach erfolgen, indem Sie den Designpfad auf einen anderen Knoten im Stammverzeichnis der Website von `design/v1` bis `design/v2.` zeigen.

* `/etc/designs` und  `/content` sind die einzigen externen URLs, die der Browser sieht, um Sie davor zu schützen, dass ein externer Benutzer neugierig darauf wird, was sich unter Ihrem  `/apps` Baum befindet. Die obigen URL-Vorteile helfen auch Ihrem Systemadministrator, bessere Sicherheitsmaßnahmen einzurichten, weil die Angriffsfläche der Assets auf wenige spezifische Orte beschränkt wird.

