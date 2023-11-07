---
title: Fügen Sie benutzerdefinierte Aktionen/Schaltflächen der Benutzeroberfläche „Korrespondenz erstellen“ hinzu
description: Erfahren Sie, wie Sie benutzerdefinierte Aktionen/Schaltflächen in der Benutzeroberfläche "Korrespondenz erstellen"hinzufügen
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: a582ba41-83cb-46f2-9de9-3752f6a7820a
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 79%

---

# Hinzufügen einer benutzerdefinierten Aktionsschaltfläche in der Benutzeroberfläche „Korrespondenz erstellen“ {#add-custom-action-button-in-create-correspondence-ui}

## Übersicht {#overview}

Mit der Correspondence Management-Lösung können Sie benutzerdefinierte Aktionen zur Benutzeroberfläche &quot;Korrespondenz erstellen&quot;hinzufügen.

In dem Szenario in diesem Dokument wird erklärt, wie Sie eine Schaltfläche in der Benutzeroberfläche „Korrespondenz erstellen“ einfügen können, um einen Brief als Überprüfungs-PDF im Anhang einer E-Mail zu teilen.

### Voraussetzungen {#prerequisites}

Um dieses Szenario abzuschließen, benötigen Sie Folgendes:

* Kenntnisse über CRX und JavaScript
* LiveCycle Server

## Szenario: Erstellen Sie die Schaltfläche in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;, um einen Brief zur Überprüfung zu senden {#scenario-create-the-button-in-the-create-correspondence-user-interface-to-send-a-letter-for-review}

Das Hinzufügen einer Schaltfläche mit einer Aktion (hier Brief zur Überprüfung senden) zur Benutzeroberfläche &quot;Korrespondenz erstellen&quot;umfasst Folgendes:

1. Hinzufügen der Schaltfläche zur Benutzeroberfläche &quot;Korrespondenz erstellen&quot;
1. Hinzufügen der Aktionsbearbeitung zur Schaltfläche
1. Hinzufügen eines LiveCycle-Prozesses, um die Aktionsbearbeitung zu aktivieren

### Hinzufügen der Schaltfläche „Korrespondenz erstellen“ zur Benutzeroberfläche  {#add-the-button-to-the-create-correspondence-user-interface}

1. Wechseln Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als Administrator an.
1. Erstellen Sie im Ordner &quot;apps&quot;einen Ordner mit dem Namen `defaultApp` mit einem ähnlichen Pfad/einer ähnlichen Struktur zum Ordner defaultApp (im Konfigurationsordner). Mit den folgenden Schritten können Sie den Ordner erstellen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **defaultApp** unter dem folgenden Pfad und wählen Sie **Überlagerungsknoten**:

      /libs/fd/cm/config/defaultApp/

      ![Überlagerungsknoten](assets/1_defaultapp.png)

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad**: /libs/fd/cm/config/defaultApp/

      **Überlagerungsspeicherort**: /apps/

      **Knotentypen abgleichen**: Kontrollkästchen aktiviert

      ![Überlagerungsknoten](assets/2_defaultappoverlaynode.png)

   1. Klicken Sie auf **OK**.
   1. Klicken Sie auf **Alle speichern**.

1. Erstellen Sie eine Kopie der acmExtensionsConfig.xml-Datei (vorhanden unter der /libs-Verzweigung) unter der /apps-Verzweigung.

   1. Wechseln Sie zu „/libs/fd/cm/config/defaultApp/acmExtensionsConfig.xml“

   1. Klicken Sie mit der rechten Maustaste auf die Datei &quot;acmExtensionsConfig.xml&quot;und wählen Sie **Kopieren**.

      ![Kopieren Sie acmExtensionsConfig.xml](assets/3_acmextensionsconfig_xml_copy.png)

   1. Rechtsklicken Sie auf die **defaultApp** Ordner unter &quot;/apps/fd/cm/config/defaultApp/&quot; und wählen Sie **Einfügen**.
   1. Klicken Sie auf **Alle speichern**.

