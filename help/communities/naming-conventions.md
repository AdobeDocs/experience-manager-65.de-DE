---
title: Benennungskonventionen im Java-&trade;-Paketnamen
description: Erfahren Sie mehr über Namenskonventionen und die Verwendung von Bindestrichen im Java-&trade;-Paketnamen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
solution: Experience Manager
feature: Communities
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%
---
# Benennungskonventionen {#naming-conventions}

## Bindestriche im Java™-Paketnamen {#hyphens-in-java-package-name}

Beim Erstellen eines Speicherorts für eine Java™-Klasse muss der Paketname mit dem des Speicherorts des Repository-Ordners mit allen Bindestrichen im Pfad übereinstimmen, die ordnungsgemäß maskiert sind.

Obwohl die Verwendung von Bindestrichen in den Namen von Repository-Elementen eine empfohlene Praxis in der AEM-Entwicklung ist, sind Bindestriche in Java™-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss zwischen einem tatsächlichen Unterstrich `_ ` einem Bindestrich `-`. Daher muss in JCR der Bindestrich durch seinen Unicode-Wert (u002d) ersetzt und mit einem Unterstrich `_`.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java** lautet, sollte der Paketname `java package apps.my_002dexample.component.info;` sein

Beachten Sie, dass ein Unterstrich in ähnlicher Weise maskiert werden muss, sodass `_` `_005f` wird.
