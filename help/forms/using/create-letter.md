---
title: Erstellen eines Briefes
seo-title: Create Letter
description: In diesem Thema erfahren Sie, wie Sie einen Brief erstellen, Datenmodule und Anhänge hinzufügen und ihn in der Correspondence Management-Vorschau anzeigen können.
seo-description: This topic gives you the steps to create a letter, add data modules and attachments to it, and preview it in Correspondence Management.
uuid: b5cdbf01-db85-4ff8-9fda-1489542bffef
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 6cef0bcf-e2f0-4a5a-85a1-6d8a5dd9bd01
feature: Correspondence Management
exl-id: 2f996a50-7c7d-41b6-84b2-523b6609254b
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '3979'
ht-degree: 46%

---

# Erstellen eines Briefes {#create-letter}

## Correspondence Management-Workflow {#correspondence-management-workflow}

Der Correspondence Management-Workflow besteht aus vier Phasen:

1. Vorlagenerstellung
1. Dokumentfragmenterstellung
1. Brieferstellung
1. Nachbearbeitung

### Vorlagenerstellung {#template-creation}

Die folgende Abbildung zeigt einen typischen Workflow zum Erstellen einer Korrespondenzvorlage.

![Arbeitsablauf für das Erstellen einer Korrespondenzvorlage](assets/01.png)

Die einzelnen Workflow-Schritte:

1. Formularentwickler erstellen Layouts und Fragmentlayouts mit Adobe Forms Designer und laden sie in ein CRX-Repository hoch. Die Layouts enthalten typische Formularfelder, Layoutfunktionen wie Kopf- und Fußzeilen und leere &quot;Zielbereiche&quot;für die Platzierung von Inhalten. Später ordnen Anwendungsspezialisten den Inhalt zu, der für diese Zielbereiche erforderlich ist. Weitere Informationen über [Designlayout](/help/forms/using/layout-design-details.md).
1. Subject Matter Experts aus Rechts-, Finanz- oder Marketingabteilungen erstellen und laden Inhalte wie Textklauseln, Haftungsausschlüsse, Nutzungsbedingungen und Bilder wie Logos hoch, die in verschiedenen Korrespondenzvorlagen wiederverwendet werden.
1. Anwendungsspezialisten erstellen Korrespondenzvorlagen. Der Anwendungsspezialist

   * Ordnet den Zielbereichen in den Layoutvorlagen Textbausteine und Bilder zu
   * Definiert Bedingungen/Regeln für die Einbeziehung von Inhalten
   * Bindet Layout-Felder und Variablen an die zugrunde liegenden Datenmodelle

1. Verfasser zeigt den Brief in einer Vorschau an und reicht ihn zur Nachbearbeitung ein. Weitere Informationen über [Nachbearbeitung](/help/forms/using/submit-letter-topostprocess.md).

#### Verwenden von Briefvorlagen, die mit Correspondence Management bereitgestellt werden {#using-letter-templates-provided-with-correspondence-management}

Anstatt eine neue Layoutvorlage zu erstellen, können Sie die von Correspondence Management bereitgestellten Vorlagen ändern und wiederverwenden. Mit Designer können Sie das Branding sowie die Daten- und Inhaltsfelder der Vorlagen schnell an die Anforderungen Ihres Unternehmens anpassen. Weitere Informationen zu Correspondence Management-Vorlagen finden Sie unter [Referenzieren von Briefvorlagen](/help/forms/using/reference-cm-layout-templates.md).

### Dokumentfragmenterstellung {#document-fragment-creation}

Dokumentfragmente sind wiederverwendbare Teile/Komponenten einer Korrespondenz, mit der Sie Briefe/Korrespondenz erstellen können.

Es gibt Dokumentfragmente der folgenden Typen:

#### Text {#text}

Ein Textelement ist eine Inhaltskomponente, die aus einem oder mehreren Textabsätzen besteht. Ein Absatz kann statisch oder dynamisch sein. Ein dynamischer Absatz enthält Verweise auf Datenelemente, deren Werte zur Laufzeit bereitgestellt werden.

#### Liste {#list}

Eine Liste ist eine Reihe von Dokumentenfragmenten, einschließlich Text, Listen (die gleiche Liste kann nicht zu sich selbst hinzugefügt werden), Bedingungen und Bildern. Die Reihenfolge der Listenelemente kann festgelegt sein oder bearbeitet werden. Beim Erstellen eines Briefs können Sie einige oder alle Listenelemente verwenden, um ein wiederverwendbares Muster von Elementen zu replizieren.

#### Bedingung {#condition}

Mithilfe von Bedingungen können Sie festlegen, welche Inhalte zum Zeitpunkt der Dokumenterstellung je nach den bereitgestellten Daten in das Schriftstück einbezogen werden sollen. Die Bedingung wird in Form von Steuerungsvariablen beschrieben. Die Variablen können entweder ein Datenwörterbuchelement oder ein Platzhalter sein. Beim Hinzufügen einer Bedingung haben Sie die Möglichkeit, ein Asset einzubeziehen, das auf dem Wert beruht, den die Steuerungsvariable hat. Bedingungen führen zu einer einzelnen Ausgabe, die von einem Ausdruck abhängt. Der erste Ausdruck wird basierend auf der aktuellen Bedingungsvariablen als &quot;true&quot;erkannt. Sein Wert wird zur Ausgabe der Bedingung.