1. Doppelklicken Sie auf die Kopie von acmExtentionsConfig.xml, die Sie neu im Apps-Ordner erstellt haben. Die Datei wird zur Bearbeitung geöffnet.
1. Suchen Sie folgenden Code:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <extensionsConfig>
       <modelExtensions>
           <modelExtension type="LetterInstance">
     <customAction name="Preview" label="loc.letterInstance.preview.label" tooltip="loc.letterInstance.preview.tooltip" styleName="previewButton"/>
               <customAction name="Submit" label="loc.letterInstance.submit.label" tooltip="loc.letterInstance.submit.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="SaveAsDraft" label="loc.letterInstance.saveAsDraft.label" tooltip="loc.letterInstance.saveAsDraft.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="Close" label="loc.letterInstance.close.label" tooltip="loc.letterInstance.close.tooltip" styleName="closeButton"/>
           </modelExtension>
       </modelExtensions>
   </extensionsConfig>
   ```

1. Um ein Schreiben per E-Mail zu versenden, können Sie den LiveCycle Forms-Arbeitsablauf verwenden. Fügen Sie in „acmExtensionsConfig.xml“ ein Tag „customAction“ unter dem Tag „modelExtension“ wie folgt hinzu:

   ```xml
    <customAction name="Letter Review" label="Letter Review" tooltip="Letter Review" styleName="" permissionName="forms-users" actionHandler="CM.domain.CCRCustomActionHandler">
         <serviceName>Forms Workflow -> SendLetterForReview/SendLetterForReviewProcess</serviceName>
       </customAction>
   ```

   ![customAction-Tag](assets/5_acmextensionsconfig_xml.png)

   Das modelExtension-Tag verfügt über einen Satz von untergeordneten customAction-Tags, die die Aktion, die Berechtigungen und das Erscheinungsbild der Aktionsschaltfläche konfigurieren. Im Folgenden finden Sie eine Liste der customAction-Konfigurations-Tags:

   | **Name** | **Beschreibung** |
   |---|---|
   | name | Der alphanumerische Name für die auszuführende Aktion. Der Wert dieses Tags wird benötigt, muss eindeutig sein (d. h. innerhalb des modelExtension-Tags) und muss mit einem Buchstaben beginnen. |
   | label | Die auf der Aktionsschaltfläche anzuzeigende Bezeichnung |
   | QuickInfo | QuickInfo-Text der Schaltfläche, der angezeigt wird, wenn der Benutzer den Mauszeiger über die Schaltfläche bewegt. |
   | styleName | Name des benutzerdefinierten Stils, der auf die Aktionsschaltfläche angewendet wird. |
   | permissionName | Die entsprechende Aktion wird nur angezeigt, wenn der Benutzer über die von permissionName festgelegte Berechtigung verfügt. Wenn Sie permissionName als `forms-users` angeben, erhalten alle Benutzer Zugriff auf diese Option. |
   | actionHandler | Vollqualifizierter Name der Klasse „ActionHandler“, die aufgerufen wird, wenn der Benutzer auf die Schaltfläche klickt. |

   Neben den oben genannten Parametern kann es weitere Konfigurationen geben, die mit einer customAction verknüpft sind. Diese zusätzlichen Konfigurationen werden für den Handler über das CustomAction-Objekt verfügbar gemacht.

   | **Name** | **Beschreibung** |
   |---|---|
   | serviceName | Wenn eine customAction ein untergeordnetes Tag mit dem Namen „serviceName“ enthält, wird beim Klicken auf die entsprechende Schaltfläche/Verknüpfung ein Prozess mit dem Namen aufgerufen, der im Tag „serviceName“ repräsentiert wird. Stellen Sie sicher, dass dieser Vorgang dieselbe Signatur wie der Brief PostProcess hat. Fügen Sie das Präfix „Forms-Arbeitsablauf“ zum Servicenamen hinzu. |
   | Parameters, die das Präfix „cm_“ im Tag-Namen enthalten | Wenn eine customAction untergeordnete Tags mit dem Namen „cm_“ am Anfang enthält, dann sind diese Parameter in der Nachbearbeitung (Briefnachbearbeitung oder besonderer Prozess, der vom Tag „serviceName“ repräsentiert wird) im Eingabe-XML-Code unter dem relevanten Tag, bei dem das Präfix „cm_“ entfernt wurde, verfügbar. |
   | actionName | Wann immer eine Nachbearbeitung aufgrund eines Klicks erfolgt, enthält die gesendete XML ein spezielles Tag mit einem Namen der Benutzeraktion unter dem Tag. |

1. Klicken Sie auf **Alle speichern**.

#### Erstellen eines Gebietsschemaordners mit einer Eigenschaftendatei in der /apps-Verzweigung {#create-a-locale-folder-with-properties-file-in-the-apps-branch}

Die Datei „ACMExtensionsMessages.properties“ beinhaltet Beschriftungen und Quickinfo-Meldungen von verschiedenen Feldern in der Benutzeroberfläche zur Korrespondenzerstellung. Damit die benutzerdefinierten Aktionen/Schaltflächen funktionieren, müssen Sie eine Kopie dieser Datei in der /apps-Verzweigung erstellen.

1. Klicken Sie mit der rechten Maustaste auf den Ordner **locale** unter dem folgenden Pfad und wählen Sie **Überlagerungsknoten**:

   /libs/fd/cm/config/defaultApp/locale

1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

   **Pfad**: /libs/fd/cm/config/defaultApp/locale

   **Überlagerungsspeicherort**: /apps/

   **Knotentypen abgleichen**: Kontrollkästchen aktiviert

1. Klicken Sie auf **OK**.
1. Klicken Sie auf **Alle speichern**.
1. Klicken Sie mit der rechten Maustaste auf die folgende Datei und wählen Sie **Kopieren**:

   `/libs/fd/cm/config/defaultApp/locale/ACMExtensionsMessages.properties`

1. Klicken Sie mit der rechten Maustaste auf den Ordner **locale** unter folgendem Pfad und wählen Sie die Option **Einfügen**:

   `/apps/fd/cm/config/defaultApp/locale/`

   ACMExtensionsMessages.properties-Datei wird in den Ordner „locale“ kopiert.

1. Um die Beschriftungen der neu hinzugefügten benutzerdefinierten Aktion/Schaltfläche zu lokalisieren, erstellen Sie die Datei „ACMExtensionsMessages.properties“ für das entsprechende Gebietsschema in `/apps/fd/cm/config/defaultApp/locale/`.

   Beispiel für die Lokalisierung der benutzerdefinierten Aktion/Schaltfläche, die in diesem Artikel erstellt wurde, erstellen Sie eine Datei mit dem Namen ACMExtensionsMessages_fr.properties mit folgendem Eintrag:

   `loc.letterInstance.letterreview.label=Revue De Lettre`

   Sie können in dieser Datei auch mehr Eigenschaften wie für Quickinfo und Stil hinzufügen.  

1. Klicken Sie auf **Alle speichern**.

#### Starten Sie das Adobe Asset Composer-Baustein-Bundle neu {#restart-the-adobe-asset-composer-building-block-bundle}

Nachdem Sie alle serverseitigen Änderungen vorgenommen haben, starten Sie das Adobe Asset Composer-Baustein-Bundle neu. In diesem Szenario werden die Dateien „acmExtensionsConfig.xml“ und „ACMExtensionsMessages.properties“ auf der Server-Seite bearbeitet, und folglich erfordert das Asset Composer-Baustein-Bundle von Adobe einen Neustart.

>[!NOTE]
>
>Möglicherweise müssen Sie die Daten im Browsercache löschen.

1. Rufen Sie `https://[host]:'port'/system/console/bundles` auf. Falls erforderlich, melden Sie sich als Administrator an.

