---
title: Einführung in Java API QuickStart
seo-title: Einführung in Java API QuickStart
description: 'null'
seo-description: 'null'
uuid: 480e1809-f789-4ad8-b5d5-2d97aba8411a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools
discoiquuid: 38fd51ec-347e-4ae3-86d4-9d2429f79bdd
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---


# Einführung in Java API Quick Beginn {#introducing-java-api-quickstart}

Der Adobe AEM Forms API Quick Beginn unterstützt Sie bei der Beschleunigung Ihrer Bemühungen, Programm zu entwickeln, die mit AEM Forms-Diensten interagieren. *Quick* Beginn sind vollständige Programme, die Sie kopieren und in Ihre eigenen Projekte einfügen können und als Ausgangspunkt verwenden können. Sie können einen Quick Beginn ausführen, um zu sehen, wie er sich verhält, und ihn für Ihre eigenen Anforderungen anpassen.

AEM Forms-Vorgänge können mit der stark typisierten API von AEM Forms ausgeführt werden, und der Verbindungsmodus sollte auf SOAP eingestellt werden.

Java-Schnelleingabe-API-Beginn bietet eine Liste der JAR-Dateien, die zum Ausführen der Java-Anwendung erforderlich sind. Bei den meisten Java Quick-Beginn handelt es sich um eine Konsolenanwendung, die innerhalb von `main`ausgeführt wird. Der Java-Schnelleintrag für Formulare wird jedoch als Java-Servlet implementiert, das in einer Webanwendung ausgeführt wird.

Die JAR-Dateiliste befindet sich in einem Kommentarabschnitt am Anfang des Quick Beginns. Der folgende Kommentar befindet sich beispielsweise in einem Output Quick Beginn und ist eine typische JAR-Dateiliste, die in jedem Java Quick Beginn enthalten ist.

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

## Schnellerer Beginn zu mehreren Diensten {#multiple-services-quick-start}

Die meisten Quick-Beginn unter *Programmieren mit AEM Forms on JEE* rufen einen bestimmten Dienst auf, um einen Vorgang auszuführen. Einige Quick-Beginn rufen jedoch mehrere AEM Forms-Dienste auf, um einen bestimmten Workflow auszuführen. Die folgende Liste bietet Java-Schnellzugriff-Beginn, die mehr als einen AEM Forms-Dienst aufrufen:

[Quick Beginn (SOAP-Modus): Übergeben eines Dokuments im AEM Forms-Repository an den Output-Dienst mithilfe der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (ruft den Repository- und den Output-Dienst auf)

[Quick Beginn (SOAP-Modus): Erstellen eines PDF-Dokuments basierend auf Fragmenten mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (ruft den Assembler- und den Output-Dienst auf)

[Quick Beginn (SOAP-Modus): Erstellen von PDF-Dokumenten mit gesendeten XML-Daten mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (ruft den Forms-, Output- und Dokument-Verwaltungsdienst auf)

[Quick Beginn (SOAP-Modus): Übergeben von Dokumenten an den Forms-Dienst mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (ruft den Forms and Dokument Management-Dienst auf)

[Quick Beginn (SOAP-Modus): Digitales Signieren eines XFA-basierten Formulars mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (ruft den Forms and Signature-Dienst auf)

[Quick Beginn (SOAP-Modus): Rollen und Berechtigungen mithilfe der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) verwalten (ruft den DirectoryManager und den AuthorizationManager-Dienst auf)

[Quick Beginn (SOAP-Modus): Übergeben von Dokumenten an den Output-Dienst mit der Java-API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (Aufruf des Output- und Dokument-Verwaltungsdiensts)

>[!NOTE]
>
>Quick Beginn, die sich unter Programmieren mit AEM Forms befinden, basieren auf AEM Forms, die auf JBoss® Application Server und dem Microsoft® Windows®-Betriebssystem bereitgestellt werden. Wenn Sie jedoch ein anderes Betriebssystem wie UNIX® verwenden, ersetzen Sie Windows-spezifische Pfade durch Pfade, die vom jeweiligen Betriebssystem unterstützt werden. Wenn Sie einen anderen J2EE-Anwendungsserver verwenden, stellen Sie sicher, dass Sie gültige Verbindungseigenschaften angeben. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>Die meisten Quick-Beginn für Webdienste werden in C# geschrieben und verwenden das .NET-Framework. Sie können jedoch eine Client-Anwendungslogik erstellen, mit der AEM Forms-Dienste in jeder Umgebung aufgerufen werden können, die SOAP-Standards unterstützt. (See [Invoking AEM Forms Using Web Services](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

