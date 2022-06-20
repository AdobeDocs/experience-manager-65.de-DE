---
title: Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector]
description: Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2660de7c-0281-4884-98d9-e78f20cf571c
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 96%

---

# Konfigurieren von [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-configure.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-connector-configure.html?lang=en) |

Ein Benutzer mit Administratorzugriff in [!DNL Adobe Experience Manager]  konfiguriert den erweiterten Connector nach der Installation. Anweisungen zur Installation finden Sie unter [Installieren des Connectors](/help/assets/workfront-integrations.md).

>[!IMPORTANT]
>
>* Adobe fordert, dass die Bereitstellung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services] durchgeführt wird. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt erweiterte Connector-Versionen 1.7.4 und höher. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Navigieren Sie zur erweiterten Connector-Version, um sie zu überprüfen. `digital.hoodoo` im linken Bereich in [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de).
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie unter [Prüfungsleitfaden](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


## Konfigurieren von Ereignisabonnements {#event-subscriptions}

Ereignisabonnements werden verwendet, um AEM über Ereignisse zu informieren, die in [!DNL Adobe Workfront] stattfinden. Es gibt drei [!DNL Workfront for Experience Manager enhanced connector]-Funktionen, die Ereignisabonnements benötigen, um zu funktionieren, und zwar:

* Automatische Erstellung von projektgebundenen Ordnern.
* Synchronisierung von Änderungen in benutzerdefinierten Formularwerten in Workfront-Dokumenten mit AEM Asset-Metadaten.
* Automatische Veröffentlichung von Assets in Brand Portal nach Abschluss des Projekts.

Um diese Funktionen nutzen zu können, müssen Sie die Ereignisabonnements aktivieren.

* Bearbeiten Sie die Cloud Services-Konfiguration [!UICONTROL Workfront-Tools], die Sie in Schritt 5 erstellt haben, und wählen Sie die Registerkarte [!UICONTROL Ereignisabonnements].
* Wählen Sie die [!UICONTROL benutzerdefinierte Workfront-Integration] aus, die Sie in Abschnitt 6 erstellt haben.
* Klicken Sie auf [!UICONTROL Workfront-Ereignisabonnements aktivieren].

   ![Ereignisabonnement](/help/assets/assets/event-subs.png)

## Konfigurieren von verknüpften Ordnern {#linked-folders}

Gehen Sie wie folgt vor, um die Ereignisse zu abonnieren:

1. Navigieren Sie zur Registerkarte **[!UICONTROL Ereignisabonnements]** in den Cloud-Services.
1. Wählen Sie die in [!DNL Workfront] erstellte benutzerdefinierte Integration aus.
1. Klicken Sie auf **[!UICONTROL Workfront-Ereignisabonnements aktivieren]**.

### Konfiguration der verknüpften Ordnerstruktur {#linked-folder-structure}

1. Gehen Sie in den Cloud-Services zur Registerkarte „Projektverknüpfte Ordner“.
1. Übergeordneter Pfad des verknüpften Ordners: Wählen Sie einen Ordner im DAM aus, in dem Sie die verknüpften Ordner erstellen möchten. Wenn Sie das Feld leer lassen, wird standardmäßig /content/dam verwendet. Stellen Sie sicher, dass das Metadatenschema für Workfront-Tools und das Metadatenschema für Workfront-Ordner mit verknüpften Ordnern auf den ausgewählten Ordner angewendet wurden.
1. Verknüpfte Ordnerstruktur: Geben Sie durch Kommas getrennte Werte ein. Jeder Wert sollte `DE:<some-project-custom-form-field>`, Portfolio, Programm, Jahr, Name oder ein „literaler Zeichenfolgenwert“ sein (letzteres in Anführungszeichen). Er ist derzeit auf Portfolio,Programm,Jahr,DE:Projekttyp,Name festgelegt.
1. Das Kontrollkästchen „Verknüpfte Ordnertitel in Workfront unter Verwendung der Namen der Ordnerstruktur erstellen“ sollte aktiviert werden, wenn der Titel des Ordners in Workfront alle Ordner in der Struktur enthalten soll. Andernfalls wird der Titel des letzten Ordners verwendet.
1. Im Mehrfachfeld „Unterordner“ können Sie eine Liste von Ordnern angeben, die als Unterordner des verknüpften Ordners erstellt werden sollen.
1. Projektstatus: Wählen Sie den Status aus, auf den das Projekt gesetzt werden muss, um den verknüpften Ordner zu erstellen.
1. Verknüpften Ordner in Projekten mit Portfolio erstellen: Liste der Portfolios, denen das Projekt angehören muss, damit der verknüpfte Ordner erstellt werden kann. Lassen Sie diese Liste leer, wenn der verknüpfte Ordner für alle Projektportfolios erstellt werden soll.
1. Verknüpften Ordner in Projekten mit benutzerdefiniertem Formularfeld erstellen: Benutzerdefiniertes Formularfeld und sein entsprechender Wert, den das Projekt haben muss, damit der verknüpfte Ordner erstellt werden kann. Diese Konfiguration wird ignoriert, wenn sie leer gelassen wird. Wählen Sie `CUSTOM FORMS: Create DAM Linked Folder` als Feld und geben Sie `Yes` als Wert ein.
1. Klicken Sie auf „Automatische Erstellung verknüpfter Ordner aktivieren“. Wenn Sie zur Registerkarte „Ereignisabonnements“ zurückkehren, sehen Sie, dass es jetzt ein Erstellungsereignis gibt.

![Konfiguration verknüpfter Ordner](/help/assets/assets/wf-linked-folder-config.png)

## Metadatenschema-Zuordnung {#metadata-schema-mapping}

### Konfigurieren der Ordner-Metadatenzuordnung {#folder-metadata-mapping}

Die Metadaten-Zuordnung zwischen Workfront-Projekten und AEM-Ordnern wird in AEM-Ordner-Metadatenschemata definiert. Ordner-Metadatenschemata sollten wie gewohnt in AEM erstellt und konfiguriert werden. Workfront Tools fügt für jedes Metadatenschema-Formularfeld ein Dropdown-Menü mit automatischer Vervollständigung zu dessen Registerkarte „Einstellungen“ hinzu. In diesem Dropdown-Menü mit automatischer Vervollständigung können Sie angeben, welchem Workfront-Feld jede AEM-Ordnereigenschaft zugeordnet werden soll.

Gehen Sie wie folgt vor, um die Zuordnungen zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Ordner-Metadatenschemata]**.
1. Wählen Sie das Formular für das Ordner-Metadatenschema, das Sie bearbeiten möchten, und klicken Sie auf „Bearbeiten“.
1. Wählen Sie das Formularfeld des Ordner-Metadatenschemas aus, das Sie bearbeiten möchten, und klicken Sie im rechten Bedienfeld auf die Registerkarte „Einstellungen“.
1. Wählen Sie im Feld [!UICONTROL Aus Workfront-Feld zugeordnet] den Namen des Workfront-Felds aus, das Sie der ausgewählten AEM-Ordnereigenschaft zuordnen möchten. Verfügbare Optionen sind:

   * Benutzerdefinierte Formularfelder für Projekte
   * Felder mit Projektübersicht (ID, Name, Beschreibung, Referenznummer, Geplantes Abschlussdatum, Projektinhaber, Projekt-Sponsor, Portfolio oder Programm)

