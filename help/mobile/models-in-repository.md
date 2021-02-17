---
title: Modelle im Repository
seo-title: Modelle im Repository
description: 'null'
seo-description: 'null'
uuid: 54f81180-4178-4e33-a6f0-e9e6ea50798e
contentOwner: User
content-type: reference
discoiquuid: ae1a72f4-d8c1-4c75-ba2c-7322f3743b17
noindex: true
redirecttarget: /content/help/en/experience-manager/6-4/mobile/using/administer-mobile-apps
translation-type: tm+mt
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 2%

---


# Modelle in Repository{#models-in-repository}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Ein Modell enthält eine Reihe von Datentypen, die die Eigenschaften definieren, die letztendlich von Content Services wiedergegeben werden. Ein Modell definiert auch die Beziehungen zwischen anderen Modellen, um die Datenintegrität zu erzwingen.

Als Entwickler sollten Sie mit der Modellstruktur im Repository vertraut sein. Sie können Ihre eigenen Modelle und Entitäten gemäß Ihren App-Anforderungen erstellen.

## Erstellen von Modelltypen {#creating-model-types}

Es gibt zwei vom System bereitgestellte Modelltypen unter */libs/settings/mobileapps/model-types*. Wenn Sie die Systemmodelltypen außer Kraft setzen möchten, muss ein Knoten *mobileapps/model-types* unter dem Konfigurationsknoten erstellt werden, auf dem die Außerkraftsetzung erfolgen soll.

Wenn Sie beispielsweise Konfigurationen unter */conf/myconf1* und */conf/myconf2* erstellt haben und die Systemmodelltypen nur auf *conf1* überschreiben möchten, erstellen Sie unter den Einstellungen von *mobileapps/model-types* einen Knoten 8/>conf1 *.*

Wenn Sie zulassen möchten, dass Datentypen zu einem Modell hinzugefügt werden, muss der Modelltyp einen untergeordneten Knoten mit dem Namen &quot;Gerüst&quot;vom Typ &quot;cq:Page&quot;und einen Ressourcentyp von *wcm/scaffolding/components/scaffolding* haben.

Die Gerüstungsseite muss auch eine *dataTypesConfig*-Eigenschaft auf dem Knoten PageContent enthalten, die angibt, dass die von diesem Typ erstellten Datentypen verwendet werden dürfen.

>[!NOTE]
>
>Ein **Gerüst** ist eine Seite, die die Datentypen definiert, die von einer Entität basierend auf dem Modell bearbeitet werden können. Jeder Datentyp kann auch so konfiguriert werden, dass definiert wird, wie das Feld in der Benutzeroberfläche angezeigt wird und wie der Datenwert beibehalten wird.

### Konfiguration der Datentypen {#data-types-config}

Der Knoten &quot;Datentypen konfigurieren&quot;enthält eine Liste von Datentypelementen. Jedes Datentypelement gibt an, wie ein Datentyp im Modelleditor angezeigt wird und wie er für die spätere Wiedergabe durch eine Entität beibehalten werden muss.

| **Eigenschaftsname** | **Beschreibung** |
|---|---|
| fieldIcon | Klasse des CoralUI-Symbols zur Darstellung des Datentyps |
| fieldPropResourceType | Komponente, die alle Eigenschaften zum Konfigurieren des Datentyps ausgibt |
| fieldProperties | Liste von Eigenschaftenkomponenten mit mehreren Werten, die verwendet werden, wenn fieldPropResourceType *mobileapps/caas/gui/components/models/editor/datatypes/field* ist |
| fieldResourceType | resourceType des persistenten Knotens für den Datentyp (d. h. die Komponente, die die Eigenschaft im Entitäts-Editor wiedergibt) |
| fieldViewResourceType | Komponente, die zur Wiedergabe des Datentyps in der Ansicht des Modelleditors verwendet wird (fieldResourceType wird verwendet, wenn diese Eigenschaft weggelassen wird) |
| fieldTitle | Name des Datentyps, der im Modelleditor angezeigt wird |
| multiFieldResourceType | Ressourcentyp, der auf einem persistenten Knoten verwendet wird, wenn Mehrfachwert ausgewählt ist |
| renderType | Rendering-Hinweis für clientseitiges Rendering |

