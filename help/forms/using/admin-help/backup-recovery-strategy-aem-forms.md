---
title: Sicherungs- und Wiederherstellungsstrategie für AEM Forms
seo-title: Sicherungs- und Wiederherstellungsstrategie für AEM Forms
description: Erfahren Sie, wie Sie eine Strategie implementieren, um Daten zu sichern und sicherzustellen, dass diese mit den AEM-Formdaten verbleiben.
seo-description: Erfahren Sie, wie Sie eine Strategie implementieren, um Daten zu sichern und sicherzustellen, dass diese mit den AEM-Formdaten verbleiben.
uuid: 98fc3115-76e5-4e58-aa30-3601866a441f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f192a8a3-1116-4d32-9b57-b53d532c0dbf
exl-id: 01ec6ebc-6d80-4417-9604-c8571aebb57e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 93%

---

# Sicherungs- und Wiederherstellungsstrategie für AEM Forms{#backup-and-recovery-strategy-for-aem-forms}

Wenn in Ihrer AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank gespeichert werden, sind Sie dafür verantwortlich, eine Strategie zum Sichern dieser Daten zu implementieren und sicherzustellen, dass diese mit den AEM Forms-Daten synchronisiert bleiben. Darüber hinaus muss die Anwendung so ausgelegt sein, dass sie robust genug ist, um in einem Szenario zu funktionieren, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert sind. Es wird dringend empfohlen, alle Datenbankvorgänge im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand aufrechtzuerhalten.

Nachdem Sie ermittelt haben, wie AEM Forms verwendet wird, bestimmen Sie, welche Dateien wie häufig gesichert werden müssen und welches Sicherungszeitfenster verfügbar gemacht werden muss.

>[!NOTE]
>
>Wie es auch bei allen anderen Aspekten Ihrer AEM Forms-Implementierung der Fall ist, muss Ihre Sicherungs- und Wiederherstellungsstrategie in einer Entwicklungs- oder Testumgebung entwickelt und getestet werden, bevor sie in der Produktion zum Einsatz kommt. So wird sichergestellt, dass die gesamte Lösung wie erwartet und ohne Datenverlust funktioniert.

Adobe Experience Manager (AEM) ist ein wichtiger Bestandteil von AEM Forms. Daher müssen Sie AEM mit der AEM Forms-Sicherung ebenso synchronisieren wie Correspondence Management Solution und Dienste, wie beispielsweise Forms Manager, die auf im AEM-Teil von AEM Forms gespeicherten Daten basieren. Um Datenverlust vorzubeugen, müssen die AEM Forms-spezifischen Daten so gesichert werden, dass GDS und AEM (Repository) mit Datenbankverweisen übereinstimmen. Die Datenbank, GDS, AEM und die Stammordner für Inhalte müssen auf einem Computer mit denselben DNS-Namen wie das Original wiederhergestellt werden.

## Sicherungsarten {#types-of-backups}

Die AEM Forms-Sicherungsstrategie umfasst zwei Sicherungsarten:

**Systemabbild:** Eine vollständige Systemsicherung, mit der Sie den Inhalt Ihres Computers wiederherstellen können, wenn die Festplatte oder der gesamte Computer nicht mehr funktioniert. Eine Systemabbildsicherung ist nur vor der Bereitstellung von AEM Forms in der Produktionsumgebung erforderlich. Interne Unternehmensrichtlinien bestimmen anschließend, wie häufig Systemabbildsicherungen erforderlich sind.

**AEM formularspezifische Daten:** Anwendungsdaten sind in der Datenbank, dem globalen Dokumentenspeicher (GDS) und AEM Repository vorhanden und müssen in Echtzeit gesichert werden. Der globale Dokumentenspeicher ist ein Ordner zum Speichern dauerhaft in einem Prozess genutzter Dateien. Diese Dateien können PDFs, Richtlinien und Formularvorlagen beinhalten.

