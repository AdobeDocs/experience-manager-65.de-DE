---
title: Namenskonventionen im Namen des Java-Pakets
description: Bindestriche in Java-Paketname
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
source-git-commit: a2fd3c0c1892ac648c87ca0dec440e22144c37a2
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Benennungskonventionen {#naming-conventions}

## Bindestriche in Java-Paketname {#hyphens-in-java-package-name}

Beachten Sie beim Erstellen eines Speicherorts für eine Java-Klasse, dass der Paketname mit dem Paketnamen des Repository-Ordnerspeicherorts übereinstimmen muss und alle Bindestriche im Pfad ordnungsgemäß maskiert sind.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei AEM Entwicklung, aber Bindestriche sind in Java-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss in der Lage sein, zwischen einem tatsächlichen Unterstrich zu unterscheiden `_ `und Bindestriche `-`. Daher muss der Bindestrich in JCR durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich maskiert werden `_`.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java**, sollte der Paketname `java package apps.my_002dexample.component.info;`

Beachten Sie, dass ein Unterstrich in ähnlicher Weise maskiert werden muss, sodass `_` wird `_005f`.
