---
title: Einrichten einer Umgebung für die AEM Forms-App
description: Hardware, Software und Lizenzen zum Erstellen und Bereitstellen der AEM Forms-App.
uuid: 4123a6b7-5766-476c-9afb-f57029b148ad
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e6b01ade-7ea3-42a7-872d-cc35a3d2782a
docset: aem65
exl-id: 1d1f9db2-83cf-4612-ac8c-d2638c3bbaea
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 22%

---

# Einrichten einer Umgebung für die AEM Forms-App{#set-up-environment-for-aem-forms-app}

Sie benötigen die folgende Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und bereitzustellen:

## Für Windows-Geräte {#for-windows-devices}

* Microsoft® Windows 10
* Microsoft® Visual Studio 2015
* Microsoft® Visual Studio Tools for Apache Cordova

## Für iOS-Geräte {#for-ios-devices}

* Intel-basierte Apple Mac mit macOS X 10.9.5 oder höher
* iOS SDK 8.4 oder höher
* Xcode-Version: Xcode 6.4 für OS X oder höher
* Mitgliedschaft im iOS Developer Enterprise Program
* Enterprise-Zertifikat zum Verteilen interner iOS-Apps
* Apple iPad mit iOS 8.4 oder höher

## Für Android™-Geräte {#for-android-devices}

* Android™ Development Toolkit (ADT bundle), das heruntergeladen werden kann von [https://developer.android.com/studio](https://developer.android.com/studio)
* Wenn die Umgebung auf einem Mac-System eingerichtet ist, sollte ADT im Ordner &quot;Applications&quot;installiert werden.
* Wenn die ADT an einem anderen Speicherort auf Mac installiert ist oder die Umgebung auf einem Windows-System eingerichtet ist, muss der ADT SDK-Pfad in `local.properties` -Datei. Diese Datei ist im `src\android` Ordner im extrahierten Quellarchiv `mobileworkspace-src.zip`. Zeigen Sie in dieser Datei die Variable `sdk.dir` auf den ADT SDK-Speicherort auf Ihrem Desktop.

>[!NOTE]
>
>Die Datei „adobe-lc-mobileworkspace-src.zip“ enthält PhoneGap SDK 5.0. Vergewissern Sie sich, dass PhoneGap SDK nicht vorinstalliert ist.