### Datentypkonfigurationsüberlagerung {#data-types-config-overlay}

Die Eigenschaft &#39;dataTypesConfig&#39; unterstützt das Zusammenführen von Sling-Ressourcen. Dies bedeutet, dass die Datentypen, die von den Systemmodelltypen (oder sogar benutzerdefinierten Modelltypen) verwendet werden, mithilfe von Überlagerungsknoten angepasst werden können.

Eine Überlagerung von */libs/settings/mobileapps/models/formbuilderconfig/datatypes* muss erstellt und dann nach Bedarf angepasst werden.

Beispielsweise könnte eine Überlagerung für den Datentyp String hinzugefügt werden, um fieldResourceType in eine benutzerdefinierte Komponente zu ändern.

Weitere Informationen zur Zusammenführung von Sling-Ressourcen finden Sie unter [Verwenden der Sling-Ressourcen-Fusion in AEM](/help/sites-developing/sling-resource-merger.md).

![chlimage_1-7](assets/chlimage_1-7.png)

### Datentypen {#data-types}

Ein Modelldatentyp ist eine Formularkomponente, die Daten einschließen kann, die beim Posten eines Formulars eingeschlossen werden müssen. Die Datentypkomponente kann so kompliziert sein, wie gewünscht. Ein Beispiel für einen benutzerdefinierten Datentyp könnte ein Adressblock für ein bestimmtes Land sein, um zu vermeiden, dass dieser jederzeit mit den primitiven Datentypen neu erstellt werden muss.

Ein Beispiel für einen benutzerdefinierten Datentyp finden Sie unter &quot;/libs/mobileapps/caas/components/form/contentreference&quot;.

Alle Primitive-Datentypen verwenden vorhandene Granite-Formularkomponenten. Siehe: [https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html)

Jeder benutzerdefinierte Datentyp kann dann einer Datentypkonfiguration hinzugefügt werden, damit er vom Modelleditor verwendet werden kann.

## Erstellen von Modellen {#creating-models}

Sie können Beginn beim Erstellen von Modellen erstellen, sobald alle gewünschten Modelltypen und Datentypen entwickelt wurden. Die Autoren verwenden letztendlich Modelle, um Entitäten zu erstellen, aus denen Content Services ihre Daten wiedergeben.

Das Erstellen eines Modells besteht darin, einen zulässigen Modelltyp basierend auf der aktuellen Konfiguration auszuwählen und dann einen Titel und eine Beschreibung anzugeben.

Weitere Informationen zum Erstellen und Verwalten eines Dashboards finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt zum Authoring für mobile Apps.

### Eigenschaften eines Modells {#properties-of-a-model}

Die folgende Tabelle zeigt die für ein Modell definierten Eigenschaften:

| **Eigenschaftsname** | **Beschreibung** |
|---|---|
| Modelltitel | Name des Modells |
| Beschreibung | Beschreibung des Modells |
| Miniaturansicht  | Miniaturansicht des Modells |
| Modelltyp | Modelltyp (kann eine einfache Zeichenfolge oder ein Pfad zu einer tatsächlichen Komponente sein) |
| Zugelassene untergeordnete Elemente | Pfad einer Vorlage, die dieser Vorlage untergeordnet sein darf |
| Zugelassene übergeordnete Elemente | Pfad einer Vorlage, die dieser Vorlage übergeordnet sein darf |

