---
title: Best Practices für die Arbeit mit adaptiven Formularen
seo-title: Best practices for working with adaptive forms
description: Erläutert Best Practices für die Einrichtung eines AEM Forms-Projekts, die Entwicklung adaptiver Formulare und die Optimierung der Leistung für das AEM Forms-System.
seo-description: Explains best practices for setting up an AEM Forms project, developing adaptive forms, and optimizing the performance for AEM Forms system.
uuid: ed95fc64-56b3-4ea1-a5ba-2e96953fca56
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 43c431e4-5286-4f4e-b94f-5a7451c4a22c
feature: Adaptive Forms
exl-id: 5c75ce70-983e-4431-a13f-2c4c219e8dde
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '4586'
ht-degree: 47%

---

# Best Practices für die Arbeit mit adaptiven Formularen {#best-practices-for-working-with-adaptive-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

## Übersicht {#overview}

Mit Adobe Experience Manager-Formularen (AEM) können Sie komplexe Transaktionen in einfache, angenehme digitale Erlebnisse umwandeln. Es erfordert jedoch konzertierte Bemühungen, ein effizientes und produktives AEM Forms-Ökosystem zu implementieren, zu erstellen, auszuführen und zu warten.

Dieses Dokument enthält Vorgaben und Empfehlungen, von denen Forms-Administratoren, Verfasser und Entwickler profitieren können, wenn sie mit AEM Forms und insbesondere mit adaptiven Formularkomponenten arbeiten. Es beschreibt bewährte Verfahren vom Einrichten eines Formularentwicklungsprojekts bis zum Konfigurieren, Anpassen, Authoring und Optimieren von AEM Forms. Diese bewährten Verfahren tragen zusammen zur Gesamtleistung des AEM Forms-Systems bei.

Darüber hinaus finden Sie hier einige Informationen für bewährte Verfahren zu AEM:

* [Bewährte Verfahren: Bereitstellung und Wartung von AEM ](/help/sites-deploying/best-practices.md)
* [Bewährte Verfahren: Erstellen von Inhalten ](/help/sites-authoring/best-practices.md)
* [Bewährte Verfahren: Verwaltung von AEM ](/help/sites-administering/administer-best-practices.md)
* [Bewährte Verfahren: Entwicklung von Lösungen ](/help/sites-developing/best-practices.md)

## Einrichten und Konfigurieren von AEM Forms {#set-up-and-configure-aem-forms}

### Einrichten eines Formularentwicklungsprojekts {#setting-up-forms-development-project}

Eine vereinfachte und standardisierte Projektstruktur kann den Entwicklungs- und Wartungsaufwand erheblich reduzieren. Apache Maven ist ein Open-Source-Tool, das zum Erstellen AEM Projekte empfohlen wird.

* Verwenden Sie Apache Maven `aem-project-archetype`, um eine Struktur für AEM-Projekte zu erstellen und zu verwalten. Es werden empfohlene Strukturen und Vorlagen für Ihr AEM-Projekt erstellt. Darüber hinaus bietet es Versionsautomatisierungs- und Änderungskontrollsysteme, um das Projekt zu verwalten.

   * Verwenden Sie den Maven-Befehl `archetype:generate`, um die anfängliche Struktur zu generieren.
   * Verwenden Sie den Maven-Befehl `eclipse:eclipse`, um die Eclipse-Projektdateien zu generieren und das Projekt in Eclipse zu importieren.

Weitere Informationen finden Sie unter[ Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md).

* Mit dem FileVault-Tool oder VLT können Sie den Inhalt einer CRX- oder AEM-Instanz Ihrem Dateisystem zuordnen. Es bietet Änderungskontrollverwaltungsvorgänge, wie das Ein- und Auschecken des AEM Projektinhalts. Siehe [Vewenden des VLT-Tools](/help/sites-developing/ht-vlttool.md).

* Wenn Sie die Eclipse-integrierte Entwicklungsumgebung verwenden, können Sie AEM Entwickler-Tools für die nahtlose Integration der Eclipse IDE mit AEM-Instanzen verwenden, um AEM Anwendungen zu erstellen. Weitere Informationen finden Sie unter [AEM Entwicklertools für Eclipse](/help/sites-developing/aem-eclipse.md).

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Wenn Sie Pakete zum Verschieben von Inhalten erstellen, stellen Sie sicher, dass die Paketfilterpfade korrekt sind und nur erforderliche Pfade erwähnt werden.

* Speichern Sie keine Inhalte und nehmen Sie keine Änderungen im Ordner /libs vor. Erstellen Sie Überlagerungen in /app-Ordnern, um Standardfunktionen zu erweitern oder zu überschreiben.

* Definieren Sie die richtigen Abhängigkeiten für die Pakete, um eine vorab bestimmte Installationsreihenfolge zu erzwingen.

* Erstellen Sie keinen referenzierbaren Knoten in /libs oder /apps.

### Planen der Authoring-Umgebung {#planning-for-authoring-environment}

Nachdem Sie Ihr AEM Projekt eingerichtet haben, definieren Sie eine Strategie für das Authoring und Anpassen von Vorlagen und Komponenten für adaptive Formulare.

