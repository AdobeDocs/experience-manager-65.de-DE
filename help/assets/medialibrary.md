---
title: Media Library für grundlegende Verwaltung von digitalen Assets verwenden
description: '[!DNL Experience Manager Assets] und Media Library für das Asset-Management.'
contentOwner: AG
role: Architect, Leader
feature: Asset Management
exl-id: e10d632d-1d90-4f28-8617-95ee41602997
source-git-commit: 823f36bb7eab6c74a07f90883fa040428d8f8420
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 80%

---


# Media Library für grundlegendes Asset-Management verwenden {#manage-assets-using-media-library}

Die [!DNL Adobe Experience Manager]-Plattform bietet verschiedene Funktionen zum Verwalten von Assets. Mit Media Library können Benutzer eine kleine Anzahl von Assets in das Repository hochladen, diese auf den Web-Seiten suchen und verwenden und einfache Asset-Management-Aufgaben für die Assets ausführen.

Media Library ist eine einfache DAM-Lösung (Digital Asset Management), die im Lieferumfang einer [!DNL Adobe Experience Manager Sites]-Lizenz enthalten ist. [!DNL Sites] ist ein WCM-Angebot (Web Content Management). Media Library arbeitet mit allen Funktionen von Experience Manager.

Die [!DNL Adobe Experience Manager Assets]-Lizenz kann separat erworben werden. [!DNL Experience Manager Assets] ermöglicht eine robuste Handhabung von Assets über Anwendungsfälle für Unternehmen, Anpassungen für Metadaten, Schemas, Suchen und die Benutzeroberfläche sowie viele andere Funktionen, die über die von Media Library bereitgestellten hinausgehen.

## Lizenzanforderungen {#avail-media-library-license}

Kunden, die über eine [!DNL Sites]-Lizenz verfügen, sind berechtigt, Media Library zu verwenden. Es funktioniert mit allen Komponenten von [!DNL Experience Manager].

Media Library wird als Teil von Sites installiert. Über die Sites-Lizenz und -Installation hinaus ist keine zusätzliche Lizenz und kein Package erforderlich.

## [!DNL Assets] im Vergleich mit Media Library {#assets-and-media-library}

Experience Manager Assets bietet DAM-Funktionen im Unternehmensmaßstab. Die Funktionalität vo Assets wird mit [!DNL Experience Manager] in einem einzigen Package bereitgestellt. Benutzer, die keine Assets-Lizenz erworben haben, sind nicht berechtigt, die erweiterten DAM-Funktionen zu verwenden. Ohne Assets-Lizenz sind nur [Media Library-Funktionen](#use-media-library) verfügbar.

Wenn Sie eine unbeabsichtigte Verwendung von nicht lizenzierten [!DNL Assets]-Funktionen verhindern möchten, entfernen Sie alle [!DNL Assets]-spezifischen Workflows, Komponenten, Taxonomien, Optionen und den [!DNL Assets]-Administrator aus [!DNL Experience Manager]. Hierdurch verhindern Sie, dass Benutzer versehentlich [!DNL Assets]-Funktionen nutzen, für die Sie keine Lizenz haben.

## Media Library verwenden {#use-media-library}

Media Library bietet grundlegende DAM-Funktionen für die folgenden Anwendungsfälle:

* Mit [!DNL Adobe Experience Manager Sites] erstellte Webseiten.
* Adaptive Formulare und Kommunikationen, die mit [!DNL Adobe Experience Manager Forms] erstellt wurden.
* Mit [!DNL Adobe Experience Manager Screens] erstellte digitale Bildschirmerlebnisse.
* [!DNL Assets]-HTTP-REST-APIs für Headless-Vorgänge.

<!--
 TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.
* Static renditions

-->

Um die Media Library-Funktionalität zu verwenden, können Sie die Standardbenutzeroberfläche von [!DNL Experience Manager] verwenden. Media Library ist Teil der [!DNL Experience Manager Sites]-Installation und es ist keine separate Oberfläche oder Add-on erforderlich. Über die vorhandene Benutzeroberfläche sind Media Library-Benutzer berechtigt, die folgenden Aufgaben auszuführen:

* Erstellen von Ordnern zum Organisieren von Assets.
* Hochladen von Assets.
* Veröffentlichen von Assets.
* Bearbeiten, Verschieben und Kopieren von Assets.
* Durchsuchen, Filtern und Suchen (einschließlich Ähnlichkeitssuche) von Assets.
* Hinzufügen von Werten zu den Metadatenfeldern und ihre Bearbeitung, mit Ausnahme von Smart-Tags, die standardmäßig auf der Registerkarte [!UICONTROL Standard] der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar sind.
* Hinzufügen und Löschen von statischen Ausgabedarstellungen.
* Herunterladen von Ordnern, Assets und Asset-Ausgabedarstellungen.
* Erstellen von Asset-Versionen.
* Erstellen von Assets und Durchführen von Prüfungsaufgaben für Assets.
* Kommentieren von Assets.
* Hinzufügen von Assets zu [!DNL Sites]-Seiten über die Content-Suche.
* Verwenden von [!DNL Content Fragments].
* Verwenden Sie HTTP REST- und GraphQL-APIs für [!DNL Content Fragments] und referenzierte Medien-Assets unter Sites-Lizenz.
* Marketing Cloud-Integration.
* Anpassen und Erweitern der Benutzeroberfläche für die Asset-Verwaltung.
* Greifen Sie auf Query Builder (API) zu, um die Suchfunktion zu erweitern.
* Erstellen Sie statische Tags.
* Erstellen von Projekten und Aufgaben.
* Aktivitäts-Stream (Zeitleiste).
* Kommentare und Anmerkungen.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we don't have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Viele erweiterte DAM-Anwendungsfälle werden von [!DNL Experience Manager Assets] erfüllt. Die Media Library-Lizenz berechtigt Sie nur dazu, die aufgelisteten Anwendungsfälle mit Media Library zu erfüllen. Wenn ein Anwendungsfall nicht aufgeführt ist, wenden Sie ihn nicht mit der Media Library-Lizenz an. Wenden Sie sich bei Fragen an den Support von Adobe.

Beachten Sie, dass Sie keine Smart-Tags, [!DNL Asset]-Links, [!DNL Asset]-Selektoren, Massen-Tagging, Ändern von Asset-Workflows oder standardmäßigen [!DNL Adobe Experience Manager]-Benutzeroberflächen verwenden können, um ohne [!DNL Assets]-Lizenz auf Media Library zuzugreifen.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [DAM-Funktionen in  [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/home.html?lang=de)
>* [[!DNL Experience Manager] 6.5 Managed Services - Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager] 6.5 On-Premise-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

