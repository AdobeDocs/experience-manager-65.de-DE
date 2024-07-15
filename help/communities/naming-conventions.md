---
title: Namenskonventionen in Java& Handel; Paketname
description: Erfahren Sie mehr über Benennungskonventionen und die Verwendung von Bindestrichen in Java&trade;package name.
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

## Bindestriche in Java™-Paketname {#hyphens-in-java-package-name}

Beim Erstellen eines Speicherorts für eine Java™-Klasse muss der Paketname mit dem des Repository-Ordnerspeicherorts übereinstimmen und alle Bindestriche im Pfad müssen ordnungsgemäß maskiert sein.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei AEM Entwicklung, aber Bindestriche sind in Java™-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss zwischen einem tatsächlichen Unterstrich `_ ` und einem Bindestrich `-` unterscheiden können. Daher muss der Bindestrich in JCR durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich (`_`) maskiert werden.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java** lautet, sollte der Paketname `java package apps.my_002dexample.component.info;` lauten.

Beachten Sie, dass ein Unterstrich auf ähnliche Weise maskiert werden muss, sodass `_` zu `_005f` wird.
