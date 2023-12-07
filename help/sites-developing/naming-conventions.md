---
title: Namenskonventionen von Knoten im Java Content Repository
description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 01c6bb29-1d2d-4a45-b291-0e8d97c01a08
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 96%

---

# Benennungskonventionen {#naming-conventions}

Knoten im Repository unterliegen den Benennungskonventionen des [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). AEM erfordert jedoch weitere Konventionen für die Namen von Seitenknoten.

## Benennungskonventionen für Seiten {#naming-conventions-for-pages}

Diese Benennungskonventionen werden auf verschiedenen Ebenen implementiert:

* JcrUtil: die AEM-Implementierung der [JCR-Service-Programme](#jcr-utilities).
* PageManager: der [Seiten-Manager](#page-manager) stellt Methoden für Operationen auf Seitenebene bereit.
* Je nach verwendeter Benutzeroberfläche:

   * [Touch-optimierte Standard-Benutzeroberfläche](#standard-ui)
   * [Klassische Benutzeroberfläche](#classic-ui)

### JCR-Service-Programme {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) ist die AEM-Implementierung der JCR-Service-Programme. Bei der Namensvalidierung sind die Zeichenzuordnungen, die diese Implementierung steuert, und die folgenden Validierungen von besonderem Interesse:

* `isValidName`

   * Stellt sicher, dass der Name nicht leer ist und nur gültige Zeichen enthält.
   * Kann verwendet werden, um zu prüfen, ob ein vorgeschlagener Name gültig ist.

* `createValidName`

   * Erstellt eine gültige Beschriftung aus einer beliebigen Zeichenfolge.
   * Diese Funktion kann verwendet werden, um einen Namen aus einem Titel zu erstellen.

### Seiten-Manager {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) stellt basierend auf [JCRUtil](#jcr-utilities) Methoden für Vorgänge auf Seitenebene bereit.

### Standard-Benutzeroberfläche {#standard-ui}

Die standardmäßige Touch-optimierte Benutzeroberfläche:

* Validiert den Namen entsprechend der Einschränkungen, die PageManager vorgibt, wenn entweder:

   * ein Seitentitel zum Konvertieren in den Knotennamen angegeben ist
   * ein expliziter Knotenname angegeben ist

### Klassische Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche weist stärkere Einschränkungen auf:

* Validiert den Namen für einen expliziten Knotennamen, wenn entweder:

   * ein Seitentitel zum Konvertieren in den Knotennamen angegeben ist
   * ein expliziter Knotenname angegeben ist

* Gültige Zeichen (beim Erstellen innerhalb der klassischen Benutzeroberfläche sind nur diese Zeichen tatsächlich gültig, obwohl `PageManagerImpl` weitere Zeichen erlauben würde):

   * „a“ bis „z“
   * „A“ bis „Z“
   * „0“ bis „9“
   * _ (Unterstrich)
   * `-` (Strich/Minus)
