---
title: Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector]
description: Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
source-git-commit: 8d39e1c86e5185a181400f10b7822a57c9d3aeae
workflow-type: tm+mt
source-wordcount: '1635'
ht-degree: 0%

---


# Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager] konfiguriert den erweiterten Connector nach der Installation. Anweisungen zur Installation finden Sie unter [Connector installieren](/help/assets/workfront-integrations.md).

>[!IMPORTANT]
>
>Adobe erfordert Bereitstellung und Konfiguration der [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird ohne zertifizierten Partner bereitgestellt und konfiguriert oder [!DNL Adobe Professional Services], wird sie von Adobe nicht unterstützt.
>
>Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager] die diesen Connector redundant machen; In diesem Fall kann es erforderlich sein, dass Kunden von der Verwendung dieses Connectors übergehen.

## Ereignisabonnements konfigurieren {#event-subscriptions}

Ereignisabonnements werden verwendet, um AEM über Ereignisse zu informieren, die in [!DNL Adobe Workfront]. Es gibt drei [!DNL Workfront for Experience Manager enhanced connector] -Funktionen, für die Ereignisanmeldungen erforderlich sind, um zu funktionieren, sind:

* Automatische Erstellung von projektbezogenen Ordnern.
* Synchronisierung von Änderungen in benutzerdefinierten Formularwerten in Workfront-Dokumenten mit AEM Asset-Metadaten.
* Automatische Veröffentlichung von Assets in Brand Portal nach Abschluss des Projekts.

Um diese Funktionen zu verwenden, aktivieren Sie Abonnements für Ereignisse.

* Bearbeiten [!UICONTROL Workfront-Tools] Die in Schritt 5 erstellte Cloud Services-Konfiguration und wählen Sie die [!UICONTROL Ereignisabos] Registerkarte.
* Wählen Sie die [!UICONTROL Benutzerdefinierte Workfront-Integration] haben Sie in Abschnitt 6 erstellt.
* Klicken [!UICONTROL Aktivieren von Workfront-Ereignisanmeldungen].

   ![Ereignisabonnement](/help/assets/assets/event-subs.png)

## Verknüpfte Ordner konfigurieren {#linked-folders}

Gehen Sie wie folgt vor, um die Ereignisse zu abonnieren:

1. Navigieren Sie zum **[!UICONTROL Ereignisabos]** in den Cloud-Services.
1. Wählen Sie die in erstellte benutzerdefinierte Integration aus. [!DNL Workfront].
1. Klicken **[!UICONTROL Aktivieren von Workfront-Ereignisanmeldungen]**.

### Konfiguration der verknüpften Ordnerstruktur {#linked-folder-structure}

1. Gehen Sie in den Cloud Services zur Registerkarte Projektverknüpfte Ordner .
1. Übergeordneter Pfad des verknüpften Ordners: Wählen Sie einen Ordner im DAM aus, in dem Sie die verknüpften Ordner erstellen möchten. Wenn Sie das Feld leer lassen, wird standardmäßig /content/dam verwendet. Stellen Sie sicher, dass das Metadatenschema für Workfront Tools und das Metadatenschema für Workfront-Ordner mit verknüpften Ordnern auf den ausgewählten Ordner angewendet wurden.
1. Verknüpfte Ordnerstruktur: Geben Sie durch Kommas getrennte Werte ein. Jeder Wert sollte `DE:<some-project-custom-form-field>`, Portfolio, Programm, Jahr, Name oder ein beliebiger &quot;Literaler Zeichenfolgenwert&quot;(dieser letzte Wert mit Anführungszeichen). Sie ist derzeit auf Portfolio,Programm,Jahr,DE:Projekttyp,Name festgelegt.
1. Erstellen Sie einen verknüpften Ordnertitel in Workfront mithilfe des Kontrollkästchens Ordnernamen , wenn der Ordnertitel in Workfront alle Ordner in der Struktur enthalten soll. Andernfalls wird es der Titel des letzten Ordners sein.
1. Mehrfeld &quot;Unterordner&quot;ermöglicht die Angabe einer Liste von Ordnern, die als untergeordneter Ordner des verknüpften Ordners erstellt werden sollen.
1. Projektstatus: Wählen Sie den Status aus, auf den das Projekt gesetzt werden muss, um den verknüpften Ordner zu erstellen.
1. Erstellen Sie einen verknüpften Ordner in Projekten mit Portfolio: Liste der Portfolios, zu denen das Projekt gehören muss, um den verknüpften Ordner zu erstellen. Lassen Sie diese Liste leer, um den verknüpften Ordner für alle Projektportfolios zu erstellen.
1. Erstellen Sie einen verknüpften Ordner in Projekten mit einem benutzerdefinierten Formularfeld: Benutzerdefiniertes Formularfeld und der entsprechende Wert, den das Projekt haben muss, um den verknüpften Ordner zu erstellen. Diese Konfiguration wird ignoriert, wenn sie leer gelassen wird. Auswählen `CUSTOM FORMS: Create DAM Linked Folder` für das Feld und die Eingabe `Yes` für den Wert.
1. Klicken Sie auf Automatische Erstellung verknüpfter Ordner aktivieren . Wenn Sie zur Registerkarte Ereignisabonnements zurückkehren, sehen Sie, dass es jetzt ein Erstellungsereignis gibt.

