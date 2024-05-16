---
title: Best Practices für die Arbeit mit adaptiven Formularen
description: Das Dokument erläutert bewährte Verfahren zur Einrichtung eines AEM Forms-Projekts, zur Entwicklung adaptiver Formulare und zur Optimierung der Leistung für AEM Forms-Systeme.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components, Core Components
exl-id: 5c75ce70-983e-4431-a13f-2c4c219e8dde
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '5504'
ht-degree: 100%

---

# Best Practices für die Arbeit mit adaptiven Formularen {#best-practices-for-working-with-adaptive-forms}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Überblick {#overview}

Mit Adobe Experience Manager(AEM)-Formularen können Sie komplexe Transaktionen in einfache, beeindruckende digitale Erlebnisse transformieren. Allerdings bedarf es gemeinsamer Anstrengungen, ein effizientes und produktives AEM Forms-System zu implementieren, zu erstellen, auszuführen und zu warten.

Dieses Dokument enthält Vorgaben und Empfehlungen, von denen Forms-Administratoren, Verfasser und Entwickler profitieren können, wenn sie mit AEM Forms und insbesondere mit adaptiven Formularkomponenten arbeiten. Es beschreibt bewährte Verfahren vom Einrichten eines Formularentwicklungsprojekts bis zum Konfigurieren, Anpassen, Authoring und Optimieren von AEM Forms. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung des AEM Forms-Systems bei.

Darüber hinaus finden Sie hier einige Informationen für bewährte Verfahren zu AEM:

* [Bewährte Verfahren: Bereitstellung und Wartung von AEM ](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren: Erstellen von Inhalten ](/help/sites-authoring/best-practices.md)
* [Bewährte Verfahren: Verwaltung von AEM ](/help/sites-administering/administer-best-practices.md)
* [Bewährte Verfahren: Entwicklung von Lösungen ](/help/sites-developing/best-practices.md)

## Einrichten und Konfigurieren von AEM Forms {#set-up-and-configure-aem-forms}

### Einrichten des Formularentwicklungsprojekts {#setting-up-forms-development-project}

Eine vereinfachte und standardisierte Projektstruktur kann die Entwicklungs- und Wartungsbemühungen erheblich reduzieren. Apache Maven ist ein Open Source-Werkzeug, das zum Erstellen von AEM-Projekten empfohlen wird.

* Verwenden Sie Apache Maven `aem-project-archetype`, um eine Struktur für AEM-Projekte zu erstellen und zu verwalten. Es werden empfohlene Strukturen und Vorlagen für Ihr AEM-Projekt erstellt. Darüber hinaus bietet es Versionsautomatisierungs- und Änderungskontrollsysteme, um das Projekt zu verwalten.

   * Verwenden Sie den Maven-Befehl `archetype:generate`, um die anfängliche Struktur zu generieren.
   * Verwenden Sie den Maven-Befehl `eclipse:eclipse`, um die Eclipse-Projektdateien zu generieren und das Projekt in Eclipse zu importieren.

Weitere Informationen finden Sie unter[ Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md).

* Mit dem FileVault-Werkzeug oder VLT können Sie den Inhalt einer CRX- oder AEM-Instanz auf Ihr Dateisystem zuordnen. Es bietet Änderungskontroll-Management-Vorgänge, wie z. B. das Einchecken und Auschecken des AEM-Projektinhalts. Siehe [Vewenden des VLT-Tools](/help/sites-developing/ht-vlttool.md).

* Wenn Sie die integrierte Entwicklungsumgebung für Eclipse verwenden, können Sie AEM Developer Tools für eine nahtlose Integration der Eclipse IDE in AEM-Instanzen verwenden und AEM-Anwendungen erstellen. Weitere Informationen finden Sie unter [AEM- Entwicklerwerkzeuge für Eclipse](/help/sites-developing/aem-eclipse.md).

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Wenn Sie Pakete zum Verschieben von Inhalten erstellen, stellen Sie sicher, dass die Paketfilterpfade korrekt sind und nur erforderliche Pfade erwähnt werden.

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Definieren Sie die richtigen Abhängigkeiten für die Pakete, um eine vorab bestimmte Installationsreihenfolge zu erzwingen.

* Erstellen Sie keinen referenzierbaren Knoten in /libs oder /apps.

### Planen der Authoring-Umgebung {#planning-for-authoring-environment}

Nachdem Sie Ihr AEM-Projekt eingerichtet haben, definieren Sie eine Strategie für das Authoring und Anpassen von Vorlagen für adaptive Formulare und Komponenten.

