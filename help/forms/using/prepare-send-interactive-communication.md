---
title: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
seo-title: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
description: Über die Benutzeroberfläche der Agenten können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck.
seo-description: Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden
uuid: d1a19b83-f630-4648-9ad2-a22374e31aa9
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 110c86ea-9bd8-4018-bfcc-ca33e6b3f3ba
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2062'
ht-degree: 37%

---


# Interaktive Kommunikation mithilfe der Benutzeroberfläche für Agenten vorbereiten und senden {#prepare-and-send-interactive-communication-using-the-agent-ui}

Über die Benutzeroberfläche der Agenten können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck.

## Überblick {#overview}

Nachdem eine interaktive Kommunikation erstellt wurde, kann der Agent die Interaktive Kommunikation in der Agent-Benutzeroberfläche öffnen und eine Empfänger-spezifische Kopie erstellen, indem er Daten eingibt und Inhalte und Anlagen verwaltet. Schließlich kann der Agent die interaktive Kommunikation an einen Nachbearbeitungsprozess senden.

Während der Vorbereitung der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche verwaltet der Agent die folgenden Aspekte der interaktiven Kommunikation in der Agent-Benutzeroberfläche, bevor er sie an einen Nachbearbeitungsprozess übermittelt:

* **Daten**: Die Registerkarte „Daten“ der Benutzeroberfläche für Agenten zeigt alle vom Agenten bearbeitbaren Variablen und entsperrten Datenmodelleigenschaften in der interaktiven Kommunikation an. Diese Variablen/Eigenschaften werden beim Bearbeiten oder Erstellen von Dokumentfragmenten in der interaktiven Kommunikation erstellt. Die Registerkarte „Daten“ enthält auch alle Felder, die in der XDP/Druckkanalvorlage erstellt wurden. Die Registerkarte &quot;Daten&quot;wird nur angezeigt, wenn Variablen, Formulardatenmodelleigenschaften oder Felder in der interaktiven Kommunikation vorhanden sind, die vom Agenten bearbeitet werden können.
* **Inhalt**: Auf der Registerkarte „Inhalt“ verwalten Sie den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen in der interaktiven Kommunikation. Der Agent kann die Änderungen im Dokument-Fragment wie zulässig vornehmen, während die Interaktive Kommunikation in den Eigenschaften dieser Dokument-Fragmente erstellt wird. Der Agent kann auch ein Dokumentfragment neu anordnen, hinzufügen/entfernen und Seitenumbrüche hinzufügen, sofern dies zulässig ist.
* **Anlagen**: Die Registerkarte &quot;Anlagen&quot;wird in der Benutzeroberfläche des Agenten nur angezeigt, wenn die interaktive Kommunikation über Anlagen verfügt oder der Agent über Bibliothekszugriff verfügt. Der Agent darf die Anlagen ändern oder bearbeiten.

## Vorbereitung der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche {#prepare-interactive-communication-using-the-agent-ui}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.
1. Wählen Sie die entsprechende interaktive Kommunikation aus und tippen Sie auf **[!UICONTROL Benutzeroberfläche des offenen Agenten]**.

   >[!NOTE]
   >
   >Die Benutzeroberfläche des Agenten funktioniert nur, wenn die ausgewählte Interaktive Kommunikation über einen Kanal zum Drucken verfügt.

   ![openagentiui](assets/openagentiui.png)

   Basierend auf dem Inhalt und den Eigenschaften der interaktiven Kommunikation wird die Benutzeroberfläche für Agenten mit den folgenden drei Registerkarten angezeigt: Daten, Inhalt und Anlage.

   ![agentuitabs](assets/agentuitabs.png)

   Fahren Sie mit der Dateneingabe, der Verwaltung des Inhalts und der Verwaltung der Anlagen fort.

### Daten eingeben {#enter-data}

