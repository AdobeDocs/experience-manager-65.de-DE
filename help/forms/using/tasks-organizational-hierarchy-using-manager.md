---
title: Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manager-Ansicht
description: Wie Führungskräfte und Unternehmensleitungen auf der Registerkarte „Aufgaben“ in AEM Forms Workspace auf die Aufgaben ihrer direkt und indirekt unterstellten Mitarbeiterinnen und Mitarbeiter zugreifen und sie verwenden können.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: e50974a7-01ac-4a08-bea2-df9cc975c69e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 100%

---

# Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manager-Ansicht{#managing-tasks-in-an-organizational-hierarchy-using-manager-view}

In AEM Forms Workspace können Manager jetzt auf die Aufgaben zugreifen, die Benutzern in ihren Hierarchien – direkt oder indirekt unterstellten Mitarbeitern – zugewiesen sind, und dafür verschiedene Aktionen ausführen. Die Aufgaben sind in AEM Forms Workspace auf der Registerkarte „Aufgaben“ verfügbar. Die folgenden Aktionen werden für die Aufgaben von direkt unterstellten Mitarbeiterinnen und Mitarbeitern unterstützt:

**Weiterleiten** – Leitet eine Aufgabe von direkt unterstellten Mitarbeiterinnen und Mitarbeitern an eine beliebige Benutzerin oder einen beliebigen Benutzer weiter.

**Anfordern** – Fordert eine Aufgabe von direkt unterstellten Mitarbeiterinnen und Mitarbeitern an.

**Anfordern und öffnen** Fordert eine Aufgabe von direkt unterstellten Mitarbeiterinnen und Mitarbeitern an und öffnet sie automatisch in der Aufgabenliste der Führungskraft.

**Ablehnen** Lehnt eine Aufgabe ab, die von einer anderen Benutzerin oder einem anderen Benutzer an eine direkt unterstellte Person weitergeleitet wurde. Diese Option ist für die Aufgaben verfügbar, die von anderen Benutzern an einen direkt unterstellten Mitarbeiter weitergeleitet wurden.

AEM Forms beschränkt den Zugriff eines Benutzers auf die Aufgaben, für die der Benutzer die Zugriffskontrolle (ACL) hat. Durch diese Überprüfung wird sichergestellt, dass Benutzende nur die Aufgaben abrufen können, für die sie Zugriffsberechtigungen haben. Ein Unternehmen kann die Hierarchie mit Web-Diensten von Drittanbietern definieren und die Definition von Führungskräften und direkt unterstellten Mitarbeiterinnen und Mitarbeitern an ihren Bedarf anpassen.

1. Erstellen Sie einen DSC. Weitere Informationen erhalten Sie unter „Entwickeln von Komponenten für AEM Forms“ im Handbuch [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).
1. Definieren Sie in dem DSC eine neue SPI für das Hierarchiemanagement, um direkt unterstellte Mitarbeiter und Hierarchie unter den AEM Forms-Benutzern zu definieren. Im Folgenden finden Sie ein Java™-Beispiel-Code-Fragment.

   ```java
   public class MyHierarchyMgmtService
   {
        /*
       Input : Principal Oid for a livecycle user
       Output : Returns true when the user is either the service invoker OR his direct/indirect report.
       */
       boolean isInHierarchy(String principalOid) {
   
       }
   
       /*
       Input : Principal Oid for a livecycle user
       Output : List of principal Oids for direct reports of the livecycle user
       A user may get direct reports only for himself OR his direct/indirect reports.
       So the API is functionally equivalent to -
       isInHierarchy(principalOid) ? <return direct reports> : <return empty list>
       */
       List<String> getDirectReports(String principalOid) {
   
       }
   
       /*
       Returns whether a livecycle user has direct reports or not.
       It is functionally equivalent to -
       getDirectReports(principalOid).size()>0
       */
       boolean isManager(String principalOid) {
   
       }
   }
   ```

1. Erstellen Sie die Datei „component.xml“. Stellen Sie sicher, dass spec-id mit dem unten angegebenen Code-Fragment übereinstimmt. Im Folgenden finden Sie ein Beispiel-Code-Fragment, das Sie für Ihre Zwecke anpassen können.

   ```xml
   <component xmlns="https://adobe.com/idp/dsc/component/document">
       <component-id>com.adobe.sample.SampleDSC</component-id>
       <version>1.1</version>
       <supports-export>false</supports-export>
         <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class>
         <services>
           <service name="MyHierarchyMgmtService" title="My hierarchy management service" orchestrateable="false">
           <auto-deploy service-id="MyHierarchyMgmtService" category-id="Sample DSC" major-version="1" minor-version="0" />
           <description>Service for resolving hierarchy management.</description>
            <specifications>
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.HierarchyManagementProvider"/>
            </specifications>
           <specification-version>1.0</specification-version>
           <implementation-class>com.adobe.sample.hierarchymanagement.MyHierarchyMgmtService</implementation-class>
           <request-processing-strategy>single_instance</request-processing-strategy>
           <supported-connectors>default</supported-connectors>
           <operation-config>
               <operation-name>*</operation-name>
               <transaction-type>Container</transaction-type>
               <transaction-propagation>supports</transaction-propagation>
               <!--transaction-timeout>3000</transaction-timeout-->
           </operation-config>
           <operations>
               <operation anonymous-access="true" name="isInHierarchy" method="isInHierarchy">
                   <input-parameter name="principalOid" type="java.lang.String" />
                   <output-parameter name="result" type="java.lang.Boolean"/>
               </operation>
               <operation anonymous-access="true" name="getDirectReports" method="getDirectReports">
                   <input-parameter name="principalOid" type="java.lang.String" />
                   <output-parameter name="result" type="java.util.List"/>
               </operation>
               <operation anonymous-access="true" name="isManager" method="isManager">
                   <input-parameter name="principalOid" type="java.lang.String" />
                   <output-parameter name="result" type="java.lang.Boolean"/>
               </operation>
               </operations>
               </service>
         </services>
   </component>
   ```

1. Stellen Sie das DSC über Workbench bereit. Starten Sie den Service `ProcessManagementTeamTasksService` neu.
1. Möglicherweise müssen Sie den Browser aktualisieren oder sich für den Benutzer erneut abmelden/anmelden.

Der folgende Bildschirm veranschaulicht den Zugriff auf die Aufgaben direkt unterstellter Mitarbeiterinnen und Mitarbeiter und die verfügbaren Aktionen.

![cu_manager_view](assets/cu_manager_view.png)

Zugreifen auf Aufgaben direkt unterstellter Mitarbeiter und Ausführen von Aktionen für die Aufgaben
