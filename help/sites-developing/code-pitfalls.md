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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
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
