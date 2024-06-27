---
title: Konfigurieren des Connectors für EMC Documentum
description: Erfahren Sie, wie Sie den Connector für EMC Documentum konfigurieren, um die Kommunikation zwischen AEM Forms und EMC Documentum zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a31a496f-87b9-43c0-a98c-5f6ca5d11690
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: ht
source-wordcount: '1020'
ht-degree: 100%

---

# Konfigurieren des Connectors für EMC Documentum {#configuring-connector-for-emc-documentum}

Connector für EMC Documentum aktiviert die Kommunikation zwischen AEM Forms und EMC Documentum. Weitere Hintergrundinformationen finden Sie unter „Connector-Dienste für ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

Das Einrichten von Connector für EMC Documentum umfasst das Konfigurieren der Server-Verbindung und der Repository-Anmeldeinformationen.

>[!NOTE]
>
>In früheren Versionen konnten Assets in einem ECM-Repository gespeichert werden. In der aktuellen Version werden Assets im nativen AEM Forms-Repository gespeichert und die Repository Provider-Dienste werden nicht mehr unterstützt. Die Migration von Assets aus einem ECM-Repository zum AEM Forms-Repository erfolgt, wenn Sie ein Upgrade auf AEM Forms vornehmen. Weitere Informationen hierzu finden Sie im Handbuch zum AEM Forms-Upgrade für Ihren Anwendungs-Server.

## Konfigurieren der Server-Verbindung {#configuring-the-server-connection}

Dieses Thema beschreibt die Aufgaben für Connector for EMC Documentum, die Sie auf der Seite „Konfigurationseinstellungen“ durchführen können.

>[!NOTE]
>
>Wenn Sie alle Einstellungen gleichzeitig konfigurieren, müssen Sie nur einmal auf „Speichern“ klicken.

### Konfigurieren des Servers {#configure-the-server}

Sie müssen die Server-Informationen des Verbindungs-Brokers konfigurieren. Diese Informationen sind erforderlich, um eine Verbindung mit den Documentum-Inhalts-Repositorys herzustellen und um Connector für EMC Documentum zu starten.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Geben Sie im Bereich mit den Documentum-Konfigurationsinformationen den Hostnamen bzw. die IP-Adresse und die Portzahl des Verbindungsbrokers ein. Die Portzahl muss eine positive Ganzzahl sein (z. B. 1489).
1. Klicken Sie auf Speichern.

### Konfigurieren von Prinzipalanmeldeinformationen   {#configure-principal-credentials}

Beim Konfigurieren der Prinzipalanmeldeinformationen hängt der anzugebende Repository-Name davon ab, ob Sie bei der Anmeldung einen expliziten Repository-Namen angegeben haben.

Wenn Sie einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie in Abhängigkeit davon, ob der Dienst aktuell ausgeführt wird, folgende Ergebnisse:

* Wenn der Repository Anbieter-Dienst für EMC Documentum und der EMC Documentum Content-Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen beendet sind, tritt kein Fehler auf. Wenn Sie den Dienst das nächste Mal starten, wird jedoch eine Ausnahme ausgelöst und der Dienst startet nicht.
* Wenn der Repository Anbieter-Dienst für EMC Documentum oder der EMC Documentum Content-Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet sind, versucht der Dienst sofort, die Anmeldedaten zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Geben Sie im Bereich „Documentum-Prinzipalanmeldeinformationen“ den Benutzernamen und das Kennwort einer Person mit Superadministrator-Berechtigungen ein.
1. Wenn bei der Anmeldung kein expliziter Repository-Name angegeben wird, geben Sie den Repository-Namen ein, mit dem die Anmeldeinformationen verknüpft sind.
1. Klicken Sie auf Speichern.

### Ändern des Repository-Dienstanbieters {#change-the-repository-service-provider}

Sie können konfigurieren, welcher Repository Service Provider mit Documentum verwendet werden soll. Aufrufe des Repository-Dienstes werden an den konfigurierten Anbieter delegiert. Die folgenden Optionen sind verfügbar:

**Name des aktuellen Repository Service Providers:** Der Name des aktuellen Repository Service Providers

**ECM Documentum Repository Provider:** Legt den Documentum Repository Provider als Provider des Repositorys fest. Diese Option ist veraltet.

**Repository Provider:** Legt den nativen Repository-Provider als Provider des Repositorys fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie „RepositoryService“ in „Anwendungen und Dienste“ > „Service-Management“. <!-- Fix broken link (See Managing Services) -->

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Wählen Sie im Bereich „Repository Service Provider-Informationen“ einen anderen Repository Service Provider aus.
1. Klicken Sie auf Speichern.

