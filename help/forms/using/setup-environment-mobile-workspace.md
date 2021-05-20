---
title: Einrichten einer Umgebung für die AEM Forms-App
seo-title: Einrichten einer Umgebung für die AEM Forms-App
description: Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und zu bereitstellen.
seo-description: Hardware, Software und Lizenzen, um die AEM Forms-App zu erstellen und zu bereitstellen.
uuid: 4123a6b7-5766-476c-9afb-f57029b148ad
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e6b01ade-7ea3-42a7-872d-cc35a3d2782a
docset: aem65
exl-id: 1d1f9db2-83cf-4612-ac8c-d2638c3bbaea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 66%

---

# Einrichten einer Umgebung für die AEM Forms-App{#set-up-environment-for-aem-forms-app}

Sie benötigen folgende Hardware, Software und Lizenzen, um die AEM Forms-App erstellen und bereitstellen zu können:

## Für Windows-Geräte {#for-windows-devices}

* Microsoft Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio-Tools für Apache Cordova

## Für iOS-Geräte {#for-ios-devices}

* Intel-basierte Apple Mac, auf dem Mac OS X 10.9.5 oder höher ausgeführt wird
* iOS SDK 8.4 oder höher
* Xcode-Version: Xcode 6.4 für OS X oder höher
* Mitgliedschaft im iOS Developer Enterprise Program
* Enterprise-Zertifikat zum Verteilen interner iOS-Apps
* Apple iPad mit iOS 8.4 oder höher

## Für Android-Geräte  {#for-android-devices}

* Android Development Toolkit (ADT bundle), das heruntergeladen werden kann von [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Wenn diese Umgebung auf einem MAC-System eingerichtet wird, sollte die ADT im Anwendungsordner installiert werden.
* Wenn die ADT an einem anderen Speicherort auf dem MAC installiert ist oder die Umgebung auf einem Windows-System eingerichtet ist, muss der ADT SDK-Pfad in der Datei `local.properties` aktualisiert werden, die im Ordner `src\android` im extrahierten Quellarchiv `mobileworkspace-src.zip` verfügbar ist. Zeigen Sie in dieser Datei die Variable `sdk.dir` auf den ADT SDK-Speicherort auf Ihrem Desktop.

>[!NOTE]
>
>Die Datei adobe-lc-mobileworkspace-src.zip enthält PhoneGap SDK 5.0. Stellen Sie sicher, dass PhoneGap SDK nicht vorinstalliert ist.
