---
title: Einführung in das Authoring adaptiver Formulare
description: AEM Forms bietet eine benutzerfreundliche, aber leistungsstarke Benutzeroberfläche zum Authoring adaptiver Formulare. Es enthält eine Reihe von Komponenten und Werkzeugen, mit denen Sie Formulare erstellen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction, author
docset: aem65
feature: Adaptive Forms
exl-id: 935b734c-6fb1-45e8-8515-e98c8b85286c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3142'
ht-degree: 99%

---

# Einführung in das Authoring adaptiver Formulare {#introduction-to-authoring-adaptive-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/introduction-forms-authoring.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


## Übersicht {#overview}

Mit adaptiven Formularen können Sie Formulare erstellen, die ansprechend, reaktionsfähig, dynamisch und anpassungsfähig sind. AEM Forms bietet eine intuitive Benutzeroberfläche sowie vordefinierte Komponenten zum Erstellen und Verarbeiten von adaptiven Formularen. Sie können adaptive Formulare auf der Basis eines Formularmodells oder Schemas oder ohne Formularmodell erstellen. Es ist wichtig, sorgfältig ein Formularmodell zu wählen, das nicht nur Ihren Verwendungszwecken entspricht, sondern auch Ihre bestehenden Infrastrukturinvestitionen und -Assets erweitert. Zum Erstellen eines adaptiven Formulars werden die folgenden Optionen bereitgestellt:

* **Verwendung eines Formulardatenmodell**
  [Datenintegration](../../forms/using/data-integration.md) ermöglicht die Integration von Entitäten und Services aus unterschiedlichen Datenquellen in ein Formulardatenmodell, das Sie zum Erstellen adaptiver Formulare verwenden können. Wählen Sie das Formulardatenmodell, wenn Sie ein adaptives Formular erstellen, für das Daten aus mehreren Datenquellen abgerufen und in diese geschrieben werden sollen.

* **Verwenden einer XDP-Formularvorlage** Dieses Formularmodell ist ideal, wenn bereits ein Bestand an XFA- oder XDP-basierten Formularen vorhanden ist. Es bietet eine direkte Möglichkeit, Ihre XFA-basierten Formulare in adaptive Formulare zu konvertieren. Alle vorhandenen XFA-Regeln bleiben in den zugehörigen adaptiven Formularen erhalten. Die resultierenden adaptiven Formulare unterstützen XFA-Konstrukte, z. B. Überprüfungen, Ereignisse, Eigenschaften und Muster.

* **Verwendung einer XML-Schemadefinition (XSD) oder eines JSON-Schemas** XML- und JSON-Schemas stellen die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können das Schema mit einem adaptiven Formular verknüpfen und dem Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas sind für die Verwendung auf der Registerkarte „Datenmodellobjekte“ des Content Browser verfügbar, wenn sie adaptive Formulare erstellen.

* **Verwenden von &quot;none&quot;oder &quot;without&quot;(Formularmodell)**
Adaptive Formulare, die mit dieser Option erstellt wurden, verwenden kein Formularmodell. Die XML-Datendatei, die aus diesen Formularen generiert wird, hat eine flache Struktur mit Feldern und entsprechenden Werten.

Weitere Informationen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).

## Benutzeroberfläche für Authoring adaptiver Formulare {#adaptive-form-authoring-ui}

Die Touch-optimierte Benutzeroberfläche für das Erstellen adaptiver Formulare ist intuitiv bedienbar und bietet:

* Drag-and-Drop-Funktion
* Standardmäßige Formularkomponenten
* Integriertes Repository für Assets

Wenn Sie ein vorhandenes adaptives Formular erstellen oder bearbeiten, verwenden Sie die folgenden UI-Elemente:

