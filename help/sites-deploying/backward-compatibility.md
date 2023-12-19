---
title: Abwärtskompatibilität in AEM 6.5
description: Erfahren Sie, wie Sie Ihre Apps und Konfigurationen mit Adobe Experience Manager (AEM) 6.5 kompatibel halten.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
exl-id: c432a014-2dab-4c49-a25b-e4f461d13f9b
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 38%

---

# Abwärtskompatibilität in AEM 6.5{#backward-compatibility-in-aem}

## Übersicht {#overview}

>[!NOTE]
>
>Eine Liste der Inhalts- und Konfigurationsänderungen, die nicht unter das Kompatibilitätspaket fallen, finden Sie unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).

In Adobe Experience Manager (AEM) 6.5 wurden alle Funktionen mit Rückwärtskompatibilität entwickelt.

Normalerweise sollten Kunden, die AEM 6.3 ausführen, den Code oder die Anpassungen bei der Aktualisierung nicht ändern müssen. Für Kunden von AEM 6.1 und 6.2 gibt es keine zusätzlichen Änderungen, die grundlegend sind, als dies bei einem Upgrade auf 6.3 der Fall wäre.

Für Ausnahmen, in denen Funktionen nicht abwärtskompatibel gehalten werden konnten, können Abwärtskompatibilitätsprobleme bei Paketen und Inhalten reduziert werden. Installieren Sie dazu ein Kompatibilitätspaket für 6.4 (weitere Informationen zum Herunterladen finden Sie unten unter Einrichten ). Dieses Kompatibilitätspaket hilft bei der Wiederherstellung der Kompatibilität, die normalerweise für Anwendungen gilt, die AEM 6.4 erfüllen.

Mit dem Kompatibilitätspaket können Sie AEM im Kompatibilitätsmodus ausführen und so die benutzerdefinierte Entwicklung für neue AEM-Funktionen zurückstellen:

>[!NOTE]
>
>Das Kompatibilitätspaket ist nur eine temporäre Lösung, um die Entwicklung zu verschieben, die für die Kompatibilität mit AEM 6.5 erforderlich ist. Adobe empfiehlt dies nur als letzte Option, wenn Sie Kompatibilitätsprobleme nicht unmittelbar nach der Aktualisierung durch die Entwicklung beheben können. Darüber hinaus empfiehlt Adobe, in den nativen Modus zu wechseln und das Kompatibilitätspaket zu deinstallieren, sobald Sie sich für eine 6.5-basierte benutzerdefinierte Entwicklung entscheiden und die vollständige 6.5-Funktionalität nutzen.

![sase](assets/sase.png)

Das Kompatibilitätspaket bietet zwei Modi: **Routing aktiviert** und **Routing deaktiviert**.

Dadurch kann AEM 6.5 in drei Modi ausgeführt werden:

**Nativer Modus:**

Der native Modus eignet sich für Kundinnen und Kunden, die alle neuen Funktionen von AEM 6.5 nutzen möchten und bereit sind, ihre Anpassungen durch Entwicklungsarbeiten an alle neuen Funktionen anzupassen.

Dies bedeutet, dass Sie Ihre Anwendung sofort nach dem Upgrade anpassen müssen.

**Kompatibilitätsmodus: Kompatibilitätspaket mit aktiviertem Routing installiert**

Der Kompatibilitätsmodus eignet sich für Kundinnen und Kunden mit Schnittstellenanpassungen, die nicht abwärtskompatibel sind. Damit kann AEM im Kompatibilitätsmodus ausgeführt und die für nicht mit Ihrem benutzerdefinierten Code kompatible neue AEM-Funktionen erforderliche Eigenentwicklung zurückgestellt werden.

**Legacy-Modus: Kompatibilitätspaket mit deaktiviertem Routing installiert**

Der Legacy-Modus eignet sich für Kundinnen und Kunden, die benutzerdefinierte Schnittstellen besitzen, die auf Legacy- oder veraltetem Code von AEM basieren, der in das Kompatibilitätspaket ausgelagert wurde.

![sapte](assets/sapte.png)

## Einrichtung {#how-to-set-up}

Die **AEM 6.4 Compatibility Pack für 6.5** kann als Paket mit Package Manager installiert werden. Sie können die [AEM 6.4-Kompatibilitätspaket für 6.5 von der Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=compat*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fcompatpack%2Faem-compat-cq65-to-cq64) Site.

Sobald das Kompatibilitätspaket installiert wurde, können Sie das Routing über einen Schalter in der OSGi-Konfiguration aktivieren oder deaktivieren:

![Schalter für Kompatibilität](assets/compat-switches.png)

Nachdem das Kompatibilitätspaket installiert und eingerichtet wurde, werden die Funktionen basierend auf dem ausgewählten Kompatibilitätsmodus verwendet.
