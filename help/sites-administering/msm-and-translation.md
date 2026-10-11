---
title: Multi-Site Manager und Übersetzung
description: Erfahren Sie, wie Sie Ihre Inhalte projektübergreifend wiederverwenden und mehrsprachige Websites in Adobe Experience Manager verwalten können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
exl-id: 8f11f5de-f5af-4ce7-a448-2b4299de2930
solution: Experience Manager, Experience Manager Sites
feature: Multi Site Manager, Language Copy
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e86b80f2-7cb0-4646-8fcd-51d3bf272fce
    internal-label: Multi Site Manager
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 100%
---
# Multi-Site Manager und Übersetzung {#msm-and-translation}

Die folgenden Administrations-Tools sind für die Verwaltung von Websites und Seiten verfügbar:

* Multi Site Manager (MSM) ermöglicht Ihnen die Verwendung derselben Website-Inhalte an mehreren Stellen und lässt gleichzeitig Varianten zu:

  * [Wiederverwenden von Inhalten: Multi-Site Manager und Live Copy](/help/sites-administering/msm.md)

* Die Übersetzungsfunktion ermöglicht Ihnen die Automatisierung der Übersetzung von Seiteninhalten, Assets und nutzergenerierten Inhalten, um mehrsprachige Websites zu erstellen und zu pflegen:

  * [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md)

* Diese beiden Funktionen können kombiniert und für [internationale, mehrsprachige](#multinational-and-multilingual-sites) Websites eingesetzt werden.

## Internationale, mehrsprachige Websites {#multinational-and-multilingual-sites}

Sie können durch den kombinierten Einsatz von Multi-Site Manager und Übersetzungs-Workflow auf effiziente Weise Inhalte für internationale, mehrsprachige Websites erstellen. Erstellen Sie eine Primär-Site in einer Sprache und für ein bestimmtes Land und verwenden Sie diese Inhalte als Grundlage für die anderen Sites, wobei Sie diese bei Bedarf übersetzen lassen:

* [Übersetzen](/help/sites-administering/translation.md) Sie die primäre Website in verschiedene Sprachen.

* Verwenden Sie [Multi Site Manager](/help/sites-administering/msm.md) für Folgendes:

  * Sie können die Inhalte der Primär-Site sowie die zugehörigen Übersetzungen wiederverwenden, um Sites für andere Länder und Kulturen zu erstellen.
  * Achten Sie darauf, die Verwendung des Multi-Site Managers auf Inhalte in einer Sprache zu begrenzen, z. B. englische Primär-Site > englische Sprachzweige auf Länder-Sites, französische Primär-Site > französische Sprachzweige auf Länder-Sites.
  * Trennen Sie bei Bedarf Elemente von den Live Copies, um Lokalisierungsdetails hinzuzufügen.

Das folgende Diagramm veranschaulicht, wie sich die Hauptkonzepte überschneiden (es sind jedoch nicht alle beteiligten Ebenen/Elemente dargestellt):

![Abbildung der Hauptkonzepte der MSM- und Übersetzungsfunktion](assets/chlimage_1-71a.png)

>[!NOTE]
>
>Bei diesem und vergleichbaren Szenarien verwaltet MSM nicht die verschiedenen Sprachversionen als solche.
>
>* [MSM](/help/sites-administering/msm.md) verwaltet die Bereitstellung der übersetzten Inhalte von einem Blueprint (z. B. einem globalen Stamm) für die Live Copies (z. B. die lokalen Sites) innerhalb einer Sprache.
>* Die AEM-Integrationsfunktionen zur [Übersetzung](/help/sites-administering/translation.md) verwalten kombiniert mit Übersetzungs-Management-Services von Drittanbietern die Sprachen und die Übersetzung der Inhalte in diese verschiedenen Sprachen.
>
>Bei noch komplexeren Nutzungsszenarien kann MSM auch über Sprachstämme hinweg eingesetzt werden.

>[!NOTE]
>
>Bei allen Nutzungsszenarien wird empfohlen, die folgenden Best Practices zu lesen:
>
>* [Best Practices für MSM](/help/sites-administering/msm-best-practices.md); vor allem:
>
>   * [Erstellen einer Website](/help/sites-administering/msm-best-practices.md#create-site)
>   * [MSM und mehrsprachige Websites](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites)
>
>* [Best Practices für die Übersetzung](/help/sites-administering/tc-bp.md)
