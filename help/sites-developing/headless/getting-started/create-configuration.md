---
title: 'Schnellstartanleitung für Headless: Erstellen einer Konfiguration'
description: Erstellen Sie eine Konfiguration als ersten Schritt zu den ersten Schritten mit Headless in AEM 6.5.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
source-git-commit: 8ab774b8d21dd16e4873cd39ef0175ead3f2da23
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 74%

---

# Schnellstartanleitung für Headless: Erstellen einer Konfiguration {#creating-configuration}

Als ersten Schritt zu den ersten Schritten mit Headless in AEM 6.5 müssen Sie eine Konfiguration erstellen.

## Was ist eine Konfiguration? {#what-is-a-configuration}

Der Konfigurations-Browser bietet eine generische Konfigurations-API, eine Inhaltsstruktur und einen Auflösungsmechanismus für Konfigurationen in AEM.

Stellen Sie sich im Kontext von Headless-Content-Management in AEM eine Konfiguration als einen Arbeitsplatz in AEM vor, an dem Sie Ihre Inhaltsmodelle erstellen können, die die Struktur Ihrer zukünftigen Inhalte und Inhaltsfragmente definieren. Sie können über mehrere Konfigurationen verfügen, um diese Modelle zu trennen.

>[!NOTE]
>
>Wenn Sie mit [Seitenvorlagen in einer Full-Stack-AEM-Implementierung](/help/sites-authoring/templates.md) vertraut sind, ist die Verwendung von Konfigurationen für die Verwaltung von Inhaltsmodellen ähnlich.

## Erstellen einer Konfiguration {#how-to-create-a-configuration}

Ein Administrator muss eine Konfiguration nur einmal oder sehr selten erstellen, wenn für die Organisation Ihrer Inhaltsmodelle ein neuer Arbeitsbereich erforderlich ist. Für die Zwecke dieser ersten Schritte müssen wir nur eine Konfiguration erstellen.

1. Melden Sie sich bei AEM an und wählen Sie im Hauptmenü die Option **Tools -> Allgemein -> Konfigurationsbrowser**.
1. Bereitstellung einer **Titel** für Ihre Konfiguration.
   * Ein Name wird automatisch basierend auf dem Titel generiert und entsprechend [AEM Benennungskonventionen.](/help/sites-developing/naming-conventions.md). Sie wird zum Knotennamen im Repository.
1. Überprüfen Sie die folgenden Optionen:
   * **Inhaltsfragmentmodelle**
   * **Persistente GraphQL-Abfragen**

   ![Konfiguration erstellen](../assets/create-configuration.png)

1. Tippen oder klicken Sie auf **Erstellen**

Sie können bei Bedarf mehrere Konfigurationen erstellen. Konfigurationen können auch verschachtelt sein.

>[!NOTE]
>
>Abhängig von Ihren Implementierungsanforderungen können zusätzlich zu **Inhaltsfragmentmodellen** und **persistenten GraphQL-Abfragen** Konfigurationsoptionen erforderlich sein.

## Nächste Schritte {#next-steps}

Mit dieser Konfiguration können Sie nun mit dem zweiten Teil der ersten Schritte fortfahren und [Inhaltsfragmentmodelle](create-content-model.md) erstellen.

<!--
>[!TIP]
>
>For complete details about the Configuration Browser, [see the Configuration Browser documentation.](/help/sites-developing/configurations.md)
-->
