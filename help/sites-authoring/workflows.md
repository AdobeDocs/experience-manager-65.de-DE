---
title: Arbeiten mit Workflows
description: In Adobe Experience Manager können Sie mit Workflows eine Reihe von Schritten automatisieren, die auf einer Seite oder bei einem Asset durchgeführt werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 7383d590-c6b7-440a-a33d-196dce9736ef
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
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
