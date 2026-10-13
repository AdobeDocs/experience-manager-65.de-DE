---
title: Einführung in Java&trade; API QuickStart
description: Erfahren Sie, wie AEM Forms-Vorgänge mit der AEM Forms Java&trade;-API mit starker Typisierung und SOAP-Verbindung durchgeführt werden können.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop, development-tools
role: Developer
exl-id: 1d4062ef-fb24-4527-b899-896ce757beda
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 95%
---
# Einführung in den Java™-API-Schnellstart {#introducing-java-api-quickstart}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Die Kurzanleitung zu den Adobe AEM Forms-APIs kann Sie bei der schnelleren Entwicklung von Programmen unterstützen, die mit AEM Forms-Services interagieren. *Kurzanleitungen* sind komplette Programme, die Sie kopieren und in Ihre eigenen Projekte einfügen und als Ausgangspunkt verwenden können. Sie können eine Kurzanleitung ausführen, um zu sehen, wie das Programm sich verhält, und es für Ihre eigenen Anforderungen anpassen.

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API ausgeführt werden, und der Verbindungsmodus sollte auf SOAP festgelegt werden.

Der stark typisierte Java™-API-Schnellstart bietet eine Liste von JAR-Dateien, die zum Ausführen der Java™-Anwendung erforderlich sind. Die meisten Java™-Schnellstarts sind Konsolenanwendungen, die innerhalb von `main` ausgeführt werden. Der stark typisierte Forms Java™-API-Schnellstart wird jedoch als Java™-Servlet implementiert, das innerhalb einer Web-Anwendung ausgeführt wird.

Die Liste der JAR-Dateien befindet sich in einem Kommentarabschnitt am Anfang des Schnellstarts. Der folgende Kommentar befindet sich beispielsweise in einem Ausgabe-Schnellstart und ist eine typische JAR-Dateiliste, die in jedem Java™-Schnellstart enthalten ist.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-output-client.jar
     * 2. adobe--client.jar
     * 3. adobe-usermanager-client.jar
     *
     * These JAR files are in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client
     *
     * If you want to invoke a remote AEM Forms instance and there is a
     * firewall between the client application and AEM Forms, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms library files" in Programming
     * with AEM Forms
     */
```

## Kurzanleitung für mehrere Services {#multiple-services-quick-start}

Die meisten Schnellstarts, die sich in *Programmieren mit AEM Forms auf JEE* befinden, rufen einen bestimmten Service auf, um einen Vorgang durchzuführen. Einige Schnellstarts rufen jedoch mehrere AEM Forms-Dienste auf, um einen bestimmten Workflow durchzuführen. Die folgende Liste enthält Java™-Schnellstarts, die mehr als einen AEM Forms-Dienst aufrufen:

[Schnellstart (SOAP-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Ausgabe-Service mithilfe der Java™-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (ruft den Repository- und Ausgabe-Service auf)

[Schnellstart (SOAP-Modus): Erstellen eines auf Fragmenten basierenden PDF-Dokuments mithilfe der Java™-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (ruft den Assembler- und Ausgabe-Service auf)

[Schnellstart (SOAP-Modus): Erstellen von PDF-Dokumenten mit gesendeten XML-Daten mithilfe der Java™-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (ruft den Forms-, Ausgabe- und Document Management-Service auf)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java™-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (ruft den Forms- und Document Management-Dienst auf)

[Schnellstart (SOAP-Modus): Digitales Signieren eines XFA-basierten Formulars mit der Java™-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (ruft den Forms- und Signatur-Dienst auf)

[Schnellstart (SOAP-Modus): Verwalten von Rollen und Berechtigungen mithilfe der Java™-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (ruft den DirectoryManager- und den AuthorizationManager-Dienst auf)

[Schnellstart (SOAP-Modus): Übergeben von Dokumenten an den Ausgabe-Service mithilfe der Java™-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (ruft den Ausgabe- und Document Management-Service auf)

>[!NOTE]
>
>Schnellstarts für die Programmierung mit AEM Forms basierend auf der Bereitstellung von AEM Forms auf dem JBoss®-Anwendungs-Server und dem Microsoft® Windows®-Betriebssystem. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX® verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungs-Server verwenden, müssen Sie ebenfalls sicherstellen, dass Sie gültige Verbindungseigenschaften angeben. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Die meisten Webservice-Schnellstarts sind in C# geschrieben und verwenden das .NET-Framework. Sie können jedoch eine Client-Anwendungslogik erstellen, die in der Lage ist, AEM Forms-Services in jeder Entwicklungsumgebung aufzurufen, die SOAP-Standards unterstützt. (Siehe [Aufrufen von AEM Forms mithilfe von Web-Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
