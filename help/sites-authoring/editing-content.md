---
title: Bearbeiten des Inhalts von Seiten
description: Nachdem die Seite erstellt wurde, können Sie den Inhalt bearbeiten, um die erforderlichen Aktualisierungen vorzunehmen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: d5cf4478-51e4-4ca8-b3f8-6d7caed7d515
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '3015'
ht-degree: 98%

---

# Bearbeiten des Seiteninhalts{#editing-page-content}

Sobald Ihre Seite erstellt ist (neu oder im Rahmen eines Launches oder einer Live Copy), können Sie den Inhalt bearbeiten und die erforderlichen Aktualisierungen vornehmen.

Inhalte werden mithilfe von [Komponenten](/help/sites-authoring/default-components-console.md) hinzugefügt (entsprechend dem Inhaltstyp), die per Drag-and-Drop auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

>[!NOTE]
>
>Ihr Konto benötigt die [entsprechenden Zugriffsrechte](/help/sites-administering/security.md) und [Berechtigungen](/help/sites-administering/security.md#permissions), um Seiten zu bearbeiten.
>
>Wenn Sie auf Probleme stoßen, empfiehlt Adobe Ihnen, sich an Ihre Systemadmins zu wenden.

>[!NOTE]
>
>Wenn Ihre Seite und/oder Vorlage entsprechend eingerichtet sind, können Sie das [responsive Layout](/help/sites-authoring/responsive-layout.md) für die Bearbeitung verwenden.

>[!NOTE]
>
>Im **Bearbeitungsmodus** werden Links in Ihrem Inhalt angezeigt, können jedoch **nicht aufgerufen werden**. Verwenden Sie den [Vorschaumodus](#previewingpagestouchoptimizedui), wenn Sie mithilfe von Links in Ihrem Inhalt navigieren möchten.

## Seitensymbolleiste {#page-toolbar}

Die Seite-Symbolleiste bietet Zugriff auf die entsprechenden Funktionen, die von der Seitenkonfiguration abhängig sind.

![Seitensymbolleiste](assets/screen_shot_2018-03-22at111338.png)

Die Symbolleiste bietet Zugriff auf eine Vielzahl von Optionen. Je nach aktuellem Kontext und Ihrer Konfiguration sind einige Optionen möglicherweise nicht verfügbar.

* **Seitliches Bedienfeld ein/aus**

  Dadurch wird das seitliche Bedienfeld geöffnet/geschlossen, das den [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser), den [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) und die [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree) enthält.

  ![Seitliches Panel ein/aus](do-not-localize/screen_shot_2018-03-22at111425.png)

* **Seiteninformationen**

  Ermöglicht den Zugriff auf das Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) mit Seitendetails und Aktionen, die auf der Seite durchgeführt werden können, einschließlich Anzeigen und Bearbeiten von Seiteninformationen, Anzeigen von Seiteneigenschaften und Veröffentlichen/Entfernen der Seite.

  ![Seiteninformationen](do-not-localize/screen_shot_2018-03-22at111437.png)

* **Emulator**

  Blendet die [Emulator-Symbolleiste](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate) ein bzw. aus, über die das Look-and-Feel der Seite auf einem anderen Gerät emuliert werden kann. Dies wird im Layout-Modus automatisch umgeschaltet.

  ![Emulator](do-not-localize/screen_shot_2018-03-22at111442.png)

* **ContextHub**

  Öffnet den [ContextHub](/help/sites-authoring/ch-previewing.md). Dieser ist nur im Vorschaumodus verfügbar.

  ![Context-Hub](assets/screen_shot_2018-03-22at111543.png)

* **Seitentitel**

  Dient nur zu Informationszwecken.

  ![Seitentitel](assets/screen_shot_2018-03-22at111554.png)

* **Modusauswahl**

  Zeigt den aktuellen [Modus](/help/sites-authoring/author-environment-tools.md#page-modes) an und ermöglicht die Auswahl eines anderen Modus, z. B. Bearbeiten, Layout, Timewarp oder Targeting.

  ![Modusauswahl](assets/chlimage_1-120.png)

* **Vorschau**

  Aktiviert den [Vorschaumodus](/help/sites-authoring/editing-content.md#preview-mode). Mit diesem wird die Seite so angezeigt, wie sie bei der Veröffentlichung dargestellt wird.

  ![Vorschaumodus](assets/chlimage_1-121.png)

* **Anmerken**

  Hierüber können Sie die Seite mit [Anmerkungen](/help/sites-authoring/annotations.md) versehen (z. B. zu Prüfungszwecken). Nach der ersten Anmerkung wird anstelle des Symbols eine Zahl für die Anzahl der Anmerkungen auf der Seite angezeigt.

  ![Anmerken](do-not-localize/screen_shot_2018-03-22at111638.png)

### Statusbenachrichtigung {#status-notification}

Wird eine Seite bearbeitet, die einem oder mehreren [Workflows](/help/sites-authoring/workflows.md) unterliegt, wird oben im Bildschirm eine Benachrichtigungsleiste mit einem entsprechenden Hinweis angezeigt.

![Benachrichtigung für Workflows](assets/screen_shot_2018-03-22at111739.png)

>[!NOTE]
>
>Die Statusleiste ist nur für Benutzerkonten mit entsprechenden Berechtigungen sichtbar.

In der Benachrichtigung ist der Workflow aufgeführt, dem die Seite zugeordnet ist. Wenn Benutzende am aktuellen Workflow-Schritt beteiligt sind, sind zusätzlich auch Optionen verfügbar, die sich [auf den Workflow-Status auswirken](/help/sites-authoring/workflows-participating.md) und die weiteren Informationen zum Workflow liefern, darunter:

* **Fertig** - Öffnet die **Arbeitselement abschließen** Dialogfeld

* **Delegieren**: Öffnet das Dialogfeld **Arbeitselement fertigstellen**.

* **Details anzeigen**: Öffnet das Fenster **Details** des entsprechenden Workflows.

Das Fertigstellen und Delegieren von Workflow-Schritten über die Benachrichtigungsleiste erfolgt auf die gleiche Art und Weise wie beim [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md) über den Benachrichtigungs-Posteingang.

Wenn die Seite mehreren Workflows unterliegt, werden ganz rechts in der Benachrichtigung die Anzahl der Workflows sowie Pfeilschaltflächen angezeigt, über die Sie durch die einzelnen Workflows scrollen können.

![Benachrichtigung bezüglich der Anzahl an Workflows](assets/chlimage_1-122.png)

## Komponenten-Platzhalter {#component-placeholder}

Der Komponenten-Platzhalter zeigt an, wo eine Komponente platziert wird, wenn Sie sie ablegen – oberhalb der Komponente, über der sich der Mauszeiger gerade befindet:

* Wenn Sie eine Komponente (durch Ziehen aus dem Komponenten-Browser) zur Seite hinzufügen:

  ![Hinzufügen einer neuen Komponente](assets/screen_shot_2018-03-22at111928.png)

* Wenn Sie eine vorhandene Komponente verschieben:

  ![Verschieben einer vorhandenen Komponente](assets/screen_shot_2018-03-22at112445.png)

## Einfügen einer Komponente {#inserting-a-component}

### Einfügen einer Komponente aus dem Komponenten-Browser {#inserting-a-component-from-the-components-browser}

Sie können eine Komponente mit dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) hinzufügen. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Öffnen Sie den [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser).
1. Ziehen Sie die benötigte Komponente an die [passende Position](#component-placeholder).

1. [Bearbeiten](#editmovecopypastedelete) Sie die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Komponenten-Browser den gesamten Bildschirm ein. Sobald Sie eine Komponente per Drag-and-Drop auswählen, wird der Browser geschlossen, sodass Sie die Komponente auf der Seite ablegen können.

### Einfügen einer Komponente aus dem Absatzsystem {#inserting-a-component-from-the-paragraph-system}

Sie können eine Komponente durch das Feld **Komponenten hierher ziehen** des Absatzsystems hinzufügen.

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Komponenten können auf zwei Arten aus dem Absatzsystem ausgewählt und hinzugefügt werden:

   * Wählen Sie die Option **Komponente einfügen** (+) aus der Symbolleiste einer vorhandenen Komponente oder das Feld **Komponenten hierher ziehen**.

   ![Einfügen der Komponentenauswahl](assets/screen_shot_2018-03-22at112536.png)

   * Wenn Sie ein Desktop-Gerät verwenden, können Sie die Aktion per Doppelklick auf das Feld **Komponenten hierher ziehen** durchführen.

   Das Dialogfeld **Neue Komponente einfügen** wird geöffnet, in dem Sie die erforderliche Komponente auswählen können:

   ![Neue Komponente einfügen](assets/screen_shot_2018-03-22at112650.png)

1. Die ausgewählte Komponente wird unten auf der Seite hinzugefügt. [Bearbeiten](#editmovecopypastedelete) Sie bei Bedarf die Komponente.

### Einfügen einer Komponente mit dem Assets-Browser {#inserting-a-component-using-the-assets-browser}

Sie können auch eine Komponente zur Seite hinzufügen, indem Sie ein Asset aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) ziehen. Dadurch wird automatisch eine Komponente des entsprechenden Typs erstellt, die das Asset enthält.

Dies gilt für folgende Asset-Typen (einige sind von der Seite/dem Absatzsystem abhängig):

<table>
 <tbody>
  <tr>
   <th><strong>Asset-Typ</strong></th>
   <th><strong>Resultierender Komponententyp</strong></th>
  </tr>
  <tr>
   <td>Bild</td>
   <td>Bild</td>
  </tr>
  <tr>
   <td>Dokument</td>
   <td>Download</td>
  </tr>
  <tr>
   <td>Produkt</td>
   <td>Produkt</td>
  </tr>
  <tr>
   <td>Video </td>
   <td>Flash</td>
  </tr>
  <tr>
   <td>Inhaltsfragment</td>
   <td>Inhaltsfragment<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Dieses Verhalten kann für Ihre Installation konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren eines Absatzsystems zum Erstellen einer Komponenteninstanz infolge des Ziehens eines Assets](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance).

So erstellen Sie eine Komponente, indem Sie einen der obigen Asset-Typen ziehen:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Öffnen Sie den [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. Ziehen Sie die benötigte Komponente an die passende Position. Der [Komponenten-Platzhalter](#component-placeholder) zeigt an, wo die Komponente platziert wird.

   Eine für den Asset-Typ geeignete Komponente wird am erforderlichen Speicherort erstellt und enthält das ausgewählte Asset.

1. [Bearbeiten](#editmovecopypastedelete) Sie bei Bedarf die Komponente.

>[!NOTE]
>
>Auf Mobilgeräten nimmt der Asset-Browser den gesamten Bildschirm ein. Sobald Sie ein Asset per Drag-and-Drop auswählen, wird der Browser geschlossen, sodass Sie das Asset auf der Seite ablegen können.

Wenn Sie beim Durchsuchen der Assets feststellen, dass Sie an einem Asset eine schnelle Änderung vornehmen müssen, klicken Sie auf das Bearbeitungssymbol neben dem Namen des Assets, um den [Asset-Editor](/help/assets/manage-assets.md) zu starten.

![Bearbeitungssymbol](assets/screen_shot_2018-03-22at112735.png)

## Bearbeiten/Konfigurieren/Kopieren/Ausschneiden/Löschen/Einfügen {#edit-configure-copy-cut-delete-paste}

Wenn Sie eine Komponente auswählen, wird die Symbolleiste geöffnet. Damit können Sie verschiedene Aktionen für die Komponente auswählen.

Die tatsächlich für die Benutzenden verfügbaren Aktionen werden abhängig von der jeweiligen Situation angezeigt, sodass hier u. U. nicht alle möglichen Aktionen beschrieben werden.

![Optionen der Komponenten-Symbolleiste](assets/screen_shot_2018-03-22at112909.png)

* **Bearbeiten**

  [Abhängig vom Komponententyp](/help/sites-authoring/default-components.md) können Sie hiermit den [Inhalt der Komponente bearbeiten](#edit-content). Häufig wird eine Symbolleiste bereitgestellt.

  ![Bearbeiten](do-not-localize/screen_shot_2018-03-22at112936.png)

* **Konfigurieren**

  [Abhängig vom Komponententyp](/help/sites-authoring/default-components.md) können Sie hiermit die Eigenschaften der Komponente bearbeiten und konfigurieren. Häufig wird ein Dialogfeld geöffnet.

  ![Konfigurieren](do-not-localize/screen_shot_2018-03-22at112955.png)

* **Kopieren**

  Kopiert die Komponente in die Zwischenablage. Die ursprüngliche Komponente bleibt nach dem Einfügen erhalten.

  ![Kopieren](do-not-localize/screen_shot_2018-03-22at113000.png)

* **Ausschneiden**

  Kopiert die Komponente in die Zwischenablage. Nach dem Einfügen wird die ursprüngliche Komponente entfernt.

  ![Ausschneiden](assets/screen_shot_2018-03-22at113007.png)

* **Löschen**

  Löscht die Komponente von der Seite. Sie werden dazu aufgefordert, die Aktion zu bestätigen.

  ![Löschen](do-not-localize/screen_shot_2018-03-22at113012.png)

* **Komponente einfügen**

  Dadurch wird das Dialogfeld für das [Hinzufügen einer neuen Komponente](/help/sites-authoring/editing-content.md#inserting-a-component-from-the-paragraph-system) geöffnet.

  ![Komponente einfügen](do-not-localize/screen_shot_2018-03-22at113017.png)

* **Einfügen**

  Fügt die Komponente aus der Zwischenablage in die Seite ein. Ob das Original erhalten bleibt, hängt davon ab, ob Sie „Kopieren“ oder „Ausschneiden“ verwendet haben.

   * Sie können Komponenten auf derselben oder einer anderen Seite einfügen.
   * Das eingefügte Element wird über dem Element eingefügt, das bei der Einfügeaktion aktiv ist.
   * Die Option zum Einfügen wird nur angezeigt, wenn sich ein Inhalt in der Zwischenablage befindet.

  ![Einfügen](assets/screen_shot_2018-03-22at113553.png)

  >[!NOTE]
  >
  >Wenn Sie etwas auf einer anderen Seite einfügen, die bereits vor dem Ausschneiden bzw. Kopieren geöffnet war, müssen Sie die Seite aktualisieren, damit der eingefügte Inhalt angezeigt wird.

* **Gruppe**

  Mit dieser Aktion können Sie mehrere Komponenten gleichzeitig auswählen. Dasselbe kann auf einem Desktop-Gerät durch **Strg+Klicken** bzw. **Befehl+Klicken** erreicht werden.

  ![Gruppe](do-not-localize/screen_shot_2018-03-22at113240.png)

* **Übergeordnetes Element**

  Hierüber können Sie die Komponente auswählen, die der ausgewählten Komponente übergeordnet ist.

  ![Übergeordnetes Element](assets/screen_shot_2018-03-22at113028.png)

* **Layout**

  Hierüber können Sie das [Layout](/help/sites-authoring/editing-content.md#edit-component-layout) der ausgewählten Komponente ändern. Dies gilt nur für die ausgewählte Komponente und aktiviert nicht den [Layout-Modus](/help/sites-authoring/author-environment-tools.md#page-modes) für die gesamte Seite.

  ![Layout](do-not-localize/screen_shot_2018-03-22at113044.png)

* **Umwandeln in eine Experience Fragment-Variante**

  Hierüber können Sie ein [Experience Fragment](/help/sites-authoring/experience-fragments.md) über die ausgewählte Komponente erstellen oder zu einem bestehenden Experience Fragment hinzufügen.

  ![In Experience-Fragment-Variante umwandeln](do-not-localize/screen_shot_2018-03-22at113033.png)

## Bearbeiten (Inhalt) {#edit-content}

Für das Hinzufügen oder Bearbeiten von Inhalten in Komponenten sind zwei Verfahren verfügbar:

* Öffnen Sie das [Komponentendialogfeld für die Bearbeitung](#component-edit-dialog).
* [Ziehen Sie ein Asset](#draganddropintocomponent) aus dem Asset-Browser, um Inhalt direkt hinzuzufügen.

### Dialogfeld „Komponente bearbeiten“ {#component-edit-dialog}

Sie können eine Komponente öffnen, um den Inhalt zu bearbeiten, indem Sie das Symbol [„Bearbeiten“ (Stiftsymbol) in der Komponenten-Symbolleiste](#edit-configure-copy-cut-delete-paste) verwenden.

Die exakten Bearbeitungsoptionen hängen von der jeweiligen Komponente ab. Für einige Komponenten sind [alle Aktionen nur im Vollbildmodus verfügbar](#edit-content-full-screen-mode). Beispiel:

* [Textkomponente](/help/sites-authoring/rich-text-editor.md#main-pars-title-24)

  ![Textkomponente](assets/screen_shot_2018-03-22at120215.png)

* Bildkomponente

  ![Bildkomponente](assets/screen_shot_2018-03-22at120252.png)

  >[!NOTE]
  >
  >Die Bearbeitung funktioniert nicht bei leeren Bildkomponenten.
  >
  >
  >[Ziehen Sie ein Bild per Drag-and-Drop oder laden Sie es hoch (mithilfe von „Konfigurieren“)](/help/sites-authoring/default-components-foundation.md#image), bevor Sie es bearbeiten können.

* Bildkomponente – Vollbild

  [Der Wechsel in den Vollbildmodus](/help/sites-authoring/editing-content.md#edit-content-full-screen-mode) für die Bildkomponente bietet mehr Platz zum Bearbeiten des Bildes und zeigt zusätzliche Bearbeitungsoptionen wie **Map starten** und **Zoom zurücksetzen**. Außerdem können im Vollbildmodus Zuschnittvoreinstellungen ausgewählt werden.

  ![Bildkomponente – Vollbild](assets/screen_shot_2018-03-22at120529.png)

* Bei Komponenten, die aus mehr als einer grundlegenden Komponente bestehen, etwa der [Foundation-Komponente für Text und Bild](/help/sites-authoring/default-components-foundation.md#text-image), werden Sie zunächst dazu aufgefordert, die gewünschten Bearbeitungsoptionen zu bestätigen:

  ![Bearbeitungsoptionen für Komponenten](assets/chlimage_1-123.png)

### Drag-and-Drop von Assets in Komponenten {#drag-and-drop-assets-into-component}

Bei bestimmten Komponententypen (z. B. Bildern) können Sie Assets aus dem Asset-Browser direkt in die Komponente ziehen und dort ablegen, um den Inhalt zu aktualisieren:

| **Asset-Typ** | **Komponententyp** |
|---|---|
| Bild | Bild |
| Dokument | Download |
| Produkt | Produkt |
| Video  | Flash |
| Inhaltsfragment | Inhaltsfragment |

## Bearbeiten (Inhalt) – Vollbildmodus {#edit-content-full-screen-mode}

Für alle Komponenten kann der Vollbildmodus über das folgende Symbol gestartet und beendet werden:

![Vollbildmodus bearbeiten](do-not-localize/chlimage_1-20.png)

Z. B. die **Textkomponente**:

![Texteditor](assets/screen_shot_2018-03-22at121616.png)

>[!NOTE]
>
>Für einige Komponenten sind im Vollbildmodus mehr Optionen verfügbar als im integrierten Editor.

## Verschieben einer Komponente {#moving-a-component}

So verschieben Sie eine Absatzkomponente:

1. Wählen Sie den zu verschiebenden Absatz aus, indem Sie ihn drücken und halten oder klicken und halten.
1. Ziehen Sie den Absatz an die neue Position. AEM zeigt an, wo der Absatz abgelegt werden kann. Legen Sie ihn an der gewünschten Position ab.

   ![Verschieben einer Absatzkomponente](assets/screen_shot_2018-03-22at121821.png)

1. Der Absatz wird verschoben.

>[!NOTE]
>
>Sie können eine Komponente auch durch [Ausschneiden und Einfügen](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) verschieben.

## Bearbeiten des Komponenten-Layouts {#edit-component-layout}

Wenn Sie eine Komponente anpassen möchten, müssen Sie nicht ständig zwischen dem Bearbeitungs- und dem [Layout-Modus](/help/sites-authoring/responsive-layout.md) hin- und herwechseln, sondern mithilfe der **Layout**-Aktion können Sie das Layout einer Komponente ebenfalls ändern. Dadurch sparen Sie Zeit, da Sie den Bearbeitungsmodus nicht verlassen müssen.

1. In der Sites-Konsole wird im **Bearbeitungsmodus** durch Auswählen einer Komponente die zugehörige Symbolleiste für die Komponente angezeigt.

   ![Bearbeitungsmodus im Formular](assets/screen_shot_2018-03-22at133756.png)

   Klicken Sie auf **Layout** -Aktion, damit Sie das Layout der Komponente anpassen können.

   ![Komponenten-Symbolleiste](do-not-localize/chlimage_1-21.png)

1. Sobald die Layout-Aktion ausgewählt ist, sehen Sie Folgendes:

   * Die Größenänderungsgriffe für die Komponente werden angezeigt.
   * Oben im Bildschirm wird die Emulator-Symbolleiste angezeigt.
   * In der Komponenten-Symbolleiste werden Layout-Aktionen anstelle der standardmäßigen Bearbeitungsaktionen angezeigt.

   ![Formularvorschau auf mehreren Geräten](assets/screen_shot_2018-03-22at133843.png)

   Sie können jetzt Änderungen am Layout der Komponente auf die gleiche Art und Weise vornehmen wie im [Layout-Modus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode).

1. Wenn Sie alle notwendigen Layout-Änderungen vorgenommen haben, klicken Sie im Aktionsmenü der Komponente auf die Schaltfläche **Schließen**, um die Layout-Änderung zu beenden. In der Komponenten-Symbolleiste stehen nun wieder die Standard-Bearbeitungsfunktionen zur Verfügung.

   ![Schließen](do-not-localize/screen_shot_2018-03-22at133920.png)

>[!NOTE]
>
>Die Layout-Aktion ist immer auf die jeweils ausgewählte Komponente beschränkt. Wenn Sie z. B. das Layout einer Komponente bearbeiten und dann eine andere Komponente auswählen, wird für die neu ausgewählte Komponente die standardmäßige Bearbeitungssymbolleiste und nicht die Layout-Symbolleiste angezeigt. Die Ziehpunkte zur Größenanpassung und die Emulator-Symbolleiste werden nicht mehr angezeigt.
>
>Um das allgemeine Layout für die Seite zu bearbeiten, d. h. über mehrere Komponenten hinweg, wechseln Sie in den [Layout-Modus](/help/sites-authoring/responsive-layout.md).

## Vererbte Komponenten {#inherited-components}

Vererbte Komponenten können sich aus diversen Szenarien ergeben, wie:

* [Verwaltung mehrerer Sites](/help/sites-administering/msm.md)
* [Launch](/help/sites-authoring/launches.md) (wenn auf einer Live Copy basierend).
* Spezifische Komponenten, z. B. das vererbte Absatzsystem in Geometrixx.

Sie können die Vererbung deaktivieren (und dann wieder aktivieren). Abhängig von der Komponente kann dies über Folgendes verfügbar sein:

* **Live Copy**

  Auf der Komponentensymbolleiste, wenn sich die Komponente auf einer Seite befindet, die Teil eines Live Copy- oder Launch-Vorgangs (auf Live Copy basierend) ist. Beispiel:

  ![Live Copy](assets/screen_shot_2018-03-22at134339.png)

  Die Option „Vererbung abbrechen“ ist verfügbar:

  ![Vererbung abbrechen](do-not-localize/screen_shot_2018-03-22at134406.png)

  Alternativ können Sie die ggf. bereits abgebrochene Vererbung erneut aktivieren:

  ![Vererbung erneut aktivieren](do-not-localize/screen_shot_2018-03-22at134417.png)

  Die Rollout-Aktion steht auch im Blueprint oder in der Live Copy-Quelle zur Verfügung:

  ![Rollout](do-not-localize/screen_shot_2018-03-22at134516.png)

* **Ein vererbtes Absatzsystem**

  Das Dialogfeld „Konfiguration“. Beispielsweise wie beim vererbten Absatzsystem:

  ![Vererbtes Absatzsystem](assets/chlimage_1-124.png)

## Bearbeiten der Seitenvorlage {#editing-the-page-template}

Wenn die Seite auf einer [bearbeitbaren Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates) basiert, können Sie einfach zum [Vorlagen-Editor](/help/sites-authoring/templates.md#editing-templates-template-authors) wechseln, indem Sie **Vorlage bearbeiten** im [Menü „Seiteninformationen“](/help/sites-authoring/author-environment-tools.md#page-information) auswählen.

Wenn die Seite auf einer [statischen Vorlage](/help/sites-authoring/templates.md#editable-and-static-templates) basiert, können Sie auf der Symbolleiste die [Seitenmodusauswahl](/help/sites-authoring/author-environment-tools.md#page-modes) verwenden, um zum [Design-Modus](/help/sites-authoring/default-components-designmode.md) zu wechseln und Komponenten auf der Seite zu aktivieren oder zu deaktivieren.

Durch Auswählen der Seite in der [Spaltenansicht](/help/sites-authoring/basic-handling.md#column-view) oder [Listenansicht](/help/sites-authoring/basic-handling.md#list-view) können Sie schnell und einfach feststellen, auf welcher Vorlage die Seite basiert.

## Live Copy-Status {#live-copy-status}

Mit dem [Seitenmodus „Live Copy-Status“](/help/sites-authoring/author-environment-tools.md#page-modes) erhalten Sie einen schnellen Überblick über den Live Copy-Status und darüber, welche Komponenten übernommen bzw. nicht übernommen wurden:

* Grüner Rahmen: Vererbt
* Pinkfarbener Rahmen: Vererbung wurde abgebrochen

Zum Beispiel:

![Live Copy-Vererbungsstatus](assets/screen_shot_2018-03-22at134820.png)

## Hinzufügen von Anmerkungen {#adding-annotations}

[Anmerkungen](/help/sites-authoring/annotations.md) ermöglichen es Prüferinnen und Prüfern sowie anderen Autorinnen und Autoren, Feedback zu Ihrem Inhalt zu geben. Sie werden häufig zu Überprüfungs- und Validierungszwecken verwendet.

## Anzeigen einer Seitenvorschau {#previewing-pages}

Für die Anzeige einer Seitenvorschau stehen zwei Optionen zur Verfügung:

* [Vorschaumodus](#preview-mode) – für einen schnellen Blick auf die Seite im Kontext

* [Als veröffentlicht anzeigen](#view-as-published) – eine vollständige Vorschau, die die Seite auf einer neuen Registerkarte öffnet

>[!NOTE]
>
>* Links im Inhalt sind sichtbar, können jedoch im Bearbeitungsmodus nicht aufgerufen werden.
>* Verwenden Sie eine der Vorschauoptionen, wenn Sie mithilfe von Links navigieren möchten.
>* Verwenden Sie den [Tastaturbefehl](/help/sites-authoring/keyboard-shortcuts.md) `Ctrl-Shift-M` (Strg+Umschalt+M), um zwischen der Vorschau und dem zuletzt ausgewählten Modus zu wechseln.
>

>[!NOTE]
>
>Das WCM-Modus-Cookie wird für beide Vorschauoptionen gesetzt.

### Vorschaumodus {#preview-mode}

Beim Bearbeiten von Inhalt können Sie mithilfe des [Vorschaumodus](/help/sites-authoring/author-environment-tools.md#page-modes) eine Vorschau der Seite anzeigen. In diesem Modus haben Sie folgende Möglichkeiten:

* Blenden Sie verschiedene Bearbeitungsmechanismen aus, damit Sie eine Schnellansicht darüber erhalten, wie die Seite veröffentlicht aussehen wird.
* Verwenden Sie Links zur Navigation.
* Der Seiteninhalt wird **nicht** aktualisiert.

Bei der Bearbeitung einer Seite können Sie den Vorschaumodus über das Symbol rechts oben im Seiteneditor aufrufen:

![Vorschau](assets/chlimage_1-125.png)

### Als veröffentlicht anzeigen {#view-as-published}

Die Option **Als veröffentlicht anzeigen** ist über das Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) verfügbar. Mit dieser Option wird die Seite in einer neuen Registerkarte geöffnet, ihr Inhalt aktualisiert und die Seite so angezeigt, wie sie später nach der Veröffentlichung aussieht.

## Sperren einer Seite {#locking-a-page}

AEM bietet Ihnen die Möglichkeit, eine Seite zu sperren, sodass niemand außer Ihnen den Inhalt bearbeiten kann. Dies ist nützlich, wenn Sie zahlreiche Änderungen an einer bestimmten Seite vornehmen oder eine Seite für kurze Zeit einfrieren möchten.

Eine Seite kann wie folgt gesperrt werden:

* **Sites**-Konsole

   1. Wählen Sie die Seite mit dem [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) aus.
   1. Wählen Sie das Sperrsymbol aus.

  ![Sperrsymbol](assets/screen_shot_2018-03-22at134928.png)

* **Seiteneditor**

   1. Wählen Sie das Symbol für die **Seiteninformationen** aus, um das Menü zu öffnen.
   1. Wählen Sie die Option **Seite sperren** aus.

Nach der Sperrung werden die Informationen der Konsolenansicht aktualisiert und beim Bearbeiten wird in der Symbolleiste ein Vorhängeschlosssymbol angezeigt.

![Vorhängeschlosssymbol](assets/screen_shot_2018-03-22at135010.png)

>[!CAUTION]
>
>Seiten können gesperrt werden, wenn [anstelle eines Benutzers agiert wird](/help/sites-administering/security.md#impersonating-another-user). Eine auf diese Weise gesperrte Seite kann dann jedoch nur von der Person, die stellvertretend agiert hat, oder von Admins entsperrt werden.
>
>Seiten können nicht entsperrt werden, indem man sich als die Person ausgibt, der die Seite gesperrt hat.

## Entsperren einer Seite {#unlocking-a-page}

Das Entsperren einer Seite läuft ähnlich ab wie das [Sperren der Seite](#locking-a-page). Wenn die Seite gesperrt ist, werden die Sperroptionen durch Aktionen zum Entsperren ersetzt.

Im Menü „Seiteninformationen“ steht dann die Option **Entsperren** zur Verfügung und das Vorhängeschlosssymbol in der Sites-Konsole wird durch ein **Entsperren-Symbol** ersetzt.

![Entsperren](assets/screen_shot_2018-03-22at134942.png)

>[!CAUTION]
>
>Seiten können gesperrt werden, wenn [anstelle eines Benutzers agiert wird](/help/sites-administering/security.md#impersonating-another-user). Eine auf diese Weise gesperrte Seite kann dann jedoch nur von der Person, die stellvertretend agiert hat, oder von Admins entsperrt werden.
>
>Seiten können nicht entsperrt werden, indem man sich als die Person ausgibt, der die Seite gesperrt hat.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen {#undoing-and-redoing-page-edits}

Mit den folgenden Symbolen können Sie eine Aktion rückgängig machen oder wiederholen. Diese werden gegebenenfalls in der Symbolleiste angezeigt:

![Rückgängig machen und wiederholen](do-not-localize/screen_shot_2018-03-23at093614.png)

>[!NOTE]
>
>Mit dem [Tastaturbefehl](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) `Ctrl-Z` (Strg+Z) können Sie Bearbeitungen ebenfalls rückgängig machen.
>
>Analog dazu können Sie zum Wiederholen von Bearbeitungen den Tastaturbefehl `Ctrl-Y` (Strg+Y) verwenden.

>[!NOTE]
>
>Siehe [Rückgängigmachen und Wiederholen von Seitenbearbeitungen - Die Theorie](#undoing-and-redoing-page-edits-the-theory); dort erfahren Sie, was beim Rückgängigmachen und Wiederholen von Seitenbearbeitungen möglich ist.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen - Die Theorie {#undoing-and-redoing-page-edits-the-theory}

>[!NOTE]
>
>Ihre bzw. Ihr Systemadmin kann [verschiedene Aspekte der Funktionen zum Rückgängigmachen/Wiederholen](/help/sites-administering/config-undo.md) den Anforderungen Ihrer Instanz entsprechend konfigurieren.

AEM speichert einen Verlauf der Aktionen, die Sie ausführen, sowie die Reihenfolge der Ausführung. Diese Funktion bedeutet, dass Sie mehrere Aktionen in der (umgekehrten) Reihenfolge ihrer Ausführung rückgängig machen und bei Bedarf die Aktionen wiederholen können, wenn Sie eine oder mehrere davon erneut anwenden möchten.

Wenn ein Element auf der Inhaltsseite ausgewählt wird, gelten die Befehle „Rückgängig“ und „Wiederholen“ für das ausgewählte Element, also z. B. für eine Textkomponente.

Das Verhalten der Befehle „Rückgängig“ und „Wiederherstellen“ ist ähnlich wie in anderen Software-Programmen. Verwenden Sie die Befehle, um den letzten Zustand Ihrer Web-Seite wiederherzustellen, während Sie Entscheidungen über den Inhalt treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Falls Sie dann entscheiden, dass die vorherige Position besser war, verwenden Sie den Befehl „Wiederherstellen“, um „das Rückgängigmachen rückgängig zu machen“.

>[!NOTE]
>
>Sie haben folgende Möglichkeiten:
>
>* Sie können Aktionen wiederholen, solange Sie seit der Verwendung von „Rückgängig machen“ keine Seitenbearbeitungen durchgeführt haben.
>* Sie können maximal 20 Bearbeitungsaktionen rückgängig machen (Standardeinstellung).
>* Sie können zum Rückgängigmachen und Wiederholen auch [Tastaturbefehle](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) verwenden.
>

Sie können die folgenden Arten von Seitenänderungen rückgängig machen und wiederherstellen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung von Absatzinhalten im Kontext
* Kopieren, Ausschneiden und Einfügen von Elementen auf einer Seite

Für Formularfelder, die durch Formular-Komponenten erzeugt werden, dürfen beim Erstellen von Seiten keine Werte angegeben werden. Folglich haben die Befehle „Rückgängig“ und „Wiederholen“ keine Auswirkungen auf Änderungen, die Sie an den Werten dieser Komponententypen vornehmen. Sie können beispielsweise die Auswahl eines Werts in einer Dropdown-Liste nicht rückgängig machen.

>[!NOTE]
>
>Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden.

>[!NOTE]
>
>Änderungen an Dateien und Bildern können für einen Verlauf von mindestens zehn Stunden rückgängig gemacht werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Ihre Admins können die Standardzeit von zehn Stunden ändern.
