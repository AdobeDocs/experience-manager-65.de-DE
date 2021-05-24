---
title: Arbeiten mit Paketen
seo-title: Arbeiten mit Paketen
description: Lernen Sie die Grundlagen für den Umgang mit Paketen in AEM.
seo-description: Lernen Sie die Grundlagen für den Umgang mit Paketen in AEM.
uuid: cba76a5f-5d75-4d63-a0f4-44c13fa1baf2
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 6694a135-d1e1-4afb-9f5b-23991ee70eee
docset: aem65
exl-id: e8929d7c-9920-4c02-95a9-6f7f7a365203
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3934'
ht-degree: 80%

---

# Arbeiten mit Paketen{#how-to-work-with-packages}

Pakete bieten Ihnen die Möglichkeit, Repository-Inhalte zu importieren und zu exportieren. Sie können Pakete beispielsweise verwenden, um neue Funktionen zu installieren, Inhalte zwischen Instanzen auszutauschen und Repository-Inhalte zu sichern.

Sie können von den folgenden Seiten aus auf Pakete zugreifen und/oder Pakete verwalten:

* [Package Manager](#package-manager), mit dessen Hilfe Sie die Pakete auf der lokalen AEM-Instanz verwalten.

* [Softwareverteilung](#software-distribution), ein zentralisierter Server, der sowohl öffentlich verfügbare als auch private Pakete für Ihr Unternehmen enthält. Die öffentlichen Pakete können Hotfixes, neue Funktionen, Dokumentationen usw. enthalten.

Sie können Pakete zwischen Package Manager, Software Distribution und Ihrem Dateisystem übertragen.

## Was sind Pakete? {#what-are-packages}

Ein Paket ist eine Zip-Datei mit Repository-Inhalten in Form einer Dateisystem-Serialisierung (auch „Vault“-Serialisierung genannt). Dies ermöglicht eine benutzerfreundliche und einfach zu bearbeitende Darstellung der Dateien und Ordner.

Pakete enthalten sowohl Seiteninhalte als auch projektspezifische Inhalte, die mithilfe von Filtern ausgewählt werden.

Ein Paket enthält auch Vault-Metadaten, einschließlich der Filterdefinitionen und Import-Konfigurationsinformationen. Zusätzliche Inhaltseigenschaften (die nicht für die Paketextraktion verwendet werden) können in das Paket aufgenommen werden, z. B. eine Beschreibung, ein visuelles Bild oder ein Symbol. Diese Eigenschaften dienen nur dem Inhaltspaket-Verbraucher und Informationszwecken.

>[!NOTE]
>
>Pakete repräsentieren die aktuelle Version der Inhalte zum Zeitpunkt der Erstellung des Pakets. Sie umfassen keine früheren Versionen der Inhalte, die AEM im Repository speichert.

Sie können die folgenden Aktionen hinsichtlich der Pakete ausführen:

* Neue Pakete erstellen und dabei Paketeinstellungen und Filter nach Bedarf definieren
* Paketinhalte in einer Vorschau anzeigen (vor der Erstellung)
* Pakete erstellen
* Paketinformationen anzeigen
* Inhalte des Pakets anzeigen (nach der Erstellung)
* Definition vorhandener Pakete ändern
* Vorhandene Pakete neu erstellen
* Pakete neu eingliedern
* Pakete von AEM in das Dateisystem herunterladen
* Hochladen von Paketen aus Ihrem Dateisystem in Ihre lokale AEM-Instanz
* Validieren von Paketinhalten vor der Installation
* Führen Sie eine Trockenlaufinstallation durch
* Pakete installieren (AEM installiert Pakete nach dem Hochladen nicht automatisch)
* Pakete löschen
* Pakete wie Hotfixes aus der Software Distribution-Bibliothek herunterladen
* Laden Sie Pakete in den unternehmensinternen Abschnitt der Software Distribution-Bibliothek hoch.

## Paketinformationen {#package-information}

Eine Paketdefinition umfasst verschiedene Arten von Informationen:

* [Paketeinstellungen](#package-settings)
* [Paketfilter](#package-filters)
* [Paket-Screenshots](#package-screenshots)
* [Paketsymbole](#package-icons)

### Paketeinstellungen {#package-settings}

Sie können eine Vielzahl von Paketeinstellungen bearbeiten, um Aspekte wie die Paketbeschreibung, verwandte Fehler, Abhängigkeiten und Anbieterinformationen zu definieren.

Rufen Sie das Dialogfeld **Paketeinstellungen** über die Schaltfläche **Bearbeiten** auf, wenn Sie ein Paket [erstellen](#creating-a-new-package) oder [bearbeiten](#viewing-and-editing-package-information). Es enthält drei zur Konfiguration dienende Registerkarten. Klicken Sie nach dem Vornehmen der Änderungen auf **OK**, um diese Einstellungen zu speichern.

![packagesedit](assets/packagesedit.png)

| **Feld** | **Beschreibung** |
|---|---|
| Name | Der Name des Pakets. |
| Gruppe | Der Name der Gruppe, der das Paket hinzugefügt werden soll, um Pakete zu organisieren. Geben Sie den Namen für eine neue Gruppe ein oder wählen Sie eine vorhandene Gruppe aus. |
| Version | Text für die benutzerdefinierte Version. |
| Beschreibung | Eine kurze Beschreibung des Pakets. HTML-Markup kann zum Formatieren verwendet werden. |
| Miniaturansicht | Das Symbol, das mit der Paketliste angezeigt wird. Klicken Sie auf „Durchsuchen“, um eine lokale Datei auszuwählen. |

![chlimage_1-108](assets/chlimage_1-108.png)

<table>
 <tbody>
  <tr>
   <th><strong>Feld</strong></th>
   <th><strong>Beschreibung</strong></th>
   <th><strong>Format/Beispiel</strong></th>
  </tr>
  <tr>
   <td>Name</td>
   <td>Name des Anbieters.</td>
   <td><em>AEM Geometrixx<br /> </em></td>
  </tr>
  <tr>
   <td>URL</td>
   <td>URL des Anbieters.</td>
   <td><em>https://www.aem-geometrixx.com</em></td>
  </tr>
  <tr>
   <td>Verknüpfung</td>
   <td>Paketspezifischer Link zu einer Anbieterseite.</td>
   <td><em>https://www.aem-geometrixx.com/mypackage.html</em></td>
  </tr>
  <tr>
   <td>Erfordert<br /> </td>
   <td>
    <ul>
     <li>Admin: Wählen Sie diese Option aus, wenn das Paket nur von einem Konto mit Administratorrechten installiert werden kann.</li>
     <li>Neu starten: Wählen Sie diese Option aus, wenn der Server nach der Installation des Pakets neu gestartet werden muss.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>AC-Verwaltung</td>
   <td><p>Legen Sie fest, wie die im Paket definierten Zugriffssteuerungsinformationen beim Importieren des Pakets verarbeitet werden:</p>
    <ul>
     <li><strong>Groß-/Kleinschreibung</strong></li>
     <li><strong>Überschreiben</strong></li>
     <li><strong>Zusammenführen</strong></li>
     <li><strong>Clear</strong></li>
     <li><strong>Zusammenführung beibehalten</strong></li>
    </ul> <p>Der Standardwert lautet <strong>Ignorieren</strong>.</p> </td>
   <td>
    <ul>
     <li><strong>Ignorieren</strong>: Die ACLs werden im Repository beibehalten.</li>
     <li><strong>Überschreiben</strong>: Die ACLs werden im Repository überschrieben.</li>
     <li><strong>Zusammenführen</strong>: Beide ACL-Sätze werden zusammengeführt.</li>
     <li><strong>Entfernen</strong>: Die ACLs werden entfernt.</li>
     <li><strong>Zusammenführung beibehalten</strong>: Die Zugriffssteuerung im Inhalt wird mit der im Paket zusammengeführt, indem die Zugriffssteuerungseinträge von Prinzipalen, die nicht im Inhalt vorhanden sind, hinzugefügt werden.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

![packagesdependencies](assets/packagesdependencies.png)

| **Feld** | **Beschreibung** | **Format/Beispiel** |
|---|---|---|
| Getestet mit | Der Produktname und die Version, auf die dieses Paket ausgerichtet ist oder mit der es kompatibel ist. | *AEM 6* |
| Behobene Fehler/Probleme | Ein Textfeld, in dem Sie Details zu Fehlern auflisten können, die mit diesem Paket behoben wurden. Listen Sie die einzelnen Fehler in separaten Zeilen auf. | bug-nr summary |
| Abhängig von | Listet Abhängigkeitsinformationen auf, die beachtet werden müssen, wenn andere Pakete erforderlich sind, damit das aktuelle Paket erwartungsgemäß ausgeführt werden kann. Dieses Feld ist bei Verwendung von Hotfixes wichtig. | groupId:name:version |
| Ersetzt | Eine Liste veralteter Pakete, die dieses Paket ersetzt. Überprüfen Sie vor der Installation, ob dieses Paket alle erforderlichen Inhalte von den veralteten Paketen beinhaltet, sodass keine Inhalte überschrieben werden. | groupId:name:version |

### Paketfilter {#package-filters}

Filter identifizieren die Repository-Knoten, die in das Paket eingeschlossen werden sollen. Eine **Filterdefinition** legt die folgenden Informationen fest:

* Den **Stammpfad** der einzufügenden Inhalte
* **** Regeln, die bestimmte Knoten unter dem Stammpfad ein- oder ausschließen.

Filter können keine oder mehrere Regeln enthalten. Wenn keine Regeln definiert sind, enthält das Paket alle Inhalte unter dem Stammpfad.

Sie können eine oder mehrere Filterdefinitionen für ein Paket definieren. Verwenden Sie mehr als einen Filter, um Inhalte aus mehreren Stammpfaden einzuschließen.

![chlimage_1-109](assets/chlimage_1-109.png)

In der folgenden Tabelle sind diese Regeln und einige Beispiele beschrieben:

<table>
 <tbody>
  <tr>
   <th> Regeltyp</th>
   <th>Beschreibung </th>
   <th>Beispiel </th>
  </tr>
  <tr>
   <td> include</td>
   <td>Sie können einen Pfad definieren oder einen regulären Ausdruck verwenden, um alle Knoten anzugeben, die Sie einschließen möchten.<br /> <br /> Wird ein Verzeichnis eingeschlossen:
    <ul>
     <li>werden dieses Verzeichnis <i>und</i> alle Dateien und Ordner in diesem Verzeichnis (d. h. die gesamte Unterstruktur) eingeschlossen</li>
     <li>werden andere Dateien oder Ordner unter dem angegebenen Stammpfad <strong>nicht</strong> eingeschlossen</li>
    </ul> </td>
   <td>/libs/sling/install(/.*)? </td>
  </tr>
  <tr>
   <td> exclude</td>
   <td>Sie können einen Pfad angeben oder einen regulären Ausdruck verwenden, um alle Knoten anzugeben, die Sie ausschließen möchten.<br /> <br /> Wird ein Verzeichnis ausgeschlossen, werden dieses Verzeichnis <i>und</i> alle Dateien und Ordner in diesem Verzeichnis (d. h. die gesamte Unterstruktur) ausgeschlossen.<br /> </td>
   <td>/libs/wcm/foundation/components(/.*)?</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Ein Paket kann mehrere Filterdefinitionen enthalten, sodass sich Knoten von verschiedenen Orten einfach in einem Paket kombinieren lassen.

Paketfilter werden in den meisten Fällen bei der [Erstellung des Pakets](#creating-a-new-package) definiert, sie können aber auch zu einem späteren Zeitpunkt bearbeitet werden (anschließend sollte das Paket neu erstellt werden).

### Paket-Screenshots {#package-screenshots}

Sie können Screenshots an das Paket anhängen, um eine visuelle Darstellung vom Erscheinungsbild der Inhalte bereitzustellen. So können Sie beispielsweise Screenshots von neuen Funktionen bereitstellen.

### Paketsymbole  {#package-icons}

Sie können auch ein Symbol an das Paket anhängen, um eine schnelle visuelle Darstellung von dem bereitzustellen, was im Paket enthalten ist. Dieses wird dann in der Paketliste angezeigt und ermöglicht Ihnen, das Paket oder die Klasse des Pakets auf einfache Weise zu identifizieren.

Da ein Paket ein Symbol enthalten kann, gelten folgende Konventionen für offizielle Pakete:

>[!NOTE]
>
>Um Verwirrungen zu vermeiden, sollten Sie ein aussagekräftiges Symbol für das Paket und keines der offiziellen Symbole verwenden.

Offizielles Hotfix-Paket:

![](do-not-localize/chlimage_1-28.png)

Offizielles AEM-Installations- oder AEM-Erweiterungspaket:

Offizielle Funktionspakete:

![](do-not-localize/chlimage_1-29.png)

## Package Manager {#package-manager}

Der Package Manager verwaltet die Pakete auf der lokalen AEM-Installation. Nachdem Sie [die erforderlichen Berechtigungen zugewiesen haben,](#permissions-needed-for-using-the-package-manager) können Sie den Package Manager für verschiedene Aktionen, u. a. zum Konfigurieren, Erstellen, Herunterladen und Installieren von Paketen, verwenden. Folgende wichtige Elemente sind zu konfigurieren:

* [Paketeinstellungen](#package-settings)
* [Paketfilter](#package-filters)

### Für die Verwendung des Package Manager erforderlichen Berechtigungen {#permissions-needed-for-using-the-package-manager}

Wenn Sie Benutzern das Recht zum Erstellen, Ändern, Hochladen und Installieren von Paketen gewähren wollen, müssen Sie ihnen die entsprechenden Berechtigungen für die folgenden Orte zuweisen:

* **/etc/packages** (umfassende Rechte außer „Löschen“)
* den Knoten, der die Paketinhalte beinhaltet

Weitere Informationen zum Ändern von Berechtigungen finden Sie in [Festlegen von Berechtigungen](/help/sites-administering/security.md#setting-page-permissions).

### Erstellen eines neuen Pakets  {#creating-a-new-package}

So erstellen Sie eine neue Paketdefinition:

1. Klicken Sie im AEM Begrüßungsbildschirm auf **Pakete** (oder doppelklicken Sie in der Konsole **Tools** auf **Pakete**).

1. Wählen Sie dann **Package Manager** aus.
1. Klicken Sie auf **Paket erstellen**.

   >[!NOTE]
   >
   >Wenn Ihre Instanz über viele Pakete verfügt, ist möglicherweise eine Ordnerstruktur vorhanden, sodass Sie vor der Erstellung des neuen Pakets zum erforderlichen Zielordner navigieren können.

1. Im Dialogfeld:

   ![packagesnew](assets/packagesnew.png)

   Geben Sie Folgendes ein:

   * **Gruppenname**

      Der Name der Zielgruppe (oder des Ordners). Gruppen sollen Ihnen bei der Organisation Ihrer Pakete helfen.

      Das System legt einen Ordner für die Gruppe an, sollte sie noch nicht vorhanden sein. Wenn Sie keinen Gruppennamen eingeben, wird das Paket in der Hauptpaketliste („Startseite“ > „Pakete“) erstellt.

   * **Paket-Name**

      Der Name des neuen Pakets. Wählen Sie einen beschreibenden Namen aus, über den Sie (und andere) die Inhalte des Pakets leicht identifizieren können.

   * **Version**

      Ein Textfeld zur Eingabe einer Version. Diese wird an den Paketnamen angehängt, um den Namen der ZIP-Datei zu bilden.
   Klicken Sie auf **OK**, um das Paket zu erstellen.

1. AEM listet das neue Paket im entsprechenden Gruppenordner auf.

   ![packagesitem](assets/packagesitem.png)

   Klicken Sie auf das Symbol oder den Paketnamen, um es zu öffnen.

   ![packagesitemclicked](assets/packagesitemclicked.png)

   >[!NOTE]
   >
   >Sie können ggf. zu einem späteren Zeitpunkt zu dieser Seite zurückkehren.

1. Klicken Sie auf **Bearbeiten**, um die [Paketeinstellungen](#package-settings) zu bearbeiten.

   Hier können Sie Informationen hinzufügen und/oder bestimmte Einstellungen festlegen. Dazu gehören z. B. eine Beschreibung, das [Symbol](#package-icons), verwandte Fehler und das Hinzufügen von Anbieterdetails.

   Klicken Sie auf **OK**, wenn Sie mit der Bearbeitung der Einstellungen fertig sind.

1. Fügen Sie dem Paket bei Bedarf **[Screenshots](#package-screenshots)** hinzu. Eine Instanz ist verfügbar, wenn das Paket erstellt wurde. Fügen Sie weitere hinzu, falls dies erforderlich sein sollte, indem Sie die Option **Paket-Screenshot** im Sidekick verwenden.

   Fügen Sie das Ist-Bild hinzu, indem Sie auf die Bildkomponente im Bereich **Screenshots** doppelklicken, ein Bild hinzufügen und auf **OK** klicken.

1. Definieren Sie die **[Paketfilter](#package-filters)**, indem Sie die Instanzen der **Filterdefinition** aus dem Sidekick ziehen und dann darauf doppelklicken, um sie zur Bearbeitung zu öffnen:

   ![packagesfilter](assets/packagesfilter.png)

   Geben Sie Folgendes an:

   * **Stammpfad** Die zu packenden Inhalte. Dabei kann es sich um den Stamm einer Unterstruktur handeln.
   * **Regeln** Regeln sind optional. Bei einfachen Paketdefinitionen ist es nicht notwendig, Regeln zum Ein- oder Ausschließen festzulegen.

      Bei Bedarf können Sie Regeln zum [**Einschließen** oder **Ausschließen**](#package-filters) definieren, um die Paketinhalte genau festzulegen.

      Fügen Sie Regeln mithilfe des **+**-Symbols hinzu und entfernen Sie Regeln mithilfe des **-**-Symbols. Regeln werden entsprechend ihrer Reihenfolge angewendet. Positionieren Sie sie daher mit den Schaltflächen **Nach oben** und **Nach unten** wie gewünscht.
   Klicken Sie dann auf **OK**, um den Filter zu speichern.

   >[!NOTE]
   >
   >Sie können so viele Filterdefinitionen verwenden, wie Sie brauchen. Achten Sie jedoch darauf, dass sie nicht in Konflikt miteinander stehen. Vergewissern Sie sich mithilfe der **Vorschau**, welche Inhalte im Paket enthalten sind.

1. Sie können mithilfe der **Vorschau** feststellen, welche Inhalte im Paket enthalten sind. Bei Auswahl dieser Option wird der Erstellungsprozess in einem Probelauf durchgeführt und anschließend alles aufgelistet, was zum Paket hinzugefügt wird, wenn es tatsächlich erstellt wird.
1. [Sie können nun das Paket ](#building-a-package)erstellen.

   >[!NOTE]
   >
   >Es ist nicht zwingend erforderlich, das Paket an diesem Punkt zu erstellen, Sie können dies auch zu einem späteren Zeitpunkt tun.

### Erstellen eines Pakets {#building-a-package}

In den meisten Fällen wird das Paket erstellt, wenn [die Paketdefinition erstellt wird](#creating-a-new-package), Sie können aber auch zu einem späteren Zeitpunkt zurückkehren, um das Paket entweder zu erstellen oder neu zu erstellen. Dies ist beispielsweise dann nützlich, wenn sich die Inhalte innerhalb des Repositorys geändert haben.

>[!NOTE]
>
>Bevor Sie das Paket erstellen, kann es hilfreich sein, die Inhalte des Pakets in einer Vorschau anzuzeigen. Klicken Sie dazu auf **Vorschau**.

1. Öffnen Sie die Paketdefinition im **Package Manager** (klicken Sie auf das Paketsymbol oder den Paketnamen).

1. Klicken Sie auf **Erstellen**. Es wird ein Dialogfeld mit der Aufforderung zur Bestätigung angezeigt, dass Sie das Paket erstellen wollen.

   >[!NOTE]
   >
   >Dies ist insbesondere dann wichtig, wenn Sie ein Paket neu erstellen, da die Paketinhalte dabei überschrieben werden.

1. Klicken Sie auf **OK**. AEM erstellt das Paket und listet währenddessen alle Inhalte auf, die dem Paket hinzugefügt werden. Nachdem der Vorgang abgeschlossen ist, zeigt AEM eine Bestätigung an, dass das Paket erstellt wurde. Zudem aktualisiert AEM die Paketlisteninformationen (wenn Sie das Dialogfeld schließen).

### Neueingliedern eines Pakets {#rewrapping-a-package}

Nach der Erstellung kann das Paket bei Bedarf neu eingegliedert werden.

Bei einer Neueingliederung werden die Paketinformationen *ohne* Änderung der Paketinhalte geändert. Zu den Paketinformationen gehören die Miniaturansicht, die Beschreibung usw., d. h. alle Informationen, die Sie im Dialogfeld **Paketeinstellungen** bearbeiten können (klicken Sie zum Öffnen des Dialogfelds auf **Bearbeiten**).

Ein wichtiger Anwendungsfall für die Umverpackung ist die Vorbereitung eines Pakets. Es könnte beispielsweise sein, dass Sie ein vorhandenes Paket haben, das Sie für andere freigeben möchten. Bevor Sie dies tun, möchten Sie eine Miniaturansicht und eine Beschreibung hinzufügen. Anstatt das gesamte Paket mit allen Funktionen neu zu erstellen (was möglicherweise einige Zeit in Anspruch nimmt und das Risiko birgt, dass das Paket nicht mit dem Original identisch ist), können Sie es neu eingliedern und nur die Miniaturansicht und die Beschreibung hinzufügen.

1. Öffnen Sie die Paketdefinition im **Package Manager** (klicken Sie auf das Paketsymbol oder den Paketnamen).

1. Klicken Sie auf **Bearbeiten** und aktualisieren Sie die **[Paketeinstellungen](#package-settings)** nach Bedarf. Klicken Sie zum Speichern auf **OK**.

1. Klicken Sie auf **Erneut verpacken**. Daraufhin wird ein Bestätigungsdialogfeld angezeigt.

### Anzeigen und Bearbeiten von Paketinformationen {#viewing-and-editing-package-information}

So zeigen Sie Informationen zu einer Paketdefinition an oder bearbeiten sie:

1. Navigieren Sie im Package Manager zum anzuzeigenden Paket.
1. Klicken Sie auf das Paketsymbol des anzuzeigenden Pakets. Daraufhin wird die Paketseite aufgerufen, auf der Informationen zur Paketdefinition aufgelistet sind:

   ![packagesitemclicked-1](assets/packagesitemclicked-1.png)

   >[!NOTE]
   >
   >Sie können das Paket über diese Seite auch bearbeiten und bestimmte Aktionen hinsichtlich des Pakets durchführen.
   >
   >Welche Schaltflächen verfügbar sind, hängt davon ab, ob das Paket bereits erstellt wurde oder nicht.

1. **Wurde das Paket bereits erstellt, klicken Sie auf „Inhalte“, woraufhin ein Fenster mit einer Liste der gesamten Inhalte des Pakets geöffnet wird:**

### Anzeigen von Paketinhalten und Testen der Installation {#viewing-package-contents-and-testing-installation}

Nach der Erstellung eines Pakets können Sie dessen Inhalte anzeigen:

1. Navigieren Sie im Package Manager zum anzuzeigenden Paket.
1. Klicken Sie auf das Paketsymbol des anzuzeigenden Pakets. Daraufhin wird die Paketseite aufgerufen, auf der Informationen zur Paketdefinition aufgelistet sind.

1. Klicken Sie zum Anzeigen der Inhalte auf **Inhalte**, woraufhin ein Fenster mit einer Liste der gesamten Inhalte des Pakets geöffnet wird:

   ![packgescontents](assets/packgescontents.png)

1. Klicken Sie auf **Testinstallation**, um einen Probedurchlauf der Installation durchzuführen. Nachdem Sie die Aktion bestätigt haben, wird ein Fenster geöffnet, in dem die Ergebnisse wie bei einer echten Installation angezeigt werden:

   ![packagestestinstall](assets/packagestestinstall.png)

### Herunterladen von Paketen in das Dateisystem {#downloading-packages-to-your-file-system}

In diesem Abschnitt wird beschrieben, wie Sie mit dem **Package Manager** ein Paket von AEM in das Dateisystem herunterladen.

1. Klicken Sie im AEM Begrüßungsbildschirm auf **Pakete** und wählen Sie dann **Package Manager** aus.
1. Navigieren Sie zum Paket, das Sie herunterladen möchten.

   ![packagesdownload](assets/packagesdownload.png)

1. Klicken Sie auf den Link, der sich aus dem Namen der ZIP-Datei (unterstrichen) für das Paket ergibt, das Sie herunterladen möchten. Beispiel: `export-for-offline.zip`.

   AEM lädt das Paket auf Ihren Computer herunter (mithilfe eines standardmäßigen Browser-Download-Dialogfelds).

### Hochladen von Paketen von dem Dateisystem {#uploading-packages-from-your-file-system}

Mit einem Package-Upload können Sie ein Paket aus Ihrem Dateisystem in den AEM Package Manager hochladen.
So laden Sie ein Paket hoch:

1. Navigieren Sie zum **Package Manager**. Klicken Sie dann auf den Gruppenordner, in den Sie das Paket hochladen wollen.

   ![packagesuploadbutton](assets/packagesuploadbutton.png)

1. Klicken Sie auf **Paket hochladen**.

   ![packagesuploaddialog](assets/packagesuploaddialog.png)

   * **File**

      Sie können entweder den Dateinamen direkt eingeben oder **Durchsuchen... verwenden.** Dialogfeld, um das erforderliche Paket aus Ihrem lokalen Dateisystem auszuwählen (klicken Sie nach der Auswahl auf **OK**).

   * **Hochladen erzwingen**

      Wenn bereits ein Paket mit diesem Namen existiert, können Sie auf dieses klicken, um den Upload zu erzwingen (und das vorhandene Paket zu überschreiben).
   Klicken Sie auf **OK**, damit das neue Paket hochgeladen und in der Package Manager-Liste angezeigt wird.

   >[!NOTE]
   >
   >Denken Sie daran, [das Paket zu installieren](#installing-packages), damit die Inhalte in AEM verfügbar sind.

### Validieren von Paketen  {#validating-packages}

Vor der Installation eines Pakets sollten Sie seinen Inhalt überprüfen. Da Pakete überlagerte Dateien unter `/apps` ändern und/oder ACLs hinzufügen, ändern und entfernen können, ist es oft nützlich, diese Änderungen vor der Installation zu validieren.

#### Validierungsoptionen {#validation-options}

Der Validierungsmechanismus kann folgende Merkmale des Pakets überprüfen:

* OSGi-Paketimporte
* Überlagerungen
* ACLs

Diese Optionen werden nachfolgend beschrieben.

* **OSGi-Paketimporte validieren**

   **Prüfumfang**

   Diese Validierung prüft das Paket auf JAR-Dateien (OSGi-Bundles), extrahiert deren `manifest.xml`-Datei (die die versionierten Abhängigkeiten enthält, die für das OSGi-Bundle erforderlich sind) und stellt sicher, dass die AEM-Instanz die Abhängigkeiten mit den richtigen Versionen exportiert.

   **Berichterstellung**

   Alle versionierten Abhängigkeiten, die von der AEM nicht erfüllt werden können, werden im **Aktivitätsprotokoll** des Package Managers aufgelistet.

   **Fehlerstatus**

   Sind die Abhängigkeiten nicht erfüllt, werden die OSGi-Bundles im Paket mit diesen Abhängigkeiten nicht gestartet. Dies führt zu einer fehlerhaften Anwendungsbereitstellung, da alle auf dem nicht gestarteten OSGi-Bundle basierenden Prozesse nicht ordnungsgemäß funktionieren.

   **Fehlerbehebung**

   Um die Fehler zu beheben, die auf OSGi-Bundles mit nicht erfüllten Abhängigkeiten basieren, muss die Abhängigkeitsversion in diesen Bundles angepasst werden.

* **Überlagerungen bestätigen**

   **Prüfumfang**

   Diese Validierung ermittelt, ob das zu installierende Paket eine Datei enthält, die bereits in der AEM-Zielinstanz überlagert ist.

   Wenn beispielsweise eine vorhandene Überlagerung unter `/apps/sling/servlet/errorhandler/404.jsp` vorhanden ist, ein Paket, das `/libs/sling/servlet/errorhandler/404.jsp` enthält, wird die vorhandene Datei unter `/libs/sling/servlet/errorhandler/404.jsp` geändert.

   **Berichterstellung**

   Solche Überlagerungen werden im **Aktivitätsprotokoll** von Package Manager beschrieben.

   **Fehlerstatus**

   Ein Fehlerstatus bedeutet, dass das Paket versucht, eine bereits überlagerte Datei bereitzustellen. Die Änderungen im Paket werden somit durch die Überlagerung überschrieben (und „ausgeblendet“) und nicht umgesetzt.

   **Fehlerbehebung**

   Um dieses Problem zu beheben, muss der Betreuer der Überlagerungsdatei in `/apps` die Änderungen an der überlagerten Datei in `/libs` überprüfen, die erforderlichen Änderungen in die Überlagerung ( `/apps`) übernehmen und die überlagerte Datei erneut bereitstellen.

   >[!NOTE]
   >
   >Beachten Sie, dass der Validierungsmechanismus keine Möglichkeit zur Abstimmung bietet, wenn der überlagerte Inhalt ordnungsgemäß in die Überlagerungsdatei integriert wurde. Daher berichtet diese Validierung auch weiterhin über Konflikte, selbst wenn die erforderlichen Änderungen vorgenommen wurden.

* **ACLs bestätigen**

   **Prüfumfang**

   Diese Validierung prüft, welche Berechtigungen hinzugefügt werden, wie diese verarbeitet werden (zusammenführen/ersetzen) und ob sie sich auf aktuelle Berechtigungen auswirken.

   **Berichterstellung**

   Die Berechtigungen werden im **Aktivitätsprotokoll** von Package Manager beschrieben.

   **Fehlerstatus**

   Die Angabe von expliziten Fehlern ist nicht möglich. Die Validierung gibt lediglich an, ob durch Installieren des Pakets neue ACL-Berechtigungen hinzugefügt oder aktuelle beeinträchtigt werden.

   **Fehlerbehebung**

   Anhand der von der Validierung bereitgestellten Informationen können die betroffenen Knoten in CRXDE überprüft und die ACLs nach Bedarf im Paket angepasst werden.

   >[!CAUTION]
   >
   >Als Best Practice wird empfohlen, dass Pakete keine Auswirkungen auf von AEM bereitgestellte ACLs haben sollten, da dies möglicherweise zu unerwartetem Produktverhalten führen kann.

#### Durchführen der Validierung  {#performing-validation}

Die Validierung von Paketen kann auf zweierlei Weise erfolgen:

* Über die Benutzeroberfläche von Package Manager
* Über HTTP POST-Anfragen, wie z. B. mit cURL

>[!NOTE]
>
>Führen Sie die Validierung stets nach dem Hochladen und vor dem Installieren eines Pakets durch.

**Paketvalidierung über Package Manager**

1. Öffnen Sie den Paketmanager unter `https://<server>:<port>/crx/packmgr` .
1. Wählen Sie das Paket in der Liste aus und wählen Sie dann **Mehr** aus der Dropdown-Liste aus der Überschrift und dann **Validate** aus dem Dropdown-Menü.

   >[!NOTE]
   >
   >Führen Sie diesen Schritt nach dem Hochladen des Inhaltspakets aber vor seiner Installation aus.

1. Aktivieren Sie im angezeigten modalen Dialogfeld das Kontrollkästchen des gewünschten Validierungstyps und starten Sie die Validierung durch Klicken auf **Überprüfen**. Alternativ können Sie auf **Abbrechen** klicken.

1. Die ausgewählten Validierungen werden ausgeführt. Die Ergebnisse werden im Aktivitätsprotokoll von Package Manager angezeigt.

**Paketvalidierung über HTTP POST-Anfrage**

Die POST-Anfrage hat folgendes Format.

```
https://<host>:<port>/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls
```

>[!NOTE]
>
>Der Parameter `type` kann eine ungeordnete und durch Kommas getrennte Liste aus folgenden Elementen sein:
>
>* `osgiPackageImports`
>* `overlays`
>* `acls`

>
>
Der Wert von `type` wird standardmäßig auf `osgiPackageImports` gesetzt, wenn er nicht übergeben wird.

Im Folgenden finden Sie ein Beispiel für die Verwendung von cURL zur Ausführung einer Paketvalidierung.

1. Wenn Sie cURL verwenden, führen Sie eine Anweisung ähnlich der folgenden aus:

   ```shell
   curl -v -X POST --user admin:admin -F file=@/Users/SomeGuy/Desktop/core.wcm.components.all-1.1.0.zip 'http://localhost:4502/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls'
   ```

1. Die gewünschte Validierung wird ausgeführt und die Antwort als JSON-Objekt zurückgesendet.

>[!NOTE]
>
>Die Antwort auf eine HTTP POST-Anfrage ist ein JSON-Objekt mit den Ergebnissen der Validierung.

### Installieren von Paketen {#installing-packages}

Nachdem Sie ein Paket hochgeladen haben, müssen Sie dessen Inhalte installieren. Damit die Paketinhalte installiert und verwendet werden können, müssen sie:

* in AEM geladen (entweder [aus Ihrem Dateisystem hochgeladen](#uploading-packages-from-your-file-system) oder heruntergeladen von [Softwareverteilung](#software-distribution))

* installiert werden.

>[!CAUTION]
>
>Beim Installieren eines Pakets können vorhandene Inhalte überschrieben oder gelöscht werden. Laden Sie ein Paket nur hoch, wenn Sie sich sicher sind, dass dadurch keine benötigten Inhalte gelöscht oder überschrieben werden.
>
>Um die Inhalte oder Auswirkungen eines Pakets anzuzeigen, können Sie:
>
>* Führen Sie eine Testinstallation des Pakets durch, ohne den Inhalt zu ändern:
   >  Öffnen Sie das Paket (klicken Sie auf das Paketsymbol oder den Paketnamen) und klicken Sie auf **Installation testen**.
   >
   >
* Eine Liste der Paketinhalte anzeigen:
   >  Öffnen Sie das Paket und klicken Sie auf **Inhalt**.

>



>[!NOTE]
>
>Unmittelbar vor der Installation des Pakets wird ein Snapshot-Paket erstellt, das die Inhalte enthält, die überschrieben werden.
>
>Dieser Snapshot wird wieder installiert, wenn Sie das Paket deinstallieren.

>[!CAUTION]
>
>Wenn Sie digitale Assets installieren, müssen Sie:
>
>* als Erstes den WorkflowLauncher deaktivieren.
   >  Verwenden Sie die Menüoption „Komponenten“ der OSGi-Konsole zur Deaktivierung der Option `com.day.cq.workflow.launcher.impl.WorkflowLauncherImpl`.
   >
   >
* als Nächstes den WorkflowLauncher reaktivieren, wenn die Installation abgeschlossen ist.
>
>
Die Deaktivierung des WorkflowLauncher gewährleistet, dass die Assets nach der Installation nicht (versehentlich) vom Asset-Importer-Framework verändert werden.

1. Navigieren Sie im Package Manager zum Paket, das Sie installieren wollen.

   Die Schaltfläche **Installieren** wird neben den Paketen angezeigt, die noch nicht installiert wurden.

   >[!NOTE]
   >
   >Alternativ können Sie das Paket öffnen, indem Sie auf das zugehörige Symbol klicken und dann auf die Schaltfläche **Installieren** zugreifen.

1. Klicken Sie auf **Installieren**, um die Installation zu starten. Es wird ein Dialogfeld mit einer Liste aller vorgenommenen Änderungen und der Aufforderung zur Bestätigung angezeigt. Wenn Sie fertig sind, klicken Sie im Dialogfeld auf **Schließen**.

   Das Wort **Installiert** wird neben dem Paket angezeigt, nachdem es installiert wurde.

### Dateisystem-basierte(r) Upload und Installation  {#file-system-based-upload-and-installation}

Es gibt eine alternative Methode, um Pakete auf Ihre Instanz hochzuladen und dort zu installieren. In Ihrem Dateisystem befindet sich neben Ihrer JAR- und `license.properties`-Datei ein Ordner `crx-quicksart` . Sie müssen einen Ordner mit dem Namen `install` unter `crx-quickstart` erstellen. Sie haben dann Folgendes: `<aem_home>/crx-quickstart/install`

In diesem „install“-Ordner können Sie die Pakete direkt hinzufügen. Sie werden automatisch auf Ihre Instanz hochgeladen und dort installiert. Anschließend können Sie die Pakete im Package Manager sehen.

Wird Ihre Instanz ausgeführt und Sie fügen dem `install`-Ordner ein Paket hinzu, werden der Upload und die Installation direkt auf der Instanz gestartet. Wird Ihre Instanz nicht ausgeführt, werden die von Ihnen dem `install`-Ordner hinzugefügten Pakete beim Start in alphabetischer Reihenfolge installiert.

>[!NOTE]
>
>Sie können dies auch tun, bevor Sie die Instanz das erste Mal starten. Dazu müssen Sie zunächst den Ordner `crx-quickstart` manuell erstellen, dann unter diesem Ordner den Ordner `install` erstellen und die Pakete dort speichern. Wenn Sie dann Ihre Instanz das erste Mal starten, werden die Pakete in alphabetischer Reihenfolge installiert.

### Deinstallieren von Paketen  {#uninstalling-packages}

AEM ermöglicht die Deinstallation von Paketen. Durch diese Aktion werden die Inhalte des Repositorys zurückgesetzt, die im Snapshot enthalten sind, der unmittelbar vor der Paketinstallation erstellt wurde.

>[!NOTE]
>
>Nach der Installation wird ein Snapshot-Paket erstellt, das die Inhalte enthält, die überschrieben werden.
>
>Dieses Paket wird wieder installiert, wenn Sie das Paket deinstallieren.

1. Navigieren Sie im Package Manager zum Paket, das Sie deinstallieren wollen.
1. Klicken Sie auf das Paketsymbol des Pakets, das Sie deinstallieren wollen.
1. Klicken Sie auf **Deinstallieren**, um die Inhalte dieses Pakets aus dem Repository zu entfernen. Es wird ein Dialogfeld mit einer Liste aller vorgenommenen Änderungen und der Aufforderung zur Bestätigung angezeigt. Wenn Sie fertig sind, klicken Sie im Dialogfeld auf **Schließen**.

### Löschen von Paketen {#deleting-packages}

So löschen Sie ein Paket aus der/den Package Manager-Liste(n):

>[!NOTE]
>
>Die installierten Dateien/Knoten aus dem Paket werden **nicht** gelöscht.

1. Erweitern Sie in der Konsole **Tools** den Ordner **Pakete** , um Ihr Paket im rechten Bereich anzuzeigen.

1. Klicken Sie auf das zu löschende Paket, um es zu markieren, und:

   * Klicken Sie im Symbolleistenmenü auf **Löschen**.
   * Klicken Sie mit der rechten Maustaste und wählen Sie **Löschen** aus.

   ![packagesdelete](assets/packagesdelete.png)

1. AEM bittet um Bestätigung, dass Sie das Paket löschen möchten. Klicken Sie auf **OK**, um den Löschvorgang zu bestätigen.

>[!CAUTION]
>
>Falls dieses Paket bereits installiert wurde, werden die *installierten* Inhalte **nicht** gelöscht.

### Replizieren von Paketen {#replicating-packages}

Replizieren Sie die Inhalte eines Pakets, um sie auf der veröffentlichten Instanz zu installieren:

1. Navigieren Sie im **Package Manager** zu dem Paket, das Sie replizieren möchten.

1. Klicken Sie auf das Symbol oder den Namen des Pakets, das Sie replizieren möchten, um es zu erweitern.
1. Wählen Sie in der Symbolleiste das Dropdown-Menü **Mehr** und dann die Option **Replizieren** aus.

## Package Share {#package-share}

Package Share war ein zentralisierter Server, der öffentlich für die Freigabe von Inhaltspaketen zur Verfügung gestellt wurde.

Sie wurde durch [Softwareverteilung](#software-distribution) ersetzt.

## Softwareverteilung {#software-distribution}

[Software ](https://downloads.experiencecloud.adobe.com) Distribution ist die neue Benutzeroberfläche, die die Suche und den Download von AEM-Paketen vereinfacht.

Weitere Informationen finden Sie in der [Dokumentation zur Softwareverteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

>[!CAUTION]
>
>AEM Package Manager kann derzeit nicht mit Software Distribution verwendet werden, laden Sie Ihre Pakete auf Ihre lokale Festplatte herunter.