* Eine adaptive Formularvorlage ist eine spezielle AEM, die die Struktur und die Kopf- und Fußzeileninformationen eines adaptiven Formulars definiert. Eine Vorlage verfügt über vorkonfigurierte Layouts, Stile und eine grundlegende Struktur für ein adaptives Formular. AEM Forms bietet Standardvorlagen und -Komponenten, die Sie verwenden können, um adaptive Formulare zu erstellen. Sie können jedoch benutzerdefinierte Vorlagen und Komponenten entsprechend Ihren Anforderungen erstellen. Es wird empfohlen, Anforderungen für zusätzliche Vorlagen und Komponenten zu erfassen, die Sie in Ihren adaptiven Formularen benötigen. Weitere Informationen finden Sie unter [Anpassen adaptiver Formulare und Komponenten](/help/forms/using/adaptive-forms-best-practices.md#customize-components).
* Mit AEM Forms können Sie adaptive Formulare erstellen, die auf den folgenden Formularmodellen basieren. Die Formularmodelle fungieren als Schnittstelle für den Datenaustausch zwischen einem Formular und AEM System und stellen eine XML-basierte Struktur für Datenfluss innerhalb und außerhalb eines adaptiven Formulars bereit. Darüber hinaus legen die Formularmodelle Regeln und Einschränkungen für adaptive Formulare in Form von Schema- und XFA-Beschränkungen fest.

   * **Keines**: Adaptive Formulare, die mit dieser Option erstellt wurden, verwenden kein Formularmodell. Die XML-Datendatei, die aus diesen Formularen generiert wird, hat eine flache Struktur mit Feldern und entsprechenden Werten.
   * **XML- oder JSON-Schema**: XML- und JSON-Schemata stellen die Struktur dar, in der Daten vom Back-End-System in Ihrer Organisation produziert oder genutzt werden. Sie können ein Schema mit einem adaptiven Formular verknüpfen und dem adaptiven Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas stehen auf der Registerkarte „Datenmodellobjekt“ des Inhalts-Browsers für das Erstellen von adaptiven Formularen zur Verfügung. Sie können die Schemaelemente zum Erstellen des Formulars ziehen und ablegen.
   * **XFA-Formularvorlage**: Es ist ein ideales Formularmodell, wenn Sie in XFA-basierte HTML5-Formulare investieren. Es bietet eine direkte Möglichkeit, Ihre XFA-basierten Formulare in adaptive Formulare zu konvertieren. Alle vorhandenen XFA-Regeln werden in den zugehörigen adaptiven Formularen beibehalten. Die resultierenden adaptiven Formulare unterstützen XFA-Konstrukte wie Überprüfungen, Ereignisse, Eigenschaften und Muster.
   * **Formulardatenmodell**: Dies ist das bevorzugte Formularmodell, wenn Sie Ihre Backend-Systeme wie Datenbanken, Web-Services und AEM-Benutzerprofile integrieren möchten, um adaptive Formulare vorauszufüllen und übermittelte Formulardaten zurück in die Backend-Systeme zu schreiben. Mit einem Formulardatenmodell-Editor können Sie Entitäten und Dienste in einem Formulardatenmodell definieren und konfigurieren, das Sie zum Erstellen adaptiver Formulare verwenden können. Weitere Informationen finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

Es ist wichtig, das Datenmodell mit Bedacht auszuwählen, das nicht nur Ihren Anforderungen entspricht, aber Ihre bereits getätigten Investitionen in XSD-Asset XFA-Assets erweitert. Es wird empfohlen, das XSD-Modell zu verwenden, um Formularvorlagen zu erstellen, weil die generiert XML-Daten enthält, die per XPFAD vom Schema definiert wurden. Die Verwendung des XSD-Modells als Standardoption für das Formulardatenmodell ist ebenfalls hilfreich, da es den Formularentwurf vom Back-End-System entkoppelt, das Daten verarbeitet und verbraucht, und die Leistung des Formulars verbessert, da das Formularfeld einer zu einer Zuordnung zugeordnet wird. Außerdem kann BindRef des Felds den XPATH seines Datenwerts in XML erstellen.

Weitere Informationen finden Sie unter [Erstellen eines adaptiven Formulars](/help/forms/using/creating-adaptive-form.md).

* Es gibt einige gemeinsame Abschnitte für adaptive Formulare. Sie können sie identifizieren und eine Strategie definieren, um die Wiederverwendung von Inhalten zu fördern. Mit adaptiven Formularen können Sie eigenständige Fragmente erstellen und sie formularübergreifend wiederverwenden. Sie können auch ein Bedienfeld in einem adaptiven Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen Formularen übernommen. Auf diese Weise können Sie die Bearbeitungszeit verkürzen und Formularkonsistenz gewährleisten. Darüber hinaus macht die Verwendung von Fragmenten adaptive Formulare einfach und sorgt so für ein verbessertes Authoring-Erlebnis, insbesondere bei großen Formularen. Weitere Informationen finden Sie unter [Adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md).

### Anpassen adaptiver Formulare und Komponenten {#customize-components}

* AEM Forms bietet vordefinierte adaptive Formularvorlagen, mit denen Sie adaptive Formulare erstellen können. Sie können auch eigene Vorlagen erstellen. AEM stellt statische und bearbeitbare Vorlagen bereit.

   * Statische Vorlagen werden von den Entwicklern definiert und konfiguriert.
   * Bearbeitbare Vorlagen werden von Autoren mithilfe des Vorlageneditors erstellt. Mit dem Vorlagen-Editor können Sie eine grundlegende Struktur und anfänglichen Inhalt in einer Vorlage definieren. Jede Änderung in der Strukturebene wird in allen Formularen, die diese Vorlage verwenden, übernommen. Der anfängliche Inhalt kann ein vorkonfiguriertes Design, einen Vorbefüllungs-Dienst, eine Sendeaktion usw. umfassen. Diese Einstellungen können jedoch mit dem Formular-Editor für ein Formular geändert werden. Weitere Informationen finden Sie unter [Adaptive Formularvorlagen](/help/forms/using/template-editor.md).

* Verwenden Sie [Inline-Formatierung](/help/forms/using/inline-style-adaptive-forms.md) für die Formatierung einer bestimmten Feld- oder Bedienfeldinstanz. Alternativ können Sie eine Klasse in einer CSS-Datei definieren und den Klassennamen in der CSS-Klasseneigenschaft der Komponente angeben.
* Schließen Sie eine Client-Bibliothek in eine Komponente ein, um Stile konsistent auf alle adaptiven Formulare oder Fragmente anzuwenden, die diese Komponente verwenden. Weitere Informationen finden Sie unter [Erstellen einer Seitenkomponente für adaptive Formulare](/help/forms/using/custom-adaptive-forms-templates.md).
* Wenden Sie in einer Client-Bibliothek definierte Stile an, um adaptive Formulare auszuwählen, indem Sie den Pfad zur Client-Bibliothek im Feld CSS-Dateipfad in den Eigenschaften des adaptiven Formularcontainers angeben.
* Um eine Client-Bibliothek Ihrer Stile zu erstellen, können Sie die benutzerdefinierte CSS-Datei in der Client-Bibliothek des Design-Editors oder in den Eigenschaften des Formular-Containers konfigurieren.
* Adaptive Formulare bieten Bedienfeldlayouts, z. B. responsive Layouts, Registerkarten, Akkordeons und Assistenten, um zu steuern, wie Formularkomponenten in einem Bedienfeld angeordnet werden. Sie können benutzerdefinierte Bedienfeldlayouts erstellen und sie für Formularautoren zur Verfügung stellen. Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Layout-Komponenten für adaptive Formulare](/help/forms/using/custom-layout-components-forms.md).
* Sie können auch bestimmte adaptive Formularkomponenten wie Felder und Bedienfeldlayout anpassen.

   * Verwenden Sie die [Überlagerung](/help/sites-developing/overlays.md) Funktionalität von AEM , um eine Kopie einer Komponente zu ändern. Es wird nicht empfohlen, Standardkomponenten zu ändern.
   * Um das Layout von vordefinierten adaptiven Formularkomponenten in /libs anzupassen, [Erstellen benutzerdefinierter Layoutkomponenten](/help/forms/using/custom-layout-components-forms.md) zusätzlich zu [Standardlayouts](/help/forms/using/layout-capabilities-adaptive-forms.md).
   * Stellen Sie benutzerdefinierte Interaktivitäten ein, indem Sie benutzerdefinierte Widgets oder Erscheinungsbilder erstellen. Es wird nicht empfohlen, Standardkomponenten zu ändern. Weitere Informationen finden Sie unter [Erscheinungsbild-Framework](/help/forms/using/introduction-widgets.md).

