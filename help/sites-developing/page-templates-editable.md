---
title: Bearbeitbare Seitenvorlagen
description: Es wurden bearbeitbare Vorlagen eingeführt, die es auch Nicht-Entwickelnden ermöglichen, Vorlagen zu erstellen und zu bearbeiten, Vorlagen bereitzustellen, die eine dynamische Verbindung zu allen daraus erstellten Seiten beibehalten, und die Seitenkomponente allgemeiner zu gestalten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: dcb66b6d-d731-493e-8936-12d529f6cbde
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3186'
ht-degree: 99%

---

# Bearbeitbare Seitenvorlagen {#page-templates-editable}

Bearbeitbare Vorlagen wurden eingeführt:

* Sie sollen spezialisierten Autorinnen und Autoren [das Erstellen und Bearbeiten von Vorlagen](/help/sites-authoring/templates.md) ermöglichen.

   * Diese spezialisierten Autoren werden als **Vorlagenautoren** bezeichnet.
   * Vorlagenautoren müssen Mitglieder der Gruppe `template-authors` sein.

* Es werden Vorlagen bereitgestellt, die eine dynamische Verbindung zu allen damit erstellten Seiten beibehalten. Dadurch wird sichergestellt, dass alle Änderungen an der Vorlage auf den Seiten widergespiegelt werden.
* Die Seitenkomponente wird allgemeiner gestaltet, damit die Seitenkernkomponente ohne Anpassung verwendet werden kann.

Mit bearbeitbaren Vorlagen werden die Aspekte, die eine Seite bilden, innerhalb von Komponenten isoliert. Sie können die erforderlichen Kombinationen von Komponenten in einer Benutzeroberfläche konfigurieren, sodass Sie nicht für jede Seitenvariante eine neue Seitenkomponente entwickeln müssen.

>[!NOTE]
>
>[Statische Vorlagen](/help/sites-developing/page-templates-static.md) sind ebenfalls verfügbar.

Dieses Dokument:

* Bietet einen Überblick über das Erstellen bearbeitbarer Vorlagen

   * Umfassende Informationen finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

* Beschreibt die zum Erstellen bearbeitbarer Vorlagen erforderlichen Aufgaben für Admin-/Entwicklerpersonal
* Beschreibt die technischen Grundlagen bearbeitbarer Vorlagen

Bei den in diesem Dokument beschriebenen Schritten wird vorausgesetzt, dass Sie bereits mit dem Erstellen und Bearbeiten von Vorlagen vertraut sind. Weitere Informationen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) für Autoren, das detailliert beschreibt, welche Funktionen Vorlagenautoren mit bearbeitbaren Vorlagen zur Verfügung stehen.

>[!NOTE]
>
>Das folgende Tutorial kann auch für das Einrichten einer bearbeitbaren Seitenvorlage in einem neuen Projekt von Interesse sein:
>[Erste Schritte mit AEM Sites Teil 2 – Erstellen einer Basisseite und Vorlage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/pages-templates.html)

## Erstellen neuer Vorlagen {#creating-a-new-template}

Bearbeitbare Vorlagen werden von Vorlagenautoren in erster Linie mit der [Vorlagenkonsole und dem Vorlagen-Editor](/help/sites-authoring/templates.md) erstellt. In diesem Abschnitt finden Sie einen Überblick über diesen Prozess, der anschließend aus technischer Perspektive beleuchtet wird.

Informationen zur Verwendung bearbeitbarer Vorlagen in einem AEM-Projekt finden Sie unter [Erstellen eines AEM-Projekts mit Lazybones](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/create-aem-project-structure-using-lazybones/m-p/186478).

Gehen Sie zum Erstellen einer bearbeitbaren Vorlage wie folgt vor:

1. Erstellen Sie einen [Ordner für die Vorlagen](#template-folders). Dieser Ordner ist nicht obligatorisch, wird jedoch als Best Practice empfohlen.
1. Wählen Sie einen [Vorlagentyp](#template-type) aus. Dieser wird kopiert, um die [Vorlagendefinition](#template-definitions) zu erstellen.

   >[!NOTE]
   >
   >Eine Auswahl von Vorlagentypen ist standardmäßig verfügbar. Sie können auch [eigene Site-spezifische Vorlagentypen erstellen](/help/sites-developing/page-templates-editable.md#creating-template-types), falls erforderlich.

1. Konfigurieren Sie die Struktur, die Inhaltsrichtlinien, den anfänglichen Inhalt und das Layout der neuen Vorlage.

   **Struktur**

   * Die Struktur ermöglicht die Definition von Komponenten und Inhalten für Ihre Vorlage.
   * Komponenten, die in der Vorlagenstruktur definiert sind, können nicht auf einer resultierenden Seite verschoben oder von den resultierenden Seiten gelöscht werden.

      * Wenn Sie eine Vorlage in einem benutzerdefinierten Ordner außerhalb des `We.Retail`-Beispielinhalts erstellen, können Sie Foundation-Komponenten wählen oder [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html?lang=de) verwenden.

   * Wenn Sie möchten, dass Seitenautorinnen und -autoren Komponenten hinzufügen und entfernen können, fügen Sie der Vorlage ein Absatzsystem hinzu.
   * Komponenten lassen sich entsperren und erneut sperren, damit Sie den anfänglichen Inhalt definieren können.

   Einzelheiten dazu, wie Vorlagenautorinnen und -autoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Technische Details zur Struktur werden in diesem Dokument unter [Struktur](/help/sites-developing/page-templates-editable.md#structure) erläutert.

   **Richtlinien**

   * Die Richtlinien für Inhalte definieren die Design-Eigenschaften einer Komponente.

      * Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen.

   * Diese Richtlinien sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).

   Einzelheiten dazu, wie Vorlagenautorinnen und -autoren Richtlinien definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Technische Details zu Richtlinien werden in diesem Dokument unter [Inhaltsrichtlinien](/help/sites-developing/page-templates-editable.md#content-policies) erläutert.

   **Anfänglicher Inhalt**

   * Der anfängliche Inhalt definiert den Inhalt, der angezeigt wird, wenn eine Seite anfänglich auf Grundlage einer Vorlage erstellt wird.
   * Der anfängliche Inhalt kann dann bearbeitet werden.

   Einzelheiten dazu, wie Vorlagenautoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-initial-content-author).

   Technische Details zum anfänglichen Inhalt finden Sie unter [Anfänglicher Inhalt](/help/sites-developing/page-templates-editable.md#initial-content) in diesem Dokument.

   **Layout**

   * Sie können das Vorlagen-Layout für verschiedene Geräte definieren.
   * Responsives Layout funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.

   Einzelheiten dazu, wie Vorlagenautorinnen und -autoren Vorlagen-Layouts definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-layout-template-author).

   Technische Details zum Vorlagen-Layout finden Sie unter [Layout](/help/sites-developing/page-templates-editable.md#layout) in diesem Dokument.

1. Aktivieren Sie die Vorlage und lassen Sie sie dann für bestimmte Inhaltsstrukturen zu.

   * Eine Vorlage kann aktiviert oder deaktiviert werden, um sie für Vorlagenautorinnen und -autoren verfügbar bzw. nicht verfügbar zu machen.
   * Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.

   Einzelheiten dazu, wie Vorlagen aktiviert werden können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author).

   Technische Details zum Aktivieren von Vorlagen werden in diesem Dokument unter [Aktivieren und Zulassen von Vorlagen](/help/sites-developing/page-templates-editable.md#enabling-and-allowing-a-template-for-use) erläutert.

1. Verwenden Sie sie, um Inhaltsseiten zu erstellen.

   * Wenn Sie eine Vorlage zum Erstellen einer Seite verwenden, ist kein Unterschied zwischen statischen und bearbeitbaren Vorlagen ersichtlich.
   * Für die Seitenautoren ist der Prozess transparent.

   Einzelheiten dazu, wie Seitenautoren Vorlagen zum Erstellen von Seiten verwenden können, finden Sie unter [Erstellen und Organisieren von Seiten](/help/sites-authoring/managing-pages.md#templates).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Resultierende Inhaltsseiten](/help/sites-developing/page-templates-editable.md#resultant-content-pages) erläutert.

>[!TIP]
>
>Geben Sie in eine Vorlage nie Informationen ein, die internationalisiert werden müssen. Für die Internationalisierung werden die [Lokalisierungsfunktionen der Hauptkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html?lang=de) empfohlen.

>[!NOTE]
>
>Vorlagen sind leistungsstarke Tools zur Optimierung des Seitenerstellungs-Workflows. Allerdings können zu viele Vorlagen die Autoren überwältigen und das Erstellen von Seiten unübersichtlich machen. Eine gute Faustregel ist, die Anzahl der Vorlagen unter 100 zu halten.
>
>Adobe empfiehlt, aufgrund möglicher Leistungsauswirkungen nicht mehr als 1.000 Vorlagen zu verwenden.

>[!NOTE]
>
>Die Client-Bibliothek des Editors setzt voraus, dass der `cq.shared`-Namespace in Inhaltsseiten vorhanden ist. Wenn er nicht vorhanden ist, tritt der JavaScript-Fehler `Uncaught TypeError: Cannot read property 'shared' of undefined` auf.
>
>Alle Beispielinhaltsseiten enthalten `cq.shared`, sodass jeglicher darauf basierender Inhalt automatisch `cq.shared` umfasst. Wenn Sie sich jedoch ganz neue eigene Inhaltsseiten erstellen möchten, die nicht auf Beispielinhalt basieren, müssen Sie sicherstellen, dass Sie den Namespace `cq.shared` einbinden.
>
>Weitere Informationen finden Sie unter [Verwendung Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md).

## Vorlagenordner {#template-folders}

Zum Organisieren Ihrer Vorlagen können Sie die folgenden Ordner verwenden:

* **global**
* Site-spezifische Ordner 
Die Site-spezifischen Ordner, die Sie zum Organisieren Ihrer Vorlagen erstellen, werden mit einem Konto mit Administratorrechten erstellt.

>[!NOTE]
>
>Obwohl Sie Ihre Ordner verschachteln können, werden sie den Benutzenden in der **Vorlagenkonsole** als flache Struktur angezeigt.

In einer Standard-AEM-Instanz ist der Ordner **Global** in der Vorlagenkonsole vorhanden. Dieser Ordner enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Vorlagentypen im aktuellen Ordner gefunden werden. Sie können Ihre Standardvorlagen entweder zu diesem Ordner hinzufügen oder aber einen Ordner erstellen (empfohlen).

>[!NOTE]
>
>Als Best Practice wird empfohlen, einen Ordner für Ihre benutzerdefinierten Vorlagen zu erstellen und nicht den globalen Ordner zu verwenden.

>[!CAUTION]
>
>Ordner müssen von einem Benutzer mit `admin`-Rechten erstellt werden.

Arten von Vorlagen und Richtlinien werden gemäß der folgenden Rangordnung in allen Ordnern übernommen:

1. der aktuelle Ordner
1. dem aktuellen Ordner übergeordnete Elemente
1. `/conf/global`
1. `/apps`
1. `/libs`

Eine Liste aller zulässigen Einträge wird erstellt. Wenn sich Konfigurationen (`path`/`label`) überschneiden, wird den Benutzern nur die Instanz angezeigt, die dem aktuellen Ordner am nächsten ist.

Gehen Sie wie folgt vor, um einen Ordner zu erstellen:

* Programmierbar oder mit CRXDE Lite
* Verwenden des Konfigurations-Browsers

## Verwenden von CRXDE Lite  {#using-crxde-lite}

1. Ein neuer Ordner (unter „/conf“) kann für Ihre Instanz entweder programmgesteuert oder mit CRXDE Lite erstellt werden.

   Die folgende Struktur muss verwendet werden:

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. Sie können die folgenden Eigenschaften des Ordnerstammknotens definieren:

   `<your-folder-name> [sling:Folder]`

   Name: `jcr:title`

   * Typ: `String`

   * Wert: Der Titel (für den Ordner), der in der **Vorlagen**-Konsole angezeigt werden soll

1. Weisen Sie *zusätzlich* zu den standardmäßigen Autorenberechtigungen (z. B. `content-authors`) jetzt eine oder mehrere Gruppen zu und definieren Sie die erforderlichen Zugriffsrechte (ACLs), damit Ihre Autorinnen und Autoren in der Lage sind, Vorlagen im neuen Ordner zu erstellen.

   Die Gruppe `template-authors` ist die Standardgruppe, die zugewiesen werden muss. Weitere Informationen finden Sie im folgenden Abschnitt [ACLs und Gruppen](/help/sites-developing/page-templates-editable.md#acls-and-groups).

   Umfassende Informationen zum Verwalten und Zuweisen von Zugriffsrechten finden Sie unter [Verwalten von Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md#access-right-management).

### Verwenden des Konfigurations-Browsers {#using-the-configuration-browser}

1. Wechseln Sie zu **Globale Navigation** > **Tools** > **Konfigurations-Browser**.

   Die vorhandenen Ordner werden links aufgelistet, einschließlich des Ordners **global**.

1. Klicken Sie auf **Erstellen**.
1. Im Dialogfeld **Konfiguration erstellen** müssen die folgenden Felder konfiguriert werden:

   * **Titel**: Geben Sie einen Titel für den Konfigurationsordner an.
   * **Bearbeitbare Vorlagen**: Aktivieren Sie diese Option, um bearbeitbare Vorlagen in diesem Ordner zuzulassen.

1. Klicken Sie auf **Erstellen**.

>[!NOTE]
>
>Im Konfigurations-Browser können Sie den Ordner „Global“ bearbeiten und die Option **Bearbeitbare Vorlagen** aktivieren, wenn Sie in diesem Ordner Vorlagen erstellen möchten. Diese Vorgehensweise wird jedoch nicht empfohlen.
>
>Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).

### ACLs und Gruppen {#acls-and-groups}

Sobald Ihre Vorlagenordner erstellt sind (entweder über CRXDE oder mit dem Konfigurations-Browser), müssen ACLs für die entsprechenden Gruppen für die Vorlagenordner definiert werden, um ein angemessenes Maß an Sicherheit zu gewährleisten.

Die Vorlagenordner für die [`We.Retail`-Referenzimplementierung](/help/sites-developing/we-retail.md) können als Beispiel herangezogen werden.

#### Die Gruppe „template-authors“  {#the-template-authors-group}

Die Gruppe `template-authors` ist die Gruppe zum Verwalten des Zugriffs auf Vorlagen und standardmäßig in AEM integriert. Sie ist aber leer. Benutzer müssen der Gruppe für das Projekt bzw. die Site hinzugefügt werden.

>[!CAUTION]
>
>Die Gruppe `template-authors` ist *nur* für Benutzerinnen und Benutzer, die die Möglichkeit haben müssen, neue Vorlagen zu erstellen.
>
>Das Bearbeiten von Vorlagen hat weitreichende Auswirkungen, und bei nicht ordnungsgemäßem Vorgehen können vorhandene Vorlagen beschädigt werden. Daher sollte diese Rolle zielgerichtet und nur qualifizierten Benutzerinnen und Benutzern zugewiesen werden.

In der folgenden Tabelle sind die erforderlichen Berechtigungen für die Bearbeitung von Vorlagen aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Pfad</th>
   <th>Rolle/Gruppe</th>
   <th>Berechtigungen<br /> </th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Vorlagenautoren<br /> </td>
   <td>lesen, schreiben, replizieren</td>
   <td>Vorlagenautorinnen und -autoren, die Vorlagen im Site-spezifischen <code>/conf</code>-Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>lesen</td>
   <td>Anonymer Web-Anwender muss Vorlagen beim Rendern einer Seite lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsautorinnen und -autoren müssen beim Aktivieren einer Seite die Vorlagen einer Seite aktivieren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lesen, schreiben, replizieren</td>
   <td>Vorlagenautorinnen und -autoren, die Vorlagen im Site-spezifischen <code>/conf</code>-Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>lesen</td>
   <td>Anonymer Web-Anwender muss beim Rendern einer Seite Richtlinien lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsautorinnen und -autoren müssen beim Aktivieren einer Seite die Richtlinien einer Vorlage aktivieren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Vorlagenautor</td>
   <td>lesen</td>
   <td>Vorlagenautorinnen und -autoren erstellen eine neue Vorlage, basierend auf einem der vordefinierten Vorlagentypen.</td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>keine</td>
   <td>Anonymer Web-Anwender darf nicht auf die Vorlagentypen zugreifen</td>
  </tr>
 </tbody>
</table>

Diese standardmäßige `template-authors`-Gruppe umfasst nur die Projekteinstellungen, bei denen alle Mitglieder von `template-authors` auf alle Vorlagen zugreifen und diese erstellen dürfen. Für komplexere Setups, bei denen mehrere Vorlagenautorengruppen benötigt werden, um einen getrennten Zugriff auf Vorlagen zu ermöglichen, müssen weitere benutzerdefinierte Vorlagenautorengruppen erstellt werden. Die Berechtigungen für die Vorlagenautorengruppen bleiben dabei jedoch dieselben.

#### Alte Vorlagen unter /conf/global {#legacy-templates-under-conf-global}

Speichern Sie keine Vorlagen in `/conf/global`. Bei einigen älteren Installationen gibt es jedoch möglicherweise noch Vorlagen an diesem Speicherort. *Nur* in diesen Fällen sollten die folgenden `/conf/global`-Pfade explizit konfiguriert werden.

<table>
 <tbody>
  <tr>
   <th>Pfad</th>
   <th>Rolle/Gruppe</th>
   <th>Berechtigungen<br /> </th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/global/settings/wcm/templates</code></td>
   <td>Vorlagenautorinnen und -autoren</td>
   <td>lesen, schreiben, replizieren</td>
   <td>Vorlagenautoren, die Vorlagen erstellen, lesen, aktualisieren, löschen und replizieren <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>lesen</td>
   <td>Anonymer Web-Anwender muss Vorlagen beim Rendern einer Seite lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsautorinnen und -autoren müssen die Vorlagen einer Seite aktivieren, wenn sie eine Seite aktivieren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/global/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lesen, schreiben, replizieren</td>
   <td>Vorlagenautoren, die Vorlagen erstellen, lesen, aktualisieren, löschen und replizieren <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>lesen</td>
   <td>Anonymer Web-Anwender muss beim Rendern einer Seite Richtlinien lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsautorinnen und -autoren müssen beim Aktivieren einer Seite die Richtlinien einer Vorlage aktivieren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/global/settings/wcm/template-types</code></td>
   <td>Vorlagenautor</td>
   <td>lesen</td>
   <td>Vorlagenautorinnen und -autoren erstellen eine neue Vorlage, basierend auf einem der vordefinierten Vorlagentypen</td>
  </tr>
  <tr>
   <td>Anonymer Web-Anwender</td>
   <td>keine</td>
   <td>Anonymer Web-Anwender darf nicht auf die Vorlagentypen zugreifen</td>
  </tr>
 </tbody>
</table>

## Vorlagentyp {#template-type}

Geben Sie beim Erstellen einer Vorlage einen Vorlagentyp an:

* Vorlagentypen stellen effektiv Vorlagen für eine Vorlage bereit. Bei der Erstellung einer Vorlage werden Struktur und anfänglicher Inhalt des ausgewählten Vorlagentyps zum Erstellen der Vorlage verwendet.

   * Der Vorlagentyp wird kopiert, um die Vorlage zu erstellen.
   * Nach dem Kopieren besteht die einzige Verbindung zwischen der Vorlage und dem Vorlagentyp in einer statischen Referenz zu Informationszwecken.

* Vorlagentypen ermöglichen es Ihnen, Folgendes zu definieren:

   * Den Ressourcentyp der Seitenkomponente.
   * Die Richtlinie des Stammknotens, die die im Vorlageneditor zulässigen Komponenten definiert.
   * Adobe empfiehlt, die Breakpoints für das responsive Raster und das Setup des Emulators für Mobilgeräte über den Vorlagentyp zu definieren. Dieser Schritt ist optional, da die Konfiguration auch für die jeweilige Vorlage definiert werden kann (siehe [Vorlagentyp und Mobilgerätegruppen](/help/sites-developing/page-templates-editable.md#p-template-type-and-mobile-device-groups-br-p)).

* AEM stellt einige vordefinierte Vorlagentypen wie HTML5-Seiten und Seiten mit adaptivem Formular bereit.

   * Weitere Beispiele werden als Teil des [`We.Retail`](/help/sites-developing/we-retail.md)-Beispielinhalts bereitgestellt.

* Vorlagentypen werden normalerweise von Entwicklerinnen und Entwicklern definiert.

Die vordefinierten Vorlagentypen werden unter folgendem Pfad gespeichert:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen. Der Grund dafür ist, dass der Inhalt von `/libs` überschrieben wird, wenn Sie Ihre Instanz das nächste Mal aktualisieren (und möglicherweise überschrieben wird, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

Ihre Site-spezifischen Vorlagentypen sollten an einer mit dem folgenden Pfad vergleichbaren Stelle gespeichert werden:

* `/apps/settings/wcm/template-types`

Definitionen für Ihre benutzerdefinierten Vorlagentypen sollten in benutzerdefinierten Ordnern (empfohlen) oder alternativ im Ordner `global` gespeichert werden. Zum Beispiel:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>Die Vorlagentypen müssen die korrekte Ordnerstruktur aufweisen (also `/settings/wcm/...`), sonst werden die Vorlagentypen nicht gefunden.

### Vorlagentyp und Mobilgerätegruppen {#template-type-and-mobile-device-groups-br}

Die [Gerätegruppen](/help/sites-developing/mobile.md#device-groups), die für eine bearbeitbare Vorlage verwendet werden (als relativer Pfad der Eigenschaft `cq:deviceGroups` festgelegt), definieren, welche mobilen Geräte als Emulatoren im [Layout-Modus](/help/sites-authoring/responsive-layout.md) der Seitenbearbeitung verfügbar sind. Dieser Wert kann an zwei Stellen festgelegt werden:

* Über den bearbeitbaren Vorlagentyp
* Über die bearbeitbare Vorlage

Beim Erstellen einer bearbeitbaren Vorlage wird der Wert aus dem Vorlagentyp in die jeweilige Vorlage kopiert. Wenn der Wert nicht für den Typ festgelegt ist, kann er für die Vorlage festgelegt werden. Sobald eine Vorlage erstellt wurde, findet keine Vererbung vom Typ auf die Vorlage statt.

>[!CAUTION]
>
>Der Wert von `cq:deviceGroups` muss als relativer Pfad wie `mobile/groups/responsive` festgelegt werden und nicht als absoluter Pfad wie `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>Bei [statischen Vorlagen](/help/sites-developing/page-templates-static.md) lässt sich der Wert von `cq:deviceGroups` im Stammverzeichnis der Site festlegen.
>
>Bei bearbeitbaren Vorlagen wird dieser Wert nun auf Vorlagenebene gespeichert und nicht mehr auf der Stammebene der Seiten unterstützt.

### Erstellen von Vorlagentypen {#creating-template-types}

Wenn Sie eine Vorlage erstellt haben, die als Grundlage für andere Vorlagen dienen kann, können Sie diese Vorlage als Vorlagentyp kopieren.

1. Erstellen Sie eine Vorlage wie andere bearbeitbare Vorlagen auch, [wie hier dokumentiert](/help/sites-authoring/templates.md#creating-a-new-template-template-author). Diese dient dann als Grundlage für Ihren Vorlagentyp.
1. Kopieren Sie mit CRXDE Lite die neu erstellte Vorlage aus dem Knoten `templates` in den Knoten `template-types` unter dem [Vorlagenordner](/help/sites-developing/page-templates-editable.md#template-folders).
1. Löschen Sie die Vorlage aus dem Knoten `templates` unter dem [Vorlagenordner](/help/sites-developing/page-templates-editable.md#template-folders).
1. Löschen Sie in der Kopie der Vorlage, die sich unter dem `template-types`-Knoten befindet, alle `cq:template`- und `cq:templateType`-Eigenschaften aus allen `jcr:content`-Knoten.

Sie können auch Ihren eigenen Vorlagentyp entwickeln, indem Sie eine bearbeitbare Beispielvorlage von GitHub als Grundlage verwenden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-sites-example-custom-template-type auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type).
* Laden Sie das Projekt als [ZIP-Datei](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/zip/refs/heads/master) herunter.

## Vorlagendefinitionen {#template-definitions}

Definitionen für bearbeitbare Vorlagen werden in [benutzerdefinierten Ordnern](/help/sites-developing/page-templates-editable.md#template-folders) (empfohlen) oder alternativ im Ordner `global` gespeichert. Zum Beispiel:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

Der Stammknoten der Vorlage weist den Typ `cq:Template` und das folgende Strukturgerüst auf:

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

Die Hauptelemente sind:

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:content {#jcr-content}

Dieser Knoten enthält Eigenschaften für die Vorlage:

* **Name**: `jcr:title`

* **Name**: `status`

   * **Typ**: `String`

   * **Wert**: `draft`, `enabled`, oder `disabled`

### Struktur {#structure}

Definiert die Struktur der resultierenden Seite:

* Sie wird beim Erstellen einer Seite mit dem anfänglichen Inhalt (`/initial`) zusammengeführt.
* Änderungen an der Struktur spiegeln sich in allen Seiten wider, die mit der Vorlage erstellt wurden.
* Der Knoten `root` (`structure/jcr:content/root`) definiert die Liste der Komponenten, die auf der resultierenden Seite verfügbar sind.

   * Komponenten, die in der Vorlagenstruktur definiert sind, können in resultierenden Seiten nicht verschoben oder gelöscht werden.
   * Nachdem eine Komponente entsperrt wurde, wird die Eigenschaft `editable` auf `true` gesetzt.

   * Nachdem eine Komponente, die bereits Inhalt enthält, entsperrt wurde, wird dieser Inhalt in die Verzweigung `initial` verschoben.

* Der Knoten `cq:responsive` enthält Definitionen für das responsive Layout.

### Anfänglicher Inhalt {#initial-content}

Definiert den anfänglichen Inhalt, den eine neue Seite bei der Erstellung enthält:

* Er enthält einen Knoten `jcr:content`, der auf alle neue Seiten kopiert wird.
* Er wird beim Erstellen einer Seite mit der Struktur (`/structure`) zusammengeführt.
* Vorhandene Seiten werden aktualisiert, wenn der anfängliche Inhalt nach der Erstellung geändert wird.
* Der Knoten `root` enthält eine Liste von Komponenten, die definieren, was auf der resultierenden Seite verfügbar ist.
* Wird einer Komponente im Strukturmodus Inhalt hinzugefügt und wird diese Komponente anschließend entsperrt (oder umgekehrt), so wird dieser Inhalt als anfänglicher Inhalt verwendet.

### Layout {#layout}

Beim [Bearbeiten einer Vorlage können Sie das Layout definieren](/help/sites-authoring/templates.md). Diese Praxis verwendet standardmäßig ein [responsives Layout](/help/sites-authoring/responsive-layout.md), das auch [konfiguriert werden kann](/help/sites-administering/configuring-responsive-layout.md).

### Inhaltsrichtlinien {#content-policies}

Die Inhalts- (oder Design-) Richtlinien definieren die Design-Eigenschaften einer Komponente, wie z. B. die Verfügbarkeit der Komponente oder die minimalen/maximalen Abmessungen. Diese Richtlinien sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden). Inhaltsrichtlinien können mit dem Vorlageneditor erstellt und ausgewählt werden.

* Die Eigenschaft `cq:policy` im Knoten `root`
  `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Stellt einen relativen Verweis auf die Inhaltsrichtlinie für das Absatzsystem der Seite bereit.

* Die Eigenschaft `cq:policy` der komponentenexpliziten Knoten unter `root` stellt Links zu den Richtlinien für die einzelnen Komponenten bereit.

* Die tatsächlichen Richtliniendefinitionen werden gespeichert unter:
  `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>Die Pfade der Richtliniendefinitionen sind vom Pfad der Komponente abhängig. Die `cq:policy` enthält einen relativen Verweis auf die Konfiguration selbst.

>[!NOTE]
>
>Für Seiten, die anhand bearbeitbarer Vorlagen erstellt wurden, steht der Design-Modus im Seiten-Editor nicht zur Verfügung.
>
>Die Baumstruktur `policies` einer bearbeitbaren Vorlage weist dieselbe Hierarchie auf wie die Designmodus-Konfiguration einer statischen Vorlage unter:
>
>`/etc/designs/<my-site>/jcr:content/<component-name>`
>
>Die Design-Modus-Konfiguration einer statischen Vorlage wurde pro Seitenkomponente definiert.

### Seitenrichtlinien {#page-policies}

Seitenrichtlinien ermöglichen es, die [Inhaltsrichtlinie](#content-policies) für die Seite (Hauptabsatzsystem) entweder in der Vorlage oder den resultierenden Seiten zu definieren.

### Aktivieren und Zulassen einer Vorlage {#enabling-and-allowing-a-template-for-use}

1. **Aktivieren der Vorlage**

   Bevor eine Vorlage verwendet werden kann, muss sie wie folgt aktiviert werden:

   * Durch [Aktivieren der Vorlage](/help/sites-authoring/templates.md#enablingatemplateauthor) über die **Vorlagen**-Konsole.

   * Durch Festlegen der Statuseigenschaft des Knotens `jcr:content`

      * Zum Beispiel unter:
        `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieren Sie die Eigenschaft:

         * Name: Status
         * Typ: String
         * Wert: `enabled`

1. **Zugelassene Vorlagen**

   * [Definieren Sie die Pfade zugelassener Vorlagen über die **Seiteneigenschaften**](/help/sites-authoring/templates.md#allowing-a-template-author) der entsprechenden Seite oder Stammseite einer Unterverzweigung.
   * Legen Sie die folgende Eigenschaft fest:
     `cq:allowedTemplates`
Auf dem `jcr:content`-Knoten der erforderlichen Verzweigung.

   Beispielsweise mit dem Wert:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resultierende Inhaltsseiten {#resultant-content-pages}

Für Seiten, die anhand bearbeitbarer Vorlagen erstellt wurden, gilt Folgendes:

* Sie werden mit einer Unterbaumstruktur erstellt, die aus `structure` und `initial` in der Vorlage zusammengeführt wird.

* Sie enthalten Verweise auf Informationen, die in der Vorlage und im Vorlagentyp enthalten sind. Sie können diese Funktion mit einem `jcr:content`-Knoten mit den folgenden Eigenschaften erzielen:

   * `cq:template`
Stellt den dynamischen Verweis auf die aktuelle Vorlage bereit und ermöglicht es, Änderungen an der Vorlage auf den aktuellen Seiten widerzuspiegeln.

   * `cq:templateType`
Stellt einen Verweis auf den Vorlagentyp bereit.

![chlimage_1-71](assets/chlimage_1-71.png)

Das obige Diagramm veranschaulicht, wie Vorlagen, Inhalte und Komponenten zusammenhängen:

* Controller – `/content/<my-site>/<my-page>`
Die resultierende Seite, die auf die Vorlage verweist. Der Inhalt steuert den gesamten Prozess. Gemäß den Definitionen greift er auf die entsprechenden Vorlagen und Komponenten zu.

* Konfiguration – `/conf/<my-folder>/settings/wcm/templates/<my-template>`
Die [Vorlage und zugehörigen Inhaltsrichtlinien](#template-definitions) definieren die Seitenkonfiguration.

* Modell – OSGi-Bundles Die [OSGi-Bundles](/help/sites-deploying/osgi-configuration-settings.md) implementieren die Funktionalität.

* Ansicht – `/apps/<my-site>/components`
Der Inhalt wird sowohl in der Authoring- als auch in der Publishing-Umgebung durch [Komponenten](/help/sites-developing/components.md) gerendert.

Beim Rendern einer Seite:

* **Vorlagen**:

   * Die `cq:template`-Eigenschaft des Knotens `jcr:content` wird referenziert, um auf die Vorlage zuzugreifen, die dieser Seite entspricht.

* **Komponenten**:

   * Die Seitenkomponente führt die Baumstruktur `structure/jcr:content` der Vorlage mit der Baumstruktur `jcr:content` der Seite zusammen.

   * Die Seitenkomponente gestattet es der Autorin bzw. dem Autor nur, die Knoten der Vorlagenstruktur zu bearbeiten, die als bearbeitbar gekennzeichnet wurden (sowie jegliche untergeordneten Elemente).
   * Beim Rendern einer Komponente auf einer Seite wird der relative Pfad dieser Komponente vom Knoten `jcr:content` übernommen. Derselbe Pfad unter dem Knoten `policies/jcr:content` der Vorlage wird dann durchsucht.

      * Die Eigenschaft `cq:policy` dieses Knotens verweist auf die eigentliche Inhaltsrichtlinie (d. h. sie enthält die Design-Konfiguration für diese Komponente).

      * Mit dieser Funktion können Sie über mehrere Vorlagen verfügen, die dieselben Inhaltsrichtlinienkonfigurationen wiederverwenden.
