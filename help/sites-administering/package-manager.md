---
title: Package Manager
description: Erfahren Sie mehr über die Grundlagen der AEM Paketverwaltung mit Package Manager.
feature: Administering
role: Admin
uuid: cba76a5f-5d75-4d63-a0f4-44c13fa1baf2
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 6694a135-d1e1-4afb-9f5b-23991ee70eee
docset: aem65
exl-id: e8929d7c-9920-4c02-95a9-6f7f7a365203
source-git-commit: de58ba638c22b7148e1349417d1f514c26c5887e
workflow-type: tm+mt
source-wordcount: '3525'
ht-degree: 18%

---


# Package Manager {#working-with-packages}

Pakete bieten Ihnen die Möglichkeit, Repository-Inhalte zu importieren und zu exportieren. Sie können Pakete verwenden, um neue Inhalte zu installieren, neue Funktionen zu installieren, Inhalte zwischen Instanzen zu übertragen und Repository-Inhalte zu sichern.

Mithilfe von Package Manager können Sie Pakete zu Entwicklungszwecken zwischen Ihrer AEM-Instanz und Ihrem lokalen Dateisystem übertragen.

## Was sind Pakete? {#what-are-packages}

Ein Paket ist eine ZIP-Datei, die Repository-Inhalte im Serialisierungsformular des Dateisystems enthält, die Vault-Serialisierung genannt wird und eine benutzerfreundliche und einfach zu bearbeitende Darstellung von Dateien und Ordnern bietet. Der im Paket enthaltene Inhalt wird mithilfe von Filtern definiert.

Ein Paket enthält auch Vault-Metadaten, einschließlich der Filterdefinitionen und Import-Konfigurationsinformationen. Zusätzliche Inhaltseigenschaften, die nicht für die Paketextraktion verwendet werden, können in das Paket aufgenommen werden, z. B. eine Beschreibung, ein visuelles Bild oder ein Symbol. Diese zusätzlichen Inhaltseigenschaften dienen nur dem Inhaltspaket-Verbraucher und nur zu Informationszwecken.

>[!NOTE]
>
>Pakete repräsentieren die aktuelle Version der Inhalte zum Zeitpunkt der Erstellung des Pakets. Sie umfassen keine früheren Versionen der Inhalte, die AEM im Repository speichert.

## Package Manager {#package-manager}

