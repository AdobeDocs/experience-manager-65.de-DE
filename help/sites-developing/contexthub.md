---
title: ContextHub
seo-title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
seo-description: ContextHub is a framework for storing, manipulating, and presenting context data
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
exl-id: 3fd50655-7461-4900-a3b8-c01b04c7ba7a
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 49%

---

# ContextHub{#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Die clientseitige JavaScript-API ermöglicht den Zugriff auf die Daten zur Personalisierung von Inhalten.

>[!NOTE]
>
>Die [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) implementiert ContextHub und kann als Referenz dienen, wenn Sie ContextHub in Ihr eigenes Projekt integrieren.

>[!CAUTION]
>
>Der Pfad, der die ContextHub-Beispielkonfiguration enthält, die von der [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) verwendet wird (`/libs/settings/cloudsettings/legacy`), sollte nur als Referenz zum Erstellen einer eigenen Konfiguration verwendet werden.
>
>Es sollte nicht in einem Projekt als eigene ContextHub-Konfiguration verwendet werden.

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Stores zugreifen, um bei Bedarf Daten zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Store ist eine Instanz eines vordefinierten Storetyps:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](/help/sites-developing/ch-samplestores.md).
* Verwenden AEM Konsolen für [Stores erstellen](ch-configuring.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Entwickler können [Zugriffsspeicherdaten](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) über JavaScript.

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentierungsmaschine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die JavaScript-API verwenden, um [aufgelöste Segmente bestimmen](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-authoring/ch-previewing.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die Zugriff auf ContextHub-Stores bieten.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub bietet mehrere [Beispielmodultypen](/help/sites-developing/ch-samplemodules.md).
* Verwenden AEM Konsolen für [Benutzeroberflächenmodule hinzufügen](ch-configuring.md#adding-a-ui-module)und [gruppieren sie in UI-Modi](ch-configuring.md#adding-a-ui-mode).

* Entwickler können [Erstellen benutzerdefinierter Modultypen](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Entwickler müssen [Fügen Sie die ContextHub-Komponente zur Seite hinzu.](/help/sites-developing/ch-adding.md).
