---
title: Welche Testumgebungen sind erforderlich?
seo-title: Welche Testumgebungen sind erforderlich?
description: Mehrere Umgebungen sollten als Teil von Tests betrachtet werden
seo-description: Mehrere Umgebungen sollten als Teil von Tests betrachtet werden
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Um zu definieren, welche Konfigurationen für Tests verwendet werden, sollten Sie Folgendes beachten:

**Entwicklung** - Für Einheiten und bestimmte Integrationstests.

**Test** - Für die Mehrzahl der Tests.

**Live** - Für Endleistungs- und Stresstests. Auch für Akzeptanztests mit dem Kunden.

Sie müssen auch entscheiden, welche Instanzen wo erforderlich sind (in der Regel mindestens eine für jede Teststufe):

**Autor** - In dieser Instanz können Autoren Inhalte eingeben und veröffentlichen.

**Publish** - Diese Instanz stellt die Website in ihrem veröffentlichten Formular für den Zugriff von Besuchern dar.

Sollte in Verbindung mit dem Dispatcher getestet werden.

Als Letztes müssen Sie die verwendete Hardware berücksichtigen. Leistungstests sollten auf einem System ausgeführt werden, das möglichst ähnlich wie die endgültige Live-Umgebung konfiguriert ist. Daher wird empfohlen, den Projektstart wie folgt zu unterteilen:

**Soft Launch** - reduzierte Verfügbarkeit die Zeit für Leistungstests, Abstimmung und Optimierung unter realistischen Bedingungen in der Produktionsumgebung erlaubt.

**Harter Start** - Vollständige Verfügbarkeit.
