---
title: Best Practices für die Arbeit mit adaptiven Formularen
seo-title: Best Practices für die Arbeit mit adaptiven Formularen
description: Das Dokument erläutert bewährte Verfahren zur Einrichtung eines AEM Forms-Projekts, zum Entwickeln adaptiver Formulare und zur Optimierung der Leistung für AEM Forms-Systeme.
seo-description: Das Dokument erläutert bewährte Verfahren zur Einrichtung eines AEM Forms-Projekts, zum Entwickeln adaptiver Formulare und zur Optimierung der Leistung für AEM Forms-Systeme.
uuid: ed95fc64-56b3-4ea1-a5ba-2e96953fca56
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 43c431e4-5286-4f4e-b94f-5a7451c4a22c
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '4298'
ht-degree: 80%

---


# Best Practices für die Arbeit mit adaptiven Formularen {#best-practices-for-working-with-adaptive-forms}

## Überblick {#overview}

Mit Adobe Experience Manager (AEM) Forms können Sie komplexe Transaktionen in einfache, beeindruckende digitale Erlebnisse umwandeln. Allerdings bedarf es gemeinsamer Anstrengungen, ein effizientes und produktives AEM Forms-System zu implementieren, zu erstellen, auszuführen und zu warten.

Dieses Dokument enthält Vorgaben und Empfehlungen, von denen Forms-Administratoren, Verfasser und Entwickler profitieren können, wenn sie mit AEM Forms und insbesondere mit adaptiven Formularkomponenten arbeiten. Es beschreibt bewährte Verfahren vom Einrichten eines Formularentwicklungsprojekts bis zum Konfigurieren, Anpassen, Authoring und Optimieren von AEM Forms. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung des AEM-Forms-Systems bei.

Darüber hinaus finden Sie hier einige Informationen für bewährte Verfahren zu AEM:

* [Bewährte Verfahren: Bereitstellen und Warten von AEM](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren: Erstellen von Inhalten](/help/sites-authoring/best-practices.md) 
* [Bewährte Verfahren: Verwaltung von AEM](/help/sites-administering/administer-best-practices.md) 
* [Bewährte Verfahren: Entwicklung von Lösungen](/help/sites-developing/best-practices.md) 

## Einrichten und Konfigurieren von AEM Forms {#set-up-and-configure-aem-forms}

### Einrichten des Formularentwicklungsprojekts {#setting-up-forms-development-project}

Eine vereinfachte und standardisierte Projektstruktur kann die Entwicklungs- und Wartungsbemühungen erheblich reduzieren. Apache Maven ist ein Open Source-Werkzeug, das zum Erstellen von AEM-Projekten empfohlen wird.

* Verwenden Sie Apache Maven `aem-project-archetype`, um eine Struktur für AEM-Projekte zu erstellen und zu verwalten. Es werden empfohlene Strukturen und Vorlagen für Ihr AEM-Projekt erstellt. Darüber hinaus bietet es Versionsautomatisierungs- und Änderungskontrollsysteme, um das Projekt zu verwalten.

   * Verwenden Sie den Maven-Befehl `archetype:generate`, um die anfängliche Struktur zu generieren.
   * Verwenden Sie den Maven-Befehl `eclipse:eclipse`, um die Eclipse-Projektdateien zu generieren und das Projekt in Eclipse zu importieren.

Weitere Informationen finden Sie unter[ Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md).

* Mit dem FileVault-Werkzeug oder VLT können Sie den Inhalt einer CRX- oder AEM-Instanz auf Ihr Dateisystem zuordnen. Es bietet Änderungskontrollmanagementvorgänge, wie z. B. das Einchecken und Auschecken des AEM-Projektinhalts. Siehe [So verwenden Sie das VLT-Tool](/help/sites-developing/ht-vlttool.md).

* Wenn Sie die Eclipse-integrierte Entwicklungsumgebung für Eclipse verwenden, können Sie AEM-Developer Tools für eine nahtlose Integration der Eclipse IDE mit AEM-Instanzen verwenden und AEM-Apps erstellen. Weitere Informationen finden Sie unter[ AEM-Developer Tools für Eclipse](/help/sites-developing/aem-eclipse.md).

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Wenn Sie Pakete zum Verschieben von Inhalten erstellen, stellen Sie sicher, dass Paketfilterpfade korrekt sind und nur erforderliche Pfade erwähnt werden.

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Definieren Sie die richtigen Abhängigkeiten für die Pakete, um eine vorab festgelegte Installationsreihenfolge zu erzwingen.

* Erstellen Sie keinen referenzierbaren Knoten in /libs oder /apps.

### Planen der Authoring-Umgebung {#planning-for-authoring-environment}

Nachdem Sie Ihr AEM-Projekt eingerichtet haben, definieren Sie eine Strategie für das Erstellen und Anpassen von Vorlagen für adaptive Formulare und Komponenten.

