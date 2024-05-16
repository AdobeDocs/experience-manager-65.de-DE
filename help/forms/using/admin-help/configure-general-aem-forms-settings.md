---
title: Allgemeine AEM Forms-Einstellungen
description: Erfahren Sie, wie Sie die Seite „Core-Konfigurationen“ in der Administrationskonsole so konfigurieren, dass dies zu einer Verbesserung der Leistung des Systems beitragen kann.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: e1519477-b5a8-4947-8597-26b945a3b819
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1762'
ht-degree: 100%

---

# Allgemeine AEM Forms-Einstellungen {#general-aem-forms-settings}

Auf der Seite „Core-Konfigurationen“ in der Administrationskonsole finden Sie Einstellungen, mit deren Hilfe Sie die Leistung des Systems verbessern können. Nach dem Konfigurieren oder Aktualisieren dieser Einstellungen müssen Sie den Anwendungs-Server neu starten.

>[!NOTE]
>
> Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

Informationen zum Aktivieren des abgesicherten Sicherungsmodus finden Sie unter [Aktivieren und Deaktivieren des abgesicherten Sicherungsmodus](/help/forms/using/admin-help/enabling-disabling-safe-backup-mode.md#enabling-and-disabling-safe-backup-mode).


>[!NOTE]
>
>Die Dateien im temporären Ordner sowie die dauerhaft genutzten Dokumente im Stammordner des globalen Dokumentenspeichers (GDS) können vertrauliche Benutzerinformationen enthalten, z. B. Informationen, für die spezielle Berechtigungen erforderlich sind, wenn der Zugriff über die APIs oder Benutzeroberflächen erfolgt. Aus diesem Grund ist es wichtig, dass dieser Ordner mithilfe einer der vom Betriebssystem angebotenen Methoden ordnungsgemäß abgesichert wird. Es wird empfohlen, dass nur das Betriebssystemkonto, das zum Ausführen des Anwendungs-Servers dient, Lese- und Schreibzugriff auf diesen Ordner hat.


1. Wählen Sie in der Administrationskonsole **[!UICONTROL Einstellungen > Core-Systemeinstellungen > Konfigurationen]** aus.
1. Ändern Sie auf der Seite „Core-Konfigurationen“ die folgenden Optionen nach Bedarf und wählen Sie **[!UICONTROL OK]** aus. Einzelheiten zu den Optionen finden Sie unter [Optionen für die Core-Konfigurationen](configure-general-aem-forms-settings.md#core-configurations-options).


## Optionen für die Core-Konfigurationen {#core-configurations-options}

**Speicherort des temporären Ordners** Der Ordnerpfad, in dem AEM Forms temporäre Produktdateien erstellt. Wenn der Wert dieser Einstellung leer ist, wird als Speicherort standardmäßig ein Ordner unterhalb des Systemordners „temp“ gewählt. Stellen Sie sicher, dass der temporäre Ordner ein beschreibbarer Ordner ist.

>[!NOTE]
>
>Stellen Sie sicher, dass sich der temporäre Ordner im lokalen Dateisystem befindet. AEM Forms unterstützt keine temporären Ordner an einem Remote-Standort.

**Stammverzeichnis des globalen Dokumentenspeichers** – Das Stammverzeichnis des globalen Dokumentenspeichers (GDS) wird für folgende Zwecke verwendet:

* Speichern von dauerhaft genutzten Dokumenten. Dauerhaft genutzte Dokumente verfügen nicht über einen Ablaufzeitpunkt und bleiben so lange bestehen, bis sie entfernt werden (z. B. in einem Workflow-Prozess verwendete PDF-Dateien). Die dauerhaft genutzten Dokumente bilden einen wichtigen Teil für den gesamten Systemstatus. Wenn einige oder alle dieser Dokumente verloren gehen oder beschädigt werden, kann der Formular-Server instabil werden. Aus diesem Grund muss dieses Verzeichnis auf einem RAID-Gerät gespeichert werden.
* Speichern von temporären Dokumenten, die während der Verarbeitung benötigt werden.

>[!NOTE]
>
>Sie können die Dokumentenspeicherung auch in der AEM Forms-Datenbank aktivieren. Die Systemleistung ist jedoch bei der Verwendung des GDS höher.

* Übertragen von Dokumenten zwischen Knoten in einem Cluster. Wenn Sie AEM Forms in einer Cluster-Umgebung ausführen, muss auf diesen Ordner von allen Knoten im Cluster zugegriffen werden können.
* Empfangen eingehender Parameter von Remote-API-Aufrufen.

Wenn Sie keinen GDS-Stammordner angeben, wird als Ordner standardmäßig der Ordner des Anwendungs-Servers gewählt:

* `[JBOSS_HOME]/server/<server>/svcnative/DocumentStorage`
* `[WEBSPHERE_HOME]/installedApps/adobe/'server'/DocumentStorage`
* `[WEBLOGIC_HOME]/user_projects/<domain>/'server'/adobe/AEMformsserver/DocumentStorage`

>[!NOTE]
>
>Das Ändern des Wertes dieser Einstellung für den Stammordner des globalen Dokumentenspeichers muss mit besonderer Sorgfalt erfolgen. Das GDS-Verzeichnis wird zum Speichern sowohl von in einem Prozess dauerhaft genutzten Dateien als auch von kritischen AEM Forms-Produktkomponenten verwendet. Das Ändern des Speicherorts des GDS-Ordners stellt eine wesentliche Systemänderung dar. Eine fehlerhafte Konfiguration des Speicherorts des GDS-Ordners führt dazu, dass AEM Forms nicht mehr funktionsfähig ist, und kann eine vollständige Neuinstallation von AEM Forms erforderlich machen. Wenn Sie einen neuen Speicherort für den Ordner des globalen Dokumentenspeichers angeben, muss der Anwendungs-Server heruntergefahren und die Daten migriert werden, bevor der Server neu gestartet werden kann. Die Systemadmins müssen unter Beibehaltung der internen Ordnerstruktur alle Dateien aus dem alten an den neuen Speicherort verschieben.

>[!NOTE]
>
>Geben Sie für den temporären Ordner („temp“) und den GDS-Ordner nicht denselben Ordner an..

Zusätzliche Informationen zum GDS-Ordner finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver).](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)

