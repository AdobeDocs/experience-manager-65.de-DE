---
title: Bearbeitbare Seitenvorlagen
seo-title: Bearbeitbare Seitenvorlagen
description: Bearbeitbare Vorlagen wurden eingeführt, um es Benutzern, die keine Entwickler sind, zu ermöglichen, Vorlagen zu erstellen und zu bearbeiten, Vorlagen bereitzustellen, die eine dynamische Verbindung zu allen mit ihnen erstellten Seiten beibehalten, und die Seitenkomponente allgemeiner zu gestalten.
seo-description: Bearbeitbare Vorlagen wurden eingeführt, um es Benutzern, die keine Entwickler sind, zu ermöglichen, Vorlagen zu erstellen und zu bearbeiten, Vorlagen bereitzustellen, die eine dynamische Verbindung zu allen mit ihnen erstellten Seiten beibehalten, und die Seitenkomponente allgemeiner zu gestalten.
uuid: 61791960-fdef-4e49-878a-11fdf1d4f0ab
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 1099cc44-de6d-499e-8b52-f2f5811ae086
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Bearbeitbare Seitenvorlagen {#page-templates-editable}

Bearbeitbare Vorlagen wurden zu folgenden Zwecken eingeführt:

* Sie sollen spezialisierten Autoren [das Erstellen und Bearbeiten von Vorlagen](/help/sites-authoring/templates.md) ermöglichen.

   * Diese spezialisierten Autoren werden als **Vorlagenautoren** bezeichnet.
   * Vorlagenautoren müssen Mitglieder der Gruppe `template-authors` sein.

* Damit sollen Vorlagen bereitgestellt werden, die eine dynamische Verbindung zu allen damit erstellten Seiten beibehalten. Dadurch wird sichergestellt, dass alle Änderungen an der Vorlage auf den Seiten widergespiegelt werden.
* Die Seitenkomponente soll damit allgemeiner gestaltet werden, damit die Seitenkernkomponente ohne Anpassung verwendet werden kann.

Mit bearbeitbaren Vorlagen werden die Aspekte, die eine Seite bilden, innerhalb von Komponenten isoliert. Sie können die erforderlichen Komponentenkombinationen über eine Benutzeroberfläche konfigurieren. Damit entfällt die Notwendigkeit, für jede Seitenvariante eine neue Seitenkomponente zu entwickeln.

>[!NOTE]
>
>[Statische Vorlagen](/help/sites-developing/page-templates-static.md) sind ebenfalls verfügbar.

Dieses Dokument:

* bietet einen Überblick über die Erstellung bearbeitbarer Vorlagen.

   * For details see [Creating Page Templates](/help/sites-authoring/templates.md)

* beschreibt die Administrator- bzw. Entwickleraufgaben, die zur Erstellung bearbeitbarer Vorlagen erforderlich sind.
* beschreibt die technischen Grundlagen bearbeitbarer Vorlagen.

Bei den in diesem Dokument beschriebenen Schritten wird vorausgesetzt, dass Sie bereits mit dem Erstellen und Bearbeiten von Vorlagen vertraut sind. Weitere Informationen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) für Autoren, das detailliert beschreibt, welche Funktionen Vorlagenautoren mit bearbeitbaren Vorlagen zur Verfügung stehen.

>[!NOTE]
>
>Folgende Übung könnte auch für die Einrichtung einer bearbeitbaren Seitenvorlage in einem neuen Projekt von Interesse sein:
>[Erste Schritte mit AEM-Sites Teil 2 - Erstellen einer Basisseite und Vorlage](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part2.html)

## Erstellen neuer Vorlagen {#creating-a-new-template}

Bearbeitbare Vorlagen werden von Vorlagenautoren in erster Linie mit der [der Vorlagenkonsole und dem Vorlagen-Editor](/help/sites-authoring/templates.md) erstellt. In diesem Abschnitt finden Sie einen Überblick über diesen Prozess, der anschließend aus technischer Perspektive beleuchtet wird.