## Konfigurieren von Repository-Anmeldeinformationen {#configuring-repository-credentials}

Die Documentum-Anmeldedaten werden im AEM Forms-Systemkontext verwendet. Repository-Anmeldeinformationen gelten für bestimmte Repositorys in Documentum. Sie können Anmeldeinformationen für eine beliebige Anzahl von Repositorys angeben. Sie können jedoch nur einen Satz Anmeldeinformationen pro Repository angeben.

### Hinzufügen von Repository-Anmeldedaten {#add-a-repository-credential}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Einstellungen für Repository-Anmeldeinformationen“.
1. Klicken Sie auf Hinzufügen. Die Seite „Documentum-Systemanmeldeinformationen“ wird angezeigt.
1. Geben Sie einen Namen für das Repository ein.
1. Geben Sie einen Benutzernamen und ein Kennwort ein.
1. Klicken Sie auf Speichern.

Wenn der Dienst „Content Repository Connector for EMC Documentum“ und/oder der Repository-Dienst für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen mit dem angegebenen Repository abgeglichen, bevor sie in der Datenbank gespeichert werden. Sind die Anmeldeinformationen ungültig oder nicht vorhanden, wird eine Fehlermeldung angezeigt.

### Entfernen von Repository-Anmeldeinformationen {#remove-a-repository-credential}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Aktivieren Sie das Kontrollkästchen neben dem Repository, von dem die Anmeldeinformationen entfernt werden sollen, und klicken Sie auf „Entfernen“. Die Anmeldeinformationen für das ausgewählte Repository werden aus der Datenbank entfernt.

### Ändern des Benutzernamens und Kennworts für Repository-Anmeldeinformationen {#change-the-user-name-and-password-for-a-repository-credential}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Klicken Sie auf den Namen des Repositorys, für das Anmeldeinformationen bearbeitet werden sollen.
1. Ändern Sie den Benutzernamen oder das Kennwort (oder beides) für das Repository. (Der Repository-Name ist schreibgeschützt.)
1. Klicken Sie auf Speichern.

Wenn der Dienst „Content Repository Connector for EMC Documentum“ und/oder der Repository-Dienst für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen mit dem angegebenen Repository abgeglichen, bevor sie in der Datenbank gespeichert werden. Sind die Anmeldeinformationen ungültig oder nicht vorhanden, wird eine Fehlermeldung angezeigt.

## Aktivieren der Anfrage für die Freigabe von Workspace-Aufgabenwarteschlangen {#enable-the-request-for-sharing-of-workspace-task-queues}

In Workspace sind verschiedene manuelle Schritte erforderlich, um sicherzustellen, dass die Funktion für die Anfrage zur Freigabe von Aufgabenwarteschlangen bei Connector für EMC Documentum ordnungsgemäß funktioniert.

1. Nachdem Sie AEM Forms bereitgestellt und Workbench installiert haben, melden Sie sich bei Workbench an und öffnen Sie die Ansicht „Ressourcen“. In dieser Ansicht stellen Sie fest, wo sich die Datei „QueueSharing.swf“ befindet.
1. Ziehen Sie die Datei „QueueSharing.swf“ aus der Ansicht „Ressourcen“ auf den Windows-Desktop oder an einen vergleichbaren Speicherort (je nach Betriebssystem).
1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Connector für EMC Documentum“ > „Konfigurationseinstellungen“.
1. Ändern Sie unter „Repository Service Provider-Informationen“ den konfigurierten Repository-Provider in „EMC Documentum Repository Provider“.
1. Starten Sie Workbench und kopieren Sie die Datei „QueueSharing.swf“ von dem Speicherort, an den Sie sie ursprünglich kopiert haben (z. B. vom Windows-Desktop), in einen vorhandenen Ordner innerhalb des EMC Documentum-Repositorys.
1. Öffnen Sie in der Workbench-Prozessansicht den Prozess „Queue Sharing“.
1. Öffnen Sie in der Ansicht „Variablen“ die Eigenschaften der Variablen „theForm“ und ändern Sie den URI in den Pfad, unter dem Sie die Datei „QueueSharing.swf“ in Schritt 5 abgelegt haben.
1. Speichern Sie den Prozess.
1. Migrieren Sie den Prozess gemäß den Richtlinien Ihres Unternehmens zur Produktionsumgebung.