**Speicherort des Verzeichnisses für Adobe Server-Schriftarten** – Geben Sie den Pfad zum Verzeichnis ein, der die Adobe-Server-Schriftarten enthält. Diese Schriftarten werden mit AEM Forms installiert. Der Standardspeicherort dieser Schriftarten ist der Ordner [aem-forms root]/fonts. Wenn auf diesen Ordner nicht zugegriffen werden kann, können Sie die Schriftarten an einen anderen Speicherort kopieren und über diese Einstellung den neuen Speicherort angeben.

**Speicherort des Verzeichnisses für Kundenschriftarten** – Geben Sie den Pfad zu einem Verzeichnis ein, das zusätzliche Schriftarten enthält, die Sie verwenden möchten.

***Hinweis **: Schriftarten werden aus dem Windows-Systemschriftarten-Cache ausgewählt, und ein Neustart des Systems ist erforderlich, um den Cache zu aktualisieren. Nachdem Sie das Verzeichnis für Kundenschriftarten angegeben haben, müssen Sie das System neu starten, auf dem AEM Forms installiert ist.*

**Speicherort des Verzeichnisses für Systemschriftarten** – Geben Sie den Pfad zu dem von Ihrem Betriebssystem vorgegebenen Verzeichnis für Schriftarten ein. Mehrere Ordner können hinzugefügt werden, indem sie durch ein Semikolon **;** voneinander getrennt werden.

**Speicherort der Data Service-Konfigurationsdatei** – Gibt den Speicherort der Datei „services-config.xml“ an. Diese Datei ist standardmäßig in die Datei „adobe-core-appserver.ear“ eingebettet und für Benutzende nicht zugänglich. Eine Kopie der Standarddatei „services-config.xml“ befindet sich unter [aem-forms-Stamm]\sdk\misc\DataServices\Server-Configuration. Wenn Sie Änderungen an dieser Datei vorgenommen und sie verschoben haben, geben Sie in dieses Feld den neuen Speicherort ein.

Mithilfe der Konfigurationsdatei für Data Services können Sie die Einstellungen von Data Services anpassen, wie z. B. den Authentifizierungstyp oder die Debug-Ausgabe.

Diese Einstellung ist standardmäßig leer.

