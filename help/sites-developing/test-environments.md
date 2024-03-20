---
title: Welche Testumgebungen sind erforderlich?
description: Bei Tests sollten mehrere Umgebungen berücksichtigt werden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: 05f7a513-5ee7-4870-a691-4a0602e0cbb2
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 100%

---

# Welche Testumgebungen sind erforderlich?{#which-test-environments-will-be-needed}

Beim Definieren der Konfigurationen für Tests sollten Sie Folgendes beachten:

**Entwicklung**: Für Komponententests und bestimmte Integrationstests.

**Testen**: Für die meisten Tests.

**Live**: Für abschließende Leistungs- und Belastungstests. Auch für Akzeptanztests mit dem Kunden.

Legen Sie fest, welche Instanzen Sie benötigen und wo (normalerweise mindestens jeweils eine für alle Testebenen):

**Author**: In dieser Instanz können Autoren Inhalte eingeben und veröffentlichen.

**Publish**: Diese Instanz stellt die Website in veröffentlichter Form dar, auf die Besucher zugreifen können.

Mit dem Dispatcher getestet.

Schließlich muss die tatsächliche Hardware berücksichtigt werden – alle Leistungstests sollten auf einem System durchgeführt werden, das der Konfiguration der endgültigen Live-Umgebung so ähnlich wie möglich ist. Aus diesem Grund wird auch empfohlen, den Projekt-Launch wie folgt aufzuteilen:

**Soft Launch**: Reduzierte Verfügbarkeit, sodass Zeit für Leistungstests, Anpassungen und Optimierungen unter realistischen Bedingungen in der Produktionsumgebung bleibt.

**Hard Launch**: Vollständige Verfügbarkeit.
