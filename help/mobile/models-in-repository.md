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
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 2%

---


# Modelle im Repository{#models-in-repository}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Ein Modell enthält einen Satz von Datentypen, die die Eigenschaften definieren, die letztendlich von Content Services gerendert werden. Ein Modell definiert auch die Beziehungen zwischen anderen Modellen, um die Datenintegrität zu erzwingen.

Als Entwickler sollten Sie mit der Modellstruktur im Repository vertraut sein. Sie können Ihre eigenen Modelle und Entitäten gemäß Ihren App-Anforderungen erstellen.

## Erstellen von Modelltypen {#creating-model-types}

Es gibt zwei vom System bereitgestellte Modelltypen unter */libs/settings/mobileapps/model-types*. Wenn Sie die Systemmodelltypen überschreiben möchten, muss ein Knoten *mobileapps/model-types* unter dem Konfigurationsknoten erstellt werden, unter dem die Überschreibung erfolgen soll.

Wenn Sie beispielsweise Konfigurationen unter */conf/myconf1* und */conf/myconf2* erstellt haben und die Systemmodelltypen nur unter *conf1* überschreiben möchten, erstellen Sie einen *mobileapps/model-types* -Knoten unter den Einstellungen von &lt;a 8/>conf1 *.*

Wenn Sie zulassen möchten, dass einem Modell Datentypen hinzugefügt werden, muss der Modelltyp einen untergeordneten Knoten namens &quot;scaffolding&quot;vom Typ &quot;cq:Page&quot;und einen Ressourcentyp von *wcm/scaffolding/components/scaffolding* haben.

Die Strukturvorlagen-Seite muss auch eine *dataTypesConfig* -Eigenschaft auf dem Knoten PageContent enthalten, die angibt, welche Datentypmodelle von diesem Typ erstellt werden dürfen.

>[!NOTE]
>
>Eine **Strukturvorlage** ist eine Seite, die die Datentypen definiert, die von einer Entität basierend auf dem Modell bearbeitet werden können. Jeder Datentyp kann auch so konfiguriert werden, dass er definiert, wie das Feld in der Benutzeroberfläche angezeigt wird und wie der Datenwert beibehalten wird.

### Konfiguration der Datentypen {#data-types-config}

Der Knoten &quot;data types config&quot;enthält eine Liste von Datentypelementen. Jedes Datentypelement gibt an, wie ein Datentyp im Modell-Editor angezeigt wird und wie er für die spätere Wiedergabe durch eine Entität beibehalten werden muss.

| **Eigenschaftsname** | **Beschreibung** |
|---|---|
| fieldIcon | Klasse des CoralUI-Symbols zur Darstellung des Datentyps |
| fieldPropResourceType | -Komponente, die alle Eigenschaften zum Konfigurieren des Datentyps rendert |
| fieldProperties | Liste mit mehreren Werten für Eigenschaftskomponenten, die verwendet werden, wenn fieldPropResourceType *mobileapps/caas/gui/components/models/editor/datatypes/field* ist |
| fieldResourceType | resourceType des persistenten Knotens für den Datentyp (d. h. die Komponente, die die Eigenschaft im Entitäts-Editor rendert) |
| fieldViewResourceType | Komponente, die zum Rendern des Datentyps in der Ansicht des Modell-Editors verwendet wird (fieldResourceType wird verwendet, wenn diese Eigenschaft weggelassen wird) |
| fieldTitle | Name des Datentyps, der im Modell-Editor angezeigt wird |
| multiFieldResourceType | Ressourcentyp, der auf einem persistenten Knoten verwendet werden soll, wenn mehrere Werte ausgewählt sind |
| renderType | Rendering-Schlüssel für Client-seitiges Rendering |

### Konfigurationsüberlagerung für Datentypen {#data-types-config-overlay}

Die Eigenschaft &quot;dataTypesConfig&quot;unterstützt die Zusammenführung von Sling-Ressourcen. Dies bedeutet, dass die von den Systemmodelltypen (oder sogar von benutzerdefinierten Modelltypen) verwendeten Datentypen mithilfe von Überlagerungsknoten angepasst werden können.

Eine Überlagerung von */libs/settings/mobileapps/models/formbuilderconfig/datatypes* muss erstellt und dann nach Bedarf angepasst werden.

Beispielsweise könnte eine Überlagerung für den Datentyp String hinzugefügt werden, um fieldResourceType in eine benutzerdefinierte Komponente zu ändern.

Weitere Informationen zur Zusammenführung von Sling-Ressourcen finden Sie unter [Verwenden von Sling Resource Merger in AEM](/help/sites-developing/sling-resource-merger.md).

![chlimage_1-7](assets/chlimage_1-7.png)

### Datentypen {#data-types}

Ein Modelldatentyp ist eine Formularkomponente, die Daten einschließen kann, die beim Posten eines Formulars einbezogen werden sollen. Die Datentypkomponente kann beliebig kompliziert sein. Ein Beispiel für einen benutzerdefinierten Datentyp könnte ein Adressblock für ein bestimmtes Land sein, um zu vermeiden, dass dieser immer mit den primitiven Datentypen neu erstellt werden muss.

Siehe &quot;/libs/mobileapps/caas/components/form/contentreference&quot;als Beispiel für einen benutzerdefinierten Datentyp.

Alle primitiven Datentypen verwenden vorhandene Granite-Formularkomponenten. Siehe: [https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html)

Jeder benutzerdefinierte Datentyp kann dann zu einer Datentypkonfiguration hinzugefügt werden, die vom Modell-Editor verwendet werden kann.

## Erstellen von Modellen {#creating-models}

