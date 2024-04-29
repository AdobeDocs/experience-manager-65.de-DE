---
title: Einführung in die Benutzeroberfläche für Erstellung von interaktiven Kommunikationen
description: Eine Einführung in die verschiedenen Elemente der Benutzeroberfläche, mit denen Sie interaktive Kommunikation erstellen können
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications
docset: aem65
feature: Interactive Communication
exl-id: 3d15a723-df6c-4b4a-992e-a6636f4cf3dc
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1318'
ht-degree: 100%

---

# Einführung in die Benutzeroberfläche für interaktive Kommunikationserstellung{#introduction-to-interactive-communication-authoring-ui}

Die Benutzeroberfläche für das Erstellen von [interaktiver Kommunikation](/help/forms/using/interactive-communications-overview.md) ist intuitiv und bietet Folgendes für die Erstellung des Druck- und Web-Kanals der interaktiven Kommunikation:

* WYSIWYG Drag-and-Drop-Dokumenteditor
* Integriertes Repository für Assets – die Assets, die auf den Server hochgeladen und dort erstellt wurden, sind im Asset-Browser der Authoring-Oberfläche der interaktiven Kommunikation verfügbar.

Wenn Sie eine [interaktive Kommunikation erstellen oder eine vorhandene bearbeiten](../../forms/using/create-interactive-communication.md), verwenden Sie die folgenden Elemente der Benutzeroberfläche:

