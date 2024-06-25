---
title: Einrichten einer Umgebung für die AEM Forms-App
description: Hardware, Software und Lizenzen zum Erstellen und Bereitstellen der AEM Forms-App.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 1d1f9db2-83cf-4612-ac8c-d2638c3bbaea
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '211'
ht-degree: 100%

---

# Einrichten einer Umgebung für die AEM Forms-App{#set-up-environment-for-aem-forms-app}

Sie benötigen die folgende Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und bereitzustellen:

## Für Windows-Geräte {#for-windows-devices}

* Microsoft® Windows 10
* Microsoft® Visual Studio 2015
* Microsoft® Visual Studio Tools für Apache Cordova

## Für iOS-Geräte {#for-ios-devices}

* Intel-basierter Apple Mac mit macOS X 10.9.5 oder höher
* iOS SDK 8.4 oder höher
* Xcode-Version: Xcode 6.4 für OS X oder höher
* Mitgliedschaft im iOS Developer Enterprise Program
* Enterprise-Zertifikat zum Verteilen interner iOS-Apps
* Apple iPad mit iOS 8.4 oder höher

## Für Android™-Geräte {#for-android-devices}

* Android™ Development Toolkit (ADT-Bundle), das unter [https://developer.android.com/studio](https://developer.android.com/studio) heruntergeladen werden kann
* Wenn diese Umgebung auf einem Mac-System eingerichtet wird, sollte die ADT im Applikationsordner installiert werden.
* Wenn die ADT an einem anderen Speicherort auf dem Mac installiert ist oder die Umgebung auf einem Windows-System eingerichtet ist, muss der ADT SDK-Pfad in der Datei `local.properties` aktualisiert werden. Diese Datei ist im Ordner `src\android` im extrahierten Quellarchiv `mobileworkspace-src.zip` verfügbar. Zeigen Sie in dieser Datei die Variable `sdk.dir` auf den ADT SDK-Speicherort auf Ihrem Desktop.

>[!NOTE]
>
>Die Datei „adobe-lc-mobileworkspace-src.zip“ enthält PhoneGap SDK 5.0. Vergewissern Sie sich, dass PhoneGap SDK nicht vorinstalliert ist.
