---
title: Inhaltsfragmente – Konfigurationsbrowser
description: Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurationsbrowser aktivieren, um die leistungsstarken Funktionen von Adobe Experience Manager für die Headless-Bereitstellung zu nutzen.
feature: Content Fragments
role: User
exl-id: a9990b0c-56c7-4e61-bae9-98e19a7f364e
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: a45b1e7f-e65f-4cd3-be86-5cec5d9449ef
    internal-label: Content management
subfeature_v2:
  - id: b7f5d1e0-aa2f-4a55-83f4-c2b35a8bd3a7
    internal-label: Content fragments
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%
---
# Inhaltsfragmente – Konfigurationsbrowser{#content-fragments-configuration-browser}

Erfahren Sie, wie Sie bestimmte Inhaltsfragmentfunktionen im Konfigurationsbrowser aktivieren, um die leistungsstarken Funktionen von Adobe Experience Manager (AEM) für die Headless-Bereitstellung zu nutzen.

## Aktivieren der Funktionen für Inhaltsfragmente für Ihre Instanz {#enable-content-fragment-functionality-instance}

Bevor Sie Inhaltsfragmente verwenden können, müssen Sie den **Konfigurationsbrowser** verwenden, um Folgendes zu aktivieren:

* **Inhaltsfragmentmodelle** – obligatorisch
* **Persistente GraphQL-Abfragen** – optional

>[!CAUTION]
>
>Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren:
>
>* ist die Option **Erstellen** für das Erstellen von Modellen nicht verfügbar.
>* können Sie nicht [die Sites-Konfiguration auswählen, um den entsprechenden Endpunkt zu erstellen](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint).

Um die Funktion für Inhaltsfragmente zu aktivieren, müssen Sie die folgenden Schritte ausführen:

* Aktivieren Sie die Verwendung der Inhaltsfragmentfunktionen im Konfigurationsbrowser.
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an.

### Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser {#enable-content-fragment-functionality-in-configuration-browser}

Um [bestimmte Inhaltsfragmentfunktionen](#creating-a-content-fragment-model) zu nutzen, **müssen** Sie diese zunächst über den **Konfigurationsbrowser** aktivieren:

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurationsbrowser](/help/sites-administering/configurations.md#using-configuration-browser).

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.

1. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   1. Um ihre Verwendung zu aktivieren, wählen Sie
      * **Inhaltsfragmentmodelle**
      * **Persistente GraphQL-Abfragen**

      ![Konfiguration definieren](assets/cfm-conf-01.png)

1. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

<!-- 1. Select the location appropriate to your website. -->

### Anwenden der Konfiguration auf Ihren Assets-Ordner {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **Global** für die Inhaltsfragmentfunktionalität aktiviert ist, gilt sie für jeden Assets-Ordner.

Um andere Konfigurationen (d. h. nicht global) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Wählen Sie dazu die entsprechende **Konfiguration** in der Registerkarte **Cloud-Services** der **Ordnereigenschaften** des entsprechenden Ordners aus.

![Konfiguration anwenden](assets/cfm-conf-02.png)
