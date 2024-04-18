---
title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 3fd50655-7461-4900-a3b8-c01b04c7ba7a
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 100%

---

# ContextHub{#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Die Client-seitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

>[!NOTE]
>
>Die [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) implementiert ContextHub und kann als Referenz dienen, wenn Sie ContextHub in Ihr eigenes Projekt integrieren.

>[!CAUTION]
>
>Der Pfad, der die ContextHub-Beispielkonfiguration enthält, die von der [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) verwendet wird (`/libs/settings/cloudsettings/legacy`), sollte nur als Referenz zum Erstellen einer eigenen Konfiguration verwendet werden.
>
>Er sollte nicht in einem Projekt als eigene ContextHub-Konfiguration verwendet werden.

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Stores zugreifen, um Daten bei Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Store ist eine Instanz eines vordefinierten Store-Typs:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](/help/sites-developing/ch-samplestores.md).
* Verwenden Sie AEM-Konsolen, um [Stores zu erstellen](ch-configuring.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Entwickelnde können per JavaScript auf [Store-Daten zugreifen](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores).

## Segmentierung {#segmentation}

ContextHub enthält eine Segmentierungs-Engine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die JavaScript-API verwenden, um [aufgelöste Segmente zu bestimmen](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-authoring/ch-previewing.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die Zugriff auf ContextHub-Stores ermöglichen.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub stellt verschiedene [Beispiel-Modultypen](/help/sites-developing/ch-samplemodules.md) bereit.
* Verwenden Sie AEM-Konsolen, um [UI-Module hinzuzufügen](ch-configuring.md#adding-a-ui-module) und sie [in UI-Modi zu gruppieren](ch-configuring.md#adding-a-ui-mode).

* Entwicklerinnen und Entwickler können [benutzerdefinierte Modultypen erstellen](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Entwicklerinnen und Entwickler müssen [die ContextHub-Komponente zur Seite hinzufügen](/help/sites-developing/ch-adding.md).
