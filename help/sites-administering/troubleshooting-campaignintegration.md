---
title: Fehlerbehebung bei der Adobe Campaign Classic-Integration
description: Erfahren Sie, wie Sie Probleme mit der Adobe Campaign Classic-Integration beheben können.
uuid: 835ac2c3-ef2f-4963-9047-aeda3647b114
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: b1d45f01-78de-423c-8f6b-5cb7067c3a2f
exl-id: 317bab41-3504-4e46-9ddc-72e291a34e06
source-git-commit: d673a447e9ce2377c8645c87f12be81cbad06238
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 2%

---


# Fehlerbehebung bei der Adobe Campaign Classic-Integration{#troubleshooting-your-adobe-campaign-classic-integration}

Erfahren Sie, wie Sie Probleme mit der Integration von Adobe Campaign Classic (ACC) beheben können.

Die folgenden Tipps zur Fehlerbehebung helfen bei der Lösung der häufigsten Probleme, die bei der Integration von AEM in ACC auftreten können.

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

Überprüfen Sie, ob HTTP-Aufrufe von beiden Lösungen gesendet und empfangen werden (AEM > Adobe Campaign Classic, Adobe Campaign Classic > AEM). Dieser Tipp hilft Ihnen, Firewall-/SSL-Probleme zu vermeiden.

* Für AEM Funktion können Sie sehen, dass JSON-Aufrufe über die AEM-Autorenoberfläche angefordert werden
   * Diese Aufrufe sollten nicht zu einem HTTP-500-Fehler führen.
   * Wenn HTTP-500-Fehler auftreten, überprüfen Sie die `error.log` für weitere Informationen.
* Die Anhebung der Debugging-Stufe für Kampagnenklassen in AEM kann auch zur Fehlerbehebung beitragen.

## Wenn die Verbindung fehlschlägt {#when-the-connection-fails}

Vergewissern Sie sich, dass Sie die **`aemserver`** Operator in Adobe Campaign Classic.

## Wenn Bilder nicht in der Adobe Campaign Classic-Konsole angezeigt werden {#if-images-do-not-appear-in-the-adobe-campaign-console}

Überprüfen Sie die HTML-Quelle und überprüfen Sie, ob Sie die URL vom Clientcomputer aus öffnen können. Wenn die URL `localhost:4503` Ändern Sie darin die Konfiguration von Day CQ Link Externalizer in Ihrer AEM Autoreninstanz. Sie muss auf eine Veröffentlichungsinstanz verweisen, die vom Adobe Campaign Classic-Konsolencomputer aus erreicht werden kann.

