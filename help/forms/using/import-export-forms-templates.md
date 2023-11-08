---
title: Importieren und Exportieren von Assets in AEM Forms
seo-title: Importing and exporting assets to AEM Forms
description: Sie können adaptive Formulare und Vorlagen aus und in AEM Instanzen importieren und exportieren. Dies erleichtert das Integrieren von Formularen oder das Verschieben von Formularen zwischen Systemen.
seo-description: You can import and export adaptive forms and templates from and in to AEM instances. This helps in migrating forms or moving them across systems.
uuid: 937daedd-56f3-4e02-b695-b194b494d9bf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 69210727-dde3-495a-87b7-2e8173e6b664
docset: aem65
role: Admin
exl-id: b5f6a54e-92d1-4631-a1d1-184f37d174b6
source-git-commit: 941e5d7574d31622f50e50e717c21cd2eba2e602
workflow-type: tm+mt
source-wordcount: '2509'
ht-degree: 56%

---

# Importieren und Exportieren von Assets in AEM Forms{#importing-and-exporting-assets-to-aem-forms}

Sie können Formulare und verwandte Assets, Designs, Datenwörterbücher, Dokumentfragmente und Briefe zwischen verschiedenen AEM Forms-Instanzen verschieben. Ein solches Verschieben ist bei der Migration von Systemen oder beim Verschieben von Formularen von einem Staging Server auf einen Produktionsserver erforderlich. Für Assets, für die das Hochladen und Importieren über die AEM Forms-Benutzeroberfläche unterstützt wird, ist die Verwendung der Forms-Benutzeroberfläche die empfohlene Methode zum Exportieren oder Importieren. Die Verwendung von AEM Package Manager zum Exportieren oder Importieren solcher Assets wird nicht empfohlen.

>[!NOTE]
>
>* In AEM 6.4 Forms haben sich die Struktur und Pfade des crx-Repository geändert. Wenn Sie Assets aus einer früheren Version in AEM 6.4 Forms importieren und das Formular einige Abhängigkeiten von der älteren Struktur aufweist, müssen Sie die Abhängigkeiten manuell exportieren. Details zu Änderungen an der Struktur und den Pfaden des Repositorys finden Sie unter [Repository-Umstrukturierung in AEM](/help/sites-deploying/repository-restructuring.md).
>

## Download und Upload von Assets für Formulare und Dokumente {#download-or-upload-forms-amp-documents-assets}

Mit der AEM Forms-Benutzeroberfläche können Sie Assets aus einer AEM exportieren, indem Sie sie als AEM CRX-Paket oder Binärdateien herunterladen. Sie können dann das heruntergeladene AEM CRX-Paket oder die Binärdatei in eine andere AEM-Instanz importieren.

Export und Import über die Benutzeroberfläche von AEM Forms wird für alle Assets mit Ausnahme von adaptiven Formularvorlagen und adaptiven Formularinhaltsrichtlinien unterstützt. Daher werden beim Exportieren eines adaptiven Formulars aus der AEM Forms-Benutzeroberfläche die zugehörige adaptive Formularvorlage und die Inhaltsrichtlinien nicht automatisch wie andere zugehörige Assets exportiert.

Sie müssen AEM Package Manager verwenden, um ein CRX-Paket dieser Elemente auf dem AEM-Quellserver zu erstellen und das Paket auf dem Zielserver zu installieren. Weitere Informationen zum Erstellen und Installieren von Paketen finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

### Download von Assets für Formulare und Dokumente {#download-forms-amp-documents-assets}

Download von Assets für Formulare und Dokumente

1. Melden Sie sich bei der AEM Forms-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/compass.png) > Formulare > Formulare und Dokumente.
1. Wählen Sie die AEM Forms-Assets und klicken Sie auf das Symbol **Herunterladen**.
1. Wählen Sie unter „Asset(s) herunterladen“ eine der folgenden Optionen und tippen Sie auf **Herunterladen**.

   * **Als CRX-Paket herunterladen:** Verwenden Sie diese Option zum Herunterladen und Verschieben aller ausgewählten Assets und der zugehörigen Abhängigkeiten von einer AEM Forms-Instanz in eine andere. Dadurch werden alle Assets und Ordner als CRX-Paket heruntergeladen. Alle Formular-Assets, einschließlich der in AEM erstellten Formulare (adaptive Formulare, interaktive Kommunikation und adaptive Formularfragmente), Formularsätze, Formularvorlagen, PDF-Dokumente und Ressourcen (XSDs, XFS, Bilder) können als Paket von der AEM Forms-Benutzeroberfläche heruntergeladen werden.