* Eine adaptive Formularvorlage ist eine spezielle AEM-Seite, die die Struktur und die Informationen für Kopfzeile und Fußzeile eines adaptiven Formulars definiert. Eine Vorlage enthält vorkonfigurierte Layouts, Stile und eine einfache Struktur für ein adaptives Formular. AEM Forms bietet Standardvorlagen und -Komponenten, die Sie verwenden können, um adaptive Formulare zu erstellen. Sie können jedoch benutzerdefinierte Vorlagen und Komponenten entsprechend Ihren Anforderungen erstellen. Es wird empfohlen, Anforderungen für zusätzliche Vorlagen und Komponenten zu erfassen, die Sie in Ihren adaptiven Formularen benötigen. Weitere Informationen finden Sie unter [Anpassen von adaptiven Formularen und Komponenten](/help/forms/using/adaptive-forms-best-practices.md#customize-components).
* Mit AEM Forms können Sie adaptive Formulare erstellen, die auf folgenden Formularmodellen basieren. Die Formularmodelle fungieren als Schnittstelle für den Datenaustausch zwischen einem Formular und einem AEM-System und liefern eine XML-basierte Struktur für den Datenfluss innerhalb und außerhalb eines adaptiven Formulars. Außerdem legen die Formularmodelle die Regeln und Beschränkungen für adaptive Formulare in Form von Schema- und XFA-Beschränkungen fest.

   * **Keine**: Adaptive Formulare, die mit dieser Option erstellt worden sind, verwenden kein Formularmodell. Die XML-Datendatei, die aus diesen Formularen generiert wird, hat eine flache Struktur mit Feldern und entsprechenden Werten.
   * **XML- oder JSON-Schema**: XML- und JSON-Schemata stellen die Struktur dar, in der Daten vom Back-End-System in Ihrer Organisation produziert oder genutzt werden. Sie können ein Schema mit einem adaptiven Formular verknüpfen und dem adaptiven Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas stehen auf der Registerkarte „Datenmodellobjekt“ des Inhalts-Browsers für das Erstellen von adaptiven Formularen zur Verfügung. Sie können die Schemaelemente zum Erstellen des Formulars ziehen und ablegen.
   * **XFA-Formularvorlage**: Dieses Formularmodell ist ideal, wenn bereits ein Bestand an XFA-basierten HTML5-Formularen vorhanden ist. Es bietet eine direkte Möglichkeit, Ihre XFA-basierten Formulare in adaptive Formulare zu konvertieren. Alle vorhandenen XFA-Regeln bleiben in den zugehörigen adaptiven Formularen erhalten. Die resultierenden adaptiven Formulare unterstützen XFA-Konstrukte, z. B. Überprüfungen, Ereignisse, Eigenschaften und Muster.
   * **Formulardatenmodell**: Dies ist das bevorzugte Formularmodell, wenn Sie Ihre Backend-Systeme wie Datenbanken, Web-Services und AEM-Benutzerprofile integrieren möchten, um adaptive Formulare vorauszufüllen und übermittelte Formulardaten zurück in die Backend-Systeme zu schreiben. Mit einem Formulardatenmodell-Editor können Sie Entitäten und Dienste in einem Formulardatenmodell definieren und konfigurieren, das Sie zum Erstellen adaptiver Formulare verwenden können. Weitere Informationen finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

Es ist wichtig, das Datenmodell mit Bedacht auszuwählen, das nicht nur Ihren Anforderungen entspricht, aber Ihre bereits getätigten Investitionen in XSD-Asset XFA-Assets erweitert. Verwenden Sie das XSD-Modell, um Formularvorlagen zu erstellen, da die generierte XML Daten enthält, die per XPATH vom Schema definiert wurden. Die Verwendung des XSD-Modells als Standardoption für das Formulardatenmodell ist ebenfalls hilfreich, weil wegen der One-to-One-Zuweisung des Formularfelds der Formularentwurf vom Backend-System, das Daten verarbeitet und verbraucht, entkoppelt und die Leistung des Formulars verbessert wird. Außerdem kann BindRef des Felds als XPATH seines Datenwerts in XML verwendet werden.

Weitere Informationen finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

* Es gibt einige gemeinsame Abschnitte für adaptive Formulare. Sie können sie identifizieren und eine Strategie definieren, um die Wiederverwendung von Inhalten zu fördern. Adaptive Formulare gestatten Ihnen, eigenständige Fragmente zu erstellen und sie in allen Formularen wiederzuverwenden. Zudem können Sie ein Panel in einem adaptiven Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen Formularen widergespiegelt. Dies hilft Ihnen, die Authoring-Zeit zu reduzieren, und gewährleistet die Konsistenz in allen Formularen. Darüber hinaus werden adaptive Formulare durch die Verwendung von Fragmenten einfacher, was insbesondere bei größeren Formularen zu einer verbesserten Authoring-Erfahrung führt. Weitere Informationen finden Sie unter [Adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md).

### Anpassen adaptiver Formulare und Komponenten {#customize-components}

* AEM Forms bietet vordefinierte adaptive Formularvorlagen, mit denen Sie adaptive Formulare erstellen können. Sie können auch eigene Vorlagen erstellen. AEM stellt statische und bearbeitbare Vorlagen bereit.

   * Statische Vorlagen werden von den Entwicklern definiert und konfiguriert.
   * Bearbeitbare Vorlagen werden von Autorinnen und Autoren mithilfe des Vorlageneditors erstellt. Mit dem Vorlageneditor können Sie eine grundlegende Struktur und den anfänglichen Inhalt einer Vorlage definieren. Jede Änderung der Strukturebene wird in allen Formularen, die diese Vorlage verwenden, widergespiegelt. Der anfängliche Inhalt kann vorkonfigurierte Designs, Vorfülldienste, Sendeaktionen usw. umfassen. Diese Einstellungen können jedoch mit dem Formulareditor für ein Formular geändert werden. Weitere Informationen finden Sie unter [Adaptive Formularvorlagen](/help/forms/using/template-editor.md).

* Verwenden Sie [Inline-Formatierung](/help/forms/using/inline-style-adaptive-forms.md) für die Formatierung einer bestimmten Feld- oder Bedienfeldinstanz. Stattdessen können Sie auch eine Klasse in einer CSS-Datei definieren und den Klassennamen in der CSS-Klasseneigenschaft der Komponente angeben.
* Binden Sie eine Client-Bibliothek in eine Komponente ein, um Stile in allen adaptiven Formularen oder Fragmenten, die diese Komponente verwenden, konsistent anzuwenden. Weitere Informationen finden Sie unter [Erstellen einer Seitenkomponente für adaptive Formulare](/help/forms/using/custom-adaptive-forms-templates.md).
* Wenden Sie in einer Client-Bibliothek definierte Stile auf ausgewählte adaptive Formulare an, indem Sie den Pfad zur Client-Bibliothek im Feld „CSS-Dateipfad“ in den Eigenschaften des adaptiven Formular-Containers angeben.
* Um eine Client-Bibliothek mit eigenen Stilen zu erstellen, können Sie die benutzerdefinierte CSS-Datei im Design-Editor unter dem Basisverzeichnis „clientlib“ oder in den Eigenschaften des Formular-Containers konfigurieren.
* Adaptive Formulare bieten Bereichs-Layouts, z. B. responsive Layouts, Panels mit Registerkarten, Akkordeons und Assistenten, um zu steuern, wie Formularkomponenten in einem Bereich angeordnet werden. Sie können benutzerdefinierte Panel-Layouts erstellen und für Autorinnen und Autoren von Formularen verfügbar machen. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Layout-Komponenten für adaptive Formulare](/help/forms/using/custom-layout-components-forms.md).
* Sie können auch bestimmte adaptive Formularkomponenten wie Felder und das Panel-Layout anpassen.

   * Verwenden Sie die Funktion [Überlagerung](/help/sites-developing/overlays.md) von AEM, um eine Kopie einer Komponente zu ändern. Es wird nicht empfohlen, Standardkomponenten zu ändern.
   * Um das Layout von vordefinierten adaptiven Formularkomponenten in /libs anzupassen, [erstellen Sie benutzerdefinierte Layout-Komponenten](/help/forms/using/custom-layout-components-forms.md) zusätzlich zu den [Standard-Layouts](/help/forms/using/layout-capabilities-adaptive-forms.md).
   * Führen Sie benutzerdefinierte Interaktivitäten ein, indem Sie benutzerdefinierte Widgets oder Erscheinungsbilder erstellen. Es wird nicht empfohlen, Standardkomponenten zu ändern. Weitere Informationen finden Sie unter [Erscheinungsbild-Framework](/help/forms/using/introduction-widgets.md).

* Weitere Informationen finden Sie unter[ Bearbeiten von persönlichen identifizierbaren Informationen](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) für Vorschläge zum Umgang mit PII-Daten.

### Erstellen von Formularvorlagen

Sie können ein adaptives Formular mithilfe der in **Konfigurations-Browser** aktivierten Formularvorlagen erstellen. Informationen zum Aktivieren der Formularvorlagen finden Sie unter [Erstellen einer adaptiven Formularvorlage](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/creating-your-first-adaptive-form/create-adaptive-form-template.html?lang=de).

