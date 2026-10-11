---
title: Demopaket für Assets Insights verwenden
description: Mithilfe des Demopakets können Sie Adobe Assets Insights aktivieren, um Daten aus einer Webseite zu erfassen und Statistiken dazu zu erstellen.
contentOwner: AG
role: User, Admin
feature: Asset Insights,Asset Reports
exl-id: 13947513-da76-43e1-ae01-abd24a59752a
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: a4e1c1f5-18fc-592e-bfc7-453ce6ae0030
    internal-label: Asset Insights
  - id: ac365bec-0634-4744-9473-c42f47320593
    internal-label: Asset management and governance
subfeature_v2:
  - id: c29e3a96-cd2b-4e21-b382-a8279aa04553
    internal-label: Asset reports
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%
---
# Demopaket für Assets Insights verwenden {#using-demo-package-for-asset-insights}

Mithilfe des Demopakets können Sie Adobe Assets Insights aktivieren, um Daten aus einer Beispiel-Webseite zu erfassen und Statistiken dazu zu erzeugen.

## [!DNL Use Experience Manager Assets] Insights mit Beispiel-Webseite  {#using-aem-assets-insights-with-sample-web-page}

1. Konfigurieren Sie Assets Insights anhand der Anleitungen unter [Konfigurieren von Assets Insights](configure-asset-insights.md).
1. Laden Sie das Assets-Beispielpaket unten herunter und installieren Sie das Paket über den CRXDE-Paket-Manager.

   [Datei laden](assets/insightsdemo.zip)

1. Laden Sie unten die ZIP-Datei herunter, die die Beispiel-Webseite enthält, und extrahieren Sie sie auf Ihrem lokalen Dateisystem.

   [Datei laden](assets/demosite.zip)

1. Klicken Sie auf die Web-Seite, um sie im Webbrowser zu öffnen.

   >[!CAUTION]
   >
   >Die Web-Seite ist so konfiguriert, dass Assets vom Localhost-Server geladen werden. Wenn Ihr Server an einer anderen Stelle ausgeführt wird, ändern Sie die Server-Adresse von „localhost“ zu der Server-Adresse im HTML-Inhalt der Web-Seite.

   >[!NOTE]
   >
   >Die externe Web-Seite kann sich in [!DNL Experience Manager] selbst befinden.
