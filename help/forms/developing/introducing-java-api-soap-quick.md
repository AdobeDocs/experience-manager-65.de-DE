---
title: Einführung in Java API QuickStart
seo-title: Introducing Java API QuickStart
description: Einführung in Java API QuickStart
uuid: 480e1809-f789-4ad8-b5d5-2d97aba8411a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop, development-tools
discoiquuid: 38fd51ec-347e-4ae3-86d4-9d2429f79bdd
role: Developer
exl-id: 1d4062ef-fb24-4527-b899-896ce757beda
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 100%

---

# Kurzanleitung zur Einführung in die Java-API {#introducing-java-api-quickstart}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Die Kurzanleitung zu den Adobe AEM Forms-APIs kann Sie bei der schnelleren Entwicklung von Programmen unterstützen, die mit AEM Forms-Services interagieren. *Kurzanleitungen* sind komplette Programme, die Sie kopieren und in Ihre eigenen Projekte einfügen und als Ausgangspunkt verwenden können. Sie können eine Kurzanleitung ausführen, um zu sehen, wie das Programm sich verhält, und es für Ihre eigenen Anforderungen anpassen.

AEM Forms-Vorgänge können mit der stark typisierten AEM Forms-API durchgeführt werden und der Verbindungsmodus sollte auf SOAP eingestellt werden.

Eine Java-Kurzanleitung mit starker Typisierung für die API bietet eine Liste von JAR-Dateien, die zum Ausführen des Java-Programms erforderlich sind. Die meisten Java-Kurzanleitungen sind Konsolenprogramme, die innerhalb von `main` ausgeführt werden. Die Forms-Java-Kurzanleitung mit starker Typisierung für die API wird jedoch als Java-Servlet implementiert, das innerhalb eines Web-Programms ausgeführt wird.

Die Liste der JAR-Dateien befindet sich in einem Kommentarabschnitt am Anfang der Kurzanleitung. Der folgende Kommentar befindet sich beispielsweise in einer Kurzanleitung für die Ausgabe und ist eine typische JAR-Dateiliste, die in jeder Kurzanleitung für Java enthalten ist.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-output-client.jar
     * 2. adobe--client.jar
     * 3. adobe-usermanager-client.jar
     *
     * These JAR files are located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common
     *
     * The adobe-utilities.jar file is located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss
     *
     * The jboss-client.jar file is located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client
     *
     * If you want to invoke a remote AEM Forms instance and there is a
     * firewall between the client application and AEM Forms, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files located in the following
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

Die meisten Kurzanleitungen, die sich in *Programmieren mit AEM Forms auf JEE* befinden, rufen einen bestimmten Service auf, um einen Vorgang durchzuführen. Einige Kurzanleitungen rufen jedoch mehrere AEM Forms-Service auf, um einen bestimmten Workflow durchzuführen. Die folgende Liste enthält Java-Kurzanleitungen, die mehr als einen AEM Forms-Service aufrufen:

[Kurzanleitung (SOAP-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (ruft den Repository- und Ausgabe-Service auf)

[Kurzanleitung (SOAP-Modus): Erstellen eines PDF-Dokuments, das auf Fragmenten basiert, mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (ruft den Assembler- und Ausgabe-Service auf)

[Kurzanleitung (SOAP-Modus): Erstellen von PDF-Dokumenten mit gesendeten XML-Daten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (ruft den Forms-, Ausgabe- und Document Management-Service auf)

[Kurzanleitung (SOAP-Modus): Übergeben von Dokumenten an den Forms-Service mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (ruft den Forms- und Document Management-Service auf)

[Kurzanleitung (SOAP-Modus): Digitales Signieren eines XFA-basierten Formulars mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (ruft den Forms- und Signature-Service auf)

[Kurzanleitung (SOAP-Modus): Verwalten von Rollen und Berechtigungen mithilfe der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (ruft den DirectoryManager- und den AuthorizationManager-Service auf)

[Kurzanleitung (SOAP-Modus): Übergeben von Dokumenten an den Ausgabe-Service mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (ruft den Ausgabe- und Document Management-Service auf)

>[!NOTE]
>
>Kurzanleitungen für die Programmierung mit AEM Forms basieren auf der Bereitstellung von AEM Forms auf dem JBoss®-Programm-Server und dem Microsoft® Windows®-Betriebssystem. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX® verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungs-Server verwenden, müssen Sie ebenfalls sicherstellen, dass Sie gültige Verbindungseigenschaften angeben. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Die meisten Webservice-Kurzanleitungen sind in C# geschrieben und verwenden das .NET-Framework. Sie können jedoch eine Client-Anwendungslogik erstellen, die in der Lage ist, AEM Forms-Services in jeder Entwicklungsumgebung aufzurufen, die SOAP-Standards unterstützt. (Siehe [Aufrufen von AEM Forms mithilfe von Web-Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
