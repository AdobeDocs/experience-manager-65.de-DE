---
title: Wiedergabe von Formularen
seo-title: Wiedergabe von Formularen
description: 'null'
seo-description: 'null'
uuid: 68d7b7bc-7730-4a83-b7b9-ebe2a29d6c51
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8749793-e53f-4812-a093-8278f480e6a8
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 1%

---


# Wiedergabe von Formularen {#rendering-forms}

**Info zum Forms-Dienst**

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen für die Datenerfassung erstellen, mit denen in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Formularersteller können einen einzelnen Formularentwurf entwickeln, den der Forms-Dienst in verschiedenen Browser-Umgebung in PDF, SWF oder HTML wiedergibt.

Wenn ein Endbenutzer ein Formular anfordert, sendet eine Clientanwendung die Anforderung an den Forms-Dienst, der das Formular in einem geeigneten Format zurückgibt. Sobald der Forms-Dienst eine Anforderung erhält, werden Daten mit einem Formularentwurf zusammengeführt und das Formular dann im gewünschten Format bereitgestellt. Die Formulardienstausgabe ist ein interaktives Formular, normalerweise ein PDF-Dokument. Mit einem interaktiven Formular können Benutzer Felder im Formular ausfüllen.

Je nach Typ der Clientanwendung können Sie das Formular in einen Client-Webbrowser schreiben oder als PDF-Datei speichern. Eine webbasierte Anwendung kann das Formular in einen Webbrowser schreiben. Eine Desktopanwendung kann das Formular als PDF-Datei speichern. Um zu veranschaulichen, wie das Schreiben an einen Webbrowser und an eine PDF-Datei erfolgt, werden die Beginn im Abschnitt &quot; *Wiedergabeformulare* &quot;wie folgt organisiert:

* Die stark typisierten Java-API-Beispiele (SOAP-Modus) sind ein Java-Servlet.
* Die Beispiele für den Webdienst (Java Base64) sind ein Java-Servlet.
* Die Beispiele für den Webdienst (MTOM) sind eine Konsolenanwendung (nicht alle Quick Beginn haben ein MTOM-Beispiel).

>[!NOTE]
>
>Weitere Informationen zum Erstellen einer Webanwendung, die Java-Servlets zum Aufrufen des Forms-Dienstes verwendet, finden Sie unter [Erstellen von Webanwendungen, die Forms](/help/forms/developing/creating-web-applications-renders-forms.md)rendern.

Sie können einen Formularentwurf (eine XDP-Datei) oder ein PDF-Dokument auf zwei Arten an den Forms-Dienst übergeben:

* Sie können den Formularentwurf mit einem URL-Wert referenzieren. Dieser Ansatz umfasst die Verwendung eines `URLSpec` Objekts. Der Inhaltsstamm wird mithilfe der `URLSpec` Methode des `setContentRootURI` Objekts an den Forms-Dienst übergeben. Der Name des Formularentwurfs ( `formQuery`) wird als separater Parameter übergeben. Die beiden Werte werden verkettet, um den absoluten Verweis auf den Formularentwurf zu erhalten. (Die meisten schnellen Beginn im Abschnitt *Wiedergabeformulare* verwenden diesen Ansatz.)
* Sie können einen Formularentwurf `com.adobe.idp.Document` an den Forms-Dienst übergeben. Zwei neue Methoden mit dem Namen `renderPDFForm2` und `renderHTMLForm2` der Annahme eines `com.adobe.idp.Document` Objekts, das einen Formularentwurf enthält. (Siehe [Übergeben von Dokumenten an den Forms-Dienst.)](/help/forms/developing/passing-documents-forms-service.md)

Sie können diese Aufgaben mithilfe des Forms-Dienstes ausführen:

* Interaktive PDF forms wiedergeben (Siehe [Rendern von interaktiven PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Wiedergabe von Formularen auf dem Client. (Siehe [Wiedergabe von Formularen auf dem Client](/help/forms/developing/rendering-forms-client.md).)
* Wiedergabe von Formularen basierend auf Fragmenten (See [Rendering Forms Based on Fragments](/help/forms/developing/rendering-forms-based-fragments.md).)
* Wiedergabe von Formularen mit aktivierten Verwendungsrechten. (Siehe [Wiedergabe von Formularen](/help/forms/developing/rendering-rights-enabled-forms.md)mit aktivierten Rechten.)
* Wiedergabe von Formularen als HTML (Siehe [Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)
* Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien ([Wiedergabe von HTML-Formularen mit benutzerdefinierten CSS-Dateien](/help/forms/developing/rendering-html-forms-using-custom.md))
* Verarbeiten Sie gesendete Formulare. (Siehe [Verarbeiten gesendeter Formulare](/help/forms/developing/handling-submitted-forms.md).)
* Erstellen von PDF-Dokumenten mit gesendeten XML-Daten. (Siehe [Erstellen von PDF-Dokumenten mit gesendeten XML-Daten](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Formulare im Voraus ausfüllen. (Siehe [Vorausfüllen von Formularen mit flexiblen Layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Übergeben von Dokumenten. (Siehe [Übergeben von Dokumenten an den Forms-Dienst.)](/help/forms/developing/passing-documents-forms-service.md)
* Berechnen von Formulardaten. (Siehe [Berechnen von Formulardaten](/help/forms/developing/calculating-form-data.md).)
* Optimieren Sie eine Anwendung. (Siehe [Optimieren der Leistung des Forms-Dienstes](/help/forms/developing/optimizing-performance-forms-service.md).)

   ***Tipp **: Die Adobe Developer-Website enthält den folgenden Artikel, in dem erläutert wird, wie eine ASP.NET-Anwendung erstellt wird, die den Forms-Dienst aufruft und Formulare wiedergibt. Siehe[Erstellen von ASP.NET-Formularen](https://www.adobe.com/devnet/livecycle/articles/asp_net.html).*