**Standardmäßige Maximalgröße für Inline-Dokumente (Byte)** – die maximale Anzahl von Bytes, die im Speicher beibehalten werden, wenn Dokumente zwischen verschiedenen AEM Forms-Komponenten übergeben werden. Mit dieser Einstellung können Sie die Leistung anpassen. Dokumente, die diesen Wert unterschreiten, werden im Arbeitsspeicher gespeichert und bleiben in der Datenbank erhalten. Dokumente, die diesen Höchstwert überschreiten, werden auf der Festplatte gespeichert.

Dies ist eine obligatorische Einstellung. Der Standardwert ist 65536 Bytes.

**Maximale Standardwartezeit für Entsorgung (Sekunden)** – die maximale Zeit in Sekunden, während der ein Dokument, das zwischen verschiedenen AEM Forms-Komponenten weitergeleitet wird, als aktiv angesehen wird. Nach Ablauf dieser Zeit können alle Dateien entfernt werden, die zum Speichern dieses Dokuments verwendet wurden. Mit dieser Einstellung können Sie die Auslastung des Festplattenspeicherplatzes steuern.

Dies ist eine obligatorische Einstellung. Der Standardwert ist 600 Sekunden.

**Sweep-Intervall für Dokumente (Sekunden)** – die Zeit in Sekunden, die zwischen zwei Versuchen vergehen soll, Dateien zu löschen, die nicht mehr benötigt werden und zuvor zum Weiterleiten der Dokumentdaten zwischen Diensten verwendet wurden.

Dies ist eine obligatorische Einstellung. Der Standardwert ist 30 Sekunden.

**FIPS aktivieren** –– Wählen Sie diese Option zum Aktivieren des FIPS-Modus. FIPS 140-2 (Federal Information Processing Standard) ist ein von der US-Regierung definierter Kryptographiestandard. Im FIPS-Modus wird der Datenschutz von AEM Forms auf gemäß FIPS 140-2 zugelassene Algorithmen eingeschränkt, indem das Verschlüsselungsmodul „RSA BSAFE Crypto-C 2.1“ verwendet wird.

Im FIPS-Modus werden die in Adobe Acrobat®-Versionen vor 7.0 verwendeten Verschlüsselungsalgorithmen nicht unterstützt. Wenn der FIPS-Modus aktiviert ist und Sie den Encryption-Dienst zum Verschlüsseln von PDFs mit einem Kennwort mit einer Kompatibilitätsstufe verwenden, die auf Acrobat 5 festgelegt ist, kommt es bei dem Verschlüsselungsversuch zu einem Fehler.

Im Allgemeinen wendet der Assembler-Dienst bei aktiviertem FIPS keine Kennwortverschlüsselung auf Dokumente an. Wird dies dennoch versucht, wird eine FIPSModeException-Ausnahme ausgelöst, die angibt, dass „Kennwortverschlüsselung im FIPS-Modus nicht zulässig“ ist. Darüber hinaus wird das DDX-Element (Document Description XML) PDFsFromBookmarks im FIPS-Modus nicht unterstützt, wenn das Basisdokument kennwortverschlüsselt ist.

>[!NOTE]
>
>AEM Forms überprüft keinen Code, um die FIPS-Kompatibilität sicherzustellen. Es bietet einen FIPS-Betriebsmodus, sodass gemäß FIPS zugelassene Algorithmen für Kryptographiedienste aus den FIPS-zugelassenen Bibliotheken (RSA) verwendet werden.

**WSDL aktivieren** – Wählen Sie diese Option, um die Generierung von WSDL (Web Service Definition Language) für alle Dienste zu aktivieren, die Teil von AEM Forms sind.

Aktivieren Sie diese Option in Entwicklungsumgebungen, in denen Entwickelnde mithilfe der WSDL-Generierung Client-Anwendungen erstellen. Sie können die WSDL-Generierung in einer Produktionsumgebung deaktivieren, um zu vermeiden, dass interne Details eines Dienstes offengelegt werden.

