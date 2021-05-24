---
title: Fallstricke beim Programmieren
seo-title: Fallstricke beim Programmieren
description: Allgemeine Fallstricke beim Programmieren, die Sie bei der Entwicklung für AEM vermeiden sollten
seo-description: Allgemeine Fallstricke beim Programmieren, die Sie bei der Entwicklung für AEM vermeiden sollten
uuid: e7413bdc-4889-45ff-bdcb-b0893d33a3b7
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 01362026-a696-4a5d-94e9-ea784eaa6e4b
exl-id: c448c5d5-def8-4c1a-8db4-41eb49d0cd20
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 94%

---

# Fallstricke beim Programmieren{#code-pitfalls}

## Sling-Bindungen im Java-Code vermeiden {#avoid-sling-bindings-in-java-code}

Sling-Bindungen sind in 90 Prozent der Fälle keine gute Möglichkeit, auf einen Dienst zuzugreifen. Verwenden Sie stattdessen die Anmerkungen *@Reference* oder *@Inject*.

## Vermeiden Sie Thread.interrupt in Java-Code {#avoid-thread-interrupt-in-java-code}

*Thread.interrupt* ist riskant, da es Dateien (darunter auch Lucene-Dateien und persistente Cache-Dateien) schließen kann, wenn es zum falschen Zeitpunkt aufgerufen wird.

## Mischen von Java-Synchronisierung mit ReadWriteLocks vermeiden  {#avoid-mixing-java-synchronization-with-readwritelocks}

Dies kann zu Überschneidungen führen, bei denen der Code irgendwann zum Stillstand kommt.
