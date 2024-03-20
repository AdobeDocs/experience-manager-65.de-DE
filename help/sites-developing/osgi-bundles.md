---
title: OSGi-Bundles
description: Erfahren Sie mehr über die Verwaltung Ihrer OSGi-Bundles in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 30%

---

# OSGi-Bundles{#osgi-bundles}

## Verwenden der semantischen Versionierung {#use-semantic-versioning}

Die vereinbarten Best Practices für die semantische Versionsnummeriierung finden Sie unter [https://semver.org/](https://semver.org/).

## Betten Sie nicht mehr Klassen und JARs ein, als in OSGi-Bundles unbedingt erforderlich sind {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Gemeinsame Bibliotheken sollten in separate Bundles zusammengefasst werden. Dadurch können sie in allen Bundles wiederverwendet werden. Beim Umbrechen einer *JAR* in einem OSGi-Bundle überprüfen Sie die Online-Quellen, um festzustellen, ob dies bereits geschehen ist. Einige gängige Orte, an denen Sie vorhandene Bundle-Wrapper finden, sind: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes und das SpringSource Enterprise Bundle Repository.

## Abhängig von den am wenigsten benötigten Bundle-Versionen {#depend-on-the-lowest-needed-bundle-versions}

Bei Kompilierungszeitabhängigkeiten in POM-Dateien hängen Sie immer von der niedrigsten benötigten Version ab, die die benötigte API verfügbar macht. Dies ermöglicht eine höhere Abwärtskompatibilität und erleichtert die Rückportierung von Fehlerbehebungen in älteren Versionen.

## Exportieren der Mindestanzahl erforderlicher Pakete aus OSGi-Bundles {#export-a-minimal-set-of-packages-from-osgi-bundles}

Wenn ein Package exportiert wurde, wurde eine API erstellt, von der andere abhängig sind. Exportieren Sie so wenig wie möglich und stellen Sie sicher, dass Sie tatsächlich APIs exportieren. Es ist einfacher, eine private Methode oder Klasse öffentlich zu machen, als eine zuvor exportierte Komponente privat zu machen.

Implementierungen immer in einer separaten *impl* Paket. Standardmäßig wird die Variable *maven-bundle-plugin* exportiert alles im Projekt, das keine *impl* im Namen.

## Definieren Sie immer explizit eine semantische Version für jedes exportierte Paket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Dadurch können sich Verbraucher Ihrer API mit Ihnen entwickeln. Folgen Sie dabei immer den Best Practices für die semantische Versionierung. Dadurch können Verbraucher Ihrer API wissen, welche Arten von Änderungen in einer neuen Version zu erwarten sind.

## Angeben von angezeigten Metatyp-Informationen {#include-metatype-information-where-exposed}

Durch Angabe aussagekräftiger Metatypinformationen werden Ihre Dienste und Komponenten in der Felix-Konsole leichter zu verstehen sein. Eine Liste der SCR-Anmerkungen und Attribute finden Sie unter: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