**Dokumentenspeicher in der Datenbank aktivieren** – Wählen Sie diese Option, um dauerhaft genutzte Dokumente in der AEM Forms-Datenbank zu speichern. Wenn Sie diese Option aktivieren, benötigen Sie weiterhin einen GDS-Ordner. Dafür werden bei Auswahl dieser Option AEM Forms-Sicherungen vereinfacht. Wenn Sie den globalen Dokumentenspeicher verwenden, umfasst eine Sicherung, dass das AEM Forms-System in den Sicherungsmodus versetzt wird und anschließend die Sicherungen der Datenbank und des globalen Dokumentenspeichers ausgeführt werden. Wenn Sie die Datenbankoption auswählen, umfasst die Sicherung das Ausführen der Datenbanksicherung für eine neue Installation oder das Ausführen der Datenbanksicherung und die einmalige Sicherung des globalen Dokumentenspeichers für eine Aktualisierung. Es ist möglicherweise eine zusätzliche Verwaltung Ihrer Datenbank erforderlich, um Aufträge und Daten im Vergleich zu einer alleinigen Konfiguration des globalen Dokumentenspeichers zu entfernen. (Siehe Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird.)

**DSC-Aufrufstatistik aktivieren** – Wenn diese Option ausgewählt ist, verfolgt AEM Forms Aufrufstatistiken, z. B. die Anzahl der Aufrufe, die für das Aufrufen erforderliche Zeit und die Anzahl der Fehler in den Aufrufen. Diese Informationen werden in einer JMX-Bean gespeichert, sodass Sie die Java™ JConsole oder die Software eines anderen Herstellers zum Anzeigen der Statistiken verwenden können. Wenn Sie diese Statistiken nicht anzeigen möchten, deaktivieren Sie diese Option, um die Leistung von AEM Forms zu verbessern.

**RDS aktivieren** – Durch die Auswahl dieser Option wird das Remote Development Services (RDS)-Servlet in AEM Forms aktiviert. Wenn diese Option aktiviert ist, können Client-seitige Werkzeuge mit Data Services interagieren, um zum Erstellen von Zielen oder Endpunkten Modelle bereitzustellen oder deren Bereitstellung wieder aufzuheben oder zu ermitteln, welche Modelle in Endpunkten bereitgestellt wurden. Standardmäßig ist diese Option nicht aktiviert. 

**Nicht gesicherte RDS-Anfrage zulassen** – Wenn diese Option ausgewählt ist, müssen RDS-Anfragen keine HTTPS verwenden. Standardmäßig ist diese Option nicht ausgewählt und die Kommunikation mit Data Services muss über „https“-Anforderungen ausgeführt werden. 

**Unsicheren Dokumenten-Upload von Flex-Anwendungen zulassen** – Das Datei-Upload-Servlet für das Hochladen von Dokumenten aus Adobe Flex®-Anwendungen in AEM Forms erfordert, dass Benutzende authentifiziert und autorisiert werden, bevor sie Dokumente hochladen können. Benutzenden muss die Rolle „Benutzer der Dokumenten-Upload-Anwendung“ oder eine andere Rolle, die die Berechtigung zum Hochladen von Dokumenten enthält, zugewiesen sein. Dadurch wird verhindert, dass nicht autorisierte Benutzende Dokumente auf den AEM-Formular-Server hochladen. Wählen Sie diese Option aus, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung oder für die Abwärtskompatibilität mit vorherigen Versionen von AEM Forms deaktivieren wollen. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter „Aufrufen von AEM Forms mithilfe von AEM Forms Remoting“ in „Programmieren mit AEM Forms“.

**Zulassen von ungesichertem Dokumenten-Upload aus Java SDK-Anwendungen:** HTTP DocumentManager-Uploads müssen gesichert sein. HTTP-Uploads erfordern standardmäßig, dass Benutzende authentifiziert und autorisiert sind, bevor sie Dokumente hochladen können. Benutzenden muss die Rolle „Dienstbenutzer“ oder eine andere Rolle zugewiesen sein, die die Berechtigung zum Aufrufen von Diensten enthält. Dadurch wird verhindert, dass nicht autorisierte Benutzende Dokumente auf den Formular-Server hochladen. Wählen Sie diese Option aus, wenn Sie diese Sicherheitsfunktion in einer Entwicklungsumgebung deaktivieren möchten, um die Abwärtskompatibilität mit früheren Versionen von AEM Forms zu gewährleisten oder je Ihrer Firewall-Einrichtung. Standardmäßig ist diese Option nicht aktiviert. Weitere Informationen finden Sie unter „Aufrufen von AEM Forms mithilfe der Java-API“ in „Programmieren mit AEM Forms“.
