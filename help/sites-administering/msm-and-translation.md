---
title: Website-Administration
seo-title: Website Administration
description: Erfahren Sie, wie Sie mehrsprachige Websites mit Adobe Experience Manager verwalten.
seo-description: Learn how to manage multilingual websites in AEM.
uuid: a32d458b-a5ad-46ef-a68c-4717c63b4bdd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: fabaa3e8-1657-4ed4-abb2-990117bec39c
exl-id: 8f11f5de-f5af-4ce7-a448-2b4299de2930
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 50%

---

# Website-Administration{#website-administration}

Die folgenden Administrations-Tools sind für die Verwaltung von Websites und Seiten verfügbar:

* Multi Site Manager (MSM) ermöglicht Ihnen die Verwendung derselben Website-Inhalte an mehreren Stellen und lässt gleichzeitig Varianten zu:

   * [Wiederverwenden von Inhalten: Multi Site Manager und Live Copy](/help/sites-administering/msm.md)

* Mit der Übersetzung können Sie die Übersetzung von Seiteninhalten, Assets und benutzergenerierten Inhalten automatisieren, um mehrsprachige Websites zu erstellen und zu verwalten:

   * [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md)

* Diese beiden Funktionen können kombiniert werden, um Websites zu unterstützen, die beide [Mehrsprachige und mehrsprachige Inhalte](#multinational-and-multilingual-sites).

## Internationale, mehrsprachige Websites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Websites erstellen. Erstellen Sie eine Master-Site in einer Sprache für ein bestimmtes Land und verwenden Sie diesen Inhalt dann als Grundlage für die anderen Sites, wobei Sie bei Bedarf eine Übersetzung verwenden:

* [Übersetzen](/help/sites-administering/translation.md) Sie die primäre Website in verschiedene Sprachen.

* Verwenden Sie [Multi Site Manager](/help/sites-administering/msm.md) für Folgendes:

   * Verwenden Sie Inhalte von der Master-Site und die Übersetzungen erneut, um Sites für andere Länder und Kulturen zu erstellen.
   * Stellen Sie sicher, dass Sie die Verwendung von Multi Site Manager auf Inhalte in einer Sprache beschränken, z. B. auf englische Master > englische Sprachzweige auf Länderseiten, französische Master > französische Sprachzweige auf Länderseiten.
   * Trennen Sie bei Bedarf die Elemente der Live Copies, um Lokalisierungsdetails hinzuzufügen.

Das folgende Diagramm veranschaulicht, wie sich die Hauptkonzepte überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Abbildung der wichtigsten Konzepte von MSM und Übersetzung](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.
>
>* [MSM](/help/sites-administering/msm.md) verwaltet die Bereitstellung übersetzter Inhalte von einem Blueprint (z. B. einem globalen Master) zu den Live Copies (z. B. den lokalen Sites) innerhalb der Grenzen einer Sprache.
>* Die AEM-Integrationsfunktionen zur [Übersetzung](/help/sites-administering/translation.md) verwalten kombiniert mit Übersetzungs-Management-Services von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.
>
>Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprachstämme hinweg eingesetzt werden.

>[!NOTE]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md); insbesondere:
>
>   * [Erstellen einer Website](/help/sites-administering/msm-best-practices.md#create-site)
>   * [MSM und mehrsprachige Websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md)
