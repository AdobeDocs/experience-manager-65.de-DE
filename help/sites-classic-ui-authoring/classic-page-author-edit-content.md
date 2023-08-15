---
title: Bearbeiten des Seiteninhalts
description: Inhalte werden mithilfe von Komponenten hinzugefügt, die per Drag-and-Drop auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.
uuid: e7b65ceb-263c-46f2-91e3-11dec3a016fa
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: de321869-ebf9-41a1-8203-e12bdb088678
docset: aem65
exl-id: e1b5aea0-983c-4e7b-9d35-d7beeee45dc7
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 95%

---

# Bearbeiten des Seiteninhalts{#editing-page-content}

Sobald Ihre Seite erstellt ist (neu oder im Rahmen eines Launch oder einer Live Copy), können Sie den Inhalt bearbeiten und die erforderlichen Aktualisierungen vornehmen.

Inhalte werden mithilfe von [Komponenten](/help/sites-classic-ui-authoring/classic-page-author-default-components.md) hinzugefügt (entsprechend dem Inhaltstyp), die per Drag-and-Drop auf die Seite gezogen werden können. Dort können sie dann bearbeitet, verschoben oder gelöscht werden.

>[!NOTE]
>
>Ihr Konto benötigt die [entsprechenden Zugriffsrechte](/help/sites-administering/security.md) und [Berechtigungen](/help/sites-administering/security.md#permissions), um Seiten zu bearbeiten, z. B. Komponenten hinzuzufügen, zu bearbeiten oder zu löschen, zu kommentieren, freizuschalten.
>
>Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an die bzw. den Systemadmin zu wenden.

## Sidekick {#sidekick}

Der Sidekick ist ein wichtiges Tool beim Erstellen von Seiten. Er ist beim Bearbeiten einer Seite nicht verankert und dadurch immer sichtbar.

Unter anderem sind folgende Registerkarten und Symbole verfügbar:

* Komponenten
* Seite
* Informationen
* Versionierung
* Workflow
* Modi
* Strukturvorlage
* ClientContext
* Websites

![chlimage_1-71](assets/chlimage_1-71.png)

Diese bieten Zugriff auf eine Vielzahl von Funktionen, zu denen unter anderem folgende gehören:

* [Auswählen der Komponenten](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#sidekick)
* [Anzeigen der Verweise](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#showing-references)
* [Zugriff auf das Auditprotokoll](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#audit-log)
* [Umschalten zwischen Modi](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#page-modes)
* [Erstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#creating-a-new-version), [Wiederherstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick) und [Vergleichen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#comparing-with-a-previous-version) von Versionen

* [Veröffentlichen einer Seite](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#publishing-a-page), [Rückgängigmachen der Veröffentlichung](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#unpublishing-a-page)

* [Bearbeiten der Seiteneigenschaften](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)

* [Strukturvorlagen](/help/sites-authoring/scaffolding.md)

* [ClientContext](/help/sites-administering/client-context.md)

## Einfügen einer Komponente {#inserting-a-component}

### Einfügen einer Komponente {#inserting-a-component-1}

Nachdem Sie die Seite geöffnet haben, können Sie beginnen, Inhalte hinzuzufügen. Dies erfolgt durch Hinzufügen von Komponenten (auch Absätze genannt).

So fügen Sie eine neue Komponente ein:

1. Es gibt mehrere Möglichkeiten, die Art des einzufügenden Absatzes auszuwählen:

   * Doppelklicken Sie auf den Bereich **Komponenten oder Assets hierher ziehen…** – die Symbolleiste **Neue Komponente einfügen** öffnet sich. Wählen Sie eine Komponente aus und klicken Sie auf **OK**.

   * Ziehen Sie per Drag-and-Drop eine Komponente aus der unverankerten Symbolleiste (auch Sidekick genannt), um einen neuen Absatz einzufügen.
   * Klicken Sie mit der rechten Maustaste auf einen bestehenden Absatz und wählen Sie **Neu...**. Die Symbolleiste „Neue Komponente einfügen“ wird geöffnet. Wählen Sie eine Komponente aus und klicken Sie auf **OK**.

   ![screen_shot_2012-02-15at115605am](assets/screen_shot_2012-02-15at115605am.png)

1. Sowohl im Sidekick als auch in der Symbolleiste **Neue Komponente einfügen** wird eine Liste der verfügbaren Komponenten (Absatztypen) angezeigt. Diese Liste kann gegliedert sein (z. B. in „Allgemein“, „Spalten“ usw.) und Sie können die Gliederungen nach Bedarf aus- oder einblenden.

   Abhängig von Ihrer Produktionsumgebung können diese Optionen unterschiedlich sein. Ausführliche Informationen zu Komponenten finden Sie unter [Standardkomponenten](/help/sites-classic-ui-authoring/classic-page-author-default-components.md).

1. Fügen Sie die gewünschte Komponente auf der Seite ein. Doppelklicken Sie dann auf den Absatz. Daraufhin wird ein Fenster geöffnet, in dem Sie Ihren Absatz konfigurieren und Inhalt hinzufügen können.

### Einfügen einer Komponente mit der Inhaltssuche {#inserting-a-component-using-the-content-finder}

Sie können eine neue Komponente zur Seite hinzufügen, indem Sie ein Asset aus dem [Content Finder](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#the-content-finder) ziehen. Dadurch wird automatisch eine neue Komponente des entsprechenden Typs erstellt, die das Asset enthält.

Dies gilt für folgende Asset-Typen (einige sind vom Seiten-/Absatzsystem abhängig):

| Asset-Typ | Resultierender Komponententyp |
|---|---|
| Bild | Bild |
| Dokument | Download |
| Produkt | Produkt |
| Video  | Flash |

>[!NOTE]
>
>Dieses Verhalten kann für Ihre Installation konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren eines Absatzsystems zum Erstellen einer Komponenteninstanz infolge des Ziehens eines Assets](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance).

So erstellen Sie eine Komponente, indem Sie einen der obigen Asset-Typen ziehen:

1. Öffnen Sie die Seite im Modus [**Bearbeiten**](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#page-modes).
1. Öffnen Sie die [Inhaltssuche](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#the-content-finder).
1. Ziehen Sie die benötigte Komponente an die passende Position. Der [Komponenten-Platzhalter](#componentplaceholder) zeigt an, wo die Komponente platziert wird.

   Eine für den Asset-Typ geeignete Komponente wird am erforderlichen Speicherort erstellt und enthält das ausgewählte Asset.

1. [Bearbeiten](#editmovecopypastedelete) Sie bei Bedarf die Komponente.

## Bearbeiten einer Komponente (Inhalt und Eigenschaften) {#editing-a-component-content-and-properties}

Führen Sie einen der folgenden Schritte aus, um einen vorhandenen Absatz zu bearbeiten:

* **Doppelklicken** Sie auf den Absatz, um ihn zu öffnen. Es wird dasselbe Fenster angezeigt wie bei der Erstellung des Absatzes mit dem vorhandenen Inhalt. Nehmen Sie die gewünschten Änderungen vor und klicken Sie auf **OK**.

* **Klicken Sie mit der rechten Maustaste** auf den Absatz und dann auf **Bearbeiten**.

* **Klicken** Sie zweimal auf den Absatz (langsamer Doppelklick), um in den Bearbeitungsmodus zu wechseln. Sie können nun den Text direkt auf der Seite bearbeiten, anstatt ein Dialogfenster aufrufen zu müssen. In diesem Modus steht am oberen Rand der Seite eine Werkzeugleiste zur Verfügung. Nehmen Sie einfach Ihre Änderungen vor, und sie werden automatisch gespeichert.

## Verschieben einer Komponente {#moving-a-component}

So verschieben Sie eine Absatzkomponente:

>[!NOTE]
>
>Sie können eine Komponente auch durch [Ausschneiden und Einfügen](#cut-copy-paste-a-component) verschieben.

1. Wählen Sie den Absatz aus, den Sie verschieben möchten:

   ![screen_shot_2012-02-15at115855am](assets/screen_shot_2012-02-15at115855am.png)

1. Ziehen Sie den Absatz an die neue Stelle. AEM zeigt durch ein grünes Häkchen an, wohin der Absatz verschoben werden kann. Legen Sie ihn an der gewünschten Position ab.
1. Der Absatz wird verschoben:

   ![screen_shot_2012-02-15at120030pm](assets/screen_shot_2012-02-15at120030pm.png)

## Löschen einer Komponente {#deleting-a-component}

So löschen Sie einen Absatz:

1. Wählen Sie den Absatz aus und **klicken Sie mit der rechten Maustaste** darauf:

   ![screen_shot_2012-02-15at120220pm](assets/screen_shot_2012-02-15at120220pm.png)

1. Wählen Sie **Löschen** aus dem Menü. AEM WCM fordert Sie auf, das Löschen des Absatzes zu bestätigen, da es nicht mehr rückgängig gemacht werden kann.
1. Klicken Sie auf **OK**.

>[!NOTE]
>
>Wenn Sie in den [Benutzereigenschaften festgelegt haben, dass die globale Bearbeitungssymbolleiste](/help/sites-classic-ui-authoring/author-env-user-props.md) angezeigt werden soll, können Sie die verfügbaren Schaltflächen **Kopieren**, **Ausschneiden**, **Einfügen** und **Löschen** verwenden.
>
>Es stehen auch verschiedene [Tastaturbefehle](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zur Verfügung.

## Ausschneiden/Kopieren/Einfügen einer Komponente {#cut-copy-paste-a-component}

Wie beim [Löschen einer Komponente](#deleting-a-component) können Sie das Kontextmenü nutzen, um eine Komponente zu kopieren, auszuschneiden und/oder einzufügen.

>[!NOTE]
>
>Wenn Sie in den [Benutzereigenschaften festgelegt haben, dass die globale Bearbeitungssymbolleiste](/help/sites-classic-ui-authoring/author-env-user-props.md) angezeigt werden soll, können Sie die verfügbaren Schaltflächen **Kopieren**, **Ausschneiden**, **Einfügen** und **Löschen** verwenden.
>
>Es stehen auch verschiedene [Tastaturbefehle](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zur Verfügung.

>[!NOTE]
>
>Das Ausschneiden, Kopieren und Einfügen von Inhalt wird nur innerhalb derselben Seite unterstützt.

## Vererbte Komponenten {#inherited-components}

Vererbte Komponenten können sich aus diversen Szenarien ergeben, wie:

* [Verwaltung mehrerer Sites](/help/sites-administering/msm.md), auch in Kombination mit [Strukturvorlagen](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md#scaffolding-with-msm-inheritance).

* [Launch](/help/sites-classic-ui-authoring/classic-launches.md) (wenn er auf Live Copy basiert).
* Spezifische Komponenten, z. B. das Vererbungs-Absatzsystem in Geometrixx.

Sie können die Vererbung deaktivieren (und dann wieder aktivieren). Abhängig von der Komponente kann dies über Folgendes verfügbar sein:

1. **Live Copy**

   Wenn eine Komponente Teil einer Live Copy oder eines Launches ist, wird dies durch ein Schlosssymbol angezeigt. Sie können auf das Vorhängeschloss klicken, um die Vererbung abzubrechen.

   * Das Schlosssymbol wird angezeigt, wenn die Komponente ausgewählt wird. Beispiel:

   ![chlimage_1-72](assets/chlimage_1-72.png)

   * Das Schloss wird ebenfalls im Dialogfeld von Komponenten angezeigt. Beispiel:

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. **Ein vererbtes Absatzsystem**

   Das Konfigurationsdialogfeld. Beispielsweise wie beim vererbten Absatzsystem in Geometrixx:

   ![chlimage_1-74](assets/chlimage_1-74.png)

## Hinzufügen von Anmerkungen {#adding-annotations}

[Anmerkungen](/help/sites-classic-ui-authoring/classic-page-author-annotations.md) ermöglichen es anderen Autorinnen und Autoren, Feedback zu Ihrem Inhalt zu geben. Dies wird häufig zu Überprüfungs- und Validierungszwecken verwendet.

## Anzeigen einer Seitenvorschau {#previewing-pages}

Es gibt zwei Symbole im unteren Rand des Sidekicks, die für die Vorschau von Seiten wichtig sind:

![Unterer Rand des Sidekicks mit einer horizontalen Zeile mit sieben Symbolen. Zwei der Symbole am Anfang der Zeile, das Symbol „Bearbeiten“ und das Symbol „Vorschaumodus“, werden durch ein Bleistiftsymbol bzw. ein Lupensymbol dargestellt.](do-not-localize/chlimage_1-5.png)

* Das Bleistiftsymbol zeigt an, dass Sie sich derzeit im Bearbeitungsmodus befinden, in dem Sie Inhalte hinzufügen, ändern, verschieben oder löschen können.

  ![Symbol „Bearbeiten“, dargestellt durch ein Bleistiftsymbol.](do-not-localize/chlimage_1-6.png)

* Mit dem Lupensymbol können Sie den Vorschaumodus auswählen, in dem die Seite so angezeigt wird, wie sie in der Veröffentlichungsumgebung angezeigt wird (manchmal ist auch eine Seitenaktualisierung erforderlich):

  ![Symbol „Vorschaumodus“, dargestellt durch ein Lupensymbol.](do-not-localize/chlimage_1-7.png)

  Im Vorschaumodus wird der Sidekick minimiert. Klicken Sie auf den Pfeil nach unten, um in den Bearbeitungsmodus zurückzukehren:

  ![Balken mit AEM als Titel und einem Symbol „Bearbeiten“ rechts neben dem Titel, dargestellt durch ein Abwärtspfeilsymbol.](do-not-localize/chlimage_1-8.png)

## Suchen und Ersetzen {#find-replace}

Bei umfangreicheren Bearbeitungen desselben Satzes wird ein **[Suchen und Ersetzen](/help/sites-classic-ui-authoring/author-env-search.md#find-and-replace)** -Menüoption können Sie innerhalb eines Bereichs der Website nach mehreren Instanzen einer Zeichenfolge suchen und diese ersetzen.

## Sperren einer Seite {#locking-a-page}

AEM ermöglicht das Sperren einer Seite, sodass niemand außer Ihnen den Inhalt ändern kann. Dies ist hilfreich, wenn Sie eine Vielzahl von Bearbeitungen an einer bestimmten Seite vornehmen oder wenn Sie eine Seite für eine kurze Zeit einfrieren möchten.

>[!CAUTION]
>
>Das Sperren einer Seite sollte mit Vorsicht verwendet werden, da die einzige Person, die eine Seite entsperren kann, die Person ist, die sie gesperrt hat (oder ein Konto mit Administratorrechten).

So sperren Sie eine Seite:

1. Wählen Sie auf der Registerkarte **Websites** die Seite aus, die Sie sperren möchten.
1. Doppelklicken Sie auf die Seite, um sie zur Bearbeitung zu öffnen.
1. Wählen Sie auf der Registerkarte **Seite** des Sidekicks die Option **Seite sperren**:

   ![screen_shot_2012-02-08at15750pm](assets/screen_shot_2012-02-08at15750pm.png)

   Eine Meldung über die Sperrung der Seite für andere Benutzer wird angezeigt. Darüber hinaus wird die Seite im rechten Fenster der Konsole **Websites** von AEM WCM als gesperrt angezeigt und angegeben, wer die Seite gesperrt hat.

   ![screen_shot_2012-02-08at20657pm](assets/screen_shot_2012-02-08at20657pm.png)

## Entsperren einer Seite {#unlocking-a-page}

Um eine Seite zu entsperren:

1. Wählen Sie auf der Registerkarte **Websites** die Seite aus, die Sie entsperren möchten.
1. Doppelklicken Sie auf die Seite, um sie zu öffnen.
1. Wählen Sie auf der Registerkarte **Seite** des Sidekicks **Seite entsperren** aus.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen {#undoing-and-redoing-page-edits}

Verwenden Sie die folgenden Tastaturbefehle, während der Inhalts-Frame der Seite im Fokus ist:

* Rückgängig: Strg+Z (Windows) bzw. Befehl+Z (Mac)
* Wiederholen: Strg+Y (Windows) bzw. Befehl+Y (Mac)

Wenn Sie das Entfernen, Hinzufügen oder Verschieben von Absätzen rückgängig machen bzw. wiederholen, werden die betroffenen Absätze (standardmäßig) durch Markierungen hervorgehoben.

>[!NOTE]
>
>Siehe [Rückgängigmachen und Wiederholen von Seitenbearbeitungen – Die Theorie](#undoing-and-redoing-page-edits-the-theory); dort erfahren Sie, was beim Rückgängigmachen und Wiederholen von Seitenbearbeitungen möglich ist.

## Rückgängigmachen und Wiederholen von Seitenbearbeitungen - Die Theorie {#undoing-and-redoing-page-edits-the-theory}

>[!NOTE]
>
>Ihre bzw. Ihr Systemadmin kann [verschiedene Aspekte der Funktionen zum Rückgängigmachen/Wiederholen](/help/sites-administering/config-undo.md) den Anforderungen Ihrer Instanz entsprechend konfigurieren.

AEM speichert einen Verlauf der Aktionen, die Sie ausführen, sowie die Reihenfolge der Ausführung. Sie können also mehrere Aktionen in der umgekehrten Reihenfolge ihrer Ausführung rückgängig machen. Dann können Sie den Befehl zum Wiederherstellen verwenden, um eine oder mehrere Aktionen zu wiederholen.

Wenn ein Element auf der Inhaltsseite ausgewählt wird, gelten die Befehle „Rückgängig“ und „Wiederherstellen“ für das ausgewählte Element, also z. B. für eine Textkomponente.

Das Verhalten der Befehle „Rückgängig“ und „Wiederherstellen“ ist ähnlich wie in anderen Software-Programmen. Verwenden Sie die Befehle, um den letzten Zustand Ihrer Web-Seite wiederherzustellen, während Sie Entscheidungen über den Inhalt treffen. Wenn Sie beispielsweise einen Textabsatz an eine Stelle auf der Seite verschoben haben, können Sie ihn mithilfe des Befehls zum Rückgängigmachen wieder zurück an die ursprüngliche Stelle verschieben. Wenn Sie sich dann erneut dafür entscheiden, den Absatz zu verschieben, verwenden Sie den Befehl zum Wiederherstellen.

>[!NOTE]
>
>Sie haben folgende Möglichkeiten:
>
>* Sie können Aktionen wiederholen, solange Sie seit der Verwendung von „Rückgängig machen“ keine Seitenbearbeitungen durchgeführt haben.
>* Sie können maximal 20 Bearbeitungsaktionen rückgängig machen (Standardeinstellung).
>* [Tastaturbefehle](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zum Rückgängigmachen und Wiederherstellen verwenden.
>

Sie können die folgenden Arten von Seitenänderungen rückgängig machen und wiederherstellen:

* Hinzufügen, Bearbeiten, Entfernen und Verschieben von Absätzen
* Bearbeitung von Absatzinhalten im Kontext
* Kopieren, Ausschneiden und Einfügen von Elementen auf einer Seite
* Seitenübergreifendes Kopieren, Ausschneiden und Einfügen von Elementen
* Hinzufügen, Entfernen und Ändern von Dateien und Bildern
* Hinzufügen, Entfernen und Ändern von Anmerkungen und Zeichnungen
* Änderungen an der Strukturvorlage
* Hinzufügen und Entfernen von Verweisen
* Ändern von Eigenschaftswerten in Komponentendialogfeldern

Für Formularfelder, die durch Formular-Komponenten erzeugt werden, dürfen beim Erstellen von Seiten keine Werte angegeben werden. Folglich haben die Befehle „Rückgängig“ und „Wiederholen“ keine Auswirkungen auf Änderungen, die Sie an den Werten dieser Komponententypen vornehmen. Sie können beispielsweise die Auswahl eines Werts in einer Dropdown-Liste nicht rückgängig machen.

>[!NOTE]
>
>Spezielle Berechtigungen sind erforderlich, um Änderungen rückgängig zu machen bzw. wiederherzustellen, die an Dateien und Bildern vorgenommen wurden. Außerdem kann das Rückgängigmachen Änderungen an Dateien und Bildern nur einige Stunden garantiert werden. Bei länger zurückliegenden Änderungen ist dies unter Umständen nicht mehr möglich. Der bzw. die zuständige Admin kann Berechtigungen erteilen und die Standarddauer von zehn Stunden ändern.
