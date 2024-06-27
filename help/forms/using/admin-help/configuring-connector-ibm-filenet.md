---
title: Konfigurieren des Connectors für IBM FileNet
description: Erfahren Sie, wie Sie Connector für IBM FileNet konfigurieren, um die Kommunikation zwischen AEM Forms und IBM FileNet zu ermöglichen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORM
exl-id: f4045df5-a35b-41d7-910e-971017148597
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: ht
source-wordcount: '730'
ht-degree: 100%

---

# Konfigurieren des Connectors für IBM FileNet {#configuring-connector-for-ibm-filenet}

Connector für IBM FileNet ermöglicht die Kommunikation zwischen AEM Forms und IBM FileNet. Weitere Hintergrundinformationen finden Sie unter „Connector-Dienste für ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>In früheren Versionen konnten Assets in einem ECM-Repository gespeichert werden. In dieser Version werden Assets im nativen AEM Forms-Repository gespeichert und die Repository-Anbieter-Dienste werden nicht mehr unterstützt. Die Migration von Assets aus einem ECM-Repository zum AEM Forms-Repository erfolgt, wenn Sie ein Upgrade auf AEM Forms vornehmen. Weitere Informationen hierzu finden Sie im Handbuch zum AEM Forms-Upgrade für Ihren Anwendungs-Server.

## Konfigurieren der Content Engine-Verbindung {#configure-the-connection-to-the-content-engine}

IBM FileNet P8 Content Engine bietet Software-Dienste zum Verwalten von Unternehmensinhalten und kundendefinierten Geschäftsobjekten in FileNet-Inhalts-Repositorys.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für IBM FileNet“.
1. Geben Sie in das Feld für die Content Engine-URL die vollständige Verbindungs-URL ein. Beispiel:

   Wenn Sie FileNet Content Engine 4.x mit CEWS-Transport verwenden, geben Sie Folgendes ein:

   `cemp:https://ContentEngineHostNameorIP:port/wsi/FNCEWS40DIME?jaasConfigurationName=FileNetP8WSI`

   Wenn Sie die FileNet Content Engine 4.x mit EJB-Transport verwenden, geben Sie Folgendes ein (der EJB-Transport wird nur für WebLogic unterstützt):

   `cemp:t3://ContentEngineHostNameorIP:port/FileNet/Engine?jaasConfigurationName=FileNetP8Engine`

1. Wählen Sie in der Liste „Schema für den Anmeldeinformationsschutz“ eine dieser Schutzebenen aus:

   * **Löschen:** Sendet Anmeldeinformationen im ungeschützten Modus über das Netzwerk
   * **Symmetrisch:** Sendet Anmeldeinformationen verschlüsselt über das Netzwerk

1. Geben Sie in das Feld „Speicherort der Verschlüsselungsdatei“ den Pfad zur Verschlüsselungsdatei ein:

   * Wenn Sie als Schema für den Anmeldeinformationsschutz „Klartext“ ausgewählt haben, werden dieses Schlüsselwort und sein Wert ignoriert.
   * Wenn Sie als Schema für den Anmeldeinformationsschutz „Symmetrisch“ ausgewählt haben, zeigt der eingegebene Pfad auf den Speicherort einer Verschlüsselungsdatei auf dem Formular-Server, in der die zu verwendenden kryptografischen Schlüssel enthalten sind.

1. Geben Sie in das Feld „Standardobjektspeicher“ den Objektspeicher-Connector ein, zu dem AEM Forms standardmäßig eine Verbindung herstellt.
1. Geben Sie in das Feld „Benutzername“ den Benutzernamen einer Person mit Zugriffsrechten auf den im vorherigen Schritt angegebenen Standardobjektspeicher ein.
1. Geben Sie in das Feld „Kennwort“ das Kennwort für die Person ein und klicken Sie auf „Speichern“.

## Konfigurieren der Prozess-Engine-Einstellungen {#configure-the-process-engine-settings}

Connector für IBM FileNet enthält den Prozess-Engine-Connector für den IBM FileNet-Dienst, über den mit der IBM FileNet Process Engine interagiert wird. Sie können Einstellungen für diesen Dienst konfigurieren.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für IBM FileNet“.
1. Um den Prozess-Engine-Connector für den IBM FileNet-Dienst verwenden zu können, wählen Sie „Prozess-Engine-Connectordienst verwenden“ aus.
1. Geben Sie in das Feld „Prozessrouter/Verbindungspunkt“ den Host-Namen oder die IP-Adresse und die Port-Nummer sowie den Namen des Prozess-Routers ein. Beispiel:

   `rmi://ProcessEngineHostNameorIP:port/Name`

1. Geben Sie in das Feld für den Benutzernamen den Benutzernamen ein, über den eine Verbindung zu der Prozess-Engine hergestellt wird.
1. Geben Sie in das Feld „Kennwort“ das Kennwort ein, über das eine Verbindung zu der Prozess-Engine hergestellt wird, und klicken Sie auf „Speichern“.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie beim Konfigurieren der Content Engine-Verbindung oder der Prozess-Engine-Einstellungen einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie abhängig davon, ob die Dienste aktuell ausgeführt werden, folgende Ergebnisse:

* Wenn der Dienst „Repository-Anbieter“ für IBM FileNet und der Dienst „Content Repository Connector for IBM FileNet“ beim Speichern der Dienstkonfigurationsinformationen beendet sind, tritt kein Fehler auf. Wenn Sie den Dienst das nächste Mal starten, wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Dienst „Repository-Anbieter“ für IBM FileNet oder der Dienst „Content Repository Connector for IBM FileNet“ beim Speichern der Dienstkonfigurationsinformationen gestartet ist, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

## Ändern des Repository-Dienstanbieters {#change-the-repository-service-provider}

Sie können konfigurieren, welcher Repository-Dienstanbieter mit FileNet verwendet werden soll. Aufrufe des Repository-Dienstes werden an den konfigurierten Anbieter delegiert.

Die folgenden Optionen sind verfügbar:

**Name des aktuellen Repository-Anbieters**: Der Name des aktuellen Repository-Anbieters

**IBM FileNet Repository-Anbieter**: Legt den FileNet-Repository-Anbieter als Anbieter für das Repository fest. Diese Option ist veraltet.

**Repository-Anbieter**: Legt den nativen Repository-Anbieter als Anbieter des Repositorys fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie RepositoryService in Anwendungen und Dienste. <!-- Fix broken link(See Managing Services) -->

1. Wählen Sie in der Administrationskonsole „Dienste“ > „Connector für IBM FileNet“ aus.
1. Wählen Sie im Bereich „Repository-Dienstleister-Informationen“ einen anderen Repository-Dienstleister aus und klicken Sie auf „Speichern“.
