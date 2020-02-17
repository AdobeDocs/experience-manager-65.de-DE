---
title: Verwenden von Tags
seo-title: Verwenden von Tags
description: Tags bieten eine schnelle und einfache Methode zur Klassifizierung von Inhalten innerhalb einer Website.
seo-description: Tags bieten eine schnelle und einfache Methode zur Klassifizierung von Inhalten innerhalb einer Website.
uuid: 5d922443-f924-426e-acf4-27dffd1053f6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 9fb6d603-eb17-4192-bfa6-6c316f14ac7d
docset: aem65
translation-type: tm+mt
source-git-commit: 2d7492cdee9f7f730dfa6ad2ffae396b3a737b15

---


# Verwenden von Tags{#using-tags}

Tags bieten eine schnelle und einfache Methode zur Klassifizierung von Inhalten innerhalb einer Website. Tags können als Keywords oder Beschriftungen betrachtet werden, die einer Seite, einem Asset oder einem anderen Inhalt zugeordnet werden können, um Suchen zu ermöglichen und dadurch Inhalte und verwandte Inhalte zu finden.

* See [Administering Tags](/help/sites-administering/tags.md) for information about creating and managing tags, as well as to which content tags have been applied.
* See [Tagging for Developers](/help/sites-developing/tags.md) for information about the tagging framework as well as including and extending tags in custom applications.

## Zehn Gründe für das Verwenden von Tags {#ten-reasons-to-use-tagging}

1. **Inhaltsorganisierung** - Tagging erleichtert Autoren das Leben, da sie Inhalte mit wenig Aufwand schnell organisieren können.
1. **Tags** organisieren - Während Tags Inhalte organisieren, organisieren hierarchische Taxonomien/Namespaces Tags.
1. **Sehr organisierte Tags** - Mit der Möglichkeit, Tags und Untertags zu erstellen, können ganze taxonomische Systeme mit Begriffen, Subbegriffen und deren Beziehungen ausgeprägt werden. Dies ermöglicht die Erstellung einer zweiten (oder dritten) Inhaltshierarchie parallel zur offiziellen Inhaltshierarchie.
1. **Kontrolliertes Tagging** - Tagging kann gesteuert werden, indem Berechtigungen auf Tags und/oder Namespaces zur Steuerung der Tag-Erstellung und -Anwendung angewendet werden.
1. **Flexibles Tagging** - Tags haben viele Namen und Gesichter: Tags, taxonomische Begriffe, Kategorien, Etiketten und vieles mehr. Ihr Inhaltsmodell und ihre Verwendung flexibel und können an die jeweiligen Bedürfnisse angepasst werden, z. B. bei der Zielgruppendefinition, der Kategorisierung und Bewertung von Inhalten oder bei der Erstellung sekundärer Inhaltshierarchien.
1. **Verbesserte Suche** - Die Standardsuchkomponente in AEM umfasst im Wesentlichen erstellte Tags und angewendete Tags, auf die Filter angewendet werden können, um die Ergebnisse auf die relevanten einzuschränken.
1. **SEO-Aktivierung** - Tags, die als Seiteneigenschaften angewendet werden, werden automatisch in den Metatags der Seite angezeigt, sodass sie für Suchmaschinen sichtbar sind.
1. **Einfache Eleganz** - Tags können einfach aus einem Wort und dem Touch einer Schaltfläche erstellt werden. Danach können ein Titel, eine Beschreibung und eine unbegrenzte Anzahl von Beschriftungen hinzugefügt werden, um mehr semantische Informationen für das Tag bereitzustellen.
1. **Kernkonsistenz** - Das Tagging-System ist eine Kernkomponente von AEM und wird von allen AEM-Funktionen zur Kategorisierung von Inhalten verwendet. Darüber hinaus ist die Tagging-API für Entwickler zum Erstellen Tagging-fähiger Anwendungen mit Zugriff auf dieselben Taxonomien verfügbar.
1. **Kombiniert Struktur und Flexibilität** - AEM ist aufgrund der Verschachtelung von Seiten und Pfaden ideal für die Arbeit mit strukturierten Informationen. Es ist wegen der integrierten Volltextsuche genauso leistungsfähig, was das Arbeiten mit unstrukturierten Informationen angeht. Tagging kombiniert die Stärken der Struktur und Flexibilität.

Wenn Sie die Inhaltsstruktur für eine Website oder das Metadatenschema für Assets entwerfen, sollten Sie den leichten und zugänglichen Ansatz berücksichtigen, den Tagging bietet.

## Anwenden von Tags {#applying-tags}

In the author environment, authors may apply tags by accessing the page properties and entering one or more tags in the **Tags/Keywords** field.

To apply [pre-defined tags](/help/sites-administering/tags.md), in the **Page Properties** window use the **Tags** field and the **Select Tags** window. The **Standard Tags** tab is the default namespace, which means there is no `namespace-string:` prefixed to the taxonomy.

![chlimage_1-41](assets/chlimage_1-41.png)

### Veröffentlichen von Tags {#publishing-tags}

Wie bei Seiten können die folgenden Aufgaben für Tags und Namespaces durchgeführt werden:

**Aktivieren**

* Einzelne Tags können aktiviert werden.

   Genau wie Seiten müssen neu erstellte Tags zuerst aktiviert werden, bevor sie in einer Veröffentlichungsumgebung verfügbar sind.

>[!NOTE]
>
>Wenn Sie eine Seite aktivieren, wird automatisch ein Dialogfeld geöffnet, in dem Sie inaktivierte Tags aktivieren können, die zur Seite gehören.

**Deaktivieren**

* Deaktivieren Sie die ausgewählten Tags.