* Eine adaptive Formularvorlage ist eine spezielle AEM-Seite, die Struktur und die Informationen für Kopfzeile und Fußzeile eines adaptiven Formulars definiert. Eine Vorlage hat vorkonfigurierte Layouts, Stile und eine einfache Struktur für ein adaptives Formular. AEM Forms bietet Standardvorlagen und -Komponenten, die Sie verwenden können, um adaptive Formulare zu erstellen. Sie haben jedoch die Möglichkeit, benutzerdefinierte Vorlagen und Komponenten entsprechend Ihrer Anforderungen zu erstellen. Es wird empfohlen, Anforderungen für zusätzliche Vorlagen und Komponenten zu erfassen, die Sie in Ihren adaptiven Formularen benötigen. Weitere Informationen finden Sie unter[ Anpassen von adaptiven Formularen und Komponenten](/help/forms/using/adaptive-forms-best-practices.md#customize-components).
* Mit AEM Forms können Sie adaptive Formulare erstellen, die auf den folgenden Formularmodellen basieren. Die Formularmodelle fungieren als Schnittstelle für den Datenaustausch zwischen einem Formular und einem AEM-System und liefern eine XML-basierte Struktur für Datenfluss innerhalb und außerhalb eines adaptiven Formulars. Die Formularmodelle legen die Regeln und Beschränkungen für adaptive Formulare in dem Formular von Schema- und XFA-Beschränkungen fest.

   * **Ohne**: Die adaptiven Formulare, die mit dieser Option erstellt worden sind, verwenden kein Datenmodell. Die XML-Datendatei, die aus diesen Formularen generiert wurde, hat eine flache Struktur mit Feldern und entsprechenden Werten.
   * **XML- oder JSON-Schema**: XML- und JSON-Schema stellen die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können ein Schema mit einem adaptiven Formular verknüpfen und mit dessen Elementen dem adaptiven Formular dynamische Inhalte hinzufügen. Die Elemente des Schemas stehen auf der Registerkarte &quot;Datenmodellobjekt&quot;des Inhaltsbrowsers zum Authoring adaptiver Formulare zur Verfügung. Sie können die Schemaelemente zum Erstellen des Formulars ziehen und ablegen.
   * **XFA-Formularvorlage**: Es ist ein optimales Datenmodell, wenn Sie Investitionen in XFA-basierten HTML5-Formularen haben. Es bietet eine direkte Möglichkeit, Ihre XFA-basierten Formulare in adaptive Formulare zu konvertieren. Alle vorhandenen XFA-Regeln werden in den zugehörigen adaptiven Formularen beibehalten. Die resultierenden adaptiven Formulare unterstützen XFA-Konstrukte, z. B. Überprüfungen, Ereignisse, Eigenschaften und Muster.
   * **Formulardatenmodell**: Es ist ein bevorzugtes Formularmodell, wenn Sie Backend-Profile wie Datenbanken, Webdienste und AEM benutzerspezifischen  integrieren möchten, um adaptive Formulare im Voraus auszufüllen und gesendete Formulardaten in Backend-Systeme zu schreiben. Verwendung eines Formulardatenmodells Datenintegration ermöglicht die Integration von Entitäten und Diensten aus unterschiedlichen Datenquellen in ein Formulardatenmodell, das Sie zum Erstellen adaptiver Formulare verwenden können. Weitere Informationen finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

Es ist wichtig, das Datenmodell mit Bedacht auszuwählen, das nicht nur Ihren Anforderungen entspricht, aber Ihre bereits getätigten Investitionen in XSD-Asset XFA-Assets erweitert. Es wird empfohlen, das XSD-Modell zu verwenden, um Formularvorlagen zu erstellen, weil die generiert XML-Daten enthält, die per XPFAD vom Schema definiert wurden. Die Verwendung des XSD-Modells als Standardauswahl für das Formulardatenmodell hilft auch dabei, weil es das Formulardesign vom Backendsystem abkoppelt, das Daten verarbeitet und verbraucht und es verbessert die Leistung des Formulard, wegen der One-to-One-Zuweisung des Formularfelds. BindRef des Felds kann auch aus dem XPFAD seines Datenwerts in XML gemacht werden.

Weitere Informationen finden Sie unter[ Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

* Es gibt einige allgemeine Abschnitte über adaptive Formulare. Sie müssen diese Bereiche identifizieren und eine Strategie definieren, um die Wiederverwendung von Inhalten zu fördern. Adaptive Formulare bieten Ihnen die Möglichkeit, eigenständige Fragment zu erstellen und sie in allen Formularen wiederzuverwenden. Sie können auch einen Bereich in einem adaptiven Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen Formularen dargestellt. Dies hilft Ihnen, die Authoring-Zeit zu reduzieren und stellt Konsistenz in allen Formularen sicher. Darüber hinaus macht die Verwendung von Fragmenten adaptive Formulare einfach und führt deshalb zu einer verbesserten Authoring-Erfahrung, insbesondere für größere Formulare. Weitere Informationen finden Sie unter [Adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md).

### Anpassen adaptiver Formulare und Komponenten {#customize-components}

* Die AEM Forms-Installation bietet verschiedene integrierte Vorlagen für adaptive Formulare, die Sie verwenden können, um adaptive Formulare zu erstellen. Sie können auch Ihre eigenen Vorlagen erstellen. AEM bietet die statischen und bearbeitbaren Vorlagen.

   * Statische Vorlagen werden von den Entwicklern definiert und konfiguriert.
   * Bearbeitbare Vorlagen werden von Autoren mit Hilfe des Vorlageneditors erstellt. Mit dem Vorlageneditor können Sie eine Grundstruktur und den anfänglichen Inhalt einer Vorlage definieren. Jede Änderung in der Strukturebene wird in allen Formularen, die diese Vorlage verwenden, berücksichtigt. Der anfängliche Inhalt kann vorkonfigurierte Designs, Vorfülldienste, Sendeaktionen usw. umfassen. Diese Einstellungen können jedoch mit dem Formular-Editor für ein Formular geändert werden. Weitere Informationen finden Sie unter [Vorlagen für adaptive Formulare](/help/forms/using/template-editor.md).

* Zum Formatieren einer bestimmten Feld- oder Bereichsinstanz verwenden Sie [Inline-Formatierung](/help/forms/using/inline-style-adaptive-forms.md). Alternativ dazu können Sie eine Klasse in einer CSS-Datei definieren und den Klassennamen in der CSS-Klasseneigenschaft der Komponente angeben.
* Verknüpfen Sie eine Client-Bibliothek in einer Komponente, um Stile in allen adaptiven Formularen oder Fragmenten konsistent anzuwenden, die diese Komponente verwenden. Weitere Informationen finden Sie unter[ Erstellen einer adaptiven Formularseitenkomponente](/help/forms/using/custom-adaptive-forms-templates.md).
* Wenden Sie die Stile an, die in einer Client-Bibliothek definiert werden, um adaptive Formulare auszuwählen, indem Sie den Pfad zur Client-Bibliothek im CSS-Datei-Pfadfeld in den Eigenschaften für den adaptiven Forrmularcontainer angeben.
* Um eine Client-Bibliothek ihrer Stile zu erstellen, können Sie die benutzerdefinierte CSS-Datei im Design-Editor oder im Formularcontainer konfigurieren.
* Adaptive Formulare bieten Bereichslayouts, z. B. Responsive Layouts, Bedienfelder mit Registerkarten, Akkordeons und Assistenten, um zu steuern, wie Formularkomponenten in einem Bereich angeordnet werden. Sie können benutzerdefinierte Bedienfeldlayouts erstellen und für Formularverfasser verfügbar machen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Layoutkomponenten für adaptive Formulare](/help/forms/using/custom-layout-components-forms.md).
* Sie können auch bestimmte adaptive Formularkomponenten wie Felder und das Bedienfeldlayout anpassen.

   * Verwenden Sie die[ Überlagerungs](/help/sites-developing/overlays.md)-Funktion von AEM, um eine Kopie einer Komponente zu ändern. Es wird nicht empfohlen, die Standardkomponenten zu ändern.
   * Um das Layout von adaptiven Standardformularkomponenten von in /libs anzupassen,[ erstellen Sie benutzerdefinierte Layoutkomponenten](/help/forms/using/custom-layout-components-forms.md) zusätzlich zu den[ Standardlayouts](/help/forms/using/layout-capabilities-adaptive-forms.md).
   * Führen Sie benutzerdefinierte Interaktivitäten ein, indem Sie benutzerdefinierte Widgets oder Erscheinungsbilder erstellen. Es wird nicht empfohlen, die Standardkomponenten zu ändern. Weitere Informationen finden Sie unter[ Framework für Erscheinungsbild](/help/forms/using/introduction-widgets.md).

* Weitere Informationen finden Sie unter[ Bearbeiten von persönlichen identifizierbaren Informationen](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) für Vorschläge zum Umgang mit PII-Daten.

## Adaptive Verfasserformulare {#author-adaptive-forms}

### Verwendung touch-optimierter Benutzeroberflächen für die Bearbeitung {#using-touch-optimized-ui-for-authoring}

* Verwenden Sie den Browser &quot;Objekte&quot;in der Seitenleiste, um schnell auf Felder in der Formularhierarchie zuzugreifen. Sie können im Suchfeld nach Objekten in der Formular- oder Objektstruktur, um von einem Objekt zu einem anderen zu navigieren.
* Um die Eigenschaften einer Komponente im Komponentenbrowser in der Seitenleiste Ansicht und zu bearbeiten, wählen Sie die Komponente aus und klicken Sie auf ![cmppr-1](assets/cmppr-1.png). Sie können auch auf eine Komponente doppelkicken, um ihre Eigenschaften im Eigenschaftenbrowser anzuzeigen.
* Verwenden Sie die Tastaturkürzel, um schnelle Aktionen in Ihren Formularen durchzuführen. Siehe [AEM Forms-Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md).

* Adaptive Formularkomponenten werden für die Verwendung nur in adaptiven Formularseiten empfohlen. Die Komponenten haben Abhängigkeiten von ihrer übergeordneten Hierarchie. Daher dürfen Sie diese nicht auf der AEM-Seite verwenden.

Weitere Informationen finden Sie außerdem in „Komponentenbeschreibungen und optimale Verfahren“ in [Einführung zum Erstellen adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

### Verwenden von Regeln in adaptiven Formularen  {#using-rules-in-adaptive-forms}

AEM Forms bietet einen [Regeleditor](/help/forms/using/rule-editor.md), der es Ihnen ermöglicht, Regeln zu erstellen, um dynamisches Verhalten zu adaptiven Formularkomponenten hinzuzufügen. Mithilfe dieser Regeln können Sie Bedingungen und Trigger-Aktionen für Komponenten auswerten, z. B. Felder ein- oder ausblenden, Werte berechnen, Dropdown-Listen dynamisch ändern usw.

Der Regeleditor bietet einen visuellen Editor und einen Code-Editor für Schreibregeln. Achten Sie auf Folgendes, wenn Sie Schreibregeln mit dem Code-Editormodus verwenden:

* Verwenden Sie eindeutige Namen aussagekräftig und Formularfelder und Komponenten, damit alle möglichen Konflikten während Schreibregeln vermeiden.
* Verwenden Sie für eine Komponente den Operator `this`, um sich in einem Regel-Ausdruck zu referenzieren. Es wird sichergestellt, dass die Regel gültig bleibt, selbst wenn sich der Komponentenname ändert. Beispiel: `field1.valueCommit script: this.value > 10`.

* Verwenden Sie Komponentennamen, wenn Sie auf verschiedene Formularkomponenten verweisen. Verwenden Sie die Eigenschaft `value`, um den Wert eines Felds oder einer Komponente abzurufen. Beispiel: `field1.value`.

* Verweisen Sie auf Komponenten durch die relative eindeutige Hierarchie, um Konflikte zu vermeiden. Beispiel: `parentName.fieldName`.

* Wenn Sie komplexe oder häufig verwendete Regeln bearbeiten, sollten Sie die Geschäftslogik als Funktionen in einer separaten Client-Bibliothek schreiben, die Sie für adaptive Formulare angeben und wiederverwenden können. Die Client-Bibliothek sollte eine eigenständige Bibliothek sein und darf keine externen Abhängigkeiten, außer von jQuery und Underscore.js haben. Sie können auch die Client-Bibliothek verwenden, um die [serverseitige Überprüfung](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) der gesendeten Formulardaten zu erzwingen.
* Adaptive Formulare bieten eine Reihe von APIs, die Sie verwenden können, um zu kommunizieren und Aktionen auf adaptiven Formularen anzuzeigen. Einige Schlüssel-APIs lauten wie folgt: Weitere Informationen finden Sie unter[ JavaScript-Bibliotheks-API-Referenz für adaptive Formulare](https://adobe.com/go/learn_aemforms_documentation_63).

   * `guideBridge.reset()`: Setzt ein Formular zurück.
   * `guideBridge.submit()`: Sendet ein Formular.
   * `guideBridge.setFocus(somExp, focusOption, runCompletionExp)`: Legt den Fokus auf ein Feld fest.
   * `guideBridge.validate(errorList, somExpression, focus)`: Überprüft ein Formular.
   * `guideBridge.getDataXML(options)`: Ruft Formulardaten als XML ab.
   * `guideBridge.resolveNode(somExpression)`: Ruft ein Formularobjekt ab.
   * `guideBridge.setProperty(somList, propertyName, valueList)`: Legt die Eigenschaft eines Formularobjekts fest.
   * Darüber hinaus können Sie die folgenden Feldeigenschaften verwenden:

      * `field.value`, um den Wert eines Felds zu ändern.
      * f`ield.enabled`, um ein Feld zu aktivieren.
      * `field.visible`, um die Sichtbarkeit eines Felds zu ändern. 

* Autoren für adaptive Formulare müssen möglicherweise JavaSript-Code schreiben, um Businesslogik in ein Formular zu integrieren. JavaScript ist zwar leistungsstark und effektiv, aber kann die Sicherheit beeinflussen.  Daher müssen Sie sicherstellen, dass der Formularautor eine vertrauenswürdige Person ist und Prozesse zum Review und zur Genehmigung von JavaScript-Code bereitgestellt werden, bevor Sie ein Formular verwenden. Der Administrator kann den Zugriff auf den Regeleditor auf Benutzergruppen entsprechend ihrer Rolle oder Funktion beschränken. Siehe [Ausgewählten Benutzern Zugriff auf den Regel-Editor gewähren](/help/forms/using/rule-editor-access-user-groups.md).
* Sie können Ausdrücke in Regeln verwenden, um adaptive Formulareigenschaften zu erstellen. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Weitere Informationen zu Ausdrücken und optimalen Verfahren finden Sie unter[ Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md). 

### Arbeiten mit Designs {#working-with-themes}

Mit „Adaptive für Designs“ können Sie wiederverwendbare Stile erstellen, die über alle Formulare hinweg angewendet werden können, um ein einheitliches Aussehen und Stile zu erzielen. Es wird empfohlen,  Designs zu verwenden, um Formatierung für Formularkomponenten und Bedienfelder zu definieren. Einige optimale Verfahren zu Designs lauten wie folgt:

* Nutzen Sie die Asset-Bibliothek für die schnelle Anwendung von Textstilen, Hintergründen und Bildern. Wenn ein Stil in der Asset-Bibliothek hinzugefügt wird, steht er für andere Designs und im Stil-Modus des Formular-Editors zur Verfügung.
* Wenden Sie globale Einstellungen wie Schriftart und Seitenhintergrund mithilfe der Seitenebenenauswahl an.
* Verwenden Sie Client-Bibliotheken, um vorhandene oder erweiterte Stile in Ihre Designs zu importieren.
* Sie können Stile für bestimmte Felder, Bereiche oder Schaltflächen in einer Formularstilebene außer Kraft setzen. 
* Wenn ein Design nicht die Formatierungsanforderungen erfüllt, können Sie vordefinierte Klassen wie guideFieldNode, guideFieldLabel, guideFieldWidget und guidePanelNode verwenden, um häufige Stile auf allen Formularen anzuwenden.

Weitere Informationen finden Sie unter [Designanpassung](/help/forms/using/themes.md).

### Optimieren der Leistung von großen und komplexen Formularen  {#optimizing-performance-of-large-and-complex-forms}

Formularverfasser und Benutzer werden normalerweise mit Leistungsproblemen konfrontiert, wenn große Formulare im Bearbeitungsmodus oder zur Laufzeit geladen werden. Wenn die Anzahl der Objekte (Felder und Bereiche) in den Formularen zunimmt, nimmt die Authoring- und Laufzeiterfahrung ab. Es wird außerdem verhindert, dass mehrere Autoren gleichzeitig zusammenzuarbeiten und ein Formular zusammen bearbeiten.

Beachten Sie die folgenden bewährten Verfahren, um, Leistungsprobleme mit großen Formularen zu vermeiden:

* Es wird empfohlen, adaptive Formulare mithilfe von XSD-Formulardatenmodellen zu erstellen, selbst bei Konvertierung einer XFA in ein adaptives Formular. 
* Schließen Sie nur die Felder und Bereiche in adaptiven Formularen, die Informationen vom Benutzer erfassen. Beachten Sie, dass statischer Inhalt gering gehalten werden muss oder verwenden Sie URLs, um sie in einem separaten Fenster zu öffnen.
* Während jedes Formular für einen bestimmten Zweck entwickelt wurde, gibt es einige häufige Segmente in den meisten Formularen. Beispielsweise persönliche Details, Adressen, Beschäftigungsdetails usw. Erstellen Sie [adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md) für allgemeine Formularelemente und -abschnitte und verwenden Sie sie für alle Formulare. Sie können auch einen Bereich in einem vorhandenen Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen adaptiven Formularen dargestellt. Es unterstützt gemeinsames Authoring, da mehrere Verfasser an verschiedenen Fragmenten, die ein Formular bilden, gleichzeitig arbeiten können.

   * Ähnlich wie in adaptiven Formularen, wird empfohlen, dass alle fragmentspezifischen Stile und benutzerdefinierte Skripte in der Client-Bibliothek mithilfe des Dialogfelds „Fragmentcontainer“ definiert werden. Außerdem sollten Sie eigenständige Fragmente erstellen, die nicht von Objekten außerhalb der Komponente abhängen.
   * Außerdem sollten Sie Cross-Fragments-Skripterstellung vermeiden. Wenn es ein Objekt außerhalb des Fragments gibt, auf das Sie verweisen möchten, müssen Sie das Objekt als Teil des übergeordneten Formulars einarbeiten. Wenn das Objekt in einem anderen Fragmente bleiben muss, verweisen Sie darauf durch seinen Namen in dem Skript..

* Verwenden Sie „Speichern“ und „Fortsetzen“ mit einer automatischen Speicherung, um das adaptive Formular periodisch zu speichern und den Benutzern zu ermöglichen, das Formular später erneut zu öffnen, um es zu vervollständigen.
* Konfigurieren Sie Fragmente, um sie verzögert zu laden. Fragmente, die zur Laufzeit als „Verzögert laden“ markiert sind, werden nur gerendert, wenn sie erforderlich sind. Die Ladezeit für große Formulare wird dadurch erheblich reduziert. Es wird außerdem in Fragmenten mit wiederholbaren Bereichen unterstützt. Weitere Informationen finden Sie unter [ Konfigurieren von verzögertem Laden](/help/forms/using/lazy-loading-adaptive-forms.md).

   * Konfigurieren Sie kein verzögertes Laden in Fragmenten in einem Responsive-Rasterlayout oder in dem ersten Bereich.
   * In verzögert geladenen Fragmenten werden keine Komponenten für Dateianlagen und Geschäftsbedingungen unterstützt.
   * Markieren Sie einen Wert in einem verzögerten geladenen Bereich als „Wert global verwenden“, wenn dieser Wert in einem anderen Teil des Formulars verwendet wird, sodass der Wert für die Verwendung verfügbar ist, wenn der enthaltene Bereich entladen wird.
   * Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen.

### Vorbefüllen von adaptiven Formularen  {#prefilling-adaptive-forms}

Sie können adaptive Formularfelder mit Daten aus dem Backend vorbefüllen, um Benutzern zu helfen, das Formular schnell auszufüllen und Tippfehler zu vermeiden.

* AEM Forms bietet einen Prefill-Dienst, um Daten aus einer vordefinierten Daten-XML-Datei zu lesen und die Felder eines adaptiven Formulars mit dem Inhalt der Prefill-XML-Datei vorzubefüllen.
* Die Prefill-Daten XML muss mit dem Schema des Formularmodells, das mit dem adaptiven Formular verknüpft ist, konform sein.
* Schließen Sie die Abschnitte`afBoundedData`   und`afUnBoundedData`   in die Prefill-XML zum Vorbefüllen von gebundenen und ungebundenen Feldern in einem adaptiven Formular ein.

* Für adaptive Formulare, die auf dem Formulardatenmodell basieren, stellt AEM Forms den vordefinierten Formulardatenmodellvorfülldienst bereit. Der Prefill-Dienst fragt nach Datenquellen für Datenmodellobjekte im adaptiven Formular und befüllt Feldwerte beim Rendern des Formulars.
* Sie können auch die Protokolle file, crx, service oder http verwenden, um adaptive Formulare vorzubefüllen.
* AEM Forms unterstützt benutzerdefinierte Prefill-Dienste, die Sie als OSGi-Dienst einbinden können, um adaptive Formulare vorzubefüllen.

Weitere Informationen finden Sie unter [Vorfüllen von Feldern in adaptiven Formularen](/help/forms/using/prepopulate-adaptive-form-fields.md).

### Adaptive Formulare signieren und senden {#signing-and-submitting-adaptive-forms}

Adaptive Formulare benötigen Übermittlungsaktionen für die Verarbeitung der von Benutzern angegebenen Daten. Eine Übermittlungsaktion bestimmt die Aufgabe der Daten, die Sie mit einem adaptiven Formular senden.

* Es gibt mehrere Sendeaktionen, die in adaptiven Formularen sofort verfügbar sind. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md).
* Sie können eine benutzerdefinierte Sendeaktion schreiben, wenn die standardmäßigen Sendeaktionen Ihren Anwendungsfall nicht erfüllen. Weitere Informationen finden Sie unter[ Schreiben von benutzerdefinierten Übermittlungsaktionen für ein adaptives Formular](/help/forms/using/custom-submit-action-form.md).
* Beziehen Sie serverseitige Validierungen ein, um zu verhindern, dass ungültige Daten übermittelt werden. 

Sie können die Funktion der mehrfachen Signaturen von Adobe Sign in adaptiven Formularen nutzen. Beachten Sie die folgenden Punkte bei der Konfiguration von Adobe Sign in adaptiven Formularen. Weitere Informationen finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

* Adobe Sign-aktiviertes Formular wird nur gesendet, nachdem alle Unterzeichner das Formular unterzeichnet haben. Forms wird im Status &quot;Ausstehende Unterschrift&quot;angezeigt, bis das Formular von allen Unterzeichnern unterzeichnet wurde.
* Sie können die Funktion des Unterzeichnens im Formular konfigurieren oder Unterzeichner auf eine neue Signaturseite beim Senden umleiten.
* Konfigurieren Sie je nach Bedarf sequentielle oder parallele Signaturfunktionen.

### Generieren von Dokument aus Datensatz  {#generating-document-of-record}

Ein Dokument aus Datensatz (DoR) ist eine komprimierte PDF-Version eines adaptiven Formulars, die gedruckt, signiert oder archiviert werden kann.

* Je nach dem Formular-Datenmodell, auf dem ein adaptives Formular basiert, können Sie eine Vorlage für DoR wie folgt konfigurieren:

   * **XFA-Formularvorlage**: Verwenden Sie die zugeordnete XDP-Datei als DoR-Vorlage.
   * **XSD-Schema**: Verwenden Sie die zugeordnete XFA-Vorlage, die das gleiche Schema wie das adaptive Formular verwendet.
   * **Ohne**: Verwenden Sie automatisch generierte DoR.

* Konfigurieren Sie Kopf- und Fußzeile, Bilder, Farbe, Schriftart usw. direkt auf der Registerkarte „Datensatzdokument“ des adaptiven Formular-Editors.
* Verwenden Sie`DoRService` , , um das DoR programmatisch zu generieren.
* Ausgeblendete Felder aus DoR ausschließen.
* Verwenden Sie den Anforderungsparameter `afAcceptLang`, um DoR in einem anderen Gebietsschema Ansicht.

### Debuggen und Testen von adaptiven Formularen {#debugging-and-testing-adaptive-forms}

Das [AEM Chrome Plugin](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) ist eine Browsererweiterung für Google Chrome, die Tools zum Debugging adaptiver Formulare bereitstellt. Formularautoren und Entwickler können diese Tool für Folgendes verwenden:

* Identifizieren von Engpässen und Optimieren von Leistung von Formularwiedergabe
* Debuggen von Schlüsselwörtern und bindRef-Fehler in Formularen
* Aktivieren und Konfigurieren von Protokollen
* Debuggen von Regeln und Skripten in Formularen
* Durchsuchen und erfahren Sie mehr über guideBridge APIs

Weitere Informationen finden Sie unter [AEM Chrome-Plugin - Adaptives Formular](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/).

Calvin SDK ist eine Dienstprogramm-API für Entwickler von adaptiven Formularen zum Testen von adaptiven Formularen. Calvin SDK basiert auf dem Testframework [Hobbes.js](https://docs.adobe.com/docs/de/aem/6-3/develop/ref/test-api/index.html). Sie können den Rahmen verwenden, um Folgendes zu testen:

* Wiedergabefunktionen eines adaptiven Formulars
* Befüllen eines adaptiven Formulars
* Übertragen eines adaptiven Formulars
* Ausdrucksregeln
* Validierungen
* Verzögertes Laden

Weitere Informationen finden Sie unter[ Automatisieren von Tests für adaptive Formulare](/help/forms/using/calvin.md).

### Validieren von adaptiven Formularen auf dem AEM-Server  {#validating-adaptive-forms-on-aem-server}

Serverseitige Überprüfungen sind erforderlich, um alle Versuche zu verhindern, die Überprüfungen auf dem Client und mögliche Gefahren von Datenübertragungen und Verletzungen von Geschäftsregeln umgehen wollen. Serverseitige Überprüfungen werden auf dem Server ausgeführt, indem die erforderliche Client-Bibliothek geladen wird.

* Schließen Sie Funktionen in einer Client-Bibliothek für die Validierung von Ausdrücken in adaptiven Formularen ein und legen Sie die Client-Bibliothek im Dialogfeld von adaptiven Formularcontainern fest. Weitere Informationen finden Sie unter[ Serverseitige erneute Überprüfung](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p).
* Serverseitige Überprüfung überprüft das Formularmodell. Es wird empfohlen, eine separate Client-Bibliothek für Überprüfungen zu erstellen und sie nicht mit anderen Elementen wie HTML-Stil und DOM-Manipulation in derselben Client-Bibliothek zu mischen.

### Lokalisieren von adaptiven Formularen  {#localizing-adaptive-forms}

AEM bietet Übersetzungsarbeitsläufe, die Sie zur Lokalisierung adaptiver Formulare verwenden können. Siehe [Verwenden von AEM-Übersetzungs-Workflow zum Lokalisieren von adaptiven Formularen](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).

Einige empfohlene Vorgehensweisen beim Lokalisieren adaptiver Formulare lauten wie folgt:

* Verwenden Sie adaptive Formularfragmente für allgemeine Elemente in Formularen und lokalisieren Sie Fragmente. Das stellt sicher, dass Sie ein Fragment einmal lokalisieren und es wird in allen Formularen reflektiert, in denen das Fragment verwendet wird.
* Alle Modifizierungen wie das Hinzufügen einer neuen Komponente oder das Anwenden eines Skripts in einem lokalisierten Formular, werden nicht automatisch lokalisiert. Daher müssen Sie ein Formular vor der Lokalisierung fertigstellen, um mehrere lokale Anpassungen zu vermeiden.
* Verwenden Sie den Anforderungsparameter `afAcceptLang` , , um das Browsergebietsschemazu überschreiben und das Formular in einem spezifischen Gebietsschema zu lokalisieren. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im japanischen Gebietsschema, unabhängig vom in der Browsereinstellung angegebenen Gebietsschema:

   `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms unterstützt derzeit die lokale Anpassung von Inhalten für adaptive Formulare in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (es), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR), Chinesisch (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können jedoch neuen Support für neue Gebietsschemata für adaptive Formulare zur Laufzeit hinzufügen. Weitere Informationen finden Sie unter [Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen](/help/forms/using/supporting-new-language-localization.md).

## Vorbereiten von Formularprojekten für die Produktion  {#prepare-forms-project-for-production}

### Hinzufügen eines Formularverarbeitungsservers {#adding-forms-processing-server}

Sie können eine weitere Instanz des AEM-Forms-Servers konfigurieren, der sich hinter der Firewall in einem geschützten Bereich befindet. Sie können diese Instanz für Folgendes verwenden:

* **Stapelverarbeitung**: Aufträge, die in Stapeln mit hoher Last wiederholt oder geplant werden. Beispielsweise das Drucken von Anweisungen, das Generieren von Schriftstücken und die Verwendung von Dokumentdiensten wie PDF Generator, Output und Assembler.
* **Speichern von PII-Daten**: Speichern Sie PII-Daten auf dem Verarbeitungsserver. Es ist nicht erforderlich, wenn Sie bereits benutzerdefinierte Speicheranbieter zum Speichern von PII-Daten verwenden.

### Verschieben eines Projekts in eine andere Umgebung  {#moving-project-to-another-environment}

Oft müssen Sie AEM-Projekte aus einer Umgebung in eine andere verschieben. Einige der wichtigsten Aspekte beim Verschieben lauten wie folgt:

* Erstellen Sie eine Sicherungskopie der vorhandenen Client-Bibliotheken, des benutzerdefinierten Codes und der Konfigurationen.
* Stellen Sie Produktpakete und Patches manuell bereit und in der angegebenen Reihenfolge in der neuen Umgebung bereit.
* Stellen Sie projektspezifische Codepakete und Bundles manuell und als separates Paket oder Bundle auf dem neuen AEM-Server bereit.
* (*Nur AEM Forms on JEE*) Stellen Sie LCAs und DSCs manuell auf dem Forms Workflow bereit.
* Verwenden Sie[ Export-Import](/help/forms/using/import-export-forms-templates.md)-Funktionen, um Elemente in die neue Umgebung zu verschieben. Sie können auch den Replizierungsagenten konfigurieren und Assets veröffentlichen.
* Ersetzen Sie beim Upgrade alle nicht mehr unterstützten APIs und Funktionen durch neue APIs und Funktionen.

### Konfigurieren von AEM {#configuring-aem}

Im Folgenden werden einige bewährte Verfahren zum Konfigurieren von AEM zur Verbesserung der Gesamtleistung gezeigt:

* Aktivieren Sie HTML-Client-Bibliothekskomprimierung für JavaScript und CSS-Code aus der Felix-Konsole. Siehe [Clientlibs erklärt durch Beispiel](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/).
* Zwischenspeichern Sie alle Client-Bibliotheken unter `/etc.clientlibs/fd` und alle weiteren benutzerdefinierten Client-Bibliotheken auf AEM Dispatcher, um die Reaktionsgeschwindigkeit und Sicherheit Ihrer veröffentlichten Formulare zu erhöhen. Weitere Informationen finden Sie unter [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)

* Zwischenspeichern Sie die Pfade `/content/forms/af/` und `/content/dam/formsanddocuments/*` nicht. Weitere Informationen zum Konfigurieren der Zwischenspeicherung adaptiver Formulare finden Sie unter [Zwischenspeichern adaptiver Formulare](/help/forms/using/configure-adaptive-forms-cache.md).

* Aktivieren Sie HTML über das Webserverkomprimierungsmodul. Weitere Informationen finden Sie im Abschnitt [Leistungsoptimierung des AEM-Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Erhöhen Sie Aufrufe für die Anforderungskonfiguration für große Formulare. Siehe[ Optimieren der Leistung von großen und komplexen Formularen](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Erstellen Sie[ benutzerdefinierte Fehlerseiten, die vom Fehler-Handler angezeigt werden](https://helpx.adobe.com/experience-manager/6-2/sites-developing/customizing-errorhandler-pages.html).
* Sichere AEM Forms-Server.

   * Verwenden Sie `nosamplecontent`-Laufzeitmodus unter, um sicherzustellen, dass die Anwendung keine Beispielinhalte und Beispielbenutzer enthält, die auf dem Produktionsserver bereitgestellt werden. Siehe [Ausführen AEM im produktionsfertigen Modus](/help/sites-administering/production-ready.md).

* Halten Sie die Heapgröße auf einem Minimum von 8 GB. Für andere Einstellungen finden Sie weitere Informationen im Abschnitt [Leistungsoptimierung des AEM-Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Verwenden Sie Service-Benutzersitzungen anstatt Admin-Sitzungen zum Ausführen von Aufgaben auf Serverebene. Weitere Informationen finden Sie unter [ Dienstauthentifizierung](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html).

>[!VIDEO](https://vimeo.com/)

### Konfigurieren von externem Speicher für Entwürfe und eingereichte Formulardaten {#external-storage}

In einer Produktionsumgebung wird empfohlen, eingereichte Formulardaten nicht im AEM-Repository zu speichern. Die Standardimplementierung von Sendeaktionen wie Formularportalspeicher, Inhaltsspeicher und PDF-Speicher speichert Formulardaten im AEM-Repository. Diese Sendeaktionen sind nur für Demozwecke geeignet. Die Funktionen „Speichern und fortsetzen“ und Automatische Speicherung“ verwenden auch standardmäßig Portalspeicher. Beachten Sie daher folgende Empfehlungen:

* **Speichern von Entwurfsdaten**: Wenn Sie die Funktion „Entwurf“ in ein adaptiven Formularen verwenden, müssen Sie eine benutzerdefinierte Service Provide Interface (Dienstanbieterbenutzeroberfläche, SPI) verwenden, um Entwurfsdaten in einem sichereren Speicher wie in einer Datenbank zu speichern. Weitere Informationen finden Sie unter [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

* **Speichern von Übermittlungsdaten**: Wenn Sie den Form Portal Submit Store verwenden, sollten Sie eine benutzerdefinierte SPI implementieren, um die Sendungsdaten in einer Datenbank zu speichern. Eine Beispielintegration finden Sie unter [Beispiel für die Integration der Komponente &quot;Drafts &amp; Submissions&quot;in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

   Sie können auch eine benutzerdefinierte Übermittlungsaktion schreiben, die Formulardaten und Anhänge in einem sicheren Speicher speichert. Weitere Informationen finden Sie unter [Schreiben von benutzerdefinierten Übermittlungsaktionen für adaptive Formulare](/help/forms/using/custom-submit-action-form.md).

* **Länge der Entwurfs-ID**: Wenn Sie ein adaptives Formular als Entwurf speichern, wird eine Entwurfs-ID generiert, um den Entwurf eindeutig zu identifizieren. Der Mindestwert für die Länge des Entwurfs-ID-Felds beträgt 26 Zeichen. Adobe empfiehlt, die Entwurfslänge der ID auf 26 Zeichen oder mehr festzulegen.

### Bearbeiten von persönlichen identifizierbaren Informationen {#handling-personally-identifiable-information}

Eine der Hauptherausforderungen für Unternehmen ist es, wie persönliche identifizierbare Informationen (PII) bearbeitet werden. Einige bewährte Verfahren, die Ihnen dabei helfen, diese Daten zu bearbeiten, lauten wie folgt:

* Verwenden Sie einen sicheren externen Speicherort wie eine Datenbank, um Daten aus dem Entwurf und dem übermittelten Formular zu speichern. Siehe [Externe Datenspeicherung für Entwürfe und gesendete Formulardaten konfigurieren](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* Verwenden Sie die Formularkomponente „Bedingungen“, um die ausdrückliche Zustimmung des Benutzers zu erhalten, bevor die automatische Speicherung aktiviert wird. In diesem Fall können Sie die automatische Speicherung nur aktivieren, wenn der Benutzer den Bedingungen in der Komponente zustimmt.