Die Formularvorlagen können auch aus Paketen mit adaptiven Formularen, die auf einem anderen Autoren-Computer erstellt werden, hochgeladen werden. Formularvorlagen werden durch die Installation von [aemforms-references-* packages](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) verfügbar gemacht. Zu den empfohlenen Best Practices gehören:

* Der Ausführungsmodus **nosamplecontent** wird nur für Autor- und nicht für Veröffentlichungsknoten empfohlen.
* Die Bearbeitung von Assets wie adaptiven Formularen, Designs, Vorlagen oder Cloud-Konfigurationen erfolgt nur über Autorknoten, die auf den konfigurierten Veröffentlichungsknoten veröffentlicht werden können.
Weitere Informationen finden Sie unter [Veröffentlichung von Formularen und Dokumenten und Veröffentlichungen rückgängig machen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=de)
* Das Add-On-Paket für Forms ist für Authoring und Publishing erforderlich, um die Document Service-Vorgänge zu unterstützen. Daher kann es als Abhängigkeit betrachtet werden.
Wenn Sie nur Forms-bezogene Beispielvorlagen, Designs und DOR-Pakete möchten, können Sie sie von [aemforms-references-* packages](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=de) herunterladen.

Weitere Informationen finden Sie im Abschnitt zu empfohlenen Vorgehensweisen unter [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

## Erstellen adaptiver Formulare {#author-adaptive-forms}

### Verwenden Touch-optimierter Benutzeroberflächen für das Authoring {#using-touch-optimized-ui-for-authoring}

* Verwenden Sie den Objekt-Browser in der Seitenleiste, um schnell auf Felder in der Formularhierarchie zuzugreifen. Sie können im Suchfeld nach Objekten in der Formular- oder Objektstruktur, um von einem Objekt zu einem anderen zu navigieren.
* Um die Eigenschaften einer Komponente im Komponenten-Browser in der Seitenleiste anzuzeigen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr-1](assets/cmppr-1.png). Sie können auch auf eine Komponente doppelklicken, um deren Eigenschaften im Eigenschaften-Browser anzuzeigen.
* Verwenden Sie die Tastaturkürzel, um schnelle Aktionen in Ihren Formularen durchzuführen. Siehe [Tastaturbefehle für AEM Forms](/help/forms/using/keyboard-shortcuts.md).

* Adaptive Formularkomponenten werden nur zur Verwendung auf adaptiven Formularseiten empfohlen. Die Komponenten weisen Abhängigkeiten von ihrer übergeordneten Hierarchie auf. Daher dürfen Sie diese nicht auf der AEM-Seite verwenden.