Siehe [Konfigurieren des Externalizers](/help/sites-administering/campaignstandard.md#configuring-the-externalizer).

## Wenn keine Verbindung zwischen AEM und Adobe Campaign Classic hergestellt werden kann  {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Suchen Sie in Adobe Campaign Classic nach der folgenden Fehlermeldung.

* `No datasource defined in the instance 'default'.`

* `Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

Um dieses Problem zu beheben, ändern Sie Folgendes in `$CAMPAIGN_HOME/conf/config-<instance-name>.xml`:

* `<dataStore hosts="*" lang="en_GB">`

## Wenn keine Daten im Dialogfeld &quot;Adobe Campaign Classic&quot;angezeigt werden {#if-no-data-displays-in-the-adobe-campaign-dialog}

Stellen Sie in Adobe Campaign Classic sicher, dass kein Schrägstrich (`/`) nach der Portnummer.

![chlimage_1-149](assets/chlimage_1-149.png)

## Wenn Sie eine Warnung über setlocale erhalten {#if-you-get-a-warning-about-your-setlocale}

Beim Starten des Apache HTTPD-Dienstes für Adobe Campaign Classic wird möglicherweise der Fehler angezeigt `Warning: setlocale: LC_CTYPE cannot change locale`

Vergewissern Sie sich, dass Sie `en_CA.ISO-8859-15 locale` auf Ihrem Adobe Campaign Classic-Server installiert.

* Mit `local -a` können Sie überprüfen, ob es installiert ist. 
* Wenn es nicht installiert ist, können Sie den `/usr/local/neolane/nl6/env.sh` und ändern Sie das Gebietsschema in ein installiertes.

## Wenn beim Kompilieren des Skripts &#39;get_nms_amcGetSeedMetaData_jssp&#39; ein Fehler auftritt {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Wenn die folgende Fehlermeldung in der AEM-Protokolldatei angezeigt wird:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Verwenden Sie die folgende Problemumgehung auf dem Adobe Campaign Classic-Server.

1. Datei öffnen `$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js`
1. Änderungszeile 467 der Methode `amcGetSeedMetaData`
1. Ändern Sie `label : [inclView.@label](mailto:inclView.@label)` in `label : String([inclView.@label](mailto:inclView.@label))`.
1. Speichern.
1. Starten Sie den Server neu.

## Wenn in Adobe Campaign Classic beim Klicken auf die Schaltfläche &quot;Synchronisieren&quot;ein Fehler angezeigt wird {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Wenn Sie auf **Synchronisieren** -Schaltfläche in Adobe Campaign Classic wird möglicherweise der folgende Fehler angezeigt.

* `Error while executing the method 'aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Um dieses Problem zu beheben, stellen Sie sicher, dass die AEM Verbindungs-URL, die im **Externe Konten** in Adobe Campaign Classic ist vom Computer aus erreichbar.

Ein Schalter aus `localhost` auf eine IP-Adresse für die URL kann dieses Problem oft lösen.

## Wenn Sie den Fehler &quot;XTK-Datum+Uhrzeit kann nicht analysiert werden&quot;erhalten {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error}

Nach dem Klicken **Synchronisieren** in AEM erhalten Sie möglicherweise einen Fehler, dass ein Skript auf den Seiten aufgetreten ist.

* `Cannot parse XTK Date+Time 'undefined': not a valid XTK value.`

Dieser Fehler tritt auf, wenn veraltete Adobe Campaign Classic-Informationen auf der AEM-Instanz vorhanden sind. Sie können dieses Problem wie folgt beheben:

1. Entfernen Sie alle Adobe Campaign Classic-Integrationskonfigurationen, die sich auf AEM befinden.
1. Erstellen Sie die Integration neu.
1. Erstellen von Vorlagen.

## Wenn eine Verbindung zu SSL einen Fehler beim Einrichten des Cloud Service anzeigt {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

Senden Sie ein Ticket an das Adobe Campaign-Supportteam, wenn Folgendes im `error.log` AEM.

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

Wenn Sie versuchen, Inhalte im Adobe Campaign Classic-Versand zu synchronisieren, gibt AEM eine Liste von Newslettern zurück. Die URLs zu den Newslettern in der Liste können jedoch HTTP-Adressen anstelle von HTTPS sein. Bei Auswahl eines der Elemente in der Liste tritt ein Fehler auf. Dieser Fehler kann bei der folgenden Einrichtung auftreten.

* Gehostete Adobe Campaign mit HTTPS für die Kommunikation mit AEM Author
* Umgekehrter Proxy, der SSL beendet
* On-Premise-AEM-Autoreninstanz

Gehen Sie wie folgt vor, um dieses Problem zu beheben:

* Der AEM Dispatcher oder Reverse-Proxy muss konfiguriert werden, um das Originalprotokoll als Kopfzeile zu übergeben.
* Die **Apache Felix HTTP Service SSL-Filter** in der OSGi-Konfiguration von AEM müssen mit den erforderlichen Kopfzeileneinstellungen konfiguriert werden.
   * `https://<host>:<port>/system/console/configMgr`
   * Siehe [https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter](https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter)

## Eine benutzerdefinierte Vorlage kann nicht in den Seiteneigenschaften ausgewählt werden {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Beim Erstellen einer E-Mail-Vorlage in AEM für Adobe Campaign Classic müssen Sie die -Eigenschaft einbeziehen `acMapping` mit dem Wert `mapRecipient` im `jcr:content` Knoten der Vorlage. Ist dies nicht der Fall, kann die Adobe Campaign Classic-Vorlage in **Seiteneigenschaften** AEM. Das Feld wird deaktiviert angezeigt.

## Wenn der Fehler &quot;com.day.cq.mcm.campaign.servlets.util.ParameterMapper&quot;in den AEM Logs angezeigt wird {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs}

Möglicherweise wird der Fehler angezeigt `com.day.cq.mcm.campaign.servlets.util.ParameterMapper` in den AEM Logs bei Verwendung einer benutzerdefinierten Vorlage.

Dieser Fehler tritt auf, wenn die `acMapping` -Eigenschaft auf einen anderen Wert als `recipient.firstName`, wird im Adobe Campaign Manager ein leerer Wert erstellt.

Wenn dieser Fehler auftritt, installieren Sie Feature Pack 6576 für AEM aus [Package Share](/help/sites-administering/package-manager.md#package-share).