1. Suchen Sie das Asset Composer-Baustein-Bundle von Adobe. Starten Sie das Bundle neu: Klicken Sie auf „Anhalten“ und klicken Sie dann auf „Start“.

   ![Asset Composer-Baustein von Adobe ](assets/6_assetcomposerbuildingblockbundle.png)

Nach dem Neustart des Adobe Asset Composer-Baustein-Bundles wird die benutzerdefinierte Schaltfläche in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;angezeigt. Sie können einen Brief in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;öffnen, um eine Vorschau der benutzerdefinierten Schaltfläche anzuzeigen.

### Hinzufügen der Aktionsbearbeitung zur Schaltfläche {#add-action-handling-to-the-button}

Die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;verfügt standardmäßig über die Implementierung von ActionHandler in der Datei cm.domain.js am folgenden Speicherort:

/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccr/js/cm.domain.js

Erstellen Sie für die benutzerdefinierte Aktionsbearbeitung eine Überlagerung der cm.domain.js-Datei in der /apps-Verzweigung von CRX.

Das Bearbeiten der Aktion/der Schaltfläche beim Klicken auf die Aktion/Schaltfläche beinhaltet Logik für:

* Ein-/Ausblenden der neu hinzugefügten Aktion: durch Überschreiben der Funktion „actionVisible()“.
* Aktivieren/Deaktivieren der neu hinzugefügten Aktion: erfolgt durch Überschreiben der Funktion actionEnabled().
* Tatsächliche Verarbeitung der Aktion, wenn der Benutzer auf die Schaltfläche klickt: durch Überschreiben der Implementierung der Funktion handleAction().

