---
title: Allgemeine AEM Forms-Einstellungen
seo-title: General AEM Forms settings
description: Erfahren Sie, wie Sie die Einstellungen der Seite "Core-Konfigurationen"in Administration Console konfigurieren, um die Systemleistung zu verbessern.
seo-description: Learn to configure the Core Configurations page settings in administration console that can help improve system performance.
uuid: 940680fd-b7ab-4376-aa5b-e139223522ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bd648c38-731b-420e-973d-a4728b69868e
exl-id: e1519477-b5a8-4947-8597-26b945a3b819
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 31%

---

# Allgemeine AEM Forms-Einstellungen {#general-aem-forms-settings}

Die Seite &quot;Core-Konfigurationen&quot;in Administration Console enthält Einstellungen, die zur Verbesserung der Systemleistung beitragen können. Nachdem Sie diese Einstellungen konfiguriert oder aktualisiert haben, starten Sie den Anwendungsserver neu.

Informationen zum Aktivieren des abgesicherten Sicherungsmodus finden Sie unter [Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus](/help/forms/using/admin-help/enabling-disabling-safe-backup-mode.md#enabling-and-disabling-safe-backup-mode).


>[!NOTE]
>
>Die Dateien im temporären Ordner und die dauerhaft genutzten Dokumente im Stammordner des globalen Dokumentenspeichers (GDS) können vertrauliche Benutzerinformationen enthalten, z. B. Informationen, für die spezielle Berechtigungen erforderlich sind, wenn der Zugriff über die APIs oder Benutzeroberflächen erfolgt. Daher ist es wichtig, dass dieser Ordner mit allen verfügbaren Methoden ordnungsgemäß gesichert wird. Es wird empfohlen, dass nur das Betriebssystemkonto, das zum Ausführen des Anwendungsservers verwendet wird, Lese- und Schreibzugriff auf diesen Ordner hat.


1. Klicken Sie in der Administrationskonsole auf **[!UICONTROL „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“]**.
1. Ändern Sie auf der Seite „Core-Konfigurationen“ die folgenden Einstellungen nach Bedarf und klicken Sie auf **[!UICONTROL OK]**. Weitere Informationen zu den Optionen finden Sie unter [Optionen für zentrale Konfigurationen](configure-general-aem-forms-settings.md#core-configurations-options).


## Optionen für zentrale Konfigurationen {#core-configurations-options}

**Speicherort des temporären Ordners** Der Ordnerpfad, in dem AEM Forms temporäre Produktdateien erstellt. Wenn der Wert dieser Einstellung leer ist, wird als Speicherort standardmäßig der temporäre Ordner des Systems verwendet. Stellen Sie sicher, dass der temporäre Ordner ein beschreibbarer Ordner ist.

>[!NOTE]
>
>Stellen Sie sicher, dass sich der temporäre Ordner im lokalen Dateisystem befindet. AEM Forms unterstützt keine temporären Ordner an einem Remote-Speicherort.

**Stammordner des globalen Dokumentenspeichers** Der Stammordner des globalen Dokumentenspeichers (GDS) wird für folgende Zwecke verwendet:

* Speichern langlebiger Dokumente. Dauerhaft genutzte Dokumente haben keine Ablaufzeit und bleiben bestehen, bis sie entfernt werden (z. B. die in einem Workflow-Prozess verwendeten PDF-Dateien). Die langlebigen Dokumente sind ein wichtiger Teil des Gesamtzustands des Systems. Wenn einige oder alle dieser Dokumente verloren gehen oder beschädigt sind, kann der Forms-Server instabil werden. Daher ist es wichtig, dass dieser Ordner auf einem RAID-Gerät gespeichert wird.
* Speichern temporärer Dokumente, die während der Verarbeitung benötigt werden.

>[!NOTE]
>
>Sie können auch die Dokumentenspeicherung in der AEM Formulardatenbank aktivieren. Die Systemleistung ist jedoch besser, wenn Sie den globalen Dokumentenspeicher verwenden.

* Übertragen von Dokumenten zwischen Knoten in einem Cluster. Wenn Sie AEM Formulare in einer Clusterumgebung ausführen, muss auf diesen Ordner von allen Knoten im Cluster zugegriffen werden können.
* Empfangen eingehender Parameter über Remote-API-Aufrufe.

Wenn Sie keinen Ordner des globalen Dokumentenspeichers angeben, wird standardmäßig der Ordner des Anwendungsservers verwendet:

* `[JBOSS_HOME]/server/<server>/svcnative/DocumentStorage`
* `[WEBSPHERE_HOME]/installedApps/adobe/'server'/DocumentStorage`
* `[WEBLOGIC_HOME]/user_projects/<domain>/'server'/adobe/AEMformsserver/DocumentStorage`

>[!NOTE]
>
>Das Ändern des Werts der Einstellung für den Stammordner des globalen Dokumentenspeichers sollte mit besonderer Sorgfalt erfolgen. Der Ordner des globalen Dokumentenspeichers wird verwendet, um sowohl in einem Prozess verwendete dauerhaft genutzte Dateien als auch kritische AEM Formularkomponenten zu speichern. Das Ändern des Speicherorts des Ordners des globalen Dokumentenspeichers ist eine wesentliche Systemänderung. Wenn Sie den Speicherort des Ordners des globalen Dokumentenspeichers falsch konfigurieren, sind AEM Formulare nicht mehr funktionsfähig und erfordern möglicherweise eine vollständige Neuinstallation AEM Formulare. Wenn Sie einen neuen Speicherort für den Ordner des globalen Dokumentenspeichers angeben, muss der Anwendungsserver heruntergefahren und die Daten migriert werden, bevor der Server neu gestartet werden kann. Der Systemadministrator muss alle Dateien vom alten Speicherort an den neuen Speicherort verschieben, aber die interne Ordnerstruktur beibehalten.

>[!NOTE]
>
>Geben Sie für den temporären Ordner („temp“) und den GDS-Ordner nicht denselben Ordner an..

Zusätzliche Informationen zum GDS-Ordner finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver).](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)