* [Seitenleiste](#sidebar)
* [Seitensymbolleiste](#page-toolbar)
* [Komponenten-Symbolleiste](#component-toolbar)
* [Seite mit adaptivem Formular](#af-page)

![Benutzeroberfläche für Authoring adaptiver Formulare](assets/formeditor.png)

**A.** Seitenleiste **B.** Seitensymbolleiste **C.** Seite des adaptiven Formulars

### Seitenleiste {#sidebar}

Die Seitenleiste ermöglicht Ihnen Folgendes:

* Anzeigen von Formularinhalt wie Bereichen, Komponenten, Feldern und Layout.
* Bearbeiten von Komponenteneigenschaften.
* Suchen, Anzeigen und Verwenden von Assets in Ihrem DAM (AEM Digital Asset Management)-Repository.
* Hinzufügen von Komponenten im Formular.

![Randleiste](assets/sidebar-comps.png)

**A.** Inhalt-Browser **B.** Eigenschaften-Browser **C.** Assets-Browser **D.** Komponenten-Browser

<!--Click to enlarge

](assets/sidebar-comps-1.png) -->

Die Seitenleiste enthält folgende Browser:

* **Inhalt-Browser**
Im Inhalt-Browser können Sie Folgendes anzeigen

   * **Formularobjekte** Zeigt die Objekthierarchie des Formulars an. Der Autor kann zu bestimmten Formularkomponenten navigieren, indem er auf das entsprechende Element in der Formularobjektstruktur tippt. Der Autor kann in dieser Struktur Objekte suchen und neu anordnen.

   * **Datenmodellobjekte**
Hiermit können Sie die Formularmodellhierarchie anzeigen.
Damit können Sie Formularmodellelemente per Drag-and-Drop auf das adaptive Formular ziehen. Die hinzugefügten Elemente werden automatisch in Formularkomponenten konvertiert, während ihre ursprünglichen Eigenschaften beibehalten werden. Sie können Datenmodellobjekte anzeigen, wenn in Ihrem Formular ein XML-Schema, ein JSON-Schema oder eine XDP-Vorlage verwendet wird.

* **Eigenschaften-Browser**

  Hier können Sie die Eigenschaften einer Komponente bearbeiten. Die Eigenschaften sind je nach Komponente verschieden. So zeigen Sie die Eigenschaften des Containers für adaptive Formulare an:

  Wählen Sie eine Komponente aus und wählen Sie dann ![field-level](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und anschließend ![cmppr](assets/cmppr.png).

* **Assets-Browser**

  Trennt verschiedene Inhaltstypen wie Bilder, Dokumente, Seiten, Filme usw. voneinander.

* **Komponenten-Browser**

  Enthält Komponenten, mit denen Sie ein adaptives Formular erstellen können. Sie können Komponenten in das adaptive Formular ziehen, um Formularelemente hinzuzufügen, und hinzugefügte Elemente gemäß den Anforderungen konfigurieren. In der folgenden Tabelle sind die im Komponenten-Browser aufgelisteten Komponenten beschrieben.

<table>
 <tbody>
  <tr>
   <th><strong>Komponente</strong></th>
   <th><strong>Funktionalität</strong></th>
  </tr>
  <tr>
   <td>Adobe Sign Block</td>
   <td>Fügt einen Textblock mit Platzhaltern für Felder hinzu, die beim Signieren mit Adobe Sign ausgefüllt werden sollen.</td>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td>Fügt eine Schaltfläche hinzu, die Sie konfigurieren können, um Aktionen auszuführen, wie Speichern, Zurücksetzen, Weiter, Zurück usw.</td>
  </tr>
  <tr>
   <td>Captcha</td>
   <td>Fügt die CAPTCHA-Validierung mithilfe des Google reCAPTCHA-Service hinzu. Weitere Informationen finden Sie unter <a href="../../forms/using/captcha-adaptive-forms.md" target="_blank">Verwenden von CAPTCHA in adaptiven Formularen</a>.</td>
  </tr>
  <tr>
   <td>Diagramm</td>
   <td>Fügt ein Diagramm hinzu, das Sie in adaptiven Formularen und Dokumenten für die visuelle Darstellung von zweidimensionalen Daten in wiederholbaren Bereichen und Tabellenzeilen verwenden können.</td>
  </tr>
  <tr>
   <td>Kontrollkästchen</td>
   <td>Fügt ein Kontrollkästchen hinzu.</td>
  </tr>
  <tr>
   <td>Feld zur Datumseingabe</td>
   <td>Verwenden Sie die Komponente „Feld zur Datumseingabe“ in Ihrem Formular, damit Kundinnen und Kunden Tag, Monat und Jahr in drei separaten Feldern ausfüllen können. Sie können das Erscheinungsbild der Komponente anpassen und das Datumsformat ändern. Sie können beispielsweise Ihre Kunden Datumsangaben im Format TT.MM.JJ oder TT.MM.JJJJ eingeben lassen.</td>
  </tr>
  <tr>
   <td>Datumsauswahl</td>
   <td>Fügt für die Auswahl eines Datums ein Kalenderfeld hinzu.</td>
  </tr>
  <tr>
   <td>Dokumentfragment</td>
   <td>Ermöglicht das Hinzufügen wiederverwendbarer Komponenten einer Korrespondenz.</td>
  </tr>
  <tr>
   <td>Dokumentfragmentgruppe</td>
   <td>Ermöglicht das Hinzufügen einer Gruppe verwandter Dokumentfragmente, die Sie in einer Briefvorlage als zusammenhängende Einheit verwenden können.</td>
  </tr>
  <tr>
   <td>Dropdown-Liste</td>
   <td>Fügt eine Dropdown-Liste für Einzel- oder Mehrfachauswahl hinzu.</td>
  </tr>
  <tr>
   <td>E-Mail</td>
   <td><p>Fügt ein Feld zum Erfassen der E-Mail-Adresse hinzu. Die E-Mail-Komponente überprüft standardmäßig E-Mail-Adressen mit dem folgenden regulären Ausdruck.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td>
  </tr>
  <tr>
   <td>Dateianhang</td>
   <td><p>Fügt eine Schaltfläche hinzu, mit der Benutzer ergänzende Dokumente suchen und an das Formular anhängen können. An eine Dateianhangskomponente lassen sich mehrere Dateien anhängen. Sie können auch die **[!UICONTROL Maximale Dateigröße]** und **[!UICONTROL Unterstützte Dateitypen]** für die Anhänge im Eigenschaftenbrowser der Komponente angeben. </p> <p><strong> Hinweis: </strong><ul> <li> Die Komponente unterstützt nicht das Anhängen von Dateien mit Dateinamen, die mit den Zeichen (.) beginnen bzw. die Zeichen \ / : * ? " &lt; &gt; | ; % $ enthalten oder spezielle Dateinamen enthalten, die für Windows-Betriebssysteme reserviert sind, wie z. B. nul, prn, con, lpt oder com. </li> <li> Um mehrere Dateien an eine Dateianhangskomponente anzuhängen, die im Apple Safari-Browser geöffnet ist, wählen Sie die Dateien einzeln aus und hängen Sie sie einzeln an. Es ist nicht möglich, mehrere Dateien gleichzeitig auszuwählen und anzuhängen.</li> <li>Die Dateianhangskomponente unterstützt eine vordefinierte Gruppe von Dateiformaten in adaptiven Formularen, die für Adobe Sign aktiviert sind. Weitere Informationen finden Sie unter <a href="https://helpx.adobe.com/de/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text">Unterstützte Dateiformate</a>. </li></ul></p> </td>
  </tr>
  <tr>
   <td>Auflistung der Dateianhänge</td>
   <td>Fügt ein Feld hinzu, das alle mit der Dateianlagenkomponente hochgeladenen Anlagen auflistet.</td>
  </tr>
  <tr>
   <td>Kopfzeile<br /> </td>
   <td>Fügt die Kopfzeile hinzu, die normalerweise das Logo eines Unternehmens, den Titel des Formulars und eine Zusammenfassung enthält.<br /> </td>
  </tr>
  <tr>
   <td>den Namen Fußzeile zu</td>
   <td>Fügt die Fußzeile hinzu, die normalerweise Copyright-Informationen und Links zu anderen Seiten enthält. </td>
  </tr>
  <tr>
   <td>Bild</td>
   <td>Ermöglicht das Einfügen eines Bildes.</td>
  </tr>
  <tr>
   <td>Bildauswahl</td>
   <td>Ermöglicht es Ihrer Kundschaft, ein Bild auszuwählen, um Informationen bereitzustellen. Mithilfe dieser Informationen können Sie Ihrer Kundschaft personalisierte Dienste anbieten.</td>
  </tr>
  <tr>
   <td>Schaltfläche „Weiter“</td>
   <td>Fügt eine Schaltfläche hinzu, um zum nächsten Feld in einem Formular zu navigieren.</td>
  </tr>
  <tr>
   <td>Numerisches Feld</td>
   <td>Fügt ein Feld zum Erfassen numerischer Werte hinzu</td>
  </tr>
  <tr>
   <td>Numerische Schritte</td>
   <td>Verwenden Sie „Numerische Schritte“ in Ihrem Formular, damit Ihre Kundschaft einen numerischen Wert eingeben kann, den sie basierend auf einem vordefinierten numerischen Schritt erhöhen oder verringern kann.</td>
  </tr>
  <tr>
   <td>Bereich</td>
   <td><p>Fügt einen Bereich oder Unterbereich hinzu.</p> <p>Sie können auch eine Bedienfeldkomponente aus der Symbolleiste des übergeordneten Bedienfelds hinzufügen, indem Sie die Schaltfläche <span class="uicontrol">„Untergeordnetes Bedienfeld“</code> hinzufügen. In ähnlicher Weise können Sie mit der Funktion <span class="uicontrol">„Panel-Symbolleiste hinzufügen“ eine bedienfeldspezifische Symbolleiste</code> hinzufügen. Sie können die Position der Bedienfeld-Symbolleiste mithilfe des Dialogfelds „Bedienfeld bearbeiten“ konfigurieren.</p> </td>
  </tr>
  <tr>
   <td>Kennwortfeld</td>
   <td>Fügt ein Feld zum Erfassen eines Kennworts hinzu.</td>
  </tr>
  <tr>
   <td>Schaltfläche „Zurück“</td>
   <td>Fügt eine Schaltfläche hinzu, die Benutzende benötigen, um zur vorherigen Seite oder zum vorherigen Bedienfeld zurückzukehren.</td>
  </tr>
  <tr>
   <td>Optionsschaltfläche</td>
   <td>Fügt Optionsfelder hinzu.</td>
  </tr>
  <tr>
   <td>Zurücksetzen-Schaltfläche</td>
   <td>Fügt eine Schaltfläche zum Zurücksetzen von Formularfeldern hinzu.</td>
  </tr>
  <tr>
   <td>Schaltfläche „Speichern“</td>
   <td>Fügt eine Schaltfläche zum Speichern der Formulardaten hinzu.</td>
  </tr>
  <tr>
   <td>Freihändige Unterschrift</td>
   <td>Fügt ein Feld zum Erfassen von Freihandsignaturen hinzu.</td>
  </tr>
  <tr>
   <td>Trennzeichen</td>
   <td>Aktiviert die visuelle Trennung von Bereichen im Formular.</td>
  </tr>
  <tr>
   <td>Unterschriftsschritt</td>
   <td>Zeigt die im Formular angegebenen Informationen und die Unterschriftsfelder an, damit die Benutzerin bzw. der Benutzer das Formular überprüfen und unterschreiben kann.</td>
  </tr>
  <tr>
   <td>Text</td>
   <td>Ermöglicht es Ihnen, statischen Text anzugeben.</td>
  </tr>
  <tr>
   <td>Schaltfläche „Absenden“</td>
   <td>Fügt eine Schaltfläche zum Absenden hinzu, um das Formular an die konfigurierte Sendeaktion zu senden.</td>
  </tr>
  <tr>
   <td>Zusammenfassungsschritt</td>
   <td>Sendet das Formular und zeigt von den Autoren angegebenen Zusammenfassungstext an, nachdem das Formular gesendet wurde. </td>
  </tr>
  <tr>
   <td>Schalter</td>
   <td>Fügt einen Schalter hinzu, der einen Umschalter ausführt oder eine Aktion aktiviert/deaktiviert. Sie können nicht mehr als zwei Optionen in der Schalter-Komponente hinzufügen. Da ein Schalter nur zwei Werte haben kann: An und Aus, ist „Obligatorisch“ nicht verfügbar. Mindestens ein Wert wird unabhängig von der Benutzereingabe gespeichert. <br /> </td>
  </tr>
  <tr>
   <td>Tabelle</td>
   <td>Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. </td>
  </tr>
  <tr>
   <td>Telefonnummer</td>
   <td><p>Fügt ein Feld zum Erfassen der Telefonnummer hinzu. Mit der Komponente „Telefonnummer“ können Autoren einen der folgenden Telefonnummerntypen konfigurieren. Jeder Typ ist mit einem standardmäßigen regulären Ausdruck für die Validierung verknüpft.</p>
    <ul>
     <li>Der Typ „International“ wird durch <code>^[+][0-9]{0,14}$</code> validiert.</li>
     <li>Der Typ „USPhoneNumber“ wird durch <code>{'+1 ('999') '999-9999}</code> validiert.</li>
     <li>Der Typ „UKPhoneNumber“ wird durch <code>text{'+'99 999 999 9999}</code> validiert.</li>
     <li>Beim Typ „Benutzerdefiniert“ steht kein standardmäßiges Validierungsmuster zur Verfügung. Er nimmt den Wert des zuletzt ausgewählten Telefonnummerntyps an. Sie können auch ein eigenes, benutzerdefiniertes Validierungsmuster angeben.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Geschäftsbedingungen<br /> </td>
   <td>Fügt ein Feld hinzu, mit dem Autorinnen und Autoren die allgemeinen Geschäftsbedingungen angeben können, damit Benutzende diese überprüfen, bevor sie das Formular ausfüllen.</td>
  </tr>
  <tr>
   <td>Textfeld </td>
   <td><p>Fügt ein Textfeld hinzu, in dem Benutzende die erforderlichen Informationen angeben können. </p> <p>In der Textfeldkomponente kann standardmäßig nur einfacher Text angegeben werden. Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. In Textkomponenten mit Rich-Text stehen Optionen zum Hinzufügen von Überschriften, zum Ändern des Schriftstils (Fett, Kursiv, Unterstrichen), zum Erstellen geordneter und ungeordneter Listen, zum Ändern des Texthintergrunds und der Textfarbe sowie zum Hinzufügen von Hyperlinks zur Verfügung. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie die Option <strong>Rich Text erlauben</strong> in den Komponenteneigenschaften.</p> </td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Geben Sie einen Titel für das adaptive Formular an.</td>
  </tr>
  <tr>
   <td>Überprüfungsschritt</td>
   <td><p>Fügt einen Platzhalter hinzu, um das ausgefüllte Formular zur Überprüfung durch die Benutzenden anzuzeigen.</p> <p><strong>Hinweis</strong>: Adaptive Formulare, die die Überprüfungskomponente enthalten, unterstützen keine anonymen Benutzenden. Außerdem wird davon abgeraten, die Überprüfungskomponente in einem adaptiven Formularfragment zu verwenden.</p> </td>
  </tr>
 </tbody>
</table>

#### Optimale Verfahren für das Arbeiten mit Komponenten {#best-practices}

Einige Best Practices und wichtige Hinweise zum Arbeiten mit Komponenten von adaptiven Formularen:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Wählen Sie zum Konfigurieren der Eigenschaften einer Komponente erst die Komponente und dann ![cmppr](assets/cmppr.png), um die Komponenteneigenschaften im Eigenschaften-Browser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. Wenn Sie ![cmppr](assets/cmppr.png) auswählen, können Sie den Namen der Komponente ändern, indem Sie den Wert des Felds **[!UICONTROL Elementname]** im Eigenschaften-Browser ändern. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_). Andere Sonderzeichen sind nicht zulässig, und der Elementname sollte mit einem Buchstaben beginnen.

* Sie können die title-Eigenschaft einer Komponente eines adaptiven Formulars inline im Formular-Editor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel im Formular sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie eine Komponente aus, in der die Eigenschaft **[!UICONTROL Titel]** vorhanden und deren Eigenschaft **[!UICONTROL Titel ausblenden]** deaktiviert ist.

   1. Wählen Sie ![aem_6_3_edit](assets/aem_6_3_edit.png) aus, damit der Titel bearbeitet werden kann.

   1. Ändern Sie den Titel und drücken Sie die Eingabetaste oder wählen Sie eine beliebige Stelle außerhalb der Komponente aus, um die Änderungen zu speichern. Drücken Sie die Esc-Taste, um die Änderungen zu verwerfen.

* Bei einigen Komponenten für adaptive Formulare, z. B. E-Mail und Telefon, stehen vordefinierte Überprüfungsmuster zur Verfügung. Sie können jedoch eine benutzerdefinierte Validierung angeben, indem Sie das Feld **[!UICONTROL Validierungsmuster]** unter dem Akkordeon „Muster“ in den Komponenteneigenschaften aktualisieren. Weitere Informationen zu Standardvalidierungen finden Sie in den Komponentenbeschreibungen in der Tabelle oben.

* Felder in adaptiven Formularen, z. B. numerische Felder und E-Mail, können so konfiguriert werden, dass spezifische HTML5-Eingabetypen einbezogen werden. Wenn diese Felder auf Mobilgeräten und Tablets im Fokus sind, enthält die Tastatur direkt spezifische Buchstaben, Zahlen und andere Zeichen, die häufig für die Eingabe von Informationen in das betreffende Feld verwendet werden. Damit können Benutzer schnell Informationen eingeben, ohne zwischen Zeichensätzen auf der Tastatur zu wechseln. Um spezielle Eingaben für eine Komponente zu ermöglichen, aktivieren Sie das Kontrollkästchen **[!UICONTROL HTML-Typnummer verwenden]** in den Komponenteneigenschaften.

* Sie können die Eingabe von Rich Text in einer Textfeldkomponente ermöglichen. Um Rich Text für ein Textfeld zu aktivieren, aktivieren Sie das Kontrollkästchen **[!UICONTROL Rich Text zulassen]** in den Komponenteneigenschaften.

* Mithilfe von Textfeld-, E-Mail- und Telefonkomponenten können Sie in Feldern wie Name, Adresse, Kreditkarte, Telefon und E-Mail automatisch Werte aus den Daten übernehmen lassen, die in den Browsereinstellungen für das automatische Ausfüllen gespeichert sind. Um diese Funktion zu aktivieren, wählen Sie **[!UICONTROL Automatisches Ausfüllen aktivieren]** in den Komponenteneigenschaften und ein **[!UICONTROL Attribut für automatisches Ausfüllen]** aus. Wenn jemand ein adaptives Formular ausfüllt, werden Werte aus dem Profil für automatisches Ausfüllen im Browser oder anhand früher von der Person eingegebener Werte vorgeschlagen. Beachten Sie, dass das automatische Ausfüllen nur funktioniert, wenn die Einstellungen für automatisches Ausfüllen im Browser des Benutzers aktiviert sind.

* Geben Sie in den Komponenteneigenschaften Werte für Optionsfeld- und Kontrollkästchenelemente im Format `{value}={text}` an.
* Die Dateianlagenkomponente ermöglicht es Benutzenden standardmäßig, nur eine Datei anzuhängen. Sie können die Komponenteneigenschaften jedoch so konfigurieren, dass mehrere Anhänge unterstützt werden. Wenn mehrere Dateien mit demselben Dateinamen angehängt werden, können die Anhänge einige Probleme verursachen. Daher wird empfohlen, bei der Formularübermittlung für jeden gesendeten Anhang eine eindeutige Kennung damit zu verknüpfen. Gehen Sie dazu wie folgt vor:

   1. Navigieren Sie auf Ihrem AEM Forms-Server zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Webkonsole]**.
   1. Suchen Sie nach **[!UICONTROL Konfigurationsdienst für adaptive Formulare]** und wählen Sie ihn aus.
   1. Aktivieren Sie im Dialog „Konfigurations-Service für adaptive Formulare“ **[!UICONTROL Dateinamen individualisieren]**. Diese Option ist standardmäßig deaktiviert.

* Damit Benutzende eine PDF-Datei mit dem Safari-Browser anhängen können, stellen Sie sicher, dass **application/pdf** zur Eigenschaft „Unterstützte Dateitypen“ der Dateianhangskomponente hinzugefügt wird. Adaptive Formulare, die mit einer früheren AEM Forms-Version erstellt wurden, enthalten möglicherweise **.pdf** anstelle von **application/pdf** in der Eigenschaft „Unterstützte Dateitypen“.

Weitere Informationen zum optimalen Arbeiten mit adaptiven Formularen finden Sie unter [Best Practices für die Arbeit mit adaptiven Formularen](/help/forms/using/adaptive-forms-best-practices.md).

>[!NOTE]
>
>Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.

### Seitensymbolleiste {#page-toolbar}

Die Seitensymbolleiste oben bietet Optionen, mit denen Sie eine Vorschau des Formulars anzeigen, Formulareigenschaften ändern und das Formular-Layout bearbeiten können. Sie können beim Verfassen eine Vorschau des Formulars anzeigen und die gewünschten Änderungen vornehmen. In der Symbolleiste der Seite wird Folgendes angezeigt:

* **Seitliches Bedienfeld ein/aus** ![toggle-side-panel](assets/toggle-side-panel.png): Hiermit können Sie die Seitenleiste ein- oder ausblenden.

* **Seiteninformationen** ![theme-options](assets/theme-options.png): Hier können Sie Seiteneigenschaften anzeigen, ein Formular veröffentlichen bzw. dessen Veröffentlichung zurücknehmen, einen Formular-Workflow starten und ein Formular auf der klassischen Benutzeroberfläche öffnen.

* **Emulator** ![ruler](assets/ruler.png): Hiermit können Sie die Darstellung des Formulars für verschiedene Displaygrößen (z. B. für Tablets und Mobiltelefone) emulieren.

* **Bearbeiten**: Hiermit können Sie andere Modi auswählen, wie etwa: **[!UICONTROL Bearbeiten]**, **[!UICONTROL Stil]**, **[!UICONTROL Entwickler]** und **[!UICONTROL Design]**.

   * **Bearbeiten**: Hiermit können Sie die Eigenschaften des Formulars und seiner Komponenten bearbeiten. Dies tun Sie, indem Sie beispielsweise eine Komponente hinzufügen, ein Bild ablegen oder obligatorische Felder festlegen.
   * **Stil**: Hiermit können Sie das Erscheinungsbild von Komponenten im Formular stilistisch anpassen. Im Stilmodus können Sie beispielsweise einen Bereich auswählen und dessen Hintergrundfarbe festlegen.

   * **Entwickler**: Hier haben Entwickler folgende Möglichkeiten:

      * Ermitteln der Bestandteile von Formularen.
      * Debuggen Sie, was wo und wann passiert, was wiederum hilft, Probleme zu lösen.

   * **Design**: Hier können Sie benutzerdefinierte Komponenten oder auch nicht in der Seitenleiste aufgelistete vordefinierte Komponenten aktivieren oder deaktivieren.

* **Vorschau**: Hier können Sie das Aussehen des Formulars bei Veröffentlichung in einer Vorschau anzeigen.

### Komponenten-Symbolleiste {#component-toolbar}

![Komponentensymbolleiste in der Touch-Benutzeroberfläche](assets/component-toolbar.png)

Wenn Sie eine Komponente auswählen, wird eine Symbolleiste angezeigt, mit der Sie sie bearbeiten können. Sie erhalten Optionen zum Ausschneiden, Einfügen, Verschieben und Angeben von Eigenschaften der Komponenten. Ihre Optionen sind:

A. **Konfigurieren**: Wenn Sie **[!UICONTROL Konfigurieren]** auswählen, werden die Komponenteneigenschaften in der Seitenleiste sichtbar. Durch das Konfigurieren dieser Eigenschaften können Sie das Benutzererlebnis beim Erfassen von Daten anpassen. Sie können den Elementnamen der Komponente ändern und den Beschriftungstext im Titelfeld der Komponente angeben. Mit dem Elementnamen können Sie Werte erfassen, die Benutzende mithilfe der Komponente eingeben. In den Komponenteneigenschaften geben Sie das Verhalten der Komponente an und verwalten die Benutzereingabe. Konfigurieren Sie Eigenschaften in der Seitenleiste, um Benutzerdaten zu erfassen und sie für die weitere Verarbeitung zu verwenden. Mit den Eigenschaften für den adaptiven Formularcontainer können Sie Clientbibliotheken, Layouts, Designs, Datensatzdokument-, Speicher-, Sende- und Metadateneinstellungen festlegen.

B. **Kopieren**: Sie können die Kopieroption verwenden, um eine Komponente zu kopieren und an anderen Positionen im Formular einzufügen. Wenn Sie eine Komponente einfügen, erhält die eingefügte Komponente einen neuen Elementnamen, behält jedoch die Eigenschaften der kopierten Komponente bei.

C.**Ausschneiden**: Sie können die Option zum Ausschneiden verwenden, um eine Komponente von einer Position im adaptiven Formular an eine andere Position zu verschieben.

D. **Löschen**: Hiermit können Sie die Komponente aus dem Formular löschen.

E. **Einfügen**: Hiermit können Sie eine Komponente oberhalb der ausgewählten Komponente einfügen.

F. **Einfügen**: Hiermit können Sie die mithilfe der oben genannten Optionen ausgeschnittene oder kopierte Komponente einfügen.

G. **Regeln bearbeiten**: Hiermit können Sie den Regel-Editor öffnen. Weitere Informationen finden Sie unter [Regel-Editor](../../forms/using/rule-editor.md).

H. **Gruppieren**: Mit dieser Funktion können Sie mehrere Komponenten auswählen, um sie zusammen auszuschneiden, zu kopieren oder einzufügen.

I. **Übergeordnet**: Hier können Sie das übergeordnete Element einer Komponente auswählen. Beispiel: Ein Textfeld, das innerhalb eines Unterabschnitts liegt, der seinerseits Teil eines Abschnitts ist. Der Abschnitt befindet sich im Stammbereich (guideRootPanel), und der adaptive Formular-Container ist einem Stammbereich (guideRootPanel) übergeordnet. Bei einer Komponente können Sie alle Optionen sehen, wobei die Sortierhierarchie von unten nach oben verläuft.

Wenn Sie beispielsweise für ein Textfeld **[!UICONTROL Übergeordnet]** auswählen, sehen Sie Folgendes:

* Unterabschnitt
* Abschnitt
* guideRootPanel
* Container für ein adaptives Formular

J. **Andere**: Bietet weitere Optionen für die Arbeit mit der ausgewählten Komponente.

* SOM-Ausdruck anzeigen
* Bereich als Fragment speichern (nur für Bereiche)
* Untergeordneten Bereich hinzufügen (nur für Bereiche)
* Bedienfeld-Symbolleiste hinzufügen (nur für Bereiche)
* Ersetzen (nicht für Bereiche)

### Seite mit adaptivem Formular {#af-page}

Die Seite mit dem adaptiven Formular enthält das eigentliche Formular. Sie wird wie jede andere WCM-Seite als WCM-`cq:Page`-Komponente modelliert. Die folgende Abbildung zeigt die Inhaltsstruktur eines typischen adaptiven Formulars an.

![Inhaltstruktur einer WCM-Seite mit adaptivem Formular](assets/afstructure.png)

Die Inhaltsstruktur enthält in der Regel die folgenden Hauptkomponenten:

* **guideContainer**: Der Stamm eines adaptiven Formulars, der als **[!UICONTROL Beginn eines adaptiven Formulars]** in der Benutzeroberfläche des adaptiven Formulars markiert ist. In dieser Komponente können Sie Folgendes angeben:

   * *Layout des adaptiven Formulars für Mobilgeräte*: Definiert die Darstellung des Formulars auf mobilen Geräten.
   * *Dankeseite*: Definiert die Seite, auf die die Benutzenden nach dem Senden des Formulars umgeleitet werden.
   * *Übermittlungsaktion*: Definiert, wie das Formular auf dem Server verarbeitet wird, sobald die Benutzenden das Formular absenden.
   * *Stile*: Gibt den Pfad zur CSS-Datei an, die zum Anpassen des Erscheinungsbilds des Formulars verwendet wird.

* **rootPanel:** Der Stammbereich eines adaptiven Formulars. Er kann Unterbereiche unter dem Elementknoten enthalten. Jedem Bereich einschließlich des Stammbereichs kann ein Layout zugeordnet sein. Das Layout des Bereichs bestimmt das Layout des Formulars. Im Akkordeonlayout beispielsweise werden die Elemente als Akkordeonschritte angeordnet.

* **Symbolleiste:** Ein Container für ein adaptives Formular verfügt über eine zugehörige globale Symbolleiste, die global für das Formular gilt. Diese Symbolleiste kann mit der Aktion **[!UICONTROL Symbolleiste hinzufügen]** in der Bearbeitungsleiste hinzugefügt werden. Damit können Autoren Aktionen wie Übermitteln, Speichern, Zurücksetzen usw. hinzufügen.

* **assets**: Dieser Knoten enthält zusätzliche Informationen für das Formular-Authoring. Beispiele: Formularmodelldetails, Lokalisierungsdetails usw).