![Konfiguration verknüpfter Ordner](/help/assets/assets/wf-linked-folder-config.png)

## Metadatenschema-Zuordnung {#metadata-schema-mapping}

### Konfigurieren der Ordner-Metadatenzuordnung {#folder-metadata-mapping}

Die Metadaten-Zuordnung zwischen Workfront-Projekten und AEM-Ordnern wird in AEM Ordner-Metadatenschemata definiert. Ordner-Metadatenschemata sollten wie gewohnt in AEM erstellt und konfiguriert werden. Workfront Tools fügt der Registerkarte &quot;Einstellungen&quot;jedes Ordner-Metadatenschema-Formularfelds ein Dropdown-Menü zum automatischen Ausfüllen hinzu. In diesem Dropdown-Menü für die automatische Vervollständigung können Sie angeben, welchem Workfront-Feld jede AEM Ordnereigenschaft zugeordnet werden soll.

Gehen Sie wie folgt vor, um die Zuordnungen zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Wählen Sie das zu bearbeitende Ordner-Metadatenschema-Formular aus und klicken Sie auf Bearbeiten.
1. Wählen Sie das zu bearbeitende Ordner-Metadatenschema-Formularfeld aus und klicken Sie im rechten Bereich auf die Registerkarte Einstellungen .
1. In [!UICONTROL Aus Workfront-Feld zugeordnet] Wählen Sie den Namen des Workfront-Felds aus, das Sie der ausgewählten AEM Ordnereigenschaft zuordnen möchten. Verfügbare Optionen sind:

   * Benutzerdefinierte Formularfelder für Projekte
   * Felder mit Projektübersicht (ID, Name, Beschreibung, Referenznummer, Geplantes Abschlussdatum, Projektinhaber, Projektsponsor, Portfolio oder Programm)

![Konfiguration der Metadatenzuordnung](/help/assets/assets/wf-metadata-mapping-config2.png)

### Asset-Metadatenzuordnung konfigurieren {#asset-metadata-mapping}

Die Metadaten-Zuordnung zwischen Adobe Workfront-Dokumenten und Assets wird in AEM Metadatenschemata definiert. Metadatenschemata sollten wie gewohnt in AEM erstellt und konfiguriert werden. Workfront Tools fügt Konfigurationsoptionen zur Registerkarte &quot;Einstellungen&quot;jedes Metadatenschema-Formularfelds hinzu. Mit diesen Optionen können Sie angeben, welchen Workfront-Feldern die einzelnen AEM zugeordnet werden sollen.

Gehen Sie wie folgt vor, um die Zuordnungen zu konfigurieren:

1. Navigieren Sie zu **Instrumente** > **Assets** > **Metadatenschemata**.
1. Wählen Sie das Metadatenschema-Formular aus, das Sie bearbeiten möchten, und klicken Sie auf **Bearbeiten** oder erstellen Sie ein neues Metadatenschema von Grund auf.
1. Wählen Sie das Metadatenschema-Formularfeld aus, das Sie bearbeiten möchten, und wählen Sie **Einstellungen** im rechten Bereich.
1. In [!DNL Workfront] Benutzerdefiniertes Formularfeld: Wählen Sie den Namen der [!DNL Workfront] -Feld, das Sie der ausgewählten AEM-Eigenschaft zuordnen möchten. Verfügbare Optionen sind:

   * Benutzerdefinierte Formularfelder dokumentieren
   * Benutzerdefinierte Formularfelder für Projekte
   * Benutzerdefinierte Formularfelder ausgeben
   * Benutzerdefinierte Formularfelder Aufgabenfelder
   * Felder mit Projektübersicht (ID, Name, Beschreibung oder Referenznummer)