1. Rufen Sie `https://'[server]:[port]'/[ContextPath]/crx/de` auf. Falls erforderlich, melden Sie sich als Administrator an.

1. Erstellen Sie im Anwendungsordner einen Ordner mit dem Namen`js` in der /apps-Verzweigung von CRX, mit einer ähnlichen Struktur des folgenden Ordners:

   `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   Mit den folgenden Schritten können Sie den Ordner erstellen:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **js** unter dem folgenden Pfad und wählen Sie **Überlagerungsknoten**:

      `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad**: /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js

      **Überlagerungsspeicherort**: /apps/

      **Knotentypen abgleichen**: Kontrollkästchen aktiviert

   1. Klicken Sie auf **OK**.
   1. Klicken Sie auf **Alle speichern**.

1. Erstellen Sie im Ordner „js“ eine Datei namens „ccrcustomization.js“ mit dem Code für Aktionsbearbeitung der Schaltfläche mithilfe der folgendem Schritte:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **js** unter dem folgenden Pfad und wählen Sie **Erstellen > Datei erstellen**:

      `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

      Benennen Sie die Datei als ccrcustomization.js.

   1. Doppelklicken Sie auf die Datei ccrcustomization.js , um sie in CRX zu öffnen.
   1. Fügen Sie in die Datei den folgenden Code ein und klicken Sie auf **Alle speichern**:

      ```javascript
      /* for adding and handling custom actions in Extensible Toolbar.
        * One instance of handler will be created for each action.
        * CM.domain.CCRCustomActionHandler is actionHandler class.
        */
      var CCRCustomActionHandler;
          CCRCustomActionHandler = CM.domain.CCRCustomActionHandler = new Class({
              className: 'CCRCustomActionHandler',
              extend: CCRDefaultActionHandler,
              construct : function(action,model){
              }
          });
          /**
           * Called when user user click an action
           * @param extraParams additional arguments that may be passed to handler (For future use)
           */
          CCRCustomActionHandler.prototype.handleAction = function(extraParams){
              if (this.action.name == CCRCustomActionHandler.SEND_FOR_REVIEW) {
                  var sendForReview = function(){
                      var serviceName = this.action.actionConfig["serviceName"];
                      var inputParams = {};
                      inputParams["dataXML"] = this.model.iccData.data;
                      inputParams["letterId"] = this.letterVO.id;
                      inputParams["letterName"] = this.letterVO.name;
                      inputParams["mailId"] = $('#email').val();
                      /*function to invoke the LivecyleService */
                      ServiceDelegate.callJSONService(this,"lc.icc.renderlib.serviceInvoker.json","invokeProcess",[serviceName,inputParams],this.onProcessInvokeComplete,this.onProcessInvokeFail);
                      $('#ccraction').modal("hide");
                  }
                  if($('#ccraction').length == 0){
                      /*For first click adding popup & setting letterName.*/
                      $("body").append(popUp);
                      $("input[id*='letterName']").val(this.letterVO.name);
                      $(document).on('click',"#submitLetter",$.proxy( sendForReview, this ));
                  }
                  $('#ccraction').modal("show");
              }
          };
          /**
           * Should the action be enabled in toolbar
           * @param extraParams additional arguements that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
         CCRCustomActionHandler.prototype.actionEnabled = function(extraParams){
                  /*can be customized as per user requirement*/
                  return true;
          };
          /**
           * Should the action be visible in toolbar
           * @param extraParams additional arguments that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
          CCRCustomActionHandler.prototype.actionVisible = function(extraParams){
              /*Check can be enabled for Non-Preview Mode.*/
              return true;
          };
          /*SuccessHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeComplete = function(response) {
              ErrorHandler.showSuccess("Letter Sent for Review");
          };
          /*FaultHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeFail = function(event) {
              ErrorHandler.showError(event.message);
          };
          CCRCustomActionHandler.SEND_FOR_REVIEW  = "Letter Review";
      /*For PopUp*/
          var popUp = '<div class="modal fade" id="ccraction" tabindex="-1" role="dialog" aria-hidden="true">'+
          '<div class="modal-dialog modal-sm">'+
              '<div class="modal-content">' +
                  '<div class="modal-header">'+
                      '<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</code></button>'+
                      '<h4 class="modal-title"> Send Review </h4>'+
                  '</div>'+
                  '<div class="modal-body">'+
                      '<form>'+
                          '<div class="form-group">'+
                              '<label class="control-label">Email Id</label>'+
                              '<input type="text" class="form-control" id="email">'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<label  class="control-label">Letter Name</label>'+
                              '<input id="letterName" type="text" class="form-control" readonly>'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<input id="letterData" type="text" class="form-control hide" readonly>'+
                          '</div>'+
                      '</form>'+
                  '</div>'+
                  '<div class="modal-footer">'+
                     '<button type="button" class="btn btn-default" data-dismiss="modal"> Cancel </button>'+
                     '<button type="button" class="btn btn-primary" id="submitLetter"> Submit </button>'+
                  '</div>'+
              '</div>'+
          '</div>'+
      '</div>';
      ```

### LiveCycle-Prozess hinzufügen, um die Aktion zu aktivieren <span class="acrolinxCursorMarker"></code>Handhabung {#add-the-livecycle-process-to-enable-action-span-class-acrolinxcursormarker-span-handling}

Aktivieren Sie in diesem Szenario die folgenden Komponenten, die ein Teil der angehängten Datei „components.zip“ sind:

* DSC-Komponenten-JAR (DSCSample.jar)
* Brief zum Review-Prozess senden LCA (SendLetterForReview.lca)

Laden Sie die Datei „components.zip“ herunter und extrahieren Sie daraus die Dateien „DSCSample.jar“ und „SendLetterForReview.lca“. Verwenden Sie diese Dateien, wie in den folgenden Verfahren angegeben.
[Datei laden](assets/components.zip)

#### Konfigurieren Sie den LiveCycle-Server, um den LCA-Vorgang auszuführen {#configure-the-livecycle-server-to-run-the-lca-process}

>[!NOTE]
>
>Dieser Schritt ist nur erforderlich, wenn Sie eine OSGI-Installation verwenden und die LC-Integration für die Art der Anpassung, die Sie implementieren, erforderlich ist.

Der LCA-Vorgang wird auf dem LiveCycle-Server ausgeführt und erfordert die Serveradresse und die Anmeldeinformationen.

1. Wechseln Sie zu `https://'[server]:[port]'/system/console/configMgr` und melden Sie sich als Administrator an.
1. Suchen Sie nach Adobe LiveCycle Client SDK-Konfiguration und klicken Sie auf **Bearbeiten** (Bearbeiten-Symbol). Das Konfigurationsfenster öffnet sich.