![Konfiguration der Metadatenzuordnung](/help/assets/assets/wf-metadata-mapping-config2.png)

### Konfigurieren der Asset-Metadatenzuordnung {#asset-metadata-mapping}

Die Zuordnung von Metadaten zwischen Adobe Workfront-Dokumenten und Assets wird in AEM-Metadatenschemata definiert. Metadatenschemata sollten wie gewohnt in AEM erstellt und konfiguriert werden. Workfront Tools fügt für jedes Metadatenschema-Formularfeld Konfigurationsoptionen zu dessen Registerkarte „Einstellungen“ hinzu. Mit diesen Optionen können Sie angeben, welchen Workfront-Feldern die einzelnen AEM-Eigenschaften zugeordnet werden sollen.

Gehen Sie wie folgt vor, um die Zuordnungen zu konfigurieren:

1. Navigieren Sie zu **Tools** > **Assets** > **Metadatenschemata**.
1. Wählen Sie das Metadatenschema-Formular aus, das Sie bearbeiten möchten, und klicken Sie auf **Bearbeiten** oder erstellen Sie ein neues Metadatenschema von Grund auf.
1. Wählen Sie das Metadatenschema-Formularfeld aus, das Sie bearbeiten möchten, und wählen Sie die Registerkarte **Einstellungen** im rechten Bedienfeld.
1. Wählen Sie in [!DNL Workfront] unter „Benutzerdefiniertes Formularfeld“ den Namen des [!DNL Workfront]-Feldes, das Sie der ausgewählten AEM-Eigenschaft zuordnen möchten. Verfügbare Optionen sind:

   * Benutzerdefinierte Formularfelder für Dokumente
   * Benutzerdefinierte Formularfelder für Projekte
   * Benutzerdefinierte Formularfelder für Probleme
   * Benutzerdefinierte Formularfelder für Aufgaben
   * Felder zur Projektübersicht (ID, Name, Beschreibung oder Referenznummer)

