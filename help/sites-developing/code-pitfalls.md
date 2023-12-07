---
title: Fallstricke beim Programmieren
description: Häufige Fallstricke beim Programmieren bei der Entwicklung für AEM vermeiden
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: c448c5d5-def8-4c1a-8db4-41eb49d0cd20
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 10%

---

# Fallstricke beim Programmieren{#code-pitfalls}

## Vermeiden von Sling-Bindungen in Java-Code {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 % der Fälle eine ungeeignete Methode, auf einen Dienst zuzugreifen. Verwenden Sie stattdessen *@reference* oder *@Inject* Anmerkungen.

## Thread.interrupt im Java-Code vermeiden {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* ist gefährlich, da Dateien, einschließlich Lucene-Dateien und persistente Cache-Dateien, geschlossen werden können, wenn sie zur falschen Zeit aufgerufen werden.

## Vermeiden Sie das Mischen von Java-Synchronisation mit ReadWriteLocks {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu einer Wettlaufsituation führen, in der der Code schließlich zum Stillstand kommt.