Package Manager verwaltet die Pakete in Ihrer AEM-Installation. Nachdem Sie [den erforderlichen Berechtigungen zugewiesen wurde](#permissions-needed-for-using-the-package-manager) Sie können Package Manager für verschiedene Aktionen verwenden, z. B. für das Konfigurieren, Erstellen, Herunterladen und Installieren Ihrer Pakete.

### Erforderliche Berechtigungen {#required-permissions}

Um Pakete erstellen, ändern, hochladen und installieren zu können, müssen Benutzer über die entsprechenden Berechtigungen für die folgenden Knoten verfügen:

* Vollständige Berechtigungen, die Löschung ausschließen `/etc/packages`
* Der Knoten, der den Paketinhalt enthält

>[!CAUTION]
>
>Die Erteilung von Berechtigungen für Pakete kann zu sensiblen Informationen und Datenverlust führen.
>
>Um diese Risiken zu begrenzen, wird dringend empfohlen, bestimmte Gruppenberechtigungen nur für dedizierte Unterbäume zu gewähren.

### Zugriff auf Package Manager {#accessing}

Sie haben drei Möglichkeiten, auf Package Manager zuzugreifen:

1. Im AEM Hauptmenü -> **Instrumente** -> **Implementierung** -> **Pakete**
1. Von [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) Verwenden der oberen Umschalter-Leiste
1. Direkter Zugriff durch Zugriff `http://<host>:<port>/crx/packmgr/`

### Benutzeroberfläche von Package Manager {#ui}

Package Manager ist in vier Hauptfunktionsbereiche unterteilt:

* **Linke Navigationsleiste** - In diesem Bereich können Sie die Liste der Packages filtern und sortieren.
* **Paketliste** - Dies ist die Liste der Pakete in Ihrer Instanz, die nach Auswahl im linken Navigationsbereich gefiltert und sortiert wurden.
* **Aktivitätsprotokoll** - Dieses Bedienfeld wird zunächst minimiert und erweitert, um die Aktivität von Package Manager detailliert zu beschreiben, z. B. wenn ein Paket erstellt oder installiert wird. Auf der Registerkarte &quot;Aktivitätsprotokoll&quot;sind weitere Schaltflächen verfügbar, um:
   * **Protokoll löschen**
   * **Einblenden/ausblenden**
* **Symbolleiste** - Die Symbolleiste enthält Aktualisierungsschaltflächen für die Liste des linken Navigationsbereichs und der Pakete sowie Schaltflächen zum Suchen, Erstellen und Hochladen von Paketen.

![Benutzeroberfläche von Package Manager](assets/package-manager-ui.png)

Wenn Sie im linken Navigationsbereich auf eine Option klicken, wird die Paketliste sofort gefiltert.

Wenn Sie auf einen Paketnamen klicken, wird der Eintrag in der Paketliste um weitere Details zum Paket erweitert.

![Erweiterte Paketdetails](assets/package-expand.png)

Es gibt eine Reihe von Aktionen, die mit den Schaltflächen der Symbolleiste durchgeführt werden können, die verfügbar sind, wenn die Paketdetails erweitert werden.

* [Bearbeiten](#edit-package)
* [Build](#building-a-package)
* [Neu installieren](#reinstalling-packages)
* [Download](#downloading-packages-to-your-file-system)
* [Link freigeben](#share)

Weitere Aktionen sind unter dem **Mehr** Schaltfläche.

* [Löschen](#deleting-packages)
* [Abdeckung](#package-coverage)
* [Inhalt](#viewing-package-contents-and-testing-installation)
* [Rewrap](#rewrapping-a-package)
* [Andere Versionen](#other-versions)
* [Deinstallieren](#uninstalling-packages)
* [Testen der Installation](#viewing-package-contents-and-testing-installation)
* [Validieren](#validating-packages)
* [Replizieren](#replicating-packages)

### Paketstatus {#package-status}

Jeder Eintrag in der Paketliste verfügt über eine Statusanzeige, die Ihnen den Status des Pakets auf einen Blick mitteilt. Wenn Sie den Mauszeiger über den Status bewegen, wird eine QuickInfo mit Details zum Status angezeigt.

![Paketstatus](assets/package-status.png)

Wenn das Paket geändert wurde oder noch nie erstellt wurde, wird der Status als Link angezeigt, über den schnell gehandelt werden kann, um das Paket neu zu erstellen oder zu installieren.

## Paketeinstellungen {#package-settings}

Ein Paket ist im Wesentlichen ein Satz von Filtern und den Repository-Daten, die auf diesen Filtern basieren. Mithilfe der Package Manager-Benutzeroberfläche können Sie auf ein Paket klicken und dann auf die **Bearbeiten** -Schaltfläche, um die Details eines Pakets mit den folgenden Einstellungen anzuzeigen.

* [Allgemeine Einstellungen](#general-settings)
* [Paketfilter](#package-filters)
* [Paketabhängigkeiten](#package-dependencies)
* [Erweiterte Einstellungen](#advanced-settings)
* [Paket-Screenshots](#package-screenshots)

### Allgemeine Einstellungen {#general-settings}

Sie können verschiedene Paketeinstellungen bearbeiten, um Informationen wie die Paketbeschreibung, Abhängigkeiten und Anbieterdetails zu definieren.

Die **Paketeinstellungen** ist über **Bearbeiten** Schaltfläche beim [erstellen](#creating-a-new-package) oder [Bearbeiten](#viewing-and-editing-package-information) ein Paket. Nachdem Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.

![Dialogfeld &quot;Paket bearbeiten&quot;, allgemeine Einstellungen](assets/general-settings.png)

| Feld | Beschreibung |
|---|---|
| Name | Der Name des Pakets |
| Gruppe | Für die Organisation von Paketen können Sie den Namen einer neuen Gruppe eingeben oder eine bestehende Gruppe auswählen |
| Version | Für die Version zu verwendender Text |
| Beschreibung | Eine kurze Beschreibung des Pakets, das HTML Markup zum Formatieren ermöglicht |
| Miniatur | Das Symbol, das mit der Paketliste angezeigt wird |

#### Paketminiaturen {#thumbnails}

Eine Miniaturansicht bietet eine schnelle visuelle Darstellung dessen, was das Paket enthält. Dies wird dann in der Paketliste angezeigt und kann dazu beitragen, das Paket oder die Paketklasse leicht zu identifizieren.

Die folgenden Konventionen werden für offizielle Pakete verwendet:

Offizielles Hotfix

![Offizielles Hotfix-Miniaturbild](assets/official-hotfix.png)

Offizielle AEM Installation der Erweiterung

![Offizielles AEM oder Erweiterungsminiaturbild](assets/official-installation.png)

Offizielles Service Pack

![Symbol für Offizielles AEM](assets/official-service-pack.png)

Verwenden Sie ein eindeutiges Symbol für Ihr Paket. Verwenden Sie kein von Adobe verwendetes Symbol erneut.

### Paketfilter {#package-filters}

Filter identifizieren die Repository-Knoten, die in das Paket eingeschlossen werden sollen. Eine **Filterdefinition** legt die folgenden Informationen fest:

* Die **Stammverzeichnis** des einzuschließenden Inhalts
* **Regeln** die bestimmte Knoten unterhalb des Stammpfads ein- oder ausschließen

Hinzufügen von Regeln mithilfe der **+** Schaltfläche. Entfernen Sie Regeln mithilfe der **-** Schaltfläche.

Regeln werden in der Reihenfolge angewendet, sodass sie nach Bedarf mithilfe der **up** und **Nach** Pfeiltasten.

Filter können keine oder mehrere Regeln enthalten. Wenn keine Regeln definiert sind, enthält das Paket alle Inhalte unter dem Stammpfad.

Sie können eine oder mehrere Filterdefinitionen für ein Paket definieren. Verwenden Sie mehr als einen Filter, um Inhalte aus mehreren Stammpfaden einzuschließen.

![Registerkarte Filter](assets/edit-filter.png)

Beim Erstellen von Filtern können Sie einen Pfad definieren oder einen regulären Ausdruck verwenden, um alle Knoten anzugeben, die ein- oder ausgeschlossen werden sollen.

| Regeltyp | Beschreibung |
|---|---|
| include | Das Einschließen eines Ordners umfasst diesen Ordner sowie alle Dateien und Ordner in diesem Verzeichnis (d. h. die gesamte Unterstruktur), jedoch **nicht** andere Dateien oder Ordner aus unter dem angegebenen Stammpfad einschließen. |
| exclude |   Wird ein Verzeichnis ausgeschlossen, werden dieses Verzeichnis und alle Dateien und Ordner in diesem Verzeichnis (d. h. die gesamte Unterstruktur) ausgeschlossen. |

Paketfilter werden meist beim ersten Mal definiert [Erstellen Sie das Paket.](#creating-a-new-package) Sie können jedoch auch später bearbeitet werden. Danach sollte das Paket neu erstellt werden, um seinen Inhalt basierend auf den neuen Filterdefinitionen zu aktualisieren.

>[!TIP]
>
>Ein Paket kann mehrere Filterdefinitionen enthalten, sodass Knoten aus verschiedenen Speicherorten einfach zu einem Paket kombiniert werden können.

### Abhängigkeiten {#dependencies}

![Registerkarte &quot;Abhängigkeiten&quot;](assets/dependencies.png)

| Feld | Beschreibung | Beispiel/Details |
|---|---|---|
| Getestet mit | Der Produktname und die Version, auf die dieses Paket ausgerichtet ist oder mit der es kompatibel ist. | `6.5` |
| Behobene Probleme | Ein Textfeld, in dem Details zu Fehlern aufgelistet werden können, die mit diesem Paket behoben wurden, ein Fehler pro Zeile | - |
| Abhängig von | Führt andere Pakete auf, die erforderlich sind, damit das aktuelle Paket bei der Installation wie erwartet ausgeführt wird | `groupId:name:version` |
| Ersetzt | Eine Liste veralteter Pakete, die dieses Paket ersetzt | `groupId:name:version` |

### Erweiterte Einstellungen {#advanced-settings}

![Registerkarte &quot;Erweiterte Einstellungen&quot;](assets/advanced-settings.png)

| Feld | Beschreibung | Beispiel/Details |
|---|---|---|
| Name | Der Name des Anbieters des Pakets | `WKND Media Group` |
| URL | URL des Anbieters | `https://wknd.site` |
| Verknüpfung | Paketspezifischer Link zu einer Anbieterseite | `https://wknd.site/package/` |
| Erfordert | Definiert, ob bei der Installation des Pakets Einschränkungen bestehen | **Admin** - Das Paket darf nur mit Administratorrechten installiert werden <br>**Neu starten** - AEM muss nach der Installation des Pakets neu gestartet werden |
| AC-Verwaltung | Gibt an, wie die im Paket definierten Zugriffssteuerungsinformationen beim Import des Pakets verarbeitet werden | **Ignorieren** - ACLs im Repository beibehalten <br>**Überschreiben** - Überschreiben von ACLs im Repository <br>**Zusammenführen** - Beide ACL-Sätze zusammenführen <br>**MergePreserve** - Zusammenführen der Zugriffskontrolle im Inhalt mit dem im Paket enthaltenen durch Hinzufügen der Zugriffssteuerungseinträge von Prinzipalen, die nicht im Inhalt vorhanden sind <br>**Löschen** - ACLs löschen |

### Paket-Screenshots {#package-screenshots}

Sie können mehrere Screenshots an Ihr Paket anhängen, um eine visuelle Darstellung des Inhalts zu erhalten.

![Registerkarte &quot;Screenshots&quot;](assets/screenshots.png)

## Paketaktionen {#package-actions}

Es gibt viele Aktionen, die mit einem Paket durchgeführt werden können.

### Erstellen eines Pakets {#creating-a-new-package}

1. [Auf Package Manager zugreifen.](#accessing)

1. Klicken Sie auf **Paket erstellen**.

   >[!TIP]
   >
   >Wenn Ihre Instanz viele Pakete hat, kann es eine Ordnerstruktur geben. In solchen Fällen ist es einfacher, zum gewünschten Zielordner zu navigieren, bevor Sie das neue Paket erstellen.

1. Im **Neues Paket** Geben Sie die folgenden Felder ein:

   ![Dialogfeld &quot;Neues Paket&quot;](assets/new-package-dialog.png)

   * **Paketname** - Wählen Sie einen beschreibenden Namen aus, der Ihnen (und anderen) dabei hilft, den Inhalt des Pakets leicht zu identifizieren.

   * **Version** - Dies ist ein Textfeld, in dem Sie eine Version angeben können. Dieser wird an den Paketnamen angehängt, um den Namen der ZIP-Datei zu bilden.

   * **Gruppe** - Dies ist der Name der Zielgruppe (oder des Ordners). Gruppen helfen Ihnen bei der Organisation Ihrer Pakete. Für die Gruppe wird ein Ordner erstellt, sofern er noch nicht vorhanden ist. Wenn Sie den Gruppennamen leer lassen, wird das Paket in der Hauptpaketliste erstellt.

1. Klicken Sie auf **OK**, um das Paket zu erstellen.

1. AEM listet das neue Paket oben in der Liste der Pakete auf.

   ![Neues Paket](assets/new-package.png)

1. Klicken **Bearbeiten** , um [Paketinhalte.](#package-contents) Klicken **Speichern** nach Abschluss der Bearbeitung der Einstellungen.

1. [Sie können nun das Paket ](#building-a-package)erstellen.

Es ist nicht zwingend erforderlich, das Paket sofort nach seiner Erstellung zu erstellen. Ein nicht erstelltes Paket enthält keinen Inhalt und besteht nur aus den Filterdaten und anderen Metadaten des Pakets.

### Erstellen eines Pakets {#building-a-package}

Ein Paket wird oft gleichzeitig mit Ihnen erstellt [Package erstellen](#creating-a-new-package), Sie können jedoch zu einem späteren Zeitpunkt zurückkehren, um das Paket zu erstellen oder neu zu erstellen. Dies kann nützlich sein, wenn sich der Inhalt im Repository geändert hat oder sich die Paketfilter geändert haben.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken Sie auf **Erstellen**. Ein Dialogfeld fordert Sie auf zu bestätigen, dass Sie das Paket erstellen möchten, da vorhandene Paketinhalte überschrieben werden.

1. Klicken Sie auf **OK**. AEM erstellt das Paket und listet alle zum Paket hinzugefügten Inhalte so auf, wie dies in der Aktivitätenliste der Fall ist. Nachdem der Vorgang abgeschlossen ist, zeigt AEM eine Bestätigung an, dass das Paket erstellt wurde. Zudem aktualisiert AEM die Paketlisteninformationen (wenn Sie das Dialogfeld schließen).

### Bearbeiten eines Pakets {#edit-package}

Nachdem ein Paket in AEM hochgeladen wurde, können Sie seine Einstellungen ändern.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken Sie auf **Bearbeiten** und aktualisieren Sie die **[Paketeinstellungen](#package-settings)** nach Bedarf.

1. Klicken **Speichern** speichern.

Möglicherweise müssen Sie [Paket neu erstellen](#building-a-package) , um den Inhalt auf Grundlage der von Ihnen vorgenommenen Änderungen zu aktualisieren.

### Neueingliedern eines Pakets {#rewrapping-a-package}

Nachdem ein Paket erstellt wurde, kann es neu eingeschlossen werden. Durch eine Umbruch-Aktion werden die Paketinformationen ohne Miniaturansicht, Beschreibung usw. geändert, ohne dass der Paketinhalt geändert werden muss.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken Sie auf **Bearbeiten** und aktualisieren Sie die **[Paketeinstellungen](#package-settings)** nach Bedarf.

1. Klicken **Speichern** speichern.

1. Klicken **Mehr** -> **Rewrap** und ein Dialogfeld wird zur Bestätigung aufgerufen.

### Anzeigen anderer Paketversionen {#other-versions}

Da jede Version eines Pakets in der Liste wie jedes andere Paket angezeigt wird, kann Package Manager andere Versionen eines ausgewählten Pakets finden.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken **Mehr** -> **Andere Versionen** und ein Dialogfeld mit einer Liste anderer Versionen desselben Pakets mit Statusinformationen geöffnet.

### Anzeigen von Paketinhalten und Testen der Installation {#viewing-package-contents-and-testing-installation}

Nachdem ein Paket erstellt wurde, können Sie den Inhalt anzeigen.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Um den Inhalt anzuzeigen, klicken Sie auf **Mehr** -> **Inhalt**, und der Package Manager listet den gesamten Inhalt des Pakets im Aktivitätsprotokoll auf.

   ![Paketinhalt](assets/package-contents.png)

1. Klicken Sie auf , um einen Probelauf der Installation durchzuführen. **Mehr** -> **Testen der Installation** und Package Manager-Berichte in der Aktivität protokollieren die Ergebnisse so, als ob die Installation durchgeführt würde.

   ![Testinstallation](assets/test-install.png)

### Herunterladen von Paketen in das Dateisystem {#downloading-packages-to-your-file-system}

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken Sie auf **Download** oder den verknüpften Dateinamen des Pakets im Bereich mit Paketdetails.

1. AEM lädt das Paket auf Ihren Computer herunter.

### Freigeben eines Pakets {#share}

Package Share war ein zentralisierter öffentlicher Dienst zur Verteilung von Inhaltspaketen. Package Share wurde durch [Softwareverteilung](#software-distribution) und diese Schaltfläche funktioniert nicht mehr.

### Hochladen von Paketen von dem Dateisystem {#uploading-packages-from-your-file-system}

1. [Auf Package Manager zugreifen.](#accessing)

1. Wählen Sie den Gruppenordner aus, in den das Paket hochgeladen werden soll.

1. Klicken Sie auf **Paket hochladen** Schaltfläche.

1. Geben Sie die erforderlichen Informationen zum hochgeladenen Paket an.

   ![Dialogfeld &quot;Package-Upload&quot;](assets/package-upload-dialog.png)

   * **Paket** - Verwenden Sie die **Durchsuchen...** -Schaltfläche, um das gewünschte Paket aus Ihrem lokalen Dateisystem auszuwählen.
   * **Hochladen erzwingen** - Wenn bereits ein Paket mit diesem Namen existiert, erzwingt diese Option den Upload und überschreibt das vorhandene Paket.

1. Klicken **OK** und das ausgewählte Paket hochgeladen und die Paketliste entsprechend aktualisiert wird.

Der Paketinhalt ist jetzt auf AEM vorhanden. Um den Inhalt jedoch verfügbar zu machen, stellen Sie sicher, dass Sie [Paket installieren](#installing-packages).

### Validieren von Paketen {#validating-packages}

Da Pakete vorhandenen Inhalt ändern können, ist es oft nützlich, diese Änderungen vor der Installation zu validieren.

#### Validierungsoptionen {#validation-options}

Package Manager kann die folgenden Validierungen durchführen:

* [OSGi-Paketimporte](#osgi-package-imports)
* [Überlagerungen](#overlays)
* [ACLs](#acls)

##### OSGi-Paketimporte validieren {#osgi-package-imports}

**Prüfumfang**

Diese Validierung prüft das Paket auf alle JAR-Dateien (OSGi-Bundles) und extrahiert deren `manifest.xml` (enthält die versionierten Abhängigkeiten, von denen das OSGi-Bundle abhängt) und überprüft, ob die AEM Instanz diese Abhängigkeiten mit den richtigen Versionen exportiert.

**Berichterstellung**

Alle versionierten Abhängigkeiten, die von der AEM nicht erfüllt werden können, werden im Aktivitätsprotokoll von Package Manager aufgeführt.

**Fehlerstatus**

Sind die Abhängigkeiten nicht erfüllt, werden die OSGi-Bundles im Paket mit diesen Abhängigkeiten nicht gestartet. Dies führt zu einer fehlerhaften Anwendungsbereitstellung, da alles, was auf das nicht gestartete OSGi-Bundle angewiesen ist, wiederum nicht ordnungsgemäß funktioniert.

**Fehlerbehebung**

Um Fehler zu beheben, die auf nicht zufrieden gestellte OSGi-Bundles zurückzuführen sind, muss die Abhängigkeitsversion im Bundle mit nicht zufrieden stellenden Importen angepasst werden.

##### Überlagerungen bestätigen {#overlays}

**Prüfumfang**

Diese Validierung ermittelt, ob das zu installierende Paket eine Datei enthält, die bereits in der AEM-Zielinstanz überlagert ist.

Beispielsweise bei einer vorhandenen Überlagerung unter `/apps/sling/servlet/errorhandler/404.jsp`, ein Paket, das `/libs/sling/servlet/errorhandler/404.jsp`, sodass die vorhandene Datei unter `/libs/sling/servlet/errorhandler/404.jsp`.

**Berichterstellung**

Solche Überlagerungen werden im Aktivitätsprotokoll von Package Manager beschrieben.

**Fehlerstatus**

Ein Fehlerstatus bedeutet, dass das Paket versucht, eine bereits überlagerte Datei bereitzustellen. Die Änderungen im Paket werden somit durch die Überlagerung überschrieben (und „ausgeblendet“) und nicht umgesetzt.

**Fehlerbehebung**

Um dieses Problem zu beheben, muss der Verantwortliche der Überlagerungsdatei in `/apps` muss die Änderungen an der überlagerten Datei in `/libs` und die erforderlichen Änderungen in die Überlagerung ( `/apps`) und stellen Sie die überlagerte Datei erneut bereit.

>[!NOTE]
>
>Der Validierungsmechanismus kann nicht abgestimmt werden, wenn der überlagerte Inhalt ordnungsgemäß in die Überlagerungsdatei integriert wurde. Daher berichtet diese Validierung auch weiterhin über Konflikte, selbst wenn die erforderlichen Änderungen vorgenommen wurden.

##### ACLs bestätigen {#acls}

**Prüfumfang**

Diese Validierung prüft, welche Berechtigungen hinzugefügt werden, wie diese verarbeitet werden (zusammenführen/ersetzen) und ob sie sich auf aktuelle Berechtigungen auswirken.

**Berichterstellung**

Die Berechtigungen werden im Aktivitätsprotokoll von Package Manager beschrieben.

**Fehlerstatus**

Die Angabe von expliziten Fehlern ist nicht möglich. Die Validierung gibt lediglich an, ob durch Installieren des Pakets neue ACL-Berechtigungen hinzugefügt oder aktuelle beeinträchtigt werden.

**Fehlerbehebung**

Anhand der von der Validierung bereitgestellten Informationen können die betroffenen Knoten in CRXDE überprüft und die ACLs nach Bedarf im Paket angepasst werden.

>[!CAUTION]
>
>Als Best Practice wird empfohlen, dass Pakete keine AEM bereitgestellten ACLs beeinträchtigen sollten, da dies zu unerwartetem Verhalten führen kann.

#### Durchführen der Validierung {#performing-validation}

Die Validierung von Paketen kann auf zweierlei Weise erfolgen:

* [Über die Benutzeroberfläche von Package Manager](#via-package-manager)
* [Über HTTP POST-Anfragen, wie z. B. mit cURL](#via-post-request)

Führen Sie die Validierung stets nach dem Hochladen und vor dem Installieren eines Pakets durch.

##### Paketvalidierung über Package Manager {#via-package-manager}

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Um das Paket zu validieren, klicken Sie auf **Mehr** -> **Bestätigen**,

1. Aktivieren Sie im angezeigten modalen Dialogfeld das Kontrollkästchen des gewünschten Validierungstyps und starten Sie die Validierung durch Klicken auf **Überprüfen**.

1. Die ausgewählten Validierungen werden dann ausgeführt und die Ergebnisse werden im Aktivitätsprotokoll von Package Manager angezeigt.

##### Paketvalidierung über HTTP POST-Anfrage {#via-post-request}

Die POST-Anfrage hat folgendes Format.

```
https://<host>:<port>/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls
```

Die `type` -Parameter kann eine beliebige kommagetrennte, ungeordnete Liste sein, die aus Folgendem besteht:

* `osgiPackageImports`
* `overlays`
* `acls`

Der Wert von `type` standardmäßig auf `osgiPackageImports` wenn nicht explizit übergeben wurde.

Führen Sie bei Verwendung von cURL eine Anweisung ähnlich der folgenden aus:

```shell
curl -v -X POST --user admin:admin -F file=@/Users/SomeGuy/Desktop/core.wcm.components.all-1.1.0.zip 'http://localhost:4502/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls'
```

Bei der Validierung über eine POST-Anfrage wird die Antwort als JSON-Objekt zurückgesendet.

### Anzeigen der Paketabdeckung {#package-coverage}

Pakete werden durch ihre Filter definiert. Sie können Package Manager anweisen, Filter eines Pakets auf Ihren vorhandenen Repository-Inhalt anzuwenden, um anzuzeigen, welcher Inhalt des Repositorys von der Filterdefinition des Pakets abgedeckt wird.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken **Mehr** -> **Reichweite**.

1. Die Details zur Abdeckung sind im Aktivitätsprotokoll aufgeführt.

### Installieren von Paketen {#installing-packages}

Beim Hochladen eines Pakets wird nur der Paketinhalt zum Repository hinzugefügt, es ist jedoch nicht verfügbar. Sie müssen das hochgeladene Paket installieren, um den Inhalt des Pakets verwenden zu können.

>[!CAUTION]
>
>Beim Installieren eines Pakets können vorhandene Inhalte überschrieben oder gelöscht werden. Laden Sie ein Paket nur hoch, wenn Sie sich sicher sind, dass dadurch keine benötigten Inhalte gelöscht oder überschrieben werden.

Vor der Installation Ihres Pakets erstellt Package Manager automatisch ein Snapshot-Paket, das den zu überschreibenden Inhalt enthält. Dieser Schnappschuss wird neu installiert, wenn Sie Ihr Paket deinstallieren.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails des Pakets, das Sie installieren möchten, in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken Sie entweder auf **Installieren** in den Elementdetails oder der **Installieren** im Paketstatus.

1. In einem Dialogfeld wird eine Bestätigung angefordert und es können zusätzliche Optionen angegeben werden.

   * **Nur extrahieren** - Extrahieren Sie das Paket nur, damit kein Snapshot erstellt wird und daher keine Deinstallation möglich ist.
   * **Schwellenwert speichern** - Anzahl der Übergangsknoten, bis das automatische Speichern ausgelöst wird (erhöht sich, wenn bei gleichzeitiger Änderung Ausnahmen auftreten)
   * **Teilpakete extrahieren** - Automatisches Extrahieren von Unterpaketen aktivieren
   * **Umgang mit Zugriffskontrolle** - Gibt an, wie die im Paket definierten Zugriffssteuerungsinformationen verarbeitet werden, wenn das Paket installiert wird (Optionen sind mit denen des [Erweiterte Paketeinstellungen](#advanced-settings))
   * **Umgang mit Abhängigkeiten** - Geben Sie an, wie Abhängigkeiten während der Installation verarbeitet werden

1. Klicken Sie auf **Installieren**.

1. Im Aktivitätsprotokoll wird der Fortschritt der Installation beschrieben.

Sobald die Installation abgeschlossen und erfolgreich war, wird die Paketliste aktualisiert und das Wort **Installiert** im Paketstatus angezeigt.

### Neuinstallation von Paketen {#reinstalling-packages}

Bei der Neuinstallation von Paketen werden dieselben Schritte für ein bereits installiertes Paket ausgeführt, das verarbeitet wird, wenn [Installieren Sie zunächst das Paket.](#installing-packages)

### Dateisystem-basierte(r) Upload und Installation {#file-system-based-upload-and-installation}

Sie können bei der Installation von Paketen ganz auf Package Manager verzichten. AEM können Pakete erkennen, die an einem bestimmten Speicherort im lokalen Dateisystem des Hostcomputers platziert wurden, und sie automatisch hochladen und installieren.

1. Unter dem AEM Installationsordner befindet sich ein `crx-quicksart` Ordner neben der JAR-Datei und `license.properties` -Datei. Erstellen Sie einen Ordner mit dem Namen `install` under `crx-quickstart` , was zu einem Pfad führt `<aem-home>/crx-quickstart/install`.

1. Fügen Sie in diesem Ordner Ihre Pakete hinzu. Sie werden automatisch auf Ihre Instanz hochgeladen und dort installiert.

1. Nach dem Hochladen und der Installation können Sie die Pakete in Package Manager sehen, als hätten Sie sie mit der Package Manager-Benutzeroberfläche installiert.

Wenn die Instanz ausgeführt wird, beginnen der Upload und die Installation sofort, wenn Sie sie zum Paket zum `install` Ordner

Wenn die Instanz nicht ausgeführt wird, werden Pakete in der `install` -Ordner beim Start in alphabetischer Reihenfolge installiert werden.

### Deinstallieren von Paketen {#uninstalling-packages}

Durch die Deinstallation des Pakets wird der Inhalt des Repositorys auf den Schnappschuss zurückgesetzt, der von Package Manager vor der Installation automatisch erstellt wurde.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails des Pakets, das Sie deinstallieren möchten, indem Sie in der Paketliste auf den Paketnamen klicken.

1. Klicken **Mehr** -> **Deinstallieren**, um den Inhalt dieses Pakets aus dem Repository zu entfernen.

1. Es wird ein Dialogfeld mit einer Liste aller vorgenommenen Änderungen und der Aufforderung zur Bestätigung angezeigt.

1. Das Paket wird entfernt und der Schnappschuss wird angewendet. Der Fortschritt des Prozesses wird im Aktivitätsprotokoll angezeigt.

### Löschen von Paketen {#deleting-packages}

Beim Löschen eines Pakets werden nur dessen Details aus Package Manager gelöscht. Wenn dieses Paket bereits installiert wurde, wird der installierte Inhalt nicht gelöscht.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails des Pakets, das Sie aus der Paketliste löschen möchten, indem Sie auf den Paketnamen klicken.

1. Package Manager fordert Sie zur Bestätigung auf, dass Sie das Paket löschen möchten. Klicken Sie auf **OK**, um den Löschvorgang zu bestätigen.

1. Die Paketinformationen werden gelöscht und die Details werden im Aktivitätsprotokoll aufgeführt.

### Replizieren von Paketen {#replicating-packages}

Replizieren Sie den Inhalt eines Pakets, um es auf der Veröffentlichungsinstanz zu installieren.

1. [Auf Package Manager zugreifen.](#accessing)

1. Öffnen Sie die Paketdetails des Pakets, das Sie replizieren möchten, in der Paketliste, indem Sie auf den Paketnamen klicken.

1. Klicken **Mehr** -> **Replizieren**.

1. Das Paket wird repliziert und Details werden im Aktivitätsprotokoll aufgeführt.

## Softwareverteilung {#software-distribution}

AEM Pakete können verwendet werden, um Inhalte in AEM Umgebungen zu erstellen und freizugeben.

[Softwareverteilung](https://downloads.experiencecloud.adobe.com) ist ein zentralisierter Dienst, der die Suche und den Download AEM Packages vereinfacht.

Weitere Informationen finden Sie im Abschnitt [Dokumentation zur Softwareverteilung.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

>[!NOTE]
>
>Package Manager ist derzeit nicht in Software Distribution integriert, da es mit dem früheren Package Share-Dienst verwendet wurde. Daher funktionieren die Freigabeschaltflächen und andere Links zur Paketfreigabe in Package Manager nicht mehr. Die Lösung besteht darin, Pakete auf Ihre lokale Festplatte herunterzuladen.
