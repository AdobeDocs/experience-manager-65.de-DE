---
title: Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare
description: Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular abzusenden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: Mobile Forms
exl-id: 89118bb8-6ec8-4048-b3d6-5c73a9eea33e
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 91%

---

# Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare{#integrating-form-bridge-with-custom-portal-for-html-forms}

FormBridge ist eine Brücken-API für HTML5-Formulare, die es Ihnen ermöglicht, mit einem Formular zu interagieren. Die FormBridge-API-Referenz finden Sie unter [FormBridge-API-Referenz](/help/forms/using/form-bridge-apis.md).

Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular abzusenden. Beispielsweise können Sie die API verwenden, um eine assistentenähnliche Erfahrung zu erstellen.

Eine bestehende HTML-Anwendung kann die FormBridge-API verwenden, um mit einem Formular zu interagieren und es in die HTML-Seite einzubetten. Sie können folgende Schritte verwenden, um den Wert eines Felds mithilfe der Form Bridge-API festzulegen.

## Integrieren von HTML5-Formularen in eine Web-Seite {#integrating-html-forms-to-a-web-page}

1. **Wählen oder erstellen Sie ein Profil.**

   1. Navigieren Sie in der CRX DE-Benutzeroberfläche zu `https://'[server]:[port]'/crx/de`.
   1. Melden Sie sich mit Administratorberechtigungen an.
   1. Erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil aus.

      Weitere Informationen zum Erstellen eines Profils finden Sie unter [Erstellen eines Profils](/help/forms/using/custom-profile.md).

1. **Ändern Sie das HTML-Profil**

   Schließen Sie die XFA-Laufzeitumgebung, die XFA-Gebietsschemabibliothek und das XFA-Form-HTML-Fragment im Profil-Renderer ein, entwerfen Sie Ihre Web-Seite und platzieren Sie das Formular darauf.

   Verwenden Sie beispielsweise das folgende Code-Fragment, um eine App mit zwei Eingabefeldern und einem Formular zu erstellen, um die Interaktion zwischen dem Formular und einer externen App zu demonstrieren.

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
   >In **Zeile 9** befinden sich zusätzliche JSP-Verweise für CSS-Stile und JavaScript-Dateien für das Seiten-Design.
   >
   >
   >Das Tag &lt;div id=&quot;rightdiv&quot;> in **Zeile 18** bezeichnet das HTML-Fragment des XFA-Formulars.
   >
   >
   Die Seite wird in zwei Container unterteilt: **links** und **rechts**. Der rechte Container enthält das Formular. Der linke Container enthält zwei Eingabefelder und einen Teil der externen HTML-Seite.
   >
   >
   Der folgende Screenshot zeigt, wie das Formular in einem Browser angezeigt wird.

   ![Portal](assets/portal.jpg)

   Die linke Seite ist Teil der **HTML-Seite**. Die rechte Seite, die die Felder enthält, ist das **XFA-Formular**.

1. **Zugriff auf die Formularfelder auf der Seite**

   Nachstehend finden Sie ein Beispielskript, das Sie hinzufügen können, um Werte in einem Formularfeld festzulegen.

   Wenn Sie beispielsweise den **Mitarbeiternamen** anhand der Werte in den Feldern **Vorname** und **Nachname** festlegen möchten, rufen Sie die Funktion **window.formBridge.setFieldValue** auf.

   Ebenso können Sie den Wert lesen, indem Sie die API **window.formBridge.getFieldValue** aufrufen.

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
