---
title: Fehlerbehebung Artikel zur Behebung des Problems, wenn der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) auf PDF nicht durchführen kann.
description: Erfahren Sie, wie Sie das Problem beheben, dass der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) auf PDF nicht durchführen kann.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 18005ba060954151df126789496c81f7238e32f6
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---


# PaperCature-Dienst führt OCR auf PDF nicht aus

## Problem

Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 wird die `PaperCapture` -Dienst führt keine OCR-Vorgänge (Optical Character Recognition) auf PDF durch. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei.

## Lösung

1. Laden Sie die [Hotfix](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Ca285aedf27094c9e8d9b08dc91e26aa7%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545648843177070%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=uWk0PsSSDjLRxqEMGMW%2BbD%2Fv4egR4vWL%2B0mfKpXdrKQ%3D&amp;reserved=0) über das Software Distribution-Portal.
1. Extrahieren und kopieren Sie den Inhalt des heruntergeladenen Ordners.
1. Navigieren Sie für die entsprechenden Anwendungsserver zu den unten stehenden Pfaden:
   * **jboss**:
     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **weblogic**:
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **websphere**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **OSGi-Einrichtung**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. Vorhandenen Inhalt der `PaperCaptureSvc` Ordner mit dem kopierten Inhalt.
1. [Starten Sie die AEM-Instanz neu](/help/forms/using/restart-aem-sdk.md).


