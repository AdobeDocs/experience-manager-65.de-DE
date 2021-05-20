---
title: Connector für EMC Documentum konfigurieren
seo-title: Connector für EMC Documentum konfigurieren
description: Erfahren Sie, wie Sie den Connector für EMC Documentum, um die Kommunikation zwischen AEM Forms und EMC Documentum zu aktivieren.
seo-description: Erfahren Sie, wie Sie den Connector für EMC Documentum, um die Kommunikation zwischen AEM Forms und EMC Documentum zu aktivieren.
uuid: fc96900a-ec8a-4efd-ad8e-25e9967e649b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e62370a7-9d9e-43a3-8014-8e53800c870d
exl-id: a31a496f-87b9-43c0-a98c-5f6ca5d11690
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 93%

---

# Connector für EMC Documentum konfigurieren {#configuring-connector-for-emc-documentum}

Connector für EMC Documentum aktiviert die Kommunikation zwischen AEM Forms und EMC Documentum. Weitere Hintergrundinformationen finden Sie im Abschnitt über Connectors für ECM in [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

Das Einrichten von Connector für EMC Documentum umfasst das Konfigurieren der Serververbindung und der Repository-Anmeldeinformationen.

>[!NOTE]
>
>In früheren Versionen konnten Elemente in einem ECM-Repository gespeichert werden. In der aktuellen Version werden Elemente im systemeigenen AEM Forms-Repository gespeichert und die Repository Provider-Dienste werden nicht mehr unterstützt. Die Migration von Elementen aus einem ECM-Repository zum AEM Forms-Repository erfolgt, wenn Sie eine Aktualisierung auf AEM Forms vornehmen. Weitere Informationen hierzu finden Sie im AEM Forms-Aktualisierungshandbuch für Ihren Anwendungsserver.

## Serververbindung konfigurieren {#configuring-the-server-connection}

In diesem Abschnitt werden die Aufgaben für Connector für EMC Documentum, den Sie auf der Seite „Konfigurationseinstellungen“ ausführen können, beschrieben.

>[!NOTE]
>
>Wenn Sie alle Einstellungen gleichzeitig konfigurieren, müssen Sie nur einmal auf „Speichern“ klicken.

### Anwendungsserver konfigurieren  {#configure-the-server}

Sie müssen die Serverinformationen des Verbindungsbrokers konfigurieren. Diese Informationen werden zum Verbinden mit den Documentum-Inhalts-Repositorys und zum Starten von Connector für EMC Documentum benötigt.

1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Geben Sie im Bereich mit den Documentum-Konfigurationsinformationen den Hostnamen bzw. die IP-Adresse und die Anschlussnummer des Verbindungsbrokers ein. Die Anschlussnummer muss eine positive Ganzzahl sein (beispielsweise 1489).
1. Klicken Sie auf Speichern.

### Prinzipalanmeldeinformationen konfigurieren  {#configure-principal-credentials}

Beim Konfigurieren der Prinzipalanmeldeinformationen hängt der anzugebende Repository-Name davon ab, ob Sie bei der Anmeldung einen expliziten Repository-Namen angegeben haben.

Wenn Sie einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob der Dienst aktuell ausgeführt wird, folgende Ergebnisse:

* Wenn der Repository Provider-Dienst für EMC Documentum und der EMC Documentum Content Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen beendet sind, tritt kein Fehler auf. Beim nächsten Start des Dienstes wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Repository Provider-Dienst für EMC Documentum oder der EMC Documentum Content Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet sind, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Geben Sie im Bereich „Documentum-Prinzipalanmeldeinformationen“ den Benutzernamen und das Kennwort eines Benutzers mit Superadministrator-Berechtigungen ein.
1. Wurde bei der Anmeldung kein expliziter Repository-Name angegeben, geben Sie den Repository-Namen ein, dem die Anmeldeinformationen zugeordnet sind.
1. Klicken Sie auf Speichern.

### Repository Service Provider ändern  {#change-the-repository-service-provider}

Sie können festlegen, welcher Repository Service Provider mit Documentum verwendet werden soll. Aufrufe des Repository-Dienstes werden an den konfigurierten Provider delegiert. Die folgenden Optionen sind verfügbar:

**Aktueller Repository Service Provider-Name:** Der Name des aktuellen Repository Service Providers

**ECM Documentum Repository Provider:** Legt den Documentum Repository Provider als Provider für das Repository fest. Diese Option ist veraltet.

**Repository-Anbieter:** Legt den nativen Repository-Provider als Provider für das Repository fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie RepositoryService unter &quot;Anwendungen und Dienste&quot;> &quot;Dienstverwaltung&quot;. <!-- Fix broken link (See Managing Services) -->.

1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Wählen Sie im Bereich „Repository Service Provider-Informationen“ einen anderen Repository Service Provider aus.
1. Klicken Sie auf Speichern.

## Repository-Anmeldeinformationen konfigurieren  {#configuring-repository-credentials}

Die Documentum-Anmeldeinformationen werden im AEM Forms-Systemkontext verwendet. Repository-Anmeldeinformationen gelten für bestimmte Repositorys in Documentum. Sie können Anmeldeinformationen für beliebig viele Repositorys angeben. Sie dürfen jedoch nur einen Satz Anmeldeinformationen pro Repository angeben.

### Repository-Anmeldeinformationen hinzufügen  {#add-a-repository-credential}

1. Klicken Sie in Administration Console auf „Dienste“ > „Connector für EMC Documentum“ > „Einstellungen für Repository-Anmeldeinformationen“.
1. Klicken Sie auf Hinzufügen. Die Seite „Documentum-Systemanmeldeinformationen“ wird eingeblendet.
1. Geben Sie einen Namen für das Repository ein.
1. Geben Sie einen Benutzernamen und ein Kennwort ein.
1. Klicken Sie auf Speichern.

Wenn der Content Repository Connector für EMC Documentum-Dienst und/oder der Repository-Dienst für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen im Abgleich mit dem angegebenen Repository überprüft, bevor sie in der Datenbank gespeichert werden. Sind die Anmeldeinformationen ungültig oder vorhanden, wird eine Fehlermeldung angezeigt.

### Repository-Berechtigung entfernen  {#remove-a-repository-credential}

1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Aktivieren Sie das Kontrollkästchen neben dem Repository, von dem Berechtigung entfernt werden sollen, und klicken Sie auf „Entfernen“. Die Anmeldeinformationen für das ausgewählte Repository werden aus der Datenbank entfernt.

### Benutzernamen und Kennwort für die Repository-Anmeldeinformationen ändern  {#change-the-user-name-and-password-for-a-repository-credential}

1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Klicken Sie auf den Namen des Repositorys, für das Anmeldeinformationen bearbeitet werden sollen.
1. Ändern Sie den Benutzernamen oder das Kennwort (oder beide Angaben) für das Repository. (Der Repository-Name ist schreibgeschützt.)
1. Klicken Sie auf Speichern.

Wenn der Content Repository Connector für EMC Documentum-Dienst und/oder der Repository-Dienst für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen im Abgleich mit dem angegebenen Repository überprüft, bevor sie in der Datenbank gespeichert werden. Sind die Anmeldeinformationen ungültig oder vorhanden, wird eine Fehlermeldung angezeigt.

## Anforderung für die Freigabe von Workspace-Aufgabenwarteschlangen aktivieren  {#enable-the-request-for-sharing-of-workspace-task-queues}

In Workspace sind einige manuelle Schritte erforderlich, um sicherzustellen, dass die Funktion für die Anforderung zur Freigabe von Aufgabenwarteschlangen in EMC Documentum ordnungsgemäß funktioniert.

1. Nachdem Sie AEM Forms bereitgestellt und Workbench installiert haben, melden Sie sich bei Workbench an und öffnen Sie die Ansicht „Ressourcen“. In dieser Ansicht stellen Sie fest, wo sich die Datei „QueueSharing.swf“ befindet.
1. Ziehen Sie die Datei „QueueSharing.swf“ aus der Ansicht „Ressourcen“ auf den Windows-Desktop oder an einen vergleichbaren Speicherplatz (je nach Betriebssystem).
1. Wählen Sie in Administration Console „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Ändern Sie unter „Repository Service Provider-Informationen“ den konfigurierten Repository-Provider in „EMC Documentum Repository Provider“.
1. Starten Sie Workbench und kopieren Sie die Datei „QueueSharing.swf“ von dem Speicherort, an den Sie sie ursprünglich kopiert haben (z. B. vom Windows-Desktop), in einen vorhandenen Ordner innerhalb des EMC Documentum-Repositorys.
1. Öffnen Sie in der Workbench-Prozessansicht den Prozess „Queue Sharing“.
1. Öffnen Sie in der Ansicht „Variablen“ die Eigenschaften der Variablen „theForm“ und ändern Sie den URI in den Pfad, in dem Sie die Datei „QueueSharing.swf“ in Schritt 5 abgelegt haben.
1. Speichern Sie den Prozess.
1. Migrieren Sie den Prozess gemäß den Richtlinien Ihres Unternehmens zur Produktionsumgebung.
