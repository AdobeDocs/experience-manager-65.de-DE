---
title: OSGi-Bundles
description: Hier finden Sie Tipps für die Verwaltung Ihrer OSGi-Bundles in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 100%

---

# OSGi-Bundles{#osgi-bundles}

## Verwenden der semantischen Versionierung {#use-semantic-versioning}

Die vereinbarten Best Practices für die semantische Versionsnummeriierung finden Sie unter [https://semver.org/](https://semver.org/).

## Bedarfsbeschränktes Einbetten von Klassen und JAR-Dateien in OSGi-Bundles {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Allgemeine Bibliotheken sollten in separate Bundles ausgelagert werden. So können Sie sie für alle Bundles wiederverwenden. Wenn Sie einen *JAR*-Wrapper für ein OSGi-Bundle erstellen möchten, überprüfen Sie zuerst online, ob dieser Vorgang bereits von jemand anderem vor Ihnen ausgeführt wurde. Bereits vorhandene Bundle-Wrapper finden Sie unter anderem in: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes und dem SpringSource Enterprise Bundle Repository.

## Verwenden Sie die niedrigsten erforderlichen Bundle-Versionen {#depend-on-the-lowest-needed-bundle-versions}

Verwenden Sie für Kompilierungszeit-Abhängigkeiten in POM-Dateien immer die niedrigste erforderliche Version, die die benötigte API verfügbar macht. Dies ermöglicht eine höhere Abwärtskompatibilität und erleichtert die Backport-Fehlerbehebung bei älteren Versionen.

## Exportieren der Mindestanzahl erforderlicher Pakete aus OSGi-Bundles {#export-a-minimal-set-of-packages-from-osgi-bundles}

Nach dem Exportieren eines Pakets wird eine API erstellt, von der andere Komponenten abhängen. Exportieren Sie so wenig wie möglich und stellen Sie sicher, dass Sie tatsächlich APIs exportieren. Es ist einfacher, eine private Methode oder Klasse öffentlich zu machen, als eine zuvor exportierte Komponente privat zu machen.

Platzieren Sie Implementierungen immer in einem separaten *impl*-Paket. Standardmäßig exportiert das *maven-bundle*-Plug-in alle Komponenten eines Projekts, die kein *impl* im Namen enthalten.

## Definieren Sie immer ausdrücklich eine semantische Version für jedes exportierte Paket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Dadurch können sich Nutzerinnen und Nutzer der API an Ihr Entwicklungstempo anpassen. Folgen Sie dabei immer den Best Practices für die semantische Versionierung. Nutzerinnen und Nutzer der API sind dann immer darüber informiert, mit welchen Änderungen in einer neuen Version zu rechnen ist.

## Geben Sie Metatyp-Informationen ein, wo sie benötigt werden {#include-metatype-information-where-exposed}

Durch Angabe aussagekräftiger Metatyp-Informationen sind Ihre Services und Komponenten in der Felix-Konsole leichter verständlich. Eine Liste der SCR-Anmerkungen und Attribute finden Sie unter [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
