---
title: Artikel verwalten
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Verwalten von Artikeln.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: ea6c8aa3-f86e-4878-8550-fe1662f10696
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 4%

---

# Artikel verwalten{#managing-articles}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Content-Management-Aktionen sind die Bausteine, mit denen Sie Artikel in einem Programm erstellen und verwalten können. Die folgenden Aktionen werden für Artikel innerhalb der Anwendung ausgeführt.

## Artikelübersicht {#articles-overview}

Artikel stellen den Text zusammen mit der Kunst dar, um Informationen zu vermitteln.

>[!NOTE]
>
>In den folgenden Ressourcen in der Online-Hilfe erfahren Sie mehr über die folgenden Themen in AEM Mobile-Programmen:
>
>* [Überlegungen zum Design](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Artikel verwalten](https://helpx.adobe.com/digital-publishing-solution/help/creating-articles.html)
>

## Erstellen eines Artikels {#creating-an-article}

Der allgemeine Arbeitsablauf zum Erstellen eines Artikels lautet wie folgt:

1. Wählen **in** Seitenleiste „Mobil“ aus.
1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie auf den Abwärtspfeil in der oberen rechten Ecke der Kachel **Artikel verwalten**.
1. Wählen Sie eine Artikelvorlage aus und klicken Sie auf **Weiter**.
1. Führen Sie die einzelnen Schritte des Assistenten aus, um mit der Erstellung Ihres neuen Artikels fortzufahren.
1. Wenn Sie bereit sind, klicken Sie auf **Erstellen**.
1. Ihr neuer Artikel wird in der Kachel **Artikel verwalten** angezeigt.

## Importieren eines neuen Artikels {#importing-a-new-article}

Vorhandene Mobile-On-Demand-Inhalte können von Mobile On-Demand in AEM heruntergeladen (importiert) werden. Dies ermöglicht die Bearbeitung und Anzeige lokaler Inhalte.

>[!NOTE]
>
>Bilder werden nicht importiert.

Der Workflow zum Importieren eines neuen Artikels

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie auf den Abwärtspfeil oben rechts in der Kachel **Artikel verwalten** und wählen Sie Artikel importieren aus.
1. Klicken Sie **Dialogfeld auf** Artikel importieren“ und dann auf Schließen.
1. Ihre Mobile-On-Demand-Artikel werden jetzt in der Kachel **Artikel verwalten** angezeigt.

>[!CAUTION]
>
>Verknüpfen Sie zuerst eine Mobile-On-Demand-Verbindung.

![chlimage_1-3](assets/chlimage_1-3.gif)

## Bearbeiten eines Artikels {#editing-an-article}

Verwenden Sie den integrierten AEM-Drag-and-Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder von DAM Assets können eingefügt werden.

>[!CAUTION]
>
>Nur in AEM erstellte Artikel können im Editor geöffnet werden.

Der Workflow zum Bearbeiten eines Artikels:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie einen Artikel aus der AEM-Quelle aus der Kachel **Artikel verwalten**.
1. Klicken Sie auf den hervorgehobenen Artikel in der Listenansicht, um ihn im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Artikelinhalte (Manuskripte, Bilder, Text usw.) per Drag-and-Drop zu verschieben.

### Anzeigen und Bearbeiten von Metadaten in einem Artikel {#viewing-and-editing-the-metadata-within-an-article}

Inhalte wie Artikel, Banner usw. weisen zahlreiche Eigenschaften wie Titel, Beschreibungen und Bilder auf. Diese Aktion wird verwendet, um diese Eigenschaften anzuzeigen und zu ändern. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Der allgemeine Workflow zum Anzeigen/Bearbeiten eines Artikels:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie einen Artikel aus der Kachel **Artikel verwalten**.

1. Wählen **in der** „Eigenschaften anzeigen“ aus.
1. Alle verfügbaren Metadaten für diesen Artikel anzeigen.
1. Bearbeiten Sie bei Bedarf die Metadaten und klicken Sie **Speichern**.
1. Laden Sie optional die Änderungen sofort in Mobile On-Demand hoch.

## Artikel hochladen {#uploading-an-article}

Beim Hochladen wird der ausgewählte Inhalt kopiert und einem Mobile-On-Demand-Projekt hinzugefügt. Bereits vorhandene Mobile-On-Demand-Inhalte werden durch die neue Version ersetzt.

Der allgemeine Workflow zum Hochladen eines Artikels:

1. Wählen Sie **Mobile** Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen **in der Kachel** Artikel verwalten“ einen Artikel zum Hochladen auf Mobile On-Demand aus.
1. Fügen Sie bei Bedarf weitere Artikel aus der Listenansicht hinzu.
1. Wählen **in der** „Hochladen“ aus und klicken Sie dann im Dialogfeld auf Hochladen .
1. Ihre Artikel werden jetzt auf Mobile On-Demand hochgeladen.

![chlimage_1-4](assets/chlimage_1-4.gif)

## Löschen eines Artikels {#deleting-an-article}

Dieser Vorgang löscht die ausgewählten Inhalte aus Mobile On-Demand und optional aus der lokalen AEM-Instanz.

Der allgemeine Workflow zum Löschen eines Artikels:

1. Wählen Sie unter Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie den zu löschenden Artikel in der **Artikel verwalten** aus.
1. Stellen Sie sicher, dass es in der Liste ausgewählt ist; wählen Sie ggf. weitere aus, die gelöscht werden sollen.
1. Klicken **in** Aktionsleiste auf „Löschen“.
1. Aktivieren Sie diese Option, wenn Sie aus AEM und Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihr Artikel wurde jetzt aus der Liste entfernt.

![chlimage_1-5](assets/chlimage_1-5.gif)

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Artikeln finden Sie unter

* [Verwalten von Bannern](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Rückgängigmachen der Veröffentlichung von Inhalten](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
