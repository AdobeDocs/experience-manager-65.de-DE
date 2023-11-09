---
title: Verwalten von Artikeln
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Verwalten von Artikeln.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: ea6c8aa3-f86e-4878-8550-fe1662f10696
source-git-commit: 451fb472e170a79f9854efadf9be1d4fe0628b94
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 1%

---

# Verwalten von Artikeln{#managing-articles}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Inhaltsverwaltungsaktionen sind die Bausteine, mit denen Sie Artikel in einer Anwendung erstellen und verwalten können. Die folgenden Aktionen werden für Artikel in der Anwendung ausgeführt.

## Artikelübersicht {#articles-overview}

Artikel repräsentieren den Text, der auf Kunst basiert, um Informationen zu vermitteln.

>[!NOTE]
>
>Weitere Informationen zu den folgenden Themen in AEM Mobile-Apps finden Sie in den folgenden Ressourcen der Online-Hilfe:
>
>* [Designüberlegungen](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Verwalten von Artikeln](https://helpx.adobe.com/digital-publishing-solution/help/creating-articles.html)
>

## Artikel erstellen {#creating-an-article}

Der allgemeine Workflow zum Erstellen eines Artikels sieht wie folgt aus:

1. Auswählen **Mobilnummer** über die Seitenleiste aus.
1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts in der **Artikel verwalten** Kachel.
1. Wählen Sie eine Artikelvorlage aus und klicken Sie auf **Nächste**.
1. Führen Sie jeden Schritt des Assistenten durch, um mit der Erstellung des neuen Artikels fortzufahren.
1. Wenn Sie bereit sind, klicken Sie auf **Erstellen**.
1. Ihr neuer Artikel wird im **Artikel verwalten** Kachel.

## Importieren eines neuen Artikels {#importing-a-new-article}

Vorhandene On-Demand-Inhalte für Mobilgeräte können von Mobile On-Demand heruntergeladen (importiert) werden, um sie zu AEM. Dies ermöglicht die Bearbeitung und Anzeige lokaler Inhalte.

>[!NOTE]
>
>Beim Import sind keine Bilder enthalten.

Der Workflow zum Importieren eines neuen Artikels

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts in der **Artikel verwalten** und wählen Sie Artikel importieren aus.
1. Klicks **Artikel importieren** im Dialogfeld und dann Schließen.
1. Ihre On-Demand-Artikel für Mobilgeräte werden jetzt im **Artikel verwalten** Kachel.

>[!CAUTION]
>
>Sie müssen zuerst eine Mobile On-Demand-Verbindung verknüpfen.

![chlimage_1-3](assets/chlimage_1-3.gif)

## Bearbeiten eines Artikels {#editing-an-article}

Verwenden Sie den integrierten AEM Drag &amp; Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder aus DAM-Assets können eingefügt werden.

>[!CAUTION]
>
>Im Editor können nur in AEM erstellte Artikel geöffnet werden.

Der Workflow zum Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie einen AEM Artikel aus dem **Artikel verwalten** Kachel.
1. Klicken Sie in der Listenansicht auf den hervorgehobenen Artikel, um ihn im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Artikelinhalte (Manuskripte, Bilder, Text usw.) zu ziehen.

### Anzeigen und Bearbeiten von Metadaten in einem Artikel {#viewing-and-editing-the-metadata-within-an-article}

Inhalte wie Artikel, Banner usw. haben zahlreiche Eigenschaften wie Titel, Beschreibungen und Bilder. Diese Aktion wird verwendet, um solche Eigenschaften anzuzeigen und zu ändern. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Allgemeiner Workflow zum Anzeigen/Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie einen Artikel aus der **Artikel verwalten** Kachel.

1. Auswählen **Eigenschaften anzeigen** in der Aktionsleiste aus.
1. Alle verfügbaren Metadaten für diesen Artikel anzeigen.
1. Bearbeiten Sie die Metadaten nach Bedarf und klicken Sie auf **Speichern** wann geschehen.
1. Optional können Sie die Änderungen sofort in Mobile On-Demand hochladen.

## Hochladen eines Artikels {#uploading-an-article}

Mit der Aktion &quot;Hochladen&quot;wird der ausgewählte Inhalt kopiert und zu einem On-Demand-Projekt für Mobilgeräte hinzugefügt. Bereits vorhandene mobile On-Demand-Inhalte werden durch die neue Version ersetzt.

Der allgemeine Workflow zum Hochladen eines Artikels:

1. Von **Mobilnummer** wählen Sie Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Im **Artikel verwalten** -Kachel einen Artikel zum Hochladen auf Mobile On-Demand auswählen.
1. Fügen Sie bei Bedarf in der Listenansicht weitere Artikel hinzu.
1. Auswählen **Hochladen** Klicken Sie in der Aktionsleiste auf Hochladen im Dialogfeld.
1. Ihre Artikel werden jetzt in Mobile On-Demand hochgeladen.

![chlimage_1-4](assets/chlimage_1-4.gif)

## Löschen eines Artikels {#deleting-an-article}

Durch diesen Vorgang wird der ausgewählte Inhalt aus Mobile On-Demand und optional aus der lokalen AEM gelöscht.

Der allgemeine Workflow zum Löschen eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie den zu löschenden Artikel im **Artikel verwalten** Kachel.
1. Stellen Sie sicher, dass es in der Liste ausgewählt ist. Wählen Sie Andere aus, um sie nach Bedarf zu löschen.
1. Klicks **Löschen** in der Aktionsleiste aus.
1. Überprüfen Sie, ob Sie aus AEM und Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihr Artikel wurde jetzt aus der Liste entfernt.

![chlimage_1-5](assets/chlimage_1-5.gif)

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Artikeln finden Sie unter

* [Banner verwalten](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Veröffentlichung des Inhalts rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
