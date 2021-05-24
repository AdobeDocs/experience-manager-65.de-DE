---
title: Arbeiten mit Workflows
seo-title: Arbeiten mit Workflows
description: Workflows in AEM ermöglichen es Ihnen, eine Reihe von Schritten zu automatisieren, die auf einer Seite oder bei einem Asset durchgeführt werden.
seo-description: Workflows in AEM ermöglichen es Ihnen, eine Reihe von Schritten zu automatisieren, die auf einer Seite oder bei einem Asset durchgeführt werden.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 7383d590-c6b7-440a-a33d-196dce9736ef
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 100%

---

# Arbeiten mit Workflows{#working-with-workflows}

AEM-Workflows ermöglichen es Ihnen, eine Reihe von Schritten zu automatisieren, die an Seiten und/oder Assets ausgeführt werden.

Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor ein Site-Administrator die Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Der Autor wendet den Workflow auf der Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn er fertig ist, wird angegeben, dass sein Arbeitselement abgeschlossen ist.
1. Der Site-Administrator erhält dann ein Arbeitselement, das die Aktivierung der Seite anfordert. Wenn er fertig ist, wird angegeben, dass sein Arbeitselement abgeschlossen ist.

In der Regel gilt:

* Inhaltsautoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die Workflows, die Sie verwenden, sind für die Geschäftsprozesse Ihres Unternehmens spezifisch.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
