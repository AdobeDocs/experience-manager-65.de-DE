---
title: Einführung in die Benutzeroberfläche für interaktive Kommunikationserstellung
seo-title: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
description: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
seo-description: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
uuid: e8c5b1e8-b2bb-46b4-b42e-1f343192641a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications
discoiquuid: 5855d21b-340c-4139-aabe-c3a534cedb98
docset: aem65
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 53%

---


# Einführung in die Benutzeroberfläche für interaktive Kommunikationserstellung{#introduction-to-interactive-communication-authoring-ui}

Die Benutzeroberfläche für das Authoring [Interaktive Kommunikation](/help/forms/using/interactive-communications-overview.md) ist intuitiv intuitiv und bietet Folgendes zum Authoring von Druck- und Web-Kanal der Interaktiven Kommunikation:

* WYSIWYG Drag-and-Drop-Dokumenteditor
* Integriertes Repository für Assets - Die auf den Server hochgeladenen und erstellten Assets sind im Asset-Browser der Authoring-Oberfläche für interaktive Kommunikation verfügbar

Wenn Sie eine [neue interaktive Kommunikation](../../forms/using/create-interactive-communication.md) erstellen oder eine vorhandene bearbeiten, verwenden Sie die folgenden Elemente der Benutzeroberfläche:

