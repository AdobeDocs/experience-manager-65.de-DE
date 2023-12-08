---
title: Übersicht über die neuen Funktionen | AEM 6.5 Forms
description: Neueste Funktionen und Verbesserungen für AEM Formulare und Dokumente, die weltweit fortschrittlichste Lösung für das digitale Erlebnismanagement.
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 47b9de1f-b16a-424c-b8b4-e9d7b3dcca86
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 4%

---

# Übersicht über die neuen Funktionen | AEM 6.5 Forms{#new-features-summary-aem-forms}

| Produkt | Adobe Experience Manager 6.5 |
| -------- | ---------------------------- |
| Version | 6.5.19.0 |
| Typ | Service Pack-Version |
| Datum | Samstag, 8. Dezember 2023 |

## Was ist in Adobe Experience Manager 6.5 Forms Service Pack 19 (6.5.19.0) enthalten?

Experience Manager 6.5.19.0 enthält neue Funktionen, wichtige von Kunden angeforderte Verbesserungen, Fehlerbehebungen sowie Leistungs-, Stabilitäts- und Sicherheitsverbesserungen, die seit der ersten Verfügbarkeit von 6.5 im April 2019 veröffentlicht wurden. [Dieses Service Pack installieren](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de) Experience Manager 6.5.

### Neue Funktionen

#### Neue Kernkomponenten für adaptive Formulare

Vertikale Registerkarten, Geschäftsbedingungen und Kontrollkästchen werden hinzugefügt, um die Skalierbarkeit von Formularen zu verbessern.

