---
title: Entwicklung von Formularen (klassische Benutzeroberfläche)
seo-title: Entwicklung von Formularen (klassische Benutzeroberfläche)
description: Lernen Sie das Entwickeln von Formularen
seo-description: Lernen Sie das Entwickeln von Formularen
uuid: 33859f29-edc5-4bd5-a634-35549f3b5ccf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 6ee3bd3b-51d1-462f-b12e-3cbe24898b85
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Entwicklung von Formularen (klassische Benutzeroberfläche){#developing-forms-classic-ui}

Die grundlegende Struktur eines Formulars sieht wie folgt aus:

* Beginn des Formulars
* Formularelemente
* Ende des Formulars

All diese Teile werden mit einer Reihe standardmäßiger [Formularkomponenten ](/help/sites-authoring/default-components.md#form) realisiert, die in einer Standard-AEM-Installation verfügbar sind.

Neben der [Entwicklung neuer Komponenten](/help/sites-developing/developing-components-samples.md) für Ihre Formulare ist auch Folgendes möglich:

* [Ein Formular vorab mit Werten ausfüllen](#preloading-form-values)
* [(Bestimmte) Felder mit mehreren Werten vorab ausfüllen 
   ](#preloading-form-fields-with-multiple-values)
* [Neue Aktionen entwickeln](#developing-your-own-form-actions)
* [Neue Einschränkungen entwickeln](#developing-your-own-form-constraints)
* [Bestimmte Formularfelder ein- oder ausblenden](#showing-and-hiding-form-components)

[Skripte verwenden](#developing-scripts-for-use-with-forms), um die Funktionalität bei Bedarf zu erweitern.

>[!NOTE]
>
>Dieses Dokument befasst sich hauptsächlich mit der Entwicklung von Formularen mit den [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md) in der klassischen Benutzeroberfläche. Adobe empfiehlt, bei der Formularentwicklung in der Touch-optimierten Benutzeroberfläche die neuen [Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) und [Ausblendebedingungen](/help/sites-developing/hide-conditions.md) zu nutzen.

## Vorausfüllen von Formularwerten {#preloading-form-values}

Die Formular-Start-Komponente stellt ein Feld für den **Ladepfad** bereit. Dies ist ein optionaler Pfad, der auf einen Knoten im Repository verweist.

Der Ladepfad ist der Pfad zu den Knoteneigenschaften, mit dem vordefinierte Werte in mehrere Felder im Formular geladen werden.

Dies ist ein optionales Feld, das den Pfad zu einem Knoten im Repository angibt. Wenn dieser Knoten Eigenschaften hat, die den Feldnamen entsprechen, werden die jeweiligen Felder im Formular vorab mit den Werten dieser Eigenschaften ausgefüllt. Wenn keine Übereinstimmung besteht, steht im Feld der Standardwert.

>[!NOTE]
>
>Eine [Formularaktion](#developing-your-own-form-actions) kann auch festlegen, von welcher Ressource die Anfangswerte geladen werden. This is done using `FormsHelper#setFormLoadResource` inside `init.jsp`.
>
>Das Formular wird nur über den Pfad, den der Autor in der Formular-Start-Komponente festgelegt hat, ausgefüllt, wenn dies nicht festgelegt wurde.

### Vorabladen von Formularfeldern mit mehreren Werten {#preloading-form-fields-with-multiple-values}

Einige Formularfelder haben auch den **Element-Ladepfad**. Dies ist ein weiterer optionaler Pfad, der auf einen Knoten im Repository verweist.

Der **Element-Ladepfad** ist der Pfad zu Knoteneigenschaften, mit dem vordefinierte Werte in dieses Formularfeld geladen werden – z. B. eine [Dropdown-Liste](/help/sites-authoring/default-components-foundation.md#dropdown-list), eine [Gruppe von Kontrollkästchen](/help/sites-authoring/default-components-foundation.md#checkbox-group) oder eine [Gruppe von Optionsschaltern](/help/sites-authoring/default-components-foundation.md#radio-group).

#### Beispiel: Vorabladen einer Dropdown-Liste mit mehreren Werten {#example-preloading-a-dropdown-list-with-multiple-values}

Eine Dropdown-Liste kann mit Ihren Werten konfiguriert werden, die ausgewählt werden können.

Mit dem **Element-Ladepfad** kann auf eine Liste aus einem Ordner im Repository zugegriffen werden, die in das Feld geladen wird:

1. Create a new sling folder ( `sling:Folder`)
for example, `/etc/designs/<myDesign>/formlistvalues`

1. Add a new property (for example, `myList`) of type multi-value string ( `String[]`) to contain the list of drop down items. Sie können auch mithilfe eines Skripts Inhalte importieren, z. B. mit einem JSP-Skript oder cURL in einem Shell-Skript.

1. Use the full path in the **Items Load Path** field:
for example, `/etc/designs/geometrixx/formlistvalues/myList`

Note that if the values in the `String[]` are of the formatted like this:

* `AL=Alabama`
* `AK=Alaska`
* *usw.*

generiert AEM die Liste wie folgt:

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

Diese Funktion kann beispielsweise in einer mehrsprachigen Umgebung nützlich sein.

### Entwicklung Ihrer eigenen Formularaktionen {#developing-your-own-form-actions}

Für ein Formular ist eine Aktion erforderlich. Die Aktion bestimmt den Vorgang, der ausgeführt wird, wenn das Formular mit Benutzerdaten eingereicht wird.

Mit einer Standardinstallation von AEM stehen verschiedene Aktionen zur Verfügung. Sie finden diese unter:

`/libs/foundation/components/form/actions`

und in der **Action Type**-Liste der **Formular**-Komponente:

![chlimage_1-8](assets/chlimage_1-8.png)

Dieser Abschnitt erläutert, wie Sie Ihre eigene Formularaktion entwickeln und zu dieser Liste hinzufügen können.

You can add your own action under `/apps` as follows:

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Aktion entspricht.

   Beispiel:

   `/apps/myProject/components/customFormAction`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType` - festgelegt als `foundation/components/form/action`

   * `componentGroup` - definieren als `.hidden`

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Dropdown-Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt

      * `jcr:description` - Geben Sie eine Beschreibung Ihrer Wahl ein

1. Erstellen Sie im Ordner einen Dialogknoten:

   1. Fügen Sie Felder hinzu, damit der Autor das Formular-Dialogfeld bearbeiten kann, nachdem die Aktion ausgewählt wurde.

1. Im Ordner erstellen Sie entweder:

   1. Ein Postskript.
The name of the script is `post.POST.<extension>`, e.g. `post.POST.jsp`
The post script is invoked when a form is submitted to process the form, it contains the code that handles the data arriving from the form `POST`.

   1. Fügen Sie ein Weiterleitungsskript hinzu, das aufgerufen wird, wenn das Formular eingereicht wird.
Der Name des Skripts ist `forward.<extension`>, z.B. kann `forward.jsp`dieses Skript einen Pfad definieren. Die aktuelle Anfrage wird dann an den angegebenen Pfad weitergeleitet.
   The necessary call is `FormsHelper#setForwardPath` (2 variants). Ein typischer Anwendungsfall besteht darin, eine Validierung oder Logik auszuführen, um den Zielpfad zu finden, und anschließend zu diesem Pfad weiterzuleiten. Dabei wird die Speicherung in JCR dem standardmäßigen Sling-POST-Servlet überlassen.

   Es kann auch ein weiteres Servlet verwendet werden, das die eigentliche Verarbeitung übernimmt. In diesem Fall stellen die Formularaktion und `forward.jsp` nur die Verbindung dar. An example of this is the mail action at `/libs/foundation/components/form/actions/mail`, which forwards details to `<currentpath>.mail.html`where a mail servlet sits.

   Das bedeutet:

   * Ein `post.POST.jsp` eignet sich für kleine Vorgänge, die vollständig von der Aktion selbst ausgeführt werden.
   * `forward.jsp` ist hingegen hilfreich, wenn nur Delegation erforderlich ist.
   Die Skripte werden in folgender Reihenfolge ausgeführt:

   * Upon rendering the form ( `GET`):

      1. `init.jsp`
      1. for all field&#39;s constraints: `clientvalidation.jsp`
      1. form&#39;s validationRT: `clientvalidation.jsp`
      1. Das Formular wird über eine Laderessource geladen, wenn dies festgelegt ist
      1. `addfields.jsp` while inside rendering `<form></form>`
   * upon handling a form `POST`:

      1. `init.jsp`
      1. for all field&#39;s constraints: `servervalidation.jsp`
      1. form&#39;s validationRT: `servervalidation.jsp`
      1. `forward.jsp`
      1. Wenn ein Weiterleitungspfad festgelegt wurde (`FormsHelper.setForwardPath`), leiten Sie die Anfrage weiter und rufen Sie anschließend `cleanup.jsp` auf

      1. Wenn kein Weiterleitungspfad festgelegt wurde, rufen Sie `post.POST.jsp` auf (der Vorgang ist hier beendet, `cleanup.jsp` wird nicht aufgerufen)




1. Auch hier können Sie optional Folgendes zum Ordner hinzufügen:

   1. Ein Skript für das Hinzufügen von Feldern.
Der Name des Skripts wird `addfields.<extension>`z. B. `addfields.jsp`Ein addfields-Skript wird unmittelbar nach dem Schreiben des HTML für den Formularstart aufgerufen. Dadurch kann die Aktion benutzerdefinierte Eingabefelder oder sonstigen HTML-Code in das Formular einfügen.

   1. Ein Initialisierungsskript.
Der Name des Skripts wird `init.<extension>`z. B. `init.jsp`Dieses Skript wird aufgerufen, wenn das Formular wiedergegeben wird. Es kann zur Initialisierung von handlungsspezifischen Elementen verwendet werden. ``

   1. Ein Bereinigungsskript.
Der Name des Skripts ist `cleanup.<extension>`z.B. `cleanup.jsp`Dieses Skript kann zur Bereinigung verwendet werden.

1. Verwenden Sie die **Formular**-Komponente in einem parsys. Das Dropdown-Menü **Aktionstyp** enthält nun Ihre neue Aktion.

   >[!NOTE]
   >
   >So zeigen Sie weitere Standardaktionen, die im Produkt inbegriffen sind:
   >
   >
   >`/libs/foundation/components/form/actions`

### Entwicklung Ihrer eigenen Formulareinschränkungen {#developing-your-own-form-constraints}

Einschränkungen können auf zwei Ebenen angewendet werden:

* Für [einzelne Felder (siehe nachfolgendes Verfahren)](#constraints-for-individual-fields)
* Als [globale Validierung für das Formular](#form-global-constraints)

#### Einschränkungen für einzelne Felder {#constraints-for-individual-fields}

You can add your own constraints for an individual field (under `/apps`) as follows:

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Einschränkung entspricht.

   Beispiel:

   `/apps/myProject/components/customFormConstraint`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType` - festgelegt auf `foundation/components/form/constraint`

   * `constraintMessage`: eine individuelle Nachricht, die beim Einreichen des Formulars angezeigt wird, wenn das Feld gemäß der Einschränkung nicht gültig ist

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt
      * `hint`: zusätzliche Informationen für den Benutzer zur Verwendung dieses Felds

1. In diesem Ordner benötigen Sie möglicherweise auch die folgenden Skripte:

   * Ein Client-Überprüfungsskript:
Der Name des Skripts wird `clientvalidation.<extension>`beispielsweise aufgerufen, `clientvalidation.jsp`wenn das Formularfeld wiedergegeben wird. Es kann verwendet werden, um Client-JavaScript zur Validierung des Felds im Client zu erstellen.

   * Ein Serverüberprüfungsskript:
Der Name des Skripts wird `servervalidation.<extension>`beispielsweise aufgerufen, `servervalidation.jsp`wenn das Formular gesendet wird. Es kann verwendet werden, um das Feld auf dem Server zu validieren, nachdem das Formular eingereicht wurde.

>[!NOTE]
>
>Sie finden einige Beispiele für Einschränkungen unter:
>
>`/libs/foundation/components/form/constraints`

#### Globale Formulareinschränkungen {#form-global-constraints}

Legen Sie die globale Validierung eines Formulars fest, indem Sie einen Ressourcentyp in der Start-Formularkomponente angeben ( `validationRT`). Beispiel:

`apps/myProject/components/form/validation`

Anschließend können Sie Folgendes definieren:

* a `clientvalidation.jsp` - injected after the field&#39;s client validation scripts
* and a `servervalidation.jsp` - also called after the individual field server validations upon a `POST`.

### Ein- und Ausblenden von Formularkomponenten {#showing-and-hiding-form-components}

Sie können das Formular so konfigurieren, dass Formularkomponenten abhängig vom Wert anderer Formularfelder ein- oder ausgeblendet werden.

Das Ändern der Sichtbarkeit eines Formularfelds ist nützlich, wenn das Feld nur unter besonderen Bedingungen erforderlich ist. Auf einem Feedback-Formular werden Kunden beispielsweise gefragt, ob ihnen Produktinformationen per E-Mail zugesendet werden sollen. Nach der Auswahl von „Ja“ wird ein Textfeld eingeblendet, damit der Kunde seine E-Mail-Adresse eingeben kann.

Legen Sie mit dem Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** die Bedingungen fest, unter denen eine Formularkomponente ein- oder ausgeblendet wird.

![showhideeditor](assets/showhideeditor.png)

Legen Sie mit den Feldern, die im Dialogfeld oben sind, die folgenden Informationen fest:

* Ob Sie Bedingungen zum Ausblenden oder Einblenden der Komponente festlegen.
* Ob eine oder alle Bedingungen erfüllt sein müssen, um die Komponente ein- oder auszublenden.

Eine oder mehrere Bedingungen werden unter diesen Feldern eingeblendet. Eine Bedingung vergleicht den Wert einer anderen Formularkomponente (auf dem gleichen Formular) mit einem Wert. Wenn der tatsächliche Wert im Feld die Bedingung erfüllt, wird die Bedingung als wahr ausgewertet. Bedingungen enthalten die folgenden Informationen:

* Den Titel des Formularfeldes, das geprüft wird.
* Einen Operator.
* Einen Wert, mit dem der Feldwert verglichen wird.

Beispielsweise enthält eine Optionsfeldkomponente mit dem Titel `Receive email notifications?`* * `Yes` und `No` Optionsfelder. A Text Field component with the title of `Email Address` uses the following condition so that it is visible if `Yes` is selected:

![showhidebedingung](assets/showhidecondition.png)

In JavaScript verweisen Bedingungen mit dem Wert der Eigenschaft „Elementname“ auf Felder. In the previous example, the Element Name property of the Radio Group component is `contact`. Der folgende Code entspricht dem JavaScript-Code für dieses Beispiel:

`((contact == "Yes"))`

**Ein- oder Ausblenden einer Formular-Komponente:**

1. Bearbeiten Sie die entsprechende Formular-Komponente.

1. Wählen Sie **Einblenden/Ausblenden**, um das Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** zu öffnen:

   * Wählen Sie in der ersten Dropdown-Liste entweder **Einblenden** oder **Ausblenden** aus, um anzugeben, ob die Bedingungen das Einblenden oder das Ausblenden der Komponente bestimmen.

   * Wählen Sie in der Dropdown-Liste am Ende der obersten Zeile Folgendes aus:

      * **Alle**: Wenn alle Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden.
      * **Beliebig**: Wenn nur eine oder mehrere Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden
   * Wählen Sie in der Bedingungszeile (eine wird als Standard gezeigt) eine Komponente und einen Operator aus und geben Sie einen Wert an.
   * Klicken Sie bei Bedarf auf **Bedingung hinzufügen**, um weitere Bedingungen hinzuzufügen.
   Beispiel:

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Klicken Sie auf **OK**, um die Definition zu speichern.

1. Nachdem Sie Ihre Definition gespeichert haben, wird in den Eigenschaften der Formularkomponente der Link **Regeln bearbeiten** neben der Option **Einblenden/Ausblenden** angezeigt. Klicken Sie auf diesen Link, um das Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** zu öffnen, damit Sie Änderungen vornehmen können.

   Klicken Sie auf **OK**, um alle Änderungen zu speichern.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!CAUTION]
   >
   >Sie können die Auswirkungen von Ein-/Ausblendedefinitionen überprüfen und testen:
   >
   >
   >
   >    * im **Vorschaumodus** in der Autorenumgebung (Sie müssen die Seite neu laden, wenn Sie zum ersten Mal zur Vorschau wechseln)
      >
      >    
   * in der Veröffentlichungsumgebung


#### Behandlung von nicht mehr gültigen Komponentenverweisen {#handling-broken-component-references}

Einblenden/Ausblenden-Bedingungen verweisen mit dem Wert der Eigenschaft „Elementname“ auf andere auf dem Formular befindliche Komponenten. Die Konfiguration &quot;Ein-/Ausblenden&quot;ist ungültig, wenn eine der Bedingungen auf eine Komponente verweist, die gelöscht wurde oder deren Elementname geändert wurde. In diesen Fällen müssen Sie die Bedingungen manuell aktualisieren. Anderenfalls tritt beim Laden des Formulars ein Fehler auf.

Wenn die Konfiguration &quot;Anzeigen/Ausblenden&quot;ungültig ist, wird die Konfiguration nur als JavaScript-Code bereitgestellt. Bearbeiten Sie den Code, um die Probleme zu beheben. Der Code verwendet die Eigenschaft „Elementname“, mit der ursprünglich auf die Komponenten verwiesen wurde.

### Entwicklung von Skripten zur Verwendung mit Formularen {#developing-scripts-for-use-with-forms}

Weitere Informationen über die API-Elemente, die Sie zur Erstellung von Skripten verwenden können, finden Sie in den [javadocs zu Formularen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

Sie können dies z. B. verwenden, um einen Dienst aufzurufen, bevor das Formular übermittelt wird, und den Dienst abbrechen, wenn es fehlschlägt:

* Validierungs-Ressourcentyp definieren
* Aufnehmen eines Skripts zur Überprüfung:

   * Rufen Sie in der JSP den Webdienst auf und erstellen Sie ein Objekt `com.day.cq.wcm.foundation.forms.ValidationInfo` mit den Fehlermeldungen. Wenn Fehler auftreten, werden die Formulardaten nicht ausgegeben.