>[!NOTE]
>
>Wenn Content Services (nicht mehr unterstützt) installiert ist, sichern Sie auch das Stammordner für Inhalte. Siehe [Stammordner für Inhalte (nur Content Services)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

In der Datenbank werden Formularartefakte, Dienstkonfigurationen, Prozesszustände und Datenbankverweise auf Dateien im globalen Dokumentenspeicher gespeichert. Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, werden permanente Daten und Dokumente im globalen Dokumentenspeicher ebenfalls in der Datenbank gespeichert. Die Datenbank kann mithilfe der folgenden Methoden gesichert und wiederhergestellt werden:

* **Snapshot-Sicherungsmodus** gibt an, dass sich das AEM Forms-System entweder für unbegrenzte Zeit oder für eine angegebene Anzahl von Minuten im Sicherungsmodus befindet, nach deren Ablauf der Sicherungsmodus nicht mehr aktiv ist. Um den Snapshot-Sicherungsmodus zu starten bzw. zu beenden, können Sie die folgenden Optionen verwenden. Nach einem Wiederherstellungsszenario darf der Snapshot-Sicherungsmodus nicht aktiviert werden.

   * Verwenden Sie die Seite „Sicherungseinstellungen“ in Administration Console. Um in den Snapshot-Modus zu wechseln, aktivieren Sie das Kontrollkästchen „Im abgesicherten Sicherungsmodus arbeiten“. Deaktivieren Sie das Kontrollkästchen, um den Snapshot-Modus zu beenden.
   * Verwenden Sie das LCBackupMode-Skript (siehe [Die Datenbank, den Ordner des globalen Dokumentenspeichers sowie den Stammordner für Inhalte sichern](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Zum Beenden des Snapshot-Sicherungsmodus legen Sie im Skriptargument den `continuousCoverage`-Parameter auf `false` fest oder verwenden Sie die Option `leaveContinuousCoverage`.
   * Verwenden Sie die bereitgestellte Sicherungs-/Wiederherstellungs-API. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **Der kontinuierliche Sicherungsmodus** gibt an, dass das System stets im Sicherungsmodus ist, wobei eine neue Sicherungsmodussitzung ausgelöst wird, sobald die vorherige Sitzung freigegeben wurde. Beim kontinuierlichen Sicherungsmodus gibt es kein Zeitlimit. Wenn das bereitgestellte LCBackupMode-Skript oder die APIs aufgerufen werden, um den kontinuierlichen Sicherungsmodus zu beenden, wird eine neue kontinuierliche Sicherungsmodussitzung gestartet. Dieser Modus eignet sich zur Unterstützung fortlaufender Sicherungen und ermöglicht zugleich das Entfernen alter und nicht benötigter Dokumente aus dem globalen Dokumentenspeicher. Der kontinuierliche Sicherungsmodus wird nicht über die Seite „Sicherung und Wiederherstellung“ unterstützt. Nach einem Wiederherstellungsszenario ist der kontinuierliche Sicherungsmodus weiter aktiv. Sie können den kontinuierlichen Sicherungsmodus mithilfe des bereitgestellten LCBackupMode-Skripts mit der Option `leaveContinuousCoverage` deaktivieren.

>[!NOTE]
>
>Durch Beenden des kontinuierlichen Sicherungsmodus wird unmittelbar eine neue Sicherungsmodussitzung ausgelöst. Wenn Sie den kontinuierlichen Sicherungsmodus vollständig deaktivieren möchten, verwenden Sie die Option `leaveContinuousCoverage` im Skript. Damit wird die vorhandene Sicherungssitzung überschrieben. Im Snapshot-Modus können Sie den Sicherungsmodus wie gewohnt beenden.

Zum Vermeiden von Datenverlusten müssen die AEM Forms-spezifischen Daten so gesichert werden, dass Dokumente im Ordner des globalen Dokumentenspeichers und im Stammordner für Inhalte in Korrelation zu Datenbankverweisen stehen.

>[!NOTE]
>
>Wenn der globale Dokumentspeicher im Dateisystem und nicht in der Datenbank gespeichert wird, führen Sie die Datenbanksicherung vor der Sicherung des globalen Dokumentspeichers durch.

## Besondere Überlegungen zur Sicherung und Wiederherstellung  {#special-considerations-for-backup-and-recovery}

Verwenden Sie die folgenden Richtlinien, wenn Sie AEM Forms in einer anderen Umgebung aufgrund der folgenden Änderungen wiederherstellen müssen:

* Änderungen der IP-Adresse, des Hostnamens oder Anschlusses des AEM Forms-Servers
* Änderungen des Laufwerkbuchstabens oder Ordnerpfades
* Änderungen an einem anderen Datenbankhost, Anschluss oder Namen

In der Regel werden solche Szenarien durch Hardwarefehler des Servers, der als Host für den Anwendungsserver, Datenbankserver oder Formularserver dient, verursacht. Zusätzlich zu den AEM Forms-spezifischen Konfigurationen, die in diesem Abschnitt beschrieben werden, sollten Sie außerdem die notwendigen Änderungen für andere Teile der AEM Forms-Bereitstellung, z. B. Lastenausgleich und Firewalls, vornehmen, wenn sich der Hostname oder die IP-Adresse eines AEM Forms-Servers ändert.

### Was nicht änderbar ist  {#what-cannot-be-changed}

Sie können zwar den Datenbankserver und viele andere Parameter ändern, nicht jedoch den Typ des Anwendungsservers und der Datenbank, wenn Sie AEM Forms aus einer Sicherung wiederherstellen. Wenn Sie beispielsweise eine AEM Forms-Sicherung wiederherstellen, können Sie nicht den Anwendungsserver von JBoss in WebLogic oder die Datenbank von Oracle in DB2 ändern. Zusätzlich muss das wiederhergestellte AEM Forms dieselben Dateisystempfade, z. B. den Ordner für Schriftarten, verwenden.

### Neustart nach einer Wiederherstellung  {#restarting-after-a-recovery}

Bevor Sie den Formularserver nach einer Wiederherstellung neu starten, führen Sie folgende Schritte aus:

1. Starten Sie das System im Wartungsmodus.
1. Führen Sie folgende Schritte aus, um sicherzustellen, dass Forms Manager im Wartungsmodus mit AEM Forms synchronisiert wird:

   1. Wechseln Sie zu https://&lt;*server*:&lt;*port*/lc/fm und melden Sie sich mit den Anmeldeinformationen von adminstrator/password an.
   1. Klicken Sie rechts oben auf den Namen des Benutzers (in diesem Fall „Super Administrator“).
   1. Klicken Sie auf **Admin-Optionen**.
   1. Klicken Sie auf **Start**, um Elemente im Repository zu synchronisieren.

1. In einer Clusterumgebung sollte sich der primäre Knoten (in Bezug auf AEM) vor den sekundären Knoten befinden.
1. Stellen Sie sicher, dass keine Prozesse aus internen oder externen Quellen, z. B. dem Internet, SOAP oder EJB-Prozessinitiatoren, initiiert werden, bis der normale Betrieb des Systems überprüft wurde.

Wenn die AEM Forms-Hauptdatenbank verschoben oder geändert wird, lesen Sie die entsprechenden Installationshandbücher für Ihren Anwendungsserver, um Informationen zur Aktualisierung der Datenbankverbindungsinformationen für die AEM Forms-Datenquellen IDP_DS und EDC_DS zu finden.

### AEM Forms-Hostnamen oder IP-Adresse ändern  {#changing-the-aem-forms-hostname-or-ip-address}

In einem Cluster müssen Sie die Cache-Locator-Konfiguration aktualisieren, wenn Sie TCP-Zwischenspeicherung anstelle von UDP verwenden. Siehe „Konfigurieren des Zwischenspeicherungs-Locators (nur Zwischenspeicherung unter Verwendung von TCP)“ im Konfigurationshandbuch für Ihren Anwendungsserver.

### AEM Forms-Knotendatei-Systempfade ändern  {#changing-the-aem-forms-node-file-system-paths}

Wenn Sie die Dateisystempfade für einen eigenständigen Knoten ändern, müssen Sie die entsprechenden Referenzen in Voreinstellungen, anderen Systemkonfigurationen, benutzerdefinierten Anwendungen und bereitgestellten AEM Forms-Anwendungen aktualisieren. Andererseits müssen für ein Cluster alle Knoten dieselbe Dateisystempfad-Konfiguration verwenden. Sie müssen den Ordner des globalen Dokumentenspeichers (GDS) festlegen und sicherstellen, dass es auf eine Kopie des wiederhergestellten GDS verweist, die mit der wiederhergestellten Datenbank synchronisiert ist. Das Festlegen des GDS-Pfades ist wichtig, da der GDS Daten enthalten kann, die beim Neustart von Anwendungsservern bestehen bleiben sollen.

In einer Clusterumgebung muss die Konfiguration des Dateisystempfads des Repositorys für alle Clusterknoten vor der Sicherung und nach der Wiederherstellung gleich sein.

Verwenden Sie das Skript `LCSetGDS`im Ordner `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` , um den GDS-Pfad festzulegen, nachdem Sie die Dateisystempfade geändert haben. Einzelheiten finden Sie in der `ReadMe.txt`-Datei im selben Ordner. Wenn der alte GDS-Ordnerpfad nicht verwendet werden kann, muss das `LCSetGDS`-Skript verwendet werden, um den neuen Pfad für den GDS festzulegen, bevor Sie AEM Forms starten.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem dieses Skript zum Ändern des Speicherorts für den Ordner des globalen Dokumentenspeichers verwendet werden sollte. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) *

Nach dem Festlegen des GDS-Pfades starten Sie den Formularserver im Wartungsmodus und verwenden Sie Administration Console, um die verbleibenden Dateisystempfade für den neuen Knoten zu aktualisieren. Wenn Sie sich vergewissert haben, dass alle notwendigen Konfigurationen aktualisiert sind, starten Sie AEM Forms neu und testen Sie die Anwendung.
