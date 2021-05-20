---
title: Benennungskonventionen
seo-title: Benennungskonventionen
description: Bindestriche in Java-Paketname
seo-description: Bindestriche in Java-Paketname
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 4%

---

# Benennungskonventionen {#naming-conventions}

## Bindestriche im Java-Paketnamen {#hyphens-in-java-package-name}

Beachten Sie beim Erstellen eines Speicherorts für eine Java-Klasse, dass der Paketname mit dem Paketnamen des Repository-Ordnerspeicherorts übereinstimmen muss und alle Bindestriche im Pfad ordnungsgemäß maskiert sind.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei AEM Entwicklung, aber Bindestriche sind in Java-Paketnamen unzulässig.

Die zugrunde liegende CRX-Plattform muss zwischen einem tatsächlichen Unterstrich `_ `und einem Bindestrich `-` unterscheiden können. Daher muss der Bindestrich in JCR durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich (`_`) maskiert werden.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java** lautet, sollte der Paketname `java package apps.my_002dexample.component.info;` lauten.

Beachten Sie, dass ein Unterstrich auf ähnliche Weise maskiert werden muss, sodass `_` `_005f` wird.