Informationen zum Verwenden bearbeitbarer Vorlagen in AEM-Projekten finden Sie unter [Erstellen von AEM-Projekten mithilfe von Lazybones](https://helpx.adobe.com/experience-manager/using/aem_lazybones.html).

Gehen Sie zum Erstellen einer neuen bearbeitbaren Vorlage wie folgt vor:

1. Erstellen Sie einen [Ordner für die Vorlagen](#template-folders). Dies ist zwar nicht unbedingt erforderlich, wird aber empfohlen.
1. Wählen Sie einen [Vorlagentyp](#template-type) aus. This is copied to create the [template definition](#template-definitions).

   >[!NOTE]
   >
   >Standardmäßig sind bereits diverse Vorlagen verfügbar. Bei Bedarf können Sie aber auch [eigene Site-spezifische Vorlagentypen](/help/sites-developing/page-templates-editable.md#creating-template-types) erstellen.

1. Konfigurieren Sie die Struktur, die Inhaltsrichtlinien, den anfänglichen Inhalt und das Layout der neuen Vorlage.

   **Struktur**

   * Die Struktur ermöglicht es Ihnen, Komponenten und Inhalte für Ihre Vorlage zu definieren.
   * Komponenten, die in der Vorlagenstruktur definiert sind, können auf resultierenden Seiten nicht verschoben oder gelöscht werden.

      * Wenn Sie eine Vorlage in einem benutzerdefinierten Ordner außerhalb des We.Retail-Beispielinhalts erstellen, können Sie Foundation-Komponenten wählen oder [Kernkomponenten](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) verwenden.
   * Wenn Seitenautoren die Möglichkeit haben sollen, Komponenten hinzuzufügen und zu entfernen, fügen Sie der Vorlage ein Absatzsystem hinzu.
   * Komponenten können entsperrt und erneut gesperrt werden, damit Sie den anfänglichen Inhalt definieren können.
   Einzelheiten dazu, wie Vorlagenautoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Technische Details zu den Strukturen werden in diesem Dokument unter [Struktur](/help/sites-developing/page-templates-editable.md#structure) erläutert.

   **Richtlinien**

   * Die Richtlinien für Inhalte definieren die Designeigenschaften einer Komponente.

      * Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen.
   * Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden).
   Einzelheiten dazu, wie Vorlagenautoren Richtlinien definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Inhaltsrichtlinien](/help/sites-developing/page-templates-editable.md#content-policies) erläutert.

   **Anfänglicher Inhalt**

   * Der anfängliche Inhalt definiert Inhalt, der angezeigt wird, wenn eine Seite anfänglich auf Grundlage einer Vorlage erstellt wird.
   * Der anfängliche Inhalt kann dann von Seitenautoren bearbeitet werden.
   Einzelheiten dazu, wie Vorlagenautoren Strukturen definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-initial-content-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Anfänglicher Inhalt](/help/sites-developing/page-templates-editable.md#initial-content) erläutert.

   **Layout**

   * Sie können das Vorlagen-Layout für verschiedene Geräte definieren.
   * Responsives Layout funktioniert für Vorlagen ebenso wie für die Seitenbearbeitung.
   Einzelheiten dazu, wie Vorlagenautoren Vorlagen-Layouts definieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-layout-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Layout](/help/sites-developing/page-templates-editable.md#layout) erläutert.

1. Aktivieren Sie die Vorlage und lassen Sie ihre Verwendung dann für bestimmte Inhaltsbäume zu.

   * Eine Vorlage kann aktiviert oder deaktiviert werden, um sie für Vorlagenautoren verfügbar bzw. nicht verfügbar zu machen.
   * Eine Vorlage kann für bestimmte Seitenverzweigungen verfügbar oder nicht verfügbar gemacht werden.
   Einzelheiten dazu, wie Vorlagenautoren Vorlagen aktivieren können, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Aktivieren und Zulassen von Vorlagen](/help/sites-developing/page-templates-editable.md#enabling-and-allowing-a-template-for-use) erläutert.

1. Verwenden Sie sie, um Inhaltsseiten zu erstellen.

   * Wenn Sie eine Vorlage zum Erstellen einer neuen Seite verwenden, ist kein Unterschied zwischen den statischen und bearbeitbaren Vorlagen ersichtlich.
   * Für die Seitenautoren ist der Prozess transparent.
   For details on how a page author uses templates to create a page, see [Creating and Organizing Pages](/help/sites-authoring/managing-pages.md#templates).

   Technische Details zu den Richtlinien werden in diesem Dokument unter [Resultierende Inhaltsseiten](/help/sites-developing/page-templates-editable.md#resultant-content-pages) erläutert.

>[!NOTE]
>
>The editor client library assumes the presence of the `cq.shared` namespace in content pages, and if it is absent the JavaScript error `Uncaught TypeError: Cannot read property 'shared' of undefined` will result.
>
>Alle Beispielinhaltsseiten enthalten `cq.shared`, sodass jeglicher darauf basierender Inhalt automatisch `cq.shared` umfasst. Wenn Sie sich jedoch ganz neue eigene Inhaltsseiten erstellen möchten, die nicht auf Beispielinhalt basieren, müssen Sie sicherstellen, dass Sie den `cq.shared`-Namespace einbinden.
>
>Weitere Informationen finden Sie unter [Verwendung clientseitiger Bibliotheken](/help/sites-developing/clientlibs.md).

>[!CAUTION]
>
>Geben Sie in eine Vorlage nie Informationen ein, die [internationalisiert](/help/sites-developing/i18n.md) werden müssen.

## Vorlagenordner {#template-folders}

Zum Organisieren Ihrer Vorlagen können Sie die folgenden Ordner verwenden:

* **global**
* Site-spezifische Ordner Die Site-spezifischen Ordner, die Sie zum Organisieren Ihrer Vorlagen erstellen, werden mit einem Konto mit Administratorrechten erstellt.

>[!NOTE]
>
>Obwohl Sie Ihre Ordner verschachteln können, werden sie den Benutzern in der **Vorlagenkonsole** als flache Struktur angezeigt.

In einer Standard-AEM-Instanz ist der Ordner **Global** bereits in der Vorlagen-Konsole vorhanden. Er enthält Standardvorlagen und dient als Ausweichlösung, wenn keine Richtlinien und/oder Arten von Vorlagen im aktuellen Ordner gefunden werden. Sie können Ihre Standardvorlagen entweder zu diesem Ordner hinzufügen oder aber einen neuen Ordner erstellen.

>[!NOTE]
>
>Als Best Practice wird empfohlen, einen neuen Ordner für Ihre benutzerdefinierten Vorlagen zu erstellen und nicht den globalen Ordner zu verwenden.

>[!CAUTION]
>
>Folders must be created by a user with `admin` rights.

Arten von Vorlagen und Richtlinien werden gemäß der folgenden Rangordnung in allen Ordnern übernommen:

1. der aktuelle Ordner
1. dem aktuellen Ordner übergeordnete Elemente
1. `/conf/global`
1. `/apps`
1. `/libs`

Eine Liste aller zulässigen Einträge wird erstellt. If any configurations overlap ( `path`/ `label`), only the instance closest to the current folder is presented to the user.

Zum Erstellen eines neuen Ordners stehen Ihnen die folgenden Optionen zur Auswahl:

* Die programmgesteuerte Erstellung oder die Erstellung mit CRXDE Lite
* Verwenden des Konfigurationsbrowsers

## Verwenden von CRXDE Lite {#using-crxde-lite}

1. Ein neuer Ordner (unter /conf) kann entweder programmgesteuert oder mit CRXDE Lite erstellt werden.

   Nur die folgende Struktur darf verwendet werden:

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

   * Wert: Der Titel (für den Ordner), der Ihnen in der **Vorlagen**-Konsole angezeigt werden soll

1. *Zusätzlich* zu den standardmäßigen Autorenprivilegien und -berechtigungen (z. B. `content-authors`), müssen Sie jetzt eine oder mehrere Gruppen zuweisen und die erforderlichen Zugriffsrechte (ACLs) definieren, damit Ihre Autoren in der Lage sind, Vorlagen im neuen Ordner zu erstellen.

   Die Gruppe `template-authors` ist die Standardgruppe, die zugewiesen werden muss. Weitere Informationen finden Sie im folgenden Abschnitt [ACLs und Gruppen](/help/sites-developing/page-templates-editable.md#acls-and-groups).

   See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.

### Verwenden des Konfigurationsbrowsers {#using-the-configuration-browser}

1. Wechseln Sie zu **Globale Navigation** > **Tools** > **Konfigurationsbrowser**.

   Die vorhandenen Ordner werden links aufgelistet, einschließlich des Ordners **global**.

1. Klicken Sie auf **Erstellen**.
1. In the **Create Configuration** dialog the following fields need to be configured:

   * **Titel**: Geben Sie einen Titel für den Konfigurationsordner ein.
   * **Bearbeitbare Vorlagen**: Aktivieren Sie dieses Kontrollkästchen, um bearbeitbare Vorlagen in diesem Ordner zuzulassen.

1. Klicken Sie auf **Erstellen**

>[!NOTE]
>
>Im Konfigurationsbrowser können Sie den Ordner „global“ bearbeiten und die Option **Bearbeitbare Vorlagen** aktivieren, wenn Sie in diesem Ordner Vorlagen erstellen möchten. Davon ist jedoch abzuraten.

### ACLs und Gruppen {#acls-and-groups}

Sobald Ihre Vorlagenordner erstellt sind (entweder über CRXDE oder mit dem Konfigurationsbrowser), müssen ACLs für die entsprechenden Gruppen für die Vorlagenordner definiert werden, um ein angemessenes Maß an Sicherheit zu gewährleisten.

Die Vorlagenordner für die [We.Retail-Referenzimplementierung ](/help/sites-developing/we-retail.md) können als Beispiel herangezogen werden.

#### Die Gruppe „template-authors“ {#the-template-authors-group}

Die Gruppe `template-authors` ist die Gruppe zum Verwalten des Zugriffs auf Vorlagen und ist standardmäßig in AEM integriert, diese ist aber leer. Benutzer müssen der Gruppe für das Projekt bzw. die Site hinzugefügt werden.

>[!CAUTION]
>
>Die Gruppe `template-authors` ist *nur* für Benutzer, die die Möglichkeit haben müssen, neue Vorlagen zu erstellen.
>
>Das Bearbeiten von Vorlagen hat weitreichende Auswirkungen und bei nicht ordnungsgemäßem Vorgehen können vorhandene Vorlagen beschädigt werden. Daher sollte diese Rolle zielgerichtet und nur qualifizierten Benutzer zugewiesen werden.

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
   <td>Template Authors<br /> </td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen im Site-spezifischen <code>/conf</code> Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss Vorlagen beim Rendern einer Seite lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>replicateContent-Autoren müssen beim Aktivieren einer Seite die Vorlagen einer Seite aktivieren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen im Site-spezifischen <code>/conf</code> Raum erstellen, lesen, aktualisieren, löschen und replizieren</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss beim Rendern einer Seite Richtlinien lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsersteller müssen beim Aktivieren einer Seite die Richtlinien einer Vorlage aktivieren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Vorlagenautor</td>
   <td>lesen</td>
   <td>Der Vorlagenautor erstellt eine neue Vorlage basierend auf einem der vordefinierten Vorlagentypen.</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>none</td>
   <td>Anonymer Webbenutzer darf nicht auf die Vorlagentypen zugreifen</td>
  </tr>
 </tbody>
</table>

This default `template-authors` group only covers the project setups, where all `template-authors` members are allowed to access and author all templates. Für komplexere Setups, bei denen mehrere Vorlagenautorengruppen benötigt werden, um einen getrennten Zugriff auf Vorlagen zu ermöglichen, müssen weitere benutzerdefinierte Vorlagenautorengruppen erstellt werden. Die Berechtigungen für die Vorlagenautorengruppen bleiben dabei jedoch dieselben.

#### Alte Vorlagen unter /conf/global {#legacy-templates-under-conf-global}

Templates should no longer be stored in `/conf/global`, however for some legacy installations there may still be templates in this location. ONLY in such legacy situations should the following `/conf/global` paths be explicitly configured.

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
   <td>Vorlagenautoren</td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen erstellen, lesen, aktualisieren, löschen und replizieren in <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss Vorlagen beim Rendern einer Seite lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsersteller müssen beim Aktivieren einer Seite die Vorlagen einer Seite aktivieren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/global/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>Lesen, Schreiben, Replizieren</td>
   <td>Vorlagenautoren, die Vorlagen erstellen, lesen, aktualisieren, löschen und replizieren in <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>lesen</td>
   <td>Anonymer Webbenutzer muss beim Rendern einer Seite Richtlinien lesen</td>
  </tr>
  <tr>
   <td>Autoren von Inhalten</td>
   <td>replizieren</td>
   <td>Inhaltsersteller müssen beim Aktivieren einer Seite die Richtlinien einer Vorlage aktivieren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/global/settings/wcm/template-types</code></td>
   <td>Vorlagenautor</td>
   <td>lesen</td>
   <td>Vorlagenautor erstellt eine neue Vorlage basierend auf einem der vordefinierten Vorlagentypen</td>
  </tr>
  <tr>
   <td>Anonymer Webbenutzer</td>
   <td>none</td>
   <td>Anonymer Webbenutzer darf nicht auf die Vorlagentypen zugreifen</td>
  </tr>
 </tbody>
</table>

## Vorlagentyp {#template-type}

Beim Erstellen einer neuen Vorlage müssen Sie einen Vorlagentyp angeben:

* Vorlagentypen stellen quasi Vorlagen für eine Vorlage bereit. Beim Erstellen einer neuen Vorlage wird die Struktur und der anfängliche Inhalt des gewählten Vorlagentyps verwendet, um die neue Vorlage zu erstellen.

   * Der Vorlagentyp wird zum Erstellen der Vorlage kopiert.
   * Nach Abschluss des Kopiervorgangs ist die einzige Verbindung zwischen der Vorlage und dem Vorlagentyp ein statischer Verweis zu Informationszwecken.

* Vorlagentypen ermöglichen es Ihnen, Folgendes zu definieren:

   * Den Ressourcentyp der Seitenkomponente.
   * Die Richtlinie des Stammknotens, die die im Vorlagen-Editor zulässigen Komponenten definiert.
   * Es wird empfohlen, die Haltepunkte für das responsive Raster und das Setup des Emulators für mobile Geräte über den Vorlagentyp zu definieren. Dies ist optional, da die Konfiguration auch für eine einzelne Vorlage definiert werden kann (siehe [Vorlagentyp und Mobilgerätegruppen](/help/sites-developing/page-templates-editable.md#p-template-type-and-mobile-device-groups-br-p)).

* AEM stellt einige vordefinierte Vorlagentypen wie HTML5-Seiten und Seiten mit adaptivem Formular bereit.

   * Weitere Beispiele finden Sie in den [We.Retail](/help/sites-developing/we-retail.md)-Beispielinhalten.

* Vorlagentypen werden in der Regel von Entwicklern definiert.

Die vordefinierten Vorlagentypen werden unter dem folgenden Pfad gespeichert:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>You must not change anything in the `/libs` path. This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may be overwritten when you apply either a hotfix or feature pack).

Ihre Site-spezifischen Vorlagentypen sollten an einer mit dem folgenden Pfad vergleichbaren Stelle gespeichert werden:

* `/apps/settings/wcm/template-types`

Definitions for your customized templates types should be stored in user-defined folders (recommended) or alternatively in `global`. Beispiel:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>The template types have to respect the correct folder structure (i.e. `/settings/wcm/...`), otherwise the template types will not be found.

### Vorlagentyp und Mobilgerätegruppen {#template-type-and-mobile-device-groups-br}

Die [Gerätegruppen](/help/sites-developing/mobile.md#device-groups), die für eine bearbeitbare Vorlage verwendet werden (als relativer Pfad der Eigenschaft `cq:deviceGroups` festgelegt), definieren, welche mobilen Geräte als Emulatoren im [Layout-Modus](/help/sites-authoring/responsive-layout.md) der Seitenbearbeitung verfügbar sind. Dieser Wert kann an zwei Stellen festgelegt werden:

* Über den bearbeitbaren Vorlagentyp
* Über die bearbeitbare Vorlage

Beim Erstellen einer neuen bearbeitbaren Vorlage wird der Wert aus dem Vorlagentyp in die jeweilige Vorlage übernommen. Wenn der Wert nicht über den Typ festgelegt wird, kann er über die Vorlage festgelegt werden. Sobald eine Vorlage erstellt wurde, findet keine Vererbung vom Typ auf die Vorlage statt.

>[!CAUTION]
>
>The value of `cq:deviceGroups` must be set as a relative path such as `mobile/groups/responsive` and not as an absolute path such as `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>Bei [statischen Vorlagen](/help/sites-developing/page-templates-static.md) lässt sich der Wert von `cq:deviceGroups` im Stammverzeichnis der Site festlegen.
>
>Bei bearbeitbaren Vorlagen wird dieser Wert nun auf Vorlagenebene gespeichert und nicht mehr auf der Stammebene der Seiten unterstützt.

### Erstellen von Vorlagentypen {#creating-template-types}

Wenn Sie eine Vorlage erstellt haben, die als Grundlage für andere Vorlagen dienen kann, können Sie diese Vorlage als Vorlagentyp kopieren.

1. Create a template as you would any editable template [as documented here](/help/sites-authoring/templates.md#creating-a-new-template-template-author), which will serve as the basis of your template type.
1. Kopieren Sie mit CRXDE Lite die neu erstellte Vorlage aus dem Knoten `templates` in den Knoten `template-types` unter dem [Vorlagenordner](/help/sites-developing/page-templates-editable.md#template-folders).
1. Delete the template from the `templates` node under the [template folder](/help/sites-developing/page-templates-editable.md#template-folders).
1. In the copy of the template that is under the `template-types` node, delete all `cq:template` and `cq:templateType` `jcr:content` properties.

Sie können auch Ihren eigenen Vorlagentyp entwickeln, indem Sie eine bearbeitbare Beispielvorlage von GitHub als Grundlage verwenden.

CODE AUF GITHUB

Den Code dieser Seite finden Sie auf GitHub

* [Öffnen Sie das Projekt aem-sites-example-custom-template-type auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip) herunter

## Vorlagendefinitionen {#template-definitions}

Definitionen für bearbeitbare Vorlagen werden in [benutzerdefinierten Ordnern](/help/sites-developing/page-templates-editable.md#template-folders) (empfohlen) oder alternativ im Ordner `global` gespeichert. Beispiel:

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

### jcr:content{#jcr-content} gespeichert 

Dieser Knoten enthält Eigenschaften für die Vorlage:

* **Name**: `jcr:title`

* **Name**: `status`

   * ``**Typ**: `String`

   * **Wert**: `draft`, `enabled` oder `disabled`

### Struktur {#structure}

Definiert die Struktur der resultierenden Seite:

* Is merged with the initial content ( `/initial`) when creating a new page.
* Änderungen an der Struktur werden auf allen mit der Vorlage erstellten Seiten berücksichtigt.
* The `root` ( `structure/jcr:content/root`) node defines the list of components that will be available in the resulting page.

   * Komponenten, die in der Vorlagenstruktur definiert sind, können auf resultierenden Seiten nicht verschoben oder gelöscht werden.
   * Sobald eine Komponente entsperrt ist, wird die Eigenschaft `editable` auf `true` festgelegt.

   * Sobald eine Komponente, die bereits Inhalt enthält, entsperrt ist, wird dieser Inhalt in die Verzweigung `initial` verschoben.

* The `cq:responsive` node holds definitions for the responsive layout.

### Anfänglicher Inhalt {#initial-content}

Definiert den anfänglichen Inhalt, den eine neue Seite bei Erstellung enthält:

* Er enthält einen Knoten `jcr:content`, der auf alle neue Seiten kopiert wird.
* Is merged with the structure ( `/structure`) when creating a new page.
* Vorhandene Seiten werden nicht aktualisiert, wenn der anfängliche Inhalt nach der Erstellung geändert wird.
* Der Knoten `root` enthält eine Liste von Komponenten, mit denen festgelegt wird, was auf der resultierenden Seite verfügbar sein soll.
* Wird einer Komponente im Strukturmodus Inhalt hinzugefügt und wird diese Komponente anschließend entsperrt (oder umgekehrt), so wird dieser Inhalt als anfänglicher Inhalt verwendet.

### Layout {#layout}

When [editing a template you can define the layout](/help/sites-authoring/templates.md), this uses [standard responsive layout](/help/sites-authoring/responsive-layout.md) that can also be [configured](/help/sites-administering/configuring-responsive-layout.md).

### Inhaltsrichtlinien {#content-policies}

Die Richtlinien für Inhalt (oder Design) definieren die Entwurfseigenschaften einer Komponente. Zum Beispiel die verfügbaren Komponenten oder minimale/maximale Abmessungen. Diese sind auf die Vorlage anwendbar (und auf Seiten, die mit der Vorlage erstellt wurden). Inhaltsrichtlinien können mit dem Vorlagen-Editor erstellt und ausgewählt werden.

* Die Eigenschaft `cq:policy`auf dem `root` Knoten
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Stellt einen relativen Verweis auf die Inhaltsrichtlinie für das Absatzsystem der Seite bereit.

* The property `cq:policy`, on the component-explicit nodes under `root`, provide links to the policies for the individual components.

* Die tatsächlichen Richtliniendefinitionen werden gespeichert unter:
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>Die Pfade der Richtliniendefinitionen sind vom Pfad der Komponente abhängig. `cq:policy` enthält einen relativen Verweis auf die Konfiguration selbst.

>[!NOTE]
>
>Für Seiten, die anhand bearbeitbarer Vorlagen erstellt wurden, steht der Designmodus im Seiten-Editor nicht zur Verfügung.
>
>The `policies` tree of an editable template has the same hierarchy as the design mode configuration of a static template under:
>
>`/etc/designs/<my-site>/jcr:content/<component-name>`
>
>Die Designmodus-Konfiguration statischer Vorlagen wird auf Seitenkomponentenebene definiert.

### Seitenrichtlinien {#page-policies}

Seitenrichtlinien ermöglichen es, die [Inhaltsrichtlinie](#content-policies) für die Seite (Hauptabsatzsystem) entweder in der Vorlage oder den resultierenden Seiten zu definieren.

### Aktivieren und Zulassen einer Vorlage {#enabling-and-allowing-a-template-for-use}

1. **Aktivieren Sie die Vorlage.**

   Bevor eine Vorlage verwendet werden kann, muss sie auf eine der folgenden Weisen aktiviert werden:

   * [Durch Aktivieren der Vorlage](/help/sites-authoring/templates.md#enablingatemplateauthor) über die **Vorlagenkonsole**

   * Setting the status property on the `jcr:content` node.

      * Beispiel:
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * die Eigenschaft:

         * Name: status
         * Typ: String
         * Wert: `enabled`

1. **Zugelassene Vorlagen**

   * [Definieren Sie die Pfade zugelassener Vorlagen über die **Seiteneigenschaften **](/help/sites-authoring/templates.md#allowing-a-template-author)der entsprechenden Seite oder Stammseite einer Unterverzweigung.
   * Legen Sie die Eigenschaft fest:
      `cq:allowedTemplates`
Auf dem `jcr:content` Knoten der erforderlichen Verzweigung.
   Beispielsweise mit dem Wert:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resultierende Inhaltsseiten {#resultant-content-pages}

Für Seiten, die anhand bearbeitbarer Vorlagen erstellt wurden, gilt Folgendes:

* Sie werden mit einer Unterbaumstruktur erstellt, die aus `structure` und `initial` in der Vorlage zusammengeführt wird.

* Sie enthalten Verweise auf Informationen, die in der Vorlage und im Vorlagentyp enthalten sind. Dies wird mithilfe des Knotens `jcr:content` mit den folgenden Eigenschaften erreicht:

   * `cq:template`
Stellt den dynamischen Verweis auf die aktuelle Vorlage bereit und ermöglicht es, Änderungen an der Vorlage auf den aktuellen Seiten widerzuspiegeln.

   * `cq:templateType`
Stellt einen Verweis auf den Vorlagentyp bereit.

![chlimage_1-71](assets/chlimage_1-71.png)

Das obige Diagramm veranschaulicht, wie Vorlagen, Inhalte und Komponenten zusammenhängen:

* Controller - `/content/<my-site>/<my-page>`Die Zielseite, die auf die Vorlage verweist. Der Inhalt steuert den gesamten Prozess. Gemäß den Definitionen greift er auf die entsprechenden Vorlagen und Komponenten zu.

* Konfiguration - `/conf/<my-folder>/settings/wcm/templates/<my-template>`Die Seitenkonfiguration wird von der [Vorlage und den entsprechenden Inhaltsrichtlinien](#template-definitions) definiert.

* Modell – OSGi-Bundles Die [OSGi-Bundles](/help/sites-deploying/osgi-configuration-settings.md) implementieren die Funktionalität.

* View - `/apps/<my-site>/components`
On both the author and publish environments the content is rendered by [components](/help/sites-developing/components.md).

Beim Rendern einer Seite:

* **Vorlagen**:

   * The `cq:template` property of its `jcr:content` node will be referenced to access the template that corresponds to that page.

* **Komponenten**:

   * The page component will merge the `structure/jcr:content` tree of the template with the `jcr:content` tree of the page.

   * Die Seitenkomponente gestattet es dem Autor, nur die Knoten der Vorlagenstruktur zu bearbeiten, die als bearbeitbar gekennzeichnet sind (sowie jegliche untergeordneten Elemente).
   * Beim Rendern einer Komponente auf einer Seite wird der relative Pfad dieser Komponente vom Knoten `jcr:content` übernommen. Derselbe Pfad unter dem Knoten `policies/jcr:content` der Vorlage wird dann durchsucht.

      * The `cq:policy` property of this node points to the actual content policy (i.e. it holds the design configuration for that component).

      * Auf diese Weise können Sie mehrere Vorlagen verwenden, die dieselben Inhaltsrichtlinienkonfigurationen wiederverwenden.