1. In dem Fall, in dem die [!DNL Workfront] in [!UICONTROL Workfront Custom Form Field] ist ein Workfront-Benutzertyp-Ahead-Feld. Es muss angegeben werden, welches Workfront-Benutzerfeld Sie zuordnen möchten. Aktivieren Sie dazu die Option Wert aus dem Workfront referenzierten Objektfeld abrufen und geben Sie dann den Namen der [!UICONTROL Benutzerdefiniertes Formularfeld für Workfront-Benutzer] von dem der abzugebende Wert abgerufen werden soll.

   ![Konfiguration der Metadatenzuordnung](/help/assets/assets/wf-metadata-mapping-config1.png)

## Zuordnungseigenschaft {#map-property}

Mit diesem Workflow-Schritt kann ein Benutzer eine Eigenschaft einem [!DNL Workfront] benutzerdefiniertes Formular für ein Projekt, eine Aufgabe, ein Problem oder ein Dokument. Die [!DNL Workfront] Artefakt, auf das dieser Schritt wirkt, wird mithilfe eines relativen Pfads aus der Payload nachgeschlagen. Die Eigenschaften, die zugeordnet werden sollen, werden in der Konfiguration des Schrittdialogs gesteuert.

**Typ**: In diesem Feld können Sie den Workfront-Objekttyp auswählen, dem die Eigenschaften zugeordnet werden sollen.

**ID-Eigenschaft**: In diesem Feld können Sie den Pfad zur ID des Workfront-Objekts angeben, dem die Eigenschaften zugeordnet werden sollen. Der in diesem Feld angegebene Pfad sollte relativ zur Workflow-Payload sein.

**Eigenschaftszuweisungen**: In diesem Multifeld können Sie die Zuordnungen zwischen AEM Eigenschaften und Workfront-Feldern festlegen. Jedes Element im Mehrfachfeld gibt eine Zuordnung an. Jede Zuordnung sollte das Format haben `<workfront-field>=<aem-mapped-property>`.

* Die `workfront-field` kann

   * Ein benutzerdefiniertes Formularfeld, das durch das Präfix identifiziert wird `DE:`.
   * Ein editierbares Feld, das durch seinen Namen identifiziert wird. Die Feldnamen finden Sie unter [[!DNL Workfront] API-Explorer](https://experience.workfront.com/s/api-explorer).

* Die `aem-mapped-property` kann sein:

   * Ein Literalwert. Diese sollten von Anführungszeichen umgeben sein.
   * Eine AEM Eigenschaft. Diese Referenz sollte relativ zur Workflow-Payload sein.
   * Ein benannter Wert. Diese sollten von Klammern umgeben sein.
   * Eine Verkettung der drei oben genannten Elemente. Geben Sie ihn mithilfe von `{+}`.
   * Eine Änderung der drei oben genannten Elemente durch Umgeben des Werts mit `{replace(<value>,”old-char”,”new-char”)}`.

* Beispiele:

   * `status="INP"`
   * `DE:Asset Type=jcr:content/metadata/assetType`
   * `DE:Path={path}`
   * `URL=”https://my-aem-author/assets.html”{+}{path}`

![Konfiguration für Zuordnungseigenschaft](/help/assets/assets/wf-map-property-config.png)

## Status festlegen {#set-status}

Bearbeiten Sie im Workflow-Editor die Eigenschaften von **[!UICONTROL Workfront - Status festlegen]** im **[!UICONTROL Argumente]** Registerkarte.

![Workflow bearbeiten, um Status festzulegen](/help/assets/assets/wf-set-status.png)

## Kommentarsynchronisierung {#comments-sync}

1. In [!DNL Experience Manager], Zugriff **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]**, wählen Sie die Konfiguration aus und wählen Sie **[!UICONTROL Eigenschaften]**.

   ![Kommentarsynchronisierung](/help/assets/assets/comments-sync1.png)

1. Auswählen **[!UICONTROL Ereignisabos]** Registerkarte, klicken Sie auf **[!UICONTROL Kommentarsynchronisierung aktivieren]** on **[!UICONTROL In Workfront vorgenommene Kommentare an AEM senden]** -Option.

   ![Die Synchronisierung ist aktiviert](/help/assets/assets/wf-comment-sync-enabled.png)

Gehen Sie wie folgt vor, um die Synchronisierung von Kommentaren von Workfront mit AEM zu testen:

1. Navigieren Sie zu einem verknüpften Dokument in Workfront und fügen Sie auf der Registerkarte Aktualisierungen einen Kommentar hinzu.

   ![Kommentar in Workfront hinterlassen](/help/assets/assets/comments-sync2.png)

