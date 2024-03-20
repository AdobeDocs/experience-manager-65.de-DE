---
title: Entwickeln mit CRXDE Lite
description: CRXDE Lite ist in Adobe Experience Manager (AEM) eingebettet und ermöglicht es Ihnen, Standardentwicklungsaufgaben im Browser durchzuführen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
docset: aem65
exl-id: 9e88ca55-ac3d-4857-b6b2-aeb732562664
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 54%

---

# Entwickeln mit CRXDE Lite{#developing-with-crxde-lite}

In diesem Abschnitt wird beschrieben, wie Sie Ihre Adobe Experience Manager (AEM)-Anwendung mithilfe von CRXDE Lite entwickeln.

Weitere Informationen zu den verschiedenen verfügbaren Entwicklungsumgebungen finden Sie in der Übersichtsdokumentation .

CRXDE Lite ist in AEM integriert und ermöglicht Ihnen die Durchführung von Standardentwicklungsaufgaben im Browser. Mit CRXDE Lite können Sie ein Projekt erstellen, Dateien (wie .jsp und .java), Ordner, Vorlagen, Komponenten, Dialogfelder, Knoten, Eigenschaften und Bundles erstellen und bearbeiten, während Sie die Protokollierung vornehmen.
CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den AEM haben. Oder wenn Sie eine Anwendung entwickeln, indem Sie die vordefinierten Komponenten und Java™-Bundles erweitern oder ändern oder wenn Sie keinen dedizierten Debugger benötigen, die Codevervollständigung und die Syntaxhervorhebung.

>[!NOTE]
>
>Ab AEM 6.5.5.0 ist der anonyme Zugriff auf CRXDE Lite nicht mehr möglich.
>Benutzer werden zum Anmeldebildschirm weitergeleitet.


>[!NOTE]
>
>Adobe empfiehlt die Verwendung der [AEM Entwicklertools für Eclipse](/help/sites-developing/aem-eclipse.md) und [AEM HTL Brackets-Erweiterung](/help/sites-developing/aem-brackets.md) während der Projektentwicklung.

## Erste Schritte mit CRXDE Lite {#getting-started-with-crxde-lite}

Gehen Sie für die ersten Schritte mit CRXDE Lite wie folgt vor:

1. Installieren Sie AEM.
1. Geben Sie in Ihrem Browser `https://<host>:<port>/crx/de` ein. Standardmäßig ist dies `https://localhost:4502/crx/de`.
1. Geben Sie Ihren **Benutzernamen** und Ihr **Kennwort** ein. Standardmäßig ist es `admin` und `admin`.

1. Klicken Sie auf **OK**.

Die Benutzeroberfläche von CRXDE Lite sieht in Ihrem Browser wie folgt aus:

![chlimage_1-18](assets/crx-interface.jpg)

Jetzt können Sie CRXDE Lite verwenden, um Ihr Programm zu entwickeln.

## Überblick über die Benutzeroberfläche {#overview-of-the-user-interface}

CRXDE Lite bietet folgende Funktionen:

<table>
 <tbody>
  <tr>
   <td>Obere Wechselleiste</td>
   <td>Wechseln Sie schnell zwischen CRXDE Lite, Package Manager und Package Share.</td>
  </tr>
  <tr>
   <td>Knotenpfad-Widget</td>
   <td><p>Zeigt den Pfad zum ausgewählten Knoten an.</p> <p>Sie können es auch verwenden, um zu einem Knoten zu springen, indem Sie den Pfad manuell eingeben oder ihn von woanders einfügen und die Eingabetaste drücken.</p> <p>Es bietet auch Unterstützung für die Suche nach Knoten mit einem bestimmten Knotennamen. Geben Sie den Namen des Knotens ein, den Sie suchen möchten, und warten Sie (oder drücken Sie auf das Suchsymbol auf der rechten Seite). Sie können beispielsweise die Zeichenfolge eingeben <em>oak</em> in das Widget ein, um zu sehen, wie es funktioniert. Wenn ein bestimmter Knoten in den Explorer geladen wird, wird die Liste angezeigt. Sie können den Pfad auswählen und die Eingabetaste drücken, um zu ihm zu navigieren. Dies funktioniert nur für die Knoten, die in die CRXDE-Clientanwendung im Browser geladen werden. Wenn Sie das gesamte Repository durchsuchen möchten, verwenden Sie „Tools“ &gt; „Abfrage“.</p> </td>
  </tr>
  <tr>
   <td>Explorer-Bereich</td>
   <td><p>Zeigt eine Baumstruktur aller Knoten im Repository an.</p> <p>Klicken Sie auf einen Knoten, damit dessen Eigenschaften im <strong>Eigenschaften</strong> Registerkarte. Nachdem Sie auf einen Knoten geklickt haben, können Sie eine Aktion in der Symbolleiste auswählen. Klicken Sie erneut auf den Knoten, um ihn umzubenennen.</p> <p>Baumstrukturnavigationsfilter (Fernglassymbol): Ermöglicht es Ihnen, im Repository die Knoten zu filtern, deren Name den Eingabetext enthält. Gilt nur für Knoten, die lokal geladen wurden.<br /> </p> </td>
  </tr>
  <tr>
   <td>Bearbeitungsbereich</td>
   <td><p>Registerkarte <strong>Home</strong>: Ermöglicht die Suche nach Inhalten und/oder Dokumentation sowie den Zugang zu Entwicklerressourcen (Dokumentation, Entwickler-Blog, Knowledgebase) und Support (Adobe-Homepage und Support Center).<br /> </p> <p>Doppelklicken Sie auf eine Datei im <strong>Explorer</strong> -Bereich, damit Sie den zugehörigen Inhalt anzeigen können. Beispielsweise eine .jsp- oder eine .java-Datei. Anschließend können Sie diesen ändern und die Änderungen speichern.</p> <p>Sobald eine Datei im <strong>Bearbeitungsbereich</strong> bearbeitet wurde, sind die folgenden Tools in der Symbolleiste verfügbar:<br /> </p> - <strong>In Struktur anzeigen</strong>: Zeigt die Datei in der Repository-Baumstruktur an.<br /> – <strong>Suchen/Ersetzen</strong>: Führt einen Suchen- oder Ersetzen-Vorgang durch.<br /> <br /> Doppelklicken Sie auf die Statuszeile des <strong>Bearbeiten</strong> -Bereich öffnet <strong>Gehe zu Zeile</strong> -Dialogfeld, damit Sie eine bestimmte Zeilennummer eingeben können, zu der Sie wechseln können.<br /> </td>
  </tr>
  <tr>
   <td>Registerkarte „Eigenschaften“<br /> </td>
   <td>Zeigt die Eigenschaften des Knotens an, den Sie ausgewählt haben. Sie können neue Eigenschaften hinzufügen oder die vorhandenen löschen.<br /> </td>
  </tr>
  <tr>
   <td>Registerkarte „Zugangssteuerung“</td>
   <td><p>Zeigt Berechtigungen basierend auf dem Pfad, der Repository-Ebene oder dem Prinzipal an.</p> <p>Die Berechtigungen werden wie folgt aufgeschlüsselt:</p> <p>- <strong>Gültige Richtlinie zur Zugriffssteuerung</strong>: Die Richtlinien, die auf die Auswahl angewendet werden können.</p> <p>- <strong>Richtlinien zur lokalen Zugriffssteuerung</strong>: Die lokal auf die Auswahl angewendeten Richtlinien.</p> <p>- <strong>Effektive Richtlinien zur Zugriffssteuerung</strong>: Die Richtlinien, die für die Auswahl angewendet werden, können lokal festgelegt oder von übergeordneten Knoten übernommen werden.</p> <p>Hinweis. Um die Zugriffssteuerungsinformationen überhaupt sehen zu können, muss der bei CRXDE Lite angemeldete Benutzer über Leseberechtigungen für ACL-Einträge verfügen. Der anonyme Benutzer kann diese Informationen standardmäßig nicht sehen - melden Sie sich als Administrator an, um die Informationen anzuzeigen, z. B.</p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Replikation“</td>
   <td><p>Anzeigen des Replikationsstatus des Knotens Sie können den Knoten replizieren und replizieren und löschen.</p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Konsole“<br /> </td>
   <td><p><strong>Server-Protokolle</strong>:</p> <p>Zeigt Protokollmeldungen an. Sie können die Protokollebene konfigurieren, die Konsole löschen, an der ausgewählten Bildlaufposition anheften und die Anzeige von Nachrichten aktivieren oder deaktivieren.<br /> </p> <p><strong>Versionskontrolle</strong>:</p> <p>Zeigt Versionskontrollmeldungen an.<br /> </p> </td>
  </tr>
  <tr>
   <td>Registerkarte „Build-Informationen“ <br /> </td>
   <td>Zeigt Informationen an, wenn ein Bundle erstellt wird.<br /> </td>
  </tr>
  <tr>
   <td>Aktualisieren<br /> </td>
   <td>Aktualisiert die Auswahl. Änderungen von anderen Benutzern werden in Ihrer Ansicht des Repositorys aktualisiert. Änderungen, die Sie vorgenommen haben, sind nicht betroffen.<br /> </td>
  </tr>
  <tr>
   <td>Alle speichern</td>
   <td><p><strong>Alle speichern</strong>:<br /> </p> <p>Speichert alle von Ihnen vorgenommenen Änderungen. Bis Sie auf "Speichern"klicken, sind die Änderungen temporär und gehen beim Beenden der Konsole verloren.</p> <p><strong>Zurück zur letzten Version</strong>:</p> <p>Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion an dem ausgewählten Knoten vorgenommen haben, und lädt dann den Status des Repositorys für den ausgewählten Knoten neu.</p> <p><strong>Alle zurücksetzen</strong>:</p> <p>Verwirft alle Änderungen, die Sie seit der letzten Speicheraktion im gesamten Repository vorgenommen haben, und lädt dann den Status des Repositorys neu.</p> </td>
  </tr>
  <tr>
   <td>Erstellen ...<br /> </td>
   <td><p>Dropdown-Menü, um Folgendes unter dem ausgewählten Knoten zu erstellen:<br /> </p> <p>- <strong>Knoten</strong>: Knoten mit einem beliebigen Knotentyp<br /> </p> <p>- <strong>Datei</strong>: nt:file-Knoten und dessen nt:ressource-Unterknoten</p> <p>- <strong>Ordner</strong>: nt:folder-Knoten</p> <p>- <strong>Vorlage</strong>: AEM-Vorlage</p> <p>- <strong>Komponente</strong>: AEM-Komponente</p> <p>- <strong>Dialogfeld</strong>: AEM-Dialogfeld</p> </td>
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
   <td>Fügt den kopierten Knoten unter dem ausgewählten Knoten ein.<br /> </td>
  </tr>
  <tr>
   <td>Verschieben ...<br /> </td>
   <td>Verschiebt den ausgewählten Knoten zu dem über das Dialogfeld festgelegten Knoten.</td>
  </tr>
  <tr>
   <td>Umbenennen ...<br /> </td>
   <td>Benennt den ausgewählten Knoten um.<br /> </td>
  </tr>
  <tr>
   <td>Mixins ...<br /> </td>
   <td>Ermöglicht das Hinzufügen von Mixin-Typen zum Knotentyp. Die Mixin-Typen werden meist verwendet, um erweiterte Funktionen wie Versionierung, Zugriffssteuerung, Referenzierung und Knotensperre hinzuzufügen.</td>
  </tr>
  <tr>
   <td>Tools<br /> </td>
   <td><p>Dropdown-Menü mit den folgenden Tools:</p> <p>- <strong>Server-Konfiguration</strong>: Zum Zugreifen auf die Felix-Konsole</p> <p>- <strong>Abfrage</strong>: Zum Abfragen des Repositorys</p> <p>- <strong>Berechtigungen</strong>: Zum Öffnen der Rechteverwaltung, in der Sie Berechtigungen anzeigen und hinzufügen können</p> <p>- <strong>Zugriffskontrolle testen ...</strong>: ein Ort, an dem Sie die Berechtigung für einen bestimmten Pfad und/oder Prinzipal testen können.</p> <p>- <strong>Knotentyp exportieren</strong>: Zum Exportieren von Knotentypen im System als CND-Notation</p> <p>- <strong>Knotentyp importieren</strong>: Zum Importieren von Knotentypen unter Verwendung der CND-Notation</p> <p>- <strong>SiteCatalyst Debugger installieren</strong>: Anweisungen zum Installieren von Analytics Debugger</p> </td>
  </tr>
  <tr>
   <td>Anmelde-Widget<br /> </td>
   <td><p>Zeigt die angemeldeten Benutzer und den Arbeitsbereich an, in dem sie angemeldet sind, z. B. admin@crx.default.</p> <p>Klicken Sie darauf, um sich als bestimmter Benutzer anzumelden oder sich erneut anzumelden. Wenn Sie keinen Arbeitsbereich für die Anmeldung angeben, werden Sie im Standardarbeitsbereich crx.default angemeldet.</p> <p>Wenn Sie das Repository als anonymen Benutzer durchsuchen möchten, verwenden Sie <strong>anonymous</strong> als Anmeldenamen und ein beliebiges Kennwort (z. B. ein Leerzeichen oder ein Punkt).<br /> </p> <p>Wenn Ihre Autorisierung nicht mehr gültig ist (z. B. abgelaufen), wird im Anmelde-Widget "<strong>Nicht autorisiert - Anmeldung..</strong>". Klicken Sie darauf, um sich erneut anzumelden.</p> </td>
  </tr>
 </tbody>