* [Seitenleiste](#sidebar)
* [Seitensymbolleiste](#page-toolbar)
* [Komponenten-Symbolleiste](#component-toolbar)
* Inhaltsbereich

![Benutzeroberfläche der interaktiven Kommunikation](assets/form-editor.png)

**A.** Seitenleiste **B.** Seitensymbolleiste **C.** Inhaltsbereich

## Seitenleiste {#sidebar}

![Seitenleiste](assets/sidebar-comps-2.png)

**A.** Kanal-Browser **B.** Inhalts-Browser **C.** Eigenschaften-Browser **D.** Asset-Browser **E.** Komponenten-Browser **F.** Datenquellen-Browser – Datenmodell **G.** Datenquellen-Browser – Übergeordnete Inhalte

<!-- Click to enlarge

![sidebar-comps-3](assets/sidebar-comps-3.png)-->

Die Seitenleiste beinhaltet Folgendes:

* **Kanalbrowser**

Mit dem Kanal-Browser können Sie zwischen Druck- und Internet-Kanal der interaktiven Kommunikation wechseln. Je nach dem Kanal, den Sie im Kanal-Browser ausgewählt haben, zeigen die Browser, z. B. Inhalts- und Komponenten-Browser, die Optionen an.

* **Inhalts-Browser**: Im Inhalts-Browser können Sie die Objekthierarchie des Dokuments für den ausgewählten Kanal sehen. Autorinnen und Autoren können zu bestimmten Formularkomponenten navigieren, indem sie auf das entsprechende Element in der Dokumentobjektstruktur tippen. Autorinnen und Autoren können Objekte im Web-Kanal suchen und in dieser Struktur neu anordnen.

* **Eigenschaften-Browser**

  Hier können Sie die Eigenschaften einer Komponente bearbeiten. Die Eigenschaften sind je nach Komponente verschieden. So zeigen Sie beispielsweise die Eigenschaften des Dokument-Containers an: 
Wählen Sie eine Komponente, dann ![field-level](assets/field-level.png) > **Dokument-Container** und schließlich ![cmppr](assets/cmppr.png) aus.

* **Assets-Browser** Trennt verschiedene Arten von Inhalten wie Layout-Fragmente, Bilder, Dokumente, Seiten, Videos. Der Autor kann Assets in die interaktive Kommunikation ziehen und ablegen.

* **Komponentenbrowser** Enthält Komponenten, mit denen Sie die Druck- und Webkanäle eines Dokuments erstellen können. Sie können Komponenten per Drag-und-Drop in die interaktive Kommunikation ziehen, um Elemente hinzuzufügen, und hinzugefügte Elemente gemäß den Anforderungen konfigurieren. In der folgenden Tabelle werden die im Komponentenbrowser aufgelisteten Komponenten für Druck- und Webkanäle beschrieben. 

| **Komponente** | **Druckkanal** | **Web-Kanal** | **Funktionalität** |
|---|---|---|---|
| Diagramm | ✓ | ✓ | Fügt ein Diagramm hinzu, das Sie in interaktiver Kommunikation zur visuellen Darstellung von zweidimensionalen Daten verwenden können, die aus einem FDM-Sammlungselement abgerufen werden. |
| Dokumentfragment | ✓ | ✓ | Ermöglicht Ihnen das Hinzufügen einer wiederverwendbaren Komponente, eines Textes, einer Liste oder einer Bedingung zu einer interaktiven Kommunikation. Die wiederverwendbare Komponente, die Sie einer interaktiven Kommunikation hinzufügen, kann entweder formulardatenmodellbasiert sein oder ohne ein Formulardatenmodell sein. |
| Bild | ✓ | ✓ | Ermöglicht das Einfügen eines Bildes. |
| Bedienfeld | - | ✓ | Die Bedienfeldkomponente ist ein Platzhalter zum Gruppieren anderer Komponenten und steuert, wie eine Gruppe von Komponenten in einer interaktiven Kommunikation angeordnet wird. Mit einer Bedienfeldkomponente können Sie auch eine Gruppe von Komponenten für die Endbenutzenden wiederholbar machen, z. B. in mehreren Einträgen, die zum Ausfüllen von Bildungsnachweisen erforderlich sind. Es ist sinnvoll, einen Bereich jeweils für eine Registerkarte einer interaktiven Kommunikation mit mehreren Registerkarten zu verwenden. |
| Tabelle | &#42; | ✓ | Fügt eine Tabelle hinzu, mit der Sie Daten in Zeilen und Spalten organisieren können. |
| Zielbereich | &#42;&#42; | ✓ | Fügt einen Zielbereich in einen Web-Kanal ein, um die Web-kanalspezifischen Komponenten zu organisieren. |
| Text | - | ✓ | Fügt Text zum Web-Kanal einer interaktiven Kommunikation hinzu. Text kann Formulardatenmodellobjekte verwenden, um den Inhalt dynamisch zu gestalten. |

&#42; Verwenden Sie Layout-Fragmente im Druckkanal, um Tabellen hinzuzufügen.

&#42;&#42; Im Druckkanal sind Zielbereiche in der XDP-/Druckvorlage vordefiniert. Sie können keine neuen Zielbereiche mithilfe der Autorenoberfläche für die interaktive Kommunikation hinzufügen.

* **Datenquellenbrowser** Datenquellenbrowser zeigt die verfügbaren Datenquellen in dem Formulardatenmodell an, das Sie beim Erstellen der interaktiven Kommunikation ausgewählt haben.

### Wichtige Punkte beim Arbeiten mit Komponenten {#key-points-for-working-with-components}

Die wichtigsten Punkte beim Arbeiten mit interaktiven Kommunikationskomponenten sind:

* Jede Komponente verfügt über zugehörige Eigenschaften, die ihre Darstellung und Funktion steuern. Wählen Sie zum Konfigurieren der Eigenschaften einer Komponente erst die Komponente und dann ![cmppr](assets/cmppr.png), um die Komponenteneigenschaften im Eigenschaften-Browser zu öffnen.
* Eine Komponente wird mit ihrem Elementnamen gekennzeichnet. Wenn Sie ![cmppr](assets/cmppr.png) auswählen, können Sie den Namen der Komponente ändern, indem Sie den Wert des Felds „Elementname“ im Eigenschaften-Browser ändern. Das Feld „Elementname“ akzeptiert nur Buchstaben, Zahlen, Bindestriche (-) und Unterstriche (_). Andere Sonderzeichen sind nicht zulässig, und der Elementname sollte mit einem Buchstaben beginnen.
* Sie können die Titel-Eigenschaft einer Komponente einer interaktiven Kommunikation inline im Editor ändern, ohne den Eigenschaften-Browser zu öffnen, solange der Titel in der interaktiven Kommunikation sichtbar ist. Gehen Sie dazu wie folgt vor:

   1. Wählen Sie eine Komponente aus, in der die Eigenschaft „Titel“ vorhanden und deren Eigenschaft „Titel ausblenden“ deaktiviert ist.
   1. Wählen Sie ![aem_6_3_edit](assets/aem_6_3_edit.png) aus, damit der Titel bearbeitet werden kann.

   1. Ändern Sie den Titel und drücken Sie die Eingabetaste oder wählen Sie eine beliebige Stelle außerhalb der Komponente aus, um die Änderungen zu speichern. Drücken Sie die Esc-Taste, um die Änderungen zu verwerfen.

## Komponenten-Symbolleiste {#component-toolbar}

![Komponenten-Symbolleistenbeschriftungen](do-not-localize/component_toolbar_labels_new.png)

Wenn Sie eine Komponente auswählen, wird eine Symbolleiste angezeigt, über die Sie mit ihr arbeiten können. Sie erhalten Optionen zum Ausschneiden, Einfügen, Verschieben und Angeben von Eigenschaften der Komponenten. Ihre Optionen sind:

A. **Konfigurieren**: Wenn Sie **Konfigurieren** auswählen, werden in der Seitenleiste die Komponenteneigenschaften sichtbar.

B. **Regeln bearbeiten**: Wenn Sie „Regeln bearbeiten“ auswählen, wird der Regeleditor angezeigt, in dem Sie Regeln für die ausgewählte Komponente bearbeiten und erstellen können. Im Regeleditor können Sie auch andere Formularobjekte (Komponenten) auswählen und Regeln für diese Formularobjekte bearbeiten/erstellen.

C. **Kopieren**: Sie können die Kopieroption verwenden, um eine Komponente zu kopieren und an andere Positionen im Formular einzufügen.

D. **Ausschneiden**: Sie können die Option zum Ausschneiden verwenden, um in der interaktiven Kommunikation eine Komponente von einer Position an eine andere zu verschieben.

E. **Löschen**: Hiermit können Sie die Komponente aus der interaktiven Kommunikation löschen.

F. **Komponente einfügen**: Hiermit können Sie eine Komponente oberhalb der ausgewählten Komponente einfügen.

G. **Einfügen**: Hiermit können Sie die mithilfe der oben genannten Optionen ausgeschnittenen oder kopierten Komponente einfügen.

H. **Gruppieren**: Mit dieser Funktion können Sie mehrere Komponenten auswählen, um sie zusammen auszuschneiden, zu kopieren oder einzufügen.

I. **Übergeordnet**: Hier können Sie das übergeordnete Element einer Komponente auswählen.

J. **SOM-Ausdruck anzeigen**: Damit können Sie den [SOM-Ausdruck](../../forms/using/using-som-expressions-adaptive-forms.md) für die Komponente anzeigen.

K: **Gruppieren von Objekten im Bereich**: Hiermit können Sie die Komponenten in einem Bedienfeld gruppieren, um Vorgänge für diese Komponenten gleichzeitig durchführen zu können. Weitere Informationen finden Sie unter [Gruppieren von Objekten im Bedienfeld](create-interactive-communication.md#groupobjectspanel).

L. **Untergeordnetes Bedienfeld hinzufügen** (nur für Bedienfelder): Hiermit können Sie dem Bedienfeld ein untergeordnetes Bedienfeld hinzufügen.

M: **Symbolleiste hinzufügen** (Nur für Bedienfelder): Hiermit können Sie die Symbolleisten-Komponente für Bedienfelder hinzufügen. Sie können dann weitere Aktionen in der Symbolleiste ausführen.

Außerdem können Sie mit der Option **Ersetzen** in der Symbolleiste die vorhandene Komponente durch eine andere Komponente ersetzen. Die Option ist für die Bedienfeldkomponente nicht verfügbar.

## Seitensymbolleiste {#page-toolbar}

Die Seitensymbolleiste oben bietet Optionen, mit denen Sie die interaktive Kommunikation in der Vorschau anzeigen und ihre Eigenschaften ändern können. Sie können beim Bearbeiten die interaktive Kommunikation in der Vorschau anzeigen und die gewünschten Änderungen vornehmen. In der Seitensymbolleiste wird Folgendes angezeigt:

* Seitliches Bedienfeld ein/aus![ toggle-side-panel](assets/toggle-side-panel.png): Hiermit können Sie die Seitenleiste ein- oder ausblenden.
* Seiteninformationen ![pageinformationad](assets/pageinformationad.png): Hiermit können Sie die Seiteneigenschaften anzeigen.
* Emulator ![ruler](assets/ruler.png): Hiermit können Sie die Darstellung des Formulars für verschiedene Display-Größen (z. B. für Tablets und Smartphones) emulieren.
* Bearbeiten: Hiermit können Sie andere Modi auswählen, wie etwa: Bearbeiten, Stil, Entwickler und Design.

   * Bearbeiten: Hiermit können Sie die Eigenschaften der interaktiven Kommunikation und ihre Komponenten bearbeiten. Dies tun Sie, indem Sie beispielsweise eine Komponente hinzufügen, ein Bild ablegen oder obligatorische Felder festlegen.
   * Stil: Hiermit können Sie das Erscheinungsbild von Komponenten der interaktiven Kommunikation stilistisch anpassen. Im Stilmodus können Sie beispielsweise einen Bereich auswählen und dessen Hintergrundfarbe festlegen.
   * Entwickler: Hier haben Entwickler folgende Möglichkeiten:

      * Entdecken Sie, woraus interaktive Kommunikation besteht.
      * Debugging der am Formular durchgeführten Aktionen zur Behebung von Fehlern.

   * Ziel: Hier können Sie benutzerdefinierte Komponenten oder auch vordefinierte, nicht in der Seitenleiste aufgelistete Komponenten aktivieren oder deaktivieren.

* Vorschau: Hier können Sie das Aussehen der interaktiven Kommunikation in der Vorschau anzeigen, wenn sie veröffentlicht wird.
