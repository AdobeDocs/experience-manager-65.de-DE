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
translation-type: tm+mt
source-git-commit: 22e853ecaf2696c7329a81bb9d375b1dbc74452c

---


# Benennungskonventionen {#naming-conventions}

## Bindestriche in Java-Paketname {#hyphens-in-java-package-name}

Beachten Sie beim Erstellen eines Speicherorts für eine Java-Klasse, dass der Paketname dem Speicherort des Repository-Ordners mit den ordnungsgemäß Escape-Zeichen im Pfad entsprechen muss.

Die Verwendung von Bindestrichen in den Namen von Repository-Elementen ist eine empfohlene Vorgehensweise bei der AEM-Entwicklung. Bindestriche sind innerhalb von Java-Paketnamen nicht zulässig.

Die zugrunde liegende CRX-Plattform muss zwischen einem tatsächlichen Unterstrich `_ `und einem Bindestrich unterscheiden können `-`. In JCR muss der Bindestrich daher durch den Unicode-Wert (u002d) ersetzt und mit einem Unterstrich versehen werden `_`.

Wenn der Repository-Pfad beispielsweise **/apps/my-example/component/info/Info.java** lautet, sollte der Paketname `java package apps.my_002dexample.component.info;`

Beachten Sie, dass ein Unterstrich auf ähnliche Weise mit einem Escape-Zeichen versehen werden muss, sodass `_` es `_005f`wird.
