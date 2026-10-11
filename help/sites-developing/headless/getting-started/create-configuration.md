---
title: 'Schnellstartanleitung für Headless: Erstellen einer Konfiguration'
description: Erstellen Sie als ersten Schritt eine Konfiguration, um mit Headless in AEM 6.5 zu beginnen.
exl-id: f1df97a1-164f-4ed4-bb63-34caf35ae27c
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d429a63e-ade4-4117-b04e-9b996d1c94ef
    internal-label: Integrations
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: a02b73a7-bdfc-4225-bdfd-69f7891ab55e
    internal-label: GraphQL
  - id: d781bc8f-52af-43f6-84d0-b73e59a130d5
    internal-label: Persisted queries
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 91%
---
# Schnellstartanleitung für Headless: Erstellen einer Konfiguration {#creating-configuration}

Als ersten Schritt für den Einstieg in Headless in AEM 6.5 müssen Sie eine Konfiguration erstellen.

## Was ist eine Konfiguration? {#what-is-a-configuration}

Der Konfigurations-Browser bietet eine generische Konfigurations-API, eine Inhaltsstruktur und einen Auflösungsmechanismus für Konfigurationen in AEM.

Stellen Sie sich im Kontext von Headless-Content-Management in AEM eine Konfiguration als einen Arbeitsplatz in AEM vor, an dem Sie Ihre Inhaltsmodelle erstellen können, die die Struktur Ihrer zukünftigen Inhalte und Inhaltsfragmente definieren. Sie können über mehrere Konfigurationen verfügen, um diese Modelle zu trennen.

>[!NOTE]
>
>Wenn Sie mit [Seitenvorlagen in einer Full-Stack-AEM-Implementierung](/help/sites-authoring/templates.md) vertraut sind, ist die Verwendung von Konfigurationen für die Verwaltung von Inhaltsmodellen ähnlich.

## Erstellen einer Konfiguration {#how-to-create-a-configuration}

Ein Administrator muss eine Konfiguration nur einmal oder sehr selten erstellen, wenn für die Organisation Ihrer Inhaltsmodelle ein neuer Arbeitsbereich erforderlich ist. Für die Zwecke dieser ersten Schritte müssen wir nur eine Konfiguration erstellen.

1. Melden Sie sich bei AEM an und wählen Sie im Hauptmenü **Tools > Allgemein > Konfigurations-Browser** aus.
1. Geben Sie einen **Titel** für Ihre Konfiguration ein.
   * Der Name wird automatisch auf der Grundlage des Titels generiert und gemäß den [AEM-Benennungskonventionen &#x200B;](/help/sites-developing/naming-conventions.md). Er wird zum Knotennamen im Repository.
1. Überprüfen Sie die folgenden Optionen:
   * **Inhaltsfragmentmodelle**
   * **Persistente GraphQL-Abfragen**

   ![Konfiguration erstellen](assets/create-configuration.png)

1. Klicken Sie auf **Erstellen**.

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