1. Geben Sie auf der Registerkarte „Daten“ die erforderlichen Daten für Variablen, Formulardatenmodelleigenschaften und Druckvorlagenfelder (XDP) ein. Füllen Sie alle erforderlichen Felder mit einem Sternchen (&amp;ast;) aus, um die Schaltfläche **Senden** zu aktivieren.

   Tippen Sie auf einen Datenfeldwert in der Vorschau Interaktive Kommunikation, um das entsprechende Datenfeld auf der Registerkarte &quot;Daten&quot;zu markieren oder umgekehrt.

### Inhalt verwalten {#manage-content}

Verwalten Sie auf der Registerkarte „Inhalt“ den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen in der interaktiven Kommunikation.

1. Wählen Sie **[!UICONTROL Inhalt]**. Die Registerkarte &quot;Inhalt&quot;der interaktiven Kommunikation wird angezeigt.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ ggf. die Dokumentfragmente. Um den Fokus auf das relevante Fragment in der Inhaltshierarchie zu legen, können Sie entweder auf die entsprechende Zeile oder den entsprechenden Absatz in der Vorschau Interaktive Kommunikation tippen oder direkt in der Inhaltshierarchie auf das Fragment tippen.

   Beispielsweise wird das Dokumentfragment mit der Zeile „Jetzt online bezahlen ...“ in der Vorschau in der untenstehenden Grafik ausgewählt und das gleiche Dokumentfragment wurde auf der Registerkarte „Inhalt“ ausgewählt.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   Wenn Sie auf der Registerkarte &quot;Inhalt&quot;oder &quot;Daten&quot;links oben auf der Vorschau auf &quot;Ausgewählte Module im Inhalt markieren&quot;( ![highlightsselectedModuleIncontentccr](assets/highlightselectedmodulesincontentccr.png)) tippen, können Sie die Funktion deaktivieren oder aktivieren, um zum Dokument-Fragment zu wechseln, wenn auf den entsprechenden Text, Absatz oder das Datenfeld in der Vorschau getippt/ausgewählt wird.

   Die Fragmente, die vom Agenten beim Erstellen der interaktiven Kommunikation bearbeitet werden dürfen, haben das Symbol Ausgewählten Inhalt bearbeiten ( ![iconeditselectedcontent](assets/iconeditselectedcontent.png)). Tippen Sie auf das Symbol „Ausgewählten Inhalt bearbeiten“, um das Fragment im Bearbeitungsmodus zu starten und Änderungen daran vorzunehmen. Verwenden Sie die folgenden Optionen zum Formatieren und Verwalten von Text:

   * [Formatierungsoptionen](#formattingtext)

      * [Formatierten Text aus anderen Anwendungen kopieren/einfügen](#pasteformattedtext)
      * [Teile des Textes markieren](#highlightemphasize)
   * [Sonderzeichen](#specialcharacters)
   * [Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md)

   Weitere Informationen zu den Aktionen, die für verschiedene Fragmente des Dokuments in der Agent-Benutzeroberfläche verfügbar sind, finden Sie unter [Aktionen und Informationen in der Agent-Benutzeroberfläche](#actionsagentui).

1. Um der Druckausgabe der interaktiven Kommunikation einen Seitenumbruch hinzuzufügen, platzieren Sie den Cursor an der Stelle, an der Sie einen Seitenumbruch einfügen möchten, und wählen Sie &quot;Seitenumbruch vor&quot;oder &quot;Seitenumbruch nach&quot;( ![pagebreakVorher](assets/pagebreakbeforeafter.png)).

   Ein Platzhalter für einen expliziten Seitenumbruch wird in der interaktiven Kommunikation eingefügt. Sie können in der Druckvorschau anzeigen, wie sich ein expliziter Seitenumbruch auf die interaktive Kommunikation auswirkt.

   ![explicitpagebreak](assets/explicitpagebreak.png)

   Fahren Sie mit der Verwaltung der Anlagen der interaktiven Kommunikation fort.

### Anlagen verwalten {#manage-attachments}

1. Wählen Sie **[!UICONTROL Anlage]**. Die Benutzeroberfläche für Agenten zeigt die verfügbaren Anlagen so an, wie sie beim Erstellen der interaktiven Kommunikation eingerichtet wurden.

   Sie können festlegen, dass keine Anlage zusammen mit der interaktiven Kommunikation gesendet werden soll, indem Sie auf das Symbol &quot;Ansicht&quot;tippen, und Sie können auf das Kreuz in der Anlage tippen, um sie zu löschen (wenn der Agent die Anlage löschen oder ausblenden darf). Für die Anhänge, die beim Erstellen der interaktiven Kommunikation als obligatorisch festgelegt wurden, sind die Symbole „Anzeigen“ und „Löschen“ deaktiviert.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. Tippen Sie auf das Symbol &quot;Bibliothekszugriff&quot;( ![Bibliothekszugriff](assets/libraryaccess.png)), um auf die Inhaltsbibliothek zuzugreifen und DAM-Assets als Anlagen einzufügen.

   >[!NOTE]
   >
   >Das Symbol &quot;Bibliothekszugriff&quot;ist nur verfügbar, wenn beim Erstellen der Interaktiven Kommunikation der Bibliothekszugriff aktiviert wurde (in den Eigenschaften des Dokument-Containers des Kanals &quot;Drucken&quot;).

1. Wenn die Reihenfolge der Anhänge beim Erstellen der interaktiven Kommunikation nicht gesperrt war, können Sie die Reihenfolge der Anhänge neu anordnen, indem Sie einen Anhang auswählen und auf die Pfeile nach unten oder nach oben tippen.
1. Verwenden Sie Webvorschau und Druckvorschau, um zu sehen, ob die beiden Ausgaben Ihren Anforderungen entsprechen.

   Wenn die Vorschauen zufriedenstellend sind, tippen Sie auf **[!UICONTROL Senden]**, um die interaktive Kommunikation an einen Nachbearbeitungsprozess zu senden/zu senden. Um Änderungen vorzunehmen, beenden Sie die Vorschau, um zu den vorzunehmenden Änderungen zurückzukehren.

## Text formatieren {#formattingtext}

Beim Bearbeiten eines Textfragments in der Benutzeroberfläche für Agenten ändert sich die Symbolleiste abhängig vom Typ der von Ihnen vorgenommenen Änderungen: Schriftart, Absatz oder Liste:

![](assets/typeofformattingtoolbar.png) ![typeofformattingtoolbarFont, Symbolleiste](do-not-localize/fonttoolbar.png)

Schriftart-Symbolleiste

![Absatz-Symbolleiste](do-not-localize/paragraphtoolbar.png)

Absatz-Symbolleiste

![Liste-Symbolleiste](do-not-localize/listtoolbar.png)

Liste-Symbolleiste

### Teile des Textes markieren/hervorheben  {#highlightemphasize}

Um Teile eines Textes in einem bearbeitbaren Fragment hervorzuheben, wählen Sie den Text aus und tippen Sie auf „Hervorhebungsfarbe“.

![highlighttextagentui](assets/highlighttextagentui.png)

### Formatierten Text einfügen {#pasteformattedtext}

![pastedtext](assets/pastedtext.png)

### Sonderzeichen in Text einfügen {#specialcharacters}

Die Benutzeroberfläche für Agenten enthält integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung](/help/forms/using/custom-special-characters.md) hinzufügen.

#### Anlagenübermittlung {#attachmentdelivery}

* Wenn die interaktive Kommunikation mit serverseitigen APIs als interaktive oder nicht interaktive PDF gerendert wird, enthält die gerenderte PDF-Datei Anlagen als PDF-Anlagen.
* Wenn ein mit einer interaktiven Kommunikation verknüpfter Nachbearbeitungsprozess als Teil der Benutzeroberfläche &quot;Mit Agent senden&quot;geladen wird, werden Anlagen als Parameter &quot;Liste&lt;com.adobe.idp.Dokument> inAttachmentDocs&quot;übergeben.
* Vordefinierte Übermittlungsmechanismen, wie z. B. E-Mail und Drucken, übermitteln auch Anlagen zusammen mit einer PDF-Datei der interaktiven Kommunikation.

## Aktionen und Informationen, die auf der Benutzeroberfläche für Agenten verfügbar sind  {#actionsagentui}

### Dokumentfragmente {#document-fragments}

![](do-not-localize/contentoptionsdocfragments.png)

* **Pfeile nach oben bzw. nach unten**: Pfeile zum Verschieben von Dokumentenfragmenten nach unten oder oben in der interaktiven Kommunikation.
* **Löschen**: Wenn zulässig, löschen Sie das Dokumentfragment aus der interaktiven Kommunikation.
* **Seitenumbruch vor** (anwendbar für untergeordnete Fragmente des Zielbereichs): Fügt Seitenumbruch vor dem Dokumentfragment ein.
* **Einzug:** Einzug eines Dokumentenfragments vergrößern oder verkleinern.
* **Seitenumbruch nach**  (gilt für untergeordnete Fragmente des Bereichs Zielgruppe): Fügt nach dem Fragment des Dokuments einen Seitenumbruch ein.

![docfragoptions](assets/docfragoptions.png)

* Bearbeiten (nur Textfragmente): Öffnen Sie den Rich-Text-Editor zum Bearbeiten des Textdokumentfragments. Weitere Informationen finden Sie unter [Text formatieren](#formattingtext).

* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein/schließt sie daraus aus.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

### Listendokumentfragmente  {#list-document-fragments}

![listoptions](assets/listoptions.png)

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein/schließt sie daraus aus.
* Aufzählungszeichen/Nummerierungen überspringen: Aktivieren Sie „Aufzählungszeichen/Nummerierungen überspringen“ im Listendokumentfragment.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

## Interaktive Kommunikation als Entwurf speichern {#save-as-draft}

Sie können die Agent-Benutzeroberfläche verwenden, um einen oder mehrere Entwürfe für jede interaktive Kommunikation zu speichern und den Entwurf später abzurufen, um weiter daran zu arbeiten. Sie können für jeden Entwurf einen anderen Namen angeben, um ihn zu identifizieren.

Adobe empfiehlt, diese Anweisungen nacheinander auszuführen, um eine interaktive Kommunikation erfolgreich als Entwurf zu speichern.

### Aktivieren Sie die Funktion Als Entwurf speichern {#before-save-as-draft}

Die Funktion Als Entwurf speichern ist standardmäßig nicht aktiviert. Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Implementieren Sie die Dienstleister-Schnittstelle (SPI) [ccrDocumentInstance](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/ccr/ccrDocumentInstance/api/services/CCRDocumentInstanceService.html).

   Mit der SPI können Sie die Entwurfsversion der interaktiven Kommunikation mit einer Entwurfs-ID als eindeutigen Bezeichner in der Datenbank speichern. Bei diesen Anweisungen wird davon ausgegangen, dass Sie bereits über Kenntnisse zum Erstellen eines OSGi-Bundles mithilfe eines Maven-Projekts verfügen.

   Eine Beispielimplementierung der SPI finden Sie unter [Beispielimplementierung der ccrDocumentInstance-Instanz](#sample-ccrDocumentInstance-spi).
1. Öffnen Sie `http://<hostname>:<port>/ system/console/bundles` und tippen Sie auf **[!UICONTROL Installieren/Aktualisieren]**, um das OSGi-Bundle hochzuladen. Überprüfen Sie, ob der Status des hochgeladenen Pakets als **Aktiv** angezeigt wird. Starten Sie den Server neu, wenn der Status des Pakets nicht als **Aktiv** angezeigt wird.
1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf.
1. Tippen Sie auf **[!UICONTROL Korrespondenzkonfiguration erstellen]**.
1. Wählen Sie **[!UICONTROL Speichern mit CCRDocumentInstanceService]** aktivieren und tippen Sie auf **[!UICONTROL Speichern]**.

### Interaktive Kommunikation als Entwurf speichern {#save-as-draft-agent-ui}

Führen Sie die folgenden Schritte aus, um eine interaktive Kommunikation als Entwurf zu speichern:

1. Wählen Sie im Forms Manager eine interaktive Kommunikation aus und tippen Sie auf **[!UICONTROL Benutzeroberfläche des Agenten öffnen]**.

1. Nehmen Sie die gewünschten Änderungen in der Benutzeroberfläche des Agenten vor und tippen Sie auf **[!UICONTROL Als Entwurf speichern]**.

1. Geben Sie den Namen des Entwurfs im Feld **[!UICONTROL Name]** ein und tippen Sie auf **[!UICONTROL Fertig]**.

Nachdem Sie die interaktive Kommunikation als Entwurf gespeichert haben, tippen Sie auf **[!UICONTROL Änderungen speichern]**, um weitere Änderungen am Entwurf zu speichern.

### Entwurf einer interaktiven Kommunikation abrufen{#retrieve-draft}

Nachdem Sie eine interaktive Kommunikation als Entwurf gespeichert haben, können Sie sie abrufen, um die Bearbeitung fortzusetzen. Rufen Sie die interaktive Kommunikation ab, indem Sie:

`https://server:port/aem/forms/createcorrespondence.hmtl?draftid=[draftid]`

[draftid] bezieht sich auf den eindeutigen Bezeichner für die Entwurfsversion, die nach dem Speichern einer interaktiven Kommunikation als Entwurf generiert wird.

>[!NOTE]
>
>Wenn Sie Änderungen an der interaktiven Kommunikation vornehmen, nachdem Sie sie als Entwurf gespeichert haben, kann der Entwurf nicht geöffnet werden.

### Beispiel für eine ccrDocumentInstance-SPI-Implementierung {#sample-ccrDocumentInstance-spi}

Implementieren Sie die SPI `ccrDocumentInstance`, um eine interaktive Kommunikation als Entwurf zu speichern. Im Folgenden finden Sie eine Beispielimplementierung von `ccrDocumentInstance` SPI.

```javascript
package Implementation;

import com.adobe.fd.ccm.ccr.ccrDocumentInstance.api.exception.CCRDocumentException;
import com.adobe.fd.ccm.ccr.ccrDocumentInstance.api.model.CCRDocumentInstance;
import com.adobe.fd.ccm.ccr.ccrDocumentInstance.api.services.CCRDocumentInstanceService;
import org.apache.commons.lang3.StringUtils;
import org.osgi.service.component.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import java.util.*;


@Component(service = CCRDocumentInstanceService.class, immediate = true)
public class CCRDraftService implements CCRDocumentInstanceService {

    private static final Logger logger = LoggerFactory.getLogger(CCRDraftService.class);

    private HashMap<String, Object> draftDataMap = new HashMap<>();

    @Override
    public String save(CCRDocumentInstance ccrDocumentInstance) throws CCRDocumentException {
        String documentInstanceName = ccrDocumentInstance.getName();
        if (StringUtils.isNotEmpty(documentInstanceName)) {
            logger.info("Saving ccrData with name : {}", ccrDocumentInstance.getName());
            if (!CCRDocumentInstance.Status.SUBMIT.equals(ccrDocumentInstance.getStatus())) {
                ccrDocumentInstance = mySQLDataBaseServiceCRUD(ccrDocumentInstance,null, "SAVE");
            }
        } else {
            logger.error("Could not save data as draft name is empty");
        }
        return ccrDocumentInstance.getId();
    }

    @Override
    public void update(CCRDocumentInstance ccrDocumentInstance) throws CCRDocumentException {
        String documentInstanceName = ccrDocumentInstance.getName();
        if (StringUtils.isNotEmpty(documentInstanceName)) {
            logger.info("Saving ccrData with name : {}", documentInstanceName);
            mySQLDataBaseServiceCRUD(ccrDocumentInstance, ccrDocumentInstance.getId(), "UPDATE");
        } else {
            logger.error("Could not save data as draft Name is empty");
        }
    }

    @Override
    public CCRDocumentInstance get(String id) throws CCRDocumentException {
        CCRDocumentInstance cCRDocumentInstance;
        if (StringUtils.isEmpty(id)) {
            logger.error("Could not retrieve data as draftId is empty");
            cCRDocumentInstance = null;
        } else {
            cCRDocumentInstance = mySQLDataBaseServiceCRUD(null, id,"GET");
        }
        return cCRDocumentInstance;
    }

    @Override
    public List<CCRDocumentInstance> getAll(String userId, Date creationTime, Date updateTime,
                                            Map<String, Object> optionsParams) throws CCRDocumentException {
        List<CCRDocumentInstance> ccrDocumentInstancesList = new ArrayList<>();

        HashMap<String, Object> allSavedDraft = mySQLGetALLData();
        for (String key : allSavedDraft.keySet()) {
            ccrDocumentInstancesList.add((CCRDocumentInstance) allSavedDraft.get(key));
        }
        return ccrDocumentInstancesList;
    }

    //The APIs call the service in the database using the following section.
    private CCRDocumentInstance mySQLDataBaseServiceCRUD(CCRDocumentInstance ccrDocumentInstance,String draftId, String method){
        if(method.equals("SAVE")){

            String autoGenerateId = draftDataMap.size() + 1 +"";
            ccrDocumentInstance.setId(autoGenerateId);
            draftDataMap.put(autoGenerateId, ccrDocumentInstance);
            return ccrDocumentInstance;

        }else if (method.equals("UPDATE")){

            draftDataMap.put(ccrDocumentInstance.getId(), ccrDocumentInstance);
            return ccrDocumentInstance;

        }else if(method.equals("GET")){

            return (CCRDocumentInstance) draftDataMap.get(draftId);

        }
        return null;
    }

    private HashMap<String, Object> mySQLGetALLData(){
        return draftDataMap;
    }
}
```

Die Vorgänge `save`, `update`, `get` und `getAll` rufen den Datenbankdienst auf, um eine interaktive Kommunikation als Entwurf zu speichern, eine interaktive Kommunikation zu aktualisieren, Daten aus der Datenbank abzurufen und Daten für alle in der Datenbank verfügbaren interaktiven Kommunikation abzurufen. In diesem Beispiel wird `mySQLDataBaseServiceCRUD` als Name des Datenbankdiensts verwendet.

In der folgenden Tabelle wird die Beispielimplementierung von `ccrDocumentInstance` SPI beschrieben. Es wird gezeigt, wie die Vorgänge `save`, `update`, `get` und `getAll` den Datenbankdienst in der Beispielimplementierung aufrufen.

<table> 
 <tbody>
 <tr>
  <td><p><strong>Vorgang</strong></p></td>
  <td><p><strong>Beispiele für Datenbankdienste</strong></p></td> 
   </tr>
  <tr>
   <td><p>Sie können entweder einen Entwurf für eine interaktive Kommunikation erstellen oder ihn direkt senden. Die API für den Speichervorgang prüft, ob die interaktive Kommunikation als Entwurf übermittelt wird und einen Namen für den Entwurf enthält. Die API ruft dann den Dienst mySQLDataBaseServiceCRUD mit Save als Eingabemethode auf.</p></br><img src="assets/save-as-draft-save-operation.png"/></br>[#$sd1_sf1_dp9]</td>
   <td><p>Der mySQLDataBaseServiceCRUD-Dienst überprüft Save als Eingabemethode und generiert eine automatisch generierte Entwurfs-ID und gibt sie an AEM zurück. Die Logik zum Generieren einer Entwurfs-ID kann je nach Datenbank variieren.</p></br><img src="assets/save-operation-service.png"/></br>[#$sd1_sf1_dp13]</td>
   </tr>
  <tr>
   <td><p>Die API für den Aktualisierungsvorgang ruft den Status des Entwurfs der interaktiven Kommunikation ab und prüft, ob die interaktive Kommunikation einen Namen enthält. Die API ruft den Dienst mySQLDataBaseServiceCRUD auf, um diesen Status in der Datenbank zu aktualisieren.</p></br><img src="assets/save-as-draft-update-operation.png"/></br>[#$sd1_sf1_dp17]</td>
   <td><p>Der mySQLDataBaseServiceCRUD-Dienst überprüft Update als Eingabemethode und speichert den Status des Entwurfs der interaktiven Kommunikation in der Datenbank.</br></p><img src="assets/update-operation-service.png"/></td>
   </tr>
   <tr>
   <td><p>Die API für den get-Vorgang prüft, ob die interaktive Kommunikation eine Entwurfs-ID enthält. Die API ruft dann den Dienst mySQLDataBaseServiceCRUD mit Get als Eingabemethode auf, um die Daten für die interaktive Kommunikation abzurufen.</br></p><img src="assets/save-as-draft-get-operation.png"/></td>
   <td><p>Der mySQLDataBaseServiceCRUD-Dienst überprüft Get als Eingabemethode und ruft die Daten für die interaktive Kommunikation basierend auf der Entwurfs-ID ab.</p></br><img src="assets/get-operation-service.png"/></br>[#$sd1_sf1_dp29]</td>
   </tr>
   <tr>
   <td><p>Die API für den getAll-Vorgang ruft den Dienst mySQLGetALLData auf, um Daten für alle in der Datenbank gespeicherten interaktiven Nachrichten abzurufen.</br></p><img src="assets/save-as-draft-getall-operation.png"/></td>
   <td><p>Der mySQLGetALLData-Dienst ruft Daten für alle in der Datenbank gespeicherten interaktiven Kommunikation ab.</p></br><img src="assets/getall-operation-service.png"/></br>[#$sd1_sf1_dp37]</td>
   </tr>
  </tbody>
</table>

Die folgende Tabelle zeigt ein Beispiel für die `pom.xml`-Datei, die Teil der Implementierung ist:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.adobe.livecycle</groupId>
    <artifactId>draft-sample</artifactId>
    <version>2.0.0-SNAPSHOT</version>

    <name>Interact</name>
    <packaging>bundle</packaging>

    <dependencies>
        <dependency>
            <groupId>com.adobe.aemfd</groupId>
            <artifactId>aemfd-client-sdk</artifactId>
            <version>6.0.160</version>
        </dependency>
    </dependencies>


    <!-- ====================================================================== -->
    <!-- B U I L D D E F I N I T I O N -->
    <!-- ====================================================================== -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.felix</groupId>
                <artifactId>maven-bundle-plugin</artifactId>
                <version>3.3.0</version>
                <extensions>true</extensions>
                <executions>
                    <!--Configure extra execution of 'manifest' in process-classes phase to make sure SCR metadata is generated before unit test runs-->
                    <execution>
                        <id>scr-metadata</id>
                        <goals>
                            <goal>manifest</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <exportScr>true</exportScr>
                    <instructions>
                        <!-- Enable processing of OSGI DS component annotations -->
                        <_dsannotations>*</_dsannotations>
                        <!-- Enable processing of OSGI metatype annotations -->
                        <_metatypeannotations>*</_metatypeannotations>
                        <Bundle-SymbolicName>${project.groupId}-${project.artifactId}</Bundle-SymbolicName>
                    </instructions>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>8</source>
                    <target>8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
    <profiles>
        <profile>
            <id>autoInstall</id>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.apache.sling</groupId>
                        <artifactId>maven-sling-plugin</artifactId>
                        <executions>
                            <execution>
                                <id>install-bundle</id>
                                <phase>install</phase>
                                <goals>
                                    <goal>install</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
    </profiles>

</project>
```

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die `aemfd-client-sdk`-Abhängigkeit in der Datei `pom.xml` auf 6.0.160 aktualisieren.
