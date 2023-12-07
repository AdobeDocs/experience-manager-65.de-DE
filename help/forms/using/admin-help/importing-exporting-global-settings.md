---
title: Importieren und Exportieren von globalen Einstellungen
description: Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: cdb7ff54-7891-45b1-a921-10b01ef5188d
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 38%

---

# Importieren und Exportieren von globalen Einstellungen {#importing-and-exporting-global-settings}

Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Sie können beispielsweise von einer Entwicklungsumgebung zu einer Produktionsumgebung wechseln, indem Sie die Suchvorlagendefinitionen und globalen Einstellungen aus einer Umgebung exportieren und in die andere importieren.

Nach dem Export der Datei mit den globalen Einstellungen können Sie die Einstellungen in einem XML- oder Texteditor ändern. Die einzigen Einstellungen, die Sie bearbeiten können, sind jedoch die Einstellungen JChannelConnectionProperties, formViewOnly und specialRoutes . Weitere Informationen finden Sie unter [Globale Workspace-Einstellungen](importing-exporting-global-settings.md#workspace-global-settings).


>[!NOTE]
>
>Wenn Sie die Ereigniseigenschaften in der Datei mit den globalen Einstellungen ändern, müssen Sie den Server neu starten.

## Eine Suchvorlagendefinition importieren {#import-a-search-template-definition}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Workspace&quot;> &quot;Globale Administration&quot;.
1. Klicken Sie unter dem Feld Suchvorlagendefinition importieren auf Datei auswählen und wählen Sie die Suchvorlage aus. Sie können nur Suchvorlagendefinitionen importieren, die ursprünglich aus einer Instanz von Workspace exportiert wurden.
1. Wählen Sie Importieren.

## Eine Suchvorlagendefinition exportieren {#export-a-search-template-definition}

1. Klicken Sie auf der Seite &quot;Globale Verwaltung&quot;unter &quot;Definition der Suchvorlage exportieren&quot;auf &quot;Alle auflisten&quot;.
1. Wählen Sie in der Liste der Suchvorlagen die zu exportierende Vorlage aus.

   >[!NOTE]
   >
   >Sie können mehrere Vorlagen auswählen, es wird jedoch nur die zuletzt ausgewählte Vorlage exportiert.

1. Klicken Sie auf Exportieren und speichern Sie dann die Datei auf Ihrem Computer.

## Globale Einstellungen importieren {#import-global-settings}

1. Klicken Sie auf der Seite &quot;Globale Verwaltung&quot;unter &quot;Globale Einstellungen importieren&quot;auf Datei auswählen und wählen Sie die globale Einstellungsdatei aus. Die Datei mit den globalen Einstellungen muss im XML-Format vorliegen.
1. Wählen Sie Importieren.

## Globale Einstellungen exportieren {#export-global-settings}

1. Klicken Sie auf der Seite &quot;Globale Verwaltung&quot;unter &quot;Globale Einstellungen exportieren&quot;auf &quot;Exportieren&quot;.
1. Speichern Sie die Datei auf Ihrem Computer.

## Globale Workspace-Einstellungen {#workspace-global-settings}

Sie können die Datei mit den globalen Einstellungen ändern. Die einzigen Einstellungen, die Sie bearbeiten können, sind jedoch die Einstellungen JChannelConnectionProperties, formViewOnly und specialRoutes .

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Die Datei mit den globalen Einstellungen für Workspace enthält die folgenden Einstellungen:

### specialRoutes settings {#specialroutes-settings}

Die Einstellungen unter *specialRoutes* geben die Eigenschaften der Sonderrouten („Genehmigen“ und „Ablehnen“) in Workspace an. Unter bestimmten Umständen werden die Schaltflächen für diese Routen auf den Aufgabenkarten in Workspace angezeigt und der Benutzer kann sie auswählen, ohne das Formular zu öffnen. Sie können die Einstellungen für specialRoutes in der Datei mit den globalen Einstellungen ändern, um benutzerdefinierte Namen für die Genehmigung und Ablehnung hinzuzufügen oder zusätzliche Routen zu erstellen.

**client_specialRoutes_routes_approve_style:** Der Name des Stils, der sich im Workspace-Design befindet und die Symbole der Schaltfläche &quot;Genehmigen&quot;angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Um einen Stil für eine benutzerdefinierte Schaltfläche zu definieren, müssen Sie die folgende Vorlage verwenden:
` .buttonApprove {  icon: Embed('images/LC_DirectApprove_Sm_N.png');  disabledIcon: Embed('images/LC_DirectApprove_Sm_D.png');  paddingLeft: 5;  }` Die CSS-Datei von Workspace ist in die Datei &quot;workspace-theme.swf&quot;eingebettet, die sich in der Datei &quot;adobe-workspace-client.ear > adobe-workspace-client.war&quot;befindet. Um das Erscheinungsbild von Workspace zu ändern, müssen Sie die Datei „workspace-theme.swf“ erneut kompilieren.

**client_specialRoutes_routes_deny_names:** Die verschiedenen Zeichenfolgen, die ein Workbench-Benutzer verwenden kann, um als „Ablehnen“ interpretiert zu werden. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise Ablehnen. Wenn der Workspace-Benutzer das Wort Ablehnen in einem Prozess verwendet, wird es nicht erkannt. Der Begriff Ablehnen muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_routes_deny_style:** Der Name des Stils, der sich in der Workspace-Designdatei befindet und die Symbole für die Schaltfläche &quot;Ablehnen&quot;angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Um einen Stil für eine benutzerdefinierte Schaltfläche zu definieren, müssen Sie die folgende Vorlage verwenden:
`  .buttonDeny {   icon: Embed('images/LC_DirectDeny_Sm_N.png');   disabledIcon: Embed('images/LC_DirectDeny_Sm_D.png');   paddingLeft: 0;   }` **client_specialRoutes_routes_approve_names:** Die verschiedenen Zeichenfolgen, die ein Workbench-Benutzer als &quot;Genehmigen&quot;interpretieren kann. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise „genehmigen“. Wenn der Workspace-Benutzer das Wort „Genehmigen“ in einem Prozess verwendet, wird es nicht erkannt. Der Begriff „Genehmigen“ muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_names:** Die Schlüssel zum Lokalisieren des benutzerdefinierten Zeichenfolgenwerts aus den Ressourcendateien. Jeder Eintrag in dieser Einstellung muss die Werte für Namen und Stil enthalten.

### JGroup-Einstellungen {#jgroup-settings}

Diese Einstellungen werden nur angezeigt, wenn Sie von Adobe LiveCycle ES 2.5 oder früher aktualisiert haben.

**server_remoteevents_ClientTimeoutMilliseconds:** Die maximale Zeitspanne, die die JGroup auf Ereignismeldungen wartet. Diese Einstellung sollte nicht geändert werden.

**server_remoteevents_ServerTimeoutMilliseconds:** Die maximale Wartezeit für den Empfang von JGroup-Meldungen auf dem Server. Diese Option legt die Verzögerung zum Senden von Meldungen vom Server an den Client fest.

**server_remoteevents_JChannelConnectionProperties:** Die Verbindungseigenschaften für die JGroup, die für die Kommunikation zwischen dem Server (auf dem ein Service-Ereignis vom RemoteEvent-Service verarbeitet wird) und allen Instanzen von Workspace verwendet werden.

Möglicherweise müssen Sie die UDP-Werte für die Multicast-IP-Adresse (mcast_addr), den Multicast-IP-Port (mcast_port) und die TTL für die Multicast-Pakete (ip_ttl) ändern. Standardmäßig werden die Multicast-IP-Adresse und Port-Werte zufällig generiert und müssen im Allgemeinen nicht geändert werden. Wenn Ihr Unternehmen jedoch Netzwerkrichtlinien für bestimmte Multicast-Bereiche für Multicast-IP-Adressen hat, müssen Sie die Werte möglicherweise ändern.

>[!NOTE]
>
>Die TTL muss größer sein als die Anzahl der Netzwerkwechsel zwischen den Servern im Cluster. Wenn der Wert jedoch zu hoch eingestellt ist, kann dies dazu führen, dass Multicast-Pakete in Subnetze gelangen, wo sie verworfen werden.

Die übrigen Eigenschaften dieser Einstellung sollten nicht geändert werden.

**server_remoteevents_JGroupName:** Der Name der JGroup, die für die Remote-Ereigniskommunikation verwendet wird. Dieser Wert wird zufällig generiert, um Konflikte in Clustern zu vermeiden. Dieser Wert sollte nicht geändert werden.

<!--

For additional information on JGroups and Workspace, see [JGroups and AEM forms Workspace - Explained](https://blogs.adobe.com/livecycle/2011/03/jgroups-and-livecycle-workspace-explained.html).

-->

### formView-Einstellungen {#formview-settings}

**client_formView_openFormInFullScreen:** Wählen Sie zum Anzeigen aller Formulare in Workspace im Vollbildmodus für diese Option die Einstellung „true“. Standardmäßig ist diese Option auf „false“ festgelegt und die Formulare werden nicht im Vollbildmodus angezeigt. Der User-Dienst enthält eine Option zum Öffnen des Dokuments, das einer Aufgabe zugeordnet ist, im Vollbildmodus. Auf diese Weise können Sie die Anzeige pro Prozess steuern.

**client_routes_formViewOnly:** Bei der Einstellung „True“ werden Routen nicht in der Karten- oder Listenansicht von Workspace angezeigt. Der Standardwert „False“ bedeutet, dass Routen in der Karten- und Listenansicht angezeigt werden.

### Andere Einstellungen {#other-settings}

**client_mimeTypes_openOutsideBrowser:** Der MIME-Typ von Dokumenten, die außerhalb der Workspace-Browserinstanz geöffnet werden. Wenn die Prozesse Ihres Unternehmens einen zusätzlichen MIME-Typ erfordern, geben Sie ihn hier an. Die Standardwerte sind:

* `application/msword`
* `application/msexcel`
* `application/ms-powerpoint`

**client_customUI_caching:** Dient zum Zwischenspeichern einer benutzerdefinierten Aufgabenbenutzeroberfläche.

**server_debugLevel:** Ändern Sie diese Einstellung nicht.

**client_pollingInterval:** Legt das Abfrageintervall (in Sekunden) fest, das für Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) verwendet wird, um die neuen und geänderten Aufgaben zu erkennen. Der Standardwert ist 3 Sekunden. Dies funktioniert nicht für AEM Forms Workspace.

**client_systemContext_name:** Geben Sie einen benutzerdefinierten Namen (z. B. Bürger) an, der im Feld Hinzugefügt von (auf der Registerkarte Anlagen für die Anlagen einer Aufgabe in AEM Forms Workspace angezeigt werden soll.

Definieren des benutzerdefinierten Namens:

`<client_systemContext_name>[custom name to display]</client_systemContext_name>`

>[!NOTE]
>
>Für die Demo-Anwendung lautet der standardmäßige Anzeigename **Bürger**. Für eine benutzerdefinierte Anwendung, die Sie erstellen, lautet der standardmäßige Anzeigename **Systemkontextkonto**.
>
>**client_idleTimeout:** Wenn ein Benutzer über einen bestimmte Zeitraum hinweg inaktiv bleibt, läuft die AEM Forms Workspace-Sitzung ab. Um die Funktion zu aktivieren, fügen Sie „Globale Einstellungen &lt;client_idleTimeout>*IDLE_TIMEOUT_IN_SECONDS*&lt;/client_idleTimeout>“ einen Eintrag hinzu. Sie können den Wert 0 angeben, um die Zeitüberschreitung im Leerlauf zu deaktivieren. Der Zeitraum wird in Sekunden angegeben.
