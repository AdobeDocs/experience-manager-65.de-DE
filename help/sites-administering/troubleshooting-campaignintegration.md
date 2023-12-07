---
title: Fehlerbehebung bei der Adobe Campaign Classic-Integration
description: Erfahren Sie, wie Sie Probleme mit der Adobe Campaign Classic-Integration beheben können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 317bab41-3504-4e46-9ddc-72e291a34e06
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 98%

---


# Fehlerbehebung bei der Adobe Campaign Classic-Integration{#troubleshooting-your-adobe-campaign-classic-integration}

Erfahren Sie, wie Sie Probleme mit der Integration von Adobe Campaign Classic (ACC) beheben können.

Die folgenden Tipps zur Fehlerbehebung helfen bei der Lösung der häufigsten Probleme, die bei der Zusammenarbeit von AEM mit ACC auftreten können.

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

Überprüfen Sie, ob HTTP-Aufrufe von beiden Lösungen gesendet und empfangen werden (AEM > Adobe Campaign Classic, Adobe Campaign Classic > AEM). Dieser Tipp hilft Ihnen, Firewall-/SSL-Probleme zu vermeiden.

* Bei AEM Funktionen können Sie sehen, dass JSON-Aufrufe über die AEM-Authoring-Oberfläche angefordert werden
   * Diese Aufrufe sollten nicht zu einem HTTP-500-Fehler führen.
   * Wenn HTTP-500-Fehler auftreten, finden Sie in der Datei `error.log` weitere Informationen.
* Auch die Anhebung der Debugging-Stufe für Kampagnenklassen in AEM kann zur Fehlerbehebung beitragen.

## Wenn die Verbindung fehlschlägt {#when-the-connection-fails}

Vergewissern Sie sich, dass Sie in Adobe Campaign Classic den Operator **`aemserver`** konfiguriert haben.

## Wenn in der Adobe Campaign Classic-Konsole keine Bilder angezeigt werden {#if-images-do-not-appear-in-the-adobe-campaign-console}

Überprüfen Sie die HTML-Quelle und prüfen Sie, ob Sie die URL vom Clientcomputer aus öffnen können. Wenn die URL `localhost:4503` enthält, ändern Sie die Konfiguration von Day CQ Link Externalizer in Ihrer AEM Authoring-Instanz. Sie muss auf eine Publishing-Instanz verweisen, die vom Adobe Campaign Classic-Konsolen-Computer aus erreicht werden kann.

