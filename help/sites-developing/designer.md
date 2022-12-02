---
title: Designs und der Designer
seo-title: Designs and the Designer
description: Sie müssen ein Design für Ihre Website erstellen. In AEM verwenden Sie dazu den Designer.
seo-description: You will need to create a design for your website and in AEM, you do so by using the Designer
uuid: b880ab49-8bea-4925-9b7b-e911ebda14ee
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f9bcb6eb-1df4-4709-bcec-bef0931f797a
exl-id: c81c5910-b6c9-41bd-8840-a6782792701f
source-git-commit: adbdff9ff5b5bd8f5f6b22fb724a0e5273072de2
workflow-type: ht
source-wordcount: '362'
ht-degree: 100%

---

# Designs und der Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In diesem Artikel wird erläutert, wie Sie Websites über die klassische Benutzeroberfläche erstellen. Adobe empfiehlt, die neuesten AEM-Technologien für Ihre Websites zu nutzen, wie ausführlich im Artikel [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md) beschrieben.

Mit dem Designer erstellen Sie mit der [klassischen Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md) in AEM einen Entwurf für Ihre Website.

>[!NOTE]
>
>Weitere Informationen zum Webzugriff finden Sie unter [AEM und Richtlinien für barrierefreien Webzugang](/help/managing/web-accessibility.md).

## Verwenden des Designers {#using-the-designer}

Das Design wird auf der Registerkarte **Tools** im Abschnitt **Designs** definiert:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier erstellen Sie die Struktur, die zum Speichern des Designs erforderlich ist, und laden dann die erforderlichen Cascaded Style Sheet und Bilder hoch.

Designs werden gespeichert unter `/apps/<your-project>`. Der Pfad zu einem Design, das für eine Website verwendet wird, wird anhand der Eigenschaft `cq:designPath` des Knotens `jcr:content` angegeben.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle Änderungen, die im Designmodus an einer Seite vorgenommen werden, werden unterhalb des Designknotens der Website beibehalten und automatisch auf alle Seiten mit demselben Design angewendet.

## Voraussetzungen {#what-you-will-need}

Zur Realisierung des Design benötigen Sie:

**CSS**: Cascading Style Sheets definieren die Formate bestimmter Bereiche auf Ihren Seiten.
**Bild**: Alle Bilder, die Sie für Funktionen wie Hintergrundbilder oder Schaltflächen benötigen.

### Überlegungen zum Entwurf Ihrer Website {#considerations-when-designing-your-website}

Für die Entwicklung einer Website wird nachdrücklich empfohlen, dass Sie Bilder und CSS-Dateien im Ordner `/apps/<your-project>` speichern, damit Sie anhand des aktuellen Designs auf Ihre Ressourcen verweisen können. Der folgende Ausschnitt verdeutlicht dies.

```xml
<%= currentDesign.getPath() + "/static/img/icon.gif %>
```

Das vorstehende Beispiel bietet verschiedene Vorteile:

* Je nach Designpfad verschiedener Websites haben Komponenten ein anderes Erscheinungsbild.
* Die Umgestaltung einer Website erfolgt einfach, indem der Verweis des Designpfads in einen anderen Knoten am Stamm der Website geändert wird, z. B. von `design/v1` in `design/v2.`.

* `/etc/designs` und `/content` sind die einzigen externen URLs, die der Browser erkennt. So sind Sie geschützt vor externen Benutzern, die herauszufinden versuchen, was sich unterhalb Ihrer `/apps`-Baumstruktur befindet. Die obigen URL-Vorteile helfen auch Ihrer bzw. Ihrem Systemadmin, bessere Sicherheitsmaßnahmen einzurichten, weil die Angriffsfläche der Assets auf wenige spezifische Orte beschränkt wird.
