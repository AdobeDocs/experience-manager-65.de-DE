---
title: Konfigurieren des Connectors für EMC Documentum
description: Erfahren Sie, wie Sie den Connector für EMC Documentum konfigurieren, um die Kommunikation zwischen AEM Formularen und EMC Documentum zu aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: a31a496f-87b9-43c0-a98c-5f6ca5d11690
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 11%

---

# Konfigurieren des Connectors für EMC Documentum {#configuring-connector-for-emc-documentum}

Connector für EMC Documentum aktiviert die Kommunikation zwischen AEM Forms und EMC Documentum. Weitere Hintergrundinformationen finden Sie unter „Connectors for ECM“ in der [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

Das Einrichten von Connector für EMC Documentum umfasst das Konfigurieren der Serververbindung und der Repository-Anmeldeinformationen.

>[!NOTE]
>
>In früheren Versionen konnten Assets in einem ECM-Repository gespeichert werden. In der aktuellen Version werden Assets im nativen AEM Forms-Repository gespeichert und die Repository Provider-Dienste werden nicht mehr unterstützt. Die Migration von Assets aus einem ECM-Repository in das AEM Forms-Repository erfolgt bei einer Aktualisierung auf AEM Formulare. Weitere Informationen finden Sie im AEM Forms-Aktualisierungshandbuch für Ihren Anwendungsserver.

## Serververbindung konfigurieren {#configuring-the-server-connection}

Hier werden die Aufgaben für Connector für EMC Documentum beschrieben, die Sie auf der Seite &quot;Konfigurationseinstellungen&quot;ausführen können.

>[!NOTE]
>
>Wenn Sie alle Einstellungen gleichzeitig konfigurieren, müssen Sie nur einmal auf Speichern klicken.

### Server konfigurieren {#configure-the-server}

Sie müssen die Serverinformationen des Verbindungsbrokers konfigurieren. Diese Informationen sind erforderlich, um eine Verbindung zu den Documentum-Inhalts-Repositorys herzustellen und den Connector für EMC Documentum zu starten.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Geben Sie im Bereich &quot;Documentum Configuration Information&quot;den Hostnamen oder die IP-Adresse und die Anschlussnummer des Verbindungsbrokers ein. Die Portnummer muss eine positive Ganzzahl sein (z. B. 1489).
1. Klicken Sie auf Speichern.

### Prinzipalanmeldeinformationen konfigurieren {#configure-principal-credentials}

Beim Konfigurieren der Prinzipal-Anmeldeinformationen hängt der von Ihnen angegebene Repository-Name davon ab, ob bei der Anmeldung ein expliziter Repository-Name angegeben wird.

Wenn Sie einen falschen Benutzernamen oder ein falsches Kennwort eingeben, erhalten Sie die folgenden Ergebnisse, je nachdem, ob der Dienst derzeit ausgeführt wird:

* Wenn der Repository Provider-Dienst für EMC Documentum und der EMC Documentum Content Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen beendet sind, wird kein Fehler angezeigt. Wenn Sie den Dienst jedoch das nächste Mal starten, wird eine Ausnahme ausgelöst und der Dienst wird nicht gestartet.
* Wenn der Repository Provider-Dienst für EMC Documentum oder der EMC Documentum Content Repository Connector-Dienst beim Speichern der Dienstkonfigurationsinformationen gestartet werden, versucht der Dienst sofort, die Anmeldeinformationen zu überprüfen. In diesem Fall tritt ein Fehler auf und die Konfigurationsinformationen werden nicht gespeichert.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Geben Sie im Bereich &quot;Documentum Principal Credentials Information&quot;den Benutzernamen und das Kennwort eines Benutzers mit Superadministrator-Berechtigungen ein.
1. Wenn bei der Anmeldung kein expliziter Repository-Name angegeben wird, geben Sie den Repository-Namen ein, mit dem die Anmeldeinformationen verknüpft sind.
1. Klicken Sie auf Speichern.

### Repository Service Provider ändern {#change-the-repository-service-provider}

Sie können konfigurieren, welcher Repository Service Provider mit Documentum verwendet werden soll. Repository-Dienstaufrufe werden an den konfigurierten Provider delegiert. Die folgenden Optionen sind verfügbar:

**Name des aktuellen Repository Service Providers:** Der Name des aktuellen Repository Service Providers

**ECM Documentum Repository Provider:** Legt den Documentum Repository Provider als Provider des Repositorys fest. Diese Option ist veraltet.

**Repository Provider:** Legt den nativen Repository-Provider als Provider des Repositorys fest.

>[!NOTE]
>
>Um einen Repository Service Provider auszuwählen, der nicht aufgeführt ist, konfigurieren Sie „RepositoryService“ in „Anwendungen und Dienste“ > „Service-Management“. <!-- Fix broken link (See Managing Services) -->

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Wählen Sie im Bereich &quot;Repository Service Provider Information&quot;den alternativen Repository Service Provider aus.
1. Klicken Sie auf Speichern.

## Repository-Anmeldeinformationen konfigurieren {#configuring-repository-credentials}

Die Documentum-Anmeldeinformationen werden im Systemkontext von AEM Forms verwendet. Repository-Anmeldeinformationen gelten für bestimmte Repositorys in Documentum. Sie können Anmeldeinformationen für eine beliebige Anzahl von Repositorys angeben. Sie können jedoch nur einen Satz Anmeldeinformationen pro Repository angeben.

### Repository-Anmeldeinformationen hinzufügen {#add-a-repository-credential}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Einstellungen für Repository-Anmeldeinformationen&quot;.
1. Klicken Sie auf Hinzufügen. Die Seite &quot;Documentum-Systemanmeldeinformationen&quot;wird angezeigt.
1. Geben Sie einen Namen für das Repository ein.
1. Geben Sie einen Benutzernamen und ein Kennwort ein.
1. Klicken Sie auf Speichern.

Wenn der Content Repository Connector für EMC Documentum-Dienst und/oder der Repository Service für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen anhand des angegebenen Repositorys überprüft, bevor sie in der Datenbank gespeichert werden. Wenn die Anmeldeinformationen ungültig sind oder vorhanden sind, wird eine Fehlermeldung angezeigt.

### Repository-Berechtigung entfernen {#remove-a-repository-credential}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Aktivieren Sie das Kontrollkästchen neben dem Repository, aus dem Sie Anmeldeinformationen entfernen möchten, und klicken Sie auf &quot;Entfernen&quot;. Die Anmeldeinformationen für das ausgewählte Repository werden aus der Datenbank entfernt.

### Benutzernamen und Kennwort für Repository-Anmeldeinformationen ändern {#change-the-user-name-and-password-for-a-repository-credential}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Klicken Sie auf den Namen des Repositorys, für das Anmeldeinformationen bearbeitet werden sollen.
1. Ändern Sie den Benutzernamen oder das Kennwort des Repositorys oder beides. (Der Repository-Name ist schreibgeschützt.)
1. Klicken Sie auf Speichern.

Wenn der Content Repository Connector für EMC Documentum-Dienst und/oder der Repository Service für EMC Documentum ausgeführt werden, werden die Anmeldeinformationen anhand des angegebenen Repositorys überprüft, bevor sie in der Datenbank gespeichert werden. Wenn die Anmeldeinformationen ungültig sind oder vorhanden sind, wird eine Fehlermeldung angezeigt.

## Aktivieren der Anforderung für die Freigabe von Workspace-Aufgabenwarteschlangen {#enable-the-request-for-sharing-of-workspace-task-queues}

Es sind einige manuelle Schritte erforderlich, um sicherzustellen, dass die Funktion &quot;Anforderung zur Freigabe der Aufgabenwarteschlange&quot;in Workspace mit Connector für EMC Documentum ordnungsgemäß funktioniert.

1. Nachdem AEM Formulare bereitgestellt und Workbench installiert wurde, melden Sie sich bei Workbench an und öffnen Sie die Ansicht &quot;Resources&quot;. In dieser Ansicht legen Sie fest, wo sich die Datei QueueSharing.swf befindet.
1. Ziehen Sie die Datei QueueSharing.swf aus der Ressourcenansicht auf den Windows-Desktop oder je nach Betriebssystem einen entsprechenden Speicherort.
1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Connector für EMC Documentum&quot;> &quot;Konfigurationseinstellungen&quot;.
1. Ändern Sie unter &quot;Repository Service Provider-Informationen&quot;den konfigurierten Repository-Provider in EMC Documentum Repository Provider.
1. Starten Sie Workbench und kopieren Sie die Datei QueueSharing.swf von dem Speicherort, an den Sie sie ursprünglich kopiert haben (z. B. den Windows-Desktop oder einen anderen Speicherort) in einen vorhandenen Ordner innerhalb des EMC Documentum-Repositorys.
1. Öffnen Sie in der Ansicht &quot;Workbench Processes&quot;den Prozess &quot;Queue Sharing&quot;.
1. Öffnen Sie in der Ansicht &quot;Variables&quot;die Eigenschaften der Variablen &quot;theForm&quot;und ändern Sie den URI so, dass er mit dem Pfad übereinstimmt, in dem Sie die Datei &quot;QueueSharing.swf&quot;in Schritt 5 platziert haben.
1. Speichern Sie den Prozess.
1. Migrieren Sie den Prozess gemäß den Richtlinien Ihres Unternehmens in die Produktionsumgebung.
