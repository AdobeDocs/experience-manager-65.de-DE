---
title: Benennungskonventionen im Java&trade;-Paketnamen
description: Erfahren Sie mehr über Benennungskonventionen und die Verwendung von Bindestrichen im Java-&trade;-Paketnamen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 1%

---

# Benennungskonventionen {#naming-conventions}

## Bindestriche im Java™-Paketnamen {#hyphens-in-java-package-name}

Beim Erstellen eines Speicherorts für eine Java™-Klasse muss der Paketname mit dem des Speicherorts des Repository-Ordners mit allen Bindestrichen im Pfad übereinstimmen, die ordnungsgemäß maskiert sind.

Obwohl die Verwendung von Bindestrichen in den Namen von Repository-Elementen eine empfohlene Praxis in der AEM-Entwicklung ist, sind Bindestriche in Java™-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss zwischen einem tatsächlichen Unterstrich `_ ` einem Bindestrich `-`. Daher muss in JCR der Bindestrich durch seinen Unicode-Wert (u002d) ersetzt und mit einem Unterstrich `_`.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java** lautet, sollte der Paketname `java package apps.my_002dexample.component.info;` sein

Beachten Sie, dass ein Unterstrich in ähnlicher Weise maskiert werden muss, sodass `_` `_005f` wird.
