---
title: '"Tutorial: Testen des adaptiven Formulars"'
seo-title: '"Tutorial: Testen des adaptiven Formulars"'
description: Verwenden Sie automatisierte Tests, um mehrere adaptive Formulare gleichzeitig zu testen.
seo-description: Verwenden Sie automatisierte Tests, um mehrere adaptive Formulare gleichzeitig zu testen.
uuid: 6d182bbc-b47a-4c97-af70-c960b52fdfac
contentOwner: khsingh
discoiquuid: ecddb22e-c148-441f-9088-2e5b35c7021b
docset: aem65
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 12%

---


# Übung: Testen des adaptiven Formulars {#tutorial-testing-your-adaptive-form}

![](do-not-localize/10-test-your-adaptive-form.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Nachdem das adaptive Formular fertig ist, müssen Sie das adaptive Formular testen, bevor Sie es an die Endbenutzer übertragen. Sie können jedes Feld manuell testen (funktionelle Tests) oder das Testen des adaptiven Formulars automatisieren. Wenn Sie mehrere adaptive Formulare haben, wird das manuelle Testen aller Felder der adaptiven Formulare zu einer beängstigenden Aufgabe.

AEM [!DNL Forms] stellen Sie ein Testframework bereit, Calvin, um das Testen Ihrer adaptiven Formulare zu automatisieren. Mit diesem Framework können Sie Tests der Benutzeroberfläche direkt in einem Webbrowser schreiben und ausführen. Das Framework stellt JavaScript-APIs zum Erstellen von Tests bereit. Mit dem automatisierten Test können Sie das Erlebnis zum Vorausfüllen eines adaptiven Formulars testen, die Sendeerfahrung eines adaptiven Formulars, die Regeln für den Ausdruck von Überprüfungen, verzögertes Laden und Benutzeroberflächeninteraktionen testen. Dieses Lernprogramm führt Sie durch die Schritte zum Erstellen und Ausführen automatisierter Tests für ein adaptives Formular. Am Ende dieser Schulung können Sie Folgendes:

* [Testsuite für Ihr adaptives Formular erstellen](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-suite)
* [Erstellen von Tests für Ihr adaptives Formular](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-case-to-prefill-values-in-an-adaptive-form)
* [Testsuite und für Ihr adaptives Formular erstellte Tests ausführen](#step-run-all-the-tests-in-a-suite-or-individual-tests-cases)

## Schritt 1: Testsuite {#step-create-a-test-suite} erstellen

Test Suites verfügen über eine Reihe von Testfällen. Sie können über mehrere Testsuiten verfügen. Es wird empfohlen, für jedes Formular eine separate Testsuite zu verwenden. So erstellen Sie eine Test-Suite:

1. Melden Sie sich bei AEM [!DNL Forms] Autoreninstanz als Administrator an. Öffnen Sie [!UICONTROL CRXDE Lite]. Sie können AEM Logo > **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]** oder die [https://localhost:4502/crx/de/index.jsp](https://localhost:4502/crx/de/index.jsp)-URL in einem Browser öffnen, um die CRXDE Lite zu öffnen.

1. Navigieren Sie zu /etc/clientlibs in [!UICONTROL CRXDE Lite]. Klicken Sie mit der rechten Maustaste auf den Unterordner /etc/clientlibs und dann auf **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**. Geben Sie im Feld **[!UICONTROL Name]** **WeRetailFormTestCases** ein. Wählen Sie den Typ **cq:ClientLibraryFolder** und klicken Sie auf **[!UICONTROL OK]**. Es wird eine Node erstellt. Sie können jeden beliebigen Namen anstelle von `WeRetailFormTestCases` verwenden.
1. hinzufügen Sie die folgenden Eigenschaften auf den Knoten `WeRetailFormTestCases` und tippen Sie auf **[!UICONTROL Save ALL]**.

   <table>
    <tbody>
     <tr>
      <td><strong>Eigenschaft</strong></td>
      <td><strong>Typ</strong></td>
      <td><strong>Multi</strong></td>
      <td><strong>Wert</strong></td>
     </tr>
     <tr>
      <td>categories</td>
      <td>Zeichenfolge</td>
      <td>Aktiviert</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.tests<br /> </li>
        <li>granite.testing.calvin.tests</li>
       </ul> </td>
     </tr>
     <tr>
      <td>dependencies</td>
      <td>Zeichenfolge</td>
      <td>Aktiviert</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.testrunner <br /> </li>
        <li>granite.testing.calvin <br /> </li>
        <li>apps.testframework.all</li>
       </ul> </td>
     </tr>
    </tbody>
   </table>

   Stellen Sie sicher, dass jede Eigenschaft wie unten dargestellt einem separaten Feld hinzugefügt wird:

   ![dependencies](assets/dependencies.png)

1. Klicken Sie mit der rechten Maustaste auf den Knoten **[!UICONTROL WeRetailFormTestCases]** und klicken Sie auf **[!UICONTROL Create]** > **[!UICONTROL Create File]**. Geben Sie im Feld **[!UICONTROL Name]** `js.txt` ein und klicken Sie auf **[!UICONTROL OK]**.
1. Öffnen Sie die Datei &quot;js.txt&quot;zur Bearbeitung, fügen Sie den folgenden Code hinzu und speichern Sie die Datei:

   ```text
   #base=.
    init.js
   ```

1. Erstellen Sie eine Datei, init.js, im Knoten `WeRetailFormTestCases`. hinzufügen Sie den folgenden Code in die Datei ein und tippen Sie auf **[!UICONTROL Alle speichern]**.

   ```javascript
   (function(window, hobs) {
       'use strict';
       window.testsuites = window.testsuites || {};
     // Registering the test form suite to the sytem
     // If there are other forms, all registration should be done here
       window.testsuites.testForm3 = new hobs.TestSuite("We retail - Tests", {
           path: '/etc/clientlibs/WeRetailFormTestCases/init.js',
           register: true
       });
    // window.testsuites.testForm2 = new hobs.TestSuite("testForm2");
   }(window, window.hobs));
   ```

   Mit dem obigen Code wird eine Testsuite mit dem Namen **Wir für den Handel - Tests** erstellt.

1. Öffnen Sie AEM Benutzeroberfläche für Tests (AEM > **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Tests]**). Die Testsuite - **Wir für den Handel - Tests** - ist in der Benutzeroberfläche aufgeführt.

   ![we-retail-test-suite](assets/we-retail-test-suite.png)

## Schritt 2: Erstellen Sie einen Testfall, um Werte in einem adaptiven Formular vorab auszufüllen. {#step-create-a-test-case-to-prefill-values-in-an-adaptive-form}

Ein Testfall ist eine Reihe von Aktionen zum Testen einer bestimmten Funktion. Beispielsweise müssen Sie alle Felder eines Formulars im Voraus ausfüllen und einige Felder überprüfen, um sicherzustellen, dass die richtigen Werte eingegeben werden.

Eine Aktion ist eine bestimmte Aktivität in einem adaptiven Formular, z. B. durch Klicken auf eine Schaltfläche. So erstellen Sie einen Testfall und Aktionen, um die Benutzereingabe für jedes adaptive Formularfeld zu überprüfen:

1. Navigieren Sie in [!UICONTROL CRXDE Lite] zum Ordner `/content/forms/af/create-first-adaptive-form`. Klicken Sie mit der rechten Maustaste auf den Ordnernamen **[!UICONTROL create-first-adaptive-form]** und klicken Sie auf **[!UICONTROL Create]** **[!UICONTROL Create File]**. Geben Sie im Feld **[!UICONTROL Name]** `prefill.xml` ein und klicken Sie auf **[!UICONTROL OK]**. Fügen Sie der Datei den folgenden Code hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?><afData>
     <afUnboundData>
       <data>
         <customer_ID>371767</customer_ID>
         <customer_Name>John Jacobs</customer_Name>
         <customer_Shipping_Address>1657 1657 Riverside Drive Redding</customer_Shipping_Address>
         <customer_State>California</customer_State>
         <customer_ZIPCode>096001</customer_ZIPCode>
        </data>
     </afUnboundData>
     <afBoundData>
       <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"/>
     </afBoundData>
   </afData>
   ```

1. Navigieren Sie zu `/etc/clientlibs`. Klicken Sie mit der rechten Maustaste auf den Unterordner `/etc/clientlibs` und klicken Sie auf **[!UICONTROL Erstellen]** **[!UICONTROL Erstellen Sie Knoten]**.

   Geben Sie im Feld **[!UICONTROL Name]** den Wert `WeRetailFormTests` ein. Wählen Sie den Typ `cq:ClientLibraryFolder` und klicken Sie auf **[!UICONTROL OK]**.

1. hinzufügen Sie die folgenden Eigenschaften auf den Knoten **[!UICONTROL WeRetailFormTests]**.

   <table>
    <tbody>
     <tr>
      <td><strong>Eigenschaft</strong></td>
      <td><strong>Typ</strong></td>
      <td><strong>Multi</strong></td>
      <td><strong>Wert</strong></td>
     </tr>
     <tr>
      <td>Kategorien</td>
      <td>Zeichenfolge</td>
      <td>Aktiviert</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.tests<br /> </li>
        <li>granite.testing.hobbes.tests.testForm</li>
       </ul> </td>
     </tr>
     <tr>
      <td>Abhängigkeiten</td>
      <td>Zeichenfolge</td>
      <td>Aktiviert</td>
      <td>
       <ul>
        <li>granite.testing.calvin.tests</li>
       </ul> </td>
     </tr>
     </tbody>
   </table>

1. Erstellen Sie die Datei &quot;js.txt&quot;im Knoten **[!UICONTROL WeRetailFormTests]**. Fügen Sie der Datei den folgenden hinzu:

   ```shell
   #base=.
   prefillTest.js
   ```

   Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Erstellen Sie eine Datei mit dem Namen `prefillTest.js` im Knoten **[!UICONTROL WeRetailFormTests]**. hinzufügen Sie den unten stehenden Code in die Datei ein. Der Code erstellt einen Testfall. Der TestCase füllt alle Felder eines Formulars im Voraus aus und überprüft einige Felder, um sicherzustellen, dass korrekte Werte eingegeben werden.

   ```javascript
   (function (window, hobs) {
       'use strict';
   
       var ts = new hobs.TestSuite("Prefill Test", {
           path: '/etc/clientlibs/WeRetailFormTests/prefillTest.js',
           register: false
       })
   
       .addTestCase(new hobs.TestCase("Prefill Test")
           // navigate to the testForm which is to be test
           .navigateTo("/content/forms/af/create-first-adaptive-form/shipping-address-add-update-form.html?wcmmode=disabled&dataRef=crx:///content/forms/af/create-first-adaptive-form/prefill.xml")
           // check if adaptive form is loaded
           .asserts.isTrue(function () {
               return calvin.isFormLoaded()
           })
           .asserts.isTrue(function () {
               return calvin.model("customer_ID").value == 371767;
           })
           .asserts.isTrue(function () {
               return calvin.model("customer_ZIPCode").value == 96001;
           })
       );
   
       // register the test suite with testForm
       window.testsuites.testForm3.add(ts);
   
   }(window, window.hobs));
   ```

   Der Testfall wird erstellt und kann ausgeführt werden. Sie können Testfälle erstellen, um verschiedene Aspekte eines adaptiven Formulars zu validieren, z. B. die Ausführung des Berechnungsskripts, die Überprüfung von Mustern und die Überprüfung der Sendeerfahrung eines adaptiven Formulars. Weitere Informationen zu verschiedenen Aspekten des Testens adaptiver Formulare finden Sie unter Automatisches Testen von adaptiven Formularen.

## Schritt 3: Führen Sie alle Tests in einer Suite oder einzelnen Testfällen aus.{#step-run-all-the-tests-in-a-suite-or-individual-tests-cases}

Eine Testsuite kann mehrere Testfälle aufweisen. Sie können alle Testfälle in einer Testsuite auf einmal oder einzeln ausführen. Wenn Sie einen Test durchführen, werden die Ergebnisse durch die Symbole angezeigt:

* Ein Häkchen-Symbol zeigt an, dass ein Test bestanden hat: ![save_icon](assets/save_icon.svg)
* Ein X-Symbol weist auf einen fehlgeschlagenen Test hin: ![close-icon](assets/close-icon.svg)

1. Navigieren Sie zu AEM Symbol > **[!UICONTROL Tools]** **[!UICONTROL Vorgänge]** **[!UICONTROL Testen]**
1. So führen Sie alle Tests der Test Suite aus:

   1. Tippen Sie im Bedienfeld [!UICONTROL Tests] auf **[!UICONTROL Wir für den Handel - Tests (1)]**. Die Suite wird erweitert, um die Liste des Tests anzuzeigen.
   1. Tippen Sie auf die Schaltfläche **[!UICONTROL Tests ausführen]**. Der leere Bereich auf der rechten Seite des Bildschirms wird durch ein adaptives Formular ersetzt, während der Test ausgeführt wird.

      ![all-test](assets/run-all-test.png)

1. So führen Sie einen einzelnen Test aus der Test Suite aus:

   1. Tippen Sie im Testbedienfeld auf **[!UICONTROL Wir für den Handel - Tests (1)]**. Die Suite wird erweitert, um die Liste des Tests anzuzeigen.
   1. Tippen Sie auf **[!UICONTROL Test vor dem Ausfüllen]** und dann auf die Schaltfläche **[!UICONTROL Tests ausführen]**. Der leere Bereich auf der rechten Seite des Bildschirms wird durch ein adaptives Formular ersetzt, während der Test ausgeführt wird.

1. Tippen Sie auf den Testnamen &quot;Vorausfüllen&quot;, um die Ergebnisse des Test Case zu überprüfen. Es wird das Bedienfeld [!UICONTROL Ergebnis] geöffnet. Tippen Sie im Bereich [!UICONTROL Ergebnis] auf den Namen Ihres Testfalls, um alle Testdetails Ansicht.

   ![review-results](assets/review-results.png)

Jetzt kann das adaptive Formular veröffentlicht werden.