</table>

## Erstellen eines Ordners {#creating-a-folder}

So erstellen Sie einen Ordner mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Ordner, unter dem Sie den Ordner erstellen möchten, und wählen Sie **Erstellen ...**, dann **Ordner erstellen...**.

1. Geben Sie den **Namen** des Ordners ein und klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen einer Vorlage {#creating-a-template}

So erstellen Sie eine Vorlage mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Ordner, in dem Sie die Vorlage erstellen möchten, wählen Sie **Erstellen...** und dann **Vorlage erstellen...**.

1. Geben Sie die **Titel**, **Titel**, **Beschreibung**, **Ressourcentyp**, und **Ranking** der Vorlage. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Legen Sie die **zugelassenen Pfade** fest. Klicken Sie auf **Weiter**

1. Dieser Schritt ist optional: Legen Sie die **zugelassenen übergeordneten Elemente** fest. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Legen Sie die **zugelassenen untergeordneten Elemente** fest. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Folgendes wird erstellt:

* Ein Knoten vom Typ `cq:Template` mit Vorlageneigenschaften

* Ein untergeordneter Knoten vom Typ `cq:PageContent` mit Seiteninhaltseigenschaften

Sie können Eigenschaften zu Ihrer Vorlage hinzufügen: siehe [Erstellen einer Eigenschaft](#creating-a-property) Abschnitt.

## Erstellen einer Komponente {#creating-a-component}

Die Funktion, die hier beschrieben wird, ist nur verfügbar, wenn CQ5 installiert ist, d. h. wenn der Knoten `cq:Component` im Repository verfügbar ist.

So erstellen Sie eine Komponente mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Ordner, in dem die Komponente erstellt werden soll, wählen Sie **Erstellen...** und dann **Komponente erstellen...**.

1. Geben Sie die **Titel**, **Titel**, **Beschreibung**, **Superressourcentyp**, und **Gruppe** der Komponente. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Festlegen der Komponenteneigenschaften **Ist Container,** **Keine Dekoration**, **Zellname**, und **Dialogpfad**. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Legen Sie die Komponenteneigenschaft **Zugelassene übergeordnete Elemente** fest. Klicken Sie auf **Weiter**.

1. Dieser Schritt ist optional: Legen Sie die Komponenteneigenschaft **Zugelassene untergeordnete Elemente** fest. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Folgendes wird erstellt:

* Ein Knoten vom Typ `cq:Component`
* Komponenteneigenschaften
* Ein Komponenten-JSP-Skript

## Erstellen eines Dialogfelds {#creating-a-dialog}

So erstellen Sie ein Dialogfeld mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf die Komponente, in der Sie das Dialogfeld erstellen möchten, wählen Sie **Erstellen...** und dann **Dialogfeld erstellen...**.

1. Geben Sie das **Label** und den **Titel** ein. Klicken Sie auf **OK**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Es wird ein Dialogfeld mit der folgenden Struktur erstellt:

`dialog[cq:Dialog]/items[cq:Widget]/items[cq:WidgetCollection]/tab1[cq:Panel]`

Sie können das Dialogfeld nun an Ihre Anforderungen anpassen, indem Sie Eigenschaften ändern oder Knoten erstellen.

Sie können den Dialogfeld-Editor auch verwenden, um ein Dialogfeld zu bearbeiten. Durch Doppelklicken auf den Dialogfeldknoten in der CRXDE Lite wird der Editor geöffnet. Weitere Informationen über den Dialog-Editor finden Sie [hier](/help/sites-developing/dialog-editor.md).

## Erstellen eines Knotens {#creating-a-node}

So erstellen Sie einen Knoten mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsfenster mit der rechten Maustaste auf den Knoten, in dem Sie den Knoten erstellen möchten, und wählen Sie **Erstellen ...**, dann **Knoten erstellen...**.
1. Geben Sie den **Namen** und den **Typ** ein. Klicken Sie auf **OK**.
1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

Sie können den Knoten nun an Ihre Anforderungen anpassen, indem Sie Eigenschaften ändern oder Knoten erstellen.

>[!NOTE]
>
>Die meisten Bearbeitungsvorgänge, einschließlich Knoten erstellen, behalten alle Änderungen im Speicher bei und speichern sie nur beim Speichern im Repository (über die Schaltfläche &quot;Alle speichern&quot;). Einige Vorgänge wie das Verschieben werden jedoch automatisch beibehalten.
>
>Die Überprüfung, ob der neu erstellte Knoten vom Knotentyp des übergeordneten Knotens zugelassen ist, wird auch zuerst beim Speichern von Änderungen vom JCR-Repository durchgeführt. Wenn Sie beim Speichern eines Knotens eine Fehlermeldung erhalten, überprüfen Sie, ob die Inhaltsstruktur gültig ist (Sie können beispielsweise keine `nt:unstructured` Knoten als untergeordnetes Element von `nt:folder` Knoten).

## Erstellen einer Eigenschaft {#creating-a-property}

So erstellen Sie eine Eigenschaft mit CRXDE Lite:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie im Navigationsbereich den Knoten aus, an dem Sie die neue Eigenschaft hinzufügen möchten.
1. Im **Eigenschaften** im unteren Bereich die Registerkarte **Name**, die **Typ** und die **Wert**. Klicken Sie auf **Hinzufügen**.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Erstellen eines Skripts {#creating-a-script}

Erstellen eines Skripts:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Klicken Sie im Navigationsbereich mit der rechten Maustaste auf die Komponente, in der Sie das Skript erstellen möchten, wählen Sie **Erstellen ...** und dann **Datei erstellen ...**.

1. Geben Sie den **Dateinamen** mit der Erweiterung ein. Klicken Sie auf **OK**.

1. Die neue Datei wird als Registerkarte im Bearbeitungsbereich geöffnet.
1. Bearbeiten Sie die Datei.
1. Klicken Sie auf **Alle speichern**, um die Änderungen zu speichern.

## Exportieren und Importieren von Knotentypen {#exporting-and-importing-node-types}

Mit CRXDE Lite können Sie Knotentypdefinitionen importieren und/oder exportieren in [CND-Notation (Compact Namespace and Node Type Definition)](https://jackrabbit.apache.org/jcr/node-type-notation.html).

So exportieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie den gewünschten Knoten aus.
1. Wählen Sie **Tools** und dann **Knotentyp exportieren** aus.

1. Die Definition in cnd -Notation wird in Ihrem Browser angezeigt. Speichern Sie die Informationen bei Bedarf.

So importieren Sie eine Knotentypdefinition:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie **Tools** und dann **Knotentyp importieren...**.

1. Geben Sie die CND-Notation für die Definition in das Textfeld ein.
1. Aktivieren Sie **Update zulassen**, wenn Sie eine vorhandene Definition aktualisieren.
1. Wählen Sie **Importieren**.

## Protokollierung {#logging}

Mit CRXDE Lite können Sie die Datei anzeigen `error.log` , das sich im Dateisystem unter `<crx-install-dir>/crx-quickstart/server/logs` und filtern Sie sie mit der entsprechenden Protokollebene. Gehen Sie wie folgt vor:

1. Öffnen Sie CRXDE Lite in Ihrem Browser.
1. Wählen Sie auf der Registerkarte **Konsole** am unteren Rand des Fensters im Dropdown-Menü auf der rechten Seite **Serverprotokolle**.

1. Klicken Sie auf das **Stopp-Symbol**, um die Nachrichten anzuzeigen.

Sie haben folgende Möglichkeiten:

* Passen Sie die Protokollparameter in der Felix-Konsole an, indem Sie auf das Symbol **Protokollierungskonfigurationen** klicken.
* Löschen Sie die Meldungen, indem Sie auf das **Pinselsymbol** klicken.
* Veröffentlichen Sie die Nachricht an der Auswahl, indem Sie auf die **Pin** Symbol.
* Aktivieren oder deaktivieren Sie die Anzeige von Meldungen, indem Sie auf das **Stopp**-Symbol klicken.

## Zugriffssteuerung {#access-control}

>[!NOTE]
>
>Siehe [Verwaltung von Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md) für weitere Informationen.
