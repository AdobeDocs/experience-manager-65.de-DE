---
title: Welche Testumgebungen sind erforderlich?
description: Bei Tests sollten mehrere Umgebungen berücksichtigt werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: 05f7a513-5ee7-4870-a691-4a0602e0cbb2
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 46%

---

# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Beim Definieren der Konfigurationen für Tests sollten Sie Folgendes beachten:

**Entwicklung**: Für Komponententests und bestimmte Integrationstests.

**Test** - Für die meisten Tests.

**Live**: Für abschließende Leistungs- und Belastungstests. Auch für Akzeptanztests mit dem Kunden.

Legen Sie fest, welche Instanzen Sie benötigen und wo (normalerweise mindestens eine für alle Testebenen):

**Author**: In dieser Instanz können Autoren Inhalte eingeben und veröffentlichen.

**Publish**: Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.

Mit dem Dispatcher getestet.

Schließlich muss die tatsächliche Hardware berücksichtigt werden - alle Leistungstests sollten auf einem System durchgeführt werden, das der Konfiguration der endgültigen Live-Umgebung so ähnlich wie möglich ist. Aus diesem Grund wird auch empfohlen, den Projekt-Launch in einen aufzuteilen:

**Soft Launch** - Geringere Verfügbarkeit, die Zeit für Leistungstests, Optimierung und Optimierung unter realistischen Bedingungen in der Produktionsumgebung lässt.

**Hard Launch**: Vollständige Verfügbarkeit.
