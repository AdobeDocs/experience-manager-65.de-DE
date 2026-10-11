---
title: Konfigurieren Ihrer Seite für die Massenbearbeitung von Seiteneigenschaften
description: Durch Massenbearbeitung von Seiteneigenschaften können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 1787e643-fc8e-40e0-8e14-97b222a7c320
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 5ef752af-d616-5b23-8312-06964e46b208
    internal-label: Administering
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 100%
---
# Konfigurieren Ihrer Seite für die Massenbearbeitung von Seiteneigenschaften {#configuring-your-page-for-bulk-editing-of-page-properties}

[Massenbearbeitung von Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) ermöglicht es Ihnen, die Eigenschaften mehrerer Seiten gleichzeitig zu bearbeiten.

Aufgrund der Möglichkeit unterschiedlicher Werte sind die Seiteneigenschaften für die Massenbearbeitung nicht standardmäßig aktiviert. Sie müssen explizit zugelassen sein (aktiviert). Beim Definieren der Seiteneigenschaften, die für die Massenbearbeitung verfügbar sein sollen, müssen Sie bestimmte Auswirkungen berücksichtigen, wie zum Beispiel:

* Bestimmte Felder sind normalerweise eindeutig, z. B. ein Seitentitel. Sie müssen entscheiden, ob es sinnvoll ist, diese Felder für die Massenbearbeitung zu aktivieren, wenn ein Wert angewendet wird.
* Bestimmte Felder können mehrere Werte haben - dies erfordert eine sinnvolle Darstellung beim Rendern.

  Zum Beispiel ein Kontrollkästchen, das „Bereit zur Veröffentlichung“ anzeigt. Dies kann vor der Massenbearbeitung mehrere Werte haben (z. B. bereit, in Prüfung, in Bearbeitung).

>[!CAUTION]
>
>Die Massenbearbeitung von Seiteneigenschaften ist:
>
>* Nicht in der klassischen Benutzeroberfläche verfügbar.
>* Nicht verfügbar für Seiten in einer Live Copy.
>* Nur für Seiten mit demselben Ressourcentyp verfügbar.
>

>[!NOTE]
>
>Massenbearbeitung ist auch für Assets verfügbar. Sie ist sehr ähnlich, unterscheidet sich aber in einigen Punkten. Weitere Informationen dazu finden Sie unter [Bearbeiten von Eigenschaften für mehrere Assets](/help/assets/metadata.md). Sie können die Felder im Metadaten-Masseneditor für Assets mit dem [Schema-Editor](/help/assets/metadata-schemas.md) anpassen.

## Aktivieren eines Felds {#enabling-a-field}

>[!NOTE]
>
>Bestimmte Felder können mehrere Werte haben - dies erfordert eine sinnvolle Darstellung beim Rendern. Aus diesem Grund sollten Sie nur die folgenden Feldtypen aktivieren:
>
>* `/libs/granite/ui/components/foundation/form/textfield`
>* `/libs/granite/ui/components/foundation/form/textarea`
>* `/libs/granite/ui/components/foundation/form/tagspicker`
>* `/libs/granite/ui/components/foundation/form/datepicker`
>* `/libs/granite/ui/components/foundation/form/pathbrowser`
>* `/libs/granite/ui/components/foundation/form/checkbox`
>

Felder sind in der Seitenkomponente aktiviert (*nicht* auf der Vorlage):

1. Öffnen Sie die Seitenkomponente mit CRXDE Lite (oder einer entsprechenden Methode).

   Beispiel: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >In diesem Beispiel wird davon ausgegangen, dass die Kernkomponenten auf der Instanz installiert wurden. Dies ist der Fall, wenn die Instanz mit We.Retail-Beispielinhalten ausgeführt wird. Weitere Informationen finden Sie in der [Dokumentation für Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).

1. Navigieren Sie zum erforderlichen Feld innerhalb der `cq:dialog`-Definition.
1. Definieren Sie die folgende Eigenschaft auf dem Feldknoten:

   * **Name**: `allowBulkEdit`
   * **Typ**: `Boolean`
   * **Wert**: `true`

   Beispiel: für die [Grundlagenkomponente](/help/sites-authoring/default-components-foundation.md) der Standardseite:

   `/libs/foundation/components/page`

   würde die Eigenschaft definiert werden auf:

   `cq:dialog/content/items/tabs/items/basic/items/column/items/onofftime/items/ondate`

   >[!CAUTION]
   >
   >Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
   >
   >    1. Erstellen Sie das erforderliche Element unter `/apps` neu (d. h. wie es in `/libs` existiert).
   >    1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

1. Wählen Sie **Alle speichern**, um ihre Aktualisierungen beizubehalten.
