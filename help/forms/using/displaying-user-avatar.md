---
title: Anzeigen des Benutzeravatars
seo-title: Anzeigen des Benutzeravatars
description: Anpassen von AEM Forms Workspace, um das Bild eines angemeldeten Benutzers anzuzeigen.
seo-description: Anpassen von AEM Forms Workspace, um das Bild eines angemeldeten Benutzers anzuzeigen.
uuid: 2961dc93-f0d0-4842-80f1-3c239a20e348
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: aec03ea5-17a6-4775-92cb-2ad361895fdf
exl-id: ee0708b0-b630-4a2b-84b6-3c0b92dd7777
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 80%

---

# Anzeigen des Benutzeravatars {#displaying-the-user-avatar}

Der Avatar des angemeldeten Benutzers wird in der oberen rechten Ecke von AEM Forms Workspace angezeigt. Auch die Avatare von direkten Berichten in der hierarchischen Struktur werden in der Manageransicht angezeigt. Sie können AEM Forms Workspace so konfigurieren, dass die Benutzerbilder aus Ihrer Datenbank, z. B. vom LDAP-Server, ausgewählt werden.

>[!NOTE]
>
>Für Benutzerbilder wird nur das Seitenverhältnis 1:1 unterstützt.

1. Erstellen Sie ein DSC mithilfe der Informationen, die im nächsten Schritt angegeben werden. Weitere Informationen finden Sie unter &quot;Entwickeln von Komponenten für AEM Forms&quot;im Handbuch [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).
1. Definieren Sie im DSC eine neue SPI, die mithilfe der Methoden getCurrentUserImageUrl und getUserImageUrl eine Bild-URL für einen AEM Forms-Benutzer abruft. Im Folgenden finden Sie ein Java™-Beispielcodefragment:

   ```java
   public class DemoUserImageURLProviderService {
     public String getCurrentUserImageUrl()
     {
        // return the URL for profile Image of logged in user
     }
     public String getUserImageUrl(String principalOid)
     {
         // return the URL for profile Image for user represented by this principal Oid
      }
   }
   ```

1. Erstellen Sie die Datei component.xml. Stellen Sie sicher, dass spec-id wie im unten gezeigten Codefragment lautet.

   Das folgende Codefragment ist ein Beispiel. Passen Sie es an Ihre spezifischen Anforderungen an.

   ```java
   <component xmlns="https://adobe.com/idp/dsc/component/document">
       <component-id>com.adobe.sample.DemoUsersComponent</component-id>
       <version>1.1</version>
       <supports-export>false</supports-export>
       <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class>
       <services>
           <service name="DemoUserImageURLProviderService" title="Demo User ImageURL provider service" orchestrateable="false">
           <auto-deploy service-id="DemoUserImageURLProviderService" category-id="Demo Users Component DSC" major-version="1" minor-version="0" />
           <description>Service for resolving user image url.</description>
            <specifications>
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.UserImageUrlProvider"/>
            </specifications>
           <specification-version>1.0</specification-version>
           <implementation-class>com.adobe.sample.demousers.DemoUserImageURLProviderService</implementation-class>
           <request-processing-strategy>single_instance</request-processing-strategy>
           <supported-connectors>default</supported-connectors>
           <operation-config>
               <operation-name>*</operation-name>
               <transaction-type>Container</transaction-type>
               <transaction-propagation>supports</transaction-propagation>
               <!--transaction-timeout>3000</transaction-timeout-->
           </operation-config>
           <operations>
               <operation anonymous-access="false" name="getCurrentUserImageUrl" method="getCurrentUserImageUrl">
                   <output-parameter name="result" type="java.lang.String"/>
               </operation>
               <operation anonymous-access="false" name="getUserImageUrl"
   method="getUserImageUrl">
               <input-parameter name="principalOid" type="java.lang.String"/>
               <output-parameter name="result" type="java.lang.String"/>
               </operation>
           </operations>
           </service>
       </services>
   </component>
   ```

1. Stellen Sie das DSC über Workbench bereit. Starten Sie den Dienst `ProcessManagementClientSessionService` neu.
1. Möglicherweise müssen Sie den Browser aktualisieren oder sich für den Benutzer erneut abmelden/anmelden.
