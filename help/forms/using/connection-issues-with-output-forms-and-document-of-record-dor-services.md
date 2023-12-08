---
title: Verbindungsprobleme mit Output-, Forms- und (Datensatzdokument-)DoR-Diensten
description: Beheben Sie AEM Forms-Verbindungsfehler nach SP19. Beenden, installieren Sie Microsoft Visual C++, starten Sie den Server für eine nahtlose Lösung neu. Fehlerbehebung bei Output, Forms, DoR-Diensten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
source-git-commit: cf5da092fabbc7834108dc54d65eb97e160984ce
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 1%

---


# Output-Dienst, Forms-Dienst oder DoR-Dienst (Document of Record) können nicht verwendet werden {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Problem

Nach der Installation von AEM Forms 6.5 Service Pack 19 kann der Versuch, den Output-Dienst, den Forms-Dienst oder den DoR-Dienst (Document of Record) zu verwenden, zu einem `Connection to failed service` Fehler.

## Lösung

So lösen Sie das Problem:

1. Beenden Sie Ihre AEM 6.5 Forms-Instanz.
1. Laden Sie die [64-Bit-Version von Microsoft Visual C++ Redistributable Packages for Visual Studio 2015, 2017, 2019 und 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) auf dem Computer, auf dem AEM 6.5 Forms installiert ist.
1. Starten Sie den AEM Forms-Server neu.


>[!NOTE]
>
>
> Stellen Sie sicher, dass Sie das Redistributable installieren, auch wenn eine frühere Version installiert ist.
