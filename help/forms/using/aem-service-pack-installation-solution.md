---
title: Fehler bei CRX/Bundle und Startseitendienst nicht verfügbar, sobald das neueste Service Pack 6.5.15.0 installiert ist
description: Fehler bei CRX/Bundle und Startseitendienst nicht verfügbar, sobald das neueste Service Pack 6.5.15.0 installiert ist
exl-id: dfe015a3-3a24-41c5-aede-8e086851d62b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 93%

---

# Fehler „Dienst nicht verfügbar“ nach der Installation von AEM (6.5.15.0) Service Pack {#steps-to-resolve-error-after-installing-service-pack}

## Problem {#issue}

Nach der Installation des [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) tritt der Fehler wie folgt auf:
* FEHLER [FelixDispatchQueue] org.apache.sling.scripting.console FrameworkEvent FEHLER (org.osgi.framework.BundleException: org.apache.sling.scripting.console kann nicht aufgelöst werden

Nach der Installation von AEM 6.5.15.0 Service Pack zeigen das CRX/Bundle und die Startseite Fehlermeldungen an, dass der Dienst nicht verfügbar ist.

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
1. Öffnen Sie die Datei `bundle.info` in einem Texteditor und suchen Sie nach dem Bundle-Namen als `org.apache.felix.http.bridge`.

   >[!NOTE]
   >
   >In diesem Fall `bundle.info` under `bundle52` enthält nicht die `org.apache.felix.http.bridge` Bundle, überprüfen Sie die Bundle-Nummer in eckiger Klammer neben `org.apache.felix.http.bridge`. Navigieren Sie dann zu [aem-forms root]\crx-repository\launchpad\felix\bundle[x] und führen Sie die nächsten Schritte an dieser Stelle aus.

1. Navigieren Sie zur URL `[aem-forms root]\crx-repository\launchpad\felix\bundle[x]\version0.1`.
1. Suchen Sie nach `bundle.jar` und benennen Sie `bundle.jar` in `bundle.jar.bak` um.
1. Kopieren Sie `Bundle for AEM 6.5 Forms on JEE Service Pack 15` aus der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bundle.jar) an dieser Stelle.
1. Starten Sie den Anwendungs-Server, warten Sie, bis sich die Protokolle stabilisiert haben und überprüfen Sie den Bundle-Status.
1. Sobald sich alle Bundles im aktiven Zustand befinden, installieren Sie das [Fragment for AEM 6.5 Forms on JEE Service Pack 15](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) vom `system/console/bundles` und warten Sie, bis sich der Anwendungs-Server stabilisiert hat.
1. Stoppen Sie den Anwendungs-Server.
1. Navigieren Sie zu `[aem-forms root]\crx-repository\launchpad\felix\bundle52\version0.1` und löschen Sie `bundle.jar`.
1. Benennen Sie `bundle.jar.bak` in `bundle.jar` um.
1. Starten Sie den Anwendungs-Server.
