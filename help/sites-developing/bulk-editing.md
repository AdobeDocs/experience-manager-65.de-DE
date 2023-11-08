---
title: Konfigurieren Ihrer Seite für die Massenbearbeitung von Seiteneigenschaften
seo-title: Configuring your Page for Bulk Editing of Page Properties
description: Durch Massenbearbeitung von Seiteneigenschaften können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten
seo-description: Bulk editing of page properties lets you edit the properties of multiple pages at once
uuid: 1ad403d2-4b93-4943-ae45-74bf20705b81
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: fe61ee4b-51b6-4a6f-91d8-1c02b29cc1db
exl-id: 1787e643-fc8e-40e0-8e14-97b222a7c320
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 54%

---

# Konfigurieren Ihrer Seite für die Massenbearbeitung von Seiteneigenschaften {#configuring-your-page-for-bulk-editing-of-page-properties}

[Massenbearbeitung von Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md#from-the-sites-console-multiple-pages) können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten.

Aufgrund der Möglichkeit unterschiedlicher Werte sind die Seiteneigenschaften für die Massenbearbeitung nicht standardmäßig aktiviert. Sie müssen explizit zugelassen sein (aktiviert). Beim Definieren der Seiteneigenschaften, die für die Massenbearbeitung verfügbar sein sollen, müssen Sie bestimmte Auswirkungen berücksichtigen, z. B.:

* Bestimmte Felder sind in der Regel eindeutig, z. B. ein Seitentitel. Sie müssen entscheiden, ob es sinnvoll ist, diese Felder für die Massenbearbeitung zu aktivieren, wenn ein Wert angewendet wird.
* Bestimmte Felder können mehrere Werte haben - dies erfordert eine sinnvolle Darstellung beim Rendern.

  Zum Beispiel ein Kontrollkästchen, das „Bereit zur Veröffentlichung“ anzeigt. Dies kann mehrere Werte vor der Massenbearbeitung aufweisen (z. B. &quot;Bereit&quot;, &quot;In Überprüfung&quot;, &quot;In Bearbeitung&quot;).

>[!CAUTION]
>
>Massenbearbeitung von Seiteneigenschaften:
>
>* Nicht in der klassischen Benutzeroberfläche verfügbar.
>* Nicht verfügbar für Seiten in einer Live Copy.
>* Nur für Seiten mit demselben Ressourcentyp verfügbar.
>

>[!NOTE]
>
>Massenbearbeitung ist auch für Assets verfügbar. Sie ist sehr ähnlich, unterscheidet sich aber in einigen Punkten. Siehe [Bearbeiten von Eigenschaften mehrerer Assets](/help/assets/metadata.md) für vollständige Informationen. Sie können die Felder im Metadaten-Masseneditor für Assets mit dem [Schema-Editor](/help/assets/metadata-schemas.md) anpassen.

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

Felder sind in der Seitenkomponente (*not* auf der Vorlage):

1. Öffnen Sie die Seitenkomponente mit CRXDE Lite (oder einer entsprechenden Methode).

   Beispiel: `/apps/core/wcm/components/page/v1/page`

   >[!NOTE]
   >
   >In diesem Beispiel wird davon ausgegangen, dass die Kernkomponenten auf der Instanz installiert wurden. Dies ist der Fall, wenn die Instanz mit We.Retail-Beispielinhalten ausgeführt wird. Siehe [Dokumentation zu Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) für weitere Informationen.

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
   >Die empfohlene Methode für Konfigurations- und sonstige Änderungen sieht wie folgt aus:
   >
   >    1. Erstellen Sie das erforderliche Element (d. h., wie es in `/libs`) unter `/apps`
   >    1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

1. Wählen Sie **Alle speichern**, um ihre Aktualisierungen beizubehalten.
