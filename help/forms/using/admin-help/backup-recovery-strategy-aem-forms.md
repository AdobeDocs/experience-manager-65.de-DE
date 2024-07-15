---
title: Sicherungs- und Wiederherstellungsstrategie für AEM Forms
description: Erfahren Sie, wie Sie eine Strategie implementieren, um Daten zu sichern und sicherzustellen, dass diese mit den AEM Forms-daten verbleiben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 01ec6ebc-6d80-4417-9604-c8571aebb57e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 100%

---

# Sicherungs- und Wiederherstellungsstrategie für AEM Forms{#backup-and-recovery-strategy-for-aem-forms}

Wenn in Ihrer AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank gespeichert werden, sind Sie dafür verantwortlich, eine Strategie zum Sichern dieser Daten zu implementieren und sicherzustellen, dass diese mit den AEM Forms-Daten synchronisiert bleiben. Außerdem muss die Anwendung so konzipiert sein, dass sie robust genug ist, um ein Szenario zu handhaben, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert werden. Es wird dringend empfohlen, alle Datenbankoperationen im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand zu gewährleisten.

Nachdem Sie ermittelt haben, wie AEM Forms verwendet wird, bestimmen Sie, welche Dateien wie häufig gesichert werden müssen und welches Backup-Fenster verfügbar gemacht werden muss.

>[!NOTE]
>
>Wie auch bei allen anderen Aspekten einer AEM Forms-Implementierung gilt, dass die Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Staging-Umgebung entwickelt und getestet werden muss, bevor sie in der Produktion zum Einsatz kommt. So wird sichergestellt, dass die gesamte Lösung wie erwartet und ohne Datenverlust funktioniert.

Adobe Experience Manager (AEM) ist ein wichtiger Bestandteil von AEM Forms. Daher müssen Sie AEM ebenfalls synchron mit AEM Forms sichern, da Correspondence Management Solution und Dienste wie Forms Manager auf Daten basieren, die im AEM-Teil von AEM Forms gespeichert sind. Um Datenverlust zu vermeiden, müssen die spezifischen AEM Forms-Daten so gesichert werden, dass GDS und AEM (Repository) mit Datenbankverweisen korrelieren. Die Stammordner für Inhalte, Datenbank, GDS und AEM müssen auf einem Computer mit demselben DNS-Namen wie der des Originals wiederhergestellt werden.

## Sicherungsarten {#types-of-backups}

Die AEM Forms-Sicherungsstrategie umfasst zwei Sicherungsarten:

**System-Image:** Ein vollständiges System-Backup, mit dem Sie den Inhalt Ihres Computers wiederherstellen können, wenn die Festplatte oder der gesamte Computer nicht mehr funktioniert. Eine Systemabbildsicherung ist nur vor der Bereitstellung von AEM Forms in der Produktionsumgebung erforderlich. Interne Unternehmensrichtlinien bestimmen anschließend, wie häufig Systemabbildsicherungen erforderlich sind.

**AEM Forms-spezifische Daten:** Anwendungsdaten befinden sich in der Datenbank, in Global Document Storage (GDS) sowie dem AEM-Repository und müssen in Echtzeit gesichert werden. Der globale Dokumentenspeicher ist ein Verzeichnis zum Speichern von dauerhaft in einem Prozess genutzten Dateien. Diese Dateien können PDFs, Richtlinien und Formularvorlagen beinhalten.

