---
title: Abwärtskompatibilität in AEM 6.5
seo-title: Backward Compatibility in AEM 6.5
description: Erfahren Sie, wie Sie Ihre Applikationen und Konfigurationen mit AEM 6.5 kompatibel machen.
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.5
uuid: 81dc2771-f59b-4b24-8932-9e938cba05e0
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: f3b4ec1d-9054-47d4-afcb-0a0121b94190
docset: aem65
feature: Upgrading
exl-id: c432a014-2dab-4c49-a25b-e4f461d13f9b
source-git-commit: 50a11e30ccd720065962e8dd03cbcc71ec9f715a
workflow-type: ht
source-wordcount: '500'
ht-degree: 100%

---

# Abwärtskompatibilität in AEM 6.5{#backward-compatibility-in-aem}

## Übersicht {#overview}

>[!NOTE]
>
>Eine Liste der Änderungen am Inhalt und an der Konfiguration, die das Kompatibilitätspaket nicht betreffen, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

In AEM 6.5 wurden alle Funktionen im Hinblick auf die Abwärtskompatibilität entwickelt.

In den meisten Fällen sollten Kunden, die mit AEM 6.3 arbeiten, weder ihren Code noch ihre Anpassungen ändern müssen, wenn sie die Aktualisierung durchführen. Kunden mit AEM 6.1 und 6.2 müssen nicht mehr zusätzliche Änderungen durchführen, als dies bei einem Upgrade auf 6.3 erforderlich ist.

Für die Ausnahmen, in denen Funktionen nicht abwärtskompatibel realisiert werden konnten, kann die Abwärtskompatibilität für Pakete und Inhalte erzielt werden, indem ein Kompatibilitätspaket für 6.4 installiert wird (im Folgenden finden Sie weitere Informationen und erfahren, wo Sie das Paket herunterladen können). Dieses Kompatibilitätspaket wird in den meisten Fällen dazu beitragen, die Kompatibilität für Programme, die mit AEM 6.4 kompatibel sind, wiederherzustellen.

Mit dem Kompatibilitätspaket können Sie AEM im Kompatibilitätsmodus ausführen und so die benutzerdefinierte Entwicklung für neue AEM-Funktionen zurückstellen:

>[!NOTE]
>
>Bitte beachten Sie, dass das Kompatibilitätspaket nur eine Zwischenlösung ist, um die für die Kompatibilität mit AEM 6.5 erforderliche Entwicklung aufzuschieben. Es wird nur als letzte Option empfohlen, falls Sie Kompatibilitätsprobleme nicht direkt nach der Aktualisierung durch Eigenentwicklungen beheben können. Es wird dringend empfohlen, in den nativen Modus zu wechseln und das Kompatibilitätspaket zu deinstallieren, sobald Sie auf 6.5 basierende Eigenentwicklungen vornehmen, damit Sie den vollen Funktionsumfang von 6.5 nutzen können.

![sase](assets/sase.png)

Das Kompatibilitätspaket bietet zwei Modi: **Routing aktiviert** und **Routing deaktiviert**.

Damit kann AEM 6.5 in drei Modi ausgeführt werden:

**Nativer Modus:**

Der native Modus eignet sich für Kunden, die alle neuen Funktionen von AEM 6.5 nutzen möchten und bereit sind, ihre Anpassungen durch Entwicklungsarbeiten an alle neuen Funktionen anzupassen.

Dies bedeutet, dass Sie die Korrekturen in Ihrer Anwendung sofort nach der Aktualisierung durchführen müssen.

**Kompatibilitätsmodus: Kompatibilitätspaket mit aktiviertem Routing installiert** 

Der Kompatibilitätsmodus eignet sich für Kunden, die Schnittstellen angepasst haben, die nicht abwärtskompatibel sind. Damit kann AEM im Kompatibilitätsmodus ausgeführt und die für nicht mit Ihrem benutzerdefinierten Code kompatible neue AEM-Funktionen erforderliche Eigenentwicklung zurückgestellt werden.

**Legacy-Modus: Kompatibilitätspaket mit deaktiviertem Routing installiert** 

Der Legacy-Modus eignet sich für Kunden, die benutzerdefinierte Schnittstellen besitzen, die auf Legacy- oder veraltetem Code von AEM basieren, der in das Kompatibilitätspaket ausgelagert wurde.

![sapte](assets/sapte.png)

## Einrichtung {#how-to-set-up}

Das **AEM 6.4-Kompatibilitätspaket für 6.5** kann als Paket mit Package Manager installiert werden. Sie können das [AEM 6.4-Kompatibilitätspaket für 6.5 von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=compat*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fcompatpack%2Faem-compat-cq65-to-cq64) herunterladen.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![Schalter für Kompatibilität](assets/compat-switches.png)

Sobald das Kompatibilitätspaket installiert und konfiguriert wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
