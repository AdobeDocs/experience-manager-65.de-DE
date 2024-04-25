---
title: Abwärtskompatibilität in AEM 6.5
description: Erfahren Sie, wie Sie die Kompatibilität Ihrer Apps und Konfigurationen mit Adobe Experience Manager (AEM) 6.5 sicherstellen.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
exl-id: c432a014-2dab-4c49-a25b-e4f461d13f9b
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---

# Abwärtskompatibilität in AEM 6.5{#backward-compatibility-in-aem}

## Übersicht {#overview}

>[!NOTE]
>
>Eine Liste der Änderungen am Inhalt und an der Konfiguration, die das Kompatibilitätspaket nicht betreffen, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

In Adobe Experience Manager (AEM) 6.5 wurden alle Funktionen im Hinblick auf die Abwärtskompatibilität entwickelt.

In der Regel sollten Kundinnen und Kunden, die mit AEM 6.3 arbeiten, weder ihren Code noch ihre Anpassungen ändern müssen, wenn sie das entsprechende Upgrade durchführen. Für Kundinnen und Kunden mit AEM 6.1 und 6.2 gibt es nicht wesentlich mehr zusätzliche Änderungen, als dies bei einem Upgrade auf 6.3 erforderlich wäre.

In den Ausnahmefällen, in denen Funktionen nicht abwärtskompatibel realisiert werden konnten, können Abwärtskompatibilitätsprobleme bei Bundles und Inhalten reduziert werden. Installieren Sie dazu ein Kompatibilitätspaket für 6.4. (Weitere Informationen zum Herunterladen finden Sie nachstehend unter „Einrichtung“.) Dieses Kompatibilitätspaket wird normalerweise dazu beitragen, die Kompatibilität für Anwendungen, die mit AEM 6.4 kompatibel sind, wiederherzustellen.

Mit dem Kompatibilitätspaket können Sie AEM im Kompatibilitätsmodus ausführen und so die benutzerdefinierte Entwicklung für neue AEM-Funktionen zurückstellen:

>[!NOTE]
>
>Das Kompatibilitätspaket ist nur eine Zwischenlösung, um die für die Kompatibilität mit AEM 6.5 erforderliche Entwicklung aufzuschieben. Adobe empfiehlt dies nur als letzte Option, falls Sie Kompatibilitätsprobleme nicht direkt nach dem Upgrade durch Eigenentwicklungen beheben können. Adobe empfiehlt zudem, in den nativen Modus zu wechseln und das Kompatibilitätspaket zu deinstallieren, sobald Sie auf 6.5 basierende Eigenentwicklungen vornehmen, damit Sie den vollen Funktionsumfang von 6.5 nutzen können.

![sase](assets/sase.png)

Das Kompatibilitätspaket bietet zwei Modi: **Routing aktiviert** und **Routing deaktiviert**.

Damit kann AEM 6.5 in drei Modi ausgeführt werden:

**Nativer Modus:**

Der native Modus eignet sich für Kundinnen und Kunden, die alle neuen Funktionen von AEM 6.5 nutzen möchten und bereit sind, ihre Anpassungen durch Entwicklungsarbeiten an alle neuen Funktionen anzupassen.

Dies bedeutet, dass Sie Ihre Anwendung sofort nach dem Upgrade anpassen müssen.

**Kompatibilitätsmodus: Kompatibilitätspaket mit aktiviertem Routing installiert**

Der Kompatibilitätsmodus eignet sich für Kundinnen und Kunden mit Schnittstellenanpassungen, die nicht abwärtskompatibel sind. Damit kann AEM im Kompatibilitätsmodus ausgeführt und die für nicht mit Ihrem benutzerdefinierten Code kompatible neue AEM-Funktionen erforderliche Eigenentwicklung zurückgestellt werden.

**Legacy-Modus: Kompatibilitätspaket mit deaktiviertem Routing installiert**

Der Legacy-Modus eignet sich für Kundinnen und Kunden, die benutzerdefinierte Schnittstellen besitzen, die auf Legacy- oder veraltetem Code von AEM basieren, der in das Kompatibilitätspaket ausgelagert wurde.

![sapte](assets/sapte.png)

## Einrichtung {#how-to-set-up}

Das **AEM 6.4-Kompatibilitätspaket für 6.5** kann als Paket mit Package Manager installiert werden. Sie können das [AEM 6.4-Kompatibilitätspaket für 6.5 von der Software Distribution-Site](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=compat*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fcompatpack%2Faem-compat-cq65-to-cq64) herunterladen.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![Schalter für Kompatibilität](assets/compat-switches.png)

Nachdem das Kompatibilitätspaket installiert und konfiguriert wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
