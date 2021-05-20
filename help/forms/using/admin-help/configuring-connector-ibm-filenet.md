---
title: Connector für IBM FileNet konfigurieren
seo-title: Connector für IBM FileNet konfigurieren
description: Erfahren Sie, wie Sie den Connector für IBM FileNet konfiguriert, um die Kommunikation zwischen AEM Forms und IBM FileNet zu aktivieren.
seo-description: Erfahren Sie, wie Sie den Connector für IBM FileNet konfiguriert, um die Kommunikation zwischen AEM Forms und IBM FileNet zu aktivieren.
uuid: 29d4e221-97f7-4cfb-b7e4-75a8289d2604
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: be4994de-12f8-436e-926a-49a6783b006e
exl-id: f4045df5-a35b-41d7-910e-971017148597
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 94%

---

# Connector für IBM FileNet konfigurieren {#configuring-connector-for-ibm-filenet}

Connector für IBM FileNet aktiviert die Kommunikation zwischen AEM Forms und IBM FileNet. Weitere Hintergrundinformationen finden Sie im Abschnitt über Connectors für ECM in [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>In früheren Versionen konnten Elemente in einem ECM-Repository gespeichert werden. In dieser Version werden Elemente im systemeigenen AEM Forms-Repository gespeichert und die Repository Provider-Dienste werden nicht mehr unterstützt. Die Migration von Elementen aus einem ECM-Repository zum AEM Forms-Repository erfolgt, wenn Sie eine Aktualisierung auf AEM Forms vornehmen. Weitere Informationen hierzu finden Sie im AEM Forms-Aktualisierungshandbuch für Ihren Anwendungsserver.

## Verbindung zu Content Engine konfigurieren {#configure-the-connection-to-the-content-engine}

Die IBM FileNet P8 Content Engine bietet Softwaredienste zum Verwalten von Unternehmensinhalten und kundendefinierten Geschäftsobjekten in FileNet-Inhalts-Repositorys.

1. Wählen Sie in Administration Console „Dienste“ > „ Connector für IBM FileNet“.
1. Geben Sie in das Feld „Content Engine-URL“ die vollständige Verbindungs-URL ein. Beispiel:

   Wenn Sie die FileNet Content Engine 4.x mit CEWS-Transport verwenden, geben Sie Folgendes ein:

   `cemp:https://ContentEngineHostNameorIP:port/wsi/FNCEWS40DIME?jaasConfigurationName=FileNetP8WSI`

   Wenn Sie die FileNet Content Engine 4.x mit EJB-Transport verwenden, geben Sie Folgendes ein (der EJB-Transport wird nur für WebLogic unterstützt):

   `cemp:t3://ContentEngineHostNameorIP:port/FileNet/Engine?jaasConfigurationName=FileNetP8Engine`

1. Wählen Sie in der Liste „Schema für den Anmeldeinformationsschutz“ eine dieser Schutzebenen aus:

   * **Löschen:** Sendet Anmeldeinformationen im ungeschützten Modus über das Netzwerk
   * **Symmetrisch:** Sendet Anmeldeinformationen verschlüsselt über das Netzwerk

1. Geben Sie in das Feld „Speicherort der Verschlüsselungsdatei“ den Pfad zur Verschlüsselungsdatei ein:

   * Wenn Sie als Schema für den Anmeldeinformationsschutz „Löschen“ ausgewählt haben, werden dieses Schlüsselwort und sein Wert ignoriert.
   * Wenn Sie als Schema für den Anmeldeinformationsschutz „Symmetrisch“ ausgewählt haben, zeigt der eingegebene Pfad auf den Speicherort einer Verschlüsselungsdatei auf dem Formularserver, in der die zu verwendenden kryptografischen Schlüssel enthalten sind.

1. Geben Sie in das Feld „Standard-Objektspeicher“ den Objektspeicher-Connector ein, mit dem AEM Forms standardmäßig eine Verbindung herstellt.
1. Geben Sie in das Feld „Benutzername“ den Benutzernamen eines Benutzers ein, der über Zugriffsrechte auf den Standard-Objektspeicher, den Sie im vorherigen Schritt angegeben haben, verfügt.
1. Geben Sie in das Feld „Kennwort“ das Kennwort für den Benutzer ein, und klicken Sie auf „Speichern“.

## Prozess-Engine-Einstellungen konfigurieren  {#configure-the-process-engine-settings}

Connector für IBM FileNet enthält den Process Engine Connector für IBM FileNet-Dienst, mit dessen Hilfe mit der IBM FileNet Process Engine interagiert wird. Sie können Einstellungen für diesen Dienst konfigurieren.

1. Wählen Sie in Administration Console „Dienste“ > „Connector für IBM FileNet“.
1. Um die Verwendung des Process Engine Connectors für den IBM FileNet-Dienst zu aktivieren, wählen Sie „Prozess-Engine-Connectordienst verwenden“.
1. Geben Sie in das Feld „Prozessrouter/Verbindungspunkt“ den Hostnamen oder die IP-Adresse und die Anschlussnummer sowie den Namen des Prozessrouters ein. Beispiel:

   `rmi://ProcessEngineHostNameorIP:port/Name`

1. Geben Sie in das Feld „Benutzername“ den Benutzernamen ein, mit dessen Hilfe eine Verbindung mit der Prozess-Engine hergestellt wird.
1. Geben Sie in das Feld „Kennwort“ das Kennwort ein, mit dessen Hilfe eine Verbindung mit der Prozess-Engine hergestellt wird, und klicken Sie auf „Speichern“.

## Diensteinstellungen überprüfen  {#validation-of-service-settings}

Wenn Sie beim Konfigurieren der Verbindung mit Content Engine oder beim Konfigurieren der Prozess-Engine-Einstellungen einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob die Dienste aktuell ausgeführt werden, folgende Ergebnisse:

* Wenn der Repository Provider-Dienst für IBM FileNet und der Content Repository Connector for IBM FileNet-Dienst beim Speichern der Dienstkonfigurationsinformationen beendet sind, tritt kein Fehler auf. Beim nächsten Start des Dienstes wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Content Repository Provider-Dienst für IBM FileNet oder der Repository Connector for IBM FileNet-Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet ist, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

## Repository Service Provider ändern  {#change-the-repository-service-provider}

Sie können konfigurieren, welcher Repository Service Provider mit FileNet verwendet werden soll. Aufrufe des Repository-Dienstes werden an den konfigurierten Provider delegiert.

Die folgenden Optionen sind verfügbar:

**Aktueller Repository Provider-Name:** Der Name des aktuellen Repository Service Providers

**IBM FileNet Repository Provider:** Stellt den FileNet Repository Provider zum Provider des Repositorys dar. Diese Option ist veraltet.

**Repository-Anbieter:** Legt den nativen Repository-Provider als Provider für das Repository fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie RepositoryService in Anwendungen und Dienste. <!-- Fix broken link(See Managing Services) -->

1. Wählen Sie in Administration Console „Dienste“ > „ Connector für IBM FileNet“.
1. Wählen Sie im Bereich „Repository Service Provider-Informationen“ einen anderen Repository Service Provider aus und klicken Sie auf „Speichern“.
