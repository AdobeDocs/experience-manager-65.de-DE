---
title: Fallstricke beim Programmieren
description: Häufige Fallstricke beim Programmieren, die Sie bei der Entwicklung für AEM vermeiden sollten
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: c448c5d5-def8-4c1a-8db4-41eb49d0cd20
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 100%

---

# Fallstricke beim Programmieren{#code-pitfalls}

## Sling-Bindungen im Java-Code vermeiden {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 % der Fälle ungeeignet, um Zugriff auf einen Dienst zu erhalten. Stattdessen sollten Sie *@Reference*- oder *@Inject*-Anmerkungen verwenden.

## Thread.interrupt im Java-Code vermeiden {#avoid-thread-interrupt-in-java-code}

Bei *Thread.interrupt* ist Vorsicht geboten, da diese Methode Dateien, darunter Lucene-Dateien und persistente Cache-Dateien, schließen kann, wenn sie zum falschen Zeitpunkt aufgerufen wird.

## Mischen von Java-Synchronisierung mit ReadWriteLocks vermeiden {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu Überschneidungen führen, bei denen der Code irgendwann zum Stillstand kommt.