1. Geben Sie die folgenden Details ein und klicken Sie auf **Speichern**:

   * **Server-URL**: URL des LC-Servers, dessen Service „An Review senden“ den Aktionsbearbeitungs-Code verwendet.
   * **Benutzername**: Admin-Benutzername des LC-Servers
   * **Kennwort:** Kennwort des Adminbenutzernamens 

   ![Adobe LiveCycle Client SDK-Konfiguration](assets/3_clientsdkconfiguration.png)

#### Installieren des LiveCycle Archivs (LCA) {#install-livecycle-archive-lca}

Der erforderliche LiveCycle-Prozess, der den E-Mail-Service-Vorgang aktiviert.

>[!NOTE]
>
>Wenn Sie sehen möchten, wie dieser Vorgang funktioniert oder wenn Sie ähnliche Vorgänge selbst erstellen möchten, benötigen Sie Workbench.

1. Melden Sie sich als Administrator bei der Admin-Benutzeroberfläche des LiveCycle®-Servers unter `https:/[lc server]/:[lc port]/adminui` an.

1. Navigieren Sie zu **Startseite > Dienste > Anwendungen und Dienste > Anwendungsverwaltung**.

1. Wenn das Programm SendLetterForReview bereits vorhanden ist, überspringen Sie die verbleibenden Schritte in diesem Verfahren, fahren Sie ansonsten mit den nächsten Schritten fort.

   ![SendLetterForReview-Anwendung in der Benutzeroberfläche](assets/12_applicationmanagementlc.png)

