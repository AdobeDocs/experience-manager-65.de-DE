---
title: Verwalten von Bannern
description: Banner stehen für normalerweise für grafische Werbelinks. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: c65a24e6-3041-4774-aeed-8e188ea19b78
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 6%

---

# Verwalten von Bannern{#managing-banners}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Content-Management-Aktionen sind die Bausteine, mit denen Inhalte in einer Anwendung erstellt und verwaltet werden können. Die folgenden Aktionen werden für Inhalte in der Anwendung ausgeführt.

## Banner - Übersicht {#banners-overview}

Banner stehen für normalerweise für grafische Werbelinks.

>[!NOTE]
>
>In den folgenden Ressourcen in der Online-Hilfe erfahren Sie mehr über die folgenden Themen in AEM Mobile-Programmen:
>
>* [Überlegungen zum Design](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Erstellen von Bannern](https://helpx.adobe.com/digital-publishing-solution/help/creating-banners.html)
>

## Erstellen eines Banners {#creating-a-banner}

Der allgemeine Arbeitsablauf zum Erstellen eines Artikels lautet wie folgt:

1. Wählen **in** Seitenleiste „Mobil“ aus.
1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie auf den Abwärtspfeil in der oberen rechten Ecke der Kachel **Banner verwalten**.
1. Führen Sie die einzelnen Schritte des Assistenten aus, um mit der Erstellung des neuen Banners fortzufahren.
1. Wenn Sie bereit sind, klicken Sie auf **Erstellen**.
1. Das neue Banner wird in der Kachel **Banner verwalten** angezeigt.

![chlimage_1-6](assets/chlimage_1-6.gif)

## Ein neues Banner importieren {#importing-a-new-banner}

Vorhandene Mobile-On-Demand-Inhalte können von Mobile On-Demand in AEM heruntergeladen (importiert) werden. Dies ermöglicht die Bearbeitung und Anzeige lokaler Inhalte.

>[!NOTE]
>
>Bilder werden nicht importiert.

Der Workflow zum Importieren eines neuen Artikels

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie auf den Abwärtspfeil oben rechts auf der Kachel **Banner verwalten** und wählen Sie Banner importieren aus.
1. Klicken Sie **Dialogfeld auf** Banner importieren“ und dann auf Schließen.
1. Ihre Mobile-On-Demand-Artikel werden jetzt auf der Kachel **Banner verwalten** angezeigt.

>[!CAUTION]
>
>Verknüpfen Sie zuerst eine Mobile-On-Demand-Verbindung.

## Bearbeiten eines Banners {#editing-a-banner}

Verwenden Sie den integrierten AEM-Drag-and-Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder von DAM Assets können eingefügt werden.

>[!CAUTION]
>
>Nur in AEM erstellte Banner können im Editor geöffnet werden.

Der Workflow zum Bearbeiten eines Artikels:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie ein Banner aus AEM-Quellen aus der Kachel **Banner verwalten** aus.
1. Klicken Sie in der Listenansicht auf das hervorgehobene Banner, um es im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Bannerinhalte (Manuskripte, Bilder, Text usw.) in den Arbeitsbereich zu ziehen.

### Anzeigen und Bearbeiten von Metadaten in einem Banner {#viewing-and-editing-the-metadata-within-a-banner}

Banner haben zahlreiche Eigenschaften wie Titel, Beschreibungen, Bilder. Diese Aktion wird verwendet, um diese Eigenschaften anzuzeigen und zu ändern. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Der allgemeine Workflow zum Anzeigen/Bearbeiten eines Artikels:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie ein Banner aus der Kachel **Banner verwalten**.

1. Wählen Sie in der Aktionsleiste **Eigenschaften** aus.
1. Alle verfügbaren Metadaten für diesen Artikel anzeigen.
1. Bearbeiten Sie bei Bedarf die Metadaten und klicken Sie **Speichern**.
1. Laden Sie optional die Änderungen sofort in Mobile On-Demand hoch.

## Hochladen eines Banners {#uploading-a-banner}

Beim Hochladen wird der ausgewählte Inhalt kopiert und einem Mobile-On-Demand-Projekt hinzugefügt. Bereits vorhandene Mobile-On-Demand-Inhalte werden durch die neue Version ersetzt.

Der allgemeine Workflow zum Hochladen eines Banners:

1. Wählen Sie **Mobile** Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen **in der Kachel** Banner verwalten“ ein Banner für den Upload auf Mobile On-Demand aus.
1. Fügen Sie bei Bedarf weitere Banner aus der Listenansicht hinzu.
1. Wählen **in der** „Hochladen“ aus und klicken Sie dann im Dialogfeld auf Hochladen .
1. Ihre Banner werden jetzt auf Mobile On-Demand hochgeladen.

![chlimage_1-7](assets/chlimage_1-7.gif)

## Löschen eines Banners {#deleting-a-banner}

Dieser Vorgang löscht das ausgewählte Banner aus Mobile On-Demand und optional aus der lokalen AEM-Instanz.

Der allgemeine Workflow zum Löschen eines Banners:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie das zu löschende Banner in der Kachel **Banner verwalten** aus.
1. Stellen Sie sicher, dass es in der Liste ausgewählt ist (wählen Sie ggf. weitere aus, die gelöscht werden sollen).
1. Klicken **in** Aktionsleiste auf „Löschen“.
1. Aktivieren Sie diese Option, wenn Sie aus AEM und Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihr Banner wurde jetzt aus der Liste entfernt.

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Bannern finden Sie unter

* [Artikel verwalten](/help/mobile/mobile-on-demand-managing-articles.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Rückgängigmachen der Veröffentlichung von Inhalten](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