Weitere Informationen finden Sie außerdem unter „Komponentenbeschreibungen und optimale Verfahren“ in der [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

### Verwenden von Regeln in adaptiven Formularen {#using-rules-in-adaptive-forms}

AEM Forms bietet einen [Regeleditor](/help/forms/using/rule-editor.md), der es Ihnen ermöglicht, Regeln zu erstellen, um dynamisches Verhalten zu adaptiven Formularkomponenten hinzuzufügen. Unter Verwendung dieser Regeln können Bedingungen ausgewertet werden und Aktionen auf Komponenten ausgelöst werden, wie z. B. Felder anzeigen oder ausblenden, Werte berechnen, Dropdownlisten dynamisch ändern und so weiter.

Der Regeleditor bietet einen visuellen Editor und einen Code-Editor zum Schreiben von Regeln. Beachten Sie beim Schreiben von Regeln im Code-Editor-Modus Folgendes:

* Verwenden Sie aussagekräftige und eindeutige Namen für Formularfelder und Komponenten, um mögliche Konflikte beim Schreiben von Regeln zu vermeiden.
* Verwenden Sie den `this`-Operator für eine Komponente, damit diese auf sich selbst in einem Regelausdruck verweist. Es wird sichergestellt, dass die Regel gültig bleibt, selbst wenn sich der Komponentenname ändert. Beispiel: `field1.valueCommit script: this.value > 10`.

* Verwenden Sie Komponentennamen, wenn Sie auf verschiedene Formularkomponenten verweisen. Verwenden Sie die `value`-Eigenschaft, um den Wert eines Feldes oder einer Komponente abzurufen. Beispiel: `field1.value`.

* Verweisen Sie auf Komponenten durch die relative eindeutige Hierarchie, um Konflikte zu vermeiden. Beispiel: `parentName.fieldName`.

* Beim Bearbeiten von komplexen oder häufig verwendeten Regeln sollten Sie die Business-Logik als Funktionen in eine separate Client-Bibliothek schreiben, die Sie in adaptiven Formularen festlegen und wieder verwenden können. Die Client-Bibliothek sollte eine eigenständige Bibliothek sein und darf keine externen Abhängigkeiten, außer von jQuery und Underscore.js haben. Sie können die Client-Bibliothek auch benutzen, um [serverseitige erneute Überprüfung](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) der übermittelten Formulardaten zu erzwingen.
* Adaptive Formulare bieten eine Reihe von APIs, über die Sie kommunizieren und Aktionen für adaptive Formulare anzeigen können. Einige der wichtigsten APIs sind im Folgenden aufgeführt. Weitere Informationen finden Sie in der [Referenz zur JavaScript-Bibliotheks-API für adaptive Formulare](https://adobe.com/go/learn_aemforms_documentation_63_de).

   * `guideBridge.reset()`: Setzt ein Formular zurück.
   * `guideBridge.submit()`: Versendet ein Formular.
   * `guideBridge.setFocus(somExp, focusOption, runCompletionExp)`: Setzt den Fokus auf ein Feld.
   * `guideBridge.validate(errorList, somExpression, focus)`: Validiert ein Formular.
   * `guideBridge.getDataXML(options)`: Ruft Formulardaten als XML ab.
   * `guideBridge.resolveNode(somExpression)`: Ruft ein Formularobjekt ab.
   * `guideBridge.setProperty(somList, propertyName, valueList)`: Setzt die Eigenschaft eines Formularobjekts.
   * Darüber hinaus können Sie die folgenden Feldeigenschaften verwenden:

      * `field.value`, um den Wert eines Felds zu ändern.
      * `field.enabled`, um ein Feld zu aktivieren.
      * `field.visible`, um die Sichtbarkeit eines Felds zu ändern. 

* Autorinnen und Autoren adaptiver Formulare müssen möglicherweise JavaScript-Code schreiben, um Business-Logik in ein Formular zu integrieren. JavaScript ist zwar leistungsstark und effektiv, aber kann die Sicherheit beeinflussen. Daher müssen Sie sicherstellen, dass die Autorin bzw. der Autor des Formulars eine vertrauenswürdige Person ist und Prozesse zur Überprüfung und Genehmigung von JavaScript-Code vorhanden sind, bevor ein Formular produktiv eingesetzt wird. Admins können den Zugriff auf den Regeleditor für Benutzergruppen entsprechend ihrer Rolle oder Funktion beschränken. Siehe [Gewähren von Zugriff auf den Regeleditor für ausgewählte Benutzergruppen](/help/forms/using/rule-editor-access-user-groups.md).
* Sie können Ausdrücke in Regeln verwenden, um adaptive Formulare dynamisch zu gestalten. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und nutzen Scripting-Modell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Weitere Informationen zu Ausdrücken und optimalen Verfahren finden Sie unter[ Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md). 

* Adobe empfiehlt bei der Regelerstellung mit dem Regeleditor die Verwendung von synchronen statt asynchronen JavaScript-Vorgängen. Es wird dringend davon abgeraten, asynchrone Vorgänge zu verwenden. Wenn Sie sich jedoch in einer Situation befinden, in der asynchrone Vorgänge unvermeidbar sind, müssen JavaScript-Closure-Funktionen implementiert werden. So können Sie sich wirksam vor potenziellen Wettlaufsituationen schützen und Regelimplementierungen mit optimaler Leistung sowie Stabilität im gesamten System sicherstellen.

  Nehmen wir beispielsweise an, wir müssen Daten aus einer externen API abrufen und wenden dann einige auf diesen Daten basierende Regeln an. Wir setzen eine Closure ein, um den asynchronen API-Aufruf zu verarbeiten und sicherzustellen, dass die Regeln angewendet werden, nachdem die Daten abgerufen wurden. Dies ist der Beispiel-Code:

  ```JavaScript
       function fetchDataFromAPI(apiEndpoint, callback) {
        // Simulate asynchronous API call with setTimeout
        setTimeout(() => {
          // Assuming the API call is successful, we receive some data
          const data = {
            someValue: 42,
          };
          // Invoke the callback with the fetched data
          callback(data);
        }, 2000); // Simulate a 2-second delay for the API call
      }
      // Rule implementation using Closure
      function ruleImplementation(apiEndpoint) {
        // Using a closure to handle the asynchronous API call and rule application
        // say you have set this value in street field inside address panel
        var streetField = address.street;
        fetchDataFromAPI(apiEndpoint, (data) => {
          streetField.value = data.someValue;
        });
      }
      // Example usage of the rule implementation
      const apiEndpoint = "https://example-api.com/data";
      ruleImplementation(apiEndpoint);
  ```

  In diesem Beispiel simuliert `fetchDataFromAPI` einen asynchronen API-Aufruf mithilfe von `setTimeout`. Nach dem Datenabruf wird die bereitgestellte Callback-Funktion aufgerufen, bei der es sich um die Closure zur Verarbeitung der nachfolgenden Regelanwendung handelt. Die Funktion `ruleImplementation` enthält die Regellogik.


### Arbeiten mit Designs {#working-with-themes}

Mit Designs für adaptive Formulare können Sie wiederverwendbare Stile erstellen, die formularübergreifend angewendet werden können, um Einheitlichkeit in Bezug auf Look und Stil zu erreichen. Verwenden Sie Designs, um Formatierungen für Formularkomponenten und Bedienfelder zu definieren. Einige Best Practices zu Designs lauten wie folgt:

* Nutzen Sie die Asset-Bibliothek zur schnellen Anwendung von Textstilen, Hintergründen und Bildern. Wenn ein Stil in der Asset-Bibliothek hinzugefügt wird, steht er für andere Designs und im Stilmodus des Formulareditors zur Verfügung.
* Wenden Sie globale Einstellungen, z. B. für Schrift und Seitenhintergrund, mithilfe der Auswahl auf Seitenebene an.
* Verwenden Sie Client-Bibliotheken, um vorhandene oder erweiterte Stile in Ihre Designs zu importieren.
* Sie können Stile für bestimmte Felder, Bereiche oder Schaltflächen in einer Formularstilebene außer Kraft setzen. 
* Wenn ein Design nicht Ihre Formatierungsanforderungen erfüllt, können Sie vordefinierte Klassen wie „guideFieldNode“, „guideFieldLabel“, „guideFieldWidget“ und „guidePanelNode“ verwenden, um einen gemeinsamen Stil formularübergreifend anzuwenden.

Weitere Informationen finden Sie unter [Designs](/help/forms/using/themes.md).

### Optimieren der Leistung von großen und komplexen Formularen {#optimizing-performance-of-large-and-complex-forms}

Formularautorinnen und -autoren sowie Endbenutzende sehen sich in der Regel mit Leistungsproblemen konfrontiert, wenn große Formulare im Authoring-Modus oder zur Laufzeit geladen werden. Wenn die Anzahl der Objekte (Felder und Bereiche) in den Formularen zunimmt, nimmt die Authoring- und Laufzeiterfahrung ab. Es wird außerdem verhindert, dass mehrere Autorinnen und Autoren zusammenarbeiten und ein Formular gleichzeitig bearbeiten.

Erwägen Sie die folgenden Best Practices, um Leistungsprobleme bei großen Formularen zu vermeiden:

* Es wird empfohlen, adaptive Formulare mithilfe von XSD-Formulardatenmodellen zu erstellen, selbst bei Konvertierung einer XFA in ein adaptives Formular. 
* Schließen Sie nur die Felder und Bereiche in adaptiven Formularen, die Informationen vom Benutzer erfassen. Versuchen Sie, statische Inhalte auf ein Minimum zu reduzieren, oder verwenden Sie URLs, um sie in einem separaten Fenster zu öffnen.
* Zwar wird jedes Formular für einen bestimmten Zweck entwickelt, dennoch gibt es bei den meisten Formularen auch gemeinsame Abschnitte. Ein Beispiel hierfür sind etwa persönliche Daten, die Adresse, Angaben zur Beschäftigung usw. Erstellen Sie [adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md) für allgemeine Formularelemente und -abschnitte und verwenden Sie diese in allen Formularen. Sie können auch ein Panel in einem vorhandenen Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen adaptiven Formularen widergespiegelt. Es unterstützt gemeinsames Authoring, da mehrere Verfasser an verschiedenen Fragmenten, die ein Formular bilden, gleichzeitig arbeiten können.

   * Ähnlich wie bei adaptiven Formularen wird empfohlen, dass alle fragmentspezifischen Stile und benutzerdefinierten Skripte mithilfe des Fragment-Container-Dialogfelds in der Client-Bibliothek definiert werden. Außerdem sollten Sie eigenständige Fragmente erstellen, die nicht von externen Objekten abhängig sind.
   * Außerdem sollten Sie Cross-Fragments-Skripterstellung vermeiden. Wenn es ein Objekt außerhalb des Fragments gibt, auf das Sie verweisen möchten, müssen Sie das Objekt als Teil des übergeordneten Formulars einarbeiten. Wenn sich das Objekt dennoch in einem anderen Fragment befinden muss, verweisen Sie im Skript anhand seines Namens darauf.

* Verwenden Sie „Speichern und fortsetzen“ mit der automatischen Speicherung, um das adaptive Formular regelmäßig zu speichern und es Benutzenden zu ermöglichen, das Formular später erneut zu öffnen und zu vervollständigen.
* Konfigurieren Sie Fragmente, um sie verzögert zu laden. Fragmente, die zur Laufzeit als „Verzögert laden“ markiert sind, werden nur gerendert, wenn sie erforderlich sind. Die Ladezeit für große Formulare wird dadurch erheblich reduziert. Dies wird außerdem in Fragmenten mit wiederholbaren Panels unterstützt. Weitere Informationen finden Sie unter [Konfigurieren von verzögertem Laden](/help/forms/using/lazy-loading-adaptive-forms.md).

   * Konfigurieren Sie Lazy Loading (verzögertes Laden) nicht in Fragmenten in einem Layout mit responsivem Raster oder im ersten Panel.
   * In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.
   * Markieren Sie einen Wert in einem verzögert geladenen Panel mit „Wert global verwenden“, wenn dieser Wert in einem anderen Teil des Formulars verwendet wird, sodass der Wert für die Verwendung verfügbar ist, wenn das enthaltene Panel entladen wird.
   * Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen.
* Legen Sie den Wert der **Anzahl der Aufrufe pro Anfrage** im **Apache Sling Main Servlet** auf eine recht große Zahl fest. Dadurch kann der Formular-Server zusätzliche Aufrufe zulassen. Die Konfiguration zeigt den Standardwert 1500 an. Dieser Wert (1500 Aufrufe) ist für andere Experience Manager-Komponenten wie Sites und Assets bestimmt. Der Standardwert für adaptive Formulare ist 20.000. Wenn Sie auf `too many calls`-Fehler in den Protokollen stoßen sollten oder das Formular nicht gerendert werden kann, versuchen Sie, den Wert auf eine große Zahl zu erhöhen, um das Problem zu beheben. Wenn die Anzahl der Aufrufe 20.000 überschreitet, bedeutet das, dass das Formular komplex ist und es einige Zeit dauern kann, das Formular im Browser zu rendern. Dies geschieht nur beim ersten Laden des Formulars. Danach wird das Formular zwischengespeichert, und sobald das Formular zwischengespeichert wurde, gibt es keine wesentliche Auswirkung mehr auf die Leistung.

### Vorausfüllen adaptiver Formulare {#prefilling-adaptive-forms}

Sie können Felder eines adaptiven Formulars mit Daten aus dem Backend vorbefüllen, um Benutzenden zu helfen, das Formular schnell auszufüllen und Tippfehler zu vermeiden.

* AEM Forms bietet einen Vorbefüllungsdienst, um Daten aus einer vordefinierten XML-Datendatei zu lesen und die Felder eines adaptiven Formulars mit dem Inhalt der XML-Vorbefüllungsdatei vorab auszufüllen.
* Die XML-Datei mit den Vorbefüllungsdaten muss mit dem Schema des Formularmodells, das mit dem adaptiven Formular verknüpft ist, konform sein.
* Schließen Sie die Abschnitte`afBoundedData` und`afUnBoundedData` in die Prefill-XML zum Vorbefüllen von gebundenen und ungebundenen Feldern in einem adaptiven Formular ein.

* Für adaptive Formulare, die auf dem Formulardatenmodell basieren, bietet AEM Forms einen sofort einsatzbereiten Vorbefüllungs-Service für Formulardatenmodelle an. Der Vorbefüllungsdienst fragt Datenquellen für Datenmodellobjekte im adaptiven Formular ab und trägt Feldwerte beim Rendern des Formulars vorab ein.
* Sie können auch die Datei-, CRX-, Dienst- oder HTTP-Protokolle zum Vorausfüllen adaptiver Formulare verwenden.
* AEM Forms unterstützt benutzerdefinierte Vorbefüllungsdienste, die Sie als OSGi-Dienst einbinden können, um adaptive Formulare vorauszufüllen.

Weitere Informationen finden Sie unter [Vorbefüllen der Felder in adaptiven Formularen](/help/forms/using/prepopulate-adaptive-form-fields.md).

### Signieren und Übermitteln adaptiver Formulare {#signing-and-submitting-adaptive-forms}

Adaptive Formulare benötigen Übermittlungsaktionen für die Verarbeitung der von Benutzern angegebenen Daten. Eine Sendeaktion bestimmt die Aufgabe, die auf die mithilfe eines adaptiven Formulars übermittelten Daten angewendet wird.

* Es gibt mehrere Sendeaktionen, die in adaptiven Formularen sofort verfügbar sind. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md).
* Sie können eine benutzerdefinierte Sendeaktion schreiben, wenn die standardmäßigen Sendeaktionen Ihren Anwendungsfall nicht erfüllen. Weitere Informationen finden Sie unter[ Schreiben von benutzerdefinierten Übermittlungsaktionen für ein adaptives Formular](/help/forms/using/custom-submit-action-form.md).
* Beziehen Sie serverseitige Validierungen ein, um zu verhindern, dass ungültige Daten übermittelt werden. 

Sie können die Funktion der mehrfachen Signaturen von Adobe Sign in adaptiven Formularen nutzen.  Beachten Sie die folgenden Punkte bei der Konfiguration von Adobe Sign in adaptiven Formularen.  Weitere Informationen finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

* Adobe Sign-aktiviertes Formular wird nur gesendet, nachdem alle Unterzeichner das Formular unterzeichnet haben. Formulare werden im Status „Ausstehende Signatur“ angezeigt, bis das Formular von allen Signierern unterzeichnet wurde.
* Sie können die Funktion des Unterzeichnens im Formular konfigurieren oder Unterzeichnende beim Absenden auf eine neue Signaturseite umleiten.
* Konfigurieren Sie das sequenzielle oder parallele Signieren nach Bedarf.

### Generieren eines Datensatzdokuments {#generating-document-of-record}

Ein Datensatzdokument (Document of Record, DoR) ist eine komprimierte PDF-Version eines adaptiven Formulars, die Sie drucken, signieren oder archivieren können.

* Je nach dem Formular-Datenmodell, auf dem ein adaptives Formular basiert, können Sie eine Vorlage für ein DoR wie folgt konfigurieren:

   * **XFA-Formularvorlage**: Verwendet die zugeordnete XDP-Datei als DoR-Vorlage.
   * **XSD-Schema**: Verwendet die zugeordnete XFA-Vorlage, die das gleiche XML-Schema wie das adaptive Formular verwendet.
   * **Ohne**: Verwendet ein automatisch generiertes DoR.

* Konfigurieren Sie Kopf- und Fußzeile, Bilder, Farbe und Schrift direkt auf der Registerkarte „Datensatzdokument“ des Editors für adaptive Formulare.
* Verwenden Sie `DoRService`, um das DoR programmatisch zu generieren.
* Ausgeblendete Felder aus DoR ausschließen.
* Verwenden Sie den Aufforderungsparameter `afAcceptLang`; um DoR in einem anderen Gebietsschema anzuzeigen.

### Debuggen und Testen von adaptiven Formularen {#debugging-and-testing-adaptive-forms}

Das [AEM-Chrome-Plug-in](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) ist eine Browser-Erweiterung für Google Chrome, die Tools zum Debugging adaptiver Formulare bereitstellt. Formularautorinnen und -autoren sowie Entwickelnde können diese Tools für Folgendes verwenden:

* Identifizieren von Engpässen und Optimieren der Leistung der Formularwiedergabe
* Debuggen von Schlüsselwörtern und bindRef-Fehlern im Formular
* Aktivieren und Konfigurieren von Protokollen
* Debuggen von Regeln und Skripten im Formular
* Erkunden von guideBridge APIs, um mehr darüber zu erfahren

Weitere Informationen finden Sie unter [AEM-Plug-In für Chrome – Adaptive Formulare](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/).

### Validieren von adaptiven Formularen auf dem AEM-Server {#validating-adaptive-forms-on-aem-server}

Serverseitige Überprüfungen sind erforderlich, um alle Versuche zu verhindern, die Überprüfungen auf dem Client und mögliche Gefahren von Datenübertragungen und Verletzungen von Geschäftsregeln umgehen wollen. Server-seitige Validierungen werden auf dem Server ausgeführt, indem die erforderliche Client-Bibliothek geladen wird.

* Schließen Sie Funktionen in einer Client-Bibliothek für die Validierung von Ausdrücken in adaptiven Formularen ein und legen Sie die Client-Bibliothek im Dialogfeld von adaptiven Formular-Containern fest.  Weitere Informationen finden Sie unter [Server-seitige erneute Validierung](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p).
* Die Server-seitige Validierung prüft das Formularmodell. Es wird empfohlen, eine separate Client-Bibliothek für Validierungen zu erstellen und sie nicht mit anderen Elementen wie HTML-Stil und DOM-Manipulation in derselben Client-Bibliothek zu mischen.

### Lokalisieren von adaptiven Formularen {#localizing-adaptive-forms}

AEM bietet Übersetzungs-Workflows, die Sie zur Lokalisierung adaptiver Formulare verwenden können.  Siehe [Verwenden von AEM-Übersetzungs-Workflows zum Lokalisieren adaptiver Formulare](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).

Einige Best Practices beim Lokalisieren von adaptiven Formularen lauten wie folgt:

* Verwenden Sie adaptive Formularfragmente für gängige Elemente in Formularen und lokalisieren Sie Fragmente. Das stellt sicher, dass Sie ein Fragment einmal lokalisieren und es dann in allen Formularen reflektiert wird, in denen das Fragment verwendet wird.
* Alle Modifizierungen wie das Hinzufügen einer neuen Komponente oder das Anwenden eines Skripts in einem lokalisierten Formular werden nicht automatisch lokalisiert.  Daher müssen Sie ein Formular vor der Lokalisierung fertigstellen, um mehrere Lokalisierungszyklen zu vermeiden.
* Verwenden Sie den Anforderungsparameter `afAcceptLang`, um das Browsergebietsschemazu überschreiben und das Formular in einem spezifischen Gebietsschema zu lokalisieren. Die folgende URL erzwingt beispielsweise die Darstellung des Formulars im japanischen Gebietsschema, unabhängig vom Gebietsschema, das in den Browser-Einstellungen angegeben ist:

  `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms unterstützt die Lokalisierung von Inhalten adaptiver Formulare derzeit für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italianisch (it), Deutsch (de), Japanisch (ja), Portugiesisch – Brasilien (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können jedoch zur Laufzeit Unterstützung für neue Gebietsschemata für adaptive Formulare hinzufügen. Weitere Informationen finden Sie unter [Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen](/help/forms/using/supporting-new-language-localization.md).

## Vorbereiten von Formularprojekten für die Produktion {#prepare-forms-project-for-production}

### Hinzufügen eines Servers zur Formularverarbeitung {#adding-forms-processing-server}

Sie können eine weitere Instanz des AEM Forms-Servers konfigurieren, der sich hinter der Firewall in einem geschützten Bereich befindet. Sie können diese Instanz für Folgendes verwenden:

* **Stapelverarbeitung**: Aufträge, die wiederkehrend sind oder in Stapeln mit hoher Belastung geplant werden. Beispiele hierfür sind das Drucken von Anweisungen, Generieren von Korrespondenz und Verwenden von Dokumentendiensten wie PDF Generator, Output und Assembler.
* **Speichern personenbezogener Daten**: Speicherung personenbezogener Daten auf dem Verarbeitungs-Server. Dies ist nicht erforderlich, wenn Sie bereits einen benutzerdefinierten Speicheranbieter zum Speichern personenbezogener Daten nutzen.

### Verschieben eines Projekts in eine andere Umgebung {#moving-project-to-another-environment}

Oft müssen Sie AEM-Projekte aus einer Umgebung in eine andere verschieben. Einige der wichtigsten Aspekte beim Verschieben lauten wie folgt:

* Erstellen Sie ein Backup von vorhandenen Client-Bibliotheken, benutzerdefiniertem Code und Konfigurationen.
* Stellen Sie Produktpakete und Patches manuell und in der angegebenen Reihenfolge in der neuen Umgebung bereit.
* Stellen Sie projektspezifische Code-Pakete und Bundles manuell und als separates Paket bzw. Bundle auf dem neuen AEM-Server bereit.
* (*Nur AEM Forms auf JEE*) Manuelle Bereitstellung von LCAs und DSCs auf dem Forms Workflow-Server.
* Verwenden Sie [Export-Import](/help/forms/using/import-export-forms-templates.md)-Funktionen, um Assets in die neue Umgebung zu verschieben. Sie können auch den Replikationsagenten konfigurieren und die Assets veröffentlichen.
* Ersetzen Sie bei der Aktualisierung alle veralteten APIs und Funktionen durch neue APIs und Funktionen.

### Konfigurieren von AEM {#configuring-aem}

Einige Best Practices zum Konfigurieren von AEM für eine bessere Gesamtleistung lauten wie folgt:

* Aktivieren Sie HTML-Client-Bibliothekskomprimierung für JavaScript und CSS-Code aus der Felix-Konsole.
* Speichern Sie alle Client-Bibliotheken unter `/etc.clientlibs/fd` und alle zusätzlichen benutzerdefinierten Client-Bibliotheken auf dem AEM-Dispatcher zwischen, um die Interaktivität und Sicherheit Ihrer veröffentlichen Formulare zu erhöhen. Weitere Informationen finden Sie unter [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html)

* Speichern Sie keine `/content/forms/af/`- und `/content/dam/formsanddocuments/*`-Pfade im Cache. Detaillierte Informationen zum Konfigurieren der Zwischenspeicherung adaptiver Formulare finden Sie unter [Zwischenspeichern adaptiver Formulare](/help/forms/using/configure-adaptive-forms-cache.md).

* Aktivieren Sie HTML über das Webserver-Komprimierungsmodul. Weitere Informationen finden Sie im Abschnitt [Leistungsoptimierung des AEM Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Erhöhen Sie die Aufrufe per Anfragekonfiguration für große Formulare. Siehe [Optimieren der Leistung von großen und komplexen Formularen](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Erstellen Sie [benutzerdefinierte, vom Fehler-Handler angezeigte Fehlerseiten](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/customizing-errorhandler-pages.html?lang=de).
* Sichere AEM Forms-Server.

   * Verwenden Sie `nosamplecontent`-Laufzeitmodus unter, um sicherzustellen, dass die Anwendung keine Beispielinhalte und Beispielbenutzer enthält, die auf dem Produktionsserver bereitgestellt werden. Siehe [Ausführen von AEM im produktionsfertigen Modus](/help/sites-administering/production-ready.md).

* Halten Sie die Heap-Größe bei mindestens 8 GB. Für andere Einstellungen finden Sie weitere Informationen im Abschnitt [Leistungsoptimierung des AEM Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Verwenden Sie Dienstbenutzersitzungen anstelle von Admin-Sitzungen zum Ausführen von Aufgaben auf Dienstebene. Weitere Informationen finden Sie unter [Dienstauthentifizierung](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html).

>[!VIDEO](https://vimeo.com/de/)

### Konfigurieren von externem Speicher für Entwürfe und übermittelte Formulardaten {#external-storage}

In einer Produktionsumgebung wird empfohlen, übermittelte Formulardaten nicht im AEM-Repository zu speichern. Bei der Standardimplementierung der Übermittlungsaktionen „Formularportal-Speicher“, „Inhalt speichern“ und „PDF speichern“ werden Formulardaten im AEM-Repository gespeichert. Diese Übermittlungsaktionen dienen nur zu Demonstrationszwecken. Die Funktionen „Speichern und fortsetzen“ und Automatische Speicherung“ verwenden auch standardmäßig Portalspeicher. Beachten Sie daher folgende Empfehlungen:

* **Speichern von Entwurfsdaten**: Wenn Sie die Funktion „Entwurf“ in ein adaptiven Formularen verwenden, müssen Sie eine benutzerdefinierte Service Provide Interface (Dienstanbieterbenutzeroberfläche, SPI) verwenden, um Entwurfsdaten in einem sichereren Speicher wie in einer Datenbank zu speichern. Weitere Informationen finden Sie unter [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

* **Speichern von Übermittlungsdaten**: Wenn Sie den Formularportalübermittlungs-Store verwenden, sollten Sie eine benutzerdefinierte SPI implementieren, um Übermittlungsdaten in einer Datenbank zu speichern. Siehe [Beispiel für die Integration der Komponente für Entwürfe und Übermittlungen mit der Datenbank](/help/forms/using/integrate-draft-submission-database.md) für ein Integrationsbeispiel.

  Sie können auch eine benutzerdefinierte Übermittlungsaktion schreiben, die Formulardaten und Anhänge in einem sicheren Speicher speichert. Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten Sendeaktion für adaptive Formulare](/help/forms/using/custom-submit-action-form.md).

* **Länge der Entwurfs-ID**: Wenn Sie ein adaptives Formular als Entwurf speichern, wird eine Entwurfs-ID generiert, um den Entwurf eindeutig zu identifizieren. Der Mindestwert für die Länge des Entwurfs-ID-Felds beträgt 26 Zeichen. Adobe empfiehlt, die Länge der Entwurfs-ID auf 26 oder mehr Zeichen festzulegen.

### Umgang mit personenbezogenen Daten {#handling-personally-identifiable-information}

Eine der größten Herausforderungen für Unternehmen besteht im Umgang mit personenbezogenen Daten (Personally Identifiable Information, PII). Einige Best Practices, die Ihnen beim Umgang mit solchen Daten helfen können, lauten wie folgt:

* Verwenden Sie einen sicheren externen Speicherort wie eine Datenbank, um Daten aus Entwürfen und übermittelten Formularen zu speichern. Siehe [Konfigurieren von externem Speicher für Entwürfe und eingereichte Formulardaten](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* Verwenden Sie die Formularkomponente „Geschäftsbedingungen“, um die ausdrückliche Zustimmung der Benutzenden vor Aktivierung der automatischen Speicherung einzuholen. Aktivieren Sie in diesem Fall die automatische Speicherung nur, wenn die Benutzenden den Bedingungen in der Komponente „Geschäftsbedingungen“ zustimmen.

## Auswählen von Regeleditor, Code-Editor oder benutzerdefinierten Client-Bibliotheken für adaptive Formulare {#RuleEditor-CodeEditor-ClientLibs}

### Regeleditor {#rule-editor}

<!--The AEM Forms Rule Editor offers predefined functions for defining rules in adaptive forms without extensive programming. It facilitates the implementation of conditional logic, data validation, and integration with external sources. This visual interface is especially valuable for business users and form designers, enabling them to create dynamic and complex rules with ease, here we discusss few use cases where rule editor allows you to:-->

Der AEM Forms-Regeleditor bietet eine visuelle Benutzeroberfläche zum Erstellen und Verwalten von Regeln, wodurch sich der Programmieraufwand deutlich reduziert. Dies kann insbesondere für Business-Anwenderinnen und Business-Anwender oder Formularentwicklerinnen und Formularentwickler nützlich sein, die möglicherweise keine größeren Programmierkenntnisse besitzen, aber Geschäftsregeln in den Formularen definieren und verwalten müssen. Hier werden einige Anwendungsfälle besprochen, in denen der Regeleditor Folgendes ermöglicht:

* <!-- Allows you --> Definieren von Geschäftsregeln für Ihre Formulare, ohne dass eine umfangreiche Programmierung erforderlich ist.
* <!-- Use the Rule Editor when you need --> Implementieren von Bedingungslogik in Ihren Formularen. Dazu gehören das Ein- oder Ausblenden von Formularelementen, das Ändern von Feldwerten basierend auf bestimmten Bedingungen oder das dynamische Ändern des Verhaltens Ihrer Formulare.
* <!--When you want --> Durchsetzen von Datenvalidierungsregeln bei Formularübermittlungen. Der Regeleditor kann hier zum Definieren von Validierungsbedingungen verwendet werden.
* <!-- When you need --> Integrieren Ihrer Formulare in externe Datenquellen (Formulardatenmodell) oder Dienste. Der Regeleditor kann hier beim Definieren von Regeln zum Abrufen, Anzeigen oder Bearbeiten von Daten während Formularinteraktionen helfen.
* <!-- If you want -->Erstellen dynamischer und interaktiver Formulare, die auf Benutzeraktionen reagieren. Mit dem Regeleditor können Sie hier Regeln definieren, die das Verhalten von Formularelementen in Echtzeit steuern.

Der Regeleditor ist sowohl für Foundation-Komponenten als auch für Kernkomponenten von AEM Forms verfügbar.

### Code-Editor {#code-editor}

Der Code-Editor ist ein Tool in Adobe Experience Manager (AEM) Forms, mit dem Sie benutzerdefinierte Skripte und Code für komplexere und erweiterte Funktionen in Ihre Formulare schreiben können. Hier werden einige Anwendungsfälle besprochen:

* Wenn Sie benutzerdefinierte Client-seitige Logik oder Verhaltensweisen implementieren müssen, die über die Funktionen des AEM Forms-Regeleditors hinausgehen, können Sie mit dem Code-Editor JavaScript-Code schreiben, um komplexe Interaktionen, Berechnungen oder Überprüfungen abzuwickeln.
* Wenn für Ihr Formular eine Server-seitige Verarbeitung oder Integration mit externen Systemen erforderlich ist, können Sie mit dem Code-Editor benutzerdefinierte Server-seitige Skripte schreiben. Sie können auf die guideBridge-API im Code-Editor zugreifen, um komplexe Logik in Formularereignissen und -objekten zu implementieren.
* Wenn Sie stark angepasste Benutzeroberflächen benötigen, die über die Standardfunktionen von AEM Forms-Komponenten hinausgehen, können Sie mit dem Code-Editor benutzerdefinierte Stile und Verhaltensweisen implementieren oder sogar benutzerdefinierte Formularkomponenten erstellen.
* Wenn Ihr Formular asynchrone Vorgänge wie das asynchrone Laden von Daten umfasst, können Sie diese Vorgänge mit dem Code-Editor über benutzerdefinierten asynchronen JavaScript-Code verwalten.

Beachten Sie, dass die Verwendung des Code-Editors gute Kenntnisse in JavaScript und der AEM Forms-Architektur voraussetzt. Stellen Sie außerdem bei der Implementierung von benutzerdefiniertem Code sicher, dass Sie die Best Practices befolgen, die Sicherheitsrichtlinien einhalten und Ihren Code gründlich testen, um potenzielle Probleme in Produktionsumgebungen zu vermeiden. Sie können mithilfe des Code-Editors eine Rückruffunktion für Formulardatenmodelle implementieren.

Der Code-Editor ist nur für die Foundation-Komponente von AEM Forms verfügbar. Für die Kernkomponenten des adaptiven Formulars können Sie mithilfe benutzerdefinierter Funktionen eigene Formularregeln erstellen, wie im nächsten Abschnitt beschrieben.

### Benutzerdefinierte Funktionen {#custom-client-libs}

Die Verwendung benutzerdefinierter Client-Bibliotheken in AEM Forms (Adobe Experience Manager Forms) kann in verschiedenen Szenarien von Vorteil sein, um Funktionalität, Stil oder Verhalten Ihrer Formulare zu verbessern. In bestimmten Situationen kann die Verwendung benutzerdefinierter Client-Bibliotheken sinnvoll sein:

* Wenn Sie ein eindeutiges Design oder Branding für Ihre Formulare implementieren müssen, das über die Funktionen der von AEM Forms bereitgestellten standardmäßigen Stiloptionen hinausgeht, können Sie benutzerdefinierte Client-Bibliotheken erstellen und darüber das Look-and-Feel steuern.
* Wenn eine benutzerdefinierte Client-seitige Logik und die Wiederverwendbarkeit von Methoden über mehrere Formulare hinweg oder Verhalten benötigt wird und sich dies nicht durch die standardmäßigen AEM Forms-Funktionen erreichen lässt. Dazu können dynamische Formularinteraktionen, benutzerdefinierte Validierungen oder die Integration in Bibliotheken von Drittanbietern gehören.
* Um die Leistung Ihrer Formulare durch Optimierung und Minimierung Client-seitiger Ressourcen zu verbessern.  Benutzerdefinierte Client-Bibliotheken können verwendet werden, um JavaScript- und CSS-Dateien zu bündeln und zu komprimieren, wodurch die Seitenladezeit insgesamt reduziert wird.
* Wenn Sie zusätzliche JavaScript-Bibliotheken oder -Frameworks integrieren müssen, die nicht im standardmäßigen AEM Forms-Setup enthalten sind. Dies kann für Funktionen wie erweiterte Datumsauswahl, Diagramme oder andere interaktive Komponenten erforderlich sein.

Bevor Sie sich für die Verwendung benutzerdefinierter Client-Bibliotheken entscheiden, müssen Sie den Wartungsaufwand, potenzielle Konflikte mit zukünftigen Updates und die Einhaltung von Best Practices berücksichtigen. Stellen Sie sicher, dass Ihre Anpassungen gut dokumentiert sind und getestet werden, um Probleme bei Upgrades oder der Zusammenarbeit mit anderen Entwickelnden zu vermeiden.

>[!NOTE]
> Benutzerdefinierte Funktionen sind sowohl für Foundation-Komponenten als auch für Kernkomponenten von AEM Forms verfügbar.

**Vorteile benutzerdefinierter Funktionen:**

**Benutzerdefinierte Funktionen** haben einen erheblichen Vorteil gegenüber dem **Code-Editor**, weil sie eine klare Trennung zwischen Inhalt und Code bieten, was die Zusammenarbeit verbessert und Workflows optimiert. Es wird empfohlen, benutzerdefinierte Funktionen zu verwenden, um folgende Vorteile zu erhalten:

* **Nahtlose Verwendung einer Versionskontrolle wie Git:**
   * Code und Inhalte voneinander zu isolieren, führt zu einer deutlichen Reduzierung von Git-Konflikten beim Content-Management und einem gut organisierten Repository.
   * Benutzerdefinierte Funktionen sind für Projekte nützlich, an denen mehrere Mitwirkende gleichzeitig arbeiten.

* **Technische Vorteile:**
   * Benutzerdefinierte Funktionen bieten Modularität und Kapselung.
   * Module können unabhängig entwickelt, getestet und gewartet werden.
   * Wiederverwendbarkeit und Wartbarkeit von Code werden verbessert.

* **Effizienter Entwicklungsprozess:**
   * Dank Modularität können sich Entwickelnde auf bestimmte Funktionen konzentrieren.
   * Entwickelnde werden entlastet, indem die Komplexität der gesamten Code-Basis für einen effizienteren Entwicklungsprozess reduziert wird.



