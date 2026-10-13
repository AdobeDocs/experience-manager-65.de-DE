---
title: Anzeigen von Seitenanalysedaten zur Messung der Effektivität des Seiteninhalts
description: Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
legacypath: /content/help/en/experience-manager/6-4/help/sites-authoring/pa-using.html
exl-id: 2e406512-47fb-451d-b837-0a3898ae1f08
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 97%
---
# Anzeigen von Seitenanalysedaten{#seeing-page-analytics-data}

Verwenden Sie Seitenanalysedaten, um die Effektivität des Seiteninhalts zu messen.

## In der Konsole sichtbare Analysen {#analytics-visible-from-the-console}

![spad-01](assets/spad-01.png)

Seitenanalysedaten werden in der [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) der Sites-Konsole angezeigt. Wenn die Seiten im Listenformat angezeigt werden, sind die folgenden Spalten standardmäßig verfügbar:

* Seitenansichten
* Unique Visitors
* Zeit auf Seite

Jede Spalte zeigt einen Wert für den aktuellen Berichtszeitraum an und zeigt dazu an, ob der Wert seit dem vorherigen Berichtszeitraum gestiegen oder gesunken ist. Die angezeigten Daten werden alle 12 Stunden aktualisiert.

>[!NOTE]
>
>Um den Aktualisierungszeitraum zu ändern, [konfigurieren Sie das Importintervall](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Öffnen Sie die **Sites**-Konsole, z. B. [https://localhost:4502/sites.html/content](https://localhost:4502/sites.html/content)
1. Klicken Sie ganz rechts in der Symbolleiste (rechte obere Ecke) auf das Symbol zur Auswahl der **Listenansicht** (das angezeigte Symbol hängt von der [aktuellen Ansicht](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) ab).

1. Klicken Sie erneut ganz rechts in der Symbolleiste (rechte obere Ecke) auf das Symbol und wählen Sie dann **Einstellungen anzeigen** aus. Das Dialogfeld **Spalten konfigurieren** öffnet sich. Nehmen Sie die erforderlichen Änderungen vor und bestätigen Sie den Vorgang mit **Aktualisieren**.

   ![spad-02](assets/spad-02.png)

### Auswählen des Berichtszeitraums {#selecting-the-reporting-period}

Wählen Sie den Berichtszeitraum aus, für den Analytics-Daten in der Sites-Konsole angezeigt werden:

* Daten der letzten 30 Tage
* Daten der letzten 90 Tage
* Daten aus diesem Jahr

Der aktuelle Berichtszeitraum wird in der Symbolleiste der Konsole „Sites“ (rechts neben der oberen Symbolleiste) angezeigt. Wählen Sie den gewünschten Berichtszeitraum über die Dropdown-Liste aus.

![aa-05](assets/aa-05.png)

### Konfigurieren der verfügbaren Datenspalten {#configuring-available-data-columns}

Mitglieder der Benutzergruppe „Analytics-Administratoren“ können die Sites-Konsole konfigurieren, damit Autorinnen und Autoren zusätzliche Analytics-Spalten sehen können.

>[!NOTE]
>
>Wenn ein Seitenbaum untergeordnete Elemente enthält, die verschiedenen Cloud-Konfigurationen von Adobe Analytics zugeordnet sind, können Sie die verfügbaren Datenspalten für die Seiten nicht konfigurieren.

1. Verwenden Sie in der Listenansicht die Ansichtsselektoren (rechts neben der Symbolleiste) und wählen Sie **Anzeigeeinstellungen** und anschließend **Benutzerdefinierte Analysedaten hinzufügen** aus.

   ![spad-03](assets/spad-03.png)

1. Wählen Sie die Metriken aus, die Sie Autoren in der Sites-Konsole bereitstellen möchten, und klicken Sie dann auf **Hinzufügen**.

   Die angezeigten Spalten werden aus Adobe Analytics abgerufen.

   ![aa-16](assets/aa-16.png)

### Öffnen von Inhaltseinblicken mithilfe von Sites {#opening-content-insights-from-sites}

Öffnen Sie [Inhaltseinsicht](/help/sites-authoring/content-insights.md) von der Konsole „Sites“ aus, um die Seiteneffektivität weiter zu untersuchen.

1. Wählen Sie in der Sites-Konsole die Seite aus, für die Sie Inhaltseinblicke anzeigen möchten.
1. Klicken Sie in der Symbolleiste auf das Symbol „Analysen und Empfehlungen“.

   ![Symbol „Analytics und Empfehlungen“](do-not-localize/chlimage_1-14.png)

## Im Seiteneditor sichtbare Analysen (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!CAUTION]
>
>Aufgrund von Sicherheitsänderungen in der Adobe Analytics-API ist es nicht mehr möglich, die in AEM enthaltene Version von Activity Map zu verwenden.
>
>Ab jetzt sollte das [über Adobe Analytics bereitgestellte Activity Map-Plug-in](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=de) verwendet werden.