Der Vorteil des Herunterladens von Assets als Paket besteht darin, dass dabei auch Assets enthalten sind, die von den ausgewählten Assets verwendet wurden. Wenn Sie beispielsweise über ein adaptives Formular verfügen, das eine Formularvorlage, XSD und ein Bild verwendet. Wenn Sie dieses adaptive Formular auswählen und als Paket herunterladen, enthält das heruntergeladene Paket auch die Formularvorlage, XSD und das Bild. Alle mit dem Asset verknüpften Metadateneigenschaften (einschließlich benutzerdefinierter Eigenschaften) werden ebenfalls heruntergeladen.

   * **Asset(s) als Binärdateien herunterladen:** Verwenden Sie die Option nur zum Herunterladen von Formularvorlagen (XDP), PDF-Formularen (PDF), Dokumenten (PDF) und Ressourcen (Bilder, Schemas, Stylesheets). Sie können diese Assets mit externen Anwendungen bearbeiten. Es werden die Forms-Assets, die Binärdaten enthalten, wie XSDs, XDPs, Bilder, PDFs, und XDPs, als .zip-Datei heruntergeladen.
Sie können keine adaptiven Formulare, interaktive Kommunikation, adaptiven Formularfragmente, Designs und Formularsätze mit der Option **Asset(s) als binäre Dateien herunterladen** herunterladen. Um diese Assets herunterzuladen, sollten Sie **Als CRX-Paket herunterladen** -Option.

   Die ausgewählten Assets werden als Archiv heruntergeladen (.zip-Datei).

   >[!NOTE]
   >
   >Das AEM-Paket und die Binärdateien werden als ein Archiv (.zip-Datei) heruntergeladen. Die Vorlagen für die Assets werden nicht zusammen mit den Assets heruntergeladen. Sie müssen die Asset-Vorlagen separat exportieren.

### Hochladen von Forms- und Dokumenten-Assets {#upload-forms-amp-documents-assets}

Hochladen von Assets für Formulare und Dokumente:

>[!VIDEO](https://vimeo.com/de/)

1. Melden Sie sich bei der AEM Forms-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/compass.png) > Formulare > Formulare und Dokumente.
1. Tippen Sie auf **Erstellen** > **Datei hochladen**. Ein Dialogfeld zum Hochladen von Formularen oder Paketen wird angezeigt.
1. Navigieren Sie im Dialogfeld zum Paket oder Archiv, das importiert werden soll, und wählen Sie es aus. Sie können außerdem PDF-Dokumente, XSDs, Bilder, Stylesheets und XDP-Formulare auswählen. Tippen Sie auf **Öffnen**. Der ausgewählte Ordner- oder Dateiname darf keine Sonderzeichen enthalten.

   Überprüfen Sie im Dialogfeld die Details der Assets, die hochgeladen werden, und tippen Sie auf **Hochladen**.

   Wenn Sie ein vorhandenes Formular-Asset hochladen, wird das Asset aktualisiert.

   >[!NOTE]
   >
   >Beim Hochladen eines Pakets wird eine vorhandene Ordnerhierarchie nicht ersetzt. Wenn Sie beispielsweise ein adaptives Formular mit dem Namen &quot;Training&quot;unter &quot;/content/dam/formsanddocuments&quot;auf einem Server haben. Sie laden das adaptive Formular herunter und laden es auf einen anderen Server hoch. Der zweite Server hat ebenfalls einen Ordner „Training“ am selben Standort „/content/dam/formsanddocuments“. Der Hochladevorgang schlägt fehl.

## Download oder Upload eines Designs {#downloading-or-uploading-a-theme}

