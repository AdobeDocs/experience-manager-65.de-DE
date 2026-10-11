---
title: Namenskonventionen von Knoten im Java Content-Repository
description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 01c6bb29-1d2d-4a45-b291-0e8d97c01a08
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 100%
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
