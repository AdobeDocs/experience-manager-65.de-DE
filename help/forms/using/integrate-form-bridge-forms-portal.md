---
title: Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare
seo-title: Integrating Form Bridge with custom portal for HTML5 forms
description: Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu senden.
seo-description: You can use the FormBridge API to get or set the values of form fields from the HTML page and submit the form.
uuid: c8911f82-1a25-47a5-9a06-19b5dce74a2c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bd9bf095-d74d-458c-afe7-fab04050849d
docset: aem65
feature: Mobile Forms
exl-id: 89118bb8-6ec8-4048-b3d6-5c73a9eea33e
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 23%

---

# Integrieren von Form Bridge in das benutzerdefinierte Portal für HTML5-Formulare{#integrating-form-bridge-with-custom-portal-for-html-forms}

FormBridge ist eine HTML5 Forms Bridge-API, mit der Sie mit einem Formular interagieren können. Die FormBridge-API-Referenz finden Sie unter [FormBridge-API-Referenz](/help/forms/using/form-bridge-apis.md).

Sie können die FormBridge-API verwenden, um die Werte von Formularfeldern von der HTML-Seite abzurufen oder festzulegen und das Formular zu senden. Sie können beispielsweise die API verwenden, um ein assistentenähnliches Erlebnis zu erstellen.

Eine bestehende HTML-Anwendung kann die FormBridge-API verwenden, um mit einem Formular zu interagieren und es in die HTML-Seite einzubetten. Sie können die folgenden Schritte ausführen, um den Wert eines Felds mithilfe der Form Bridge-API festzulegen.

## Integrieren von HTML5-Formularen in eine Webseite {#integrating-html-forms-to-a-web-page}

1. **Wählen oder erstellen Sie ein Profil.**

   1. Navigieren Sie in der CRX DE-Benutzeroberfläche zu `https://'[server]:[port]'/crx/de`.
   1. Melden Sie sich mit Administratorberechtigungen an.
   1. Erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil aus.

      Weitere Informationen zum Erstellen eines Profils finden Sie unter [Erstellen eines Profils](/help/forms/using/custom-profile.md).

1. **Ändern des HTML-Profils**

   Schließen Sie die XFA-Laufzeitumgebung, die XFA-Gebietsschema-Bibliothek und das XFA-Formular-HTML-Snippet in den Profil-Renderer ein, entwerfen Sie Ihre Webseite und platzieren Sie das Formular auf der Webseite.

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
   >In **Zeile 9** befinden sich zusätzliche JSP-Verweise für CSS-Stile und JavaScript-Dateien für das Seiten-Design.
   >
   >
   >Die &lt;div id=&quot;rightdiv&quot;> Tag auf **Zeile 18** enthält das HTML-Fragment des XFA-Formulars.
   >
   >
   Die Seite ist in zwei Container formatiert: **left** und **right**. Der rechte Container enthält das Formular. Der linke Container enthält zwei Eingabefelder und einen Teil der externen HTML-Seite.
   >
   >
   Der folgende Screenshot zeigt, wie das Formular in einem Browser angezeigt wird.

   ![Portal](assets/portal.jpg)

   Die linke Seite ist Teil der **HTML Seite**. Die rechte Seite, die die Felder enthält, ist die **xfa form**.

1. **Zugriff auf die Formularfelder von der Seite aus**

   Im Folgenden finden Sie ein Beispielskript, das Sie hinzufügen können, um Werte in einem Formularfeld festzulegen.

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
