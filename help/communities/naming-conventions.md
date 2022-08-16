---
title: Benennungskonventionen
seo-title: Naming Conventions
description: Bindestriche in Java-Paketname
seo-description: Hyphens in Java Package Name
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# Benennungskonventionen {#naming-conventions}

## Bindestriche in Java-Paketname {#hyphens-in-java-package-name}

Beachten Sie beim Erstellen eines Speicherorts für eine Java-Klasse, dass der Paketname mit dem Paketnamen des Repository-Ordnerspeicherorts übereinstimmen muss und alle Bindestriche im Pfad ordnungsgemäß maskiert sind.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei AEM Entwicklung, aber Bindestriche sind in Java-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss in der Lage sein, zwischen einem tatsächlichen Unterstrich zu unterscheiden `_ `und Bindestriche `-`. Daher muss der Bindestrich in JCR durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich maskiert werden `_`.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java**, sollte der Paketname `java package apps.my_002dexample.component.info;`

Beachten Sie, dass ein Unterstrich in ähnlicher Weise maskiert werden muss, sodass `_` wird `_005f`.
