---
title: Verwalten von Artikeln
seo-title: Verwalten von Artikeln
description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Verwalten von Artikeln.
seo-description: Auf dieser Seite erfahren Sie mehr über das Erstellen und Verwalten von Artikeln.
uuid: 72b86cd7-3016-41b6-a001-9dce4084e9db
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: b46058f9-4691-4fba-a656-0f8507875a79
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 4%

---


# Verwalten von Artikeln{#managing-articles}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Content-Management-Aktionen sind die Bausteine, die beim Erstellen und Verwalten von Artikeln in einer Anwendung helfen. Die folgenden Aktionen werden für Artikel in der Anwendung ausgeführt.

## Artikelübersicht {#articles-overview}

Artikel stellen den Text dar, der zusammen mit Kunst zur Informationsübermittlung verwendet wird.

>[!NOTE]
>
>In der Online-Hilfe finden Sie die folgenden Ressourcen, um mehr über die folgenden Themen in AEM Mobile-Apps zu erfahren:
>
>* [Betrachtungen zum Entwurf](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
   >
   >
* [Verwalten von Artikeln](https://helpx.adobe.com/digital-publishing-solution/help/creating-articles.html)

>



## Erstellen eines Artikels {#creating-an-article}

Der allgemeine Arbeitsablauf zum Erstellen eines Artikels lautet wie folgt:

1. Wählen Sie **Mobil** aus der Seitenleiste.
1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog.
1. Klicken Sie auf den Pfeil nach unten rechts oben in der Kachel **Artikel verwalten**.
1. Wählen Sie eine Artikelvorlage und klicken Sie auf **Weiter**.
1. Gehen Sie durch jeden Schritt des Assistenten, um mit der Erstellung des neuen Artikels fortzufahren.
1. Klicken Sie nach Abschluss der Vorbereitungen auf **Erstellen**.
1. Ihr neuer Artikel wird in der Kachel **Artikel verwalten** angezeigt.

## Importieren eines neuen Artikels {#importing-a-new-article}

Vorhandene Mobile On-Demand-Inhalte können von Mobile On-Demand heruntergeladen (importiert) werden, um sie zu AEM. Dadurch können lokale Inhalte bearbeitet und angezeigt werden.

>[!NOTE]
>
>Beim Importieren werden keine Bilder berücksichtigt.

Der Workflow zum Importieren eines neuen Artikels

1. Wählen Sie in Mobile die mobile On-Demand-App aus dem Katalog.
1. Klicken Sie auf den Pfeil nach unten rechts oben in der Kachel **Artikel verwalten** und wählen Sie Artikel importieren.
1. Klicken Sie im Dialogfeld auf **Artikel importieren** und schließen Sie dann.
1. Ihre Mobile On-Demand-Artikel werden jetzt in der Kachel **Artikel verwalten** angezeigt.

>[!CAUTION]
>
>Zuerst müssen Sie eine Mobile On-Demand-Verbindung herstellen.

![chlimage_1-3](assets/chlimage_1-3.gif)

## Bearbeiten eines Artikels {#editing-an-article}

Verwenden Sie den integrierten AEM Drag &amp; Drop-Editor, um einen Artikel hinzuzufügen oder zu ändern. Komponenten wie Text und Bilder können hinzugefügt/entfernt werden. Bilder aus DAM-Assets können eingefügt werden.

>[!CAUTION]
>
>Im Editor können nur in AEM erstellte Artikel geöffnet werden.

Der Workflow zum Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog.
1. Wählen Sie in der Kachel **Artikel verwalten** einen AEM Artikel aus.
1. Klicken Sie in der Ansicht Liste auf den markierten Artikel, um ihn im Inhaltseditor zu öffnen.
1. Verwenden Sie den Inhaltseditor, um Artikelinhalte (Manuskripte, Bilder, Text usw.) zu ziehen.

### Anzeigen und Bearbeiten der Metadaten in einem Artikel {#viewing-and-editing-the-metadata-within-an-article}

Inhalte wie Artikel, Banner usw. haben zahlreiche Eigenschaften wie Titel, Beschreibungen, Bilder. Diese Aktion wird zur Ansicht und Änderung solcher Eigenschaften verwendet. Optional können diese Änderungen beim Speichern in Mobile On-Demand hochgeladen werden.

Der allgemeine Arbeitsablauf zum Ansichten/Bearbeiten eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog.
1. Wählen Sie einen Artikel aus der Kachel **Artikel verwalten**.

1. Wählen Sie in der Aktionsleiste **Eigenschaften von Ansichten** aus.
1. Ansicht aller für diesen Artikel verfügbaren Metadaten.
1. Bearbeiten Sie die Metadaten nach Bedarf und klicken Sie nach Abschluss des Vorgangs auf **Speichern**.
1. Optional können Sie die Änderungen sofort in Mobile On-Demand hochladen.

## Hochladen eines Artikels {#uploading-an-article}

Mit der Upload-Aktion wird der ausgewählte Inhalt kopiert und einem Mobile On-Demand-Projekt hinzugefügt. Bereits vorhandene Mobile On-Demand-Inhalte werden durch die neue Version ersetzt.

Der allgemeine Arbeitsablauf zum Hochladen eines Artikels:

1. Wählen Sie unter **Mobil** Ihre Mobile On-Demand-App aus dem Katalog.
1. Wählen Sie in der Kachel **Artikel verwalten** einen Artikel zum Hochladen in Mobile On-Demand aus.
1. hinzufügen Sie bei Bedarf weitere Artikel aus der Ansicht Liste.
1. Wählen Sie **Upload** in der Aktionsleiste aus und klicken Sie dann im Dialogfeld auf Hochladen.
1. Ihre Artikel werden jetzt in Mobile On-Demand hochgeladen.

![chlimage_1-4](assets/chlimage_1-4.gif)

## Löschen eines Artikels {#deleting-an-article}

Durch diesen Vorgang werden die ausgewählten Inhalte aus Mobile On-Demand und optional aus der lokalen AEM gelöscht.

Der allgemeine Arbeitsablauf zum Löschen eines Artikels:

1. Wählen Sie in Mobile Ihre Mobile On-Demand-App aus dem Katalog.
1. Wählen Sie den zu löschenden Artikel in der Kachel **Artikel verwalten** aus.
1. Vergewissern Sie sich, dass sie in der Liste ausgewählt ist (wählen Sie nach Bedarf andere zum Löschen aus).
1. Klicken Sie in der Aktionsleiste auf **Löschen**.
1. Überprüfen Sie, ob Sie sowohl AEM als auch Mobile On-Demand löschen möchten.
1. Klicken Sie auf **Löschen**.
1. Ihr Artikel wurde jetzt aus der Liste entfernt.

![chlimage_1-5](assets/chlimage_1-5.gif)

### Die nächsten Schritte {#the-next-steps}

Informationen zum Verwalten von Artikeln finden Sie unter

* [Verwalten von Bannern](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Rückgängigmachen der Veröffentlichung des Inhalts](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