#### Layout-Fragment {#layout-fragment}

Ein Layout-Fragment ist ein Layout, das in einem oder mehreren Briefen verwendet werden kann. Ein Layout-Fragment wird verwendet, um wiederholbare Muster, insbesondere dynamische Tabellen, zu erstellen. Das Layout kann typische Formularfelder wie „Adresse“ und „Referenznummer“ enthalten. Es enthält auch leere Unterformulare, die Zielbereiche kennzeichnen. Die Layouts (XDP-Dateien) werden in Designer erstellt und können dann [in Formulare und Dokumente hochgeladen werden](/help/forms/using/get-xdp-pdf-documents-aem.md).

### Brieferstellung {#letter-creation}

Es gibt zwei Möglichkeiten, die Korrespondenz zu generieren, die an Ihre Kunden gesendet wird: benutzergesteuert und systemgesteuert.

#### Benutzergesteuert {#user-driven}

Kundenorientierte Mitarbeiter wie Schadensregulierer oder Fallmitarbeiter können eine angepasste Korrespondenz erstellen. Mithilfe einer einfachen und intuitiven Benutzeroberfläche zum Ausfüllen von Briefen können Geschäftsbenutzer optionalen Text zur Korrespondenz hinzufügen, bearbeitbaren Inhalt personalisieren und die Korrespondenz in Echtzeit in der Vorschau anzeigen. Sie können die angepasste Korrespondenz dann an einen Back-End-Prozess senden.

![Benutzergesteuerte, angepasste Korrespondenz](assets/02.png)

#### Systemgesteuert {#system-driven}

Die Erstellung von Schriftstücken wird durch sogenannte Ereignistrigger ausgelöst und erfolgt automatisch. Beispiel: Ein Mahnschreiben zur Erinnerung an eine Steuervorauszahlung wird durch Zusammenfügung der vorab definierten Vorlage mit den Kontaktdaten des Empfängers generiert. Der endgültige Brief kann per E-Mail gesendet, ausgedruckt, als Fax verschickt oder archiviert werden.

![Systemgesteuerte Korrespondenz](assets/us_cm_generate.png)

### Nachbearbeitung {#post-processing}

Die endgültige Korrespondenz kann zur Nachbearbeitung an einen Back-End-Prozess gesendet werden. Die Korrespondenz kann:

1. Verarbeitet für E-Mail-, Fax- oder Stapeldruck oder in einem Ordner zum Drucken oder E-Mail-Versand.
1. Zur Überprüfung und Genehmigung vorgelegt.
1. Durch Anwendung digitaler Signaturen, Zertifizierung, Verschlüsselung oder Rechteverwaltung gesichert.
1. Konvertiert in ein durchsuchbares PDF-Dokument, das alle für Archivierungs- und Auditing-Zwecke erforderlichen Metadaten enthält.
1. Eingebunden in ein PDF-Portfolio, das mehr Dokumente enthält, z. B. Marketingmaterial. Das PDF-Portfolio kann dann als endgültiges Schriftstück gesendet werden.

### Architektur der Correspondence Management-Lösung {#correspondence-management-solution-architecture}

Die folgende Grafik bietet eine Übersicht über eine Beispielarchitektur der Brieflösung.

![Architektur für Brieflösung](assets/us_cm_architecture_es3.png)

## Einzelkomponenten eines Briefs {#deconstructing-a-letter}

Dieses Dokument einer Kündigungsmitteilung ist ein Beispiel für eine typische Korrespondenz:

![Ein Beispielkündigungsbrief](assets/5_deconstructingaletter.png)

