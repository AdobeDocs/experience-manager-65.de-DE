---
title: Designs und der Designer
description: Erfahren Sie, wie Sie ein Design für Ihre Website erstellen. In AEM verwenden Sie dazu den Designer.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: c81c5910-b6c9-41bd-8840-a6782792701f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 100%

---

# Designs und der Designer{#designs-and-the-designer}

>[!CAUTION]
>
>In diesem Artikel wird erläutert, wie Sie Websites über die klassische Benutzeroberfläche erstellen. Adobe empfiehlt, für Ihre Websites die neuesten AEM-Technologien zu nutzen, die ausführlich im Artikel [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md) beschrieben werden.

Mit dem Designer erstellen Sie mit der [klassischen Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md) in AEM einen Entwurf für Ihre Website.

>[!NOTE]
>
>Weitere Informationen zum Web-Zugriff finden Sie unter [AEM und die Richtlinien für barrierefreies Webdesign](/help/managing/web-accessibility.md).

## Verwenden des Designers {#using-the-designer}

Das Design wird auf der Registerkarte **Tools** im Abschnitt **Designs** definiert:

![screen_shot_2012-02-01at30237pm](assets/screen_shot_2012-02-01at30237pm.png)

Hier erstellen Sie die Struktur, die zum Speichern des Designs erforderlich ist, und laden dann die erforderlichen Cascaded Style Sheet und Bilder hoch.

Designs werden gespeichert unter `/apps/<your-project>`. Der Pfad zu einem Design, das für eine Website verwendet wird, wird anhand der Eigenschaft `cq:designPath` des Knotens `jcr:content` angegeben.

![chlimage_1-74](assets/chlimage_1-74a.png)

>[!NOTE]
>
>Alle Änderungen, die im Design-Modus an einer Seite vorgenommen werden, werden unterhalb des Design-Knotens der Site beibehalten und automatisch auf alle Seiten mit demselben Design angewendet.

## Voraussetzungen {#what-you-will-need}

Zur Realisierung des Designs benötigen Sie:

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
