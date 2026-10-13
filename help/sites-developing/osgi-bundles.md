---
title: OSGi-Pakete
description: Hier finden Sie Tipps für die Verwaltung Ihrer OSGi-Pakete in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
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
source-wordcount: '359'
ht-degree: 100%
---
# OSGi-Pakete{#osgi-bundles}

## Verwenden der semantischen Versionierung {#use-semantic-versioning}

Die vereinbarten Best Practices für die semantische Versionsnummeriierung finden Sie unter [https://semver.org/](https://semver.org/).

## Bedarfsbeschränktes Einbetten von Klassen und JAR-Dateien in OSGi-Pakete {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Allgemeine Bibliotheken sollten in separate Pakete ausgelagert werden. So können Sie sie für alle Pakete wiederverwenden. Wenn Sie einen *JAR*-Wrapper für ein OSGi-Paket erstellen möchten, überprüfen Sie zuerst online, ob dieser Vorgang bereits von jemand anderem vor Ihnen ausgeführt wurde. Bereits vorhandene Paket-Wrapper finden Sie unter anderem in: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes und dem SpringSource Enterprise Bundle Repository.

## Verwenden Sie die niedrigsten erforderlichen Paketversionen {#depend-on-the-lowest-needed-bundle-versions}

Verwenden Sie für Kompilierungszeit-Abhängigkeiten in POM-Dateien immer die niedrigste erforderliche Version, die die benötigte API verfügbar macht. Dies ermöglicht eine höhere Abwärtskompatibilität und erleichtert die Backport-Fehlerbehebung bei älteren Versionen.

## Exportieren der Mindestanzahl erforderlicher Pakete aus OSGi-Bundles {#export-a-minimal-set-of-packages-from-osgi-bundles}

Nach dem Exportieren eines Pakets wird eine API erstellt, von der andere Komponenten abhängen. Exportieren Sie so wenig wie möglich und stellen Sie sicher, dass Sie tatsächlich APIs exportieren. Es ist einfacher, eine private Methode oder Klasse öffentlich zu machen, als eine zuvor exportierte Komponente privat zu machen.

Platzieren Sie Implementierungen immer in einem separaten *impl*-Paket. Standardmäßig exportiert das *maven-bundle*-Plug-in alle Komponenten eines Projekts, die kein *impl* im Namen enthalten.

## Definieren Sie immer ausdrücklich eine semantische Version für jedes exportierte Paket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Dadurch können sich Nutzerinnen und Nutzer der API an Ihr Entwicklungstempo anpassen. Folgen Sie dabei immer den Best Practices für die semantische Versionierung. Nutzerinnen und Nutzer der API sind dann immer darüber informiert, mit welchen Änderungen in einer neuen Version zu rechnen ist.

## Geben Sie Metatyp-Informationen ein, wo sie benötigt werden {#include-metatype-information-where-exposed}

Durch Angabe aussagekräftiger Metatyp-Informationen sind Ihre Services und Komponenten in der Felix-Konsole leichter verständlich. Eine Liste der SCR-Anmerkungen und Attribute finden Sie unter [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