1. Wenn das als [!UICONTROL Benutzerdefiniertes Workfront-Formularfeld] ausgewählte [!DNL Workfront]-Feld ein Workfront-Benutzerfeld mit Eingabepuffer ist, müssen Sie angeben, welches Workfront-Benutzerfeld Sie zuordnen möchten. Aktivieren Sie dazu die Option „Wert aus dem von Workfront referenzierten Objektfeld abrufen“ und geben Sie dann den Namen des [!UICONTROL benutzerdefinierten Workfront-Formularfelds] an, von dem der zuzuordnende Wert abgerufen werden soll.

   ![Konfiguration der Metadatenzuordnung](/help/assets/assets/wf-metadata-mapping-config1.png)

## Zuordnungseigenschaft {#map-property}

Mit diesem Workflow-Schritt kann ein Benutzer eine Eigenschaft einem benutzerdefinierten [!DNL Workfront]-Formular für ein Projekt, eine Aufgabe, ein Problem oder ein Dokument zuordnen. Das [!DNL Workfront]-Artefakt, auf das sich dieser Schritt auswirkt, wird mithilfe eines relativen Pfads aus der Payload nachgeschlagen. Die Eigenschaften, die zugeordnet werden sollen, werden in der Konfiguration des Schrittdialogfelds gesteuert.

**Typ**: In diesem Feld können Sie den Typ des Workfront-Objekts auswählen, dem die Eigenschaften zugeordnet werden sollen.

**ID-Eigenschaft**: In diesem Feld können Sie den Pfad zur ID des Workfront-Objekts angeben, dem die Eigenschaften zugeordnet werden sollen. Der in diesem Feld angegebene Pfad sollte relativ zur Payload des Workflows sein.

**Eigenschaftszuweisungen**: In diesem Mehrfachfeld können Sie die Zuordnungen zwischen AEM-Eigenschaften und Workfront-Feldern festlegen. Jedes Element im Mehrfachfeld gibt eine Zuordnung an. Jede Zuordnung sollte das Format `<workfront-field>=<aem-mapped-property>` haben.

* Beim `workfront-field` kann es sich handeln um:

   * Ein benutzerdefiniertes Formularfeld, das durch das Präfix `DE:` identifiziert wird.
   * Ein editierbares Feld, das durch seinen Namen identifiziert wird. Die Feldnamen finden Sie unter [[!DNL Workfront] API-Explorer](https://experience.workfront.com/s/api-explorer).

* `aem-mapped-property` kann sein:

   * Ein literaler Wert. Diese sollten von Anführungszeichen umgeben sein.
   * Eine AEM-Eigenschaft. Diese Referenz sollte relativ zur Payload des Workflows sein.
   * Ein benannter Wert. Diese sollten von Klammern umgeben sein.
   * Eine Verkettung der drei oben genannten Elemente. Geben Sie dies mithilfe von `{+}` an.
   * Eine Abwandlung der drei oben genannten Elemente, indem der Wert mit `{replace(<value>,”old-char”,”new-char”)}` umschlossen wird.

* Einige Beispiele:

   * `status="INP"`
   * `DE:Asset Type=jcr:content/metadata/assetType`
   * `DE:Path={path}`
   * `URL=”https://my-aem-author/assets.html”{+}{path}`

![Konfiguration für Zuordnungseigenschaft](/help/assets/assets/wf-map-property-config.png)

## Festlegen des Status {#set-status}

Bearbeiten Sie im Workflow-Editor die Eigenschaften von **[!UICONTROL Workfront - Status festlegen]** auf der Registerkarte **[!UICONTROL Argumente]**.

![Workflow bearbeiten, um Status festzulegen](/help/assets/assets/wf-set-status.png)

## Kommentarsynchronisierung {#comments-sync}

1. Gehen Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]**, wählen Sie die Konfiguration aus und wählen Sie dann **[!UICONTROL Eigenschaften]**.

   ![Kommentarsynchronisierung](/help/assets/assets/comments-sync1.png)

1. Wählen Sie die Registerkarte **[!UICONTROL Ereignis-Abonnements]** und klicken Sie auf **[!UICONTROL Kommentarsynchronisierung aktivieren]** unter der Option **[!UICONTROL Kommentare aus Workfront an AEM senden]**.

   ![Synchronisierung ist aktiviert](/help/assets/assets/wf-comment-sync-enabled.png)

Gehen Sie wie folgt vor, um die Synchronisierung von Kommentaren von Workfront nach AEM zu testen:

1. Navigieren Sie zu einem verknüpften Dokument in Workfront und fügen Sie auf der Registerkarte „Aktualisierungen“ einen Kommentar hinzu.

   ![Kommentar in Workfront hinterlassen](/help/assets/assets/comments-sync2.png)

