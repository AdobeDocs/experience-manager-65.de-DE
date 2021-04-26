---
title: Entwicklung AEM Handels
description: Erfahren Sie, wie Sie ein Commerce-fähiges AEM-Projekt mithilfe des AEM-Projektarchetyps generieren. Erfahren Sie, wie Sie das Projekt in einer lokalen Entwicklungs-Umgebung erstellen und bereitstellen.
topics: Commerce, Development
feature: Commerce Integration Framework
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 8ead3d1b24177effa4d40141408c5676eaabcc30
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 38%

---


# Entwickeln AEM Commerce {#develop}

Die Entwicklung AEM Commerce-Projekte auf der Grundlage von Commerce Integration Framework (CIF) für AEM folgt den gleichen Regeln und Best Practices wie andere AEM Projekte. Sehen Sie sich zuerst die folgenden Artikel an:

- [AEM 6.5-Entwickleranleitung](/help/sites-developing/home.md)
- [Grundlegende AEM-Konzepte](/help/sites-developing/the-basics.md)
- [AEM-Entwicklung – Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md)
- [So erstellen Sie AEM-Projekte mit Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale Entwicklung für AEM Commerce {#local}

Für die Arbeit mit CIF-Projekten wird eine lokale Entwicklungsumgebung empfohlen.

>[!NOTE]
>
>Die folgenden Anweisungen helfen Ihnen beim Einrichten einer lokalen AEM Umgebung für AEM Commerce mit CIF mit Schwerpunkt für AEM 6.5). Wenn Sie AEM als Cloud Service verwenden, lesen Sie bitte die [AEM Commerce as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/home.html)-Dokumentation.

Das AEM Commerce Hinzufügen-On für AEM 6.5 alias. CIF Hinzufügen-On steht auch für die lokale Entwicklung zur Verfügung und wird als AEM angeboten. Es kann als Feature Pack vom [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) heruntergeladen werden.

### Erforderliche Software

Folgendes sollte lokal installiert werden:

- Lokale AEM 6.5
- [AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)  7 oder höher
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 oder höher)
- [Knoten LTS](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Zugriff auf das CIF-Add-on

Das CIF-Add-on kann vom [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) heruntergeladen werden, suchen Sie nach &quot;AEM Commerce Add-on&quot;.

>[!TIP]
>
>Stellen Sie sicher, dass Sie immer die neueste Version des CIF-Add-ons verwenden.

### Lokales Setup

Für die Entwicklung lokaler CIF-Projekte unter Verwendung des AEM und des CIF-Add-ons:

1. Besorgen Sie sich die AEM 6.5 Version und installieren Sie das AEM 6.5 Service Pack. AEM 6.5 Service Pack 7 ist erforderlich, wir empfehlen jedoch, das letzte verfügbare Service Pack zu installieren.

1. Entpacken Sie die AEM.jar, um den `crx-quickstart`-Ordner zu erstellen, und führen Sie Folgendes aus:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Erstellen Sie einen `crx-quickstart/install`-Ordner.

1. Kopieren Sie das CIF-Add-on für alle Pakete, die Sie vom Software Distribution Portal heruntergeladen haben, in den Ordner `crx-quickstart/install`.

>[!TIP]
>
>Alternativ kann das CIF-Add-On-Paket auch über Package Manager installiert werden.

1. Beginn des AEM Schnellstarts

Überprüfen Sie das Setup über die OSGi-Konsole: `http://localhost:4502/system/console/osgi-installer`. Die Liste sollte die CIF-Add-on-bezogenen Bundles, Inhaltspakete und OSGI-Konfigurationen umfassen. Stellen Sie sicher, dass alle Pakete gestartet wurden.

## Projekt-Setup {#project}

Es gibt zwei Möglichkeiten, Ihr AEM Commerce-Projekt mit CIF Beginn.

### Verwenden des AEM-Projektarchetyps

Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) ist das wichtigste Tool für das Bootstrapping eines vorkonfigurierten Projekts, um mit CIF zu beginnen. CIF-Kernkomponenten und alle erforderlichen Konfigurationen können mit einer zusätzlichen Option in ein generiertes Projekt aufgenommen werden.

