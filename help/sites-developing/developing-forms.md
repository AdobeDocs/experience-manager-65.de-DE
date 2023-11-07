---
title: Entwickeln von Formularen (klassische Benutzeroberfläche)
seo-title: Developing Forms (Classic UI)
description: Erfahren Sie, wie Sie Formulare für die klassische Benutzeroberfläche von Adobe Experience Manager entwickeln.
seo-description: Learn how to develop forms
uuid: 33859f29-edc5-4bd5-a634-35549f3b5ccf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 6ee3bd3b-51d1-462f-b12e-3cbe24898b85
docset: aem65
exl-id: f43e9491-aa8f-40af-9800-123695142559
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '1946'
ht-degree: 54%

---

# Entwickeln von Formularen (klassische Benutzeroberfläche){#developing-forms-classic-ui}

Die grundlegende Struktur eines Formulars ist:

* Formularstart
* Formularelemente
* Formular-Ende

All diese Teile werden mit einer Reihe standardmäßiger [Formularkomponenten](/help/sites-authoring/default-components.md#form) realisiert, die in einer Standard-AEM-Installation verfügbar sind.

Neben der [Entwicklung neuer Komponenten](/help/sites-developing/developing-components-samples.md) für Ihre Formulare ist auch Folgendes möglich:

* [Ein Formular vorab mit Werten ausfüllen](#preloading-form-values)
* [(Bestimmte) Felder mit mehreren Werten vorab ausfüllen ](#preloading-form-fields-with-multiple-values)
* [Neue Aktionen entwickeln](#developing-your-own-form-actions)
* [Neue Einschränkungen entwickeln](#developing-your-own-form-constraints)
* [Bestimmte Formularfelder ein- oder ausblenden](#showing-and-hiding-form-components)

[Skripte verwenden](#developing-scripts-for-use-with-forms), um die Funktionalität bei Bedarf zu erweitern.

>[!NOTE]
>
>Dieses Dokument konzentriert sich auf die Entwicklung von Formularen mit dem [Foundation-Komponenten](/help/sites-authoring/default-components-foundation.md) in der klassischen Benutzeroberfläche. Adobe empfiehlt die Verwendung der neuen [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und [Bedingungen ausblenden](/help/sites-developing/hide-conditions.md) für die Formularentwicklung in der Touch-optimierten Benutzeroberfläche.

## Vorabladen von Formularwerten {#preloading-form-values}

Die Formular-Startkomponente stellt ein Feld für die **Ladepfad**, ein optionaler Pfad, der auf einen Knoten im Repository verweist.

Der Ladepfad ist der Pfad zu Knoteneigenschaften, mit dem vordefinierte Werte in mehrere Felder im Formular geladen werden.

Dies ist ein optionales Feld, das den Pfad zu einem Knoten im Repository angibt. Wenn dieser Knoten Eigenschaften hat, die den Feldnamen entsprechen, werden die jeweiligen Felder im Formular vorab mit den Werten dieser Eigenschaften ausgefüllt. Wenn keine Übereinstimmung besteht, steht im Feld der Standardwert.

>[!NOTE]
>
>A [Formularaktion](#developing-your-own-form-actions) kann auch die Ressource festlegen, von der die Anfangswerte geladen werden sollen. Dies erfolgt mit `FormsHelper#setFormLoadResource` in `init.jsp`.
>
>Nur wenn dies nicht festgelegt ist, wird das Formular vom Autor aus dem in der Formular-Startkomponente festgelegten Pfad ausgefüllt.

### Vorabladen von Formularfeldern mit mehreren Werten {#preloading-form-fields-with-multiple-values}

Verschiedene Formularfelder verfügen auch über die **Element-Ladepfad**, wiederum ein optionaler Pfad, der auf einen Knoten im Repository verweist.

Die **Element-Ladepfad** ist der Pfad zu den Knoteneigenschaften, mit denen vordefinierte Werte in dieses spezifische Feld im Formular geladen werden, z. B. ein [Dropdown-Liste](/help/sites-authoring/default-components-foundation.md#dropdown-list), [Kontrollkästchengruppe](/help/sites-authoring/default-components-foundation.md#checkbox-group) oder [Optionsfeldgruppe](/help/sites-authoring/default-components-foundation.md#radio-group).

#### Beispiel - Vorausfüllen einer Dropdown-Liste mit mehreren Werten {#example-preloading-a-dropdown-list-with-multiple-values}

Eine Dropdown-Liste kann mit Ihrem Wertebereich zur Auswahl konfiguriert werden.

Die **Element-Ladepfad** kann verwendet werden, um auf eine Liste aus einem Ordner im Repository zuzugreifen und sie in das Feld vorab zu laden:

1. Erstellen Sie einen Sling-Ordner ( `sling:Folder`), zum Beispiel `/etc/designs/<myDesign>/formlistvalues`

1. Hinzufügen einer neuen Eigenschaft (z. B. `myList`) vom Typ Zeichenfolge mit mehreren Werten ( `String[]`), um die Liste der Dropdown-Elemente zu enthalten. Sie können auch mithilfe eines Skripts Inhalte importieren, z. B. mit einem JSP-Skript oder cURL in einem Shell-Skript.

1. Verwenden Sie den vollständigen Pfad im Feld **Element-Ladepfad**.
Zum Beispiel `/etc/designs/geometrixx/formlistvalues/myList`

Hinweis: Wenn die Werte im `String[]` wie folgt formatiert sind:

* `AL=Alabama`
* `AK=Alaska`
* und so weiter

generiert AEM die Liste wie folgt:

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

Diese Funktion kann beispielsweise in einer mehrsprachigen Umgebung gut genutzt werden.

### Entwickeln eigener Formularaktionen {#developing-your-own-form-actions}

Für ein Formular ist eine Aktion erforderlich. Eine Aktion definiert den Vorgang, der ausgeführt wird, wenn das Formular mit den Benutzerdaten gesendet wird.

Eine Reihe von Aktionen wird mit einer standardmäßigen AEM-Installation bereitgestellt. Diese sind zu sehen unter:

`/libs/foundation/components/form/actions`

und in der **Action Type**-Liste der **Formular**-Komponente:

![chlimage_1-8](assets/chlimage_1-8.png)

Dieser Abschnitt erläutert, wie Sie Ihre eigene Formularaktion entwickeln und zu dieser Liste hinzufügen können.

Sie können Ihre eigene Aktion wie folgt unter `/apps` hinzufügen:

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Aktion entspricht.

   Beispiel:

   `/apps/myProject/components/customFormAction`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType`: als `foundation/components/form/action` festlegen

   * `componentGroup`: als `.hidden` definieren

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Dropdown-Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt

      * `jcr:description`: Geben Sie eine Beschreibung Ihrer Wahl ein

1. Erstellen Sie im Ordner einen Dialogfeldknoten:

   1. Fügen Sie Felder hinzu, damit der Autor das Dialogfeld &quot;Formulare&quot;bearbeiten kann, sobald die Aktion ausgewählt wurde.

1. Erstellen Sie im Ordner entweder:

   1. Ein Postskript.
Der Name des Skripts lautet `post.POST.<extension>`, beispielsweise `post.POST.jsp`
Das Post-Skript wird aufgerufen, wenn ein Formular zur Verarbeitung des Formulars gesendet wird. Es enthält den Code, der die aus dem Formular eingehenden Daten verarbeitet `POST`.

   1. Fügen Sie ein Weiterleitungsskript hinzu, das aufgerufen wird, wenn das Formular eingereicht wird.
Der Name des Skripts lautet `forward.<extension`>, z. B. `forward.jsp`
Dieses Skript kann einen Pfad definieren. Die aktuelle Anfrage wird dann an den angegebenen Pfad weitergeleitet.

   Der erforderliche Aufruf ist `FormsHelper#setForwardPath` (2 Varianten). Ein typischer Anwendungsfall besteht darin, eine Validierung oder Logik auszuführen, um den Zielpfad zu finden, und anschließend zu diesem Pfad weiterzuleiten. Dabei wird die Speicherung in JCR dem standardmäßigen Sling-POST-Servlet überlassen.

   Es kann auch ein weiteres Servlet verwendet werden, das die eigentliche Verarbeitung übernimmt. In diesem Fall stellen die Formularaktion und `forward.jsp` nur die Verbindung dar. Ein Beispiel dafür ist die E-Mail-Aktion unter `/libs/foundation/components/form/actions/mail`, die Details an `<currentpath>.mail.html` weiterleitet, wo sich ein E-Mail-Servlet befindet.

   Das bedeutet:

   * Ein `post.POST.jsp` eignet sich für kleine Vorgänge, die vollständig von der Aktion selbst ausgeführt werden.
   * `forward.jsp` ist hingegen hilfreich, wenn nur Delegation erforderlich ist.

   Die Skripte werden in folgender Reihenfolge ausgeführt:

   * Nach dem Rendering des Formulars ( `GET`):

      1. `init.jsp`
      1. Für alle Feldeinschränkungen: `clientvalidation.jsp`
      1. validationRT des Formulars: `clientvalidation.jsp`
      1. Das Formular wird über eine Laderessource geladen, wenn dies festgelegt ist
      1. `addfields.jsp` während des Renderings von `<form></form>`

   * Nach der Verarbeitung eines Formular-`POST`:

      1. `init.jsp`
      1. Für alle Feldeinschränkungen: `servervalidation.jsp`
      1. validationRT des Formulars: `servervalidation.jsp`
      1. `forward.jsp`
      1. Wenn ein Weiterleitungspfad festgelegt wurde (`FormsHelper.setForwardPath`), leiten Sie die Anfrage weiter und rufen Sie anschließend `cleanup.jsp` auf

      1. Wenn kein Weiterleitungspfad festgelegt wurde, rufen Sie `post.POST.jsp` auf (der Vorgang ist hier beendet, `cleanup.jsp` wird nicht aufgerufen)

1. Auch hier können Sie optional Folgendes zum Ordner hinzufügen:

   1. Ein Skript für das Hinzufügen von Feldern.
Der Name des Skripts lautet `addfields.<extension>`, beispielsweise `addfields.jsp`
Ein `addfields` wird unmittelbar nach dem Schreiben der HTML für den Formularstart aufgerufen. Dadurch kann die Aktion benutzerdefinierte Eingabefelder oder sonstigen HTML-Code in das Formular einfügen.

   1. Ein Initialisierungsskript.
Der Name des Skripts lautet `init.<extension>`, beispielsweise `init.jsp`
Dieses Skript wird aufgerufen, wenn das Formular wiedergegeben wird. Es kann zur Initialisierung von handlungsspezifischen Elementen verwendet werden.

   1. Ein Bereinigungsskript.
Der Name des Skripts lautet `cleanup.<extension>`, beispielsweise `cleanup.jsp`
Dieses Skript kann für die Bereinigung verwendet werden.

1. Verwenden Sie die **Forms** -Komponente in einem parsys. Die **Aktionstyp** -Dropdown-Liste enthält jetzt Ihre neue Aktion.

   >[!NOTE]
   >
   >So zeigen Sie Standardaktionen an, die Teil des Produkts sind:
   >
   >
   >`/libs/foundation/components/form/actions`

### Entwickeln eigener Formularbeschränkungen {#developing-your-own-form-constraints}

Beschränkungen können auf zwei Ebenen auferlegt werden:

* Für [einzelne Felder (siehe das folgende Verfahren)](#constraints-for-individual-fields)
* As [Formular-globale Validierung](#form-global-constraints)

#### Einschränkungen für einzelne Felder {#constraints-for-individual-fields}

Sie können wie folgt Ihre eigenen Einschränkungen für ein einzelnes Feld hinzufügen (unter `/apps`):

1. Erstellen Sie einen Knoten des Typs `sling:Folder`. Geben Sie einen Namen an, der der zu implementierenden Einschränkung entspricht.

   Beispiel:

   `/apps/myProject/components/customFormConstraint`

1. Definieren Sie in diesem Knoten die folgenden Eigenschaften und klicken Sie anschließend auf **Alle speichern**, um Ihre Änderungen zu speichern:

   * `sling:resourceType`: auf `foundation/components/form/constraint` festlegen

   * `constraintMessage` - eine benutzerdefinierte Meldung, die angezeigt wird, wenn das Feld gemäß der Einschränkung bei der Übermittlung des Formulars ungültig ist

   * Optional:

      * `jcr:title`: Geben Sie einen Titel Ihrer Wahl an, der in der Auswahlliste angezeigt wird. Wenn Sie dies nicht festlegen, wird der Name des Knotens angezeigt
      * `hint`: zusätzliche Informationen für den Benutzer zur Verwendung dieses Felds

1. In diesem Ordner benötigen Sie möglicherweise auch die folgenden Skripte:

   * Ein Client-Validierungsskript: Der Name des Skripts lautet `clientvalidation.<extension>`, beispielsweise `clientvalidation.jsp`
Dies wird aufgerufen, wenn das Formularfeld wiedergegeben wird. Es kann verwendet werden, um Client-JavaScript zur Validierung des Felds im Client zu erstellen.

   * Ein Servervalidierungsskript: Der Name des Skripts lautet `servervalidation.<extension>`, beispielsweise `servervalidation.jsp`
Dies wird beim Senden des Formulars aufgerufen. Sie kann verwendet werden, um das Feld auf dem Server zu validieren, nachdem es gesendet wurde.

>[!NOTE]
>
>Beispielbegrenzungen finden Sie unter:
>
>`/libs/foundation/components/form/constraints`

#### Globale Formulareinschränkungen {#form-global-constraints}

Legen Sie die globale Validierung eines Formulars fest, indem Sie einen Ressourcentyp in der Start-Formularkomponente angeben ( `validationRT`). Beispiel:

`apps/myProject/components/form/validation`

Anschließend können Sie Folgendes definieren:

* ein `clientvalidation.jsp`, das nach den Client-Validierungsskripten des Felds eingefügt wird
* und ein `servervalidation.jsp`, das auch nach den einzelnen Feld-Servervalidierungen bei einem `POST` aufgerufen wird.

### Ein- und Ausblenden von Formularkomponenten {#showing-and-hiding-form-components}

Sie können Ihr Formular so konfigurieren, dass Formularkomponenten entsprechend dem Wert anderer Felder im Formular ein- oder ausgeblendet werden.

Das Ändern der Sichtbarkeit eines Formularfelds ist nützlich, wenn das Feld nur unter besonderen Bedingungen erforderlich ist. Auf einem Feedback-Formular werden Kunden beispielsweise gefragt, ob ihnen Produktinformationen per E-Mail zugesendet werden sollen. Bei Auswahl von &quot;Ja&quot;erscheint ein Textfeld, in das der Kunde seine E-Mail-Adresse eingeben kann.

Legen Sie mit dem Dialogfeld **Einblenden-/Ausblenden-Regeln bearbeiten** die Bedingungen fest, unter denen eine Formularkomponente ein- oder ausgeblendet wird.

![showhideeditor](assets/showhideeditor.png)

Verwenden Sie die Felder oben im Dialogfeld, um die folgenden Informationen anzugeben:

* Gibt an, ob Sie Bedingungen zum Ausblenden oder Einblenden der Komponente festlegen.
* Ob eine oder alle Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden.

Eine oder mehrere Bedingungen werden unter diesen Feldern eingeblendet. Eine Bedingung vergleicht den Wert einer anderen Formularkomponente (im selben Formular) mit einem Wert. Wenn der tatsächliche Wert im Feld die Bedingung erfüllt, wird die Bedingung als wahr ausgewertet. Bedingungen enthalten die folgenden Informationen:

* Der Titel des Formularfelds, das getestet wird.
* Ein Operator.
* Ein Wert mit dem Feldwert wird verglichen.

Beispiel: eine Optionsfeldgruppen-Komponente mit dem Titel `Receive email notifications?`* * enthält die Optionsfelder `Yes` und `No`. Eine Textfeld-Komponente mit dem Titel `Email Address` verwendet die folgende Bedingung, damit sie sichtbar wird, wenn `Yes` ausgewählt wird:

![showhidecondition](assets/showhidecondition.png)

In JavaScript verwenden Bedingungen den Wert der Eigenschaft &quot;Elementname&quot;, um auf Felder zu verweisen. Im vorigen Beispiel ist `contact` der Wert der Eigenschaft „Elementname“ der Optionsfeld-Gruppen-Komponente. Der folgende Code entspricht dem entsprechenden JavaScript-Code für dieses Beispiel:

`((contact == "Yes"))`

**Ein- oder Ausblenden einer Formular-Komponente:**

1. Bearbeiten Sie die entsprechende Formular-Komponente.

1. Auswählen **Einblenden/Ausblenden** , um die **Einblenden-/Ausblenden-Regeln bearbeiten** dialog:

   * Wählen Sie in der ersten Dropdownliste entweder **Anzeigen** oder **Ausblenden** um anzugeben, ob Ihre Bedingungen bestimmen, ob die Komponente ein- oder ausgeblendet werden soll.

   * Wählen Sie in der Dropdownliste am Ende der obersten Zeile Folgendes aus:

      * **all** - wenn alle Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden
      * **any** - wenn nur eine oder mehrere Bedingungen wahr sein müssen, um die Komponente ein- oder auszublenden

   * Wählen Sie in der Bedingungszeile (standardmäßig eine) eine Komponente und einen Operator aus und geben Sie dann einen Wert an.
   * Fügen Sie bei Bedarf weitere Bedingungen hinzu, indem Sie auf **Bedingung hinzufügen**.

   Beispiel:

   ![chlimage_1-9](assets/chlimage_1-9.png)

1. Klicken Sie auf **OK**, um die Definition zu speichern.

1. Nachdem Sie Ihre Definition gespeichert haben, wird ein **Regeln bearbeiten** neben dem **Einblenden/Ausblenden** in den Eigenschaften der Formularkomponente. Klicken Sie auf diesen Link, um **Einblenden-/Ausblenden-Regeln bearbeiten** Dialogfeld, um Änderungen vorzunehmen.

   Klicks **OK** , um alle Änderungen zu speichern.

   ![chlimage_1-10](assets/chlimage_1-10.png)

   >[!CAUTION]
   >
   >Sie können die Auswirkungen von Ein-/Ausblendedefinitionen überprüfen und testen:
   >
   >* im **Vorschaumodus** in der Autorenumgebung (Sie müssen die Seite neu laden, wenn Sie zum ersten Mal zur Vorschau wechseln)
   >
   >* in der Veröffentlichungsumgebung

#### Umgang mit fehlerhaften Komponentenverweisen {#handling-broken-component-references}

Einblenden/Ausblenden-Bedingungen verweisen mit dem Wert der Eigenschaft „Elementname“ auf andere auf dem Formular befindliche Komponenten. Die Einblenden/Ausblenden-Konfiguration ist ungültig, wenn eine der Bedingungen auf eine Komponente verweist, die gelöscht oder bei der die Eigenschaft „Elementname“ geändert wurde. In diesen Fällen müssen Sie die Bedingungen manuell aktualisieren. Anderenfalls tritt beim Laden des Formulars ein Fehler auf.

Wenn die Einblenden/Ausblenden-Konfiguration ungültig ist, wird die Konfiguration nur als JavaScript-Code bereitgestellt. Bearbeiten Sie den Code, um die Probleme zu beheben. Der Code verwendet die Eigenschaft „Elementname“, mit der ursprünglich auf die Komponenten verwiesen wurde.

### Entwicklung von Skripten zur Verwendung mit Formularen {#developing-scripts-for-use-with-forms}

Weitere Informationen über die API-Elemente, die Sie zur Erstellung von Skripten verwenden können, finden Sie in den [javadocs zu Formularen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

Sie können dies z. B. verwenden, um einen Dienst aufzurufen, bevor das Formular übermittelt wird, und den Dienst abbrechen, wenn es fehlschlägt:

* Validierungs-Ressourcentyp definieren
* Aufnehmen eines Skripts zur Überprüfung:

   * Rufen Sie in der JSP den Webdienst auf und erstellen Sie ein Objekt `com.day.cq.wcm.foundation.forms.ValidationInfo` mit den Fehlermeldungen. Wenn Fehler auftreten, werden die Formulardaten nicht ausgegeben.
