---
title: '"Tutorial: Testing your adaptive form"'
seo-title: '"Tutorial: Testing your adaptive form"'
description: Use automated testing to test multiple adaptive forms at once.
seo-description: Verwenden Sie automatisierte Tests, um mehrere adaptive Formulare gleichzeitig zu testen.
uuid: 6d182bbc-b47a-4c97-af70-c960b52fdfac
contentOwner: khsingh
discoiquuid: ecddb22e-c148-441f-9088-2e5b35c7021b
docset: aem65
translation-type: tm+mt
source-git-commit: 1a816672b3e97346f5a7a984fcb4dc0df1a5b0da
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 10%

---


# Übung: Testen des adaptiven Formulars {#tutorial-testing-your-adaptive-form}

![](do-not-localize/10-test-your-adaptive-form.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Nachdem das adaptive Formular fertig ist, müssen Sie das adaptive Formular testen, bevor Sie es an die Endbenutzer übertragen. Sie können jedes Feld manuell testen (funktionelle Tests) oder das Testen des adaptiven Formulars automatisieren. Wenn Sie mehrere adaptive Formulare haben, wird das manuelle Testen aller Felder der adaptiven Formulare zu einer beängstigenden Aufgabe.

AEM [!DNL Forms] bieten ein Testframework, Calvin, um das Testen Ihrer adaptiven Formulare zu automatisieren. Mit diesem Framework können Sie Tests der Benutzeroberfläche direkt in einem Webbrowser schreiben und ausführen. Das Framework stellt JavaScript-APIs zum Erstellen von Tests bereit. Mit dem automatisierten Test können Sie das Erlebnis zum Vorausfüllen eines adaptiven Formulars testen, die Sendeerfahrung eines adaptiven Formulars, die Regeln für den Ausdruck von Überprüfungen, verzögertes Laden und Benutzeroberflächeninteraktionen testen. Dieses Lernprogramm führt Sie durch die Schritte zum Erstellen und Ausführen automatisierter Tests für ein adaptives Formular. Am Ende dieser Schulung können Sie Folgendes:

* [Testsuite für Ihr adaptives Formular erstellen](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-suite)
* [Create tests for your adaptive form](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-case-to-prefill-values-in-an-adaptive-form)
* [Run test suite and tests created for your adaptive form](#step-run-all-the-tests-in-a-suite-or-individual-tests-cases)

## Step 1: Create a test suite {#step-create-a-test-suite}

Test suites have a collection of test cases. You can have multiple test suites. Es wird empfohlen, für jedes Formular eine separate Testsuite zu verwenden. So erstellen Sie eine Test-Suite:

1. Log to AEM [!DNL Forms] author instance in as an administrator. Open [!UICONTROL CRXDE Lite]. You can tap AEM Logo > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]** or open the [https://localhost:4502/crx/de/index.jsp](https://localhost:4502/crx/de/index.jsp) URL in a browser to open CRXDE Lite.

1. Navigate to /etc/clientlibs in [!UICONTROL CRXDE Lite]. Klicken Sie mit der rechten Maustaste auf den Unterordner /etc/clientlibs und dann auf **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**. In the **[!UICONTROL Name]** field type **WeRetailFormTestCases**. Select the type as **cq:ClientLibraryFolder** and click **[!UICONTROL OK]**. It creates a node. You can use any name in place of `WeRetailFormTestCases`.
1. Add the following properties to the `WeRetailFormTestCases` node and tap **[!UICONTROL Save ALL]**.

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

1. Right-click the **[!UICONTROL WeRetailFormTestCases]** node click **[!UICONTROL Create]** > **[!UICONTROL Create File]**. In the **[!UICONTROL Name]** field, type `js.txt` and click **[!UICONTROL OK]**.
1. Öffnen Sie die Datei &quot;js.txt&quot;zur Bearbeitung, fügen Sie den folgenden Code hinzu und speichern Sie die Datei:

   ```text
   #base=.
    init.js
   ```

1. Erstellen Sie eine Datei, init.js, im `WeRetailFormTestCases`Knoten. hinzufügen Sie den folgenden Code in die Datei und tippen Sie auf Alle **[!UICONTROL speichern]**.

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

   Mit dem obigen Code wird eine Testsuite mit dem Namen **We retail - Tests** erstellt.

1. Öffnen Sie AEM Testing UI (AEM > **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Tests]**). Die Testsuite - **Wir für den Handel - Tests** - wird in der Benutzeroberfläche aufgelistet.

   ![we-retail-test-suite](assets/we-retail-test-suite.png)

## Schritt 2: Erstellen eines Testfalls zum Vorausfüllen von Werten in einem adaptiven Formular {#step-create-a-test-case-to-prefill-values-in-an-adaptive-form}

Ein Testfall ist eine Reihe von Aktionen zum Testen einer bestimmten Funktion. Beispielsweise müssen Sie alle Felder eines Formulars im Voraus ausfüllen und einige Felder überprüfen, um sicherzustellen, dass die richtigen Werte eingegeben werden.

Eine Aktion ist eine bestimmte Aktivität in einem adaptiven Formular, z. B. durch Klicken auf eine Schaltfläche. So erstellen Sie einen Testfall und Aktionen, um die Benutzereingabe für jedes adaptive Formularfeld zu überprüfen:

1. Navigieren Sie in [!UICONTROL CRXDE Lite]zum `/content/forms/af/create-first-adaptive-form` Ordner. Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL create-first-adaptive-form]** und klicken Sie auf **[!UICONTROL Create]**> **[!UICONTROL Create File]**. In the **[!UICONTROL Name]** field, type `prefill.xml` and click **[!UICONTROL OK]**. Fügen Sie der Datei „“ den folgenden Code hinzu:

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