Mit AEM Forms können Sie Designs erstellen, herunterladen oder hochladen. Ein Design wird wie andere Assets wie Formulare, Dokumente und Briefe erstellt. Sie können ein Design erstellen, es herunterladen und auf eine andere Instanz hochladen, um es wiederzuverwenden. Weitere Informationen zu Designs finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).

### Herunterladen eines Designs {#downloading-a-theme}

Sie können Designs in AEM Forms exportieren und in anderen Projekten oder Instanzen verwenden. Mit AEM können Sie ein Design als ZIP-Datei herunterladen, die Sie in die Instanz hochladen können.

Herunterladen von Designs

1. Melden Sie sich bei der AEM Forms-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/compass.png) > Formulare > Designs.
1. Wählen Sie das Design und tippen Sie auf **Herunterladen**. Das Design wird als ein Archiv (.zip-Datei) heruntergeladen.

### Hochladen eines Designs {#uploading-a-theme}

Sie können erstellte Designs mit Stilvorgaben für Ihr Projekt verwenden. Sie können Design-Pakete importieren, die von anderen erstellt werden, indem Sie sie in Ihr Projekt hochladen.

Hochladen von Designs

1. In Experience Manager navigieren Sie zu **Formulare > Designs**.
1. Auf der Seite „Designs“ klicken Sie auf **Erstellen > Datei-Upload**.
1. In der Eingabeaufforderung zu „Datei-Upload“ suchen Sie ein Design-Paket auf Ihrem Computer, wählen es aus und klicken auf **Hochladen**.
Das hochgeladene Design ist auf der Seite „Designs“ verfügbar.

1. Melden Sie sich bei der AEM Forms-Instanz an.
1. Tippen Sie auf das Symbol „Experience Manager“ ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Symbol „Navigation“ ![compass](assets/compass.png) > Formulare > Designs.
1. Klicken Sie auf **Erstellen** > **Datei hochladen**. In der Eingabeaufforderung zur Dateiaktualisierung suchen Sie ein Designpaket auf Ihrem Computer, wählen es aus und klicken auf **Hochladen**. Das Design wird hochgeladen.

## Importieren und Exportieren von Assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

Um Assets wie Datenwörterbücher, Briefe und Dokumentfragmente zwischen zwei verschiedenen Implementierungen von Correspondence Management freizugeben, können Sie .cmp-Dateien erstellen und freigeben. Eine .cmp-Datei kann ein oder mehrere Datenwörterbücher, Briefe, Dokumentfragmente und Formulare enthalten.

### Exportieren von Dokumentfragmenten, Briefen und/oder Datenwörterbüchern {#export-document-fragments-letters-and-or-data-dictionaries}

1. Tippen Sie auf den Seiten für die Briefe, Dokumentfragmente oder Datenwörterbücher auf die Assets, die Sie in ein einzelnes Paket exportieren möchten, und tippen Sie dann auf „Warteschlange für den Download“. Die Assets werden für den Export in eine Warteschlange gestellt.
1. Wiederholen Sie den obigen Schritt nach Bedarf, um Briefe, Dokumentfragmente und Datenwörterbücher hinzuzufügen.
1. Tippen Sie auf **Herunterladen**.
1. Das Correspondence Management zeigt das Dialogfeld „Asset(s) herunterladen“ mit einer Liste von Assets in der Exportliste an.

   ![Export](assets/export.png)

1. Tippen Sie auf Auflösen , um die Abhängigkeiten anzuzeigen, die exportiert werden. Oder fahren Sie mit dem nächsten Schritt fort. Selbst wenn Sie nicht auf &quot;Auflösen&quot;tippen, werden die Abhängigkeiten weiterhin exportiert.
1. Um die .cmp-Datei herunterzuladen, tippen Sie auf **OK**.
1. Correspondence Management lädt eine .cmp-Datei auf Ihren Computer herunter.

   Die .cmp-Datei enthält die exportierten Assets. Sie können die .cmp-Datei mit anderen teilen. Andere Benutzer können die .cmp-Datei auf einen anderen Server importieren, um alle Assets auf dem neuen Server abzurufen.