1. Wählen Sie **Importieren**.

1. Klicken Sie auf **Datei wählen** und wählen Sie „SendLetterForReview.lca“.

   ![Wählen Sie die SendLetterForReview.lca-Datei](assets/14_sendletterforreview_lca.png)

1. Klicken Sie auf **Vorschau**. 

1. Wählen Sie **Assets nach Abschluss des Imports für die Laufzeit bereitstellen**.

1. Wählen Sie **Importieren**.

#### Hinzufügen von ServiceName zur Zulassungsliste der Services {#adding-servicename-to-the-allowlist-service-list}

Geben Sie auf dem Experience Manager-Server an, auf welche LiveCycle-Services der Experience Manager-Server zugreifen soll.

1. Melden Sie sich als Administrator bei `https:/[host]:'port'/system/console/configMgr` an.

1. Klicken Sie auf die **Adobe LiveCycle Client SDK-Konfiguration**. Das Bedienfeld Adobe LiveCycle Client SDK-Konfiguration wird angezeigt.
1. Klicken Sie in der Liste „Service-Name“ auf das Symbol „+“ und fügen Sie einen serviceName **SendLetterForReview/SendLetterForReviewProcess** hinzu.

1. Klicken Sie auf **Speichern**.

#### E-Mail-Dienst konfigurieren {#configure-the-email-service}

In diesem Szenario müssen Sie den E-Mail-Dienst im LiveCycle-Server konfigurieren, damit Correspondence Management eine E-Mail senden kann.

