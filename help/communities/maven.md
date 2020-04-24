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
source-git-commit: f7e5afe46100db7837647ac89aaf58cf101143b0

---


# Verwenden von Maven für Communities {#using-maven-for-communities}

## Übersicht {#overview}

Dieser Abschnitt der Dokumentation zu AEM Communities ergänzt:

* [Erstellen von AEM-Projekten mit Apache Maven](../../help/sites-developing/ht-projects-maven.md).

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
1. Navigieren Sie zu [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

1. Suchen Sie das Paket *cq-socialgroups-pkg-1.x.xxx*
1. Extrahieren Sie die Version aus dem Paketnamen:
   * Die erste Version von AEM 6.3 ist Version 1.11.170.
   * Feature Packs sind die Versionen 1.12.xxx.

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
