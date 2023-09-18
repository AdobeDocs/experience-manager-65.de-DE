---
title: Connector für IBM&reg konfigurieren - Content Manager
description: Konfigurieren Sie den Connector für IBM&reg; Content Manager , um die Kommunikation zwischen AEM Forms und IBM&reg; Content Manager zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 50f0c963-8007-4e2a-aa73-d99b97d9a1aa
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 2%

---

# Connector für IBM® Content Manager konfigurieren{#configuring-connector-for-ibm-content-manager}

Connector für IBM® Content Manager ermöglicht die Kommunikation zwischen AEM Formularen und IBM® Content Manager. Weitere Hintergrundinformationen finden Sie unter &quot;Connectors for ECM&quot;in [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

## Verbindung mit IBM® Content Manager konfigurieren {#configure-the-ibm-content-manager-connection}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für IBM® Content Manager&quot;.
1. Geben Sie in das Feld &quot;Datastore Name&quot;den Namen des IBM® Content Manager-Datenspeichers ein, mit dem Sie eine Verbindung herstellen möchten. Wenn es sich um eine lokale Datenbank handelt, geben Sie den Namen der Datenbank ein. Wenn es sich um eine Remote-Datenbank handelt, geben Sie deren Aliasnamen ein.
1. Geben Sie in das Feld &quot;Benutzername&quot;die Benutzer-ID eines Benutzers ein, der eine Verbindung zum IBM® Content Manager-Datenspeicher herstellen soll.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort des Benutzers ein.
1. (Optional) Geben Sie im Feld &quot;Alias-Verbindungszeichenfolge&quot;zusätzliche Verbindungsargumente ein. Normalerweise sollte dieses Feld leer sein. Weitere Informationen finden Sie in Ihrer IBM®-Dokumentation.
1. Klicken Sie auf Speichern.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie einen falschen Alias, Benutzernamen oder Kennwort für den Datenspeicher eingeben, erhalten Sie je nachdem, ob der Content Repository Connector für IBM® Content Manager-Dienst ausgeführt wird, die folgenden Ergebnisse:

* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen angehalten wird, wird kein Fehler angezeigt. Wenn Sie den Dienst jedoch das nächste Mal starten, wird eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet wird, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.
