---
title: Verbindungsprobleme mit Output-, Forms- und (Document of Record) DoR-Diensten
description: Beheben Sie AEM Forms-Verbindungsfehler nach SP19. Stoppen Sie die Instanz, installieren Sie Microsoft Visual C++ und starten Sie den Server für eine nahtlose Lösung neu. Fehlerbehebung für Output-, Forms- und DoR-Dienste.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
exl-id: bd58099c-08cd-4056-afb6-a5935454429a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '168'
ht-degree: 100%

---

# Ausgabe-Service, Forms-Service oder DoR-Service (Document of Record) kann nicht verwendet werden {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Problem

Nach der Installation von AEM Forms 6.5 Service Pack 19 kann der Versuch, den Output-Dienst, den Forms-Dienst oder den DoR-Dienst (Document of Record) zu verwenden, zu einem `Connection to failed service`-Fehler führen.

## Lösung

Das Problem beheben Sie wie folgt:

1. Beenden Sie Ihre AEM 6.5 Forms-Instanz.
1. Laden Sie die [64-Bit-Version der Microsoft Visual C++ Redistributable Packages for Visual Studio 2015, 2017, 2019 und 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) auf den Computer herunter, auf dem AEM 6.5 Forms installiert ist, und installieren Sie sie.
1. Starten Sie den AEM Forms-Server neu.

   >[!NOTE]
   >
   > Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.


>[!NOTE]
>
>
> Stellen Sie sicher, dass Sie das Redistributable installieren, auch wenn eine frühere Version bereits installiert ist.
