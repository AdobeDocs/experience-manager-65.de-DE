---
title: Entwickeln mit CRXDE Lite
seo-title: Entwickeln mit CRXDE Lite
description: CRXDE Lite ist in AEM integriert und ermöglicht Ihnen die Durchführung von Standardentwicklungsaufgaben im Browser
seo-description: CRXDE Lite ist in AEM integriert und ermöglicht Ihnen die Durchführung von Standardentwicklungsaufgaben im Browser
uuid: f4890354-d8b8-4fb9-af2f-3359f931f883
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 4537c1fb-f99c-42e2-a222-b037794bdb52
docset: aem65
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Entwickeln mit CRXDE Lite{#developing-with-crxde-lite}

In diesem Abschnitt wird beschrieben, wie Sie Ihre AEM-Anwendung mit CRXDE Lite entwickeln.

Weitere Informationen zu den verschiedenen verfügbaren Entwicklungsumgebungen finden Sie in der Übersichtsdokumentation.

CRXDE Lite ist in AEM integriert und ermöglicht Ihnen die Durchführung von Standardentwicklungsaufgaben im Browser. Mit CRXDE Lite können Sie ein Projekt erstellen und Dateien (wie .jsp und .java), Ordner, Vorlagen, Komponenten, Dialogfelder, Knoten, Eigenschaften und Pakete erstellen und bearbeiten, während Sie mit SVN protokollieren und integrieren.
CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den AEM-Server haben, wenn Sie eine Anwendung entwickeln, indem Sie die im Lieferumfang enthaltenen Komponenten und Java-Bundle erweitern oder modifizieren, oder wenn Sie keinen dedizierten Debugger, Code-Vervollständigung und Syntaxhervorhebung benötigen.

>[!NOTE]
>
>Standardmäßig können alle AEM-Benutzer auf CRXDE Lite zugreifen. If desired, [configure ACLs](/help/sites-administering/security.md#permissions-and-acls) for the following node so that only developers can access CRX DE Lite:
>
>`/libs/granite/crxde`

>[!NOTE]
>
>Während der Projektentwicklung wird empfohlen, die [AEM Developer Tools for Eclipse](/help/sites-developing/aem-eclipse.md) und die [AEM HTL Brackets Extension](/help/sites-developing/aem-brackets.md) zu verwenden.

## Erste Schritte mit CRXDE Lite {#getting-started-with-crxde-lite}

Um mit CRXDE Lite zu beginnen, gehen Sie wie folgt vor:

1. Installieren Sie AEM.
1. Geben Sie in Ihren Browser ein `https://<host>:<port>/crx/de`. Standardmäßig ist dies `https://localhost:4502/crx/de`der Fall.
1. Geben Sie Ihren **Benutzernamen** und Ihr **Kennwort** ein. By default it is `admin` and `admin`.

1. Klicken Sie auf **OK**.

Die Benutzeroberfläche von CRXDE Lite sieht in Ihrem Browser wie folgt aus:

![chlimage_1-18](assets/chlimage_1-18.png)

Jetzt können Sie CRXDE Lite verwenden, um Ihre Anwendung zu entwickeln.

## Überblick über die Benutzeroberfläche {#overview-of-the-user-interface}

CRXDE Lite bietet folgende Funktionen:

<table>
 <tbody>
  <tr>
   <td>Obere Wechselleiste</td>
   <td>Ermöglicht es Ihnen, schnell zwischen CRXDE Lite, Package Manager und Package Share zu wechseln.</td>
  </tr>
  <tr>
   <td>Knotenpfad-Widget</td>
   <td><p>Zeigt den Pfad zum aktuell ausgewählten Knoten.</p> <p>Sie können es auch verwenden, um zu einem Knoten zu springen, indem Sie den Pfad von Hand eingeben oder ihn von woanders einfügen und die Eingabetaste drücken.</p> <p>Es bietet auch Unterstützung für die Suche nach Knoten mit bestimmtem Knotennamen. Geben Sie den Namen des Knotens, den Sie suchen möchten, ein, und warten Sie (oder klicken Sie auf das Suchsymbol auf der rechten Seite). Sie können z. B. versuchen, die Zeichenfolge <em>oak</em> in das Widget einzugeben, um zu sehen, wie dies funktioniert. Wenn ein bestimmte Knoten im Explorer-Fenster geladen werden, wird die Liste angezeigt und Sie können den Pfad auswählen und die Eingabetaste drücken, um dorthin zu navigieren. Beachten Sie, dass dies nur für die Knoten funktioniert, die derzeit in der CRXDE-Client-Anwendung im Browser geladen sind. Wenn Sie das gesamte Repository durchsuchen möchten, verwenden Sie „Tools“ &gt; „Anfrage“.</p> </td>
  </tr>
  <tr>
   <td>Explorer-Fenster</td>
   <td><p>Zeigt eine Baumstruktur aller Knoten im Repository an.</p> <p>Klicken Sie auf einen Knoten, um seine Eigenschaften auf der Registerkarte <strong>Eigenschaften</strong> anzuzeigen. Nachdem Sie auf einen Knoten geklickt haben, können Sie eine Aktion in der Symbolleiste auswählen. Klicken Sie erneut auf den Knoten, um ihn umzubenennen.</p> <p>Baumstrukturnavigationsfilter (Fernglassymbol): ermöglicht es Ihnen, die Knoten im Repository zu filtern, deren Name den Eingabetext enthält. Gilt nur für Knoten, die lokal geladen wurden.<br /> </p> </td>
  </tr>
  <tr>
   <td>Bearbeitungsfenster</td>
   <td><p>Registerkarte <strong>Home</strong>: ermöglicht die Suche nach Inhalt und/oder Dokumentation und Zugang zu Entwicklerressourcen (Dokumentation, Entwicklerblog, Wissensdatenbank) und Support (Adobe-Homepage und Support-Center).<br /> </p> <p>Doppelklicken Sie im <strong>Explorer-Fenster</strong> auf eine Datei, wie z. B. eine .jsp- oder eine .java-Datei, um deren Inhalt anzuzeigen. Anschließend können Sie sie ändern und die Änderungen speichern.</p> <p>Sobald eine Datei im <strong>Bearbeitungsfenster</strong> bearbeitet wurde, sind die folgenden Werkzeuge in der Symbolleiste verfügbar:<br /> </p> - <strong>In Struktur anzeigen: </strong>zeigt die Datei in der Repository-Baumstruktur an.<br /> - <strong>Suchen/Ersetzen...</strong>: führen Sie Suchen oder Ersetzungen durch.<br /><br /> Durch einen Doppelklick auf die Statuszeile des <strong>Bearbeitungsfensters</strong> öffnen Sie das Dialogfeld <strong>Zu Zeile wechseln</strong>, in dem Sie eine bestimmte Zeilennummer eingeben können, um dorthin zu gelangen.<br /> </td>
  </tr>
  <tr>
   <td>Registerkarte „Eigenschaften“<br /> </td>
   <td>Zeigt die Eigenschaften des Knotens, den Sie ausgewählt haben. Sie können neue Eigenschaften hinzufügen oder die vorhandenen löschen.<br /> </td>
  </tr>
  <tr>
   <td>Registerkarte „Zugriffssteuerung“</td>
   <td><p>Zeigt Berechtigungen basierend auf dem aktuellen Pfad, Repository-Level oder Prinzipal an.</p> <p>Die Berechtigungen werden aufgeschlüsselt in</p> <p>- <strong>Gültige Richtlinie für die Zugriffssteuerung</strong>: Die Richtlinien, die auf die aktuelle Auswahl angewendet werden können.</p> <p>- <strong>Richtlinien zur lokalen Zugriffssteuerung</strong>: Die aktuellen Richtlinien, die lokal auf die aktuelle Auswahl angewendet werden.</p> <p>- <strong>Gültige Richtlinien zur Zugriffssteuerung</strong>: Die aktuellen Richtlinien, die auf die aktuelle Auswahl angewendet werden, sie können lokal festgelegt oder von übergeordneten Knoten übernommen werden.</p> <p>Hinweis. Um die Zugriffssteuerungsinformationen überhaupt zu sehen, muss der Benutzer, der sich bei CRXDE Lite angemeldet hat, über Berechtigungen zum Lesen von ACL-Einträgen verfügen. Der anonyme Benutzer kann diese Informationen nicht standardmäßig sehen - melden Sie sich z. B. als Admin an, um die Informationen zu sehen.</p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Replikation“</td>
   <td><p>Zeigt den Replikationsstatus des aktuellen Knotens an. Sie können den aktuellen Knoten nachbilden oder nachbilden und löschen.</p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Konsole“<br /> </td>
   <td><p><strong>Serverprotokolle</strong>:</p> <p>Zeigt Protokollmeldungen an. Sie können die Protokollebene konfigurieren, die Konsole löschen, an der ausgewählten Bildlaufposition anheften und die Anzeige von Meldungen aktivieren/deaktivieren.<br /> </p> <p><strong>Versionskontrolle</strong>:</p> <p>Zeigt Versionssteuerungsnachrichten an.<br /> </p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Build-Informationen“<br /> </td>
   <td>Zeigt Informationen an, wenn ein Paket erstellt wird.<br /> </td>
  </tr>
  <tr>
   <td>Aktualisieren<br /> </td>
   <td>Aktualisiert die aktuelle Auswahl. Änderungen von anderen Benutzern werden in Ihrer Ansicht des Repositorys aktualisiert. Änderungen, die Sie vorgenommen haben, sind nicht betroffen.<br /> </td>
  </tr>
  <tr>
   <td>Alle speichern</td>
   <td><p><strong>Alle speichern</strong>:<br /> </p> <p>Speichert alle von Ihnen vorgenommenen Änderungen. Solange Sie nicht auf „Speichern“ klicken, sind die Änderungen vorübergehend und gehen verloren, wenn Sie die Konsole verlassen.</p> <p><strong>Zurück zur letzten Version</strong>:</p> <p>Verwirft alle Änderungen, die Sie seit dem letzten Speichervorgang auf dem ausgewählten Knoten vorgenommen haben, lädt dann den aktuellen Status des Repositorys für den ausgewählten Knoten erneut.</p> <p><strong>Alle zurücksetzen</strong>:</p> <p>Verwirft alle Änderungen, die Sie seit dem letzten Speichervorgang im gesamten Repository vorgenommen haben, lädt dann den aktuellen Status des Repositorys erneut.</p> </td>
  </tr>
  <tr>
   <td>Erstellen...<br /> </td>
   <td><p>Dropdown-Menü, um Folgendes unter dem ausgewählten Knoten zu erstellen:<br /> </p> <p>- <strong>Knoten</strong>: ein Knoten mit einem beliebigen Knotentyp<br /> </p> <p>- <strong>File</strong>: nt:file node and its nt:resource subnode</p> <p>- <strong>Ordner</strong>: nt:folder-Knoten</p> <p>- <strong>Vorlage</strong>: AEM-Vorlage</p> <p>- <strong>Komponente</strong>: AEM-Komponente</p> <p>- <strong>Dialog</strong>: AEM-Dialogfeld</p> </td>
  </tr>
  <tr>
   <td>Löschen<br /> </td>
   <td>Löscht den ausgewählten Knoten.<br /> </td>
  </tr>
  <tr>
   <td>Kopieren</td>
   <td>Kopiert den ausgewählten Knoten.<br /> </td>
  </tr>
  <tr>
   <td>Einfügen<br /> </td>
   <td>Pastes the copied node under the selected node.<br /> </td>
  </tr>
  <tr>
   <td>Verschieben...<br /> </td>
   <td>Verschiebt den ausgewählten Knoten zu dem Knoten, der über das Dialogfeld festgelegt wurde.</td>
  </tr>
  <tr>
   <td>Umbenennen...<br /> </td>
   <td>Benennt den ausgewählten Knoten um.<br /> </td>
  </tr>
  <tr>
   <td>Mixins...<br /> </td>
   <td>Ermöglicht es Ihnen, dem Knotentyp Mixin-Typen hinzuzufügen. Die Mixin-Typen werden meist verwendet, um erweiterte Funktionen wie Versionierung, Zugriffssteuerung, Referenzierung und Knotensperre hinzuzufügen.</td>
  </tr>
  <tr>
   <td>Team<br /> </td>
   <td><p>Dropdown-Menü, um Standardaufgaben im Zusammenhang mit der Versionssteuerung auszuführen:</p> <p>- <strong>Aktualisieren</strong> des Repositorys vom SVN-Server</p> <p>- <strong>Bestätigen</strong> lokaler Änderungen auf dem SVN-Server </p> <p>- <strong>Status</strong> des aktuellen Knotens anzeigen</p> <p>- <strong>Rekursiven Status</strong> der Unterstruktur des aktuellen Knotens anzeigen</p> <p>- <strong>Auschecken</strong> einer Arbeitskopie vom SVN-Server</p> <p>- <strong>Exportieren</strong>eines Projekts vom SVN-Server (ohne eine Arbeitskopie zu erstellen)</p> <p>- <strong>Importieren</strong> eines Projekts aus dem Repository auf den SVN-Server<br /> </p> <p>Beachten Sie, dass Sie als Benutzer mit ausreichenden Berechtigungen angemeldet sein müssen, um einige der Aufgaben (insbesondere die, die in das lokale Repository schreiben) ausführen zu können.<br /> </p> </td>
  </tr>
  <tr>
   <td>Tools<br /> </td>
   <td><p>Dropdown-Menü mit den folgenden Tools:</p> <p>- <strong>Serverkonfiguration...</strong>: zum Zugriff auf die Felix-Konsole.</p> <p>- <strong>Abfrage...</strong>: für Abfragen im Repository.</p> <p>- <strong>Berechtigungen...</strong>: um die Rechteverwaltung zu öffnen, in der Sie Berechtigungen anzeigen und hinzufügen können.</p> <p>- <strong>Zutrittssteuerung testen...</strong>: ein Ort, an dem Sie die Berechtigung für einen bestimmten Pfad und/oder Prinzipal testen können.</p> <p>- <strong>Knotentyp exportieren</strong>: um Knotentypen im System als CND-Notation zu exportieren.</p> <p>- <strong>Knotentyp importieren...</strong>: um Knotentypen unter Verwendung von CND-Notation zu importieren.</p> <p>- <strong>SiteCatalyst Debugger installieren...</strong>: Anweisungen zum Installieren von Analytics-Debugger.</p> </td>
  </tr>
  <tr>
   <td>Login-Widget<br /> </td>
   <td><p>Zeigt die aktuell angemeldeten Benutzer und den Arbeitsbereich an, bei dem sie angemeldet sind, z. B. admin@crx.default.</p> <p>Klicken Sie es, um sich als bestimmter Benutzer anzumelden bzw. erneut anzumelden. Wenn Sie keinen Arbeitsbereich angeben, um sich anzumelden, werden Sie beim Standardarbeitsbereich, crx.default, angemeldet.</p> <p>Wenn Sie das Repository als anonymer Benutzer durchsuchen möchten, verwenden Sie <strong>Anonym</strong> als Anmeldenamen und ein beliebiges Kennwort (z. B. ein Leerzeichen oder einen Punkt).<br /> </p> <p>Wenn Ihre Autorisierung nicht mehr gültig ist (weil sie z. B. abgelaufen ist), zeigt das Login-Widget <strong>Nicht autorisiert – Anmelden...</strong>. Klicken Sie darauf, um sich erneut anzumelden.</p> </td>
  </tr>
 </tbody>
</table>

## Erstellen eines Projekts {#creating-a-project}

Mit CRXDE Lite können Sie ein Arbeitsprojekt in drei Mausklicks erstellen. The project wizard creates a new project under `/apps`, some content under `/conten`t and a package wrapping all the project the content under `/etc/packages`. Das Projekt kann sofort verwendet werden, um eine Beispielseite mit **Hello World** zu rendern, basierend auf einem jsp-Skript, das eine Eigenschaft aus dem Repository rendert und eine Java-Klasse aufruft, um Text zu rendern.

So erstellen Sie ein Projekt mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf einen Knoten, wählen Sie **Erstellen...** und dann **Projekt erstellen...**.
Note: you can right-click any node in the tree navigation, as the new project nodes are, by design, created below `/apps,` `/content` and `/etc/packages`.

1. Definieren Sie Folgendes:

   * **Projektname** - Der Projektname wird verwendet, um die neuen Knoten und das Bundle, z. B. `myproject`, zu erstellen.

   * **Java-Paket** - das Präfix des Java-Paketnamens, z. B. `com.mycompany`.

1. Klicken Sie auf **Erstellen**.
1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Um auf die Beispielseite zuzugreifen, die **Hello World** anzeigt, geben Sie in Ihrem Browser die folgende Adresse ein:

`https://localhost:4502/content/<project-name>.html`

Die Seite **Hello World** basiert auf einem Inhaltsknoten, der ein jsp-Skript durch die Eigenschaft `sling:resourceType` abruft. Das Skript liest die Eigenschaft `jcr:title` aus dem Repository und ruft den Hauptinhalt ab, indem eine Methode der SampleUtil-Klasse aufgerufen wird, die im Projektbundle verfügbar ist.

Folgende Knoten werden erstellt:

* `/apps/<project-name>`: den Anwendungscontainer.
* `/apps/<project-name>/components`: der Komponenten-Container, der die html.jsp-Beispieldatei enthält, die zum Rendern einer Seite verwendet wird.

* `/apps/<project-name>/src`: den Bundles-Container mit einem Beispielprojektpaket.

* `/apps/<project-name>/install`: den kompilierten Bundles-Container mit dem kompilierten Beispiel-Projektpaket.
* `/content/<project-name>`: den Inhaltsbehälter.
* /etc/packages/&lt;Java-Suffix>/&lt;Projektname>.zip, ein Paket, das alle Projekt-Anwendungen und -Inhalte enthält. Sie können es verwenden, um das Projekt weiter zu entwickeln (z. B. in anderen Umgebungen) oder über Package Share zu teilen.

Die Struktur sieht in CRXDE Lite wie folgt aus: Ein Projekt namens **myproject** und ein Java-Paketsuffix namens **mycompany**:

![chlimage_1-19](assets/chlimage_1-19.png)

![chlimage_1-20](assets/chlimage_1-20.png)

## Erstellen eines Ordners {#creating-a-folder}

So erstellen Sie einen Ordner mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. **Klicken Sie im Navigationsbereich mit der rechten Maustaste auf den Ordner, unter dem Sie den neuen Ordner erstellen möchten, wählen Sie** Erstellen ...**und dann Ordner** erstellen ... .

1. Geben Sie den **Namen** des Ordners ein und klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen einer Vorlage {#creating-a-template}

So erstellen Sie eine Vorlage mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Ordner, in dem Sie die Vorlage erstellen möchten, wählen Sie **Erstellen...** und dann **Vorlage erstellen...**.

1. Geben Sie **Beschriftung**, **Titel**, **Beschreibung**, **Ressourcentyp** und **Rangfolge** der Vorlage ein. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Legen Sie die **zugelassenen Pfade** fest. Klicken Sie auf **Weiter**

1. This step is optional: set the **Allowed Parents**. Klicken Sie auf **Weiter**.

1. This step is optional: set the **Allowed Children**. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Folgendes wird erstellt:

* A node of type `cq:Template` with Template properties

* Ein untergeordneter Knoten vom Typ `cq:PageContent` mit Seiteninhaltseigenschaften

Sie können Ihrer Vorlage Eigenschaften hinzufügen: weitere Informationen finden Sie unter [Erstellen einer Eigenschaft](#creating-a-property).

## Erstellen einer Komponente {#creating-a-component}

Die Funktion, die hier beschrieben wird, ist nur verfügbar, wenn CQ5 installiert ist, d. h. wenn der Knoten `cq:Component` im Repository verfügbar ist.

So erstellen Sie eine Komponente mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Ordner, in dem die Komponente erstellt werden soll, wählen Sie **Erstellen...** und dann **Komponente erstellen...**.

1. Geben Sie **Beschriftung**, **Titel**, **Beschreibung**, **Superressourcentyp** und die **Gruppe** der Komponente ein. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: legen Sie die Komponenteneigenschaften fest: **Ist Container**, **Keine Auszeichnung**, **Zellenname** und **Dialogpfad**. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: legen Sie die Komponenteneigenschaft **Zugelassene übergeordnete Elemente** fest. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: legen Sie die Komponenteneigenschaft **Zugelassene untergeordnete Elemente** fest. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Folgendes wird erstellt:

* A node of type `cq:Component`
* Komponenteneigenschaften
* Ein Komponenten-.jsp-Skript

## Erstellen eines Dialogfelds {#creating-a-dialog}

So erstellen Sie ein Dialogfeld mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. **Klicken Sie im Navigationsbereich mit der rechten Maustaste auf die Komponente, in der Sie das Dialogfeld erstellen möchten, wählen Sie** Erstellen ...**und dann Dialogfeld** erstellen ... .

1. Geben Sie **Beschriftung** und **Titel** ein. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Ein Dialogfeld mit folgender Struktur wird erstellt:

`dialog[cq:Dialog]/items[cq:Widget]/items[cq:WidgetCollection]/tab1[cq:Panel]`

Sie können das Dialogfeld jetzt Ihren Anforderungen anpassen, indem Sie die Eigenschaften ändern oder neue Knoten erstellen.

Sie können den Dialogfeld-Editor auch verwenden, um ein Dialogfeld zu bearbeiten. Mit einem Doppelklick auf den Dialogfeldknoten in CRXDE Lite wird der Editor geöffnet. Weitere Informationen über den Dialogfeld-Editor finden Sie [hier](/help/sites-developing/dialog-editor.md).

## Erstellen eines Knotens {#creating-a-node}

So erstellen Sie einen Knoten mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Knoten, in dem Sie den neuen Knoten erstellen möchten, wählen Sie **Erstellen...** und dann **Knoten erstellen…**.
1. Geben Sie den **Namen** und den **Typ** ein. Klicken Sie auf **OK**.
1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Jetzt können Sie den Knoten an Ihre Anforderungen anpassen, indem Sie die Eigenschaften ändern oder neue Knoten erstellen.

>[!NOTE]
>
>Die meisten Bearbeitungsvorgänge, einschließlich der Knotenerstellung, behalten alle Änderungen im Speicher und speichern sie erst beim Speichern im Repository (über die Schaltfläche „Alle speichern“). Einige Vorgänge wie Verschieben werden jedoch automatisch beibehalten.
>
>Die Prüfung, ob der neu erstellte Knoten vom Knotentyp des übergeordneten Knoten zugelassen ist, wird auch zuerst vom JCR-Repository ausgeführt, wenn Änderungen gespeichert werden sollen. Wenn Sie beim Speichern eines Knotens eine Fehlermeldung erhalten, überprüfen Sie, ob die Inhaltsstruktur gültig ist (Sie können z. B. keinen Knoten `nt:unstructured` als untergeordneten Knoten des Knotens `nt:folder` erstellen).

## Erstellen einer Eigenschaft {#creating-a-property}

So erstellen Sie eine Eigenschaft mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie im Navigationsbereich den Knoten aus, an dem Sie die neue Eigenschaft hinzufügen möchten.
1. Geben Sie auf der Registerkarte **Eigenschaften** im unteren Fensterbereich den **Namen**, den **Typ** und den **Wert** ein. Klicken Sie auf **Hinzufügen**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen eines Skripts {#creating-a-script}

So erstellen Sie ein neues Skript:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf die Komponente, in der Sie das Skript erstellen möchten, wählen Sie **Erstellen...** und dann **Datei erstellen…**.

1. Geben Sie den **Dateinamen** mit der Erweiterung ein. Klicken Sie auf **OK**.

1. Die neue Datei wird als Registerkarte im Bearbeitungsfenster geöffnet.
1. Bearbeiten Sie die Datei.
1. Klicken Sie auf **Alle speichern**, um die Änderungen zu speichern.

## Verwalten eines Bundles {#managing-a-bundle}

Mit CRXDE Lite ist es einfach, ein OSGI-Bundle zu entwerfen, ihm Java-Klassen hinzuzufügen und es zu erstellen. Das Bundle wird dann im OSGI-Container automatisch installiert und gestartet.

This section describes how to create a `Test` bundle with a `HelloWorld` Java class that displays **Hello World!** anzeigt in Ihrem Browser erstellen, wenn die Ressource angefordert wird.

### Erstellen eines Bundles {#creating-a-bundle}

So erstellen Sie ein Testbundle mit CRXDE Lite:

1. Erstellen Sie in CRXDE Lite das Projekt `myapp` mit dem [Projektassistenten](#creating-a-project). Unter anderem werden die folgenden Knoten erstellt:

   * `/apps/myapp/src`
   * `/apps/myapp/install`

1. `/apps/myapp/src`Klicken Sie mit der rechten Maustaste auf den Ordner `Test` , der das **Bundle enthalten wird, wählen Sie** Erstellen ...**und dann Bündel** erstellen ... .

1. Legen Sie die Bundleeigenschaften wie folgt fest:

   * Symbolic Bundle Name: `com.mycompany.test.TestBundle`

   * Bundle-Name: `Test Bundle`
   * Bündelbeschreibung:

      ```
      This is my Test Bundle
      ```

   * Paket:

      ```
      com.mycompany.test
      ```
   Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Der Assistent erstellt die folgenden Elemente:

* Die Node `com.mycompany.test.TestBundle` des Typs `nt:folder.` &quot;It&quot;ist der Bundle-Container-Knoten.

* Die Datei `com.mycompany.test.TestBundle.bnd`. Sie fungiert als Bereitstellungsdeskriptor für Ihr Bundle und besteht aus einer Reihe von Kopfzeilen.

* Die Ordnerstrukturen:

   * `src/main/java/com/mycompany/test`. Umfasst die Pakete und die Java-Klassen.

   * `src/main/resources`. Enthält die Ressourcen, die innerhalb des Bundles verwendet werden.

* Die `Activator.java` Datei. Dies ist die optionale Listener-Klasse, die über Start- und Stopp-Ereignisse des Bundles benachrichtigt wird.

In der folgenden Tabelle sind alle Eigenschaften der.bnd-Datei, deren Werte und Beschreibungen aufgelistet:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Wert (bei Bündelbildung)<br /> </strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Exportpaket:</td>
   <td><p>*</p> <p>Hinweis: dieser Wert muss an die Spezifität des Pakets angepasst werden.</p> </td>
   <td>Der Header Export-Paket definiert exportierte Pakete aus dem Bundle (kommagetrennte Liste der Pakete). The exported packages constitute the public<br /> view of the bundle.<br /> </td>
  </tr>
  <tr>
   <td>Importpaket:</td>
   <td><p>*</p> <p>Hinweis: dieser Wert muss an die Spezifität des Pakets angepasst werden.</p> </td>
   <td>Der Header "Paket importieren"definiert importierte Pakete für das Bundle (kommagetrennte Liste von Paketen)</td>
  </tr>
  <tr>
   <td>Privates Paket:</td>
   <td><p>*</p> <p>Hinweis: dieser Wert muss an die Spezifität des Pakets angepasst werden.</p> </td>
   <td>Die Kopfzeile Private-Package definiert private Pakete für das Bundle (durch Komma getrennte Liste der Pakete). Die privaten Pakete bilden die interne Implementierung.<br /> </td>
  </tr>
  <tr>
   <td>Bundle-Name:</td>
   <td>Testpaket</td>
   <td>Definiert einen kurzen, für Menschen lesbaren Namen für das Bundle</td>
  </tr>
  <tr>
   <td>Bundle-Beschreibung:</td>
   <td>Dies ist mein Test Bundle</td>
   <td>Definiert eine kurze, für Menschen lesbare Beschreibung des Bundles</td>
  </tr>
  <tr>
   <td>Bundle-SymbolicName:</td>
   <td>com.meinunternehmen.test.TestBundle</td>
   <td>Gibt einen eindeutigen, nicht lokalisierbaren Namen für das Bundle an</td>
  </tr>
  <tr>
   <td>Bundle-Version:</td>
   <td>1.0.0-SNAPSHOT</td>
   <td>Gibt die Version des Bundles an</td>
  </tr>
  <tr>
   <td>Bundle-Aktivator:</td>
   <td>com.mycompany.test.Activator</td>
   <td>Gibt den Namen der optionalen Lister-Klasse an, die über Bundle-Start- und -Stopp-Ereignisse benachrichtigt werden soll</td>
  </tr>
 </tbody>
</table>

Weitere Informationen zum bnd-Format finden Sie im [bnd-Dienstprogramm](https://bndtools.org/), das von CRXDE zum Erstellen von OSGI-Bundles verwendet wird.

### Erstellen einer Java-Klasse {#creating-a-java-class}

So erstellen Sie die Java-Klasse `HelloWorld` innerhalb des Testbundles:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. `Activator.java`Klicken Sie im Navigationsbereich mit der rechten Maustaste auf den Knoten, der die `/apps/myapp/src/com.mycompany.test.TestBundle/src/main/java` Datei enthält ( **), wählen Sie** Erstellen ...**und dann Datei** erstellen ... .

1. Name the file `HelloWorld.java`. Klicken Sie auf **OK**.

1. Die Datei `HelloWorld.java`-Datei wird im Bearbeitungsfenster geöffnet.
1. Fügen Sie die folgenden Zeilen hinzu `HelloWorld.java`:

   ```
     package com.mycompany.test;
   
     public class HelloWorld {
     public String getString(){
     return "Hello World!";
     }
     }
   ```
1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

### Erstellen eines Bundles {#building-a-bundle}

So erstellen Sie das Testbundle:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf die.bnd-Datei, wählen Sie **Tools** und dann **Bundle**.

Der Assistent zum Erstellen von Bundles:

* Kompiliert die Java-Klassen.
* Erstellt die .jar-Datei, die die kompilierten Java-Klassen und Ressourcen enthält, und platziert sie im Ordner `myapp/install`.
* Installiert und startet das Bundle im OSGI-Container.

Um die Wirkung des Testpakets zu sehen, erstellen Sie eine Komponente, die die Java-Methode HelloWorld.getString() und eine Ressource verwendet, die von dieser Komponente gerendert wird:

1. Create the component `mycomp` under `myapp/components`.

1. Bearbeiten `mycomp.jsp` und ersetzen Sie den Code durch die folgenden Zeilen:

   ```
     <%@ page import="com.mycompany.test.HelloWorld"%><%
     %><%@ include file="/libs/foundation/global.jsp"%><%
     %><% HelloWorld hello = new HelloWorld();%><%
     %>
     <html>
     <body>
     <b><%= hello.getString() %></b><br>
     </body>
     </html>
   ```

1. Create the resource `test_node` of type `nt:unstructured` under `/content`.

1. For `test_node`, create the following property: Name = `sling:resourceType`, Type = `String`, Value = `myapp/components/mycomp`.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

1. Fordern Sie im Browser `test_node`Folgendes an: `https://<hostname>:<port>/content/test_node.html`.

1. Eine Seite mit der Nachricht **Hello World!** wird angezeigt.

## Exportieren und Importieren von Knotentypen {#exporting-and-importing-node-types}

With CRXDE Lite you can import and/or export node type definitions in [CND (Compact Namespace and Node Type Definition) notation](https://jackrabbit.apache.org/jcr/node-type-notation.html).

So exportieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie Ihren gewünschten Knoten aus.
1. Wählen Sie **Tools** und dann **Knotentyp exportieren**.

1. Die Definition wird in CND-Notation in Ihrem Browser angezeigt. Speichern Sie die Informationen (falls erforderlich).

So importieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie **Tools** und dann **Knotentyp importieren...**.

1. Geben Sie die CND-Notation für die Definition in das Textfeld ein.
1. Aktivieren Sie **Aktualisierung zulassen**, wenn Sie eine vorhandene Definition aktualisieren.
1. Wählen Sie **Importieren**.

## Protokollierung {#logging}

With CRXDE Lite you can display the file `error.log` that is located on the file system at `<crx-install-dir>/crx-quickstart/server/logs` and filter it with the appropriate log level. Gehen Sie wie folgt vor:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie auf der Registerkarte **Konsole** am unteren Rand des Fensters im Dropdown-Menü auf der rechten Seite **Serverprotokolle** aus.

1. Klicken Sie auf das **Stopp-Symbol**, um die Nachrichten anzuzeigen.

Sie haben folgende Möglichkeiten:

* Adjust the log parameters in the Felix Console by clicking the **Logging Configurations** icon.
* Löschen Sie die Meldungen, indem Sie auf das **Pinselsymbol** klicken.
* Heften Sie die Nachricht an der aktuellen Auswahl an, indem Sie auf das **Pin-Symbol** klicken.
* Aktivieren oder deaktivieren Sie die Anzeige von Meldungen, indem Sie auf das **Stopp-Symbol** klicken.

## Zugriffssteuerung {#access-control}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verwaltung von Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).
