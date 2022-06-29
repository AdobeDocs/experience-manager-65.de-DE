---
title: Globale Einstellungen importieren und exportieren
seo-title: Importing and exporting global settings
description: Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.
seo-description: You can import and export search template definitions and global settings for Workspace.
uuid: 8f1f210d-e850-4b2c-bb5a-942fa8299791
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 72fe5749-2fa2-442f-b679-7889faeafcac
exl-id: cdb7ff54-7891-45b1-a921-10b01ef5188d
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: ht
source-wordcount: '1245'
ht-degree: 100%

---

# Globale Einstellungen importieren und exportieren {#importing-and-exporting-global-settings}

Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

So können Sie beispielsweise von einer Entwicklungsumgebung zu einer Produktionsumgebung wechseln, indem Sie die Suchvorlagendefinitionen und globalen Einstellungen aus der einen Umgebung exportieren und in die andere Umgebung importieren.

Im Anschluss an den Export der Datei mit den globalen Einstellungen können Sie die Einstellungen in einem XML- oder Texteditor ändern. Sie sollten jedoch nur die JChannelConnectionProperties-, formViewOnly- und specialRoutes-Einstellungen ändern. Weitere Informationen finden Sie unter [Einstellungen für Workspace](importing-exporting-global-settings.md#workspace-global-settings).


>[!NOTE]
>
>Wenn Sie die Ereigniseigenschaften in der Datei mit den globalen Einstellungen ändern, müssen Sie den Server neu starten.

## Eine Suchvorlagendefinition importieren {#import-a-search-template-definition}

1. Klicken Sie in Administration Console auf „Dienste“ > „ Workspace “ > „Globale Verwaltung“.
1. Klicken Sie unter dem Feld „Suchvorlagendefinition importieren“ auf „Datei auswählen“, und wählen Sie die Suchvorlage aus. Sie können nur Suchvorlagendefinitionen importieren, die ursprünglich aus einer Instanz von Workspace exportiert wurden.
1. Wählen Sie Importieren.

## Eine Suchvorlagendefinition exportieren {#export-a-search-template-definition}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Suchvorlagendefinition exportieren“ auf „Alles auflisten“.
1. Wählen Sie in der Liste der Suchvorlagen die zu exportierende Vorlage aus.

   >[!NOTE]
   >
   >Sie können zwar mehrere Vorlage auswählen, es wird jedoch nur die zuletzt ausgewählte Vorlage exportiert.

1. Klicken Sie auf „Exportieren“ und speichern Sie die Datei auf Ihrem Computer.

## Globale Einstellungen importieren {#import-global-settings}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Globale Einstellungen importieren“ auf „Datei auswählen“, und wählen Sie die globale Einstellungsdatei aus. Die Datei mit den globalen Einstellungen muss im XML-Format vorliegen.
1. Wählen Sie Importieren.

## Globale Einstellungen exportieren {#export-global-settings}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Globale Einstellungen exportieren“ auf „Exportieren“.
1. Speichern Sie die Datei auf Ihrem Computer.

## Globale Einstellungen für Workspace {#workspace-global-settings}

Sie können die Datei mit den globalen Einstellungen ändern, sollten jedoch nur die Einstellungen „JChannelConnectionProperties“, „formViewOnly“ und „specialRoutes“ bearbeiten.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Die Datei mit den globalen Einstellungen für Workspace enthält folgende Einstellungen:

### Einstellungen unter „specialRoutes“ {#specialroutes-settings}

Die Einstellungen unter *specialRoutes* geben die Eigenschaften der Sonderrouten („Genehmigen“ und „Ablehnen“) in Workspace an. Unter bestimmten Umständen werden die Schaltflächen für diese Routen auf den Aufgabenkarten in Workspace angezeigt, so dass sie der Benutzer auswählen kann, ohne das Formular zu öffnen. Sie können die Einstellungen unter „specialRoutes“ in der Datei mit den globalen Einstellungen ändern, um benutzerdefinierte Namen für das Genehmigen oder Ablehnen hinzuzufügen oder zusätzliche Routen zu erstellen.

**client_specialRoutes_routes_approve_style:** Der Name des Stils, der sich im Workspace-Design befindet und die Symbole für die Genehmigungsschaltfläche angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Zum Definieren eines Stils für eine benutzerdefinierte Schaltfläche müssen Sie die folgende Vorlage verwenden:

` .buttonApprove {  icon: Embed('images/LC_DirectApprove_Sm_N.png');  disabledIcon: Embed('images/LC_DirectApprove_Sm_D.png');  paddingLeft: 5;  }` Die CCS-Datei von Workspace ist in die Datei „workspace-theme.swf“ eingebettet, die in der Datei „adobe-workspace-client.ear > adobe-workspace-client.war“ enthalten ist. Um das Erscheinungsbild von Workspace zu ändern, müssen Sie die Datei „workspace-theme.swf“ erneut kompilieren.

**client_specialRoutes_routes_deny_names:** Die verschiedenen Zeichenfolgen, die ein Workbench-Benutzer verwenden kann, um als „Ablehnen“ interpretiert zu werden. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise Ablehnen. Wenn der Workspace-Benutzer das Wort Ablehnen in einem Prozess verwendet, wird es nicht erkannt. Der Begriff Ablehnen muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_routes_deny_style:** Der Name des Stils, der sich in der Workspace-Design-Datei befindet und die Symbole für die Schaltfläche „Ablehnen“ angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Zum Definieren eines Stils für eine benutzerdefinierte Schaltfläche müssen Sie die folgende Vorlage verwenden:

`  .buttonDeny {   icon: Embed('images/LC_DirectDeny_Sm_N.png');   disabledIcon: Embed('images/LC_DirectDeny_Sm_D.png');   paddingLeft: 0;   }` **client_specialRoutes_routes_approve_names:** Die verschiedenen Zeichenfolgen, die ein Workbench-Benutzer verwenden kann und die als „Genehmigen“ interpretiert werden. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise „genehmigen“. Wenn der Workspace-Benutzer das Wort „Genehmigen“ in einem Prozess verwendet, wird es nicht erkannt. Der Begriff „Genehmigen“ muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_names:** Die Schlüssel zum Lokalisieren des benutzerdefinierten Zeichenfolgenwerts aus den Ressourcendateien. Jeder Eintrag in diesen Einstellungen muss die Werte für die Namen und den Stil umfassen.

### JGroup-Einstellungen {#jgroup-settings}

Diese Einstellungen werden nur angezeigt, wenn Sie Adobe LiveCycle ES2.5 oder früher aktualisiert haben.

**server_remoteevents_ClientTimeoutMilliseconds:** Die maximale Zeitspanne, die die JGroup auf Ereignismeldungen wartet. Diese Einstellung sollte nicht geändert werden.

**server_remoteevents_ServerTimeoutMilliseconds:** Die maximale Wartezeit für den Empfang von JGroup-Meldungen auf dem Server. Diese Option legt die Verzögerung zum Senden von Meldungen vom Server an den Client fest.

**server_remoteevents_JChannelConnectionProperties:** Die Verbindungseigenschaften für die JGroup, die für die Kommunikation zwischen dem Server (auf dem ein Service-Ereignis vom RemoteEvent-Service verarbeitet wird) und allen Instanzen von Workspace verwendet werden.

Eventuell müssen Sie die UDP-Werte für die Multicast-IP-Adresse (mcast_addr), den Multicast-IP-Anschluss (mcast_port) und die TTL für die Multicast-Pakete (ip_ttl) ändern. Standardmäßig werden die Werte für Multicast-IP-Adresse und -Anschluss nach dem Zufallsprinzip generiert und müssen im allgemeinen nicht geändert werden. Falls in Ihrer Firma jedoch Netzwerkrichtlinien hinsichtlich bestimmter Multicast-Bereiche für Multicast-IP-Adressen bestehen, müssen Sie die Werte eventuell ändern.

>[!NOTE]
>
>Die TTL muss größer als die Anzahl der Netzwerkswitches zwischen den Servern im Cluster sein. Wird der Wert jedoch zu hoch eingestellt, kann dies dazu führen, dass Multicast-Pakete in Subnetze gelangen, wo sie gelöscht werden.

Die restlichen Eigenschaften dieser Einstellung sollten nicht geändert werden.

**server_remoteevents_JGroupName:** Der Name der JGroup, die für die Remote-Ereigniskommunikation verwendet wird. Dieser Wert wird nach dem Zufallsprinzip generiert, um Konflikte in Clustern zu vermeiden. Dieser Wert sollte nicht geändert werden.

<!--

For additional information on JGroups and Workspace, see [JGroups and AEM forms Workspace - Explained](https://blogs.adobe.com/livecycle/2011/03/jgroups-and-livecycle-workspace-explained.html).

-->

### formView-Einstellungen {#formview-settings}

**client_formView_openFormInFullScreen:** Wählen Sie zum Anzeigen aller Formulare in Workspace im Vollbildmodus für diese Option die Einstellung „true“. Standardmäßig ist diese Option auf „false“ festgelegt und die Formulare werden nicht im Vollbildmodus angezeigt. Beachten Sie, dass der User-Dienst eine Option zum Öffnen des Dokuments, das einer Aufgabe im Vollbildmodus zugeordnet ist, enthält. Damit können Sie die Anzeige auf der Basis pro Prozess steuern.

**client_routes_formViewOnly:** Bei der Einstellung „True“ werden Routen nicht in der Karten- oder Listenansicht von Workspace angezeigt. Der Standardwert „False“ bedeutet, dass Routen in der Karten- und Listenansicht angezeigt werden.

### Andere Einstellungen {#other-settings}

**client_mimeTypes_openOutsideBrowser:** Der MIME-Typ der Dokumente, die außerhalb der Workspace -Browser-Instanz geöffnet werden. Wenn die Prozesse in Ihrem Unternehmen einen zusätzlichen MIME-Typ erfordern, geben Sie ihn hier an. Die Standardwerte lauten:

* `application/msword`
* `application/msexcel`
* `application/ms-powerpoint`

**client_customUI_caching:** Dient zum Zwischenspeichern einer benutzerdefinierten Aufgabenbenutzeroberfläche.

**server_debugLevel:** Ändern Sie diese Einstellung nicht.

**client_pollingInterval:** Legt das Abfrageintervall (in Sekunden) fest, das für Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) verwendet wird, um die neuen und geänderten Aufgaben zu erkennen. Der Standardwert ist 3 Sekunden. Dies ist für AEM Forms Workspace nicht möglich.

**client_systemContext_name:** Geben Sie einen benutzerdefinierten Namen (z. B. Bürger) an, der im Feld „Hinzugefügt von“ (auf der Registerkarte „Anlagen“) für die Anlagen einer Aufgabe in AEM Forms Workspace angezeigt werden soll.

Definieren des benutzerdefinierten Namens:

`<client_systemContext_name>[custom name to display]</client_systemContext_name>`

>[!NOTE]
>
>In der Demoanwendung lautet der standardmäßige Anzeigename **Bürger**. In einer von Ihnen erstellten benutzerdefinierte Anwendung lautet der standardmäßige Anzeigename **Systemkontextkonto**.
>
>**client_idleTimeout:** Wenn ein Benutzer über einen bestimmte Zeitraum hinweg inaktiv bleibt, läuft die AEM Forms Workspace-Sitzung ab. Um die Funktion zu aktivieren, fügen Sie „Globale Einstellungen &lt;client_idleTimeout>*IDLE_TIMEOUT_IN_SECONDS*&lt;/client_idleTimeout>“ einen Eintrag hinzu. Sie können den Wert 0 angeben, um die Zeitüberschreitung im Leerlauf zu deaktivieren. Der Zeitraum wird in Sekunden angegeben.
