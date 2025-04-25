---
title: Vorbereiten und Senden der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche
description: 'Über die Agent-Benutzeroberfläche können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck. '
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Interactive Communication
exl-id: 4fb82e9b-f870-47db-ac92-2d7510acace8
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2010'
ht-degree: 100%

---

# Vorbereiten und Senden der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche {#prepare-and-send-interactive-communication-using-the-agent-ui}

Über die Agent-Benutzeroberfläche können die Agenten die interaktive Kommunikation vorbereiten und an den Nachbearbeitungsprozess senden. Der Agent nimmt die erforderlichen Änderungen vor und übergibt die interaktive Kommunikation an einen Nachbearbeitungsprozess, z. B. E-Mail oder Druck. 

## Übersicht {#overview}

Nachdem eine interaktive Kommunikation erstellt wurde, kann der Agent die interaktive Kommunikation in der Benutzeroberfläche für Agenten öffnen und eine empfängerspezifische Kopie vorbereiten, indem er Daten eingibt und Inhalte und Anhänge verwaltet. Schließlich kann der Agent die interaktive Kommunikation an einen Nachbearbeitungsprozess senden.

Beim Vorbereiten der interaktiven Kommunikation über die Agent-Benutzeroberfläche verwaltet der Agent die folgenden Aspekte der interaktiven Kommunikation in der Agent-Benutzeroberfläche, bevor er sie an einen Nachbearbeitungsprozess sendet:

* **Daten**: Die Registerkarte „Daten“ der Agent-Benutzeroberfläche zeigt alle vom Agenten bearbeitbaren Variablen und entsperrten Eigenschaften des Formulardatenmodells in der interaktiven Kommunikation an. Diese Variablen/Eigenschaften werden beim Bearbeiten oder Erstellen von Dokumentfragmenten in der interaktiven Kommunikation erstellt. Die Registerkarte „Daten“ enthält auch alle Felder, die in der XDP-/Druckkanalvorlage erstellt wurden. Die Registerkarte „Daten“ wird nur angezeigt, wenn Variablen, Formulardatenmodelleigenschaften oder Felder in der interaktiven Kommunikation vorhanden sind, die vom Agenten bearbeitet werden können.
* **Inhalt**: Auf der Registerkarte „Inhalt“ verwalten Sie den Inhalt, z. B. Dokumentfragmente und die Inhaltsvariablen in der interaktiven Kommunikation. Der Agent kann die Änderungen im Dokumentfragment so vornehmen, wie dies beim Erstellen der interaktiven Kommunikation in den Eigenschaften dieser Dokumentfragmente zulässig ist. Der Agent kann auch ein Dokumentfragment neu anordnen, hinzufügen/entfernen und Seitenumbrüche hinzufügen, sofern dies zulässig ist.
* **Anlagen**: Die Registerkarte „Anlagen“ wird nur dann in der Agent-Benutzeroberfläche angezeigt, wenn die interaktive Kommunikation Anlagen hat oder der Agent über Bibliothekszugriff verfügt. Der Agent darf die Anlagen ändern oder bearbeiten.

## Vorbereiten der interaktiven Kommunikation mithilfe der Agent-Benutzeroberfläche {#prepare-interactive-communication-using-the-agent-ui}

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.
1. Wählen Sie die entsprechende interaktive Kommunikation und dann **[!UICONTROL Agent-UI öffnen]** aus.

   >[!NOTE]
   >
   >Die Agent-Benutzeroberfläche funktioniert nur, wenn die ausgewählte interaktive Kommunikation über einen Druckkanal verfügt.

   ![openagentiui](assets/openagentiui.png)

   Basierend auf dem Inhalt und den Eigenschaften der interaktiven Kommunikation wird die Benutzeroberfläche für Agenten mit den folgenden drei Registerkarten angezeigt: Daten, Inhalt und Anlage.

   ![agentuitabs](assets/agentuitabs.png)

   Fahren Sie mit der Dateneingabe, der Verwaltung des Inhalts und der Verwaltung der Anlagen fort.

### Daten eingeben {#enter-data}

1. Geben Sie auf der Registerkarte „Daten“ die erforderlichen Daten für Variablen, Formulardatenmodell-Eigenschaften und Druckvorlagenfelder (XDP) ein. Füllen Sie alle erforderlichen Felder (mit einem Sternchen (*) gekennzeichnet) aus, um die Schaltfläche **Senden** zu aktivieren.

   Wählen Sie einen Datenfeldwert in der Vorschau der interaktiven Kommunikation aus, um das entsprechende Datenfeld auf der Registerkarte „Daten“ hervorzuheben.

