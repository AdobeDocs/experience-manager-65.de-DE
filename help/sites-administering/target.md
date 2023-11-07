---
title: Integrieren mit Adobe Target
seo-title: Integrating with Adobe Target
description: Erfahren Sie, wie Sie Adobe Experience Manager mit Adobe Target integrieren.
seo-description: Learn about integrating AEM with Adobe Target.
uuid: b90346e8-9757-4272-a870-bbe5e647303f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 454854f8-6053-406c-888d-f427777bf570
exl-id: 2b17d8cd-a43c-4d54-b990-a6f0cb1db22b
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 74%

---

# Integrieren mit Adobe Target{#integrating-with-adobe-target}

Als Teil von Adobe Marketing Cloud ermöglicht [Adobe Target](https://www.adobe.com/ro/solutions/testing-targeting/testandtarget.html) Ihnen die Steigerung der Inhaltsrelevanz durch Targeting und Messungen über alle Kanäle hinweg. Adobe Target wird von Marketing-Experten genutzt, um Online-Tests zu entwerfen und auszuführen, in kurzer Zeit Zielgruppensegmente zu erstellen (anhand des Verhaltens) und das Targeting für Inhalte und Online-Erlebnisse zu automatisieren. AEM hat den Zielgruppen-Workflow übernommen, der in Adobe Target Standard verwendet wird. Wenn Sie Target verwenden, sind Sie mit der Targeting-Bearbeitungsumgebung in AEM vertraut.

Integrieren Sie Ihre AEM-Sites in Adobe Target, um Inhalte auf Ihren Seiten zu personalisieren:

* Implementieren Sie das Content-Targeting.
* Verwenden Sie Target-Zielgruppen, um personalisierte Erlebnisse zu erstellen.
* Senden Sie Kontextdaten an Target, wenn Besuchende mit Ihren Seiten interagieren.
* Verfolgen Sie Konversionsraten.

Führen Sie zur Integration mit Target die folgenden Aufgaben durch:

1. [Führen Sie vorbereitende Aufgaben durch](/help/sites-administering/target-requirements.md): Registrieren Sie sich bei Adobe Target und konfigurieren Sie bestimmte Aspekte der AEM-Autoreninstanz. Ihr Adobe Target-Konto muss mindestens über Berechtigungen auf der Ebene **Genehmigende Person** verfügen. Darüber hinaus müssen Sie die Aktivitätseinstellungen auf dem Veröffentlichungsknoten so sichern, dass sie für Benutzer nicht zugänglich sind.

1. Sie haben folgende Möglichkeiten:

   1. [Anmelden bei Adobe Target](/help/sites-administering/opt-in.md): Der Opt-in-Assistent übernimmt Ihre Target-Kontoinformationen und erstellt eine Adobe Target-Cloud-Konfiguration sowie ein Target-Framework. Der Assistent ordnet auch Ihre Sites dem Target-Framework zu. Wenn der Assistent keine Verbindung zu Target herstellen kann, lesen Sie den Abschnitt [Verbindungsfehler](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) Abschnitt. Sie können dann [Ändern der standardmäßigen Cloud-Konfigurationen](/help/sites-administering/target-configuring.md#modifying-the-opt-in-wizard-configurations): Ändern Sie bei Bedarf die Cloud-Konfiguration und das Framework, die vom Opt-in-Assistenten erstellt wurden. Ändern Sie beispielsweise das Framework, um zusätzliche Kontextdaten an Target zu senden. Wenn Sie Adobe Analytics als eine Reporting-Quelle für Adobe Target verwenden möchten, müssen Sie die Cloud-Konfiguration so ändern, dass Sie auf die A4T-Konfiguration verweist.
   1. [Führen Sie eine manuelle Integration mit Adobe Target durch](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).

1. [Konfigurieren Sie die Aktivitäten](/help/sites-authoring/activitylib.md): Verknüpfen Sie Ihre Aktivitäten mit der Target-Cloud-Konfiguration.

>[!NOTE]
>
>Siehe auch [Integrieren von AEM in Adobe Target und Adobe Analytics mithilfe von DTM](https://helpx.adobe.com/de/experience-manager/using/integrate-digital-marketing-solutions.html).

>[!NOTE]
>
>Wenn Sie Target mit einer benutzerdefinierten Proxy-Konfiguration verwenden, müssen Sie beide HTTP-Client-Proxy-Konfigurationen vornehmen, da manche Funktionen von AEM 3.x-APIs verwenden und andere wiederum 4.x-APIs:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.
>

>[!CAUTION]
>
>Sie müssen den Aktivitätseinstellungsknoten sichern **cq:ActivitySettings** auf der Veröffentlichungsinstanz, sodass sie für normale Benutzer nicht zugänglich ist. Der Aktivitätseinstellungsknoten sollte ausschließlich für den Service zur Verfügung stehen, mit dem die Aktivitätssynchronisierung mit Adobe Target durchgeführt wird.
>
>Detaillierte Informationen finden Sie unter [Voraussetzungen für die Integration mit Adobe Target](/help/sites-administering/target-requirements.md#securing-the-activity-settings-node).

Wenn die Integration abgeschlossen ist, können Sie [gezielte Inhalte verfassen](/help/sites-authoring/content-targeting-touch.md), die Besucherdaten an Adobe Target senden. Beachten Sie, dass Seitenkomponenten einen spezifischen Code für die Aktivierung von Content-Targeting benötigen. (Siehe [Entwicklung im Hinblick auf gezielte Inhalte](/help/sites-developing/target.md)).)

>[!NOTE]
>
>Wenn Sie eine Komponente in AEM Author anvisieren, führt die Komponente eine Reihe von Server-seitigen Aufrufen an Adobe Target durch, um die Kampagne zu registrieren, Angebote einzurichten und Adobe Target-Segmente abzurufen (falls konfiguriert). Es werden keine Server-seitigen Aufrufe von AEM Publish an Adobe Target vorgenommen.

## Quellen für Hintergrundinformationen {#background-information-sources}

Die Integration von AEM in Adobe Target erfordert Kenntnisse über Adobe Target, AEM Aktivitätsverwaltung und AEM Zielgruppen-Management. Sie sollten mit den folgenden Informationen vertraut sein:

* Adobe Target (siehe [Adobe Target-Dokumentation](https://experienceleague.adobe.com/docs/target/using/target-home.html?lang=de)).
* AEM-Aktivitätskonsole (siehe [Verwalten von Aktivitäten](/help/sites-authoring/activitylib.md)).
* AEM-Zielgruppen (siehe [Verwalten von Zielgruppen](/help/sites-authoring/managing-audiences.md)).

>[!NOTE]
>
>Bei der Arbeit mit Adobe Target ist Folgendes die maximal zulässige Anzahl an Artefakten innerhalb einer Kampagne:
>
>* 50 Speicherorte
>* 2.000 Erlebnisse
>* 50 Metriken
>* 50 Reporting-Segmente
>
