---
title: Fehler bei CRX/Bundle und Startseitendienst nicht verfügbar, sobald das neueste 6.5.15.0 Service Pack installiert ist
description: Fehler bei CRX/Bundle und Startseitendienst nicht verfügbar, sobald das neueste 6.5.15.0 Service Pack installiert ist
SEO Description: Trouble shooting steps to resolve the errors after installing latest 6.5.15.0 service pack
exl-id: dfe015a3-3a24-41c5-aede-8e086851d62b
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 94663796-0ee7-58b9-84f4-b425ebb69e83
    internal-label: AEM Forms on JEE
  - id: 8c4fb903-572c-5473-ad45-8ebb0d5d8134
    internal-label: AEM Forms on OSGi
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 76%
---
# Fehler „Dienst nicht verfügbar“ nach der Installation von AEM (6.5.15.0) Service Pack {#steps-to-resolve-error-after-installing-service-pack}

## Problem {#issue}

Nach der Installation des [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) tritt der Fehler wie folgt auf:
* FEHLER [FelixDispatchQueue] org.apache.sling.scripting.console FrameworkEvent FEHLER (org.osgi.framework.BundleException: org.apache.sling.scripting.console kann nicht aufgelöst werden

Nach der Installation von AEM 6.5.15.0 Service Pack zeigen das CRX/Bundle und die Startseite Fehler bezüglich der Nichtverfügbarkeit von Diensten an.

## Gilt für {#applies-to}

Diese Lösung gilt für:
* AEM Forms auf allen JEE-Servern außer denen, die unter JBoss EAP 7.4.0 laufen

## Lösung {#solution}

>[!NOTE]
>
>Die Schritte zur Fehlerbehebung gelten für alle Anwendungs-Server außer JBoss EAP 7.4.

Wenn nach der Installation von [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) das CRX/Bundle und die Startseite Fehler bezüglich der Nichtverfügbarkeit von Diensten anzeigen, führen Sie die folgenden Schritte aus:

1. Stoppen Sie den Anwendungs-Server.
1. Navigieren Sie zu `[aem-forms root]\crx-repository\launchpad\felix\bundle52`.
1. Suchen Sie die Datei `bundle.info`.
1. Öffnen Sie die Datei `bundle.info` in einem Texteditor und suchen Sie nach dem Paketnamen als `org.apache.felix.http.bridge`.

   >[!NOTE]
   >
   >Falls `bundle.info` unter `bundle52` nicht das Paket `org.apache.felix.http.bridge` enthält, überprüfen Sie die Paketnummer in der eckigen Klammer neben `org.apache.felix.http.bridge`. Navigieren Sie dann zu [aem-forms root]\crx-repository\launchpad\felix\bundle[x] und führen Sie die nächsten Schritte an dieser Stelle aus.

1. Navigieren Sie zur URL `[aem-forms root]\crx-repository\launchpad\felix\bundle[x]\version0.1`.
1. Suchen Sie nach `bundle.jar` und benennen Sie `bundle.jar` in `bundle.jar.bak` um.
1. Kopieren Sie `Bundle for AEM 6.5 Forms on JEE Service Pack 15` aus der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bundle.jar) an dieser Stelle.
1. Starten Sie den Anwendungs-Server, warten Sie, bis sich die Protokolle stabilisiert haben und überprüfen Sie den Paketstatus.
1. Sobald sich alle Pakete im aktiven Zustand befinden, installieren Sie das [Fragment for AEM 6.5 Forms on JEE Service Pack 15](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) vom `system/console/bundles` und warten Sie, bis sich der Anwendungs-Server stabilisiert hat.
1. Stoppen Sie den Anwendungs-Server.
1. Navigieren Sie zu `[aem-forms root]\crx-repository\launchpad\felix\bundle52\version0.1` und löschen Sie `bundle.jar`.
1. Benennen Sie `bundle.jar.bak` in `bundle.jar` um.
1. Starten Sie den Anwendungs-Server.