1. Navigieren Sie zum selben verknüpften Dokument in AEM, wählen Sie das Dokument aus und öffnen Sie das [!UICONTROL Timeline] in der linken Navigation und wählen Sie [!UICONTROL Kommentare]. In der linken Seitenleiste werden die Kommentare angezeigt, die aus synchronisiert wurden [!DNL Workfront].

## Asset-Versionen {#asset-versions}

Um den Versionsverlauf von Assets in AEM beizubehalten, konfigurieren Sie die Asset-Versionierung in AEM.

1. In Experience Manager können Sie auf **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]** und öffnen Sie die **[!UICONTROL Erweitert]** Registerkarte.

1. Option auswählen **[!UICONTROL Speichern von Assets mit demselben Namen wie Versionen des vorhandenen Assets]**. Wenn diese Option aktiviert ist, können Sie Assets speichern, die mit demselben Namen und demselben Speicherort wie die Version des vorhandenen Assets hochgeladen wurden. Wenn diese Option deaktiviert ist, wird ein neues Asset mit einem anderen Namen erstellt (z. B. `asset-name.pdf` und `asset-name-1.pdf`).

1. Option auswählen **[!UICONTROL Aktualisieren von Asset-Metadaten beim Erstellen einer neuen Version]**. Wenn diese Option aktiviert ist, werden die Asset-Metadaten bei jeder Erstellung einer neuen Version des Assets aktualisiert. Wenn diese Option deaktiviert ist, behält das Asset die Metadaten bei, die es vor dem Erstellen der neuen Version hatte.

![Konfigurieren der Asset-Versionierung](/help/assets/assets/wf-config-versioning.png)

>[!NOTE]
>
>Die Versionierung wird in verknüpften Ordnern nicht unterstützt. Beim Erstellen einer [!DNL Workfront] mit einem Dokument innerhalb eines verknüpften Ordners, werden die Kommentare und Anmerkungen zur vorherigen Version des Assets entfernt.

## Benutzerdefinierte Formulare anhängen {#attach-custom-forms}

Mit diesem Workflow-Schritt können Benutzer ein benutzerdefiniertes Formular an eine [!DNL Workfront] Artefakt. Dieser Workflow-Schritt kann zu jedem Workflow-Modell hinzugefügt werden. Die [!DNL Workfront] Artefakt, auf das dieser Schritt wirkt, wird mithilfe eines relativen Pfads aus der Payload nachgeschlagen.

Bearbeiten Sie im Workflow-Editor in Experience Manager die Eigenschaften des [!UICONTROL Workfront - Benutzerdefiniertes Formular anhängen] Workflow-Schritt.

![benutzerdefinierte Formulare](/help/assets/assets/wf-custom-forms.png).

## Automatische Veröffentlichung von Assets {#auto-publish-assets}

1. In Experience Manager können Sie auf **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront Tools]** und öffnen Sie die **[!UICONTROL Erweitert]** Registerkarte.

1. Auswählen **[!UICONTROL Automatische Veröffentlichung von Assets beim Senden aus Workfront]**. Diese Option ermöglicht die automatische Veröffentlichung von Assets, wenn sie von Workfront an AEM gesendet werden. Diese Funktion kann bedingt aktiviert werden, indem ein benutzerdefiniertes Workfront-Formularfeld und der Wert angegeben werden, auf den sie eingestellt werden soll. Wenn ein Dokument an AEM gesendet wird und die Bedingung erfüllt, wird das Asset automatisch veröffentlicht.

1. Auswählen **[!UICONTROL Alle Projekt-Assets nach Abschluss des Projekts in Brand Portal veröffentlichen]**. Diese Option ermöglicht die automatische Veröffentlichung von Assets in [!DNL Brand Portal] wenn der Status des Workfront-Projekts, zu dem sie gehören, geändert wird in `Complete`.

![automatische Veröffentlichung konfigurieren](/help/assets/assets/wf-auto-publish-config.png)

## Aktualisierungen des benutzerdefinierten Workfront-Formulars {#subscribe-workfront-doc-custom-form-updates}

Abonnieren der Änderungen in [!DNL Workfront] Benutzerdefinierte Formulare in Dokumenten dokumentieren: Wählen Sie die entsprechende Option in der **[!UICONTROL Erweitert]** Registerkarte. Wenn Sie diese Aktualisierungen abonnieren, wird Ihre zugeordnete [!DNL Experience Manager] Metadatenfelder, wenn das entsprechende Feld in [!DNL Workfront] Das benutzerdefinierte Formular für Dokumente wurde geändert.

![Konfiguration für benutzerdefinierte Formularaktualisierungen in Workfront Document [!DNL Experience Manager]](/help/assets/assets/wf-custom-form-update.png)