### Alle Correspondence Management-Assets als Paket exportieren {#export-all-the-correspondence-management-assets-as-a-package}

Verwenden Sie diese Option, um alle Correspondence Management-Assets und die zugehörigen Abhängigkeiten als Paket von einer AEM Formularinstanz herunterzuladen.

Beispiel: Wenn Correspondence Management ein Schreiben verwendet, das ein Bild und Text enthält, dann enthält auch das heruntergeladene Paket das Bild und den Text des Schreibens. Alle mit dem Asset verknüpften Metadateneigenschaften (einschließlich benutzerdefinierter Eigenschaften) werden ebenfalls heruntergeladen. Sobald Sie das Paket (.cmp) heruntergeladen haben, können Sie [das Paket in eine andere AEM Forms-Instanz importieren](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

Um alle Correspondence Management-Assets und die zugehörigen Abhängigkeiten als Paket herunterzuladen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich beim AEM Forms-Server als Formularbenutzer an.
1. Tippen **Adobe Experience Manager** in der Symbolleiste für globale Navigation.
1. Tippen Sie auf Werkzeuge (![Werkzeuge](assets/tools.png)) und dann auf **Formulare**.
1. Tippen Sie auf **Correspondence Management-Assets exportieren**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``Die Seite „Alle Correspondence Management-Assets exportieren“ wird angezeigt und enthält Informationen über den letzten Exportversuch sowie einen Link zum Herunterladen des letzten erfolgreich exportierten Pakets.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Tippen Sie auf **Exportieren** und in der Bestätigungsmeldung auf **OK**.

   Nach Abschluss eines Batch-Prozesses werden die Details der letzten Ausführung und der Link zum Herunterladen des Pakets aktualisiert. Dazu gehören Informationen wie die Administrator-Anmeldung und ob der Batch erfolgreich ausgeführt wurde oder fehlgeschlagen ist. Die Assets werden in ein Paket exportiert und der Link Exportiertes Paket herunterladen wird angezeigt.

   >[!NOTE]
   >
   >Der Vorgang „Alle Assets exportieren“ kann nicht abgebrochen werden, sobald er gestartet wurde. Während der Vorgang &quot;Alle Assets exportieren&quot;ausgeführt wird, dürfen Sie keine Assets erstellen, löschen, ändern oder veröffentlichen oder den Prozess &quot;Alle Assets veröffentlichen&quot;starten.a

1. Tippen Sie auf **Exportiertes Paket herunterladen** -Link, um die Paketdatei herunterzuladen.

   Um die Assets im Paket einer anderen Instanz von Correspondence Management hinzuzufügen, [importieren Sie das Paket in eine Instanz von AEM Forms](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

### Importieren von Dokumentfragmenten, Briefen und/oder Datenwörterbüchern in Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

Sie können Assets importieren, die in eine .cmp-Datei exportiert werden. Eine .cmp-Datei kann einen oder mehrere Briefe, Datenwörterbücher, Dokumentfragmente und abhängige Assets enthalten.

>[!NOTE]
>
>Beim Importieren älterer Correspondence Management-Assets für die Migration, müssen Sie sich mithilfe eines Administratorkontos anmelden. Weitere Informationen zum Migrieren alter Correspondence Management-Assets finden Sie unter [Correspondence Managment-Assets in AEM 6.1 Forms migrieren](/help/forms/using/migration-utility.md).

1. Tippen Sie auf der Seite mit den Datenwörterbüchern, Briefe oder Dokumentfragmenten auf **Erstellen > Datei hochladen** und wählen Sie die .cmp-Datei aus.
1. Correspondence Management zeigt das Dialogfeld „Assets importieren“ mit der Liste der Assets, die importiert werden, an. Tippen Sie auf **Importieren**.

   Nach dem Importieren der Assets werden die folgenden Eigenschaften der Assets aktualisiert, während die anderen Eigenschaften unverändert bleiben:

   * Autor: Zeigt die ID des Benutzers an, der das Asset auf den Server importiert hat
   * Geändert: Der Zeitpunkt, zu dem das Asset auf den Server importiert wurde

   >[!NOTE]
   >
   >Damit Sie XDPs hochladen können (als Teil der CMP-Datei oder anderweitig), müssen Sie Teil der Gruppe &quot;Formularbenutzer&quot;sein. Wenden Sie sich für Zugriffsberechtigungen an den Administrator.

## Exportieren eines Workflow-Programms {#export-a-workflow-application}

Sie können den AEM-Paket-Manager verwenden, um Workflow-Programme zu exportieren. Das Verfahren wird im Folgenden erläutert:

1. Öffnen Sie AEM Forms Package Manager. Die URL des Paketmanagers lautet „https://&lt;server>:&lt;port>/crx/packmgr“.
1. Klicken Sie auf **[!UICONTROL Paket erstellen]**. Das Dialogfeld **[!UICONTROL Neues Paket]** wird angezeigt.
1. Geben Sie den Namen, die Version und die Gruppe für das Paket an. Klicken Sie auf **[!UICONTROL OK]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** und öffnen Sie die Registerkarte **[!UICONTROL Filter]**. Klicks **[!UICONTROL Filter hinzufügen]**. Geben Sie den Pfad der Workflow-Anwendung an. Beispiel: /etc/fd/dashboard/startpoints/homemortgage. Klicken Sie auf **[!UICONTROL Regel hinzufügen]**.

1. Öffnen Sie die Registerkarte **[!UICONTROL Erweitert]**. Wählen Sie **[!UICONTROL Zusammenführen]** oder **[!UICONTROL Überschreiben]** im Feld „ACL-Bearbeitung“. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Paket zu erstellen.

   Nachdem das Paket erstellt wurde, können Sie es herunterladen und auf den anderen Server importieren. Die Workflow-Anwendung wird auf dem Server angezeigt, auf den das Paket hochgeladen wurde.

   >[!NOTE]
   >
   >Damit die Workflow-Anwendung ordnungsgemäß funktioniert, exportieren Sie auch das entsprechende adaptive Formular und das Workflow-Modell mit der Arbeitsanwendung.

## Ordner und Organisieren von Assets {#folders-and-organizing-assets}

Die Benutzeroberfläche von AEM Forms verwendet Ordner zum Anordnen von Assets. Diese Ordner werden für Elemente verwendet, die in der Benutzeroberfläche von AEM Forms erstellt werden. Sie können Assets und Dokumente in diesen Ordnern umbenennen, Unterordner erstellen und speichern. Durch die Organisation von Dokumenten und Assets in einem Ordner können Sie die Dateien zur einfachen Verwaltung gruppieren. Sie können einen Ordner auswählen und ihn herunterladen oder löschen.

Um einen Ordner zu erstellen, führen Sie die folgenden Schritte aus:

### Erstellen von Ordnern {#create-a-folder}

1. Melden Sie sich bei der AEM Forms-Benutzeroberfläche unter `https://<server>:<port>/aem/forms.html` an.
1. Navigieren Sie zu dem Speicherort, unter dem Sie einen Ordner erstellen möchten.
1. Tippen Sie auf Erstellen > Ordner .
1. Geben Sie die folgenden Details ein:

   * **Titel**: Anzeigename für den Ordner
   * **Name**: *(obligatorisch)* Der Knotenname, unter dem Sie den Ordner im Repository speichern möchten

   >[!NOTE]
   >
   >Standardmäßig wird der Wert des Namensfelds automatisch mit dem Titel ausgefüllt. Der Name darf nur alphanumerische Zeichen oder die Sonderzeichen Bindestrich (-) und Unterstrich (_) enthalten. Alle anderen Sonderzeichen, die im Titel eingegeben werden, werden automatisch durch einen Bindestrich ersetzt und Sie werden aufgefordert, den neuen Namen zu bestätigen. Sie können mit dem vorgeschlagenen Namen fortfahren oder ihn weiter bearbeiten.

1. Ein neuer Ordner mit dem definierten Titel wird an der aktuellen Position in der Asset-Liste angezeigt.

   Wenn ein Ordner mit dem angegebenen Namen vorhanden ist, schlägt das Senden mit einem Fehler fehl. Sie können die Fehlermeldung anzeigen, indem Sie die Maus über das Fehlersymbol ![aem6forms_error_alert](assets/aem6forms_error_alert.png) bewegen, das neben dem Namensfeld angezeigt wird.

   Sie können auf den neu erstellten Ordner tippen, um in den Ordner zu wechseln und Assets oder Ordner im Ordner zu erstellen. Außerdem können Sie einen Ordner auswählen und ihn zum Herunterladen in die Warteschlange stellen, löschen oder seinen Namen bearbeiten.

   ![editdeletedownloadafolder](assets/editdeletedownloadafolder.png)

### Erstellen von Kopien eines oder mehrerer Assets oder Briefe {#create-copies-of-one-or-more-assets-or-letters}

Sie können vorhandene Assets und Briefe verwenden, um schnell Assets und Briefe mit ähnlichen Eigenschaften, Inhalten und vererbten Assets zu erstellen. Sie können Datenwörterbücher, Dokumentfragmente und Briefe kopieren und einfügen.

Führen Sie die folgenden Schritte aus, um Kopien von Assets und Briefen zu erstellen:

1. Wählen Sie auf der entsprechenden Seite Assets oder Briefe ein oder mehrere Assets/Briefe aus. Auf der Benutzeroberfläche wird das Symbol „Kopieren“ angezeigt.
1. Tippen Sie auf Kopieren. Auf der Benutzeroberfläche wird das Symbol „Einfügen“ angezeigt. Sie können auch vor dem Einfügen in einen Ordner navigieren. Verschiedene Ordner können Assets mit demselben Namen enthalten. Weitere Informationen zu Ordnern finden Sie unter [Ordner und Organisieren von Assets](#folders-and-organizing-assets).
1. Tippen Sie auf „Einfügen“. Das Dialogfeld „Einfügen“ wird angezeigt. Das System generiert automatisch Namen und Titel für die neuen Kopien von Assets/Briefen, aber Sie können die Titel und Namen der Assets/Briefe bearbeiten.

   Wenn Sie die Assets/Briefe an dieselbe Stelle kopieren und einfügen, wird dem bestehenden Namen der Assets/Briefe ein Suffix „-CopyXX“ hinzugefügt. Wenn für das kopierte Asset/den kopierten Brief kein Titel vorhanden war, bleibt das automatisch generierte Titelfeld leer.

1. Bearbeiten Sie bei Bedarf den Titel und den Namen, mit denen Sie die Kopie des Assets/Briefs speichern möchten.
1. Tippen Sie auf „Einfügen“. Es werden neue Kopien der kopierten Assets erstellt.

## Suchen {#search-forms}

In der AEM Forms-Benutzeroberfläche können Sie nach Inhalten suchen. In der oberen Leiste können Sie auf Suchen **[A]** tippen, um Ihre Inhalte nach Ressourcen wie Assets und Dokumenten zu durchsuchen.

Wenn Sie nach Assets suchen, zeigt AEM Forms den Seitenbereich an. Sie können auch auf ![Assets-browser-content-only](assets/assets-browser-content-only.png) > Filter **[B]** tippen, um das seitliche Bedienfeld aufzurufen. Mithilfe der verschiedenen Filter im Seitenbereich können Sie die Suche eingrenzen. Im seitlichen Bedienfeld können Sie Ihre Suchvorgänge auch speichern.

![search_topbar](assets/search_topbar.png)

**A.** Suche **B.** Filter

![Seitenbereich - Filter](assets/search_sidepanel.png)

Seitenbereich – Filter

Im seitlichen Bedienfeld können Sie die folgenden verwenden, um Ihre Suchergebnisse einzugrenzen:

* Verzeichnis durchsuchen
* Tags
* Suchkriterien, z. B. Änderungsdatum, Veröffentlichungsstatus, Live Copy-Status.

Im seitlichen Bedienfeld können Sie außerdem Ihre Sucheinstellungen mit Namen Ihrer Wahl speichern.

Weitere Informationen und Anweisungen zur Verwendung der Suche, Filter, gespeicherte Suche und seitlichem Bedienfeld, finden Sie unter [Suche](/help/sites-authoring/search.md).
