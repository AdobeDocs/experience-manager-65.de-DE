---
title: Media Library für grundlegende digitale Asset-Verwaltung verwenden
description: '[!DNL Experience Manager Assets] und Media Library für die Asset-Verwaltung.'
contentOwner: AG
role: Architect, Leader
feature: Asset-Verwaltung
exl-id: e10d632d-1d90-4f28-8617-95ee41602997
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 2%

---

<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Media Library für grundlegende Asset-Verwaltung verwenden {#manage-assets-using-media-library}

[!DNL Adobe Experience Manager] Die Plattform bietet verschiedene Funktionen zum Verwalten von Assets. Mit Media Library können Benutzer eine kleine Anzahl von Assets in das Repository hochladen, diese auf den Webseiten suchen und verwenden und einfache Asset-Verwaltungsaufgaben für die Assets ausführen.

Media Library ist eine einfache DAM-Lösung (Digital Asset Management), die im Lieferumfang einer [!DNL Adobe Experience Manager Sites] -Lizenz enthalten ist. [!DNL Sites] ist ein WCM-Angebot (Web Content Management). Media Library arbeitet mit allen Funktionen von Experience Manager.

[!DNL Adobe Experience Manager Assets] -Lizenz ist separat erhältlich. [!DNL Experience Manager Assets] ermöglicht eine robuste Verarbeitung von Assets über Anwendungsfälle für Unternehmen, Anpassungen für Metadaten, Schemata, Suchen und die Benutzeroberfläche sowie viele andere Funktionen, die über das von Media Library bereitgestellte hinausgehen.

## Lizenzanforderungen {#avail-media-library-license}

Kunden, die über eine [!DNL Sites] -Lizenz verfügen, sind berechtigt, Media Library zu verwenden. Es funktioniert mit allen Komponenten von [!DNL Experience Manager].

Media Library wird als Teil von Sites installiert. Über die Sites-Lizenz und -Installation hinaus ist keine zusätzliche Lizenz oder kein Paket erforderlich.

## [!DNL Assets] versus Media Library  {#assets-and-media-library}

Experience Manager Assets bietet DAM-Funktionen von Unternehmensklassen. Die Asset-Funktionalität wird mit [!DNL Experience Manager] in einem einzigen Paket bereitgestellt. Benutzer, die keine Assets-Lizenz erworben haben, sind jedoch nicht berechtigt, die erweiterten DAM-Funktionen zu verwenden. Ohne Assets-Lizenz sind nur [Media Library-Funktionen](#use-media-library) verfügbar.

Wenn Sie eine unbeabsichtigte Verwendung von nicht lizenzierten [!DNL Assets]-Funktionen verhindern möchten, entfernen Sie alle [!DNL Assets]-spezifischen Workflows, Komponenten, Taxonomien, Optionen und den [!DNL Assets]-Administrator aus [!DNL Experience Manager]. Dadurch wird verhindert, dass Ihre Benutzer versehentlich [!DNL Assets] Funktionen verwenden, die Sie nicht lizenziert haben.

## Media Library {#use-media-library} verwenden

Media Library deckt im Großen und Ganzen die folgenden Anwendungsfälle ab:

* Stellen Sie grundlegende DAM-Funktionen für Web-Seiten bereit, die mit [!DNL Adobe Experience Manager Sites] erstellt wurden.
* Adaptive Formulare und Kommunikationen, die mit [!DNL Adobe Experience Manager Forms] erstellt wurden.
* Mit [!DNL Adobe Experience Manager Screens] erstellte digitale Bildschirmerlebnisse.
* [!DNL Assets] HTTP-REST-APIs für Headless-Vorgänge.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Basic metadata properties
* Tag management
* Version control
* Static renditions
* Projects, tasks, workflow authoring
* Activity stream (timeline)
* Query Builder (API)
* Marketing Cloud integration
* User interface customization and extension
* Comments and annotation
-->

Um die Media Library-Funktion zu verwenden, können Sie die Standardbenutzeroberfläche [!DNL Experience Manager] verwenden. Media Library ist Teil der [!DNL Experience Manager Sites]-Installation und es ist keine separate Schnittstelle oder Add-on erforderlich. Über die vorhandene Benutzeroberfläche sind Media Library-Benutzer berechtigt, die folgenden Aufgaben auszuführen:

* Erstellen Sie Ordner zum Organisieren von Assets.
* Hochladen von Assets.
* Veröffentlichen von Assets.
* Bearbeiten, verschieben und kopieren Sie Assets.
* Assets durchsuchen, filtern und suchen (einschließlich Ähnlichkeitssuche).
* Fügen Sie Werte zu den Metadatenfeldern hinzu und bearbeiten Sie sie, mit Ausnahme von Smart-Tags, die standardmäßig auf der Registerkarte [!UICONTROL Einfach] der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar sind.
* Hinzufügen und Löschen von statischen Ausgabeformaten.
* Herunterladen von Ordnern, Assets und Asset-Ausgabedarstellungen.
* Erstellen Sie Asset-Versionen.
* Erstellen Sie Assets und führen Sie Prüfungsaufgaben für Assets durch.
* Kommentieren von Assets.
* Fügen Sie über Content Finder Assets zu [!DNL Sites]-Seiten hinzu.
* Verwenden [!DNL Content Fragments].

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?
-->

>[!IMPORTANT]
>
>Viele erweiterte DAM-Anwendungsfälle werden von [!DNL Experience Manager Assets] erfüllt. Media Library-Lizenz berechtigt Sie, nur die aufgelisteten Anwendungsfälle mit Media Library zu erfüllen. Wenn ein Anwendungsfall nicht aufgeführt ist, verwenden Sie ihn nicht mit der Media Library-Lizenz. Wenden Sie sich bei Fragen an die Kundenunterstützung von Adobe.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [DAM-Funktionen in [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/home.html?lang=de)
>* [[!DNL Experience Manager] 6.5 Managed Services - Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager] 6.5 On-Premise-Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

