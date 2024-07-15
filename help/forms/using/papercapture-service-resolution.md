---
title: Fehlerbehebung Artikel zur Behebung des Problems, wenn der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) auf PDF nicht durchführen kann.
description: Erfahren Sie, wie Sie das Problem beheben, dass der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) auf PDF nicht durchführen kann.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 64e120ee-5f16-4cd3-9ae9-95b165169e47
source-git-commit: f9e98d7de24d516eab163d42f6c1c3155915856e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 36%

---


# Der PaperCature-Dienst kann OCR-Vorgänge auf PDF nicht durchführen

## Problem

Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 kann der `PaperCapture`-Dienst keine OCR-Vorgänge (Optical Character Recognition) für PDFs mehr durchführen. Der Dienst generiert keine Ausgabe in Form einer PDF oder einer Protokolldatei.

## Gilt für

Diese Lösung gilt für:
* AEM Forms auf allen JEE-Servern (JBoss, Weblogic, Websphere)
* AEM Forms auf OSGi-Servern

## Lösung

1. Laden Sie den [Hotfix](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0) über das Software-Verteilungsportal herunter.
1. Extrahieren und kopieren Sie den Inhalt des heruntergeladenen Ordners.
1. Navigieren Sie für die entsprechenden Anwendungsserver zu den unten stehenden Pfaden:
   * **jboss**:
     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **weblogic**:
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **websphere**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **OSGi setup**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. Beenden Sie den AEM-Anwendungsserver.
1. Ersetzen Sie den vorhandenen Inhalt des Ordners `PaperCaptureSvc` durch den kopierten Inhalt.
1. Starten Sie den AEM-Anwendungsserver neu.

   >[!NOTE]
   >
   > Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
