---
title: Experience Manager Forms kann nicht mit bestimmten Versionen von Oracle JDK verwendet werden
seo-title: Unable to use Experience Manager Forms with certain versions of Oracle JDK
description: Experience Manager Forms kann nicht mit bestimmten Versionen von Oracle JDK verwendet werden
seo-description: Unable to use Experience Manager Forms with certain versions of Oracle JDK
source-git-commit: 91b012f8024350effc19613bcecfc42dee4130d9
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 5%

---

# Experience Manager Forms kann nicht mit bestimmten Versionen von Oracle JDK verwendet werden {#unable-to-use-forms-with-certain-versions-of-oracle-jdk}

Das Problem tritt bei den folgenden Versionen auf:

* Experience Manager 6.3 Forms
* Experience Manager 6.4 Forms
* Experience Manager 6.5 Forms

## Problem {#issue}

Der Benutzer trifft auf die folgende Ausnahme zu:
`Caused by: javax.xml.xpath.XPathExpressionException: javax.xml.transform.TransformerException: JAXP0801002: the compiler encountered an XPath expression containing '101' operators that exceeds the '100' limit set by 'FEATURE_SECURE_PROCESSING'.`

## Grund {#reason}

Die Ausnahme tritt auf, wenn Sie Experience Manager Forms mit Oracle JDK (Java Development Kit)-Version ausführen, die größer oder gleich den folgenden Versionen ist:

* [JDK7u341](https://www.oracle.com/java/technologies/javase/7u341-relnotes.html)
* [JDK8u331](https://www.oracle.com/java/technologies/javase/8u331-relnotes.html)
* [JDK11u15](https://www.oracle.com/java/technologies/javase/11-0-15-relnotes.html)

Die oben genannten und späteren Versionen von Java enthalten neue XML-Verarbeitungsbeschränkungen in der JVM (Java Virtual Machine), die dazu führen, dass bestimmte Forms-spezifische Vorgänge fehlschlagen.

## Problemumgehung {#workaround}

1. Beenden Sie Ihren Experience Manager Forms-Server.
1. Konfigurieren Sie das folgende JVM-Argument für Ihren Anwendungsserver:

   `-Djdk.xml.xpathExprOpLimit=2000`

   Sie setzt die Systemeigenschaft in JVM auf einen relativ hohen Wert, sodass die Standardgrenze nicht erreicht wird.

1. Starten Sie Ihren Experience Manager Forms-Server.