>[!NOTE]
>
>Wenn Content Services (nicht mehr unterstützt) installiert ist, sichern Sie auch das Stammverzeichnis für den Content-Speicher. Siehe [Stammordner für Inhalte (nur Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

In der Datenbank werden Formularartefakte, Dienstkonfigurationen, Prozesszustände und Datenbankverweise auf Dateien im globalen Dokumentenspeicher gespeichert. Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, werden permanente Daten und Dokumente im globalen Dokumentenspeicher ebenfalls in der Datenbank gespeichert. Die Datenbank kann mithilfe der folgenden Methoden gesichert und wiederhergestellt werden:

* **Snapshot-Sicherungsmodus** gibt an, dass sich das AEM Forms-System entweder für unbegrenzte Zeit oder für eine angegebene Anzahl von Minuten im Sicherungsmodus befindet, nach deren Ablauf der Sicherungsmodus nicht mehr aktiv ist. Sie können anhand der folgenden Optionen den Snapshot-Sicherungsmodus starten bzw. beenden. Nach einem Wiederherstellungsszenario darf der Snapshot-Sicherungsmodus nicht aktiviert werden.

   * Verwenden Sie die Seite „Sicherungseinstellungen“ in der Administrationskonsole. Um in den Snapshot-Modus zu wechseln, wählen Sie das Kontrollkästchen „Im abgesicherten Sicherungsmodus arbeiten“ aus. Deaktivieren Sie das Kontrollkästchen, um den Snapshot-Modus zu beenden.
   * Verwenden Sie das LCBackupMode-Skript (siehe [Sichern der Stammordner für Datenbank, globalen Dokumentenspeicher und Inhalte](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Zum Beenden des Snapshot-Sicherungsmodus legen Sie im Skriptargument den `continuousCoverage`-Parameter auf `false` fest oder verwenden Sie die Option `leaveContinuousCoverage`.
   * Verwenden Sie die bereitgestellte Backup-/Wiederherstellungs-API. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* Der **kontinuierliche Sicherungsmodus** gibt an, dass das System stets im Sicherungsmodus ist, wobei eine neue Sicherungsmodussitzung ausgelöst wird, sobald die vorherige Sitzung freigegeben wurde. Beim kontinuierlichen Sicherungsmodus gibt es kein Zeit-Limit. Wenn das bereitgestellte LCBackupMode-Skript oder APIs aufgerufen werden, um den kontinuierlichen Sicherungsmodus zu beenden, wird eine neue kontinuierliche Sicherungsmodussitzung gestartet. Dieser Modus eignet sich zur Unterstützung kontinuierlicher Sicherungen und ermöglicht zugleich das Entfernen alter und nicht benötigter Dokumente aus dem Verzeichnis des globalen Dokumentenspeichers. Der kontinuierliche Sicherungsmodus wird nicht über die Seite „Sicherung und Wiederherstellung“ unterstützt. Nach einem Wiederherstellungsszenario ist der kontinuierliche Sicherungsmodus weiter aktiv. Sie können den kontinuierlichen Sicherungsmodus mithilfe des bereitgestellten LCBackupMode-Skripts mit der Option `leaveContinuousCoverage` deaktivieren.

>[!NOTE]
>
>Durch Beenden des kontinuierlichen Sicherungsmodus wird unmittelbar eine neue Sicherungsmodussitzung ausgelöst. Wenn Sie den kontinuierlichen Sicherungsmodus vollständig deaktivieren möchten, verwenden Sie die Option `leaveContinuousCoverage` im Skript. Damit wird die vorhandene Sicherungssitzung überschrieben. Im Snapshot-Sicherungsmodus können Sie den Sicherungsmodus wie gewohnt beenden.

Zum Vermeiden von Datenverlusten müssen die spezifischen AEM Forms-Daten so gesichert werden, dass Dokumente im Stammordner für Inhalte und globalen Dokumentenspeicher in Korrelation zu Datenbankverweisen stehen.

>[!NOTE]
>
>Wenn der globale Dokumentspeicher im Dateisystem und nicht in der Datenbank gespeichert wird, führen Sie die Datenbanksicherung vor der Sicherung des globalen Dokumentspeichers durch.

## Weitere Informationen zur Sicherung und Wiederherstellung {#special-considerations-for-backup-and-recovery}

Nutzen Sie die folgenden Richtlinien, wenn Sie AEM Forms aufgrund der folgenden Änderungen in einer anderen Umgebung wiederherstellen müssen:

* Änderungen der IP-Adresse oder des Host-Namens oder Ports vom AEM Forms-Server
* Änderung der Laufwerksbuchstaben oder des Verzeichnispfads
* Wechsel zu einem anderen Datenbank-Host, Port oder Namen

In der Regel werden solche Wiederherstellungsszenarien durch Hardware-Fehler des Servers verursacht, der als Host für den Anwendungs-Server, Datenbank-Server oder Formular-Server dient. Zusätzlich zu den spezifischen Konfigurationen von AEM-Formularen, die in diesem Abschnitt beschrieben werden, sollten Sie außerdem die notwendigen Änderungen für andere Teile der Bereitstellung von AEM-Formularen vornehmen, z. B. Lastenausgleich und Firewalls, wenn sich der Host-Name oder die IP-Adresse eines AEM-Formular-Servers ändert.

### Was nicht änderbar ist {#what-cannot-be-changed}

Sie können zwar den Datenbank-Server und viele andere Parameter ändern, nicht jedoch den Typ des Anwendungs-Servers und der Datenbank, wenn Sie AEM Forms aus einem Backup wiederherstellen. Wenn Sie beispielsweise ein Backup von AEM Forms wiederherstellen, können Sie den Anwendungs-Server nicht von JBoss in WebLogic oder die Datenbank von Oracle in DB2 ändern. Zusätzlich müssen wiederhergestellte AEM-Formulare dieselben Dateisystempfade, z. B. den Ordner für Schriftarten, verwenden.

### Neustarten nach einer Wiederherstellung {#restarting-after-a-recovery}

Bevor Sie den Formular-Server nach einer Wiederherstellung neu starten, führen Sie folgende Schritte aus:

1. Starten Sie das System im Wartungsmodus.
1. Führen Sie folgende Schritte aus, um sicherzustellen, dass Forms Manager im Wartungsmodus mit AEM Forms synchronisiert wird:

   1. Gehen Sie zu https://&lt;*server*>:&lt;*port*>/lc/fm und melden Sie sich mit Ihren Administrator-/Passwort-Anmeldeinformationen an.
   1. Klicken Sie rechts oben auf den Namen der Person (in diesem Fall „Super Administrator“).
   1. Klicken Sie auf **Admin-Optionen**.
   1. Klicken Sie auf **Starten**, um Elemente im Repository zu synchronisieren.

1. In einer Cluster-Umgebung sollte der primäre Knoten (in Bezug auf AEM) vor den sekundären Knoten in Betrieb sein.
1. Stellen Sie sicher, dass keine Prozesse aus internen oder externen Quellen, z. B. dem Internet, SOAP oder EJB-Prozessinitiatoren, initiiert werden, bis der normale Betrieb des Systems überprüft wurde.

Wenn die AEM Forms-Hauptdatenbank verschoben oder geändert wird, lesen Sie die entsprechenden Installationshandbücher für Ihren Anwendungs-Server, um Informationen zur Aktualisierung der Datenbankverbindungsinformationen für die AEM Forms-Datenquellen IDP_DS und EDC_DS zu finden.

>[!NOTE]
> 
> Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

### Ändern des AEM Forms-Host-Namen oder der IP-Adresse {#changing-the-aem-forms-hostname-or-ip-address}

In einem Cluster müssen Sie die Cache-Locator-Konfiguration aktualisieren, wenn Sie TCP-Caching anstelle von UDP verwenden. Siehe „Konfigurieren des Caching-Locators (nur Caching unter Verwendung von TCP)“ im Konfigurationshandbuch für Ihren Anwendungs-Server.

### Ändern von Dateisystempfaden für AEM Forms-Knoten {#changing-the-aem-forms-node-file-system-paths}

Wenn Sie die Dateisystempfade für einen eigenständigen Knoten ändern, müssen Sie die entsprechenden Referenzen in den Voreinstellungen, anderen Systemkonfigurationen, benutzerdefinierten Anwendungen und bereitgestellten AEM Forms-Anwendungen aktualisieren. Andererseits müssen für ein Cluster alle Knoten dieselbe Dateisystempfad-Konfiguration verwenden. Legen Sie das Stammverzeichnis des globalen Dokumentenspeichers (GDS) fest und stellen Sie sicher, dass er auf eine Kopie des wiederhergestellten GDS verweist, die mit der wiederhergestellten Datenbank synchronisiert ist. Das Festlegen des GDS-Pfades ist wichtig, da der GDS Daten enthalten kann, die beim Neustart von Anwendungs-Servern bestehen bleiben sollen.

In einer Cluster-Umgebung muss die Dateisystempfad-Konfiguration des Repositorys für alle Cluster-Knoten vor der Sicherung und nach der Wiederherstellung gleich sein.

Verwenden Sie das `LCSetGDS`-Skript im Ordner `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline`, um den GDS-Pfad festzulegen, nachdem Sie die Datei-System-Pfade geändert haben. Einzelheiten finden Sie in der `ReadMe.txt`-Datei im selben Ordner. Wenn der alte GDS-Ordnerpfad nicht verwendet werden kann, muss das `LCSetGDS`-Skript verwendet werden, um den neuen Pfad für den GDS festzulegen, bevor Sie AEM Forms starten.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem dieses Skript zum Ändern des Speicherorts für den Ordner des globalen Dokumentenspeichers verwendet werden sollte. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Starten Sie den Formular-Server nach dem Festlegen des GDS-Pfades im Wartungsmodus und verwenden Sie die Administrationskonsole, um die verbleibenden Dateisystempfade für den neuen Knoten zu aktualisieren. Wenn Sie sich vergewissert haben, dass alle notwendigen Konfigurationen aktualisiert sind, starten Sie AEM Forms neu und testen Sie die Anwendung.
