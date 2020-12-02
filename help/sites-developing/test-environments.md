---
title: Welche Test-Umgebung sind erforderlich?
seo-title: Welche Test-Umgebung sind erforderlich?
description: Mehrere Umgebung sollten als Teil der Tests betrachtet werden
seo-description: Mehrere Umgebung sollten als Teil der Tests betrachtet werden
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 44%

---


# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Um zu definieren, welche Konfigurationen für Tests verwendet werden, sollten Sie Folgendes beachten:

**Entwicklung**  - Für Einheit und bestimmte Integrationstests.

**Prüfung**  - Für die Mehrzahl der Tests.

**Live** - Für Endleistungs- und Stresstests. Auch für Akzeptanztests mit dem Kunden.

Sie müssen auch entscheiden, welche Instanzen wo erforderlich sind (in der Regel mindestens eine für jede Teststufe):

**Autor** : Diese Instanz ermöglicht Autoren die Eingabe und Veröffentlichung von Inhalten.

**Publish**  - Diese Instanz stellt die Website in ihrem veröffentlichten Formular für den Zugriff von Besuchern dar.

Sollte in Verbindung mit dem Dispatcher getestet werden.

Als Letztes müssen Sie die verwendete Hardware berücksichtigen. Leistungstests sollten auf einem System ausgeführt werden, das möglichst ähnlich wie die endgültige Live-Umgebung konfiguriert ist. Daher wird empfohlen, den Projektstart wie folgt zu unterteilen:

**Soft Launch**  - reduzierte Verfügbarkeit; die Zeit für Leistungstests, Optimierungen und Optimierungen unter realistischen Bedingungen auf der Umgebung der Produktion lässt.

**Harter Start**  - Vollständige Verfügbarkeit.
