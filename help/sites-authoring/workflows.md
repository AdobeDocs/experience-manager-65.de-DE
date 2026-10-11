---
title: Arbeiten mit Workflows
description: In Adobe Experience Manager können Sie mit Workflows eine Reihe von Schritten automatisieren, die auf einer Seite oder bei einem Asset durchgeführt werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 7383d590-c6b7-440a-a33d-196dce9736ef
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Workflow
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
  - id: f6a6f91a-8819-530a-8e7b-c50884a25aef
    internal-label: Workflow
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 100%
---
# Arbeiten mit Workflows{#working-with-workflows}

Mit AEM-Workflows können Sie eine Reihe von Schritten automatisieren, die für (eine oder mehrere) Seiten und/oder Assets durchgeführt werden.

Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor eine oder ein Site-Admindie Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Die Autorin oder der Autor wendet den Workflow auf die Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.
1. Die Site-Admins erhalten dann ein Arbeitselement, das von ihnen die Aktivierung der Seite anfordert. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.

In der Regel gilt Folgendes:

* Inhaltsautorinnen und -autoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die von Ihnen verwendeten Workflows sind spezifisch für die Geschäftsprozesse Ihres Unternehmens.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
