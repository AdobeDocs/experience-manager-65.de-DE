---
title: Connector for IBM Content Manager konfigurieren
seo-title: Connector für IBM Content Manager konfigurieren
description: Connector für IBM Content Manager aktiviert die Kommunikation zwischen AEM Forms und IBM Content Manager.
seo-description: Connector für IBM Content Manager aktiviert die Kommunikation zwischen AEM Forms und IBM Content Manager.
uuid: 3d55169d-93e3-4d4e-b18b-2a3394e1de3b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3094b178-3b1a-46b3-8fbd-c20388afa3a7
exl-id: 50f0c963-8007-4e2a-aa73-d99b97d9a1aa
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 96%

---

# Connector für IBM Content Manager konfigurieren{#configuring-connector-for-ibm-content-manager}

Connector für IBM Content Manager aktiviert die Kommunikation zwischen AEM Forms und IBM Content Manager. Weitere Hintergrundinformationen finden Sie im Abschnitt über Connectors für ECM in [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

## IBM Content Manager-Verbindung konfigurieren {#configure-the-ibm-content-manager-connection}

1. Wählen Sie in Administration Console „Dienste“ > „Connector für IBM Content Manager“.
1. Geben Sie in das Feld „Datenspeichername“ den Namen des IBM Content Manager-Datenspeichers ein, mit dem eine Verbindung hergestellt werden soll. Wenn es sich um eine lokale Datenbank handelt, geben Sie deren Namen ein. Wenn es sich um eine Remotedatenbank handelt, geben Sie deren Aliasnamen ein.
1. Geben Sie in das Feld „Benutzername“ die Benutzer-ID eines Benutzers ein, der mit dem IBM Content Manager-Datenspeicher eine Verbindung herstellen können soll.
1. Geben Sie in das Feld „Kennwort“ das Kennwort des Benutzers ein.
1. (Optional) Geben Sie in das Feld „Alias-Verbindungszeichenfolge“ zusätzliche Verbindungsargumente ein. In den meisten Fällen sollte dieses Feld leer sein. Weitere Informationen finden Sie in der IMB-Dokumentation.
1. Klicken Sie auf Speichern.

## Diensteinstellungen überprüfen  {#validation-of-service-settings}

Wenn Sie einen falschen Aliasnamen für den Datenspeicher, einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob der Content Repository Connector für IBM Content Manager-Dienst aktuell ausgeführt wird, folgende Ergebnisse:

* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen beendet ist, tritt kein Fehler auf. Beim nächsten Start des Dienstes wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet ist, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.
