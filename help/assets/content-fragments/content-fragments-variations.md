---
title: Varianten – Erstellen von Fragmentinhalten
description: Erfahren Sie, wie Sie mit Varianten Ihre Headless-Inhalte in AEM noch flexibler gestalten können. Sie können damit Inhalte für ein Fragment und dann entsprechend dem jeweiligen Verwendungszweck Varianten dieses Inhalts erstellen.
feature: Content Fragments
role: User
exl-id: 50982ede-7ccf-45b2-b0dd-a49d23e0f971
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2309'
ht-degree: 100%

---

# Varianten – Erstellen von Fragmentinhalten{#variations-authoring-fragment-content}

[Varianten](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) sind eine wichtige Funktion für Inhaltsfragmente in AEM, da sie Ihnen die Möglichkeit bieten, Kopien des primären Inhalts für die Verwendung in bestimmten Kanälen und/oder Szenarien zu erstellen und zu bearbeiten, was die Bereitstellung von Headless-Inhalten noch flexibler macht.

Auf der Registerkarte **Varianten** können Sie Folgendes tun:

* [Eingeben des Inhalts](#authoring-your-content) für Ihr Fragment,
* [Erstellen und Verwalten von Varianten](#managing-variations) des **primären** Inhalts,

Führen Sie eine Vielzahl weiterer Aktionen abhängig vom bearbeiteten Datentyp aus, z. B.:

* [Einfügen von visuellen Assets in Ihr Fragment](#inserting-assets-into-your-fragment) (Bilder)

* Wählen zwischen [Rich-Text](#rich-text), [Nur Text](#plain-text) und [Markdown](#markdown) für die Bearbeitung

* [Inhalt hochladen](#uploading-content)

* [Anzeigen von Schlüsselstatistiken](#viewing-key-statistics) (über mehrzeiligen Text)

* [Zusammenfassen von Text](#summarizing-text)

* [Synchronisieren von Varianten mit dem primären Inhalt](#synchronizing-with-master)

>[!CAUTION]
>
>Nachdem ein Fragment veröffentlicht und/oder referenziert wurde, zeigt AEM eine Warnmeldung an, wenn eine Autorin bzw. ein Autor das Fragment erneut zur Bearbeitung öffnet. Dies dient als Hinweis darauf, dass am Fragment vorgenommene Änderungen sich auch auf die referenzierten Seiten auswirken.

## Verfassen Ihres Inhalts {#authoring-your-content}

Wenn Sie das Inhaltsfragment zur Bearbeitung öffnen, wird die Registerkarte **Varianten** standardmäßig geöffnet. Hier können Sie den Inhalt bearbeiten, und zwar den der primären Version sowie sämtlicher Varianten. Das strukturierte Fragment enthält verschiedene Felder mit verschiedenen Datentypen, die im Inhaltsmodell definiert wurden.

Zum Beispiel:

![Vollbild-Editor](assets/cfm-variations-02.png)



Sie haben folgende Möglichkeiten:

* Bearbeiten Sie Ihre Inhalte direkt auf der Registerkarte **Varianten**. Jeder Datentyp bietet verschiedene Bearbeitungsoptionen, z. B.:

   * Für **mehrzeilige Textfelder** können Sie auch den [Vollbild-Editor](#full-screen-editor) öffnen, um:

      * das [Format](#formats) auszuwählen
      * weitere Bearbeitungsoptionen anzuzeigen ([Rich-Text](#rich-text)-Format)
      * auf eine Reihe von [Aktionen](#actions) zuzugreifen

   * Für die Felder **Fragmentreferenz** kann je nach Modelldefinition die Option [Inhaltsfragment bearbeiten](#fragment-references-edit-content-fragment) verfügbar sein.

* Weisen Sie der aktuellen Variante **Tags** zu. Die Tags können hinzugefügt, aktualisiert und entfernt werden

   * [Tags](/help/sites-authoring/tags.md) sind leistungsstark bei der Organisation Ihrer Fragmente, da sie für die Inhaltsklassifizierung und -taxonomie verwendet werden können. Tags können zum Suchen von Inhalten (nach Tags) und zum Anwenden von Massenvorgängen verwendet werden.

      * Bei der Suche nach einem Tag wird das Fragment zurückgegeben, wobei die getaggte Variante hervorgehoben ist.
      * Varianten-Tags können auch verwendet werden, um Varianten für ein bestimmtes CDN-Profil (Content Delivery Network) (für CDN-Caching) zu gruppieren, anstatt den Variantennamen zu verwenden.

     Beispielsweise können Sie relevante Fragmente als „Weihnachts-Launch“ taggen, um nur diese als Teilmenge zu durchsuchen oder sie für einen anderen zukünftigen Launch in einen neuen Ordner zu kopieren.

  >[!NOTE]
  >
  >**Tags** können auch (in der **primären** Variante) als Teil der [Metadaten](/help/assets/content-fragments/content-fragments-metadata.md) hinzugefügt werden

* [Erstellen und Verwalten von Varianten](#managing-variations) des **primären** Inhalts.

### Vollbild-Editor {#full-screen-editor}

Beim Bearbeiten eines mehrzeiligen Textfelds können Sie den Vollbild-Editor öffnen. Klicken Sie auf den eigentlichen Text und wählen Sie dann das folgende Aktionssymbol aus:

![Symbol für den Vollbild-Editor](assets/cfm-variations-03.png)

Dadurch wird der Vollbild-Texteditor geöffnet:

![Vollbild-Editor](assets/cfm-variations-fullscreentexteditor.png)

Der Vollbild-Texteditor bietet Folgendes:

* Zugriff auf verschiedene [Aktionen](#actions)
* Je nach [Format](#formats) zusätzliche Formatierungsoptionen ([Rich-Text](#rich-text))

### Aktionen {#actions}

Die folgenden Aktionen sind ebenfalls verfügbar (für sämtliche [Formate](#formats)), wenn der Vollbild-Editor (d. h. mehrzeiliger Text) geöffnet ist:

* [Format](#formats) auswählen ([Rich-Text](#rich-text), [Nur Text](#plain-text), [Markdown](#markdown))

* [Inhalt hochladen](#uploading-content)

* [Textstatistiken anzeigen](#viewing-key-statistics)

* [Mit primärer Version synchronisieren](#synchronizing-with-master) (beim Bearbeiten einer Variante)

* [Zusammenfassen von Text](#summarizing-text)

### Formate {#formats}

Die Optionen für das Bearbeiten von mehrzeiligem Text hängen vom ausgewählten Format ab:

* [Rich-Text](#rich-text)
* [Nur Text](#plain-text)
* [Markdown](#markdown)

Das Format kann im Vollbild-Editor ausgewählt werden.

### Rich-Text {#rich-text}

Die Rich-Text-Bearbeitung ermöglicht folgende Formatierungen:

* Fett
* Kursiv
* Unterstrichen
* Ausrichtung: links, zentriert, rechts
* Aufzählungsliste
* Nummerierte Liste
* Einzug: erhöhen, verringern
* Hyperlinks erstellen/unterbrechen
* Text aus Word einfügen
* Tabelle einfügen
* Absatzformat: Absatz, Überschrift 1/2/3
* [Asset einfügen](#inserting-assets-into-your-fragment)
* Öffnen Sie den Vollbild-Editor, in dem die folgenden Formatierungsoptionen zur Verfügung stehen:
   * Suchen
   * Suchen/Ersetzen
   * Rechtschreibprüfung
   * [Anmerkungen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhaltsfragment einfügen](#inserting-content-fragment-into-your-fragment); verfügbar, wenn Ihr **mehrzeiliges Textfeld** mit **Fragmentreferenz zulassen** konfiguriert wurde.

Die [Aktionen](#actions) sind ebenfalls über den Vollbild-Editor verfügbar.

### Nur Text {#plain-text}

Nur Text ermöglicht die schnelle Eingabe von Inhalt ohne Formatierungs- oder Markdown-Informationen. Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie **Nur Text** auswählen, gehen möglicherweise alle Formatierungen, Markierungen und/oder Assets verloren, die Sie in **Rich-Text** oder **Markdown** eingefügt haben.

### Markdown {#markdown}

>[!NOTE]
>
>Umfassende Informationen finden Sie in der [Markdown](/help/assets/content-fragments/content-fragments-markdown.md)-Dokumentation.

Auf diese Weise können Sie Ihren Text mithilfe von Markdown formatieren. Sie können Folgendes definieren:

* Überschriften
* Absätze und Zeilenumbrüche
* Links
* Bilder
* Blockzitate
* Listen
* Hervorhebungen
* Code-Blöcke
* Umgekehrter Schrägstrich als Escape-Zeichen

Für weitere [Aktionen](#actions) können Sie auch den Vollbild-Editor öffnen.

>[!CAUTION]
>
>Wenn Sie zwischen **Rich-Text** und **Markdown** umschalten, treten möglicherweise unerwartete Effekte mit Blockzitaten und Code-Blöcken auf, da diese beiden Formate unterschiedlich verarbeitet werden.

### Fragmentreferenzen {#fragment-references}

Wenn das Inhaltsfragmentmodell Fragmentreferenzen enthält, stehen Ihren Fragmentautoren möglicherweise zusätzliche Optionen zur Verfügung:

* [Inhaltsfragment bearbeiten](#fragment-references-edit-content-fragment)
* [Neues Inhaltsfragment](#fragment-references-new-content-fragment)

![Fragmentreferenzen](assets/cfm-variations-12.png)

#### Inhaltsfragment bearbeiten {#fragment-references-edit-content-fragment}

Die Option **Inhaltsfragment bearbeiten** öffnet dieses Fragment in einer neuen Fensterregisterkarte.

<!--
The option **Edit Content Fragment** opens that fragment in a new editor tab (within the same browser tab).

Selecting the original tab again (for example, **Little Pony Inc.**), will close this secondary tab (in this case, **Adam Smith**).

![Fragment References](assets/cfm-variations-editreference.png)
-->

#### Neues Inhaltsfragment {#fragment-references-new-content-fragment}

Mit der Option **Neues Inhaltsfragment** können Sie ein Fragment erstellen. Dazu öffnet sich im Editor eine Variante des Assistenten zum Erstellen von Inhaltsfragmenten.

Anschließend können Sie folgendermaßen ein Fragment erstellen:

1. Navigieren Sie zum gewünschten Ordner und wählen Sie ihn aus.
1. Wählen Sie **Weiter** aus.
1. Legen Sie Eigenschaften fest, z. B. **Titel**.
1. Wählen Sie **Erstellen** aus.
1. Abschließend:
   1. Mit **Fertig** kehren Sie (zum ursprünglichen Fragment) zurück und verweisen auf das neue Fragment.
   1. **Öffnen** referenziert das neue Fragment und öffnet das neue Fragment zur Bearbeitung in einer neuen Browser-Registerkarte.

### Anzeigen von wichtigen Statistiken {#viewing-key-statistics}

Wenn der Vollbild-Editor geöffnet ist, zeigt die Aktion **Textstatistik** eine Reihe von Informationen über den Text an.

Zum Beispiel:

![Statistiken](assets/cfm-variations-04.png)

### Hochladen von Inhalt {#uploading-content}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie Text hochladen, der in einem externen Editor vorbereitet wurde, und ihn direkt in das Fragment einfügen.

### Zusammenfassung von Text {#summarizing-text}

Mithilfe der Zusammenfassung von Text können Benutzende die Länge des Textes auf eine vordefinierte Anzahl von Wörtern verringern, während die wichtigsten Punkte und die allgemeine Bedeutung beibehalten werden.

>[!NOTE]
>
>Auf technischer Ebene behält das System die Sätze bei, die in Übereinstimmung mit bestimmten Algorithmen das *beste Verhältnis von Informationsdichte und Eindeutigkeit* bieten.

>[!CAUTION]
>
>Das Inhaltsfragment muss einen gültigen Sprachordner (ISO-Code) als Vorgänger haben, der verwendet wird, um das zu verwendende Sprachmodell zu bestimmen.
>
>Beispiel: `en/` wie im folgenden Pfad:
>
>  `/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
>
>Englisch ist standardmäßig verfügbar.
>
>Andere Sprachen sind als Sprachmodellpakete von Package Share verfügbar:
>
>* [Französisch (fr)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
>* [Deutsch (de)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
>* [Italienisch (it)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
>* [Spanisch (es)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?lang=de?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
>

1. Wählen Sie **Primäre Version** oder die erforderliche Variante aus.
1. Öffnen Sie den Vollbild-Editor.

1. Wählen Sie in der Symbolleiste die Option **Text zusammenfassen** aus.

   ![Zusammenfassung](assets/cfm-variations-05.png)

1. Geben Sie den Zielwert der Wörter an und wählen Sie **Starten**:
1. Der ursprüngliche Text wird neben der vorgeschlagenen Zusammenfassung angezeigt:

   * Alle zu löschenden Sätze sind rot hervorgehoben und durchgestrichen.
   * Klicken Sie auf einen beliebigen hervorgehobenen Satz, wenn Sie ihn im zusammengefassten Inhalt beibehalten möchten.
   * Klicken Sie auf einen beliebigen nicht hervorgehobenen Satz, wenn Sie ihn beseitigen möchten.

1. Wählen Sie **Zusammenfassen** aus, um die Änderungen zu bestätigen.

1. Der ursprüngliche Text wird neben der vorgeschlagenen Zusammenfassung angezeigt:

   * Alle zu löschenden Sätze sind rot hervorgehoben und durchgestrichen.
   * Klicken Sie auf einen beliebigen hervorgehobenen Satz, wenn Sie ihn im zusammengefassten Inhalt beibehalten möchten.
   * Klicken Sie auf einen beliebigen nicht hervorgehobenen Satz, wenn Sie ihn beseitigen möchten.
   * Die Zusammenfassungsstatistiken werden gezeigt: **Actual** und **Target**.
   * Sie können die Änderungen in der **Vorschau** sehen.

   ![Zusammenfassungsvergleich](assets/cfm-variations-06.png)

### Anmerkungen zu Inhaltsfragmenten {#annotating-a-content-fragment}

So fügen Sie eine Anmerkung zu einem Fragment hinzu:

1. Wählen Sie **Primäre Version** oder die erforderliche Variante aus.

1. Öffnen Sie den Vollbild-Editor.

1. Das Symbol **Anmerken** ist in der Symbolleiste oben verfügbar. Sie können bei Bedarf Text auswählen.

   ![Anmerken](assets/cfm-variations-07.png)

1. Ein Dialogfeld wird angezeigt. Hier können Sie Ihre Anmerkungen eingeben.

   ![Anmerken](assets/cfm-variations-07a.png)

1. Wählen Sie **Anwenden** im Dialogfeld aus.

   ![Anmerken](assets/cfm-variations-annotations-apply-icon.png)

   Wenn die Anmerkung auf den ausgewählten Text angewendet wurde, bleibt dieser Text hervorgehoben.

   ![Anmerken](assets/cfm-variations-07b.png)

1. Schließen Sie den Vollbild-Editor. Die Anmerkungen sind weiterhin hervorgehoben. Wenn diese Option aktiviert ist, wird ein Dialogfeld geöffnet, in dem Sie die Anmerkung weiter bearbeiten können.

1. Klicken Sie auf **Speichern**.

1. Schließen Sie den Vollbild-Editor. Die Anmerkungen sind weiterhin hervorgehoben. Wenn diese Option aktiviert ist, wird ein Dialogfeld geöffnet, in dem Sie die Anmerkung weiter bearbeiten können.

   ![Anmerken](assets/cfm-variations-07c.png)

### Anzeigen, Bearbeiten und Löschen von Anmerkungen {#viewing-editing-deleting-annotations}

Anmerkungen:

* Sie werden durch die Markierung auf dem Text sowohl im Vollbildmodus als auch im normalen Modus des Editors angezeigt. Vollständige Details einer Anmerkung können angezeigt, bearbeitet und/oder gelöscht werden, indem Sie auf den markierten Text klicken, wodurch das Dialogfeld erneut geöffnet wird.

  >[!NOTE]
  >
  >Eine Dropdown-Liste wird angezeigt, wenn mehrere Anmerkungen auf einen Textausschnitt angewendet wurden.

* Wenn Sie den gesamten Text löschen, auf den die Anmerkung angewendet wurde, wird der Kommentar ebenfalls gelöscht.

* Kann durch das Auswählen der Registerkarte **Anmerkungen** im Fragment-Editor aufgeführt und gelöscht werden.

  ![Anmerkungen](assets/cfm-variations-08.png)

* Können in der [Timeline](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) für das ausgewählte Fragment angezeigt und gelöscht werden.

### Einfügen von Assets in das Fragment {#inserting-assets-into-your-fragment}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie [Assets](/help/assets/manage-assets.md) (Bilder) direkt zum Fragment hinzufügen.

Sie werden der Absatzsequenz des Fragments ohne Formatierung hinzugefügt. Formatierungen können vorgenommen werden, wenn das [Fragment auf einer Seite verwendet/referenziert wird](/help/sites-authoring/content-fragments.md).

>[!CAUTION]
>
>Diese Assets können auf einer referenzierenden Seite nicht verschoben oder gelöscht werden, sondern nur im Fragment-Editor.
>
>Das Formatieren von Assets (z. B. Größe) muss im [Seiten-Editor](/help/sites-authoring/content-fragments.md) erfolgen. Die Darstellung des Assets im Fragment-Editor dient lediglich der Erstellung des Inhaltsflusses.

>[!NOTE]
>
>Es gibt verschiedene Methoden, um [Bilder](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder einer Seite hinzuzufügen.

1. Positionieren Sie den Cursor an der Position, an der Sie das Bild hinzufügen möchten.
1. Öffnen Sie das Suchdialogfeld mithilfe der Schaltfläche **Asset einfügen**.

   ![Symbol „Asset einfügen“](assets/cfm-variations-09.png)

1. In diesem Dialogfeld haben Sie folgende Möglichkeiten:

   * Navigieren zum erforderlichen Asset im DAM
   * Suchen nach dem Asset im DAM

   Nachdem Sie das gewünschte Asset gefunden haben, wählen Sie es aus, indem Sie auf die Miniatur klicken.

1. Verwenden Sie **Auswählen**, um das Asset dem Absatzsystem Ihres Inhaltsfragments am aktuellen Speicherort hinzuzufügen.

   >[!CAUTION]
   >
   >Folgendes geschieht, wenn Sie das Format nach dem Hinzufügen eines Assets wie folgt ändern:
   >
   >* **Nur Text**: Das Asset geht im Fragment verloren.
   >* **Markdown**: Das Asset wird nicht angezeigt, ist aber immer noch vorhanden, wenn Sie zu **Rich-Text** zurückkehren.

### Einfügen eines Inhaltsfragments in ein Fragment {#inserting-content-fragment-into-your-fragment}

Um die Erstellung von Inhaltsfragmenten zu vereinfachen, können Sie Ihrem Fragment auch ein anderes Inhaltsfragment hinzufügen.

Es wird an der aktuellen Position in Ihrem Fragment als Verweis hinzugefügt.

>[!NOTE]
>
>Diese Option ist verfügbar, wenn Ihr **mehrzeiliges Textfeld** mit **Fragmentreferenz zulassen** konfiguriert wurde.

>[!CAUTION]
>
>Diese Assets können auf einer referenzierenden Seite nicht verschoben oder gelöscht werden, sondern nur im Fragment-Editor.
>
>Das Formatieren von Assets (z. B. Größe) muss im [Seiten-Editor](/help/sites-authoring/content-fragments.md) erfolgen. Die Darstellung des Assets im Fragment-Editor dient lediglich der Erstellung des Inhaltsflusses.

>[!NOTE]
>
>Es gibt verschiedene Methoden, um [Bilder](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder einer Seite hinzuzufügen.

1. Positionieren Sie den Cursor an der Stelle, an der Sie das Fragment hinzufügen möchten.
1. Öffnen Sie das Suchdialogfeld mithilfe der Schaltfläche **Inhaltsfragment einfügen**.

   ![Symbol „Inhaltsfragment einfügen“](assets/cfm-variations-13.png)

1. In diesem Dialogfeld haben Sie folgende Möglichkeiten:

   * Navigieren zum gewünschten Fragment im Assets-Ordner,
   * Suchen nach dem Fragment,

   Nachdem Sie das gewünschte Fragment gefunden haben, klicken Sie auf die Miniaturansicht, um das Fragment auszuwählen.

1. Verwenden Sie **Auswählen**, um dem aktuellen Inhaltsfragment (an der aktuellen Position) eine Referenz zum ausgewählten Inhaltsfragment hinzuzufügen.

   >[!CAUTION]
   >
   >Folgendes geschieht, wenn Sie das Format nach dem Hinzufügen eines Verweises zu einem anderen Fragment wie folgt ändern:
   >
   >* **Nur Text**: Der Verweis geht im Fragment verloren.
   >* **Markdown**: Der Verweis bleibt erhalten.

## Verwalten von Varianten {#managing-variations}

### Erstellen einer Variante {#creating-a-variation}

Varianten ermöglichen die Abänderung von **primärem** Inhalt für einen bestimmten Zweck (sofern notwendig).

So erstellen Sie eine Variante:

1. Öffnen Sie Ihr Fragment und stellen Sie sicher, dass das seitliche Bedienfeld sichtbar ist.
1. Wählen Sie im seitlichen Bedienfeld in der Symbolleiste die Option **Varianten** aus.
1. Wählen Sie **Variante erstellen** aus.
1. Geben Sie im daraufhin geöffneten Dialogfeld einen **Titel** und eine **Beschreibung** für die neue Variante an.
1. Wählen Sie **Hinzufügen** aus. Das Fragment **Primäre Version** wird in die neue Variante kopiert, die nun zur [Bearbeitung](#editing-a-variation) geöffnet ist.

   >[!NOTE]
   >
   >Wenn eine Variante erstellt wird, wird immer die **primäre Version** kopiert, nicht die geöffnete Variante.

   >[!NOTE]
   >
   >Wenn Sie eine Variante erstellen, werden alle **Tags**, die derzeit der **primären** Variante zugewiesen sind, in Ihre neue Variante kopiert.

### Bearbeiten einer Variante {#editing-a-variation}

Nehmen Sie nach einer der folgenden Aktionen Änderungen am Inhalt der Variante vor:

* [Erstellen einer Variante](#creating-a-variation)
* Öffnen eines vorhandenen Fragments und Auswahl der gewünschten Variante über das seitliche Bedienfeld

![Bearbeiten einer Variante](assets/cfm-variations-10.png)

### Umbenennen einer Variante {#renaming-a-variation}

So benennen Sie eine vorhandene Variante um:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **Varianten** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **Aktionen** die Option **Umbenennen** aus.

1. Geben Sie im Dialogfeld den neuen **Titel** und/oder die **Beschreibung** ein.

1. Bestätigen Sie die Aktion **Umbenennen**.

>[!NOTE]
>
>Dies betrifft nur den **Titel** der Variante.

### Löschen einer Variante {#deleting-a-variation}

So löschen Sie eine vorhandene Variante:

1. Öffnen Sie das Fragment und wählen Sie über den Seitenbereich die Option **Varianten** aus.
1. Wählen Sie die gewünschte Variante aus.
1. Wählen Sie im Dropdown-Menü **Aktionen** die Option **Löschen** aus.

1. Bestätigen Sie im Dialogfeld die Aktion **Löschen**.

>[!NOTE]
>
>**Primäre Version** kann nicht gelöscht werden.

### Mit primärer Version synchronisieren {#synchronizing-with-master}

Die **primäre Version** ist ein Teil eines Inhaltsfragments und enthält per Definition die primäre Kopie des Inhalts, während die Varianten einzelne aktualisierte und angepasste Versionen des Inhalts enthalten. Wenn die primäre Version aktualisiert wird, können diese Änderungen auch für die Varianten relevant sein und müssen daher auf diese übertragen werden.

Beim Bearbeiten einer Variante haben Sie Zugriff auf die Aktion zur Synchronisierung des aktuellen Elements der Variante mit der primären Version. Dadurch können Sie die an der primären Version vorgenommenen Änderungen automatisch in die entsprechende Variante kopieren.

>[!CAUTION]
>
>Die Synchronisierung ist nur verfügbar, um Änderungen *von der **primären Version**in die Variante* zu kopieren.
>
>Nur das aktuelle Element der Variante wird synchronisiert.
>
>Die Synchronisierung funktioniert nur mit dem Datentyp **Mehrzeiliger Text**.
>
>Es ist nicht möglich, Änderungen *von einer Variante auf die **primäre Version*** zu übertragen.

<!-- needs new screenshot for synchronize effect -->

1. Öffnen Sie das Inhaltsfragment im Fragment-Editor. Stellen Sie sicher, dass die **primäre Version** bearbeitet wurde.

1. Es gibt folgende Möglichkeiten, eine bestimmte Variante sowie die entsprechende Synchronisierung auszuwählen:

   * über den Dropdown-Selektor **Aktionen** – **Aktuelles Element mit primärer Version synchronisieren**

     ![Mit primärer Version synchronisieren](assets/cfm-variations-11a.png)

   * über die Symbolleiste des Vollbild-Editors – **Mit primärer Version synchronisieren**

     ![Mit primärer Version synchronisieren](assets/cfm-variations-11b.png)

1. Primäre Version und Variante werden nebeneinander angezeigt:

   * Grün zeigt an, dass der Inhalt (zur Variante) hinzugefügt wurde
   * Rot zeigt an, dass Inhalt entfernt wurde (aus der Variante)
   * Blau zeigt an, dass Text ersetzt wurde

   ![Mit primärer Version synchronisieren](assets/cfm-variations-11c.png)

1. Wählen Sie **Synchronisieren**. Die Variante wird dann aktualisiert und angezeigt.