* Weitere Informationen finden Sie unter[ Bearbeiten von persönlichen identifizierbaren Informationen](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) für Vorschläge zum Umgang mit PII-Daten.

### Erstellen von Formularvorlagen

Sie können ein adaptives Formular mithilfe der in **Konfigurations-Browser** aktivierten Formularvorlagen erstellen. Informationen zum Aktivieren der Formularvorlagen finden Sie unter [Erstellen einer adaptiven Formularvorlage](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/creating-your-first-adaptive-form/create-adaptive-form-template.html?lang=de).

Die Formularvorlagen können auch aus Paketen mit adaptiven Formularen, die auf einem anderen Autoren-Computer erstellt werden, hochgeladen werden. Formularvorlagen werden durch die Installation von [aemforms-references-* packages](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) verfügbar gemacht. Zu den empfohlenen Best Practices gehören:
* Der Ausführungsmodus **nosamplecontent** wird nur für Autor- und nicht für Veröffentlichungsknoten empfohlen.
* Die Bearbeitung von Assets wie adaptiven Formularen, Designs, Vorlagen oder Cloud-Konfigurationen erfolgt nur über Autorknoten, die auf den konfigurierten Veröffentlichungsknoten veröffentlicht werden können.
Weitere Informationen finden Sie unter [Veröffentlichung von Formularen und Dokumenten und Veröffentlichungen rückgängig machen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=de)
* Das Add-On-Paket für Forms ist für das Authoring sowie für die Veröffentlichung erforderlich, um die Document Service-Vorgänge zu unterstützen. Daher kann es als Abhängigkeit betrachtet werden.
Wenn Sie nur Forms-bezogene Beispielvorlagen, Designs und DOR-Pakete möchten, können Sie sie von [aemforms-references-* packages](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=de) herunterladen.

Weitere Informationen finden Sie im Abschnitt zu empfohlenen Vorgehensweisen unter [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

## Adaptive Formulare erstellen {#author-adaptive-forms}

### Verwenden der Touch-optimierten Benutzeroberfläche für das Authoring {#using-touch-optimized-ui-for-authoring}

* Verwenden Sie den Objekt-Browser in der Seitenleiste, um schnell auf Felder in der Formularhierarchie zuzugreifen. Sie können im Suchfeld nach Objekten in der Formular- oder Objektstruktur, um von einem Objekt zu einem anderen zu navigieren.
* Um die Eigenschaften einer Komponente im Komponenten-Browser in der Seitenleiste anzuzeigen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr-1](assets/cmppr-1.png). Sie können auch auf eine Komponente doppelklicken, um deren Eigenschaften im Eigenschaftenbrowser anzuzeigen.
* Verwenden Sie die Tastaturkürzel, um schnelle Aktionen in Ihren Formularen durchzuführen. Siehe [Tastaturbefehle für AEM Forms](/help/forms/using/keyboard-shortcuts.md).

