---
title: Übersicht über die neuen Funktionen | AEM 6.5 Forms
seo-title: Übersicht über die neuen Funktionen | AEM 6.5 Forms
description: Neueste Funktionen und Verbesserungen bei Formularen und Dokumenten der fortschrittlichsten Lösung für das digitale Experience Management.
seo-description: Neueste Funktionen und Verbesserungen bei Formularen und Dokumenten der fortschrittlichsten Lösung für das digitale Experience Management.
uuid: 179d372d-b7f6-4771-8349-fc6b7854efac
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 0e949429-cd5f-4301-aa72-14803cdfab00
docset: aem65
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Übersicht über die neuen Funktionen | AEM 6.5 Forms{#new-features-summary-aem-forms}

## Transaktionsberichte {#transaction-reports}

Mit Transaktionsberichten können Sie die Anzahl der gesendeten Formulare, verarbeiteten Dokumente und gerenderten Dokumente erfassen und verfolgen. Das Ziel bei der Verfolgung dieser Transaktionen besteht darin, eine fundierte Entscheidung über die Produktverwendung zu treffen und Investitionen in Hardware und Software neu auszurichten. Beispiele für Transaktionen:

* Übermitteln eines adaptiven Formulars, eines HTML5-Formulars oder eines Formularsatzes
* Darstellung eines Drucks oder einer Webversion einer interaktiven Kommunikation
* Konvertierung eines Dokuments von einem Dateiformat in ein anderes

Informationen zum Konfigurieren und Verwenden von Transaktionsberichten finden Sie unter Übersicht über [Transaktionsberichte](../../forms/using/transaction-reports-overview.md).

![Beispiel eines Transaktionsberichts](assets/surface_transaction_reporting.png)

## Interaktive Kommunikation {#interactive-communications}

**Datenanzeigemuster definieren**

Autoren interaktiver Kommunikation können jetzt [Datenanzeigemuster](create-interactive-communication.md#datadisplaypatterns) für Felder, Variablen und Formulardatenmodellelemente definieren. Beispiel: Datumsformat, Währung oder Telefonformat.

**Neue Diagrammtypen verwenden**

Sie können jetzt Diagramme und Diagramme mit [Quadranten mit mehreren Reihen](../../forms/using/chart-component-interactive-communications.md) zu interaktiven Mitteilungen hinzufügen.

**Spalten in einer Tabelle sortieren**

In der interaktiven Kommunikation können Sie jetzt Tabellenspalten [sortieren](../../forms/using/create-interactive-communication.md#sortcolumns) . Sie können Tabellenspalten mit statischem Text oder Datenmodellobjekten binden und sortieren.

**Neue Komponenten in einem Web-Kanal verwenden**

Sie können dem Web-Kanal jetzt Schaltflächen- und Trennzeichenkomponenten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen Schaltflächenkomponente zur Webkomponente &quot;Kanal](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) &quot;und &quot; [Trennzeichenkomponente&quot;in Web Kanal](../../forms/using/create-interactive-communication.md#separatorcomponent).

**Layout-Modus zur Größenanpassung von Komponenten**

Sie können jetzt mithilfe einer WYSIWYG-Schnittstelle zum [Layoutmodus](../../forms/using/resize-using-layout-mode.md) wechseln, um die Größe von Komponenten im Web Kanal zu ändern.

**Verbesserungen der Benutzerfreundlichkeit**

Autoren interaktiver Kommunikation können beim Erstellen von Schriftstücken jetzt verschiedene, einfach zu bedienende Vorgänge verwenden. Die Liste der Maßnahmen umfasst:

* [Rückgängigmachen von Wiederholungsaktionen in Druck- und Web-Kanälen](../../forms/using/create-interactive-communication.md#undoredoactions)
* [Variablen in einem Dokument-Fragment mit dem Symbol @ Hinzufügen](../../forms/using/texts-interactive-communications.md#searchvariables)
* [Hinzufügen von Datenmodellelementen in einem Dokument-Fragment mit dem @-Symbol](../../forms/using/texts-interactive-communications.md#searchdatamodelproperties)
* [Löschen oder Hinzufügen eines Web-Kanals zu einer vorhandenen interaktiven Kommunikation](../../forms/using/create-interactive-communication.md#edit-interactive-communication-properties)
* [Binden von Datenquellenelementen mit Feldern und Variablen mithilfe von Drag &amp; Drop-Aktionen](../../forms/using/create-interactive-communication.md#binddatasourceelements)
* [Ungebundene Felder und Variablen beim Authoring der interaktiven Kommunikation hervorheben](../../forms/using/create-interactive-communication.md#distinguishunboundfields)
* [Durchführen zusätzlicher Aktionen wie Kopieren, Gruppieren oder mehr für geerbte Komponenten in einem Web Kanal](../../forms/using/create-interactive-communication.md#componenttoolbar)

**Verbesserungen beim Synchronisierungsprozess**

Das Web-Kanal-Layout, das mit dem Kanal &quot;Drucken&quot;automatisch generiert wird, wurde um einige Verbesserungen erweitert.

![Diagramme für interaktive Kommunikation](assets/interactive-communication-charts.png)

## Adaptive Formulare {#adaptive-forms}

### Verwenden der Cloud-basierten digitalen Signaturen von Adobe Sign in adaptiven Formularen {#use-adobe-sign-s-cloud-based-digital-signatures-in-adaptive-forms}

[Cloud-basierte digitale Signaturen](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) oder Remote-Signaturen sind eine neue Generation digitaler Signaturen, die über Desktop, Mobilgeräte und das Web funktioniert — und die höchste Kompatibilitätsstufe und die höchste Sicherheit für die Signiererauthentifizierung erfüllen. Sie können jetzt ein adaptives Formular [mit Cloud-basierten digitalen Signaturen](../../forms/using/working-with-adobe-sign.md) signieren.

#### Embed an Adaptive Form or Interactive Communication in AEM Sites Single Page Applications {#embed-an-adaptive-form-or-interactive-communcation-in-aem-sites-single-page-applications}

Mit AEM Forms können Sie ein adaptives Formular [oder eine interaktive Kommunikation](../../forms/using/embed-adaptive-form-aem-sites-spa.md) nahtlos in eine Einzelseitenanwendung (SPA) von AEM Sites einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig. Benutzer können das Formular ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem adaptiven Formular oder der interaktiven Kommunikation zu interagieren.

#### Spalten in Tabellen des adaptiven Formulars sortieren {#sort-columns-of-adaptive-form-tables}

Sie können jede Spalte einer Tabelle [für adaptives Formular in auf- oder absteigender Reihenfolge](../../forms/using/adaptive-forms-tables.md#sortcolumnstable) sortieren. Sie können die Sortierung auf Tabellenspalten mit statischem Text, Datenmodellobjekteigenschaften oder einer Kombination aus statischen Text- und Datenmodellobjekteigenschaften anwenden.

#### Die Verfügbarkeit von Vorlagen für adaptive Formulare auf bestimmte Pfade beschränken {#restrict-the-availability-of-adaptive-forms-templates-to-specific-paths}

Adaptive Formulare unterstützen jetzt die Eigenschaft cq:allowedPaths. Die Eigenschaft [beschränkt die Verfügbarkeit von Vorlagen für adaptive Formulare auf bestimmte Pfade](../../forms/using/creating-adaptive-form.md#main-pars-text).

#### Kontrollkästchen für das adaptive Formular dynamisch Hinzufügen {#add-check-boxes-to-the-adaptive-form-dynamically}

Sie können nun Regeln definieren, um dem adaptiven Formular basierend auf benutzerdefinierten Funktionen, Formularobjekten oder Objekteigenschaften dynamisch [Kontrollkästchen](../../forms/using/rule-editor.md#setpropertyrule) hinzuzufügen.

## AEM-Workflows {#aem-workflows}

### Variablen in AEM Workflows verwenden {#use-variables-in-aem-workflows}

Variablen ermöglichen Arbeitsablaufschritte zum Speichern und Übergeben von Metadaten über Arbeitsablaufschritte zur Laufzeit. Sie können verschiedene Typen von Variablen zum Speichern verschiedener Datentypen erstellen. Beispielsweise Ganzzahlen, Zeichenfolgen, Dokumente oder Formulardatenmodellinstanzen. In der Regel verwenden Sie eine Variable oder eine Sammlung von Variablen, wenn Sie eine Entscheidung basierend auf dem Wert treffen müssen, den sie enthält, oder Informationen speichern möchten, die Sie später in einem Prozess benötigen.

Variablen sind eine Erweiterung der in der vorherigen Version verfügbaren [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) -Schnittstelle. Auf diese Weise sparen Sie Zeit beim Entwickeln von benutzerspezifischem ECMAScript-Code, der zum Abrufen und Aktualisieren von Metadatenwerten verwendet wird. Sie verwenden weiterhin die MetaDataMap-Schnittstelle und den ECMAScript-Code zum Bearbeiten von Metadaten. Die Verwendung von Variablen über MetaDataMap und ECMAScript bietet unter anderem folgende Vorteile:

* Dynamische Speicherung, Aktualisierung und Verwendung von Werten, die in einer Variablen gespeichert sind, im gesamten Workflow ohne Verwendung von benutzerspezifischem Code
* Abrufen und Aktualisieren von Werten direkt in ein Formulardatenmodell und eine Datendatei (XML/JSON) eines gesendeten Formulars
* Speichern Sie vollständige Dokumente in einer Variablen, um die Verarbeitung von Dokumenten durchzuführen

Der Schritt &quot;Gehe zu&quot;, &quot;ODER teilen&quot;, und alle AEM Forms-Workflow-Schritte unterstützen Variablen. Sie können die MetaDataMap-Schnittstelle verwenden, um auf Variablen in Workflow-Schritten zuzugreifen, die keine native Unterstützung für Variablen haben. Weitere Informationen finden Sie unter [Variablen in AEM Workflows](../../forms/using/variable-in-aem-workflows.md).

![Festlegen einer Variablen für einen Workflow](assets/variable.png)

#### Verwenden eines Workflows mit verschiedenen adaptiven Formularen {#use-a-workflow-with-different-adaptive-forms}

Sie können ein adaptives Formular für die zuweisende Aufgabe [und das Dokument des Datensatzschritts der formularzentrierten Workflows zur Laufzeit](../../forms/using/aem-forms-workflow-step-reference.md#assign-task-step) angeben. Dadurch kann ein Workflow mit verschiedenen adaptiven Formularen arbeiten. Sie können die Methode zur Auswahl eines adaptiven Formulars beim Entwerfen des Workflows festlegen. Das adaptive Formular kann sich an einem absoluten Pfad befinden, als Payload an den Workflow gesendet werden, oder an einem Pfad verfügbar sein, der mithilfe einer Variablen berechnet wird.

#### Erweiterte Protokollierungsfunktionen für formularorientierte Workflow-Schritte {#use-enhanced-logging-capabilities-of-forms-centric-workflow-steps}

Die Protokollierungsfunktionen von formularorientierten Workflow-Schritten werden standardisiert. Alle formularzentrierten Arbeitsablaufschritte erzeugen ähnlich standardisierte Protokolle. Dadurch wird die Debugging-Geschwindigkeit verbessert.

## Datenintegration {#data-integration}

Sie können jetzt:

* [Überprüfen Sie die Eingabedaten](../../forms/using/work-with-form-data-model.md#automated-validation-of-input-data) anhand einer Liste von Einschränkungen. Dadurch wird sichergestellt, dass nur gültige Daten an die Datenquelle gesendet werden.
* [Überschreiben Sie den in einer WSDL-Datei (Web Services Description Language) definierten Standard-Endpunkt](../../forms/using/configure-data-sources.md#configure-soap-web-services) .

* [Außerkraftsetzen des standardmäßigen](../../forms/using/configure-data-sources.md#configure-restful-web-services) [Schemas, Hosts und Basispfades](../../forms/using/configure-data-sources.md#configure-restful-web-services) , der in der Swagger-Definitionsdatei definiert ist.

## Plattformaktualisierungen und Sicherheitsupdates {#platform-and-security-updates}

### Wichtige Plattformupdates {#major-platform-updates}

AEM Forms kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungsservern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden. The following are the major changes in [supported platforms](../../forms/using/aem-forms-jee-supported-platforms.md):

<table>
 <tbody>
  <tr>
   <td>Komponente</td>
   <td>Unterstützung entfernt</td>
  </tr>
  <tr>
   <td>Betriebssysteme</td>
   <td>
    <ul>
     <li>Microsoft Windows Server 2012 R2</li>
     <li>IBM AIX*</li>
     <li>Sun Solaris*</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Anwendungsserver<br /> </td>
   <td>
    <ul>
     <li>Oracle Weblogic</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datenbanken</td>
   <td>
    <ul>
     <li>IBM DB2 <br /> </li>
     <li>Oracle RAC</li>
    </ul> </td>
  </tr>
  <tr>
   <td>LDAP-Server</td>
   <td>
    <ul>
     <li>Microsoft Active Directory 2012</li>
     <li>Novell eDirectory 8.8.7 </li>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>E-Mail-Server</td>
   <td>
    <ul>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Connectoren</td>
   <td>
    <ul>
     <li>Connector für Microsoft Sharepoint 2013</li>
     <li>Connector für EMC Documentum 7.0</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Forms-App<br /> </td>
   <td>
    <ul>
     <li>Unterstützung für Windows 8.1</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Java </td>
   <td>
    <ul>
     <li>Java 11</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

* Wenden Sie sich an den Adobe Support, um Informationen zur Migration auf eine andere Plattform zu erhalten.

#### Neue HTML5-basierte Benutzeroberfläche {#new-html-based-uis}

In Übereinstimmung mit der geplanten EOL-Version von Adobe Flash Player und der allgemeinen Ausrichtung der Migration von Flash-basierten Inhalten auf offene Standards hat AEM 6.5 Forms die Flash-basierte Benutzeroberfläche von Health Monitor, Process Management, Reader Extension und Kategorie Management UI von AEM Forms on JEE Administration Console durch eine HTML5-basierte Benutzeroberfläche ersetzt.

#### Sicherheitsverbesserungen {#security-improvements}

* Die Benutzeroberfläche von AEM 6.5 Forms on JEE Administration Console basiert jetzt auf Apache Struts 2.5.
* AEM 6.5 Forms verwendet jetzt jQuery bis 3.2.1 und jQuery UI 1.12.1. Informationen zu den Auswirkungen der Änderung finden Sie in der [Aktualisierungsdokumentation](/help/forms/home.md) .

#### Verbesserungen der Zugänglichkeit {#accessibility-improvements}

AEM 6.5 Forms hat die Barrierefreiheit von AEM Forms Workspace verbessert.