Sie können Modelle erstellen, sobald alle gewünschten Modelltypen und Datentypen entwickelt wurden. Die Autoren verwenden letztendlich Modelle, um Entitäten zu erstellen, aus denen Content Services seine Daten rendern.

Das Erstellen eines Modells besteht darin, einen zulässigen Modelltyp basierend auf der aktuellen Konfiguration auszuwählen und dann einen Titel und eine Beschreibung anzugeben.

Weitere Informationen zum Erstellen und Verwalten eines Modells über das Dashboard finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt zum Erstellen für mobile Apps.

### Eigenschaften eines Modells {#properties-of-a-model}

Die folgende Tabelle zeigt die für ein Modell definierten Eigenschaften:

| **Eigenschaftsname** | **Beschreibung** |
|---|---|
| Modelltitel | Name des Modells |
| Beschreibung | Beschreibung des Modells |
| Miniaturansicht  | Miniaturbild des Modells |
| Modelltyp | Modelltyp (dies kann eine einfache Zeichenfolge oder ein Pfad zu einer tatsächlichen Komponente sein) |
| Zugelassene untergeordnete Elemente | Pfad einer Vorlage, die dieser Vorlage untergeordnet sein darf |
| Zugelassene übergeordnete Elemente | Pfad einer Vorlage, die dieser Vorlage übergeordnet sein darf |

>[!NOTE]
>
>Die Eigenschaften *Zulässige untergeordnete Elemente* und *zulässige übergeordnete Elemente* folgen denselben Regeln wie Seitenvorlagen. Weitere Informationen finden Sie unter [Seitenvorlagen](/help/sites-developing/page-templates-static.md).
>
>Unter Bezugnahme auf die Eigenschaft *Modelltyp* müssen alle Modelle über einen Supertyp von *mobileapps/caas/components/data/entity* verfügen, jedoch über einen Untertyp verfügen, der die Anpassung der Inhaltsbereitstellung ermöglicht. Wenn Sie sicherstellen, dass alle Modelltypen eindeutig sind, können Clients von Content Services auch dabei helfen, zwischen Objekten in den Daten zu unterscheiden.

### Bearbeiten eines Modells {#editing-a-model}

Das Bearbeiten eines Modells umfasst das Öffnen des mit einem Modell zur Bearbeitung verknüpften Dialogfelds für die Strukturvorlage. Im Allgemeinen ist die Strukturvorlage ein untergeordneter Knoten des Modells, kann sich jedoch bei Bedarf außerhalb des Modells befinden, indem der Pfad mithilfe der Eigenschaft &quot;cq:scaffolding&quot;angegeben wird. Dies ist nützlich, wenn Sie dieselbe Strukturvorlage für mehrere Modelle freigeben möchten, für die unterschiedliche Eigenschaften erforderlich sind.

Wenn sich die Strukturvorlage für das Modell befindet, rendert der Modell-Editor alles, was unter &quot;jcr:content/cq:dialog/content&quot;zu finden ist. Derzeit wird von der clientseitigen formbuilder-Engine nur ein statisches Layout mit bis zu 3 Spalten unterstützt. Rechts neben dem Dialogfeld für das wiedergegebene Formular befindet sich eine Liste aller Datentypen, die in der Datentypkonfiguration angegeben sind. Datentypen können durch Anklicken bearbeitet werden. Die rechte Leiste wechselt dann zur Registerkarte &quot;Eigenschaften&quot;für den ausgewählten Datentyp. Neue Datentypen können hinzugefügt werden, indem Sie sie auf die Vorschau-Arbeitsfläche ziehen. Durch Klicken auf Speichern werden die Änderungen auf den Server übertragen. Durch Klicken auf Abbrechen wird der Modell-Editor geschlossen.

>[!NOTE]
>
>Alle Modelle sind Vorlagen, sodass sie allen Vorlagenregeln AEM. Dies ermöglicht die Verwendung von Eigenschaften wie *allowedParents* und *allowedChildren* -Eigenschaften. Diese sind beim Erstellen neuer Entitäten basierend auf einem Modell effektiv. Die Vorlagenregeln stellen sicher, dass Entitäten je nach Hierarchie nur auf bestimmten Modellen basieren können.
>
>Weitere Informationen zum Bearbeiten eines Modells über das Dashboard finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt zum Erstellen für mobile Apps.

### Systemmodelle {#system-models}

Für die einfache Wiederverwendung von Inhalten stehen zwei Arten vordefinierter Systemmodelle zur Verfügung. Diese Modelle können nicht bearbeitet werden.

**Seitenmodell** Das Seitenmodell bietet eine schnelle Methode zur Wiederverwendung vorhandener Inhalte von Sites zur Bereitstellung durch Inhaltsdienste.

Der resourceType der Entitäten, die auf dem Seitenmodell basieren, lautet: mobileapps/caas/components/data/pages

Pfad: Pfad zu einer Sites-Seite. Inhalte aus diesem Pfad (und seinen untergeordneten Elementen) werden von Content Service-Handlern gerendert.

**Asset-** ModellDas Asset-Modell bietet eine schnelle Methode zur Wiederverwendung vorhandener Inhalte aus Assets für die Bereitstellung durch Inhaltsdienste.

Der resourceType der Entitäten, die auf dem Seitenmodell basieren, lautet: *mobileapps/caas/components/data/assets.*

Asset-Liste: Liste der Pfade aus Assets. Jedes Asset wird als untergeordneter Entitätsknoten mit dem Ressourcentyp *wcm/foundation/components/image* hinzugefügt.

>[!NOTE]
>
>Weitere Informationen zur Verwendung dieser Vorlagen zum Erstellen von Modellen über das Dashboard finden Sie unter [Erstellen eines Modells](/help/mobile/administer-mobile-apps.md) im Abschnitt &quot;Authoring&quot;für mobile Apps.
