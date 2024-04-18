---
title: Anpassen der Ansichten von Seiteneigenschaften
description: Jede Seite verfügt über eine Reihe von Eigenschaften, die Sie nach Bedarf bearbeiten können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 292874bf-2ee6-4638-937c-f8f26c93ca65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 100%

---

# Anpassen der Ansichten von Seiteneigenschaften{#customizing-views-of-page-properties}

Jede Seite verfügt über einen Satz von [Eigenschaften](/help/sites-authoring/editing-page-properties.md), die von Benutzenden angezeigt und bearbeitet werden können. Einige sind beim Erstellen der Seite erforderlich (Ansicht erstellen), andere können später angezeigt und bearbeitet werden (Ansicht bearbeiten). Diese Seiteneigenschaften werden über das Dialogfeld (`cq:dialog`) der entsprechenden Seitenkomponente definiert und bereitgestellt.

>[!CAUTION]
>
>In der klassischen Benutzeroberfläche kann die Ansicht der Seiteneigenschaften nicht angepasst werden.

Der Standardstatus für jede Seiteneigenschaft ist wie folgt:

* In der Erstellungsansicht ausgeblendet (z. B. im **Seitenerstellungsassistenten**)

* In der Bearbeitungsansicht verfügbar (z. B. unter **Eigenschaften anzeigen**)

Felder müssen einzeln konfiguriert werden, wenn eine Änderung erforderlich ist. Dies erfolgt mithilfe der entsprechenden Knoteneigenschaften:

* Seiteneigenschaft, die in der Erstellungsansicht verfügbar sein soll (z. B. im **Seitenerstellungsassistenten**):

   * Name: `cq:showOnCreate`
   * Typ: `Boolean`

* Seiteneigenschaft, die in der Bearbeitungsansicht verfügbar sein soll (z. B. die Option **Anzeigen**/**Bearbeiten**) von **Eigenschaften**):

   * Name: `cq:hideOnEdit`
   * Typ: `Boolean`

Sehen Sie als Beispiel die Einstellungen für Felder, die unter **Weitere Titel und Beschreibungen** auf der Registerkarte **Allgemein** der Foundation-Seitenkomponente gruppiert sind. Sie sind im **Seitenerstellungsassistenten** verfügbar, da `cq:showOnCreate` auf `true` gesetzt ist:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/moretitles
```

>[!TIP]
>
>Eine Anleitung zum Anpassen der Seiteneigenschaften finden Sie im [Tutorial zum Erweitern der Seiteneigenschaften](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/developing/page-properties-technical-video-develop.html?lang=de).

## Konfiguration von Seiteneigenschaften {#configuring-your-page-properties}

Sie können diese Felder auch konfigurieren, indem Sie das Dialogfeld Ihrer Seitenkomponente konfigurieren und die entsprechenden Knoteneigenschaften anwenden.

Beispiel: Der [**Seitenerstellungsassistent**](/help/sites-authoring/managing-pages.md#creating-a-new-page) zeigt standardmäßig die Felder an, die unter **Weitere Titel und Beschreibungen** gruppiert sind. Um diese auszublenden, nehmen Sie folgende Konfiguration vor:

1. Erstellen Sie Ihre Seitenkomponente unter `/apps`.
1. Erstellen Sie eine Überschreibung (mit *dialog diff*, das von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) bereitgestellt wird) für den Abschnitt `basic` der Seitenkomponente. Beispiel:

   ```xml
   <your-page-component>/cq:dialog/content/items/tabs/items/basic
   ```

   >[!NOTE]
   >
   >Siehe als Referenz:
   >
   >    `/libs/wcm/foundation/components/basicpage/v1/basicpage/cq:dialog`
   >
   >Sie dürfen jedoch ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
   >
   >da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
   >
   >Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
   >
   >1. Erstellen Sie das erforderliche Element unter `/apps` neu (d. h. wie es in `/libs` existiert).
   >1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

1. Legen Sie die Eigenschaft `path` auf `basic` fest, um auf die Überschreibung der Registerkarte „Standard“ zu verweisen (siehe auch den nächsten Schritt). Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic
   ```

1. Erstellen Sie eine Überschreibung des Abschnitts `basic` - `moretitles` am entsprechenden Pfad; Beispiel:

   ```xml
   /apps/demos/components/page/tabs/basic/items/column/items/moretitles
   ```

1. Wenden Sie die entsprechende Knoteneigenschaft an:

   * **Name**: `cq:showOnCreate`
   * **Typ**: `Boolean`
   * **Wert**: `false`

   Der Abschnitt **Weitere Titel und Beschreibungen** wird nicht mehr im **Seitenerstellungsassistenten** angezeigt.

>[!NOTE]
>
>Wenn Sie Seiteneigenschaften für die Verwendung mit Live Copies konfigurieren, finden Sie weitere Details unter [Konfigurieren von MSM-Sperren für Seiteneigenschaften](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-page-properties-touch-enabled-ui).

## Beispielkonfiguration von Seiteneigenschaften {#sample-configuration-of-page-properties}

Dieses Beispiel zeigt die „dialog diff“-Technik von [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md), einschließlich der Verwendung von [`sling:orderBefore`](/help/sites-developing/sling-resource-merger.md#properties). Es zeigt auch die Verwendung von `cq:showOnCreate` und `cq:hideOnEdit`.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-authoring-extension-page-dialog in GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-page-dialog)