>[!NOTE]
>
>Die Eigenschaften *Zulässige untergeordnete Elemente* und *Zulässige Eltern* folgen denselben Regeln wie Seitenvorlagen. Weitere Informationen finden Sie unter [Seitenvorlagen](/help/sites-developing/page-templates-static.md).
>
>In Bezug auf die Eigenschaft *Modelltyp* müssen alle Modelle über einen Super-Typ von *mobileapps/caas/components/data/entity* verfügen, jedoch über einen Subtyp verfügen, der die Anpassung des Content-Versands ermöglicht. Die Gewährleistung, dass alle Modelltypen eindeutig sind, kann auch Kunden von Content Services helfen, zwischen Objekten in den Daten zu unterscheiden.

### Bearbeiten eines Modells {#editing-a-model}

Das Bearbeiten eines Modells umfasst das Öffnen des mit einem Modell verknüpften Dialogfelds &quot;Gerüst&quot;zur Bearbeitung. Im Allgemeinen ist die Gerüste eine untergeordnete Node des Modells, sie kann sich jedoch, falls gewünscht, außerhalb des Modells befinden, indem ihr Pfad mithilfe der Eigenschaft &quot;cq:scaffolding&quot;angegeben wird. Dies ist nützlich, wenn Sie die gleiche Gerüste für mehrere Modelle verwenden möchten, für die unterschiedliche Eigenschaften erforderlich sind.

Wenn sich das Gerüst für das Modell befindet, rendert der Modelleditor alles, was unter &quot;jcr:content/cq:dialog/content&quot;zu finden ist. Derzeit wird nur ein bis zu 3-Spalten-festes Layout von der clientseitigen Formularersteller-Engine unterstützt. Rechts neben dem Dialogfeld für das wiedergegebene Formular befindet sich eine Liste aller Datentypen, die in der Datentypkonfiguration angegeben sind. Datentypen können durch Klicken bearbeitet werden. Die rechte Leiste wechselt dann zur Registerkarte Eigenschaften des ausgewählten Datentyps. Neue Datentypen können hinzugefügt werden, indem Sie sie auf die Arbeitsfläche der Vorschau ziehen. Durch Klicken auf Speichern werden die Änderungen an den Server weitergeleitet. Durch Klicken auf &quot;Abbrechen&quot;wird der Modelleditor geschlossen.

>[!NOTE]
>
>Alle Modelle sind Vorlagen, sodass sie allen Vorlagenregeln AEM. Dies ermöglicht die Verwendung von Eigenschaften wie *allowedParents* und *allowedChildren*-Eigenschaften. Diese sind beim Erstellen neuer Entitäten, die auf einem Modell basieren, effektiv. Die Vorlagenregeln stellen sicher, dass Entitäten je nach Hierarchie nur auf bestimmten Modellen basieren können.
>
>Weitere Informationen zum Bearbeiten eines Dashboards finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt zum Authoring für mobile Apps.

### Systemmodelle {#system-models}

Für die einfache Wiederverwendung von Inhalten stehen zwei Arten vordefinierter Systemmodelle zur Verfügung. Diese Modelle können nicht bearbeitet werden.

**SeitenmodellDas** Seitenmodell bietet eine schnelle Methode zur Wiederverwendung vorhandener Inhalte von Sites zum Versand durch Inhaltsdienste.

Der resourceType von Entitäten, die auf dem Seitenmodell basieren, lautet: mobileapps/caas/components/data/pages

Pfad: Pfad zu einer Seite &quot;Sites&quot;. Inhalte aus diesem Pfad (und seinen untergeordneten Elementen) werden von Content-Service-Handlern gerendert.

**Assets** ModelDas Assets-Modell bietet eine schnelle Methode, um vorhandene Inhalte aus Assets für den Versand durch Inhaltsdienste wiederzuverwenden.

Der resourceType von Entitäten, die auf dem Seitenmodell basieren, lautet: *mobileapps/caas/components/data/assets.*

Asset-Liste: Liste von Pfaden aus Assets. Jedes Asset wird als untergeordneter Entitätsknoten mit einem resourceType von *wcm/foundation/components/image* hinzugefügt.

>[!NOTE]
>
>Weitere Informationen zur Verwendung dieser Vorlagen zum Erstellen von Modellen aus dem Dashboard finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt zum Authoring für mobile Apps.
