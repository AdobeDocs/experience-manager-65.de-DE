---
title: Importieren und Exportieren von globalen Einstellungen
description: Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: cdb7ff54-7891-45b1-a921-10b01ef5188d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 100%

---

# Importieren und Exportieren von globalen Einstellungen {#importing-and-exporting-global-settings}

Sie können Suchvorlagendefinitionen und globale Einstellungen für Workspace importieren und exportieren.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Sie können beispielsweise von einer Entwicklungsumgebung zu einer Produktionsumgebung wechseln, indem Sie die Suchvorlagendefinitionen und globalen Einstellungen aus einer Umgebung exportieren und in die andere importieren.

Nach dem Export der Datei mit den globalen Einstellungen können Sie die Einstellungen in einem XML- oder Texteditor ändern. Allerdings sind die einzigen Einstellungen, die Sie bearbeiten sollten, die Einstellungen für JChannelConnectionProperties, formViewOnly und specialRoutes. Weitere Informationen finden Sie unter [Globale Workspace-Einstellungen](importing-exporting-global-settings.md#workspace-global-settings).


>[!NOTE]
>
>Wenn Sie die Ereigniseigenschaften in der Datei mit den globalen Einstellungen ändern, müssen Sie den Server neu starten.

## Importieren einer Suchvorlagendefinition {#import-a-search-template-definition}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Workspace“ > „Globale Verwaltung“.
1. Klicken Sie unter dem Feld „Suchvorlagendefinition importieren“ auf „Datei auswählen“ und wählen Sie die Suchvorlage aus. Sie können nur Suchvorlagendefinitionen importieren, die ursprünglich aus einer Instanz von Workspace exportiert wurden.
1. Wählen Sie Importieren.

## Exportieren einer Suchvorlagendefinition {#export-a-search-template-definition}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Suchvorlagendefinition exportieren“ auf „Alle auflisten“.
1. Wählen Sie in der Liste der Suchvorlagen die zu exportierende Vorlage aus.

   >[!NOTE]
   >
   >Sie können mehrere Vorlagen auswählen, es wird jedoch nur die zuletzt ausgewählte Vorlage exportiert.

1. Klicken Sie auf „Exportieren“ und speichern Sie dann die Datei auf Ihrem Computer.

## Importieren globaler Einstellungen {#import-global-settings}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Globale Einstellungen importieren“ auf „Datei auswählen“ und wählen Sie die globale Einstellungsdatei aus. Die globale Einstellungsdatei muss im XML-Format vorliegen.
1. Wählen Sie Importieren.

## Exportieren globaler Einstellungen {#export-global-settings}

1. Klicken Sie auf der Seite „Globale Verwaltung“ unter „Globale Einstellungen exportieren“ auf „Exportieren“.
1. Speichern Sie die Datei auf Ihrem Computer.

## Globale Workspace-Einstellungen {#workspace-global-settings}

Sie können die Datei mit den globalen Einstellungen ändern, sollten jedoch nur die Einstellungen für „JChannelConnectionProperties“, „formViewOnly“ und „specialRoutes“ bearbeiten.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Die Datei mit den globalen Einstellungen für Workspace enthält die folgenden Einstellungen:

### Einstellungen für specialRoutes {#specialroutes-settings}

Die Einstellungen unter *specialRoutes* geben die Eigenschaften der Sonderrouten („Genehmigen“ und „Ablehnen“) in Workspace an. Unter bestimmten Umständen werden die Schaltflächen für diese Routen auf den Aufgabenkarten in Workspace angezeigt und die Benutzenden können sie auswählen, ohne das Formular zu öffnen. Sie können die Einstellungen für specialRoutes in der globalen Einstellungsdatei ändern, um benutzerdefinierte Namen für die Genehmigung und Ablehnung hinzuzufügen oder zusätzliche Routen zu erstellen.

**client_specialRoutes_routes_approve_style:** Der Name des Stils, der sich im Workspace-Design befindet und die Symbole für die Genehmigungsschaltfläche angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Zum Definieren eines Stils für eine benutzerdefinierte Schaltfläche müssen Sie die folgende Vorlage verwenden:
` .buttonApprove {  icon: Embed('images/LC_DirectApprove_Sm_N.png');  disabledIcon: Embed('images/LC_DirectApprove_Sm_D.png');  paddingLeft: 5;  }` Die Workspace-CCS-Datei ist in der Datei „workspace-theme.swf“ eingebettet, die in der Datei „adobe-workspace-client.ear > adobe-workspace-client.war“ enthalten ist. Um das Erscheinungsbild von Workspace zu ändern, müssen Sie die Datei „workspace-theme.swf“ erneut kompilieren.

**client_specialRoutes_routes_deny_names:** Die verschiedenen Zeichenfolgen, die ein Workbench-Benutzer verwenden kann, um als „Ablehnen“ interpretiert zu werden. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise Ablehnen. Wenn der Workspace-Benutzer das Wort Ablehnen in einem Prozess verwendet, wird es nicht erkannt. Der Begriff Ablehnen muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_routes_deny_style:** Der Name des Stils, der sich in der Workspace-Design-Datei befindet und die Symbole für die Ablehnungsschaltfläche angibt. Der Stil muss Werte für ein aktiviertes und ein deaktiviertes Symbol enthalten. Zum Definieren eines Stils für eine benutzerdefinierte Schaltfläche müssen Sie die folgende Vorlage verwenden:
`  .buttonDeny {   icon: Embed('images/LC_DirectDeny_Sm_N.png');   disabledIcon: Embed('images/LC_DirectDeny_Sm_D.png');   paddingLeft: 0;   }` **client_specialRoutes_routes_approve_names:** Die verschiedenen Zeichenfolgen, die Workspace-Benutzende in der Bedeutung von „Genehmigen“ verwenden können. Bei den Zeichenfolgen muss die Groß-/Kleinschreibung beachtet werden. Der Standardwert lautet beispielsweise „genehmigen“. Wenn der Workspace-Benutzer das Wort „Genehmigen“ in einem Prozess verwendet, wird es nicht erkannt. Der Begriff „Genehmigen“ muss dieser Einstellung hinzugefügt werden, damit die Routenschaltfläche angepasst und mit dem Stil versehen wird.

**client_specialRoutes_names:** Die Schlüssel zum Lokalisieren des benutzerdefinierten Zeichenfolgenwerts aus den Ressourcendateien. Jeder Eintrag in dieser Einstellung muss die Werte für Namen und Stil enthalten.

### Einstellungen für JGroup {#jgroup-settings}

Diese Einstellungen werden nur angezeigt, wenn Sie von Adobe LiveCycle ES 2.5 oder früher aktualisiert haben.

**server_remoteevents_ClientTimeoutMilliseconds:** Die maximale Zeitspanne, die die JGroup auf Ereignismeldungen wartet. Diese Einstellung sollte nicht geändert werden.

**server_remoteevents_ServerTimeoutMilliseconds:** Die maximale Wartezeit für den Empfang von JGroup-Meldungen auf dem Server. Diese Option legt die Verzögerung zum Senden von Meldungen vom Server an den Client fest.

**server_remoteevents_JChannelConnectionProperties:** Die Verbindungseigenschaften für die JGroup, die für die Kommunikation zwischen dem Server (auf dem ein Service-Ereignis vom RemoteEvent-Service verarbeitet wird) und allen Instanzen von Workspace verwendet werden.

Möglicherweise müssen Sie die UDP-Werte für die Multicast-IP-Adresse (mcast_addr), den Multicast-IP-Port (mcast_port) und die TTL für die Multicast-Pakete (ip_ttl) ändern. Standardmäßig werden die Werte für Multicast-IP-Adresse und -Port nach dem Zufallsprinzip generiert und müssen im Allgemeinen nicht geändert werden. Falls in Ihrer Firma jedoch Netzwerkrichtlinien hinsichtlich bestimmter Multicast-Bereiche für Multicast-IP-Adressen bestehen, müssen Sie die Werte eventuell ändern.

>[!NOTE]
>
>Die TTL muss größer als die Anzahl der Netzwerk-Switches zwischen den Servern im Cluster sein. Wird der Wert jedoch zu hoch eingestellt, kann dies dazu führen, dass Multicast-Pakete in Subnetze gelangen, wo sie gelöscht werden.

Die übrigen Eigenschaften dieser Einstellung sollten nicht geändert werden.

**server_remoteevents_JGroupName:** Der Name der JGroup, die für die Remote-Ereigniskommunikation verwendet wird. Dieser Wert wird nach dem Zufallsprinzip generiert, um Konflikte in Clustern zu vermeiden. Dieser Wert sollte nicht geändert werden.

<!--

For additional information on JGroups and Workspace, see [JGroups and AEM forms Workspace - Explained](https://blogs.adobe.com/livecycle/2011/03/jgroups-and-livecycle-workspace-explained.html).

-->

### formView-Einstellungen {#formview-settings}

**client_formView_openFormInFullScreen:** Wählen Sie zum Anzeigen aller Formulare in Workspace im Vollbildmodus für diese Option die Einstellung „true“. Standardmäßig ist diese Option auf „false“ festgelegt und die Formulare werden nicht im Vollbildmodus angezeigt. Der Benutzerdienst enthält eine Option zum Öffnen des Dokuments, die einer Aufgabe im Vollbildmodus zugeordnet ist. Auf diese Weise können Sie die Anzeige pro Prozess steuern.

**client_routes_formViewOnly:** Bei der Einstellung „True“ werden Routen nicht in der Karten- oder Listenansicht von Workspace angezeigt. Der Standardwert „False“ bedeutet, dass Routen in der Karten- und Listenansicht angezeigt werden.

### Andere Einstellungen {#other-settings}

**client_mimeTypes_openOutsideBrowser:** Der MIME-Typ der Dokumente, die außerhalb der Workspace-Browser-Instanz geöffnet werden. Wenn die Prozesse Ihres Unternehmens einen zusätzlichen MIME-Typ erfordern, geben Sie ihn hier an. Die Standardwerte lauten:

* `application/msword`
* `application/msexcel`
* `application/ms-powerpoint`

**client_customUI_caching:** Dient zum Zwischenspeichern einer benutzerdefinierten Aufgabenbenutzeroberfläche.

**server_debugLevel:** Ändern Sie diese Einstellung nicht.

**client_pollingInterval:** Legt das Abfrageintervall (in Sekunden) fest, das für Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) verwendet wird, um die neuen und geänderten Aufgaben zu erkennen. Der Standardwert ist 3 Sekunden. Dies funktioniert für AEM Forms Workspace nicht.

**client_systemContext_name:** Geben Sie einen benutzerdefinierten Namen (z. B. Bürger) an, der im Feld „Hinzugefügt von“ (auf der Registerkarte „Anlagen“) für die Anlagen einer Aufgabe in AEM Forms Workspace angezeigt werden soll.

Definieren des benutzerdefinierten Namens:

`<client_systemContext_name>[custom name to display]</client_systemContext_name>`

>[!NOTE]
>
>In der Demoanwendung lautet der standardmäßige Anzeigename **Bürger**. In einer von Ihnen erstellten benutzerdefinierten Anwendung lautet der standardmäßige Anzeigename **Systemkontextkonto**.
>
>**client_idleTimeout:** Wenn ein Benutzer über einen bestimmte Zeitraum hinweg inaktiv bleibt, läuft die AEM Forms Workspace-Sitzung ab. Um die Funktion zu aktivieren, fügen Sie „Globale Einstellungen &lt;client_idleTimeout>*IDLE_TIMEOUT_IN_SECONDS*&lt;/client_idleTimeout>“ einen Eintrag hinzu. Sie können den Wert 0 angeben, um die Zeitüberschreitung im Leerlauf zu deaktivieren. Der Zeitraum wird in Sekunden angegeben.
