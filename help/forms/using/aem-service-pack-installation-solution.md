---
title: CRX/Bundle- und Start-Seitendienst nicht verfügbare Fehler, sobald das neueste Service Pack 6.5.15.0 installiert ist
description: CRX/Bundle- und Start-Seitendienst nicht verfügbare Fehler, sobald das neueste Service Pack 6.5.15.0 installiert ist
source-git-commit: 974796a6b9e921f8c2f40d72a4764eb9f4d8b92b
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 16%

---


# Service unavailable error after install AEM (6.5.15.0) service pack {#steps-to-resolve-error-after-installing-service-pack}

## Problem {#issue}

Nach der Installation der [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip), tritt der Fehler wie folgt auf:
* FEHLER [FelixDispatchQueue] org.apache.sling.scripting.console FrameworkEvent-FEHLER (org.osgi.framework.BundleException: org.apache.sling.scripting.console kann nicht aufgelöst werden

Nach der Installation von AEM 6.5.15.0 Service Pack zeigen das CRX/Bundle und die Startseite unverfügbare Fehler an.

## Gilt für {#applies-to}

Diese Lösung gilt für:
* AEM Forms auf allen JEE-Servern mit Ausnahme der JBoss EAP 7.4.0

## Lösung {#solution}

>[!NOTE]
>
>Die Schritte zur Fehlerbehebung gelten für alle Anwendungsserver außer JBoss EAP 7.4.

Nach der Installation [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip), wenn CRX/Bundle und die Startseite Fehler anzeigen, die nicht verfügbar sind, führen Sie die folgenden Schritte aus:

1. Beenden Sie den Anwendungsserver.
1. Navigieren Sie zu `[aem-forms root]\crx-repository\launchpad\felix\bundle52`.
1. Suchen Sie die `bundle.info` -Datei.
1. Öffnen Sie die `bundle.info` -Datei im Texteditor und suchen Sie nach dem Bundle-Namen als `org.apache.felix.http.bridge`.

   >[!NOTE]
   >
   >In diesem Fall `bundle.info` under `bundle52` enthält nicht die `org.apache.felix.http.bridge` Bundle, überprüfen Sie die Bundle-Nummer in eckiger Klammer neben `org.apache.felix.http.bridge`. Navigieren Sie dann zu [AEM-Forms-Stamm]\crx-repository\launchpad\felix\bundle[x] und führen Sie die nächsten Schritte an dieser Stelle aus.

1. zu URL navigieren: `[aem-forms root]\crx-repository\launchpad\felix\bundle[x]\version0.1`.
1. Suchen Sie nach `bundle.jar` und benennen Sie die `bundle.jar` nach `bundle.jar.bak`.
1. Kopieren Sie die `Bundle for AEM 6.5 Forms on JEE Service Pack 15` an dieser Stelle aus dem [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bundle.jar).
1. Starten Sie den Anwendungsserver, warten Sie, bis sich die Protokolle stabilisieren, und überprüfen Sie den Bundle-Status.
1. Sobald sich alle Pakete im aktiven Status befinden, installieren Sie die [Fragment für AEM 6.5 Forms on JEE Service Pack 15](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) von `system/console/bundles` und warten Sie, bis sich der Anwendungsserver stabilisiert.
1. Beenden Sie den Anwendungsserver.
1. Navigieren Sie zu `[aem-forms root]\crx-repository\launchpad\felix\bundle52\version0.1` und löschen Sie die `bundle.jar`.
1. Benennen Sie die `bundle.jar.bak` der `bundle.jar`.
1. Starten Sie den Anwendungsserver.