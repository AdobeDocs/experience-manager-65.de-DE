---
title: Erstellen von Seitenvorlagen
description: Eine Vorlage definiert die Struktur einer erstellten Seite und mit dem Vorlageneditor ist die Erstellung und Verwaltung von Vorlagen nicht mehr nur Entwicklern vorbehalten.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
exl-id: 363b8fab-6ce7-4338-8478-3f25f2a1f117
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '4840'
ht-degree: 83%

---

# Erstellen von Seitenvorlagen{#creating-page-templates}

Wenn Sie eine Seite erstellen, müssen Sie eine Vorlage auswählen. Diese wird als Grundlage für die Erstellung der neuen Seite verwendet. Die Vorlage definiert die Struktur der Seite, anfängliche Inhalte und die Komponenten, die verwendet werden können.

Mit dem **Vorlageneditor** ist das Erstellen und Verwalten von Vorlagen nicht mehr nur eine Aufgabe für Entwickler. Auch ein Power User, der als **Vorlagenautor** bezeichnet wird, kann einbezogen werden. Entwickler müssen weiterhin die Umgebung einrichten, Clientbibliotheken erstellen und die zu verwendenden Komponenten erstellen. Sobald diese Grundlagen vorhanden sind, hat der **Vorlagenautor** jedoch die Flexibilität, Vorlagen ohne Entwicklungsprojekt zu erstellen und zu konfigurieren.

Mit der **Vorlagenkonsole** können Vorlagenautorinnen bzw. -autoren:

* Erstellen Sie eine Vorlage oder kopieren Sie eine vorhandene Vorlage.
* Verwalten des Lebenszyklus der Vorlage

Mit dem **Vorlageneditor** können Vorlagenautoren:

* Komponenten zur Vorlage hinzufügen und sie auf einem responsiven Raster positionieren
* die Komponenten vorkonfigurieren
* Definieren Sie, welche Komponenten auf Seiten bearbeitet werden können, die mit der Vorlage erstellt wurden.

In diesem Dokument wird erklärt, wie ein **Vorlagenautor** die Vorlagenkonsole und den Vorlageneditor verwenden kann, um bearbeitbare Vorlagen zu erstellen und zu verwalten.

Ausführliche Informationen zur Funktionsweise von bearbeitbaren Vorlagen auf technischer Ebene finden Sie im Entwicklerdokument [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md) für weitere Informationen.

>[!NOTE]
>
>Der **Vorlageneditor** unterstützt kein Targeting direkt auf Vorlagenstufe. Seiten, die auf der Basis einer bearbeitbaren Vorlage erstellt wurden, können als Zielgruppe ausgewählt werden, die Vorlagen selbst können jedoch nicht erstellt werden.

>[!CAUTION]
>
>Die Seiten und Vorlagen, die mit der **Vorlagenkonsole** erstellt wurden, sind nicht zur Verwendung in der klassischen Benutzeroberfläche bestimmt und eine solche Verwendung wird nicht unterstützt.

## Bevor Sie beginnen {#before-you-start}

>[!NOTE]
>
>Ein Admin muss im **Konfigurations-Browser** einen Vorlagenordner konfigurieren und entsprechende Berechtigungen anwenden, bevor ein Vorlagenautor eine Vorlage in diesem Ordner erstellen kann.

Beachten Sie vor dem Start die folgenden Punkte:

* Das Erstellen einer Vorlage erfordert Zusammenarbeit. Aus diesem Grund wird für jede Aufgabe eine [Rolle](#roles) angezeigt.

* Je nachdem, wie Ihre Instanz konfiguriert ist, kann es nützlich sein, sich darüber im Klaren zu sein, dass AEM jetzt [zwei grundlegende Vorlagentypen](/help/sites-authoring/templates.md#editable-and-static-templates). Dies hat keine Auswirkungen auf die tatsächliche [Verwenden einer Vorlage zum Erstellen einer Seite](#using-a-template-to-create-a-page), aber es wirkt sich auf den Typ der Vorlage aus, die Sie erstellen können, und darauf aus, wie eine Seite mit der Vorlage in Beziehung steht.

### Rollen {#roles}

Erstellen einer Vorlage mit dem **Vorlagenkonsole** und **Vorlagen-Editor** erfordert die Zusammenarbeit zwischen den folgenden Rollen:

* **Admin**:

   * Erstellt neue Ordner für Vorlagen, wofür `admin`-Berechtigungen erforderlich sind.

   * Solche Aufgaben können oft auch von einer Entwicklungsperson durchgeführt werden

* **Entwickler**:

   * Konzentriert sich auf die technischen/internen Details
   * Muss Erfahrung mit der Entwicklungsumgebung haben.
   * Versorgt den Vorlagenautor mit den erforderlichen Informationen.

* **Vorlagenautor**:

   * Dies ist ein bestimmter Autor, der Mitglied der Gruppe `template-authors` ist.

      * Weist die erforderlichen Berechtigungen zu.

   * Kann die Verwendung von Komponenten und andere wichtige Einzelheiten konfigurieren, was Folgendes erfordert:

      * Einige technische Kenntnisse

         * Zum Beispiel zur Verwendung von Mustern, wenn Pfade definiert werden.

      * Technische Informationen vom Entwickler.

Aufgrund der Natur einiger Aufgaben (etwa das Erstellen eines Ordners) ist eine Entwicklungsumgebung erforderlich, für die wiederum Wissen/Erfahrung benötigt wird.

Die in diesem Dokument beschriebenen Aufgaben werden jeweils mit der Rolle aufgelistet, die für ihre Durchführung verantwortlich ist.

### Bearbeitbare und statische Vorlagen {#editable-and-static-templates}

AEM bietet nun zwei grundlegende Arten von Vorlagen:

* [Bearbeitbare Vorlagen](/help/sites-authoring/templates.md#creatingandmanagingnewtemplates)

   * Können von Vorlagenautoren [erstellt](#creatinganewtemplate) und [bearbeitet](#editingatemplate) werden, indem die **Vorlagenkonsole und der Vorlagen-Editor** verwendet werden. Auf die **Vorlagenkonsole** kann im Bereich **Allgemein** der Konsole **Werkzeuge** zugegriffen werden.

   * Nachdem die neue Seite erstellt wurde, wird eine dynamische Verbindung zwischen der Seite und der Vorlage aufrechterhalten. Das bedeutet, dass Änderungen an der Vorlagenstruktur und/oder an gesperrten Inhalten auf allen Seiten übernommen werden, die mit dieser Vorlage erstellt werden. Änderungen am entsperrten (d. h. anfänglichen) Inhalt werden nicht übernommen.
   * Verwenden Sie die Inhaltsrichtlinien, die Sie im Vorlagen-Editor definieren können, um die Designeigenschaften beizubehalten. Der Designmodus im Seiteneditor wird nicht mehr für bearbeitbare Vorlagen verwendet.

* Statische Vorlagen

   * Statische Vorlagen sind bereits seit längerem für diverse Versionen von AEM verfügbar.
   * Sie werden [von Ihren Entwicklern bereitgestellt](/help/sites-developing/page-templates-static.md) und können somit nicht von Autoren erstellt oder bearbeitet werden.
   * Sie werden kopiert, um die neue Seite zu erstellen, wobei danach keine dynamische Verbindung besteht (obwohl der Name der Vorlage zu Informationszwecken registriert ist).
   * Verwenden Sie den [Designmodus](/help/sites-authoring/default-components-designmode.md), um Designeigenschaften beizubehalten.
   * Da die Bearbeitung statischer Vorlagen die ausschließliche Aufgabe eines Entwicklers ist, lesen Sie das Entwicklerdokument [Seitenvorlagen - Statisch](/help/sites-developing/page-templates-static.md) für weitere Informationen.

Die Vorlagenkonsole und der Vorlagen-Editor ermöglichen standardmäßig nur die Erstellung und Bearbeitung bearbeitbarer Vorlagen. Deshalb konzentriert sich dieses Dokument ausschließlich auf bearbeitbare Vorlagen.

### Verwenden einer Vorlage zum Erstellen einer Seite {#using-a-template-to-create-a-page}

Bei Verwendung einer Vorlage für [Erstellen einer Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page) Es gibt keinen sichtbaren Unterschied und keinen Hinweis zwischen statischen und bearbeitbaren Vorlagen. Für die Seitenautoren ist der Prozess transparent.

## Erstellen und Verwalten von Vorlagen {#creating-and-managing-templates}

Beim Erstellen einer bearbeitbaren Vorlage haben Sie folgende Möglichkeiten:

* Verwenden Sie die **Vorlagenkonsole**, die im Bereich **Allgemein** der Konsole **Tools** verfügbar ist.

   * Oder direkt unter: [https://localhost:4502/libs/wcm/core/content/sites/templates.html/conf](https://localhost:4502/libs/wcm/core/content/sites/templates.html/conf)

* Erstellen Sie bei Bedarf [einen Ordner für die Vorlagen](#creating-a-template-folder-admin).
* [Erstellen einer Vorlage](#creatinganewtemplateauthor), der anfangs leer ist

* [Definieren Sie bei Bedarf weitere Eigenschaften](#definingtemplatepropertiesauthor) für die Vorlage.
* [Bearbeiten Sie die Vorlage](#editingtemplates), um Folgendes zu definieren:

   * [Struktur](#editingatemplatestructureauthor) – vordefinierter Inhalt, der auf Seiten, die mit der Vorlage erstellt werden, nicht geändert werden kann.
   * [Anfänglicher Inhalt](#editing-a-template-initial-content-author) – vordefinierter Inhalt, der auf den Seiten geändert werden kann, die mit der Vorlage erstellt werden.
   * [Layout](#editingatemplatelayoutauthor) – für eine Vielzahl von Geräten.
   * [Stile](/help/sites-authoring/style-system.md) – zum Definieren der Stile für die Vorlage und ihre Komponenten.

* [Aktivieren Sie die Vorlage](#enablingatemplateauthor) zur Verwendung, wenn Sie eine Seite erstellen.
* [Lassen Sie die Vorlage zu](#allowing-a-template-author), damit sie für die erforderliche Seite oder die Verzweigung Ihrer Website verwendet werden kann.
* [Veröffentlichen Sie die Vorlage](#publishingatemplateauthor), um sie in der Publishing-Umgebung bereitzustellen.

>[!NOTE]
>
>Die **zugelassenen Vorlagen** werden häufig vordefiniert, wenn Sie Ihre Website erstmals einrichten.

>[!CAUTION]
>
>Geben Sie in eine Vorlage nie Informationen ein, die [internationalisiert](/help/sites-developing/i18n.md) werden müssen. Für die Internationalisierung werden die [Lokalisierungsfunktionen der Hauptkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=de) empfohlen.

### Erstellen eines Vorlagenordners – Administrator {#creating-a-template-folder-admin}

Für Ihr Projekt sollte ein Vorlagenordner für Ihre projektspezifischen Vorlagen erstellt werden. Dies ist eine Administratoraufgabe, die im Dokument beschrieben wird [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md#template-folders).

### Erstellen einer neuen Vorlage – Vorlagenautor {#creating-a-new-template-template-author}

1. Öffnen Sie die **Vorlagenkonsole** (über **Tools >** **Allgemein**) und navigieren Sie zum gewünschten Ordner.

   >[!NOTE]
   >
   >In einer Standard-AEM-Instanz ist der Ordner **Global** bereits in der Vorlagenkonsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden.
   >
   >
   >Es wird als Best Practice empfohlen, einen [Vorlagenordner zu verwenden, der für Ihr Projekt erstellt wurde](/help/sites-developing/page-templates-editable.md#template-folders).

1. Wählen Sie **Erstellen** und anschließend **Vorlage erstellen**, um den Assistenten zu öffnen.

1. Wählen Sie einen **Vorlagentyp** aus und klicken Sie dann auf **Weiter**.

   >[!NOTE]
   >
   >Vorlagenarten sind vordefinierte Vorlagen, die als Vorlagen für eine Vorlage betrachtet werden können. Diese werden von Entwicklungspersonen oder den Systemadmins vordefiniert. Weitere Informationen finden Sie im Entwicklerdokument [Seitenvorlagen - bearbeitbar](/help/sites-developing/page-templates-editable.md#template-type).

1. Füllen Sie die **Vorlagendetails** aus:

   * **Vorlagenname**
   * **Beschreibung**

1. Wählen Sie **Erstellen**. Eine Bestätigung wird angezeigt. Wählen Sie **Öffnen**[](#editingatemplate), um mit der Bearbeitung der Vorlage zu beginnen, oder **Fertig**, um zur Vorlagenkonsole zurückzukehren.

   >[!NOTE]
   >
   >Wenn eine neue Vorlage erstellt wird, wird sie in der Konsole als **Entwurf** markiert, was bedeutet, dass sie noch nicht für Seitenautoren zur Verfügung steht.

### Definieren von Vorlageneigenschaften – Vorlagenautor  {#defining-template-properties-template-author}

Eine Vorlage kann die folgenden Eigenschaften aufweisen:

* Bild

   * Bild, das als [Miniatur der Vorlage verwendet wird](/help/sites-authoring/templates.md#template-thumbnail-image), um die Auswahl zu vereinfachen, beispielsweise im Seitenerstellungsassistenten.

      * Kann hochgeladen werden
      * Kann basierend auf dem Vorlageninhalt generiert werden

* Titel

   * Ein Titel, der zur Identifizierung der Vorlage verwendet wird, z. B. im Assistenten **Seite erstellen**.

* Beschreibung

   * Eine optionale Beschreibung, die weitere Informationen über die Vorlage und ihre Verwendung bereitstellt, die beispielsweise im **Seite erstellen** Assistent.

So zeigen Sie die Eigenschaften an bzw. bearbeiten sie:

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Eigenschaften anzeigen** in der Symbolleiste oder in den Schnelloptionen aus, um das Dialogfeld zu öffnen.
1. Jetzt können Sie die Vorlageneigenschaften anzeigen oder bearbeiten.

>[!NOTE]
>
>Vorlagen sind leistungsstarke Tools zur Optimierung des Seitenerstellungs-Workflows. Allerdings können zu viele Vorlagen die Autoren überwältigen und das Erstellen von Seiten unübersichtlich machen. Eine gute Faustregel ist, die Anzahl der Vorlagen unter 100 zu halten.
>
>Adobe empfiehlt, aufgrund möglicher Leistungsauswirkungen nicht mehr als 1.000 Vorlagen zu verwenden.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Vorlagenminiaturbild {#template-thumbnail-image}

So definieren Sie eine Vorlagenminiaturansicht:

1. Bearbeiten Sie die Vorlageneigenschaften.
1. Wählen Sie aus, ob Sie eine Miniaturansicht hochladen oder aus dem Vorlageninhalt generieren lassen möchten.

   * Wenn Sie eine Miniaturansicht hochladen möchten, klicken oder tippen Sie auf **Bild hochladen**.
   * Wenn Sie eine Miniatur erzeugen möchten, klicken oder tippen Sie auf **Vorschau generieren**

1. Für beide Methoden wird eine Vorschau der Miniaturansicht angezeigt.

   Wenn Sie mit dem Ergebnis nicht zufrieden sind, klicken oder tippen Sie auf **Löschen**, um ein anderes Bild hochzuladen oder die Miniaturansicht neu zu erzeugen.

1. Wenn Sie mit der Miniaturansicht zufrieden sind, klicken oder tippen Sie auf **Speichern und schließen**.

### Aktivieren und Zulassen einer Vorlage – Vorlagenautor {#enabling-and-allowing-a-template-template-author}

Um beim Erstellen einer Seite eine Vorlage zu verwenden, gehen Sie wie folgt vor:

* [Aktivieren Sie die Vorlage](#enablingatemplate), um sie verfügbar zu machen, wenn Seiten erstellt werden.
* [Lassen Sie die Vorlage zu](#allowingatemplate), um die Inhaltsverzweigungen anzugeben, in denen die Vorlage verwendet werden kann.

#### Aktivieren einer Vorlage – Vorlagenautor {#enabling-a-template-template-author}

Eine Vorlage kann aktiviert oder deaktiviert werden, damit sie im Assistenten **Seite erstellen** verfügbar bzw. nicht verfügbar ist.

>[!CAUTION]
>
>Sobald eine Vorlage aktiviert ist, wird eine Warnung angezeigt, wenn ein Vorlagenautor beginnt, die Vorlage weiter zu aktualisieren. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie in der Symbolleiste die Option **Aktivieren** oder **Deaktivieren** und bestätigen Sie Ihre Wahl im Bestätigungsdialogfeld.
1. Sie können Ihre Vorlage jetzt verwenden, wenn [Erstellen einer Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page), obwohl Sie wahrscheinlich [Vorlage bearbeiten](#editingatemplate) nach Ihren eigenen Anforderungen.

>[!NOTE]
>
>Der Status einer Vorlage („Entwurf“, „Aktiviert“ oder „Deaktiviert“) wird in der Konsole angezeigt.

#### Zulassen einer Vorlage – Autor {#allowing-a-template-author}

Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

1. Öffnen Sie die [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) für die Stammseite der Verzweigung, in der die Vorlage verfügbar sein soll.

1. Öffnen Sie die Registerkarte **Erweitert**.

1. under **Vorlageneinstellungen** use **Feld hinzufügen** um die Pfade zu Ihren Vorlagen anzugeben.

   Der Pfad kann explizit sein oder Muster verwenden. Ein Beispiel:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   Die Reihenfolge der Pfade ist irrelevant, alle Pfade werden geprüft und alle Vorlagen werden abgerufen.

   >[!NOTE]
   >
   >Wenn die Variable **Zulässige Vorlagen** leer ist, wird der Baum aufgerissen, bis ein Wert/eine Liste gefunden wird.
   >
   >
   >Weitere Informationen finden Sie unter [Vorlagenverfügbarkeit](/help/sites-developing/templates.md#template-availability) – die Prinzipien für zugelassene Vorlagen bleiben gleich.

1. Klicken Sie auf **Speichern**, um die Änderungen an den Seiteneigenschaften zu speichern.

>[!NOTE]
>
>Häufig werden die zugelassenen Vorlagen für Ihre gesamte Site vordefiniert, wenn diese eingerichtet wird.

### Veröffentlichen einer Vorlage – Vorlagenautor {#publishing-a-template-template-author}

Da auf die Vorlage verwiesen wird, wenn eine Seite dargestellt wird, muss die voll konfigurierte Vorlage veröffentlicht werden, damit sie in der Veröffentlichungsumgebung verfügbar ist.

1. Wählen Sie in der **Vorlagenkonsole** eine Vorlage aus.
1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Assistenten zu öffnen.
1. Wählen Sie die **Inhaltsrichtlinien**, die mit veröffentlicht werden sollen.

1. Wählen Sie **Veröffentlichen** in der Symbolleiste, um den Vorgang abzuschließen.

## Bearbeiten von Vorlagen   – Vorlagenautoren {#editing-templates-template-authors}

Beim Erstellen oder Bearbeiten einer Vorlage können verschiedene Aspekte definiert werden. Das Bearbeiten von Vorlagen ähnelt dem Erstellen von Seiten.

Die folgenden Aspekte einer Vorlage können bearbeitet werden:

* [Struktur](#editingatemplatestructure)

  Komponenten, die hier hinzugefügt werden, können von den Seitenautoren nicht von den resultierenden Seiten verschoben/entfernt werden. Wenn Seitenautoren in der Lage sein sollen, neue Komponenten zu resultierenden Seiten hinzuzufügen und daraus zu entfernen, müssen Sie der Vorlage ein Absatzsystem hinzufügen.

  Wenn Komponenten gesperrt sind, können Sie Inhalte hinzufügen, die von Seitenautorinnen bzw. -autoren nicht bearbeitet werden können. Sie können Komponenten entsperren, damit Sie [Anfänglicher Inhalt](#editingatemplateinitialcontent).

  >[!NOTE]
  >
  >Im Strukturmodus können Komponenten, die einer entsperrten Komponente übergeordnet sind, nicht verschoben, ausgeschnitten oder gelöscht werden.

* [Anfänglicher Inhalt](#editingatemplateinitialcontent)

  Wenn eine Komponente entsperrt wurde, können Sie den anfänglichen Inhalt definieren, der auf die resultierenden Seiten kopiert wird, die aus der Vorlage erstellt werden. Diese entsperrten Komponenten können auf den resultierenden Seiten bearbeitet werden.

  >[!NOTE]
  >
  >In **Anfänglicher Inhalt** -Modus und auf den resultierenden Seiten können alle entsperrten Komponenten, die über ein barrierefreies übergeordnetes Element verfügen (d. h. Komponenten in einem Layout-Container), gelöscht werden.

* [Layout](#editingatemplatelayout)

  Hier können Sie das Vorlagenlayout für die erforderlichen Geräteformate vordefinieren. Der Modus **Layout** für das Erstellen von Vorlagen bietet dieselben Funktionen wie der Modus [**Layout** für das Erstellen von Seiten](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode).

* [Seitenrichtlinien](#editingatemplatepagepolicies)

  Unter „Seitenrichtlinien“ können Sie vordefinierte Seitenrichtlinien für die Seite verknüpfen. Diese Seitenrichtlinien definieren die verschiedenen Design-Konfigurationen.

* [Stile](/help/sites-authoring/style-system.md)

  Das Stilsystem ermöglicht es einem Vorlagenautor, in der Inhaltsrichtlinie für Komponenten Stilklassen festzulegen, die ein Inhaltsautor später bei der Bearbeitung der Komponente auf einer Seite auswählen kann. Diese Stile können alternative visuelle Varianten einer Komponente sein, um das Verfahren flexibler zu gestalten.

  Weitere Informationen finden Sie in der [Dokumentation für das Stilsystem](/help/sites-authoring/style-system.md).

Die **Modus** Mit der Auswahl in der Symbolleiste können Sie den entsprechenden Aspekt der Vorlage auswählen und bearbeiten:

* [Struktur](#editingatemplatestructure)
* [Anfänglicher Inhalt](#editingatemplateinitialcontent)
* [Layout](#editingatemplatelayout)

![chlimage_1-133](assets/chlimage_1-133.png)

Während **Seitenrichtlinie** -Option auf **Seiteninformationen** Menü [die erforderlichen Seitenrichtlinien auswählen](#editingatemplatepagepolicies):

![screen_shot_2018-03-23at120604](assets/screen_shot_2018-03-23at120604.png)

>[!CAUTION]
>
>Wenn ein Autor beginnt, eine bereits aktivierte Vorlage zu bearbeiten, wird eine Warnung angezeigt. Diese dient dazu, den Benutzer zu informieren, dass die Vorlage referenziert wird und damit sämtliche Änderungen, die die Vorlage referenzierenden Seiten beeinträchtigen könnten.

### Bearbeiten einer Vorlage – Struktur – Vorlagenautor {#editing-a-template-structure-template-author}

Im **Strukturmodus** definieren Sie Komponenten und Inhalte für Ihre Vorlage sowie Richtlinien für die Vorlage und die zugehörigen Komponenten.

* Komponenten, die in der Vorlagenstruktur definiert sind, können auf einer resultierenden Seite nicht verschoben oder von dort gelöscht werden.
* Wenn Sie möchten, dass Seitenautorinnen und -autoren Komponenten hinzufügen und entfernen können, fügen Sie der Vorlage ein Absatzsystem hinzu.
* Komponenten können entsperrt und erneut gesperrt werden, damit Sie [anfänglicher Inhalt](#editingatemplateinitialcontent).

* Die Design-Richtlinien für die Komponenten und die Seite werden definiert.

![screen_shot_2018-03-23at120819](assets/screen_shot_2018-03-23at120819.png)

In **Struktur** -Modus des Vorlageneditors:

* **Komponenten hinzufügen**

  Es gibt mehrere Möglichkeiten, Komponenten zur Vorlage hinzuzufügen:

   * Über den **Komponenten**-Browser im Seitenbereich.
   * über die Option **Komponente einfügen** (**Plussymbol**) in der Symbolleiste von Komponenten, die bereits in der Vorlage sind, oder dem Feld **Kompenenten hierher ziehen**

   * Durch Ziehen eines Assets (aus dem **Assets**-Browser im Seitenbereich) direkt auf die Vorlage wird die entsprechende Komponente an Ort und Stelle erzeugt.

  Nach dem Hinzufügen wird jede Komponente mit folgenden Elementen markiert:

   * Einem Rand
   * Einer Markierung, die den Komponententyp zeigt
   * Einer Markierung, die anzeigt, ob die Komponente entsperrt ist

  >[!NOTE]
  >
  >Wenn Sie eine vordefinierte **Titelkomponente** zur Vorlage hinzufügen, enthält sie den Standardtext **Struktur**.
  >
  >
  >Wenn Sie diesen ändern und Ihren eigenen Text einfügen, wird dieser aktualisierte Text verwendet, wenn eine Seite aus der Vorlage erstellt wird.
  >
  >
  >Wenn Sie den Standardtext (Struktur) nicht ändern, wird der Titel standardmäßig mit dem Namen der nachfolgenden Seite benannt.

  >[!NOTE]
  >
  >Das Hinzufügen von Komponenten und Assets zu einer Vorlage ist zwar nicht dasselbe wie das [Erstellen von Seiten](/help/sites-authoring/editing-content.md), es gibt aber durchaus einige Ähnlichkeiten.

* **Komponenten-Aktionen**

  Nehmen Sie Aktionen für die Komponenten vor, nachdem sie der Vorlage hinzugefügt wurden. Jede einzelne Instanz verfügt über eine Symbolleiste, über die Sie auf die verfügbaren Aktionen zugreifen können. Die Symbolleiste hängt vom Komponententyp ab.

  ![screen_shot_2018-03-23at120909](assets/screen_shot_2018-03-23at120909.png)

  Sie kann auch von durchgeführten Aktionen abhängig sein. Wenn z. B. eine Richtlinie mit der Komponente verbunden wurde, ist das Design-Konfigurationssymbol verfügbar.

* **Bearbeiten und Konfigurieren**

  Mit diesen zwei Aktionen können Sie Inhalte zu Ihren Komponenten hinzufügen.

* **Rand für die Anzeige der Struktur**

  Wenn Sie im **Struktur**-Modus arbeiten, zeigt eine orangefarbene Umrandung die aktuell ausgewählte Komponente an. Außerdem zeigt eine gepunktete Linie die übergeordnete Komponente an.

  Im Screenshot weiter unten ist beispielsweise die Komponente **Text** in einem **Layout-Container** ausgewählt (responsivegrid).

  ![chlimage_1-134](assets/chlimage_1-134.png)

* **Richtlinien und Eigenschaften (Allgemein)**

  Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

  Erstellen Sie für eine Komponente eine Inhaltsrichtlinie oder wählen Sie eine vorhandene. Auf diese Weise können Sie die Designdetails definieren.

  ![chlimage_1-135](assets/chlimage_1-135.png) ![chlimage_1-136](assets/chlimage_1-136.png)

  Das Konfigurationsfenster ist in zwei Hälften geteilt.

   * Auf der linken Seite des Dialogfelds können Sie unter **Richtlinie** eine vorhandene Richtlinie auswählen.
   * Auf der rechten Seite des Dialogfelds können Sie unter **Eigenschaften** die für den Komponententyp spezifischen Eigenschaften festlegen.

  Die verfügbaren Eigenschaften hängen von der ausgewählten Komponente ab. Beispielsweise definieren die Eigenschaften für eine Textkomponente die Optionen zum Kopieren und Einfügen, Formatierungsoptionen und den Absatzstil unter anderen Optionen.

  ***Richtlinie***

  Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

  Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird.

  ![chlimage_1-137](assets/chlimage_1-137.png)

  Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

  ![chlimage_1-138](assets/chlimage_1-138.png)

  Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Name der kopierten Richtlinie ist.

  ![chlimage_1-139](assets/chlimage_1-139.png)

  Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.

  Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

  ![chlimage_1-140](assets/chlimage_1-140.png)

  >[!NOTE]
  >
  >Wenn mehrere Komponenten des gleichen Typs als anfänglicher Inhalt hinzugefügt werden, gilt für alle Komponenten dieselbe Richtlinie. Dies entspricht der Einschränkung für statische Vorlagen im [**Designmodus**](/help/sites-authoring/default-components-designmode.md).

  ***Eigenschaften***

  Unter der Überschrift **Eigenschaften** können Sie die Einstellungen der Komponente festlegen. Die Überschrift hat zwei Registerkarten:

   * Allgemein
   * Funktionen

  *Allgemein*

  Auf der Registerkarte **Allgemein** sind die wichtigsten Einstellungen der Komponente definiert.

  Beispielsweise kann die zulässige Breite für eine Bildkomponente zusammen mit der Aktivierung des „Lazy Loading“ (Langsames Laden) definiert werden.

  Wenn eine Einstellung mehrere Konfigurationen erlaubt, klicken oder tippen Sie auf die Schaltfläche **Hinzufügen**, um eine weitere Konfiguration hinzuzufügen.

  ![chlimage_1-141](assets/chlimage_1-141.png)

  Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**, die sich rechts neben der Konfiguration befindet.

  Um eine Konfiguration zu entfernen, klicken oder tippen Sie auf die Schaltfläche **Löschen**.

  ![chlimage_1-142](assets/chlimage_1-142.png)

  *Funktionen*

  Die **Funktionen** -Tab können Sie zusätzliche Funktionen der Komponente aktivieren oder deaktivieren.

  Beispielsweise können Sie für eine Bildkomponente die Zuschneideproportionen, die zulässigen Bildausrichtungen und die Möglichkeit von Uploads definieren.

  ![chlimage_1-143](assets/chlimage_1-143.png)

  >[!CAUTION]
  >
  >Beachten Sie, dass in AEM die Beschneidungsverhältnisse als **Höhe/Breite** definiert sind. Dies unterscheidet sich von der herkömmlichen Definition als Breite/Höhe und erfolgt aus Gründen der Legacy-Kompatibilität. Benutzer, die Seiten erstellen, bemerken keinen Unterschied, vorausgesetzt, dass Sie den **Namen** klar definieren, da dieser auf der Benutzeroberfläche angezeigt wird.

  >[!NOTE]
  >
  >[Inhaltsrichtlinien für Komponenten, die den Rich-Text-Editor implementieren](/help/sites-administering/rich-text-editor.md#main-pars-header-206036638), können nur für Optionen definiert werden, die vom RTE über die UI-Einstellungen bereitgestellt werden.   [](/help/sites-administering/rich-text-editor.md#main-pars_header_206036638) [](/help/sites-administering/rich-text-editor.md#main-pars_header_206036638)

* **Richtlinien und Eigenschaften (Layout-Container)**

  Die Richtlinien- und Eigenschafteneinstellungen eines Layout-Containers ähneln der allgemeinen Verwendung, allerdings mit einigen Unterschieden.

  >[!NOTE]
  >
  >Die Konfiguration einer Richtlinie ist für Container-Komponenten obligatorisch, da sie es Ihnen ermöglicht, Komponenten zu definieren, die im Container verfügbar sein werden.

  Das Konfigurationsfenster ist in zwei Bereiche unterteilt, ebenso wie in der allgemeinen Nutzung des Fensters.

  ***Richtlinie***

  Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

  Unter **Richtlinie** können Sie eine vorhandene Richtlinie auswählen, die über das Dropdown-Menü auf die Komponente angewendet wird. Dies funktioniert ebenso wie bei der allgemeinen Verwendung des Fensters.

  ***Eigenschaften***

  Unter der Überschrift **Eigenschaften** können Sie auswählen, welche Komponenten für den Layout-Container zur Verfügung stehen, und deren Einstellungen festlegen. Die Überschrift hat drei Registerkarten:

   * Zugelassene Komponenten
   * Standardkomponenten
   * Responsive Einstellungen

  *Zugelassene Komponenten*

  Auf der Registerkarte **Zugelassene Komponenten** legen Sie fest, welche Komponenten für den Layout-Container verfügbar sind.

   * Die Komponenten werden nach Komponentengruppen gruppiert, die sich erweitern und reduzieren lassen.
   * Es kann eine ganze Gruppe ausgewählt werden, indem das Kontrollkästchen für den Gruppennamen aktiviert wird. Um die Auswahl aller Elemente wieder aufzuheben, deaktivieren Sie das Kontrollkästchen.
   * Ein Minuszeichen zeigt an, dass mindestens eines, aber nicht alle Elemente in einer Gruppe ausgewählt sind.
   * Es steht eine Suchfunktion zur Verfügung, um nach einer Komponente anhand ihres Namens zu filtern.
   * Die rechts neben dem Namen der Komponentengruppe aufgeführten Zahlen geben die Gesamtzahl der ausgewählten Komponenten in diesen Gruppen an, unabhängig vom Filter.

  ![chlimage_1-144](assets/chlimage_1-144.png)

  *Standardkomponenten*

  Auf der Registerkarte **Standardkomponenten** legen Sie fest, welche Komponenten automatisch mit bestimmten Medientypen verknüpft werden, damit AEM beim Ziehen eines Assets aus dem Asset-Browser weiß, mit welcher Komponente es verknüpft werden soll. Beachten Sie, dass für diese Konfiguration nur Komponenten mit Ablageflächen verfügbar sind.

  Klicken oder tippen Sie auf **Zuordnung hinzufügen**, um eine völlig neue Komponente und MIME-Typzuordnung hinzuzufügen.

  Wählen Sie eine Komponente in der Liste aus und tippen/klicken Sie auf **Typ hinzufügen**, um einer bereits zugeordneten Komponente einen zusätzlichen MIME-Typ hinzuzufügen. Klicken Sie auf das Symbol **Löschen**, um einen MIME-Typ zu entfernen.

  ![chlimage_1-145](assets/chlimage_1-145.png)

  *Responsive Einstellungen*

  Auf der Registerkarte **Responsive Einstellungen** können Sie die Anzahl der Spalten im resultierenden Raster des Layout-Containers konfigurieren.

* **Komponenten entsperren/sperren**

  Komponenten werden entsperrt/gesperrt, um festzulegen, ob der Inhalt im Modus **Anfänglicher Inhalt** geändert werden darf.

  Wenn eine Komponente entsperrt wurde:

   * Wird am Rand ein offenes Vorhängeschloss angezeigt.
   * Die Komponenten-Symbolleiste wird entsprechend angepasst.
   * Bereits eingegebene Inhalte werden nicht mehr im **Strukturmodus** angezeigt.

      * Bereits eingegebener Inhalt wird als anfänglicher Inhalt betrachtet und ist nur im Modus **Anfänglicher Inhalt** sichtbar.

   * Die Komponenten, die der entsperrten Komponente übergeordnet sind, können nicht verschoben, ausgeschnitten oder gelöscht werden.

  ![chlimage_1-146](assets/chlimage_1-146.png)

  Dies umfasst das Entsperren von Containerkomponenten, sodass weitere Komponenten hinzugefügt werden können, entweder im **Ursprüngliche Inhalte** oder auf den daraus resultierenden Seiten. Wenn Sie dem Container bereits Komponenten/Inhalte hinzugefügt haben, bevor Sie ihn entsperren, werden diese nicht mehr angezeigt, wenn Sie **Struktur** -Modus, sie werden jedoch in **Anfänglicher Inhalt** -Modus. Im **Strukturmodus** werden nur die Container-Komponente selbst und die zugehörige Liste der **zugelassenen Komponenten** angezeigt.

  ![chlimage_1-147](assets/chlimage_1-147.png)

  Der Layout-Container wächst nicht an, um die Liste der zulässigen Komponenten aufzunehmen. Auf diese Weise wird Speicherplatz gespart. Stattdessen wird der Container zu einer scrollbaren Liste.

  Komponenten, die konfigurierbar sind, werden mit einem Symbol für **Richtlinien** angezeigt, auf das Sie tippen/klicken können, um die Richtlinie und Eigenschaften dieser Komponente zu bearbeiten.

  ![chlimage_1-148](assets/chlimage_1-148.png)

* **Beziehung zu vorhandenen Seiten**

  Auf diesen Seiten werden die Änderungen an der Vorlage widergespiegelt, wenn die Struktur aktualisiert wird, nachdem die Seiten auf der Grundlage der Vorlage erstellt wurden. In der Symbolleiste wird eine Warnung mit einem Bestätigungsdialog angezeigt, um Sie an diese Tatsache zu erinnern.

  ![chlimage_1-149](assets/chlimage_1-149.png)

### Bearbeiten einer Vorlage – Anfänglicher Inhalt – Autor {#editing-a-template-initial-content-author}

Der Modus **Anfänglicher Inhalt** wird für definierten Inhalt verwendet, der angezeigt wird, wenn eine Seite anfänglich auf der Grundlage einer Vorlage erstellt wird. Der anfängliche Inhalt kann dann von Seitenautorinnen bzw. -autoren bearbeitet werden.

Obwohl der gesamte Inhalt, der im Modus **Struktur** erstellt wird, im Modus **Anfänglicher Inhalt** sichtbar ist, können nur entsperrte Komponenten ausgewählt und bearbeitet werden.

>[!NOTE]
>
>Der Modus **Anfänglicher Inhalt** kann als Bearbeitungsmodus für Seiten betrachtet werden, die mit dieser Vorlage erstellt werden. Daher sind Richtlinien nicht im Modus **Anfänglicher Inhalt**, sondern im [**Strukturmodus** definiert](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

* Entsperrte Komponenten, die zur Bearbeitung verfügbar sind, sind markiert. Wenn ausgewählt, wird ein blauer Rahmen angezeigt:

  ![chlimage_1-150](assets/chlimage_1-150.png)

* Entsperrte Komponenten haben eine Symbolleiste, mit der Sie den Inhalt bearbeiten und konfigurieren können:

  ![chlimage_1-151](assets/chlimage_1-151.png)

* Wenn eine Container-Komponente (im Modus **Struktur**) entsperrt wurde, können Sie neue Komponenten zum Container hinzufügen (im Modus **Anfänglicher Inhalt**). Komponenten, die im Modus **Anfänglicher Inhalt** hinzugefügt werden, können auf resultierende Seiten verschoben oder von diesen gelöscht werden.

  Sie können Komponenten über den Bereich **Komponenten hierher ziehen** oder mithilfe der Option **Neue Komponente einfügen** in der Symbolleiste des jeweiligen Containers hinzufügen.

  ![chlimage_1-152](assets/chlimage_1-152.png) ![chlimage_1-153](assets/chlimage_1-153.png)

* Wenn der anfängliche Inhalt der Vorlage aktualisiert wird, nachdem Seiten auf der Grundlage der Vorlage erstellt wurden, wirken sich die Änderungen am anfänglichen Inhalt der Vorlage nicht auf diese Seiten aus.

>[!NOTE]
>
>Der ursprüngliche Inhalt dient zum Vorbereiten von Komponenten und dem Seitenlayout, die als Ausgangspunkt für die Erstellung des Inhalts dienen. Dies soll nicht der eigentliche Inhalt sein, der unverändert bleibt. Aus diesem Grund können anfängliche Inhalte nicht übersetzt werden.
>
>Wenn Sie in Ihre Vorlage übersetzbaren Text aufnehmen möchten, z. B. in Kopf- oder Fußzeilen, können Sie die [Lokalisierungsfunktionen der Hauptkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=de) verwenden.

### Bearbeiten einer Vorlage – Layout – Vorlagenautor {#editing-a-template-layout-template-author}

Sie können das Vorlagen-Layout für verschiedene Geräte definieren. [Responsives Layout](/help/sites-authoring/responsive-layout.md) funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.

>[!NOTE]
>
>Änderungen am Layout werden im Modus **Anfänglicher Inhalt** widergespiegelt, doch im **Strukturmodus** sind keine Änderungen zu sehen.

![chlimage_1-154](assets/chlimage_1-154.png)

### Bearbeiten einer Vorlage – Seitendesign – Vorlagenautor/Entwickler {#editing-a-template-page-design-template-author-developer}

Der Seitenentwurf, einschließlich der erforderlichen Client-seitigen Bibliotheken und Seitenrichtlinien, wird unter der Option **Seitendesign** im Menü **Seiteninformationen** beibehalten.

So greifen Sie auf das Dialogfeld **Seitendesign** zu:

1. Wählen Sie im **Vorlagen-Editor** in der Symbolleiste die Option **Seiteninformationen** und anschließend **Seitendesign**, um das Dialogfeld zu öffnen.
1. Die **Seitendesign** wird geöffnet und ist in zwei Abschnitte unterteilt:

   * Die linke Hälfte definiert die [Seitenrichtlinien](/help/sites-authoring/templates.md#page-policies).
   * Die rechte Hälfte definiert die [Seiteneigenschaften](/help/sites-authoring/templates.md#page-properties).

   ![chlimage_1-155](assets/chlimage_1-155.png)

#### Seitenrichtlinien {#page-policies}

Sie können eine Inhaltsrichtlinie auf die Vorlage oder resultierende Seiten anwenden. So wird die Inhaltsrichtlinie für das Hauptabsatzsystem auf der Seite definiert.

![chlimage_1-156](assets/chlimage_1-156.png)

* Sie können eine vorhandene Richtlinie für die Seite im Dropdown-Menü **Richtlinie auswählen** auswählen.

  ![chlimage_1-157](assets/chlimage_1-157.png)

  Sie können eine neue Richtlinie hinzufügen, indem Sie auf die Schaltfläche „Hinzufügen“ klicken, die sich neben dem Dropdown-Menü **Richtlinie auswählen** befindet. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden.

  ![chlimage_1-158](assets/chlimage_1-158.png)

  Die im Dropdown-Menü **Richtlinie auswählen** ausgewählte vorhandene Richtlinie kann mithilfe der Schaltfläche „Kopieren“, die sich neben dem Dropdown-Menü befindet, kopiert werden. Dann muss ein neuer Name in das Feld **Richtlinienname** eingegeben werden. Standardmäßig erhält die kopierte Richtlinie den Namen **Kopie von X**, wobei X der Name der kopierten Richtlinie ist.

  ![chlimage_1-159](assets/chlimage_1-159.png)

* Geben Sie im Feld **Richtlinienname** einen Namen für die Richtlinie an. Eine Richtlinie muss einen Namen tragen, damit sie mühelos im Dropdown-Menü **Richtlinie auswählen** ausgewählt werden kann.

  ![chlimage_1-160](assets/chlimage_1-160.png)

* Eine Beschreibung der Richtlinie im Feld **Richtlinienbeschreibung** ist optional.
* Im Abschnitt **Andere Vorlagen, die ebenfalls die ausgewählte Richtlinie verwenden** ist leicht ersichtlich, welche anderen Vorlagen die Richtlinie verwenden, die in der Dropdown-Liste **Richtlinie auswählen** ausgewählt wurde.

  ![chlimage_1-161](assets/chlimage_1-161.png)

#### Seiteneigenschaften {#page-properties}

Mithilfe der Seiteneigenschaften können Sie die erforderlichen Client-seitigen Bibliotheken definieren, indem Sie das Dialogfeld **Seiten-Design** verwenden. Diese Client-seitigen Bibliotheken enthalten Stylesheets und JavaScript, die zusammen mit der Vorlage und den mit der Vorlage erstellten Seiten geladen werden.

![chlimage_1-162](assets/chlimage_1-162.png)

* Geben Sie die Client-seitigen Bibliotheken an, die auf die mit dieser Vorlage erstellten Seiten angewendet werden sollen. Eingabe des Namens einer Bibliothek in das Textfeld im Bereich **Client-Bibliotheken**.

  ![chlimage_1-163](assets/chlimage_1-163.png)

* Wenn mehrere Bibliotheken erforderlich sind, klicken Sie auf die Schaltfläche „Hinzufügen“, um ein zusätzliches Textfeld für den Namen der Bibliothek hinzuzufügen.

  ![chlimage_1-164](assets/chlimage_1-164.png)

  Fügen Sie für Ihre Client-seitigen Bibliotheken so viele Textfelder wie nötig hinzu.

  ![chlimage_1-165](assets/chlimage_1-165.png)

* Definieren Sie bei Bedarf die relative Position der Bibliotheken, indem Sie die Felder mithilfe des Ziehpunkts ziehen.

  ![chlimage_1-166](assets/chlimage_1-166.png)

>[!NOTE]
>
>Der Vorlagenautor kann zwar die Seitenrichtlinie in der Vorlage angeben, muss jedoch vom Entwickler Details zu den entsprechenden clientseitigen Bibliotheken erhalten.

### Bearbeiten einer Vorlage – Anfängliche Seiteneigenschaften – Autor {#editing-a-template-initial-page-properties-author}

Mit der Option **Anfängliche Seiteneigenschaften** können Sie die anfänglichen [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) definieren, die bei der Erstellung einer neuen Seite gelten sollen.

1. Wählen Sie im Vorlageneditor **Seiteninformationen** aus der Symbolleiste und anschließend **Anfängliche Seiteneigenschaften**, um das Dialogfeld zu öffnen.

1. Im Dialogfeld können Sie Eigenschaften definieren, die für Seiten gelten sollen, die mit dieser Vorlage erstellt werden.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bestätigen Sie Ihre Definitionen mit **Fertig**.

## Best Practices {#best-practices}

Beachten Sie beim Erstellen von Vorlagen Folgendes:

1. Die Auswirkungen von Änderungen an der Vorlage, sobald Seiten aus dieser Vorlage erstellt wurden.

   Im Folgenden finden Sie eine Liste der verschiedenen Vorgänge, die für Vorlagen möglich sind, sowie deren Auswirkungen auf die daraus erstellten Seiten:

   * Änderungen an der Struktur:

      * Diese werden sofort auf die resultierenden Seiten angewendet.
      * Die geänderte Vorlage muss erst veröffentlicht werden, damit Besuchende die Änderungen sehen können.

   * Änderungen an Inhaltsrichtlinien und Design-Konfigurationen:

      * Diese gelten sofort für die resultierenden Seiten.
      * Die Änderungen müssen veröffentlicht werden, damit Besuchende die Änderungen sehen können.

   * Änderungen am anfänglichen Inhalt:

      * Diese gelten nur für Seiten, die nach den Änderungen an der Vorlage erstellt wurden.

   * Änderungen am Layout sind von der Zugehörigkeit der modifizierten Komponente abhängig:

      * Nur Struktur – wird sofort angewendet
      * Enthält anfänglichen Inhalt – wird nur auf Seiten übernommen, die nach der Änderung erstellt werden

   Besondere Vorsicht ist erforderlich bei:

   * Sperren oder Entsperren von Komponenten in aktivierten Vorlagen.
   * Dies kann Nebeneffekte haben, da die Komponenten bereits von vorhandenen Seiten verwendet werden können. In der Regel gilt Folgendes:

      * Das Entsperren von Komponenten (die gesperrt waren) fehlt auf vorhandenen Seiten.
      * Wenn Komponenten (die bearbeitbar waren) gesperrt werden, wird der entsprechende Inhalt auf den Seiten ausgeblendet.

   >[!NOTE]
   >
   >AEM gibt ausdrückliche Warnhinweise aus, wenn der Sperrstatus von Komponenten in Vorlagen geändert wird, bei denen es sich nicht mehr um Entwürfe handelt.

1. [Erstellen Sie Ihre eigenen Ordner](#creatingatemplatefolderdeveloper) für Ihre Site-spezifischen Vorlagen.
1. [Veröffentlichen Sie Ihre Vorlagen](#publishingatemplateauthor) von der **Vorlagenkonsole** aus.
