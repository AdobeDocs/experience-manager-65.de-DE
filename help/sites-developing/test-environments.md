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
exl-id: 05f7a513-5ee7-4870-a691-4a0602e0cbb2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 44%

---

# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Um zu bestimmen, welche Konfigurationen getestet werden sollen, sollten Sie Folgendes beachten:

**Entwicklung**  - für Einheiten und bestimmte Integrationstests.

**Test**  - Für die meisten Tests.

**Live** : Für Leistungs- und Belastungstests. Auch für Akzeptanztests mit dem Kunden.

Sie müssen auch entscheiden, welche Instanzen wo erforderlich sind (in der Regel mindestens eine für jede Teststufe):

**Autor**  - Diese Instanz ermöglicht es Autoren, Inhalte einzugeben und zu veröffentlichen.

**Veröffentlichen**  - Diese Instanz stellt die Website in ihrem veröffentlichten Formular für den Zugriff von Besuchern dar.

Sollte in Verbindung mit dem Dispatcher getestet werden.

Als Letztes müssen Sie die verwendete Hardware berücksichtigen. Leistungstests sollten auf einem System ausgeführt werden, das möglichst ähnlich wie die endgültige Live-Umgebung konfiguriert ist. Daher wird empfohlen, den Projektstart wie folgt zu unterteilen:

**Soft Launch**  - reduzierte Verfügbarkeit die Zeit für Leistungstests, Optimierung und Optimierung unter realistischen Bedingungen in der Produktionsumgebung lässt.

**Hard Launch**  - Vollständige Verfügbarkeit.
