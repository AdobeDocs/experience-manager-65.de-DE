---
title: Erstellen eines benutzerdefinierten Index für Verweise auf adaptive Formulare
description: Erfahren Sie, wie Sie in AEM Forms einen getaggten Lucene-Index für Referenzabfragen für adaptive Formulare erstellen, um Durchlaufabfragen beim Veröffentlichen von Experience Fragments zu vermeiden.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, Developer
source-git-commit: 9240de61985dc32f17593f416e5d054cadb8a392
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 1%
---

# Erstellen eines benutzerdefinierten Index für Verweise auf adaptive Formulare {#create-custom-index-for-adaptive-forms-references}

Erstellen Sie einen getaggten Lucene-Index, um Durchlaufabfragen zu vermeiden, wenn Adobe Experience Manager (AEM) Forms Verweise auf adaptive Formulare auflöst. Ohne einen geeigneten Index kann das Veröffentlichen eines Experience Fragments, das einen Verweis auf ein adaptives Formular enthält, eine `Traversal query (query without index)` in den Protokollen auslösen.

In AEM Forms 6.5.24.0 und höher verwendet die Referenzabfrage das `aemformsAFReferences` Index-Tag. Diese Versionen enthalten die Abfrageänderung, Sie müssen jedoch einen benutzerdefinierten Index mit diesem Tag erstellen. Dieser Artikel zeigt, wie Sie den Index definieren und bereitstellen.

Informationen zu AEM Forms 6.5 LTS finden Sie unter [Erstellen eines benutzerdefinierten Index für Verweise auf adaptive Formulare in AEM Forms 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/install-aem-forms/configure-aem-forms/create-custom-index-for-adaptive-forms-references).

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen, stellen Sie Folgendes sicher:

* AEM Forms 6.5.24.0 oder höher, wobei das entsprechende Forms-Add-on installiert ist.
* Zugriff zum Erstellen eines Index unter `/oak:index` auf der Autoreninstanz.
* Ein AEM-Projekt mit einem `ui.apps`, wenn Sie den Index über ein Inhaltspaket bereitstellen oder auf CRXDE Lite als Entwicklungsalternative zugreifen.