Siehe [Konfigurieren des Externalizers](/help/sites-administering/campaignstandard.md#configuring-the-externalizer).

## Wenn keine Verbindung zwischen AEM und Adobe Campaign Classic hergestellt werden kann  {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Suchen Sie in Adobe Campaign Classic nach der folgenden Fehlermeldung.

* `No datasource defined in the instance 'default'.`

* `Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

Um dieses Problem zu beheben, ändern Sie Folgendes in `$CAMPAIGN_HOME/conf/config-<instance-name>.xml`:

* `<dataStore hosts="*" lang="en_GB">`

## Wenn im Adobe Campaign Classic-Dialogfeld keine Daten angezeigt werden {#if-no-data-displays-in-the-adobe-campaign-dialog}

Stellen Sie sicher, dass in Adobe Campaign Classic nach der Port-Nummer kein Schrägstrich (`/`) steht.

![Adobe Campaign Classic - Sicherstellen, dass kein Schrägstrich nach der Anschlussnummer eingefügt wird](assets/chlimage_1-149.png)

## Wenn Sie eine Warnung bezüglich setlocale erhalten {#if-you-get-a-warning-about-your-setlocale}

Beim Starten des Apache HTTPD-Dienstes für Adobe Campaign Classic wird möglicherweise der Fehler `Warning: setlocale: LC_CTYPE cannot change locale` angezeigt

Vergewissern Sie sich, dass Sie `en_CA.ISO-8859-15 locale` auf Ihrem Adobe Campaign Classic-Server installiert haben.

* Mit `local -a` können Sie überprüfen, ob es installiert ist. 
* Wenn es nicht installiert ist, können Sie das Skript `/usr/local/neolane/nl6/env.sh` patchen und das Gebietsschema in ein installiertes Gebietsschema ändern.

## Wenn beim Kompilieren des Skripts „get_nms_amcGetSeedMetaData_jssp“ ein Fehler auftritt {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Wenn die folgende Fehlermeldung in der AEM-Protokolldatei angezeigt wird:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Verwenden Sie die folgende Problemumgehung auf dem Adobe Campaign Classic-Server.

1. Öffnen Sie die Datei `$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js`
1. Ändern Sie Zeile 467 der Methode `amcGetSeedMetaData`
1. Ändern Sie `label : [inclView.@label](mailto:inclView.@label)` in `label : String([inclView.@label](mailto:inclView.@label))`.
1. Speichern.
1. Starten Sie den Server neu.

## Wenn in Adobe Campaign Classic beim Klicken auf die Schaltfläche „Synchronisieren“ ein Fehler angezeigt wird {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Wenn Sie in Adobe Campaign Classic auf die Schaltfläche **Synchronisieren** klicken, wird möglicherweise der folgende Fehler angezeigt.

* `Error while executing the method 'aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Um dieses Problem zu beheben, stellen Sie sicher, dass die AEM-Verbindungs-URL, die unter **Externe Konten** in Adobe Campaign Classic konfiguriert ist, vom Rechner aus erreichbar ist.

Ein Wechsel von `localhost` zu einer IP-Adresse für die URL kann dieses Problem oft lösen.

## Wenn Sie den Fehler „Cannot parse XTK Date+Time ‚undefined‘“ erhalten {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error}

Nachdem Sie in AEM auf **Synchronisieren** geklickt haben, erhalten Sie möglicherweise eine Fehlermeldung, dass ein Skript auf den Seiten aufgetreten ist.

* `Cannot parse XTK Date+Time 'undefined': not a valid XTK value.`

Dieser Fehler tritt auf, wenn veraltete Adobe Campaign Classic-Informationen auf der AEM-Instanz vorhanden sind. Sie können dieses Problem wie folgt beheben:

1. Entfernen Sie alle Adobe Campaign Classic-Integrationskonfigurationen, die sich auf AEM befinden.
1. Erstellen Sie die Integration neu.
1. Erstellen von Vorlagen.

## Wenn eine Verbindung zu SSL einen Fehler beim Einrichten des Cloud Service anzeigt {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

Senden Sie ein Ticket an das Adobe Campaign-Supportteam, wenn Sie Folgendes in der `error.log` von AEM sehen.

```text
javax.net.ssl.SSLProtocolException: handshake alert:  unrecognized_name
at sun.security.ssl.ClientHandshaker.handshakeAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.recvAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.readRecord(Unknown Source)
at sun.security.ssl.SSLSocketImpl.performInitialHandshake(Unknown Source)
at sun.security.ssl.SSLSocketImpl.writeRecord(Unknown Source)
at sun.security.ssl.AppOutputStream.write(Unknown Source)
```

## Wenn HTTP anstelle der erwarteten HTTPS-Links im Synchronisierungsdialogfeld angezeigt wird {#if-you-see-http-instead-of-an-expected-https-links-in-the-synchronization-dialog}

Wenn Sie versuchen, Inhalte in der Adobe Campaign Classic-Bereitstellung zu synchronisieren, gibt AEM eine Liste von Newslettern zurück. Die URLs zu den Newslettern in der Liste können jedoch HTTP-Adressen anstelle von HTTPS sein. Bei Auswahl eines der Elemente in der Liste tritt ein Fehler auf. Dieser Fehler kann beim folgenden Setup auftreten.

* Gehostetes Adobe Campaign mit HTTPS für die Kommunikation mit AEM Author
* Reverse-Proxy, der SSL beendet
* On-Premise-AEM Authoring-Instanz

Gehen Sie wie folgt vor, um dieses Problem zu beheben:

* Der AEM-Dispatcher oder Reverse-Proxy muss so konfiguriert werden, dass das Originalprotokoll als Header übergeben wird.
* Der **Apache Felix HTTP Service SSL-Filter** in der OSGi-Konfiguration von AEM muss mit den erforderlichen Header-Einstellungen konfiguriert werden.
   * `https://<host>:<port>/system/console/configMgr`
   * Siehe [https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter](https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter)

## Eine benutzerdefinierte Vorlage kann nicht in den Seiteneigenschaften ausgewählt werden {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Beim Erstellen einer E-Mail-Vorlage in AEM für Adobe Campaign Classic müssen Sie die Eigenschaft `acMapping` mit dem Wert `mapRecipient` in den Knoten `jcr:content` der Vorlage einschließen. Wenn Sie dies nicht tun, können Sie die Adobe Campaign Classic-Vorlage in den **Seiteneigenschaften** von AEM nicht auswählen. Das Feld wird als deaktiviert angezeigt.

## Wenn der Fehler „com.day.cq.mcm.campaign.servlets.util.ParameterMapper“ in den AEM-Protokollen angezeigt wird {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs}

Wenn Sie eine benutzerdefinierte Vorlage verwenden, wird möglicherweise der Fehler `com.day.cq.mcm.campaign.servlets.util.ParameterMapper` in den AEM-Protokollen angezeigt.

Dieser Fehler tritt auf, wenn die Eigenschaft `acMapping` auf einen anderen Wert als `recipient.firstName` gesetzt wird und deshalb ein leerer Wert in Adobe Campaign Manager erstellt wird.

Wenn dieser Fehler auftritt, installieren Sie Feature Pack 6576 für AEM von [Package Share](/help/sites-administering/package-manager.md#package-share).