* [Randleiste](#sidebar)
* [Seitensymbolleiste](#page-toolbar)
* [Komponenten-Symbolleiste](#component-toolbar)
* Inhaltsbereich

![Benutzeroberfläche der interaktiven Kommunikation](assets/form-editor.png)

**A.** Seitenleiste  **B.** Seitensymbolleiste  **C.** Inhaltsbereich

## Randleiste {#sidebar}

![Randleiste](assets/sidebar-comps-2.png)

**A.** Kanal-Browser  **B.** Inhaltsbrowser  **C.** Eigenschaftenbrowser  **D.** Asset-Browser  **E.** Komponentenbrowser  ****   **** F.Datenquellen-Browser - DatenmodellG.APIData Sources-Browser - Übergeordnet Content

<!-- Click to enlarge

![sidebar-comps-3](assets/sidebar-comps-3.png)-->

Die Seitenleiste beinhaltet Folgendes:

* **Kanalbrowser**

Mit dem Kanalbrowser können Sie zwischen den Druck- und Internetkanälen der interaktiven Kommunikation wechseln. Je nach dem Kanal, den Sie im Kanalbrowser ausgewählt haben, zeigen die Browser, z. B. Inhalts- und Komponentenbrowser, die Optionen an.

* **Content**
browserIm Inhaltsbrowser können Sie die Objekthierarchie des Dokuments für den ausgewählten Kanal sehen. Der Autor kann zu bestimmten Formularkomponenten navigieren, indem er auf das entsprechende Element in der Dokumentobjektstruktur tippt. Der Autor kann Objekte im Webkanal suchen und in dieser Struktur neu anordnen. 

* **Eigenschaftenbrowser**

   Hiermit können Sie die Eigenschaften einer Komponente bearbeiten. Die Eigenschaften sind je nach Komponente verschieden. So zeigen Sie beispielsweise die Eigenschaften des Dokument-Containers an:
Wählen Sie eine Komponente aus, tippen Sie dann auf ![field-level](assets/field-level.png) > **Dokument Container** und dann auf ![cmppr](assets/cmppr.png).

* **Assets**
browserUnterteilt verschiedene Inhaltstypen wie Layout-Fragmente, Bilder, Dokumente, Seiten, Videos. Der Autor kann Assets in die interaktive Kommunikation ziehen und ablegen.

* **Komponentenbrowser** Enthält Komponenten, mit denen Sie die Druck- und Webkanäle eines Dokuments erstellen können. Sie können Komponenten in die interaktive Kommunikation ziehen, um Elemente hinzuzufügen und hinzugefügte Elemente gemäß den Anforderungen zu konfigurieren. In der folgenden Tabelle werden die im Komponentenbrowser aufgelisteten Komponenten für Druck- und Webkanäle beschrieben. 

| **Komponente** | **Druckkanal** | **Webkanal** | **Funktion** |
|---|---|---|---|
| Diagramm | ✓ | they | Fügt ein Diagramm hinzu, das Sie in interaktiver Kommunikation zur visuellen Darstellung von zweidimensionalen Daten verwenden können, die aus einem FDM-Sammlungselement abgerufen werden. |
| Dokumentfragment | they | they | Ermöglicht das Hinzufügen einer wiederverwendbaren Komponente, eines Textes, einer Liste oder einer Bedingung zu einer interaktiven Kommunikation. Die wiederverwendbare Komponente, die Sie einer interaktiven Kommunikation hinzufügen, kann entweder auf Formulardatenmodellen oder ohne Formulardatenmodell basieren. |
| Bild | they | they | Ermöglicht es Ihnen, ein Bild einzufügen. |
| Fenster | - | they | Die Bereichskomponente ist ein Platzhalter zum Gruppieren anderer Komponenten und steuert, wie eine Gruppe von Komponenten in einer interaktiven Kommunikation angeordnet wird. Mit einer Bereichskomponente können Sie auch eine Gruppe von Komponenten für den Endbenutzer wiederholbar machen, z. B. mehrere Einträge zum Ausfüllen von Bildungsnachweisen. Es empfiehlt sich außerdem, ein Bedienfeld für jede Registerkarte einer interaktiven Kommunikation mit mehreren Registerkarten zu verwenden. |
| Tabelle | * | they | Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. |
| Zielbereich | ** | they | Fügt einen Zielbereich in einen Webkanal ein, um die webkanalspezifischen Komponenten zu organisieren. |
| Text | - | they | Fügt dem Webkanal einer interaktiven Kommunikation Text hinzu. Text kann Formulardatenmodellobjekte verwenden, um den Inhalt dynamisch zu gestalten. |

* Verwenden Sie Layout-Fragmente im Druckkanal, um Tabellen hinzuzufügen.

** Im Druckkanal sind Zielbereiche in der XDP/Druckvorlage vordefiniert. Sie können keine neuen Zielbereiche mithilfe der Autorenoberfläche für die interaktive Kommunikation hinzufügen.

* **Datenquellenbrowser** Datenquellenbrowser zeigt die verfügbaren Datenquellen in dem Formulardatenmodell an, das Sie beim Erstellen der interaktiven Kommunikation ausgewählt haben.

### Wichtige Punkte für das Arbeiten mit Komponenten {#key-points-for-working-with-components}

Die wichtigsten Punkte beim Arbeiten mit interaktiven Kommunikationskomponenten sind:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Um die Eigenschaften einer Komponente zu konfigurieren, tippen Sie auf die Komponente und dann auf ![cmppr](assets/cmppr.png), um die Komponenteneigenschaften im Eigenschaftenbrowser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. Wenn Sie auf ![cmppr](assets/cmppr.png) tippen, können Sie den Namen der Komponente ändern, indem Sie den Feldwert &quot;Elementname&quot;im Eigenschaftenbrowser ändern. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_). Andere Sonderzeichen sind nicht zulässig. Der Elementname muss mit einem Buchstaben beginnen.
* Sie können die Eigenschaft &quot;Titel&quot;einer interaktiven Kommunikationskomponente inline im Editor ändern, ohne den Eigenschaftenbrowser zu öffnen, solange der Titel in der interaktiven Kommunikation sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie auf eine Komponente, in der die Eigenschaft Title vorhanden ist und deren Eigenschaft Titel ausblenden deaktiviert ist, aus, indem Sie darauf tippen.
   1. Tippen Sie auf ![aem_6_3_edit](assets/aem_6_3_edit.png), um den Titel bearbeitbar zu machen.

   1. Ändern Sie den Titel und tippen Sie auf die Return-Taste oder tippen Sie auf eine beliebige Stelle außerhalb der Komponente, um die Änderungen zu speichern. Tippen Sie auf die Esc-Taste, um die Änderungen zu verwerfen.

## Komponenten-Symbolleiste {#component-toolbar}

![Komponenten-Symbolleistenbeschriftungen](do-not-localize/component_toolbar_labels_new.png)

Wenn Sie eine Komponente auswählen, sehen Sie eine Symbolleiste, die folgende Funktionen bietet. Sie erhalten Optionen zum Ausschneiden, Einfügen, Verschieben und Festlegen von Eigenschaften der Komponenten. Ihre Optionen sind:

A.**Konfigurieren**: Wenn Sie auf **Konfigurieren** tippen, werden in der Seitenleiste Komponenteneingenschaften sichtbar.

B.**Regeln bearbeiten**: Wenn Sie auf Regeln bearbeiten tippen, wird der Regeleditor angezeigt, in dem Sie die Regeln für die ausgewählte Komponente bearbeiten und erstellen können. Im Regeleditor können Sie auch andere Formularobjekte (Komponenten) auswählen und Regeln für diese Formularobjekte bearbeiten/erstellen.

C. **Kopieren**: Sie können die Kopieroption verwenden, um eine Komponente zu kopieren und an andere Positionen im Formular einzufügen.

D.**Ausschneiden**: Mit der Option &quot;Ausschneiden&quot;können Sie eine Komponente in der interaktiven Kommunikation von einem Ort zum anderen verschieben.

E. **Löschen**: Hiermit können Sie die Komponente aus der interaktiven Kommunikation löschen.

F. **Komponente einfügen**: Ermöglicht das Einfügen einer Komponente über der ausgewählten Komponente.

G. **Einfügen**: Ermöglicht das Einfügen der Komponente, die Sie mithilfe der oben beschriebenen Optionen ausgeschnitten oder kopiert haben.

H. **Gruppieren**: Mit dieser Funktion können Sie mehrere Komponenten auswählen, um sie zusammen auszuschneiden, zu kopieren oder einzufügen.

I. **Übergeordnet**: Hier können Sie das übergeordnete Element einer Komponente auswählen.

J. **Ansicht SOM-Ausdruck: Ermöglicht die Ansicht des [SOM-Ausdrucks](../../forms/using/using-som-expressions-adaptive-forms.md) für die Komponente.**

K: **Objekte im Bedienfeld gruppieren: Hiermit können Sie die Komponenten in einem Bedienfeld gruppieren, um Vorgänge für diese Komponenten gleichzeitig ausführen zu können.** Weitere Informationen finden Sie unter [Objekte in Bedienfeld](create-interactive-communication.md#groupobjectspanel) gruppieren.

L. **Hinzufügen untergeordnetes Bedienfeld** (nur für Bedienfelder): Hiermit können Sie dem Bedienfeld ein untergeordnetes Bedienfeld hinzufügen.

M: **Hinzufügen Bereichssymbolleiste** (nur für Bereiche): Hiermit können Sie die Symbolleiste für die Bereichskomponente hinzufügen. Anschließend können Sie weitere Aktionen in der Symbolleiste durchführen.

Darüber hinaus können Sie mit der Option **Ersetzen** in der Symbolleiste die vorhandene Komponente durch eine alternative Komponente ersetzen. Die Option steht für die Bereichskomponente nicht zur Verfügung.

## Seitensymbolleiste {#page-toolbar}

Die Seitensymbolleiste oben bietet Optionen, mit denen Sie die interaktive Kommunikation Vorschau und ihre Eigenschaften ändern können. Sie können die interaktive Kommunikation beim Erstellen einer Vorschau erstellen und entsprechende Änderungen vornehmen. In der Seitensymbolleiste wird Folgendes angezeigt:

* Seitliches Bedienfeld ![umschaltbares Bedienfeld](assets/toggle-side-panel.png) ein/aus: Hiermit können Sie die Seitenleiste ein- oder ausblenden.
* Seiteninformationen ![pageinformationad](assets/pageinformationad.png): Ermöglicht die Ansicht von Seiteneigenschaften.
* Emulator ![Lineal](assets/ruler.png): Hiermit können Sie das Aussehen Ihrer interaktiven Kommunikation für verschiedene Displaygrößen wie Tablets und Smartphones emulieren.
* Bearbeiten: Hiermit können Sie andere Modi auswählen, wie etwa: Bearbeiten, Stil, Entwickler und Design.

   * Bearbeiten: Ermöglicht die Bearbeitung der Eigenschaften der interaktiven Kommunikation und ihrer Komponenten. Dies tun Sie, indem Sie beispielsweise eine Komponente hinzufügen, ein Bild ablegen oder obligatorische Felder festlegen.
   * Stil: Hiermit können Sie das Erscheinungsbild von Komponenten der interaktiven Kommunikation stilistisch anpassen. Im Stilmodus können Sie beispielsweise einen Bereich auswählen und dessen Hintergrundfarbe festlegen.
   * Entwickler: Ermöglicht Entwicklern Folgendes:

      * Entdecken Sie, woraus interaktive Kommunikation besteht.
      * Debugging der am Formular durchgeführten Aktionen zur Behebung von Fehlern.
   * Zielgruppe: Ermöglicht die Aktivierung oder Deaktivierung benutzerdefinierter Komponenten oder von vordefinierten Komponenten, die nicht in der Seitenleiste aufgeführt sind.


* Vorschau: Ermöglicht die Vorschau, wie die interaktive Kommunikation aussieht, wenn Sie sie veröffentlichen.

