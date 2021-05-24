---
title: ContextHub
seo-title: ContextHub
description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
seo-description: ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
exl-id: 3fd50655-7461-4900-a3b8-c01b04c7ba7a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 86%

---

# ContextHub{#contexthub}

ContextHub ist ein Framework zum Speichern, Ändern und Darstellen von Kontextdaten. Die Client-seitige JavaScript-API ermöglicht Ihnen den Zugriff auf die Daten zur Personalisierung von Inhalten.

>[!NOTE]
>
>Die [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) implementiert ContextHub und kann als Referenz dienen, wenn Sie ContextHub in Ihr eigenes Projekt integrieren.

>[!CAUTION]
>
>Der Pfad mit der ContextHub-Beispielkonfiguration, die von der [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) verwendet wird, sollte nur als Referenz zum Erstellen Ihrer eigenen Konfiguration verwendet werden.
>
>Sie sollte nicht in einem Projekt als eigene ContextHub-Konfiguration verwendet werden.

## Persistenz {#persistence}

ContextHub speichert persistente Kontextdaten auf dem Client. Mit der ContextHub-JavaScript-API können Sie auf Speicher zugreifen, um Daten bei Bedarf zu erstellen, zu aktualisieren und zu löschen. Daher stellt ContextHub eine Datenschicht auf Ihren Seiten dar.

Jeder ContextHub-Speicher ist eine Instanz eines vordefinierten Speichertyps:

* ContextHub stellt verschiedene [Beispielspeicherarten bereit](/help/sites-developing/ch-samplestores.md).
* Verwenden Sie AEM-Konsolen zum [Erstellen von Speichern](ch-configuring.md#creating-a-contexthub-store).
* Entwickler können [anwenderdefinierte Speichertypen erstellen](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Entwickler können auf die [gespeicherten Daten](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) über JavaScript zugreifen.

## Segmentierung  {#segmentation}

ContextHub enthält eine Segmentations-Engine, die Segmente verwaltet und bestimmt, welche Segmente für den aktuellen Kontext aufgelöst werden. Mehrere Segmente sind definiert. Sie können die Javascript-API verwenden, um [aufgelöste Segmente zu ermitteln](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Präsentation {#presentation}

Die [ContextHub-Symbolleiste](/help/sites-authoring/ch-previewing.md) ermöglicht es Marketern und Autoren, gespeicherte Daten anzuzeigen und zu bearbeiten, um das Anwendererlebnis beim Erstellen von Seiten zu simulieren. Die Symbolleiste besteht aus Gruppen von UI-Modulen, die den Zugriff auf ContextHub-Speicher ermöglichen.

Jedes ContextHub-UI-Modul ist eine Instanz eines vordefinierten Modultyps:

* ContextHub stellt mehrere [Beispielmodularten](/help/sites-developing/ch-samplemodules.md) bereit.
* Verwenden Sie AEM-Konsolen, um [UI-Module hinzuzufügen](ch-configuring.md#adding-a-ui-module) und sie in [UI-Modi zu gruppieren](ch-configuring.md#adding-a-ui-mode).

* Entwickler können [benutzerdefinierte Modularten erstellen](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Entwickler müssen die [ContextHub-Komponente in die Seite einfügen](/help/sites-developing/ch-adding.md).