1. Navigieren Sie zu `/etc/clientlibs`. Right-click the `/etc/clientlibs` subfolder and click **[!UICONTROL Create]**> **[!UICONTROL Create Node]**.

   Geben Sie im Feld **[!UICONTROL Name]** den gewünschten Wert ein `WeRetailFormTests`. Wählen Sie den Typ aus `cq:ClientLibraryFolder` und klicken Sie auf **[!UICONTROL OK]**.

1. Add the following properties to the **[!UICONTROL WeRetailFormTests]** node.

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
        <li>granite.testing.hobbes.tests.testForm</li>
       </ul> </td>
     </tr>
     <tr>
      <td>dependencies</td>
      <td>Zeichenfolge</td>
      <td>Aktiviert</td>
      <td>
       <ul>
        <li>granite.testing.calvin.tests</li>
       </ul> </td>
     </tr>
     </tbody>
   </table>

1. Erstellen Sie die Datei &quot;js.txt&quot;im Knoten **[!UICONTROL WeRetailFormTests]** . hinzufügen Sie Folgendes zur Datei:

   ```shell
   #base=.
   prefillTest.js
   ```

   Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Erstellen Sie eine Datei `prefillTest.js`im Knoten **[!UICONTROL WeRetailFormTests]** . hinzufügen Sie den unten stehenden Code in die Datei ein. Der Code erstellt einen Testfall. Der TestCase füllt alle Felder eines Formulars im Voraus aus und überprüft einige Felder, um sicherzustellen, dass korrekte Werte eingegeben werden.

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

## Schritt 3: Führen Sie alle Tests in einer Suite oder in einzelnen Testfällen aus {#step-run-all-the-tests-in-a-suite-or-individual-tests-cases}

Eine Testsuite kann mehrere Testfälle aufweisen. Sie können alle Testfälle in einer Testsuite auf einmal oder einzeln ausführen. Wenn Sie einen Test durchführen, werden die Ergebnisse durch die Symbole angezeigt:

* A checkmark icon indicates a passed test: ![save_icon](assets/save_icon.svg)
* An &quot;X&quot; icon indicates a failed test: ![close-icon](assets/close-icon.svg)

1. Navigate to AEM icon > **[!UICONTROL Tools]**> **[!UICONTROL Operations]**> **[!UICONTROL Testing]**
1. To run all the tests of the Test Suite:

   1. In the [!UICONTROL Tests] panel, tap **[!UICONTROL We retail - Tests (1)]**. Die Suite wird erweitert, um die Liste des Tests anzuzeigen.
   1. Tap the **[!UICONTROL Run tests]** button. Der leere Bereich auf der rechten Seite des Bildschirms wird durch ein adaptives Formular ersetzt, während der Test ausgeführt wird.

      ![all-test](assets/run-all-test.png)

1. So führen Sie einen einzelnen Test aus der Test Suite aus:

   1. Tippen Sie im Fenster Tests auf **[!UICONTROL Wir für den Handel - Tests (1)]**. Die Suite wird erweitert, um die Liste des Tests anzuzeigen.
   1. Tippen Sie auf den Test **[!UICONTROL zum Vorausfüllen]** und dann auf die Schaltfläche zum **[!UICONTROL Ausführen von Tests]** . Der leere Bereich auf der rechten Seite des Bildschirms wird durch ein adaptives Formular ersetzt, während der Test ausgeführt wird.

1. Tippen Sie auf den Testnamen &quot;Vorausfüllen&quot;, um die Ergebnisse des Test Case zu überprüfen. It opens the [!UICONTROL Result] panel. Tap the name of your Test Case in the [!UICONTROL Result] panel to view all the details of the test.

   ![review-results](assets/review-results.png)

Now the adaptive form is ready for publishing.
