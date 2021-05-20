---
title: Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manageransicht
seo-title: Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manageransicht
description: Wie Manager und Unternehmensleitungen auf die Aufgaben ihrer direkt oder indirekt unterstellten Mitarbeiter in der Registerkarte „Aufgaben“ in AEM Forms Workspace zugreifen und sie verwenden können.
seo-description: Wie Manager und Unternehmensleitungen auf die Aufgaben ihrer direkt oder indirekt unterstellten Mitarbeiter in der Registerkarte „Aufgaben“ in AEM Forms Workspace zugreifen und sie verwenden können.
uuid: c44c55e6-6cc1-417d-8e89-c8d5c32914c8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2e60df86-d8ff-4cf9-b801-9559857b5ff4
docset: aem65
exl-id: e50974a7-01ac-4a08-bea2-df9cc975c69e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 79%

---

# Verwalten von Aufgaben in einer hierarchischen Struktur mithilfe der Manageransicht{#managing-tasks-in-an-organizational-hierarchy-using-manager-view}

In AEM Forms Workspace können Manager jetzt auf die Aufgaben zugreifen, die Benutzern in ihren Hierarchien – direkt oder indirekt unterstellten Mitarbeitern – zugewiesen sind, und dafür verschiedene Aktionen ausführen. Die Aufgaben sind in AEM Forms Workspace auf der Registerkarte „Aufgaben“ verfügbar. Die folgenden Aktionen werden für die Aufgaben direkt unterstellter Mitarbeiter unterstützt:

**** Weiterleiten einer Aufgabe vom direkten Bericht an einen beliebigen Benutzer.

**** Fordert eine Aufgabe eines direkt unterstellten Mitarbeiters an.

**Anfordern und** ÖffnenFordert eine Aufgabe eines direkt unterstellten Mitarbeiters an und öffnet sie automatisch in der Aufgabenliste des Managers.

**** RejectRejectRejectRejectRejectEine Aufgabe, die von einem anderen Benutzer an einen direkten Bericht weitergeleitet wird. Diese Option ist für die Aufgaben verfügbar, die von anderen Benutzern an einen direkt unterstellten Mitarbeiter weitergeleitet wurden.

AEM Forms beschränkt den Zugriff eines Benutzers auf die Aufgaben, für die der Benutzer die Zugriffskontrolle (ACL) hat. Durch diese Überprüfung wird sichergestellt, dass ein Benutzer nur die Aufgaben abrufen kann, für die er Zugriffsberechtigungen hat. Eine Organisation kann die Hierarchie mit Webdiensten von Drittanbietern definieren und die Definition von Managern und direkt unterstellten Mitarbeitern an ihren Bedarf anpassen.

1. Erstellen Sie ein DSC. Weitere Informationen finden Sie unter &quot;Entwickeln von Komponenten für AEM Forms&quot;im Handbuch [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).
1. Definieren Sie in dem DSC eine neue SPI für das Hierarchiemanagement, um direkt unterstellte Mitarbeiter und Hierarchie unter den AEM Forms-Benutzern zu definieren. Im Folgenden finden Sie ein Java™-Beispielcodefragment.

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
       It's functionally equivalent to -
       getDirectReports(principalOid).size()>0
       */
       boolean isManager(String principalOid) {
   
       }
   }
   ```

1. Erstellen Sie die Datei component.xml. Stellen Sie sicher, dass spec-id mit dem unten angegebenen Codefragment bereinstimmt. Im Folgenden finden Sie ein Beispielcodefragment, das Sie für Ihre Zwecke anpassen können.

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

1. Stellen Sie das DSC über Workbench bereit. Starten Sie den Dienst `ProcessManagementTeamTasksService` neu.
1. Möglicherweise müssen Sie den Browser aktualisieren oder sich für den Benutzer erneut abmelden/anmelden.

Der folgende Bildschirm veranschaulicht den Zugriff auf die Aufgaben direkt unterstellter Mitarbeiter und die verfügbaren Aktionen.

![cu_manager_view](assets/cu_manager_view.png)

Zugreifen auf Aufgaben direkt unterstellter Mitarbeiter und Ausführen von Aktionen für die Aufgaben