### Inhalt verwalten {#manage-content}

Verwalten Sie auf der Registerkarte „Inhalt“ den Inhalt, z. B. Dokumentfragmente und Inhaltsvariablen in der interaktiven Kommunikation.

1. Wählen Sie **[!UICONTROL Inhalt]**. Die Registerkarte „Inhalt“ der interaktiven Kommunikation wird angezeigt.

   ![agentuicontenttab](assets/agentuicontenttab.png)

1. Bearbeiten Sie auf der Registerkarte „Inhalt“ ggf. die Dokumentfragmente. Um den Fokus auf das relevante Fragment in der Inhaltshierarchie zu legen, können Sie entweder die betreffende Zeile oder den betreffenden Absatz in der Vorschau der interaktiven Kommunikation oder direkt das Fragment in der Inhaltshierarchie auswählen.

   Beispielsweise wird das Dokumentfragment mit der Zeile „Jetzt online bezahlen ...“ in der Vorschau in der untenstehenden Grafik ausgewählt und das gleiche Dokumentfragment wurde auf der Registerkarte „Inhalt“ ausgewählt.

   ![contentmodulefocus](assets/contentmodulefocus.png)

   Auf der Registerkarte „Inhalt“ oder „Daten“ können Sie durch Tippen auf „Ausgewählte Module im Inhalt markieren“ (![highlightselectedmodulesincontentccr](assets/highlightselectedmodulesincontentccr.png)) links oben in der Vorschau eine Funktion aktivieren oder deaktivieren, die bewirkt, dass beim Klicken auf den relevanten Text oder Absatz bzw. das Datenfeld in der Vorschau das dazugehörige Inhalts-/Datenmodul aufgerufen wird.

   Die Fragmente, die vom Agenten beim Erstellen der interaktiven Kommunikation bearbeitet werden können, weisen das Symbol „Gewählten Inhalt bearbeiten“ (![iconeditselectedcontent](assets/iconeditselectedcontent.png)) auf. Wählen Sie das Symbol „Gewählten Inhalt bearbeiten“ aus, um das Fragment im Bearbeitungsmodus zu starten und Änderungen daran vorzunehmen. Verwenden Sie die folgenden Optionen zum Formatieren und Verwalten von Text:

   * [Formatierungsoptionen](#formattingtext)

      * [Formatierten Text aus anderen Anwendungen kopieren/einfügen](#pasteformattedtext)
      * [Teile des Textes markieren](#highlightemphasize)

   * [Sonderzeichen](#specialcharacters)
   * [Tastaturbefehle](/help/forms/using/keyboard-shortcuts.md)

   Weitere Informationen zu Aktionen, die für verschiedene Dokumentfragmente in der Benutzeroberfläche für Agenten verfügbar sind, finden Sie unter [Aktionen und Informationen, die in der Benutzeroberfläche für Agenten verfügbar sind](#actionsagentui).

1. Um der Druckausgabe der interaktiven Kommunikation einen Seitenumbruch hinzuzufügen, tippen Sie auf die Stelle, an der Sie den Seitenumbruch einfügen möchten, und wählen Sie „Seitenumbruch vor“ oder „Seitenumbruch nach“ ( ![pagebreakbeforeafter](assets/pagebreakbeforeafter.png)).

   Ein Platzhalter für einen expliziten Seitenumbruch wird in der interaktiven Kommunikation eingefügt. Sie können in der Druckvorschau anzeigen, wie sich ein expliziter Seitenumbruch auf die interaktive Kommunikation auswirkt.

   ![explicitpagebreak](assets/explicitpagebreak.png)

   Fahren Sie mit der Verwaltung der Anlagen der interaktiven Kommunikation fort.

### Verwalten von Anlagen {#manage-attachments}

1. Wählen Sie **[!UICONTROL Anlage]**. Die Benutzeroberfläche für Agenten zeigt die verfügbaren Anlagen so an, wie sie beim Erstellen der interaktiven Kommunikation eingerichtet wurden.

   Sie können festlegen, dass keine Anlagen mit der interaktiven Kommunikation versendet werden sollen, indem Sie das Symbol „Anzeigen“ und dann das Kreuz in der Anlage auswählen, um sie aus der interaktiven Kommunikation zu entfernen (sofern der Agent die Anlage löschen oder ausblenden darf). Für die Anhänge, die beim Erstellen der interaktiven Kommunikation als obligatorisch festgelegt wurden, sind die Symbole „Anzeigen“ und „Löschen“ deaktiviert.

   ![attachmentsagentui](assets/attachmentsagentui.png)

1. Wählen Sie das Symbol „Bibliothekszugriff“ (![libraryaccess](assets/libraryaccess.png)) aus, um auf die Inhaltsbibliothek zuzugreifen und DAM-Assets als Anlagen einzufügen.

   >[!NOTE]
   >
   >Das Symbol „Bibliothekszugriff“ ist nur verfügbar, wenn der Bibliothekszugriff beim Erstellen der interaktiven Kommunikation aktiviert wurde (in den Eigenschaften des Dokumentcontainers des Druckkanals).

1. Wenn die Reihenfolge der Anhänge beim Erstellen der interaktiven Kommunikation nicht gesperrt war, können Sie die Reihenfolge der Anhänge neu anordnen, indem Sie einen Anhang auswählen und auf die Pfeile nach unten oder nach oben tippen.
1. Verwenden Sie Webvorschau und Druckvorschau, um zu sehen, ob die beiden Ausgaben Ihren Anforderungen entsprechen.

   Wenn Sie mit den Vorschauen zufrieden sind, wählen Sie **[!UICONTROL Übermitteln]** aus, um die interaktive Kommunikation an einen Nachbearbeitungsprozess zu übermitteln/zu senden. Um Änderungen vorzunehmen, beenden Sie die Vorschau, um zu den Änderungen zurückzukehren.

## Formatieren von Text {#formattingtext}

Beim Bearbeiten eines Textfragments in der Agent-Benutzeroberfläche ändert sich die Symbolleiste abhängig vom Typ der von Ihnen vorgenommenen Änderungen zu „Schrift“, „Absatz“ oder „Liste“:

![typeofformattingtoolbar](assets/typeofformattingtoolbar.png) ![Schrift-Symbolleiste](do-not-localize/fonttoolbar.png)

Schriftart-Symbolleiste

![Absatz-Symbolleiste](do-not-localize/paragraphtoolbar.png)

Absatz-Symbolleiste

![Liste-Symbolleiste](do-not-localize/listtoolbar.png)

Listen-Symbolleiste

### Hervorheben von Teilen des Textes {#highlightemphasize}

Um Teile eines Textes in einem bearbeitbaren Fragment hervorzuheben, wählen Sie den Text und dann „Hervorhebungsfarbe“ aus.

![highlighttextagentui](assets/highlighttextagentui.png)

### Formatierten Text einfügen {#pasteformattedtext}

![pastedtext](assets/pastedtext.png)

### Einfügen von Sonderzeichen in Text {#specialcharacters}

Die Agent-Benutzeroberfläche bietet eine integrierte Unterstützung für 210 Sonderzeichen. Der Administrator kann [Unterstützung für mehr/benutzerdefinierte Sonderzeichen durch Anpassung hinzufügen](/help/forms/using/custom-special-characters.md).

#### Anlagenübermittlung {#attachmentdelivery}

* Wenn die interaktive Kommunikation mit serverseitigen APIs als interaktive oder nicht interaktive PDF gerendert wird, enthält die gerenderte PDF-Datei Anlagen im PDF-Format.
* Wenn ein mit einer interaktiven Kommunikation verknüpfter Nachbearbeitungsprozess als Teil der Option „Senden mit Benutzeroberfläche für Agenten“ geladen wird, werden Anlagen als List&lt;com.adobe.idp.Document> im AttachmentDocs-Parameter weitergeleitet.
* Vordefinierte Übermittlungsmechanismen, wie z. B. E-Mail und Drucken, übermitteln auch Anlagen zusammen mit einer PDF-Datei der interaktiven Kommunikation.

## In der Agent-Benutzeroberfläche verfügbare Aktionen und Informationen {#actionsagentui}

### Dokumentfragmente {#document-fragments}

![ ](do-not-localize/contentoptionsdocfragments.png)

* **Pfeil nach oben/unten**: Pfeile zum Verschieben von Dokumentenfragmenten nach unten oder oben in der interaktiven Kommunikation.
* **Löschen**: Wenn zulässig, löschen Sie das Dokumentfragment aus der interaktiven Kommunikation.
* **Seitenumbruch vor** (anwendbar für untergeordnete Fragmente des Zielbereichs): Fügt Seitenumbruch vor dem Dokumentfragment ein.
* **Einzug:** Einzug eines Dokumentenfragments vergrößern oder verkleinern.
* **Seitenumbruch nach** (anwendbar für untergeordnete Fragmente des Zielbereichs): Fügt Seitenumbruch nach dem Dokumentfragment ein.

![docfragoptions](assets/docfragoptions.png)

* Bearbeiten (nur Textfragmente): Öffnen Sie den Rich-Text-Editor zum Bearbeiten des Textdokumentfragments. Weitere Informationen finden Sie unter [Text formatieren](#formattingtext).

* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein bzw. schließt sie daraus aus.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

### Listendokumentfragmente {#list-document-fragments}

![listoptions](assets/listoptions.png)

* Leere Linie einfügen: Fügt eine neue leere Linie ein.
* Auswahl (Augensymbol): Schließt Dokumentfragmente in die interaktive Kommunikation ein/schließt sie daraus aus.
* Aufzählungszeichen/Nummerierungen überspringen: Überspringt Aufzählungszeichen/Nummerierungen im Listendokumentfragment.
* Nicht ausgefüllte Werte (Info): Gibt die Anzahl der nicht ausgefüllten Variablen im Dokumentfragment an.

## Speichern interaktiver Kommunikation als Entwurf {#save-as-draft}

Sie können die Benutzeroberfläche für Agenten verwenden, um einen oder mehrere Entwürfe für jede interaktive Kommunikation zu speichern und den Entwurf später abzurufen, um mit der Bearbeitung fortzufahren. Sie können für jeden Entwurf einen anderen Namen angeben, um ihn eindeutig zu identifizieren.

Adobe empfiehlt, diese Anweisungen nacheinander auszuführen, um eine interaktive Kommunikation erfolgreich als Entwurf zu speichern.

### Aktivieren der Funktion „Als Entwurf speichern“ {#before-save-as-draft}

Die Funktion „Als Entwurf speichern“ ist standardmäßig nicht aktiviert. Führen Sie zum Aktivieren der Funktion folgende Schritte durch:

1. Implementieren Sie das [ccrDocumentInstance](https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/ccr/ccrDocumentInstance/api/services/CCRDocumentInstanceService.html) Service Provider Interface (SPI).

   Mit dem SPI können Sie die Entwurfsversion der interaktiven Kommunikation mit einer Entwurfs-ID als eindeutiger Kennung in der Datenbank speichern. Bei diesen Anweisungen wird davon ausgegangen, dass Sie über Vorkenntnisse zum Erstellen eines OSGi-Bundles mithilfe eines Maven-Projekts verfügen.

   Eine Beispiel-SPI-Implementierung finden Sie unter [Beispielhafte ccrDocumentInstance-SPI-Implementierung](#sample-ccrDocumentInstance-spi).
1. Öffnen Sie `http://<hostname>:<port>/ system/console/bundles` und wählen Sie **[!UICONTROL Installieren/Aktualisieren]**, um das OSGi-Bundle hochzuladen. Stellen Sie sicher, dass der Status des hochgeladenen Pakets als **Aktiv** angezeigt wird. Starten Sie den Server neu, wenn der Status des Pakets nicht als **Aktiv** angezeigt wird.
1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf.
1. Wählen Sie die Option zum **[!UICONTROL Erstellen der Korrespondenzkonfiguration]** aus.
1. Wählen Sie die Option zum **[!UICONTROL Aktivieren der Speicherung mit CCRDocumentInstanceService]** und dann **[!UICONTROL Speichern]** aus.

### Speichern einer interaktiven Kommunikation als Entwurf {#save-as-draft-agent-ui}

Gehen Sie wie folgt vor, um eine interaktive Kommunikation als Entwurf zu speichern:

1. Wählen Sie im Formular-Manager eine interaktive Kommunikation und dann **[!UICONTROL Agent-UI öffnen]** aus.

1. Nehmen Sie in der Agent-Benutzeroberfläche die entsprechenden Änderungen vor und wählen Sie **[!UICONTROL Als Entwurf speichern]** aus.

1. Geben Sie den Namen des Entwurfs im Feld **[!UICONTROL Name]** an und wählen Sie **[!UICONTROL Fertig]** aus.

Nachdem Sie die interaktive Kommunikation als Entwurf gespeichert haben, wählen Sie **[!UICONTROL Änderungen speichern]** aus, um alle weiteren Änderungen am Entwurf zu speichern.

### Abrufen des Entwurfs einer interaktiven Kommunikation {#retrieve-draft}

Nachdem Sie eine interaktive Kommunikation als Entwurf gespeichert haben, können Sie sie abrufen, um sie weiter zu bearbeiten. Rufen Sie die interaktive Kommunikation ab unter Verwendung von:

`https://server:port/aem/forms/createcorrespondence.hmtl?draftid=[draftid]`

[draftid] bezieht sich auf die eindeutige Kennung für die Entwurfsversion, die nach dem Speichern einer interaktiven Kommunikation als Entwurf erzeugt wird.

### Beispielhafte ccrDocumentInstance-SPI-Implementierung {#sample-ccrDocumentInstance-spi}

Implementieren Sie das `ccrDocumentInstance`-SPI zum Speichern einer interaktiven Kommunikation als Entwurf. Im Folgenden finden Sie ein Beispiel für die Implementierung des `ccrDocumentInstance`-SPI.

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

Die Vorgänge `save`, `update`, `get` und `getAll` rufen den Datenbank-Service auf, um eine interaktive Kommunikation als Entwurf zu speichern, eine interaktive Kommunikation zu aktualisieren, Daten aus der Datenbank abzurufen und Daten für alle in der Datenbank verfügbaren Einträge von interaktiver Kommunikation abzurufen. Dieses Beispiel verwendet `mySQLDataBaseServiceCRUD` als Name des Datenbank-Services.

In der folgenden Tabelle wird das Beispiel einer `ccrDocumentInstance`-SPI-Implementierung erläutert. Sie zeigt, wie die Vorgänge `save`, `update`, `get` und `getAll` in der Beispielimplementierung den Datenbank-Service aufrufen.

<table> 
 <tbody>
 <tr>
  <td><p><strong>Vorgang</strong></p></td>
  <td><p><strong>Beispiele für Datenbank-Services</strong></p></td> 
   </tr>
  <tr>
   <td><p>Sie können einen Entwurf für eine interaktive Kommunikation entweder erstellen oder ihn direkt senden. Die API für den Speichervorgang prüft, ob die interaktive Kommunikation als Entwurf übermittelt wird, und sie enthält einen Entwurfsnamen. Die API ruft dann den Service mySQLDataBaseServiceCRUD mit „Speichern“ als Eingabemethode auf.</p></br><img src="assets/save-as-draft-save-operation.png"/></td>
   <td><p>Der Service mySQLDataBaseServiceCRUD überprüft „Speichern“ als Eingabemethode, erzeugt eine automatisch generierte Entwurfs-ID und gibt sie an AEM zurück. Die Logik zum Erzeugen einer Entwurfs-ID kann je nach Datenbank variieren.</p></br><img src="assets/save-operation-service.png"/></td>
   </tr>
  <tr>
   <td><p>Die API für den Aktualisierungsvorgang ruft den Status des Entwurfs der interaktiven Kommunikation ab und prüft, ob die interaktive Kommunikation einen Entwurfsnamen enthält. Die API ruft den Service mySQLDataBaseServiceCRUD auf, um diesen Status in der Datenbank zu aktualisieren.</p></br><img src="assets/save-as-draft-update-operation.png"/></td>
   <td><p>Der Service mySQLDataBaseServiceCRUD überprüft „Aktualisieren“ als Eingabemethode und speichert den Status des Entwurfs der interaktiven Kommunikation in der Datenbank.</br></p><img src="assets/update-operation-service.png"/></td>
   </tr>
   <tr>
   <td><p>Die API für den GET-Vorgang prüft, ob die interaktive Kommunikation eine Entwurfs-ID enthält. Die API ruft dann den Service mySQLDataBaseServiceCRUD mit GET als Eingabemethode auf, um die Daten für die interaktive Kommunikation abzurufen.</br></p><img src="assets/save-as-draft-get-operation.png"/></td>
   <td><p>Der Service mySQLDataBaseServiceCRUD überprüft GET als Eingabemethode und ruft die Daten für die interaktive Kommunikation basierend auf der Entwurfs-ID ab.</p></br><img src="assets/get-operation-service.png"/></td>
   </tr>
   <tr>
   <td><p>Die API für den Vorgang getAll ruft den Service mySQLGetALLData auf, um Daten für alle in der Datenbank gespeicherten interaktiven Kommunikationen abzurufen.</br></p><img src="assets/save-as-draft-getall-operation.png"/></td>
   <td><p>Der Service mySQLGetALLData ruft Daten für alle in der Datenbank gespeicherten interaktiven Kommunikationen ab.</p></br><img src="assets/getall-operation-service.png"/></td>
   </tr>
  </tbody>
</table>

Im Folgenden finden Sie ein Beispiel für die Datei `pom.xml`, die Teil der Implementierung ist:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0"
         xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
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
>Stellen Sie sicher, dass Sie in der Datei `pom.xml` die `aemfd-client-sdk`-Abhängigkeit auf 6.0.160 aktualisieren.
