---
title: Konfigurieren des Connectors für IBM&reg; Content Manager
description: Konfigurieren Sie den Connector für IBM&reg; Content Manager, um die Kommunikation zwischen AEM Forms und IBM&reg; Content Manager zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 50f0c963-8007-4e2a-aa73-d99b97d9a1aa
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 90%
---
# Konfigurieren von Connector for IBM® Content Manager{#configuring-connector-for-ibm-content-manager}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Connector for IBM® Content Manager ermöglicht die Kommunikation zwischen AEM Forms und IBM® Content Manager. Weitere Hintergrundinformationen finden Sie unter „Connectors for ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

## Konfigurieren der Verbindung mit IBM® Content Manager {#configure-the-ibm-content-manager-connection}

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Connector for IBM® Content Manager“ aus.
1. Geben Sie in das Feld „Datenspeichername“ den Namen des IBM® Content Manager-Datenspeichers ein, mit dem eine Verbindung hergestellt werden soll. Wenn es sich um eine lokale Datenbank handelt, geben Sie den Namen der Datenbank ein. Wenn es sich um eine Remote-Datenbank handelt, geben Sie deren Aliasnamen ein.
1. Geben Sie in das Feld „Benutzername“ die Benutzer-ID der Person ein, die mit dem IBM® Content Manager-Datenspeicher eine Verbindung herstellen können soll.
1. Geben Sie in das Feld „Kennwort“ das Kennwort der Benutzerin bzw. des Benutzers ein.
1. (Optional) Geben Sie in das Feld „Alias-Verbindungszeichenfolge“ zusätzliche Verbindungsargumente ein. Normalerweise sollte dieses Feld leer sein. Weitere Informationen finden Sie in der IBM®-Dokumentation.
1. Klicken Sie auf Speichern.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie einen falschen Aliasnamen für den Datenspeicher, einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob der Content-Repository-Dienst für Connector for IBM® Content Manager ausgeführt wird, folgende Ergebnisse:

* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestoppt ist, tritt kein Fehler auf. Beim nächsten Start des Dienstes wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet ist, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.
