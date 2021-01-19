---
title: Verwenden von Maven für Communities
seo-title: Verwenden von Maven für Communities
description: AEM Uber API jar
seo-description: AEM Uber API jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: 5e7cc6ab82ba450b9be7c97266ec4c81b18fe3d2
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# Verwenden von Maven for Communities {#using-maven-for-communities}

## Überblick {#overview}

Dieser Abschnitt der AEM Communities-Dokumentation ergänzt:

* [Erstellen AEM Projekte mit Apache Maven](../../help/sites-developing/ht-projects-maven.md).

Es gibt nur ein &quot;Uber&quot;-Artefakt, das einzelne Artefakte ersetzt:

* AEM [Uber-API-JAR](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>Ab AEM 6.4 werden die Communities APIs nicht explizit veröffentlicht. Alle Communities APIs sind jetzt in der Uber-JAR selbst enthalten.
>
>Es wird empfohlen, mit der neuesten Version von Communities auf dem Laufenden zu bleiben.
>
>Die neueste Version finden Sie im Abschnitt [Neueste Versionen](deploy-communities.md#latest-releases).

## Beispiel für eine bestimmte Abhängigkeit {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.7</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Siehe [AEM Uber-JAR-Repository](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar), um das neueste Uber-JAR-Artefakt zu identifizieren.

<!--
There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Log in with adminstrative privileges.
1. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

1. Locate the package: `cq-socialcommunities-pkg-1.x.xxx`
1. Extract the version from the package name:
   * First version for AEM 6.3 is version 1.11.170.
   * Feature packs will be versions 1.12.xxx.

>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
-->