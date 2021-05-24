---
title: OSGi-Bundles
seo-title: OSGi-Bundles
description: Tipps für die Verwaltung von OSGi-Bundles
seo-description: Tipps für die Verwaltung von OSGi-Bundles
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 89%

---

# OSGi-Bundles{#osgi-bundles}

## Verwenden von semantischer Versionierung {#use-semantic-versioning}

Die vereinbarten Best Practices für die semantische Versionsnummerierung finden Sie unter [https://semver.org/](https://semver.org/).

## Bedarfsbeschränktes Einbetten von Klassen und JAR-Dateien in OSGi-Bundles {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Allgemeine Bibliotheken sollten in separate Bundles ausgelagert werden. So können Sie sie für alle Bundles wiederverwenden. Wenn Sie einen *JAR*-Wrapper für ein OSGi-Bundle erstellen möchten, überprüfen Sie zuerst online, ob dieser Vorgang bereits von jemand anderem ausgeführt wurde. Bereits vorhandene Bundle-Wrapper finden Sie unter anderem in: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes und dem SpringSource Enterprise Bundle Repository.

## Verwenden der niedrigsten erforderlichen Bundle-Versionen  {#depend-on-the-lowest-needed-bundle-versions}

Verwenden Sie für Kompilierungszeit-Abhängigkeiten in POM-Dateien immer die niedrigste erforderliche Version, die die API verfügbar macht. Dies ermöglicht eine höhere Abwärtskompatibilität und erleichtert die Backport-Fehlerbehebung bei älteren Versionen.

## Exportieren der Mindestanzahl erforderlicher Pakete aus OSGi-Bundles {#export-a-minimal-set-of-packages-from-osgi-bundles}

Unmittelbar nach dem Exportieren eines Pakets wird eine API erstellt, von der andere Komponenten abhängen. Exportieren Sie so wenig wie möglich und stellen Sie sicher, dass Sie tatsächlich APIs exportieren. Es ist einfacher, eine private Methode oder Klasse öffentlich zu machen, als eine zuvor exportierte Komponente privat zu machen.

Implementierungen müssen immer in einem separaten *impl*-Paket erfolgen. Standardmäßig exportiert das *maven-bundle*-Plug-in alle Komponenten eines Projekts, die kein *impl* im Namen enthalten.

## Ausdrückliches Definieren einer semantischen Version für jedes exportierte Paket  {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Dadurch können sich Nutzer der API an Ihr Entwicklungstempo anpassen. Folgen Sie dabei immer den Best Practices für die semantische Versionierung. Verbraucher der API sind dann immer darüber informiert, mit welchen Änderungen in einer neuen Version zu rechnen ist.

## Angeben von angezeigten Metatyp-Informationen {#include-metatype-information-where-exposed}

Durch Angabe aussagekräftiger Metatyp-Informationen sind Ihre Services und Komponenten in der Felix-Konsole verständlicher. Eine Liste der SCR-Anmerkungen und -Attribute finden Sie unter: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