* Adaptive Formularkomponenten werden nur zur Verwendung auf Seiten mit adaptiven Formularen empfohlen. Die Komponenten hängen von ihrer übergeordneten Hierarchie ab. Daher dürfen Sie diese nicht auf der AEM-Seite verwenden.

Weitere Informationen finden Sie unter Komponentenbeschreibungen und Best Practices in [Einführung in das Authoring adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

### Verwenden von Regeln in adaptiven Formularen {#using-rules-in-adaptive-forms}

AEM Forms bietet einen [Regeleditor](/help/forms/using/rule-editor.md), der es Ihnen ermöglicht, Regeln zu erstellen, um dynamisches Verhalten zu adaptiven Formularkomponenten hinzuzufügen. Unter Verwendung dieser Regeln können Bedingungen ausgewertet werden und Aktionen auf Komponenten ausgelöst werden, wie z. B. Felder anzeigen oder ausblenden, Werte berechnen, Dropdownlisten dynamisch ändern und so weiter.

Der Regeleditor bietet einen visuellen Editor und einen Code-Editor zum Schreiben von Regeln. Beachten Sie beim Schreiben von Regeln im Code-Editor-Modus Folgendes:

* Verwenden Sie aussagekräftige und eindeutige Namen für Formularfelder und Komponenten, um mögliche Konflikte beim Schreiben von Regeln zu vermeiden.
* Verwenden Sie den `this`-Operator für eine Komponente, damit diese auf sich selbst in einem Regelausdruck verweist. Es wird sichergestellt, dass die Regel gültig bleibt, selbst wenn sich der Komponentenname ändert. Beispiel: `field1.valueCommit script: this.value > 10`.

* Verwenden Sie Komponentennamen, wenn Sie auf verschiedene Formularkomponenten verweisen. Verwenden Sie die `value`-Eigenschaft, um den Wert eines Feldes oder einer Komponente abzurufen. Beispiel: `field1.value`.

* Verweisen Sie auf Komponenten durch die relative eindeutige Hierarchie, um Konflikte zu vermeiden. Beispiel: `parentName.fieldName`.

* Beim Bearbeiten von komplexen oder häufig verwendeten Regeln, sollten Sie die Geschäftslogik als Funktionen in eine separaten Client-Bibliothek schreiben, die Sie in adaptiven Formularen festlegen und wieder verwenden können. Die Client-Bibliothek sollte eine eigenständige Bibliothek sein und darf keine externen Abhängigkeiten, außer von jQuery und Underscore.js haben. Sie können die Client-Bibliothek auch benutzen, um [serverseitige erneute Überprüfung](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) der übermittelten Formulardaten zu erzwingen.
* Adaptive Formulare bieten eine Reihe von APIs, mit denen Sie kommunizieren und Aktionen für adaptive Formulare ausführen können. Einige der wichtigsten APIs sind wie folgt: Weitere Informationen finden Sie unter [JavaScript-Bibliotheks-API-Referenz für adaptive Forms](https://adobe.com/go/learn_aemforms_documentation_63_de).

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

* Autoren adaptiver Formulare müssen möglicherweise JavaScript-Code schreiben, um Geschäftslogik in einem Formular zu erstellen. JavaScript ist zwar leistungsstark und effektiv, aber kann die Sicherheit beeinflussen. Daher müssen Sie sicherstellen, dass der Formularautor eine vertrauenswürdige Person ist und dass Prozesse zum Überprüfen und Genehmigen des JavaScript-Codes vorhanden sind, bevor ein Formular in Produktion genommen wird. Der Administrator kann den Zugriff auf den Regeleditor auf Benutzergruppen je nach Rolle oder Funktion beschränken. Siehe [Zugriff des Regeleditors auf ausgewählte Benutzergruppen gewähren](/help/forms/using/rule-editor-access-user-groups.md).
* Sie können Ausdrücke in Regeln verwenden, um adaptive Formulare dynamisch zu gestalten. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Weitere Informationen zu Ausdrücken und optimalen Verfahren finden Sie unter[ Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md). 

### Arbeiten mit Designs {#working-with-themes}

Adaptiv für Designs ermöglicht es Ihnen, wiederverwendbare Stile zu erstellen, die über Formulare hinweg angewendet werden können, um ein konsistentes Erscheinungsbild und Stile zu erhalten. Es wird empfohlen, Designs zu verwenden, um Formatierung für Formularkomponenten und Bedienfelder zu definieren. Einige Best Practices rund um Themen lauten wie folgt:

* Verwenden Sie die Asset-Bibliothek für die schnelle Anwendung von Textstilen, Hintergrund und Bildern. Wenn ein Stil in der Asset-Bibliothek hinzugefügt wird, ist er für andere Designs und im Stilmodus des Formular-Editors verfügbar.
* Wenden Sie globale Einstellungen wie Schriftart und Seitenhintergrund mithilfe der Seitenebenenauswahl an.
* Verwenden Sie Client-Bibliotheken, um vorhandene oder erweiterte Stile in Ihre Designs zu importieren.
* Sie können Stile für bestimmte Felder, Bereiche oder Schaltflächen in einer Formularstilebene außer Kraft setzen. 
* Wenn ein Design Ihre Stilanforderung nicht erfüllt, können Sie vordefinierte Klassen wie guideFieldNode, guideFieldLabel, guideFieldWidget und guidePanelNode verwenden, um einen gemeinsamen Stil für alle Formulare anzuwenden.

Weitere Informationen finden Sie unter [Designs](/help/forms/using/themes.md).

### Optimieren der Leistung von großen und komplexen Formularen {#optimizing-performance-of-large-and-complex-forms}

Formularverfasser und Endbenutzer stoßen normalerweise beim Laden großer Formulare im Authoring-Modus oder zur Laufzeit auf Leistungsprobleme. Wenn die Anzahl der Objekte (Felder und Bereiche) in den Formularen zunimmt, nimmt die Authoring- und Laufzeiterfahrung ab. Es verhindert auch, dass mehrere Autoren gleichzeitig zusammenarbeiten und ein Formular erstellen.

Beachten Sie die folgenden Best Practices, um Leistungsprobleme mit großen Formularen zu beheben:

* Es wird empfohlen, adaptive Formulare mithilfe von XSD-Formulardatenmodellen zu erstellen, selbst bei Konvertierung einer XFA in ein adaptives Formular. 
* Schließen Sie nur die Felder und Bereiche in adaptiven Formularen, die Informationen vom Benutzer erfassen. Erwägen Sie, statische Inhalte zu minimieren oder URLs zu verwenden, um sie in einem separaten Fenster zu öffnen.
* Während jedes Formular für einen bestimmten Zweck entwickelt wurde, gibt es in den meisten Formularen einige gängige Segmente. Zum Beispiel persönliche Details, Adresse, Beschäftigungsdetails usw. Erstellen Sie [adaptive Formularfragmente](/help/forms/using/adaptive-form-fragments.md) für allgemeine Formularelemente und -abschnitte und verwenden Sie diese in allen Formularen. Sie können auch einen Bereich in einem vorhandenen Formular als Fragment speichern. Jede Änderung in einem Fragment wird in allen zugehörigen adaptiven Formularen übernommen. Es unterstützt gemeinsames Authoring, da mehrere Verfasser an verschiedenen Fragmenten, die ein Formular bilden, gleichzeitig arbeiten können.

   * Ähnlich wie bei adaptiven Formularen wird empfohlen, dass alle fragmentspezifischen Stile und benutzerdefinierten Skripte in der Client-Bibliothek mithilfe des Dialogfelds &quot;Fragmentcontainer&quot;definiert werden. Versuchen Sie außerdem, selbstständige Fragmente zu erstellen, die nicht von Objekten außerhalb des Fragments abhängig sind.
   * Außerdem sollten Sie Cross-Fragments-Skripterstellung vermeiden. Wenn es ein Objekt außerhalb des Fragments gibt, auf das Sie verweisen möchten, müssen Sie das Objekt als Teil des übergeordneten Formulars einarbeiten. Wenn sich das Objekt noch in einem anderen Fragment befinden muss, verweisen Sie im Skript anhand seines Namens darauf.

* Verwenden Sie Speichern und Fortsetzen mit automatischem Speichern, um das adaptive Formular regelmäßig zu speichern und Benutzern zu ermöglichen, das Formular zu einem späteren Zeitpunkt erneut aufzurufen, um es auszufüllen.
* Konfigurieren Sie Fragmente, um sie verzögert zu laden. Fragmente, die zur Laufzeit als „Verzögert laden“ markiert sind, werden nur gerendert, wenn sie erforderlich sind. Die Ladezeit für große Formulare wird dadurch erheblich reduziert. Sie wird auch in Fragmenten mit wiederholbaren Bereichen unterstützt. Weitere Informationen finden Sie unter [Konfigurieren von verzögertem Laden](/help/forms/using/lazy-loading-adaptive-forms.md).

   * Konfigurieren Sie kein verzögertes Laden für Fragmente in einem responsiven Rasterlayout oder im ersten Bereich.
   * In verzögert geladenen Fragmenten werden keine Komponenten für Dateianhänge und Geschäftsbedingungen unterstützt.
   * Markieren Sie einen Wert in einem verzögert geladenen Bereich als &quot;Wert global verwenden&quot;, wenn dieser Wert in einem anderen Teil des Formulars verwendet wird, sodass der Wert verfügbar ist, wenn der übergeordnete Bereich entladen wird.
   * Erwägen Sie, Sichtbarkeitsregeln für Fragmente zu erstellen, die basierend auf einer Bedingung ein- bzw. ausgeblendet werden sollen.
* Legen Sie den Wert der **Anzahl der Aufrufe pro Anfrage** im **Apache Sling Main Servlet** auf eine recht große Zahl fest. Dadurch kann der Formular-Server zusätzliche Aufrufe zulassen. Die Konfiguration zeigt den Standardwert 1500 an. Dieser Wert (1500 Aufrufe) ist für andere Experience Manager-Komponenten wie Sites und Assets bestimmt. Der Standardwert für adaptive Formulare ist 20.000. Wenn Sie auf `too many calls`-Fehler in den Protokollen stoßen sollten oder das Formular nicht gerendert werden kann, versuchen Sie, den Wert auf eine große Zahl zu erhöhen, um das Problem zu beheben. Wenn die Anzahl der Aufrufe 20.000 überschreitet, bedeutet das, dass das Formular komplex ist und es einige Zeit dauern kann, das Formular im Browser zu rendern. Dies geschieht nur beim ersten Laden des Formulars. Danach wird das Formular zwischengespeichert, und sobald das Formular zwischengespeichert wurde, gibt es keine wesentliche Auswirkung mehr auf die Leistung.

### Vorausfüllen adaptiver Formulare {#prefilling-adaptive-forms}

Sie können adaptive Formularfelder vorab mit Daten ausfüllen, die aus dem Backend abgerufen werden, damit Benutzer das Formular schnell ausfüllen und Tippfehler vermeiden können.

* AEM Forms bietet einen Vorbefüllungs-Dienst zum Lesen von Daten aus einer vordefinierten XML-Datendatei und zum Vorbefüllen der Felder eines adaptiven Formulars mit dem Inhalt in der XML-Datei zum Vorausfüllen.
* Die XML zum Vorausfüllen der Daten muss mit dem Schema des Formularmodells konform sein, das mit dem adaptiven Formular verknüpft ist.
* Schließen Sie die Abschnitte`afBoundedData` und`afUnBoundedData` in die Prefill-XML zum Vorbefüllen von gebundenen und ungebundenen Feldern in einem adaptiven Formular ein.

* Für adaptive Formulare, die auf dem Formulardatenmodell basieren, bietet AEM Forms einen sofort einsatzbereiten Vorbefüllungs-Service für Formulardatenmodelle an. Der Vorbefüllungs-Dienst fragt Datenquellen für Datenmodellobjekte im adaptiven Formular ab und füllt Feldwerte bei der Wiedergabe des Formulars vorab aus.
* Sie können auch die Protokolle Datei, crx, service oder http verwenden, um adaptive Formulare vorab auszufüllen.
* AEM Forms unterstützt benutzerdefinierte Vorbefüllungs-Dienste, die Sie als OSGi-Dienst einbinden können, um adaptive Formulare vorab auszufüllen.

Weitere Informationen finden Sie unter [Vorbefüllen der Felder in adaptiven Formularen](/help/forms/using/prepopulate-adaptive-form-fields.md).

### Signieren und Senden adaptiver Formulare {#signing-and-submitting-adaptive-forms}

Adaptive Formulare benötigen Übermittlungsaktionen für die Verarbeitung der von Benutzern angegebenen Daten. Eine Sendeaktion bestimmt die Aufgabe, die auf die mithilfe eines adaptiven Formulars übermittelten Daten angewendet wird.

* Es gibt mehrere Sendeaktionen, die in adaptiven Formularen sofort verfügbar sind. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md).
* Sie können eine benutzerdefinierte Sendeaktion schreiben, wenn die standardmäßigen Sendeaktionen Ihren Anwendungsfall nicht erfüllen. Weitere Informationen finden Sie unter[ Schreiben von benutzerdefinierten Übermittlungsaktionen für ein adaptives Formular](/help/forms/using/custom-submit-action-form.md).
* Beziehen Sie serverseitige Validierungen ein, um zu verhindern, dass ungültige Daten übermittelt werden. 

Sie können Adobe Sign in adaptiven Formularen mit mehreren Signaturen nutzen. Beachten Sie Folgendes bei der Konfiguration von Adobe Sign in adaptiven Formularen. Weitere Informationen finden Sie unter [Verwenden von Adobe Sign in einem adaptiven Formular](/help/forms/using/working-with-adobe-sign.md).

* Adobe Sign-aktiviertes Formular wird nur gesendet, nachdem alle Unterzeichner das Formular unterzeichnet haben. Formulare werden im Status „Ausstehende Signatur“ angezeigt, bis das Formular von allen Signierern unterzeichnet wurde.
* Sie können das Signiererlebnis im Formular konfigurieren oder Unterzeichner beim Senden zu einer Signaturseite weiterleiten.
* Konfigurieren Sie die sequenzielle oder parallele Signierung nach Bedarf.

### Generieren des Datensatzdokuments {#generating-document-of-record}

Ein Datensatzdokument (DoR) ist eine reduzierte PDF-Version eines adaptiven Formulars, die Sie drucken, signieren oder archivieren können.

* Je nach Formulardatenmodell, auf dem ein adaptives Formular basiert, können Sie eine Vorlage für das DoR wie folgt konfigurieren:

   * **XFA-Formularvorlage**: Verwenden Sie die zugehörige XDP-Datei als DoR-Vorlage.
   * **XSD-Schema**: Verwenden Sie die zugeordnete XFA-Vorlage, die dasselbe XML-Schema wie das adaptive Formular verwendet.
   * **Keines**: Verwenden Sie automatisch generierte DoR.

* Konfigurieren Sie Kopf- und Fußzeile, Bilder, Farbe, Schriftart usw. direkt auf der Registerkarte &quot;Datensatzdokument&quot;des adaptiven Formulareditors.
* Verwenden Sie `DoRService`, um das DoR programmatisch zu generieren.
* Ausgeblendete Felder aus DoR ausschließen.
* Verwenden Sie den Aufforderungsparameter `afAcceptLang`; um DoR in einem anderen Gebietsschema anzuzeigen.

### Debuggen und Testen von adaptiven Formularen {#debugging-and-testing-adaptive-forms}

[AEM Chrome-Plug-in](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) ist eine Browsererweiterung für Google Chrome, die Tools zum Debugging adaptiver Formulare bereitstellt. Formularverfasser und -entwickler können die folgenden Tools verwenden:

* Identifizieren von Engpässen und Optimieren der Leistung der Formularwiedergabe
* Debuggen von Schlüsselwörtern und bindRef-Fehlern im Formular
* Protokolle aktivieren und konfigurieren
* Debuggen von Regeln und Skripten im Formular
* Weitere Informationen zu guideBridge-APIs

Weitere Informationen finden Sie unter [AEM-Plug-In für Chrome – Adaptive Formulare](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/).

### Validieren adaptiver Formulare auf AEM Server {#validating-adaptive-forms-on-aem-server}

Serverseitige Überprüfungen sind erforderlich, um alle Versuche zu verhindern, die Überprüfungen auf dem Client und mögliche Gefahren von Datenübertragungen und Verletzungen von Geschäftsregeln umgehen wollen. Serverseitige Überprüfungen werden auf dem Server ausgeführt, indem die erforderliche Client-Bibliothek geladen wird.

* Schließen Sie Funktionen in eine Client-Bibliothek ein, um Ausdrücke in adaptiven Formularen zu überprüfen, und geben Sie die Client-Bibliothek im Container-Dialogfeld für adaptive Formulare an. Weitere Informationen finden Sie unter [Serverseitige erneute Überprüfung](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p).
* Die Server-seitige Validierung prüft das Formularmodell. Es wird empfohlen, eine separate Client-Bibliothek für Überprüfungen zu erstellen und sie nicht mit anderen Elementen wie HTML-Styling und DOM-Manipulation in derselben Client-Bibliothek zu mischen.

### Lokalisieren von adaptiven Formularen {#localizing-adaptive-forms}

AEM bietet Übersetzungs-Workflows, mit denen Sie adaptive Formulare lokalisieren können. Weitere Informationen finden Sie unter [Verwenden AEM Übersetzungs-Workflows zum Lokalisieren adaptiver Formulare](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).

Einige Best Practices beim Lokalisieren von adaptiven Formularen lauten wie folgt:

* Verwenden Sie adaptive Formularfragmente für gängige Elemente in Formularen und lokalisieren Sie Fragmente. Dadurch wird sichergestellt, dass Sie ein Fragment einmal lokalisieren und es in allen Formularen wiedergeben, in denen das lokalisierte Fragment verwendet wird.
* Änderungen wie das Hinzufügen einer neuen Komponente oder das Anwenden eines Skripts in einem lokalisierten Formular werden nicht automatisch lokalisiert. Daher müssen Sie ein Formular vor der Lokalisierung fertigstellen, um mehrere Lokalisierungszyklen zu vermeiden.
* Verwenden Sie den Anforderungsparameter `afAcceptLang`, um das Browsergebietsschemazu überschreiben und das Formular in einem spezifischen Gebietsschema zu lokalisieren. Die folgende URL erzwingt beispielsweise die Darstellung des Formulars im japanischen Gebietsschema, unabhängig vom Gebietsschema, das in den Browser-Einstellungen angegeben ist:

  `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms unterstützt die Lokalisierung von Inhalten adaptiver Formulare derzeit für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italianisch (it), Deutsch (de), Japanisch (ja), Portugiesisch – Brasilien (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können jedoch zur Laufzeit Unterstützung für neue Gebietsschemata für adaptive Formulare hinzufügen. Weitere Informationen finden Sie unter [Unterstützung neuer Gebietsschemata für die Lokalisierung adaptiver Formulare](/help/forms/using/supporting-new-language-localization.md).

## Vorbereiten des Formularprojekts für die Produktion {#prepare-forms-project-for-production}

### Hinzufügen von Formularverarbeitungsservern {#adding-forms-processing-server}

Sie können eine weitere Instanz des AEM Forms-Servers konfigurieren, der sich hinter der Firewall in einem geschützten Bereich befindet. Sie können diese Instanz für Folgendes verwenden:

* **Stapelverarbeitung**: Aufträge, die wiederkehrend sind oder in Stapeln mit hoher Belastung geplant werden. Beispielsweise das Drucken von Anweisungen, das Generieren von Korrespondenzen und die Verwendung von Document Services wie PDF Generator, Output und Assembler.
* **Speichern von PII-Daten**: Speichern Sie personenbezogene Daten auf dem Verarbeitungsserver. Dies ist nicht erforderlich, wenn Sie bereits einen benutzerdefinierten Speicheranbieter zum Speichern von PII-Daten verwenden.

### Verschieben eines Projekts in eine andere Umgebung {#moving-project-to-another-environment}

Oft müssen Sie Ihre AEM Projekte von einer Umgebung in eine andere verschieben. Einige der wichtigsten Dinge, die beim Verschieben beachtet werden müssen, sind:

* Erstellen Sie eine Sicherungskopie Ihrer vorhandenen Client-Bibliotheken, Ihres benutzerdefinierten Codes und Ihrer Konfigurationen.
* Stellen Sie Produktpakete und Patches manuell und in der angegebenen Reihenfolge in der neuen Umgebung bereit.
* Stellen Sie projektspezifische Code-Pakete und -Bundles manuell und als separates Paket oder Bundle auf dem neuen AEM bereit.
* (*Nur AEM Forms auf JEE*) Manuelle Bereitstellung von LCAs und DSCs auf dem Forms Workflow-Server.
* Verwendung [Export-Import](/help/forms/using/import-export-forms-templates.md) Funktionen zum Verschieben von Assets in die neue Umgebung. Sie können auch den Replikationsagenten konfigurieren und die Assets veröffentlichen.
* Ersetzen Sie bei der Aktualisierung alle veralteten APIs und Funktionen durch neue APIs und Funktionen.

### Konfigurieren von AEM {#configuring-aem}

Einige Best Practices zur Konfiguration von AEM zur Verbesserung der Gesamtleistung lauten wie folgt:

* Aktivieren Sie HTML-Client-Bibliothekskomprimierung für JavaScript und CSS-Code aus der Felix-Konsole.
* Speichern Sie alle Client-Bibliotheken unter `/etc.clientlibs/fd` und alle zusätzlichen benutzerdefinierten Client-Bibliotheken auf dem AEM-Dispatcher zwischen, um die Interaktivität und Sicherheit Ihrer veröffentlichen Formulare zu erhöhen. Weitere Informationen finden Sie unter [Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html)

* Speichern Sie keine `/content/forms/af/`- und `/content/dam/formsanddocuments/*`-Pfade im Cache. Detaillierte Informationen zum Konfigurieren der Zwischenspeicherung adaptiver Formulare finden Sie unter [Zwischenspeichern adaptiver Formulare](/help/forms/using/configure-adaptive-forms-cache.md).

* Aktivieren Sie HTML über das Webserver-Komprimierungsmodul. Weitere Informationen finden Sie im Abschnitt [Leistungsoptimierung des AEM Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Erhöhen Sie Aufrufe pro Anforderungskonfiguration für große Formulare. Siehe [Optimieren der Leistung von großen und komplexen Formularen](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Erstellen [Benutzerdefinierte Fehlerseiten, die vom Fehler-Handler angezeigt werden](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/customizing-errorhandler-pages.html?lang=de).
* Sichere AEM Forms-Server.

   * Verwenden Sie `nosamplecontent`-Laufzeitmodus unter, um sicherzustellen, dass die Anwendung keine Beispielinhalte und Beispielbenutzer enthält, die auf dem Produktionsserver bereitgestellt werden. Siehe [Ausführen von AEM im produktionsfertigen Modus](/help/sites-administering/production-ready.md).

* Halten Sie die Heap-Größe auf mindestens 8 GB fest. Für andere Einstellungen finden Sie weitere Informationen im Abschnitt [Leistungsoptimierung des AEM Forms-Servers](/help/forms/using/performance-tuning-aem-forms.md).
* Verwenden Sie Dienstbenutzersitzungen anstelle von Admin-Sitzungen zum Ausführen von Aufgaben auf Dienstebene. Weitere Informationen finden Sie unter [Dienstauthentifizierung](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html).

>[!VIDEO](https://vimeo.com/de/)

### Externen Speicher für Entwürfe und gesendete Formulardaten konfigurieren {#external-storage}

In einer Produktionsumgebung wird empfohlen, keine gesendeten Formulardaten in AEM Repository zu speichern. Die Standardimplementierung der Übermittlungsaktionen Forms Portal Store, Store Content und Store PDF speichert Formulardaten in AEM Repository. Diese Übermittlungsaktionen dienen nur zu Demonstrationszwecken. Die Funktionen „Speichern und fortsetzen“ und Automatische Speicherung“ verwenden auch standardmäßig Portalspeicher. Beachten Sie daher folgende Empfehlungen:

* **Speichern von Entwurfsdaten**: Wenn Sie die Funktion „Entwurf“ in ein adaptiven Formularen verwenden, müssen Sie eine benutzerdefinierte Service Provide Interface (Dienstanbieterbenutzeroberfläche, SPI) verwenden, um Entwurfsdaten in einem sichereren Speicher wie in einer Datenbank zu speichern. Weitere Informationen finden Sie unter [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

* **Speichern von Übermittlungsdaten**: Wenn Sie den Formularportalübermittlungs-Store verwenden, sollten Sie eine benutzerdefinierte SPI implementieren, um Übermittlungsdaten in einer Datenbank zu speichern. Siehe [Beispiel für die Integration der Komponente für Entwürfe und Übermittlungen mit der Datenbank](/help/forms/using/integrate-draft-submission-database.md) für ein Integrationsbeispiel.

  Sie können auch eine benutzerdefinierte Übermittlungsaktion schreiben, die Formulardaten und Anhänge in einem sicheren Speicher speichert. Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten Sendeaktion für adaptive Formulare](/help/forms/using/custom-submit-action-form.md).

* **Länge der Entwurfs-ID**: Wenn Sie ein adaptives Formular als Entwurf speichern, wird eine Entwurfs-ID generiert, um den Entwurf eindeutig zu identifizieren. Der Mindestwert für die Länge des Entwurfs-ID-Felds beträgt 26 Zeichen. Adobe empfiehlt, die Länge der Entwurfs-ID auf 26 oder mehr Zeichen festzulegen.

### Umgang mit personenbezogenen Daten {#handling-personally-identifiable-information}

Eine der wichtigsten Herausforderungen für Unternehmen besteht darin, wie personenbezogene Daten (PII) verarbeitet werden können. Einige Best Practices, die Ihnen bei der Verarbeitung solcher Daten helfen, lauten wie folgt:

* Verwenden Sie einen sicheren externen Speicher wie eine Datenbank, um Daten aus Entwürfen und gesendeten Formularen zu speichern. Siehe [Konfigurieren von externem Speicher für Entwürfe und eingereichte Formulardaten](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* Verwenden Sie die Formularkomponente &quot;Bedingungen&quot;, um die ausdrückliche Zustimmung des Benutzers zu erhalten, bevor Sie die automatische Speicherung aktivieren. Aktivieren Sie in diesem Fall die automatische Speicherung nur, wenn der Benutzer den Bedingungen in der Komponente &quot;Allgemeine Geschäftsbedingungen&quot;zustimmt.


