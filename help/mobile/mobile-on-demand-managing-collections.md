---
title: Verwalten von Sammlungen
description: Sammlungen stellen einen klar definierten Behälter dar, der mit Inhalten wie Artikeln oder Bannern gefüllt ist, die dem Titelthema entsprechen. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: 0b4aa1a4-449a-4882-8f7c-3ceea6ac7f83
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 5%

---

# Verwalten von Sammlungen{#managing-collections}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Inhaltsverwaltungsaktionen sind die Bausteine, mit denen Inhalte in einer Anwendung erstellt und verwaltet werden können. Die folgenden Aktionen werden für Inhalte in der Anwendung ausgeführt.

## Sammlungen - Überblick {#collections-overview}

Sammlungen stellen einen klar definierten *Behälter* dar, der mit Inhalten wie Artikeln oder Bannern gefüllt ist, die zum Thema des Titelbildes passen.

>[!NOTE]
>
>Weitere Informationen zu den folgenden Themen in AEM Mobile-Apps finden Sie in den folgenden Ressourcen der Online-Hilfe:
>
>* [Designüberlegungen](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Verwalten von Sammlungen](https://helpx.adobe.com/digital-publishing-solution/help/creating-collections.html)
>

## Erstellen einer Sammlung {#creating-a-collection}

Der allgemeine Workflow zum Erstellen einer Kollektion lautet wie folgt:

1. Wählen Sie in der Seitenleiste **Mobil** aus.
1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts in der Kachel **Sammlungen verwalten** auf den Abwärtspfeil.
1. Führen Sie jeden Schritt des Assistenten durch, um mit der Erstellung des neuen Artikels fortzufahren.
1. Wenn Sie bereit sind, klicken Sie auf **Erstellen**.
1. Ihr neuer Artikel wird in der Kachel **Sammlungen verwalten** angezeigt.

![chlimage_1-1](assets/chlimage_1-1.gif)

## Importieren einer neuen Sammlung {#importing-a-new-collection}

Vorhandene On-Demand-Inhalte für Mobilgeräte können von Mobile On-Demand heruntergeladen (importiert) werden, um sie zu AEM. Dies ermöglicht die Bearbeitung und Anzeige lokaler Inhalte.

>[!NOTE]
>
>Beim Import sind keine Bilder enthalten.

Der Workflow zum Importieren einer neuen Sammlung

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie oben rechts in der Kachel **Sammlungen verwalten** auf den Abwärtspfeil und wählen Sie &quot;Sammlungen importieren&quot;.
1. Klicken Sie im Dialogfeld auf **Sammlungen importieren** und dann auf Schließen.
1. Ihre On-Demand-Sammlungen für Mobilgeräte werden jetzt in der Kachel **Sammlungen verwalten** angezeigt.

>[!CAUTION]
>
>Verknüpfen Sie zuerst eine Mobile On-Demand-Verbindung.

## Bearbeiten einer Sammlung {#editing-a-collection}

Verwenden Sie den integrierten AEM Drag &amp; Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder aus DAM Assets können eingefügt werden.

Der Workflow zum Bearbeiten einer Sammlung:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie in der Kachel **Sammlungen verwalten** einen AEM bezogenen Artikel aus.
1. Klicken Sie in der Listenansicht auf die markierte Sammlung, um sie im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Sammlungsinhalte (Manuskripte, Bilder, Text usw.) zu ziehen.

### Anzeigen und Bearbeiten von Metadaten in einer Sammlung {#viewing-and-editing-the-metadata-within-a-collection}

Sammlungen verfügen über zahlreiche Eigenschaften wie Titel, Beschreibungen und Bilder. Diese Aktion wird verwendet, um solche Eigenschaften anzuzeigen und zu ändern. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Allgemeiner Workflow zum Anzeigen/Bearbeiten einer Sammlung:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie eine Sammlung aus der Kachel **Sammlungen verwalten** aus.

1. Wählen Sie in der Aktionsleiste **Eigenschaften** aus.
1. Alle verfügbaren Metadaten für diesen Artikel anzeigen.
1. Bearbeiten Sie die Metadaten nach Bedarf und klicken Sie danach auf **Speichern** .
1. Optional können Sie die Änderungen sofort in Mobile On-Demand hochladen.

## Hochladen einer Sammlung {#uploading-a-collection}

Mit der Aktion &quot;Hochladen&quot;wird der ausgewählte Inhalt kopiert und zu einem On-Demand-Projekt für Mobilgeräte hinzugefügt. Bereits vorhandene mobile On-Demand-Inhalte werden durch die neue Version ersetzt.

Allgemeiner Workflow zum Hochladen einer Sammlung:

1. Wählen Sie in **Mobile** Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie in der Kachel **Sammlungen verwalten** einen Artikel zum Hochladen auf Mobile On-Demand aus.
1. Fügen Sie bei Bedarf in der Listenansicht weitere Sammlungen hinzu.
1. Wählen Sie in der Aktionsleiste **Upload** aus und klicken Sie dann im Dialogfeld auf Hochladen .
1. Ihre Sammlung(en) wurde(n) jetzt in Mobile On-Demand hochgeladen.

## Löschen einer Sammlung {#deleting-a-collection}

Durch diesen Vorgang wird die ausgewählte Sammlung aus Mobile On-Demand und optional aus der lokalen AEM gelöscht.

Der allgemeine Workflow zum Löschen einer Sammlung:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie den zu löschenden Artikel in der Kachel **Sammlungen verwalten** aus.
1. Stellen Sie sicher, dass es in der Liste ausgewählt ist. Wählen Sie Andere aus, um sie nach Bedarf zu löschen.
1. Klicken Sie in der Aktionsleiste auf **Löschen** .
1. Überprüfen Sie, ob Sie aus AEM und Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihre Sammlung wird jetzt aus der Liste entfernt.

## Hinzufügen von Inhalten zu Sammlungen {#adding-content-to-collections}

Sammlungen sind im Wesentlichen eine Kategorie verwandter Inhalte. Sie sammeln Inhalte wie Artikel und Banner in Paketen, die die Navigationsstruktur Ihrer Anwendung definieren. Sammlungen können verschachtelt werden.

>[!NOTE]
>
>Inhalte müssen in Mobile On-Demand hochgeladen werden, bevor sie zu einer Sammlung hinzugefügt werden können.

Kollektionen sind im Wesentlichen eine Kategorie verwandter Inhalte: Sie sammeln Inhalte wie Artikel und Banner in Paketen, die die Navigationsstruktur Ihrer Anwendung definieren. Sammlungen können verschachtelt werden.

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Wählen Sie einen zuvor hochgeladenen Artikel (oder Banner/Sammlung) aus.
1. Wählen Sie in der Aktionsleiste Hinzufügen zu aus.
1. Wählen Sie im Dialogfeld eine zuvor hochgeladene Sammlung aus.
1. Klicken Sie auf **Aktualisieren** , um Inhalte zur Sammlung hinzuzufügen.

![chlimage_1-2](assets/chlimage_1-2.gif)

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Sammlungen finden Sie unter

* [Banner verwalten](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Veröffentlichung des Inhalts rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