1. Melden Sie sich als Administrator bei der Admin-Benutzeroberfläche des LiveCycle-Servers unter `https:/[lc server]:[lc port]/adminui` an.

1. Navigieren Sie zu **Startseite > Dienste > Anwendungen und Dienste > Dienstverwaltung**.

1. Suchen Sie nach der Option **EmailService** und klicken Sie darauf.

1. Konfigurieren Sie im **SMTP-Host** den E-Mail-Service.

1. Klicken Sie auf **Speichern**.

#### DSC-Dienst konfigurieren {#configure-the-dsc-service}

Um die Correspondence Management-API zu verwenden, laden Sie die Datei „DSCSample.jar“ (diesem Dokument als Teil von „components.zip“ beigefügt) herunter und laden Sie sie auf den LiveCycle-Server hoch. Nachdem die Datei „DSCSample.jar“ auf den LiveCycle-Server hochgeladen wurde, verwendet der AEM-Server die Datei „DSCSample.jar“, um auf die renderLetter-API zuzugreifen.

Weitere Informationen finden Sie unter [Verbinden von AEM Forms mit Adobe LiveCycle](/help/forms/using/aem-livecycle-connector.md).

1. Aktualisieren Sie die URL des Experience Manager-Servers in „cmsa.properties“ in der Datei „DSCSample.jar“, die sich am folgenden Speicherort befindet:

   DSCSample.jar\com\adobe\livecycle\cmsa.properties

1. Stellen Sie die folgenden Parameter in der Konfigurationsdatei bereit:

   * **crx.serverUrl**=https:/host:port/[Kontextpfad]/[AEM URL]
   * **crx.username**= Benutzername in Experience Manager
   * **crx.password**= Kennwort in Experience Manager
   * **crx.appRoot** = /content/apps/cm

   >[!NOTE]
   >
   >Jedes Mal, wenn Sie Änderungen auf Server-Seite vornehmen, müssen Sie den LiveCycle-Server neu starten.

   Die Datei „DSCSample.jar“ verwendet die renderLetter-API. Weitere Informationen zur renderLetter-API finden Sie unter [Benutzeroberfläche „LetterRenderService“](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html).

#### Importieren von DSC in LiveCycle {#import-dsc-to-livecyle}

Die Datei „DSCSample.jar“ verwendet die renderLetter-API, um ein Schreiben als PDF-Bytes aus XML-Daten zu generieren, die von DSC als Eingabe gegeben werden. Weitere Informationen zum renderLetter und anderen APIs finden Sie unter [Brief-Render-Dienst](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html).

1. Starten Sie Workbench und melden Sie sich an.
1. Wählen Sie **Fenster > Ansicht anzeigen > Komponenten**. Die Komponentenansicht wird in Workbench ES2 hinzugefügt.

1. Klicken Sie mit der rechten Maustaste auf **Komponenten** und wählen Sie **Komponente installieren**.

1. Wählen Sie die Datei **DSCSample.jar** über den Datei-Browser aus und klicken Sie auf **Öffnen**.
1. Klicken Sie mit der rechten Maustaste auf **RenderWrapper** und wählen Sie **Komponente starten**. Wenn die Komponente gestartet wird, erscheint ein grüner Pfeil neben dem Komponentennamen.

## Brief zur Überprüfung senden {#send-letter-for-review}

Nachdem Sie die Aktion und Schaltfläche zum Senden des Briefs zur Überprüfung konfiguriert haben:

1. Löschen Sie den Browsercache.

1. Klicken Sie in der Benutzeroberfläche „Korrespondenz erstellen“ auf **Brief-Review** und geben Sie die E-Mail-ID des Überprüfers an.

1. Klicken Sie auf **Senden**.

![sendreview](assets/sendreview.png)

Der Reviewer erhält eine E-Mail von einem System mit dem Schreiben als PDF-Anlage.
