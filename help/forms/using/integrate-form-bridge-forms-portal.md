---
title: Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare
seo-title: Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare
description: Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu versenden.
seo-description: Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu versenden.
uuid: c8911f82-1a25-47a5-9a06-19b5dce74a2c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bd9bf095-d74d-458c-afe7-fab04050849d
docset: aem65
translation-type: tm+mt
source-git-commit: 19299fb5fc764d0e71c0ea3a5ec2286183dd6861

---


# Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare{#integrating-form-bridge-with-custom-portal-for-html-forms}

FormBridge ist eine Brücken-API für HTML5-Formulare, die es Ihnen ermöglicht, mit einem Formular zu interagieren. For the FormBridge API reference, see [FormBridge API reference](/help/forms/using/form-bridge-apis.md).

Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu versenden. Beispielsweise können Sie die API verwenden, um eine assistentenähnliche Erfahrung zu erstellen.

Eine vorhandene HTML-Anwendung kann die FormBridge-API nutzen, um mit einem Formular zu interagieren und es in die HTML-Seite einzubetten. Sie können folgende Schritte verwenden, um den Wert eines Felds mithilfe der Form Bridge-API festzulegen.

## Integrieren von HTML5-Formularen in eine Webseite {#integrating-html-forms-to-a-web-page}

1. **Wählen oder erstellen Sie ein Profil.**

   1. Navigieren Sie in der CRX DE-Schnittstelle zu: `https://[server]:[port]/crx/de`.
   1. Melden Sie sich mit Administratorberechtigungen an.
   1. Erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil aus.

      For details on how to create a profile, see [Creating a new Profile](/help/forms/using/custom-profile.md).

1. **Ändern Sie das HTML-Profil**

   Schließen Sie die XFA-Laufzeitumgebung, die XFA-Gebietsschemabibliothek und das XFA-Form-HTML-Fragment im Profil-Renderer ein, entwerfen Sie Ihre Webseite und platzieren Sie das Formular darauf.

   Verwenden Sie beispielsweise das folgende Codefragment, um eine App mit zwei Eingabefeldern und einem Formular zu erstellen, um die Interaktion zwischen dem Formular und einer externen App zu demonstrieren.

   ```xml
   <%@ page session="false"
                  contentType="text/html; charset=utf-8"%><%
   %><%@ taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
   %><!DOCTYPE html>
   <html manifest="${param.offlineSpec}">
       <head>
          <cq:include script="formRuntime.jsp"/>
           <!-- Portal Scripts and Styles -->
          <cq:include script="portalheader.jsp"/>
       </head>
       <body>
           <div id="leftdiv" >
               <div id="leftdivcontentarea">
                   <!-- Portal Body -->
                 <cq:include script="portalbody.jsp"/>
               </div>
           </div>
           <div id="rightdiv">
               <div id="formBody">
               <cq:include script="config.jsp"/>
               <!-- Form body -->
               <cq:include script="formBody.jsp"/>
               <!  --To assist in page transitions -- add navigation, based on scrolling -->
               <cq:include  script="../nav/scroll/nav_footer.jsp"/>
               <cq:include script="footer.jsp"/>
               </div>
           </div>
       </body>
   </html>
   ```

   >[!NOTE]
   >
   >The **line 9**, contains additional JSP reference for CSS styles and JavaScript files to design the page.
   >
   >
   >Das Tag &lt;div id=&quot;rightdiv&quot;> in **Zeile 18** bezeichnet das HTML-Fragment des XFA-Formulars.
   Die Seite wird in zwei Container unterteilt: **links** und **rechts**. Der rechte Container enthält das Formular. Der linke Container enthält zwei Eingabefelder und einen Teil der externen HTML-Seite.
   Der folgende Screenshot zeigt, wie das Formular in einem Browser erscheint.

   ![Portal](assets/portal.jpg)

   Die linke Seite ist Teil der **HTML-Seite**. Die rechte Seite, die die Felder enthält, ist das **XFA-Formular**.

1. **Zugriff auf die Formularfelder auf der Seite**

   Nachstehend finden Sie ein Beispielskript, das Sie hinzufügen können, um Werte in einem Formularfeld festzulegen.

   For example, if you want to set the **EmployeeName** using the values in the Fields **First Name** and **Last Name**, call the **window.formBridge.setFieldValue** function.

   Similarly, you can read the value by calling **window.formBridge.getFieldValue** API.

   ```javascript
   $(function() {
               $(".input").blur(function() {
                   window.formBridge.setFieldValue(
                               'xfa.form.form1.#subform[0].EmployeeName',
                                $("#lname").val()+' '+$("#fname").val()
                              )
                   });
           });
   ```

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
