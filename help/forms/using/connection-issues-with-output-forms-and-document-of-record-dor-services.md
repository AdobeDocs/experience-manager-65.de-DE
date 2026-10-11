---
title: Verbindungsprobleme mit Output-, Forms- und (Document of Record) DoR-Diensten
description: Beheben Sie AEM Forms-Verbindungsfehler nach SP19. Stoppen Sie die Instanz, installieren Sie Microsoft Visual C++ und starten Sie den Server für eine nahtlose Lösung neu. Fehlerbehebung für Output-, Forms- und DoR-Dienste.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
exl-id: bd58099c-08cd-4056-afb6-a5935454429a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
  - id: f19cff18-c8cc-4a4b-adad-85dd2fa3dbe2
    internal-label: Document Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 100%
---
# Ausgabe-Service, Forms-Service oder DoR-Service (Document of Record) kann nicht verwendet werden {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Problem

Nach der Installation von AEM Forms 6.5 Service Pack 19 kann der Versuch, den Output-Dienst, den Forms-Dienst oder den DoR-Dienst (Document of Record) zu verwenden, zu einem `Connection to failed service`-Fehler führen.

## Lösung

Das Problem beheben Sie wie folgt:

1. Stoppen Sie Ihre AEM 6.5 Forms-Instanz.
1. Laden Sie die [64-Bit-Version der Microsoft Visual C++ Redistributable Packages for Visual Studio 2015, 2017, 2019 und 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) auf den Computer herunter, auf dem AEM 6.5 Forms installiert ist, und installieren Sie sie.
1. Starten Sie den AEM Forms-Server neu.

   >[!NOTE]
   >
   > Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.


>[!NOTE]
>
>
> Stellen Sie sicher, dass Sie das Redistributable installieren, auch wenn eine frühere Version bereits installiert ist.
