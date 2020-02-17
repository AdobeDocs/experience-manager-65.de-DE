---
title: Verwenden von Maven für Communities
seo-title: Verwenden von Maven für Communities
description: AEM Communities API JAR und AEM Uber API JAR
seo-description: AEM Communities API JAR und AEM Uber API JAR
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Verwenden von Maven für Communities {#using-maven-for-communities}

## Überblick {#overview}

Dieser Abschnitt der Dokumentation zu AEM Communities ergänzt:

* [So erstellen Sie AEM-Projekte mit Apache Maven](../../help/sites-developing/ht-projects-maven.md)

Es gibt jetzt zwei &quot;Uber&quot;-Artefakte, die einzelne Artefakte ersetzen:

* AEM [Communities API-JAR](#communities-api-jar-artifact)
* AEM [Uber API-JAR](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API JAR Artefakt {#communities-api-jar-artifact}

Im Folgenden finden Sie ein Beispiel für eine GAV für die AEM Communities API-JAR:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
```

Stellen Sie sicher, dass die angegebene Version der Communities-Paketversion entspricht, die für AEM Communities installiert wurde. So überprüfen Sie die installierte Versionsnummer:

1. Melden Sie sich mit Administratorrechten an.
2. Navigieren Sie zu [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. Suchen Sie das Paket *cq-socialgroups-pkg-1.x.xxx.*
4. Version aus dem Paketnamen extrahieren
   * Die erste Version für AEM 6.3 ist Version 1.11.170
   * Feature Packs sind die Versionen 1.12.xxx

>[!NOTE]
>
>Es wird empfohlen, mit der neuesten Version von Communities auf dem Laufenden zu bleiben.
>
>Im Abschnitt [Neueste Versionen](deploy-communities.md#latest-releases) finden Sie die neueste Version.

## Beispiel für eine Maven-Abhängigkeit {#maven-dependency-example}

Die Communities API-JAR-Datei muss vor der Uber API-JAR-Datei angegeben werden.

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