**Speicherort des Ordners für Adobe Server-Schriftarten** Geben Sie den Pfad zu dem Ordner ein, der die Adobe-Server-Schriftarten enthält. Diese Schriftarten werden mit AEM Forms installiert. Der Standardspeicherort dieser Schriftarten ist der Ordner [aem-forms root]/fonts. Wenn auf diesen Ordner nicht zugegriffen werden kann, können Sie die Schriftarten an einen anderen Speicherort kopieren und über diese Einstellung den neuen Speicherort angeben.

**Speicherort des Ordners für Kundenschriftarten** Geben Sie den Pfad zu einem Ordner ein, der zusätzliche Schriftarten enthält, die Sie verwenden möchten.

***Hinweis **: Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.*

**Speicherort des Ordners für Systemschriftarten** Geben Sie den Pfad zu dem von Ihrem Betriebssystem vorgegebenen Schriftartenordner ein. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.

**Speicherort der Data Service-Konfigurationsdatei** Gibt den Speicherort der Datei „services-config.xml“ an. Diese Datei ist standardmäßig in die Datei „adobe-core-appserver.ear“ eingebettet und für Benutzer nicht zugänglich. Eine Kopie der standardmäßigen Datei services-config.xml befindet sich in [AEM-Forms-Stamm]\sdk\misc\DataServices\Server-Configuration Wenn Sie diese Datei geändert und verschoben haben, geben Sie den neuen Speicherort in dieses Feld ein.

Die Konfigurationsdatei für Data Services ermöglicht die Anpassung der Data Services-Einstellungen, z. B. Authentifizierungstyp und Debug-Ausgabe.

Diese Einstellung ist standardmäßig leer.

**Standardmäßige Maximalgröße für Inline-Dokumente (Byte)**: Die maximale Anzahl von Bytes, die im Speicher beibehalten werden, wenn Dokumente zwischen verschiedenen AEM Forms-Komponenten übergeben werden. Verwenden Sie diese Einstellung zur Leistungsoptimierung. Dokumente, die kleiner als diese Zahl sind, werden im Speicher gespeichert und bleiben in der Datenbank erhalten. Dokumente, die diesen Maximalwert überschreiten, werden auf der Festplatte gespeichert.

