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
exl-id: c81c5910-b6c9-41bd-8840-a6782792701f
source-git-commit: adbdff9ff5b5bd8f5f6b22fb724a0e5273072de2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 58%

---

# Designs und der Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In diesem Artikel wird beschrieben, wie Sie eine Website basierend auf der klassischen Benutzeroberfläche erstellen. Adobe empfiehlt, die neuesten AEM-Technologien für Ihre Websites zu nutzen, wie ausführlich im Artikel [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md) beschrieben.

Der Designer wird verwendet, um ein Design für Ihre Website mithilfe der [Klassischen Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md) in AEM zu erstellen.

>[!NOTE]
>
>Weitere Informationen zum Webzugriff finden Sie unter [AEM und Richtlinien für barrierefreien Webzugang](/help/managing/web-accessibility.md).

## Verwenden des Designers  {#using-the-designer}

Ihr Design kann im Abschnitt **designs** der Registerkarte **Tools** definiert werden:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier erstellen Sie die Struktur, die zum Speichern des Designs erforderlich ist, und laden dann die erforderlichen Cascaded Style Sheet und Bilder hoch.

Designs werden unter `/apps/<your-project>` gespeichert. Der Pfad zu einem Design, das für eine Website verwendet wird, wird anhand der Eigenschaft `cq:designPath` des Knotens `jcr:content` angegeben.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle Änderungen, die im Designmodus an einer Seite vorgenommen werden, werden unterhalb des Designknotens der Website beibehalten und automatisch auf alle Seiten mit demselben Design angewendet.

## Voraussetzungen  {#what-you-will-need}

Zur Realisierung des Design benötigen Sie:

**CSS**  - Die Cascading Style Sheets definieren die Formate bestimmter Bereiche auf Ihren Seiten.
**Bilder**  - Alle Bilder, die Sie für Funktionen wie Hintergründe und Schaltflächen verwenden.

### Überlegungen zum Entwurf Ihrer Website {#considerations-when-designing-your-website}

Bei der Entwicklung einer Website wird dringend empfohlen, Bilder und CSS-Dateien unter `/apps/<your-project>` zu speichern, damit Sie Ihre Ressourcen basierend auf dem aktuellen Design referenzieren können, wie im folgenden Snippet beschrieben.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Das obige Beispiel bietet mehrere Vorteile:

* Je nach Designpfad verschiedener Websites erwecken Komponenten einen anderen Eindruck.
* Die Neugestaltung der Website kann einfach durch Verweis des Designpfads auf einen anderen Knoten im Stammverzeichnis der Website von `design/v1` zu `design/v2.` vorgenommen werden.

* `/etc/designs` und  `/content` sind die einzigen externen URLs, die der Browser sieht, um Sie vor einem externen Benutzer zu schützen, der neugierig darüber wird, was sich unter Ihrem  `/apps` Baum befindet. Die obigen URL-Vorteile helfen auch Ihrem Systemadministrator, bessere Sicherheitsmaßnahmen einzurichten, weil die Angriffsfläche der Assets auf wenige spezifische Orte beschränkt wird.
