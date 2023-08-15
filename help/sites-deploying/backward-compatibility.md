---
title: Abwärtskompatibilität in AEM 6.5
seo-title: Backward Compatibility in AEM 6.5
description: Erfahren Sie, wie Sie Ihre Apps und Konfigurationen mit AEM 6.5 kompatibel halten.
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
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 53%

---

# Abwärtskompatibilität in AEM 6.5{#backward-compatibility-in-aem}

## Übersicht {#overview}

>[!NOTE]
>
>Eine Liste der Inhalts- und Konfigurationsänderungen, die nicht unter das Kompatibilitätspaket fallen, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

In AEM 6.5 wurden alle Funktionen im Hinblick auf die Abwärtskompatibilität entwickelt.

In den meisten Fällen sollten Kunden, die mit AEM 6.3 arbeiten, weder ihren Code noch ihre Anpassungen ändern müssen, wenn sie die Aktualisierung durchführen. Kunden mit AEM 6.1 und 6.2 müssen nicht mehr zusätzliche Änderungen durchführen, als dies bei einem Upgrade auf 6.3 erforderlich ist.

Für die Ausnahmen, in denen Funktionen nicht abwärtskompatibel realisiert werden konnten, kann die Abwärtskompatibilität für Pakete und Inhalte erzielt werden, indem ein Kompatibilitätspaket für 6.4 installiert wird (im Folgenden finden Sie weitere Informationen und erfahren, wo Sie das Paket herunterladen können). Dieses Kompatibilitätspaket wird in den meisten Fällen dazu beitragen, die Kompatibilität für Programme, die mit AEM 6.4 kompatibel sind, wiederherzustellen.

Mit dem Kompatibilitätspaket können Sie AEM im Kompatibilitätsmodus ausführen und die benutzerdefinierte Entwicklung für neue AEM Funktionen verschieben:

>[!NOTE]
>
>Bitte beachten Sie, dass das Kompatibilitätspaket nur eine Zwischenlösung ist, um die für die Kompatibilität mit AEM 6.5 erforderliche Entwicklung aufzuschieben. Es wird nur als letzte Option empfohlen, falls Sie Kompatibilitätsprobleme nicht direkt nach der Aktualisierung durch Eigenentwicklungen beheben können. Es wird dringend empfohlen, in den nativen Modus zu wechseln und das Kompatibilitätspaket zu deinstallieren, sobald Sie sich für eine 6.5-basierte benutzerdefinierte Entwicklung entscheiden und die vollständige 6.5-Funktionalität nutzen.

![sase](assets/sase.png)

Das Kompatibilitätspaket umfasst zwei Modi: **Routing aktiviert** und **Routing deaktiviert**.

Dadurch kann AEM 6.5 in drei Modi ausgeführt werden:

**Nativer Modus:**

Der native Modus richtet sich an Kunden, die alle neuen Funktionen von AEM 6.5 nutzen möchten und bereit sind, einige Entwicklungsschritte vorzunehmen, damit ihre Anpassungen mit allen neuen Funktionen funktionieren.

Dies bedeutet, dass Sie möglicherweise sofort nach der Aktualisierung Anpassungen in Ihrer Anwendung vornehmen müssen.

**Kompatibilitätsmodus: Kompatibilitätspaket mit aktiviertem Routing installiert**

Der Kompatibilitätsmodus eignet sich für Kunden, die Benutzeroberflächen anpassen, die nicht abwärtskompatibel sind. Dies ermöglicht AEM Ausführung im Kompatibilitätsmodus und verzögert die benutzerdefinierte Entwicklung, die für neue AEM Funktionen erforderlich ist, die nicht mit einigen Ihrem benutzerdefinierten Code kompatibel sind.

**Legacy-Modus: Kompatibilitätspaket mit deaktiviertem Routing installiert**

Der alte Modus richtet sich an Kunden mit benutzerdefinierten Schnittstellen, die auf veraltetem oder veraltetem Code aus AEM basieren, der im Kompatibilitätspaket entfernt wurde.

![sapte](assets/sapte.png)

## Einrichtung {#how-to-set-up}

Das **AEM 6.4-Kompatibilitätspaket für 6.5** kann als Paket mit Package Manager installiert werden. Sie können das [AEM 6.4-Kompatibilitätspaket für 6.5 von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=compat*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fcompatpack%2Faem-compat-cq65-to-cq64) herunterladen.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![Schalter für Kompatibilität](assets/compat-switches.png)

Sobald das Kompatibilitätspaket installiert und konfiguriert wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