* **[Kontrollkästchenkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt eine Kontrollkästchenkomponente enthalten. Sie ermöglicht Benutzern, binäre Entscheidungen zu treffen, eine bestimmte Option auszuwählen oder zu deaktivieren. Es wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: &quot;aktiviert&quot;und &quot;deaktiviert&quot;. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder true/false-Auswahl zu geben.

* **[Komponente &quot;Allgemeine Geschäftsbedingungen&quot;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt eine Komponente für Geschäftsbedingungen enthalten. Sie ermöglicht es Formularautoren, einen bestimmten Abschnitt innerhalb des Formulars einzuführen, in dem den Benutzern die Bedingungen oder rechtlichen Vereinbarungen im Zusammenhang mit der Verwendung eines Dienstes, Produkts oder einer Plattform präsentiert werden. Diese Komponente soll Benutzer über die Regeln, Vorschriften und Verpflichtungen informieren, denen sie zustimmen, indem sie das Formular übermitteln.

  ![Vertikale Registerkarten, Geschäftsbedingungen und Kontrollkästchen-Komponenten](/help/forms/using/assets/forms-components.png)

* **[Komponente mit vertikalen Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: Der auf Kernkomponenten basierende adaptive Forms kann jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bereitstellen. Die Verwendung von vertikalen Registerkarten in einem Formular kann das gesamte Benutzererlebnis verbessern, indem die Navigation vereinfacht und die Organisation des Formularinhalts verbessert wird, insbesondere in Situationen, in denen ein Formular mehrere Abschnitte oder komplexe Informationen enthält.

#### 64-Bit-Version von AEM Forms Designer

Die [64-Bit-Version von AEM Forms Designer](/help/forms/using/installing-configuring-designer.md) bietet verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Erstellung von Formularen zu optimieren. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfskompetenzen und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

#### Verbinden einer adaptiven Forms-Liste mit Microsoft® SharePoint-Liste

AEM Forms bietet eine OOTB-Integration für [Formulardaten direkt an SharePoint List senden](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)), sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft® SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion &quot;Senden mit Formulardatenmodell&quot;verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

#### Unterstützung zum Konfigurieren der Eigenschaften des Datensatzdokuments für adaptive Formularfragmente

Sie können jetzt einfach [Anpassen der adaptiven Formularfragmente und ihrer Felder im Editor für adaptive Formulare](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).


## Fehlerbehebungen

Die Version enthält auch Fehlerbehebungen für mehr als 20 von Kunden gemeldete Probleme. Eine detaillierte Liste der im Service Pack enthaltenen Fehlerbehebungen finden Sie unter [Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=en#forms-6519)


## Service Pack installieren

Das Service Pack enthält neue Funktionen und Fehlerkorrekturen für AEM Forms on JEE und AEM Forms unter OSGi. Die Installationsanweisungen haben Änderungen gegenüber vorherigen Service Packs. Installationsanweisungen finden Sie unter [Installationsanweisungen für das AEM Forms Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=en).






<!-- 
## Transaction Reports {#transaction-reports}



Transaction reports lets you capture and track the number of submitted forms, processed documents, and rendered documents. The objective behind tracking these transactions is to make an informed decision about the product usage and rebalancing investments in hardware and software. Some examples of transactions include:

* Submission of an Adaptive Form, an HTML5 Form, or a Form Set
* Rendition of a print or a web version of an interactive communication
* Conversion of a document from one file format to another

For information about configuring and using transaction reports, see [Transaction Reports Overview](../../forms/using/transaction-reports-overview.md).

![A sample transaction report](assets/surface_transaction_reporting.png)

## Interactive Communications {#interactive-communications}

**Define data display patterns**

Interactive Communication authors can now define [data display patterns](create-interactive-communication.md#datadisplaypatterns) for fields, variables, and form data model elements. For example, date, currency, or phone formats.

**Use new types of charts**

You can now add [Quadrant charts and charts with multiple series](../../forms/using/chart-component-interactive-communications.md) to Interactive Communications.

**Sort columns in a table**

You can now [sort columns of a table](../../forms/using/create-interactive-communication.md#sortcolumns) in the Interactive Communication. You can bind and sort table columns with static text or data model objects.

**Use new components in a web channel**

You can now add Button and Separator components to the web channel. For more information, see [Add Button component to the web channel](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) and [Separator component in web channel](../../forms/using/create-interactive-communication.md#separatorcomponent).

**Layout mode to resize components**

You can now switch to [Layout mode](../../forms/using/resize-using-layout-mode.md) to resize components in the Web channel using a WYSIWYG interface.

**Usability improvements**

Interactive Communication authors can now utilize various easy-to-use operations while creating correspondences. The list of operations includes:

* [Perform undo-redo actions in print and web channels](../../forms/using/create-interactive-communication.md#undoredoactions)
* [Add variables in a document fragment using @ symbol](../../forms/using/texts-interactive-communications.md#searchvariables)
* [Add data model elements in a document fragment using @ symbol](../../forms/using/texts-interactive-communications.md#searchdatamodelproperties)
* [Delete or add a web channel to an existing Interactive Communication](../../forms/using/create-interactive-communication.md#edit-interactive-communication-properties)
* [Bind data source elements with fields and variables using drag-and-drop actions](../../forms/using/create-interactive-communication.md#binddatasourceelements)
* [Highlight unbound fields and variables while authoring Interactive Communication](../../forms/using/create-interactive-communication.md#distinguishunboundfields)
* [Perform additional actions such as copy, group, or more on inherited components in a web channel](../../forms/using/create-interactive-communication.md#componenttoolbar)

**Improvements in sync process**

There are several improvements in the Web channel layout auto-generated using the Print channel.

![Interactive Communications Charts](assets/interactive-communication-charts.png)

## Adaptive Forms {#adaptive-forms}

### Use Adobe Sign's cloud-based digital signatures in Adaptive Forms {#use-adobe-sign-s-cloud-based-digital-signatures-in-adaptive-forms}

[Cloud-based digital signatures](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) or remote signatures are a new generation of digital signatures that work across desktop, mobile, and the web — and meet the highest levels of compliance and assurance for signer authentication. You can now [sign an Adaptive Form](../../forms/using/working-with-adobe-sign.md) with Cloud-based digital signatures.

#### Embed an Adaptive Form or Interactive Communication in AEM Sites Single Page Applications {#embed-an-adaptive-form-or-interactive-communcation-in-aem-sites-single-page-applications}

AEM Forms lets you [seamlessly embed an Adaptive Form](../../forms/using/embed-adaptive-form-aem-sites-spa.md) or Interactive Communication in an AEM Sites single page application (SPA). The embedded Adaptive Form and Interactive Communication is fully functional and users can fill and submit the form without leaving the page. It helps user remain in context of other elements on the web page and simultaneously interact with the adaptive form or Interactive Communication.

#### Sort columns of Adaptive Form tables {#sort-columns-of-adaptive-form-tables}

You can [sort any column of an Adaptive Form table](../../forms/using/adaptive-forms-tables.md#sortcolumnstable) in an ascending or descending order. You can apply sorting to table columns with static text, data model object properties, or a combination of static text and data model object properties.

#### Restrict the availability of Adaptive Forms templates to specific paths {#restrict-the-availability-of-adaptive-forms-templates-to-specific-paths}

Adaptive forms has added support for the cq:allowedPaths property. The property [restricts availability of Adaptive Forms templates to specific paths](creating-adaptive-form.md#adaptive-form-templates).

#### Add check boxes to the Adaptive Form dynamically {#add-check-boxes-to-the-adaptive-form-dynamically}

You can now define rules to [add checkboxes to the Adaptive Form dynamically](../../forms/using/rule-editor.md#setpropertyrule) based on custom function, a form object, or an object property.

## AEM Workflows {#aem-workflows}

### Use variables in AEM Workflows {#use-variables-in-aem-workflows}

Variables enable workflow steps to hold and pass metadata across workflow steps at runtime. You can create different types of variables for storing different types of data. For example, integers, strings, documents, or form data model instances. Typically, you use a variable or a collection of variables when you need to make a decision based on the value that it holds or to store information that you need later in a process.

Variables are an extension of [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface available in the previous version. It helps save time spent in developing custom ECMAScript code used to retrieve and update metadata values. You continue using MetaDataMap interface and ECMAScript code to manipulate metadata. Some benefits of using variables over MetaDataMap and ECMAScript are:

* Dynamically store, update, and use values stored in a variable across the workflow without relying on custom code
* Retrieve and update values directly to a form data model and data file (XML/JSON ) of a submitted form
* Store complete documents in a variable to perform document processing

The Go To step, OR Split step, and all AEM Forms workflow steps support variables. You can use MetaDataMap interface to access variables in workflow steps that do not have a native support for variables. For more information, see [Variables in AEM Workflows](../../forms/using/variable-in-aem-workflows.md).

![Setting a variable for in a workflow](assets/variable.png)

#### Use a workflow with different Adaptive Forms  {#use-a-workflow-with-different-adaptive-forms}

You can [specify an Adaptive Form for the assign task](../../forms/using/aem-forms-workflow-step-reference.md#assign-task-step) and document of record step of form-centric workflows on the runtime. It allows a workflow to work with different Adaptive Forms. You can decide the method to select an Adaptive Form while designing the workflow. The Adaptive Form can be located at an absolute path, submitted as payload to the workflow, or available at a path calculated using a variable.

#### Use enhanced logging capabilities of forms-centric workflow steps {#use-enhanced-logging-capabilities-of-forms-centric-workflow-steps}

Logging capabilities of forms-centric workflow steps are standardized. Now, all form-centric workflow steps produce similarly standardized logs. It helps improve debugging speed.

## Data Integration {#data-integration}

You can now:

* [Validate input data](../../forms/using/work-with-form-data-model.md#automated-validation-of-input-data) based on a list of constraints. It helps ensure that only valid data is submitted to data source.
* [Override default endpoint](../../forms/using/configure-data-sources.md#configure-soap-web-services) defined in a WSDL (Web Services Description Language) file.

* [Override default](../../forms/using/configure-data-sources.md#configure-restful-web-services) [scheme, host, and base path](../../forms/using/configure-data-sources.md#configure-restful-web-services) defined in Swagger definition file.

## Platform and Security updates {#platform-and-security-updates}

### Major platform updates {#major-platform-updates}

AEM Forms can be set up using any combination of supported operating systems, application servers, databases, database drivers, JDK, LDAP servers, and email servers. The following are the major changes in [supported platforms](../../forms/using/aem-forms-jee-supported-platforms.md):

<table>
 <tbody>
  <tr>
   <td>Component</td>
   <td>Support Removed</td>
  </tr>
  <tr>
   <td>Operating systems</td>
   <td>
    <ul>
     <li>Microsoft Windows Server 2012 R2</li>
     <li>IBM AIX*</li>
     <li>Sun Solaris*</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Application servers<br /> </td>
   <td>
    <ul>
    <li>WebSphere Liberty profile</li>
    <li>Oracle WebLogic</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Databases</td>
   <td>
    <ul>
     <li>IBM DB2 <br /> </li>
     <li>Oracle RAC</li>
    </ul> </td>
  </tr>
  <tr>
   <td>LDAP servers</td>
   <td>
    <ul>
     <li>Microsoft Active Directory 2012</li>
     <li>Novell eDirectory 8.8.7 </li>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Email servers</td>
   <td>
    <ul>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Connectors</td>
   <td>
    <ul>
     <li>Connector for Microsoft Sharepoint 2013</li>
     <li>Connector for EMC Documentum 7.0</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Forms app<br /> </td>
   <td>
    <ul>
     <li>Windows 8.1 support</li>
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

&#42; Contact Adobe Support for information on migrating to a different platform

#### New HTML5-based UIs {#new-html-based-uis}

In line with planned EOL of Adobe Flash Player and overall direction of migrating Flash-based content to open standards, AEM 6.5 Forms has replaced Flash-based UI of Health Monitor, Process Management, Reader Extension, and Category Management UI of AEM Forms on JEE Administration Console with HTML5-based UI.

#### Security improvements {#security-improvements}

* AEM 6.5 Forms on JEE administration console UI is now based on Apache Struts 2.5.
* AEM 6.5 Forms now uses jQuery to 3.2.1 and jQuery UI 1.12.1. See, [upgrade documentation](/help/forms/home.md) for the impact of the change.

#### Accessibility improvements {#accessibility-improvements}

AEM 6.5 Forms has improved accessibility of AEM Forms Workspace. 
!-->

