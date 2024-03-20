---
title: Konfigurieren des Connectors für IBM FileNet
description: Erfahren Sie, wie Sie den Connector für IBM FileNet konfigurieren, um die Kommunikation zwischen AEM Formularen und IBM FileNet zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f4045df5-a35b-41d7-910e-971017148597
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 21%

---

# Konfigurieren des Connectors für IBM FileNet {#configuring-connector-for-ibm-filenet}

Connector für IBM FileNet ermöglicht die Kommunikation zwischen AEM Formularen und IBM FileNet. Weitere Hintergrundinformationen finden Sie unter „Connectors for ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>In früheren Versionen konnten Assets in einem ECM-Repository gespeichert werden. In dieser Version werden Assets im nativen AEM Forms-Repository gespeichert und die Repository Provider-Dienste werden nicht mehr unterstützt. Die Migration von Assets aus einem ECM-Repository in das AEM Forms-Repository erfolgt bei einer Aktualisierung auf AEM Formulare. Weitere Informationen finden Sie im AEM Forms-Aktualisierungshandbuch für Ihren Anwendungsserver.

## Konfigurieren der Verbindung zur Content Engine {#configure-the-connection-to-the-content-engine}

Die IBM FileNet P8 Content Engine bietet Softwaredienste für die Verwaltung von Unternehmensinhalten und kundendefinierten Geschäftsobjekten in FileNet Content Repositories.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für IBM FileNet&quot;.
1. Geben Sie in das Feld &quot;Content Engine URL&quot;die vollständige Verbindungs-URL ein. Beispiel:

   Wenn Sie die FileNet Content Engine 4.x mit CEWS-Transport verwenden, geben Sie Folgendes ein:

   `cemp:https://ContentEngineHostNameorIP:port/wsi/FNCEWS40DIME?jaasConfigurationName=FileNetP8WSI`

   Wenn Sie die FileNet Content Engine 4.x mit EJB-Transport verwenden, geben Sie Folgendes ein (der EJB-Transport wird nur für WebLogic unterstützt):

   `cemp:t3://ContentEngineHostNameorIP:port/FileNet/Engine?jaasConfigurationName=FileNetP8Engine`

1. Wählen Sie in der Liste „Schema für den Anmeldeinformationsschutz“ eine dieser Schutzebenen aus:

   * **Löschen:** Sendet Anmeldeinformationen im ungeschützten Modus über das Netzwerk
   * **Symmetrisch:** Sendet Anmeldeinformationen verschlüsselt über das Netzwerk

1. Geben Sie im Feld Speicherort der Verschlüsselungsdatei den Pfad zur Verschlüsselungsdatei ein:

   * Wenn Sie als Schema für den Berechtigungsschutz die Option Löschen ausgewählt haben, werden dieses Schlüsselwort und sein Wert ignoriert.
   * Wenn Sie als Schema für den Berechtigungsschutz &quot;Symmetrisch&quot;ausgewählt haben, zeigt der von Ihnen eingegebene Pfad auf den Speicherort einer Verschlüsselungsdatei auf dem Forms-Server, die die zu verwendenden kryptografischen Schlüssel enthält.

1. Geben Sie in das Feld &quot;Standardobjektspeicher&quot;den Objektspeicher-Connector ein, mit dem AEM Formulare standardmäßig eine Verbindung herstellen.
1. Geben Sie in das Feld &quot;Benutzername&quot;den Benutzernamen eines Benutzers ein, der über Zugriffsrechte für den standardmäßigen Objektspeicher verfügt, den Sie im vorherigen Schritt angegeben haben.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort für den Benutzer ein und klicken Sie auf &quot;Speichern&quot;.

## Konfigurieren der Prozess-Engine-Einstellungen {#configure-the-process-engine-settings}

Connector für IBM FileNet enthält den Process Engine Connector für IBM FileNet-Dienst, der zur Interaktion mit der IBM FileNet Process Engine verwendet wird. Sie können Einstellungen für diesen Dienst konfigurieren.

1. Klicken Sie in Administration Console auf Dienste > Connector für IBM FileNet.
1. Um die Verwendung des Process Engine Connector for IBM FileNet-Dienstes zu aktivieren, wählen Sie &quot;Use Process Engine Connector Service&quot;.
1. Geben Sie in das Feld Prozess-Router/Verbindungspunkt den Hostnamen oder die IP-Adresse und die Anschlussnummer sowie den Namen des Prozess-Routers ein. Beispiel:

   `rmi://ProcessEngineHostNameorIP:port/Name`

1. Geben Sie in das Feld &quot;Benutzername&quot;den Benutzernamen ein, mit dem die Verbindung zur Prozess-Engine hergestellt wird.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort ein, mit dem die Verbindung zur Prozess-Engine hergestellt wird, und klicken Sie auf &quot;Speichern&quot;.

## Validierung der Diensteinstellungen {#validation-of-service-settings}

Wenn Sie beim Konfigurieren der Verbindung mit der Content Engine oder den Prozess-Engine-Einstellungen einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie die folgenden Ergebnisse, je nachdem, ob die Dienste derzeit ausgeführt werden:

* Wenn sowohl der Repository Provider-Dienst für IBM FileNet als auch der Content Repository Connector für IBM FileNet-Dienst beim Speichern der Dienstkonfigurationsinformationen angehalten werden, wird kein Fehler angezeigt. Wenn Sie den Dienst jedoch das nächste Mal starten, wird eine Ausnahme ausgelöst und der Dienst wird nicht gestartet.
* Wenn der Repository Provider-Dienst für IBM FileNet oder der Content Repository Connector für IBM FileNet-Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet werden, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

## Repository Service Provider ändern {#change-the-repository-service-provider}

Sie können konfigurieren, welcher Repository Service Provider mit FileNet verwendet werden soll. Repository-Dienstaufrufe werden an den konfigurierten Provider delegiert.

Die folgenden Optionen sind verfügbar:

**Name des aktuellen Repository-Anbieters**: Der Name des aktuellen Repository-Anbieters

**IBM FileNet Repository-Anbieter**: Legt den FileNet-Repository-Anbieter als Anbieter für das Repository fest. Diese Option ist veraltet.

**Repository-Anbieter**: Legt den nativen Repository-Anbieter als Anbieter des Repositorys fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie RepositoryService in Anwendungen und Dienste. <!-- Fix broken link(See Managing Services) -->

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für IBM FileNet&quot;.
1. Wählen Sie im Bereich &quot;Repository Service Provider-Informationen&quot;den alternativen Repository Service Provider aus und klicken Sie auf &quot;Speichern&quot;.