>[!TIP]
>
>Verwenden Sie [AEM-Projektarchetyp 25 oder höher](https://github.com/adobe/aem-project-archetype/releases), um das Projekt zu erstellen.

Weitere Informationen zum Generieren eines AEM-Projekts finden Sie in den [Anweisungen zur Verwendung](https://github.com/adobe/aem-project-archetype#usage) des AEM-Projektarchetyps. Verwenden Sie die Option `includeCommerce`, um CIF in das Projekt aufzunehmen.

Beispiel:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D aemVersion=6.5.5 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF-Kernkomponenten können in jedem Projekt verwendet werden, indem entweder das bereitgestellte `all`-Paket oder die Einzelperson mit dem CIF-Inhaltspaket und den dazugehörigen OSGI-Paketen eingeschlossen wird. Verwenden Sie die folgenden Abhängigkeiten, um einem Projekt manuell CIF-Kernkomponenten hinzuzufügen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### Verwenden des AEM Venia Reference Store

Eine zweite Möglichkeit, ein CIF-Projekt zu starten, besteht darin, den [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) zu klonen und zu verwenden. Der AEM Venia Reference Store ist ein Beispiel-Referenz-Storefront-Programm, das die Verwendung von CIF-Kernkomponenten für AEM demonstriert. Es ist als Best-Practice-Satz von Beispielen und als potenzieller Ausgangspunkt zur Entwicklung Ihrer eigenen Funktionalität gedacht.

Um mit dem Venia Reference Store zu beginnen, klonen Sie einfach das [Git Repository](https://github.com/adobe/aem-cif-guides-venia) und Beginn passen Sie das Projekt an Ihre Bedürfnisse an.

>[!NOTE]
>
>Das Venia Reference Store-Projekt enthält zwei Build-Profile für AEM as a Cloud Service und AEM 6.5. Schauen Sie sich die Datei [readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) des Projekts an, um zu sehen, wie sie verwendet werden. Verwenden Sie für AEM 6.5 das Profil `classic`.

### AEM mit dem Commerce-System verbinden

Um Ihr Projekt mit dem Commerce-System zu verbinden, muss AEM mit dem GraphQL-Endpunkt Ihres Commerce-Systems konfiguriert werden.

In beiden Fällen enthält ein Projekt, das vom [AEM Projektarchiv](https://github.com/adobe/aem-project-archetype) oder vom [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) generiert wurde, bereits eine [Standardkonfiguration](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json), die angepasst werden muss.

Ersetzen Sie den Wert von `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` durch den GraphQL-Endpunkt Ihres vom Projekt verwendeten Commerce-Systems.

Die AEM Commerce Hinzufügen-On- und CIF Core-Komponenten verbinden sich mit dem Commerce GraphQL Endpunkt über den AEM Server und direkt über den Browser. Clientseitige CIF-Kernkomponenten und CIF-Hinzufügen-On-Authoring-Werkzeuge stellen standardmäßig eine Verbindung zu `/api/graphql` her. Bei Bedarf kann dies über die CIF-Cloud Service-Konfiguration angepasst werden (siehe unten).

Das CIF-Add-on stellt ein GraphQL-Proxy-Servlet bei `/api/graphql` bereit. Wenn Sie nicht planen, einen lokalen AEM Dispatcher zu verwenden, wird empfohlen, auch das GraphQL-Proxy-Servlet zu konfigurieren.

Navigieren Sie zu http://localhost:4502/system/console/configMgr und erstellen Sie eine OSGI-Konfiguration für den `Adobe CIF GraphQL Proxy Configuration`-Dienst. Verwenden Sie denselben GraphQL-Endpunkt Ihres Commerce-Systems wie für den GraphQL-Client oben.

## Zusätzliche Ressourcen

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