<table> 
 <tbody> 
  <tr> 
   <td><strong>Briefelemente</strong></td> 
   <td><strong>Beschreibung</strong></td> 
   <td><strong>Formuliert mit</strong></td> 
  </tr> 
  <tr> 
   <td>Daten aus Back-End-Unternehmenssystemen</td> 
   <td>Daten, die aus Back-End-Unternehmenssystemen bezogen werden. Die Daten werden dynamisch mit der Korrespondenzvorlage zusammengeführt.</td> 
   <td>Die<br /> Datendatei, die basierend auf einem Datenwörterbuch erstellt wurde</td> 
  </tr> 
  <tr> 
   <td>Daten<br /> Eingabe durch einen Frontend-Mitarbeiter</td> 
   <td>Daten, die von einem Front-Line-Mitarbeiter bereitgestellt werden können, der den Brief vor dem Versand anpasst.<br /> </td> 
   <td><p>Ungeschützte DD-Elemente<br /> Bearbeitbare Textabsätze<br /> Variablen/Platzhalter<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Vorab genehmigt<br /> Textabsätze</td> 
   <td>Vorab genehmigte Textinhalte. Experten in den Bereichen Recht, Finanzen oder einer Branche, die den Geschäftskontext des Briefs verstehen, verfassen den Textinhalt normalerweise. Inhalte wie Kopf- und Fußzeile, Haftungsausschlüsse und Anrede wären für die meisten Briefe üblich. Inhalte wie "Grund für die Kündigung"wären jedoch spezifisch für den jeweiligen Brief.</td> 
   <td><p>Text\Listen\<br /> Bedingungen\Layout</p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>Daten<br /> basierend auf benutzerspezifischer Logik ?</td> 
   <td>Für einige Briefe, z. B. einen Brief, in dem weitere Informationen zu einem Schaden angefordert werden, können Benutzer wie etwa der Schadensregulierer benutzerdefinierte Textinhalte hinzufügen.</td> 
   <td>Dokument<br />-Fragment der Typenbedingung </td> 
  </tr> 
  <tr> 
   <td>Gespeichert<br /> Bilder aus dem zentralen Repository</td> 
   <td>Bilder wie Logos und Signaturbilder. Bilder wie Unternehmenslogos würden in den meisten Schriftstücken oder in allen Schriftstücken angezeigt. Unterschriftsbilder sind spezifisch für den Brief und für die Person, in deren Namen der Brief gesendet wird.</td> 
   <td><p>In AEM Assets (DAM) gespeicherte Bilder<br /> </p> <p> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analysieren Sie einen Brief, bevor Sie ihn erstellen {#analyze-a-letter-before-you-construct-it}

Analysieren Sie jeden Brief, um die verschiedenen Teile freizulegen, die den Brief bilden. Der Anwendungsspezialist analysiert die generierten Schriftstücke.

* Welche Teile der Korrespondenz sind statisch und welche sind dynamisch? Die Variablen, die aus Back-End-Datenquellen oder von Endbenutzern ausgefüllt werden.
* Die Reihenfolge, in der die verschiedenen Textabsätze in der Korrespondenz angezeigt werden, z. B. ob ein Geschäftsbenutzer Absätze während der Korrespondenzerstellung ändern kann.
* Wird die Korrespondenz systemgeneriert oder benötigt ein Endbenutzer, um die Korrespondenz zu bearbeiten? Wie viele Korrespondenzen werden systemgeneriert und wie viele erfordern ein Eingreifen des Benutzers?
* Wie oft ändert sich die Korrespondenzvorlage? Wird sie jährlich, vierteljährlich oder nur bei einer Änderung bestimmter Rechtsvorschriften aktualisiert? Welche Art von Änderungen wird erwartet? Ist es eine Änderung, um typografische Fehler zu beheben, eine Layoutänderung, das Hinzufügen weiterer Felder, das Hinzufügen weiterer Absätze usw.
* Stellen Sie bei der Planung Ihrer Korrespondenzanforderungen die Liste der neuen Korrespondenzvorlagen zusammen. Für jede Korrespondenzvorlage benötigen Sie:

   * Textbausteine, Bilder und Tabellen
   * Datenwerte aus Backend-Systemen
   * Layout und Fragmentlayouts der Korrespondenz
   * Die Reihenfolge, in der der Inhalt im Brief angezeigt wird, und Regeln für die Einbeziehung und den Ausschluss von Inhalten

* Die Bedingungen, unter denen gewerbliche Benutzer wie Schadensregulierer oder Fallarbeiter Inhalte oder Teile davon im Brief ändern.
* Szenarien beschreiben das Benutzererlebnis, die Anforderungen und die Vorteile der Verwendung der Brieflösung.
* Szenarien bieten auch:Die erforderlichen Fertigkeiten und Tools, die Sie für Ihr Projekt benötigen.
* Empfohlene Vorgehensweisen für die Planung Ihrer Implementierung. ``Allgemeine Übersicht über die Implementierung.

## Vorteile der Analyse {#benefits-of-performing-the-analysis}

**Wiederverwendung von Inhalten**: Sie haben eine konsolidierte Liste mit neuen Inhalten, die für die Generierung von Korrespondenz erforderlich sind. Ein Großteil des Inhalts, wie Kopf- und Fußzeilen, Haftungsausschlüsse und Einführungen, ist in vielen Briefen üblich und kann in verschiedenen Briefen wiederverwendet werden. All diese gemeinsamen Inhalte können einmalig von Experten erstellt und genehmigt und dann in vielen Schriftstücken wiederverwendet werden.

**Aufbau des Datenwörterbuchs**: Es gibt Datenwerte wie „Kundennummer“ und „Kundenname“, die in vielen Briefen verwendet werden. Sie können eine konsolidierte Liste aller dieser Datenwerte erstellen. Normalerweise wird bei der Strukturplanung jemand vom Middleware-Team des Unternehmens konsultiert. Dies bildet die Grundlage für die Erstellung des Datenwörterbuchs.

**Datenquellen aus Back-End-Unternehmenssystemen** Sie werden auch alle erforderlichen Datenwerte kennen und erfahren, von wo aus die Daten des Unternehmenssystems abgerufen werden. Sie können dann die Architektur so einrichten, dass die Daten aus dem Unternehmenssystem extrahiert und an die Brieflösung übermittelt werden.

**Schätzung der Komplexität von Briefen**: Es ist wichtig zu ermitteln, wie komplex die Erstellung einer bestimmten Korrespondenz sein wird. Diese Analyse hilft bei der Bestimmung der Zeit und der Fertigkeiten, die zum Erstellen der Briefvorlagen erforderlich sind. Dies wiederum hilft bei der Schätzung der Ressourcen und Kosten für die Implementierung der Brieflösung.

## Komplexität der Korrespondenz {#correspondence-complexity}

Die Komplexität der Korrespondenz kann durch Analyse der folgenden Parameter bestimmt werden:

**Komplexität des Layouts** Wie komplex ist das Layout? Briefe wie etwa Kündigungsmitteilungen haben einfache Layouts. Briefe wie z. B. &quot;Schadensabdeckungsbestätigungen&quot;haben dagegen ein komplexes Layout mit mehreren Tabellen und mehr als 60 Formularfeldern. Das Erstellen komplexer Layouts nimmt mehr Zeit in Anspruch und erfordert fortgeschrittene Layoutfähigkeiten.

**Anzahl der Textabsätze und Bedingungen**: Ein Darlehensvertrag kann 10 Seiten lang sein und mehr als 40 Textbausteine enthalten. Viele dieser Textbausteine hängen von den Darlehensparametern ab. Auf der Grundlage der genauen Vertragsbedingungen würden die Klauseln in den Vertrag aufgenommen oder aus dem Vertrag ausgeschlossen. Die Erstellung solcher Briefe erfordert eine gründliche Planung und eine sorgfältige Definition der komplexen Bedingungen.

Diese Tabelle enthält einige Richtlinien, mit denen Sie Ihre Briefe klassifizieren können:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Komplexitätsstufe</strong></p> </td> 
   <td><p><strong>Komplexität des Layouts (subjektiv)</strong></p> </td> 
   <td><p><strong>Anzahl der Textabsätze</strong></p> </td> 
   <td><p><strong>Anzahl bedingter Textbausteine oder Bilder</strong></p> </td> 
   <td><p><strong>Erforderliche Kompetenz</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Geringe Komplexität</p> </td> 
   <td><p>Niedrig. Layout hat nur wenige Formularfelder (&lt;15).</p> <p>Normalerweise eine Seite<span class="acrolinxCursorMarker"></span>.</p> </td> 
   <td><p>8</p> </td> 
   <td><p>1</p> </td> 
   <td><p>Mittleres Kenntnisniveau von Designer.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mittlere Komplexität</p> </td> 
   <td><p>Layout mit mittlerer Komplexität. Umfasst Strukturen wie Tabellen. In der Regel mehr als eine Seite lang.</p> </td> 
   <td><p>16</p> </td> 
   <td><p>2</p> </td> 
   <td><p>Mittleres Kenntnisniveau von Designer.</p> <p> </p> <p>Möglichkeit, komplexe Ausdrücke mithilfe von Benutzeroberflächen zu erstellen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Hohe Komplexität</p> </td> 
   <td><p>Komplexes Layout. Kann mehr als drei Seiten umfassen. Enthält Tabellen und mehr als 60 Formularfelder.</p> </td> 
   <td><p>40</p> </td> 
   <td><p>8</p> </td> 
   <td><p>Kenntnisse von Designer auf Expertenniveau.</p> <p> </p> <p>Möglichkeit, komplexe Ausdrücke mithilfe von Benutzeroberflächen zu erstellen.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Übersicht über das Erstellen eines Briefs {#overview-of-creating-a-letter}

1. Wählen Sie das entsprechende Layout aus, das als Grundlage für den Brief dient, und erstellen Sie einen Brief.
1. Fügen Sie dem Brief Datenmodule oder Layout-Fragmente hinzu und konfigurieren Sie sie.
1. Wählen Sie die Vorschau der Korrespondenz aus.
1. Bearbeiten Sie die Felder, Variablen, Inhalte und Anlagen und richten Sie sie ein.

### Voraussetzungen {#prerequisites}

Sie müssen zunächst Folgendes einrichten, um eine Korrespondenz zu erstellen:

* [Kompatibilitätspaket](compatibility-package.md). Installieren Sie das Kompatibilitätspaket, um die Option **Briefe** auf der Seite **Formulare** anzuzeigen.
* Die XDP-Datei des Briefs ([Layout](/help/forms/using/document-fragments.md)).
* Andere XDP-Dateien ([Layoutfragmente](document-fragments.md#document-fragments)), die Bestandteile des Briefs bilden. Die XDP-Dateien/Layouts werden in [Designer](https://www.adobe.com/go/learn_aemforms_designer_65_de) erstellt.
* Das relevante [Datenwörterbuch](/help/forms/using/data-dictionary.md) (optional).
* Die [Datenmodule](/help/forms/using/document-fragments.md), die Sie in der Korrespondenz verwenden möchten.
* [Test-Daten](/help/forms/using/data-dictionary.md#p-working-with-test-data-p) bestehen aus der XML-Datei, in die die Testdaten portiert wurden. Testdaten sind erforderlich, wenn Sie ein Datenwörterbuch verwenden.

## Erstellen einer Briefvorlage {#create-a-letter-template}

### Wählen Sie ein Layout aus und geben Sie die Briefeigenschaften ein {#select-a-layout-and-enter-the-letter-properties}

1. Wählen Sie **Formulare** > **Briefe**.

1. Wählen Sie **Erstellen > Brief**. Correspondence Management zeigt die verfügbaren Layouts (XDPs) an. Diese Layouts stammen von Designer. Die Layouts enthalten auch die Briefvorlagen, die Correspondence Management standardmäßig bereitstellt. Weitere Informationen finden Sie unter [Referenzieren von Briefvorlagen](/help/forms/using/reference-cm-layout-templates.md). Um Ihre eigenen Layouts hinzuzufügen, erstellen Sie XDP-Dateien (Layout) in Designer und [laden Sie sie in AEM Forms hoch](/help/forms/using/get-xdp-pdf-documents-aem.md).

   ![create-letter](assets/create-letter.png)

1. Wählen Sie ein Layout durch Antippen aus und tippen Sie auf **Weiter**.

   ![Wählen Sie „Layout“, um einen Brief zu erstellen](assets/selectlayout.png)

1. Geben Sie die Eigenschaften für die Korrespondenz ein und tippen Sie auf **Speichern:**

   * **Titel (optional)**: Geben Sie einen Titel für den Brief ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nichtenglische Zeichen enthalten.
   * **Name**: Der eindeutige Name des Briefs. Es darf immer nur ein Brief mit einem bestimmten Namen in einem Status vorhanden sein. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch auf der Grundlage des Titelfelds vorausgefüllt. Die Sonderzeichen, Leerzeichen, Zahlen und die nichtenglischen Zeichen im Feld „Titel“ werden im Feld „Name“ durch Bindestriche ersetzt. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.
   * **Beschreibung (optional):** Geben Sie eine Beschreibung des Briefs als Referenz ein.
   * **Datenwörterbuch (optional)**: Das Datenwörterbuch kann mit der Korrespondenz verknüpft werden. Die Assets, die Sie später in diese Korrespondenz einfügen, sollten entweder dasselbe Datenwörterbuch wie Sie es für die Korrespondenz hier auswählen, oder gar kein Datenwörterbuch enthalten.
   * **Tags (optional)**: Wählen Sie die Tags aus, die auf die Korrespondenz angewendet werden sollen. Sie können auch einen neuen/benutzerdefinierten Tag-Namen eingeben und die Eingabetaste drücken, um ihn zu erstellen.
   * **Nachbearbeitungsprozess (optional)**: Wählen Sie den Nachbearbeitungsprozess aus, die auf die Briefvorlage angewendet werden soll. Es gibt sowohl standardmäßige Nachbearbeitungsprozesse als auch jene, die Sie mithilfe von AEM wie E-Mail und Druck erstellt haben.

   ![Eigenschaften der Korrespondenz](assets/createcorrespondenceproperties.png)

1. Das System zeigt eine Nachricht an: „Brief erfolgreich erstellt.“ Tippen Sie (in der Warnmeldung) auf **Öffnen**, um die darin enthaltenen Datenmodule und Layout-Fragmente zu konfigurieren. Oder tippen Sie auf **Fertig**, um zur vorherigen Seite zurückzukehren.

   ![Warnmeldung: Brief erfolgreich erstellt](assets/createcorrespondencecreated.png)

   **Weiter**: Wenn Sie auf **Öffnen** tippen, zeigt Correspondence Management eine Darstellung des Layouts an, in der alle Komponenten des Layouts (XDP) aufgeführt sind. Fahren Sie mit dem Einfügen des [Datenmodule und Layout-Fragmente und deren Konfiguration](/help/forms/using/create-letter.md#p-insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them-p).

### Fügen Sie Datenmodule und Layout-Fragmente in einen Brief ein und konfigurieren Sie sie {#insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them}

Wenn Sie nach dem Erstellen einer Korrespondenz auf „Öffnen“ tippen, zeigt Correspondence Management eine Darstellung des Layouts an, in der alle Unterformulare/Zielbereiche des Layouts (XDP) aufgelistet sind. Sie können in jeden Zielbereich entweder ein Datenmodul oder ein Layout-Fragment einfügen (und dann Datenmodule in das Layout-Fragment).

>[!NOTE]
>
>Sie können auch auf der Seite &quot;Briefe&quot;auf das Symbol &quot;Bearbeiten&quot;tippen, um Datenmodule und Layout-Fragmente in einen Brief einzufügen und sie zu konfigurieren.

1. Tippen Sie für jedes der Teilformulare auf **Einfügen** und wählen Sie Datenmodule oder ein Layout-Fragment zum Einfügen in jedes der Teilformulare aus.

   ![Fügen Sie Datenmodule und Layout-Fragmente ein](assets/insertdmandlf.png)

1. Wählen Sie für diese Optionen für jeweils jedes der Unterformulare „Datenmodul“ oder „Layout-Fragment“ aus und wählen Sie dann die einzufügenden Datenmodule oder Layout-Fragmente aus. Mit einem Layout-Fragment können Sie je nach Entwurf (bis zu vier Ebenen) weitere Datenmodule oder Layout-Fragmente darin einfügen.

   ![nestedlf](assets/nestedlf.png)

1. Wenn Sie ein Layout-Fragment einfügen, wird der Name des Layout-Fragments im Teilformular angezeigt. Je nach ausgewähltem Fragment werden verschachtelte Teilformulare im Teilformular angezeigt.
1. Nachdem die ausgewählten Datenmodule in das Layout eingefügt wurden, können Sie nach dem Tippen auf das Symbol Bearbeiten für jedes der Module auf Modus konfigurieren tippen und Folgendes festlegen:

   1. **Bearbeitbar**: Wenn diese Option aktiviert ist, kann der Inhalt in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;bearbeitet werden. Markieren Sie Inhalte nur dann als bearbeitbar, wenn der Business-Anwender (z. B. ein Schadensregulierer) sie ändern muss.
   1. **Obligatorisch**: Wenn diese Option aktiviert ist, ist der Inhalt in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;erforderlich.
   1. **Ausgewählt**: Wenn diese Option aktiviert ist, wird der Inhalt standardmäßig in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;ausgewählt.
   1. **Einzug**: Vergrößern oder verkleinern Sie den Einzug des Moduls/Inhalts im Brief. Einzüge werden in Form von Ebenen angegeben, beginnend bei null. Jede Ebene eingerückt 36 Pkt. Weitere Informationen zum Anpassen von Formularen finden Sie unter **[!UICONTROL Correspondence Management-Konfigurationen]** in [Forms-Workflow](submit-letter-topostprocess.md#formsworkflow).
   1. **Seitenumbruch vor**: Wenn Sie die Option &quot;Seitenumbruch vor&quot;auf &quot;Ein&quot;einstellen, werden die Inhalte DIESES Moduls immer auf einer neuen Seite angezeigt.
   1. **Seitenumbruch nach**: Wenn Sie für ein bestimmtes Modul die Option Seitenumbruch nach auf &quot;ein&quot;einstellen, werden die Inhalte des NEXT-Moduls immer auf einer neuen Seite angezeigt.

   ![Eingefügte Datenmodule und Layout-Fragmente](assets/insertdmandlf2.png)

1. Tippen Sie zum Bearbeiten eines Moduls auf das Symbol „Bearbeiten“ daneben. Tippen Sie nach Bearbeiten des Moduls auf **Speichern**.

   Auf dieser Seite können Sie für die Unterformulare auch die folgenden Optionen einstellen:

   1. **Freien Text zulassen**: Wenn die Option „Freien Text zulassen“ aktiviert wird, dann kann der Benutzer in der CCR-Ansicht Inline-Text in einem Brief hinzufügen. In der CCR-Ansicht wird die Aktion ‚T‘ für jene Zielbereiche aktiviert, für die „Freien Text zulassen“ aktiviert wurde. Wenn der Benutzer darauf tippt, wird er nach einem Namen und einer Beschreibung des Textes gefragt. Anschließend tippt der Benutzer auf „OK“ und dieser Text wird im Bearbeitungsmodus geöffnet, damit der Benutzer Text hinzufügen kann. Das funktioniert wie andere Textmodule
   1. **Reihenfolge sperren**: Sperrt die Reihenfolge der Teilformulare im Brief. Der Autor darf die Teilformulare/Komponenten beim Erstellen des Briefs nicht neu anordnen.

   Auf dieser Seite können Sie auch für jedes der Assets in den Teilformularen die folgenden Schritte ausführen:

   1. **Reihenfolge der Assets ändern**: Ziehen Sie dazu das Symbol „Neu anordnen“ (![dragndrop](assets/dragndrop.png)) eines Assets per Drag-and-Drop an die gewünschte Stelle.
   1. **Assets löschen:** Tippen Sie neben dem Asset auf das Symbol „Löschen“, um das Asset zu löschen.
   1. **Vorschau von Assets**: Tippen Sie auf das Symbol „Vorschau anzeigen“ (![showpreview](assets/showpreview.png)) neben einem Asset.

1. Tippen Sie auf **Weiter**.
1. Auf der Seite &quot;Daten&quot;wird beschrieben, wie Datenfelder und Variablen in der Vorlage verwendet werden. Daten können mit Datenquellen wie einem Datenwörterbuch oder einer Benutzereingabe verknüpft werden. Jedes Feld definiert Eigenschaften, aus denen Datenwörterbücher Daten zuordnen oder welche Beschriftungen für Benutzereingabefelder angezeigt werden.

   Linkage:

   * Die **field** -Elemente können mit einem Literal, einem Datenwörterbuchelement, einem Asset oder einem vom Benutzer angegebenen Wert verknüpft werden. Sie können ein Feldelement auch ignorieren, indem Sie es an die Option Ignorieren binden.
   * Die **Variable** -Elemente können mit einem Literal, einem Datenwörterbuchelement, einem Feld, einer Variablen, einem Asset oder einem vom Benutzer angegebenen Wert verknüpft werden.

   Im Folgenden finden Sie einige Hauptfelder in der Verknüpfung:

   * **Mehrzeilig**: Sie können angeben, ob die Dateneingabe für ein Feld oder eine Variable mehrzeilig ist. Wenn Sie diese Option auswählen, wird das Eingabefeld für das Feld oder die Variable in der Datenbearbeitungsansicht als mehrzeiliges Eingabefeld angezeigt. Das Feld oder die Variable wird in den Ansichten &quot;Daten&quot;und &quot;Inhalt&quot;der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;auch als mehrzeilig angezeigt. Das mehrzeilige Eingabefeld ähnelt dem Feld zur Eingabe von Kommentaren in einem Textmodul. Die Option „Mehrzeilig“ ist nur für Felder und Variablen mit Verbindungstyp „Benutzer“ oder nicht geschützte Datenlexikonelemente verfügbar.
   * **Optional**: Sie können angeben, ob der Wert für Feld oder Variable optional ist oder nicht. Die Option „Optional“ ist für Felder und Variablen mit Verbindungstyp Benutzer oder nicht geschützte Datenlexikonelemente verfügbar.

   * **Validierung des Feldes/der Variablen**: Zur verbesserten Validierung des Werts eines Felds oder einer Variablen können Sie dem Feld bzw. der Variablen einen Validator zuweisen. Die Option ist nur für Felder und Variablen mit Verbindungstyp „Benutzer“ oder nicht geschützte Datenlexikonelemente verfügbar.
   * **Beschriftung** und **QuickInfo**: Beschriftung ist die Beschreibung des Feldes, das in der CCR-Benutzeroberfläche vor dem Feld angezeigt wird. Diese Option ist für Felder und Variablen mit dem Verbindungstyp „Benutzer“ oder ungeschützte Elemente des Datenwörterbuchs verfügbar.

   Die folgenden Validierungstypen können für die Felder verwendet werden:

   * **String Validator**: Verwenden Sie den Validator für Zeichenfolge , um eine Mindest- und Höchstlänge der in das Feld oder die Variable eingegebenen Zeichenfolge anzugeben. Wenn Sie einen String-Validator erstellen, stellen Sie sicher, dass Sie gültige Validierungsparameter angeben. Geben Sie eine gültige Länge für die Mindest- und Höchstwerte ein. Für den Validator Zeichenfolge können Sie die Mindest- und Höchstlänge des eingegebenen Werts angeben. Wenn der eingegebene Wert nicht der angegebenen Mindest- und Höchstlänge entspricht, wird das entsprechende Feld in der CCR-Benutzeroberfläche rot markiert.

   * **Zahlenvalidator:** Verwenden Sie den Zahlenvalidator, um den minimalen und maximalen in ein Feld oder eine Variable eingegebenen numerischen Wert festzulegen. Stellen Sie beim Erstellen eines Zahlenvalidators sicher, dass Sie gültige Validierungsparameter angeben. Geben Sie für Mindest- und Höchstwerte numerische Werte ein.

   * **Validator für regulären Ausdruck**: Verwenden Sie den Validator für regulären Ausdruck , um einen regulären Ausdruck zu definieren, mit dem der Wert eines Felds oder einer Variablen validiert wird. Darüber hinaus können Sie die Fehlermeldung anpassen. Wenn Sie einen Validator für regulären Ausdruck erstellen, stellen Sie sicher, dass Sie einen gültigen regulären Ausdruck angeben.

   >[!NOTE]
   >
   >Die Validatoren für Felder und Variablen sind nur für Felder oder Variablen mit Verbindungstyp Benutzer oder nicht geschützte Datenlexikonelemente verfügbar.

   ![Verknüpfungen](assets/linkages.png)

1. Klicken Sie nach Angabe der Verknüpfung auf **Weiter**. Correspondence Management zeigt den Anhänge-Bildschirm an.

### Richten Sie die Anlagen ein {#set-up-the-attachments}

1. Wählen Sie **Medienelement hinzufügen**.
1. Klicken Sie im Bildschirm „Asset auswählen“ auf die Anlagen, die dem Brief angehängt werden sollen, und klicken Sie auf **Fertig**. Sie müssen die Anlagen zuerst in „Anlagen“ hochladen“. Es wird empfohlen, dass Sie nur PDF- und Microsoft Office-Dokumente anhängen. Sie können aber auch Bilder anhängen. Weitere Informationen über das Hochladen von Assets in DAM finden Sie unter [Assets hochladen](/help/assets/manage-assets.md).
1. Wenn Sie die Sortierreihenfolge festschreiben möchten, sodass der Schadensregulierer sie nicht ändern kann, tippen Sie auf **Sperrungsreihenfolge**. Wenn Sie diese Option nicht aktivieren, kann der Schadensregulierer die Reihenfolge der Listenelemente ändern.
1. Reihenfolge der Assets ändern: Ziehen Sie ein Assets per Drag and Drop, indem Sie das Symbol „Neu anordnen“ für ein Asset gedrückt halten (![dragndrop](assets/dragndrop.png)).
1. Tippen Sie auf **Bearbeiten** vor einer Anlage und geben Sie eine Anlage als Obligatorisch an, wenn Sie nicht möchten, dass der Verfasser diese löschen kann. Geben Sie eine Anlage als „Ausgewählt“ an, wenn sie in der CCR-Benutzeroberfläche vorausgewählt werden soll.
1. Wählen Sie **Bibliothekszugriff** aus, um Zugriff auf die Bibliothek zu gewähren. Wenn der Bibliothekszugriff aktiviert ist, kann der Schadensregulierer beim Erstellen eines Briefs auf die Inhaltsbibliothek zugreifen und Anlagen einfügen.
1. Wählen Sie **Anlagenkonfiguration** aus und geben Sie die maximale Anzahl von Anlagen an.

1. Tippen Sie auf **Speichern**. Ihre Korrespondenz wird erstellt und auf der Seite „Briefe“ aufgeführt.

Nachdem in Correspondence Management eine Briefvorlage erstellt wurde, kann der Endbenutzer/Agent/Schadensregulierer den Brief in der CCR-Benutzeroberfläche öffnen und durch Eingabe von Daten, Einrichten von Inhalten und Verwalten von Anlagen eine Korrespondenz erstellen. Weitere Informationen finden Sie unter [Korrespondenz erstellen](/help/forms/using/create-correspondence.md).

## Für jedes der Felder verfügbare Verknüpfungstypen {#types-of-linkage-available-for-each-of-the-fields}

In der folgenden Tabelle wird beschrieben, welche Verknüpfungstypen für verschiedene Feldtypen verfügbar sind.

Die folgenden Werte in der Tabelle

* **Ja:** Feldtyp in der Spalte ganz links unterstützt diesen Typ der Zuordnung
* **Nein:** Feldtyp in der Spalte ganz links unterstützt nicht diesen Typ der Zuordnung
* **Nicht zutreffend**: Feldtyp in der Spalte ganz links ist nicht zutreffend

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Literal</strong></td> 
   <td><strong>Asset</strong></td> 
   <td><strong>Datenwörterbuch</strong></td> 
   <td><strong>Groß-/Kleinschreibung</strong></td> 
   <td><strong>User</strong></td> 
   <td><strong>Feld</strong></td> 
   <td><strong>Variable</strong></td> 
  </tr> 
  <tr> 
   <td><strong>date</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>Zeit </strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>datetime</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>integer</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>float</strong></td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>richtext</strong></td> 
   <td>Ja</td> 
   <td>Nur Text</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>plain</strong> <strong>text</strong></td> 
   <td>Ja</td> 
   <td>Nur Text</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>image</strong></td> 
   <td>Nein</td> 
   <td>Nur Bild</td> 
   <td>Nein</td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td><strong>signature</strong></td> 
   <td>Nein</td> 
   <td>Nein</td> 
   <td>Nein<br /> </td> 
   <td>Ja</td> 
   <td>Nein</td> 
   <td>Nicht zutreffend</td> 
   <td>Nicht zutreffend<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Erstellen Sie eine Kopie einer Briefvorlage {#createcopylettertemplate}

Sie können eine vorhandene Briefvorlage verwenden, um schnell eine Briefvorlage mit ähnlichen Eigenschaften, Inhalten und vererbten Assets wie Dokumentfragmenten und Datenwörterbuch zu erstellen. Kopieren Sie dazu einen Brief und fügen Sie ihn ein.

1. Wählen Sie auf der Seite &quot;Briefe&quot;einen oder mehrere Buchstaben aus. Auf der Benutzeroberfläche wird das Symbol „Kopieren“ angezeigt.
1. Tippen Sie auf Kopieren. Auf der Benutzeroberfläche wird das Symbol „Einfügen“ angezeigt. Sie können vor dem Einfügen auch in einen Ordner wechseln. Verschiedene Ordner können Assets mit demselben Namen enthalten. Weitere Informationen zu Ordnern finden Sie unter [Ordner und Organisieren von Assets](/help/forms/using/import-export-forms-templates.md#folders-and-organizing-assets).
1. Tippen Sie auf „Einfügen“. Das Dialogfeld „Einfügen“ wird angezeigt. Wenn Sie die Briefe kopieren und an derselben Stelle einfügen, weist das System den neuen Kopien automatisch Namen und Titel zu, Sie können jedoch die Titel und Namen der Briefe bearbeiten.
1. Bearbeiten Sie bei Bedarf den Titel und den Namen, mit denen Sie die Kopie des Briefs speichern möchten.
1. Tippen Sie auf „Einfügen“. Die Kopie des Briefs wird erstellt. Jetzt können Sie die erforderlichen Änderungen in Ihrem neu erstellten Brief vornehmen.