Testen Sie den Index in einer Entwicklungs- oder Staging-Umgebung, bevor Sie ihn in der Produktion bereitstellen. [Die Erstellung eines Index kann bei einem großen Repository einige Zeit in Anspruch nehmen](/help/sites-deploying/queries-and-indexing.md#configuring-the-indexes).

## Definieren des benutzerdefinierten Index {#define-the-custom-index}

Erstellen Sie den Index unter `/oak:index/customAFReferenceLuceneIndex-1`. Sie können einen anderen Indexknotennamen auswählen, das `aemformsAFReferences`-Tag jedoch unverändert lassen, damit die Forms-Referenzabfrage den Index auswählen kann.

Verwenden Sie die folgende Definition. Er indiziert `sling:resourceType` auf `nt:unstructured` Knoten unter `/content`.

```json
{
  "jcr:primaryType": "oak:QueryIndexDefinition",
  "selectionPolicy": "tag",
  "compatVersion": 2,
  "includedPaths": ["/content"],
  "queryPaths": ["/content"],
  "tags": ["aemformsAFReferences"],
  "type": "lucene",
  "async": ["async"],
  "evaluatePathRestrictions": true,
  "reindex": false,
  "indexRules": {
    "jcr:primaryType": "nt:unstructured",
    "nt:unstructured": {
      "jcr:primaryType": "nt:unstructured",
      "properties": {
        "jcr:primaryType": "nt:unstructured",
        "resourceType": {
          "jcr:primaryType": "nt:unstructured",
          "propertyIndex": true,
          "name": "sling:resourceType"
        }
      }
    }
  }
}
```

`analyzed=true` nicht hinzufügen. Die Referenzabfrage verwendet Eigenschaftsbeschränkungen anstelle einer Volltext-`contains`, sodass die Einstellung nicht erforderlich ist.

## Bereitstellen des Index mit einem Inhaltspaket {#deploy-the-index-with-a-content-package}

Verwenden Sie ein Inhaltspaket für Produktionsbereitstellungen.

1. Erstellen Sie im `ui.apps` Ihres AEM-Projekts `ui.apps/src/main/content/jcr_root/_oak_index/customAFReferenceLuceneIndex-1/`.
1. Erstellen Sie `.content.xml` in diesem Verzeichnis mit der folgenden Definition:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0"
             xmlns:jcr="http://www.jcp.org/jcr/1.0"
             xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
             jcr:primaryType="oak:QueryIndexDefinition"
             async="[async]"
             compatVersion="{Long}2"
             evaluatePathRestrictions="{Boolean}true"
             includedPaths="[/content]"
             queryPaths="[/content]"
             reindex="{Boolean}false"
             selectionPolicy="tag"
             tags="[aemformsAFReferences]"
             type="lucene">
       <indexRules jcr:primaryType="nt:unstructured">
           <nt:unstructured jcr:primaryType="nt:unstructured">
               <properties jcr:primaryType="nt:unstructured">
                   <resourceType jcr:primaryType="nt:unstructured"
                                 name="sling:resourceType"
                                 propertyIndex="{Boolean}true"/>
               </properties>
           </nt:unstructured>
       </indexRules>
   </jcr:root>
   ```

1. Fügen Sie den folgenden Filter innerhalb des vorhandenen `workspaceFilter` in `ui.apps/src/main/content/META-INF/vault/filter.xml` hinzu. Die anderen Filter des Projekts bleiben unverändert.

   ```xml
   <filter root="/oak:index/customAFReferenceLuceneIndex-1"/>
   ```

1. Erstellen Sie das Projekt mit der vorhandenen Build-Konfiguration und installieren Sie das resultierende Inhaltspaket auf der Autoreninstanz. Informationen zu Paket-Upload und Installationsanweisungen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system).
1. Bestätigen Sie, dass `/oak:index/customAFReferenceLuceneIndex-1` vorhanden ist. Zulassen, dass die asynchrone Indizierung abgeschlossen wird, bevor der Abfrageplan überprüft wird.

Wenn Sie einen anderen Indexnamen ausgewählt haben, verwenden Sie diesen Namen durchgängig im Verzeichnis, im Filter und im Repository-Pfad.

## Erstellen des Index mit CRXDE Lite {#create-the-index-with-crxde-lite}

Verwenden Sie diese Alternative in einer Entwicklungsumgebung anstelle der Content-Package-Methode.

Verwenden Sie beim Erstellen des Indexknotens die folgenden Eigenschaften:

| Eigenschaft | Typ | Wert |
| --- | --- | --- |
| `selectionPolicy` | Zeichenfolge | `tag` |
| `compatVersion` | Long | `2` |
| `includedPaths` | `String[]` | `/content` |
| `queryPaths` | `String[]` | `/content` |
| `tags` | `String[]` | `aemformsAFReferences` |
| `type` | Zeichenfolge | `lucene` |
| `async` | `String[]` | `async` |
| `evaluatePathRestrictions` | Boolescher Wert | `true` |
| `reindex` | Boolescher Wert | `false` |

`String[]` bedeutet eine String-Eigenschaft mit mehreren Werten, auch wenn sie nur einen Wert enthält.

1. Öffnen Sie `http://localhost:4502/crx/de/index.jsp`. Ersetzen Sie den Host und Port durch die Ihrer Autoreninstanz.
1. Navigieren Sie zu `/oak:index`. Klicken Sie mit der rechten Maustaste auf den Knoten und wählen [!UICONTROL Erstellen] > [!UICONTROL Knoten erstellen].
1. Erstellen Sie `customAFReferenceLuceneIndex-1` mit dem Typ `oak:QueryIndexDefinition`.
1. Fügen Sie die Eigenschaften aus der obigen Tabelle zum Indexknoten hinzu.
1. Erstellen Sie unter dem Indexknoten die folgende Hierarchie untergeordneter Knoten. Legen Sie den Typ jedes untergeordneten Knotens auf `nt:unstructured` fest:

   ```text
   indexRules
       nt:unstructured
           properties
               resourceType
   ```

1. Fügen Sie auf `resourceType` `name` (Zeichenfolge) mit dem Wert `sling:resourceType` und `propertyIndex` (Boolesch) mit dem Wert `true` hinzu.
1. Wählen Sie [!UICONTROL Alle speichern] und warten Sie, bis die asynchrone Indizierung abgeschlossen ist.

## Stellen Sie sicher, dass die Abfrage den Index verwendet {#verify-that-the-query-uses-the-index}

Überprüfen Sie den Abfrageplan, um sicherzustellen, dass die Referenzabfrage Ihren benutzerdefinierten Index auswählt.

1. Vergewissern Sie sich, dass die asynchrone Indizierung abgeschlossen ist. Verwenden [Index-Manager](/help/sites-administering/operations-dashboard.md#the-index-manager), um den Indexstatus zu überprüfen.
1. Öffnen Sie [!UICONTROL Tools] > [!UICONTROL Vorgänge] > [!UICONTROL Diagnose] > [!UICONTROL Abfrageleistung] und wählen Sie [!UICONTROL Abfrage erläutern]. Wählen Sie die XPath-Abfragesprache aus und geben Sie Folgendes ein:

   ```text
   /jcr:root/content//element(*, nt:unstructured)[
     (@sling:resourceType = 'fd/af/components/aemform'
     or jcr:like(@sling:resourceType, '%components/aemformscontainer%')
     or jcr:like(@sling:resourceType, '%components/adaptiveForm/fragment%'))]
   option (index tag aemformsAFReferences)
   ```

1. Wählen Sie [!UICONTROL Erläuterung] aus. Vergewissern Sie sich, dass der Plan `lucene:customAFReferenceLuceneIndex-1` und `/oak:index/customAFReferenceLuceneIndex-1` oder Ihren ausgewählten Indexnamen für die Verzweigungen der Abfrage statt eines Durchlaufplans verwendet. Weitere Informationen finden Sie unter [Abfrage erläutern](/help/sites-administering/operations-dashboard.md#explain-query).
1. Wiederholen Sie den Experience Fragment-Veröffentlichungsvorgang, der die Warnung ausgelöst hat. Überprüfen Sie `error.log` auf neue Durchlaufwarnungen von `com.adobe.aem.formsndocuments.publish.AssetReferenceProvider.resolvePathsToFindReferences`.

Wenn der Plan den benutzerdefinierten Index nicht auswählt, überprüfen Sie das -Tag, die `indexRules` und die Definition der `sling:resourceType`-Eigenschaft mit den obigen Beispielen. Weitere Informationen zur Diagnose finden Sie [Fehlerbehebung bei Oak-Indizes](/help/sites-deploying/troubleshooting-oak-indexes.md).

## Verwandte Aufgaben {#related-tasks}

Weitere Informationen zur Abfrageleistung und Indexkonfiguration finden Sie unter:

* [Oak-Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md)
* [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md)
* [Fehlerbehebung bei langsamen Abfragen](/help/sites-developing/troubleshooting-slow-queries.md)