1. Gehen Sie zum selben verknüpften Dokument in AEM, wählen Sie das Dokument aus und öffnen Sie die Option [!UICONTROL Zeitleiste] in der linken Navigation und wählen Sie dann [!UICONTROL Kommentare] aus. In der linken Seitenleiste werden die Kommentare angezeigt, die aus [!DNL Workfront] synchronisiert wurden.

## Asset-Versionen {#asset-versions}

Um den Versionsverlauf von Assets in AEM beizubehalten, konfigurieren Sie die Asset-Versionierung in AEM.

1. Gehen Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]** und öffnen Sie die Registerkarte **[!UICONTROL Erweitert]**.

1. Wählen Sie die Option **[!UICONTROL Assets mit demselben Namen wie Versionen des vorhandenen Assets speichern]**. Wenn diese Option aktiviert ist, können Sie Assets speichern, die mit demselben Namen und demselben Speicherort wie die Version des vorhandenen Assets hochgeladen wurden. Wenn diese Option deaktiviert ist, wird ein neues Asset mit einem anderen Namen erstellt (z. B. `asset-name.pdf` und `asset-name-1.pdf`).

1. Wählen Sie die Option **[!UICONTROL Asset-Metadaten beim Erstellen einer neuen Version aktualisieren]**. Wenn diese Option aktiviert ist, werden die Asset-Metadaten bei jeder Erstellung einer neuen Version des Assets aktualisiert. Wenn diese Option deaktiviert ist, behält das Asset die Metadaten bei, die es vor dem Erstellen der neuen Version hatte.

![Asset-Versionierung konfigurieren](/help/assets/assets/wf-config-versioning.png)

>[!NOTE]
>
>Die Versionierung wird in verknüpften Ordnern nicht unterstützt. Beim Erstellen eines [!DNL Workfront]-Korrekturabzugs mit einem Dokument innerhalb eines verknüpften Ordners werden die Kommentare und Anmerkungen zur vorherigen Version des Assets entfernt.

## Anhängen benutzerdefinierter Formulare {#attach-custom-forms}

Mit diesem Workflow-Schritt können Benutzer ein benutzerdefiniertes Formular an ein [!DNL Workfront]-Artefakt anhängen. Dieser Workflow-Schritt kann zu jedem Workflow-Modell hinzugefügt werden. Das [!DNL Workfront]-Artefakt, das von diesem Schritt beeinflusst wird, wird mithilfe eines relativen Pfads aus der Payload nachgeschlagen.

Bearbeiten Sie im Workflow-Editor in Experience Manager die Eigenschaften des Workflow-Schritt [!UICONTROL Workfront - Benutzerdefiniertes Formular anhängen].

![benutzerdefinierte Formulare](/help/assets/assets/wf-custom-forms.png).

## Automatisches Veröffentlichen von Assets {#auto-publish-assets}

1. Gehen Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der Workfront-Tools]** und öffnen Sie die Registerkarte **[!UICONTROL Erweitert]**.

1. Wählen Sie **[!UICONTROL Assets, die aus Workfront gesendet werden, automatisch veröffentlichen]**. Diese Option ermöglicht die automatische Veröffentlichung von Assets, wenn sie von Workfront an AEM gesendet werden. Diese Funktion kann bedingt aktiviert werden, indem ein benutzerdefiniertes Workfront-Formularfeld und der Wert angegeben werden, auf den es eingestellt werden soll. Wenn ein Dokument an AEM gesendet wird und die Bedingung erfüllt, wird das Asset automatisch veröffentlicht.

1. Wählen Sie **[!UICONTROL Alle Projekt-Assets nach Abschluss des Projekts in Brand Portal veröffentlichen]**. Diese Option ermöglicht die automatische Veröffentlichung von Assets in [!DNL Brand Portal], wenn der Status des Workfront-Projekts, zu dem sie gehören, in `Complete` geändert wird.

![Konfigurieren automatischer Veröffentlichungen](/help/assets/assets/wf-auto-publish-config.png)

## Aktualisierungen des benutzerdefinierten Formulars im Workfront-Dokument {#subscribe-workfront-doc-custom-form-updates}

Um Änderungen in benutzerdefinierten Formularen von [!DNL Workfront]-Dokumenten zu abonnieren, wählen Sie die entsprechende Option auf der Registerkarte **[!UICONTROL Erweitert]**. Wenn Sie diese Aktualisierungen abonnieren, werden Ihre zugeordnete [!DNL Experience Manager]-Metadatenfelder aktualisiert, sobald das entsprechende Feld im benutzerdefinierten Formular des [!DNL Workfront]-Dokuments geändert wurde.

![Konfiguration für benutzerdefinierte Formularaktualisierungen im Workfront-Dokument in [!DNL Experience Manager]](/help/assets/assets/wf-custom-form-update.png)