Diese Einstellung ist obligatorisch. Der Standardwert ist 65536 Byte.

**Standard-Zeitsperre für Entsorgung (Sekunden)**: Die maximale Zeit in Sekunden, während der ein Dokument, das zwischen verschiedenen AEM Forms-Komponenten weitergeleitet wird, als aktiv angesehen wird. Nach Ablauf dieser Zeit können Dateien, die zum Speichern dieses Dokuments verwendet werden, entfernt werden. Verwenden Sie diese Einstellung, um die Auslastung des Festplattenspeichers zu steuern.

Diese Einstellung ist obligatorisch. Der Standardwert ist 600 Sekunden.

**Sweep-Intervall für Dokumente (Sekunden)**: Die Zeit in Sekunden, die zwischen zwei Versuchen vergehen soll, Dateien zu löschen, die nicht mehr benötigt werden und zuvor zum Weiterleiten der Dokumentdaten zwischen Services verwendet wurden.

Diese Einstellung ist obligatorisch. Der Standardwert ist 30 Sekunden.

**FIPS aktivieren**: Wählen Sie diese Option zum Aktivieren des FIPS-Modus. FIPS 140-2 (Federal Information Processing Standard) ist ein von der US-Regierung definierter Verschlüsselungsstandard. Bei Ausführung im FIPS-Modus beschränkt AEM Forms den Datenschutz auf gemäß FIPS 140-2 zugelassene Algorithmen, indem das Verschlüsselungsmodul RSA BSAFE Crypto-C 2.1 verwendet wird.

Der FIPS-Modus unterstützt keine Verschlüsselungsalgorithmen, die in Adobe Acrobat®-Versionen vor 7.0 verwendet werden. Wenn der FIPS-Modus aktiviert ist und Sie den Encryption-Dienst zum Verschlüsseln des PDF mit einem Kennwort verwenden, dessen Kompatibilitätsstufe auf Acrobat 5 festgelegt ist, schlägt der Verschlüsselungsversuch mit einem Fehler fehl.

Im Allgemeinen wendet der Assembler-Dienst bei aktiviertem FIPS keine Kennwortverschlüsselung auf Dokumente an. Wenn dies versucht wird, wird eine FIPSModeException-Ausnahme ausgelöst, die angibt, dass &quot;Kennwortverschlüsselung im FIPS-Modus nicht zulässig ist&quot;. Darüber hinaus wird das Element Document Description XML (DDX) PDFsFromBookmarks im FIPS-Modus nicht unterstützt, wenn das Basisdokument kennwortverschlüsselt ist.

>[!NOTE]
>
>AEM Forms-Software überprüft keinen Code, um die FIPS-Kompatibilität sicherzustellen. Es bietet einen FIPS-Betriebsmodus, sodass FIPS-zugelassene Algorithmen für kryptografische Dienste aus den FIPS-zugelassenen Bibliotheken (RSA) verwendet werden.

**WSDL aktivieren**: Wählen Sie diese Option, um die WSDL-Generierung (Web Service Definition Language) für alle Services zu aktivieren, die Teil von AEM Forms sind.

Aktivieren Sie diese Option in Entwicklungsumgebungen, in denen Entwickler die WSDL-Generierung zum Erstellen ihrer Clientanwendungen verwenden. Sie können die WSDL-Generierung in einer Produktionsumgebung deaktivieren, um zu vermeiden, dass interne Details eines Dienstes offen gelegt werden.

**Dokumentenspeicher in der Datenbank aktivieren**: Wählen Sie diese Option, um dauerhaft genutzte Dokumente in der AEM Forms-Datenbank zu speichern. Durch Aktivierung dieser Option wird kein Ordner des globalen Dokumentenspeichers benötigt. Die Auswahl dieser Option vereinfacht jedoch AEM Formulare-Sicherungen. Wenn Sie nur den globalen Dokumentenspeicher verwenden, umfasst eine Sicherung die Aktivierung des AEM Forms AEM Forms-Systems in den Sicherungsmodus. Anschließend erfolgt die Sicherung der Datenbank und des globalen Dokumentenspeichers. Wenn Sie die Datenbankoption auswählen, umfasst die Sicherung das Abschließen der Datenbanksicherung für eine neue Installation oder das Abschließen der Datenbanksicherung sowie die einmalige Sicherung des globalen Dokumentenspeichers für eine Aktualisierung. Möglicherweise ist eine zusätzliche Verwaltung Ihrer Datenbank erforderlich, um Aufträge und Daten im Vergleich zu einer Konfiguration des globalen Dokumentenspeichers zu bereinigen. (Siehe Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird.)

**DSC-Aufrufstatistik aktivieren**: Wenn diese Option ausgewählt ist, verfolgt AEM Forms Aufrufstatistiken, z. B. die Anzahl der Aufrufe, die für das Aufrufen erforderliche Zeit und die Anzahl der Fehler in den Aufrufen. Diese Informationen werden in einem JMX-Bean gespeichert, sodass Sie die Java™ JConsole oder die Software von Drittanbietern verwenden können, um die Statistiken anzuzeigen. Wenn diese Statistiken nicht angezeigt werden sollen, deaktivieren Sie diese Option, um die Leistung AEM Formulare zu verbessern.

**RDS aktivieren**: Durch die Auswahl dieser Option wird das Remote Development Services (RDS)-Servlet in AEM Forms aktiviert. Wenn diese Option aktiviert ist, können clientseitige Tools mit Data Services interagieren, um beispielsweise Modelle bereitzustellen oder die Bereitstellung aufzuheben, um Ziele und Endpunkte zu erstellen oder herauszufinden, welche Modelle in Endpunkten bereitgestellt wurden. Standardmäßig ist diese Option nicht aktiviert. 

**Nicht gesicherte RDS-Anforderung zulassen** Wenn diese Option ausgewählt ist, müssen RDS-Anfragen keine HTTPS verwenden. Standardmäßig ist diese Option nicht ausgewählt und die Kommunikation mit Data Services muss über „https“-Anforderungen ausgeführt werden.

**Nicht gesichertes Hochladen von Dokumenten aus Flex-Anwendungen zulassen:** Das Dateiupload-Servlet, das zum Hochladen von Dokumenten aus Adobe Flex®-Programmen in AEM Formulare verwendet wird, erfordert, dass Benutzer authentifiziert und autorisiert werden, bevor sie Dokumente hochladen können. Dem Benutzer muss die Rolle &quot;Document Upload Application User&quot;oder eine andere Rolle zugewiesen sein, die die Berechtigung zum Hochladen von Dokumenten enthält. Dadurch wird verhindert, dass nicht autorisierte Benutzer Dokumente auf den AEM Forms-Server hochladen. Wählen Sie diese Option aus, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung oder aus Gründen der Abwärtskompatibilität mit früheren Versionen von AEM Forms deaktivieren möchten. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter „Aufrufen von AEM Forms mithilfe von AEM Forms Remoting“ in „Programmieren mit AEM Forms“.

**Nicht gesichertes Hochladen von Dokumenten aus Java SDK-Anwendungen zulassen:** HTTP DocumentManager-Uploads müssen gesichert werden. HTTP-Uploads erfordern standardmäßig, dass Benutzer authentifiziert und autorisiert sind, bevor sie Dokumente hochladen können. Dem Benutzer muss die Rolle &quot;Dienstbenutzer&quot;oder eine andere Rolle zugewiesen sein, die die Berechtigung zum Aufrufen von Diensten enthält. Dadurch wird verhindert, dass nicht autorisierte Benutzer Dokumente auf den Forms-Server hochladen. Wählen Sie diese Option aus, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung deaktivieren möchten, um die Abwärtskompatibilität mit früheren Versionen von AEM Forms zu gewährleisten oder um sie auf der Grundlage Ihrer Firewall-Einrichtung zu installieren. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter „Aufrufen von AEM Forms mithilfe der Java-API“ in „Programmieren mit AEM Forms“.
